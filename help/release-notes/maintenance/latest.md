---
title: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: b0198fee3fb8c2f02f50819bea5757e5b8373ac1
workflow-type: tm+mt
source-wordcount: '1241'
ht-degree: 0%

---

# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In de volgende sectie worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van as a Cloud Service Experience Manager beschreven.

## Release 15262 {#release-15262}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 15262 samengevat, die op 6 maart 2024 openbaar werd gemaakt. De vorige onderhoudsrelease was release 14697.

2024.3.0 Activering van functies biedt de volledige functionaliteit die is ingesteld voor deze onderhoudsrelease. Zie de [Experience Manager geeft Routekaart vrij](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html) voor meer informatie .

### Verbeteringen {#enhancements-15262}

* ASSETS-30632: een aparte Brand Portal-kolom met de publicatiestatus toegevoegd in de lijstweergave.
* ASSETS-30934: extra ondersteuning voor `Iptc4xmpCore:AltTextAccessibility` en `Iptc4xmpCore:ExtDescrAccessibility` eigenschappen voor de Editor metagegevens van element.
* ASSETS-31297: Verbetering van de controles om te voorkomen dat gekopieerde elementen uit dynamische media worden verwijderd.
* ACTIVA-33246: Definitie van releaseindex `damAssetLucene-10`.
* ASSETS-33590: voeg ondersteuning toe voor webvertoningen voor video&#39;s in verwerkingsprofielen.
* GRANITE-36205: Werk de eikeversie bij naar 1.60-T20240131102219-0cde853.
* SITES-19326: Update links in Activa UI om CF in nieuwe Redacteur van het CF te openen.
* HULPLIJNEN-12945: Slimme suggesties voor AI om inhoudsverwijzingen toe te voegen tijdens het ontwerpen van inhoud
* HULPLIJNEN-12706: Herziene eigenschap van de versiegeschiedenis in de Redacteur van het Web
* GUIDES-14948: Verbeterde gebruikerservaring in het deelvenster Vertaling
* HULPLIJNEN-8782: Verbeterde zoeklogica in het dialoogvenster Element invoegen
* GUIDES-14681: Mogelijkheid om meerdere uitvoervoorinstellingen met dynamische basislijnen te publiceren
* Voor een volledige lijst met verbeteringen in AEM hulplijnen raadpleegt u : [Nieuwe functies in AEM hulplijnen](https://experienceleague.adobe.com/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2024-releases/2402-release/whats-new-2024-2-0.html?lang=en#release-info)

### Opgeloste problemen {#fixed-issues-15262}

* ASSETS-15977: verwijderde v1-zoekgebeurtenissen en producent van pijpleidingen verwijderen.
* ASSETS-18088: Upgrade bibliotheekafhankelijkheden naar 1.17.
* ASSETS-21965: de terugschrijfworkflow voor metagegevens mag alleen worden gestart bij wijzigingen in metagegevens van elementen.
* ASSETS-26368: Geplande taken voor Bulk-import zijn niet verwijderd als taakconfiguratie niet bestaat.
* ASSETS-26549: Elementen / Nodes met &quot;jcr:lastModifiedBy&quot;: &quot;workflow-process-service&quot; worden in de lijstweergave weergegeven als &quot;externe gebruiker&quot;.
* ASSETS-26842: werk de tekst van de &quot;Firefly&quot;bij om &quot;App Builder&quot;in het Profiel van de Verwerking te lezen.
* ASSETS-28708: zeer trage reactie voor sommige IMS-tokenverzoeken.
* ASSETS-28767: inconsistente publicatiestatus op middelen als map grote nr. bevat. van gepubliceerde activa.
* ASSETS-29011: Smart crop is zichtbaar voor alleen-lezen gebruikers.
* ASSETS-29348: AssetMoveEventHandler kan te veel geheugen verbruiken.
* ASSETS-29738: Asset Upload Restriction mislukt met NullPointerException voor afwateringsbestanden.
* ASSETS-30068: Bulk Import Asset Essentials to include status COMPLETED_WITH_ERROR for &quot;job completed, but with error&quot;.
* ASSETS-30261: Onjuiste imsUserId verzonden naar Pipeline voor activagebeurtenissen.
* ASSETS-30538: de optie Pagina weergeven ontbreekt na het verplaatsen van een PDF-bestand.
* ASSETS-30626: Geen leveringsverzoek ingediend voor activa met lege assetId.
* ASSETS-30756: de handeling Wizard Element verplaatsen mislukt wanneer de mapnaam eindigt in &#39;html&#39;.
* ASSETS-30810: maak tags voordat u de oudere configuratie van uw YouTube rendert.
* ASSETS-31015: Kan elementen met de bestandsnaamtoevoeging .msg niet uploaden.
* ACTIVA-31038: De gebeurtenissen van taken die door de kennisgevingsdienst worden ontvangen worden niet verwerkt.
* ASSETS-31097: Schakel Async Copy for WCM Content uit om doorlopende querywaarschuwingen te voorkomen.
* ASSETS-31256: Elementen / Nodes met &quot;jcr:lastModifiedBy&quot;: &quot;workflow-process-service&quot; worden in de lijstweergave weergegeven als &quot;externe gebruiker&quot;.
* ASSETS-31260: Het veld Formulier Dropdown voor metagegevens van element werkt niet correct wanneer het vervolgkeuzemenu JSON een grote lijst bevat.
* ASSETS-31280: activa in een samengevoegde structuur laten downloaden wanneer deze aan een verzameling worden toegevoegd.
* ACTIVA-31301: `dynamicmedia_sly.js` kan niet correct worden geïnstantieerd door de Use API.
* ASSETS-31330: ko_KR: Niet-gelokaliseerde tekenreeksen in ondertitels en audiotracks.
* ASSETS-31405: de verwerking van de server van het InDesign mislukt voor grote InDesign lay-outs.
* ASSETS-31570: Verenigde Shell - de activadetails &quot;sparen &amp; dicht&quot;, &quot;annuleren&quot;knopen moeten meer dan eens worden geduwd op om te werken.
* ASSETS-31673: Bulk importeren mislukt voor grote Dropbox bestanden.
* ASSETS-32108: AEM Assets slaat door de gebruiker gedefinieerde kaartgrootte niet op in Weergave-instellingen.
* ASSETS-32230: upgrade minimum runtime versie van com.adobe.aem.repoapi bundle.
* ASSETS-32544: De uitvoertaak van metagegevens mislukt af en toe.
* ASSETS-32679: Caching issues with asset (PDF) previews.
* ASSETS-32754: Taken kunnen niet worden toegewezen aan gebruikers die zich niet eerder hebben aangemeld.
* ASSETS-32755: Configureer het taakonderwerp com/adobe/cq/dam/assetmove om een geordende wachtrij te gebruiken.
* ASSETS-32899: zoeken in verzamelingen is bijzonder traag.
* ASSETS-33098: AEM Assets search facets &quot;Tags preate&quot; werkt niet zoals verwacht.
* ASSETS-33454: Controleer de taakactiviteit en opmerkingen die niet in de tijdlijn worden weergegeven.
* ASSETS-34088: PDF preview werkt niet op AEM Assets.
* ASSETS-34155: Dynamic Media - Updated AEM Viewers / 2024.1.0.
* ASSETS-34684: Handle multivalue dc:title in content tree.
* ASSETS-34789: Corrigeer normalisatieproblemen bij de controle van bestandsconflicten.
* DXML-13276: AEM gidsen - integreer indexen in GraniteContent en verwijder hen uit de bibliotheek.
* GRANITE-47995: Verwijderingsbewerkingen kunnen mislukken vanwege conflicten met de eigenschap &quot;cq:isDelivered&quot;.
* GRANITE-48079: Laat de verzoeken van de POST voor online symbolische bevestiging OAuth toe.
* GRANITE-48143: Upgrade org.apache.sling.resourcemerger naar 1.4.4.
* GRANITE-49031: Update to Jackson 2.16.1.
* SCRNS-3961: Schermen - het kanaal van de Opeenvolging: De animatie van Jquery die in de overgang van de Vervaging wordt gebruikt leidt tot zwart scherm.
* SITES-15868: Verbeter de prestaties voor het vermelden van fragmenten.
* SITES-16079: `/fragments/{id}/references` begonnen duplicaten te retourneren.
* SITES-16118: Als een fragment wordt gepatcheerd en een fragmentveld ontbreekt in het model, wordt een uitzondering gegenereerd.
* SITES-16121: Het terugwinnen van een modeldatumveld genereert een uitzondering.
* SITES-16207: De bewerking POST/adobe/sites/cf/models retourneert twee verschillende statuscodes voor OK.
* SITES-17361: Sluit Jsoup opnieuw in in de bundel zonder kop.
* SITES-17768: GraphQL naar Dynamic Media URL uitvoeren voor elementen waarnaar wordt verwezen in Inhoudsfragmenten.
* SKYOPS-66622: De plaatsing van de auteur crasht na het runnen van een bouwstijl voor bouwstijlTransform toegelaten pijpleiding.
* SKYOPS-69977: adaptieve afbeeldingsserver laadt de afbeelding niet na de laatste update.
* GUIDEN-15045: De controle van de spelling in de Redacteur staat niet de selectie van suggesties toe.
* GUIDEN-14968: De globale navigatieknoop werkt niet, en het dashboard kan niet laden.
* GUIDEN-14943: In het inheemse publiceren van PDF, werken de douanekenmerken binnen voorwaardenvooraf instelt niet voor het inheemse publiceren van PDF.
* GUIDEN-15085: In de inheemse publicatie van PDF, worden de belangrijkste verwijzingen niet opgelost voor de versie van December 2023 van de Gidsen van Adobe Experience Manager.
* GUIDEN-13486: **Basislijnfilter** de dossiers werken niet met de Naam van het Dossier in de Redacteur van het Web.
* Voor een volledige lijst met problemen die in AEM hulplijnen zijn opgelost, raadpleegt u : [Opgeloste problemen AEM hulplijnen](https://experienceleague.adobe.com/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2024-releases/2402-release/fixed-issues-2024-2-0.html?lang=en#release-info)

### Bekende problemen {#known-issues-15262}

* ACTIVA-35923: `UnsupportedClassVersionError` in de pijpleiding van CM bouwt stap na verbetering `aem-sdk-api` versie naar `2024.2.15262.20240224T002940Z-231200`. **Vereist actie van klant om versie van CM Java aan 11 te plaatsen**, zie [Build Environment / Setting the Maven JDK Version](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/create-application-project/build-environment-details.html?lang=en#alternate-maven-jdk-version)
* ASSETS-35860: onjuiste tijdzoneconversie in de kolomweergave van AEM Assets.
* SCRNS-4171: De Schermen van vensters gaan leeg en ophouden werkend wanneer bevordering aan 15262 en het publiceren van een kanaal.
* GRANITE-50774: GraniteContent zou deterministische orde van bezit-waarden op init tijd moeten gebruiken.

### Kennisgeving wijzigen {#change-notice-15262}

**Handelingen vereist**

#### CM Java-versie instellen op 11 {#set-java-version-11}

De nieuwe versie van aem-sdk-api bevat klassen die met een doel Java 11 worden gecompileerd, die niet compatibel is met de milieu-standaard JDK versie 1.8 van de Manager van de Wolk bouwt. Deze update vereist dat Maven wordt uitgevoerd met JDK 11.

Klanten wordt aangeraden een `.cloudmanager/java-version` bestand naar de hoofdmap van hun waarschuwingsbericht met de inhoud: `11`. [Build Environment / Setting the Maven JDK Version](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/create-application-project/build-environment-details.html?lang=en#alternate-maven-jdk-version)

#### Aem-cloud-testing-clients bijwerken naar 1.2.1 {#update-aem-cloud-testing-clients}

Voor komende wijzigingen is de bibliotheek vereist [aem-cloud-testing-clients](https://github.com/adobe/aem-testing-clients) gebruikt in uw aangepaste functionele tests die moeten worden bijgewerkt naar ten minste versie **1.**

Zorg ervoor dat uw afhankelijkheid binnen `it.tests/pom.xml` is bijgewerkt.

```xml
<dependency>
   <groupId>com.adobe.cq</groupId>
   <artifactId>aem-cloud-testing-clients</artifactId>
   <version>1.2.1</version>
</dependency>
```

Deze wijziging moet worden uitgevoerd vóór 6 april 2024.

Als u er niet in slaagt de afhankelijkheidsbibliotheek bij te werken, treedt er een fout op bij de stap Aangepast functioneel testen.

### Ingesloten technologieën {#embedded-tech-15262}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM AK | 1,60-T20240131102219-0cde853 | [API voor eik 1.60.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.60.0/index.html) |
| AEM SLING-API | Versie 2.27.2 | [API voor Apache Sling API 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Versie 1.4.20-1.4.0 | [HTML Sjabloontaalspecificaties](https://github.com/adobe/htl-spec) |
| AEM-kerncomponenten | Versie 2.23.4 | [AEM WCM Core-componenten](https://github.com/adobe/aem-core-wcm-components) |
