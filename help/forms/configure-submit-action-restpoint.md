---
Title: How to configure submit to Rest Endpoint submit action for an Adaptive Form?
Description: Discover the steps to set up Rest Endpoint when submitting an Adaptive Form.
keywords: AEM Forms REST Endpoint, Submit naar REST Endpoint, Post Data to REST URL, Configure REST Endpoint Action
feature: Adaptive Forms, Core Components
exl-id: 58c63ba6-aec5-4961-a70a-265990ab9cc8
title: "Hoe te om een Submit Actie voor een Aangepast Vorm te vormen?"
role: User, Developer
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 1%

---

# Een adaptieve vorm configureren voor het verzenden van REST-eindpunten

Gebruik de **[!UICONTROL Submit to REST Endpoint]** actie om de verzonden gegevens naar een REST URL te posten. De URL kan van een interne (de server waarop het formulier wordt gegenereerd) of van een externe server zijn.

AEM as a Cloud Service biedt verschillende mogelijkheden in het vak Acties verzenden voor het verwerken van verzonden formulieren. Meer informatie over deze opties vindt u in het gedeelte [Handeling Adaptief verzenden van formulier](/help/forms/configure-submit-actions-core-components.md)  artikel.

## Voordelen

Sommige voordelen van het configureren van de **[!UICONTROL Submit to REST endpoint]** acties voor Adaptive Forms indienen zijn:

* Het maakt naadloze integratie van formuliergegevens met externe systemen en services mogelijk via RESTful-API&#39;s.
* Het biedt flexibiliteit bij de verwerking van gegevensverzendingen van Adaptive Forms en ondersteunt dynamische en complexe gegevensstructuren.
* De URL ondersteunt het dynamisch toewijzen van formuliervelden aan parameters in de URL van het REST-eindpunt, zodat aanpasbare en aanpasbare gegevens kunnen worden verzonden.


## Vorm voorleggen aan REST Endpoint voorlegt actie {#steps-to-configure-submit-to-restendpoint-submit-action}

Verzendactie configureren:

1. Open de Inhoudsbrowser en selecteer de **[!UICONTROL Guide Container]** van uw adaptieve formulier.
1. Klik op de eigenschappen van de container van de hulplijn ![Eigenschappen van hulplijnen](/help/forms/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer wordt geopend.
1. Klik op de knop  **[!UICONTROL Submission]** tab.
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Submit Action]** de optie **[!UICONTROL Submit to Rest endpoint]**.
   ![Configuratie van handeling voor verzenden naar eindpunt van set](/help/forms/assets/submit-action-restendpoint.png)

   Om gegevens aan een interne server te posten, verstrek weg van het middel. De gegevens worden gepost de weg van het middel. Bijvoorbeeld: `/content/restEndPoint`. Voor dergelijke postverzoeken wordt de authenticatieinformatie van het verzendverzoek gebruikt.

   Geef een URL op om gegevens naar een externe server te posten. De opmaak van de URL is `https://host:port/path_to_rest_end_point`. Zorg ervoor dat u de weg vormt om het verzoek van de POST anoniem te behandelen.

   ![Toewijzing voor veldwaarden die zijn doorgegeven als parameters voor de pagina Bedankt](assets/post-enabled-actionconfig.png)

   In het bovenstaande voorbeeld heeft de gebruiker informatie ingevoerd in `textbox` wordt vastgelegd met parameter `param1`. Syntaxis om gegevens te posten die zijn vastgelegd met `param1` is:

   `String data=request.getParameter("param1");`

   Ook parameters die u gebruikt voor het posten van XML-gegevens en -bijlagen zijn `dataXml` en `attachments`.

   U gebruikt deze twee parameters in uw script bijvoorbeeld om gegevens te parseren op een eindpunt in de rest. U gebruikt de volgende syntaxis om de gegevens op te slaan en te ontleden:

   `String data=request.getParameter("dataXml");`
   `String att=request.getParameter("attachments");`

   In dit voorbeeld: `data` de XML-gegevens worden opgeslagen, en `att` slaat gehechtheidsgegevens op.

   De **[!UICONTROL Submit to REST endpoint]** Met Handeling verzenden worden de gegevens die in het formulier zijn ingevuld, als onderdeel van de HTTP-aanvraag naar een geconfigureerde bevestigingspagina verzonden. U kunt de naam toevoegen van het veld dat u wilt aanvragen. De indeling van het verzoek is:

   `{fieldName}={request parameter name}`

   Zoals in de onderstaande afbeelding wordt getoond: `param1` en `param2` worden doorgegeven als parameters met waarden die zijn gekopieerd uit de **textbox** en **numericbox** velden voor de volgende actie.

   ![Rest Endpoint-verzendhandeling configureren](assets/action-config.png)

   U kunt **[!UICONTROL Enable POST request]** en geef een URL op om de aanvraag te posten. Als u gegevens wilt verzenden naar de AEM server waarop het formulier zich bevindt, gebruikt u een relatief pad dat overeenkomt met het hoofdpad van de AEM server. Bijvoorbeeld: `/content/forms/af/SampleForm.html`. Gebruik absoluut pad om gegevens naar een andere server te verzenden.

1. Klik op **[!UICONTROL Done]**.

## Aanbevolen procedures

* Wanneer het posten van gegevens aan een externe server, zorg ervoor URL veilig is, en vorm de weg om het verzoek van de POST anoniem te behandelen om gevoelige informatie te beschermen.
* Als u de velden als parameters in een REST-URL wilt doorgeven, moeten alle velden verschillende elementnamen hebben, zelfs als de velden op verschillende deelvensters zijn geplaatst.

## Verwante artikelen

{{af-submit-action}}
