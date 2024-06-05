---
title: Maven Project Version Handling
description: Voor implementatie van AEM as a Cloud Service in fasen en productie genereert Cloud Manager een unieke, incrementele versie.
exl-id: 658bcbed-0733-45da-a3e3-9a5f817099c5
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---


# Maven Project Version Handling {#maven-project-version-handling}

Voor implementatie van AEM as a Cloud Service staging en productie genereert Cloud Manager een unieke, incrementele versie

Deze versie is te zien op de [detailpagina voor uitvoering van pijpleiding](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#view-details) en de activiteitenpagina. Wanneer een bouwstijl in werking wordt gesteld, wordt het Maven project bijgewerkt om deze versie te gebruiken en een markering wordt gecreeerd in de git bewaarplaats met die versie als zijn naam.

Als de oorspronkelijke projectversie aan bepaalde criteria voldoet, voegt de bijgewerkte versie van het Maven-project zowel de oorspronkelijke projectversie als de door Cloud Manager gegenereerde versie samen. De tag gebruikt echter altijd de gegenereerde versie. Deze samenvoeging vindt pas plaats als de oorspronkelijke projectversie is samengesteld met precies drie versiesegmenten, bijvoorbeeld `1.0.0` of `1.2.3`, maar niet `1.0` of `1`en mag de oorspronkelijke versie niet eindigen in `-SNAPSHOT`.

>[!IMPORTANT]
>
>Deze oorspronkelijke waarde voor de projectversie moet statisch worden ingesteld in het dialoogvenster `<version>` element van het hoogste niveau `pom.xml` bestand in de vertakking van de it-opslagplaats.

Als de originele versie aan deze criteria voldoet, dan wordt de geproduceerde versie toegevoegd aan de originele versie als nieuw versiesegment. De gegenereerde versie wordt ook enigszins aangepast, zodat de versie correct wordt gesorteerd en verwerkt. Bijvoorbeeld, veronderstellend een geproduceerde versie van `2019.926.121356.0000020490` zou de volgende resultaten opleveren.

| Versie | Versie in `pom.xml` | Opmerking |
|---|---|---|
| `1.0.0` | `1.0.0.2019_0926_121356_0000020490` | Oorspronkelijke versie met de juiste indeling |
| `1.0.0-SNAPSHOT` | `2019.926.121356.0000020490` | Opnameversie, overschreven |
| `1` | `2019.926.121356.0000020490` | Onvolledige versie, overschreven |

>[!NOTE]
>
>Ongeacht of de oorspronkelijke versie is opgenomen in de door Cloud Manager geïnitialiseerde versie, de oorspronkelijke versie is beschikbaar als een Maven-eigenschap met de naam `cloudManagerOriginalVersion`.
