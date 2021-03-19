---
title: Opmerkingen bij de release voor Cloud Manager in AEM als Cloud Service Release 2020.10.0
description: Opmerkingen bij de release voor Cloud Manager in AEM als Cloud Service Release 2020.10.0
feature: Geen informatie
translation-type: tm+mt
source-git-commit: 0f2b7176b44bb79bdcd1cecf6debf05bd652a1a1
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 1%

---


# Opmerkingen bij de release voor Cloud Manager in Adobe Experience Manager als Cloud Service 2020.10.0 {#release-notes}

Deze pagina bevat de releaseopmerkingen voor Cloud Manager in AEM als Cloud Service 2020.10.0.

## Releasedatum {#release-date}

De releasedatum voor Cloud Manager in AEM als Cloud Service 2020.10.0 is 1 oktober 2020.

## Cloud Manager {#cloud-manager}

### Wat is er nieuw?{#what-is-new}

* De pagina Omgevingen is opnieuw ontworpen.

* In gedownneerde omgevingen wordt nu een aparte status weergegeven in Cloud Manager wanneer deze worden gehiberneerd.

* De buildcontainer van Cloud Manager ondersteunt nu het compileren van projecten met behulp van Java 8 of Java 11. Ondersteuning voor Java 11 wordt geleverd door het Maven-toolketensysteem.

* Het aantal omgevingsvariabelen per omgeving is verhoogd tot 200.

* De kaart van het Milieu op de pagina van het Overzicht zal nu tot drie milieu&#39;s een lijst maken. Gebruikers kunnen de knop **Alles weergeven** selecteren om naar de overzichtspagina Omgeving te navigeren en een tabel met een volledige lijst met omgevingen weer te geven.
Zie [Omgeving weergeven](/help/implementing/cloud-manager/manage-environments.md#viewing-environment) voor meer informatie.


### Opgeloste problemen {#bug-fixes-cloud-manager}

* De koppeling van Cloud Manager naar de Developer Console was onjuist actief voordat omgevingen volledig werden gemaakt.

* De koppeling naar de ontwikkelaarsconsole rechtstreeks vanuit Cloud Manager gaf de optie voor het dehiberneren/hberneren van de omgeving van een Sandbox-programma niet weer.

* De knoppen Annuleren en Opslaan op de pagina Bewerken zonder productiepijplijn zijn niet altijd zichtbaar.

* Bepaalde fouten in het proces van de codekwaliteit kunnen ertoe leiden dat het logbestand niet correct wordt gegenereerd.

* Bij het maken van een nieuw programma retourneert de voorgestelde naam soms een duplicaat van een bestaande programmanaam.

* Sommige logboeken van grote pijpleidingsstappen konden niet constant door het gebruikersinterface worden gedownload.

* De validatie van omgevingsnamen had een off-by-one fout.

* Op de pagina Milieu&#39;s worden soms publicatie- en verzendingssegmenten weergegeven wanneer er geen aanwezig was.