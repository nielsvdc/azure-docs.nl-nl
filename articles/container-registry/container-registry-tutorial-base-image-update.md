---
title: 'Zelfstudie: build van installatiekopie activeren bij bijwerken van basisinstallatiekopie'
description: In deze zelfstudie leert u hoe u een Azure Container Registry-taak configureert om builds van containerinstallatiekopieën automatisch te activeren in de cloud wanneer een basisinstallatiekopie wordt bijgewerkt in hetzelfde register.
ms.topic: tutorial
ms.date: 01/22/2020
ms.custom: seodec18, mvc, devx-track-js, devx-track-azurecli
ms.openlocfilehash: 8188fb715e4e24c523bc25399cea6cdc76f8696b
ms.sourcegitcommit: daab0491bbc05c43035a3693a96a451845ff193b
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/29/2020
ms.locfileid: "93027649"
---
# <a name="tutorial-automate-container-image-builds-when-a-base-image-is-updated-in-an-azure-container-registry"></a>Zelfstudie: Builds van containerinstallatiekopieën automatiseren wanneer een basisinstallatiekopie wordt bijgewerkt in een Azure-containerregister 

ACR Tasks ondersteunt de automatische compilatie van containerinstallatiekopieën wanneer de [basisinstallatiekopie van een container wordt bijgewerkt](container-registry-tasks-base-images.md), bijvoorbeeld wanneer u het besturingssysteem of toepassingsframework patcht in een van uw basisinstallatiekopieën. 

In deze zelfstudie leert u hoe u een ACR-taak maakt waarmee een build in de cloud wordt geactiveerd wanneer de basisinstallatiekopie van een container naar hetzelfde register wordt gepusht. U kunt ook een zelfstudie volgen voor het maken van een ACR-taak waarmee de build van een installatiekopie wordt geactiveerd wanneer een basisinstallatiekopie naar [een ander Azure-containerregister](container-registry-tutorial-private-base-image-update.md) wordt gepusht. 

In deze zelfstudie:

> [!div class="checklist"]
> * De basisinstallatiekopie bouwen
> * Een toepassingsinstallatiekopie maken in hetzelfde register om de basisinstallatiekopie te volgen 
> * De basisinstallatiekopie bijwerken om een taak voor een toepassingsinstallatiekopie bij te werken
> * De geactiveerde taak weergeven
> * De bijgewerkte toepassingsinstallatiekopie controleren

[!INCLUDE [cloud-shell-try-it.md](../../includes/cloud-shell-try-it.md)]

Als u Azure CLI lokaal wilt gebruiken, moet u ervoor zorgen dat versie **2.0.46** of hoger van Azure CLI is geïnstalleerd. Voer `az --version` uit om de versie te bekijken. Als u de CLI wilt installeren of upgraden, raadpleegt u [Azure CLI installeren][azure-cli].

## <a name="prerequisites"></a>Vereisten

### <a name="complete-the-previous-tutorials"></a>De vorige zelfstudies voltooien

In deze zelfstudie wordt ervan uitgegaan dat u de stappen van de eerste twee zelfstudies in de serie al hebt uitgevoerd:

* Azure Container Registry maken
* Voorbeeldopslagplaats splitsen
* Voorbeeldopslagplaats klonen
* Persoonlijk toegangstoken van GitHub maken

Als u de volgende zelfstudies nog niet hebt afgerond, doet u dit voordat u verdergaat:

[Zelfstudie: containerinstallatiekopieën bouwen in de cloud met Azure Container Registry Tasks](container-registry-tutorial-quick-task.md)

[Builds van containerinstallatiekopieën automatiseren met Azure Container Registry Tasks](container-registry-tutorial-build-task.md)

### <a name="configure-the-environment"></a>De omgeving configureren

Vul deze variabelen voor de shell-omgeving in met waarden die geschikt zijn voor uw omgeving. Hoewel deze stap strikt genomen niet vereist is, vereenvoudigt u hiermee de uitvoering van meerregelige Azure CLI-opdrachten in deze zelfstudie. Als u deze omgevingsvariabelen niet invult, moet u elke bijbehorende waarde handmatig vervangen wanneer deze wordt weergegeven in de voorbeeldopdrachten.

