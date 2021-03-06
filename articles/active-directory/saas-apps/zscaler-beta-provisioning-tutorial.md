---
title: 'Zelf studie: Zscaler Beta configureren voor het automatisch inrichten van gebruikers met Azure Active Directory | Microsoft Docs'
description: Meer informatie over het configureren van Azure Active Directory voor het automatisch inrichten en ongedaan maken van de inrichting van gebruikers accounts naar Zscaler Beta.
services: active-directory
author: zchia
writer: zchia
manager: CelesteDG
ms.service: active-directory
ms.subservice: saas-app-tutorial
ms.workload: identity
ms.topic: tutorial
ms.date: 03/27/2019
ms.author: jeedes
ms.openlocfilehash: de42230639351c0dc1e7986156a33b178386d1a4
ms.sourcegitcommit: 0b9fe9e23dfebf60faa9b451498951b970758103
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94357739"
---
# <a name="tutorial-configure-zscaler-beta-for-automatic-user-provisioning"></a>Zelf studie: Zscaler Beta configureren voor het automatisch inrichten van gebruikers

Het doel van deze zelf studie is het demonstreren van de stappen die moeten worden uitgevoerd in Zscaler Beta en Azure Active Directory (Azure AD) om Azure AD te configureren voor het automatisch inrichten en ongedaan maken van de inrichting van gebruikers en/of groepen in Zscaler Beta.

> [!NOTE]
> In deze zelfstudie wordt een connector beschreven die is gebaseerd op de Azure AD-service voor het inrichten van gebruikers. Zie voor belangrijke details over wat deze service doet, hoe het werkt en veelgestelde vragen [Inrichting en ongedaan maken van inrichting van gebruikers automatiseren naar SaaS-toepassingen met Azure Active Directory](../app-provisioning/user-provisioning.md).
>


## <a name="prerequisites"></a>Vereisten

In het scenario dat in deze zelf studie wordt beschreven, wordt ervan uitgegaan dat u het volgende al hebt:

* Een Azure AD-Tenant
* Een Zscaler Beta-Tenant
* Een gebruikers account in Zscaler Beta met beheerders machtigingen

> [!NOTE]
> De integratie van Azure AD-inrichting is afhankelijk van de Zscaler Beta SCIM-API, die beschikbaar is voor Zscaler bèta-ontwikkel aars voor accounts met het ondernemings pakket.

## <a name="adding-zscaler-beta-from-the-gallery"></a>Zscaler Beta toevoegen vanuit de galerie

Voordat u Zscaler Beta configureert voor het automatisch inrichten van gebruikers met Azure AD, moet u Zscaler Beta van de Azure AD-toepassings galerie toevoegen aan uw lijst met beheerde SaaS-toepassingen.

**Voer de volgende stappen uit om Zscaler Beta toe te voegen vanuit de Azure AD-toepassings galerie:**

