---
title: Functionele tests
description: Leer over de drie verschillende types van functionele tests die in het AEM as a Cloud Service plaatsingsproces worden gebouwd om kwaliteit en betrouwbaarheid van uw code te verzekeren.
exl-id: 7eb50225-e638-4c05-a755-4647a00d8357
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---


# Functionele tests {#functional-testing}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_functionaltesting"
>title="Functionele tests"
>abstract="Leer over de drie verschillende types van functionele tests die in het AEM as a Cloud Service plaatsingsproces worden gebouwd om kwaliteit en betrouwbaarheid van uw code te verzekeren."

Meer informatie over de drie verschillende typen functionele tests die in de [as a Cloud Service implementatieproces AEM](/help/implementing/cloud-manager/deploy-code.md) om de kwaliteit en betrouwbaarheid van uw code te garanderen.

## Scope

Het doel van de stappen voor functionele tests in de Cloud Manager-pijplijn is om ervoor te zorgen dat de essentiële functionaliteit van uw toepassing naar behoren functioneert.

Deze testfase is het laatste niveau van geautomatiseerde tests voordat u uw code implementeert op productie.

Functionele tests moeten andere teststrategieën, zoals eenheidstests, integratietests of functionele tests die buiten de uitvoering van de pijpleiding in Cloud Manager worden uitgevoerd, niet vervangen, maar aanvullen en uitbreiden.

## Overzicht {#overview}

Er zijn drie verschillende soorten functionele tests in AEM as a Cloud Service.

* [Functioneel testen van producten](#product-functional-testing)
* [Aangepaste functionele tests](#custom-functional-testing)
* [Aangepaste UI-tests](#custom-ui-testing)

Voor alle functionele tests kunnen de gedetailleerde resultaten van de tests als een `.zip` bestand met de **Buildlog downloaden** knoop in het bouwstijloverzichtsscherm als deel van [implementatieproces](/help/implementing/cloud-manager/deploy-code.md).

Deze logboeken bevatten niet de logboeken van het werkelijke AEM runtimeproces. Ga voor toegang tot deze logboeken naar [Logbestanden openen en beheren](/help/implementing/cloud-manager/manage-logs.md) voor meer informatie .

Zowel de functionele tests van het product als de aangepaste functionele tests zijn gebaseerd op de [AEM Clients testen.](https://github.com/adobe/aem-testing-clients)

### Functioneel testen van producten {#product-functional-testing}

De functionele tests van het product zijn een reeks stabiele HTTP integratietests (ITs) van kernfunctionaliteit in AEM zoals creatie en replicatietaken. Deze tests worden onderhouden door Adobe en zijn bedoeld om te voorkomen dat wijzigingen in aangepaste toepassingscode worden geïmplementeerd als deze de kernfunctionaliteit verbreekt.

* [Productiepijpleidingen](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md): De functionele tests van het product worden automatisch uitgevoerd wanneer u nieuwe code implementeert in Cloud Manager en kunnen niet worden overgeslagen.
* [Niet-productiepijpleidingen](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md): U kunt desgewenst testen op productfuncties selecteren om te worden uitgevoerd wanneer u de niet-productiepijplijn uitvoert.

De functionele tests van het product worden gehandhaafd als open-source-project. Zie [functionele producttests](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) in GitHub voor meer informatie.

### Aangepaste functionele tests {#custom-functional-testing}

Hoewel het testen van de productfunctionaliteit wordt gedefinieerd door Adobe, kunt u uw eigen kwaliteitstests voor uw eigen toepassing schrijven. Dit wordt uitgevoerd als aangepaste functionele tests als onderdeel van het [productiepijpleiding](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) of optioneel [niet-productiepijpleiding](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) om de kwaliteit van uw toepassing te garanderen.

Het functionele testen van de douane wordt in werking gesteld zowel voor douanecodeplaatsingen als duw verbeteringen, wat het bijzonder belangrijk maakt om goede functionele tests te schrijven die AEM codeveranderingen verhinderen uw toepassingscode te breken. De aangepaste functionele teststap is altijd aanwezig en kan niet worden overgeslagen.

Zie [Functionele Java-tests](/help/implementing/cloud-manager/java-functional-testing.md) voor meer informatie .


### Aangepaste UI-tests {#custom-ui-testing}

Het testen UI van de douane is een facultatieve eigenschap die u toelaat om tests UI voor uw toepassingen tot stand te brengen en automatisch in werking te stellen. De tests UI zijn op selenium-Gebaseerde tests die in een beeld van de Docker worden verpakt om voor een brede keus van taal en kaders zoals Java en Maven, Node en WebDriver.io, of om het even welk ander kader en technologie toe te staan die op Selenium worden gebouwd.

Zie [Aangepaste UI-tests](/help/implementing/cloud-manager/ui-testing.md#custom-ui-testing) voor meer informatie .

