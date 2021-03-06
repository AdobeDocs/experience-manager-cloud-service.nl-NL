---
title: Aan de slag met Content Transfer Tool (verouderd)
description: Aan de slag met het gereedschap Inhoud overbrengen
hide: true
hidefromtoc: true
source-git-commit: 1fb4d0f2a3b3f9a27f5ab1228ec2d419149e0764
workflow-type: tm+mt
source-wordcount: '966'
ht-degree: 20%

---

# Aan de slag met Content Transfer Tool (verouderd) {#getting-started-content-transfer-tool}


## Beschikbaarheid {#availability}

Het gereedschap Inhoud overbrengen kan als een ZIP-bestand worden gedownload van de Software Distribution Portal. U kunt het pakket installeren via [Pakketbeheer](/help/implementing/developing/tools/package-manager.md) op uw Adobe Experience Manager-bronexemplaar (AEM). Download de nieuwste versie. Raadpleeg voor meer informatie over de nieuwste versie [Opmerkingen bij de release](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html).

>[!NOTE]
>Download de Content Transfer-tool van de [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)-portal.

## Connectiviteit bronomgeving {#source-environment-connectivity}

De bron AEM instantie kan achter een firewall lopen waar het slechts bepaalde gastheren kan bereiken die aan een Lijst van gewenste personen zijn toegevoegd. Als u een extractie wilt uitvoeren, moeten de volgende eindpunten toegankelijk zijn vanaf de instantie die AEM uitvoert:

* Het doel AEM de as a Cloud Service omgeving: `author-p<program_id>-e<env_id>.adobeaemcloud.com`
* De Azure-opslagservice: `*.blob.core.windows.net`
* Het eindpunt van de Toewijzing van de Gebruiker IO: `usermanagement.adobe.io`

Om connectiviteit aan het doel AEM as a Cloud Service milieu te testen, geef het volgende cURL bevel van shell van de broninstantie uit (vervang `program_id`, `environment_id`, en `migration_token`):

`curl -i https://author-p<program_id>-e<environment_id>.adobeaemcloud.com/api/migration/migrationSet -H "Authorization: Bearer <migration_token>"`

>[!NOTE]
>Als een `HTTP/2 200` is ontvangen, is een verbinding met AEM as a Cloud Service gelukt.

## De Content Transfer-tool uitvoeren {#running-tool}

>[!VIDEO](https://video.tv.adobe.com/v/35460/?quality=12&learn=on)


In deze sectie leert u hoe u de Content Transfer-tool gebruikt om content te migreren naar AEM as a Cloud Service (Auteur/Publiceren):

1. Selecteer de Adobe Experience Manager en navigeer naar de gereedschappen -> **Bewerkingen** -> **Inhoud migreren**.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/ctt01.png)

1. Selecteer **Inhoud overbrengen** optie van **Inhoud migreren** wizard.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/ctt02.png)


1. De onderstaande console wordt weergegeven wanneer u de eerste migratieset maakt. Klik op **Create Migration Set** om een nieuwe migratieset te maken.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/ctt03.png)

   >[!NOTE]
   >Als u bestaande migratiesets hebt, zal de console de lijst van bestaande migratiesets met hun huidige status tonen.


1. Vul de velden in **Migratieset maken** scherm, zoals hieronder beschreven.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/ctt04.png)

   1. **Name**: Voer de naam van de migratieset in.
      >[!NOTE]
      >Er zijn geen speciale tekens toegestaan voor de naam van de migratieset.

   1. **Cloud Service Configuration**: Voer de doelversie in van de auteur-URL voor AEM as a Cloud Service.

      >[!NOTE]
      >U kunt maximaal tien migratiesets tegelijk maken en onderhouden tijdens de activiteit voor de overdracht van inhoud.
      >Bovendien moet u voor elke specifieke omgeving een afzonderlijke migratie maken: *stage*, *ontwikkeling* of *productie*.

   1. **Access Token**: Voer het toegangstoken in.

      >[!NOTE]
      >U kunt het toegangstoken terugwinnen door **Toegangstoken openen** knop. U moet ervoor zorgen dat u tot de groep van &quot;Beheerders&quot;in de instantie van de doelCloud Service behoort.

   1. **Parameters**: Selecteer de volgende parameters om de migratieset te maken:

      1. **Include Version**: Selecteer de versie die u wilt opnemen. Wanneer versies worden opgenomen, wordt het pad `/var/audit` wordt automatisch opgenomen om auditgebeurtenissen te migreren.

         ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/ctt05.png)

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

