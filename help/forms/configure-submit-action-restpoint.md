---
title: Hoe te vormen voorlegt aan Rest Eindpunt actie voor een AanpassingsVorm?
description: Ontdek de stappen aan opstellingsRest Eindpunt wanneer het voorleggen van een AanpassingsVorm.
keywords: AEM Forms REST Endpoint, Submit aan REST Endpoint, Post Gegevens aan REST URL, vormt de Actie van het Eindpunt van REST
feature: Adaptive Forms, Core Components, Foundation Components, Edge Delivery Services
role: User, Developer
exl-id: 58c63ba6-aec5-4961-a70a-265990ab9cc8
source-git-commit: 44a8d5d5fdd2919d6d170638c7b5819c898dcefe
workflow-type: tm+mt
source-wordcount: '1419'
ht-degree: 0%

---

# Een adaptieve vorm configureren voor het verzenden van REST-eindpunten

<span class="preview"> De mogelijkheid om het REST-eindpunt op te geven met behulp van de configuratie is een programma voor vroege adoptie en alleen van toepassing op Core Components (Basiscomponenten) en Edge Delivery Services Forms. U kunt vanuit uw officiële e-mailid naar `aem-forms-ea@adobe.com` schrijven om deel te nemen aan het programma voor vroegtijdige adoptie en toegang tot deze functie aanvragen. </span>

Gebruik de handeling **[!UICONTROL Submit to REST Endpoint]** om de verzonden gegevens naar een REST-URL te verzenden. De URL kan van een interne (de server waarop het formulier wordt gegenereerd) of van een externe server zijn.

AEM as a Cloud Service biedt verschillende mogelijkheden in het vak Acties verzenden voor het verwerken van verzonden formulieren. U kunt meer over deze opties leren in het [ AanpassingsVorm voorlegt Artikel van de Actie ](/help/forms/aem-forms-submit-action.md).

## Voordelen

Een aantal voordelen van het configureren van de verzendactie **[!UICONTROL Submit to REST endpoint]** voor Adaptive Forms zijn:

* Het maakt naadloze integratie van formuliergegevens met externe systemen en services mogelijk via RESTful-API&#39;s.
* Het biedt flexibiliteit bij de verwerking van gegevensverzendingen van Adaptive Forms en ondersteunt dynamische en complexe gegevensstructuren.
* De URL ondersteunt het dynamisch toewijzen van formuliervelden aan parameters in de URL van het REST-eindpunt, zodat aanpasbare en aanpasbare gegevens kunnen worden verzonden.


## Vorm voorleggen aan REST Endpoint voorlegt actie {#steps-to-configure-submit-to-restendpoint-submit-action}

>[!BEGINTABS]

>[!TAB  Component van de Stichting ]

Verzendactie configureren op basis van de Swagger Open API-specificatie voor Adaptief formulier op basis van Foundation Components:

1. Open het Adaptief formulier voor bewerking en ga naar de sectie **[!UICONTROL Submission]** van de eigenschappen van de container van adaptieve formulieren.
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Submit Action]** de optie **[!UICONTROL Submit to Rest endpoint]**.

   ![ configuratie van de Actie van voorleggen aan het eindpunt van het Rest ](/help/forms/assets/submit-action-restendpoint.png)

   Om gegevens aan een interne server te posten, verstrek weg van het middel. De gegevens worden gepost de weg van het middel. Bijvoorbeeld `/content/restEndPoint` . Voor dergelijke postverzoeken wordt de authenticatieinformatie van het verzendverzoek gebruikt.
