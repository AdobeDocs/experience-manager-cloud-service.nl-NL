---
title: Dynamic Media met OpenAPI-mogelijkheden
description: Leer belangrijke concepten zoals waarom Dynamic Media met OpenAPI-mogelijkheden wordt gebruikt en hoe u dit kunt inschakelen.
role: User
source-git-commit: 540aa876ba7ea54b7ef4324634f6c5e220ad19d3
workflow-type: tm+mt
source-wordcount: '980'
ht-degree: 0%

---

# Dynamic Media met OpenAPI-mogelijkheden {#new-dynaminc-media-apis-overview}

In de snelle digitale wereld van vandaag, is het ontsluiten van het volledige potentieel van de digitale activa van uw merk cruciaal om voor de concurrentie te blijven. Een holistische DAM-oplossing (Digital Assets Management) vereenvoudigt het beheer van bedrijfsmiddelen, bevordert de consistentie van merken en versnelt de levering van inhoud, waarbij de integriteit van merken en uitzonderlijke ervaringen met klanten worden gegarandeerd.

Dynamic Media met OpenAPI-mogelijkheden plaatst DAM centraal in een flexibel en efficiënt systeem voor de toeleveringsketen van inhoud om het beheer en de levering van middelen te garanderen.

## Waarom Dynamic Media gebruiken met OpenAPI-mogelijkheden? {#dynamic-media-open-api-features}

Dynamic Media met OpenAPI-mogelijkheden biedt de volgende belangrijke voordelen:

* **Naadloze integratie**: Dynamic Media met OpenAPI-mogelijkheden biedt een uitgebreide set API&#39;s voor zoeken en leveren. Het stelt uw ontwikkelaars in staat om gemakkelijk [de levering van elementen met hun toepassingen integreren](/help/assets/integrate-dynamic-media-open-apis.md). De toepassingen omvatten Adobe evenals derdetoepassingen. Het biedt een [Gebruikersinterface Micro Frontend Assets](/help/assets/asset-selector.md) om goedgekeurde elementen te zoeken en te selecteren. De kiezer kan moeiteloos worden geïntegreerd met elke toepassing die is gebaseerd op JavaScript-frameworks zoals React JS, Angular JS en Vanilla JS.

* **Gecentraliseerd beheer van digitale middelen**: DAM is de enige bron van waarheid voor alle digitale middelen. Uw digitale middelen worden centraal beheerd in AEM Assets en worden aan verbruikende toepassingen geleverd door verwijzing gebruikend levering URLs, zonder activa te kopiëren binaries.

* **Updates in realtime**: Wijzigingen die worden aangebracht in goedgekeurde elementen in DAM, inclusief versies-updates en wijzigingen in metagegevens, worden automatisch doorgevoerd in de URL&#39;s van de levering. Met een korte TTL-waarde (Time-to-Live) van 10 minuten die voor Dynamic Media met OpenAPI mogelijkheden via CDN wordt gevormd, worden de updates zichtbaar over alle creatie en gepubliceerde interfaces binnen 10 minuten.

* **Merkconsistentie** Alleen : [merkgebonden activa](/help/assets/approve-assets.md) worden blootgesteld aan downstreamtoepassingen. [Merkbeheerders en verkopers houden strikte controle over merkactiva](/help/assets/restrict-assets-delivery.md). Alleen goedgekeurde en nieuwste versie van het middel is beschikbaar voor gebruik, zodat alle kanalen en toepassingen consistent blijven.

* **Web-geoptimaliseerde levering**: Digitale middelen worden geleverd in voor het web geoptimaliseerde indelingen voor een betere weergave van de Kernwebdiversiteit van uw digitale beleving. Dit omvat ondersteuning voor WebP-uitvoeringen voor afbeeldingen, adaptieve streaming via HLS- of DASH-protocollen voor video&#39;s en originele uitvoeringen voor documenten.

