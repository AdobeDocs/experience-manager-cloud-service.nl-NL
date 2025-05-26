---
title: Door de klant beheerde toetsen voor AEM as a Cloud Service
description: Meer informatie over het beheren van coderingssleutels voor AEM as a Cloud Service
feature: Security
role: Admin
hide: true
hidefromtoc: true
exl-id: 100ddbf2-9c63-406f-a78d-22862501a085
source-git-commit: eb38369ee918851a9f792af811bafff9b2e49a53
workflow-type: tm+mt
source-wordcount: '1167'
ht-degree: 0%

---

# Setup van door klanten beheerde sleutels voor AEM as a Cloud Service {#cusomer-managed-keys-for-aem-as-a-cloud-service}

AEM as a Cloud Service slaat de klantgegevens momenteel op in Azure Blob Storage en MongoDB, waarbij standaard door de leverancier beheerde coderingssleutels worden gebruikt om gegevens te beveiligen. Terwijl deze opstelling aan de veiligheidsbehoeften van vele organisaties voldoet, kunnen de ondernemingen in gereglementeerde industrieën of die die verbeterde gegevensveiligheid vereisen grotere controle over hun encryptiepraktijken zoeken. Voor organisaties die prioriteit geven aan gegevensbeveiliging, compatibiliteit en de mogelijkheid om hun coderingssleutels te beheren, biedt de CMK-oplossing (Customer Managed Keys) een essentiële verbetering.

## Het probleem dat wordt opgelost {#the-problem-being-solved}

Door de provider beheerde sleutels kunnen zorgen veroorzaken voor bedrijven die extra privacy en integriteit nodig hebben. Zonder controle over zeer belangrijk beheer, staan de organisaties voor uitdagingen in het voldoen aan nalevingsvereisten, het uitvoeren van het beleid van de douaneveiligheid, en het verzekeren van volledige gegevensveiligheid.

De introductie van Customer Managed Keys (CMK) lost deze problemen op door AEM-klanten volledige controle te geven over hun coderingssleutels. Door verificatie via de Microsoft Entra ID (voorheen Azure Active Directory) maakt AEM CS veilig verbinding met de Azure Key Vault van de klant, zodat deze de levenscyclus van de coderingssleutels kan beheren, waaronder het maken, roteren en intrekken van sleutels.

CMK biedt verschillende voordelen:

* **Gegevens van de Controle en de Encryptie van de Toepassing:** verhoog veiligheid met direct beheer van uw toepassing van AEM en gegevens cryptografische sleutels.
* **verhoogt Vertrouwelijkheid en Integriteit:** Verminder de waarschijnlijkheid van onopzettelijke toegang en onthulling van gevoelige of merkgebonden gegevens met volledig encryptiebeheer.
* **Azure Key Vault Support:** Met het gebruik van Azure Key Vault kunt u belangrijke opslag, bewerkingen met betrekking tot geheimen verwerken en belangrijke rotaties uitvoeren.

Door CMK aan te nemen, kunnen klanten de controle over hun gegevensbeveiliging en encryptiepraktijken verhogen, de veiligheid verbeteren en risico&#39;s verlichten, terwijl zij van de scalability en de flexibiliteit van AEM CS blijven genieten.

Met AEM as a Cloud Service kunt u uw eigen coderingssleutels gebruiken om gegevens in rust te coderen. Deze handleiding bevat stappen voor het instellen van een door de klant beheerde sleutel (CMK) in Azure Key Vault voor AEM as a Cloud Service.

>[!WARNING]
>
>Nadat u CMK hebt ingesteld, kunt u niet terugkeren naar de toetsen die door het systeem worden beheerd. U bent verantwoordelijk voor het veilig beheren van uw sleutels en het bieden van toegang tot uw Key Vault-, Key- en CMK-app in Azure om te voorkomen dat de toegang tot uw gegevens verloren gaat.

U zult ook door de volgende stappen voor het creëren van en het vormen van de vereiste infrastructuur worden geleid:

1. Uw omgeving instellen
1. Een toepassings-id verkrijgen van Adobe
1. Een nieuwe bronnengroep maken
1. Een sleutelhanger maken
1. Adobe toegang verlenen tot de sleutelkault
1. Een coderingssleutel maken

U moet de URL van de sleutelkluis, de naam van de coderingssleutel en informatie over de sleutelvault delen met Adobe.

## Uw omgeving instellen {#setup-your-environment}

De Azure Command Line Interface (CLI) is de enige vereiste voor deze gids. Als u niet reeds geïnstalleerde Azure CLI hebt, volg hier de officiële installatieinstructies [ ](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli).

