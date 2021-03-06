---
title: Overzicht van intentie herkenning-spraak service
titleSuffix: Azure Cognitive Services
description: Met intentie herkenning kunt u de gebruikers doelstellingen herkennen die u vooraf hebt gedefinieerd. Dit artikel bevat een overzicht van de voor delen en mogelijkheden van de intentie herkennings service.
services: cognitive-services
author: v-demjoh
manager: nitinme
ms.service: cognitive-services
ms.subservice: speech-service
ms.topic: conceptual
ms.date: 10/13/2020
ms.author: v-demjoh
keywords: intentieherkenning
ms.openlocfilehash: 0d718459e0fd0ea410232d3a165b560aa8c59cd1
ms.sourcegitcommit: 2989396c328c70832dcadc8f435270522c113229
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "92174634"
---
# <a name="what-is-intent-recognition"></a>Wat is de intentie herkenning?

[!INCLUDE [TLS 1.2 enforcement](../../../includes/cognitive-services-tls-announcement.md)]

In dit overzicht vindt u meer informatie over de voor delen en mogelijkheden van de intentie herkenning. De Speech SDK van Cognitive Services kan voor intentieherkenning worden geïntegreerd met de Language Understanding-service (LUIS). Een intentie is iets dat de gebruiker wil doen: een vlucht reserveren, de weersverwachting controleren of iemand bellen.
Met behulp van de intentie herkenning kunnen uw toepassingen, hulpprogram ma's en apparaten bepalen wat de gebruiker wil initiëren of uitvoeren op basis van de opties die u in LUIS definieert.

## <a name="luis-key-required"></a>De LUIS-sleutel is vereist

* LUIS kan worden geïntegreerd met de Speech-service voor het herkennen van intenties van spraak. U hebt geen abonnement op de Speech-service nodig, alleen op LUIS.
* Herkenning van spraak intentie is geïntegreerd met de SDK. U kunt een LUIS-sleutel gebruiken met de spraak service.
* Intentie herkenning via de Speech SDK wordt [aangeboden in een subset van regio's die worden ondersteund door Luis](https://docs.microsoft.com/azure/cognitive-services/speech-service/regions#intent-recognition).

## <a name="get-started"></a>Aan de slag

Bekijk de [Snelstartgids](quickstarts/intent-recognition.md) om aan de slag te gaan met intentie herkenning.

## <a name="sample-code"></a>Voorbeeldcode

Voorbeeld code voor intentie herkenning:

* [Snelstart: Een vooraf gemaakte app voor huisautomatisering gebruiken](https://docs.microsoft.com/azure/cognitive-services/luis/luis-get-started-create-app)
* [Intenties van gesproken inhoud herkennen met de Speech SDK voor C#](https://docs.microsoft.com/azure/cognitive-services/speech-service/how-to-recognize-intents-from-speech-csharp)
* [Intentie herkenning en andere spraak Services met eenheid in C #](https://github.com/Azure-Samples/cognitive-services-speech-sdk/tree/master/samples/unity/speechrecognizer)
* [Intenties herkennen met Speech SDK voor python](https://github.com/Azure-Samples/cognitive-services-speech-sdk/tree/master/samples/python/console)
* [Intentie herkenning en andere spraak Services met behulp van de Speech SDK voor C++ in Windows](https://github.com/Azure-Samples/cognitive-services-speech-sdk/tree/master/samples/cpp/windows/console)
* [Intentie herkenning en andere spraak Services met behulp van de Speech SDK voor Java op Windows of Linux](https://github.com/Azure-Samples/cognitive-services-speech-sdk/tree/master/samples/java/jre/console)
* [Intentie herkenning en andere spraak Services met behulp van de Speech SDK voor Java script in een webbrowser](https://github.com/Azure-Samples/cognitive-services-speech-sdk/tree/master/samples/js/browser)

## <a name="reference-docs"></a>Naslagdocumentatie

* [Speech-SDK](speech-sdk-reference.md)

## <a name="next-steps"></a>Volgende stappen

* De [Snelstartgids](quickstarts/intent-recognition.md) voor de Intent herkenning volt ooien
* [Verkrijg gratis een spraakserviceabonnementssleutel](overview.md#try-the-speech-service-for-free)
* [De Speech SDK ophalen](speech-sdk.md)
