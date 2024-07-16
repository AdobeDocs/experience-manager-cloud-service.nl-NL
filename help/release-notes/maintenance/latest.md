---
title: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 573de431328650778b3ef0979a24190477382310
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 1%

---


# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In het volgende gedeelte worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van Experience Manager as a Cloud Service beschreven.

## Release 17098 {#release-17098}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 17098 samengevat, die op 16 juli 2024 openbaar werd gemaakt. De vorige onderhoudsrelease was release 16971.

De activering van de 2024.7.0-functie biedt de volledige functionaliteit die is ingesteld voor deze onderhoudsrelease. Zie de [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) voor meer informatie vrij.

### Verbeteringen {#enhancements-17098}

- SKYOPS-79817: Laat de Taak van de Analysator van de Eigenschap van de Verkoop voor de Toewijzingen van de Gebruiker van de Dienst toe

### Opgeloste problemen {#fixed-issues-17098}

- ASSETS-39665: Smart Crops Sync werkt niet na migratie van 6.5 naar AEMCS
- FORMS-14993: Forms API retourneert 500 voor het eerder gebruikte onderpand
- GRANITE-52120: CRXDE die 500 terugkeren wanneer het tonen van de gegevens van het Toegangsbeheer
- GRANITE-52573: Verzoeken die 400 retourneren bij gebruik van // in opnieuw geschreven URL&#39;s
- GRANITE-52746: Alle knooppunttypen die niet zijn geladen in het dialoogvenster Knooppunt maken
- GRANITE-52777: Gebroken behandeling van 404s wanneer het verzoek is verpakt
- GRANITE-52871: Zorg ervoor dat de publicatiewerker wordt gesynchroniseerd met gouden publicatie en wordt voltooid vóór de compactie
- SKYOPS-79173: Replicator die niet aan veelvoudige agenten herhaalt die een bepaalde AgentIdFilter aanpassen
- SKYOPS-80075: Problemen met Umlauts in namen van bedrijfsmiddelen die de Blockage van de Gepubliceerde Rij (Mac) veroorzaken
- SKYOPS-81032: Filter uit logboeken die door verzoeken worden geproduceerd om logboeken te krijgen wanneer het gebruiken van Verbeterde het Registreren

### Bekende problemen {#known-issues-17098}

Geen

### Kennisgeving wijzigen {#change-notice-17098}

- Vanaf september 2024 zal AEM as a Cloud Service de serialisatie van Resolvers van Middel via het Sling ModelExporter kader onbruikbaar maken. Zie [ de documentatie ](/help/implementing/developing/hybrid/disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter.md) voor meer details.

### Verouderde functies en API&#39;s {#deprecated-17098}

Vervangen en verwijderde eigenschappen en APIs in AEM as a Cloud Service zijn gedetailleerd in [ Vervangen en Verwijderde Eigenschappen en APIs ](/help/release-notes/deprecated-removed-features.md) document.

### Ingesloten technologieën {#embedded-tech-17098}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM Oak | 1 66,0 | [ Oak API 1.66.0 ](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.66.0/index.html) |
| AEM SLING-API | 2.27.2. | [ Apache Sling API 2.27.2 API ](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24-1.4.0 | {de Specificatie van de Taal van het Malplaatje 0} HTML ](https://github.com/adobe/htl-spec)[ |
| AEM-kerncomponenten | 2,25,4 | [ AEM de Componenten van de Kern WCM ](https://github.com/adobe/aem-core-wcm-components) |
