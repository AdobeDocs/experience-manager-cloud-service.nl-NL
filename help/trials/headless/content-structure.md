---
title: De inhoudsstructuur voor uw app maken
description: Leer hoe u AEM modellen van inhoudsfragmenten kunt gebruiken om uw inhoudsstructuur te maken, die fungeert als basis voor inhoud zonder kop.
hidefromtoc: true
index: false
exl-id: ace9b9f3-8bc6-4a36-a51c-ff60cdd339ce
feature: Headless
role: Admin, User, Developer
source-git-commit: c9cddf9f0e344a2a24ee1a608b3ea920e258f34a
workflow-type: tm+mt
source-wordcount: '1013'
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
>abstract="Laten we onderzoeken hoe u een herbruikbaar schema, een zogenaamd Content Fragment-model, kunt maken voor uw inhoud in Adobe Experience Manager as a Cloud Service. Bekijk de video zodat u begrijpt waarom deze stap belangrijk is. <br><br> in deze het leren module, gebruikt u een reisplaats als voorbeeld en loopt door het creëren van een model dat een reis vertegenwoordigt.<br><br> Lancering deze module in een nieuw lusje door de hieronder knoop te klikken en dan deze gids te volgen."
>additional-url="https://video.tv.adobe.com/v/3413261" text="Video over intro-inhoud"

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_overview_guide_footer"
>title="Gefeliciteerd! U hebt geleerd hoe u een model van een inhoudsfragment kunt maken om de structuur van uw gegevens zonder kop weer te geven en u hebt de eerste stap gezet om inhoud met meerdere kanalen op een geschaalde en standaardmanier te leveren."
>abstract=""

## Een model maken {#create-model}

De console van het model van het Fragmentmodel van de Inhoud opent in een nieuw lusje. U kunt de modelconsole van het inhoudsfragment beschouwen als uw bibliotheek met modellen, waarin u modellen maakt en bestaande modellen beheert.

Bijvoorbeeld, creeert u een model dat de gegevensstructuur van een reis vertegenwoordigt die op een reiswebsite wordt voorzien. Een reis die dit model gebruikt wordt bedoeld als **avontuur**.

1. In de hoger-juiste hoek van het scherm, creeert de klik **** beginnen creërend een model van het Fragment van de Inhoud.

1. De wizard Model maken begeleidt u bij het maken van uw model. Geef de verplichte informatie op.

   * **ModelTitel** - een kort etiket van het model en wijst gewoonlijk op het doel van het model. U kunt het nieuwe model `Adventure` roepen.
   * **laat model** toe - deze optie wordt gecontroleerd door gebrek en moet worden gecontroleerd om tot Inhoudsfragmenten te kunnen leiden die op dit model worden gebaseerd.

1. Nadat de verplichte gebieden worden bevolkt, leidt de klik **** tot bij het hoogste recht om het model tot stand te brengen.

1. Het **de dialoogvakje van het Succes** bevestigt dat het model werd gecreeerd. Klik **Open** in de dialoogdoos zodat kunt u uw nieuw Model van het Fragment van de Inhoud in de redacteur in een nieuw lusje openen. Ga vervolgens verder met de volgende stap om gegevensvelden aan uw model toe te voegen.

![ Stappen twee en drie van het creëren van een model van het Fragment van de Inhoud ](assets/do-not-localize/create-model.png)

## De modeleditor gebruiken {#configure-model}

U hebt nu een model genoemd **Avontuur**, maar het heeft geen details zoals duur, bestemming, en activiteiten. Voordat u het model kunt gebruiken, moet u de structuur van de gegevens definiëren.

In de editor van het inhoudsfragmentmodel configureert u de gegevenstypen en eigenschappen die de inhoud van het model definiëren.

>[!TIP]
>
>Het is belangrijk om de noemende schema&#39;s in de volgende instructies te volgen omdat deze specifieke namen in recentere modules worden bedoeld.

1. Sleep a **Enige lijntekst** van het **paneel van de Types van Gegevens** rechts van de redacteur en laat vallen het op uw model van het Fragment van de Inhoud.

