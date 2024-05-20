---
title: Hoe wordt hCaptcha® gebruikt in een AEM Adaptive Form Core-component?
description: Verbeter de formulierbeveiliging zonder problemen met de hCaptcha®-service. Stap-voor-stap gids binnen!
topic-tags: Adaptive Forms, author
keywords: hCaptcha®-service, Adaptive Forms, CAPTCHA-uitdaging, Boot Prevention, Core Components, Security Formulierverzending, Preventie van formulierspam
feature: Adaptive Forms, Core Components
hide: true
hidefromtoc: true
source-git-commit: a8a31bae0f937aa8941d258af648d6be030a9fac
workflow-type: tm+mt
source-wordcount: '811'
ht-degree: 0%

---

# Sluit uw AEM Forms-omgeving aan met hCaptcha® {#connect-your-forms-environment-with-hcaptcha-service}

<span class="preview"> Dit onderdeel valt onder het programma Vroege adoptie. U kunt vanaf uw officiële e-mailadres naar aem-forms-ea@adobe.com schrijven om deel te nemen aan het programma voor vroege adoptie en toegang tot de functie te vragen. </span>

De service Captcha® beschermt uw formulieren tegen bots, spam en automatisch misbruik. Er wordt een widget selectievakje ingesteld en de reactie van de gebruiker geëvalueerd om te bepalen of deze een mens of bot is die met het formulier communiceert. Het verhindert de gebruiker om te werk te gaan als de test ontbreekt en de hulp maakt online transacties veilig door bots te houden spam of kwaadwillige activiteiten posten.

AEM Forms as a Cloud Service ondersteunt hCaptcha® in Adaptive Forms Core Components. U kunt dit gebruiken om een widget-uitdaging voor selectievakjes weer te geven bij het verzenden van een formulier.

<!-- ![hCaptcha®](assets/hCaptcha®-challenge.png)-->


## Vereisten om de AEM Forms-omgeving te integreren met hCaptcha® {#prerequisite}

