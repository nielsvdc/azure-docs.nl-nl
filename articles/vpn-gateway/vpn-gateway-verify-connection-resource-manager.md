---
title: 'Azure VPN Gateway: een gateway verbinding controleren'
description: In dit artikel leest u hoe u een virtueel netwerk VPN Gateway verbinding kunt controleren.
services: vpn-gateway
author: cherylmc
ms.service: vpn-gateway
ms.topic: how-to
ms.date: 10/19/2020
ms.author: cherylmc
ms.custom: devx-track-azurecli
ms.openlocfilehash: fef9eb49b10008c86ee044a199ae69a43585f4f3
ms.sourcegitcommit: 8d8deb9a406165de5050522681b782fb2917762d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/20/2020
ms.locfileid: "92217936"
---
# <a name="verify-a-vpn-gateway-connection"></a>Een VPN Gateway verbinding controleren

In dit artikel leest u hoe u een VPN-gateway verbinding kunt controleren voor zowel het klassieke als het Resource Manager-implementatie model.

## <a name="azure-portal"></a>Azure Portal

[!INCLUDE [Azure portal](../../includes/vpn-gateway-verify-connection-portal-rm-include.md)]

## <a name="powershell"></a>PowerShell

Als u een VPN-gateway verbinding wilt controleren voor het Resource Manager-implementatie model met behulp van Power shell, installeert u de nieuwste versie van de [Azure Resource Manager Power shell-cmdlets](/powershell/azure/).

[!INCLUDE [PowerShell](../../includes/vpn-gateway-verify-connection-ps-rm-include.md)]

## <a name="azure-cli"></a>Azure CLI

Als u een VPN-gateway verbinding wilt controleren voor het Resource Manager-implementatie model met behulp van Azure CLI, installeert u de meest recente versie van de [cli-opdrachten](https://docs.microsoft.com/cli/azure/install-azure-cli) (2,0 of hoger).

[!INCLUDE [CLI](../../includes/vpn-gateway-verify-connection-cli-rm-include.md)]

## <a name="azure-portal-classic"></a>Azure Portal (klassiek)

[!INCLUDE [Azure portal](../../includes/vpn-gateway-verify-connection-azureportal-classic-include.md)]

## <a name="powershell-classic"></a>PowerShell (klassiek)

Installeer de nieuwste versies van de Azure PowerShell-cmdlets om uw VPN-gateway verbinding te controleren voor het klassieke implementatie model met behulp van Power shell. Zorg ervoor dat u de [Service Management](/powershell/azure/servicemanagement/install-azure-ps?#azure-service-management-cmdlets) -module downloadt en installeert. Gebruik ' add-AzureAccount ' om u aan te melden bij het klassieke implementatie model.

[!INCLUDE [Classic PowerShell](../../includes/vpn-gateway-verify-connection-ps-classic-include.md)]

## <a name="next-steps"></a>Volgende stappen

* U kunt virtuele machines toevoegen aan uw virtuele netwerken. Zie [Een virtuele machine maken](../virtual-machines/windows/quick-create-portal.md) voor de stappen.
