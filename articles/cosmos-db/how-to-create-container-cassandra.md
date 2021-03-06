---
title: Een container maken in Azure Cosmos DB Cassandra-API
description: Meer informatie over het maken van een container in Azure Cosmos DB Cassandra-API met behulp van Azure Portal, .NET, Java, Python, Node.js en andere Sdk's.
author: markjbrown
ms.service: cosmos-db
ms.subservice: cosmosdb-cassandra
ms.topic: how-to
ms.date: 10/16/2020
ms.author: mjbrown
ms.custom: devx-track-azurecli, devx-track-csharp
ms.openlocfilehash: 01030a563c15eee7786058c2eae30d23803dfe42
ms.sourcegitcommit: 3bdeb546890a740384a8ef383cf915e84bd7e91e
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/30/2020
ms.locfileid: "93101643"
---
# <a name="create-a-container-in-azure-cosmos-db-cassandra-api"></a>Een container maken in Azure Cosmos DB Cassandra-API
[!INCLUDE[appliesto-cassandra-api](includes/appliesto-cassandra-api.md)]

In dit artikel worden de verschillende manieren beschreven voor het maken van een container in Azure Cosmos DB Cassandra-API. U ziet hoe u een container maakt met behulp van Azure Portal, Azure CLI, Power shell of ondersteunde Sdk's. In dit artikel ziet u hoe u een container maakt, de partitiesleutel opgeeft en doorvoer inricht.

In dit artikel worden de verschillende manieren beschreven voor het maken van een container in Azure Cosmos DB Cassandra-API. Als u een andere API gebruikt, raadpleegt u [API voor MongoDb](how-to-create-container-mongodb.md), [Gremlin API](how-to-create-container-gremlin.md), [Table-API](how-to-create-container-table.md)en [SQL API](how-to-create-container.md) -artikelen om de container te maken.

> [!NOTE]
> Wanneer u containers maakt, moet u ervoor zorgen dat u niet twee containers maakt met dezelfde naam, maar met een ander hoofdletter gebruik. Dat komt omdat sommige onderdelen van het Azure-platform niet hoofdletter gevoelig zijn. Dit kan leiden tot Verwar ring/botsing van telemetriegegevens en acties op containers met dergelijke namen.

## <a name="create-using-azure-portal"></a><a id="portal-cassandra"></a>Maken met behulp van de Azure-portal

1. Meld u aan bij [Azure Portal](https://portal.azure.com/).

1. [Maak een nieuw Azure Cosmos-account](create-cassandra-dotnet.md#create-a-database-account)of selecteer een bestaand account.

1. Open het deel venster **Data Explorer** en selecteer **nieuwe tabel** . Geef de volgende gegevens op:

   * Geef aan of u een nieuwe keyspace maakt of een bestaande keyspace gebruikt.
   * Voer een tabelnaam in.
   * Voer de eigenschappen in en geef een primaire sleutel op.
   * Geef een door Voer op die moet worden ingericht (bijvoorbeeld 1000 RUs).
   * Selecteer **OK** .

    :::image type="content" source="./media/how-to-create-container/partitioned-collection-create-cassandra.png" alt-text="Schermopname van Cassandra-API, dialoogvenster Tabel toevoegen":::

> [!NOTE]
> Voor de Cassandra-API wordt de primaire sleutel gebruikt als de partitiesleutel.

## <a name="create-using-net-sdk"></a><a id="dotnet-cassandra"></a>Maken met behulp van .NET SDK

```csharp
// Create a Cassandra table with a partition/primary key and provision 1000 RU/s throughput.
session.Execute(CREATE TABLE myKeySpace.myTable(
    user_id int PRIMARY KEY,
    firstName text,
    lastName text) WITH cosmosdb_provisioned_throughput=1000);
```

Als er een time-outuitzondering optreedt bij het maken van een verzameling, moet u een lees bewerking uitvoeren om te controleren of de verzameling is gemaakt. Met de Lees bewerking wordt een uitzonde ring gegenereerd totdat de bewerking voor het maken van de verzameling is voltooid. Zie de [HTTP-status codes voor Azure Cosmos DB](/rest/api/cosmos-db/http-status-codes-for-cosmosdb) artikel voor een lijst met status codes die door de maak bewerking worden ondersteund.

## <a name="create-using-azure-cli"></a><a id="cli-mongodb"></a>Maken met behulp van Azure CLI

[Maak een Cassandra-tabel met Azure cli](./scripts/cli/cassandra/create.md). Zie [Azure CLI-voor beelden voor Azure Cosmos DB](cli-samples.md)voor een overzicht van alle Azure CLI-voor beelden in alle Azure Cosmos DB api's.

## <a name="create-using-powershell"></a>Maken met PowerShell

[Maak een Cassandra-tabel met Power shell](./scripts/powershell/cassandra/create.md). Zie [Power shell](powershell-samples.md) -voor beelden voor een lijst met alle Power shell-voor beelden in alle Azure Cosmos DB api's

## <a name="next-steps"></a>Volgende stappen

* [Partitionering in Azure Cosmos DB](partitioning-overview.md)
* [Aanvraageenheden in Azure Cosmos DB](request-units.md)
* [Doorvoer voor containers en databases inrichten](set-throughput.md)
* [Werken met een Azure Cosmos-account](./account-databases-containers-items.md)