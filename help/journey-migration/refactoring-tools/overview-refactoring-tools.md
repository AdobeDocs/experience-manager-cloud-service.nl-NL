---
title: Overzicht van Refactoring-gereedschappen
description: Leer hoe u aan de slag kunt met de AEM Refactoring Tools
exl-id: b8137e01-87e8-4298-b0cc-b376330cb730
source-git-commit: 879f4f3476ee369554188d6e3b7973d32454ed4b
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

<!-- Alexandru: temporarily commeting this out, since it breaks validation

>[!CONTEXTUALHELP]
>id="aemcloud_rs_overview"
>title="Overview"
>abstract="Refactoring Tools is a solution developed by Adobe to help refactor existing AEM projects for compatibility with AEM as a Cloud Service. The tools are executed via Cloud Acceleration Manager (CAM) and automate key modernization tasks."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=nl-NL" text="Guidelines and Best Practices"

-->

# Overzicht van Refactoring-gereedschappen {#refactoring-tools-overview}

**Refactoring Hulpmiddelen** stroomlijnt het proces om bestaande projecten van AEM bij te werken om compatibel te zijn met **AEM as a Cloud Service (AEMaaCS)**. Deze hulpmiddelen automatiseren gemeenschappelijke refactoring en moderniseringstaken en zijn geïntegreerd met **Cloud Acceleration Manager (CAM)** voor een naadloze ervaring.

Eerder beschikbaar slechts als nut CLI, verstrekken de Hulpmiddelen van het Refactoring nu een verenigde interface met eigenschappen zoals geautomatiseerde inspectie, configuratiegeneratie, en baanuitvoering - verminderend handleiding overheadkosten en verbeterend zicht.

## Inspectiewerkstroom {#inspection-workflow}

Het **Werkschema van de Inspectie** vereenvoudigt het voorbereidingsproces voor het runnen van refactoring hulpmiddelen.

### Belangrijkste kenmerken:

* **Automatische Trekker** - het Uploaden van een project begint automatisch de inspectie.
* **Generatie van de Configuratie** - de hulpmiddelen inspecteren de geuploade broncode en produceren de noodzakelijke configuraties.
* **Verzending van de Payload** - Deze configuraties worden overgegaan direct tot de geselecteerde hulpmiddelen voor uitvoering.

## Beschikbare Refactoring-gereedschappen

### Repository Modernizer {#repo-modernizer}

De **Modernizer van de Bewaarplaats van de Bewaarplaats** herstructureert de de bewaarplaats van uw AEM project lay-out en inhoud om met normen AEMaaCS en beste praktijken te richten. Het vervangt het oude moderniseringsinstrument van de repository door verbeterde automatisering en nauwkeurigheid.

### Codetransformator {#code-transformer}

De **Transformator van de Code** gebruikt intelligente patroonerkenning en AI-gedreven analyse om codesegmenten te ontdekken en bij te werken die onverenigbaar met AEMaaCS zijn. Dit hulpmiddel vereenvoudigt de migratie-inspanning en vermindert handcodeveranderingen.

## Refactoring Workflowfasen {#phases-in-refactoring-tools}

De Refactoring-gereedschappen volgen een gestructureerd tweefaseproces:

### Fase 1: Je Source-code uploaden

* Upload uw broncode (in ZIP-indeling) met behulp van de CAM-interface.
* Zodra geupload, wordt het **Werkschema van de Inspectie** automatisch teweeggebracht om het project te analyseren en het voor hulpmiddeluitvoering voor te bereiden.

>[!NOTE]
>Tijdens het inspectieproces is het niet toegestaan een ander project te uploaden.

### Fase 2: Een Refactoring-taak activeren

Na een succesvolle inspectie, kunt u één of meerdere refactoring hulpmiddelen in werking stellen:

* **de Modernisering van de Opslagplaats van de looppas** - voert bewaarplaatsanering uit.
* **looppas de Transformator van de Code** - stelt codetransformatie in werking die op inspectieoutput wordt gebaseerd.
* **Looppas Alle Hulpmiddelen samen** - voert alle beschikbare hulpmiddelen in één enkele verrichting uit.

>[!NOTE]
>Refactoring-taken kunnen alleen worden gestart nadat de broncode is geüpload en geïnspecteerd.

>[!NOTE]
>Gebruikers kunnen meerdere refactoring-taken tegelijk activeren, maar elke taak wordt afzonderlijk uitgevoerd.
