---
title: Starten voor inhoudsfragmenten
description: Leer hoe u Launches kunt gebruiken voor inhoudsfragmenten in Adobe Experience Manager as a Cloud Service. Met behulp van Starten kunt u op efficiënte wijze inhoud ontwikkelen voor een toekomstige release, terwijl uw huidige contentfragmenten behouden blijven.
feature: Content Fragments
role: User, Developer, Architect
hide: true
hidefromtoc: true
index: false
solution: Experience Manager Sites
source-git-commit: f2adbc7fd92e846c6e09e52644f45c720c04dc4e
workflow-type: tm+mt
source-wordcount: '1582'
ht-degree: 0%

---


# Starten voor inhoudsfragmenten {#launches-for-content-fragments}

Met Launches kunt u in Adobe Experience Manager (AEM) as a Cloud Service op efficiënte wijze inhoud ontwikkelen voor een toekomstige release.

A *Lancering* wordt gecreeerd om u toe te staan om veranderingen in voorbereiding op toekomstige publicatie aan te brengen, tezelfdertijd als het handhaven van uw huidige inhoud. Voor Inhoudsfragmenten betekent dit dat u in feite twee versies tegelijk bewerkt: inhoud die momenteel is gepubliceerd en een versie van die inhoud die in de toekomst tegelijk moet worden gepubliceerd. Zodra dat tijdstip is bereikt, kunt u de inhoud van de oorspronkelijke inhoudsfragmenten vervangen en de nieuwe versies publiceren.

