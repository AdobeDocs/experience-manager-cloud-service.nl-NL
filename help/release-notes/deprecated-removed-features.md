---
title: Verouderde en verwijderde functies
description: Opmerkingen bij de release die specifiek zijn voor vervangen en verwijderde functies in [!DNL Adobe Experience Manager] als [!DNL Cloud Service].
exl-id: ef082184-4eb7-49c7-8887-03d925e3da6f
source-git-commit: 9316018864c3bb0bbca3f03a6fe2f6cad809159f
workflow-type: tm+mt
source-wordcount: '1707'
ht-degree: 0%

---

# Verouderde en verwijderde functies en API&#39;s {#deprecated-and-removed-features-apis}

>[!CONTEXTUALHELP]
>id="aem_cloud_deprecated_features"
>title="Vervangen en verwijderde functies in AEM as a Cloud Service"
>abstract="AEM as a Cloud Service heeft een implementatiemodel in de cloud. Bepaalde mogelijkheden en functies zijn vervangen door in de cloud geïntegreerde tegenhangers en op dit tabblad worden die functies weergegeven."


Adobe evalueert voortdurend de productmogelijkheden, om oudere eigenschappen met modernere alternatieven te heruitvinden of te vervangen om de algemene waarde van de klant te verbeteren, altijd onder zorgvuldige overweging van achterwaartse verenigbaarheid. Ook, als [!DNL Adobe Experience Manager] als [!DNL Cloud Service] biedt een implementatiemodel in de cloud, bepaalde mogelijkheden en functies zijn vervangen door in de cloud geïntegreerde tegenhangers.

De aanstaande verwijdering/vervanging van [!DNL Experience Manager] vermogens zijn de volgende regels van toepassing :

1. Aankondiging van afkeuring komt voorop. Verouderde mogelijkheden blijven beschikbaar maar worden niet verder uitgebreid.
1. Capabilities waarvan is aangekondigd dat ze zullen worden afgekeurd, worden ten vroegste in de volgende grote release verwijderd. De werkelijke streefdatum voor verwijdering wordt bekendgemaakt.

Dit proces biedt klanten minstens één releasecyclus om hun implementatie aan een nieuwe versie of opvolger van een vervangen capaciteit aan te passen, alvorens daadwerkelijke verwijdering.

## Verouderde functies {#deprecated-features}

Deze sectie bevat een lijst met functies en mogelijkheden die zijn gemarkeerd als verouderd in [!DNL Experience Manager] als [!DNL Cloud Service]. Functies die in een toekomstige versie moeten worden verwijderd, worden doorgaans eerst vervangen door een alternatief.

Klanten wordt aangeraden na te gaan of zij de functie/functionaliteit in hun huidige implementatie gebruiken en plannen te maken om hun implementatie te wijzigen en het meegeleverde alternatief te gebruiken.

