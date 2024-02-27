---
title: Tijdlijnweergave voor AEM Screens configureren
description: Deze pagina beschrijft hoe u een tijdlijnweergave in as a Cloud Service schermen configureert.
source-git-commit: 30317d006142b3fbfc1b62fab5b4e28cb1b7dbb7
workflow-type: tm+mt
source-wordcount: '819'
ht-degree: 0%

---

# Tijdlijnweergave voor AEM Screens configureren {#configuring-timelineview-screens}

## Inleiding {#introduction}

In deze sectie wordt beschreven hoe u een tijdlijnweergave voor AEM Screens kunt maken.

AEM biedt een reeks functies waarmee meerdere personen in groepen in een organisatie kunnen samenwerken aan het maken, beheren en gebruiken van kanalen.
De tijdlijn, die zich in de linkerbar bevindt, beschrijft de kanalen, de plaats, of de het levenscyclus van om het even welke het schermomslag in tijd om te tonen wat met het over zijn leven is gebeurd. Dit kan naar beneden door type worden gefiltreerd.
De tijdlijn biedt naast de logboeken van de levenscyclus ook de volgende functies.

![Profiel toepassen op map](/help/screens-cloud/assets/configure/Screens-timeline1.jpg)

![Profiel toepassen op map](/help/screens-cloud/assets/configure/screens-timeline2.jpg)

Voer de volgende stappen uit om een tijdlijnweergave voor AEM Screens te maken:

1. Een opmerking toevoegen
1. Een versie opslaan
1. Een workflow starten

In de volgende sectie worden deze stappen gedetailleerd beschreven.

### Een opmerking toevoegen {#addcomment}

Door opmerkingen beschikbaar te maken via de tijdlijn kunnen gebruikers een gecentraliseerde en historische record maken voor discussies over het kanaal, de locatie of een map op het scherm.
Opmerkingen bieden een mooie geconsolideerde manier voor AEM gebruikers om een manier te bespreken die kan worden voortgezet, zodat anderen belangrijke beslissingen kunnen begrijpen.

1. Ga naar het kanaal waaraan u een opmerking wilt toevoegen
1. Selecteer het kanaal
1. De kolom Tijdlijn openen
1. Voeg de gewenste opmerking toe en druk op Enter

![Een opmerking toevoegen](/help/screens-cloud/assets/configure/screen-timeline3.jpg)

De informatie in de tijdlijn wordt bijgewerkt om aan te geven dat de opmerking is toegevoegd.

![Een opmerking toevoegen](/help/screens-cloud/assets/configure/screens-timeline4.jpg)

### Versie opslaan {#saveversion}

Met Versioning maakt u een &#39;momentopname&#39; van een kanaal op een bepaald tijdstip. Met versioning kunt u de volgende handelingen uitvoeren:
* Maak een versie van een kanaal.
* Een kanaal terugzetten naar een vorige versie, bijvoorbeeld:
   * om een wijziging die u hebt aangebracht in de pagina ongedaan te maken.
* Vergelijk de huidige versie van een kanaal met een vorige versie:
   * om verschillen in de kanaalinhoud te benadrukken.


#### Een nieuwe versie maken {#createnewversion}

1. Ga naar het kanaal waaraan u een opmerking wilt toevoegen
1. Selecteer het kanaal
1. De kolom Tijdlijn openen
1. Klik op de knop (drie punten) in het veld Opmerking onderaan.

   ![Een opmerking toevoegen](/help/screens-cloud/assets/configure/screens-timeline5.jpg)

1. Opslaan als versie selecteren
1. Voer indien nodig een label en opmerking in

   ![Een opmerking toevoegen](/help/screens-cloud/assets/configure/screens-timeline6.jpg)

1. Bevestig de nieuwe versie met Maken. De informatie in de tijdlijn wordt bijgewerkt en geeft de nieuwe versie aan.

#### Een versie herstellen {#revertversion}

