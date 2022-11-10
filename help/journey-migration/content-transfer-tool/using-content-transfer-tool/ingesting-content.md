---
title: Inhoud in doel invoegen
description: Inhoud in doel invoegen
exl-id: d8c81152-f05c-46a9-8dd6-842e5232b45e
source-git-commit: e8b4fe047c9656aa592fc851279dc6a189144023
workflow-type: tm+mt
source-wordcount: '916'
ht-degree: 12%

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
>U kunt de optionele pre-copy stap uitvoeren om de innamefase aanzienlijk te versnellen. De pre-copy stap is het meest effectief voor de eerste volledige extractie en inname. Zie [Inschakelen met AzCopy](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#ingesting-azcopy) voor meer informatie .

1. Ga naar Cloud Acceleration Manager. Klik op uw projectkaart en klik op de kaart van de Overdracht van de Inhoud. Navigeren naar **Ingestietaken** en klik op **Nieuwe inname**

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-01.png)

1. Geef de vereiste informatie op om een nieuwe opname te maken.

   * Selecteer de migratieset die u net als bron hebt geëxtraheerd
   * Selecteer de doelomgeving. Dit is waar de inhoud van de migratieset wordt opgenomen. Selecteer de laag. (Auteur/Publicatie).

   >[!NOTE]
   >
   >Als de bron Auteur was, wordt het geadviseerd om het in de rij van de Auteur op het doel op te nemen. Als de bron Publiceren was, zou het doel ook Publiceren moeten zijn.

   >[!NOTE]
   >
   >U kunt de optionele pre-copy stap uitvoeren om de innamefase aanzienlijk te versnellen. Zie [Inschakelen met AzCopy](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#ingesting-azcopy) voor meer informatie .
   > 
   >Als het opnemen met pre-copy wordt gebruikt (voor S3 of Azure Data Store), wordt het geadviseerd om de opname van de Auteur eerst alleen in werking te stellen. Hierdoor wordt de opname voor publiceren sneller wanneer deze later wordt uitgevoerd.

   >[!IMPORTANT]
   >
   >U kunt een opname alleen afschoppen in de doelomgeving als u tot de lokale omgeving behoort **AEM** groep op de de auteursdienst van de bestemmingsCloud Service. Als u geen inname kunt starten, raadpleegt u [Kan inname niet starten](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#unable-to-start-ingestion) voor meer informatie .

   >[!IMPORTANT]
   >
   >Als de instelling **Sluitereffect** wordt ingeschakeld voordat de inhoud wordt ingevoerd, wordt de gehele bestaande opslagplaats verwijderd en wordt een nieuwe opslagplaats gemaakt waarin inhoud wordt ingevoerd. Dit betekent dat alle instellingen, inclusief de machtigingen voor de Cloud Service van het doel, opnieuw worden ingesteld. Dit geldt ook voor een beheerder die is toegevoegd aan de **beheerders** groep. U zult aan de beheerdersgroep opnieuw moeten worden toegevoegd om een opname te beginnen.

1. Klikken op **Ingest**

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam22.png)

1. U kunt dan de fase van de Opname van de de lijstmening van Banen van de Opname controleren en het de actiemenu gebruiken van de opname om het logboek te bekijken aangezien de opname vordert.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam23.png)

1. Nadat de inname is voltooid, klikt u op de knop i) in de rechterbovenhoek van het scherm voor meer informatie over de innametaak.

<!-- Alexandru: hiding temporarily, until it's reviewed 

1. The **Migration Set ingestion** dialog box displays. Content can be ingested to either Author instance or Publish instance at a time. Select the instance to ingest content to. Click on **Ingest** to start the ingestion phase. 

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-02.png)

   >[!IMPORTANT]
   >If ingesting with pre-copy is used (for S3 or Azure Data Store), it is recommended to run Author ingestion first alone. This will speed up the Publish ingestion when it is run later. 

   >[!IMPORTANT]
   >When the **Wipe existing content on Cloud instance before ingestion** option is enabled, it deletes the entire existing repository and creates a new repository to ingest content into. This means that it resets all settings including permissions on the target Cloud Service instance. This is also true for an admin user added to the **administrators** group.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-03.png)

   Additionally, click on **Customer Care** to log a ticket, as shown in the figure below. 

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-04.png)
   
   Also, refer to [Important Considerations for Using Content Transfer Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=en#important-considerations) to learn more.

1. Once the ingestion is complete, the status under **Author ingestion** updates to **FINISHED**.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-05.png) -->

