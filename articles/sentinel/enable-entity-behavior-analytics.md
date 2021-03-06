---
title: Gebruik de analyse van entiteits gedrag om geavanceerde bedreigingen te detecteren | Microsoft Docs
description: Gedrags analyse van gebruikers en entiteiten inschakelen in azure Sentinel en gegevens bronnen configureren
services: sentinel
documentationcenter: na
author: yelevin
manager: rkarlin
editor: ''
ms.service: azure-sentinel
ms.subservice: azure-sentinel
ms.devlang: na
ms.topic: how-to
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/28/2020
ms.author: yelevin
ms.openlocfilehash: 140228a65be166bc172e81267c4449b49621e02c
ms.sourcegitcommit: 0dcafc8436a0fe3ba12cb82384d6b69c9a6b9536
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94425776"
---
# <a name="enable-user-and-entity-behavior-analytics-ueba-in-azure-sentinel"></a>UEBA (User and entity Behavior Analytics) inschakelen in azure Sentinel 

> [!IMPORTANT]
>
> - De functies UEBA en Entity pages zijn nu **algemeen beschikbaar** in de volgende Azure Sentinel-geografische gebieden en regio's:
>    - Verenigde Staten Geografie
>    - Regio Oost-West
>    - Geografie van Australië
>
> - In alle andere geografische gebieden en regio's blijven deze functies gedurende de **Preview** -periode. Zie de [aanvullende gebruiks voorwaarden voor Microsoft Azure previews](https://azure.microsoft.com/support/legal/preview-supplemental-terms/) voor aanvullende juridische voor waarden die van toepassing zijn op Azure-functies die in bèta, preview of op andere wijze nog niet beschikbaar zijn in algemene Beschik baarheid.

## <a name="prerequisites"></a>Vereisten

Om deze functie in of uit te scha kelen (deze vereisten zijn niet vereist voor het gebruik van de functie):

- Uw gebruiker moet lid zijn van de Azure Active Directory van uw organisatie en geen gast gebruiker.

- Aan uw gebruiker moet de rol van **globale beheerder** of **beveiligings beheerder** zijn toegewezen in azure AD.

- Aan uw gebruiker moet ten minste één van de volgende **Azure-rollen** zijn toegewezen (meer [informatie over Azure RBAC](roles.md)):
    - **Azure Sentinel contributor** op het niveau van de werk ruimte of de resource groep.
    - **Log Analytics Inzender** op het niveau van de resource groep of het abonnement.

- Er mogen geen Azure-resource vergrendelingen op uw werk ruimte worden toegepast. Meer [informatie over het vergren delen van Azure-resources](../azure-resource-manager/management/lock-resources.md).

## <a name="how-to-enable-user-and-entity-behavior-analytics"></a>De analyse van gebruikers-en entiteits gedrag inschakelen

1. Selecteer **entiteit gedrag** in het navigatie menu van de Azure-Sentinel.

1. Schakel onder de kop **deze in** **op aan.**

1. Klik op de knop **gegevens bronnen selecteren** .

1. Schakel in het selectie deel venster **gegevens bron** de selectie vakjes in naast de gegevens bronnen waarvoor u UEBA wilt inschakelen en selecteer vervolgens **Toep assen**.

    > [!NOTE]
    >
    > In de onderste helft van het **selectie deel venster gegevens bron** ziet u een lijst met UEBA-ondersteunde gegevens bronnen die u nog niet hebt ingeschakeld. 
    >
    > Wanneer u UEBA hebt ingeschakeld, hebt u de optie om nieuwe gegevens bronnen te verbinden, zodat ze rechtstreeks vanuit het deel venster gegevens connector kunnen worden UEBA als deze UEBA-compatibel zijn.

1. Selecteer **Ga naar entiteit zoeken**. Hiermee gaat u naar het deel venster entiteit zoeken, dat vanaf nu wordt weer geven wanneer u **entiteit gedrag** kiest in het hoofd menu van Azure.

## <a name="next-steps"></a>Volgende stappen
In dit document hebt u geleerd hoe u UEBA (User and entity Behavior Analytics) inschakelt en configureert in azure Sentinel. Zie de volgende artikelen voor meer informatie over Azure Sentinel:
- Meer informatie over het [verkrijgen van inzicht in uw gegevens en mogelijke bedreigingen](quickstart-get-visibility.md).
- Ga aan de slag met [het detecteren van bedreigingen met Azure Sentinel](tutorial-detect-threats-built-in.md).
