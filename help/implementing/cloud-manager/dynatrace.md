---
title: Dynatrace
description: Leer hoe u Dynatrace gebruikt met AEM as a Cloud Service
exl-id: b58c8b82-a098-4d81-bc36-664e890c8f66
source-git-commit: fec3aa6debec49014406ab241c3ce0338ec5a1d2
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 0%

---

# Dynatrace {#dynatrace}

Adobe biedt de mogelijkheid om gebruik te maken van Dynatrace om AEM as a Cloud Service te controleren als onderdeel van de implementatie van een bedrijf, de oorzaak van mogelijke problemen te identificeren en actie te ondernemen om deze problemen indien nodig te verhelpen.

Met Dynatrace krijgt u een naadloze waarneming voor al uw AEM toepassingen. Dynatrace biedt uitgebreide zichtbaarheid in de gebruikerservaring door uw AEM toepassingen automatisch te detecteren en hun afhankelijkheden van de website naar de container naar de cloudservice zichtbaar te maken. Intertwined met de sporen van begin tot eind over elke rij en Echte Controle van de Gebruiker, neem uw AEM inhoud-geleide ervaringen aan het volgende niveau zonder hiaten of dode vlekken. Als er anomalieën optreden, worden deze door Dynatrace in realtime gediagnosticeerd met de Davis AI-engine en wordt de oorzaak van de beschadigde code aangegeven voordat de klant wordt beïnvloed. Hierdoor wordt de gemiddelde hersteltijd tot een minimum beperkt.

Voor meer informatie over Dynatrace raadpleegt u de [Integratie van Adobe AEM Cloud Service](https://www.dynatrace.com/hub/detail/adobe-experience-manager-1/).

![Prestatiegegevens van AEM auteur en uitgever](/help/implementing/cloud-manager/assets/dynatrace-performance-metrics.png)

## Integratie van Dynatrace met AEM as a Cloud Service {#integrating-dynatrace-with-aem-as-a-cloud-service}

De klanten van de  kunnen hun AEM milieu&#39;s controleren door connectiviteit door een kaartje van de klantensteun te verzoeken.

De details die voor connectiviteitsverzoeken worden vereist worden hieronder beschreven:

| **Veld** | **Beschrijving** |
|---|---|
| [!DNL Dynatrace Environment URL] | De URL van uw Dynatrace-omgeving.<br><br>Voor klanten van Dynatrace SaaS is de indeling `https://<your-environment-id>.live.dynatrace.com`.<br><br>Voor klanten met Dynatrace Managed is de indeling `https://<your-managed-url>/e/<environmentId>` |
| [!DNL Dynatrace Environment ID] | Uw ID van de dynatraciemilieu. Zie [Informatie over de dynamische omgeving ophalen](#get-dynatrace-env-info) voor hoe dit te krijgen. |
| [!DNL Dynatrace Environment Token] | Uw Dynatrace-omgevingstoken. Zie [Informatie over de dynamische omgeving ophalen](#get-dynatrace-env-info) voor hoe dit te krijgen.<br><br>Dit moet als een geheim worden beschouwd, dus gebruik passende veiligheidspraktijken. Het wachtwoord beveiligt het bijvoorbeeld in een website, zoals **zerobin.net**, waarnaar het klantenondersteuningsticket kan verwijzen, samen met het wachtwoord. |
| [!DNL Dynatrace API access token] | Het API toegangstoken van uw milieu van de Naslaggids.  Zie [Een API-toegangstoken voor dynamisch maken](#create-dynatrace-access-token) voor hoe u dit kunt maken.<br><br>Dit moet als een geheim worden beschouwd, dus gebruik maken van passende veiligheidspraktijken. Het wachtwoord beveiligt het bijvoorbeeld in een website, zoals **zerobin.net**, waarnaar het klantenondersteuningsticket kan verwijzen, samen met het wachtwoord.<br><br>Opmerking: dit is alleen vereist voor Dynatrace Managed. |
| [!DNL Dynatrace ActiveGate Port] | De ActiveGate-poort van de Dynatrace waarmee de AEM moet worden verbonden.<br><br>Opmerking: dit is alleen vereist voor Dynatrace Managed. |
| [!DNL Dynatrace ActiveGate Network Zone] | Uw [Dynatrace ActiveGate-netwerkzone](https://docs.dynatrace.com/docs/manage/network-zones) om AEM controlegegevens efficiënt over gegevenscentra en netwerkgebieden te leiden.<br><br>Opmerking: een ActiveGate-netwerkzone van Dynarace is optioneel. |
| [!DNL AEM Environment ID(s)] | De AEM milieu-id(s) voor Dynatrace om te controleren. |

>[!NOTE]
>
>Als Dynatrach eenmaal is geïntegreerd, worden de gegevens niet meer doorgevoerd naar andere APM-gereedschappen, zoals New Relic, als deze voorheen waren ingeschakeld.


## Een API-toegangstoken voor dynamisch maken {#create-dynatrace-access-token}

1. Meld u aan bij uw Dynatrace-omgeving.
1. In de [!DNL Dynatrace] menu, ga naar [!DNL Manage] > [!DNL Access tokens].
1. Selecteren [!DNL Generate new token].
1. Een [!DNL token name].

1. Optioneel: een [!DNL expiration date]. Zorg ervoor dat u een nieuwe token genereert voordat deze verloopt.
1. Stel de [!DNL token scope] tot [!DNL PaaS integration - Installer download]
1. Selecteren [!DNL Generate token].
1. Kopieer het gegenereerde toegangstoken en sla deze op een veilige plaats op.


## Informatie over de dynamische omgeving ophalen {#get-dynatrace-env-info}

1. Voer het volgende API verzoek aan uw milieu van de Varkenshaar uit:

`curl -X GET "<environmentUrl>/api/v1/deployment/installer/agent/connectioninfo" -H "accept: application/json" -H "Authorization: Api-Token <accessToken>"`

\ vervangen&lt;environmenturl> met de URL en \ van uw dynamische omgeving&lt;accesstoken> met uw gemaakte API-toegangstoken.

1. Kopieer de \&lt;environmentid> en \&lt;environmenttoken> van de antwoordlading en bewaar ze op een beveiligde plaats.

```
{
   "tenantUUID": "<environmentId>",
   "tenantToken": "<environmentToken>",
   "communicationEndpoints": [
   ... 
   ],
   "formattedCommunicationEndpoints": "<endpoints>" 
}
```