Deze optie staat u toe om het doelREST eindpunt direct in te gaan.
Geef een URL op om gegevens naar een externe server te posten. De opmaak van de URL is `https://host:port/path_to_rest_end_point` . Zorg ervoor dat u de weg vormt om het POST- verzoek anoniem te behandelen.
   ![ Toewijzing voor gebiedswaarden die als Dank worden overgegaan de parameters van de Pagina ](assets/post-enabled-actionconfig.png)

   In het bovenstaande voorbeeld wordt door de gebruiker ingevoerde informatie in `textbox` vastgelegd met parameter `param1` . De syntaxis voor het posten van gegevens die zijn vastgelegd met `param1` is:

   `String data=request.getParameter("param1");`

   Op dezelfde manier zijn de parameters die u gebruikt voor het posten van XML-gegevens en -bijlagen `dataXml` en `attachments` .

   U gebruikt deze twee parameters in uw script bijvoorbeeld om gegevens te parseren op een eindpunt in de rest. U gebruikt de volgende syntaxis om de gegevens op te slaan en te ontleden:

   `String data=request.getParameter("dataXml");`
   `String att=request.getParameter("attachments");`

   In dit voorbeeld slaat `data` de XML-gegevens op en slaat `att` de gegevens in de bijlage op.
Met de handeling **[!UICONTROL Submit to REST endpoint]** Verzenden worden de gegevens die in het formulier zijn ingevuld, verzonden naar een geconfigureerde bevestigingspagina als onderdeel van de HTTP GET-aanvraag. U kunt de naam toevoegen van het veld dat u wilt aanvragen. De indeling van het verzoek is:
   `{fieldName}={request parameter name}`

   Zoals aangetoond in het beeld hieronder, `param1` en `param2` worden overgegaan als parameters met waarden die van **worden gekopieerd textbox** en **numericbox** gebieden voor de volgende actie.

   ![ Vormend Rest Eindpunt legt Actie ](assets/action-config.png) voor

   U kunt ook **[!UICONTROL Enable POST request]** opgeven en een URL opgeven om de aanvraag te verzenden. Als u gegevens wilt verzenden naar de AEM-server waarop het formulier zich bevindt, gebruikt u een relatief pad dat overeenkomt met het hoofdpad van de AEM-server. Bijvoorbeeld `/content/forms/af/SampleForm.html` . Gebruik absoluut pad om gegevens naar een andere server te verzenden.

1. Klik op **[!UICONTROL Done]**.

>[!TAB  Component van de Kern ]

Verzendactie configureren op basis van de Swagger Open API-specificatie voor Adaptief formulier op basis van Core Components:

1. Open de browser Inhoud en selecteer de component **[!UICONTROL Guide Container]** van het adaptieve formulier.
1. Klik de eigenschappen van de Container van de Gids ![ eigenschappen van de Gids ](/help/forms/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer wordt geopend.
1. Klik op de tab **[!UICONTROL Submission]** .
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Submit Action]** de optie **[!UICONTROL Submit to Rest endpoint]**.

   ![ Vormend Rest Endpoint ](assets/rest-service-endpoint-config.png)

   Om gegevens aan een interne server te posten, verstrek weg van het middel. De gegevens worden gepost de weg van het middel. Bijvoorbeeld `/content/restEndPoint` . Voor dergelijke postverzoeken wordt de authenticatieinformatie van het verzendverzoek gebruikt.

   U hebt twee opties om het REST-eindpunt op te geven:

   +++URL

   Deze optie staat u toe om het doelREST eindpunt direct in te gaan.
