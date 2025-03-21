---
title: Dynamische media-elementen publiceren
description: Leer hoe u video en afbeeldingselementen van dynamische media publiceert, zodat u deze via een URL of code op een webpagina kunt opnemen.
contentOwner: Rick Brough
feature: Asset Management
role: User
exl-id: 8ee759dc-cb8f-4e80-8175-2c3ba06da862
source-git-commit: c82f84fe99d8a196adebe504fef78ed8f0b747a9
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 2%

---

# Dynamische media-elementen publiceren {#publishing-dynamic-media-assets}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b> Dynamische Media Prime en Ultimate </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b> AEM Assets Ultimate </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b> integratie van AEM Assets met Edge Delivery Services </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b> Uitbreidbaarheid UI </b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuw </i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b> laat Dynamische Media Prime en Ultimate </b></a> toe
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b> Beste praktijken van het Onderzoek </b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b> Beste praktijken van Meta-gegevens </b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b> Content Hub </b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b> Dynamische Media met mogelijkheden OpenAPI </b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b> de ontwikkelaarsdocumentatie van AEM Assets </b></a>
        </td>
    </tr>
</table>

U publiceert uw dynamische media-elementen door de elementen te selecteren die u al hebt geüpload en **[!UICONTROL Publish]** of **[!UICONTROL Quick Publish]** te selecteren. Nadat uw dynamische media-elementen zijn gepubliceerd, kunt u ze via een URL of door code in te sluiten op de pagina opnemen.

U kunt ook direct elementen publiceren die u uploadt, zonder tussenkomst van de gebruiker. U kunt deze elementen ook selectief publiceren. Zie [ Dynamische Media ](config-dm.md) vormen. U kunt ook selectief elementen publiceren naar Dynamic Media of Adobe Experience Manager, die elkaar wederzijds uitsluiten, met **[!UICONTROL Selective Publish]** op mapniveau. Zie [ Werk met Selectief publiceren in Dynamische Media ](/help/assets/dynamic-media/selective-publishing.md).

In **[!UICONTROL Card View]** wordt een klein globpictogram direct onder de naam van een element weergegeven en links van de datum en tijd om aan te geven dat het is gepubliceerd. In de **[!UICONTROL List View]** geeft een kolom **[!UICONTROL Published]** aan welke assets zijn gepubliceerd en welke niet.

>[!NOTE]
>
>Als een element al is gepubliceerd, verplaatst u het element naar een andere map en publiceert u het opnieuw vanaf de nieuwe locatie. De oorspronkelijke locatie van het gepubliceerde element blijft dan beschikbaar, samen met het opnieuw gepubliceerde element. Het oorspronkelijke gepubliceerde middel is echter &quot;verloren&quot; aan Experience Manager en kan niet ongepubliceerd worden. Daarom is het aan te raden eerst de publicatie van elementen ongedaan te maken voordat u deze naar een andere map verplaatst.

Als u video-elementen direct na het coderen wilt publiceren, moet u ervoor zorgen dat het coderen is voltooid. Wanneer video&#39;s worden gecodeerd, geeft het systeem aan dat er een videoverwerkingsworkflow wordt uitgevoerd. Wanneer videocodering is voltooid, kunt u een voorvertoning van de video-uitvoeringen bekijken. Op dat moment kunt u de video&#39;s veilig publiceren zonder publicatiefouten te maken.

Zie ook [ Verbinding URLs aan uw Webtoepassing ](linking-urls-to-yourwebapplication.md).

Zie ook [ bed de Dynamische Video van Media kijker of de kijker van het Beeld op een Web-pagina ](embed-code.md) in.

>[!NOTE]
>
>* Assets moet worden gepubliceerd om de URL te kunnen gebruiken. Als de elementen niet worden gepubliceerd, werkt het kopiëren en plakken van de URL in een webbrowser niet.
>* Voorinstellingen voor afbeeldingen en viewervoorinstellingen moeten worden geactiveerd en gepubliceerd voor live levering.
>

Voor gedetailleerde informatie bij het publiceren van een reeks of activa, zie [ het Publiceren Assets ](/help/assets/manage-digital-assets.md).

## HTTP/2-levering van Dynamic Media-elementen {#http-delivery-of-dynamic-media-assets}

Experience Manager ondersteunt nu de levering van alle Dynamic Media-inhoud (afbeeldingen en video) via HTTP/2. Dit wil zeggen dat er een gepubliceerde URL of insluitcode voor de afbeelding of video beschikbaar is om te worden geïntegreerd met elke toepassing die een gehoste element accepteert. Dat gepubliceerde element wordt vervolgens geleverd via het HTTP/2-protocol. Deze methode van levering verbetert de manier browsers en servers communiceren, die voor betere reactie en ladingstijden van al uw Dynamische activa van Media toestaan.

Zie [ HTTP/2 levering van inhoud vaak gestelde vragen ](/help/assets/dynamic-media/http2faq.md).

<!--this md file used to reside under sites-administering-->
