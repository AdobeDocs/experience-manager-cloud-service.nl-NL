---
title: Hoe kan ik ondersteuning voor nieuwe landinstellingen toevoegen aan een adaptief formulier op basis van kerncomponenten?
description: Leer nieuwe landinstellingen toe te voegen voor een adaptief formulier.
feature: Adaptive Forms, Core Components
Role: Developer, Author
exl-id: bc06542b-84c8-4c6a-a305-effbd16d5630
role: User, Developer
source-git-commit: 8f39bffd07e3b4e88bfa200fec51572e952ac837
workflow-type: tm+mt
source-wordcount: '2154'
ht-degree: 0%

---

# Een landinstelling toevoegen voor Adaptive Forms op basis van Core Components {#supporting-new-locales-for-adaptive-forms-localization}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| Elementaire componenten | [&#x200B; klik hier &#x200B;](supporting-new-language-localization.md) |
| Kernonderdelen | Dit artikel |

<span class="preview"> De ondersteuning voor talen die van rechts naar links worden geschreven, is beschikbaar in het programma voor vroege adopties. U kunt vanaf uw officiële e-mailadres naar aem-forms-ea@adobe.com schrijven om deel te nemen aan het programma voor vroege adoptie en toegang tot de functie te vragen. </span>

AEM Forms biedt in de box-ondersteuning voor de landinstellingen Engels (en), Spaans (es), Frans (fr), Italiaans (it), Duits (de), Japans (ja), Portugees-Braziliaans (pt-BR), Chinees (zh-CN), Chinees-Taiwan (zh-TW) en Koreaans (ko-KR). U kunt ook ondersteuning toevoegen voor meer landinstellingen, zoals Hindi(hi_IN). U kunt Adaptief Forms ook weergeven in een RTL-taal (rechts naar links), zoals Arabisch, Perzisch en Urdu, door deze landinstellingen toe te voegen.

