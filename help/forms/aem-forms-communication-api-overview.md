---
title: AEM Forms Communications API's - Overzicht
description: Overzicht van AEM Forms Communications API's, inclusief verificatiemethoden en volledige API-referentie
role: Developer, User
feature: Adaptive Forms, APIs & Integrations
hide: true
hidefromtoc: true
index: false
source-git-commit: e2f57a32fcc098a2331ad74540a3d48832c2b3c3
workflow-type: tm+mt
source-wordcount: '965'
ht-degree: 0%

---


# AEM Forms API&#39;s - Overzicht

AEM Forms API&#39;s bieden een uitgebreid pakket van in de cloud geïntegreerde API&#39;s die zijn ontworpen om bedrijven te helpen bij het automatiseren van documentworkflows.

AEM Forms API&#39;s zijn gestructureerd en toegankelijk via twee primaire consoles:

* [ Adobe Developer Console (ADC) ](https://developer.adobe.com/developer-console/) - Adobe Developer Console is de gateway aan Adobe APIs, Gebeurtenissen, Runtime en App Builder.

* [ AEM Developer Console ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console) - AEM Developer Console verleent toegang tot milieu-vlakke details, configuraties, technische rekeningen, en de dienstgeloofsbrieven om operationele en integratietaken te steunen.

Verschillende APIs steunt verschillende [ authentificatiemethodes ](#authentication-methods).

## Verificatiemethoden

Verschillende Forms API&#39;s gebruiken verschillende verificatiemethoden op basis van hun releasetijdlijn:

* [OAuth Server-to-Server](/help/forms/oauth-api-authetication.md)
* [ JWT (het Token van het Web JSON) server-aan-Server ](/help/forms/jwt-api-authentication.md)

Eerdere API&#39;s ondersteunen JWT-gebaseerde server-to-server verificatie, die wordt geconfigureerd en beheerd via de AEM Developer Console. Nieuwere API&#39;s maken gebruik van OAuth Server-to-Server-verificatie en worden geconfigureerd via de Adobe Developer Console.

>[!NOTE]
>
> Adobe is bezig met het standaardiseren van verificatiemethoden voor alle API&#39;s en neemt geleidelijk API&#39;s aan bij de Adobe Developer Console, die de OAuth Server-to-Server verificatiemethode ondersteunt.

## API-classificatieoverzicht

Alle AEM Forms API&#39;s zijn verdeeld in twee hoofdonderdelen:

* [ Aangepaste Levering van de Vorm &amp; Runtime APIs ](https://developer-stage.adobe.com/experience-cloud/experience-manager-apis/api/stable/forms/)

* [AEM Forms Communication-API&#39;s](#aem-forms-communications-apis)

| Details | API&#39;s voor adaptieve levering en uitvoering van formulieren | Communicatie-API&#39;s |
|--------------|----------------------------|--------------------------|
| Doel | Aangepaste levering van formulieren en runtimebewerkingen verwerken | Documentgeneratie en -manipulatie |
| Gevallen gebruiken | - Formulierweergave <br> - Vooraf ingevulde gegevens <br> - Formulierverzendingen <br> - Conceptbeheer | - PDF genereren <br> - Document samenvoegen <br> - Batchverwerking <br> - Afdrukbewerkingen |
| Autorisatiemethode | Ondersteunt de verificatiemethoden van beide servers. | Ondersteunt server-naar-serververificatie, JWT of OAuth, afhankelijk van de API. Een API kan beide verificatiemethoden niet ondersteunen. |

### AEM Forms Communications API&#39;s

Communicatie-API&#39;s vormen de belangrijkste focus voor documentgerichte bewerkingen.

De lijst hieronder maakt een lijst van alle [ Communicatie APIs van AEM Forms ](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/) samen met hun gesteunde authentificatiemethodes en uitvoeringsmodellen:

#### API&#39;s voor het genereren van documenten


| API-eindpunt | Beschrijving | Uitvoeringsmodel | Verificatiemethode |
| ----- | ------ |------- | ------ |
| [ /adobe/forms/batch/output/config ](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-batch/#tag/Batch-Configuration/operation/CreateBatchConfig) | Hiermee maakt u een nieuwe batchconfiguratie voor taken voor het genereren van documenten. | Asynchroon/Batch | [ JWT ](/help/forms/jwt-api-authentication.md) |
| [ /adobe/forms/batch/output/config/{configName} ](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-batch/#tag/Batch-Configuration/operation/GetBatchConfigbyName) | Haalt details van een specifieke partijconfiguratie op. | Asynchroon/Batch | [ JWT ](/help/forms/jwt-api-authentication.md) |
| [ /adobe/forms/batch/output/config/configs ](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-batch/#tag/Batch-Configuration/operation/GetAllBatchConfigs) | Retourneert een lijst met alle beschikbare batchconfiguraties. | Asynchroon/Batch | [ JWT ](/help/forms/jwt-api-authentication.md) |
| [ /adobe/forms/batch/output/config/{configName}/executing](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-batch/#tag/Batch-Execution/operation/StartBatchRun) | Begint een runtime van de partijoutputgeneratie gebruikend een configuratie. | Asynchroon/Batch | [ JWT ](/help/forms/jwt-api-authentication.md) |
| [ /adobe/forms/batch/output/config/{configName} /executing/{executionId} ](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-batch/#tag/Batch-Execution/operation/GetBatchRunInstanceState) | Hiermee wordt de uitvoeringsstatus van een batchtaak opgehaald. | Asynchroon/Batch | [ JWT ](/help/forms/jwt-api-authentication.md) |
| [ /adobe/forms/batch/output/config/{configName} /Executions](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-batch/#tag/Batch-Execution/operation/GetAllRunningInstancesForBatch) | Vermeldt alle lopende instanties voor een specifieke partijconfiguratie. | Asynchroon/Batch | [ JWT ](/help/forms/jwt-api-authentication.md) |
| [ /adobe/forms/doc/v1/generatePDFOutput ](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-sync/#tag/Communications-Services/paths/~1adobe~1forms~1doc~1v1~1generatePDFOutput/post) | Hiermee genereert u synchroon PDF-uitvoer op basis van sjablonen en gegevens. | Synchroon | [ OAuth ](/help/forms/oauth-api-authetication.md) |
| [ /adobe/forms/doc/v1/generatePrintedOutput ](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-sync/#tag/Batch-Execution/operation/GetAllRunningInstancesForBatch) | Hiermee genereert u uitvoerindelingen die klaar zijn voor afdrukken (bijvoorbeeld PCL, PostScript). | Synchroon | [ OAuth ](/help/forms/oauth-api-authetication.md) |
| [ /adobe/forms/doc/v1/generate/afp ](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-sync/#tag/Communications-Services/paths/~1adobe~1forms~1doc~1v1~1generate~1afp/post) | Hiermee genereert u AFP-uitvoer voor afdrukken op grote volumes. | Synchroon | [ OAuth ](/help/forms/oauth-api-authetication.md) |
| [ /adobe/document/generate/pdfform ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/renderPDFForm) | Hiermee maakt u een PDF-formulier (XFA/XDP) met samengevoegde gegevens. | Synchroon | [ OAuth ](/help/forms/oauth-api-authetication.md) |
| [ /adobe/document/generate/pdfform/jobs/{id} /status](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/renderPDFFormJobStatus) | Hiermee wordt de status van een PDF-formuliergeneratietaak opgehaald. | Synchroon | [ OAuth ](/help/forms/oauth-api-authetication.md) |
| [ /adobe/document/generate/pdfform/jobs/{id} /result ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/renderPDFFormJobResult) | Hiermee wordt de uitvoer/het resultaat van een voltooide PDF-formuliertaak opgehaald. | Synchroon | [ OAuth ](/help/forms/oauth-api-authetication.md) |


#### Documentmanipulatie-API&#39;s

| API-eindpunt | Beschrijving | Uitvoeringsmodel | Verificatiemethode |
| ------------------ | ---------------- | ----------| ---------- |
| [ /adobe/forms/assembler/ddx/invoke ](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/assembler-sync/#tag/DDX-execution/operation/InvokeDDX) | Hiermee voert u DDX-instructies uit om PDF&#39;s te combineren, te splitsen of te bewerken. | Synchroon | [ JWT ](/help/forms/jwt-api-authentication.md) |
| [ /adobe/forms/assembler/pdfa/convert](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/assembler-sync/#tag/Document-conversion/operation/ConvertToPDFA) | Converteert een PDF-document naar de indeling PDF/A. | Synchroon | [ JWT ](/help/forms/jwt-api-authentication.md) |
| [ /adobe/forms/assembler/pdfa/validate ](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/assembler-sync/#tag/Document-validation/operation/CheckIsPDFA) | Valideert of een PDF voldoet aan de PDF/A-standaard | Synchroon | [ JWT ](/help/forms/jwt-api-authentication.md) |

#### Documentconversie-API&#39;s

| API-eindpunt | Beschrijving | Uitvoeringsmodel | Verificatiemethode |
|--------- | -------|---------|----------------------|
| [ /adobe/document/convert/pdftoxdp ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Conversion/paths/~1convert~1pdftoxdp/post) | Converteert een PDF-formulier naar XDP-indeling. | Synchroon | [ OAuth ](/help/forms/oauth-api-authetication.md) |

#### Extractie-API&#39;s voor documenten

| API-eindpunt | Beschrijving | Uitvoeringsmodel | Verificatiemethode |
|---------| -------|---------|----------------------|
| [ /adobe/forms/doc/v1/extract/pdfproperties ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Extraction/paths/~1extract~1pdfproperties/post) | Hiermee worden eigenschappen en structuurgegevens opgehaald uit een PDF. | Synchroon | [ OAuth ](/help/forms/oauth-api-authetication.md) |
| [ /adobe/forms/doc/v1/extract/usagerights ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/extractUsageRights) | Extraheert gebruiksrechten die zijn ingesloten in een PDF. | Synchroon | [ OAuth ](/help/forms/oauth-api-authetication.md) |
| [ /adobe/forms/doc/v1/extract/metadata ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Extraction/paths/~1extract~1metadata/post) | Extraheert metagegevens zoals titel, auteur en trefwoorden. | Synchroon | [ OAuth ](/help/forms/oauth-api-authetication.md) |
| [ /adobe/forms/doc/v1/extract/data ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/exportData) | Extraheert formuliergegevens (XML/JSON) uit PDF forms. | Synchroon | [ OAuth ](/help/forms/oauth-api-authetication.md) |
| [ /adobe/document/extract/security](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Extraction/paths/~1extract~1security/post) | Hiermee worden beveiligingsinstellingen opgehaald, zoals machtigingen en versleuteling. | Synchroon | [ OAuth ](/help/forms/oauth-api-authetication.md) |

#### API&#39;s voor documenttransformatie


| API-eindpunt | Beschrijving | Uitvoeringsmodel | Verificatiemethode |
|--------|---------|---------|----------------------|
| [ /adobe/document/transform/metadata ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Transformation/paths/~1transform~1metadata/post) | Hiermee werkt u metagegevens bij in een PDF-document of voegt u deze toe. | Synchroon | [ OAuth ](/help/forms/oauth-api-authetication.md) |
| [ /adobe/document/field/signature/add](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Transformation/paths/~1field~1signature~1add/post) | Hiermee voegt u een veld voor een digitale handtekening toe aan een PDF. | Synchroon | [ OAuth ](/help/forms/oauth-api-authetication.md) |
| [ /adobe/document/field/signature/clear ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Transformation/paths/~1field~1signature~1clear/post) | Wist de inhoud van een handtekeningveld. | Synchroon | [ OAuth ](/help/forms/oauth-api-authetication.md) |
| [ /adobe/document/field/signature/remove](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Transformation/paths/~1field~1signature~1remove/post) | Hiermee verwijdert u een handtekeningveld uit een PDF. | Synchroon | [ OAuth ](/help/forms/oauth-api-authetication.md) |

#### Document Assurance API&#39;s

| API-eindpunt | Beschrijving | Uitvoeringsmodel | Verificatiemethode |
|---------|-------|---------|----------------------|
| [ /adobe/document/sure/usagerights ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/applyUsageRights) | Hiermee past u gebruiksrechten toe op een PDF (bijvoorbeeld opmerking, vulling, teken). | Synchroon | [ OAuth ](/help/forms/oauth-api-authetication.md) |
| [ /adobe/document/confirm/encrypt ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Assurance/paths/~1assure~1encrypt/post) | Codeert een PDF met wachtwoord- of certificaatbeveiliging. | Synchroon | [ OAuth ](/help/forms/oauth-api-authetication.md) |
| [ /adobe/document/sure/decrypt ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Assurance/paths/~1assure~1decrypt/post) | Decodeert een beveiligd PDF-document. | Synchroon | [ OAuth ](/help/forms/oauth-api-authetication.md) |
| [ /adobe/document/confirm/sign](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Assurance/paths/~1assure~1sign/post) | Hiermee wordt een PDF-document digitaal ondertekend. | Synchroon | [ OAuth ](/help/forms/oauth-api-authetication.md) |
| [ /adobe/document/confirm/certify](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Assurance/paths/~1assure~1certify/post) | Hiermee wordt een PDF gecertificeerd met een digitaal certificaat. | Synchroon | [ OAuth ](/help/forms/oauth-api-authetication.md) |


## Verwante stappen

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
