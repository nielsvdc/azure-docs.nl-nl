---
title: 'Azure AD Connect: functies in de preview-versie | Microsoft Docs'
description: In dit onderwerp vindt u meer informatie over de functies in de preview-versie van Azure AD Connect.
services: active-directory
documentationcenter: ''
author: billmath
manager: daveba
editor: ''
ms.assetid: c75cd8cf-3eff-4619-bbca-66276757cc07
ms.service: active-directory
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: how-to
ms.date: 05/15/2020
ms.subservice: hybrid
ms.author: billmath
ms.collection: M365-identity-device-management
ms.openlocfilehash: b543cf4655d0b961a144e9180385a532ae4216d6
ms.sourcegitcommit: 829d951d5c90442a38012daaf77e86046018e5b9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/09/2020
ms.locfileid: "89657094"
---
# <a name="more-details-about-features-in-preview"></a>Meer informatie over functies in Preview
In dit onderwerp wordt beschreven hoe u functies kunt gebruiken die momenteel als preview-versie beschikbaar zijn.

## <a name="azure-ad-connect-sync-v2-endpoint-api-public-preview"></a>Azure AD Connect Sync v2-eind punt-API (open bare preview) 

We hebben een nieuw eind punt (API) voor Azure AD Connect geïmplementeerd, waarmee de prestaties van de synchronisatie service-bewerkingen voor Azure Active Directory worden verbeterd. Door gebruik te maken van het nieuwe v2-eind punt, kunt u zien dat er prestatie verhogingen optreden bij het exporteren en importeren naar Azure AD. Dit nieuwe eind punt biedt ook ondersteuning voor het synchroniseren van groepen met Maxi maal 250.000-leden. Met dit eind punt kunt u ook een back-up maken van Microsoft 365 Unified groups, zonder maximale lidmaatschaps limiet, naar uw on-premises Active Directory, wanneer u groeps terugschrijven hebt ingeschakeld. Zie [Azure AD Connect Sync v2-eind punt-API (open bare preview)](how-to-connect-sync-endpoint-api-v2.md)voor meer informatie.

## <a name="user-writeback"></a>Gebruikers terugschrijven
> [!IMPORTANT]
> De preview-functie voor het terugschrijven van gebruikers is in de update van augustus 2015 voor Azure AD Connect verwijderd. Als u het hebt ingeschakeld, moet u deze functie uitschakelen.
>
>

## <a name="next-steps"></a>Volgende stappen
Ga door met de [aangepaste installatie van Azure AD Connect](how-to-connect-install-custom.md).

Lees meer over het [integreren van uw on-premises identiteiten met Azure Active Directory](whatis-hybrid-identity.md).
