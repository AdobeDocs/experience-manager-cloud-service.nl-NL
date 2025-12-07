---
title: UI-uitbreidbaarheid inschakelen in  [!DNL AEM Assets View]
description: Leer over het vermogen van de Uitbreidbaarheid UI van  [!DNL AEM Assets View]. [!DNL AEM Assets View]  UI toelaat het toevoegen van componenten van douaneUI om aan specifieke bedrijfsbehoeften te voldoen.
feature: App Builder
role: User, Developer
exl-id: a11f7043-17cf-4331-b76c-d3db099c2411
source-git-commit: f83324be68bdab65e5c76ef336eb7e4a2e318dd1
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 0%

---

# UI-uitbreidbaarheid inschakelen in [!DNL AEM Assets View] {#AEM-Assets-View-UI-Extensibility}

[!DNL AEM Assets View] ondersteunt de uitbreidbaarheid van de gebruikersinterface, zodat u aangepaste UI-componenten aan uw [!DNL Assets View] -gebruikersinterface kunt toevoegen voor specifieke workflows en bedrijfsvereisten waaraan de out-of-the-box-mogelijkheden van [!DNL AEM Assets View] niet voldoen. Deze UI-uitbreidingsmogelijkheid van [!DNL AEM Assets View] verbetert de flexibiliteit, waardoor organisaties de interface voor specifieke workflows en vereisten kunnen aanpassen.\
U kunt uw uitbreidingen aan **Activa** toevoegen, **Omslag** en **het niveau van de Inzameling**. De toegevoegde uitbreidingsvertoningen op een specifiek paneel op de **Activa**, **Inzameling**, of **omslag** **[!UICONTROL Details]** pagina.

