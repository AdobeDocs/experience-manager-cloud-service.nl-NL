---
title: reCAPTCHA gebruiken met Edge Delivery Services voor AEM Forms as a Cloud Service
description: Google reCAPTCHA gebruiken in een formulier voor Edge Delivery Services for AEM Forms
feature: Edge Delivery Services
keywords: reCAPTCHA in formulieren, met reCAPTCHA in Universal Editor, reCAPTCHA toevoegen in formulieren
role: Admin, Architect, Developer
hide: true
hidefromtoc: true
exl-id: 1f28bd13-133f-487e-8b01-334be7c08a3f
source-git-commit: 320ab86bc73e874705d985b927e90eec3cad1cf9
workflow-type: tm+mt
source-wordcount: '1174'
ht-degree: 0%

---


# reCAPTCHA gebruiken in WYSIWYG Authoring

CAPTCHA (Complete Automated Public Turing test to tell Computers and Humans Apart) is een populair hulpmiddel om websites te beschermen tegen frauduleuze activiteiten, spam en misbruik.

Neem bijvoorbeeld een formulier dat de belasting berekent op basis van aanvullende aftrekkingen en het belastingtarief. In dergelijke gevallen bestaat het risico dat kwaadwillende gebruikers het formulier exploiteren voor doeleinden als het verzenden van phishinge-mails of het overlopen van het formulier met irrelevante of schadelijke inhoud met behulp van spambots. Het integreren CAPTCHA biedt extra veiligheid door te verifiëren dat de bijdragen van echte gebruikers zijn, effectief minimaliserend spamingingingangen.

![ Google recaptcha ](/help/edge/docs/forms/universal-editor/assets/google-recaptcha.png)

