---
title: Hoe wordt Google reCAPTCHA gebruikt in een AEM Adaptive Form?
description: Verbeter de formulierbeveiliging zonder problemen met de Google reCAPTCHA-service. Stap-voor-stap gids binnen!
topic-tags: Adaptive Forms, author
keywords: De Google reCAPTCHA-service, Adaptive Forms, CAPTCHA-uitdaging, Boot Prevention, Core Components, Security Formulierverzending, Preventie van formulierspam
feature: Adaptive Forms, Core Components
role: User, Developer
exl-id: d116f979-efb6-4fac-8202-89afd1037b2c
source-git-commit: 76301ca614ae2256f5f8b00c41399298c761ee33
workflow-type: tm+mt
source-wordcount: '1348'
ht-degree: 0%

---

# Google reCAPTCHA gebruiken in een AEM adaptief formulier op basis van Core Components {#using-reCAPTCHA-in-adaptive-forms}

| Van toepassing op | Artikelkoppeling |
| -------- | ---------------------------- |
| Adaptief formulier op basis van kerncomponenten | Dit artikel |
| Adaptief formulier op basis van elementaire componenten | [&#x200B; klik hier &#x200B;](/help/forms/captcha-adaptive-forms.md) |

CAPTCHA (Complete Automated Public Turing test to tell Computers and Humans Apart) is een programma dat vaak wordt gebruikt bij online transacties om onderscheid te maken tussen mensen en geautomatiseerde programma&#39;s of bots. Het stelt een uitdaging en evalueert de reactie van de gebruiker om te bepalen of het een mens of bot is die met de site communiceert. Het verhindert de gebruiker om te werk te gaan als de test ontbreekt en de hulp maakt online transacties veilig door bots te houden spam of kwaadwillige doeleinden posten.

AEM Forms as a Cloud Service ondersteunt de volgende CAPTCHA-oplossingen:

* [Google reCAPTCHA](#connect-your-aem-forms-environment-with-recaptcha-service-by-google)
* [&#x200B; hCaptcha &#x200B;](/help/forms/integrate-adaptive-forms-hcaptcha-core-components.md)


## Sluit uw AEM Forms Core-componenten aan op de reCAPTCHA-service van Google {#connect-your-forms-environment-with-recaptcha-service-by-google}

Auteurs van formulieren kunnen de reCAPTCHA-service van Google gebruiken om reCAPTCHA te implementeren in Adaptive Forms. Het biedt geavanceerde CAPTCHA-mogelijkheden om uw site te beschermen. Voor meer informatie over hoe reCAPTCHA werkt, zie [&#x200B; Google reCAPTCHA &#x200B;](https://developers.google.com/recaptcha/). U gebruikt dit om een CAPTCHA-uitdaging aan te bieden bij het verzenden van formulieren.[!DNL AEM Forms] als [!DNL Cloud Service] ondersteunt Google reCAPTCHA v2 en reCAPTCHA Enterprise. Andere versies worden niet ondersteund. Het is ook duidelijk dat reCAPTCHA in Adaptive Forms niet wordt ondersteund in de offlinemodus in de AEM Forms-app.

Gebaseerd op uw vereiste kunt u de dienst vormen reCAPTCHA om toe te laten:

* [reCAPTCHA Enterprise](#steps-to-implement-reCAPTCHA-enterprise-in-forms-core-components)
* [reCAPTCHA v2](#steps-to-implement-reCAPTCHA-v2-in-forms)

### reCAPTCHA Enterprise configureren  {#steps-to-implement-reCAPTCHA-enterprise-in-forms-core-components}

1. Creeer of selecteer a [&#x200B; het project van de Wolk van Google &#x200B;](https://cloud.google.com/recaptcha-enterprise/docs/set-up-non-google-cloud-environments-api-keys#before-you-begin) en laat [&#x200B; reCAPTCHA Onderneming API &#x200B;](https://cloud.google.com/recaptcha-enterprise/docs/set-up-non-google-cloud-environments-api-keys#enable-the-recaptcha-enterprise-api) toe.
1. Verkrijg [&#x200B; identiteitskaart van het Project &#x200B;](https://support.google.com/googleapi/answer/7014113?hl=en#:~:text=To%20locate%20your%20project%20ID,a%20member%20of%20are%20displayed) en creeer een [&#x200B; API sleutel &#x200B;](https://cloud.google.com/recaptcha-enterprise/docs/set-up-non-google-cloud-environments-api-keys#create_an_api_key) en de sleutel van de a [&#x200B; plaats voor websites &#x200B;](https://cloud.google.com/recaptcha-enterprise/docs/create-key#create-key).
1. Configuratiecontainer maken voor cloudservices.

   1. Ga naar **[!UICONTROL Tools > General > Configuration Browser]** .
   1. Selecteer een map of maak een map en schakel de map in voor cloudconfiguraties met behulp van de volgende stappen:
      1. Selecteer de map in de Configuration Browser en selecteer **[!UICONTROL Properties]** .
      1. Schakel in het dialoogvenster Configuration Properties **[!UICONTROL Cloud Configurations]** in.
      1. Selecteer **[!UICONTROL Save & Close]** om de configuratie op te slaan en het dialoogvenster af te sluiten.

1. Configureer de cloudservice voor [!DNL reCAPTCHA Enterprise] .

   1. Op uw de auteursinstantie van Experience Manager, ga ![&#x200B; hulpmiddelen-1 &#x200B;](assets/tools-1.png) > **[!UICONTROL Cloud Services]**.
   1. Selecteer **[!UICONTROL reCAPTCHA]**. De pagina Configurations wordt geopend. Selecteer de configuratiecontainer die u hebt gemaakt en selecteer **[!UICONTROL Create]** .
   1. Selecteer versie als [!DNL reCAPTCHA Enterprise] en geef Naam, Project-id, Sitecode en API-sleutel (verkregen in stap 2) op voor de reCAPTCHA Enterprise-service.
   1. Selecteer zeer belangrijk type, zou het zeer belangrijke type als plaatstoets moeten zijn die u in het [&#x200B; project van de Wolk van Google &#x200B;](https://cloud.google.com/recaptcha-enterprise/docs/set-up-non-google-cloud-environments-api-keys#before-you-begin) vormde, bijvoorbeeld, **de plaatskaart van Checkbox** of **Score-based plaatstoets**.
   1. Specificeer a [&#x200B; drempelscore in waaier 0 tot 1 &#x200B;](https://cloud.google.com/recaptcha-enterprise/docs/interpret-assessment#interpret_scores). Scores groter dan of gelijk aan de drempelscores identificeren menselijke interactie, anders beschouwd als beide interactie.
   1. Selecteer **[!UICONTROL Create]** om de configuratie van de cloudservice te maken.

<!--
    1. In the Edit Component dialog, specify the name, project ID, site key, API key (obtained in steps 2 and 3), select the key type, and enter the threshold score. Select **[!UICONTROL Save Settings]** and then select **[!UICONTROL OK]** to complete the configuration.
-->

Zodra de reCAPTCHA Enterprise-service is ingeschakeld, is deze beschikbaar voor gebruik in adaptieve formulieren. Zie [&#x200B; gebruikend CAPTCHA in adaptieve vormen &#x200B;](#using-reCAPTCHA).

<!--
![reCAPTCHA Enterprise](/help/forms/assets/recaptcha1-enterprise.png)
-->


### Google reCAPTCHA v2 configureren {#steps-to-implement-reCAPTCHA-v2-in-forms}

1. Verkrijg [&#x200B; reCAPTCHA API zeer belangrijk paar &#x200B;](https://www.google.com/recaptcha/admin) van Google. Het omvat a **plaats sleutel** en a **geheime sleutel**.

   ![&#x200B; creeer Google reCAPTCHA configuratie van de website van Google om reCAPTCHA Sleutels &#x200B;](/help/forms/assets/google-captcha.gif) te verkrijgen
1. Maak een configuratiecontainer op uw AEM Forms as a Cloud Service-omgeving. Een configuratiecontainer bevat cloudconfiguraties waarmee AEM wordt verbonden met externe services. Om een Container van de Configuratie te creëren en te vormen om uw milieu van AEM Forms met de dienst van reCAPTCHA aan te sluiten door Google:
   1. Open uw AEM Forms as a Cloud Service-exemplaar.
   1. Ga naar **[!UICONTROL Tools > General > Configuration Browser]** . In Browser van de Configuratie, kunt u:
   1. Selecteer een bestaande map of maak een map. U kunt een map maken en de optie Cloud Configurations hiervoor inschakelen of de optie Cloud Configurations inschakelen voor een bestaande map:

      * Een map maken en de optie Cloud Configurations inschakelen:
         1. Klik op **[!UICONTROL Create]** in de Configuration Browser.
         1. Geef in het dialoogvenster Configuratie maken een naam, titel en selecteer de optie **[!UICONTROL Cloud Configurations]** .
         1. Klikken **[!UICONTROL Create]**
      * De optie Cloud Configurations inschakelen voor een bestaande map:
         1. Selecteer de map in de Configuration Browser en selecteer **[!UICONTROL Properties]** .
         1. Schakel in het dialoogvenster Configuration Properties **[!UICONTROL Cloud Configurations]** in.
         1. Selecteer **[!UICONTROL Save & Close]** om de configuratie op te slaan en het dialoogvenster af te sluiten.

1. De Cloud Service configureren:
   1. Op uw de auteursinstantie van AEM, ga ![&#x200B; hulpmiddelen-1 &#x200B;](assets/tools-1.png) > **[!UICONTROL Cloud Services]** en selecteer **[!UICONTROL reCAPTCHA]**.
   1. Selecteer een Container van de Configuratie, die in vorige sectie wordt gecreeerd of wordt bijgewerkt. Selecteer **[!UICONTROL Create]** .
   1. Geef **[!UICONTROL Title]** , **[!UICONTROL Name]** , **[!UICONTROL Site Key]** en **[!UICONTROL Secret Key]** op voor de service reCAPTCHA (verkregen in stap 1). Selecteer **[!UICONTROL Create]** .

   ![&#x200B; vorm Cloud Service om uw milieu van AEM Forms met de dienst te verbinden reCAPTCHA door Google &#x200B;](/help/forms/assets/captcha-configuration.gif)

   Zodra de dienst reCAPTCHA wordt gevormd, is het beschikbaar voor gebruik in een AanpassingsVorm. Voor meer informatie, zie [&#x200B; gebruikend Google reCAPTCHA in een Aanpassende Vorm &#x200B;](#using-reCAPTCHA).


Google reCAPTCHA gebruiken in adaptieve formulieren

## Google reCAPTCHA gebruiken in een adaptief formulier {#using-reCAPTCHA}

ReCAPTCHA gebruiken in Adaptive Forms:

1. Open uw AEM Forms as a Cloud Service-exemplaar.
1. Ga naar **[!UICONTROL Forms]** > **[!UICONTROL Forms and Documents]** .
1. Selecteer een adaptieve Forms en selecteer **[!UICONTROL Properties]** . Selecteer voor de optie **[!UICONTROL Configuration Container]** de configuratiecontainer die de Cloud Configuration bevat die AEM Forms verbindt met de reCAPTCHA-service van Google en selecteer **[!UICONTROL Save & Close]** .

   Als u geen dergelijke Container van de Configuratie hebt, zie sectie [&#x200B; uw milieu van AEM Forms met de dienst reCAPTCHA door Google &#x200B;](#connect-your-forms-environment-with-recaptcha-service-by-google) verbinden om te leren hoe te om zulk een Container van de Configuratie tot stand te brengen.

   ![&#x200B; Uitgezochte Container van de Configuratie &#x200B;](/help/forms/assets/captcha-properties.png)

1. Selecteer een adaptieve Forms en selecteer **[!UICONTROL Edit]** . Het adaptieve formulier wordt geopend in de Adaptive Forms Editor.
1. Sleep de component **[!UICONTROL Adaptive Form reCAPTCHA]** vanuit de componentbrowser naar het adaptieve formulier.

   >[!NOTE]
   > * De Google reCAPTCHA-validatie is tijdgevoelig en verloopt over een paar minuten. Daarom raadt Adobe aan de component **[!UICONTROL Adaptive Form reCAPTCHA]** vlak voor de knop **[!UICONTROL Submit]** te plaatsen.

1. Selecteer de **[!UICONTROL Adaptive Form reCAPTCHA]** component en selecteer het eigenschappen ![&#x200B; pictogram van Eigenschappen &#x200B;](assets/configure-icon.svg) pictogram. Hiermee wordt het dialoogvenster met eigenschappen geopend. Geef de volgende verplichte eigenschappen op:
   * **[!UICONTROL Name]:** u kunt een formuliercomponent gemakkelijk identificeren met zijn unieke naam in zowel het formulier als de regeleditor, maar de naam mag geen spaties of speciale tekens bevatten.
   * **[!UICONTROL Title]:** Geef een titel op voor de CAPTCHA-widget. De standaardwaarde is **Captcha**. Selecteer **titel van de Verbergen** als u geen titel wilt verschijnen. Selecteer **Verrijkte Tekst voor Titel** toestaan om uw titel in rijk tekstformaat uit te geven. U kunt uw titel als **Ongebonden Element van de Vorm** ook merken.
   * **[!UICONTROL CAPTCHA Configuration]:** selecteer een configuratie van de drop-down Montages voor **reCAPTCHA Onderneming** of **reCAPTCHA v2** om de dialoog van Google reCAPTCHA voor de vorm voor te stellen:
      1. Als u **versie 0&rbrace; reCAPTCHA van de Onderneming &lbrace;selecteert, kan het zeer belangrijke type van** checkbox **of** gebaseerde score **zijn, is het gebaseerd op uw selectie wanneer u [&#x200B; plaats sleutel voor websites &#x200B;](https://cloud.google.com/recaptcha-enterprise/docs/create-key#create-key) vormt:**

         >[!NOTE]
         >
         >* In de wolkenconfiguratie met **zeer belangrijk type** als **checkbox**, verschijnt het aangepaste foutenbericht als gealigneerd bericht als de bevestiging captcha ontbreekt.
         >* In de wolkenconfiguratie met **zeer belangrijk type** als **gebaseerde score**, toont het aangepaste foutenbericht als pop-up bericht als de bevestiging captcha ontbreekt.

      1. U kunt grootte selecteren als **[!UICONTROL Normal]** en **[!UICONTROL Compact]** .

     >[!NOTE]
     >* U kunt voor vergelijkbare doeleinden meerdere Cloud Configurations in uw omgeving gebruiken. Kies de service dus zorgvuldig. Als geen dienst vermeld is, zie [&#x200B; uw milieu van AEM Forms met de dienst reCAPTCHA door Google &#x200B;](#connect-your-forms-environment-with-recaptcha-service-by-google) verbinden om te leren hoe te om een Cloud Service tot stand te brengen die uw milieu van AEM Forms met de dienst reCAPTCHA door Google verbindt.

   * **Grootte Captcha:** U kunt de vertoningsgrootte van Google reCAPTCHA uitdagingsdialoog selecteren. Gebruik de optie **[!UICONTROL Compact]** om een klein formaat weer te geven en de optie **[!UICONTROL Normal]** om een relatief groot Google reCAPTCHA-uitdagingsdialoogvenster weer te geven.
Als u **reCAPTCHA v2** versie selecteert:
      1. U kunt de grootte selecteren als **[!UICONTROL Normal]** of **[!UICONTROL Compact]** voor de reCAPTCHA-widget.
      1. U kunt de optie **[!UICONTROL Invisible]** selecteren om de CAPTCHA-uitdaging alleen te tonen in het geval van een verdachte activiteit.

   De reCAPTCHA-service is ingeschakeld op het adaptieve formulier. U kunt een voorbeeld van het formulier bekijken en de CAPTCHA bekijken. **die door reCAPTCHA** wordt beschermd badge, hieronder wordt getoond, wordt getoond op de beschermde vormen.

   ![&#x200B; Google die door reCAPTCHA badge &#x200B;](/help/forms/assets/google-recaptcha-v2.png) wordt beschermd

1. Selecteer **[!UICONTROL Done]** .

   Nu, wordt **beschermd door reCAPTCHA** getoond op uw Aangepaste Vorm. Het wordt weergegeven op alle Adaptive Forms die zijn geconfigureerd om de Google reCAPTCHA-service te gebruiken.

   Nu kunnen alleen legitieme formulieren worden verzonden, waarin de invuller van het formulier de uitdaging van de Google reCAPTCHA-service met succes heeft verholpen.

<!--
### Show or hide CAPTCHA component based on rules {#show-hide-captcha}

You can select to show or hide the CAPTCHA component based on rules that you apply on a component in an Adaptive Form. Select the component, select ![edit rules](assets/edit-rules-icon.svg), and select **[!UICONTROL Create]** to create a rule. For more information on creating rules, see [Rule Editor](rule-editor.md).

For example, the CAPTCHA component must display in an Adaptive Form only if the Currency Value field in the form has a value of more than 25000.

Select the **[!UICONTROL Currency Value]** field in the form and create the following rules:

![Show or hide rules](assets/rules-show-hide-captcha.png)

   >[!NOTE]
   >
   > When you select a reCAPTCHA v2 configuration and the size is set to [!UICONTROL Invisible], the show/hide option remains disabled.

   -->

## Veelgestelde vragen

**Q: Kan ik meer dan één component Captcha in een AanpassingsVorm gebruiken?**
**Ans:** het gebruiken van meer dan één component Captcha in een AanpassingsVorm wordt niet gesteund. Het wordt ook afgeraden de component Captcha te gebruiken in een fragment of een deelvenster dat is gemarkeerd voor wazig laden.

## Zie ook {#see-also}

{{see-also}}
