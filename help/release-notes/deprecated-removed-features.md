---
title: Verouderde en verwijderde functies
description: De nota's van de versie specifiek voor afgekeurde en verwijderde eigenschappen in  [!DNL Adobe Experience Manager]  als a  [!DNL Cloud Service].
mini-toc-levels: 1
exl-id: ef082184-4eb7-49c7-8887-03d925e3da6f
feature: Release Information
role: Admin
source-git-commit: 910876ef77698680266a2ef99cd5650b0adbd1ac
workflow-type: tm+mt
source-wordcount: '3695'
ht-degree: 0%

---

# Verouderde en verwijderde functies en API&#39;s {#deprecated-and-removed-features-apis}

>[!CONTEXTUALHELP]
>id="aem_cloud_deprecated_features"
>title="Verouderde en verwijderde functies in AEM as a Cloud Service"
>abstract="AEM as a Cloud Service heeft een implementatiemodel in de cloud. Dit tabblad markeert functies en mogelijkheden die zijn vervangen door hun in de cloud geïntegreerde tegenhangers."

Adobe controleert regelmatig functies, waaronder API&#39;s en configuraties, om ervoor te zorgen dat deze voldoen aan de veranderende standaarden voor prestaties, beveiliging en algemene waarde voor AEM as a Cloud Service. Op basis van deze evaluaties kunnen bepaalde mogelijkheden worden gemarkeerd voor afschrijving. Indien mogelijk zal Adobe een geschikte vervanging bieden.

Wanneer een afschrijving wordt aangekondigd, blijft de functie slechts voor een beperkte periode beschikbaar en moeten klanten alle gebruik voor een opgegeven verwijderingsdatum verwijderen. Adobe zal een redelijke kennisgeving en richtsnoeren verstrekken om een soepele overgang te ondersteunen.

Tijdens het venster met de verouderingstijd herinnert Adobe klanten aan de acties die ze moeten uitvoeren om een functie niet meer te gebruiken via e-mailmeldingen, waarschuwingen van het Actions Center of herinneringen in Cloud Manager.

>[!WARNING]
>
>In sommige gevallen is verwijdering van een functie vereist voordat een nieuwe Cloud Manager-build of upgrade naar de nieuwste versie van AEM as a Cloud Service wordt geïmplementeerd.

