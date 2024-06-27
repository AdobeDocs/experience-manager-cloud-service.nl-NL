---
title: Aan de slag met het gereedschap Inhoud overbrengen
description: Leer hoe u aan de slag kunt met het gereedschap Inhoud overbrengen
exl-id: c0cecf65-f419-484b-9d55-3cbd561e8dcd
feature: Migration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1362'
ht-degree: 2%

---

# Aan de slag met het gereedschap Inhoud overbrengen {#getting-started-content-transfer-tool}


## Beschikbaarheid {#availability}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_download"
>title="Downloaden"
>abstract="Het gereedschap Inhoud overbrengen kan als een ZIP-bestand worden gedownload van de Software Distribution Portal. U kunt het pakket via Package Manager installeren op uw Adobe Experience Manager-bronexemplaar (AEM). Download de nieuwste versie."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/release-notes/release-notes-current.html" text="Release-opmerkingen"
>additional-url="https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html" text="Software Distribution Portal"

Het gereedschap Inhoud overbrengen kan als een ZIP-bestand worden gedownload van de Software Distribution Portal. U kunt het pakket installeren door [Pakketbeheer](/help/implementing/developing/tools/package-manager.md) op uw bron-Adobe Experience Manager (AEM)-exemplaar. Download de nieuwste versie. Ga voor meer informatie over de nieuwste versie naar [Opmerkingen bij de release](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/release-notes/release-notes-current.html).

Alleen versie 2.0.0 en hoger wordt ondersteund en het is raadzaam de meest recente versie te gebruiken.

>[!NOTE]
>Download de Content Transfer-tool van de [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)-portal.

## Connectiviteit Source-omgeving {#source-environment-connectivity}

>[!NOTE]
>
>Er kan ook een verbindingsfout optreden als een migratieset uit Cloud Acceleration Manager is verwijderd.

De bron AEM instantie kan achter een firewall lopen waar het slechts bepaalde gastheren kan bereiken die aan een Lijst van gewenste personen zijn toegevoegd. Als u een extractie wilt uitvoeren, moeten de volgende eindpunten toegankelijk zijn vanuit de instantie die AEM uitvoert:

* De Azure-opslagservice: `casstorageprod.blob.core.windows.net`

>[!NOTE]
>Als de extractie mislukt als gevolg van de volgende fout: &quot;javax.net.ssl.SSLHandshakeException: sun.security.validator.ValidatorException: PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certificate path to requested target&quot;, kan dit worden opgelost door het relevante CA-certificaat te importeren.

### SSL-registratie inschakelen {#enable-ssl-logging}

Soms is het lastig om te begrijpen hoe problemen met SSL/TLS-verbindingen optreden. Als u verbindingsproblemen wilt oplossen tijdens een extractieproces, kunt u SSL-logboekregistratie inschakelen via de systeemconsole van de AEM omgeving door de volgende stappen uit te voeren:

1. Navigeer naar de Adobe Experience Manager Web Console op uw broninstantie door naar **Gereedschappen > Bewerkingen > Webconsole** of rechtstreeks naar de URL op *https://serveraddress:serverport/system/console/configMgr*
1. Zoeken naar **Configuratie van de service Content Transfer Tool Extraction**
1. Gebruik de knop voor het potloodpictogram om de configuratiewaarden ervan te bewerken
1. De optie **SSL-registratie inschakelen voor extractie** instellen en vervolgens op **Opslaan**:

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets/enable_ssl_logging.png)

>[!NOTE]
>Deze markering is alleen voor foutopsporing in SSL-problemen. Zorg ervoor dat de markering is uitgeschakeld voordat u de extractie uitvoert, omdat dit veel schijfruimte kan vereisen. Hierdoor kan de stationscapaciteit worden gevuld en kan het extractieproces mislukken.

## Het gereedschap Inhoud overbrengen uitvoeren {#running-tool}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_demo"
>title="Gereedschap Inhoud overbrengen uitvoeren"
>abstract="Leer hoe u Content Transfer Tool gebruikt om de inhoud te migreren naar AEM as a Cloud Service (Author/Publish)."
>additional-url="https://video.tv.adobe.com/v/35460/?quality=12&amp;learn=on" text=" Zie demo"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/content-transfer-tool.html#migration" text="Zelfstudie - gebruik van het gereedschap Inhoud overbrengen"

