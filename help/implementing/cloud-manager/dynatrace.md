---
title: Dynatrace
description: Meer informatie over het gebruik van Dynatrace met AEM as a Cloud Service
exl-id: b58c8b82-a098-4d81-bc36-664e890c8f66
solution: Experience Manager
feature: Log Files, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '577'
ht-degree: 0%

---

# Dynatrace {#dynatrace}

Adobe biedt de mogelijkheid om Dynatrace te gebruiken om AEM as a Cloud Service te bewaken als onderdeel van de implementatie van bedrijven, de oorzaak van mogelijke problemen te identificeren en actie te ondernemen om deze problemen indien nodig op te lossen.

Met Dynatrace kunt u naadloze waarneming krijgen voor al uw AEM-toepassingen. Dynatrace ontdekt uw AEM-apps en toont hun paden, van website tot container tot cloudservice, om de gebruikerservaring te onthullen. Intertwined met end-to-end sporen over elke rij en Reëel Toezicht van het Gebruik, neem uw AEM inhoud-geleide ervaringen tot het volgende niveau zonder hiaten of dode vlekken. Als er anomalieën optreden, stelt Dynatrace deze in real-time vast met de Davis AI-engine. Het benadrukt de worteloorzaak neer aan de gebroken code alvorens uw klanten worden beïnvloed, die de gemiddelde tijd minimaliseren om te herstellen.

Meer over Dynatrace leren, zie de [&#x200B; integratie van de Dienst van de Wolk van Adobe AEM &#x200B;](https://www.dynatrace.com/hub/detail/adobe-experience-manager-1/).

![&#x200B; de auteur en de metriek van uitgeversprestaties van AEM &#x200B;](/help/implementing/cloud-manager/assets/dynatrace-performance-metrics.png)

## Dynatrace integreren met AEM as a Cloud Service {#integrating-dynatrace-with-aem-as-a-cloud-service}

Dynatrace-klanten kunnen hun AEM-omgevingen controleren door connectiviteit aan te vragen via een ticket voor klantenondersteuning.

De details die voor connectiviteitsverzoeken worden vereist worden hieronder beschreven:

| **Gebied** | **Beschrijving** |
|---|---|
| [!DNL Dynatrace Environment URL] | URL voor uw Dynatrace-omgeving.<br><br> voor klanten van Dynatrace SaaS, is het formaat `https://<your-environment-id>.live.dynatrace.com`.<br><br> Voor Dynatrace Managed-klanten is de indeling `https://<your-managed-url>/e/<environmentId>` |
| [!DNL Dynatrace Environment ID] | Je Dynatrace-omgeving-id. Zie [&#x200B; hoe krijg ik mijn Gegevens van de Verbinding van Dynatrace?](#how-do-i-get-my-dynatrace-connection-details) voor hoe u het kunt ophalen. |
| [!DNL Dynatrace Environment Token] | Uw Dynatrace-omgevingstoken. Zie [&#x200B; hoe krijg ik mijn Gegevens van de Verbinding van Dynatrace?](#how-do-i-get-my-dynatrace-connection-details) voor hoe u het kunt ophalen.<br><br> Dit teken zou als geheim moeten worden beschouwd, zodat gebruik aangewezen veiligheidspraktijken. Bijvoorbeeld, beschermt het wachtwoord het in een website zoals **zerobin.net**, die het kaartje van de klantensteun, samen met het wachtwoord kan van verwijzingen voorzien. |
| [!DNL Dynatrace API access token] | Het API toegangstoken van uw milieu van Dynatrace. Zie [&#x200B; tot een de toegangstoken van Dynatrace API &#x200B;](#create-dynatrace-access-token) voor hoe te om het tot stand te brengen.<br><br> Dit teken zou als geheim moeten worden beschouwd zodat gebruik aangewezen veiligheidspraktijken. Bijvoorbeeld, beschermt het wachtwoord het in een website zoals **zerobin.net**, die het kaartje van de klantensteun, samen met het wachtwoord kan van verwijzingen voorzien.<br> |
| [!DNL Dynatrace ActiveGate Port] | De Dynatrace ActiveGate-poort waarmee de AEM-integratie verbinding moet maken.<br><br> Deze haven wordt slechts vereist voor Beheerde Dynatrace. |
| [!DNL Dynatrace ActiveGate Network Zone] | Uw [&#x200B; het netwerkstreek van Dynatrace ActiveGate &#x200B;](https://docs.dynatrace.com/docs/manage/network-zones) om AEM controlegegevens over gegevenscentra en netwerkgebieden efficiënt te leiden.<br><br> Nota: Een het netwerkstreek van Dynatrace ActiveGate is facultatief. |
| [!DNL AEM Environment IDs] | De AEM-omgeving-id of -id&#39;s die Dynatrace moet controleren. |

>[!NOTE]
>
>Als Dynatrace eenmaal is geïntegreerd, worden de gegevens niet meer naar andere APM-gereedschappen, zoals New Relic, verzonden als deze voorheen was ingeschakeld.

## Veelgestelde vragen {#faq}

### Welke licentie heb ik nodig voor Dynatrace AEM Monitoring? {#which-license-do-i-need-for-AEM-monitoring}

Voor Dynatrace AEM-bewaking is een Dynatrace-licentie vereist. Het verlenen van vergunningen van Dynatrace AEM is gebaseerd op [&#x200B; volledig-stapel controle voor containers Kubernetes &#x200B;](https://docs.dynatrace.com/docs/shortlink/dps-hosts#gib-hour-calculation-for-containers-and-application-only-monitoring). De geheugengrootten van gecontroleerde AEM-containers (auteur- en uitgeversservices) worden automatisch gedetecteerd.

De Adobe-implementatiespecificaties per AEM-omgeving zijn:

* Productie: gemiddeld 4 containers, 16 GB geheugen elk
* Niet-productie: gemiddeld 4 containers, 8 GB geheugen elk

Meer over Dynatrace verlenen van vergunningen, zie het [&#x200B; Abonnement van het Platform van Dynatrace &#x200B;](https://docs.dynatrace.com/docs/shortlink/dynatrace-platform-subscription).

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
1. Ga naar **[!DNL Access tokens]** en klik op de optie **[!DNL Generate new token]** .
1. Definieer een [!DNL token name] .
1. Stel het tokenbereik in op **[!DNL PaaS integration - Installer download]** .
1. Selecteer **[!DNL Generate token]** .
1. Kopieer het gegenereerde toegangstoken en sla deze op een veilige plaats op.





