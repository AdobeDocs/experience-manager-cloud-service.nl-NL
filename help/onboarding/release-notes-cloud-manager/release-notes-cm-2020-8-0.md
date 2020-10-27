---
title: Opmerkingen bij de release voor Cloud Manager in AEM als Cloud Service Release 2020.8.0
description: Opmerkingen bij de release voor Cloud Manager in AEM als Cloud Service Release 2020.8.0
translation-type: tm+mt
source-git-commit: ca690144a8254d5ffba354f0f96d9ef1c5202533
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---


# Opmerkingen bij de release voor Cloud Manager in Adobe Experience Manager als Cloud Service 2020.8.0 {#release-notes}

Deze pagina bevat de releaseopmerkingen voor Cloud Manager in AEM als Cloud Service 2020.8.0.

## Releasedatum {#release-date}

De releasedatum voor Cloud Manager in AEM als Cloud Service 2020.8.0 is 6 augustus 2020.

## Wat is er nieuw?{#whats-new-cloud-manager}

* De Controle van de inhoud is een eigenschap die op de Pijpleidingen van de Productie van de Plaatsen van de Manager van de Wolk wordt toegelaten. De configuratie van de Pijpleiding van de Productie voor programma&#39;s met Plaatsen omvat nu een derde lusje genoemd **Inhoud Controle**. Wanneer een productiepijpleiding in werking wordt gesteld, zal een nieuwe stap van de Controle van de Inhoud in de pijpleiding na douane functionele tests worden omvat die de plaats tegen een aantal dimensies met inbegrip van prestaties, SEO (de Optimalisering van de Motor van het Onderzoek), toegankelijkheid, beste praktijken en PWA (Progressieve App van het Web) zullen evalueren.


   >[!NOTE]
   >De naam van Content Audit is sindsdien gewijzigd in Experience Audit.

   Raadpleeg [Experience Audit Testing](/help/implementing/cloud-manager/experience-audit-testing.md) voor meer informatie.

* Nieuw gemaakte omgevingen in middelenprogramma&#39;s worden nu automatisch geconfigureerd met Smart Content Services.

* Gesamberde omgevingen kunnen worden gedehiberneerd op de pagina **Overzicht** van Cloud Manager.

* Mogelijkheid om ervaringscontroles uit te voeren op pagina&#39;s, aangedreven door Google Lighthouse. Als onderdeel van de Cloud Manager-pijplijn kunnen maximaal 25 pagina&#39;s worden gecontroleerd en gevalideerd op basis van ervaringen met KPI&#39;s en scores worden weergegeven in de gebruikersinterface van Cloud Manager.

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