---
title: Java API-richtlijnen
description: AEM is gebaseerd op een rijke open-source softwarestack die veel Java API's beschikbaar maakt voor gebruik.
translation-type: tm+mt
source-git-commit: b927992107d7e7e4df5511a366c71449ff73ec93
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---


# Java API Guidelines {#java-api-guidelines}

Adobe Experience Manager (AEM) is gebaseerd op een rijke open-source softwarestack die veel Java API&#39;s beschikbaar maakt voor gebruik tijdens de ontwikkeling.

AEM is gebaseerd op de volgende vier primaire Java API-sets in aflopende volgorde van voorkeur.

1. **Adobe Experience Manager (AEM)**  - Productabstracties zoals pagina&#39;s, middelen, workflows, enz.
1. **[Apache Sling Web Framework](https://sling.apache.org/apidocs/sling11/)**  - REST en resource-based abstractions zoals middelen, waardekaarten, en HTTP- verzoeken.
1. **[JCR (Apache Jackrabbit Oak)](http://jackrabbit.apache.org/oak/docs/oak_api/overview.html)**  - Abstracties van gegevens en inhoud, zoals knooppunten, eigenschappen en sessies.
1. **[OSGi (Apache Felix)](https://felix.apache.org)** - OSGi-applicatiecontainerabstracties zoals services en (OSGi) componenten.

Als een API door AEM wordt verstrekt, verkies het over Sling, JCR, en OSGi. Als AEM geen API aanbiedt, kiest u Verdelen boven JCR en OSGi.

Zie het document [Java API Best Practices](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/understand-java-api-best-practices.html) voor meer informatie over deze richtlijnen.
