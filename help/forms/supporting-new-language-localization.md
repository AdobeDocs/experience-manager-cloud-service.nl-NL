---
title: Hoe voeg ik steun voor nieuwe scènes aan een Aangepast Vorm toe dat op de Componenten van de Stichting wordt gebaseerd?
description: Voor Adaptief Forms kunt u naast de landinstellingen uit het tekstvak ook landinstellingen voor meer talen toevoegen.
feature: Adaptive Forms, Foundation Components
exl-id: 4c7d6caa-1adb-4663-933f-b09129b9baef
role: User, Developer
source-git-commit: b5340c23f0a2496f0528530bdd072871f0d70d62
workflow-type: tm+mt
source-wordcount: '1220'
ht-degree: 0%

---

# Ondersteuning voor nieuwe landinstellingen voor Adaptive Forms-lokalisatie {#supporting-new-locales-for-adaptive-forms-localization}

>[!NOTE]
>
> De Adobe adviseert het gebruiken van de moderne en verlengbare gegevens vangt [ Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) voor [ het creëren van nieuwe Aangepaste Forms ](/help/forms/creating-adaptive-form-core-components.md) of [ het toevoegen van Aangepaste Forms aan de pagina&#39;s van AEM Sites ](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten.


| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/manage-administer-aem-forms/supporting-new-language-localization.html) |
| Kernonderdelen | [ klik hier ](supporting-new-language-localization-core-components.md) |
| Elementaire componenten | Dit artikel |

AEM Forms biedt in de box-ondersteuning voor de landinstellingen Engels (en), Spaans (es), Frans (fr), Italiaans (it), Duits (de), Japans (ja), Portugees-Braziliaans (pt-BR), Chinees (zh-CN), Chinees-Taiwan (zh-TW) en Koreaans (ko-KR). U kunt ook ondersteuning toevoegen voor meer landinstellingen, zoals Hindi(hi_IN).

## Werken met taalwoordenboeken {#about-locale-dictionaries}

De lokalisatie van adaptieve formulieren is afhankelijk van twee typen taalwoordenboeken:

* **vorm-specifiek woordenboek** bevat koorden die in adaptieve vormen worden gebruikt. Bijvoorbeeld labels, veldnamen, foutberichten en Help-beschrijvingen. Het wordt beheerd als een set XLIFF-bestanden voor elke landinstelling en u hebt toegang tot dit bestand via `[author-instance]/libs/cq/i18n/gui/translator.html` .

* **Globale woordenboeken** Er zijn twee globale woordenboeken, die als voorwerpen JSON, in de AEM cliëntbibliotheek worden beheerd. Deze woordenboeken bevatten standaardfoutberichten, naam van de maand, valutasymbolen, datum- en tijdpatronen, enzovoort. U vindt deze woordenboeken op `[author-instance]/libs/fd/xfaforms/clientlibs/I18N` . Deze locaties bevatten afzonderlijke mappen voor elke landinstelling. Omdat algemene woordenboeken niet vaak worden bijgewerkt, kunnen browsers door afzonderlijke JavaScript-bestanden voor elke landinstelling in cache te houden en het gebruik van de netwerkbandbreedte verminderen wanneer ze verschillende adaptieve formulieren op dezelfde server gebruiken.

## Ondersteuning voor nieuwe landinstellingen toevoegen {#add-support-for-new-locales}

Voer de volgende stappen uit om ondersteuning voor een nieuwe landinstelling toe te voegen:

