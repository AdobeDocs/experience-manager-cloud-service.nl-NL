---
title: Starten voor pagina's
description: Leer hoe u Launches voor pagina's in Adobe Experience Manager as a Cloud Service gebruikt. Met behulp van Starten kunt u op efficiënte wijze inhoud ontwikkelen voor een toekomstige release, terwijl uw huidige pagina's behouden blijven.
exl-id: 3e410120-d08f-4d05-932f-07bc4440af2b
solution: Experience Manager Sites
feature: Authoring, Launches
role: User
source-git-commit: 20ad1d468ac0d8ec3933477f954120debe4e9240
workflow-type: tm+mt
source-wordcount: '1027'
ht-degree: 3%

---

# Starten voor pagina&#39;s {#launches-for-pages}

Met Launches kunt u in Adobe Experience Manager (AEM) as a Cloud Service op efficiënte wijze inhoud ontwikkelen voor een toekomstige release.

A *Lancering* wordt gecreeerd om u toe te staan om veranderingen in voorbereiding op toekomstige publicatie aan te brengen, tezelfdertijd als het handhaven van uw huidige inhoud. Voor AEM-pagina&#39;s betekent dit dat u in feite twee versies tegelijk bewerkt: pagina&#39;s die momenteel worden gepubliceerd en een versie van deze pagina&#39;s die in de toekomst tegelijk worden gepubliceerd. Zodra dat tijdstip is bereikt, kunt u de originele pagina&#39;s vervangen en de nieuwe versies publiceren.

