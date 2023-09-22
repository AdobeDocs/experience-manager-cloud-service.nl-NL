---
title: Hoe kunt u ondersteuning voor nieuwe landinstellingen toevoegen aan een adaptief formulier op basis van kerncomponenten?
description: Met AEM Forms kunt u nieuwe landinstellingen toevoegen voor het lokaliseren van adaptieve formulieren.
source-git-commit: 0a1310290c25a94ffe6f95ea6403105475ef5dda
workflow-type: tm+mt
source-wordcount: '1079'
ht-degree: 0%

---

# Een landinstelling toevoegen voor Adaptive Forms op basis van Core Components {#supporting-new-locales-for-adaptive-forms-localization}


| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| Elementaire componenten | [Klik hier](supporting-new-language-localization.md) |
| Kernonderdelen | Dit artikel |

AEM Forms biedt in de box-ondersteuning voor de landinstellingen Engels (en), Spaans (es), Frans (fr), Italiaans (it), Duits (de), Japans (ja), Portugees-Braziliaans (pt-BR), Chinees (zh-CN), Chinees-Taiwan (zh-TW) en Koreaans (ko-KR).

U kunt ook ondersteuning toevoegen voor meer landinstellingen, zoals Hindi(hi_IN).

<!-- 
## Understanding locale dictionaries {#about-locale-dictionaries}

The localization of adaptive forms relies on two types of locale dictionaries:

*   **Form-specific dictionary** Contains strings used in adaptive forms. For example, labels, field names, error messages, help descriptions. It is managed as a set of XLIFF files for each locale and you can access it at `[AEM Forms as a Cloud Service Author instance]/libs/cq/i18n/gui/translator.html`.

*   **Global dictionaries** There are two global dictionaries, managed as JSON objects, in AEM client library. These dictionaries contain default error messages, month names, currency symbols, date and time patterns, and so on.  These locations contain separate folders for each locale. Because global dictionaries are not updated frequently, keeping separate JavaScript files for each locale enables browsers to cache them and reduce network bandwidth usage when accessing different adaptive forms on same server.

-->

## Vereisten {#prerequistes}

Voordat u ondersteuning voor een nieuwe landinstelling gaat toevoegen,

* Installeer een normale tekstverwerker (IDE) voor eenvoudige bewerking. De voorbeelden in dit document zijn gebaseerd op Microsoft VS-code.
* Clone the Adaptive Forms Core Components repository. De gegevensopslagruimte klonen:
   1. Open de opdrachtregel of het tijdelijke venster en navigeer naar een locatie waar u de opslagplaats wilt opslaan. Bijvoorbeeld `/adaptive-forms-core-components`
   1. Voer de volgende opdracht uit om de gegevensopslagruimte te klonen:

      ```SHELL
          git clone https://github.com/adobe/aem-core-forms-components.git
      ```

  De gegevensopslagruimte bevat een clientbibliotheek die nodig is om een landinstelling toe te voegen.


## Een landinstelling toevoegen {#add-localization-support-for-non-supported-locales}

Ga als volgt te werk als u ondersteuning voor een nieuwe landinstelling wilt toevoegen:

![Een landinstelling toevoegen aan een gegevensopslagruimte](add-a-locale-adaptive-form-core-components.png)

### Cloud uw AEM as a Cloud Service Git-opslagplaats {#clone-the-repository}

1. Open de opdrachtregel en kies een directory waarin de opslagplaats moet worden opgeslagen, zoals `/cloud-service-repository/`.

