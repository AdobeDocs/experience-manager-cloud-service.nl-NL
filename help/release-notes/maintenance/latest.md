---
title: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: d3a935a061831befaebd2ce25c00f8bf10522f6c
workflow-type: tm+mt
source-wordcount: '1553'
ht-degree: 0%

---


# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In het volgende gedeelte worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van Experience Manager as a Cloud Service beschreven.

## Release 20783 {#20783}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 20783 samengevat, die op 13 mei 2025 openbaar werd gemaakt. De vorige onderhoudrelease werd uitgebracht in 20626.

De activering van de 2025.5.0-functie biedt de volledige functie die is ingesteld voor deze onderhoudrelease. Zie [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) voor meer informatie vrij.

### Verbeteringen {#enhancements-20783}

* FORMS-18455: De AEM Forms Core Component Adaptive Form Editor is verbeterd en beschikt nu over visuele indicatoren (punten) voor gegevensobjecten die al in het formulier worden gebruikt of toegewezen in de gegevensbronstructuur. Met deze functie kunnen auteurs eenvoudig gebruikte gegevenselementen herkennen.
* FORMS-18450: het product wordt verbeterd door de reCaptcha V2-domeinlogica naar de `AdaptiveFormConfigurationServiceImpl` te migreren. Deze wijziging is bedoeld om de configuratie te centraliseren en kan worden uitgelijnd met het toevoegen van ondersteuning voor onzichtbare reCaptcha V2 in Core Components.
* FORMS-19630: De AEM 6.5 quickstart uber-jar wordt bijgewerkt met het nieuwste Adaptive Forms Core Components-pakket, zodat de quickstart-omgeving de meest actuele Adaptive Forms-functionaliteit weerspiegelt en de oudere code vervangt.
* FORMS-19125: De editor voor adaptieve formulieren voor kerncomponenten is verbeterd en biedt nu ondersteuning voor automatische toewijzing van beschikbare fragmenten van adaptieve formulieren wanneer een corresponderende sectie uit de gegevensbronstructuur naar het formuliercanvas wordt neergezet. Dit brengt een zeer belangrijke productiviteitseigenschap van de stichtingsredacteur aan kerncomponenten.
* FORMS-17887: AEM Forms biedt nu de mogelijkheid om documenten te genereren in de AFP-indeling (Advanced Function Presentation) via de uitvoerservice. Deze verbetering komt tegemoet aan de behoeften van klanten aan supersnelle, hoogwaardige afdrukomgevingen die doorgaans AFP gebruiken.
* FORMS-15089: AEM Forms heeft de mogelijkheid geïntroduceerd om een formulier bij publicatie zodanig te versieren dat alle samenstellende fragmenten in die specifieke gepubliceerde versie worden ingebouwd (ingesloten). Dit zorgt voor een exacte, op zichzelf staande weergave van het formulier zoals het op het moment van publicatie werd weergegeven. Dit kan van essentieel belang zijn voor archiveringsdoeleinden, juridische aspecten of nalevingsdoeleinden.
* SITES-2775: Geoptimaliseerde zoekopdracht naar verwijzingen tijdens de publicatie.
* SITES-30885: Geoptimaliseerde verwerking JSON in persisted query.
* SITES-25433: Edge Delivery met Universal Editor: ondersteuning voor rendering van volledige pagina&#39;s bij vergelijking van oude versies.
* SITES-27792: Edge Delivery met Universal Editor: specifieke sjabloon toevoegen voor Edge Delivery Service-configuraties
* SITES-19754: Edge Delivery met Universal Editor: aansprekend foutbericht wanneer de installatie wordt verbroken.
* SITES-30328: Edge Delivery met Universal Editor: voorvertoning van Sidekick-ondersteuning.
* SITES-23499: Edge Delivery met Universal Editor: toestaan dat meerdere velden worden gebruikt voor blokopties.
* SITES-29987: Voeg mogelijkheden toe om `previewUrlPattern` in te stellen bij het maken van modellen voor inhoudsfragmenten.
* SITES-29874: Voeg ondersteuning toe voor LongTextField-verwijzingen in Content Fragment API.
* SITES-29601: Voeg validatie toe voor inhoudsfragmenten waarnaar wordt verwezen via LongText-velden.
* SITES-24623: maak ETags die door GET en SEARCH fragments API worden geretourneerd, bruikbaar voor patch.
* SITES-28557: URL-parameter toestaan `references` in PATCH Content Fragment.
* SITES-5358: [ OpenAPI ] de Fragmenten van de Inhoud van het Exemplaar met kinderen.
* SITES-29614: GET-workfloweindpunt.
* SITES-29615: De partij van de lijst vraagt API eindpunt.
* SITES-25130: Upgrade Core Components to 2.28.0
* SITES-10575: &quot;MSM Blueprint Bloomfilter Loader&quot; probeert meer dan 100&#39;000 rijen te laden.
* SITES-26711: Koppelingen voor RTE-tekstvelden worden niet bijgewerkt om naar de live kopie op MSM-rollout te verwijzen.
* SITES-25976: Koppelingen binnen ervaringsfragmenten die zich niet aanpassen na MSM-implementatie.

