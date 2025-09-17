---
title: Problemen in AEM Assets en Forms oplossen
description: Problemen met AEM Assets en Forms die vaak voorkomen, oplossen met de artikelkoppelingen voor belangrijke gebieden, zoals uploads, metagegevens, zoeken, leveren, maken van formulieren, verzenden en integreren.
hidefromtoc: true
hide: true
source-git-commit: 5074e777c68c51955b9ad8f055e04067163b9596
workflow-type: tm+mt
source-wordcount: '798'
ht-degree: 0%

---


# Problemen met AEM Assets en Forms oplossen {#troubleshoot-aem-assets-forms}

AEM as a Cloud Service biedt uitgebreide oplossingen voor Digital Asset Management via AEM Assets en krachtige mogelijkheden voor het maken van formulieren via AEM Forms. Beide diensten verstrekken wolk-inheems, oplossingen PaaS met volgende-generatie slimme mogelijkheden, zoals AI/ML, allen binnen een systeem dat altijd huidig is, altijd beschikbaar, en altijd het leren.

Complexe bedrijfsomgevingen kunnen echter op verschillende gebieden met verschillende technische uitdagingen worden geconfronteerd.

Deze uitvoerige het oplossen van problemengids verstrekt systematische kenmerkende benaderingen, gecategoriseerde oplossingen, en geleidelijke oplossingspaden voor zowel AEM Assets als Forms. Elke sectie bevat snelle naslaggidsen, gedetailleerde methoden voor het oplossen van problemen en uitgebreide bronkoppelingen om u te helpen problemen efficiënt op te lossen en uw AEM Cloud Service-omgeving te optimaliseren.

## AEM Assets-probleemoplossing {#aem-assets-troubleshooting}

AEM Assets stroomlijnt de manier waarop u digitale middelen beheert, ordent en levert. Er kunnen zich echter problemen voordoen die van invloed zijn op het uploaden van elementen, metagegevens, integratie of levering. Dit artikel bevat stappen voor het oplossen van problemen waarmee u algemene AEM Assets-problemen kunt opsporen en oplossen. Door de instructies hier te volgen, kunt u werkstromen efficiënt herstellen en ervoor zorgen blijven de activa toegankelijk, nauwkeurig, en klaar voor gebruik over kanalen.

### Verwerking en uitvoering van bedrijfsmiddelen {#asset-processing-renditions-issues}

<table>
  <tbody>
  <tr>
    <td><strong>Uploaden en verwerken</strong></td>
    <td><strong>Uitvoeringen</strong></td>
    <td><strong>PDF- en tekstextractie</strong></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26610">Verwerking van middelen is mislukt voor grote MP4-bestanden in AEM as a Cloud Service</a></td>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26639">DAM-uitvoeringen komen niet overeen met oorspronkelijke bestanden</a></td>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26785">AEM kapt geëxtraheerde tekst van grote PDF's na 100K-tokens af</a></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-23916">TIFF-bestand met geüploade ZIP-compressie genereert geen uitvoeringen</a></td>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26233">Afbeeldingen zonder miniatuurweergaven in AEM as a Cloud Service</a></td>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-25518">Beperkingen voor het uitnemen van tekst voor grote PDF's in AEM as a Cloud Service</a></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-21865">Slepen en neerzetten van een map met middelen naar de gebruikersinterface van AEM Assets Web mislukt</a></td>
    <td></td>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26528">Uitgave van elementrotatie maakt volgende rotaties onzichtbaar</a></td>
  </tr>
  <tr>
  <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26450">Uploadlimiet voor enkelvoudige onderdelen voor Photoshop Firefly API-integratie verhogen</a></td>
  <td></td>
  <td></td>
  </tr>
  </tbody>
</table>

### Dynamische media {#dynamic-media-issues}

