---
title: Hoe kan ik ondersteuning voor nieuwe landinstellingen toevoegen aan een adaptief formulier op basis van kerncomponenten?
description: Leer nieuwe landinstellingen toe te voegen voor een adaptief formulier.
feature: Adaptive Forms, Core Components
Role: Developer, Author
exl-id: bc06542b-84c8-4c6a-a305-effbd16d5630
source-git-commit: 8730383d26c6f4fbe31a25a43d33bf314251d267
workflow-type: tm+mt
source-wordcount: '2068'
ht-degree: 0%

---

# Een landinstelling toevoegen voor Adaptive Forms op basis van Core Components {#supporting-new-locales-for-adaptive-forms-localization}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| Elementaire componenten | [Klik hier](supporting-new-language-localization.md) |
| Kernonderdelen | Dit artikel |

<span class="preview"> De ondersteuning voor talen die van rechts naar links worden geschreven, is beschikbaar in het programma voor vroegtijdige adoptie. U kunt vanaf uw officiële e-mailadres naar aem-forms-ea@adobe.com schrijven om deel te nemen aan het programma voor vroege adoptie en toegang tot de functie te vragen. </span>

AEM Forms biedt in de box-ondersteuning voor de landinstellingen Engels (en), Spaans (es), Frans (fr), Italiaans (it), Duits (de), Japans (ja), Portugees-Braziliaans (pt-BR), Chinees (zh-CN), Chinees-Taiwan (zh-TW) en Koreaans (ko-KR). U kunt ook ondersteuning toevoegen voor meer landinstellingen, zoals Hindi(hi_IN). U kunt Adaptief Forms ook weergeven in een RTL-taal (rechts naar links), zoals Arabisch, Perzisch en Urdu, door deze landinstellingen toe te voegen.

## Hoe bepaalt AEM Forms de landinstelling voor een adaptief formulier?

Kennis van de manier waarop AEM Forms de landinstelling selecteert voor het weergeven van een adaptief formulier is van cruciaal belang voor een correcte lokalisatie. Hier volgt een uitsplitsing van het selectieproces:

### Landinstelling selecteren op basis van prioriteit

AEM Forms geeft prioriteit aan de volgende methoden om de landinstelling voor een adaptief formulier te bepalen:

1. **URL-kiezer voor landinstelling ([landinstelling])**:

   Het systeem geeft prioriteit aan de landinstelling die in de URL is opgegeven met behulp van de [landinstelling] kiezer. Met deze indeling kan caching worden gebruikt voor betere prestaties.

   Indeling: De URL volgt deze notatie: http:/[URL AEM Forms-server]/content/forms/af/[afName].[landinstelling].html?wcmmode=disabled.

   Voorbeeld: https://[server]/content/forms/af/contact-us.hi.html geeft het formulier in het Hindi weer.


1. **afAcceptLang Request-parameter**:

   Als u de landinstelling van de browser van de gebruiker wilt overschrijven, kunt u de `afAcceptLang` in de URL.

   Voorbeeld: https://[server]/forms/af/survey.ca-fr.html?afAcceptLang=ca-fr dwingt het formulier om het in het Canadese Frans weer te geven.

1. **Landinstelling browser van gebruiker (Koptekst voor geaccepteerde taal)**:

   Als er geen andere landinstelling is opgegeven, neemt AEM Forms de landinstelling van de browser van de gebruiker in overweging die met de `Accept-Language` header.


### Terugvalmechanisme:


* Als een clientbibliotheek (proces voor het toevoegen van een nieuwe landinstelling, zoals verderop in dit document wordt uitgelegd) voor de aangevraagde landinstelling niet beschikbaar is, zoekt AEM Forms naar een bibliotheek op basis van de taalcode in de landinstelling.

  Voorbeeld: als en_ZA (Zuid-Afrikaans Engels) wordt aangevraagd en er geen en_ZA-bibliotheek is, wordt en (Engels) gebruikt, indien beschikbaar.

  Als er geen geschikte clientbibliotheek wordt gevonden, wordt het standaardwoordenboek (meestal `en`) wordt gebruikt voor de ontwerptaal van het formulier.

  Als er geen landinstellingsgegevens beschikbaar zijn, wordt het Adaptief formulier weergegeven in de oorspronkelijke taal die tijdens de ontwikkeling is gebruikt.


