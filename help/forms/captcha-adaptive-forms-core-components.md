---
title: Hoe wordt Google reCAPTCHA in een AEM adaptieve vorm gebruikt?
description: Verbeter de formulierbeveiliging zonder problemen met de Google reCAPTCHA-service. Stap-voor-stap gids binnen!
topic-tags: Adaptive Forms, author
keywords: Google reCAPTCHA service, Adaptive Forms, CAPTCHA challenge, Bot prevention, Core Components, Form submission security, Form spam prevention
feature: Adaptive Forms, Core Components
exl-id: d116f979-efb6-4fac-8202-89afd1037b2c
role: User, Developer
source-git-commit: bba5e5d283da616baa57b788181af73d59d86ee3
workflow-type: tm+mt
source-wordcount: '887'
ht-degree: 0%

---

# Use Google reCAPTCHA in an AEM Adaptive Form based on Core Components {#using-reCAPTCHA-in-adaptive-forms}

| Applies to | Article link |
| -------- | ---------------------------- |
| Adaptive Form based on Core Components | This article |
| Adaptive Form based on Foundation Components | [](/help/forms/captcha-adaptive-forms.md) |

CAPTCHA (Completely Automated Public Turing test to tell Computers and Humans Apart) is a program commonly used in online transactions to distinguish between humans and automated programs or bots. It poses a challenge and evaluates user response to determine if it&#39;s a human or a bot interacting with the site. It prevents the user to proceed if the test fails and helps make online transactions secure by keeping bots from posting spam or malicious purposes.

AEM Forms as a Cloud Service supports the following CAPTCHA solutions:

* [Google reCAPTCHA](#connect-your-aem-forms-environment-with-recaptcha-service-by-google)
* [ hCaptcha ](/help/forms/integrate-adaptive-forms-hcaptcha-core-components.md)


## Connect your AEM Forms environment with reCAPTCHA service by Google {#connect-your-forms-environment-with-recaptcha-service-by-google}

Form authors can use the reCAPTCHA service by Google to implement reCAPTCHA in Adaptive Forms. It offers advance CAPTCHA capabilities to protect your site. [](https://developers.google.com/recaptcha/) [!DNL AEM Forms][!DNL Cloud Service] You can use it to present a CAPTCHA challenge on form submission. To connect your AEM Forms environment with reCAPTCHA service by Google

1. [](https://www.google.com/recaptcha/admin) ********

   ![ creeer Google reCAPTCHA configuratie van de website van Google om reCAPTCHA Sleutels ](/help/forms/assets/google-captcha.gif) te verkrijgen
1. Maak een configuratiecontainer op uw AEM Forms as a Cloud Service omgeving. Een configuratiecontainer bevat Cloud Configurations die worden gebruikt om AEM te verbinden met externe services. Om een Container van de Configuratie te creëren en te vormen om uw milieu van AEM Forms met de dienst van reCAPTCHA aan te sluiten door Google:
   1. Open your AEM Forms as a Cloud Service instance.
   1. **[!UICONTROL Tools > General > Configuration Browser]** In the Configuration Browser, you can:
   1. Select an existing folder or create a folder. You can create a folder and enable the Cloud Configurations option for it or Enable the Cloud Configurations option for an existing folder:

      * To create a folder and enable the Cloud Configurations option for it:
         1. **[!UICONTROL Create]**
         1. **[!UICONTROL Cloud Configurations]**
         1. **[!UICONTROL Create]**
      * To enable the Cloud Configurations option for an existing folder:
         1. **[!UICONTROL Properties]**
         1. **[!UICONTROL Cloud Configurations]**
         1. Selecteer **[!UICONTROL Save & Close]** om de configuratie op te slaan en het dialoogvenster af te sluiten.

1. Configureer de Cloud Service:
   1. ![](assets/tools-1.png)**[!UICONTROL Cloud Services]****[!UICONTROL reCAPTCHA]**
   1. Select a Configuration Container, created or updated in previous section. **[!UICONTROL Create]**
   1. **[!UICONTROL Title]****[!UICONTROL Name]****[!UICONTROL Site Key]****[!UICONTROL Secret Key]** **[!UICONTROL Create]**

   ![](/help/forms/assets/captcha-configuration.gif)

   Zodra de dienst reCAPTCHA wordt gevormd, is het beschikbaar voor gebruik in een AanpassingsVorm. Voor meer informatie, zie [ gebruikend Google reCAPTCHA in een Aanpassende Vorm ](#using-reCAPTCHA).

## Google reCAPTCHA gebruiken in een adaptief formulier {#using-reCAPTCHA}

ReCAPTCHA gebruiken in Adaptive Forms:

1. Open je AEM Forms as a Cloud Service exemplaar.
1. **[!UICONTROL Forms]****[!UICONTROL Forms and Documents]**
1. **[!UICONTROL Properties]** **[!UICONTROL Configuration Container]****[!UICONTROL Save & Close]**

   [](#connect-your-forms-environment-with-recaptcha-service-by-google)

   ![](/help/forms/assets/captcha-properties.png)

1. **[!UICONTROL Edit]** Het adaptieve formulier wordt geopend in de Adaptive Forms Editor.
1. Sleep de component **[!UICONTROL Adaptive Form reCAPTCHA]** vanuit de componentbrowser naar het adaptieve formulier.

   Google reCAPTCHA validation is time-sensitive and expires in about a couple of minutes. Daarom wordt aangeraden de component **[!UICONTROL Adaptive Form reCAPTCHA]** vlak voor de knop **[!UICONTROL Submit]** te plaatsen.

1. **[!UICONTROL Adaptive Form reCAPTCHA]**![](assets/configure-icon.svg) It opens the properties dialog. Specify the following mandatory properties:
   * **[!UICONTROL Name]**
   * **[!UICONTROL CAPTCHA Configuration]:** Selecteer een Cloud-configuratie die is geconfigureerd om het Google reCAPTCHA-dialoogvenster weer te geven voor het formulier. You can have multiple Cloud Configurations in your environment for similar purpose. Kies de service dus zorgvuldig. Als geen dienst vermeld is, zie [ uw milieu van AEM Forms met de dienst reCAPTCHA door Google ](#connect-your-forms-environment-with-recaptcha-service-by-google) verbinden om te leren hoe te om een Cloud Service tot stand te brengen die uw milieu van AEM Forms met de dienst reCAPTCHA door Google verbindt.
   * **Grootte Captcha:** U kunt de vertoningsgrootte van Google reCAPTCHA uitdagingsdialoog selecteren. Gebruik de optie **[!UICONTROL Compact]** om een klein formaat weer te geven en de optie **[!UICONTROL Normal]** om een relatief groot Google reCAPTCHA-uitdagingsdialoogvenster weer te geven.

1. Selecteer **[!UICONTROL Done]** .

   **** It is displayed on all the Adaptive Forms which are configured to use the Google reCAPTCHA service.

   Now, only legitimate forms, in which the form filler successfully clears the challenge posed by the Google reCAPTCHA service, are allowed for submission.
   ![](/help/forms/assets/google-recaptcha-v2.png)

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

## Frequently Asked Questions

******** Also, it is not recommended to use Captcha component in a fragment or a panel marked for lazy loading.

## See Also {#see-also}

{{see-also}}