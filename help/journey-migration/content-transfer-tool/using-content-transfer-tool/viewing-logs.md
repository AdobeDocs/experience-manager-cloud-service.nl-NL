---
title: Logbestanden voor een migratieset weergeven in het gereedschap Inhoud overbrengen
description: Logbestanden voor een migratieset weergeven in het gereedschap Inhoud overbrengen
exl-id: aed1ac83-a2fb-425e-aca4-39cd0bb42fd3
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 52%

---

# Logboeken voor een migratieset weergeven {#view-logs-content-transfer-tool}


>[!CONTEXTUALHELP]
>id="aemcloud_ctt_logs"
>title="Logbestanden weergeven"
>abstract="Na voltooiing van Extractie van Ingestie, controleer de logboeken om het even welke fout/waarschuwingen. Fouten moeten onmiddellijk worden verholpen, hetzij door de gemelde problemen te verhelpen, hetzij door contact op te nemen met de ondersteuning van Adobe."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#troubleshooting" text="Problemen oplossen"
>additional-url="https://helpx.adobe.com/ca/enterprise/admin-guide.html/ca/enterprise/using/support-for-experience-cloud.ug.html" text="Contact opnemen met Adobe-ondersteuning"

Controleer na elke stap (extractie en inname) de logboeken en zoek op fouten.  Fouten moeten onmiddellijk worden verholpen, hetzij door de gemelde problemen te verhelpen, hetzij door contact op te nemen met de ondersteuning van Adobe.

## Stappen voor het bekijken van logboeken {#viewing-logs}

Op de pagina *Overview* kunt u de logboeken voor een bestaande migratieset bekijken.
Voer de onderstaande stappen uit:

1. Ga naar de pagina *Overview* en selecteer de migratieset waarvan u het logboek wilt bekijken. Klik op **View Log** op de actiebalk.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets/view-log1.png)

1. Het dialoogvenster **Logs** wordt weergegeven. Klik op **Extraction Log** om de extractielogbestanden op een nieuw tabblad weer te geven.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets/view-log2.png)
Of:

   U kunt de logboeken voor uw migratieset ook bekijken op het scherm *Overview*. Selecteer de migratieset en klik op de status onder het veld **EXTRACTION**. Klik in dit geval op **FINISHED** om de logbestanden op een nieuw tabblad weer te geven.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets/view-log3.png)

1. Als u de logboeken wilt koppelen zonder de gebruikersinterface te gebruiken, past u SSH toe in uw bron AEM-omgeving op `crx-quickstart/cloud-migration/extraction-XXXXX/output.log file`.
