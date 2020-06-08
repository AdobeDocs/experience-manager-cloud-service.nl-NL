---
title: Het gereedschap Inhoud overbrengen gebruiken
description: Het gereedschap Inhoud overbrengen gebruiken
translation-type: tm+mt
source-git-commit: 7a0fa12198c69791caf7e44bfbfe7d71e389a984
workflow-type: tm+mt
source-wordcount: '1538'
ht-degree: 1%

---


# Het gereedschap Inhoud overbrengen gebruiken {#using-content-transfer-tool}

## Belangrijke overwegingen voor het gebruik van het gereedschap Inhoud overbrengen {#pre-reqs}

Volg de onderstaande sectie om inzicht te krijgen in de belangrijke overwegingen bij het uitvoeren van het gereedschap Inhoud overbrengen:

* De minimale systeemvereisten voor Content Transfer Tool zijn AEM 6.3 + en JAVA 8. Als u een lagere AEM-versie gebruikt, moet u de opslagplaats voor inhoud upgraden naar AEM 6.5 om het gereedschap Inhoud overbrengen te kunnen gebruiken.

* Als u een *Sandbox Milieu* gebruikt, zorg ervoor dat uw milieu wordt bevorderd tot Versie van 29 mei 2020 of later. Als u een *Productomgeving* gebruikt, wordt deze automatisch bijgewerkt.

* Om het hulpmiddel van de Overdracht van de Inhoud te gebruiken, zult u een admin gebruiker op uw broninstantie moeten zijn en tot de beleidsgroep in de instantie behoren van de Dienst van de Wolk u inhoud overbrengt naar. De onbevoorrechte gebruikers zullen niet het toegangstoken kunnen terugwinnen om het Hulpmiddel van de Overdracht van de Inhoud te gebruiken.

* Tijdens de extractiefase wordt het gereedschap Inhoud overbrengen uitgevoerd op een actieve AEM-broninstantie.

* De *Ingestiefase* voor de auteur zal de volledige auteursplaatsing verminderen. Dit betekent dat de auteur AEM niet beschikbaar zal zijn tijdens het volledige innameproces.

## Beschikbaarheid {#availability}

Het gereedschap Inhoud overbrengen kan als een ZIP-bestand worden gedownload van de portal Software Distribution. U kunt het pakket installeren via Package Manager op uw AEM-bronexemplaar (Adobe Experience Manager).

>[!NOTE]
>Download de Content Transfer Tool van [Adobe Experience Cloud](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html).

## Het gereedschap Inhoud overbrengen uitvoeren {#running-tool}

Volg deze sectie om te leren hoe u het gereedschap Inhoud overbrengen kunt gebruiken om de inhoud als cloudservice (Auteur/Publiceren) naar AEM te migreren:

1. Selecteer Adobe Experience Manager en navigeer naar gereedschappen -> **Bewerkingen** -> **Inhoud overbrengen**.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/content1.png)

1. Klik op **Migratieset** maken om een nieuwe migratieset te maken. De details **van de** Content Migrations Set worden weergegeven.

   >[!NOTE]
   >U zult de bestaande migratiesets op dit scherm met hun huidige status bekijken.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ctt-img4.png)

1. Vul de velden in het gedetailleerde **scherm voor de** Content Migrations Set, zoals hieronder wordt beschreven.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/content-3.png)


   1. **Naam**: Voer de naam van de migratieset in.
      >[!NOTE]
      >Er zijn geen speciale tekens toegestaan voor de naam van de migratieset.

   1. **Configuratie** cloudservice: Voer de AEM van het doel in als URL van auteur van de cloudservice.

      >[!NOTE]
      >U kunt maximaal vier migratiesets tegelijk maken en onderhouden tijdens de activiteit voor inhoudsoverdracht.
      >Bovendien moet u een migratie afzonderlijk maken voor elk van de specifieke omgevingen: *werkgebied*, *ontwikkeling* of *productie*.

   1. **Toegangstoken**: Voer het toegangstoken in.

      >[!NOTE]
      >U kunt het toegangstoken van de auteursinstantie terugwinnen door aan te navigeren `/libs/granite/migration/token.json`. Het toegangstoken wordt teruggewonnen van de auteursinstantie van de Dienst van de Wolk.

   1. **Parameters**: Selecteer de volgende parameters om de migratieset te maken:

      1. **Inclusief versie**: Selecteer de gewenste optie.

      1. **In te voegen** paden: Gebruik padbrowser om paden te selecteren die moeten worden gemigreerd.

         >[!IMPORTANT]
         >De volgende paden zijn beperkt tijdens het maken van een migratieset:
         >* `/apps`
         >* `/libs`
         >* `/home`
         >* `/etc`


1. Klik op **Opslaan** nadat u alle velden hebt gevuld in het scherm Details **over** inhoudsmigraties instellen.

