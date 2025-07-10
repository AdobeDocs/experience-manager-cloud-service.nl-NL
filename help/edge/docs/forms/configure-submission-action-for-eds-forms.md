---
title: Verzendacties voor AEM Forms configureren met Edge Delivery Services
description: Leer hoe u verzendacties in AEM Forms configureert met Edge Delivery Services. Kies tussen Forms-verzendservice en AEM-publicatieactie voor verzending om formuliergegevens veilig en efficiënt te verwerken.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 8f490054-f7b6-40e6-baa3-3de59d0ad290
source-git-commit: 75d8ea4f0913e690e3374d62c6e7dcc44ea74205
workflow-type: tm+mt
source-wordcount: '2166'
ht-degree: 0%

---

# Formulierverzendingen configureren: waar gaan uw gegevens naartoe?

Nadat een gebruiker **** op uw vorm klikt voorlegt, moet u Edge Delivery Services vertellen wat met die gegevens te doen. U hebt twee hoofdopties:

## Methode 1: De AEM Forms-verzendservice gebruiken (vereenvoudigd)

Deze service is ideaal voor veelvoorkomende, eenvoudige handelingen, zoals het verzenden van gegevens naar een spreadsheet of een e-mail.

**wat is het en hoe kan het u helpen?**

De [ Dienst van de Verzending van Forms ](/help/forms/forms-submission-service.md) is een Adobe-ontvangen eindpunt. Wanneer uw formulier gegevens naar het formulier verzendt, neemt deze service de taak over en voert deze een vooraf geconfigureerde actie uit. Het is ontworpen om eenvoudig te kunnen worden ingesteld. U kunt configureren: verzenden naar spreadsheets of e-mail:

* **voorleggen aan Spreadsheet:** voeg automatisch de voorgelegde vormgegevens als nieuwe rij in een Blad van Google of een dossier van Microsoft toe Excel (dat op OneDrive of SharePoint wordt opgeslagen).
* **verzend E-mail:** verzend een e-mail die de vormgegevens aan één of meerdere e-mailadressen bevat u specificeert.

#### Belangrijk: installatievereisten

* **Toegang van Spreadsheet:** om gegevens naar een Blad van Google of een dossier van Excel op OneDrive/SharePoint te verzenden, heeft de de dienstrekening van Adobe (vaak `forms@adobe.com`) gewoonlijk **toestemmingen** op dat specifieke spreadsheet nodig uitgeven.
* **Vroege Programma van de Toegang:** Sommige eigenschappen van deze dienst, vooral voor spreadsheets, zouden deel van een vroege toegangsprogramma kunnen uitmaken. Mogelijk moet u toegang aanvragen door een e-mail `aem-forms-ea@adobe.com` te verzenden of een specifiek Adobe-formulier in te vullen met uw projectgegevens. Raadpleeg altijd de nieuwste Adobe-documentatie.

**Stroomschema van de Dienst van de Indiening van Forms**
<!--
```mermaid
    graph TD
    UserForm[User Submits Form on Your EDS Site] >|Data Sent| FormSubmissionService[AEM Forms Submission Service]
    FormSubmissionService -- "If configured for Google Sheets" > GoogleSheet[Data written to Google Sheet]
    FormSubmissionService -- "If configured for Excel (OneDrive or SharePoint)" > ExcelSheet[Data written to Excel]
    FormSubmissionService -- "If configured for Email" > Email[Email with data is sent]

    style UserForm fill:#ccf,stroke:#333
    style FormSubmissionService fill:#fca,stroke:#333
    style GoogleSheet fill:#90ee90,stroke:#333
    style ExcelSheet fill:#90ee90,stroke:#333
    style Email fill:#add8e6,stroke:#333
```-->
![ de Verzending van Forms ](/help/forms/assets/eds-fss.png)

In dit stroomschema ziet u hoe de Forms-verzendservice de verzonden gegevens verwerkt en naar een geconfigureerd werkblad of e-mail verzendt.

