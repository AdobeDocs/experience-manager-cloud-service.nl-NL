---
title: Voorwaarden voor het gereedschap Inhoud overbrengen
description: Voorwaarden voor het gereedschap Inhoud overbrengen
exl-id: ef6d0e1a-0ed2-4485-adab-df6e0cf3ac4d
source-git-commit: fa7e5d07ed52a71999de95bbf6299ae5eb7af537
workflow-type: tm+mt
source-wordcount: '569'
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
| AEM | Het gereedschap Inhoud overbrengen kan alleen worden uitgevoerd in AEM 6.3 of hoger. Als u Content Transfer Tool wilt gebruiken met AEM 6.2 of oudere versies, is een upgrade van de opslagplaats voor inhoud op locatie naar AEM 6.5 vereist. U hoeft de code hiervoor niet bij te werken naar AEM 6.5. |
| Grootte van segmentwinkel | Een bestaande opslagplaats die minder dan 55 miljoen JCR knopen en tot 83 GB (online gecomprimeerde grootte) op *Auteur* en 31 GB op *Publish* heeft wordt momenteel gesteund. Creeer een steunkaartje met de Zorg van de Klant van Adobe om opties voor de grootte van de segmentopslag boven deze grenzen te bespreken. |
| Totale grootte van gegevensopslagruimte <br>*(segmentopslag + gegevensopslag)* | Content Transfer Tool is ontworpen om inhoud van maximaal 10 TB over te brengen voor het type gegevensopslag van bestandsgegevens. Hoger dan 10 TB wordt momenteel niet ondersteund. Maak een ondersteuningsticket met de klantenservice van Adobe om opties voor inhoud groter dan 10 TB te bespreken. <br>Voor Amazon S3- en Azure Data Store-typen voor gegevensopslag kan een optionele  [pre-](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en#setting-up-pre-copy-step) copystep worden gebruikt om het proces voor de overdracht van inhoud aanzienlijk te versnellen en ondersteunt een gegevensopslag van meer dan 10 TB. |
| Totale indexgrootte | De totale indexgrootte van maximaal 25 GB wordt momenteel ondersteund. Maak een ondersteuningsticket met de klantenservice van Adobe om opties voor indexgrootte boven deze limiet te bespreken. |
| Lengte knooppuntnaam | De lengte van een knooppuntnaam moet 150 bytes of minder zijn. Node-namen die langer zijn dan 150 bytes, moeten worden ingekort tot &lt;= 150 bytes om te worden ondersteund door de Document node store in AEM as a Cloud Service. De oplossingen mislukken als deze lange knooppuntnamen niet vast zijn. |
| Inhoud in onveranderbare paden | Het gereedschap Inhoud overbrengen kan niet worden gebruikt om inhoud in onveranderbare paden te migreren. Als u inhoud wilt overbrengen van `/etc`, mogen alleen bepaalde `/etc` paden worden geselecteerd, maar alleen ter ondersteuning van [AEM Forms naar AEM Forms as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/migrate-to-forms-as-a-cloud-service.html?lang=en#paths-of-various-aem-forms-specific-assets). Raadpleeg [Common Repository Reform](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/all-repository-restructuring-in-aem-6-4.html?lang=en#restructuring) voor alle andere gebruiksgevallen voor meer informatie over de herstructurering van de opslagplaats. |
| Waarde van eigenschap Node in MongoDB | Eigenschapwaarden voor knooppunten die zijn opgeslagen in MongoDB, mogen niet groter zijn dan 16 MB. Dit wordt afgedwongen door MongoDB. De suggesties zullen ontbreken als er bezitswaarden groter dan deze grens zijn. Alvorens een extractie in werking te stellen, stel dit [eak-looppas](https://repo1.maven.org/maven2/org/apache/jackrabbit/oak-run/1.38.0/oak-run-1.38.0.jar) manuscript in werking. Controleer alle waarden van grote eigenschappen en valideer als deze nodig zijn. Degenen die 16 MB overschrijden, moeten worden omgezet in binaire waarden. |

## Volgende functies {#whats-next}

Zodra u de eerste vereisten hebt herzien en hebt bepaald of u het Hulpmiddel van de Overdracht van de Inhoud in uw migratieproject kunt gebruiken, verwijs naar [Richtlijnen en Beste praktijken voor het gebruiken van het Hulpmiddel van de Overdracht van de Inhoud](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=en).