1. U zult uw migratieset in de *overzichtspagina* bekijken.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ctt-img4.png)

   Alle bestaande migratiesets op dit scherm worden weergegeven op de pagina *Overzicht* met hun huidige status en statusinformatie.

   * Een *rode wolk* geeft aan dat u het extractieproces niet kunt voltooien.
   * Een *groene cloud* geeft aan dat u het extractieproces kunt voltooien.
   * Een *geel pictogram* geeft aan dat u de bestaande migratieset niet hebt gemaakt en dat de specifieke migratieset door een andere gebruiker in dezelfde instantie wordt gemaakt.

1. Selecteer een migratieset op de overzichtspagina en klik op **Eigenschappen** om de eigenschappen van de migratieset weer te geven of te bewerken.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ctt-img6.png)

### Extractieproces in inhoudsoverdracht {#extraction-process}

Voer de onderstaande stappen uit om uw migratieset te extraheren uit het gereedschap Inhoud overbrengen:

1. Selecteer een migratieset op de pagina *Overzicht* en klik op **Extraheren** om de extractie te starten.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/extraction-img1.png)

1. Het dialoogvenster extractie **van de** migratieset wordt weergegeven en klik op **Extraheren** om de extractiefase te voltooien.

   >[!NOTE]
   >U hebt de optie om het opvoeren container tijdens de extractiefase te overschrijven.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/extract-2.png)

1. In het veld **EXTRACTION** wordt nu de status **RUNNING** weergegeven voor het extractieproces dat in uitvoering is.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/extract-3.png)

   Zodra de extractie is voltooid, wordt de status van de migratieset bijgewerkt naar **FINISHED** en wordt een *effen groen* wolkenpictogram weergegeven onder het veld **INFO** .

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/extract-4.png)

   >[!NOTE]
   >U moet de pagina vernieuwen om de bijgewerkte status weer te geven.
   >Wanneer de extractiefase wordt gestart, wordt de schrijfvergrendeling gemaakt en na *60 seconden* vrijgegeven. Dus als een extractie wordt gestopt, moet je een minuut wachten tot de vergrendeling weer wordt losgelaten voordat je de extractie opnieuw start.

#### Extractie bovenaan {#top-up-extraction-process}

Het gereedschap Inhoud overbrengen heeft een functie die ondersteuning biedt voor differentiële aanvulling van inhoud, waarbij alleen wijzigingen kunnen worden overgebracht die zijn aangebracht sinds de vorige activiteit voor inhoudsoverdracht.

>[!NOTE]
>Na de eerste overdracht van inhoud wordt aangeraden regelmatig differentiële toevoegingen aan inhoud uit te voeren om de periode waarin de inhoud wordt vastgezet voor de uiteindelijke differentiële overdracht van inhoud te verkorten voordat u live gaat met de Cloud Service.

Als het extractieproces is voltooid, kunt u delta-inhoud overbrengen met behulp van de extractiemethode top-up. Voer de onderstaande stappen uit:

1. Navigeer naar de pagina *Overzicht* en selecteer de migratieset waarvoor u de bovenste extractie wilt uitvoeren.

1. Klik op **Extraheren** om de extractie bovenaan te starten.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/extraction-img1.png)

1. Het dialoogvenster voor extractie **van** migratieset wordt weergegeven.

   >[!IMPORTANT]
   >Schakel de optie voor het **overschrijven van de staging container tijdens het extraheren** uit.
   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/extract-topup-1.png)

### Ingestieproces in inhoudsoverdracht {#ingestion-process}

Voer de onderstaande stappen uit om uw migratieset vanuit het gereedschap Inhoud overbrengen in te voeren:

1. Selecteer een migratieset op de *overzichtspagina* en klik op **Samenvatting** om de extractie te starten.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ingest-1.png)

1. Het dialoogvenster **Invoer** migratieset wordt weergegeven.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ingest-2.png)

   Voor demonstratiedoeleinden is de optie Inhoud **samenvoegen tot instantie** Auteur uitgeschakeld. Het is mogelijk inhoud tegelijkertijd in te voeren bij Auteur en te publiceren.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ingest-3.png)

   Klik op **Ingest** om de innamefase te voltooien.

1. Zodra de opname is voltooid, wordt de status in het veld **AUTHOR INGESTION** bijgewerkt naar **FINISHED** en wordt een effen groen wolkenpictogram weergegeven onder de **INFO**.
   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ingest-4.png)

   >[!NOTE]
   > U moet de pagina vernieuwen om de bijgewerkte status weer te geven.

#### Top Up-inname {#top-up-ingestion-process}

Het gereedschap Inhoud overbrengen beschikt over een functie die ondersteuning biedt voor differentiële *aanvulling* van inhoud, waarbij alleen wijzigingen kunnen worden overgedragen die zijn aangebracht sinds de vorige activiteit voor inhoudsoverdracht.

>[!NOTE]
>Na de eerste overdracht van inhoud wordt aangeraden regelmatig differentiële toevoegingen aan inhoud uit te voeren om de periode waarin de inhoud wordt vastgezet voor de uiteindelijke differentiële overdracht van inhoud te verkorten voordat u live gaat met de Cloud Service.

Als het inslikken is voltooid, kunt u delta-inhoud gebruiken met de methode voor het toevoegen van de inhoud aan de bovenkant. Voer de onderstaande stappen uit:

1. Navigeer naar de pagina *Overzicht* en selecteer de migratieset waarvoor u de bovenste opname wilt uitvoeren.

1. Klik op **Samenvatting** om de extractie bovenaan te starten.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ingest-1.png)

1. Het dialoogvenster **Opname** migratieset wordt weergegeven.

   >[!NOTE]
   >Schakel de optie *Sluitereffect* uit om te voorkomen dat de bestaande inhoud uit de vorige insluitingsactiviteit wordt verwijderd.
   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ingest-topup-1.png)

### Logboeken voor een migratieset weergeven {#viewing-logs-migration-set}

U kunt logboeken voor een bestaande migratieset van de pagina van het *Overzicht* bekijken.
Voer de onderstaande stappen uit:

1. Navigeer naar de pagina *Overzicht* en selecteer de migratieset die u wilt verwijderen en klik op Logboek **** weergeven op de actiebalk.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/view-log1.png)

1. Het dialoogvenster **Logs** wordt weergegeven. Klik op **Extractielogbestanden** om de logbestanden op een nieuw tabblad weer te geven.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets/view-log2.png)of

   U kunt logboeken voor uw migratie ook bekijken die van het scherm van het *Overzicht* wordt geplaatst. Selecteer de migratieset en klik op de status onder **EXTRACTION** -veld. Klik in dit geval op **Voltooid** om de logbestanden op een nieuw tabblad weer te geven.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/view-log3.png)

### Een migratieset verwijderen {#deleting-migration-set}

U kunt de migratieset verwijderen uit de pagina *Overzicht* .
Voer de onderstaande stappen uit:

1. Navigeer naar de pagina *Overzicht* en selecteer de migratieset die u wilt verwijderen en klik op **Verwijderen** op de actiebalk.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/delete-1.png)

1. Klik op **Verwijderen** uit het dialoogvenster Migratieset **** verwijderen om de verwijdering te bevestigen.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/delete-3.png)

## Problemen oplossen {#troubleshooting}

### Ontbrekende blob-id&#39;s {#missing-blobs}

Als er ontbrekende blob-id&#39;s worden gerapporteerd, zoals hieronder vermeld, is het nodig een consistentiecontrole uit te voeren in de bestaande opslagplaats en de ontbrekende lobs te herstellen.
`ERROR o.a.j.o.p.b.AbstractSharedCachingDataStore - Error retrieving record [ba45c53f8b687e7056c85dceebf8156a0e6abc7e]`

De volgende opdracht wordt uitgevoerd

>[!NOTE]
> `--verbose` markering is vereist om de knoopwegen van te melden waar de klokken van verwijzingen worden voorzien.

**Voor gegevensbanken AEM 6.5 (eikel 1.8 en lager)**

```shell
java -jar oak-run.jar datastorecheck --consistency --store [<SEGMENT_STORE_PATH>|<MONGO_URI>] --[s3ds|fds] <DATASTORE_CFG> --verbose <OUT_DIR> --dump
```

**Voor opslagplaatsen met eikenhout > 1.10**

```shell
java -jar oak-run.jar datastore --check-consistency [<SEGMENT_STORE_PATH>|<MONGO_URI>] --[s3ds|fds|azureds] <DATASTORE_CFG> --out-dir <OUT_DIR> --work-dir <TEMP_DIR> --verbose
```

Raadpleeg [Oak Runnable Jar](https://github.com/apache/jackrabbit-oak/tree/trunk/oak-run) voor meer informatie.

De bestanden die in de *OUT_DIR* hierboven zijn gemaakt voor consistentie, kunnen vervolgens worden gecontroleerd op paden met ontbrekende binaire elementen en op de juiste manier, zoals het herstellen van een back-up, het verwijderen van paden, het opnieuw indexeren, enzovoort.

### Werking gebruikersinterface {#ui-behavior}

Als gebruiker, zou u de volgende gedragsveranderingen in het Gebruikersinterface (UI) voor het Hulpmiddel van de Overdracht van de Inhoud kunnen zien:

* De gebruiker maakt een migratieset voor een auteur-URL (Development/Stage/Production) en voert de extractie en opname uit.

* De gebruiker maakt vervolgens een nieuwe migratieset voor dezelfde auteur-URL en voert de extractie en opname uit voor de nieuwe migratieset. UI toont aan dat de innamestatus van de eerste migratieset verandert in **MISLUKT** en geen logboeken beschikbaar zijn.

* Dit betekent niet dat de opname voor de eerste migratieset is mislukt. Dit gedrag wordt gezien omdat wanneer een nieuwe innametaak wordt gestart, de vorige innametaak wordt verwijderd. De status van de wijzigingen in de eerste migratieset moet daarom worden genegeerd.

* De pictogrammen in de gebruikersinterface van het gereedschap Inhoud overbrengen kunnen afwijken van de schermafbeeldingen die in deze handleiding worden getoond of worden mogelijk helemaal niet weergegeven, afhankelijk van de versie van de AEM-broninstantie.


