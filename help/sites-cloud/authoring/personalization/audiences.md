---
title: Audiences beheren
description: Met de console Soorten publiek kunt u soorten publiek voor uw Adobe Target-account maken, organiseren en beheren of segmenten voor ContextHub beheren
translation-type: tm+mt
source-git-commit: bffc335fdafe6bf12a66bcd2f7aacf029fce567e
workflow-type: tm+mt
source-wordcount: '975'
ht-degree: 11%

---


# Audiences beheren{#managing-audiences}

Met de console Soorten publiek kunt u soorten publiek voor uw Adobe Target-account maken, organiseren en beheren of segmenten voor ContextHub beheren:

* Voeg Soorten publiek toe - of Adobe Target publiek of segmenten ContextHub.
* Het publiek beheren.

Een publiek, genoemd *segment* in ContextHub, is een klasse bezoekers die door specifieke criteria worden bepaald, die dan bepaalt wie een gerichte activiteit ziet. Wanneer u een activiteit richt, kunt u of publiek direct in het Doelproces selecteren of nieuwe degenen in de console van het Publiek creëren.

In de console van het publiek, worden de soorten publiek georganiseerd door merk.

De soorten publiek zijn beschikbaar op Doelwijze voor het [ontwerpen van gerichte inhoud](/help/sites-cloud/authoring/personalization/targeted-content.md), waar u publiek kunt ook tot stand brengen (maar u moet Adobe Target publiek in de console van het Publiek tot stand brengen). De soorten publiek dat u op het richten wijze creeert verschijnen in de console van het Soorten publiek.

Het publiek wordt weergegeven met een label waarin wordt beschreven welk soort publiek wordt gedefinieerd:

* CH - ContextHub-segment
* AT - Adobe Target-publiek

## Het creëren van een Segment ContextHub in de Console van het publiek {#creating-a-contexthub-segment-in-the-audiences-console}

U kunt een segment ContextHub of in de console van het publiek of tijdens het het richten proces tot stand brengen.

Om een segment ContextHub in de console van het publiek tot stand te brengen:

1. In the Navigation console, click or tap **Personalization**. Klik of tik **Soorten publiek**.
1. Tik of klik op **ContextHub-segment** maken.

   ![Een segment maken](/help/sites-cloud/authoring/assets/audiences-create-segment.png)

1. In het **Nieuwe de dialoogvakje van het Segment** ContextHub, ga een titel in en pas de verhoging aan en klik **creëren**. Uw nieuw segment ContextHub verschijnt in de publiekslijst.

   >[!NOTE]
   >
   >U kunt de gewijzigde lijst sorteren door op **Gewijzigd** te tikken of te klikken om in aflopende volgorde te sorteren om de nieuwe doelgroep te zien.

Voor meer detail over het creëren van segmenten die ContextHub gebruiken, gelieve te zien de het Vormen Segmentatie met documentatie ContextHub. <!--For further detail about creating segments using ContextHub, please see the [Configuring Segmentation with ContextHub](/help/sites-administering/segmentation.md) documentation.-->

## Een Adobe Target-publiek maken met de Audience Console {#creating-an-adobe-target-audience-using-the-audience-console}

U kunt een Adobe Target-publiek rechtstreeks in AEM maken met behulp van de console Soorten publiek.

Het publiek wordt bepaald door regels die bepalen wie in een doelactiviteit inbegrepen is. Een publieksdefinitie kan veelvoudige regels omvatten en elke regel kan veelvoudige parameters omvatten.

Wanneer u meer dan één regel gebruikt, worden deze regels gecombineerd door de exploitant van Boole EN, wat betekent dat om het even welk potentieel publiekslid aan alle bepaalde voorwaarden moet voldoen om in de activiteit worden omvat. Als u bijvoorbeeld een OS-regel EN een browserregel definieert, worden alleen bezoekers die zowel het gedefinieerde besturingssysteem ALS de gedefinieerde browser gebruiken, opgenomen in de activiteit.

>[!NOTE]
>
>Als u **Doelgroep maken** niet ziet in het menu **Maken**, hebt u niet de benodigde machtigingen om een doelgroep te maken. U hebt schrijfmachtigingen nodig onder `/etc/segmentation` om een doelgroep te kunnen maken. De makers van groepscontent hebben standaard schrijfmachtigingen.

Een Adobe Target-publiek maken:

1. In the Navigation console, click or tap **Personalization**. Klik of tik **Soorten publiek**.

   ![Navigeren naar publiek](/help/sites-cloud/authoring/assets/audiences-navigation.png)