* **Dynamische transformatie van elementen**: Ons systeem maakt het mogelijk om ter plekke afbeeldingen te transformeren met URL-parameters die afbeeldingsmodifiers worden genoemd. [Breedte, hoogte, roteren, spiegelen, kwaliteit, uitsnijden, opmaken en slim uitsnijden](/help/assets/deliver-assets-apis.md). Transformeerde uitvoeringen worden dynamisch gegenereerd en naadloos via de CDN geleverd.

* **Beveiligde levering van activa**: Dynamic Media met OpenAPI-mogelijkheden biedt een mechanisme voor het beheren van de toegang tot uw digitale middelen. U kunt gebruikersrollen of groepen opgeven als metagegevens voor te beveiligen elementen en een vooraf gedefinieerd tijdsbestek instellen gedurende welke [alleen geautoriseerde gebruikers hebben toegang tot deze middelen](/help/assets/restrict-assets-delivery.md). De leverings-URL&#39;s voor beveiligde elementen worden tijdens de beperkte periode niet opgelost voor onbevoegde gebruikers.

* **Gegevens inzichten om geïnformeerde beslissingen te nemen (komende tijd)**: Naast beheer en levering van bedrijfsmiddelen, legt het de inzichten van leveringsgegevens in activa leveranties bij CDN vast die de managers van het Merk toestaan om leveringsmetriek over kanalen te volgen. Het stelt hen in staat gegevensgestuurde beslissingen te nemen met het oog op een continue optimalisering van het beheer en de leveringsstrategieën van activa.

![Dynamic Media Open API-gegevensstroomdiagram](assets/dm-openapi-dfd.png)

## Vereisten voor toegang tot Dynamic Media met OpenAPI-mogelijkheden {#prerequisites-dynaminc-media-open-apis}

Voor toegang tot Dynamic Media met OpenAPI-mogelijkheden hebt u licenties nodig voor:

* AEM Assets as a Cloud Service

* AEM Dynamic Media

## Hoe kan ik de Dynamic Media inschakelen met OpenAPI-mogelijkheden? {#enable-dynamic-media-open-apis}

Voordat u een aanvraag indient om Dynamic Media met OpenAPI-mogelijkheden in te schakelen op AEM as a Cloud Service, moet u controleren of dit nog niet is ingeschakeld.

