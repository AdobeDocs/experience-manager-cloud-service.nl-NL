---
title: Hoe wordt Turnstile gebruikt in een AEM Adaptive Form Core-component?
description: Verbeter de formulierbeveiliging met de Turnstile-service zonder moeite. Stap-voor-stap gids binnen!
topic-tags: Adaptive Forms, author
feature: Adaptive Forms, Core Components
role: User, Developer
exl-id: e9c13228-0857-4936-9c39-12ed2bddf429
source-git-commit: 76301ca614ae2256f5f8b00c41399298c761ee33
workflow-type: tm+mt
source-wordcount: '865'
ht-degree: 0%

---

# Verbind uw AEM Forms-omgeving met Turnstift {#connect-your-forms-environment-with-turnstile-service}

<span class="preview"> Deze functie valt onder het programma Vroege adopter. U kunt vanaf uw officiële e-mailadres naar aem-forms-ea@adobe.com schrijven om deel te nemen aan het programma voor vroege adoptie en toegang tot de functie te vragen. </span>

CAPTCHA (Complete Automated Public Turing test to tell Computers and Humans Apart) is een programma dat vaak wordt gebruikt bij online transacties om onderscheid te maken tussen mensen en geautomatiseerde programma&#39;s of bots. Het stelt een uitdaging en evalueert de reactie van de gebruiker om te bepalen of het een mens of bot is die met de site communiceert. Het verhindert de gebruiker om te werk te gaan als de test ontbreekt en de hulp maakt online transacties veilig door bots te houden spam of kwaadwillige doeleinden posten.

AEM Forms as a Cloud Service ondersteunt de volgende CAPTCHA-oplossingen:


* [Turnstile](/help/forms/integrate-adaptive-forms-turnstile-core-components.md)
* [Google reCAPTCHA](/help/forms/captcha-adaptive-forms-core-components.md)
* [ hCaptcha ](/help/forms/integrate-adaptive-forms-hcaptcha-core-components.md)

<!-- ![Turnstile](assets/Turnstile-challenge.png)-->

## AEM Forms-omgeving integreren met Turnstile Captcha

Cloudflare Turnstile Captcha is een veiligheidsmaatregel die tot doel heeft formulieren en sites te beschermen tegen geautomatiseerde bots, kwaadaardige aanvallen, spam en ongewenst geautomatiseerd verkeer. Er wordt een selectievakje weergegeven bij het verzenden van formulieren om te controleren of het formulier menselijk is, voordat het formulier kan worden verzonden. AEM Forms as a Cloud Service ondersteunt Turnstile Captcha in Adaptive Forms Core Components.

### Vereisten om de AEM Forms-omgeving te integreren met Turnstile Captcha {#prerequisite}

