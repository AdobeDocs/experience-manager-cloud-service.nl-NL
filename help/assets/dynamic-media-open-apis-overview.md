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

* **Naadloze integraties**: Dynamic Media met mogelijkheden OpenAPI biedt een uitvoerige reeks onderzoek en levering APIs aan. Het staat uw ontwikkelaars toe om levering van activa met hun toepassingen ](/help/assets/integrate-dynamic-media-open-apis.md) gemakkelijk [ te integreren. De toepassingen omvatten Adobe evenals derdetoepassingen. Het verstrekt a [ Micro Frontend activa selecteerde gebruikersinterface ](/help/assets/asset-selector.md) om goedgekeurde activa te zoeken en te selecteren. De kiezer kan moeiteloos worden geïntegreerd met elke toepassing die is gebaseerd op JavaScript-frameworks zoals React JS, Angular JS en Vanilla JS.

* **Gecentraliseerd beheer van digitale activa**: DAM is de enige bron van waarheid voor alle digitale activa. Uw digitale middelen worden centraal beheerd in AEM Assets en worden aan verbruikende toepassingen geleverd door verwijzing gebruikend levering URLs, zonder activa te kopiëren binaries.

* **updates in real time**: Om het even welke veranderingen die in goedgekeurde activa in DAM, met inbegrip van versieupdates en meta-gegevenswijzigingen worden aangebracht, worden automatisch weerspiegeld in levering URLs. Met een korte TTL-waarde (Time-to-Live) van 10 minuten die voor Dynamic Media met OpenAPI mogelijkheden via CDN wordt gevormd, worden de updates zichtbaar over alle creatie en gepubliceerde interfaces binnen 10 minuten.

* **de consistentie van het Merk**: Slechts [ merk-goedgekeurde activa ](/help/assets/approve-assets.md) worden blootgesteld aan stroomafwaartse toepassingen. [ de Managers en de Marketers van de Merk handhaven strikte controle over merkactiva ](/help/assets/restrict-assets-delivery.md). Alleen goedgekeurde en nieuwste versie van het middel is beschikbaar voor gebruik, zodat alle kanalen en toepassingen consistent blijven.

* **Web-geoptimaliseerde levering**: De digitale activa worden geleverd in Web-geoptimaliseerde formaten om de Velen van het Web van de Kern van uw digitale ervaringen te verbeteren. Dit omvat ondersteuning voor WebP-uitvoeringen voor afbeeldingen, adaptieve streaming via HLS- of DASH-protocollen voor video&#39;s en originele uitvoeringen voor documenten.

* **Dynamische activa transformatie**: Ons systeem staat voor de transformatie van het beeld toe het gebruiken van parameters URL die als beeldbepalingen worden bekend. [ bijvoorbeeld, breedte, hoogte, roteert, keert, kwaliteit, gewas, formaat, en slimme gewas ](/help/assets/deliver-assets-apis.md) om. Transformeerde uitvoeringen worden dynamisch gegenereerd en naadloos via de CDN geleverd.

* **Veilige levering van activa**: Dynamic Media met mogelijkheden OpenAPI verstrekt een mechanisme voor controle over toegang tot uw digitale activa. U kunt gebruikersrollen of groepen als meta-gegevens voor te beveiligen activa specificeren en een vooraf bepaald tijdskader plaatsen waarin [ slechts geautoriseerde gebruikers tot deze activa ](/help/assets/restrict-assets-delivery.md) kunnen toegang hebben. De leverings-URL&#39;s voor beveiligde elementen worden tijdens de beperkte periode niet opgelost voor onbevoegde gebruikers.

* **Inzichten van Gegevens om geïnformeerde besluiten (aanstaande) te nemen**: Buiten activabeheer en levering, vangt het de inzichten van leveringsgegevens in activa leveranties bij CDN die de managers van het Merk toestaan om leveringsmetriek over kanalen te volgen. Het stelt hen in staat gegevensgestuurde beslissingen te nemen met het oog op een continue optimalisering van het beheer en de leveringsstrategieën van activa.

![ Dynamic Media Open API gegevensstroomdiagram ](assets/dm-openapi-dfd.png)

## Vereisten voor toegang tot Dynamic Media met OpenAPI-mogelijkheden {#prerequisites-dynaminc-media-open-apis}

Voor toegang tot Dynamic Media met OpenAPI-mogelijkheden hebt u licenties nodig voor:

* AEM Assets as a Cloud Service

* AEM Dynamic Media

## Hoe kan ik de Dynamic Media inschakelen met OpenAPI-mogelijkheden? {#enable-dynamic-media-open-apis}

Voordat u een aanvraag indient om Dynamic Media met OpenAPI-mogelijkheden in te schakelen op AEM as a Cloud Service, moet u controleren of dit nog niet is ingeschakeld.

Zodra de [ Eerste vereisten ](#prerequisites-dynaminc-media-open-apis) worden voldaan en als Dynamic Media met mogelijkheden OpenAPI op uw instantie van AEM as a Cloud Service wordt toegelaten, is er een Levering URL beschikbaar voor elk goedgekeurd middel in de bewaarplaats. Voor informatie over hoe te om levering URL te kopiëren, zie [ levering URL van het Exemplaar voor goedgekeurde activa ](approve-assets.md#copy-delivery-url-approved-assets). Adobe raadt u aan deze methode te gebruiken om te controleren of Dynamic Media met OpenAPI-mogelijkheden is ingeschakeld op AEM as a Cloud Service voordat u een ondersteuningsticket verzendt om dit in te schakelen.

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
>Sluit `/conf/global/settings/dam/assets-configurations/assetdelivery` uit van een inhoudspakket om deactivering van Dynamic Media met OpenAPI-mogelijkheden te voorkomen.

## Dien meer in zeer belangrijke mogelijkheden {#learn-more-key-capabilities}

<table>
<td>
   <a href="/help/assets/approve-assets.md">
   <img alt="Elementen goedkeuren in Experience Manager Assets" src="./assets/approved-assets.jpeg" />
   </a>
   <div>
      <a href="/help/assets/approve-assets.md">
      <strong> keur activa in Experience Manager Assets </strong> goed
      </a>
   </div>
   <p>
      <em> keur activa in AEM Assets goed om activabeheer te stroomlijnen, die een gecontroleerd en efficiënt proces verzekeren om activa te behandelen.</em>
   </p>
</td>
<td>
   <a href="/help/assets/integrate-dynamic-media-open-apis.md">
   <img alt="AEM Assets integreren met downstreamtoepassingen" src="./assets/asset-selector-integration.png" />
   </a>
   <div>
      <a href="/help/assets/integrate-dynamic-media-open-apis.md">
      <strong> integreer AEM Assets met stroomafwaartse toepassingen </strong>
      </a>
   </div>
   <p>
      <em> integreer uw eigen douanegebruikersinterface met de bewaarplaats van Experience Manager Assets gebruikend het Onderzoek en Levering APIs of de selecteur van de Activa van de Adobe Micro-Frontend.</em>
   </p>
</td>
<td>
   <a href="/help/assets/asset-selector.md">
   <img alt="Asset Selector van Adobe" src="./assets/asset-selector-prereqs.png" />
   </a>
   <div>
      <a href="/help/assets/asset-selector.md">
      <strong> de Micro-Frontend selecteur van Activa van de Adobe </strong>
      </a>
   </div>
   <p>
      <em> een gebruikersinterface die met de bewaarplaats van AEM Assets aan onderzoeksactiva in wisselwerking staat en dan hen in uw toepassing creërende ervaring gebruikt.</em>
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
      <strong> activa van het Onderzoek in de bewaarplaats van Experience Manager Assets </strong>
      </a>
   </div>
   <p>
      <em> de activa van het Onderzoek in de bewaarplaats van AEM Assets zodat zij aan stroomafwaartse toepassingen kunnen leveren.</em>
   </p>
</td>
<td>
   <a href="/help/assets/deliver-assets-apis.md">
   <img alt="Elementen leveren aan downstreamtoepassingen" src="./assets/delivery-url.png" />
   </a>
   <div>
      <a href="/help/assets/deliver-assets-apis.md">
      <strong> lever activa aan stroomafwaartse toepassingen </strong>
      </a>
   </div>
   <p>
      <em> lever activa aan geïntegreerde stroomafwaartse toepassingen gebruikend een Levering URL.</em>
   </p>
</td>
<td>
   <a href="/help/assets/restrict-assets-delivery.md">
   <img alt="Toegang tot elementen in Experience Manager beperken" src="./assets/restricted-access.png" />
   </a>
   <div>
      <a href="/help/assets/restrict-assets-delivery.md">
      <strong> Beperk toegang tot activa in Experience Manager </strong>
      </a>
   </div>
   <p>
      <em> DAM Admin of Merk Managers beperken de toegang door rollen voor goedgekeurde activa op de het auteursinstantie van AEM as a Cloud Service te vormen.</em>
   </p>
</td>
</table>

