---
title: Dynamische media-elementen publiceren
description: Leer hoe u video en afbeeldingselementen van dynamische media publiceert, zodat u deze via een URL of code op een webpagina kunt opnemen.
contentOwner: Rick Brough
feature: Asset Management
role: User
exl-id: 8ee759dc-cb8f-4e80-8175-2c3ba06da862
source-git-commit: 36ab36ba7e14962eba3947865545b8a3f29f6bbc
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 2%

---

# Dynamische media-elementen publiceren {#publishing-dynamic-media-assets}

U publiceert uw dynamische media-elementen door de elementen te selecteren die u al hebt geüpload en **[!UICONTROL Publish]** of **[!UICONTROL Quick Publish]** te selecteren. Nadat uw dynamische media-elementen zijn gepubliceerd, kunt u ze via een URL of door code in te sluiten op de pagina opnemen.

U kunt ook direct elementen publiceren die u uploadt, zonder tussenkomst van de gebruiker. U kunt deze elementen ook selectief publiceren. Zie [&#x200B; Dynamische Media &#x200B;](config-dm.md) vormen. U kunt ook selectief elementen publiceren naar Dynamic Media of Adobe Experience Manager, die elkaar wederzijds uitsluiten, met **[!UICONTROL Selective Publish]** op mapniveau. Zie [&#x200B; Werk met Selectief publiceren in Dynamische Media &#x200B;](/help/assets/dynamic-media/selective-publishing.md).

In **[!UICONTROL Card View]** wordt een klein globpictogram direct onder de naam van een element weergegeven en links van de datum en tijd om aan te geven dat het is gepubliceerd. In de **[!UICONTROL List View]** geeft een kolom **[!UICONTROL Published]** aan welke assets zijn gepubliceerd en welke niet.

>[!NOTE]
>
>Als een element al is gepubliceerd, verplaatst u het element naar een andere map en publiceert u het opnieuw vanaf de nieuwe locatie. De oorspronkelijke locatie van het gepubliceerde element blijft dan beschikbaar, samen met het opnieuw gepubliceerde element. Het oorspronkelijke gepubliceerde middel is echter &quot;verloren&quot; aan Experience Manager en kan niet ongepubliceerd worden. Daarom is het aan te raden eerst de publicatie van elementen ongedaan te maken voordat u deze naar een andere map verplaatst.

Als u video-elementen direct na het coderen wilt publiceren, moet u ervoor zorgen dat het coderen is voltooid. Wanneer video&#39;s worden gecodeerd, geeft het systeem aan dat er een videoverwerkingsworkflow wordt uitgevoerd. Wanneer videocodering is voltooid, kunt u een voorvertoning van de video-uitvoeringen bekijken. Op dat moment kunt u de video&#39;s veilig publiceren zonder publicatiefouten te maken.

Zie ook [&#x200B; Verbinding URLs aan uw Webtoepassing &#x200B;](linking-urls-to-yourwebapplication.md).

Zie ook [&#x200B; bed de Dynamische Video van Media kijker of de kijker van het Beeld op een Web-pagina &#x200B;](embed-code.md) in.

>[!NOTE]
>
>* Assets moet worden gepubliceerd om de URL te kunnen gebruiken. Als de elementen niet worden gepubliceerd, werkt het kopiëren en plakken van de URL in een webbrowser niet.
>* Voorinstellingen voor afbeeldingen en viewervoorinstellingen moeten worden geactiveerd en gepubliceerd voor live levering.
>

Voor gedetailleerde informatie bij het publiceren van een reeks of activa, zie [&#x200B; het Publiceren Assets &#x200B;](/help/assets/manage-digital-assets.md).

## HTTP/2-levering van Dynamic Media-elementen {#http-delivery-of-dynamic-media-assets}

Experience Manager ondersteunt nu de levering van alle Dynamic Media-inhoud (afbeeldingen en video) via HTTP/2. Dit wil zeggen dat er een gepubliceerde URL of insluitcode voor de afbeelding of video beschikbaar is om te worden geïntegreerd met elke toepassing die een gehoste element accepteert. Dat gepubliceerde element wordt vervolgens geleverd via het HTTP/2-protocol. Deze methode van levering verbetert de manier browsers en servers communiceren, die voor betere reactie en ladingstijden van al uw Dynamische activa van Media toestaan.

Zie [&#x200B; HTTP/2 levering van inhoud vaak gestelde vragen &#x200B;](/help/assets/dynamic-media/http2faq.md).

<!--this md file used to reside under sites-administering-->