Meld uw CLI aan met `az login` voordat u verder gaat met de rest van deze handleiding.

>[!NOTE]
>
>Terwijl deze gids Azure CLI gebruikt, is het mogelijk om de zelfde verrichtingen via de Azure console uit te voeren. Als u liever de Azure-console gebruikt, gebruikt u de onderstaande opdrachten als referentie.

## Een toepassings-id verkrijgen van Adobe {#obtain-an-application-id-from-adobe}

Adobe geeft u een Entra-toepassings-id die u in de rest van deze handleiding nodig hebt. Als u nog geen toepassings-id hebt, neemt u contact op met Adobe om een id te verkrijgen.

## Een nieuwe bronnengroep maken {#create-a-new-resource-group}

Creeer een nieuwe middelgroep in een plaats van uw keus.

```powershell
# Choose a location and a name for the resource group.
$location="<AZURE LOCATION>"
$resourceGroup="<RESOURCE GROUP>"

# Create the resource group.
az group create --location $location --resource-group $resourceGroup
```

Als u al een middelgroep hebt, voel vrij om het in plaats daarvan te gebruiken. In de rest van deze handleiding worden de locatie van de resourcegroep en de naam ervan aangeduid met respectievelijk `$location` en `$resourceGroup` .

## Een belangrijke vault maken {#create-a-key-vault}

U moet een sleutelkluis maken voor de coderingssleutel. De sleutelvault moet ontruimingsbescherming hebben toegelaten. De zuiveringsbescherming is noodzakelijk voor het coderen van gegevens in rust van andere Azure diensten. Openbare netwerktoegang moet ook worden toegelaten, om ervoor te zorgen dat de huurder van Adobe tot de belangrijkste kluis kan toegang hebben.

>[!IMPORTANT]
>Het maken van de Key Vault met Public Network Access is uitgeschakeld. Hiermee wordt afgedwongen dat alle belangrijke vaultbewerkingen, zoals het maken van sleutels of het roteren, moeten worden uitgevoerd vanuit een omgeving die toegang heeft tot het netwerk van KeyVault, bijvoorbeeld een VM die toegang heeft tot de KeyVault.

```powershell
# Reuse this information from the previous step.
$location="<AZURE LOCATION>"
$resourceGroup="<RESOURCE GROUP>"

# Choose a name for the key vault.
$keyVaultName="<KEY VAULT NAME>"

# Create the key vault.
az keyvault create `
  --location $location `
  --resource-group $resourceGroup `
  --name $keyVaultName `
  --default-action=Deny `
  --enable-purge-protection `
  --enable-rbac-authorization `
  --public-network-access Enabled
```

## Adobe Access verlenen voor de Key Vault {#grant-adobe-access-to-the-key-vault}

In deze stap geeft u Adobe via een Entra-toepassing toegang tot de keyvault. De id van de Entra-toepassing had al door Adobe moeten worden verstrekt.

Eerst, moet u een de diensthoofd tot stand brengen in bijlage aan de Entra toepassing en aan het toewijzen de **Zeer belangrijke Uitvault Reader** en **Zeer belangrijke Server van Crypto Gebruiker** rollen. De rollen zijn beperkt tot de sleutelkluis die in deze gids wordt gecreeerd.

```powershell
# Reuse this information from the previous steps.
$resourceGroup="<RESOURCE GROUP>"
$keyVaultName="<KEY VAULT NAME>"

# The application ID is provided by Adobe.
$appId="<APPLICATION ID>"

# Retrieve the ID of the key vault.
$keyVaultId=(az keyvault show --resource-group $resourceGroup --name $keyVaultName --query id --output tsv)

# Create a new service principal.
$servicePrincipalId=(az ad sp create --id $appId --query id --out tsv)

# Assign the roles to the service principal.
az role assignment create --assignee $servicePrincipalId --role "Key Vault Reader" --scope $keyVaultId
az role assignment create --assignee $servicePrincipalId --role "Key Vault Crypto User" --scope $keyVaultId
```

## Een coderingssleutel maken {#create-an-ecryption-key}

Tot slot kunt u een encryptiesleutel in uw zeer belangrijke vault tot stand brengen. Gelieve te merken op dat u de **Zeer belangrijke rol van de Medewerker van Crypto** zult nodig hebben om deze stap te voltooien. Als de het programma geopende gebruiker deze rol niet heeft, contacteer uw systeembeheerder om deze rol te hebben die aan u wordt verleend of vraag iemand die reeds die rol heeft om deze stap voor u te voltooien.

Netwerktoegang tot de sleutelkluis is is vereist om de coderingssleutel te maken. Controleer eerst of u toegang hebt tot de sleutelvault en ga verder met het maken van de sleutel:

```powershell
# Reuse this information from the previous steps.
$keyVaultName="<KEY VAULT NAME>"

