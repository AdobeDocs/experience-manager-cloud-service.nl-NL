---
title: Lanceringen
description: Met behulp van opstartprogramma's kunt u op efficiënte wijze inhoud ontwikkelen voor een toekomstige release. Met deze sjablonen kunt u wijzigingen klaar maken voor toekomstige publicatie, terwijl uw huidige pagina's behouden blijven
translation-type: tm+mt
source-git-commit: 21f14d1f4e0ae26e097d4b31fe6811f1d089813d
workflow-type: tm+mt
source-wordcount: '907'
ht-degree: 5%

---


# Lanceringen {#launches}

Met behulp van opstartprogramma&#39;s kunt u op efficiënte wijze inhoud ontwikkelen voor een toekomstige release.

Er wordt een lancering gecreeerd zodat u veranderingen klaar voor toekomstige publicatie kunt maken (terwijl het handhaven van uw huidige pagina&#39;s). Nadat u de startpagina&#39;s hebt bewerkt en bijgewerkt, publiceert u deze weer naar de bron en activeert u vervolgens de bronpagina&#39;s (hoofdniveau). Als u de opstartinhoud verhoogt, wordt deze teruggezet naar de bronpagina&#39;s en kan dit handmatig of automatisch gebeuren (afhankelijk van de velden die zijn ingesteld bij het maken en bewerken van de opstart).

De seizoensgebonden productpagina&#39;s van uw online winkel worden bijvoorbeeld elk kwartaal bijgewerkt, zodat de aanbevolen producten op één lijn komen met het huidige seizoen. Als u de volgende driemaandelijkse update wilt voorbereiden, kunt u de juiste webpagina&#39;s starten. In het hele kwartaal worden de volgende wijzigingen in de opstartafbeelding opgebouwd:

* Wijzigingen in de bronpagina&#39;s die optreden als gevolg van normale onderhoudstaken. Deze wijzigingen worden automatisch gedupliceerd op de startpagina&#39;s.
* Bewerkingen die rechtstreeks worden uitgevoerd op de startpagina&#39;s ter voorbereiding op het volgende kwartaal.

U kunt ook:

* Navigeren door inhoud in de startvertakking; pagina&#39;s toevoegen of verwijderen, al naar gelang wat nodig is.
* Geef een voorvertoning weer van hoe gepubliceerde inhoud er in de toekomst uitziet naar een specifieke datum/tijd.

Wanneer het volgende kwartaal verschijnt, promoot u de startpagina&#39;s zodat u de bronpagina&#39;s kunt publiceren (met de bijgewerkte inhoud). U kunt alle pagina&#39;s of alleen de pagina&#39;s die u hebt gewijzigd, opwaarderen.

Launches kunnen ook:

* Gemaakt voor meerdere hoofdvertakkingen. Hoewel u de lancering voor de volledige plaats (en de veranderingen daar) kon tot stand brengen kan dit onpraktisch zijn aangezien de volledige plaats moet worden gekopieerd. Wanneer er honderden of zelfs duizenden pagina&#39;s bij betrokken zijn, worden de systeemvereisten en de prestaties beïnvloed door zowel de kopieeractie als later de vergelijkingen die vereist zijn voor de promotietaken.
* Genest (een lancering binnen een lancering) om u de capaciteit te geven om een lancering van een bestaande lancering tot stand te brengen zodat de auteurs van reeds aangebrachte veranderingen kunnen voordeel halen, eerder dan het moeten de zelfde veranderingen veelvoudige tijden voor elke lancering aanbrengen.

In deze sectie wordt beschreven hoe u startpagina&#39;s kunt maken, bewerken en promoten (en zo nodig [delete](/help/sites-cloud/authoring/launches/creating.md#deleting-a-launch)) vanuit de Sites-console of [de Launches-console](#the-launches-console):

* [Lanceringen maken](/help/sites-cloud/authoring/launches/creating.md)
* [Lanceringen bewerken](/help/sites-cloud/authoring/launches/editing.md)
* [Pagina&#39;s beheren in starten](/help/sites-cloud/authoring/launches/managing-pages.md)
* [Tijdverdraaiing gebruiken om een voorvertoning van uw inhoud weer te geven op basis van startpunten](/help/sites-cloud/authoring/launches/preview.md)
* [Lanceringen promoten](/help/sites-cloud/authoring/launches/promoting.md)

## Starten - de volgorde van gebeurtenissen {#launches-the-order-of-events}

Met behulp van opstartprogramma&#39;s kunt u op efficiënte wijze inhoud ontwikkelen voor een toekomstige release van een of meer geactiveerde webpagina&#39;s.

Met Launches kunt u:

* Een kopie van de bronpagina&#39;s maken:
   * De kopie is uw lancering.
   * De bronpagina&#39;s op het hoogste niveau worden **Productie** genoemd.
      * De bronpagina&#39;s kunnen uit meerdere (afzonderlijke) vertakkingen worden genomen.

   ![Volgorde van de lanceringen](/help/sites-cloud/authoring/assets/launches-order.png)

* De startconfiguratie bewerken:
   * Pagina&#39;s en/of vertakkingen toevoegen aan of verwijderen uit het opstarten.
   * Bewerk starteigenschappen, zoals markeringen voor **Titel**, **Startdatum**, **Geschikt voor productie**.
* U kunt de inhoud handmatig of automatisch publiceren:
   * Handmatig:
      * Bevestig uw lanceringsinhoud terug naar **Doel** (bronpagina&#39;s) wanneer het klaar is om te worden gepubliceerd.
      * Publiceer de inhoud van de bronpagina&#39;s (na het promoten van de achterpagina&#39;s).
      * Alle pagina&#39;s of alleen gewijzigde pagina&#39;s promoten.
   * Automatisch - dit omvat het volgende:
      * Het **Launch**(**Live**) **date** veld: dit kan worden ingesteld wanneer u een opstart maakt of bewerkt.
      * De markering **Production Ready**: dit kan alleen worden ingesteld wanneer u een opstart bewerkt.
      * Als de markering **Production Ready** is ingesteld, wordt de lancering automatisch bevorderd tot de productiepagina&#39;s op de opgegeven **Launch**(**Live**) **date**. Na de promotie worden de productiepagina’s automatisch gepubliceerd.\
         Als er geen datum is ingesteld, heeft de markering geen effect.
* Werk de bron- en startpagina&#39;s parallel bij:
   * Wijzigingen in de bronpagina&#39;s worden automatisch geïmplementeerd in de opstartafbeelding (als deze zijn ingesteld op basis van overerving); d.w.z. als een live kopie).
   * U kunt wijzigingen aanbrengen in de opstartafbeelding zonder deze automatische updates of de bronpagina&#39;s te onderbreken.

   ![Parallel uitgevoerde acties](/help/sites-cloud/authoring/assets/launches-parallel.png)

* [Een geneste opstart](/help/sites-cloud/authoring/launches/creating.md#creating-a-nested-launch)  maken - een opstart binnen een opstart:
   * De bron is een bestaande opstart.
   * U kunt een geneste opstart [promoten](/help/sites-cloud/authoring/launches/promoting.md#promoting-a-nested-launch) naar elk doel; Dit kan een bovenliggende opstart of de bronpagina&#39;s op het hoogste niveau (Productie) zijn.

   ![Een geneste start](/help/sites-cloud/authoring/assets/launches-nested.png)

   >[!CAUTION]
   >
   >Als u een opstart verwijdert, wordt de opstart zelf en alle afstammende geneste opstarties verwijderd.

>[!NOTE]
>
>Voor het maken en bewerken van startpagina&#39;s zijn toegangsrechten vereist voor `/content/launches` - zoals bij de standaardgroep `content-authors`.
>
>Neem contact op met de systeembeheerder als u problemen ondervindt.

## Start in References (Sites Console) {#launches-in-references-sites-console}

1. Navigeer in de **Sites**-console naar de bron van de opstart(en).
1. Open **References** rail en selecteer de bronpagina.
1. Selecteer **Launches**, de bestaande lancering(en) zullen worden vermeld, samen met toegang tot **Console** van Lanceringen:

   ![Referenties van lanceringen in plaatsenconsole](/help/sites-cloud/authoring/assets/launches-references.png)

1. Tik/klik op de gewenste opstart. De lijst met mogelijke acties wordt weergegeven:

   ![Handelingen om lanceringen in plaatsenconsole over te nemen](/help/sites-cloud/authoring/assets/launches-references-actions.png)

## De opstartconsole {#the-launches-console}

De console van Lanceringen verstrekt een overzicht van uw lanceringen en staat u toe om acties op die vermelde te voeren. De console is toegankelijk via:

* De console **Tools**: **Gereedschappen**, **Sites**, **Launches**.

* **Start** Consoleat onder aan  **** Starten van de  **** Referencesrail bij navigeren naar broninhoud in de Sites-console.

   ![Start Console in References of launds in Sites-console](/help/sites-cloud/authoring/assets/launches-references.png)

* De **Launches**-knop rechtsboven wanneer u in de Sites-console navigeert naar de opstartinhoud:

   ![Optie Starten in Sites-console](/help/sites-cloud/authoring/assets/launches-console-navigate-launch-content.png)

* of rechtstreeks; bijvoorbeeld met:
   `https://<host>:<port>/libs/launches/content/launches.html`
