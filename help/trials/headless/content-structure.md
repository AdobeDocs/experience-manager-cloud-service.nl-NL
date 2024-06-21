---
title: De inhoudsstructuur voor uw app maken
description: Leer hoe u AEM modellen van inhoudsfragmenten kunt gebruiken om uw inhoudsstructuur te maken, die fungeert als basis voor inhoud zonder kop.
hidefromtoc: true
index: false
exl-id: ace9b9f3-8bc6-4a36-a51c-ff60cdd339ce
feature: Headless
role: Admin, User, Developer
source-git-commit: f66ea281e6abc373e9704e14c97b77d82c55323b
workflow-type: tm+mt
source-wordcount: '1002'
ht-degree: 0%

---


# De inhoudsstructuur voor uw app maken {#content-structure}

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_overview"
>title="Maak de inhoudsstructuur voor uw app"
>abstract="Als u deze reeks interactieve hulplijnen volgt, leert u een structuur te maken (het model Inhoudsfragment) die fungeert als basisstructuur voor inhoud zonder kop."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_overview_guide"
>title="De modelconsole starten"
>abstract="Laten we onderzoeken hoe u een herbruikbaar schema, een zogenaamd Content Fragment-model, kunt maken voor uw inhoud in Adobe Experience Manager as a Cloud Service. Bekijk de video zodat u begrijpt waarom deze stap belangrijk is. <br><br>In deze het leren module, gebruikt u een reisplaats als voorbeeld en loopt door het creëren van een model dat een reis vertegenwoordigt.<br><br>Start deze module op een nieuw tabblad door op de onderstaande knop te klikken en volg deze handleiding."
>additional-url="https://video.tv.adobe.com/v/3413261" text="Video over intro-inhoud"

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_overview_guide_footer"
>title="Gefeliciteerd! U hebt geleerd hoe u een model van een inhoudsfragment kunt maken om de structuur van uw gegevens zonder kop weer te geven en u hebt de eerste stap gezet om inhoud met meerdere kanalen op een geschaalde en standaardmanier te leveren."
>abstract=""

## Een model maken {#create-model}

De console van het model van het Fragmentmodel van de Inhoud opent in een nieuw lusje. U kunt de modelconsole van het inhoudsfragment beschouwen als uw bibliotheek met modellen, waarin u modellen maakt en bestaande modellen beheert.

Bijvoorbeeld, creeert u een model dat de gegevensstructuur van een reis vertegenwoordigt die op een reiswebsite wordt voorzien. Een reis die dit model gebruikt wordt bedoeld als **Adventure**.

1. Klik in de rechterbovenhoek van het scherm op **Maken** om te beginnen met het maken van een model voor een inhoudsfragment.

1. De wizard Model maken begeleidt u bij het maken van uw model. Geef de verplichte informatie op.

   * **Modeltitel** - Een kort label van het model en geeft meestal het doel van het model aan. U kunt het nieuwe model roepen `Adventure`.
   * **Model inschakelen** - Deze optie is standaard ingeschakeld en moet zijn ingeschakeld om op dit model gebaseerde inhoudsfragmenten te kunnen maken.

1. Nadat de verplichte velden zijn ingevuld, klikt u op **Maken** rechtsboven om het model te maken.

1. De **Succes** bevestigt dat het model is gemaakt. Klikken **Openen** in het dialoogvenster zodat u het nieuwe inhoudsfragmentmodel in de editor kunt openen op een nieuw tabblad. Ga vervolgens verder met de volgende stap om gegevensvelden aan uw model toe te voegen.

![Stap 2 en 3 van het creëren van een model van het Fragment van de Inhoud](assets/do-not-localize/create-model.png)

## De modeleditor gebruiken {#configure-model}

U hebt nu een model genaamd **Adventure**, maar het heeft geen details zoals duur, bestemming, en activiteiten. Voordat u het model kunt gebruiken, moet u de structuur van de gegevens definiëren.

In de editor van het inhoudsfragmentmodel configureert u de gegevenstypen en eigenschappen die de inhoud van het model definiëren.

>[!TIP]
>
>Het is belangrijk om de noemende schema&#39;s in de volgende instructies te volgen omdat deze specifieke namen in recentere modules worden bedoeld.

