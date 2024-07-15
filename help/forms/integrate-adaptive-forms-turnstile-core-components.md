---
title: Hoe wordt Turnstile gebruikt in een AEM Adaptive Form Core-component?
description: Verbeter de formulierbeveiliging met de Turnstile-service zonder moeite. Stap-voor-stap gids binnen!
topic-tags: Adaptive Forms, author
feature: Adaptive Forms, Core Components
hide: true
hidefromtoc: true
exl-id: e9c13228-0857-4936-9c39-12ed2bddf429
role: User, Developer
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '839'
ht-degree: 0%

---

# Verbind uw AEM Forms-omgeving met Turnstift {#connect-your-forms-environment-with-turnstile-service}

<span class="preview"> Deze functie valt onder het programma Vroege adoptie. U kunt vanaf uw officiële e-mailadres naar aem-forms-ea@adobe.com schrijven om deel te nemen aan het programma voor vroege adoptie en toegang tot de functie te vragen. </span>

CAPTCHA (Complete Automated Public Turing test to tell Computers and Humans Apart) is een programma dat vaak wordt gebruikt bij online transacties om onderscheid te maken tussen mensen en geautomatiseerde programma&#39;s of bots. Het stelt een uitdaging en evalueert de reactie van de gebruiker om te bepalen of het een mens of bot is die met de site communiceert. Het verhindert de gebruiker om te werk te gaan als de test ontbreekt en de hulp maakt online transacties veilig door bots te houden spam of kwaadwillige doeleinden posten.

AEM Forms as a Cloud Service ondersteunt de volgende CAPTCHA-oplossingen:


