---
title: Door de klant beheerde sleutels voor uw Azure Batch account configureren met Azure Key Vault en beheerde identiteit
description: Meer informatie over het versleutelen van batch-gegevens met behulp van sleutels
author: pkshultz
ms.topic: how-to
ms.date: 07/17/2020
ms.author: peshultz
ms.openlocfilehash: 35780f915247e88a5de093594b653ddcebdfb06b
ms.sourcegitcommit: 829d951d5c90442a38012daaf77e86046018e5b9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/09/2020
ms.locfileid: "89008876"
---
# <a name="configure-customer-managed-keys-for-your-azure-batch-account-with-azure-key-vault-and-managed-identity"></a>Door de klant beheerde sleutels voor uw Azure Batch account configureren met Azure Key Vault en beheerde identiteit

Standaard Azure Batch gebruikt door het platform beheerde sleutels voor het versleutelen van alle klant gegevens die zijn opgeslagen in de Azure Batch-service, zoals certificaten, taak-en taak gegevens. U kunt desgewenst uw eigen sleutels gebruiken, dat wil zeggen door de klant beheerde sleutels, om gegevens te versleutelen die zijn opgeslagen in Azure Batch.

De sleutels die u opgeeft, moeten worden gegenereerd in [Azure Key Vault](../key-vault/general/basic-concepts.md)en de batch-accounts die u wilt configureren met door de klant beheerde sleutels moeten worden ingeschakeld met [Azure Managed Identity](../active-directory/managed-identities-azure-resources/overview.md).

