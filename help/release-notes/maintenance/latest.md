---
title: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: a1686d7796bb1e310b776195bd19df98f6f10650
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 1%

---

# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In de volgende sectie worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van as a Cloud Service Experience Manager beschreven.

## Release 13323 {#release-13323}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 13323 samengevat, die op 1 september 2023 openbaar werd gemaakt. Deze onderhoudrelease vervangt release 13239.

2023.9.0 Activering van de functie biedt de volledige functie die is ingesteld voor deze onderhoudsrelease. Zie de [Experience Manager geeft Routekaart vrij](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html) voor meer informatie .

### Verbeteringen {#enhancements-13323}

- GRANITE-46784: Voeg optie toe om BeonderAuthenticationHandler onbruikbaar te maken
- GRANITE-36205: Update internal eak release version to latest
- ASSETS-26713: Touch UI External Link to New Experience UI Dashboard - Unified-shell-integratie en upgrade die geoptimaliseerd is voor ui-touch
- SKYOPS-63302: Upgrade com.adobe.granite:com.adobe.granite.auth.saml naar v1.0.54
- GRANITE-46634: Upgrade naar gebeurtenisclient 1.4.0
- GRANITE-46788: Werk bibliotheken bij naar Apache Commons IO 2.13.0, Commons Lang 3.13.0, Commons Code 1.16.0 en Commons Compress 1.23.0
- GRANITE-46705: Update to Apache Felix HTTP Jetty 4.1.14
- GRANITE-46631: Update Jackrabbit versie to 2.20.11
- SKYOPS-61895: Update to Jackrabbit FileVault 3.7.0

### Opgeloste problemen {#fixed-issues-13323}

- SKYOPS-63290: Correctie van onjuiste evolutie van emmers
- SKYOPS-54607: Ratelimiter-serverlaadberekening is niet correct voor een verzoek dat is mislukt
- ASSETS-27648: ContentModelIT kan uitsluitingsbestanden van andere bundels niet lezen
- GRANITE-43744: Het stileren Authenticator werkt niet behoorlijk als er wanconfiguratie met authentificatie-vereiste en ijdelingspad is
- GRANITE-46419: AEM integratieprobleem met Auth0 Idp
- GRANITE-46292: Okta SAML configuratie werkt niet na AEM Cloud-update
- GRANITE-47059: SSL-bundel van graniet verwijderen

### Bekende problemen {#known-issues-13323}

- SITES-15622: GraphQL - Issue with persisted query with number &amp; boolean parameters.
- SITES-15654: GraphQL - Issues with union and properties of same name.

### Ingesloten technologieën {#embedded-tech-13323}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM AK | 1,54-T20230817132355-3800a65 | [API 1.54.0 voor ongewenste API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.54.0/index.html) |
| AEM SLING-API | Versie 2.27.2 | [API voor Apache Sling API 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Versie 1.4.20-1.4.0 | [HTML Sjabloontaalspecificaties](https://github.com/adobe/htl-spec) |
| AEM-kerncomponenten | Versie 2.23.2 | [AEM WCM Core-componenten](https://github.com/adobe/aem-core-wcm-components) |
