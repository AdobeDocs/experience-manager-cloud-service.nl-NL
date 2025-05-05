---
title: Hoe te om Salesforce te integreren gebruikend OAuth 2.0 cliëntcredentiële stroom met AEM Forms?
description: Leer Salesforce met AEM Forms te integreren met behulp van OAuth 2.0 client credential flow. Er worden stappen weergegeven voor de integratie met AEM Forms Salesforce.
Keywords: Integration of Salesforce using OAuth 2.0 client credential flow, salesforce integration with oauth2 using client credential flow, salesforce and client credential integration, AEM Forms Salesforce integration
feature: Adaptive Forms, Form Data Model
role: User, Developer
exl-id: 2c2029ab-6fb4-41a6-846c-175c3a79d921
source-git-commit: 9eb15dda5f56938d686d0b863cb1ffa841f8228b
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 1%

---

# Adaptief formulier integreren met Salesforce {#configure-salesforce-with-ouath-2.0-client-credential}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/oauth2-client-credentials-flow-for-server-to-server-integration.html?lang=nl-NL) |
| AEM as a Cloud Service | Dit artikel |

Dankzij de integratie van Adobe Experience Manager (AEM) Forms met Salesforce kunnen organisaties processen stroomlijnen door hun mogelijkheden voor het maken en beheren van formulieren te verbinden met het Salesforce-platform. Door een adaptief formulier aan te sluiten met Salesforce, kunt u naadloze gegevensuitwisseling tussen de twee platforms tot stand brengen. Wanneer gebruikers formulieren verzenden, worden de gegevens automatisch gesynchroniseerd met Salesforce. Het zorgt ervoor dat alle klanteninformatie bijgewerkt en binnen het systeem gecentraliseerd is.

U kunt OAuth 2.0 cliëntgeloofsbrieven gebruiken om AEM Forms met de toepassing van Salesforce te integreren. OAuth 2.0 cliëntgeloofsbrieven zijn een standaard en veilige methode voor directe mededeling zonder gebruikersbetrokkenheid.

![ Werkschema terwijl het plaatsen van mededeling tussen AEM Forms en toepassing Salesforce ](/help/forms/assets/salesforce-workflow.png)

AEM Forms wisselt de aanmeldingsgegevens van de client uit (de sleutel van de consument en het consumentengeheim), die zijn gedefinieerd in de toepassing Salesforce waarmee verbinding wordt gemaakt, om een toegangstoken te verkrijgen.

AEM as a Cloud Service biedt verschillende mogelijkheden in het vak Acties verzenden voor het verwerken van verzonden formulieren. U kunt meer over deze opties leren in het [ AanpassingsVorm voorlegt Artikel van de Actie ](/help/forms/configure-submit-actions-core-components.md).

Er zijn veelvoudige voordelen om OAuth 2.0 cliëntgeloofsbrieven voor authentificatie over de authentificatie van de Stroom van de Code van de Vergunning te gebruiken:

* OAuth 2.0 de authentificatie van de cliëntgeloofsbrieven staat meer dan vijf verbindingen per gebruiker toe.
* AEM gegevensbronconfiguratie werkt verder aan deactivering, toegangsveranderingen, wachtwoordupdate voor een AEM gebruiker.

## Vereisten {#prerequisites}

Voordat u de communicatie tussen een Salesforce-toepassing en een AEM omgeving instelt:

* Creeer a [ Salesforce verbonden app met OAuth 2.0 stroom van de cliëntcredentie ](https://help.salesforce.com/s/articleView?id=sf.connected_app_client_credentials_setup.htm&amp;type=5) en een slechts API-gebruiker voor uw organisatie en verkrijg de sleutel van de consument en het consumentengeheim voor app.

* Zorg ervoor dat het Swagger-bestand op de juiste wijze is geconfigureerd zodat het overeenkomt met de API&#39;s van uw organisatie. Alternatief, kunt u verkiezen om [ tot een dossier van de Swagger ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/forms/integrate-with-salesforce/describe-rest-api.html?lang=nl-NL) van het kras te leiden, dat voor gebruik in uw AEM milieu wordt gemaakt.


## Salesforce-toepassing configureren met OAuth 2.0 Client Credential-stroom {#steps-to-create-aem-datasource-configuration}

Voer de volgende stappen uit om Adaptief formulier te verbinden met de Salesforce-toepassing met OAuth 2.0-instellingen voor clientverificatie:

1. Meld u aan bij de instantie Auteur.
1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Data Sources]** .
1. Selecteer de configuratiemap.
1. Klik op **[!UICONTROL Create]** en **[!UICONTROL Create Data Source Configuration]** verschijnt.
1. Geef de waarde **[!UICONTROL Title]** op en selecteer de waarde **[!UICONTROL Service Type]** as **[!UICONTROL RESTful Service]** .
1. Klik op **[!UICONTROL Next]**.
1. Selecteer **[!UICONTROL Swagger Source]** als **[!UICONTROL File].**

   >[!NOTE]
   >
   > Wanneer het wagerbestand is geselecteerd, worden het schema, de hostnaam en het basispad automatisch ingevuld.

1. Upload het gemaakte wagerbestand van uw lokale computer door op **[!UICONTROL Browse]** te klikken.
1. Selecteer **[!UICONTROL Authentication Type]** as **[!UICONTROL OAuth 2.0]** en het deelvenster **[!UICONTROL Authentication Settings]** verschijnt.
1. Selecteer **[!UICONTROL Grant Type]** als **[!UICONTROL Client Credential]** .
1. Geef de **[!UICONTROL Client Id]** en **[!UICONTROL Client Secret]** op die u wilt ophalen uit de met Salesforce verbonden app.
1. De **[!UICONTROL Access Token URL]** opgeven in de notatie
   `https://[MyDomainName].my.salesforce.com/services/oauth2/token`.

   >[!NOTE]
   >
   > Elke organisatie heeft een eigen specifieke domeinnaam.

1. Klik op **[!UICONTROL Test Connection]**.
1. Klik op de knop **[!UICONTROL Create]** als de verbinding tot stand is gebracht.


Nadat u de Salesforce-toepassing hebt geconfigureerd, kunt u de configuratie gebruiken tijdens het maken van een FDM (Form Data Model). Voor meer informatie, zie [ het model van vormgegevens (FDM) ](create-form-data-models.md) creëren. [ vorm het Model van Gegevens van de Vorm verzendt Actie ](/help/forms/using-form-data-model.md) voor een Aangepaste Vorm om gegevens naar toepassingen te verzenden Salesforce.

Voor meer informatie over het creëren van en het gebruiken van het Model van de Gegevens van de Vorm (FDM) in bedrijfswerkschema&#39;s, zie {de Integratie van 0} Gegevens [&#128279;](data-integration.md).

## Verwante artikelen

{{af-submit-action}}


