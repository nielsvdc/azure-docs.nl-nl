---
title: Linux-Vm's samen zoeken
description: Meer informatie over het co-locatie van Azure VM-resources voor Linux kan de latentie verbeteren.
ms.service: virtual-machines
ms.topic: conceptual
ms.date: 10/30/2019
ms.author: zivr
ms.openlocfilehash: 822d67211982526bdd7a36cb5922f33b448eb7c7
ms.sourcegitcommit: d103a93e7ef2dde1298f04e307920378a87e982a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "91973373"
---
# <a name="co-locate-resources-for-improved-latency"></a>Resources gecombineerd zoeken voor verbeterde latentie

Wanneer u uw toepassing in azure implementeert, wordt er netwerk latentie gemaakt, wat van invloed kan zijn op de algehele prestaties van uw toepassing. 

## <a name="proximity-placement-groups"></a>Nabijheidsplaatsingsgroepen

[!INCLUDE [virtual-machines-common-ppg-overview](../../../includes/virtual-machines-common-ppg-overview.md)]

## <a name="next-steps"></a>Volgende stappen

Implementeer een virtuele machine op een [proximity-plaatsings groep](proximity-placement-groups.md) met behulp van de Azure cli.

Meer informatie over het testen van de [netwerk latentie](../../virtual-network/virtual-network-test-latency.md?toc=%252fazure%252fvirtual-machines%252flinux%252ftoc.json).

Meer informatie over het optimaliseren van de [netwerk doorvoer](../../virtual-network/virtual-network-optimize-network-bandwidth.md?toc=%2fazure%2fvirtual-machines%2flinux%2ftoc.json).  

Meer informatie over het [gebruik van proximity-plaatsings groepen met SAP-toepassingen](../workloads/sap/sap-proximity-placement-scenarios.md?toc=%2fazure%2fvirtual-machines%2flinux%2ftoc.json).