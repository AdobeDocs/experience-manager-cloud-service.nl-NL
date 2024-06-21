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

De **Aanbiedingen** console zal in de toekomst verouderd zijn. Dus vanaf nu is het:

* Alleen beschikbaar voor klanten met *verouderd* reeds gedefinieerde aanbiedingen (dat wil zeggen, bestaande aanbiedingen)
* Aanbevolen dat dergelijke verouderde aanbiedingen worden geconverteerd naar Experience Fragment-aanbiedingen
   * Zodra het laatste verouderde aanbod is omgezet/verwijderd, wordt het **Aanbiedingen** console is niet meer beschikbaar.

![Aanpassingsconsoles](/help/sites-cloud/authoring/assets/offers-consoles.png)

>[!NOTE]
>
>Klanten met bestaande oudere aanbiedingen kunnen nog steeds gebruikmaken van de **Aanbiedingen** -console om bestaande aanbiedingen te bekijken en nieuwe, verouderde aanbiedingen te maken.
>
>Klanten zonder bestaande oudere aanbiedingen zien de **Aanbiedingen** console.
>
>Alle klanten kunnen **Geniet van fragmenten** om aanbiedingen te maken en te beheren.

## Een verouderde aanbieding omzetten in een ervaringsfragment {#convert-legacy-offer-to-experience-fragment}

A **Omzetten in ervaring met fragmentvariatie** en workflow zijn geïmplementeerd om u te helpen uw oudere aanbieding om te zetten in een Experience Fragment:

>[!NOTE]
>
>Dit is de aanbevolen workflow voor het converteren van verouderde aanbiedingen naar ervaringsfragmenten.

>[!NOTE]
>
>U kunt ook zelf een Experience Fragment maken, de inhoud van uw verouderde aanbieding handmatig overbrengen naar het fragment en vervolgens de verouderde aanbieding verwijderen.

>[!CAUTION]
>
>De **Omzetten in ervaring met fragmentvariatie** is beschikbaar voor alle Core Components.
>
>Deze optie wordt niet ondersteund voor aangepaste componenten. Voor dergelijke componenten moet u de inhoud handmatig omzetten in een ervaringsfragment.

>[!CAUTION]
>
>Zodra het laatste verouderde aanbod is omgezet/verwijderd:
>
>* De **Aanbiedingen** console is niet meer beschikbaar.
>* Het doelpictogram in de werkbalkbalk van andere betrokken componenten wordt niet meer weergegeven.

1. Open een pagina die de aanbieding voor bewerking bevat.

1. Overschakelen op **Targeting** voor die pagina.

1. Selecteren **Doelstelling starten**.

1. Selecteer de juiste (beoogde) component.

1. De componentwerkbalk biedt een optie voor **Omzetten in ervaring met fragmentvariatie**:

   ![Verouderde aanbieding omzetten in fragment](/help/sites-cloud/authoring/assets/offers-convert-legacy-icon.png)

1. Er wordt een dialoogvenster weergegeven. Hier kunt u de vereiste **Handeling**:

   * Een nieuw ervaringsfragment maken
   * De inhoud toevoegen aan een bestaand ervaringsfragment

   Voor dit scenario selecteert u **Een nieuw ervaringsfragment maken**.

   ![Omzetten in dialoogvenster Fragmentvariatie beleven](/help/sites-cloud/authoring/assets/offers-convert-dialog.png)

1. Vul de vereiste velden in het dialoogvenster in:

   * **Bovenliggend pad**
Het bovenliggende pad van het nieuwe ervaringsfragment opgeven
   * **Sjabloon**
Selecteer de sjabloon die u wilt gebruiken voor het maken van het ervaringsfragment.
   * **Fragmenttitel**
Geef de titel op.
   * **Fragmenttags**
Voeg indien nodig codes toe.

1. Bevestigen met **Gereed**.

   Als u nu naar de **Geniet van fragmentatieaanbiedingen** -console, kunt u het nieuwe ervaringsfragment zien, samen met de bijbehorende variaties.

### Aanwijzen met de aanbiedingensjabloon {#targeting-offers-template}

