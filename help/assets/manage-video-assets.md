---
title: Video-elementen beheren
description: Upload, voorproef, annoteer, en publiceer videoactiva in  [!DNL Adobe Experience Manager].
contentOwner: AG
feature: Asset Management, Publishing, Collaboration, Video
role: User
exl-id: 91edce4a-dfa0-4eca-aba7-d41ac907b81e
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '4661'
ht-degree: 4%

---

# Video-elementen beheren {#manage-video-assets}

| [ Beste praktijken van het Onderzoek ](/help/assets/search-best-practices.md) | [ Beste praktijken van Meta-gegevens ](/help/assets/metadata-best-practices.md) | [ Content Hub ](/help/assets/product-overview.md) | [ Dynamic Media met mogelijkheden OpenAPI ](/help/assets/dynamic-media-open-apis-overview.md) | [ de ontwikkelaarsdocumentatie van AEM Assets ](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/managing-video-assets.html?lang=en) |
| AEM as a Cloud Service | Dit artikel |

De video-indeling is een essentieel onderdeel van digitale middelen van een organisatie. [!DNL Adobe Experience Manager] biedt geavanceerde aanbiedingen en functies om de volledige levenscyclus van uw video-elementen te beheren nadat deze zijn gemaakt.

Leer hoe u de video-elementen beheert en bewerkt in [!DNL Adobe Experience Manager Assets] . Videocodering en -transcodering, bijvoorbeeld MPEG-transcodering, is mogelijk met behulp van Procesprofielen verwerken en [!DNL Dynamic Media] -integratie. Zonder [!DNL Dynamic Media] licentie biedt [!DNL Experience Manager] basisondersteuning voor video&#39;s, zoals transcoderen met Mpeg, het uitnemen van voorvertoningsminiaturen voor de ondersteunde bestandsindelingen en een voorvertoning in de gebruikersinterface voor indelingen die rechtstreeks in de browser kunnen worden afgespeeld.

## Video-elementen uploaden en voorvertonen {#upload-and-preview-video-assets}

U kunt video-elementen van ondersteunde indeling uploaden en hiervan een voorvertoning weergeven in [!DNL Experience Manager Assets] .
<!-- It generates previews for video assets with the extension MP4. -->

### Video-elementen uploaden

Voer de volgende stappen uit om een video-element te uploaden:

