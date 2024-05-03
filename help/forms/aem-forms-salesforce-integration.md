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
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/oauth2-client-credentials-flow-for-server-to-server-integration.html) |
| AEM as a Cloud Service | Dit artikel |

Dankzij de integratie van Adobe Experience Manager (AEM) Forms met Salesforce kunnen organisaties processen stroomlijnen door hun mogelijkheden voor het maken en beheren van formulieren te verbinden met het Salesforce-platform. Door een adaptief formulier aan te sluiten met Salesforce, kunt u naadloze gegevensuitwisseling tussen de twee platforms tot stand brengen. Wanneer gebruikers formulieren verzenden, worden de gegevens automatisch gesynchroniseerd met Salesforce. Het zorgt ervoor dat alle klanteninformatie bijgewerkt en binnen het systeem gecentraliseerd is.

U kunt OAuth 2.0 cliëntgeloofsbrieven gebruiken om AEM Forms met de toepassing van Salesforce te integreren. OAuth 2.0 cliëntgeloofsbrieven zijn een standaard en veilige methode voor directe mededeling zonder gebruikersbetrokkenheid.

![Workflow bij het instellen van communicatie tussen AEM Forms en Salesforce-toepassing](/help/forms/assets/salesforce-workflow.png)

AEM Forms wisselt de aanmeldingsgegevens van de client uit (de sleutel van de consument en het consumentengeheim), die zijn gedefinieerd in de toepassing Salesforce waarmee verbinding wordt gemaakt, om een toegangstoken te verkrijgen.

AEM as a Cloud Service biedt verschillende mogelijkheden in het vak om acties in te dienen voor de verwerking van formulierverzendingen. Meer informatie over deze opties vindt u in het gedeelte [Handeling Adaptief verzenden van formulier](/help/forms/configure-submit-actions-core-components.md) artikel.

Er zijn veelvoudige voordelen om OAuth 2.0 cliëntgeloofsbrieven voor authentificatie over de authentificatie van de Stroom van de Code van de Vergunning te gebruiken:

* OAuth 2.0 de authentificatie van de cliëntgeloofsbrieven staat meer dan vijf verbindingen per gebruiker toe.
* AEM gegevensbronconfiguratie werkt verder aan deactivering, toegangsveranderingen, wachtwoordupdate voor een AEM gebruiker.

## Vereisten {#prerequisites}

Voordat u de communicatie tussen een Salesforce-toepassing en een AEM omgeving instelt:

* Een [Salesforce-app verbonden met OAuth 2.0-clientreferentiestroom](https://help.salesforce.com/s/articleView?id=sf.connected_app_client_credentials_setup.htm&amp;type=5) en een gebruiker die alleen voor de API verantwoordelijk is voor uw organisatie en die de consumentensleutel en het consumentengeheim voor de app ontvangt.

* Zorg ervoor dat het Swagger-bestand op de juiste wijze is geconfigureerd zodat het overeenkomt met de API&#39;s van uw organisatie. U kunt er ook voor kiezen [een Swagger-bestand maken](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/forms/integrate-with-salesforce/describe-rest-api.html) helemaal op maat, voor gebruik in uw AEM.


## Salesforce-toepassing configureren met OAuth 2.0 Client Credential-stroom {#steps-to-create-aem-datasource-configuration}

Voer de volgende stappen uit om Adaptief formulier te verbinden met de Salesforce-toepassing met OAuth 2.0-instellingen voor clientverificatie:

1. Meld u aan bij de instantie Auteur.
1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Data Sources]**.
1. Selecteer de configuratiemap.
1. Klikken **[!UICONTROL Create]** en de **[!UICONTROL Create Data Source Configuration]** wordt weergegeven.
1. Geef de **[!UICONTROL Title]** en selecteert u de **[!UICONTROL Service Type]** als **[!UICONTROL RESTful Service]**.
1. Klik op **[!UICONTROL Next]**.
1. Selecteer de **[!UICONTROL Swagger Source]** als **[!UICONTROL File].**

   >[!NOTE]
   >
   > Wanneer het wagerbestand is geselecteerd, worden het schema, de hostnaam en het basispad automatisch ingevuld.

1. Upload het gemaakte wagerbestand van uw lokale computer door op **[!UICONTROL Browse]**.
1. Selecteer de **[!UICONTROL Authentication Type]** als **[!UICONTROL OAuth 2.0]** en de **[!UICONTROL Authentication Settings]** wordt weergegeven.
1. Selecteer de **[!UICONTROL Grant Type]** als **[!UICONTROL Client Credential]**.
1. Geef de **[!UICONTROL Client Id]** en **[!UICONTROL Client Secret]** verkregen uit de Salesforce-app.
1. Geef de **[!UICONTROL Access Token URL]** in formaat
   `https://[MyDomainName].my.salesforce.com/services/oauth2/token`.

   >[!NOTE]
   >
   > Elke organisatie heeft een eigen specifieke domeinnaam.

1. Klik op **[!UICONTROL Test Connection]**.
1. Als de verbinding succesvol is, klik **[!UICONTROL Create]** knop.


Nadat u de Salesforce-toepassing hebt geconfigureerd, kunt u de configuratie gebruiken tijdens het maken van een FDM (Form Data Model). Zie voor meer informatie [Formuliergegevensmodel maken (FDM)](create-form-data-models.md). [De handeling Verzenden van formuliergegevensmodel configureren](/help/forms/using-form-data-model.md) voor een adaptief formulier om gegevens naar Salesforce-toepassingen te verzenden.

Voor meer informatie over het creëren van en het gebruiken van het Model van de Gegevens van de Vorm (FDM) in bedrijfswerkschema&#39;s, zie [Gegevensintegratie](data-integration.md).

## Verwante artikelen

{{af-submit-action}}


