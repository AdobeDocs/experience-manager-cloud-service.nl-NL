---
title: Aan de slag met het gereedschap Inhoud overbrengen
description: Leer hoe u aan de slag kunt met het gereedschap Inhoud overbrengen
exl-id: c0cecf65-f419-484b-9d55-3cbd561e8dcd
feature: Migration
role: Admin
source-git-commit: edfefb163e2d48dc9f9ad90fa68809484ce6abb0
workflow-type: tm+mt
source-wordcount: '1654'
ht-degree: 2%

---


# Aan de slag met het gereedschap Inhoud overbrengen {#getting-started-content-transfer-tool}


## Beschikbaarheid {#availability}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_download"
>title="Downloaden"
>abstract="Het gereedschap Inhoud overbrengen kan als een ZIP-bestand worden gedownload van de Software Distribution Portal. U kunt het pakket via Package Manager installeren op uw Adobe Experience Manager-bronexemplaar (AEM). Download de nieuwste versie."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/release-notes/release-notes-current.html?lang=nl-NL" text="Release-opmerkingen"
>additional-url="https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html" text="Software Distribution Portal"

Het gereedschap Inhoud overbrengen kan als een ZIP-bestand worden gedownload van de Software Distribution Portal. U kunt het pakket als [ Manager van het Pakket ](/help/implementing/developing/tools/package-manager.md) op uw bronAdobe Experience Manager (AEM) instantie installeren. Download de nieuwste versie. Voor meer details op de recentste versie, zie [ de Nota&#39;s van de Versie ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/release-notes/release-notes-current.html?lang=nl-NL).

Alleen versie 2.0.0 en hoger wordt ondersteund en het is raadzaam de meest recente versie te gebruiken.

>[!NOTE]
>Download de Content Transfer-tool van de [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)-portal.

## Connectiviteit Source-omgeving {#source-environment-connectivity}

>[!NOTE]
>
>Er kan ook een verbindingsfout optreden als een migratieset uit Cloud Acceleration Manager is verwijderd.

De AEM-broninstantie wordt mogelijk achter een firewall uitgevoerd, waarbij deze alleen bepaalde hosts kan bereiken die aan een Lijst van gewenste personen zijn toegevoegd. Als u een extractie wilt uitvoeren, moeten de volgende eindpunten toegankelijk zijn vanuit de instantie waarop AEM wordt uitgevoerd:

* De Azure-opslagservice: `casstorageprod.blob.core.windows.net`

>[!NOTE]
>Als de extractie mislukt als gevolg van de volgende fout: &quot;javax.net.ssl.SSLHandshakeException: sun.security.validator.ValidatorException: PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certificate path to requested target&quot;, kan dit worden opgelost door het relevante CA-certificaat te importeren.

### SSL-registratie inschakelen {#enable-ssl-logging}

Soms is het lastig om te begrijpen hoe problemen met SSL/TLS-verbindingen optreden. Als u verbindingsproblemen wilt oplossen tijdens een extractieproces, kunt u SSL-registratie inschakelen via de System Console van de AEM-bronomgeving door de volgende stappen uit te voeren:

1. Navigeer aan de Console van het Web van Adobe Experience Manager op uw broninstantie, door **Hulpmiddelen > Verrichtingen > de Console van het Web** of direct aan URL in *https://serveraddress :serverport te gaan/system/console/configMgr*
1. Onderzoek naar {de Configuratie van de Dienst van de Extractie van het Hulpmiddel van de Overdracht van 0} Inhoud **&#x200B;**
1. Gebruik de knop voor het potloodpictogram om de configuratiewaarden ervan te bewerken
1. Laat **toe het registreren ssl voor extractie** plaatsen, dan druk **sparen**:

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets/enable_ssl_logging.png)

>[!NOTE]
>
>Deze markering is alleen voor foutopsporing in SSL-problemen. Zorg ervoor dat de markering is uitgeschakeld voordat u de extractie uitvoert, omdat dit veel schijfruimte kan vereisen. Hierdoor kan de stationscapaciteit worden gevuld en kan het extractieproces mislukken.

