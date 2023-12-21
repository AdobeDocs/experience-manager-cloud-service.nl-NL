---
title: Dynatrace OneAgent
description: Leer hoe u de OneAgent van Dynatrace met AEM as a Cloud Service
source-git-commit: 9379e6a1ec323ff4f05e994e9265da1363b4a3df
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 0%

---


# Dynatrace OneAgent {#dynatrace-oneagent}

Adobe verstrekt de capaciteit om de OneAgent van Dynatrace te gebruiken om AEM as a Cloud Service als deel van een ondernemingsplaatsing te controleren, de oorzaak van om het even welke potentiële kwesties te identificeren, en actie te voeren om hen te verhelpen zoals nodig. <!-- When GA, add: Read this [Dynatrace article](https://www.dynatrace.com/hub/detail/adobe-experience-manager/) about AEM monitoring to learn more. -->

## OneAgent integreren met AEM as a Cloud Service {#integrating-oneagent-with-aem-as-a-cloud-service}

Dynatrace OneAgent-klanten kunnen hun AEM gebruiken controleren door connectiviteit aan te vragen via een ticket voor klantenondersteuning.

De details die voor connectiviteitsverzoeken worden vereist worden hieronder beschreven:

| **Veld** | **Beschrijving** |
|---|---|
| URL van dynamische omgeving | De URL van uw Dynatrace-omgeving.<br><br>Voor klanten van Dynatrace SaaS is de indeling `https://<you-environment-id>.live.dynatrace.com`.<br><br>Voor klanten met Dynatrace Managed is de indeling `https://<your-managed-url>/e/<environmentId>` |
| ID Dynatracie | Uw milieu-id van de Dynatrace, die u vindt in de URL van het milieu |
| Dynatrace Environment Token | Uw OneAgent-omgevingstoken. Raadpleeg de documentatie bij Dynatrace voor meer informatie.<br><br>Dit moet als een geheim worden beschouwd, dus gebruik passende veiligheidspraktijken. Het wachtwoord beveiligt het bijvoorbeeld in een website, zoals **zerobin.net**, waarnaar het klantenondersteuningsticket kan verwijzen, samen met het wachtwoord. |
| Toegangstoken API van Dynatrace | Het API toegangstoken van uw milieu van de Naslaggids. Raadpleeg de documentatie bij Dynatrace voor meer informatie.<br><br>Dit moet als een geheim worden beschouwd, dus gebruik maken van passende veiligheidspraktijken. Het wachtwoord beveiligt het bijvoorbeeld in een website, zoals **zerobin.net**, waarnaar het klantenondersteuningsticket kan verwijzen, samen met het wachtwoord.<br><br>Opmerking: dit is alleen vereist voor Dynatrace Managed. |
| Dynatrace ActiveGate-poort | Uw ActiveGate-poort van Dynatrace waarmee OneAgent verbinding moet maken.<br><br>Opmerking: dit is alleen vereist voor Dynatrace Managed. |
| AEM milieu-id(&#39;s) | De AEM milieu-id(s) voor Dynatrace om te controleren. |


