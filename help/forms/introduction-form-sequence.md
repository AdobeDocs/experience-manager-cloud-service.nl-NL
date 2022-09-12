---
title: Hoe maakt u een uit meerdere stappen bestaande formulierreeks?
description: Met [!DNL Experience Manager Forms]kunt u een reeks formulierdeelvensters definiëren waarmee gebruikers door een adaptief formulier kunnen navigeren en dit kunnen invullen. Dig dieper door een gebruikscasebenadering als voorbeeld te nemen om multi-step vormopeenvolging tot stand te brengen.
feature: Adaptive Forms
role: User
level: Intermediate
exl-id: 6b3f9131-db6b-451b-a932-b57d809222eb
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# Inleiding tot een formulierreeks die uit meerdere stappen bestaat {#introduction-to-multi-step-form-sequence}

Met Adaptive Forms kunnen auteurs van formulieren heel eenvoudig ervaringen met het vastleggen van gegevens in meerdere stappen maken. De klasse wordt geleverd met ingebouwde ondersteuning voor het maken van meerdere deelvensters en het koppelen van elk deelvenster aan verschillende navigatiepatronen. Auteurs van formulieren kunnen formuliervelden groeperen in logische secties en een groep weergeven als deelvenster. De algemene navigatie tussen deelvensters wordt bepaald door de indeling van het deelvenster. Auteurs kunnen ervoor kiezen om deelvensters in verschillende lay-outs te rangschikken, bijvoorbeeld door de wizard-lay-out opeenvolgend te gebruiken of op een ad-hocmanier met de lay-out Tabbed. Voor informatie over paneellay-outs raadpleegt u [Lay-outmogelijkheden van adaptieve Forms](layout-capabilities-adaptive-forms.md).

In een typisch voorbeeld van het invullen van formulieren zijn er meer stappen nodig dan alleen het vastleggen van gegevens. Een volledig formulier dat wordt verzonden, kan andere stappen bevatten, zoals het digitaal ondertekenen van het formulier, het controleren van de informatie die is ingevuld in het formulier, het verwerken van betalingen, enzovoort. Het verschilt van geval tot geval.

Als uw gebruiksgeval een reeks stappen voor gegevens het vangen verplicht stelt of er verordeningen zijn die bepaalde te volgen stappen vereisen, [!DNL Experience Manager Forms] biedt een manier om die gemeenschappelijke structuur in verschillende formulieren te handhaven. De vooraf ingestelde implementatie van de formulierstructuur definieert de reeks stappen voor een formulier. ![Voorbeeld van een formulierreeks die uit meerdere stappen bestaat](assets/formpipeline.png)

Voorbeeld van een formulierreeks die uit meerdere stappen bestaat

Laten we een voorbeeld nemen waarbij u een reeks moet maken voor het invullen, verifiëren, ondertekenen en bevestigen van een formulier. U kunt een dergelijke reeks als volgt maken:

1. Definieer een formuliersjabloon en voeg het vereiste deelvenster toe. Er moet één deelvenster zijn voor elke stap in de reeks. U kunt echter wel subdeelvensters in een deelvenster opnemen.

   In dit voorbeeld kunt u de volgende deelvensters toevoegen:

   * **[!UICONTROL Fill]**: Het bevat formuliervelden voor het vastleggen van gegevens. Hier kunt u geneste subdeelvensters opnemen om secties te maken voor verschillende soorten informatie, zoals persoonlijke gegevens, familiegegevens, financiële gegevens enzovoort.

   <!--* **[!UICONTROL Verify]**: It contains the **[!UICONTROL Verify]** component that can be used in an XFA-based Adaptive Form. It displays the information captured in the Fill panel in read-only mode for verification.-->


   * **[!UICONTROL E-sign]**: Het bevat de **[!UICONTROL Sign]** -component die kan worden gebruikt in een op XFA gebaseerde adaptieve vorm. De toepassing biedt de volgende ondertekeningsservices:

      * Adobe Document Cloud eSign-services
      * Krabbelhandtekening
   * **[!UICONTROL Confirmation]**: Het bevat de **[!UICONTROL Summary]** een bericht wordt weergegeven waarin de verzending van het formulier wordt bevestigd nadat een gebruiker het formulier heeft ondertekend en de stap Bevestigen (overzicht) in de reeks heeft bereikt. Auteurs kunnen de tekst van de [!UICONTROL Summary] , toont een dank u bericht, toont een verbinding aan de geproduceerde PDF, etc.



1. De lay-out van het hoofddeelvenster selecteren als **[!UICONTROL Wizard]**.
1. Voer de overige stappen uit om de formuliersjabloon te maken. <!-- For more information, see [Creating a custom Adaptive Form template](custom-adaptive-forms-templates.md). -->

Nadat u de formuliervolgorde in de formuliersjabloon hebt gedefinieerd, kunt u er formulieren mee maken die de basisstructuur hebben gedefinieerd als de ingestelde reeks. U kunt het formulier echter altijd aan uw wensen aanpassen.
