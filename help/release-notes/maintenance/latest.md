---
title: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: b7e7bc7546b836667fff9db0ea5419e751f492cb
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 2%

---

# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In de volgende sectie worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van as a Cloud Service Experience Manager beschreven.

## Release 15977 {#release-15977}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 15977 samengevat, die op 19 april 2024 openbaar werd gemaakt. De vorige onderhoudsrelease was release 15939.

2024.4.0 Activering van de functie biedt de volledige functie die is ingesteld voor deze onderhoudsrelease. Zie de [Experience Manager geeft Routekaart vrij](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html) voor meer informatie .

### Verbeteringen {#enhancements-15977}

* GRANITE-51335: Optimaliseer AEM health check om de stabiliteit van instanties te verhogen.

### Opgeloste problemen {#fixed-issues-15977}

* CQ-4357226: Fix regression in the IMS Configurations support for OAuth credentials.
* GRANITE-51335: Ratelimit upgrade naar 5.0.4 Fixed Felix Health Check registrations.

### Bekende problemen {#known-issues-15977}

* **(Alleen voor AEM Forms)** Nadat u AEM onderhoudsversie 15977 van de Cloud Foundation hebt geïnstalleerd, worden de velden Adaptief formulier in de onjuiste volgorde weergegeven tijdens het ontwerpen van formulieren en voor gepubliceerde formulieren. Als u AEM Forms gebruikt om ongemak te voorkomen, wordt u geadviseerd niet bij te werken naar de release van 15977 totdat het probleem is opgelost in de volgende onderhoudsversie.


### Verouderde functies en API&#39;s {#deprecated-15977}

* [JWT Credentials Deprection in Adobe Developer Console](/help/security/jwt-credentials-deprecation-in-adobe-developer-console.md)

Kijk eens naar [Verouderde en verwijderde functies en API&#39;s](/help/release-notes/deprecated-removed-features.md) om te weten wat in AEM as a Cloud Service is vervangen of verwijderd.

### Ingesloten technologieën {#embedded-tech-15977}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM AK | 1 62,0 | [API voor eik 1.62.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.62.0/index.html) |
| AEM SLING-API | 2.27.2. | [API voor Apache Sling API 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.20-1.4.0 | [HTML Sjabloontaalspecificaties](https://github.com/adobe/htl-spec) |
| AEM-kerncomponenten | 2,24,6 | [AEM WCM Core-componenten](https://github.com/adobe/aem-core-wcm-components) |