* [Cloudflare Turnstile](#integrate-aem-forms-environment-with-turnstile-captcha)
* [Google reCAPTCHA](/help/forms/captcha-adaptive-forms-core-components.md)
* [ hCaptcha ](/help/forms/integrate-adaptive-forms-hcaptcha-core-components.md)



<!-- ![Turnstile](assets/Turnstile-challenge.png)-->

## AEM Forms-omgeving integreren met Turnstile Captcha

Cloudflare Turnstile Captcha is een veiligheidsmaatregel die tot doel heeft formulieren en sites te beschermen tegen geautomatiseerde bots, kwaadaardige aanvallen, spam en ongewenst geautomatiseerd verkeer. Er wordt een selectievakje weergegeven bij het verzenden van formulieren om te controleren of het formulier menselijk is, voordat het formulier kan worden verzonden. AEM Forms as a Cloud Service ondersteunt Turnstile Captcha in Adaptive Forms Core Components.

### Vereisten om de AEM Forms-omgeving te integreren met Turnstile Captcha {#prerequisite}

Om Turnstile voor de Componenten van de Kern van AEM Forms te vormen, moet u [ Turnstile sitekey en geheime sleutel ](https://developers.cloudflare.com/turnstile/get-started/) van de Website van Turnstile verkrijgen.

### Draaien configureren {#steps-to-configure-hcaptcha}

Voer de volgende stappen uit om AEM Forms te integreren met de Turnstile-service:

1. Maak een configuratiecontainer op uw AEM Forms as a Cloud Service omgeving. Een configuratiecontainer bevat Cloud Configurations die worden gebruikt om AEM te verbinden met externe services. Om een Container van de Configuratie te creëren en te vormen om uw milieu van AEM Forms met Turnstile te verbinden:
   1. Open je AEM Forms as a Cloud Service exemplaar.
   1. Ga naar **[!UICONTROL Tools > General > Configuration Browser]** .
   1. In Browser van de Configuratie, kunt u een bestaande omslag selecteren of een omslag creëren. U kunt een map maken en de optie Cloud Configurations hiervoor inschakelen of de optie Cloud Configurations inschakelen voor een bestaande map:

      * Een map maken en de optie Cloud Configurations inschakelen:
         1. Klik op **[!UICONTROL Create]** in de Configuration Browser.
         1. Geef in het dialoogvenster Configuratie maken een naam, titel en selecteer de optie **[!UICONTROL Cloud Configurations]** .
         1. Klik op **[!UICONTROL Create]**.
      * De optie Cloud Configurations inschakelen voor een bestaande map:
         1. Selecteer de map in de Configuration Browser en selecteer **[!UICONTROL Properties]** .
         1. Schakel in het dialoogvenster Configuration Properties **[!UICONTROL Cloud Configurations]** in.
         1. Selecteer **[!UICONTROL Save & Close]** om de configuratie op te slaan en het dialoogvenster af te sluiten.

1. Configureer de Cloud Service:
   1. Voor uw AEM auteursinstantie, ga ![ hulpmiddelen-1 ](assets/tools-1.png) > **[!UICONTROL Cloud Services]** en selecteer **[!UICONTROL Turnstile]**.
      ![ Turnstile in ui ](assets/turnstile-in-ui.png)
   1. Selecteer een configuratiecontainer, gecreeerd of bijgewerkt, zoals die in de vorige sectie wordt beschreven. Selecteer **[!UICONTROL Create]** .
      ![ Turnstile van de Configuratie ](assets/config-hcaptcha.png)
   1. Specificeer **[!UICONTROL Widget Type]** zoals geleid, **[!UICONTROL Title]**, **[!UICONTROL Name]**, **[!UICONTROL Site Key]**, en **[!UICONTROL Secret Key]** voor de dienst van de Turnstiel [ die in voorwaarde ](#prerequisite) wordt verkregen.
   1. Klik op **[!UICONTROL Create]**.

      ![ vorm de Cloud Service om uw milieu van AEM Forms met Turnstile te verbinden ](assets/config-turntstile.png)

   >[!NOTE]
   > Gebruikers hoeven de URL voor JavaScript-validatie aan de clientzijde en de URL voor validatie aan de serverzijde niet aan te passen, omdat deze al zijn voorgevuld voor Microsoft-validatie.

   Zodra de Turnstile dienst Captcha wordt gevormd, is het beschikbaar voor gebruik in een [ Aangepaste Vorm die op de Componenten van de Kern ](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/introduction) wordt gebaseerd.

## Draaien in een adaptieve vorm gebruiken {#using-turnstile-core-components}

1. Open je AEM Forms as a Cloud Service exemplaar.
1. Ga naar **[!UICONTROL Forms]** > **[!UICONTROL Forms and Documents]** .
1. Selecteer een adaptief formulier en selecteer **[!UICONTROL Properties]** . Selecteer voor de optie **[!UICONTROL Configuration Container]** de configuratiecontainer die de Cloud Configuration bevat die AEM Forms met Turnstile verbindt en selecteer **[!UICONTROL Save & Close]** .

   Als u geen dergelijke Container van de Configuratie hebt, zie sectie [ uw milieu van AEM Forms met Draaien ](#connect-your-forms-environment-with-turnstile-service) verbinden om te leren hoe te om een Container van de Configuratie tot stand te brengen.

   ![ Uitgezochte Container van de Configuratie ](/help/forms/assets/captcha-properties.png)

1. Selecteer een adaptief formulier en selecteer **[!UICONTROL Edit]** . Het adaptieve formulier wordt geopend in de Adaptive Forms Editor.
1. Sleep vanuit de browser van de component de component **[!UICONTROL Adaptive Form Turnstile]** naar het adaptieve formulier of voeg deze toe.
1. Selecteer de **[!UICONTROL Adaptive Form Turnstile]** component en klik eigenschappen ![ pictogram van Eigenschappen ](assets/configure-icon.svg) pictogram. Hiermee wordt het dialoogvenster met eigenschappen geopend. Geef de volgende eigenschappen op:

   ![ Draai v2 ](assets/turnstile-settings-v2.png)

   * **[!UICONTROL Name]:** Geef de naam voor de component Captcha op. U kunt een formuliercomponent gemakkelijk identificeren met zijn unieke naam, zowel in het formulier als in de regeleditor.
   * **[!UICONTROL Title]:** specificeer de titel voor uw component Captcha.
   * **[!UICONTROL Configuration Settings]:** selecteer een Cloud-configuratie die voor Turnstile is geconfigureerd.
   * **[!UICONTROL Validation Message]:** Geef een validatiebericht op voor het valideren van Captcha bij het verzenden van formulieren.
   * **[!UICONTROL Script Validation Message]**: met deze optie kunt u een bericht invoeren dat wordt weergegeven als de scriptvalidatie mislukt.
     >[!NOTE]
     >U kunt voor een vergelijkbaar doel meerdere Cloud Configurations in uw omgeving gebruiken. Kies de service dus zorgvuldig. Als geen de dienst vermeld is, zie [ uw milieu van AEM Forms met Turnstile ](#connect-your-forms-environment-with-turnstile-service) verbinden om te leren hoe te om een Cloud Service tot stand te brengen die uw milieu van AEM Forms met de Dienst van de Draai verbindt.
   * **Bericht van de Fout:** verstrek het foutenbericht aan vertoning aan de gebruiker wanneer de voorlegging Captcha ontbreekt.

1. Selecteer **[!UICONTROL Done]** .


Alleen legitieme formulieren waarin de invuller van het formulier de uitdaging van de Turnstile-service met succes heeft verholpen, kunnen nu worden verzonden.

![ Veranderlijke Uitdaging ](assets/turnstile-challenge.png)


## Veelgestelde vragen

* **Q: Kan ik meer dan één component Captcha in een Aangepaste Vorm gebruiken?**
* **Ans:** het gebruiken van meer dan één component Captcha in een AanpassingsVorm wordt niet gesteund. Het wordt ook afgeraden een Captcha-component te gebruiken in een fragment of een deelvenster dat is gemarkeerd voor wazig laden.

## Zie ook {#see-also}

{{see-also}}