[![Starten insluiten](https://shell.azure.com/images/launchcloudshell.png "Azure Cloud Shell starten")](https://shell.azure.com)

```console
ACR_NAME=<registry-name>        # The name of your Azure container registry
GIT_USER=<github-username>      # Your GitHub user account name
GIT_PAT=<personal-access-token> # The PAT you generated in the second tutorial
```


### <a name="base-image-update-scenario"></a>Bijwerkscenario van basisinstallatiekopieën

In deze zelfstudie besteden we aandacht aan een scenario voor het bijwerken van een basisinstallatie kopie waarbij een basisinstallatiekopie en een toepassingsinstallatiekopie in één register worden onderhouden. 

Het [codevoorbeeld][code-sample] bevat twee Dockerfiles: een toepassingsinstallatiekopie en een installatiekopie als basis. In de volgende gedeeltes maakt u een ACR-taak waarmee automatisch een build van de toepassingsinstallatiekopie wordt geactiveerd wanneer een nieuwe versie van de basisinstallatiekopie naar hetzelfde containerregister wordt gepusht.

* [Dockerfile-app][dockerfile-app]: Een kleine Node.js-webtoepassing die een statische webpagina maakt waarop de Node.js-versie ervan wordt weergegeven. De versietekenreeks wordt gesimuleerd: deze geeft de inhoud weer van een omgevingsvariabele, `NODE_VERSION`, die is gedefinieerd in de basisinstallatiekopie.

* [Dockerfile-basis][dockerfile-base]: De installatiekopie die `Dockerfile-app` opgeeft als basis. Deze is zelf gebaseerd op een [Node][base-node]-installatiekopie en bevat de omgevingsvariabele `NODE_VERSION`.

In de volgende gedeeltes maakt u een taak, werkt u de waarde `NODE_VERSION` in het Docker-bestand van de basisinstallatiekopie bij en gebruikt u ACR Tasks om de basisinstallatiekopie te maken. Zodra de ACR-taak de nieuwe basisinstallatiekopie naar uw register pusht, wordt er automatisch een build van de toepassingsinstallatiekopie geactiveerd. Optioneel kunt u de containerinstallatiekopie van de toepassing lokaal uitvoeren om de verschillende versietekenreeksen in de ingebouwde installatiekopieën te bekijken.

In deze zelfstudie wordt met uw ACR-taak een containerinstallatiekopie voor een toepassing gemaakt en gepusht. De installatiekopie is opgegeven in een Dockerfile. Met ACR-taken kunnen ook [taken bestaande uit meerdere stappen](container-registry-tasks-multi-step.md) worden uitgevoerd. Hierbij wordt een YAML-bestand gebruikt om de stappen voor het bouwen, pushen en optioneel testen van meerdere containers te definiëren.

## <a name="build-the-base-image"></a>De basisinstallatiekopie bouwen

Start met het bouwen van de basisinstallatiekopie met een *snelle taak* met behulp van [az acr build][az-acr-build]. Zoals beschreven in de [eerste zelfstudie](container-registry-tutorial-quick-task.md) in de reeks, wordt met dit proces niet alleen de installatiekopie gebouwd, maar wordt deze ook naar het containerregister gepusht als de build is gelukt.

```azurecli-interactive
az acr build --registry $ACR_NAME --image baseimages/node:9-alpine --file Dockerfile-base .
```

## <a name="create-a-task"></a>Een taak maken

Maak vervolgens een taak met [az acr task create][az-acr-task-create]:

```azurecli-interactive
az acr task create \
    --registry $ACR_NAME \
    --name taskhelloworld \
    --image helloworld:{{.Run.ID}} \
    --arg REGISTRY_NAME=$ACR_NAME.azurecr.io \
    --context https://github.com/$GIT_USER/acr-build-helloworld-node.git \
    --file Dockerfile-app \
    --git-access-token $GIT_PAT
```

Deze taak is vergelijkbaar met de taak die u in de [vorige zelfstudie](container-registry-tutorial-build-task.md) hebt gemaakt. De taak geeft ACR Tasks de opdracht om een installatiekopiebuild te activeren wanneer doorvoeracties worden gepusht naar de opslagplaats die met `--context` is opgegeven. De Dockerfile die wordt gebruikt om de installatiekopie te bouwen in de vorige zelfstudie, geeft een openbare basisinstallatiekopie (`FROM node:9-alpine`) op. De Dockerfile in deze taak, [Dockerfile-app][dockerfile-app], geeft een basisinstallatiekopie in hetzelfde register op:

```dockerfile
FROM ${REGISTRY_NAME}/baseimages/node:9-alpine
```

Met deze configuratie kunt u eenvoudig een frameworkpatch in de basisinstallatiekopie simuleren verderop in deze zelfstudie.

## <a name="build-the-application-container"></a>De toepassingscontainer bouwen

Gebruik [az acr task run][az-acr-task-run] om handmatig de taak te activeren en de toepassingsinstallatiekopie te bouwen: Deze stap is nodig om ervoor te zorgen dat de taak de afhankelijkheid van de toepassingsinstallatiekopie van de basisinstallatiekopie bijhoudt.

```azurecli-interactive
az acr task run --registry $ACR_NAME --name taskhelloworld
```

Zodra de taak is voltooid, moet u de **run-id** (bijvoorbeeld 'da6') noteren als u de volgende optionele stap wilt voltooien.

### <a name="optional-run-application-container-locally"></a>Optioneel: Toepassingscontainer lokaal uitvoeren

Als u lokaal werkt (niet in Cloud Shell) en Docker hebt geïnstalleerd, voert u de container uit om de toepassing te bekijken in een webbrowser voordat u de basisinstallatiekopie opnieuw bouwt. Als u Cloud Shell gebruikt, slaat u deze sectie over (Cloud Shell biedt geen ondersteuning voor `az acr login` of `docker run`).

Verifieer uzelf eerst bij uw containerregister met [az acr login][az-acr-login]:

```azurecli
az acr login --name $ACR_NAME
```

Voer de container nu lokaal uit met `docker run`. Vervang **\<run-id\>** door de gevonden run-id in de uitvoer van de vorige stap (bijvoorbeeld 'da6'). Dit voorbeeld noemt de container `myapp` en bevat de parameter `--rm` om de container te verwijderen wanneer u deze stopt.

```bash
docker run -d -p 8080:80 --name myapp --rm $ACR_NAME.azurecr.io/helloworld:<run-id>
```

Ga naar `http://localhost:8080` in uw browser. U ziet nu het weergegeven nummer van de Node.js-versie op de webpagina, zoals hieronder weergegeven. In een latere stap verhoogt u de versie door een 'a' toe te voegen aan de versietekenreeks.

![Schermafbeelding van de voorbeeldtoepassing die wordt weergegeven in de browser.][base-update-01]

Voer de volgende opdracht uit om de container te stoppen en te verwijderen:

```bash
docker stop myapp
```

## <a name="list-the-builds"></a>De builds weergeven

Geef vervolgens een overzicht weer van de taken die ACR Tasks heeft voltooid voor het register door de opdracht [az acr task list-runs][az-acr-task-list-runs] te gebruiken:

```azurecli-interactive
az acr task list-runs --registry $ACR_NAME --output table
```

Als u de vorige zelfstudie hebt voltooid (en het register niet hebt verwijderd), ziet u de uitvoer zoals hieronder weergegeven. Noteer het aantal taak-runs en de meest recente run-id, zodat u de uitvoer kunt vergelijken nadat u in het volgende gedeelte de basisinstallatiekopie hebt bijgewerkt.

```output
RUN ID    TASK            PLATFORM    STATUS     TRIGGER     STARTED               DURATION
--------  --------------  ----------  ---------  ----------  --------------------  ----------
da6       taskhelloworld  Linux       Succeeded  Manual      2018-09-17T23:07:22Z  00:00:38
da5                       Linux       Succeeded  Manual      2018-09-17T23:06:33Z  00:00:31
da4       taskhelloworld  Linux       Succeeded  Git Commit  2018-09-17T23:03:45Z  00:00:44
da3       taskhelloworld  Linux       Succeeded  Manual      2018-09-17T22:55:35Z  00:00:35
da2       taskhelloworld  Linux       Succeeded  Manual      2018-09-17T22:50:59Z  00:00:32
da1                       Linux       Succeeded  Manual      2018-09-17T22:29:59Z  00:00:57
```

## <a name="update-the-base-image"></a>De basisinstallatiekopie bijwerken

Hier kunt u een frameworkpatch in de basisinstallatiekopie simuleren. Bewerk de **Dockerfile-basis**  en voeg een 'a' toe achter het versienummer dat is gedefinieerd in `NODE_VERSION`:

```dockerfile
ENV NODE_VERSION 9.11.2a
```

Voer een snelle taak uit om de gewijzigde basisinstallatiekopie te bouwen. Noteer de waarde van **run-id** in de uitvoer.

```azurecli-interactive
az acr build --registry $ACR_NAME --image baseimages/node:9-alpine --file Dockerfile-base .
```

Zodra de build is voltooid en de ACR-taak de nieuwe basisinstallatiekopie naar uw register heeft gepusht, wordt automatisch een build van de toepassingsinstallatiekopie geactiveerd. Het kan enkele ogenblikken duren voordat de toepassingsinstallatiekopie wordt geactiveerd door de taak die u eerder hebt gemaakt, omdat met de taak de pas gemaakte en gepushte basisinstallatiekopie moet worden gedetecteerd.

## <a name="list-updated-build"></a>Bijgewerkte build weergeven

Nu u de basisinstallatiekopie hebt bijgewerkt, geeft u opnieuw een lijst van uw taken weer om deze te vergelijken met de vorige lijst. Als de uitvoer in eerste instantie niet verschilt, voert u regelmatig de opdracht uit tot de nieuwe taak-run in de lijst wordt weergegeven.

```azurecli-interactive
az acr task list-runs --registry $ACR_NAME --output table
```

De uitvoer lijkt op het volgende. De TRIGGER voor de als laatste uitgevoerde build moet Update van installatiekopie zijn. Hiermee wordt aangegeven dat de taak is gestart door uw snelle taak van de basisinstallatiekopie.

```output
Run ID    TASK            PLATFORM    STATUS     TRIGGER       STARTED               DURATION
--------  --------------  ----------  ---------  ------------  --------------------  ----------
da8       taskhelloworld  Linux       Succeeded  Image Update  2018-09-17T23:11:50Z  00:00:33
da7                       Linux       Succeeded  Manual        2018-09-17T23:11:27Z  00:00:35
da6       taskhelloworld  Linux       Succeeded  Manual        2018-09-17T23:07:22Z  00:00:38
da5                       Linux       Succeeded  Manual        2018-09-17T23:06:33Z  00:00:31
da4       taskhelloworld  Linux       Succeeded  Git Commit    2018-09-17T23:03:45Z  00:00:44
da3       taskhelloworld  Linux       Succeeded  Manual        2018-09-17T22:55:35Z  00:00:35
da2       taskhelloworld  Linux       Succeeded  Manual        2018-09-17T22:50:59Z  00:00:32
da1                       Linux       Succeeded  Manual        2018-09-17T22:29:59Z  00:00:57
```

Als u de volgende optionele stap van de nieuw gebouwde container wilt uitvoeren om het bijgewerkte versienummer te zien, noteert u de **RUN ID** -waarde voor het bijwerken van de door de installatiekopie getriggerde build (in de vorige uitvoer is dit 'da8').

### <a name="optional-run-newly-built-image"></a>Optioneel: Nieuw gebouwde installatiekopie uitvoeren

Als u lokaal werkt (niet in Cloud Shell) en u hebt Docker geïnstalleerd, voert u de nieuwe toepassingsinstallatiekopie uit zodra de build is voltooid. Vervang `<run-id>` door de run-id uit de vorige stap. Als u Cloud Shell gebruikt, slaat u deze sectie over (Cloud Shell biedt geen ondersteuning voor `docker run`).

```bash
docker run -d -p 8081:80 --name updatedapp --rm $ACR_NAME.azurecr.io/helloworld:<run-id>
```

Ga naar http://localhost:8081 in uw browser. U ziet nu het bijgewerkte nummer van de Node.js-versie (met de 'a') op de webpagina:

![Schermafbeelding van de voorbeeldtoepassing die wordt weergegeven in de browser][base-update-02]

U hebt uw **basis** installatiekopie bijgewerkt met een nieuw versienummer, maar de **toepassings** installatiekopie die als laatste is gebouwd, geeft nieuwe versie weer. ACR Tasks heeft uw wijziging van de basisinstallatiekopie herkend en heeft de toepassingsinstallatiekopie automatisch opnieuw opgebouwd.

Voer de volgende opdracht uit om de container te stoppen en te verwijderen:

```bash
docker stop updatedapp
```

## <a name="next-steps"></a>Volgende stappen

In deze zelfstudie hebt u geleerd hoe u een taak configureert om automatisch builds van containerinstallatiekopieën te activeren wanneer een basisinstallatiekopie is bijgewerkt. Ga nu verder met de volgende zelfstudie voor meer informatie over het activeren van taken volgens een gedefinieerd schema.

> [!div class="nextstepaction"]
> [Een taak volgens een schema uitvoeren](container-registry-tasks-scheduled.md)

<!-- LINKS - External -->
[base-node]: https://hub.docker.com/_/node/
[code-sample]: https://github.com/Azure-Samples/acr-build-helloworld-node
[dockerfile-app]: https://github.com/Azure-Samples/acr-build-helloworld-node/blob/master/Dockerfile-app
[dockerfile-base]: https://github.com/Azure-Samples/acr-build-helloworld-node/blob/master/Dockerfile-base

<!-- LINKS - Internal -->
[azure-cli]: /cli/azure/install-azure-cli
[az-acr-build]: /cli/azure/acr#az-acr-build
[az-acr-task-create]: /cli/azure/acr/task#az-acr-task-create
[az-acr-task-update]: /cli/azure/acr/task#az-acr-task-update
[az-acr-task-run]: /cli/azure/acr/task#az-acr-task-run
[az-acr-login]: /cli/azure/acr#az-acr-login
[az-acr-task-list-runs]: /cli/azure/acr
[az-acr-task]: /cli/azure/acr

<!-- IMAGES -->
[base-update-01]: ./media/container-registry-tutorial-base-image-update/base-update-01.png
[base-update-02]: ./media/container-registry-tutorial-base-image-update/base-update-02.png