1. [Ondersteuning voor lokalisatie toevoegen voor niet-ondersteunde landinstellingen](#add-localization-support-for-non-supported-locales)
1. [Toegevoegde landinstellingen gebruiken in Adaptive Forms](#use-added-locale-in-af)

### Ondersteuning voor lokalisatie toevoegen voor niet-ondersteunde landinstellingen {#add-localization-support-for-non-supported-locales}

AEM Forms ondersteunt momenteel de lokalisatie van Adaptive Forms-inhoud in het Engels (en), Spaans (es), Frans (fr), Italiaans (it), Duits (de), Japans (ja), Portugees-Braziliaans (pt-BR), Chinees (zh-CN), Chinees-Taiwan (zh-TW) en Koreaans (ko-KR).

Ondersteuning voor een nieuwe landinstelling toevoegen in de Adaptive Forms-runtime:

1. [Uw gegevensopslagruimte klonen](#clone-the-repository)
1. [Een landinstelling toevoegen aan de GuideLocalizationService-service](#add-a-locale-to-the-guide-localization-service)
1. [Specifieke map voor landnamen toevoegen](#add-locale-name-specific-folder)
1. [Ondersteuning voor landinstellingen toevoegen voor het woordenboek](#add-locale-support-for-the-dictionary)
1. [Leg de wijzigingen in de opslagplaats vast en implementeer de pijpleiding](#commit-changes-in-repo-deploy-pipeline)

#### 1. Kloont de repository {#clone-the-repository}

1. Navigeer vanaf de opdrachtregel naar de locatie waar u de Forms Cloud Service-opslagplaats wilt klonen.
1. Voer het bevel uit dat u [ van Cloud Manager wordt teruggewonnen.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#accessing-git) Deze lijkt op `git clone https://git.cloudmanager.adobe.com/<my-org>/<my-program>/` .
1. Gebruik de gebruikersnaam en het wachtwoord van de it om de repository te klonen.
1. Open de gekloonde opslagmap voor Forms Cloud Service in de voorkeurseditor.

#### 2. Voeg een landinstelling toe aan de Guide Localization-service {#add-a-locale-to-the-guide-localization-service}

1. Zoek het `Guide Localization Service.cfg.json` -bestand en voeg de landinstelling toe die u wilt toevoegen aan de lijst met ondersteunde landinstellingen.

   >[!NOTE]
   >
   > Maak een bestand met de naam `Guide Localization Service.cfg.json` als dat nog niet het geval is.

#### 3. Voeg een locale-name specifieke mapclientbibliotheek toe {#add-locale-name-specific-folder}

1. Maak `etc/clientlibs` -map in de map UI.content.
1. Maak verder een map met de naam `locale-name` under `etc/clientlibs` als container voor xfa- en af-clientlibs.

##### 3.1 XFA-clientbibliotheek toevoegen voor een landinstelling in een map met landnamen

Maak een knooppunt met de naam `[locale-name]_xfa` en typ `cq:ClientLibraryFolder` onder `etc/clientlibs/locale_name` , met categorie `xfaforms.I18N.<locale>` , en voeg de volgende bestanden toe:

* **I18N.js** bepalend `xfalib.locale.Strings` voor `<locale>` zoals bepaald in `/etc/clientlibs/fd/xfaforms/I18N/ja/I18N`.
* **js.txt** die het volgende bevatten:
  */libs/fd/xfaforms/clientlibs/I18N/Namespace.js
I18N.js
/etc/clientlibs/fd/xfaforms/I18N/LogMessages.js*

##### 3.2. Voeg een adaptieve clientbibliotheek van het formulier toe voor een landinstellingsnaammap

1. Maak een knooppunt met de naam `[locale-name]_af` en typ als `cq:ClientLibraryFolder` onder `etc/clientlibs/locale_name` , met categorie als `guides.I18N.<locale>` en afhankelijkheden als `xfaforms.3rdparty` , `xfaforms.I18N.<locale>` en `guide.common` .
1. Maak een map met de naam `javascript` en voeg de volgende bestanden toe:

   * **i18n.js** het bepalen `guidelib.i18n`, die patronen van &quot;agendaSymbols&quot;hebben, `datePatterns`, `timePatterns`, `dateTimeSymbols`, `numberPatterns`, `numberSymbols`, `currencySymbols`, `typefaces` voor `<locale>` volgens de XFA specificaties in [ Vastgestelde Specificatie van de Landinstelling ](https://helpx.adobe.com/content/dam/Adobe/specs/xfa_spec_3_3.pdf) worden beschreven.
   * **LogMessages.js** definiërend `guidelib.i18n.strings` en `guidelib.i18n.LogMessages` voor `<locale>` zoals die in `/etc/clientlibs/fd/af/I18N/fr/javascript/LogMessages.js` wordt bepaald.

1. Voeg **js.txt** toe die het volgende bevatten:

   ```
     i18n.js
     LogMessages.js
   ```

#### 4. Ondersteuning voor landinstellingen toevoegen voor het woordenboek {#add-locale-support-for-the-dictionary}

Voer deze stap alleen uit als de `<locale>` die u toevoegt, niet behoort tot `en` , `de` , `es` , `fr` , `it` , `pt-br` , `zh-cn` , `zh-tw` , `ja` , `ko-kr` .

1. Maak een map `languages` onder `etc` als deze nog niet aanwezig is.

1. Voeg een multi-getaxeerde koordbezit `languages` aan de knoop toe, als niet reeds aanwezig.
1. Voeg de `<locale-name>` standaardwaarden voor de landinstelling `de` , `es` , `fr` , `it` , `pt-br` , `zh-cn` , `zh-tw` , `ja` en `ko-kr` toe als deze nog niet aanwezig zijn.

1. Voeg de waarde `<locale>` toe aan de waarden van de eigenschap `languages` van `/etc/languages` .
1. Voeg de gecreeerde omslagen in `filter.xml` onder etc/META-INF/[ omslaghiërarchie ] toe als:

   ```
   <filter root="/etc/clientlibs/[locale-name]"/>
   <filter root="/etc/languages"/>
   ```

Alvorens de veranderingen in de AEM bewaarplaats van het Git vast te leggen, moet u tot uw [ informatie van de bewaarplaats van de Git toegang hebben ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=en#accessing-git).

#### 5. Leg de wijzigingen in de opslagplaats vast en implementeer de pijpleiding {#commit-changes-in-repo-deploy-pipeline}

Leg de wijzigingen vast in de GIT-opslagplaats nadat u een ondersteuning voor landinstellingen hebt toegevoegd. Implementeer uw code met de volledige stackpijplijn. Leer [ hoe te opstelling een pijpleiding ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=en#setup-pipeline) om nieuwe scènesteun toe te voegen.
Zodra de pijpleiding volledig is, verschijnt de onlangs toegevoegde scène in het AEM milieu.

### Toegevoegde landinstelling gebruiken in Adaptive Forms {#use-added-locale-in-af}

Voer de volgende stappen uit om een adaptief formulier te gebruiken en weer te geven met de nieuwe landinstelling:

1. Meld u aan bij de AEM auteur.
1. Ga naar **Forms** > **Forms en Documenten**.
1. Selecteer een AanpassingsVorm en klik **toevoegen Woordenboek** en **voeg Woordenboek aan de tovenaar van het Project van de Vertaling** verschijnt.
1. Specificeer de **Titel van het Project** en selecteer de **Talen van het Doel** van het drop-down menu in **Woordenboek aan de tovenaar van het Project van de Vertaling** toevoegen.
1. Klik **Gedaan** en voer het gecreeerde vertaalproject uit.
1. Selecteer een AanpassingsVorm en klik **Voorproef als HTML**.
1. Voeg `&afAcceptLang=<locale-name>` toe aan de URL van een adaptief formulier.
1. De pagina vernieuwen en het adaptieve formulier wordt weergegeven in een opgegeven landinstelling.

Er zijn twee methoden om de landinstelling van een adaptief formulier te bepalen. Wanneer een adaptief formulier wordt weergegeven, geeft dit de aangevraagde landinstelling aan met:

* De kiezer van `[local]` ophalen in het aangepaste formulier-URL. De opmaak van de URL is `http://host:[port]/content/forms/af/[afName].[locale].html?wcmmode=disabled` . Met `[local]` -kiezer kunt u een adaptief formulier in cache plaatsen.

* De volgende parameters in de vermelde volgorde ophalen:

   * Request-parameter `afAcceptLang`
Als u de landinstelling van de browser van gebruikers wilt overschrijven, kunt u de `afAcceptLang` request-parameter doorgeven om de landinstelling te forceren. Met de volgende URL wordt bijvoorbeeld gedwongen het formulier te genereren in de landinstelling Canadees-Frans:
     `https://'[server]:[port]'/<contextPath>/<formFolder>/<formName>.html?wcmmode=disabled&afAcceptLang=ca-fr`

   * De landinstelling van de browser die voor de gebruiker is ingesteld en die in de aanvraag wordt opgegeven met de header `Accept-Language` .

Als er geen clientbibliotheek voor de aangevraagde landinstelling bestaat, wordt in de bibliotheek gecontroleerd of er taalcode in de landinstelling aanwezig is. Als de aangevraagde landinstelling bijvoorbeeld `en_ZA` (Zuid-Afrikaans Engels) is en de clientbibliotheek voor `en_ZA` niet bestaat, gebruikt het adaptieve formulier de clientbibliotheek voor `en` -taal (Engels), als deze bestaat. Als er echter geen van deze functies bestaat, gebruikt het adaptieve formulier het woordenboek voor de landinstelling `en` .


Nadat de landinstelling is geïdentificeerd, wordt in het adaptieve formulier het formulierspecifieke woordenboek gekozen. Als het formulierspecifieke woordenboek voor de aangevraagde landinstelling niet wordt gevonden, wordt het woordenboek gebruikt voor de taal waarin het adaptieve formulier is geschreven.

Als er geen landinstellingsgegevens aanwezig zijn, wordt het adaptieve formulier geleverd in de oorspronkelijke taal van het formulier. De oorspronkelijke taal is de taal die wordt gebruikt bij het ontwikkelen van het adaptieve formulier.

Krijg de bibliotheek van de a [ steekproefcliënt ](/help/forms/assets/locale-support-sample.zip) om steun voor nieuwe scène toe te voegen. U moet de inhoud van de map wijzigen in de vereiste landinstelling.

## Aanbevolen procedures voor ondersteuning van nieuwe lokalisatie {#best-practices}

* Adobe raadt u aan een vertaalproject te maken nadat u een adaptief formulier hebt gemaakt.

* Wanneer nieuwe velden worden toegevoegd aan een bestaand adaptief formulier:
   * **voor machinevertaling**: creeer het woordenboek opnieuw en stel het vertaalproject in werking. Velden die na het maken van een vertaalproject aan een adaptief formulier zijn toegevoegd, blijven onvertaald.
   * **voor menselijke vertaling**: Exporteer het woordenboek door `[server:port]/libs/cq/i18n/gui/translator.html`. Werk het woordenboek voor de zojuist toegevoegde velden bij en upload het.


## Zie ook {#see-also}

{{see-also}}