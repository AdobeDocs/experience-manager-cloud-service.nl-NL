---
title: Hoe instellen van OAuth Server-to-Server verificatie?
description: Leer hoe u OAuth Server-to-Server verificatie voor Adobe Experience Manager Forms as a Cloud Service configureert
role: Admin, Developer, User
feature: Adaptive Forms, APIs & Integrations
hide: true
hidefromtoc: true
index: false
source-git-commit: fcc25eb44b485db69ec1c267f4cf8774c4279b24
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 0%

---


# OAuth Server-to-Server Authentificatie - Aanbevolen

Met verificatie van server naar server kunt u veilige, tokengebaseerde toegang tot AEM Forms Communications API&#39;s toestaan zonder gebruikersinteractie te vereisen. Deze methode is ideaal voor geautomatiseerde systemen, achtergrondservices en integraties die programmatisch moeten worden geverifieerd.

## Vereisten

Voordat u begint, moet u controleren of aan de volgende voorwaarden is voldaan:

* Zorg ervoor dat u toegang tot [ Adobe Developer Console ](https://developer.adobe.com/console) specifiek voor het milieu hebt u gebruikt.
* Wijs de rol Systeembeheerder of Ontwikkelaar in de Adobe Admin Console toe om toegang tot de Adobe Developer Console mogelijk te maken.

## Hoe te om een Token van de Toegang te produceren die de Server-aan-server Authentificatie van OAuth gebruikt?

Volg de stappen hieronder die u toont hoe te om een toegangstoken van de console van Adobe Developer te produceren, en uw eerste API vraag door de Authentificatie van Server-aan-Server van OAuth te maken.


1. Ga aan [ Adobe Developer Console ](https://developer.adobe.com/console)
2. Meld u aan bij uw Adobe ID

3. Nieuw project maken of naar een bestaand project navigeren

   **om een nieuw project tot stand te brengen:**

   1. Van de **Snelle sectie van het Begin**, klik **creeer nieuw project**
   2. Een nieuw project wordt gecreeerd met een standaardnaam

      ![ creeer ADC Project ](/help/forms/assets/adc-home.png)

   3. Klik **uitgeven project** in de hoogste juiste hoek

      ![ geef Project ](/help/forms/assets/adc-edit-project.png) uit

   4. Geef een betekenisvolle naam op (bijvoorbeeld &quot;formsproject&quot;)
   5. Klik **sparen**

      ![ geef de Naam van het Project uit ](/help/forms/assets/adc-edit-projectname.png)


   **om aan uw bestaand project te navigeren:**

   1. Klik **Alle Projecten** van Adobe Developer Console

      ![ Projecten van het Onderzoek ](/help/forms/assets/search-adc-project.png)

   2. Zoek uw project en klik om het te openen.

      ![ plaats Projecten ](/help/forms/assets/locate-adc-project.png)


      >[!NOTE]
      >
      > U kunt API en authentificatiemethode aan uw bestaand project toevoegen door **te klikken voegt aan Project** toe > **API**\
      > ![ voeg API aan bestaand Project ](/help/forms/assets/add-api-existing-project.png) toe
      > Om API en authentificatiemethode toe te voegen, voer de zelfde stappen uit zoals hieronder voor uw bestaand project wordt verklaard.

4. Voeg verschillende AEM Forms Communications API&#39;s toe, afhankelijk van uw vereisten.

   **A. Voor Document Services API&#39;s**

   1. Klik **toevoegen API**

      ![ voeg api ](/help/forms/assets/adc-add-api.png) toe

   2. Selecteer **Communicatie APIs van Forms**
      1. In _voeg API_ dialoog toe, filter door **Experience Cloud**
      2. Selecteer **&quot;Communicatie APIs van Forms&quot;**

         ![ voeg Communicatie API van Forms toe ](/help/forms/assets/adc-add-forms-api.png)


   3. Selecteer **Server-aan-Server** authentificatiemethode

      ![ Uitgezochte methode van de Authentificatie ](/help/forms/assets/adc-add-authentication-method.png)


   **B. Voor Adaptive Forms Runtime API&#39;s**

   1. **klik toevoegen API**
In uw project, klik **toevoegen API** knoop

      ![ voeg api ](/help/forms/assets/adc-add-api.png) toe

   2. **Uitgezochte AEM Forms Levering en Runtime API**
      1. In _voeg API_ dialoog toe, filter door **Experience Cloud**
      2. Selecteer **&quot;AEM Forms Delivery and Runtime API&quot;**
      3. Klik **daarna**

   3. **Methode van de Authentificatie**
Selecteer **Server-aan-Server** authentificatiemethode.


      ![ Uitgezochte methode van de Authentificatie ](/help/forms/assets/adc-add-authentication-method.png)

5. **voeg het Profiel van het Product** toe:

   1. Selecteer het aangewezen **Profiel van het Product** dat op vereist toegangsniveau wordt gebaseerd:

      | Toegangstype | Productprofiel |
      |------------------|----------------------|
      | Alleen-lezen toegang | `AEM Users - author - Program XXX - Environment XXX` |
      | Toegang lezen/schrijven | `AEM Assets Collaborator Users - author - Program XXX - Environment XXX` |
      | Volledige administratieve toegang | `AEM Administrators - author - Program XXX - Environment XXX` |

   2. Selecteer het **Profiel van het Product** dat uw Dienst URL van de Auteur (`https://author-pXXXXX-eYYYYY.adobeaemcloud.com`) aanpast. Selecteer bijvoorbeeld `https://author-pXXXXX-eYYYYY.adobeaemcloud.com` .

   3. Klik **sparen gevormde API**. De API en het Profiel van het Product worden toegevoegd aan uw project

      ![ Uitgezochte Configuratie van het Project ](/help/forms/assets/adc-add-product-profile.png)

6. Credentials genereren en opslaan

   1. Ga naar uw project in Adobe Developer Console
   2. Klik op **Server-aan-Server** referentie
   3. Bekijk de **Credentials details** sectie

      ![ Credentials van de Mening ](/help/forms/assets/adc-view-credential.png)

   4. Opname API-referenties

      ```text
      API Credentials:
      ================
      Client ID: <your_client_id>
      Client Secret: <your_client_secret>
      Technical Account ID: <tech_account_id>
      Organization ID: <org_id>
      Scopes: AdobeID,openid,read_organizations
      ```

7. Tokengeneratie openen

   **A. Voor testen**

   Handmatig toegangstokens genereren in Adobe Developer Console:

   1. **ga aan uw Project**
      1. Open uw project in Adobe Developer Console
      2. Klik **Server-aan-Server**

   2. **produceer het Token van de Toegang**
      1. Klik **&quot;produceer toegangstoken&quot;** knoop in de API van uw project sectie
      2. Het gegenereerde toegangstoken kopiëren

      ![ produceer het Token van de Toegang ](/help/forms/assets/adc-access-token.png)

      >[!NOTE]
      >
      > Het teken van de toegang is geldig slechts voor **24 uren**

   **B. Voor productie**

   Tkens programmatisch genereren met Adobe IMS API:

   **Vereiste Referenties:**

   * Client-id
   * Clientgeheim
   * Bereiken (doorgaans: `openid, AdobeID, read_organizations, additional_info.projectedProductContext, read_pc.dma_aem_cloud, aem.document`)

   **Symbolische Eindpunt:**

   ```
   https://ims-na1.adobelogin.com/ims/token/v3
   ```

   **Verzoek van de Steekproef (krulling):**

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

U kunt het gegenereerde toegangstoken nu gebruiken om API-aanroepen te maken voor ontwikkelings-, stage- of productieomgevingen.

>[!NOTE]
>
> Om meer over Server-aan-Server implementatie te weten OAuth om toegangstoken te produceren en API vraag te maken, [ klik hier ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation).

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


