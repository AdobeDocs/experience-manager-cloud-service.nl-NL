---
title: Programma's bewerken
description: Leer hoe u uw productie- en sandboxprogramma's kunt bewerken om de opties aan te passen nadat u deze hebt gemaakt.
exl-id: 819e4a6e-f77a-4594-a402-a300dcbdf510
source-git-commit: ecb168e9261b3e3ed89e4cbe430b3da9f777a795
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 0%

---

# Programma&#39;s bewerken {#editing-programs}

Gebruikers met de vereiste machtigingen kunnen bewerkingen uitvoeren [productieprogramma&#39;s die in uw organisatie zijn gemaakt](creating-production-programs.md) en [sandboxprogramma&#39;s die in uw organisatie zijn gemaakt.](creating-sandbox-programs.md) Door een programma te bewerken kunt u:

* Voeg de oplossing van Plaatsen aan een bestaand programma met Activa toe en omgekeerd.
* Sites of middelen verwijderen uit een bestaand programma met zowel sites als middelen.
* Voeg een tweede, ongebruikte oplossingsrecht, aan of een bestaand programma of als nieuw Programma toe.
* Sandboxprogramma&#39;s verwijderen.

## Machtigingen {#permissions}

U moet lid zijn van de **Zakelijke eigenaar** rol om programma&#39;s te bewerken of sandboxprogramma&#39;s te verwijderen.

## Een programma bewerken {#editing}

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie.

1. Klik op het programma dat u wilt bewerken om de details weer te geven.

1. Klik op de naam van het programma linksboven op de pagina en selecteer **Programma bewerken**.

   ![Programma bewerken, optie](assets/edit-program-overview.png)

1. De **Programma bewerken** pagina wordt geopend. Op de **Algemeen** de naam en beschrijving van het programma bewerken.

   * Voor een programma moet ten minste één oplossing worden gekozen.

   ![Tabblad Algemeen](assets/edit-program-prod1.png)

1. Op de **Oplossingen en invoegtoepassingen** wijzigt u de oplossingen voor het programma.

   ![Oplossingen selecteren](assets/edit-prg.png)

1. Klik op het chevron voor de naam van de oplossing om optionele invoegtoepassingen weer te geven, zoals het selecteren van de **Handel** invoegoptie onder **Sites**.

   ![Invoegtoepassingen bewerken](assets/edit-program-add-on.png)

1. Op de **Live-instellingen** wijzigen, wijzigt u de geplande datum voor de introductie van het programma.

   ![Instellingen voor go-live bewerken](assets/edit-program-go-live.png)

   * Deze datum is uitsluitend ter informatie. De widget Go Live wordt geactiveerd op de pagina met het programmaoverzicht. Het biedt op zijn beurt in-product koppelingen naar de as a Cloud Service documentatie over beste praktijken van Adobe Experience Manager (AEM), die op uw reis is afgestemd. Dit culmineert in een geslaagde Go Live-ervaring.
   * Dit tabblad is niet beschikbaar voor sandboxprogramma&#39;s.

1. Indien de vereiste rechten voor het programma beschikbaar zijn, **Beveiliging** wordt weergegeven waar u de beveiligingsopties voor het programma kunt wijzigen.

   ![Beveiligingsinstellingen bewerken](assets/edit-program-security.png)

   * HIPAA kan niet worden ingeschakeld of uitgeschakeld na [programma&#39;s maken.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md)
      * [Meer informatie](https://www.adobe.com/go/hipaa-ready) over de HIPAA-gereed implementatie van de oplossing van Adobe.
   * Zodra geactiveerd, kan de bescherming WAF-DDOS dan door opstelling worden gevormd [niet-productiepijpleiding.](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md)

   {{waf-limited-release}}

1. Klikken **Bijwerken** om uw wijzigingen in het programma op te slaan.

Telkens wanneer een programma wordt uitgegeven, met inbegrip van het toevoegen van of het verwijderen van een oplossing of toe:voegen-op, worden die veranderingen van kracht na de volgende plaatsing.

## Sandbox-programma&#39;s verwijderen {#delete-sandbox-program}

Als u een sandboxprogramma verwijdert, worden alle bijbehorende omgevingen en pijpleidingen verwijderd.

>[!TIP]
>
>Gebruikers met de **Zakelijke eigenaar** of **Implementatiebeheer** rollen kunnen hun productie en werkgebiedmilieu&#39;s in plaats van het volledige zandbakprogramma Alternatief schrappen.

Ga als volgt te werk om een sandboxprogramma te verwijderen.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie.

1. Klik op het programma dat u wilt bewerken om de details weer te geven.

1. Klik op de naam van het programma linksboven op de pagina en selecteer **Programma verwijderen**.

   ![Programma verwijderen, optie](assets/delete-sandbox1.png)

U kunt ook op de knop Ovaal op de kaart van uw programma klikken op de overzichtspagina van Cloud Manager en **Programma verwijderen**.

![Sandbox verwijderen van programmakaart](assets/delete-sandbox2.png)

>[!NOTE]
>
>Alleen sandboxprogramma&#39;s kunnen worden verwijderd. Productieprogramma&#39;s kunnen niet worden verwijderd.
