---
title: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: d107f40c4bc43837db9d8fab3d06627d9e930620
workflow-type: tm+mt
source-wordcount: '1574'
ht-degree: 0%

---

# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In de volgende sectie worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van as a Cloud Service Experience Manager beschreven.

## Release 16357 {#release-16357}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 16357 samengevat, die op 22 mei 2024 openbaar werd gemaakt. De vorige onderhoudsrelease was release 16145.

2024.5.0 Activering van functies biedt de volledige functionaliteit die is ingesteld voor deze onderhoudsrelease. Zie de [Experience Manager geeft Routekaart vrij](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) voor meer informatie .

### Verbeteringen {#enhancements-16357}

* SITES-19579: Java API om inhoudsfragmenten van het ene model naar het andere te migreren.
* SITES-19698: [API openen] Maak een leesbewerking voor het beheer van een UI-schema per model in de OpenAPI-definitie.
* SITES-19834: Adobe I/O-gebeurtenis heeft geen id voor publiceren/verwijderen.
* SITES-20146: Enable Preview Version / Compare for moving pages.
* SITES-19973: CFM Search API Implementation.
* SITES-2033: Verbeter bevestiging wanneer het creëren van Inhoudsfragmenten.
* SITES-2034: Verbeterde validatie bij het bewerken van modellen van inhoudsfragmenten.
* SITES-20585: Verbeter de zoekAPI voor inhoudsfragmenten om te filteren op landinstelling.
* SITES-20594: Retourneer de volledige naam van de gebruiker die een bron maakt, wijzigt of repliceert.
* SITES-20601 [OpenAPI] Werk de zoekAPI van CF bij om alleen fragmenten van directe onderliggende inhoud op te halen.
* SITES-20656: [BE] Geef een optie die overeenkomt met hoofdletters en kleine letters bij het vervangen van een tekenreeks.
* SITES-20405: [Xwalk] Ondersteuning voor mimeType voor het samenvouwen van velden.
* SITES-17854: Steun UID voor CF &amp; activa verwijzingen (Pfizer MVP).
* SITES-1955: Simple Model API voor UI-schema.
* SITES-19611: [API openen] Maak een schrijf-/updatebewerking voor het beheer van een UI-schema per model in de OpenAPI-definitie.
* SITES-19614: [Xwalk] Paginering van werkblad / oneindige schuifbalk.
* SITES-2005: De auteurspijpleiding zou een configureerbare gebeurtenisvertraging moeten hebben.
* SITES-20121: Allow defaultValue for enum fields.
* SITES-20342: [Achtergrond] Publiceren op mapniveau - filter toevoegen om alleen CF&#39;s te publiceren.
* SITES-20355: Verwijder modellen van inhoudsfragmenten en toestemmings API servlets.
* SITES-20387: Door de tagbeheerder te navigeren, wordt het taggebruik altijd berekend.
* SITES-20495: [BE] Mogelijkheid om toestemming te krijgen om te publiceren op mapniveau.
* SITES-20653: [Xwalk] Voeg een begin- en einddatum voor het experiment toe.
* SITES-2066: [Xwalk] experimenteren moet standaard worden uitgeschakeld tijdens het ontwerpen.
* SITES-20752: [cq-wcm-core] Apple start op voor CF&#39;s.
* SITES-20946: Voeg markering als bezit in het modeleindpunt van LIST toe.
* SITES-20947: [volharding] subtaak ophalen met id van inhoudsfragment.
* SITES-21012: Merge Model Metadata Schema to product.
* SITES-21769: Gebruik het /jcr:id/ padvoorvoegsel voor bron-voor-id-opvraging.
* ASSETS-30379: met DRM-licentiecontrole wordt een volledige structuur met elementen beheerd die worden gedownload.
* ACTIVA-35535: [Fout in DataS-adapter] Lege Asset-downloads moeten worden genegeerd voor gebeurtenissen van versie 1.
* SITES-2150: [Xwalk] Aangepaste metagegevens: nummer, datum, datumtijd, tijdvelden.
* SITES-20149: RTC: [cq-wcm-lanceerkern] Exporteer nieuwe API voor opstarters voor CF&#39;s.
* SITES-20150: RTC [cq, opdracht] Nieuwe methoden toevoegen aan bestaande API.
* SITES-20451: Voeg secundaire plug-in toe aan wcm-commons.
* SITES-2049: [MSM][Async] Extraheer de code van AsyncOperationServlet naar een hulpprogrammaklasse.
* SITES-20763: Werk API-eindpunten voor levering bij in de integratie van sites.
* SITES-20583: Add tag as property in `LIST`/search fragments.
* CQ-4356445: Implementatie van gebeurtenisproducent en -schema.
* CQ-4356625: Verbetering van de controle van vergunningen in languageCopyrendercondition.jsp.
* CQ-4356629: Verbeter toelatingscontrole in isWorkflowUser rendercondition.
* CQ-4356934: Vereenvoudig de API RequestProcessor wanneer u werkt met ResponseEntities.
* CQ-4357214: Processors voor aanvragen mogen niet afhankelijk zijn van servletlogica.
* SITES-16392: Het maken van de opstart is mislukt. Verlaat geen afvalinhoud.
* SITES-20238: [RTC] Pfizer MVP - voeg CF API toe om de wegen van CF aan IDs en voor vice versa op te lossen.
* SITES-21043: [CF][launches] Prestatieverbeteringen aan de Cloud Service op de zijkant.
* SITES-21044 [CF][launches] De async van de zijhaven geeft nuttige ladingimplementatie aan Cloud Service uit.
* FORMS-7483: AEM Forms JSON Schema Parser ondersteunt nu het JSON-schema (2020-2012).
* FORMS-13209: Een handler is inbegrepen om de standaardverwerkings- en verzendmislukkingshandlers van Adaptive Forms te negeren. U kunt deze handlers configureren via de Adaptive Forms Rule Editor.
* FORMS-13612: Schermlezers lezen nu foutberichten, korte beschrijvingen en lange beschrijvingen voor velden in de belangrijkste op componenten gebaseerde Adaptieve Forms. Daarnaast is ondersteuning toegevoegd voor het ongeldig maken van adaptieve invoer van formulieren als het formulier fouten bevat en niet geldig is voor verzending.
* FORMS-12052: Een auteur van een formulier kan nu aangepaste functies toepassen om gegevens vooraf te verwerken voordat ze worden verzonden.
* FORMS-11295: extra ondersteuning voor SHA256 met ECDSA-algoritme voor AEM Forms Digital Signature.
* FORMS-9432: Een extra inhoudstype (REST Endpoint) is toegevoegd aan de configuratie van de gegevensbronwolk. Het laat gegevensvoorlegging in zeer belangrijk-waardeparen aan een voor authentiek verklaard eindpunt toe.

