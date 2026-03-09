---
title: Gelicentieerde Assets beheren op Content Hub
description: Leer hoe u een licentieveld toevoegt aan het metagegevensformulier voor elementen, de eigenschap Licentie-metagegevens toepast op de mappen met elementen en elementen goedkeurt met gebruikslicenties.
badgeSaas: label="AEM Assets" type="Positive" tooltip="van toepassing op AEM Assets)."
exl-id: ac3aad9f-c7b3-47a7-9314-a2f8277f0d3e
source-git-commit: a641933d1049cd07ee8935672c8ef357a5bbf18c
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 0%

---

# Gelicentieerde Assets beheren op Content Hub {#manage-licensed-assets-on-content-hub}

Als beheerder kunt u het metagegevensformulier bewerken en het veld voor de elementlicentie opnemen, zodat het in de AEM-auteursomgeving wordt weergegeven in de eigenschappen Asset. Vervolgens kunt u het element goedkeuren, evenals de licentie om het middel onder licentie te geven en beschikbaar te maken op Content Hub.

Voer de volgende stappen uit:

1. Bewerk het metagegevensformulier om een nieuw tekstveld op te nemen waarin de licentiegegevens worden opgenomen. Wijs het tekstveld toe aan de eigenschap `dc:license` . Voor meer informatie over hoe te om gebieden aan een meta-gegevensvorm toe te voegen en eigenschappen te bepalen, zie {de Meta-gegevens van de Opstelling Forms [.](/help/assets/metadata-assets-view.md#metadata-forms)
   ![ zip extractie ](/help/assets/assets/metadata-form-edit.png)
1. Pas het metagegevensformulier toe op de elementmap om de instellingen in stap 1 toe te passen. Voor informatie over hoe te om een meta-gegevensvorm aan de activaomslag toe te wijzen, zie [ meta-gegevensvorm aan een omslag ](/help/assets/metadata-assets-view.md#metadata-forms) toewijzen.
1. [De PDF met licentie goedkeuren](/help/assets/manage-organize-assets-view.md#set-asset-status)
1. Selecteer de activa en klik **Details** om zijn eigenschappen te bekijken. In het vergunningsgebied dat in Stap 1 wordt toegevoegd, bepaal de absolute weg voor de activavergunning die in Stap 3 is goedgekeurd of reeds eerder goedgekeurd. Het absolute Content Hub-pad volgt het volgende standaardpatroon: `/content/dam/(The asset's folder hierarchy within the DAM repository)/(asset_name).(file_extension)`. Bijvoorbeeld /content/dam/teamA/projects/documents/file1.pdf
   ![ absolute weg ](/help/assets/assets/absolute-path.png)
1. Stem de activa goed om het in Content Hub beschikbaar te maken en klik **sparen**. Voor informatie over hoe te om activa goed te keuren, zie [ Vastgestelde activastatus ](/help/assets/manage-organize-assets-view.md#set-asset-status).

## Veelgestelde vragen {#faqs-manage-licensed-assets-content-hub}

### Wat is het doel van het beheer van gelicentieerde activa op AEM Assets Content Hub?

Met het beheer van gelicentieerde middelen op Content Hub kunnen beheerders ervoor zorgen dat alleen goedgekeurde middelen met geldige licenties beschikbaar zijn voor gebruik, dat de compatibiliteit en juiste controle van metagegevens binnen de AEM-auteursomgeving behouden blijven.

### Hoe kan ik een licentieveld toevoegen aan eigenschappen van elementen in Experience Manager as a Cloud Service?

U kunt een licentieveld toevoegen aan de eigenschappen van elementen door het metagegevensformulier te bewerken en een nieuw tekstveld op te nemen dat is toegewezen aan de eigenschap `dc:license` . Dit veld wordt vervolgens weergegeven in de eigenschappen van het element in de ontwerpomgeving van AEM Assets.

### Hoe kunt u een metagegevensformulier toepassen op een map met middelen om het licentieveld op te nemen in de eigenschappen van elementen?

Bewerk het metagegevensformulier om het licentieveld op te nemen. Pas dit metagegevensformulier toe op de gewenste elementmap om ervoor te zorgen dat de nieuwe instellingen worden opgenomen voor alle elementen in die map.

### Hoe specificeer ik de vergunningsdetails voor een activa?

Om de vergunningsdetails te specificeren, selecteer het element, klik **Details** om zijn eigenschappen te bekijken, en de absolute weg van de goedgekeurde activavergunning op het vergunningsgebied in te gaan dat aan de meta-gegevensvorm wordt toegevoegd.

### Wat is de vereiste indeling voor het absolute pad van Content Hub voor een licentie voor activa?

Het absolute pad van Content Hub moet het patroon volgen: /content/dam/(De maphiërarchie van het element in de DAM-opslagplaats)/(asset_name).(file_extension). Bijvoorbeeld `/content/dam/teamA/projects/documents/file1.pdf` .

### Waarom is het belangrijk om zowel het actief als zijn licentie goed te keuren en deze beschikbaar te stellen op AEM Assets Content Hub?

Door zowel het bedrijfsmiddel als de licentie goed te keuren, zorgt u ervoor dat alleen bedrijfsmiddelen met een licentie en geautoriseerde bedrijfsmiddelen beschikbaar worden gesteld op AEM Assets Content Hub, zodat u zich aan de regels kunt houden en de gebruiksrechten kunt behouden.

### Hoe maak ik een middel beschikbaar in AEM Assets Content Hub nadat ik de licentie heb goedgekeurd?

Nadat u het licentiepad hebt gedefinieerd in de eigenschappen van het element, keurt u het element goed en klikt u op Opslaan. Deze actie stelt het in licentie gegeven actief beschikbaar in AEM Assets Content Hub.

### Wie is verantwoordelijk voor het beheer van gelicentieerde activa in Content Hub?

Beheerders zijn verantwoordelijk voor het bewerken van metagegevensformulieren, het toewijzen van deze formulieren aan mappen met elementen en het goedkeuren van zowel elementen als hun licenties in Content Hub.
