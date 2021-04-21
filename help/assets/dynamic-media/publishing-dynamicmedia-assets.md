---
title: Dynamic Media-middelen publiceren
description: Leer hoe u Dynamic Media-middelen publiceert.
contentOwner: Rick Brough
feature: Beheer van bedrijfsmiddelen
role: Business Practitioner
exl-id: 8ee759dc-cb8f-4e80-8175-2c3ba06da862
translation-type: tm+mt
source-git-commit: e94289bccc09ceed89a2f8b926817507eaa19968
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 2%

---

# Dynamic Media-middelen {#publishing-dynamic-media-assets} publiceren

U publiceert uw Dynamic Media-elementen door de elementen te selecteren die u al hebt geüpload en op **[!UICONTROL Publish]** of **[!UICONTROL Quick Publish]** te tikken. Nadat uw Dynamic Media-elementen zijn gepubliceerd, kunt u ze via een URL of door code in te sluiten op de pagina opnemen.

U kunt ook direct elementen publiceren die u uploadt—zonder tussenkomst van de gebruiker. U kunt deze elementen ook selectief publiceren. Zie [Dynamic Media configureren](config-dm.md). U kunt ook selectief elementen publiceren naar Dynamic Media of Adobe Experience Manager, wederzijds exclusief van elkaar, met **[!UICONTROL Selective Publish]** op mapniveau. Zie [Werken met Selectieve publicatie in Dynamic Media](/help/assets/dynamic-media/selective-publishing.md).

In **[!UICONTROL Card View]** verschijnt een klein globe pictogram direct onder de naam van een element en links van de datum en tijd om erop te wijzen dat het wordt gepubliceerd. In de **[!UICONTROL List View]** geeft een kolom **[!UICONTROL Published]** aan welke assets zijn gepubliceerd en welke niet.

>[!NOTE]
>
>Als een element al is gepubliceerd, verplaatst u het element naar een andere map en publiceert u het opnieuw vanaf de nieuwe locatie. De oorspronkelijke locatie van het gepubliceerde element blijft dan beschikbaar, samen met het opnieuw gepubliceerde element. Het oorspronkelijke gepubliceerde middel is echter &quot;verloren&quot; voor de Experience Manager en kan niet ongepubliceerd worden. Daarom is het aan te raden eerst de publicatie van elementen ongedaan te maken voordat u deze naar een andere map verplaatst.

Als u video-elementen direct na het coderen wilt publiceren, moet u ervoor zorgen dat het coderen is voltooid. Wanneer video&#39;s worden gecodeerd, geeft het systeem aan dat er een videoverwerkingsworkflow wordt uitgevoerd. Wanneer videocodering is voltooid, kunt u een voorvertoning van de video-uitvoeringen bekijken. Op dat moment kunt u de video&#39;s veilig publiceren zonder publicatiefouten te maken.

Zie ook [URLs aan uw Toepassing van het Web verbinden](linking-urls-to-yourwebapplication.md).

Zie ook [De Dynamic Media Video-viewer of Afbeeldingsviewer insluiten op een webpagina](embed-code.md).

>[!NOTE]
>
>* Elementen moeten worden gepubliceerd om de URL te kunnen gebruiken. Als de elementen niet worden gepubliceerd, werkt het kopiëren en plakken van de URL in een webbrowser niet.
>* Voorinstellingen voor afbeeldingen en viewervoorinstellingen moeten worden geactiveerd en gepubliceerd voor live levering.

>



Zie [Elementen publiceren](/help/assets/manage-digital-assets.md) voor gedetailleerde informatie over het publiceren van een set of element.

## HTTP/2 levering van Dynamic Media-middelen {#http-delivery-of-dynamic-media-assets}

Experience Manager ondersteunt nu de levering van alle Dynamic Media-inhoud (afbeeldingen en video) via HTTP/2. Dit wil zeggen dat er een gepubliceerde URL of insluitcode voor de afbeelding of video beschikbaar is om te worden geïntegreerd met elke toepassing die een gehoste element accepteert. Dat gepubliceerde element wordt vervolgens geleverd via het HTTP/2-protocol. Deze leveringsmethode verbetert de manier waarop browsers en servers communiceren, waardoor u betere responstijd en laadtijden voor al uw Dynamic Media-middelen krijgt.

Zie [HTTP/2 levering van inhoud vaak gestelde vragen](/help/assets/dynamic-media/http2faq.md).

<!--this md file used to reside under sites-administering-->
