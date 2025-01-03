---
title: AEM Assets integreren tijdens het ontwerpen van inhoud voor Edge Delivery Services
description: Leer hoe u de AEM Assets met Edge Delivery Services kunt integreren. Dankzij deze integratie kunt u AEM Assets integreren met Microsoft Word- en Google Docs, AEM Assets integreren met Universal Editor, Dynamic Media integreren met OpenAPI-mogelijkheden met Universal Editor en Dynamic Media integreren met OpenAPI-mogelijkheden met Microsoft Word en Google Docs.
exl-id: e58db2ce-a55a-49b3-ae8e-709b5ea8d095
source-git-commit: ed9d559e09746023577c27dafbd64a8c46acc5da
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 0%

---

# AEM Assets integreren tijdens het ontwerpen van inhoud voor Edge Delivery Services {#integrate-aem-assets-while-authoring-for-edge-delivery-services}

![ EDS2 ](/help/assets/assets/EDS2.png)

[ Edge Delivery Services ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/overview) is een composable reeks diensten die voor een hoge graad van flexibiliteit in toestaat hoe u auteur en inhoud op uw website levert. U kunt zowel [ AEM inhoudsbeheer ](/help/sites-cloud/authoring/author-publish.md) gebruiken en [ het auteursrecht van WYSIWYG gebruikend de Universele Redacteur evenals op document-Gebaseerde Authoring ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/wysiwyg-authoring/authoring).

U kunt inhoud bewerken in:

* [Microsoft Word- of Google Docs](#integrate-aem-assets-with-document-based-authoring-tools)

* [Universele editor](#integrate-aem-assets-with-universal-editor)

Nadat u de inhoud hebt bewerkt, kunt u deze publiceren naar Edge Delivery Services.

## AEM Assets integreren met authoringstromen op basis van documenten voor Edge Delivery Services {#integrate-aem-assets-with-document-based-authoring-tools}

AEM Assets-integratie met de op documenten gebaseerde ontwerpgereedschappen, zoals Microsoft Word of Google Docs, biedt rechtstreeks een middelenkiezer in uw editor. Gebruik deze middelenkiezer om toegang te krijgen tot de AEM Assets en voeg goedgekeurde elementen in uw document in.
Als u reeds een website van Edge Delivery Services hebt, zie [ insteekmodule van AEM Assets ](https://github.com/adobe-rnd/aem-assets-plugin/blob/main/README.md) om AEM Assets met uw bestaand AEM project te integreren. Als u geen website van Edge Delivery Services ziet, [ Vereisten ](#integrate-aem-assets-with-microsoft-word-and-google-docs) en [ Integrerend AEM Assets met document-Gebaseerde het auteursmilieu ](#integrate-aem-assets-with-microsoft-word-or-google-docs-to-use-aem-assets-with-microsoft-word-or-google-docs) hieronder secties.

### Vereisten{#integrate-aem-assets-with-microsoft-word-and-google-docs}

Voordat u begint, moet u ervoor zorgen dat de ontwerpomgeving op basis van documenten gereed is:

* Integreer AEM met een ontwerpgereedschap op basis van documenten om de ontwerpomgeving in te stellen. Zie [ Begonnen het Worden - het Leerprogramma van de Ontwikkelaar ](https://www.aem.live/developer/tutorial) aan opstelling het auteursmilieu.

### AEM Assets integreren met een op documenten gebaseerde ontwerpomgeving{#integrate-aem-assets-with-microsoft-word-or-google-docs-to-use-aem-assets-with-microsoft-word-or-google-docs}

Configureer de AEM Assets Sidekick-insteekmodule om elementen te gebruiken tijdens het ontwerpen van inhoud in Microsoft Word of Google Docs.

* Zie [ Insteekmodule van de Sidekick van Adobe Experience Manager Assets ](https://www.aem.live/docs/aem-assets-sidekick-plugin#using-experience-manager-assets-for-website-authors) leren hoe te om tot AEM Assets in Microsoft Word of Google toegang te hebben en te gebruiken Docs.
* Zie [ Vormend de Insteekmodule van de Sidekick van Adobe Experience Manager Assets ](https://www.aem.live/developer/configuring-aem-assets-sidekick-plugin) voor configuratiedetails.
  ![ my-assets-sidebar ](/help/assets/assets/my-assets-sidebar.png)

## Middelen leveren met Dynamic Media met OpenAPI-mogelijkheden {#integrate-Dynamic-Media-with-OpenAPI-capabilities-with-Microsoft-Word-Google-Docs-and-universal-editor}

U kunt ook elementen gebruiken die via DM met OpenAPI-mogelijkheden worden geleverd. Het biedt veel voordelen, zoals:

* Alleen toegang tot door een merk goedgekeurde elementen (afbeeldingen, video&#39;s, PDF en andere typen elementen) van AEM Assets-Cloud Servicen.
* Governance (verwijzingen versus kopieën van het element), wat helpt met automatische propagatie van gebeurtenissen in de levenscyclus van elementen zoals vervaldatum, verwijdering en updates.
* Dynamische afbeeldingsuitvoeringen en Slim uitsnijden.
* Rijke media optimalisering en levering, zoals adaptieve video die uit-de-doos, en originele levering van activa voor PDF stroomt.
* Het activa-vlakke beeld rapporteert ([ beperkte beschikbaarheid ](/help/assets/manage-reports-assets-view.md#dynamic-media-delivery-reports)).

Voor meer details op de mogelijkheden, zie [ Dynamic Media met mogelijkheden OpenAPI ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/dynamic-media-open-apis/dynamic-media-open-apis-overview) documentatie.

### Vereisten {#prerequisites-for-dm-with-openapi-capabilities-to-use-aem-assets}

Als u een elementverwijzing wilt gebruiken, moet u beschikken over:

* Toestemming voor een Assets Cloud Service-omgeving waarin Dynamic Media met Open API-mogelijkheden is ingeschakeld.
* Een Dynamic Media-licentie.
* De AEM Assets-insteekmodule sidekick is ingeschakeld en de verwijzing naar de kopie voor afbeeldingselementen is ingeschakeld. Voor meer details, zie [ dit ](https://www.aem.live/developer/configuring-aem-assets-sidekick-plugin#copymode) voor Op document-Gebaseerd Authoring en zie [ dit ](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/#extension-overview) voor Universele Redacteur gebaseerd auteursrecht.
* Assets die zijn goedgekeurd. Goedgekeurde middelen hebben `dam:status=Approved` via de Assets Cloud Servicen back-end- of UI-acties.

### Elementen gebruiken die zijn geleverd met Dynamic Media met OpenAPI-mogelijkheden{#how-to-use-Dynamic-Media-with-OpenAPI-assets}

Ga als volgt te werk als u elementen die via Dynamic Media met OpenAPI-mogelijkheden worden geleverd, wilt gebruiken tijdens het ontwerpen van inhoud:

* [ Gebruikend beeldverwijzingen ](https://www.aem.live/docs/aem-assets-sidekick-plugin#using-image-references-when-authoring-content)
* [ Gebruikend videoverwijzingen ](https://www.aem.live/docs/aem-assets-sidekick-plugin#using-video-references-when-authoring-content)
* [ Gebruikend activa verwijzingen voor niet-beeld en videoactiva zoals PDF, dossiers van het ZIP en meer ](https://www.aem.live/docs/aem-assets-sidekick-plugin#using-asset-references-for-pdf-zip-etc-when-authoring-content)

Bekijk deze video voor informatie over hoe u middelen kunt leveren met Dynamic Media met OpenAPI-mogelijkheden.

>[!VIDEO](https://video.tv.adobe.com/v/3441155)

## Voorbeeldsite voor Edge Delivery Services{#example-of-an-Edge-Delivery-Services-site}

Zie [ WKND Reizen ](https://aem-dynamicmedia-demo--dm--hlxsites.aem.live/travel-hospitality/wknd-trvl-home). Deze site wordt gemaakt met behulp van de op documenten gebaseerde ontwerpmogelijkheden van Edge Delivery Services. De inhoud van de plaats wordt authored in [ Dokken van Google ](https://drive.google.com/drive/folders/1HCCHRWp4HJIXW_cUv5cRDQ5DzzqiZsXT), gebruikend Dynamic Media met mogelijkheden OpenAPI voor activalevering. Nadat de inhoud is gemaakt, wordt deze rechtstreeks vanuit het document gepubliceerd. Voor deze op document-Gebaseerde Opstelling van de Authoring, worden alle essentiële dossiers, omslagen, configuraties, het stileren van de website en functionaliteit codes opgeslagen in deze [ bewaarplaats van de Git ](https://github.com/hlxsites/franklin-assets-selector/tree/aem-dynamicmedia-demo/blocks).

## AEM Assets integreren met op Universal Editor gebaseerde ontwerpflows voor Edge Delivery Services {#integrate-aem-assets-with-universal-editor}

Stel de Universal Editor in om deze te integreren met AEM Assets. Dankzij deze integratie kunt u Dynamic Media met OpenAPI-mogelijkheden gebruiken om middelen te leveren.

* Zie [ Configuratie in de Plaats van Edge Delivery ](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/#configuration-in-edge-delivery-site) om een functie van de plukker van douanemiddelen in Universele Redacteur toe te voegen. Met de aangepaste elementkiezer kunt u elementen rechtstreeks in uw Universal Editor-inhoud invoegen.
* Zie [ Overzicht van de Uitbreiding ](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/#extension-overview) leren hoe te om tot AEM Assets toegang te hebben en de activa op te nemen terwijl het ontwerpen in Universele Redacteur.
