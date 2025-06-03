---
title: Aan de slag met Refactoring Tools
description: Leer hoe u aan de slag kunt met de AEM Refactoring Tools
exl-id: c0cecf65-f419-484b-9d55-3cbd561e8dcd
source-git-commit: fa65b489d54d5333811145a1875a8f6fc89317bc
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---


>[!CONTEXTUALHELP]
>id="aemcloud_rs_overview"
>title="Overzicht"
>abstract="Refactoring Tools is een oplossing die door Adobe is ontwikkeld om bestaande AEM-projecten te helpen refactoreren voor compatibiliteit met AEM as a Cloud Service. De hulpmiddelen worden uitgevoerd via Cloud Acceleration Manager (CAM) en automatiseren zeer belangrijke moderniseringstaken."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=nl-NL" text="Richtlijnen en beste praktijken"

# Aan de slag met Refactoring Tools {#getting-started-refactoring-tools}

**Refactoring Hulpmiddelen** stroomlijnt het proces om bestaande projecten van AEM bij te werken om compatibel te zijn met **AEM as a Cloud Service (AEMaaCS)**. Deze hulpmiddelen automatiseren gemeenschappelijke refactoring en moderniseringstaken en zijn geïntegreerd met **Cloud Acceleration Manager (CAM)** voor een naadloze ervaring.

Eerder beschikbaar slechts als nut CLI, verstrekken de Hulpmiddelen van het Refactoring nu een verenigde interface met eigenschappen zoals geautomatiseerde inspectie, configuratiegeneratie, en baanuitvoering - verminderend handleiding overheadkosten en verbeterend zicht.

&#x200B;---

## Inspectiewerkstroom {#inspection-workflow}

Het **Werkschema van de Inspectie** vereenvoudigt het voorbereidingsproces voor het runnen van refactoring hulpmiddelen.

### Belangrijkste kenmerken:

* **Automatische Trekker** - het Uploaden van een project begint automatisch de inspectie.
* **Generatie van de Configuratie** - de hulpmiddelen inspecteren de geuploade broncode en produceren de noodzakelijke configuraties.
* **Verzending van de Payload** - Deze configuraties worden overgegaan direct tot de geselecteerde hulpmiddelen voor uitvoering.

&#x200B;---

## Beschikbare Refactoring-gereedschappen

### Repository Modernizer {#repo-modernizer}

De **Modernizer van de Bewaarplaats van de Bewaarplaats** herstructureert de de bewaarplaats van uw AEM project lay-out en inhoud om met normen AEMaaCS en beste praktijken te richten. Het vervangt het oude moderniseringsinstrument van de repository door verbeterde automatisering en nauwkeurigheid.

### Codetransformator {#code-transformer}

De **Transformator van de Code** gebruikt intelligente patroonerkenning en AI-gedreven analyse om codesegmenten te ontdekken en bij te werken die onverenigbaar met AEMaaCS zijn. Dit hulpmiddel vereenvoudigt de migratie-inspanning en vermindert handcodeveranderingen.

&#x200B;---

## Refactoring Workflowfasen {#phases-in-refactoring-tools}

De Refactoring-gereedschappen volgen een gestructureerd tweefaseproces:

### Fase 1: Je Source-code uploaden

* Upload uw broncode (in ZIP-indeling) met behulp van de CAM-interface.
* Zodra geupload, wordt het **Werkschema van de Inspectie** automatisch teweeggebracht om het project te analyseren en het voor hulpmiddeluitvoering voor te bereiden.

>[!NOTE]
>Tijdens het inspectieproces is het niet toegestaan een ander project te uploaden.

&#x200B;---

### Fase 2: Een Refactoring-taak activeren

Na een succesvolle inspectie, kunt u één of meerdere refactoring hulpmiddelen in werking stellen:

* **de Modernisering van de Opslagplaats van de looppas** - voert bewaarplaatsanering uit.
* **looppas de Transformator van de Code** - stelt codetransformatie in werking die op inspectieoutput wordt gebaseerd.
* **Looppas Alle Hulpmiddelen samen** - voert alle beschikbare hulpmiddelen in één enkele verrichting uit.

>[!NOTE]
>Refactoring-taken kunnen alleen worden gestart nadat de broncode is geüpload en geïnspecteerd.

>[!NOTE]
>Gebruikers kunnen meerdere refactoring-taken tegelijk activeren, maar elke taak wordt afzonderlijk uitgevoerd.
