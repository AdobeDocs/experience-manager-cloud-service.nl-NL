---
title: Tijdlijnweergave voor AEM Screens configureren
description: Op deze pagina wordt beschreven hoe u een tijdlijnweergave in Screens as a Cloud Service configureert.
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

![&#x200B; pas Profiel op Omslag &#x200B;](/help/screens-cloud/assets/configure/Screens-timeline1.jpg) toe

![&#x200B; pas Profiel op Omslag &#x200B;](/help/screens-cloud/assets/configure/screens-timeline2.jpg) toe

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
1. Open de **kolom van de Chronologie**.
1. Voeg uw commentaar toe en druk **binnengaan**.

![&#x200B; voeg een Commentaar &#x200B;](/help/screens-cloud/assets/configure/screen-timeline3.jpg) toe

De informatie in de tijdlijn wordt bijgewerkt om aan te geven dat de opmerking is toegevoegd.

![&#x200B; voeg een Commentaar &#x200B;](/help/screens-cloud/assets/configure/screens-timeline4.jpg) toe

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
1. Open de **kolom van de Chronologie**.
1. Klik op de knop (drie punten) in het veld Opmerking onder aan de pagina.

   ![&#x200B; voeg een Commentaar &#x200B;](/help/screens-cloud/assets/configure/screens-timeline5.jpg) toe

1. Selecteer **sparen als Versie**.
1. Ga a **Etiket** en **Commentaar** voor de versie in.

   ![&#x200B; voeg een Commentaar &#x200B;](/help/screens-cloud/assets/configure/screens-timeline6.jpg) toe

1. Bevestig de nieuwe versie door te selecteren **creeer**. De informatie in de chronologie wordt bijgewerkt om op de nieuwe versie te wijzen.

#### Een versie herstellen {#revertversion}

De geselecteerde pagina herstellen naar een vorige versie:

1. Blader naar het kanaal om een opmerking toe te voegen.
1. Selecteer het kanaal.
1. Open de **kolom van de Chronologie**.
1. Selecteer of **tonen Al** of **Versies** van de filterdrop. De kanaalversies voor het geselecteerde kanaal worden vermeld.
1. Selecteer de versie waarnaar u wilt terugkeren. De mogelijke opties worden weergegeven:

   ![&#x200B; voeg een Commentaar &#x200B;](/help/screens-cloud/assets/configure/screens-timeline7.jpg) toe

1. Selecteer **terugkeren aan deze Versie**. De geselecteerde versie wordt hersteld en de informatie in de tijdlijn wordt bijgewerkt.

#### Een versie voorvertonen {#previewversion}

U kunt een voorvertoning van een specifieke versie weergeven:

1. Blader naar het kanaal om een opmerking toe te voegen.
1. Selecteer het kanaal.
1. Open de **kolom van de Chronologie**.
1. Selecteer of **tonen Al** of **Versies** van de filterdrop. De kanaalversies voor het geselecteerde kanaal worden vermeld.
1. Selecteer de versie die u wilt voorvertonen. De mogelijke opties worden weergegeven:

   ![&#x200B; Versie van de Voorproef &#x200B;](/help/screens-cloud/assets/configure/screens-timeline8.jpg)

1. Selecteer **Voorproef**. Het kanaal wordt weergegeven op een nieuw tabblad.

#### Een versie vergelijken met de huidige versie {#compareversion}

U kunt een specifieke versie vergelijken met de huidige versie:

1. Navigeer naar het kanaal waaraan u een opmerking wilt toevoegen.
1. Selecteer het kanaal.
1. Open de **kolom van de Chronologie**
1. Selecteer of **tonen Al** of **Versies** van de filterdrop. De kanaalversies voor het geselecteerde kanaal worden vermeld.
1. Selecteer de versie die u wilt vergelijken. De mogelijke opties worden weergegeven:

   ![&#x200B; vergelijk Versie &#x200B;](/help/screens-cloud/assets/configure/screens-timeline9.jpg)

1. Selecteer **vergelijken met Huidige**. De popup opent om de verschillen te tonen.

### Een workflow starten {#workflowstart}

Tijdens het ontwerpen kunt u workflows aanroepen om actie te ondernemen op uw kanalen. Het is ook mogelijk om meerdere workflows toe te passen.
Wanneer u de workflow toepast, geeft u de volgende informatie op:

* De workflow die moet worden toegepast.
* Naar keuze, een titel die helpt de werkschemainstantie in Inbox van een gebruiker identificeren.
* De lading van de werkstroom.

#### De workflow starten

1. Navigeer naar het kanaal waaraan u een opmerking wilt toevoegen.
1. Selecteer het kanaal.
1. Open de **kolom van de Chronologie**.
1. Klik op de knop (drie punten) in het veld Opmerking onderaan.

   ![&#x200B; Werkschema van het Begin &#x200B;](/help/screens-cloud/assets/configure/screens-timeline10.jpg)

1. Selecteer **Werkschema van het Begin**.
1. De wizard Werkstroom maken wordt geopend en geeft de workflowdetails op.
1. Selecteer **model van het Werkschema** van de dropdown lijst en ga de titel van het Werkschema in.

   ![&#x200B; Werkschema van het Begin &#x200B;](/help/screens-cloud/assets/configure/screens-timeline11.jpg)

1. Ga door **daarna** te klikken.
1. In de bereikstap kunt u:
   * **voegt Inhoud** toe om extra middelen aan het werkschema toe te voegen.
   * **omvat kinderen** om te specificeren dat de kinderen van dat middel in het werkschema zullen worden omvat.
   * **verwijder Selectie** om dat middel uit het werkschema te verwijderen.

   ![&#x200B; Werkschema van het Begin &#x200B;](/help/screens-cloud/assets/configure/screens-timeline12.jpg)

1. Selecteer **creeer** om de tovenaar te sluiten en de werkschemainstantie tot stand te brengen.
1. Afhankelijk van het geselecteerde workflowmodel moet u mogelijk enkele aanvullende acties uitvoeren om de workflow te voltooien.

   ![&#x200B; Werkschema van het Begin &#x200B;](/help/screens-cloud/assets/configure/screens-timeline13.jpg)
