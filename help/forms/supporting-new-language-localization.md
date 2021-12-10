---
title: Ondersteuning voor nieuwe landinstellingen voor Adaptive Forms-lokalisatie
seo-title: Supporting new locales for Adaptive Forms localization
description: Met AEM Forms kunt u nieuwe landinstellingen toevoegen voor het lokaliseren van Adaptive Forms. De landinstellingen die standaard worden ondersteund, zijn Engels, Frans, Duits en Japans.
seo-description: AEM Forms allows you to add new locales for localizing Adaptive Forms. The supported locales by default are English, French, German, and Japanese.
uuid: 7f9fab6b-8d93-46bb-8c7c-7b723d5159ea
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
discoiquuid: d4e2acb0-8d53-4749-9d84-15b8136e610b
docset: aem65
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '781'
ht-degree: 0%

---


# Ondersteuning voor nieuwe landinstellingen voor Adaptive Forms-lokalisatie{#supporting-new-locales-for-adaptive-forms-localization}

## Over woordenboeken voor landinstellingen {#about-locale-dictionaries}

De lokalisatie van Adaptive Forms is gebaseerd op twee typen woordenboeken voor landinstellingen:

**Formulierspecifiek woordenboek** Bevat tekenreeksen die worden gebruikt in Adaptive Forms. Bijvoorbeeld labels, veldnamen, foutberichten, Help-beschrijvingen enzovoort. Het wordt beheerd als een set XLIFF-bestanden voor elke landinstelling en u kunt het bestand openen op `https://<host>:<port>/libs/cq/i18n/translator.html`.

**Algemene woordenboeken** Er zijn twee algemene woordenboeken, beheerd als JSON-objecten, in AEM clientbibliotheek. Deze woordenboeken bevatten standaardfoutberichten, naam van de maand, valutasymbolen, datum- en tijdpatronen, enzovoort. U vindt deze woordenboeken in CRXDe Lite op /libs/fd/xfaforms/clientlibs/I18N. Deze locaties bevatten afzonderlijke mappen voor elke landinstelling. Omdat algemene woordenboeken meestal niet regelmatig worden bijgewerkt, kunnen browsers door afzonderlijke JavaScript-bestanden voor elke landinstelling te behouden deze in cache plaatsen en het gebruik van netwerkbandbreedte verminderen wanneer ze toegang krijgen tot verschillende Adaptive Forms op dezelfde server.

### Hoe lokalisatie van adaptief formulier werkt {#how-localization-of-adaptive-form-works}

Er zijn twee methoden om de landinstelling van het adaptieve formulier te identificeren. Wanneer een adaptief formulier wordt gegenereerd, geeft dit de aangevraagde landinstelling aan met:

* het bekijken van `[local]` in de URL van het adaptieve formulier. De opmaak van de URL is `http://host:port/content/forms/af/[afName].[locale].html?wcmmode=disabled`. Gebruiken `[local]` kunt u een adaptief formulier in cache plaatsen.

* de volgende parameters in de opgegeven volgorde bekijken:

   * Request-parameter `afAcceptLang`
Als u de browserlandinstelling van gebruikers wilt overschrijven, kunt u het 
`afAcceptLang` request parameter to force the locale. Met de volgende URL wordt het formulier bijvoorbeeld geforceerd weergegeven in de Japanse landinstelling:
      `https://'[server]:[port]'/<contextPath>/<formFolder>/<formName>.html?wcmmode=disabled&afAcceptLang=ja`

   * De landinstelling van de browser die voor de gebruiker is ingesteld. Deze landinstelling wordt in de aanvraag opgegeven met de functie `Accept-Language` header.

   * Taalinstelling van de gebruiker opgegeven in AEM.

   * Landinstelling browser is standaard ingeschakeld. Als u de landinstelling van de browser wilt wijzigen,
      * Open configuratiebeheer. De URL is `http://[server]:[port]/system/console/configMgr`
      * Zoek en open de **[!UICONTROL Adaptive Form and Interactive Communication Web Channel]** configuratie.
      * Status van de **[!UICONTROL Use Browser Locale]** en  **[!UICONTROL Save]** de configuratie.

Zodra de landinstelling is geïdentificeerd, kiest de Adaptive Forms het formulierspecifieke woordenboek. Als het formulierspecifieke woordenboek voor de aangevraagde landinstelling niet wordt gevonden, wordt het woordenboek gebruikt voor de taal waarin het adaptieve formulier is gemaakt.

Als er geen landinstellingsgegevens aanwezig zijn, wordt het adaptieve formulier geleverd in de oorspronkelijke taal van het formulier. De oorspronkelijke taal is de taal die wordt gebruikt bij het ontwikkelen van het adaptieve formulier.

Als er geen clientbibliotheek voor de aangevraagde landinstelling bestaat, wordt in de bibliotheek gecontroleerd of er taalcode aanwezig is in de landinstelling. Als de aangevraagde landinstelling bijvoorbeeld `en_ZA` (Zuid-Afrikaans Engels) en de clientbibliotheek voor `en_ZA` bestaat niet. Het Adaptief formulier gebruikt de clientbibliotheek voor `en` (Engels) taal, als deze bestaat. Als er echter geen van deze profielen bestaat, wordt in het adaptieve formulier het woordenboek gebruikt voor `en` landinstelling.