## Het gereedschap Inhoud overbrengen uitvoeren {#running-tool}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_demo"
>title="Gereedschap Inhoud overbrengen uitvoeren"
>abstract="Leer hoe u Content Transfer Tool gebruikt om de inhoud te migreren naar AEM as a Cloud Service (auteur/publiceren)."
>additional-url="https://video.tv.adobe.com/v/35460/?quality=12&amp;learn=on" text=" Zie demo"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/content-transfer-tool.html?lang=nl-NL#migration" text="Zelfstudie - gebruik van het gereedschap Inhoud overbrengen"

De volgende sectie is van toepassing op de nieuwe versie van het gereedschap Inhoud overbrengen. Ga als volgt te werk om te leren hoe u inhoud kunt migreren naar AEM as a Cloud Service met het gereedschap Inhoud overbrengen:

### Installatiefase voor extractie {#extraction-setup-phase}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_extraction_setup"
>title="Installatiefase voor extractie"
>abstract="Leer hoe u een migratieset maakt en beheert en hoe u de extractiesleutel kopieert."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/content-transfer-tool.html?lang=nl-NL#migration" text="Zelfstudie - gebruik van het gereedschap Inhoud overbrengen"

<!-- Contextualhelp id "aemcloud_ctt_extraction_setup" must be added here -->

1. Meld u aan bij Cloud Acceleration Manager (CAM) en klik op het CAM-project dat u eerder hebt gemaakt om te beoordelen of u klaar bent om naar AEM as a Cloud Service te gaan. Als u geen CAM project hebt gecreeerd, verwijs naar het Creëren van en het Leiden van een Project in CAM.

1. Klik de **kaart van de Overdracht van de Inhoud 0&rbrace; &lbrace;om de Vastgestelde mening van de Lijst van de Migratie te openen.**

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam1.png)

1. Creeer een Migratie die door **wordt geplaatst te klikken leidt de Reeks van de Migratie**.

   >[!NOTE]
   >
   >Per project in Cloud Acceleration Manager kunnen maximaal 10 migratiesets worden gemaakt, inclusief verlopen sets.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam2.png)

   Het volgende dialoogvenster wordt weergegeven. Een migratieset verloopt na een langdurige periode van inactiviteit. Nadat de waarschuwingen op de projectkaart en de rijen van de migratietabel voor een tijdspanne worden getoond, zal de migratiereeks verlopen en zijn gegevens zullen niet meer beschikbaar zijn. Het overzicht [ Vastgestelde Verval van de Migratie ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/overview-content-transfer-tool.md#migration-set-expiry) voor details.

   Tijdens het maken van de migratieset kunt u het geografische gebied kiezen waarin de tijdelijke migratiegegevens worden opgeslagen.  U wordt aangeraden het gebied te kiezen dat het dichtst bij uw doelcloud-omgeving ligt om optimale prestaties tijdens inname te garanderen.  U kunt de regio niet wijzigen nadat u de migratieset hebt gemaakt. Als u een ander gebied wilt gebruiken, moet u een nieuwe migratieset maken.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam3.png)

   >[!NOTE]
   >
   >De naam moet dezelfde conventies hebben als een AEM-knooppunt, zodat deze geen van de volgende tekens kan bevatten: `. / : [ ] | * < > ^ ? { } % # ` of ongebruikelijke symbolen of emojis.

1. De migratielijst wordt nu weergegeven in de lijstweergave. Selecteer het drie puntensymbool (**...**) om drop-down te openen en **de sleutel van de Extractie van het Extractie van het Exemplaar te selecteren**. U hebt deze sleutel nodig tijdens de extractiefase. Kopieer deze extractietoets.

   >[!NOTE]
   >
   >Met de extractietoets kan uw AEM-bronomgeving veilig verbinding maken met de migratieset. Behandel deze sleutel met de zelfde zorg die u een wachtwoord zou, en nooit het over een onbeveiligd middel zoals e-mail delen.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam4.png)