<table>
  <tbody>
  <tr>
    <td><strong>Video</strong></td>
    <td><strong>Sets draaien en slim uitsnijden</strong></td>
    <td><strong>Levering &amp; instellingen</strong></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26533">Problemen met het uploaden, verwerken en renderen van video in AEM verhelpen</a></td>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26715">Draaiende sets blijven steken in verwerkingsstatus</a></td>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-17628">URL van dynamische media voor elementen wijzigen</a></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26677">Videominiaturen komen niet overeen tussen Dynamic Media en DAM Card View</a></td>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26873">Smart Crop-uitvoeringen niet gegenereerd in AEM as a Cloud Service</a></td>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26367">Probleem met gebroken afbeeldingen met SmartCrop in AEM 6.5</a></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26610">Fout bij verwerking van middelen in AEM Dynamic Media</a></td>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26637">Probleem met achtergrondkleur voor TIFF-uitvoeringen</a></td>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-25294">De pagina Algemene instellingen van dynamische media wordt niet geopend</a></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26197">Audioproblemen in videobestanden oplossen met Dynamic Media</a></td>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-25885">Fout bij synchronisatie van middelen in dynamische media</a></td>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26461">Verschillen in elementnamen in verschillende omgevingen oplossen</a></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26871">Dynamic Media Video Player werkt niet in lagere omgevingen</a></td>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-25471">Aanbevelingen voor gebruikers voor synchronisatie van dynamische media</a></td>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26902">Elementen en metagegevens exporteren vanuit dynamische media met behulp van API</a></td>
  </tr>
  </tbody>
</table>

### Metagegevens, tags toepassen en delen {#metadata-tagging-sharing-issues}

<table>
  <tbody>
  <tr>
    <td><strong>Metagegevens</strong></td>
    <td><strong>Slimme tags</strong></td>
    <td><strong>Toegang en delen</strong></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-25828">Verschil tussen metagegevens van afbeeldingen in AEM Assets</a></td>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-25925">Automatisch labelen van nieuw geüploade elementen</a></td>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26928">Opmerkingen zijn beperkt in de Assets-weergave ondanks leestoegang</a></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26655">Problemen met de zichtbaarheid van het metagegevensschema voor niet-beheerders oplossen</a></td>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-25889">Slimme tags werken niet na JWT naar OAuth-migratie</a></td>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-25903">Problemen met gedeelde koppelingen in AEM Managed Services oplossen</a></td>
  </tr>

</tbody>
</table>

### Integratie en toegang {#integrations-access}

<table>
  <tbody>
    <tr>
      <td><strong>Koppeling met middelen</strong></td>
      <td><strong>Licenties en aanpassingen</strong></td>
    </tr>
    <tr>
      <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26922">Adobe Asset Link laat koppelingen in InDesign ontoegankelijk</a></td>
      <td>
        <a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26616"> de fragmenten van de Inhoud niet inbegrepen in de vergunning van AEM Assets </a><br>
        </td>
    </tr>
    <tr>
      <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-25562">Verbindingsproblemen met AEM Asset Link in InDesign oplossen</a></td>
      <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-25525">Problemen met de verwerking van bedrijfsmiddelen in AEM as a Cloud Service oplossen</a></td>
    </tr>
    <tr>
      <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-25506">Adobe Asset Link Plug-In-netwerkfout: server niet bereikbaar</a></td>
      <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-25829"> Bijwerkend douaneduimnagels voor videoactiva in AEM as a Cloud Service </a>
      </td>
    </tr>
  </tbody>
</table>




## AEM Forms-probleemoplossing {#aem-forms-troubleshooting}

AEM Forms as a Cloud Service biedt krachtige mogelijkheden voor het maken en beheren van formulieren. Het is echter mogelijk dat er problemen optreden tijdens installatie-, configuratie-, formulier- of verzendprocessen. Deze sectie biedt uitgebreide richtlijnen voor het oplossen van problemen voor algemene AEM Forms-problemen.

### Problemen met installatie en configuratie

