---
title: Dynatrace
description: Meer informatie over het gebruik van Dynatrace met AEM as a Cloud Service
exl-id: b58c8b82-a098-4d81-bc36-664e890c8f66
solution: Experience Manager
feature: Log Files, Developing
role: Admin, Architect, Developer
source-git-commit: 500e1b78fb9688601848fc17f312fc23be83bcb0
workflow-type: tm+mt
source-wordcount: '586'
ht-degree: 0%

---

# Dynatrace {#dynatrace}

Adobe biedt de mogelijkheid om Dynatrace te gebruiken om AEM as a Cloud Service te bewaken als onderdeel van de implementatie van een onderneming, de oorzaak van mogelijke problemen te identificeren en actie te ondernemen om deze indien nodig te verhelpen.

Met Dynatrace kunt u naadloze waarneming krijgen voor al uw AEM toepassingen. Dynatrace biedt uitgebreide zichtbaarheid in de ervaring van eindgebruikers door uw AEM toepassingen automatisch te detecteren en hun afhankelijkheden van de website naar de container naar de cloudservice te visualiseren. Intertwined met de sporen van begin tot eind over elke rij en Reëel Toezicht van het Gebruik, neem uw AEM inhoud-geleide ervaringen tot het volgende niveau zonder hiaten of dode vlekken. Als er anomalieën optreden, worden deze door Dynatrace in realtime gediagnosticeerd met de Davis AI-engine en wordt de oorzaak van de beschadigde code aangegeven voordat de problemen bij uw klanten optreden. Hierdoor wordt de gemiddelde hersteltijd tot een minimum beperkt.

Meer over Dynatrace leren, zie de [ integratie van AEM Cloud Service van de Adobe ](https://www.dynatrace.com/hub/detail/adobe-experience-manager-1/).

![ AEM auteur en uitgeverspreidingsmetriek ](/help/implementing/cloud-manager/assets/dynatrace-performance-metrics.png)

## Dynatrace integreren met AEM as a Cloud Service {#integrating-dynatrace-with-aem-as-a-cloud-service}

Dynatrace-klanten kunnen hun AEM bekijken door connectiviteit aan te vragen via een ticket voor klantenondersteuning.

De details die voor connectiviteitsverzoeken worden vereist worden hieronder beschreven:

| **Gebied** | **Beschrijving** |
|---|---|
| [!DNL Dynatrace Environment URL] | URL voor uw Dynatrace-omgeving.<br><br> voor klanten van Dynatrace SaaS, is het formaat `https://<your-environment-id>.live.dynatrace.com`.<br><br> Voor Dynatrace Managed-klanten is de indeling `https://<your-managed-url>/e/<environmentId>` |
| [!DNL Dynatrace Environment ID] | Je Dynatrace-omgeving-id. Zie [ hoe krijg ik mijn Gegevens van de Verbinding van Dynatrace?](#how-do-i-get-my-dynatrace-connection-details) voor hoe u dit kunt verkrijgen. |
| [!DNL Dynatrace Environment Token] | Uw Dynatrace-omgevingstoken. Zie [ hoe krijg ik mijn Gegevens van de Verbinding van Dynatrace?](#how-do-i-get-my-dynatrace-connection-details) voor hoe u dit kunt verkrijgen.<br><br> dit zou als geheim moeten worden beschouwd, zo gebruik aangewezen veiligheidspraktijken. Bijvoorbeeld, beschermt het wachtwoord het in een website zoals **zerobin.net**, die het kaartje van de klantensteun, samen met het wachtwoord kan van verwijzingen voorzien. |
| [!DNL Dynatrace API access token] | Het API toegangstoken van uw milieu van Dynatrace. Zie [ tot een toegangstoken van Dynatrace API ](#create-dynatrace-access-token) voor hoe te om dit tot stand te brengen.<br><br> dit zou als geheim moeten worden beschouwd zodat gebruik aangewezen veiligheidspraktijken. Bijvoorbeeld, beschermt het wachtwoord het in een website zoals **zerobin.net**, die het kaartje van de klantensteun, samen met het wachtwoord kan van verwijzingen voorzien.<br><br> Nota: Dit wordt slechts vereist voor Beheerde Dynatrace. |
| [!DNL Dynatrace ActiveGate Port] | De Dynatrace ActiveGate-poort waarmee de AEM verbinding moet maken.<br><br> Nota: Dit wordt slechts vereist voor Beheerde Dynatrace. |
| [!DNL Dynatrace ActiveGate Network Zone] | Uw [ het netwerkstreek van Dynatrace ActiveGate ](https://docs.dynatrace.com/docs/manage/network-zones) om AEM controlegegevens over gegevenscentra en netwerkgebieden efficiënt te leiden.<br><br> Nota: Een het netwerkstreek van Dynatrace ActiveGate is facultatief. |
| [!DNL AEM Environment ID(s)] | De AEM milieu-id(s) voor Dynatrace om te controleren. |

>[!NOTE]
>
>Als Dynatrace eenmaal is geïntegreerd, gaan de gegevens niet meer naar andere APM-gereedschappen, zoals New Relic, als deze voorheen was ingeschakeld.

## Veelgestelde vragen {#faq}

### Welke licentie heb ik nodig voor Dynatrace AEM Monitoring? {#which-license-do-i-need-for-AEM-monitoring}

Voor Dynatrace AEM monitoring is een Dynatrace-licentie vereist. Dynatrace AEM verlenen van vergunningen is gebaseerd op [ volledig-stapel controle voor containers Kubernetes ](https://docs.dynatrace.com/docs/shortlink/dps-hosts#gib-hour-calculation-for-containers-and-application-only-monitoring). De geheugengrootte van gecontroleerde AEM containers (auteur en uitgeversdiensten) wordt automatisch ontdekt.

De implementatiespecificaties voor de Adobe per AEM omgeving zijn:

* Productie: gemiddeld 4 containers, 16 GB geheugen elk
* Niet-productie: gemiddeld 4 containers, 8 GB geheugen elk

Meer over Dynatrace verlenen van vergunningen, zie het [ Abonnement van het Platform van Dynatrace ](https://docs.dynatrace.com/docs/shortlink/dynatrace-platform-subscription).

### Hoe krijg ik mijn Dynatrace Connection Details? {#how-do-i-get-my-dynatrace-connection-details}

1. Voer het volgende API-verzoek uit naar uw Dynatrace-omgeving:

   ```
   curl -X GET "<environmentUrl>/api/v1/deployment/installer/agent/connectioninfo" -H "accept: application/json" -H "Authorization: Api-Token <accessToken>"
   ```


   Vervang `<environmentUrl>` door de URL van de Dynatrace-omgeving en `<accessToken>` door het API-toegangstoken dat u hebt gemaakt.

1. Kopieer de `<environmentId>` en `<environmentToken>` van de antwoordlading en bewaar ze op een beveiligde plaats.

   ```
   {
      "tenantUUID": "<environmentId>",
      "tenantToken": "<environmentToken>",
      "communicationEndpoints": [...]
   }
   ```

### Een Dynatrace API-toegangstoken maken {#create-dynatrace-access-token}

1. Meld u aan bij uw Dynatrace-omgeving.
1. Ga naar **[!DNL Access tokens]** en selecteer **[!DNL Generate new token]** .
1. Definieer een [!DNL token name] .
1. Stel het tokenbereik in op **[!DNL PaaS integration - Installer download]** .
1. Selecteer **[!DNL Generate token]** .
1. Kopieer het gegenereerde toegangstoken en sla deze op een veilige plaats op.





