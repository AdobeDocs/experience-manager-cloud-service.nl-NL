---
title: Dynatrace
description: Meer informatie over het gebruik van Dynatrace met AEM as a Cloud Service
exl-id: b58c8b82-a098-4d81-bc36-664e890c8f66
solution: Experience Manager
feature: Log Files, Developing
role: Admin, Architect, Developer
source-git-commit: 8d5d8910a906e2adf17fa9c75f17634602c2e0b9
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 0%

---

# Dynatrace {#dynatrace}

Adobe biedt de mogelijkheid om Dynatrace te gebruiken om toezicht te houden op AEM as a Cloud Service als onderdeel van de implementatie van een onderneming, de oorzaak van mogelijke problemen te identificeren en actie te ondernemen om deze indien nodig te verhelpen.

Met Dynatrace kunt u naadloze waarneming krijgen voor al uw AEM toepassingen. Dynatrace biedt uitgebreide zichtbaarheid in de ervaring van eindgebruikers door uw AEM toepassingen automatisch te detecteren en hun afhankelijkheden van de website naar de container naar de cloudservice te visualiseren. Intertwined met de sporen van begin tot eind over elke rij en Reëel Toezicht van het Gebruik, neem uw AEM inhoud-geleide ervaringen tot het volgende niveau zonder hiaten of dode vlekken. Als er anomalieën optreden, worden deze door Dynatrace in realtime gediagnosticeerd met de Davis AI-engine en wordt de oorzaak van de beschadigde code aangegeven voordat de problemen bij uw klanten optreden. Hierdoor wordt de gemiddelde hersteltijd tot een minimum beperkt.

Ga voor meer informatie over Dynatrace naar de [Integratie van Adobe AEM Cloud Service](https://www.dynatrace.com/hub/detail/adobe-experience-manager-1/).

![Prestatiegegevens van AEM auteur en uitgever](/help/implementing/cloud-manager/assets/dynatrace-performance-metrics.png)

## Dynatrace integreren met AEM as a Cloud Service {#integrating-dynatrace-with-aem-as-a-cloud-service}

Dynatrace-klanten kunnen hun AEM bekijken door connectiviteit aan te vragen via een ticket voor klantenondersteuning.

De details die voor connectiviteitsverzoeken worden vereist worden hieronder beschreven:

| **Veld** | **Beschrijving** |
|---|---|
| [!DNL Dynatrace Environment URL] | URL voor uw Dynatrace-omgeving.<br><br>Voor Dynatrace SaaS-klanten is de indeling `https://<your-environment-id>.live.dynatrace.com`.<br><br>Voor Dynatrace Managed-klanten is de indeling `https://<your-managed-url>/e/<environmentId>` |
| [!DNL Dynatrace Environment ID] | Je Dynatrace-omgeving-id. Zie [Hoe krijg ik mijn Dynatrace Connection Details?](#how-do-i-get-my-dynatrace-connection-details) voor hoe dit te krijgen. |
| [!DNL Dynatrace Environment Token] | Uw Dynatrace-omgevingstoken. Zie [Hoe krijg ik mijn Dynatrace Connection Details?](#how-do-i-get-my-dynatrace-connection-details) voor hoe dit te krijgen.<br><br>Dit moet als een geheim worden beschouwd, dus gebruik passende veiligheidspraktijken. Het wachtwoord beveiligt het bijvoorbeeld in een website, zoals **zerobin.net**, waarnaar het klantenondersteuningsticket kan verwijzen, samen met het wachtwoord. |
| [!DNL Dynatrace API access token] | Het API toegangstoken van uw milieu van Dynatrace.  Zie [Een Dynatrace API-toegangstoken maken](#create-dynatrace-access-token) voor hoe u dit kunt maken.<br><br>Dit moet als een geheim worden beschouwd, dus gebruik maken van passende veiligheidspraktijken. Het wachtwoord beveiligt het bijvoorbeeld in een website, zoals **zerobin.net**, waarnaar het klantenondersteuningsticket kan verwijzen, samen met het wachtwoord.<br><br>Opmerking: dit is alleen vereist voor Dynatrace Managed. |
| [!DNL Dynatrace ActiveGate Port] | De Dynatrace ActiveGate-poort waarmee de AEM verbinding moet maken.<br><br>Opmerking: dit is alleen vereist voor Dynatrace Managed. |
| [!DNL Dynatrace ActiveGate Network Zone] | Uw [Dynatrace ActiveGate-netwerkzone](https://docs.dynatrace.com/docs/manage/network-zones) om AEM controlegegevens efficiënt over gegevenscentra en netwerkgebieden te leiden.<br><br>Opmerking: een Dynatrace ActiveGate-netwerkzone is optioneel. |
| [!DNL AEM Environment ID(s)] | De AEM milieu-id(s) voor Dynatrace om te controleren. |

>[!NOTE]
>
>Als Dynatrace eenmaal is geïntegreerd, gaan de gegevens niet meer naar andere APM-gereedschappen, zoals New Relic, als deze voorheen was ingeschakeld.

## Veelgestelde vragen {#faq}

### Welke licentie heb ik nodig voor Dynatrace AEM Monitoring? {#which-license-do-i-need-for-AEM-monitoring}

Voor Dynatrace AEM monitoring is een Dynatrace-licentie vereist. Dynatrace AEM-licenties zijn gebaseerd op [full-stack controle voor Kubernetes containers](https://docs.dynatrace.com/docs/shortlink/dps-hosts#gib-hour-calculation-for-containers-and-application-only-monitoring). De geheugengrootte van gecontroleerde AEM containers (auteur en uitgeversdiensten) wordt automatisch ontdekt.

De implementatiespecificaties voor de Adobe per AEM omgeving zijn:

* Productie: gemiddeld 4 containers, 16 GB geheugen elk
* Niet-productie: gemiddeld 4 containers, 8 GB geheugen elk

Voor meer informatie over Dynatrace-licenties raadpleegt u de [Dynatrace Platform Subscription](https://docs.dynatrace.com/docs/shortlink/dynatrace-platform-subscription).

### Hoe krijg ik mijn Dynatrace Connection Details? {#how-do-i-get-my-dynatrace-connection-details}

1. Voer het volgende API-verzoek uit naar uw Dynatrace-omgeving:

   ```
   curl -X GET "<environmentUrl>/api/v1/deployment/installer/agent/connectioninfo" -H "accept: application/json" -H "Authorization: Api-Token <accessToken>"
   ```


   Vervangen `<environmentUrl>` met uw Dynatrace-omgeving URL en `<accessToken>` met uw gemaakte API-toegangstoken.

1. De `<environmentId>` en `<environmentToken>` van de antwoordlading en bewaar ze op een beveiligde plaats.

   ```
   {
      "tenantUUID": "<environmentId>",
      "tenantToken": "<environmentToken>",
      "communicationEndpoints": [...]
   }
   ```

### Een Dynatrace API-toegangstoken maken {#create-dynatrace-access-token}

1. Meld u aan bij uw Dynatrace-omgeving.
1. Ga naar **[!DNL Access tokens]** en selecteert u **[!DNL Generate new token]**.
1. Een [!DNL token name].
1. Tokenbereik instellen op **[!DNL PaaS integration - Installer download]**.
1. Selecteren **[!DNL Generate token]**.
1. Kopieer het gegenereerde toegangstoken en sla deze op een veilige plaats op.





