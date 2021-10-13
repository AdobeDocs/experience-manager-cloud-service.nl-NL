---
title: De tool Content Transfer gebruiken
description: De tool Content Transfer gebruiken
exl-id: a19b8424-33ab-488a-91b3-47f0d3c8abf5
source-git-commit: 04494e116fcdd38622ae2d4434d7cf8e4034d5aa
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# De tool Content Transfer gebruiken {#using-content-transfer-tool}

## Extractieproces in Content Transfer {#extraction-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_extraction"
>title="Inhoud extraheren"
>abstract="Extractie heeft betrekking op het extraheren van inhoud van de bron AEM instantie naar een tijdelijk gebied dat migratieset wordt genoemd. Een migratieset is een opslaggebied op de cloud dat door Adobe wordt geleverd om overgedragen content tijdelijk op te slaan tussen de AEM-broninstantie en de AEM Cloud Service-instantie."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#top-up-extraction-process" text="Extractie naar boven"

Voer de onderstaande stappen uit om uw migratieset te extraheren uit de Content Transfer-tool:
>[!NOTE]
>Als Amazon S3 of Azure Data Store wordt gebruikt als het type gegevensopslag, kunt u de optionele stap voor het kopiëren uitvoeren om de extractiefase aanzienlijk te versnellen. Hiervoor moet u een `azcopy.config`-bestand configureren voordat extractie wordt uitgevoerd. Raadpleeg [Grote opslagplaatsen voor inhoud verwerken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en) voor meer informatie.

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

### Extractie aanvullen {#top-up-extraction-process}

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

## Opnameproces in Content Transfer {#ingestion-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion"
>title="Inktatie van inhoud"
>abstract="Ingestie verwijst naar het opnemen van inhoud van de migratie die is ingesteld in de Cloud Service-instantie van het doel. De Content Transfer-tool heeft een functie die ondersteuning biedt voor differentiële aanvulling van content. Hierbij worden alleen die wijzigingen overgedragen die zijn aangebracht sinds de vorige activiteit voor contentoverdracht."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#top-up-ingestion-process" text="Opname aanvullen"

Voer de onderstaande stappen uit om uw migratieset uit de Content Transfer-tool op te nemen:
>[!NOTE]
>Als Amazon S3 of Azure Data Store wordt gebruikt als het type gegevensopslag, kunt u de optionele pre-copy stap uitvoeren om de innamefase aanzienlijk te versnellen. Raadpleeg [Ingesting met AzCopy](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en#ingesting-azcopy) voor meer informatie.

1. Selecteer een migratieset van *Overzicht* pagina en klik **Ingest** om opname te beginnen. Het dialoogvenster voor het **opnemen van de migratieset** wordt weergegeven. Inhoud kan tegelijkertijd worden ingevoerd in een instantie Auteur of Publiceren. Selecteer de instantie waaraan u inhoud wilt toevoegen. Klik op **Ingest** om de innamefase te starten.

   >[!IMPORTANT]
   >Als het opnemen met pre-copy wordt gebruikt (voor S3 of Azure Data Store), wordt het geadviseerd om de opname van de Auteur eerst alleen in werking te stellen. Hierdoor wordt de opname voor publiceren sneller wanneer deze later wordt uitgevoerd.

   >[!IMPORTANT]
   >Wanneer de optie **Bestaande inhoud op een Cloud-instantie vegen voordat de optie** wordt ingesloten, wordt de gehele bestaande opslagruimte verwijderd en wordt een nieuwe opslagplaats gemaakt waarin inhoud wordt opgenomen. Dit betekent dat alle instellingen, inclusief de machtigingen voor de Cloud Service van het doel, opnieuw worden ingesteld. Dit geldt ook voor een beheerder die wordt toegevoegd aan de groep **beheerders**.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets/content-ingestion-03.png)

   Klik bovendien op **Klantenservice** om een ticket te registreren, zoals in de bovenstaande afbeelding wordt getoond. Ook, verwijs naar [Belangrijke Overwegingen voor het Gebruiken van het Hulpmiddel van de Overdracht van de Inhoud](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#pre-reqs) om meer te leren.

1. Zodra de opname volledig is, werkt de status aan **FINISHED** bij.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets/15-ingestion-complete.png)

### Opname aanvullen {#top-up-ingestion-process}

De Content Transfer-tool heeft een functie die ondersteuning biedt voor differentiële *aanvulling* van content. Hierbij worden alleen die wijzigingen overgedragen die zijn aangebracht sinds de vorige activiteit voor contentoverdracht.

>[!NOTE]
>
>Na de eerste overdracht van content wordt het aangeraden om regelmatig differentiële aanvullingen van content uit te voeren. Zo houdt u de periode waarin content wordt &#39;bevroren&#39; voor de uiteindelijke differentiële contentoverdracht zo kort mogelijk, voordat u live gaat op Cloud Service.

Als het opnameproces is voltooid, kunt u deltacontent gebruiken via de opnamemethode met aanvullen. Voer de onderstaande stappen uit:

1. Ga naar de pagina *Overview* en selecteer de migratieset waarvoor u de aanvullingsopname wilt uitvoeren. Klik op **Ingest** om de opname te starten. Het dialoogvenster voor het **opnemen van de migratieset** wordt weergegeven.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets/content-ingestion-02.png)

   >[!IMPORTANT]
   >Schakel de optie **Bestaande inhoud vegen op een Cloud-instantie uit voordat u** inneemt om te voorkomen dat de bestaande inhoud wordt verwijderd uit de vorige insluitingsactiviteit. Bovendien, klik op **de Zorg van de Klant** om een kaartje, zoals aangetoond in het voorafgaande cijfer te registreren.