>[!NOTE]
>
>Launches zijn ook beschikbaar voor Content Fragments. De basisbegrippen zijn hetzelfde, maar er zijn verschillen in de manier waarop ze in AEM moeten worden beheerd.
>
>Voor volledige details zie [&#x200B; Lanceringen voor de Fragmenten van de Inhoud &#x200B;](/help/sites-cloud/administering/content-fragments/launches-for-content-fragments.md).

U creeert a *Lancering*, dan na het uitgeven en het bijwerken van uw *3&rbrace; pagina&#39;s van de Lancering &lbrace;u* bevordert *hen terug naar* Source *.* U kunt deze *Source* pagina&#39;s (top-level) dan activeren. Als u de opstartinhoud verhoogt, wordt deze teruggezet naar de bronpagina&#39;s en kan dit handmatig of automatisch gebeuren (afhankelijk van de velden die zijn ingesteld bij het maken en bewerken van de opstart).

De seizoensgebonden productpagina&#39;s van uw online winkel worden bijvoorbeeld elk kwartaal bijgewerkt, zodat de aanbevolen producten op één lijn komen met het huidige seizoen. Als u de volgende driemaandelijkse update wilt voorbereiden, kunt u de juiste webpagina&#39;s starten. In het hele kwartaal worden de volgende wijzigingen in de opstartafbeelding opgebouwd:

* Wijzigingen in de bronpagina&#39;s die optreden als gevolg van normale onderhoudstaken. Deze wijzigingen worden automatisch gedupliceerd op de startpagina&#39;s.
* Bewerkingen die rechtstreeks worden uitgevoerd op de startpagina&#39;s ter voorbereiding op het volgende kwartaal.

U kunt ook:

* Navigeren door inhoud in de startvertakking; zo nodig pagina&#39;s toevoegen of verwijderen.
* Geef een voorvertoning weer van hoe gepubliceerde inhoud er in de toekomst uitziet op een bepaalde datum.

Wanneer het volgende kwartaal verschijnt, promoot u de startpagina&#39;s zodat u de bronpagina&#39;s kunt publiceren (met de bijgewerkte inhoud). U kunt alle pagina&#39;s of alleen de pagina&#39;s die u hebt gewijzigd, opwaarderen.

Launches kunnen ook:

* Gemaakt voor meerdere hoofdvertakkingen. Hoewel u de lancering voor de volledige plaats (en de veranderingen daar) kon tot stand brengen kan dit onpraktisch zijn aangezien de volledige plaats moet worden gekopieerd. Wanneer er honderden of zelfs duizenden pagina&#39;s bij betrokken zijn, worden de systeemvereisten en de prestaties beïnvloed door zowel de kopieeractie als later de vergelijkingen die vereist zijn voor de promotietaken.
* Genest (een lancering binnen een lancering) om u de capaciteit te geven om een lancering van een bestaande lancering tot stand te brengen zodat de auteurs van reeds aangebrachte veranderingen kunnen voordeel halen, eerder dan het moeten de zelfde veranderingen veelvoudige tijden voor elke lancering aanbrengen.

Deze sectie beschrijft om te creëren, uit te geven en te bevorderen (en indien nodig [&#x200B; schrapt &#x200B;](/help/sites-cloud/authoring/launches/creating.md#deleting-a-launch)) lanceringspagina&#39;s van binnen de console van Plaatsen of [&#x200B; de console van Lanceringen &#x200B;](#the-launches-console):

* [Starten maken](/help/sites-cloud/authoring/launches/creating.md)
* [Starten bewerken](/help/sites-cloud/authoring/launches/editing.md)
* [Pagina&#39;s beheren in starten](/help/sites-cloud/authoring/launches/managing-pages.md)
* [Tijdverdraaiing gebruiken om een voorvertoning van uw inhoud weer te geven op basis van startpunten](/help/sites-cloud/authoring/launches/preview.md)
* [Starten promoten](/help/sites-cloud/authoring/launches/promoting.md)

## Starten - de volgorde van gebeurtenissen {#launches-the-order-of-events}

Met behulp van opstartprogramma&#39;s kunt u op efficiënte wijze inhoud ontwikkelen voor een toekomstige release van een of meer geactiveerde webpagina&#39;s.

Met Launches kunt u:

* Een kopie van de bronpagina&#39;s maken:
   * De kopie is uw lancering.
   * De bronpagina&#39;s op het hoogste niveau worden **Productie** genoemd.
      * De bronpagina&#39;s kunnen uit meerdere (afzonderlijke) vertakkingen worden genomen.

  ![&#x200B; Orde van verrichting van lanceringen &#x200B;](/help/sites-cloud/authoring/assets/launches-order.png)

* De startconfiguratie bewerken:
   * Pagina&#39;s en/of vertakkingen toevoegen aan of verwijderen uit het opstarten.
   * Bewerk starteigenschappen, zoals markeringen voor **Titel**, **Startdatum**, **Geschikt voor productie**.
* U kunt de inhoud handmatig of automatisch publiceren:
   * Handmatig:
      * Bevestig uw lanceringsinhoud terug naar het **Doel** (bronpagina&#39;s) wanneer het klaar is om te worden gepubliceerd.
      * Publiceer de inhoud van de bronpagina&#39;s (na het promoten van de achterpagina&#39;s).
      * Alle pagina&#39;s of alleen gewijzigde pagina&#39;s promoten.
   * Automatisch - dit omvat het volgende:
      * Het **Lanceergebied** (**Levende**) **datum**: dit kan worden geplaatst wanneer het creëren van of het uitgeven van een lancering.
      * De **Klaar vlag van de Productie**: dit kan slechts worden geplaatst wanneer het uitgeven van een lancering.
      * Als de **Klaar van de Productie** vlag wordt geplaatst, wordt de lancering automatisch bevorderd tot de productiepagina&#39;s op de gespecificeerde **Lanceer** (**Levende**) **datum**. Na de promotie worden de productiepagina&#39;s automatisch gepubliceerd.\
        Als er geen datum is ingesteld, heeft de markering geen effect.
* Werk de bron- en startpagina&#39;s parallel bij:
   * Wijzigingen in de bronpagina&#39;s worden automatisch geïmplementeerd in de opstartafbeelding (als deze worden ingesteld op basis van overerving, dat wil zeggen als een live kopie).
   * U kunt wijzigingen aanbrengen in de opstartafbeelding zonder deze automatische updates of de bronpagina&#39;s te onderbreken.

  ![&#x200B; Acties parallel &#x200B;](/help/sites-cloud/authoring/assets/launches-parallel.png)

* [&#x200B; creeer een genestelde lancering &#x200B;](/help/sites-cloud/authoring/launches/creating.md#creating-a-nested-launch) - een lancering binnen een lancering:
   * De bron is een bestaande opstart.
   * U kunt [&#x200B; een genestelde lancering &#x200B;](/help/sites-cloud/authoring/launches/promoting.md#promoting-a-nested-launch) aan om het even welk doel bevorderen; dit kan een ouderlancering of de top-level bronpagina&#39;s (Productie) zijn.

  ![&#x200B; Een genestelde lancering &#x200B;](/help/sites-cloud/authoring/assets/launches-nested.png)

  >[!CAUTION]
  >
  >Als u een opstart verwijdert, wordt de opstart zelf en alle afstammende geneste opstarties verwijderd.

>[!NOTE]
>
>Voor het maken en bewerken van startpagina&#39;s zijn toegangsrechten vereist voor `/content/launches` , net als voor de standaardgroep `content-authors` .
>
>Neem contact op met de systeembeheerder als u problemen ondervindt.

## Starten in verwijzingen (siteconsole) {#launches-in-references-sites-console}

1. In de **console van Plaatsen**, navigeer aan de bron van lancering(en).
1. Open het **spoor van Verwijzingen** en selecteer de bronpagina.
1. Selecteer **Lanceringen**, zijn de bestaande lanceringen vermeld, samen met toegang tot de **Console van Lanceringen**:

   ![&#x200B; Verwijzingen van lanceringen in plaatsenconsole &#x200B;](/help/sites-cloud/authoring/assets/launches-references.png)

1. Selecteer de juiste start en de lijst met mogelijke acties wordt weergegeven:

   ![&#x200B; Acties om lanceringen in plaatsenconsole &#x200B;](/help/sites-cloud/authoring/assets/launches-references-actions.png) over te nemen

## De opstartconsole {#the-launches-console}

>[!NOTE]
>
>Deze console is alleen voor Launches voor Pagina&#39;s.
>
>Om uw Fragmenten van de Inhoud te beheren zie [&#x200B; Lanceringen voor de Fragmenten van de Inhoud &#x200B;](/help/sites-cloud/administering/content-fragments/launches-for-content-fragments.md).

De console van Lanceringen verstrekt een overzicht van uw lanceringen en laat u op die vermelde handelen.

![&#x200B; Console van de Lancering - beheer Inhoud &#x200B;](/help/sites-cloud/authoring/assets/launches-navigate-launches-console.png)

De console is toegankelijk via:

* De **Console van Hulpmiddelen**: **Hulpmiddelen**, **Algemeen**, **Lanceringen**.

* **Console van Lanceringen** bij de bodem van de **sectie van Lanceringen** van de **Verwijzingen** spoor wanneer het navigeren van broninhoud in de console van Plaatsen.

  ![&#x200B; Console van Lanceringen in Verwijzingen van lanceringen in de console van Plaatsen &#x200B;](/help/sites-cloud/authoring/assets/launches-references.png)

* De **Starten** knoop bij het hoogste recht, wanneer het navigeren van lanceringsinhoud in de console van Plaatsen:

  ![&#x200B; optie van Lanceringen in de console van Plaatsen &#x200B;](/help/sites-cloud/authoring/assets/launches-console-navigate-launch-content.png)
