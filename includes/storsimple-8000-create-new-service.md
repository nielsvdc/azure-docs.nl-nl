---
author: alkohli
ms.service: storsimple
ms.topic: include
ms.date: 10/26/2018
ms.author: alkohli
ms.openlocfilehash: d47cf21e25c89c20a8baa31a80b867b74ada93df
ms.sourcegitcommit: 6a902230296a78da21fbc68c365698709c579093
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/05/2020
ms.locfileid: "93360672"
---
#### <a name="to-create-a-new-service"></a>Een nieuwe service maken

1. Gebruik de referenties van uw Microsoft-account om u aan te melden bij [Azure Portal](https://portal.azure.com/).

2. Klik in Azure Portal op **Een resource maken** en klik vervolgens in de Marketplace op **Alles weergeven**.

    ![StorSimple-apparaatbeheerfunctie maken](./media/storsimple-8000-create-new-service/createssdevman1.png)

    Zoek naar _Fysieke StorSimple_. Selecteer en klik op **Serie met fysieke StorSimple-apparaten** en klik vervolgens op **Maken**. U kunt ook in de Azure Portal klikken **+** en vervolgens onder **opslag** klikken op **StorSimple fysieke apparaat Series**.

    ![StorSimple maken Apparaatbeheer 2](./media/storsimple-8000-create-new-service/createssdevman11.png)

3. Voer de volgende stappen uit op de blade **StorSimple-apparaatbeheerfunctie** :

   1. Geef een unieke **resourcenaam** voor uw service op. Deze naam is een beschrijvende naam die kan worden gebruikt om de service te identificeren. De naam kan tussen 2 en 50 tekens bevatten (letters, cijfers en afbreekstreepjes). De naam moet beginnen en eindigen met een letter of cijfer.

   2. Kies een **abonnement** in de vervolgkeuzelijst. Het abonnement is gekoppeld aan uw factureringsrekening. Dit veld wordt niet weergegeven als u slechts één abonnement hebt.

   3. Gebruik voor **Resourcegroep** de optie **Bestaande groep gebruiken** of **Nieuwe groep maken**. Zie [Azure-resourcegroepen](/azure/azure-resource-manager/management/manage-resource-groups-portal) voor meer informatie.

   4. Geef een **locatie** voor uw service op. Kies in het algemeen een locatie die het dichtst bij de geografische regio ligt waar u uw apparaat wilt implementeren. U kunt ook rekening houden met de volgende overwegingen:

      * Als u bestaande workloads in Azure hebt die u ook wilt implementeren met uw StorSimple-apparaat, moet u dat datacenter gebruiken.
      * Uw StorSimple Manager-apparaatbeheerfunctie en Azure Storage kunnen zich op twee verschillende locaties bevinden. In dat geval moet u de StorSimple--apparaatbeheerfunctie en het Azure Storage-account afzonderlijk maken. U maakt een Azure Storage-account door naar de Azure Storage-service in Azure Portal te gaan en de stappen in [Een Azure Storage-account maken](../articles/storage/common/storage-account-create.md) uit te voeren. Nadat u dit account hebt gemaakt, voegt u het toe aan de StorSimple-apparaatbeheerfunctie met de stappen in [Een nieuw opslagaccount voor de service maken](../articles/storsimple/storsimple-8000-deployment-walkthrough-u2.md#configure-a-new-storage-account-for-the-service).

   5. Selecteer **Een nieuw opslagaccount maken** om automatisch een opslagaccount te maken met de service. Geef een naam op voor dit opslagaccount. Als u een andere locatie voor uw gegevens wilt kiezen, schakelt u dit vakje uit.

   6. Schakel **Aan dashboard vastmaken** in als u een snelkoppeling naar deze service op uw dashboard wilt.

   7. Klik op **Maken** om de StorSimple-apparaatbeheerfunctie te maken.

       ![StorSimple Apparaatbeheer 3 maken](./media/storsimple-8000-create-new-service/createssdevman2.png)

Het maken van de service duurt enkele minuten. Nadat de service is gemaakt, ziet u een melding en wordt de blade met de nieuwe service geopend.

![StorSimple Apparaatbeheer 4 maken](./media/storsimple-8000-create-new-service/createssdevman5.png)
