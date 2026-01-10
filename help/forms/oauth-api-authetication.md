---
title: Hoe instellen van OAuth Server-to-Server verificatie?
description: Leer hoe u OAuth Server-to-Server verificatie voor Adobe Experience Manager Forms as a Cloud Service configureert
role: Admin, Developer, User
feature: Adaptive Forms, APIs & Integrations
hide: true
hidefromtoc: true
index: false
source-git-commit: 6bd2e1698cceaf8fe47e19e0645d0782c916644a
workflow-type: tm+mt
source-wordcount: '817'
ht-degree: 0%

---


# OAuth Server-to-Server Authentificatie

Met verificatie van server naar server kunt u veilige, tokengebaseerde toegang tot AEM Forms Communications API&#39;s toestaan zonder gebruikersinteractie te vereisen. OAuth server-aan-server authentificatie wordt gesteund door Adobe Developer Console.

## Vereisten

Voordat u begint, moet u controleren of aan de volgende voorwaarden is voldaan:

* Zorg ervoor dat u [&#x200B; toegang tot Adobe Developer Console &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-manager/content/requirements/access-rights) specifiek voor het milieu hebt u gebruikt.
* [&#x200B; wijs de rol van de Beheerder of van de Ontwikkelaar van het Systeem in Adobe Admin Console &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-manager/content/requirements/role-based-permissions) toe om toegang tot Adobe Developer Console toe te laten.

## Hoe te om een Token van de Toegang te produceren die de Server-aan-server Authentificatie van OAuth gebruikt?

Volg de onderstaande stappen om een toegangstoken van de console van Adobe Developer te produceren, en uw eerste API vraag door de Server-aan-Server Authentificatie van OAuth te maken.

### 1. Adobe Developer Console Project Setup

1. Ga aan [&#x200B; Adobe Developer Console &#x200B;](https://developer.adobe.com/console)
2. Meld u aan bij uw Adobe ID

3. Nieuw project maken of naar een bestaand project navigeren

>[!BEGINTABS]

>[!TAB om een nieuw project  te creëren]

1. Van de **Snelle sectie van het Begin**, klik **creeer nieuw project**
2. Een nieuw project wordt gecreeerd met een standaardnaam

   ![&#x200B; creeer ADC Project &#x200B;](/help/forms/assets/adc-home.png)

3. Klik **uitgeven project** in de hoogste juiste hoek

   ![&#x200B; geef Project &#x200B;](/help/forms/assets/adc-edit-project.png) uit

4. Geef een betekenisvolle naam op (bijvoorbeeld &quot;formsproject&quot;)
5. Klik **sparen**

   ![&#x200B; geef de Naam van het Project uit &#x200B;](/help/forms/assets/adc-edit-projectname.png)

>[!TAB om aan uw bestaand project  te navigeren]

1. Klik **Alle Projecten** van Adobe Developer Console

   ![&#x200B; Projecten van het Onderzoek &#x200B;](/help/forms/assets/search-adc-project.png)

2. Zoek uw project en klik om het te openen.

   ![&#x200B; plaats Projecten &#x200B;](/help/forms/assets/locate-adc-project.png)

>[!ENDTABS]

### &#x200B;2. Forms API&#39;s toevoegen

Voeg Forms API&#39;s toe op basis van wat u wilt doen:

* **Communicatie APIs van AEM Forms**: gebruik wanneer u, documenten (PDF en verwante formaten) moet produceren omzetten, assembleren of beveiligen.
* **Adaptieve Runtime van Forms APIs** - gebruik wanneer u, Adaptieve Forms bij runtime moet teruggeven voorleggen of verwerken.

>[!BEGINTABS]

>[!TAB  voor Communicatie APIs van AEM Forms ]

1. Klik **toevoegen API**

   ![&#x200B; voeg api &#x200B;](/help/forms/assets/adc-add-api.png) toe

2. Selecteer **Communicatie APIs van Forms**
   1. In _voeg API_ dialoog toe, filter door **Experience Cloud**
   2. Selecteer **&quot;Communicatie APIs van Forms&quot;**

      ![&#x200B; voeg Communicatie API van Forms toe &#x200B;](/help/forms/assets/adc-add-forms-api.png)

   3. Klik **daarna**
   4. Selecteer **Server-aan-Server** authentificatiemethode

      ![&#x200B; Uitgezochte methode van de Authentificatie &#x200B;](/help/forms/assets/adc-add-authentication-method.png)

>[!TAB  voor AanpassingsForms Runtime APIs ]

1. **klik toevoegen API**

   ![&#x200B; voeg api &#x200B;](/help/forms/assets/adc-add-api.png) toe

2. **Uitgezochte AEM Forms Levering en Runtime API**
   1. In _voeg API_ dialoog toe, filter door **Experience Cloud**
   2. Selecteer **&quot;AEM Forms Delivery and Runtime API&quot;**
      ![&#x200B; voeg Communicatie API van Forms toe &#x200B;](/help/forms/assets/adc-add-runtime-api.png)

   3. Klik **daarna**
   4. Selecteer **Server-aan-Server** authentificatiemethode.
      ![&#x200B; Uitgezochte methode van de Authentificatie &#x200B;](/help/forms/assets/adc-add-authentication-method.png)

>[!ENDTABS]

U kunt API en authentificatiemethode aan uw bestaand project ook toevoegen door **te klikken toevoegt aan Project** > **API**\
![&#x200B; voeg API aan bestaand Project &#x200B;](/help/forms/assets/add-api-existing-project.png) toe

### &#x200B;3. Productprofiel toevoegen

Het productprofiel bevat machtigingen (of autorisaties) voor referenties om toegang te krijgen tot de AEM-bronnen.

1. Selecteer het **Profiel van het Product** dat uw instantie URL van AEM (`https://Service Type -Environment Type-Program XXX-Environment XXX.adobeaemcloud.com`) aanpast.

   * **Type van Dienst** - specificeert de diensten of toestemmingen verbonden aan de instantie van AEM

   * **Type van Milieu** - specificeert of het milieu voor de dienst van de Auteur of van de Publicatie is

   * **Programma XXX** - identificeert Cloud Manager programma identiteitskaart

   * **Milieu XXX** - identificeert specifieke milieuidentiteitskaart binnen dat programma

   >[!NOTE]
   >
   > Productprofielen zijn gekoppeld aan een specifieke AEM-instantie (programma + omgeving). Kies altijd het profiel dat overeenkomt met de instantie-URL.

2. Klik **sparen gevormde API**. De API en het Profiel van het Product worden toegevoegd aan uw project

   ![&#x200B; Uitgezochte Configuratie van het Project &#x200B;](/help/forms/assets/adc-add-product-profile.png)

### &#x200B;4. Referenties genereren en opslaan

1. Ga naar uw project in Adobe Developer Console
2. Klik **Server-aan-Server** referentie
3. Bekijk de **Credentials details** sectie

   ![&#x200B; Credentials van de Mening &#x200B;](/help/forms/assets/adc-view-credential.png)

**Opname API geloofsbrieven**

```text
    API Credentials:
    ================
    Client ID: <your_client_id>
    Client Secret: <your_client_secret>
    Technical Account ID: <tech_account_id>
    Organization ID: <org_id>
    Scopes: AdobeID,openid,read_organizations
```

### &#x200B;5. Tokengeneratie benaderen

Genereer het toegangstoken handmatig of programmatisch:

>[!BEGINTABS]

>[!TAB  voor het Testen ]

Handmatig toegangstokens genereren in Adobe Developer Console:

1. **ga aan uw Project**
   1. Open uw project in Adobe Developer Console
   2. Klik **Server-aan-Server**

2. **produceer het Token van de Toegang**
   1. Klik **&quot;produceer toegangstoken&quot;** knoop in de API van uw project sectie
   2. Het gegenereerde toegangstoken kopiëren

   ![&#x200B; produceer het Token van de Toegang &#x200B;](/help/forms/assets/adc-access-token.png)

   >[!NOTE]
   >
   > Het teken van de toegang is geldig slechts voor **24 uren**

>[!TAB  voor Productie ]

Genereer programmatically tokens gebruikend [&#x200B; IMS van Adobe &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/security/setting-up-ims-integrations-for-aem-as-a-cloud-service) API:

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

>[!ENDTABS]

U kunt het gegenereerde toegangstoken nu gebruiken om API-aanroepen te maken voor ontwikkelings-, stage- of productieomgevingen.

>
>
> Om meer over Server-aan-Server implementatie te weten OAuth om toegangstoken te produceren en API vraag te maken, [&#x200B; klik hier &#x200B;](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation).

## Tips en trucs: Beheer uw aanmeldingsgegevens voor Ontwikkeling, Staging en Productie

* Gebruik altijd afzonderlijke referenties voor Ontwikkeling, Staging en Productie.

* Wijs elke referentie toe aan de juiste URL voor de AEM-omgeving.

* Sla geheimen veilig op en verbind ze nooit tot broncontrole.

* Geldigheid van toegangstoken bijhouden, aangezien tokens slechts 24 uur geldig zijn.

## Volgende stappen

Leren hoe te opstellingsmilieu voor Synchrone Communicatie APIs van Forms, zie [&#x200B; Communicatie van AEM Forms as a Cloud Service Synchrone Verwerking &#x200B;](/help/forms/aem-forms-cloud-service-communications-on-demand-processing.md).


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