<table>
  <tbody>
  <tr>
    <td><strong>Instellen en configureren</strong></td>
    <td><strong>Problemen bij het maken van formulieren</strong></td>
    <td><strong>Prestaties en caching</strong></td>
  </tr>
  <tr>
    <td><a href="/help/forms/troubleshooting-installation-and-configuration.md">Forms-optie niet beschikbaar in Navigatie</a></td>
    <td><a href="/help/forms/form-creation-failing.md">Maken van formulier mislukt na publicatie van sjabloon</a></td>
    <td><a href="/help/forms/troubleshooting-caching-performance.md">Aanpassingsproblemen met Forms-caching</a></td>
  </tr>
  <tr>
    <td><a href="/help/forms/troubleshooting-installation-and-configuration.md#build-pipeline-fails">Fouten met pijplijnen maken</a></td>
    <td><a href="/help/forms/form-creation-failing.md#cause-form-creation-fails">Problemen met publicatiereeks voor sjablonen</a></td>
    <td><a href="/help/forms/troubleshooting-caching-performance.md#images-videos-not-invalidated">Problemen bij validatie van Dispatcher-cache</a></td>
  </tr>
  <tr>
    <td><a href="/help/forms/troubleshooting-installation-and-configuration.md#bundles-inactive-state">Problemen met activering van bundels</a></td>
    <td><a href="/help/forms/known-issues.md">Bekende beperkingen voor het maken van formulieren</a></td>
    <td><a href="/help/forms/troubleshooting-caching-performance.md#cdn-caching-stops-working-after-300-seconds">Fouten in CDN-cache</a></td>
  </tr>
  </tbody>
</table>

### Problemen met het verzenden en integreren van formulieren

<table>
  <tbody>
  <tr>
    <td><strong>Edge Delivery Services</strong></td>
    <td><strong>Aangepaste verzendhandelingen</strong></td>
    <td><strong>Integratieproblemen</strong></td>
  </tr>
  <tr>
    <td><a href="/help/forms/troubleshooting-403-forbidden-edge-delivery-form-submission.md">403 Verboden fouten bij het indienen van formulieren</a></td>
    <td><a href="/help/forms/custom-submit-action-troubleshooting.md">502 fouten in aangepaste verzendacties</a></td>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-27434">DRM-SAML-omleidingsfouten</a></td>
  </tr>
  <tr>
    <td><a href="/help/forms/troubleshooting-403-forbidden-edge-delivery-form-submission.md#cors-issues">CORS-configuratieproblemen</a></td>
    <td><a href="/help/forms/custom-submit-action-troubleshooting.md#resolution">Afhandeling van onverwerkte uitzonderingen</a></td>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-27075">Verzendknop uitgeschakeld op AEM Sites</a></td>
  </tr>
  <tr>
    <td><a href="/help/forms/troubleshooting-403-forbidden-edge-delivery-form-submission.md#referrer-filter-issues">Configuratie van filter Referrer</a></td>
    <td><a href="/help/forms/custom-submit-action-for-adaptive-forms-based-on-core-components.md">Aanbevolen werkwijzen voor aangepaste handelingen</a></td>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26532">Zichtbaarheid van verborgen velden na upgrades</a></td>
  </tr>
  </tbody>
</table>

### Designer en Ontwikkeling

<table>
  <tbody>
  <tr>
    <td><strong>AEM Forms Designer</strong></td>
    <td><strong>Ontwikkelingsomgeving</strong></td>
    <td><strong>Versie en compatibiliteit</strong></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26558">Designer 6.5 wordt niet geopend na upgrade</a></td>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-27089">Locators kunnen niet beginnen met JDK 8/11</a></td>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26862">Weergaveproblemen met AEM Forms (AEMFD)-pakketversies</a></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-21018">Fouten in PDF Generator JPEG 2000</a></td>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-22689">JBoss-configuratie van logpad</a></td>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26846">Onjuiste versienummers in Windows</a></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-27406">Knop ontbreekt in PDF-uitvoer</a></td>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-18084">Configuratiebeheer-upgradefouten</a></td>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-17339">Workarges voor indexbeschadiging</a></td>
  </tr>
  </tbody>
</table>



