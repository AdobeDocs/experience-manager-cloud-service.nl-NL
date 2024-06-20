---
title: Tijdlijnweergave voor AEM Screens configureren
description: Deze pagina beschrijft hoe u een tijdlijnweergave in as a Cloud Service schermen configureert.
exl-id: 53afe1f5-8f0b-4cca-a819-d3e9375cbe37
feature: Administering Screens
role: Admin, Developer, User
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '813'
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

In de volgende secties worden deze stappen gedetailleerd beschreven.

### Een opmerking toevoegen {#addcomment}

Door opmerkingen beschikbaar te maken via de tijdlijn kunnen gebruikers een gecentraliseerde en historische record maken voor discussies over het kanaal, de locatie of een map op het scherm.
Opmerkingen bieden een mooie geconsolideerde manier voor AEM gebruikers om een manier te bespreken die kan worden voortgezet, zodat anderen belangrijke beslissingen kunnen begrijpen.

1. Navigeer naar het kanaal waaraan u een opmerking wilt toevoegen.
1. Selecteer het kanaal.
1. Open de **Tijdlijn** kolom.
1. Voeg uw opmerking toe en druk op **Enter**.

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

1. Navigeer naar het kanaal waaraan u een opmerking wilt toevoegen.
1. Selecteer het kanaal.
1. Open de **Tijdlijn** kolom.
1. Klik op de knop (drie punten) in het veld Opmerking onder aan de pagina.

   ![Een opmerking toevoegen](/help/screens-cloud/assets/configure/screens-timeline5.jpg)

1. Selecteren **Opslaan als versie**.
1. Voer een **Label** en **Opmerking** voor de versie.

   ![Een opmerking toevoegen](/help/screens-cloud/assets/configure/screens-timeline6.jpg)

1. Bevestig de nieuwe versie door **Maken**.De informatie in de tijdlijn wordt bijgewerkt om op de nieuwe versie te wijzen.

#### Een versie herstellen {#revertversion}

De geselecteerde pagina herstellen naar een vorige versie:

1. Blader naar het kanaal om een opmerking toe te voegen.
1. Selecteer het kanaal.
1. Open de **Tijdlijn** kolom.
1. Selecteer een van beide **Alles tonen** of **Versies** in de vervolgkeuzelijst met filters. De kanaalversies voor het geselecteerde kanaal worden vermeld.
1. Selecteer de versie waarnaar u wilt terugkeren. De mogelijke opties worden weergegeven:

   ![Een opmerking toevoegen](/help/screens-cloud/assets/configure/screens-timeline7.jpg)

1. Selecteren **Deze versie herstellen**. De geselecteerde versie wordt hersteld en de informatie in de tijdlijn wordt bijgewerkt.

#### Een versie voorvertonen {#previewversion}

U kunt een voorvertoning van een specifieke versie weergeven:

1. Blader naar het kanaal om een opmerking toe te voegen.
1. Selecteer het kanaal.
1. Open de **Tijdlijn** kolom.
1. Selecteer een van beide **Alles tonen** of **Versies** in de vervolgkeuzelijst met filters. De kanaalversies voor het geselecteerde kanaal worden vermeld.
1. Selecteer de versie die u wilt voorvertonen. De mogelijke opties worden weergegeven:

   ![Voorvertoning versie](/help/screens-cloud/assets/configure/screens-timeline8.jpg)

1. Selecteren **Voorvertoning**. Het kanaal wordt weergegeven op een nieuw tabblad.

#### Een versie vergelijken met de huidige versie {#compareversion}

U kunt een specifieke versie vergelijken met de huidige versie:

1. Navigeer naar het kanaal waaraan u een opmerking wilt toevoegen.
1. Selecteer het kanaal.
1. Open de **Tijdlijn** kolom
1. Selecteer een van beide **Alles tonen** of **Versies** in de vervolgkeuzelijst met filters. De kanaalversies voor het geselecteerde kanaal worden vermeld.
1. Selecteer de versie die u wilt vergelijken. De mogelijke opties worden weergegeven:

   ![Versie vergelijken](/help/screens-cloud/assets/configure/screens-timeline9.jpg)

1. Selecteren **Vergelijken met huidige**. De popup opent om de verschillen te tonen.

### Een workflow starten {#workflowstart}

Tijdens het ontwerpen kunt u workflows aanroepen om actie te ondernemen op uw kanalen. Het is ook mogelijk om meerdere workflows toe te passen.
Wanneer u de workflow toepast, geeft u de volgende informatie op:

* De workflow die moet worden toegepast.
* Naar keuze, een titel die helpt de werkschemainstantie in Inbox van een gebruiker identificeren.
* De lading van de werkstroom.

#### De workflow starten

1. Navigeer naar het kanaal waaraan u een opmerking wilt toevoegen.
1. Selecteer het kanaal.
1. Open de **Tijdlijn** kolom.
1. Klik op de knop (drie punten) in het veld Opmerking onderaan.

   ![Workflow starten](/help/screens-cloud/assets/configure/screens-timeline10.jpg)

1. Selecteren **Workflow starten**.
1. De wizard Werkstroom maken wordt geopend en geeft de workflowdetails op.
1. Selecteren **Workflowmodel** in de vervolgkeuzelijst en voer de titel Werkstroom in.

   ![Workflow starten](/help/screens-cloud/assets/configure/screens-timeline11.jpg)

1. Doorgaan door te klikken **Volgende**.
1. In de bereikstap kunt u:
   * **Inhoud toevoegen** om extra bronnen aan de workflow toe te voegen.
   * **Inclusief onderliggende items** om te specificeren dat de kinderen van die bron in het werkschema zullen worden omvat.
   * **Selectie verwijderen** om die bron uit de workflow te verwijderen.

   ![Workflow starten](/help/screens-cloud/assets/configure/screens-timeline12.jpg)

1. Selecteren **Maken** om de wizard te sluiten en de instantie van de workflow te maken.
1. Afhankelijk van het geselecteerde workflowmodel moet u mogelijk enkele aanvullende acties uitvoeren om de workflow te voltooien.

   ![Workflow starten](/help/screens-cloud/assets/configure/screens-timeline13.jpg)
