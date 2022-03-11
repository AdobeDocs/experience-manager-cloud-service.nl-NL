---
title: Inhoud in doel invoegen
description: Inhoud in doel invoegen
exl-id: d8c81152-f05c-46a9-8dd6-842e5232b45e
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '527'
ht-degree: 29%

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
>U kunt de optionele pre-copy stap uitvoeren om de innamefase aanzienlijk te versnellen. Zie [Inschakelen met AzCopy](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en#ingesting-azcopy) voor meer informatie .

1. Een migratieset selecteren vanuit **Inhoud overbrengen** pagina en klik op **Ingest** om te beginnen met inslikken.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-01.png)

1. Het dialoogvenster voor het **opnemen van de migratieset** wordt weergegeven. Inhoud kan tegelijkertijd worden ingevoerd in een instantie Auteur of Publiceren. Selecteer de instantie waaraan u inhoud wilt toevoegen. Klikken op **Ingest** om de inname fase te starten.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-02.png)

   >[!IMPORTANT]
   >Als het opnemen met pre-copy wordt gebruikt (voor S3 of Azure Data Store), wordt het geadviseerd om de opname van de Auteur eerst alleen in werking te stellen. Hierdoor wordt de opname voor publiceren sneller wanneer deze later wordt uitgevoerd.

   >[!IMPORTANT]
   >Wanneer de **Bestaande inhoud vegen op Cloud-instantie voordat deze wordt ingesloten** is ingeschakeld, wordt de gehele bestaande opslagplaats verwijderd en wordt een nieuwe opslagplaats gemaakt waarin inhoud kan worden ingevoerd. Dit betekent dat alle instellingen, inclusief de machtigingen voor de Cloud Service van het doel, opnieuw worden ingesteld. Dit geldt ook voor een beheerder die is toegevoegd aan de **beheerders** groep.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-03.png)

   Klik bovendien op **Klantenservice** om een kaartje, zoals aangetoond in het hieronder cijfer te registreren.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-04.png)

   Zie ook: [Belangrijke overwegingen voor het gebruik van het gereedschap Inhoud overbrengen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=en#important-considerations) voor meer informatie.

1. Zodra de inname is voltooid, is de status onder **Inname door auteur** updates voor **VOLTOOID**.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-05.png)

## Opname aanvullen {#top-up-ingestion-process}

De Content Transfer-tool heeft een functie die ondersteuning biedt voor differentiële *aanvulling* van content. Hierbij worden alleen die wijzigingen overgedragen die zijn aangebracht sinds de vorige activiteit voor contentoverdracht.

>[!NOTE]
>Na de eerste overdracht van content wordt het aangeraden om regelmatig differentiële aanvullingen van content uit te voeren. Zo houdt u de periode waarin content wordt &#39;bevroren&#39; voor de uiteindelijke differentiële contentoverdracht zo kort mogelijk, voordat u live gaat op Cloud Service.

Als het opnameproces is voltooid, kunt u deltacontent gebruiken via de opnamemethode met aanvullen. Voer de onderstaande stappen uit:

1. Ga naar de **Inhoud overbrengen** en selecteert u de migratieset waarvoor u de bovenste opname wilt uitvoeren. Klik op **Ingest** om de opname te starten.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/topup-ingest1.png)


1. Het dialoogvenster voor het **opnemen van de migratieset** wordt weergegeven.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/topup-ingest2.png)

   >[!IMPORTANT]
   >U moet de opdracht **Bestaande inhoud vegen op Cloud-instantie voordat deze wordt ingesloten** gebruiken, om te voorkomen dat de bestaande inhoud uit de vorige insluitingsactiviteit wordt verwijderd. Klik bovendien op **Klantenservice** om een kaartje, zoals aangetoond in het voorafgaande cijfer te registreren.

## Volgende functies {#whats-next}

Als u Ingesterende inhoud hebt geleerd in Doel in het gereedschap Inhoud overbrengen, kunt u logbestanden weergeven na elke stap (extractie en opname) en op fouten zoeken. Zie [Logboeken voor een migratieset weergeven](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/viewing-logs.html?lang=en) voor meer informatie.
