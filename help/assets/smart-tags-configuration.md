---
title: Verbeterde slimme tags
description: U kunt contextafhankelijke en beschrijvende bedrijfstags toepassen met de AI- en ML-service van Adobe Sensei om de detectie van middelen en de snelheid van inhoud te verbeteren.
contentOwner: AG
translation-type: tm+mt
source-git-commit: bf7bb91dd488f39181a08adc592971d6314817de
workflow-type: tm+mt
source-wordcount: '882'
ht-degree: 8%

---


# Experience Manager configureren voor slimme tags van elementen {#configure-aem-for-smart-tagging}

Door elementen te labelen met een woordenschat die door de taxonomie wordt bepaald, kunt u de elementen eenvoudig herkennen en ophalen door zoekopdrachten op basis van tags. Adobe biedt slimme tags die gebruikmaken van algoritmen voor kunstmatige intelligentie en het leren van machines om afbeeldingen op te leiden. Slimme tags gebruiken een kunstmatig intelligentieframework van [Adobe Sensei](https://www.adobe.com/sensei/experience-cloud-artificial-intelligence.html) om het algoritme voor beeldherkenning op te leiden voor uw tagstructuur en bedrijfscatonomie.

De functie Slimme tags kan als een invoegtoepassing worden aangeschaft [!DNL Experience Manager]. Nadat u de aankoop hebt gedaan, wordt een e-mail verzonden naar de beheerder van uw organisatie met een koppeling naar de Adobe I/O. De beheerder heeft toegang tot de koppeling om de slimme tags te integreren met [!DNL Experience Manager] gebruik van Adobe I/O.

<!-- TBD: 
1. Can a similar flowchart be created about how training works in CS? ![flowchart](assets/flowchart.gif)
2. Is there a link to buy SCS or initiate a sales call.
3. Keystroke all steps and check all screenshots.
4. Post-GA, if time permits, create a video.
-->

## Integreren met Adobe I/O {#aio-integration}

Voordat u de afbeeldingen kunt voorzien van tags met behulp van SCS, moet u ze integreren [!DNL Adobe Experience Manager] met de service Slimme tags aan de hand van Adobe I/O. Aan de achterkant verifieert de [!DNL Experience Manager] server uw servicegegevens met de Adobe I/O-gateway voordat uw verzoek naar de service wordt doorgestuurd.

* Creeer een configuratie binnen [!DNL Experience Manager] om een openbare sleutel te produceren. Overheidscertificaat verkrijgen voor OAuth-integratie.
* Maak een integratie in Adobe I/O en upload de gegenereerde openbare sleutel.
* Configureer uw [!DNL Experience Manager] instantie met behulp van de API-sleutel en andere referenties van Adobe I/O.
* Schakel eventueel automatische labeling in bij het uploaden van elementen.

### Vereisten voor Adobe I/O-integratie {#prerequisite-for-aio-integration}

Voordat u de slimme tags kunt gebruiken, moet u het volgende doen om een integratie in de Adobe I/O te maken:

* Een Adobe-id-account met beheerdersrechten voor de organisatie.
* De slimme tags zijn ingeschakeld voor uw organisatie.

### Obtain a public certificate {#obtain-public-certificate}

Met een openbaar certificaat kunt u uw profiel verifiëren op Adobe I/O.

1. Ga in de [!DNL Experience Manager] gebruikersinterface naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Legacy Cloud Services]**.

1. On the Cloud Services page, click **[!UICONTROL Configure Now]** under **[!UICONTROL Assets Smart Tags]**.

1. Geef in het **[!UICONTROL Create Configuration]** dialoogvenster een titel en naam op voor de configuratie Slimme tags. Klik op **[!UICONTROL Create]**.

