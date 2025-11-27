---
title: Architectuur van HTML5-formulieren
description: HTML5-formulieren worden geïmplementeerd als een pakket binnen de ingesloten AEM-instantie en geven de functionaliteit weer als REST-eindpunt boven HTTP/S met behulp van RESTful Apache Sling-architectuur.
contentOwner: robhagat
content-type: reference
topic-tags: hTML5_forms
feature: HTML5 Forms,Mobile Forms
exl-id: ed8349a1-f761-483f-9186-bf435899df7d
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
hide: true
hidefromtoc: true
source-git-commit: 1496d7517d586c99c5f1001fff13d88275e91d09
workflow-type: tm+mt
source-wordcount: '1991'
ht-degree: 0%

---

# Architectuur van HTML5-formulieren{#architecture-of-html-forms}

<span class="preview"> De HTML5 Forms-functionaliteit wordt aangeboden als onderdeel van het programma voor vroege toegang. Als u toegang wilt aanvragen, stuurt u een e-mail van uw officiële (werk)e-mailadres naar aem-forms-ea@adobe.com.
</span>

## Architectuur {#architecture}

HTML5 vormenfunctionaliteit wordt opgesteld als pakket binnen de ingebedde instantie van AEM en wordt blootgesteld als eindpunt van REST over HTTP/S gebruikend RESTful [&#x200B; Apache Sling Architecture &#x200B;](https://sling.apache.org/).

![&#x200B; 02-a-a-form-architectuur_large &#x200B;](assets/02-aem-forms-architecture_large.jpg)

### Sling Framework gebruiken {#using-sling-framework}

[&#x200B; Apache Sling &#x200B;](https://sling.apache.org/) is middel-centric. Er wordt een aanvraag-URL gebruikt om de bron eerst op te lossen. Elk middel heeft het bezit van de a **gooien:resourceType** (of **sling:resourceSuperType**). Gebaseerd op dit bezit, de verzoekmethode, en de eigenschappen van het verzoek URL, wordt een sling manuscript dan geselecteerd om het verzoek te behandelen. Dit sling script kan een JSP of een servlet zijn. Voor HTML5 vormen, **de knopen van het 0&rbrace; Profiel &lbrace;dienst als sling middelen en** Renderer van het Profiel **doet dienst als sling manuscript dat het verzoek behandelt om de mobiele vorm met een bepaald profiel terug te geven.** A **Renderer van het Profiel** is JSP die parameters van een verzoek leest en Forms OSGi Service roept.

Voor details op REST eindpunt en gesteunde verzoekparameters, zie [&#x200B; Teruggevend het Malplaatje van de Vorm &#x200B;](/help/forms/rendering-form-template.md).

Wanneer een gebruiker een verzoek indient van een clientapparaat zoals een iOS- of Android™-browser, lost Sling eerst het profielknooppunt op op basis van de aanvraag-URL. Van dit Knoop van Profiel, leest het **sling:resourceSuperType** en **sling:resourceType** om alle beschikbare manuscripten te bepalen die deze Vorm kunnen behandelen geeft verzoek terug. Het gebruikt dan het Verdelen verzoekselecteurs samen met verzoekmethode om het manuscript te identificeren het meest geschikt voor de behandeling van dit verzoek. Zodra het verzoek een Renderer JSP van het Profiel bereikt, roept JSP de dienst Forms OSGi.

Voor meer details bij het sling manuscriptresolutie, zie [&#x200B; AEM het Schuiven het Blad van de Cheat &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions.html?lang=nl-NL) of [&#x200B; Apache het Schuiven Url decomposition &#x200B;](https://sling.apache.org/documentation/the-sling-engine/url-decomposition.html).

#### Typische stroom van de de vraagvraag van de vormverwerking {#typical-form-processing-call-flow}

HTML5-formulieren plaatsen alle tussenliggende objecten in cache die vereist zijn om een formulier op de eerste aanvraag te verwerken (uitvoering of verzending). De objecten die afhankelijk zijn van de gegevens worden niet in het cachegeheugen opgeslagen, omdat dergelijke objecten waarschijnlijk worden gewijzigd.

Mobiel formulier behoudt twee verschillende niveaus van cache, namelijk de PreRender-cache en de Render-cache. Het preRender-cache bevat alle fragmenten en afbeeldingen van een opgeloste sjabloon en het Render-cache bevat gerenderde inhoud, zoals HTML.

![&#x200B; HTML5 vormenwerkschema &#x200B;](assets/cacheworkflow.png)

Workflow voor HTML5-formulieren

In HTML5-formulieren worden geen sjablonen met ontbrekende verwijzingen naar fragmenten en afbeeldingen in de cache opgeslagen. Als HTML5-formulieren meer tijd in beslag nemen dan normaal, controleert u in de serverlogboeken of er ontbrekende verwijzingen en waarschuwingen zijn. Zorg er ook voor dat de maximumgrootte van het object niet wordt bereikt.

De dienst van Forms OSGi verwerkt een verzoek in twee stappen:

* **Lay-out en de Aanvankelijke generatie van de Staat van de Vorm**: Forms OSGi geeft de dienst terug roept de component van het Geheime voorgeheugen van Forms om te bepalen als de vorm reeds in het voorgeheugen ondergebracht is en niet ongeldig is gemaakt. Als het formulier in de cache is opgeslagen en geldig is, wordt het gegenereerde HTML-formulier weergegeven vanuit de cache. Als het formulier ongeldig wordt gemaakt, genereert de Forms OSGi-renderservice de Initial Form Layout and Form State in XML-indeling. Deze XML wordt door de Forms OSGi-service getransformeerd in de HTML-indeling en de initiële JSON-formulierstatus en vervolgens in de cache geplaatst voor volgende aanvragen.
* **Voorbevolkte Forms**: Terwijl het teruggeven, als een gebruiker om vormen met vooraf ingevulde gegevens verzoekt, geeft Forms OSGi de dienstcontainer van Forms terug en produceert een nieuwe staat van de Vorm met samengevoegde gegevens. Nochtans, aangezien de lay-out reeds in de bovengenoemde stap wordt geproduceerd, is deze vraag sneller dan de eerste vraag. Met deze aanroep worden alleen de gegevenssamenvoeging uitgevoerd en worden de scripts op de gegevens uitgevoerd.

Als er een update in het formulier is of een van de elementen die in het formulier worden gebruikt, detecteert de component in de formuliercache dit en wordt de cache voor dat formulier ongeldig gemaakt. Zodra de Forms OSGi-service de verwerking heeft voltooid, voegt de Profile Renderer jsp JavaScript-bibliotheekreferenties en -stijlen toe aan dit formulier en wordt de reactie op de client geretourneerd. Een typische Webserver zoals [&#x200B; Apache &#x200B;](https://httpd.apache.org/) kan hier met de compressie van HTML worden gebruikt. Een webserver zou de responsgrootte, het netwerkverkeer en de tijd die nodig is om de gegevens tussen de server en de clientcomputer te streamen aanzienlijk verminderen.

Wanneer een gebruiker de vorm voorlegt, verzendt browser staat van vorm in formaat JSON naar [&#x200B; voorlegt de dienstvolmacht &#x200B;](/help/forms/service-proxy.md); dan produceert de voorlegt de dienstvolmacht van de dienst een gegevens XML gebruikend gegevens JSON en legt die gegevens XML voor om eindpunt voor te leggen.

## Onderdelen {#components}

U hebt een AEM Forms-add-on-pakket nodig om HTML5-formulieren in te schakelen. Voor informatie over het installeren van het toe:voegen-op pakket van AEM Forms, zie [&#x200B; Installerend en het vormen AEM Forms &#x200B;](/help/forms/setup-local-development-environment.md).

### OSGi-componenten (adobe-lc-forms-core.jar) {#osgi-components-adobe-lc-forms-core-jar}

**Adobe XFA Forms Renderer (com.adobe.livecycle.adobe-lc-forms-core)** is de vertoningsnaam van de HTML5 bundel OSGi van vormen wanneer bekeken van de Bundle Mening van Felix admin console `(https://[host]:[port]/system/console/bundles)`.

Deze component bevat componenten OSGi voor teruggeven, geheim voorgeheugenbeheer, en configuratiemontages.

#### Forms OSGi Service {#forms-osgi-service}

This OSGi Service contains the logic to render an XDP as HTML and handle the submission of a form to generate data XML. Deze service gebruikt Forms-servicecontainer. De Forms-servicecontainer roept intern de native component `XMLFormService.exe` aan die de verwerking uitvoert.

Als een renderverzoek wordt ontvangen, roept deze component de dienstcontainer van Forms aan om lay-out en staatsinformatie te produceren die verder wordt verwerkt om HTML en JSON vorm DOM staten te produceren.

Deze component is ook verantwoordelijk voor het genereren van gegevens-XML van de verzonden formulierstatus JSON.

#### Cache-component {#cache-component}

HTML5-formulieren gebruiken caching om de doorvoer en de responstijd te optimaliseren. U kunt het niveau van de geheim voorgeheugendienst vormen om het compromis tussen prestaties en ruimtegebruik te verfijnen.

<table>
 <tbody>
  <tr>
   <th>Cachestrategie</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td>Geen</td>
   <td>Artefacten niet in cache plaatsen <br /> </td>
  </tr>
  <tr>
   <td>conservatief</td>
   <td>Alleen tussenliggende artefacten opslaan die zijn gegenereerd voordat het formulier wordt gegenereerd, zoals een sjabloon met inline fragmenten en afbeeldingen</td>
  </tr>
  <tr>
   <td>Agressief</td>
   <td>Gerenderde HTML-inhoud in cache plaatsen <br /> Alle artefacten in cache plaatsen op conservatief niveau.<br /> <strong> Nota </strong>: Deze strategie resulteert in beste prestaties maar verbruikt meer geheugen voor het opslaan van de caching artefacten.</td>
  </tr>
 </tbody>
</table>

HTML5-formulieren maken gebruik van LRU-strategie om geheugen in cache te plaatsen. Als de cachestrategie aan niets geheim voorgeheugen wordt geplaatst zal niet worden gecreeerd en de bestaande geheim voorgeheugengegevens, als om het even welk, zouden worden ontruimd. Naast de caching strategie, kunt u de totale grootte van het in-geheugengeheime voorgeheugen ook vormen die in het hebben van het maximum gebonden aan geheim voorgeheugengrootte kan helpen en als het verder gaat dat het wijze LRU zal gebruiken om geheim voorgeheugenmiddelen vrij te maken.

>[!NOTE]
>
>Cache in het geheugen wordt niet gedeeld tussen clusterknooppunten.

#### Configuratieservice {#configuration-service}

De Dienst van de configuratie laat het stemmen van de configuratieparameters en geheim voorgeheugenmontages voor HTML5 vormen toe.

Om deze montages bij te werken, ga naar de Admin Console van de Felix CQ (beschikbaar in https://&lt;&#39;[ server ]:[ haven ]&#39;/system/console/configMgr), onderzoek naar en selecteer de Mobiele Configuratie van Forms.

U kunt de geheim voorgeheugengrootte vormen of het geheime voorgeheugen onbruikbaar maken gebruikend de configuratieservice. U kunt foutopsporing ook inschakelen met de parameter Opties voor foutopsporing. Meer informatie over het zuiveren van vormen kan bij [&#x200B; het Zuiveren HTML5 vormen &#x200B;](/help/forms/debug.md) worden gevonden.

### Runtime Components (adobe-lc-forms-runtime-pkg.zip) {#runtime-components-adobe-lc-forms-runtime-pkg-zip}

Het Runtime-pakket bevat de client-side bibliotheken die worden gebruikt om HTML-formulieren te genereren.

**Belangrijke componenten beschikbaar als deel van Runtime pakket:**

#### Scriptengine {#scripting-engine}

Adobe XFA-implementatie ondersteunt twee soorten scripttalen om door de gebruiker gedefinieerde logische uitvoering in formulieren mogelijk te maken: JavaScript en FormCalc.

De scriptengine van HTML Forms is in JavaScript geschreven ter ondersteuning van de XFA-scripting-API in beide talen.

Tijdens het renderen wordt het FormCalc-script vertaald (en in cache geplaatst) naar JavaScript op de server die transparant is voor de gebruiker of ontwerper.

Deze scriptengine gebruikt een deel van de functie van ECMAScript5, zoals Object.defineProperty. De motor/de bibliotheek wordt geleverd als Bibliotheek van de Cliënt CQ met de categorienaam **xfaforms.profile**. Het verstrekt ook **FormBridge API** om externe portals of apps toe te laten om met vorm in wisselwerking te staan. Met FormBridge kan een externe toepassing via programmacode bepaalde elementen verbergen, de waarden ervan ophalen of instellen of de kenmerken ervan wijzigen.

Voor meer details, zie het [&#x200B; artikel van Bridge van de Vorm 0&rbrace; &lbrace;.](/help/forms/integrate-form-bridge-forms-portal.md)

#### Layout Engine {#layout-engine}

De indeling en visuele aspecten van de HTML5-formulieren zijn gebaseerd op SVG 1.1-, jQuery-, BackBone- en CSS3-functies. De aanvankelijke weergave van een formulier wordt gegenereerd en in cache geplaatst op de server. De aanpassing van de oorspronkelijke indeling en eventuele verdere incrementele wijzigingen in de formulierindeling worden op de client beheerd. Hiertoe bevat het runtimepakket een lay-outengine die in JavaScript is geschreven en is gebaseerd op jQuery/Backbone. Deze motor behandelt al dynamisch gedrag, zoals toevoegen/verwijderen herhaalbare instanties, Growable objecten lay-out. Deze indelingsengine genereert een formulier per pagina. In eerste instantie bekijkt een gebruiker slechts één pagina en de horizontale schuifbalk geldt alleen voor de eerste pagina. Wanneer de gebruiker echter naar beneden schuift, wordt de volgende pagina gestart met de rendering. Deze paginaweergave verkort de tijd die nodig is om de eerste pagina in een browser weer te geven en verbetert de waargenomen prestaties van het formulier. Deze motor/bibliotheek maakt deel uit van de Bibliotheek van de Cliënt CQ met de categorienaam **xfaforms.profile**.

De Layout Engine bevat ook een set widgets die worden gebruikt om de waarde van formuliervelden van een gebruiker vast te leggen. Deze widgets worden gemodelleerd als [&#x200B; jQuery UI Widgets &#x200B;](https://api.jqueryui.com/jQuery.widget/) die bepaalde extra contract uitvoeren om foutloos met de motor van de Lay-out te werken.

Voor meer details op widgets en de overeenkomstige contracten, zie [&#x200B; Douane Widgets voor vormen HTML5 &#x200B;](/help/forms/custom-widgets.md).

#### Stijlen {#styling}

De stijl die aan de HTML-elementen is gekoppeld, wordt inline toegevoegd of gebaseerd op een ingesloten CSS-blok. Sommige veelvoorkomende stijlen die niet afhankelijk zijn van het formulier, maken deel uit van de CQ-clientbibliotheek met de categorienaam xfaforms.profile.

Naast de standaardeigenschappen voor stijlen bevat elk formulierelement ook bepaalde CSS-klassen op basis van het elementtype, de naam en andere eigenschappen. Met deze klassen kunt u elementen opnieuw opmaken door hun eigen CSS op te geven.

Voor meer details op standaard het stileren en klassen, zie [&#x200B; Inleiding aan stijlen &#x200B;](/help/forms/css-styles.md).

#### Server-kant manuscript en de Diensten van het Web {#server-side-script-and-web-services}

Om het even welke manuscripten die duidelijk aan looppas-bij-server of duidelijk zijn om de Dienst van het Web te roepen (ongeacht waar het duidelijk is uit te voeren) voert altijd op server uit.

De clientscriptengine:

1. Maakt een synchrone aanroep naar de server die de huidige formulierstatus doorgeeft in de vorm van JSON
1. Hiermee wordt het script of de webservice op de server uitgevoerd
1. Genereert een nieuwe JSON-status
1. Voegt de nieuwe JSON-status op de client samen wanneer de reactie wordt geretourneerd.

#### Bronnen voor lokalisatie {#localization-resource-bundles}

HTML5-formulieren ondersteunen Italiaans (it), Spaans (es), Braziliaans Portugees (pt_BR), Vereenvoudigd Chinees (zh_CN), Traditioneel Chinees (alleen beperkte ondersteuning) (zh_TW), Koreaans (ko_KR), Engels (en_US), Frans (fr_FR), Duits (de_DE) en Japans (ja). Op basis van de landinstelling die in de aanvraagheader is ontvangen, wordt de corresponderende bronnenbundel naar de client verzonden. Deze middelbundel wordt toegevoegd aan Profiel JSP als Bibliotheek van de Cliënt CQ met categorienaam **xfaforms.I18N**. U kunt de logica negeren om het pakket met landinstellingen in het profiel op te nemen.

### Sling Components (adobe-lc-forms-content-pkg.zip) {#sling-components-adobe-lc-forms-content-pkg-zip}

Het pakket Sling bevat inhoud die gerelateerd is aan profielen en profielrenderer.

#### Profielen {#profiles}

Profielen zijn de bronknooppunten in sling die een formulier of familie van Forms vertegenwoordigen. Op CQ-niveau zijn deze profielen JCR-knooppunten. De knooppunten bevinden zich onder de map **/content** in de JCR-opslagruimte en kunnen zich in elke submap onder de map **/content** bevinden.

#### Profielrenderers {#profile-renderers}

De knoop van het Profiel heeft een bezit **sling:resourceSuperType** met waarde **xfaforms/profiel**. Deze eigenschap verzendt intern aanvragen naar het sling-script voor profielknooppunten in de map **/libs/xfaforms/profile** . Deze scripts zijn JSP-pagina&#39;s, die containers zijn voor het samenstellen van de HTML-formulieren en vereiste JS/CSS-artefacten. De pagina&#39;s bevatten verwijzingen naar:

* **xfaforms.I18N.&lt;locale>**: Deze bibliotheek bevat gelokaliseerde gegevens.
* **xfaforms.profile**: Deze bibliotheek bevat implementatie voor de motor van Scripting XFA en van de Lay-out.

Deze bibliotheken zijn gemodelleerd als CQ-clientbibliotheken die gebruikmaken van de mogelijkheden voor automatische samenvoeging, minificatie en compressie van de JavaScript-bibliotheken van het CQ-framework.
Voor meer informatie over de Bibliotheken van de Cliënt CQ, zie {de Documentatie van de Clientlib van 0} CQ [.](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions.html?lang=nl-NL)

Zoals hierboven beschreven, roept de profielrenderer JSP de Dienst van Forms via het verbinden omvat. Dit JSP plaatst ook diverse zuivert opties die op adminconfiguratie of verzoekparameters worden gebaseerd.

Met HTML5-formulieren kunnen ontwikkelaars Profiel en Profielrenderer maken om de weergave van de formulieren aan te passen. Met HTML-formulieren kunnen ontwikkelaars bijvoorbeeld formulieren integreren in een deelvenster of in een sectie &lt;div> van een bestaande HTML-portal.
Voor meer details bij het creëren van douaneprofielen, zie [&#x200B; Creërend een Profiel van de Douane &#x200B;](/help/forms/custom-profile.md).
