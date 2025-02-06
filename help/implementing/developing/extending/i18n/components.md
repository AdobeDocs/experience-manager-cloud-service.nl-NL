---
title: Internationaliserende componenten
description: Internationaliseer uw componenten en dialogen zodat hun reeksen UI in verschillende talen kunnen worden voorgesteld
topic-tags: components
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: 0276b310-b9a9-44b6-b295-06c51ef17208
source-git-commit: 401685af02c720994d72cd95d36f0cfcdf15d198
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# Internationaliserende componenten{#internationalizing-components}

Internationaliseer uw componenten en dialogen zodat hun koorden UI in verschillende talen kunnen worden voorgesteld. Componenten die zijn ontworpen voor internationalisatie maken het mogelijk om UI-tekenreeksen te extern maken, te vertalen en vervolgens te importeren in de opslagplaats. Tijdens runtime bepaalt de taalvoorkeuren van de gebruiker of de landinstelling van de pagina welke taal wordt weergegeven in de gebruikersinterface.

![ i18n-components-1.png ](/help/implementing/developing/extending/assets/i18n-comp1.png)

Gebruik het volgende proces om uw componenten te internationaliseren en de gebruikersinterface in verschillende talen te bieden:

1. [ voer uw componenten uit gebruikend code die koorden internationaliseert.](/help/implementing/developing/extending/i18n/dev.md) De code identificeert de tekenreeksen die moeten worden vertaald en selecteert de taal die moet worden weergegeven bij uitvoering.
1. [ creeer woordenboeken ](/help/implementing/developing/extending/i18n/translator.md#creating-a-dictionary).
1. [ de Uitvoer ](/help/implementing/developing/extending/i18n/translator.md#exporting-a-dictionary) het woordenboek aan formaat XLIFF, vertaalt de koorden, dan de dossiers XLIFF terug in AEM.
1. Neem het woordenboek op in het releasebeheerproces van uw toepassing.

>[!NOTE]
>
>De hier beschreven methoden voor het internationaliseren van componenten zijn bedoeld voor het omzetten van statische tekenreeksen. Wanneer componenttekenreeksen naar verwachting zullen veranderen, moet u conventionele vertaalworkflows gebruiken. Wanneer ontwerpers bijvoorbeeld een UI-tekenreeks kunnen bewerken met eigenschappen in het dialoogvenster Bewerken van een component, mogen ze geen taalwoordenboek gebruiken om de tekenreeks te internationaliseren.

## Taalwoordenboeken {#language-dictionaries}

Het AEM internationalisatiekader gebruikt woordenboeken in de repository om Engelse tekenreeksen en hun vertalingen in andere talen op te slaan. Het framework gebruikt Engels als de standaardtaal. Tekenreeksen worden geïdentificeerd met behulp van hun Engelse versie. Bij internationalisatieframes worden doorgaans alfanumerieke id&#39;s gebruikt voor UI-tekenreeksen. Het gebruik van de Engelse versie van de tekenreeks als de id heeft verschillende voordelen:

* Code is gemakkelijk te lezen.
* De standaardtaal is altijd beschikbaar.

Het [ hulpmiddel van de Vertaling ](/help/implementing/developing/extending/i18n/translator.md) laat u toe om alle woordenboeken van één centrale plaats te beheren.

![ i18n-componenten-2 ](/help/implementing/developing/extending/assets/i18n-comp2.png)

De vertalingsveranderingen moeten van Git via de [ CI/CD pijpleiding ](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) in AEM als wolkendienst komen.

### Tekenreeksen in systeemwoordenboeken overschrijven {#overlaying-strings-in-system-dictionaries}

Als uw componenten tekenreeksen gebruiken die in de systeemwoordenboeken van het AEM zijn opgenomen, dupliceert u de tekenreeks in uw eigen woordenboek. Alle componenten gebruiken de tekenreeksen uit uw woordenboek.

U kunt niet voorspellen welke vertaling wordt gebruikt wanneer tekenreeksen worden gedupliceerd in woordenboeken die zich allemaal onder het knooppunt `/apps` bevinden.
