---
title: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: c1e175128ab6e4b483e3940d9bd86a06540ef40f
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 0%

---


# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In het volgende gedeelte worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van Experience Manager as a Cloud Service beschreven.

## Release 24464 {#release-24464}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 24464 samengevat, die op 18 februari 2026 openbaar werd gemaakt. De vorige onderhoudsrelease was release 24288.

De activering van de 2026.2.0-functie biedt de volledige functie die is ingesteld voor deze onderhoudrelease. Zie [&#x200B; Experience Manager geeft Roadmap &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) voor meer informatie vrij.

### Verbeteringen {#enhancements-24464}

* AEMARCH-264: Voeg steun voor het bevestigen van voorwaardelijke verzoeken toe die op RequestEntiteit worden gebaseerd.
* AEMARCH-269: JavaEE-validatie-API&#39;s voor OpenAPI-implementaties beschikbaar maken.
* AEMARCH-276: i18n steun verlenen door RequestEntiteit.
* ASSETS-10995: limiet instellen voor het aantal elementen in ZIP-bestand voor downloaden.
* ASSETS-50788: zoek-API bijwerken voor gebruik van de Asset Metadata GET API.
* ASSETS-50946: Wijs aanvraaginstantie met Metadata GET API toe aan JCR-metagegevens.
* ASSETS-55866: Vermijd het indienen van een nieuwe aanvraag voor hetzelfde middel totdat de vorige verwerking is voltooid.
* ASSETS-60300: API opgeven om de async taakcontext en het resultaat op te halen.
* ASSETS-60574: voeg ondersteuning toe voor de nieuwste versie van Sling API-bundel.
* ASSETS-61049: Doorgaan met de ontwikkeling van bundels voor het beheer van metagegevens.
* ASSETS-61692: Voer standaard semantische zoekopdrachten uit in de API voor openen van zoeken.
* ASSETS-61696: BAM route en MFE wrapper on assets view.
* ASSETS-61854: GenStudio-oplossing verzenden in activerings-/deactiveringsbericht.
* ASSETS-61973: Maak een API in AEM voor het beheer van vragen.
* ASSETS-62182: Asset Compute-gebeurtenishandler voor c2pa-manifest-uitvoering.
* ASSETS-62311: Problemen met zoekregressie.
* ASSETS-62413: voeg ondersteuning voor het veld customModifier toe in elke laag in JSON.
* ASSETS-62432: Merge folder delete API PR.
* ASSETS-62540: verhoog de voor ui-touch geoptimaliseerde versie in QuickStart.
* ASSETS-62622: Handle search mode in MatchQuery.
* ASSETS-62671: Fix MatchQuery startWith, operator.
* ASSETS-62780: functiewissel toevoegen voor map-API.
* ASSETS-62988: Verberg c2pa-manifestuitvoering in het tabblad Uitvoeringen.
* ASSETS-63336: Sjablonen synchroniseren van AEM naar DM dient alleen plaats te vinden voor dam namespaced metadata.
* ASSETS-63375: Zet het experiment met OpenAPI&#39;s voor het uploaden van middelen in een functiewissel.
* ASSETS-63453: Zorg ervoor dat alle gebruikers de configuratie van het volledige zoekprogramma kunnen lezen.
* GRANITE-63744: Sta verbindende async banen aan sling banen toe.
* GRANITE-64567: Schakel semantische zoekopdracht naar SKU-zoekopdrachten automatisch uit.
* HULPLIJNEN-41187: Voeg kopballen voor het gebruik van Gidsen toe.
* SITES-30452: Content API met ASO - title- en beschrijvingssuggesties.
* SITES-33116: Padvalidatie herstellen.
* SITES-34234: Pagina-editor: status van inhoudsboomstructuur behouden.

### Opgeloste problemen {#fixed-issues-24464}

* ASSETS-43198: E-mailberichten over het verlopen van bedrijfsmiddelen voldoen niet aan de voorkeur voor de gebruikerstaal.
* ASSETS-51840: Verbeteringen in de verwerking van bedrijfsmiddelen.
* ASSETS-52061: kan niet terugnavigeren nadat u een opgeslagen zoekopdracht hebt geselecteerd.
* ASSETS-53155: Verbeteringen aan de inhoud van bedrijfsmiddelen.
* ASSETS-53745: bij dynamische media-downloadstroom is het vereist dat u het oorspronkelijke element niet selecteert voordat u een webvoorinstelling kiest.
* ASSETS-54260: fixes voor de inhoud van activa.
* ASSETS-54787: Verbeteringen aan de inhoud van bedrijfsmiddelen.
* ASSETS-57391: updates van de inhoud van bedrijfsmiddelen.
* ASSETS-59213: cq-dynamicmedia-core is afhankelijk van afgekeurde commons-lang-bibliotheek.
* ASSETS-59214: cq-scene7-imaging is afhankelijk van vervangen commons-lang-bibliotheek.
* ASSETS-59546: cq-remotedam-client-core is afhankelijk van vervangen commons-lang bibliotheek.
* ASSETS-59703: cq-dam-core is afhankelijk van vervangen komma-lang bibliotheek.
* ASSETS-59705: cq-dam-handler is afhankelijk van afgekeurde commons-lang-bibliotheek.
* ASSETS-59707: cq-dam-indesign is afhankelijk van vervangen komma-lang bibliotheek.
* ASSETS-59709: cq-scene7-core is afhankelijk van afgekeurde commons-lang-bibliotheek.
* ASSETS-59929: CSV van meta-gegevens wordt uitgevoerd breken wanneer het gebied newline karakter heeft.
* ASSETS-60241: Verplaats een synchronisatietaak mislukt bij het wijzigen van de mapnaam.
* ASSETS-61134: Verwijder vergelijkingsversietags uit pombestanden.
* ASSETS-61309: Verplaatsen/kopiëren van inhoudsfragment werkt interne verwijzingen niet meer bij.
* ASSETS-61730: Omleiding naar Directe Binaire Toegang dient de codering van middelen te respecteren.
* ASSETS-62358: Assets-rapport CSV geeft corrupte waarden weer in het inhoudspad.
* ASSETS-62610: Adobe Stock-licentieknop uitgeschakeld in Assets-gebruikersinterface.
* ASSETS-62613: NPE in `downloadasset`/`saveas` .
* ASSETS-62656: zoekindicator van Omnsearch AI onjuist weergegeven voor zoekopdrachten van andere leveranciers dan Assets.
* GRANITE-55387: Als u het woord corrigeert dat tussen aanhalingstekens staat, wordt het hele woord verwijderd.
* GRANITE-61240: RCE via stored XSS in lazycontainer.js.
* GRANITE-64101: OOTB indexen omgezet in ES keerden terug naar Lucene bij opnieuw opstarten.
* SITES-24530: aanraakdoel van knop Sluiten/Verwijderen in zoekmodus is niet groot genoeg.
* SITES-31425: Niet-gelokaliseerd foutbericht in startworkflow.

### Bekende problemen {#known-issues-24464}

Geen.

### Verouderde functies en API&#39;s {#deprecated-24464}

Vervangen en verwijderde eigenschappen en APIs in AEM as a Cloud Service zijn gedetailleerd in [&#x200B; Vervangen en Verwijderde Eigenschappen en APIs &#x200B;](/help/release-notes/deprecated-removed-features.md) document.

### Beveiligingsproblemen {#security-24464}

AEM as a Cloud Service is gewijd aan het optimaliseren van de beveiliging en prestaties van uw platform. Deze onderhoudrelease verhelpt 14 geïdentificeerde kwetsbaarheden en versterkt onze inzet voor robuuste systeembescherming.

### Ingesloten technologieën {#embedded-tech-24464}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM Oak | 1 90,0 | [&#x200B; Oak 1.90.0 API &#x200B;](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.90.0/index.html) |
| AEM SLING-API | 2,27,6 | [&#x200B; Apache Sling API 2.27.6 API &#x200B;](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTML | 1.4.28-1.4.0 | [&#x200B; Specificatie van de Taal van het Malplaatje van HTML &#x200B;](https://github.com/adobe/htl-spec) |
| Apache HTTP Server | 2,4,65 | [&#x200B; Apache Httpd 2.4.65 &#x200B;](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| AEM-kerncomponenten | 2.30.4. | [&#x200B; AEM WCM de Componenten van de Kern &#x200B;](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (standaard) | [&#x200B; Ondersteunde versies Node.js &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |

