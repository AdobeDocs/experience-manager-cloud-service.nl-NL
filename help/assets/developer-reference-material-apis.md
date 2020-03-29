---
title: 'Middelen-API''s voor beheer van digitale middelen in Adobe Experience Manager als Cloud Service '
description: Elementen-API's maken het mogelijk om standaard CRUD-bewerkingen (create-read-update-delete) uit te voeren voor het beheer van elementen, waaronder binaire elementen, metagegevens, uitvoeringen, opmerkingen en inhoudsfragmenten.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 68b2214a4c8941365120bdef670e89b4c9058966

---


# Assets as a Cloud Service APIs {#assets-cloud-service-apis}

<!-- 
Give a list of and overview of all reference information available.
* New upload method
* Javadocs
* Assets HTTP API documented at [https://helpx.adobe.com/experience-manager/6-5/assets/using/mac-api-assets.html](https://helpx.adobe.com/experience-manager/6-5/assets/using/mac-api-assets.html)

-->

## Elementen uploaden {#asset-upload-technical}

Experience Manager als cloudservice biedt een nieuwe manier om elementen naar de opslagplaats te uploaden: directe binaire upload naar binaire cloudopslag. Dit gedeelte geeft een technisch overzicht.

### Overzicht van directe binaire upload {#overview-binary-upload}

Het algoritme op hoog niveau om een binair getal te uploaden is:

1. Verzend een HTTP-aanvraag om AEM te informeren over de intentie om een nieuw binair getal te uploaden.
1. POST de inhoud van binair binair aan één of meerdere URIs die door het openingsverzoek wordt verstrekt.
1. Verzend een HTTP- verzoek om de server mee te delen dat de inhoud van binair getal met succes werd geupload.

![Overzicht van het directe binaire upload protocol](assets/add-assets-technical.png)

Belangrijke verschillen in vergelijking met eerdere versies van AEM zijn:

* De binaire getallen gaan niet door AEM, die nu eenvoudig het uploadproces met de binaire wolkenopslag coördineert die voor de plaatsing wordt gevormd
* Binaire cloudopslag wordt voorafgegaan door een Content Delivery Network (CDN, Edge Network), dat het uploadeindpunt dichter bij de client brengt, waardoor uploadprestaties en gebruikerservaring worden verbeterd, met name voor gedistribueerde teams die middelen uploaden

Deze aanpak moet zorgen voor een schaalbaardere en krachtigere verwerking van geüploade bedrijfsmiddelen.

> !![NOTE]
Als u de clientcode wilt bekijken die deze aanpak implementeert, raadpleegt u de open-source [aem-upload bibliotheek](https://github.com/adobe/aem-upload)

### Uploaden starten {#initiate-upload}

De eerste stap bestaat uit het indienen van een HTTP POST-aanvraag bij de map waarin het element moet worden gemaakt of bijgewerkt. Neem de kiezer op `.initiateUpload.json` om aan te geven dat de aanvraag moet beginnen met een binaire upload. Het pad naar de map waar het element moet worden gemaakt is bijvoorbeeld `/assets/folder`:

```
POST https://[aem_server]/content/dam/assets/folder.initiateUpload.json
````

Het inhoudstype van de aanvraaginstantie moet formuliergegevens zijn, die de volgende velden bevatten: `application/x-www-form-urlencoded`

* `(string) fileName`: Vereist. De naam van het element zoals het in de instantie wordt weergegeven.
* `(number) fileSize`: Vereist. De totale lengte, in bytes, van het binaire getal dat moet worden geüpload.

Eén aanvraag kan worden gebruikt om uploads voor meerdere binaire bestanden te starten, zolang elk binair getal de vereiste velden bevat. Als dit lukt, reageert de aanvraag met een `201` statuscode en een body die JSON-gegevens in de volgende indeling bevat:

```
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

* `completeURI` (tekenreeks): Roep deze URI aan wanneer het binaire bestand is geüpload. De URI kan een absolute of relatieve URI zijn en clients moeten beide kunnen afhandelen. De waarde kan dus zijn `"https://author.acme.com/content/dam.completeUpload.json"` of `"/content/dam.completeUpload.json"` Zie het [uploaden](#complete-upload)voltooien.
* `folderPath` (tekenreeks): Volledig pad naar de map waar het binaire bestand wordt geüpload.
* `(files)` (array): Een lijst van elementen waarvan lengte en orde de lengte en de orde van de lijst van binaire informatie zal aanpassen die in de in werking stelt verzoek wordt verstrekt.
* `fileName` (tekenreeks): De naam van het overeenkomstige binaire getal, zoals opgegeven in het initiërende verzoek. Deze waarde moet in het volledige verzoek worden opgenomen.
* `mimeType` (tekenreeks): Het mime type van het overeenkomstige binaire getal, zoals die in binnen wordt verstrekt stelt verzoek in werking. Deze waarde moet in het volledige verzoek worden opgenomen.
* `uploadToken` (tekenreeks): Een upload token voor het overeenkomstige binaire getal. Deze waarde moet in het volledige verzoek worden opgenomen.
* `uploadURIs` (array): Een lijst met tekenreeksen waarvan de waarden volledige URI&#39;s zijn waarnaar de inhoud van het binaire bestand moet worden geüpload (zie binair [](#upload-binary)uploaden).
* `minPartSize` (nummer): De minimale lengte, in bytes, van gegevens die aan om het even welke uploadURIs kunnen worden verstrekt, als er meer dan één URI is.
* `maxPartSize` (nummer): De maximumlengte, in bytes, van gegevens die aan om het even welke uploadURIs kunnen worden verstrekt, als er meer dan één URI is.

### Binair bestand uploaden {#upload-binary}

De uitvoer van het starten van een upload bevat een of meer URI-waarden voor uploaden. Als meer dan één URI wordt verstrekt, is het de verantwoordelijkheid van de cliënt om het binaire getal in delen en POST elk deel, in orde, aan elk URI te &quot;verdelen&quot;, in orde. Alle URI&#39;s moeten worden gebruikt en elk onderdeel moet groter zijn dan de minimale grootte en kleiner dan de maximale grootte die is opgegeven in het initiëringsantwoord. Die verzoeken zullen door CDN randknopen worden genegeerd om het uploaden van binaire getallen te versnellen.

Dit kan onder andere worden bereikt door de grootte van de onderdelen te berekenen op basis van het aantal URI&#39;s voor uploaden dat door de API wordt verschaft. Voorbeeld dat de totale grootte van het binaire getal 20.000 bytes is en het aantal URI&#39;s voor uploaden 2 is:

* Onderdeelgrootte berekenen door totale grootte te delen door aantal URI&#39;s: 20,000 / 2 = 10,000
* POST bytewaaier 0-9.999 van binair aan eerste URI in de lijst van upload URIs
* POST bytewaaier 10.000-19.999 van binair aan tweede URI in de lijst van upload URIs

Als dit gelukt is, reageert de server op elke aanvraag met een `201` statuscode.

### Uploaden voltooien {#complete-upload}

Wanneer alle delen van een binair getal zijn geüpload, bestaat de laatste stap uit het verzenden van een HTTP POST-aanvraag naar de volledige URI die door de initiatiegegevens wordt verschaft. Het inhoudstype van de aanvraaginstantie moet toepassings-/`x-www-form-urlencoded` formuliergegevens zijn, die de volgende velden bevatten:

* `(string) fileName`: Vereist. De naam van het element, zoals deze werd verstrekt in de inleidingsgegevens.
* `(string) mimeType`: Vereist. Het HTTP-inhoudstype van het binaire getal, zoals is opgegeven door de initiatiegegevens.
* `(string) uploadToken`: Vereist. Upload token voor het binaire bestand, zoals werd opgegeven in de initiatiegegevens.
* `(bool) createVersion`: Optioneel. Als de waarde true is en er al een element met de opgegeven naam bestaat, maakt de instantie een nieuwe versie van het element.
* `(string) versionLabel`: Optioneel. Als er een nieuwe versie wordt gemaakt, het label dat aan de versie wordt gekoppeld.
* `(string) versionComment`: Optioneel. Als er een nieuwe versie wordt gemaakt, worden opmerkingen toegevoegd die aan de versie worden gekoppeld.
* `(bool) replace`: Optioneel: Als true en een element met de opgegeven naam al bestaat, verwijdert de instantie het element en maakt deze opnieuw.

>!![NOTE]
>
> Als het element al bestaat en createVersion noch replace is opgegeven, werkt de instantie de huidige versie van het element bij met het nieuwe binaire getal.

Net als bij het initiëringsproces kunnen de volledige aanvraaggegevens informatie voor meer dan één bestand bevatten.

Het uploaden van een binair getal gebeurt pas wanneer de volledige URL voor het bestand wordt aangeroepen. Zelfs als het binaire bestand van een bestand volledig is geüpload, wordt het element pas door de instantie verwerkt nadat het uploadproces is voltooid.

Als dit gelukt is, reageert de server met een `200` statuscode.

### Uploadbibliotheek met open bron {#open-source-upload-library}

Voor meer informatie over de uploadalgoritmen of om uw eigen uploadscripts en -gereedschappen te maken, biedt Adobe opensource-bibliotheken en -gereedschappen als uitgangspunt:

* [Bibliotheek voor het uploaden van bronbestanden openen](https://github.com/adobe/aem-upload)
* [Opdrachtregelgereedschap van bron openen](https://github.com/adobe/aio-cli-plugin-aem)

### Verouderde API&#39;s voor middelenupload {#deprecated-asset-upload-api}

<!-- #ENGCHECK review / update the list of deprecated APIs below -->

>[!NOTE]
Voor Experience Manager als Cloud Service worden alleen de nieuwe upload-API&#39;s ondersteund. API&#39;s van Experience Manager 6.5 zijn afgekeurd.

Methoden die betrekking hebben op het uploaden of bijwerken van elementen of uitvoeringen (elke binaire upload) zijn afgekeurd in de volgende API&#39;s:

* [AEM Assets HTTP API](mac-api-assets.md)
* `AssetManager` Java API, zoals `AssetManager.createAsset(..)`

>[!MORELIKETHIS]
* [Bibliotheek voor het uploaden van bronbestanden openen](https://github.com/adobe/aem-upload)
* [Opdrachtregelgereedschap van bron openen](https://github.com/adobe/aio-cli-plugin-aem)


## Workflows voor de verwerking en naverwerking van bedrijfsmiddelen {#post-processing-workflows}

De meeste verwerking van bedrijfsmiddelen wordt uitgevoerd op basis van de configuratie van **[!UICONTROL verwerkingsprofielen]** door [asset microservices](asset-microservices-configure-and-use.md#get-started-using-asset-microservices)en vereist geen ontwikkelaarsextensies.

Voor de configuratie van de workflow na verwerking, standaard AEM Workflows met extensies (aangepaste stappen kunnen bijvoorbeeld worden gebruikt). Lees de volgende subsectie om te begrijpen welke workflowstappen kunnen worden gebruikt in de workflows voor het naverwerken van bedrijfsmiddelen.

### Workflowstappen in de workflow na verwerking {#post-processing-workflows-steps}

>[!NOTE]
Deze sectie is vooral van toepassing op klanten die als Cloud Service van vorige versies van AEM bijwerken aan AEM.

Vanwege een nieuw implementatiemodel dat is geïntroduceerd met Experience Manager als Cloud Service, worden bepaalde workflowstappen die vóór de introductie van asset microservices in de `DAM Update Asset` workflow zijn gebruikt, mogelijk niet meer ondersteund voor workflows na verwerking. Merk op dat de meeste van hen door een veel eenvoudiger worden vervangen om activa microdiensten te vormen en te gebruiken.

Hier volgt een lijst met technische workflowmodellen en hun supportniveau in AEM als cloudservice:

### Ondersteunde workflowstappen {#supported-workflow-steps}

De volgende workflowstappen worden ondersteund in de Cloud Service.

* `com.day.cq.dam.similaritysearch.internal.workflow.process.AutoTagAssetProcess`
* `com.day.cq.dam.core.impl.process.CreateAssetLanguageCopyProcess`
* `com.day.cq.wcm.workflow.process.CreateVersionProcess`
* `com.day.cq.dam.similaritysearch.internal.workflow.smarttags.StartTrainingProcess`
* `com.day.cq.dam.similaritysearch.internal.workflow.smarttags.TransferTrainingDataProcess`
* `com.day.cq.dam.core.impl.process.TranslateAssetLanguageCopyProcess`
* `com.day.cq.dam.core.impl.process.UpdateAssetLanguageCopyProcess`
* `com.adobe.cq.workflow.replication.impl.ReplicationWorkflowProcess`
* `com.day.cq.dam.core.impl.process.DamUpdateAssetWorkflowCompletedProcess`

### Niet-ondersteunde of vervangen modellen {#unsupported-replaced-models}

De volgende technische workflowmodellen worden vervangen door asset microservices of de ondersteuning is niet beschikbaar.

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
