---
title: De tool Content Transfer gebruiken
description: De tool Content Transfer gebruiken
translation-type: tm+mt
source-git-commit: 7af431be9817c5d5fda933e4697a63ab1085276f
workflow-type: tm+mt
source-wordcount: '2018'
ht-degree: 66%

---


# De tool Content Transfer gebruiken {#using-content-transfer-tool}

## Belangrijke overwegingen voor het gebruik van de Content Transfer-tool {#pre-reqs}

Bekijk de onderstaande sectie om inzicht te krijgen in de belangrijke overwegingen bij het uitvoeren van de Content Transfer-tool:

* De minimale systeemvereisten voor de Content Transfer-tool zijn AEM 6.3 + en JAVA 8. Bij lagere versies van AEM moet u de content-repository upgraden naar AEM 6.5 om de tool Content Transfer te gebruiken.

* Java moet op het AEM worden gevormd milieu, zodat het `java` bevel door de gebruiker kan worden uitgevoerd die AEM begint.

* U kunt het gereedschap Inhoud overbrengen gebruiken met de volgende typen gegevensopslag: File Data Store, S3 Data Store, Shared S3 Data Store en Azure Blob Store Data Store.

* Als u een *Sandbox Milieu* gebruikt, zorg ervoor dat uw milieu huidig is en aan de recentste versie wordt bevorderd. Als u een *Productieomgeving* gebruikt, wordt deze automatisch bijgewerkt.

* Om het hulpmiddel van de Overdracht van de Inhoud te gebruiken, zult u een admin gebruiker op uw broninstantie moeten zijn en tot de lokale AEM beheerdersgroep in de instantie behoren van de Cloud Service u inhoud overbrengt naar. Zonder deze machtigingen kunnen gebruikers het toegangstoken tot de Content Transfer-tool niet ophalen.

* Het toegangstoken kan periodiek of na een specifieke tijdspanne verlopen of nadat het milieu van de Cloud Service is bevorderd. Als het toegangstoken is verlopen, zult u niet met de instantie van de Cloud Service kunnen verbinden en u zult het nieuwe toegangstoken moeten terugwinnen. Het statuspictogram dat aan een bestaande migratieset is gekoppeld, wordt gewijzigd in een rode cloud en er wordt een bericht weergegeven wanneer u de muisaanwijzer op de desbetreffende cloud plaatst.

* Momenteel is de standaardgrootte van MongoDB voor een AEM als instantie van de Auteur van de Cloud Service 32 GB. Het wordt geadviseerd dat voor de grootte van de segmentopslag groter dan 20GB, u een kaartje van de Steun zou moeten voorleggen om de grootte te verhogen MongoDB.

* De gebruikers en de Groepen die door het Hulpmiddel van de Overdracht van de Inhoud worden overgebracht zijn slechts die die door de inhoud worden vereist om aan toestemmingen te voldoen. Met het proces *Extractie* wordt de gehele `/home` naar de migratieset gekopieerd en met het proces *Ingestie* worden alle gebruikers en groepen gekopieerd waarnaar in de gemigreerde inhoud-ACL&#39;s wordt verwezen.

* Tijdens de extractiefase wordt de Content Transfer-tool uitgevoerd op een actieve AEM-broninstantie.

* Nadat u de *Extractie*-fase van het proces voor inhoudsoverdracht hebt voltooid en voordat u de *Ingestiefase* start om inhoud in uw AEM in te voeren als een Cloud Service *Stage* of *Production*-instanties, moet u een ondersteuningsticket registreren om de Adobe te informeren over uw voornemen om *Ingestikt uit te voeren* zodat Adobe ervoor kan zorgen dat er geen onderbrekingen optreden tijdens het *Ingestieproces*. U zult het steunkaartje 1 week vóór uw geplande *Ingestiedatum* moeten registreren. Zodra, hebt u het steunkaartje voorgelegd, zal het ondersteuningsteam begeleiding op volgende stappen verstrekken.
   * Logboek een steunkaartje met de volgende details:
      * De nauwkeurige datum en de geschatte tijd (met uw tijd-streek) wanneer u van plan bent om de *Ingestiefase* te beginnen.
      * Omgevingstype (werkgebied of productie) waarin u gegevens wilt opnemen.
      * Programma-id.

* In de *Opnamefase* voor de auteur wordt de volledige auteurimplementatie omlaag geschaald. Dit betekent dat de auteur-AEM niet beschikbaar is tijdens het volledige opnameproces. Zorg er ook voor dat er geen Cloud Manager-pijpleidingen worden uitgevoerd terwijl u de *Ingestiefase* uitvoert.