Wanneer de [Vereisten](#prerequisites-dynaminc-media-open-apis) wordt voldaan en als Dynamic Media met OpenAPI-mogelijkheden is ingeschakeld op uw AEM as a Cloud Service-exemplaar, is er een Delivery URL beschikbaar voor elk goedgekeurd middel in de opslagplaats. Ga voor informatie over het kopiëren van de URL voor levering naar [Leverings-URL kopiëren voor goedgekeurde elementen](approve-assets.md#copy-delivery-url-approved-assets) . Adobe raadt u aan deze methode te gebruiken om te controleren of Dynamic Media met OpenAPI-mogelijkheden is ingeschakeld op AEM as a Cloud Service voordat u een ondersteuningsticket verzendt om dit in te schakelen.

Als u Dynamic Media met OpenAPI-mogelijkheden op AEM as a Cloud Service wilt inschakelen, dient u een ondersteuningsticket voor Adobe in met de volgende gegevens:

* Programma Cloud Servicen en milieu-id

* Details van het gebruiksgeval dat moet worden opgelost met Dynamic Media met integratie van OpenAPI-mogelijkheden.

* Gegevens over de downstreamtoepassing(en) die met Dynamic Media met OpenAPI-mogelijkheden moet worden geïntegreerd.

  >[!NOTE]
  >
  > Als u wilt integreren met een toepassing die geen Adobe is, geeft u domeinnamen op aan de whitelist waar de toepassing wordt gehost.

* Details van zeer belangrijke klantencontacten betrokken bij integratieproject.

* Lijst met sleutelleden van het accountteam voor de Adobe (e-mail).

Nadat u het ondersteuningsticket hebt verzonden, biedt Adobe Dynamic Media met OpenAPI-mogelijkheden in uw Cloud Servicen-omgeving en deelt u de gegevens, zoals de IMS-client-id, zodat u verder kunt gaan met de integratie.

>[!NOTE]
>
>Uitsluiten `/conf/global/settings/dam/assets-configurations/assetdelivery` uit een inhoudspakket om deactivering van Dynamic Media met OpenAPI-mogelijkheden te voorkomen.

## Dien meer in zeer belangrijke mogelijkheden {#learn-more-key-capabilities}

<table>
<td>
   <a href="/help/assets/approve-assets.md">
   <img alt="Elementen goedkeuren in Experience Manager Assets" src="./assets/approved-assets.jpeg" />
   </a>
   <div>
      <a href="/help/assets/approve-assets.md">
      <strong>Elementen goedkeuren in Experience Manager Assets</strong>
      </a>
   </div>
   <p>
      <em>Goedkeuren van bedrijfsmiddelen in AEM Assets om het beheer van bedrijfsmiddelen te stroomlijnen, zodat een gecontroleerd en efficiënt proces voor de verwerking van bedrijfsmiddelen wordt gewaarborgd.</em>
   </p>
</td>
<td>
   <a href="/help/assets/integrate-dynamic-media-open-apis.md">
   <img alt="AEM Assets integreren met downstreamtoepassingen" src="./assets/asset-selector-integration.png" />
   </a>
   <div>
      <a href="/help/assets/integrate-dynamic-media-open-apis.md">
      <strong>AEM Assets integreren met downstreamtoepassingen</strong>
      </a>
   </div>
   <p>
      <em>Integreer uw eigen aangepaste gebruikersinterface met de Experience Manager Assets-opslagplaats met de zoek- en leverings-API's of gebruik de Micro-Frontend Asset Selector van de Adobe.</em>
   </p>
</td>
<td>
   <a href="/help/assets/asset-selector.md">
   <img alt="Asset Selector van Adobe" src="./assets/asset-selector-prereqs.png" />
   </a>
   <div>
      <a href="/help/assets/asset-selector.md">
      <strong>Adobe: Micro-Frontend Asset Selector</strong>
      </a>
   </div>
   <p>
      <em>Een gebruikersinterface die communiceert met de AEM Assets-opslagplaats om te zoeken naar middelen en deze vervolgens te gebruiken in de ontwerpervaring van uw toepassing.</em>
   </p>
</td>
</table>
<table>
<td>
   <a href="/help/assets/search-assets-api.md">
   <img alt="Zoeken in Experience Manager Assets-opslagplaats" src="./assets/search-assets-api-overview.png" />
   </a>
   <div>
      <a href="/help/assets/search-assets-api.md">
      <strong>Middelen zoeken in Experience Manager Assets-opslagplaats</strong>
      </a>
   </div>
   <p>
      <em>Zoek middelen in AEM Assets-opslagplaats zodat ze aan downstreamtoepassingen kunnen worden geleverd.</em>
   </p>
</td>
<td>
   <a href="/help/assets/deliver-assets-apis.md">
   <img alt="Elementen leveren aan downstreamtoepassingen" src="./assets/delivery-url.png" />
   </a>
   <div>
      <a href="/help/assets/deliver-assets-apis.md">
      <strong>Elementen leveren aan downstreamtoepassingen</strong>
      </a>
   </div>
   <p>
      <em>Elementen leveren aan geïntegreerde downstreamtoepassingen met behulp van een Delivery URL.</em>
   </p>
</td>
<td>
   <a href="/help/assets/restrict-assets-delivery.md">
   <img alt="Toegang tot elementen in Experience Manager beperken" src="./assets/restricted-access.png" />
   </a>
   <div>
      <a href="/help/assets/restrict-assets-delivery.md">
      <strong>Toegang tot elementen in Experience Manager beperken</strong>
      </a>
   </div>
   <p>
      <em> DAM Admin of Merk Managers beperken de toegang door rollen voor goedgekeurde activa op de de auteursinstantie van AEM as a Cloud Service te vormen.</em>
   </p>
</td>
</table>

