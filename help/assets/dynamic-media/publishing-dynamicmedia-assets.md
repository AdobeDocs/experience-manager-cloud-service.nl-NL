---
title: Dynamische media-elementen publiceren
description: Dynamische media-elementen publiceren
contentOwner: Rick Brough
translation-type: tm+mt
source-git-commit: b65ce0af6281f60272322744f0e6f81b7eb6b96a
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 2%

---


# Dynamische media-elementen publiceren {#publishing-dynamic-media-assets}

U publiceert uw dynamische media-elementen door de elementen te selecteren die u al hebt geüpload en op **[!UICONTROL Publish]** of **[!UICONTROL Quick Publish]** te tikken. Nadat uw dynamische media-elementen zijn gepubliceerd, kunt u ze via een URL of door code in te sluiten op de pagina opnemen.

U kunt ook direct elementen publiceren die u uploadt—zonder tussenkomst van de gebruiker. U kunt deze elementen ook selectief publiceren. Zie [Dynamische media configureren.](config-dm.md) Of u kunt selectief elementen publiceren naar Dynamic Media of AEM, elkaar wederzijds uitsluiten, met behulp van  **[!UICONTROL Selective Publish]** op mapniveau. Zie [Werken met Selectieve publicatie in dynamische media.](/help/assets/dynamic-media/selective-publishing.md)

In **[!UICONTROL Card View]** verschijnt een klein globe pictogram direct onder de naam van een element en links van de datum en tijd om erop te wijzen dat het wordt gepubliceerd. In de **[!UICONTROL List View]** geeft een kolom **[!UICONTROL Published]** aan welke assets zijn gepubliceerd en welke niet.

>[!NOTE]
>
>Als een element al is gepubliceerd, gebruikt u AEM om het element naar een andere map te verplaatsen en vanaf de nieuwe locatie opnieuw te publiceren, is de oorspronkelijke locatie van het gepubliceerde element nog steeds beschikbaar, samen met het opnieuw gepubliceerde element. Het oorspronkelijke gepubliceerde middel is echter &quot;verloren&quot; aan AEM en kan niet ongepubliceerd worden. Daarom is het aan te raden eerst de publicatie van elementen ongedaan te maken voordat u deze naar een andere map verplaatst.

Als u video-elementen direct na het coderen wilt publiceren, moet u ervoor zorgen dat de codering volledig is uitgevoerd. Wanneer video&#39;s nog steeds worden gecodeerd, wordt u via het systeem op de hoogte gebracht van een actieve workflow voor videoverwerking. Wanneer videocodering is voltooid, moet u een voorvertoning van de video-uitvoeringen kunnen bekijken. Op dat moment kunt u de video&#39;s veilig publiceren zonder publicatiefouten te maken.

Zie ook [URL&#39;s koppelen aan uw webtoepassing.](linking-urls-to-yourwebapplication.md)

Zie ook [De Dynamic Media Video-viewer of de Image Viewer insluiten op een webpagina.](embed-code.md)

>[!NOTE]
>
>* Elementen moeten worden gepubliceerd om de URL te kunnen gebruiken. Als de elementen niet worden gepubliceerd, werkt het kopiëren en plakken van de URL in een webbrowser niet.
>* Voorinstellingen voor afbeeldingen en viewervoorinstellingen moeten worden geactiveerd en gepubliceerd voor live levering.

>



Zie [Elementen publiceren.](/help/assets/manage-digital-assets.md)

## HTTP/2-levering van dynamische media-elementen {#http-delivery-of-dynamic-media-assets}

AEM ondersteunt nu de levering van alle Dynamic Media-inhoud (afbeeldingen en video) via HTTP/2. Dit wil zeggen dat er een gepubliceerde URL of insluitcode voor de afbeelding of video beschikbaar is om te worden geïntegreerd met elke toepassing die een gehoste element accepteert. Dat gepubliceerde element wordt vervolgens geleverd via het HTTP/2-protocol. Deze methode van levering verbetert de manier browsers en servers communiceren, die voor betere reactie en ladingstijden van al uw Dynamische activa van Media toestaan.

Zie [HTTP/2 levering van inhoud vaak gestelde vragen](/help/assets/dynamic-media/http2faq.md) om meer te leren.
<!--this md file used to reside under sites-administering-->
