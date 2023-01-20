---
title: Inhoud extraheren via de GraphQL API
description: Leer hoe u Content Fragments en de GraphQL API gebruikt als een beheersysteem zonder kop.
hidefromtoc: true
index: false
exl-id: f5e379c8-e63e-41b3-a9fe-1e89d373dc6b
source-git-commit: 741fadcffc496cb1c32d1943f7759e8d70cf92ff
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 0%

---


# Inhoud extraheren via de GraphQL API {#extract-content}

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_graphql"
>title="Inhoud extraheren met de GraphQL API"
>abstract="In deze module leert u hoe u Content Fragments en de GraphQL API kunt gebruiken als een beheersysteem zonder kop."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_graphql_guide"
>title="GraphQL Explorer starten"
>abstract="GraphQL biedt een API op basis van query&#39;s waarmee externe clienttoepassingen AEM kunnen zoeken voor alleen de inhoud die het nodig heeft, met behulp van één API-aanroep. Volg deze module om te leren hoe te om twee verschillende types van vragen in werking te stellen. Leer vervolgens hoe u de inhoud ophaalt uit het inhoudsfragment dat u in de vorige module hebt gemaakt.<br><br>Start deze module op een nieuw tabblad door hieronder te klikken."
>additional-url="https://video.tv.adobe.com/v/328618" text="Inhoudsintro-video extraheren"

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_graphql_guide_footer"
>title="Mooi werk! U hebt over de twee basistypes van vragen geleerd en hoe te om uw eigen inhoud te vragen. U begrijpt nu hoe u de AEM GraphQL API kunt gebruiken om efficiënte query&#39;s te maken die inhoud leveren in een indeling die u door de app verwacht."
>abstract=""

## Query voor een lijst met voorbeeldinhoud {#list-query}

U start in GraphQL Explorer op een nieuw tabblad. Hier kunt u query&#39;s samenstellen en valideren op basis van uw inhoud zonder kop voordat u deze gebruikt om de inhoud van uw app of website van stroom te voorzien.

1. Uw AEM proefversie zonder kop wordt geleverd met een eindpunt dat is voorgeladen met Content Fragments waaruit u inhoud voor testdoeleinden kunt extraheren. Zorg ervoor dat de **AEM Demo-elementen** het eindpunt wordt geselecteerd in het dialoogvenster **Endpoint** vervolgkeuzelijst in de rechterbovenhoek van de editor.

1. Kopieer het volgende codefragment voor een lijstvraag van vooraf geladen **AEM Demo-elementen** eindpunt. Een lijstvraag keert een lijst van alle inhoud terug die een specifiek model van het Fragment van de Inhoud gebruikt. De inventaris en de categoriepagina&#39;s gebruiken typisch dit vraagformaat.

   ```text
   {
       adventureList {
         items {
            _path
            adventureTitle
            adventurePrice
            adventureTripLength
            adventurePrimaryImage {
              ... on ImageRef {
               _path
               mimeType
               width
               height
             }
           }
         }
      }
    }
   ```

1. Vervang de bestaande inhoud in de vraagredacteur door de gekopieerde code te kleven.

1. Klik op de knop **Afspelen** knoop bij de bovenkant verlaten van de vraagredacteur om de vraag uit te voeren.

1. De resultaten worden getoond in het juiste paneel, naast de vraagredacteur. Als de query onjuist is, wordt een fout weergegeven in het rechterdeelvenster.

   ![Lijstquery](assets/do-not-localize/list-query-1-3-4-5.png)

U hebt net een lijstvraag voor een volledige lijst van alle Fragments van de Inhoud bevestigd. Dit proces helpt ervoor te zorgen dat de reactie is wat uw app verwacht, met resultaten die aantonen hoe uw apps en websites de in AEM gemaakte inhoud zullen ophalen.

## Query voor een specifiek deel van de voorbeeldinhoud {#bypath-query}

Als u een query van het type byPath uitvoert, kunt u inhoud voor een bepaald inhoudsfragment ophalen. Productdetailpagina&#39;s en pagina&#39;s die zich op een specifieke set inhoud richten, vereisen doorgaans dit type query.

1. Kopieer het volgende codefragment voor een byPath-query van het vooraf geladen bestand **AEM Demo-elementen** eindpunt.

   ```text
    {
     adventureByPath(
       _path: "/content/dam/aem-demo-assets/en/adventures/bali-surf-camp/bali-surf-camp"
     ) {
       item {
         _path
         title
         description {
           json
         }
         primaryImage {
           ... on ImageRef {
             _path
             width
             height
           }
         }
       }
     }
   }
   ```

1. Vervang de bestaande inhoud in de vraagredacteur door de gekopieerde code te kleven.

1. Klik op de knop **Afspelen** knoop bij de bovenkant verlaten van de vraagredacteur om de vraag uit te voeren.

1. De resultaten worden getoond in het juiste paneel, naast de vraagredacteur. Als de query onjuist is, wordt een fout weergegeven in het rechterdeelvenster.

   ![byPath-queryresultaten](assets/do-not-localize/bypath-query-2-3-4.png)

U hebt zojuist een query byPath gevalideerd om een specifiek inhoudsfragment op te halen dat wordt aangegeven door het pad van dat fragment.

## Vraag uw eigen inhoud op {#own-queries}

Nu u de twee primaire soorten vragen in werking hebt gesteld, bent u bereid om uw eigen inhoud te vragen.

1. Om vragen tegen uw eigen Fragmenten van de Inhoud in werking te stellen, verander het eindpunt van **AEM Demo-elementen** aan de **Uw project** map.

1. Verwijder alle bestaande inhoud in de query-editor. Typ vervolgens open haakje `{` en druk Ctrl+Space of Option+Space voor een automatisch aangevulde lijst van de modellen die in uw eindpunt werden bepaald. Selecteer het model dat u hebt gemaakt en waarin u eindigt `List` van de opties.

   ![Aangepaste query starten](assets/do-not-localize/custom-query-1-2.png)

1. Definieer de items die de query moet bevatten voor het model Inhoudsfragment dat u hebt geselecteerd. Typ nogmaals haakje openen `{`Druk vervolgens op Ctrl+Space of Option+Space voor een lijst die automatisch wordt voltooid. Selecteren `items` van de opties.

1. Tik of klik op de knop **prettiseren** om de code automatisch op te maken zodat deze gemakkelijker kan worden gelezen.

1. Tik of klik op de knop **Afspelen** knoop bij de bovenkant verlaten van de redacteur om de vraag in werking te stellen. De redacteur auto voltooit `items` en de query wordt uitgevoerd.

1. De resultaten worden getoond in het juiste paneel, naast de vraagredacteur.

   ![Aangepaste query uitvoeren](assets/do-not-localize/custom-query-3-4-5-6.png)

Zo kunt u uw inhoud leveren aan alominakanale digitale ervaringen.
