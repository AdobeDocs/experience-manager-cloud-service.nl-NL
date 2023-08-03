---
title: Inhoud in doel invoegen
description: Leer hoe u met het gereedschap Inhoud overbrengen inhoud uit een migratieset kunt toevoegen aan een Cloud Service-instantie.
exl-id: d8c81152-f05c-46a9-8dd6-842e5232b45e
source-git-commit: f7ffe727ecc7f1331c1c72229a5d7f940070c011
workflow-type: tm+mt
source-wordcount: '1941'
ht-degree: 6%

---

# Inhoud in doel invoegen {#ingesting-content}

## Ingestieproces in gereedschap Inhoud overbrengen {#ingestion-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion"
>title="Inktatie van inhoud"
>abstract="Ingestie verwijst naar het opnemen van inhoud van de migratie die is ingesteld in de Cloud Service-instantie van het doel. De Content Transfer-tool heeft een functie die ondersteuning biedt voor differentiële aanvulling van content. Hierbij worden alleen die wijzigingen overgedragen die zijn aangebracht sinds de vorige activiteit voor contentoverdracht."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html" text="Opname aanvullen"

Voer de onderstaande stappen uit om uw migratieset uit de Content Transfer-tool op te nemen:

>[!NOTE]
>Heb je een ondersteuningsticket voor deze inname onthouden? Zie [Belangrijke overwegingen voordat u het gereedschap Inhoud overbrengen gebruikt](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html#important-considerations) om die reden en om andere redenen kan de inname succesvol zijn .

1. Ga naar Cloud Acceleration Manager. Klik op de projectkaart en klik op de kaart voor inhoudsoverdracht. Navigeren naar **Ingestietaken** en klik op **Nieuwe inname**

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-01.png)

1. Controleer de innamecontrolelijst en zorg ervoor dat alle stappen zijn voltooid. Deze stappen zijn nodig om een succesvolle inname te waarborgen. Ga door naar de **Volgende** stap alleen als de checklist is voltooid.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/Ingestion-checklist.png)

1. Geef de vereiste informatie op om een opname te maken.

   * Selecteer de migratieset die de geëxtraheerde gegevens als bron bevat.
      * De Reeksen van de migratie zullen verlopen na een lange periode van inactiviteit, zodat wordt verwacht dat de inname vrij snel na de extractie plaatsvindt. Controleren [Vervaldatum migratieset](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/overview-content-transfer-tool.md#migration-set-expiry) voor meer informatie.
   * Selecteer de doelomgeving. In deze omgeving wordt de inhoud van de migratieset opgenomen. Selecteer de laag. (Auteur/Publicatie). Snelle ontwikkelomgevingen worden niet ondersteund.

   >[!NOTE]
   >De volgende opmerkingen zijn van toepassing op het opnemen van inhoud:
   > Als de bron Auteur was, wordt het geadviseerd om het in de rij van de Auteur op het doel op te nemen. Als de bron Publiceren was, zou het doel ook Publiceren moeten zijn.
   > Als de doellaag `Author`, wordt de auteurinstantie gesloten tijdens de lengte van de opname en niet beschikbaar voor gebruikers (bijvoorbeeld, auteurs of iedereen die onderhoud uitvoert). De reden is om het systeem te beschermen en om eventuele veranderingen te voorkomen die verloren zouden kunnen gaan of een innameconflict zouden kunnen veroorzaken. Zorg ervoor dat uw team zich hiervan bewust is. Houd er ook rekening mee dat de omgeving tijdens de opname door de auteur wordt genegeerd.
   > U kunt de optionele pre-copy stap uitvoeren om de innamefase aanzienlijk te versnellen. Zie [Inschakelen met AzCopy](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#ingesting-azcopy) voor meer informatie .
   > Als het opnemen met pre-copy wordt gebruikt (voor S3 of Azure Data Store), wordt het geadviseerd om de opname van de Auteur eerst alleen in werking te stellen. Als u dit doet, wordt de opname Publish sneller wanneer deze later wordt uitgevoerd.
   > De oplossingen steunen geen bestemming van de Milieu van de Snelle Ontwikkeling (RDE) en verschijnen niet als mogelijke bestemmingskeus, zelfs als de gebruiker toegang tot het heeft.

   >[!IMPORTANT]
   > De volgende belangrijke kennisgevingen zijn van toepassing op het opnemen van inhoud:
   > U kunt een opname aan het bestemmingsmilieu in werking stellen slechts als u tot lokaal behoort **AEM** groep op de de auteursdienst van de bestemmingsCloud Service. Als u geen inname kunt starten, zie [Kan inname niet starten](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#unable-to-start-ingestion) voor meer informatie .
   > Als de instelling **Sluitereffect** wordt ingeschakeld voordat de inhoud wordt ingevoerd, wordt de gehele bestaande opslagplaats verwijderd en wordt een opslagplaats gemaakt waarin u inhoud kunt invoeren. Dit werkschema betekent dat het alle montages met inbegrip van toestemmingen op de instantie van de doelCloud Service terugstelt. Dit opnieuw instellen geldt ook voor een beheerder die is toegevoegd aan de **beheerders** groep. U moet aan de beheerdersgroep worden gelezen om een opname te beginnen.

1. Klikken **Ingest**.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam22.png)

1. U kunt dan de fase van de Opname van de de lijstmening van Banen van de Opname controleren en het de actiemenu gebruiken van de opname om het logboek te bekijken aangezien de opname vordert.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam23.png)

1. Klik op de knop **i)** voor meer informatie over de innametaak. U kunt de duur van elke stap van de Ingestie zien wanneer het loopt of door te klikken **...** en klik vervolgens op **Duur weergeven**. Uit de informatie over de extractie blijkt ook dat men zich realiseert wat er wordt ingeslikt.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam23b.png)

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
   
   Also, see [Important Considerations for Using Content Transfer Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html#important-considerations) to learn more.

1. Once the ingestion is complete, the status under **Author ingestion** updates to **FINISHED**.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-05.png) -->

