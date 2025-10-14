---
title: Hoe kan ik een verzendactie naar Marketo Engage configureren voor formulieren?
description: Leer hoe u de verzendactie van het adaptieve formulier configureert voor het verzenden van gegevens naar Marketo Engage.
keywords: Gegevens naar Marketo verzenden, verzenden configureren als Verzenden naar Marketo Engage
feature: Adaptive Forms, Form Data Model
role: User, Developer
exl-id: 0683564b-1ac4-42b4-bc08-101c4fdef286
source-git-commit: 1be7bafc1d93a65a81eeb2f7e86cac33cde7aa35
workflow-type: tm+mt
source-wordcount: '760'
ht-degree: 0%

---

# De verzendactie naar Marketo Engage configureren voor bestaande formulieren

<span class="preview"> De functie is beschikbaar in het programma voor vroege adoptie. U kunt vanaf uw officiële e-mailadres naar aem-forms-ea@adobe.com schrijven om deel te nemen aan het programma voor vroege adoptie en toegang tot de functie te vragen. </span>

![Workflow](/help/forms/assets/workflow-marketo-3.png)

De adaptieve redacteur van Forms verstrekt **voorleggen aan Marketo Engage** actie om de Adaptieve gegevens van Forms naar Adobe Marketo Engage voor verwerking te verzenden. U kunt een bestaande Aangepaste Vorm vormen om gegevens aan [&#x200B; Adobe Marketo Engage &#x200B;](https://experienceleague.adobe.com/nl/docs/marketo/using/home) op voorlegging voor te leggen.

Er zijn verschillende verzendacties beschikbaar die niet in de verpakking staan en waarmee formulierverzendingen kunnen worden verwerkt. U kunt meer over deze opties leren in het [&#x200B; AanpassingsVorm voorlegt Artikel van de Actie &#x200B;](/help/forms/configure-submit-actions-core-components.md).

## Overwegingen bij het configureren van verzendactie naar Marketo Engage voor formulier

* Zorg ervoor dat het adaptieve formulier is geconfigureerd met de Marketo Engage-gegevensbron om gegevens naar Marketo Engage te verzenden wanneer het formulier wordt verzonden. Nochtans, kunt u de verzendactie aan alternatieven veranderen, bijvoorbeeld, **voorleggen aan OneDrive** of **voorleggen aan SharePoint**, zelfs als de vorm met het de gegevensschema van Marketo Engage wordt gevormd.

## Vereiste om de verzendhandeling voor een bestaand formulier te configureren naar Marketo Engage

Vereiste om de verzendhandeling naar Marketo Engage te configureren:

* Vorm de [&#x200B; gegevensbron van Marketo Engage voor AanpassingsVorm &#x200B;](/help/forms/use-marketo-engage-data-source-in-form.md) en verbind de vormelementen met de gebieden van Marketo Engage.

## Hoe te om verzendactie aan Marketo Engage voor bestaande vormen te vormen?

>[!VIDEO](https://video.tv.adobe.com/v/3442866/submit-action-marketo-engage-marketo-aem-aem-forms-engage)

<span> Deze video is alleen van toepassing op Core Components. Voor de Componenten van de UE/Foundation, gelieve naar het artikel te verwijzen.</span>


>[!BEGINTABS]

>[!TAB  Component van de Stichting ]

U kunt de verzendactie van een adaptief formulier configureren op basis van Foundation Components om gegevens naar Adobe Marketo Engage te verzenden. Voer de volgende stappen uit om de verzendactie naar Marketo Engage te configureren:

1. Meld u aan bij de [!DNL Experience Manager Forms] Author-instantie.
1. Open de Adaptieve Vorm voor het uitgeven en navigeer aan **[!UICONTROL Submission]** sectie van de Adaptieve eigenschappen van de Container van de Vorm en selecteer een voorleggingsactie zoals **voorleggen aan Marketo Engage**.
1. Klik op **[!UICONTROL Done]**.

![&#x200B; Marketo legt Actie &#x200B;](/help/forms/assets/marketo-engage-submit-action-af.png){width=50%, height=50%} voor

Na het vormen van voorlegt actie voor de Aangepaste Vorm als **voorleggen aan Marketo Engage**, kunt u gegevens naar Adobe Marketo Engage voor verwerking verzenden. De gegevens kunnen worden gebruikt voor het analyseren en optimaliseren van marketingcampagnes, het automatiseren van follow-up-e-mails en het activeren van workflows op basis van formulierverzendingen.

>[!TAB  Component van de Kern ]

U kunt de verzendactie van een adaptief formulier configureren op basis van kerncomponenten om gegevens naar Adobe Marketo Engage te verzenden. Voer de volgende stappen uit om de verzendactie naar Marketo Engage te configureren:

1. Open het adaptieve formulier voor bewerking.
1. Open de inhoudsstructuur en selecteer de **[!UICONTROL Guide Container]** .
1. Klik het AanpassingsEigenschappen van de Container van de Vorm ![&#x200B; AanpassingsContainer eigenschappen &#x200B;](/help/forms/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer om verzendactie te configureren wordt geopend.
1. Open het **[!UICONTROL Submission]** lusje en selecteer voorlegt actie aangezien **aan Marketo Engage** voorlegt.
1. Klik op **[!UICONTROL Done]**.

![&#x200B; Marketo legt Actie &#x200B;](/help/forms/assets/marketo-engage-submit-action.png){width=50%, height=50%} voor

Na het vormen van voorlegt actie voor de Aangepaste Vorm als **voorleggen aan Marketo Engage**, kunt u gegevens naar Adobe Marketo Engage voor verwerking verzenden. De gegevens kunnen worden gebruikt voor het analyseren en optimaliseren van marketingcampagnes, het automatiseren van follow-up-e-mails en het activeren van workflows op basis van formulierverzendingen.

>[!TAB  Universele Redacteur ]

U kunt de verzendactie configureren van een adaptief formulier dat is geschreven in de Universal Editor om gegevens naar Adobe Marketo Engage te verzenden. Voer de volgende stappen uit om de verzendactie naar Marketo Engage te configureren:

1. Open het adaptieve formulier voor bewerking.
1. Klik **uitgeven de uitbreiding van de Eigenschappen van de Vorm** op de redacteur.
Het **de dialoogvakje van de Eigenschappen van de Vorm** verschijnt.

   >[!NOTE]
   >
   > * Als u niet **ziet geef de Eigenschappen van de Vorm** pictogram in uw Universele interface van de Redacteur uit, laat **toe geef de 3&rbrace; uitbreiding van de Eigenschappen van de Vorm &lbrace;in Extension Manager uit.**
   > * Verwijs naar het [&#x200B; artikel van de Hoogtepunten van de Eigenschap van 0&rbrace; Extension Manager om te leren hoe te om uitbreidingen in of onbruikbaar te maken in de Universele Redacteur.](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions)

1. Klik **Verzending** lusje en selecteer **[!UICONTROL Submit to Marketo Engage]** voorlegt actie.

   ![&#x200B; Marketo legt Actie &#x200B;](/help/forms/assets/marketo-engage-submit-action-ue.png) voor

1. Klik op **[!UICONTROL Save & Close]**.

Na het vormen van voorlegt actie voor de Aangepaste Vorm als **voorleggen aan Marketo Engage**, kunt u gegevens naar Adobe Marketo Engage voor verwerking verzenden. De gegevens kunnen worden gebruikt voor het analyseren en optimaliseren van marketingcampagnes, het automatiseren van follow-up-e-mails en het activeren van workflows op basis van formulierverzendingen.

>[!ENDTABS]

## Veelgestelde vraag (FAQ)

**Q: Kan u verzendactie voor vormen veranderen die om met het schema van Marketo Engage worden gevormd te verbinden?**
**A:** Door gebrek, **voorleggen aan Marketo** actie wordt geselecteerd wanneer een vorm wordt gevormd om met het schema van Marketo Engage te verbinden. U kunt de verzendactie voor de formulieren echter wijzigen als dat nodig is.

## Volgende stap

U kunt een AanpassingsVorm met de [&#x200B; bibliotheek van Munchkin &#x200B;](https://experienceleague.adobe.com/nl/docs/marketo/using/product-docs/administration/setup/munchkin) ook verbinden om het aantal bezoeken, klikken, en vormvoorlegging te volgen.

## Verwante artikelen

{{af-submit-action}}

## Zie ook

{{marketo-engage-see-also}}