## Methode 2: verzenden naar uw AEM-publicatieexemplaar (geavanceerd)

Voor complexere behoeften, [ vormen (vooral die die met de Universele Redacteur worden gecreeerd) kunnen gegevens rechtstreeks naar uw AEM as a Cloud Service verzenden publiceren instantie ](/help/forms/configure-submit-actions-core-components.md). Dit ontgrendelt AEM volledige back-endkracht.

**wanneer moet u aan AEM voorleggen publiceren?**

* Aangepaste AEM Workflows activeren na verzending.
* Om het Model van de Gegevens van de Vorm van AEM (FDM) te gebruiken om met gegevensbestanden of andere ondernemingssystemen te integreren.
* Verbinding maken met services van derden, zoals Marketo, Microsoft Power Automate of Adobe Workfront Fusion.
* Gegevens opslaan op specifieke locaties, zoals Azure Blob Storage of SharePoint-lijsten/documentbibliotheken (niet alleen eenvoudige spreadsheets).
* Als u in AEM complexe validatie op de server of gegevensverwerkingslogica hebt.

**Beschikbare voorlegt Acties (AEM publiceert Verzending)**

* [Verzenden naar een REST-eindpunt](/help/forms/configure-submit-action-restpoint.md)
* [E-mail verzenden (met AEM-mailservices)](/help/forms/configure-submit-action-send-email.md)
* [Verzenden met gebruik van FDM (Form Data Model)](/help/forms/configure-data-sources.md)
* [Een AEM-workflow aanroepen](/help/forms/aem-forms-workflow-step-reference.md)
* [Verzenden naar SharePoint (als lijstitems of -documenten)](/help/forms/configure-submit-action-sharepoint.md)
* [Verzenden naar OneDrive (als documenten)](/help/forms/configure-submit-action-onedrive.md)
* [Verzenden naar Azure Blob Storage](/help/forms/configure-submit-action-azure-blob-storage.md)
* [Verzenden naar Microsoft Power Automate](/help/forms/forms-microsoft-power-automate-integration.md)
* [Verzenden naar Adobe Workfront Fusion](/help/forms/submit-adaptive-form-to-workfront-fusion.md)
* [ voorleggen aan Adobe Marketo Engage ](/help/forms/submit-adaptive-form-to-marketo-engage.md)

>[!NOTE]
>
> Zelfs als het richten van Google Sheet/Excel van AEM publiceert, impliceert het verschillende configuratiestappen dan de directe Dienst van de Verzending van Forms.

**AEM publiceert het Stroomschema van de Verzending**

<!--```mermaid
    graph TD
    UEForm[User Submits Universal Editor Form on EDS Site] >|Data sent to AEM Publish URL - example: /adobe/forms/af/submit/...| AEMPublish[AEM Publish Instance]
    AEMPublish -- Configured to run AEM Workflow > AEMWorkflow[AEM Workflow is Triggered]
    AEMPublish -- Configured to use Form Data Model > FDM[FDM updates Backend System or Database]
    AEMPublish -- Configured for Marketo > Marketo[Data sent to Marketo Engage]
    AEMPublish -- Other configured actions... > OtherIntegrations[...]

    style UEForm fill:#ccf,stroke:#333
    style AEMPublish fill:#fca,stroke:#333
    style AEMWorkflow fill:#add8e6,stroke:#333
    style FDM fill:#add8e6,stroke:#333
    style Marketo fill:#add8e6,stroke:#333
```-->

![ AEM publiceert het Stroomschema van de Verzending ](/help/forms/assets/eds-aem-publish.png)
In dit stroomschema ziet u een formulier dat wordt verzonden naar AEM Publish en dat vervolgens complexe back-endtaken verwerkt.

### Forms-verzendservice versus AEM-publicatieberichten

