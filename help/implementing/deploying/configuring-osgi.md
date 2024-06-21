---
title: OSGi configureren voor Adobe Experience Manager as a Cloud Service
description: OSGi-configuratie met geheime waarden en milieu-specifieke waarden
feature: Deploying
exl-id: f31bff80-2565-4cd8-8978-d0fd75446e15
role: Admin
source-git-commit: f66ea281e6abc373e9704e14c97b77d82c55323b
workflow-type: tm+mt
source-wordcount: '3302'
ht-degree: 0%

---


# OSGi configureren voor Adobe Experience Manager as a Cloud Service {#configuring-osgi-for-aem-as-a-cloud-service}

[OSGi](https://www.osgi.org/) is een fundamenteel element in de technologiestapel van Adobe Experience Manager (AEM). Het wordt gebruikt om de samengestelde bundels van AEM en zijn configuraties te controleren.

OSGi verstrekt de gestandaardiseerde primitieven die toepassingen toestaan om van kleine, herbruikbare, en samenwerkingscomponenten worden geconstrueerd. Deze componenten kunnen in een toepassing worden samengesteld en worden opgesteld. Dit staat gemakkelijk beheer van bundels OSGi toe aangezien zij kunnen worden tegengehouden, geïnstalleerd, individueel begonnen. De onderlinge afhankelijkheden worden automatisch verwerkt. Elke component OSGi is bevat in één van de diverse bundels. Zie de klasse [OSGi-specificatie](https://help.eclipse.org/latest/index.jsp).

U kunt de configuratiemontages voor componenten OSGi door configuratiedossiers beheren die deel van een AEM codeproject uitmaken.

>[!TIP]
>
>U kunt Cloud Manager gebruiken om omgevingsvariabelen te configureren. Raadpleeg de documentatie voor meer informatie [hier.](/help/implementing/cloud-manager/environment-variables.md)

## OSGi-configuratiebestanden {#osgi-configuration-files}

De veranderingen van de configuratie worden bepaald in de codepakketten van het AEM Project (`ui.config`) als configuratiebestanden (`.cfg.json`) onder specifieke configuratiemappen voor de runmode:

`/apps/example/config.<runmode>`

De indeling van OSGi-configuratiebestanden is gebaseerd op JSON met behulp van de `.cfg.json` indeling die is gedefinieerd door het Apache Sling-project.

OSGi-configuraties richten OSGi-componenten via hun Persistent Identity (PID), die standaard de Java™-klassenaam van de OSGi-component krijgt. Bijvoorbeeld, om configuratie OSGi voor een dienst te verstrekken OSGi die door wordt uitgevoerd:

`com.example.workflow.impl.ApprovalWorkflow.java`

een OSGi-configuratiebestand wordt gedefinieerd op:

`/apps/example/config/com.example.workflow.impl.ApprovalWorkflow.cfg.json`

na de `cfg.json` OSGi-configuratieformaat.

>[!NOTE]
>
>Eerdere versies van AEM ondersteunde OSGi-configuratiebestanden die verschillende bestandsindelingen gebruiken, zoals `.cfg`, `.config` en als XML `sling:OsgiConfig` brondefinities. Deze indelingen worden vervangen door de `.cfg.json` OSGi-configuratieformaat.

>[!NOTE]
>
>De OSGi-configuraties worden niet opgeslagen onder /apps, zoals AEM instanties in de cloud die ze op een externe locatie opslaan. Inchecken in Cloud Manager [Ontwerpconsole](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console#configurations) om OSGi te bekijken vormt.

## Resolutie van de uitvoermodus {#runmode-resolution}

>[!TIP]
>
>AEM 6.x ondersteunt aangepaste runmodi, maar AEM as a Cloud Service niet. AEM as a Cloud Service ondersteuning en [exacte set runmodi](./overview.md#runmodes). Om het even welke variatie in configuraties OSGi tussen AEM as a Cloud Service milieu&#39;s moet worden behandeld gebruikend [OSGi-configuratiemomgevingsvariabelen](#environment-specific-configuration-values).

De specifieke configuraties OSGi kunnen aan specifieke AEM instanties worden gericht door runmodes te gebruiken. Om runmode te gebruiken, creeer config omslagen onder `/apps/example` (waar het voorbeeld uw projectnaam is), in de volgende notatie:

`/apps/example/config.<author|publish>.<dev|stage|prod>/`

Om het even welke configuraties OSGi in dergelijke omslagen worden gebruikt als de runmodes die in de config omslagnaam worden bepaald de runmodes aanpassen die door AEM worden gebruikt.

Als AEM bijvoorbeeld de auteur en dev van de runmodi gebruikt, worden configuratieknooppunten in `/apps/example/config.author/` en `/apps/example/config.author.dev/` worden toegepast, terwijl configuratieknooppunten in `/apps/example/config.publish/` en `/apps/example/config.author.stage/` niet worden toegepast.

Als meerdere configuraties voor dezelfde PID van toepassing zijn, wordt de configuratie met het hoogste aantal overeenkomende uitvoeringsmodi toegepast.

De granulariteit van deze regel staat op een PID-niveau. Dit betekent dat u geen eigenschappen voor dezelfde PID kunt definiëren in `/apps/example/config.author/` en meer specifieke `/apps/example/config.author.dev/` voor dezelfde PID. De configuratie met het hoogste aantal passende runmodes is effectief voor volledige PID.

>[!NOTE]
>
>A `config.preview` OSGi-configuratiemap **kan** op dezelfde wijze worden gedeclareerd `config.publish` kan worden gedeclareerd als map. In plaats daarvan, erft de voorproefrij zijn configuratie OSGi van de waarden van publicatielaag.

Bij lokale ontwikkeling, een runtime startparameter `-r`, wordt gebruikt om de configuratie op te geven van de runmode OSGI.

```shell
$ java -jar aem-sdk-quickstart-xxxx.x.xxx.xxxx-xxxx.jar -r publish,dev
```

### Runmodi controleren

AEM as a Cloud Service runmodes worden duidelijk bepaald gebaseerd op het milieutype en de dienst. Controleer de [volledige lijst van beschikbare AEM as a Cloud Service runmodi](./overview.md#runmodes).

De OSGi-configuratiewaarden die door de runmode worden gespecificeerd, kunnen worden geverifieerd door:

1. Het openen van de AEM als omgeving van Cloud Servicen [Ontwerpconsole](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html)
1. De te inspecteren servicelaag(s) selecteren met de opdracht __Pod__ vervolgkeuzelijst
1. De __Status__ tab
1. Selecteren __Configuraties__ van de __Status dumpen__ vervolgkeuzelijst
1. De __Status ophalen__ knop

In de resulterende weergave worden alle configuraties van OSGi-componenten voor de geselecteerde laag of lagen weergegeven met hun toepasselijke OSGi-configuratiewaarden. Deze waarden kunnen met de OSGi configuratiewaarden in de broncode van het AEM project onder worden van verwijzingen voorzien `/apps/example/osgiconfig/config.<runmode(s)>`.


Om te verifiëren worden de aangewezen OSGi configuratiewaarden toegepast:

1. In de Uitvoer van de Configuratie van de Console van de Ontwikkelaar
1. Zoek de `pid` die de configuratie OSGi vertegenwoordigen om te verifiëren; dit is de naam van het OSGi configuratiedossier in de broncode van het AEM project.
1. Inspect the `properties` lijst voor de `pid` en verifieer de sleutel en de waarden het OSGi- configuratiedossier in de AEM projectbroncode voor runmode aanpassen die wordt geverifieerd.=


## Typen OSGi-configuratiewaarden {#types-of-osgi-configuration-values}

Er zijn drie soorten OSGi configuratiewaarden die met Adobe Experience Manager as a Cloud Service kunnen worden gebruikt.

1. **Inline-waarden**, die waarden zijn die hard-gecodeerd in de configuratie OSGi zijn en in Git worden opgeslagen. Bijvoorbeeld:

   ```json
   {
      "connection.timeout": 1000
   }
   ```

1. **Geheime waarden**, dit zijn waarden die om veiligheidsredenen niet in Git mogen worden opgeslagen. Bijvoorbeeld:

   ```json
   {
   "api-key": "$[secret:server-api-key]"
   } 
   ```

1. **Milieuspecifieke waarden**, die waarden zijn die tussen de milieu&#39;s van de Ontwikkeling variëren, en daarom niet nauwkeurig kunnen worden gericht door looppas wijze (aangezien er één enkele is `dev` (in Adobe Experience Manager as a Cloud Service). Bijvoorbeeld:

   ```json
   {
    "url": "$[env:server-url]"
   }
   ```

   Één enkel OSGi- configuratiedossier kan om het even welke combinatie deze types van configuratiewaarde samen gebruiken. Bijvoorbeeld:

   ```json
   {
   "connection.timeout": 1000,
   "api-key": "$[secret:server-api-key]",
   "url": "$[env:server-url]"
   }
   ```

## Hoe te om het aangewezen Type van Waarde van de Configuratie te kiezen OSGi {#how-to-choose-the-appropriate-osgi-configuration-value-type}

Het algemene geval voor OSGi gebruikt inline OSGi configuratiewaarden. Milieu-specifieke configuraties worden gebruikt slechts voor specifieke gebruiksgevallen waar een waarde tussen dev milieu&#39;s verschilt.

![De beslissende boom op hoe te om het aangewezen type van configuratiewaarde te gebruiken](assets/choose-configuration-value-type_res1.png)

De milieu-specifieke configuraties breiden de traditionele, statisch bepaalde configuraties OSGi uit die gealigneerde waarden bevatten, die de capaciteit verstrekken om de OSGi configuratiewaarden extern via de Manager API van de Wolk te beheren. Het is belangrijk om te begrijpen wanneer de gemeenschappelijke en traditionele benadering van het bepalen van gealigneerde waarden en het opslaan van hen in Git, zou moeten worden gebruikt, tegenover het abstraheren van de waarden in milieu-specifieke configuraties.

De volgende richtlijnen richten wanneer om niet geheime en geheime milieu-specifieke configuraties te gebruiken:

### Wanneer moet inline configuratiewaarden worden gebruikt? {#when-to-use-inline-configuration-values}

Inline-configuratiewaarden worden als de standaardbenadering beschouwd en moeten waar mogelijk worden gebruikt. Inline configuraties bieden de voordelen van:

* Zij worden gehandhaafd, met bestuur en versiegeschiedenis in Git
* Waarden zijn impliciet gekoppeld aan code-implementaties
* Zij vereisen geen extra overwegingen van plaatsing of coördinatie

Wanneer het bepalen van een OSGi configuratiewaarde, begin met gealigneerde waarden, en selecteer slechts geheime of milieu-specifieke configuraties indien nodig voor het gebruiksgeval.

### Wanneer te gebruiken de niet geheime milieu-specifieke configuratiewaarden {#when-to-use-non-secret-environment-specific-configuration-values}

Gebruik alleen omgevingspecifieke configuraties (`$[env:ENV_VAR_NAME]`) voor niet-geheime configuratiewaarden wanneer de waarden variëren voor de voorproefrij of over ontwikkelomgevingen variëren. Dit omvat lokale ontwikkelingsinstanties en alle Adobe Experience Manager as a Cloud Service-ontwikkelomgevingen. Vermijd het gebruik van niet-geheime omgevingspecifieke configuraties voor Adobe Experience Manager as a Cloud Service Stage- of Production-omgevingen, anders dan voor het instellen van unieke waarden voor de voorvertoningslaag.

* Gebruik alleen niet-geheime omgevingspecifieke configuraties voor configuratiewaarden die verschillen tussen de publicatie- en voorvertoningslaag, of voor waarden die verschillen tussen ontwikkelomgevingen, inclusief lokale ontwikkelingsinstanties.
* Naast het scenario wanneer de voorproefrij van publicatielaag moet variëren, gebruik de standaard gealigneerde waarden in de configuraties OSGi voor Stadium en Productie niet geheime waarden. In verband hiermee wordt het niet aanbevolen om omgevingspecifieke configuraties te gebruiken om het aanbrengen van configuratiewijzigingen tijdens runtime in werkgebied- en productieomgevingen te vergemakkelijken; deze wijzigingen moeten worden geïntroduceerd via broncodebeheer.

### Wanneer gebruiken geheim milieu-specifieke configuratiewaarden {#when-to-use-secret-environment-specific-configuration-values}

Adobe Experience Manager as a Cloud Service vereist het gebruik van omgevingspecifieke configuraties (`$[secret:SECRET_VAR_NAME]`) voor om het even welke geheime OSGi configuratiewaarden, zoals wachtwoorden, privé API sleutels, of om het even welke andere waarden die niet in Git om veiligheidsredenen kunnen worden opgeslagen.

Gebruik geheime omgevingspecifieke configuraties om de waarde voor geheimen op te slaan in alle Adobe Experience Manager as a Cloud Service-omgevingen, inclusief werkgebied en productie.

## OSGi-configuraties maken {#creating-osgi-configurations}

Er zijn twee manieren om configuraties tot stand te brengen OSGi, zoals hieronder beschreven. De eerste benadering wordt typisch gebruikt voor het vormen van componenten van douaneOSGi die bekende eigenschappen OSGi en waarden door de ontwikkelaar, en laatstgenoemde voor AEM-verstrekte componenten OSGi hebben.

### OSGi-configuraties schrijven {#writing-osgi-configurations}

De JSON geformatteerde OSGi configuratiedossiers kunnen door hand in het AEM project worden geschreven. Dit is vaak de snelste manier om configuraties OSGi voor bekende componenten te creëren OSGi, en vooral de componenten van douane OSGi die door de zelfde ontwikkelaar die de configuraties bepalen zijn ontworpen en ontwikkeld. Deze benadering kan ook worden gebruikt om configuraties voor de zelfde component te kopiëren/te kleven en bij te werken OSGi over diverse runmode omslagen.

1. In uw winde, open `ui.apps` project, bepaal de plaats van of creeer de config omslag (`/apps/.../config.<runmode>`) die de runmodes richt de nieuwe configuratie OSGi moet uitvoeren
1. In deze configuratiemap maakt u een `<PID>.cfg.json` bestand. PID is de Persistente Identiteit van de component OSGi. Het is gewoonlijk de volledige klassennaam van de OSGi componentimplementatie. Bijvoorbeeld:
   `/apps/.../config/com.example.workflow.impl.ApprovalWorkflow.cfg.json`
Voor de OSGi-configuratiefabrieksbestandsnamen wordt het `<factoryPID>-<name>.cfg.json` naamgevingsconventie
1. De nieuwe openen `.cfg.json` dossier, en bepaal de sleutel/waardecombinaties voor het bezit OSGi en waardeparen, na [JSON OSGi-configuratie-indeling](https://sling.apache.org/documentation/bundles/configuration-installer-factory.html#configuration-files-cfgjson-1).
1. Sla uw wijzigingen op in de nieuwe `.cfg.json` file
1. Voeg en bewijs uw nieuw OSGi configuratiedossier aan Git toe

### OSGi-configuraties genereren met de AEM SDK QuickStart {#generating-osgi-configurations-using-the-aem-sdk-quickstart}

De AEM QuickStart Jar&#39;s AEM Web Console van SDK kan worden gebruikt vormt componenten OSGi, en de configuraties van export OSGi als JSON. Dit is nuttig om AEM-verstrekte componenten te vormen OSGi waarvan eigenschappen OSGi en hun waardeformaten niet goed kunnen worden begrepen door de ontwikkelaar die de configuraties OSGi in het AEM project bepaalt.

>[!NOTE]
>
>De configuratie-interface van de AEM webconsole schrijft `.cfg.json` in de opslagplaats. Daarom ben zich van dit werkschema bewust om potentieel onverwacht gedrag tijdens lokale ontwikkeling te vermijden, wanneer de AEM project-bepaalde configuraties OSGi van de geproduceerde configuraties kunnen verschillen.

1. Meld u aan bij de AEM SDK QuickStart Jar&#39;s AEM webconsole op `https://<host>:<port>/system/console` als beheerder
1. Navigeren naar **OSGi** > **Configuratie**
1. Om te vormen, bepaal de plaats van de component OSGi en selecteer zijn te uitgeven titel
   ![OSGi-configuratie](./assets/configuring-osgi/configuration.png)
1. Bewerk indien nodig de OSGi-waarden van het configuratiebezit via de webinterface
1. Registreer de Persistent Identity (PID) op een veilige plaats. Dit wordt later gebruikt om de configuratie te produceren OSGi JSON
1. Selecteer Opslaan
1. Ga naar OSGi > OSGi Installer Configuration Printer
1. Plak in PID die in Stap 5 wordt gekopieerd, zorg ervoor de Formaat van de Rangschikking wordt geplaatst aan &quot;OSGi Configurator JSON&quot;
1. Afdrukken selecteren
1. De configuratie OSGi in formaat JSON zal in de Serialized sectie van de Eigenschappen van de Configuratie tonen
   ![OSGi-installateursconfiguratieserver](./assets/configuring-osgi/osgi-installer-configurator-printer.png)
1. In uw winde, open `ui.apps` project, bepaal de plaats van of creeer de config omslag (`/apps/.../config.<runmode>`) die de runmodes richt de nieuwe configuratie OSGi moet uitvoeren.
1. In deze configuratiemap maakt u een `<PID>.cfg.json` bestand. De PID is dezelfde waarde uit stap 5.
1. Plak de Generialiseerde Eigenschappen van de Configuratie van Stap 10 in `.cfg.json` bestand.
1. Sla uw wijzigingen op in de nieuwe `.cfg.json` bestand.
1. Voeg en bewijs uw nieuw OSGi configuratiedossier aan Git toe.


## Indelingen van eigenschappen van OSGi-configuratie {#osgi-configuration-property-formats}

### Inline-waarden {#inline-values}

Inline-waarden worden opgemaakt als standaard naam-waardeparen, volgens de standaard JSON-syntaxis. Bijvoorbeeld:

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

De klanten zouden deze techniek voor OSGi configuratieeigenschappen met betrekking tot hun douanecode slechts moeten gebruiken; het moet niet worden gebruikt om Adobe-bepaalde configuratie met voeten te treden OSGi.

>[!NOTE]
>
>Plaatsaanduidingen kunnen niet worden gebruikt in [instructies opnieuw aanwijzen](/help/implementing/deploying/overview.md#repoinit).

### Geheime configuratiewaarden {#secret-configuration-values}

De configuratie OSGi zou placeholder voor het geheim moeten toewijzen dat bestemd is om per milieu te worden bepaald:

```
use $[secret:SECRET_VAR_NAME]
```

### Naam variabele {#variable-naming}

Het volgende is op zowel milieu-specifieke als geheime configuratiewaarden van toepassing.

De namen van variabelen moeten de volgende regels volgen:

* Minimumlengte: 2
* Maximumlengte: 100
* Moet overeenkomen met regex: `[a-zA-Z_][a-zA-Z_0-9]*`

Waarden voor de variabelen mogen niet meer dan 2048 tekens bevatten.

>[!CAUTION]
>
>Er zijn regels met betrekking tot het gebruik van bepaalde voorvoegsels voor variabelennamen:
>
>1. Variabelennamen vooraf ingesteld met `INTERNAL_`, `ADOBE_`, of `CONST_` zijn gereserveerd door Adobe. Om het even welke klant-vastgestelde variabelen die met deze prefixen beginnen worden genegeerd.
>
>1. Klanten mogen niet verwijzen naar variabelen vooraf met `INTERNAL_` of `ADOBE_` ofwel.
>
>1. Omgevingsvariabelen met het voorvoegsel `AEM_` worden door het product gedefinieerd als Public API die door klanten moet worden gebruikt en ingesteld.
>   Terwijl klanten omgevingsvariabelen kunnen gebruiken en instellen die beginnen met het voorvoegsel `AEM_` zij zouden hun eigen variabelen niet met dit voorvoegsel moeten bepalen.

### Standaardwaarden {#default-values}

Het volgende is op zowel milieu-specifieke als geheime configuratiewaarden van toepassing.

Als er geen waarde per omgeving is ingesteld, wordt de tijdelijke aanduiding tijdens runtime niet vervangen en blijft deze op zijn plaats omdat er geen interpolatie heeft plaatsgevonden. Om dit te voorkomen, kan een standaardwaarde als deel van placeholder met de volgende syntaxis worden verstrekt:

```
$[env:ENV_VAR_NAME;default=<value>]
```

Als er een standaardwaarde is opgegeven, wordt de tijdelijke aanduiding vervangen door de waarde voor de afzonderlijke omgeving, indien opgegeven, of door de opgegeven standaardwaarde.

### Lokale ontwikkeling {#local-development}

Het volgende is op zowel milieu-specifieke als geheime configuratiewaarden van toepassing.

Variabelen kunnen in de lokale omgeving worden gedefinieerd, zodat ze tijdens runtime door de lokale AEM worden opgehaald. Bijvoorbeeld op Linux®:

```bash
export ENV_VAR_NAME=my_value
```

Men adviseert dat een eenvoudig bash manuscript wordt geschreven dat de milieuvariabelen plaatst die in de configuraties worden gebruikt en het uitvoeren alvorens AEM te beginnen. Gereedschappen zoals [https://direnv.net/](https://direnv.net/) helpen bij het vereenvoudigen van deze aanpak. Afhankelijk van het type van de waarden, zouden zij in broncodebeheer kunnen worden gecontroleerd, als zij tussen iedereen kunnen worden gedeeld.

De waarden voor geheimen worden gelezen uit bestanden. Daarom moet voor elke plaatsaanduiding die een geheim gebruikt, een tekstbestand met de geheime waarde worden gemaakt.

Als `$[secret:server_password]` wordt gebruikt, een tekstbestand genaamd **server_password** moet worden gemaakt. Al deze geheime dossiers moeten in de zelfde folder en het kader bezit worden opgeslagen `org.apache.felix.configadmin.plugin.interpolation.secretsdir` moet met die lokale folder worden gevormd.

>[!CAUTION]
>
>Bestandsextensies zijn niet toegestaan voor het tekstbestand.
>
>In het bovenstaande voorbeeld moet het tekstbestand een naam hebben **server_password** - zonder bestandsextensie.

De `org.apache.felix.configadmin.plugin.interpolation.secretsdir` is een Sling framework-eigenschap; deze eigenschap wordt dus niet ingesteld in de felix-console (/system/console), maar wel in het sling.properties-bestand dat wordt gebruikt wanneer het systeem wordt opgestart. Dit bestand staat in de subdir /conf van de uitgepakte map Jar/install (crx-quickstart/conf).

voorbeeld: voeg deze regel toe aan het einde van het bestand &#39;crx-quickstart/conf/sling.properties&#39; om &#39;crx-quickstart/secretsdir&#39; te configureren als een geheime map:

```
org.apache.felix.configadmin.plugin.interpolation.secretsdir=${sling.home}/secretsdir
```

### Auteur versus configuratie publiceren {#author-vs-publish-configuration}

Als een bezit OSGi verschillende waarden voor auteur tegenover publiceert vereist:

* Afzonderlijk `config.author` en `config.publish` U dient OSGi-mappen te gebruiken, zoals beschreven in het dialoogvenster [Sectie Resolutie van uitvoermodus](#runmode-resolution).
* Er zijn twee opties om de onafhankelijke variabelennamen te maken die moeten worden gebruikt:
   * de eerste optie, die wordt aanbevolen: in alle OSGi-mappen (zoals `config.author` en `config.publish`) gedeclareerd om verschillende waarden te definiëren, dezelfde variabelenaam gebruiken. Bijvoorbeeld
     `$[env:ENV_VAR_NAME;default=<value>]`, waarbij de standaardwaarde overeenkomt met de standaardwaarde voor die laag (auteur of publicatie). Wanneer u de omgevingsvariabele instelt via [Cloud Manager-API](#cloud-manager-api-format-for-setting-properties) of via een client, onderscheid maken tussen de lagen aan de hand van de parameter &quot;service&quot; zoals in dit [API-naslagdocumentatie](https://developer.adobe.com/experience-cloud/cloud-manager/api-reference/). De &quot;dienst&quot;parameter zal de waarde van de variabele aan de aangewezen OSGi rij binden. Het kan &quot;auteur&quot;, &quot;publish&quot; of &quot;preview&quot; zijn.
   * de tweede optie is het declareren van verschillende variabelen met een voorvoegsel, zoals `author_<samevariablename>` en `publish_<samevariablename>`

### Configuratievoorbeelden {#configuration-examples}

In de onderstaande voorbeelden wordt ervan uitgegaan dat er naast het werkgebied en de prod-omgevingen drie ontwikkelomgevingen zijn.

**Voorbeeld 1**

De intent is voor de waarde van de eigenschap OSGi `my_var1` hetzelfde zijn voor het werkgebied en de pod, maar verschillen voor elk van de drie ontwikkelomgevingen.

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
{ "my_var1": "val", "my_var2": "abc", "my_var3": 500 }
</pre>
</td>
</tr>
<tr>
<td>
config.dev
</td>
<td>
<pre>
{ "my_var1" : "$[env:my_var1]" "my_var2": "abc", "my_var3": 500 }
</pre>
</td>
</tr>
</table>

**Voorbeeld 2**

De intent is voor de waarde van de eigenschap OSGi `my_var1` verschillen voor het werkgebied, de prod en voor elk van de drie ontwikkelomgevingen. De API voor Cloud Manager moet dus worden aangeroepen om de waarde in te stellen voor `my_var1` voor elke dev env.

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
{ "my_var1": "val1", "my_var2": "abc", "my_var3": 500 }
</pre>
</td>
</tr>
<tr>
<td>
config.prod
</td>
<td>
<pre>
{ "my_var1": "val2", "my_var2": "abc", "my_var3": 500 }
</pre>
</td>
</tr>
<tr>
<td>
config.dev
</td>
<td>
<pre>
{ "my_var1" : "$[env:my_var1]" "my_var2": "abc", "my_var3": 500 }
</pre>
</td>
</tr>
</table>

**Voorbeeld 3**

De intent is voor de waarde van de eigenschap OSGi `my_var1` hetzelfde moet zijn voor werkgebied, productie en slechts een van de ontwikkelomgevingen, maar anders voor de andere twee ontwikkelomgevingen. In dit geval moet de API voor Cloud Manager worden aangeroepen om de waarde in te stellen van `my_var1` voor elk van de ontwikkelomgevingen, inclusief voor de ontwikkelomgeving, die dezelfde waarde moet hebben als fase en productie. De waarde die in de map is ingesteld, wordt niet overgenomen **config**.

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
{ "my_var1": "val1", "my_var2": "abc", "my_var3": 500 }
</pre>
</td>
</tr>
<tr>
<td>
config.dev
</td>
<td>
<pre>
{ "my_var1" : "$[env:my_var1]" "my_var2": "abc", "my_var3": 500 }
</pre>
</td>
</tr>
</table>

Een andere manier om dit te verwezenlijken zou zijn een standaardwaarde voor het vervangingsteken in config.dev omslag dusdanig te plaatsen dat het de zelfde waarde zoals in in **config** map.

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
{ "my_var1": "val1", "my_var2": "abc", "my_var3": 500 }
</pre>
</td>
</tr>
<tr>
<td>
config.dev
</td>
<td>
<pre>
{ "my_var1": "$[env:my_var1;default=val1]" "my_var2": "abc", "my_var3": 500 }
</pre>
</td>
</tr>
</table>

## Cloud Manager API-indeling voor het instellen van eigenschappen {#cloud-manager-api-format-for-setting-properties}

Zie [deze pagina](https://developer.adobe.com/experience-cloud/cloud-manager/docs/) over hoe API moet worden gevormd.
>[!NOTE]
>
>Zorg ervoor dat de gebruikte API voor Cloud Manager de rol &quot;Deployment Manager - Cloud Service&quot; heeft toegewezen. Andere rollen kunnen niet alle onderstaande opdrachten uitvoeren.

>[!TIP]
>
>U kunt Cloud Manager ook gebruiken om omgevingsvariabelen te configureren. Raadpleeg de documentatie voor meer informatie [hier.](/help/implementing/cloud-manager/environment-variables.md)

### Waarden instellen via API {#setting-values-via-api}

Het roepen van API stelt de nieuwe variabelen en de waarden aan een milieu van de Wolk op, gelijkend op een typische pijpleiding van de de plaatsing van de klantencode. De auteur- en publicatieservices worden opnieuw gestart en er wordt een verwijzing naar de nieuwe waarden gemaakt. Dit duurt meestal enkele minuten.

```
PATCH /program/{programId}/environment/{environmentId}/variables
```

```json
[
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

>[!NOTE]
>Standaardvariabelen worden niet ingesteld via API, maar in de eigenschap OSGi zelf.
>
>Zie [deze pagina](https://developer.adobe.com/experience-cloud/cloud-manager/api-reference/) voor meer informatie .

### Waarden ophalen via API {#getting-values-via-api}

```
GET /program/{programId}/environment/{environmentId}/variables
```

Zie [deze pagina](https://developer.adobe.com/experience-cloud/cloud-manager/api-reference/) voor meer informatie .

### Waarden verwijderen via API {#deleting-values-via-api}

```
PATCH /program/{programId}/environment/{environmentId}/variables
```

Als u een variabele wilt verwijderen, neemt u deze op met een lege waarde.

Zie [deze pagina](https://developer.adobe.com/experience-cloud/cloud-manager/api-reference/) voor meer informatie .

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
>Zie [deze pagina](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid) voor meer informatie over het configureren van waarden met de plug-in Cloud Manager voor Adobe I/O CLI.

### Aantal variabelen {#number-of-variables}

Er kunnen maximaal 200 variabelen per omgeving worden gedeclareerd.

## De Overwegingen van de plaatsing voor geheime en milieu-specifieke configuratiewaarden {#deployment-considerations-for-secret-and-environment-specific-configuration-values}

Omdat de geheime en milieu-specifieke configuratiewaarden buiten Git leven, en daarom geen deel van de formele de plaatsingsmechanismen van Adobe Experience Manager as a Cloud Service uitmaken, zou de klant, in het plaatsingsproces van Adobe Experience Manager as a Cloud Service moeten leiden beheren en integreren.

Zoals hierboven vermeld, voert het roepen van API de nieuwe variabelen en waarden aan de milieu&#39;s van de Wolk, gelijkend op een typische pijpleiding van de de plaatsing van de klantencode op. De auteur- en publicatieservices worden opnieuw gestart en er wordt een verwijzing naar de nieuwe waarden gemaakt. Dit duurt meestal enkele minuten. De kwaliteitspoorten en -tests die worden uitgevoerd door Cloud Manager tijdens een reguliere code-implementatie, worden tijdens dit proces niet uitgevoerd.

Klanten bellen de API doorgaans om omgevingsvariabelen in te stellen voordat ze code implementeren die op hen is gebaseerd in Cloud Manager. In sommige situaties, zou men een bestaande variabele kunnen willen wijzigen nadat de code reeds is opgesteld.

>[!NOTE]
>
>API kan niet slagen wanneer een pijpleiding in gebruik is, of een AEM update of klantenplaatsing, afhankelijk van welk deel van het eind aan eind pijpleiding op dat ogenblik wordt uitgevoerd. Het antwoord op de fout geeft aan dat het verzoek niet is geslaagd, hoewel de specifieke reden niet wordt vermeld.

Er kunnen scenario&#39;s zijn waar een geplande plaatsing van de klantencode op bestaande variabelen baseert om nieuwe waarden te hebben, die niet met de huidige code aangewezen zouden zijn. Als dit een probleem is, wordt aanbevolen op additieve wijze variabele wijzigingen aan te brengen. Hiertoe maakt u nieuwe variabelenamen in plaats van alleen de waarde van oude variabelen te wijzigen zodat oude code nooit naar de nieuwe waarde verwijst. Wanneer de nieuwe versie van de klant stabiel lijkt, kunt u de oudere waarden verwijderen.

Op dezelfde manier aangezien de waarden van een variabele niet versioned zijn, zou een terugdraaiing van code het kunnen veroorzaken om nieuwere waarden te verwijzen die kwesties veroorzaken. De eerder genoemde additieve variabele-strategie zou hier ook toe bijdragen.

Deze additieve variabele strategie is ook nuttig voor scenario&#39;s van de rampenterugwinning waar als de code van verscheidene dagen vóór moest worden opnieuw opgesteld, de veranderlijke namen en de waarden het verwijzingen nog intact zal zijn. Dit is gebaseerd op een strategie waarbij een klant een paar dagen wacht voordat deze oudere variabelen worden verwijderd, anders zou de oudere code geen geschikte variabelen hebben om naar te verwijzen.