### Logboeken voor een migratieset weergeven {#viewing-logs-migration-set}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_logs"
>title="Logbestanden weergeven"
>abstract="Na voltooiing van Extractie van Ingestie, controleer de logboeken om het even welke fout/waarschuwingen. Fouten moeten onmiddellijk worden verholpen, hetzij door de gemelde problemen te verhelpen, hetzij door contact op te nemen met de ondersteuning van Adobe."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#troubleshooting" text="Problemen oplossen"
>additional-url="https://helpx.adobe.com/ca/enterprise/admin-guide.html/ca/enterprise/using/support-for-experience-cloud.ug.html" text="Contact opnemen met Adobe-ondersteuning"

Controleer na elke stap (extractie en inname) de logboeken en zoek op fouten.  Fouten moeten onmiddellijk worden verholpen, hetzij door de gemelde problemen te verhelpen, hetzij door contact op te nemen met de ondersteuning van Adobe.

Op de pagina *Overview* kunt u de logboeken voor een bestaande migratieset bekijken.
Voer de onderstaande stappen uit:

1. Ga naar de pagina *Overview* en selecteer de migratieset waarvan u het logboek wilt bekijken. Klik op **View Log** op de actiebalk.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets/view-log1.png)

1. Het dialoogvenster **Logs** wordt weergegeven. Klik op **Extraction Log** om de extractielogbestanden op een nieuw tabblad weer te geven.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets/view-log2.png)
Of:

   U kunt de logboeken voor uw migratieset ook bekijken op het scherm *Overview*. Selecteer de migratieset en klik op de status onder het veld **EXTRACTION**. Klik in dit geval op **FINISHED** om de logbestanden op een nieuw tabblad weer te geven.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets/view-log3.png)

1. Als u de logboeken wilt koppelen zonder de gebruikersinterface te gebruiken, past u SSH toe in uw bron AEM-omgeving op `crx-quickstart/cloud-migration/extraction-XXXXX/output.log file`.

### Een migratieset verwijderen {#deleting-migration-set}

U kunt de migratieset verwijderen vanaf de pagina *Overview*.
Voer de onderstaande stappen uit:

1. Ga naar de pagina *Overview* en selecteer de migratieset die u wilt verwijderen. Klik op **Delete** op de actiebalk.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets/delete-1.png)

1. Klik op **Delete** in het dialoogvenster **Delete Migration Set** om de verwijdering te bevestigen.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets/delete-3.png)


## Het gereedschap Inhoud overbrengen uitvoeren op een instantie Publiceren {#running-ctt-on-publish}

Het wordt aanbevolen om tijdens het verplaatsen van inhoud naar een instantie Publish, CTT te installeren op de instantie source Publish om inhoud naar de instantie target Publish te verplaatsen. Volg de onderstaande aanbevolen aanpak:

* Gebruik dezelfde versie van de CTT die op de instantie Auteur is gebruikt.

* Er hoeft slechts één publicatieknooppunt te worden gemigreerd. Deze moet uit het taakverdelingsmechanisme worden verwijderd voordat de extractie wordt gestart.

* Gebruik bij het maken van de migratieset de URL van de auteur-AEMaaCS-omgeving.

* Tijdens het publiceren wordt de publicatielaag NIET verkleind (in tegenstelling tot de auteur). Als voorzorgsmaatregel, gelieve te vermijden om het even welke gebruiker in werking gestelde schrijfverrichtingen zoals:

   * Distributie van inhoud van AEMaaCS-auteur naar Publiceren in die omgeving
   * Gebruikerssynchronisatie tussen publicatie-instanties


## Problemen oplossen {#troubleshooting}

### Ontbrekende blob-id&#39;s {#missing-blobs}

Als er ontbrekende blob-id&#39;s worden gerapporteerd, zoals hieronder vermeld, is het nodig een consistentiecontrole uit te voeren in de bestaande repository en de ontbrekende blobs te herstellen.
`ERROR o.a.j.o.p.b.AbstractSharedCachingDataStore - Error retrieving record [ba45c53f8b687e7056c85dceebf8156a0e6abc7e]`

De volgende opdracht wordt uitgevoerd 

>[!NOTE]
>
>`--verbose` markering is vereist om te rapporteren vanuit welke knooppuntpaden wordt verwezen naar de blobs.

**Voor repository&#39;s van AEM 6.5 (Oak 1.8 en lager)**

```shell
java -jar oak-run.jar datastorecheck --consistency --store [<SEGMENT_STORE_PATH>|<MONGO_URI>] --[s3ds|fds] <DATASTORE_CFG> --verbose <OUT_DIR> --dump
```

**Voor repository&#39;s met Oak > 1.10**

```shell
java -jar oak-run.jar datastore --check-consistency [<SEGMENT_STORE_PATH>|<MONGO_URI>] --[s3ds|fds|azureds] <DATASTORE_CFG> --out-dir <OUT_DIR> --work-dir <TEMP_DIR> --verbose
```

Raadpleeg [Oak Runnable Jar](https://github.com/apache/jackrabbit-oak/tree/trunk/oak-run) voor meer informatie.

De bestanden die in de *OUT_DIR* hierboven zijn gemaakt voor consistentie, kunnen vervolgens worden gecontroleerd op paden met ontbrekende binaire elementen en op de juiste manier gecorrigeerd, zoals herstellen via een back-up, paden verwijderen, opnieuw indexeren, enzovoort.


### Gedrag van gebruikersinterface {#ui-behavior}

Als gebruiker ziet u de volgende wijzigingen in het gedrag van de Content Transfer-gebruikersinterface:

* De pictogrammen in de gebruikersinterface van de Content Transfer-tool kunnen afwijken van de schermafbeeldingen die in deze handleiding worden getoond. Mogelijk worden ze zelfs helemaal niet weergegeven, afhankelijk van de versie van de AEM-broninstantie.
