---
title: Ondersteuning voor nieuwe landinstellingen toevoegen aan een adaptief formulier
description: Met AEM Forms kunt u nieuwe landinstellingen toevoegen voor het lokaliseren van adaptieve formulieren. Engels (en), Spaans (es), Frans (fr), Italiaans (it), Duits (de), Japans (ja), Portugees-Braziliaans (pt-BR), Chinees (zh-CN), Chinees-Taiwan (zh-TW) en Koreaanse (ko-KR) landinstellingen.
exl-id: 4c7d6caa-1adb-4663-933f-b09129b9baef
source-git-commit: 9a1bb716256b5e820723911f4e78a6a4c69d940c
workflow-type: tm+mt
source-wordcount: '1352'
ht-degree: 0%

---

# Een landinstelling toevoegen voor Adaptive Forms op basis van Core Components {#supporting-new-locales-for-adaptive-forms-localization}


| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| Elementaire componenten | [Klik hier](supporting-new-language-localization.md) |
| Kernonderdelen | Dit artikel |

AEM Forms biedt in de box-ondersteuning voor de landinstellingen Engels (en), Spaans (es), Frans (fr), Italiaans (it), Duits (de), Japans (ja), Portugees-Braziliaans (pt-BR), Chinees (zh-CN), Chinees-Taiwan (zh-TW) en Koreaans (ko-KR). U kunt ook ondersteuning toevoegen voor meer landinstellingen, zoals Hindi(hi_IN).

## Werken met taalwoordenboeken {#about-locale-dictionaries}

De lokalisatie van adaptieve formulieren is afhankelijk van twee typen taalwoordenboeken:

* **Formulierspecifiek woordenboek** Bevat tekenreeksen die in adaptieve formulieren worden gebruikt. Bijvoorbeeld labels, veldnamen, foutberichten en Help-beschrijvingen. Het wordt beheerd als een set XLIFF-bestanden voor elke landinstelling en u kunt het bestand openen op `[author-instance]/libs/cq/i18n/gui/translator.html`.

* **Algemene woordenboeken** Er zijn twee algemene woordenboeken, beheerd als JSON-objecten, in AEM clientbibliotheek. Deze woordenboeken bevatten standaardfoutberichten, naam van de maand, valutasymbolen, datum- en tijdpatronen, enzovoort. U vindt deze woordenboeken op `[author-instance]/libs/fd/xfaforms/clientlibs/I18N`. Deze locaties bevatten afzonderlijke mappen voor elke landinstelling. Omdat algemene woordenboeken niet vaak worden bijgewerkt, kunnen browsers door afzonderlijke JavaScript-bestanden voor elke landinstelling te bewaren deze in cache plaatsen en het gebruik van de netwerkbandbreedte verminderen wanneer ze toegang krijgen tot verschillende adaptieve formulieren op dezelfde server.

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

AEM Forms ondersteunt momenteel de lokalisatie van Adaptive Forms-inhoud in het Engels (en), Spaans (es), Frans (fr), Italiaans (it), Duits (de), Japans (ja), Portugees-Braziliaans (pt-BR), Chinees (zh-CN), Chinees-Taiwan (zh-TW) en Koreaans (ko-KR). Ga als volgt te werk als u ondersteuning voor een nieuwe landinstelling wilt toevoegen bij Adaptive Forms runtime:

![Een landinstelling toevoegen aan een gegevensopslagruimte](add-a-locale-adaptive-form-core-components.png)

### 1. Kloont uw AEM as a Cloud Service Git-opslagplaats {#clone-the-repository}

1. Open de opdrachtregel en kies een directory waarin de opslagplaats moet worden opgeslagen, zoals `/cloud-service-repository/`.

