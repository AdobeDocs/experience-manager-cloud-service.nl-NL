---
title: Beheer uw PDF documenten in  [!DNL Adobe Experience Manager].
description: Beheer de documenten van PDF in  [!DNL Adobe Experience Manager]  als a  [!DNL Cloud Service].
feature: Asset Management
role: User, Admin
exl-id: 29660869-6902-4093-845b-cd629be59d4d
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '856'
ht-degree: 0%

---

# PDF-documenten beheren in Experience Manager Assets as a Cloud Service {#add-assets-to-experience-manager}

| [ Beste praktijken van het Onderzoek ](/help/assets/search-best-practices.md) | [ Beste praktijken van Meta-gegevens ](/help/assets/metadata-best-practices.md) | [ Content Hub ](/help/assets/product-overview.md) | [ Dynamic Media met mogelijkheden OpenAPI ](/help/assets/dynamic-media-open-apis-overview.md) | [ de ontwikkelaarsdocumentatie van AEM Assets ](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

Experience Manager Assets kan naadloos worden geïntegreerd met de Document Cloud PDF Viewer, waarmee u meerdere pagina&#39;s van een PDF-document kunt voorvertonen. Daarnaast kunt u ook geavanceerde viewerfuncties voor PDF gebruiken, zoals annotaties, zoektekst, navigatie in het PDF-document met bladwijzers en miniaturen, enzovoort, onder hetzelfde dak. Met Experience Manager Assets kunt u ook documenten in andere ondersteunde indelingen uploaden en deze voorvertonen in een PDF-indeling.

De PDF-viewer van Document Cloud profiteert AEM Assets op de volgende manieren:
* [Ondersteuning voor PDF Document Cloud Viewer-componenten](#pdf-doc-cloud)
* [Ondersteuning voor Voorvertoning van meerdere pagina&#39;s en annotaties voor PDF-element](#multi-page)
* [Ondersteuning voor Voorvertoning van meerdere pagina&#39;s voor documenten in andere indelingen](#multi-format)

> Tip
> Als u niet veelvoudige paginavoorproef van een eerder geupload document van de PDF kunt krijgen dan de PDF selecteren en **![](/help/assets/assets/Reprocess.svg) opnieuw verwerken Assets** klikken.
>

## Ondersteuning voor PDF Document Cloud Viewer-componenten {#pdf-doc-cloud}

De native PDF Doc Cloud-viewer heeft de volgende componenten in AEM Assets:

* **de kijker die van de PDF paginaminiaturen** gebruikt de mening van de Duimnagel is een kleine voorproef van de pagina&#39;s van een document van de PDF. Met behulp van miniaturen kunt u rechtstreeks naar de gewenste pagina gaan. U kunt tot duimnagels van het geselecteerde document van de PDF door ![ duimnagel ](/help/assets/assets/thumbnail.svg) op de linkerruit toegang hebben.

* **de kijker van de PDF gebruikend referenties** Bladwijzer is een directe verbinding die u aan de inhoud in het document navigeert. U kunt tot referenties van het geselecteerde document van de PDF door ![ referentie ](/help/assets/assets/bookmark.svg) op de linkerruit toegang hebben.

* **Onderzoek in PDF** u onderzoek ![ ](/help/assets/assets/Search.svg) kunt gebruiken om omhoog de tekst in het document van de PDF te kijken.

* **pagina omhoog/pagina onderaan** pagina van het Gebruik omhoog ![ pagina ](/help/assets/assets/ArrowUp.svg) of pagina onderaan ![ pagina neer ](/help/assets/assets/ArrowDown.svg) om door het document te scrollen.

* **Uitzoomen/Gezoem binnen** Uitzoomen van het Gebruik ![ Uitzoomen ](/help/assets/assets/ZoomOut.svg) of Gezoem binnen ![ Gezoem binnen ](/help/assets/assets/ZoomIn.svg) om het document te stromen.

* **Breedte of hoogtedimensies van het Gebruik van het Passen van 0} Pagina {om het document volgens uw het schermgrootte te passen.**

* **Dock/undock PDF** u kunt de componenten van inheemse PDF de kijker dokken of losmaken gebruikend deze optie.

## Ondersteuning voor Voorvertoning van meerdere pagina&#39;s en annotaties voor PDF-element {#multi-page}

Met Adobe Experience Manager Assets kunt u een voorvertoning weergeven van een PDF-document dat uit meerdere pagina&#39;s bestaat. Neem de volgende stappen om een voorvertoning weer te geven van meerdere pagina&#39;s van een PDF-document:

1. Volg de stappen om [ activa in AEM ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/add-assets.html?lang=en) te uploaden.
1. Blader naar het PDF-document dat u wilt uploaden en bekijk een voorvertoning.
1. Open het document.
1. De PDF-documentviewer wordt standaard geladen. U kunt ook PDF-uitvoering selecteren onder het deelvenster Vertoning.
1. Onder drop-down Vertoningen, uitgezochte **Alle Vertoningen**.

U kunt [ annotaties ](#pdf-annotations) op het document van de PDF in een veelvoudige paginavoorproef ook toepassen.

> OPMERKING
> De maximale grootte van een element waarvan u een voorbeeld kunt bekijken, is 100 MB.
>

>[!VIDEO](https://video.tv.adobe.com/v/3409355)

<!--
![Multi-page Preview](/help/assets/assets/multi-page.png)
-->

**PDF-annotaties{#pdf-annotations}**

Met Experience Manager Assets kunt u opmerkingen toevoegen aan een PDF-document. Een PDF-document kan meerdere annotaties hebben.

Ga als volgt te werk om een PDF-document van een annotatie te voorzien:
1. Ga naar de Assets-interface en navigeer naar het PDF-document dat u wilt annoteren. De native PDF-viewer wordt aan de rechterkant geopend en geeft een voorvertoning van het geselecteerde PDF-document weer.
1. Klik **annoteren** van het hoogste menu.
Hieronder vindt u de annotaties die kunnen worden toegepast op een PDF-document:

<table>
        <tr>
             <th> Aantekening </th>
            <th> Beschrijving </th>
        </tr>
        <tr>
           <td> <img src="/help/assets/assets/Comment.svg"> Opmerking </td>
            <td> Selecteer Opmerking om een opmerking weer te geven. </td>
        </tr>
        <tr>
            <td> <img src="/help/assets/assets/Text.svg"> TextBox </td>
            <td> Selecteer Tekstvak om de tekst in te voeren. </td>
        </tr>
        <tr>
            <td> <img src="/help/assets/assets/Note.svg"> Vaste opmerkingen </td>
            <td> Voeg een kleine tekst of herinnering toe die u aan een bepaald gebied op de PDF kunt toevoegen. </td>
        </tr>
        <tr>
            <td> <img src="/help/assets/assets/Comment.svg"> Tekst markeren </td>
            <td> Selecteer de tekst die u in verschillende kleuren wilt markeren. </td>
        </tr>
        <tr>
            <td> <img src="/help/assets/assets/TextUnderline.svg"> Tekst onderstrepen </td>
            <td> Selecteer de tekst die u wilt onderstrepen. </td>
        </tr>
        <tr>
            <td> <img src="/help/assets/assets/TextStrikethrough.svg"> Doorhalen </td>
            <td> Selecteer de tekst die u wilt doorkruisen. </td>
        </tr>
        <tr>
            <td> <img src="/help/assets/assets/Draw.svg"> Tekenen </td>
            <td> Een visuele illustratie invoegen in de PDF. </td>
        </tr>
        <tr>
            <td> <img src="/help/assets/assets/Erase.svg"> Tekenen wissen </td>
             <td> Tekenen verwijderen of ongedaan maken. </td>
        </tr>
    </table>

>[!NOTE]
>
>De annotaties die u toevoegt aan het PDF-document zijn beschikbaar in de voorvertoningsmodus. De annotaties worden echter niet weergegeven wanneer u het PDF-document downloadt of afdrukt.

## Ondersteuning voor Voorvertoning van meerdere pagina&#39;s voor documenten in andere indelingen {#multi-format}

Naast de PDF-documenten kunt u ook een voorvertoning weergeven van meerdere pagina&#39;s voor documenten in andere indelingstypen. De ondersteunde documentindelingen zijn TXT, RTF, DOC, DOCX, PPT, PPTX, XLS en XLSX. Experience Manager Assets converteert deze documentindelingen automatisch naar een PDF-indeling en stelt deze beschikbaar voor een voorvertoning.

![ Multi-pageVoorproef van Documenten in Andere Formaten ](/help/assets/assets/multi-page-other-formats.png)

Voer de volgende stappen uit voor de voorvertoning van meerdere pagina&#39;s van andere ondersteunde documentindelingen:
1. Volg de stappen om [ activa in AEM ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/add-assets.html?lang=en) te uploaden.
1. Blader naar het document dat u wilt uploaden en bekijk een voorvertoning.
1. Open het document.
1. Selecteer PDF onder het statische gedeelte in het linkerdeelvenster. In het rechterdeelvenster ziet u de voorvertoning van meerdere pagina&#39;s van een element. Selecteer een miniatuur in het linkerdeelvenster om de pagina te kiezen waarvan u een voorvertoning wilt weergeven.

> OPMERKING
> * De maximale grootte van een element waarvan u een voorbeeld kunt bekijken, is 100 MB.
> * De maximale grootte van XLS- of XLSX-bestanden die u wilt voorvertonen, is 20 MB.
>

**zie ook**

* [Assets vertalen](translate-assets.md)
* [ASSETS HTTP API](mac-api-assets.md)
* [Door Assets ondersteunde bestandsindelingen](file-format-support.md)
* [Zoeken in middelen](search-assets.md)
* [Verbonden elementen](use-assets-across-connected-assets-instances.md)
* [Elementen rapporteren](asset-reports.md)
* [Metagegevensschema&#39;s](metadata-schemas.md)
* [Elementen downloaden](download-assets-from-aem.md)
* [Metagegevens beheren](manage-metadata.md)
* [Zoeken in facetten](search-facets.md)
* [Verzamelingen beheren](manage-collections.md)
* [Bulkmetagegevens importeren](metadata-import-export.md)
* [Publish Assets naar AEM en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)