| Functie | Forms-verzendservice | AEM-verzendingen publiceren |
| :- | :- | :-- |
| **Best voor** | Eenvoudige gegevensvastlegging voor werkbladen, e-mailmeldingen | Complexe workflows, bedrijfsintegratie, aangepaste logica |
| **Authoring van de Vorm** | Goed voor op document gebaseerd; OK voor eenvoudige UE-formulieren | Meest geschikt voor geschreven formulieren in de Universal Editor |
| **Instellingsinspanning** | Laag (vaak eenvoudige configuratie) | Hoger (AEM Publish, Dispatcher, OSGi, CDN setup vereist) |
| **Het Systeem van de Achtergrond** | Adobe-gehoste service | Uw AEM as a Cloud Service-publicatie-exemplaar |
| **Flexibiliteit** | Beperkt tot blad/e-mail | Zeer flexibel, volledig scala aan AEM Forms-acties |
| **Voorbeeld** | Formuliergegevens koppelen aan een Google-blad | Toepassing van een lening die een AEM goedkeuringswerkschema in werking stelt |

## Forms insluiten op verschillende sites of pagina&#39;s

Soms wilt u een formulier weergeven dat op één locatie is gemaakt en beheerd (bijvoorbeeld een centrale &quot;formuliersite&quot;) op een andere webpagina of site.

### Waarom zou u een formulier insluiten?

* U hebt een standaardformulier &#39;Contact opnemen&#39; gemaakt met de Universal Editor dat moet verschijnen op meerdere bestemmingspagina&#39;s die zijn gemaakt met Document-Based Authoring.
* De inhoud van uw hoofdwebsite bevindt zich in Document Authoring (DA) en u moet een speciaal formulier opnemen.
* U wilt één enkele, goed onderhouden vorm over verscheidene verschillende EDS projecten opnieuw gebruiken.

### Technisch werkt insluiten van formulieren

De pagina waar u het formulier wilt weergeven (we noemen het &quot;hostpagina&quot;) bevat code (meestal een speciaal blok of script). Wanneer een gebruiker de hostpagina bezoekt, vraagt deze code naar de URL waar het daadwerkelijke formulier wordt gehost (we noemen het &quot;Form Source&quot;). De Form Source stuurt vervolgens de HTML terug, die de Host Page injecteert en weergeeft.

**Ingebedde Architectuur van de Vorm**

<!--```mermaid
   graph LR
    User[User] >|Visits| HostPage[Host Page - for example: your-site.com/landing-page]
    HostPage >|Contains code to embed form| FetchForm{Host Page Requests Form HTML}
    FetchForm >|HTTP GET request to the form URL| FormSource[Form Source - for example: forms-repo.hlx.page/my-form]
    FormSource >|Returns form HTML| FetchForm
    FetchForm >|Injects form HTML into page| HostPage
    HostPage >|Displays full page with embedded form| User

    subgraph Submission ["Form Submission from Host Page"]
        HostPage_Form[Embedded form on the host page] >|User submits| TargetEndpoint[Submission endpoint - FSS or AEM Publish]
    end

    style HostPage fill:#e6f3ff,stroke:#333
    style FormSource fill:#ffe6e6,stroke:#333
    style FetchForm fill:#fff2cc,stroke:#333
    style Submission fill:#f0fff0,stroke:#333
```-->
![ Ingebedde Architectuur van de Vorm ](/help/forms/assets/eds-embedded-form.png)
In dit diagram ziet u hoe de hostpagina HTML ophaalt van de Form Source en deze weergeeft. Voor verzending wordt het geconfigureerde eindpunt van het oorspronkelijke formulier gebruikt.

## CORS instellen voor ingesloten Forms

[ CORS (Cross-Origin Middel dat deelt) ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing) is een browser veiligheidseigenschap. Als uw hostpagina (bijvoorbeeld `site-a.com` ) een formulier probeert op te halen uit een ander domein (bijvoorbeeld `forms-site-b.com` ), blokkeert de browser het formulier tenzij `forms-site-b.com` het expliciet toestaat via CORS-koppen.

