---
title: Overzicht van de universele editor voor AEM ontwikkelaars
description: Als u een AEM ontwikkelaar bent geïnteresseerd in hoe de Universele Redacteur werkt en hoe te om het in uw project te gebruiken, geeft dit document u een inleiding van begin tot eind door u door het van instrumenten voorzien van instrumenten te leiden het WKND project om met de Universele Redacteur te werken.
exl-id: d6f9ed78-f63f-445a-b354-f10ea37b0e9b
source-git-commit: 0bb649b91c42f43b852d7fdd54b367c0c5df2c99
workflow-type: tm+mt
source-wordcount: '3139'
ht-degree: 0%

---


# Overzicht van de universele editor voor AEM ontwikkelaars {#developer-overview}

Als u een AEM ontwikkelaar bent geïnteresseerd in hoe de Universele Redacteur werkt en hoe te om het in uw project te gebruiken, geeft dit document u een inleiding van begin tot eind door u door het van instrumenten voorzien van instrumenten te leiden het WKND project om met de Universele Redacteur te werken.

## Doel {#purpose}

Dit document fungeert als een inleiding van ontwikkelaars op zowel de manier waarop de Universal Editor werkt als de manier waarop u uw toepassing kunt afstemmen op het werken ermee.

Het doet dit door een standaardvoorbeeld te nemen dat de meeste AEM ontwikkelaars met, de Componenten van de Kern en de plaats WKND vertrouwd zijn, en instrumenten een paar voorbeeldcomponenten om bewerkbaar te zijn gebruikend de Universele redacteur.

>[!TIP]
>
>Dit document neemt extra stappen om te illustreren hoe de Universele Redacteur werkt en is bedoeld om het begrip van de ontwikkelaar van de redacteur te verdiepen. Het is dus niet de meest directe manier om een app van instrumenten te voorzien, maar de meest illustratieve van de Universal Editor en hoe deze werkt.
>
>Als u zo snel mogelijk aan de slag wilt gaan, gelieve te zien [Aan de slag met de Universal Editor in AEM](/help/implementing/universal-editor/getting-started.md) document.

## Vereisten {#prerequisites}

Om dit overzicht te volgen, hebt u het volgende beschikbaar nodig.

