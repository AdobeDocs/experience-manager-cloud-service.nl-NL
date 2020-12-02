---
title: Ontwikkelaarsreferenties voor [!DNL Assets]
description: '[!DNL Assets] APIs and developer reference content lets you manage assets, including binary files, metadata, renditions, comments, and [!DNL Content Fragments].'
contentOwner: AG
translation-type: tm+mt
source-git-commit: 5be8ab734306ad1442804b3f030a56be1d3b5dfa
workflow-type: tm+mt
source-wordcount: '1203'
ht-degree: 1%

---


# [!DNL Assets] API&#39;s en referentiemateriaal voor ontwikkelaars  {#assets-cloud-service-apis}

Het artikel bevat referentiemateriaal en bronnen voor ontwikkelaars van [!DNL Assets] als een [!DNL Cloud Service]. Het omvat nieuwe uploadmethode, API verwijzing, en informatie over de steun die in postverwerkingswerkschema&#39;s wordt verstrekt.

## Elementen uploaden {#asset-upload-technical}

[!DNL Experience Manager] als  [!DNL Cloud Service] biedt een nieuwe methode om elementen te uploaden naar de repository. Gebruikers kunnen de elementen rechtstreeks uploaden naar de cloudopslag met HTTP API. De stappen voor het uploaden van een binair bestand zijn:

1. [Verzend een HTTP-aanvraag](#initiate-upload). Het informeert [!DNL Experience Manage]r plaatsing van uw intent om een nieuw binair getal te uploaden.
1. [POST de inhoud van de ](#upload-binary) binaire illustratie aan één of meerdere URIs die door het openingsverzoek wordt verstrekt.
1. [Verzend een HTTP-](#complete-upload) aanvraag om de server te laten weten dat de inhoud van het binaire bestand is geüpload.

![Overzicht van het directe binaire upload protocol](assets/add-assets-technical.png)

Deze aanpak biedt een schaalbare en krachtigere verwerking van geüploade bedrijfsmiddelen. De verschillen ten opzichte van [!DNL Experience Manager] 6.5 zijn:

* De binaire getallen gaan niet door [!DNL Experience Manager], die nu eenvoudig het uploadproces met de binaire wolkenopslag coördineert die voor de plaatsing wordt gevormd.
* Binaire cloudopslag werkt met een Content Delivery Network (CDN) of Edge-netwerk. Een CDN selecteert een uploadeindpunt dat dichter voor een cliënt is. Wanneer de gegevens een kortere afstand aan een nabijgelegen eindpunt reizen, verbeteren de uploadprestaties en de gebruikerservaring, vooral voor geografisch verdeelde teams.

>[!NOTE]
>
>Zie de cliëntcode om deze benadering in open-bron [aem-upload bibliotheek](https://github.com/adobe/aem-upload) uit te voeren.

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
* `minPartSize` (nummer): De minimale lengte, in bytes, van gegevens die aan om het even welke uploadURIs kunnen worden verstrekt, als er meer dan één URI is.
* `maxPartSize` (nummer): De maximumlengte, in bytes, van gegevens die aan om het even welke uploadURIs kunnen worden verstrekt, als er meer dan één URI is.

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

>!![NOTE]
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
* [De Experience Cloud als  [!DNL Cloud Service] SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md).

