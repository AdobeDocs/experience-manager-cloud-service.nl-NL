---
title: Een aangepaste component voor Screens as a Cloud Service ontwikkelen
description: De volgende zelfstudie doorloopt de stappen om een aangepaste component voor AEM Screens te maken. AEM Screens gebruikt veel bestaande ontwerppatronen en technologieën van andere AEM-producten opnieuw. In de zelfstudie worden verschillen en speciale overwegingen benadrukt bij het ontwikkelen voor AEM Screens.
exl-id: fe8e7bf2-6828-4a5a-b650-fb3d9c172b97
feature: Developing Screens
role: Admin, Developer, User
source-git-commit: 1179e45f6e75a8a4f5e5e76903243f64d9f406ae
workflow-type: tm+mt
source-wordcount: '2039'
ht-degree: 0%

---

# Een aangepaste component voor AEM Screens as a Cloud Service ontwikkelen{#developing-a-custom-component-for-aem-screens}

De volgende zelfstudie doorloopt de stappen om een aangepaste component voor AEM Screens te maken. AEM Screens gebruikt veel bestaande ontwerppatronen en technologieën van andere AEM-producten opnieuw. In de zelfstudie worden verschillen en speciale overwegingen benadrukt bij het ontwikkelen voor AEM Screens.

## Overzicht {#overview}

Deze zelfstudie is bedoeld voor nieuwe ontwikkelaars van AEM Screens. In deze zelfstudie wordt een eenvoudige component &quot;Hello World&quot; gemaakt voor een volgnummer in AEM Screens. In een dialoogvenster kunnen auteurs de weergegeven tekst bijwerken.


## Vereisten {#prerequisites}

U hebt het volgende nodig om deze zelfstudie te voltooien:

1. Nieuwste Screens-functiepakket

1. AEM Screens Player

1. Lokale ontwikkelomgeving

De stappen en de schermafbeeldingen van het leerprogramma worden uitgevoerd gebruikend **CRXDE Lite**. IDEs kan ook worden gebruikt om het leerprogramma te voltooien. Meer informatie bij het gebruiken van winde om [ met AEM te ontwikkelen kan hier ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/project-archetype/project-setup.html?lang=nl-NL) worden gevonden.


## Projectinstelling {#project-setup}

