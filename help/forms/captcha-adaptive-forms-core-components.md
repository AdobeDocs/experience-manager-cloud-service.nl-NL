---
title: Google reCAPTCHA gebruiken in een adaptieve vorm op basis van Core Components
description: Verbeter de formulierbeveiliging zonder problemen met de Google reCAPTCHA-service. Stap-voor-stap gids binnen!
topic-tags: Adaptive Forms, author
hide: true
hidefromtoc: true
Keywords: Google reCAPTCHA service, Adaptive Forms, CAPTCHA challenge, Bot prevention, Core Components, Form submission security, Form spam prevention
source-git-commit: b81acc99b1d90b05b7c341253e7cbb46c6ea12ae
workflow-type: tm+mt
source-wordcount: '828'
ht-degree: 0%

---

# Gebruik reCAPTCHA in Adaptive Forms op basis van Core Components {#using-reCAPTCHA-in-adaptive-forms}

CAPTCHA (Complete Automated Public Turing test to tell Computers and Humans Apart) is een programma dat vaak wordt gebruikt bij online transacties om onderscheid te maken tussen mensen en geautomatiseerde programma&#39;s of bots. Het stelt een uitdaging en evalueert de reactie van de gebruiker om te bepalen of het een mens of bot is die met de site communiceert. Het verhindert de gebruiker om te werk te gaan als de test ontbreekt en de hulp maakt online transacties veilig door bots te houden spam of kwaadwillige doeleinden posten.

[!DNL AEM Forms] als [!DNL Cloud Service] ondersteunt Google reCAPTCHA v2 in Adaptive Forms. U kunt het gebruiken om een CAPTCHA-uitdaging aan te bieden bij het verzenden van formulieren. De reCAPTCHA gebruiken in een adaptieve vorm:

1. [Verbind uw AEM Forms-omgeving met de reCAPTCHA-service van Google](#connect-your-forms-environment-with-recaptcha-service-by-google)
1. [Configureer uw adaptieve formulier om de CAPTCHA-uitdaging bij het verzenden van formulieren weer te geven](#using-reCAPTCHA)

## Verbind uw AEM Forms-omgeving met de reCAPTCHA-service van Google {#connect-your-forms-environment-with-recaptcha-service-by-google}

Om uw AEM Forms-omgeving te verbinden met de reCAPTCHA-service van Google

1. Verkrijgen [reCAPTCHA API-sleutelpaar](https://www.google.com/recaptcha/admin) uit Google. Het omvat een **site-sleutel** en **geheime sleutel**.

   ![Google reCAPTCHA-configuratie van Google-website maken voor reCAPTCHA-sleutels](/help/forms/assets/google-captcha.gif)
1. Maak een configuratiecontainer op uw as a Cloud Service AEM Forms-omgeving. Een configuratiecontainer bevat Cloud Configurations die worden gebruikt om AEM te verbinden met externe services. Om een Container van de Configuratie te creëren en te vormen om uw milieu van AEM Forms met de dienst van reCAPTCHA aan te sluiten door Google:
   1. Open uw as a Cloud Service AEM Forms-exemplaar.
   1. Ga naar **[!UICONTROL Tools > General > Configuration Browser]**. In Browser van de Configuratie, kunt u:
   1. Selecteer een bestaande map of maak een map. U kunt een map maken en de optie Cloud Configurations hiervoor inschakelen of de optie Cloud Configurations inschakelen voor een bestaande map:

      * Een map maken en de optie Cloud Configurations inschakelen:
         1. In Browser van de Configuratie, klik **[!UICONTROL Create]**.
         1. Geef in het dialoogvenster Configuratie maken een naam, titel en selecteer de optie **[!UICONTROL Cloud Configurations]** -optie.
         1. Klik op **[!UICONTROL Create]**
      * De optie Cloud Configurations inschakelen voor een bestaande map:
         1. Selecteer de map in de configuratiegrowser en tik op **[!UICONTROL Properties]**.
         1. Schakel in het dialoogvenster Configuratieeigenschappen de optie **[!UICONTROL Cloud Configurations]**.
         1. Tikken **[!UICONTROL Save & Close]** om de configuratie op te slaan en het dialoogvenster af te sluiten.

1. Configureer de Cloud Service:
   1. Ga naar de AEM ![gereedschappen-1](assets/tools-1.png) > **[!UICONTROL Cloud Services]** en tikken **[!UICONTROL reCAPTCHA]**.
   1. Selecteer een Container van de Configuratie, die in vorige sectie wordt gecreeerd of wordt bijgewerkt. Tik op **[!UICONTROL Create]**.
   1. Opgeven **[!UICONTROL Title]**, **[!UICONTROL Name]**, **[!UICONTROL Site Key]**, en **[!UICONTROL Secret Key]** voor de service reCAPTCHA (verkregen in stap 1). Tik op **[!UICONTROL Create]**.


   ![Configureer de Cloud Service om uw AEM Forms-omgeving te verbinden met de reCAPTCHA-service van Google](/help/forms/assets/captcha-configuration.gif)



   Zodra de dienst reCAPTCHA wordt gevormd, is het beschikbaar voor gebruik in een AanpassingsVorm. Zie voor meer informatie [Google reCAPTCHA gebruiken in een adaptief formulier](#using-reCAPTCHA).


## Google reCAPTCHA gebruiken in een adaptief formulier {#using-reCAPTCHA}

ReCAPTCHA gebruiken in Adaptive Forms:

1. Open uw as a Cloud Service AEM Forms-exemplaar.
1. Ga naar **[!UICONTROL Forms]** > **[!UICONTROL Forms and Documents]**.
1. Selecteer een adaptieve Forms en tik op **[!UICONTROL Properties]**. Voor de **[!UICONTROL Configuration Container]** Selecteer de configuratiecontainer die de Cloud Configuration bevat die AEM Forms verbindt met de reCAPTCHA-service van Google en tik **[!UICONTROL Save & Close]**.

   Als u niet zulk een Container van de Configuratie hebt, zie sectie [Verbind uw AEM Forms-omgeving met de reCAPTCHA-service van Google](#connect-your-forms-environment-with-recaptcha-service-by-google) om te leren hoe te om zulk een Container van de Configuratie tot stand te brengen.

   ![Configuratiecontainer selecteren](/help/forms/assets/captcha-properties.png)

1. Selecteer een adaptieve Forms en tik op **[!UICONTROL Edit]**. Het adaptieve formulier wordt geopend in de Adaptive Forms Editor.
1. Sleep vanuit de componentbrowser de **[!UICONTROL Adaptive Form reCAPTCHA]** naar het adaptieve formulier.

   De Google reCAPTCHA-validatie is tijdgevoelig en verloopt over een paar minuten. Daarom raadt Adobe aan de **[!UICONTROL Adaptive Form reCAPTCHA]** component vlak voor de **[!UICONTROL Submit]** knop.

1. Selecteer de **[!UICONTROL Adaptive Form reCAPTCHA]** component en tik op de eigenschappen ![Pictogram Eigenschappen](assets/configure-icon.svg) pictogram. Hiermee wordt het dialoogvenster met eigenschappen geopend. Geef de volgende verplichte eigenschappen op:
   * **[!UICONTROL Name]:** U kunt een formuliercomponent gemakkelijk herkennen met de unieke naam, zowel in het formulier als in de regeleditor, maar de naam mag geen spaties of speciale tekens bevatten.
   * **[!UICONTROL CAPTCHA Configuration]:** Selecteer een Cloud-configuratie die is geconfigureerd om het Google reCAPTCHA-dialoogvenster weer te geven voor het formulier. U kunt voor vergelijkbare doeleinden meerdere Cloud Configurations in uw omgeving gebruiken. Kies de service dus zorgvuldig. Als er geen service wordt vermeld, raadpleegt u [Verbind uw AEM Forms-omgeving met de reCAPTCHA-service van Google](#connect-your-forms-environment-with-recaptcha-service-by-google) om te leren hoe u een Cloud Service kunt maken die uw AEM Forms-omgeving verbindt met de reCAPTCHA-service van Google.
   * **Grootte captcha:** U kunt de weergavegrootte van het Google reCAPTCHA-dialoogvenster selecteren. Gebruik de **[!UICONTROL Compact]** als u een klein formaat en de **[!UICONTROL Normal]** optie om een relatief grote Google reCAPTCHA-uitbreidingsdialoog weer te geven.

1. Tik op **[!UICONTROL Done]**.

   Nu, **beveiligd door reCAPTCHA** wordt weergegeven op uw Adaptief formulier. Het wordt weergegeven op alle Adaptive Forms die zijn geconfigureerd om de Google reCAPTCHA-service te gebruiken.

   Nu kunnen alleen legitieme formulieren worden verzonden, waarin de invuller van het formulier de uitdaging van de Google reCAPTCHA-service met succes heeft verholpen.
   ![Google beveiligd door reCAPTCHA-badge](/help/forms/assets/google-recaptcha-v2.png)

<!--
### Show or hide CAPTCHA component based on rules {#show-hide-captcha}

You can select to show or hide the CAPTCHA component based on rules that you apply on a component in an Adaptive Form. Tap the component, select ![edit rules](assets/edit-rules-icon.svg), and tap **[!UICONTROL Create]** to create a rule. For more information on creating rules, see [Rule Editor](rule-editor.md).

For example, the CAPTCHA component must display in an Adaptive Form only if the Currency Value field in the form has a value of more than 25000.

Tap the **[!UICONTROL Currency Value]** field in the form and create the following rules:

![Show or hide rules](assets/rules-show-hide-captcha.png)

   >[!NOTE]
   >
   > When you select a reCAPTCHA v2 configuration and the size is set to [!UICONTROL Invisible], the show/hide option remains disabled.

   -->

## Veelgestelde vragen

**V: Kan ik meer dan één Captcha-component in een adaptieve vorm gebruiken?**
**Ans:** Het gebruik van meerdere Captcha-componenten in een adaptief formulier wordt niet ondersteund. Het wordt ook afgeraden de component Captcha te gebruiken in een fragment of een deelvenster dat is gemarkeerd voor wazig laden.

