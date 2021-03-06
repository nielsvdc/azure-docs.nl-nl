---
title: Problemen met connectiviteit tussen Synapse Studio en Storage oplossen
description: Problemen met connectiviteit tussen Synapse Studio en Storage oplossen
author: saveenr
ms.service: synapse-analytics
ms.topic: conceptual
ms.date: 11/11/2020
ms.author: xujiang1
ms.reviewer: jrasnick
ms.openlocfilehash: 0b8a64d24242e6fb34c963b14429fdfee2398f62
ms.sourcegitcommit: dc342bef86e822358efe2d363958f6075bcfc22a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/12/2020
ms.locfileid: "94557676"
---
# <a name="troubleshoot-connectivity-between-azure-synapse-analytics-synapse-studio-and-storage"></a>Problemen met de verbinding tussen Azure Synapse Analytics Synapse Studio en Storage oplossen

In Synapse Studio (preview) kunt u gegevens bronnen verkennen die zich in uw gekoppelde opslag bevinden. Deze hand leiding helpt u bij het oplossen van verbindings problemen wanneer u toegang probeert te krijgen tot uw gegevens bronnen. 

## <a name="case-1-storage-account-lacks-proper-permissions"></a>Case #1: het opslag account heeft geen de juiste machtigingen

Als uw opslag account niet over de juiste machtigingen beschikt, kunt u de opslag structuur niet uitbreiden via ' gegevens '--> ' gekoppeld ' in Synapse Studio. Bekijk de scherm opname van het probleem symptoom hieronder. 

Het gedetailleerde fout bericht kan verschillen, maar de algemene betekenis van het fout bericht is: "deze aanvraag is niet gemachtigd om deze bewerking uit te voeren.".

![Probleem met opslag connectiviteit 1](media/troubleshoot-synapse-studio-and-storage-connectivity/storage-connectivity-issue.1.png)

**Oplossing** : zie [de Azure Portal gebruiken om een Azure-rol toe te wijzen voor toegang tot Blob-en wachtrij gegevens](../../storage/common/storage-auth-aad-rbac-portal.md) om uw account toe te wijzen aan de juiste rol.


## <a name="case-2-failed-to-send-the-request-to-storage-server"></a>Case #2: verzenden van de aanvraag naar de opslag server is mislukt

Wanneer u de pijl selecteert om de opslag structuur uit te breiden in ' gegevens '--> ' gekoppeld ' in Synapse Studio, ziet u mogelijk het probleem ' REQUEST_SEND_ERROR ' in het linkerdeel venster. Bekijk de scherm opname van het probleem symptoom hieronder:

![Probleem met opslag connectiviteit 2](media/troubleshoot-synapse-studio-and-storage-connectivity/storage-connectivity-issue.2.png)

Er kunnen verschillende mogelijke redenen zijn om dit probleem op te lossen:

### <a name="the-storage-resource-is-behind-a-vnet-and-a-storage-private-endpoint-needs-to-configure"></a>De opslag Resource bevindt zich achter een vNet en een persoonlijk eind punt voor opslag moet worden geconfigureerd

**Oplossing** : in dit geval moet u het persoonlijke eind punt voor opslag configureren voor uw opslag account. Zie [de Azure Portal gebruiken om een Azure-rol toe te wijzen voor toegang tot Blob-en wachtrij gegevens](../security/how-to-connect-to-workspace-from-restricted-network.md)voor meer informatie over het configureren van het persoonlijke opslag eindpunt voor vNet.

U kunt de opdracht ' nslookup \<storage-account-name\> . DFS.core.Windows.net ' gebruiken om de connectiviteit te controleren nadat het persoonlijke opslag eindpunt is geconfigureerd. Deze moet een teken reeks retour neren die lijkt op: ' \<storage-account-name\> . privatelink.DFS.core.Windows.net '.

### <a name="the-storage-resource-is-not-behind-a-vnet-but-the-blob-service-azure-ad-endpoint-is-not-accessible-due-to-firewall-configured"></a>De opslag Resource bevindt zich niet achter een vNet, maar het Blob service-eind punt (Azure AD) is niet toegankelijk omdat de firewall is geconfigureerd

**Oplossing** : in dit geval moet u uw opslag account openen in de Azure Portal. Schuif in het linkernavigatievenster omlaag naar **ondersteuning en probleem oplossing** en selecteer **connectiviteits controle** om de verbindings status van de **BLOB service (Azure AD)** te controleren. Als deze niet toegankelijk is, volgt u de gepromoveerde gids voor het controleren van de **firewalls en configuratie van virtuele netwerken** op de pagina van uw opslag account. Zie [Azure Storage firewalls en virtuele netwerken configureren](../../storage/common/storage-network-security.md)voor meer informatie over opslag firewalls.

### <a name="other-issues-to-check"></a>Andere te controleren problemen 

* De opslag resource die u wilt openen, is Azure Data Lake Storage Gen2 en bevindt zich achter een firewall en een vNet (waarbij het persoonlijke opslag eindpunt is geconfigureerd).
* De container resource die u wilt openen, is verwijderd of bestaat niet.


## <a name="next-steps"></a>Volgende stappen
Als de vorige stappen niet helpen om uw probleem op te lossen, [maakt u een ondersteunings ticket](../../sql-data-warehouse/sql-data-warehouse-get-started-create-support-ticket.md).
