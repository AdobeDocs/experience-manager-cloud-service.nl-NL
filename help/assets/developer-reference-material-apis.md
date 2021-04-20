---
title: Ontwikkelaarsreferenties voor [!DNL Assets]
description: '[!DNL Assets] APIs and developer reference content lets you manage assets, including binary files, metadata, renditions, comments, and [!DNL Content Fragments].'
contentOwner: AG
feature: APIs,Assets HTTP API
role: Developer,Architect,Administrator
translation-type: tm+mt
source-git-commit: 70068609e51f96c010204b8915593a52f610aded
workflow-type: tm+mt
source-wordcount: '1392'
ht-degree: 1%

---


# [!DNL Adobe Experience Manager Assets] Gebruiksgevallen, API&#39;s en referentiemateriaal voor ontwikkelaars  {#assets-cloud-service-apis}

Het artikel bevat aanbevelingen, referentiematerialen en bronnen voor ontwikkelaars van [!DNL Assets] als een [!DNL Cloud Service]. Het omvat nieuwe module voor het uploaden van middelen, API-referentie en informatie over de ondersteuning die wordt geboden in workflows na verwerking.

## [!DNL Experience Manager Assets] API&#39;s en bewerkingen  {#use-cases-and-apis}

[!DNL Assets] as  [!DNL Cloud Service] biedt verschillende API&#39;s die programmatisch kunnen communiceren met digitale elementen. Elke API ondersteunt specifieke gebruiksgevallen, zoals vermeld in de onderstaande tabel. De [!DNL Assets]-gebruikersinterface, [!DNL Experience Manager]-bureaubladtoepassing en [!DNL Adobe Asset Link] ondersteunen alle of sommige bewerkingen.

>[!CAUTION]
>
>Sommige API&#39;s blijven bestaan, maar worden niet actief ondersteund (aangeduid met een ×). Gebruik deze API&#39;s zoveel mogelijk niet.

| Ondersteuningsniveau | Beschrijving |
| ------------- | --------------------------- |
| ✓ | Ondersteund |
| × | Niet ondersteund. Niet gebruiken. |
| - | Niet beschikbaar |

