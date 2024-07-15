---
title: Hoe wordt Google reCAPTCHA in een AEM adaptieve vorm gebruikt?
description: Verbeter de formulierbeveiliging zonder problemen met de Google reCAPTCHA-service. Stap-voor-stap gids binnen!
topic-tags: Adaptive Forms, author
keywords: De Google reCAPTCHA-service, Adaptive Forms, CAPTCHA-uitdaging, Boot Prevention, Core Components, Security Formulierverzending, Preventie van formulierspam
feature: Adaptive Forms, Core Components
exl-id: d116f979-efb6-4fac-8202-89afd1037b2c
role: User, Developer
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '889'
ht-degree: 0%

---

# Google reCAPTCHA gebruiken in een AEM adaptief formulier op basis van Core Components {#using-reCAPTCHA-in-adaptive-forms}

| Van toepassing op | Artikelkoppeling |
| -------- | ---------------------------- |
| Adaptief formulier op basis van kerncomponenten | Dit artikel |
| Adaptief formulier op basis van elementaire componenten | [ klik hier ](/help/forms/captcha-adaptive-forms.md) |

CAPTCHA (Complete Automated Public Turing test to tell Computers and Humans Apart) is een programma dat vaak wordt gebruikt bij online transacties om onderscheid te maken tussen mensen en geautomatiseerde programma&#39;s of bots. Het stelt een uitdaging en evalueert de reactie van de gebruiker om te bepalen of het een mens of bot is die met de site communiceert. Het verhindert de gebruiker om te werk te gaan als de test ontbreekt en de hulp maakt online transacties veilig door bots te houden spam of kwaadwillige doeleinden posten.

AEM Forms as a Cloud Service ondersteunt de volgende CAPTCHA-oplossingen:

