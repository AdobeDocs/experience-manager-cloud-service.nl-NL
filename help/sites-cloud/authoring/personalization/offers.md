---
title: Aanbiedingen maken en beheren (console Aanbiedingen)
description: Gebruik de console van Aanbiedingen om aanbiedingen tot stand te brengen die u in activiteitenervaringen kunt gebruiken
exl-id: 81d2fda2-06a9-48f6-820a-dd9e11d94fcc
solution: Experience Manager Sites
feature: Authoring, Personalization
role: User
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '1351'
ht-degree: 0%

---

# Aanbiedingen maken en beheren (console Aanbiedingen) {#creating-and-managing-offers}

De **console van Aanbiedingen** zal in de toekomst worden afgekeurd. Dus vanaf nu is het:

* Slechts beschikbaar aan klanten die *erfenis* reeds gedefiniëerde aanbiedingen hebben (namelijk reeds bestaand)
* Aanbevolen dat dergelijke verouderde aanbiedingen worden geconverteerd naar Experience Fragment-aanbiedingen
   * Zodra de laatste erfenisaanbieding wordt omgezet/verwijderd, zal de **console van Aanbiedingen** niet meer beschikbaar zijn.

![&#x200B; Consoles van Personalization &#x200B;](/help/sites-cloud/authoring/assets/offers-consoles.png)

>[!NOTE]
>
>De klanten die reeds bestaande erfenisaanbiedingen hebben kunnen nog de **console van Aanbiedingen** gebruiken om zowel bestaand te zien, en nieuwe, erfenisaanbiedingen tot stand te brengen.
>
>De klanten zonder reeds bestaande erfenisaanbiedingen zullen niet de **console van Aanbiedingen** zien.
>
>Alle klanten kunnen **Aanbiedingen van de Fragmenten van de Ervaring gebruiken** om aanbiedingen tot stand te brengen en te beheren.

## Een verouderde aanbieding omzetten in een ervaringsfragment {#convert-legacy-offer-to-experience-fragment}

A **Bekeerling aan ervaringsfragmentvariatie** optie, en het werkschema, is uitgevoerd om u te helpen uw erfenisaanbieding in een Fragment van de Ervaring omzetten:

>[!NOTE]
>
>Dit is de aanbevolen workflow voor het converteren van verouderde aanbiedingen naar ervaringsfragmenten.

>[!NOTE]
>
>U kunt ook zelf een Experience Fragment maken, de inhoud van uw verouderde aanbieding handmatig overbrengen naar het fragment en vervolgens de verouderde aanbieding verwijderen.

>[!CAUTION]
>
>De **Bekeerling aan ervaringsfragmentvariatie** optie is beschikbaar voor alle Componenten van de Kern.
>
>Deze optie wordt niet ondersteund voor aangepaste componenten. Voor dergelijke componenten moet u de inhoud handmatig omzetten in een ervaringsfragment.

>[!CAUTION]
>
>Zodra het laatste verouderde aanbod is omgezet/verwijderd:
>
>* De **console van Aanbiedingen** zal niet meer beschikbaar zijn.
>* Het doelpictogram in de werkbalkbalk van andere betrokken componenten wordt niet meer weergegeven.

1. Open een pagina die de aanbieding voor bewerking bevat.

1. Schakelaar aan **het richten** wijze voor die pagina.

1. Selecteer **Begin richtend**.

1. Selecteer de juiste (beoogde) component.

1. De componententoolbar zal een optie aan **Bekeerling aan ervaringsfragmentvariatie** verstrekken:

   ![&#x200B; het Omzetten van Verouderde Aanbieding van de Verouderde aan het Fragment van de Ervaring &#x200B;](/help/sites-cloud/authoring/assets/offers-convert-legacy-icon.png)

1. Er wordt een dialoogvenster weergegeven. Hier kunt u de vereiste **Actie** selecteren:

   * Een nieuw ervaringsfragment maken
   * De inhoud toevoegen aan een bestaand ervaringsfragment

   Voor dit scenario, creeer **een nieuw Fragment van de Ervaring**.

   ![&#x200B; Bekeerling in de dialoog van de Variatie van het Fragment van de Ervaring &#x200B;](/help/sites-cloud/authoring/assets/offers-convert-dialog.png)

1. Vul de vereiste velden in het dialoogvenster in:

   * **Bovenliggende weg**
Het bovenliggende pad van het nieuwe ervaringsfragment opgeven
   * **Malplaatje**
Selecteer de sjabloon die u wilt gebruiken voor het maken van het ervaringsfragment.
   * **titel van het Fragment**
Geef de titel op.
   * **de markeringen van het Fragment**
Voeg indien nodig codes toe.

1. Bevestig met **Gedaan**.

   Als u nu aan de **console van de Aanbiedingen van het Fragment van de Ervaring** navigeert, kunt u uw nieuw ervaringsfragment, samen met zijn bijbehorende variaties zien.

### Aanwijzen met de aanbiedingensjabloon {#targeting-offers-template}

>[!CAUTION]
>
>Deze optie is alleen beschikbaar voor klanten met bestaande oudere aanbiedingen.
>
>Zoals met de **console van Aanbiedingen** zal het niet meer beschikbaar of zijn:
>
>* zodra het laatste verouderde aanbod is omgezet in Experience Fragments
>* wanneer oude aanbiedingen zijn verouderd (in de toekomst)
>
>Daarom is de geadviseerde optie het Fragmenten van de Ervaring te gebruiken, niet deze optie.

Voor klanten met reeds bestaande erfenisaanbiedingen, zijn de **opties van het Malplaatje van de Aanbieding van het 0&rbrace; Gebruik zichtbaar wanneer het richten van componenten die** niet **de Fragmenten van de Ervaring zijn:**

![&#x200B; Bekeerling in de dialoog van de Variatie van het Fragment van de Ervaring &#x200B;](/help/sites-cloud/authoring/assets/offers-legacy-target-non-experience-fragment.png)

## De aanbiedingenconsole {#offers-console}

>[!CAUTION]
>
>Deze console wordt afgekeurd in de toekomst, aangezien het een erfenismanier aanbiedt om inhoud te personaliseren.
>
>Je hebt wat tijd om je voor te bereiden. Zie hoe te [&#x200B; uw bestaande erfenisaanbiedingen in een aanbieding van het ervaringsfragment omzetten &#x200B;](#convert-legacy-offer-to-experience-fragment).

Gebruik de console van Aanbiedingen om aanbiedingen tot stand te brengen die u in activiteitenervaringen [&#128279;](/help/sites-cloud/authoring/personalization/targeted-content.md) kunt  gebruiken. Het creëren van aanbiedingen in de console van Aanbiedingen bespaart tijd wanneer verscheidene ervaringen de zelfde aanbieding vereisen:

* Maak het aanbod eenmaal in de bibliotheek en gebruik het in meerdere ervaringen met uw merkactiviteiten.
* Wijzig de aanbieding in de bibliotheek en de wijziging is van invloed op alle ervaringen die er gebruik van maken.

De console van Aanbiedingen organiseert aanbiedingen door merk. Elk merk bevat een bibliotheek met aanbiedingen die in de ervaringen van een merk kunnen worden gebruikt. Gebruik mappen om een hiërarchische structuur te definiëren voor het organiseren van aanbiedingen in elke bibliotheek. Met een logische mapstructuur kunnen auteurs eenvoudig aanbiedingen zoeken door te bladeren. Met tags en zoekgereedschappen kunnen auteurs ook aanbiedingen vinden.

### Een merk toevoegen met de aanbiedingsconsole {#add-a-brand-using-the-offers-console}

Maak een merk waaraan uw aanbiedingen zijn gekoppeld. Open een merk in de console van Aanbiedingen om tot zijn aanbiedingsbibliotheek toegang te hebben waar u omslagen en aanbiedingen kunt tot stand brengen.

Wanneer u een merk gebruikend de console van Aanbiedingen creeert, verschijnt het ook in de [&#x200B; console van Activiteiten &#x200B;](/help/sites-cloud/authoring/personalization/activities.md) waar u activiteiten voor het merk kunt toevoegen en beheren.

1. In de console van de Navigatie, uitgezochte **Personalization** > **Aanbiedingen**.

   ![&#x200B; die aan de console van Aanbiedingen navigeren &#x200B;](/help/sites-cloud/authoring/assets/offers-navigation.png)

1. Selecteer **creeer** en dan **creeer** **Merk**.
1. Selecteer het merkmalplaatje en selecteer **daarna**.
1. Typ een titel voor het merk zoals u deze wilt weergeven in de consoles van Aanbiedingen en Activiteiten. Typ of selecteer eventueel een of meer tags die u aan het merk wilt koppelen.
1. Selecteer **creeer**.

### Een map toevoegen aan een aanbiedingsbibliotheek {#add-a-folder-to-an-offer-library}

Voeg een map toe aan de aanbiedingsbibliotheek van een merk om aanbiedingen te organiseren en op te slaan. U kunt een map maken onder het merk of onder andere mappen.

1. Open in de console Aanbiedingen de locatie waar u de map wilt maken. Open bijvoorbeeld het merk om een map op hoofdniveau te maken of open een andere map in de bibliotheek.
1. Selecteer **creeer** > **creeer Omslag of Aanbieding**.

   ![&#x200B; Creërend aanbiedingsomslag &#x200B;](/help/sites-cloud/authoring/assets/offers-create-folder.png)

1. Selecteer **Omslag** en klik **daarna**.
1. Typ een titel voor de map zoals u deze wilt weergeven in de aanbiedingsbibliotheek en typ of selecteer tags.

   ![&#x200B; het bepalen van omslageigenschappen &#x200B;](/help/sites-cloud/authoring/assets/offers-folder-properties.png)

1. Selecteer **creeer**.

### Een voorstel toevoegen aan een bibliotheek met aanbiedingen {#add-an-offer-to-an-offer-library}

Voeg een aanbieding toe aan de aanbiedingsbibliotheek van een merk zodat deze aan de ervaringen van het merk kan worden toegevoegd. Als je een voorstel toevoegt, geef je een titel op. U kunt de aanbieding ook koppelen aan een of meer tags om de zoekbaarheid te verbeteren.

Nadat u het voorstel hebt gemaakt, kunt u het openen om de inhoud te ontwerpen.

1. In de console van Aanbiedingen, open de plaats waar u de aanbieding wilt tot stand brengen. Open bijvoorbeeld het merk om een aanbieding op hoofdniveau te maken of open een map in de bibliotheek.
1. Selecteer **creeer** > **creeer Omslag of Aanbieding**.

   ![&#x200B; Creërend aanbiedingsomslag &#x200B;](/help/sites-cloud/authoring/assets/offers-create-folder.png)

1. Selecteer het **malplaatje van de Pagina van 0&rbrace; Aanbieding &lbrace;en selecteer dan** daarna **.**
1. Typ een titel voor de aanbieding en selecteer of typ naar keuze één of meerdere markeringen aan vennoot met de aanbieding, dan uitgezocht **creeer**.
1. In de bevestigingsdialoogdoos, om de aanbieding voor het uitgeven te openen uitgezochte **Open Pagina**.

### Een voorstel bewerken {#editing-an-offer}

Open een aanbieding en bewerk de inhoud zoals u die in de ervaringen wilt weergeven die het gebruiken. Als u een aanbieding bewerkt die in een willekeurige ervaring wordt gebruikt, worden de wijzigingen in de ervaringen weergegeven.

U kunt een voorstel van een omslag in een aanbiedingsbibliotheek of van onderzoeksresultaten openen. Je kunt ook een voorstel openen vanuit een ervaring die gebruikmaakt van het voorstel.

1. In de console van Aanbiedingen, selecteer het pictogram naast de aanbieding en selecteer **uitgeven**.
1. Voeg componenten toe aan de aanbieding en bewerk de componenteninhoud zoals gebruikelijk.

### Een voorstel verwijderen {#deleting-an-offer}

Een voorstel verwijderen wanneer het niet meer nodig is. Wanneer u een aanbieding probeert te verwijderen die in een ervaring wordt gebruikt, wordt u gevraagd de verwijdering te bevestigen. Als u bevestigt, wordt het aanbod verwijderd en wordt het uit de ervaringen verwijderd.

U kunt een aanbieding verwijderen terwijl u de mapinhoud in een aanbiedingsbibliotheek of de zoekresultaten bekijkt.

1. In de console van Aanbiedingen, selecteer het pictogram naast de aanbieding en selecteer **Schrapping**.

   Selecteer de aanbieding en selecteer **Schrapping**.

1. In de dialoogdoos die verschijnt, uitgezochte **Schrapping** om de schrapping te bevestigen.
1. Als de aanbieding in een of meer ervaringen wordt gebruikt, verschijnt er een dialoogvenster waarin wordt aangegeven dat naar de aanbieding wordt verwezen:

   * Om de aanbieding te schrappen en het uit de ervaringen te verwijderen, uitgezochte **Schrapping** dwingen.
   * Om de aanbieding te houden, annuleert de uitgezochte **&#x200B;**.

### Zoeken naar voorstellen {#searching-for-offers}

Zoek naar voorstellen van om het even welk merk gebruikend sleutelwoorden om de titel te passen.

![&#x200B; zoekend naar een aanbieding &#x200B;](/help/sites-cloud/authoring/assets/offers-search.png)

De huidige zoekcriteria worden naast de zoekresultaten weergegeven. U kunt de resultaten ook in oplopende of aflopende volgorde op kolom sorteren. U kunt een onderzoek van om het even welke omslag van om het even welke aanbiedingsbibliotheek uitvoeren. De zoekresultaten zijn hetzelfde, ongeacht de huidige map.

Zoekvoorstellen:

1. Selecteer boven aan de console Aanbiedingen het vergrootglaspictogram. Standaard is de zoekopdracht beperkt tot voorstellen.
1. Voer uw trefwoord in om naar voorstellen te zoeken. Maak een keuze uit de resultaten.
