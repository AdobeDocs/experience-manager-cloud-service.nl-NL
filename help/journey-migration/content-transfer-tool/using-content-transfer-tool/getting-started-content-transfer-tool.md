---
title: Aan de slag met het gereedschap Inhoud overbrengen
description: Aan de slag met het gereedschap Inhoud overbrengen
exl-id: c0cecf65-f419-484b-9d55-3cbd561e8dcd
source-git-commit: f84806c1579f8ef163dd9454fcae4a57bf22a452
workflow-type: tm+mt
source-wordcount: '1242'
ht-degree: 7%

---

# Aan de slag met het gereedschap Inhoud overbrengen {#getting-started-content-transfer-tool}


## Beschikbaarheid {#availability}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_download"
>title="Downloaden"
>abstract="Het gereedschap Inhoud overbrengen kan als een ZIP-bestand worden gedownload van de Software Distribution Portal. U kunt het pakket via Package Manager installeren op uw AEM-broninstantie (Adobe Experience Manager). Download de nieuwste versie."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html" text="Release-opmerkingen"
>additional-url="https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html" text="Software Distribution Portal"

Het gereedschap Inhoud overbrengen kan als een ZIP-bestand worden gedownload van de Software Distribution Portal. U kunt het pakket installeren via [Pakketbeheer](/help/implementing/developing/tools/package-manager.md) op uw Adobe Experience Manager-bronexemplaar (AEM). Download de nieuwste versie. Raadpleeg voor meer informatie over de nieuwste versie [Opmerkingen bij de release](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html).

>[!NOTE]
>Download de Content Transfer-tool van de [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)-portal.

## Connectiviteit bronomgeving {#source-environment-connectivity}

>[!NOTE]
>
>Er kan ook een verbindingsfout optreden als een migratieset is verwijderd uit Cloud Acceleration Manager.

De bron AEM instantie kan achter een firewall lopen waar het slechts bepaalde gastheren kan bereiken die aan een Lijst van gewenste personen zijn toegevoegd. Als u een extractie wilt uitvoeren, moeten de volgende eindpunten toegankelijk zijn vanaf de instantie die AEM uitvoert:

* Het doel AEM de as a Cloud Service omgeving: `author-p<program_id>-e<env_id>.adobeaemcloud.com`
* De Azure-opslagservice: `*.blob.core.windows.net`
* Het eindpunt van de Toewijzing van de Gebruiker IO: `usermanagement.adobe.io`

Om connectiviteit aan het doel AEM as a Cloud Service milieu te testen, geef het volgende cURL bevel van shell van de broninstantie uit (vervang `program_id`, `environment_id`, en `migration_token`):

`curl -i https://author-p<program_id>-e<environment_id>.adobeaemcloud.com/api/migration/migrationSet -H "Authorization: Bearer <migration_token>"`

>[!NOTE]
>Als een `HTTP/2 200` is ontvangen, is een verbinding met AEM as a Cloud Service gelukt.

## De Content Transfer-tool uitvoeren {#running-tool}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_demo"
>title="Gereedschap Inhoud overbrengen uitvoeren"
>abstract="Leer hoe u Inhoud overbrengen kunt gebruiken om de inhoud te migreren naar AEM as a Cloud Service (Auteur/Publiceren)."
>additional-url="https://video.tv.adobe.com/v/35460/?quality=12&amp;learn=on" text=" Zie demo"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/content-transfer-tool.html?lang=en#migration" text="Zelfstudie - gebruik van het gereedschap Inhoud overbrengen"

