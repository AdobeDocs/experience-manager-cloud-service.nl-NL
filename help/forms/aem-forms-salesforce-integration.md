---
title: Hoe te om Salesforce te integreren gebruikend OAuth 2.0 cliëntcredentiële stroom met AEM Forms?
description: Leer Salesforce met AEM Forms te integreren met behulp van OAuth 2.0 client credential flow. Er worden stappen weergegeven voor de integratie met AEM Forms Salesforce.
Keywords: Integration of Salesforce using OAuth 2.0 client credential flow, salesforce integration with oauth2 using client credential flow, salesforce and client credential integration, AEM Forms Salesforce integration
feature: Adaptive Forms, Form Data Model
role: User, Developer
badgeSaas: label="AEM Forms" type="Positive" tooltip="van toepassing op AEM Forms)."
exl-id: 2c2029ab-6fb4-41a6-846c-175c3a79d921
source-git-commit: 89b0f2a8ca9d2f60365a5c3962b0b4e826f79b3e
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 1%

---

# Adaptief formulier integreren met Salesforce {#configure-salesforce-with-ouath-2.0-client-credential}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6.5 | [&#x200B; klik hier &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/oauth2-client-credentials-flow-for-server-to-server-integration.html?lang=nl-NL) |
| AEM as a Cloud Service | Dit artikel |

Dankzij de integratie van Adobe Experience Manager (AEM) Forms met Salesforce kunnen organisaties processen stroomlijnen door hun mogelijkheden voor het maken en beheren van formulieren te verbinden met het Salesforce-platform. Als u een adaptief formulier aansluit op Salesforce, kunt u naadloze gegevensuitwisseling tussen de twee platforms tot stand brengen. Wanneer gebruikers formulieren verzenden, worden de gegevens automatisch gesynchroniseerd met Salesforce. Het zorgt ervoor dat alle klanteninformatie bijgewerkt en binnen het systeem gecentraliseerd is.

U kunt OAuth 2.0 cliëntgeloofsbrieven gebruiken om AEM Forms met de toepassing van Salesforce te integreren. OAuth 2.0 cliëntgeloofsbrieven zijn een standaard en veilige methode voor directe mededeling zonder gebruikersbetrokkenheid.

![&#x200B; Werkschema terwijl het plaatsen van mededeling tussen de toepassing van AEM Forms en van Salesforce &#x200B;](/help/forms/assets/salesforce-workflow.png)

AEM Forms wisselt de clientgegevens uit (de consumentensleutel en het consumentengeheim), die zijn gedefinieerd in de Salesforce-toepassing, om een toegangstoken te verkrijgen.

AEM as a Cloud Service biedt verschillende mogelijkheden in het vak Acties verzenden voor het verwerken van verzonden formulieren. U kunt meer over deze opties leren in het [&#x200B; AanpassingsVorm voorlegt Artikel van de Actie &#x200B;](/help/forms/configure-submit-actions-core-components.md).

Er zijn veelvoudige voordelen om OAuth 2.0 cliëntgeloofsbrieven voor authentificatie over de authentificatie van de Stroom van de Code van de Vergunning te gebruiken:

* OAuth 2.0 de authentificatie van de cliëntgeloofsbrieven staat meer dan vijf verbindingen per gebruiker toe.
* AEM-gegevensbronconfiguratie werkt verder aan deactivering, toegangswijzigingen en wachtwoordupdate voor een AEM-gebruiker.

## Vereisten {#prerequisites}

Voordat u de communicatie tussen een Salesforce-toepassing en een AEM-omgeving instelt:

* Creeer a [&#x200B; Salesforce verbonden app met OAuth 2.0 cliëntcredentiële stroom &#x200B;](https://help.salesforce.com/s/articleView?id=sf.connected_app_client_credentials_setup.htm&type=5) en een API-enige gebruiker voor uw organisatie en verkrijg de consumentensleutel en het consumentengeheim voor app.

* Zorg ervoor dat het Swagger-bestand op de juiste wijze is geconfigureerd zodat het overeenkomt met de API&#39;s van uw organisatie. Alternatief, kunt u verkiezen om [&#x200B; tot een dossier van de Swagger &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/forms/integrate-with-salesforce/describe-rest-api.html?lang=nl-NL) van het kras te leiden, dat voor gebruik in uw milieu van AEM wordt gemaakt.


## Salesforce-toepassing configureren met OAuth 2.0 Client Credential-stroom {#steps-to-create-aem-datasource-configuration}

Voer de volgende stappen uit om een adaptief formulier te verbinden met een Salesforce-toepassing met OAuth 2.0-instellingen voor clientverificatie:

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
1. Geef de **[!UICONTROL Client Id]** en **[!UICONTROL Client Secret]** op die u wilt ophalen uit de Salesforce-app.
1. De **[!UICONTROL Access Token URL]** opgeven in de notatie
   `https://[MyDomainName].my.salesforce.com/services/oauth2/token`.

   >[!NOTE]
   >
   > Elke organisatie heeft een eigen specifieke domeinnaam.

1. Klik op **[!UICONTROL Test Connection]**.
1. Klik op de knop **[!UICONTROL Create]** als de verbinding tot stand is gebracht.


Nadat u de Salesforce-toepassing hebt geconfigureerd, kunt u de configuratie gebruiken tijdens het maken van een FDM (Form Data Model). Voor meer informatie, zie [&#x200B; het model van vormgegevens (FDM) &#x200B;](create-form-data-models.md) creëren. [&#x200B; vorm het Model van Gegevens van de Vorm verzendt Actie &#x200B;](/help/forms/using-form-data-model.md) voor een Aangepast Vorm om gegevens naar de toepassingen van Salesforce te verzenden.

Voor meer informatie over het creëren van en het gebruiken van het Model van de Gegevens van de Vorm (FDM) in bedrijfswerkschema&#39;s, zie {de Integratie van 0} Gegevens [.](data-integration.md)

## Verwante artikelen

{{af-submit-action}}


