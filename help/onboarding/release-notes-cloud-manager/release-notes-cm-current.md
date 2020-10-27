---
title: Opmerkingen bij de release voor Cloud Manager in AEM als Cloud Service Release 2020.10.0
description: Opmerkingen bij de release voor Cloud Manager in AEM als Cloud Service Release 2020.10.0
translation-type: tm+mt
source-git-commit: 7fdbdd8bfe80d5f87d9917c905c8d04c4c277534
workflow-type: tm+mt
source-wordcount: '287'
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

* De buildcontainer van Cloud Manager ondersteunt nu zowel Java 8 als Java 11.

* Het aantal omgevingsvariabelen per omgeving is verhoogd tot 200.

* De kaart van het Milieu op de pagina van het Overzicht zal nu tot drie milieu&#39;s een lijst maken. Gebruikers kunnen de knop Alles **** tonen selecteren om naar de overzichtspagina Omgeving te navigeren en een tabel met een volledige lijst met omgevingen weer te geven.
Zie [Weergaveomgeving](/help/implementing/cloud-manager/manage-environments.md#viewing-environment) voor meer informatie.


### Bug Fixes {#bug-fixes-cloud-manager}

* De koppeling van Cloud Manager naar de Developer Console was onjuist actief voordat omgevingen volledig werden gemaakt.

* De koppeling naar de ontwikkelaarsconsole rechtstreeks vanuit Cloud Manager gaf de optie voor het dehiberneren/hberneren van de omgeving van een Sandbox-programma niet weer.

* De knoppen Annuleren en Opslaan op de pagina Bewerken zonder productiepijplijn zijn niet altijd zichtbaar.

* Bepaalde fouten in het proces van de codekwaliteit kunnen ertoe leiden dat het logbestand niet correct wordt gegenereerd.

* Bij het maken van een nieuw programma retourneert de voorgestelde naam soms een duplicaat van een bestaande programmanaam.

* Sommige logboeken van grote pijpleidingsstappen konden niet constant door het gebruikersinterface worden gedownload.

* De validatie van omgevingsnamen had een off-by-one fout.

* Op de pagina Milieu&#39;s worden soms publicatie- en verzendingssegmenten weergegeven wanneer er geen aanwezig was.