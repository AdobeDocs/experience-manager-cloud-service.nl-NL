---
title: Ontwikkelaarsreferenties voor [!DNL Assets]
description: '"[!DNL Assets] Met API''s en inhoud voor ontwikkelaarsverwijzing kunt u elementen beheren, zoals binaire bestanden, metagegevens, uitvoeringen, opmerkingen en [!DNL Content Fragments]."'
contentOwner: AG
feature: APIs,Assets HTTP API
role: Developer,Architect,Admin
exl-id: c75ff177-b74e-436b-9e29-86e257be87fb
source-git-commit: f5282d149e80328742ff9008441960f62cea6290
workflow-type: tm+mt
source-wordcount: '1732'
ht-degree: 1%

---

# [!DNL Adobe Experience Manager Assets] Gebruiksgevallen, API&#39;s en referentiemateriaal voor ontwikkelaars {#assets-cloud-service-apis}

Het artikel bevat aanbevelingen, referentiematerialen en bronnen voor ontwikkelaars van [!DNL Assets] als [!DNL Cloud Service]. Het omvat nieuwe module voor het uploaden van middelen, API-referentie en informatie over de ondersteuning die wordt geboden in workflows na verwerking.

## [!DNL Experience Manager Assets] API&#39;s en bewerkingen {#use-cases-and-apis}

[!DNL Assets] als [!DNL Cloud Service] bevat verschillende API&#39;s die programmatisch kunnen communiceren met digitale elementen. Elke API ondersteunt specifieke gebruiksgevallen, zoals vermeld in de onderstaande tabel. De [!DNL Assets] gebruikersinterface, [!DNL Experience Manager] bureaubladtoepassing en [!DNL Adobe Asset Link] alle of sommige bewerkingen ondersteunen.

>[!CAUTION]
>
>Sommige API&#39;s blijven bestaan, maar worden niet actief ondersteund (aangeduid met een ×). Gebruik deze API&#39;s zoveel mogelijk niet.

| Ondersteuningsniveau | Beschrijving |
| ------------- | --------------------------- |
| ✓ | Ondersteund |
| × | Niet ondersteund. Niet gebruiken. |
| - | Niet beschikbaar |

