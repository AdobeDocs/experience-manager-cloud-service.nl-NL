---
title: Aan de slag met het gereedschap Inhoud overbrengen
description: Aan de slag met het gereedschap Inhoud overbrengen
exl-id: a19b8424-33ab-488a-91b3-47f0d3c8abf5
source-git-commit: eae5b6a8903f68d4736e44db9a9e598716a15b75
workflow-type: tm+mt
source-wordcount: '776'
ht-degree: 30%

---

# Aan de slag met het gereedschap Inhoud overbrengen {#getting-started-content-transfer-tool}

## Beschikbaarheid {#availability}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_download"
>title="Downloaden"
>abstract="Het gereedschap Inhoud overbrengen kan als een ZIP-bestand worden gedownload van de Software Distribution Portal. U kunt het pakket via Package Manager installeren op uw AEM-broninstantie (Adobe Experience Manager). Download de nieuwste versie."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html" text="Release-opmerkingen"
>additional-url="https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html" text="Software Distribution Portal"

Het gereedschap Inhoud overbrengen kan als een ZIP-bestand worden gedownload van de Software Distribution Portal. U kunt het pakket via Package Manager installeren op uw AEM-broninstantie (Adobe Experience Manager). Download de nieuwste versie. Raadpleeg [Opmerkingen bij de release](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html) voor meer informatie over de nieuwste versie.

>[!NOTE]
>Download de Content Transfer-tool van de [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)-portal.

## De Content Transfer-tool uitvoeren {#running-tool}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_demo"
>title="Gereedschap Inhoud overbrengen uitvoeren"
>abstract="Leer hoe u Inhoud overbrengen kunt gebruiken om de inhoud te migreren naar AEM as a Cloud Service (Auteur/Publiceren)."
>additional-url="https://video.tv.adobe.com/v/35460/?quality=12&amp;learn=on" text=" Zie demo"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/content-transfer-tool.html?lang=en#migration" text="Zelfstudie - gebruik van het gereedschap Inhoud overbrengen"

>[!VIDEO](https://video.tv.adobe.com/v/35460/?quality=12&learn=on)


In deze sectie leert u hoe u de Content Transfer-tool gebruikt om content te migreren naar AEM as a Cloud Service (Auteur/Publiceren):

1. Selecteer de Adobe Experience Manager en navigeer naar gereedschappen -> **Bewerkingen** -> **Inhoud migreren**.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ctt01.png)

1. Selecteer de optie **Content Transfer** van de wizard **Content Migration**.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ctt02.png)


1. De onderstaande console wordt weergegeven wanneer u de eerste migratieset maakt. Klik op **Create Migration Set** om een nieuwe migratieset te maken.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ctt03.png)

   >[!NOTE]
   >Als u bestaande migratiesets hebt, zal de console de lijst van bestaande migratiesets met hun huidige status tonen.


1. Vul de velden in **Migratieset maken** scherm, zoals hieronder wordt beschreven.

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
      >U kunt het toegangstoken terugwinnen door **open toegangstoken** te gebruiken knoop. U moet ervoor zorgen dat u tot de groep van AEM beheerders in de instantie van de doelCloud Service behoort.

   1. **Parameters**: Selecteer de volgende parameters om de migratieset te maken:

      1. **Include Version**: Selecteer de versie die u wilt opnemen. Wanneer versies worden opgenomen, wordt het pad `/var/audit` automatisch opgenomen om auditgebeurtenissen te migreren.

      ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ctt05.png)

      >[!NOTE]
      >Als u van plan bent versies op te nemen als onderdeel van een migratieset en extra-ups uitvoert met `wipe=false`, dan moet u versiezuivering uitschakelen vanwege een huidige beperking in het gereedschap Inhoud overbrengen. Als u versiereiniging liever ingeschakeld houdt en top-ups uitvoert in een migratieset, moet u de opname uitvoeren als `wipe=true`.

      1. **Toewijzing van IMS-gebruikers en -groepen** opnemen: Selecteer de optie om toewijzingen van gebruikers en groepen IMS op te nemen.
Raadpleeg [Hulpprogramma voor gebruikerstoewijzing](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html) voor meer informatie.

      1. **Paths to be included**: Gebruik de padbrowser om paden te selecteren die moeten worden gemigreerd. Padkiezer accepteert invoer door te typen of te selecteren.

         >[!IMPORTANT]
         >Voor de volgende paden gelden beperkingen bij het maken van een migratieset:
         >* `/apps`
         >* `/libs`
         >* `/home`
         >* `/etc` (sommige  `/etc` paden mogen worden geselecteerd in CTT)




1. Klik op **Save** nadat u alle velden in het **Create Migration Set** detailscherm vult.

1. U zult uw migratie bekijken die in **de tovenaar van de Overdracht van de Inhoud** wordt geplaatst, zoals aangetoond in het hieronder cijfer.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ctt07.png)

   Alle bestaande migratiesets worden weergegeven op de wizard **Inhoud overbrengen** met hun huidige status en statusinformatie. Sommige van deze pictogrammen worden hieronder beschreven.

   * Een *rode wolk* geeft aan dat u het extractieproces niet kunt voltooien.
   * Een *groene cloud* geeft aan dat u het extractieproces kunt voltooien.
   * Een *geel pictogram* geeft aan dat u de bestaande migratieset niet hebt gemaakt en dat de specifieke migratieset door een andere gebruiker in dezelfde instantie wordt gemaakt.

1. Selecteer een migratieset en klik op **Eigenschappen** om de eigenschappen van de migratieset weer te geven of te bewerken. Tijdens het bewerken van eigenschappen is het niet mogelijk de naam **Migratieset** of **Service URL** te wijzigen.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ctt06.png)


## Volgende functies {#whats-next}

Nadat u hebt geleerd hoe u een migratieset kunt maken, kunt u nu meer leren over Extractie- en Ingestieprocessen in het gereedschap Inhoud overbrengen. Voordat u deze processen leert, moet u [Omgaan met grote opslagplaatsen voor inhoud](help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md) doornemen om de extractie- en insluitingsfasen van de activiteit voor inhoudsoverdracht aanzienlijk te versnellen en de inhoud naar AEM as a Cloud Service te verplaatsen.