Geef een URL op om gegevens naar een externe server te posten. De opmaak van de URL is `https://host:port/path_to_rest_end_point` . Zorg ervoor dat u de weg vormt om het POST- verzoek anoniem te behandelen.

   ![ Toewijzing voor gebiedswaarden die als Dank worden overgegaan de parameters van de Pagina ](assets/post-enabled-actionconfig.png)

   In het bovenstaande voorbeeld wordt door de gebruiker ingevoerde informatie in `textbox` vastgelegd met parameter `param1` . De syntaxis voor het posten van gegevens die zijn vastgelegd met `param1` is:

   `String data=request.getParameter("param1");`

   Op dezelfde manier zijn de parameters die u gebruikt voor het posten van XML-gegevens en -bijlagen `dataXml` en `attachments` .

   U gebruikt deze twee parameters in uw script bijvoorbeeld om gegevens te parseren op een eindpunt in de rest. U gebruikt de volgende syntaxis om de gegevens op te slaan en te ontleden:

   `String data=request.getParameter("dataXml");`
   `String att=request.getParameter("attachments");`

   In dit voorbeeld slaat `data` de XML-gegevens op en slaat `att` de gegevens in de bijlage op.

   Met de handeling **[!UICONTROL Submit to REST endpoint]** Verzenden worden de gegevens die in het formulier zijn ingevuld, verzonden naar een geconfigureerde bevestigingspagina als onderdeel van de HTTP GET-aanvraag. U kunt de naam toevoegen van het veld dat u wilt aanvragen. De indeling van het verzoek is:

   `{fieldName}={request parameter name}`

   Zoals aangetoond in het beeld hieronder, `param1` en `param2` worden overgegaan als parameters met waarden die van **worden gekopieerd textbox** en **numericbox** gebieden voor de volgende actie.

   ![ Vormend Rest Eindpunt legt Actie ](assets/action-config.png) voor

   U kunt ook **[!UICONTROL Enable POST request]** opgeven en een URL opgeven om de aanvraag te verzenden. Als u gegevens wilt verzenden naar de AEM-server waarop het formulier zich bevindt, gebruikt u een relatief pad dat overeenkomt met het hoofdpad van de AEM-server. Bijvoorbeeld `/content/forms/af/SampleForm.html` . Gebruik absoluut pad om gegevens naar een andere server te verzenden.

   +++

   +++Configuration

   Met deze optie kunt u een vooraf gedefinieerde HTTP-configuratie toevoegen die via de AEM Configuration Browser wordt beheerd. U kunt de Configuratie selecteren die voor uw Type van Authentificatie van het Eindpunt van de Rest van de Dienst en de Types van Inhoud wordt gecreeerd. Om meer over het Type van Authentificatie en de Types van Inhoud te weten, bezoek [ vormen gegevensbronnen ](/help/forms/configure-data-sources.md#configure-restful-services-using-service-endpoint-configure-restful-services-service-endpoint)

   +++

1. Klik op **[!UICONTROL Done]**.

>[!TAB  Universele Redacteur ]

Verzendactie configureren op basis van de Swagger Open API-specificatie voor Adaptief formulier geschreven in Universal Editor:

1. Open het adaptieve formulier voor bewerking.
1. Klik **uitgeven de uitbreiding van de Eigenschappen van de Vorm** op de redacteur.
Het **de dialoogvakje van de Eigenschappen van de Vorm** verschijnt.
   >[!NOTE]
   >
   > * Als u niet **ziet geef de Eigenschappen van de Vorm** pictogram in uw Universele interface van de Redacteur uit, laat **toe geef de 3&rbrace; uitbreiding van de Eigenschappen van de Vorm &lbrace;in Extension Manager uit.**
   > * Verwijs naar het [ artikel van de Hoogtepunten van de Eigenschap van 0&rbrace; Extension Manager om te leren hoe te om uitbreidingen in of onbruikbaar te maken in de Universele Redacteur.](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions)
1. Klik **Verzending** lusje en selecteer **[!UICONTROL Submit to Rest endpoint]** voorlegt actie.

   Om gegevens aan een interne server te posten, verstrek weg van het middel. De gegevens worden gepost de weg van het middel. Bijvoorbeeld `/content/restEndPoint` . Voor dergelijke postverzoeken wordt de authenticatieinformatie van het verzendverzoek gebruikt.

   U hebt twee opties om het REST-eindpunt op te geven:

   +++URL

   Deze optie staat u toe om het doelREST eindpunt direct in te gaan.
Geef een URL op om gegevens naar een externe server te posten. De opmaak van de URL is `https://host:port/path_to_rest_end_point` . Zorg ervoor dat u de weg vormt om het POST- verzoek anoniem te behandelen.

   ![ Toewijzing voor gebiedswaarden die als Dank worden overgegaan de parameters van de Pagina ](assets/post-enabled-actionconfig.png)

   In het bovenstaande voorbeeld wordt door de gebruiker ingevoerde informatie in `textbox` vastgelegd met parameter `param1` . De syntaxis voor het posten van gegevens die zijn vastgelegd met `param1` is:

   `String data=request.getParameter("param1");`

   Op dezelfde manier zijn de parameters die u gebruikt voor het posten van XML-gegevens en -bijlagen `dataXml` en `attachments` .

   U gebruikt deze twee parameters in uw script bijvoorbeeld om gegevens te parseren op een eindpunt in de rest. U gebruikt de volgende syntaxis om de gegevens op te slaan en te ontleden:

   `String data=request.getParameter("dataXml");`
   `String att=request.getParameter("attachments");`

   In dit voorbeeld slaat `data` de XML-gegevens op en slaat `att` de gegevens in de bijlage op.

   Met de handeling **[!UICONTROL Submit to REST endpoint]** Verzenden worden de gegevens die in het formulier zijn ingevuld, verzonden naar een geconfigureerde bevestigingspagina als onderdeel van de HTTP GET-aanvraag. U kunt de naam toevoegen van het veld dat u wilt aanvragen. De indeling van het verzoek is:

   `{fieldName}={request parameter name}`

   Zoals aangetoond in het beeld hieronder, `param1` en `param2` worden overgegaan als parameters met waarden die van **worden gekopieerd textbox** en **numericbox** gebieden voor de volgende actie.

   ![ Vormend Rest Eindpunt legt Actie ](/help/forms/assets/submit-to-rest-endpoint-ue.png) voor

   U kunt ook **[!UICONTROL Enable POST request]** opgeven en een URL opgeven om de aanvraag te verzenden. Als u gegevens wilt verzenden naar de AEM-server waarop het formulier zich bevindt, gebruikt u een relatief pad dat overeenkomt met het hoofdpad van de AEM-server. Bijvoorbeeld `/content/forms/af/SampleForm.html` . Gebruik absoluut pad om gegevens naar een andere server te verzenden.

   +++

   +++Configuration

   Met deze optie kunt u een vooraf gedefinieerde HTTP-configuratie toevoegen die via de AEM Configuration Browser wordt beheerd. U kunt de Configuratie selecteren die voor uw Type van Authentificatie van het Eindpunt van de Rest van de Dienst en de Types van Inhoud wordt gecreeerd. Om meer over het Type van Authentificatie en de Types van Inhoud te weten, bezoek [ vormen gegevensbronnen ](/help/forms/configure-data-sources.md#configure-restful-services-using-service-endpoint-configure-restful-services-service-endpoint)

   +++

1. Klik op **[!UICONTROL Save&Close]**.

>[!ENDTABS]

<!-- ### Configure submit action based on Service Rest Endpoint {#config-service-endpoint-auth}



1. Open the Content browser, and select the **[!UICONTROL Guide Container]** component of your Adaptive Form.
2. Click the Guide Container properties ![Guide properties](/help/forms/assets/configure-icon.svg) icon. The Adaptive Form Container dialog box opens. 
3. Click the  **[!UICONTROL Submission]** tab. 
4. From the **[!UICONTROL Submit Action]** drop-down list, select **[!UICONTROL Submit to Rest endpoint]**.
5. Enable the POST request.
6. Specify the REST endpoint URL.
7. Select the Configuration you have created for your Service Rest Endpoint Authentication Type and the Content Types. To know more about Authentication Type and the Content Types, visit [configure data sources](/help/forms/configure-data-sources.md#configure-restful-services-using-service-endpoint-configure-restful-services-service-endpoint).
    ![Configuring Rest Endpoint](assets/rest-service-endpoint-config.png)
8. Click Done. -->



## Aanbevolen procedures

* Wanneer het posten van gegevens aan een externe server, zorg ervoor URL veilig is, en vorm de weg om het POST- verzoek anoniem te behandelen om gevoelige informatie te beschermen.
* Als u de velden als parameters in een REST-URL wilt doorgeven, moeten alle velden verschillende elementnamen hebben, zelfs als de velden op verschillende deelvensters zijn geplaatst.

## Verwante artikelen

{{af-submit-action}}