### De migratieset vullen {#populating-the-migration-set}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_populate_migrationset"
>title="Migratieset vullen"
>abstract="Nadat u een migratieset hebt gemaakt, moet deze zijn gevuld met de inhoud van de broninstantie die naar de AEM as a Cloud Service-omgeving moet worden verplaatst. Hiervoor moet het gereedschap Inhoud overbrengen op de broninstantie zijn geïnstalleerd."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/extracting-content.html?lang=nl-NL" text="Inhoud uitnemen"

Als u de migratieset die u in de Cloud Acceleration Manager hebt gemaakt, wilt vullen, installeert u de nieuwste versie van het Content Transfer Tool op uw Adobe Experience Manager-bronexemplaar (AEM). Volg deze sectie voor informatie over het vullen van de migratieset.

1. Na het installeren van de recentste versie van het Hulpmiddel van de Overdracht van de Inhoud op uw bronAdobe Experience Manager instantie, ga **Verrichtingen - de Migratie van de Inhoud**

1. Klik **creëren de Reeks van de Migratie**.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam5.png)

1. Plak de extractiesleutel die van CAM vroeger in het zeer belangrijke de inputgebied van de Extractie van **werd gekopieerd creeer de Reeks van de Migratie** vorm. Hierna worden de naam van de migratieset en de velden Cloud Acceleration Manager (CAM)-projectnaam automatisch ingevuld. Deze zouden de Vastgestelde naam van de Migratie in CAM en het CAM projectnaam moeten aanpassen die u creeerde. U kunt nu inhoudspaden toevoegen. Sla de migratieset op nadat u inhoudspaden hebt toegevoegd. U kunt de extractie uitvoeren met inbegrepen of uitgesloten versies.

   >[!NOTE]
   >
   >Zorg ervoor dat de extractietoets geldig is en niet bij het verlopen ervan is. U kunt deze informatie in **krijgen creeer de Reeks van de Migratie** dialoog nadat u de extractiesleutel kleeft. Als u een verbindingsfout krijgt, zie [ Connectiviteit van het Milieu van Source ](#source-environment-connectivity) voor meer informatie.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/createMigrationSet.png)

1. Selecteer vervolgens de volgende parameters om een migratieset te maken:

   1. **omvat Versie**: Selecteer zoals vereist. Wanneer versies worden opgenomen, wordt het pad `/var/audit` automatisch opgenomen om auditgebeurtenissen te migreren.

      ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/includeVersion.png)

      >[!NOTE]
      >Als u van plan bent versies op te nemen als onderdeel van een migratieset en aanvullende versies uitvoert met `wipe=false` , moet u versiebeheer uitschakelen vanwege een huidige beperking in het gereedschap Inhoud overbrengen. Als u versiereiniging liever ingeschakeld houdt en top-ups uitvoert in een migratieset, moet u de opname uitvoeren als `wipe=true` .

      >[!NOTE]
      >Vanaf CTT-versie (3.0.24) zijn er nieuwe functies toegevoegd aan het gereedschap Inhoud overbrengen, waardoor het proces voor het opnemen en uitsluiten van paden is verbeterd. Eerder moesten paden een voor een worden geselecteerd, wat vervelend en tijdrovend was. Gebruikers kunnen nu paden rechtstreeks vanuit de gebruikersinterface opnemen of een CSV-bestand uploaden, afhankelijk van hun voorkeur.  Het CSV-bestand moet één pad per regel hebben en geen komma.

   1. **Wegen om** te omvatten: De wegbrowser van het gebruik om wegen te selecteren die moeten worden gemigreerd. Padkiezer accepteert invoer door te typen of te selecteren. Gebruikers kunnen slechts één optie selecteren om paden op te nemen: in de gebruikersinterface of door een CSV-bestand te uploaden.
      >[!IMPORTANT]
      >Voor de volgende paden gelden beperkingen bij het maken van een migratieset:
      >* `/apps`
      >* `/libs`
      >* `/home`
      >* `/etc` (sommige `/etc` paden mogen in CTT worden geselecteerd)

      ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/includeAndExcludePath.png)

      1. Alleen padselectie is toegestaan en er moet ten minste één pad aanwezig zijn. Als er geen pad is geselecteerd, treedt een serverfout op.

         ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/ServerError.png)

      1. Wanneer het gebruiken van **CSV uploadt optie**, moet het Csv- dossier geldige wegen bevatten.

         ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/validCsvUpload.png)

      1. Om terug te schakelen naar de padkiezer, moeten gebruikers de pagina vernieuwen en opnieuw beginnen.

      1. Als **ongeldige wegen** in geupload CSV worden gevonden, zal een afzonderlijke dialoog de ongeldige wegen tonen.

         ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/invalidPathsInCsv.png)

      1. Gebruikers moeten het CSV-bestand corrigeren en het opnieuw uploaden of de gebruikersinterface vernieuwen om paden te selecteren via de padkiezer.

   1. **Wegen om worden uitgesloten**: Een nieuwe eigenschap staat gebruikers toe om specifieke wegen uit te sluiten als zij hen niet inbegrepen willen. Als het pad in de include-sectie bijvoorbeeld /content/dam is, kunnen gebruikers nu paden zoals /content/dam/catalogs uitsluiten.

      ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/excludePathHighlighted.png)