De geselecteerde pagina herstellen naar een vorige versie:
1. Ga naar het kanaal waaraan u een opmerking wilt toevoegen
1. Selecteer het kanaal
1. De kolom Tijdlijn openen
1. Selecteer Alle of Versies tonen in het keuzemenu met filters. De kanaalversies voor het geselecteerde kanaal worden weergegeven
1. Selecteer de versie waarnaar u wilt terugkeren. De mogelijke opties worden weergegeven:

   ![Een opmerking toevoegen](/help/screens-cloud/assets/configure/screens-timeline7.jpg)

1. Selecteer Vorige versie. De geselecteerde versie wordt hersteld en de informatie in de tijdlijn wordt bijgewerkt

#### Een versie voorvertonen {#previewversion}

U kunt een voorvertoning van een specifieke versie weergeven:
1. Ga naar het kanaal waaraan u een opmerking wilt toevoegen
1. Selecteer het kanaal
1. De kolom Tijdlijn openen
1. Selecteer Alle of Versies tonen in het keuzemenu met filters. De kanaalversies voor het geselecteerde kanaal worden weergegeven
1. Selecteer de versie die u wilt voorvertonen. De mogelijke opties worden weergegeven:

   ![Voorvertoning versie](/help/screens-cloud/assets/configure/screens-timeline8.jpg)

1. Selecteer Voorvertoning. Het kanaal wordt weergegeven op een nieuw tabblad.

#### Een versie vergelijken met de huidige versie {#compareversion}

U kunt een specifieke versie vergelijken met de huidige versie:
1. Ga naar het kanaal waaraan u een opmerking wilt toevoegen
1. Selecteer het kanaal
1. De kolom Tijdlijn openen
1. Selecteer Alle of Versies tonen in het keuzemenu met filters. De kanaalversies voor het geselecteerde kanaal worden weergegeven
1. Selecteer de versie die u wilt vergelijken. De mogelijke opties worden weergegeven:

   ![Versie vergelijken](/help/screens-cloud/assets/configure/screens-timeline9.jpg)

1. Selecteer Vergelijken met huidige. De pop-up wordt geopend om de verschillen te tonen

### Een workflow starten {#workflowstart}

Tijdens het ontwerpen kunt u workflows aanroepen om actie te ondernemen op uw kanalen. Het is ook mogelijk om meerdere workflows toe te passen.
Wanneer u de workflow toepast, geeft u de volgende informatie op:
* De workflow die moet worden toegepast
* Naar keuze, een titel die helpt de werkschemainstantie in Inbox van een gebruiker identificeren
* Het laden van de workflow

#### De workflow starten

1. Ga naar het kanaal waaraan u een opmerking wilt toevoegen
1. Selecteer het kanaal
1. De kolom Tijdlijn openen
1. Klik op de knop (drie punten) in het veld Opmerking onderaan

   ![Workflow starten](/help/screens-cloud/assets/configure/screens-timeline10.jpg)

1. Start Workflow selecteren
1. De wizard Werkstroom maken wordt geopend en geeft de werkstroomgegevens op
1. Selecteer workflowmodel in de vervolgkeuzelijst en voer de titel van de workflow in

   ![Workflow starten](/help/screens-cloud/assets/configure/screens-timeline11.jpg)

1. Ga verder door op Volgende te klikken
1. In de stap Bereik kunt u
* Inhoud toevoegen om extra bronnen aan de workflow toe te voegen
* Inclusief onderliggende elementen om op te geven dat onderliggende elementen van die bron worden opgenomen in de workflow
* Selectie verwijderen om die bron uit de workflow te verwijderen

  ![Workflow starten](/help/screens-cloud/assets/configure/screens-timeline12.jpg)

1. Gebruik Maken om de wizard te sluiten en de werkstroominstantie te maken
1. Afhankelijk van het geselecteerde workflowmodel moet u mogelijk enkele aanvullende acties uitvoeren om de workflow te voltooien

![Workflow starten](/help/screens-cloud/assets/configure/screens-timeline13.jpg)