1. Tik op of klik op **Maken** in de console Soorten publiek en maak vervolgens** Target Audience**.

   ![Een Target-publiek maken](/help/sites-cloud/authoring/assets/audiences-create-target.png)

1. Selecteer de doelconfiguratie in het dialoogvenster **Adobe Target Configuration** en tik of klik op **OK**.
1. Tik of klik in het gebied Rule#1 op het kenmerktype en voer in de velden die beschikbaar zijn kenmerkgegevens in. Als u klaar bent, selecteert u het vinkje rechts van het kenmerk om het op te slaan. Zie [Kenmerken en de bijbehorende opties](#attributes-and-their-options) voor informatie over alle kenmerken.
1. Klik op **Regel toevoegen** om nog een regel toe te voegen. Voer zoveel regels in als nodig is. De regels worden gecombineerd met de booleaanse operator AND, wat betekent dat de doelgroep aan alle vereisten van elke regel moet voldoen om voor een activiteit in aanmerking te komen.
1. Tik of klik op **Volgende**.
1. Voer een naam voor de doelgroep in en tik of klik op **Opslaan**.
1. Tik of klik op **Opslaan**. Uw publiek wordt vermeld in de lijst van het Publiek.

### Kenmerken en hun opties {#attributes-and-their-options}

U kunt het richten regels voor elk van de volgende attributen tot stand brengen:

| **Kenmerk** | **Beschrijving** | **Voor meer informatie** |
|---|---|---|
| **Mobiel** | Mobiele Target-apparaten op basis van parameters zoals mobiel apparaat, apparaattype, leverancier van het apparaat, schermafmetingen (in pixels) en meer. | Zie [Mobiele documentatie](https://docs.adobe.com/content/help/en/target/using/audiences/create-audiences/categories-audiences/mobile.html) op Adobe Target. |
| **Aangepast** | Aangepaste parameters zijn parameters mbox. Als u om het even welke mbox parameters tot dozen, of de targetPageParams functie doorgeeft, verschijnen die parameters hier voor gebruik in publiek. | Zie documentatie over [aangepaste parameters](https://docs.adobe.com/content/help/en/target/using/audiences/create-audiences/categories-audiences/custom-parameters.html) op Adobe Target. |
| **OS** | U kunt zich richten op bezoekers die een bepaald besturingssysteem gebruiken. | Target-gebruikers die Linux, Macintosh of Windows gebruiken. |
| **Sitepagina&#39;s** | Target-bezoekers die zich op een specifieke pagina bevinden of een specifieke mbox-parameter hebben. | Zie documentatie [over](https://docs.adobe.com/content/help/en/target/using/audiences/create-audiences/categories-audiences/site-pages.html) sitepagina&#39;s op Adobe Target. |
| **Browser** | U kunt zich richten op gebruikers die een specifieke browser of specifieke browseropties gebruiken wanneer zij uw pagina bezoeken. | Zie documentatie over [browseropties](https://docs.adobe.com/help/en/target/using/audiences/create-audiences/categories-audiences/browser.html) op Adobe Target. |
| **Bezoekerprofiel** | Target-bezoekers die voldoen aan specifieke profielparameters. | Raadpleeg de documentatie bij [Bezoekersprofiel](https://docs.adobe.com/content/help/en/target/using/audiences/visitor-profiles/visitor-profile.html) in Adobe Target. |
| **Verkeersbronnen** | Target-bezoekers op basis van het zoekprogramma of de bestemmingspagina die ze naar uw site verwijzen. | Zie [de documentatie](https://docs.adobe.com/content/help/en/target/using/audiences/create-audiences/categories-audiences/traffic-sources.html) van de Bronnen van het Verkeer bij Adobe Target. |

## Een publiek wijzigen in de console Soorten publiek {#modifying-an-audience-in-the-audiences-console}

>[!NOTE]
>
>U kunt alleen Adobe Target-soorten publiek bewerken die zijn gemaakt in dezelfde AEM-instantie waarin u bewerkt. Target-publiek dat in verschillende AEM-omgevingen is gemaakt, kan niet worden bewerkt.

U kunt om het even welk publiek ContextHub van de console van het Publiek uitgeven. U kunt ook het Adobe Target-publiek bewerken, maar alleen het publiek dat is gemaakt in AEM:

1. In the Navigation console, click or tap **Personalization**. Klik of tik **Soorten publiek**.
1. Tik of klik op het pictogram naast het ContextHub-segment dat u wilt bewerken en tik of klik op **Bewerken**.
1. Breng desgewenst wijzigingen aan in de segmenteditor. Zie de documentatie ContextHub voor meer informatie. <!--See the [ContextHub](/help/sites-administering/contexthub-config.md) documentation for more information.-->
