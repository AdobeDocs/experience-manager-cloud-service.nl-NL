---
title: Een pagina ontwerpen voor mobiele apparaten
description: Wanneer het ontwerpen voor mobiel, kunt u tussen verscheidene mededingers schakelen om te zien wat de eindgebruiker ziet
translation-type: tm+mt
source-git-commit: dbd7b8084445b03beff3b5a96b0fa6b5512e10b8
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%

---


# Een pagina ontwerpen voor mobiele apparaten {#authoring-a-page-for-mobile-devices}

De pagina&#39;s van Adobe Experience Manager zijn gebaseerd op een responsieve lay-out. De responsieve lay-out past uw inhoud automatisch aan aan het doelapparaat, waardoor het niet nodig is om inhoud voor specifieke apparaten te ontwerpen.

Wanneer u een mobiele pagina ontwerpt, wordt de pagina weergegeven op een manier die het mobiele apparaat emuleert. Wanneer u de pagina ontwerpt, kunt u schakelen tussen verschillende emulators om te zien wat de eindgebruiker ziet wanneer hij of zij de pagina opent.

Apparaten worden gegroepeerd in de categoriefunctie, de functie voor slim afdrukken en de functie voor aanraken op basis van de mogelijkheden van de apparaten om een pagina weer te geven. Wanneer de eindgebruiker tot een mobiele pagina toegang heeft, ontdekt AEM het apparaat en verzendt de vertegenwoordiging die aan zijn apparatengroep beantwoordt.

>[!NOTE]
>
>Als u een mobiele site wilt maken op basis van een bestaande standaardsite, maakt u een live kopie van de standaardsite. Zie Een actieve kopie maken voor verschillende kanalen.
>
>AEM-ontwikkelaars kunnen nieuwe apparaatgroepen maken. Zie Apparaatgroepfilters maken.

<!--
>To create a mobile site based on an existing standard site, create a live copy of the standard site. (See [Creating a Live Copy for Different Channels](/help/sites-administering/msm-livecopy.md).)
>
>AEM developers can create new device groups. (See [Creating Device Group Filters](/help/sites-developing/groupfilters.md).)
-->

Gebruik de volgende procedure om een mobiele pagina te ontwerpen:

1. Open vanuit globale navigatie de **Sites** -console.
1. Bewerk een inhoudspagina.
1. Ga naar de gewenste emulator door op het pictogram **Emulator** boven aan de pagina te klikken.

   ![Emulatorpictogram](/help/sites-cloud/authoring/assets/emulator.png)

1. Sleep componenten van de componentbrowser of de middelenbrowser naar de pagina.
1. [Wijzig de responsieve lay-out](/help/sites-cloud/authoring/features/responsive-layout.md) van de pagina en de componenten ervan op basis van het geselecteerde apparaat.

De pagina ziet er ongeveer als volgt uit:

![Voorbeeld van mobiel](/help/sites-cloud/authoring/assets/mobile.png)

>[!NOTE]
>
>De emulators worden uitgeschakeld wanneer een pagina op de auteurinstantie wordt opgevraagd bij een mobiel apparaat.