## Voorwaarden voor het toevoegen van een landinstelling

Voordat u een nieuwe landinstelling gaat toevoegen voor uw Adaptive Forms, moet u het volgende doen:

**Software:**

* Redacteur van de Tekst van het normaal (winde): Terwijl om het even welke gewone tekstredacteur kan werken, een Geïntegreerde Ontwikkelomgeving (winde) zoals [Microsoft Visual Studio-code](https://code.visualstudio.com/download) biedt geavanceerde functies om het bewerken te vereenvoudigen.

* Git: Dit versiebeheersysteem is vereist voor het beheren van codewijzigingen. Als u het niet hebt geïnstalleerd, download het van [https://git-scm.com](https://git-scm.com).


**Codeopslagplaats:**

Clone the Adaptive Forms Core Components Repository: U hebt een clientbibliotheek van deze opslagplaats nodig om een landinstelling toe te voegen. De gegevensopslagruimte klonen:

1. Open de opdrachtregel of het terminalvenster.

1. Navigeer naar de gewenste locatie op uw computer waar u de opslagplaats wilt opslaan (bijvoorbeeld /adaptive-forms-core-components).

1. Voer de volgende opdracht uit om de gegevensopslagruimte te klonen:

   ```
   git clone https://github.com/adobe/aem-core-forms-components.git
   ```

   Met deze opdracht downloadt u de opslagplaats en maakt u een map met de naam `aem-core-forms-components` op uw computer. In deze handleiding wordt deze map de `[Adaptive Forms Core Components repository]`


## Een landinstelling toevoegen {#add-localization-support-for-non-supported-locales}

Ga als volgt te werk om ondersteuning voor nieuwe landinstellingen toe te voegen aan een adaptief formulier op basis van kerncomponenten:

### Cloud uw AEM as a Cloud Service Git-opslagplaats

1. Open de opdrachtregel en kies een directory waarin de AEM as a Cloud Service opslagplaats moet worden opgeslagen, zoals `/cloud-service-repository/`.

1. Voer de onderstaande opdracht uit om de gegevensopslagruimte te klonen:

   ```SHELL
   git clone https://git.cloudmanager.adobe.com/<organization-name>/<program id>/
   ```

   U hebt enkele informatie nodig om uw Git-opslagplaats te klonen:

   * **Naam organisatie**: Dit identificeert uw team of project binnen Adobe Experience Manager as a Cloud Service (AEM as a Cloud Service).

   * **Programma-id**: Dit geeft het programma aan dat is gekoppeld aan uw opslagplaats.

   * **Credentials**: U hebt een gebruikersnaam en wachtwoord (of een persoonlijke toegangstoken) nodig om veilig toegang te krijgen tot de opslagplaats.

   **Waar vind je deze informatie?**

   Raadpleeg het Adobe Experience League-artikel &quot;[Toegang tot it](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#accessing-git)&quot;.

   **Uw project is klaar!**

   Wanneer de opdracht met succes is voltooid, ziet u een nieuwe map die in uw lokale map is gemaakt. Deze map krijgt de naam van uw programma (bijvoorbeeld programma-id). Deze map bevat alle bestanden en code die zijn gedownload van de AEM as a Cloud Service Git-opslagplaats.

   In deze handleiding wordt deze map de `[AEMaaCS project directory]`.


### De nieuwe landinstelling toevoegen aan de Guide Localization Service

1. Open de opslagplaats map in een editor.

   ![Map met opslagplaats in een editor](/help/forms/assets/repository-folder-in-an-editor.png)

1. Zoek de `Guide Localization Service.cfg.json` bestand. Dit bestand bepaalt de landinstellingen die worden ondersteund door uw AEM Forms-toepassing. U kunt dit bestand bewerken en een nieuwe landinstelling toevoegen.

   * **Bestaand bestand**: Als het bestand al bestaat, zoekt u het in de AEM Forms-projectmap. De gebruikelijke locatie is:

     ```Shell
     [AEMaaCS project directory]/ui.config/src/main/content/jcr_root/apps/<appid>/osgiconfig/config`. 
     ```

     Vervangen `<appid>` met uw projectspecifieke toepassings-id. U kunt zoeken `<appid>` voor uw AEM Project in `archetype.properties` bestand.

     ![Eigenschappen van Archetype](/help/forms/assets/archetype-properties.png)

   * **Nieuw bestand**: Als het bestand niet bestaat, moet u het op de hierboven vermelde locatie maken. Kopieer niet de naam van het bestand uit dit document, maar typ de naam handmatig. De bestandsnaam `Guide Localization Service.cfg.json` bevat spaties. Dit is opzettelijk en geen typefout in de documentatie.

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
   1. Gebruik de [Lijst van ISO 639-1-codes](https://en.wikipedia.org/wiki/List_of_ISO_639_language_codes) om de code van twee letters te vinden die uw gewenste taal vertegenwoordigt.

   1. De landinstellingscode opnemen in het dialoogvenster `Guide Localization Service.cfg.json` bestand. Hier volgen enkele voorbeelden:

      * Talen van links naar rechts:
         * Engels (Verenigde Staten): en-US
         * Spaans (Spanje): es-ES
         * Frans (Frankrijk): fr-FR
      * Talen van rechts naar links:
         * Arabische Emiraten: ar-ae
         * Hebreeuws: he (of iw voor historische referentie)
         * Farsi: fa

1. Nadat u wijzigingen hebt aangebracht, controleert u de `Guide Localization Service.cfg.json` bestand correct is opgemaakt als een geldig JSON-bestand. Fouten in JSON-opmaak kunnen ervoor zorgen dat deze niet goed werkt. Sla het bestand op.



### Gebruik de voorbeeldclientbibliotheek voor eenvoudige locale toevoeging

AEM Forms biedt een handige voorbeeldclientbibliotheek. `clientlib-it-custom-locale`om het toevoegen van nieuwe landinstellingen te vereenvoudigen. Deze bibliotheek maakt deel uit van de [Adaptive Forms Core Components-opslagplaats](https://github.com/adobe/aem-core-forms-components), beschikbaar op GitHub.


Voordat we beginnen, zorg er dan voor dat u een lokale kopie van de [Adaptive Forms Core Components-opslagplaats]. Als dat niet het geval is, kunt u het gemakkelijk klonen met Git met de volgende opdracht:

```SHELL
git clone https://github.com/adobe/aem-core-forms-components.git
```

Met deze opdracht downloadt u de gehele opslagplaats, inclusief de client-it-custom-locale bibliotheek, naar een map met de naam aem-core-forms-components op uw computer.

![Adaptive Forms Core Components repository directory op lokale computer](/help/forms/assets/core-forms-components-repo-on-local-machine.png)

### De voorbeeldclientbibliotheek integreren

Laten we nu de `clientlib-it-custom-locale` bibliotheek in uw AEM as a Cloud Service; [AEMaaCS-projectmap]:

1. Zoek de voorbeeldclientbibliotheek:

   Binnen uw lokale exemplaar van [Adaptive Forms Core Components-opslagplaats]navigeer naar het volgende pad:

   ```
       /aem-core-forms-components/it/apps/src/main/content/jcr_root/apps/forms-core-components-it/clientlibs
   ```

1. Kopieer en plak de bibliotheek:

   1. De `clientlib-it-custom-locale` map.

      ![Clientlib-it-custom-locale kopiëren](/help/forms/assets/clientlib-it-custom-locale-copy.png)

   1. Navigeer naar de volgende map in de map [AEMaaCS-projectmap]:

      ```
      /ui.apps/src/main/content/jcr_root/apps/<app-id>/clientlib
      ```

      **Belangrijk**: Vervangen `<app-id>` met de werkelijke id van uw toepassing.

   1. De gekopieerde bestanden plakken `clientlib-it-custom-locale` in deze map.

      ![Clilib-it-custom-locale plakken](/help/forms/assets/clientlib-it-custom-locale-paste.png)


### Maak een bestand voor uw nieuwe landinstelling:

1. Navigeer naar de map Locale:

   Binnen uw `[AEMaaCS project directory]`navigeer naar het volgende pad:

   ```
       /ui.apps/src/main/content/jcr_root/apps/<program-id>/clientlibs/clientlib-it-custom-locale/resources/i18n/
   ```

   **Belangrijk**: Vervangen `<program-id>` met uw werkelijke toepassings-id.

1. Zoek het voorbeeld Engels:

   AEM Forms biedt een [voorbeeld Engelstalig bestand (.json) op GitHub](https://github.com/adobe/aem-core-forms-components/blob/master/ui.af.apps/src/main/content/jcr_root/apps/core/fd/af-clientlibs/core-forms-components-runtime-all/resources/i18n/en.json).

   Het Engelstalige bestand bevat de standaardset tekenreeksen ter referentie. In het bestand dat specifiek is voor de landinstelling, moet de structuur van het taalbestand worden nagebootst.

   Voor talen zoals Arabisch, Hebreeuws en Farsi wordt tekst van rechts naar links (RTL) gelezen in plaats van van van links naar rechts (LTR) zoals Engels. Om ervoor te zorgen dat uw formulieren correct in deze talen worden weergegeven, raden we u aan onze voorbeeldbestanden als richtlijn te gebruiken. Deze bestanden bevatten een referentie voor het opmaken van tekst, datums en andere elementen voor RTL-talen. U kunt de voorbeeldbestanden voor landinstellingen vinden:

   * [Arabisch](/help/forms/assets/ar-ae.json)
   * [Hebreeuws](/help/forms/assets/he.json)
   * [Farsi](/help/forms/assets/fa.json)

   Door deze voorbeeldbestanden te benutten, kunt u ervoor zorgen dat uw formulieren gebruikers die in RTL-talen werken, een naadloze ervaring bieden.


1. Maak uw lokale bestand:

   1. Maak een nieuw .json-bestand in het dialoogvenster `i18n` directory.
   1. Geef het bestand een naam met de juiste landcode voor de gewenste taal (bijvoorbeeld fr-FR.json voor Frans en ar-ae.json voor Arabisch). De structuur van dit bestand moet het Engelse landinstellingsbestand weerspiegelen.


1. Structuur en omzetting:

   1. Open het nieuwe bestand in een teksteditor.

   1. Vervang de Engelse waarden door de corresponderende vertalingen voor uw doeltaal.

   1. Nadat u de tekenreeksen hebt vertaald, slaat u het bestand op.




### Ondersteuning voor landinstellingen toevoegen aan het woordenboek

Deze stap is alleen van toepassing op andere landinstellingen dan de volgende algemeen ondersteunde landinstellingen: Engels (en), Duits (de), Spaans (es), Frans (fr), Italiaans (it), Braziliaans Portugees (pt-br), Chinees (vereenvoudigd - zh_cn), Chinees (Traditioneel - zh_tw), Japans (ja) en Koreaans (ko_kr).

1. Zoek de configuratiemap:

   Navigeer naar de volgende map in de [AEMaaCS-projectmap]:

   ```
   /ui.content/src/main/content/jcr_root/etc
   ```

1. Maak de benodigde mappen (indien deze ontbreken):

   Als de `etc` map bestaat niet binnen `jcr_root` maken. Binnen `etc`, maakt u een andere map met de naam `languages` als het ontbreekt.

1. Maak het configuratiebestand voor de landinstelling:

   Binnen de `languages` een nieuw bestand met de naam `.content.xml`. Kopieer niet de naam van het bestand uit dit document, maar typ de naam handmatig.

   ![een nieuw bestand met de naam `.content.xml`](etc-content-xml.png)

   Open dit bestand en plak de volgende inhoud, waarbij u [LOCALE_CODE] met de werkelijke landinstellingscode (bijvoorbeeld ar-ae voor Arabisch).


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

   Ga naar de `/ui.content/src/main/content/meta-inf/vault/filter.xml` bestand in uw [AEMaaCS-projectmap].

   Open het bestand en voeg de volgende regel aan het einde toe:

   ```
   <filter root="/etc/languages"/>
   ```

   ![Voeg de gemaakte mappen toe aan het dialoogvenster `filter.xml` krachtens `/ui.content/src/main/content/meta-inf/vault/filter.xml`](langauge-filter.png)

1. Sla het bestand op.

### De nieuwe landinstelling implementeren in uw AEM

U bent nu klaar om de nieuwe landinstelling te gebruiken met uw Adaptive Forms. U kunt

* Implementeer de AEM as a Cloud Service, [AEMaaCS-projectmap], naar uw lokale ontwikkelomgeving om de nieuwe configuratie voor landinstellingen op uw lokale computer uit te proberen. Distribueren naar uw lokale ontwikkelomgeving:

   1. Zorg ervoor dat uw lokale ontwikkelomgeving actief is. Als u nog geen lokale ontwikkelomgeving hebt ingesteld, raadpleegt u de handleiding op [Lokale ontwikkelomgeving instellen voor AEM Forms](/help/forms/setup-local-development-environment.md).

   1. Open het eindvenster of de bevelherinnering.

   1. Ga naar de [AEMaaCS-projectmap]

   1. Voer de volgende opdracht uit:

      ```
      mvn -PautoInstallPackage clean install
      ```

* Implementeer de AEM as a Cloud Service, [AEMaaCS-projectmap]aan uw Cloud Service-omgeving. Implementeren in uw Cloud Service-omgeving:

   1. Uw wijzigingen vastleggen:

      Nadat u de nieuwe landinstellingsconfiguratie hebt toegevoegd, geeft u uw wijzigingen door een duidelijk Git-bericht met een beschrijving van de toevoeging aan de landinstelling (bijvoorbeeld &quot;Toegevoegde ondersteuning voor [Landinstelling]&quot;).

   1. Implementeer de bijgewerkte code:

      Trigger een plaatsing van uw code door [bestaande full-stack pijpleiding](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=en#setup-pipeline). Hiermee wordt de bijgewerkte code automatisch samengesteld en geïmplementeerd met de nieuwe ondersteuning voor landinstellingen.

      Als u niet reeds opstelling een pijpleiding hebt, verwijs naar de gids op [hoe een pijpleiding voor AEM Forms as a Cloud Service op te zetten](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=en#setup-pipeline).


## Een voorbeeld bekijken van een adaptief formulier met de nieuwe landinstelling

Deze stappen begeleiden u door een voorbeeld weer te geven van een adaptief formulier met de nieuwe landinstelling:

1. Meld u aan bij uw as a Cloud Service AEM Forms-exemplaar.
1. Ga naar **Forms** >  **Forms en Documenten**.
1. Selecteer een adaptief formulier en klik op **Woordenboek toevoegen** en **Woordenboek toevoegen aan vertaalproject** wordt weergegeven.
1. Geef de **Projecttitel** en selecteert u de **Doeltalen** in het keuzemenu in het dialoogvenster **Woordenboek toevoegen aan vertaalproject** wizard.
1. Klikken **Gereed** en voert het gemaakte vertaalproject uit.
1. Ga naar **Forms** >  **Forms en Documenten**.
1. Selecteer het adaptieve formulier en kies de optie **Voorvertonen als HTML** -optie.
1. Toevoegen `&afAcceptLang=<locale-name>` naar de URL van de voorvertoning en druk op Enter. Vervangen `<locale-name>` met uw werkelijke landinstellingscode. Het adaptieve formulier wordt weergegeven in de opgegeven landinstelling.

## Aanbevolen procedures voor ondersteuning van nieuwe lokalisatie {#best-practices}

* Adobe raadt u aan een vertaalproject te maken nadat u een adaptief formulier hebt gemaakt. Dit stroomlijnt het lokalisatieproces.
* Wanneer de componenten Numeriek vak en Datumkiezer naar een specifieke landinstelling worden vertaald, kunnen er opmaakproblemen optreden. Om dit te beperken, **Taal** is opgenomen in het dialoogvenster Configureren van [component Datumkiezer](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/number-input#formats-configure-tab) en [Component Numeriek vak](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/numeric-box#formats-configure-tab).


* Nieuwe velden verwerken:

   * **Machinevertaling**: Als u automatische vertaling gebruikt, moet u het woordenboek opnieuw maken en[het vertaalproject uitvoeren](/help/forms/using-aem-translation-workflow-to-localize-adaptive-forms-core-components.md) na het toevoegen van nieuwe velden aan een bestaand adaptief formulier. Nieuwe velden die na het eerste vertaalproject worden toegevoegd, blijven onvertaald.

   * **Menselijke vertaling**: Voor workflows voor menselijke vertaling exporteert u het woordenboek met de gebruikersinterface op `[AEM Forms Server]/libs/cq/i18n/gui/translator.html`. Werk het woordenboek voor de nieuwe gebieden bij en upload de herziene versie.


## Zie ook {#see-also}

{{see-also}}

* [Opnamedocument genereren voor Adaptive Forms](/help/forms/generate-document-of-record-core-components.md)
* [Een adaptief formulier toevoegen aan een AEM Sites-pagina of Ervaar fragment](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)