## Ondersteuning voor lokalisatie toevoegen voor niet-ondersteunde landinstellingen {#add-localization-support-for-non-supported-locales}

[!DNL AEM Forms] biedt momenteel ondersteuning voor de lokalisatie van Adaptive Forms-inhoud in het Engels (en), Spaans (es), Frans (fr), Italiaans (it), Duits (de), Japans (ja), Portugees-Braziliaans (pt-BR), Chinees (zh-CN), Chinees-Taiwan (zh-TW) en Koreaans (ko-KR).

Ondersteuning voor een nieuwe landinstelling toevoegen bij Adaptive Forms-runtime:

1. [Een landinstelling toevoegen aan de GuideLocalizationService-service](supporting-new-language-localization.md#p-add-a-locale-to-the-guide-localization-service-br-p)

1. [XFA-clientbibliotheek toevoegen voor een landinstelling](supporting-new-language-localization.md#p-add-xfa-client-library-for-a-locale-br-p)

1. [Aangepaste formulierclientbibliotheek toevoegen voor een landinstelling](supporting-new-language-localization.md#p-add-adaptive-form-client-library-for-a-locale-br-p)
1. [Ondersteuning voor landinstellingen toevoegen voor het woordenboek](supporting-new-language-localization.md#p-add-locale-support-for-the-dictionary-br-p)
1. [De server opnieuw starten](supporting-new-language-localization.md#p-restart-the-server-p)

### Een landinstelling toevoegen aan de Guide Localization-service {#add-a-locale-to-the-guide-localization-service-br}

1. Ga naar `https://'[server]:[port]'/system/console/configMgr`.
1. Klik om de **Guide Localization Service** component.
1. Voeg de landinstelling toe die u wilt toevoegen aan de lijst met ondersteunde landinstellingen.

![GuideLocalizationService](assets/configservice.png)

### XFA-clientbibliotheek toevoegen voor een landinstelling {#add-xfa-client-library-for-a-locale-br}

Een knooppunt van het type maken `cq:ClientLibraryFolder` krachtens `etc/<folderHierarchy>`, met categorie `xfaforms.I18N.<locale>`en voeg de volgende bestanden toe aan de clientbibliotheek:

* **I18N.js** definiëren `xfalib.locale.Strings` voor de `<locale>` zoals gedefinieerd in `/etc/clientlibs/fd/xfaforms/I18N/ja/I18N`.

* **js.txt** die het volgende bevatten:

```text
/libs/fd/xfaforms/clientlibs/I18N/Namespace.js
I18N.js
/etc/clientlibs/fd/xfaforms/I18N/LogMessages.js
```

### Aangepaste formulierclientbibliotheek toevoegen voor een landinstelling {#add-adaptive-form-client-library-for-a-locale-br}

Een knooppunt van het type maken `cq:ClientLibraryFolder` krachtens `etc/<folderHierarchy>`, met categorie als `guides.I18N.<locale>` en afhankelijkheden als `xfaforms.3rdparty`, `xfaforms.I18N.<locale>` en `guide.common`. &quot;

Voeg de volgende bestanden toe aan de clientbibliotheek:

* **i18n.js** definiëren `guidelib.i18n`met patronen van &quot;agendaSymbolen&quot;, `datePatterns`, `timePatterns`, `dateTimeSymbols`, `numberPatterns`, `numberSymbols`, `currencySymbols`, `typefaces` voor de `<locale>` volgens de XFA-specificaties die worden beschreven in [Locale Set Specification](https://helpx.adobe.com/content/dam/Adobe/specs/xfa_spec_3_3.pdf). U kunt ook zien hoe de definitie voor andere ondersteunde landinstellingen is vastgelegd in `/etc/clientlibs/fd/af/I18N/fr/javascript/i18n.js`.
* **LogMessages.js** definiëren `guidelib.i18n.strings` en `guidelib.i18n.LogMessages` voor de `<locale>` zoals gedefinieerd in `/etc/clientlibs/fd/af/I18N/fr/javascript/LogMessages.js`.
* **js.txt** die het volgende bevatten:

```text
i18n.js
LogMessages.js
```

### Ondersteuning voor landinstellingen toevoegen voor het woordenboek {#add-locale-support-for-the-dictionary-br}

Voer deze stap alleen uit als de `<locale>` u toevoegt behoort niet tot `en`, `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja`, `ko-kr`.

1. Een `nt:unstructured` node `languages` krachtens `etc`, indien niet aanwezig.

1. Een multi-getaxeerde tekenreekseigenschap toevoegen `languages` aan de knoop, als niet reeds aanwezig.
1. Voeg de `<locale>` standaardwaarden voor landinstellingen `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja`, `ko-kr`, indien niet aanwezig.

1. Voeg de `<locale>` op de waarden van de `languages` eigenschap van `/etc/languages`.

De `<locale>` wordt weergegeven op `https://'[server]:[port]'/libs/cq/i18n/translator.html`.

### De server opnieuw starten {#restart-the-server}

Start de AEM server opnieuw om de toegevoegde landinstelling te activeren.

## Voorbeeldbibliotheken voor het toevoegen van ondersteuning voor Spaans {#sample-libraries-for-adding-support-for-spanish}

Voorbeeld van clientbibliotheken voor het toevoegen van ondersteuning voor Spaans

[Bestand ophalen](assets/sample.zip)
