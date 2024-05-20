---
title: Hoe wordt Turnstile gebruikt in een AEM Adaptive Form Core-component?
description: Verbeter de formulierbeveiliging met de Turnstile-service zonder moeite. Stap-voor-stap gids binnen!
topic-tags: Adaptive Forms, author
feature: Adaptive Forms, Core Components
hide: true
hidefromtoc: true
source-git-commit: a8a31bae0f937aa8941d258af648d6be030a9fac
workflow-type: tm+mt
source-wordcount: '745'
ht-degree: 0%

---

# Verbind uw AEM Forms-omgeving met Turnstift {#connect-your-forms-environment-with-turnstile-service}

<span class="preview"> Dit onderdeel valt onder het programma Vroege adoptie. U kunt vanaf uw officiële e-mailadres naar aem-forms-ea@adobe.com schrijven om deel te nemen aan het programma voor vroege adoptie en toegang tot de functie te vragen. </span>

Cloudflare Turnstile Captcha is een veiligheidsmaatregel die tot doel heeft formulieren en sites te beschermen tegen geautomatiseerde bots, kwaadaardige aanvallen, spam en ongewenst geautomatiseerd verkeer. Er wordt een selectievakje weergegeven bij het verzenden van formulieren om te controleren of het formulier menselijk is, voordat het formulier kan worden verzonden. AEM Forms as a Cloud Service ondersteunt Turnstile Captcha in Adaptive Forms Core Components.

<!-- ![Turnstile](assets/Turnstile-challenge.png)-->

## Vereisten om de AEM Forms-omgeving te integreren met Turnstile Captcha {#prerequisite}

Om Turnstile voor de Componenten van de Kern van AEM Forms te vormen, moet u verkrijgen [Turnstile sitekey en geheime sleutel](https://developers.cloudflare.com/turnstile/get-started/) van de website van Turnstile.

## Stappen voor het configureren van Turnstile {#steps-to-configure-hcaptcha}

Voer de volgende stappen uit om AEM Forms te integreren met de Turnstile-service:

1. Maak een configuratiecontainer in de as a Cloud Service AEM Forms-omgeving. Een configuratiecontainer bevat Cloud Configurations die worden gebruikt om AEM te verbinden met externe services. Om een Container van de Configuratie te creëren en te vormen om uw milieu van AEM Forms met Turnstile te verbinden:
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
   1. Ga naar de AEM ![gereedschappen-1](assets/tools-1.png) > **[!UICONTROL Cloud Services]** en selecteert u **[!UICONTROL Turnstile]**.
      ![Turnstile in ui](assets/turnstile-in-ui.png)
   1. Selecteer een configuratiecontainer, gecreeerd of bijgewerkt, zoals die in de vorige sectie wordt beschreven. Selecteren **[!UICONTROL Create]**.
      ![Configuratietransiast](assets/config-hcaptcha.png)
   1. Opgeven **[!UICONTROL Widget Type]** zoals beheerd, **[!UICONTROL Title]**, **[!UICONTROL Name]**, **[!UICONTROL Site Key]**, en **[!UICONTROL Secret Key]** voor Turnstile [verkregen in eerste instantie](#prerequisite).
   1. Klik op **[!UICONTROL Create]**.

      ![Configureer de Cloud Service om uw AEM Forms-omgeving te verbinden met Turnstim](assets/config-turntstile.png)

   >[!NOTE]
   > Gebruikers hoeven de URL voor JavaScript-validatie aan de clientzijde en de URL voor validatie aan de serverzijde niet aan te passen, omdat deze al zijn voorgevuld voor Microsoft-validatie.

   Zodra de Turnstile Captcha dienst wordt gevormd, is het beschikbaar voor gebruik in [Adaptief formulier op basis van kerncomponenten](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/introduction).

## Draaien gebruiken in een adaptieve Forms Core-component {#using-turnstile-core-components}

1. Open uw as a Cloud Service AEM Forms-exemplaar.
1. Ga naar **[!UICONTROL Forms]** > **[!UICONTROL Forms and Documents]**.
1. Selecteer een adaptief formulier en selecteer **[!UICONTROL Properties]**. Voor de **[!UICONTROL Configuration Container]** Selecteer de configuratiecontainer die de Cloud Configuration bevat die AEM Forms met Turnstile verbindt en selecteer **[!UICONTROL Save & Close]**.

   Als u niet zulk een Container van de Configuratie hebt, zie sectie [Verbind uw AEM Forms-omgeving met Turnstift](#connect-your-forms-environment-with-turnstile-service) om te leren hoe te om een Container van de Configuratie te creëren.

   ![Configuratiecontainer selecteren](/help/forms/assets/captcha-properties.png)

1. Selecteer een adaptief formulier en selecteer **[!UICONTROL Edit]**. Het adaptieve formulier wordt geopend in de Adaptive Forms Editor.
1. Sleep vanuit de componentbrowser de **[!UICONTROL Adaptive Form Turnstile]** naar het adaptieve formulier.
1. Selecteer de **[!UICONTROL Adaptive Form Turnstile]** component en klik eigenschappen ![Pictogram Eigenschappen](assets/configure-icon.svg) pictogram. Hiermee wordt het dialoogvenster met eigenschappen geopend. Geef de volgende eigenschappen op:

   ![Turnstile v2](assets/turnstile-settings-v2.png)

   * **[!UICONTROL Name]:** Als u de naam voor de component Captcha opgeeft, kunt u een formuliercomponent gemakkelijk identificeren met de unieke naam in zowel het formulier als de regeleditor.
   * **[!UICONTROL Title]:** Geef de titel voor de component Captcha op.
   * **[!UICONTROL Configuration Settings]:** Selecteer een cloudconfiguratie die is geconfigureerd voor Turnstile.
   * **[!UICONTROL Validation Message]:** Geef een validatiebericht op voor het valideren van Captcha bij het verzenden van formulieren.
   * **[!UICONTROL Script Validation Message]**: Met deze optie kunt u een bericht invoeren dat wordt weergegeven als de scriptvalidatie mislukt.
     >[!NOTE]
     >U kunt voor een vergelijkbaar doel meerdere Cloud Configurations in uw omgeving gebruiken. Kies de service dus zorgvuldig. Als er geen service wordt vermeld, raadpleegt u [Verbind uw AEM Forms-omgeving met Turnstift](#connect-your-forms-environment-with-turnstile-service) om te leren hoe u een Cloud Service maakt die uw AEM Forms-omgeving verbindt met de Turnstile-service.
   * **Foutbericht:** Geef het foutbericht op dat aan de gebruiker moet worden weergegeven wanneer het verzenden van Captcha mislukt.

1. Selecteren **[!UICONTROL Done]**.


Alleen legitieme formulieren waarin de invuller van het formulier de uitdaging van de Turnstile-service met succes heeft verholpen, kunnen nu worden verzonden.

![Turnstile Challenge](assets/turnstile-challenge.png)


## Veelgestelde vragen

* **V: Kan ik meer dan één Captcha-component in een adaptieve vorm gebruiken?**
* **Ans:** Het gebruik van meerdere Captcha-componenten in een adaptief formulier wordt niet ondersteund. Het wordt ook afgeraden een Captcha-component te gebruiken in een fragment of een deelvenster dat is gemarkeerd voor wazig laden.

## Zie ook {#see-also}

{{see-also}}
