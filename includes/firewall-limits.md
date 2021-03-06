---
title: Include-bestand
description: bestand opnemen
services: firewall
author: vhorne
ms.service: firewall
ms.topic: include
ms.date: 11/06/2020
ms.author: victorh
ms.custom: include file
ms.openlocfilehash: d479c3087b971aa17cf145e0111890da07381eab
ms.sourcegitcommit: 8a1ba1ebc76635b643b6634cc64e137f74a1e4da
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/09/2020
ms.locfileid: "94386574"
---
| Resource | Limiet |
| --- | --- |
| Gegevensdoorvoer |30 Gbps<sup>1</sup> |
|Regels|10.000. Alle regeltypen gecombineerd.|
|Maximaal aantal DNAT-regels|298 voor één openbaar IP-adres.<br>Eventuele extra openbare IP-adressen dragen bij aan de beschikbare SNAT-poorten, maar verminderen het aantal beschikbare DNAT-regels. Zo zijn bij twee openbare IP-adressen bijvoorbeeld 297 DNAT-regels mogelijk. Als het protocol van een regel is geconfigureerd voor zowel TCP als UDP, telt dit als twee regels.|
|Minimale AzureFirewallSubnet-grootte |/26|
|Poortbereik in netwerk- en toepassingsregels|1 - 65535|
|Openbare IP-adressen|maximaal 250. Alle openbare IP-adressen kunnen worden gebruikt in DNAT-regels en ze dragen allemaal bij aan de beschikbare SNAT-poorten.|
|IP-adressen in IP-groepen|Maximaal 100 IP-groepen per firewall.<br>Maximaal 5000 afzonderlijke IP-adressen of IP-voorvoegsels per IP-groep.
|Routetabel|AzureFirewallSubnet heeft standaard een 0.0.0.0/0-route waarbij de NextHopType-waarde is ingesteld op **Internet**.<br><br>Azure Firewall moet een directe verbinding met internet hebben. Als uw AzureFirewallSubnet een standaardroute naar uw on-premises netwerk via BGP leert, moet u deze overschrijven met een UDR van 0.0.0.0/0 met de waarde **NextHopType** ingesteld op **Internet** om directe verbinding met internet te houden. Standaard biedt Azure Firewall geen ondersteuning voor geforceerde tunneling naar een on-premisesnetwerk.<br><br>Als uw configuratie echter geforceerde tunneling voor een on-premisesnetwerk vereist, zal Microsoft deze per geval ondersteunen. Neem contact op met het ondersteuningsteam zodat we uw aanvraag kunnen controleren. Als u dit hebt geaccepteerd, wordt uw abonnement toegestaan en wordt de vereiste firewallinternetverbinding onderhouden.|
|FQDN's in netwerkregels|Voor goede prestaties moet u per firewall niet meer dan 1000 FQDN's overschrijden in alle netwerkregels.|

<sup>1</sup>als u deze limieten wilt verhogen, neemt u contact op met ondersteuning voor Azure.
