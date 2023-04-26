---
title: De inhoudsstructuur voor uw app maken
description: Leer hoe u AEM modellen van inhoudsfragmenten kunt gebruiken om uw inhoudsstructuur te maken, die fungeert als basis voor inhoud zonder kop.
hidefromtoc: true
index: false
exl-id: ace9b9f3-8bc6-4a36-a51c-ff60cdd339ce
source-git-commit: 7134951a588eae3ee0c7c11abea17a34eac21474
workflow-type: tm+mt
source-wordcount: '1062'
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
>abstract="Laten we onderzoeken hoe u een herbruikbaar schema, een zogenaamd Content Fragment-model, kunt maken voor uw inhoud in Adobe Experience Manager as a Cloud Service. Bekijk de video om te begrijpen waarom dit een belangrijke stap is. <br><br>In deze het leren module zullen wij een reisplaats als ons voorbeeld gebruiken en door het creëren van een model lopen dat een reis vertegenwoordigt. Wij zullen naar dit model in recentere modules verwijzen, zodat zorg ervoor u het noemende schema zoals verstrekt volgt.<br><br>Start deze module op een nieuw tabblad door op de onderstaande knop te klikken en volg deze handleiding."
>additional-url="https://video.tv.adobe.com/v/3413261" text="Video over intro-inhoud"

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_overview_guide_footer"
>title="Gefeliciteerd! U hebt geleerd hoe u een model van een inhoudsfragment kunt maken om de structuur van uw gegevens zonder kop weer te geven en u hebt de eerste stap gezet om inhoud met meerdere kanalen op een geschaalde en standaardmanier te leveren."
>abstract=""

## Een model maken {#create-model}

De console van het model van het Fragmentmodel van de Inhoud opent in een nieuw lusje. Beschouw de modelconsole van het inhoudsfragment als uw bibliotheek met modellen, waar u nieuwe modellen maakt en bestaande modellen beheert.

Voor ons voorbeeld, zullen wij een model creëren dat de gegevensstructuur van een reis vertegenwoordigt die op een reiswebsite wordt voorzien. We zullen een reis in dit model als een **Adventure.**

1. Klik op de knop **Maken** aan de rechterbovenhoek van het scherm om een model voor inhoudsfragmenten te maken.

1. De wizard Model maken begint en begeleidt u bij het maken van uw model. Geef de verplichte informatie op.

   * **Modeltitel** - Dit is een korte beschrijving van het model en geeft meestal het doel van het model aan. We noemen ons nieuwe model `Adventure`.
   * **Model inschakelen** - Deze optie is standaard ingeschakeld en moet zijn ingeschakeld om op dit model gebaseerde inhoudsfragmenten te kunnen maken.

1. Als de verplichte velden zijn ingevuld, klikt u op **Maken** boven aan links om het model te maken.

1. De **Succes** bevestigt dat het model is gemaakt. Klikken **Openen** in het dialoogvenster om het nieuwe inhoudsfragmentmodel in de editor te openen op een nieuw tabblad. Ga vervolgens verder met de volgende stap om gegevensvelden aan uw model toe te voegen.

![Stap 2 en 3 van het creëren van een model van het Fragment van de Inhoud](assets/do-not-localize/create-model.png)

## De modeleditor gebruiken {#configure-model}

We hebben nu een model genaamd **Adventure** om reizen op een reiswebsite te vertegenwoordigen, maar het heeft geen details zoals duur, bestemming, activiteiten, enz. Voordat u het model kunt gebruiken, moet u de structuur van de gegevens definiëren.

In de editor van het inhoudsfragmentmodel configureert u de gegevenstypen en eigenschappen die de inhoud van het model definiëren.

>[!TIP]
>
>Wij zullen een aantal belangrijke gebieden toevoegen aan de **Adventure**. In recentere modules zullen wij gebruiken en aan het model toevoegen, zodat te volgen gelieve het noemende schema zoals verstrekt.

