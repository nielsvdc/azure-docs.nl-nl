---
title: Tijdelijke opslag Firewall-instellingen
description: Een instelling voor netwerk firewall van een opslag account kan een fout veroorzaken bij het maken van een Azure Blob-opslag doel in azure HPC-cache. Dit artikel geeft een tijdelijke oplossing voor de beperking tot er een software oplossing is geïmplementeerd.
author: ekpgh
ms.service: hpc-cache
ms.topic: troubleshooting
ms.date: 11/7/2019
ms.author: v-erkel
ms.openlocfilehash: 6916c79e9110a88beff65d487fac72441382c2f4
ms.sourcegitcommit: 829d951d5c90442a38012daaf77e86046018e5b9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/09/2020
ms.locfileid: "87092367"
---
# <a name="work-around-blob-storage-account-firewall-settings"></a>Rond firewallinstellingen van Blob-opslag werken

Een bepaalde instelling die wordt gebruikt in opslag account firewalls kan ertoe leiden dat het maken van het Blob-opslag doel mislukt. Het team van de HPC-cache van Azure werkt aan een software oplossing voor dit probleem, maar u kunt deze omzeilen door de instructies in dit artikel te volgen.

De firewall instelling die alleen toegang toestaat vanuit geselecteerde netwerken kan verhinderen dat de cache een Blob-opslag doel maakt. Deze configuratie bevindt zich op de instellingen pagina **firewalls en virtuele netwerken** van het opslag account.

Het probleem is dat de cache service gebruikmaakt van een verborgen service virtueel netwerk dat losstaat van de klant omgevingen. Het is niet mogelijk dit netwerk expliciet te autoriseren voor toegang tot uw opslag account.

Wanneer u een Blob-opslag doel maakt, gebruikt de cache service dit netwerk om te controleren of de container leeg is. Als de firewall geen toegang toestaat vanuit het verborgen netwerk, mislukt de controle en mislukt het maken van de opslag doel.

U kunt het probleem omzeilen door uw firewall instellingen tijdelijk te wijzigen tijdens het maken van het opslag doel:

1. Ga naar de pagina **firewalls en virtuele netwerken** van het opslag account en wijzig de instelling toegang tot **alle netwerken**toestaan.
1. Maak het Blob-opslag doel in uw Azure HPC-cache.
1. Nadat het opslag doel is gemaakt, wijzigt u de firewall instelling van het account terug naar de **geselecteerde netwerken**.

Azure HPC cache maakt geen gebruik van het virtuele netwerk van de service voor toegang tot het voltooide opslag doel.

[Neem contact op met de service en ondersteuning van micro soft](hpc-cache-support-ticket.md)voor hulp bij deze tijdelijke oplossing.
