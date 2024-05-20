---
title: Hoe wordt hCaptcha&reg gebruikt in een AEM adaptieve vorm?
description: Verbeter de formulierbeveiliging met hCaptcha&reg; service zonder problemen. Stap-voor-stap gids binnen!
topic-tags: Adaptive Forms, author
keywords: hCaptcha&reg; service, Adaptive Forms, CAPTCHA-uitdaging, Bot-preventie, beveiliging bij het verzenden van formulieren, formulierspampreventie
feature: Adaptive Forms, Foundation Components
hide: true
hidefromtoc: true
source-git-commit: d2c6514eb1f38b06dfa58daa03b781920b8928f6
workflow-type: tm+mt
source-wordcount: '934'
ht-degree: 0%

---


# Sluit uw AEM Forms-omgeving aan met hCaptcha® {#connect-your-forms-environment-with-hcaptcha-service}

<span class="preview"> Dit onderdeel valt onder het programma Vroege adoptie. U kunt vanaf uw officiële e-mailadres naar aem-forms-ea@adobe.com schrijven om deel te nemen aan het programma voor vroege adoptie en toegang tot de functie te vragen. </span>

CAPTCHA (Complete Automated Public Turing test to tell Computers and Humans Apart) is een programma dat vaak wordt gebruikt bij online transacties om onderscheid te maken tussen mensen en geautomatiseerde programma&#39;s of bots. Het stelt een uitdaging en evalueert de reactie van de gebruiker om te bepalen of het een mens of bot is die met de site communiceert. Het verhindert de gebruiker om te werk te gaan als de test ontbreekt en de hulp maakt online transacties veilig door bots te houden spam of kwaadwillige doeleinden posten.

AEM Forms as a Cloud Service ondersteunt de volgende CAPTCHA-oplossingen:

* [hCaptcha](#integrate-aem-forms-environment-with-hcaptcha-captcha)
* [Cloudflare Turnstile](/help/forms/integrate-adaptive-forms-turnstile.md)
* [Google reCAPTCHA](/help/forms/captcha-adaptive-forms.md)

## AEM Forms-omgeving integreren met hCaptcha Captcha

De service Captcha® beschermt uw formulieren tegen bots, spam en automatisch misbruik. Er wordt een widget selectievakje ingesteld en de reactie van de gebruiker geëvalueerd om te bepalen of het een mens of bot is die met het formulier communiceert. Het verhindert de gebruiker om te werk te gaan als de test ontbreekt en de hulp maakt online transacties veilig door bots te houden spam of kwaadwillige activiteiten posten.

AEM Forms as a Cloud Service ondersteunt hCaptcha® in Adaptive Forms Core Components. U kunt dit gebruiken om een widget-uitdaging voor selectievakjes weer te geven bij het verzenden van een formulier.

<!-- ![hCaptcha&reg;](assets/hCaptcha&reg;-challenge.png)-->

## Vereisten om de AEM Forms-omgeving te integreren met hCaptcha® {#prerequisite}

Om hCaptcha® met AEM Forms te configureren, moet u de [Captcha® sitekey en geheime sleutel](https://docs.hcaptcha.com/switch/#get-your-hcaptcha-sitekey-and-secret-key) van de website van Captcha®.

## Stappen voor het configureren van hCaptcha® {#steps-to-configure-hcaptcha}

1. Maak een configuratiecontainer in de as a Cloud Service AEM Forms-omgeving. Een configuratiecontainer bevat Cloud Configurations die worden gebruikt om AEM te verbinden met externe services. Om een Container van de Configuratie te creëren en te vormen om uw milieu van AEM Forms met hCaptcha® te verbinden:
   1. Open uw as a Cloud Service AEM Forms-exemplaar.
   1. Ga naar **[!UICONTROL Tools > General > Configuration Browser]**.
   1. In Browser van de Configuratie, kunt u een bestaande omslag selecteren of een omslag creëren. U kunt een map maken en de optie Cloud Configurations hiervoor inschakelen of de optie Cloud Configurations inschakelen voor een bestaande map:

      * **Een map maken en de optie Cloudinstellingen hiervoor inschakelen**:
         1. In Browser van de Configuratie, klik **[!UICONTROL Create]**.
         1. Geef in het dialoogvenster Configuratie maken een naam, titel en selecteer de optie **[!UICONTROL Cloud Configurations]** -optie.
         1. Klik op **[!UICONTROL Create]**.
      * De optie Cloud Configurations inschakelen voor een bestaande map:
         1. Selecteer de map in de configuratiegrowser en selecteer **[!UICONTROL Properties]**.
         1. Schakel in het dialoogvenster Configuratieeigenschappen de optie **[!UICONTROL Cloud Configurations]**.
         1. Selecteren **[!UICONTROL Save & Close]** om de configuratie op te slaan en het dialoogvenster af te sluiten.

1. Configureer de Cloud Service:
   1. Ga naar de AEM ![gereedschappen-1](assets/tools-1.png) > **[!UICONTROL Cloud Services]** en selecteert u **[!UICONTROL hCaptcha®]**.
      ![hCaptcha® in ui](assets/hcaptcha-in-ui.png)
   1. Selecteer een configuratiecontainer, gecreeerd of bijgewerkt, zoals die in de vorige sectie wordt beschreven. Selecteren **[!UICONTROL Create]**.
      ![Configuratie hCaptcha®](assets/config-hcaptcha.png)
   1. Opgeven **[!UICONTROL Title]**, **[!UICONTROL Name]**, **[!UICONTROL Site Key]**, en **[!UICONTROL Secret Key]** voor de hCaptcha®-service [verkregen in eerste instantie](#prerequisite). Selecteren **[!UICONTROL Create]**.

      ![Configureer de Cloud Service om uw AEM Forms-omgeving te verbinden met hCaptcha®](assets/create-hcaptcha-config.png)

>[!NOTE]
> Gebruikers hoeven zich niet aan te passen [JavaScript-validatie-URL aan clientzijde](https://docs.hcaptcha.com/#add-the-hcaptcha-widget-to-your-webpage) en [URL voor validatie op de server](https://docs.hcaptcha.com/#verify-the-user-response-server-side) omdat deze al zijn voorgevuld voor hCaptcha®-validatie. Voor sommige landen kunnen de eindpunten verschillen, bezoek [Veelgestelde vragen over Captcha®](https://docs.hcaptcha.com/faq#does-hcaptcha-support-access-by-users-in-china) voor meer informatie .

Zodra de dienst hCAPTCHA wordt gevormd, is het beschikbaar voor gebruik in een Aangepast Vorm.

## Captcha® gebruiken in een adaptieve vorm{#using-hCaptcha®-foundation-components}

1. Open uw as a Cloud Service AEM Forms-exemplaar.
1. Ga naar **[!UICONTROL Forms]** > **[!UICONTROL Forms and Documents]**.
1. Selecteer een adaptief formulier en selecteer **[!UICONTROL Properties]**. Voor de **[!UICONTROL Configuration Container]** Selecteer de configuratiecontainer die de Cloud Configuration bevat die AEM Forms met hCaptcha® verbindt, en selecteer **[!UICONTROL Save & Close]**.

   Als u niet zulk een Container van de Configuratie hebt, zie sectie [Sluit uw AEM Forms-omgeving aan met hCaptcha®](#connect-your-forms-environment-with-hcaptcha-service) om te leren hoe te om een Container van de Configuratie te creëren.

   ![Configuratiecontainer selecteren](/help/forms/assets/captcha-properties.png)

1. Selecteer een adaptief formulier en selecteer **[!UICONTROL Edit]**. Het adaptieve formulier wordt geopend in de Adaptive Forms Editor.
1. Sleep vanuit de componentbrowser de **[!UICONTROL Captcha]** naar het adaptieve formulier.
1. Selecteer de **[!UICONTROL Captcha]** component en klik op eigenschappen ![Pictogram Eigenschappen](assets/configure-icon.svg) pictogram. Hiermee wordt het dialoogvenster met eigenschappen geopend.

   ![alt-tekst](assets/hcaptcha-properties.png)

   Geef de volgende eigenschappen op:

   * **[!UICONTROL Title]:** Als u de titel voor de component Captcha opgeeft, kunt u een formuliercomponent gemakkelijk identificeren met zijn unieke naam, zowel in het formulier als in de regeleditor.
   * **[!UICONTROL Validation Message]:** Geef een validatiebericht op voor uw Captcha-validatie bij het verzenden van formulieren.
   * **[!UICONTROL Validate Captcha]:** U kunt een van de opties selecteren om Captcha te valideren:
      * Bij verzending van formulier
      * Op een gebruikersactie.
   * **[!UICONTROL Captcha Service]:** Selecteer uw Captcha-service, waar u de service hCaptcha® kiest.
   * **[!UICONTROL Captcha Configuration]:** Selecteer een cloudconfiguratie die is geconfigureerd voor hCaptcha®.
     >[!NOTE]
     >U kunt voor een vergelijkbaar doel meerdere Cloud Configurations in uw omgeving gebruiken. Kies de service dus zorgvuldig. Als er geen service wordt vermeld, raadpleegt u [Sluit uw AEM Forms-omgeving aan met hCaptcha®](#connect-your-forms-environment-with-hcaptcha-service) voor meer informatie over het maken van een Cloud Service die uw AEM Forms-omgeving aansluit op de hCaptcha®-service.

   * **Foutbericht:** Geef het foutbericht op dat aan de gebruiker moet worden weergegeven wanneer het verzenden van Captcha mislukt.
   * **Grootte captcha:** U selecteert de weergavegrootte van het dialoogvenster Captcha®-uitdaging. Gebruik de **[!UICONTROL Compact]** als u een klein formaat en de **[!UICONTROL Normal]** optie om een relatief groot hCaptcha®-uitdagingsdialoogvenster weer te geven of **[!UICONTROL Invisible]** om hCaptcha® te valideren zonder de widget selectievakje expliciet te renderen in de gebruikersinterface.

1. Selecteren **[!UICONTROL Done]**.

Alleen legitieme formulieren waarin de invuller van het formulier de uitdaging van de hCaptcha®-service met succes heeft verholpen, kunnen nu worden verzonden.

**Captcha® is a registered trademark of Intution Machines, Inc.**

## Veelgestelde vragen

* **V: Kan ik meer dan één Captcha-component in een adaptieve vorm gebruiken?**
* **Ans:** Het gebruik van meerdere Captcha-componenten in een adaptief formulier wordt niet ondersteund. Het wordt ook afgeraden een Captcha-component te gebruiken in een fragment of een deelvenster dat is gemarkeerd voor wazig laden.

## Zie ook {#see-also}

{{see-also}}
