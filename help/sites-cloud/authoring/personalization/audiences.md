---
title: Soorten publiek beheren
description: Met de console Soorten publiek kunt u soorten publiek voor uw Adobe Target-account maken, organiseren en beheren of segmenten voor ContextHub beheren
exl-id: dff72c15-afcd-4b16-a711-e9ca3010e3ec
solution: Experience Manager Sites
feature: Authoring, Personalization
role: User
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '885'
ht-degree: 9%

---

# Soorten publiek beheren{#managing-audiences}

Met de console Soorten publiek kunt u soorten publiek voor uw Adobe Target-account maken, organiseren en beheren of segmenten voor ContextHub beheren:

* Voeg Soorten publiek toe - of Adobe Target publiek of segmenten ContextHub.
* Het publiek beheren.

Een publiek, genoemd *segment* in ContextHub, is een klasse van bezoekers die door specifieke criteria worden bepaald, die dan bepaalt wie een gerichte activiteit ziet. Wanneer u een activiteit richt, kunt u of publiek direct in het Doelproces selecteren of nieuwe degenen in de console van het Publiek creëren.

In de console van het publiek, worden de soorten publiek georganiseerd door merk.

Het publiek is beschikbaar op het richten wijze voor [ creërend gerichte inhoud ](/help/sites-cloud/authoring/personalization/targeted-content.md), waar u publiek kunt ook tot stand brengen (maar u moet het publiek van Adobe Target in de console van het Publiek tot stand brengen). De soorten publiek dat u op het richten wijze creeert verschijnen in de console van het Soorten publiek.

Het publiek wordt weergegeven met een label waarin wordt beschreven welk soort publiek wordt gedefinieerd:

* CH - ContextHub-segment
* AT - Adobe Target-publiek

## Het creëren van een Segment ContextHub in de Console van het publiek {#creating-a-contexthub-segment-in-the-audiences-console}

U kunt een segment ContextHub of in de console van het publiek of tijdens het het richten proces tot stand brengen.

Om een segment ContextHub in de console van het publiek tot stand te brengen:

1. In de console van de Navigatie, uitgezochte **Personalization**. Selecteer **Soorten publiek**.
1. Selecteer **tot Segment ContextHub**.

   ![ Creërend een segment ](/help/sites-cloud/authoring/assets/audiences-create-segment.png)

1. In het **Nieuwe de dialoogvakje van het Segment ContextHub**, ga een titel in en pas de verhoging aan en klik **creeer**. Uw nieuw segment ContextHub verschijnt in de publiekslijst.

   >[!NOTE]
   >
   >U kunt de gewijzigde lijst sorteren door te tikken of **Gewijzigd** te klikken om door dalende orde te sorteren om het even welk gecreeerd publiek te zien.

Voor verder detail over het creëren van segmenten die ContextHub gebruiken, zie de het Vormen Segmentatie met documentatie ContextHub. <!--For further detail about creating segments using ContextHub, see [Configuring Segmentation with ContextHub](/help/sites-administering/segmentation.md).-->

## Een Adobe Target-publiek maken met de Audience Console {#creating-an-adobe-target-audience-using-the-audience-console}

U kunt een Adobe Target-publiek rechtstreeks in AEM maken met behulp van de console Soorten publiek.

Het publiek wordt bepaald door regels die bepalen wie in een doelactiviteit inbegrepen is. Een publieksdefinitie kan veelvoudige regels omvatten en elke regel kan veelvoudige parameters omvatten.

Wanneer u meer dan één regel gebruikt, worden deze regels gecombineerd door de exploitant van Boole EN, wat betekent dat om het even welk potentieel publiekslid aan alle bepaalde voorwaarden moet voldoen om in de activiteit worden omvat. Als u bijvoorbeeld een OS-regel EN een browserregel definieert, worden alleen bezoekers die zowel het gedefinieerde besturingssysteem ALS de gedefinieerde browser gebruiken, opgenomen in de activiteit.

>[!NOTE]
>
>Als u **Doelgroep maken** niet ziet in het menu **Maken**, hebt u niet de benodigde machtigingen om een doelgroep te maken. U hebt schrijfmachtigingen nodig onder `/etc/segmentation` om een doelgroep te kunnen maken. De makers van groepscontent hebben standaard schrijfmachtigingen.

Een Adobe Target-publiek maken:

1. In de console van de Navigatie, uitgezochte **Personalization**. Selecteer **Soorten publiek**.

   ![ die aan publiek navigeren ](/help/sites-cloud/authoring/assets/audiences-navigation.png)

1. In de console van het publiek, creeer de uitgezochte **&#x200B;**&#x200B;en dan **tot Doelpubliek**.

   ![ Creërend een publiek van het Doel ](/help/sites-cloud/authoring/assets/audiences-create-target.png)

