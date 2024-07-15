---
title: Screens Notification Service in Screens as a Cloud Service
description: Deze pagina beschrijft hoe te om de Dienst van het Bericht in Screens as a Cloud Service te vormen.
index: true
exl-id: 74215a70-45c8-4b7f-ba30-60c332de07e9
feature: Developing Screens
role: Admin, Developer, User
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---

# Screens Notification Service {#notification-service}

## Inleiding {#introduction}

### Overzicht

Met AEM Screens Notifications Service kunnen beheerders een rapport ontvangen met een lijst van alle AEM Screens-spelers die niet voor een configureerbare periode in een e-mailbericht hebben gepingeld.

### Hoe te vormen

In AEM Screens Cloud kunnen klanten een rapport aanvragen over de status van inactiviteit van een apparaat door een ondersteuningsticket te maken met de volgende informatie:

* Naam klant
* IMS OrgID
* Planningsfrequentie: geef een tijd of frequentie op in uren (bijvoorbeeld 1) waarop deze monitor e-mailberichten moet verzenden.
* Ping Timeout: specificeert het interval in notulen waarna een apparaat als niet bereikbaar zou moeten worden beschouwd.
* E-mailadres(sen): E-mailadres(sen) waar het rapport wordt verzonden

>[!NOTE]
>De speler wordt alleen in e-mails gemeld als het apparaat dat niet is gepingeld voor de opgegeven pingelt-time-out op het moment dat de e-mail wordt gegenereerd.

### Voorbeeld: hoofdletter gebruiken

Als u de rapporttijd als 5 am plaatst en pingelt onderbreking als 1 uur, dan als uw Screens apparaat niet tussen 4:00 uur - 5:00 am pingelt, zult u een e-mailbericht ontvangen die apparateninactiviteit bevestigen.
