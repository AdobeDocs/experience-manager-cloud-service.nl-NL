---
title: Adobe Experience Manager als de Nota's van de Versie van de Cloud Service voor 2020.7.0
description: Opmerkingen bij de release van Experience Manager voor 2020.7.0
translation-type: tm+mt
source-git-commit: 66f066fe55ef872b62d4dcee711d3c7077bfccd1
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Opmerkingen bij de release voor AEM als Cloud Service 2020.7.0 {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor Experience Manager beschreven als Cloud Service 2020.7.0.

## Nieuwe functies in Cloud Manager {#cloud-manager}

Volg deze sectie voor meer informatie over nieuwe functies en de updates voor Cloud Manager in AEM als Cloud Service Release 2020.7.0.

### Releasedatum {#release-date}

De releasedatum voor [!UICONTROL Cloud Manager] versie 2020.7.0 is 9 juli 2020.

### What&#39;s New {#what-is-new-cloud-manager}

* De pagina met omgevingen is opnieuw ontworpen.

* In gedownneerde omgevingen wordt nu een aparte status weergegeven in Cloud Manager wanneer deze worden gehiberneerd.

* Het aantal omgevingsvariabelen per omgeving is verhoogd tot 200.

* De buildcontainer van Cloud Manager ondersteunt nu zowel Java 8 als Java 11.

### Bug Fixes {#bug-fixes-cm}

* De koppeling van Cloud Manager naar de Developer Console was onjuist actief voordat omgevingen volledig werden gemaakt.

* De koppeling naar de ontwikkelaarsconsole rechtstreeks vanuit Cloud Manager gaf de optie voor het dehiberneren/hberneren van de omgeving van een Sandbox-programma niet weer.

* De opties **Annuleren** en **Opslaan** op de bewerkingspagina Niet-productiepijplijn zijn niet altijd zichtbaar.

* Bepaalde fouten in het proces van de codekwaliteit kunnen ertoe leiden dat het logbestand niet correct wordt gegenereerd.

* Bij het maken van een nieuw programma retourneert de voorgestelde naam soms een duplicaat van een bestaande programmanaam.

* Sommige logboeken van grote pijpleidingsstappen konden niet constant door het gebruikersinterface worden gedownload.

* De validatie van omgevingsnamen had een off-by-one fout.

* Op de pagina Milieu&#39;s worden soms publicatie- en verzendingssegmenten weergegeven wanneer er geen aanwezig was.

## Nieuwe functies in de Cloud Readiness Analyzer {#cloud-readiness-analyzer}

Volg deze sectie om te weten te komen wat nieuw is en de updates voor Cloud Readiness Analyzer Release v1.0.2.

### Bug Fixes {#cra-bug-fixes}

* Eerdere versie van de CRA kan niet worden uitgevoerd op Adobe Experience Manager (AEM) 6.1. Er is expliciete ondersteuning toegevoegd om gebruikers in de beheerdersgroep toe te staan.

   Raadpleeg [CRA installeren op AEM 6.1](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/moving/cloud-migration/cloud-readiness-analyzer/using-cloud-readiness-analyzer.html#installing-on-aem61) voor meer informatie.

* De tijdstempel voor verlopen die in het samenvattingsrapport wordt weergegeven, is onjuist.

* CRA detecteerde dubbele aangepaste componenten.

* Op AEM 6.1 werd de inhoudsinspectie afgesloten voordat de volledige inspectie werd voltooid. Uitzonderingsafhandeling is toegevoegd, zodat de controle kan overslaan en doorgaan totdat de volledige inspectie is voltooid.

