---
title: Integreer  [!DNL AEM Assets]  terwijl het ontwerpen van inhoud voor  [!DNL Edge Delivery Services]
description: Leer hoe te om  [!DNL AEM Assets]  met  [!DNL Edge Delivery Services]. This integration enables you to integrate [!DNL AEM Assets]  met  [!DNL Microsoft Word]  te integreren en  [!DNL Google Docs], integrate [!DNL AEM Assets]  met  [!DNL Universal Editor], integrate [!DNL Dynamic Media with OpenAPI capabilities]  met  [!DNL Universal Editor]  en  [!DNL Dynamic Media with OpenAPI capabilities]  met  [!DNL Microsoft Word]  en  [!DNL Google Docs] te integreren.
exl-id: e58db2ce-a55a-49b3-ae8e-709b5ea8d095
source-git-commit: fe3286bf792f387c2209d7b827ba195b50c586b5
workflow-type: tm+mt
source-wordcount: '670'
ht-degree: 0%

---

# [!DNL AEM Assets] integreren tijdens het ontwerpen van inhoud voor [!DNL Edge Delivery Services] {#integrate-aem-assets-while-authoring-for-edge-delivery-services}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b> Dynamische Media Prime en Ultimate </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b> AEM Assets Ultimate </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b> Uitbreidbaarheid UI </b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuw </i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b> laat Dynamische Media Prime en Ultimate </b></a> toe
        </td>
         <td>
            <a href="/help/assets/search-best-practices.md"><b> Beste praktijken van het Onderzoek </b></a>
        </td>
    </tr>
    <tr>
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

![ de activa van AEM integratie met Universele redacteur ](/help/assets/assets/EDS2.png)

[[!DNL Edge Delivery Services] ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/overview) is een composable reeks diensten die voor een hoge graad van flexibiliteit in toestaat hoe u ontwerpt en inhoud op uw website levert. U kunt zowel [ AEM inhoudsbeheer ](/help/sites-cloud/authoring/author-publish.md) gebruiken en [ het auteursrecht van WYSIWYG gebruikend  [!DNL Universal Editor]  evenals op document-Gebaseerde Authoring ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/wysiwyg-authoring/authoring).

U kunt inhoud bewerken in:

* [[!DNL Microsoft Word] of  [!DNL Google Docs]](#integrate-aem-assets-with-document-based-authoring-tools)
* [[!DNL Universal Editor]](#integrate-aem-assets-with-UE-universal-editor)

Nadat u de inhoud hebt bewerkt, kunt u deze publiceren naar Edge Delivery Services.

## [!DNL AEM Assets] integreren met authoringstromen op basis van documenten voor [!DNL Edge Delivery Services] {#integrate-aem-assets-with-document-based-authoring-tools}

Wanneer [!DNL AEM Assets] integreert met uw op documenten gebaseerde ontwerpgereedschappen, zoals [!DNL Microsoft Word] of [!DNL Google Docs] , beschikt het over een elementenkiezer in het ontwerpgereedschap. Gebruik deze elementkiezer om [!DNL AEM Assets] te openen en de goedgekeurde elementen in uw inhoud in te voegen.
Als u reeds een [!DNL Edge Delivery Services] website hebt, zie [[!DNL AEM Assets]  insteekmodule ](https://github.com/adobe-rnd/aem-assets-plugin/blob/main/README.md) documentatie leren hoe te om [!DNL AEM Assets] met uw bestaand [!DNL AEM] project te integreren.
Volg de volgende [ Vereisten ](#integrate-aem-assets-with-microsoft-word-and-google-docs) en [ Integrerend  [!DNL AEM Assets]  met document-Gebaseerde het Authoring milieu ](#integrate-aem-assets-with-microsoft-word-or-google-docs-to-use-aem-assets-with-microsoft-word-or-google-docs) secties als u geen [!DNL Edge Delivery Services] website hebt om uw [!DNL AEM Assets] inclusieve inhoud te publiceren die in document gebaseerde auteurshulpmiddelen wordt geschreven.

### Vereisten{#integrate-aem-assets-with-microsoft-word-and-google-docs}

Voordat u begint, moet u ervoor zorgen dat de ontwerpomgeving op basis van documenten gereed is:

* Integreer [!DNL AEM] met een ontwerpgereedschap dat is gebaseerd op documenten om de ontwerpomgeving in te stellen. Zie [ Begonnen het Krijgen - het Leerprogramma van de Ontwikkelaar ](https://www.aem.live/developer/tutorial) leren hoe te opstelling het auteursmilieu.

### [!DNL AEM Assets] integreren met een op documenten gebaseerde ontwerpomgeving{#integrate-aem-assets-with-microsoft-word-or-google-docs-to-use-aem-assets-with-microsoft-word-or-google-docs}

Configureer de [!DNL AEM Assets] Sidekick-insteekmodule om elementen te gebruiken tijdens het ontwerpen van inhoud in [!DNL Microsoft Word] of [!DNL Google Docs] .

* Zie [[!DNL Adobe Experience Manager Assets Sidekick Plugin] ](https://www.aem.live/docs/aem-assets-sidekick-plugin#using-experience-manager-assets-for-website-authors) om tot AEM Assets in Microsoft Word of Google Docs toegang te hebben en te gebruiken.
* Zie [ Vormend  [!DNL Adobe Experience Manager Assets Sidekick Plugin] ](https://www.aem.live/developer/configuring-aem-assets-sidekick-plugin) voor configuratiedetails.
  ![ gebruik dynamische media met openAPI mogelijkheden in ms woord en google docs ](/help/assets/assets/my-assets-sidebar.png)

## Elementen leveren met [!DNL Dynamic Media with OpenAPI capabilities] {#integrate-Dynamic-Media-with-OpenAPI-capabilities-with-Microsoft-Word-Google-Docs-and-universal-editor}

U kunt ook elementen gebruiken die met [!DNL Dynamic Media with OpenAPI capabilities] zijn geleverd. Het biedt veel voordelen, zoals:

* Alleen toegang tot door een merk goedgekeurde elementen (afbeeldingen, video&#39;s, PDF&#39;s en andere elementtypen) vanuit [!DNL AEM Assets Cloud Services] .
* Governance (verwijzingen versus kopieën van het element), wat helpt met automatische propagatie van gebeurtenissen in de levenscyclus van elementen zoals vervaldatum, verwijdering en updates.
* Dynamische afbeeldingsuitvoeringen en Slim uitsnijden.
* Rijke media optimalisering en levering, zoals adaptieve video die uit-van-de-doos, en originele levering van activa voor PDFs stroomt.
* Het activa-vlakke beeld rapporteert ([ beperkte beschikbaarheid ](/help/assets/manage-reports-assets-view.md#dynamic-media-delivery-reports)).

Voor meer details over de mogelijkheden, zie [[!DNL Dynamic Media with OpenAPI capabilities] ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/dynamic-media-open-apis/dynamic-media-open-apis-overview) documentatie.

### Vereisten {#prerequisites-for-dm-with-openapi-capabilities-to-use-aem-assets}

Als u een elementverwijzing wilt gebruiken, moet u beschikken over:

* Machtigingen tot een Assets Cloud Service-omgeving waarin [!DNL Dynamic Media with Open API capabilities] is ingeschakeld.
* Een [!DNL Dynamic Media] -licentie.
* De [!DNL AEM Assets sidekick plugin] wordt ingeschakeld met de kopieerverwijzing voor afbeeldingselementen ingeschakeld. Voor meer details, zie [ deze documentatie ](https://www.aem.live/developer/configuring-aem-assets-sidekick-plugin#copymode) voor Op document-Gebaseerd Authoring en zie [ deze documentatie ](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/#extension-overview) voor Universele Redacteur gebaseerd auteursrecht.
* Assets die zijn goedgekeurd. Goedgekeurde middelen zijn `dam:status=Approved` via de Assets Cloud Services-back-end- of UI-acties.

### Elementen gebruiken die zijn geleverd met [!DNL Dynamic Media with OpenAPI capabilities]{#how-to-use-Dynamic-Media-with-OpenAPI-assets}

Selecteer de volgende koppelingen om te leren hoe u [!DNL Dynamic Media with OpenAPI capabilities] kunt gebruiken voor het leveren van afbeeldingen, video&#39;s en andere typen elementen in uw inhoud:

* [ voeg beelden aan uw inhoud ](https://www.aem.live/docs/aem-assets-sidekick-plugin#using-image-references-when-authoring-content) toe
* [ voeg video&#39;s aan uw inhoud toe ](https://www.aem.live/docs/aem-assets-sidekick-plugin#using-video-references-when-authoring-content)
* [ voeg niet-beeld en videoactiva zoals PDF toe, ip dossiers en meer aan uw inhoud ](https://www.aem.live/docs/aem-assets-sidekick-plugin#using-asset-references-for-pdf-zip-etc-when-authoring-content)

Bekijk deze video voor informatie over hoe u elementen in uw inhoud kunt leveren met gebruik van Dynamic Media met OpenAPI-mogelijkheden.

>[!VIDEO](https://video.tv.adobe.com/v/3441155)

## Voorbeeld [!DNL Edge Delivery Services] -site{#example-of-an-Edge-Delivery-Services-site}

Zie [ WKND Reizen ](http://bit.ly/3DExLnf), een plaats die gebruikend op document-Gebaseerde Authoring mogelijkheden van [!DNL Edge Delivery Services] wordt gebouwd. De inhoud van de plaats wordt authored in [ Google Docs ](https://drive.google.com/drive/folders/1HCCHRWp4HJIXW_cUv5cRDQ5DzzqiZsXT) en [!DNL Dynamic Media with OpenAPI capabilities] wordt gebruikt om activa in de inhoud te leveren. Na het ontwerpen wordt de inhoud rechtstreeks vanuit het document gepubliceerd. Onderzoek deze [ bewaarplaats van de Git ](https://github.com/hlxsites/franklin-assets-selector/tree/aem-dynamicmedia-demo/blocks) om over alle essentiële dossiers, omslagen, configuraties, het stileren van de website en functionaliteitcodes te weten die worden gebruikt om de op document-Gebaseerde Authoring opstelling voor deze [!DNL Edge Delivery Services (EDS)] plaats tot stand te brengen.

## [!DNL AEM Assets] integreren met [!DNL Universal Editor] gebaseerde ontwerpflows voor [!DNL Edge Delivery Services] {#integrate-aem-assets-with-UE-universal-editor}

Stel de [!DNL Universal Editor] in die u wilt integreren met [!DNL AEM Assets] . Dankzij deze integratie kunt u [!DNL Dynamic Media with OpenAPI capabilities] gebruiken om elementen te leveren.

* Zie [ Configuratie in  [!DNL Edge Delivery]  Plaats ](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/#configuration-in-edge-delivery-site) leren hoe te om een functie van de plukker van douaneactiva in [!DNL Universal Editor] toe te voegen. Met de aangepaste elementkiezer kunt u elementen rechtstreeks in uw [!DNL Universal Editor] -inhoud invoegen.
* Zie [ Overzicht van de Uitbreiding ](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/#extension-overview) leren hoe te om tot [!DNL AEM Assets] toegang te hebben en de activa op te nemen terwijl het ontwerpen in [!DNL Universal Editor].
