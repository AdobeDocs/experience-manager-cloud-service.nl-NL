---
title: Hoe maakt u uit meerdere stappen bestaande formulierreeks?
description: Met  [!DNL Experience Manager Forms] kunt u een reeks formulierdeelvensters definiëren waarmee gebruikers door een adaptief formulier kunnen navigeren en dit invullen.
role: User, Developer
level: Intermediate
feature: Adaptive Forms, Foundation Components
exl-id: 6b3f9131-db6b-451b-a932-b57d809222eb
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 0%

---

# Inleiding tot een formulierreeks die uit meerdere stappen bestaat {#introduction-to-multi-step-form-sequence}

<span class="preview"> de Adobe adviseert gebruikend de moderne en verlengbare gegevens vangen [ Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) voor [ het creëren van nieuwe Aangepaste Forms ](/help/forms/creating-adaptive-form-core-components.md) of [ het toevoegen van Aangepaste Forms aan de pagina&#39;s van AEM Sites ](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/introduction-form-sequence.html) |
| AEM as a Cloud Service | Dit artikel |

Met Adaptive Forms kunnen auteurs van formulieren heel eenvoudig ervaringen met het vastleggen van gegevens in meerdere stappen maken. De klasse wordt geleverd met ingebouwde ondersteuning voor het maken van meerdere deelvensters en het koppelen van elk deelvenster aan verschillende navigatiepatronen. Auteurs van formulieren kunnen formuliervelden groeperen in logische secties en een groep weergeven als deelvenster. De algemene navigatie tussen deelvensters wordt bepaald door de indeling van het deelvenster. Auteurs kunnen ervoor kiezen om deelvensters in verschillende lay-outs te rangschikken, bijvoorbeeld door de wizard-lay-out opeenvolgend te gebruiken of op een geïmproviseerde manier met de lay-out Tabbed. Voor informatie over paneellay-outs, zie [ mogelijkheden van de Lay-out van Aanpassings Forms ](layout-capabilities-adaptive-forms.md).

In een typisch voorbeeld van het invullen van formulieren zijn er meer stappen nodig dan alleen het vastleggen van gegevens. Een volledig formulier dat wordt verzonden, kan andere stappen bevatten, zoals het digitaal ondertekenen van het formulier, het controleren van de informatie die is ingevuld in het formulier, het verwerken van betalingen, enzovoort. Het verschilt van geval tot geval.

Als uw gebruikscase een set stappen voor het vastleggen van gegevens verplicht stelt of als er regels zijn die bepaalde stappen moeten volgen, biedt [!DNL Experience Manager Forms] een manier om die gemeenschappelijke structuur in alle formulieren af te dwingen. De vooraf ingestelde implementatie van de formulierstructuur definieert de reeks stappen voor een formulier. ![ Voorbeeld van een multi-step vormopeenvolging ](assets/formpipeline.png)

Voorbeeld van een formulierreeks die uit meerdere stappen bestaat

Laten we een voorbeeld nemen waarbij u een reeks moet maken voor het invullen, verifiëren, ondertekenen en bevestigen van een formulier. U kunt een dergelijke reeks als volgt maken:

1. Definieer een formuliersjabloon en voeg het vereiste deelvenster toe. Er moet één deelvenster zijn voor elke stap in de reeks. U kunt echter wel subdeelvensters in een deelvenster opnemen.

   In dit voorbeeld kunt u de volgende deelvensters toevoegen:

   * **[!UICONTROL Fill]**: Het bevat formuliervelden voor het vastleggen van gegevens. Hier kunt u geneste subdeelvensters opnemen om secties te maken voor verschillende soorten informatie, zoals persoonlijke gegevens, familiegegevens, financiële gegevens enzovoort.

   <!--* **[!UICONTROL Verify]**: It contains the **[!UICONTROL Verify]** component that can be used in an XFA-based Adaptive Form. It displays the information captured in the Fill panel in read-only mode for verification.-->


   * **[!UICONTROL E-sign]**: Het bevat de **[!UICONTROL Sign]** -component die in een op XFA gebaseerde adaptieve vorm kan worden gebruikt. De toepassing biedt de volgende ondertekeningsservices:

      * Adobe Document Cloud eSign-services
      * Krabbelhandtekening

   * **[!UICONTROL Confirmation]**: Deze bevat de component **[!UICONTROL Summary]** die een bericht weergeeft waarin de verzending van het formulier wordt bevestigd nadat een gebruiker het formulier heeft ondertekend en de stap Bevestigen (Samenvatting) in de reeks heeft bereikt. Auteurs kunnen de tekst van de [!UICONTROL Summary] -component configureren, een bedankbericht weergeven, een koppeling naar de gegenereerde PDF weergeven, enzovoort.

1. Selecteer de layout van het hoofddeelvenster als **[!UICONTROL Wizard]** .
1. Voer de overige stappen uit om de formuliersjabloon te maken. <!-- For more information, see [Creating a custom Adaptive Form template](custom-adaptive-forms-templates.md). -->

Nadat u de formuliervolgorde in de formuliersjabloon hebt gedefinieerd, kunt u er formulieren mee maken die de basisstructuur hebben gedefinieerd als de ingestelde reeks. U kunt het formulier echter altijd aan uw wensen aanpassen.


## Zie ook {#see-also}

{{see-also}}