1. Voer de volgende opdracht uit om de gegevensopslagruimte te klonen:

   ```SHELL
   git clone https://git.cloudmanager.adobe.com/<my-org>/<my-program>/
   ```

   Vervangen `<my-org>` en `<my-program>` in de bovenstaande URL met de naam van uw organisatie en het programma. Voor gedetailleerde instructies voor het verkrijgen van de naam van de organisatie, de naam van het programma of het volledige pad van uw Git-opslagplaats en de gegevens die nodig zijn om de opslagplaats te klonen, raadpleegt u de [Toegang tot it](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#accessing-git) artikel.

   Na succesvolle voltooiing van bevel, een omslag `<my-program>` wordt gemaakt. Het bevat de inhoud die is gekloond uit de Git-opslagplaats. In de rest van het artikel wordt de map aangeduid als: `[AEM Forms as a Cloud Service Git repostory]`.


### De nieuwe landinstelling toevoegen aan de Guide Localization Service {#add-a-locale-to-the-guide-localization-service}

1. Open de repository map, gekloond in vorige sectie, in een onbewerkte teksteditor.
1. Ga naar de `[AEM Forms as a Cloud Service Git repostory]/ui.config/src/main/content/jcr_root/apps/<appid>/osgiconfig/config` map. U kunt de `<appid>` in de `archetype.properties` bestanden van het project.
1. Open de `[AEM Forms as a Cloud Service Git repostory]/ui.config/src/main/content/jcr_root/apps/<appid>/osgiconfig/config/Guide Localization Service.cfg.json` bestand voor bewerking. Als het bestand niet bestaat, maakt u het. Een voorbeeldbestand met ondersteunde landinstellingen ziet er als volgt uit:

   ![Een voorbeeldgids Localization Service.cfg.json](locales.png)

1. Voeg de [landinstellingscode voor de taal](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) u wilt bijvoorbeeld &#39;hi&#39; toevoegen voor hindi.
1. Sla het bestand op en sluit het.

### Een clientbibliotheek maken om een landinstelling toe te voegen

AEM Forms biedt een voorbeeldclientbibliotheek waarmee u eenvoudig nieuwe landinstellingen kunt toevoegen. U kunt de `clientlib-it-custom-locale` clientbibliotheek van de Adaptive Forms Core Components-opslagplaats op GitHub naar uw as a Cloud Service Forms-opslagplaats. Ga als volgt te werk om de clientbibliotheek toe te voegen:

1. Open de Adaptive Forms Core Components-opslagplaats in uw normale teksteditor. Als de repository niet gekloond is, zie [Vereisten](#prerequistes) voor instructies om de gegevensopslagplaats te klonen.
1. Ga naar de `/aem-core-forms-components/it/apps/src/main/content/jcr_root/apps/forms-core-components-it/clientlibs` directory.
1. De `clientlib-it-custom-locale` directory.
1. Navigeren naar `[AEM Forms as a Cloud Service Git repostory]/ui.apps/src/main/content/jcr_root/apps/moonlightprodprogram/clientlibs` en plak de `clientlib-it-custom-locale` directory.


### Een landspecifiek bestand maken {#locale-specific-file}

1. Ga naar `[AEM Forms as a Cloud Service Git repostory]/ui.apps/src/main/content/jcr_root/apps/<program-id>/clientlibs/clientlib-it-custom-locale/resources/i18n/`
1. Zoek de [English locale.json file on GitHub](https://github.com/adobe/aem-core-forms-components/blob/master/ui.af.apps/src/main/content/jcr_root/apps/core/fd/af-clientlibs/core-forms-components-runtime-all/resources/i18n/en.json), die de meest recente set standaardtekenreeksen bevat die in het product zijn opgenomen.
1. Maak een nieuw JSON-bestand voor uw specifieke landinstelling.
1. In het nieuwe .json-bestand weerspiegelt u de structuur van het Engelse landinstellingsbestand.
1. Vervang de Engelse taaltekenreeksen in het JSON-bestand door de overeenkomstige gelokaliseerde tekenreeksen voor uw taal.
1. Sla het bestand op en sluit het.


### Ondersteuning voor landinstellingen toevoegen aan het woordenboek {#add-locale-support-for-the-dictionary}

Voer deze stap alleen uit als de `<locale>` u toevoegt behoort niet tot `en`, `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja`, `ko-kr`.

1. Ga naar de `[AEM Forms as a Cloud Service Git repostory]/ui.content/src/main/content/jcr_root/etc/` map.

1. Een `etc` map onder de `jcr_root` map, indien nog niet aanwezig.

1. Een map maken `languages` onder de `etc` map, indien nog niet aanwezig.

   ![Alt-tekst](etc-content-xml.png)

1. Een `.content.xml` bestand onder de `languages` map. Voeg de volgende inhoud toe aan het bestand:

   ```XML
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:nt="http://www.jcp.org/jcr/nt/1.0"
   jcr:primaryType="nt:unstructured"
   languages="[de,es,fr,it,pt-br,zh-cn,zh-tw,ja,ko-kr]"/>
   ```

1. Voeg de landinstellingscode toe aan de `languages` eigenschap. Deze wordt bijvoorbeeld voor het achterhoofd toegevoegd aan de volgende voorbeeldcode.


   ```XML
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:nt="http://www.jcp.org/jcr/nt/1.0"
   jcr:primaryType="nt:unstructured"
   languages="[de,es,fr,it,pt-br,zh-cn,zh-tw,ja,ko-kr,hi]"/>
   ```

1. Voeg de nieuwe mappen toe aan het dialoogvenster `filter.xml` krachtens `/ui.content/src/main/content/meta-inf/vault/filter.xml` als:

   ```
   <filter root="/etc/languages"/>
   ```

   ![Voeg de nieuwe mappen toe aan het dialoogvenster `filter.xml` krachtens `/ui.content/src/main/content/meta-inf/vault/filter.xml`](langauge-filter.png)

### Leg de wijzigingen vast en implementeer de pijpleiding {#commit-changes-in-repo-deploy-pipeline}

Leg de wijzigingen vast in de GIT-opslagplaats nadat u een nieuwe ondersteuning voor landinstellingen hebt toegevoegd. Implementeer uw code met de volledige stackpijplijn. Meer informatie [hoe een pijpleiding op te zetten](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=en#setup-pipeline) om nieuwe ondersteuning voor landinstellingen toe te voegen.

Zodra de pijpleidingslooppas succesvol is, is de onlangs toegevoegde scène klaar voor gebruik.

## Een voorbeeld bekijken van een adaptief formulier met de nieuwe landinstelling {#use-added-locale-in-af}

Voer de volgende stappen uit om een voorvertoning weer te geven van een adaptief met de nieuwe landinstelling:

1. Meld u aan bij uw as a Cloud Service AEM Forms-exemplaar.
1. Ga naar **Forms** >  **Forms en Documenten**.
1. Selecteer een adaptief formulier en klik op **Woordenboek toevoegen** en **Woordenboek toevoegen aan vertaalproject** wordt weergegeven.
1. Geef de **Projecttitel** en selecteert u de **Doeltalen** in het keuzemenu in het dialoogvenster **Woordenboek toevoegen aan vertaalproject** wizard.
1. Klikken **Gereed** en voert het gemaakte vertaalproject uit.
1. Selecteer een adaptief formulier en klik op **Voorvertonen als HTML**.
1. Toevoegen `&afAcceptLang=<locale-name>` in de URL van een adaptief formulier.
1. De pagina vernieuwen en het adaptieve formulier wordt weergegeven in een opgegeven landinstelling.

Er zijn twee methoden om de landinstelling van een adaptief formulier te bepalen. Wanneer een adaptief formulier wordt weergegeven, geeft dit de aangevraagde landinstelling aan met:

* De `[local]` in het aangepaste formulier-URL. De opmaak van de URL is `http:/[AEM Forms Server URL]/content/forms/af/[afName].[locale].html?wcmmode=disabled`. Gebruiken `[local]` kunt u een adaptief formulier in cache plaatsen.

* De volgende parameters in de vermelde volgorde ophalen:

   * Request-parameter `afAcceptLang`
Als u de browserlandinstelling van gebruikers wilt overschrijven, kunt u het `afAcceptLang` request parameter to force the locale. Met de volgende URL wordt bijvoorbeeld gedwongen het formulier te genereren in de landinstelling Canadees-Frans:
     `https://'[server]:[port]'/<contextPath>/<formFolder>/<formName>.html?wcmmode=disabled&afAcceptLang=ca-fr`

   * De landinstelling van de browser die voor de gebruiker is ingesteld. Deze landinstelling wordt in de aanvraag opgegeven met de functie `Accept-Language` header.

Als er geen clientbibliotheek voor de aangevraagde landinstelling bestaat, wordt in de bibliotheek gecontroleerd of er taalcode in de landinstelling aanwezig is. Als de aangevraagde landinstelling bijvoorbeeld `en_ZA` (Zuid-Afrikaans Engels) en de clientbibliotheek voor `en_ZA` niet bestaat, gebruikt het adaptieve formulier de clientbibliotheek voor `en` (Engels) taal, als deze bestaat. Als er echter geen van deze profielen bestaat, wordt in het adaptieve formulier het woordenboek gebruikt voor `en` landinstelling.

Nadat de landinstelling is geïdentificeerd, wordt in het adaptieve formulier het formulierspecifieke woordenboek gekozen. Als het formulierspecifieke woordenboek voor de aangevraagde landinstelling niet wordt gevonden, wordt het woordenboek gebruikt voor de taal waarin het adaptieve formulier is geschreven.

Als er geen landinstellingsinformatie beschikbaar is, wordt het adaptieve formulier weergegeven in de oorspronkelijke taal, de taal die wordt gebruikt tijdens de ontwikkeling van het formulier.

<!--
Get [sample client library](/help/forms/assets/locale-support-sample.zip) to add support for new locale. You need to change the content of the folder in the required locale.

## Best Practices to support for new localization {#best-practices}

*   Adobe recommends creating a translation project after creating an Adaptive Form.

*   When new fields are added in an existing Adaptive Form:
    * **For machine translation**: Re-create the dictionary and run the translation project. Fields added to an Adaptive Form after creating a translation project remain untranslated. 
    * **For human translation**: Export the dictionary through `[server:port]/libs/cq/i18n/gui/translator.html`. Update the dictionary for the newly added fields and upload it.
-->
