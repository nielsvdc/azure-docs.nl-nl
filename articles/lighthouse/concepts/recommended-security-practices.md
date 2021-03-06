---
title: Aanbevolen beveiligingsprocedures
description: Wanneer u Azure Lighthouse gebruikt, is het belang rijk om te overwegen voor beveiliging en toegangs beheer.
ms.date: 08/12/2020
ms.topic: conceptual
ms.openlocfilehash: 097611837e3bba2d1a44ec521862e03cc467d707
ms.sourcegitcommit: 829d951d5c90442a38012daaf77e86046018e5b9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/09/2020
ms.locfileid: "91399377"
---
# <a name="recommended-security-practices"></a>Aanbevolen beveiligingsprocedures

Wanneer u [Azure Lighthouse](../overview.md)gebruikt, is het belang rijk om te overwegen voor beveiliging en toegangs beheer. Gebruikers in uw Tenant hebben direct toegang tot klant abonnementen en resource groepen, dus u wilt stappen ondernemen om de beveiliging van uw Tenant te behouden. U wilt er ook voor zorgen dat u alleen de toegang toestaat die nodig is om de resources van uw klanten effectief te beheren. In dit onderwerp vindt u aanbevelingen waarmee u dit kunt doen.

> [!TIP]
> Deze aanbevelingen zijn ook van toepassing op [ondernemingen die meerdere tenants beheren](enterprise.md) met Azure Lighthouse.

## <a name="require-azure-multi-factor-authentication"></a>Azure Multi-Factor Authentication vereisen

[Azure multi-factor Authentication](../../active-directory/authentication/concept-mfa-howitworks.md) (ook wel verificatie in twee stappen genoemd) helpt voor komen dat aanvallers toegang krijgen tot een account door meerdere verificaties tappen te vereisen. U moet Multi-Factor Authentication vereisen voor alle gebruikers in uw Tenant beheren, met inbegrip van gebruikers die toegang hebben tot gedelegeerde klanten resources.

U wordt aangeraden om uw klanten ook in te stellen om Azure Multi-Factor Authentication te implementeren in hun tenants.

## <a name="assign-permissions-to-groups-using-the-principle-of-least-privilege"></a>Machtigingen toewijzen aan groepen met behulp van het principe van minimale bevoegdheden

Gebruik Azure Active Directory-groepen (Azure AD) voor elke rol die is vereist voor het beheren van de resources van uw klanten om het beheer te vereenvoudigen. Zo kunt u afzonderlijke gebruikers aan de groep toevoegen of verwijderen, in plaats van machtigingen rechtstreeks aan elke gebruiker toe te wijzen.

> [!IMPORTANT]
> Als u machtigingen wilt toevoegen voor een Azure AD-groep, moet u het **groeps type** instellen op **beveiliging**. Deze optie wordt geselecteerd wanneer de groep wordt gemaakt. Zie [Een basisgroep maken en leden toevoegen met behulp van Azure Active Directory](../../active-directory/fundamentals/active-directory-groups-create-azure-portal.md) voor meer informatie.

Wanneer u uw machtigingen structuur maakt, moet u ervoor zorgen dat u het principe van minimale bevoegdheden volgt, zodat gebruikers alleen de benodigde machtigingen hebben om hun taak te volt ooien, waardoor de kans op onbedoelde fouten wordt verminderd.

U kunt bijvoorbeeld een structuur als volgt gebruiken:

|Groepsnaam  |Type  |principalId  |Roldefinitie  |Roldefinitie-ID  |
|---------|---------|---------|---------|---------|
|Ontwerpers     |Gebruikersgroep         |\<principalId\>         |Inzender         |b24988ac-6180-42a0-ab88-20f7382dd24c  |
|Beoordeling     |Gebruikersgroep         |\<principalId\>         |Lezer         |acdd72a7-3385-48ef-bd42-f606fba81ae7  |
|VM-specialisten     |Gebruikersgroep         |\<principalId\>         |Inzender voor VM'S         |9980e02c-c2be-4d73-94e8-173b1dc7cf3c  |
|Automation     |SPN (Service Principal Name)         |\<principalId\>         |Inzender         |b24988ac-6180-42a0-ab88-20f7382dd24c  |

Wanneer u deze groepen hebt gemaakt, kunt u indien nodig gebruikers toewijzen. Voeg alleen de gebruikers toe die echt toegang moeten hebben. Zorg ervoor dat u het groepslid maatschap regel matig controleert en alle gebruikers verwijdert die niet meer geschikt of nood zakelijk zijn om op te nemen.

Houd er rekening mee dat bij het opheffen van [klanten via een openbaar beheerd service-aanbod](../how-to/publish-managed-services-offers.md)elke groep (of gebruiker of Service-Principal) die u opneemt, dezelfde machtigingen heeft voor elke klant die het abonnement koopt. Als u verschillende groepen wilt toewijzen voor samen werking met elke klant, moet u een afzonderlijk privé-plan publiceren dat exclusief is voor elke klant, of dat klanten met behulp van Azure Resource Manager sjablonen afzonderlijk kunnen worden opgeheven. U kunt bijvoorbeeld een openbaar abonnement met zeer beperkte toegang publiceren en vervolgens rechtstreeks samen werken met de klant om hun resources uit te geven voor aanvullende toegang met behulp van een aangepaste Azure-resource sjabloon waarmee extra toegang wordt verleend als dat nodig is.

## <a name="next-steps"></a>Volgende stappen

- [Azure multi-factor Authentication implementeren](../../active-directory/authentication/howto-mfa-getstarted.md).
- Meer informatie over [beheerervaring in meerdere tenants](cross-tenant-management-experience.md).