## Opname aanvullen {#top-up-ingestion-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion_topup" title="Top Up Ingestion"
>abstract="Gebruik de functie Boven om gewijzigde inhoud te verplaatsen sinds de vorige activiteit voor inhoudsoverdracht. Na voltooiing van Ingestie, controleer de logboeken om het even welke fout/waarschuwingen. Eventuele fouten moeten onmiddellijk worden opgelost door de gemelde problemen te verhelpen of door contact op te nemen met de klantenservice van Adobe."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/viewing-logs.html?lang=en" text="Logbestanden weergeven"

De Content Transfer-tool heeft een functie die ondersteuning biedt voor differentiële *aanvulling* van content. Hierbij worden alleen die wijzigingen overgedragen die zijn aangebracht sinds de vorige activiteit voor contentoverdracht.

>[!NOTE]
>Na de eerste overdracht van content wordt het aangeraden om regelmatig differentiële aanvullingen van content uit te voeren. Zo houdt u de periode waarin content wordt &#39;bevroren&#39; voor de uiteindelijke differentiële contentoverdracht zo kort mogelijk, voordat u live gaat op Cloud Service. Als u de pre-exemplaarstap voor de eerste volledige opname hebt gebruikt, kunt u pre-exemplaar voor verdere bovenop-up ingezien overslaan (als de top-up migratie vastgestelde grootte minder dan 200GB) omdat het tijd aan het volledige proces kan toevoegen.

Als het inslikken is voltooid, moet u een [Extractie bovenaan](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process) en gebruikt u vervolgens de methode van de bovenste opname.

U kunt dit doen door een nieuwe Ingestietaak te creëren en ervoor te zorgen dat **Sluitereffect** is uitgeschakeld tijdens de Ingestiefase, zoals hieronder wordt getoond:

![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam24.png)

## Problemen oplossen {#troubleshooting}

### CAM Kan migratietoken niet ophalen {#cam-unable-to-retrieve-the-migration-token}

De automatische herwinning van het migratietoken kan om verschillende redenen ontbreken, met inbegrip van u [een IP-lijst van gewenste personen instellen via Cloud Manager](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) in de omgeving van de doelCloud Service.  In dergelijke scenario&#39;s zult u de volgende dialoog zien wanneer u probeert om een opname te beginnen:

![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/troubleshooting-token.png)

U moet het migratietoken handmatig ophalen door op de koppeling &#39;Token ophalen&#39; in het dialoogvenster te klikken. Hiermee wordt een ander tabblad geopend waarin het token wordt weergegeven. U kunt het token vervolgens kopiëren en plakken in het dialoogvenster **Invoer van migratietoken** veld. Nu moet je de inname kunnen starten.

>[!NOTE]
>
>Het token is beschikbaar voor gebruikers die tot de lokale server behoren **AEM** groep op de de auteursdienst van de bestemmingsCloud Service.

### Kan inname niet starten {#unable-to-start-ingestion}

U kunt een opname alleen afschoppen in de doelomgeving als u tot de lokale omgeving behoort **AEM** groep op de de auteursdienst van de bestemmingsCloud Service. Als u niet tot de groep van AEM beheerders behoort, zult u een fout zoals hieronder getoond zien wanneer u probeert om een opname te beginnen. U kunt de beheerder vragen om u toe te voegen aan de lokale **AEM** of vraag om de token zelf, die u vervolgens in de **Invoer van migratietoken** veld.

![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/error_nonadmin_ingestion.png)

## Volgende functies {#whats-next}

Nadat u Ingesting Content in Target hebt voltooid, kunt u logboeken van elke stap (extractie en opname) weergeven en op fouten zoeken. Zie [Logboeken voor een migratieset weergeven](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/viewing-logs.html?lang=en) voor meer informatie.
