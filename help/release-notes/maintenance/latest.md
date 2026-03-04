---
title: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 4b05f571904384521b79dbaf0fa5f4a3a75fef2b
workflow-type: tm+mt
source-wordcount: '1561'
ht-degree: 0%

---


# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In het volgende gedeelte worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van Experience Manager as a Cloud Service beschreven.

## Release 24678 {#release-24678}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 24678 samengevat, die op 4 maart 2026 openbaar werd gemaakt. De vorige onderhoudsrelease was release 24464.

De activering van de 2026.3.0-functie biedt de volledige functionaliteit die is ingesteld voor deze onderhoudsrelease. Zie [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) voor meer informatie vrij.

### Verbeteringen {#enhancements-24678}

* FORMS-18927: extra ondersteuning voor aangepaste MIME-typen en bestandsextensies in de AEM Forms-component Bestandsbijlage, waarmee gebruikers een groter aantal verschillende documenttypen kunnen toevoegen.
* FORMS-18211, FORMS-22936: gebruikers hebben een toegankelijkheidsprobleem ervaren waarbij selectievakjes niet correct zijn gegroepeerd in een `<fieldset>` -element, waarbij het groepslabel niet in een `<legend>` is genest als eerste onderliggend item. Dit betrof gebruikers met een handicap die voor navigatie op schermlezers vertrouwen. Op Adaptive Forms gebaseerde Core Components heeft nu ondersteuning voor veldsets en legenda geïntroduceerd om betere toegankelijkheidsondersteuning te bieden.
De optie Veldset toegevoegd in het deelvenster waarmee gebruikers gerelateerde velden effectiever kunnen indelen en groeperen in hun formulieren.
* FORMS-23880: Toegevoegde ondersteuning voor Thema-editor in kerncomponenten. Dankzij deze uitbreiding kunnen gebruikers thema&#39;s binnen de kerncomponenten efficiënter aanpassen en beheren, waardoor hun ontwerpflexibiliteit en -workflow worden verbeterd.
* FORMS-21772: Added versioning support to Forms Management UI. Dankzij deze uitbreiding kunnen gebruikers versies maken en ophalen voor zowel Core Components (Basiscomponenten) als Foundation Components based Adaptive Forms, Form Fragments, Thema&#39;s en Binary Assets, waardoor middelenbeheer en versiebeheer worden verbeterd.
* FORMS-23094: toegevoegd client-side parsering voor Foundation Components based Adaptive Forms, waarmee zakelijke klanten hun formulieren naar de cloud kunnen migreren. Deze verbetering steunt eigenschappen EcmaScript in de code-redacteursregels, die eerder niet werden gesteund, die een vlotter migratieproces vergemakkelijken.
* FORMS-23853: extra ondersteuning voor het overschrijven van reCAPTCHA in de component sling. Dankzij deze uitbreiding kunnen gebruikers de reCAPTCHA-instellingen aanpassen, waardoor de flexibiliteit en beveiliging voor zakelijke klanten worden verbeterd.
* SITES-34936: Edge Delivery met Universal Editor: Voeg filtercontentfragmenten per model toe voor publicatie.
* SITES-36203: Edge Delivery met Universal Editor: codeschakeloptie toevoegen om ondersteuning voor meerdere velden en samengestelde multivelden in te schakelen.
* SITES-37037: Edge Delivery met Universal Editor: verbeter het importeren van spreadsheets om het scheidingsteken automatisch te detecteren.
* SITES-37804: Edge Delivery met Universal Editor: voeg ondersteuning toe voor Gesloten gebruikersgroepauteurs (Vroege toegang).
* SITES-38990: Edge Delivery met Universal Editor: voeg ondersteuning voor uitsluitingen toe aan padtoewijzingen.
* SITES-39171: Edge Delivery met Universal Editor: voeg ondersteuning voor `cq:tags` toe in blokken en blokitems.
* SITES-40042: Edge Delivery met Universele Redacteur: maak de Dienst Config het gebrek voor nieuwe plaatsen.
* SITES-37649: GraphQL: Ondersteuning voor filteren van meerdere tekstvelden op JCR-niveau.
* SITES-37843: GraphQL: Filteren voor multivalue-velden (verzamelingen) wordt niet ondersteund op JCR-niveau.
* SITES-37540: Vervangen en vervangenAlle bewerkingen voor CF-veldwaarden (zoeken en vervangen voor een bepaalde veldnaam).
* SITES-37741: Voeg de eigenschap &quot;card&quot; toe in de reactie van de get fragmentvariatie (kaartweergave in de interface van Admin).
* SITES-37754: Publiceer map via API: structuurvalidatie op aanvraag als `validateReferences` is ingesteld op true.
* SITES-37756: Geef statusinformatie voor het in- en uitchecken van een inhoudsfragment weer.
* SITES-37805: Schema-update: GEWIJZIGDE fragmenten kunnen niet worden hernoemd/verplaatst (documentatie).
* SITES-37847: Verbeterde prestaties voor SQL-2-query van Lent Content ReferenceProvider (LentContent ophalen).
* SITES-39255: Update OpenAPI-implementatie naar recente Java API-wijzigingen voor Composite-veld.
* SITES-37096: Verwijder de consolevertraging van Lanceringen wanneer de orphaned knopen aanwezig zijn.
* SITES-38117: Vind een manier om kindlanceringen zonder prestatieseffect te vragen.
* SITES-38317: Voeg gebruiker toe die aan meta-gegevens (daadwerkelijke gebruiker in plaats van generisch begon wanneer looppas door de dienstgebruiker) begon.
* SITES-39203: De gebruiker van de vertoning die werkschema (in plaats van generische gebruiker begon wanneer looppas door de dienstgebruiker) begon.
* SITES-13083: Foutopdrachten lokaliseren in Sites > dialoogvenster voor het maken van Live Copy.
* SITES-13389: Lokaliseer &quot;Gemaakt versie van ... voordat u de opstartreeks promoot&quot; in Sites > Tijdlijn.
* SITES-16176: Lokaliseer tekenreeksen in de redacteur van de Pagina > de component van het Beeld v3 vormt dialoog.
* SITES-35702: Niet-gelokaliseerde tekenreeks &quot;Live kopie up-to-date met beperkte overerving&quot; op het tabblad &quot;Overzicht van live kopie&quot;.
* SITES-35748: Niet-gelokaliseerde keuzelijst Selectie van productvariabele inschakelen in &#39;Content Fragment Model Editor&#39;.
* SITES-35750: Niet-gelokaliseerde tijdelijke aanduiding voor &quot;Product-SKU(&#39;s) gescheiden door `#` teken&quot; in invoerveld in &quot;Content Fragment Model Editor&quot;.
* SITES-37113: Niet-gelokaliseerd dialoogvenster Overerving annuleren op het tabblad &quot;CIF Configurations&quot;.
* SITES-25240: Accessibility fix for teaser modal call to action.
* SITES-25531: Toegankelijkheidscorrectie voor kleurcontrast in zoekmodaal.
* SITES-37115: Afgebroken pictogrammen in de Vienia demo store.

### Opgeloste problemen {#fixed-issues-24678}

* CQ-4361552: Fixed i18n JSON dictionary preserve HTML-escapode in import translations.
* CQ-4361634: Vaste-Erviteitsfragmenten niet selecteerbaar of toegevoegd aan vertaalproject.
* CQ-4362072: Vaste AEMaaCS-omzettingsworkflow - DE > ES-stap kan geen pagina toevoegen aan vertaalproject.
* FORMS-23741: Gebruikers ondervonden problemen waarbij de stappen InvokeDDX en Asset Upload niet trapsgewijs werden uitgevoerd, waardoor twee afzonderlijke workflowuitvoeringen nodig waren. Dit beïnvloedde de productieomgeving gebruikend AEM as a Cloud Service met de Plaatsen en toe:voegen-on van Forms.
* FORMS-23877: gebruikers ondervonden problemen met aangepaste functies die niet tijdens runtime werden geladen wanneer ze formulieren rechtstreeks binnen Sites-pagina&#39;s maakten met een oudere versie van Core Components.
* FORMS-24038: Gebruikers ondervonden problemen met de navigatieknop toen er dynamisch meer tabbladen werden toegevoegd.
* FORMS-23721: Probleem verholpen waarbij validatiepatronen die waren geconfigureerd voor tekstinvoer in het dialoogvenster Bewerken niet werden voortgezet. Eerder werd de patroonwaarde opgeslagen, maar niet behouden of weergegeven in de gebruikersinterface. Dit heeft tot verwarring geleid voor auteurs van formulieren.
* FORMS-23456: gebruikers hebben onjuiste aankondigingen van schermlezers op mobiele apparaten ervaren voor verborgen koptekstrijen in een tabel bij gebruik van de component Tabel in Adaptief Forms. Een verborgen tabelkoptekst is buiten de context aangekondigd, waardoor gebruikers die op iOS VoiceOver en Android TalkBack vertrouwen, in verwarring raken.
* FORMS-23454: Gebruikers ondervonden problemen met de Date Picker for Core Components based Adaptive Forms. Bij het invoeren van ongeldige datums zou het systeem automatisch corrigeren naar mogelijk gesloten datums.
* FORMS-23117: Gebruikers hadden ervaring met hCaptcha die niet correct werd vertaald in Foundation Components based Adaptive Forms.
* FORMS-22634: gebruikers ondervonden een probleem waarbij e-mailbijlagen niet werden opgenomen wanneer de opties &quot;Include Attachment&quot; en &quot;Use HTML template&quot; samen werden gebruikt.
* FORMS-23288: Gebruikers ondervonden problemen met Adaptive Forms die zijn ingesloten in de modaliteiten voor het delen van bedrijfsmiddelen. Het formulier kan niet correct worden geladen wanneer de URL `.html` in het middelste pad bevatte.
* FORMS-19198: gebruikers hebben 404 fouten ervaren bij het insluiten van formulieren volgens de regels van de verzender. De fouten kwamen voor URLs zoals /etc.clientlibs/toggles.json, rumbibliotheek, en analyticsparserconfigparser.json voor, toe te schrijven aan URL rewriter die deze URLs niet kan herschrijven.
* SITES-33799: Edge Delivery met Universal Editor: Fix optimized video rendition not published.
* SITES-35082: Edge Delivery met Universal Editor: verwijder lege alinea&#39;s, regeleinden en regeleinden uit richtexts.
* SITES-35524: Edge Delivery met Universal Editor: repareer mislukte publicatie voor paden die niet-ASCII speciale tekens bevatten.
* SITES-38647: Edge Delivery met Universal Editor: verhelpen prestatieknelpunten op omgevingen met veel sites.
* SITES-40521: Edge Delivery with Universal Editor: Fix duplicate class names for Blocks and Block Items.
* SITES-37887: GraphQL: UUID-zoekopdrachten voor grotere resultaatsets kunnen leiden tot langere responstijden.
* SITES-38412: Kan fragmenten niet repareren tijdens het starten wanneer er een uniek veld/witruimte bestaat (unieke beperking sluit nu CF&#39;s in opstarters uit).
* SITES-38606: Validatiefout bij het toevoegen van variatie aan CF met fragmentverwijzing UUID (hydrate CFs referenced door uuid in variaties).
* SITES-39489: Assets UI die fragmenten van cq :discarded omslagen toont (soft-deleted CFs wordt verwijderd uit Beheer API reacties).
* SITES-39517: GET CF met samengesteld veld dat opsomming bevat, mislukt met 500-fout.
* SITES-40072: Samengestelde velden met tabs retourneren lege plaatsaanduidingswaarden.
* SITES-39575: Met Live Copy opslaan wordt `cq:rolloutConfigs` verwijderd. De rollout-configuratie gaat verloren.
* SITES-39694: Productie-rollouts ontbreken met NPE.
* SITES-39761: NavigationItem.getLink() retourneert null in CIF v2 Navigation-component.
* SITES-40519: De rollout MSM ontbreekt met NullPointerException wanneer het levende-exemplaardoelmiddel ongeldig is.
* SITES-17531: Gehardcodeerde tekenreeks voor &#39;&#39;Smart crop preview&#39;&#39; in de Pagina-editor > Afbeelding > Slim uitsnijden.
* SITES-31575: De knopinfo met informatie is niet volledig zichtbaar in Pagina-editor > Carousel-component > Eigenschappen.
* SITES-34215: De Autocomplete component JS heft directe bevestigingsfout op vereist pathfield op dialooglusje op.
* SITES-35218: sommige AEM Core-componenten geven de lege alt-tag niet correct weer.
* SITES-37114: De knopinfo &quot;Ondersteuning voor Catalog UID inschakelen&quot; op het tabblad &quot;CIF Configurations&quot; is ingekort.
* SITES-36138: Query zonder index gedetecteerd (incident).
* SITES-37682: Inhoudstype overschrijven in `/libs/cq/Page/Page.css.jsp` en `/libs/cq/Page/Page.js.jsp.`
* SITES-38709: Klassieke UI-tekst RTE laat onbewerkte HTML zien na upgrade naar 6.5.24.
* SITES-39630: updates van geneste inhoudsfragmenten worden niet weerspiegeld in geëxporteerde doelaanbiedingen.
* SITES-39696: Aan/uit-tijd voor het plannen van activering/deactivering werkt niet.
* SITES-39824: Exporting Experience Fragments aan Adobe Target keert 500 (NPE) terug.
* SITES-40253: Periodieke 500 Fouten bij `/bin/cif/invalidate-cache` - Oak-conflicten onder `/var/cif/cacheinvalidation` .
* SITES-40341: Fix base64 inline images in styles tag in `HtmlToJsonConvertorImpl` .

### Bekende problemen {#known-issues-24678}

Geen.

### Verouderde functies en API&#39;s {#deprecated-24678}

Vervangen en verwijderde eigenschappen en APIs in AEM as a Cloud Service zijn gedetailleerd in [ Vervangen en Verwijderde Eigenschappen en APIs ](/help/release-notes/deprecated-removed-features.md) document.

### Beveiligingsproblemen {#security-24678}

AEM as a Cloud Service is gewijd aan het optimaliseren van de beveiliging en prestaties van uw platform. Deze onderhoudrelease verhelpt 15 geïdentificeerde kwetsbaarheden en versterkt onze inzet voor robuuste systeembescherming.

### Ingesloten technologieën {#embedded-tech-24678}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM Oak | 1 90,0 | [ Oak 1.90.0 API ](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.90.0/index.html) |
| AEM SLING-API | 2,27,6 | [ Apache Sling API 2.27.6 API ](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTML | 1.4.28-1.4.0 | [ Specificatie van de Taal van het Malplaatje van HTML ](https://github.com/adobe/htl-spec) |
| Apache HTTP Server | 2,4,65 | [ Apache Httpd 2.4.65 ](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| AEM-kerncomponenten | 2.30.4. | [ AEM WCM de Componenten van de Kern ](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (standaard) | [ Ondersteunde versies Node.js ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |

