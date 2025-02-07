---
Title: How to configure submit to Rest Endpoint submit action for an Adaptive Form?
Description: Discover the steps to set up Rest Endpoint when submitting an Adaptive Form.
keywords: AEM Forms REST Endpoint, Submit aan REST Endpoint, Post Gegevens aan REST URL, vormt de Actie van het Eindpunt van REST
feature: Adaptive Forms, Core Components
title: Hoe te om een Submit Actie voor een Aangepast Vorm te vormen?
role: User, Developer
source-git-commit: c20b8909bb884f14bd7fe59f190de3cd375a7111
workflow-type: tm+mt
source-wordcount: '669'
ht-degree: 1%

---

# Een adaptieve vorm configureren voor het verzenden van REST-eindpunten

Gebruik de handeling **[!UICONTROL Submit to REST Endpoint]** om de verzonden gegevens naar een REST-URL te verzenden. De URL kan van een interne (de server waarop het formulier wordt gegenereerd) of van een externe server zijn.

AEM as a Cloud Service biedt verschillende mogelijkheden in het vak Acties verzenden voor het verwerken van verzonden formulieren. U kunt meer over deze opties leren in het [ AanpassingsVorm voorlegt Artikel van de Actie ](/help/forms/configure-submit-actions-core-components.md).

## Voordelen

Een aantal voordelen van het configureren van de verzendactie **[!UICONTROL Submit to REST endpoint]** voor Adaptive Forms zijn:

* Het maakt naadloze integratie van formuliergegevens met externe systemen en services mogelijk via RESTful-API&#39;s.
* Het biedt flexibiliteit bij de verwerking van gegevensverzendingen van Adaptive Forms en ondersteunt dynamische en complexe gegevensstructuren.
* De URL ondersteunt het dynamisch toewijzen van formuliervelden aan parameters in de URL van het REST-eindpunt, zodat aanpasbare en aanpasbare gegevens kunnen worden verzonden.


## Vorm voorleggen aan REST Endpoint voorlegt actie {#steps-to-configure-submit-to-restendpoint-submit-action}

Verzendactie configureren op basis van de Swagger Open API-specificatie:

1. Open de browser Inhoud en selecteer de component **[!UICONTROL Guide Container]** van het adaptieve formulier.
1. Klik de eigenschappen van de Container van de Gids ![ eigenschappen van de Gids ](/help/forms/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer wordt geopend.
1. Klik op de tab **[!UICONTROL Submission]** .
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Submit Action]** de optie **[!UICONTROL Submit to Rest endpoint]**.
   ![ configuratie van de Actie van voorleggen aan het eindpunt van het Rest ](/help/forms/assets/submit-action-restendpoint.png)

   Om gegevens aan een interne server te posten, verstrek weg van het middel. De gegevens worden gepost de weg van het middel. Bijvoorbeeld `/content/restEndPoint` . Voor dergelijke postverzoeken wordt de authenticatieinformatie van het verzendverzoek gebruikt.

   Geef een URL op om gegevens naar een externe server te posten. De opmaak van de URL is `https://host:port/path_to_rest_end_point` . Zorg ervoor dat u de weg vormt om het verzoek van de POST anoniem te behandelen.

   ![ Toewijzing voor gebiedswaarden die als Dank worden overgegaan de parameters van de Pagina ](assets/post-enabled-actionconfig.png)

   In het bovenstaande voorbeeld wordt door de gebruiker ingevoerde informatie in `textbox` vastgelegd met parameter `param1` . De syntaxis voor het posten van gegevens die zijn vastgelegd met `param1` is:

   `String data=request.getParameter("param1");`

   Op dezelfde manier zijn de parameters die u gebruikt voor het posten van XML-gegevens en -bijlagen `dataXml` en `attachments` .

   U gebruikt deze twee parameters in uw script bijvoorbeeld om gegevens te parseren op een eindpunt in de rest. U gebruikt de volgende syntaxis om de gegevens op te slaan en te ontleden:

   `String data=request.getParameter("dataXml");`
   `String att=request.getParameter("attachments");`

   In dit voorbeeld slaat `data` de XML-gegevens op en slaat `att` de gegevens in de bijlage op.

   Met de handeling **[!UICONTROL Submit to REST endpoint]** Verzenden worden de gegevens die in het formulier zijn ingevuld, als onderdeel van de HTTP-aanvraag verzonden naar een geconfigureerde bevestigingspagina. U kunt de naam toevoegen van het veld dat u wilt aanvragen. De indeling van het verzoek is:

   `{fieldName}={request parameter name}`

   Zoals aangetoond in het beeld hieronder, `param1` en `param2` worden overgegaan als parameters met waarden die van **worden gekopieerd textbox** en **numericbox** gebieden voor de volgende actie.

   ![ Vormend Rest Eindpunt legt Actie ](assets/action-config.png) voor

   U kunt ook **[!UICONTROL Enable POST request]** opgeven en een URL opgeven om de aanvraag te verzenden. Als u gegevens wilt verzenden naar de AEM server waarop het formulier zich bevindt, gebruikt u een relatief pad dat overeenkomt met het hoofdpad van de AEM server. Bijvoorbeeld `/content/forms/af/SampleForm.html` . Gebruik absoluut pad om gegevens naar een andere server te verzenden.

1. Klik op **[!UICONTROL Done]**.

### Vorm voorlegt actie die op het Eindpunt van de Rest van de Dienst wordt gebaseerd {#config-service-endpoint-auth}

<span class="preview"> De service-eindpuntfunctionaliteit valt onder het programma Vroege adopter en is alleen van toepassing op kerncomponenten. U kunt vanaf uw officiële e-mailadres naar aem-forms-ea@adobe.com schrijven om deel te nemen aan het programma voor vroege adoptie en toegang tot de functie te vragen. </span>

1. Open de browser Inhoud en selecteer de component **[!UICONTROL Guide Container]** van het adaptieve formulier.
1. Klik de eigenschappen van de Container van de Gids ![ eigenschappen van de Gids ](/help/forms/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer wordt geopend.
1. Klik op de tab **[!UICONTROL Submission]** .
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Submit Action]** de optie **[!UICONTROL Submit to Rest endpoint]**.
1. Schakel het verzoek van de POST in.
1. Geef de URL van het REST-eindpunt op.
1. Selecteer de Configuratie u voor uw Type van Authentificatie van het Eindpunt van de Dienst en de Types van Inhoud hebt gecreeerd. Om meer over het Type van Authentificatie en de Types van Inhoud te weten, vormt het bezoek [ gegevensbronnen ](/help/forms/configure-data-sources.md#configure-restful-services-using-service-endpoint-configure-restful-services-service-endpoint).
   ![ Vormend Rest Endpoint ](assets/rest-service-endpoint-config.png)
1. Klik op Gereed.

## Aanbevolen procedures

* Wanneer het posten van gegevens aan een externe server, zorg ervoor URL veilig is, en vorm de weg om het verzoek van de POST anoniem te behandelen om gevoelige informatie te beschermen.
* Als u de velden als parameters in een REST-URL wilt doorgeven, moeten alle velden verschillende elementnamen hebben, zelfs als de velden op verschillende deelvensters zijn geplaatst.

## Verwante artikelen

{{af-submit-action}}