## Opname aanvullen {#top-up-ingestion-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion_topup"
>title="Opname aanvullen"
>abstract="Gebruik de functie top-up om gewijzigde inhoud te verplaatsen sinds de vorige activiteit van de inhoudsoverdracht. Na voltooiing van Ingestie, controleer de logboeken om het even welke fout/waarschuwingen. Eventuele fouten moeten onmiddellijk worden opgelost door de gemelde problemen te verhelpen of door contact op te nemen met de klantenservice van Adobe."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/viewing-logs.html" text="Logbestanden weergeven"

De Content Transfer-tool heeft een functie die ondersteuning biedt voor differentiële *aanvulling* van content. Hierbij worden alleen die wijzigingen overgedragen die zijn aangebracht sinds de vorige activiteit voor contentoverdracht.

>[!NOTE]
>Na de eerste overdracht van content wordt het aangeraden om regelmatig differentiële aanvullingen van content uit te voeren. Zo houdt u de periode waarin content wordt &#39;bevroren&#39; voor de uiteindelijke differentiële contentoverdracht zo kort mogelijk, voordat u live gaat op Cloud Service. Als u de pre-exemplaarstap voor de eerste volledige opname hebt gebruikt, kunt u pre-exemplaar voor verdere bovenop-up ingezien overslaan (als de top-up migratie vastgestelde grootte minder dan 200 GB is). De reden is dat het tijd kan toevoegen aan het hele proces.

Als u de delta-inhoud wilt innemen nadat het inslikken is voltooid, moet u een [Extractie bovenaan](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process)en gebruikt u vervolgens de methode voor het verhogen van de inname.

Begin met het maken van een Ingestietaak en zorg ervoor dat **Sluitereffect** is uitgeschakeld tijdens de Ingestiefase, zoals hieronder wordt getoond:

![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam24.png)

## Problemen oplossen {#troubleshooting}

### CAM Kan migratietoken niet ophalen {#cam-unable-to-retrieve-the-migration-token}

Het automatisch ophalen van het migratietoken kan om verschillende redenen mislukken, waaronder u [een IP-lijst van gewenste personen instellen via Cloud Manager](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) in de omgeving van de doelCloud Service. In dergelijke scenario&#39;s, ziet u de volgende dialoogdoos wanneer u probeert om een opname te beginnen:

![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/troubleshooting-token.png)

U kunt het migratietoken handmatig ophalen door op de koppeling Token ophalen in het dialoogvenster te klikken. Er wordt een ander tabblad geopend waarin het token wordt weergegeven. U kunt het token vervolgens kopiëren en plakken in het dialoogvenster **Invoer van migratietoken** veld. Nu moet je de inname kunnen starten.

>[!NOTE]
>
>De token is beschikbaar voor gebruikers die tot de lokale server behoren **AEM** groep op de de auteursdienst van de bestemmingsCloud Service.

### Kan inname niet starten {#unable-to-start-ingestion}

U kunt een opname aan het bestemmingsmilieu in werking stellen slechts als u tot lokaal behoort **AEM** groep op de de auteursdienst van de bestemmingsCloud Service. Als u niet tot de groep van AEM beheerders behoort, ziet u een fout zoals hieronder getoond wanneer u probeert om een opname te beginnen. U kunt de beheerder vragen om u toe te voegen aan de lokale **AEM** of vraag om de token zelf, die u vervolgens in de **Invoer van migratietoken** veld.

![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/error_nonadmin_ingestion.png)

### Kan de migratieservice niet bereiken {#unable-to-reach-migration-service}

Nadat een opname wordt gevraagd, kan een bericht als het volgende aan de gebruiker worden voorgesteld: &quot;De migratiedienst op het bestemmingsmilieu is onbereikbaar. Als dat het geval is, probeert u het later opnieuw of neemt u contact op met de Adobe-ondersteuning.&quot;

![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/error_cannot_reach_migser.png)

Dit bericht geeft aan dat de Cloud Acceleration Manager de migratieservice van de doelomgeving niet kan bereiken om de opname te starten. Dit kan om verschillende redenen gebeuren.

>[!NOTE]
> 
> Het veld &quot;Migratietoken&quot; wordt weergegeven omdat het ophalen van dat token in sommige gevallen niet is toegestaan. Door het handmatig aanbrengen van de injectie toe te staan, kan de gebruiker de opname snel starten, zonder extra hulp. Als het token is opgegeven en het bericht nog steeds wordt weergegeven, was het ophalen van het token niet het probleem.

* AEM as a Cloud Service handhaaft de milieustaat, en moet af en toe de migratiedienst opnieuw beginnen om diverse normale redenen. Als die dienst opnieuw begint, kan het niet worden bereikt, maar is uiteindelijk beschikbaar.
* Het is mogelijk dat een ander proces op de instantie wordt uitgevoerd. Bijvoorbeeld, als het Orchestrator van de Versie een update toepast, kan het systeem bezig zijn en de migratiedienst regelmatig niet beschikbaar. Daarom wordt het ten zeerste aanbevolen om updates tijdens een opname te pauzeren, en de mogelijkheid om het werkgebied of de productie-instantie te beschadigen.
* Als een [IP de Lijst van gewenste personen is toegepast](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) via Cloud Manager wordt het bereiken van de migratieservice door Cloud Acceleration Manager geblokkeerd. Een IP adres kan niet voor ingesties worden toegevoegd omdat zijn adres dynamisch is. Momenteel, is de enige oplossing de IP lijst van gewenste personen onbruikbaar te maken terwijl de opname loopt.
* Er kunnen andere redenen zijn die een onderzoek vereisen. Neem contact op met de klantenservice van Adobe als de opname nog steeds mislukt.

### Automatische updates via Release Orchestrator zijn nog steeds ingeschakeld

De Orchestrator van de versie houdt automatisch milieu-bijgewerkt door updates automatisch toe te passen. Als de update wordt geactiveerd wanneer een opname wordt uitgevoerd, kunnen er onvoorspelbare resultaten optreden, waaronder de beschadiging van de omgeving. Een goede reden om een kaartje van de klantensteun te registreren alvorens een ingang (zie &quot;Nota&quot;hierboven) te beginnen, zodat tijdelijk het onbruikbaar maken van Orchestrator van de Versie kan worden gepland.

