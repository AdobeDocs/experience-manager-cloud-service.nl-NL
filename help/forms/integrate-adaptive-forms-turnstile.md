---
title: Hoe wordt Turnstile gebruikt in een AEM adaptieve vorm?
description: Verbeter de formulierbeveiliging met de Turnstile-service zonder moeite. Stap-voor-stap gids binnen!
topic-tags: Adaptive Forms, author
feature: Adaptive Forms, Foundation Components
hide: true
hidefromtoc: true
source-git-commit: 54914728ee892f14ab8d669051504a52942a6c01
workflow-type: tm+mt
source-wordcount: '806'
ht-degree: 0%

---

# Verbind uw AEM Forms-omgeving met Turnstift {#connect-your-forms-environment-with-turnstile-service}

<span class="preview"> Dit onderdeel valt onder het programma Vroege adoptie. U kunt vanaf uw officiële e-mailadres naar aem-forms-ea@adobe.com schrijven om deel te nemen aan het programma voor vroege adoptie en toegang tot de functie te vragen. </span>


Cloudflare Turnstile Captcha is een veiligheidsmaatregel die tot doel heeft formulieren en sites te beschermen tegen geautomatiseerde bots, kwaadaardige aanvallen, spam en ongewenst geautomatiseerd verkeer. Er wordt een selectievakje weergegeven bij het verzenden van formulieren om te controleren of het formulier menselijk is, voordat het formulier kan worden verzonden. AEM Forms as a Cloud Service ondersteunt Turnstile Captcha in Adaptive Forms.

<!-- ![Turnstile](assets/Turnstile-challenge.png)-->

## Vereisten om de AEM Forms-omgeving te integreren met Turnstile {#prerequisite}