1. Sleep een **Tekst met één regel** veld van **Gegevenstypen** aan de rechterkant van de editor en zet deze neer op het model Inhoudsfragment.

1. Wanneer een gegevenstype is geplaatst, wordt de **Gegevenstypen** automatisch gewijzigd in **Eigenschappen** , waarin u de details kunt definiëren van het gegevenstype dat u net hebt geplaatst. Voor dit eerste veld willen we de titel van de reis of het avontuur opslaan. Voer de volgende eigenschappen in.

   * **Renderen als:** **Tekstveld** - Wanneer u een avontuur creeert, zal dit gebied de titel van het avontuur opslaan.
   * **Veldlabel:** `Title` - Dit is het label dat voor dit veld wordt weergegeven wanneer u een nieuw avontuur maakt.

1. Wanneer u de eigenschappen van het veld hebt gedefinieerd, kunt u terugschakelen naar het tabblad **Gegevenstypen** in het rechterdeelvenster en voeg aanvullende velden toe door te slepen en neer te zetten.

Op deze manier kunt u zoveel velden toevoegen als nodig zijn voor het ondersteunen van elke gegevensstructuur die u nodig hebt. De typen gegevensvelden variëren, maar het proces om deze aan uw model toe te voegen, blijft ongewijzigd.

Ga verder met de volgende sectie om de velden toe te voegen die nodig zijn om de **Adventure** model

![Stap 1, 2 en 3 van het toevoegen van velden aan het model](assets/do-not-localize/define-model-fields.png)

## Velden toevoegen aan het model {#additional-fields}

U hebt al een veld voor de titel van het avontuur. Nu moet u velden toevoegen om de beschrijving, de prijs en een representatief beeld van de reis vast te leggen.

>[!TIP]
>
>De **Adventure** model is gebaseerd op de WKND-voorbeeldsite voor AEM. U kunt [bezoek hier de site](https://wknd.site/us/en/adventures/yosemite-backpacking.html) om er meer over te leren als u dat wenst, maar kennis van het is niet nodig voor deze leermodules.

Voer dezelfde stappen uit als hierboven om deze extra velden toe te voegen. Het enige verschil zijn de eigenschappen die u moet instellen.

1. Voeg een veld toe waarin u de beschrijving van het avontuur kunt opslaan door een **Tekst met meerdere regels** en voer de volgende eigenschappen in:

   * **Renderen als:** **Tekstgebied** - Wanneer u een avontuur creeert, zal dit gebied een korte beschrijving van de reis opslaan.
   * **Veldlabel:** `Description` - Dit is het label dat voor dit veld wordt weergegeven wanneer u een nieuw avontuur maakt.

1. Voeg een veld toe om de prijs van het avontuur op te slaan door een **Tekst met één regel** en voer de volgende eigenschappen in:

   * **Renderen als:** **Tekstveld** - Wanneer u een avontuur creeert, zal dit gebied de prijs van de reis opslaan.
   * **Veldlabel:** `Price` - Dit is het label dat voor dit veld wordt weergegeven wanneer u een nieuw avontuur maakt.

1. Voeg een veld toe waarin u een afbeelding voor de tijdelijke conversie wilt opslaan. Afbeeldingen in AEM worden opgeslagen als een ander type inhoud, ook wel **Activa**. Als u een veld voor ze wilt maken, moet u een veld slepen en neerzetten **Content Reference** veld dat verwijst naar het element van de afbeelding.

   * **Renderen als:** **Content Reference** - Wanneer u een avontuur creeert, zal dit gebied aan beeldactiva richten die deze reis vertegenwoordigen.
   * **Veldlabel:** `Image` - Dit is het label dat voor dit veld wordt weergegeven wanneer u een nieuw avontuur maakt.

1. Als u alle velden hebt toegevoegd die nodig zijn voor het model Inhoudsfragment, klikt u op **Opslaan** rechtsboven in het venster.

1. Het model wordt opgeslagen en u keert terug naar de Console van het model van het Fragment van de Inhoud.
