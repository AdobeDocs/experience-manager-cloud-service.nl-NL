---
title: Inhoud extraheren via de GraphQL API
description: Leer hoe u Content Fragments en de GraphQL API gebruikt als een beheersysteem zonder kop.
hidefromtoc: true
index: false
exl-id: f5e379c8-e63e-41b3-a9fe-1e89d373dc6b
source-git-commit: bcab02cbd84955ecdc239d4166ae38e5f79b3264
workflow-type: tm+mt
source-wordcount: '847'
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

Klik op de knop **GraphQL Explorer starten** opent de GraphQL Explorer op een nieuw tabblad.

![De GraphQL Query Editor](assets/extract-content/query-editor.png)

Met de GraphQL Explorer kunt u query&#39;s maken en valideren op basis van uw inhoud zonder kop voordat u deze gebruikt om de inhoud van uw app of website aan te sturen. Laten we eens kijken hoe dat is gelukt!

1. Uw AEM proefversie zonder kop wordt geleverd met een eindpunt dat is voorgeladen met Content Fragments waaruit u inhoud voor testdoeleinden kunt extraheren. Selecteer **AEM Demo-elementen** van de **Endpoint** vervolgkeuzelijst in de rechterbovenhoek van de editor.

   ![Eindpunt selecteren](assets/extract-content/select-endpoint.png)

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

   ![Lijstquery](assets/extract-content/list-query.png)

1. Klik op de knop **Afspelen** knoop bij de bovenkant verlaten van de vraagredacteur om de vraag uit te voeren.

1. De resultaten worden getoond in het juiste paneel, naast de vraagredacteur. Als de query onjuist is, wordt een fout weergegeven in het rechterdeelvenster.

   ![Zoekresultaten weergeven](assets/extract-content/list-query-results.png)

U hebt net een lijstvraag voor een volledige lijst van alle Fragments van de Inhoud bevestigd. Dit proces helpt ervoor te zorgen dat de reactie is wat uw app verwacht, met resultaten die aantonen hoe uw apps en websites de in AEM gemaakte inhoud zullen ophalen.

## Query voor een specifiek deel van de voorbeeldinhoud {#bypath-query}

Als u een query van het type byPath uitvoert, kunt u inhoud voor een bepaald inhoudsfragment ophalen. Productdetailpagina&#39;s en pagina&#39;s die zich op een specifieke set inhoud richten, vereisen doorgaans dit type query. Laten we eens kijken hoe het werkt!

1. Kopieer het volgende codefragment voor een byPath-query van het vooraf geladen bestand **AEM Demo-elementen** eindpunt.

   ```text
    {
     adventureByPath(
       _path: "/content/dam/aem-demo-assets/en/adventures/bali-surf-camp/bali-surf-camp"
     ) {
       item {
         _path
         adventureTitle
         adventureDescription {
           json
         }
         adventurePrimaryImage {
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

   ![byPath-query](assets/extract-content/bypath-query.png)

1. Klik op de knop **Afspelen** knoop bij de bovenkant verlaten van de vraagredacteur om de vraag uit te voeren.

1. De resultaten worden getoond in het juiste paneel, naast de vraagredacteur. Als de query onjuist is, wordt een fout weergegeven in het rechterdeelvenster.

   ![byPath-queryresultaten](assets/extract-content/bypath-query-results.png)

U hebt zojuist een query byPath gevalideerd om een specifiek inhoudsfragment op te halen dat wordt aangegeven door het pad van dat fragment.

## Vraag uw eigen inhoud op {#own-queries}

Nu u de twee primaire soorten vragen in werking hebt gesteld, bent u bereid om uw eigen inhoud te vragen!

1. Om vragen tegen uw eigen Fragmenten van de Inhoud in werking te stellen, verander het eindpunt van **AEM Demo-elementen** aan de **Uw project** map.

   ![Uw eigen eindpunt selecteren](assets/extract-content/select-endpoint.png)

1. Verwijder alle bestaande inhoud in de query-editor. Typ vervolgens open haakje `{` en druk Ctrl+Space of Option+Space voor een automatisch aangevulde lijst van de modellen die in uw eindpunt werden bepaald. Selecteer het model dat u hebt gemaakt en waarin u eindigt `List` van de opties.

   ![Automatisch voltooide modellen in vraagredacteur](assets/extract-content/auto-complete-models.png)

1. Definieer de items die de query moet bevatten voor het model Inhoudsfragment dat u hebt geselecteerd. Typ nogmaals haakje openen `{`Druk vervolgens op Ctrl+Space of Option+Space voor een lijst die automatisch wordt voltooid. Selecteren `items` van de opties.

   ![Items automatisch aanvullen in de query-editor](assets/extract-content/auto-complete-items.png)

1. Definieer de velden die de query moet bevatten voor het geselecteerde inhoudsfragmentmodel. Typ nogmaals haakje openen `{`Druk vervolgens op Ctrl+Space of Option+Space voor een automatisch aangevulde lijst met beschikbare velden in het model Inhoudsfragment. Selecteer in de lijst de gewenste velden in uw model.

   ![Velden automatisch aanvullen in de query-editor](assets/extract-content/auto-complete-fields.png)

1. Meerdere velden scheiden met een komma (`,`) of spatie en druk nogmaals op Ctrl+Space of Option+Space om extra velden te selecteren.

1. Terwijl u werkt, kunt u tikken of op de knop **prettiseren** om de code automatisch op te maken zodat deze gemakkelijker kan worden gelezen.

   ![prettiseren](assets/extract-content/prettify.png)

1. Tik of klik op de knop **Afspelen** knoop bij de bovenkant verlaten van de redacteur om de vraag in werking te stellen.

   ![Resultaten van uw eigen query](assets/extract-content/custom-query-results.png)

1. De resultaten worden getoond in het juiste paneel, naast de vraagredacteur.

Zo kunt u uw inhoud leveren aan alominakanale digitale ervaringen.
