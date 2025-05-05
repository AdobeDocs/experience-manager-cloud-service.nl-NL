---
title: Inhoud extraheren via de GraphQL API
description: Leer hoe u Content Fragments en de GraphQL API gebruikt als een beheersysteem zonder kop.
hidefromtoc: true
index: false
exl-id: f5e379c8-e63e-41b3-a9fe-1e89d373dc6b
feature: Headless
role: Admin, User, Developer
source-git-commit: f66ea281e6abc373e9704e14c97b77d82c55323b
workflow-type: tm+mt
source-wordcount: '1069'
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
>abstract="GraphQL biedt een API op basis van query&#39;s waarmee externe clienttoepassingen AEM alleen kunnen vragen voor de inhoud die het nodig heeft, met behulp van één API-aanroep. Volg deze module om te leren hoe te om twee verschillende types van vragen in werking te stellen. Leer vervolgens hoe u de inhoud ophaalt uit het inhoudsfragment dat u in de vorige module hebt gemaakt.<br><br> lanceer deze module in een nieuw lusje door hieronder te klikken."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_graphql_guide_footer"
>title="Mooi werk! U hebt over de twee basistypes van vragen geleerd en hoe te om uw eigen inhoud te vragen. U begrijpt nu hoe u de AEM GraphQL API kunt gebruiken om efficiënte query&#39;s te maken die inhoud leveren in een indeling die u door de app verwacht."
>abstract=""

## Query voor een lijst met voorbeeldinhoud {#list-query}

U start in GraphQL Explorer op een nieuw tabblad. Hier kunt u query&#39;s samenstellen en valideren op basis van uw inhoud zonder kop voordat u deze gebruikt om de inhoud van uw app of website van stroom te voorzien.

1. De proefversie zonder kop van AEM wordt geleverd met een eindpunt dat is voorgeladen met Content Fragments waaruit u inhoud voor testdoeleinden kunt extraheren. Zorg ervoor dat het **eindpunt van de Demo Assets van 0&rbrace; AEM &lbrace;in het** Eindpunt **drop-down menu bij de hoogste juiste hoek van de redacteur wordt geselecteerd.**