| Hoofdletters gebruiken | [aem-upload](https://github.com/adobe/aem-upload) | [AEM / Sling / ](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/index.html) JCRJava API&#39;s | [Asset compute](https://experienceleague.adobe.com/docs/asset-compute/using/extend/understand-extensibility.html) | [[!DNL Assets] HTTP-API](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/admin/mac-api-assets.html#create-an-asset) | Sling [GET](https://sling.apache.org/documentation/bundles/rendering-content-default-get-servlets.html) / [POST](https://sling.apache.org/documentation/bundles/manipulating-content-the-slingpostservlet-servlets-post.html) servlets | [GraphQL](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html) _(Voorvertoning)_ |
| ----------------|:---:|:---:|:---:|:---:|:---:|:---:|
| **Origineel binair** |  |  |  |  |  |  |
| Origineel maken | ✓ | × | - | × | × | - |
| Origineel lezen | - | × | ✓ | ✓ | ✓ | - |
| Origineel bijwerken | ✓ | × | ✓ | × | × | - |
| Origineel verwijderen | - | ✓ | - | ✓ | ✓ | - |
| Origineel kopiëren | - | ✓ | - | ✓ | ✓ | - |
| Origineel verplaatsen | - | ✓ | - | ✓ | ✓ | - |
| **Metagegevens** |  |  |  |  |  |  |
| Metagegevens maken | - | ✓ | ✓ | ✓ | ✓ | - |
| Metagegevens lezen | - | ✓ | - | ✓ | ✓ | - |
| Metagegevens bijwerken | - | ✓ | ✓ | ✓ | ✓ | - |
| Metagegevens verwijderen | - | ✓ | ✓ | ✓ | ✓ | - |
| Metagegevens kopiëren | - | ✓ | - | ✓ | ✓ | - |
| Metagegevens verplaatsen | - | ✓ | - | ✓ | ✓ | - |
| **Inhoudsfragmenten (CF)** |  |  |  |  |  |  |
| CF maken | - | ✓ | - | ✓ | - | - |
| CF lezen | - | ✓ | - | ✓ | - | ✓ |
| CF bijwerken | - | ✓ | - | ✓ | - | - |
| CF verwijderen | - | ✓ | - | ✓ | - | - |
| CF kopiëren | - | ✓ | - | ✓ | - | - |
| CF verplaatsen | - | ✓ | - | ✓ | - | - |
| **Versies** |  |  |  |  |  |  |
| Versie maken | ✓ | ✓ | - | - | - | - |
| Leesversie | - | ✓ | - | - | - | - |
| Versie verwijderen | - | ✓ | - | - | - | - |
| **Mappen** |  |  |  |  |  |  |
| Map maken | ✓ | ✓ | - | ✓ | - | - |
| Map lezen | - | ✓ | - | ✓ | - | - |
| Map verwijderen | ✓ | ✓ | - | ✓ | - | - |
| Map kopiëren | ✓ | ✓ | - | ✓ | - | - |
| Map verplaatsen | ✓ | ✓ | - | ✓ | - | - |

## Elementen uploaden {#asset-upload-technical}

In [!DNL Experience Manager] als [!DNL Cloud Service], kunt u de activa aan de cloudopslag direct uploaden gebruikend HTTP API. De stappen voor het uploaden van een binair bestand zijn:

1. [Verzend een HTTP-aanvraag](#initiate-upload). Het informeert [!DNL Experience Manage]r plaatsing van uw intent om een nieuw binair getal te uploaden.
1. [POST de inhoud van de ](#upload-binary) binaire illustratie aan één of meerdere URIs die door het openingsverzoek wordt verstrekt.
1. [Verzend een HTTP-](#complete-upload) aanvraag om de server te laten weten dat de inhoud van het binaire bestand is geüpload.

![Overzicht van het directe binaire upload protocol](assets/add-assets-technical.png)

Deze aanpak biedt een schaalbare en krachtigere verwerking van geüploade bedrijfsmiddelen. De verschillen ten opzichte van [!DNL Experience Manager] 6.5 zijn:

* De binaire getallen gaan niet door [!DNL Experience Manager], die nu eenvoudig het uploadproces met de binaire wolkenopslag coördineert die voor de plaatsing wordt gevormd.
* Binaire cloudopslag werkt met een Content Delivery Network (CDN) of Edge-netwerk. Een CDN selecteert een uploadeindpunt dat dichter voor een cliënt is. Wanneer de gegevens een kortere afstand aan een nabijgelegen eindpunt reizen, verbeteren de uploadprestaties en de gebruikerservaring, vooral voor geografisch verdeelde teams.

>[!NOTE]
Zie de cliëntcode om deze benadering in open-bron [aem-upload bibliotheek](https://github.com/adobe/aem-upload) uit te voeren.

### Uploaden {#initiate-upload} starten

Verzend een HTTP-POST-aanvraag naar de gewenste map. In deze map worden middelen gemaakt of bijgewerkt. Neem de kiezer `.initiateUpload.json` op om aan te geven dat de aanvraag het uploaden van een binair bestand moet starten. Het pad naar de map waar het element moet worden gemaakt, is bijvoorbeeld `/assets/folder`. Het verzoek van de POST is `POST https://[aem_server]:[port]/content/dam/assets/folder.initiateUpload.json`.

Het inhoudstype van de aanvraaginstantie moet `application/x-www-form-urlencoded` formuliergegevens zijn, die de volgende velden bevatten:

* `(string) fileName`: Vereist. De naam van het element zoals deze wordt weergegeven in [!DNL Experience Manager].
* `(number) fileSize`: Vereist. De bestandsgrootte, in bytes, van het element dat wordt geüpload.

Eén aanvraag kan worden gebruikt om uploads voor meerdere binaire bestanden te starten, zolang elk binair getal de vereiste velden bevat. Als dit lukt, reageert de aanvraag met een `201`-statuscode en een body die JSON-gegevens in de volgende indeling bevat:

```json
{
    "completeURI": "(string)",
    "folderPath": (string)",
    "files": [
        {
            "fileName": "(string)",
            "mimeType": "(string)",
            "uploadToken": "(string)",
            "uploadURIs": [
                "(string)"
            ]
        }
    ]
}
```

* `completeURI` (tekenreeks): Roep deze URI aan wanneer het binaire bestand klaar is met uploaden. De URI kan een absolute of relatieve URI zijn en clients moeten beide kunnen afhandelen. Dat wil zeggen dat de waarde `"https://author.acme.com/content/dam.completeUpload.json"` of `"/content/dam.completeUpload.json"` Zie [complete upload](#complete-upload) kan zijn.
* `folderPath` (tekenreeks): Volledig pad naar de map waarin het binaire bestand is geüpload.
* `(files)` (array): Een lijst met elementen waarvan de lengte en volgorde overeenkomen met de lengte en volgorde van de lijst met binaire informatie die in het verzoek tot inleiding wordt verstrekt.
* `fileName` (tekenreeks): De naam van het overeenkomstige binaire getal, zoals opgegeven in het initiërende verzoek. Deze waarde moet in het volledige verzoek worden opgenomen.
* `mimeType` (tekenreeks): Het mime type van het overeenkomstige binaire getal, zoals die in het in werking gestelde verzoek wordt verstrekt. Deze waarde moet in het volledige verzoek worden opgenomen.
* `uploadToken` (tekenreeks): Een upload token voor het overeenkomstige binaire getal. Deze waarde moet in het volledige verzoek worden opgenomen.
* `uploadURIs` (array): Een lijst met tekenreeksen waarvan de waarden volledige URI&#39;s zijn waarnaar de inhoud van het binaire bestand moet worden geüpload (zie binair [ ](#upload-binary)uploaden).
* `minPartSize` (nummer): De minimale lengte, in bytes, van gegevens die aan om het even welk van het  `uploadURIs`, als er meer dan één URI kan worden verstrekt.
* `maxPartSize` (nummer): De maximumlengte, in bytes, van gegevens die aan om het even welk van het kunnen worden verstrekt,  `uploadURIs`als er meer dan één URI is.

### Binair {#upload-binary} uploaden

De uitvoer van het starten van een upload bevat een of meer URI-waarden voor uploaden. Als er meer dan één URI is opgegeven, splitst de client het binaire getal in delen en vraagt de POST van elk onderdeel naar elke URI, op volgorde. Alle URI&#39;s gebruiken. Zorg ervoor dat de grootte van elk onderdeel binnen de minimum- en maximumgrootte ligt die in de reactie van de aanvrager zijn opgegeven. Met behulp van CDN-randknooppunten kunt u het opvragen van binaire bestanden versnellen.

Een mogelijke methode hiervoor is het berekenen van de onderdeelgrootte op basis van het aantal URI&#39;s voor uploaden dat door de API wordt verschaft. Bijvoorbeeld, veronderstel de totale grootte van het binaire getal 20.000 bytes is en het aantal upload URIs 2 is. Voer vervolgens de volgende stappen uit:

* Onderdeelgrootte berekenen door totale grootte te delen door aantal URI&#39;s: 20,000 / 2 = 10,000.
* POST bytewaaier 0-9.999 van binair aan eerste URI in de lijst van upload URIs.
* POST bytewaaier 10.000 - 19.999 van binair aan tweede URI in de lijst van upload URIs.

Als het uploaden is voltooid, reageert de server op elk verzoek met een `201` statuscode.

### Uploaden {#complete-upload} voltooien

Nadat alle delen van een binair dossier worden geupload, leg een verzoek van de POST van HTTP aan volledige URI voor die door de initiatiegegevens wordt verstrekt. Het inhoudstype van de aanvraaginstantie moet `application/x-www-form-urlencoded` formuliergegevens zijn, die de volgende velden bevatten.

| Fields | Type | Vereist of niet | Beschrijving |
|---|---|---|---|
| `fileName` | Tekenreeks | Vereist | De naam van het element, zoals deze werd verstrekt in de inleidingsgegevens. |
| `mimeType` | Tekenreeks | Vereist | Het HTTP-inhoudstype van het binaire getal, zoals is opgegeven door de initiatiegegevens. |
| `uploadToken` | Tekenreeks | Vereist | Upload token voor het binaire bestand, zoals werd opgegeven in de initiatiegegevens. |
| `createVersion` | Boolean | Optioneel | Als `True` en een element met de opgegeven naam bestaan, maakt [!DNL Experience Manager] een nieuwe versie van het element. |
| `versionLabel` | Tekenreeks | Optioneel | Als er een nieuwe versie wordt gemaakt, wordt het label gekoppeld aan de nieuwe versie van een element. |
| `versionComment` | Tekenreeks | Optioneel | Als er een nieuwe versie wordt gemaakt, worden de opmerkingen gekoppeld aan de versie. |
| `replace` | Boolean | Optioneel | Als `True` en een element met de opgegeven naam bestaat, verwijdert [!DNL Experience Manager] het element en maakt u het opnieuw. |

>[!NOTE]
Als het element bestaat en `createVersion` noch `replace` is opgegeven, werkt [!DNL Experience Manager] de huidige versie van het element bij met het nieuwe binaire getal.

Net als bij het initiëringsproces kunnen de volledige aanvraaggegevens informatie voor meer dan één bestand bevatten.

Het uploaden van een binair getal gebeurt pas wanneer de volledige URL voor het bestand wordt aangeroepen. Een element wordt verwerkt nadat het uploadproces is voltooid. De verwerking wordt niet gestart, zelfs niet als het binaire bestand van het element volledig is geüpload maar het uploadproces niet is voltooid.

Als dit gelukt is, reageert de server met de statuscode `200`.

### Opensource-uploadbibliotheek {#open-source-upload-library}

Adobe biedt opensource-bibliotheken en -gereedschappen voor meer informatie over de uploadalgoritmen of om uw eigen uploadscripts en -gereedschappen te maken:

* [Open-source Aem-upload bibliotheek](https://github.com/adobe/aem-upload).
* [Opensource opdrachtregelprogramma](https://github.com/adobe/aio-cli-plugin-aem).

### API&#39;s voor het uploaden van afgekeurde elementen {#deprecated-asset-upload-api}

<!-- #ENGCHECK review / update the list of deprecated APIs below. -->

De nieuwe uploadmethode wordt alleen ondersteund voor [!DNL Adobe Experience Manager] als [!DNL Cloud Service]. De API&#39;s van [!DNL Adobe Experience Manager] 6.5 zijn afgekeurd. De methoden voor het uploaden of bijwerken van elementen of uitvoeringen (elke binaire upload) zijn afgekeurd in de volgende API&#39;s:

* [Experience Manager Assets HTTP API](mac-api-assets.md)
* `AssetManager` Java API, zoals  `AssetManager.createAsset(..)`

>[!MORELIKETHIS]
* [Open-source Aem-upload bibliotheek](https://github.com/adobe/aem-upload).
* [Opensource opdrachtregelprogramma](https://github.com/adobe/aio-cli-plugin-aem).


## Workflows voor verwerking en naverwerking van bedrijfsmiddelen {#post-processing-workflows}

In [!DNL Experience Manager], is de activaverwerking gebaseerd op **[!UICONTROL Processing Profiles]** configuratie die [activa microservices](asset-microservices-configure-and-use.md#get-started-using-asset-microservices) gebruikt. Voor verwerking zijn geen ontwikkelaarsextensies vereist.

Voor workflowconfiguratie na verwerking gebruikt u de standaardworkflows met extensies met aangepaste stappen.

## Ondersteuning van workflowstappen in de naverwerkingsworkflow {#post-processing-workflows-steps}

Klanten die een upgrade uitvoeren van eerdere versies van [!DNL Experience Manager], kunnen de asset-microservices gebruiken om elementen te verwerken. De &#39;cloud-native asset microservices&#39; zijn veel eenvoudiger te configureren en gebruiken. Enkele workflowstappen die in de [!UICONTROL DAM Update Asset]-workflow in de vorige versie werden gebruikt, worden niet ondersteund.

[!DNL Experience Manager] als  [!DNL Cloud Service] ondersteuning voor de volgende workflowstappen:

* `com.day.cq.dam.similaritysearch.internal.workflow.process.AutoTagAssetProcess`
* `com.day.cq.dam.core.impl.process.CreateAssetLanguageCopyProcess`
* `com.day.cq.wcm.workflow.process.CreateVersionProcess`
* `com.day.cq.dam.similaritysearch.internal.workflow.smarttags.StartTrainingProcess`
* `com.day.cq.dam.similaritysearch.internal.workflow.smarttags.TransferTrainingDataProcess`
* `com.day.cq.dam.core.impl.process.TranslateAssetLanguageCopyProcess`
* `com.day.cq.dam.core.impl.process.UpdateAssetLanguageCopyProcess`
* `com.adobe.cq.workflow.replication.impl.ReplicationWorkflowProcess`
* `com.day.cq.dam.core.impl.process.DamUpdateAssetWorkflowCompletedProcess`

De volgende technische workflowmodellen worden vervangen door asset microservices of de ondersteuning is niet beschikbaar:

* `com.day.cq.dam.core.impl.process.DamMetadataWritebackWorkflowCompletedProcess`
* `com.day.cq.dam.core.process.DeleteImagePreviewProcess`
* `com.day.cq.dam.s7dam.common.process.DMEncodeVideoWorkflowCompletedProcess`
* `com.day.cq.dam.core.process.GateKeeperProcess`
* `com.day.cq.dam.core.process.AssetOffloadingProcess`
* `com.day.cq.dam.core.process.MetadataProcessorProcess`
* `com.day.cq.dam.core.process.XMPWritebackProcess`
* `com.adobe.cq.dam.dm.process.workflow.DMImageProcess`
* `com.day.cq.dam.s7dam.common.process.S7VideoThumbnailProcess`
* `com.day.cq.dam.scene7.impl.process.Scene7UploadProcess`
* `com.day.cq.dam.s7dam.common.process.VideoProxyServiceProcess`
* `com.day.cq.dam.s7dam.common.process.VideoThumbnailDownloadProcess`
* `com.day.cq.dam.s7dam.common.process.VideoUserUploadedThumbnailProcess`
* `com.day.cq.dam.core.process.CreatePdfPreviewProcess`
* `com.day.cq.dam.core.process.CreateWebEnabledImageProcess`
* `com.day.cq.dam.video.FFMpegThumbnailProcess`
* `com.day.cq.dam.core.process.ThumbnailProcess`
* `com.day.cq.dam.cameraraw.process.CameraRawHandlingProcess`
* `com.day.cq.dam.core.process.CommandLineProcess`
* `com.day.cq.dam.pdfrasterizer.process.PdfRasterizerHandlingProcess`
* `com.day.cq.dam.core.process.AddPropertyWorkflowProcess`
* `com.day.cq.dam.core.process.CreateSubAssetsProcess`
* `com.day.cq.dam.core.process.DownloadAssetProcess`
* `com.day.cq.dam.word.process.ExtractImagesProcess`
* `com.day.cq.dam.word.process.ExtractPlainProcess`
* `com.day.cq.dam.video.FFMpegTranscodeProcess`
* `com.day.cq.dam.ids.impl.process.IDSJobProcess`
* `com.day.cq.dam.indd.process.INDDMediaExtractProcess`
* `com.day.cq.dam.indd.process.INDDPageExtractProcess`
* `com.day.cq.dam.core.impl.lightbox.LightboxUpdateAssetProcess`
* `com.day.cq.dam.pim.impl.sourcing.upload.process.ProductAssetsUploadProcess`
* `com.day.cq.dam.core.process.ScheduledPublishBPProcess`
* `com.day.cq.dam.core.process.ScheduledUnPublishBPProcess`
* `com.day.cq.dam.core.process.SendDownloadAssetEmailProcess`
* `com.day.cq.dam.core.impl.process.SendTransientWorkflowCompletedEmailProcess`

<!-- PPTX source: slide in add-assets.md - overview of direct binary upload section of 
https://adobe-my.sharepoint.com/personal/gklebus_adobe_com/_layouts/15/guestaccess.aspx?guestaccesstoken=jexDC5ZnepXSt6dTPciH66TzckS1BPEfdaZuSgHugL8%3D&docid=2_1ec37f0bd4cc74354b4f481cd420e07fc&rev=1&e=CdgElS
-->

>[!MORELIKETHIS]
* [[!DNL Experience Cloud] as a [!DNL Cloud Service] SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md).

