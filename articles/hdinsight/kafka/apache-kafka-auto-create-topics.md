---
title: Automatisch maken van een onderwerp in Apache Kafka-Azure HDInsight inschakelen
description: Meer informatie over het configureren van Apache Kafka op HDInsight om automatisch onderwerpen te maken. U kunt Kafka configureren door `auto.create.topics.enable` in te stellen op True via Ambari. Of tijdens het maken van een cluster via Power shell of Resource Manager-sjablonen.
author: hrasheed-msft
ms.author: hrasheed
ms.reviewer: jasonh
ms.service: hdinsight
ms.topic: how-to
ms.custom: hdinsightactive,seoapr2020
ms.date: 04/28/2020
ms.openlocfilehash: 829f91452725615af4d444426e25ffad62d6ab6d
ms.sourcegitcommit: 829d951d5c90442a38012daaf77e86046018e5b9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/09/2020
ms.locfileid: "86087499"
---
# <a name="how-to-configure-apache-kafka-on-hdinsight-to-automatically-create-topics"></a>Apache Kafka op HDInsight configureren om automatisch onderwerpen te maken

Standaard wordt het automatisch maken van een onderwerp niet ingeschakeld door Apache Kafka op HDInsight. U kunt het automatisch maken van een onderwerp voor bestaande clusters inschakelen met Apache Ambari. U kunt ook automatisch onderwerpen maken inschakelen wanneer u een nieuw Kafka-cluster maakt met behulp van een Azure Resource Manager sjabloon.

## <a name="apache-ambari-web-ui"></a>Apache Ambari-webgebruikersinterface

Gebruik de volgende stappen om het automatisch maken van een onderwerp in een bestaand cluster via de Ambari-webgebruikersinterface in te scha kelen:

1. Selecteer uw Kafka-cluster uit het [Azure Portal](https://portal.azure.com).

1. Selecteer **Ambari Home**van **cluster dashboards**.

    ![Afbeelding van de portal waarop het cluster dashboard is geselecteerd](./media/apache-kafka-auto-create-topics/azure-portal-cluster-dashboard-ambari.png)

    Verifieer, wanneer u hierom wordt gevraagd, met behulp van de aanmeldings referenties (admin) voor het cluster. In plaats daarvan kunt u rechtstreeks verbinding maken met Amabri vanuit `https://CLUSTERNAME.azurehdinsight.net/` waar `CLUSTERNAME` de naam van uw Kafka-cluster is.

1. Selecteer de Kafka-service in de lijst aan de linkerkant van de pagina.

    ![Tabblad Apache Ambari service List](./media/apache-kafka-auto-create-topics/hdinsight-service-list.png)

1. Selecteer configuraties in het midden van de pagina.

    ![Tabblad Apache Ambari service-configuratie](./media/apache-kafka-auto-create-topics/hdinsight-service-config.png)

1. Voer in het veld Filter een waarde van in `auto.create` .

    ![Veld Apache Ambari search filter](./media/apache-kafka-auto-create-topics/hdinsight-filter-field.png)

    Met deze instelling wordt de lijst met eigenschappen gefilterd en wordt de instelling weer gegeven `auto.create.topics.enable` .

1. Wijzig de waarde van `auto.create.topics.enable` in `true` en selecteer vervolgens **Opslaan**. Voeg een notitie toe en selecteer vervolgens **Opslaan** opnieuw.

    ![Afbeelding van het bestand auto. Create. topics. enable entry](./media/apache-kafka-auto-create-topics/auto-create-topics-enable.png)

1. Selecteer de Kafka-service, selecteer __opnieuw opstarten__en selecteer vervolgens __alle betrokkenen opnieuw opstarten__. Selecteer __Bevestig opnieuw opstarten__als dit wordt gevraagd.

    ![Apache Ambari start alle betrokkenen opnieuw](./media/apache-kafka-auto-create-topics/restart-all-affected.png)

> [!NOTE]  
> U kunt Ambari-waarden ook instellen via de Ambari-REST API. Dit is over het algemeen moeilijker, omdat u meerdere REST-aanroepen moet maken om de huidige configuratie op te halen, deze te wijzigen, enzovoort. Zie [HDInsight-clusters beheren met het Apache Ambari rest API](../hdinsight-hadoop-manage-ambari-rest-api.md) -document voor meer informatie.

## <a name="resource-manager-templates"></a>Resource Manager-sjablonen

Wanneer u een Kafka-cluster maakt met behulp van een Azure Resource Manager-sjabloon, kunt u dit rechtstreeks instellen `auto.create.topics.enable` door het te voegen in een `kafka-broker` . In het volgende JSON-code fragment ziet u hoe u deze waarde instelt op `true` :

```json
"clusterDefinition": {
    "kind": "kafka",
    "configurations": {
    "gateway": {
        "restAuthCredential.isEnabled": true,
        "restAuthCredential.username": "[parameters('clusterLoginUserName')]",
        "restAuthCredential.password": "[parameters('clusterLoginPassword')]"
    },
    "kafka-broker": {
        "auto.create.topics.enable": "true"
    }
}
```

## <a name="next-steps"></a>Volgende stappen

In dit document hebt u geleerd hoe u het automatisch maken van een onderwerp voor Apache Kafka op HDInsight inschakelt. Raadpleeg de volgende koppelingen voor meer informatie over het werken met Kafka:

* [Apache Kafka-logboeken analyseren](apache-kafka-log-analytics-operations-management.md)
* [Gegevens repliceren tussen Apache Kafka-clusters](apache-kafka-mirroring.md)
