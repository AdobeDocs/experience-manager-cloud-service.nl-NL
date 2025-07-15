---
title: API's op basis van OpenAPI's
description: Meer informatie over AEM as a Cloud Service-ondersteuning voor op OpenAPI gebaseerde API's
feature: Developing
role: Admin, Architect, Developer
exl-id: 4aeafba9-8f9e-4ecb-9e37-8d048b0474cc
source-git-commit: 320fe55d652b94cd63dfe82d4165c1f957653a63
workflow-type: tm+mt
source-wordcount: '653'
ht-degree: 0%

---

# API&#39;s op basis van OpenAPI&#39;s {#openapi-based-apis}

Nieuwere AEM as a Cloud Service API&#39;s volgen de OpenAPI-specificatie en bieden dus een consistente en goed gedocumenteerde set API&#39;s.

>[!NOTE]
>
> Een [ leerprogramma van begin tot eind ](https://experienceleague.adobe.com/nl/docs/experience-manager-learn/cloud-service/aem-apis/invoke-openapi-based-aem-apis) is een geadviseerd middel om te leren hoe te om op OpenAPI-Gebaseerde AEM APIs te vormen en aan te halen.

Voor eindpunten die authentificatie vereisen, verschilt de authentificatiebenadering gebaseerd op het eindpunt, maar kan Server-aan-Server, App van het Web OAuth, of App van één pagina OAuth (SPA) gebruiken. De geloofsbrieven worden gevormd door projecten in [ Adobe Developer Console ](https://developer.adobe.com/developer-console/).

Veelvoorkomende gevallen van API-gebruik betreffen integratie met systemen zoals een CRM of PIM, waarbij AEM API&#39;s worden aangeroepen om gegevens op te halen of te behouden. Als deel van de integratieimplementatie, kunnen de toepassingen aan [ AEM-emitting gebeurtenissen ](https://experienceleague.adobe.com/nl/docs/experience-manager-learn/cloud-service/aem-eventing/overview) intekenen, die bedrijfslogica in Adobe App Builder of andere infrastructuur kunnen teweegbrengen.

Dit document fungeert als een overzicht, maar op de volgende pagina&#39;s is meer gedetailleerde documentatie beschikbaar:

* De verbindingen van de op OpenAPI-Gebaseerde sectie van [ verwijzingsdocumentatie ](https://developer.adobe.com/experience-cloud/experience-manager-apis/). De referentiedocumentatie van elke API bevat ook een API-afspeelveld, waarmee u eenvoudig een eindpunt kunt uitproberen met behulp van een token dat met de Adobe Developer Console wordt gegenereerd.

* Informatieve [ Gidsen ](https://developer.adobe.com/experience-cloud/experience-manager-apis/guides/), met inbegrip van [ API concepten en syntaxis ](https://developer.adobe.com/experience-cloud/experience-manager-apis/guides/how-to/).

* Een top-level leerprogramma beschrijvend [ authentificatiemethodes ](https://experienceleague.adobe.com/nl/docs/experience-manager-learn/cloud-service/aem-apis/openapis/overview#authentication-support) en andere concepten.

* Een leerprogramma met video concentreerde zich op [ hoe te om op OpenAPIs ](https://experienceleague.adobe.com/nl/docs/experience-manager-learn/cloud-service/aem-apis/openapis/setup) te vormen.

* [ een leerprogramma van begin tot eind ](https://experienceleague.adobe.com/nl/docs/experience-manager-learn/cloud-service/aem-apis/invoke-openapi-based-aem-apis) over het vormen van en het aanhalen van OpenAPIs met de server-aan-server authentificatiestrategie. Soortgelijke zelfstudies kunt u ook vinden voor webtoepassingen en toepassingen met één pagina.

## API-toegang configureren {#configuring-api-access}

Sommige op OpenAPI-Gebaseerde AEM APIs vereisen authentificatie, die geloofsbrieven vereist worden geproduceerd gebruikend [ Adobe Developer Console ](https://developer.adobe.com/developer-console/). De configuratie omvat de volgende stappen:

1. Modernisering van de AEM as a Cloud Service-omgeving. Voor meer informatie, zie [ Modernisering van het milieu van AEM as a Cloud Service ](https://experienceleague.adobe.com/nl/docs/experience-manager-learn/cloud-service/aem-apis/openapis/setup?#modernization-of-aem-as-a-cloud-service-environment) tutorial stap.
1. Toegang tot de AEM API&#39;s via productprofielen inschakelen. De Profielen van het product worden geassocieerd met de Diensten die de gebruikersgroepen van AEM met vooraf bepaalde Lijsten van het Toegangsbeheer (ACLs) vertegenwoordigen. Terwijl sommige diensten met specifieke productprofielen door gebrek worden geassocieerd, moeten anderen uitdrukkelijk worden geassocieerd; bijvoorbeeld, wordt de Dienst van de Gebruikers van AEM Assets API niet geassocieerd met om het even welk [ Profiel van het Product ](/help/onboarding/aem-cs-team-product-profiles.md#aem-product-profiles), zodat moet u het toelaten om AEM Assets API te gebruiken. Voor meer informatie, zie [ de toegangsstap van AEM APIs ](https://experienceleague.adobe.com/nl/docs/experience-manager-learn/cloud-service/aem-apis/openapis/setup#enable-aem-apis-access) tutorial.
1. Om server-aan-server authentificatie toe te voegen, moet de gebruikersinstellingsintegratie de systeembeheerder van de organisatie in Adobe Admin Console zijn of als Ontwikkelaar aan het Profiel van het Product worden toegevoegd waar de Dienst wordt geassocieerd. Voor meer informatie, zie [ de toegangsstap van AEM APIs ](https://experienceleague.adobe.com/nl/docs/experience-manager-learn/cloud-service/aem-apis/openapis/setup#enable-aem-apis-access) tutorial.
1. Maak een Adobe Developer Console-project (ADC).
1. Vorm het Project ADC. Dit produceert geloofsbrieven die later zullen worden gebruikt om voor een dragertoken te ruilen wanneer het aanhalen van API.
1. Vorm de instantie van AEM om de mededeling van het Project van ADC toe te laten. Dit impliceert het registreren van cliëntidentiteitskaart met het milieu door een dossier te vormen en op te stellen YAML, zoals die in [ wordt beschreven het Registreren van een identiteitskaart van de Cliënt ](#registering-a-client-id) hieronder sectie.

Voor gedetailleerde geleidelijke instructies, zie de [ opstelling op openAPI-Gebaseerde leerprogramma&#39;s ](https://experienceleague.adobe.com/nl/docs/experience-manager-learn/cloud-service/aem-apis/openapis/setup).

### Client-id registreren {#registering-a-client-id}

Client-id&#39;s zijn van toepassing op de API&#39;s in een Adobe Developer Console-project voor specifieke AEM-omgevingen. Dit wordt als volgt bereikt:

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
