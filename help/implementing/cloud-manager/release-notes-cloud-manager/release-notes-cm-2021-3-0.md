---
title: Opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service versie 2021.3.0
description: Opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service versie 2021.3.0
feature: Release Information
exl-id: f826e0c6-3b1d-44f5-99a2-f792f5df3a55
source-git-commit: 71647239fc5e740faa25524a01a8ef21ed2d7a3b
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# Opmerkingen bij de release voor Cloud Manager in Adobe Experience Manager as a Cloud Service 2021.3.0 {#release-notes}

Deze pagina bevat een overzicht van de opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service 2021.3.0.

## Releasedatum {#release-date}

De releasedatum voor Cloud Manager in AEM as a Cloud Service 2021.3.0 is 11 maart 2021.

## Cloud Manager {#cloud-manager}

### Wat is er nieuw? {#what-is-new}

* Klanten met omgevingen met bestaande aangepaste domeinnaamconfiguraties voor [IP-Lijsten van gewenste personen](/help/implementing/cloud-manager/ip-allow-lists/managing-ip-allow-lists.md#pre-existing-cdn), [SSL-certificaten](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md#pre-existing-cdn) en [Aangepaste domeinnamen](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md#pre-existing-cdn) zal een bericht over hun eerder bestaande configuraties zien en zal kunnen zelf-dienen via UI.

* Gebruikers met de vereiste machtigingen kunnen nu een programma bewerken, zodat zij het volgende op een zelfbedieningsmanier kunnen doen:
   * Voeg de oplossing van Plaatsen aan een bestaand programma met Activa of vice versa toe.
   * Sites of middelen verwijderen uit een bestaand programma met zowel Sites als Middelen.
   * Voeg tweede, ongebruikte oplossingsrechten toe aan een bestaand programma of aan een nieuw programma.

* **AEM bijwerken** Het label wordt nu weergegeven voor zowel het scherm Uitvoeren als Activiteit van de pijplijn.

* Als een omgeving is gehiberneerd maar er ook een AEM update beschikbaar is, kunt u het volgende doen: **Gesamberneerd** status heeft voorrang op **Update beschikbaar**.

* Gebruikers kunnen nu hun rol(en) in de cloud Manager zien door de optie &#39;Rol(en) in de cloud-manager weergeven&#39; te selecteren nadat ze naar het pictogram Gebruikersprofiel (rechtsboven) van Unified Shell zijn genavigeerd.

* Het label **Goedkeuringsaanvraag** is opnieuw gelabeld aan **Erkenning productie** voor meer duidelijkheid.

* De **Versie** label is opnieuw gelabeld aan **Git-tag** in het scherm van de de pijpleiding van de Productie uitvoeren.

* De labels die het gedrag bepalen wanneer belangrijke metriek niet aan de bepaalde drempel voldoet, zijn opnieuw ge??tiketteerd om op hun ware gedrag te wijzen: **Direct annuleren** en **Direct goedkeuren**.

* De lijsten met klassen en methoden zijn bijgewerkt op basis van versie `2021.3.4997.20210303T022849Z-210225` van de SDK van AEM Cloud Service.

* De productiepijplijn van Cloud Manager wordt nu opgenomen [Aangepaste UI-tests](/help/implementing/cloud-manager/functional-testing.md#custom-ui-testing) capaciteit.

### Opgeloste problemen  {#bug-fixes}

* Pakketversie is in sommige gevallen overgeslagen tijdens AEM upgrade.

* Bepaalde kwaliteitsproblemen zijn niet goed ontdekt wanneer pakketten in andere pakketten waren ingesloten.

* In duistere situaties, zou de standaardprogrammanaam die bij het openen van de Add dialoog van het Programma wordt geproduceerd een duplicaat van een bestaande programmanaam kunnen zijn.

* Wanneer de gebruiker bij gelegenheid vanaf de pagina voor de uitvoering van de pijpleiding navigeert onmiddellijk nadat een pijpleiding is gestart, wordt een foutbericht weergegeven met de mededeling dat de handeling is mislukt, hoewel de uitvoering daadwerkelijk wordt gestart.

* De bouwstijlstap werd onnodig opnieuw begonnen toen de klant bouwt in ongeldige pakketten resulteerde.

* Soms, kan de gebruiker een groene &quot;actieve&quot;status naast een IP Lijst van gewenste personen zien zelfs wanneer die configuratie niet werd opgesteld.

* Alle bestaande productiepijpleidingen worden automatisch ingeschakeld met behulp van de stap Experience Audit.
