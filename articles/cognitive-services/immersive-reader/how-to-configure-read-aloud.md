---
title: Hardop voorlezen configureren
titleSuffix: Azure Cognitive Services
description: In dit artikel wordt uitgelegd hoe u de verschillende opties configureert voor hardop voor lezen.
author: metanMSFT
manager: guillasi
ms.service: cognitive-services
ms.subservice: immersive-reader
ms.topic: conceptual
ms.date: 06/29/2020
ms.author: metang
ms.openlocfilehash: 648227521e5e4e8feecd864d3e572a4758e551ca
ms.sourcegitcommit: fb3c846de147cc2e3515cd8219d8c84790e3a442
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92633260"
---
# <a name="how-to-configure-read-aloud"></a>Hardop voor lezen configureren

In dit artikel wordt beschreven hoe u de verschillende opties voor hardop lezen in de insluitende lezer kunt configureren.

## <a name="automatically-start-read-aloud"></a>Hardop voor lezen automatisch starten

De `options` para meter bevat alle vlaggen die kunnen worden gebruikt voor het configureren van hardop voor lezen. Instellen `autoplay` op `true` om automatisch starten van hardop voor lezen in te scha kelen na het starten van de insluitende lezer.

```typescript
const options = {
    readAloudOptions: {
        autoplay: true
    }
};

ImmersiveReader.launchAsync(YOUR_TOKEN, YOUR_SUBDOMAIN, YOUR_DATA, options);
```

> [!NOTE]
> Vanwege beperkingen van de browser wordt automatisch afspelen niet ondersteund in Safari.

## <a name="configure-the-voice"></a>De stem configureren

Ingesteld `voice` op `male` of `female` . Niet alle talen ondersteunen beide stemmen. Zie de pagina [taal ondersteuning](./language-support.md) voor meer informatie.

```typescript
const options = {
    readAloudOptions: {
        voice: 'female'
    }
};
```

## <a name="configure-playback-speed"></a>Afspeel snelheid configureren

Ingesteld `speed` op een getal tussen `0.5` (50%) en `2.5` (250%) tot. Waarden buiten dit bereik worden geschroefd tot 0,5 of 2,5.

```typescript
const options = {
    readAloudOptions: {
        speed: 1.5
    }
};
```

## <a name="next-steps"></a>Volgende stappen

* Lees de [naslagdocumentatie voor de Immersive Reader-SDK](./reference.md).