1. Gebruik de volgende waarden in het **[!UICONTROL AEM Smart Content Service]** dialoogvenster:

   **[!UICONTROL Service URL]**: `https://mc.adobe.io/marketingcloud/smartcontent`

   **[!UICONTROL Authorization Server]**: `https://ims-na1.adobelogin.com`

   Laat de overige velden voorlopig leeg (later te verstrekken). Klik op **[!UICONTROL OK]**.

   ![Het dialoogvenster Experience Manager Smart Content Service om de contentservice URL te bieden](assets/aem_scs.png)

1. Klik **[!UICONTROL Download Public Certificate for OAuth Integration]** en download het openbare certificaatbestand `AEM-SmartTags.crt`.

   ![Instellingen gemaakt voor de service voor slimme tags](assets/download_link.png)

### Opnieuw configureren als een certificaat verloopt {#certrenew}

Wanneer het certificaat verloopt, wordt het niet meer vertrouwd. Voer de volgende stappen uit om een nieuw certificaat toe te voegen. U kunt een verlopen certificaat niet vernieuwen.

1. Log in your [!DNL Experience Manager] deployment as an administrator. Klik op **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**.

1. Zoek en klik op **[!UICONTROL dam-update-service]** Gebruiker. Klik op **[!UICONTROL Keystore]** tabblad.
1. Verwijder het bestaande **[!UICONTROL similaritysearch]** sleutelarchief met het verlopen certificaat. Klik op **[!UICONTROL Save & Close]**.

   ![Bestaande vermelding voor zoeken op basis van overeenkomst in sleutelarchief verwijderen om een nieuw beveiligingscertificaat toe te voegen](assets/smarttags_delete_similaritysearch_keystore.png)

   *Afbeelding: Verwijder het bestaande`similaritysearch`item in het sleutelarchief om een nieuw beveiligingscertificaat toe te voegen.*

1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Legacy Cloud Services]**. Klik op **[!UICONTROL Asset Smart Tags]** > **[!UICONTROL Show Configuration]** > **[!UICONTROL Available Configurations]**. Klik op de gewenste configuratie.

1. Als u een openbaar certificaat wilt downloaden, klikt u op **[!UICONTROL Download Public Certificate for OAuth Integration]**.

