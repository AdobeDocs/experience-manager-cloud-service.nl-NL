---
title: Screeningmeldingsservice in as a Cloud Service schermen
description: Deze pagina beschrijft hoe te om de Dienst van het Bericht in as a Cloud Service Schermen te vormen.
index: true
exl-id: 74215a70-45c8-4b7f-ba30-60c332de07e9
source-git-commit: 69798b1ac3758d37c4e2f480ccc23bae24d6a814
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---

# Service voor schermmeldingen {#notification-service}

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

Als u de rapporttijd als 5 am plaatst en pingelt onderbreking als 1 uur, dan als uw apparaat van de Schermen niet tussen 4:00 am - 5:00 am pingelt, zult u een e-mailbericht ontvangen die apparateninactiviteit bevestigt.
