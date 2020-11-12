---
title: Release-aantekeningen voor de release 2020.10.0 [!DNL Adobe Experience Manager] van een Cloud Service.
description: '[!DNL Adobe Experience Manager] als opmerkingen bij de release van de Cloud Service voor 2020.10.0.'
translation-type: tm+mt
source-git-commit: f0ac4b511fefa0bcde8d59c416da638941cd52ad
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---


# Opmerkingen bij de release [!DNL Adobe Experience Manager] als Cloud Service {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release [!DNL Experience Manager] als Cloud Service 2020.10.0 beschreven.

## Cloud Manager {#cloud-manager}

* De pagina Omgevingen is opnieuw ontworpen.

* In gedownneerde omgevingen wordt nu een aparte status weergegeven in Cloud Manager wanneer deze worden gehiberneerd.

* De buildcontainer van Cloud Manager ondersteunt nu het compileren van projecten met behulp van Java 8 of Java 11. Ondersteuning voor Java 11 wordt geleverd door het Maven-toolketensysteem.

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

