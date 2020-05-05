---
title: OSGi configureren voor AEM als cloudservice
description: 'OSGi-configuratie met geheime waarden en milieu-specifieke waarden '
translation-type: tm+mt
source-git-commit: 743a8b4c971bf1d3f22ef12b464c9bb0158d96c0

---


# OSGi-configuraties {#osgi-configurations}

[OSGi](https://www.osgi.org/) is een fundamenteel element in de technologiestapel van de Manager van de Ervaring van Adobe (AEM). Het wordt gebruikt om de samengestelde bundels van AEM en zijn configuraties te controleren.

OSGi verstrekt de gestandaardiseerde primitieven die toepassingen toestaan om van kleine, herbruikbare en samenwerkende componenten worden gebouwd. Deze componenten kunnen in een toepassing worden samengesteld en worden opgesteld. Dit staat gemakkelijk beheer van bundels OSGi toe aangezien zij kunnen worden tegengehouden, geïnstalleerd, individueel begonnen. De onderlinge afhankelijkheden worden automatisch verwerkt. Elke component OSGi is bevat in één van de diverse bundels. Zie de [OSGi-specificatie](https://www.osgi.org/Specifications/HomePage)voor meer informatie.

U kunt de configuratiemontages voor componenten OSGi door configuratiedossiers beheren die deel van een AEM codeproject uitmaken.

## OSGi-configuratiebestanden {#osgi-configuration-files}

De veranderingen van de configuratie worden bepaald in de codepakketten (`ui.apps`) van het Project AEM als configuratiedossiers (`.cfg.json`) onder runtime specifieke config omslagen:

`/apps/example/config.<runmode>`

De indeling van OSGi-configuratiebestanden is gebaseerd op JSON met behulp van de `.cfg.json` indeling die is gedefinieerd in het Apache Sling-project.

OSGi-configuraties richten OSGi-componenten via hun Persistent Identiteit (PID), die standaard de Java-klassenaam van de OSGi-component krijgt. Bijvoorbeeld, om configuratie OSGi voor een dienst te verstrekken OSGi die door wordt uitgevoerd:

`com.example.workflow.impl.ApprovalWorkflow.java`

een OSGi-configuratiebestand wordt gedefinieerd op:

`/apps/example/config/com.example.workflow.impl.ApprovalWorkflow.cfg.json`

volgend op het [cfg.json OSGi configuratieformaat](volgens het cfg.json OSGi configuratieformaat).

> [!NOTE]
>
> Eerdere versies van AEM ondersteunden OSGi configuratiedossiers gebruikend verschillende dossierformaten zoals .cfg., .config en als het sling van XML:OsgiConfig middeldefinities. Deze formaten worden vervangen door het cfg.json OSGi configuratieformaat.

## Resolutie van de uitvoermodus {#runmode-resolution}

De specifieke configuraties OSGi kunnen aan specifieke instanties worden gericht AEM door runmodes te gebruiken. Om runmode te gebruiken, creeer config omslagen onder `/apps/example` (waar het voorbeeld uw projectnaam is), in het formaat:

`/apps/example/config.<author|publish>.<dev|stage|prod>/`

Om het even welke configuraties OSGi in dergelijke omslagen zullen worden gebruikt als de looppaswijzen die in de config omslagnaam worden bepaald aan de looppaswijzen aanpassen die door AEM worden gebruikt.

Als AEM bijvoorbeeld de auteur en dev van de runmodi gebruikt, worden configuratieknooppunten in `/apps/example/config.author/` en `/apps/example/config.author.dev/` toegepast, terwijl configuratieknooppunten in `/apps/example/config.publish/` en `/apps/example/config.author.stage/` niet worden toegepast.

Als meerdere configuraties voor dezelfde PID van toepassing zijn, wordt de configuratie met het hoogste aantal overeenkomende uitvoeringsmodi toegepast.

De granulariteit van deze regel staat op een PID-niveau. Dit betekent dat u bepaalde eigenschappen voor dezelfde PID niet kunt definiëren in `/apps/example/config.author/` `/apps/example/config.author.dev/` en meer specifieke eigenschappen voor dezelfde PID.  De configuratie met het hoogste aantal passende looppaswijzen zal voor volledige PID efficiënt zijn.

Wanneer het ontwikkelen plaatselijk, kan een loopmode startparameter worden overgegaan om te dicteren welke loopmode configuratie OSGI zal worden gebruikt.

## Typen OSGi-configuratiewaarden {#types-of-osgi-configuration-values}

Er zijn drie soorten OSGi configuratiewaarden die met AEM als Dienst van de Wolk kunnen worden gebruikt.

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

1. **Milieu-specifieke waarden**, die waarden zijn die tussen de milieu&#39;s van de Ontwikkeling variëren, en kunnen daarom niet nauwkeurig door looppas worden gericht wijze (aangezien er één enkele `dev` runmode in AEM als Dienst van de Wolk is). Bijvoorbeeld:

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

![](assets/choose-configuration-value-type.png)

De milieu-specifieke configuraties breiden de traditionele, statisch-bepaalde configuraties OSGi uit die gealigneerde waarden bevatten, die de capaciteit verstrekken om de OSGi configuratiewaarden extern via de Manager API van de Wolk te beheren. Het is belangrijk om te begrijpen wanneer de gemeenschappelijke en traditionele benadering van het bepalen van gealigneerde waarden en het opslaan van hen in Git, zou moeten worden gebruikt, tegenover het abstraheren van de waarden in milieu-specifieke configuraties.

De volgende richtlijnen richten wanneer om niet geheime en geheime milieu-specifieke configuraties te gebruiken:

### Wanneer moet inline configuratiewaarden worden gebruikt? {#when-to-use-inline-configuration-values}

Inline-configuratiewaarden worden als de standaardbenadering beschouwd en moeten waar mogelijk worden gebruikt. Inline configuraties bieden de voordelen van:

* Zij worden gehandhaafd, met bestuur en versiegeschiedenis in Git
* Waarden zijn impliciet gekoppeld aan code-implementaties
* Zij vereisen geen extra overwegingen van plaatsing of coördinatie

Wanneer het bepalen van een OSGi configuratiewaarde, begin met gealigneerde waarden, om het even welk slechts geheim of milieu-specifieke configuraties selecteren indien vereist voor het gebruiksgeval.

### Wanneer te gebruiken de niet geheime milieu-specifieke configuratiewaarden {#when-to-use-non-secret-environment-specific-configuration-values}

Gebruik alleen omgevings-specifieke configuraties (`$[env:ENV_VAR_NAME]`) voor niet-geheime configuratiewaarden wanneer de waarden variëren per ontwikkelomgeving. Dit omvat lokale ontwikkelingsinstanties en elke AEM als een Cloud Service Development-omgeving. Vermijd het gebruik van niet-geheime omgevingspecifieke configuraties voor AEM als een Cloud Service Stage of Production-omgeving.

* Gebruik alleen niet-geheime omgevings-specifieke configuraties voor configuratiewaarden die verschillen tussen ontwikkelomgevingen, inclusief lokale ontwikkelingsinstanties.
* In plaats daarvan, gebruik de standaard gealigneerde waarden in de configuraties OSGi voor Stadium en Productie niet-geheime waarden.  In verband hiermee wordt het niet aanbevolen om omgevingspecifieke configuraties te gebruiken om het aanbrengen van configuratiewijzigingen tijdens runtime in werkgebied- en productieomgevingen te vergemakkelijken. deze wijzigingen moeten worden ingevoerd via het beheer van de broncode .

### Wanneer om geheime milieu-specifieke configuratiewaarden te gebruiken {#when-to-use-secret-environment-specific-configuration-values}

AEM als Dienst van de Wolk vereist het gebruik van milieu-specifieke configuraties (`$[secret:SECRET_VAR_NAME]`) voor om het even welke geheime OSGi configuratiewaarden, zoals wachtwoorden, privé API sleutels, of een andere waarden die niet in Git om veiligheidsredenen kunnen worden opgeslagen.

Gebruik geheime milieu-specifieke configuraties om de waarde voor geheimen op alle AEM als milieu&#39;s van de Dienst van de Wolk, met inbegrip van Stadium en Productie op te slaan.

### Een nieuwe configuratie toevoegen aan de opslagplaats {#adding-a-new-configuration-to-the-repository}

#### Wat u moet weten {#what-you-need-to-know}

Om een nieuwe configuratie aan de bewaarplaats toe te voegen moet u het volgende weten:

1. The **Persistent Identity** (PID) of the service.

   Verwijs naar het gebied van **Configuraties** in de console van het Web. De naam wordt tussen haakjes weergegeven na de bundelnaam (of in de **configuratiegegevens** onder aan de pagina).

   Maak bijvoorbeeld een knooppunt `com.day.cq.wcm.core.impl.VersionManagerImpl.` om **AEM WCM Version Manager** te configureren.

   ![chlimage_1-141](assets/chlimage_1-141.png)

1. Of een specifieke runmode wordt vereist. Maak de map:

   * `config` - voor alle uitvoeringsmodi
   * `config.author` - voor de auteursomgeving
   * `config.publish` - voor de publicatieomgeving
   * `config.<run-mode>` - in voorkomend geval

1. Of een **Configuratie** of een Configuratie **van de** Fabriek noodzakelijk is.
1. de afzonderlijke parameters die moeten worden geconfigureerd; met inbegrip van bestaande parameterdefinities die opnieuw moeten worden gemaakt.

   Verwijs het individuele parametergebied in de console van het Web. De naam wordt tussen haakjes weergegeven voor elke parameter.

   Maak bijvoorbeeld een eigenschap
   `versionmanager.createVersionOnActivation` om versie **maken bij activering** te configureren.

   ![chlimage_1-142](assets/chlimage_1-142.png)

1. Bestaat er al een configuratie in `/libs`? Als u alle configuraties in uw instantie wilt weergeven, gebruikt u het gereedschap **Query** in CRXDE Lite om de volgende SQL-query te verzenden:

   `select * from sling:OsgiConfig`

   Als zo, kan deze configuratie aan worden gekopieerd ` /apps/<yourProject>/`, dan in de nieuwe plaats worden aangepast.

## De configuratie maken in de opslagplaats {#creating-the-configuration-in-the-repository}

Om de nieuwe configuratie aan de bewaarplaats eigenlijk toe te voegen:

1. Gebruik CRXDE Lite om te navigeren naar:

   ` /apps/<yourProject>`

1. Als deze nog niet bestaat, maakt u de `config` map ( `sling:Folder`):

   * `config` - van toepassing op alle uitvoeringsmodi
   * `config.<run-mode>` - specifiek voor een bepaalde uitvoeringsmodus

1. Maak in deze map een knooppunt:

   * Type: `sling:OsgiConfig`
   * Naam: de persistente identiteit (PID);

      bijvoorbeeld het gebruik van AEM WCM Version Manager `com.day.cq.wcm.core.impl.VersionManagerImpl`
   >[!NOTE]
   >
   >Wanneer het maken van een Configuratie van de Fabriek voegt `-<identifier>` aan de naam toe.
   >
   >Zoals in: `org.apache.sling.commons.log.LogManager.factory.config-<identifier>`
   >
   >Waar `<identifier>` wordt vervangen door vrije tekst die u (moet) invoeren om het exemplaar te identificeren (u kunt deze informatie niet weglaten); bijvoorbeeld:
   >
   >`org.apache.sling.commons.log.LogManager.factory.config-MINE`

1. Voor elke parameter die u wilt vormen, creeer een bezit op deze knoop:

   * Naam: de parameternaam zoals aangetoond in de console van het Web; de naam wordt tussen haakjes weergegeven aan het einde van de veldbeschrijving. Bijvoorbeeld voor `Create Version on Activation` gebruik `versionmanager.createVersionOnActivation`
   * Type: in voorkomend geval.
   * Waarde: zoals vereist.
   U hoeft alleen eigenschappen te maken voor de parameters die u wilt configureren, anderen gebruiken nog steeds de standaardwaarden die door AEM zijn ingesteld.

1. Sla alle wijzigingen op.

   De veranderingen worden toegepast zodra de knoop door de dienst (zoals met veranderingen die in de console van het Web worden aangebracht) opnieuw te beginnen wordt bijgewerkt.

>[!CAUTION]
>
>U mag niets in het `/libs` pad wijzigen.

>[!CAUTION]
>
>De volledige weg van een configuratie moet correct zijn om het bij opstarten te lezen.


## Indeling van eigenschappen configuratie in bronbeheer {#configuration-property-format-in-source-control}

Het creëren van een nieuw bezit van de Configuratie OSGI wordt beschreven in het [Toevoegen van een nieuwe configuratie aan de bewaarplaats](#creating-the-configuration-in-the-repository) hierboven sectie. Voer de volgende stappen uit en wijzig de syntaxis zoals beschreven in de onderstaande subsecties:

### Inline-waarden {#inline-values}

Zoals u zou kunnen verwachten, worden inline waarden geformatteerd als standaardnaam-waarde paren, volgens standaardJSON syntaxis. Bijvoorbeeld:

```json
 {

 "my_var1": "val",
 "my_var2": "abc",
 "my_var3": 500

}
```

### Omgevingsspecifieke configuratiewaarden {#environment-specific-configuration-values}

De configuratie OSGi zou placeholder voor de variabele moeten toewijzen die bestemd is om per milieu te worden bepaald:

```
use $[env:ENV_VAR_NAME]
```

Klanten dienen deze techniek alleen te gebruiken voor OSGI-configuratie-eigenschappen die gerelateerd zijn aan hun aangepaste code. mag niet worden gebruikt om de door Adobe gedefinieerde OSGI-configuratie te overschrijven.

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

Men adviseert dat een eenvoudig bash manuscript wordt geschreven dat de milieuvariabelen plaatst die in de configuraties worden gebruikt en om het uit te voeren alvorens AEM te beginnen. Gereedschappen zoals [https://direnv.net/](https://direnv.net/) helpen u bij het vereenvoudigen van deze aanpak. Afhankelijk van het type van de waarden, zouden zij in broncodebeheer kunnen worden gecontroleerd, als zij tussen iedereen kunnen worden gedeeld.

De waarden voor geheimen worden gelezen uit bestanden. Daarom moet voor elke plaatsaanduiding die een geheim gebruikt, een tekstbestand met de geheime waarde worden gemaakt.

Als bijvoorbeeld `$[secret:server_password]` wordt gebruikt, moet een tekstbestand met de naam **server_password** worden gemaakt. Al deze geheime dossiers moeten in de zelfde folder worden opgeslagen en het kaderbezit `org.apache.felix.configadmin.plugin.interpolation.secretsdir` moet met die lokale folder worden gevormd.

### Auteur versus configuratie publiceren {#author-vs-publish-configuration}

Als voor een OSGI-eigenschap andere waarden zijn vereist voor auteur en publiceren:

* Er moeten aparte `config.author` en `config.publish` OSGi-mappen worden gebruikt, zoals wordt beschreven in de sectie [Resolutie van](#runmode-resolution)uitvoermodus.
* er moeten onafhankelijke variabelenamen worden gebruikt . Het wordt aangeraden een voorvoegsel te gebruiken, bijvoorbeeld auteur_<variablename> en publish_<variablename> waarbij de namen van variabelen gelijk zijn

### Configuratievoorbeelden {#configuration-examples}

In de onderstaande voorbeelden wordt ervan uitgegaan dat er naast het werkgebied en de prod-omgevingen 3 ontwikkelomgevingen zijn.

**Voorbeeld 1**

De bedoeling is dat de waarde van de eigenschap OSGI voor het werkgebied en de prod gelijk `my_var1` moet zijn, maar voor elk van de 3 dev-omgevingen verschilt.

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
{ "my_var1": "val", "my_var2": "abc", "my_var3": 500}
</pre>
</td>
</tr>
<tr>
<td>
config.dev
</td>
<td>
<pre>
{ "my_var1": "$[env:my_var1]" "my_var2": "abc", "my_var3": 500}
</pre>
</td>
</tr>
</table>

**Voorbeeld 2**

De bedoeling is dat de waarde van de eigenschap OSGI `my_var1` verschilt voor het werkgebied, de prod en voor elk van de drie dev-omgevingen. De API voor Cloud Manager moet dus worden aangeroepen om de waarde voor elke dev- `my_var1` gebeurtenis in te stellen.

