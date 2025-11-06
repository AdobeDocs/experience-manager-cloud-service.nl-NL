---
title: Integratie van Adobe Workfront Fusion met AEM Forms-verzending
description: Met Adobe Workfront Fusion kunt u zich richten op nieuwe taken in plaats van zich te richten op herhaalde taken. U kunt Adobe Workfront Fusion via Formulierverzending verbinden met een adaptief formulier.
keywords: Een adaptief formulier verzenden naar Adobe Workfront Fusion, Integration of Adobe Workfront Fusion with AEM Forms Submission, Adobe Workfront Fusion with AEM Forms, Workfront Fusion with AEM Forms, Connect Workfront Fusion to AEM Forms, AEM Forms en Workfront Fusion, How to connect Workfront Fusion with AEM Forms, Connect Workfront Fusion to a Form?
topic-tags: author, developer
feature: Adaptive Forms, Foundation Components, Edge Delivery Services, Core Components
role: Admin, User
exl-id: d3efb450-a879-40ae-8958-0040f99bdafc
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1227'
ht-degree: 1%

---

# Een adaptief formulier verzenden naar Adobe Workfront Fusion

<span class="preview"> De functie is beschikbaar in het programma voor vroege adoptie. U kunt vanaf uw officiële e-mailadres naar aem-forms-ea@adobe.com schrijven om deel te nemen aan het programma voor vroege adoptie en toegang tot de functie te vragen. </span>

