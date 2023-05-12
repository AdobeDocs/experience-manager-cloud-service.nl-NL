---
title: Sandbox-programma's maken
description: Leer hoe u Cloud Manager gebruikt om uw eigen sandboxprogramma te maken voor training, demo, POC of andere niet-productiedoeleinden.
exl-id: 10011392-3059-4bb0-88db-0af1d390742e
source-git-commit: b916bf5b252045120659600293e004fc34b96e7a
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---

# Sandbox-programma&#39;s maken {#create-sandbox-program}

Een zandbakprogramma wordt typisch gecreeerd om ten behoeve van opleiding, lopende demo&#39;s, enablement, POCs, of documentatie te dienen en is niet bedoeld om levend verkeer te vervoeren.

Meer informatie over programmatypen in het document [Het begrip van Programma en de Types van Programma.](program-types.md)

## Een Sandbox-programma maken {#create}

Ga als volgt te werk om een sandboxprogramma te maken.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie.

1. Klik op de landingspagina van Cloud Manager op **Programma toevoegen** in de rechterbovenhoek van het scherm.

   ![Openingspagina van Cloud Manager](assets/cloud-manager-my-programs.png)

1. Selecteer in de wizard Programma maken de optie **Een sandbox instellen** en geef een programmanaam op.

   ![Programma-type maken](assets/create-sandbox.png)

1. U kunt desgewenst een afbeelding aan het programma toevoegen door een afbeeldingsbestand naar het **Een programmaafbeelding toevoegen** Selecteer een afbeelding in een bestandenbrowser of klik erop. Tik of klik op **Doorgaan**.

   * De afbeelding fungeert alleen als de tegel in het venster met het programmaoverzicht en helpt het programma te identificeren.

1. In de **Sandbox instellen** kiest u welke oplossingen u wilt inschakelen in uw sandboxprogramma door de opties in het dialoogvenster **Oplossingen en invoegtoepassingen** tabel.

   * Gebruik de chevrons naast de oplossingsnamen om extra, facultatieve toe:voegen-ons voor de oplossingen te tonen.

   * De **Sites** en **Activa** -oplossingen worden altijd opgenomen in sandboxprogramma&#39;s en kunnen niet worden uitgeschakeld.

   ![Oplossingen en invoegtoepassingen selecteren voor een sandbox](assets/sandbox-solutions-add-ons.png)

1. Tik op **Maken**.

Naarmate het installatieproces vordert, wordt op de bestemmingspagina een nieuwe sandbox-programmakaart met een statusindicator weergegeven.

![Sandbox-ontwerp van overzichtspagina](assets/sandbox-setup.png)

## Toegang tot sandbox {#access}

U kunt de details van de configuratie van uw sandbox bekijken en de omgeving openen (zodra deze beschikbaar is) door de overzichtspagina van het programma te bekijken.

1. Klik op de landingspagina van Cloud Manager op de knop voor weglatingen in het zojuist gemaakte programma.

   ![Overzicht van programma openen](assets/program-overview-sandbox.png)

1. Nadat de stap voor het maken van het project is voltooid, hebt u toegang tot de **Repo-info openen** om uw git-repo te kunnen gebruiken.

   ![Programmaconfiguratie](assets/create-program4.png)

   >[!TIP]
   >
   >Raadpleeg het document voor meer informatie over het openen en beheren van de git-opslagplaats [Toegang tot Git.](/help/implementing/cloud-manager/managing-code/accessing-repos.md)

1. Als de ontwikkelomgeving eenmaal is gemaakt, kunt u de **AEM** koppeling om u aan te melden bij AEM.

   ![Toegang AEM koppeling](assets/create-program-5.png)

1. Zodra de niet-productiepijplijn die aan ontwikkeling opstelt volledig is, leidt de tovenaar u om of tot de AEM ontwikkelomgeving toegang te hebben of code aan ontwikkelomgeving op te stellen.

   ![Sandbox implementeren](assets/create-program-setup-deploy.png)

Als u op een bepaald moment naar een ander programma moet schakelen of naar de overzichtspagina moet terugkeren om een ander programma te maken, klikt u op de naam van het programma linksboven in het scherm om het **Navigeren naar** optie.

![Ga naar](assets/create-program-a1.png)
