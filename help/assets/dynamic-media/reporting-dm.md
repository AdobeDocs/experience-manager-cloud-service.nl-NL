---
title: Rapportage in dynamische media
description: Leer hoe te om een foutenrapport voor Dynamische Media te verzoeken levert URLs die ontbreken.
contentOwner: Rick Brough
feature: Asset Management
role: User
hide: true
hidefromtoc: true
exl-id: 2488f813-df15-4dbb-8747-f827ee5925e1
source-git-commit: c82f84fe99d8a196adebe504fef78ed8f0b747a9
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 0%

---

# Vraag een foutenrapport voor Dynamische levering URLs van Media die ontbreken

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

U kunt om een foutenrapport verzoeken dat Dynamische Media URLs identificeert die in leveringstijd ontbrak. Het rapport is een aggregatie van gegevens tot vijf dagen en is beschikbaar in CSV-indeling. Het foutenrapport bevat de volgende informatie:

* Dynamische URL voor levering van media is mislukt - Een mislukte URL is een door dynamische media gegenereerde URL die geen inhoud kan produceren op het moment van levering.
* Referrer-URL - De referentie-URL waarvan de mislukte leverings-URL wordt aangeroepen.
* Aantal mislukkingen - Het aantal keren dat de leverings-URL is geladen en dat tot een fout heeft geleid.

Wanneer u om het foutenrapport verzoekt, e-mailt het team van de Media van Adobe het rapport aan u, in Csv formaat. Het heeft betrekking op een periode van vijf dagen vanaf de dag waarop uw verzoek is ingediend.

U kunt een foutenrapport eens per maand, voor een bepaald bedrijf aanvragen.

**om een foutenrapport voor Dynamische levering URLs van Media te verzoeken die ontbreken:**

1. [ verzend een e-mail naar reports-dynamic-media@adobe.com ](mailto:reports-dynamic-media@adobe.com) met de bedrijfsnaam die met uw Dynamische rekening van Media wordt geassocieerd.

   Als u niet de bedrijfsnaam kent, zie de [ Dynamische pagina van de Configuratie van Media ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/config-dm.html?lang=en#configuring-dynamic-media-cloud-services) in **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Dynamic Media Configuation]**. Voor de Dynamische Browser van de Configuratie van Media pagina, klik **[!UICONTROL global]**, selecteer *[Dynamic_Media_folder_icon]* checkbox, dan uitgezochte **[!UICONTROL Edit]**. U moet beheerdersrechten in AEM hebben om toegang te krijgen tot de pagina Dynamic Media Configuration.

   ![ die tot de Dynamische pagina van de Configuratie van Media toegang hebben.](/help/assets/dynamic-media/assets/reporting-accessdmconfig.png)
