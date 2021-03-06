---
title: Azure-beveiligings basislijn voor Azure Machine Learning
description: De Azure Machine Learning Security Baseline voorziet in procedure richtlijnen en resources voor het implementeren van de beveiligings aanbevelingen die zijn opgegeven in de Azure Security-Bench Mark.
author: msmbaldwin
ms.service: machine-learning
ms.subservice: core
ms.topic: conceptual
ms.date: 08/19/2020
ms.author: mbaldwin
ms.custom: subject-security-benchmark
ms.openlocfilehash: ccc9f7c2521f846529642c644e70654d17ae54ce
ms.sourcegitcommit: 96918333d87f4029d4d6af7ac44635c833abb3da
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/04/2020
ms.locfileid: "93305710"
---
# <a name="azure-security-baseline-for-azure-machine-learning"></a>Azure-beveiligings basislijn voor Azure Machine Learning

De Azure-beveiligings basislijn voor Microsoft Azure Machine Learning bevat aanbevelingen waarmee u de beveiligings postuur van uw implementatie kunt verbeteren. De basis lijn voor deze service wordt opgehaald uit de [Azure Security Bench Mark-versie 1,0](../security/benchmarks/overview.md), die aanbevelingen biedt over hoe u uw cloud oplossingen kunt beveiligen in azure met onze richt lijnen voor best practices. Zie [overzicht van Azure Security-basis lijnen](../security/benchmarks/security-baselines-overview.md)voor meer informatie.

## <a name="network-security"></a>Netwerkbeveiliging

*Zie [Azure Security Bench Mark: Network Security](../security/benchmarks/security-control-network-security.md)(Engelstalig) voor meer informatie.*

### <a name="11-protect-azure-resources-within-virtual-networks"></a>1,1: Azure-resources in virtuele netwerken beveiligen

**Hulp** : Azure machine learning is afhankelijk van andere Azure-Services voor reken resources. Reken bronnen (Compute-doelen) worden gebruikt om modellen te trainen en te implementeren. U kunt deze reken doelen maken in een virtueel netwerk. U kunt bijvoorbeeld Azure Virtual Machine Learning Compute-instantie gebruiken om een model te trainen en het model vervolgens implementeren in azure Kubernetes service (AKS). U kunt uw machine learning levenscyclusn beveiligen door Azure Machine Learning training te isoleren en taken in een virtueel Azure-netwerk af te leiden.

Azure Firewall kan worden gebruikt om de toegang tot uw Azure Machine Learning-werk ruimte en het open bare Internet te beheren.

- [Overzicht van virtuele netwerk isolatie en privacy](how-to-network-security-overview.md)

- [Werk ruimte achter Azure Firewall gebruiken voor Azure Machine Learning](how-to-access-azureml-behind-firewall.md)

**Azure Security Center bewaking** : Ja

**Verantwoordelijkheid** : klant

### <a name="12-monitor-and-log-the-configuration-and-traffic-of-virtual-networks-subnets-and-nics"></a>1,2: de configuratie en het verkeer van virtuele netwerken, subnetten en Nic's bewaken en vastleggen

**Hulp** : Azure machine learning is afhankelijk van andere Azure-Services voor reken resources. Netwerk beveiligings groepen toewijzen aan de netwerken die zijn gemaakt als uw Machine Learning-implementatie. 

Schakel logboeken stroom van de netwerk beveiligings groep in en verzend de logboeken naar een Azure Storage account voor controle. U kunt de stroom logboeken ook naar een Log Analytics-werk ruimte verzenden en vervolgens Traffic Analytics gebruiken om inzicht te krijgen in verkeers patronen in uw Azure-Cloud. Enkele voor delen van Traffic Analytics zijn de mogelijkheid om netwerk activiteiten te visualiseren, HOTS pots en beveiligings Risico's te identificeren, verkeers patronen te begrijpen en netwerk configuraties te lokaliseren.

- [Stroom logboeken van netwerk beveiligings groepen inschakelen](../network-watcher/network-watcher-nsg-flow-logging-portal.md)

- [Traffic Analytics inschakelen en gebruiken](../network-watcher/traffic-analytics.md)

- [Informatie over de netwerk beveiliging die wordt verschaft door Azure Security Center](../security-center/security-center-network-recommendations.md)

**Azure Security Center bewaking** : Ja

**Verantwoordelijkheid** : klant

### <a name="13-protect-critical-web-applications"></a>1,3: essentiële webtoepassingen beveiligen

**Richt lijnen** : u kunt HTTPS inschakelen voor het beveiligen van communicatie met webservices die zijn geïmplementeerd door Azure machine learning. Webservices worden geïmplementeerd op Azure Kubernetes Services (AKS) of Azure Container Instances (ACI) en beveiligen de gegevens die door clients worden verzonden. U kunt ook persoonlijk IP-adres met AKS gebruiken om de score te beperken, zodat alleen clients achter een virtueel netwerk toegang hebben tot de webservice.

- [TLS gebruiken om een webservice te beveiligen via Azure Machine Learning](how-to-secure-web-service.md)

