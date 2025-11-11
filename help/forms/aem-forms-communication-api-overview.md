---
title: AEM Forms Communications API's - Overzicht
description: Overzicht van AEM Forms Communications API's, inclusief verificatiemethoden en volledige API-referentie
role: Developer, User
feature: Adaptive Forms, APIs & Integrations
hide: true
hidefromtoc: true
index: false
source-git-commit: fcc25eb44b485db69ec1c267f4cf8774c4279b24
workflow-type: tm+mt
source-wordcount: '899'
ht-degree: 0%

---


# AEM Forms Communications API&#39;s - Overzicht

AEM Forms Communications API&#39;s bieden een uitgebreide suite van in de cloud geïntegreerde API&#39;s die zijn ontworpen om bedrijven te helpen bij het automatiseren van documentworkflows.

AEM Forms API&#39;s zijn gestructureerd en toegankelijk via twee primaire consoles:

* [ Adobe Developer Console (ADC) ](https://developer.adobe.com/developer-console/) - Adobe Developer Console is de gateway aan Adobe APIs, Gebeurtenissen, Runtime en App Builder.

* [ AEM Developer Console ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console) - AEM Developer Console verstrekt hulpmiddelen om milieu&#39;s van AEM as a Cloud Service te zuiveren en te inspecteren.

Elke console biedt toegang tot verschillende API&#39;s en services voor documentverwerking, genereren, converteren, coderen en communicatietaken. APIs steunt verschillende [ authentificatiemethodes ](#authentication-methods).

## Verificatiemethoden

API&#39;s ondersteunen meerdere verificatiemethoden voor een veilige integratie tussen uw toepassingen en Adobe-services:

| Verhouding | OAuth Server-aan-Server (geadviseerd) | JWT (JSON Web Token) |
|-------------|------------------------------------------|---------------------------|
| Beschrijving | Moderne en veilige methode voor API-toegang zonder gebruikersinteractie. | Oudere methode die ondertekende tokens voor toegang gebruikt. |
| Locatie instellen | Adobe Developer Console en AEM Developer Console | Alleen AEM Developer Console |
| Beveiliging | High - gebruikt clientreferenties en -bereik | Matig - hangt van zeer belangrijk beheer af |
| Schaalbaarheid | Zeer schaalbaar voor back-endintegratie | Beperkt, geschikt voor verouderd gebruik |
| Tokenbeheer | Automatisch genereren en vernieuwen | Handmatig ondertekenen en roteren van token |
| Status | Aanbevolen | Vervangen |


>[!NOTE]
>
> Klik op de onderstaande koppelingen voor meer informatie over :-
> 
> * [ OAuth server-aan-Server (Geadviseerd) ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation)
> * [ JWT (Token van het Web JSON) ](https://developer.adobe.com/developer-console/docs/guides/authentication/JWT/)

<!--### Execution Models

The following table highlights the key differences between Synchronous (On-Demand) and Asynchronous (Batch) execution models supported in AEM Forms Communications APIs:

| Feature | Synchronous (On-Demand) | Batch (Asynchronous) |
|---------|-------------------------|----------------------|
| **Execution Model** | Real-time, immediate | Queued, scheduled |
| **Response Time** | Seconds | Minutes to hours |
| **Volume** | Single or few documents | Hundreds to thousands |
| **Testing Environment** | Author & Publish | Author Only |
| **Use Case** | User-triggered actions | Scheduled bulk operations |
| **Console Access** | ADC & AEM Developer Console | AEM Developer Console Only |-->

## API-classificatieoverzicht

Alle AEM Forms API&#39;s zijn verdeeld in twee hoofdonderdelen:

* [ Aangepaste Levering van de Vorm &amp; Runtime APIs ](https://developer-stage.adobe.com/experience-cloud/experience-manager-apis/api/stable/forms/)

* [AEM Forms Communication-API&#39;s](#aem-forms-communications-apis)

| Details | API&#39;s voor adaptieve levering en uitvoering van formulieren | Communicatie-API&#39;s |
|--------------|----------------------------|--------------------------|
| Doel | Aangepaste levering van formulieren en runtimebewerkingen verwerken | Documentgeneratie en -manipulatie |
| Gevallen gebruiken | - Formulierweergave <br> - Vooraf ingevulde gegevens <br> - Formulierverzendingen <br> - Conceptbeheer | - PDF genereren <br> - Document samenvoegen <br> - Batchverwerking <br> - Afdrukbewerkingen |
| Autorisatiemethode | Ondersteunt de verificatiemethoden van beide servers. | Ondersteunt alleen OAuth Server-to-Server verificatie. |

### AEM Forms Communications API&#39;s

Communicatie-API&#39;s vormen de belangrijkste focus voor documentgerichte bewerkingen.

De lijst hieronder maakt een lijst van alle [ Communicatie APIs van AEM Forms ](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/) samen met hun gesteunde authentificatiemethodes en uitvoeringsmodellen:

#### API&#39;s voor het genereren van documenten

| API-eindpunt | Uitvoeringsmodel | Verificatiemethode |
| ------------------ | ---------------- | --------------------------- |
| [ /adobe/forms/batch/output/config ](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-batch/#tag/Batch-Configuration/operation/CreateBatchConfig) | Asynchroon/Batch | [ OAuth Server aan Server ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation)/[ JWT ](https://developer.adobe.com/developer-console/docs/guides/authentication/JWT/) |
| [ /adobe/forms/batch/output/config/{configName} ](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-batch/#tag/Batch-Configuration/operation/GetBatchConfigbyName) | Asynchroon/Batch | [ OAuth Server aan Server ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation)/[ JWT ](https://developer.adobe.com/developer-console/docs/guides/authentication/JWT/) |
| [ /adobe/forms/batch/output/config/configs ](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-batch/#tag/Batch-Configuration/operation/GetAllBatchConfigs) | Asynchroon/Batch | [ OAuth Server aan Server ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation)/[ JWT ](https://developer.adobe.com/developer-console/docs/guides/authentication/JWT/) |
| [ /adobe/forms/batch/output/config/{configName}/executing](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-batch/#tag/Batch-Execution/operation/StartBatchRun) | Asynchroon/Batch | [ OAuth Server aan Server ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation)/[ JWT ](https://developer.adobe.com/developer-console/docs/guides/authentication/JWT/) |
| [ /adobe/forms/batch/output/config/{configName} /executing/{executionId} ](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-batch/#tag/Batch-Execution/operation/GetBatchRunInstanceState) | Asynchroon/Batch | [ OAuth Server aan Server ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation)/[ JWT ](https://developer.adobe.com/developer-console/docs/guides/authentication/JWT/) |
| [ /adobe/forms/batch/output/config/{configName} /Executions](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-batch/#tag/Batch-Execution/operation/GetAllRunningInstancesForBatch) | Asynchroon/Batch | [ OAuth Server aan Server ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation)/[ JWT ](https://developer.adobe.com/developer-console/docs/guides/authentication/JWT/) |
| [ /adobe/forms/doc/v1/generatePDFOutput ](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-sync/#tag/Communications-Services/paths/~1adobe~1forms~1doc~1v1~1generatePDFOutput/post) | Synchroon | [ OAuth Server aan Server ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation)/[ JWT ](https://developer.adobe.com/developer-console/docs/guides/authentication/JWT/) |
| [ /adobe/forms/doc/v1/generatePrintedOutput ](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-sync/#tag/Batch-Execution/operation/GetAllRunningInstancesForBatch) | Synchroon | [ OAuth Server aan Server ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation)/[ JWT ](https://developer.adobe.com/developer-console/docs/guides/authentication/JWT/) |
| [ /adobe/forms/doc/v1/generate/afp ](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-sync/#tag/Communications-Services/paths/~1adobe~1forms~1doc~1v1~1generate~1afp/post) | Synchroon | [ OAuth Server aan Server ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation)/[ JWT ](https://developer.adobe.com/developer-console/docs/guides/authentication/JWT/) |
| [ /adobe/document/generate/pdfform ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/renderPDFForm) | Synchroon | [ Server OAuth aan Server ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation) |
| [ /adobe/document/generate/pdfform/jobs/{id} /status](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/renderPDFFormJobStatus) | Synchroon | [ Server OAuth aan Server ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation) |
| [ /adobe/document/generate/pdfform/jobs/{id} /result ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/renderPDFFormJobResult) | Synchroon | [ Server OAuth aan Server ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation) |


#### Documentmanipulatie-API&#39;s

| API-eindpunt | Uitvoeringsmodel | Verificatiemethode |
| ------------------ | ---------------- | --------------------------- |
| [ /adobe/forms/assembler/ddx/invoke ](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/assembler-sync/#tag/DDX-execution/operation/InvokeDDX) | Synchroon | [ OAuth Server aan Server ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation)/[ JWT ](https://developer.adobe.com/developer-console/docs/guides/authentication/JWT/) |
| [ /adobe/forms/assembler/pdfa/convert](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/assembler-sync/#tag/Document-conversion/operation/ConvertToPDFA) | Synchroon | [ OAuth Server aan Server ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation)/[ JWT ](https://developer.adobe.com/developer-console/docs/guides/authentication/JWT/) |
| [ /adobe/forms/assembler/pdfa/validate ](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/assembler-sync/#tag/Document-validation/operation/CheckIsPDFA) | Synchroon | [ OAuth Server aan Server ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation)/[ JWT ](https://developer.adobe.com/developer-console/docs/guides/authentication/JWT/) |

#### Documentconversie-API&#39;s

| API-eindpunt | Uitvoeringsmodel | Verificatiemethode |
|----------------|---------|----------------------|
| [ /adobe/document/convert/pdftoxdp ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Conversion/paths/~1convert~1pdftoxdp/post) | Synchroon | [ Server OAuth aan Server ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation) |

#### Extractie-API&#39;s voor documenten

| API-eindpunt | Uitvoeringsmodel | Verificatiemethode |
|----------------|---------|----------------------|
| [ /adobe/forms/doc/v1/extract/pdfproperties ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Extraction/paths/~1extract~1pdfproperties/post) | Synchroon | [ Server OAuth aan Server ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation) |
| [ /adobe/forms/doc/v1/extract/usagerights ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/extractUsageRights) | Synchroon | [ Server OAuth aan Server ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation) |
| [ /adobe/forms/doc/v1/extract/metadata ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Extraction/paths/~1extract~1metadata/post) | Synchroon | [ Server OAuth aan Server ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation) |
| [ /adobe/forms/doc/v1/extract/data ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/exportData) | Synchroon | [ Server OAuth aan Server ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation) |
| [ /adobe/document/extract/security](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Extraction/paths/~1extract~1security/post) | Synchroon | [ Server OAuth aan Server ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation) |

#### API&#39;s voor documenttransformatie


| API-eindpunt | Uitvoeringsmodel | Verificatiemethode |
|----------------|---------|----------------------|
| [ /adobe/document/transform/metadata ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Transformation/paths/~1transform~1metadata/post) | Synchroon | [ Server OAuth aan Server ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation) |
| [ /adobe/document/field/signature/add](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Transformation/paths/~1field~1signature~1add/post) | Synchroon | [ Server OAuth aan Server ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation) |
| [ /adobe/document/field/signature/clear ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Transformation/paths/~1field~1signature~1clear/post) | Synchroon | [ Server OAuth aan Server ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation) |
| [ /adobe/document/field/signature/remove](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Transformation/paths/~1field~1signature~1remove/post) | Synchroon | [ Server OAuth aan Server ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation) |

#### Document Assurance API&#39;s

| API-eindpunt | Uitvoeringsmodel | Verificatiemethode |
|----------------|---------|----------------------|
| [ /adobe/document/sure/usagerights ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/applyUsageRights) | Synchroon | [ Server OAuth aan Server ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation) |
| [ /adobe/document/confirm/encrypt ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Assurance/paths/~1assure~1encrypt/post) | Synchroon | [ Server OAuth aan Server ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation) |
| [ /adobe/document/sure/decrypt ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Assurance/paths/~1assure~1decrypt/post) | Synchroon | [ Server OAuth aan Server ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation) |
| [ /adobe/document/confirm/sign](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Assurance/paths/~1assure~1sign/post) | Synchroon | [ Server OAuth aan Server ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation) |
| [ /adobe/document/confirm/certify](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Assurance/paths/~1assure~1certify/post) | Synchroon | [ Server OAuth aan Server ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation) |


## Volgende stappen

Leer hoe u een omgeving instelt voor synchrone (On-Demand) en asynchrone (Batch) Forms Communications API&#39;s:

<!-- START CARDS HTML - DO NOT MODIFY BY HAND -->
<div class="columns">
    <!-- Synchronous APIs Card -->
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="AEM Forms Communications APIs - Synchronous">
        <div class="card" style="height: 100%; display: flex; flex-direction: column;">
            <div class="card-image">
                <figure class="image x-is-16by9">
                    <a href="/help/forms/aem-forms-cloud-service-communications-on-demand-processing.md" title="Synchrone API&apos;s" target="_self" rel="referrer">
                        <img class="is-bordered-r-small" src="/help/forms/assets/sync-api.png" alt="Synchrone API&apos;s"
                             style="width: 100%; aspect-ratio: 16 / 9; object-fit: cover; overflow: hidden; display: block; margin: auto;">
                    </a>
                </figure>
            </div>
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">
                        <a href="/help/forms/aem-forms-cloud-service-communications-on-demand-processing.md" target="_self" rel="referrer" title="AEM Forms Communications API&apos;s - synchroon"> Communicatie APIs van AEM Forms - Synchroon </a>
                    </p>
                    <p class="is-size-6">Leer hoe u een omgeving instelt voor synchrone (on-demand) communicatie-API's die direct documenten genereren of verwerken. </p>
                </div>
                <a href="/help/forms/aem-forms-cloud-service-communications-on-demand-processing.md" target="_self" rel="referrer" class="spectrum-Button spectrum-Button--outline spectrum-Button--primary spectrum-Button--sizeM" style="align-self: flex-start; margin-top: 1rem;">
                    <span class="spectrum-Button-label has-no-wrap has-text-weight-bold"> Leer meer </span>
                </a>
            </div>
        </div>
    </div>
    <!-- Asynchronous APIs Card -->
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="AEM Forms Communications APIs - Asynchronous">
        <div class="card" style="height: 100%; display: flex; flex-direction: column;">
            <div class="card-image">
                <figure class="image x-is-16by9">
                    <a href="/help/forms/aem-forms-cloud-service-communications-batch-processing.md" title="AEM Forms Communications API&apos;s - Asynchroon" target="_self" rel="referrer">
                        <img class="is-bordered-r-small" src="/help/forms/assets/async-api.png" alt="Asynchrone API&apos;s"
                             style="width: 100%; aspect-ratio: 16 / 9; object-fit: cover; overflow: hidden; display: block; margin: auto;">
                    </a>
                </figure>
            </div>
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">
                        <a href="/help/forms/aem-forms-cloud-service-communications-batch-processing.md" target="_self" rel="referrer" title="Asynchrone API&apos;s"> Communicatie APIs van AEM Forms - Asynchroon (Partij) </a>
                    </p>
                    <p class="is-size-6">Leer hoe u een omgeving instelt voor Asynchronous (Batch) Forms Communications API's die meerdere documenten op een geplande manier genereren of verwerken.</p>
                </div>
                <a href="/help/forms/aem-forms-cloud-service-communications-batch-processing.md" target="_self" rel="referrer" class="spectrum-Button spectrum-Button--outline spectrum-Button--primary spectrum-Button--sizeM" style="align-self: flex-start; margin-top: 1rem;">
                    <span class="spectrum-Button-label has-no-wrap has-text-weight-bold"> Leer meer </span>
                </a>
            </div>
        </div>
    </div>
</div>
<!-- END CARDS HTML - DO NOT MODIFY BY HAND -->


>[!MORELIKETHIS]
>
>* [ Inleiding aan de Mededelingen van AEM Forms as a Cloud Service ](/help/forms/aem-forms-cloud-service-communications-introduction.md)
>* [ de Architectuur van as a Cloud Service van AEM Forms voor Adaptieve Forms en Communicatie APIs ](/help/forms/aem-forms-cloud-service-architecture.md)
>* [ Communicatie Verwerking - Synchrone APIs ](/help/forms/aem-forms-cloud-service-communications.md)
>* [ Communicatie Verwerking - Partij APIs ](/help/forms/aem-forms-cloud-service-communications-batch-processing.md)
>* [ Communicatie Verwerking - Op bestelling APIs ](/help/forms/aem-forms-cloud-service-communications-on-demand-processing.md)