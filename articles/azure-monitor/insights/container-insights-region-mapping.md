---
title: Azure Monitor voor de regio toewijzingen voor containers
description: Hierin worden de regio toewijzingen beschreven die worden ondersteund tussen Azure Monitor voor containers, Log Analytics werk ruimte en aangepaste metrische gegevens.
ms.topic: conceptual
ms.date: 09/22/2020
ms.custom: references_regions
ms.openlocfilehash: 9e3b8635c70dfdf33b0a062be80c948cd77923cc
ms.sourcegitcommit: 829d951d5c90442a38012daaf77e86046018e5b9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/09/2020
ms.locfileid: "91272902"
---
# <a name="region-mappings-supported-by-azure-monitor-for-containers"></a>Regio toewijzingen die worden ondersteund door Azure Monitor voor containers

 Als Azure Monitor voor containers wordt ingeschakeld, worden alleen bepaalde regio's ondersteund voor het koppelen van een Log Analytics-werk ruimte en een AKS-cluster en het verzamelen van aangepaste metrische gegevens die aan Azure Monitor zijn verzonden.

## <a name="log-analytics-workspace-supported-mappings"></a>Ondersteunde toewijzingen Log Analytics werk ruimte

Ondersteunde AKS regio's worden vermeld in [beschik bare producten per regio](https://azure.microsoft.com/global-infrastructure/services/?products=kubernetes-service). De Log Analytics-werk ruimte moet zich in dezelfde regio bevinden, met uitzonde ring van de regio's die in de volgende tabel worden weer gegeven. Bekijk [opmerkingen](https://github.com/Azure/AKS/releases) bij de release van AKS voor updates.


|**AKS-cluster regio** | **Log Analytics werkruimte regio** |
|-----------------------|------------------------------------|
|**Afrika** | |
|SouthAfricaNorth |West-Europa |
|SouthAfricaWest |West-Europa |
|**Australië** | |
|AustraliaCentral2 |AustraliaCentral |
|**Brazilië** | |
|BrazilSouth | SouthCentralUS |
|**Canada** ||
|CanadaEast |CanadaCentral |
|**Europa** | |
|FranceSouth |FranceCentral |
|UKWest |UKSouth |
|**India** | |
|SouthIndia |CentralIndia |
|WestIndia |CentralIndia |
|**Japan** | |
|JapanWest |JapanEast |
|**Korea** | |
|KoreaSouth |KoreaCentral |
|**VS** | |
|WestCentralUS<sup>1</sup>|Oost,<sup>1</sup>|


<sup>1</sup> vanwege capaciteits beperkingen is de regio niet beschikbaar bij het maken van nieuwe resources. Dit omvat een Log Analytics-werk ruimte. Bestaande gekoppelde resources in de regio moeten echter blijven werken.

## <a name="custom-metrics-supported-regions"></a>Ondersteunde regio's voor aangepaste metrische gegevens

Het verzamelen van metrische gegevens van knoop punten van Azure Kubernetes Services (AKS)-clusters en peulen wordt alleen ondersteund voor publicatie als aangepaste metrische gegevens in de volgende [Azure-regio's](../platform/metrics-custom-overview.md#supported-regions).

## <a name="next-steps"></a>Volgende stappen

Als u wilt beginnen met het bewaken van uw AKS-cluster, raadpleegt u [How to Enable the Azure monitor for containers](container-insights-onboard.md) voor meer informatie over de vereisten en beschik bare methoden voor het inschakelen van  
