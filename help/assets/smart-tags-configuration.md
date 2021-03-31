---
title: Verbeterde slimme tags
description: U kunt contextafhankelijke en beschrijvende bedrijfstags toepassen met de AI- en ML-service van Adobe Sensei om de detectie van assets en de snelheid van content te verbeteren.
contentOwner: AG
feature: Slimme tags, labelen
role: Beheerder
translation-type: tm+mt
source-git-commit: 8093f6cec446223af58515fd8c91afa5940f9402
workflow-type: tm+mt
source-wordcount: '889'
ht-degree: 82%

---


# [!DNL Experience Manager] configureren voor slimme labeling van elementen {#configure-aem-for-smart-tagging}

Wanneer assets zijn getagd op basis van een specifieke taxonomie, kunt u ze eenvoudig herkennen en ophalen door te zoeken op basis van tags. Adobe biedt slimme tags die gebruikmaken van algoritmen voor kunstmatige intelligentie en machinaal leren om afbeeldingen op te leiden. De Smart Tags-functie gebruikt een AI-framework van [Adobe Sensei](https://www.adobe.com/nl/sensei/experience-cloud-artificial-intelligence.html) om de algoritmen voor beeldherkenning te &#39;trainen&#39; op basis van uw tagstructuur en bedrijfstaxonomie.

De Smart Tags-functie voor slimme tags kan als invoegtoepassing worden aangeschaft [!DNL Experience Manager]. Nadat u de aankoop hebt gedaan, wordt een e-mail verzonden naar de beheerder van uw organisatie met een koppeling naar Adobe Developer Console. De beheerder opent de koppeling om de Smart Tags-functie met behulp van Adobe Developer Console te integreren met [!DNL Experience Manager].

<!-- TBD: 
1. Can a similar flowchart be created about how training works in CS? ![flowchart](assets/flowchart.gif)
2. Is there a link to buy SCS or initiate a sales call.
3. Keystroke all steps and check all screenshots.
-->

>[!IMPORTANT]
>
>Als uw [!DNL Experience Manager Assets]-implementaties zijn gemaakt na [August 2020 release](/help/release-notes/release-notes-cloud/2020/release-notes-2020-8-0.md#assets), is [!DNL Adobe Developer Console] standaard geïntegreerd. De functie helpt de functionaliteit voor slimme tags sneller te configureren. Voor de oudere plaatsingen, kunnen de beheerders de integratie manueel vormen gebruikend de volgende instructies.

## Integreren met Adobe Developer Console {#aio-integration}

Voordat u afbeeldingen kunt voorzien van tags met gebruik van SCS, moet u [!DNL Adobe Experience Manager] integreren met de Smart Tags-service via Adobe Developer Console. Bij de back-end verifieert de [!DNL Experience Manager]-server uw servicegegevens met de Adobe Developer Console-gateway voordat uw aanvraag naar de service wordt doorgestuurd.

* Maak een configuratie in [!DNL Experience Manager] om een openbare sleutel te genereren. [Verkrijg een openbaar certificaat voor OAuth-integratie.](#obtain-public-certificate)
* [Maak een integratie in Adobe Developer Console en upload de gegenereerde openbare sleutel.](#create-aio-integration)
* [Configureer Smart Tags](#configure-smart-content-service) in uw [!DNL Experience Manager] instantie met de API-sleutel en andere referenties van Adobe Developer Console.
* [Test de configuratie](#validate-the-configuration).
* [Configureer opnieuw na het verlopen van het certificaat](#certrenew).

### Vereisten voor Adobe Developer Console-integratie {#prerequisite-for-aio-integration}

Voordat u de Smart Tags-functie kunt gebruiken, moet u de volgende stappen uitvoeren om een integratie te maken in Adobe Developer Console:

* Een Adobe ID-account met beheerdersrechten voor de organisatie.
* De functie Smart Tags is ingeschakeld voor uw organisatie.

### Een openbaar certificaat verkrijgen {#obtain-public-certificate}

Met een openbaar certificaat kunt u uw profiel verifiëren op Adobe Developer Console. U maakt een certificaat vanuit [!DNL Experience Manager].

1. Ga in de [!DNL Experience Manager]-gebruikersinterface naar **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**.

1. Ga naar de pagina [!UICONTROL Adobe IMS Configurations] en klik op **[!UICONTROL Create]**. In het menu **[!UICONTROL Cloud Solution]** selecteert u **[!UICONTROL Smart Tags]**.

1. Selecteer **[!UICONTROL Create new certificate]**. Geef een naam op en klik op **[!UICONTROL Create certificate]**. Klik op **[!UICONTROL OK]**.

1. Klik op **[!UICONTROL Download Public Key]**.

   ![[!DNL Experience Manager] Slimme tags maken openbare sleutel](assets/aem_smarttags-config1.png)

### Een integratie maken {#create-aio-integration}

Om de Smart Tags-functie te gebruiken moet u een integratie in Adobe Developer Console maken en vervolgens een API-sleutel, technische account-id, organisatie-id en clientgeheim genereren.

1. Open [https://console.adobe.io](https://console.adobe.io/) in uw browser. Selecteer het gewenste account en verifieer dat de bijbehorende organisatierol is ingesteld op systeembeheerder.
1. Maak een project een geef het de gewenste naam. Klik op **[!UICONTROL Add API]**.
1. Selecteer op de pagina **[!UICONTROL Add an API]** **[!UICONTROL Experience Cloud]** en selecteer **[!UICONTROL Smart Content]**. Klik op **[!UICONTROL Next]**.
1. Selecteer **[!UICONTROL Upload your public key]**. Geef het certificaatbestand op dat u hebt gedownload van [!DNL Experience Manager]. Er wordt een [!UICONTROL Public key(s) uploaded successfully]-bericht weergegeven. Klik op **[!UICONTROL Next]**.
1. [!UICONTROL Create a new Service Account (JWT) credential] De pagina toont de openbare sleutel voor de de dienstrekening. Klik op **[!UICONTROL Next]**.
1. Ga naar de pagina **[!UICONTROL Select product profiles]** en selecteer **[!UICONTROL Smart Content Services]**. Klik op **[!UICONTROL Save configured API]**. De pagina die verschijnt biedt meer informatie over de configuratie. Laat deze pagina open om deze waarden in [!DNL Experience Manager] te kopiëren en toe te voegen wanneer het verder vormen van Slimme Markeringen in [!DNL Experience Manager].

   ![Op het tabblad Overview kunt u de informatie bekijken die is opgegeven voor de integratie.](assets/integration_details.png)

### De functie Smart Tags configureren {#configure-smart-content-service}

Om de integratie te configureren gebruikt u de waarden in de velden Payload, Client Secret, Authorization Server en API Key uit de Adobe Developer Console-integratie.

1. Ga in de [!DNL Experience Manager]-gebruikersinterface naar **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**.
1. Ga naar de pagina **[!UICONTROL Adobe IMS Technical Account Configuration]** en geef de gewenste **[!UICONTROL Title]** op.
1. Geef in het veld **[!UICONTROL Authorization Server]** de `https://ims-na1.adobelogin.com`-URL op.
1. Geef in het veld **[!UICONTROL API Key]** de waarde **[!UICONTROL Client ID]** op van [!DNL Adobe Developer Console].
1. Geef in het veld **[!UICONTROL Client Secret]** de waarde **[!UICONTROL Client Secret]** op van [!DNL Adobe Developer Console]. Klik op de optie **[!UICONTROL Retrieve Client Secret]** om deze weer te geven.
1. Klik in uw project in [!DNL Adobe Developer Console] op **[!UICONTROL Service Account (JWT)]** in de linkermarge. Klik op het tabblad **[!UICONTROL Generate JWT]**. Klik op **[!UICONTROL Copy]** om de weergegeven **[!UICONTROL JWT Payload]** te kopiëren. Geef deze waarde op in het veld **[!UICONTROL Payload]** in [!DNL Experience Manager]. Klik op **[!UICONTROL Create]**.

### De configuratie valideren {#validate-the-configuration}

Nadat u de configuratie hebt voltooid, volgt u deze stappen om de configuratie te bevestigen.

1. Ga in de [!DNL Experience Manager]-gebruikersinterface naar **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**.

1. Selecteer de Smart Tags-configuratie. Klik op **[!UICONTROL Check Health]** op de werkbalk. Klik op **[!UICONTROL Check]**. Een dialoogvenster met een [!UICONTROL Healthy configuration]-bericht bevestigt dat de configuratie goed functioneert.

![Smart Tags-configuratie valideren](assets/smart-tag-config-validation.png)

### Opnieuw configureren als een certificaat verloopt {#certrenew}

Wanneer het certificaat verloopt, wordt het niet meer vertrouwd. Voer de volgende stappen uit om een certificaat toe te voegen. U kunt een verlopen certificaat niet verlengen.

1. Meld u als beheerder aan bij uw [!DNL Experience Manager]-implementatie. Klik op **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**.

1. Zoek en klik op **[!UICONTROL dam-update-service]**-gebruiker. Klik op het tabblad **[!UICONTROL Keystore]**. 
1. Verwijder het bestaande **[!UICONTROL similaritysearch]**-sleutelarchief met het verlopen certificaat. Klik op **[!UICONTROL Save & Close]**.

   ![Bestaande zoekfunctie voor gelijkenis verwijderen in Keystore om een nieuw beveiligingscertificaat toe te voegen](assets/smarttags_delete_similaritysearch_keystore.png)

   *Afbeelding: Verwijder het bestaande  `similaritysearch` item in het sleutelarchief om een beveiligingscertificaat toe te voegen.*

1. Ga in de [!DNL Experience Manager]-gebruikersinterface naar **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**. Open de beschikbare Smart Tags-configuratie. Als u een openbaar certificaat wilt downloaden, klikt u op **[!UICONTROL Download Public Certificate]**.

1. Open [https://console.adobe.io](https://console.adobe.io) en navigeer naar de bestaande service in het project. Upload en configureer het nieuwe certificaat. Zie de instructies in [Adobe Developer Console-integratie maken](#create-aio-integration) voor meer informatie over de configuratie.

## Automatisch labelen inschakelen wanneer elementen worden geüpload (optioneel) {#enable-smart-tagging-for-uploaded-assets}

1. Ga in [!DNL Experience Manager] naar **[!UICONTROL Tools > Workflow > Models]**.
1. Selecteer op de pagina **[!UICONTROL Workflow Models]** het **[!UICONTROL DAM Update Asset]**-workflowmodel.
1. Klik op **[!UICONTROL Edit]** op de werkbalk.
1. Vouw het zijpaneel uit om de stappen weer te geven. Sleep de stap **[!UICONTROL Smart Tag Asset]** die beschikbaar is in de DAM-workflowsectie en plaats deze na de stap **[!UICONTROL Process Thumbnails]**.

   ![De stap Asset met slimme tag toevoegen na de stap met de procesminiaturen in de DAM Update Asset-workflow](assets/chlimage_1-105.png)

   *Afbeelding: De stap Asset met slimme tag toevoegen na de stap met de procesminiaturen in de DAM Update Asset-workflow*

1. Open de stap die u wilt configureren. Ga naar **[!UICONTROL Advanced Settings]** en controleer of de optie **[!UICONTROL Handler Advance]** is ingeschakeld.

   ![Instelling om naar de volgende stap in de workflow te gaan.](assets/smart-tags-workflow-handler-setting.png)

1. Ga naar het tabblad **[!UICONTROL Arguments]** en schakel de optie **[!UICONTROL Ignore Errors]** in als u wilt dat de workflow fouten negeert bij het voorspellen van tags. Als u assets tijdens het uploaden wilt voorzien van een tag (ongeacht of slimme tags zijn ingeschakeld voor mappen), moet u de optie **[!UICONTROL Ignore Smart Tag Flag]** inschakelen.

1. Klik op **[!UICONTROL OK]**. De processtap wordt gesloten. Sla de workflow op. Klik op **[!UICONTROL Sync]**.

>[!MORELIKETHIS]
>
>* [Assets voorzien van een tag met een intelligente service](smart-tags.md)

