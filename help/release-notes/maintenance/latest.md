---
title: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 3fbdb150a9a1c133b4910603682e37f1c5d885d2
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 1%

---

# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In de volgende sectie worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van as a Cloud Service Experience Manager beschreven.

## Release 13804 {#release-13804}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 13804 samengevat, die op 10 oktober 2023 openbaar werd gemaakt. Deze onderhoudrelease is een update van eerdere onderhoudrelease 13665.

2023.10.0 Activering van de functie biedt de volledige functie die is ingesteld voor deze onderhoudsrelease. Zie de [Experience Manager geeft Routekaart vrij](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html) voor meer informatie .

### Verbeteringen {#enhancements-13804}

* GRANITE-47238: Het Onderhoud van het Logboek van de controle - zuivert contraJob om de klantenconfiguratie te gebruiken.
* GRANITE-47123: Publiceer (het Schilderen) - verbeter starttijd door het geheime voorgeheugen van de ijdelingspad asynchroon door gebrek te initialiseren.
* GRANITE-46618: Publiceer (Replicatie) - verbeter Publish startsnelheid door de berichten van de replicatiestatus batching.
* GRANITE-47136: Indexering (download) - Verbeter downloadsnelheid van nieuwe parallelle indexdownloader (door checksum bevestiging onbruikbaar te maken).
* GRANITE-47211: Publiceer (Infra) - verbeter ontkoppeling van de plaatsingen van de Publish rij (door de naam van de segmentwinkelrevisie op te slaan en te halen).
* GRANITE-47267: Update aan Apache Felix Http Jetty 4.2.18 (omvat insectenmoeilijke situatie voor de behandeling van de verzoekparameter ([FELIX-6625](https://issues.apache.org/jira/browse/FELIX-6625)) met prestatieverbeteringen voor lokale en RDE-ontwikkelingen).
* GRANITE-47247: Update to Sling Servlets Resolver 2.9.14 met prestatiesverbeteringen in servletresolutie.

### Opgeloste problemen {#fixed-issues-13804}

* GRANITE-47376: Auteur (Infra) - Oplossing voor DiscoveryTopologyUndefined fouten na het rollen opnieuw beginnen.
* CQ-4353436: AEM Webconsole (het Sling) - Lege configuraties in Validators ServiceUserMapperImpl (Hoofd/Gebruiker) onderbrekingen AEM Instantie ([SLING-1912](https://issues.apache.org/jira/browse/SLING-11912)).
* SKYOPS-63925: De Baan van de transformatie - vermijd mislukkingen TransformJob met JDK 11 - ZipException: Ongeldige CEN kopbalfouten (met disableZip64ExtraFieldValidation JVM vlag).
* SKYOPS-63361: De Baan van de transformatie (het Registreren) verbeterde het registreren met de Banen van de Transformatie (substep CUSTOMER_EXTRACT).
* SKYOPS-64103: Het Hulpmiddel van de FACT (het Registreren) - vermindert, of beknott Clientlib compilatiefout en waarschuwingsberichten.
* SKYOPS-65109: Het Hulpmiddel van de FACT (de Verwerking van de Fout) - de Pakketten van de inhoud met onopgeloste gebiedsdelen resulteert in een behoorlijk gerapporteerde fout.
* SKYOPS-65368: FACT Tool (Error Handling) - Het hulpmiddel loopt in eindeloze integratiecyclus en uiteindelijk keren uit op kringvormige bedden van Clientlibs.
* SKYOPS-64031: RDE - ComponentCacheImpl kan in inconsistent staat wegens dubbele registratie ResourceResolverFactory ([SLING-12019](https://issues.apache.org/jira/browse/SLING-12019)).
* ASSETS-29105: RDE - Restriction provider missing from SecurityProviderRegistration requiredServicePids in RDE feature model.
* GRANITE-44674: CoralUI - Datepicker vereiste gebiedsfunctionaliteit is onjuist.

### Bekende problemen {#known-issues-13804}

Geen.

### Ingesloten technologieën {#embedded-tech-13804}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM AK | 1,56-T20230927085643-189caed | [API 1.56.0 voor ongewenste API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.56.0/index.html) |
| AEM SLING-API | Versie 2.27.2 | [API voor Apache Sling API 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Versie 1.4.20-1.4.0 | [HTML Sjabloontaalspecificaties](https://github.com/adobe/htl-spec) |
| AEM-kerncomponenten | Versie 2.23.4 | [AEM WCM Core-componenten](https://github.com/adobe/aem-core-wcm-components) |
