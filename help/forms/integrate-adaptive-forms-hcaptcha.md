---
title: Hoe kan hCaptcha&reg; in een AEM Adaptive Form worden gebruikt?
description: Verbeter de formulierbeveiliging met hCaptcha&reg; service zonder problemen. Stap-voor-stap gids binnen!
topic-tags: Adaptive Forms, author
keywords: hCaptcha&reg; service, Adaptive Forms, CAPTCHA-uitdaging, Bot-preventie, Formulierverzendbeveiliging, Formulierspampreventie
feature: Adaptive Forms, Foundation Components
role: User, Developer
exl-id: dc7ca723-1008-472a-b6eb-8e9ed6332a16
source-git-commit: 914139a6340f15ee77024793bf42fa30c913931e
workflow-type: tm+mt
source-wordcount: '932'
ht-degree: 0%

---

# Sluit uw AEM Forms-omgeving aan met hCaptcha® {#connect-your-forms-environment-with-hcaptcha-service}

<span class="preview"> Deze functie valt onder het programma Vroege adoptie. U kunt vanaf uw officiële e-mailadres naar aem-forms-ea@adobe.com schrijven om deel te nemen aan het programma voor vroege adoptie en toegang tot de functie te vragen. </span>

CAPTCHA (Complete Automated Public Turing test to tell Computers and Humans Apart) is een programma dat vaak wordt gebruikt bij online transacties om onderscheid te maken tussen mensen en geautomatiseerde programma&#39;s of bots. Het stelt een uitdaging en evalueert de reactie van de gebruiker om te bepalen of het een mens of bot is die met de site communiceert. Het verhindert de gebruiker om te werk te gaan als de test ontbreekt en de hulp maakt online transacties veilig door bots te houden spam of kwaadwillige doeleinden posten.

AEM Forms as a Cloud Service ondersteunt de volgende CAPTCHA-oplossingen:

* [&#x200B; hCaptcha &#x200B;](#integrate-aem-forms-environment-with-hcaptcha-captcha)
* [Cloudflare Turnstile](/help/forms/integrate-adaptive-forms-turnstile.md)
* [Google reCAPTCHA](/help/forms/captcha-adaptive-forms.md)

## AEM Forms-omgeving integreren met hCaptcha Captcha

De service Captcha® beschermt uw formulieren tegen bots, spam en automatisch misbruik. Er wordt een widget selectievakje ingesteld en de reactie van de gebruiker geëvalueerd om te bepalen of het een mens of bot is die met het formulier communiceert. Het verhindert de gebruiker om te werk te gaan als de test ontbreekt en de hulp maakt online transacties veilig door bots te houden spam of kwaadwillige activiteiten posten.

AEM Forms as a Cloud Service ondersteunt hCaptcha® in Adaptive Forms. U kunt dit gebruiken om een widget-uitdaging voor selectievakjes weer te geven bij het verzenden van een formulier.

<!-- ![hCaptcha&reg;](assets/hCaptcha&reg;-challenge.png)-->

## Vereisten om de AEM Forms-omgeving te integreren met hCaptcha® {#prerequisite}

Om hCaptcha® met AEM Forms te vormen, moet u [&#x200B; hCaptcha® sitekey en geheime sleutel &#x200B;](https://docs.hcaptcha.com/switch/#get-your-hcaptcha-sitekey-and-secret-key) van de website hCaptcha® verkrijgen.

## Stappen voor het configureren van hCaptcha® {#steps-to-configure-hcaptcha}

1. Maak een configuratiecontainer op uw AEM Forms as a Cloud Service-omgeving. Een configuratiecontainer bevat cloudconfiguraties waarmee AEM wordt verbonden met externe services. Om een Container van de Configuratie te creëren en te vormen om uw milieu van AEM Forms met hCaptcha® te verbinden:
   1. Open uw AEM Forms as a Cloud Service-exemplaar.
   1. Ga naar **[!UICONTROL Tools > General > Configuration Browser]** .
   1. In Browser van de Configuratie, kunt u een bestaande omslag selecteren of een omslag creëren. U kunt een map maken en de optie Cloud Configurations hiervoor inschakelen of de optie Cloud Configurations inschakelen voor een bestaande map:

      * **om een omslag tot stand te brengen en de optie van de Configuraties van de Wolk voor het toe te laten**:
         1. Klik op **[!UICONTROL Create]** in de Configuration Browser.
         1. Geef in het dialoogvenster Configuratie maken een naam, titel en selecteer de optie **[!UICONTROL Cloud Configurations]** .
         1. Klik op **[!UICONTROL Create]**.
      * De optie Cloud Configurations inschakelen voor een bestaande map:
         1. Selecteer de map in de Configuration Browser en selecteer **[!UICONTROL Properties]** .
         1. Schakel in het dialoogvenster Configuration Properties **[!UICONTROL Cloud Configurations]** in.
         1. Selecteer **[!UICONTROL Save & Close]** om de configuratie op te slaan en het dialoogvenster af te sluiten.

1. De Cloud Service configureren:
   1. Op uw de auteursinstantie van AEM, ga ![&#x200B; hulpmiddelen-1 &#x200B;](assets/tools-1.png) > **[!UICONTROL Cloud Services]** en selecteer **[!UICONTROL hCaptcha®]**.

      ![&#x200B; hCaptcha® in ui &#x200B;](assets/hcaptcha-in-ui.png)
   1. Selecteer een configuratiecontainer, gecreeerd of bijgewerkt, zoals die in de vorige sectie wordt beschreven. Selecteer **[!UICONTROL Create]** .

      ![&#x200B; Configuratie hCaptcha® &#x200B;](assets/config-hcaptcha.png)
   1. Specificeer **[!UICONTROL Title]**, **[!UICONTROL Name]**, **[!UICONTROL Site Key]**, en **[!UICONTROL Secret Key]** voor de dienst hCaptcha® [&#x200B; in eerste instantie wordt verkregen die &#x200B;](#prerequisite). Selecteer **[!UICONTROL Create]** .

      ![&#x200B; vorm Cloud Service om uw milieu van AEM Forms met hCaptcha® &#x200B;](assets/create-hcaptcha-config.png) te verbinden

>[!NOTE]
> De gebruikers moeten niet [&#x200B; cliënt-zijbevestiging URL van JavaScript &#x200B;](https://docs.hcaptcha.com/#add-the-hcaptcha-widget-to-your-webpage) en [&#x200B; server-zijbevestiging URL &#x200B;](https://docs.hcaptcha.com/#verify-the-user-response-server-side) wijzigen aangezien zij reeds voor bevestiging hCaptcha® worden voorgevuld. Voor sommige landen, kunnen de eindpunten verschillen, bezoek [&#x200B; hCaptcha® FAQs &#x200B;](https://docs.hcaptcha.com/faq#does-hcaptcha-support-access-by-users-in-china) voor meer informatie.

Zodra de dienst hCAPTCHA wordt gevormd, is het beschikbaar voor gebruik in een Aangepast Vorm.

## Gebruik hCaptcha® in een AanpassingsVorm {#using-hCaptcha®-foundation-components}

1. Open uw AEM Forms as a Cloud Service-exemplaar.
1. Ga naar **[!UICONTROL Forms]** > **[!UICONTROL Forms and Documents]** .
1. Selecteer een adaptief formulier en selecteer **[!UICONTROL Properties]** . Selecteer voor de optie **[!UICONTROL Configuration Container]** de configuratiecontainer die de Cloud Configuration bevat die AEM Forms verbindt met hCaptcha® en selecteer **[!UICONTROL Save & Close]** .

   Als u geen dergelijke Container van de Configuratie hebt, zie sectie [&#x200B; uw milieu van AEM Forms met hCaptcha® &#x200B;](#connect-your-forms-environment-with-hcaptcha-service) verbinden om te leren hoe te om een Container van de Configuratie tot stand te brengen.

   ![&#x200B; Uitgezochte Container van de Configuratie &#x200B;](/help/forms/assets/captcha-properties.png)

1. Selecteer een adaptief formulier en selecteer **[!UICONTROL Edit]** . Het adaptieve formulier wordt geopend in de Adaptive Forms Editor.
1. Sleep de component **[!UICONTROL Captcha]** vanuit de componentbrowser naar het adaptieve formulier.
1. Selecteer de **[!UICONTROL Captcha]** component en klik op eigenschappen ![&#x200B; pictogram van Eigenschappen &#x200B;](assets/configure-icon.svg) pictogram. Hiermee wordt het dialoogvenster met eigenschappen geopend.

   ![&#x200B; alt tekst &#x200B;](assets/hcaptcha-properties.png)

   Geef de volgende eigenschappen op:

   * **[!UICONTROL Title]:** Geef de titel voor de component Captcha op. U kunt een formuliercomponent gemakkelijk identificeren met zijn unieke naam, zowel in het formulier als in de regeleditor.
   * **[!UICONTROL Validation Message]:** Geef een validatiebericht op voor uw Captcha-validatie bij het verzenden van formulieren.
   * **[!UICONTROL Validate Captcha]:** u kunt één van de opties selecteren om Captcha te bevestigen:
      * Bij verzending van formulier
      * Op een gebruikersactie.
   * **[!UICONTROL Captcha Service]:** selecteer uw dienst Captcha, hier selecteert u de dienst hCaptcha®.
   * **[!UICONTROL Captcha Configuration]:** selecteer een Configuratie van de Wolk die voor hCaptcha® wordt gevormd.

     >[!NOTE]
     >
     > U kunt voor een vergelijkbaar doel meerdere Cloud Configurations in uw omgeving gebruiken. Kies de service dus zorgvuldig. Als geen dienst vermeld is, zie [&#x200B; uw milieu van AEM Forms met hCaptcha® &#x200B;](#connect-your-forms-environment-with-hcaptcha-service) verbinden om te leren hoe te om een Cloud Service tot stand te brengen die uw milieu van AEM Forms met de dienst hCaptcha® verbindt.

   * **Bericht van de Fout:** verstrek het foutenbericht aan vertoning aan de gebruiker wanneer de voorlegging Captcha ontbreekt.
   * **Grootte Captcha:** U selecteert de vertoningsgrootte van de de uitdagingsdialoog hCaptcha®. Gebruik de optie **[!UICONTROL Compact]** om een klein formaat weer te geven en de optie **[!UICONTROL Normal]** om een relatief groot hCaptcha®-provocatievenster weer te geven of **[!UICONTROL Invisible]** om hCaptcha® te valideren zonder de widget selectievakje expliciet in de gebruikersinterface weer te geven.

1. Selecteer **[!UICONTROL Done]** .

Alleen legitieme formulieren waarin de invuller van het formulier de uitdaging van de hCaptcha®-service met succes heeft verholpen, kunnen nu worden verzonden.

**hCaptcha® is een geregistreerd handelsmerk van de Machines van de Intusie, Inc.**

## Veelgestelde vragen

* **Q: Kan ik meer dan één component Captcha in een Aangepaste Vorm gebruiken?**
* **Ans:** het gebruiken van meer dan één component Captcha in een AanpassingsVorm wordt niet gesteund. Het wordt ook afgeraden een Captcha-component te gebruiken in een fragment of een deelvenster dat is gemarkeerd voor wazig laden.

## Zie ook {#see-also}

{{see-also}}