## Beschikbaarheid {#availability}

Het gereedschap Inhoud overbrengen kan als een ZIP-bestand worden gedownload van de Software Distribution Portal. U kunt het pakket via Package Manager installeren op uw AEM-broninstantie (Adobe Experience Manager). Download de nieuwste versie. Raadpleeg [Opmerkingen bij de release](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html) voor meer informatie over de nieuwste versie.

>[!NOTE]
>Download de Content Transfer-tool van de [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)-portal.

## De Content Transfer-tool uitvoeren {#running-tool}

>[!VIDEO](https://video.tv.adobe.com/v/35460/?quality=12&learn=on)


In deze sectie leert u hoe u de Content Transfer-tool gebruikt om content te migreren naar AEM as a Cloud Service (Auteur/Publiceren):

1. Selecteer de Adobe Experience Manager en navigeer naar Tools -> **Operations** -> **Content Transfer**.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets/content1.png)

1. De onderstaande console wordt weergegeven wanneer u de eerste migratieset maakt. Klik op **Create Migration Set** om een nieuwe migratieset te maken.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets/01-migration-set-overview.png)

   >[!NOTE]
   >Als u bestaande migratiesets hebt, zal de console de lijst van bestaande migratiesets met hun huidige status tonen.

1. Vul de velden in het scherm met de gegevens voor de **contentmigratieset** in, zoals hieronder beschreven.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets/02-migration-set-creation.png)


   1. **Name**: Voer de naam van de migratieset in.
      >[!NOTE]
      >Er zijn geen speciale tekens toegestaan voor de naam van de migratieset.

   1. **Cloud Service Configuration**: Voer de doelversie in van de auteur-URL voor AEM as a Cloud Service.

      >[!NOTE]
      >Tijdens de contentoverdracht kunt u maximaal vier migratiesets tegelijk maken en onderhouden.
      >Bovendien moet u voor elke specifieke omgeving een afzonderlijke migratie maken: *stage*, *ontwikkeling* of *productie*.

   1. **Access Token**: Voer het toegangstoken in.

      >[!NOTE]
      >U kunt het toegangstoken terugwinnen door **open toegangstoken** te gebruiken knoop. U moet ervoor zorgen dat u tot de AEM beheerdersgroep in de instantie van de doelCloud Service behoort.

   1. **Parameters**: Selecteer de volgende parameters om de migratieset te maken:

      1. **Include Version**: Selecteer de versie die u wilt opnemen.

      1. **Paths to be included**: Gebruik de padbrowser om paden te selecteren die moeten worden gemigreerd. Padkiezer accepteert invoer door te typen of te selecteren.

         >[!IMPORTANT]
         >Voor de volgende paden gelden beperkingen bij het maken van een migratieset:
         >* `/apps`
         >* `/libs`
         >* `/home`
         >* `/etc`


1. Klik op **Save** nadat u alle velden hebt gevuld in het scherm met de gegevens over de **contentmigratieset**.

1. U kunt de migratieset bekijken op de overzichtspagina *Overview*.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets/04-item-selection-and-quick-actions.png)

   Alle bestaande migratiesets op dit scherm worden met hun huidige status en statusinformatie weergegeven op de pagina *Overview.* Sommige van deze pictogrammen worden hieronder beschreven.

   * Een *rode wolk* geeft aan dat u het extractieproces niet kunt voltooien.
   * Een *groene wolk* geeft aan dat u het extractieproces wel kunt voltooien.
   * Een *geel pictogram* geeft aan dat u de bestaande migratieset niet hebt gemaakt en dat de specifieke migratieset door een andere gebruiker in dezelfde instantie wordt gemaakt.

1. Selecteer een migratieset op de overzichtspagina en klik op **Properties** om de eigenschappen van de migratieset weer te geven of te bewerken. Tijdens het bewerken van eigenschappen is het niet mogelijk de containernaam of de service-URL te wijzigen.



### Extractieproces in Content Transfer {#extraction-process}

Voer de onderstaande stappen uit om uw migratieset te extraheren uit de Content Transfer-tool:

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

#### Extractie aanvullen {#top-up-extraction-process}

De Content Transfer-tool heeft een functie die ondersteuning biedt voor differentiële aanvulling van content. Hierbij worden alleen die wijzigingen overgedragen die zijn aangebracht sinds de vorige activiteit voor contentoverdracht.

