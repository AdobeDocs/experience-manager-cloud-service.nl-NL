---
title: Inhoud uit Source extraheren
description: Leer hoe u inhoud van een Adobe Experience Manager-broninstantie (AEM) extraheert om deze later naar een Cloud Service-AEM over te brengen.
exl-id: c5c08c4e-d5c3-4a66-873e-96986e094fd3
feature: Migration
role: Admin
source-git-commit: 4408f15ef85d0fc2c6a0e2b45038dc900d212187
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 9%

---

# Inhoud uit Source extraheren {#extracting-content}

## Extractieproces in gereedschap voor inhoudsoverdracht {#extraction-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_extraction"
>title="Inhoud extraheren"
>abstract="Extractie heeft betrekking op het extraheren van inhoud van de Adobe Experience Manager-instantie (AEM) van de bron naar een tijdelijk gebied dat migratieset wordt genoemd. Een migratieset is een gebied van de wolkenopslag dat door Adobe wordt verstrekt om de overgebracht inhoud tussen de bron AEM instantie en de AEM van de Cloud Service tijdelijk op te slaan."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html#top-up-extraction-process" text="Extractie naar boven"


Voer de onderstaande stappen uit om uw migratieset te extraheren uit de Content Transfer-tool:

>[!NOTE]
>Als Amazon S3, Azure Data Store of File Data Store wordt gebruikt als het type gegevensopslag, kunt u de optionele stap voor het kopiëren uitvoeren om de extractiefase te versnellen. De voorkopieerstap is het meest effectief voor de eerste volledige extractie en inname. Zie [ Behandelend Grote Inhoudsbewaarplaatsen van de Inhoud ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md) voor meer details.

1. Selecteer een migratie die van de **tovenaar van de Overdracht van de Inhoud** wordt geplaatst en klik **trekken** om extractie te beginnen.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam12.png)

   >[!TIP]
   >Een opname kan nu automatisch worden gepland om onmiddellijk te beginnen nadat een extractie is gelukt. Zie [ Ingesterend Inhoud in Doel ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md) voor meer informatie.

   >[!IMPORTANT]
   >
   >Zorg ervoor dat de sleutel van de Extractie geldig is en niet dichtbij zijn vervaldatum is. Als deze bijna verlopen is, kunt u de Extractietoets vernieuwen door de migratieset te selecteren en op Eigenschappen te klikken. Klik **Vernieuwen**. Dit neemt u aan Cloud Acceleration Manager waar u **Sleutel van de Extractie van het Extractie van het Exemplaar** kunt klikken. Telkens als u **Sleutel van de Extractie van het Extractie van het Exemplaar** klikt, wordt een nieuwe sleutel van de Uitwinning geproduceerd die 14 dagen van de tijd van verwezenlijking geldig is.
   >![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam13.png)

1. Hiermee wordt het dialoogvenster Extractie weergegeven. Klik **Extraheren** om de extractiefase te beginnen.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam14c.png)

   >[!NOTE]
   >U kunt optioneel de container overschrijven tijdens de extractiefase. Als **staging container** wordt onbruikbaar gemaakt overschrijven, kan het extracties voor verdere migraties versnellen waar de inhoudspaden of versiemontages omvatten niet zijn veranderd. Nochtans, als de inhoudspaden of versiemontages omvatten zijn veranderd, dan **zou de staging container** moeten worden toegelaten.

1. Het **gebied van de Uitwinning** toont nu de **RUNNING** status om erop te wijzen dat de extractie lopend is.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam15.png)

   U kunt **Voortgang van de Mening** klikken om een korrelige mening van de aan de gang zijnde extractie te krijgen.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam16.png)

   U kunt de vooruitgang van de Fase van de Uitwinning van Cloud Acceleration Manager ook controleren door de pagina van de Overdracht van de Inhoud te bezoeken, en het meer in detail te zien door **te klikken..** > **de details van de Mening**.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam17.png)

1. Wanneer de Uitwinning wordt voltooid, herzie de andere kolommen zoals **Source** en **Wegen** voor details van de geplaatste migratie die u bevolkte. Het klikken **..** > **Details van de Mening** om details, met inbegrip van de duur van elke stap van de extractie te zien. Dit dialoogvenster weergeven tijdens het uitpakken, zodat u kunt zien hoe de stappen worden uitgevoerd.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam18b.png)


## Extractie bovenaan {#top-up-extraction-process}

De Content Transfer-tool heeft een functie die ondersteuning biedt voor differentiële aanvulling van content. Hierbij worden alleen die wijzigingen overgedragen die zijn aangebracht sinds de vorige activiteit voor contentoverdracht.

>[!NOTE]
>Na de eerste overdracht van inhoud wordt aanbevolen regelmatig differentiële toevoegingen toe te passen om de periode waarin de inhoud wordt vastgezet voor de uiteindelijke differentiële overdracht van inhoud te verkorten voordat deze live gaat met de Cloud Service. Als u de stap voor het vooraf kopiëren hebt gebruikt voor de eerste volledige extractie, kunt u de voorkopie voor volgende aanvullende extracties overslaan (als de ingestelde grootte voor de bovenste migratie kleiner is dan 200 GB). De reden is dat het tijd kan toevoegen aan het hele proces.
>Het is ook van essentieel belang dat de inhoudstructuur van bestaande inhoud niet wordt gewijzigd vanaf het moment dat de eerste extractie wordt uitgevoerd tot het moment dat de aanvullende extractie wordt uitgevoerd. Top-ups kunnen niet worden uitgevoerd op inhoud waarvan de structuur is gewijzigd sinds de eerste extractie. Zorg ervoor dat u dit tijdens het migratieproces beperkt.

Als het extractieproces is voltooid, kunt u delta-inhoud overbrengen met behulp van de extractiemethode top-up.

Voer de onderstaande stappen uit:

1. Navigeer aan de **tovenaar van de Overdracht van de Inhoud** en selecteer de migratie plaatste waarvoor u de top-up extractie wilt uitvoeren. Klik op **Extract** om de extractie te starten.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam19.png)

1. De **Vastgestelde extractie van de Migratie** vertoningen van de dialoogdoos. Klik **Extraheren**.

   >[!IMPORTANT]
   >Zorg dat de optie **Overwrite staging container during extraction** (voor het overschrijven van de stagingcontainer tijdens de extractie) is uitgeschakeld.
   >![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam20.png)


## Volgende functies {#whats-next}

Nadat u het Uitpakken van Inhoud van Source in het Hulpmiddel van de Overdracht van de Inhoud hebt geleerd, bent u nu bereid om het Proces van de Ingestie in het Hulpmiddel van de Overdracht van de Inhoud te leren. Zie [ Ingesterend Inhoud in Doel ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md) waar u kunt leren hoe te om uw migratie in te nemen die van het Hulpmiddel van de Overdracht van de Inhoud wordt geplaatst.
