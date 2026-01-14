---
title: Hoe instellen van JWT-verificatie (JSON Web Token)?
description: Leer hoe u JWT-verificatie (JSON Web Token) voor Adobe Experience Manager Forms as a Cloud Service configureert
role: Admin, Developer, User
feature: Adaptive Forms, APIs & Integrations
source-git-commit: 43b648eb3984867fda35ee04de10b78dd836b481
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---


# JWT (JSON Web Token) Server-aan-server Authentificatie

JWT server-aan-server authentificatie in AEM Forms, vooral voor server-zijintegratie met AEM as a Cloud Service, impliceert een specifiek proces om veilig met de diensten van AEM in wisselwerking te staan. JWT-verificatie van server naar server wordt ondersteund door AEM Developer Console.

## Vereisten

Voordat u begint, moet u controleren of aan de volgende voorwaarden is voldaan:

* Zorg ervoor dat u toegang tot [&#x200B; Adobe Cloud Manager &#x200B;](https://experience.adobe.com/#/@formsinternal01/cloud-manager/landing.html) specifiek voor het milieu hebt u gebruikt.
* Wijs de [&#x200B; rol van de Beheerder of van de Ontwikkelaar van het Systeem aan toegang Adobe Cloud Manager &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-manager/content/requirements/access-rights) toe.

## Hoe te om een Token van de Toegang te produceren gebruikend geloofsbrieven JWT?

Volg de stappen hieronder die u tonen hoe te om een toegangstoken van de geloofsbrieven te produceren JWT.

1. **Adobe Cloud Manager**

   1. Login aan uw [&#x200B; rekening van Cloud Manager &#x200B;](https://experience.adobe.com/#/@formsinternal01/cloud-manager/landing.html).
   2. Klik op **[!UICONTROL Program Overview]** voor het geselecteerde programma.

      ![&#x200B; Cloud Manager- Rekening &#x200B;](/help/forms/assets/jwt-cloud-manager-landing.png)

   3. Klik in uw programma op het menu met drie puntjes en selecteer **[!UICONTROL Developer Console]** .

      ![Developer Console](/help/forms/assets/jwt-developer-console.png)

2. **AEM Developer Console**
   1. Aanmelden bij AEM Developer Console
   2. Klik op **[!UICONTROL Integrations]** in de bovenste menubalk.

      ![&#x200B; Integraties &#x200B;](/help/forms/assets/jwt-integrations.png)

   3. Klik op de optie om **[!UICONTROL Create new technical account]** te gebruiken.

      ![&#x200B; creeer nieuwe technische rekening &#x200B;](/help/forms/assets/jwt-creae-new-tech-account.png)

   Nadat u op een nieuwe technische account hebt geklikt, wordt de vereiste informatie voor het genereren van een toegangstoken gegenereerd, zoals de client-id en het clientgeheim, samen met andere technische accountgegevens, zoals de persoonlijke sleutel, de openbare sleutel en de vervaldatum.

   ![&#x200B; JWT Credentials &#x200B;](/help/forms/assets/jwt-credentials.png)


3. **produceer en sparen Referenties**

   1. Opname API-referenties

      ```text
      API Credentials:
      ================
      Client ID: <your_client_id>
      Client Secret: <your_client_secret>
      Technical Account ID: <tech_account_id>
      Organization ID: <org_id>
      Scopes: AdobeID,openid,read_organizations
      ```

4. **Symbolische Generatie van de Toegang**

   Tkens programmatisch genereren met de opdracht cURL:

   **Vereiste Referenties:**

   * Client-id
   * Clientgeheim
   * Bereiken (doorgaans: `openid, AdobeID, read_organizations, additional_info.projectedProductContext, read_pc.dma_aem_cloud, aem.document`)

   **Symbolische Eindpunt:**

   ```
   https://ims-na1.adobelogin.com/ims/token/v3
   ```

   **Verzoek van de Steekproef (cURL):**

   ```bash
   curl -X POST 'https://ims-na1.adobelogin.com/ims/token/v3' \
   -H 'Content-Type: application/x-www-form-urlencoded' \
   -d 'grant_type=client_credentials' \
   -d 'client_id=<YOUR_CLIENT_ID>' \
   -d 'client_secret=<YOUR_CLIENT_SECRET>' \
   -d 'scope=AdobeID,openid,read_organizations'
   ```

   **Reactie:**

   ```json
   {
   "access_token": "eyJhbGciOiJSUz...",
   "token_type": "bearer",
   "expires_in": 86399
   }
   ```


>[!NOTE]
>
> Meer over de dienstgeloofsbrieven leren en hoe te om een toegangstoken te produceren gebruikend Adobe IMS API, [&#x200B; klik hier &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials).

U kunt het gegenereerde toegangstoken nu gebruiken om API-aanroepen te maken voor ontwikkelings-, stage- of productieomgevingen.

## Verwante artikelen

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
>* [&#x200B; Inleiding aan de Mededelingen van AEM Forms as a Cloud Service &#x200B;](/help/forms/aem-forms-cloud-service-communications-introduction.md)
>* [&#x200B; de Architectuur van as a Cloud Service van AEM Forms voor Adaptieve Forms en Communicatie APIs &#x200B;](/help/forms/aem-forms-cloud-service-architecture.md)
>* [&#x200B; Communicatie Verwerking - Synchrone APIs &#x200B;](/help/forms/aem-forms-cloud-service-communications.md)
>* [&#x200B; Communicatie Verwerking - Partij APIs &#x200B;](/help/forms/aem-forms-cloud-service-communications-batch-processing.md)
>* [&#x200B; Communicatie API van Forms - Leerprogramma &#x200B;](/help/forms/aem-forms-cloud-service-communications-on-demand-processing.md)