- [Overzicht van virtuele netwerk isolatie en privacy](how-to-network-security-overview.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="14-deny-communications-with-known-malicious-ip-addresses"></a>1,4: communicatie met bekende schadelijke IP-adressen weigeren

**Hulp** : Schakel DDoS Protection standaard in op de virtuele netwerken die zijn gekoppeld aan uw machine learning-exemplaar om te beschermen tegen gedistribueerde Denial-of-service-aanvallen (DDoS). Gebruik Azure Security Center geïntegreerde detectie van bedreigingen om communicaties te detecteren met bekende of ongebruikte Internet-IP-adressen.

Implementeer Azure Firewall op alle netwerk grenzen van de organisatie met op bedreigingen gebaseerd filteren en is geconfigureerd voor ' waarschuwen en weigeren ' voor schadelijk netwerk verkeer.

- [DDoS-beveiliging configureren](../ddos-protection/manage-ddos-protection.md)

- [Werk ruimte achter Azure Firewall gebruiken voor Azure Machine Learning](how-to-access-azureml-behind-firewall.md)

- [Voor meer informatie over de Azure Security Center-detectie van bedreigingen](../security-center/azure-defender.md)

**Azure Security Center bewaking** : Ja

**Verantwoordelijkheid** : klant

### <a name="15-record-network-packets"></a>1,5: netwerk pakketten opnemen

**Richt lijnen** : voor alle vm's met de juiste extensie die in uw Azure Machine Learning Services is geïnstalleerd, kunt u Network Watcher pakket opname inschakelen om afwijkende activiteiten te onderzoeken. 

- [Een Network Watcher-exemplaar maken](../network-watcher/network-watcher-create.md)

**Azure Security Center bewaking** : Ja

**Verantwoordelijkheid** : klant

### <a name="16-deploy-network-based-intrusion-detectionintrusion-prevention-systems-idsips"></a>1,6: op netwerk gebaseerde inbreuk detectie/indringings systemen (ID'S/IP-adressen) implementeren

**Richt lijnen** : implementeer de door u gewenste firewall oplossing op elk van de netwerk grenzen van uw organisatie om schadelijk verkeer te detecteren en/of te blok keren.

Selecteer een aanbieding van Azure Marketplace die ondersteuning biedt voor ID'S/IP-adressen met Payload-inspectie mogelijkheden.  Als Payload-inspectie geen vereiste is, kan Azure Firewall Threat Intelligence worden gebruikt. Azure Firewall op bedreigingen gebaseerd filteren wordt gebruikt om het verkeer van en naar bekende schadelijke IP-adressen en domeinen te Signa lering en/of te blok keren. De IP-adressen en domeinen zijn afkomstig van de Microsoft Bedreigingsinformatie-feed.

- [Azure Firewall implementeren](../firewall/tutorial-firewall-deploy-portal.md)

- [Waarschuwingen configureren met Azure Firewall](../firewall/threat-intel.md)

- [Azure Marketplace](https://azuremarketplace.microsoft.com/marketplace/?term=Firewall)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="17-manage-traffic-to-web-applications"></a>1,7: verkeer naar webtoepassingen beheren

**Richt lijnen** : niet van toepassing; deze aanbeveling is bedoeld voor webtoepassingen die worden uitgevoerd op Azure App Service of reken bronnen.

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : niet van toepassing

### <a name="18-minimize-complexity-and-administrative-overhead-of-network-security-rules"></a>1,8: de complexiteit en administratieve overhead van netwerk beveiligings regels minimaliseren

**Richt lijnen** : voor bronnen die toegang nodig hebben tot uw Azure machine learning-account, gebruikt u Virtual Network Service Tags om netwerk toegangs beheer te definiëren voor netwerk beveiligings groepen of Azure firewall. U kunt servicetags gebruiken in plaats van specifieke IP-adressen wanneer u beveiligingsregels maakt. Door de naam van de service label (bijvoorbeeld AzureMachineLearning) op te geven in het juiste bron-of doel veld van een regel, kunt u het verkeer voor de bijbehorende service toestaan of weigeren. Micro soft beheert de adres voorvoegsels die zijn opgenomen in het servicetag van de service en werkt de servicetag automatisch bij met gewijzigde adressen.

Azure Machine Learning-service documenteert een lijst met Service Tags voor de reken doelen binnen een virtueel netwerk waarmee de complexiteit kan worden geminimaliseerd. u kunt deze gebruiken als richt lijnen in uw netwerk beheer.

- [Voor meer informatie over het gebruik van service Tags](../virtual-network/service-tags-overview.md)

- [Overzicht van virtuele netwerk isolatie en privacy](how-to-network-security-overview.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="19-maintain-standard-security-configurations-for-network-devices"></a>1,9: standaard beveiligings configuraties voor netwerk apparaten onderhouden

**Hulp** : Definieer en implementeer standaard beveiligings configuraties voor netwerk bronnen die zijn gekoppeld aan uw Azure machine learning-naam ruimten met Azure Policy. Gebruik Azure Policy aliassen in de naam ruimten ' micro soft. MachineLearning ' en ' micro soft. Network ' om aangepaste beleids regels te maken om de netwerk configuratie van uw Machine Learning naam ruimten te controleren of af te dwingen. 

- [Azure Policy configureren en beheren](../governance/policy/tutorials/create-and-manage.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="110-document-traffic-configuration-rules"></a>1,10: configuratie regels voor het document verkeer

**Richt lijnen** : Gebruik labels voor netwerk bronnen die zijn gekoppeld aan uw Azure machine learning-implementatie om ze logisch te organiseren op basis van een taxonomie.

Voor een resource in uw Azure Machine Learning virtuele netwerk dat het beschrijvings veld ondersteunt, gebruikt u dit om de regels te documenteren die verkeer van of naar een netwerk toestaan.

- [Tags maken en gebruiken](../azure-resource-manager/management/tag-resources.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="111-use-automated-tools-to-monitor-network-resource-configurations-and-detect-changes"></a>1,11: gebruik automatische hulpprogram ma's om netwerk bron configuraties te bewaken en wijzigingen te detecteren

**Hulp** : Azure-activiteiten logboek gebruiken om netwerk resource configuraties te bewaken en wijzigingen te detecteren voor netwerk bronnen die betrekking hebben op Azure machine learning. Maak waarschuwingen in Azure Monitor die worden geactiveerd wanneer er wijzigingen in kritieke netwerk bronnen plaatsvinden.

- [Activiteiten logboek gebeurtenissen van Azure weer geven en ophalen](../azure-monitor/platform/activity-log.md#view-the-activity-log)

- [Waarschuwingen maken in Azure Monitor](../azure-monitor/platform/alerts-activity-log.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

## <a name="logging-and-monitoring"></a>Logboekregistratie en bewaking

*Zie [Azure Security Bench Mark: Logging and monitoring](../security/benchmarks/security-control-logging-monitoring.md)(Engelstalig) voor meer informatie.*

### <a name="21-use-approved-time-synchronization-sources"></a>2,1: goedgekeurde tijd synchronisatie bronnen gebruiken

**Richt lijnen** : micro soft onderhoudt de tijd bron die wordt gebruikt voor Azure-resources, zoals Azure machine learning voor tijds tempels in de logboeken.

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : micro soft

### <a name="22-configure-central-security-log-management"></a>2,2: Centraal beveiligings logboek beheer configureren

**Hulp** : opname logboeken via Azure monitor voor het verzamelen van beveiligings gegevens die zijn gegenereerd door Azure machine learning. Gebruik in Azure Monitor Log Analytics-werk ruimten om analyses uit te voeren en te uitvoeren en gebruik Azure Storage accounts voor lange termijn-en archiverings opslag. U kunt ook gegevens naar Azure Sentinel of een beveiligings incident en gebeurtenis beheer van derden (SIEM) inschakelen en op de trein zetten.

- [Diagnostische logboeken voor Azure Machine Learning configureren](monitor-azure-machine-learning.md#configuration)

- [Azure-Sentinel onboarden](../sentinel/quickstart-onboard.md)

**Azure Security Center bewaking** : Ja

**Verantwoordelijkheid** : klant

### <a name="23-enable-audit-logging-for-azure-resources"></a>2,3: controle logboek registratie inschakelen voor Azure-resources

**Hulp** : Diagnostische instellingen inschakelen op Azure-resources voor toegang tot controle-, beveiligings-en Diagnostische logboeken. Activiteiten logboeken, die automatisch beschikbaar zijn, omvatten gebeurtenis bron, datum, gebruiker, tijds tempel, bron adressen, doel adressen en andere nuttige elementen.

U kunt ook Machine Learning service bewerkings logboeken voor beveiligings-en nalevings doeleinden correleren.

- [Platform logboeken en metrische gegevens verzamelen met Azure Monitor](../azure-monitor/platform/diagnostic-settings.md)

- [Logboek registratie en verschillende logboek typen in azure](../azure-monitor/platform/platform-logs-overview.md)

- [Logboek registratie inschakelen in Azure Machine Learning](./how-to-track-experiments.md)

- [Bewakings Azure Machine Learning](monitor-azure-machine-learning.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="24-collect-security-logs-from-operating-systems"></a>2,4: beveiligings logboeken verzamelen van besturings systemen

**Richt lijnen** : als de reken resource eigendom is van micro soft, is micro soft verantwoordelijk voor het verzamelen en bewaken van deze. 

Azure Machine Learning heeft verschillende ondersteuning voor verschillende reken bronnen en zelfs uw eigen reken bronnen. Gebruik Azure Security Center om het besturings systeem te bewaken voor alle reken resources die eigendom zijn van uw organisatie. 

- [Interne host-logboeken van de virtuele machine van Azure verzamelen met Azure Monitor](../azure-monitor/learn/quick-collect-azurevm.md)

- [Meer informatie over het verzamelen van Azure Security Center gegevens](../security-center/security-center-enable-data-collection.md)

**Azure Security Center bewaking** : Ja

**Verantwoordelijkheid** : gedeeld

### <a name="25-configure-security-log-storage-retention"></a>2,5: Bewaar beveiliging van het beveiligings logboek configureren

**Richt lijnen** : stel in azure monitor de Bewaar periode voor het logboek In voor log Analytics werk ruimten die zijn gekoppeld aan uw Azure machine learning-instanties volgens de nalevings voorschriften van uw organisatie.

- [Para meters voor het bewaren van Logboeken instellen](../azure-monitor/platform/manage-cost-storage.md#change-the-data-retention-period)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="26-monitor-and-review-logs"></a>2,6: Logboeken bewaken en controleren

**Hulp** : Analyseer en bewaak logboeken voor afwijkend gedrag en controleer regel matig de resultaten van uw Azure machine learning. Gebruik Azure Monitor en een Log Analytics werk ruimte om logboeken te controleren en query's uit te voeren op logboek gegevens.

U kunt ook gegevens in-en inschakelen voor Azure Sentinel of een SIEM van derden. 

- [Query's uitvoeren voor Azure Machine Learning in Log Analytics-werk ruimten](monitor-azure-machine-learning.md#analyzing-log-data)

- [Logboek registratie inschakelen in Azure Machine Learning](./how-to-track-experiments.md)

- [Azure-Sentinel onboarden](../sentinel/quickstart-onboard.md)

- [Aan de slag met Log Analytics query's](../azure-monitor/log-query/get-started-portal.md)

- [Aangepaste query's uitvoeren in Azure Monitor](../azure-monitor/log-query/get-started-queries.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="27-enable-alerts-for-anomalous-activities"></a>2,7: waarschuwingen inschakelen voor afwijkende activiteiten

**Richt lijnen** : in azure monitor kunt u logboeken met betrekking tot Azure machine learning in het activiteiten logboek configureren en machine learning Diagnostische instellingen voor het verzenden van logboeken naar een log Analytics werk ruimte om een query uit te sturen naar een opslag account voor opslag op lange termijn archivering. Gebruik Log Analytics werk ruimte om waarschuwingen te maken voor afwijkende activiteiten die in beveiligings logboeken en gebeurtenissen zijn gevonden.

U kunt ook gegevens naar Azure-Sentinel inschakelen en op het bord zetten.

- [Voor meer informatie over Azure Machine Learning-waarschuwingen](monitor-azure-machine-learning.md#alerts)

- [Waarschuwingen voor Log Analytics werkruimte logboek gegevens](../azure-monitor/learn/tutorial-response.md)

- [Azure-Sentinel onboarden](../sentinel/quickstart-onboard.md)

**Azure Security Center bewaking** : Ja

**Verantwoordelijkheid** : klant

### <a name="28-centralize-anti-malware-logging"></a>2,8: registratie van anti-malware centraliseren

**Richt lijnen** : als de reken resource eigendom is van micro soft, is micro soft verantwoordelijk voor de implementatie van de antimalware van Azure machine learning service. 

Azure Machine Learning heeft verschillende ondersteuning voor verschillende reken bronnen en zelfs uw eigen reken bronnen. Voor reken resources die eigendom zijn van uw organisatie, schakelt u de verzameling van antimalware-gebeurtenissen in voor micro soft antimalware voor Azure Cloud Services en Virtual Machines.

- [Micro soft antimalware configureren voor een virtuele machine](/powershell/module/servicemanagement/azure.service/set-azurevmmicrosoftantimalwareextension)

- [Micro soft antimalware-extensie voor Cloud Services configureren](/powershell/module/servicemanagement/azure.service/set-azureserviceantimalwareextension?view=azuresmps-4.0.0)

- [Micro soft antimalware begrijpen](../security/fundamentals/antimalware.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : gedeeld

### <a name="29-enable-dns-query-logging"></a>2,9: DNS-query logboek registratie inschakelen

**Richt lijnen** : niet van toepassing; Azure Machine Learning worden geen DNS-gerelateerde logboeken verwerkt of geproduceerd.

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : niet van toepassing

### <a name="210-enable-command-line-audit-logging"></a>2,10: controle logboek registratie op opdracht regel inschakelen

**Hulp** : Azure machine learning heeft verschillende ondersteuning voor verschillende reken bronnen en zelfs uw eigen reken bronnen. Voor reken bronnen die eigendom zijn van uw organisatie, gebruikt u Azure Security Center om bewaking van beveiligings logboeken voor virtuele Azure-machines in te scha kelen. Azure Security Center voorziet de Log Analytics agent op alle ondersteunde virtuele machines van Azure en nieuwe die worden gemaakt als automatisch inrichten is ingeschakeld. U kunt de agent ook hand matig installeren. De agent maakt de gebeurtenis 4688 voor het maken van processen en het veld commandline in gebeurtenis 4688 mogelijk. Nieuwe processen die op de virtuele machine worden gemaakt, worden vastgelegd door het gebeurtenis logboek en worden bewaakt door de detectie services van Security Center.

**Azure Security Center bewaking** : Ja

**Verantwoordelijkheid** : klant

## <a name="identity-and-access-control"></a>Identiteits- en toegangsbeheer

*Zie [Azure Security Bench Mark: identiteits-en toegangs beheer](../security/benchmarks/security-control-identity-access-control.md)voor meer informatie.*

### <a name="31-maintain-an-inventory-of-administrative-accounts"></a>3,1: een inventaris van beheerders accounts onderhouden

**Richt lijnen** : u kunt het tabblad identiteits-en toegangs beheer voor een resource in de Azure Portal gebruiken om op rollen gebaseerd toegangs beheer (Azure RBAC) voor Azure te configureren en inventaris op Azure machine learning resources te onderhouden. De rollen worden toegepast op gebruikers, groepen, service-principals en beheerde identiteiten in Active Directory. U kunt ingebouwde rollen of aangepaste rollen gebruiken voor individuen en groepen.

Azure Machine Learning biedt ingebouwde rollen voor algemene beheer scenario's in Azure Machine Learning. Een persoon die een profiel in Azure Active Directory (Azure AD) heeft, kan deze rollen toewijzen aan gebruikers, groepen, service-principals of beheerde identiteiten voor het verlenen of weigeren van toegang tot resources en bewerkingen op Azure Machine Learning-resources.

U kunt ook de Azure AD Power shell-module gebruiken om ad hoc query's uit te voeren om accounts te detecteren die lid zijn van beheer groepen.

- [Meer informatie over toegangs beheer op basis van rollen in Azure in Azure Machine Learning](how-to-assign-roles.md)

- [Een directory-rol verkrijgen in Azure Active Directory met Power shell](/powershell/module/azuread/get-azureaddirectoryrole?view=azureadps-2.0)

**Azure Security Center bewaking** : Ja

**Verantwoordelijkheid** : klant

### <a name="32-change-default-passwords-where-applicable"></a>3,2: standaard wachtwoorden wijzigen indien van toepassing

**Hulp** : toegangs beheer voor machine learning bronnen wordt beheerd via Azure Active Directory (Azure AD). Azure AD heeft niet het concept van standaard wachtwoorden.

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="33-use-dedicated-administrative-accounts"></a>3,3: speciale beheerders accounts gebruiken

**Hulp** : Azure machine learning wordt geleverd met drie standaard rollen wanneer er een nieuwe werk ruimte wordt gemaakt, waardoor er standaard procedures worden gemaakt rondom het gebruik van eigenaars accounts.

U kunt ook een just-in-time-toegang tot beheerders accounts inschakelen met behulp van Azure AD Privileged Identity Management en Azure Resource Manager. 

- [Meer informatie Machine Learning standaard rollen](how-to-assign-roles.md#default-roles)

- [Meer informatie over Privileged Identity Management](../active-directory/privileged-identity-management/index.yml)

**Azure Security Center bewaking** : Ja

**Verantwoordelijkheid** : klant

### <a name="34-use-single-sign-on-sso-with-azure-active-directory"></a>3,4: eenmalige aanmelding (SSO) met Azure Active Directory gebruiken

**Hulp** : machine learning is geïntegreerd met Azure Active Directory, Azure Active Directory SSO gebruiken in plaats van afzonderlijke zelfstandige referenties per service te configureren. Gebruik Azure Security Center-aanbevelingen voor identiteit en toegang.  

- [Informatie over eenmalige aanmelding met Azure AD](../active-directory/manage-apps/what-is-single-sign-on.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="35-use-multi-factor-authentication-for-all-azure-active-directory-based-access"></a>3,5: multi-factor Authentication gebruiken voor alle op Azure Active Directory gebaseerde toegang

**Hulp** : schakel Azure Active Directory multi-factor Authentication in en volg de aanbevelingen voor Azure Security Center identiteit en toegang.

- [MFA inschakelen in azure](../active-directory/authentication/howto-mfa-getstarted.md)

- [Identiteit en toegang bewaken in Azure Security Center](../security-center/security-center-identity-access.md)

**Azure Security Center bewaking** : Ja

**Verantwoordelijkheid** : klant

### <a name="36-use-dedicated-machines-privileged-access-workstations-for-all-administrative-tasks"></a>3,6: gebruik speciale machines (privileged Access workstations) voor alle beheer taken

**Hulp** : gebruik een beveiligd, door Azure beheerd werk station (ook wel een privileged Access Workstation of paw) voor beheer taken waarvoor verhoogde bevoegdheden zijn vereist.

- [Meer informatie over veilige, door Azure beheerde werk stations](../active-directory/devices/concept-azure-managed-workstation.md)

- [Azure AD MFA inschakelen](../active-directory/authentication/howto-mfa-getstarted.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="37-log-and-alert-on-suspicious-activities-from-administrative-accounts"></a>3,7: Logboeken en waarschuwingen voor verdachte activiteiten van beheerders accounts

**Hulp** : gebruik Azure Active Directory beveiligings rapporten en-bewaking om te detecteren wanneer verdachte of onveilige activiteiten in de omgeving worden uitgevoerd. Gebruik Azure Security Center om identiteits-en toegangs activiteiten te bewaken.

- [Azure AD-gebruikers identificeren die zijn gemarkeerd voor Risk ante activiteiten](../active-directory/identity-protection/overview-identity-protection.md)

- [Identiteits-en toegangs activiteiten van gebruikers controleren in Azure Security Center](../security-center/security-center-identity-access.md)

**Azure Security Center bewaking** : Ja

**Verantwoordelijkheid** : klant

### <a name="38-manage-azure-resources-only-from-approved-locations"></a>3,8: beheer Azure-resources alleen op goedgekeurde locaties

**Richt lijnen** : gebruik Azure AD benoemde locaties om alleen toegang toe te staan vanuit specifieke logische groepen met IP-adresbereiken of landen/regio's.
 
 
 
- [De benoemde locaties van Azure AD configureren](../active-directory/reports-monitoring/quickstart-configure-named-locations.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="39-use-azure-active-directory"></a>3,9: Azure Active Directory gebruiken

**Hulp** : gebruik Azure Active Directory (Azure AD) als centrale verificatie-en autorisatie systeem. Azure AD beveiligt gegevens door gebruik te maken van sterke versleuteling voor gegevens in rust en onderweg. Azure AD bevat ook zouten, hashes en veilige gebruikers referenties.
 
De toegang tot rollen kan worden beperkt tot meerdere niveaus in Azure. Voor Machine Learning kunnen rollen worden beheerd op het niveau van de werk ruimte, bijvoorbeeld als de eigenaar toegang heeft tot een werk ruimte, mag de eigenaar geen toegang hebben tot de resource groep die de werk ruimte bevat. Dit biedt meer nauw keurige toegangs controles voor het scheiden van rollen binnen dezelfde resource groep. 

- [De toegang tot een Azure Machine Learning-werkruimte beheren](how-to-assign-roles.md) 
 
- [Een Azure AD-exemplaar maken en configureren](../active-directory/fundamentals/active-directory-access-create-new-tenant.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="310-regularly-review-and-reconcile-user-access"></a>3,10: regel matig gebruikers toegang controleren en afstemmen

**Richt lijnen** : Azure AD biedt logboeken waarmee u verlopen accounts kunt detecteren. Daarnaast kunt u Azure AD Identity and Access revisies gebruiken om groepslid maatschappen, toegang tot bedrijfs toepassingen en roltoewijzingen op efficiënte wijze te beheren. Gebruikers toegang kan regel matig worden gecontroleerd om ervoor te zorgen dat alleen de juiste gebruikers toegang hebben. 
 
Gebruik Azure Active Directory (Azure AD) Privileged Identity Management (PIM) voor het genereren van Logboeken en waarschuwingen wanneer verdachte of onveilige activiteiten in de omgeving worden uitgevoerd.

- [Meer informatie over Azure AD-rapportage](../active-directory/reports-monitoring/index.yml)

- [Azure AD-identiteits-en toegangs beoordelingen gebruiken](../active-directory/governance/access-reviews-overview.md)

- [Azure AD Privileged Identity Management implementeren (PIM)](../active-directory/privileged-identity-management/pim-deployment-plan.md)

**Azure Security Center bewaking** : Ja

**Verantwoordelijkheid** : klant

### <a name="311-monitor-attempts-to-access-deactivated-credentials"></a>3,11: controle pogingen om toegang te krijgen tot gedeactiveerde referenties

**Richt lijnen** : u hebt toegang tot de Azure AD-aanmeldings activiteit, audit en risico gebeurtenis logboek bronnen, waarmee u kunt integreren met elk Siem/bewakings programma.

U kunt dit proces stroom lijnen door Diagnostische instellingen voor Azure AD-gebruikers accounts te maken en de audit logboeken en aanmeldings logboeken te verzenden naar een Log Analytics-werk ruimte. U kunt de gewenste waarschuwingen configureren in Log Analytics werk ruimte.
 
 
- [Azure-activiteiten logboeken integreren met Azure Monitor](../active-directory/reports-monitoring/howto-integrate-activity-logs-with-log-analytics.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="312-alert-on-account-login-behavior-deviation"></a>3,12: waarschuwing voor de afwijking van het aanmeldings gedrag van accounts

**Hulp** : gebruik Azure AD Identity Protection functies om automatische antwoorden te configureren op gedetecteerde verdachte acties met betrekking tot gebruikers identiteiten. U kunt ook gegevens opnemen in azure Sentinel voor verder onderzoek.
 
- [Risk ante aanmeldingen voor Azure AD weer geven](../active-directory/identity-protection/overview-identity-protection.md)
 
- [Risico beleid voor identiteits beveiliging configureren en inschakelen](../active-directory/identity-protection/howto-identity-protection-configure-risk-policies.md)
 
- [Azure-Sentinel onboarden](../sentinel/quickstart-onboard.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="313-provide-microsoft-with-access-to-relevant-customer-data-during-support-scenarios"></a>3,13: micro soft biedt toegang tot relevante klant gegevens tijdens ondersteunings scenario's

**Richt lijnen** : niet van toepassing; Azure Machine Learning-service biedt geen ondersteuning voor klant-lockbox.

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : niet van toepassing

## <a name="data-protection"></a>Gegevensbescherming

*Zie [Azure Security Bench Mark: Data Protection](../security/benchmarks/security-control-data-protection.md)voor meer informatie.*

### <a name="41-maintain-an-inventory-of-sensitive-information"></a>4,1: een inventaris van gevoelige informatie onderhouden

**Hulp** : Tags gebruiken om Azure-resources te helpen bij het bijhouden of verwerken van gevoelige informatie.
 
- [Tags maken en gebruiken](../azure-resource-manager/management/tag-resources.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="42-isolate-systems-storing-or-processing-sensitive-information"></a>4,2: systemen isoleren die gevoelige informatie opslaan of verwerken

**Richt lijnen** : isolatie implementeren met afzonderlijke abonnementen en beheer groepen voor afzonderlijke beveiligings domeinen, zoals omgevings type en gegevens gevoeligheids niveau. U kunt het toegangs niveau voor uw Azure-resources beperken die worden vereist door uw toepassingen en bedrijfs omgevingen. U kunt de toegang tot Azure-resources beheren via Azure RBAC.
 
- [Aanvullende Azure-abonnementen maken](../cost-management-billing/manage/create-subscription.md)

- [Beheer groepen maken](../governance/management-groups/create-management-group-portal.md)
 
- [Tags maken en gebruiken](../azure-resource-manager/management/tag-resources.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="43-monitor-and-block-unauthorized-transfer-of-sensitive-information"></a>4,3: niet-geautoriseerde overdracht van gevoelige gegevens controleren en blok keren

**Richt lijnen** : gebruik een oplossing van een derde partij van Azure Marketplace in netwerk verbindingen om te controleren op niet-geautoriseerde overdracht van gevoelige informatie en om dergelijke overdrachten te blok keren terwijl u waarschuwt voor informatie beveiliging. 

Voor het onderliggende platform, dat wordt beheerd door micro soft, behandelt micro soft alle klant inhoud als gevoelig en bescherming tegen verlies en bloot stelling van klant gegevens. Om ervoor te zorgen dat klant gegevens binnen Azure veilig blijven, heeft micro soft een reeks robuuste besturings elementen en mogelijkheden voor gegevens bescherming geïmplementeerd en onderhouden. 

- [Informatie over beveiliging van klanten in azure](../security/fundamentals/protection-customer-data.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="44-encrypt-all-sensitive-information-in-transit"></a>4,4: alle gevoelige gegevens in de overdracht versleutelen

**Hulp** : webservices die via Azure machine learning worden geïmplementeerd, ondersteunen alleen TLS-versie 1,2 die de gegevens versleuteling tijdens de overdracht afdwingt.

- [TLS gebruiken om een webservice te beveiligen via Azure Machine Learning](how-to-secure-web-service.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="45-use-an-active-discovery-tool-to-identify-sensitive-data"></a>4,5: een actief detectie hulpprogramma gebruiken om gevoelige gegevens te identificeren

**Hulp** : de functies gegevens identificatie, classificatie en verlies preventie zijn nog niet beschikbaar voor Azure machine learning. Implementeer, indien nodig, een oplossing van derden voor naleving.

Voor het onderliggende platform, dat wordt beheerd door micro soft, behandelt micro soft alle inhoud van de klant als gevoelig en gaat het om tot een uitstekende lengte van het verlies en de bloot stelling van klant gegevens. Om ervoor te zorgen dat klant gegevens binnen Azure veilig blijven, heeft micro soft een reeks robuuste besturings elementen en mogelijkheden voor gegevens bescherming geïmplementeerd en onderhouden.

- [Informatie over beveiliging van klanten in azure](../security/fundamentals/protection-customer-data.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="46-use-azure-rbac-to-manage-access-to-resources"></a>4,6: Azure RBAC gebruiken om de toegang tot resources te beheren

**Hulp** : Azure machine learning ondersteunt het gebruik van Azure Active Directory (Azure AD) om aanvragen voor machine learning bronnen goed te keuren. Met Azure AD kunt u op rollen gebaseerd toegangs beheer (RBAC) van Azure gebruiken om machtigingen te verlenen aan een beveiligingsprincipal, die een gebruiker of een service-principal van de toepassing is.

- [De toegang tot een Azure Machine Learning-werkruimte beheren](how-to-assign-roles.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="47-use-host-based-data-loss-prevention-to-enforce-access-control"></a>4,7: voor komen dat gegevens verlies op basis van host wordt gebruikt voor het afdwingen van toegangs beheer

**Richt lijnen** : niet van toepassing; deze richt lijn is bedoeld voor reken resources.

Micro soft beheert de onderliggende infra structuur voor Machine Learning en heeft strikte controles geïmplementeerd om verlies of bloot stelling van klant gegevens te voor komen.

- [Informatie over beveiliging van klanten in azure](../security/fundamentals/protection-customer-data.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : micro soft

### <a name="48-encrypt-sensitive-information-at-rest"></a>4,8: gevoelige informatie op rest versleutelen

**Hulp** : Azure machine learning slaan moment opnamen, uitvoer en logboeken op in het Azure Blob Storage-account dat is gekoppeld aan de Azure machine learning-werk ruimte en uw abonnement. Alle gegevens die zijn opgeslagen in Azure Blob Storage, worden op rest versleuteld met door micro soft beheerde sleutels. U kunt gegevens die zijn opgeslagen in Azure Blob Storage, ook versleutelen met uw eigen sleutels in Machine Learning service. 

- [Azure Machine Learning gegevens versleuteling in rust](concept-enterprise-security.md#encryption-at-rest)

- [Meer informatie over versleuteling in de rest van Azure](../security/fundamentals/encryption-atrest.md)

- [Door de klant beheerde versleutelings sleutels configureren](../storage/common/customer-managed-keys-configure-key-vault.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="49-log-and-alert-on-changes-to-critical-azure-resources"></a>4,9: wijzigingen in essentiële Azure-resources vastleggen en waarschuwen

**Hulp** : gebruik Azure monitor met het Azure-activiteiten logboek om waarschuwingen te maken wanneer wijzigingen worden aangebracht in productie-exemplaren van Azure machine learning en andere essentiële of gerelateerde resources.

- [Waarschuwingen maken voor gebeurtenissen in het Azure-activiteiten logboek](../azure-monitor/platform/alerts-activity-log.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

## <a name="vulnerability-management"></a>Beheer van beveiligingsproblemen

*Zie voor meer informatie de [Azure Security Bench Mark: beveiligingslek beheer](../security/benchmarks/security-control-vulnerability-management.md).*

### <a name="51-run-automated-vulnerability-scanning-tools"></a>5,1: automatische hulpprogram ma's voor het scannen van beveiligings problemen uitvoeren

**Richt lijnen** : als de reken resource eigendom is van micro soft, is micro soft verantwoordelijk voor het beheer van beveiligings problemen van Azure machine learning service. 

Azure Machine Learning heeft verschillende ondersteuning voor verschillende reken bronnen en zelfs uw eigen reken bronnen. Voor reken bronnen die eigendom zijn van uw organisatie, volgt u de aanbevelingen van Azure Security Center voor het uitvoeren van beveiligings evaluaties op uw virtuele machines van Azure, container installatie kopieën en SQL-servers.

- [Aanbevelingen voor de evaluatie van Azure Security Center-beveiligings problemen implementeren](../security-center/deploy-vulnerability-assessment-vm.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : gedeeld

### <a name="52-deploy-automated-operating-system-patch-management-solution"></a>5,2: geautomatiseerde oplossing voor patch beheer voor besturings systemen implementeren

**Richt lijnen** : als de reken resource eigendom is van micro soft, is micro soft verantwoordelijk voor patch beheer van Azure machine learning service. 

Azure Machine Learning heeft verschillende ondersteuning voor verschillende reken bronnen en zelfs uw eigen reken bronnen. Voor alle reken resources die eigendom zijn van uw organisatie, gebruikt u Azure Automation Updatebeheer om ervoor te zorgen dat de meest recente beveiligings updates worden geïnstalleerd op uw Windows-en Linux-Vm's. Zorg ervoor dat Windows Update is ingeschakeld en is ingesteld om automatisch te worden bijgewerkt voor virtuele Windows-machines.

- [Updatebeheer configureren voor virtuele machines in azure](../automation/update-management/overview.md)

- [Meer informatie over Azure-beveiligings beleid bewaakt door Security Center](../security-center/policy-reference.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : gedeeld

### <a name="53-deploy-an-automated-patch-management-solution-for-third-party-software-titles"></a>5,3: een geautomatiseerde oplossing voor patch beheer implementeren voor titels van software van derden

**Hulp** : Azure machine learning heeft verschillende ondersteuning voor verschillende reken bronnen en zelfs uw eigen reken bronnen. Voor reken bronnen die eigendom zijn van uw organisatie, gebruikt u een oplossing voor patch beheer van derden. Klanten die al gebruikmaken van Configuration Manager in hun omgeving kunnen System Center Updates Publisher ook gebruiken om aangepaste updates te publiceren in Windows Server Update service. Op deze manier kunnen Updatebeheer patches voor machines die gebruikmaken van Configuration Manager als update opslagplaats met software van derden.

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="54-compare-back-to-back-vulnerability-scans"></a>5,4: vergelijken van back-to-back-problemen

**Hulp** : Azure machine learning heeft verschillende ondersteuning voor verschillende reken bronnen en zelfs uw eigen reken bronnen. Voor reken bronnen die eigendom zijn van uw organisatie, volgt u aanbevelingen van Azure Security Center voor het uitvoeren van evaluatie van beveiligings problemen op uw Azure virtual machines, container installatie kopieën en SQL-servers. Scan resultaten worden met consistente intervallen uitgevoerd en vergelijken de resultaten met eerdere scans om te controleren of beveiligings problemen zijn opgelost. Wanneer u aanbevelingen voor beveiligings beheer gebruikt die worden voorgesteld door Azure Security Center, kunt u in de portal van de geselecteerde oplossing draaien om historische scan gegevens weer te geven.

- [Aanbevelingen voor de evaluatie van Azure Security Center-beveiligings problemen implementeren](../security-center/deploy-vulnerability-assessment-vm.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="55-use-a-risk-rating-process-to-prioritize-the-remediation-of-discovered-vulnerabilities"></a>5,5: een risico classificatie proces gebruiken om prioriteit te geven aan het herstel van ontdekte beveiligings problemen

**Richt lijnen** : niet van toepassing; deze richt lijn is bedoeld voor reken resources.

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : niet van toepassing

## <a name="inventory-and-asset-management"></a>Inventarisatie en asset-management

*Zie [Azure Security Bench Mark: Inventory and Asset Management](../security/benchmarks/security-control-inventory-asset-management.md)voor meer informatie.*

### <a name="61-use-automated-asset-discovery-solution"></a>6,1: automatische Asset-detectie oplossing gebruiken

**Hulp** : Azure resource Graph gebruiken om resources te zoeken en te detecteren (zoals compute, opslag, netwerk, poorten en protocollen enz.) in uw abonnementen.  Zorg ervoor dat de juiste (Lees-) machtigingen voor uw Tenant zijn en alle Azure-abonnementen en de resources in uw abonnementen inventariseren.

Hoewel klassieke Azure-resources kunnen worden gedetecteerd via Azure resource Graph Explorer, is het raadzaam om Azure Resource Manager resources te maken en te gebruiken.

- [Query's maken met Azure Resource Graph Explorer](../governance/resource-graph/first-query-portal.md)

- [Uw Azure-abonnementen weer geven](/powershell/module/az.accounts/get-azsubscription?view=azps-3.0.0)

- [Meer informatie over Azure RBAC](../role-based-access-control/overview.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="62-maintain-asset-metadata"></a>6,2: meta gegevens van activa onderhouden

**Richt lijnen** : Tags Toep assen op Azure-resources, meta gegevens toevoegen aan de logische organisatie op basis van een taxonomie.

- [Tags maken en gebruiken](../azure-resource-manager/management/tag-resources.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="63-delete-unauthorized-azure-resources"></a>6,3: niet-geautoriseerde Azure-resources verwijderen

**Richt lijnen** : Gebruik labels, beheer groepen en afzonderlijke abonnementen, indien van toepassing, om assets te organiseren en bij te houden. Sluit de inventaris regel matig af en zorg ervoor dat niet-geautoriseerde resources tijdig worden verwijderd uit het abonnement.
 
 
 
- [ Aanvullende Azure-abonnementen maken](../cost-management-billing/manage/create-subscription.md)
 
 
 
- [ Beheer groepen maken](../governance/management-groups/create-management-group-portal.md)
 
 
 
- [ Tags maken en gebruiken](../azure-resource-manager/management/tag-resources.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="64-define-and-maintain-an-inventory-of-approved-azure-resources"></a>6,4: een inventaris van goedgekeurde Azure-resources definiëren en onderhouden

**Richt lijnen** : Maak een inventaris van goedgekeurde Azure-resources en goedgekeurde software voor reken resources conform uw organisatie behoeften.

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="65-monitor-for-unapproved-azure-resources"></a>6,5: monitor voor niet-goedgekeurde Azure-resources

**Hulp: gebruik** Azure Policy om beperkingen toe te voegen voor het type resources dat kan worden gemaakt in klant abonnementen met behulp van de volgende ingebouwde beleids definities:

* Niet toegestane resourcetypen
* Toegestane brontypen

Daarnaast kunt u met de Azure-resource grafiek bronnen in de abonnementen opvragen/ontdekken.

- [Azure Policy configureren en beheren](../governance/policy/tutorials/create-and-manage.md)

- [Query's maken met Azure Graph](../governance/resource-graph/first-query-portal.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="66-monitor-for-unapproved-software-applications-within-compute-resources"></a>6,6: monitor voor niet-goedgekeurde software toepassingen binnen reken resources

**Hulp** : Azure machine learning heeft verschillende ondersteuning voor verschillende reken bronnen en zelfs uw eigen reken bronnen. Voor reken resources die eigendom zijn van uw organisatie, gebruikt u Azure Automation Wijzigingen bijhouden en inventaris om het verzamelen van inventaris gegevens van uw Windows-en Linux-Vm's te automatiseren. De software naam, versie, uitgever en tijd van vernieuwen zijn beschikbaar via de Azure Portal. Als u de software-installatie datum en andere informatie wilt ophalen, schakelt u Diagnostische gegevens op gast niveau in en stuurt u de Windows-gebeurtenis logboeken naar Log Analytics werk ruimte.

- [Azure Automation voorraad verzameling inschakelen voor een virtuele machine](../automation/automation-tutorial-installed-software.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : gedeeld

### <a name="67-remove-unapproved-azure-resources-and-software-applications"></a>6,7: niet-goedgekeurde Azure-resources en software toepassingen verwijderen

**Hulp** : Azure machine learning heeft verschillende ondersteuning voor verschillende reken bronnen en zelfs uw eigen reken bronnen. Voor reken resources die eigendom zijn van uw organisatie, gebruikt u Azure Security Center de File Integrity Monitoring (FIM) voor het identificeren van alle software die op Vm's is geïnstalleerd. Een andere optie die kan worden gebruikt in plaats van of in combi natie met FIM is Azure Automation Wijzigingen bijhouden en inventaris voor het verzamelen van inventaris van uw Linux-en Windows-Vm's. 

U kunt uw eigen proces voor het verwijderen van onbevoegde software implementeren. U kunt ook een oplossing van derden gebruiken om niet-goedgekeurde software te identificeren.

Verwijder Azure-resources wanneer ze niet meer nodig zijn.

- [Bestands integriteit controleren gebruiken](../security-center/security-center-file-integrity-monitoring.md)

- [Meer informatie over Azure Automation Wijzigingen bijhouden en inventaris](../automation/change-tracking/overview.md)

- [Inventarisatie van virtuele Azure-machines inschakelen](../automation/automation-tutorial-installed-software.md)

- [Azure-resource groep en-resource verwijderen](../azure-resource-manager/management/delete-resource-group.md)

**Azure Security Center bewaking** : Ja

**Verantwoordelijkheid** : gedeeld

### <a name="68-use-only-approved-applications"></a>6,8: alleen goedgekeurde toepassingen gebruiken

**Hulp** : Azure machine learning heeft verschillende ondersteuning voor verschillende reken bronnen en zelfs uw eigen reken bronnen. Voor reken resources die eigendom zijn van uw organisatie, kunt u Azure Security Center adaptieve toepassings besturings elementen gebruiken om ervoor te zorgen dat alleen geautoriseerde software wordt uitgevoerd en alle niet-geautoriseerde software wordt geblokkeerd voor het uitvoeren van Azure Virtual Machines.

- [Azure Security Center adaptieve toepassings besturings elementen gebruiken](../security-center/security-center-adaptive-application.md)

**Azure Security Center bewaking** : Ja

**Verantwoordelijkheid** : gedeeld

### <a name="69-use-only-approved-azure-services"></a>6,9: alleen goedgekeurde Azure-Services gebruiken

**Hulp: gebruik** Azure Policy om beperkingen toe te voegen voor het type resources dat kan worden gemaakt in klant abonnementen met behulp van de volgende ingebouwde beleids definities:

* Niet toegestane resourcetypen
* Toegestane brontypen

Daarnaast gebruikt u de resource grafiek van Azure om resources in de abonnementen op te vragen en te detecteren.

- [Azure Policy configureren en beheren](../governance/policy/tutorials/create-and-manage.md)

- [Query's maken met Azure resource Graph](../governance/resource-graph/first-query-portal.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="610-maintain-an-inventory-of-approved-software-titles"></a>6,10: een inventaris van goedgekeurde software titels onderhouden

**Hulp** : Azure machine learning heeft verschillende ondersteuning voor verschillende reken bronnen en zelfs uw eigen reken bronnen. Voor alle reken resources die eigendom zijn van uw organisatie, gebruikt u Azure Security Center adaptieve toepassings besturings elementen om op te geven welke bestands typen een regel kan of niet van toepassing is op.

Implementeer een oplossing van derden als adaptieve toepassings besturings elementen niet aan de vereiste voldoen.

- [Azure Security Center adaptieve toepassings besturings elementen gebruiken](../security-center/security-center-adaptive-application.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : niet van toepassing

### <a name="611-limit-users-ability-to-interact-with-azure-resource-manager"></a>6,11: de mogelijkheid van gebruikers om te communiceren met Azure Resource Manager beperken

**Richt lijnen** : gebruik de voorwaardelijke toegang van Azure AD om de interactie van gebruikers met Azure Resources Manager te beperken door ' toegang blok keren ' te configureren voor de app Microsoft Azure management.
 
- [Voorwaardelijke toegang configureren om de toegang tot Azure-bronnen beheer te blok keren](../role-based-access-control/conditional-access-azure-management.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="612-limit-users-ability-to-execute-scripts-in-compute-resources"></a>6,12: de mogelijkheid van gebruikers om scripts in reken bronnen uit te voeren, beperken

**Hulp** : Azure machine learning heeft verschillende ondersteuning voor verschillende reken bronnen en zelfs uw eigen reken bronnen. Voor reken resources die eigendom zijn van uw organisatie, afhankelijk van het type scripts, kunt u specifieke configuraties van het besturings systeem of bronnen van derden gebruiken om de mogelijkheid van gebruikers om scripts uit te voeren in azure Compute-resources te beperken.  U kunt ook Azure Security Center adaptieve toepassings besturings elementen gebruiken om ervoor te zorgen dat alleen geautoriseerde software wordt uitgevoerd en alle niet-geautoriseerde software wordt geblokkeerd voor uitvoering op Azure Virtual Machines.

- [De uitvoering van Power shell-scripts beheren in Windows-omgevingen](/powershell/module/microsoft.powershell.security/set-executionpolicy?view=powershell-6)

- [Azure Security Center adaptieve toepassings besturings elementen gebruiken](../security-center/security-center-adaptive-application.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : niet van toepassing

### <a name="613-physically-or-logically-segregate-high-risk-applications"></a>6,13: toepassingen met een hoog risico fysiek of logisch scheiden

**Richt lijnen** : niet van toepassing; deze aanbeveling is bedoeld voor webtoepassingen die worden uitgevoerd op Azure App Service of reken bronnen.

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : niet van toepassing

## <a name="secure-configuration"></a>Veilige configuratie

*Zie [Azure Security Bench Mark: Secure Configuration](../security/benchmarks/security-control-secure-configuration.md)(Engelstalig) voor meer informatie.*

### <a name="71-establish-secure-configurations-for-all-azure-resources"></a>7,1: veilige configuraties instellen voor alle Azure-resources

**Hulp** : Definieer en implementeer standaard beveiligings configuraties voor uw Azure machine learning-service met Azure Policy. Gebruik Azure Policy aliassen in de naam ruimte ' micro soft. MachineLearning ' om aangepaste beleids regels te maken om de configuratie van uw Azure Machine Learning Services te controleren of af te dwingen.

Azure Resource Manager kunt de sjabloon in JavaScript Object Notation (JSON) exporteren, die moet worden gecontroleerd om ervoor te zorgen dat de configuraties voldoen aan de beveiligings vereisten voor uw organisatie.

U kunt ook de aanbevelingen van Azure Security Center gebruiken als een veilige configuratie basislijn voor uw Azure-resources.

Azure Machine Learning biedt volledige ondersteuning voor git-opslag plaatsen voor het bijhouden van werk. u kunt opslag plaatsen rechtstreeks op het bestands systeem van de gedeelde werk ruimte klonen, Git op uw lokale werk station gebruiken en ervoor zorgen dat veilige configuraties van toepassing zijn op code bronnen als onderdeel van uw Machine Learning omgeving.

- [Beschik bare Azure Policy aliassen weer geven](/powershell/module/az.resources/get-azpolicyalias?view=azps-3.3.0)

- [Zelfstudie: Beleidsregels voor het afdwingen van naleving maken en beheren](../governance/policy/tutorials/create-and-manage.md)

- [Eén en meerdere resources exporteren naar een sjabloon in Azure Portal](../azure-resource-manager/templates/export-template-portal.md)

- [Aanbevelingen voor beveiliging: een naslaggids](../security-center/recommendations-reference.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="72-establish-secure-operating-system-configurations"></a>7,2: veilige configuraties van besturings systemen instellen

**Richt lijnen** : als de reken resource eigendom is van micro soft, is micro soft verantwoordelijk voor de veilige configuratie van Azure machine learning-service door het besturings systeem.

Azure Machine Learning heeft verschillende ondersteuning voor verschillende reken bronnen en zelfs uw eigen reken bronnen. Gebruik Azure Security Center aanbevelingen voor reken bronnen die eigendom zijn van uw organisatie om beveiligings configuraties voor alle reken resources te onderhouden.  Daarnaast kunt u aangepaste installatie kopieën van besturings systemen of de configuratie van Azure Automation status gebruiken om de beveiligings configuratie te bepalen van het besturings systeem dat door uw organisatie wordt vereist.

- [Azure Security Center aanbevelingen bewaken](../security-center/security-center-recommendations.md)

- [Aanbevelingen voor beveiliging: een naslaggids](../security-center/recommendations-reference.md)

- [Overzicht van Azure Automation status configuratie](../automation/automation-dsc-overview.md)

- [Een VHD uploaden en gebruiken om nieuwe Windows-Vm's in azure te maken](../virtual-machines/windows/upload-generalized-managed.md)

- [Een virtuele Linux-machine maken op basis van een aangepaste schijf met de Azure CLI](../virtual-machines/linux/upload-vhd.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : gedeeld

### <a name="73-maintain-secure-azure-resource-configurations"></a>7,3: Beveilig Azure-resource configuraties onderhouden

**Hulp** : gebruik Azure Policy [deny] en [implementeren indien niet aanwezig] voor het afdwingen van beveiligde instellingen voor uw Azure-resources. Daarnaast kunt u Azure Resource Manager sjablonen gebruiken om de beveiligings configuratie van uw Azure-resources te onderhouden die uw organisatie nodig heeft. 
 
 
 
- [Azure Policy effecten begrijpen](../governance/policy/concepts/effects.md)
 
- [Beleidsregels voor het afdwingen van naleving maken en beheren](../governance/policy/tutorials/create-and-manage.md)
 
- [ Overzicht van Azure Resource Manager sjablonen](../azure-resource-manager/templates/overview.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="74-maintain-secure-operating-system-configurations"></a>7,4: veilige configuraties van besturings systemen onderhouden

**Richt lijnen** : als de reken resource eigendom is van micro soft, is micro soft verantwoordelijk voor de veilige configuratie van Azure machine learning-service door het besturings systeem.

Azure Machine Learning heeft verschillende ondersteuning voor verschillende reken bronnen en zelfs uw eigen reken bronnen. Voor reken resources die eigendom zijn van uw organisatie, volgt u aanbevelingen van Azure Security Center over het uitvoeren van evaluatie van beveiligings problemen op uw Azure Compute-resources.  Daarnaast kunt u Azure Resource Manager sjablonen, aangepaste installatie kopieën van besturings systemen of de configuratie van Azure Automation status gebruiken om de beveiligings configuratie van het besturings systeem te onderhouden dat door uw organisatie wordt vereist.   De micro soft-sjablonen voor virtuele machines in combi natie met de configuratie van de Azure Automation status kunnen helpen bij de vergadering en het onderhouden van de beveiligings vereisten. 

Houd er rekening mee dat installatie kopieën van virtuele machines van Azure Marketplace die door micro soft zijn gepubliceerd, worden beheerd en beheerd door micro soft. 

- [Aanbevelingen voor de evaluatie van Azure Security Center-beveiligings problemen implementeren](../security-center/deploy-vulnerability-assessment-vm.md)

- [Een virtuele Azure-machine maken op basis van een ARM-sjabloon](../virtual-machines/windows/ps-template.md)

- [Overzicht van Azure Automation status configuratie](../automation/automation-dsc-overview.md)

- [Een virtuele Windows-machine maken in de Azure Portal ](../virtual-machines/windows/quick-create-portal.md)

- [Informatie over het downloaden van de VM-sjabloon](../virtual-machines/windows/download-template.md)

- [Voorbeeld van een script voor het uploaden van een VHD naar Azure om een nieuwe VM te maken](../virtual-machines/scripts/virtual-machines-windows-powershell-upload-generalized-script.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : gedeeld

### <a name="75-securely-store-configuration-of-azure-resources"></a>7,5: de configuratie van Azure-resources veilig opslaan

**Richt lijnen** : als u aangepaste Azure Policy definities gebruikt voor uw machine learning of gerelateerde resources, gebruikt u Azure opslag plaatsen om uw code veilig op te slaan en te beheren.

Azure Machine Learning biedt volledige ondersteuning voor git-opslag plaatsen voor het bijhouden van werk. u kunt opslag plaatsen rechtstreeks op het bestands systeem van de gedeelde werk ruimte klonen, Git op uw lokale werk station gebruiken en ervoor zorgen dat veilige configuraties van toepassing zijn op code bronnen als onderdeel van uw Machine Learning omgeving.

- [Code opslaan in azure DevOps](/azure/devops/repos/git/gitworkflow?view=azure-devops)

- [Documentatie voor Azure opslag plaatsen](/azure/devops/repos/index?view=azure-devops)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="76-securely-store-custom-operating-system-images"></a>7,6: aangepaste installatie kopieën van een besturings systeem veilig opslaan

**Hulp** : Azure machine learning heeft verschillende ondersteuning voor verschillende reken bronnen en zelfs uw eigen reken bronnen. Voor reken resources die eigendom zijn van uw organisatie, kunt u gebruikmaken van Azure RBAC (op rollen gebaseerd toegangs beheer) om ervoor te zorgen dat alleen geautoriseerde gebruikers toegang hebben tot uw aangepaste installatie kopieën. Een galerie met gedeelde Azure-afbeeldingen gebruiken u kunt uw installatie kopieën delen met verschillende gebruikers, service-principals of Azure AD-groepen in uw organisatie. Container installatie kopieën opslaan in Azure Container Registry en Azure RBAC gebruiken om ervoor te zorgen dat alleen gemachtigde gebruikers toegang hebben.

- [Meer informatie over Azure RBAC](../role-based-access-control/rbac-and-directory-admin-roles.md)

- [Meer informatie over Azure RBAC voor Container Registry](../container-registry/container-registry-roles.md)

- [Azure RBAC configureren](../role-based-access-control/quickstart-assign-role-user-portal.md)

- [Overzicht van Galerie gedeelde afbeeldingen](../virtual-machines/windows/shared-image-galleries.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : niet van toepassing

### <a name="77-deploy-configuration-management-tools-for-azure-resources"></a>7,7: hulpprogram ma's voor configuratie beheer voor Azure-resources implementeren

**Hulp** : gebruik Azure Policy aliassen in de naam ruimte ' micro soft. MachineLearning ' om aangepaste beleids regels te maken om systeem configuraties te Signa lering, te controleren en af te dwingen. Ontwikkel bovendien een proces en pijp lijn voor het beheren van beleids uitzonderingen.

- [Azure Policy configureren en beheren](../governance/policy/tutorials/create-and-manage.md)

- [Aliassen gebruiken](../governance/policy/concepts/definition-structure.md#aliases)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="78-deploy-configuration-management-tools-for-operating-systems"></a>7,8: hulpprogram ma's voor configuratie beheer voor besturings systemen implementeren

**Richt lijnen** : als de reken resource eigendom is van micro soft, is micro soft verantwoordelijk voor de veilige configuratie van Azure machine learning service.

Azure Machine Learning heeft verschillende ondersteuning voor verschillende reken bronnen en zelfs uw eigen reken bronnen. Voor reken resources die eigendom zijn van uw organisatie, gebruikt u Azure Automation status configuratie voor desired state Configuration (DSC)-knoop punten in een Cloud of on-premises Data Center. U kunt eenvoudig computers onboarden, de declaratieve configuraties toewijzen en rapporten weer geven met de naleving van elke computer die u hebt opgegeven. 

- [De configuratie van Azure Automation-status inschakelen](../automation/automation-dsc-onboarding.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : gedeeld

### <a name="79-implement-automated-configuration-monitoring-for-azure-resources"></a>7,9: geautomatiseerde configuratie bewaking voor Azure-resources implementeren

**Hulp** : gebruik Azure Security Center om basislijn scans voor uw Azure-resources uit te voeren. Gebruik Azure Policy bovendien om een waarschuwing te krijgen en Azure-resource configuraties te controleren.
 
 
 
- [ Aanbevelingen herstellen in Azure Security Center](../security-center/security-center-remediate-recommendations.md)

**Azure Security Center bewaking** : Ja

**Verantwoordelijkheid** : klant

### <a name="710-implement-automated-configuration-monitoring-for-operating-systems"></a>7,10: geautomatiseerde configuratie bewaking voor besturings systemen implementeren

**Richt lijnen** : als de reken resource eigendom is van micro soft, is micro soft verantwoordelijk voor het automatisch beveiligen van de configuratie van Azure machine learning service.

Azure Machine Learning heeft verschillende ondersteuning voor verschillende reken bronnen en zelfs uw eigen reken bronnen. Voor reken resources die eigendom zijn van uw organisatie, gebruikt u Azure Security Center COMPUTE- &amp; apps en volgt u de aanbevelingen voor vm's en servers en containers.

- [Aanbevelingen van Azure Security Center voor containers](../security-center/container-security.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : gedeeld

### <a name="711-manage-azure-secrets-securely"></a>7,11: Azure-geheimen veilig beheren

**Richt lijnen** : gebruik beheerde identiteiten in combi natie met Azure Key Vault om het geheime beheer van uw Cloud toepassingen te vereenvoudigen.

Azure Machine Learning ondersteunt versleuteling van gegevens opslag met door de klant beheerde sleutels, u moet de sleutel draaien en intrekken per organisatie beveiligings-en nalevings vereisten beheren. 

Gebruik Azure Key Vault om geheimen door te geven aan externe uitvoeringen veilig uit te voeren in plaats van een lees bewerking in uw trainings scripts.

- [Azure Machine Learning door de klant beheerde sleutels](concept-enterprise-security.md#azure-blob-storage)

- [Verificatie referentie geheimen gebruiken in Azure Machine Learning training-uitvoeringen](how-to-use-secrets-in-runs.md)

- [Beheerde identiteiten gebruiken voor Azure-resources](../azure-app-configuration/howto-integrate-azure-managed-service-identity.md)

- [Een Key Vault maken](../key-vault/secrets/quick-create-portal.md)

- [Verifiëren bij Key Vault](../key-vault/general/authentication.md)

- [Toegangs beleid voor Key Vault toewijzen](../key-vault/general/assign-access-policy-portal.md)

**Azure Security Center bewaking** : Ja

**Verantwoordelijkheid** : klant

### <a name="712-manage-identities-securely-and-automatically"></a>7,12: identiteiten veilig en automatisch beheren

**Hulp** : Azure machine learning ondersteunt zowel ingebouwde rollen als de mogelijkheid om aangepaste rollen te maken. Gebruik beheerde identiteiten om Azure-Services te voorzien van een automatisch beheerde identiteit in azure AD. Met beheerde identiteiten kunt u zich verifiëren bij elke service die ondersteuning biedt voor Azure AD-verificatie, met inbegrip van Key Vault, zonder dat u referenties in uw code hoeft op te geven.

 
- [De toegang tot een Azure Machine Learning-werkruimte beheren](how-to-assign-roles.md)

- [Beheerde identiteiten voor Azure-resources configureren](../active-directory/managed-identities-azure-resources/qs-configure-portal-windows-vm.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="713-eliminate-unintended-credential-exposure"></a>7,13: onbedoelde referentie blootstelling elimineren

**Richt lijnen** : referentie scanner implementeren om referenties in code te identificeren. Referentie scanner stimuleert ook het verplaatsen van gedetecteerde referenties naar veiliger locaties, zoals Azure Key Vault. 

- [Referentie scanner instellen](https://secdevtools.azurewebsites.net/helpcredscan.html)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

## <a name="malware-defense"></a>Beveiliging tegen malware

*Zie voor meer informatie de [Azure Security Bench Mark: beveiliging tegen schadelijke software](../security/benchmarks/security-control-malware-defense.md).*

### <a name="81-use-centrally-managed-antimalware-software"></a>8,1: centraal beheerde antimalware-software gebruiken

**Hulp** : micro soft anti-malware is ingeschakeld op de onderliggende host die ondersteuning biedt voor Azure-Services (bijvoorbeeld Azure machine learning), maar wordt niet uitgevoerd op de inhoud van de klant.

Azure Machine Learning heeft verschillende ondersteuning voor verschillende reken bronnen en zelfs uw eigen reken bronnen. Voor reken resources die eigendom zijn van uw organisatie, gebruikt u micro soft antimalware voor Azure om uw resources voortdurend te controleren en te beschermen. Gebruik voor Linux een oplossing van antimalware van derden. Gebruik ook de bedreigings detectie van Azure Security Center voor gegevens Services om malware te detecteren die is geüpload naar opslag accounts.

- [Micro soft antimalware voor Azure configureren](../security/fundamentals/antimalware.md)

- [Bescherming tegen bedreiging in Azure Security Center](../security-center/azure-defender.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : gedeeld

### <a name="82-pre-scan-files-to-be-uploaded-to-non-compute-azure-resources"></a>8,2: scan bestanden die moeten worden geüpload naar niet-reken resources van Azure

**Hulp** : micro soft anti-malware is ingeschakeld op de onderliggende host die ondersteuning biedt voor Azure-Services (bijvoorbeeld Azure machine learning), maar wordt niet uitgevoerd op de inhoud van de klant.

Het is uw verantwoordelijkheid om vooraf te scannen op inhoud die wordt geüpload naar niet-reken resources van Azure. Micro soft heeft geen toegang tot klant gegevens en kan daarom geen anti-malware scans uitvoeren van klant inhoud namens u.

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="83-ensure-antimalware-software-and-signatures-are-updated"></a>8,3: controleren of antimalware-software en hand tekeningen zijn bijgewerkt

**Hulp** : micro soft anti-malware is ingeschakeld en wordt onderhouden voor de onderliggende host die ondersteuning biedt voor Azure-Services (bijvoorbeeld Azure machine learning), maar wordt niet uitgevoerd op de inhoud van de klant.

Azure Machine Learning heeft verschillende ondersteuning voor verschillende reken bronnen en zelfs uw eigen reken bronnen. Voor alle reken resources die eigendom zijn van uw organisatie, volgt u aanbevelingen in Azure Security Center, reken &amp; apps om ervoor te zorgen dat alle eind punten up-to-date zijn met de nieuwste hand tekeningen. Gebruik voor Linux een oplossing van antimalware van derden.

- [Micro soft antimalware voor Azure implementeren](../security/fundamentals/antimalware.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : gedeeld

## <a name="data-recovery"></a>Gegevensherstel

*Zie [Azure Security Bench Mark: Data Recovery](../security/benchmarks/security-control-data-recovery.md)(Engelstalig) voor meer informatie.*

### <a name="91-ensure-regular-automated-back-ups"></a>9,1: controleren op regel matige automatische back-ups

**Hulp** : het beheer van gegevens herstel in de machine learning-service is via gegevens beheer in verbonden gegevens archieven. Zorg ervoor dat u de richt lijnen voor gegevens herstel voor verbonden winkels opvolgt om een back-up te maken van gegevens per organisatie beleid van de klant.

- [Bestanden herstellen vanuit back-up van Azure virtual machine](../backup/backup-azure-restore-files-from-vm.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="92-perform-complete-system-backups-and-backup-any-customer-managed-keys"></a>9,2: volledige back-ups van het systeem uitvoeren en een back-up maken van door de klant beheerde sleutels

**Richt lijnen** : gegevens back-up in machine learning-service is via gegevens beheer in verbonden gegevens archieven. Schakel Azure Backup voor Vm's in en configureer de gewenste frequentie en bewaar perioden. Maak een back-up van door de klant beheerde sleutels in Azure Key Vault.

- [Bestanden herstellen vanuit back-up van Azure virtual machine](../backup/backup-azure-restore-files-from-vm.md)
- [Key Vault sleutels herstellen in azure](/powershell/module/azurerm.keyvault/restore-azurekeyvaultkey?view=azurermps-6.13.0)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="93-validate-all-backups-including-customer-managed-keys"></a>9,3: alle back-ups valideren, inclusief door de klant beheerde sleutels

**Richt lijnen** : validatie van gegevens back-ups in machine learning-service is via gegevens beheer in verbonden gegevens archieven. Periodiek gegevens herstel van inhoud in Azure Backup uitvoeren. Zorg ervoor dat u een back-up van door de klant beheerde sleutels kunt herstellen.

- [Bestanden herstellen vanuit een back-up van een virtuele Azure-machine](../backup/backup-azure-restore-files-from-vm.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="94-ensure-protection-of-backups-and-customer-managed-keys"></a>9,4: zorg voor de bescherming van back-ups en door de klant beheerde sleutels

**Richt lijnen** : voor on-premises back-ups wordt versleuteling in rust gegeven met behulp van de wachtwoordzin die u opgeeft bij het maken van een back-up naar Azure. Gebruik Azure op rollen gebaseerd toegangs beheer voor het beveiligen van back-ups en door de klant beheerde sleutels. 

Schakel de beveiliging van zacht verwijderen en opschonen in Key Vault in om sleutels te beschermen tegen onbedoelde of schadelijke verwijdering. Als Azure Storage wordt gebruikt voor het opslaan van back-ups, schakelt u de optie voor het tijdelijk verwijderen in om uw gegevens op te slaan en te herstellen wanneer blobs of BLOB-moment opnamen worden verwijderd.
 
 
- [Meer informatie over Azure RBAC](../role-based-access-control/overview.md)

- [Zacht verwijderen en beveiliging opschonen inschakelen in Key Vault](../storage/blobs/soft-delete-blob-overview.md?tabs=azure-portal)

- [Zacht verwijderen voor Azure Blob Storage](../storage/blobs/soft-delete-blob-overview.md?tabs=azure-portal)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

## <a name="incident-response"></a>Reageren op incidenten

*Zie [Azure Security Bench Mark: Incident Response](../security/benchmarks/security-control-incident-response.md)(Engelstalig) voor meer informatie.*

### <a name="101-create-an-incident-response-guide"></a>10,1: een hand leiding voor reactie op incidenten maken

**Hulp** : een antwoord gids voor incidenten ontwikkelen voor uw organisatie. Zorg ervoor dat er schriftelijke incidenten abonnementen zijn die alle personeels rollen definiëren, evenals de fasen van het verwerken van incidenten en het beheer van de detectie tot een beoordeling van het incident. 

- [Richt lijnen voor het bouwen van uw eigen beveiligings incident antwoord proces](https://msrc-blog.microsoft.com/2019/07/01/inside-the-msrc-building-your-own-security-incident-response-process/)

- [Micro soft Security Response Center anatomie van een incident](https://msrc-blog.microsoft.com/2019/06/27/inside-the-msrc-anatomy-of-a-ssirp-incident/)

- [De verwerkings gids voor het computer beveiligings incident van het NIST gebruiken om u te helpen bij het maken van uw eigen reactie plan voor incidenten](https://csrc.nist.gov/publications/detail/sp/800-61/rev-2/final)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="102-create-an-incident-scoring-and-prioritization-procedure"></a>10,2: een beoordelings procedure voor incidenten en prioriteits procedures maken

**Hulp** : Azure Security Center wijst aan elke waarschuwing een Ernst toe om u te helpen bepalen welke waarschuwingen het eerst moeten worden onderzocht. De ernst is gebaseerd op de manier waarop vertrouwen Security Center zich in de zoek actie bevindt of de analyse die wordt gebruikt om de waarschuwing te geven, evenals het betrouwbaarheids niveau dat er schadelijke intentie is achter de activiteit die tot de waarschuwing heeft geleid.

Markeer bovendien abonnementen met tags en maak een naamgevings systeem voor het identificeren en categoriseren van Azure-resources, met name voor de verwerking van gevoelige gegevens. Het is uw verantwoordelijkheid om prioriteit te geven aan het herstel van waarschuwingen op basis van de ernst van de Azure-resources en-omgeving waar het incident heeft plaatsgevonden.

- [Beveiligingswaarschuwingen in Azure Security Center](../security-center/security-center-alerts-overview.md)

- [Tags gebruiken om Azure-resources te organiseren](../azure-resource-manager/management/tag-resources.md)

**Azure Security Center bewaking** : Ja

**Verantwoordelijkheid** : klant

### <a name="103-test-security-response-procedures"></a>10,3: procedures voor beveiligings antwoorden testen

**Richt lijnen** : oefent oefeningen uit om de respons mogelijkheden van uw systeem te testen op een reguliere uitgebracht om uw Azure-resources te beschermen. Identificeer zwakke punten en tussen ruimten en wijzig vervolgens uw reactie schema naar wens.

- [Publicatie van het NIST-hand leiding voor het testen, trainen en uitoefenen van Program Ma's voor IT-plannen en-mogelijkheden](https://csrc.nist.gov/publications/detail/sp/800-84/final)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="104-provide-security-incident-contact-details-and-configure-alert-notifications-for-security-incidents"></a>10,4: contact gegevens van het beveiligings incident opgeven en waarschuwings meldingen configureren voor beveiligings incidenten

**Hulp** : contact gegevens van beveiligings incidenten worden door micro soft gebruikt om contact met u op te nemen als het micro soft Security Response Center (MSRC) detecteert dat uw gegevens zijn geopend door een onrecht matige of niet-gemachtigde partij. Bekijk incidenten na het feit om te controleren of de problemen zijn opgelost.

- [De Azure Security Center Security-contact persoon instellen](../security-center/security-center-provide-security-contact-details.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="105-incorporate-security-alerts-into-your-incident-response-system"></a>10,5: beveiligings waarschuwingen opnemen in uw reactie systeem van uw incident

**Hulp** : exporteer uw Azure Security Center waarschuwingen en aanbevelingen met behulp van de functie continue export om Risico's voor Azure-resources te identificeren. Met doorlopend exporteren kunt u waarschuwingen en aanbevelingen hand matig of op een doorlopende manier exporteren. U kunt de Azure Security Center Data Connector gebruiken om de waarschuwingen naar Azure Sentinel te streamen.

- [Continue export configureren](../security-center/continuous-export.md)

- [Waarschuwingen streamen naar Azure Sentinel](../sentinel/connect-azure-security-center.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

### <a name="106-automate-the-response-to-security-alerts"></a>10,6: de reactie op beveiligings waarschuwingen automatiseren

**Hulp** : werk stroom automatisering gebruiken Azure Security Center om automatisch reacties te activeren op beveiligings waarschuwingen en aanbevelingen voor het beveiligen van uw Azure-resources.

- [Werk stroom automatisering configureren in Security Center](../security-center/workflow-automation.md)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : klant

## <a name="penetration-tests-and-red-team-exercises"></a>Penetratietests en Red Team-oefeningen

*Zie [Azure Security Bench Mark: Indringings tests en rode team oefeningen](../security/benchmarks/security-control-penetration-tests-red-team-exercises.md)voor meer informatie.*

### <a name="111-conduct-regular-penetration-testing-of-your-azure-resources-and-ensure-remediation-of-all-critical-security-findings"></a>11,1: voert regel matig indringings tests van uw Azure-resources uit en zorgt voor herbemiddeling van alle essentiële beveiligings resultaten

**Richt lijnen** : Volg de stappen voor het testen van de Microsoft Cloud indringings regels om ervoor te zorgen dat uw indringings tests niet worden geschonden door het micro soft-beleid. Gebruik de strategie van micro soft en de uitvoering van de implementatie van de indringing van een live site in de Cloud, services en toepassingen die door micro soft worden beheerd.

- [Regels van betrokkenheid voor het testen van indringing](https://www.microsoft.com/msrc/pentest-rules-of-engagement?rtc=1)

- [Microsoft Cloud rode teams](https://gallery.technet.microsoft.com/Cloud-Red-Teaming-b837392e)

**Azure Security Center bewaking** : niet van toepassing

**Verantwoordelijkheid** : gedeeld

## <a name="next-steps"></a>Volgende stappen

- Zie de [Azure Security-Bench Mark](../security/benchmarks/overview.md)
- Meer informatie over [Azure-beveiligings basislijnen](../security/benchmarks/security-baselines-overview.md)