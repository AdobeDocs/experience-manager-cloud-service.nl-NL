---
title: How to use hCaptcha&reg; in an AEM Adaptive Form Core Components?
description: Verbeter de formulierbeveiliging met hCaptcha&reg; service zonder problemen. Stap-voor-stap gids binnen!
topic-tags: Adaptive Forms, author
keywords: hCaptcha&reg; service, Adaptive Forms, CAPTCHA-uitdaging, botpreventie, Core Components, Formulierverzendbeveiliging, Formulierspampreventie
feature: Adaptive Forms, Core Components
hide: true
hidefromtoc: true
exl-id: 6c559df2-7b6a-42fe-b44c-29a782570a0c
role: User, Developer
source-git-commit: bba5e5d283da616baa57b788181af73d59d86ee3
workflow-type: tm+mt
source-wordcount: '908'
ht-degree: 0%

---

# Sluit uw AEM Forms-omgeving aan met hCaptcha® {#connect-your-forms-environment-with-hcaptcha-service}

<span class="preview"> Deze functie valt onder het programma Vroege adoptie. U kunt vanaf uw officiële e-mailadres naar aem-forms-ea@adobe.com schrijven om deel te nemen aan het programma voor vroege adoptie en toegang tot de functie te vragen. </span>

CAPTCHA (Complete Automated Public Turing test to tell Computers and Humans Apart) is een programma dat vaak wordt gebruikt bij online transacties om onderscheid te maken tussen mensen en geautomatiseerde programma&#39;s of bots. Het stelt een uitdaging en evalueert de reactie van de gebruiker om te bepalen of het een mens of bot is die met de site communiceert. Het verhindert de gebruiker om te werk te gaan als de test ontbreekt en de hulp maakt online transacties veilig door bots te houden spam of kwaadwillige doeleinden posten.

AEM Forms as a Cloud Service ondersteunt de volgende CAPTCHA-oplossingen:

* [Google reCAPTCHA](/help/forms/captcha-adaptive-forms-core-components.md)
* [](/help/forms/integrate-adaptive-forms-hcaptcha-core-components.md)

## Integrate AEM Forms environment with hCaptcha Captcha

hCaptcha® service protects your forms from bots, spam, and automated abuse. It poses a checkbox widget challenge and evaluates the user response to determine if it&#39;s a human or a bot interacting with the form. It prevents the user to proceed if the test fails and helps make online transactions secure by keeping bots from posting spam or malicious activities.

AEM Forms as a Cloud Service supports hCaptcha® in Adaptive Forms Core Components. You can use it to present a checkbox widget challenge on form submission.

<!-- ![hCaptcha&reg;](assets/hCaptcha&reg;-challenge.png)-->


### Vereisten om de AEM Forms-omgeving te integreren met hCaptcha® {#prerequisite}