Zonder correcte kopballen CORS op de **server van Source van de Vorm**, verhindert browser de pagina van de Gastheer de vorm te laden, en uw ingebedde vorm zou niet verschijnen.

### Hoe te om CORS op de Plaats te vormen die uw Vorm dienen?

U moet de server vormen die **Vorm Source** ontvangt om specifieke kopballen van HTTP in zijn reactie te verzenden. De nauwkeurige methode hangt van uw opstelling EDS (bijvoorbeeld, voor projecten van Franklin af, wordt dit vaak gedaan in een `helix-config.yaml` of gelijkaardig configuratiedossier in uw bewaarplaats GitHub die gedrag CDN of de logica van de randworker controleert).
Belangrijke kopteksten die moeten worden toegevoegd aan de Source-reacties op formulier:

* `Access-Control-Allow-Origin: <URL_of_Host_Page>` (bijvoorbeeld `https://your-site.com` ). Voor het testen kunt u `*` gebruiken, maar voor de productie geeft u het exacte domein of de exacte domeinen op.
* `Access-Control-Allow-Methods: GET, OPTIONS` (U hebt mogelijk `POST` nodig als de verzending van het formulier zelf ook van oorsprong is, maar verzendingen doorgaans naar een afzonderlijk eindpunt gaan, vaak van dezelfde oorsprong of specifiek geconfigureerd.)
* `Access-Control-Allow-Headers: Content-Type` (en eventuele andere aangepaste kopteksten die uw formulier ophaalt, kunnen worden gebruikt).

**Voorbeeld (conceptueel voor een config- dossier):**

```yaml
        # In the configuration for the site HOSTING THE FORM (Form Source)
        headers:
          # Apply to paths where your forms are served, e.g., /forms/**
          - path: /forms/**
            custom:
              Access-Control-Allow-Origin: https://host-page-domain.com
              Access-Control-Allow-Methods: GET, OPTIONS
```

## Aanvullende overwegingen: CDN&#39;s en meerdere Codebases (Helix 4)

* **CDN Regels:** Uw CDN zou manieren aan volmachtsverzoeken kunnen aanbieden. Een aanvraag naar `host-page.com/embedded-form` kan bijvoorbeeld intern door de CDN worden gerouteerd om inhoud van `form-source.com/actual-form` op te halen, zodat deze dezelfde oorsprong voor de browser heeft. Dit kan complex zijn om in te stellen.
* **Veelvoudige Codebases (Helix 4):** als uw de Pagina van de Gastheer en Source van de Vorm in verschillende bewaarplaatsen GitHub (gemeenschappelijk in Helix 4 montages) zijn, zorg ervoor dat om het even welk &quot;blok van de Vorm&quot;nodig om de vorm terug te geven of te beheren beschikbaar in de codebase van de Pagina van de Gastheer is, of dat de vorm HTML die van de Vorm Source wordt gehaald met al zijn noodzakelijk JavaScript volledig is. In de oorspronkelijke documenten wordt aangegeven dat voor &quot;helix4 met verschillende codebasen, u het blok van de Vorm op beide codebases moet toevoegen.&quot;

### Gemeenschappelijke architectuurinstellingen en configuratiestappen

Hier volgen enkele voorbeelden van manieren waarop u formulieren kunt instellen, waarbij u ontwerpmethoden combineert met verzendingsstrategieën en belangrijke configuratiepunten.

#### Op document gebaseerd formulier met spreadsheet/e-mailverzending

Dit is de eenvoudigste instelling. U maakt uw formulier in Word/Google Docs en verzendt gegevens naar een werkblad of e-mail via de verzendservice van Forms.

