---
title: Uw PDF-documenten beheren in [!DNL Adobe Experience Manager].
description: PDF-documenten beheren in [!DNL Adobe Experience Manager] als [!DNL Cloud Service].
feature: Asset Management
role: User,Admin
exl-id: 29660869-6902-4093-845b-cd629be59d4d
source-git-commit: f7f60036088a2332644ce87f4a1be9bae3af1c5e
workflow-type: tm+mt
source-wordcount: '838'
ht-degree: 0%

---

# PDF-documenten beheren in Experience Manager Assets as a Cloud Service {#add-assets-to-experience-manager}

Experience Manager Assets kan naadloos worden geïntegreerd met de Document Cloud PDF Viewer, waarmee u meerdere pagina&#39;s van een PDF-document kunt voorvertonen. Daarnaast kunt u ook geavanceerde viewerfuncties voor PDF gebruiken, zoals annotaties, zoektekst, navigatie in het PDF-document met bladwijzers en miniaturen, enzovoort, onder hetzelfde dak. Met Experience Manager Assets kunt u ook documenten in andere ondersteunde indelingen uploaden en deze voorvertonen in een PDF-indeling.

De PDF-viewer van Document Cloud profiteert AEM Assets op de volgende manieren:
* [Ondersteuning voor PDF Document Cloud Viewer-componenten](#pdf-doc-cloud)
* [Ondersteuning voor Voorvertoning van meerdere pagina&#39;s en annotaties voor PDF-element](#multi-page)
* [Ondersteuning voor Voorvertoning van meerdere pagina&#39;s voor documenten in andere indelingen](#multi-format)

> Tip
> Als u de voorvertoning van meerdere pagina&#39;s van een eerder geüpload PDF-document niet kunt ophalen, selecteert u de PDF en klikt u op **![Opnieuw verwerken](/help/assets/assets/Reprocess.svg) Elementen opnieuw verwerken**.
>

## Ondersteuning voor PDF Document Cloud Viewer-componenten {#pdf-doc-cloud}

De native PDF Doc Cloud-viewer heeft de volgende componenten in AEM Assets:

* **PDF-viewer gebruiken met paginaminiaturen** De miniatuurweergave is een kleine voorvertoning van de pagina&#39;s van een PDF-document. Met behulp van miniaturen kunt u rechtstreeks naar de gewenste pagina gaan. U hebt toegang tot miniaturen van het geselecteerde PDF-document via ![miniatuur](/help/assets/assets/thumbnail.svg) in het linkerdeelvenster.

* **PDF-viewer met bladwijzers** Bladwijzer is een directe koppeling waarmee u naar de inhoud in het document kunt navigeren. U hebt toegang tot bladwijzers in het geselecteerde PDF-document via ![bladwijzer](/help/assets/assets/bookmark.svg) in het linkerdeelvenster.

* **Zoeken in PDF** U kunt zoeken gebruiken ![zoeken](/help/assets/assets/Search.svg) om de tekst in het PDF-document op te zoeken.

* **Page Up/Page Down** Pagina omhoog gebruiken ![Page Up](/help/assets/assets/ArrowUp.svg) of Page Down ![Page Down](/help/assets/assets/ArrowDown.svg) om door het document te schuiven.

* **Uitzoomen/Inzoomen** Uitzoomen gebruiken ![Uitzoomen](/help/assets/assets/ZoomOut.svg) of Inzoomen ![Inzoomen](/help/assets/assets/ZoomIn.svg) om het document uit te rekken.

* **Pagina passend maken** Gebruik breedte- of hoogteafmetingen om het document aan te passen aan de schermgrootte.

* **PDF koppelen/loskoppelen** Met deze optie kunt u de componenten van de native PDF-viewer koppelen of loskoppelen.

## Ondersteuning voor Voorvertoning van meerdere pagina&#39;s en annotaties voor PDF-element {#multi-page}

Met Adobe Experience Manager Assets kunt u een voorvertoning weergeven van een PDF-document dat uit meerdere pagina&#39;s bestaat. Neem de volgende stappen om een voorvertoning weer te geven van meerdere pagina&#39;s van een PDF-document:

1. Voer de volgende stappen uit om [elementen uploaden in AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/add-assets.html?lang=en).
1. Blader naar het PDF-document dat u wilt uploaden en bekijk een voorvertoning.
1. Open het document.
1. De PDF-documentviewer wordt standaard geladen. U kunt ook PDF-uitvoering selecteren onder het deelvenster Vertoning.
1. Selecteer in de vervolgkeuzelijst Uitvoeringen de optie **Alle uitvoeringen**.

U kunt ook [annotaties](#pdf-annotations) op het PDF-document in een voorvertoning van meerdere pagina&#39;s.

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
1. Ga naar de interface Middelen en navigeer naar het PDF-document dat u wilt annoteren. De native PDF-viewer wordt aan de rechterkant geopend en geeft een voorvertoning van het geselecteerde PDF-document weer.
1. Klikken **Annoteren** in het bovenste menu.
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
            <td> <img src="/help/assets/assets/Text.svg"> Tekstvak </td>
            <td> Selecteer Tekstvak om de tekst in te voeren. </td>
        </tr>
        <tr>
            <td> <img src="/help/assets/assets/Note.svg"> Notities </td>
            <td> Voeg een kleine tekst of herinnering toe die u aan een bepaald gebied op de PDF kunt toevoegen. </td>
        </tr>
        <tr>
            <td> <img src="/help/assets/assets/Comment.svg"> Tekstmarkering </td>
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

![Voorvertoning van meerdere pagina&#39;s van documenten in andere indelingen](/help/assets/assets/multi-page-other-formats.png)

Voer de volgende stappen uit voor de voorvertoning van meerdere pagina&#39;s van andere ondersteunde documentindelingen:
1. Voer de volgende stappen uit om [elementen uploaden in AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/add-assets.html?lang=en).
1. Blader naar het document dat u wilt uploaden en bekijk een voorvertoning.
1. Open het document.
1. Selecteer PDF onder het statische gedeelte in het linkerdeelvenster. In het rechterdeelvenster ziet u de voorvertoning van meerdere pagina&#39;s van een element. Selecteer een miniatuur in het linkerdeelvenster om de pagina te kiezen waarvan u een voorvertoning wilt weergeven.

> OPMERKING
> * De maximale grootte van een element waarvan u een voorbeeld kunt bekijken, is 100 MB.
> * De maximale grootte van XLS- of XLSX-bestanden die u wilt voorvertonen, is 20 MB.
>

**Zie ook**

* [Elementen vertalen](translate-assets.md)
* [Elementen HTTP-API](mac-api-assets.md)
* [Ondersteunde bestandsindelingen](file-format-support.md)
* [Zoeken in middelen](search-assets.md)
* [Verbonden elementen](use-assets-across-connected-assets-instances.md)
* [Elementen rapporteren](asset-reports.md)
* [Metagegevensschema&#39;s](metadata-schemas.md)
* [Elementen downloaden](download-assets-from-aem.md)
* [Metagegevens beheren](manage-metadata.md)
* [Zoeken in facetten](search-facets.md)
* [Verzamelingen beheren](manage-collections.md)
* [Bulkmetagegevens importeren](metadata-import-export.md)
* [Middelen publiceren naar AEM en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)
