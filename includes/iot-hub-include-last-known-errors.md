---
title: bestand opnemen
description: bestand opnemen
author: robinsh
ms.service: iot-hub
services: iot-hub
ms.topic: conceptual
ms.date: 04/22/2019
ms.author: robinsh
ms.custom: include file
ms.openlocfilehash: d8583a1fee96d0a6eb3300882b2b115f057cbeec
ms.sourcegitcommit: 3bdeb546890a740384a8ef383cf915e84bd7e91e
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/30/2020
ms.locfileid: "93135923"
---
Als u de [eindpunt status](https://docs.microsoft.com/rest/api/iothub/iothubresource/getendpointhealth#iothubresource_getendpointhealth) in de rest API de status van de eind punten en de laatste bekende fout geeft om de reden voor het identificeren van een eind punt niet in orde is. De volgende tabel bevat de meest voorkomende fouten.

|Laatst bekende fout|Beschrijving/wanneer deze plaatsvindt|Mogelijke beperking|
|-----|-----|-----|
|Wijk|Er is een tijdelijke fout opgetreden en IoT Hub voert de bewerking opnieuw uit.|Bekijk [route-resource logboeken](https://docs.microsoft.com/azure/iot-hub/monitor-iot-hub-reference#routes).|
|InternalError|Er is een fout opgetreden tijdens het leveren van een bericht aan een eind punt.|Dit is een interne uitzonde ring, maar ook de [routes met bron logboeken](https://docs.microsoft.com/azure/iot-hub/monitor-iot-hub-reference#routes).|
|Niet geautoriseerd|IoT Hub is niet gemachtigd om berichten naar het opgegeven eind punt te verzenden.|Controleer of de connection string up-to-date is voor het eind punt. Als deze is gewijzigd, kunt u een update op uw IoT Hub. Als het eind punt beheerde identiteit gebruikt, controleert u of de IoT Hub principal de vereiste machtigingen voor het doel heeft.|
|Beperkt|IoT Hub wordt beperkt tijdens het schrijven van berichten naar het eind punt.|Controleer de beperkings limieten voor het betreffende eind punt. Pas de configuraties voor het eind punt zodanig aan dat deze zo nodig worden geschaald.|
|Time-out|Time-out van bewerking.|Voer de bewerking opnieuw uit.|
|Niet gevonden|Doel resource bestaat niet.|Zorg ervoor dat de doel resource bestaat.|
|Kan de container niet vinden|De opslag container bestaat niet.|Zorg ervoor dat de opslag container bestaat.|
|Container uitgeschakeld|De opslag container is uitgeschakeld.|Zorg ervoor dat de opslag container is ingeschakeld.|
|MaxMessageSizeExceeded|Bericht routering heeft een maximale bericht grootte van 256 KB. de bericht grootte die wordt gerouteerd, overschrijdt deze limiet.|Controleer of de bericht grootte kan worden verminderd met minder toepassings eigenschappen of minder bericht verrijkingen.|
|PartitioningAndDuplicateDetectionNotSupported|Er is geen duplicaten detectie ingeschakeld voor service bus.|Schakel duplicaten detectie uit Service Bus uit of overweeg het gebruik van een entiteit zonder duplicaten detectie.|
|SessionfulEntityNotSupported|Voor service bus zijn mogelijk geen sessies ingeschakeld.|Schakel de sessie uit Service Bus of overweeg het gebruik van een entiteit zonder sessies.|
|NoMatchingSubscriptionsForMessage|Er is geen abonnement op het schrijven van een bericht in het service bus-onderwerp.|Een abonnement maken voor IoT Hub berichten waarnaar moet worden doorgestuurd.|
|EndpointExternallyDisabled|Het eind punt bevindt zich niet in een actieve status, dus IoT Hub kan berichten verzenden.|Schakel het eind punt in om het terug te zetten naar de actieve status.|
|DeviceMaximumQueueDepthExceeded|De service bus-grootte limiet is bereikt.|Overweeg het verwijderen van berichten van de doel Event Hubs zodat nieuwe berichten kunnen worden opgenomen in de Event Hubs.|