Als het Orchestrator van de Versie nog loopt wanneer een ingestie wordt begonnen, presenteert het gebruikersinterface dit bericht. U kunt desondanks doorgaan, waarbij u het risico accepteert, door het veld te controleren en nogmaals op de knop te drukken.

>[!NOTE]
>
> De Orchestrator van de versie wordt nu opgesteld aan de milieu&#39;s van de Ontwikkeling, zodat zou het pauzeren updates op die milieu&#39;s eveneens moeten worden gedaan.

![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/error_releaseorchestrator_ingestion.png)

### Bijkomende congestiefout als gevolg van Uniqueness Constraint

Een gemeenschappelijke oorzaak van een [Bovenste inname](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process) error is een conflict in knoop ids. Als u deze fout wilt identificeren, downloadt u het innamelogboekbestand met de interface van Cloud Acceleration Manager en zoekt u een item als de volgende:

>java.lang.RuntimeException: org.apache.jackrabbit.oak.api.CommitFailedException: OakConstraint0030: Uniqueness constraint violated property [jcr:uuid] met waarde a1a1a1a1-b2b2-c3c3-d4d4-e5e5e5e5e5: /some/path/jcr:content, /some/other/path/jcr:content

Elk knooppunt in AEM moet een unieke uuid hebben. Deze fout geeft aan dat een knooppunt dat wordt ingesloten, dezelfde uuid heeft als een knooppunt dat zich elders op een ander pad op de doelinstantie bevindt.
Deze situatie kan zich voordoen als een knooppunt van de bron wordt verplaatst tussen een extractie en een volgende [Extractie bovenaan](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process).
Het kan ook gebeuren als een knoop op het doel tussen een inname en een verdere top-up inname wordt bewogen.

Dit conflict moet handmatig worden opgelost. Iemand die bekend is met de inhoud, moet beslissen welke van de twee knooppunten moet worden verwijderd, rekening houdend met andere inhoud die ernaar verwijst. De oplossing kan vereisen dat de top-up extractie opnieuw wordt gedaan zonder de beledigende knoop.

### Opsommingsfout vanwege niet-verwijderen knooppunt waarnaar wordt verwezen

Een andere veelvoorkomende oorzaak van een [Bovenste inname](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process) de mislukking is een versieconflict voor een bepaalde knoop op de doelinstantie. Als u deze fout wilt identificeren, downloadt u het innamelogboekbestand met de interface van Cloud Acceleration Manager en zoekt u een item als de volgende:
>java.lang.RuntimeException: org.apache.jackrabbit.oak.api.CommitFailedException: OakIntegrity0001: Unable to delete referenced node: 8a2289f4-b904-4bd0-8410-15e41e 976a8

Dit kan gebeuren als een knooppunt op het doel wordt gewijzigd tussen een opname en een volgende opvulopname, zodat er een nieuwe versie is gemaakt. Als voor de opname &#39;include-versies&#39; is ingeschakeld, kan er een conflict optreden omdat het doel nu een recentere versie heeft waarnaar wordt verwezen door de versiegeschiedenis en andere inhoud. Het insluitingsproces kan het conflicterende versieknooppunt niet verwijderen omdat ernaar wordt verwezen.

De oplossing kan vereisen dat de top-up extractie opnieuw wordt gedaan zonder de beledigende knoop. Of u maakt een kleine migratieset van het aanstootgevende knooppunt, maar met &quot;include-versies&quot; uitgeschakeld.

De beste praktijken wijzen erop dat als een opname met wipe=false en &quot;omvat versies&quot;=waar moet worden in werking gesteld het van cruciaal belang is dat de inhoud op het doel zo weinig mogelijk wordt gewijzigd, tot de migratiereis volledig is. Anders kunnen deze conflicten optreden.


## Volgende functies {#whats-next}

Nadat u Ingesting Content in Target hebt voltooid, kunt u logboeken van elke stap (extractie en opname) weergeven en op fouten zoeken. Zie [Logboeken voor een migratieset weergeven](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/viewing-logs.html) voor meer informatie.