1. Klik in het linkernavigatievenster in de **[Azure-portal](https://portal.azure.com)** op het **Azure Active Directory** -pictogram.

    ![De knop Azure Active Directory](common/select-azuread.png)

2. Navigeer naar **Bedrijfstoepassingen** en selecteer vervolgens de optie **Alle toepassingen**.

    ![De blade Bedrijfstoepassingen](common/enterprise-applications.png)

3. Als u de nieuwe toepassing wilt toevoegen, klikt u op de knop **Nieuwe toepassing** boven aan het dialoogvenster.

    ![De knop Nieuwe toepassing](common/add-new-app.png)

4. Typ in het zoekvak **Zscaler Beta** , selecteer **Zscaler Beta** in het resultaatvenster en klik op de knop **Toevoegen** om de toepassing toe te voegen.

    ![Zscaler Beta in de lijst met resultaten](common/search-new-app.png)

## <a name="assigning-users-to-zscaler-beta"></a>Gebruikers toewijzen aan Zscaler Beta

Azure Active Directory gebruikt een concept met de naam 'toewijzingen' om te bepalen welke gebruikers toegang moeten krijgen tot geselecteerde apps. In de context van het automatisch inrichten van gebruikers worden alleen de gebruikers en/of groepen gesynchroniseerd die zijn toegewezen aan een toepassing in Azure AD.

Voordat u automatische gebruikers inrichting configureert en inschakelt, moet u beslissen welke gebruikers en/of groepen in azure AD toegang nodig hebben tot Zscaler Beta. Nadat u hebt besloten, kunt u deze gebruikers en/of groepen toewijzen aan Zscaler Beta door de volgende instructies te volgen:

* [Een gebruiker of groep toewijzen aan een bedrijfs-app](../manage-apps/assign-user-or-group-access-portal.md)

### <a name="important-tips-for-assigning-users-to-zscaler-beta"></a>Belang rijke tips voor het toewijzen van gebruikers aan Zscaler Beta

* Het is raadzaam dat er één Azure AD-gebruiker wordt toegewezen aan Zscaler Beta om de configuratie van automatische gebruikers inrichting te testen. Extra gebruikers en/of groepen kunnen later worden toegewezen.

* Wanneer u een gebruiker toewijst aan Zscaler beta, moet u een geldige toepassingsspecifieke rol (indien beschikbaar) selecteren in het dialoog venster toewijzing. Gebruikers met de rol **Standaard toegang** worden uitgesloten van het inrichten.

## <a name="configuring-automatic-user-provisioning-to-zscaler-beta"></a>Automatische gebruikers inrichting configureren voor Zscaler Beta

In deze sectie wordt u begeleid bij de stappen voor het configureren van de Azure AD-inrichtings service om gebruikers en/of groepen in Zscaler Beta te maken, bij te werken en uit te scha kelen op basis van gebruikers-en/of groeps toewijzingen in azure AD.

> [!TIP]
> U kunt er ook voor kiezen om eenmalige aanmelding op basis van SAML in te scha kelen voor Zscaler beta, gevolgd door de instructies in de [zelf studie voor Zscaler bèta-](zscaler-beta-tutorial.md)eenmalige aanmelding. Eenmalige aanmelding kan onafhankelijk van automatische gebruikers inrichting worden geconfigureerd, hoewel deze twee functies elkaar behoeven.

### <a name="to-configure-automatic-user-provisioning-for-zscaler-beta-in-azure-ad"></a>Automatische gebruikers inrichting configureren voor Zscaler beta in azure AD:

1. Meld u aan bij de [Azure Portal](https://portal.azure.com) en selecteer **bedrijfs toepassingen** , selecteer **alle toepassingen** en selecteer vervolgens **Zscaler Beta**.

    ![De blade Bedrijfstoepassingen](common/enterprise-applications.png)

2. Selecteer in de lijst toepassingen de optie **Zscaler Beta**.

    ![De Zscaler Beta-koppeling in de lijst met toepassingen](common/all-applications.png)

3. Selecteer het tabblad **Inrichten**.

    ![Zscaler bèta inrichten](./media/zscaler-beta-provisioning-tutorial/provisioning-tab.png)

4. Stel de **Inrichtingsmodus** in op **Automatisch**.

    ![Zscaler bèta inrichten](./media/zscaler-beta-provisioning-tutorial/provisioning-credentials.png)

5. Voer in het gedeelte **beheerders referenties** de **Tenant-URL** en het **geheime token** van uw Zscaler-bèta account in, zoals beschreven in stap 6.

6. Als u de **Tenant-URL** en het **geheime token** wilt ophalen, gaat u naar **beheer > verificatie-instellingen** in de gebruikers interface van de Zscaler-bèta Portal en klikt u op **SAML** onder **verificatie type**.

    ![Zscaler bèta inrichten](./media/zscaler-beta-provisioning-tutorial/secret-token-1.png)

    Klik op **SAML configureren** om de SAML-opties voor **configuratie** te openen.

    ![Zscaler bèta inrichten](./media/zscaler-beta-provisioning-tutorial/secret-token-2.png)

    Selecteer **SCIM-Based inrichting inschakelen** om basis- **URL** en **Bearer-token** op te halen en sla de instellingen op. Kopieer de **basis-URL** naar de **Tenant-URL** en **Bearer-token**  naar een **geheim token** in de Azure Portal.

7. Klik bij het invullen van de velden die worden weer gegeven in stap 5 op **verbinding testen** om te controleren of Azure AD verbinding kan maken met Zscaler Beta. Als de verbinding mislukt, zorg er dan voor dat uw Zscaler-bèta account beheerders machtigingen heeft en probeer het opnieuw.

    ![Zscaler bèta inrichten](./media/zscaler-beta-provisioning-tutorial/test-connection.png)

8. Voer in het veld **e-mail melding** het e-mail adres in van een persoon of groep die de inrichtings fout meldingen moet ontvangen en schakel het selectie vakje **e-mail melding verzenden als er een fout optreedt**.

    ![Zscaler bèta inrichten](./media/zscaler-beta-provisioning-tutorial/notification.png)

9. Klik op **Opslaan**.

10. Selecteer in de sectie **toewijzingen** de optie **Azure Active Directory gebruikers synchroniseren met Zscaler Beta**.

    ![Zscaler bèta inrichten](./media/zscaler-beta-provisioning-tutorial/user-mappings.png)

11. Controleer de gebruikers kenmerken die zijn gesynchroniseerd vanuit Azure AD naar Zscaler beta in de sectie **kenmerk toewijzing** . De kenmerken die zijn geselecteerd als **overeenkomende** eigenschappen worden gebruikt om te voldoen aan de gebruikers accounts in Zscaler Beta voor bijwerk bewerkingen. Selecteer de knop **Opslaan** om eventuele wijzigingen door te voeren.

    ![Zscaler bèta inrichten](./media/zscaler-beta-provisioning-tutorial/user-attribute-mappings.png)

12. Selecteer in de sectie **toewijzingen** de optie **Azure Active Directory groepen synchroniseren met Zscaler Beta**.

    ![Zscaler bèta inrichten](./media/zscaler-beta-provisioning-tutorial/group-mappings.png)

13. Controleer de groeps kenmerken die zijn gesynchroniseerd vanuit Azure AD naar Zscaler beta in de sectie **kenmerk toewijzing** . De kenmerken die zijn geselecteerd als **overeenkomende** eigenschappen worden gebruikt om te voldoen aan de groepen in Zscaler Beta voor bijwerk bewerkingen. Selecteer de knop **Opslaan** om eventuele wijzigingen door te voeren.

    ![Zscaler bèta inrichten](./media/zscaler-beta-provisioning-tutorial/group-attribute-mappings.png)

14. Als u bereikfilters wilt configureren, raadpleegt u de volgende instructies in de [zelfstudie Bereikfilter](../app-provisioning/define-conditional-rules-for-provisioning-user-accounts.md).

15. Als u de Azure AD Provisioning Service voor Zscaler Beta wilt inschakelen, **wijzigt u de** **inrichtings status** in in het gedeelte **instellingen** .

    ![Zscaler bèta inrichten](./media/zscaler-beta-provisioning-tutorial/provisioning-status.png)

16. Definieer de gebruikers en/of groepen die u wilt inrichten voor Zscaler Beta door de gewenste waarden in het **bereik** in het gedeelte **instellingen** te kiezen.

    ![Zscaler bèta inrichten](./media/zscaler-beta-provisioning-tutorial/scoping.png)

17. Wanneer u klaar bent om in te richten, klikt u op **Opslaan**.

    ![Zscaler bèta inrichten](./media/zscaler-beta-provisioning-tutorial/save-provisioning.png)

Met deze bewerking wordt de eerste synchronisatie gestart van alle gebruikers en/of groepen die zijn gedefinieerd onder **Bereik** in de sectie **Instellingen**. De initiële synchronisatie duurt langer dan volgende synchronisaties, die ongeveer om de 40 minuten plaatsvinden zolang de Azure AD-inrichtingsservice wordt uitgevoerd. U kunt de sectie **synchronisatie Details** gebruiken om de voortgang te bewaken en koppelingen naar het rapport inrichtings activiteiten te volgen, waarin alle acties worden beschreven die worden uitgevoerd door de Azure AD Provisioning-Service op Zscaler Beta.

Zie [Rapportage over automatische inrichting van gebruikersaccounts](../app-provisioning/check-status-user-account-provisioning.md) voor informatie over het lezen van de Azure AD-inrichtingslogboeken.

## <a name="additional-resources"></a>Aanvullende resources

* [Gebruikersaccountinrichting voor zakelijke apps beheren](../app-provisioning/configure-automatic-user-provisioning-portal.md)
* [What is application access and single sign-on with Azure Active Directory?](../manage-apps/what-is-single-sign-on.md) (Wat houden toegang tot toepassingen en eenmalige aanmelding met Azure Active Directory in?)

## <a name="next-steps"></a>Volgende stappen

* [Meer informatie over het controleren van logboeken en het ophalen van rapporten over de inrichtingsactiviteit](../app-provisioning/check-status-user-account-provisioning.md)

<!--Image references-->
[1]: ./media/zscaler-beta-provisioning-tutorial/tutorial-general-01.png
[2]: ./media/zscaler-beta-provisioning-tutorial/tutorial-general-02.png
[3]: ./media/zscaler-beta-provisioning-tutorial/tutorial-general-03.png