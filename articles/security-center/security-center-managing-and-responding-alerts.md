---
title: Beveiligingswaarschuwingen beheren in Azure Security Center | Microsoft Docs
description: Dit document bevat informatie over het gebruik van de mogelijkheden van Azure Security Center om beveiligingswaarschuwingen te beheren en hierop te reageren.
services: security-center
documentationcenter: na
author: memildin
manager: rkarlin
ms.assetid: b88a8df7-6979-479b-8039-04da1b8737a7
ms.service: security-center
ms.topic: how-to
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/15/2020
ms.author: memildin
ms.openlocfilehash: 75ca0438336825bf8d4bbdc6e08eca109f430fde
ms.sourcegitcommit: 400f473e8aa6301539179d4b320ffbe7dfae42fe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/28/2020
ms.locfileid: "92785915"
---
# <a name="manage-and-respond-to-security-alerts-in-azure-security-center"></a>Beveiligingswaarschuwingen beheren en erop reageren in Azure Security Center

In dit onderwerp wordt beschreven hoe u de waarschuwingen die u hebt ontvangen, kunt weer geven en verwerken om uw resources te beveiligen. 

* Zie [beveiligings waarschuwings typen](alerts-reference.md)voor meer informatie over de verschillende typen waarschuwingen.
* Zie [how Azure Security Center detecteert en reageert op bedreigingen](security-center-alerts-overview.md)voor een overzicht van de manier waarop Security Center waarschuwingen genereert.

> [!NOTE]
> Als u geavanceerde detectie wilt inschakelen, schakelt u Azure Defender in. Er is een gratis proefversie beschikbaar. Als u een upgrade wilt uitvoeren, selecteert u de prijscategorie in het [beveiligingsbeleid](tutorial-security-policy.md). Zie [Prijsinformatie over Azure Security Center](security-center-pricing.md) voor meer informatie.

## <a name="what-are-security-alerts"></a>Wat zijn beveiligingswaarschuwingen?
Security Center verzamelt, analyseert en integreert automatisch logboekgegevens van uw Azure-resources, het netwerk en verbonden partneroplossingen, zoals firewall- en eindpuntbeveiligingsoplossingen om werkelijke dreigingen te detecteren en fout-positieven te reduceren. In Security Center wordt een lijst met beveiligingswaarschuwingen met prioriteiten weergegeven samen met de informatie die u nodig hebt om snel onderzoek te doen naar het probleem en aanbevelingen voor het herstellen van een aanval.

> [!NOTE]
> Zie [how Azure Security Center detecteert en reageert op bedreigingen](security-center-alerts-overview.md#detect-threats)voor meer informatie over de werking van Security Center detectie mogelijkheden.

## <a name="manage-your-security-alerts"></a>Beveiligings waarschuwingen beheren

1. Ga in het Security Center-dash board naar de tegel  **bedreigings beveiliging** om de waarschuwingen weer te geven en te bekijken.

    ![De tegel Beveiligingswaarschuwingen in Security Center](./media/security-center-managing-and-responding-alerts/security-center-dashboard-alert.png)

1. Klik op de tegel om meer informatie over de waarschuwingen weer te geven.

   ![Beveiligingswaarschuwingen in Security Center](./media/security-center-managing-and-responding-alerts/security-center-manage-alerts.png)

1. Als u de weer gegeven waarschuwingen wilt filteren, klikt u op **filter** en selecteert u op de Blade **filter** die wordt geopend de filter opties die u wilt Toep assen. De lijst wordt bijgewerkt op basis van het geselecteerde filter. Filteren kan zeer nuttig zijn. U kunt u bijvoorbeeld concentreren op de beveiligingswaarschuwingen van de afgelopen 24 uur, omdat u een mogelijke inbreuk in het systeem onderzoekt.

    ![Waarschuwingen filteren in Security Center](./media/security-center-managing-and-responding-alerts/security-center-filter-alerts.png)

## <a name="respond-to-security-alerts"></a>Reageren op beveiligingswaarschuwingen

1. Klik in de lijst **beveiligings waarschuwingen** op een beveiligings waarschuwing. De betrokken resources en de stappen die u moet nemen om een aanval te herstellen, worden weer gegeven.

    ![Reageren op beveiligingswaarschuwingen](./media/security-center-managing-and-responding-alerts/security-center-alert.png)

1. Nadat u de informatie hebt bekeken, klikt u op een bron die is aangevallen.

    In het linkerdeel venster van de pagina beveiligings waarschuwing wordt informatie op hoog niveau weer gegeven met betrekking tot de beveiligings waarschuwing: titel, Ernst, status, activiteit tijd, beschrijving van de verdachte activiteit en de betrokken resource. Naast de betreffende resource bevinden de Azure-Tags die relevant zijn voor de resource. Gebruik deze om de organisatie context van de resource af te leiden bij het onderzoeken van de waarschuwing.

    Het rechterdeel venster bevat het tabblad **waarschuwings Details** met meer details over de waarschuwing die u kan helpen bij het onderzoeken van het probleem: IP-adressen, bestanden, processen en meer.
     
    ![Suggesties voor wat u moet doen over beveiligings waarschuwingen](./media/security-center-managing-and-responding-alerts/security-center-alert-remediate.png)

    In het rechterdeel venster vindt u ook het tabblad **actie ondernemen** . Gebruik dit tabblad om verdere acties uit te voeren met betrekking tot de beveiligings waarschuwing. Acties zoals:
    - *De dreiging verminderen* : Hiermee worden hand matige herstel stappen voor deze beveiligings waarschuwing geboden
    - *Toekomstige aanvallen voor komen* : bevat aanbevelingen voor beveiliging om de kwets baarheid te verminderen, de beveiliging postuur te verbeteren en toekomstige aanvallen te voor komen
    - *Automatische reactie activeren* : biedt de mogelijkheid om een logische app te activeren als reactie op deze beveiligings waarschuwing
    - *Vergelijk bare waarschuwingen onderdrukken* : biedt de mogelijkheid om toekomstige waarschuwingen met vergelijk bare kenmerken te onderdrukken als de waarschuwing niet relevant is voor uw organisatie

    ![Tabblad actie uitvoeren](./media/security-center-managing-and-responding-alerts/alert-take-action.png)




## <a name="see-also"></a>Zie ook

In dit document hebt u geleerd hoe u beveiligings waarschuwingen kunt weer geven. Raadpleeg de volgende pagina's voor gerelateerde materialen:

- [Regels voor het onderdrukken van waarschuwingen configureren](alerts-suppression-rules.md)
- [Reacties op Security Center triggers automatiseren](workflow-automation.md)
