---
title: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: d73ccc454c89c7e06752de694af97ac26694be17
workflow-type: tm+mt
source-wordcount: '902'
ht-degree: 0%

---


# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In het volgende gedeelte worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van Experience Manager as a Cloud Service beschreven.

## Release 22450 {#22450}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 22450 samengevat, die op 16 september 2025 openbaar werd gemaakt. De vorige onderhoudsrelease was release 22171.

De activering van de 2025.9.0-functie biedt de volledige functie die is ingesteld voor deze onderhoudrelease. Zie [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/nl/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) voor meer informatie vrij.

### Nieuwe functies {#new-features-22450}

* SITES-32595: Workflows die met overgeslagen of geweigerde fragmenten zijn voltooid, kunnen nu worden geïdentificeerd. Er is een nieuwe eigenschap beschikbaar in de API-reactie voor de workflow. Deze bevat een lijst met fragmenten die zijn uitgesloten omdat ze ongeldig zijn of omdat ze ongeldige referenties hebben.
* SITES-33642: Er wordt nu een nieuwe API-gebeurtenis gemaakt en gebruikt voor gewijzigde Content Fragments.
* SITES-33320: Het is nu mogelijk om naar een Model van het Fragment van de Inhoud te zoeken gebruikend zijn `technicalName` via het Onderzoek API.

### Verbeteringen {#enhancements-22450}

* SITES-34023: Het veld `technicalName` is toegevoegd aan de antwoorden van de eindpunten van het Content Fragment Model voor betere identificatie.
* SITES-32766: De verwijzingen naar inhoudselementen in Content Fragment Models ondersteunen nu een groter aantal binaire bestandstypen.
* SITES-33974: Verbeterde OpenAPI-documentatie waardoor deze nauwkeuriger en gebruiksvriendelijker wordt.
* SITES-9173: Cache `ContentPolicyStatus`.
* SITES-9290: Verbeter caching van `TouchEditContext`.
* SITES-33355: Open nieuwe CF-editor op &quot;View payload&quot; in workflowconsole.
* SITES-33356: Open nieuwe CF-editor bij Maken CF → Openen in TouchUI-beheerinterface.
* SITES-32952: Inconsistente verwerking van standaardwaarden voor CFM-velden bij gebruik van API voor levering.
* SITES-31539: Edge Delivery met Universal Editor: voeg ondersteuning voor de metatags voor de configuratie van Universal Editor toe in `head.html` .
* SITES-20672: Edge Delivery met Universal Editor: voeg ondersteuning toe voor extra spreadsheets met bulkmetagegevens in ontwerpomgeving.
* SITES-32963: Edge Delivery met Universal Editor: voeg nieuwe metagegevens voor experimenten toe voor het optimaliseren van het doel, de automatische toewijzing en het zelfstudie.
* SITES-30847: Release Core Components 2.30.0.
* SITES-29617: Het referencedBy eindpunt is bijgewerkt om de klasse te gebruiken ReferenceSearch, verbeterend zijn prestaties en betrouwbaarheid.
* SITES-19308: Verbeterde prestaties van het verwijderingsproces van pagina&#39;s door de stap voor verwijzingsvalidatie te optimaliseren.
* SITES-34293: Implemented lazy loading for templated resources to improve performance.
* SITES-33892: Er is een functieschakeloptie toegevoegd om referentiecontroles voor pseudo-pagina&#39;s over te slaan, die de prestaties kunnen verbeteren.

### Opgeloste problemen {#fixed-issues-22450}

