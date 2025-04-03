---
title: API's op basis van OpenAPI's
description: Meer informatie over AEM as a Cloud Service-ondersteuning voor op OpenAPI gebaseerde API's
feature: Developing
role: Admin, Architect, Developer
exl-id: 4aeafba9-8f9e-4ecb-9e37-8d048b0474cc
source-git-commit: e735f7d2a39e3165907969d2e27565639499a636
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---

# API&#39;s op basis van OpenAPI&#39;s {#openapi-based-apis}

>[!NOTE]
>
>OpenAPI&#39;s zijn beschikbaar als onderdeel van een programma voor vroege toegang. Als u in de toegang tot van hen geinteresseerd bent, moedigen wij u aan om [ aem-apis@adobe.com ](mailto:aem-apis@adobe.com) met een beschrijving van uw gebruiksgeval te e-mailen.

Nieuwere AEM as a Cloud Service API&#39;s voldoen aan de OpenAPI-specificatie en produceren dus consistente, goed gedocumenteerde en gebruikersvriendelijke API&#39;s. Uitgebreide informatie is beschikbaar op de volgende pagina&#39;s:

* Een [ zelfstudie van begin tot eind ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/aem-apis/invoke-openapi-based-aem-apis) over om op OpenAPI-Gebaseerde AEM APIs te vormen en aan te halen gebruikend server-aan-server authentificatie.
* Informatieve [ Gidsen ](https://developer.adobe.com/experience-cloud/experience-manager-apis/guides/), met inbegrip van [ API concepten en syntaxis ](https://developer.adobe.com/experience-cloud/experience-manager-apis/guides/how-to/).
* API-eindpunt [ verwijzingsdocumentatie ](https://developer.adobe.com/experience-cloud/experience-manager-apis/), waar sommige APIs op OpenAPI-Gebaseerd, zoals [ deze Plaatsen API ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/) zijn. De documentatie van de verwijzing omvat ook een API playground, die het eenvoudig maakt om een eindpunt uit te proberen gebruikend een dragertoken dat met Adobe Developer Console wordt geproduceerd.

Een veelvoorkomend geval van API-gebruik omvat integratie met systemen zoals een CRM of PIM, waarbij AEM API&#39;s worden aangeroepen om gegevens op te halen of te behouden. Als deel van de integratieimplementatie, kunnen de toepassingen aan [ AEM-emitting gebeurtenissen ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/aem-eventing/overview) intekenen, die bedrijfslogica in Adobe App Builder of andere infrastructuur kunnen teweegbrengen.

Ondersteunde API-verificatietypen verschillen op basis van het eindpunt, maar kunnen OAuth Server-to-Server, OAuth Web App en OAuth Single Page App (SPA) zijn.

>[!NOTE]
>
> Het [ leerprogramma van begin tot eind ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/aem-apis/invoke-openapi-based-aem-apis) is een geadviseerd middel om te leren hoe te om op OpenAPI-Gebaseerde AEM APIs te vormen en aan te halen.


## API-toegang configureren {#configuring-api-access}

Vele op open API-Gebaseerde AEM APIs vereisen authentificatie, die geloofsbrieven vereist worden geproduceerd gebruikend [ Adobe Developer Console ](https://developer.adobe.com/developer-console/docs/guides/). De configuratie omvat de volgende stappen:

1. Verzeker de het productprofielen van uw AEM programma [ worden bijgewerkt ](/help/onboarding/aem-cs-team-product-profiles.md#aem-product-profiles) en hebben de aangewezen dienst die wordt toegelaten om tot gewenste API toegang te hebben.
1. Maak een nieuw project in Adobe Developer Console en voeg de gewenste API&#39;s toe aan het project en selecteer het juiste verificatietype.
1. Genereer de referentie, die later wordt gebruikt voor het inwisselen van een token bij het aanroepen van de API.
1. Registreer cliëntidentiteitskaart met het milieu door een dossier te vormen YAML, dat gebruikend de Pijpleiding Config (of bevellijn voor RDEs) wordt opgesteld.

Zie de [ opstelling op openAPI-Gebaseerde zelfstudie APIs ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/aem-apis/setup) voor geleidelijke instructies.

## Client-id registreren {#registering-a-client-id}

Het bereik van client-id&#39;s dat de toegangspunt in een Adobe Developer Console-project heeft voor specifieke AEM-omgevingen. Dit wordt als volgt bereikt:

1. Maak een bestand met de naam `api.yaml` of vergelijkbaar met een configuratie zoals het onderstaande fragment, inclusief de gewenste lagen (auteur, publicatie, voorvertoning). `Client_id` -waarden moeten afkomstig zijn van uw Adobe Developer Console API-project(en).

   De `kind`, `version`, en `metadata` eigenschappen worden beschreven in het [ artikel van de Pijpleiding Config ](/help/operations/config-pipeline.md#common-syntax). De `kind` bezitswaarde zou aan *API* moeten worden geplaatst en het `version` bezit zou aan *1* moeten worden geplaatst.

   ```
   kind: "API"
   version: "1"
   metadata:
     envTypes: ["dev"]
   data:
     allowedClientIDs:
       author:
         - "<client_id>"
       publish:
         - "<client_id>"
       preview:
         - "<client_id>"
   ```

1. Plaats het dossier ergens onder een top niveauomslag genoemd `config` of gelijkaardig, zoals die onder [ wordt beschreven Config Pijpleiding ](/help/operations/config-pipeline.md#folder-structure).
1. Voor milieutypes buiten RDE (die het hulpmiddel van de bevellijn gebruikt), creeer een gerichte plaatsing config pijpleiding in Cloud Manager, zoals die door [ wordt van verwijzingen voorzien deze sectie ](/help/operations/config-pipeline.md#creating-and-managing) in het artikel van de Pijpleiding Config. Merk op dat de Volledige pijpleidingen van het Stapel en de pijpleidingen van de Rij van het Web niet het configuratiedossier opstellen.
1. Implementeer de configuratie.
