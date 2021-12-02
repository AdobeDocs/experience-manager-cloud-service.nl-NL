---
title: Voorwaarden voor het gereedschap Inhoud overbrengen
description: Voorwaarden voor het gereedschap Inhoud overbrengen
exl-id: ef6d0e1a-0ed2-4485-adab-df6e0cf3ac4d
source-git-commit: 3b1ef6eef7249a33908102b287ee4b373d7e843b
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 1%

---

# Voorwaarden voor het gereedschap Inhoud overbrengen {#prerequisites}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_prereqs"
>title="Belangrijke overwegingen voor het gebruik van het gereedschap Inhoud overbrengen"
>abstract="Houd rekening met belangrijke overwegingen om het gereedschap Inhoud overbrengen te gebruiken, zoals Java- en AEM-versies, ondersteunde datastore-typen, gebruikersgroepoverwegingen en meer."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#pre-reqs" text="Belangrijke overwegingen voor het gebruik van de Content Transfer-tool"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=en#best-practices" text="Beste praktijken en richtlijnen"

In de volgende tabel staan de voorwaarden voor het gebruik van het gereedschap Inhoud overbrengen.

Controleer alle onderstaande overwegingen:

| Overwegingen | Wat wordt momenteel ondersteund |
|--- |--- |
| AEM | Het gereedschap Inhoud overbrengen kan alleen worden uitgevoerd in AEM 6.3 of hoger. |
| Grootte van segmentwinkel | Een bestaande opslagplaats met minder dan 55 miljoen JCR-knooppunten en maximaal 83 GB (gecomprimeerde onlinegrootte) op *Auteur* en 31 GB op *Publiceren* worden momenteel ondersteund. Creeer een steunkaartje met de Zorg van de Klant van Adobe om opties voor de grootte van de segmentopslag boven deze grenzen te bespreken. |
| Totale grootte van opslagplaats voor inhoud <br>*(segmentopslag + gegevensopslag)* | Content Transfer Tool is ontworpen om inhoud van maximaal 20 TB over te brengen voor het type gegevensopslag van bestandsgegevens. Hoger dan 20 TB wordt momenteel niet ondersteund. Maak een ondersteuningsticket met de klantenservice van Adobe om opties voor inhoud groter dan 20 TB te bespreken. <br>Als u het proces voor het overdragen van inhoud voor grote opslagplaatsen aanzienlijk wilt versnellen, kunt u [voorkopie](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en#setting-up-pre-copy-step) kan worden gebruikt. Dit geldt voor File Data Store, Amazon S3 en Azure Data Store. Voor Amazon S3 en Azure Data Store wordt opslagruimte van meer dan 20 TB ondersteund. |
| Totale indexgrootte van Lucene | De totale grootte van de Index van Lucene van 25GB maximum wordt momenteel gesteund. Maak een ondersteuningsticket met de klantenservice van Adobe om opties voor indexgrootte boven deze limiet te bespreken. |
| Lengte knooppuntnaam | De lengte van een knooppuntnaam moet 150 bytes of minder zijn. Node-namen die langer zijn dan 150 bytes, moeten worden ingekort tot &lt;= 150 bytes om te worden ondersteund door de Document node store in AEM as a Cloud Service. De oplossingen mislukken als deze lange knooppuntnamen niet vast zijn. |
| Inhoud in onveranderbare paden | Het gereedschap Inhoud overbrengen kan niet worden gebruikt om inhoud in onveranderbare paden te migreren. Inhoud overbrengen van `/etc` slechts `/etc` paden mogen worden geselecteerd, maar alleen ter ondersteuning van [AEM Forms naar AEM Forms as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/migrate-to-forms-as-a-cloud-service.html?lang=en#paths-of-various-aem-forms-specific-assets). Voor alle andere gevallen van gebruik raadpleegt u [Herstructurering van de gemeenschappelijke opslagplaats](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/all-repository-restructuring-in-aem-6-4.html?lang=en#restructuring) voor meer informatie over herstructurering van opslagplaatsen. |
| Waarde van eigenschap Node in MongoDB | Eigenschapwaarden voor knooppunten die zijn opgeslagen in MongoDB, mogen niet groter zijn dan 16 MB. Dit wordt afgedwongen door MongoDB. De suggesties zullen ontbreken als er bezitswaarden groter dan deze grens zijn. Voer deze uit voordat u een extractie uitvoert [eik](https://repo1.maven.org/maven2/org/apache/jackrabbit/oak-run/1.38.0/oak-run-1.38.0.jar) script. Controleer alle waarden van grote eigenschappen en valideer als deze nodig zijn. Degenen die 16 MB overschrijden, moeten worden omgezet in binaire waarden. |

## Volgende functies {#whats-next}

Zodra u de eerste vereisten hebt herzien en hebt bepaald of u het Hulpmiddel van de Overdracht van de Inhoud in uw migratieproject kunt gebruiken, verwijs naar [Richtlijnen en aanbevolen procedures voor het gebruik van het gereedschap Inhoud overbrengen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=en).
