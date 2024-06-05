---
title: Gereedschap AEM
description: Het gereedschap AEM repo is een eenvoudige oplossing voor het overbrengen van JCR-inhoud tussen uw lokale bestandssysteem en de AEM server via een opdrachtregel die vergelijkbaar is met FTP.
exl-id: fb887ba3-e40b-4ab1-b142-0748c6d9f18e
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---

# Gereedschap AEM {#aem-repo-tool}

Het gereedschap AEM repo is een eenvoudige oplossing voor het overbrengen van JCR-inhoud tussen uw lokale bestandssysteem en de AEM server via een opdrachtregel die vergelijkbaar is met FTP. Het gereedschap AEM herhalen is vergelijkbaar met het gereedschap [Jackrabbit FileVault Maven-plug-in](https://jackrabbit.apache.org/filevault-package-maven-plugin), maar is sneller, heeft minimale gebiedsdelen, en is een eenvoudig bash manuscript.

Dit hulpmiddel vereenvoudigt de overdracht van dossiers voor de ontwikkelaar en kan ook in Eclipse en IntelliJ worden geïntegreerd om ontwikkeling nog efficiënter te maken.

## Overzicht {#overview}

Voor een bepaald pad binnen een `jcr_root` De FileVault-structuur op het bestandssysteem maakt met het AEM Repo Tool een pakket met één filter voor de gehele substructuur en plaatst dat op de server (vergelijkbaar met FTP) `put`), haalt het op van de server ( `get`) of vergelijkt de verschillen ( `status` en `diff`).

Het gereedschap ondersteunt geen meerdere filterpaden of FileVault-paden `filter.xml`.

>[!CAUTION]
>
>Met het gereedschap AEM repo overschrijft u altijd het gehele opgegeven bestand of de opgegeven map.

## Downloaden en documentatie {#download-and-documentation}

De [AEM Repo Tool is beschikbaar op GitHub via deze koppeling](https://github.com/Adobe-Marketing-Cloud/tools/tree/master/repo) samen met gedetailleerde installatie- en gebruiksinstructies.

Als u de bron van het Hulpmiddel van de AEM wilt downloaden, zie het hieronder verbonden project GitHub.

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden

* [Open hulpmiddelenproject op GitHub](https://github.com/Adobe-Marketing-Cloud/tools)
* Het project downloaden als [een ZIP-bestand](https://github.com/Adobe-Marketing-Cloud/tools/archive/master.zip)