1. In het **de dialoogvakje van de Configuratie van Adobe Target**, selecteer de doelconfiguratie en selecteer **O.K.**.
1. In het gebied Rule#1, selecteer het attributentype en ga om het even welke attributeninformatie op de gebieden in die beschikbaar zijn. Als u klaar bent, selecteert u het vinkje rechts van het kenmerk om het op te slaan. Zie [ Attributen en hun opties ](#attributes-and-their-options) voor informatie over alle attributen.
1. Klik op **Regel toevoegen** om nog een regel toe te voegen. Voer zoveel regels in als nodig is. De regels worden gecombineerd met de booleaanse operator AND, wat betekent dat de doelgroep aan alle vereisten van elke regel moet voldoen om voor een activiteit in aanmerking te komen.
1. Selecteer **daarna**.
1. Ga een naam voor het publiek in en selecteer **sparen**.
1. Selecteer **sparen**. Uw publiek wordt vermeld in de lijst van het Publiek.

### Kenmerken en hun opties {#attributes-and-their-options}

U kunt het richten regels voor elk van de volgende attributen tot stand brengen:

| **Attribuut** | **Beschrijving** | **voor meer informatie** |
|---|---|---|
| **Mobiel** | Het doel mobiele apparaten die op parameters zoals mobiel apparaat, type van apparaat, apparatenverkoper, het schermafmetingen (door pixel) worden gebaseerd, en meer. | Zie [ Mobiele documentatie ](https://experienceleague.adobe.com/docs/target/using/audiences/create-audiences/categories-audiences/mobile.html) bij Adobe Target. |
| **Douane** | Aangepaste parameters zijn parameters mbox. Als u om het even welke mbox parameters tot dozen, of de targetPageParams functie doorgeeft, verschijnen die parameters hier voor gebruik in publiek. | Zie {de documentatie van Parameters van de Douane 0} [&#128279;](https://experienceleague.adobe.com/docs/target/using/audiences/create-audiences/categories-audiences/custom-parameters.html) bij Adobe Target. |
| **OS** | U kunt zich richten op bezoekers die een bepaald besturingssysteem gebruiken. | Doelgebruikers die Linux, Macintosh of Windows gebruiken. |
| **Pagina&#39;s van de Plaats** | Doelbezoekers die zich op een specifieke pagina bevinden of een specifieke parameter mbox hebben. | Zie {de documentatie van de Pagina&#39;s van 0} Plaats [&#128279;](https://experienceleague.adobe.com/docs/target/using/audiences/create-audiences/categories-audiences/site-pages.html) in Adobe Target. |
| **Browser** | U kunt zich richten op gebruikers die een specifieke browser of specifieke browseropties gebruiken wanneer zij uw pagina bezoeken. | Zie [ Browser optiesdocumentatie ](https://experienceleague.adobe.com/docs/target/using/audiences/create-audiences/categories-audiences/browser.html) bij Adobe Target. |
| **Profiel van de Bezoeker** | Doelbezoekers die voldoen aan specifieke profielparameters. | Zie {de documentatie van het Profiel van 0} Bezoeker [&#128279;](https://experienceleague.adobe.com/docs/target/using/audiences/visitor-profiles/visitor-profile.html) bij Adobe Target. |
| **Bronnen van het Verkeer** | Doelbezoekers op basis van het zoekprogramma of de bestemmingspagina die hen naar uw site verwijst. | Zie [ documentatie van de Bronnen van het Verkeer ](https://experienceleague.adobe.com/docs/target/using/audiences/create-audiences/categories-audiences/traffic-sources.html) bij Adobe Target. |

## Een publiek wijzigen in de console Soorten publiek {#modifying-an-audience-in-the-audiences-console}

>[!NOTE]
>
>U kunt alleen Adobe Target-soorten publiek bewerken die zijn gemaakt in hetzelfde AEM waarin u bewerkt. Doelpubliek dat in verschillende AEM is gemaakt, kan niet worden bewerkt.

U kunt om het even welk publiek ContextHub van de console van het Publiek uitgeven. U kunt ook het Adobe Target-publiek bewerken, maar alleen het publiek dat is gemaakt in AEM:

1. In de console van de Navigatie, uitgezochte **Personalization**. Selecteer **Soorten publiek**.
1. Selecteer het pictogram naast het segment ContextHub u wilt uitgeven, en selecteren **uitgeeft**.
1. Breng om het even welke veranderingen in de segmentredacteur aan. Zie de documentatie ContextHub voor meer informatie. <!--See the [ContextHub](/help/sites-administering/contexthub-config.md) documentation for more information.-->