1. Definieer het formulier in een Word/Google Doc/Sheet met behulp van de opgegeven tabelstructuur of het opgegeven formulierblok.
1. Geef in het document (of de verwante configuratie) de URL of het e-mailadres van de doelspreadsheet voor de Forms-verzendservice op.
1. Controleer of `forms@adobe.com` (of het desbetreffende serviceaccount) toegang tot uw doelspreadsheet heeft bewerkt.
1. Publiceer uw document naar uw Edge Delivery-site.

**op document-Gebaseerd + de Architectuur van de Dienst van de Verzending van Forms**
<!--
```mermaid
    graph TD
        User[<img src='https://img.icons8.com/ios-filled/50/000000/user.png' width='30' /> User] >|Fills Out| EDS_Page_DocBased[EDS Page with Document-Based Form]
        EDS_Page_DocBased >|Submits Data| FSS[AEM Forms Submission Service]
        FSS > Target[<img src='https://img.icons8.com/color/48/000000/google-sheets.png' width='30' /> Data to Spreadsheet / <img src='https://img.icons8.com/color/48/000000/filled-sent.png' width='30' /> Email Notification]

        Authoring[Form defined in Google Doc/Sheet] >|EDS Syncs & Renders| EDS_Page_DocBased

        style EDS_Page_DocBased fill:#ccf,stroke:#333
        style FSS fill:#fca,stroke:#333
        style Target fill:#90ee90,stroke:#333
        style Authoring fill:#e6ffe6,stroke:#333
```-->

![ op document-Gebaseerd + de Architectuur van de Dienst van de Verzending van Forms ](/help/forms/assets/eds-doc-fss.png)

#### Universal Editor-formulier met spreadsheet/e-mailverzending

U gebruikt de visuele Universal Editor om uw formulier samen te stellen, maar nog steeds de eenvoudige Forms-verzendservice voor het vastleggen van gegevens.

1. Maak uw formulier met de Universal Editor in AEM.
1. Configureer de verzendactie van het formulier in de EU voor gebruik van de optie &quot;Verzenden naar Forms-verzendservice&quot;.
1. Geef de URL of het e-mailadres van de doelspreadsheet op.
1. Als u spreadsheets gebruikt, moet u ervoor zorgen dat `forms@adobe.com` over bewerkingstoegang beschikt.
1. Publiceer uw pagina met het formulier van AEM naar uw Edge Delivery-site.

   **Universele Redacteur + de Architectuur van de Dienst van de Verzending van Forms**

   ![ Universele Redacteur + de Architectuur van de Dienst van de Verzending van Forms ](/help/forms/assets/eds-ue-fss.png)

   <!--```mermaid
    graph TD
    User[User] >|Fills Out| EDS_Page_UE[EDS Page with Universal Editor Form]
    EDS_Page_UE >|Submits Data| FSS[AEM Forms Submission Service]
    FSS > Target[Data sent to Google Sheet and Email Notification]
    AuthoringUE[Form built in Universal Editor - AEM] >|AEM Publishes to EDS| EDS_Page_UE
    style EDS_Page_UE fill:#ccf,stroke:#333
    style FSS fill:#fca,stroke:#333
    style Target fill:#90ee90,stroke:#333
    style AuthoringUE fill:#e6f3ff,stroke:#333
    ```
    -->

#### Universal Editor-formulier met publicatieverzending voor AEM (geavanceerd)

Deze instelling gebruikt de Universal Editor voor het maken van formulieren en uw AEM Publish-instantie voor krachtige back-endverwerking (workflows, FDM, enzovoort). Hiervoor is meer configuratie nodig.

1. **creeer Vorm in UE:** bouw uw vorm in de Universele Redacteur. Configureer de verzendactie zodat deze naar een AEM Forms-actie wijst (bijvoorbeeld &quot;Invoke an AEM Workflow&quot;, &quot;Submit using Form Data Model&quot;).
1. **AEM Dispatcher Configuratie (op uw AEM publiceer rij):**
   * **Geen Omleiding:** verzeker uw regels van Dispatcher ** opnieuw richten verzoeken die aan `/adobe/forms/af/submit/...` wegen worden gemaakt.
   * **Verzending toestaan:** wijzig uw filters van Dispatcher (b.v., in `filters.any`) aan uitdrukkelijk `allow` POST- verzoeken aan `/adobe/forms/af/submit/...` van het domein of IP van uw plaats van Edge Delivery adressen.
