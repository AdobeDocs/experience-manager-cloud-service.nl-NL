---
title: Inhoud uit bron extraheren
description: Leer hoe u inhoud van een Adobe Experience Manager-broninstantie (AEM) extraheert om deze later naar een Cloud Service-AEM over te brengen.
exl-id: c5c08c4e-d5c3-4a66-873e-96986e094fd3
feature: Migration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 9%

---

# Inhoud uit bron extraheren {#extracting-content}

## Extractieproces in gereedschap voor inhoudsoverdracht {#extraction-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_extraction"
>title="Inhoud extraheren"
>abstract="Extractie heeft betrekking op het extraheren van inhoud van de Adobe Experience Manager-instantie (AEM) van de bron naar een tijdelijk gebied dat migratieset wordt genoemd. Een migratieset is een gebied van de wolkenopslag dat door Adobe wordt verstrekt om de overgebracht inhoud tussen de bron AEM instantie en de AEM van de Cloud Service tijdelijk op te slaan."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html#top-up-extraction-process" text="Extractie naar boven"


Voer de onderstaande stappen uit om uw migratieset te extraheren uit de Content Transfer-tool:

>[!NOTE]
>Als Amazon S3, Azure Data Store of File Data Store wordt gebruikt als het type gegevensopslag, kunt u de optionele stap voor het kopiëren uitvoeren om de extractiefase te versnellen. De voorkopieerstap is het meest effectief voor de eerste volledige extractie en inname. Zie [Afhandeling van grote opslagplaatsen voor inhoud](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md) voor meer informatie .

1. Selecteer een migratieset in het menu **Inhoud overbrengen** wizard en klik op **Extraheren** om de extractie te starten.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam12.png)

   >[!TIP]
   >Een opname kan nu automatisch worden gepland om onmiddellijk te beginnen nadat een extractie is gelukt. Zie [Inhoud in doel invoegen](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md) voor meer informatie .

   >[!IMPORTANT]
   >
   >Zorg ervoor dat de sleutel van de Extractie geldig is en niet dichtbij zijn vervaldatum is. Als deze bijna verlopen is, kunt u de Extractietoets vernieuwen door de migratieset te selecteren en op Eigenschappen te klikken. Klikken **Vernieuwen**. Hiermee gaat u naar Cloud Acceleration Manager waar u kunt klikken **Extractietoets kopiëren**. Elke keer dat u klikt **Extractietoets kopiëren**Er wordt een nieuwe extractiesleutel gegenereerd die 14 dagen geldig is vanaf het moment waarop deze is gemaakt.
   >![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam13.png)

1. Hiermee wordt het dialoogvenster Extractie weergegeven. Klikken **Extraheren** om de extractiefase te starten.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam14b.png)

   >[!NOTE]
   >U kunt optioneel de container overschrijven tijdens de extractiefase. Indien **Stapelcontainer overschrijven** is uitgeschakeld, kunt u extracties versnellen voor volgende migraties waarbij de paden naar de inhoud of de instellingen van versies niet zijn gewijzigd. Als de instellingen voor de inhoudspaden of de include-versies echter zijn gewijzigd, **Stapelcontainer overschrijven** moet zijn ingeschakeld.

1. De **Extractie** wordt nu het veld weergegeven **UITVOEREN** status om aan te geven dat de extractie wordt uitgevoerd.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam15.png)

   U kunt op **Voortgang van weergave** om een korrelig beeld van de lopende extractie te krijgen.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam16.png)

   U kunt de voortgang van de extractiefase ook controleren vanuit Cloud Acceleration Manager door naar de pagina Content Transfer te gaan en deze voor meer informatie te bekijken door op **...** > **Details weergeven**.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam17.png)

1. Wanneer het Uittrekken wordt voltooid, herzie de andere kolommen als **Bron** en **Paden** voor meer informatie over de migratieset die u hebt gevuld. Klikken **...** > **Details weergeven** nadere gegevens, met inbegrip van de duur van elke extractiestap. Dit dialoogvenster weergeven tijdens het uitpakken, zodat u kunt zien hoe de stappen worden uitgevoerd.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam18b.png)


## Extractie bovenaan {#top-up-extraction-process}

De Content Transfer-tool heeft een functie die ondersteuning biedt voor differentiële aanvulling van content. Hierbij worden alleen die wijzigingen overgedragen die zijn aangebracht sinds de vorige activiteit voor contentoverdracht.

>[!NOTE]
>Na de eerste overdracht van inhoud wordt aanbevolen regelmatig differentiële toevoegingen toe te passen om de periode waarin de inhoud wordt vastgezet voor de uiteindelijke differentiële overdracht van inhoud te verkorten voordat deze live gaat met de Cloud Service. Als u de stap voor het vooraf kopiëren hebt gebruikt voor de eerste volledige extractie, kunt u de voorkopie voor volgende aanvullende extracties overslaan (als de ingestelde grootte voor de bovenste migratie kleiner is dan 200 GB). De reden is dat het tijd kan toevoegen aan het hele proces.
>Het is ook van essentieel belang dat de inhoudstructuur van bestaande inhoud niet wordt gewijzigd vanaf het moment dat de eerste extractie wordt uitgevoerd tot het moment dat de aanvullende extractie wordt uitgevoerd. Top-ups kunnen niet worden uitgevoerd op inhoud waarvan de structuur is gewijzigd sinds de eerste extractie. Zorg ervoor dat u dit tijdens het migratieproces beperkt.

Als het extractieproces is voltooid, kunt u delta-inhoud overbrengen met behulp van de extractiemethode top-up.

Voer de onderstaande stappen uit:

1. Ga naar de **Inhoud overbrengen** en selecteert u de migratieset waarvoor u de extractie bovenaan wilt uitvoeren. Klik op **Extract** om de extractie te starten.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam19.png)

1. De **Extractie van migratieset** wordt weergegeven. Klikken **Extraheren**.

   >[!IMPORTANT]
   >Zorg dat de optie **Overwrite staging container during extraction** (voor het overschrijven van de stagingcontainer tijdens de extractie) is uitgeschakeld.
   >![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam20.png)


## Volgende functies {#whats-next}

Nadat u het Uithalen van Inhoud van Bron in het Hulpmiddel van de Overdracht van de Inhoud hebt geleerd, bent u nu bereid om het Proces van de Ingestie in het Hulpmiddel van de Overdracht van de Inhoud te leren. Zie [Inhoud in doel invoegen](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md) waar u kunt leren hoe u uw migratieset kunt opnemen via het gereedschap Inhoud overbrengen.
