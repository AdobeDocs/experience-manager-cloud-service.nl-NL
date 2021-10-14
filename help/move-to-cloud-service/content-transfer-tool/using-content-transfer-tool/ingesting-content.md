---
title: Inhoud in doel invoegen
description: Inhoud in doel invoegen
source-git-commit: 6a6fa69d2eb79e41c79a0916bfd6e34ecf490d34
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 28%

---


# Inhoud in doel invoegen {#ingesting-content}

## Ingestieproces in gereedschap Inhoud overbrengen {#ingestion-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion"
>title="Inktatie van inhoud"
>abstract="Ingestie verwijst naar het opnemen van inhoud van de migratie die is ingesteld in de Cloud Service-instantie van het doel. De Content Transfer-tool heeft een functie die ondersteuning biedt voor differentiële aanvulling van content. Hierbij worden alleen die wijzigingen overgedragen die zijn aangebracht sinds de vorige activiteit voor contentoverdracht."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#top-up-ingestion-process" text="Opname aanvullen"

Voer de onderstaande stappen uit om uw migratieset uit de Content Transfer-tool op te nemen:
>[!NOTE]
>Als Amazon S3 of Azure Data Store wordt gebruikt als het type gegevensopslag, kunt u de optionele pre-copy stap uitvoeren om de innamefase aanzienlijk te versnellen. Raadpleeg [Ingesting met AzCopy](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en#ingesting-azcopy) voor meer informatie.

1. Selecteer een migratieset van **Content Transfer** pagina en klik **Ingest** om opname te beginnen.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ingestion-01.png)

1. Het dialoogvenster voor het **opnemen van de migratieset** wordt weergegeven. Inhoud kan tegelijkertijd worden ingevoerd in een instantie Auteur of Publiceren. Selecteer de instantie waaraan u inhoud wilt toevoegen. Klik op **Ingest** om de innamefase te starten.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ingestion-02.png)

   >[!IMPORTANT]
   >Als het opnemen met pre-copy wordt gebruikt (voor S3 of Azure Data Store), wordt het geadviseerd om de opname van de Auteur eerst alleen in werking te stellen. Hierdoor wordt de opname voor publiceren sneller wanneer deze later wordt uitgevoerd.

   >[!IMPORTANT]
   >Wanneer de optie **Bestaande inhoud op een Cloud-instantie vegen voordat de optie** wordt ingesloten, wordt de gehele bestaande opslagruimte verwijderd en wordt een nieuwe opslagplaats gemaakt waarin inhoud wordt opgenomen. Dit betekent dat alle instellingen, inclusief de machtigingen voor de Cloud Service van het doel, opnieuw worden ingesteld. Dit geldt ook voor een beheerder die wordt toegevoegd aan de groep **beheerders**.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ingestion-03.png)

   Klik bovendien op **Klantenservice** om een ticket te registreren, zoals in de onderstaande afbeelding wordt getoond.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ingestion-04.png)

   Ook, verwijs naar [Belangrijke Overwegingen voor het Gebruiken van het Hulpmiddel van de Overdracht van de Inhoud](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=en#important-considerations) om meer te leren.

1. Wanneer de inname is voltooid, wordt de status onder **Inname door auteur** bijgewerkt naar **FINISHED**.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ingestion-05.png)

## Opname aanvullen {#top-up-ingestion-process}

De Content Transfer-tool heeft een functie die ondersteuning biedt voor differentiële *aanvulling* van content. Hierbij worden alleen die wijzigingen overgedragen die zijn aangebracht sinds de vorige activiteit voor contentoverdracht.

>[!NOTE]
>Na de eerste overdracht van content wordt het aangeraden om regelmatig differentiële aanvullingen van content uit te voeren. Zo houdt u de periode waarin content wordt &#39;bevroren&#39; voor de uiteindelijke differentiële contentoverdracht zo kort mogelijk, voordat u live gaat op Cloud Service.

Als het opnameproces is voltooid, kunt u deltacontent gebruiken via de opnamemethode met aanvullen. Voer de onderstaande stappen uit:

1. Navigeer naar de wizard **Inhoud overbrengen** en selecteer de migratieset waarvoor u de bovenste opname wilt uitvoeren. Klik op **Ingest** om de opname te starten.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/topup-ingest1.png)


1. Het dialoogvenster voor het **opnemen van de migratieset** wordt weergegeven.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/topup-ingest2.png)

   >[!IMPORTANT]
   >Schakel de optie **Bestaande inhoud vegen op een Cloud-instantie uit voordat u** inneemt om te voorkomen dat de bestaande inhoud wordt verwijderd uit de vorige insluitingsactiviteit. Bovendien, klik op **de Zorg van de Klant** om een kaartje, zoals aangetoond in het voorafgaande cijfer te registreren.

## Volgende functies {#whats-next}

Als u Ingesterende inhoud hebt geleerd in Doel in het gereedschap Inhoud overbrengen, kunt u logbestanden weergeven na elke stap (extractie en opname) en op fouten zoeken. Zie [Logbestanden voor een migratieset weergeven](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/viewing-logs.html?lang=en) voor meer informatie.
