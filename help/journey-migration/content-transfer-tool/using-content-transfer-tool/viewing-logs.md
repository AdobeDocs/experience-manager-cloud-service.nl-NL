---
title: Logbestanden voor een migratieset weergeven in het gereedschap Inhoud overbrengen
description: Logbestanden voor een migratieset weergeven in het gereedschap Inhoud overbrengen
exl-id: aed1ac83-a2fb-425e-aca4-39cd0bb42fd3
feature: Migration
role: Admin
source-git-commit: 91f9bcafc087b6f9329d7a47509cc659714705ff
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 9%

---

# Logboeken voor een migratieset weergeven {#view-logs-content-transfer-tool}


>[!CONTEXTUALHELP]
>id="aemcloud_ctt_logs"
>title="Logbestanden weergeven"
>abstract="Na voltooiing van Extractie van Ingestie, controleer de logboeken om het even welke fout/waarschuwingen. Fouten moeten onmiddellijk worden verholpen door de gemelde problemen te verhelpen of door contact op te nemen met de ondersteuning van Adobe."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html#troubleshooting" text="Problemen oplossen"
>additional-url="https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html" text="Contact opnemen met Adobe-ondersteuning"

Controleer na elke stap (extractie en inname) de logboeken en zoek op fouten.  Fouten moeten onmiddellijk worden verholpen door de gemelde problemen te verhelpen of door contact op te nemen met de ondersteuning van Adobe.

## Stappen voor het bekijken van logboeken {#viewing-logs}

### Logboeken voor uitpakken

Ga naar de Adobe Experience Manager-broninstantie en selecteer de gewenste migratieset om de extractielogbestanden weer te geven.

Voer vervolgens de onderstaande stappen uit:

1. Selecteer een migratiereeks en klik **Logboek van de Mening** van de actiebar. Dit zal de dialoog van Logs omhoog brengen. Klik **Logboek van de Uitwinning** om de logboeken in een nieuw lusje te bekijken.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/logs.png) \
   Of, klik de **EINDIGDE** status aan meningslogboeken in een nieuw lusje.

1. Als u de logboeken wilt koppelen zonder de gebruikersinterface te gebruiken, past u SSH toe in uw bron AEM-omgeving op `crx-quickstart/cloud-migration/extraction-XXXXX/output.log file`.

### Ingestielogbestanden

Om de logboeken van de Opname te bekijken, ga naar de lijst van Banen van de Opname in Cloud Acceleration Manager, dan de gewenste migratiebaan en klik de drie punten (**...**) van de baan. U kunt dan **Logboek van de Download** klikken om logboeken te downloaden.

![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam28.png)
