---
title: Gelicentieerde Assets beheren op Content Hub
description: Leer hoe u een licentieveld toevoegt aan het metagegevensformulier voor elementen, de eigenschap Licentie-metagegevens toepast op de mappen met elementen en elementen goedkeurt met gebruikslicenties.
exl-id: ac3aad9f-c7b3-47a7-9314-a2f8277f0d3e
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---

# Gelicentieerde Assets beheren op Content Hub {#manage-licensed-assets-on-content-hub}

Als beheerder kunt u het metagegevensformulier bewerken en het veld voor de elementlicentie opnemen, zodat het in de AEM-auteursomgeving wordt weergegeven in de eigenschappen Asset. Vervolgens kunt u het element goedkeuren, evenals de licentie om het middel onder licentie te geven en beschikbaar te maken op Content Hub.

Voer de volgende stappen uit:

1. Bewerk het metagegevensformulier om een nieuw tekstveld op te nemen waarin de licentiegegevens worden opgenomen. Wijs het tekstveld toe aan de eigenschap `dc:license` . Voor meer informatie over hoe te om gebieden aan een meta-gegevensvorm toe te voegen en eigenschappen te bepalen, zie &lbrace;de Meta-gegevens van de Opstelling Forms [&#128279;](/help/assets/metadata-assets-view.md#metadata-forms).
   ![&#x200B; zip extractie &#x200B;](/help/assets/assets/metadata-form-edit.png)
1. Pas het metagegevensformulier toe op de elementmap om de instellingen in stap 1 toe te passen. Voor informatie over hoe te om een meta-gegevensvorm aan de activaomslag toe te wijzen, zie [&#x200B; meta-gegevensvorm aan een omslag &#x200B;](/help/assets/metadata-assets-view.md#metadata-forms) toewijzen.
1. [De PDF met licentie goedkeuren](/help/assets/manage-organize-assets-view.md#set-asset-status)
1. Selecteer de activa en klik **Details** om zijn eigenschappen te bekijken. In het vergunningsgebied dat in Stap 1 wordt toegevoegd, bepaal de absolute weg voor de activavergunning die in Stap 3 is goedgekeurd of reeds eerder goedgekeurd. Het absolute Content Hub-pad volgt het volgende standaardpatroon: `/content/dam/(The asset's folder hierarchy within the DAM repository)/(asset_name).(file_extension)`. Bijvoorbeeld /content/dam/teamA/projects/documents/file1.pdf
   ![&#x200B; absolute weg &#x200B;](/help/assets/assets/absolute-path.png)
1. Stem de activa goed om het in Content Hub beschikbaar te maken en klik **sparen**. Voor informatie over hoe te om activa goed te keuren, zie [&#x200B; Vastgestelde activastatus &#x200B;](/help/assets/manage-organize-assets-view.md#set-asset-status).
