---
title: Dynamische media-elementen publiceren
description: Dynamische media-elementen publiceren
translation-type: tm+mt
source-git-commit: 6224d193adfb87bd9b080f48937e0af1f03386d6

---


# Dynamische media-elementen publiceren {#publishing-dynamic-media-assets}

U publiceert uw dynamische media-elementen door de elementen te selecteren en op **[!UICONTROL Publiceren]** te tikken. Nadat uw dynamische media-elementen zijn gepubliceerd, kunt u ze via URL of via insluiten op een webpagina opnemen.

U kunt ook direct elementen publiceren die u uploadt—zonder tussenkomst van de gebruiker. Zie Dynamische media [configureren](config-dm.md).

In de **[!UICONTROL Kaartweergave]** wordt direct onder de naam van een element een pictogram van een kleine bol weergegeven om aan te geven dat het is gepubliceerd. In de **[!UICONTROL Lijstweergave]** geeft een kolom **[!UICONTROL Gepubliceerd]** aan welke elementen worden gepubliceerd of welke niet.

>[!NOTE]
>
>Als een element al is gepubliceerd, gebruikt u AEM om het element naar een andere map te verplaatsen en vanaf de nieuwe locatie opnieuw te publiceren, is de oorspronkelijke locatie van het gepubliceerde element nog steeds beschikbaar, samen met het opnieuw gepubliceerde element. Het oorspronkelijke gepubliceerde middel is echter &quot;verloren&quot; aan AEM en kan niet ongepubliceerd worden. Daarom is het aan te raden eerst de publicatie van elementen ongedaan te maken voordat u deze naar een andere map verplaatst.

Als u video-elementen direct na het coderen wilt publiceren, moet u ervoor zorgen dat de codering volledig is uitgevoerd. Wanneer video&#39;s nog steeds worden gecodeerd, wordt u via het systeem op de hoogte gebracht van een actieve workflow voor videoverwerking. Wanneer videocodering is voltooid, moet u een voorvertoning van de video-uitvoeringen kunnen bekijken. Op dat moment kunt u de video&#39;s veilig publiceren zonder publicatiefouten te maken.

Zie ook URLs [verbinden aan uw Toepassing](linking-urls-to-yourwebapplication.md)van het Web.

Zie ook De video-viewer [insluiten op een webpagina.](embed-code.md)

>[!NOTE]
>
>* Elementen moeten worden gepubliceerd om de URL te kunnen gebruiken. Als de elementen niet worden gepubliceerd, werkt het kopiëren en plakken van de URL in een webbrowser niet.
>* Voorinstellingen voor afbeeldingen en viewervoorinstellingen moeten worden geactiveerd en gepubliceerd voor live levering.
>



Zie Elementen [publiceren voor gedetailleerde informatie over het publiceren van een set of element.](/help/assets/manage-digital-assets.md)

## HTTP/2-levering van Dynamic Media-elementen {#http-delivery-of-dynamic-media-assets}

AEM ondersteunt nu de levering van alle Dynamic Media-inhoud (afbeeldingen en video) via HTTP/2. Dit wil zeggen dat er een gepubliceerde URL of insluitcode voor de afbeelding of video beschikbaar is om te worden geïntegreerd met elke toepassing die een gehoste element accepteert. Dat gepubliceerde element wordt vervolgens geleverd via het HTTP/2-protocol. Deze methode van levering verbetert de manier browsers en servers communiceren, die voor betere reactie en ladingstijden van al uw Dynamische activa van Media toestaan.

Zie [HTTP/2 levering van inhoud vaak gestelde vragen](/help/assets/dynamic-media/scene7-http2faq.md) om meer te leren.
<!--this md file used to reside under sites-administering-->