>[!IMPORTANT]
>
> * [!DNL AEM Assets View] De uitbreidbaarheid van de gebruikersinterface is beschikbaar in [[!DNL Assets Ultimate]](/help/assets/assets-ultimate-overview.md) .
> * Om toegang tot [!DNL Assets view] uitbreidbaarheid UI te krijgen, [&#x200B; creeer en voorleg het geval van de Steun van de a [!DNL Adobe]  Klant &#x200B;](https://helpx.adobe.com/nl/enterprise/using/support-for-experience-cloud.html).
> * U kunt documentfeedback opgeven door **[!UICONTROL Detailed Feedback options]** uit te vouwen en op **[!UICONTROL Report an issue]** te klikken.

## <a id="1"></a> Toegang tot de weergave Assets {#add-UI-Extensibility-in-AEM-Assets-View}

Voer de stappen in de onderstaande afbeelding uit om het dialoogvenster [!DNL Assets View] te openen:
![&#x200B; toegang-activa-mening-ui &#x200B;](/help/assets/assets/access-assets-view.jpg)

## UI-extensies weergeven in [!DNL Assets View] {#ui-extensibility-panel-assets-view}

Navigeer in [!DNL Assets View] naar de pagina **[!UICONTROL Details]** van een element, map of verzameling. Op de pagina **[!UICONTROL Details]** wordt de toegevoegde UI-extensie weergegeven in een speciaal deelvenster.
![&#x200B; mijn werkruimte &#x200B;](/help/assets/assets/my-workspace-assets-view3.png)

## Vereisten voor het toevoegen van de uitbreidbaarheidscomponent{#assets-view-ui-extensibility}

Voldoe aan de volgende vereisten om de uitbreidbaarheidscomponent aan uw [!DNL Assets View UI] toe te voegen:

* [&#x200B; Toegang tot  [!DNL Assets View]](#1).
* Toegang tot [[!DNL Adobe app builder] &#x200B;](https://developer.adobe.com/app-builder/docs/overview/).
* Recht op de ontwikkelaar van de rol van systeembeheerder binnen de organisatie. Zie [&#x200B; deze documentatie &#x200B;](https://developer.adobe.com/uix/docs/guides/get-access/) voor meer informatie.
* [!DNL Adobe IO command line tool (AIO CLI)] is geïnstalleerd op uw lokale computers. Dit hulpmiddel is essentieel voor het creëren van en het opstellen van uitbreidingsprojecten. Zie [&#x200B; uw Eerste Toepassing van App Builder &#x200B;](https://developer.adobe.com/app-builder/docs/get_started/app_builder_get_started/first-app#local-environment-set-up) (vereist authentificatie voor toegang) voor meer informatie creëren.
* Goed inzicht in [!DNL JavaScript] -, [!DNL Node.js] - en [!DNL React] -technologieën.

## De UI-uitbreidingscomponent toevoegen aan [!DNL Assets View] {#ui-extensibility-in-assets-view}

1. Zie [&#x200B; Begonnen het Krijgen &#x200B;](https://developer.adobe.com/uix/docs/getting-started/) voor essentiële informatie over Uitbreidingen UI en het [!DNL Adobe App Builder] kader. Leer hoe de Uitbreidbaarheid UI integratie van douanelogica en UI binnen [!DNL Adobe Experience Cloud services] toelaat en de architectuur en het werkschema voor het uitvoeren van Uitbreidingen UI begrijpt.
1. Zie [&#x200B; Gidsen &#x200B;](https://developer.adobe.com/uix/docs/guides/) voor algemene informatie betreffende Uitbreidbaarheid UI, met inbegrip van lokale milieu opstelling, lokale voorproef, het publiceren, en beheer.
1. Zie [&#x200B; Gemeenschappelijke concepten in het creëren van uitbreidingen &#x200B;](https://developer.adobe.com/uix/docs/services/aem-assets-view/api/commons/) om de grondbeginselen te begrijpen die worden vereist om een uitbreiding UI voor [!DNL AEM Assets View] te ontwikkelen.
1. Voeg aangepaste zijpanelen aan de [!DNL Assets View] interface toe. De gastheertoepassing ([!DNL Assets View]) beheert deze panelen om interactie UI zoals het schakelen en diep verbinden te behandelen. Extensies gebruiken het extensiepunt `aem/assets/details/1` om aangepaste deelvensters te integreren die eigenschappen opgeven, zoals deelvenster-id, titel en inhoud-URL. Ontwikkelaars registreren aangepaste deelvensters met de methode `getPanels()` en bouwen routes om aangepaste inhoud weer te geven. Voor gedetailleerde implementatie, met inbegrip van API verwijzingen en codevoorbeelden, zie [&#x200B; Mening van Details &#x200B;](https://developer.adobe.com/uix/docs/services/aem-assets-view/api/details-view/).
1. Stel uw lokale omgeving in en maak uw eerste UI-extensie zodat u een eerste ervaring hebt met het ontwikkelen van UI-extensies in [!DNL Assets View] . Zie [&#x200B; geleidelijke de Ontwikkeling van de Uitbreiding van de Uitbreiding van de Mening van AEM Assets &#x200B;](https://developer.adobe.com/uix/docs/services/aem-assets-view/extension-development/) voor meer details.
1. Stel uw toepassing in met behulp van de AIO CLI om de basisextensiestructuur en de vereiste code te genereren. Zie [&#x200B; codegeneratie voor  [!DNL AEM Assets View] &#x200B;](https://developer.adobe.com/uix/docs/services/aem-assets-view/code-generation/) voor gedetailleerde informatie.
1. Test uw extensies lokaal om te controleren of ze werken zoals u had verwacht vóór de implementatie. Voer de extensie uit in een volledig geïsoleerde omgeving of met gedeeltelijke isolatie en sluit de extensie aan op de productie [!DNL AEM Assets View] voor testdoeleinden. Zie [&#x200B; het Oplossen van problemen -  [!DNL AEM Assets View]  rekbaarheid &#x200B;](https://developer.adobe.com/uix/docs/services/aem-assets-view/debug/) voor gedetailleerde informatie.

## Handelingen aanpassen in de weergave Assets {#customize-actions-assets-view}

In de weergave AEM Assets kunt u de volgende acties aanpassen in de weergave Bladeren:

* Pas de acties aan die worden weergegeven wanneer u een of meer elementen in de actiebalk selecteert.

* Pas de acties aan die worden weergegeven wanneer u op Meer opties (...) op de kaart klikt.

* Pas de acties aan die beschikbaar zijn in het menu Koptekst.

Voor meer informatie, zie [&#x200B; Bladeren Mening &#x200B;](https://developer.adobe.com/uix/docs/services/aem-assets-view/api/browse-view/).

## Aangepaste dialoogvensters openen in de Assets-weergave {#open-custom-dialogs-assets-view}

In de Assets-weergave kunt u ook aangepaste dialoogvensters openen met tekst naar keuze. U kunt ook koppelingen naar de tekst toevoegen. Voor meer informatie, zie [&#x200B; Modal API &#x200B;](https://developer.adobe.com/uix/docs/services/aem-assets-view/api/commons/#modal-api).