>[!CAUTION]
>
>Deze optie is alleen beschikbaar voor klanten met bestaande oudere aanbiedingen.
>
>Net als bij de **Aanbiedingen** -console is niet meer beschikbaar:
>
>* zodra het laatste verouderde aanbod is omgezet in Experience Fragments
>* wanneer oude aanbiedingen zijn verouderd (in de toekomst)
>
>Daarom is de geadviseerde optie het Fragmenten van de Ervaring te gebruiken, niet deze optie.

Voor klanten met bestaande, oudere aanbiedingen geldt dat de **Aanbiedingssjabloon gebruiken** opties zijn zichtbaar wanneer u zich richt op componenten die **niet** Geniet van fragmenten:

![Omzetten in dialoogvenster Fragmentvariatie beleven](/help/sites-cloud/authoring/assets/offers-legacy-target-non-experience-fragment.png)

## De aanbiedingenconsole {#offers-console}

>[!CAUTION]
>
>Deze console wordt afgekeurd in de toekomst, aangezien het een erfenismanier aanbiedt om inhoud te personaliseren.
>
>Je hebt wat tijd om je voor te bereiden. Zie hoe te [zet uw bestaande oude aanbiedingen om in een ervaringsfragmentaanbieding](#convert-legacy-offer-to-experience-fragment).

Gebruik de console van Aanbiedingen om aanbiedingen tot stand te brengen die u kunt [gebruik in de praktijk](/help/sites-cloud/authoring/personalization/targeted-content.md). Het creëren van aanbiedingen in de console van Aanbiedingen bespaart tijd wanneer verscheidene ervaringen de zelfde aanbieding vereisen:

* Maak het aanbod eenmaal in de bibliotheek en gebruik het in meerdere ervaringen met uw merkactiviteiten.
* Wijzig de aanbieding in de bibliotheek en de wijziging is van invloed op alle ervaringen die er gebruik van maken.

De console van Aanbiedingen organiseert aanbiedingen door merk. Elk merk bevat een bibliotheek met aanbiedingen die in de ervaringen van een merk kunnen worden gebruikt. Gebruik mappen om een hiërarchische structuur te definiëren voor het organiseren van aanbiedingen in elke bibliotheek. Met een logische mapstructuur kunnen auteurs eenvoudig aanbiedingen zoeken door te bladeren. Met tags en zoekgereedschappen kunnen auteurs ook aanbiedingen vinden.

### Een merk toevoegen met de aanbiedingsconsole {#add-a-brand-using-the-offers-console}

Maak een merk waaraan uw aanbiedingen zijn gekoppeld. Open een merk in de console van Aanbiedingen om tot zijn aanbiedingsbibliotheek toegang te hebben waar u omslagen en aanbiedingen kunt tot stand brengen.

Wanneer u een merk maakt met de console Aanbiedingen, wordt dit ook weergegeven in het dialoogvenster [Activiteitenconsole](/help/sites-cloud/authoring/personalization/activities.md) waar u activiteiten voor het merk kunt toevoegen en beheren.

1. Selecteer in de navigatieconsole de optie **Personalisatie** > **Aanbiedingen**.

   ![Navigeren naar de console Aanbiedingen](/help/sites-cloud/authoring/assets/offers-navigation.png)

1. Selecteren **Maken** en vervolgens **Maken** **Merk**.
1. Selecteer de merksjabloon en selecteer **Volgende**.
1. Typ een titel voor het merk zoals u deze wilt weergeven in de consoles van Aanbiedingen en Activiteiten. Typ of selecteer eventueel een of meer tags die u aan het merk wilt koppelen.
1. Selecteren **Maken**.

### Een map toevoegen aan een aanbiedingsbibliotheek {#add-a-folder-to-an-offer-library}

Voeg een map toe aan de aanbiedingsbibliotheek van een merk om aanbiedingen te organiseren en op te slaan. U kunt een map maken onder het merk of onder andere mappen.

1. Open in de console Aanbiedingen de locatie waar u de map wilt maken. Open bijvoorbeeld het merk om een map op hoofdniveau te maken of open een andere map in de bibliotheek.
1. Selecteren **Maken** > **Map of voorstel maken**.

   ![Aanbiedingsmap maken](/help/sites-cloud/authoring/assets/offers-create-folder.png)

1. Selecteren **Map** en klik op **Volgende**.
1. Typ een titel voor de map zoals u deze wilt weergeven in de aanbiedingsbibliotheek en typ of selecteer tags.

   ![Mapeigenschappen definiëren](/help/sites-cloud/authoring/assets/offers-folder-properties.png)

1. Selecteren **Maken**.

### Een voorstel toevoegen aan een bibliotheek met aanbiedingen {#add-an-offer-to-an-offer-library}

Voeg een aanbieding toe aan de aanbiedingsbibliotheek van een merk zodat deze aan de ervaringen van het merk kan worden toegevoegd. Als je een voorstel toevoegt, geef je een titel op. U kunt de aanbieding ook koppelen aan een of meer tags om de zoekbaarheid te verbeteren.

Nadat u het voorstel hebt gemaakt, kunt u het openen om de inhoud te ontwerpen.

1. In de console van Aanbiedingen, open de plaats waar u de aanbieding wilt tot stand brengen. Open bijvoorbeeld het merk om een aanbieding op hoofdniveau te maken of open een map in de bibliotheek.
1. Selecteren **Maken** > **Map of voorstel maken**.

   ![Aanbiedingsmap maken](/help/sites-cloud/authoring/assets/offers-create-folder.png)

1. Selecteer de **Pagina voorstellen** sjabloon en selecteer vervolgens **Volgende**.
1. Typ een titel voor de aanbieding en selecteer desgewenst een of meer tags die u aan de aanbieding wilt koppelen. Selecteer vervolgens **Maken**.
1. Selecteer in het bevestigingsdialoogvenster de optie voor het openen van de aanbieding voor bewerken **Pagina openen**.

### Een voorstel bewerken {#editing-an-offer}

Open een aanbieding en bewerk de inhoud zoals u die in de ervaringen wilt weergeven die het gebruiken. Als u een aanbieding bewerkt die in een willekeurige ervaring wordt gebruikt, worden de wijzigingen in de ervaringen weergegeven.

U kunt een voorstel van een omslag in een aanbiedingsbibliotheek of van onderzoeksresultaten openen. Je kunt ook een voorstel openen vanuit een ervaring die gebruikmaakt van het voorstel.

1. Selecteer in de console Aanbiedingen het pictogram naast de aanbieding en selecteer **Bewerken**.
1. Voeg componenten toe aan de aanbieding en bewerk de componenteninhoud zoals gebruikelijk.

### Een voorstel verwijderen {#deleting-an-offer}

Een voorstel verwijderen wanneer het niet meer nodig is. Wanneer u een aanbieding probeert te verwijderen die in een ervaring wordt gebruikt, wordt u gevraagd de verwijdering te bevestigen. Als u bevestigt, wordt het aanbod verwijderd en wordt het uit de ervaringen verwijderd.

U kunt een aanbieding verwijderen terwijl u de mapinhoud in een aanbiedingsbibliotheek of de zoekresultaten bekijkt.

1. Selecteer in de console Aanbiedingen het pictogram naast de aanbieding en selecteer **Verwijderen**.

   Selecteer de aanbieding en selecteer **Verwijderen**.

1. Selecteer in het dialoogvenster dat wordt weergegeven **Verwijderen** om de schrapping te bevestigen.
1. Als de aanbieding in een of meer ervaringen wordt gebruikt, verschijnt er een dialoogvenster waarin wordt aangegeven dat naar de aanbieding wordt verwezen:

   * Als u het voorstel wilt verwijderen en uit de ervaringen wilt verwijderen, selecteert u **Verwijderen forceren**.
   * Selecteer **Annuleren**.

### Zoeken naar voorstellen {#searching-for-offers}

Zoek naar voorstellen van om het even welk merk gebruikend sleutelwoorden om de titel te passen.

![Zoeken naar een voorstel](/help/sites-cloud/authoring/assets/offers-search.png)

De huidige zoekcriteria worden naast de zoekresultaten weergegeven. U kunt de resultaten ook in oplopende of aflopende volgorde op kolom sorteren. U kunt een onderzoek van om het even welke omslag van om het even welke aanbiedingsbibliotheek uitvoeren. De zoekresultaten zijn hetzelfde, ongeacht de huidige map.

Zoekvoorstellen:

1. Selecteer boven aan de console Aanbiedingen het vergrootglaspictogram. Standaard is de zoekopdracht beperkt tot voorstellen.
1. Voer uw trefwoord in om naar voorstellen te zoeken. Maak een keuze uit de resultaten.