1. Voer de volgende opdracht uit om de gegevensopslagruimte te klonen:

   ```SHELL
   git clone https://git.cloudmanager.adobe.com/<my-org>/<my-program>/
   ```

   Vervangen `<my-org>` en `<my-program>` in de bovenstaande URL met de naam van uw organisatie en het programma. Voor gedetailleerde instructies voor het verkrijgen van de naam van de organisatie, de naam van het programma of het volledige pad van uw Git-opslagplaats en de gegevens die nodig zijn om de opslagplaats te klonen, raadpleegt u de [Toegang tot it](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#accessing-git) artikel.

   Na succesvolle voltooiing van bevel, een omslag `<my-program>` wordt gemaakt. Het bevat de inhoud die is gekloond uit de Git-opslagplaats. In de rest van het artikel wordt de map aangeduid als: `[AEM Forms as a Cloud Service Git repostory]`.


### 2. Voeg de nieuwe landinstelling toe aan de Guide Localization Service {#add-a-locale-to-the-guide-localization-service}

1. Open de repository map, gekloond in vorige sectie, in een onbewerkte teksteditor.
1. Ga naar de `[AEM Forms as a Cloud Service Git repostory]/ui.config/src/main/content/jcr_root/apps/<appid>/osgiconfig/config` map. U kunt de `<appid>` in de `archetype.properties` bestanden van het project.
1. Open de `[AEM Forms as a Cloud Service Git repostory]/ui.config/src/main/content/jcr_root/apps/<appid>/osgiconfig/config/Guide Localization Service.cfg.json` bestand voor bewerking. Als het bestand niet bestaat, maakt u het. Een voorbeeldbestand met ondersteunde landinstellingen ziet er als volgt uit:

   ![Een voorbeeldgids Localization Service.cfg.json](locales.png)

1. Voeg de [landinstellingscode voor de taal](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) u wilt bijvoorbeeld &#39;hi&#39; toevoegen voor hindi.
1. Sla het bestand op en sluit het.

### 3. Maak een clientbibliotheek om een landinstelling toe te voegen

AEM Forms biedt een voorbeeldclientbibliotheek waarmee u eenvoudig nieuwe landinstellingen kunt toevoegen. U kunt de `clientlib-it-custom-locale` clientbibliotheek van de Adaptive Forms Core Components-opslagplaats op GitHub naar uw as a Cloud Service Forms-opslagplaats. Ga als volgt te werk om de clientbibliotheek toe te voegen:

1. Open de Adaptive Forms Core Components-opslagplaats in uw normale teksteditor. Als de repository niet gekloond is, zie [Vereisten](#prerequistes) voor instructies om de gegevensopslagplaats te klonen.
1. Ga naar de `/aem-core-forms-components/it/apps/src/main/content/jcr_root/apps/forms-core-components-it/clientlibs` directory.
1. De `clientlib-it-custom-locale` directory.
1. Navigeren naar `[AEM Forms as a Cloud Service Git repostory]/ui.apps/src/main/content/jcr_root/apps/moonlightprodprogram/clientlibs` en plak de `clientlib-it-custom-locale` directory.


### 4. Maak een bestand dat specifiek is voor de landinstelling {#locale-specific-file}

1. Ga naar `[AEM Forms as a Cloud Service Git repostory]/ui.apps/src/main/content/jcr_root/apps/<program-id>/clientlibs/clientlib-it-custom-locale/resources/i18n/`
1. Zoek de [English locale.json file on GitHub](https://github.com/adobe/aem-core-forms-components/blob/master/ui.af.apps/src/main/content/jcr_root/apps/core/fd/af-clientlibs/core-forms-components-runtime-all/resources/i18n/en.json), die de meest recente set standaardtekenreeksen bevat die in het product zijn opgenomen.
1. Maak een nieuw JSON-bestand voor uw specifieke landinstelling.
1. In het nieuwe .json-bestand weerspiegelt u de structuur van het Engelse landinstellingsbestand.
1. Vervang de Engelse taaltekenreeksen in het JSON-bestand door de overeenkomstige gelokaliseerde tekenreeksen voor uw taal.
1. Sla het bestand op en sluit het.


### 4. Voeg ondersteuning voor landinstellingen toe aan het woordenboek {#add-locale-support-for-the-dictionary}

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

### 5. Leg de veranderingen vast en stel de pijpleiding op {#commit-changes-in-repo-deploy-pipeline}

Leg de wijzigingen vast in de GIT-opslagplaats nadat u een nieuwe ondersteuning voor landinstellingen hebt toegevoegd. Implementeer uw code met de volledige stackpijplijn. Meer informatie [hoe een pijpleiding op te zetten](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=en#setup-pipeline) om nieuwe ondersteuning voor landinstellingen toe te voegen.
Zodra de pijpleiding volledig is, verschijnt de onlangs toegevoegde scène in het AEM milieu.

## Toegevoegde landinstelling gebruiken in Adaptive Forms {#use-added-locale-in-af}

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

Als er geen landinstellingsinformatie beschikbaar is, wordt het adaptieve formulier weergegeven in de oorspronkelijke taal, de taal die tijdens de ontwikkeling wordt gebruikt.

Get [voorbeeldclientbibliotheek](/help/forms/assets/locale-support-sample.zip) om ondersteuning voor nieuwe landinstellingen toe te voegen. U moet de inhoud van de map wijzigen in de vereiste landinstelling.

## Aanbevolen procedures voor ondersteuning van nieuwe lokalisatie {#best-practices}

* Adobe raadt u aan een vertaalproject te maken nadat u een adaptief formulier hebt gemaakt.

* Wanneer nieuwe velden worden toegevoegd aan een bestaand adaptief formulier:
   * **Voor automatische vertaling**: Maak het woordenboek opnieuw en voer het vertaalproject uit. Velden die na het maken van een vertaalproject aan een adaptief formulier zijn toegevoegd, blijven onvertaald.
   * **Voor menselijke vertaling**: Exporteer het woordenboek door `[server:port]/libs/cq/i18n/gui/translator.html`. Werk het woordenboek voor de zojuist toegevoegde velden bij en upload het.