| Hoofdletters gebruiken | [aem-upload](https://github.com/adobe/aem-upload) | [Experience Manager / Verkopen / JCR](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/index.html) Java API&#39;s | [Asset compute](https://experienceleague.adobe.com/docs/asset-compute/using/extend/understand-extensibility.html) | [[!DNL Assets] HTTP-API](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/admin/mac-api-assets.html#create-an-asset) | Sling [GET](https://sling.apache.org/documentation/bundles/rendering-content-default-get-servlets.html) / [POST](https://sling.apache.org/documentation/bundles/manipulating-content-the-slingpostservlet-servlets-post.html) servlets | [GraphQL](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html) |
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

## Elementen uploaden {#asset-upload}

In [!DNL Experience Manager] als [!DNL Cloud Service]kunt u de elementen rechtstreeks uploaden naar de cloudopslag met HTTP API. De stappen voor het uploaden van een binair bestand staan hieronder. Voer deze stappen uit in een externe toepassing en niet in de [!DNL Experience Manager] JVM.

1. [Een HTTP-aanvraag verzenden](#initiate-upload). Het geeft informatie [!DNL Experience Manage]r plaatsing van uw intent om een nieuw binair getal te uploaden.
1. [PUT de inhoud van binair getal](#upload-binary) naar een of meer URI&#39;s die in het inleidingsverzoek worden verstrekt.
1. [Een HTTP-aanvraag verzenden](#complete-upload) om de server mee te delen dat de inhoud van binair getal met succes werd geüpload.

![Overzicht van het directe binaire upload protocol](assets/add-assets-technical.png)

>[!IMPORTANT]
Voer de bovenstaande stappen uit in een externe toepassing en niet in de [!DNL Experience Manager] JVM.

Deze aanpak biedt een schaalbare en krachtigere verwerking van geüploade bedrijfsmiddelen. De verschillen ten opzichte van [!DNL Experience Manager] 6,5 zijn:

* Binaire getallen worden niet doorlopen [!DNL Experience Manager], die het uploadproces nu eenvoudig coördineert met de binaire cloudopslag die voor de plaatsing wordt gevormd.
* Binaire cloudopslag werkt met een Content Delivery Network (CDN) of Edge-netwerk. Een CDN selecteert een uploadeindpunt dat dichter voor een cliënt is. Wanneer de gegevens een kortere afstand aan een nabijgelegen eindpunt reizen, verbeteren de uploadprestaties en de gebruikerservaring, vooral voor geografisch verdeelde teams.

>[!NOTE]
Zie de cliëntcode om deze benadering in open-source uit te voeren [aem-upload bibliotheek](https://github.com/adobe/aem-upload).

### Uploaden starten {#initiate-upload}

Verzend een HTTP-POST-aanvraag naar de gewenste map. In deze map worden middelen gemaakt of bijgewerkt. Inclusief de kiezer `.initiateUpload.json` om erop te wijzen dat het verzoek het uploaden van een binair dossier moet in werking stellen. Het pad naar de map waar het element moet worden gemaakt, is bijvoorbeeld `/assets/folder`. Het verzoek van de POST is `POST https://[aem_server]:[port]/content/dam/assets/folder.initiateUpload.json`.

Het inhoudstype van de aanvraaginstantie moet `application/x-www-form-urlencoded` formuliergegevens met de volgende velden:

* `(string) fileName`: Vereist. De naam van het element zoals het wordt weergegeven [!DNL Experience Manager].
* `(number) fileSize`: Vereist. De bestandsgrootte, in bytes, van het element dat wordt geüpload.

Eén aanvraag kan worden gebruikt om uploads voor meerdere binaire bestanden te starten, zolang elk binair getal de vereiste velden bevat. Als dit lukt, reageert de aanvraag op een `201` statuscode en een body die JSON-gegevens in de volgende indeling bevat:

```json
{
    "completeURI": "(string)",
    "folderPath": "(string)",
    "files": [
        {
            "fileName": "(string)",
            "mimeType": "(string)",
            "uploadToken": "(string)",
            "uploadURIs": [
                "(string)"
            ],
            "minPartSize": (number),
            "maxPartSize": (number)
        }
    ]
}
```

* `completeURI` (tekenreeks): Roep deze URI aan wanneer het binaire bestand klaar is met uploaden. De URI kan een absolute of relatieve URI zijn en clients moeten beide kunnen afhandelen. De waarde kan dus `"https://[aem_server]:[port]/content/dam.completeUpload.json"` of `"/content/dam.completeUpload.json"` Zie [uploaden voltooien](#complete-upload).
* `folderPath` (tekenreeks): Volledig pad naar de map waarin het binaire bestand is geüpload.
* `(files)` (array): Een lijst met elementen waarvan de lengte en volgorde overeenkomen met de lengte en volgorde van de lijst met binaire informatie die in het verzoek tot inleiding wordt verstrekt.
* `fileName` (tekenreeks): De naam van het overeenkomstige binaire getal, zoals opgegeven in het initiërende verzoek. Deze waarde moet in het volledige verzoek worden opgenomen.
* `mimeType` (tekenreeks): Het mime type van het overeenkomstige binaire getal, zoals die in het in werking gestelde verzoek wordt verstrekt. Deze waarde moet in het volledige verzoek worden opgenomen.
* `uploadToken` (tekenreeks): Een upload token voor het overeenkomstige binaire getal. Deze waarde moet in het volledige verzoek worden opgenomen.
* `uploadURIs` (array): Een lijst met tekenreeksen waarvan de waarden volledige URI&#39;s zijn waarnaar de inhoud van het binaire bestand moet worden geüpload (zie [Binair bestand uploaden](#upload-binary)).
* `minPartSize` (nummer): De minimumlengte, in bytes, van gegevens die aan om het even welk van `uploadURIs`, als er meer dan één URI is.
* `maxPartSize` (nummer): De maximumlengte, in bytes, van gegevens die aan om het even welk van `uploadURIs`, als er meer dan één URI is.

### Binair bestand uploaden {#upload-binary}

De uitvoer van het starten van een upload bevat een of meer URI-waarden voor uploaden. Als er meerdere URI&#39;s zijn opgegeven, kan de client de binaire code splitsen in onderdelen en PUT-aanvragen van elk onderdeel naar de opgegeven URI&#39;s voor uploaden in volgorde indienen. Houd u aan de volgende richtlijnen wanneer u ervoor kiest om het binaire getal in delen te splitsen:

* Elk deel, met uitzondering van het laatste, moet groter zijn dan of gelijk zijn aan `minPartSize`.
* Elk onderdeel moet een grootte hebben die kleiner is dan of gelijk is aan `maxPartSize`.
* Als de grootte van uw binair getal overschrijdt `maxPartSize`, splitst de binaire waarde in delen om deze te uploaden.
* U hoeft niet alle URI&#39;s te gebruiken.

Als de grootte van uw binair getal kleiner dan of gelijk aan is `maxPartSize`, kunt u in plaats daarvan het gehele binaire bestand uploaden naar één URI voor uploaden. Als er meer dan één URI voor uploaden is opgegeven, gebruikt u de eerste URI en negeert u de rest. U hoeft niet alle URI&#39;s te gebruiken.

Met behulp van CDN-randknooppunten kunt u het opvragen van binaire bestanden versnellen.

De eenvoudigste manier om dit te bereiken is om de waarde van `maxPartSize` als de grootte van uw onderdeel. Het API-contract garandeert dat er voldoende URI&#39;s zijn voor het uploaden van het binaire bestand als u deze waarde als deelgrootte gebruikt. Hiervoor splitst u het binaire bestand in delen van grootte `maxPartSize`, met één URI voor elk onderdeel op volgorde. Het laatste deel kan elke grootte kleiner dan of gelijk aan `maxPartSize`. Stel bijvoorbeeld dat de totale grootte van het binaire getal 20.000 bytes is. `minPartSize` is 5.000 bytes, `maxPartSize` is 8.000 bytes, en het aantal upload URIs is 5. Voer de volgende stappen uit:

* Upload de eerste 8.000 bytes van het binaire getal met behulp van de eerste upload URI.
* Upload de tweede 8.000 bytes van het binaire getal met behulp van de tweede upload URI.
* Upload de laatste 4.000 bytes van het binaire getal met behulp van de derde upload URI. Aangezien dit het laatste deel is, hoeft het niet groter te zijn dan `minPartSize`.
* U hoeft de laatste twee URI&#39;s voor uploaden niet te gebruiken. U kunt ze negeren.

Een algemene fout is om de onderdeelgrootte te berekenen op basis van het aantal URI&#39;s voor uploaden dat door de API wordt verschaft. Het API-contract garandeert niet dat deze aanpak werkt en kan leiden tot deelgrootten die buiten het bereik liggen tussen `minPartSize` en `maxPartSize`. Dit kan resulteren in binaire upload mislukkingen.

Opnieuw, de gemakkelijkste en veiligste manier is eenvoudig delen van grootte gelijk aan te gebruiken `maxPartSize`.

Als het uploaden is gelukt, reageert de server op elke aanvraag met een `201` statuscode.

>[!NOTE]
Voor meer informatie over het uploadalgoritme, zie [officiële functiedocumentatie](https://jackrabbit.apache.org/oak/docs/features/direct-binary-access.html#Upload) en [API-documentatie](https://jackrabbit.apache.org/oak/docs/apidocs/org/apache/jackrabbit/api/binary/BinaryUpload.html) in het Apache Jackrabbit Oak-project.

### Uploaden voltooien {#complete-upload}

Nadat alle delen van een binair dossier worden geupload, leg een verzoek van de POST van HTTP aan volledige URI voor die door de initiatiegegevens wordt verstrekt. Het inhoudstype van de aanvraaginstantie moet `application/x-www-form-urlencoded` formuliergegevens, die de volgende velden bevatten.

| Fields | Type | Vereist of niet | Beschrijving |
|---|---|---|---|
| `fileName` | Tekenreeks | Vereist | De naam van het element, zoals deze werd verstrekt in de inleidingsgegevens. |
| `mimeType` | Tekenreeks | Vereist | Het HTTP-inhoudstype van het binaire getal, zoals is opgegeven door de initiatiegegevens. |
| `uploadToken` | Tekenreeks | Vereist | Upload token voor het binaire bestand, zoals werd opgegeven in de initiatiegegevens. |
| `createVersion` | Boolean | Optioneel | Indien `True` en er een element met de opgegeven naam bestaat, dan [!DNL Experience Manager] maakt een nieuwe versie van het element. |
| `versionLabel` | Tekenreeks | Optioneel | Als er een nieuwe versie wordt gemaakt, wordt het label gekoppeld aan de nieuwe versie van een element. |
| `versionComment` | Tekenreeks | Optioneel | Als er een nieuwe versie wordt gemaakt, worden de opmerkingen gekoppeld aan de versie. |
| `replace` | Boolean | Optioneel | Indien `True` en er een element met de opgegeven naam bestaat, [!DNL Experience Manager] Hiermee verwijdert u het element en maakt u het opnieuw. |

>[!NOTE]
Als het element bestaat en beide `createVersion` noch `replace` wordt opgegeven, dan [!DNL Experience Manager] werkt de huidige versie van het element met het nieuwe binaire getal bij.

Net als bij het initiëringsproces kunnen de volledige aanvraaggegevens informatie voor meer dan één bestand bevatten.

Het uploaden van een binair getal gebeurt pas wanneer de volledige URL voor het bestand wordt aangeroepen. Een element wordt verwerkt nadat het uploadproces is voltooid. De verwerking wordt niet gestart, zelfs niet als het binaire bestand van het element volledig is geüpload maar het uploadproces niet is voltooid. Als het uploaden is voltooid, reageert de server met een `200` statuscode.

### Uploadbibliotheek met open bron {#open-source-upload-library}

Adobe biedt opensource-bibliotheken en -gereedschappen voor meer informatie over de uploadalgoritmen of om uw eigen uploadscripts en -gereedschappen te maken:

* [Opensource-em-upload-bibliotheek](https://github.com/adobe/aem-upload).
* [Opensource opdrachtregelprogramma](https://github.com/adobe/aio-cli-plugin-aem).

### Verouderde API&#39;s voor middelenupload {#deprecated-asset-upload-api}

<!-- #ENGCHECK review / update the list of deprecated APIs below. -->

De nieuwe uploadmethode wordt alleen ondersteund voor [!DNL Adobe Experience Manager] als [!DNL Cloud Service]. De API&#39;s van [!DNL Adobe Experience Manager] 6.5 zijn afgekeurd. De methoden voor het uploaden of bijwerken van elementen of uitvoeringen (elke binaire upload) zijn afgekeurd in de volgende API&#39;s:

* [Experience Manager Assets HTTP API](mac-api-assets.md)
* `AssetManager` Java API, zoals `AssetManager.createAsset(..)`

>[!MORELIKETHIS]
* [Opensource-em-upload-bibliotheek](https://github.com/adobe/aem-upload).
* [Opensource opdrachtregelprogramma](https://github.com/adobe/aio-cli-plugin-aem).
* [Apache Jackrabbit Oak-documentatie voor direct uploaden](https://jackrabbit.apache.org/oak/docs/features/direct-binary-access.html#Upload).


## Workflows voor de verwerking en naverwerking van bedrijfsmiddelen {#post-processing-workflows}

In [!DNL Experience Manager]is de verwerking van de activa gebaseerd op **[!UICONTROL Processing Profiles]** configuratie die gebruikt [assetmicroservices](asset-microservices-configure-and-use.md#get-started-using-asset-microservices). Voor verwerking zijn geen ontwikkelaarsextensies vereist.

Voor workflowconfiguratie na verwerking gebruikt u de standaardworkflows met extensies met aangepaste stappen.

## Ondersteuning van workflowstappen in de naverwerkingsworkflow {#post-processing-workflows-steps}

Als u een upgrade uitvoert van een vorige versie van [!DNL Experience Manager], kunt u met behulp van asset-microservices elementen verwerken. De &#39;cloud-native asset microservices&#39; zijn eenvoudiger te configureren en gebruiken. Enkele workflowstappen die in het dialoogvenster [!UICONTROL DAM Update Asset] in de vorige versie wordt niet ondersteund. Zie voor meer informatie over ondersteunde klassen de klasse [Java API-referentie of JavaDocs](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/index.html).

De volgende technische workflowmodellen worden vervangen door asset microservices of de ondersteuning is niet beschikbaar:

* `com.day.cq.dam.cameraraw.process.CameraRawHandlingProcess`
* `com.day.cq.dam.core.process.CommandLineProcess`
* `com.day.cq.dam.pdfrasterizer.process.PdfRasterizerHandlingProcess`
* `com.day.cq.dam.core.process.AddPropertyWorkflowProcess`
* `com.day.cq.dam.core.process.CreateSubAssetsProcess`
* `com.day.cq.dam.core.process.DownloadAssetProcess`
* `com.day.cq.dam.word.process.ExtractImagesProcess`
* `com.day.cq.dam.word.process.ExtractPlainProcess`
* `com.day.cq.dam.ids.impl.process.IDSJobProcess`
* `com.day.cq.dam.indd.process.INDDMediaExtractProcess`
* `com.day.cq.dam.indd.process.INDDPageExtractProcess`
* `com.day.cq.dam.core.impl.lightbox.LightboxUpdateAssetProcess`
* `com.day.cq.dam.pim.impl.sourcing.upload.process.ProductAssetsUploadProcess`
* `com.day.cq.dam.core.process.SendDownloadAssetEmailProcess`
* `com.day.cq.dam.similaritysearch.internal.workflow.smarttags.StartTrainingProcess`
* `com.day.cq.dam.similaritysearch.internal.workflow.smarttags.TransferTrainingDataProcess`
* `com.day.cq.dam.switchengine.process.SwitchEngineHandlingProcess`
* `com.day.cq.dam.core.process.GateKeeperProcess`
* `com.day.cq.dam.s7dam.common.process.DMEncodeVideoWorkflowCompletedProcess`
* `com.day.cq.dam.core.process.DeleteImagePreviewProcess`
* `com.day.cq.dam.video.FFMpegTranscodeProcess`
* `com.day.cq.dam.core.process.ThumbnailProcess`
* `com.day.cq.dam.video.FFMpegThumbnailProcess`
* `com.day.cq.dam.core.process.CreateWebEnabledImageProcess`
* `com.day.cq.dam.core.process.CreatePdfPreviewProcess`
* `com.day.cq.dam.s7dam.common.process.VideoUserUploadedThumbnailProcess`
* `com.day.cq.dam.s7dam.common.process.VideoThumbnailDownloadProcess`
* `com.day.cq.dam.s7dam.common.process.VideoProxyServiceProcess`
* `com.day.cq.dam.scene7.impl.process.Scene7UploadProcess`
* `com.day.cq.dam.s7dam.common.process.S7VideoThumbnailProcess`
* `com.day.cq.dam.core.process.MetadataProcessorProcess`
* `com.day.cq.dam.core.process.AssetOffloadingProcess`
* `com.adobe.cq.dam.dm.process.workflow.DMImageProcess`

<!-- Commenting the previous list documented at the time of GA. Replacing it with the updated list via cqdoc-18231.

* `com.day.cq.dam.core.process.DeleteImagePreviewProcess`
* `com.day.cq.dam.s7dam.common.process.DMEncodeVideoWorkflowCompletedProcess`
* `com.day.cq.dam.core.process.GateKeeperProcess`
* `com.day.cq.dam.core.process.AssetOffloadingProcess`
* `com.day.cq.dam.core.process.MetadataProcessorProcess`
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
-->

<!-- PPTX source: slide in add-assets.md - overview of direct binary upload section of
https://adobe-my.sharepoint.com/personal/gklebus_adobe_com/_layouts/15/guestaccess.aspx?guestaccesstoken=jexDC5ZnepXSt6dTPciH66TzckS1BPEfdaZuSgHugL8%3D&docid=2_1ec37f0bd4cc74354b4f481cd420e07fc&rev=1&e=CdgElS
-->

>[!MORELIKETHIS]
* [[!DNL Experience Cloud] as a [!DNL Cloud Service] SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md).