>[!NOTE]
>Na de eerste overdracht van content wordt het aangeraden om regelmatig differentiële aanvullingen van content uit te voeren. Zo houdt u de periode waarin content wordt &#39;bevroren&#39; voor de uiteindelijke differentiële contentoverdracht zo kort mogelijk, voordat u live gaat op Cloud Service.

Als het extractieproces is voltooid, kunt u deltacontent overdragen via de extractiemethode voor aanvullen. Voer de onderstaande stappen uit:

1. Ga naar de pagina *Overview* en selecteer de migratieset waarvoor u de aanvullingsextractie wilt uitvoeren. Klik op **Extract** om de extractie te starten. Het dialoogvenster voor de **extractie van de migratieset** wordt weergegeven.

   >[!IMPORTANT]
   >
   >Zorg dat de optie **Overwrite staging container during extraction** (voor het overschrijven van de stagingcontainer tijdens de extractie) is uitgeschakeld.
   >
   >![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets/11-topup-extraction.png)

### Opnameproces in Content Transfer {#ingestion-process}

Voer de onderstaande stappen uit om uw migratieset uit de Content Transfer-tool op te nemen:

1. Selecteer een migratieset op de pagina *Overview* en klik op **Ingest** om de extractie te starten. Het dialoogvenster voor het **opnemen van de migratieset** wordt weergegeven. Klik op **Ingest** om de innamefase te starten. Voor demonstratiedoeleinden is de optie voor het **opnemen van content naar de Auteur-instantie** uitgeschakeld. U kunt content gelijktijdig opnemen in de modules Auteur en Publiceren.

   >[!IMPORTANT]
   >Wanneer de optie **Bestaande inhoud op een Cloud-instantie vegen voordat de optie** wordt ingesloten, wordt de gehele bestaande opslagruimte verwijderd en wordt een nieuwe opslagplaats gemaakt waarin inhoud kan worden ingevoerd. Dit betekent dat alle instellingen, inclusief de machtigingen voor de Cloud Service van het doel, opnieuw worden ingesteld.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets/12-content-ingestion.png)

1. Zodra de opname volledig is, werkt de status in **PUBLISH INGESTION** gebied aan **FINISHED** bij.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets/15-ingestion-complete.png)

#### Opname aanvullen {#top-up-ingestion-process}

De Content Transfer-tool heeft een functie die ondersteuning biedt voor differentiële *aanvulling* van content. Hierbij worden alleen die wijzigingen overgedragen die zijn aangebracht sinds de vorige activiteit voor contentoverdracht.

>[!NOTE]
>
>Na de eerste overdracht van content wordt het aangeraden om regelmatig differentiële aanvullingen van content uit te voeren. Zo houdt u de periode waarin content wordt &#39;bevroren&#39; voor de uiteindelijke differentiële contentoverdracht zo kort mogelijk, voordat u live gaat op Cloud Service.

Als het opnameproces is voltooid, kunt u deltacontent gebruiken via de opnamemethode met aanvullen. Voer de onderstaande stappen uit:

1. Ga naar de pagina *Overview* en selecteer de migratieset waarvoor u de aanvullingsopname wilt uitvoeren. Klik op **Ingest** om de opname te starten. Het dialoogvenster voor het **opnemen van de migratieset** wordt weergegeven.

   >[!IMPORTANT]
   >
   >Schakel de optie **Bestaande inhoud vegen op een Cloud-instantie uit voordat u** inneemt om te voorkomen dat de bestaande inhoud wordt verwijderd uit de vorige insluitingsactiviteit.
   >
   >![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets/16-topup-ingestion.png)

### Logboeken voor een migratieset weergeven {#viewing-logs-migration-set}

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

* De gebruiker maakt een migratieset voor een auteur-URL (Ontwikkeling/Stage/Productie) en voert de extractie en opname uit.

* De gebruiker maakt vervolgens een nieuwe migratieset voor dezelfde auteur-URL en voert de extractie en opname uit voor de nieuwe migratieset. De gebruikersinterface toont dat de opnamestatus van de eerste migratieset verandert in **FAILED** en dat er geen logboeken beschikbaar zijn.

* Dit betekent niet dat de opname voor de eerste migratieset is mislukt. Dit gedrag laat alleen zien dat, wanneer een nieuwe opnametaak wordt gestart, de vorige opnametaak wordt verwijderd. De status van de wijzigingen in de eerste migratieset moet daarom worden genegeerd.

* De pictogrammen in de gebruikersinterface van de Content Transfer-tool kunnen afwijken van de schermafbeeldingen die in deze handleiding worden getoond. Mogelijk worden ze zelfs helemaal niet weergegeven, afhankelijk van de versie van de AEM-broninstantie.