* [Google reCAPTCHA](#connect-your-aem-forms-environment-with-recaptcha-service-by-google)
* [Cloudflare Turnstile](/help/forms/integrate-adaptive-forms-turnstile-core-components.md)
* [ hCaptcha ](/help/forms/integrate-adaptive-forms-hcaptcha-core-components.md)


## Verbind uw AEM Forms-omgeving met de reCAPTCHA-service van Google {#connect-your-forms-environment-with-recaptcha-service-by-google}

Auteurs van formulieren kunnen de reCAPTCHA-service van Google gebruiken om reCAPTCHA te implementeren in Adaptive Forms. Het biedt geavanceerde CAPTCHA-mogelijkheden om uw site te beschermen. Voor meer informatie over hoe reCAPTCHA werkt, zie [ Google reCAPTCHA ](https://developers.google.com/recaptcha/). [!DNL AEM Forms] als [!DNL Cloud Service] ondersteunt Google reCAPTCHA v2 in Adaptive Forms. U kunt het gebruiken om een CAPTCHA-uitdaging aan te bieden bij het verzenden van formulieren. Om uw AEM Forms-omgeving te verbinden met de reCAPTCHA-service van Google

1. Verkrijg [ reCAPTCHA API zeer belangrijk paar ](https://www.google.com/recaptcha/admin) van Google. Het omvat a **plaats sleutel** en a **geheime sleutel**.

   ![ creeer Google reCAPTCHA configuratie van de website van Google om reCAPTCHA Sleutels ](/help/forms/assets/google-captcha.gif) te verkrijgen
1. Maak een configuratiecontainer op uw AEM Forms as a Cloud Service omgeving. Een configuratiecontainer bevat Cloud Configurations die worden gebruikt om AEM te verbinden met externe services. Om een Container van de Configuratie te creëren en te vormen om uw milieu van AEM Forms met de dienst van reCAPTCHA aan te sluiten door Google:
   1. Open je AEM Forms as a Cloud Service exemplaar.
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

1. Configureer de Cloud Service:
   1. Voor uw AEM auteursinstantie, ga ![ hulpmiddelen-1 ](assets/tools-1.png) > **[!UICONTROL Cloud Services]** en selecteer **[!UICONTROL reCAPTCHA]**.
   1. Selecteer een Container van de Configuratie, die in vorige sectie wordt gecreeerd of wordt bijgewerkt. Selecteer **[!UICONTROL Create]** .
   1. Geef **[!UICONTROL Title]** , **[!UICONTROL Name]** , **[!UICONTROL Site Key]** en **[!UICONTROL Secret Key]** op voor de service reCAPTCHA (verkregen in stap 1). Selecteer **[!UICONTROL Create]** .

   ![ vorm de Cloud Service om uw milieu van AEM Forms met de dienst te verbinden reCAPTCHA door Google ](/help/forms/assets/captcha-configuration.gif)

   Zodra de dienst reCAPTCHA wordt gevormd, is het beschikbaar voor gebruik in een AanpassingsVorm. Voor meer informatie, zie [ gebruikend Google reCAPTCHA in een Aanpassende Vorm ](#using-reCAPTCHA).

## Google reCAPTCHA gebruiken in een adaptief formulier {#using-reCAPTCHA}

ReCAPTCHA gebruiken in Adaptive Forms:

1. Open je AEM Forms as a Cloud Service exemplaar.
1. Ga naar **[!UICONTROL Forms]** > **[!UICONTROL Forms and Documents]** .
1. Selecteer een adaptieve Forms en selecteer **[!UICONTROL Properties]** . Selecteer voor de optie **[!UICONTROL Configuration Container]** de configuratiecontainer die de Cloud Configuration bevat die AEM Forms verbindt met de reCAPTCHA-service van Google en selecteer **[!UICONTROL Save & Close]** .

   Als u geen dergelijke Container van de Configuratie hebt, zie sectie [ uw milieu van AEM Forms met de dienst reCAPTCHA door Google ](#connect-your-forms-environment-with-recaptcha-service-by-google) verbinden om te leren hoe te om zulk een Container van de Configuratie tot stand te brengen.

   ![ Uitgezochte Container van de Configuratie ](/help/forms/assets/captcha-properties.png)

1. Selecteer een adaptieve Forms en selecteer **[!UICONTROL Edit]** . Het adaptieve formulier wordt geopend in de Adaptive Forms Editor.
1. Sleep de component **[!UICONTROL Adaptive Form reCAPTCHA]** vanuit de componentbrowser naar het adaptieve formulier.

   De Google reCAPTCHA-validatie is tijdgevoelig en verloopt over een paar minuten. Daarom wordt aangeraden de component **[!UICONTROL Adaptive Form reCAPTCHA]** vlak voor de knop **[!UICONTROL Submit]** te plaatsen.

1. Selecteer de **[!UICONTROL Adaptive Form reCAPTCHA]** component en selecteer het eigenschappen ![ pictogram van Eigenschappen ](assets/configure-icon.svg) pictogram. Hiermee wordt het dialoogvenster met eigenschappen geopend. Geef de volgende verplichte eigenschappen op:
   * **[!UICONTROL Name]:** u kunt een formuliercomponent gemakkelijk identificeren met zijn unieke naam in zowel het formulier als de regeleditor, maar de naam mag geen spaties of speciale tekens bevatten.
   * **[!UICONTROL CAPTCHA Configuration]:** Selecteer een Cloud-configuratie die is geconfigureerd om het Google reCAPTCHA-dialoogvenster weer te geven voor het formulier. U kunt voor vergelijkbare doeleinden meerdere Cloud Configurations in uw omgeving gebruiken. Kies de service dus zorgvuldig. Als geen dienst vermeld is, zie [ uw milieu van AEM Forms met de dienst reCAPTCHA door Google ](#connect-your-forms-environment-with-recaptcha-service-by-google) verbinden om te leren hoe te om een Cloud Service tot stand te brengen die uw milieu van AEM Forms met de dienst reCAPTCHA door Google verbindt.
   * **Grootte Captcha:** U kunt de vertoningsgrootte van Google reCAPTCHA uitdagingsdialoog selecteren. Gebruik de optie **[!UICONTROL Compact]** om een klein formaat weer te geven en de optie **[!UICONTROL Normal]** om een relatief groot Google reCAPTCHA-uitdagingsdialoogvenster weer te geven.

1. Selecteer **[!UICONTROL Done]** .

   Nu, wordt **beschermd door reCAPTCHA** getoond op uw Aangepaste Vorm. Het wordt weergegeven op alle Adaptive Forms die zijn geconfigureerd om de Google reCAPTCHA-service te gebruiken.

   Nu kunnen alleen legitieme formulieren worden verzonden, waarin de invuller van het formulier de uitdaging van de Google reCAPTCHA-service met succes heeft verholpen.
   ![ Google die door reCAPTCHA badge ](/help/forms/assets/google-recaptcha-v2.png) wordt beschermd

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