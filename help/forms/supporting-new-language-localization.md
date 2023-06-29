---
title: Ondersteuning voor nieuwe landinstellingen toevoegen aan een adaptief formulier
seo-title: Learn to add support for new locales to your adaptive forms
description: Met AEM Forms kunt u nieuwe landinstellingen toevoegen voor het lokaliseren van adaptieve formulieren. Engels (en), Spaans (es), Frans (fr), Italiaans (it), Duits (de), Japans (ja), Portugees-Braziliaans (pt-BR), Chinees (zh-CN), Chinees-Taiwan (zh-TW) en Koreaanse (ko-KR) landinstellingen.
seo-description: AEM Forms allows you to add new locales for localizing adaptive forms. We support 10 locales out of the box curently, as  "en","fr","de","ja","pt-br","zh-cn","zh-tw","ko-kr","it","es".
exl-id: 4c7d6caa-1adb-4663-933f-b09129b9baef
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '1190'
ht-degree: 0%

---

# Ondersteuning voor nieuwe landinstellingen voor Adaptive Forms-lokalisatie {#supporting-new-locales-for-adaptive-forms-localization}

AEM Forms biedt in de box-ondersteuning voor de landinstellingen Engels (en), Spaans (es), Frans (fr), Italiaans (it), Duits (de), Japans (ja), Portugees-Braziliaans (pt-BR), Chinees (zh-CN), Chinees-Taiwan (zh-TW) en Koreaans (ko-KR). U kunt ook ondersteuning toevoegen voor meer landinstellingen, zoals Hindi(hi_IN).

## Werken met taalwoordenboeken {#about-locale-dictionaries}

De lokalisatie van adaptieve formulieren is afhankelijk van twee typen taalwoordenboeken:

* **Formulierspecifiek woordenboek** Bevat tekenreeksen die in adaptieve formulieren worden gebruikt. Bijvoorbeeld labels, veldnamen, foutberichten en Help-beschrijvingen. Het wordt beheerd als een set XLIFF-bestanden voor elke landinstelling en u kunt het bestand openen op `[author-instance]/libs/cq/i18n/gui/translator.html`.

* **Algemene woordenboeken** Er zijn twee algemene woordenboeken, beheerd als JSON-objecten, in AEM clientbibliotheek. Deze woordenboeken bevatten standaardfoutberichten, naam van de maand, valutasymbolen, datum- en tijdpatronen, enzovoort. U vindt deze woordenboeken op `[author-instance]/libs/fd/xfaforms/clientlibs/I18N`. Deze locaties bevatten afzonderlijke mappen voor elke landinstelling. Omdat algemene woordenboeken niet vaak worden bijgewerkt, kunnen browsers door afzonderlijke JavaScript-bestanden voor elke landinstelling te bewaren deze in cache plaatsen en het gebruik van de netwerkbandbreedte verminderen wanneer ze toegang krijgen tot verschillende adaptieve formulieren op dezelfde server.

## Ondersteuning voor nieuwe landinstellingen toevoegen {#add-support-for-new-locales}

Voer de volgende stappen uit om ondersteuning voor een nieuwe landinstelling toe te voegen:

1. [Ondersteuning voor lokalisatie toevoegen voor niet-ondersteunde landinstellingen](#add-localization-support-for-non-supported-locales)
1. [Toegevoegde landinstellingen gebruiken in Adaptive Forms](#use-added-locale-in-af)

### Ondersteuning voor lokalisatie toevoegen voor niet-ondersteunde landinstellingen {#add-localization-support-for-non-supported-locales}

AEM Forms ondersteunt momenteel de lokalisatie van Adaptive Forms-inhoud in het Engels (en), Spaans (es), Frans (fr), Italiaans (it), Duits (de), Japans (ja), Portugees-Braziliaans (pt-BR), Chinees (zh-CN), Chinees-Taiwan (zh-TW) en Koreaans (ko-KR).

Ondersteuning voor een nieuwe landinstelling toevoegen bij Adaptive Forms-runtime:

1. [Uw opslagplaats klonen](#clone-the-repository)
1. [Een landinstelling toevoegen aan de GuideLocalizationService-service](#add-a-locale-to-the-guide-localization-service)
1. [Specifieke map voor landnamen toevoegen](#add-locale-name-specific-folder)
1. [Ondersteuning voor landinstellingen toevoegen voor het woordenboek](#add-locale-support-for-the-dictionary)
1. [Leg de wijzigingen in de opslagplaats vast en implementeer de pijpleiding](#commit-changes-in-repo-deploy-pipeline)

#### 1. De opslagplaats klonen {#clone-the-repository}

1. Navigeer vanaf de opdrachtregel naar de locatie waar u de Forms Cloud Service-opslagplaats wilt klonen.
1. Voer het bevel uit dat u [opgehaald uit Cloud Manager.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#accessing-git) Het lijkt op `git clone https://git.cloudmanager.adobe.com/<my-org>/<my-program>/`.
1. Gebruik de gebruikersnaam en het wachtwoord van de it om de repository te klonen.
1. Open de gekloonde opslagmap voor Forms Cloud Service in de voorkeurseditor.

#### 2. Een landinstelling toevoegen aan de Guide Localization-service {#add-a-locale-to-the-guide-localization-service}

1. Zoek de `Guide Localization Service.cfg.json` en voeg de landinstelling toe die u wilt toevoegen aan de lijst met ondersteunde landinstellingen.

   >[!NOTE]
   >
   > Een bestand maken met de naam `Guide Localization Service.cfg.json` bestand, als dit nog niet bestaat.

#### 3. Specifieke mapclientbibliotheek toevoegen aan de naam van een landinstelling {#add-locale-name-specific-folder}

1. Maak in de map UI.content `etc/clientlibs` map.
1. Maak een map met de naam `locale-name` krachtens `etc/clientlibs` om als container voor xfa en af clientlibs te dienen.

##### 3.1 XFA-clientbibliotheek toevoegen voor een landinstelling in de map locale-name

Een knooppunt maken met de naam `[locale-name]_xfa` en type as `cq:ClientLibraryFolder` krachtens `etc/clientlibs/locale_name`, met categorie `xfaforms.I18N.<locale>`en voeg de volgende bestanden toe:

* **I18N.js** definiëren `xfalib.locale.Strings` voor de `<locale>` zoals gedefinieerd in `/etc/clientlibs/fd/xfaforms/I18N/ja/I18N`.
* **js.txt** die het volgende bevatten:
  */libs/fd/xfaforms/clientlibs/I18N/Namespace.js I18N.js /etc/clientlibs/fd/xfaforms/I18N/LogMessages.js*

##### 3.2. Adaptief formulier-clientbibliotheek toevoegen voor een landinstellingsnaammap

1. Een knooppunt maken met de naam `[locale-name]_af` en type as `cq:ClientLibraryFolder` krachtens `etc/clientlibs/locale_name`, met categorie als `guides.I18N.<locale>` en afhankelijkheden als `xfaforms.3rdparty`, `xfaforms.I18N.<locale>` en `guide.common`.
1. Een map maken met de naam `javascript` en voeg de volgende bestanden toe:

   * **i18n.js** definiëren `guidelib.i18n`met patronen van &quot;agendaSymbolen&quot;, `datePatterns`, `timePatterns`, `dateTimeSymbols`, `numberPatterns`, `numberSymbols`, `currencySymbols`, `typefaces` voor de `<locale>` volgens de XFA-specificaties die worden beschreven in [Locale Set Specification](https://helpx.adobe.com/content/dam/Adobe/specs/xfa_spec_3_3.pdf).
   * **LogMessages.js** definiëren `guidelib.i18n.strings` en `guidelib.i18n.LogMessages` voor de `<locale>` zoals gedefinieerd in `/etc/clientlibs/fd/af/I18N/fr/javascript/LogMessages.js`.

1. Toevoegen **js.txt** die het volgende bevatten:

   ```
     i18n.js
     LogMessages.js
   ```

#### 4. Ondersteuning voor landinstellingen toevoegen voor het woordenboek {#add-locale-support-for-the-dictionary}

Voer deze stap alleen uit als de `<locale>` u toevoegt behoort niet tot `en`, `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja`, `ko-kr`.

1. Een map maken `languages` krachtens `etc`, indien niet aanwezig.

1. Een multi-getaxeerde tekenreekseigenschap toevoegen `languages` aan de knoop, als niet reeds aanwezig.
1. Voeg de `<locale-name>` standaardwaarden voor landinstellingen `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja`, `ko-kr`, indien niet aanwezig.

1. Voeg de `<locale>` op de waarden van de `languages` eigenschap van `/etc/languages`.
1. Voeg de nieuwe mappen toe aan het dialoogvenster `filter.xml` onder etc/META-INF/[maphiërarchie] als:

   ```
   <filter root="/etc/clientlibs/[locale-name]"/>
   <filter root="/etc/languages"/>
   ```

Voordat u de wijzigingen doorvoert in de AEM Git-opslagplaats, hebt u toegang nodig tot uw [Gegevens opslagplaats ophalen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=en#accessing-git).

#### 5. Leg de wijzigingen in de opslagplaats vast en implementeer de pijpleiding {#commit-changes-in-repo-deploy-pipeline}

Leg de wijzigingen vast in de GIT-opslagplaats nadat u een nieuwe ondersteuning voor landinstellingen hebt toegevoegd. Implementeer uw code met de volledige stackpijplijn. Meer informatie [hoe een pijpleiding op te zetten](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=en#setup-pipeline) om nieuwe ondersteuning voor landinstellingen toe te voegen.
Zodra de pijpleiding volledig is, verschijnt de onlangs toegevoegde scène in het AEM milieu.

### Toegevoegde landinstelling gebruiken in Adaptive Forms {#use-added-locale-in-af}

Voer de volgende stappen uit om een adaptief formulier te gebruiken en weer te geven met behulp van een nieuw toegevoegde landinstelling:

1. Meld u aan bij de AEM auteur.
1. Ga naar **Forms** >  **Forms en Documenten**.
1. Selecteer een adaptief formulier en klik op **Woordenboek toevoegen** en **Woordenboek toevoegen aan vertaalproject** wordt weergegeven.
1. Geef de **Projecttitel** en selecteert u de **Doeltalen** in het keuzemenu in het dialoogvenster **Woordenboek toevoegen aan vertaalproject** wizard.
1. Klikken **Gereed** en voert het gemaakte vertaalproject uit.
1. Selecteer een adaptief formulier en klik op **Voorvertonen als HTML**.
1. Toevoegen `&afAcceptLang=<locale-name>` in de URL van een adaptief formulier.
1. De pagina vernieuwen en het adaptieve formulier wordt weergegeven in een opgegeven landinstelling.

Er zijn twee methoden om de landinstelling van een adaptief formulier te bepalen. Wanneer een adaptief formulier wordt weergegeven, geeft dit de aangevraagde landinstelling aan met:

* De `[local]` in het aangepaste formulier-URL. De opmaak van de URL is `http://host:[port]/content/forms/af/[afName].[locale].html?wcmmode=disabled`. Gebruiken `[local]` kunt u een adaptief formulier in cache plaatsen.

* De volgende parameters in de vermelde volgorde ophalen:

   * Request-parameter `afAcceptLang`
Als u de browserlandinstelling van gebruikers wilt overschrijven, kunt u het `afAcceptLang` request parameter to force the locale. Met de volgende URL wordt bijvoorbeeld gedwongen het formulier te genereren in de landinstelling Canadees-Frans:
     `https://'[server]:[port]'/<contextPath>/<formFolder>/<formName>.html?wcmmode=disabled&afAcceptLang=ca-fr`

   * De landinstelling van de browser die voor de gebruiker is ingesteld. Deze landinstelling wordt in de aanvraag opgegeven met de functie `Accept-Language` header.

Als er geen clientbibliotheek voor de aangevraagde landinstelling bestaat, wordt in de bibliotheek gecontroleerd of er taalcode in de landinstelling aanwezig is. Als de aangevraagde landinstelling bijvoorbeeld `en_ZA` (Zuid-Afrikaans Engels) en de clientbibliotheek voor `en_ZA` niet bestaat, gebruikt het adaptieve formulier de clientbibliotheek voor `en` (Engels) taal, als deze bestaat. Als er echter geen van deze profielen bestaat, wordt in het adaptieve formulier het woordenboek gebruikt voor `en` landinstelling.


Nadat de landinstelling is geïdentificeerd, wordt in het adaptieve formulier het formulierspecifieke woordenboek gekozen. Als het formulierspecifieke woordenboek voor de aangevraagde landinstelling niet wordt gevonden, wordt het woordenboek gebruikt voor de taal waarin het adaptieve formulier is geschreven.

Als er geen landinstellingsgegevens aanwezig zijn, wordt het adaptieve formulier geleverd in de oorspronkelijke taal van het formulier. De oorspronkelijke taal is de taal die wordt gebruikt bij het ontwikkelen van het adaptieve formulier.

Get [voorbeeldclientbibliotheek](/help/forms/assets/locale-support-sample.zip) om ondersteuning voor nieuwe landinstellingen toe te voegen. U moet de inhoud van de map wijzigen in de vereiste landinstelling.

## Aanbevolen procedures voor ondersteuning van nieuwe lokalisatie {#best-practices}

* Adobe raadt u aan een vertaalproject te maken nadat u een adaptief formulier hebt gemaakt.

* Wanneer nieuwe velden worden toegevoegd aan een bestaand adaptief formulier:
   * **Voor machinevertaling**: Maak het woordenboek opnieuw en voer het vertaalproject uit. Velden die na het maken van een vertaalproject aan een adaptief formulier zijn toegevoegd, blijven onvertaald.
   * **Voor menselijke vertaling**: Het woordenboek exporteren door `[server:port]/libs/cq/i18n/gui/translator.html`. Werk het woordenboek voor de zojuist toegevoegde velden bij en upload het.
