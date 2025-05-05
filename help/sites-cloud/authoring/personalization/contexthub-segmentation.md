---
title: Het vormen Segmentatie met ContextHub
description: Leer hoe te om segmentatie te vormen gebruikend ContextHub.
exl-id: fbc38611-dbee-426e-b823-df64b6730c45
solution: Experience Manager Sites
feature: Authoring, Personalization
role: User
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '1653'
ht-degree: 0%

---

# Het vormen Segmentatie met ContextHub{#configuring-segmentation-with-contexthub}

Segmentering is een belangrijke overweging bij het maken van een campagne. Zie [ Begrijpend Segmentatie ](segmentation.md) voor informatie over hoe de segmentatie en zeer belangrijke termijnen werkt.

Afhankelijk van de informatie u reeds over uw plaatsbezoekers en de doelstellingen hebt verzameld u wilt bereiken, bepaal de segmenten en de strategieën nodig voor uw gerichte inhoud.

Deze segmenten worden vervolgens gebruikt om een bezoeker specifieke inhoud te bieden. {de activiteiten van 0} die [&#128279;](activities.md) hier worden bepaald kunnen op om het even welke pagina worden omvat en bepalen welk bezoekerssegment de gespecialiseerde inhoud van toepassing is.

Met AEM kunt u de ervaringen van uw gebruikers eenvoudig aanpassen. Het laat u ook de resultaten van uw segmentdefinities verifiëren.

## Segmenten openen {#accessing-segments}

De [&#128279;](audiences.md) console van 0&rbrace; Soorten publiek &lbrace;wordt gebruikt om segmenten voor ContextHub en publiek voor uw rekening van Adobe Target te beheren.  Deze documentatie behandelt het beheren van segmenten voor ContextHub.

Om tot uw segmenten toegang te hebben, in globale navigatie selecteren **Navigatie > Personalization > Soorten publiek**. Selecteer uw configuratie (bijvoorbeeld, Plaats WKND) om uw segmenten te zien:

![ het Leiden publiek ](../assets/contexthub-segmentation-audiences.png)

## Segment-editor {#segment-editor}

<!--The **Segment Editor** lets you easily modify a segment. To edit a segment, select a segment in the [list of segments](/help/sites-administering/segmentation.md#accessing-segments) and click the **Edit** button.-->
De **Redacteur van het Segment** laat u gemakkelijk een segment wijzigen. Om een segment uit te geven, selecteer een segment in de lijst van segmenten en klik **uitgeven** knoop.

![ de redacteur van het Segment ](../assets/contexthub-segment-editor.png)

Gebruikend de componentenbrowser kunt u **EN** en **OF** containers toevoegen om de segmentlogica te bepalen, dan extra componenten toevoegen om eigenschappen en waarden of verwijzingsmanuscripten en andere segmenten te vergelijken om de selectiecriteria (zie [ Creërend een Nieuw Segment ](#creating-a-new-segment)) te bepalen om het nauwkeurige scenario voor het selecteren van het segment te bepalen.

Wanneer de volledige verklaring aan waar evalueert dan heeft het segment opgelost. In het geval van veelvoudige segmenten die van toepassing zijn, dan wordt de **factor van de Verhoging** ook gebruikt. Zie [ Creërend een Nieuw Segment ](#creating-a-new-segment) voor details op de verhogingsfactor.

>[!CAUTION]
>
>De segmentredacteur controleert geen cirkelverwijzingen. Zo verwijst segment A bijvoorbeeld naar een ander segment B, dat weer naar segment A verwijst. U moet ervoor zorgen dat de segmenten geen cirkelverwijzingen bevatten.

### Containers {#containers}

De volgende containers zijn beschikbaar uit-van-de-doos en staan u toe om vergelijkingen en verwijzingen samen te groeperen voor booleaanse evaluatie. U kunt deze vanuit de componentbrowser naar de editor slepen. Zie de volgende sectie [ Gebruikend EN EN OF Containers ](#using-and-and-or-containers) voor meer informatie.

|  |  |
|---|---|
| Container en | De Booleaanse operator AND |
| Container OF | De operator Boolean OR |

### Vergelijkingen {#comparisons}

De volgende segmentvergelijkingen zijn beschikbaar uit-van-de-doos om segmenteigenschappen te evalueren. U kunt deze vanuit de componentbrowser naar de editor slepen.

|  |  |
|---|---|
| Eigenschap-waarde | Vergelijkt een bezit van een opslag met een bepaalde waarde |
| Eigenschap | Vergelijkt één bezit van een opslag aan een ander bezit |
| Eigenschap-segmentverwijzing | Vergelijkt een bezit van een opslag aan een ander referenced segment |
| Eigenschapverwijzing | Vergelijkt een bezit van een opslag met de resultaten van een manuscript |
| Referentie-script voor segment | Vergelijkt een segment waarnaar wordt verwezen met de resultaten van een script |

>[!NOTE]
>
>Wanneer het vergelijken van waarden, als het gegevenstype van de vergelijking niet wordt geplaatst (d.w.z. wordt geplaatst om auto te ontdekken), zal de de segmenteringsmotor van ContextHub eenvoudig de waarden zoals javascript vergelijken. Er worden geen waarden naar de verwachte typen gecast, wat tot misleidende resultaten kan leiden. Bijvoorbeeld:
>
>`null < 30 // will return true`
>
>Daarom wanneer [ creërend een segment ](#creating-a-new-segment), zou u a **gegevenstype** moeten selecteren wanneer de types van vergeleken waarden gekend zijn. Bijvoorbeeld:
>
>Wanneer het vergelijken van het bezit `profile/age`, weet u reeds dat het vergeleken type a **aantal** is, zodat zelfs als `profile/age` niet wordt geplaatst, is een vergelijking `profile/age` minder-dan 30 **vals** teruggekeerd, aangezien u zou verwachten.

### Verwijzingen {#references}

De volgende verwijzingen zijn beschikbaar uit-van-de-doos om rechtstreeks met een manuscript of een ander segment te verbinden. U kunt deze vanuit de componentbrowser naar de editor slepen.

|  |  |
|---|---|
| Segmentverwijzing | Evalueer het referenced segment |
| Scriptreferentie | Evalueer het referenced manuscript. Zie de volgende sectie [ Gebruikend de Verwijzingen van het Manuscript ](#using-script-references) voor meer informatie. |

## Een nieuw segment maken {#creating-a-new-segment}

Het nieuwe segment definiëren:

1. Na [ toegang hebbend tot de segmenten ](#accessing-segments), [ navigeer aan de omslag ](#organizing-segments) waar u het segment zou willen tot stand brengen.

1. Selecteer **creeer** knoop en selecteer **creëren Segment ContextHub**.

   ![ voeg segment ](../assets/contexthub-create-segment.png) toe

1. In het **Nieuwe Segment ContextHub**, ga een titel voor het segment en een verhogingswaarde indien nodig in en selecteer dan **creeer**.

   ![ Nieuw segment ](../assets/contexthub-new-segment.png)

   Elk segment heeft een verhogingsparameter die als weegfactor wordt gebruikt. Een hoger getal geeft aan dat het segment wordt geselecteerd bij voorkeur boven een segment met een lager getal in gevallen waarin meerdere segmenten geldig zijn.

   * Minimumwaarde: `0`
   * Maximumwaarde: `1000000`

1. Bewerk het gemaakte segment vanuit de segmentconsole en open het in de segmenteditor.
1. Sleep een vergelijking of een verwijzing naar de segmentredacteur het in het gebrek EN container zal verschijnen.
1. Dubbelselecteer de configureoptie van de nieuwe verwijzing of het nieuwe segment om de specifieke parameters uit te geven. In dit voorbeeld testen we mensen in Bazel.

   ![ het Testen voor mensen in Bazel ](../assets/contexthub-comparing-property-value.png)

   Plaats altijd het Type van Gegevens van a **&#x200B;**&#x200B;indien mogelijk om ervoor te zorgen dat uw vergelijkingen behoorlijk worden geëvalueerd. Zie [ Vergelijkingen ](#comparisons) voor meer informatie.

1. Klik **Gedaan** om uw definitie te bewaren:
1. Voeg desgewenst meer componenten toe. U kunt booleaanse uitdrukkingen formuleren gebruikend de containercomponenten voor EN en OF vergelijkingen (zie [ Gebruikend EN en of Containers ](#using-and-and-or-containers) hieronder). Met de segmentredacteur kunt u componenten schrappen niet meer nodig, of hen slepen aan nieuwe posities binnen de verklaring.

### AND en OR-containers gebruiken {#using-and-and-or-containers}

Gebruikend EN en OF containercomponenten, kunt u complexe segmenten in AEM construeren. Hierbij is het nuttig om u bewust te maken van een aantal basispunten:

* Het hoogste niveau van de definitie is altijd de EN container die aanvankelijk wordt gecreeerd. Dit kan niet worden veranderd, maar heeft geen effect op de rest van uw segmentdefinitie.
* Zorg ervoor dat het nesten van de container zinvol is. De containers kunnen als steunen van uw booleaanse uitdrukking worden bekeken.

In het volgende voorbeeld worden bezoekers geselecteerd die worden beschouwd in onze doelgroep Zwitserland:

```text
 People in Basel

 OR

 People in Zürich
```

U begint door een OF containercomponent binnen het gebrek EN container te plaatsen. Binnen de container OR kunt u de bezit of verwijzingscomponenten toevoegen.

![ Segment met OR exploitant ](../assets/contexthub-or-operator.png)

U kunt meerdere AND- en OR-operatoren naar wens nesten.

### Scriptverwijzingen gebruiken {#using-script-references}

Door de component van de Verwijzing van het Manuscript te gebruiken, kan de evaluatie van een segmentbezit aan een extern manuscript worden afgevaardigd. Zodra het manuscript behoorlijk wordt gevormd, kan het als een andere component van een segmentvoorwaarde worden gebruikt.

#### Een script definiëren naar verwijzing {#defining-a-script-to-reference}

1. Voeg bestand toe aan `contexthub.segment-engine.scripts` clientlib.
1. Voer een functie uit die een waarde terugkeert. Bijvoorbeeld:

   ```javascript
   ContextHub.console.log(ContextHub.Shared.timestamp(), '[loading] contexthub.segment-engine.scripts - script.profile-info.js');
   
   (function() {
       'use strict';
   
       /**
        * Sample script returning profile information. Returns user info if data is available, false otherwise.
        *
        * @returns {Boolean}
        */
       var getProfileInfo = function() {
           /* let the SegmentEngine know when script should be re-run */
           this.dependOn(ContextHub.SegmentEngine.Property('profile/age'));
           this.dependOn(ContextHub.SegmentEngine.Property('profile/givenName'));
   
           /* variables */
           var name = ContextHub.get('profile/givenName');
           var age = ContextHub.get('profile/age');
   
           return name === 'Joe' && age === 123;
       };
   
       /* register function */
       ContextHub.SegmentEngine.ScriptManager.register('getProfileInfo', getProfileInfo);
   
   })();
   ```

1. Registreer het script bij `ContextHub.SegmentEngine.ScriptManager.register` .

Als het script afhankelijk is van aanvullende eigenschappen, moet het script `this.dependOn()` aanroepen. Als het script bijvoorbeeld afhankelijk is van `profile/age` :

```javascript
this.dependOn(ContextHub.SegmentEngine.Property('profile/age'));
```

#### Naar een script verwijzen {#referencing-a-script}

1. Creeer segment ContextHub.
1. Voeg **component van de Verwijzing van 0&rbrace; Manuscript &lbrace;in de gewenste plaats van het segment toe.**
1. Open uitgeven dialoog van de **component van de Verwijzing van het Manuscript**. Als [ behoorlijk gevormd ](#defining-a-script-to-reference), het manuscript in de **naam van het Manuscript** drop-down zou moeten beschikbaar zijn.

## Segmenten ordenen {#organizing-segments}

Als u veel segmenten hebt, kunnen deze moeilijk te beheren worden als een platte lijst. In dergelijke gevallen kan het handig zijn om mappen te maken voor het beheer van uw segmenten.

### Een nieuwe map maken {#create-folder}

1. Na [ toegang hebbend tot de segmenten ](#accessing-segments), selecteer **creeer** knoop en selecteer **Omslag**.

   ![ voeg omslag ](../assets/contexthub-create-segment.png) toe

1. Verstrek a **Titel** en a **Naam** voor uw omslag.
   * De **Titel** zou beschrijvend moeten zijn.
   * De **Naam** wordt de knoopnaam in de bewaarplaats.
      * Het wordt automatisch geproduceerd gebaseerd op de titel en aangepast volgens [ AEM noemende overeenkomsten ](/help/implementing/developing/introduction/naming-conventions.md).
      * Deze kan zo nodig worden aangepast.

   ![ creeer omslag ](../assets/contexthub-create-folder.png)

1. Selecteer **creeer**.

   ![ bevestigt omslag ](../assets/contexthub-confirm-folder.png)

1. De map wordt weergegeven in de lijst met segmenten.
   * Hoe u de kolommen sorteert, is van invloed op de plaats in de lijst waar de nieuwe map verschijnt.
   * U kunt de kolomkoppen selecteren om de sortering aan te passen.

     ![ De nieuwe omslag ](../assets/contexthub-folder.png)

### Bestaande mappen wijzigen {#modify-folders}

1. Na [ toegang hebbend tot de segmenten ](#accessing-segments), selecteer de omslag u wilt wijzigen om het te selecteren.

   ![ Uitgezochte omslag ](../assets/contexthub-select-folder.png)

1. Selecteer **anders noemen** in de toolbar om de omslag anders te noemen.

1. Verstrek een nieuwe **Titel van de Omslag** en selecteer **sparen**.

   ![ noem omslag anders ](../assets/contexthub-rename-folder.png)

>[!NOTE]
>
>Bij het wijzigen van de mapnaam kan alleen de titel worden gewijzigd. De naam kan niet worden gewijzigd.

### Een map verwijderen

1. Na [ toegang hebbend tot de segmenten ](#accessing-segments), selecteer de omslag u wilt wijzigen om het te selecteren.

   ![ Uitgezochte omslag ](../assets/contexthub-select-folder.png)

1. Selecteer **Schrapping** in de toolbar om de omslag te schrappen.

1. Een dialoogvenster bevat een lijst met mappen die zijn geselecteerd om te worden verwijderd.

   ![ bevestigt schrapping ](../assets/contexthub-confirm-segment-delete.png)

   * Selecteer **Schrapping** om te bevestigen.
   * Selecteer **annuleren** om te aborteren.

1. Als een van de geselecteerde mappen submappen of segmenten bevat, moet de verwijdering ervan worden bevestigd.

   ![ Bevestig schrapping van kinderen ](../assets/contexthub-confirm-segment-child-delete.png)

   * Selecteer **Drijf Schrapping** om te bevestigen.
   * Selecteer **annuleren** om te aborteren.

>[!NOTE]
>
> Het is niet mogelijk een segment van de ene map naar de andere te verplaatsen.

## De toepassing van een segment testen {#testing-the-application-of-a-segment}

Zodra het segment is bepaald, kunnen de potentiële resultaten met de hulp van **[ContextHub ](contexthub.md) worden getest.**

1. Een voorvertoning van een pagina weergeven
1. Klik het pictogram ContextHub om de toolbar te openbaren ContextHub
1. Selecteer een persoon die overeenkomt met het segment dat u hebt gemaakt
1. ContextHub zal de toepasselijke segmenten voor de geselecteerde persoon oplossen

Bijvoorbeeld, is onze eenvoudige segmentdefinitie om gebruikers in Bazel te identificeren gebaseerd op de plaats van de gebruiker. Als u een specifieke persoon laadt die overeenkomt met die criteria, wordt getoond of het segment is opgelost:

![ Segment dat ](../assets/contexthub-segment-resolve.png) oplost

Of indien deze niet is opgelost:

![ Segment dat niet ](../assets/contexthub-segment-doesnt-resolve.png) oplost

>[!NOTE]
>
>Alle kenmerken worden onmiddellijk opgelost, maar de meeste wijzigingen worden alleen toegepast wanneer de pagina opnieuw wordt geladen.

Dergelijke tests kunnen ook op inhoudspagina&#39;s en in combinatie met gerichte inhoud en verwante **Activiteiten** en **Ervaringen** worden uitgevoerd.

Als u een activiteit en ervaring hebt ingesteld, kunt u uw segment gemakkelijk testen met de activiteit. Voor details over vestiging ziet een activiteit, de [ documentatie bij het ontwerpen van gerichte inhoud ](targeted-content.md).

1. In de bewerkingsmodus van een pagina waarop u doelinhoud hebt ingesteld, ziet u dat de inhoud als doel is ingesteld via het pijlpictogram op de inhoud.
1. De schakelaar aan voorproefwijze en het gebruiken van de contexthub, schakelaar aan een persoon die niet de segmentatie aanpast die voor de ervaring wordt gevormd.
1. De schakelaar aan een persoon die de segmentatie aanpast die voor de ervaring wordt gevormd en ziet dat de ervaring dienovereenkomstig verandert.

## Uw segment gebruiken {#using-your-segment}

Segmenten worden gebruikt om de werkelijke inhoud te bepalen die door specifieke doelgroepen wordt gezien. Zie [ het Leiden Soorten publiek ](audiences.md) voor meer informatie over publiek en segmenten en [ het Authoring van Gerichte Inhoud ](targeted-content.md) over het gebruiken van publiek en segmenten aan doelinhoud.
