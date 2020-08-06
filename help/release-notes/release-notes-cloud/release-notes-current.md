---
title: Opmerkingen bij de release voor 2020.8.0 [!DNL Adobe Experience Manager] van een Cloud Service.
description: '[!DNL Adobe Experience Manager] als opmerkingen bij de release van Cloud Servicen voor 2020.8.0.'
translation-type: tm+mt
source-git-commit: fe2439e506f84a191922416e9c99b496fd90016c
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 1%

---


# Opmerkingen bij de release voor [!DNL Adobe Experience Manager] als Cloud Service 2020.8.0 {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor Experience Manager beschreven als Cloud Service 2020.8.0.

## Cloud Manager {#cloud-manager}

### Releasedatum {#release-date-cm}

De releasedatum voor [!UICONTROL Cloud Manager] versie 2020.8.0 is 6 augustus 2020.

### What&#39;s New {#what-is-new-cloud-manager}

* De Controle van de inhoud is een eigenschap die op de Pijpleidingen van de Productie van de Plaatsen van de Manager van de Wolk wordt toegelaten. De configuratie van de Pijpleiding van de Productie voor programma&#39;s met Plaatsen omvat nu een derde lusje genoemd **Inhoud Controle**. Wanneer een productiepijpleiding in werking wordt gesteld, zal een nieuwe stap van de Controle van de Inhoud in de pijpleiding na douane functionele tests worden omvat die de plaats tegen een aantal dimensies met inbegrip van prestaties, SEO (de Optimalisering van de Motor van het Onderzoek), toegankelijkheid, beste praktijken en PWA (Progressieve App van het Web) zullen evalueren.

   Refer to [Content Audit Testing](/help/implementing/developing/introduction/understand-test-results.md#content-audit-testing) for more details.

* Nieuw gemaakte omgevingen in middelenprogramma&#39;s worden nu automatisch geconfigureerd met Smart Content Services.

* Gesamberde omgevingen kunnen worden gedehiberneerd via de overzichtspagina van Cloud Manager.

* Verificatie-gebonden Private Maven Repositories worden nu ondersteund.

### Bug Fixes {#bug-fixes-cm}

* Enkele onnodige en ongewenste SonarQube-plug-ins werden uitgevoerd als onderdeel van het scannen van codekwaliteit.

* Op de pagina van de pijpleiding uitvoerde, was de taknaam onjuist geformatteerd.

* In sommige gevallen werden voltooide executies van pijpleidingen niet met succes geregistreerd als voltooid, waardoor nieuwe executies van de pijpleiding werden voorkomen.

* De executies van pijpleidingen zouden af en toe &quot;vastzitten&quot;wegens interne communicatie kwesties.

* Bij de provisioning van een nieuwe organisatie kregen sommige gebruikers met andere beheerrollen dan systeembeheerders ten onrechte toegang tot Cloud Manager.

* Onder bepaalde voorwaarden werd de update-indexeertaak meerdere keren parallel gestart, wat leidde tot een implementatiefout.

* De knopinfo op de programmakaarten was niet consistent correct.

* De gebruikersinterface stond abusievelijk toe dat bewerkingen werden uitgevoerd in een omgeving terwijl deze werd verwijderd.

* Er is een kleurfout opgetreden op de overzichtspagina.

### Bekende problemen {#known-issues}

* Ongeldige pagina&#39;s worden opgenomen waardoor de gemiddelde score voor controle van inhoud lager wordt dan wat ze moeten zijn.

* Op het tabblad Inhoudscontrole wordt de basis-URL onjuist weergegeven met behulp van het auteurdomein in plaats van het publicatiedomein.

* Om de stap van de Controle van de Inhoud te activeren, moeten de gebruikers de pijpleiding uitgeven en, naar keuze, pagina&#39;s toevoegen. Als er geen pagina&#39;s worden toegevoegd, wordt de startpagina gecontroleerd.

