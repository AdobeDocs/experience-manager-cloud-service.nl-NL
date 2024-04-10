---
title: Hoe voeg ik ondersteuning voor nieuwe landinstellingen toe aan een adaptief formulier op basis van kerncomponenten?
description: Leer nieuwe landinstellingen toe te voegen voor een adaptief formulier.
feature: Adaptive Forms, Core Components
exl-id: bc06542b-84c8-4c6a-a305-effbd16d5630
source-git-commit: 559b4afa975dcd2204cd06c95f19ed38da00033e
workflow-type: tm+mt
source-wordcount: '1333'
ht-degree: 0%

---

# Een landinstelling toevoegen voor Adaptive Forms op basis van Core Components {#supporting-new-locales-for-adaptive-forms-localization}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| Elementaire componenten | [Klik hier](supporting-new-language-localization.md) |
| Kernonderdelen | Dit artikel |

<span class="preview"> De ondersteuning voor talen die van rechts naar links worden geschreven, is beschikbaar in het programma voor vroege adoptie. U kunt vanaf uw officiële e-mailadres naar aem-forms-ea@adobe.com schrijven om deel te nemen aan het programma voor vroege adoptie en toegang tot de functie te vragen. </span>

AEM Forms biedt in de box-ondersteuning voor de landinstellingen Engels (en), Spaans (es), Frans (fr), Italiaans (it), Duits (de), Japans (ja), Portugees-Braziliaans (pt-BR), Chinees (zh-CN), Chinees-Taiwan (zh-TW) en Koreaans (ko-KR). U kunt ook ondersteuning toevoegen voor meer landinstellingen, zoals Hindi(hi_IN). U kunt Adaptief Forms ook weergeven in een RTL-taal (rechts naar links), zoals Arabisch, Perzisch en Urdu, door deze landinstellingen toe te voegen.

## Hoe wordt de landinstelling geselecteerd voor een adaptief formulier?

Voordat u een landinstelling toevoegt voor Adaptive Forms, moet u begrijpen hoe een landinstelling is geselecteerd voor een adaptief formulier. Er zijn twee methoden om de landinstelling voor een adaptief formulier te identificeren en te selecteren wanneer het wordt gegenereerd:

* **Met de `locale` Kiezer in de URL**: Bij het genereren van een adaptief formulier identificeert het systeem de aangevraagde landinstelling door de [landinstelling] in de URL van het aangepaste formulier. De URL heeft de volgende notatie: http:/[URL AEM Forms-server]/content/forms/af/[afName].[landinstelling].html?wcmmode=disabled. Het gebruik van [landinstelling] kunt u het adaptieve formulier in cache plaatsen. De URL `www.example.com/content/forms/af/contact-us.hi.html?wcmmmode=disabled` geeft het formulier weer in het Hindi.

* De parameters worden in de onderstaande volgorde opgehaald:

   * **Met de `afAcceptLang`request, parameter**: Als u de landinstelling van de browser van de gebruiker wilt overschrijven, kunt u de aanvraagparameter afAcceptLang doorgeven. Bijvoorbeeld de `https://'[server]:[port]'/<contextPath>/<formFolder>/<formName>.html?wcmmode=disabled&afAcceptLang=ca-fr` URL dwingt AEM Forms Server af om het formulier te genereren in de Canadese Franse landinstelling.

   * **De landinstelling van de browser gebruiken (Koptekst van geaccepteerde taal)**: Het systeem houdt ook rekening met de landinstelling van de browser van de gebruiker, die in de aanvraag is opgegeven met de instelling `Accept-Language` header.

  Als een clientbibliotheek (het proces voor het maken en gebruiken van de bibliotheek wordt verderop in dit artikel behandeld) voor de aangevraagde landinstelling niet beschikbaar is, controleert het systeem of er een clientbibliotheek bestaat voor de taalcode binnen de landinstelling. Als de aangevraagde landinstelling bijvoorbeeld `en_ZA` (Zuid-Afrikaans Engels) en er is geen clientbibliotheek voor `en_ZA`In het Adaptief formulier wordt de clientbibliotheek voor en (Engels) gebruikt, indien beschikbaar. Als geen van beide is gevonden, wordt het adaptieve formulier opnieuw gesorteerd naar het woordenboek voor de `en` landinstelling.

  Als de landinstelling eenmaal is vastgesteld, wordt in het adaptieve formulier het bijbehorende formulierspecifieke woordenboek geselecteerd. Als het woordenboek voor de aangevraagde landinstelling niet wordt gevonden, wordt standaard het woordenboek gebruikt in de taal waarin het adaptieve formulier is gemaakt.

  Als er geen landinstellingsinformatie beschikbaar is, wordt het adaptieve formulier weergegeven in de oorspronkelijke taal, de taal die wordt gebruikt tijdens de ontwikkeling van het formulier