| Mogelijkheden | Verouderde functie | Vervanging |
| ------------ | ------------------ | ----------- |
| [!DNL Sites] | Eigenschappen van Experience Fragments voor **Status van sociale media**. | De functie wordt binnenkort verwijderd. |
| [!DNL Sites] | Eenvoudige inhoudsfragmenten op basis van een sjabloon. | [Op modellen gebaseerde gestructureerde inhoudsfragmenten](/help/assets/content-fragments/content-fragments-models.md) nu. |
| [!DNL Assets] | `DAM Asset Update` werkwijze voor het verwerken van opgenomen afbeeldingen. | Bij gebruik van middelen [microservices voor bedrijfsmiddelen](/help/assets/asset-microservices-overview.md) nu. |
| [!DNL Assets] | Elementen rechtstreeks uploaden naar [!DNL Experience Manager]. Zie [verouderde API&#39;s voor middelenupload](/help/assets/developer-reference-material-apis.md#deprecated-asset-upload-api). | Gebruiken [Direct binair uploaden](/help/assets/add-assets.md). Voor technische details, zie [directe upload-API&#39;s](/help/assets/developer-reference-material-apis.md#upload-binary). |
| [!DNL Assets] | [Bepaalde workflowstappen](/help/assets/developer-reference-material-apis.md#post-processing-workflows-steps) in `DAM Asset Update` werkstroom wordt niet ondersteund, inclusief het aanroepen van opdrachtregelprogramma&#39;s zoals [!DNL ImageMagick]. | [Middelenmicroservices](/help/assets/asset-microservices-overview.md) bieden een vervanging voor veel workflows. Gebruik voor aangepaste verwerking [nabewerkingsworkflows](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows). |
| [!DNL Assets] | MPEG-transcodering van video&#39;s. | Gebruik voor het genereren van miniaturen in MPEG [Middelenmicroservices](/help/assets/asset-microservices-overview.md). Gebruik voor MPEG-transcodering [Dynamic Media](/help/assets/manage-video-assets.md). |
| [!DNL Foundation] | De replicatie UI van de boom onder het &quot;Distribute&quot;lusje van de replicatieagent (verwijdering na 30 September, 2021) | [Publicatie beheren](/help/operations/replication.md#manage-publication) of [workflow voor publicatiestructuur](/help/operations/replication.md#publish-content-tree-workflow) benaderingen |
| [!DNL Foundation] | Noch kan het lusje van de Distribute van het scherm van de replicatieagent admin noch de Replicatie API worden gebruikt om inhoudspakketten over 10MB (handhaving na 12 september 2022) te herhalen | [Publicatie beheren](/help/operations/replication.md#manage-publication) of [workflow voor publicatiestructuur](/help/operations/replication.md#publish-content-tree-workflow) benaderingen |


| [!DNL Foundation]       | U kunt inhoudspakketten niet repliceren via het tabblad Distribute van het scherm van de replicatieagent en de Replicatie-API. In plaats daarvan kunt u beide [Publicatie beheren](/help/operations/replication.md#manage-publication) of [workflow voor publicatiestructuur](/help/operations/replication.md#publish-content-tree-workflow) |

## Verwijderde functies {#removed-features}

Deze sectie bevat een lijst met functies en mogelijkheden die zijn verwijderd uit [!DNL Experience Manager] with [!DNL Experience Manager] als [!DNL Cloud Service].

| Gebied | Functie | Vervanging | Datum van verwijderen doel |
| ------------ | ------------------ | ----------- | ------------------- |
| Gebruikersinterface | Klassieke UI wordt verwijderd uit het product gebruikersinterface. Een paar Klassieke dialogen UI zijn beschikbaar voor een paar uitgezochte mogelijkheden, zoals de Controleur van de Verbinding, de Leegmaken van de Versie, en sommige configuraties van de Cloud Service. Binnenkort [productupdates](/help/release-notes/home.md) kan de beschikbaarheid van de klassieke gebruikersinterface verder verwijderen. | Standaardinterface | Verwijderd |
| [!DNL Dynamic Media] | Eerdere integratie met [Dynamic Media Classic](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/scene7.html#integration) en [Dynamic Media Hybride, modus](https://experienceleague.adobe.com/docs/experience-manager-65/assets/dynamic/config-dynamic.html#dynamic) niet beschikbaar in [!DNL Experience Manager] als [!DNL Cloud Service]. | Gebruiken [Dynamic Media](/help/assets/dynamic-media/dynamic-media.md) verstrekt [!DNL Experience Manager] als [!DNL Cloud Service]. | Verwijderd |
| [!DNL Sites] | Portal Director en Portlet-component | Deze mogelijkheden zijn vervangen in [!DNL Experience Manager] 6.4 en zijn nu verwijderd uit [!DNL Experience Manager]. | Verwijderd |
| [!DNL Sites] | Design Importer | Deze mogelijkheid is verwijderd als onveranderlijke gedeelten van het dialoogvenster [!DNL Experience Manager] opslagruimte zijn niet toegankelijk bij uitvoering. | Verwijderd |
| [!DNL Assets] | [!DNL Assets] delen met Marketing Cloud Assets Core Service en Creative Cloud services is niet beschikbaar. | Voor integratie met [!DNL Adobe Creative Cloud], gebruik [Adobe-itemkoppeling](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html). | Verwijderd |
| [!DNL Foundation] | Ondersteuning voor Apache Sling-gegevensbronnen (OSGi bundle org.apache.sling.datasource) | NVT | Verwijderd |
| [!DNL Foundation] | Ondersteuning voor JST-scriptsjablonen (OSGi bundle org.apache.sling.scripting.jst) | NVT | Verwijderd |
| [!DNL Foundation] | Ondersteuning voor het Apache Felix Http-whiteboard | OSGi Http-whiteboard | maart 2022 |
| [!DNL Foundation] | Ondersteuning voor com.adobe.granite.oauth.server | Adobe IMS-integratie | maart 2023 |

## OSGI-configuratie {#osgi-configuration}

Zie [dit artikel](/help/implementing/deploying/osgi-configuration-api.md) voor eventuele beperkingen met betrekking tot de configuratie van OSGI-eigenschappen, waarvan sommige in de loop der tijd kunnen worden ingevoerd.

## API&#39;s AEM {#aem-apis}

Hieronder vindt u een uitgebreide lijst met verouderde AEM API&#39;s en de verwachte verwijderingsdatum. Van klanten wordt verwacht dat ze de API&#39;s verwijderen tegen de verwijderingsdatum van het doel uit hun code. Elk gebruik van de API na de verwijderingsdatum leidt tot fouten in de lokale SDK/Development Environment en het buildproces van Cloud Manager.

<details>
  <summary>Vouw uit om de lijst met verouderde API's weer te geven.</summary>
<table style="table-layout:auto">
  <tr>
    <th>Pakket/klasse</th>
    <th>Opmerkingen</th>
    <th>Vervaldatum</th>
    <th>Datum van verwijderen doel</th>
  </tr>
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
    <td>verwijderd</td>
  </tr>
  <tr>
    <td>org.apache.sling.settings</td>
    <td>AEM as a Cloud Service ondersteunt geen uitvoermodi of toegang tot het bestandssysteem tijdens runtime. </td>
    <td>05-10-20</td>
    <td>Eind 2021</td>
  </tr>
  <tr>
    <td>org.apache.fop.apps</td>
    <td></td>
    <td>01-03-21</td>
    <td>verwijderd</td>
  </tr>
  <tr>
    <td>org.apache.jackrabbit.vault.util.xml.xerces.dom<br>org.apache.jackrabbit.vault.util.xml.xerces.util<br>org.apache.jackrabbit.vault.util.xml.xerces.xni<br>org.apache.jackrabbit.vault.util.xml.xerces.xni.parser</td>
    <td></td>
    <td>05-03-21</td>
    <td>verwijderd</td>
  </tr>
  <tr>
    <td>org.json</td>
    <td>De uitvoering van de Apache Johnzon <a href="https://johnzon.apache.org/index.html">javax.json</a> wordt aanbevolen en dient te worden gebruikt. </td>
    <td>30-04-21</td>
    <td>31-12-21</td>
  </tr>
  <tr>
    <td>org.apache.felix.cm<br>org.apache.felix.cm.file</td>
    <td>Aangepaste persistentiemanagers worden niet ondersteund in AEM as a Cloud Service.</td>
    <td>30-04-21</td>
    <td>verwijderd</td>
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
    <td>verwijderd</td>
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
    <td>Het gebruik van deze API wordt niet ondersteund in AEM as a Cloud Service.</td>
    <td>27-05-21</td>
    <td>30-07-21</td>
  </tr>
  <tr>
    <td>org.apache.felix.metatype<br>org.apache.felix.scr<br>org.apache.felix.scr.info<br>org.apache.felix.scr.component</td>
    <td>Het metatype van Apache Felix en SCR APIs zijn verouderd.  Gebruik in plaats hiervan de OSGi-metatype en Declarative Service API's.</td>
    <td>27-05-21</td>
    <td>verwijderd</td>
  </tr>
  <tr>
    <td>org.slf4j.impl</td>
    <td>De de implementatieklassen van het logboek zijn niet compatibel met AEM as a Cloud Service.</td>
    <td>04-07-21</td>
    <td>verwijderd</td>
  </tr>
  <tr>
    <td>org.apache.abdera<br>org.apache.abdera.model<br>org.apache.abdera.factory<br>org.apache.abdera.ext.media<br>org.apache.abdera.util<br>org.apache.abdera.i18n.iri<br>org.apache.abdera.writer<br>org.apache.abdera.i18n.rfc4646<br>org.apache.abdera.i18n.rfc4646.enums<br>org.apache.abdera.i18n.text<br>org.apache.abdera.filter<br>org.apache.abdera.xpath<br>org.apache.abdera.i18n.text.io<br>org.apache.abdera.i18n.text.data<br>org.apache.abdera.parser</td>
    <td>Deze API is verouderd omdat Apache Abdera sinds 2017 een gepensioneerd project is.</td>
    <td>29-07-21</td>
    <td>29-09-21</td>
  </tr>
  <tr>
    <td>org.apache.abdera.ext.opensearch<br>org.apache.abdera.ext.opensearch.model<br>org.apache.abdera.ext.opensearch.server<br>org.apache.abdera.ext.opensearch.server.impl<br>org.apache.abdera.ext.opensearch.server.processors<br>org.apache.abdera.i18n.iri.data<br>org.apache.abdera.i18n.lang<br>org.apache.abdera.i18n.templates<br>org.apache.abdera.i18n.unicode.data<br>org.apache.abdera.parser.stax<br>org.apache.abdera.parser.stax.util<br>org.apache.abdera.protocol<br>org.apache.abdera.protocol.client<br>org.apache.abdera.protocol.client.cache<br>org.apache.abdera.protocol.client.util<br>org.apache.abdera.protocol.error<br>org.apache.abdera.protocol.server<br>org.apache.abdera.protocol.server.context<br>org.apache.abdera.protocol.server.filters<br>org.apache.abdera.protocol.server.impl<br>org.apache.abdera.protocol.server.multipart<br>org.apache.abdera.protocol.server.processors<br>org.apache.abdera.protocol.server.provider.basic<br>org.apache.abdera.protocol.server.provider.managed<br>org.apache.abdera.protocol.server.servlet<br>org.apache.abdera.protocol.util<br>org.apache.abdera.util.filter</td>
    <td>Deze API is verouderd omdat Apache Abdera sinds 2017 een gepensioneerd project is.</td>
    <td>08-04-19</td>
    <td>29-09-21</td>
  </tr>
  <tr>
    <td>org.apache.sling.startupfilter<br>com.adobe.granite.crypto.spi<br>com.adobe.granite.crpyto.spi.base<br>com.adobe.agl.impl.data.icudt40b<br>com.adobe.agl.impl.data.icudt40b.brkitr<br>com.adobe.agl.impl.data.icudt40b.coll<br>com.adobe.agl.impl.data.icudt40b.rbnf<br>com.<br>adobe.agl.impl.data.icudt40b.translit<br>com.adobe.internal.pdf.tika<br>com.adobe.internal.pdftoolkit.color<br>com.adobe.internal.pdftoolkit.core.encryption<br>com.adobe.internal.pdftoolkit.core.encryption.impl<br>com.adobe.internal.pdftoolkit.core.traverser<br>com.adobe.internal.pdftoolkit.graphicsDOM<br>com.adobe.internal.pdftoolkit.graphicsDOM.shading<br>com.adobe.internal.pdftoolkit.graphicsDOM.utils<br>com.adobe.internal.pdftoolkit.image<br>com.adobe.internal.pdftoolkit.pdf.content<br>com.adobe.internal.pdftoolkit.pdf.content.processor<br>com.adobe.internal.pdftoolkit.pdf.content.processor.base14fontwidths<br>com.adobe.internal.pdftoolkit.pdf.contentmodify<br>com.adobe.internal.pdftoolkit.pdf.contentmodify.impl<br>com.adobe.internal.pdftoolkit.pdf.digsig<br>com.adobe.internal.pdftoolkit.pdf.document<br>com.adobe.internal.pdftoolkit.pdf.document.listener<br>com.adobe.internal.pdftoolkit.pdf.document.permissionhandlers<br>com.adobe.internal.pdftoolkit.pdf.filters<br>com.adobe.internal.pdftoolkit.pdf.graphics<br>com.adobe.internal.pdftoolkit.pdf.graphics.colorspaces<br>com.adobe.internal.pdftoolkit.pdf.graphics.colorspaces.cmykresources<br>com.adobe.internal.pdftoolkit.pdf.graphics.font<br>com.adobe.internal.pdftoolkit.pdf.graphics.font.encodings<br>com.adobe.internal.pdftoolkit.pdf.graphics.font.impl<br>com.adobe.internal.pdftoolkit.pdf.graphics.impl<br>com.adobe.internal.pdftoolkit.pdf.graphics.optionalcontent<br>com.adobe.internal.pdftoolkit.pdf.graphics.patterns<br>com.adobe.internal.pdftoolkit.pdf.graphics.shading<br>com.adobe.internal.pdftoolkit.pdf.graphics.xobject<br>com.adobe.internal.pdftoolkit.pdf.impl<br>com.adobe.internal.pdftoolkit.pdf.inlineimage<br>com.adobe.internal.pdftoolkit.pdf.interactive<br>com.adobe.internal.pdftoolkit.pdf.interactive.action<br>com.adobe.internal.pdftoolkit.pdf.interactive.annotation<br>com.adobe.internal.pdftoolkit.pdf.interactive.forms<br>com.adobe.internal.pdftoolkit.pdf.interactive.forms.impl<br>com.adobe.internal.pdftoolkit.pdf.interactive.geospatial<br>com.adobe.internal.pdftoolkit.pdf.interactive.markedcontent<br>com.adobe.internal.pdftoolkit.pdf.interactive.navigation<br>com.adobe.internal.pdftoolkit.pdf.interactive.navigation.collection<br>com.adobe.internal.pdftoolkit.pdf.interactive.readerrequirements<br>com.adobe.internal.pdftoolkit.pdf.interactive.requirement<br>com.adobe.internal.pdftoolkit.pdf.interchange<br>com.adobe.internal.pdftoolkit.pdf.interchange.documentparts<br>com.adobe.internal.pdftoolkit.pdf.interchange.metadata<br>com.adobe.internal.pdftoolkit.pdf.interchange.prepress<br>com.adobe.internal.pdftoolkit.pdf.interchange.structure<br>com.adobe.internal.pdftoolkit.pdf.multimedia<br>com.adobe.internal.pdftoolkit.pdf.page<br>com.adobe.internal.pdftoolkit.pdf.rendering<br>com.adobe.internal.pdftoolkit.pdf.transparency<br>com.adobe.internal.pdftoolkit.pdf.utils<br>com.adobe.internal.pdftoolkit.services.Jpeg2000<br>com.adobe.internal.pdftoolkit.services.fontresources<br>com.adobe.internal.pdftoolkit.services.fontresources.subsetting<br>com.adobe.internal.pdftoolkit.services.interchange.structure<br>com.adobe.internal.pdftoolkit.services.optionalcontent<br>com.adobe.internal.pdftoolkit.services.optionalcontent.impl<br>com.adobe.internal.pdftoolkit.services.pdfParser<br>com.adobe.internal.pdftoolkit.services.permissions<br>com.adobe.internal.pdftoolkit.services.rasterizer<br>com.adobe.internal.pdftoolkit.services.readingorder<br>com.adobe.internal.pdftoolkit.services.security<br>com.adobe.internal.pdftoolkit.services.swf<br>com.adobe.internal.pdftoolkit.services.textextraction<br>com.adobe.internal.pdftoolkit.services.textextraction.impl<br>com.adobe.internal.pdftoolkit.services.xmp<br>com.adobe.internal.util.base64<br>com.adobe.internal.xmp.utils<br>com.day.crx.core.cluster<br>com.day.crx.packaging<br>com.day.crx.packaging.gfx<br>com.day.crx.query<br>com.day.crx.sling.server.jmx<br>com.day.durbo<br>com.day.durbo.io<br>com.day.imageio.plugins<br>org.apache.aries.jmx.codec<br>org.h2.mvstore<br>org.h2.mvstore.rtree<br>org.h2.mvstore.type<br>org.openxmlformats.schemas.drawingml.x2006.chart.impl<br>org.openxmlformats.schemas.drawingml.x2006.main.impl<br>org.openxmlformats.schemas.drawingml.x2006.picture.impl<br>org.openxmlformats.schemas.drawingml.x2006.spreadsheetDrawing.impl<br>org.openxmlformats.schemas.drawingml.x2006.wordprocessingDrawing.impl<br>org.openxmlformats.schemas.officeDocument.x2006.customProperties.impl<br>org.openxmlformats.schemas.officeDocument.x2006.docPropsVTypes.impl<br>org.openxmlformats.schemas.officeDocument.x2006.extendedProperties.impl<br>org.openxmlformats.schemas.officeDocument.x2006.relationships.impl<br>org.openxmlformats.schemas.presentationml.x2006.main.impl<br>org.openxmlformats.schemas.spreadsheetml.x2006.main.impl<br>org.openxmlformats.schemas.wordprocessingml.x2006.main.impl<br>org.openxmlformats.schemas.xpackage.x2006.contentTypes<br>org.openxmlformats.schemas.xpackage.x2006.contentTypes.impl<br>org.openxmlformats.schemas.xpackage.x2006.digitalSignature<br>org.openxmlformats.schemas.xpackage.x2006.digitalSignature.impl<br>org.openxmlformats.schemas.xpackage.x2006.metadata.coreProperties<br>org.openxmlformats.schemas.xpackage.x2006.metadata.coreProperties.impl<br>org.openxmlformats.schemas.xpackage.x2006.relationships<br>org.openxmlformats.schemas.xpackage.x2006.relationships.impl<br>com.adobe.internal.afml<br>com.adobe.internal.agm<br>com.adobe.internal.pdftoolkit.legacy.services.ap.es2<br>com.adobe.internal.pdftoolkit.legacy.services.ap.es3<br>com.adobe.internal.pdftoolkit.pdf.pieceinfo.compoundtype<br>com.adobe.internal.pdftoolkit.pdf.pieceinfo.editablepdf<br>com.adobe.internal.pdftoolkit.services.ap<br>com.adobe.internal.pdftoolkit.services.ap.annot<br>com.adobe.internal.pdftoolkit.services.ap.extension<br>com.adobe.internal.pdftoolkit.services.ap.impl<br>com.adobe.internal.pdftoolkit.services.ap.spi<br>com.adobe.internal.pdftoolkit.services.digsig<br>com.adobe.internal.pdftoolkit.services.digsig.cryptoprovider<br>com.adobe.internal.pdftoolkit.services.digsig.docmodanalysis<br>com.adobe.internal.pdftoolkit.services.digsig.spi<br>com.adobe.internal.pdftoolkit.services.fdf<br>com.adobe.internal.pdftoolkit.services.formflattener<br>com.adobe.internal.pdftoolkit.services.forms<br>com.adobe.internal.pdftoolkit.services.imageconversion<br>com.adobe.internal.pdftoolkit.services.javascript<br>com.adobe.internal.pdftoolkit.services.javascript.extension<br>com.adobe.internal.pdftoolkit.services.manipulations<br>com.adobe.internal.pdftoolkit.services.manipulations.impl<br>com.adobe.internal.pdftoolkit.services.optimizer<br>com.adobe.internal.pdftoolkit.services.pdfa<br>com.adobe.internal.pdftoolkit.services.pdfa.error<br>com.adobe.internal.pdftoolkit.services.pdfa2<br>com.adobe.internal.pdftoolkit.services.pdfa2.error<br>com.adobe.internal.pdftoolkit.services.pdfa2.error.codes<br>com.adobe.internal.pdftoolkit.services.pdfa3<br>com.adobe.internal.pdftoolkit.services.pdfport<br>com.adobe.internal.pdftoolkit.services.portfolio<br>com.adobe.internal.pdftoolkit.services.rcg<br>com.adobe.internal.pdftoolkit.services.rcg.impl<br>com.adobe.internal.pdftoolkit.services.redaction<br>com.adobe.internal.pdftoolkit.services.redaction.handler<br>com.adobe.internal.pdftoolkit.services.sanitization<br>com.adobe.internal.pdftoolkit.services.xbm<br>com.adobe.internal.pdftoolkit.services.xdp<br>com.adobe.internal.pdftoolkit.services.xfa<br>com.adobe.internal.pdftoolkit.services.xfa.form<br>com.adobe.internal.pdftoolkit.services.xfatext<br>com.adobe.internal.pdftoolkit.services.xfdf<br>com.adobe.internal.pdftoolkit.services.xobjhandler<br>com.adobe.internal.pdftoolkit.xml<br>com.adobe.octopus.extract<br>opennlp.tools.doccat<br>opennlp.tools.entitylinker<br>opennlp.tools.formats<br>opennlp.tools.formats.ad<br>opennlp.tools.formats.brat<br>opennlp.tools.formats.convert<br>opennlp.tools.formats.frenchtreebank<br>opennlp.tools.formats.muc<br>opennlp.tools.formats.ontonotes<br>opennlp.tools.lemmatizer<br>opennlp.tools.parser<br>opennlp.tools.parser.chunking<br>opennlp.tools.parser.lang.en<br>opennlp.tools.parser.lang.es<br>opennlp.tools.parser.treeinsert<br>opennlp.tools.sentdetect<br>opennlp.tools.sentdetect.lang<br>opennlp.tools.sentdetect.lang.th<br>opennlp.tools.stemmer<br>opennlp.tools.stemmer.snowball<br>opennlp.tools.tokenize.lang.en<br>org.apache.commons.imaging.color<br>org.apache.commons.imaging.common<br>org.apache.commons.imaging.common.itu_t4<br>org.apache.commons.imaging.common.mylzw<br>org.apache.commons.imaging.formats.bmp<br>org.apache.commons.imaging.formats.dcx<br>org.apache.commons.imaging.formats.gif<br>org.apache.commons.imaging.formats.icns<br>org.apache.commons.imaging.formats.ico<br>org.apache.commons.imaging.formats.jpeg<br>org.apache.commons.imaging.formats.jpeg.decoder<br>org.apache.commons.imaging.formats.jpeg.exif<br>org.apache.commons.imaging.formats.jpeg.iptc<br>org.apache.commons.imaging.formats.jpeg.segments<br>org.apache.commons.imaging.formats.jpeg.xmp<br>org.apache.commons.imaging.formats.pcx<br>org.apache.commons.imaging.formats.png<br>org.apache.commons.imaging.formats.png.chunks<br>org.apache.commons.imaging.formats.png.scanlinefilters<br>org.apache.commons.imaging.formats.png.transparencyfilters<br>org.apache.commons.imaging.formats.pnm<br>org.apache.commons.imaging.formats.psd<br>org.apache.commons.imaging.formats.psd.dataparsers<br>org.apache.commons.imaging.formats.psd.datareaders<br>org.apache.commons.imaging.formats.rgbe<br>org.apache.commons.imaging.formats.tiff<br>org.apache.commons.imaging.formats.tiff.constants<br>org.apache.commons.imaging.formats.tiff.datareaders<br>org.apache.commons.imaging.formats.tiff.fieldtypes<br>org.apache.commons.imaging.formats.tiff.photometricinterpreters<br>org.apache.commons.imaging.formats.tiff.taginfos<br>org.apache.commons.imaging.formats.tiff.write<br>org.apache.commons.imaging.formats.wbmp<br>org.apache.commons.imaging.formats.xbm<br>org.apache.commons.imaging.formats.xpm<br>org.apache.commons.imaging.icc<br>org.apache.commons.imaging.palette<br>org.apache.commons.imaging.util<br>com.adobe.dam.print.ids.utils<br>com.day.cq.dam.api.reporting<br>com.day.cq.dam.entitlement.api<br>com.day.cq.dam.handler.standard.epub<br>com.day.cq.dam.handler.standard.keynote<br>com.day.cq.dam.handler.standard.mp3<br>com.day.cq.dam.handler.standard.msoffice<br>com.day.cq.dam.handler.standard.msoffice.wmf<br>com.day.cq.dam.handler.standard.ooxml<br>com.day.cq.dam.handler.standard.pdf<br>com.day.cq.dam.handler.standard.pict<br>com.day.cq.dam.handler.standard.ps<br>com.day.cq.dam.handler.standard.psd<br>com.day.cq.dam.handler.standard.zip<br>com.day.cq.dam.word.extraction<br>com.day.cq.dam.word.process<br>com.adobe.xmp.worker.files<br>com.adobe.cq.address.api<br>com.adobe.cq.address.api.location<br>com.day.cq.mcm.emailprovider.impl.types<br>com.day.io<br>com.day.io.disk<br>com.day.io.file<br>org.apache.commons.exec.environment<br>org.apache.commons.exec.launcher<br>org.apache.commons.exec.util<br>com.google.zxing<br>com.google.zxing.common<br>com.google.zxing.common.reedsolomon<br>com.google.zxing.qrcode.decoder<br>com.google.zxing.qrcode.encoder<br>com.adobe.cq.dam.dm.internalapi.image_server<br>com.day.cq.dam.api.s7dam.jobs<br>com.day.cq.dam.api.s7dam.omnisearch<br>com.day.cq.dam.api.s7dam.scene7<br>com.day.cq.dam.scene7<br>com.day.cq.dam.scene7.api.net<br>com.day.cq.analytics.sitecatalyst.rsmerger<br>com.day.cq.searchpromote<br>com.day.cq.searchpromote.xml<br>com.day.cq.searchpromote.xml.form<br>com.day.cq.searchpromote.xml.result&gt;</td>
    <td>Verouderd AEM 6.x API.</td>
    <td>08-04-19</td>
    <td>verwijderd</td>
  </tr>
  <tr>
    <td>org.apache.sling.discovery.commons<br>org.apache.sling.discovery.commons.providers<br>org.apache.sling.discovery.commons.providers.base<br>org.apache.sling.discovery.commons.providers.spi<br>org.apache.sling.discovery.commons.providers.spi.base<br>org.apache.sling.discovery.commons.providers.util</td>
    <td>Deze API wordt niet ondersteund in Cloud Service.</td>
    <td>30-09-21</td>
    <td>verwijderd</td>
  </tr>
  <tr>
    <td>org.apache.jackrabbit.vault.util.xml<br>org.apache.jackrabbit.vault.util.xml.serialize</td>
    <td>Util-klassen die verwant zijn aan Apache Xerces worden verwijderd in volgende releases die een belangrijke versiewijziging veroorzaken. Aangezien deze hulpprogramma's bedoeld zijn voor intern gebruik in FileVult, wordt de API afgekeurd ten opzichte van het openbare API-oppervlak.</td>
    <td>01-09-21</td>
    <td>verwijderd</td>
  <tr>
    <td>org.apache.sling.atom.taglib<br>org.apache.sling.atom.taglib.media</td>
    <td>Verouderd AEM 6.x API.</td>
    <td>08-04-19</td>
    <td>29-09-21</td>
  </tr>
  <tr>
    <td>org.apache.felix.http.whiteboard</td>
    <td>Het Apache Felix Http-whiteboard wordt niet meer ondersteund. Migreer uw code naar het whiteboard van OSGi Http.</td>
    <td>27-01-2022</td>
    <td>24-03-2022</td>
  </tr>
  <tr>
    <td>org.apache.cocoon.xml.dom<br>org.apache.cocoon.xml.sax</td>
    <td>Deze API is vervangen, migreer uw code aan XML APIs die door JDK worden verstrekt.</td>
    <td>27-01-2022</td>
    <td>24-03-2022</td>
  </tr>
  <tr>
    <td>ch.qos.logback.classic<br>ch.qos.logback.classic.boolex<br>ch.qos.logback.classic.db.names<br>ch.qos.logback.classic.db.script<br>ch.qos.logback.classic.encoder<br>ch.qos.logback.classic.filter<br>ch.qos.logback.classic.helpers<br>ch.qos.logback.classic.html<br>ch.qos.logback.classic.jmx<br>ch.qos.logback.classic.joran<br>ch.qos.logback.classic.joran.action<br>ch.qos.logback.classic.jul<br>ch.qos.logback.classic.layout<br>ch.qos.logback.classic.log4j<br>ch.qos.logback.classic.net<br>ch.qos.logback.classic.net.server<br>ch.qos.logback.classic.pattern<br>ch.qos.logback.classic.pattern.color<br>ch.qos.logback.classic.selector<br>ch.qos.logback.classic.selector.servlet<br>ch.qos.logback.classic.servlet<br>ch.qos.logback.classic.sift<br>ch.qos.logback.classic.spi<br>ch.qos.logback.classic.turbo<br>ch.qos.logback.classic.util<br>ch.qos.logback.core<br>ch.qos.logback.core.boolex<br>ch.qos.logback.core.encoder<br>ch.qos.logback.core.filter<br>ch.qos.logback.core.helpers<br>ch.qos.logback.core.hook<br>ch.qos.logback.core.html<br>ch.qos.logback.core.joran<br>ch.qos.logback.core.joran.action<br>ch.qos.logback.core.joran.conditional<br>ch.qos.logback.core.joran.event<br>ch.qos.logback.core.joran.event.stax<br>ch.qos.logback.core.joran.node<br>ch.qos.logback.core.joran.spi<br>ch.qos.logback.core.joran.util<br>ch.qos.logback.core.joran.util.beans<br>ch.qos.logback.core.layout<br>ch.qos.logback.core.net<br>ch.qos.logback.core.net.server<br>ch.qos.logback.core.net.ssl<br>ch.qos.logback.core.pattern<br>ch.qos.logback.core.pattern.color<br>ch.qos.logback.core.pattern.parser<br>ch.qos.logback.core.pattern.util<br>ch.qos.logback.core.property<br>ch.qos.logback.core.read<br>ch.qos.logback.core.recovery<br>ch.qos.logback.core.rolling<br>ch.qos.logback.core.rolling.helper<br>ch.qos.logback.core.sift<br>ch.qos.logback.core.spi<br>ch.qos.logback.core.status<br>ch.qos.logback.core.subst<br>ch.qos.logback.core.util</td>
    <td>Deze interne logback-API wordt niet ondersteund door AEM as a Cloud Service.</td>
    <td>27-01-2022</td>
    <td>24-03-2022</td>
  </tr>
  <tr>
    <td>org.slf4j.spi</td>
    <td>Deze interne log4j API wordt niet ondersteund door AEM as a Cloud Service.</td>
    <td>27-01-2022</td>
    <td>24-03-2022</td>
  </tr>
  <tr>
    <td>org.apache.log4j<br>org.apache.log4j.helpers<br>org.apache.log4j.spi<br>org.apache.log4j.xml</td>
    <td>Apache Log4j 1 heeft het einde van zijn levensduur bereikt in 2015 en wordt niet meer ondersteund.</td>
    <td>27-01-2022</td>
    <td>24-03-2022</td>
  </tr>
  <tr>
    <td>org.apache.sling.commons.log.logback<br>org.apache.sling.commons.log.logback.webconsole</td>
    <td>Deze interne logback-API wordt niet ondersteund door AEM as a Cloud Service.</td>
    <td>27-01-2022</td>
    <td>verwijderd</td>
  </tr>
  <tr>
    <td>com.github.jknack.handlebars.js</td>
    <td>Vanwege beveiligingskwetsbaarheid is een upgrade van Handlebars vereist van 4.0.5 naar 4.3.0. Dit pakket is niet meer aanwezig in de bijgewerkte handgrepen.</td>
    <td>05-05-2022</td>
    <td>05-08-2022</td>
  </tr>
  <tr>
    <td>com.adobe.granite.resourceresolverhelper</td>
    <td>Deze API wordt niet meer ondersteund. Gebruik in plaats hiervan org.apache.sling.api.resource.ResourceResolverFactory.</td>
    <td>29-09-2022</td>
    <td>24-11-2022</td>
  </tr>
  <tr>
    <td>com.day.cq.contentsync.handler.util</td>
    <td>Deze API is vervangen. Gebruik in plaats hiervan Apache Sling's Builders.</td>
    <td>31-10-2022</td>
    <td>01-01-2023</td>
  </tr>
  <tr><td>org.apache.sling.commons.json<br>org.apache.sling.commons.json.http<br>org.apache.sling.commons.json.io<br>org.apache.sling.commons.json.jcr<br>org.apache.sling.commons.json.sling<br>org.apache.sling.commons.json.util<br>org.apache.sling.commons.json.xml</td>
    <td>Deze API wordt niet ondersteund door AEM as a Cloud Service.</td>
    <td>15-05-2023</td>
    <td>15-06-2023</td>
  </tr><td>com.google.common.annotations<br>com.google.common.base<br>com.google.common.cache<br>com.google.common.collect<br>com.google.common.escape<br>com.google.common.eventbus<br>com.google.common.hash<br>com.google.common.html<br>com.google.common.io<br>com.google.common.math<br>com.google.common.net<br>com.google.common.primitives<br>com.google.common.reflect<br>com.google.common.util.concurrent<br>com.google.common.xml</td>
    <td>De Google Guava Core Libraries zijn verouderd.</td>
    <td>15-05-2023</td>
    <td>15-06-2023</td>
  </tr>
</tbody>
</table>
</details>
