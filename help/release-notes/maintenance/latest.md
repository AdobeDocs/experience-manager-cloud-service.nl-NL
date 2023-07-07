---
title: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 1251f36ece4449d8be6a40f34421351161bf3b23
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 0%

---

# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In de volgende sectie worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van as a Cloud Service Experience Manager beschreven.

## Release 12549 {#release-12549}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 12549 samengevat, die op 4 juli 2023 openbaar werd gemaakt. Deze onderhoudrelease is een update van eerdere onderhoudrelease 12255. Onderhoudsversie 12549 vervangt versie 12441 om twee problemen op te lossen.

2023.7.0 Activering van de functie biedt de volledige functie die is ingesteld voor deze onderhoudsrelease. Zie de [Experience Manager geeft Routekaart vrij](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html) voor meer informatie .

### Verbeteringen {#enhancements-12549}

- Forms-5054: Toegevoegde ondersteuning voor alle [beelden](https://opensource.adobe.com/acrobat-sign/acrobat_sign_events/webhookeventsagreements.html) ondersteund door Adobe Sign.

### Opgeloste problemen {#fixed-issues-12549}

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

### Bekende problemen {#known-issues-12549}

- SKYOPS-61385: Met de meest recente update voor de dispatcher zijn bepaalde ongeldige reguliere expressies die eerder stilzwijgend werden genegeerd door `libpcre1` worden niet meer geaccepteerd door de bijgewerkte `libpcre2` tijdens de implementatie. De de configuratiecontrole van de verzender zal spoedig worden bijgewerkt om deze ook vroeger te identificeren.

### Ingesloten technologieën {#embedded-tech-12549}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM OAK | 1,50-T20230405052634-f9df4aa | [API 1.50.0 voor ongewenste API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.50.0/index.html) |
| AEM SLING-API | Versie 2.27.0 | [API voor Apache Sling API 2.27.0](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Versie 1.4.20-1.4.0 | [HTML Sjabloontaalspecificaties](https://github.com/adobe/htl-spec) |
| AEM-kerncomponenten | Versie 2.23.0 | [AEM WCM Core-componenten](https://github.com/adobe/aem-core-wcm-components) |