>[!IMPORTANT]
>
>Verscheidene [&#x200B; afgekeurde APIs &#x200B;](#aem-apis) richten verwijdering op **26 Februari, 2026**. Wijzig deze belangrijkste datums en effecten:
>
>* **Beginnend Januari 26, 2026**: Het bericht van het Centrum van acties e-mails wordt verzonden **wekelijks per milieu** als herinnering om gebruik van deze APIs te verwijderen.
>* **februari 26, 2026**: De pijpleidingen van Cloud Manager die code bevatten die deze APIs gebruiken zullen **pauzeren** tijdens de **Kwaliteit van de Code** stap. Een Manager van de Plaatsing, de Manager van het Project, of BedrijfsEigenaar kunnen de kwestie met voeten treden om de pijpleiding toe te staan om te werk te gaan.
>* **Maart 26, 2026**: De pijpleidingen van Cloud Manager die code bevatten die deze APIs gebruiken zullen **&#x200B;**&#x200B;tijdens de **Kwaliteit van de Code** stap ontbreken, **blokkerend plaatsingen** van nieuwe code tot het gebruik wordt verwijderd.
>* **April 30, 2026**: De milieu&#39;s die nog deze APIs gebruiken kunnen **niet meer kritieke de releaseupdates van Adobe ontvangen**.
>
>Als u implementatieblokken wilt voorkomen, verwijdert u het API-gebruik vóór 26 maart 2026.

## Verouderde functionaliteit {#deprecated-features}

De functionaliteit in de onderstaande tabel is aangekondigd als afgekeurd, maar is nog niet verwijderd.  Het gebruik van de functionaliteit moet worden beëindigd vóór de verwijderingsdatum van het doel of u riskeert problemen met betrekking tot prestaties, beschikbaarheid en beveiliging.

| Mogelijkheden | Verouderde functie | Vervanging |
| ------------ | ------------------ | ----------- |
| Sites | [&#x200B; de Steun van het Fragment van de Inhoud in HTTP API van Assets &#x200B;](/help/assets/content-fragments/assets-api-content-fragments.md) | [&#x200B; Levering van het Fragment van de Inhoud met OpenAPI &#x200B;](/help/headless/aem-content-fragment-delivery-with-openapi.md)<br> samen met <br> [&#x200B; de Fragmenten van de Inhoud en Modellen van het Fragment van de Inhoud Management OpenAPIs &#x200B;](/help/headless/content-fragment-openapis.md) |
| Sites | [&#x200B; Eigenschappen van PWA &#x200B;](/help/sites-cloud/authoring/sites-console/enable-pwa.md) | Geen |
| Sites | [&#x200B; Redacteur van het KUUROORD &#x200B;](/help/implementing/developing/hybrid/introduction.md) | De aangewezen redacteurs voor het beheren van hoofdloze inhoud in AEM zijn:<br> - [&#x200B; de Universele Redacteur &#x200B;](https://www.aem.live/docs/aem-authoring) voor het visuele uitgeven.<br> - [&#x200B; de Redacteur van het Fragment van de Inhoud &#x200B;](/help/assets/content-fragments/content-fragments-managing.md) voor op vorm-gebaseerde het uitgeven. |
| [!DNL Sites] | [&#x200B; Gebruik API van JavaScript &#x200B;](https://github.com/adobe/htl-spec/blob/master/SPECIFICATION.md#42-javascript-use-api) | [&#x200B; Gebruik API van Java &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-htl/content/java-use-api) |
| [!DNL Sites] | De eigenschappen van Fragmenten van de ervaring voor **Sociale Status van Media**. | De functie wordt binnenkort verwijderd. |
| Sites | [&#x200B; de Automatisering van de Opstelling van Experience Cloud &#x200B;](/help/sites-cloud/integrating/adobe-analytics-exc-setup-automation.md) | Geen |
| [!DNL Sites] | Eenvoudige inhoudsfragmenten op basis van een sjabloon. | [&#x200B; Model-Gebaseerde gestructureerde inhoudsfragmenten &#x200B;](/help/assets/content-fragments/content-fragments-models.md) nu. |
| [!DNL Assets] | `DAM Asset Update` gebruiken om opgenomen afbeeldingen te verwerken. | De opname van activa gebruikt [&#x200B; activa microservices &#x200B;](/help/assets/asset-microservices-overview.md) nu. |
| [!DNL Assets] | Upload elementen rechtstreeks naar [!DNL Experience Manager] . Zie [&#x200B; afgekeurde activa uploaden APIs &#x200B;](/help/assets/developer-reference-material-apis.md#deprecated-asset-upload-api). | Het gebruik [&#x200B; Directe binaire upload &#x200B;](/help/assets/add-assets.md). Voor technische details, zie [&#x200B; directe upload APIs &#x200B;](/help/assets/developer-reference-material-apis.md#upload-binary). |
| [!DNL Assets] | [&#x200B; Bepaalde werkschemasstappen &#x200B;](/help/assets/developer-reference-material-apis.md#post-processing-workflows-steps) in `DAM Asset Update` werkschema worden niet gesteund, met inbegrip van het roepen van bevel-lijn hulpmiddelen zoals [!DNL ImageMagick]. | [&#x200B; microservices van Activa &#x200B;](/help/assets/asset-microservices-overview.md) verstrekken een vervanging voor vele werkschema&#39;s. Voor douaneverwerking, gebruik [&#x200B; post-verwerkings werkschema&#39;s &#x200B;](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows). |
| [!DNL Assets] | MPEG-transcodering van video&#39;s. | Voor de duimnagelgeneratie van MPEG, gebruik [&#x200B; microservices van Activa &#x200B;](/help/assets/asset-microservices-overview.md). Voor transcodering MPEG, gebruik [&#x200B; Dynamische Media &#x200B;](/help/assets/manage-video-assets.md). |
| [!DNL Foundation] | De replicatie UI van de boom onder de replicatieagenten &quot;verdelen&quot;tabel (verwijdering na 30 September, 2021) | [&#x200B; beheer publicatie &#x200B;](/help/operations/replication.md#manage-publication) of [&#x200B; Stap van het Werkschema van de Activering van de Boom &#x200B;](/help/operations/replication.md#tree-activation) benaderingen. |
| [!DNL Foundation] | Het tabblad Distribueren van het scherm van de replicatieagent en de API voor replicatie kunnen geen inhoudspakketten repliceren die groter zijn dan 10 MB. | [&#x200B; beheer publicatie &#x200B;](/help/operations/replication.md#manage-publication) of [&#x200B; Stap van het Werkschema van de Activering van de Boom &#x200B;](/help/operations/replication.md#tree-activation) |
| [!DNL Foundation] | Integraties die gebruik maken van referenties die zijn gegenereerd uit Adobe Developer Console-projecten verliezen geleidelijk de ondersteuning voor JWT-referenties (Service Account). Vanaf 1 mei 2024 kunnen geen JWT-referenties (New Service Account) meer worden gemaakt in Adobe Developer Console. De bestaande geloofsbrieven van de Rekening van de Dienst (JWT) blijven bruikbaar voor gevormde integratie tot 1 Januari, 2025, waarna zij ophouden werkend, die klanten vereisen om aan Server-aan-Server geloofsbrieven van OAuth te migreren. [&#x200B; leer meer &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/security/jwt-credentials-deprecation-in-adobe-developer-console). | [&#x200B; migreer &#x200B;](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration#migration-overview) aan OAuth server-aan-Server geloofsbrieven. |
| [!DNL Foundation] | De workflow van de inhoudsstructuur publiceren en de gerelateerde workflowstap voor de publicatiestructuur, die werd gebruikt voor replicaties van hiërarchieën van inhoud. | De Stap van het Werkschema van de Activering van de Boom van het gebruik [&#x200B; &#x200B;](/help/operations/replication.md#tree-activation), die uitvoeriger is. |
| [!DNL Foundation] | Met YUI JavaScript-clientbibliotheken comprimeren/miniaturen maken. Adobe is niet van plan de YUI-bibliotheek verder bij te werken. | Adobe raadt klanten aan over te schakelen op de Google Closure Compiler (GCC) voor hun implementatie. |
| [!DNL Foundation] | Ondersteuning voor com.adobe.granite.oauth.server | Adobe IMS-integratie |

## Verwijderde functionaliteit {#removed-features}

Deze sectie bevat een lijst met functies die zijn verwijderd.

| Gebied | Functie | Vervanging | Datum van verwijderen doel |
| ------------ | ------------------ | ----------- | ------------------- |
| Gebruikersinterface | Klassieke UI wordt verwijderd uit het product gebruikersinterface. Er zijn enkele klassieke UI-dialoogvensters beschikbaar voor een paar geselecteerde mogelijkheden, zoals Koppelingencontrole, Versiegroepering en sommige Cloud Service-configuraties. De komende [&#x200B; productupdates &#x200B;](/help/release-notes/home.md) kunnen Klassieke beschikbaarheid verder verwijderen UI. | Standaardinterface | Verwijderd |
| [!DNL Dynamic Media] | De vorige integraties met [&#x200B; Dynamic Media Classic &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-65/content/sites/administering/integration/scene7#integration) en [&#x200B; Dynamische Hybride wijze van Media &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-65/content/assets/dynamic/config-dynamic#dynamic) zijn niet beschikbaar in [!DNL Experience Manager] als [!DNL Cloud Service]. | Het gebruik [&#x200B; Dynamische Media &#x200B;](/help/assets/dynamic-media/dynamic-media.md) van [!DNL Experience Manager] als a [!DNL Cloud Service] wordt voorzien die. | Verwijderd |
| [!DNL Sites] | Portal Director en Portlet-component | Deze functies zijn vervangen in [!DNL Experience Manager] 6.4 en zijn nu verwijderd uit [!DNL Experience Manager] . | Verwijderd |
| [!DNL Sites] | Design Importer | Deze mogelijkheid is verwijderd omdat onveranderlijke gedeelten van de [!DNL Experience Manager] -opslagplaats niet toegankelijk zijn tijdens runtime. | Verwijderd |
| [!DNL Assets] | [!DNL Assets] Delen met Assets Core Service en Creative Cloud-services is niet beschikbaar. | Voor integratie met [!DNL Adobe Creative Cloud], gebruik [&#x200B; de Verbinding van Activa van Adobe &#x200B;](https://helpx.adobe.com/nl/enterprise/using/adobe-asset-link.html). | Verwijderd |
| [!DNL Foundation] | Ondersteuning voor Apache Sling-gegevensbronnen (OSGi bundle org.apache.sling.datasource) | NVT | Verwijderd |
| [!DNL Foundation] | Ondersteuning voor JST-scriptsjablonen (OSGi bundle org.apache.sling.scripting.jst) | NVT | Verwijderd |
| [!DNL Foundation] | Ondersteuning voor het Apache Felix Http-whiteboard | OSGi Http-whiteboard | maart 2022 |
| [!DNL Foundation] | Steun voor org.apache.sling.usermapping eigenschap aan [&#x200B; krijgt de identiteitskaart van de dienstgebruiker &#x200B;](https://sling.apache.org/apidocs/sling12/org/apache/sling/serviceusermapping/ServiceUserMapper.html#getServiceUserID-org.osgi.framework.Bundle-java.lang.String-) | NVT | 30-08-24 |
| [!DNL Foundation] | Java 11-runtime is vervangen door Adobe door Java 21-runtime. Het is acceptabel dat code nog steeds in Java 11 wordt samengesteld (Java 17 en 21 zijn de andere opties) | Java 21-runtime wordt toegepast. Om verenigbaarheid te verzekeren, is het essentieel om bibliotheekversies bij te werken zoals die in [&#x200B; runtime vereisten &#x200B;](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements) worden geschetst | 29 maart 25 |

## Verouderde API&#39;s {#aem-apis}

De API&#39;s in de onderstaande tabel (klik om deze uit te vouwen) zijn aangekondigd als afgekeurd, maar zijn nog niet verwijderd.  Het gebruik van deze API&#39;s moet worden beëindigd vóór de verwijderingsdatum van het doel, anders loopt u risico&#39;s met betrekking tot prestaties, beschikbaarheid en beveiliging. Sommige API&#39;s verwijzen hieronder naar de sectie API Removal Guidance.

>[!IMPORTANT]
> Verscheidene APIs is gepland voor verwijdering op **26 Februari, 2026**. Wijzig deze belangrijkste datums en effecten:
>
> * **Beginnend Januari 26, 2026**: Het bericht van het Centrum van acties e-mails wordt verzonden **wekelijks per milieu** als herinnering om gebruik van deze APIs te verwijderen.
> * **februari 26, 2026**: De pijpleidingen van Cloud Manager die code bevatten die deze APIs gebruiken zullen **pauzeren** tijdens de **Kwaliteit van de Code** stap. Een Manager van de Plaatsing, de Manager van het Project, of BedrijfsEigenaar kunnen de kwestie met voeten treden om de pijpleiding toe te staan om te werk te gaan.
> * **Maart 26, 2026**: De pijpleidingen van Cloud Manager die code bevatten die deze APIs gebruiken zullen **&#x200B;**&#x200B;tijdens de **Kwaliteit van de Code** stap ontbreken, **blokkerend plaatsingen** van nieuwe code tot het gebruik wordt verwijderd.
> * **April 30, 2026**: De milieu&#39;s die nog deze APIs gebruiken kunnen **niet meer kritieke de releaseupdates van Adobe ontvangen**.
>
> Als u implementatieblokken wilt voorkomen, verwijdert u het API-gebruik vóór 26 maart 2026.


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
    <td>De interfaces van de Kern/van de Kern van de Auth van Sling van het gebruik als alternatief. <a href="#org.apache.sling.commons.auth"> zie hieronder verwijderingsnota's.</a></td>
    <td>2015</td>
    <td>26-02-2026</td>
  </tr>
  <tr>
<td>org.eclipse.jetty.client<br>org.eclipse.jetty.client.api<br>org.eclipse.jetty.client.http<br>org.eclipse.jetty.client.util<br>org.eclipse.jetty.http<br>org.eclipse.jetty.http.pathmap<br>org.eclipse.jetty.io<br>org.eclipse.jetty.io.ssl<br>org.eclipse.jetty.security<br>org.eclipse.jetty.server<br>org.eclipse.jetty.server.handler<br>org.eclipse.jetty.server.handler.gzip<br>org.eclipse.jetty.server.session<br>org.eclipse.jetty.servlet<br>org.eclipse.jetty.servlet.listener<br>org.eclipse.jetty.util<br>org.eclipse.jetty.util.annotation<br>org.eclipse.jetty.util.component<br>org.eclipse.jetty.util.log<br>org.eclipse.jetty.util.resource<br>org.eclipse.jetty.util.security<br>org.eclipse.jetty.util.ssl<br>org.eclipse.jetty.util.statistic<br>org.eclipse.jetty.util.thread</td>
    <td>De pakketten Eclipse Jetty en Felix HTTP Jetty worden niet meer ondersteund. <a href="#org.eclipse.jetty"> zie hieronder verwijderingsnota's.</a></td>
    <td>27-05-2021</td>
    <td>26-02-2026</td>
  </tr>
 <tr>     <td>com.mongodb<br>com.mongodb.annotations<br>com.mongodb.assertions<br>com.mongodb.async<br>com.mongodb.binding<br>com.mongodb.bulk<br>com.mongodb.client<br>com.mongodb.client.gridfs<br>com.mongodb.client.gridfs.codecs<br>com.mongodb.client.gridfs.model<br>com.mongodb.client.jndi<br>com.mongodb.client.model<br>com.mongodb.client.model.changestream<br>com.mongodb.client.model.geojson<br>com.mongodb.client.model.geojson.codecs<br>com.mongodb.client.result<br>com.mongodb.connection<br>com.mongodb.connection.netty<br>com.mongodb.diagnostics.logging<br>com.mongodb.event<br>com.mongodb.gridfs<br>com.mongodb.internal<br>com.mongodb.internal.async<br>com.mongodb.internal.authentication<br>com.mongodb.internal.connection<br>com.mongodb.internal.dns<br>com.mongodb.internal.event<br>com.mongodb.internal.management.jmx<br>com.mongodb.internal.session<br>com.mongodb.internal.thread<br>com.mongodb.internal.validator<br>com.mongodb.management<br>com.mongodb.operation<br>com.mongodb.selector<br>com.mongodb.session<br>com.mongodb.util</td>
    <td>Gebruik van deze API wordt niet ondersteund in AEM as a Cloud Service. <a href="#com.mongodb"> zie hieronder verwijderingsnota's.</a></td>
    <td>27-05-2021</td>
    <td>26-02-2026</td>
  </tr>
   <tr>
    <td>org.apache.abdera<br>org.apache.abdera.model<br>org.apache.abdera.factory<br>org.apache.abdera.ext.media<br>org.apache.abdera.util<br>org.apache.abdera.i18n.iri<br>org.apache.abdera.writer<br>org.apache.abdera.i18n.rfc4646<br>org.apache.abdera.i18n.rfc4646.enums<br>org.apache.abdera.i18n.text<br>org.apache.abdera.filter<br>org.apache.abdera.xpath<br>org.apache.abdera.i18n.text.io<br>org.apache.abdera.i18n.text.data<br>org.apache.abdera.parser</td>
    <td>Deze API is verouderd omdat Apache Abdera sinds 2017 een gepensioneerd project is. <a href="#org.apache.abdera_or_org.apache.sling.atom.taglib"> zie hieronder verwijderingsnota's.</a></td>
    <td>29-07-2021</td>
    <td>26-02-2026</td>
  </tr>
  <tr>
    <td>org.apache.abdera.ext.opensearch<br>org.apache.abdera.ext.opensearch.model<br>org.apache.abdera.ext.opensearch.server<br>org.apache.abdera.ext.opensearch.server.impl<br>org.apache.abdera.ext.opensearch.server.processors<br>org.apache.abdera.i18n.iri.data<br>org.apache.abdera.i18n.lang<br>org.apache.abdera.i18n.templates<br>org.apache.abdera.i18n.unicode.data<br>org.apache.abdera.parser.stax<br>org.apache.abdera.parser.stax.util<br>org.apache.abdera.protocol<br>org.apache.abdera.protocol.client<br>org.apache.abdera.protocol.client.cache<br>org.apache.abdera.protocol.client.util<br>org.apache.abdera.protocol.error<br>org.apache.abdera.protocol.server<br>org.apache.abdera.protocol.server.context<br>org.apache.abdera.protocol.server.filters<br>org.apache.abdera.protocol.server.impl<br>org.apache.abdera.protocol.server.multipart<br>org.apache.abdera.protocol.server.processors<br>org.apache.abdera.protocol.server.provider.basic<br>org.apache.abdera.protocol.server.provider.managed<br>org.apache.abdera.protocol.server.servlet<br>org.apache.abdera.protocol.util<br>org.apache.abdera.util.filter</td>
    <td>Deze API is verouderd omdat Apache Abdera sinds 2017 een gepensioneerd project is. <a href="#org.apache.abdera_or_org.apache.sling.atom.taglib"> zie hieronder verwijderingsnota's.</a></td>
    <td>08-04-2019</td>
    <td>26-02-2026</td>
  </tr>
  <tr>
    <td>org.apache.felix.http.whiteboard</td>
    <td>Het Apache Felix Http-whiteboard wordt niet meer ondersteund. Migreer uw code naar het whiteboard van OSGi Http. <a href="#org.apache.felix.http.whiteboard"> zie hieronder verwijderingsnota's.</a></td>
    <td>27-01-2022</td>
    <td>26-02-2026</td>
  </tr>
  <tr>
    <td>org.apache.cocoon.xml.dom<br>org.apache.cocoon.xml.sax</td>
    <td>Deze API is vervangen. Migreer uw code naar de XML APIs die door JDK worden verstrekt.</td>
    <td>27-01-2022</td>
    <td>26-02-2026</td>
  </tr>
  <tr>
    <td>ch.qos.logback.classic<br>ch.qos.logback.classic.boolex<br>ch.qos.logback.classic.db.names<br>ch.qos.logback.classic.db.script<br>ch.qos.logback.classic.encoder<br>ch.qos.logback.classic.filter<br>ch.qos.logback.classic.helpers<br>ch.qos.logback.classic.html<br>ch.qos.logback.classic.jmx<br>ch.qos.logback.classic.joran<br>ch.qos.logback.classic.joran.action<br>ch.qos.logback.classic.jul<br>ch.qos.logback.classic.layout<br>ch.qos.logback.classic.log4j<br>ch.qos.logback.classic.net<br>ch.qos.logback.classic.net.server<br>ch.qos.logback.classic.pattern<br>ch.qos.logback.classic.pattern.color<br>ch.qos.logback.classic.selector<br>ch.qos.logback.classic.selector.servlet<br>ch.qos.logback.classic.servlet<br>ch.qos.logback.classic.sift<br>ch.qos.logback.classic.spi<br>ch.qos.logback.classic.turbo<br>ch.qos.logback.classic.util<br>ch.qos.logback.core<br>ch.qos.logback.core.boolex<br>ch.qos.logback.core.encoder<br>ch.qos.logback.core.filter<br>ch.qos.logback.core.helpers<br>ch.qos.logback.core.hook<br>ch.qos.logback.core.html<br>ch.qos.logback.core.joran<br>ch.qos.logback.core.joran.action<br>ch.qos.logback.core.joran.conditional<br>ch.qos.logback.core.joran.event<br>ch.qos.logback.core.joran.event.stax<br>ch.qos.logback.core.joran.node<br>ch.qos.logback.core.joran.spi<br>ch.qos.logback.core.joran.util<br>ch.qos.logback.core.joran.util.beans<br>ch.qos.logback.core.layout<br>ch.qos.logback.core.net<br>ch.qos.logback.core.net.server<br>ch.qos.logback.core.net.ssl<br>ch.qos.logback.core.pattern<br>ch.qos.logback.core.pattern.color<br>ch.qos.logback.core.pattern.parser<br>ch.qos.logback.core.pattern.util<br>ch.qos.logback.core.property<br>ch.qos.logback.core.read<br>ch.qos.logback.core.recovery<br>ch.qos.logback.core.rolling<br>ch.qos.logback.core.rolling.helper<br>ch.qos.logback.core.sift<br>ch.qos.logback.core.spi<br>ch.qos.logback.core.status<br>ch.qos.logback.core.subst<br>ch.qos.logback.core.util</td>
    <td>AEM as a Cloud Service ondersteunt deze interne log back-API niet. <a href="#ch.qos.logback"> zie hieronder verwijderingsnota's.</a></td>
    <td>27-01-2022</td>
    <td>26-02-2026</td>
  </tr>
  <tr>
    <td>org.slf4j.spi</td>
    <td>AEM as a Cloud Service biedt geen ondersteuning voor deze interne log4j-API. <a href="#org.slf4j"> zie hieronder verwijderingsnota's.</a></td>
    <td>27-01-2022</td>
    <td>26-02-2026</td>
  </tr>
  <tr>
    <td>org.apache.log4j<br>org.apache.log4j.helpers<br>org.apache.log4j.spi<br>org.apache.log4j.xml</td>
    <td>Apache Log4j 1 heeft zijn einde in 2015 bereikt en wordt niet meer ondersteund. <a href="#org.apache.log4j"> zie hieronder verwijderingsnota's.</a></td>
    <td>27-01-2022</td>
    <td>26-02-2026</td>
  </tr>
  <tr>  <td>com.google.common.annotations<br>com.google.common.base<br>com.google.common.cache<br>com.google.common.collect<br>com.google.common.escape<br>com.google.common.eventbus<br>com.google.common.hash<br>com.google.common.html<br>com.google.common.io<br>com.google.common.math<br>com.google.common.net<br>com.google.common.primitives<br>com.google.common.reflect<br>com.google.common.util.concurrent<br>com.google.common.xml</td>
    <td>De Google Guava Core Libraries zijn verouderd in Cloud Service. <a href="#com.google.common"> zie hieronder verwijderingsnota's.</a></td>
    <td>15-05-2023</td>
    <td>26-02-2026</td>
  </tr>
  <tr>
    <td>org.slf4j.event</td>
    <td>AEM as a Cloud Service biedt geen ondersteuning voor deze interne slf4j API. <a href="#org.slf4j"> zie hieronder verwijderingsnota's.</a></td>
    <td>11-04-2022</td>
    <td>26-02-2026</td>
  </tr>
    <tr>
    <td>com.drew.*</td>
    <td>Metagegevens uit afbeeldingen en video's worden geëxtraheerd via Asset Compute in Cloud Service of via Apache POI of Apache Tika.</td>
    <td>17-09-2024</td>
    <td>26-02-2026</td>
  </tr>
  <tr>
    <td>org.apache.jackrabbit.oak.plugins.blob.*</td>
    <td>Deze API is alleen voor intern gebruik.</td>
    <td>23-09-2024</td>
    <td>26-02-2026</td>
  </tr>
  <tr>
    <td>org.apache.jackrabbit.oak.plugins.memory</td>
    <td>Deze API is alleen voor intern gebruik.</td>
    <td>23-09-2024</td>
    <td>26-02-2026</td>
  </tr>
  <tr>
<td>org.apache.felix.webconsole<br>org.apache.felix.webconsole.bundleinfo<br>org.apache.felix.webconsole.i18n<br>org.apache.felix.webconsole.spi</td>
    <td>De Felix-webconsole wordt niet ondersteund in Cloud-omgevingen. <a href="#org.apache.felix.webconsole"> zie hieronder verwijderingsnota's.</a></td>
    <td>30-04-2021</td>
    <td>26-02-2026</td>
  </tr>
<td>org.bson<br/>org.bson.assertions<br/>org.bson.codecs<br/>org.bson.codecs.configuration<br/>org.bson.codecs.pojo<br/>org.bson.codecs.pojo.annotations<br/>org.bson.conversions<br/>org.bson.diagnostics<br/>org.bson.internal<br/>org.bson.io<br/>org.bson.json<br/>org.bson.types<br/>org.bson.util</td>
    <td>Gebruik van deze API wordt niet ondersteund in AEM as a Cloud Service.</td>
    <td>31-10-2022</td>
    <td>26-02-2026</td>
  </tr>
  <tr>
    <td>org.apache.sling.runmode</td>
    <td></td>
    <td>2015</td>
    <td>TBD</td>
  </tr>
  <tr>
    <td>org.json</td>
    <td>De implementatie van Apache Johnzon van <a href="https://johnzon.apache.org/index.html"> javax.json </a> wordt geadviseerd en zou moeten worden gebruikt. </td>
    <td>30-04-2021</td>
    <td>TBD</td>
  </tr>
  <tr>
<td>org.apache.commons.lang<br>org.apache.commons.lang.enums<br>org.apache.commons.lang.builder<br>org.apache.commons.lang.exception<br>org.apache.commons.lang.math<br>org.apache.commons.lang.mutable<br>org.apache.commons.lang.reflect<br>org.apache.commons.lang.text<br>org.apache.commons.lang.time</td>
    <td>Commons Lang 2 is op onderhoudswijze. In plaats daarvan moet Commons Lang 3 worden gebruikt. <a href="#apache.commons"> zie hieronder verwijderingsnota's.</a></td>
    <td>30-04-2021</td>
    <td>TBD</td>
  </tr>
  <tr>
    <td>org.apache.commons.collections<br>org.apache.commons.collections.bag<br>org.apache.commons.collections.bidimap<br>org.apache.commons.collections.buffer<br>org.apache.commons.collections.collection<br>org.apache.commons.collections.comparators<br>org.apache.commons.collections.functors<br>org.apache.commons.collections.iterators<br>org.apache.commons.collections.keyvalue<br>org.apache.commons.collections.list<br>org.apache.commons.collections.map<br>org.apache.commons.collections.set</td>
    <td>Gemeenschappelijke Collections 3 is in onderhoudsmodus. In plaats daarvan moeten gemeenschappelijke verzamelingen 4 worden gebruikt. <a href="#apache.commons"> zie hieronder verwijderingsnota's.</a></td>
    <td>30-04-2021</td>
    <td>TBD</td>
  </tr>
  <tr>
    <td>com.day.cq.contentsync.handler.util</td>
    <td>Deze API is vervangen. Gebruik in plaats hiervan Apache Sling's Builders.</td>
    <td>31-10-2022</td>
    <td>TBD</td>
  </tr>
  <tr><td>org.apache.sling.commons.json<br>org.apache.sling.commons.json.http<br>org.apache.sling.commons.json.io<br>org.apache.sling.commons.json.jcr<br>org.apache.sling.commons.json.sling<br>org.apache.sling.commons.json.util<br>org.apache.sling.commons.json.xml</td>
    <td>AEM as a Cloud Service ondersteunt deze API niet.</td>
    <td>15-05-2023</td>
    <td>TBD</td>
  </tr>
  <tr>
    <td>com.day.cq.xss<br>com.day.cq.xss.taglib<br>com.day.cq.xss.impl</td>
    <td>Gebruik in plaats hiervan org.apache.sling.xss.</td>
    <td>12-12-2023</td>
    <td>TBD</td>
  </tr>
  <tr>
    <td>com.adobe.granite.xss<br>com.adobe.granite.xss.impl</td>
    <td>Gebruik in plaats hiervan org.apache.sling.xss.</td>
    <td>12-12-2023</td>
    <td>TBD</td>
  </tr>
  </tbody>
</table>
</details>

## Verwijderde API&#39;s {#removed-apis}

Deze sectie bevat een lijst met API&#39;s die zijn vervangen en verwijderd. Sommige API&#39;s verwijzen hieronder naar de sectie API Removal Guidance.

<details>
  <summary>Vouw uit om de lijst met verwijderde API's weer te geven.</summary>
<table style="table-layout:auto">
  <tr>
    <th>Pakket/klasse</th>
    <th>Opmerkingen</th>
  </tr>
<tbody>
  <tr>
    <td>com.day.cq.jcrclustersupport</td>
    <td>Detectie-API van Sling gebruiken als alternatief</td>
  </tr>
  <tr>
    <td>org.apache.fop.apps</td>
    <td></td>
  </tr>
  <tr>
    <td>org.apache.jackrabbit.vault.util.xml.xerces.dom<br>org.apache.jackrabbit.vault.util.xml.xerces.util<br>org.apache.jackrabbit.vault.util.xml.xerces.xni<br>org.apache.jackrabbit.vault.util.xml.xerces.xni.parser</td>
    <td></td>
  </tr>
  <tr>
    <td>org.apache.felix.cm<br>org.apache.felix.cm.file</td>
    <td>Aangepaste persistentiemanagers worden niet ondersteund in AEM as a Cloud Service.</td>
  </tr>
  <tr>
    <td>org.apache.felix.systemready</td>
    <td>Het wordt aanbevolen de API voor Apache Felix HealthCheck te gebruiken</td>
  </tr>
  <tr> <td>org.apache.felix.http.jetty<br>org.eclipse.jetty.client.jmx<br>org.eclipse.jetty.jmx<br>org.eclipse.jetty.server.handler.jmx<br>org.eclipse.jetty.server.nio<br>org.eclipse.jetty.server.jmx<br>org.eclipse.jetty.servlet.jmx<br>org.eclipse.jetty.util.preventers<br>org.eclipse.jetty.util.thread.strategy<br>org.eclipse.jetty.webapp<br>org.eclipse.jetty.websocket.api<br>org.eclipse.jetty.websocket.api.annotations<br>org.eclipse.jetty.websocket.api.extensions<br>org.eclipse.jetty.websocket.api.util<br>org.eclipse.jetty.websocket.client<br>org.eclipse.jetty.websocket.client.io<br>org.eclipse.jetty.websocket.client.masks<br>org.eclipse.jetty.websocket.common<br>org.eclipse.jetty.websocket.common.events<br>org.eclipse.jetty.websocket.common.events.annotated<br>org.eclipse.jetty.websocket.common.extensions<br>org.eclipse.jetty.websocket.common.extensions.compress<br>org.eclipse.jetty.websocket.common.extensions.fragment<br>org.eclipse.jetty.websocket.common.extensions.identity<br>org.eclipse.jetty.websocket.common.frames<br>org.eclipse.jetty.websocket.common.io<br>org.eclipse.jetty.websocket.common.io.http<br>org.eclipse.jetty.websocket.common.io.payload<br>org.eclipse.jetty.websocket.common.message<br>org.eclipse.jetty.websocket.common.scopes<br>org.eclipse.jetty.websocket.common.util<br>org.eclipse.jetty.websocket.server<br>org.eclipse.jetty.websocket.server.pathmap<br>org.eclipse.jetty.websocket.servlet<br>org.eclipse.jetty.xml</td>
    <td>De pakketten Eclipse Jetty en Felix HTTP Jetty worden niet meer ondersteund.</td>
  </tr>
  <tr>
    <td>org.apache.felix.metatype<br>org.apache.felix.scr<br>org.apache.felix.scr.info<br>org.apache.felix.scr.component</td>
    <td>Het metatype van Apache Felix en SCR APIs zijn verouderd.  Gebruik in plaats hiervan de OSGi-metatype en Declarative Service API's.</td>
  </tr>
  <tr>
    <td>org.slf4j.impl</td>
    <td>Logimplementatieklassen zijn niet compatibel met AEM as a Cloud Service.</td>
  </tr>
  <tr>
    <td>org.apache.sling.startupfilter<br>com.adobe.granite.crypto.spi<br>com.adobe.granite.crpyto.spi.base<br>com.adobe.agl.impl.data.icudt40b<br>com.adobe.agl.impl.data.icudt40b.brkitr<br>com.adobe.agl.impl.data.icudt40b.coll<br>com.adobe.agl.impl.data.icudt40b.rbnf<br>com.<br>adobe.agl.impl.data.icudt40b.translit<br>com.adobe.internal.pdf.tika<br>com.adobe.internal.pdftoolkit.color<br>com.adobe.internal.pdftoolkit.core.encryption<br>com.adobe.internal.pdftoolkit.core.encryption.impl<br>com.adobe.internal.pdftoolkit.core.traverser<br>com.adobe.internal.pdftoolkit.graphicsDOM<br>com.adobe.internal.pdftoolkit.graphicsDOM.shading<br>com.adobe.internal.pdftoolkit.graphicsDOM.utils<br>com.adobe.internal.pdftoolkit.image<br>com.adobe.internal.pdftoolkit.pdf.content<br>com.adobe.internal.pdftoolkit.pdf.content.processor<br>com.adobe.internal.pdftoolkit.pdf.content.processor.base14fontwidths<br>com.adobe.internal.pdftoolkit.pdf.contentmodify<br>com.adobe.internal.pdftoolkit.pdf.contentmodify.impl<br>com.adobe.internal.pdftoolkit.pdf.digsig<br>com.adobe.internal.pdftoolkit.pdf.document<br>com.adobe.internal.pdftoolkit.pdf.document.listener<br>com.adobe.internal.pdftoolkit.pdf.document.permissionhandlers<br>com.adobe.internal.pdftoolkit.pdf.filters<br>com.adobe.internal.pdftoolkit.pdf.graphics<br>com.adobe.internal.pdftoolkit.pdf.graphics.colorspaces<br>com.adobe.internal.pdftoolkit.pdf.graphics.colorspaces.cmykresources<br>com.adobe.internal.pdftoolkit.pdf.graphics.font<br>com.adobe.internal.pdftoolkit.pdf.graphics.font.encodings<br>com.adobe.internal.pdftoolkit.pdf.graphics.font.impl<br>com.adobe.internal.pdftoolkit.pdf.graphics.impl<br>com.adobe.internal.pdftoolkit.pdf.graphics.optionalcontent<br>com.adobe.internal.pdftoolkit.pdf.graphics.patterns<br>com.adobe.internal.pdftoolkit.pdf.graphics.shading<br>com.adobe.internal.pdftoolkit.pdf.graphics.xobject<br>com.adobe.internal.pdftoolkit.pdf.impl<br>com.adobe.internal.pdftoolkit.pdf.inlineimage<br>com.adobe.internal.pdftoolkit.pdf.interactive<br>com.adobe.internal.pdftoolkit.pdf.interactive.action<br>com.adobe.internal.pdftoolkit.pdf.interactive.annotation<br>com.adobe.internal.pdftoolkit.pdf.interactive.forms<br>com.adobe.internal.pdftoolkit.pdf.interactive.forms.impl<br>com.adobe.internal.pdftoolkit.pdf.interactive.geospatial<br>com.adobe.internal.pdftoolkit.pdf.interactive.markedcontent<br>com.adobe.internal.pdftoolkit.pdf.interactive.navigation<br>com.adobe.internal.pdftoolkit.pdf.interactive.navigation.collection<br>com.adobe.internal.pdftoolkit.pdf.interactive.readerrequirements<br>com.adobe.internal.pdftoolkit.pdf.interactive.requirement<br>com.adobe.internal.pdftoolkit.pdf.interchange<br>com.adobe.internal.pdftoolkit.pdf.interchange.documentparts<br>com.adobe.internal.pdftoolkit.pdf.interchange.metadata<br>com.adobe.internal.pdftoolkit.pdf.interchange.prepress<br>com.adobe.internal.pdftoolkit.pdf.interchange.structure<br>com.adobe.internal.pdftoolkit.pdf.multimedia<br>com.adobe.internal.pdftoolkit.pdf.page<br>com.adobe.internal.pdftoolkit.pdf.rendering<br>com.adobe.internal.pdftoolkit.pdf.transparency<br>com.adobe.internal.pdftoolkit.pdf.utils<br>com.adobe.internal.pdftoolkit.services.Jpeg2000<br>com.adobe.internal.pdftoolkit.services.fontresources<br>com.adobe.internal.pdftoolkit.services.fontresources.subsetting<br>com.adobe.internal.pdftoolkit.services.interchange.structure<br>com.adobe.internal.pdftoolkit.services.optionalcontent<br>com.adobe.internal.pdftoolkit.services.optionalcontent.impl<br>com.adobe.internal.pdftoolkit.services.pdfParser<br>com.adobe.internal.pdftoolkit.services.permissions<br>com.adobe.internal.pdftoolkit.services.rasterizer<br>com.adobe.internal.pdftoolkit.services.readingorder<br>com.adobe.internal.pdftoolkit.services.security<br>com.adobe.internal.pdftoolkit.services.swf<br>com.adobe.internal.pdftoolkit.services.textextraction<br>com.adobe.internal.pdftoolkit.services.textextraction.impl<br>com.adobe.internal.pdftoolkit.services.xmp<br>com.adobe.internal.util.base64<br>com.adobe.internal.xmp.utils<br>com.day.crx.core.cluster<br>com.day.crx.packaging<br>com.day.crx.packaging.gfx<br>com.day.crx.query<br>com.day.crx.sling.server.jmx<br>com.day.durbo<br>com.day.durbo.io<br>com.day.imageio.plugins<br>org.apache.aries.jmx.codec<br>org.h2.mvstore<br>org.h2.mvstore.rtree<br>org.h2.mvstore.type<br>org.openxmlformats.schemas.drawingml.x2006.chart.impl<br>org.openxmlformats.schemas.drawingml.x2006.main.impl<br>org.openxmlformats.schemas.drawingml.x2006.picture.impl<br>org.openxmlformats.schemas.drawingml.x2006.spreadsheetDrawing.impl<br>org.openxmlformats.schemas.drawingml.x2006.wordprocessingDrawing.impl<br>org.openxmlformats.schemas.officeDocument.x2006.customProperties.impl<br>org.openxmlformats.schemas.officeDocument.x2006.docPropsVTypes.impl<br>org.openxmlformats.schemas.officeDocument.x2006.extendedProperties.impl<br>org.openxmlformats.schemas.officeDocument.x2006.relationships.impl<br>org.openxmlformats.schemas.presentationml.x2006.main.impl<br>org.openxmlformats.schemas.spreadsheetml.x2006.main.impl<br>org.openxmlformats.schemas.wordprocessingml.x2006.main.impl<br>org.openxmlformats.schemas.xpackage.x2006.contentTypes<br>org.openxmlformats.schemas.xpackage.x2006.contentTypes.impl<br>org.openxmlformats.schemas.xpackage.x2006.digitalSignature<br>org.openxmlformats.schemas.xpackage.x2006.digitalSignature.impl<br>org.openxmlformats.schemas.xpackage.x2006.metadata.coreProperties<br>org.openxmlformats.schemas.xpackage.x2006.metadata.coreProperties.impl<br>org.openxmlformats.schemas.xpackage.x2006.relationships<br>org.openxmlformats.schemas.xpackage.x2006.relationships.impl<br>com.adobe.internal.afml<br>com.adobe.internal.agm<br>com.adobe.internal.pdftoolkit.legacy.services.ap.es2<br>com.adobe.internal.pdftoolkit.legacy.services.ap.es3<br>com.adobe.internal.pdftoolkit.pdf.pieceinfo.compoundtype<br>com.adobe.internal.pdftoolkit.pdf.pieceinfo.editablepdf<br>com.adobe.internal.pdftoolkit.services.ap<br>com.adobe.internal.pdftoolkit.services.ap.annot<br>com.adobe.internal.pdftoolkit.services.ap.extension<br>com.adobe.internal.pdftoolkit.services.ap.impl<br>com.adobe.internal.pdftoolkit.services.ap.spi<br>com.adobe.internal.pdftoolkit.services.digsig<br>com.adobe.internal.pdftoolkit.services.digsig.cryptoprovider<br>com.adobe.internal.pdftoolkit.services.digsig.docmodanalysis<br>com.adobe.internal.pdftoolkit.services.digsig.spi<br>com.adobe.internal.pdftoolkit.services.fdf<br>com.adobe.internal.pdftoolkit.services.formflattener<br>com.adobe.internal.pdftoolkit.services.forms<br>com.adobe.internal.pdftoolkit.services.imageconversion<br>com.adobe.internal.pdftoolkit.services.javascript<br>com.adobe.internal.pdftoolkit.services.javascript.extension<br>com.adobe.internal.pdftoolkit.services.manipulations<br>com.adobe.internal.pdftoolkit.services.manipulations.impl<br>com.adobe.internal.pdftoolkit.services.optimizer<br>com.adobe.internal.pdftoolkit.services.pdfa<br>com.adobe.internal.pdftoolkit.services.pdfa.error<br>com.adobe.internal.pdftoolkit.services.pdfa2<br>com.adobe.internal.pdftoolkit.services.pdfa2.error<br>com.adobe.internal.pdftoolkit.services.pdfa2.error.codes<br>com.adobe.internal.pdftoolkit.services.pdfa3<br>com.adobe.internal.pdftoolkit.services.pdfport<br>com.adobe.internal.pdftoolkit.services.portfolio<br>com.adobe.internal.pdftoolkit.services.rcg<br>com.adobe.internal.pdftoolkit.services.rcg.impl<br>com.adobe.internal.pdftoolkit.services.redaction<br>com.adobe.internal.pdftoolkit.services.redaction.handler<br>com.adobe.internal.pdftoolkit.services.sanitization<br>com.adobe.internal.pdftoolkit.services.xbm<br>com.adobe.internal.pdftoolkit.services.xdp<br>com.adobe.internal.pdftoolkit.services.xfa<br>com.adobe.internal.pdftoolkit.services.xfa.form<br>com.adobe.internal.pdftoolkit.services.xfatext<br>com.adobe.internal.pdftoolkit.services.xfdf<br>com.adobe.internal.pdftoolkit.services.xobjhandler<br>com.adobe.internal.pdftoolkit.xml<br>com.adobe.octopus.extract<br>opennlp.tools.doccat<br>opennlp.tools.entitylinker<br>opennlp.tools.formats<br>opennlp.tools.formats.ad<br>opennlp.tools.formats.brat<br>opennlp.tools.formats.convert<br>opennlp.tools.formats.frenchtreebank<br>opennlp.tools.formats.muc<br>opennlp.tools.formats.ontonotes<br>opennlp.tools.lemmatizer<br>opennlp.tools.parser<br>opennlp.tools.parser.chunking<br>opennlp.tools.parser.lang.en<br>opennlp.tools.parser.lang.es<br>opennlp.tools.parser.treeinsert<br>opennlp.tools.sentdetect<br>opennlp.tools.sentdetect.lang<br>opennlp.tools.sentdetect.lang.th<br>opennlp.tools.stemmer<br>opennlp.tools.stemmer.snowball<br>opennlp.tools.tokenize.lang.en<br>org.apache.commons.imaging.color<br>org.apache.commons.imaging.common<br>org.apache.commons.imaging.common.itu_t4<br>org.apache.commons.imaging.common.mylzw<br>org.apache.commons.imaging.formats.bmp<br>org.apache.commons.imaging.formats.dcx<br>org.apache.commons.imaging.formats.gif<br>org.apache.commons.imaging.formats.icns<br>org.apache.commons.imaging.formats.ico<br>org.apache.commons.imaging.formats.jpeg<br>org.apache.commons.imaging.formats.jpeg.decoder<br>org.apache.commons.imaging.formats.jpeg.exif<br>org.apache.commons.imaging.formats.jpeg.iptc<br>org.apache.commons.imaging.formats.jpeg.segments<br>org.apache.commons.imaging.formats.jpeg.xmp<br>org.apache.commons.imaging.formats.pcx<br>org.apache.commons.imaging.formats.png<br>org.apache.commons.imaging.formats.png.chunks<br>org.apache.commons.imaging.formats.png.scanlinefilters<br>org.apache.commons.imaging.formats.png.transparencyfilters<br>org.apache.commons.imaging.formats.pnm<br>org.apache.commons.imaging.formats.psd<br>org.apache.commons.imaging.formats.psd.dataparsers<br>org.apache.commons.imaging.formats.psd.datareaders<br>org.apache.commons.imaging.formats.rgbe<br>org.apache.commons.imaging.formats.tiff<br>org.apache.commons.imaging.formats.tiff.constants<br>org.apache.commons.imaging.formats.tiff.datareaders<br>org.apache.commons.imaging.formats.tiff.fieldtypes<br>org.apache.commons.imaging.formats.tiff.photometricinterpreters<br>org.apache.commons.imaging.formats.tiff.taginfos<br>org.apache.commons.imaging.formats.tiff.write<br>org.apache.commons.imaging.formats.wbmp<br>org.apache.commons.imaging.formats.xbm<br>org.apache.commons.imaging.formats.xpm<br>org.apache.commons.imaging.icc<br>org.apache.commons.imaging.palette<br>org.apache.commons.imaging.util<br>com.adobe.dam.print.ids.utils<br>com.day.cq.dam.api.reporting<br>com.day.cq.dam.entitlement.api<br>com.day.cq.dam.handler.standard.epub<br>com.day.cq.dam.handler.standard.keynote<br>com.day.cq.dam.handler.standard.mp3<br>com.day.cq.dam.handler.standard.msoffice<br>com.day.cq.dam.handler.standard.msoffice.wmf<br>com.day.cq.dam.handler.standard.ooxml<br>com.day.cq.dam.handler.standard.pdf<br>com.day.cq.dam.handler.standard.pict<br>com.day.cq.dam.handler.standard.ps<br>com.day.cq.dam.handler.standard.psd<br>com.day.cq.dam.handler.standard.zip<br>com.day.cq.dam.word.extraction<br>com.day.cq.dam.word.process<br>com.adobe.xmp.worker.files<br>com.adobe.cq.address.api<br>com.adobe.cq.address.api.location<br>com.day.cq.mcm.emailprovider.impl.types<br>com.day.io<br>com.day.io.disk<br>com.day.io.file<br>org.apache.commons.exec.environment<br>org.apache.commons.exec.launcher<br>org.apache.commons.exec.util<br>com.google.zxing<br>com.google.zxing.common<br>com.google.zxing.common.reedsolomon<br>com.google.zxing.qrcode.decoder<br>com.google.zxing.qrcode.encoder<br>com.adobe.cq.dam.dm.internalapi.image_server<br>com.day.cq.dam.api.s7dam.jobs<br>com.day.cq.dam.api.s7dam.omnisearch<br>com.day.cq.dam.api.s7dam.scene7<br>com.day.cq.dam.scene7<br>com.day.cq.dam.scene7.api.net<br>com.day.cq.analytics.sitecatalyst.rsmerger<br>com.day.cq.searchpromote<br>com.day.cq.searchpromote.xml<br>com.day.cq.searchpromote.xml.form<br>com.day.cq.searchpromote.xml.result&gt;</td>
    <td>Verouderde AEM 6.x API.</td>
  </tr>
  <tr>
    <td>org.apache.sling.discovery.commons<br>org.apache.sling.discovery.commons.providers<br>org.apache.sling.discovery.commons.providers.base<br>org.apache.sling.discovery.commons.providers.spi<br>org.apache.sling.discovery.commons.providers.spi.base<br>org.apache.sling.discovery.commons.providers.util</td>
    <td>Deze API wordt niet ondersteund in Cloud Service.</td>
  </tr>
  <tr>
    <td>org.apache.jackrabbit.vault.util.xml<br>org.apache.jackrabbit.vault.util.xml.serialize</td>
    <td>Util-klassen die verwant zijn aan Apache Xerces worden verwijderd in volgende releases die een belangrijke versiewijziging veroorzaken. Omdat deze hulpprogramma's bedoeld zijn voor intern gebruik in de vault File, wordt de API vervangen door het openbare API-oppervlak.</td>
  </tr>
  <tr>
    <td>org.apache.sling.atom.taglib<br>org.apache.sling.atom.taglib.media</td>
    <td>Verouderde AEM 6.x API. <a href="#org.apache.abdera_or_org.apache.sling.atom.taglib"> zie hieronder verwijderingsnota's.</a></td>
  </tr>
  <tr>
    <td>org.apache.sling.commons.log.logback<br>org.apache.sling.commons.log.logback.webconsole</td>
    <td>AEM as a Cloud Service ondersteunt deze interne log back-API niet.</td>
  </tr>
  <tr>
    <td>com.github.jknack.handlebars.js</td>
    <td>Handlebars verbetering die van 4.0.5 aan 4.3.0 wegens veiligheidskwetsbaarheid wordt vereist. Dit pakket is niet meer aanwezig in de verbeterde handgrepen.</td>
  </tr>
  <tr>
    <td>com.adobe.granite.resourceresolverhelper</td>
    <td>Deze API wordt niet meer ondersteund. Gebruik in plaats hiervan org.apache.sling.api.resource.ResourceResolverFactory.</td>
  </tr>
  <tr>
    <td>org.apache.sling.repoinit.jcr<br>org.apache.sling.repoinit.parser.operations</td>
    <td>Gebruik van deze API wordt niet ondersteund in AEM as a Cloud Service.</td>
  </tr>
  <tr>
    <td>org.apache.jackrabbit.oak.cache</td>
    <td>Deze API is alleen voor intern gebruik.</td>
  </tr>
</tbody>
</table>
</details>

## API Removal Guidance {#api-removal-guidance}

In deze sectie worden API-verwijderingshulplijnen voor verschillende API&#39;s in de bovenstaande tabellen besproken.

Om te identificeren welke afgekeurde Java APIs uw code gebruikt, integreer [&#x200B; AEM as a Cloud Service SDK bouwt Analyzer Maven Insteekmodule &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin) in uw Gemaakt project en stel het plaatselijk in werking. Het rapport bevat een lijst met alle gedetecteerde afgekeurde API-toepassingen en geeft aan naar welke OSGi-bundel wordt verwezen voor elke API.

Hoewel u alle verouderde API&#39;s in de loop der tijd moet verhelpen, geeft u prioriteit aan API&#39;s die in de Vervangen API-tabel worden vermeld met de datum van 26 februari 2026 (of eerder) als doel voor verwijdering. In het AEM Analyser-rapport worden deze API&#39;s mogelijk weergegeven met een effectieve verwijderingsdatum van 31-8-2025.

Nadat u de code hebt bijgewerkt, controleert u of er in Cloud Manager geen verouderd API-gebruik meer is door de resultaten van de stap Codekwaliteit te controleren.

### Algemene richtsnoeren

Als u een bibliotheek van derden gebruikt waarvoor momenteel een verouderde API is vereist, probeert u een update uit te voeren naar een nieuwere versie van die bibliotheek van derden.

Als u ACS AEM Commons gebruikt, gebruik minstens versie 6.11.0 (de recentste versie wordt geadviseerd) en zorg ervoor dat u [&#x200B; de versie voor Cloud Service &#x200B;](https://adobe-consulting-services.github.io/acs-aem-commons/pages/maven.html) door het classificatieapparaat `cloud` voor het inhoudspakket te specificeren omvat.

Als het importeren van een Vervangen API is gemarkeerd als `optional` , moet u toch proberen deze te verwijderen. Een dergelijk optioneel gebruik blokkeert echter geen implementaties. Maar de implementatie kan worden beïnvloed als de optionele import niet meer tevreden is.

### Verwijderen van `org.apache.sling.commons.auth*` {#org.apache.sling.commons.auth}

Als u `org.apache.sling.commons.auth` of `org.apache.sling.commons.auth.spi` of beide gebruikt, kunt u het gebruik vervangen door de code naar resp. `org.apache.sling.auth` te migreren. `org.apache.sling.auth.spi`. Als u een oude versie van [&#x200B; ACS AEM Commons &#x200B;](https://adobe-consulting-services.github.io/acs-aem-commons/) gebruikt, zorg ervoor om aan de recentste versie bij te werken.

Handelingenlijst:

* ACS AEM-GEMEENSCHAPPEN bijwerken naar recentste versie (minstens 6.11.0)
* Migreren van `org.apache.sling.commons.auth` en/of `org.apache.sling.commons.auth.spi` naar `org.apache.sling.auth` . `org.apache.sling.auth.spi` .

### Verwijderen van `org.apache.felix.webconsole*` {#org.apache.felix.webconsole}

Als u pakketten uit `org.apache.felix.webconsole*` gebruikt, verwijdert u deze code uit uw project. De webconsole is niet toegankelijk in Cloud Service.

Handelingenlijst:

* Code verwijderen met pakketten uit `org.apache.felix.webconsole*`

### Verwijderen van `org.eclipse.jetty*` {#org.eclipse.jetty}

Als u iets uit het pakket `org.eclipse.jetty` of een van de subpakketten gebruikt, kunt u migreren naar bibliotheken van derden met een vergelijkbare functionaliteit. Als migratie niet haalbaar is, voeg de vereiste bundels van de hieronder lijst aan uw project toe.

Handelingenlijst:

* Gebruik van `org.eclipse.jetty` -pakketten vervangen door andere bibliotheken van derden/eigen code of
* Selecteer in deze lijst de vereiste bundels en voeg deze toe aan uw project:
   * `org.eclipse.jetty:jetty-client:9.4.54.v20240208`
   * `org.eclipse.jetty:jetty-http:9.4.54.v20240208`
   * `org.eclipse.jetty:jetty-io:9.4.54.v20240208`
   * `org.eclipse.jetty:jetty-security:9.4.54.v20240208`
   * `org.eclipse.jetty:jetty-servlet:9.4.54.v20240208`
   * `org.eclipse.jetty:jetty-server:9.4.54.v20240208`
   * `org.eclipse.jetty:jetty-util:9.4.54.v20240208`
   * `org.eclipse.jetty:jetty-util-ajax:9.4.54.v20240208`

### Verwijderen van `com.mongodb` {#com.mongodb}

Voeg de Mongo-client-API toe aan uw project.

Handelingenlijst:

* Deze bundel toevoegen aan uw project
   * `org.mongodb:mongo-java-driver:3.12.7`

Afhankelijk van uw vereisten kunt u een andere versie kiezen.

### Verwijderen van `com.google.common*` {#com.google.common}

Verwijder het gebruik van Google Guava Core Libraries of neem een aangewezen versie in uw project op. In veel gevallen kan het gebruik van deze bibliotheek worden vervangen door verzamelingsklassen uit de JDK- of Apache Commons Collections4. Als u geen vervanging vindt, neemt u de nieuwste versie van de Google Guave Core Library in uw project op. Als u een oude versie van [&#x200B; ACS AEM Commons &#x200B;](https://adobe-consulting-services.github.io/acs-aem-commons/) gebruikt, zorg ervoor om aan de recentste versie bij te werken.

Handelingenlijst:

* ACS AEM-GEMEENSCHAPPEN bijwerken naar recentste versie (minstens 6.11.0)
* Gebruik van Google Guava Core Library vervangen door JDK-verzamelingen of Apache Commons Collections4
* Voeg, indien nog steeds vereist, deze bundel toe aan uw project (vervang de versie door de nieuwste beschikbare versie):
   * `com.google.guava:guava:33.4.8-jre`

### Verwijderen van `Apache Commons Lang 2 and Apache Commons Collections 3` {#apache.commons}

Verwijder het gebruik van de niet-onderhouden Apache Commons-bibliotheken en vervang deze door het gebruik van de supportversies. In de meeste gevallen hoeft u alleen de pakketimport aan te passen, maar in sommige gevallen is de naam van klassen of methoden gewijzigd. Als u een oude versie van [&#x200B; ACS AEM Commons &#x200B;](https://adobe-consulting-services.github.io/acs-aem-commons/) gebruikt, zorg ervoor om aan de recentste versie bij te werken.

Handelingenlijst:

* ACS AEM-GEMEENSCHAPPEN bijwerken naar recentste versie (minstens 6.11.0)
* Import van `org.apache.commons.lang*` vervangen door `org.apache.commons.lang3`
* Import van `org.apache.commons.collections*` vervangen door `org.apache.commons.collecitons4`

### Gebruik van `org.apache.abdera*` en `org.apache.sling.atom.taglib` {#org.apache.abdera_or_org.apache.sling.atom.taglib}

Vervang het gebruik van pakketten uit `org.apache.abdera` en `org.apache.sling.atom.taglib` door een externe bibliotheek met vergelijkbare functionaliteit of uw eigen code.

Handelingenlijst:

* Vervang het gebruik van pakketten uit `org.apache.abdera` en `org.apache.sling.atom.taglib` door andere bibliotheken van derden/eigen code.

### Gebruik van `org.apache.felix.http.whiteboard` {#org.apache.felix.http.whiteboard}

Vervang het gebruik van `org.apache.felix.http.whiteboard` met [&#x200B; OSGi Whiteboard Http &#x200B;](https://docs.osgi.org/specification/osgi.cmpn/7.0.0/service.http.whiteboard.html). De officiële OSGi API heeft gelijkaardige mogelijkheden en het vervangen vereist vaak slechts om de eigenschappen van de de dienstregistratie te veranderen.

Handelingenlijst:

* Vervang het gebruik van `org.apache.felix.http.whiteboard` met [&#x200B; OSGi Whiteboard Http &#x200B;](https://docs.osgi.org/specification/osgi.cmpn/7.0.0/service.http.whiteboard.html)

### Gebruik van `ch.qos.logback*` {#ch.qos.logback}

Logback wordt niet ondersteund in Cloud Service. Verwijder alle gebruiksmogelijkheden. Als u een oude versie van [&#x200B; ACS AEM Commons &#x200B;](https://adobe-consulting-services.github.io/acs-aem-commons/) gebruikt, zorg ervoor om aan de recentste versie bij te werken.

Handelingenlijst:

* ACS AEM-GEMEENSCHAPPEN bijwerken naar recentste versie (minstens 6.11.0)
* De code verwijderen met pakketten uit `ch.qos.logback`

### Gebruik van `org.slf4j.event and org.slf4j.spi` {#org.slf4j}

Als u `org.slf4j.event` of `org.slf4j.spi` gebruikt, verwijdert u het volledige gebruik ervan. Als u een oude versie van [&#x200B; ACS AEM Commons &#x200B;](https://adobe-consulting-services.github.io/acs-aem-commons/) gebruikt, zorg ervoor om aan de recentste versie bij te werken.

Handelingenlijst:

* ACS AEM-GEMEENSCHAPPEN bijwerken naar recentste versie (minstens 6.11.0)
* De code verwijderen met `org.slf4j.event` en `org.slf4j.spi`
* Als u de Cliënt van Apache Kafka gebruikt en de OSGi omslagbundel van Apache ServiceMix (`org.apache.servicemix.bundles.kafka-clients`) omvat, vervang het met [&#x200B; AEM Apache Kafka Kafka de Omheveling van de Cliënt &#x200B;](https://repo.maven.apache.org/maven2/com/adobe/aem/osgi/com.adobe.aem.osgi.kafka-clients/4.0.0_1.0/). Dit is dezelfde versie als die van Apache ServiceMix, waarbij alleen het gebruik van die twee pakketten wordt verwijderd.

### Gebruik van `org.apache.log4j` {#org.apache.log4j}

Als u `org.apache.log4j` schakelaar aan of SLF4J (`org.slf4j`) of Log4J 2.x (`org.apache.logging.log4j`) gebruikt.

Handelingenlijst:

* Gebruik van `org.apache.log4j` vervangen door `org.slf4j` (aanbevolen) of `org.apache.logging.log4j` te gebruiken

## OSGI-configuratie {#osgi-configuration}

De secties hieronder wijzen op de AEM as a Cloud Service OSGi configuratieoppervlakte, die welke klanten kunnen vormen.

1. De code van de klant moet niet de vermelde configuraties vormen OSGi.
1. Een lijst van configuraties OSGi waarvan de eigenschappen kunnen worden gevormd, maar moet zich aan de vermelde bevestigingsregels houden. Deze regels omvatten of de verklaring van het bezit, zijn type, en in sommige gevallen, zijn toegestane waaier van waarden wordt vereist.

De code van de klant kan om het even welke configuratie vormen OSGi niet vermeld.

Deze regels worden gevalideerd tijdens het Cloud Manager-ontwikkelproces. Er kunnen in de loop der tijd aanvullende regels worden toegevoegd en de verwachte datum van tenuitvoerlegging wordt in de tabel vermeld. Van klanten wordt verwacht dat zij zich aan deze regels zullen houden tegen de beoogde handhavingsdatum. Als u zich na de verwijderingsdatum niet aan de regels houdt, treden fouten op in het Cloud Manager-constructieproces. Gemaakte projecten zouden [&#x200B; AEM as a Cloud Service SDK moeten omvatten bouwt Analysator Gemaakte Insteekmodule &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin) om configuratiefouten te markeren OSGI tijdens de lokale ontwikkeling van SDK.

De extra informatie over configuratie OSGI kan bij [&#x200B; worden gevonden deze plaats &#x200B;](/help/implementing/deploying/configuring-osgi.md).

### Vervangen OSGi-eigenschappen (binnenkort niet te wijzigen) {#deprecated-unmodifiable-osgi-properties}

Eigenschappen voor de volgende PIDs van de component OSGi zijn afgekeurd en het gebruik zou tegen de handhavingsdatum moeten ophouden.

| **componentID OSGI** | **Onwijzigbare Eigenschappen** | **Verdringing** | **Handhaving** |
|---|---|---|---|
| **`org.apache.sling.commons.log.LogManager`** | alles | 24-04-25 | 31-08-25 (config genegeerd in juni) |
| **`org.apache.sling.commons.log.LogManager.factory.config`** | org.apache.sling.commons.log.file, org.apache.sling.commons.log.pattern | 24-04-25 | 31-08-25 (config genegeerd in juni) |
| **`org.apache.sling.jcr.davex.impl.servlets.SlingDavExServlet`** | alles | 2024 | 31-08-25 |
| **`com.adobe.granite.toggle.impl.dev.DynamicToggleProviderImpl`** | alles | 03-06-25 | 31-08-25 |
| **`org.apache.http.proxyconfigurator`** | alles | 03-06-25 | 31-08-25 |

### Onaanpasbare OSGi-configuraties {#unmodifiable-osgi-properties}

Eigenschappen voor de volgende PIDs van de component OSGi kunnen niet worden gewijzigd, daarom moeten deze niet worden gevormd.

| **componentID OSGI** | **Onwijzigbare Eigenschappen** |
|---|---|
| **`com.day.cq.auth.impl.cug.CugSupportImpl`** |  |
| **`com.day.cq.jcrclustersupport.ClusterStartLevelController`** | alles |
| **`com.adobe.granite.toggle.impl.ToggleRouterImpl`** | alles |
| **`org.apache.sling.engine.impl.log.RequestLoggerFilter`** | alles |
| **`org.apache.sling.feature.apiregions.impl`** | alles |
| **`org.apache.sling.jcr.resource.internal.helper.jcr.BinaryDownloadUriProvider`** | alles |
| **`com.adobe.cq.unifiedshell.impl.discovery.DiscoveryServlet`** | alles |
| **`com.adobe.cq.unifiedshell.impl.ui.FrameErrorHandler`** | alles |
| **`com.adobe.cq.unifiedshell.impl.config.UnifiedShellConfService`** | alles |
| **`com.adobe.cq.unifiedshell.impl.config.RepositoryIdentifier`** | alles |
| **`org.apache.sling.feature.apiregions.factory`** | alles |
| **`com.adobe.granite.toggle.monitor.systemproperty`** | alles |


### Toekomstige afgedwongen OSGi-eigendomsrechten {#future-restrictions-osgi-properties}

In de toekomst zal Adobe de volgende OSGi-eigenschappen-beperkingen afdwingen. Voor genoemde PIDs, slechts worden de vermelde eigenschappen toegestaan om worden gevormd.

| OSGi component PID |   | Vereist | Type | Beperking (indien van toepassing) |
|---|---|---|---|---|
| `com.day.cq.mailer.DefaultMailService` | `smtp.host` |   | string |   |
|   | `smtp.port` | Ja | integer | &quot;465&quot;, &quot;587&quot; of &quot;25&quot; |
|   | `smtp.user` |   | string |   |
|   | `smtp.password` |   | string |   |
|   | `from.address` |   | string |   |
|   | `smtp.ssl` |   | string |   |
|   | `smtp.starttls` |   | boolean |   |
|   | `smtp.requiretls` |   | boolean |   |
|   | `debug.email` |   | boolean |   |
|   | `oauth.flow` |   | boolean |   |
| `org.apache.sling.commons.log.LogManager.factory.config` | `org.apache.sling.commons.log.level` | Ja | string | &quot;INFO&quot;, &quot;DEBUG&quot; of &quot;TRACE&quot; |
|   | `org.apache.sling.commons.log.names` |   | array van tekenreeksen |   |
|   | `org.apache.sling.commons.log.additiv` |   | boolean |   |
| `com.day.cq.commons.impl.ExternalizerImpl` | `externalizer.domains` | Nee | string[] |   |
|   | `externalizer.encodedpath` | Nee | boolean |   |
|   | `externalizer.host` | Nee | string |   |
|   | `externalizer.contextpath` | Nee | string |   |

### Beperkingen van OSGi-eigenschappen {#restrictions-osgi-properties}

De waarden van deze OSGi-eigenschappen zijn beperkt tot de hieronder beschreven regels.

| OSGi component PID |   | Vereist | Type | Beperking (indien van toepassing) |
|---|---|---|---|---|
| `org.apache.felix.eventadmin.impl.EventAdmin` | `org.apache.felix.eventadmin.ThreadPoolSize` | Ja | integer | 2-100 |
|   | `org.apache.felix.eventadmin.AsyncToSyncThreadRatio` |   | double | — |
|   | `org.apache.felix.eventadmin.AsyncToSyncThreadRatio` |   | integer | — |
|   | `org.apache.felix.eventadmin.RequireTopic` |   | boolean | — |
|   | `org.apache.felix.eventadmin.IgnoreTimeout` | Ja | array van tekenreeksen | Moet ten minste alle `org.apache.felix*`, `org.apache.sling*`, `come.day*`, `com.adobe*` bevatten |
|   | `org.apache.felix.eventadmin.IgnoreTopic` |   | array van tekenreeksen | — |
| `org.apache.felix.http` | `org.apache.felix.http.timeout` |   | integer |   |
|   | `org.apache.felix.http.session.timeout` |   | integer |   |
|   | `org.apache.felix.http.jetty.threadpool.max` |   | integer |   |
|   | `org.apache.felix.http.jetty.headerBufferSize` |   | integer |   |
|   | `org.apache.felix.http.jetty.requestBufferSize` |   | integer |   |
|   | `org.apache.felix.http.jetty.responseBufferSize` |   | integer |   |
|   | `org.apache.felix.http.jetty.maxFormSize` |   | integer |   |
|   | `org.apache.felix.https.jetty.session.cookie.httpOnly` |   | boolean |   |
|   | `org.apache.felix.https.jetty.session.cookie.secure` |   | boolean |   |
|   | `org.eclipse.jetty.servlet.SessionIdPathParameterName` |   | string |   |
|   | `org.eclipse.jetty.servlet.CheckingRemoteSessionIdEncoding` |   | boolean |   |
|   | `org.eclipse.jetty.servlet.SessionCookie` |   | string |   |
|   | `org.eclipse.jetty.servlet.SessionDomain` |   | string |   |
|   | `org.eclipse.jetty.servlet.SessionPath` |   | string |   |
|   | `org.eclipse.jetty.servlet.MaxAge` |   | integer |   |
|   | `org.eclipse.jetty.servlet.SessionScavengingInterval` |   | integer |   |
|   | `org.apache.felix.jetty.gziphandler.enable` |   | boolean |   |
|   | `org.apache.felix.jetty.gzip.minGzipSize` |   | integer |   |
|   | `org.apache.felix.jetty.gzip.compressionLevel` |   | integer |   |
|   | `org.apache.felix.jetty.gzip.inflateBufferSize` |   | integer |   |
|   | `org.apache.felix.jetty.gzip.syncFlush` |   | boolean |   |
|   | `org.apache.felix.jetty.gzip.excludedUserAgents` |   | string |   |
|   | `org.apache.felix.jetty.gzip.includedMethods` |   | array van tekenreeksen |   |
|   | `org.apache.felix.jetty.gzip.excludedMethods` |   | array van tekenreeksen |   |
|   | `org.apache.felix.jetty.gzip.includedPaths` |   | array van tekenreeksen |   |
|   | `org.apache.felix.jetty.gzip.excludedPaths` |   | array van tekenreeksen |   |
|   | `org.apache.felix.jetty.gzip.includedMimeTypes` |   | array van tekenreeksen |   |
|   | `org.apache.felix.http.session.invalidate` |   | boolean |   |
|   | `org.apache.felix.http.session.container.attribute` |   | array van tekenreeksen |   |
|   | `org.apache.felix.http.session.uniqueid` |   | boolean |   |
| `org.apache.sling.scripting.cache` | `org.apache.sling.scripting.cache.size` | Ja | integer | >= 2048 |
|   | `org.apache.sling.scripting.cache.additional_extensions` | Ja | array van tekenreeksen | moet &quot;js&quot; bevatten |
| `org.apache.sling.engine.impl.log.RequestLogger` | `request.log.output` | Nee | string |   |
|   | `request.log.outputtype` | Nee | string |   |
|   | `request.log.entry.format` | Nee | string |   |
|   | `request.log.exit.format` | Nee | string |   |
|   | `request.log.enabled` | Nee | string |   |
|   | `access.log.output` | Nee | string |   |
|   | `access.log.outputtype` | Nee | string |   |
|   | `access.log.enabled` | Nee | string |   |
| `org.apache.sling.servlets.resolver.SlingServletResolver` | `servletresolver.servletRoot` | Nee | string |   |
|   | `servletresolver.cacheSize` | Nee | integer |   |
|   | `servletresolver.paths` | Nee | string[] |   |
|   | `servletresolver.defaultExtensions` | Nee | string |   |
|   | `servletresolver.mountProviders` | Nee | boolean |   |
|   | `servletresolver.scriptUser` | Nee | string | vervangen, niet gebruiken |

## Java-runtime-update naar versie 21 {#java-runtime-update-21}

Adobe Experience Manager as a Cloud Service heeft een overgang gemaakt naar de Java 21-runtime. Om verenigbaarheid te verzekeren, is het bijwerken van bibliotheekversies zoals die in [&#x200B; runtime vereisten &#x200B;](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements) worden geschetst essentieel.