1. Kopieer het volgende codefragment voor een lijstvraag van het vooraf geladen **AEM demo Assets** eindpunt. Een lijstvraag keert een lijst van alle inhoud terug die een specifiek model van het Fragment van de Inhoud gebruikt. De inventaris en de categoriepagina&#39;s gebruiken typisch dit vraagformaat.

   ```text
   {
    adventureList {
     items {
       _path
       title
       price
       tripLength
       primaryImage {
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

1. Zodra gekleefd, klik het **Spel** knoop bij de bovenkant verlaten van de vraagredacteur om de vraag uit te voeren.

1. De resultaten worden getoond in het juiste paneel, naast de vraagredacteur. Als de query onjuist is, wordt een fout weergegeven in het rechterdeelvenster.

   ![ vraag van de Lijst ](assets/do-not-localize/list-query-1-3-4-5.png)

U hebt zojuist een lijstquery voor een volledige lijst met alle inhoudsfragmenten gevalideerd. Dit proces zorgt ervoor dat de reactie is wat uw app verwacht, met resultaten die aantonen hoe uw apps en websites de in AEM gemaakte inhoud ophalen.

## Query voor een specifiek deel van de voorbeeldinhoud {#bypath-query}

Als u een query op basis van pad uitvoert, kunt u inhoud voor een bepaald inhoudsfragment ophalen. Productdetailpagina&#39;s en pagina&#39;s die zich op een specifieke set inhoud richten, vereisen doorgaans dit type query.

1. Kopieer het volgende codefragment voor a byPath vraag van het vooraf geladen **AEM demo Assets** eindpunt.

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

1. Zodra gekleefd, klik het **Spel** knoop bij de bovenkant verlaten van de vraagredacteur om de vraag uit te voeren.

1. De resultaten worden getoond in het juiste paneel, naast de vraagredacteur. Als de query onjuist is, wordt een fout weergegeven in het rechterdeelvenster.

   ![ byPath vraagresultaten ](assets/do-not-localize/bypath-query-2-3-4.png)

U hebt zojuist een bytepadquery gevalideerd om een specifiek inhoudsfragment op te halen dat wordt aangeduid door het pad van dat fragment.

## Vraag uw eigen inhoud op {#own-queries}

Nu u de twee primaire soorten vragen in werking hebt gesteld, bent u bereid om uw eigen inhoud te vragen.

1. Om vragen tegen uw eigen Fragmenten van de Inhoud in werking te stellen, verander het eindpunt van de **omslag van Assets van de Demo van 0&rbrace; AEM &lbrace;in de** Uw omslag van het Project **.**

1. Verwijder alle bestaande inhoud in de query-editor. Typ vervolgens accolade openen `{` en druk op Ctrl+Space of Option+Space voor een lijst met automatisch aangevulde modellen die in het eindpunt zijn gedefinieerd. Selecteer in de opties het model dat u hebt gemaakt en dat eindigt in `List` . Als u de voorbeelden in de vorige modules volgt, zou u `adventureList` in de auto-volledige lijst moeten vinden.

   ![ de douanequery van het Begin ](assets/do-not-localize/custom-query-1.png)

1. Definieer de items die de query moet bevatten voor het model Inhoudsfragment dat u hebt geselecteerd. Typ het rechte openingshaakje `{` en druk vervolgens op Ctrl+Spatiebalk of Option+Spatiebalk voor een lijst die automatisch wordt ingevuld. Selecteer `items` in de opties.

1. Selecteer de **Vullen** knoop om uw code automatisch te formatteren zodat het gemakkelijker is te lezen.

1. Zodra volledig, selecteer het **Spel** knoop bij de bovenkant verlaten van de redacteur om de vraag in werking te stellen. De redacteur vult automatisch `items` aan, die kort in geel worden benadrukt, en de vraaglooppas.

1. De resultaten worden getoond in het juiste paneel, naast de vraagredacteur.

   ![ de douanequery van de Looppas ](assets/do-not-localize/custom-query-2.png)

Zo kunt u uw inhoud leveren aan alominakanale digitale ervaringen.

## Blijvende query&#39;s {#persisted-queries}

Blijvende query&#39;s zijn het voorkeursmechanisme voor het toegankelijk maken van de GraphQL API voor clienttoepassingen. Zodra een vraag is voortgeduurd, kan het worden gevraagd gebruikend een verzoek van GET en in het voorgeheugen ondergebracht voor snelle terugwinning.

U maakt een doorlopende query die gegevens bevat die u van uw clienttoepassing wilt gebruiken.

1. U zult de gegevens gebruiken die u als inhoudsfragment vroeger creeerde, zodat ervoor zorgen dat het **Uw eindpunt van het Project** in het **Eindpunt** drop-down menu bij de hoogste juiste hoek van de redacteur wordt geselecteerd.

1. Kopieer het volgende codefragment.

   ```text
      {
      adventureList {
       items {
         title
         description {
           plaintext
         }
         price
         image {
           ... on ImageRef {
             _publishUrl
             mimeType
           }
         }
       }
     }
   }
   ```

1. Vervang de bestaande inhoud in de vraagredacteur door de gekopieerde code te kleven.

   >[!NOTE]
   >
   >Als u niet de zelfde gebiedsbeschrijvingen gebruikte zoals die in de vorige modules worden beschreven, werk de gebiedsnamen in deze vraag bij.
   >
   >Gebruik de GraphQL-functie voor automatisch aanvullen (Ctrl+Spatiebalk of Option+Spatiebalk), zoals eerder beschreven, om de beschikbare eigenschappen beter te kunnen identificeren.

1. Zodra gekleefd, klik het **Spel** knoop bij de bovenkant verlaten van de vraagredacteur om de vraag uit te voeren.

1. De resultaten worden getoond in het juiste paneel, naast de vraagredacteur. Als de query onjuist is, wordt een fout weergegeven in het rechterdeelvenster.

   ![ creeer eigen vraag ](assets/do-not-localize/own-query.png)

1. Wanneer tevreden met uw vraag, klik **sparen als** knoop bij de bovenkant van de vraagredacteur om de vraag voort te zetten.

1. In de **naam van de Vraag** pop-up, geef uw vraag de naam `adventure-list`.

1. Selecteer **sparen als**.

   ![ blijft vraag ](assets/do-not-localize/persist-query.png)

1. De vraag wordt voortgeduurd zoals bevestigd door een bannerbericht bij de bodem van het scherm. De query wordt nu ook weergegeven in het linkerdeelvenster met doorlopende query&#39;s in het venster.

1. Voor de persisted vraag om openbaar beschikbaar te zijn, moet het worden gepubliceerd, veel als hoe uw Fragments van de Inhoud moeten worden gepubliceerd. Klik **publiceren** bij het hoogste recht van de vraagredacteur om de vraag te publiceren.

1. De publicatie wordt bevestigd door een bannerkennisgeving.

Er is nu een nieuwe, voortgezette query die alleen de specifieke eigenschappen en indelingen bevat die u hebt gedefinieerd.
