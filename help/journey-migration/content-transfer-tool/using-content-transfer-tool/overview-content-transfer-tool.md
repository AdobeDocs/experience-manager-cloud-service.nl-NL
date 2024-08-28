---
title: Overzicht van de tool Content Transfer
description: Leer hoe u met het gereedschap Inhoud overbrengen inhoud van een on-premise AEM-instantie kunt overbrengen naar AEM as a Cloud Service
exl-id: cfc0366a-2139-4d9d-b5bc-0b65bef4013c
feature: Migration
role: Admin
source-git-commit: e73933acc3ff23d1456f03b288f2f842a6289ace
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 29%

---


# Overzicht {#overview-content-transfer-tool}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_overview"
>title="Overzicht"
>abstract="Het hulpmiddel van de Overdracht van de inhoud is een hulpmiddel dat door Adobe wordt ontwikkeld die kan worden gebruikt om de migratie van bestaande inhoud van een bron AEM instantie (op-gebouw of AMS) aan de doelinstantie van AEM Cloud Service in werking te stellen. Met dit gereedschap worden ook groepen automatisch overgedragen."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html" text="Richtlijnen en beste praktijken"

Het hulpmiddel van de Overdracht van de Inhoud is een hulpmiddel dat door Adobe wordt ontwikkeld die kan worden gebruikt om de migratie van bestaande inhoud van een bron AEM instantie (op-gebouw of AMS) aan de doelinstantie van AEM Cloud Service in werking te stellen.

Met dit gereedschap worden ook groepen automatisch overgedragen.  Zie ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/group-migration.md) van de Migratie van de Groep 0} voor meer informatie.[

Met het gereedschap Inhoud overbrengen wordt het proces voor inhoudsoverdracht geïntegreerd met Cloud Acceleration Manager. Hierdoor krijgt de gebruiker alle voordelen die het biedt:

* Zelfbediening om een migratieset één keer uit te pakken en tegelijkertijd in meerdere omgevingen in te voeren
* Verbeterde gebruikerservaring dankzij betere laadstatussen, instructies en foutafhandeling
* Logbestanden voor insluiting blijven bestaan en zijn altijd beschikbaar voor probleemoplossing
* Validatie- en hoofdmigratierapporten zijn beschikbaar voor validatie

## Fasen in gereedschap Inhoud overbrengen {#phases-content-transfer-tool}

De overdracht van content bestaat uit twee fasen:

1. **Extractie**: Dit heeft betrekking op het extraheren van content van de AEM-broninstantie naar een tijdelijke locatie, de zogenaamde *migratieset*. Een *migratieset* is een opslaggebied op de cloud dat door Adobe wordt geleverd om overgedragen content tijdelijk op te slaan tussen de AEM-broninstantie en de AEM Cloud Service-instantie.

   Zie [ Proces van de Opwinning in de Overdracht van de Inhoud ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md) voor meer details.

1. **Opname**: Dit verwijst naar het verplaatsen en opnemen van content uit de *migratieset* naar de Cloud Service-doelinstantie.

   Zie [ Proces van de Ingestie in de Overdracht van de Inhoud ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md) voor meer details.

## Attributen van een migratieset {#attributes-migration-set}

Een migratieset heeft de volgende kenmerken:

* Met de nieuwe versie kunt u maximaal tien migratiesets maken in een project dat in Cloud Acceleration Manager is gemaakt.
* Elke migratieset moet een unieke naam hebben.

De Content Transfer-tool heeft een functie die ondersteuning biedt voor differentiële aanvulling van content. Hierbij worden alleen die wijzigingen overgedragen die zijn aangebracht sinds de vorige activiteit voor contentoverdracht.

>[!NOTE]
>Na de eerste overdracht van content wordt het aangeraden om regelmatig differentiële aanvullingen van content uit te voeren. Zo houdt u de periode waarin content wordt &#39;bevroren&#39; voor de uiteindelijke differentiële contentoverdracht zo kort mogelijk, voordat u live gaat op Cloud Service.

Als u in de extractiefase een bestaande migratieset wilt ***aanvullen***, moet de optie voor *overschrijven* zijn uitgeschakeld. Zie [ Hoogste Extractie ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process) voor meer details.

Als u in de opnamefase de deltacontent boven op de huidige content wilt toepassen, moet de optie voor *wissen* zijn uitgeschakeld. Zie [ Omhoog Ingestie ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process) voor meer details.

## Vervaldatum migratieset {#migration-set-expiry}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_migrationset_expiry"
>title="Verlopen van een migratieset"
>abstract="Meer informatie over het verlopen van een migratieset."

Alle migratiesets zullen uiteindelijk verlopen na een verlengde periode van inactiviteit van ongeveer 45 dagen. Nadat de indicatoren gedurende een bepaalde periode op de projectkaart en de rijen van de migratietabel worden getoond, zal de migratieset verlopen en zijn gegevens zullen niet meer beschikbaar zijn. De verlooptijd kan eenvoudig worden verlengd door op de migratie te reageren die wordt ingesteld door:

* beschrijving bewerken
* extractietoets
* een extractie uitvoeren
* er een inname van maken

Het verstrijken van een migratieset kan op de rij van de Plaats van de Migratie worden gecontroleerd. Een nuttige visuele indicator dat een migratieset zijn vervaldatum nadert voegde ook de kaart van het project toe.

![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam29.png)

## Volgende functies {#whats-next}

Zodra u over het Hulpmiddel van de Overdracht van de Inhoud en zijn overzicht hebt geleerd dat dit hulpmiddel kan worden gebruikt om bestaande inhoud over van een bron AEM instantie (op-gebouw of AMS) aan de instantie van doelAEM Cloud Service te bewegen, moet u [ Eerste vereisten voor het Hulpmiddel van de Overdracht van de Inhoud ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/prerequisites-content-transfer-tool.md) herzien.
