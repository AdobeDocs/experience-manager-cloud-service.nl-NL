---
title: De meta-gegevensvormen van de invoer  [!DNL Admin View]  aan  [!DNL Assets View]
description: Dit artikel beschrijft hoe te om de meta-gegevensvorm in te voeren beschikbaar in  [!DNL Admin View]  aan  [!DNL Assets View]
contentOwner: AG
feature: Metadata
role: User, Admin
source-git-commit: 1ee93bee379ba48a9b42b13b5d11ff89f705b298
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 0%

---


# [!DNL Admin View] metagegevensformulieren importeren naar [!DNL Assets View] {#import-admin-view-metadata-forms-to-assets-view}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b> Dynamische Media Prime en Ultimate </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b> AEM Assets Ultimate </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b> integratie van AEM Assets met Edge Delivery Services </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b> Uitbreidbaarheid UI </b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuw </i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b> laat Dynamische Media Prime en Ultimate </b></a> toe
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b> Beste praktijken van het Onderzoek </b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b> Beste praktijken van Meta-gegevens </b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b> Content Hub </b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b> Dynamische Media met mogelijkheden OpenAPI </b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b> de ontwikkelaarsdocumentatie van AEM Assets </b></a>
        </td>
    </tr>
</table>

Met [!DNL Adobe Experience Manager Assets] kunt u metagegevensformulieren en de bijbehorende mapkoppelingen importeren van [!DNL Admin View] naar [!DNL Assets View] .

## Voordat u begint{#prerequisites-for-importing-metadata-forms-to-assets-view}

Controleer of u beheerdersrechten hebt om de metagegevensformulieren en de bijbehorende mapkoppelingen te importeren van [!DNL Admin View] naar [!DNL Assets View] .

## Metagegevensformulieren importeren naar [!DNL Assets View]{#import-metadata-forms-to-assets-view}

Als beheerder voert u de volgende stappen uit om de metagegevensformulieren die beschikbaar zijn in [!DNL Admin View] t/m [!DNL Assets View] te importeren:

