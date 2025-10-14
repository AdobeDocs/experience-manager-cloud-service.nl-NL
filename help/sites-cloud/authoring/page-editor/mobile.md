---
title: Een pagina ontwerpen voor mobiele apparaten
description: Wanneer het ontwerpen voor mobiel, kunt u tussen verscheidene mededingers schakelen om te zien wat de eindgebruiker ziet
exl-id: fabd4468-3304-402f-9522-342da3bbae94
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---

# Een pagina ontwerpen voor mobiele apparaten {#authoring-a-page-for-mobile-devices}

Adobe Experience Manager-pagina&#39;s zijn gebaseerd op een responsieve indeling. [&#x200B; Responsieve lay-out &#x200B;](/help/sites-cloud/authoring/page-editor/responsive-layout.md) past uw inhoud aan om het doelapparaat automatisch te passen, eliminerend de behoefte aan auteursinhoud voor specifieke apparaten.

Wanneer u een mobiele pagina ontwerpt, wordt de pagina weergegeven op een manier die het mobiele apparaat emuleert. Wanneer u de pagina ontwerpt, kunt u schakelen tussen verschillende emulators om te zien wat de eindgebruiker ziet wanneer hij of zij de pagina opent.

Apparaten worden gegroepeerd in de categoriefunctie, de functie voor slim afdrukken en de functie voor aanraken op basis van de mogelijkheden van de apparaten om een pagina weer te geven. Wanneer de eindgebruiker tot een mobiele pagina toegang heeft, AEM ontdekt het apparaat en verzendt de vertegenwoordiging die aan zijn apparatengroep beantwoordt.

>[!NOTE]
>
>Als u een mobiele site wilt maken op basis van een bestaande standaardsite, maakt u een live kopie van de standaardsite. Zie [&#x200B; Creërend Levende Kopieën &#x200B;](/help/sites-cloud/administering/msm/creating-live-copies.md).
>
>AEM ontwikkelaars kunnen nieuwe apparaatgroepen maken. Zie Apparaatgroepfilters maken.

<!--
>AEM developers can create new device groups. (See [Creating Device Group Filters](/help/sites-developing/groupfilters.md).)
-->

Gebruik de volgende procedure om een mobiele pagina te ontwerpen:

1. Van globale navigatie open de **console van Plaatsen**.
1. Bewerk een inhoudspagina.
1. Schakelaar aan de gewenste mededinger door het **Emulator** pictogram bij de bovenkant van de pagina te klikken.

   ![&#x200B; Emulatorpictogram &#x200B;](/help/sites-cloud/authoring/assets/emulator.png)

1. Sleep componenten van de componentbrowser of de middelenbrowser naar de pagina.
1. [&#x200B; wijzigt de ontvankelijke lay-out &#x200B;](/help/sites-cloud/authoring/page-editor/responsive-layout.md) van de pagina en zijn componenten die op het geselecteerde apparaat worden gebaseerd.

De pagina ziet er ongeveer als volgt uit:

![&#x200B; Mobiel voorbeeld &#x200B;](/help/sites-cloud/authoring/assets/mobile.png)

>[!NOTE]
>
>De emulators worden uitgeschakeld wanneer een pagina op de auteurinstantie wordt opgevraagd bij een mobiel apparaat.