1. Sleep een **Tekst met één regel** veld van de **Gegevenstypen** aan de rechterkant van de editor en zet deze neer op het model Inhoudsfragment.

1. Wanneer een gegevenstype is geplaatst, wordt de **Gegevenstypen** automatisch gewijzigd in **Eigenschappen** , waarin u de details kunt definiëren van het gegevenstype dat u hebt geplaatst. Voor dit eerste gebied, wilt u de titel van de reis of het avontuur opslaan. Voer de volgende eigenschappen in.

   * **Renderen als:** **Tekstveld** - Wanneer u een avontuur creeert, slaat dit gebied de titel van het avontuur op.
   * **Veldlabel:** `Title` - Het label dat voor dit veld wordt weergegeven wanneer u een avontuur maakt.

1. Nadat u de eigenschappen van het veld hebt gedefinieerd, kunt u terugschakelen naar het tabblad **Gegevenstypen** in het rechterdeelvenster en voeg aanvullende velden toe door te slepen en neer te zetten.

Op deze manier kunt u zoveel velden toevoegen als nodig zijn voor het ondersteunen van de gegevensstructuur die u nodig hebt. De typen gegevensvelden variëren, maar het proces om deze aan uw model toe te voegen, blijft ongewijzigd.

Ga door naar de volgende sectie zodat u de gebieden kunt toevoegen noodzakelijk om te voltooien en sparen **Adventure** model

![Stap 1, 2 en 3 van het toevoegen van velden aan het model](assets/do-not-localize/define-model-fields.png)

## Velden toevoegen aan het model {#additional-fields}

U hebt al een veld voor de titel van het avontuur. Nu moet u velden toevoegen om de beschrijving, de prijs en een representatief beeld van het avontuur vast te leggen.

>[!TIP]
>
>De **Adventure** model is gebaseerd op de WKND-voorbeeldsite voor AEM. U kunt [bezoek hier de site](https://wknd.site/us/en/adventures/yosemite-backpacking.html) om inhoud te zien die het **Adventure** model.

Voer dezelfde stappen uit als hierboven om deze extra velden toe te voegen. Het enige verschil is de eigenschappen die u moet instellen.

1. Voeg een veld toe, zodat u de beschrijving van het avontuur kunt opslaan door een **Tekst met meerdere regels** en voer de volgende eigenschappen in:

   * **Renderen als:** **Tekstgebied** - Wanneer u een avontuur creeert, slaat dit gebied een korte beschrijving van de reis op.
   * **Veldlabel:** `Description` - Het label dat voor dit veld wordt weergegeven wanneer u een avontuur maakt.

1. Voeg een veld toe, zodat u de prijs van het avontuur kunt opslaan door een **Tekst met één regel** en voer de volgende eigenschappen in:

   * **Renderen als:** **Tekstveld** - Wanneer u een avontuur creeert, slaat dit gebied de prijs van de reis op.
   * **Veldlabel:** `Price` - Het label dat voor dit veld wordt weergegeven wanneer u een avontuur maakt.

1. Voeg een veld toe zodat u een afbeelding voor de tijdelijke conversie kunt opslaan. Afbeeldingen in AEM worden opgeslagen als een ander type inhoud, ook wel **Activa**. Als u een veld voor de velden wilt maken, sleept u een **Content Reference** veld dat verwijst naar het element van de afbeelding.

   * **Renderen als:** **Content Reference** - Wanneer u een avontuur creeert, wijst dit gebied aan beeldactiva die deze reis vertegenwoordigen.
   * **Veldlabel:** `Image` - Het label dat voor dit veld wordt weergegeven wanneer u een avontuur maakt.
   * **Hoofdpad:** `/content/dam/aem-demo-assets/en` - Hiermee geeft u een beginpuntpad op bij het zoeken naar elementen met de Asset Selector.

1. Nadat u de vereiste velden voor het model Inhoudsfragment hebt toegevoegd, klikt u rechtsboven in het venster op **Opslaan**.

1. Het model wordt opgeslagen en u keert terug naar de Console van het model van het Fragment van de Inhoud.
