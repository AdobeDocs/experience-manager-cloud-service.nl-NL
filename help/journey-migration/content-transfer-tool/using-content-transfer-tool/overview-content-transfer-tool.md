---
title: Overzicht van de tool Content Transfer
description: Overzicht van de tool Content Transfer
exl-id: cfc0366a-2139-4d9d-b5bc-0b65bef4013c
source-git-commit: 99ecf1309b9fa7613bfb9c99de9677700082f128
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 43%

---

# Overzicht {#overview-content-transfer-tool}


>[!CONTEXTUALHELP]
>id="aemcloud_ctt_overview"
>title="Overzicht"
>abstract="Het hulpmiddel van de Overdracht van de inhoud is een hulpmiddel dat door Adobe wordt ontwikkeld die kan worden gebruikt om bestaande inhoud over van een bron AEM instantie (op-gebouw of AMS) aan de doelinstantie van AEM Cloud Service te bewegen. Met de tool worden &#39;principals&#39; (gebruikers of groepen) automatisch overgedragen."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=en" text="Richtlijnen en best practices"

<!-- Alexandru: Old version of contextual help, keep for failover/debugging
>[!CONTEXTUALHELP]
>id="aemcloud_ctt_overview"
>title="Overview"
>abstract="Content Transfer Tool is a tool developed by Adobe that can be used to move existing content over from a source AEM instance (on-premise or AMS) to the target AEM Cloud Service instance. This tool also transfers principals (users or groups) automatically."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#extraction-process" text="Extraction Process"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#ingestion-process" text="Ingestion Process" -->

De tool Content Transfer is door Adobe ontwikkeld. Hiermee kunt u bestaande content van een AEM-broninstantie (On-Premise of AMS) verplaatsen naar de doelinstantie van AEM Cloud Service.

Met de tool worden &#39;principals&#39; (gebruikers of groepen) automatisch overgedragen.

Er is een nieuwe versie van het gereedschap Inhoud overbrengen beschikbaar waarin het proces voor de overdracht van inhoud wordt geïntegreerd met het programma voor de versnelling van de cloud. Het wordt ten zeerste aanbevolen over te schakelen op deze nieuwe versie om alle voordelen van deze versie te benutten:

* Zelfbediening om een migratieset één keer uit te pakken en tegelijkertijd in meerdere omgevingen in te voeren
* Verbeterde gebruikerservaring dankzij betere laadstatussen, hulplijnen en foutafhandeling
* Logbestanden voor insluiting blijven bestaan en zijn altijd beschikbaar voor probleemoplossing

Als u de nieuwe versie wilt gaan gebruiken, moet u oudere versies van het gereedschap Inhoud overbrengen verwijderen, omdat het programma een belangrijke architecturale wijziging heeft ondergaan.

>[!NOTE]
>
> In situaties waarin al een migratie wordt uitgevoerd, kunt u de vorige versie van CTT blijven gebruiken totdat de migratie is voltooid. Voor documentatie met betrekking tot de vorige versie van CTT raadpleegt u de [oudere documentatie](/help/journey-migration/content-transfer-tool/ctt-legacy/overview-content-transfer-tool-legacy.md).

## Fasen in gereedschap Inhoud overbrengen {#phases-content-transfer-tool}

De overdracht van content bestaat uit twee fasen:

1. **Extractie**: Dit heeft betrekking op het extraheren van content van de AEM-broninstantie naar een tijdelijke locatie, de zogenaamde *migratieset*. Een *migratieset* is een opslaggebied op de cloud dat door Adobe wordt geleverd om overgedragen content tijdelijk op te slaan tussen de AEM-broninstantie en de AEM Cloud Service-instantie.

   Raadpleeg [Extractieproces in Content Transfer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/extracting-content.html) voor meer informatie.

   >[!NOTE]
   > Het wordt aanbevolen het gereedschap Toewijzing gebruiker uit te voeren als onderdeel van de extractiefase. Zie [Gebruikerstoewijzing gebruiken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/user-mapping-tool/using-user-mapping-tool.html) voor meer informatie .

1. **Opname**: Dit verwijst naar het verplaatsen en opnemen van content uit de *migratieset* naar de Cloud Service-doelinstantie.

   Zie [Ingestieproces in inhoudsoverdracht](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/ingesting-content.html) voor meer informatie .

## Attributen van een migratieset {#attributes-migration-set}

Een migratieset heeft de volgende kenmerken:

* Met de nieuwe versie kunt u maximaal vijf migratiesets maken in een project dat is gemaakt in Cloud Acceleration Manager.
* Elke migratieset moet een unieke naam hebben.

De Content Transfer-tool heeft een functie die ondersteuning biedt voor differentiële aanvulling van content. Hierbij worden alleen die wijzigingen overgedragen die zijn aangebracht sinds de vorige activiteit voor contentoverdracht.

>[!NOTE]
>Na de eerste overdracht van content wordt het aangeraden om regelmatig differentiële aanvullingen van content uit te voeren. Zo houdt u de periode waarin content wordt &#39;bevroren&#39; voor de uiteindelijke differentiële contentoverdracht zo kort mogelijk, voordat u live gaat op Cloud Service.

Als u in de extractiefase een bestaande migratieset wilt ***aanvullen***, moet de optie voor *overschrijven* zijn uitgeschakeld. Raadpleeg [Extractie aanvullen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/extracting-content.html?lang=en#top-up-extraction-process) voor meer informatie.

Als u in de opnamefase de deltacontent boven op de huidige content wilt toepassen, moet de optie voor *wissen* zijn uitgeschakeld. Zie [Opname aanvullen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/ingesting-content.html?lang=en#top-up-ingestion-process) voor meer informatie.

## Volgende functies {#whats-next}

Als u eenmaal over Content Transfer Tool hebt geleerd en het bijbehorende overzicht waarin dit gereedschap wordt beschreven, kunt u bestaande inhoud verplaatsen van een bron-AEM-instantie (on-premise of AMS) naar de AEM Cloud Service-doelinstantie, moet u de inhoud controleren [Voorwaarden voor het gereedschap Inhoud overbrengen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/prerequisites-content-transfer-tool.html?lang=en).
