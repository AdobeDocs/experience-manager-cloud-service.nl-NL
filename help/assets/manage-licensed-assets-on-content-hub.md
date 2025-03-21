---
title: Gelicentieerde Assets beheren op Content Hub
description: Leer hoe u een licentieveld toevoegt aan het metagegevensformulier voor elementen, de eigenschap Licentie-metagegevens toepast op de mappen met elementen en elementen goedkeurt met gebruikslicenties.
exl-id: ac3aad9f-c7b3-47a7-9314-a2f8277f0d3e
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# Gelicentieerde Assets beheren op Content Hub {#manage-licensed-assets-on-content-hub}

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

>[!AVAILABILITY]
>
>Content Hub-gids is nu beschikbaar in PDF-indeling. Download de volledige handleiding en gebruik Adobe Acrobat AI Assistant om je vragen te beantwoorden.
>
>[!BADGE  de Gids PDF van Content Hub ]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/content-hub.pdf"}

Als beheerder kunt u het metagegevensformulier bewerken en het veld voor de elementlicentie opnemen, zodat het in de AEM-auteursomgeving wordt weergegeven in de eigenschappen Asset. Vervolgens kunt u het element goedkeuren, evenals de licentie om het middel onder licentie te geven en beschikbaar te maken op Content Hub.

Voer de volgende stappen uit:

1. Bewerk het metagegevensformulier om een nieuw tekstveld op te nemen waarin de licentiegegevens worden opgenomen. Wijs het tekstveld toe aan de eigenschap `dc:license` . Voor meer informatie over hoe te om gebieden aan een meta-gegevensvorm toe te voegen en eigenschappen te bepalen, zie {de Meta-gegevens van de Opstelling Forms ](/help/assets/metadata-assets-view.md#metadata-forms).[
   ![ zip extractie ](/help/assets/assets/metadata-form-edit.png)
1. Pas het metagegevensformulier toe op de elementmap om de instellingen in stap 1 toe te passen. Voor informatie over hoe te om een meta-gegevensvorm aan de activaomslag toe te wijzen, zie [ meta-gegevensvorm aan een omslag ](/help/assets/metadata-assets-view.md#metadata-forms) toewijzen.
1. [De PDF met licentie goedkeuren](/help/assets/manage-organize-assets-view.md#set-asset-status)
1. Selecteer de activa en klik **Details** om zijn eigenschappen te bekijken. In het vergunningsgebied dat in Stap 1 wordt toegevoegd, bepaal de absolute weg voor de activavergunning die in Stap 3 is goedgekeurd of reeds eerder goedgekeurd. Het absolute Content Hub-pad volgt het volgende standaardpatroon: `/content/dam/(The asset's folder hierarchy within the DAM repository)/(asset_name).(file_extension)`. Bijvoorbeeld /content/dam/teamA/projects/documents/file1.pdf
   ![ absolute weg ](/help/assets/assets/absolute-path.png)
1. Stem de activa goed om het in Content Hub beschikbaar te maken en klik **sparen**. Voor informatie over hoe te om activa goed te keuren, zie [ Vastgestelde activastatus ](/help/assets/manage-organize-assets-view.md#set-asset-status).
