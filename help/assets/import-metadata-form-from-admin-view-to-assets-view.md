---
title: De meta-gegevensvormen van de invoer van  [!DNL Admin View]  aan  [!DNL Assets View]
description: Dit artikel beschrijft hoe te om de meta-gegevensvorm van  [!DNL Admin View]  in te voeren  [!DNL Assets View]
contentOwner: AG
feature: Metadata
role: User, Admin
exl-id: 5fb4fe97-486a-4a91-af60-a7182efcc2f9
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 0%

---

# Metagegevensformulieren importeren van [!DNL Admin View] naar [!DNL Assets View] {#import-metadata-forms-from-admin-view-to-assets-view}

Met [!DNL Adobe Experience Manager Assets] kunt u metagegevensformulieren en de bijbehorende mapkoppelingen importeren van [!DNL Admin View] naar [!DNL Assets View] .

## Voordat u begint{#prerequisites-for-importing-metadata-forms-to-assets-view}

Controleer of u beheerdersrechten hebt om de metagegevensformulieren en de bijbehorende mapkoppelingen te importeren van [!DNL Admin View] naar [!DNL Assets View] .

## Metagegevensformulieren importeren naar [!DNL Assets View]{#import-metadata-forms-to-assets-view}

Als beheerder voert u de volgende stappen uit om de metagegevensformulieren die beschikbaar zijn in [!DNL Admin View] t/m [!DNL Assets View] te importeren:

1. Navigeer naar de [!DNL Assets View] startpagina en klik **[!UICONTROL &#x200B; Metadata Forms]** onder **[!UICONTROL Settings]** om de pagina **[!UICONTROL Metadata Forms]** weer te geven met de lijst met metagegevensformulieren die beschikbaar is in [!DNL Assets View] .

   ![&#x200B; pagina van meta-gegevensvormen &#x200B;](/help/assets/assets/metadata-forms-page.png)

1. Selecteer **[!UICONTROL Import]**, toont een verwerkingsbericht (bijvoorbeeld, *Verwerking 2 meta-gegevensvormen.. Een ogenblik geduld.* ) tijdens het importeren. Nadat de verwerking is voltooid, wordt de tabel **[!UICONTROL Import metadata forms]** weergegeven met een lijst met metagegevensformulieren die beschikbaar zijn in [!DNL Admin View] . De lijstrij omvat, de naam van de meta-gegevensvorm (onder **[!UICONTROL Name]**), omslagen verbonden aan die vorm (onder **[!UICONTROL Folder Association]**) en een optie aan voorproef ![&#x200B; &#x200B;](/help/assets/assets/Preview.svg) de vorm alvorens het in te voeren.

   ![&#x200B; de pagina van Forms van Meta-gegevens van de Invoer &lbrace;](/help/assets/assets/import-metadata-forms-page.png)

   >[!NOTE]
   > 
   > In de **[!UICONTROL Import Metadata Forms]** -tabel geeft een label **[!UICONTROL Duplicate]** naast een formuliernaam aan dat het formulier al is toegepast op een map in [!DNL Assets View] . Als u dat dubbele formulier importeert, wordt de bestaande versie die op de map is toegepast, overschreven. Als u dit wilt voorkomen, wijzigt u de naam van het formulier voordat u het importeert. Klik op de naam van het formulier om de naam ervan te wijzigen.

1. Klik ![&#x200B; uitgezochte omslag &#x200B;](/help/assets/assets/x.svg) naast een omslagnaam (onder [!UICONTROL Folder Association]) om de omslagvereniging met de vorm te verwijderen.
1. Klik ![&#x200B; uitgezochte omslag &#x200B;](/help/assets/assets/add-to-folder.svg) om een omslag te selecteren om de overeenkomstige meta-gegevensvorm aan het toe te wijzen.
1. Klik op de rode cirkel om details weer te geven over niet-ondersteunde metagegevenscomponenten of toewijzingen in het formulier die zijn uitgesloten van het importeren.

   ![&#x200B; de pagina van Forms van Meta-gegevens van de Invoer &lbrace;](/help/assets/assets/unsupported-import-elements.png)

1. Selecteer een of meer formulieren in de tabel en klik op **[!UICONTROL Start Import]** om de metagegevensformulieren en de bijbehorende mappen te importeren in [!DNL Assets View] . De vertoningen van een verwerkingsbericht (bijvoorbeeld, *die 3 meta-gegevensvormen invoeren. Een ogenblik geduld.*). Zodra het importeren is voltooid, wordt met een succesbericht bevestigd dat de formulieren zijn geïmporteerd en dat op de pagina **[!UICONTROL Metadata Forms]** (van [!DNL Assets View] ) zowel recent geïmporteerde als bestaande formulieren worden weergegeven die beschikbaar zijn in [!DNL Assets View] . U kunt het volgende doen op deze pagina:

   * Klik op de kolomkop om de tabel te sorteren op [!UICONTROL Name] , [!UICONTROL Modified] of [!UICONTROL Author] .
   * Selecteer het geïmporteerde formulier en klik op **[!UICONTROL Remove from folder(s)]** en controleer vervolgens de mapnaam in het mappad om te bevestigen dat de map correct is geëxporteerd.

     ![&#x200B; verifieer de pagina van meta-gegevensvormen &#x200B;](/help/assets/assets/confirm-ported-folder.png)
   * Selecteer het geïmporteerde formulier en klik op **[!UICONTROL Edit]** om alle ondersteunde configuraties van het metagegevensformulier weer te geven. Zie &lbrace;de Meta-gegevens van de Opstelling Forms [&#128279;](https://experienceleague.adobe.com/nl/docs/experience-manager-assets-essentials/help/metadata#metadata-forms) voor meer informatie over de meta-gegevensvormen, hun componenten, en gebieden.

   ![&#x200B; verifieer de pagina van meta-gegevensvormen &#x200B;](/help/assets/assets/verify-metadata-forms-page.png)

## De geïmporteerde metagegevensformulieren controleren{#Verify-the-imported-metadata-forms}

Nadat u de metagegevensformulieren van [!DNL Admin View] naar [!DNL Assets View] hebt geïmporteerd, voert u de volgende stappen uit om het importeren te controleren:

1. Navigeer naar een van de bijbehorende mappen van het geïmporteerde metagegevensformulier.
1. Navigeer aan de detailspagina van een [&#x200B; element &#x200B;](/help/assets/navigate-assets-view.md#preview-assets) en verifieer dat de gesteunde meta-gegevenscomponenten, componentengebieden, en gebiedswaarden van [!DNL Admin View] worden gesynchroniseerd. Zie [&#x200B; Meta-gegevens in de Hoofdzaak van Activa &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-assets-essentials/help/metadata) artikel voor meer informatie over meta-gegevenscomponenten, componentengebieden, en de gebiedswaarden.

   >[!NOTE]
   >
   > In [[!DNL Assets View]  detailspagina &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/assets/assets-view/metadata-assets-view#metadata-forms) of [[!DNL Admin View]  eigenschappen pagina &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-65/content/assets/administer/metadata-schemas), worden de veranderingen in de waarden van het meta-gegevensbezit automatisch gesynchroniseerd tussen de twee interfaces. Structuurwijzigingen in het formulier, zoals het toevoegen of verwijderen van velden of andere wijzigingen, worden echter niet gesynchroniseerd.
