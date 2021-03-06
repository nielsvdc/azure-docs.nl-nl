---
title: PowerShell-script voor het maken van een keyspace en tabel voor Azure Cosmos DB Cassandra-API
description: Azure PowerShell-script - keyspace en tabel maken voor Azure Cosmos DB Cassandra-API
author: markjbrown
ms.service: cosmos-db
ms.subservice: cosmosdb-cassandra
ms.topic: sample
ms.date: 05/13/2020
ms.author: mjbrown
ms.openlocfilehash: 127810bcd7a775e10f00612efd1f1519e8e7fc6e
ms.sourcegitcommit: 3bdeb546890a740384a8ef383cf915e84bd7e91e
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/30/2020
ms.locfileid: "93099620"
---
# <a name="create-a-keyspace-and-table-for-azure-cosmos-db---cassandra-api"></a>Een keyspace en tabel maken voor Azure Cosmos DB - Cassandra-API
[!INCLUDE[appliesto-cassandra-api](../../../includes/appliesto-cassandra-api.md)]

[!INCLUDE [updated-for-az](../../../../../includes/updated-for-az.md)]

[!INCLUDE [sample-powershell-install](../../../../../includes/sample-powershell-install-no-ssh.md)]

## <a name="sample-script"></a>Voorbeeldscript

[!code-powershell[main](../../../../../powershell_scripts/cosmosdb/cassandra/ps-cassandra-create.ps1 "Create a keyspace and table for Cassandra API")]

## <a name="clean-up-deployment"></a>Opschonen van implementatie

Na het uitvoeren van het voorbeeldscript kan de volgende opdracht worden gebruikt om de resourcegroep en alle resources die er aan zijn gekoppeld te verwijderen.

```powershell
Remove-AzResourceGroup -ResourceGroupName "myResourceGroup"
```

## <a name="script-explanation"></a>Uitleg van het script

In dit script worden de volgende opdrachten gebruikt. Elke opdracht in de tabel is een koppeling naar specifieke documentatie over de opdracht.

| Opdracht | Opmerkingen |
|---|---|
|**Azure Cosmos DB**| |
| [New-AzCosmosDBAccount](/powershell/module/az.cosmosdb/new-azcosmosdbaccount) | Hiermee maakt u een Cosmos DB-account. |
| [New-AzCosmosDBCassandraKeyspace](/powershell/module/az.cosmosdb/new-azcosmosdbcassandrakeyspace) | Hiermee maakt u een Cosmos DB Cassandra-API-keyspace. |
| [New-AzCosmosDBCassandraClusterKey](/powershell/module/az.cosmosdb/new-azcosmosdbcassandraclusterkey) | Hiermee maakt u een Cosmos DB Cassandra-API-clustersleutel. |
| [New-AzCosmosDBCassandraColumn](/powershell/module/az.cosmosdb/new-azcosmosdbcassandracolumn) | Hiermee maakt u een Cosmos DB Cassandra-API-kolom. |
| [New-AzCosmosDBCassandraSchema](/powershell/module/az.cosmosdb/new-azcosmosdbcassandraschema) | Hiermee maakt u een Cosmos DB Cassandra-API-schema. |
| [New-AzCosmosDBCassandraTable](/powershell/module/az.cosmosdb/new-azcosmosdbcassandratable) | Hiermee maakt u een Cosmos DB Cassandra-API-tabel. |
|**Azure-resourcegroepen**| |
| [Remove-AzResourceGroup](/powershell/module/az.resources/remove-azresourcegroup) | Hiermee verwijdert u een resourcegroep met inbegrip van alle geneste resources. |
|||

## <a name="next-steps"></a>Volgende stappen

Zie [Documentatie over Azure PowerShell](/powershell/) voor meer informatie over Azure PowerShell.