1. Zodra een gegevenstype wordt geplaatst, wordt de **kolom van de Types van Gegevens 0} automatisch veranderd in** Eigenschappen **tabel, waar u de details van het gegevenstype kunt bepalen u plaatste.** Voor dit eerste gebied, wilt u de titel van de reis of het avontuur opslaan. Voer de volgende eigenschappen in.

   * **geeft terug als:** **Gebied van de Tekst** - wanneer u een avontuur creeert, slaat dit gebied de titel van het avontuur op.
   * **Etiket van het Gebied:** `Title` - het etiket dat voor dit gebied wanneer het creëren van een avontuur wordt getoond.

1. Nadat u de eigenschappen van het gebied bepaalt, kunt u terug naar het **lusje van de Types van Gegevens** in het juiste paneel schakelen en extra gebieden toevoegen door te slepen en te laten vallen.

Op deze manier kunt u zoveel velden toevoegen als nodig zijn voor het ondersteunen van de gegevensstructuur die u nodig hebt. De typen gegevensvelden variëren, maar het proces om deze aan uw model toe te voegen, blijft ongewijzigd.

Ga aan de volgende sectie verder zodat kunt u de gebieden noodzakelijk toevoegen om te voltooien en het **model van het Avontuur** te bewaren

![ stappen één, twee, en drie van het toevoegen van gebieden aan het model ](assets/do-not-localize/define-model-fields.png)

## Velden toevoegen aan het model {#additional-fields}

U hebt al een veld voor de titel van het avontuur. Nu moet u velden toevoegen om de beschrijving, de prijs en een representatief beeld van het avontuur vast te leggen.

>[!TIP]
>
>Het **1} model van het Avontuur is gebaseerd op de WKND steekproefplaats voor AEM.** U kunt [ de plaats van WKND hier bezoeken ](https://wknd.site/us/en/adventures/yosemite-backpacking.html) om inhoud te zien die het **3} model van het Avontuur {gebruikt.**

Voer dezelfde stappen uit als hierboven om deze extra velden toe te voegen. Het enige verschil is de eigenschappen die u moet instellen.

1. Voeg een gebied toe zodat kunt u de beschrijving van het avontuur opslaan door a **Meerdere lijntekst** gebied te slepen en te laten vallen en de volgende eigenschappen in te gaan:

   * **geeft terug als:** **Gebied van de Tekst** - wanneer u een avontuur creeert, slaat dit gebied een korte beschrijving van de reis op.
   * **Etiket van het Gebied:** `Description` - het etiket dat voor dit gebied wanneer het creëren van een avontuur wordt getoond.
   * **StandaardType**: **Onbewerkte Tekst** - het formaat dat voor dit voorbeeld wordt vereist.

1. Voeg een gebied toe zodat kunt u de prijs van het avontuur opslaan door a **Enige lijntekst** gebied te slepen en te laten vallen en de volgende eigenschappen in te gaan:

   * **geeft terug als:** **gebied van de Tekst** - wanneer u een avontuur creeert, slaat dit gebied de prijs van de reis op.
   * **Etiket van het Gebied:** `Price` - het etiket dat voor dit gebied wanneer het creëren van een avontuur wordt getoond.

1. Voeg een veld toe zodat u een afbeelding voor de tijdelijke conversie kunt opslaan. De beelden in AEM worden opgeslagen als een ander type van inhoud genoemd **Assets**. Om een gebied voor hen tot stand te brengen, sleept u het gebied van de Verwijzing van de a **Inhoud** dat verwijzingen de activa van het beeld.

   * **geeft terug als:** **Verwijzing van de Inhoud** - wanneer u een avontuur creeert, richt dit gebied aan de beeldactiva die deze reis vertegenwoordigen.
   * **Etiket van het Gebied:** `Image` - het etiket dat voor dit gebied wanneer het creëren van een avontuur wordt getoond.
   * **Weg van de Wortel:** `/content/dam/aem-demo-assets/en` - dit specificeert een uitgangspunt weg wanneer het doorbladeren naar activa met de Selecteur van Activa.

1. Nadat u de noodzakelijke gebieden voor het model van het Fragment van de Inhoud, bij top-right van het venster hebt toegevoegd, klik **sparen**.

1. Het model wordt opgeslagen en u keert terug naar de Console van het model van het Fragment van de Inhoud.
