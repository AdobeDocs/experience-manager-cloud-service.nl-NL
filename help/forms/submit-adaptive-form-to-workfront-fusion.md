---
title: Integratie van Adobe Workfront Fusion met AEM Forms-verzending
description: Met Adobe Workfront Fusion kunt u zich richten op nieuwe taken in plaats van zich te richten op herhaalde taken. U kunt Adobe Workfront Fusion via Formulierverzending verbinden met een adaptief formulier.
keywords: Een adaptief formulier verzenden naar Adobe Workfront Fusion, Integration of Adobe Workfront Fusion with AEM Forms Submission, Adobe Workfront Fusion with AEM Forms, Workfront Fusion with AEM Forms, Connect Workfront Fusion to AEM Forms, AEM Forms en Workfront Fusion, How to connect Workfront Fusion with AEM Forms, Connect Workfront Fusion to a Form?
topic-tags: author, developer
feature: Adaptive Forms
role: Admin, User
exl-id: d3efb450-a879-40ae-8958-0040f99bdafc
source-git-commit: 559b4afa975dcd2204cd06c95f19ed38da00033e
workflow-type: tm+mt
source-wordcount: '1174'
ht-degree: 0%

---

# Een adaptief formulier verzenden naar Adobe Workfront Fusion

<span class="preview"> Deze functie is beschikbaar in het programma voor vroege adoptie. U kunt vanaf uw officiële e-mailadres naar aem-forms-ea@adobe.com schrijven om deel te nemen aan het programma voor vroege adoptie en toegang tot de functie te vragen. </span>