1. **filter OSGi Referrer in AEM (op uw AEM publiceer rij):**
   * In de console van AEM OSGi (`/system/console/configMgr`), vind en vorm de &quot;Filter van de Verwijzer van de Verwijzing Apache.&quot;
   * Voeg het domein of de domeinen van uw Edge Delivery-site (bijvoorbeeld `https://your-eds-domain.hlx.page`, `https://your-custom-eds-domain.com` ) toe aan de lijst Hosts toestaan of de lijst Hosts toestaan. Dit vertelt AEM om verzendingen van uw EDS-site te accepteren.
1. **CDN richt Regel (op uw Edge Delivery CDN) om:**
   * Uw Edge Delivery-site (bijvoorbeeld `your-eds-domain.hlx.page` ) moet verzendaanvragen correct doorsturen naar uw AEM-publicatie-exemplaar.
   * Wanneer het formulier op de EDS-pagina wordt verzonden, is het mogelijk gericht op een relatief pad, bijvoorbeeld `/adobe/forms/af/submit/...` . U hebt een regel op uw Edge Delivery CDN (of Edge-worker) nodig die als volgt luidt: &quot;Als een aanvraag naar `your-eds-domain.hlx.page/adobe/forms/af/submit/...` komt, doorsturen (proxy of omleiden) deze naar `your-aem-publish-instance.com/adobe/forms/af/submit/...`.&quot;
   * De exacte implementatie is afhankelijk van uw CDN-provider (bijvoorbeeld Fastly VCL, Akamai Property Manager, Cloudflare Workers).
1. **(Optioneel) `constants.js` voor ontwikkeling (in de codebase van uw EDS-project):**
   * Voor lokale ontwikkeling of als uw cliënt-zijvormmanuscripten de volledige AEM moeten kennen publiceer URL, zou u dit in een `constants.js` of gelijkaardig configuratiedossier binnen de bewaarplaats van GitHub van uw Edge Delivery project kunnen vormen. Voorbeeld:

   ```javascript
       // in your-eds-project/scripts/constants.js
       export const AEM_PUBLISH_URL = 'https://publish-p123-e456.adobeaemcloud.com';
            // Your form submission script might then construct the submit URL:
           // const submitUrl = `${AEM_PUBLISH_URL}/adobe/forms/af/submit/...`;
   ```

1. **publiceer:** publiceer uw vormpagina van AEM aan EDS, en zorg ervoor alle configuraties van AEM actief op uw de Publish instantie van AEM zijn.

   **Universele Redacteur + AEM publiceer Architectuur**

![ Universele Redacteur + AEM publiceer Architectuur ](/help/forms/assets/eds-aem-publish.png)

Dit toont de stroom: de gebruiker legt op plaats EDS voor, CDN leidt naar AEM Dispatcher, dan publiceert AEM het.

#### Een formulier insluiten in een documentontwerppagina (DA)

De inhoud van uw hoofdwebsite wordt gemaakt in Document Authoring (DA). U maakt uw formulier met Document-Based Authoring of de Universal Editor afzonderlijk en sluit het vervolgens in uw DA-pagina in.

1. **creeer en publiceer de Vorm:**
   * Gebruik Auteurs op basis van documenten OF Universal Editor om uw formulier te maken.
   * Vorm zijn voorleggingsmethode (of aan de Dienst van de Verzending van Forms of de Publicatie van AEM, volgens Opstelling 1, 2, of 3).
   * Publiceer dit formulier zodat het live is op de eigen Edge Delivery-URL (bijvoorbeeld `.../forms/my-special-form`).
