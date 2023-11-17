---
title: Sandbox-programma's maken
description: Leer hoe u Cloud Manager gebruikt om uw eigen sandboxprogramma te maken voor training, demo, POC of andere niet-productiedoeleinden.
exl-id: 10011392-3059-4bb0-88db-0af1d390742e
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# Sandbox-programma&#39;s maken {#create-sandbox-program}

Een zandbakprogramma wordt typisch gecreeerd om ten behoeve van opleiding, lopende demo&#39;s, enablement, POCs, of documentatie te dienen en is niet bedoeld om levend verkeer te vervoeren.

Meer informatie over programmatypen in het document [Het begrip van Programma en Programma Types.](program-types.md)

## Een Sandbox-programma maken {#create}

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie.

1. Klik in de openingspagina van Cloud Manager rechtsboven in het scherm op **Programma toevoegen**.

   ![Openingspagina van Cloud Manager](assets/cloud-manager-my-programs.png)

1. Selecteer in de wizard Programma maken de optie **Een sandbox instellen** en geef een programmanaam op.

   ![Programma-type maken](assets/create-sandbox.png)

1. U kunt desgewenst een afbeelding aan het programma toevoegen door een afbeeldingsbestand naar het **Een programmaafbeelding toevoegen** Selecteer een afbeelding in een bestandenbrowser of klik erop. Selecteren **Doorgaan**.

   * De afbeelding fungeert alleen als de tegel in het venster met het programmaoverzicht en helpt het programma te identificeren.

1. In de **Sandbox instellen** kiest u welke oplossingen u wilt inschakelen in uw sandboxprogramma door de opties in het dialoogvenster **Oplossingen en invoegtoepassingen** tabel.

   * Gebruik de chevrons naast de oplossingsnamen zodat kunt u extra, facultatieve toe:voegen-ons voor de oplossingen zien.

   * De **Sites** en **Activa** -oplossingen worden altijd opgenomen in sandboxprogramma&#39;s en kunnen niet worden uitgeschakeld.

   ![Oplossingen en invoegtoepassingen selecteren voor een sandbox](assets/sandbox-solutions-add-ons.png)

1. Als u de oplossingen en invoegtoepassingen voor uw sandboxprogramma hebt geselecteerd, klikt u op **Maken**.

U ziet een nieuwe zandbakprogrammakaart op de landingspagina met een statusindicator aangezien het opstellingsproces vordert.

![Sandbox-ontwerp van overzichtspagina](assets/sandbox-setup.png)

## Toegang tot sandbox {#access}

U kunt de details van uw zandbakopstelling bekijken en tot het milieu (zodra beschikbaar) toegang hebben door de pagina van het programmaoverzicht te bekijken.

1. Klik op de landingspagina van Cloud Manager op de knop voor weglatingen in het zojuist gemaakte programma.

   ![Overzicht van programma openen](assets/program-overview-sandbox.png)

1. Nadat de stap voor het maken van het project is voltooid, hebt u toegang tot de **Repo-info openen** om uw git-repo te kunnen gebruiken.

   ![Programmaconfiguratie](assets/create-program4.png)

   >[!TIP]
   >
   >Ga voor meer informatie over toegang tot en beheer van uw it-opslagplaats naar [Toegang tot it](/help/implementing/cloud-manager/managing-code/accessing-repos.md).

1. Als de ontwikkelomgeving eenmaal is gemaakt, kunt u de **AEM** koppeling om u aan te melden AEM.

   ![Toegang AEM koppeling](assets/create-program-5.png)

1. Zodra de niet-productiepijplijn die aan ontwikkeling opstelt volledig is, leidt de tovenaar u om of tot de AEM ontwikkelomgeving toegang te hebben of code aan ontwikkelomgeving op te stellen.

   ![Sandbox implementeren](assets/create-program-setup-deploy.png)

Als u naar een ander programma moet overschakelen of naar de overzichtspagina moet terugkeren om een ander programma te maken, klikt u op de naam van het programma linksboven in het scherm om de **Navigeren naar** -optie.

![Ga naar](assets/create-program-a1.png)
