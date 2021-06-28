---
title: Voorwaarden voor het gereedschap Inhoud overbrengen
description: Voorwaarden voor het gereedschap Inhoud overbrengen
exl-id: ef6d0e1a-0ed2-4485-adab-df6e0cf3ac4d
source-git-commit: bf69ee0a033412e632236975cc772b91c554fd87
workflow-type: tm+mt
source-wordcount: '394'
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
| Grootte van segmentwinkel | Er wordt momenteel ondersteuning geboden voor maximaal 83 GB op *Auteur* en 31 GB op *Publiceren*. Creeer een steunkaartje met de Zorg van de Klant van Adobe om opties voor de grootte van de segmentopslag boven deze grenzen te bespreken. |
| Totale grootte van gegevensopslagruimte <br>*(segmentopslag + gegevensopslag)* | Content Transfer Tool is ontworpen om inhoud van maximaal 10 TB over te brengen voor het type gegevensopslag van bestandsgegevens. Hoger dan 10 TB wordt momenteel niet ondersteund. Maak een ondersteuningsticket met de klantenservice van Adobe om opties voor inhoud groter dan 10 TB te bespreken. <br>Voor Amazon S3- en Azure Data Store-typen voor gegevensopslag kan een optionele  [pre-](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en#setting-up-pre-copy-step) copystep worden gebruikt om het proces voor de overdracht van inhoud aanzienlijk te versnellen en ondersteunt een gegevensopslag van meer dan 10 TB. |
| Inhoud in onveranderbare paden | Het gereedschap Inhoud overbrengen kan niet worden gebruikt om inhoud in onveranderbare paden te migreren. Als u inhoud wilt overbrengen van `/etc`, mogen alleen bepaalde `"/etc"` paden worden geselecteerd, maar alleen ter ondersteuning van [AEM Forms naar AEM Forms als Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/migrate-to-forms-as-a-cloud-service.html?lang=en#paths-of-various-aem-forms-specific-assets). Raadpleeg [Common Repository Reform](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/all-repository-restructuring-in-aem-6-4.html?lang=en#restructuring) voor alle andere gebruiksgevallen voor meer informatie over de herstructurering van de opslagplaats. |

## Volgende functies {#whats-next}

Zodra u de eerste vereisten hebt herzien en hebt bepaald of u het Hulpmiddel van de Overdracht van de Inhoud in uw migratieproject kunt gebruiken, verwijs naar [Extra beste praktijken en overwegingen](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md) terwijl het gebruiken van het Hulpmiddel van de Overdracht van de Inhoud.
