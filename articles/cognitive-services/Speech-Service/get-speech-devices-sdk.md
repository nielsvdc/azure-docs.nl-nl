---
title: De Speech Devices SDK ophalen
titleSuffix: Azure Cognitive Services
description: De speech-service werkt met een groot aantal verschillende apparaten en audio bronnen. Nu kunt u uw spraak toepassingen naar een hoger niveau brengen met overeenkomende hardware en software. In dit artikel leert u hoe u toegang krijgt tot de speech-apparaten SDK en hoe u kunt ontwikkelen.
services: cognitive-services
author: erhopf
manager: nitinme
ms.service: cognitive-services
ms.subservice: speech-service
ms.topic: conceptual
ms.date: 04/14/2019
ms.author: erhopf
ms.openlocfilehash: 0bc1a7b5e443de0c1a95fa209d2e5a280cf28ef2
ms.sourcegitcommit: 829d951d5c90442a38012daaf77e86046018e5b9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/09/2020
ms.locfileid: "87385837"
---
# <a name="get-the-cognitive-services-speech-devices-sdk"></a>De SDK voor Cognitive Services speech-apparaten ophalen

De SDK voor spraak apparaten is een vooraf geclusterde bibliotheek die is ontworpen om te werken met doel ontwikkelde ontwikkel kits en verschillende matrix configuraties van microfoons.

## <a name="choose-a-development-kit"></a>Een Development Kit kiezen

|Apparaten|Specificatie|Beschrijving|Scenario's|
|--|--|--|--|
|[Urbetter dev kit](http://www.urbetter.com/products_56/278.html) ![ URbetter DDK](media/speech-devices-sdk/device-urbetter.jpg)|7-microfoon matrix, ARM SOC, WIFI, Ethernet, HDMI, USB-camera. <br>Linux|De SDK voor spraak apparaten op branche niveau die micro soft Mic-matrix aanpast en ondersteuning biedt voor uitgebreide I/O, zoals HDMI/Ethernet en meer USB-rand apparatuur <br> [Contact opnemen met Urbetter](http://www.urbetter.com/products_56/278.html)|Transcriptie, onderwijs, zieken huis, robots, OTT box, Voice agent, drive t/m|
|[Roobo slimme audio dev kit](http://ddk.roobo.com)<br>[Setup](speech-devices-sdk-roobo-v1.md)  /  [Snelstartgids](speech-devices-sdk-android-quickstart.md) ![ Roobo slimme audio dev kit](media/speech-devices-sdk/device-roobo-v1.jpg)|7-Mic-matrix, ARM SOC, WIFI, audio out, IO. <br>[Android](speech-devices-sdk-android-quickstart.md)|De eerste speech-apparaten SDK voor het aanpassen van micro soft Mic-matrix en front processing SDK, voor het ontwikkelen van transcriptie-en spraak scenario's van hoge kwaliteit|Conversation transcriptie, Smart spreker, Voice agent, wearable|
|[Azure Kinect DK](https://azure.microsoft.com/services/kinect-dk/)<br>[Setup](https://docs.microsoft.com/azure/Kinect-dk/set-up-azure-kinect-dk)  /  [Snelstartgids](speech-devices-sdk-windows-quickstart.md) ![ Azure Kinect DK](media/speech-devices-sdk/device-azure-kinect-dk.jpg)|7-microfoon matrix RGB en diepte camera's. <br>[Windows](speech-devices-sdk-windows-quickstart.md) / [Linux](speech-devices-sdk-linux-quickstart.md)|Een Developer Kit met geavanceerde kunst matige intelligentie (AI) Sens oren voor het bouwen van geavanceerde computer vision-en spraak modellen. Het combineert een ' best-in-class ' ruimtelijke microfoon matrix en diepte camera met een video camera en afdruk stand-sensor, allemaal op één klein apparaat met meerdere modi, opties en Sdk's om een bereik van reken typen te bieden.|Conversation transcriptie, Robotics, slim bouwen|
|Roobo slimme audio dev kit 2<br>[Installatie](speech-devices-sdk-roobo-v2.md)<br>![Roobo slimme audio dev kit 2](media/speech-devices-sdk/device-roobo-v2.jpg)|7-Mic-matrix, ARM SOC, WIFI, Bluetooth, IO. <br>Linux|De tweede generatie speech-apparaten SDK die alternatieve besturings systemen en meer functies biedt in een kosteneffectd referentie ontwerp.|Conversation transcriptie, Smart spreker, Voice agent, wearable|


## <a name="download-the-speech-devices-sdk"></a>De speech-apparaten-SDK downloaden

Down load de [SDK voor spraak apparaten](https://aka.ms/sdsdk-download).

## <a name="next-steps"></a>Volgende stappen

> [!div class="nextstepaction"]
> [Aan de slag met de SDK voor spraak apparaten](https://aka.ms/sdsdk-quickstart)