### Opgeloste problemen {#fixed-issues-16357}

* SITES-20608: De ervaring van het Fragment met toegelaten verpersoonlijking wanneer inbegrepen in een malplaatje veroorzaakt een oneindige lijn.
* SITES-1954: [Xwalk] Werkbladeditor: kan een cel niet leeg maken.
* SITES-19971: Door een CFM met tabs te repareren, wijzigt u de volgorde van de velden.
* SITES-20168: Content Fragment Model `locked` niet correct bijgewerkt.
* SITES-20522: Het onderbroken eindpunt van de Fragmenten van de Inhoud breken /adobe/sites/cf/fragments.
* SITES-20816: CF OpenAPI - Uitvoerinconsistentie met ontbrekend model voor fragment waarnaar wordt verwezen.
* SITES-21239: Verwijder circulaire afhankelijkheid van ContentFragmentSearchService.
* SITES-20582: Bij het zoeken naar en het weergeven van inhoudsfragmenten moet diepte 0 mogelijk zijn.
* SITES-2059: [MSM][XF][Lufthansa] Bij de implementatie van fragmenten uit de ervaring van stramienen/talen naar land/taal worden verwijzingen niet bijgewerkt.
* SITES-17772: AEM: Gebruiker met beheerdersgroep kan de pagina niet ontgrendelen wat een andere gebruiker heeft vergrendeld.
* SITES-20401: [Xwalk] Sectiemetagegevens ondersteunen eigenschappen met meerdere waarden niet.
* SITES-21391: [OpenAPI-gebeurtenis] Er worden geen gebeurtenissen geactiveerd tijdens het wijzigen van de titel of tags (eigenschappen) van een inhoudsfragmentmodel.
* SKYOPS-73234: Het mislukken van het foutenlogboek verhoogt op AEM Assets Global DAM programmaverbetering aan AEM versie 15553 en PR Identiteitskaart 35362.
* SKYOPS-75341: NodergelijkeMethodError in de bundel van de Crosswalk van de distributie.
* SCRNS-3945: Veldlijn: Niet-gelokaliseerde &quot;Geplande&quot;koord in Schermen.
* SITES-20586: Sjabloon &quot;Gepubliceerd&quot; tijdstempel niet bijgewerkt.
* SITES-16674: Het selectievakje Inherit rollout configureert het werk aan live kopieereigenschappen.
* SITES-18680: Kan geen verwijzingsvariaties in grafische vraag (Apple) trekken.
* SITES-2123: [CoreCmp] Accordion wordt afgebroken voor GS1 US na upgrade naar 15860.
* SITES-20367: Issue with Deleting Launches in AEM.
* CQ-4357161: AEM Inbox Payload-scherm retourneert 404.
* SITES-20214: AEM probleem met de configuratievolgorde van de rollout bij opslaan.
* SITES-20364: 302 leidt niet Werken met kiezer in URL.
* SITES-20547: Afgeknot paden in lijst met uitgesloten paden van Live kopie op AEM as a Cloud Service.
* SITES-20691: Experience Fragment Template Restriction Not Honoring cq:allowedTemplates.
* SITES-21122: AEM CS Live Copy Defect with Content Fragments.
* ASSETS-38723: NPE gegenereerd door MetadataRulesProviderImpl wanneer getReadRulesForMetadataChildNodes() wordt aangeroepen voordat this.readRules wordt geïnitialiseerd.
* SITES-1727: [GQL] Bij volledige hydratie van verwijzingen naar inhoudsfragmenten ontbreken gegevens.
* SITES-19462: Het zoeken naar middelen werkt niet correct in AEM Cloud.
* SITES-1994: De knop Sluiten wanneer de gebruikers proberen om het Fragment van de Inhoud te sluiten.
* SITES-20029: Versies voor inhoudsfragmenten worden direct na het sluiten ervan gemaakt zonder de inhoud te wijzigen.
* SITES-21316: Voorvertoning van fragment: voorvertoning mislukt als gevolg van codewijzigingen van SITES-11727.
* SITES-20023: FileUpload werkt niet voor Remote(Next gen assets)-elementen in meerdere velden.
* ASSETS-37611: De workflow &quot;Verzoek om de verplaatsing te voltooien&quot; wordt geactiveerd voor niet-gepubliceerde middelen.
* CQ-4357278: DispatcherServlet werpt NPE als getRequestBodyType null retourneert.
* CQ-4357279: De verzoekverwerking ontbreekt wanneer er geen pathInfo voor een verzoek is.
* SITES-20496: [Xwalk] Geen optie voor eigenschappen bij het selecteren van spreadsheet in sitebeheer.
* FORMS-13827: In de Adaptive Forms Rule Editor biedt de WHEN-bewerking momenteel geen ondersteuning voor verschillende typen velden met datumkiezers.
* FORMS-13786: In de Adaptive Forms Rule Editor werkt de functie voor slepen en neerzetten niet voor aangepaste functies.
* FORMS-13587: In de Adaptive Forms Editor werkt de functie Device Emulator niet correct voor op Core Components gebaseerde Adaptive Forms.
* FORMS-14376 Wanneer een gebruiker op de knop Herstellen drukt, resulteert dit in consolefouten als de statische tekst als niet geconsolideerd wordt gemarkeerd.
* FORMS-13801: Zelfs als de component terms and conditions is uitgeschakeld, blijft het bijbehorende selectievakje ingeschakeld.
* FORMS-11952: Wanneer een formulier wordt verzonden, begint de verzendings-URL die door het formulier wordt gegenereerd met /content/ in plaats van /portale/, en wordt de aanvraag verkeerd gedraaid. Hierdoor kan de aanvraag niet op de bedoelde servers worden uitgevoerd.
* FORMS-13616: De datumkiezer geeft de huidige datum als één dag achter weer, waarschijnlijk als gevolg van een tijdzoneprobleem, en het is lastig om de juiste datumnotatie in te stellen vanwege deze inconsistentie en een extra weergavepatroon-probleem.
* FORMS-13829: De vervolgkeuzelijst, die wordt gecontroleerd door regels om de functionaliteit van keuzerondjes te simuleren, wordt niet correct gevuld nadat een selectie is gewist en opnieuw is geselecteerd. Het is de bedoeling dat afzonderlijke selectievakjes als keuzerondjes fungeren, waarbij slechts één selectie tegelijk wordt toegestaan en alle opties kunnen worden uitgeschakeld.
* FORMS-14244: In een adaptief formulier dat is gebaseerd op een XDP met ingesloten scripts in selectievakjes, worden de scripts niet uitgevoerd voor elementen na dergelijke selectievakjes.
* FORMS-14267: gebruikers ondervinden consistente time-outfouten bij het verzenden van API-aanvragen in ontwikkelings-, fase- en productieomgevingen. Deze verzoeken hebben betrekking op het genereren van PDF, soms met gegevens die vooraf zijn ingevuld met gegevensbinding. De kwestie resulteert in een hangend proces dat uiteindelijk uitstijgt maar na de fout na het opnieuw proberen slaagt.
* FORMS-11589: Voor gebruikers met alleen de AEM Forms-oplossing (zonder andere oplossingen) werkt de frontend-pijplijn niet.
* FORMS-13896: In DoR (Document of Record) worden de uitvoer, datums en getallen in het Arabisch weergegeven, ongeacht of de invoergegevens zijn samengevoegd met Gregoriaanse getallen.

### Bekende problemen {#known-issues-16357}

Geen.

### Verouderde functies en API&#39;s {#deprecated-16357}

Als u wilt weten wat er is vervangen of verwijderd in AEM as a Cloud Service, raadpleegt u [Verouderde en verwijderde functies en API&#39;s](/help/release-notes/deprecated-removed-features.md).

### Ingesloten technologieën {#embedded-tech-16357}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM | 1 62,0 | [API voor eik 1.62.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.62.0/index.html) |
| AEM SLING-API | 2.27.2. | [API voor Apache Sling API 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.22-1.4.0 | [HTML Sjabloontaalspecificaties](https://github.com/adobe/htl-spec) |
| AEM-kerncomponenten | 2,25,4 | [AEM WCM Core-componenten](https://github.com/adobe/aem-core-wcm-components) |