1. Navigeer naar de [!DNL Assets View] startpagina en klik **[!UICONTROL &#x200B; Metadata Forms]** onder **[!UICONTROL Settings]** om de pagina **[!UICONTROL Metadata Forms]** weer te geven met de lijst met metagegevensformulieren die beschikbaar is in [!DNL Assets View] .
   ![ pagina van meta-gegevensvormen ](/help/assets/assets/metadata-forms-page.png)
1. Selecteer **[!UICONTROL Import]**, toont een verwerkingsbericht (bijvoorbeeld, *Verwerking 2 meta-gegevensvormen.. Een ogenblik geduld.* ) tijdens het importeren. Nadat de verwerking is voltooid, wordt de tabel **[!UICONTROL Import metadata forms]** weergegeven met een lijst met metagegevensformulieren die beschikbaar zijn in [!DNL Admin View] . De lijstrij omvat, de naam van de meta-gegevensvorm (onder **[!UICONTROL Name]**), omslagen verbonden aan die vorm (onder **[!UICONTROL Folder Association]**) en een optie aan voorproef ![ ](/help/assets/assets/Preview.svg) de vorm alvorens het in te voeren.
   ![ de pagina van Forms van Meta-gegevens van de Invoer &lbrace;](/help/assets/assets/import-metadata-forms-page.png)

   >[!NOTE]
   > 
   > In de **[!UICONTROL Import Metadata Forms]** -tabel geeft een label **[!UICONTROL Duplicate]** naast een formuliernaam aan dat het formulier al is toegepast op een map in [!DNL Assets View] . Als u dat dubbele formulier importeert, wordt de bestaande versie die op de map is toegepast, overschreven. Als u dit wilt voorkomen, wijzigt u de naam van het formulier voordat u het importeert. Klik op de naam van het formulier om de naam ervan te wijzigen.
1. Klik ![ uitgezochte omslag ](/help/assets/assets/x.svg) naast een omslagnaam (onder [!UICONTROL Folder Association]) om de omslagvereniging met de vorm te verwijderen.
1. Klik ![ uitgezochte omslag ](/help/assets/assets/add-to-folder.svg) om een omslag te selecteren om de overeenkomstige meta-gegevensvorm aan het toe te wijzen.
1. Klik op de rode cirkel om details weer te geven over niet-ondersteunde metagegevenscomponenten of toewijzingen in het formulier die zijn uitgesloten van het importeren.
   ![ de pagina van Forms van Meta-gegevens van de Invoer &lbrace;](/help/assets/assets/unsupported-import-elements.png)
1. Selecteer een of meer formulieren in de tabel en klik op **[!UICONTROL Start Import]** om de metagegevensformulieren en de bijbehorende mappen te importeren in [!DNL Assets View] . De vertoningen van een verwerkingsbericht (bijvoorbeeld, *die 3 meta-gegevensvormen invoeren. Een ogenblik geduld.*). Zodra het importeren is voltooid, wordt met een succesbericht bevestigd dat de formulieren zijn geïmporteerd en dat op de pagina **[!UICONTROL Metadata Forms]** (van [!DNL Assets View] ) zowel recent geïmporteerde als bestaande formulieren worden weergegeven die beschikbaar zijn in [!DNL Assets View] . U kunt het volgende doen op deze pagina:
   * Klik op de kolomkop om de tabel te sorteren op [!UICONTROL Name] , [!UICONTROL Modified] of [!UICONTROL Author] .
   * Selecteer het geïmporteerde formulier en klik op **[!UICONTROL Remove from folder(s)]** en controleer vervolgens de mapnaam in het mappad om te bevestigen dat de map correct is geëxporteerd.

     ![ verifieer de pagina van meta-gegevensvormen ](/help/assets/assets/confirm-ported-folder.png)
   * Selecteer het geïmporteerde formulier en klik op **[!UICONTROL Edit]** om alle ondersteunde configuraties van het metagegevensformulier weer te geven. Zie &lbrace;de Meta-gegevens van de Opstelling Forms [&#128279;](https://experienceleague.adobe.com/en/docs/experience-manager-assets-essentials/help/metadata#metadata-forms) voor meer informatie over de meta-gegevensvormen, hun componenten, en gebieden.

     ![ verifieer de pagina van meta-gegevensvormen ](/help/assets/assets/verify-metadata-forms-page.png)

## De geïmporteerde metagegevensformulieren controleren{#Verify-the-imported-metadata-forms}

Nadat u de metagegevensformulieren van [!DNL Admin View] naar [!DNL Assets View] hebt geïmporteerd, voert u de volgende stappen uit om het importeren te controleren:

1. Navigeer naar een van de bijbehorende mappen van het geïmporteerde metagegevensformulier.
1. Navigeer aan de detailspagina van een [ element ](/help/assets/navigate-assets-view.md#preview-assets) en verifieer dat de gesteunde meta-gegevenscomponenten, componentengebieden, en gebiedswaarden van [!DNL Admin View] worden gesynchroniseerd. Zie [ Meta-gegevens in de Hoofdzaak van Activa ](https://experienceleague.adobe.com/en/docs/experience-manager-assets-essentials/help/metadata) artikel voor meer informatie over meta-gegevenscomponenten, componentengebieden, en de gebiedswaarden.

   >[!NOTE]
   >
   > In [[!DNL Assets View]  detailspagina ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/assets-view/metadata-assets-view#metadata-forms) of [[!DNL Admin View]  eigenschappen pagina ](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/assets/administer/metadata-schemas), worden de veranderingen in de waarden van het meta-gegevensbezit automatisch gesynchroniseerd tussen de twee interfaces. Structuurwijzigingen in het formulier, zoals het toevoegen of verwijderen van velden of andere wijzigingen, worden echter niet gesynchroniseerd.