>[!VIDEO](https://video.tv.adobe.com/v/35460/?quality=12&learn=on)
<!-- Need to remove the video -->

De volgende sectie is van toepassing op de nieuwe versie van het gereedschap Inhoud overbrengen. Ga als volgt te werk om te leren hoe u met het gereedschap Inhoud overbrengen inhoud kunt migreren naar AEM as a Cloud Service:

### Installatiefase voor extractie {#extraction-setup-phase}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_extraction_setup"
>title="Installatiefase voor extractie"
>abstract="Leer hoe u een migratieset maakt en de extractietoets kopieert."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/content-transfer-tool.html?lang=en#migration" text="Zelfstudie - gebruik van het gereedschap Inhoud overbrengen"

<!-- Contextualhelp id "aemcloud_ctt_extraction_setup" needs to be added here -->

1. Meld u aan bij Cloud Acceleration Manager (CAM) en klik op het CAM-project dat u eerder hebt gemaakt om te beoordelen of u klaar bent om naar AEM as a Cloud Service te gaan. Als u geen CAM project hebt gecreeerd, verwijs naar het Creëren van en het Leiden van een Project in CAM.

1. Klik op de knop **Inhoud overbrengen** kaart. Hiermee gaat u naar de weergave Lijst migratieset.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam1.png)

1. Een migratieset maken door op **Migratieset maken**.

   >[!NOTE]
   >
   >Per project kunnen maximaal vijf migratiesets worden gemaakt in Cloud Acceleration Manager.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam2.png)

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam3.png)

1. De migratielijst wordt nu weergegeven in de lijstweergave. Klik op het symbool van de drie stippen (**...**) om het vervolgkeuzemenu te openen en op **Extractietoets kopiëren**. U hebt deze sleutel nodig tijdens de extractiefase. Kopieer deze extractietoets.

   >[!NOTE]
   >
   >Met de extractietoets kan uw AEM omgeving veilig verbinding maken met de migratieset. Behandel deze sleutel met dezelfde zorg als een wachtwoord en deel deze nooit via een onbeveiligd medium, zoals een e-mail.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam4.png)

### De migratieset vullen {#populating-the-migration-set}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_populate_migrationset"
>title="Populate de Reeks van de Migratie&quot; abstract=&quot;Na het creëren van een migratiereeks moet het met de inhoud van de broninstantie worden bevolkt die moet worden verplaatst naar het AEM as a Cloud Service milieu. Hiervoor moet het gereedschap Inhoud overbrengen op de broninstantie zijn geïnstalleerd."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/extracting-content.html" text="Inhoud uitnemen"

Als u de migratieset wilt vullen die u hebt gemaakt in de Cloud Acceleration Manager, moet u de nieuwste versie van het Content Transfer Tool installeren op uw Adobe Experience Manager-broninstantie (AEM). Volg deze sectie om te leren hoe u de migratieset kunt vullen.

1. Nadat u de meest recente versie (Vxxx) van het Content Transfer Tool op uw Adobe Experience Manager-bronexemplaar hebt geïnstalleerd, gaat u naar **Bewerkingen - Inhoud migreren**

1. Klikken op **Migratieset maken**

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam5.png)

1. Plak de extractietoets die eerder uit CAM is gekopieerd naar het invoerveld Extractietoets van **Migratieset maken** formulier. Als u dit doet, worden de namen van de migratieset en de projectnamen van de CAM (Cloud Acceleration Manager) automatisch ingevuld. Deze zouden de Vastgestelde naam van de Migratie in CAM en het CAM projectnaam moeten aanpassen die u creeerde. U kunt nu inhoudspaden toevoegen. Nadat u inhoudspaden hebt toegevoegd, kunt u de migratieset opslaan. U kunt de extractie uitvoeren met inbegrepen of uitgesloten versies.

   >[!NOTE]
   >
   >Zorg ervoor dat de extractietoets geldig is en niet dicht bij het verlopen ervan is. U kunt deze gegevens ophalen in het dialoogvenster **Migratieset maken** nadat u de extractietoets hebt geplakt. Als er een verbindingsfout optreedt, raadpleegt u [Connectiviteit bronomgeving](#source-environment-connectivity) voor meer informatie .

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam6.png)