De volgende sectie is van toepassing op de nieuwe versie van het gereedschap Inhoud overbrengen. Ga als volgt te werk om te leren hoe u inhoud kunt migreren naar AEM as a Cloud Service met het gereedschap Inhoud overbrengen:

### Installatiefase voor extractie {#extraction-setup-phase}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_extraction_setup"
>title="Installatiefase voor extractie"
>abstract="Leer hoe u een migratieset maakt en beheert en hoe u de extractiesleutel kopieert."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/content-transfer-tool.html#migration" text="Zelfstudie - gebruik van het gereedschap Inhoud overbrengen"

<!-- Contextualhelp id "aemcloud_ctt_extraction_setup" must be added here -->

1. Meld u aan bij Cloud Acceleration Manager (CAM) en klik op het CAM-project dat u eerder hebt gemaakt om te beoordelen of u klaar bent om naar AEM as a Cloud Service te gaan. Als u geen CAM project hebt gecreeerd, verwijs naar het Creëren van en het Leiden van een Project in CAM.

1. Klik op de knop **Inhoud overbrengen** om de weergave Lijst migratieset te openen.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam1.png)

1. Een migratieset maken door op **Migratieset maken**.

   >[!NOTE]
   >
   >Per project in Cloud Acceleration Manager kunnen maximaal 20 migratiesets worden gemaakt, inclusief verlopen sets.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam2.png)

   Het volgende dialoogvenster wordt weergegeven. Een migratieset verloopt na een langdurige periode van inactiviteit. Nadat de waarschuwingen op de projectkaart en de rijen van de migratietabel voor een tijdspanne worden getoond, zal de migratiereeks verlopen en zijn gegevens zullen niet meer beschikbaar zijn. Controleren [Vervaldatum migratieset](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/overview-content-transfer-tool.md#migration-set-expiry) voor meer informatie.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam3.png)

   >[!NOTE]
   >
   >De naam moet dezelfde conventies van een AEM gebruiken, zodat deze geen van de volgende tekens kan bevatten: . / : [ ] | *

1. De migratielijst wordt nu weergegeven in de lijstweergave. Selecteer de drie puntensymbolen (**...**) om de vervolgkeuzelijst te openen en **Extractietoets kopiëren**. U hebt deze sleutel nodig tijdens de extractiefase. Kopieer deze extractietoets.

   >[!NOTE]
   >
   >Met de extractietoets kan uw AEM omgeving veilig verbinding maken met de migratieset. Behandel deze sleutel met de zelfde zorg die u een wachtwoord zou, en nooit het over een onbeveiligd middel zoals e-mail delen.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam4.png)

### De migratieset vullen {#populating-the-migration-set}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_populate_migrationset"
>title="Migratieset vullen"
>abstract="Nadat u een migratieset hebt gemaakt, moet deze zijn gevuld met de inhoud van de broninstantie die naar de AEM as a Cloud Service-omgeving moet worden verplaatst. Hiervoor moet het gereedschap Inhoud overbrengen op de broninstantie zijn geïnstalleerd."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/extracting-content.html" text="Inhoud uitnemen"

Als u de migratieset die u in de Cloud Acceleration Manager hebt gemaakt, wilt vullen, installeert u de nieuwste versie van het Content Transfer Tool op de Adobe Experience Manager-broninstantie (AEM). Volg deze sectie voor informatie over het vullen van de migratieset.

1. Nadat u de nieuwste versie van het gereedschap Inhoud overbrengen op uw Adobe Experience Manager-bronexemplaar hebt geïnstalleerd, gaat u naar **Bewerkingen - Migratie van inhoud**

1. Klikken **Migratieset maken**.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam5.png)