[Adobe Workfront Fusion](https://experienceleague.adobe.com/docs/workfront/using/adobe-workfront-fusion/get-started-with-workfront-fusion/workfront-fusion-overview.html) automatiseert het proces waarbij dezelfde taken worden herhaald, zoals workflows voor documentgoedkeuring, filteren en sorteren via e-mail, zodat u zich kunt concentreren op nieuwe taken in plaats van op terugkerende taken. Adobe Workfront Fusion bevat meerdere scenario&#39;s. Een scenario bestaat uit een reeks modules die gegevensoverdracht tussen toepassingen en Webdiensten uitvoert. In een scenario, voegt u diverse stappen (modules) toe om een taak te automatiseren.

Met Workfront Fusion kunt u bijvoorbeeld een scenario maken voor het verzamelen van gegevens met Adaptief formulier, het verwerken van de gegevens en het verzenden van de gegevens naar een gegevensopslagruimte voor archivering. Wanneer een scenario is ingesteld, voert Workfront Fusion automatisch de taken uit wanneer een gebruiker een formulier invult en de gegevensopslag naadloos bijwerkt.

AEM Forms as a Cloud Service biedt een OOTB-connector om een adaptief formulier aan te sluiten en in te dienen bij Adobe Workfront Fusion. Het verzenden van een formulier naar Adobe Workfront Fusion kan verschillende voordelen bieden:
* Zo konden formulierverzendgegevens naadloos worden overgedragen naar Workfront Fusion-workflows.
* Hiermee kunt u verschillende taken automatiseren die worden veroorzaakt door het verzenden van formulieren. Dit kan het in werking stellen van projecten omvatten, het toewijzen van taken aan specifieke teamleden, het verzenden van berichten, en het bijwerken van projectstatus-allen zonder handinterventie.
* Alle formulierverzendingen die in Workfront Fusion zijn vastgelegd, bieden één waarheidsbron voor projectgerelateerde informatie


<!--  AEM as a Cloud Service offers various out of the box submit actions for handling form submissions. You can learn more about these options in the [Adaptive Form Submit Action](/help/forms/configure-submit-actions-core-components.md)  article.-->

>[!VIDEO](https://video.tv.adobe.com/v/3427145/adaptive-forms-adobe-workfront-af-workfront-workfront-aem-forms/?quality=12&learn=on)

## Vereisten om AEM Forms te integreren met Adobe Workfront Fusion {#prerequisites}

Voor het tot stand brengen van een verbinding tussen Workfront Fusion en AEM Forms is het volgende noodzakelijk:

* Een geldige [Workfront- en Workfront Fusion-licentie](https://experienceleague.adobe.com/docs/workfront/using/adobe-workfront-fusion/get-started-with-workfront-fusion/license-automation-vs-integration.html).
* Een AEM gebruiker met toegangsrecht [Dev Console](https://my.cloudmanager.adobe.com/) tot [winnen de de dienstgeloofsbrieven terug](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html).

## AEM Forms integreren met Adobe Workfront Fusion

### 1. Een Workfront-scenario maken {#workflow-scenario}

Voer de volgende stappen uit om een Workfront-scenario te maken:

1. [Een scenario maken](#create-scenario)
1. [Een webhaak toevoegen aan een scenario](#add-webhook)
1. [Een verbinding met een webhaak toevoegen](#add-connection)

#### Een scenario maken {#create-scenario}

Een scenario maken:
1. Aanmelden bij uw [Workfront Fusion-account](https://app-qa.workfrontfusion.com/).
1. Klikken **[!UICONTROL Scenarios]** ![Pictogram Delen](/help/forms/assets/Smock_ShareAndroid_18_N.svg) in het linkerdeelvenster.
1. Klikken **[!UICONTROL Create a new scenario]** rechtsboven op de pagina. Op het scherm verschijnt een pagina waarop u een nieuw scenario kunt maken.
1. Selecteren **[!UICONTROL New scenario]** in de linkerbovenhoek van de pagina en typ een juiste naam voor het scenario.
1. Klik op het vraagteken en controleer of u de eerste module toevoegt als **[!UICONTROL AEM Forms]**.

   ![Een AEM Forms-module toevoegen](/help/forms/assets/workfront-aemforms.png)

   De **[!UICONTROL Watch for Form Events]** wordt weergegeven.

   >[!NOTE]
   >
   > Het is verplicht de eerste module toe te voegen als **[!UICONTROL AEM Forms]**.

1. Selecteer de **[!UICONTROL Watch for Form Events]** verschijnt een venster waarin u een webhaak kunt toevoegen.

#### Webhaak toevoegen {#add-webhook}

![Webhaak toevoegen](/help/forms/assets/workfront-add-webhook.png)

Een webhaak toevoegen:

1. Klikken **[!UICONTROL Add]** en **[!UICONTROL Add a webhook]** wordt weergegeven.
1. Geef een naam voor een webhaak op.

   >[!NOTE]
   >
   > U wordt aangeraden de naam van uw webhaak zorgvuldig te kiezen, aangezien de opgegeven naam van de webhaak in het AEM wordt weergegeven.

1. Klikken **[!UICONTROL Add]** om nieuwe verbinding toe te voegen. De **[!UICONTROL Create a Connection]** wordt weergegeven.

#### Een verbinding met een webhaak toevoegen {#add-connection}

![Een verbinding toevoegen](/help/forms/assets/workfront-add-connection.png)

Een verbinding toevoegen:

1. Geef een **[!UICONTROL Connection Name]** in de **[!UICONTROL Create a Connection]** in.

1. Selecteren **Omgeving** en **Type** in de vervolgkeuzelijst.

1. Voer de **Instance-URL**.

   >[!NOTE]
   >
   > Instance-URL is het unieke webadres dat verwijst naar een specifieke AEM Forms-instantie.

   U kunt de [de dienstgeloofsbrieven van de console van de Ontwikkelaar](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html) vereist om een verbinding te maken.

1. Vervangen `ims-na1.adobelogin.com` in de **IMS-eindpunt** met de waarde van **imsEndpoint** van de de dienstgeloofsbrieven in de console van de Ontwikkelaar.

   >[!NOTE]
   >
   > De `https://` in de **IMS-eindpunt** tekstvak tijdens toevoegen van `imsEndpoint` URL.

1. Geef de volgende waarden op in het dialoogvenster **[!UICONTROL Create a Connection]** dialoogvenster:
   * Opgeven **Client-id** met waarde van **clientId** van de de dienstgeloofsbrieven in de console van de Ontwikkelaar.
   * Opgeven **Clientgeheim** met waarde van **clientSecret** van de de dienstgeloofsbrieven in de console van de Ontwikkelaar.
   * Opgeven **Technisch account-id**  met waarde van **id** van de de dienstgeloofsbrieven in de console van de Ontwikkelaar.
   * Opgeven **Org-id**  met waarde van **org** van de de dienstgeloofsbrieven in de console van de Ontwikkelaar.
   * **Metabereiken**  met waarde van **metafoons** van de de dienstgeloofsbrieven in de console van de Ontwikkelaar.
   * **Persoonlijke toetsen**  met waarde van **privateKey** van de de dienstgeloofsbrieven in de console van de Ontwikkelaar.

   >[!NOTE]
   >
   >* Voor **Persoonlijke sleutel**, verwijderen `\r\n` van de waarde.
   >  Als de waarde van de persoonlijke sleutel bijvoorbeeld:
   >`\r\nIJAVO8GDYAOZ9jMA0GCSqGSIb3DQEBCwUAMDAxL\r\nMy1lMTUxODMxLWNtc3RnLWludGVncmF0aW9uLTAw`en vervolgens na het verwijderen van de `\r\n` bij de persoonlijke sleutel ziet de sleutel er als volgt uit, waarbij beide waarden op een aparte regel worden weergegeven:
   >
   >   `IJAVO8GDYAOZ9jMA0GCSqGSIb3DQEBCwUAMDAxL`
   >
   >   `My1lMTUxODMxLWNtc3RnLWludGVncmF0aW9uLTAw`
   > 
   >* U kunt ook een persoonlijke sleutel of certificaat ophalen uit het bestand door de optie **Extraheren** knop.

1. Klikken **Doorgaan**.

   De gemaakte verbinding wordt weergegeven in de vervolgkeuzelijst van het dialoogvenster **[!UICONTROL Connection]** in de **[!UICONTROL Add a webhook]** in.

1. De gemaakte verbinding selecteren **[!UICONTROL Connection]** in de vervolgkeuzelijst.
1. Klik op **[!UICONTROL Save]**.
1. Klikken **[!UICONTROL OK]** en sla de wijzigingen voor het scenario op.
1. Als u het scenario wilt activeren, klikt u op de schakelknop AAN/UIT in de scenario-editor.

>[!NOTE]
>
> Als u het Workfront-scenario niet activeert, wordt het verzenden van het formulier niet gedetecteerd. Als u de actie Verzenden instelt op Workfront, resulteert dit in een mislukte verzending.

### 2. De verzendactie van een adaptief formulier voor Workfront Fusion configureren

U kunt de verzendactie voor Workfront Fusion configureren voor:
* [Nieuwe adaptieve Forms](#new-af-submit-action)
* [Bestaande adaptieve formulieren](#existing-af-submit-action)

#### Verzendactie voor nieuw adaptief formulier voor Workfront Fusion configureren {#new-af-submit-action}

Verzendactie van nieuw adaptief formulier voor Workfront Fusion configureren:

1. Meld u aan bij uw AEM.
1. Ga naar **[!UICONTROL Forms]** > **[!UICONTROL Forms and Documents]** > **[!UICONTROL Create]** > **[!UICONTROL Adaptive Form]**. De **[!UICONTROL Create Form]** wordt weergegeven.
1. Selecteer een adaptieve formuliersjabloon in het menu **[!UICONTROL Source]** tab.
1. Selecteer een thema in het menu **[!UICONTROL Style]** tab.

   ![Handeling verzenden voor Workfront Fusion](/help/forms/assets/workfront-scenario-new-af.png)

1. Selecteer de **[!UICONTROL Invoke a WorkFront Fusion Scenario]** van de **[!UICONTROL Submission]** tab.
1. Selecteer de gemaakte webhaak in het menu **[!UICONTROL Options]** in de **[!UICONTROL Properties]** venster.

   >[!NOTE]
   >
   > De naam van de webhaak van het Workfront-scenario wordt weergegeven in het dialoogvenster **Opties** vervolgkeuzelijst.

1. Klik op **[!UICONTROL Create]**.
1. Geef de naam voor het nieuwe adaptieve formulier op en klik op **[!UICONTROL Create]**.

#### Verzendactie van bestaand adaptief formulier voor Workfront Fusion configureren {#existing-af-submit-action}

Verzendactie van bestaand adaptief formulier voor Workfront Fusion configureren:

1. Meld u aan bij uw AEM.
1. Ga naar **[!UICONTROL Forms]** > **[!UICONTROL Forms and Documents]**.
1. Selecteer een adaptief formulier en open het formulier in de bewerkingsmodus.
1. Open de Inhoudsbrowser en selecteer de **[!UICONTROL Guide Container]** van uw adaptieve formulier.
1. Klik op de eigenschappen van de container van de hulplijn ![Eigenschappen van hulplijnen](/help/forms/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer wordt geopend.

   ![Handeling verzenden voor Workfront Fusion](/help/forms/assets/workfront-scenario-existing-af.png)

1. Open de **[!UICONTROL Submission]** tab.
1. Selecteer de **[!UICONTROL Submit action]** als **[!UICONTROL Invoke a WorkFront Fusion Scenario]**
1. Selecteren **[!UICONTROL Workfront Fusion scenario]** in de vervolgkeuzelijst.
1. Klik op **[!UICONTROL Done]**.

## Aanbevolen procedures {#best-practices}

* U wordt aangeraden de naam van uw webhaak zorgvuldig te kiezen, omdat er geen manier is om de naam van het scenario op te halen bij het AEM. Als u de naam van de webhaak in de toekomst wijzigt, wordt deze niet meer weergegeven in de vervolgkeuzelijst Handeling voor verzenden van AEM Forms.
* Een scenario kan veelvoudige webhaakverbindingen hebben maar tegelijkertijd is slechts één webhaakverbinding actief. U wordt aangeraden de ontkoppelde webhaak te verwijderen, zodat deze niet wordt weergegeven in de vervolgkeuzelijst Handeling verzenden van AEM Forms.

<!-- During testing or development of Workfront, add the Author URL to the instance URL. However, when deploying Workfront Fusion in a production environment, it is recommended to replicate the scenario URLs for the Publish instance. -->

## Verwante artikelen

{{af-submit-action}}