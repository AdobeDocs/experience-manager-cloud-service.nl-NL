---
title: Opmerkingen bij de release voor Cloud Manager in AEM als Cloud Service Release 2021.3.0
description: Opmerkingen bij de release voor Cloud Manager in AEM als Cloud Service Release 2021.3.0
translation-type: tm+mt
source-git-commit: 36e5e90785a1bc9a4f4f8d4febd462e00252a0ea
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---


# Opmerkingen bij de release voor Cloud Manager in Adobe Experience Manager als Cloud Service 2021.3.0 {#release-notes}

Deze pagina bevat de releaseopmerkingen voor Cloud Manager in AEM als Cloud Service 2021.3.0.

## Releasedatum {#release-date}

De releasedatum voor Cloud Manager in AEM als Cloud Service 2021.3.0 is 11 maart 2021.
De volgende release is gepland voor 8 april 2021.

## Cloud Manager {#cloud-manager}

### Wat is er nieuw?{#what-is-new}

* Klanten met omgevingen met reeds bestaande aangepaste domeinnaamconfiguraties voor [IP-Lijsten van gewenste personen](/help/implementing/cloud-manager/ip-allow-lists/check-ip-allow-list-status.md#pre-existing-cdn), [SSL-certificaten](/help/implementing/cloud-manager/managing-ssl-certifications/check-status-ssl-certificate.md#pre-existing-cdn) en [Aangepaste domeinnamen](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md#pre-existing-cdn) zullen een bericht zien over hun eerdere bestaande configuraties en zullen zichzelf kunnen bedienen via de gebruikersinterface.

* Gebruikers met de vereiste machtigingen kunnen nu een programma bewerken, zodat zij het volgende op een zelfbedieningsmanier kunnen doen:
   * Voeg de oplossing van Plaatsen aan een bestaand programma met Activa (of vice versa) toe.
   * Sites (of Middelen) verwijderen uit een bestaand programma met zowel Sites als Middelen.
   * Voeg tweede, ongebruikte oplossingsrechten toe aan een bestaand programma of aan een nieuw programma.

* AEM het etiket van de Update van de Duw&quot;zal nu voor zowel de Uitvoering van de Pijpleiding als de schermen van de Activiteit worden getoond.

* Als een omgeving is gehiberneerd maar er ook een AEM update beschikbaar is, heeft de status &quot;Hibernated&quot; voorrang op &quot;Update available&quot;.

* Gebruikers kunnen nu hun rol(en) in de cloud Manager zien door de optie &#39;Rol(en) in de cloud-manager weergeven&#39; te selecteren nadat ze naar het pictogram Gebruikersprofiel (rechtsboven) van Unified Shell zijn genavigeerd.

* Voor meer duidelijkheid is het etiket &quot;Goedkeuringsaanvraag&quot; gelabeld aan &quot;Goedkeuring van de productie&quot;.

* Het &quot;Versielabel&quot;etiket is opnieuw gelabeld aan &quot;Git Markering&quot;in het scherm van de de pijpleiding van de Productie uitvoeren.

* De labels die het gedrag bepalen wanneer belangrijke metriek niet aan de bepaalde drempel voldoet, zijn geëtiketteerd om op hun ware gedrag te wijzen - onmiddellijk annuleren en Onmiddellijk goedkeuren.

* De lijsten van de klasse en van de methodevervanging zijn bijgewerkt gebaseerd op versie `2021.3.4997.20210303T022849Z-210225` van de AEM Cloud Service SDK.

* De productiepijplijn van de Manager van de Wolk zal nu het testen UI van de Douane mogelijkheden omvatten.

### Opgeloste problemen {#bug-fixes}

* Pakketversie is in sommige gevallen overgeslagen tijdens AEM upgrade.

* Bepaalde kwaliteitsproblemen zijn niet goed ontdekt wanneer pakketten in andere pakketten waren ingesloten.

* In duistere situaties, zou de standaardprogrammanaam die bij het openen van de Add dialoog van het Programma wordt geproduceerd een duplicaat van een bestaande programmanaam kunnen zijn.

* Wanneer de gebruiker bij gelegenheid vanaf de pagina voor de uitvoering van de pijpleiding navigeert onmiddellijk nadat een pijpleiding is gestart, wordt een foutbericht weergegeven met de mededeling dat de handeling is mislukt, hoewel de uitvoering daadwerkelijk wordt gestart.

* De bouwstijlstap werd onnodig opnieuw begonnen toen de klant bouwt in ongeldige pakketten resulteerde.

* Soms, kan de gebruiker een groene &quot;actieve&quot;status naast een IP Lijst van gewenste personen zien zelfs wanneer die configuratie niet werd opgesteld.

* Alle bestaande productiepijpleidingen worden automatisch ingeschakeld met behulp van de stap Experience Audit.