1. U ziet de migratie die is ingesteld in het dialoogvenster **Inhoud overbrengen** zoals weergegeven in de onderstaande afbeelding.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/ctt07.png)

   Alle bestaande migratiesets worden weergegeven op de **Inhoud overbrengen** met hun huidige status en statusinformatie. Sommige van deze pictogrammen worden hieronder beschreven.

   * Een *rode wolk* geeft aan dat u het extractieproces niet kunt voltooien.
   * A *groene wolk* Hiermee wordt aangegeven dat u het extractieproces kunt voltooien.
   * Een *geel pictogram* geeft aan dat u de bestaande migratieset niet hebt gemaakt en dat de specifieke migratieset door een andere gebruiker in dezelfde instantie wordt gemaakt.

1. Selecteer een migratieset en klik op **Eigenschappen** om de eigenschappen van de migratieset weer te geven of te bewerken. Tijdens het bewerken van eigenschappen is het niet mogelijk om de **Naam migratieset** of de **Service-URL**.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/ctt06.png)

### Grootte en schijfruimte van migratieset bepalen {#migration-set-size}

Nadat u een migratieset hebt gemaakt, wordt u ten zeerste aangeraden de migratieset te controleren voordat u een extractieproces start.
Als u een formaatcontrole uitvoert op de migratieset, kunt u:
* Bepalen of er voldoende schijfruimte is in het dialoogvenster `crx-quickstart` subdirectory om extractie te voltooien.
* Bepaal of de grootte van de migratieset binnen de ondersteunde productgrenzen valt en vermijd mislukte inname van inhoud.

Voer de onderstaande stappen uit om een groottecontrole uit te voeren:

1. Selecteer een migratieset en klik op **Formaat controleren**.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image1.png)

1. Hierdoor wordt de **Formaat controleren** .

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image2.png)

1. Klikken op **Formaat controleren** om het proces te starten. Vervolgens keert u terug naar de lijstweergave van de migratieset. Er wordt dan een bericht weergegeven dat aangeeft dat **Formaat controleren** wordt uitgevoerd.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image3.png)


1. Eenmaal **Formaat controleren** proces is voltooid, verandert de status in **VOLTOOID**. Selecteer dezelfde migratieset en klik op **Formaat controleren** om de resultaten weer te geven.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image4.png)

   Hieronder ziet u een voorbeeld van **Formaat controleren** resultaten zonder waarschuwingen.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image5.png)

1. Als de **Formaat controleren** de resultaten wijzen erop dat er onvoldoende schijfruimte is en/of dat de migratie de productlimieten overschrijdt; **WAARSCHUWING** status wordt weergegeven.

![afbeelding](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image6.png)

Hieronder ziet u een voorbeeld van **Formaat controleren** resultaten met waarschuwingen.

![afbeelding](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image7.png)


## Volgende functies {#whats-next}

Nadat u hebt geleerd hoe u een migratieset kunt maken, kunt u nu meer leren over Extractie- en Ingestieprocessen in het gereedschap Inhoud overbrengen. Voordat u deze processen leert, moet u controleren [Afhandeling van grote opslagplaatsen voor inhoud](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en) om de extractie- en innamefasen van de activiteit voor de overdracht van inhoud aanzienlijk te versnellen en de inhoud naar AEM as a Cloud Service te verplaatsen.