## Vereisten {#prerequistes}

Voordat u een landinstelling toevoegt:

* Installeer een normale tekstverwerker (IDE) voor eenvoudige bewerking. De voorbeelden in dit document zijn gebaseerd op [Microsoft® Visual Studio-code](https://code.visualstudio.com/download).
* Een versie van [Git](https://git-scm.com), indien niet beschikbaar op uw computer.
* Klonen met [Adaptieve Forms Core-componenten](https://github.com/adobe/aem-core-forms-components) opslagplaats. De gegevensopslagruimte klonen:
   1. Open de opdrachtregel of het terminalvenster en navigeer naar een locatie waar u de opslagplaats wilt opslaan. Bijvoorbeeld: `/adaptive-forms-core-components`
   1. Voer de volgende opdracht uit om de gegevensopslagruimte te klonen:

      ```SHELL
          git clone https://github.com/adobe/aem-core-forms-components.git
      ```

  De gegevensopslagruimte bevat een clientbibliotheek die nodig is om een landinstelling toe te voegen.

  Als de opdracht succesvol is uitgevoerd, wordt de opslagplaats gekloond naar de `aem-core-forms-components` op uw computer. In de rest van het artikel wordt de map aangeduid als: [Adaptive Forms Core Components-opslagplaats].


## Een landinstelling toevoegen {#add-localization-support-for-non-supported-locales}

Ga als volgt te werk als u ondersteuning voor een nieuwe landinstelling wilt toevoegen:

![Een landinstelling toevoegen aan een gegevensopslagruimte](add-a-locale-adaptive-form-core-components.png)

### 1. Kloont uw AEM as a Cloud Service Git-opslagplaats {#clone-the-repository}

1. Open de opdrachtregel en kies een directory waarin de as a Cloud Service AEM Forms-opslagplaats moet worden opgeslagen, zoals `/cloud-service-repository/`.

1. Voer de volgende opdracht uit om de gegevensopslagruimte te klonen:

   ```SHELL
   git clone https://git.cloudmanager.adobe.com/<my-org>/<my-program>/
   ```

   Vervangen `<my-org>` en `<my-program>` in de bovenstaande URL met de naam van uw organisatie en het programma. Voor gedetailleerde instructies voor het verkrijgen van de naam van de organisatie, de naam van het programma of het volledige pad van uw Git-opslagplaats en de gegevens die nodig zijn om de opslagplaats te klonen, raadpleegt u [Toegang tot it](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#accessing-git) artikel.

   Na succesvolle voltooiing van bevel, een omslag `<my-program>` wordt gemaakt. Het bevat de inhoud die is gekloond uit de Git-opslagplaats. In de rest van het artikel wordt de map aangeduid als: `[AEM Forms as a Cloud Service Git repository]`.


### 2. Voeg de nieuwe landinstelling toe aan de Guide Localization Service {#add-a-locale-to-the-guide-localization-service}

1. Open de repository map, gekloond in de vorige sectie, in een onbewerkte teksteditor.
1. Ga naar de `[AEM Forms as a Cloud Service Git repository]/ui.config/src/main/content/jcr_root/apps/<appid>/osgiconfig/config` map. U kunt de `<appid>` in de `archetype.properties` bestanden van het project.
1. Open de `[AEM Forms as a Cloud Service Git repository]/ui.config/src/main/content/jcr_root/apps/<appid>/osgiconfig/config/Guide Localization Service.cfg.json` bestand voor bewerking. Als het bestand niet bestaat, maakt u het. Een voorbeeldbestand met ondersteunde landinstellingen ziet er als volgt uit:

   ![Een voorbeeldgids Localization Service.cfg.json](locales.png)

1. Voeg de [landinstellingscode voor de taal](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) u wilt bijvoorbeeld &#39;hi&#39; toevoegen voor hindi.
1. Sla het bestand op en sluit het.

### 3. Maak een clientbibliotheek om een landinstelling toe te voegen

AEM Forms biedt een voorbeeldclientbibliotheek waarmee u eenvoudig nieuwe landinstellingen kunt toevoegen. U kunt de `clientlib-it-custom-locale` clientbibliotheek van de [Adaptive Forms Core Components-opslagplaats] op GitHub naar uw as a Cloud Service opslagplaats van Forms. Ga als volgt te werk om de clientbibliotheek toe te voegen:

1. Open uw [Adaptive Forms Core Components-opslagplaats] in de teksteditor zonder opmaak. Als de repository niet gekloond is, zie [Vereisten](#prerequistes) voor instructies om de gegevensopslagplaats te klonen.
1. Ga naar de `/aem-core-forms-components/it/apps/src/main/content/jcr_root/apps/forms-core-components-it/clientlibs` directory.
1. De `clientlib-it-custom-locale` directory.
1. Navigeren naar `[AEM Forms as a Cloud Service Git repository]/ui.apps/src/main/content/jcr_root/apps/moonlightprodprogram/clientlibs` en plak de `clientlib-it-custom-locale` directory.


### 4. Maak een bestand dat specifiek is voor de landinstelling {#locale-specific-file}

1. Navigeren naar `[AEM Forms as a Cloud Service Git repository]/ui.apps/src/main/content/jcr_root/apps/<program-id>/clientlibs/clientlib-it-custom-locale/resources/i18n/`
1. Zoek de [English locale.json file on GitHub](https://github.com/adobe/aem-core-forms-components/blob/master/ui.af.apps/src/main/content/jcr_root/apps/core/fd/af-clientlibs/core-forms-components-runtime-all/resources/i18n/en.json), die de meest recente set standaardtekenreeksen bevat die in het product zijn opgenomen.
1. Maak een .json-bestand voor uw specifieke landinstelling.
1. In het nieuwe .json-bestand weerspiegelt u de structuur van het Engelse landinstellingsbestand.
1. Vervang de Engelse taaltekenreeksen in het JSON-bestand door de overeenkomstige gelokaliseerde tekenreeksen voor uw taal.
1. Sla het bestand op en sluit het.


### 5. Voeg ondersteuning voor landinstellingen toe aan het woordenboek {#add-locale-support-for-the-dictionary}

Voer deze stap alleen uit als de `<locale>` u toevoegt behoort niet tot `en`, `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja`, `ko-kr`.

1. Ga naar de `[AEM Forms as a Cloud Service Git repository]/ui.content/src/main/content/jcr_root/etc/` map.

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

   ![Voeg de gemaakte mappen toe aan het dialoogvenster `filter.xml` krachtens `/ui.content/src/main/content/meta-inf/vault/filter.xml`](langauge-filter.png)

### 6. Leg de veranderingen vast en stel de pijpleiding op {#commit-changes-in-repo-deploy-pipeline}

Breng de wijzigingen aan in de GIT-opslagplaats nadat u de nieuwe landinstelling hebt toegevoegd. Implementeer uw code met de volledige stackpijplijn. Meer informatie [hoe een pijpleiding op te zetten](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=en#setup-pipeline) om nieuwe ondersteuning voor landinstellingen toe te voegen.

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

## Aanbevolen procedures voor ondersteuning van nieuwe lokalisatie {#best-practices}

* Adobe raadt u aan een vertaalproject te maken nadat u een adaptief formulier hebt gemaakt.

* Wanneer nieuwe velden worden toegevoegd aan een bestaand adaptief formulier:
   * **Voor automatische vertaling**: Maak het woordenboek opnieuw en [het vertaalproject uitvoeren](/help/forms/using-aem-translation-workflow-to-localize-adaptive-forms-core-components.md). Velden die na het maken van een vertaalproject aan een adaptief formulier zijn toegevoegd, blijven onvertaald.
   * **Voor menselijke vertaling**: Exporteer het woordenboek met de gebruikersinterface op `[AEM Forms Server]/libs/cq/i18n/gui/translator.html`. Werk het woordenboek voor de zojuist toegevoegde velden bij en upload het.

## Meer weergeven

* [Opnamedocument genereren voor Adaptive Forms](/help/forms/generate-document-of-record-core-components.md)
* [Een adaptief formulier toevoegen aan een AEM Sites-pagina of Ervaar fragment](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)


## Zie ook {#see-also}

{{see-also}}