>[!NOTE]
>
>Startpagina&#39;s zijn ook beschikbaar. De basisbegrippen zijn hetzelfde, maar er zijn verschillen in de manier waarop ze in AEM moeten worden beheerd.
>
>Voor volledige details zie [ Lanceringen voor Pagina&#39;s ](/help/sites-cloud/authoring/launches/overview.md).

U creeert a *Lancering*, dan uitgeeft en werkt uw Fragmenten van de Inhoud in uw *Lancering* bij. Als de veranderingen in de *fragmenten van Source* tijdens deze fase worden aangebracht, kunt u hen kopiëren aan *Lancering* met *Rebase* verrichting. Wanneer klaar, *bevordert* de lanceringsinhoud terug naar de bron. Vervolgens kunt u de bronfragmenten handmatig of automatisch activeren (afhankelijk van de velden die zijn ingesteld bij het maken en bewerken van de opstart). U kunt ook opgeven of fragmenten waarnaar wordt verwezen, in dit proces moeten worden opgenomen.

Bijvoorbeeld, worden de seizoensgebonden productfragmenten van uw online opslag bijgewerkt driemaandelijks zodat de gekenmerkte producten zich aan het huidige seizoen richten. Als u de volgende driemaandelijkse update wilt voorbereiden, kunt u de juiste fragmenten starten. In het hele kwartaal worden de volgende wijzigingen in de opstartafbeelding opgebouwd:

* Bewerkingen die rechtstreeks worden uitgevoerd op de opstartfragmenten ter voorbereiding op het volgende kwartaal.
* Veranderingen in de BronFragmenten van de Inhoud die u aan de lanceringspagina&#39;s met *opnieuw baseert* overbrengt.
* U kunt ook door de inhoud in de opstartaftakking navigeren; zo nodig fragmenten toevoegen of verwijderen.

Wanneer het volgende kwartaal arriveert, publiceert u de startpagina&#39;s, zodat u de bronpagina&#39;s kunt publiceren (met de bijgewerkte inhoud). U kunt alle fragmenten opwaarderen of alleen de fragmenten die u hebt gewijzigd.

![ Overzicht van Lanceringen - Rebase en bevordert ](/help/sites-cloud/administering/content-fragments/assets/cf-launches-overview.png)

Deze sectie beschrijft om, te creëren uit te geven, te beheren, opnieuw te baseren, te bevorderen en indien nodig te schrappen, lanceert van binnen de [ console van de Fragmenten van de Inhoud ](/help/sites-cloud/administering/content-fragments/managing.md):

* [Starten openen en weergeven in de Content Fragment-console](#launches-in-the-content-fragment-console)
* [Een start maken](#create-a-launch)
* [Starten van inhoud bewerken](#edit-launch-content)
* [Inhoud beheren in een opstartprogramma](#manage-content-within-a-launch)
* [Starten vergelijken met Source](#compare-launch-to-source)
* [Starten vanuit Source opnieuw baseren](#rebase-a-launch-from-source)
* [Een introductie naar Source promoten](#promote-a-launch-to-source)
* [Een Starten verwijderen](#delete-a-launch)

## Starten in de Content Fragment Console {#launches-in-the-content-fragment-console}

Het **lusje van Lanceringen** van de console van de Fragmenten van de Inhoud staat u toe om lanceringen tot stand te brengen, van alle bestaande lanceringen een lijst te maken, zeer belangrijke eigenschappen te zien, en acties op hen te nemen.

Wanneer geen lancering wordt geselecteerd kunt u [ een nieuwe lancering ](#create-a-launch) tot stand brengen.

![ Lanceringen lusje in console ](/help/sites-cloud/administering/content-fragments/assets/cf-launches-tab.png)

Selecteer de lancering om te tonen:

* de werkbalk, met de beschikbare acties
* in het rechterdeelvenster, eigenschappen en verdere handelingen weergeven

![ de actiestoolbar van de Lancering in console ](/help/sites-cloud/administering/content-fragments/assets/cf-launches-actions.png)

Met de werkbalk kunt u:

* **[Open Lancering](#edit-launch-content)**
* **[geeft Bronnen](#manage-content-within-a-launch)** uit
* **[vergelijk Lancering aan Source](#compare-launch-to-source)**
* **[bevorderen](#promote-a-launch-to-source)**
* **[Rebase](#promote-a-launch-to-source)**
* **[Schrapping Lancering](#delete-a-launch)**

In het rechterdeelvenster kunt u:

* Bewerk de Titel van de Lancering ****
* Bewerk de Beschrijving van de Lancering ****
* De configuratiedetails van de update die werden geplaatst toen u [ de lancering ](#create-a-launch) creeerde:

   * **omvat verwijzingen**: Creeer de Lancering of met, of zonder, met inbegrip van om het even welke referenced Fragments van de Inhoud. Standaard worden fragmenten waarnaar wordt verwezen, opgenomen.

      * De fragmenten van verwijzingen worden ook beïnvloed wanneer u [ toevoegt, of fragmenten uit de lancering ](#manage-content-within-a-launch) in een recentere fase verwijdert.

     >[!NOTE]
     >
     >Zie [ Details betreffende Included Verwijzingen ](#details-concerning-included-references)

   * **publiceer Klaar**; het toelaten van deze knevel zal automatisch de fragmenten publiceren wanneer de lancering aan de bron wordt bevorderd.

* En definieer ook:

   * A **bevordert Datum** en Tijd: als de [ lancering automatisch moet worden bevorderd ](#promote-automatically)

## Een start maken {#create-a-launch}

Om uw lancering te creëren:

1. Navigeer naar de console Inhoudsfragmenten.

1. Open **Lanceringen** tabel.

1. Selecteer **creeer Lancering**.

1. Navigeer naar de juiste map en selecteer de fragmenten die u wilt opnemen in de startpagina:

   ![ selecteer inhoudsfragmenten voor nieuwe lancering ](/help/sites-cloud/administering/content-fragments/assets/cf-launches-create-select-cfs.png)

1. Selecteer **daarna**.

1. Geef details op om het starten te configureren:

   * **Titel**
   * **Beschrijving**
   * **omvat Verwijzingen**: Creeer de Lancering of met, of zonder, met inbegrip van om het even welke referenced Fragments van de Inhoud. Standaard worden fragmenten waarnaar wordt verwezen, opgenomen.

     >[!NOTE]
     >
     >Zie [ Details betreffende Included Verwijzingen ](#details-concerning-included-references)

   * **publiceer Klaar**: Het toelaten van deze knevel zal automatisch de fragmenten publiceren wanneer de lancering aan de bron wordt bevorderd.

   ![ Details voor nieuwe lancering ](/help/sites-cloud/administering/content-fragments/assets/cf-launches-create-launch-details.png)

1. **sparen** de configuratie.

1. U bent teruggekeerd aan het **1} lusje van Lanceringen {van de console van de Fragmenten van de Inhoud, waar:**

   * uw nieuwe lancering nu vermeld
   * er wordt een bericht weergegeven om te bevestigen dat de lancering is gestart :

      * **Baan begon om nieuwe Lancering tot stand te brengen, de vooruitgang in AEM te controleren en pagina opnieuw te laden wanneer gedaan.**

1. Selecteer **Mening**, van het berichtvakje, om verdere details in de console van AEM voor [ de Verrichtingen van de Achtergrond ](/help/operations/asynchronous-jobs.md) te zien.

   ![ Nieuwe lancering in console ](/help/sites-cloud/administering/content-fragments/assets/cf-launches-new-launch-in-console.png)

## Starten van inhoud bewerken {#edit-launch-content}

U bewerkt als volgt de inhoudsfragmenten in uw opstart:

1. Navigeer naar de console Inhoudsfragmenten.

1. Open **Lanceringen** tabel.

1. Selecteer uw lancering om de toolbaracties te tonen.

1. Selecteer **Open Lancering**.

   De opstart wordt samen met de fragmenten weergegeven.

   ![ geef de inhoud van de Lancering ](/help/sites-cloud/administering/content-fragments/assets/cf-launches-edit-launch-content.png) uit

1. Selecteer **uitgeven** voor het fragment u wilt bijwerken. Het zal in de [ fragmentredacteur ](/help/sites-cloud/administering/content-fragments/authoring.md) zoals gebruikelijk openen.

## Inhoud beheren in een opstartprogramma {#manage-content-within-a-launch}

U beheert als volgt de inhoudsfragmenten in uw opstart en bewerkt ook de inhoud ervan:

1. Navigeer naar de console Inhoudsfragmenten.

1. Open **Lanceringen** tabel.

1. Selecteer uw lancering.

1. Selecteer **uitgeven Bronnen**.

   De bronfragmenten van de opstart worden weergegeven.

   ![ geef Source ](/help/sites-cloud/administering/content-fragments/assets/cf-launches-edit-sources.png) uit

1. U kunt:

   1. **voeg Bronnen** toe om meer fragmenten aan uw lancering toe te voegen.

      * Als **omvat Verwijzingen** waar voor de lancering is, zullen alle referenced Fragments van de Inhoud ook in lancering worden gebracht (als niet reeds aanwezig).

   1. Selecteer **uitgeven** voor het bronfragment u wilt bijwerken. Het zal in de [ fragmentredacteur ](/help/sites-cloud/administering/content-fragments/authoring.md) zoals gebruikelijk openen.

   1. Selecteer een fragment, dan de **Bron van de Schrapping** actie van de toolbar om dat fragment uit de lancering te verwijderen.

      * Als **omvat Verwijzingen** waar voor de lancering is, zullen alle referenced Fragments van de Inhoud ook worden verwijderd uit de lancering - tenzij zij ook door andere Fragments van de Inhoud nog in de lancering van verwijzingen worden voorzien.

   >[!NOTE]
   >
   >Zie [ Details betreffende Included Verwijzingen ](#details-concerning-included-references)

## Starten vergelijken met Source {#compare-launch-to-source}

U wordt aangeraden om vóór elke actie Rebase of Promote altijd de bron te vergelijken en de toepassing te starten om de wijzigingen en hun effect op uw inhoud te bevestigen (beide acties overschrijven de doelinhoud):

1. Navigeer naar de console Inhoudsfragmenten.

1. Open **Lanceringen** tabel.

1. Selecteer uw lancering.

1. Selecteer **Vergelijk Lancering aan Source**.

   * De bron- en lanceerfragmenten worden naast elkaar weergegeven om de verschillen te benadrukken.
      * Source-fragmenten worden links weergegeven en opstartfragmenten rechts.
      * Updates worden gemarkeerd:
         * Source: blauw
         * Starten: roze
         * Conflicten: geel
   * [ bevordert ](#promote-a-launch-to-source) en [ rebase ](#rebase-a-launch-from-source) acties zijn beschikbaar van het hoogste recht.
   * **Gevonden Updates**: In de hogere linkerzijde, wordt een samenvatting van alle updates getoond. Het aantal bronupdates in blauw, het aantal opstartupdates in roze en updates voor beide (conflicten) in geel.
      * Met de oogpictogrammen kunt u de daadwerkelijke updates van de inhoud weergeven of verbergen voor een duidelijker overzicht.
   * **omvat** schuif staat u toe om de Fragmenten te bepalen van de Inhoud die in verdere Bevorderen of opnieuw te baseren verrichting moeten worden omvat:
      * **omvat allen** bij het hoogste recht
      * **omvat** boven elk fragment in de lancering

     >[!NOTE]
     >
     >De schuifregelaars zijn alleen van toepassing op acties die zijn genomen via het scherm Vergelijken, bevorderen en opnieuw baseren.

   * De inhoud van het fragment wordt getoond op gebied-niveau (het element van het Fragment van de Inhoud/datatype-niveau); met hoogtepunten die op veranderingen wijzen.
   * Selecteer **Mening** om de verschillen opnieuw samen te stellen.

   ![ vergelijk Source en Lancering ](/help/sites-cloud/administering/content-fragments/assets/cf-launches-compare.png)

## Starten opnieuw baseren (vanuit Source) {#rebase-a-launch-from-source}

Wanneer de bronfragmenten zijn bijgewerkt en u deze wijzigingen wilt kopiëren naar de opstart:

1. Navigeer naar de console Inhoudsfragmenten.

1. Open **Lanceringen** tabel.

1. Selecteer de opstart en fragmenten.

1. Selecteer **Rebase**.

>[!NOTE]
>
>U kunt **een lancering van**[ ook opnieuw vestigen **{vergelijken Lancering aan Source](#compare-launch-to-source)**.

## Starten bevorderen (naar Source) {#promote-a-launch-to-source}

Wanneer uw lancering klaar is om te worden gepubliceerd zou het aan de bron moeten worden gekopieerd. U kunt of dit in de console doen, of de montages vormen voor het om automatisch op een specifieke datum en een tijd te gebeuren.

### Handmatig promoten {#promote-manually}

Wanneer uw lancering klaar is om te worden gepubliceerd kan het aan de bron met de expliciete actie worden gekopieerd:

1. Navigeer naar de console Inhoudsfragmenten.

1. Open **Lanceringen** tabel.

1. Selecteer de opstart en fragmenten.

1. Selecteer **bevorderen**.

>[!NOTE]
>
>U kunt **ook bevorderen 1} een lancering van** Begin aan Source **vergelijken.**

### Automatisch bevorderen {#promote-automatically}

Als u een opstart automatisch wilt promoten op een bepaalde datum en tijd, moet u:

1. Bepaal **bevorderen Datum** en Tijd van het juiste paneel van het [ lusje van Lanceringen ](#launches-in-the-content-fragment-console).

1. Als de inhoud kan worden gepubliceerd wanneer het wordt bevorderd, plaats **publiceert Klaar** wanneer [ creërend de lancering ](#create-a-launch), of van het juiste paneel van het [ lusje van Lanceringen ](#launches-in-the-content-fragment-console).

## Een Starten verwijderen {#delete-a-launch}

Nadat u de introductie hebt bevorderd of hebt besloten dat u deze niet meer nodig hebt, kunt u deze verwijderen:

1. Navigeer naar de console Inhoudsfragmenten.

1. Open **Lanceringen** tabel.

1. Selecteer uw lancering.

1. Selecteer **Lanceer van de Schrapping**.

   U wordt gevraagd de actie te bevestigen voordat de lancering wordt geschrapt.

## Gegevens betreffende de opgenomen verwijzingen {#details-concerning-included-references}

Voor Lanceringen worden de volgende verwijzingen van het Fragment van de Inhoud overwogen, afhankelijk van [ gegevenstype ](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#data-types):

* Het **gegevenstype van de Verwijzing van het Fragment**, toepasselijk voor zowel enige fragmentverwijzingen, als multi-gebiedfragmentverwijzingen.
* De fragmenten die binnen het **Van meerdere lijnen tekst** worden van verwijzingen voorzien gegevenstype wanneer het gebruiken van **Rijke Tekst**.

Alle punten zijn ook van toepassing op fragmenten waarnaar binnen variaties wordt verwezen

Het volgende wordt niet in aanmerking genomen:

* De fragmenten die binnen de gegevenstypes van de inhoudsverwijzing van verwijzingen voorzien, zowel **Verwijzing van de Inhoud** (weg-gebaseerd) als **Verwijzing van de Inhoud (UUID)**.
* De fragmenten die binnen de **Verwijzing van het Fragment van verwijzingen worden voorzien (UUID)** gegevenstype.