> [!IMPORTANT]
> Ondersteuning voor door de klant beheerde sleutels in Azure Batch is momenteel beschikbaar als open bare Preview voor de Europa-west, Europa-noord, Zwitserland-noord, VS-centraal, Zuid-Centraal VS, West-Centraal VS, VS-Oost, VS-Oost 2, VS-West 2, US Gov-Virginia en US Gov-Arizona regio's.
> Deze preview-versie wordt aangeboden zonder service level agreement en wordt niet aanbevolen voor productieworkloads. Misschien worden bepaalde functies niet ondersteund of zijn de mogelijkheden ervan beperkt.
> Zie [Supplemental Terms of Use for Microsoft Azure Previews (Aanvullende gebruiksvoorwaarden voor Microsoft Azure-previews)](https://azure.microsoft.com/support/legal/preview-supplemental-terms/) voor meer informatie.

## <a name="create-a-batch-account-with-system-assigned-managed-identity"></a>Een batch-account maken met door het systeem toegewezen beheerde identiteit

### <a name="azure-portal"></a>Azure Portal

In de [Azure Portal](https://portal.azure.com/), wanneer u batch-accounts maakt, kiest u **systeem toegewezen** in het identiteits type onder het tabblad **Geavanceerd** .

![Een nieuw batch-account met een door het systeem toegewezen identiteits type](./media/batch-customer-managed-key/create-batch-account.png)

Nadat het account is gemaakt, kunt u een unieke GUID vinden in het veld **id-Principal-id** onder de sectie **eigenschap** . Het **identiteits type** wordt weer gegeven `SystemAssigned` .

![Unieke GUID in het veld id-Principal-id](./media/batch-customer-managed-key/linked-batch-principal.png)
 
### <a name="azure-cli"></a>Azure CLI

Wanneer u een nieuw batch-account maakt, moet u `SystemAssigned` voor de `--identity` para meter opgeven.

```powershell
resourceGroupName='myResourceGroup'
accountName='mybatchaccount'

az batch account create \
    -n $accountName \
    -g $resourceGroupName \
    --locations regionName='West US 2' \
    --identity 'SystemAssigned'
```

Nadat het account is gemaakt, kunt u controleren of de door het systeem toegewezen beheerde identiteit is ingeschakeld voor dit account. Noteer de `PrincipalId` , aangezien deze waarde nodig is om dit batch-account toegang te verlenen tot de Key Vault.

```powershell
az batch account show \
    -n $accountName \
    -g $resourceGroupName \
    --query identity
```

> [!NOTE]
> De door het systeem toegewezen beheerde identiteit die is gemaakt in een batch-account wordt alleen gebruikt voor het ophalen van door de klant beheerde sleutels van de Key Vault. Deze identiteit is niet beschikbaar in batch-Pools.

## <a name="configure-your-azure-key-vault-instance"></a>Uw Azure Key Vault-exemplaar configureren

### <a name="create-an-azure-key-vault"></a>Een Azure Key Vault maken

Wanneer u een Azure Key Vault-exemplaar met door de klant beheerde sleutels voor Azure Batch maakt, moet u ervoor zorgen dat de beveiliging van de functie voor **voorlopig verwijderen** en **leegmaken** is ingeschakeld.

![Key Vault scherm maken](./media/batch-customer-managed-key/create-key-vault.png)

### <a name="add-an-access-policy-to-your-azure-key-vault-instance"></a>Een toegangs beleid toevoegen aan uw Azure Key Vault-exemplaar

Voeg in de Azure Portal, nadat de Key Vault is gemaakt, in het **toegangs beleid** onder **instelling**, het batch-account toegang toe met behulp van beheerde identiteit. Selecteer bij **sleutel machtigingen** **Get**, **Inpakken** en de **toets inpakken**. 

![Toegangs beleid toevoegen](./media/batch-customer-managed-key/key-permissions.png)

Vul in het veld **selecteren** onder **Principal**de in `principalId` die u eerder hebt opgehaald, of de naam van het batch-account.

![PrincipalId invoeren](./media/batch-customer-managed-key/principal-id.png)

### <a name="generate-a-key-in-azure-key-vault"></a>Een sleutel in Azure Key Vault genereren

In de Azure Portal gaat u naar de Key Vault instantie in de sectie **sleutel** en selecteert u **genereren/importeren**. Selecteer het **sleutel type** en de `RSA` **RSA-sleutel grootte** moet ten minste `2048` bits zijn. `EC` sleutel typen worden momenteel niet ondersteund als een door de klant beheerde sleutel voor een batch-account.

![Een sleutel maken](./media/batch-customer-managed-key/create-key.png)

Nadat de sleutel is gemaakt, klikt u op de zojuist gemaakte sleutel en de huidige versie en kopieert u de **sleutel-id** onder **Eigenschappen** sectie.  Zorg ervoor dat onder **toegestane bewerkingen**, **Terugloop sleutel** en de **sleutel voor uitpakken** beide zijn ingeschakeld.

## <a name="enable-customer-managed-keys-on-azure-batch-account"></a>Door de klant beheerde sleutels op Azure Batch account inschakelen

### <a name="azure-portal"></a>Azure Portal

Ga in het [Azure Portal](https://portal.azure.com/)naar de pagina batch-account. Schakel onder de sectie **versleuteling** de door de **klant beheerde sleutel**in. U kunt de sleutel-id rechtstreeks gebruiken, of u kunt de sleutel kluis selecteren en vervolgens op **een sleutel kluis en sleutel selecteren**klikken.

![Schakel onder versleuteling de door de klant beheerde sleutel in](./media/batch-customer-managed-key/encryption-page.png)

### <a name="azure-cli"></a>Azure CLI

Nadat het batch-account is gemaakt met een door het systeem toegewezen beheerde identiteit en de toegang tot Key Vault is verleend, werkt u het batch-account bij met de `{Key Identifier}` URL onder `keyVaultProperties` para meter. Stel ook **encryption_key_source** in als `Microsoft.KeyVault` .

```powershell
az batch account set \
    -n $accountName \
    -g $resourceGroupName \
    --encryption_key_source Microsoft.KeyVault \
    --encryption_key_identifier {YourKeyIdentifier} 
```

## <a name="update-the-customer-managed-key-version"></a>De door de klant beheerde sleutel versie bijwerken

Wanneer u een nieuwe versie van een sleutel maakt, werkt u het batch-account bij voor het gebruik van de nieuwe versie. Volg deze stappen:

1. Navigeer naar uw batch-account in Azure Portal en geef de versleutelings instellingen weer.
2. Voer de URI in voor de nieuwe sleutel versie. U kunt ook de sleutel kluis en de sleutel opnieuw selecteren om de versie bij te werken.
3. Sla uw wijzigingen op.

U kunt ook Azure CLI gebruiken om de versie bij te werken.

```powershell
az batch account set \
    -n $accountName \
    -g $resourceGroupName \
    --encryption_key_identifier {YourKeyIdentifierWithNewVersion} 
```
## <a name="use-a-different-key-for-batch-encryption"></a>Een andere sleutel gebruiken voor batch versleuteling

Voer de volgende stappen uit om de sleutel te wijzigen die wordt gebruikt voor batch versleuteling:

1. Navigeer naar uw batch-account en geef de versleutelings instellingen weer.
2. Voer de URI in voor de nieuwe sleutel. U kunt ook de sleutel kluis selecteren en een nieuwe sleutel kiezen.
3. Sla uw wijzigingen op.

U kunt ook Azure CLI gebruiken voor het gebruik van een andere sleutel.

```powershell
az batch account set \
    -n $accountName \
    -g $resourceGroupName \
    --encryption_key_identifier {YourNewKeyIdentifier} 
```
## <a name="frequently-asked-questions"></a>Veelgestelde vragen
  * **Worden door de klant beheerde sleutels ondersteund voor bestaande batch-accounts?** Nee. Door de klant beheerde sleutels worden alleen ondersteund voor nieuwe batch-accounts.
  * **Kan ik RSA-sleutel grootten selecteren die groter zijn dan 2048 bits?** Ja, RSA-sleutel groottes `3072` en `4096` bits worden ook ondersteund.
  * **Welke bewerkingen zijn beschikbaar nadat een door de klant beheerde sleutel is ingetrokken?** De enige bewerking die is toegestaan, is het verwijderen van een account als batch de toegang tot de door de klant beheerde sleutel verliest.
  * **Hoe kan ik de toegang tot mijn batch-account herstellen als ik de Key Vault sleutel per ongeluk verwijder?** Aangezien het opschonen van de beveiliging en het voorlopig verwijderen zijn ingeschakeld, kunt u de bestaande sleutels herstellen. Zie [een Azure Key Vault herstellen](../key-vault/general/soft-delete-cli.md#recovering-a-key-vault)voor meer informatie.
  * **Kan ik door de klant beheerde sleutels uitschakelen?** U kunt het versleutelings type van het batch-account op elk gewenst moment weer instellen op ' micro soft Managed key '. Daarna kunt u de sleutel verwijderen of wijzigen.
  * **Hoe kan ik mijn sleutels draaien?** Door de klant beheerde sleutels worden niet automatisch gedraaid. Als u de sleutel wilt draaien, werkt u de sleutel-id bij waaraan het account is gekoppeld.
  * **Hoe lang duurt het voordat de toegang tot het batch-account is hersteld?** Het kan tot tien minuten duren voordat het account weer toegankelijk is nadat de toegang is hersteld.
  * **Wat gebeurt er met mijn resources terwijl het batch-account niet beschikbaar is?** Alle groepen die worden uitgevoerd wanneer batch toegang tot door de klant beheerde sleutels verloren gaat, blijven actief. De knoop punten gaan echter over naar een niet-beschik bare status en taken worden niet meer uitgevoerd (en worden opnieuw in de wachtrij gezet). Zodra de toegang is hersteld, worden knoop punten weer beschikbaar en worden de taken opnieuw gestart.
  * **Is dit versleutelings mechanisme van toepassing op VM-schijven in een batch-pool?** Nee. Voor Cloud service-configuratie groepen wordt er geen versleuteling toegepast voor het besturings systeem en de tijdelijke schijf. Voor virtuele-machine configuratie groepen worden het besturings systeem en de opgegeven gegevens schijven standaard versleuteld met een door micro soft platform beheerde sleutel. Op dit moment kunt u niet uw eigen sleutel opgeven voor deze schijven. Als u de tijdelijke schijf van Vm's voor een batch-pool wilt versleutelen met een door micro soft platform beheerde sleutel, moet u de eigenschap [diskEncryptionConfiguration](/rest/api/batchservice/pool/add#diskencryptionconfiguration) in de configuratie groep van de [virtuele machine](/rest/api/batchservice/pool/add#virtualmachineconfiguration) inschakelen. Voor zeer gevoelige omgevingen wordt u aangeraden tijdelijke schijf versleuteling in te scha kelen en te voor komen dat gevoelige gegevens worden opgeslagen op het besturings systeem en gegevens schijven. Zie [een groep maken met schijf versleuteling is ingeschakeld](./disk-encryption.md) voor meer informatie.
  * **Is de door het systeem toegewezen beheerde identiteit voor het batch-account dat beschikbaar is op de reken knooppunten?** Nee. Deze beheerde identiteit wordt momenteel alleen gebruikt voor toegang tot de Azure Key Vault voor de door de klant beheerde sleutel.
  
