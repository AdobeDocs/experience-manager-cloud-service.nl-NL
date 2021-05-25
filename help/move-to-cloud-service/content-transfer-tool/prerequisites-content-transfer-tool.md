---
title: Voorwaarden voor het gereedschap Inhoud overbrengen
description: Voorwaarden voor het gereedschap Inhoud overbrengen
source-git-commit: c760b97cdb565244cf20f5193de3e3ebab1579ad
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---

# Voorwaarden voor het gereedschap Inhoud overbrengen {#prerequisites}

De volgende tabel geeft een overzicht van de voorwaarden voordat u het gereedschap Inhoud overbrengen gebruikt. Controleer alle onderstaande overwegingen:

| Overwegingen | Wat wordt momenteel ondersteund |
|--- |--- |
| AEM | Het gereedschap Inhoud overbrengen kan alleen worden uitgevoerd in AEM 6.3 of hoger. Als u Content Transfer Tool wilt gebruiken met AEM 6.2 of oudere versies, is een upgrade van de opslagplaats voor inhoud op locatie naar AEM 6.5 vereist. U hoeft de code hiervoor niet bij te werken naar AEM 6.5. |
| Grootte van segmentwinkel | Content Transfer Tool biedt momenteel ondersteuning voor maximaal 83 GB op *Auteur* en 31 GB op *Publiceren*. |
| Totale grootte van opslagplaats voor inhoud (opslag van inhoud + opslag van gegevens) | Content Transfer Tool is ontworpen voor het overbrengen van inhoud tot 10 TB. Hoger dan 10 TB wordt momenteel niet ondersteund. Maak een ondersteuningsticket met de klantenservice van Adobe om opties voor inhoud groter dan 10 TB te bespreken. |
| Inhoud in onveranderbare paden | Het gereedschap Inhoud overbrengen werkt niet voor het migreren van de inhoud in onveranderlijke paden, zoals `“/etc”`. Raadpleeg [Common Repository Reform](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/all-repository-restructuring-in-aem-6-4.html?lang=en#restructuring) voor meer informatie over de herstructurering van opslaglocaties en workflowmodellen. |