[ de Fusie van Adobe Workfront ](https://experienceleague.adobe.com/docs/workfront/using/adobe-workfront-fusion/get-started-with-workfront-fusion/workfront-fusion-overview.html) automatiseert het proces om de zelfde taken, zoals de werkschema&#39;s van de documentgoedkeuring, e-mailfiltreren en het sorteren te herhalen, toestaand u om zich op nieuwe taken in plaats van terugkomende degenen te concentreren. Adobe Workfront Fusion bevat meerdere scenario&#39;s. Een scenario bestaat uit een reeks modules die gegevensoverdracht tussen toepassingen en Webdiensten uitvoert. In een scenario, voegt u diverse stappen (modules) toe om een taak te automatiseren.

Met Workfront Fusion kunt u bijvoorbeeld een scenario maken voor het verzamelen van gegevens met Adaptief formulier, het verwerken van de gegevens en het verzenden van de gegevens naar een gegevensopslagruimte voor archivering. Wanneer een scenario is ingesteld, voert Workfront Fusion automatisch de taken uit wanneer een gebruiker een formulier invult en de gegevensopslag naadloos bijwerkt.

AEM Forms as a Cloud Service beschikt over een OOTB-connector om een adaptief formulier aan te sluiten en in te dienen bij Adobe Workfront Fusion. Het verzenden van een formulier naar Adobe Workfront Fusion kan verschillende voordelen bieden:

* Zo konden formulierverzendgegevens naadloos worden overgedragen naar Workfront Fusion-workflows.
* Hiermee kunt u verschillende taken automatiseren die worden veroorzaakt door het verzenden van formulieren. Dit kan het in werking stellen van projecten omvatten, het toewijzen van taken aan specifieke teamleden, het verzenden van berichten, en het bijwerken van projectstatus-allen zonder handinterventie.
* Alle formulierverzendingen die in Workfront Fusion zijn vastgelegd, bieden één waarheidsbron voor projectgerelateerde informatie


<!--  AEM as a Cloud Service offers various out of the box submit actions for handling form submissions. You can learn more about these options in the [Adaptive Form Submit Action](/help/forms/configure-submit-actions-core-components.md)  article.-->

>[!VIDEO](https://video.tv.adobe.com/v/3427145/adaptive-forms-adobe-workfront-af-workfront-workfront-aem-forms/?quality=12&learn=on)

<span> Deze video is alleen van toepassing op Core Components. Voor de Componenten van de UE/Foundation, gelieve naar het artikel te verwijzen.</span>

## Vereisten om AEM Forms te integreren met Adobe Workfront Fusion {#prerequisites}

Voor het tot stand brengen van een verbinding tussen Workfront Fusion en AEM Forms is het volgende noodzakelijk:

* Een geldige [ Workfront en de vergunning van de Fusie van Workfront ](https://experienceleague.adobe.com/docs/workfront/using/adobe-workfront-fusion/get-started-with-workfront-fusion/license-automation-vs-integration.html).
* Een gebruiker van AEM met recht op toegang tot [ Dev Console ](https://my.cloudmanager.adobe.com/) om [ de de dienstgeloofsbrieven ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html) terug te winnen.

## AEM Forms integreren met Adobe Workfront Fusion

### &#x200B;1. Een Workfront-scenario maken {#workflow-scenario}

Voer de volgende stappen uit om een Workfront-scenario te maken:

1. [Een scenario maken](#create-scenario)
1. [Een webhaak toevoegen aan een scenario](#add-webhook)
1. [Een verbinding met een webhaak toevoegen](#add-connection)

#### Een scenario maken {#create-scenario}

Een scenario maken:

1. Teken in uw [ rekening van de Fusie van Workfront ](https://app-qa.workfrontfusion.com/).
1. Klik **[!UICONTROL Scenarios]** ![ pictogram van het Aandeel ](/help/forms/assets/Smock_ShareAndroid_18_N.svg) in het linkerpaneel.
1. Klik op **[!UICONTROL Create a new scenario]** rechtsboven op de pagina. Op het scherm verschijnt een pagina waarop u een nieuw scenario kunt maken.
1. Selecteer **[!UICONTROL New scenario]** in de linkerbovenhoek van de pagina en typ een juiste naam voor het scenario.
1. Klik op het vraagteken en controleer of u de eerste module als **[!UICONTROL AEM Forms]** toevoegt.

   ![ voeg een module van AEM Forms toe ](/help/forms/assets/workfront-aemforms.png)

   Het dialoogvenster **[!UICONTROL Watch for Form Events]** wordt weergegeven.

   >[!NOTE]
   >
   > Het is verplicht de eerste module toe te voegen als **[!UICONTROL AEM Forms]** .

1. Selecteer het dialoogvenster **[!UICONTROL Watch for Form Events]** en een venster om een webhaak toe te voegen.

#### Webhaak toevoegen {#add-webhook}

![ voeg een webhaak ](/help/forms/assets/workfront-add-webhook.png) toe

Een webhaak toevoegen:

1. Klik op **[!UICONTROL Add]** en er verschijnt een dialoogvenster **[!UICONTROL Add a webhook]** .
1. Geef een naam voor een webhaak op.

   >[!NOTE]
   >
   > U wordt aangeraden de naam van uw webhaak zorgvuldig te kiezen, zoals de opgegeven naam van de webhaak in het AEM-exemplaar wordt weergegeven.

1. Klik op **[!UICONTROL Add]** om een nieuwe verbinding toe te voegen. Het dialoogvenster **[!UICONTROL Create a Connection]** wordt weergegeven.

>[!NOTE]
>
> Zorg ervoor dat de Technische Rekening een lid van de **vorm-gebruikers** groep is; anders, ontbreekt het toevoegen van een webhaak.

#### Een verbinding met een webhaak toevoegen {#add-connection}

![ voeg een verbinding ](/help/forms/assets/workfront-add-connection.png) toe

Een verbinding toevoegen:

1. Geef een **[!UICONTROL Connection Name]** op in het dialoogvenster **[!UICONTROL Create a Connection]** .

1. Selecteer **Milieu** en **Type** van de drop-down lijst.

1. Ga **Instantie URL** in.

   >[!NOTE]
   >
   > Instance-URL is het unieke webadres dat verwijst naar een specifieke AEM Forms-instantie.

   U kunt de [ dienstgeloofsbrieven van de console van de Ontwikkelaar terugwinnen ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html) wordt vereist om een verbinding tot stand te brengen die.

1. Vervang `ims-na1.adobelogin.com` in het **IMS eindpunt** met de waarde van **imsEndpoint** van de de dienstgeloofsbrieven in de console van de Ontwikkelaar.

   >[!NOTE]
   >
   > Behoud `https://` in het **IMS eindpunt** textbox terwijl het toevoegen van `imsEndpoint` URL.

1. Geef de volgende waarden op in het dialoogvenster **[!UICONTROL Create a Connection]** :
   * Specificeer **identiteitskaart van de Cliënt** met waarde van **clientId** van de de dienstgeloofsbrieven in de console van de Ontwikkelaar.
   * Specificeer **Geheim van de Cliënt** met waarde van **clientSecret** van de de dienstgeloofsbrieven in de console van de Ontwikkelaar.
   * Specificeer **Technische identiteitskaart van de Rekening** met waarde van **identiteitskaart** van de de dienstgeloofsbrieven in de console van de Ontwikkelaar.
   * Specificeer **het Org identiteitskaart** met waarde van **org** van de de dienstgeloofsbrieven in de console van de Ontwikkelaar.
   * **de Scopes van Meta** met waarde van **metarealen** van de de dienstgeloofsbrieven in de console van de Ontwikkelaar.
   * **Privé Sleutels** met waarde van **privateKey** van de de dienstgeloofsbrieven in de console van de Ontwikkelaar.

   >[!NOTE]
   >
   >* Voor **Persoonlijke Sleutel**, verwijder `\r\n` uit zijn waarde.
   >  Als de waarde van de persoonlijke sleutel bijvoorbeeld:
   >`\r\nIJAVO8GDYAOZ9jMA0GCSqGSIb3DQEBCwUAMDAxL\r\nMy1lMTUxODMxLWNtc3RnLWludGVncmF0aW9uLTAw` ziet de sleutel er na het verwijderen van de `\r\n` uit de persoonlijke sleutel als volgt uit, waarbij beide waarden op een aparte regel worden weergegeven:
   >
   >   `IJAVO8GDYAOZ9jMA0GCSqGSIb3DQEBCwUAMDAxL`
   >
   >   `My1lMTUxODMxLWNtc3RnLWludGVncmF0aW9uLTAw`
   > 
   >* U hebt ook de optie om een privé sleutel of een certificaat van het dossier terug te winnen door de **Extraheren** knoop te selecteren.

1. Klik **verdergaan**.

   De gemaakte verbinding wordt weergegeven in de vervolgkeuzelijst van het dialoogvenster **[!UICONTROL Connection]** in het dialoogvenster **[!UICONTROL Add a webhook]** .

1. Selecteer de gemaakte verbinding **[!UICONTROL Connection]** in de vervolgkeuzelijst.
1. Klik op **[!UICONTROL Save]**.
1. Klik op **[!UICONTROL OK]** en sla de wijzigingen voor het scenario op.
1. Als u het scenario wilt activeren, klikt u op de schakelknop AAN/UIT in de scenario-editor.

>[!NOTE]
>
> Als u het Workfront-scenario niet activeert, wordt het verzenden van het formulier niet gedetecteerd. Als u de actie Verzenden instelt op Workfront, resulteert dit in een mislukte verzending.

### &#x200B;2. De verzendactie van een adaptief formulier voor Workfront Fusion configureren

>[!BEGINTABS]

>[!TAB  Component van de Stichting ]

Verzendactie van een adaptief formulier configureren op basis van Foundation Components for Workfront Fusion:

1. Open het Adaptief formulier voor bewerking en ga naar de sectie **[!UICONTROL Submission]** van de eigenschappen van de container van adaptieve formulieren.
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Submit Action]** de optie **[!UICONTROL Invoke a WorkFront Fusion Scenario]**.
   ![ voorlegt actie voor de Fusie van Workfront ](/help/forms/assets/workfront-fusion-fc.png)

1. Selecteer **[!UICONTROL Workfront Fusion scenario]** in de vervolgkeuzelijst.
1. Klik op **[!UICONTROL Done]**.


>[!TAB  Component van de Kern ]

Verzendactie configureren op basis van kerncomponenten voor Workfront Fusion:

1. Open de browser Inhoud en selecteer de component **[!UICONTROL Guide Container]** van het adaptieve formulier.
1. Klik de eigenschappen van de Container van de Gids ![ eigenschappen van de Gids ](/help/forms/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer wordt geopend.
1. Klik op de tab **[!UICONTROL Submission]** .
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Submit Action]** de optie **[!UICONTROL Invoke a WorkFront Fusion Scenario]**.

   ![ voorlegt actie voor de Fusie van Workfront ](/help/forms/assets/workfront-scenario-existing-af.png)
1. Selecteer **[!UICONTROL Workfront Fusion scenario]** in de vervolgkeuzelijst.
1. Klik op **[!UICONTROL Done]**.

>[!TAB  Universele Redacteur ]

Verzendactie configureren van een adaptief formulier dat is geschreven met de Universal Editor:

1. Open het adaptieve formulier voor bewerking.
1. Klik **uitgeven de uitbreiding van de Eigenschappen van de Vorm** op de redacteur.
Het **de dialoogvakje van de Eigenschappen van de Vorm** verschijnt.

   >[!NOTE]
   >
   > * Als u niet **ziet geef de Eigenschappen van de Vorm** pictogram in uw Universele interface van de Redacteur uit, laat **toe geef de 3} uitbreiding van de Eigenschappen van de Vorm {in Extension Manager uit.**
   > * Verwijs naar het [ artikel van de Hoogtepunten van de Eigenschap van 0} Extension Manager om te leren hoe te om uitbreidingen in of onbruikbaar te maken in de Universele Redacteur.](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions)

1. Klik **Verzending** lusje en selecteer **[!UICONTROL Invoke a WorkFront Fusion Scenario]** voorlegt actie.

   ![ voorlegt actie voor de Fusie van Workfront ](/help/forms/assets/workfront-fusion-ue.png)

1. Selecteer **[!UICONTROL Workfront Fusion scenario]** in de vervolgkeuzelijst.
1. Klik op **[!UICONTROL Save&Close]**.

>[!ENDTABS]

## Aanbevolen procedures {#best-practices}

* U wordt aangeraden de naam van uw webhaak zorgvuldig te kiezen, omdat er geen manier is om de naam van het scenario op te halen bij de AEM-instantie. Als u de naam van de webhaak in de toekomst wijzigt, wordt deze niet meer weergegeven in de vervolgkeuzelijst Handeling voor verzenden van AEM Forms.
* Een scenario kan veelvoudige webhaakverbindingen hebben maar tegelijkertijd is slechts één webhaakverbinding actief. U wordt aangeraden de ontkoppelde webhaak te verwijderen, zodat deze niet wordt weergegeven in de vervolgkeuzelijst Handeling verzenden van AEM Forms.

<!-- During testing or development of Workfront, add the Author URL to the instance URL. However, when deploying Workfront Fusion in a production environment, it is recommended to replicate the scenario URLs for the Publish instance. -->

## Verwante artikelen

{{af-submit-action}}