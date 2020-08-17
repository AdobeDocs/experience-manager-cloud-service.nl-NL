---
title: Opmerkingen bij de release voor 2020.8.0 [!DNL Adobe Experience Manager] van een Cloud Service.
description: '[!DNL Adobe Experience Manager] als opmerkingen bij de release van Cloud Servicen voor 2020.8.0.'
translation-type: tm+mt
source-git-commit: 5a53e13a3692fbb8ab3ae7760f13b6908d15db3a
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 1%

---


# Opmerkingen bij de release voor [!DNL Adobe Experience Manager] als Cloud Service 2020.8.0 {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor Experience Manager beschreven als Cloud Service 2020.8.0.

## [!DNL Adobe Experience Manager Assets] als Cloud Service {#assets}

* De nieuwe [!DNL Experience Manager Assets] plaatsingen worden geïntegreerd met [!DNL Adobe Developer Console] door gebrek. De functie helpt de functionaliteit voor slimme tags sneller te configureren. Voor de bestaande plaatsingen, [vormen de beheerders slimme markeringen integratie](/help/assets/smart-tags-configuration.md#aio-integration) zoals voordien.

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### What&#39;s New {#what-is-new-commerce}

* De functie Productconsole is nu beschikbaar. Dit staat marketers/auteurs in AEM toe om categorieën en producten te bekijken en te navigeren die in de handelskern worden opgeslagen. Er wordt ook ondersteuning geboden voor eigenschappen voor categorieën en producten in de productconsole.

* Product- en rubriekkiezers zijn verbeterd zodat marketers hun product via SKU kunnen selecteren of een categorie kunnen selecteren via rubriek-id.

## Cloud Manager {#cloud-manager}

### Releasedatum {#release-date-cm}

De releasedatum voor [!UICONTROL Cloud Manager] versie 2020.8.0 is 6 augustus 2020.

### What&#39;s New {#what-is-new-cloud-manager}

* De Controle van de inhoud is een eigenschap die op de Pijpleidingen van de Productie van de Plaatsen van de Manager van de Wolk wordt toegelaten. De configuratie van de Pijpleiding van de Productie voor programma&#39;s met Plaatsen omvat nu een derde lusje genoemd **Inhoud Controle**. Wanneer een productiepijpleiding in werking wordt gesteld, zal een nieuwe stap van de Controle van de Inhoud in de pijpleiding na douane functionele tests worden omvat die de plaats tegen een aantal dimensies met inbegrip van prestaties, SEO (de Optimalisering van de Motor van het Onderzoek), toegankelijkheid, beste praktijken en PWA (Progressieve App van het Web) zullen evalueren.

   Refer to [Content Audit Testing](/help/implementing/developing/introduction/understand-test-results.md#content-audit-testing) for more details.

* Nieuw gemaakte omgevingen in middelenprogramma&#39;s worden nu automatisch geconfigureerd met Smart Content Services.

* Gesamberde omgevingen kunnen worden gedehiberneerd op de pagina **Overzicht** van Cloud Manager.

* Verificatie-gebonden Private Maven Repositories worden nu ondersteund.

* De buildcontainer van Cloud Manager ondersteunt nu zowel Java 8 als Java 11.
Raadpleeg Ondersteuning [van Java 11](/help/onboarding/getting-access-to-aem-in-cloud/creating-aem-application-project.md#using-java-support) gebruiken voor meer informatie.

### Bug Fixes {#bug-fixes-cm}

* Enkele onnodige en ongewenste SonarQube-plug-ins werden uitgevoerd als onderdeel van het scannen van codekwaliteit.

* Op de pagina van de pijpleiding uitvoerde, was de taknaam onjuist geformatteerd.

* In sommige gevallen werden voltooide executies van pijpleidingen niet met succes geregistreerd als voltooid, waardoor nieuwe executies van de pijpleiding werden voorkomen.

* De executies van pijpleidingen zouden af en toe *vastzitten* als gevolg van interne communicatieproblemen.

* Bij de provisioning van een nieuwe organisatie kregen sommige gebruikers met andere beheerrollen dan systeembeheerders ten onrechte toegang tot Cloud Manager.

* Onder bepaalde voorwaarden werd de update-indexeertaak meerdere keren parallel gestart, wat leidde tot een implementatiefout.

* De knopinfo op de programmakaarten was niet consistent correct.

* De gebruikersinterface stond abusievelijk toe dat bewerkingen werden uitgevoerd in een omgeving terwijl deze werd verwijderd.

* Er is een kleurfout opgetreden op de pagina **Overzicht** van Cloud Manager.

### Bekende problemen {#known-issues-cm}

* Ongeldige pagina&#39;s worden opgenomen waardoor de gemiddelde score voor controle van inhoud lager wordt dan wat ze moeten zijn.

* Op het tabblad Inhoudscontrole wordt de basis-URL onjuist weergegeven met behulp van het auteurdomein in plaats van het publicatiedomein.

* Om de stap van de Controle van de Inhoud te activeren, moeten de gebruikers de pijpleiding uitgeven en, naar keuze, pagina&#39;s toevoegen. Als er geen pagina&#39;s worden toegevoegd, wordt de startpagina gecontroleerd.

## De tool Content Transfer {#content-transfer-tool}

Volg deze sectie om te leren over wat nieuw is en de updates voor Versie van het Hulpmiddel van de Overdracht van de Inhoud v1.0.4.

### What&#39;s New {#what-is-new-ctt}

* Content Transfer Tool biedt nu ondersteuning voor Shared S3 DataStore.

### Bug Fixes {#ctt-bug-fixes}

* Er zijn extra onderbrekingen toegevoegd voor het gereedschap om de handelingen te voltooien.

* De gebruikersinterface van eerdere versies toonde soms een geslaagde extractie, ook al toonde het logboek fouten.

