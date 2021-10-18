---
title: Inhoud uit bron extraheren in gereedschap voor inhoudsoverdracht
description: Inhoud uit bron extraheren in gereedschap voor inhoudsoverdracht
source-git-commit: 5ae76fbc3926f5e2cd7ed5597a9d4521adc9ddb1
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Inhoud uit bron extraheren in gereedschap voor inhoudsoverdracht {#extracting-content}

## Extractieproces in gereedschap voor inhoudsoverdracht {#extraction-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_extraction"
>title="Inhoud extraheren"
>abstract="Extractie heeft betrekking op het extraheren van inhoud van de bron AEM instantie naar een tijdelijk gebied dat migratieset wordt genoemd. Een migratieset is een opslaggebied op de cloud dat door Adobe wordt geleverd om overgedragen content tijdelijk op te slaan tussen de AEM-broninstantie en de AEM Cloud Service-instantie."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#top-up-extraction-process" text="Extractie naar boven"

Voer de onderstaande stappen uit om uw migratieset te extraheren uit de Content Transfer-tool:
>[!NOTE]
>Als Amazon S3 of Azure Data Store wordt gebruikt als het type gegevensopslag, kunt u de optionele stap voor het kopiëren uitvoeren om de extractiefase aanzienlijk te versnellen. Hiervoor moet u een `azcopy.config`-bestand configureren voordat extractie wordt uitgevoerd. Zie [Grote opslagplaatsen voor inhoud verwerken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en) voor meer informatie.

1. Selecteer een migratieset op de pagina *Overview* en klik op **Extract** om de extractie te starten. Het dialoogvenster **Extractie van migratieset** wordt weergegeven en u klikt op **Extraheren** om de extractiefase te starten.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets/06-content-extraction.png)

   >[!NOTE]
   >U kunt de stagingcontainer tijdens de extractiefase overschrijven indien u dat wilt.


1. In het veld **EXTRACTION** wordt nu de status **RUNNING** weergegeven om aan te geven dat de extractie bezig is.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets/07-extraction-job-running.png)

   Zodra de extractie is voltooid, wordt de status van de migratieset bijgewerkt naar **FINISHED** en wordt een *effen groen* wolkpictogram weergegeven onder het veld **INFO**.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets/10-extraction-complete.png)

   >[!NOTE]
   >De interface heeft een functie voor automatisch opnieuw laden waarmee de overzichtspagina elke 30 seconden opnieuw wordt geladen.
   >Bij het starten van de extractiefase wordt een schrijfvergrendeling geactiveerd. Deze wordt na *60 seconden* weer vrijgegeven. Als u een extractie stopt, moet u dus eerst een minuut wachten tot de vergrendeling is gedeactiveerd voordat u opnieuw een extractie start.

## Extractie aanvullen {#top-up-extraction-process}

De Content Transfer-tool heeft een functie die ondersteuning biedt voor differentiële aanvulling van content. Hierbij worden alleen die wijzigingen overgedragen die zijn aangebracht sinds de vorige activiteit voor contentoverdracht.

>[!NOTE]
>Na de eerste overdracht van content wordt het aangeraden om regelmatig differentiële aanvullingen van content uit te voeren. Zo houdt u de periode waarin content wordt &#39;bevroren&#39; voor de uiteindelijke differentiële contentoverdracht zo kort mogelijk, voordat u live gaat op Cloud Service.
>Bovendien is het van essentieel belang dat de inhoudstructuur van bestaande inhoud niet wordt gewijzigd vanaf het moment dat de eerste extractie wordt uitgevoerd tot het moment dat de aanvullende extractie wordt uitgevoerd. Top-ups kunnen niet worden uitgevoerd op inhoud waarvan de structuur is gewijzigd sinds de eerste extractie. Zorg ervoor dat u dit tijdens het migratieproces beperkt.

Als het extractieproces is voltooid, kunt u deltacontent overdragen via de extractiemethode voor aanvullen. Voer de onderstaande stappen uit:

1. Ga naar de pagina *Overview* en selecteer de migratieset waarvoor u de aanvullingsextractie wilt uitvoeren. Klik op **Extract** om de extractie te starten. Het dialoogvenster voor de **extractie van de migratieset** wordt weergegeven.

   >[!IMPORTANT]
   >
   >Zorg dat de optie **Overwrite staging container during extraction** (voor het overschrijven van de stagingcontainer tijdens de extractie) is uitgeschakeld.
   >
   >![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets/11-topup-extraction.png)

## Volgende functies {#whats-next}

Nadat u de opdracht Inhoud uit bron extraheren hebt geleerd in het gereedschap Inhoud overbrengen, kunt u nu leren hoe u het opmaakproces in het gereedschap Inhoud overbrengen start. Zie [Inhoud invoegen in doel in gereedschap Inhoud overbrengen](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool/ingesting-content.md) voor informatie over het opnemen van de migratieset met het gereedschap Inhoud overbrengen.
