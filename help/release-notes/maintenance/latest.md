---
title: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: c58e4645ddc9390728d6ac5cf92588caaeffae01
workflow-type: tm+mt
source-wordcount: '1167'
ht-degree: 0%

---


# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In het volgende gedeelte worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van Experience Manager as a Cloud Service beschreven.

## Release 23320 {#23320}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 23320 samengevat, die op 12 november 2025 openbaar werd gemaakt. De vorige onderhoudrelease werd uitgebracht in 2943.

De activering van de 2025.11.0-functie biedt de volledige functie die is ingesteld voor deze onderhoudsrelease. Zie [&#x200B; Experience Manager geeft Roadmap &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) voor meer informatie vrij.

>[!NOTE]
>
>Release 2312 is op 3 november privé gemaakt.

### Verbeteringen {#enhancements-23320}

* CQ-4361363: Nieuwste vertalingen van AEM en Granite.
* FORMS-21594: Vergrendeling van interactieve communicatiesjablooninhoud en -lay-out voor auteurs van inhoud inschakelen.
* FORMS-20385: Ondersteuning voor XDP-bewerking in de Interactive Communications Editor.
* FORMS-10883: Ondersteuning voor JSON met XHTML-naamruimtetags in DoR-generatie om ervoor te zorgen dat RTF-gegevens die via API&#39;s worden verzonden, correct worden weergegeven.
* FORMS-21751: Canvasfuncties - Tekstoverloop, UI voor pagina-einde.
* FORMS-22049: Interactive Communications Editor - Migratie naar spectrum 2.
* FORMS-22050: Ondersteuning voor dynamische paginanummering in de Interactive Communications Editor.
* FORMS-21606: Public OSGi Render SPIs voor Interactieve Mededelingen.
* FORMS-21613: Transactierapportering en prestatiesregistreren voor Render Interactive Communications SPIs.
* GRANITE-62394: Bijgewerkte joda-tijd aan 2.12.7.
* GRANITE-36205: Update Oak release to 1.8.0.
* GRANITE-62020: Verbeter het beleid voor het opnieuw proberen van `RepositoryServiceHttpClient`.
* GRANITE-62169: Werk komma-lang bij tot 3.19.0.
* SITES-35092: De Fragments van de inhoud - Nieuwe meng en verbeteringsprocedure voor semantische onderzoek.
* SITES-32319: Delivery OpenAPI - Support page references.
* SITES-20123: GraphQL: Support superscript elements in JSON response.
* SITES-34744: Nieuwe eigenschap &quot;card&quot; in de reactie Inhoudsfragment die gegevens bevat die kunnen worden gebruikt voor het weergeven van een miniatuur.
* SITES-34571: Opsommingsvelden mogen leeg zijn.
* SITES-34812: Toegevoegde mogelijkheid om een inhoudsfragment zonder verwijzingen op te halen met de parameter &quot;references&quot; met de waarde &quot;none&quot;.
* SITES-35176: Het controleren van een inhoudsfragment via Touch UI verhindert nu het uitgeven van het inhoudsfragment in de nieuwe redacteur door andere gebruikers.
* SITES-30371: Extra ondersteuning voor op uuid gebaseerde referentievelden.
* SITES-19309: haal maximaal 150 verwijzingen op wanneer u de wizard Verplaatsen pagina opent.
* SITES-32515: Edge Delivery met Universal Editor - Voeg ondersteuning toe voor meerdere velden en samengestelde meerdere velden (vroege toegang).
* SITES-33784: Edge Delivery met Universal Editor - Ondersteuning voor ld-json toevoegen in metagegevens van pagina&#39;s.
* SITES-34832: Edge Delivery met Universal Editor - Voeg een openbaar pad van een pagina toe aan het serverantwoord voor paginainformatie.
* SITES-25893: Edge Delivery met Universal Editor - Voeg ondersteuning voor sterk en benadrukt toe aan tekstrendering in blokken.
* SITES-26158: Edge Delivery met Universal Editor - Voeg ondersteuning toe voor tabelopmaak in blokken en kolommen (vroege toegang).
* SITES-27949: Edge Delivery met Universal Editor - Padtoewijzing optioneel maken.
* SITES-35811: Gebruik nieuwe index in de vragen van de Fragmenten van de Inhoud.
* SKYOPS-120857: Bestand bijwerken naar 4.1.4.
* SKYOPS-118390: Update JCR Resource aan 3.3.6.
* SKYOPS-121082: Update-versies van `org.apache.sling.discovery.standalone`-, `org.apache.sling.jcr.packageinit` - en `org.apache.sling.commons.fsclassloader` -bundels.

### Opgeloste problemen {#fixed-issues-23320}

* ASSETS-58926: Verbeter de miniatuurfunctie voor het wijzigen van video in DM.
* ASSETS-58623: Los npe in alinstanceSearch wanneer config bestaat.
* CQ-4361144: Oplossing voor het overslaan van contentfragmenten van vertaaltaken.
* CQ-4355446: Oplossing voor de niet-gelokaliseerde tekenreeks in het vertaalproject die plaatsvond in het dialoogvenster Vertaaltaak annuleren.
* CQ-4360747: Oplossing voor een probleem waarbij taken voor herhaalde vertaling te vaak lege ladingen en triggers maken.
* GRANITE-61318: Los een probleem op waarbij de wizard Pagina maken alleen verplichte velden op het basistabblad markeert.
* GRANITE-60514: Los een kwestie op waar ophield gepland publicaties tijdens volledig-stapel pijpleiding in werking stellen.
* GRANITE-61019: Probleem met GC verhelpen bij eerste uitvoering nadat AEM opnieuw is gestart.
* GRANITE-60456: Los probleem op wanneer de beheerder om het even welke bezitspagina van een gebruiker opent.
* SITES-34555: GraphQL - QueryValidationError na implementaties.
* SITES-35077: Inhoudsfragmenten - Publiceren mislukt voor fragmenten met ronde haakjes vanwege onjuiste URL-codering.
* SITES-35374: Inhoudsfragmenten - Bewerkt inhoudsfragment verdwijnt na terugnavigeren.
* SITES-36130: NPE in `EditorRestrictionsStatusImpl` .
* SITES-35810: NullPointerException in Launches block publishEdgeDeliverySubscriber queue.
* SITES-34368: AEM CIF genereert 12 GraphQL-aliassen - overschrijdt de Magento 2.4.6-P12-limiet van 10.
* SITES-36193: CCS-connectoroplossingen.
* SITES-35169: Het probleem dat een onjuiste paginering zou veroorzaken wanneer ongeldige fragmentbronnen werden geretourneerd door de zoekopdracht, is opgelost.
* SITES-34574: Oplossing voor een probleem waarbij de cursor in sommige gevallen niet zou worden geretourneerd door de zoekAPI voor inhoudsfragmenten.
* SITES-35520: Oplossing voor een probleem dat ClassCastException of timeouts veroorzaakte tijdens een poging om inhoud te publiceren.
* SITES-35210: Oplossing voor een NullPointerException die zou optreden wanneer wordt geprobeerd een verbroken fragment met een leeg referentiefilter te publiceren.
* SITES-35933: Oplossing voor een probleem dat ertoe zou leiden dat lege werkstromen &quot;Verzoek tot activering&quot; worden geactiveerd nadat het inhoudsfragment is gepubliceerd.
* SITES-35925: Het probleem met betrekking tot het patchen van modellen van inhoudsfragmenten is opgelost. Hiermee worden de eigenschappen &quot;translatable&quot; en &quot;showThumbnail&quot; uit het model verwijderd.
* SITES-35409: Het probleem waarbij aangepaste fragmenten niet opnieuw werden gepubliceerd tijdens het verplaatsen van een pagina, is opgelost.
* SITES-15757: Het probleem waarbij het opnieuw publiceren van aangepaste pagina&#39;s tijdens het verplaatsen van een pagina werd voorkomen, is opgelost.
* SITES-34638: Oplossing voor een probleem waarbij eigenschappen van bovenliggende pagina&#39;s bij het maken van nieuwe versies niet werden opgenomen.
* SITES-35071: CSV-export retourneert ongefilterde resultaten wanneer het algemene onderzoek gebruik maakt van de vermelde uitdrukking.
* SITES-32182: Edge Delivery met Universal Editor - verhelpt coderingsproblemen met URL&#39;s die al gecodeerde aanvraagparameters bevatten.
* SITES-34324: Edge Delivery met Universal Editor - repareer rendering van koppelingen met een tel:-protocol.
* SITES-35333: Edge Delivery met Universal Editor - verhelpt selectie van elementuitvoering voor afbeeldingen in metagegevens van pagina&#39;s.
* SITES-35549: Edge Delivery met Universal Editor - repareer dubbelgecodeerde HTML-entiteiten in metagegevens van pagina&#39;s.

#### AEM Guides {#guides-23320}

* GUIDEN-33597: Als een leeg `prop` -element zonder kenmerken of waarden wordt toegevoegd aan een DITAVAL-bestand, kunnen geen aanvullende `prop` -elementen worden toegevoegd.
* GUIDES-33693: Wanneer u een bewerkte afbeelding opnieuw uploadt via de gebruikersinterface van Experience Manager Guides, wordt de oorspronkelijke uitvoering van de afbeelding bijgewerkt, maar wordt de vorige versie van de afbeelding wel weergegeven door de bijbehorende DITA-inhoud.
* GUIDEN-35607: De logboeken van de fout die terwijl het uploaden van een middel via de UI van Assets of het creëren van een nieuw dossier van de interface van de Redacteur worden geproduceerd, gebruiken verkeerd de term `predecessor` in plaats van `successor` in het logboekbericht.
* GUIDEN-37649: Wanneer het publiceren van een kaart DITA gebruikend basislijn op AEM Sites (met erfeniscomponentenafbeelding), worden de kaartelementen met het attribuut `processing-role = resource-only` ook gepubliceerd.

Voor meer informatie over de nieuwe en verbeterde eigenschappen en kwesties die in de versie worden bevestigd, bekijk de [&#x200B; versie van Experience Manager Guides roadmap &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).


### Bekende problemen {#known-issues-23320}

Geen.

### Verouderde functies en API&#39;s {#deprecated-23320}

Vervangen en verwijderde eigenschappen en APIs in AEM as a Cloud Service zijn gedetailleerd in [&#x200B; Vervangen en Verwijderde Eigenschappen en APIs &#x200B;](/help/release-notes/deprecated-removed-features.md) document.

### Beveiligingsproblemen {#security-23320}

AEM as a Cloud Service is gewijd aan het optimaliseren van de beveiliging en prestaties van uw platform. Deze onderhoudrelease verhelpt 31 geïdentificeerde kwetsbaarheden en versterkt onze inzet voor robuuste systeembescherming.

### Ingesloten technologieën {#embedded-tech-23320}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM Oak | 1 88,0 | [&#x200B; Oak 1.88.0 API &#x200B;](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.88/index.html) |
| AEM SLING-API | 2,27,6 | [&#x200B; Apache Sling API 2.27.6 API &#x200B;](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTML | 1.4.28-1.4.0 | [&#x200B; Specificatie van de Taal van het Malplaatje van HTML &#x200B;](https://github.com/adobe/htl-spec) |
| Apache HTTP Server | 2,4,65 | [&#x200B; Apache Httpd 2.4.65 &#x200B;](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| AEM-kerncomponenten | 2.30.2. | [&#x200B; AEM WCM de Componenten van de Kern &#x200B;](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (standaard) | [&#x200B; Ondersteunde versies Node.js &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