Om hCaptcha® met AEM Forms te vormen, moet u [ hCaptcha® sitekey en geheime sleutel ](https://docs.hcaptcha.com/switch/#get-your-hcaptcha-sitekey-and-secret-key) van de website hCaptcha® verkrijgen.

### Captcha® configureren {#steps-to-configure-hcaptcha}

Voer de volgende stappen uit om AEM Forms te integreren met de service hCaptcha®:

1. Maak een configuratiecontainer op uw AEM Forms as a Cloud Service omgeving. A Configuration Container holds Cloud Configurations used to connect AEM to external services. To create and configure a Configuration Container to connect your AEM Forms environment with hCaptcha®:
   1. Open your AEM Forms as a Cloud Service instance.
   1. Ga naar **[!UICONTROL Tools > General > Configuration Browser]** .
   1. In Browser van de Configuratie, kunt u een bestaande omslag selecteren of een omslag creëren. U kunt een map maken en de optie Cloud Configurations hiervoor inschakelen of de optie Cloud Configurations inschakelen voor een bestaande map:

      * Een map maken en de optie Cloud Configurations inschakelen:
         1. Klik op **[!UICONTROL Create]** in de Configuration Browser.
         1. Geef in het dialoogvenster Configuratie maken een naam, titel en selecteer de optie **[!UICONTROL Cloud Configurations]** .
         1. Klik op **[!UICONTROL Create]**.
      * De optie Cloud Configurations inschakelen voor een bestaande map:
         1. Selecteer de map in de Configuration Browser en selecteer **[!UICONTROL Properties]** .
         1. **[!UICONTROL Cloud Configurations]**
         1. **[!UICONTROL Save & Close]**

1. Configure the Cloud Service:
   1. ![](assets/tools-1.png)**[!UICONTROL Cloud Services]****[!UICONTROL hCaptcha®]**
      ![ hCaptcha® in ui ](assets/hcaptcha-in-ui.png)
   1. Selecteer een configuratiecontainer, gecreeerd of bijgewerkt, zoals die in de vorige sectie wordt beschreven. Selecteer **[!UICONTROL Create]** .
      ![ Configuratie hCaptcha® ](assets/config-hcaptcha.png)
   1. Specificeer **[!UICONTROL Title]**, **[!UICONTROL Name]**, **[!UICONTROL Site Key]**, en **[!UICONTROL Secret Key]** voor de dienst hCaptcha® [ die in Vereiste ](#prerequisite) wordt verkregen. Selecteer **[!UICONTROL Create]** .

      ![](assets/create-hcaptcha-config.png)

   >[!NOTE]
   > [](https://docs.hcaptcha.com/#add-the-hcaptcha-widget-to-your-webpage)[](https://docs.hcaptcha.com/#verify-the-user-response-server-side)

   [](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/introduction)

## {#using-hCaptcha®-core-components}

1. Open your AEM Forms as a Cloud Service instance.
1. Ga naar **[!UICONTROL Forms]** > **[!UICONTROL Forms and Documents]** .
1. Selecteer een adaptief formulier en selecteer **[!UICONTROL Properties]** . Selecteer voor de optie **[!UICONTROL Configuration Container]** de configuratiecontainer die de Cloud Configuration bevat die AEM Forms verbindt met hCaptcha® en selecteer **[!UICONTROL Save & Close]** .

   Als u geen dergelijke Container van de Configuratie hebt, zie sectie [ uw milieu van AEM Forms met hCaptcha® ](#connect-your-forms-environment-with-hcaptcha-service) verbinden om te leren hoe te om een Container van de Configuratie tot stand te brengen.

   ![ Uitgezochte Container van de Configuratie ](/help/forms/assets/captcha-properties.png)

1. Selecteer een adaptief formulier en selecteer **[!UICONTROL Edit]** . The Adaptive Form opens in Adaptive Forms Editor.
1. **[!UICONTROL Adaptive Form hCaptcha®]**
1. **[!UICONTROL Adaptive Form hCaptcha®]**![](assets/configure-icon.svg) It opens the properties dialog. Specify the following properties:

   ![](assets/config-hcaptcha-v2.png)

   * **[!UICONTROL Name]:** Geef de naam voor de component Captcha op. U kunt een formuliercomponent gemakkelijk identificeren met zijn unieke naam, zowel in het formulier als in de regeleditor.
   * **[!UICONTROL Title]:** specificeer de titel voor uw component Captcha.
   * **[!UICONTROL Configuration Settings]:** selecteer een Configuratie van de Wolk die voor hCaptcha® wordt gevormd.
   * **** **[!UICONTROL Compact]****[!UICONTROL Normal]**<!-- or **[!UICONTROL Invisible]** to validate hCaptcha&reg; without explicitly rendering the checkbox widget on the user interface. -->
   * **[!UICONTROL Validation Message]**
   * **[!UICONTROL Script Validation Message]**
     >[!NOTE]
     >U kunt voor een vergelijkbaar doel meerdere Cloud Configurations in uw omgeving gebruiken. Kies de service dus zorgvuldig. Als geen dienst vermeld is, zie [ uw milieu van AEM Forms met hCaptcha® ](#connect-your-forms-environment-with-hcaptcha-service) verbinden om te leren hoe te om een Cloud Service tot stand te brengen die uw milieu van AEM Forms met de dienst hCaptcha® verbindt.
     <!--* **Error Message:** Provide the error message to display to the user when the Captcha submission fails.-->

1. Selecteer **[!UICONTROL Done]** .


Alleen legitieme formulieren waarin de invuller van het formulier de uitdaging van de hCaptcha®-service met succes heeft verholpen, kunnen nu worden verzonden. hCaptcha®

**hCaptcha® is een geregistreerd handelsmerk van de Machines van de Intusie, Inc.**


## Veelgestelde vragen

* **Q: Kan ik meer dan één component Captcha in een Aangepaste Vorm gebruiken?**
* **Ans:** het gebruiken van meer dan één component Captcha in een AanpassingsVorm wordt niet gesteund. Het wordt ook afgeraden een Captcha-component te gebruiken in een fragment of een deelvenster dat is gemarkeerd voor wazig laden.

## See Also {#see-also}

{{see-also}}
