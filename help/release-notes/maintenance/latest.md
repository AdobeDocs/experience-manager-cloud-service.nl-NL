---
title: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 67b9a5f73f1f8c599e902a0ac0d8efbc614c7f75
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 1%

---


# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In het volgende gedeelte worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van Experience Manager as a Cloud Service beschreven.

## Release X {#X}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease X samengevat, die op 1 april 2025 openbaar werd gemaakt. De vorige onderhoudrelease werd uitgebracht in 19823.

De activering van de 2025.4.0-functie biedt de volledige functie die is ingesteld voor deze onderhoudrelease. Zie [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) voor meer informatie vrij.

### Verbeteringen {#enhancements-X}

FORMS-19068: Toegevoegde ondersteuning voor AEP Connector verzendt acties in Forms Manager APIs om de mogelijkheden van de de integratie van vormgegevens te verbeteren.

FORMS-18513: Implemented data tree transformation support in AEP Connector voor verbeterde wizardfunctionaliteit en mogelijkheden voor gegevensverwerking.

FORMS-18432: Geïmplementeerde vorm-specifieke (op regex-Gebaseerde) cliënt-zijconfiguratie om selectieve prefill functionaliteit zonder op OSGI-niveau veranderingen toe te laten.

FORMS-17551: ondersteuning voor Document of Record (DoR) toegevoegd voor integratie van SharePoint-lijsten.

### Opgeloste problemen {#fixed-issues-X}

FORMS-19028: vooraf ingevulde functionaliteit op de client verbreekt de afhandeling van gebeurtenissen, zodat Value commit en DOMContentLoaded gebeurtenissen niet correct worden uitgevoerd tijdens het laden van het formulier.

FORMS-18360: Verbeterd SharePoint-lijstbereikbeheer voor teamsites in Forms Document Management om de gegevensorganisatie en toegangscontrole te verbeteren.

FORMS-18325: Adobe Experience Platform (AEP) Cloud-configuratie toegevoegd om de integratie en verwerkingsmogelijkheden van formuliergegevens te verbeteren.

FORMS-18213: Geïmplementeerde functionaliteit om uitgeschakelde velden te verbergen/uit te sluiten van Document of Record (DoR) om de documenthelderheid en gebruikerservaring te verbeteren.

FORMS-18189: Gewijzigde afhandeling van aangepaste functies om foutregistratie voor lege clientbibliotheken te voorkomen en de weergave van fouten in de gebruikersinterface te verbeteren.

FORMS-18426: De opzoekfunctionaliteit van de SharePoint-lijst mislukt wanneer lijstnamen speciale tekens bevatten (bijvoorbeeld &#39;-&#39;), wat van invloed is op de formulierintegratie met SharePoint-lijsten.

FORMS-18375: Op basis van stichtingscomponenten gebaseerde formulieren selecteren ten onrechte recaptcha-configuraties in de map `conf/global` als er geen specifieke configuratiecontainer is geselecteerd.

FORMS-18304: PDF/A-1b-documenten die validatie doorgeven in Acrobat en LiveCycle ES4, worden in AEM 6.5 Forms onjuist gemarkeerd als niet-compatibel vanwege apparaatafhankelijke kleurfouten.

FORMS-18271: In de Forms Thema Editor worden niet-gelokaliseerde foutberichten weergegeven die van invloed zijn op de gebruikerservaring in de formulierconfiguratie en de aanpassing van thema&#39;s.

FORMS-18068: Vette problemen met het renderen van tekst in Document of Record (DoR) voor groepen keuzerondjes en selectievakjes die RTF-velden gebruiken.

FORMS-7016: De volgorde van toetsenbordfocus in de formuliereditor volgt de logische navigatie niet.

FORMS-6950: Toegevoegde vereiste ARIA-rollen en -kenmerken aan de controlecomponenten van het dossiersysteem navigator om de toegankelijkheid van de schermlezer te verbeteren en te voldoen aan WCAG 4.1.2 Naam, Rol, Waarde (Niveau A) norm.

### Bekende problemen {#known-issues-X}

Geen.

### Verouderde functies en API&#39;s {#deprecated-X}

Vervangen en verwijderde eigenschappen en APIs in AEM as a Cloud Service zijn gedetailleerd in [ Vervangen en Verwijderde Eigenschappen en APIs ](/help/release-notes/deprecated-removed-features.md) document.

### Beveiligingsproblemen {#security-X}

AEM as a Cloud Service is gewijd aan het optimaliseren van de beveiliging en prestaties van uw platform. Deze onderhoudrelease verhelpt geïdentificeerde kwetsbaarheden van X en versterkt onze inzet voor robuuste systeembescherming.

### Ingesloten technologieën {#embedded-tech-X}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM Oak | 1 76,0 | [ Oak API 1.76.0 ](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.76.0/index.html) |
| AEM SLING-API | 2,27,6 | [ Apache Sling API 2.27.6 API ](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTML | 1.4.26-1.4.0 | [ Specificatie van de Taal van het Malplaatje van HTML ](https://github.com/adobe/htl-spec) |
| AEM-kerncomponenten | 2 27,0 | [ AEM WCM de Componenten van de Kern ](https://github.com/adobe/aem-core-wcm-components) |