1. **vorm CORS:** op de plaats/het project van Edge Delivery dat gastheren deze standalone vorm, ervoor zorgen de kopballen CORS opstelling zijn om het domein van uw Document Authoring plaats toe te staan om het te halen.
1. **de Pagina van de Auteur in DA:** creeer of geef uw pagina in Document Authoring uit.
1. **bed het Blok van de Vorm in:** gebruik het aangewezen blok in DA om externe URL in te bedden. Wijs dit blok aan URL van uw standalone gepubliceerde vorm.
1. **publiceer DA Pagina:** publiceer uw pagina van DA. Het formulier wordt nu opgehaald en weergegeven.

   **Forms Ingebed in architectuur DA**

   ![ Forms Ingebed in architectuur DA ](/help/forms/assets/eds-forms-embedd-da.png)

   Dit toont een pagina van DA die in een vorm van een andere plaats EDS trekt. Het ingesloten formulier verwerkt zijn eigen verzending.

## Problemen oplossen

* **Mijn vormvoorlegging werkt niet.**
   * **de Fouten van de Console van de Controle:** Open de de ontwikkelaarsconsole van uw browser (gewoonlijk F12) en zoek fouten op het lusje van het Netwerk of het lusje van de Console wanneer u voorlegt.
   * **verifieer Verzending URL:** probeert de vorm om aan het correcte eindpunt (de Dienst URL van de Verzending van Forms of uw AEM Publish weg) voor te leggen?
   * **de Dienst van de Verzending van Forms:** Als het verzenden naar een spreadsheet, `forms@adobe.com` heeft gegeven geef toegang uit? Klopt de URL van het werkblad?
   * **AEM publiceert Verzending:**
      * Staat uw Dispatcher POST&#39;s toe op `/adobe/forms/af/submit/...` ?
      * Is het filter Verschuivende verwijzing op AEM-publicatie geconfigureerd om uw EDS-domein toe te staan?
      * Werken de CDN-omleidingsregels voor `/adobe/forms/af/submit/...` correct?

* **Mijn ingebedde vorm verschijnt niet.**

   * **CORS!** Dit is de meest voorkomende reden. Controleer de browserconsole op CORS-fouten. Verzeker de plaats *het ontvangen* de vorm heeft de correcte `Access-Control-Allow-Origin` kopballen.
   * **Juiste vorm URL?** Wijst de insluitcode op de hostpagina naar de juiste live URL van het formulier?
   * **de Blokken van JavaScript:** als de vorm op een specifiek JavaScript &quot;blok van de Vorm&quot;voor het teruggeven vertrouwt, is de code van dat blok beschikbaar op de gastheerpagina?

* **ik krijg &quot;403 Verboden&quot;of &quot;401 Onbevoegd&quot;wanneer het voorleggen aan AEM publiceert.**

   * Dit verwijst vaak naar het filter Verschuivende verwijzing in AEM-publicatie dat aanvragen van uw EDS-domein niet toestaat. Controleer de configuratie ervan.
   * Het zou ook een authentificatie/vergunningskwestie kunnen zijn als uw AEM eindpunt voorlegt het vereist, hoewel de standaardvormverklaringen gewoonlijk anoniem zijn.

## Volgende stappen

Deze handleiding bevat een overzicht van het gebruik van formulieren met AEM Edge Delivery Services. Raadpleeg de officiële documentatie bij Adobe Experience Manager voor gedetailleerde, stapsgewijze instructies over specifieke configuraties:

* [Authoring op basis van documenten met Edge Delivery Services Forms](/help/edge/docs/forms/tutorial.md)
* [Universele editor met Edge Delivery Services Forms](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md)
* [ Document Authoring (DA) en het Inbedden Inhoud ](https://www.aem.live/developer/da-tutorial)
* [AEM Forms-verzendservice](/help/edge/docs/forms/configure-submission-action-for-eds-forms.md)
