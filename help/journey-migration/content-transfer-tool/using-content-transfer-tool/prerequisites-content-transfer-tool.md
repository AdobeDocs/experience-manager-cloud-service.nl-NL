---
title: Voorwaarden voor het gereedschap Inhoud overbrengen
description: U vertrouwd maken met de vereisten voor het gereedschap Inhoud overbrengen
exl-id: 41a9cff1-4d89-480c-b9fc-5e8efc2a0705
feature: Migration
role: Admin
source-git-commit: d8730109f5cd7dab44f535b1de008ae09811f221
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---


# Voorwaarden voor het gereedschap Inhoud overbrengen {#prerequisites}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_prereqs"
>title="Belangrijke overwegingen voor het gebruik van het gereedschap Inhoud overbrengen"
>abstract="Houd rekening met belangrijke overwegingen voor het gebruik van het gereedschap Inhoud overbrengen, zoals Java™- en AEM-versies, ondersteunde gegevenstypen, gebruikersgroepen en meer."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/prerequisites-content-transfer-tool.html?lang=nl-NL" text="Belangrijke overwegingen voor het gebruik van het gereedschap Inhoud overbrengen"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=nl-NL#best-practices" text="Beste praktijken en richtlijnen"

In de volgende tabel staan de voorwaarden voor het gebruik van het gereedschap Inhoud overbrengen.

Alle onderstaande overwegingen bekijken:

| Overwegingen | Wat wordt momenteel ondersteund |
|--------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| AEM-versie | Content Transfer Tool kan alleen worden uitgevoerd in AEM 6.3 of hoger. |
| Grootte van segmentwinkel | Een bestaande bewaarplaats die minder dan 750 miljoen knopen JCR en tot 500 GB (online samengeperste grootte) op *Auteur* heeft en 50 GB op *publiceert* wordt momenteel gesteund. Maak een ondersteuningsticket met de klantenservice van Adobe, zodat u opties voor de grootte van de segmentwinkel boven deze limieten kunt bespreken. |
| Totale grootte van de gegevensopslagplaats van de Inhoud <br>*(segmentopslag + gegevensopslag)* | Het gereedschap voor het overbrengen van inhoud is ontworpen om inhoud van maximaal 20 terabytes over te brengen voor het type gegevensopslag van bestandsgegevens. Hoger dan 20 terabytes wordt momenteel niet ondersteund. Maak een ondersteuningsticket met de klantenservice van Adobe, zodat u opties kunt bespreken voor inhoud die groter is dan 20 terabytes. <br> om het proces van de inhoudsoverdracht voor grote bewaarplaatsen beduidend te versnellen, kan een facultatieve [ pre-copy ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=nl-NL#setting-up-pre-copy-step) stap worden gebruikt. Dit proces is van toepassing op File Data Store, Amazon S3 en Azure Data Store-typen voor gegevensopslag. Voor Amazon S3 en Azure Data Store worden opslaggrootten van meer dan 20 terabytes ondersteund. |
| Totale indexgrootte van Lucene | De totale grootte van de Index van Lucene van 25 GB maximum, exclusief `/oak:index/lucene` en `/oak:index/damAssetLucene` wordt gesteund. Maak een ondersteuningsticket met de klantenservice van Adobe, zodat u opties voor de indexgrootte boven deze limiet kunt bespreken. |
| Inhoud in onveranderbare paden | Het gereedschap Inhoud overbrengen kan niet worden gebruikt om inhoud in onveranderbare paden te migreren. Om inhoud van `/etc` over te brengen, kunt u bepaalde `/etc` wegen selecteren, maar slechts om [ AEM Forms aan AEM Forms as a Cloud Service ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/setup-configure-migrate/migrate-to-forms-as-a-cloud-service.html?lang=nl-NL#paths-of-various-aem-forms-specific-assets) te steunen. Voor alle andere gebruik-gevallen, zie [ Gemeenschappelijke Herstructurering van de Bewaarplaats ](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/restructuring/all-repository-restructuring-in-aem-6-5.html?lang=nl-NL) om meer over bewaarplaatsherstructurering te leren. |
| Waarde van eigenschap Node in MongoDB | Eigenschapwaarden voor knooppunten die zijn opgeslagen in MongoDB, mogen niet groter zijn dan 16 MB. Deze regel wordt afgedwongen door MongoDB. De suggesties ontbreken als er bezitswaarden groter dan deze grens zijn. Alvorens een extractie in werking te stellen, stel dit [ eiken-in werking ](https://repo1.maven.org/maven2/org/apache/jackrabbit/oak-run/1.38.0/oak-run-1.38.0.jar) manuscript. Controleer alle waarden van grote eigenschappen en valideer als deze nodig zijn. Degenen die 16 MB overschrijden, moeten in Binaire waarden worden omgezet. |

## Volgende functies {#whats-next}

Zodra u de eerste vereisten hebt herzien en hebt bepaald of u het Hulpmiddel van de Overdracht van de Inhoud in uw migratieproject kunt gebruiken, zie [ Richtlijnen en Beste praktijken voor het gebruiken van het Hulpmiddel van de Overdracht van de Inhoud ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=nl-NL).