* CQ-4360550: Oplossing voor een onverwachte verdwijning van het taalexemplaar na het omkeren van de paginabeweging in AEM Cloud Service.
* SITES-25232: De vastgestelde verbindingen van de Tijdverdraaiing van de Datum en van de Uitgang hebben geen zichtbare nadrukindicator.
* SITES-25258: Focus wordt niet beheerd met het modale dialoogvenster Annotatie verwijderen.
* SITES-25305: De demografische werkbalk krijgt geen focus in een logische volgorde.
* SITES-25366: De laadstatus van het tasermodaal wordt niet aangekondigd door de schermlezer.
* SITES-34276: Edge Delivery met Universal Editor: repareer automatisch gemaakt CORS-beleid dat niet wordt toegepast op publicatielaag.
* SITES-34811: Edge Delivery met Universal Editor: repareer de hlx-kiezer die niet wordt toegevoegd aan koppelingen naar spreadsheets in ontwerp.
* SITES-31669: Niet-gelokaliseerde tekenreeksen &quot;Deze pagina wordt omgeleid naar&quot; in Gereedschappen > Sites > Starten.
* SITES-30879: Niet-gelokaliseerde tekenreeksen in Sites > Pagina-editor > component Zoeken.
* SITES-30959: Niet-gelokaliseerde tekenreeksen in Pagina-editor > Afbeeldingscomponent.
* SITES-21743: Niet-gelokaliseerd &quot;Selecteer een document dat u wilt weergeven.&quot; string in Page Editor > PDF Viewer
* SITES-19785: Tekenreeksen worden ontgrendeld op de site Core Components > Tabs.
* SITES-22059: Niet-gelokaliseerde tekenreeks &quot;File preview not available&quot; in Core Components site > PDF Viewer.
* SITES-33360: Niet-gelokaliseerde &quot;Fout tijdens verrichting. Opgegeven pad is geen starttekenreeks in Launches > Bewerken.
* SITES-32975: Niet-gelokaliseerde datumnotatie in Headless UI > Launches > Compare Launch to Source.
* SITES-32973: Hardcoded strings in Headless UI > Launches > Rebase.
* SITES-13540: Niet-gelokaliseerde tekenreeksen in Launches > Promotie.
* SITES-13085: Niet-gelokaliseerde foutberichten in Sites > Aanmaakpagina starten.
* SITES-21499: Niet-gelokaliseerde tekenreeks is Sites > Launches > Edit.
* SITES-14961: Truncation of date field in Sites > Properties > Blueprint > Rollout dialog.
* SITES-33764: Launch filters (Source Path/Workflow-created Launches) werkt niet.
* SITES-33884: &quot;Promote huidige pagina en subpagina&#39;s&quot;bevordert onbedoeld pagina&#39;s buiten het werkingsgebied.
* SITES-33611: Live copy overview werkt niet voor markten met veel volumes.
* SITES-34331: 503 Time-out bij laden van implementatieoverlay voor gebruikers die geen beheerder zijn.
* SITES-34403: `NullPointerException` in `GraphqlClientImpl deactivate()` tijdens afsluiten.
* SITES-33817: Oplossing voor synchronisatieproblemen tussen het schema UI en het model JCR om consistentie te verzekeren.
* SITES-31141: Inhoudsreferenties die niet via pad worden vertegenwoordigd, worden nu correct geretourneerd in de API-reactie.
* SITES-34080: Het maken van inhoudsfragmenten is nu robuuster en mislukt niet als er geen velden naar het verzoek zijn gestuurd.
* SITES-30773: De reguliere expressie voor het zoeken naar woorden met &quot;Zoeken en vervangen&quot; is verbeterd en komt nu overeen met UTF-8-tekens.
* SITES-33742: Het volgende probleem is opgelost: een fout die het verplaatsen van een inhoudsfragment tijdens het gebruik van de workflow-API heeft verhinderd.

### Bekende problemen {#known-issues-22450}

Geen.

### Verouderde functies en API&#39;s {#deprecated-22450}

Vervangen en verwijderde eigenschappen en APIs in AEM as a Cloud Service zijn gedetailleerd in [ Vervangen en Verwijderde Eigenschappen en APIs ](/help/release-notes/deprecated-removed-features.md) document.

### Beveiligingsproblemen {#security-22450}

AEM as a Cloud Service is gewijd aan het optimaliseren van de beveiliging en prestaties van uw platform. Deze onderhoudrelease verhelpt 18 geïdentificeerde kwetsbaarheden en versterkt onze inzet voor robuuste systeembescherming.

### Ingesloten technologieën {#embedded-tech-22450}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM Oak | 1 84,0 | [ Oak API 1.84.0 ](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.84/index.html) |
| AEM SLING-API | 2,27,6 | [ Apache Sling API 2.27.6 API ](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTML | 1.4.28-1.4.0 | [ Specificatie van de Taal van het Malplaatje van HTML ](https://github.com/adobe/htl-spec) |
| Apache HTTP Server | 2,4,65 | [ Apache Httpd 2.4.65 ](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| AEM-kerncomponenten | 2 29,0 | [ AEM WCM de Componenten van de Kern ](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (standaard) | [ Ondersteunde versies Node.js ](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
