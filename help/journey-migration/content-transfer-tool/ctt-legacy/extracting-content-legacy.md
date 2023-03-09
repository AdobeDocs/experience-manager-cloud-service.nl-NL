---
title: Inhoud uit bron extraheren (verouderd)
description: Inhoud uit bron extraheren
hide: true
hidefromtoc: true
exl-id: 9f43356c-ba51-48bc-97f5-f1f5db81e7f3
source-git-commit: 3c8035e4db5729f58bae29136a32a0b9944d6a2f
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 33%

---

# Inhoud uit bron extraheren (verouderd) {#extracting-content}

## Extractieproces in gereedschap voor inhoudsoverdracht {#extraction-process}

Voer de onderstaande stappen uit om uw migratieset te extraheren uit de Content Transfer-tool:
>[!NOTE]
>Als Amazon S3 of Azure Data Store wordt gebruikt als het type gegevensopslag, kunt u de optionele stap voor het kopiëren uitvoeren om de extractiefase aanzienlijk te versnellen. Om dit te doen, moet u vormen en `azcopy.config` bestand voordat extractie wordt uitgevoerd. Zie [Afhandeling van grote opslagplaatsen voor inhoud](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en) voor meer informatie .

>[!IMPORTANT]
>Voer het gereedschap Toewijzing gebruiker uit voordat u inhoud uit de bron extraheert. Zie [Het gereedschap Toewijzing gebruiker gebruiken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/legacy-user-mapping-tool/using-user-mapping-tool-legacy.html?lang=en) voor meer informatie .

1. Een migratieset selecteren vanuit **Inhoud overbrengen** wizard en klik op **Extraheren** om de extractie te starten.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/extraction-01.png)

1. De **Extractie van migratieset** wordt weergegeven en klikt u op **Extraheren** om de extractiefase te starten.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/extraction-02.png)

   >[!NOTE]
   >Tijdens de extractiefase kunt u optioneel de container overschrijven.

   >[!IMPORTANT]
   >Als de gebruikerstoewijzing niet is uitgevoerd op deze migratieset voordat u inhoud uit de bron extraheert, wordt een waarschuwing weergegeven met de melding dat de stap Gebruikerstoewijzing in behandeling is, zoals in de onderstaande afbeelding wordt getoond. Selecteren **Kaartgebruikers** om het gereedschap Toewijzing gebruiker uit te voeren.
   >![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/user-mapping-extract.png)

1. De **Extractie** wordt nu het veld weergegeven **UITVOEREN** status om aan te geven dat de extractie wordt uitgevoerd.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/extraction-03.png)

   Zodra de extractie is voltooid, wordt de status van de migratieset bijgewerkt naar **FINISHED** en wordt een *effen groen* wolkpictogram weergegeven onder het veld **INFO**.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/extraction-04.png)

   >[!IMPORTANT]
   >De interface heeft een functie voor automatisch opnieuw laden waarmee de **Inhoud overbrengen** elke 30 seconden.
   >Bij het starten van de extractiefase wordt een schrijfvergrendeling geactiveerd. Deze wordt na *60 seconden* weer vrijgegeven. Als u een extractie stopt, moet u dus eerst een minuut wachten tot de vergrendeling is gedeactiveerd voordat u opnieuw een extractie start.

## Extractie aanvullen {#top-up-extraction-process}

De Content Transfer-tool heeft een functie die ondersteuning biedt voor differentiële aanvulling van content. Hierbij worden alleen die wijzigingen overgedragen die zijn aangebracht sinds de vorige activiteit voor contentoverdracht.

>[!NOTE]
>Na de eerste overdracht van content wordt het aangeraden om regelmatig differentiële aanvullingen van content uit te voeren. Zo houdt u de periode waarin content wordt &#39;bevroren&#39; voor de uiteindelijke differentiële contentoverdracht zo kort mogelijk, voordat u live gaat op Cloud Service.
>Zorg er ook voor dat de inhoudstructuur van bestaande inhoud niet wordt gewijzigd vanaf het moment dat de eerste extractie wordt uitgevoerd tot wanneer de extractie van de opvultoepassing wordt uitgevoerd. Top-ups kunnen niet worden uitgevoerd op inhoud waarvan de structuur is gewijzigd sinds de eerste extractie. Zorg ervoor dat u dit tijdens het migratieproces beperkt.

Als het extractieproces is voltooid, kunt u deltacontent overdragen via de extractiemethode voor aanvullen.

Voer de onderstaande stappen uit:

1. Ga naar de **Inhoud overbrengen** en selecteert u de migratieset waarvoor u de extractie bovenaan wilt uitvoeren. Klik op **Extract** om de extractie te starten.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/extraction-05.png)

1. De **Extractie van migratieset** wordt weergegeven. Klikken op **Extraheren**.

   >[!IMPORTANT]
   >Zorg dat de optie **Overwrite staging container during extraction** (voor het overschrijven van de stagingcontainer tijdens de extractie) is uitgeschakeld.
   >![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/extraction-06.png)


## Volgende functies {#whats-next}

Nadat u over &quot;het Uitpakken van Inhoud van Bron&quot;in het Hulpmiddel van de Overdracht van de Inhoud hebt geleerd, bent u nu bereid om het Proces van de Ingestie in het Hulpmiddel van de Overdracht van de Inhoud te leren. Zie [Inhoud in doel invoegen](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md) om te leren hoe u uw migratieset kunt opnemen via het gereedschap Inhoud overbrengen.