1. Navigeer in de map met digitale elementen of in de submappen naar de locatie waar u het element wilt toevoegen.
1. Klik op **[!UICONTROL Create]** op de werkbalk en kies **[!UICONTROL Files]** . <br> Alternatief, sleep een dossier op het gebruikersinterface.
Leer meer over [ het uploaden activa ](manage-digital-assets.md#uploading-assets) in [!DNL Experience Manager Assets].

<!-- 1. To preview a video in the card view, click the **[!UICONTROL Play]** ![play option](assets/do-not-localize/play.png) option on the video asset. You can pause or play video in the card view only. The [!UICONTROL Play] and [!UICONTROL Pause] options are not available in the list view.
1. To preview the video in the asset details page, select **[!UICONTROL Edit]** on the card. The video plays in the native video player of the browser. You can play, pause, control the volume, and zoom the video to full screen. -->

### Video-elementen voorvertonen

U kunt video&#39;s voorvertonen in ondersteunde uitvoeringen in de gebruikersinterface van [!DNL Assets] . Voer de volgende stappen uit om een voorvertoning van een video-element weer te geven:

1. Upload een video-element met een ondersteunde indeling naar [!DNL Experience Manager Assets] . Leer meer over de [ gesteunde videoformaten ](file-format-support.md#video-formats). <br> Zodra geupload, wordt de videoactiva verwerkt, en een voorproefvertoning wordt geproduceerd.
1. Klik de activa, en selecteer ![ detailsoptie ](assets/do-not-localize/details_icon.svg) **[!UICONTROL Details]** van de hoogste toolbar. Het video-element wordt geopend in de videoviewer.
1. Klik het ![ pictogram van de speeloptie ](assets/do-not-localize/play.png) op de videoduimnagel. <br> u kunt spelen, pauzeren, het volume controleren, en de video aan het volledige scherm zoemen.

Voor bestaande video-elementen in [!DNL Experience Manager Assets] moet u **[!UICONTROL Reprocess]** de elementen in [!DNL Experience Manager] gebruiken om de functie voor videovoorvertoning in te schakelen. Leer hoe te [ digitale activa ](reprocessing.md) in [!DNL Experience Manager] opnieuw verwerken.

### Beperkingen van videovoorvertoning

* In MXF-bestanden worden geen videovoorvertoningen weergegeven, ook al wordt de vertoning gegenereerd.
* WebM-bestanden genereren geen voorvertoningsuitvoeringen omdat deze native door webbrowsers kunnen worden afgespeeld.

## Publish-video-elementen {#publish-video-assets}

Na publicatie kunt u de video-elementen in een webpagina opnemen als een URL of de elementen rechtstreeks insluiten. Voor details, zie [  [!DNL Dynamic Media]  activa ](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md) publiceren.

## Publish-video&#39;s naar YouTube {#publishing-videos-to-youtube}

U kunt video-elementen die in Experience Manager Assets worden beheerd, rechtstreeks publiceren naar een YouTube-kanaal dat u eerder hebt gemaakt.

Als u video-elementen naar YouTube wilt publiceren, kunt u tags toewijzen aan video-elementen in Experience Manager Assets. U koppelt deze tags aan een YouTube-kanaal. Als de tag van een video-element overeenkomt met de tag van een YouTube-kanaal, wordt de video gepubliceerd naar YouTube. Publish naar YouTube treedt op samen met een normale publicatie van de video zolang een bijbehorende tag wordt gebruikt.

YouTube voert zijn eigen codering uit. Als zodanig wordt het oorspronkelijke videobestand dat naar de Experience Manager is geüpload, gepubliceerd naar YouTube in plaats van elke video-uitvoering die door de codering van Dynamic Media is gemaakt. Hoewel het niet nodig is om video&#39;s te verwerken met Dynamic Media, wordt verwacht dat dit gebeurt voor het geval dat een viewer-voorinstelling nodig is voor het afspelen.

Wanneer u het videoverwerkingsprofiel overslaat en rechtstreeks naar YouTube publiceert, betekent dit gewoon dat uw video-element in Experience Manager Asset geen zichtbare miniatuur krijgt. Het betekent ook dat video&#39;s die niet zijn gecodeerd, niet werken met Dynamic Media-middelen.

Bij het publiceren van video-elementen naar YouTube-servers moeten de volgende taken worden uitgevoerd om een veilige en veilige server-naar-server verificatie met YouTube te garanderen:

1. [Google Cloud-instellingen configureren](#configuring-google-cloud-settings)
1. [Een YouTube-kanaal maken](#creating-a-youtube-channel)
1. [Codes toevoegen voor publicatie](#adding-tags-for-publishing)
1. [YouTube instellen in Experience Manager](#setting-up-youtube-in-aem)
1. [(Optioneel) Automatiseer de standaardeigenschappen van YouTube voor uw geüploade video&#39;s](#optional-automating-the-setting-of-default-youtube-properties-for-your-uploaded-videos)
1. [Publish-video&#39;s naar uw YouTube-kanaal](#publishing-videos-to-your-youtube-channel)
1. [(Optioneel) Controleer de gepubliceerde video op YouTube](/help/assets/dynamic-media/video.md#optional-verifying-the-published-video-on-youtube)
1. [YouTube-URL&#39;s koppelen aan uw webtoepassing](#linking-youtube-urls-to-your-web-application)

U kunt ook [ unpublish video&#39;s om hen uit YouTube ](#unpublishing-videos-to-remove-them-from-youtube) te verwijderen.

### Google Cloud-instellingen configureren {#configuring-google-cloud-settings}

Als u wilt publiceren naar YouTube, hebt u een Google-account nodig. Als u een GMAIL-account hebt, hebt u al een Google-account. Als u geen Google-account hebt, kunt u er eenvoudig een maken. U hebt het account nodig omdat u aanmeldingsgegevens nodig hebt om video-elementen naar YouTube te publiceren. <!-- hidden March 3 2022 If you have an account already created, then skip this task and proceed directly to [Create a YouTube channel](#creating-a-youtube-channel). -->

Het account dat wordt gebruikt met Google Cloud en het Google-account dat wordt gebruikt voor YouTube, hoeft niet hetzelfde te zijn.

Google wijzigt regelmatig de gebruikersinterface. De stappen voor het publiceren van video&#39;s naar YouTube kunnen dan ook enigszins afwijken van wat hieronder wordt beschreven. Dit voorbehoud geldt ook voor YouTube wanneer u probeert te controleren of er video&#39;s naar worden geüpload.

>[!NOTE]
>
>De volgende stappen waren correct op het moment van schrijven. Google werkt echter regelmatig hun cloudwebpagina&#39;s bij zonder dat dit wordt gemeld. Daarom kunnen sommige configuratieopties in de Google-gebruikersinterface iets anders worden genoemd dan de naam die in de stappen wordt gebruikt.

**om de montages van de Wolk van Google te vormen:**

1. Maak een Google-account.

   Als u al een Google-account hebt, kunt u de volgende stap overslaan.

1. Ga naar [ https://cloud.google.com/ ](https://cloud.google.com/).
1. Selecteer **[!UICONTROL Console]** op de pagina **[!UICONTROL Google Cloud]** in de rechterbovenhoek.

   Indien nodig, **[!UICONTROL Sign in]** gebruikt u de gegevens van uw Google-account om de optie **[!UICONTROL Console]** te zien.

1. Selecteer op de pagina **[!UICONTROL Dashboard]** rechts van **[!UICONTROL Google Cloud Platform]** de vervolgkeuzelijst **[!UICONTROL Project]** om het dialoogvenster **[!UICONTROL Select a project]** te openen.
1. Selecteer **[!UICONTROL New Project]** in het dialoogvenster **[!UICONTROL Select a project]** .
1. Typ in het dialoogvenster **[!UICONTROL New Project]** in het veld **[!UICONTROL Project name]** de naam van het nieuwe project.

   Uw project-id is gebaseerd op uw projectnaam. Kies daarom de projectnaam zorgvuldig en deze kan niet worden gewijzigd nadat deze is gemaakt. U moet dezelfde project-id opnieuw invoeren wanneer u YouTube later instelt in Experience Manager. Schrijf het daarom op.

1. Selecteer **[!UICONTROL Create]** .

1. Voer een van de volgende handelingen uit:

   * Selecteer **[!UICONTROL Explore and enable APIs]** op het dashboard van uw project in de **[!UICONTROL Getting Started]** -kaart.
   * Selecteer **[!UICONTROL Go to APIs overview]** op het dashboard van uw project in de **[!UICONTROL APIs]** -kaart.

1. Selecteer **[!UICONTROL ENABLE APIS AND SERVICES]** in het midden boven aan de pagina **[!UICONTROL APIs & Services]** . <!-- NEXT STEP BELOW IS STEP 10 -->
1. Selecteer op de pagina **[!UICONTROL API Library]** links onder **[!UICONTROL Category]** de optie **[!UICONTROL YouTube]** . Selecteer **[!UICONTROL YouTube]** rechts van de pagina.
1. Selecteer op de pagina **[!UICONTROL YouTube]** de optie **[!UICONTROL YouTube Data API v3]** .
1. Selecteer op de pagina **[!UICONTROL YouTube Data API v3]** de optie **[!UICONTROL MANAGE]** .

   ![ 6_5_googleaccount-apis-manage ](/help/assets/dynamic-media/assets/6_5_googleaccount-apis-manage.png)

1. U hebt referenties nodig om de API te gebruiken. Selecteer indien nodig links op de pagina **[!UICONTROL APIs & Services]** de optie **[!UICONTROL Credentials]** .
1. Selecteer **[!UICONTROL CREATE CREDENTIALS]** boven op de pagina **[!UICONTROL Credentials]** en selecteer vervolgens **[!UICONTROL OAuth client ID]** .
1. Selecteer op de pagina **[!UICONTROL Create OAuth client ID]** in de vervolgkeuzelijst **[!UICONTROL Application type]** de optie **[!UICONTROL Web application]** .

   ![ 6_5_googleaccount-apis-applicationType ](/help/assets/dynamic-media/assets/6_5_googleaccount-apis-applicationtype.png)

1. Voer een van de volgende handelingen uit:

   * Voer in het veld **[!UICONTROL Name]** een unieke naam in voor uw OAuth 2.0-client.
   * Gebruik de standaardnaam die Google al in het veld **[!UICONTROL Name]** heeft opgegeven.

1. Selecteer onder de kop **[!UICONTROL Authorized JavaScript origins]** de optie **[!UICONTROL ADD URI]** .

   ![ 6_5_googleaccount-apis-nameAuthorizations ](/help/assets/dynamic-media/assets/6_5_googleaccount-apis-nameauthorizations.png)

1. Voer in het tekstveld **[!UICONTROL URIs]** het volgende pad in, waarbij u uw eigen domein- en poortnummer in het pad vervangt, en druk vervolgens op **[!UICONTROL Enter]** om het pad aan de lijst toe te voegen:

   `https://<servername.domain>:<port_number>`

   Bijvoorbeeld: `https://1a2b3c.mycompany.com:4321`

   >[!NOTE]
   >
   >Het bovenstaande URI-padvoorbeeld is hypothetisch en alleen ter uitleg.

1. Selecteer onder de kop **[!UICONTROL Authorized redirect URIs]** de optie ADD URI.
1. Voer in het tekstveld **[!UICONTROL URIs]** het volgende pad in, waarbij u uw eigen domein- en poortnummer in het pad vervangt, en druk vervolgens op **[!UICONTROL Enter]** om het pad aan de lijst toe te voegen:

   `https://<servername.domain>:<port_number>/etc/cloudservices/youtube.youtubecredentialcallback.json`

   Bijvoorbeeld: `https://1a2b3c.mycompany.com:4321/etc/cloudservices/youtube.youtubecredentialcallback.json`

   >[!NOTE]
   >
   >Het bovenstaande URI-padvoorbeeld is hypothetisch en alleen ter uitleg.

1. Selecteer onder aan de pagina **[!UICONTROL Create OAuth client ID]** de optie **[!UICONTROL Create]** .
1. Ga als volgt te werk in het dialoogvenster **[!UICONTROL OAuth client created]** :

   * (Optioneel) Kopieer de waarden in de velden **[!UICONTROL Your Client ID]** en **[!UICONTROL Your Client Secret]** en sla deze op.
   * Selecteer **[!UICONTROL DOWNLOAD JSON]** en sla het JSON-bestand op.

   U hebt dit gedownloade JSON-bestand nodig wanneer u YouTube later instelt in Adobe Experience Manager.

   ![ 6_5_googleaccount-apis-oauthclient created ](/help/assets/dynamic-media/assets/6_5_googleaccount-apis-oauthclientcreated.png)

1. Selecteer **[!UICONTROL OK]** in het dialoogvenster **[!UICONTROL OAuth client created]** .
1. Log uit op je Google account. Maak nu een YouTube-kanaal.

### Een YouTube-kanaal maken {#creating-a-youtube-channel}

Voor het publiceren van video&#39;s naar YouTube hebt u een of meer kanalen nodig. Als u reeds een kanaal van YouTube hebt gecreeerd, kunt u deze taak overslaan en naar [ gaan toevoegen markeringen voor het publiceren ](/help/assets/dynamic-media/video.md#adding-tags-for-publishing).

>[!CAUTION]
>
>Ben zeker u reeds opstelling één of meerdere kanalen in YouTube *vóór* hebt u kanalen onder de Montages van YouTube in Experience Manager (zie [ Opstelling YouTube in Experience Manager ](#setting-up-youtube-in-aem) hieronder) toevoegt. Als u de kanaalinstelling niet kunt uitvoeren, wordt u niet gewaarschuwd dat er geen bestaande kanalen zijn. Google-verificatie vindt echter nog steeds plaats wanneer u een kanaal toevoegt, maar er is geen optie om te kiezen welk kanaal de video wordt verzonden.

**om een kanaal van YouTube tot stand te brengen:**

1. Ga naar [ https://www.youtube.com ](https://www.youtube.com/) en teken binnen gebruikend uw de rekeningsgeloofsbrieven van Google.
1. Selecteer in de rechterbovenhoek van de YouTube-pagina uw profielafbeelding (deze kan ook als een letter binnen een cirkel met effen kleuren worden weergegeven) en selecteer vervolgens **[!UICONTROL YouTube settings]** (pictogram met ronde versnelling).
1. Selecteer op de pagina Overzicht onder de kop Extra functies de optie **[!UICONTROL See all my channels or create a channel]** .
1. Selecteer op de pagina Kanalen de optie **[!UICONTROL Create a new channel]** .
1. Voer op de pagina Merkaccount in het veld Merknaam een bedrijfsnaam of een andere kanaalnaam in die u kiest waar u de video-elementen wilt publiceren en selecteer vervolgens **[!UICONTROL Create]** .

   Onthoud de naam die u hier invoert. Voer deze naam opnieuw in wanneer u YouTube in Experience Manager moet instellen.

1. (Optioneel) Voeg desgewenst meer kanalen toe.

   Nu voegt u labels toe voor publicatie.

### Codes toevoegen voor publicatie {#adding-tags-for-publishing}

Als u video&#39;s naar YouTube wilt publiceren, koppelt de Experience Manager de tags aan een of meer YouTube-kanalen. Om markeringen voor het publiceren toe te voegen, zie [ Markeringen beheren ](/help/sites-cloud/authoring/sites-console/tags.md).

Of, als u van plan bent om de standaardmarkeringen in Experience Manager te gebruiken, kunt u deze taak overslaan en naar [ Opstelling YouTube in Experience Manager ](#setting-up-youtube-in-aem) gaan.

>[!NOTE]
>
>Nadat de Cloud Service wordt gevormd, wordt andere configuratie niet vereist om de YouTube Publish replicatieagent op dit punt toe te laten. De reden is omdat het werd toegelaten toen de configuratie van de Cloud Service werd bewaard.

<!-- ### Enabling the YouTube Publish replication agent {#enabling-the-youtube-publish-replication-agent}

After you enable the YouTube Publish replication agent, if you want to test the connection to the Google Cloud account, select **[!UICONTROL Test Connection]**. A browser tab displays the connection results. If you have added YouTube Channels, then a listing of those is displayed as part of the test.

1. In the upper-left corner of Experience Manager, select the Experience Manager logo, then in the left rail, navigate to **[!UICONTROL Tools]** > **[!UICONTROL Deployment]** > **[!UICONTROL Replication]** > **[!UICONTROL Agents on Author]**.
1. On the Agents of Author page, select **[!UICONTROL YouTube Publish (youtube)]**.
1. On the toolbar, to the right of Settings, select **[!UICONTROL Edit]**.
1. Select the **[!UICONTROL Enabled]** checkbox to turn on the replication agent.
1. Select **[!UICONTROL OK]**. -->

### YouTube instellen in Experience Manager {#setting-up-youtube-in-aem}

Vanaf Experience Manager 6.4 is een nieuwe aanraakgebruikersinterfacemethode geïntroduceerd om YouTube-publicaties in Experience Manager in te stellen. Op basis van de geïnstalleerde Experience Manager die u gebruikt, voert u een van de volgende handelingen uit:

* Om YouTube in Experience Manager vóór 6.4 te vormen, zie [ Opstelling YouTube in Experience Manager vóór 6.4 ](/help/assets/dynamic-media/video.md#setting-up-youtube-in-aem-before).
* Om YouTube in Experience Manager 6.4 of recenter te vormen, zie [ Opstelling YouTube in Experience Manager 6.4 en later ](#setting-up-youtube-in-aem-and-later).

#### YouTube instellen in Experience Manager 6.4 en hoger {#setting-up-youtube-in-aem-and-later}

1. Meld u als beheerder aan bij uw exemplaar van Dynamic Media.
1. Selecteer in de linkerbovenhoek van de Experience Manager het logo van de Experience Manager en navigeer vervolgens in de linkertrack naar **[!UICONTROL Tools]** (hamerpictogram) > **[!UICONTROL Cloud Services]** > **[!UICONTROL YouTube Publishing Configuration]** .
1. Selecteer **[!UICONTROL global]** (niet selecteren).

1. Selecteer **[!UICONTROL Create]** in de rechterbovenhoek van de algemene pagina.
1. Voer op de pagina YouTube-configuratie maken onder Google Cloud-platforminstellingen in het veld **[!UICONTROL Application Name]** de Google-project-id in.

   U hebt de project-id opgegeven toen u de Google Cloud-instellingen voor het eerst eerder hebt geconfigureerd.
Laat de pagina YouTube-configuratie maken open. U keert er zo meteen naar terug.

   ![ 6_5_youtubepublish-createyoutubeconfiguration ](/help/assets/dynamic-media/assets/6_5_youtubepublish-createyoutubeconfiguration.png)

1. Gebruikend een gewone tekstredacteur, open het JSON dossier dat u vroeger in de taak [ downloadde en bewaarde montages van de Wolk van Google ](/help/assets/dynamic-media/video.md#configuring-google-cloud-settings) vormt.
1. Selecteer en kopieer de volledige JSON-tekst.
1. Ga terug naar het dialoogvenster YouTube-accountinstellingen. Plak de JSON-tekst in het veld **[!UICONTROL JSON Config]**.
1. Selecteer **[!UICONTROL Save]** in de rechterbovenhoek van de pagina.

   Stel nu YouTube-kanalen in Experience Manager in.

1. Selecteer **[!UICONTROL Add Channel]** .
1. Voer in het veld Kanaalnaam de naam in van het kanaal dat u in de taak **[!UICONTROL Adding one or more channels to YouTube]** eerder hebt gemaakt.

   U kunt desgewenst een beschrijving toevoegen.

1. Selecteer **[!UICONTROL Add]** .
1. YouTube/Google-verificatie wordt weergegeven. Als u zich nog niet hebt aangemeld bij het Google Cloud-account, slaat u deze stap over.

   * Voer de Google-gebruikersnaam en het wachtwoord in die aan de Google Project ID en de JSON-tekst hierboven zijn gekoppeld.
   * Afhankelijk van hoeveel kanalen uw account twee of meer items bevat. Selecteer een kanaal. Selecteer het e-mailadres niet, het is geen kanaal.
   * Selecteer op de volgende pagina **[!UICONTROL Accept]** om toegang tot dit kanaal toe te staan.

1. Selecteer **[!UICONTROL Allow]** .

   Stel nu labels in voor publicatie.

1. **[!UICONTROL Setting up tags for publishing]** - Selecteer op de pagina Cloud Servicen > YouTube het potloodpictogram om de lijst met tags die u wilt gebruiken te bewerken.
1. Als u de lijst met beschikbare labels in de Experience Manager wilt weergeven, selecteert u het vervolgkeuzelijstpictogram (ondersteboven ingedrukt caret).
1. Selecteer een of meer tags om deze toe te voegen.

   Als u een toegevoegde tag wilt verwijderen, selecteert u de tag en selecteert u **[!UICONTROL X]** .

1. Selecteer **[!UICONTROL Save]** wanneer u alle gewenste tags hebt toegevoegd.

   Nu publiceert u video&#39;s naar uw YouTube-kanaal.

#### YouTube instellen in Experience Manager vóór 6.4 {#setting-up-youtube-in-aem-before}

1. Meld u als beheerder aan bij uw exemplaar van Dynamic Media.

1. Selecteer in de linkerbovenhoek van de Experience Manager het logo van de Experience Manager en navigeer vervolgens in de linkertrack naar **[!UICONTROL Tools]** (hamerpictogram) > **[!UICONTROL Deployment]** > **[!UICONTROL Cloud Services]** .
1. Selecteer onder YouTube onder de kop Services van derden de optie **[!UICONTROL Configure now]** .
1. Voer in het dialoogvenster Configuratie maken een titel (verplicht) en een naam (optioneel) in de desbetreffende velden in.
1. Selecteer **[!UICONTROL Create]** .
1. Voer in het veld **[!UICONTROL Application Name]** in het dialoogvenster YouTube-accountinstellingen de Google-project-id in.

   U specificeerde projectidentiteitskaart wanneer u aanvankelijk [ de montages van de Wolk van Google ](/help/assets/dynamic-media/video.md#configuring-google-cloud-settings) vroeger vormde.
Laat het dialoogvenster YouTube-accountinstellingen open. U keert er zo meteen naar terug.

1. Open met een teksteditor zonder opmaak het JSON-bestand dat u eerder hebt gedownload en opgeslagen in de taak Google Cloud-instellingen configureren.
1. Selecteer en kopieer de volledige JSON-tekst.
1. Ga terug naar het dialoogvenster YouTube-accountinstellingen. Plak de JSON-tekst in het veld **[!UICONTROL JSON Config]**.
1. Selecteer **[!UICONTROL OK]** .

   Stel nu YouTube-kanalen in Experience Manager in.

1. Rechts van **[!UICONTROL Available Channels]**, uitgezochte **+** (plusteken pictogram).
1. Voer in het veld Titel in het dialoogvenster YouTube-kanaalinstellingen de naam in van het kanaal dat u eerder in de taak **[!UICONTROL Adding one or more channels to YouTube]** hebt gemaakt.

   U kunt desgewenst een beschrijving toevoegen.

1. Selecteer **[!UICONTROL OK]** .
1. YouTube/Google-verificatie wordt weergegeven. Als u zich nog niet hebt aangemeld bij het Google Cloud-account, slaat u deze stap over.

   * Voer de Google-gebruikersnaam en het wachtwoord in die aan de Google Project ID en de JSON-tekst hierboven zijn gekoppeld.
   * Afhankelijk van hoeveel kanalen uw account twee of meer items bevat. Selecteer een kanaal. Selecteer het e-mailadres niet, het is geen kanaal.
   * Selecteer op de volgende pagina **[!UICONTROL Accept]** om toegang tot dit kanaal toe te staan.

1. Selecteer **[!UICONTROL Allow]** .

   Stel nu labels in voor publicatie.

1. **[!UICONTROL Setting up tags for publishing]** - Selecteer op de pagina Cloud Servicen > YouTube het potloodpictogram om de lijst met tags die u wilt gebruiken te bewerken.
1. Als u de lijst met beschikbare labels in de Experience Manager wilt weergeven, selecteert u het vervolgkeuzelijstpictogram (ondersteboven ingedrukt caret).
1. Selecteer een of meer tags om deze toe te voegen.

   Om een markering te schrappen die u hebt toegevoegd, selecteer de markering, en selecteer **X**.

1. Selecteer **[!UICONTROL OK]** wanneer u alle gewenste tags hebt toegevoegd.

   Nu publiceert u video&#39;s naar uw YouTube-kanaal.

### (Optioneel) Automatiseer de standaardeigenschappen van YouTube voor uw geüploade video&#39;s {#optional-automating-the-setting-of-default-youtube-properties-for-your-uploaded-videos}

U kunt desgewenst de instelling van YouTube-eigenschappen automatiseren bij het uploaden van uw video&#39;s. Maak een verwerkingsprofiel voor metagegevens in de Experience Manager.

Als u het verwerkingsprofiel voor metadata wilt maken, kopieert u eerst waarden uit de velden **[!UICONTROL Field Label]**, **[!UICONTROL Map to property]** en **[!UICONTROL Choices]** die te vinden zijn in de metadataschema&#39;s voor video. Vervolgens kunt u het verwerkingsprofiel voor YouTube-videometagegevens samenstellen door deze waarden eraan toe te voegen.

**om het plaatsen van standaardYouTube eigenschappen voor uw geupload video&#39;s te automatiseren:**

1. Selecteer in de linkerbovenhoek van de Experience Manager het logo van de Experience Manager en navigeer vervolgens in de linkertrack naar **[!UICONTROL Tools]** (hamerpictogram) > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Schemas]** .
1. Selecteer **[!UICONTROL default]**. (Voeg geen vinkje toe aan het selectievak links van &quot;standaard&quot;.)
1. Schakel op de pagina **[!UICONTROL default]** het vakje links van **[!UICONTROL video]** in en selecteer vervolgens **[!UICONTROL Edit]** .
1. Selecteer het tabblad **[!UICONTROL Advanced]** op de pagina van de Editor van het metagegevensschema.
1. Selecteer onder de kop YouTube Publishing de optie **[!UICONTROL YouTube Category]** .
1. Voer aan de rechterkant van de pagina, onder de tab **[!UICONTROL Settings]** , de volgende handelingen uit:

   * Selecteer en kopieer de waarde in het tekstveld **[!UICONTROL Map to property]** .
Plak de gekopieerde waarde in de geopende teksteditor. Deze waarde hebt u later nodig wanneer u uw verwerkingsprofiel voor metagegevens maakt. Laat de teksteditor geopend.

   * Selecteer en kopieer onder **[!UICONTROL Choices]** de standaardwaarde die u wilt gebruiken (zoals Personen en blogs of Wetenschap en Technologie).
Plak de gekopieerde waarde in de geopende teksteditor. Deze waarde hebt u later nodig wanneer u uw verwerkingsprofiel voor metagegevens maakt. Laat de teksteditor geopend.

1. Selecteer onder de kop YouTube Publishing de optie **[!UICONTROL YouTube Privacy]** .
1. Voer aan de rechterkant van de pagina, onder de tab **[!UICONTROL Settings]** , de volgende handelingen uit:

   * Selecteer en kopieer de waarde in het tekstveld **[!UICONTROL Map to property]** .
Plak de gekopieerde waarde in de geopende teksteditor. Deze waarde hebt u later nodig wanneer u uw verwerkingsprofiel voor metagegevens maakt. Laat de teksteditor geopend.

   * Selecteer en kopieer onder **[!UICONTROL Choices]** de standaardwaarde die u wilt gebruiken. De keuzen zijn gegroepeerd in twee. Het onderste veld in het paar is de standaardwaarde die u wilt kopiëren, bijvoorbeeld public, unlist of private.
Plak de gekopieerde waarde in de geopende teksteditor. Deze waarde hebt u later nodig wanneer u uw verwerkingsprofiel voor metagegevens maakt. Laat de teksteditor geopend.

1. Selecteer **[!UICONTROL Cancel]** in de rechterbovenhoek van de pagina van de Editor van het metagegevensschema.
1. Selecteer in de linkerbovenhoek van de Experience Manager het logo van de Experience Manager en selecteer vervolgens in de linkertrack **[!UICONTROL Tools]** (hamerpictogram) > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Profiles]** .

1. Selecteer **[!UICONTROL Create]** in de rechterbovenhoek van de pagina Metagegevensprofielen.
1. Voer in het tekstveld **[!UICONTROL Profile title]** in het dialoogvenster Metagegevensprofiel toevoegen de naam `YouTube Video` in en selecteer **[!UICONTROL Create]** .
1. Selecteer het tabblad **[!UICONTROL Advance]** op de pagina Metagegevensprofieleditor.
1. Voeg de gekopieerde YouTube Publishing-waarden als volgt toe aan het profiel:

   * Selecteer rechts van de pagina de tab **[!UICONTROL Build Form]** .
   * (Optioneel) Sleep de component met het label **[!UICONTROL Section Header]** naar links en zet deze neer in het formuliergebied.
   * (Optioneel) Selecteer **[!UICONTROL Field Label]** om de component te selecteren.
   * (Optioneel) Typ `YouTube Publishing` rechts van de pagina onder het tabblad Instellingen in het tekstveld Veld Label.
   * Selecteer het tabblad **[!UICONTROL Build Form]** en sleep de component met het label **[!UICONTROL Multi Value Text]** naar de kop **[!UICONTROL YouTube Publishing]** die u hebt gemaakt.

   * Selecteer **[!UICONTROL Field Label]** om de component te selecteren.
   * Plak rechts van de pagina, onder het tabblad Instellingen, de YouTube Publishing-waarden (Field Label value en Map to property value) die u eerder hebt gekopieerd, in hun respectievelijke velden op het formulier. Plak de waarde Keuzen in het veld Standaardwaarde.

1. Voeg de gekopieerde YouTube-privacywaarden als volgt toe aan het profiel:

   * Selecteer rechts van de pagina de tab **[!UICONTROL Build Form]** .
   * (Optioneel) Sleep de component met het label **[!UICONTROL Section Header]** naar links en zet deze neer in het formuliergebied.
   * (Optioneel) Selecteer **[!UICONTROL Field Label]** om de component te selecteren.
   * (Optioneel) Typ `YouTube Privacy` rechts van de pagina onder het tabblad Instellingen in het tekstveld Veld Label.
   * Selecteer de tab **[!UICONTROL Build Form]** en sleep de component met het label **[!UICONTROL Multi Value Text]** naar de nieuwe kop **[!UICONTROL YouTube Privacy]** die u hebt gemaakt.

   * Selecteer **[!UICONTROL Field Label]** om de component te selecteren.
   * Plak rechts van de pagina, onder het tabblad Instellingen, de YouTube Publishing-waarden (Field Label value en Map to property value) die u eerder hebt gekopieerd, in hun respectievelijke velden op het formulier. Plak de waarde Keuzen in het veld Standaardwaarde.

1. Selecteer **[!UICONTROL Save]** in de rechterbovenhoek van de pagina.
1. Pas het metagegevensprofiel voor YouTube Publishing toe op de mappen waarin u video&#39;s gaat uploaden. U moet zowel het profiel Metagegevens als het videoprofiel hebben ingesteld.

   Zie [Metadataprofielen](/help/assets/metadata-profiles.md) en [Videoprofielen](/help/assets/dynamic-media/video-profiles.md).

### Publish-video&#39;s naar uw YouTube-kanaal {#publishing-videos-to-your-youtube-channel}

Nu associeert u de markeringen die u eerder aan videoactiva toevoegde. Dit proces stelt de Experience Manager in kennis van de elementen die naar uw YouTube-kanaal moeten worden gepubliceerd.

>[!NOTE]
>
>Publish publiceert niet automatisch naar YouTube. Wanneer Dynamische media is ingesteld, zijn er twee publicatieopties waaruit u kunt kiezen: **[!UICONTROL Immediately]** of **[!UICONTROL Upon Activation]**.
>
>**[!UICONTROL Publish Immediately]** betekent dat het geüploade element-nadat het met IPS-wordt gesynchroniseerd automatisch aan het leveringssysteem wordt gepubliceerd. Dat geldt voor Dynamic Media, maar dat geldt niet voor YouTube. Als u wilt publiceren naar YouTube, moet u publiceren als Experience Manager Auteur.

>[!NOTE]
>
>Voor het publiceren van inhoud vanuit YouTube gebruikt Experience Manager de **[!UICONTROL Publish to YouTube]** -workflow. Hiermee kunt u de voortgang volgen en eventuele foutgegevens weergeven.
>
>Zie [ video het coderen van de Monitor en YouTube het publiceren vooruitgang ](#monitoring-video-encoding-and-youtube-publishing-progress).
>
>Voor gedetailleerdere voortgangsgegevens kunt u het YouTube-logboek onder replicatie controleren. Houd er echter rekening mee dat voor dergelijke bewaking beheerderstoegang vereist is.

**om video&#39;s aan uw kanaal van YouTube te publiceren:**

1. Navigeer in Experience Manager naar een video-element dat u naar het YouTube-kanaal wilt publiceren.
1. Selecteer het video-element (de adaptieve videoset).
1. Selecteer **[!UICONTROL Properties]** op de werkbalk.
1. Selecteer op het tabblad Standaard onder de kop Metagegevens de optie **[!UICONTROL Open Selection Dialog]** rechts van het veld Codes.
1. Navigeer op de pagina Codes selecteren naar de gewenste codes en selecteer een of meer codes.

   Vergeet niet dat de tags moeten worden gekoppeld aan het YouTube-kanaal.

1. Selecteer **[!UICONTROL Select]** rechtsboven op de pagina.
1. Selecteer **[!UICONTROL Save and Close]** in de rechterbovenhoek van de eigenschappenpagina van de video.
1. Selecteer **[!UICONTROL Quick Publish]** op de werkbalk.

   Zie ook [ het Beheer van de Publicatie van het Gebruik met Experience Manager Sites ](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/page-authoring/publication-management-feature-video-use.html#page-authoring).

   U kunt desgewenst de gepubliceerde video op uw YouTube-kanaal verifiëren.

### (Optioneel) Controleer de gepubliceerde video op YouTube {#optional-verifying-the-published-video-on-youtube}

U kunt optioneel de voortgang van het publiceren van YouTube (of het ongedaan maken van het publiceren) volgen.

Zie [ video het coderen van de Monitor en YouTube het publiceren vooruitgang ](#monitoring-video-encoding-and-youtube-publishing-progress).

De het publiceren tijden kunnen zeer afhankelijk van talrijke factoren variëren die het formaat van uw primaire bronvideo, dossiergrootte, en uploadverkeer omvatten. Het publicatieproces kan een paar minuten tot enkele uren duren. Bovendien worden indelingen met een hogere resolutie veel langzamer gerenderd. Het duurt bijvoorbeeld langer om 720p en 1080p weer te geven dan 480p.

Als er na acht uur nog steeds een statusbericht met de tekst **[!UICONTROL Uploaded (processing, please wait)]** wordt weergegeven, verwijdert u de video van uw site en uploadt u deze opnieuw.

### YouTube-URL&#39;s koppelen aan uw webtoepassing {#linking-youtube-urls-to-your-web-application}

U kunt een YouTube URL-tekenreeks verkrijgen die door Dynamic Media wordt gegenereerd nadat u de video hebt gepubliceerd. Wanneer u de YouTube-URL kopieert, wordt deze op het Klembord gedownload, zodat u deze indien nodig kunt plakken naar pagina&#39;s in uw website of toepassing.

>[!NOTE]
>
>De YouTube-URL kan pas worden gekopieerd nadat u het video-element naar YouTube hebt gepubliceerd.

YouTube-URL&#39;s koppelen aan uw webtoepassing:

1. Navigeer aan *YouTube publiceerde* videoactiva waarvan URL die u wilt kopiëren, dan het selecteren.

   Herinner dat YouTube URLs slechts beschikbaar is om *te kopiëren nadat* u eerst ** de videoactiva aan YouTube hebt gepubliceerd.

1. Selecteer **[!UICONTROL Properties]** op de werkbalk.
1. Selecteer de tab **[!UICONTROL Advanced]** .
1. Selecteer onder YouTube Publishing in de URL-lijst van YouTube de URL-tekst die u naar uw webbrowser wilt kopiëren om een voorvertoning van het element weer te geven of om deze toe te voegen aan uw pagina met webinhoud.

### Publicatie van video&#39;s ongedaan maken zodat u deze kunt verwijderen uit YouTube {#unpublishing-videos-to-remove-them-from-youtube}

Wanneer u de publicatie van een video-element in Experience Manager ongedaan maakt, wordt de video verwijderd uit YouTube.

>[!CAUTION]
>
>Als u een video rechtstreeks uit YouTube verwijdert, is de Experience Manager zich hiervan niet bewust en gedragen deze zich alsof de video nog steeds naar YouTube wordt gepubliceerd. Publiceer de publicatie van een video-element vanuit YouTube altijd ongedaan als Experience Manager.

>[!NOTE]
>
>Als u inhoud uit YouTube wilt verwijderen, gebruikt Experience Manager de **[!UICONTROL Unpublish from YouTube]** -workflow. Hiermee kunt u de voortgang volgen en eventuele foutgegevens weergeven.
>
>Zie [ video het coderen van de Monitor en YouTube het publiceren vooruitgang ](#monitoring-video-encoding-and-youtube-publishing-progress).

**unpublish video&#39;s om hen uit YouTube te verwijderen:**

1. Navigeer naar de video-elementen waarvan u de publicatie via uw YouTube-kanaal wilt ongedaan maken.
1. Selecteer in de modus voor middelenselectie een of meer gepubliceerde video-elementen.
1. Selecteer **[!UICONTROL Manage Publication]** op de werkbalk. Selecteer zo nodig het pictogram met drie punten (`. . .`) op de werkbalk om **[!UICONTROL Manage Publication]** te zien.
1. Selecteer **[!UICONTROL Unpublish]** op de pagina Publicatie beheren.
1. Selecteer **[!UICONTROL Next]** rechtsboven op de pagina.
1. Selecteer **[!UICONTROL Unpublish]** rechtsboven op de pagina.

## Video-codering en YouTube-publicatievoortgang controleren {#monitoring-video-encoding-and-youtube-publishing-progress}

Wanneer u een nieuwe video uploadt naar een map waarop videocodering is toegepast of wanneer u uw video publiceert naar YouTube, controleert u hoe de videocodering/YouTube-publicatie vordert (of mislukt). Werkelijke vorderingen bij het publiceren in YouTube zijn alleen beschikbaar via de logboeken. Maar of het ontbreekt of slaagt, is het vermeld op andere manieren die in de volgende procedure worden beschreven. Bovendien ontvangt u e-mailmeldingen wanneer een publicatieworkflow of videocodering van YouTube is voltooid of onderbroken.

### Voortgang van controle {#monitoring-progress}

U kunt de voortgang controleren, inclusief mislukte codering/YouTube-publicatie.

1. De voortgang van videocodering weergeven in de map met elementen:

   * In de kaartweergave wordt de voortgang van de videocodering met een percentage weergegeven op het element. Als er een fout optreedt, wordt deze informatie ook weergegeven op het element.

   ![ chlimage_1-429 ](/help/assets/dynamic-media/assets/chlimage_1-429.png)

   * In de lijstweergave wordt de voortgang van de videocodering weergegeven in de kolom **[!UICONTROL Processing Status]** . Als er een fout is, toont dit bericht in die zelfde kolom.

   ![ chlimage_1-430 ](/help/assets/dynamic-media/assets/chlimage_1-430.png)

   Deze kolom wordt niet standaard weergegeven. Als u de kolom wilt inschakelen, selecteert u **[!UICONTROL View Settings]** in de vervolgkeuzelijst Weergaven en voegt u de kolom **[!UICONTROL Processing Status]** toe en selecteert u **[!UICONTROL Update]** .

   ![ chlimage_1-431 ](/help/assets/dynamic-media/assets/chlimage_1-431.png)

1. De voortgang van de elementen weergeven. Wanneer u een element selecteert, opent u het keuzemenu en selecteert u **[!UICONTROL Timeline]** . Selecteer **[!UICONTROL Workflows]** als u het wilt beperken tot workflowactiviteiten zoals coderen of YouTube publiceren.

   ![ chlimage_1-432 ](/help/assets/dynamic-media/assets/chlimage_1-432.png)

   Workflowinformatie, zoals codering, wordt weergegeven in de tijdlijn. Voor YouTube-publicatie bevat de tijdlijn van de workflow ook de naam van het YouTube-kanaal en de YouTube-video-URL. Bovendien ziet u eventuele foutmeldingen in de tijdlijn van de workflow nadat het publiceren is voltooid.

   >[!NOTE]
   >
   >Het kan lange tijd voor mislukking/foutenmeldingen duren om definitief te worden geregistreerd toe te schrijven aan veelvoudige werkschemeconfiguraties op **[!UICONTROL retries]**, **[!UICONTROL retry delay]**, en **[!UICONTROL timeout]** van [ https://localhost:4502/system/console/configMgr ](https://localhost:4502/system/console/configMgr), bijvoorbeeld:
   >
   >* Configuratie Apache Sling-taakwachtrij
   >* Adobe Granite Workflow External Process Handler
   >* Tijdelijke wachtrij voor Granite Workflow
   >
   >U kunt de eigenschappen **[!UICONTROL retries]** , **[!UICONTROL retry delay]** en **[!UICONTROL timeout]** in deze configuraties aanpassen.

1. Zie Workflowinstanties beschikbaar via **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Instances]** voor actieve workflows.

   >[!NOTE]
   >
   >U hebt beheerrechten nodig om het menu **[!UICONTROL Tools]** te openen.

   ![ chlimage_1-433 ](/help/assets/dynamic-media/assets/chlimage_1-433.png)

   Selecteer de instantie en selecteer **[!UICONTROL Open History]** .

   ![ chlimage_1-434 ](/help/assets/dynamic-media/assets/chlimage_1-434.png)

   Vanuit het gebied Workflowinstanties kunt u workflows ook opschorten, beëindigen of hernoemen. Zie [ werkschema&#39;s ](/help/sites-cloud/authoring/workflows/overview.md) voor meer informatie beheren.

1. Voor mislukte taken raadpleegt u de beschikbare workflowfouten in **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Failures]**. De lijst **[!UICONTROL Workflow Failure]** bevat alle mislukte workflowactiviteiten.

   >[!NOTE]
   >
   >U hebt beheerrechten nodig om het menu **[!UICONTROL Tools]** te openen.

   ![ chlimage_1-435 ](/help/assets/dynamic-media/assets/chlimage_1-435.png)

   >[!NOTE]
   >
   >Het kan lange tijd voor het foutenbericht duren om definitief te worden geregistreerd toe te schrijven aan veelvoudige werkschemeconfiguraties op **[!UICONTROL retries]**, **[!UICONTROL retry delay]**, en **[!UICONTROL timeout]** van [ https://localhost:4502/system/console/configMgr ](https://localhost:4502/system/console/configMgr), bijvoorbeeld:
   >
   >* Configuratie Apache Sling-taakwachtrij
   >* Adobe Granite Workflow External Process Handler
   >* Tijdelijke wachtrij voor Granite Workflow
   >
   >U kunt de eigenschappen **[!UICONTROL retries]** , **[!UICONTROL retry delay]** en **[!UICONTROL timeout]** in deze configuraties aanpassen.

1. Zie Workflowarchief in **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Archive]** voor voltooide workflows. In **[!UICONTROL Workflow Archive]** vindt u een lijst met alle voltooide workflowactiviteiten.

   >[!NOTE]
   >
   >U hebt beheerrechten nodig om het menu **[!UICONTROL Tools]** te openen.

   ![ chlimage_1-436 ](/help/assets/dynamic-media/assets/chlimage_1-436.png)

1. U ontvangt e-mailmeldingen over afgebroken of mislukte workflowtaken. Deze e-mailberichten kunnen door een beheerder worden geconfigureerd. Zie [ e-mailberichten ](#configuring-e-mail-notifications) vormen.

<!-- EMAIL NOT AVAILABLE IN SKYLINE

#### Configuring e-mail notifications {#configuring-e-mail-notifications}

>[!NOTE]
>
>You may need administrative rights to access the **[!UICONTROL Tools]** menu.

How you configure notification depends on whether you want notifications for YouTube publishing jobs.

* For encoding jobs, you can access the configuration page for all Experience Manager workflow email notifications at **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]** and by searching for **[!UICONTROL Day CQ Workflow Email Notification Service]**. You can select or clear the check boxes for **[!UICONTROL Notify on Abort]** or **[!UICONTROL Notify on Complete]** accordingly.

For YouTube publishing jobs, do the following:

1. In Experience Manager, navigate to **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
1. On the Workflow Models page, select **[!UICONTROL Publish to YouTube]**, then select **[!UICONTROL Edit]** on the toolbar.
1. Near the upper-right corner of the Publish to YouTube workflow page, select **[!UICONTROL Edit]**.
1. Hover the mouse pointer on the YouTube Upload component, then select once to display the inline toolbar.

   ![6_5_publishtoyoutubeworkflow](assets/6_5_publishtoyoutubeworkflow.png)

1. On the inline toolbar, select the Configuration icon (wrench). Select the **[!UICONTROL Arguments]** tab.

   ![6_5_publishtoyoutubeworkflow-configurationicon](assets/6_5_publishtoyoutubeworkflow-configurationicon.png)

1. In the YouTube Upload Process - Step Properties dialog box, select the **[!UICONTROL Arguments]** tab.

   ![6_5_publishtoyoutubeworkflow-arguments-tab](assets/6_5_publishtoyoutubeworkflow-arguments-tab.png)

1. You can select or clear the following check boxes:

    * Publish Start
    * Publish Failure
    * Publish Completion - includes information on channels and URLs

   Clearing a check box means that you will not receive the specified email notification from the YouTube Publish workflow.

   >[!NOTE]
   >
   >These emails are specific to YouTube and are in addition to the generic workflow email notifications. As a result, you may receive two sets of email notification - the generic notification available in the **[!UICONTROL Day CQ Workflow Email Notification Service]** and one specific to YouTube depending on your configuration settings.

1. When you are finished, near the upper-right corner of the dialog box, select the **[!UICONTROL Done]** icon (check mark).
1. On the Publish to YouTube workflow page, near the upper-right corner, select **[!UICONTROL Sync]**.

-->

## Transcoderen met verwerkingsprofiel {#transcode-video}

Met [!DNL Experience Manager] als een [!DNL Cloud Service] kunt u standaardtranscodering van MP4-videobestanden uitvoeren met behulp van Profielen verwerken. Met deze functie kunt u niet alleen een MP4-videobestand uploaden, maar ook een voorvertoning weergeven en schalen.

![ Verwerkingsprofiel maken voor videotranscodering in [!DNL Experience Manager]](assets/video-processing-profile-for-mp4.png)

*Cijfer: Een Profiel van de Verwerking voor videotranscodering in [!DNL Experience Manager].*

Als u alleen de breedte of alleen de hoogte opgeeft en het andere veld leeg laat, behouden de uitvoeringen de hoogte-breedteverhouding. H.264-videocodec is beschikbaar voor transcodering.

Als u elementen wilt verwerken met een verwerkingsprofiel, voegt u een profiel toe aan een map. Zie [ profielen van de gebruiksverwerking om activa ](/help/assets/asset-microservices-configure-and-use.md#use-profiles) te verwerken.

## Video-elementen notities aanbrengen {#annotate-video-assets}

U kunt notities toevoegen aan video-elementen. Tijdens het annoteren van video&#39;s pauzeert de speler zodat u notities kunt aanbrengen in een frame. Voor details, zie [ het leiden videoactiva ](manage-video-assets.md).

>[!NOTE]
>
>MXF-video-indeling wordt nog niet ondersteund met aantekeningen van video-elementen.

1. Selecteer in de [!DNL Assets] -console **[!UICONTROL Edit]** op de elementenkaart om de pagina met elementdetails weer te geven.
1. Klik op **[!UICONTROL Preview]** om de video af te spelen.
1. Klik op **[!UICONTROL Annotate]** om de video van notities te voorzien. Er wordt een aantekening toegevoegd op het specifieke tijdstip (frame) in de video. Wanneer u notities maakt, kunt u op het canvas tekenen en een opmerking bij de tekening opnemen. Opmerkingen worden automatisch opgeslagen. Klik op **[!UICONTROL Close]** om de wizard Annotatie af te sluiten.
1. Zoek naar een specifiek punt in de video, geef de tijd in seconden op in het veld voor **tekst** en klik op **Springen**. Als u bijvoorbeeld de eerste 20 seconden van de video wilt overslaan, voert u 20 in het tekstveld in.
1. Klik op een annotatie om deze in de tijdlijn weer te geven. Klik op **[!UICONTROL Delete]** om de annotatie uit de tijdlijn te verwijderen.

## Aanbevolen werkwijzen en beperkingen {#tips-limitations}

* Zonder [!DNL Dynamic Media] -licentie kunt u alleen MP4-bestanden verwerken met behulp van verwerkingsprofielen.
* Bij het transcoderen van MP4-bestanden met verwerkingsprofielen gelden de volgende richtlijnen en beperkingen:

   * Apple ProRes-bestanden kunnen alleen transcoderen naar een maximale resolutie van 1080p.
   * Als het bronbestand een bitsnelheid > 200 Mbps heeft, kunt u alleen transcoderen naar een maximale resolutie van 1080p.
   * Als de bronframesnelheid >=60 fps is, is de maximale grootte van het bronbestand dat u kunt gebruiken:

      * 400 MB voor 4.000 transcodering.
      * 800 MB voor 1080p-transcodering.
      * 8 GB voor 720p-transcodering.

   * De maximale bestandsgrootte die u kunt transcoderen naar een resolutie van 4 k is 2,55 GB MP4-bestand met een resolutie van 4 k, een bitsnelheid van 12 Mbps en 23 fps.

  **zie ook**

* [Assets vertalen](translate-assets.md)
* [ASSETS HTTP API](mac-api-assets.md)
* [Door Assets ondersteunde bestandsindelingen](file-format-support.md)
* [Zoeken in middelen](search-assets.md)
* [Verbonden elementen](use-assets-across-connected-assets-instances.md)
* [Elementen rapporteren](asset-reports.md)
* [Metagegevensschema&#39;s](metadata-schemas.md)
* [Elementen downloaden](download-assets-from-aem.md)
* [Metagegevens beheren](manage-metadata.md)
* [Zoeken in facetten](search-facets.md)
* [Verzamelingen beheren](manage-collections.md)
* [Bulkmetagegevens importeren](metadata-import-export.md)
* [Publish Assets naar AEM en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

>[!MORELIKETHIS]
>
>* [ de videodocumentatie van Dynamic Media ](/help/assets/dynamic-media/video.md).
>* [ ken meer over gebruik, types, en configuratie van verwerkingsprofielen ](/help/assets/asset-microservices-configure-and-use.md).