1. Klik **sparen** nadat u alle gebieden in **bevolkt creeer het 3&rbrace; detailsscherm van de Plaats van de Migratie**.

<!-- 1. You will view your migration set in the **Content Transfer** wizard, as shown in the figure below.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ctt07.png)

   All the existing migration sets are displayed on the **Content Transfer** wizard with their current status and status information. You may see some of these icons described below.

   * A *red cloud* indicates that you cannot complete the extraction process.
   * A *green cloud* indicates that you can complete the extraction process.
   * A *yellow icon* indicates that you did not create the existing migration set and the specific one is created by some other user in the same instance.

1. Select a migration set and click **Properties** to view or edit the migration set properties. While editing properties, it is not possible to change the **Migration Set name** or the **Service URL**. 

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ctt06.png) -->

### Formaat migratieset bepalen {#migration-set-size}

Nadat u een migratieset hebt gemaakt, wordt u ten zeerste aangeraden de migratieset te controleren voordat u een extractieproces start.
Als u een formaatcontrole uitvoert op de migratieset, kunt u:

* Bepaal of er voldoende schijfruimte is in de submap `crx-quickstart` om de extractie te voltooien.
* Bepaal of de grootte van de migratieset binnen de ondersteunde productgrenzen valt en vermijd mislukte inname van inhoud.

Voer de onderstaande stappen uit om een groottecontrole uit te voeren:

1. Selecteer een migratiereeks en klik **de Grootte van de Controle**.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam8.png)

1. Dit opent omhoog de **dialoog van de Grootte van de Controle**.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/checkMigrationSetSize.png)

1. Klik **Grootte van de Controle** om het proces te beginnen. U zult dan aan de de lijstmening van de migratiereeks terugkeren, en u zou een bericht moeten zien erop wijzend dat **de Grootte van de Controle** loopt.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam10.png)

1. Nadat **het proces van de Grootte van de Controle** wordt voltooid, verandert de status in **EINDELIJK**. Selecteer de zelfde migratiereeks en klik **Grootte van de Controle** om resultaten te bekijken. Hieronder is een voorbeeld van **de resultaten van de Grootte van de Controle** zonder waarschuwingen.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/checkSizeAfterFinished.png)

1. Als de **resultaten van de Grootte van de Controle** erop wijzen dat of er ontoereikende schijfruimte is, of de migratiereeks productgrenzen overschrijdt, of allebei, wordt de status van de a **WAARSCHUWING** getoond.

<!--   ![image](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image6.png)
   
   Below is an example of **Check Size** results with warnings.
 
   ![image](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image7.png) -->


## Volgende functies {#whats-next}

Nadat u hebt geleerd hoe u een migratieset kunt maken, kunt u nu meer leren over Extractie- en Ingestieprocessen in het gereedschap Inhoud overbrengen. Alvorens u deze processen leert, moet u [ Behandelend Grote Inhoudsbewaarplaatsen van de Inhoud ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md) herzien om de extractie en inname fasen van de activiteit van de inhoudsoverdracht beduidend te versnellen om inhoud naar AEM as a Cloud Service te bewegen.