1. Open [https://console.adobe.io](https://console.adobe.io) en navigeer naar de bestaande service in het project. Upload het nieuwe certificaat. Zie de instructies in Adobe I/O-integratie [](#create-aio-integration)maken voor meer informatie.

### Een integratie maken {#create-aio-integration}

Als u API&#39;s met slimme tags wilt gebruiken, maakt u een integratie in Adobe I/O om API-sleutel, technische account-id, organisatie-id en clientgeheim te genereren.

1. Ga naar [https://console.adobe.io](https://console.adobe.io/).
1. Selecteer de aangewezen rekening en verifieer dat de bijbehorende organisatierol systeembeheerder is. Maak een project of open een bestaand project. Voor de projectpagina, klik **[!UICONTROL Add API]**.
1. Selecteer op de **[!UICONTROL Add an API]** pagina **[!UICONTROL Experience Cloud]** en selecteer **[!UICONTROL Smart Content]**. Klik op **[!UICONTROL Continue]**.
1. Selecteer op de volgende pagina **[!UICONTROL New integration]**. Klik op **[!UICONTROL Continue]**.
1. Voor de **[!UICONTROL Integration Details]** pagina, specificeer een naam voor de integratiesgateway en voeg een beschrijving toe.
1. Upload in het **[!UICONTROL Public keys certificates]** bestand `AEM-SmartTags.crt` dat u hierboven hebt gedownload.
1. Klik op **[!UICONTROL Create Integration]**.
1. Klik op **[!UICONTROL Continue to integration details]** om de integratiegegevens weer te geven.

   ![Op het tabblad Overzicht kunt u de informatie bekijken die voor integratie is opgegeven.](assets/integration_details.png)

### Slimme tags configureren {#configure-smart-content-service}

Als u de integratie wilt configureren, gebruikt u de waarden Technical Account ID, Organization ID, Client Secret, Authorization Server en API-sleutelvelden van de Adobe I/O-integratie. Door een cloud-configuratie met slimme tags te maken, kunnen API-aanvragen van de [!DNL Experience Manager] instantie worden geverifieerd.

1. Navigeer in [!DNL Experience Manager]naar **[!UICONTROL Tools > Cloud Service > Legacy Cloud Services]** om de [!UICONTROL Cloud Services] console te openen.
1. Open onder de **[!UICONTROL Assets Smart Tags]** sectie de configuratie die hierboven is gemaakt. Klik op de pagina met service-instellingen **[!UICONTROL Edit]**.
1. Gebruik in het dialoogvenster **[!UICONTROL AEM Smart Content Service]** de vooraf ingevulde waarden voor de velden **[!UICONTROL Service URL]** en **[!UICONTROL Authorization Server]**.
1. Voor de velden **[!UICONTROL API Key]**, **[!UICONTROL Technical Account Id]**, **[!UICONTROL Organization Id]** en **[!UICONTROL Client Secret]** gebruikt u de hierboven gegenereerde waarden.

### De configuratie valideren {#validate-the-configuration}

Nadat u de configuratie hebt voltooid, kunt u een JMX MBean gebruiken om de configuratie te bevestigen. Voer de volgende stappen uit om te valideren.

1. Open uw [!DNL Experience Manager] server op `https://[aem_server]:[port]`.

1. Ga naar **[!UICONTROL Tools > Operations > Web Console]** om de console te openen OSGi. Klik op **[!UICONTROL Main > JMX]**.
1. Klik op **[!UICONTROL com.day.cq.dam.similaritysearch.internal.impl]**. Het wordt geopend **[!UICONTROL SimilaritySearch Miscellaneous Tasks.]**.
1. Klik op **[!UICONTROL validateConfigs()]**. In the **[!UICONTROL Validate Configurations]** dialog, click **[!UICONTROL Invoke]**.

   Het validatieresultaat wordt in hetzelfde dialoogvenster weergegeven.

## Slimme tags toepassen op nieuw geüploade elementen inschakelen (optioneel) {#enable-smart-tagging-for-uploaded-assets}

1. Ga [!DNL Experience Manager]naar **[!UICONTROL Tools > Workflow > Models]**.
1. Selecteer op de pagina **[!UICONTROL Workflow Models]** het **[!UICONTROL DAM Update Asset]**-workflowmodel.
1. Klik op **[!UICONTROL Edit]** de werkbalk.
1. Vouw het zijpaneel uit om de stappen weer te geven. Sleep de stap **[!UICONTROL Smart Tag Asset]** die beschikbaar is in de DAM-workflowsectie en plaats deze na de stap **[!UICONTROL Process Thumbnails]**.

   ![De stap Slim tagelement toevoegen na de stap met de procesminiaturen in de DAM Update Asset-workflow](assets/chlimage_1-105.png)

   *Afbeelding: Voeg de stap Slimme tag-elementen toe na de stap met de procesminiaturen in de DAM-workflow Element bijwerken.*

1. Open de stap die u wilt configureren. Zorg er onder **[!UICONTROL Advanced Settings]** dat de **[!UICONTROL Handler Advance]** optie is geselecteerd.

   ![Het plaatsen voor manager om aan de volgende stap in het werkschema te gaan.](assets/smart-tags-workflow-handler-setting.png)

1. Selecteer op het **[!UICONTROL Arguments]** tabblad **[!UICONTROL Ignore Errors]** of de workflow fouten bij het voorspellen van tags moet negeren. Als u elementen wilt labelen wanneer ze worden geüpload, ongeacht of slimme tags zijn ingeschakeld in mappen, selecteert u **[!UICONTROL Ignore Smart Tag Flag]**.

1. Klik **[!UICONTROL OK]** om de processtap te sluiten en sla de workflow op. Klik op **[!UICONTROL Sync]**.

>[!MORELIKETHIS]
>
>* [Elementen labelen met behulp van intelligente service](smart-tags.md)

