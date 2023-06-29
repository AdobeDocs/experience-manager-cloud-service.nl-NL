---
title: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: e8ea040ba3f8c73d7ed64c9669ac1d0a22d3a3c8
workflow-type: tm+mt
source-wordcount: '600'
ht-degree: 1%

---

# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In de volgende sectie worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van as a Cloud Service Experience Manager beschreven.

## Release 12441 {#release-12441}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 12441 samengevat, die op 27 juni 2023 openbaar werd gemaakt. Deze onderhoudrelease is een update van eerdere onderhoudrelease 12255.

2023.7.0 Activering van de functie biedt de volledige functie die is ingesteld voor deze onderhoudsrelease. Zie de [Experience Manager geeft Routekaart vrij](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html) voor meer informatie .

### Verbeteringen {#enhancements-12441}

- SITES-8769: StijlImpl-aanroepen in ResponsiveGrid verbeteren
- Forms-5054: Toegevoegde ondersteuning voor alle [beelden](https://opensource.adobe.com/acrobat-sign/acrobat_sign_events/webhookeventsagreements.html) ondersteund door Adobe Sign.

### Opgeloste problemen {#fixed-issues-12441}

- Verschillende updates met betrekking tot toegankelijkheid
- SITES-12688: Pagina-editor: Logische operator OF werkt niet correct in zoekopdracht met Asset Finder
- SITES-4951: Pagina-editor: Bij zoeken met tags in paginaeditor worden geen subtags gevonden
- SITES-12465: Geniet van fragmenten: Pijltoetsen werken niet in het dialoogvenster Experience-fragmentcomponent
- SITES-12893: Geniet van fragmenten: Cirkelverwijzingsvalidatie toepassen voor ervaringsfragmenten
- SITES-12715: Geniet van fragmenten: Cloud-serviceconfiguraties die zijn toegepast op de map Experience fragments blijven niet behouden
- SITES-13097: Geniet van fragmenten: Kan ervaringsfragmenten niet toevoegen aan een vertaalproject
- SITES-13165: GraphQL: Standaardgedrag voor filteren van null-waarden herstellen
- SITES-12577: Koppelingencontrole: Transformer not rewriting links
- SITES-13559: MSM: &#39;Is niet wijzigbaar&#39;-uitzondering gegenereerd bij uitrollen van onderdeel
- SITES-11757: MSM: Inherit rollout configuration from Parent wordt not reverback for child pages
- SITES-14073: Sites-beheerder: CSV-rapport mislukt bij 500 wanneer u geen eigenschap selecteert om te exporteren
- Forms-7648: Kan maximum aantal cijfers in een component Numeriek vak niet valideren. Het validatiescript werkt niet.
- Forms-8177: Wanneer de Forms-service actief is, wordt `com.adobe.aem.formsndocuments.publish.AssetReferenceProvider Failed to retrieve asset dependencies` foutmeldingen.
- Forms-8300: Wanneer een gebruiker probeert om een taak te delegeren na het openen van het, herlaadt de afgevaardigde reactie de taak, in plaats van het openen van AEM Inbox UI van de gebruiker.
- Forms-8500: In Microsoft® Edge-browser met de optie IE-modus ingeschakeld, kan HTML5 Forms niet worden geopend.
- Forms-8541: Bij het renderen van een adaptieve Forms treedt een uitzondering op bij Null-aanwijzer.
- Forms-8964: Wanneer een formulier wordt geopend op een Android™-apparaat op Google Chrome of Mozilla Firefox, kan de tekst die is ingevoerd in de component Tekstvak niet worden verwijderd.
- Forms-9026: Wanneer een gebruiker een adaptief formulier maakt op basis van een complex en geldig JSON-schema, gerelateerde JSON-schemavelden naar de Adaptive Forms Editor sleept om adaptieve Forms-velden te maken en het venster Adaptive Forms Editor vernieuwt, worden alle velden verwijderd en wordt de Adaptive Forms-editor leeg weergegeven.
- Forms-9263: Wanneer de weergavetekst van een optie voor selectievakjes een speciaal teken bevat, kunnen gebruikers dergelijke selectievakjes niet selecteren.
- Forms-8668: Tijdens het weergeven van een voorbeeld van een PDF van een formulier worden enkele niet-vereiste Java™-stackdumps weergegeven in de foutlogboeken. Er zijn echter geen problemen met de weergave van het formulier.
- Forms-8116: Wanneer regels worden toegepast op de adaptieve Forms Container-component, worden de toegepaste regels niet opgeslagen.
- Forms-7906: Wanneer een adaptief formulier wordt toegevoegd aan een AEM Sites Container-component, kan de regeleditor niet worden geopend.
- Forms-8846: De eigenschap Bind reference werkt niet voor de component Adaptive Forms attachments.
- Forms-9072: Als u een schema doorzoekt terwijl u een formulierfragment maakt, retourneert het zoekresultaat geen schema voor selectie.
- Forms: Oplossing voor problemen met betrekking tot toegankelijkheid om de toegankelijkheid van AEM Forms-functies te verbeteren.

### Bekende problemen {#known-issues-12441}

Geen.

### Ingesloten technologieën {#embedded-tech-12441}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM OAK | 1,50-T20230405052634-f9df4aa | [API 1.50.0 voor ongewenste API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.50.0/index.html) |
| AEM SLING-API | Versie 2.27.0 | [API voor Apache Sling API 2.27.0](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Versie 1.4.20-1.4.0 | [HTML Sjabloontaalspecificaties](https://github.com/adobe/htl-spec) |
| AEM-kerncomponenten | Versie 2.23.0 | [AEM WCM Core-componenten](https://github.com/adobe/aem-core-wcm-components) |
