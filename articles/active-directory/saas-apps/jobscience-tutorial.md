---
title: 'Zelf studie: integratie Azure Active Directory met Jobscience | Microsoft Docs'
description: Meer informatie over het configureren van eenmalige aanmelding tussen Azure Active Directory en Jobscience.
services: active-directory
author: jeevansd
manager: CelesteDG
ms.service: active-directory
ms.subservice: saas-app-tutorial
ms.workload: identity
ms.topic: article
ms.date: 07/12/2017
ms.author: jeedes
ms.openlocfilehash: 8dc4087d1a10b4c4af7477a02f397c5a2bc547c2
ms.sourcegitcommit: 9b8425300745ffe8d9b7fbe3c04199550d30e003
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/23/2020
ms.locfileid: "92459387"
---
# <a name="tutorial-azure-active-directory-integration-with-jobscience"></a>Zelf studie: integratie Azure Active Directory met Jobscience

In deze zelf studie leert u hoe u Jobscience integreert met Azure Active Directory (Azure AD).

Het integreren van Jobscience met Azure AD biedt de volgende voor delen:

- U kunt beheren in azure AD die toegang heeft tot Jobscience
- U kunt uw gebruikers in staat stellen om automatisch aangemeld te komen bij Jobscience (eenmalige aanmelding) met hun Azure AD-accounts
- U kunt uw accounts op één centrale locatie beheren: de Azure Portal

Zie [Wat is toegang tot toepassingen en eenmalige aanmelding met Azure Active Directory](../manage-apps/what-is-single-sign-on.md)als u meer wilt weten over SaaS-app-integratie met Azure AD.

## <a name="prerequisites"></a>Vereisten

Als u Azure AD-integratie met Jobscience wilt configureren, hebt u de volgende items nodig:

- Een Azure AD-abonnement
- Een abonnement met eenmalige aanmelding voor Jobscience

> [!NOTE]
> Als u de stappen in deze zelfstudie wilt testen, is het raadzaam om niet de productieomgeving te gebruiken.

Volg deze aanbevelingen als u de stappen in deze zelfstudie wilt testen:

- Gebruik niet de productieomgeving, tenzij dit echt nodig is.
- Als u niet beschikt over een evaluatieomgeving in Azure AD, kunt u hier een gratis proefversie van één maand krijgen: [Proefversie](https://azure.microsoft.com/pricing/free-trial/).

## <a name="scenario-description"></a>Scenariobeschrijving
In deze zelf studie test u eenmalige aanmelding voor Azure AD in een test omgeving. Het scenario dat in deze zelf studie wordt beschreven, bestaat uit twee belang rijke bouw stenen:

1. Jobscience toevoegen uit de galerie
1. Eenmalige aanmelding voor Azure AD configureren en testen

## <a name="adding-jobscience-from-the-gallery"></a>Jobscience toevoegen uit de galerie
Als u de integratie van Jobscience in azure AD wilt configureren, moet u Jobscience uit de galerie toevoegen aan uw lijst met beheerde SaaS-apps.

**Voer de volgende stappen uit om Jobscience toe te voegen uit de galerie:**

1. Klik in het linkernavigatievenster in de **[Azure-portal](https://portal.azure.com)** op het **Azure Active Directory**-pictogram. 

    ![Active Directory][1]

1. Navigeer naar **bedrijfs toepassingen**. Ga vervolgens naar **alle toepassingen**.

    ![Scherm afbeelding toont de Azure Portal Enter prise-toepassingen geselecteerd onder beheren, waarbij alle toepassingen zijn geselecteerd.][2]
    
1. Als u de nieuwe toepassing wilt toevoegen, klikt u op de knop **Nieuwe toepassing** boven aan het dialoogvenster.

    ![In de scherm opname wordt de geselecteerde toepassing weer gegeven.][3]

1. Typ **Jobscience**in het zoekvak.

    ![Scherm afbeelding toont de toevoeging uit de galerie waarin jobscience is ingevoerd.](./media/jobscience-tutorial/tutorial_jobscience_search.png)

1. Selecteer in het deel venster resultaten **Jobscience**en klik vervolgens op knop **toevoegen** om de toepassing toe te voegen.

    ![Scherm afbeelding toont de resultaten die Jobscience bevatten.](./media/jobscience-tutorial/tutorial_jobscience_addfromgallery.png)

##  <a name="configuring-and-testing-azure-ad-single-sign-on"></a>Eenmalige aanmelding voor Azure AD configureren en testen
In deze sectie kunt u eenmalige aanmelding voor Azure AD configureren en testen met Jobscience op basis van een test gebruiker met de naam ' Julia Simon '.

Voor gebruik van eenmalige aanmelding moet Azure AD weten wat de tegen gebruiker in Jobscience is voor een gebruiker in azure AD. Met andere woorden, een koppelings relatie tussen een Azure AD-gebruiker en de bijbehorende gebruiker in Jobscience moet tot stand worden gebracht.

In Jobscience wijst u de waarde van de **gebruikers naam** in azure AD toe als de waarde van de **naam** van de gebruiker om de koppelings relatie tot stand te brengen.

Als u eenmalige aanmelding voor Azure AD wilt configureren en testen met Jobscience, moet u de volgende bouw stenen volt ooien:

1. **[Eenmalige aanmelding van Azure AD configureren](#configuring-azure-ad-single-sign-on)** om uw gebruikers in staat te stellen deze functie te gebruiken.
1. **[Een Azure AD-test gebruiker maken](#creating-an-azure-ad-test-user)** : u kunt eenmalige aanmelding voor Azure AD testen met Julia Simon.
1. Het **[maken van een Jobscience-test gebruiker](#creating-a-jobscience-test-user)** : als u een equivalent van Julia Simon in Jobscience wilt hebben dat is gekoppeld aan de Azure AD-representatie van de gebruiker.
1. **[De Azure AD-test gebruiker toewijzen](#assigning-the-azure-ad-test-user)** : om Julia Simon in staat te stellen om eenmalige aanmelding van Azure ad te gebruiken.
1. **[Eenmalige aanmelding testen](#testing-single-sign-on)** om te controleren of de configuratie werkt.

### <a name="configuring-azure-ad-single-sign-on"></a>Eenmalige aanmelding voor Azure AD configureren

In deze sectie schakelt u eenmalige aanmelding voor Azure AD in de Azure Portal en configureert u eenmalige aanmelding in uw Jobscience-toepassing.

**Voer de volgende stappen uit om eenmalige aanmelding voor Azure AD te configureren met Jobscience:**

1. Klik in het Azure Portal op de pagina **Jobscience** toepassings integratie op **eenmalige aanmelding**.

    ![Scherm opname toont eenmalige aanmelding geselecteerd onder beheren in de Azure Portal.][4]

1. Selecteer in het dialoog venster **eenmalige aanmelding** de optie **modus** als op    **SAML gebaseerde aanmelding** om eenmalige aanmelding in te scha kelen.
 
    ![Scherm opname toont de op SAML gebaseerde aanmeldings modus geselecteerd.](./media/jobscience-tutorial/tutorial_jobscience_samlbase.png)

1. Voer de volgende stappen uit in de sectie **Jobscience domein en url's** :

    ![Scherm afbeelding toont de aanmeldings U R L.](./media/jobscience-tutorial/tutorial_jobscience_url.png)

    Typ in het tekstvak **URL voor aanmelding** een URL met het volgende patroon:  `http://<company name>.my.salesforce.com`
    
    > [!NOTE] 
    > Deze waarde is niet echt. Werk deze waarde bij met de werkelijke aanmeldings-URL. Haal deze waarde op door [Jobscience-client ondersteunings team](http://www.jobscience.com/support) of van het SSO-profiel dat u hebt gemaakt. dit wordt verderop in de zelf studie uitgelegd. 
 
1. Klik in de sectie **SAML-handtekening certificaat** op **certificaat (base64)** en sla het certificaat bestand op uw computer op.

    ![Schermopname van het deelvenster SAML-handtekeningcertificaat waar u een certificaat kunt downloaden.](./media/jobscience-tutorial/tutorial_jobscience_certificate.png) 

1. Klik op de knop **Save**.

    ![Scherm afbeelding toont de knop Opslaan.](./media/jobscience-tutorial/tutorial_general_400.png)

1. Klik in het gedeelte **Jobscience configuratie** op **Jobscience configureren** om **het venster aanmelden configureren** te openen. Kopieer de **Afmeldings-URL, de SAML-entiteit-id en de URL van de SAML Single Sign-On-service** uit de **sectie snelle verwijzing.**

    ![Scherm afbeelding toont het configuratie venster Jobscience.](./media/jobscience-tutorial/tutorial_jobscience_configure.png) 

1. Meld u als beheerder aan bij de Jobscience-bedrijfs site.

1. Ga naar **Installatie**.
   
   ![Scherm afbeelding toont het instellings item voor uw bedrijf.](./media/jobscience-tutorial/IC784358.png "Instellen")

1. Klik op **Domeinbeheer** in de sectie **Beheren** in het navigatievenster aan de linkerzijde om de verwante sectie uit te vouwen en klik vervolgens op **Mijn domein** om de pagina **Mijn domein** te openen. 
   
   ![Mijn domein](./media/jobscience-tutorial/ic767825.png "Mijn domein")

1. Als u wilt controleren of uw domein correct is ingesteld, controleert u of de**stap 4 is geïmplementeerd op gebruikers**en controleert u de**instellingen van mijn domein**.

    ![Domein geïmplementeerd voor gebruiker](./media/jobscience-tutorial/ic784377.png "Domein geïmplementeerd voor gebruiker")

1. Klik op de Jobscience-bedrijfs site op **beveiligings controles**en klik vervolgens op **instellingen voor één Sign-On**.
    
    ![Scherm opname toont de instellingen voor één Sign-On die zijn geselecteerd in beveiligings controles.](./media/jobscience-tutorial/ic784364.png "Beveiligingsmaatregelen")

1. Voer de volgende stappen uit in het gedeelte **Instellingen voor eenmalige aanmelding**:
    
    ![Instellingen voor eenmalige aanmelding](./media/jobscience-tutorial/ic781026.png "Instellingen voor eenmalige aanmelding")
    
    a. Selecteer **SAML Enabled**.

    b. Klik op **Nieuw**.

1. Voer de volgende stappen uit in het dialoog venster **instellingen voor eenmalige SAML-Sign-On instellen** :
    
    ![Instellingen voor op SAML gebaseerde eenmalige aanmelding](./media/jobscience-tutorial/ic784365.png "Instellingen voor op SAML gebaseerde eenmalige aanmelding")
    
    a. Typ in het tekstvak **Name** een naam voor de configuratie.

    b. Plak in het tekstvak van de **Uitgever** de waarde van de **SAML-entiteit-id**, die u van Azure Portal hebt gekopieerd.

    c. Typ in het tekstvak **Entiteits-ID**`https://salesforce-jobscience.com`

    d. Klik op **Bladeren** om uw Azure AD-certificaat te uploaden.

    e. Selecteer **Assertie bevat de federatie-id van het gebruikersobject** bij **SAML-identiteitstype**.

    f. Bij **SAML-identiteitslocatie** selecteert u **Identiteit bevindt zich in het NameIdentfier-element van de Onderwerpinstructie**.

    g. Plak in het tekstvak **ID-provider aanmeld-URL** de waarde van de **SAML single Sign-On service-URL**, die u hebt gekopieerd van Azure Portal.

    h. Plak in het tekstvak voor de **Afmeldings-URL van de identiteits provider** de waarde van de **afmeldings-URL**, die u van Azure Portal hebt gekopieerd.

    i. Klik op **Opslaan**.

1. Klik op **Domeinbeheer** in de sectie **Beheren** in het navigatievenster aan de linkerzijde om de verwante sectie uit te vouwen en klik vervolgens op **Mijn domein** om de pagina **Mijn domein** te openen. 
    
    ![Mijn domein](./media/jobscience-tutorial/ic767825.png "Mijn domein")

1. Klik in de sectie **Huisstijl van aanmeldingspagina** op de pagina **Mijn domein** op **Bewerken**.
    
    ![Scherm afbeelding toont de sectie huis stijl aanmeldings pagina met de knop bewerken.](./media/jobscience-tutorial/ic767826.png "Huisstijl van aanmeldingspagina")

1. In de sectie **Verificatieservice** op de pagina **Huisstijl van aanmeldingspagina** wordt de naam van uw **SAML SSO-instellingen** weergegeven. Selecteer dit en klik vervolgens op **Opslaan**.
    
    ![Scherm afbeelding toont de sectie huis stijl aanmeldings pagina met BESCHERMINGs punt en opslaan geselecteerd.](./media/jobscience-tutorial/ic784366.png "Huisstijl van aanmeldingspagina")

1. Als u de aanmeldings-URL voor de door SP geïnitieerde aanmelding wilt ophalen, klikt u op de **instellingen voor eenmalige aanmelding** in de menu sectie **beveiligings besturings elementen** .

    ![Scherm afbeelding toont het beheer van beveiligings controles waarbij de instellingen voor één Sign-On zijn geselecteerd.](./media/jobscience-tutorial/ic784368.png "Beveiligingsmaatregelen")
    
    Klik in de bovenstaande stap op het SSO-profiel dat u hebt gemaakt. Op deze pagina wordt de URL voor eenmalige aanmelding voor uw bedrijf weer gegeven (bijvoorbeeld `https://companyname.my.salesforce.com?so=companyid` .    

> [!TIP]
> U kunt nu een beknopte versie van deze instructies in [Azure Portal](https://portal.azure.com) lezen terwijl u de app instelt!  Klik nadat u deze app onder **Active Directory > Bedrijfstoepassingen** hebt toegevoegd op het tabblad **Eenmalige aanmelding** en open de ingesloten documentatie via het gedeelte **Configuratie** onderaan. U vindt hier meer informatie over de Inge sloten documentatie functie: [documentatie voor Azure AD embedded]( https://go.microsoft.com/fwlink/?linkid=845985)
> 

### <a name="creating-an-azure-ad-test-user"></a>Een Azure AD-testgebruiker maken
Het doel van deze sectie is om in de Azure-portal een testgebruiker met de naam Britta Simon te maken.

![Azure AD-gebruiker maken][100]

**Als u een test gebruiker in azure AD wilt maken, voert u de volgende stappen uit:**

1. Klik in het **Azure Portal**, in het navigatie deel venster aan de linkerkant op **Azure Active Directory** pictogram.

    ![Scherm afbeelding toont het pictogram van Azure A D in het Azure Portal.](./media/jobscience-tutorial/create_aaduser_01.png) 

1. Als u de lijst met gebruikers wilt weer geven, gaat u naar **gebruikers en groepen** en klikt u op **alle gebruikers**.
    
    ![Scherm afbeelding toont gebruikers en groepen die zijn geselecteerd in het menu beheren, met alle geselecteerde gebruikers.](./media/jobscience-tutorial/create_aaduser_02.png) 

1. Klik boven in het dialoog venster op **toevoegen** om het dialoog venster **gebruiker** te openen.
 
    ![Scherm afbeelding toont de knop toevoegen om het dialoog venster gebruiker te openen.](./media/jobscience-tutorial/create_aaduser_03.png) 

1. Voer de volgende stappen uit op de pagina **gebruikers** dialoogvenster:
 
    ![In de scherm afbeelding wordt het dialoog venster van de gebruiker weer gegeven waarin u de waarden in deze stap kunt invoeren.](./media/jobscience-tutorial/create_aaduser_04.png) 

    a. Typ **BrittaSimon**in het tekstvak **naam** .

    b. Typ in het tekstvak **gebruikers naam** het **e-mail adres** van BrittaSimon.

    c. Selecteer **wacht woord weer geven** en noteer de waarde van het **wacht woord**.

    d. Klik op **Create**.
 
### <a name="creating-a-jobscience-test-user"></a>Een Jobscience-test gebruiker maken

Om ervoor te zorgen dat Azure AD-gebruikers zich kunnen aanmelden bij Jobscience, moeten ze worden ingericht in Jobscience. In het geval van Jobscience is inrichting een hand matige taak.

>[!NOTE]
>U kunt alle andere hulpprogram ma's voor het maken van Jobscience-gebruikers accounts of Api's die worden geleverd door Jobscience, gebruiken om Azure Active Directory gebruikers accounts in te richten.
>  
        
**Voer de volgende stappen uit om de gebruikersinrichting te configureren:**

1. Meld u als beheerder aan bij de **Jobscience** -bedrijfs site.

1. Ga naar Installatie.
   
   ![Scherm afbeelding toont het instellings item.](./media/jobscience-tutorial/ic784358.png "Instellen")
1. Ga naar **Gebruikers beheren \> Gebruikers**.
   
   ![Gebruikers](./media/jobscience-tutorial/ic784369.png "Gebruikers")
1. Klik op **New User**.
   
   ![Alle gebruikers](./media/jobscience-tutorial/ic784370.png "Alle gebruikers")
1. Voer de volgende stappen uit in het dialoog venster **gebruiker bewerken** :
   
   ![Gebruiker bewerken](./media/jobscience-tutorial/ic784371.png "Gebruiker bewerken")
   
   a. Typ in het tekstvak **voor de voor naam** een voor naam van de gebruiker, zoals Julia.
   
   b. Typ in het tekstvak **Achternaam** een achternaam van de gebruiker, zoals Simon.
   
   c. Typ in het tekstvak **alias** een alias naam van de gebruiker, zoals Brittas.

   d. Typ in het tekstvak **Email** het e-mailadres van de gebruiker, bijvoorbeeld Brittasimon@contoso.com.

   e. Typ een gebruikersnaam van een gebruiker in het tekstvak **Gebruikersnaam**, bijvoorbeeld Brittasimon@contoso.com.

   f. Typ in het tekstvak **bijnaam** de Nick naam van de gebruiker, zoals Simon.

   g. Klik op **Opslaan**.

    
> [!NOTE]
> De houder van het Azure Active Directory-account ontvangt een e-mail en volgt een koppeling om het account te bevestigen voordat het actief wordt.

### <a name="assigning-the-azure-ad-test-user"></a>De Azure AD-test gebruiker toewijzen

In deze sectie schakelt u Julia Simon in om eenmalige aanmelding van Azure te gebruiken door toegang te verlenen aan Jobscience.

![Scherm afbeelding toont de weergave naam van een account.][200] 

**Voer de volgende stappen uit om Julia Simon toe te wijzen aan Jobscience:**

1. Open in de Azure Portal de weer gave toepassingen en navigeer vervolgens naar de mapweergave en ga naar **bedrijfs toepassingen** en klik vervolgens op **alle toepassingen**.

    ![Scherm opname toont zakelijke toepassingen in het menu Azure Portal met alle geselecteerde toepassingen.][201] 

1. Selecteer in de lijst toepassingen de optie **Jobscience**.

    ![Scherm afbeelding toont Jobscience geselecteerd.](./media/jobscience-tutorial/tutorial_jobscience_app.png) 

1. Klik in het menu aan de linkerkant op **gebruikers en groepen**.

    ![Scherm afbeelding toont gebruikers en groepen die zijn geselecteerd in het menu Azure Portal.][202] 

1. Klik op de knop **Add**. Selecteer vervolgens **gebruikers en groepen** in het dialoog venster **toewijzing toevoegen** .

    ![Scherm afbeelding toont de knop toevoegen, die wordt gebruikt om toewijzingen toe te voegen.][203]

1. Selecteer in het dialoog venster **gebruikers en groepen** de optie **Julia Simon** in de lijst gebruikers.

1. Klik op de knop **selecteren** in het dialoog venster **gebruikers en groepen** .

1. Klik op de knop **toewijzen** in het dialoog venster **toewijzing toevoegen** .
    
### <a name="testing-single-sign-on"></a>Eenmalige aanmelding testen

In deze sectie gaat u uw configuratie van Azure AD-eenmalige aanmelding testen via het toegangsvenster.

Wanneer u op de tegel Jobscience in het toegangs venster klikt, wordt u automatisch aangemeld bij uw Jobscience-toepassing.
Zie [Introduction to the Access Panel](../user-help/my-apps-portal-end-user-access.md) (Inleiding tot het toegangsvenster) voor meer informatie over het toegangsvenster.

## <a name="additional-resources"></a>Aanvullende bronnen

* [Lijst met zelfstudies over het integreren van SaaS-apps met Azure Active Directory](tutorial-list.md)
* [What is application access and single sign-on with Azure Active Directory?](../manage-apps/what-is-single-sign-on.md) (Wat houden toegang tot toepassingen en eenmalige aanmelding met Azure Active Directory in?)

<!--Image references-->

[1]: ./media/jobscience-tutorial/tutorial_general_01.png
[2]: ./media/jobscience-tutorial/tutorial_general_02.png
[3]: ./media/jobscience-tutorial/tutorial_general_03.png
[4]: ./media/jobscience-tutorial/tutorial_general_04.png

[100]: ./media/jobscience-tutorial/tutorial_general_100.png

[200]: ./media/jobscience-tutorial/tutorial_general_200.png
[201]: ./media/jobscience-tutorial/tutorial_general_201.png
[202]: ./media/jobscience-tutorial/tutorial_general_202.png
[203]: ./media/jobscience-tutorial/tutorial_general_203.png