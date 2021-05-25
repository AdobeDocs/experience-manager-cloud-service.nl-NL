---
title: Voorwaarden voor het gereedschap Inhoud overbrengen
description: Voorwaarden voor het gereedschap Inhoud overbrengen
source-git-commit: becb8368af8a8228bf3248bde66ad7164187a9c4
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# Voorwaarden voor het gereedschap Inhoud overbrengen {#prerequisites}

In de volgende tabel staan de voorwaarden voor het gebruik van het gereedschap Inhoud overbrengen.

Controleer alle onderstaande overwegingen:

| Overwegingen | Wat wordt momenteel ondersteund |
|--- |--- |
| AEM | Het gereedschap Inhoud overbrengen kan alleen worden uitgevoerd in AEM 6.3 of hoger. Als u Content Transfer Tool wilt gebruiken met AEM 6.2 of oudere versies, is een upgrade van de opslagplaats voor inhoud op locatie naar AEM 6.5 vereist. U hoeft de code hiervoor niet bij te werken naar AEM 6.5. |
| Grootte van segmentwinkel | Content Transfer Tool biedt momenteel ondersteuning voor maximaal 83 GB op *Auteur* en 31 GB op *Publiceren*. |
| Totale grootte van gegevensopslagruimte <br>*(segmentopslag + gegevensopslag)* | Content Transfer Tool is ontworpen voor het overbrengen van inhoud tot 10 TB. Hoger dan 10 TB wordt momenteel niet ondersteund. Maak een ondersteuningsticket met de klantenservice van Adobe om opties voor inhoud groter dan 10 TB te bespreken. |
| Inhoud in onveranderbare paden | Het gereedschap Inhoud overbrengen kan niet worden gebruikt voor het migreren van inhoud in onveranderlijke paden, zoals `“/etc”`. Er zijn bepaalde `"/etc"` wegen toegestaan om worden geselecteerd maar slechts om [AEM Forms aan AEM Forms als Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/migrate-to-forms-as-a-cloud-service.html?lang=en#paths-of-various-aem-forms-specific-assets) te steunen. Raadpleeg [Common Repository Reform](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/all-repository-restructuring-in-aem-6-4.html?lang=en#restructuring) voor alle andere gebruiksgevallen voor meer informatie over de herstructurering van de opslagplaats. |

## Volgende {#whats-next}

Zodra u de eerste vereisten hebt herzien en hebt bepaald of u het Hulpmiddel van de Overdracht van de Inhoud in uw migratieproject kunt gebruiken, verwijs naar [Extra beste praktijken en overwegingen](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md) terwijl het gebruiken van het Hulpmiddel van de Overdracht van de Inhoud.