# Chose a name for your key.
$keyName="<KEY NAME>"

# Create the key.
az keyvault key create --vault-name $keyVaultName --name $keyName
```

## De belangrijkste vaultgegevens delen {#share-the-key-vault-information}

U bent nu allemaal ingesteld. U hoeft slechts enkele vereiste informatie te delen met Adobe, die ervoor zal zorgen dat uw omgeving voor u wordt geconfigureerd.

```powershell
# Reuse this information from the previous steps.
$resourceGroup="<RESOURCE GROUP>"
$keyVaultName="<KEY VAULT NAME>"

# Retrieve the URL of your key vault.
$keyVaultUri=(az keyvault show --name $keyVaultName `
    --resource-group $resourceGroup `
    --query properties.vaultUri `
    --output tsv)

# In addition we would need the tenantId and the subscriptionId in order to setup the connection.
$tenantId=(az keyvault show --name $keyVaultName `
    --resource-group $resourceGroup `
    --query properties.tenantId `
    --output tsv)
$subscriptionId="<Subscription ID>"
```


## Implicaties van het Herhalen van Zeer belangrijke Toegang {#implications-of-revoking-key-access}

Het intrekken of uitschakelen van de toegang tot de Key Vault-, Key- of CMK-toepassing kan leiden tot aanzienlijke onderbrekingen, zoals het doorbreken van wijzigingen in de activiteiten van uw platform. Zodra deze sleutels worden onbruikbaar gemaakt, kunnen de gegevens in Platform ontoegankelijk worden, en om het even welke stroomafwaartse verrichtingen die op deze gegevens baseren zullen ophouden te functioneren. Het is van cruciaal belang dat u de downstreameffecten volledig begrijpt voordat u wijzigingen aanbrengt in uw sleutelconfiguraties.

Als u besluit om de toegang van het Platform tot uw gegevens in te trekken, kunt u dit doen door de gebruikersrol verbonden aan de toepassing uit Key Vault binnen Azure te verwijderen.

## Volgende stappen {#next-steps}

Contact opnemen met Adobe en delen:

* De URL van de sleutelkluis. U hebt deze in deze stap opgehaald en opgeslagen in de variabele `$keyVaultUri` .
* De naam van de coderingssleutel. U hebt de sleutel in een vorige stap gemaakt en in de variabele `$keyName` opgeslagen.
* De `$resourceGroup` , `$subscriptionId` en `$tenantId` die vereist zijn om de verbinding met de sleutelvault in te stellen.

<!-- Alexandru: hiding this for now

### Private Link Approvals {#private-link-approvals}

>[!TIP]
>You can also consult the [Azure Documentation](https://learn.microsoft.com/en-us/azure/key-vault/general/private-link-service?tabs=portal#how-to-manage-a-private-endpoint-connection-to-key-vault-using-the-azure-portal) on how to approve a Private Endpoint Connection.

Afterwards, an Adobe Engineer assigned to you will contact you to confirm the creation of the private endpoints, and will request you to approve a set of required Connection Requests. The requests can be approved either using the Azure Portal UI, where you can go to **KeyVault > Settings > Networking > Private Endpoint Connections** and approve the requests with names similar to these: 

`mongodb-atlas-<REGION>-<NUMBER>`, `storage-account-private-endpoint` and `backup-storage-account-private-endpoint`. 

Notify the Adobe Engineer once this process is complete and the Private Endpoints show up as **Approved**. -->

## Door klanten beheerde toetsen in Private Beta {#customer-managed-keys-in-private-beta}

Het Engineering-team van Adobe werkt momenteel aan een verbeterde implementatie van CMK met gebruikmaking van Azure&#39;s Private Link. Met de nieuwe implementatie kunt u uw sleutel delen via de Azure-backbone dankzij een directe Private Link-verbinding tussen de Adobe-gebruiker en uw Key Vault.

Deze verbeterde implementatie is momenteel in Private Beta en kan worden ingeschakeld voor geselecteerde klanten die zich aansluiten bij het Private Beta-programma en nauw samenwerken met Adobe Engineering. Neem voor meer informatie contact op met Adobe als u interesse hebt in de Private Beta for CMK via Private Link.
