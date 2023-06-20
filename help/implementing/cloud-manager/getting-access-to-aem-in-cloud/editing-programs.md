---
title: Programma's bewerken
description: Leer hoe u uw productie- en sandboxprogramma's kunt bewerken om de opties aan te passen nadat u deze hebt gemaakt.
exl-id: 819e4a6e-f77a-4594-a402-a300dcbdf510
source-git-commit: f7525b6b37e486a53791c2331dc6000e5248f8af
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 0%

---

# Programma&#39;s bewerken {#editing-programs}

Gebruikers met de vereiste machtigingen kunnen bewerken [productieprogramma&#39;s die in uw organisatie zijn gemaakt](creating-production-programs.md) alsmede [sandboxprogramma&#39;s die in uw organisatie zijn gemaakt.](creating-sandbox-programs.md) Door een programma te bewerken kunt u:

* Voeg de oplossing van Plaatsen aan een bestaand programma met Activa en vice versa toe.
* Sites of middelen verwijderen uit een bestaand programma met zowel Sites als Middelen.
* Voeg een tweede, ongebruikte oplossingsrecht aan of een bestaand programma of als nieuw Programma toe.
* Sandboxprogramma&#39;s verwijderen.

## Machtigingen {#permissions}

U moet lid zijn van de **Zakelijke eigenaar** rol voor het bewerken van programma&#39;s of het verwijderen van sandboxprogramma&#39;s.

## Een programma bewerken {#editing}

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
   * Dit tabblad is niet beschikbaar voor sandboxprogramma&#39;s.

1. Klikken op **Bijwerken** om uw wijzigingen in het programma op te slaan.

Elke keer dat een programma wordt bewerkt, inclusief het toevoegen of verwijderen van een oplossing of invoegtoepassing, worden deze wijzigingen van kracht na de volgende implementatie.

Als de uitgebreide beveiliging van uw productieprogramma is ingeschakeld, kunt u een extra **Uitgebreide beveiliging** tabblad is beschikbaar in het dialoogvenster **Programma bewerken** venster om te bevestigen dat de functie actief is voor het programma.

![Uitgebreide beveiliging actief voor een programma](assets/edit-program-enhanced.png)

Deze instelling kan niet worden gewijzigd nadat het programma is gemaakt. Voor meer informatie over de uitgebreide beveiligingsoptie raadpleegt u de [Productieprogramma&#39;s maken](creating-production-programs.md) document.

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