In Edge Delivery Services Forms, staat het Blok van de Vorm u toe [ om Google reCAPTCHA met vormen ](#connect-forms-with-recaptcha-service-by-google) te verbinden gebruikend **Captcha (Onzichtbaar)** component om tussen mensen en bots te onderscheiden. Met deze functionaliteit kunnen auteurs hun formulieren beschermen tegen spam en misbruik.

## Forms verbinden met de reCAPTCHA-service van Google

U kunt Edge Delivery Services Forms ontwerpen om de reCAPTCHA-service van Google te implementeren. Afhankelijk van uw behoeften, kunt u één van de volgende reCAPTCHA diensten voor uw Edge Delivery Services Forms vormen:

* [reCAPTCHA Enterprise](#configure-recaptcha-enterprise)
* [reCAPTCHA](#configure-recaptcha)

>[!NOTE]
>
> Voor meer informatie over hoe reCAPTCHA werkt, zie [ Google reCAPTCHA ](https://developers.google.com/recaptcha/).

### reCAPTCHA Enterprise configureren

reCAPTCHA Enterprise is een eersteklas service voor fraudedetectie en -preventie op bedrijfsniveau die door Google wordt aangeboden. Het bouwt op de stichting van reCAPTCHA (op score-gebaseerd) maar verstrekt extra eigenschappen, scalability, en aanpassing om aan de complexe behoeften van ondernemingen te voldoen.

#### Voordat u begint

Controleer of u de volgende stappen hebt uitgevoerd voordat u Google reCAPTCHA Enterprise for Edge Delivery Services Forms configureert:

1. Creeer of selecteer a [ het project van de Wolk van Google ](https://cloud.google.com/recaptcha/docs/prepare-environment#before-you-begin) en wint [ identiteitskaart van het Project ](https://support.google.com/googleapi/answer/7014113?hl=en#:~:text=To%20locate%20your%20project%20ID,a%20member%20of%20are%20displayed) terug.

1. [ laat de reCAPTCHA Onderneming API ](https://cloud.google.com/recaptcha/docs/prepare-environment#enable-api) voor uw project van de Wolk van Google toe en [ creeer een API sleutel ](https://console.cloud.google.com/apis/credentials).

1. Creeer a [ plaats sleutel voor uw project van de Wolk van Google ](https://console.cloud.google.com/security/recaptcha) en kopieer de plaatstoets.

Als u deze gegevens hebt, kunt u doorgaan met het configureren van reCAPTCHA Enterprise voor uw formulieren:

1. [Cloud Configuration Container maken](#1-create-cloud-configuration-container)
1. [De cloudserviceconfiguratie voor reCAPTCHA Enterprise maken](#2-create-the-cloud-service-configuration-for-recaptcha-enterprise)

#### 1. Cloud Configuration Container maken

Voer de volgende stappen uit om de container van de cloudconfiguratie te maken:

1. Meld u aan bij de auteur.
1. Ga naar **[!UICONTROL Tools]** ![ hulpmiddelen-1 ](/help/forms/assets/tools-1.png) > **[!UICONTROL General]** > **[!UICONTROL Configuration Browser]**.

   ![ de configuratiecontainer van de Wolk ](/help/edge/docs/forms/universal-editor/assets/recaptcha-general-configuration.png)

1. Navigeer in het **[!UICONTROL Configuration Browser]** naar het formulier en selecteer **[!UICONTROL Properties]** .

   ![ de configuratieeigenschappen van de Wolk ](/help/edge/docs/forms/universal-editor/assets/general-configuration-properties.png)

1. Schakel **[!UICONTROL Cloud Configurations]** in het dialoogvenster **[!UICONTROL Configuration Properties]** in.

1. Selecteer **[!UICONTROL Save & Close]** om de configuratie op te slaan en het dialoogvenster af te sluiten.

   ![ laat de configuratieeigenschappen van de Wolk ](/help/edge/docs/forms/universal-editor/assets/enable-cloud-configurations.png) toe
`
Publiceer de container voor de cloudconfiguratie nadat u deze hebt gemaakt.

   ![ publiceer de Configuratie van de Wolk ](/help/edge/docs/forms/universal-editor/assets/publish-cloud-configuration.png)

#### 2. Maak de cloudserviceconfiguratie voor reCAPTCHA Enterprise

Voer de volgende stappen uit om de cloudserviceconfiguratie voor reCAPTCHA Enterprise te maken:

1. Meld u aan bij de auteur.
1. Navigeer aan **[!UICONTROL Tools]** ![ hulpmiddelen-1 ](/help/forms/assets/tools-1.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL reCAPTCHA]**.

   ![ Configuratie van de Wolk Recaptcha ](/help/edge/docs/forms/universal-editor/assets/recaptcha-cloud-configuration.png)

   De **dialoog van Configuraties** opent.

1. Navigeer naar het formulier en selecteer **[!UICONTROL Create]** .

   ![ configuratie Captcha ](/help/edge/docs/forms/universal-editor/assets/create-captcha-confguration.png)

   Het dialoogvenster **[!UICONTROL Create reCAPTCHA Configuration]** wordt geopend.

   ![ reCaptcha Onderneming ](/help/edge/docs/forms/universal-editor/assets/recaptcha-enterprise.png)

1. Selecteer versie als [!DNL ReCAPTCHA Enterprise] en geef Titel, Naam, Project-id, Sitecode en API-sleutel op.

   >[!NOTE]
   >
   > U kunt identiteitskaart van het Project, de Sleutel van de Plaats, en de sleutel van API van [ verkrijgen alvorens u ](#before-you-start) sectie voor reCAPTCHA Onderneming begint.

1. Selecteer **[!UICONTROL Key type]** als **Score-Gebaseerde plaats sleutel**.
1. Specificeer a [ drempelscore in waaier 0 tot 1 ](https://cloud.google.com/recaptcha/docs/interpret-assessment-website#interpret_scores). Scores groter dan of gelijk aan de drempelscores identificeren menselijke interactie, anders beschouwd als beide interactie.
1. Selecteer **[!UICONTROL Create]** om de configuratie van de cloudservice te maken.

   Na het maken van de reCAPTCHA-cloudconfiguratie, publiceert u deze.

   ![ publiceer configuratie Recaptcha ](/help/edge/docs/forms/universal-editor/assets/publisg-recaptcha-configuration.png)

U kunt nu een formulier maken of bewerken en de reCAPTCHA-component toevoegen met behulp van de op WYSIWYG gebaseerde ontwerpfunctie. Voor gedetailleerde instructies bij het integreren van Google reCAPTCHA in uw vorm, verwijs naar [ Gebruik reCAPTCHA in Uw Vorm ](#use-recaptcha-in-your-form).

## reCAPTCHA configureren

reCAPTCHA is een gratis service die door Google wordt aangeboden en die websites helpt om misbruik, zoals bots en spam, te detecteren en te voorkomen. De klasse ondersteunt een op score gebaseerde versie die op de achtergrond werkt en wijst een risicoscore (variërend van 0,0 tot 1,0) toe aan elke gebruikersinteractie. Scores groter dan of gelijk aan de drempelscores identificeren menselijke interactie, anders beschouwd als beide interactie.

#### Voordat u begint

Alvorens Google reCAPTCHA voor Edge Delivery Services Forms te vormen, wint [ reCAPTCHA API zeer belangrijk paar van de Console van Google terug ](https://www.google.com/recaptcha/admin). Het paar omvat een sleutel van de Plaats en een Geheime sleutel.

>[!NOTE]
>
> * Edge Delivery Services Forms steunt slechts **versie 0} reCAPTCHA op basis van de Score.**

Als u het API-sleutelpaar hebt, kunt u doorgaan met het configureren van reCAPTCHA voor uw formulieren:

1. [Cloud Configuration Container maken](#1-create-cloud-configuration-container-1)
1. [De configuratie van de cloudservice voor reCAPTCHA maken](#2-create-the-cloud-service-configuration-for-recaptcha)

#### 1. Cloud Configuration Container maken

Voer de volgende stappen uit om de container van de cloudconfiguratie te maken:

1. Meld u aan bij de auteur.
1. Ga naar **[!UICONTROL Tools]** ![ hulpmiddelen-1 ](/help/forms/assets/tools-1.png) > **[!UICONTROL General]** > **[!UICONTROL Configuration Browser]**.

   ![ de configuratiecontainer van de Wolk ](/help/edge/docs/forms/universal-editor/assets/recaptcha-general-configuration.png)

1. Navigeer in het **[!UICONTROL Configuration Browser]** naar het formulier en selecteer **[!UICONTROL Properties]** .

   ![ de configuratieeigenschappen van de Wolk ](/help/edge/docs/forms/universal-editor/assets/general-configuration-properties.png)

1. Schakel **[!UICONTROL Cloud Configurations]** in het dialoogvenster **[!UICONTROL Configuration Properties]** in.

1. Selecteer **[!UICONTROL Save & Close]** om de configuratie op te slaan en het dialoogvenster af te sluiten.

   ![ laat de configuratieeigenschappen van de Wolk ](/help/edge/docs/forms/universal-editor/assets/enable-cloud-configurations.png) toe

   Publiceer de container voor de cloudconfiguratie nadat u deze hebt gemaakt.

   ![ publiceer de Configuratie van de Wolk ](/help/edge/docs/forms/universal-editor/assets/publish-cloud-configuration.png)

#### 2. Maak de cloudserviceconfiguratie voor reCAPTCHA

Voer de volgende stappen uit om de cloudserviceconfiguratie voor reCAPTCHA te maken:

1. Meld u aan bij de auteur.
1. Navigeer aan **[!UICONTROL Tools]** ![ hulpmiddelen-1 ](/help/forms/assets/tools-1.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL reCAPTCHA]**.

   ![ Configuratie van de Wolk Recaptcha ](/help/edge/docs/forms/universal-editor/assets/recaptcha-cloud-configuration.png)

   De **dialoog van Configuraties** opent.

1. Navigeer naar het formulier en selecteer **[!UICONTROL Create]** .

   ![ configuratie Captcha ](/help/edge/docs/forms/universal-editor/assets/create-captcha-confguration.png)

   Het dialoogvenster **[!UICONTROL Create reCAPTCHA Configuration]** wordt geopend.

   ![ reCaptcha Onderneming ](/help/edge/docs/forms/universal-editor/assets/recaptcha.png)

1. Selecteer versie als [!DNL ReCAPTCHA v2] en geef Titel en Naam op.
1. Geef de sitecode en de geheime sleutel op.

   >[!NOTE]
   >
   > U kunt de sleutel van de Plaats en de Geheime sleutel van [ verkrijgen alvorens u ](#before-you-begin) sectie voor reCAPTCHA begint.

1. Selecteer **[!UICONTROL Create]** om de configuratie van de cloudservice te maken.

   Na het maken van de reCAPTCHA-cloudconfiguratie, publiceert u deze.

   ![ publiceer configuratie Recaptcha ](/help/edge/docs/forms/universal-editor/assets/publisg-recaptcha-configuration.png)

U kunt nu een formulier maken en bewerken en de reCAPTCHA-component toevoegen met behulp van de op WYSIWYG gebaseerde ontwerpfunctie. Voor gedetailleerde instructies bij het integreren van Google reCAPTCHA in uw vorm, verwijs naar [ Gebruik reCAPTCHA in Uw Vorm ](#use-recaptcha-in-your-form).

### reCAPTCHA gebruiken in uw formulier

Voer de volgende stappen uit om een formulier te ontwerpen en de component reCAPTCHA (Onzichtbaar) toe te voegen:

1. Open een formulier in de Universal Editor om het te bewerken.
1. Navigeer naar de toegevoegde sectie Adaptief formulier in de Inhoudsstructuur.
1. Klik het **[!UICONTROL Add]** pictogram en voeg de **[!UICONTROL Captcha (Invisble)]** component van de **Aangepaste lijst van de Componenten van de Vorm** toe.

   ![ voeg reCaptcha component ](/help/edge/docs/forms/universal-editor/assets/add-recaptcha-component.png) toe

   U kunt ook de vereiste Adaptieve Forms-component slepen en neerzetten, aangezien de Universal Editor een intuïtieve functie voor slepen en neerzetten biedt.

1. Klik **publiceren** om de vorm na het toevoegen van de **[!UICONTROL Captcha (Invisble)]** component opnieuw te publiceren.

   ![ herpubliceer vorm ](/help/edge/docs/forms/universal-editor/assets/publish-form.png)

U kunt het formulier nu bekijken met de reCAPTCHA-service op de volgende URL:
`https://<branch>--<repo>--<owner>.aem.live/content/forms/af/<form-name`.

![ Vorm met reCAPTCHA ](/help/edge/docs/forms/universal-editor/assets/form-with-recaptcha.png)

## Veelgestelde vragen

* **wat gebeurt als een gebruiker geen reCAPTCHA wolkenconfiguratie creeert?**

  **A**: Als een gebruiker geen reCAPTCHA wolkenconfiguratie creeert, zoekt de server van AEM naar de reCAPTCHA wolkenconfiguratie in de Globale Container van de Configuratie. Als er geen configuratie in de globale configuratiecontainer bestaat, genereert de AEM-server een fout.

* **wat gebeurt als een gebruiker veelvoudige reCAPTCHA wolkenconfiguraties creeert?**
  **A**: Als een gebruiker meer dan één reCAPTCHA wolkenconfiguraties creeert, selecteert het systeem automatisch de eerste gecreeerde reCAPTCHA configuratie.

* **waarom zijn de wijzigingen of de veranderingen niet zichtbaar bij gepubliceerde URL?**
Als wijzigingen of wijzigingen niet zichtbaar zijn op de gepubliceerde URL, controleert u of het formulier opnieuw wordt gepubliceerd om de updates toe te passen.

* **welke reCAPTCHA dienst steunt Edge Delivery Services Forms?**
  **A**: Edge Delivery Services Forms steunt slechts op score-gebaseerde reCAPTCHA dienst die door Google wordt verleend.


## Zie ook

{{see-more-forms-eds}}