De broncode van een Screens-project wordt doorgaans beheerd als een Maven-project met meerdere modules. Om het leerprogramma te versnellen, werd een project pre-geproduceerd gebruikend [ Archetype 13 van het Project van AEM ](https://github.com/adobe/aem-project-archetype). Zie [ Opstelling van het Project ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/project-archetype/project-setup.html?lang=nl-NL) voor meer details bij het creëren van een project met Maven het Archetype van het Project van AEM.

1. Download en installeer de volgende pakketten gebruikend [ Manager van het Pakket van CRX ](http://localhost:4502/crx/packmgr/index.jsp):

[Bestand ophalen](/help/screens-cloud/developing/assets/base-screens-weretail-runuiapps-001-snapshot.zip)

   [ krijgt Dossier ](/help/screens-cloud/developing/assets/base-screens-weretail-runuiapps-001-snapshot.zip)
   **naar keuze** als het werken met Verduistering of een andere winde het hieronder bronpakket downloadt. Implementeer het project in een lokale AEM-instantie met de opdracht Maven:

   **`mvn -PautoInstallPackage clean install`**

   HelloWorld SRC Screens Web.Retail Run Project starten

[Bestand ophalen](/help/screens-cloud/developing/assets/src-screens-weretail-run.zip)

1. In [ de Manager van het Pakket van CRX ](http://localhost:4502/crx/packmgr/index.jsp), verifieer dat de volgende twee pakketten geïnstalleerd zijn:

   1. **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip**
   1. **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip**

   ![ Screens Wij.Retail de pakketten van de Looppas Ui.Apps en Ui.Content die via de Manager van het Pakket van CRX worden geïnstalleerd ](assets/crx-packages.png)

   Screens Web.Retail Run UI.Apps en Ui.Content pakketten geïnstalleerd via CRX Package Manager

1. Het **screens-weretail-run.ui.apps** pakket installeert code onder `/apps/weretail-run`.

   Dit pakket bevat de code die verantwoordelijk is voor het renderen van aangepaste componenten voor het project. Dit pakket bevat componentcode en eventueel benodigde JavaScript of CSS. Dit pakket sluit ook **schermen-weretail-run.core-0.0.1-SNAPSHOT.jar** in die om het even welke code Java™ bevat nodig door het project.

   >[!NOTE]
   >
   >In deze zelfstudie wordt geen Java™-code geschreven. Als complexere bedrijfslogica nodig is, kan back-end Java™ worden gemaakt en geïmplementeerd met de Core Java™-bundel.

   ![ Vertegenwoordiging van de code ui.apps in CRXDE Lite ](/help/screens-cloud/developing/assets/uipps-contents.png)

   Weergave van de code ui.apps in CRXDE Lite

   De component **`helloworld`** is slechts een plaatsaanduiding. Tijdens de zelfstudie wordt functionaliteit toegevoegd waarmee een auteur het bericht kan bijwerken dat door de component wordt weergegeven.

1. Het **screens-weretail-run.ui.content** pakket installeert code onder:

   * `/conf/we-retail-run`
   * `/content/dam/we-retail-run`
   * `/content/screens/we-retail-run`

   Dit pakket bevat de eerste inhoud en configuratiestructuur die nodig zijn voor het project. **`/conf/we-retail-run`** bevat alle configuraties voor het Web.Retail-project Run. **`/content/dam/we-retail-run`** bevat startende digitale elementen voor het project. **`/content/screens/we-retail-run`** bevat de Screens-inhoudsstructuur. De inhoud onder deze paden wordt voornamelijk in AEM bijgewerkt. Om de consistentie tussen omgevingen (lokaal, Ontwikkelen, Stage, Prod) te bevorderen, wordt vaak een basisinhoudsstructuur opgeslagen in bronbeheer.

1. **navigeer aan AEM Screens > Wij.Retail project van de Looppas:**

   Kies AEM Global Navigation > Click the Screens the icon. Verifieer het Web.Retail Project van de Looppas kan worden gezien.

   ![ wij-detailul-looppas-starter ](/help/screens-cloud/developing/assets/we-retaiul-run-starter.png)

## De Hello World-component maken {#hello-world-cmp}

De component Hello World is een eenvoudige component waarmee een gebruiker een bericht kan invoeren dat op het scherm moet worden weergegeven. De component is gebaseerd op het [ Malplaatje van de Component van AEM Screens: https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template).

AEM Screens heeft sommige interessante beperkingen die niet noodzakelijk waar voor traditionele componenten van Plaatsen WCM zijn.

* De meeste Screens-componenten moeten op volledig scherm worden uitgevoerd op de doelapparaten voor digitale handtekeningen
* De meeste Screens-componenten moeten in de volgordekanalen zijn ingesloten om presentaties te kunnen genereren
* Authoring moet het mogelijk maken afzonderlijke componenten te bewerken in een volgnummer, zodat het weergeven ervan op volledig scherm niet meer mogelijk is

1. In **CRXDE-Lite** `http://localhost:4502/crx/de/index.jsp` (of winde van keus), navigeer aan `/apps/weretail-run/components/content/helloworld.`

   Voeg de volgende eigenschappen toe aan de component `helloworld` :

   ```
       jcr:title="Hello World"
       sling:resourceSuperType="foundation/components/parbase"
       componentGroup="We.Retail Run - Content"
   ```

   ![ Eigenschappen voor /apps/weretail-run/components/content/helloworld ](/help/screens-cloud/developing/assets/2018-04-28_at_4_23pm.png)

   Eigenschappen voor /apps/weretail-run/components/content/helloworld

   De **`helloworld`** component breidt de **stichting/componenten/parbase** component uit zodat kan het behoorlijk binnen een opeenvolgingskanaal worden gebruikt.

1. Een bestand maken onder de naam `/apps/weretail-run/components/content/helloworld` `helloworld.html.`

   Vul het bestand met het volgende:

   ```xml
   <!--/*
   
    /apps/weretail-run/components/content/helloworld/helloworld.html
   
   */-->
   
   <!--/* production: preview authoring mode + unspecified mode (that is, on publish) */-->
   <sly data-sly-test.production="${wcmmode.preview || wcmmode.disabled}" data-sly-include="production.html" />
   
   <!--/* edit: any other authoring mode, that is, edit, design, scaffolding, and so on. */-->
   <sly data-sly-test="${!production}" data-sly-include="edit.html" />
   ```

   De componenten van Screens vereisen twee verschillende teruggaven afhankelijk van welke [ auteurswijze ](https://experienceleague.adobe.com/docs/experience-manager-64/authoring/authoring/author-environment-tools.html?lang=nl-NL#page-modes) wordt gebruikt:

   1. **Productie**: Voorproef of publiceer wijze (wcmmode=disabled)
   1. **geeft** uit: gebruikt voor alle andere auteurswijzen, namelijk uitgeven, ontwerp, steigers, ontwikkelaar...

   `helloworld.html` doet dienst als schakelaar, die welke auteurswijze actief is en aan een ander manuscript opnieuw richt HTML controleert. Schermcomponenten worden vaak gebruikt met een `edit.html` -script voor de bewerkingsmodus en een `production.html` -script voor de productiemodus.

1. Een bestand maken onder de naam `/apps/weretail-run/components/content/helloworld` `production.html.`

   Vul het bestand met het volgende:

   ```xml
   <!--/*
    /apps/weretail-run/components/content/helloworld/production.html
   
   */-->
   
   <div data-duration="${properties.duration}" class="cmp-hello-world">
    <h1 class="cmp-hello-world__message">${properties.message}</h1>
   </div>
   ```

   De productiemarkering hierboven is voor de Component van de Wereld van Hello. Een attribuut `data-duration` wordt opgenomen aangezien de component op een kanaal van de Opeenvolging wordt gebruikt. Het attribuut `data-duration` wordt gebruikt door het opeenvolgingskanaal om te weten hoe lang een opeenvolgingspunt moet worden getoond.

   De component rendert een `div` - en een `h1` -tag met tekst. `${properties.message}` is een deel van het HTML-script dat de inhoud van een JCR-eigenschap met de naam `message` uitvoert. Later wordt een dialoogvenster gemaakt waarin een gebruiker een waarde voor de eigenschapstekst `message` kan invoeren.

   Merk ook op dat BEM-notatie (Block Element Modifier) wordt gebruikt met de component. BEM is een CSS-coderingsconventie die het gemakkelijker maakt om herbruikbare componenten te maken. BEM is de aantekening die door [ wordt gebruikt de Componenten van de Kern van AEM ](https://github.com/adobe/aem-core-wcm-components/wiki/CSS-coding-conventions). <!-- WEBSITE WAS NOT ACCESSIBLE AS OF SEPTEMBER 1, 2022 More info can be found at: [https://getbem.com/](https://getbem.com/) -->

1. Een bestand maken onder de naam `/apps/weretail-run/components/content/helloworld` `edit.html.`

   Vul het bestand met het volgende:

   ```xml
   <!--/*
   
    /apps/weretail-run/components/content/helloworld/edit.html
   
   */-->
   
   <!--/* if message populated */-->
   <div
    data-sly-test.message="${properties.message}"
    class="aem-Screens-editWrapper cmp-hello-world">
    <p class="cmp-hello-world__message">${message}</p>
   </div>
   
   <!--/* empty place holder */-->
   <div data-sly-test="${!message}"
        class="aem-Screens-editWrapper cq-placeholder cmp-hello-world"
        data-emptytext="${'Hello World' @ i18n, locale=request.locale}">
   </div>
   ```

   De bovenstaande bewerkingsmarkering is voor de Hello World-component. In het eerste blok wordt een bewerkingsversie van de component weergegeven als het dialoogvenster is gevuld.

   Het tweede blok wordt teruggegeven als geen dialoogdoos is ingegaan. `cq-placeholder` en `data-emptytext` geven de etiket ***Wereld van Hello*** als plaatsaanduiding in dat geval terug. De tekenreeks voor het label kan met i18n worden geïnternationaliseerd ter ondersteuning van ontwerpen in meerdere landinstellingen.

1. **de Dialoogvenster van het Beeld van Screens van het Exemplaar dat voor de component van de Wereld van Hello moet worden gebruikt.**

   Het is het gemakkelijkst om van een bestaande dialoog te beginnen en dan wijzigingen te maken.

   1. Het dialoogvenster kopiëren van: `/libs/screens/core/components/content/image/cq:dialog`
   1. Het dialoogvenster onder plakken `/apps/weretail-run/components/content/helloworld`

   ![ exemplaar-beeld-dialoog ](/help/screens-cloud/developing/assets/copy-image-dialog.gif)

1. **Update de dialoog van de Wereld van Hello om een lusje voor bericht te omvatten.**

   Werk het dialoogvenster bij, zodat dit overeenkomt met het volgende. De JCR-knooppuntstructuur van het laatste dialoogvenster wordt hieronder weergegeven in XML:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0" xmlns:nt="https://www.jcp.org/jcr/nt/1.0"
       jcr:primaryType="nt:unstructured"
       jcr:title="Hello World"
       sling:resourceType="cq/gui/components/authoring/dialog">
       <content
           jcr:primaryType="nt:unstructured"
           sling:resourceType="granite/ui/components/coral/foundation/tabs"
           size="L">
           <items jcr:primaryType="nt:unstructured">
               <message
                   jcr:primaryType="nt:unstructured"
                   jcr:title="Message"
                   sling:resourceType="granite/ui/components/coral/foundation/fixedcolumns">
                   <items jcr:primaryType="nt:unstructured">
                       <column
                           jcr:primaryType="nt:unstructured"
                           sling:resourceType="granite/ui/components/coral/foundation/container">
                           <items jcr:primaryType="nt:unstructured">
                               <message
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/coral/foundation/form/textfield"
                                   fieldDescription="Message for component to display"
                                   fieldLabel="Message"
                                   name="./message"/>
                           </items>
                       </column>
                   </items>
               </message>
               <sequence
                   jcr:primaryType="nt:unstructured"
                   jcr:title="Sequence"
                   sling:resourceType="granite/ui/components/coral/foundation/fixedcolumns">
                   <items jcr:primaryType="nt:unstructured">
                       <column
                           jcr:primaryType="nt:unstructured"
                           sling:resourceType="granite/ui/components/coral/foundation/container">
                           <items jcr:primaryType="nt:unstructured">
                               <duration
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/coral/foundation/form/numberfield"
                                   defaultValue=""
                                   fieldDescription="Amount of time the image is shown in the sequence, in milliseconds"
                                   fieldLabel="Duration (ms)"
                                   min="0"
                                   name="./duration"/>
                           </items>
                       </column>
                   </items>
               </sequence>
           </items>
       </content>
   </jcr:root>
   ```

   De waarde `textfield` voor het bericht wordt opgeslagen naar een eigenschap met de naam `message` en de waarde `numberfield` voor de duur wordt opgeslagen naar een eigenschap met de naam `duration` . In `/apps/weretail-run/components/content/helloworld/production.html` door HTML wordt naar deze twee eigenschappen verwezen als `${properties.message}` en `${properties.duration}` .

   ![ de Wereld van Hello - voltooide dialoogdoos ](/help/screens-cloud/developing/assets/2018-04-29_at_5_21pm.png)

   Hello World - dialoogvenster voltooid

## Client-Side bibliotheken maken {#clientlibs}

Client-Side Libraries bieden een mechanisme voor het organiseren en beheren van CSS- en JavaScript-bestanden die nodig zijn voor een AEM-implementatie.

AEM Screens-componenten worden in de bewerkingsmodus anders weergegeven dan in de modus Voorbeeld/productie. Er worden twee clientbibliotheken gemaakt: een voor de bewerkingsmodus en een voor Voorvertoning/Productie.

1. Maak een map voor client-side bibliotheken voor de component Hello World.

   Onder `/apps/weretail-run/components/content/helloworld` maakt u een map met de naam `clientlibs` .

   ![ 2018-04-30_at_1046am ](/help/screens-cloud/developing/assets/2018-04-30_at_1046am.png)

1. Onder de map `clientlibs` maakt u een knooppunt met de naam `shared` of type `cq:ClientLibraryFolder.` .

   ![ 2018-04-30_at_1115am ](/help/screens-cloud/developing/assets/2018-04-30_at_1115am.png)

1. Voeg de volgende eigenschappen toe aan de gedeelde clientbibliotheek:

   * `allowProxy` | Boolean | `true`

   * `categories`| String [] | `cq.screens.components`

   ![ Eigenschappen voor /apps/weretail-run/components/content/helloworld/clientlibs/shared ](/help/screens-cloud/developing/assets/2018-05-03_at_1026pm.png)

   Eigenschappen voor /apps/weretail-run/components/content/helloworld/clientlibs/shared

   De eigenschap category is een tekenreeks die de clientbibliotheek identificeert. De categorie cq.screens.component wordt gebruikt in zowel de modus Bewerken als de modus Voorbeeld/productie. Daarom wordt elke CSS/JS die in de sharedclientLib is gedefinieerd, in alle modi geladen.

   Het is aan te raden geen paden in een productieomgeving rechtstreeks toegankelijk te maken voor /apps. De eigenschap allowProxy zorgt ervoor dat naar de CSS- en JS-client-bibliotheek wordt verwezen door middel van het voorvoegsel of/etc.clientlibs.

1. Maak een bestand met de naam `css.txt` onder de gedeelde map.

   Vul het bestand met het volgende:

   ```
   #base=css
   
   styles.less
   ```

1. Maak een map met de naam `css` onder de map `shared` . Voeg een bestand met de naam `style.less` toe onder de map `css` . De structuur van de clientbibliotheken moet er nu als volgt uitzien:

   ![ 2018-04-30_at_3_11pm ](/help/screens-cloud/developing/assets/2018-04-30_at_3_11pm.png)

   In plaats van CSS rechtstreeks te schrijven, gebruikt deze zelfstudie LESS. [ LESS ](https://lesscss.org/) is populaire CSS pre-compiler die CSS variabelen, mixins, en functies steunt. AEM-clientbibliotheken bieden native ondersteuning voor LESS-compilatie. Sassa&#39;s of andere voorcompilers kunnen worden gebruikt, maar moeten buiten AEM worden samengesteld.

1. Vul `/apps/weretail-run/components/content/helloworld/clientlibs/shared/css/styles.less` met het volgende:

   ```css
   /**
       Shared Styles
      /apps/weretail-run/components/content/helloworld/clientlibs/shared/css/styles.less
   
   **/
   
   .cmp-hello-world {
       background-color: #fff;
   
    &__message {
     color: #000;
     font-family: Helvetica;
     text-align:center;
    }
   }
   ```

1. Kopieer en plak de clientbibliotheekmap van `shared` om een clientbibliotheek met de naam `production` te maken.

   ![ Kopieer de gedeelde cliëntbibliotheek om een bibliotheek van de productiecliënt tot stand te brengen ](/help/screens-cloud/developing/assets/copy-clientlib.gif)

   Kopieer de gedeelde clientbibliotheek om een productieclientbibliotheek te maken.

1. Werk de eigenschap `categories` van de productiekatentbibliotheek bij als `cq.screens.components.production.`

   Zo zorgt u ervoor dat de stijlen alleen worden geladen in de modus Voorbeeld/productie.

   ![ Eigenschappen voor /apps/weretail-run/components/content/helloworld/clientlibs/production ](/help/screens-cloud/developing/assets/2018-04-30_at_5_04pm.png)

   Eigenschappen voor /apps/weretail-run/components/content/helloworld/clientlibs/production

1. Vul `/apps/weretail-run/components/content/helloworld/clientlibs/production/css/styles.less` met het volgende:

   ```css
   /**
       Production Styles
      /apps/weretail-run/components/content/helloworld/clientlibs/production/css/styles.less
   
   **/
   .cmp-hello-world {
   
       height: 100%;
       width: 100%;
       position: fixed;
   
    &__message {
   
     position: relative;
     font-size: 5rem;
     top:25%;
    }
   }
   ```

   Bij de bovenstaande stijlen wordt het bericht gecentreerd weergegeven in het midden van het scherm, maar alleen in de productiemodus.

Een derde clientbibliotheekcategorie: `cq.screens.components.edit` kan worden gebruikt om alleen-bewerkingsstijlen toe te voegen aan de component.

| Clientlib-categorie | Gebruik |
|---|---|
| `cq.screens.components` | Stijlen en scripts die worden gedeeld tussen de bewerkings- en de productiemodus |
| `cq.screens.components.edit` | Stijlen en scripts die alleen worden gebruikt in de bewerkingsmodus |
| `cq.screens.components.production` | Stijlen en scripts die alleen in de productiemodus worden gebruikt |

## Een ontwerppagina maken {#design-page}

AEM Screens gebruikt [ statische Malplaatjes van de Pagina ](https://experienceleague.adobe.com/docs/experience-manager-65/developing/platform/templates/page-templates-static.html?lang=nl-NL) en [ configuraties van het Ontwerp ](https://experienceleague.adobe.com/docs/experience-manager-64/authoring/siteandpage/default-components-designmode.html?lang=nl-NL) voor globale veranderingen. De configuraties van het ontwerp worden vaak gebruikt om toegestane componenten voor Parsys op een kanaal te vormen. U kunt deze configuraties het beste op een toepassingsspecifieke manier opslaan.

Een Web.Retail pagina van het Ontwerp van de Looppas wordt gecreeerd hieronder die alle configuraties specifiek voor het Web.Retail project van de Looppas opslaat.

1. In **CRXDE Lite** `http://localhost:4502/crx/de/index.jsp#/apps/settings/wcm/designs`, navigeer aan `/apps/settings/wcm/designs`
1. Maak een knooppunt onder de map designs met de naam `we-retail-run` met het type `cq:Page` .
1. Voeg onder de pagina `we-retail-run` een ander knooppunt met de naam `jcr:content` van het type `nt:unstructured` toe. Voeg de volgende eigenschappen toe aan het knooppunt `jcr:content` :

   | Naam | Type | Waarde |
   |---|---|---|
   | jcr :title | String | We.Retail Run |
   | sling :resourceType | String | wcm/core/components/ontwerper |
   | cq:doctype | String | html_5 |

   ![ Pagina van het Ontwerp bij /apps/settings/wcm/designs/wij-retail-run ](/help/screens-cloud/developing/assets/2018-05-07_at_1219pm.png)

   Ontwerppagina op /apps/settings/wcm/designs/we-Retail-run

## Een volgend kanaal maken {#create-sequence-channel}

De Hello World-component is bedoeld voor gebruik op een Volgekanaal. Om de component te testen, wordt een nieuw Kanaal van de Opeenvolging gecreeerd.

1. Van de Globale Navigatie van AEM, navigeer aan **Screens** > **Wij.Retail Ru** n > en selecteer **Kanalen**.

1. Klik **creëren** knoop

   1. Kies **tot Entiteit** leiden

   ![ 2018-04-30_at_5_18pm ](/help/screens-cloud/developing/assets/2018-04-30_at_5_18pm.png)

1. In de wizard Maken:

1. De Stap van het malplaatje - kies **Kanaal van de Reeks 0&rbrace;**

   1. Eigenschappenstap

   * Basis Lusje > Titel = **Onactief Kanaal**
   * Het Lusje van het kanaal > controle **maakt kanaal online**

   ![ nutteloos-kanaal ](/help/screens-cloud/developing/assets/idle-channel.gif)

1. Open de pagina-eigenschappen voor het onactieve kanaal. Werk het gebied van het Ontwerp bij zodat richt het aan `/apps/settings/wcm/designs/we-retail-run,` de ontwerppagina die in de vorige sectie wordt gecreeerd.

   ![ Ontwerp config /apps/settings/wcm/designs/wij-retail-run ](/help/screens-cloud/developing/assets/2018-05-07_at_1240pm.png)

   Ontwerpconfiguratie die wijst naar /apps/settings/wcm/designs/we-retail-run

1. Bewerk het gemaakte onactieve kanaal zodat u het kunt openen.

1. Schakelaar de paginamodus aan **Wijze van het Ontwerp**.

   1. Klik het **moersleutel** Pictogram in Parsys zodat kunt u de toegestane componenten vormen.

   1. Selecteer de **Screens** groep en **Wij.Retail looppas - de groep van de Inhoud**.

   ![ 2018-04-30_at_5_43pm ](assets/2018-04-30_at_5_43pm.png)

1. Schakelaar de paginamodus aan **geeft** uit. De component Hello World kan nu aan de pagina worden toegevoegd en met andere componenten van het opeenvolgingskanaal worden gecombineerd.

   ![ 2018-04-30_at_5_53pm ](assets/2018-04-30_at_5_53pm.png)

1. In **CRXDE Lite** `http://localhost:4502/crx/de/index.jsp#/apps/settings/wcm/designs/we-retail-run/jcr%3Acontent/sequencechannel/par`, navigeer aan `/apps/settings/wcm/designs/we-retail-run/jcr:content/sequencechannel/par`. De eigenschap `components` bevat nu `group:Screens` , `group:We.Retail Run - Content` .

   ![ configuratie van het ontwerp onder /apps/settings/wcm/designs/wij-retail-run ](/help/screens-cloud/developing/assets/2018-05-07_at_1_14pm.png)

   Ontwerpconfiguratie onder /apps/settings/wcm/designs/we-retail-run

## Sjabloon voor aangepaste handlers {#custom-handlers}

Als uw aangepaste component externe bronnen gebruikt, zoals elementen (afbeeldingen, video&#39;s, lettertypen en pictogrammen), specifieke elementuitvoeringen of clientbibliotheken (css en js), worden deze bronnen niet automatisch toegevoegd aan de offlineconfiguratie. De reden is dat Adobe de HTML-markering standaard bundelt.

Adobe biedt een extensiemechanisme voor aangepaste componenten waarmee u de exacte elementen die naar de speler zijn gedownload, kunt aanpassen en optimaliseren en waarmee u hun afhankelijkheden kunt blootstellen aan de logica voor offline in cache plaatsen in Screens.

In de onderstaande sectie ziet u de sjabloon voor aangepaste offline bronhandlers en de minimale vereisten in de `pom.xml` voor dat specifieke project.

```java
package …;

import javax.annotation.Nonnull;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Reference;
import org.apache.felix.scr.annotations.Service;
import org.apache.sling.api.resource.Resource;
import org.apache.sling.api.resource.ResourceUtil;
import org.apache.sling.api.resource.ValueMap;

import com.adobe.cq.screens.visitor.OfflineResourceHandler;

@Service(value = OfflineResourceHandler.class)
@Component(immediate = true)
public class MyCustomHandler extends AbstractResourceHandler {

 @Reference
 private …; // OSGi services injection

 /**
  * The resource types that are handled by the handler.
  * @return the handled resource types
  */
 @Nonnull
 @Override
 public String[] getSupportedResourceTypes() {
     return new String[] { … };
 }

 /**
  * Accept the provided resource, visit and traverse it as needed.
  * @param resource The resource to accept
  */
 @Override
 public void accept(@Nonnull Resource resource) {
     ValueMap properties = ResourceUtil.getValueMap(resource);
     
     /* You can directly add explicit paths for offline caching using the `visit`
        method of the visitor. */
     
     // retrieve a custom property from the component
     String myCustomRenditionUrl = properties.get("myCustomRenditionUrl", String.class);
     // adding that exact asset/rendition/path to the offline manifest
     this.visitor.visit(myCustomRenditionUrl);
     
     
     /* You can delegate handling for dependent resources so they are also added to
        the offline cache using the `accept` method of the visitor. */
     
     // retrieve a referenced dependent resource
     String referencedResourcePath = properties.get("myOtherResource", String.class);
     ResourceResolver resolver = resource.getResourceResolver();
     Resource referencedResource = resolver.getResource(referencedResourcePath);
     // let the handler for that resource handle it
     if (referencedResource != null) {
         this.visitor.accept(referencedResource);
     }
   }
}
```

De volgende code bevat de minimumvereisten in de `pom.xml` voor dat specifieke project:

```css
   <dependencies>
        …
        <!-- Felix annotations -->
        <dependency>
            <groupId>org.apache.felix</groupId>
            <artifactId>org.apache.felix.scr.annotations</artifactId>
            <version>1.9.0</version>
            <scope>provided</scope>
        </dependency>

        <!-- Screens core bundle with OfflineResourceHandler/AbstractResourceHandler -->
        <dependency>
            <groupId>com.adobe.cq.screens</groupId>
            <artifactId>com.adobe.cq.screens</artifactId>
            <version>1.5.90</version>
            <scope>provided</scope>
        </dependency>
        …
      </dependencies>
```

## Alles samenvoegen {#putting-it-all-together}

In de onderstaande video ziet u de voltooide component en de manier waarop deze aan een volgnummer kan worden toegevoegd. Het kanaal wordt vervolgens toegevoegd aan de weergave Locatie en uiteindelijk toegewezen aan een Screens-speler.

>[!VIDEO](https://video.tv.adobe.com/v/22385?quaity=9)

## Voltooide code {#finished-code}

Hieronder ziet u de voltooide code uit de zelfstudie. **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip** en **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip** zijn de gecompileerde pakketten van AEM. **SRC-screens-weretail-looppas-0.0.1.zip &#x200B;** is de uncompiled broncode die kan worden opgesteld gebruikend Maven.

[Bestand ophalen](/help/screens-cloud/developing/assets/screens-weretail-runuiapps-001-snapshot.zip)

[Bestand ophalen](/help/screens-cloud/developing/assets/screens-weretail-runuicontent-001-snapshot.zip)

[Bestand ophalen](/help/screens-cloud/developing/assets/screens-weretail-run.zip)
