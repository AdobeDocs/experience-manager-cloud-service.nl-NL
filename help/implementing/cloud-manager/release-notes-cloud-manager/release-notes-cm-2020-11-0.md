---
title: Opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service versie 2020.11.0
description: Opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service versie 2020.11.0
feature: Release Information
exl-id: e2acf515-d339-4d2b-9b62-09c1dab1ffac
source-git-commit: 09d5d125840abb6d6cc5443816f3b2fe6602459f
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 2%

---

# Opmerkingen bij de release voor Cloud Manager in Adobe Experience Manager as a Cloud Service 2020.11.0 {#release-notes}

Deze pagina bevat een overzicht van de opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service 2020.11.0.

## Releasedatum {#release-date}

De releasedatum voor Cloud Manager in AEM as a Cloud Service 2020.11.0 is 12 november 2020.

## Cloud Manager {#cloud-manager}

### Wat is er nieuw? {#what-is-new}

* Een nieuwe menuoptie **Lokale aanmelding** is nu beschikbaar voor gebruikers via de opties in het menu Omgeving op de pagina&#39;s Overzicht van de omgevingskaart en het overzicht van omgevingen.
Zie [Omgevingen beheren](/help/implementing/cloud-manager/manage-environments.md#login-locally) voor meer informatie .

* De **Meer informatie** is vernieuwd met nieuwe afbeeldingen in de gebruikersinterface.

### Opgeloste problemen {#bug-fixes-cloud-manager}

* Voor het laden van afhankelijkheden die zijn uitgevoerd voordat de build werd uitgevoerd, moest een Maven-plug-in worden gedownload.
* Met de koppeling in de voettekst van Cloud Manager om een taal te selecteren, gaat u nu naar de juiste locatie.
* Soms wordt tijdens het scannen van code het SonarQube-proces niet gestart. Dit wordt nu automatisch gedetecteerd en er wordt geprobeerd opnieuw te starten.
* Alle bestaande productiepijpleidingen worden automatisch ingeschakeld met behulp van de stap Experience Audit.
