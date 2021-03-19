---
title: Opmerkingen bij de release voor Cloud Manager in AEM als Cloud Service Release 2020.11.0
description: Opmerkingen bij de release voor Cloud Manager in AEM als Cloud Service Release 2020.11.0
feature: Geen informatie
translation-type: tm+mt
source-git-commit: 0f2b7176b44bb79bdcd1cecf6debf05bd652a1a1
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 2%

---


# Opmerkingen bij de release voor Cloud Manager in Adobe Experience Manager als Cloud Service 2020.11.0 {#release-notes}

Deze pagina bevat de releaseopmerkingen voor Cloud Manager in AEM als Cloud Service 2020.11.0.

## Releasedatum {#release-date}

De releasedatum voor Cloud Manager in AEM als Cloud Service 2020.11.0 is 12 november 2020.

## Cloud Manager {#cloud-manager}

### Wat is er nieuw?{#what-is-new}

* Een nieuwe menuoptie **Local Login** is nu beschikbaar aan gebruikers van de milieu menuopties op de kaart van het Milieu en de Summiere pagina&#39;s van Milieu.
Raadpleeg [Omgevingen beheren](/help/implementing/cloud-manager/manage-environments.md#login-locally) voor meer informatie.

* Het tabblad **Leren** in Cloud Manager is vernieuwd en bevat nieuwe afbeeldingen in de gebruikersinterface.

### Opgeloste problemen {#bug-fixes-cloud-manager}

* Voor het laden van afhankelijkheden die zijn uitgevoerd voordat de build werd uitgevoerd, moest een Maven-plug-in worden gedownload.
* Met de koppeling in de voettekst van Cloud Manager om een taal te selecteren, gaat u nu naar de juiste locatie.
* Soms wordt tijdens het scannen van code het SonarQube-proces niet gestart. Dit wordt nu automatisch gedetecteerd en er wordt geprobeerd opnieuw te starten.
* Alle bestaande productiepijpleidingen worden automatisch ingeschakeld met behulp van de stap Experience Audit.
