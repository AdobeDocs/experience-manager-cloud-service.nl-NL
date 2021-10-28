---
title: Aan de slag met het gereedschap Inhoud overbrengen
description: Aan de slag met het gereedschap Inhoud overbrengen
exl-id: a19b8424-33ab-488a-91b3-47f0d3c8abf5
source-git-commit: d8c9373da79b46d32f8da37b4dfeae815348ae8a
workflow-type: tm+mt
source-wordcount: '860'
ht-degree: 27%

---

# Getting Started with Content Transfer Tool {#getting-started-content-transfer-tool}

## Connectiviteit bronomgeving {#source-environment-connectivity}

De bron AEM instantie kan achter een firewall lopen waar het slechts bepaalde gastheren kan bereiken die aan een Lijst van gewenste personen zijn toegevoegd. Als u een extractie wilt uitvoeren, moeten de volgende eindpunten toegankelijk zijn vanaf de instantie die AEM uitvoert:

* Het doel AEM de as a Cloud Service omgeving: `author-p<program_id>-e<env_id>.adobeaemcloud.com`
* The Azure blob storage service: `*.blob.core.windows.net`
* Het eindpunt van de Toewijzing van de Gebruiker IO: `usermanagement.adobe.io`

Om connectiviteit aan het doel AEM as a Cloud Service milieu te testen, geef het volgende cURL bevel van shell van de broninstantie uit (vervang `program_id`, `environment_id`, en `migration_token`):

`curl -i https://author-p<program_id>-e<environment_id>.adobeaemcloud.com/api/migration/migrationSet -H "Authorization: Bearer <migration_token>"`


>[!NOTE]
>Als een `HTTP/2 200` is ontvangen, is een verbinding met AEM as a Cloud Service gelukt.

## Beschikbaarheid {#availability}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_download"
>title="Downloaden"
>abstract="Het gereedschap Inhoud overbrengen kan als een ZIP-bestand worden gedownload van de Software Distribution Portal. U kunt het pakket via Package Manager installeren op uw AEM-broninstantie (Adobe Experience Manager). Download de nieuwste versie."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html" text="Release-opmerkingen"
>additional-url="https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html" text="Software Distribution Portal"

Het gereedschap Inhoud overbrengen kan als een ZIP-bestand worden gedownload van de Software Distribution Portal. U kunt het pakket via Package Manager installeren op uw AEM-broninstantie (Adobe Experience Manager). Download de nieuwste versie. Raadpleeg voor meer informatie over de nieuwste versie [Opmerkingen bij de release](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html).

>[!NOTE]
>Download de Content Transfer-tool van de [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)-portal.

## De Content Transfer-tool uitvoeren {#running-tool}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_demo"
>title="Gereedschap Inhoud overbrengen uitvoeren"
>abstract="Learn how to use Content Transfer Tool to migrate the content to AEM as a Cloud Service (Author/Publish)."
>additional-url="https://video.tv.adobe.com/v/35460/?quality=12&amp;learn=on" text=" See Demo"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/content-transfer-tool.html?lang=en#migration" text="Zelfstudie - gebruik van het gereedschap Inhoud overbrengen"

>[!VIDEO](https://video.tv.adobe.com/v/35460/?quality=12&learn=on)


In deze sectie leert u hoe u de Content Transfer-tool gebruikt om content te migreren naar AEM as a Cloud Service (Auteur/Publiceren):

1. Selecteer de Adobe Experience Manager en navigeer naar de gereedschappen -> **Bewerkingen** -> **Inhoud migreren**.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ctt01.png)

1. Selecteer **Inhoud overbrengen** optie van **Inhoud migreren** wizard.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ctt02.png)


1. The console below appears when you create the first migration set. Klik op **Create Migration Set** om een nieuwe migratieset te maken.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ctt03.png)

   >[!NOTE]
   >If you have existing migration sets, the console will display the list of existing migration sets with their current status.


1. Vul de velden in **Migratieset maken** scherm, zoals hieronder beschreven.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ctt04.png)

   1. **Name**: Voer de naam van de migratieset in.
      >[!NOTE]
      >Er zijn geen speciale tekens toegestaan voor de naam van de migratieset.

   1. **Cloud Service Configuration**: Voer de doelversie in van de auteur-URL voor AEM as a Cloud Service.

      >[!NOTE]
      >U kunt maximaal tien migratiesets tegelijk maken en onderhouden tijdens de activiteit voor de overdracht van inhoud.
      >Bovendien moet u voor elke specifieke omgeving een afzonderlijke migratie maken: *stage*, *ontwikkeling* of *productie*.

   1. **Access Token**: Voer het toegangstoken in.

      >[!NOTE]
      >U kunt het toegangstoken terugwinnen door **Toegangstoken openen** knop. U moet ervoor zorgen dat u tot de groep van AEM beheerders in de instantie van de doelCloud Service behoort.

   1. **Parameters**: Selecteer de volgende parameters om de migratieset te maken:

      1. **Include Version**: Selecteer de versie die u wilt opnemen. When versions are included, the path `/var/audit` is automatically included to migrate audit events.

         ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ctt05.png)

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

1. You will view your migration set in the **Content Transfer** wizard, as shown in the figure below.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ctt07.png)

   All the existing migration sets are displayed on the **Content Transfer** wizard with their current status and status information. Sommige van deze pictogrammen worden hieronder beschreven.

   * Een *rode wolk* geeft aan dat u het extractieproces niet kunt voltooien.
   * A *groene wolk* Hiermee wordt aangegeven dat u het extractieproces kunt voltooien.
   * Een *geel pictogram* geeft aan dat u de bestaande migratieset niet hebt gemaakt en dat de specifieke migratieset door een andere gebruiker in dezelfde instantie wordt gemaakt.

1. Selecteer een migratieset en klik op **Eigenschappen** om de eigenschappen van de migratieset weer te geven of te bewerken. Tijdens het bewerken van eigenschappen is het niet mogelijk om de **Naam migratieset** of de **Service-URL**.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ctt06.png)


## Volgende functies {#whats-next}

Once you have learned how to create a migration set, you are now ready to learn about Extraction and Ingestion Processes in Content Transfer Tool. Before you learn these processes, you must review [Handling Large Content Repositories](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en) to significantly speed up the extraction and ingestion phases of the content transfer activity to move content to AEM as a Cloud Service.
