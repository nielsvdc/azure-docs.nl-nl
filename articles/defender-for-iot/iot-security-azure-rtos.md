---
title: Overzicht van de beveiligings module voor Azure RTO'S
description: Meer informatie over de beveiligings module voor Azure RTO'S-ondersteuning en-implementatie als onderdeel van Azure Defender voor IoT.
services: defender-for-iot
ms.service: defender-for-iot
documentationcenter: na
author: mlottner
manager: rkarlin
editor: ''
ms.devlang: na
ms.topic: conceptual
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 09/07/2020
ms.author: mlottner
ms.openlocfilehash: ec314a729914fee26d30165c9df1644bde3845aa
ms.sourcegitcommit: 83610f637914f09d2a87b98ae7a6ae92122a02f1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "91995488"
---
# <a name="overview-defender-for-iot-security-module-for-azure-rtos-preview"></a>Overzicht: Defender voor IoT Security module voor Azure RTO'S (preview)

De beveiligings module van Azure Defender voor IoT biedt een uitgebreide beveiligings oplossing voor apparaten die gebruikmaken van Azure RTO'S. Het biedt dekking voor veelvoorkomende bedreigingen en mogelijke schadelijke activiteiten op real-time besturings systemen (RTO'S). Azure RTO'S wordt nu geleverd met de ingebouwde Azure IoT-beveiligings module.

![Visualisatie van Defender voor IoT Azure RTO'S.](./media/architecture/azure-rtos-security-monitoring.png)


De beveiligings module voor Azure RTO'S biedt de volgende functies:

- Detectie van schadelijke netwerk activiteiten
- Gedrag van op aangepaste waarschuwingen gebaseerd apparaat basis lijnen
- Verbeterde beveiligings hygiëne van het apparaat

## <a name="detect-malicious-network-activities"></a>Schadelijke netwerk activiteiten detecteren

De inkomende en uitgaande netwerk activiteit van elk apparaat wordt gecontroleerd. Ondersteunde protocollen zijn TCP, UDP en ICMP op IPv4 en IPv6. Met Defender voor IoT worden elk van deze netwerk activiteiten gecontroleerd op basis van de micro soft Threat Intelligence-feed. De feed wordt in realtime bijgewerkt met miljoenen unieke bedreigings indicatoren die wereld wijd zijn verzameld.

## <a name="device-behavior-baselining-based-on-custom-alerts"></a>Gedrag van het apparaat basis lijnen op basis van aangepaste waarschuwingen

Basis lijnen maakt het mogelijk om apparaten te clusteren in beveiligings groepen en het verwachte gedrag van elke groep te definiëren. Omdat IoT-apparaten doorgaans zijn ontworpen om te functioneren in goed gedefinieerde en beperkte scenario's, is het eenvoudig om een basis lijn te maken die het verwachte gedrag definieert met behulp van een set para meters. Eventuele afwijkingen van de basis lijn activeren een waarschuwing.

## <a name="improve-your-device-security-hygiene"></a>Verbeter de beveiligings hygiëne van uw apparaat

Door gebruik te maken van de aanbevolen infra structuur voor IoT kunt u kennis en inzichten krijgen over problemen in uw omgeving die van invloed zijn op de beveiligings postuur van uw apparaten. Een zwakke IoT-postuur voor beveiliging kan leiden tot een geslaagde aanval als deze ongewijzigd blijft. Beveiliging wordt altijd gemeten door de zwakkere koppeling binnen een organisatie.

## <a name="get-started-protecting-azure-rtos-devices"></a>Aan de slag met het beveiligen van Azure RTO'S-apparaten

De beveiligings module voor Azure RTO'S is beschikbaar als gratis down load voor uw apparaten. De Defender voor IoT-Cloud service is beschikbaar met een proef versie van 30 dagen per Azure-abonnement. Down load de [beveiligings module voor Azure rto's](https://github.com/MicrosoftDocs/azure-docs/blob/master/articles/defender-for-iot/iot-security-azure-rtos.md)om aan de slag te gaan. 

## <a name="next-steps"></a>Volgende stappen

In dit artikel hebt u geleerd over de beveiligings module voor Azure RTO'S. Raadpleeg de volgende artikelen voor meer informatie over de beveiligings module en aan de slag:

- [Concepten van Azure RTO'S IoT Security module](concept-rtos-security-module.md)
- [Snelstartgids: Azure RTO'S IoT Security module](quickstart-azure-rtos-security-module.md)