1. Plak de extractietoets die eerder uit CAM is gekopieerd naar het invoerveld Extractietoets van **Migratieset maken** formulier. Hierna worden de naam van de migratieset en de velden Cloud Acceleration Manager (CAM)-projectnaam automatisch ingevuld. Deze zouden de Vastgestelde naam van de Migratie in CAM en het CAM projectnaam moeten aanpassen die u creeerde. U kunt nu inhoudspaden toevoegen. Sla de migratieset op nadat u inhoudspaden hebt toegevoegd. U kunt de extractie uitvoeren met inbegrepen of uitgesloten versies.

   >[!NOTE]
   >
   >Zorg ervoor dat de extractietoets geldig is en niet bij het verlopen ervan is. U kunt deze gegevens ophalen in het dialoogvenster **Migratieset maken** nadat u de extractietoets hebt geplakt. Als er een verbindingsfout optreedt, raadpleegt u [Connectiviteit Source-omgeving](#source-environment-connectivity) voor meer informatie .

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam6.png)

1. Selecteer vervolgens de volgende parameters om een migratieset te maken:

   1. **Inclusief versie**: Selecteer de gewenste optie. Wanneer versies worden opgenomen, wordt het pad `/var/audit` wordt automatisch opgenomen om auditgebeurtenissen te migreren.

      ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam7.png)

      >[!NOTE]
      >Als u van plan bent versies op te nemen als onderdeel van een migratieset en als u aanvullende versies uitvoert met `wipe=false`Vervolgens moet u versiebeheer uitschakelen vanwege een huidige beperking in het gereedschap Inhoud overbrengen. Als u versiereiniging liever ingeschakeld wilt houden en extra-ups wilt uitvoeren in een migratieset, moet u de opname uitvoeren als `wipe=true`.


   1. **In te sluiten paden**: Gebruik padbrowser om paden te selecteren die moeten worden gemigreerd. Padkiezer accepteert invoer door te typen of te selecteren.

      >[!IMPORTANT]
      >Voor de volgende paden gelden beperkingen bij het maken van een migratieset:
      >* `/apps`
      >* `/libs`
      >* `/home`
      >* `/etc` (sommige `/etc` paden mogen worden geselecteerd in CTT)

1. Klikken **Opslaan** nadat u alle velden in het dialoogvenster **Migratieset maken** detailscherm.

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

* Bepalen of er voldoende schijfruimte is in het dialoogvenster `crx-quickstart` subdirectory om extractie te voltooien.
* Bepaal of de grootte van de migratieset binnen de ondersteunde productgrenzen valt en vermijd mislukte inname van inhoud.

Voer de onderstaande stappen uit om een groottecontrole uit te voeren:

1. Selecteer een migratieset en klik op **Formaat controleren**.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam8.png)

1. Dit opent de **Formaat controleren** in.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam9.png)

1. Klikken **Formaat controleren** om het proces te starten. Vervolgens gaat u terugkeren naar de lijstweergave van de migratieset. Er wordt dan een bericht weergegeven dat aangeeft dat **Formaat controleren** wordt uitgevoerd.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam10.png)

1. Na **Formaat controleren** proces is voltooid, verandert de status in **VOLTOOID**. Selecteer dezelfde migratieset en klik op **Formaat controleren** om de resultaten weer te geven. Hieronder ziet u een voorbeeld van **Formaat controleren** resultaten zonder waarschuwingen.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam11.png)

1. Als de **Formaat controleren** de resultaten geven aan dat er onvoldoende schijfruimte is of dat de migratie-set de productlimieten of beide overschrijdt. **WAARSCHUWING** status wordt weergegeven.

<!--   ![image](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image6.png)
   
   Below is an example of **Check Size** results with warnings.
 
   ![image](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image7.png) -->


## Volgende functies {#whats-next}

Nadat u hebt geleerd hoe u een migratieset kunt maken, kunt u nu meer leren over Extractie- en Ingestieprocessen in het gereedschap Inhoud overbrengen. Voordat u deze processen leert, moet u controleren [Afhandeling van grote opslagplaatsen voor inhoud](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md) om de extractie- en innamefasen van de activiteit voor de overdracht van inhoud aanzienlijk te versnellen en inhoud naar AEM as a Cloud Service te verplaatsen.