1. Selecteer vervolgens de volgende parameters om een migratieset te maken:

   1. **Include Version**: Selecteer de versie die u wilt opnemen. Wanneer versies worden opgenomen, wordt het pad `/var/audit` wordt automatisch opgenomen om auditgebeurtenissen te migreren.

      ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam7.png)

      >[!NOTE]
      >Als u van plan bent versies op te nemen als onderdeel van een migratieset en als u aanvullende versies uitvoert met `wipe=false`Vervolgens moet u versiebeheer uitschakelen vanwege een huidige beperking in het gereedschap Inhoud overbrengen. Als u versiereiniging liever ingeschakeld wilt houden en extra-ups wilt uitvoeren in een migratieset, moet u de opname uitvoeren als `wipe=true`.


   1. **Paths to be included**: Gebruik de padbrowser om paden te selecteren die moeten worden gemigreerd. Padkiezer accepteert invoer door te typen of te selecteren.

      >[!IMPORTANT]
      >Voor de volgende paden gelden beperkingen bij het maken van een migratieset:
      >* `/apps`
      >* `/libs`
      >* `/home`
      >* `/etc` (sommige `/etc` paden mogen worden geselecteerd in CTT)


1. Klikken op **Opslaan** nadat u alle velden in het dialoogvenster **Migratieset maken** detailscherm.

<!-- 1. You will view your migration set in the **Content Transfer** wizard, as shown in the figure below.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ctt07.png)

   All the existing migration sets are displayed on the **Content Transfer** wizard with their current status and status information. You may see some of these icons described below.

   * A *red cloud* indicates that you cannot complete the extraction process.
   * A *green cloud* indicates that you can complete the extraction process.
   * A *yellow icon* indicates that you did not create the existing migration set and the specific one is created by some other user in the same instance.

1. Select a migration set and click on **Properties** to view or edit the migration set properties. While editing properties, it is not possible to change the **Migration Set name** or the **Service URL**. 

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ctt06.png) -->

### Formaat migratieset bepalen {#migration-set-size}

Nadat u een migratieset hebt gemaakt, wordt u ten zeerste aangeraden de migratieset te controleren voordat u een extractieproces start.
Als u een formaatcontrole uitvoert op de migratieset, kunt u:
* Bepalen of er voldoende schijfruimte is in het dialoogvenster `crx-quickstart` subdirectory om extractie te voltooien.
* Bepaal of de grootte van de migratieset binnen de ondersteunde productgrenzen valt en vermijd mislukte inname van inhoud.

Voer de onderstaande stappen uit om een groottecontrole uit te voeren:

1. Selecteer een migratieset en klik op **Formaat controleren**.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam8.png)

1. Hierdoor wordt de **Formaat controleren** .

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam9.png)

1. Klikken op **Formaat controleren** om het proces te starten. Vervolgens keert u terug naar de lijstweergave van de migratieset. Er wordt dan een bericht weergegeven dat aangeeft dat **Formaat controleren** wordt uitgevoerd.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam10.png)

1. Eenmaal **Formaat controleren** -proces is voltooid, verandert de status in **VOLTOOID**. Selecteer dezelfde migratieset en klik op **Formaat controleren** om de resultaten weer te geven. Hieronder ziet u een voorbeeld van **Formaat controleren** resultaten zonder waarschuwingen.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam11.png)

1. Als de **Formaat controleren** de resultaten wijzen erop dat er onvoldoende schijfruimte is en/of dat de migratie de productlimieten overschrijdt; **WAARSCHUWING** status wordt weergegeven.

<!--   ![image](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image6.png)
   
   Below is an example of **Check Size** results with warnings.
 
   ![image](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image7.png) -->


## Volgende functies {#whats-next}

Nadat u hebt geleerd hoe u een migratieset kunt maken, kunt u nu meer leren over Extractie- en Ingestieprocessen in het gereedschap Inhoud overbrengen. Voordat u deze processen leert, moet u controleren [Afhandeling van grote opslagplaatsen voor inhoud](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en) om de extractie- en innamefasen van de activiteit voor de overdracht van inhoud aanzienlijk te versnellen en de inhoud naar AEM as a Cloud Service te verplaatsen.