Om hCaptcha® met AEM Forms te configureren, moet u de [Captcha® sitekey en geheime sleutel](https://docs.hcaptcha.com/switch/#get-your-hcaptcha-sitekey-and-secret-key) van de website van Captcha®.

## Stappen voor het configureren van hCaptcha® {#steps-to-configure-hcaptcha}

Voer de volgende stappen uit om AEM Forms te integreren met de service hCaptcha®:

1. Maak een configuratiecontainer in de as a Cloud Service AEM Forms-omgeving. Een configuratiecontainer bevat Cloud Configurations die worden gebruikt om AEM te verbinden met externe services. Om een Container van de Configuratie te creëren en te vormen om uw milieu van AEM Forms met hCaptcha® te verbinden:
   1. Open uw as a Cloud Service AEM Forms-exemplaar.
   1. Ga naar **[!UICONTROL Tools > General > Configuration Browser]**.
   1. In Browser van de Configuratie, kunt u een bestaande omslag selecteren of een omslag creëren. U kunt een map maken en de optie Cloud Configurations hiervoor inschakelen of de optie Cloud Configurations inschakelen voor een bestaande map:

      * Een map maken en de optie Cloud Configurations inschakelen:
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
   1. Opgeven **[!UICONTROL Title]**, **[!UICONTROL Name]**, **[!UICONTROL Site Key]**, en **[!UICONTROL Secret Key]** voor de hCaptcha®-service [verkregen in Voorwaarde](#prerequisite). Selecteren **[!UICONTROL Create]**.

      ![Configureer de Cloud Service om uw AEM Forms-omgeving te verbinden met hCaptcha®](assets/create-hcaptcha-config.png)

   >[!NOTE]
   > Gebruikers hoeven zich niet aan te passen [JavaScript-validatie-URL aan clientzijde](https://docs.hcaptcha.com/#add-the-hcaptcha-widget-to-your-webpage) en [URL voor validatie op de server](https://docs.hcaptcha.com/#verify-the-user-response-server-side) omdat deze al zijn voorgevuld voor hCaptcha®-validatie.

   Zodra de dienst hCAPTCHA wordt gevormd, is het beschikbaar voor gebruik in een [Adaptief formulier op basis van kerncomponenten](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/introduction).

## Gebruik hCaptcha® in een adaptieve Forms Core-component {#using-hCaptcha®-core-components}

1. Open uw as a Cloud Service AEM Forms-exemplaar.
1. Ga naar **[!UICONTROL Forms]** > **[!UICONTROL Forms and Documents]**.
1. Selecteer een adaptief formulier en selecteer **[!UICONTROL Properties]**. Voor de **[!UICONTROL Configuration Container]** Selecteer de configuratiecontainer die de Cloud Configuration bevat die AEM Forms verbindt met hCaptcha® en selecteer **[!UICONTROL Save & Close]**.

   Als u niet zulk een Container van de Configuratie hebt, zie sectie [Sluit uw AEM Forms-omgeving aan met hCaptcha®](#connect-your-forms-environment-with-hcaptcha-service) om te leren hoe te om een Container van de Configuratie te creëren.

   ![Configuratiecontainer selecteren](/help/forms/assets/captcha-properties.png)

1. Selecteer een adaptief formulier en selecteer **[!UICONTROL Edit]**. Het adaptieve formulier wordt geopend in de Adaptive Forms Editor.
1. Sleep vanuit de componentbrowser de **[!UICONTROL Adaptive Form hCaptcha®]** naar het adaptieve formulier.
1. Selecteer de **[!UICONTROL Adaptive Form hCaptcha®]** component en klik eigenschappen ![Pictogram Eigenschappen](assets/configure-icon.svg) pictogram. Hiermee wordt het dialoogvenster met eigenschappen geopend. Geef de volgende eigenschappen op:

   ![hCaptcha® v2](assets/config-hcaptcha-v2.png)

   * **[!UICONTROL Name]:** Als u de naam voor de component Captcha opgeeft, kunt u een formuliercomponent gemakkelijk identificeren met de unieke naam in zowel het formulier als de regeleditor.
   * **[!UICONTROL Title]:** Geef de titel voor de component Captcha op.
   * **[!UICONTROL Configuration Settings]:** Selecteer een cloudconfiguratie die is geconfigureerd voor hCaptcha®.
   * **Grootte captcha:** U kunt de weergavegrootte van het dialoogvenster Captcha®-uitdaging selecteren. Gebruik de **[!UICONTROL Compact]** als u een klein formaat en de **[!UICONTROL Normal]** optie om een relatief groot hCaptcha®-uitdagingsdialoogvenster weer te geven.<!-- or **[!UICONTROL Invisible]** to validate hCaptcha® without explicitly rendering the checkbox widget on the user interface. -->
   * **[!UICONTROL Validation Message]:** Geef een validatiebericht op voor uw Captcha-validatie bij het verzenden van formulieren.
   * **[!UICONTROL Script Validation Message]** - Met deze optie kunt u een bericht invoeren dat wordt weergegeven als de scriptvalidatie mislukt.
     >[!NOTE]
     >U kunt voor een vergelijkbaar doel meerdere Cloud Configurations in uw omgeving gebruiken. Kies de service dus zorgvuldig. Als er geen service wordt vermeld, raadpleegt u [Sluit uw AEM Forms-omgeving aan met hCaptcha®](#connect-your-forms-environment-with-hcaptcha-service) voor meer informatie over het maken van een Cloud Service die uw AEM Forms-omgeving aansluit op de hCaptcha®-service.
     <!--* **Error Message:** Provide the error message to display to the user when the Captcha submission fails.-->

1. Selecteren **[!UICONTROL Done]**.


Alleen legitieme formulieren waarin de invuller van het formulier de uitdaging van de hCaptcha®-service met succes heeft verholpen, kunnen nu worden verzonden. hCaptcha®

**Captcha® is a registered trademark of Intution Machines, Inc.**


## Veelgestelde vragen

* **V: Kan ik meer dan één Captcha-component in een adaptieve vorm gebruiken?**
* **Ans:** Het gebruik van meerdere Captcha-componenten in een adaptief formulier wordt niet ondersteund. Het wordt ook afgeraden een Captcha-component te gebruiken in een fragment of een deelvenster dat is gemarkeerd voor wazig laden.

## Zie ook {#see-also}

{{see-also}}
