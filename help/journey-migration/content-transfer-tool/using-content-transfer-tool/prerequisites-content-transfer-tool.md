---
title: Voorwaarden voor het gereedschap Inhoud overbrengen
description: U vertrouwd maken met de vereisten voor het gereedschap Inhoud overbrengen
exl-id: 41a9cff1-4d89-480c-b9fc-5e8efc2a0705
source-git-commit: 8c73805b6ed1b7a03c65b4d21a4252c1412a5742
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 1%

---

# Voorwaarden voor het gereedschap Inhoud overbrengen {#prerequisites}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_prereqs"
>title="Belangrijke overwegingen voor het gebruik van het gereedschap Inhoud overbrengen"
>abstract="Houd rekening met belangrijke overwegingen voor het gebruik van het gereedschap Inhoud overbrengen, zoals Java™- en AEM-versies, ondersteunde gegevenstypen, gebruikersgroepoverwegingen en meer."
additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/prerequisites-content-transfer-tool.html?lang=en" text="Belangrijke overwegingen voor het gebruik van de Content Transfer-tool"
additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=en#best-practices" text="Beste praktijken en richtlijnen"

In de volgende tabel staan de voorwaarden voor het gebruik van het gereedschap Inhoud overbrengen.

Alle onderstaande overwegingen bekijken:

| Overwegingen | Wat wordt momenteel ondersteund |
|---------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| AEM | Het gereedschap Inhoud overbrengen kan alleen worden uitgevoerd in AEM 6.3 of hoger. |
| Grootte van segmentwinkel | Een bestaande opslagplaats met minder dan 55 miljoen JCR-knooppunten en maximaal 250 GB (gecomprimeerde onlinegrootte) op *Auteur* en 50 GB aan *Publiceren* worden momenteel ondersteund. Creeer een steunkaartje met de Zorg van de Klant van de Adobe zodat kunt u opties voor de grootte van de segmentopslag boven deze grenzen bespreken. |
| Totale grootte van opslagplaats voor inhoud <br>*(segmentopslag + gegevensopslag)* | Het gereedschap voor het overbrengen van inhoud is ontworpen om inhoud van maximaal 20 terabytes over te brengen voor het type gegevensopslag van bestandsgegevens. Hoger dan 20 terabytes wordt momenteel niet ondersteund. Maak een ondersteuningsticket met de klantenservice van de Adobe, zodat u opties voor inhoud groter dan 20 terabytes kunt bespreken. <br>Als u het proces voor het overdragen van inhoud voor grote opslagplaatsen aanzienlijk wilt versnellen, kunt u [voorkopie](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/handling-large-content-repositories.html#setting-up-pre-copy-step) Deze stap kan worden gebruikt. Dit proces is van toepassing op File Data Store, Amazon S3 en Azure Data Store-typen voor gegevensopslag. Voor Amazon S3 en Azure Data Store worden opslaggrootten van meer dan 20 terabytes ondersteund. |
| Totale indexgrootte van Lucene | Totale Lucene Index-grootte van maximaal 25 GB, exclusief `/oak:index/lucene` en `/oak:index/damAssetLucene` wordt ondersteund. Maak een ondersteuningsticket met de klantenservice van de Adobe, zodat u opties voor de indexgrootte boven deze limiet kunt bespreken. |
| Lengte knooppuntnaam | De lengte van een knooppuntnaam moet 150 bytes of minder zijn wanneer de knoop ouderweg >= (gelijk of groter dan) 350 bytes is. Deze knooppuntnamen moeten worden ingekort tot &lt;= 150 bytes, zodat deze door de Document node store in AEM as a Cloud Service worden ondersteund. De oplossingen mislukken als deze lange knooppuntnamen niet vast zijn. |
| Inhoud in onveranderbare paden | Het gereedschap Inhoud overbrengen kan niet worden gebruikt om inhoud in onveranderbare paden te migreren. Inhoud overbrengen van `/etc`, kunt u bepaalde `/etc` paden, maar alleen ter ondersteuning van [AEM Forms naar AEM Forms as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/setup-configure-migrate/migrate-to-forms-as-a-cloud-service.html#paths-of-various-aem-forms-specific-assets). Voor alle andere gevallen van gebruik, zie [Herstructurering van de gemeenschappelijke opslagplaats](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/restructuring/all-repository-restructuring-in-aem-6-5.html) voor meer informatie over herstructurering van opslagplaatsen. |
| Waarde van eigenschap Node in MongoDB | Eigenschapwaarden voor knooppunten die zijn opgeslagen in MongoDB, mogen niet groter zijn dan 16 MB. Deze regel wordt afgedwongen door MongoDB. De suggesties ontbreken als er bezitswaarden groter dan deze grens zijn. Voer deze uit voordat u een extractie uitvoert [eik](https://repo1.maven.org/maven2/org/apache/jackrabbit/oak-run/1.38.0/oak-run-1.38.0.jar) script. Controleer alle waarden van grote eigenschappen en valideer als deze nodig zijn. Degenen die 16 MB overschrijden, moeten in Binaire waarden worden omgezet. |

## Volgende functies {#whats-next}

Zodra u de eerste vereisten hebt herzien en hebt bepaald of u het Hulpmiddel van de Overdracht van de Inhoud in uw migratieproject kunt gebruiken, zie [Richtlijnen en aanbevolen procedures voor het gebruik van het gereedschap Inhoud overbrengen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html).
