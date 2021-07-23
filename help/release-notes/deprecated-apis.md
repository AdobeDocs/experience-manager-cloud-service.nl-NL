---
title: Verouderde API's
description: Release-aantekeningen specifiek voor afgekeurde en verwijderde API's in [!DNL Adobe Experience Manager] as a [!DNL Cloud Service].
exl-id: fbd8c60a-3e2b-4696-aaba-f4db97923184
source-git-commit: 02b610b830911b737f8caa7356d0e446958bcc2f
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 7%

---

# Verouderde API&#39;s {#deprecated-apis}

Hieronder vindt u een uitgebreide lijst met verouderde AEM API&#39;s en de verwachte verwijderingsdatum. Van klanten wordt verwacht dat ze de API&#39;s verwijderen tegen de verwijderingsdatum van het doel uit hun code. Elk gebruik van de API na de verwijderingsdatum leidt tot fouten in de lokale SDK/Development Environment en het buildproces van Cloud Manager.


<table>
<thead>
  <tr>
    <th>Pakket/klasse</th>
    <th>Opmerkingen</th>
    <th>Vervaldatum</th>
    <th>Datum van verwijderen doel</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>org.apache.sling.commons.auth<br>org.apache.sling.commons.auth.spi</td>
    <td>De Auth Core/Auth Core SPI van Sling gebruiken interfaces als alternatief</td>
    <td>2015</td>
    <td>30-07-21</td>
  </tr>
  <tr>
    <td>org.apache.sling.runmode</td>
    <td></td>
    <td>2015</td>
    <td>30-07-21</td>
  </tr>
  <tr>
    <td>com.day.cq.jcrclustersupport</td>
    <td>Detectie-API van Sling gebruiken als alternatief</td>
    <td>2015</td>
    <td>30-07-21</td>
  </tr>
  <tr>
    <td>org.apache.sling.settings</td>
    <td>AEM als Cloud Service ondersteunt geen uitvoermodi of toegang tot het bestandssysteem tijdens runtime. </td>
    <td>05-10-20</td>
    <td>Eind 2021</td>
  </tr>
  <tr>
    <td>org.apache.fop.apps</td>
    <td></td>
    <td>01-03-21</td>
    <td>01-06-21</td>
  </tr>
  <tr>
    <td>org.apache.jackrabbit.vault.util.xml.xerces.dom<br>org.apache.jackrabbit.vault.util.xml.xerces.util<br>org.apache.jackrabbit.vault.util.xml.xerces.xni<br>org.apache.jackrabbit.vault.util.xml.xerces.xni.parser</td>
    <td></td>
    <td>05-03-21</td>
    <td>06-06-21</td>
  </tr>
  <tr>
    <td>org.json</td>
    <td>De Apache Johnzon-implementatie van <a href="https://johnzon.apache.org/index.html">javax.json</a> wordt aanbevolen en moet worden gebruikt. </td>
    <td>30-04-21</td>
    <td>31-12-21</td>
  </tr>
  <tr>
    <td>org.apache.felix.cm<br>org.apache.felix.cm.file</td>
    <td>Aangepaste persistentiemanagers worden niet ondersteund in AEM als Cloud Service.</td>
    <td>30-04-21</td>
    <td>30-07-21</td>
  </tr>
  <tr>
    <td>org.apache.commons.lang<br>org.apache.commons.lang.enums<br>org.apache.commons.lang.builder<br>org.apache.commons.lang.exception<br>org.apache.commons.lang.math<br>org.apache.commons.lang.mutable<br>org.apache.commons.lang.reflect<br>org.apache.commons.lang.text<br>org.apache.commons.lang.time</td>
    <td>Commons Lang 2 is op onderhoudswijze. In plaats daarvan moet Commons Lang 3 worden gebruikt.</td>
    <td>30-04-21</td>
    <td>31-12-21</td>
  </tr>
  <tr>
    <td>org.apache.commons.collections<br>org.apache.commons.collections.bag<br>org.apache.commons.collections.bidimap<br>org.apache.commons.collections.buffer<br>org.apache.commons.collections.collection<br>org.apache.commons.collections.comparators<br>org.apache.commons.collections.functors<br>org.apache.commons.collections.iterators<br>org.apache.commons.collections.keyvalue<br>org.apache.commons.collections.list<br>org.apache.commons.collections.map<br>org.apache.commons.collections.set</td>
    <td>Gemeenschappelijke Collections 3 is in onderhoudsmodus. In plaats daarvan moeten gemeenschappelijke verzamelingen 4 worden gebruikt.</td>
    <td>30-04-21</td>
    <td>31-12-21</td>
  </tr>
  <tr>
    <td>org.apache.felix.systemready</td>
    <td>Het wordt aanbevolen de API voor Apache Felix HealthCheck te gebruiken</td>
    <td>30-04-21</td>
    <td>30-07-21</td>
  </tr>
  <tr>
    <td>org.apache.felix.webconsole<br>org.apache.felix.webconsole.bundleinfo<br>org.apache.felix.webconsole.i18n</td>
    <td>De Felix-webconsole wordt niet ondersteund in Cloud-omgevingen</td>
    <td>30-04-21</td>
    <td>30-07-21</td>
  </tr>
  <tr>
    <td>org.apache.felix.http.jetty<br>org.eclipse.jetty.http<br>org.eclipse.jetty.http.pathmap<br>org.eclipse.jetty.io<br>org.eclipse.jetty.io.ssl<br>org.eclipse.jetty.jmx<br>org.eclipse.jetty.security<br>org.eclipse.jetty.server<br>org.eclipse.jetty.server.handler<br>org.eclipse.jetty.server.handler.gzip<br>org.eclipse.jetty.server.handler.jmx<br>org.eclipse.jetty.server.jmx<br>org.eclipse.jetty.server.nio<br>org.eclipse.jetty.server.session<br>org.eclipse.jetty.servlet<br>org.eclipse.jetty.servlet.jmx<br>org.eclipse.jetty.servlet.listener<br>org.eclipse.jetty.util<br>org.eclipse.jetty.util.annotation<br>org.eclipse.jetty.util.component<br>org.eclipse.jetty.util.log<br>org.eclipse.jetty.util.preventers<br>org.eclipse.jetty.util.resource<br>org.eclipse.jetty.util.security<br>org.eclipse.jetty.util.ssl<br>org.eclipse.jetty.util.statistic<br>org.eclipse.jetty.util.thread<br>org.eclipse.jetty.util.thread.strategy<br>org.eclipse.jetty.webapp<br>org.eclipse.jetty.websocket.api<br>org.eclipse.jetty.websocket.api.annotations<br>org.eclipse.jetty.websocket.api.extensions<br>org.eclipse.jetty.websocket.api.util<br>org.eclipse.jetty.websocket.client<br>org.eclipse.jetty.websocket.client.io<br>org.eclipse.jetty.websocket.client.masks<br>org.eclipse.jetty.websocket.common<br>org.eclipse.jetty.websocket.common.events<br>org.eclipse.jetty.websocket.common.events.annotated<br>org.eclipse.jetty.websocket.common.extensions<br>org.eclipse.jetty.websocket.common.extensions.compress<br>org.eclipse.jetty.websocket.common.extensions.fragment<br>org.eclipse.jetty.websocket.common.extensions.identity<br>org.eclipse.jetty.websocket.common.frames<br>org.eclipse.jetty.websocket.common.io<br>org.eclipse.jetty.websocket.common.io.http<br>org.eclipse.jetty.websocket.common.io.payload<br>org.eclipse.jetty.websocket.common.message<br>org.eclipse.jetty.websocket.common.scopes<br>org.eclipse.jetty.websocket.common.util<br>org.eclipse.jetty.websocket.server<br>org.eclipse.jetty.websocket.server.pathmap<br>org.eclipse.jetty.websocket.servlet<br>org.eclipse.jetty.xml<br>org.eclipse.jetty.client<br>org.eclipse.jetty.client.api<br>org.eclipse.jetty.client.http<br>org.eclipse.jetty.client.jmx<br>org.eclipse.jetty.client.util</td>
    <td>De pakketten Eclipse Jetty en Felix HTTP Jetty worden niet meer ondersteund.</td>
    <td>27-05-21</td>
    <td>26-08-21</td>
  </tr>
  <tr>
    <td>com.mongodb<br>com.mongodb.annotations<br>com.mongodb.assertions<br>com.mongodb.async<br>com.mongodb.binding<br>com.mongodb.bulk<br>com.mongodb.client<br>com.mongodb.client.gridfs<br>com.mongodb.client.gridfs.codecs<br>com.mongodb.client.gridfs.model<br>com.mongodb.client.jndi<br>com.mongodb.client.model<br>com.mongodb.client.model.changestream<br>com.mongodb.client.model.geojson<br>com.mongodb.client.model.geojson.codecs<br>com.mongodb.client.result<br>com.mongodb.connection<br>com.mongodb.connection.netty<br>com.mongodb.diagnostics.logging<br>com.mongodb.event<br>com.mongodb.gridfs<br>com.mongodb.internal<br>com.mongodb.internal.async<br>com.mongodb.internal.authentication<br>com.mongodb.internal.connection<br>com.mongodb.internal.dns<br>com.mongodb.internal.event<br>com.mongodb.internal.management.jmx<br>com.mongodb.internal.session<br>com.mongodb.internal.thread<br>com.mongodb.internal.validator<br>com.mongodb.management<br>com.mongodb.operation<br>com.mongodb.selector<br>com.mongodb.session<br>com.mongodb.util</td>
    <td>Het gebruik van deze API wordt niet ondersteund in AEM als Cloud Service.</td>
    <td>27-05-21</td>
    <td>30-07-21</td>
  </tr>
  <tr>
    <td>org.apache.felix.metatype<br>org.apache.felix.scr<br>org.apache.felix.scr.info</td>
    <td>Het metatype van Apache Felix en SCR APIs zijn verouderd.  Gebruik in plaats hiervan de OSGi-metatype- en Declarative Service-API's.</td>
    <td>27-05-21</td>
    <td>26-08-21</td>
  </tr>
</tbody>
</table>