Om Turnstile voor de Componenten van de Kern van AEM Forms te vormen, moet u [ Turnstile sitekey en geheime sleutel ](https://developers.cloudflare.com/turnstile/get-started/) van de Website van Turnstile verkrijgen.

### Draaien configureren {#steps-to-configure-hcaptcha}

Voer de volgende stappen uit om AEM Forms te integreren met de Turnstile-service:

1. Maak een configuratiecontainer op uw AEM Forms as a Cloud Service-omgeving. Een configuratiecontainer bevat cloudconfiguraties waarmee AEM wordt verbonden met externe services. Om een Container van de Configuratie te creëren en te vormen om uw milieu van AEM Forms met Turnstile te verbinden, volg de hieronder gegeven stappen:
   1. Open uw AEM Forms as a Cloud Service-exemplaar.
   1. Ga naar **[!UICONTROL Tools > General > Configuration Browser]** .
   1. Maak een nieuwe map in de Configuratiebrowser en schakel hiervoor Cloud Configurations in of schakel Cloud Configurations in voor een bestaande map, zoals hieronder wordt uitgelegd:

      * Om a **nieuwe omslag** tot stand te brengen en de Configuraties van de Wolk voor het toe te laten door de stappen te volgen:
         1. Klik op **[!UICONTROL Create]** in de Configuration Browser.
         1. Geef in het dialoogvenster Configuratie maken een naam, titel en selecteer de optie **[!UICONTROL Cloud Configurations]** .
         1. Klik op **[!UICONTROL Create]**.
      * Om de optie van de Configuraties van de Wolk voor een **bestaande omslag** toe te laten:
         1. Selecteer de bestaande map in de Configuration Browser en klik op **[!UICONTROL Properties]** .
         1. Schakel in het dialoogvenster Configuration Properties **[!UICONTROL Cloud Configurations]** in.
         1. Klik op **[!UICONTROL Save & Close]** om de configuratie op te slaan en af te sluiten.

1. De Cloud Service configureren:
   1. Op uw de auteursinstantie van AEM, ga ![ hulpmiddelen-1 ](assets/tools-1.png) > **[!UICONTROL Cloud Services]** en klik **[!UICONTROL Turnstile]**.
      ![ Turnstile in ui ](assets/turnstile-in-ui.png)
   1. Selecteer een configuratiecontainer, gecreeerd of bijgewerkt, zoals die in de vorige sectie wordt beschreven. Selecteer **[!UICONTROL Create]** .
      ![ Turnstile van de Configuratie ](assets/config-hcaptcha.png)
   1. Geef **[!UICONTROL Widget Type]** op als beheerd, niet-interactief of onzichtbaar. Meer over het Type van Widget, bezoek [ Veranderlijke Widget ](https://developers.cloudflare.com/turnstile/concepts/widget/).
   1. Specificeer **[!UICONTROL Title]**, **[!UICONTROL Name]**, **[!UICONTROL Site Key]**, en **[!UICONTROL Secret Key]** voor de dienst van de Draai [ in de voorwaarde wordt verkregen die ](#prerequisite).
   1. Klik op **[!UICONTROL Create]**.

      ![ vorm Cloud Service om uw milieu van AEM Forms met Turnstile te verbinden ](assets/config-turntstile-cc.png)

   >[!NOTE]
   >
   > Gebruikers hoeven de URL voor JavaScript-validatie aan de clientzijde en de URL voor validatie aan de serverzijde niet aan te passen, omdat deze al zijn voorgevuld voor Microsoft-validatie.

   Zodra de Turnstile dienst Captcha wordt gevormd, is het beschikbaar voor gebruik in een [ Aangepaste Vorm die op de Componenten van de Kern ](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/introduction) wordt gebaseerd.

## Draaien in een adaptieve vorm gebruiken {#using-turnstile-core-components}

1. Open uw AEM Forms as a Cloud Service-exemplaar.
1. Ga naar **[!UICONTROL Forms]** > **[!UICONTROL Forms and Documents]** .
1. Selecteer het adaptieve formulier en klik op **[!UICONTROL Properties]** . Selecteer in de sectie **[!UICONTROL Configuration Container]** de configuratiecontainer die de Cloud Configuration bevat die AEM Forms met Turnstile verbindt.
1. Klik op **[!UICONTROL Save & Close]**.

   Als u geen Container van de Configuratie hebt, zie sectie [ Draaien ](#steps-to-configure-hcaptcha) vormen om te leren hoe te om een Container van de Configuratie tot stand te brengen.

   ![ Uitgezochte Container van de Configuratie ](/help/forms/assets/captcha-properties.png)

1. Selecteer een adaptief formulier en klik op **[!UICONTROL Edit]** om een formulier te openen in de editor.
1. Sleep vanuit de browser van de component de component **[!UICONTROL Adaptive Form Turnstile]** naar het aangepaste formulier of voeg deze toe.
   ![ voeg Turnstile captcha component ](/help/forms/assets/turnstile-v2.png) toe
1. Selecteer de **[!UICONTROL Adaptive Form Turnstile]** component en klik eigenschappen ![ pictogram van Eigenschappen ](assets/configure-icon.svg) pictogram. Hiermee wordt het dialoogvenster met eigenschappen geopend. Geef de volgende eigenschappen op:

   ![ Draai v2 ](assets/turnstile-settings-for-v2.png)

   * **[!UICONTROL Name]:** Geef de naam voor de component Captcha op. U kunt een formuliercomponent gemakkelijk identificeren met zijn unieke naam, zowel in het formulier als in de regeleditor.
   * **[!UICONTROL Title]:** specificeer de titel voor uw component Captcha. U kunt RTF-tekst toestaan voor de titel en u kunt de titel ook verbergen door de selectievakjes in te schakelen.
   * **[!UICONTROL Configuration Settings]:** selecteer een Configuratie van de Wolk die voor de Turnstile dienst wordt gevormd Captcha.

     >[!NOTE]
     >
     >* U kunt voor een vergelijkbaar doel meerdere Cloud Configurations in uw omgeving gebruiken. Kies de service dus zorgvuldig. Als geen de dienst vermeld is, zie de sectie, [ Vorm Turnstile ](#steps-to-configure-hcaptcha), om te leren hoe te om een Container van de Configuratie tot stand te brengen om uw milieu van AEM Forms met de Dienst van Turnstile te verbinden.

   * **[!UICONTROL Validation]:** geef Captcha-validatie op in de vorm van een foutbericht:

      * **Bericht van de Fout:** verstrek het foutenbericht aan vertoning aan de gebruiker wanneer de voorlegging Captcha ontbreekt.

        >[!NOTE]
        >
        >* Er wordt alleen een foutbericht weergegeven als de CAPTCHA op de client is ingevuld.

1. Klik op **[!UICONTROL Done]**.


Alleen legitieme formulieren waarin de invuller van het formulier de uitdaging van de Turnstile-service met succes heeft verholpen, kunnen nu worden verzonden.

![ Veranderlijke Uitdaging ](assets/turnstile-challenge.png)


## Veelgestelde vragen

* **Q: Kan ik meer dan één component Captcha in een Aangepaste Vorm gebruiken?**
* **Ans:** het gebruiken van meer dan één component Captcha in een AanpassingsVorm wordt niet gesteund. Het wordt ook afgeraden een Captcha-component te gebruiken in een fragment of een deelvenster dat is gemarkeerd voor wazig laden.

## Zie ook {#see-also}

{{see-also}}
