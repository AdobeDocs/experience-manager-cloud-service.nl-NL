---
title: Problemen in AEM Assets oplossen
description: Problemen met algemene AEM Assets oplossen met de artikelkoppelingen voor belangrijke AEM Assets s=areas, zoals uploads, metagegevens, zoeken, leveren enzovoort.
hidefromtoc: true
hide: true
source-git-commit: c8f1c40e4300b26141cc394a9208641769da1f1e
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 0%

---


# Problemen met AEM Assets oplossen {#troubleshoot-aem-assets}

AEM Assets as a Cloud Service biedt een geïntegreerde, PaaS-oplossing in de cloud voor bedrijven, niet alleen om hun Digital Asset Management en Dynamic Media-bewerkingen uit te voeren, maar ook om slimme mogelijkheden van de volgende generatie te gebruiken, zoals AI/ML. Allemaal vanuit een systeem dat altijd actueel, altijd beschikbaar en altijd leerend is.

Er kunnen zich echter problemen voordoen die gevolgen hebben voor het uploaden van elementen, metagegevens, zoeken of leveren en andere sleutelgebieden van AEM Assets. Dit artikel bevat stappen voor het oplossen van problemen waarmee u die algemene AEM Assets-problemen kunt opsporen en oplossen.

<table>
  <tbody>
  <tr>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-27140"> Vertoningen die in dossier van het PIT van de activadownload in AEM </a> ontbreken </td>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26616"> de fragmenten van de Inhoud niet inbegrepen in de vergunning van AEM Assets </a> </td>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26928"> het becommentariëren beperkt in de Mening van Assets ondanks gelezen toegang </a> </td> 
    </tr>
    <tr>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26715"> (Dynamische media) Draaiende Reeksen die in verwerkingsstaat in de Dynamische Media van AEM worden geplakt </a> </td>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26639"> de vertoningen van het Beheer van Digitaal Middelen (DAM) passen geen originele dossiers in AEM </a> aan </td>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26873"> Slimme Uitsnijdvertoningen niet die in AEMaaCS </a> worden geproduceerd </td> 
    </tr>
    <tr>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26533"> (Dynamic Media) Problemen met het uploaden, verwerken en renderen van video in AEM verhelpen </a> </td>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26922"> (Asset Link) De koppelingen van Adobe Asset Link zijn niet toegankelijk wanneer u InDesign gebruikt </a> </td>
    <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26677"> de videoduimnagel wanverhouding tussen Dynamische Media en de Mening van de Kaart DAM in AEMaaCS </a> </td> 
    </tr>
    <tr>
  <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26610">Verwerking van middelen is mislukt voor grote MP4-bestanden in AEM as a Cloud Service</a></td>
  <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26871">(Dynamic Media) Dynamische mediasvideo-speler werkt niet in lagere omgevingen</a></td>
  <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26103">(Dynamic Media met OpenAPI) Beperkte Assets-toegang tot dynamische media met open API's activeren op basis van IMS-gebruikersgroepen</a></td>
</tr>
<tr>
  <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-23916">Wanneer een TIFF-bestand met de ZIP-compressie-indeling naar AEM Assets wordt geüpload, worden geen vertoningen gegenereerd</a></td>
  <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26785">AEM kapt geëxtraheerde tekst van grote PDF's na 100K-tokens af</a></td>
  <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-17628">(Dynamische media) Dynamische media-URL wijzigen voor DM Assets</a></td>
</tr>
<tr>
  <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26655">Problemen met de zichtbaarheid van metagegevensschema's voor gebruikers zonder beheer in AEMaaCS oplossen</a></td>
  <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26637">(Dynamische media) Probleem met wijziging van achtergrondkleur voor TIFF-afbeeldingsuitvoeringen in dynamische media</a></td>
  <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26528">AEMaaCS Asset-rotatie maakt volgende rotaties onzichtbaar</a></td>
</tr>
<tr>
  <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26367">(Dynamische media) Probleem met verbroken afbeeldingen oplossen met SmartCrop in Adobe Experience Manager 6.5 Dynamic Media</a></td>
  <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26450">Uploadlimiet voor enkelvoudige onderdelen voor Photoshop Firefly API-integratie verhogen</a></td>
  <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26461">(Dynamic Media) Los verschillen tussen dynamische media-elementen in AEM-omgevingen voor PDF-bestanden op</a></td>
</tr>
<tr>
  <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26233">In Adobe Experience Manager (AEM) as a Cloud Service - Asset wordt in bepaalde afbeeldingen geen miniatuuruitvoering weergegeven</a></td>
  <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-25294">(Dynamische media) Pagina Algemene instellingen dynamische media wordt niet geopend</a></td>
  <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26197">(Dynamic Media) Het probleem van audiobestanden in videobestanden oplossen met Dynamic Media in AEM</a></td>
</tr>
<tr>
  <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-25925">Automatisch labelen van nieuw geüploade elementen in AEM as a Cloud Service</a></td>
  <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-25889">Functionaliteit voor slimme tags werkt niet na migratie van JWT naar OAuth in AEM</a></td>
  <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-25903">Problemen met gedeelde koppelingen in AEM Managed Services oplossen</a></td>
</tr>
<tr>
  <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-25607">(Dynamic Media) Problemen met de verwerking van bedrijfsmiddelen in AEM Dynamic Media</a></td>
  <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-25885">(Dynamic Media) Fout bij synchronisatie van middelen in Adobe Experience Manager (AEM) Dynamic Media</a></td>
  <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-25829">Aangepaste miniaturen voor video-elementen bijwerken in AEM as a Cloud Service</a></td>
</tr>
<tr>
  <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-25828">Verschil tussen metagegevens van afbeeldingen in Adobe Experience Manager (AEM) Assets</a></td>
  <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-21865">Slepen en neerzetten van een map met middelen naar de gebruikersinterface van AEM Assets Web mislukt</a></td>
  <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-25525">(Dynamic Media) Problemen met de verwerking van bedrijfsmiddelen in AEM as a Cloud Service oplossen</a></td>
</tr>
<tr>
  <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-25518">Beperkingen voor het uitnemen van tekst voor grote PDF's in Adobe Experience Manager as a Cloud Service</a></td>
  <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-25562">(Asset Link) Problemen met koppelingen naar Adobe Experience Manager-middelen (AEM) oplossen in InDesign</a></td>
  <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-25506">(Asset Link) Adobe Asset Link Plug-In Network Error: Server is niet bereikbaar</a></td>
</tr>
<tr>
  <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-25471">(Dynamische media) Dynamische aanbevelingen van de gebruiker van de media synchronisatie</a></td>
  <td><a href="https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26902">(Dynamische media) Exporteer elementen en metagegevens van Dynamic Media met behulp van API</a></td>
  <td></td>
</tr>

</tbody>
  <table>


