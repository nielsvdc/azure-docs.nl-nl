---
title: Gegevens redundantie in Azure Data Factory | Microsoft Docs
description: Meer informatie over de mechanismen voor redundantie van meta gegevens in Azure Data Factory
services: data-factory
documentationcenter: ''
author: nabhishek
manager: weehyongtok
ms.reviewer: abnarain
ms.service: data-factory
ms.workload: data-services
ms.tgt_pltfrm: na
ms.topic: conceptual
ms.date: 11/05/2020
ms.author: abnarain
ms.openlocfilehash: f71fdf66624d67939f915f91c2cc1dbe7553cad7
ms.sourcegitcommit: 46c5ffd69fa7bc71102737d1fab4338ca782b6f1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/06/2020
ms.locfileid: "94332071"
---
# <a name="azure-data-factory-data-redundancy"></a>**Gegevens redundantie Azure Data Factory**

Azure Data Factory gegevens bevatten meta gegevens (pijp lijn, gegevens sets, gekoppelde services, Integration runtime en triggers) en bewakings gegevens (pijp lijn-, trigger-en activiteit uitvoeringen). 

In alle regio's (met uitzonde ring van Brazilië-zuid en Zuidoost-Azië) worden Azure Data Factory gegevens opgeslagen en gerepliceerd in het [gekoppelde gebied](https://docs.microsoft.com/azure/best-practices-availability-paired-regions#azure-regional-pairs) om te beschermen tegen verlies van meta gegevens. Tijdens regionale datacenter fouten kan micro soft een regionale failover van uw Azure Data Factory-exemplaar initiëren. In de meeste gevallen is er geen actie vereist voor uw onderdeel. Wanneer de door micro soft beheerde failover is voltooid, kunt u toegang krijgen tot uw Azure Data Factory in de failover-regio. 

Als gevolg van de vereisten voor gegevens locatie in Brazilië-zuid en Zuidoost-Azië, worden Azure Data Factory gegevens [alleen in lokale regio](https://docs.microsoft.com/azure/storage/common/storage-redundancy#locally-redundant-storage)opgeslagen. Voor Zuidoost-Azië worden alle gegevens opgeslagen in Singapore. Voor Brazilië-zuid worden alle gegevens opgeslagen in Brazilië. Als de regio is verwijderd vanwege een aanzienlijke nood geval, kan micro soft uw Azure Data Factory gegevens niet herstellen.  

> [!NOTE]
> Door micro soft beheerde failover is niet van toepassing op zelf-hostende Integration runtime (SHIR), omdat deze infra structuur doorgaans door de klant wordt beheerd. Als de SHIR is ingesteld op Azure VM, is de aanbeveling om [Azure site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) te gebruiken voor het verwerken van de failover van de [Azure-VM](https://docs.microsoft.com/azure/site-recovery/azure-to-azure-architecture) naar een andere regio.



## <a name="using-source-control-in-azure-data-factory"></a>**Broncode beheer gebruiken in Azure Data Factory**

Om ervoor te zorgen dat u de wijzigingen die zijn aangebracht in uw Azure data factory meta gegevens kunt bijhouden en controleren, kunt u overwegen om het bron beheer voor uw Azure Data Factory in te stellen. U kunt hiermee ook toegang krijgen tot uw JSON-bestanden met meta gegevens voor pijp lijnen, gegevens sets, gekoppelde services en triggers. Met Azure Data Factory kunt u werken met een andere Git-opslag plaats (Azure DevOps en GitHub). 

 Meer informatie over het instellen van [broncode beheer in azure Data Factory](https://docs.microsoft.com/azure/data-factory/source-control). 

> [!NOTE]
> In het geval van een ramp (verlies van regio) kunnen nieuwe data factory hand matig of op een geautomatiseerde manier worden ingericht. Zodra de nieuwe data factory is gemaakt, kunt u uw pijp lijnen, gegevens sets en gekoppelde services JSON herstellen vanuit de bestaande Git-opslag plaats. 



## <a name="data-stores"></a>**Gegevensopslag**

Met Azure Data Factory kunt u gegevens verplaatsen tussen gegevens archieven die zich lokaal en in de cloud bevinden. Als u de bedrijfs continuïteit wilt garanderen met uw gegevens archieven, raadpleegt u de aanbevelingen voor bedrijfs continuïteit voor elk van deze gegevens archieven. 

 

## <a name="see-also"></a>Zie ook

- [Azure-regionale paren](https://docs.microsoft.com/azure/best-practices-availability-paired-regions)
- [Gegevens locatie in azure](https://azure.microsoft.com/global-infrastructure/data-residency/) 
