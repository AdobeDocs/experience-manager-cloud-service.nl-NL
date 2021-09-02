---
title: OSGi-configuratie-API
description: Beschrijving van de AEM als OSGi-configuratieoppervlak van de Cloud Service
feature: Deploying
source-git-commit: 5223d57377f5c00b090aee1ddd4dbfe2d7113181
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---


# OSGi-configuratie-API

De twee lijsten hieronder wijzen op de AEM als Cloud Service OSGi configuratieoppervlakte, die welke klanten kunnen vormen.

1. Een lijst van configuraties OSGi die niet door klantencode moeten worden gevormd
1. Een lijst van configuraties OSGi waarvan de eigenschappen kunnen worden gevormd, maar moet zich aan de vermelde bevestigingsregels houden. Deze regels omvatten of verklaring van het bezit, zijn type, en in sommige gevallen, zijn toegestane waaier van waarden wordt vereist.

Als een configuratie OSGI niet vermeld is, kan het door klantencode worden gevormd.

Deze regels worden gevalideerd tijdens het ontwikkelingsproces van Cloud Manager. Er kunnen in de loop der tijd aanvullende regels worden toegevoegd en de verwachte datum van tenuitvoerlegging wordt in de tabel vermeld. Van klanten wordt verwacht dat zij zich aan deze regels houden tegen de beoogde handhavingsdatum. Als u zich na de verwijderingsdatum niet aan de regels houdt, worden er fouten gegenereerd in het buildproces van Cloud Manager. Gemaakte projecten zouden [AEM als Cloud Service SDK bouwt Analyzer Maven Plugin](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html) moeten omvatten om OSGI configuratiefouten tijdens lokale ontwikkeling van SDK te markeren.

Aanvullende informatie over de configuratie van OSGI vindt u op [deze locatie](/help/implementing/deploying/configuring-osgi.md).

## OSGi-configuraties die niet kunnen worden gewijzigd {#osgi-configurations-that-cannot-be-modified}

* **`org.apache.felix.webconsole.internal.servlet.OsgiManager`** (Aankondigingsdatum: 30-04-2021, Datum van tenuitvoerlegging: (31-07-2021)
* **`com.day.cq.auth.impl.cug.CugSupportImpl`** (Aankondigingsdatum: 30-04-2021, Datum van tenuitvoerlegging: (31-07-2021)
* **`com.day.cq.jcrclustersupport.ClusterStartLevelController`** (Aankondigingsdatum: 30-04-2021, Datum van tenuitvoerlegging: (31-07-2021)
* **`org.apache.felix.http (Factory)`** (Aankondigingsdatum: 30-04-2021, Datum van tenuitvoerlegging: (31-07-2021)
* **`org.apache.sling.jcr.davex.impl.servlets.SlingDavExServlet`** (Aankondigingsdatum: 25-08-2021, Datum van tenuitvoerlegging: (26-11-2021)

## OSGi Configurations onderworpen aan de Regels van de Bevestiging van de Bouwstijl {#osgi-configurations-subject-to-build-validation-rules}

* **`org.apache.felix.eventadmin.impl.EventAdmin`** (Aankondigingsdatum: 30-04-2021, Datum van tenuitvoerlegging: (31-07-2021)
   * `org.apache.felix.eventadmin.ThreadPoolSize`
      * Type: integer
      * Vereist bereik: 2-100
   * `org.apache.felix.eventadmin.AsyncToSyncThreadRatio`
      * Type: double
   * `org.apache.felix.eventadmin.Timeout`
      * Type: integer
   * `org.apache.felix.eventadmin.RequireTopic`
      * Type: boolean
   * `org.apache.felix.eventadmin.IgnoreTimeout`
      * Vereist
      * Type: array van tekenreeksen
      * Vereist bereik: Moet ten minste alle `org.apache.felix*`, `org.apache.sling*`, `come.day*`, `com.adobe*` bevatten
   * `org.apache.felix.eventadmin.IgnoreTopic`
      * Type: array van tekenreeksen
* **`org.apache.felix.http`** (Aankondigingsdatum: 30-04-2021, Datum van tenuitvoerlegging: (31-07-2021)
   * `org.apache.felix.http.timeout`
      * Type: integer
   * `org.apache.felix.http.session.timeout`
      * Type: integer
   * `org.apache.felix.http.jetty.threadpool.max`
      * Type: integer
   * `org.apache.felix.http.jetty.headerBufferSize`
      * Type: integer
   * `org.apache.felix.http.jetty.requestBufferSize`
      * Type: integer
   * `org.apache.felix.http.jetty.responseBufferSize`
      * Type: integer
   * `org.apache.felix.http.jetty.maxFormSize`
      * Type: integer
   * `org.apache.felix.https.jetty.session.cookie.httpOnly`
      * Type: boolean
   * `org.apache.felix.https.jetty.session.cookie.secure`
      * Type: boolean
   * `org.eclipse.jetty.servlet.SessionIdPathParameterName`
      * Type: string
   * `org.eclipse.jetty.servlet.CheckingRemoteSessionIdEncoding`
      * Type: boolean
   * `org.eclipse.jetty.servlet.SessionCookie`
      * Type: string
   * `org.eclipse.jetty.servlet.SessionDomain`
      * Type: string
   * `org.eclipse.jetty.servlet.SessionPath`
      * Type: string
   * `org.eclipse.jetty.servlet.MaxAge`
      * Type: integer
   * `org.eclipse.jetty.servlet.SessionScavengingInterval`
      * Type: integer
   * `org.apache.felix.jetty.gziphandler.enable`
      * Type: boolean
   * `org.apache.felix.jetty.gzip.minGzipSize`
      * Type: integer
   * `org.apache.felix.jetty.gzip.compressionLevel`
      * Type: integer
   * `org.apache.felix.jetty.gzip.inflateBufferSize`
      * Type: integer
   * `org.apache.felix.jetty.gzip.syncFlush`
      * Type: boolean
   * `org.apache.felix.jetty.gzip.excludedUserAgents`
      * Type: string
   * `org.apache.felix.jetty.gzip.includedMethods`
      * Type: array van tekenreeksen
   * `org.apache.felix.jetty.gzip.excludedMethods`
      * Type: array van tekenreeksen
   * `org.apache.felix.jetty.gzip.includedPaths`
      * Type: array van tekenreeksen
   * `org.apache.felix.jetty.gzip.excludedPaths`
      * Type: array van tekenreeksen
   * `org.apache.felix.jetty.gzip.includedMimeTypes`
      * Type: array van tekenreeksen
   * `org.apache.felix.jetty.gzip.excludedMimeTypes`
      * Type: array van tekenreeksen
   * `org.apache.felix.http.session.invalidate`
      * Type: boolean
   * `org.apache.felix.http.session.container.attribute`
      * Type: array van tekenreeksen
   * `org.apache.felix.http.session.uniqueid`
      * Type: boolean
* **`org.apache.sling.scripting.cache`** (Aankondigingsdatum: 30-04-2021, Datum van tenuitvoerlegging: (31-07-2021)
   * `org.apache.sling.scripting.cache.size`
      * Type: integer
      * Vereist bereik: >= 2048
   * `org.apache.sling.scripting.cache.additional_extensions`
      * Vereist
      * Type: array van tekenreeksen
      * Vereist bereik: moet JS bevatten
* **`com.day.cq.mailer.DefaultMailService`** (Aankondigingsdatum: 30-04-2021, Datum van tenuitvoerlegging: (31-07-2021)
   * `smtp.host`
      * Type: string
   * `smtp.port`
      * Type: integer
      * Vereist bereik: 465, 587 of 25
   * `smtp.user`
      * Type: string
   * `smtp.password`
      * Type: string
   * `from.address`
      * Type: string
   * `smtp.ssl`
      * Type: string
   * `smtp.starttls`
      * Type: boolean
   * `smtp.requiretls`
      * Type: boolean
   * `debug.email`
      * Type: boolean
   * `oauth.flow`
      * Type: boolean
