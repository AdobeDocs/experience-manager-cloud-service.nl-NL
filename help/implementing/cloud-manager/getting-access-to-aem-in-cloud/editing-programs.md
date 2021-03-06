---
title: Programma's bewerken
description: Leer hoe u uw productie- en sandboxprogramma's kunt bewerken om de opties aan te passen nadat u deze hebt gemaakt.
exl-id: 819e4a6e-f77a-4594-a402-a300dcbdf510
source-git-commit: d805ed744af0e5c95863a1c67439b384cc5d11b2
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# Programma&#39;s bewerken {#editing-programs}

Gebruikers met de vereiste machtigingen kunnen bewerken [productieprogramma&#39;s die in uw organisatie zijn gemaakt](creating-production-programs.md) alsmede [sandboxprogramma&#39;s die in uw organisatie zijn gemaakt.](creating-sandbox-programs.md) Door een programma te bewerken kunt u:

* Voeg de oplossing van Plaatsen aan een bestaand programma met Activa en vice versa toe.
* Sites of middelen verwijderen uit een bestaand programma met zowel Sites als Middelen.
* Voeg een tweede, ongebruikte oplossingsrecht aan of een bestaand programma of als nieuw Programma toe.
* Sandboxprogramma&#39;s verwijderen.

>[!NOTE]
>
>U moet lid zijn van de **Zakelijke eigenaar** rol voor het bewerken van programma&#39;s of het verwijderen van sandboxprogramma&#39;s.

Voer de volgende stappen uit om een programma te bewerken.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie.

1. Klik op het programma dat u wilt bewerken om de details weer te geven.

1. Klik op de naam van uw programma linksboven op de pagina en selecteer **Programma bewerken**.

   ![Programma bewerken, optie](assets/edit-program-overview.png)

1. De **Programma bewerken** pagina wordt geopend. Op de **Algemeen** bewerken.

   * Voor een programma moet ten minste één oplossing worden gekozen.

   ![Tabblad Algemeen](assets/edit-program-prod1.png)

1. Op de **Oplossingen en invoegtoepassingen** wijzigt u de oplossingen voor het programma.

   ![Oplossingen selecteren](assets/edit-prg.png)

1. Klik op het chevron vóór de namen van de oplossingen om optionele invoegtoepassingen te tonen, zoals het selecteren van de **Handel** invoegoptie onder **Sites**.

   ![Invoegtoepassingen bewerken](assets/edit-program-add-on.png)

1. Op de **Live-instellingen** wijzigen, wijzigt u de geplande datum voor de introductie van het programma.

   ![Instellingen voor go-live bewerken](assets/edit-program-go-live.png)

   * Deze datum is alleen bedoeld voor informatief gebruik en activeert de widget Go Live op de overzichtspagina van het programma om op tijd koppelingen naar AEM as a Cloud Service documentatie over best practices te bieden, zodat deze op de juiste manier kunnen worden afgestemd op uw reis en een geslaagde en vloeiende Go Live-ervaring tot resultaat hebben.

1. Klikken op **Bijwerken** om uw wijzigingen in het programma op te slaan.

Elke keer dat een programma wordt bewerkt, inclusief het toevoegen of verwijderen van een oplossing of invoegtoepassing, worden deze wijzigingen van kracht na de volgende implementatie.

## Sandbox-programma&#39;s verwijderen {#delete-sandbox-program}

Als u een sandboxprogramma verwijdert, worden alle bijbehorende omgevingen en pijpleidingen verwijderd.

>[!TIP]
>
>Gebruikers met de **Zakelijke eigenaar** of **Implementatiebeheer** rollen kunnen hun productie en werkgebiedmilieu&#39;s in plaats van het volledige zandbakprogramma Alternatief schrappen.

Ga als volgt te werk om een sandboxprogramma te verwijderen.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie.

1. Klik op het programma dat u wilt bewerken om de details weer te geven.

1. Klik op de naam van uw programma linksboven op de pagina en selecteer **Programma verwijderen**.

   ![Programma verwijderen, optie](assets/delete-sandbox1.png)

U kunt ook op de knop Ovaal op de kaart van uw programma klikken op de overzichtspagina van Cloud Manager en **Programma verwijderen**.

![Sandbox verwijderen van programmakaart](assets/delete-sandbox2.png)

>[!NOTE]
>
>Alleen sandboxprogramma&#39;s kunnen worden verwijderd. Productieprogramma&#39;s kunnen niet worden geschrapt.