* [Een instantie voor lokale ontwikkeling van AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html)
   * Uw lokale ontwikkelingsinstantie moet [geconfigureerd met HTTPS voor ontwikkelingsdoeleinden op `localhost`.](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/use-the-ssl-wizard.html)
   * [De WKND-demosite moet zijn geïnstalleerd.](https://github.com/adobe/aem-guides-wknd)
* [Toegang tot de universele editor](/help/implementing/universal-editor/getting-started.md#onboarding)
* [Een lokale Universal Editor-service](/help/implementing/universal-editor/local-dev.md) uitvoeren voor ontwikkelingsdoeleinden
   * Zorg ervoor dat u de browser naar stuurt [accepteer het zelfondertekende certificaat voor lokale services.](/help/implementing/universal-editor/local-dev.md#editing)

Afgezien van de algemene kennis van webontwikkeling, gaat dit document uit van basiskennis van AEM ontwikkeling. Als u geen ervaring hebt met AEM ontwikkeling, kunt u overwegen om [de WKND-zelfstudie voordat u verdergaat.](/help/implementing/developing/introduction/develop-wknd-tutorial.md)

## AEM starten en aanmelden bij de Universal Editor {#sign-in}

Als u nog niet hebt, moet uw lokale AEM ontwikkelingsinstantie worden uitgevoerd met WKND geïnstalleerd en HTTPS ingeschakeld als [in de vereisten worden beschreven.](#prerequisites) In dit overzicht wordt ervan uitgegaan dat uw instantie wordt uitgevoerd op `https://localhost:8443`.

1. Open de hoofdstramienpagina voor de WKND-Engelse taal in de AEM Editor.

   ```text
   https://localhost:8443/editor.html/content/wknd/language-masters/en.html
   ```

1. In de **Pagina-informatie** menu van de editor, selecteert u **Weergeven als gepubliceerd**. Hierdoor wordt dezelfde pagina op een nieuw tabblad geopend en is de AEM Editor uitgeschakeld.

   ```text
   https://localhost:8443/content/wknd/language-masters/en.html?wcmmode=disabled
   ```

1. Kopieer deze koppeling.

1. Meld u nu aan bij de Universal Editor.

   ```text
   https://experience.adobe.com/#/aem/editor
   ```

1. Plak de koppeling die u eerder van de WKND-inhoud hebt gekopieerd in de **Site-URL** veld van de universele editor en klik op **Openen**.

   ![De WKND-pagina openen in de Universal Editor](assets/dev-ue-open.png)

## De universele editor probeert de inhoud te laden {#sameorigin}

De Universal Editor laadt inhoud die in een frame moet worden bewerkt. AEM standaardinstellingen voor X-Frame-opties verhinderen dit. Dit kan in de browser duidelijk als een fout worden gezien en in de consoleuitvoer worden beschreven wanneer u probeert uw lokale kopie van WKND te laden.

![Browserfout vanwege SAMEORIGIN-optie](assets/dev-sameorigin.png)

De optie X-frame `sameorigin` voorkomt het renderen AEM pagina&#39;s in een frame. U moet deze koptekst verwijderen om de pagina&#39;s te kunnen laden in de Universal Editor.

1. Open de Manager van de Configuratie.

   ```text
   https://localhost:8443/system/console/configMgr
   ```

1. De OSGi-configuratie bewerken `org.apache.sling.engine.impl.SlingMainServlet`

   ![OSGi, eigenschap voor SAMEORIGIN](assets/dev-sameorigin-osgi.png)

1. De eigenschap verwijderen `X-Frame-Options=SAMEORIGIN` van de eigenschap **Aanvullende antwoordheaders**.

1. Sla de wijzigingen op.

Als u nu de Universal Editor opnieuw laadt, ziet u dat de AEM pagina wordt geladen.

>[!TIP]
>
>* Zie het document [Aan de slag met de Universal Editor in AEM](/help/implementing/universal-editor/getting-started.md#sameorigin) voor meer details op deze configuratie OSGi.
>* Zie het document [OSGi configureren voor Adobe Experience Manager as a Cloud Service](/help/implementing/deploying/configuring-osgi.md) voor meer informatie over OSGi in AEM.

## Zelfde sitecookies verwerken {#samesite-cookies}

Wanneer de Universal Editor uw pagina laadt, wordt deze geladen op de AEM aanmeldpagina om ervoor te zorgen dat u geverifieerd bent om wijzigingen aan te brengen.

U kunt zich echter niet aanmelden. Als u de browserconsole weergeeft, ziet u dat de browser invoer in het frame heeft geblokkeerd

![Invoer geblokkeerd](assets/dev-cross-origin.png)

Het inlogtoken-cookie wordt als een extern domein naar AEM verzonden. Daarom moeten cookies op dezelfde locatie in AEM worden toegestaan.

1. Open de Manager van de Configuratie.

   ```text
   https://localhost:8443/system/console/configMgr
   ```

1. De OSGi-configuratie bewerken `com.day.crx.security.token.impl.impl.TokenAuthenticationHandler`

   ![OSGi-eigenschap voor cookies op dezelfde site](assets/dev-cross-origin-osgi.png)

1. De eigenschap wijzigen **Het attribuut SameSite voor het cookie met het token login** tot `None`.

1. Sla de wijzigingen op.

Als u de Universal Editor nu opnieuw laadt, kunt u zich nu aanmelden bij AEM en wordt de doelpagina geladen.

>[!TIP]
>
>* Zie het document [Aan de slag met de Universal Editor in AEM](/help/implementing/universal-editor/getting-started.md#samesite-cookies) voor meer details op deze configuratie OSGi.
>* Zie het document [OSGi configureren voor Adobe Experience Manager as a Cloud Service](/help/implementing/deploying/configuring-osgi.md) voor meer informatie over OSGi in AEM.

## Universele editor maakt verbinding met het externe frame {#ue-connect-remote-frame}

Wanneer de pagina in de Universal Editor is geladen en u zich hebt aangemeld bij AEM, probeert de Universal Editor verbinding te maken met het externe frame. Dit gebeurt via een JavaScript-bibliotheek die in het externe frame moet worden geladen. Als de JavaScript-bibliotheek niet aanwezig is, maakt de pagina uiteindelijk een time-outfout in de console.

![Time-outfout](assets/dev-timeout.png)

U moet de benodigde JavaScript-bibliotheek toevoegen aan de paginacomponent van de WKND-app.

1. Open CRXDE Lite.

   ```text
   https://localhost:8443/crx/de
   ```

1. Onder `/apps/wknd/components/page`, bewerkt u het bestand `customheaderlibs.html`.

   ![Het bestand customheaderlibs.html bewerken](assets/dev-customheaderlibs.png)

1. Voeg de JavaScript-bibliotheek toe aan het einde van het bestand.

   ```html
   <script src="https://universal-editor-service.experiencecloud.live/corslib/LATEST"></script>
   ```

1. Klikken **Alles opslaan** en laad vervolgens de Universal Editor opnieuw.

De pagina wordt nu geladen met de juiste JavaScript-bibliotheek zodat de Universal Editor verbinding kan maken met uw pagina en de time-outfout wordt niet meer weergegeven in de console.

>[!TIP]
>
>* De bibliotheek kan in de kop- of voettekst worden geladen.
>* De `universal-editor-embedded.js` bibliotheek [is beschikbaar op NPM](https://www.npmjs.com/package/@adobe/universal-editor-cors) en u kunt het zelf hosten als dat wordt vereist of het direct in uw toepassing plaatsen.

## Een verbinding definiëren om wijzigingen te behouden {#connection}

De WKND-pagina wordt nu geladen in de Universal Editor en de JavaScript-bibliotheek wordt geladen om de editor te verbinden met uw app.

U ziet waarschijnlijk echter dat u niet kunt communiceren met de pagina in de Universal Editor. De Universal Editor kan uw pagina niet bewerken. Als u wilt dat de Universal Editor uw inhoud kan bewerken, moet u een verbinding definiëren zodat deze weet waar de inhoud moet worden geschreven. Voor lokale ontwikkeling moet u terugschrijven naar uw lokale AEM-ontwikkelingsinstantie op `https://localhost:8443`.

1. Open CRXDE Lite.

   ```text
   https://localhost:8443/crx/de
   ```

1. Onder `/apps/wknd/components/page`, bewerkt u het bestand `customheaderlibs.html`.

   ![Het bestand customheaderlibs.html bewerken](assets/dev-instrument-app.png)

1. Voeg de benodigde metagegevens voor de verbinding met uw lokale AEM-instantie toe aan het einde van het bestand.

   ```html
   <meta name="urn:adobe:aue:system:aem" content="aem:https://localhost:8443">
   ```

   * De nieuwste versie van de bibliotheek wordt altijd aanbevolen. Raadpleeg het document als u een eerdere versie nodig hebt [Aan de slag met de Universal Editor in AEM.](/help/implementing/universal-editor/getting-started.md#alternative)

1. Voeg de vereiste metagegevens toe voor de verbinding met uw lokale Universal Editor-service aan het einde van het bestand.

   ```html
   <meta name="urn:adobe:aue:config:service" content="https://localhost:8000">
   ```

1. Klikken **Alles opslaan** en laad vervolgens de Universal Editor opnieuw.

Nu kan de Universele Redacteur niet alleen uw inhoud met succes van uw lokale AEM ontwikkelingsinstantie laden, maar weet ook waar te om het even welke veranderingen aan te houden u gebruikend uw lokale Universele dienst van de Redacteur aanbrengt. Dit is de eerste stap in het van instrumenten voorzien van uw app om met de Universele Redacteur editable te zijn.

>[!TIP]
>
>* Zie het document [Aan de slag met de Universal Editor in AEM](/help/implementing/universal-editor/getting-started.md#connection) voor meer informatie over de verbindingsmeta-gegevens.
>* Zie het document [Architectuur van Universal Editor](/help/implementing/universal-editor/architecture.md#service) voor meer informatie over de structuur van de Universal Editor.
>* Zie het document [Ontwikkeling van lokale AEM met de Universal Editor](/help/implementing/universal-editor/local-dev.md) voor meer informatie over het maken van een verbinding met een zelfgehoste versie van de Universal Editor.

## Instrumentele onderdelen {#instrumenting-components}

U ziet echter waarschijnlijk dat u nog steeds weinig kunt doen met de Universal Editor. Als u probeert om het gummetje bij de bovenkant van de WKND-pagina in de Universele Redacteur te klikken, kunt u het niet echt selecteren (of iets anders op de pagina).

Uw componenten moeten ook van instrumenten voorzien zijn om met de Universele Redacteur editable te zijn. Hiervoor moet u de lasercomponent bewerken. Daarom moet u de Core Components bedekken aangezien de Componenten van de Kern onder zijn `/libs`, wat onveranderlijk is.

1. Open CRXDE Lite.

   ```text
   https://localhost:8443/crx/de
   ```

1. Selecteer het knooppunt `/libs/core/wcm/components` en klik op **Overlayknooppunt** op de werkbalk.

1. Met `/apps/` geselecteerd als de **Overlay-locatie**, klikt u op **OK**.

   ![Het gummetje bedekken](assets/dev-overlay-teaser.png)

1. Selecteer de `teaser` knooppunt onder `/libs/core/wcm/components` en klik op **Kopiëren** in de werkbalk.

1. Selecteer het bovenliggende knooppunt op `/apps/core/wcm/components` en klik op **Plakken** in de werkbalk.

1. Dubbelklik op het bestand `/apps/core/wcm/components/teaser/v2/teaser/teaser.html` om het te bewerken.

   ![Het bestand teaser.html bewerken](assets/dev-edit-teaser.png)

1. Aan het einde van de eerste `div` Voeg bij ongeveer regel 26 de instrumentdetails voor de component toe.

   ```text
   data-aue-resource="urn:aem:${resource.path}"
   data-aue-type="component"
   data-aue-label="Teaser"
   ```

1. Klikken **Alles opslaan** in de werkbalk en laadt u de Universal Editor opnieuw.

1. Klik in de Universal Editor op de tasercomponent boven aan de pagina en controleer of u deze nu kunt selecteren.

1. Als u op de knop **Inhoudsstructuur** in de eigenschappenrails van de Universal Editor kunt u zien dat de editor alle theaters op de pagina herkende nu u er van hebt voorzien. Het geselecteerde tasje is gemarkeerd.

   ![De met instrumenten gecodeerde lasercomponent selecteren](assets/dev-select-teaser.png)

>[!TIP]
>
>Zie het document [Het gebruiken van de Verzameling van Middel in Adobe Experience Manager as a Cloud Service](/help/implementing/developing/introduction/sling-resource-merger.md) voor meer informatie over het bedekken van knooppunten.

## Instrumentsubcomponenten van de taser {#subcomponents}

U kunt het gummetje nu selecteren, maar nog steeds niet bewerken. Dit komt doordat het gummetje een samenstelling is van verschillende componenten, zoals de component image en title. U moet deze subcomponenten instrumenten om hen uit te geven.

1. Open CRXDE Lite.

   ```text
   https://localhost:8443/crx/de
   ```

1. Selecteer het knooppunt `/apps/core/wcm/components/teaser/v2/teaser/` en dubbelklikt u op de knop `title.html` bestand.

   ![Het bestand title.html bewerken](assets/dev-edit-title.png)

1. Voeg de volgende eigenschappen in aan het einde van het dialoogvenster `h2` tag (nabij regel 17).

   ```text
   data-aue-prop="jcr:title"
   data-aue-type="text"
   data-aue-label="Title"
   ```

1. Klikken **Alles opslaan** in de werkbalk en laadt u de Universal Editor opnieuw.

1. Klik op de titel van dezelfde lasercomponent boven aan de pagina en controleer of u deze nu kunt selecteren. In de inhoudsstructuur wordt de titel ook weergegeven als onderdeel van de geselecteerde tasercomponent.

   ![Titel selecteren binnen de teaser](assets/dev-select-title.png)

U kunt nu de titel van de lasercomponent bewerken!

## Wat betekent het allemaal? {#what-does-it-mean}

Nu u de titel van het gummetje kunt bewerken, nemen we even de tijd om te bekijken wat u hebt bereikt en hoe.

U hebt de lasercomponent geïdentificeerd aan de Universele Redacteur door het van instrumenten te voorzien.

* `data-aue-resource` identificeert de bron in AEM die wordt bewerkt.
* `data-aue-type` definieert dat de items moeten worden behandeld als een paginacomponent (in tegenstelling tot een container).
* `data-aue-label` Hiermee geeft u een gebruiksvriendelijk label in de gebruikersinterface weer voor het geselecteerde taser.

U hebt ook de titelcomponent binnen de teaser component van instrumenten voorzien.

* `data-aue-prop` is het JCR-kenmerk dat wordt geschreven.
* `data-aue-type` Dit is hoe het kenmerk moet worden bewerkt. In dit geval, met de tekstredacteur aangezien het een titel (in tegenstelling tot zeg, de rijke tekstredacteur) is.

## Verificatiekoppen definiëren {#auth-header}

Nu kunt u de titel van het gummetje online bewerken en worden de wijzigingen in de browser doorgevoerd.

![Bewerkte titel van het gummetje](assets/dev-edited-title.png)

Als u de browser echter opnieuw laadt, wordt de vorige titel opnieuw geladen. Hoewel de Universele Redacteur weet hoe te om met uw AEM instantie te verbinden, kan het redacteur aan uw AEM instantie nog niet voor authentiek verklaren om veranderingen in JCR terug te schrijven.

Als u het netwerklusje van de browser ontwikkelaarshulpmiddelen toont en onderzoek naar `update`, ziet u dat er een fout van 401 optreedt wanneer u de titel probeert te bewerken.

![Fout tijdens het bewerken van de titel](assets/dev-edit-error.png)

Wanneer u de Universal Editor gebruikt om uw productie AEM inhoud te bewerken, gebruikt de Universal Editor dezelfde IMS-token die u hebt gebruikt om u aan te melden bij de editor voor verificatie om het schrijven naar de JCR te vergemakkelijken.

Wanneer u zich plaatselijk ontwikkelt, kunt u niet de leverancier van de AEM gebruiken aangezien de tokens IMS slechts aan Adobe-bezeten domeinen worden overgegaan. U moet manueel een manier verstrekken om voor authentiek te verklaren door een authentificatiekopbal uitdrukkelijk te plaatsen.

1. Klik in de interface van de Universal Editor op de knop **Verificatiekoppen** in de werkbalk.

1. Kopieer in de vereiste authentificatiekop om aan uw lokale AEM instantie voor authentiek te verklaren en klik **Opslaan**.

   ![Verificatiekoppen configureren](assets/dev-authentication-headers.png)

1. Laad de Universal Editor opnieuw en bewerk nu de titel van het taser.

Er zijn niet meer om het even welke fouten die in de browser console worden gemeld en de veranderingen worden voortgeduurd terug naar uw lokale AEM ontwikkelingsinstantie.

Als u het verkeer in de browser ontwikkelt hulpmiddelen onderzoekt en zoekt naar `update` voor meer informatie kunt u de details van de update zien.

![De teastitel is bewerkt](assets/dev-edit-title-successfully.png)

```json
{
  "connections": [
    {
      "name": "aem",
      "protocol": "aem",
      "uri": "https://localhost:8443"
    }
  ],
  "target": {
    "resource": "urn:aem:/content/wknd/language-masters/en/jcr:content/root/container/carousel/item_1571954853062",
    "type": "text",
    "prop": "jcr:title"
  },
  "value": "Tiny Toon Adventures"
}
```

* `connections` is de verbinding met uw lokale AEM instantie
* `target` Dit is het exacte knooppunt en de exacte eigenschappen die worden bijgewerkt in het JCR
* `value` Dit is de update die u hebt uitgevoerd.

U kunt zien dat de wijziging aanhoudt in het JCR.

![Bijwerken in het JCR](assets/dev-write-back-jcr.png)

>[!TIP]
>
>Er zijn vele hulpmiddelen beschikbaar online om de noodzakelijke authentificatiekopballen voor uw test en ontwikkelingsdoeleinden te produceren.
>
>Het basisvoorbeeld voor de verificatiekoptekst `Basic YWRtaW46YWRtaW4=` is voor de combinatie gebruiker/wachtwoord van `admin:admin` hetzelfde geldt voor de ontwikkeling van lokale AEM .

## Instrumenteren van de app voor de Properties Rail {#properties-rail}

U hebt nu een app die van instrumenten is voorzien om te kunnen worden bewerkt met de Universal Editor.

Het bewerken is momenteel beperkt tot het online bewerken van de titel van de taser. Er zijn echter gevallen waarin op plaats bewerken niet voldoende is. Tekst zoals de titel van het gummetje kan worden bewerkt op de plaats waar deze zich bevindt met behulp van het toetsenbord. Nochtans moeten de meer gecompliceerde punten kunnen tonen en het uitgeven van gestructureerde gegevens los van hoe het in browser wordt teruggegeven toestaan. Dat is waar de eigenschappen van de spoorwegen voor zijn.

Als u uw app wilt bijwerken zodat de eigenschappencontrole voor bewerking wordt gebruikt, gaat u terug naar het koptekstbestand van de paginacomponent van uw app. Dit is waar u reeds de verbindingen aan uw lokale AEM ontwikkelingsinstantie en uw lokale Universele dienst van de Redacteur vestigde. Hier moet u de componenten definiëren die bewerkbaar zijn in de app en de bijbehorende gegevensmodellen.

1. Open CRXDE Lite.

   ```text
   https://localhost:8443/crx/de
   ```

1. Onder `/apps/wknd/components/page`, bewerkt u het bestand `customheaderlibs.html`.

   ![Het bestand customheaderlibs.html bewerken](assets/dev-instrument-properties-rail.png)

1. Voeg aan het einde van het bestand het script toe dat nodig is om de componenten te definiëren.

   ```html
   <script type="application/vnd.adobe.aue.component+json">
   {
     "groups": [
       {
         "title": "General Components",
         "id": "general",
         "components": [
           {
             "title": "Teaser",
             "id": "teaser",
             "plugins": {
               "aem": {
                 "page": {
                   "resourceType": "wknd/components/teaser"
                 }
               }
             }
           },
           {
             "title": "Title",
             "id": "title",
             "plugins": {
               "aem": {
                 "page": {
                   "resourceType": "wknd/components/title"
                 }
               }
             }
           }
         ]
       }
     ]
   }
   </script>
   ```

1. Hieronder voegt u aan het einde van het bestand het script toe dat nodig is om het model te definiëren.

   ```html
   <script type="application/vnd.adobe.aue.model+json">
   [
     {
       "id": "teaser",
       "fields": [
         {
           "component": "text-input",
           "name": "jcr:title",
           "label": "Title",
           "valueType": "string"
         },
         {
           "component": "text-area",
           "name": "jcr:description",
           "label": "Description",
           "valueType": "string"
         }
       ]
     },
     {
       "id": "title",
       "fields": [
         {
           "component": "select",
           "name": "type",
           "value": "h1",
           "label": "Type",
           "valueType": "string",
           "options": [
             { "name": "h1", "value": "h1" },
             { "name": "h2", "value": "h2" },
             { "name": "h3", "value": "h3" },
             { "name": "h4", "value": "h4" },
             { "name": "h5", "value": "h5" },
             { "name": "h6", "value": "h6" }
           ]
         }
       ]
     }
   ]
   </script>
   ```

1. Klikken **Alles opslaan** in de werkbalk.

## Wat betekent het allemaal? {#what-does-it-mean-2}

Om bewerkbaar te zijn met behulp van de eigenschap rail, moeten de componenten worden toegewezen aan `groups`, dus elke definitie begint als een lijst van groepen die de componenten bevatten.

* `title` is de naam van de groep.
* `id` Dit is de unieke id van de groep, in dit geval algemene componenten die de pagina-inhoud samenstellen in tegenstelling tot bijvoorbeeld geavanceerde componenten voor de pagina-indeling.

Elke groep heeft dan een array van `components`.

* `title` is de naam van de component.
* `id` is de unieke id van de component, in dit geval een teaser.

Elke component heeft dan een insteekmoduledefinitie die bepaalt hoe de component aan AEM in kaart wordt gebracht.

* `aem` Dit is de plug-in die de bewerkingen afhandelt. Dit kan van als dienst worden gedacht die de component verwerkt.
* `page` definieert wat voor soort component het is, in dit geval een standaardpagina-component.
* `resourceType` is de toewijzing aan de daadwerkelijke AEM component.

Elke component moet vervolgens worden toegewezen aan een `model` om de afzonderlijke bewerkbare velden te definiëren.

* `id` is de unieke id van het model, die moet overeenkomen met de id van de component.
* `fields` is een array van de afzonderlijke velden.
* `component` Dit is het type invoer, zoals tekst of tekstgebied.
* `name` Dit is de veldnaam in het JCR waaraan het veld is toegewezen.
* `label` Dit is de beschrijving van het veld dat wordt weergegeven in de gebruikersinterface van de editor.
* `valueType` Dit is het type gegevens.

## Instrumenteren van de component voor de Eigenschapcontrole {#properties-rail-component}

U moet ook definiëren op componentniveau, welk model de component moet gebruiken.

1. Open CRXDE Lite.

   ```text
   https://localhost:8443/crx/de
   ```

1. Dubbelklik op het bestand `/apps/core/wcm/components/teaser/v2/teaser/teaser.html` om het te bewerken.

   ![Het bestand teaser.html bewerken](assets/dev-edit-teaser.png)

1. Aan het einde van de eerste `div` op ongeveer lijn 32, na de eigenschappen u eerder toevoegde, voeg de instrumentatiedetails voor het model toe de teaser component zal gebruiken.

   ```text
   data-aue-model="teaser"
   ```

1. Klikken **Alles opslaan** in de werkbalk en laadt u de Universal Editor opnieuw.

Nu bent u klaar om de eigenschappen spoorstaaf te testen die voor uw component van instrumenten worden voorzien.

1. Klik in de Universal Editor op de titel van het gummetje om deze nogmaals te bewerken.

1. Klik op de eigenschappen-rail om het tabblad Eigenschappen weer te geven en de velden te zien waarop u net van instrumenten hebt voorzien.

   ![De instrumentatieruimte](assets/dev-properties-rail-instrumented.png)

U kunt de titel van de taser nu in line bewerken zoals u eerder had, of in de eigenschappenrails. In beide gevallen worden de wijzigingen doorgevoerd in uw lokale AEM ontwikkelingsexemplaar.

## Extra velden toevoegen aan het vak Eigenschappen {#add-fields}

Met behulp van de basisstructuur van het gegevensmodel voor de component die u al hebt geïmplementeerd, kunt u aanvullende velden toevoegen volgens hetzelfde model.

U kunt bijvoorbeeld een veld toevoegen om de opmaak van de component aan te passen.

1. Open CRXDE Lite.

   ```text
   https://localhost:8443/crx/de
   ```

1. Onder `/apps/wknd/components/page`, bewerkt u het bestand `customheaderlibs.html`.

   ![Het bestand customheaderlibs.html bewerken](assets/dev-instrument-styles.png)

1. In het modeldefinitiescript, voeg een extra punt aan toe `fields` array voor het stijlveld. Vergeet niet na het laatste veld een komma toe te voegen voordat u de nieuwe invoegt.

   ```json
   {
      "component": "select",
      "name": "cq:styleIds",
      "label": "Style",
      "valueType": "string",
        "multi": true,
      "options": [
        {"name": "hero", "value":"1555543212672"},
        {"name": "card", "value":"1605057868937"}
      ]
   }
   ```

1. Klikken **Alles opslaan** in de werkbalk en laadt u de Universal Editor opnieuw.

1. Klik op de titel van het gummetje om deze nogmaals te bewerken.

1. Klik de eigenschappen spoorstaaf en zie dat er een nieuw gebied is om de stijl van de component aan te passen.

   ![De van instrumenten voorziene eigenschappen spoorstaaf met het stijlgebied](assets/dev-style-instrumented.png)

Elk veld in het JCR voor de component kan op deze manier worden weergegeven in de Universal Editor.

## Samenvatting {#summary}

Gefeliciteerd! Nu kunt u uw eigen AEM-apps gebruiken om met de Universal Editor te werken.

Wanneer u uw eigen app van instrumenten begint te voorzien, moet u rekening houden met de basisstappen die u in dit voorbeeld hebt uitgevoerd.

1. [U stelt uw ontwikkelomgeving in.](#prerequisites)
   * AEM die lokaal wordt uitgevoerd op HTTPS terwijl WKND is geïnstalleerd
   * Universal Editor Service die lokaal wordt uitgevoerd op HTTPS
1. U hebt AEM OSGi-instellingen bijgewerkt zodat de inhoud op afstand kan worden geladen.
   * [` org.apache.sling.engine.impl.SlingMainServlet`](#sameorigin)
   * [` com.day.crx.security.token.impl.impl.TokenAuthenticationHandler`](#samesite-cookies)
1. [U hebt de ](#ue-connect-remote-frame)
1. [U hebt een verbinding gedefinieerd om de wijzigingen in het dialoogvenster ](#connection)
   * U hebt een verbinding met de lokale AEM-ontwikkelingsinstantie gedefinieerd.
   * U hebt ook een verbinding met de lokale Universal Editor-service gedefinieerd.
1. [U hebt de teaser-component van instrumenten voorzien.](#instrumenting-components)
1. [U hebt de subcomponenten van het gummetje van instrumenten voorzien.](#subcomponents)
1. [U hebt een aangepaste verificatieheader gedefinieerd zodat u wijzigingen kunt opslaan met uw lokale Universal Editor-service.](#auth-header)
1. [U hebt de app van instrumenten voorzien om de eigenschappen rail te gebruiken.](#properties-rail)
1. [U hebt de teaser-component van instrumenten voorzien om de eigenschappen rail te gebruiken.](#properties-rail-component)

U kunt dezelfde stappen volgen om uw eigen app te gebruiken met de Universal Editor. Alle eigenschappen in het JCR kunnen worden weergegeven in de Universal Editor.

## Aanvullende bronnen {#additional-resources}

Bekijk de volgende documenten voor meer informatie en details over de functies van de Universal Editor.

* Als u zo snel mogelijk aan de slag wilt gaan, gelieve te zien [Aan de slag met de Universal Editor in AEM](/help/implementing/universal-editor/getting-started.md) document.
* Zie het document [Aan de slag met de Universal Editor in AEM](/help/implementing/universal-editor/getting-started.md#sameorigin) voor meer details over de noodzakelijke configuraties OSGi.
* Zie het document [Aan de slag met de Universal Editor in AEM](/help/implementing/universal-editor/getting-started.md#connection) voor meer informatie over de verbindingsmeta-gegevens.
* Zie het document [Architectuur van Universal Editor](/help/implementing/universal-editor/architecture.md#service) voor meer informatie over de structuur van de Universal Editor.
* Zie het document [Ontwikkeling van lokale AEM met de Universal Editor](/help/implementing/universal-editor/local-dev.md) voor meer informatie over het maken van een verbinding met een zelfgehoste versie van de Universal Editor.
* Zie het document [Het gebruiken van de Verzameling van Middel in Adobe Experience Manager as a Cloud Service](/help/implementing/developing/introduction/sling-resource-merger.md) voor meer informatie over het bedekken van knooppunten.