### Opgeloste problemen {#fixed-issues-20783}

* ASSETS-50994: Binnenkomend verkeer geblokkeerd bij AemRequestEventFilter.
* CQ-4358591: Ontbrekende projecten voor weinig talen wanneer taalkopieën worden gemaakt in het referentiepaneel van sites met de optie &quot;Vertaalprojecten(en) maken&quot;.
* CQ-4359108: De XLIFF 2.0-indeling werkt niet bij gebruik van Human Translation Import/Export.
* CQ-4358722: Lokalisatie werkt niet voor oudere ISO-codes vanwege verschillende landinstellingscodes in Java 11 en Java 17.
* FORMS-19808: wanneer u een groot formulier opslaat dat fragmenten bevat die zijn ingeschakeld met &#39;lazy loading&#39;, kunnen concepten niet door de gebruiker worden opgehaald.
* FORMS-1987: Een vervolgkeuzelijst in een XFA-formulier, oorspronkelijk ingesteld op readOnly-toegang, verandert niet in een open/bewerkbare status wanneer het formulier wordt weergegeven in HTML5. Het veld blijft alleen-lezen en voorkomt gebruikersinteractie, anders dan bij PDF-rendering waarbij het naar behoren functioneert.
* FORMS-19651: In de Redacteur van de Regel, werkt een regel niet correct wanneer een knoop wordt gebruikt in een binaire voorwaarde en de zelfde knoop wordt ook gebruikt in de &quot;toen&quot;verklaring van die regel.
* FORMS-19628: In automatisch gegenereerd document of Record (DoR) voor op Core-component gebaseerde adaptieve Forms, waarbij de titel van een genest deelvenster niet in de DoR wordt opgenomen, wordt de titel van het hoofddeelvenster ook onjuist verborgen als de optie &#39;RTF-tekst toestaan voor titel&#39; in het hoofddeelvenster is ingeschakeld.
* FORMS-18977: PDF&#39;s die zijn gegenereerd door de Document of Record-service (DoR) ontbreken de documenttitel. Dit kan leiden tot niet-naleving van de toegankelijkheidsstandaarden PDF/UA en WCAG 2.1, omdat de documenttitel een verplicht kenmerk is voor toegankelijke PDF&#39;s.
* FORMS-18526: Wanneer een regel die meerdere velden in de bijbehorende omstandigheden bevat, van het ene veld naar het andere wordt gekopieerd, behoudt een vaste veldverwijzing in deze omstandigheden ten onrechte zijn verwijzing naar het oorspronkelijke bronveld in plaats van bij te werken naar het nieuwe veld waar de regel wordt gekopieerd.
* FORMS-19047: Nadat een adaptief formulier is gewijzigd en opnieuw is gepubliceerd op AEM Forms (met name 6.5.22.0 ), ontbreken mogelijk vertalingen voor bepaalde formulierelementen, met name tekstvakken.
* FORMS-19234: De tijdlijnfunctie voor PDF&#39;s in AEM Forms, waarmee gebruikers details kunnen bekijken over het maken en versieren van een PDF, werkt niet meer nadat een PDF is geüpload onder de sectie &#39;Forms and Documents&#39;.
* FORMS-19373: Replicatiefouten worden onjuist gerapporteerd tijdens een &#39;gouden publicatieproces&#39; in omgevingen waarin geen replicatiemiddelen zijn geconfigureerd.
* FORMS-18196: De HTTP-API voor `generatePrintedOutput` (of `generatePdfOutput` ) synchroniseren retourneert onjuist een antwoordcode voor 200 (Succesvol) in plaats van de verwachte foutcode voor 400 (Ongeldig verzoek) wanneer de optionele veldgegevens die door de XDP-sjabloon worden vereist, leeg blijven in de aanvraag.
* FORMS-1936: In de Adaptieve Form Editor (AF2-editor) van de Core-component werkt de zoekfunctionaliteit in de Source-structuur voor gegevens niet correct of naar behoren, waardoor gebruikers niet gemakkelijk specifieke gegevenselementen kunnen vinden.
* FORMS-19629: De JSON schema parser veroorzaakt ongeldige resultaten of onjuist interpreterend bepaalde klant-verstrekte JSON schema&#39;s. Dit probleem kan negatieve gevolgen hebben voor functies die afhankelijk zijn van correcte schemapparsering, zoals de automatische toewijzing van fragmenten.
* FORMS-19380: De introductie van versioning-ondersteuning voor Core Component Adaptive Forms heeft onbedoeld versiemogelijkheden ingeschakeld voor verschillende andere typen middelen (bijvoorbeeld Foundation Forms, PDF-bestanden, Thema&#39;s, FDM) zonder dat er een specifiek ontwerp of tests voor deze elementtypen nodig zijn. Deze onbedoelde bijwerking wordt onderzocht.
* FORMS-17707: De AEP (Adobe Experience Platform)-connector werkt niet correct wanneer deze is geconfigureerd om verbinding te maken met &#39;stage&#39;-omgevingen van het AEP-platform.
* GRANITE-58276: De cycli van de afhankelijkheid OSGi verhinderen de fabriek van de HTML manuscriptmotor correct te werken.
* OAK-11673: Oak-segment-azure v12 CPU verhoging veroorzaakt door refreshLease.
* SITES-30752: Gebruik `If-modified-since` niet/ `last-modified` kopballen wanneer het produceren van voortgezette vraagreactie.
* SITES-30353: GraphQL DataFetchingExceptions for &quot;src&quot; Field in AEM Content Fragments.
* SITES-30333: Lees metagegevens over elementen van jcr om problemen met xmp-parsering te voorkomen.
* SITES-30140: probleem met twee vensters bij het maken van een verwijzing naar een inhoudsfragment.
* SITES-29748: Corrigeer renderconditions om beheerpublicatie/quickpublish-handelingen in de CF-editor weer te geven.
* SITES-15452: Unieke CF-elementen mogen in de lancering niet op hun kopieën worden gecontroleerd.
* SITES-30386: Edge Delivery met Universal Editor: gedupliceerde UE cors.js leidt ertoe dat UE secties dupliceert wanneer inhoud wordt toegevoegd.
* SITES-29745: Probleem verholpen waarbij variaties van verwijzingen niet werden gehydrateerd.
* SITES-30585: Kan &#39;previewUrlPattern&#39; niet instellen bij het maken van modellen met referenties.
* SITES-30327: Het publiceren van inhoudsfragmenten zonder toestemmingen leidt tot afzonderlijke werkschema&#39;s voor elke ladingsmiddel.
* SITES-29528: ETag kan niet voor caching op publicatieinstantie worden gebruikt.
* SITES-30583: Het gereedschap Zoeken en vervangen wijzigt alle tekens in kleine letters.
* SITES-31157: Patch mislukt vanwege inconsistente ETag.
* SITES-31327: [ OpenAPI ] krijgt het verzoek van het inhoudsfragment op auteursinstantie kan met 304 antwoorden.
* SITES-29691: NullPointerException wanneer probeerde om Pagina te bewegen.
* SITES-30728: OnTime/OffTime publiceert/UnPublish niet zoals verwacht wanneer gevormd op activa eigenschappen.
* SITES-29789: Component Link Change on Copied Root Pages in AEM.
* SITES-29191: Kan niet meer dan 20 SKU&#39;s toevoegen aan de component Productlijst.
* SITES-30372: Smart Crop werkt niet op de kerncomponent Image(V2) van AEM.
* SITES-28693: De component van de laser geeft gebroken HTML terug wanneer de titel leeg is.
* SITES-28668: Kan Starten met LaunchPromotionParameters niet bevorderen.
* SITES-31005: Verbeter de UI van de Taak van de Uitvoer om de klant de vooruitgang te tonen.
* SITES-31020: Verbeter Create Live Copy Job UI om de klant de voortgang te laten zien.
* SITES-29816: Fout &quot;Resource Not Found&quot; tijdens het maken van een live kopie van ervaringsfragment.
* SITES-29363: De knop Live kopie herstellen werkt niet voor een geneste inhoudshiërarchie voor live kopieën.
* SKYOPS-106509: Voeg extra toe:voegen-opent vlaggen toe om GSON weerspiegelende toegang op Java 21 te steunen.

### Bekende problemen {#known-issues-20783}

Geen.

### Verouderde functies en API&#39;s {#deprecated-20783}

Vervangen en verwijderde eigenschappen en APIs in AEM as a Cloud Service zijn gedetailleerd in [ Vervangen en Verwijderde Eigenschappen en APIs ](/help/release-notes/deprecated-removed-features.md) document.

### Beveiligingsproblemen {#security-20783}

AEM as a Cloud Service is gewijd aan het optimaliseren van de beveiliging en prestaties van uw platform. Deze onderhoudrelease verhelpt 19 geïdentificeerde kwetsbaarheden en versterkt onze inzet voor robuuste systeembescherming.

### Ingesloten technologieën {#embedded-tech-20783}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM Oak | 1.78.1-T20250429061757 | [ Oak API 1.78.0 ](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.78.0/index.html) |
| AEM SLING-API | 2,27,6 | [ Apache Sling API 2.27.6 API ](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTML | 1.4.26-1.4.0 | [ Specificatie van de Taal van het Malplaatje van HTML ](https://github.com/adobe/htl-spec) |
| AEM-kerncomponenten | 2 29,0 | [ AEM WCM de Componenten van de Kern ](https://github.com/adobe/aem-core-wcm-components) |
