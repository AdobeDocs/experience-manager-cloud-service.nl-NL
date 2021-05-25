---
title: Voorwaarden voor het gereedschap Inhoud overbrengen
description: Voorwaarden voor het gereedschap Inhoud overbrengen
source-git-commit: ebe12a71df610a68c43048667136e331c1bd8f86
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Voorwaarden voor het gereedschap Inhoud overbrengen {#prerequisites}

In de volgende tabel staan de voorwaarden voor het gebruik van het gereedschap Inhoud overbrengen. Controleer alle onderstaande overwegingen:

| Overwegingen | Wat wordt momenteel ondersteund |
|--- |--- |
| AEM | Het gereedschap Inhoud overbrengen kan alleen worden uitgevoerd in AEM 6.3 of hoger. Als u Content Transfer Tool wilt gebruiken met AEM 6.2 of oudere versies, is een upgrade van de opslagplaats voor inhoud op locatie naar AEM 6.5 vereist. U hoeft de code hiervoor niet bij te werken naar AEM 6.5. |
| Grootte van segmentwinkel | Content Transfer Tool biedt momenteel ondersteuning voor maximaal 83 GB op *Auteur* en 31 GB op *Publiceren*. |
| Totale grootte van opslagplaats voor inhoud <br>*(opslag van inhoud + gegevensopslag)* | Content Transfer Tool is ontworpen voor het overbrengen van inhoud tot 10 TB. Hoger dan 10 TB wordt momenteel niet ondersteund. Maak een ondersteuningsticket met de klantenservice van Adobe om opties voor inhoud groter dan 10 TB te bespreken. |
| Inhoud in onveranderbare paden | Het gereedschap Inhoud overbrengen werkt niet voor het migreren van de inhoud in onveranderlijke paden, zoals `“/etc”`. <br>Raadpleeg  [Common Repository ](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/all-repository-restructuring-in-aem-6-4.html?lang=en#restructuring) Restructurering voor meer informatie over de reorganisatie van opslaglocaties en workflowmodellen. |