>[!VIDEO](https://video.tv.adobe.com/v/3433132/adaptive-forms-rtl--arabic-hebrew-farsi)

## Toepassings- en gebruiksgevallen

### Verzekeringen

## Steunt AEM Forms meertalige zaken voor verzekeringsgebruik?

Ja. AEM Forms ondersteunt meertalige formulierervaringen, wat belangrijk is voor verzekeraars die in verschillende regio&#39;s en talen werken.

## Hoe bepaalt AEM Forms de landinstelling voor een adaptief formulier?

Kennis van de manier waarop AEM Forms de landinstelling selecteert voor het weergeven van een adaptief formulier is van cruciaal belang voor een correcte lokalisatie. Hier volgt een uitsplitsing van het selectieproces:

### Landinstelling selecteren op basis van prioriteit

AEM Forms geeft prioriteit aan de volgende methoden om de landinstelling voor een adaptief formulier te bepalen:

1. **URL de Kiezer van de Plaats ([ scène ])**:

   Het systeem geeft voorrang aan de scène binnen URL wordt gespecificeerd gebruikend de [ scène ] selecteur die. Met deze indeling kan caching worden gebruikt voor betere prestaties.

   Formaat: URL volgt dit formaat: http:/[ de Server URL van AEM Forms ]/content/forms/af/[ afName ].[ scène ].html?wcmmode=disabled.

   Voorbeeld: https://[ server ] /content/forms/af/contact-us.hi.html geeft de vorm in Hindi terug.


1. **afAcceptLang de Parameter van het Verzoek**:

   Als u de landinstelling van de browser van de gebruiker wilt overschrijven, gebruikt u de parameter `afAcceptLang` in de URL.

   Voorbeeld: https://[ server ] /forms/af/survey.ca-fr.html?afAcceptLang=ca-fr dwingt de vorm om in het Canadese Frans terug te geven.

1. **Browser van de Gebruiker Scène (Accept-Taal Kopbal)**:

   Als er geen andere landinstelling is opgegeven, neemt AEM Forms de landinstelling van de browser van de gebruiker in overweging die met de header `Accept-Language` is verzonden.


### Terugvalmechanisme:


* Als een clientbibliotheek (proces voor het toevoegen van een nieuwe landinstelling, zoals verderop in dit document wordt uitgelegd) voor de aangevraagde landinstelling niet beschikbaar is, zoekt AEM Forms naar een bibliotheek op basis van de taalcode in de landinstelling.

  Voorbeeld: als en_ZA (Zuid-Afrikaans Engels) wordt aangevraagd en er geen en_ZA-bibliotheek is, wordt en (Engels) gebruikt, indien beschikbaar.

  Als er geen geschikte clientbibliotheek wordt gevonden, wordt het standaardwoordenboek (meestal `en` ) voor de ontwerptaal van het formulier gebruikt.

  Als er geen landinstellingsgegevens beschikbaar zijn, wordt het Adaptief formulier weergegeven in de oorspronkelijke taal die tijdens de ontwikkeling is gebruikt.


## Voorwaarden voor het toevoegen van een landinstelling

Voordat u een nieuwe landinstelling gaat toevoegen voor uw Adaptive Forms, moet u het volgende doen:

**Software:**

* De gewone Redacteur van de Tekst (winde): Terwijl om het even welke gewone tekstredacteur kan werken, biedt een Geïntegreerde Milieu van de Ontwikkeling (winde) zoals [&#x200B; de Code van Microsoft Visual Studio van 0&rbrace; geavanceerde eigenschappen voor het gemakkelijker uitgeven aan.](https://code.visualstudio.com/download)

* Git: Dit versiebeheersysteem is vereist voor het beheren van codewijzigingen. Als u het geïnstalleerd niet hebt, download het van [&#x200B; https://git-scm.com &#x200B;](https://git-scm.com).


**Bewaarplaats van de Code:**

Clone the Adaptive Forms Core Components Repository: U hebt een clientbibliotheek van deze opslagplaats nodig om een landinstelling toe te voegen. De gegevensopslagruimte klonen:

1. Open de opdrachtregel of het terminalvenster.

1. Navigeer naar de gewenste locatie op uw computer waar u de opslagplaats wilt opslaan (bijvoorbeeld /adaptive-forms-core-components).

1. Voer de volgende opdracht uit om de gegevensopslagruimte te klonen:

   ```
   git clone https://github.com/adobe/aem-core-forms-components.git
   ```

   Met deze opdracht downloadt u de opslagplaats en maakt u een map met de naam `aem-core-forms-components` op uw computer. In deze handleiding wordt deze map de `[Adaptive Forms Core Components repository]` genoemd.


## Een landinstelling toevoegen {#add-localization-support-for-non-supported-locales}

Ga als volgt te werk om ondersteuning voor nieuwe landinstellingen toe te voegen aan een adaptief formulier op basis van kerncomponenten:

### De AEM as a Cloud Service Git-gegevensopslagruimte klonen

1. Open de opdrachtregel en kies een map waarin u de AEM as a Cloud Service-opslagplaats wilt opslaan, bijvoorbeeld `/cloud-service-repository/` .

1. Voer de onderstaande opdracht uit om de gegevensopslagruimte te klonen:

   ```SHELL
   git clone https://git.cloudmanager.adobe.com/<organization-name>/<program id>/
   ```

   U hebt enkele informatie nodig om uw Git-opslagplaats te klonen:

   * **naam van de Organisatie**: Dit identificeert uw team of project binnen Adobe Experience Manager as a Cloud Service (AEM as a Cloud Service).

   * **identiteitskaart van het Programma**: Dit specificeert het programma verbonden aan uw bewaarplaats.

   * **Geloofsbrieven**: U hebt een gebruikersbenaming en een wachtwoord (of een persoonlijk toegangstoken) nodig om tot de bewaarplaats veilig toegang te hebben.

   **waar om deze informatie te vinden?**

   Voor geleidelijke instructies bij de plaats bepalen van deze details, verwijs naar het artikel van de Liga van de Ervaring van Adobe &quot;[&#x200B; Toegang tot Git &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=nl-NL#accessing-git)&quot;.

   **Uw project is klaar!**

   Wanneer de opdracht met succes is voltooid, ziet u een nieuwe map die in uw lokale map is gemaakt. Deze map krijgt de naam van uw programma (bijvoorbeeld programma-id). Deze map bevat alle bestanden en code die u hebt gedownload van uw AEM as a Cloud Service Git-opslagplaats.

   In deze handleiding wordt deze map de `[AEMaaCS project directory]` genoemd.


### De nieuwe landinstelling toevoegen aan de Guide Localization Service

1. Open de opslagplaats map in een editor.

   ![&#x200B; omslag van de Bewaarplaats in een redacteur &#x200B;](/help/forms/assets/repository-folder-in-an-editor.png)

1. Zoek het `Guide Localization Service.cfg.json` -bestand. Dit bestand bepaalt de landinstellingen die worden ondersteund door uw AEM Forms-toepassing. U kunt dit bestand bewerken en een nieuwe landinstelling toevoegen.

   * **Bestaand dossier**: Als het dossier reeds bestaat, bepaal de plaats van het binnen uw het projectfolder van AEM Forms. De gebruikelijke locatie is:

     ```Shell
     [AEMaaCS project directory]/ui.config/src/main/content/jcr_root/apps/<appid>/osgiconfig/config`. 
     ```

     Vervang `<appid>` door uw projectspecifieke toepassings-id. U kunt `<appid>` voor uw AEM-project vinden in het `archetype.properties` -bestand.

     ![&#x200B; archetype Eigenschappen &#x200B;](/help/forms/assets/archetype-properties.png)

   * **Nieuw dossier**: Als het dossier niet bestaat, moet u het in de zelfde hierboven vermelde plaats tot stand brengen. Kopieer niet de naam van het bestand uit dit document, maar typ de naam handmatig. De bestandsnaam `Guide Localization Service.cfg.json` bevat spaties. Dit is opzettelijk en geen typefout in de documentatie.

     Een voorbeeldbestand met de lijst met door OOTB ondersteunde landinstellingen is:

     ```
         {
             "supportedLocales":[
             "en",
             "fr",
             "de",
             "ja",
             "pt-br",
             "zh-cn",
             "zh-tw",
             "ko-kr",
             "it",
             "es"
             ]
         }
     ```

1. Voeg de landinstellingscode voor de gewenste taal toe aan het bestand.
   1. Gebruik de [&#x200B; Lijst van ISO 639-1 codes &#x200B;](https://en.wikipedia.org/wiki/List_of_ISO_639_language_codes) om de twee-brief code te vinden die uw gewenste taal vertegenwoordigt.

   1. Neem de landinstellingscode op in het `Guide Localization Service.cfg.json` -bestand. Hier volgen enkele voorbeelden:

      * Talen van links naar rechts:
         * Engels (Verenigde Staten): en-US
         * Spaans (Spanje): es-ES
         * Frans (Frankrijk): fr-FR
      * Talen van rechts naar links:
         * Arabische Emiraten: ar-ae
         * Hebreeuws: he (of iw voor historische referentie)
         * Farsi: fa

1. Nadat u wijzigingen hebt aangebracht, controleert u of het `Guide Localization Service.cfg.json` -bestand correct is opgemaakt als een geldig JSON-bestand. Fouten in JSON-opmaak kunnen ervoor zorgen dat deze niet goed werkt. Sla het bestand op.



### Gebruik de voorbeeldclientbibliotheek voor eenvoudige locale toevoeging

AEM Forms biedt een handige voorbeeldclientbibliotheek, `clientlib-it-custom-locale` , om het toevoegen van nieuwe landinstellingen te vereenvoudigen. Deze bibliotheek maakt deel uit van de [&#x200B; Adaptieve gegevensopslagplaats van de Componenten van de Kern van Forms &#x200B;](https://github.com/adobe/aem-core-forms-components), beschikbaar op GitHub.


Alvorens wij beginnen, verzeker u een lokaal exemplaar van de [ Aangepaste gegevensopslagplaats van de Componenten van de Kern van Forms ] hebt. Als dat niet het geval is, kunt u het gemakkelijk klonen met Git met de volgende opdracht:

```SHELL
git clone https://github.com/adobe/aem-core-forms-components.git
```

Met deze opdracht downloadt u de gehele opslagplaats, inclusief de client-it-custom-locale bibliotheek, naar een map met de naam aem-core-forms-components op uw computer.

![&#x200B; Adaptieve de opslagplaats van de Componenten van de Kern van Forms Core op lokale machine &#x200B;](/help/forms/assets/core-forms-components-repo-on-local-machine.png)

### De voorbeeldclientbibliotheek integreren

Nu, neem de `clientlib-it-custom-locale` bibliotheek in uw AEM as a Cloud Service op, [ AEMaaCS projectfolder ]:

1. Zoek de voorbeeldclientbibliotheek:

   Binnen uw lokaal exemplaar van de [ Adaptieve plaats van de Componenten van de Kern van Forms ], navigeer aan de volgende weg:

   ```
       /aem-core-forms-components/it/apps/src/main/content/jcr_root/apps/forms-core-components-it/clientlibs
   ```

1. Kopieer en plak de bibliotheek:

   1. Kopieer de map `clientlib-it-custom-locale` .

      ![&#x200B; het Kopiëren clientlib-het-douane-scène &#x200B;](/help/forms/assets/clientlib-it-custom-locale-copy.png)

   1. Navigeer aan de volgende folder binnen uw [ AEMaaCS projectfolder ]:

      ```
      /ui.apps/src/main/content/jcr_root/apps/<app-id>/clientlib
      ```

      **Belangrijk**: Vervang `<app-id>` met daadwerkelijke identiteitskaart van uw toepassing.

   1. Plak de gekopieerde `clientlib-it-custom-locale` map in deze map.

      ![&#x200B; het Plakken clientlib-het-douane-scène &#x200B;](/help/forms/assets/clientlib-it-custom-locale-paste.png)

1. `aemLangUrl` pad bijwerken in `languageinit.js`

   1. Navigeer aan de volgende folder binnen uw [ AEMaaCS projectfolder ]:

      ```
      /ui.apps/src/main/content/jcr_root/apps/<app-id>/clientlib/clientlib-it-custom-locale/js
      ```

   1. Open het `languageinit.js` -bestand in de editor.
   1. Zoek de volgende regel in het `languageinit.js` -bestand:

      `const aemLangUrl = /etc.clientlibs/forms-core-components-it/clientlibs/clientlib-it-custom-locale/resources/i18n/${lang}.json;`

   1. Vervang `forms-core-components-it` door uw `<app-id>` (werkelijke id van uw toepassing) op de bovenstaande regel.

      `const aemLangUrl = '/etc.clientlibs/<app-id>/clientlibs/clientlib-it-custom-locale/resources/i18n/${lang}.json';`

      ![&#x200B; taal-init-dossier &#x200B;](/help/forms/assets/language-init-name-change.png)

>[!NOTE]
>  
> Als u `forms-core-components-it` niet vervangt door uw projectnaam of `<app-id>` , kan de component voor de datumkiezer niet worden vertaald.

### Maak een bestand voor uw nieuwe landinstelling:

1. Navigeer naar de map Locale:

   Navigeer binnen uw `[AEMaaCS project directory]` naar het volgende pad:

   ```
       /ui.apps/src/main/content/jcr_root/apps/<program-id>/clientlibs/clientlib-it-custom-locale/resources/i18n/
   ```

   **Belangrijk**: Vervang `<program-id>` met uw daadwerkelijke toepassingsidentiteitskaart

1. Zoek het voorbeeld Engels:

   AEM Forms verstrekt het van de a [&#x200B; steekproef Engelse scènedossier (.json) op GitHub &#x200B;](https://github.com/adobe/aem-core-forms-components/blob/master/ui.af.apps/src/main/content/jcr_root/apps/core/fd/af-clientlibs/core-forms-components-runtime-all/resources/i18n/en.json).

   Het Engelstalige bestand bevat de standaardset tekenreeksen ter referentie. In het bestand dat specifiek is voor de landinstelling, moet de structuur van het taalbestand worden nagebootst.

   Voor talen zoals Arabisch, Hebreeuws en Farsi wordt tekst van rechts naar links (RTL) gelezen in plaats van van van links naar rechts (LTR) zoals Engels. Om ervoor te zorgen dat uw formulieren correct in deze talen worden weergegeven, raden we u aan onze voorbeeldbestanden als richtlijn te gebruiken. Deze bestanden bevatten een referentie voor het opmaken van tekst, datums en andere elementen voor RTL-talen. U kunt de voorbeeldbestanden voor landinstellingen vinden:

   * [&#x200B; Arabisch &#x200B;](/help/forms/assets/ar-ae.json)
   * [&#x200B; Hebreeuws &#x200B;](/help/forms/assets/he.json)
   * [&#x200B; Farsi &#x200B;](/help/forms/assets/fa.json)

   Door deze voorbeeldbestanden te benutten, kunt u ervoor zorgen dat uw formulieren gebruikers die in RTL-talen werken, een naadloze ervaring bieden.


1. Maak uw lokale bestand:

   1. Maak een nieuw .json-bestand in de map `i18n` .
   1. Geef het bestand een naam met de juiste landcode voor de gewenste taal (bijvoorbeeld fr-FR.json voor Frans en ar-ae.json voor Arabisch). De structuur van dit bestand moet het Engelse landinstellingsbestand weerspiegelen.


1. Structuur en omzetting:

   1. Open het nieuwe bestand in een teksteditor.

   1. Vervang de Engelse waarden door de corresponderende vertalingen voor uw doeltaal.

   1. Nadat u de tekenreeksen hebt vertaald, slaat u het bestand op.




### Ondersteuning voor landinstellingen toevoegen aan het woordenboek

Deze stap is alleen van toepassing op andere landinstellingen dan de volgende algemeen ondersteunde landinstellingen: Engels (en), Duits (de), Spaans (es), Frans (fr), Italiaans (it), Braziliaans Portugees (pt-br), Chinees (vereenvoudigd - zh_cn), Chinees (Traditioneel - zh_tw), Japans (ja) en Koreaans (ko_kr).

1. Zoek de configuratiemap:

   Navigeer aan de volgende folder in uw [ AEMaaCS projectfolder ]:

   ```
   /ui.content/src/main/content/jcr_root/etc
   ```

1. Maak de benodigde mappen (indien deze ontbreken):

   Als de map `etc` niet in de map `jcr_root` staat, maakt u deze. Maak binnen `etc` een andere map met de naam `languages` als deze ontbreekt.

1. Maak het configuratiebestand voor de landinstelling:

   Maak in de map `languages` een nieuw bestand met de naam `.content.xml` . Kopieer niet de naam van het bestand uit dit document, maar typ de naam handmatig.

   ![&#x200B; creeer een nieuw dossier genoemd `.content.xml`](etc-content-xml.png)

   Open dit dossier en kleef de volgende inhoud, die [ LOCALE_CODE ] met de daadwerkelijke scènecode (bijvoorbeeld, ar-ae voor Arabisch) vervangt.


   ```XML
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:nt="http://www.jcp.org/jcr/nt/1.0"
         jcr:primaryType="nt:unstructured"
         languages="[de,es,fr,it,pt-br,zh-cn,zh-tw,ja,ko-kr,hi]"/>
   ```

   Waarschuwing: vervang de bestaande lijst niet. Voeg in plaats daarvan de nieuwe landinstellingscode toe binnen vierkante haakjes, gescheiden door komma&#39;s, zoals in dit voorbeeld (met ar-ae):

   ```XML
   languages="[de,es,fr,it,pt-br,zh-cn,zh-tw,ja,ko-kr,hi,ar-ae]"
   ```

1. Neem de nieuwe mappen op in filter.xml:

   Navigeer aan het `/ui.content/src/main/content/meta-inf/vault/filter.xml` dossier in uw [ AEMaaCS projectfolder ].

   Open het bestand en voeg de volgende regel aan het einde toe:

   ```
   <filter root="/etc/languages"/>
   ```

   ![&#x200B; Voeg de gemaakte mappen toe in `filter.xml` under `/ui.content/src/main/content/meta-inf/vault/filter.xml`](langauge-filter.png)

1. Sla het bestand op.

### De nieuwe landinstelling implementeren in uw AEM-omgeving

U bent nu klaar om de nieuwe landinstelling te gebruiken met uw Adaptive Forms. U kunt

* Stel AEM as a Cloud Service, [ AEMaaCS projectfolder ], aan uw lokale ontwikkelomgeving op om de nieuwe scèneconfiguratie op uw lokale machine te proberen. Distribueren naar uw lokale ontwikkelomgeving:

   1. Zorg ervoor dat uw lokale ontwikkelomgeving actief is. Als u niet reeds opstelling een lokale ontwikkelomgeving hebt, verwijs naar de gids op [&#x200B; de lokale ontwikkelomgeving van de Opstelling voor AEM Forms &#x200B;](/help/forms/setup-local-development-environment.md).

   1. Open het eindvenster of de bevelherinnering.

   1. Ga aan de [ AEMaaCS projectfolder ]

   1. Voer de volgende opdracht uit:

      ```
      mvn -PautoInstallPackage clean install
      ```

* Stel AEM as a Cloud Service, [ AEMaaCS projectfolder ], aan uw milieu van Cloud Service op. Distribueren naar uw Cloud Service-omgeving:

   1. Uw wijzigingen vastleggen:

      Na het toevoegen van de nieuwe scèneconfiguratie, begaat uw veranderingen met een duidelijk bericht van het Git beschrijvend de scènetoevoeging (bijvoorbeeld, &quot;Toegevoegde steun voor [ Naam van de Landinstelling ]&quot;).

   1. Implementeer de bijgewerkte code:

      Trigger een plaatsing van uw code door de [&#x200B; bestaande volledig-stapelpijpleiding &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=nl-NL#setup-pipeline). Hiermee wordt de bijgewerkte code automatisch samengesteld en geïmplementeerd met de nieuwe ondersteuning voor landinstellingen.

      Als u niet reeds opstelling een pijpleiding hebt, verwijs naar de gids op [&#x200B; hoe te opstelling een pijpleiding voor AEM Forms as a Cloud Service &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=nl-NL#setup-pipeline).


## Een voorbeeld bekijken van een adaptief formulier met de nieuwe landinstelling

Deze stappen begeleiden u door een voorbeeld weer te geven van een adaptief formulier met de nieuwe landinstelling:

1. Meld u aan bij uw AEM Forms as a Cloud Service-exemplaar.
1. Ga naar **Forms** > **Forms en Documenten**.
1. Selecteer een AanpassingsVorm en klik **toevoegen Woordenboek** en **voeg Woordenboek aan de tovenaar van het Project van de Vertaling** verschijnt.
1. Specificeer de **Titel van het Project** en selecteer de **Talen van het Doel** van het drop-down menu in **Woordenboek aan de tovenaar van het Project van de Vertaling** toevoegen.
1. Klik **Gedaan** en voer het gecreeerde vertaalproject uit.
1. Ga naar **Forms** > **Forms en Documenten**.
1. Selecteer de Aangepaste Vorm en kies de **Voorproef als optie van HTML**.
1. Voeg `&afAcceptLang=<locale-name>` toe aan de URL van de voorvertoning en druk op Enter. Vervang `<locale-name>` door de werkelijke landcode. Het adaptieve formulier wordt weergegeven in de opgegeven landinstelling.

## Aanbevolen procedures voor ondersteuning van nieuwe lokalisatie {#best-practices}

* Adobe raadt u aan een vertaalproject te maken nadat u een adaptief formulier hebt gemaakt. Dit stroomlijnt het lokalisatieproces.
* Wanneer de componenten Numeriek vak en Datumkiezer naar een specifieke landinstelling worden vertaald, kunnen er opmaakproblemen optreden. Om dit te verlichten, is de optie van de Taal van a **opgenomen in de Configure dialoog van** de plukker van de Datum component [&#x200B; en &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/date-picker#format-tab) Numerieke component van de Doos [.](https://experienceleague.adobe.com/nl/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/numeric-box#formats-configure-tab)


* Nieuwe velden verwerken:

   * **Vertaling van de Machine**: Als het gebruiken van machinevertaling, moet u het woordenboek opnieuw creëren en [&#x200B; in werking stellen het vertaalproject &#x200B;](/help/forms/using-aem-translation-workflow-to-localize-adaptive-forms-core-components.md) na het toevoegen van nieuwe gebieden aan een bestaande Aangepaste Vorm. Nieuwe velden die na het eerste vertaalproject worden toegevoegd, blijven onvertaald.

   * **Menselijke Vertaling**: Voor menselijke vertaalwerkschema&#39;s, voer het woordenboek uit gebruikend UI bij `[AEM Forms Server]/libs/cq/i18n/gui/translator.html`. Werk het woordenboek voor de nieuwe gebieden bij en upload de herziene versie.


## Zie ook {#see-also}

{{see-also}}

* [Opnamedocument genereren voor Adaptive Forms](/help/forms/generate-document-of-record-core-components.md)
* [Een adaptief formulier toevoegen aan een AEM Sites-pagina of Ervaar fragment](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)

