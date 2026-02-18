---
title: Hoe te om automatisch geproduceerd Document van het malplaatje van het Verslag voor Aangepast Forms aan te passen?
description: Leer het automatisch gegenereerde Document of Record (DoR)-sjabloon voor Adaptive Forms downloaden, aanpassen en opnieuw uploaden met Adobe Forms Designer.
feature: Adaptive Forms, Core Components, Foundation Components
role: User, Developer
source-git-commit: 51ec9ef76a8f3f9b7bf2cdc25b03f72e286f586f
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 0%

---


# Het automatisch gegenereerde document van de recordsjabloon aanpassen

<span class="preview"> Dit artikel is op zowel **Componenten van de Kern** van toepassing en **de Componenten van de Stichting** gebaseerde Aangepaste Forms.</span>

Als u automatisch een Document of Record (DoR) genereert voor een adaptief formulier, maakt AEM Forms een standaardsjabloon op basis van de formulierstructuur. U kunt deze automatisch gegenereerde sjabloon aanpassen aan de vereisten voor branding en lay-out van uw organisatie.

De aanpassingsworkflow bestaat uit drie stappen:

1. Download de automatisch gegenereerde DoR-sjabloon van Forms Manager.
1. Wijzig de sjabloon met Adobe Forms Designer.
1. Upload de aangepaste sjabloon opnieuw naar AEM Forms en configureer deze als een aangepaste sjabloon.

## Vereisten {#prerequisites}

Voordat u begint, moet u het volgende doen:

* Toegang tot AEM Forms Manager met rechten voor het downloaden en uploaden van sjablonen.
* Adobe Forms Designer is op uw lokale computer geïnstalleerd.
* Een adaptief formulier met **[!UICONTROL Generate Document of Record]** ingeschakeld.

## Stap 1: Download automatisch gegenereerde DoR-sjabloon {#download-auto-generated-dor-template}

U kunt als volgt de automatisch gegenereerde DoR-sjabloon (XDP-bestand) voor uw adaptieve formulier downloaden:

1. Meld u aan bij de AEM Forms-auteur.
1. Ga naar **[!UICONTROL Forms]** > **[!UICONTROL Forms and Documents]**.
1. Selecteer het Adaptieve formulier waarvoor u de DoR-sjabloon wilt downloaden.
1. Open de eigenschappen van het geselecteerde adaptieve formulier.
1. Selecteer in het deelvenster Eigenschappen de optie **[!UICONTROL Download Document of Record]** om de automatisch gegenereerde DoR-sjabloon (XDP-bestand) te downloaden.
1. Sla het gedownloade XDP-bestand op uw lokale computer op.


## Stap 2: De sjabloon aanpassen met Adobe Forms Designer {#customize-template-using-designer}

Open de gedownloade XDP-sjabloon in Adobe Forms Designer en wijzig deze aan de behoeften van uw organisatie.

1. Open het gedownloade XDP dossier in **Adobe Forms Designer**.
1. Pas de sjabloon naar wens aan. Voorbeelden van aanpassingen zijn:

   * **Veelvoudige hoofdpagina&#39;s**: Voeg extra hoofdpagina&#39;s toe om verschillende lay-outs voor specifieke pagina&#39;s van het Document van Verslag te bepalen. Gebruik bijvoorbeeld een duidelijke eerste pagina met een briefhoofd van het bedrijf en volgende pagina&#39;s met een eenvoudigere indeling.
   * **de kleuren van de Doopvont en doopvontfamilies**: Verander de doopvontkleur, de grootte, en de familie om op uw collectieve merkrichtlijnen te richten.
   * **de elementen van de Douane**: Voeg elementen zoals bedrijflogo&#39;s, kopballen, footers, en ontkenningstekst toe om een verenigbare merkidentiteit te vestigen.
   * **lay-out en het stileren van de Pagina**: Pas marges, het uit elkaar plaatsen, en de algemene paginastructuur aan om leesbaarheid te verbeteren.
   * **het stileren van het Gebied en het plaatsen**: wijzig de verschijning en de positie van vormgebieden om uw aangewezen lay-out aan te passen.

1. Sla de aangepaste XDP-sjabloon op.

>[!NOTE]
>
> Verwijder of wijzig geen manuscripten in het malplaatje. Het wijzigen van scripts kan van invloed zijn op de gegevensbinding en het genereren van documenten.

## Stap 3: upload de aangepaste sjabloon opnieuw naar AEM {#reupload-customized-template}

Nadat u de sjabloon hebt aangepast, uploadt u deze naar AEM Forms en configureert u het adaptieve formulier om dit te gebruiken.

