---
title: AEM Assets integreren tijdens het ontwerpen van inhoud voor Edge Delivery Services
description: Leer hoe u de AEM Assets kunt integreren met Edge Delivery Services. Dankzij deze integratie kunt u AEM Assets integreren met Microsoft Word en Google Docs, AEM Assets integreren met Universal Editor, Dynamic Media integreren met OpenAPI-mogelijkheden met Universal Editor en Dynamic Media integreren met OpenAPI-mogelijkheden met Microsoft Word en Google Docs.
exl-id: e58db2ce-a55a-49b3-ae8e-709b5ea8d095
source-git-commit: e4a71d1a513bebed67b9571a483871dc16c36daa
workflow-type: tm+mt
source-wordcount: '820'
ht-degree: 0%

---

# AEM Assets integreren tijdens het ontwerpen van inhoud voor Edge Delivery Services {#integrate-aem-assets-while-authoring-for-edge-delivery-services}

![ de activa van AEM met UE ](/help/assets/assets/EDS2.png)

[ Edge Delivery Services ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/overview) is een composable reeks diensten die voor een hoge graad van flexibiliteit in toestaat hoe u auteur en inhoud op uw website levert. U kunt zowel [ AEM inhoudsbeheer ](/help/sites-cloud/authoring/author-publish.md) gebruiken en [ het auteursrecht van WYSIWYG gebruikend de Universele Redacteur evenals op document-Gebaseerde Authoring ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/wysiwyg-authoring/authoring).

U kunt inhoud bewerken in:

* [Microsoft Word of Google Docs](#integrate-aem-assets-with-document-based-authoring-tools)
* [Universele editor](#integrate-aem-assets-with-UE-universal-editor)

Nadat u de inhoud hebt bewerkt, kunt u deze publiceren naar Edge Delivery Services.

## AEM Assets integreren met authoringstromen op basis van documenten voor Edge Delivery Services {#integrate-aem-assets-with-document-based-authoring-tools}

Als AEM Assets is geïntegreerd met de ontwerpgereedschappen voor documenten, zoals Microsoft Word of Google Docs, is het programma voorzien van een kiezer voor middelen in uw editor. Gebruik deze middelenkiezer om toegang te krijgen tot de AEM Assets en voeg goedgekeurde elementen in uw document in.
Als u reeds een website van Edge Delivery Services hebt, zie [ insteekmodule van AEM Assets ](https://github.com/adobe-rnd/aem-assets-plugin/blob/main/README.md) document leren hoe te om AEM Assets met uw bestaand project van AEM te integreren.
Volg de volgende [ Vereisten ](#integrate-aem-assets-with-microsoft-word-and-google-docs) en [ Integrating AEM Assets met document-Gebaseerde het Authoring milieu ](#integrate-aem-assets-with-microsoft-word-or-google-docs-to-use-aem-assets-with-microsoft-word-or-google-docs) secties als u geen website van Edge Delivery Services hebt om uw inclusieve inhoud te publiceren AEM Assets die in document gebaseerde auteurshulpmiddelen wordt geschreven.

### Vereisten{#integrate-aem-assets-with-microsoft-word-and-google-docs}

Voordat u begint, moet u ervoor zorgen dat de ontwerpomgeving op basis van documenten gereed is:

* Integreer AEM met een ontwerpgereedschap op basis van documenten om de ontwerpomgeving in te stellen. Zie [ Begonnen het Krijgen - het Leerprogramma van de Ontwikkelaar ](https://www.aem.live/developer/tutorial) leren hoe te opstelling het auteursmilieu.

### AEM Assets integreren met een op documenten gebaseerde ontwerpomgeving{#integrate-aem-assets-with-microsoft-word-or-google-docs-to-use-aem-assets-with-microsoft-word-or-google-docs}

Configureer de AEM Assets Sidekick-insteekmodule voor het gebruik van middelen tijdens het ontwerpen van inhoud in Microsoft Word of Google Docs.

* Zie {de Insteekmodule van Sidekick van 0} Adobe Experience Manager Assets ](https://www.aem.live/docs/aem-assets-sidekick-plugin#using-experience-manager-assets-for-website-authors) leren om tot AEM Assets in Microsoft Word of Google Docs toegang te hebben en te gebruiken.[
* Zie [ Vormend de Insteekmodule van Adobe Experience Manager Assets Sidekick ](https://www.aem.live/developer/configuring-aem-assets-sidekick-plugin) voor configuratiedetails.
  ![ gebruik dynamische media met openAPI mogelijkheden in ms woord en google docs ](/help/assets/assets/my-assets-sidebar.png)

## Elementen leveren met Dynamic Media met OpenAPI-mogelijkheden {#integrate-Dynamic-Media-with-OpenAPI-capabilities-with-Microsoft-Word-Google-Docs-and-universal-editor}

U kunt ook elementen gebruiken die via DM met OpenAPI-mogelijkheden worden geleverd. Het biedt veel voordelen, zoals:

* Alleen toegang tot door een merk goedgekeurde middelen (afbeeldingen, video&#39;s, PDF&#39;s en andere typen middelen) van AEM Assets Cloud Services.
* Governance (verwijzingen versus kopieën van het element), wat helpt met automatische propagatie van gebeurtenissen in de levenscyclus van elementen zoals vervaldatum, verwijdering en updates.
* Dynamische afbeeldingsuitvoeringen en Slim uitsnijden.
* Rijke media optimalisering en levering, zoals adaptieve video die uit-van-de-doos, en originele levering van activa voor PDFs stroomt.
* Het activa-vlakke beeld rapporteert ([ beperkte beschikbaarheid ](/help/assets/manage-reports-assets-view.md#dynamic-media-delivery-reports)).

Voor meer details op de mogelijkheden, zie [ Dynamische Media met mogelijkheden OpenAPI ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/dynamic-media-open-apis/dynamic-media-open-apis-overview) documentatie.

### Vereisten {#prerequisites-for-dm-with-openapi-capabilities-to-use-aem-assets}

Als u een elementverwijzing wilt gebruiken, moet u beschikken over:

* Toestemming voor een Assets Cloud Service-omgeving waarin Dynamic Media met Open API-mogelijkheden is ingeschakeld.
* Een Dynamic Media-licentie.
* De AEM Assets-insteekmodule sidekick is ingeschakeld en de verwijzing naar de kopie voor afbeeldingselementen is ingeschakeld. Voor meer details, zie [ dit ](https://www.aem.live/developer/configuring-aem-assets-sidekick-plugin#copymode) voor Op document-Gebaseerd Authoring en zie [ dit ](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/#extension-overview) voor Universele Redacteur gebaseerd auteursrecht.
* Assets die zijn goedgekeurd. Goedgekeurde middelen zijn `dam:status=Approved` via de Assets Cloud Services-back-end- of UI-acties.

### Elementen gebruiken die worden geleverd met Dynamic Media met OpenAPI-mogelijkheden{#how-to-use-Dynamic-Media-with-OpenAPI-assets}

Selecteer de volgende koppelingen voor informatie over het gebruik van Dynamic Media met OpenAPI-mogelijkheden om afbeeldingen, video&#39;s en andere typen elementen in uw inhoud te leveren:

* [ voeg beelden aan uw inhoud ](https://www.aem.live/docs/aem-assets-sidekick-plugin#using-image-references-when-authoring-content) toe
* [ voeg video&#39;s aan uw inhoud toe ](https://www.aem.live/docs/aem-assets-sidekick-plugin#using-video-references-when-authoring-content)
* [ voeg niet-beeld en videoactiva zoals PDF toe, ip dossiers en meer aan uw inhoud ](https://www.aem.live/docs/aem-assets-sidekick-plugin#using-asset-references-for-pdf-zip-etc-when-authoring-content)

Bekijk deze video voor informatie over hoe u elementen in uw inhoud kunt leveren met gebruik van Dynamic Media met OpenAPI-mogelijkheden.

>[!VIDEO](https://video.tv.adobe.com/v/3441155)

## Voorbeeld van Edge Delivery Services-site{#example-of-an-Edge-Delivery-Services-site}

Zie [ WKND Reizen ](http://bit.ly/3DExLnf), een plaats die gebruikend op document-Gebaseerde Authoring mogelijkheden van Edge Delivery Services wordt gebouwd. De inhoud van de plaats wordt authored in [ Google Docs ](https://drive.google.com/drive/folders/1HCCHRWp4HJIXW_cUv5cRDQ5DzzqiZsXT) en de Dynamische Media met mogelijkheden OpenAPI wordt gebruikt om activa in de inhoud te leveren. Na het ontwerpen wordt de inhoud rechtstreeks vanuit het document gepubliceerd. Onderzoek deze [ bewaarplaats van de Git ](https://github.com/hlxsites/franklin-assets-selector/tree/aem-dynamicmedia-demo/blocks) om over alle essentiële dossiers, omslagen, configuraties, het stileren van de website en functionaliteitcodes te weten te komen die worden gebruikt om de op document-Gebaseerde Authoring opstelling voor deze plaats van Edge Delivery Services (EDS) tot stand te brengen.

## AEM Assets integreren met op Universal Editor gebaseerde ontwerpflows voor Edge Delivery Services {#integrate-aem-assets-with-UE-universal-editor}

Stel de Universal Editor in om deze te integreren met AEM Assets. Dankzij deze integratie kunt u Dynamic Media met OpenAPI-mogelijkheden gebruiken om middelen te leveren.

* Zie [ Configuratie in de Plaats van Edge Delivery ](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/#configuration-in-edge-delivery-site) leren hoe te om een functie van de plukker van de douaneactiva in Universele Redacteur toe te voegen. Met de aangepaste elementkiezer kunt u elementen rechtstreeks in uw Universal Editor-inhoud invoegen.
* Zie [ Overzicht van de Uitbreiding ](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/#extension-overview) leren hoe te om tot AEM Assets toegang te hebben en de activa op te nemen terwijl het ontwerpen in Universele Redacteur.
