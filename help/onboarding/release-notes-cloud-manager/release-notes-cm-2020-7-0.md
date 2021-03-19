---
title: Opmerkingen bij de release voor Cloud Manager in AEM als Cloud Service Release 2020.7.0
description: Opmerkingen bij de release voor Cloud Manager in AEM als Cloud Service Release 2020.7.0
feature: Geen informatie
translation-type: tm+mt
source-git-commit: 0f2b7176b44bb79bdcd1cecf6debf05bd652a1a1
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 1%

---


# Opmerkingen bij de release voor Cloud Manager in Adobe Experience Manager als Cloud Service 2020.7.0 {#release-notes}

Deze pagina bevat de releaseopmerkingen voor Cloud Manager in AEM als Cloud Service 2020.7.0.

## Releasedatum {#release-date}

De releasedatum voor Cloud Manager in AEM als Cloud Service 2020.7.0 is 9 juli 2020.

## Wat is er nieuw?{#whats-new-cloud-manager}

* De pagina met omgevingen is opnieuw ontworpen.

* In gedownneerde omgevingen wordt nu een aparte status weergegeven in Cloud Manager wanneer deze worden gehiberneerd.

* Het aantal omgevingsvariabelen per omgeving is verhoogd tot 200.

* De pijpleidingen van de Manager van de wolk steunen nu klant-vastgestelde variabelen en geheimen.

   Raadpleeg [Variabelen pijpleiding](/help/onboarding/getting-access-to-aem-in-cloud/build-environment-details.md#pipeline-variables) voor meer informatie.

* Verificatie-gebonden Private Maven Repositories worden nu ondersteund.

* De buildcontainer van Cloud Manager ondersteunt nu zowel Java 8 als Java 11.
Raadpleeg [Java 11-ondersteuning gebruiken](/help/onboarding/getting-access-to-aem-in-cloud/build-environment-details.md#using-java-support) voor meer informatie.

### Opgeloste problemen {#bug-fixes-cm}

* De koppeling van Cloud Manager naar de Developer Console was onjuist actief voordat omgevingen volledig werden gemaakt.

* De koppeling naar de ontwikkelaarsconsole rechtstreeks vanuit Cloud Manager gaf de optie voor het dehiberneren/hberneren van de omgeving van een Sandbox-programma niet weer.

* De opties **Annuleren** en **Opslaan** op de bewerkingspagina Niet-productiepijplijn zijn niet altijd zichtbaar.

* Bepaalde fouten in het proces van de codekwaliteit kunnen ertoe leiden dat het logbestand niet correct wordt gegenereerd.

* Bij het maken van een nieuw programma retourneert de voorgestelde naam soms een duplicaat van een bestaande programmanaam.

* Sommige logboeken van grote pijpleidingsstappen konden niet constant door het gebruikersinterface worden gedownload.

* De validatie van omgevingsnamen had een off-by-one fout.

* Op de pagina Milieu&#39;s worden soms publicatie- en verzendingssegmenten weergegeven wanneer er geen aanwezig was.

### Bekende problemen {#known-issues}

* Als gevolg van een wijziging in de manier waarop de codedekking wordt berekend, is de *minimum*-versie van de Jacoco-plug-in nu 0.7.5.201505241946 (uitgebracht in mei 2015). Klanten die expliciet verwijzen naar een oudere versie ontvangen een foutbericht in het proces voor de kwaliteit van de code.