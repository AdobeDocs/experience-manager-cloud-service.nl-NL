---
title: Logbestanden voor een migratieset weergeven in het gereedschap Inhoud overbrengen
description: Logbestanden voor een migratieset weergeven in het gereedschap Inhoud overbrengen
exl-id: aed1ac83-a2fb-425e-aca4-39cd0bb42fd3
feature: Migration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 9%

---

# Logboeken voor een migratieset weergeven {#view-logs-content-transfer-tool}


>[!CONTEXTUALHELP]
>id="aemcloud_ctt_logs"
>title="Logbestanden weergeven"
>abstract="Na voltooiing van Extractie van Ingestie, controleer de logboeken om het even welke fout/waarschuwingen. Fouten moeten onmiddellijk worden verholpen door de gemelde problemen te verhelpen of door contact op te nemen met de Adobe."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html#troubleshooting" text="Problemen oplossen"
>additional-url="https://helpx.adobe.com/ca/enterprise/using/support-for-experience-cloud.html" text="Contact opnemen met Adobe-ondersteuning"

Controleer na elke stap (extractie en inname) de logboeken en zoek op fouten.  Fouten moeten onmiddellijk worden verholpen door de gemelde problemen te verhelpen of door contact op te nemen met de Adobe.

## Stappen voor het bekijken van logboeken {#viewing-logs}

### Logboeken voor uitpakken

Ga naar de Adobe Experience Manager-broninstantie en selecteer de gewenste migratieset om de extractielogbestanden weer te geven.

Voer vervolgens de onderstaande stappen uit:

1. Selecteer een migratieset en klik op **Logboek weergeven** in de actiebalk. Dit zal de dialoog van Logs omhoog brengen. Klikken **Extractielogboek** om de logbestanden op een nieuw tabblad weer te geven.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam25.png) \
   Of klik op de knop **VOLTOOID** status om logbestanden op een nieuw tabblad weer te geven.

1. Als u de logboeken wilt koppelen zonder de gebruikersinterface te gebruiken, past u SSH toe in uw bron AEM-omgeving op `crx-quickstart/cloud-migration/extraction-XXXXX/output.log file`.

### Ingestielogbestanden

Ga naar de lijst Ingestietaken in Cloud Acceleration Manager, zoek de gewenste migratietaak en klik op de drie punten (**...**) van de baan. U kunt vervolgens op **Logbestand downloaden** om logbestanden te downloaden.

![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam28.png)
