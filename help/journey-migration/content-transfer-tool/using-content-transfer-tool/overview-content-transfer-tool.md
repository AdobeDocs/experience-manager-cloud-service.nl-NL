---
title: Overzicht van de tool Content Transfer
description: Overzicht van de tool Content Transfer
exl-id: cfc0366a-2139-4d9d-b5bc-0b65bef4013c
source-git-commit: 8197b4f4e5cda21532c3660c2f0ec4855ba53a6a
workflow-type: tm+mt
source-wordcount: '648'
ht-degree: 37%

---

# Overzicht {#overview-content-transfer-tool}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_overview"
>title="Overzicht"
>abstract="Het hulpmiddel van de Overdracht van de inhoud is een hulpmiddel dat door Adobe wordt ontwikkeld die kan worden gebruikt om de migratie van bestaande inhoud van een bron AEM instantie (op-gebouw of AMS) aan de doelinstantie van AEM Cloud Service in werking te stellen. Met de tool worden &#39;principals&#39; (gebruikers of groepen) automatisch overgedragen."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html" text="Richtlijnen en best practices"

Het hulpmiddel van de Overdracht van de Inhoud is een hulpmiddel dat door Adobe wordt ontwikkeld die kan worden gebruikt om de migratie van bestaande inhoud van een bron AEM instantie (op-gebouw of AMS) aan de doelinstantie van AEM Cloud Service in werking te stellen.

Met de tool worden &#39;principals&#39; (gebruikers of groepen) automatisch overgedragen.  Zie [Toewijzing van gebruikers en belangrijkste migratie](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/user-mapping-and-migration.md) voor meer informatie .

Met het gereedschap Inhoud overbrengen kunt u het proces voor inhoudsoverdracht integreren met Cloud Acceleration Manager. Hierdoor krijgt de gebruiker alle voordelen die het biedt:

* Zelfbediening om een migratieset één keer uit te pakken en tegelijkertijd in meerdere omgevingen in te voeren
* Verbeterde gebruikerservaring dankzij betere laadstatussen, instructies en foutafhandeling
* Logbestanden voor insluiting blijven bestaan en zijn altijd beschikbaar voor probleemoplossing
* Validatie- en hoofdmigratierapporten zijn beschikbaar voor validatie

## Fasen in gereedschap Inhoud overbrengen {#phases-content-transfer-tool}

De overdracht van content bestaat uit twee fasen:

1. **Extractie**: Dit heeft betrekking op het extraheren van content van de AEM-broninstantie naar een tijdelijke locatie, de zogenaamde *migratieset*. Een *migratieset* is een opslaggebied op de cloud dat door Adobe wordt geleverd om overgedragen content tijdelijk op te slaan tussen de AEM-broninstantie en de AEM Cloud Service-instantie.

   Raadpleeg [Extractieproces in Content Transfer](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md) voor meer informatie.

   >[!NOTE]
   >Toewijzing van gebruikers wordt nu automatisch uitgevoerd als onderdeel van de extractiefase bij de auteur (maar kan optioneel worden uitgeschakeld bij de auteur of ingeschakeld bij publicatie). Zie [Toewijzing van gebruikers en belangrijkste migratie](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/user-mapping-and-migration.md) voor meer informatie .

1. **Opname**: Dit verwijst naar het verplaatsen en opnemen van content uit de *migratieset* naar de Cloud Service-doelinstantie.

   Zie [Ingestieproces in inhoudsoverdracht](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md) voor meer informatie .

## Attributen van een migratieset {#attributes-migration-set}

Een migratieset heeft de volgende kenmerken:

* Met de nieuwe versie kunt u maximaal vijf migratiesets maken in een project dat is gemaakt in Cloud Acceleration Manager.
* Elke migratieset moet een unieke naam hebben.

De Content Transfer-tool heeft een functie die ondersteuning biedt voor differentiële aanvulling van content. Hierbij worden alleen die wijzigingen overgedragen die zijn aangebracht sinds de vorige activiteit voor contentoverdracht.

>[!NOTE]
>Na de eerste overdracht van content wordt het aangeraden om regelmatig differentiële aanvullingen van content uit te voeren. Zo houdt u de periode waarin content wordt &#39;bevroren&#39; voor de uiteindelijke differentiële contentoverdracht zo kort mogelijk, voordat u live gaat op Cloud Service.

Als u in de extractiefase een bestaande migratieset wilt ***aanvullen***, moet de optie voor *overschrijven* zijn uitgeschakeld. Raadpleeg [Extractie aanvullen](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process) voor meer informatie.

Als u in de opnamefase de deltacontent boven op de huidige content wilt toepassen, moet de optie voor *wissen* zijn uitgeschakeld. Zie [Opname aanvullen](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process) voor meer informatie.

## Vervaldatum migratieset {#migration-set-expiry}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_migrationset_expiry"
>title="Verlopen van een migratieset"
>abstract="Meer informatie over het verlopen van een migratieset."

Alle migratiesets zullen uiteindelijk verlopen na een langdurige periode van inactiviteit van ongeveer 90 dagen. Nadat de indicatoren gedurende een bepaalde periode op de projectkaart en de rijen van de migratietabel worden getoond, zal de migratieset verlopen en zijn gegevens zullen niet meer beschikbaar zijn. De verlooptijd kan eenvoudig worden verlengd door op de migratie te reageren die wordt ingesteld door:

* beschrijving bewerken
* extractietoets
* een extractie uitvoeren
* er een inname van maken

Het verstrijken van een migratieset kan op de rij van de Plaats van de Migratie worden gecontroleerd. Een nuttige visuele indicator dat een migratieset zijn vervaldatum nadert voegde ook de kaart van het project toe.

![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam29.png)


## Volgende functies {#whats-next}

Als u eenmaal over Content Transfer Tool hebt geleerd en het bijbehorende overzicht waarin dit gereedschap wordt beschreven, kunt u bestaande inhoud verplaatsen van een bron-AEM-instantie (on-premise of AMS) naar de AEM Cloud Service-doelinstantie, moet u de inhoud controleren [Voorwaarden voor het gereedschap Inhoud overbrengen](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/prerequisites-content-transfer-tool.md).