Om Turnstile voor de Componenten van de Kern van AEM Forms te vormen, moet u verkrijgen [Turnstile sitekey en geheime sleutel](https://developers.cloudflare.com/turnstile/get-started/) van de website van Turnstile.

## Stappen voor het configureren van Turnstile voor AEM Forms{#steps-to-configure-turnstile}

1. Maak een configuratiecontainer in de as a Cloud Service AEM Forms-omgeving. Een configuratiecontainer bevat Cloud Configurations die worden gebruikt om AEM te verbinden met externe services. Om een Container van de Configuratie te creëren en te vormen om uw milieu van AEM Forms met Turnstile te verbinden:
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
   1. Ga naar de AEM ![gereedschappen-1](assets/tools-1.png) > **[!UICONTROL Cloud Services]** en selecteert u **[!UICONTROL Turnstile]**.
      ![Turnstile in ui](assets/turnstile-in-ui.png)
   1. Selecteer een configuratiecontainer, gecreeerd of bijgewerkt, zoals die in de vorige sectie wordt beschreven. Selecteren **[!UICONTROL Create]**.
      ![Configuratietransiast](assets/config-hcaptcha.png)
   1. Opgeven **[!UICONTROL Widget Type]** zoals beheerd, kan het widgettype veranderen wat van de sleutel afhangt die in eerste instantie wordt verkregen; **[!UICONTROL Title]**, **[!UICONTROL Name]**, **[!UICONTROL Site Key]**, en **[!UICONTROL Secret Key]** voor Turnstile [verkregen in eerste instantie](#prerequisite). Selecteren **[!UICONTROL Create]**.

      ![Configureer de Cloud Service om uw AEM Forms-omgeving te verbinden met Turnstim](assets/config-turntstile.png)

>[!NOTE]
> Gebruikers hoeven de URL voor JavaScript-validatie aan de clientzijde en de URL voor validatie aan de serverzijde niet aan te passen, omdat deze al zijn voorgevuld voor Microsoft-validatie.

Zodra de Turnstile Captcha dienst wordt gevormd, is het beschikbaar voor gebruik in een AanpassingsVorm.

## Draaien in een adaptieve vorm gebruiken{#using-turnstile-foundation-components}

1. Open uw as a Cloud Service AEM Forms-exemplaar.
1. Ga naar **[!UICONTROL Forms]** > **[!UICONTROL Forms and Documents]**.
1. Selecteer een adaptief formulier en selecteer **[!UICONTROL Properties]**. Voor de **[!UICONTROL Configuration Container]** Selecteer de configuratiecontainer die de Cloud Configuration bevat die AEM Forms met Turnstile verbindt, en selecteer **[!UICONTROL Save & Close]**.

   Als u niet zulk een Container van de Configuratie hebt, zie sectie [Verbind uw AEM Forms-omgeving met Turnstift](#connect-your-forms-environment-with-turnstile-service) om te leren hoe te om een Container van de Configuratie te creëren.

   ![Configuratiecontainer selecteren](/help/forms/assets/captcha-properties.png)

1. Selecteer een adaptief formulier en selecteer **[!UICONTROL Edit]**. Het adaptieve formulier wordt geopend in de Adaptive Forms Editor.
1. Sleep vanuit de componentbrowser de **[!UICONTROL Captcha]** naar het adaptieve formulier.
1. Selecteer de **[!UICONTROL Captcha]** component en klik op eigenschappen ![Pictogram Eigenschappen](assets/configure-icon.svg) pictogram. Hiermee wordt het dialoogvenster met eigenschappen geopend.

   ![Instellingen](assets/turnstile-setting-v1.png)

   Geef de volgende eigenschappen op:

   * **[!UICONTROL Title]:** Als u de titel voor de component Captcha opgeeft, kunt u een formuliercomponent gemakkelijk identificeren met zijn unieke naam, zowel in het formulier als in de regeleditor.
   * **[!UICONTROL Validation Message]:** Geef een validatiebericht op voor het valideren van Captcha bij het verzenden van formulieren.
   * **[!UICONTROL Validate Captcha]:** U kunt een van de opties selecteren om Captcha te valideren:
      * Bij verzending van formulier
      * Op een gebruikersactie.
   * **[!UICONTROL Captcha Service]:** Selecteer uw dienst Captcha, hier selecteert u de dienst van het Draaien van de Wolk Captcha.
   * **[!UICONTROL Captcha Configuration]:** Selecteer een cloudconfiguratie die is geconfigureerd voor Turnstile. Hier selecteert u bijvoorbeeld de **beheerde sleutel**.
     >[!NOTE]
     >U kunt voor een vergelijkbaar doel meerdere Cloud Configurations in uw omgeving gebruiken. Kies de service dus zorgvuldig. Als er geen service wordt vermeld, raadpleegt u [Verbind uw AEM Forms-omgeving met Turnstift](#connect-your-forms-environment-with-turnstile-service) om te leren hoe u een Cloud Service maakt die uw AEM Forms-omgeving verbindt met de Turnstile-service.

   * **Foutbericht:** Geef het foutbericht op dat aan de gebruiker moet worden weergegeven wanneer het verzenden van Captcha mislukt.
   * **Grootte captcha:** U selecteert de weergavegrootte van het dialoogvenster Turnstile-uitdaging. Gebruik de **[!UICONTROL Compact]** als u een klein formaat en de **[!UICONTROL Normal]** optie om een relatief groot Turnstile-uitdagingsdialoog te tonen.


     >[!NOTE]
     >Dit is van toepassing op het widgettype Beheerd en Niet-interactief. Als het widgettype onzichtbaar is, is de eigenschap size niet vereist en is deze uitgeschakeld.

1. Selecteren **[!UICONTROL Done]**.

Alleen legitieme formulieren waarin de invuller van het formulier de uitdaging van de Turnstile-service met succes heeft verholpen, kunnen nu worden verzonden.

![Turnstile Challenge](assets/turnstile-challenge.png)

## Veelgestelde vragen

* **V: Kan ik meer dan één Captcha-component in een adaptieve vorm gebruiken?**
* **Ans:** Het gebruik van meerdere Captcha-componenten in een adaptief formulier wordt niet ondersteund. Het wordt ook afgeraden een Captcha-component te gebruiken in een fragment of een deelvenster dat is gemarkeerd voor wazig laden.

## Zie ook {#see-also}

{{see-also}}