1. Upload de aangepaste XDP-sjabloon naar uw AEM Forms-instantie:
   * Ga naar **[!UICONTROL Forms]** > **[!UICONTROL Forms and Documents]**.
   * Selecteer **[!UICONTROL Create]** > **[!UICONTROL File Upload]** en upload het aangepaste XDP-bestand.

Configureer het formulier vervolgens met de aangepaste sjabloon. De stappen verschillen afhankelijk van of uw formulier is gebaseerd op de componenten Core of Foundation.

>[!BEGINTABS]

>[!TAB  Componenten van de Kern ]

Voor Adaptive Forms op basis van Core Components:

1. Open het Adaptieve formulier in de editor waarvoor u de aangepaste sjabloon wilt toepassen.
1. Selecteer de **[!UICONTROL Guide Container]** (hoofddeelvenster) in de inhoudsstructuur.
1. Open **[!UICONTROL Properties]** en klik op het pictogram **[!UICONTROL Document of Record]** (DoR) om de eigenschappen Document of Record te openen.
1. Open op het tabblad **[!UICONTROL Basic]** het vervolgkeuzemenu **[!UICONTROL Template]** en selecteer **[!UICONTROL Custom]** .
1. Blader naar de geüploade aangepaste XDP-sjabloon en selecteer deze.
1. Selecteer het vinkje dat u wilt opslaan.

   ![&#x200B; Document van de eigenschappen van het Verslag - Malplaatje dat aan Douane (de Componenten van de Kern) wordt geplaatst &#x200B;](/help/forms/assets/submission-pdf-dor-custom-template.png)

>[!TAB  Componenten van de Stichting ]

Voor Adaptive Forms op basis van Foundation Components:

1. Open het Adaptieve formulier in de editor waarvoor u de aangepaste sjabloon wilt toepassen.
1. Selecteer het hoofdvenster (formuliercontainer).
1. Open **[!UICONTROL Document of Record Properties]** (vanuit het deelvenster Eigenschappen of het tabblad DoR).
1. Open op het tabblad **[!UICONTROL Basic]** het vervolgkeuzemenu **[!UICONTROL Template]** en selecteer **[!UICONTROL Custom]** .
1. Blader naar de geüploade aangepaste XDP-sjabloon en selecteer deze.
1. Selecteer **[!UICONTROL Done]** voor opslaan.

   ![&#x200B; Document van de eigenschappen van het Verslag - Malplaatje dat aan Douane (de Componenten van de Stichting) wordt geplaatst &#x200B;](/help/forms/assets/dor-custom-template-foundation-components.png)

>[!ENDTABS]

Het adaptieve formulier gebruikt nu de aangepaste sjabloon bij het genereren van het Document of Record.

## De aangepaste sjabloon controleren {#verify-customized-template}

Bevestig dat de aangepaste sjabloon correct is toegepast:

1. Voer een testvermelding voor het adaptieve formulier in.
1. Genereer het document of record.
1. Controleer of de gegenereerde PDF uw aanpassingen weerspiegelt, zoals logo&#39;s, lettertypen, layoutwijzigingen en andere brandingelementen.

## Problemen oplossen {#troubleshooting}

| Probleem | Resolutie |
|---|---|
| De aangepaste sjabloon uploadt niet. | Controleer of het XDP-bestand geldig en niet beschadigd is. Controleer of u de vereiste machtigingen hebt om bestanden te uploaden naar AEM Forms. |
| Aanpassingen worden niet weergegeven in het gegenereerde document met opnamen. | Bevestig dat u de juiste aangepaste sjabloon hebt geselecteerd in de sectie **[!UICONTROL Document of Record Template Configuration]** van de formuliereigenschappen. |
| Problemen met lay-out of opmaak in de gegenereerde PDF. | Verifieer dat de aanpassingen in Adobe Forms Designer de [&#x200B; overeenkomsten van het basissjabloon &#x200B;](/help/forms/generate-document-of-record-core-components.md#base-template-conventions) volgen. Zorg ervoor dat alle elementen correct zijn gepositioneerd binnen de sjabloonstructuur. |

## Zie ook {#see-also}

* [Document met record genereren voor adaptieve Forms (kerncomponenten)](/help/forms/generate-document-of-record-core-components.md)
* [Document met records genereren voor adaptieve Forms (Foundation Components)](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md)
* [Basissjabloon van een document van record](/help/forms/generate-document-of-record-core-components.md#base-template-of-a-document-of-record)
* [De brandinggegevens aanpassen in Document of Record](/help/forms/generate-document-of-record-core-components.md#customize-the-branding-information-in-document-of-record)

