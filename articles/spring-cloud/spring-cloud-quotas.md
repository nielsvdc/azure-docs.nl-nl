---
title: Service plannen en quota's voor Azure lente-Cloud
description: Meer informatie over service quota's en service plannen voor Azure lente Cloud
author: bmitchell287
ms.service: spring-cloud
ms.topic: conceptual
ms.date: 11/04/2019
ms.author: brendm
ms.custom: devx-track-java
ms.openlocfilehash: 496f2e812a102e85fea92a535552daaaadf5f31e
ms.sourcegitcommit: 30505c01d43ef71dac08138a960903c2b53f2499
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2020
ms.locfileid: "92093426"
---
# <a name="quotas-and-service-plans-for-azure-spring-cloud"></a>Quota's en service plannen voor Azure lente-Cloud

**Dit artikel is van toepassing op:** ✔️ Java ✔️ C#

Alle Azure-Services hebben standaard limieten en-quota ingesteld voor resources en functies.   Azure lente-Cloud biedt twee prijs Categorieën: Basic en Standard. In dit artikel worden de limieten voor beide lagen weer gegeven.

## <a name="azure-spring-cloud-service-tiers-and-limits"></a>Azure lente-Cloud service lagen en-limieten

| Resource | Basic | Standard
------- | ------- | -------
vCPU | 1 per service-exemplaar | 4 per service-exemplaar
Geheugen | 2 GB per service-exemplaar | 8 GB per service-exemplaar
Azure veer Cloud service-instanties per regio per abonnement | 10 | 10
Totaal aantal app-exemplaren per Azure veer Cloud service-exemplaar | 25 | 500
Permanente volumes | 1 GB/app x 10 apps | 50 GB/app x 10-apps

## <a name="next-steps"></a>Volgende stappen

Enkele standaard limieten kunnen worden verhoogd. Als uw installatie een verhoging vereist, [maakt u een ondersteunings aanvraag](../azure-portal/supportability/how-to-create-azure-support-request.md).