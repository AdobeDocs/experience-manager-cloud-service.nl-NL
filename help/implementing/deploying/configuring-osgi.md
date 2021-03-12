---
title: OSGi configureren voor AEM as a Cloud Service
description: 'OSGi-configuratie met geheime waarden en milieu-specifieke waarden '
translation-type: tm+mt
source-git-commit: a04935b3b71cff9f5f0fbc85b4d3db4dd96a28fc
workflow-type: tm+mt
source-wordcount: '2737'
ht-degree: 1%

---


# OSGi configureren voor AEM as a Cloud Service {#configuring-osgi-for-aem-as-a-cloud-service}

[](https://www.osgi.org/) OSGiis een fundamenteel element in de technologiestapel van Adobe Experience Manager (AEM). Het wordt gebruikt om de samengestelde bundels van AEM en zijn configuraties te controleren.

OSGi verstrekt de gestandaardiseerde primitieven die toepassingen toestaan om van kleine, herbruikbare en samenwerkende componenten worden gebouwd. Deze componenten kunnen in een toepassing worden samengesteld en worden opgesteld. Dit staat gemakkelijk beheer van bundels OSGi toe aangezien zij kunnen worden tegengehouden, geïnstalleerd, individueel begonnen. De onderlinge afhankelijkheden worden automatisch verwerkt. Elke component OSGi is bevat in één van de diverse bundels. Voor meer informatie, zie [OSGi specificatie](https://www.osgi.org/Specifications/HomePage).

U kunt de configuratiemontages voor componenten OSGi door configuratiedossiers beheren die deel van een AEM codeproject uitmaken.

## OSGi-configuratiebestanden {#osgi-configuration-files}

De veranderingen van de configuratie worden bepaald in de codepakketten van het AEM Project (`ui.apps`) als configuratiedossiers (`.cfg.json`) onder runtime specifieke config omslagen:

`/apps/example/config.<runmode>`

De indeling van OSGi-configuratiebestanden is gebaseerd op JSON met de indeling `.cfg.json` die is gedefinieerd door het Apache Sling-project.

OSGi-configuraties richten OSGi-componenten via hun Persistent Identiteit (PID), die standaard de Java-klassenaam van de OSGi-component krijgt. Bijvoorbeeld, om configuratie OSGi voor een dienst te verstrekken OSGi die door wordt uitgevoerd:

`com.example.workflow.impl.ApprovalWorkflow.java`

een OSGi-configuratiebestand wordt gedefinieerd op:

`/apps/example/config/com.example.workflow.impl.ApprovalWorkflow.cfg.json`

volgend op de configuratie-indeling cfg.json OSGi.

>[!NOTE]
>
>Eerdere versies van AEM ondersteunde OSGi-configuratiebestanden die verschillende bestandsindelingen gebruiken, zoals .cfg., .config en als XML sling:OsgiConfig-brondefinities. Deze formaten worden vervangen door het cfg.json OSGi configuratieformaat.

## Resolutie van runmode {#runmode-resolution}

De specifieke configuraties OSGi kunnen aan specifieke AEM instanties worden gericht door runmodes te gebruiken. Om runmode te gebruiken, creeer config omslagen onder `/apps/example` (waar het voorbeeld uw projectnaam is), in het formaat:

`/apps/example/config.<author|publish>.<dev|stage|prod>/`

Om het even welke configuraties OSGi in dergelijke omslagen zullen worden gebruikt als de looppaswijzen die in de config omslagnaam worden bepaald aan de looppaswijzen aanpassen die door AEM worden gebruikt.

Als AEM bijvoorbeeld de auteur en dev van de runmodi gebruikt, worden configuratieknooppunten in `/apps/example/config.author/` en `/apps/example/config.author.dev/` toegepast, terwijl configuratieknooppunten in `/apps/example/config.publish/` en `/apps/example/config.author.stage/` niet worden toegepast.

Als meerdere configuraties voor dezelfde PID van toepassing zijn, wordt de configuratie met het hoogste aantal overeenkomende uitvoeringsmodi toegepast.

De granulariteit van deze regel staat op een PID-niveau. Dit betekent dat u bepaalde eigenschappen voor dezelfde PID niet kunt definiëren in `/apps/example/config.author/` en meer specifieke eigenschappen in `/apps/example/config.author.dev/` voor dezelfde PID.  De configuratie met het hoogste aantal passende looppaswijzen zal voor volledige PID efficiënt zijn.

Wanneer het ontwikkelen plaatselijk, kan een loopmode startparameter worden overgegaan om te dicteren welke loopmode configuratie OSGI zal worden gebruikt.

## Typen OSGi-configuratiewaarden {#types-of-osgi-configuration-values}

Er zijn drie soorten OSGi configuratiewaarden die met AEM als Cloud Service kunnen worden gebruikt.

1. **Inline waarden**, die waarden zijn die hard-gecodeerd in de configuratie OSGi zijn en in Git worden opgeslagen. Bijvoorbeeld:

   ```json
   {
      "connection.timeout": 1000
   }
   ```

1. **Geheime waarden**, die waarden zijn die niet in Git om veiligheidsredenen zouden moeten worden opgeslagen. Bijvoorbeeld:

   ```json
   {
   "api-key": "$[secret:server-api-key]"
   } 
   ```

1. **Milieu-specifieke waarden**, die waarden zijn die tussen de milieu&#39;s van de Ontwikkeling variëren, en kunnen daarom niet nauwkeurig door looppas worden gericht wijze (aangezien er één enkele  `dev` runmode in AEM als Cloud Service is). Bijvoorbeeld:

   ```json
   {
    "url": "$[env:server-url]"
   }
   ```

   Merk op dat één enkel OSGi- configuratiedossier om het even welke combinatie van deze types van configuratiewaarde samen kan gebruiken. Bijvoorbeeld:

   ```json
   {
   "connection.timeout": 1000,
   "api-key": "$[secret:server-api-key]",
   "url": "$[env:server-url]"
   }
   ```

## Hoe te om het aangewezen Type van Waarde van de Configuratie te kiezen OSGi {#how-to-choose-the-appropriate-osgi-configuration-value-type}

Het algemene geval voor OSGi gebruikt inline OSGi configuratiewaarden. Milieu-specifieke configuraties worden gebruikt slechts voor specifieke gebruiksgevallen waar een waarde tussen dev milieu&#39;s verschilt.

![](assets/choose-configuration-value-type_res1.png)

De milieu-specifieke configuraties breiden de traditionele, statisch-bepaalde configuraties OSGi uit die gealigneerde waarden bevatten, die de capaciteit verstrekken om de OSGi configuratiewaarden extern via de Manager API van de Wolk te beheren. Het is belangrijk om te begrijpen wanneer de gemeenschappelijke en traditionele benadering van het bepalen van gealigneerde waarden en het opslaan van hen in Git, zou moeten worden gebruikt, tegenover het abstraheren van de waarden in milieu-specifieke configuraties.

De volgende richtlijnen richten wanneer om niet geheime en geheime milieu-specifieke configuraties te gebruiken:

### Wanneer moet inline configuratiewaarden {#when-to-use-inline-configuration-values} worden gebruikt

Inline-configuratiewaarden worden als de standaardbenadering beschouwd en moeten waar mogelijk worden gebruikt. Inline configuraties bieden de voordelen van:

* Zij worden gehandhaafd, met bestuur en versiegeschiedenis in Git
* Waarden zijn impliciet gekoppeld aan code-implementaties
* Zij vereisen geen extra overwegingen van plaatsing of coördinatie

Wanneer het bepalen van een OSGi configuratiewaarde, begin met gealigneerde waarden, om het even welk slechts geheim of milieu-specifieke configuraties selecteren indien vereist voor het gebruiksgeval.

### Wanneer om niet-geheime milieu-specifieke configuratiewaarden {#when-to-use-non-secret-environment-specific-configuration-values} te gebruiken

Gebruik alleen omgevings-specifieke configuraties (`$[env:ENV_VAR_NAME]`) voor niet-geheime configuratiewaarden wanneer de waarden per ontwikkelomgeving verschillen. Dit omvat lokale ontwikkelingsinstanties en om het even welke AEM als milieu&#39;s van de Ontwikkeling van de Cloud Service. Gebruik geen niet-geheime omgevingspecifieke configuraties voor AEM als werkgebied of productieomgeving voor Cloud Servicen.

* Gebruik alleen niet-geheime omgevings-specifieke configuraties voor configuratiewaarden die verschillen tussen ontwikkelomgevingen, inclusief lokale ontwikkelingsinstanties.
* In plaats daarvan, gebruik de standaard gealigneerde waarden in de configuraties OSGi voor Stadium en Productie niet-geheime waarden.  In verband hiermee wordt het niet aanbevolen om omgevingspecifieke configuraties te gebruiken om het aanbrengen van configuratiewijzigingen tijdens runtime in werkgebied- en productieomgevingen te vergemakkelijken. deze wijzigingen moeten worden ingevoerd via het beheer van de broncode .

### Wanneer om geheime milieu-specifieke configuratiewaarden {#when-to-use-secret-environment-specific-configuration-values} te gebruiken

AEM als Cloud Service vereist het gebruik van milieu-specifieke configuraties (`$[secret:SECRET_VAR_NAME]`) voor om het even welke geheime OSGi configuratiewaarden, zoals wachtwoorden, privé API sleutels, of een andere waarden die niet in Git om veiligheidsredenen kunnen worden opgeslagen.

Gebruik geheime milieu-specifieke configuraties om de waarde voor geheimen op alle AEM als milieu&#39;s van de Cloud Service, met inbegrip van Stadium en Productie op te slaan.

<!-- ### Adding a New Configuration to the Repository {#adding-a-new-configuration-to-the-repository}

#### What You Need to Know {#what-you-need-to-know}

To add a new configuration to the repository you need to know the following:

1. The **Persistent Identity** (PID) of the service.

   Reference the **Configurations** field in the Web console. The name is shown in brackets after the bundle name (or in the **Configuration Information** towards the bottom of the page).

   For example, create a node `com.day.cq.wcm.core.impl.VersionManagerImpl.` to configure **AEM WCM Version Manager**.

   ![chlimage_1-141](assets/chlimage_1-141.png)

1. Whether a specific runmode is required. Create the folder:

    * `config` - for all run modes
    * `config.author` - for the author environment
    * `config.publish` - for the publish environment
    * `config.<run-mode>` - as appropriate

1. Whether a **Configuration** or **Factory Configuration** is necessary.
1. The individual parameters to be configured; including any existing parameter definitions that will need to be recreated.

   Reference the individual parameter field in the Web console. The name is shown in brackets for each parameter.

   For example, create a property
   `versionmanager.createVersionOnActivation` to configure **Create Version on Activation**.

   ![chlimage_1-142](assets/chlimage_1-142.png)

1. Does a configuration already exist in `/libs`? To list all configurations in your instance, use the **Query** tool in CRXDE Lite to submit the following SQL query:

   `select * from sling:OsgiConfig`

   If so, this configuration can be copied to ` /apps/<yourProject>/`, then customized in the new location. -->

## OSGi-configuraties maken {#creating-sogi-configurations}

Er zijn twee manieren om nieuwe configuraties tot stand te brengen OSGi, zoals hieronder beschreven. De eerste benadering wordt typisch gebruikt voor het vormen van componenten van douaneOSGi die bekende eigenschappen OSGi en waarden door de ontwikkelaar, en laatstgenoemde voor AEM-verstrekte componenten OSGi hebben.

### OSGi-configuraties {#writing-osgi-configurations} schrijven

De JSON geformatteerde OSGi configuratiedossiers kunnen door hand in het AEM project worden geschreven. Dit is vaak de snelste manier om configuraties OSGi voor bekende componenten te creëren OSGi, en vooral de componenten van douane OSGi die door de zelfde ontwikkelaar die de configuraties bepalen zijn ontworpen en ontwikkeld. Deze benadering kan ook worden gebruikt om configuraties voor de zelfde component te kopiëren/te kleven en bij te werken OSGi over diverse runmode omslagen.

1. In uw winde, open het `ui.apps` project, bepaal de plaats of creeer de config omslag (`/apps/.../config.<runmode>`) die de runmodes richt de nieuwe configuratie OSGi zou moeten effect hebben
1. In deze config omslag, creeer een nieuw `<PID>.cfg.json` dossier. PID is de Blijvende Identiteit van de component OSGi is gewoonlijk de volledige klassennaam van de OSGi componentimplementatie. Bijvoorbeeld:
   `/apps/.../config/com.example.workflow.impl.ApprovalWorkflow.cfg.json`
Merk op dat OSGi de namen van de de configuratiefabrieksdossiers, de  `<PID>-<factory-name>.cfg.json` noemende overeenkomst gebruiken
1. Open het nieuwe `.cfg.json` dossier, en bepaal de sleutel/waardecombinaties voor het bezit OSGi en waardeparen, na [JSON OSGi configuratieformaat](https://sling.apache.org/documentation/bundles/configuration-installer-factory.html#configuration-files-cfgjson-1).
1. Sla uw wijzigingen op in het nieuwe `.cfg.json`-bestand
1. Voeg en bewijs uw nieuw OSGi configuratiedossier aan Git toe

### OSGi-configuraties genereren met de AEM SDK QuickStart {#generating-osgi-configuratuions-using-the-aem-sdk-quickstart}

De AEM QuickStart Jar&#39;s AEM Web Console van SDK kan worden gebruikt vormt componenten OSGi, en de configuraties van export OSGi als JSON. Dit is nuttig om AEM-verstrekte componenten te vormen OSGi waarvan eigenschappen OSGi en hun waardeformaten niet goed kunnen worden begrepen door de ontwikkelaar die de configuraties OSGi in het AEM project bepaalt. Merk op dat het gebruiken van de Configuratie UI van de AEMConsole van het Web `.cfg.json` dossiers in de bewaarplaats schrijft, zodat bewust van dit om potentieel onverwacht gedrag tijdens lokale ontwikkeling te vermijden, wanneer de AEM project-bepaalde configuraties OSGi van de geproduceerde configuraties kunnen verschillen.

1. Meld u als beheerder aan bij de AEM webconsole van QuickStart Jar van de AEM SDK
1. Navigeer naar OSGi > Configuratie
1. Zoek de OSGi-component die u wilt configureren en tik op de titel die u wilt bewerken
   ![OSGi-configuratie](./assets/configuring-osgi/configuration.png)
1. Bewerk indien nodig de OSGi-waarden van het configuratiebezit via de webinterface
1. Registreer de Persistent Identiteit (PID) aan veilige plaats, zal dit later worden gebruikt om de configuratie OSGi JSON te produceren
1. Tik op Opslaan
1. Navigeer naar OSGi > OSGi Installer Configuration Printer
1. Plak in PID die in Stap 5 wordt gekopieerd, zorg ervoor de Formaat van de Rangschikking wordt geplaatst aan &quot;OSGi Configurator JSON&quot;
1. Tikken,
1. De configuratie OSGi in formaat JSON zal in de Serialized sectie van de Eigenschappen van de Configuratie tonen
   ![OSGi-installateursconfiguratieserver](./assets/configuring-osgi/osgi-installer-configurator-printer.png)
1. In uw winde, open het `ui.apps` project, bepaal de plaats of creeer de config omslag (`/apps/.../config.<runmode>`) die de runmodes richt de nieuwe configuratie OSGi zou moeten effect hebben.
1. In deze config omslag, creeer een nieuw `<PID>.cfg.json` dossier. De PID is dezelfde waarde uit stap 5.
1. Plak de Generialiseerde Eigenschappen van de Configuratie van Stap 10 in het `.cfg.json` dossier.
1. Sla uw wijzigingen op in het nieuwe `.cfg.json`-bestand.
1. Voeg en bewijs uw nieuw OSGi configuratiedossier aan Git toe.


## OSGi Indelingen van het Bezit van de Configuratie {#osgi-configuration-property-formats}

### Inline-waarden {#inline-values}

Zoals u zou kunnen verwachten, worden inline waarden geformatteerd als standaardnaam-waarde paren, volgens standaardJSON syntaxis. Bijvoorbeeld:

```json
{
   "my_var1": "val",
   "my_var2": [ "abc", "def" ],
   "my_var3": 500
}
```

### Omgevingsspecifieke configuratiewaarden {#environment-specific-configuration-values}

De configuratie OSGi zou placeholder voor de variabele moeten toewijzen die bestemd is om per milieu te worden bepaald:

```
use $[env:ENV_VAR_NAME]
```

Klanten dienen deze techniek alleen te gebruiken voor OSGI-configuratie-eigenschappen die gerelateerd zijn aan hun aangepaste code. het zou niet moeten worden gebruikt om Adobe-bepaalde configuratie te overschrijven OSGI.

### Geheime configuratiewaarden {#secret-configuration-values}

De configuratie OSGi zou placeholder voor het geheim moeten toewijzen dat bestemd is om per milieu te worden bepaald:

```
use $[secret:SECRET_VAR_NAME]
```

### Naam variabele {#variable-naming}

Het volgende is op zowel milieu-specifieke als geheime configuratiewaarden van toepassing.

De namen van variabelen moeten de volgende regels volgen:

* minimumlengte: 2
* maximumlengte: 100
* moet overeenkomen met regex: `[a-zA-Z_][a-zA-Z_0-9]*`

De waarden voor de variabelen mogen niet meer dan 2048 tekens bevatten.

### Standaardwaarden {#default-values}

Het volgende is op zowel milieu-specifieke als geheime configuratiewaarden van toepassing.

Als er geen waarde per omgeving is ingesteld, wordt de tijdelijke aanduiding tijdens runtime niet vervangen en op zijn plaats gelaten omdat er geen interpolatie heeft plaatsgevonden. Om dit te voorkomen, kan een standaardwaarde als deel van placeholder met de volgende syntaxis worden verstrekt:

```
$[env:ENV_VAR_NAME;default=<value>]
```

Als een standaardwaarde is opgegeven, wordt de tijdelijke aanduiding vervangen door de waarde voor de afzonderlijke omgeving, indien deze wordt opgegeven, of door de opgegeven standaardwaarde.

### Lokale ontwikkeling {#local-development}

Het volgende is op zowel milieu-specifieke als geheime configuratiewaarden van toepassing.

Variabelen kunnen in de lokale omgeving worden gedefinieerd, zodat ze tijdens runtime door de lokale AEM worden opgehaald. Bijvoorbeeld in Linux:

```bash
export ENV_VAR_NAME=my_value
```

Men adviseert dat een eenvoudig bash manuscript wordt geschreven dat de milieuvariabelen plaatst die in de configuraties worden gebruikt en het uitvoeren alvorens AEM te beginnen. Met gereedschappen zoals [https://direnv.net/](https://direnv.net/) kunt u deze aanpak vereenvoudigen. Afhankelijk van het type van de waarden, zouden zij in broncodebeheer kunnen worden gecontroleerd, als zij tussen iedereen kunnen worden gedeeld.

De waarden voor geheimen worden gelezen uit bestanden. Daarom moet voor elke plaatsaanduiding die een geheim gebruikt, een tekstbestand met de geheime waarde worden gemaakt.

Als bijvoorbeeld `$[secret:server_password]` wordt gebruikt, moet een tekstbestand met de naam **server_password** worden gemaakt. Al deze geheime dossiers moeten in de zelfde folder worden opgeslagen en het kaderbezit `org.apache.felix.configadmin.plugin.interpolation.secretsdir` moet met die lokale folder worden gevormd.

### Auteur versus publicatieconfiguratie {#author-vs-publish-configuration}

Als voor een OSGI-eigenschap andere waarden zijn vereist voor auteur in plaats van publicatie:

* Er moeten afzonderlijke `config.author`- en `config.publish` OSGi-mappen worden gebruikt, zoals beschreven in de sectie [Runmode Resolution](#runmode-resolution).
* er moeten onafhankelijke variabelenamen worden gebruikt . Het wordt aanbevolen een voorvoegsel te gebruiken, zoals `author_<variablename>` en `publish_<variablename>`, waarbij de namen van variabelen gelijk zijn

### Configuratievoorbeelden {#configuration-examples}

In de onderstaande voorbeelden wordt ervan uitgegaan dat er naast het werkgebied en de prod-omgevingen 3 ontwikkelomgevingen zijn.

**Voorbeeld 1**

De bedoeling is dat de waarde van de eigenschap OSGI `my_var1` hetzelfde is voor het werkgebied en de prod, maar verschilt voor elk van de 3 dev-omgevingen.

<table>
<tr>
<td>
<b>Map</b>
</td>
<td>
<b>Inhoud van myfile.cfg.json</b>
</td>
</tr>
<tr>
<td>
config
</td>
<td>
<pre>
{ 
 "my_var1": "val",
 "my_var2": "abc",
 "my_var3": 500
}
</pre>
</td>
</tr>
<tr>
<td>
config.dev
</td>
<td>
<pre>
{ 
 "my_var1" : "$[env:my_var1]"
 "my_var2": "abc",
 "my_var3": 500
}
</pre>
</td>
</tr>
</table>

**Voorbeeld 2**

De bedoeling is dat de waarde van de eigenschap OSGI `my_var1` verschilt voor het werkgebied, de prod en voor elk van de 3 dev-omgevingen. De API voor Cloud Manager moet dus worden aangeroepen om de waarde in te stellen voor `my_var1` voor elk dev-element.

<table>
<tr>
<td>
<b>Map</b>
</td>
<td>
<b>Inhoud van myfile.cfg.json</b>
</td>
</tr>
<tr>
<td>
config.stage
</td>
<td>
<pre>
{ 
 "my_var1": "val1",
 "my_var2": "abc",
 "my_var3": 500
}
</pre>
</td>
</tr>
<tr>
<td>
config.prod
</td>
<td>
<pre>
{ 
 "my_var1": "val2",
 "my_var2": "abc",
 "my_var3": 500
}
</pre>
</td>
</tr>
<tr>
<td>
config.dev
</td>
<td>
<pre>
{ 
 "my_var1" : "$[env:my_var1]"
 "my_var2": "abc",
 "my_var3": 500
}
</pre>
</td>
</tr>
</table>

**Voorbeeld 3**

De bedoeling is dat de waarde van de eigenschap OSGi `my_var1` gelijk is voor werkgebied, productie en slechts één van de ontwikkelomgevingen, maar dat deze verschilt voor de andere twee ontwikkelomgevingen. In dit geval moet de API voor cloudbeheer worden aangeroepen om de waarde van `my_var1` in te stellen voor elke ontwikkelomgeving, inclusief voor de ontwikkelomgeving die dezelfde waarde moet hebben als het werkgebied en de productie. Het zal niet de waarde erven die in de omslag **config** wordt geplaatst.

<table>
<tr>
<td>
<b>Map</b>
</td>
<td>
<b>Inhoud van myfile.cfg.json</b>
</td>
</tr>
<tr>
<td>
config
</td>
<td>
<pre>
{ 
 "my_var1": "val1",
 "my_var2": "abc",
 "my_var3": 500
}
</pre>
</td>
</tr>
<tr>
<td>
config.dev
</td>
<td>
<pre>
{ 
 "my_var1" : "$[env:my_var1]"
 "my_var2": "abc",
 "my_var3": 500
}
</pre>
</td>
</tr>
</table>

Een andere manier om dit te verwezenlijken zou een standaardwaarde voor het vervangingsteken in de config.dev omslag moeten plaatsen dusdanig dat het de zelfde waarde zoals in **config** omslag is.

<table>
<tr>
<td>
<b>Map</b>
</td>
<td>
<b>Inhoud van myfile.cfg.json</b>
</td>
</tr>
<tr>
<td>
config
</td>
<td>
<pre>
{ 
 "my_var1": "val1",
 "my_var2": "abc",
 "my_var3": 500
}
</pre>
</td>
</tr>
<tr>
<td>
config.dev
</td>
<td>
<pre>
{ 
 "my_var1": "$[env:my_var1;default=val1]"
 "my_var2": "abc",
 "my_var3": 500
}
</pre>
</td>
</tr>
</table>

## Cloud Manager API-indeling voor het instellen van eigenschappen {#cloud-manager-api-format-for-setting-properties}

Zie [deze pagina](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html#!AdobeDocs/cloudmanager-api-docs/master/create-api-integration.md) over hoe API moet worden gevormd.
>[!NOTE]
>
>Zorg ervoor dat de gebruikte API voor Cloud Manager de rol &quot;Deployment Manager - Cloud Service&quot; heeft toegewezen. Andere rollen kunnen niet alle onderstaande opdrachten uitvoeren.

### Waarden instellen via API {#setting-values-via-api}

Het roepen van API zal de nieuwe variabelen en de waarden aan een milieu van de Wolk opstellen, gelijkend op een typische pijpleiding van de de plaatsing van de klantencode. De auteur- en publicatieservices worden opnieuw gestart en er wordt een verwijzing naar de nieuwe waarden opgenomen. Dit duurt meestal een paar minuten.

```
PATCH /program/{programId}/environment/{environmentId}/variables
```

```
]
        {
                "name" : "MY_VAR1",
                "value" : "plaintext value",
                "type" : "string"  <---default
        },
        {
                "name" : "MY_VAR2",
                "value" : "<secret value>",
                "type" : "secretString"
        }
]
```

Merk op dat standaardvariabelen niet via API, maar eerder in het bezit OSGi zelf worden geplaatst.

Zie [deze pagina](https://www.adobe.io/apis/experiencecloud/cloud-manager/api-reference.html#/Environment_Variables/patchEnvironmentVariables) voor meer informatie.

### Waarden ophalen via API {#getting-values-via-api}

```
GET /program/{programId}/environment/{environmentId}/variables
```

Zie [deze pagina](https://www.adobe.io/apis/experiencecloud/cloud-manager/api-reference.html#/Environment_Variables/getEnvironmentVariables) voor meer informatie.

### Waarden verwijderen via API {#deleting-values-via-api}

```
PATCH /program/{programId}/environment/{environmentId}/variables
```

Als u een variabele wilt verwijderen, neemt u deze op met een lege waarde.

Zie [deze pagina](https://www.adobe.io/apis/experiencecloud/cloud-manager/api-reference.html#/Environment_Variables/patchEnvironmentVariables) voor meer informatie.

### Waarden ophalen via de opdrachtregel {#getting-values-via-cli}

```bash
$ aio cloudmanager:list-environment-variables ENVIRONMENT_ID
Name     Type         Value
MY_VAR1  string       plaintext value 
MY_VAR2  secretString ****
```


### Waarden instellen via de opdrachtregel {#setting-values-via-cli}

```bash
$ aio cloudmanager:set-environment-variables ENVIRONMENT_ID --variable MY_VAR1 "plaintext value" --secret MY_VAR2 "some secret value"
```

### Waarden verwijderen via de opdrachtregel {#deleting-values-via-cli}

```bash
$ aio cloudmanager:set-environment-variables ENVIRONMENT_ID --delete MY_VAR1 MY_VAR2
```

>[!NOTE]
>
>Zie [deze pagina](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid) voor meer informatie over hoe u waarden kunt configureren met de plug-in Cloud Manager voor Adobe I/O CLI.

### Aantal variabelen {#number-of-variables}

Er kunnen maximaal 200 variabelen per omgeving worden gedeclareerd.

## Overwegingen bij de implementatie voor geheime en omgevingsspecifieke configuratiewaarden {#deployment-considerations-for-secret-and-environment-specific-configuration-values}

Omdat de geheime en milieu specifieke configuratiewaarden buiten Git leven, en daarom geen deel van de formele AEM als mechanismen van de plaatsing van de Cloud Service uitmaken, zou de klant moeten leiden, besturen en in de AEM als proces van de Cloud Service plaatsing integreren.

Zoals hierboven vermeld, zal het roepen van API de nieuwe variabelen en de waarden aan de milieu&#39;s van de Wolk, gelijkend op een typische pijpleiding van de de plaatsing van de klantencode opstellen. De auteur- en publicatieservices worden opnieuw gestart en er wordt een verwijzing naar de nieuwe waarden opgenomen. Dit duurt meestal een paar minuten. Merk op dat de kwaliteitspoorten en tests die tijdens een normale implementatie van code door Cloud Manager worden uitgevoerd, niet tijdens dit proces worden uitgevoerd.

Klanten bellen de API doorgaans om omgevingsvariabelen in te stellen voordat ze code implementeren die op hen is gebaseerd in Cloud Manager. In sommige situaties, zou men een bestaande variabele kunnen willen wijzigen nadat de code reeds is opgesteld.

Merk op dat API niet kan slagen wanneer een pijpleiding in gebruik is, of een AEM update of klantenplaatsing, afhankelijk van welk deel van het eind aan eind pijpleiding op dat ogenblik wordt uitgevoerd. Het antwoord op de fout geeft aan dat het verzoek niet is geslaagd, hoewel de specifieke reden niet wordt vermeld.

Er kunnen scenario&#39;s zijn waar een geplande plaatsing van de klantencode op bestaande variabelen baseert om nieuwe waarden te hebben, die niet met de huidige code aangewezen zouden zijn. Als dit reden tot zorg is, wordt aanbevolen op additieve wijze variabele wijzigingen aan te brengen. Hiertoe maakt u nieuwe variabelenamen in plaats van alleen de waarde van oude variabelen te wijzigen zodat oude code nooit naar de nieuwe waarde verwijst. Wanneer de nieuwe versie van de klant stabiel lijkt, kunt u de oudere waarden verwijderen.

Op dezelfde manier aangezien de waarden van een variabele niet versioned zijn, zou een terugdraaiing van code het kunnen veroorzaken om nieuwere waarden te verwijzen die kwesties veroorzaken. De bovengenoemde additieve variabele-strategie zou ook hier helpen.

Deze additieve variabele strategie is ook nuttig voor scenario&#39;s van de rampenterugwinning waar als de code van verscheidene dagen vóór moest worden opnieuw opgesteld, de veranderlijke namen en de waarden het verwijzingen nog intact zal zijn. Dit is gebaseerd op een strategie waarbij een klant een paar dagen wacht voordat deze oudere variabelen worden verwijderd, anders zou de oudere code geen geschikte variabelen hebben om naar te verwijzen.
