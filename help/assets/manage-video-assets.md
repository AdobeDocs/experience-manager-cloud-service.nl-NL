---
title: Video-elementen beheren
description: Video-elementen uploaden, voorvertonen, notities aanbrengen en publiceren in [!DNL Adobe Experience Manager].
contentOwner: AG
feature: Asset Management,Publishing,Collaboration,Video
role: User
exl-id: 91edce4a-dfa0-4eca-aba7-d41ac907b81e
source-git-commit: f7f60036088a2332644ce87f4a1be9bae3af1c5e
workflow-type: tm+mt
source-wordcount: '4643'
ht-degree: 4%

---

# Video-elementen beheren {#manage-video-assets}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/managing-video-assets.html?lang=en) |
| AEM as a Cloud Service | Dit artikel |

De video-indeling is een essentieel onderdeel van digitale middelen van een organisatie. [!DNL Adobe Experience Manager] biedt geavanceerde aanbiedingen en functies om de volledige levenscyclus van uw video-elementen te beheren nadat deze zijn gemaakt.

Leer hoe u de video-elementen beheert en bewerkt in [!DNL Adobe Experience Manager Assets]. Videocodering en -transcodering, bijvoorbeeld MPEG-transcodering, is mogelijk met behulp van Profielen verwerken en [!DNL Dynamic Media] integratie. Zonder [!DNL Dynamic Media] vergunning, [!DNL Experience Manager] biedt basisondersteuning voor video&#39;s, zoals transcoderen met gebruik van MPEG, het uitnemen van voorvertoningsminiaturen voor de ondersteunde bestandsindelingen en een voorvertoning in de gebruikersinterface voor indelingen die worden ondersteund voor rechtstreeks afspelen in de browser.

## Video-elementen uploaden en voorvertonen {#upload-and-preview-video-assets}

U kunt video-elementen met een ondersteunde indeling uploaden en bekijken naar [!DNL Experience Manager Assets].
<!-- It generates previews for video assets with the extension MP4. -->

### Video-elementen uploaden

Voer de volgende stappen uit om een video-element te uploaden:

1. Navigeer in de map met digitale elementen of in de submappen naar de locatie waar u het element wilt toevoegen.
1. Klikken **[!UICONTROL Create]** op de werkbalk en kiest u **[!UICONTROL Files]**. <br>U kunt ook een bestand naar de gebruikersinterface slepen.
Meer informatie over [uploaden, elementen](manage-digital-assets.md#uploading-assets) in [!DNL Experience Manager Assets].

<!-- 1. To preview a video in the card view, click the **[!UICONTROL Play]** ![play option](assets/do-not-localize/play.png) option on the video asset. You can pause or play video in the card view only. The [!UICONTROL Play] and [!UICONTROL Pause] options are not available in the list view.
1. To preview the video in the asset details page, select **[!UICONTROL Edit]** on the card. The video plays in the native video player of the browser. You can play, pause, control the volume, and zoom the video to full screen. -->

### Video-elementen voorvertonen

U kunt video&#39;s voorvertonen in ondersteunde uitvoeringen in het dialoogvenster [!DNL Assets] gebruikersinterface. Voer de volgende stappen uit om een voorvertoning van een video-element weer te geven:

1. Een video-element met een ondersteunde indeling uploaden naar [!DNL Experience Manager Assets]. Meer informatie over de [ondersteunde video-indelingen](file-format-support.md#video-formats). <br>Nadat de video is geüpload, wordt het video-element verwerkt en wordt een voorvertoning gegenereerd.
1. Klik op het element en selecteer ![optie Details](assets/do-not-localize/details_icon.svg) **[!UICONTROL Details]**  in de bovenste werkbalk. Het video-element wordt geopend in de videoviewer.
1. Klik op de knop ![afspeeloptie](assets/do-not-localize/play.png) op de videominiatuur. <br>U kunt de video afspelen, pauzeren, het volume bepalen en op het volledige scherm in- of uitzoomen.

Voor bestaande video-elementen in [!DNL Experience Manager Assets], moet u **[!UICONTROL Reprocess]** de activa in [!DNL Experience Manager] om de functie voor videovoorvertoning in te schakelen. Leer hoe u [digitale middelen opnieuw verwerken](reprocessing.md) in [!DNL Experience Manager].

### Beperkingen van videovoorvertoning

* In MXF-bestanden worden geen videovoorvertoningen weergegeven, ook al wordt de vertoning gegenereerd.
* WebM-bestanden genereren geen voorvertoningsuitvoeringen omdat deze native door webbrowsers kunnen worden afgespeeld.

## Video-elementen publiceren {#publish-video-assets}

Na publicatie kunt u de video-elementen in een webpagina opnemen als een URL of de elementen rechtstreeks insluiten. Zie voor meer informatie [publish [!DNL Dynamic Media] elementen](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

## Video&#39;s publiceren naar YouTube {#publishing-videos-to-youtube}

U kunt video-elementen die in Experience Manager Assets worden beheerd, rechtstreeks publiceren naar een YouTube-kanaal dat u eerder hebt gemaakt.

Als u video-elementen naar YouTube wilt publiceren, kunt u tags toewijzen aan video-elementen in Experience Manager Assets. U koppelt deze tags aan een YouTube-kanaal. Als de tag van een video-element overeenkomt met de tag van een YouTube-kanaal, wordt de video gepubliceerd naar YouTube. Publiceren naar YouTube vindt plaats samen met een normale publicatie van de video zolang een bijbehorende tag wordt gebruikt.

YouTube voert zijn eigen codering uit. Als zodanig wordt het oorspronkelijke videobestand dat naar de Experience Manager is geüpload, gepubliceerd naar YouTube in plaats van elke video-uitvoering die door de codering van Dynamic Media is gemaakt. Hoewel het niet nodig is om video&#39;s te verwerken met Dynamic Media, wordt verwacht dat dit gebeurt voor het geval dat een viewer-voorinstelling nodig is voor het afspelen.

Wanneer u het videoverwerkingsprofiel overslaat en rechtstreeks naar YouTube publiceert, betekent dit gewoon dat uw video-element in Experience Manager Asset geen zichtbare miniatuur krijgt. Het betekent ook dat video&#39;s die niet zijn gecodeerd, niet werken met Dynamic Media-middelen.

Bij het publiceren van video-elementen naar YouTube-servers moeten de volgende taken worden uitgevoerd om een veilige en veilige server-naar-server verificatie met YouTube te garanderen:

1. [Google Cloud-instellingen configureren](#configuring-google-cloud-settings)
1. [Een YouTube-kanaal maken](#creating-a-youtube-channel)
1. [Codes toevoegen voor publicatie](#adding-tags-for-publishing)
1. [YouTube instellen in Experience Manager](#setting-up-youtube-in-aem)
1. [(Optioneel) Automatiseer de standaardeigenschappen van YouTube voor uw geüploade video&#39;s](#optional-automating-the-setting-of-default-youtube-properties-for-your-uploaded-videos)
1. [Video&#39;s publiceren naar uw YouTube-kanaal](#publishing-videos-to-your-youtube-channel)
1. [(Optioneel) Controleer de gepubliceerde video op YouTube](/help/assets/dynamic-media/video.md#optional-verifying-the-published-video-on-youtube)
1. [YouTube-URL&#39;s koppelen aan uw webtoepassing](#linking-youtube-urls-to-your-web-application)

U kunt [Publiceren van video&#39;s ongedaan maken om deze uit YouTube te verwijderen](#unpublishing-videos-to-remove-them-from-youtube).

### Google Cloud-instellingen configureren {#configuring-google-cloud-settings}

Als u wilt publiceren naar YouTube, hebt u een Google-account nodig. Als u een GMAIL-account hebt, hebt u al een Google-account. Als u geen Google-account hebt, kunt u er eenvoudig een maken. U hebt het account nodig omdat u aanmeldingsgegevens nodig hebt om video-elementen naar YouTube te publiceren. <!-- hidden March 3 2022 If you have an account already created, then skip this task and proceed directly to [Create a YouTube channel](#creating-a-youtube-channel). -->

Het account dat wordt gebruikt met Google Cloud en het Google-account dat wordt gebruikt voor YouTube, hoeft niet hetzelfde te zijn.

Google wijzigt regelmatig de gebruikersinterface. De stappen voor het publiceren van video&#39;s naar YouTube kunnen dan ook enigszins afwijken van wat hieronder wordt beschreven. Dit voorbehoud geldt ook voor YouTube wanneer u probeert te controleren of er video&#39;s naar worden geüpload.

>[!NOTE]
>
>De volgende stappen waren correct op het moment van schrijven. Google werkt echter regelmatig hun cloudwebpagina&#39;s bij zonder dat dit wordt gemeld. Daarom kunnen sommige configuratieopties in de Google-gebruikersinterface iets anders worden genoemd dan de naam die in de stappen wordt gebruikt.

**Google Cloud-instellingen configureren:**

1. Maak een Google-account.

   Als u al een Google-account hebt, kunt u de volgende stap overslaan.

1. Ga naar [https://cloud.google.com/](https://cloud.google.com/).
1. Op de **[!UICONTROL Google Cloud]** pagina, bij de rechterbovenhoek, selecteert u **[!UICONTROL Console]**.

   Indien nodig **[!UICONTROL Sign in]** met uw Google-accountgegevens de **[!UICONTROL Console]** -optie.

1. Op de **[!UICONTROL Dashboard]** pagina, rechts van **[!UICONTROL Google Cloud Platform]**, selecteert u de **[!UICONTROL Project]** vervolgkeuzelijst om de **[!UICONTROL Select a project]** in.
1. In de **[!UICONTROL Select a project]** dialoogvenster selecteert u **[!UICONTROL New Project]**.
1. In de **[!UICONTROL New Project]** in het dialoogvenster **[!UICONTROL Project name]** veld, typt u de naam van het nieuwe project.

   Uw project-id is gebaseerd op uw projectnaam. Kies daarom de projectnaam zorgvuldig en deze kan niet worden gewijzigd nadat deze is gemaakt. U moet dezelfde project-id opnieuw invoeren wanneer u YouTube later instelt in Experience Manager. Schrijf het daarom op.

1. Selecteren **[!UICONTROL Create]**.

1. Voer een van de volgende handelingen uit:

   * Op het dashboard van uw project, in **[!UICONTROL Getting Started]** kaart, selecteren **[!UICONTROL Explore and enable APIs]**.
   * Op het dashboard van uw project, in **[!UICONTROL APIs]** kaart, selecteren **[!UICONTROL Go to APIs overview]**.

1. In het midden boven **[!UICONTROL APIs & Services]** pagina, selecteert u **[!UICONTROL ENABLE APIS AND SERVICES]**.<!-- NEXT STEP BELOW IS STEP 10 -->
1. Op de **[!UICONTROL API Library]** pagina, links, onder **[!UICONTROL Category]**, selecteert u **[!UICONTROL YouTube]**. Selecteer rechts van de pagina de optie **[!UICONTROL YouTube]**.
1. Op de **[!UICONTROL YouTube]** pagina, selecteert u **[!UICONTROL YouTube Data API v3]**.
1. Op de **[!UICONTROL YouTube Data API v3]** pagina, selecteert u **[!UICONTROL MANAGE]**.

   ![6_5_googleaccount-apis-manage](/help/assets/dynamic-media/assets/6_5_googleaccount-apis-manage.png)

1. U hebt referenties nodig om de API te gebruiken. Indien nodig, aan de linkerkant van de **[!UICONTROL APIs & Services]** pagina, selecteert u **[!UICONTROL Credentials]**.
1. Op de **[!UICONTROL Credentials]** pagina, bij de bovenkant, selecteer **[!UICONTROL CREATE CREDENTIALS]** selecteert u vervolgens **[!UICONTROL OAuth client ID]**.
1. Op de **[!UICONTROL Create OAuth client ID]** pagina, in de **[!UICONTROL Application type]** vervolgkeuzelijst, selecteert u **[!UICONTROL Web application]**.

   ![6_5_googleaccount-apis-applicationtype](/help/assets/dynamic-media/assets/6_5_googleaccount-apis-applicationtype.png)

1. Voer een van de volgende handelingen uit:

   * In de **[!UICONTROL Name]** Voer een unieke naam in voor uw OAuth 2.0-client.
   * Gebruik de standaardnaam die Google al heeft opgegeven in het dialoogvenster **[!UICONTROL Name]** veld.

1. Onder de **[!UICONTROL Authorized JavaScript origins]** kop, selecteren **[!UICONTROL ADD URI]**.

   ![6_5_googleaccount-apis-nameAuthorizations](/help/assets/dynamic-media/assets/6_5_googleaccount-apis-nameauthorizations.png)

1. In de **[!UICONTROL URIs]** tekstveld, voer het volgende pad in en vervang uw eigen domein- en poortnummer in het pad. Druk vervolgens op **[!UICONTROL Enter]** om het pad aan de lijst toe te voegen:

   `https://<servername.domain>:<port_number>`

   Bijvoorbeeld: `https://1a2b3c.mycompany.com:4321`

   >[!NOTE]
   >
   >Het bovenstaande URI-padvoorbeeld is hypothetisch en alleen ter uitleg.

1. Onder de **[!UICONTROL Authorized redirect URIs]** Selecteer URI TOEVOEGEN.
1. In de **[!UICONTROL URIs]** tekstveld, voer het volgende pad in en vervang uw eigen domein- en poortnummer in het pad. Druk vervolgens op **[!UICONTROL Enter]** om het pad aan de lijst toe te voegen:

   `https://<servername.domain>:<port_number>/etc/cloudservices/youtube.youtubecredentialcallback.json`

   Bijvoorbeeld: `https://1a2b3c.mycompany.com:4321/etc/cloudservices/youtube.youtubecredentialcallback.json`

   >[!NOTE]
   >
   >Het bovenstaande URI-padvoorbeeld is hypothetisch en alleen ter uitleg.

1. Onder aan de **[!UICONTROL Create OAuth client ID]** pagina, selecteert u **[!UICONTROL Create]**.
1. Op de **[!UICONTROL OAuth client created]** voert u de volgende handelingen uit:

   * (Optioneel) Kopieer de waarden in het dialoogvenster **[!UICONTROL Your Client ID]** en **[!UICONTROL Your Client Secret]** en sla deze op.
   * Selecteren **[!UICONTROL DOWNLOAD JSON]** en sla het JSON-bestand op.

   U hebt dit gedownloade JSON-bestand nodig wanneer u YouTube later instelt in Adobe Experience Manager.

   ![6_5_googleaccount-apis-oauthclientcreated](/help/assets/dynamic-media/assets/6_5_googleaccount-apis-oauthclientcreated.png)

1. Op de **[!UICONTROL OAuth client created]** dialoogvenster selecteert u **[!UICONTROL OK]**.
1. Log uit op je Google account. Maak nu een YouTube-kanaal.

### Een YouTube-kanaal maken {#creating-a-youtube-channel}

Voor het publiceren van video&#39;s naar YouTube hebt u een of meer kanalen nodig. Als u al een YouTube-kanaal hebt gemaakt, kunt u deze taak overslaan en naar [Codes toevoegen voor publicatie](/help/assets/dynamic-media/video.md#adding-tags-for-publishing).

>[!CAUTION]
>
>Zorg ervoor dat u al een of meer kanalen hebt ingesteld in YouTube *voor* u voegt kanalen toe onder YouTube Settings in Experience Manager (zie [YouTube instellen in Experience Manager](#setting-up-youtube-in-aem) hieronder). Als u de kanaalinstelling niet kunt uitvoeren, wordt u niet gewaarschuwd dat er geen bestaande kanalen zijn. Google-verificatie vindt echter nog steeds plaats wanneer u een kanaal toevoegt, maar er is geen optie om te kiezen welk kanaal de video wordt verzonden.

**Een YouTube-kanaal maken:**

1. Ga naar [https://www.youtube.com](https://www.youtube.com/) en meld u aan met uw Google-accountgegevens.
1. Selecteer in de rechterbovenhoek van de YouTube-pagina uw profielafbeelding (deze kan ook als een letter binnen een effen gekleurde cirkel worden weergegeven) en selecteer vervolgens **[!UICONTROL YouTube settings]** (rondtandwielpictogram).
1. Selecteer op de pagina Overzicht onder de kop Extra functies de optie **[!UICONTROL See all my channels or create a channel]**.
1. Selecteer op de pagina Kanalen de optie **[!UICONTROL Create a new channel]**.
1. Voer op de pagina Brand Account in het veld Brand Account Name een bedrijfsnaam of een andere kanaalnaam in die u kiest waar u de video-elementen wilt publiceren en selecteer vervolgens **[!UICONTROL Create]**.

   Onthoud de naam die u hier invoert. Voer deze naam opnieuw in wanneer u YouTube in Experience Manager moet instellen.

1. (Optioneel) Voeg desgewenst meer kanalen toe.

   Nu voegt u labels toe voor publicatie.

### Codes toevoegen voor publicatie {#adding-tags-for-publishing}

Als u video&#39;s naar YouTube wilt publiceren, koppelt de Experience Manager de tags aan een of meer YouTube-kanalen. Als u tags wilt toevoegen voor publicatie, raadpleegt u [Tags beheren](/help/sites-cloud/authoring/sites-console/tags.md).

Of als u de standaardlabels in de Experience Manager wilt gebruiken, kunt u deze taak overslaan en naar [YouTube instellen in Experience Manager](#setting-up-youtube-in-aem).

>[!NOTE]
>
>Nadat de Cloud Service wordt gevormd, wordt andere configuratie niet vereist om YouTube toe te laten publiceer replicatieagent op dit punt. De reden is omdat het werd toegelaten toen de configuratie van de Cloud Service werd bewaard.

<!-- ### Enabling the YouTube Publish replication agent {#enabling-the-youtube-publish-replication-agent}

After you enable the YouTube Publish replication agent, if you want to test the connection to the Google Cloud account, select **[!UICONTROL Test Connection]**. A browser tab displays the connection results. If you have added YouTube Channels, then a listing of those is displayed as part of the test.

1. In the upper-left corner of Experience Manager, select the Experience Manager logo, then in the left rail, navigate to **[!UICONTROL Tools]** > **[!UICONTROL Deployment]** > **[!UICONTROL Replication]** > **[!UICONTROL Agents on Author]**.
1. On the Agents of Author page, select **[!UICONTROL YouTube Publish (youtube)]**.
1. On the toolbar, to the right of Settings, select **[!UICONTROL Edit]**.
1. Select the **[!UICONTROL Enabled]** checkbox to turn on the replication agent.
1. Select **[!UICONTROL OK]**. -->

### YouTube instellen in Experience Manager {#setting-up-youtube-in-aem}

Vanaf Experience Manager 6.4 is een nieuwe aanraakgebruikersinterfacemethode geïntroduceerd om YouTube-publicaties in Experience Manager in te stellen. Op basis van de geïnstalleerde Experience Manager die u gebruikt, voert u een van de volgende handelingen uit:

* Om YouTube in Experience Manager vóór 6.4 te vormen, zie [YouTube instellen in Experience Manager vóór 6.4](/help/assets/dynamic-media/video.md#setting-up-youtube-in-aem-before).
* Om YouTube in Experience Manager 6.4 of later te vormen, zie [YouTube instellen in Experience Manager 6.4 en hoger](#setting-up-youtube-in-aem-and-later).

#### YouTube instellen in Experience Manager 6.4 en hoger {#setting-up-youtube-in-aem-and-later}

1. Meld u als beheerder aan bij uw exemplaar van Dynamic Media.
1. Selecteer in de linkerbovenhoek van de Experience Manager het logo van de Experience Manager en navigeer vervolgens in de linkerspoorstaaf naar **[!UICONTROL Tools]**(hamerpictogram) > **[!UICONTROL Cloud Services]** > **[!UICONTROL YouTube Publishing Configuration]**.
1. Selecteren **[!UICONTROL global]** (niet selecteren).

1. Selecteer in de rechterbovenhoek van de algemene pagina de optie **[!UICONTROL Create]**.
1. Voer op de pagina YouTube-configuratie maken onder Google Cloud-platforminstellingen in het veld **[!UICONTROL Application Name]** de Google-project-id in.

   U hebt de project-id opgegeven toen u de Google Cloud-instellingen voor het eerst eerder hebt geconfigureerd.
Laat de pagina YouTube-configuratie maken open. U keert er zo meteen naar terug.

   ![6_5_youtubepublish-createyoutubeconfiguration](/help/assets/dynamic-media/assets/6_5_youtubepublish-createyoutubeconfiguration.png)

1. Open met een teksteditor zonder opmaak het JSON-bestand dat u eerder in de taak hebt gedownload en opgeslagen [Google Cloud-instellingen configureren](/help/assets/dynamic-media/video.md#configuring-google-cloud-settings).
1. Selecteer en kopieer de volledige JSON-tekst.
1. Ga terug naar het dialoogvenster YouTube-accountinstellingen. Plak de JSON-tekst in het veld **[!UICONTROL JSON Config]**.
1. Selecteer rechtsboven in de pagina de optie **[!UICONTROL Save]**.

   Stel nu YouTube-kanalen in Experience Manager in.

1. Selecteren **[!UICONTROL Add Channel]**.
1. Voer in het veld Kanaalnaam de naam in van het kanaal dat u in de taak hebt gemaakt **[!UICONTROL Adding one or more channels to YouTube]** eerder.

   U kunt desgewenst een beschrijving toevoegen.

1. Selecteren **[!UICONTROL Add]**.
1. YouTube/Google-verificatie wordt weergegeven. Als u zich nog niet hebt aangemeld bij het Google Cloud-account, slaat u deze stap over.

   * Voer de Google-gebruikersnaam en het wachtwoord in die aan de Google Project ID en de JSON-tekst hierboven zijn gekoppeld.
   * Afhankelijk van hoeveel kanalen uw account twee of meer items bevat. Selecteer een kanaal. Selecteer het e-mailadres niet, het is geen kanaal.
   * Selecteer op de volgende pagina de optie **[!UICONTROL Accept]** toegang tot dit kanaal toestaan.

1. Selecteren **[!UICONTROL Allow]**.

   Stel nu labels in voor publicatie.

1. **[!UICONTROL Setting up tags for publishing]** - Selecteer op de pagina Cloud Servicen > YouTube het potloodpictogram om de lijst met tags die u wilt gebruiken te bewerken.
1. Als u de lijst met beschikbare labels in de Experience Manager wilt weergeven, selecteert u het vervolgkeuzelijstpictogram (ondersteboven ingedrukt caret).
1. Selecteer een of meer tags om deze toe te voegen.

   Als u een toegevoegde tag wilt verwijderen, selecteert u de tag en selecteert u **[!UICONTROL X]**.

1. Wanneer u de gewenste tags hebt toegevoegd, selecteert u **[!UICONTROL Save]**.

   Nu publiceert u video&#39;s naar uw YouTube-kanaal.

#### YouTube instellen in Experience Manager vóór 6.4 {#setting-up-youtube-in-aem-before}

1. Meld u als beheerder aan bij uw exemplaar van Dynamic Media.

1. Selecteer in de linkerbovenhoek van de Experience Manager het logo van de Experience Manager en navigeer vervolgens in de linkerspoorstaaf naar **[!UICONTROL Tools]** (hamerpictogram) > **[!UICONTROL Deployment]** > **[!UICONTROL Cloud Services]**.
1. Selecteer onder YouTube onder de kop Services van derden de optie **[!UICONTROL Configure now]**.
1. Voer in het dialoogvenster Configuratie maken een titel (verplicht) en een naam (optioneel) in de desbetreffende velden in.
1. Selecteren **[!UICONTROL Create]**.
1. Voer in het veld **[!UICONTROL Application Name]** in het dialoogvenster YouTube-accountinstellingen de Google-project-id in.

   U hebt de project-id opgegeven toen u het eerst [geconfigureerde Google Cloud-instellingen](/help/assets/dynamic-media/video.md#configuring-google-cloud-settings) eerder.
Laat het dialoogvenster YouTube-accountinstellingen open. U keert er zo meteen naar terug.

1. Open met een teksteditor zonder opmaak het JSON-bestand dat u eerder hebt gedownload en opgeslagen in de taak Google Cloud-instellingen configureren.
1. Selecteer en kopieer de volledige JSON-tekst.
1. Ga terug naar het dialoogvenster YouTube-accountinstellingen. Plak de JSON-tekst in het veld **[!UICONTROL JSON Config]**.
1. Selecteren **[!UICONTROL OK]**.

   Stel nu YouTube-kanalen in Experience Manager in.

1. Aan het recht van **[!UICONTROL Available Channels]**, selecteert u **+** (plusteken).
1. Voer in het veld Titel in het dialoogvenster YouTube-kanaalinstellingen de naam in van het kanaal dat u eerder in de taak **[!UICONTROL Adding one or more channels to YouTube]** hebt gemaakt.

   U kunt desgewenst een beschrijving toevoegen.

1. Selecteren **[!UICONTROL OK]**.
1. YouTube/Google-verificatie wordt weergegeven. Als u zich nog niet hebt aangemeld bij het Google Cloud-account, slaat u deze stap over.

   * Voer de Google-gebruikersnaam en het wachtwoord in die aan de Google Project ID en de JSON-tekst hierboven zijn gekoppeld.
   * Afhankelijk van hoeveel kanalen uw account twee of meer items bevat. Selecteer een kanaal. Selecteer het e-mailadres niet, het is geen kanaal.
   * Selecteer op de volgende pagina de optie **[!UICONTROL Accept]** toegang tot dit kanaal toestaan.

1. Selecteren **[!UICONTROL Allow]**.

   Stel nu labels in voor publicatie.

1. **[!UICONTROL Setting up tags for publishing]** - Selecteer op de pagina Cloud Servicen > YouTube het potloodpictogram om de lijst met tags die u wilt gebruiken te bewerken.
1. Als u de lijst met beschikbare labels in de Experience Manager wilt weergeven, selecteert u het vervolgkeuzelijstpictogram (ondersteboven ingedrukt caret).
1. Selecteer een of meer tags om deze toe te voegen.

   Als u een toegevoegde tag wilt verwijderen, selecteert u de tag en selecteert u **X**.

1. Wanneer u de gewenste tags hebt toegevoegd, selecteert u **[!UICONTROL OK]**.

   Nu publiceert u video&#39;s naar uw YouTube-kanaal.

### (Optioneel) Automatiseer de standaardeigenschappen van YouTube voor uw geüploade video&#39;s {#optional-automating-the-setting-of-default-youtube-properties-for-your-uploaded-videos}

U kunt desgewenst de instelling van YouTube-eigenschappen automatiseren bij het uploaden van uw video&#39;s. Maak een verwerkingsprofiel voor metagegevens in de Experience Manager.

Als u het verwerkingsprofiel voor metadata wilt maken, kopieert u eerst waarden uit de velden **[!UICONTROL Field Label]**, **[!UICONTROL Map to property]** en **[!UICONTROL Choices]** die te vinden zijn in de metadataschema&#39;s voor video. Vervolgens kunt u het verwerkingsprofiel voor YouTube-videometagegevens samenstellen door deze waarden eraan toe te voegen.

**U kunt als volgt de standaardeigenschappen van YouTube voor uw geüploade video&#39;s automatiseren:**

1. Selecteer in de linkerbovenhoek van de Experience Manager het logo van de Experience Manager en navigeer vervolgens in de linkerspoorstaaf naar **[!UICONTROL Tools]** (hamerpictogram) > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Schemas]**.
1. Selecteer **[!UICONTROL default]**. (Voeg geen vinkje toe aan het selectievak links van &quot;standaard&quot;.)
1. Op de **[!UICONTROL default]** pagina, schakel het selectievakje links van **[!UICONTROL video]** selecteert u vervolgens **[!UICONTROL Edit]**.
1. Selecteer op de pagina Metadata Schema Editor de optie **[!UICONTROL Advanced]** tab.
1. Selecteer onder YouTube Publishing (Publiceren in) de optie **[!UICONTROL YouTube Category]**.
1. Aan de rechterkant van de pagina, onder de **[!UICONTROL Settings]** doet u het volgende:

   * In de **[!UICONTROL Map to property]** tekstveld, selecteer en kopieer de waarde.
Plak de gekopieerde waarde in de geopende teksteditor. Deze waarde hebt u later nodig wanneer u uw verwerkingsprofiel voor metagegevens maakt. Laat de teksteditor geopend.

   * Onder **[!UICONTROL Choices]**selecteert en kopieert u de standaardwaarde die u wilt gebruiken (zoals Personen en blogs of Wetenschap en Technologie).
Plak de gekopieerde waarde in de geopende teksteditor. Deze waarde hebt u later nodig wanneer u uw verwerkingsprofiel voor metagegevens maakt. Laat de teksteditor geopend.

1. Selecteer onder YouTube Publishing (Publiceren in) de optie **[!UICONTROL YouTube Privacy]**.
1. Aan de rechterkant van de pagina, onder de **[!UICONTROL Settings]** doet u het volgende:

   * In de **[!UICONTROL Map to property]** tekstveld, selecteer en kopieer de waarde.
Plak de gekopieerde waarde in de geopende teksteditor. Deze waarde hebt u later nodig wanneer u uw verwerkingsprofiel voor metagegevens maakt. Laat de teksteditor geopend.

   * Onder **[!UICONTROL Choices]**selecteert en kopieert u de standaardwaarde die u wilt gebruiken. De keuzen zijn gegroepeerd in twee. Het onderste veld in het paar is de standaardwaarde die u wilt kopiëren, bijvoorbeeld public, unlist of private.
Plak de gekopieerde waarde in de geopende teksteditor. Deze waarde hebt u later nodig wanneer u uw verwerkingsprofiel voor metagegevens maakt. Laat de teksteditor geopend.

1. Selecteer in de rechterbovenhoek van de pagina Metadata Schema Editor de optie **[!UICONTROL Cancel]**.
1. Selecteer in de linkerbovenhoek van de Experience Manager het logo van de Experience Manager en selecteer vervolgens in de linkerspoorstaaf de optie **[!UICONTROL Tools]** (hamerpictogram) > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Profiles]**.

1. Selecteer in de rechterbovenhoek van de pagina Metagegevensprofielen de optie **[!UICONTROL Create]**.
1. In het dialoogvenster Metagegevensprofiel toevoegen vindt u in het dialoogvenster **[!UICONTROL Profile title]** tekstveld, voer de naam in `YouTube Video` Selecteer vervolgens **[!UICONTROL Create]**.
1. Selecteer op de pagina Metadata Profile Editor de optie **[!UICONTROL Advance]** tab.
1. Voeg de gekopieerde YouTube Publishing-waarden als volgt toe aan het profiel:

   * Selecteer rechts van de pagina de optie **[!UICONTROL Build Form]** tab.
   * (Optioneel) Sleep de component met het label **[!UICONTROL Section Header]** naar links en zet deze neer in het formuliergebied.
   * (Optioneel) Selecteer **[!UICONTROL Field Label]** om de component te selecteren.
   * (Optioneel) Typ rechts van de pagina onder het tabblad Instellingen in het tekstveld Veld Label de tekst `YouTube Publishing`.
   * Selecteer de **[!UICONTROL Build Form]** en sleep de component met het label **[!UICONTROL Multi Value Text]** en laat het onder de **[!UICONTROL YouTube Publishing]** koptekst die u hebt gemaakt.

   * Selecteer de component **[!UICONTROL Field Label]**.
   * Plak rechts van de pagina, onder het tabblad Instellingen, de YouTube Publishing-waarden (Field Label value en Map to property value) die u eerder hebt gekopieerd, in hun respectievelijke velden op het formulier. Plak de waarde Keuzen in het veld Standaardwaarde.

1. Voeg de gekopieerde YouTube-privacywaarden als volgt toe aan het profiel:

   * Selecteer rechts van de pagina de optie **[!UICONTROL Build Form]** tab.
   * (Optioneel) Sleep de component met het label **[!UICONTROL Section Header]** naar links en zet deze neer in het formuliergebied.
   * (Optioneel) Selecteer **[!UICONTROL Field Label]** om de component te selecteren.
   * (Optioneel) Typ rechts van de pagina onder het tabblad Instellingen in het tekstveld Veld Label de tekst `YouTube Privacy`.
   * Selecteer de **[!UICONTROL Build Form]** en sleep de component met het label **[!UICONTROL Multi Value Text]** en laat het onder de **[!UICONTROL YouTube Privacy]** door u gemaakte koptekst.

   * Selecteer de component **[!UICONTROL Field Label]**.
   * Plak rechts van de pagina, onder het tabblad Instellingen, de YouTube Publishing-waarden (Field Label value en Map to property value) die u eerder hebt gekopieerd, in hun respectievelijke velden op het formulier. Plak de waarde Keuzen in het veld Standaardwaarde.

1. Selecteer rechtsboven in de pagina de optie **[!UICONTROL Save]**.
1. Pas het metagegevensprofiel voor YouTube Publishing toe op de mappen waarin u video&#39;s gaat uploaden. U moet zowel het profiel Metagegevens als het videoprofiel hebben ingesteld.

   Zie [Metadataprofielen](/help/assets/metadata-profiles.md) en [Videoprofielen](/help/assets/dynamic-media/video-profiles.md).

### Video&#39;s publiceren naar uw YouTube-kanaal {#publishing-videos-to-your-youtube-channel}

Nu associeert u de markeringen die u eerder aan videoactiva toevoegde. Dit proces stelt de Experience Manager in kennis van de elementen die naar uw YouTube-kanaal moeten worden gepubliceerd.

>[!NOTE]
>
>Publiceren wordt niet automatisch naar YouTube gepubliceerd. Wanneer Dynamische media is ingesteld, zijn er twee publicatieopties waaruit u kunt kiezen: **[!UICONTROL Immediately]** of **[!UICONTROL Upon Activation]**.
>
>**[!UICONTROL Publish Immediately]** betekent dat het geüploade element-nadat het met IPS-wordt gesynchroniseerd automatisch aan het leveringssysteem wordt gepubliceerd. Dat geldt voor Dynamic Media, maar dat geldt niet voor YouTube. Als u wilt publiceren naar YouTube, moet u publiceren als Experience Manager Auteur.

>[!NOTE]
>
>Voor het publiceren van inhoud vanuit YouTube gebruikt Experience Manager de optie **[!UICONTROL Publish to YouTube]** werkstroom, waarmee u de voortgang kunt controleren en eventuele foutgegevens kunt bekijken.
>
>Zie [Video-codering en YouTube-publicatievoortgang controleren](#monitoring-video-encoding-and-youtube-publishing-progress).
>
>Voor gedetailleerdere voortgangsgegevens kunt u het YouTube-logboek onder replicatie controleren. Houd er echter rekening mee dat voor dergelijke bewaking beheerderstoegang vereist is.

**Video&#39;s publiceren naar uw YouTube-kanaal:**

1. Navigeer in Experience Manager naar een video-element dat u naar het YouTube-kanaal wilt publiceren.
1. Selecteer het video-element (de adaptieve videoset).
1. Selecteer op de werkbalk de optie **[!UICONTROL Properties]**.
1. Selecteer op het tabblad Standaard onder de kop Metagegevens de optie **[!UICONTROL Open Selection Dialog]** rechts van het veld Tags.
1. Navigeer op de pagina Codes selecteren naar de gewenste codes en selecteer een of meer codes.

   Vergeet niet dat de tags moeten worden gekoppeld aan het YouTube-kanaal.

1. Selecteer in de rechterbovenhoek van de pagina de optie **[!UICONTROL Select]**.
1. Selecteer in de rechterbovenhoek van de eigenschappenpagina van de video de optie **[!UICONTROL Save and Close]**.
1. Selecteer op de werkbalk de optie **[!UICONTROL Quick Publish]**.

   Zie ook [Publicatiebeheer gebruiken met Experience Manager Sites](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/page-authoring/publication-management-feature-video-use.html#page-authoring).

   U kunt desgewenst de gepubliceerde video op uw YouTube-kanaal verifiëren.

### (Optioneel) Controleer de gepubliceerde video op YouTube {#optional-verifying-the-published-video-on-youtube}

U kunt optioneel de voortgang van het publiceren van YouTube (of het ongedaan maken van het publiceren) volgen.

Zie [Video-codering en YouTube-publicatievoortgang controleren](#monitoring-video-encoding-and-youtube-publishing-progress).

De het publiceren tijden kunnen zeer afhankelijk van talrijke factoren variëren die het formaat van uw primaire bronvideo, dossiergrootte, en uploadverkeer omvatten. Het publicatieproces kan een paar minuten tot enkele uren duren. Bovendien worden indelingen met een hogere resolutie veel langzamer gerenderd. Het duurt bijvoorbeeld langer om 720p en 1080p weer te geven dan 480p.

Na acht uur, als u nog een statusbericht ziet dat **[!UICONTROL Uploaded (processing, please wait)]**, verwijdert u de video van uw site en uploadt u deze opnieuw.

### YouTube-URL&#39;s koppelen aan uw webtoepassing {#linking-youtube-urls-to-your-web-application}

U kunt een YouTube URL-tekenreeks verkrijgen die door Dynamic Media wordt gegenereerd nadat u de video hebt gepubliceerd. Wanneer u de YouTube-URL kopieert, wordt deze op het Klembord gedownload, zodat u deze indien nodig kunt plakken naar pagina&#39;s in uw website of toepassing.

>[!NOTE]
>
>De YouTube-URL kan pas worden gekopieerd nadat u het video-element naar YouTube hebt gepubliceerd.

YouTube-URL&#39;s koppelen aan uw webtoepassing:

1. Ga naar de *YouTube gepubliceerd* video-element waarvan u de URL die u wilt kopiëren wilt selecteren.

   Houd er rekening mee dat YouTube-URL&#39;s alleen beschikbaar zijn om te kopiëren *na* u hebt de eerste *gepubliceerd* de video-elementen naar YouTube.

1. Selecteer op de werkbalk de optie **[!UICONTROL Properties]**.
1. Selecteer de **[!UICONTROL Advanced]** tab.
1. Selecteer onder YouTube Publishing in de URL-lijst van YouTube de URL-tekst die u naar uw webbrowser wilt kopiëren om een voorvertoning van het element weer te geven of om deze toe te voegen aan uw pagina met webinhoud.

### Publicatie van video&#39;s ongedaan maken zodat u deze kunt verwijderen uit YouTube {#unpublishing-videos-to-remove-them-from-youtube}

Wanneer u de publicatie van een video-element in Experience Manager ongedaan maakt, wordt de video verwijderd uit YouTube.

>[!CAUTION]
>
>Als u een video rechtstreeks uit YouTube verwijdert, is de Experience Manager zich hiervan niet bewust en gedragen deze zich alsof de video nog steeds naar YouTube wordt gepubliceerd. Publiceer de publicatie van een video-element vanuit YouTube altijd ongedaan als Experience Manager.

>[!NOTE]
>
>Om inhoud uit YouTube te verwijderen, gebruikt de Experience Manager **[!UICONTROL Unpublish from YouTube]** werkstroom, waarmee u de voortgang kunt controleren en eventuele foutgegevens kunt bekijken.
>
>Zie [Video-codering en YouTube-publicatievoortgang controleren](#monitoring-video-encoding-and-youtube-publishing-progress).

**Publiceren van video&#39;s ongedaan maken om deze uit YouTube te verwijderen:**

1. Navigeer naar de video-elementen waarvan u de publicatie via uw YouTube-kanaal wilt ongedaan maken.
1. Selecteer in de modus voor middelenselectie een of meer gepubliceerde video-elementen.
1. Selecteer op de werkbalk de optie **[!UICONTROL Manage Publication]**. Selecteer indien nodig het pictogram met drie puntjes (`. . .`) op de werkbalk om te zien **[!UICONTROL Manage Publication]**.
1. Selecteer op de pagina Publicatie beheren de optie **[!UICONTROL Unpublish]**.
1. Selecteer in de rechterbovenhoek van de pagina de optie **[!UICONTROL Next]**.
1. Selecteer in de rechterbovenhoek van de pagina de optie **[!UICONTROL Unpublish]**.

## Video-codering en YouTube-publicatievoortgang controleren {#monitoring-video-encoding-and-youtube-publishing-progress}

Wanneer u een nieuwe video uploadt naar een map waarop videocodering is toegepast of wanneer u uw video publiceert naar YouTube, controleert u hoe de videocodering/YouTube-publicatie vordert (of mislukt). Werkelijke vorderingen bij het publiceren in YouTube zijn alleen beschikbaar via de logboeken. Maar of het ontbreekt of slaagt, is het vermeld op andere manieren die in de volgende procedure worden beschreven. Bovendien ontvangt u e-mailmeldingen wanneer een publicatieworkflow of videocodering van YouTube is voltooid of onderbroken.

### Voortgang van controle {#monitoring-progress}

U kunt de voortgang controleren, inclusief mislukte codering/YouTube-publicatie.

1. De voortgang van videocodering weergeven in de map met elementen:

   * In de kaartweergave wordt de voortgang van de videocodering met een percentage weergegeven op het element. Als er een fout optreedt, wordt deze informatie ook weergegeven op het element.

   ![chlimage_1-429](/help/assets/dynamic-media/assets/chlimage_1-429.png)

   * In de lijstweergave wordt de voortgang van de videocodering weergegeven in het dialoogvenster **[!UICONTROL Processing Status]** kolom. Als er een fout is, toont dit bericht in die zelfde kolom.

   ![chlimage_1-430](/help/assets/dynamic-media/assets/chlimage_1-430.png)

   Deze kolom wordt niet standaard weergegeven. Selecteer **[!UICONTROL View Settings]** in het vervolgkeuzemenu Weergaven en voeg de opdracht **[!UICONTROL Processing Status]** kolom en selecteer **[!UICONTROL Update]**.

   ![chlimage_1-431](/help/assets/dynamic-media/assets/chlimage_1-431.png)

1. De voortgang van de elementen weergeven. Wanneer u een element selecteert, opent u het keuzemenu en selecteert u **[!UICONTROL Timeline]**. Selecteer **[!UICONTROL Workflows]**.

   ![chlimage_1-432](/help/assets/dynamic-media/assets/chlimage_1-432.png)

   Workflowinformatie, zoals codering, wordt weergegeven in de tijdlijn. Voor YouTube-publicatie bevat de tijdlijn van de workflow ook de naam van het YouTube-kanaal en de YouTube-video-URL. Bovendien ziet u eventuele foutmeldingen in de tijdlijn van de workflow nadat het publiceren is voltooid.

   >[!NOTE]
   >
   >Het kan lang duren voordat foutberichten of foutberichten definitief worden opgenomen omdat er meerdere workflowconfiguraties zijn **[!UICONTROL retries]**, **[!UICONTROL retry delay]**, en **[!UICONTROL timeout]** van [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr), bijvoorbeeld:
   >
   >* Configuratie Apache Sling-taakwachtrij
   >* Adobe Granite Workflow External Process Handler
   >* Tijdelijke wachtrij voor Granite Workflow
   >
   >U kunt de **[!UICONTROL retries]**, **[!UICONTROL retry delay]**, en **[!UICONTROL timeout]** eigenschappen in deze configuraties.

1. Zie Workflowinstanties beschikbaar via **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Instances]** voor actieve workflows.

   >[!NOTE]
   >
   >U hebt beheerdersrechten nodig voor toegang tot de **[!UICONTROL Tools]** -menu.

   ![chlimage_1-433](/help/assets/dynamic-media/assets/chlimage_1-433.png)

   Selecteer de instantie en selecteer **[!UICONTROL Open History]**.

   ![chlimage_1-434](/help/assets/dynamic-media/assets/chlimage_1-434.png)

   Vanuit het gebied Workflowinstanties kunt u workflows ook opschorten, beëindigen of hernoemen. Zie [Workflows beheren](/help/sites-cloud/authoring/workflows/overview.md) voor meer informatie .

1. Voor mislukte taken raadpleegt u de beschikbare workflowfouten in **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Failures]**. De lijst **[!UICONTROL Workflow Failure]** bevat alle mislukte workflowactiviteiten.

   >[!NOTE]
   >
   >U hebt beheerdersrechten nodig voor toegang tot de **[!UICONTROL Tools]** -menu.

   ![chlimage_1-435](/help/assets/dynamic-media/assets/chlimage_1-435.png)

   >[!NOTE]
   >
   >Het kan lang duren voordat het foutbericht eindelijk is opgenomen omdat er meerdere workflowconfiguraties zijn **[!UICONTROL retries]**, **[!UICONTROL retry delay]**, en **[!UICONTROL timeout]** van [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr), bijvoorbeeld:
   >
   >* Configuratie Apache Sling-taakwachtrij
   >* Adobe Granite Workflow External Process Handler
   >* Tijdelijke wachtrij voor Granite Workflow
   >
   >U kunt de **[!UICONTROL retries]**, **[!UICONTROL retry delay]**, en **[!UICONTROL timeout]** eigenschappen in deze configuraties.

1. Zie Workflowarchief in **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Archive]** voor voltooide workflows. In **[!UICONTROL Workflow Archive]** vindt u een lijst met alle voltooide workflowactiviteiten.

   >[!NOTE]
   >
   >U hebt beheerdersrechten nodig voor toegang tot de **[!UICONTROL Tools]** -menu.

   ![chlimage_1-436](/help/assets/dynamic-media/assets/chlimage_1-436.png)

1. U ontvangt e-mailmeldingen over afgebroken of mislukte workflowtaken. Deze e-mailberichten kunnen door een beheerder worden geconfigureerd. Zie [E-mailmeldingen configureren](#configuring-e-mail-notifications).

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

[!DNL Experience Manager] als [!DNL Cloud Service] Hiermee kunt u MP4-videobestanden op een standaardmanier transcoderen met behulp van Profielen verwerken. Met deze functie kunt u niet alleen een MP4-videobestand uploaden, maar ook een voorvertoning weergeven en schalen.

![Verwerkingsprofiel maken voor videotranscodering in [!DNL Experience Manager]](assets/video-processing-profile-for-mp4.png)

*Afbeelding: Een verwerkingsprofiel voor videotranscodering in [!DNL Experience Manager].*

Als u alleen de breedte of alleen de hoogte opgeeft en het andere veld leeg laat, behouden de uitvoeringen de hoogte-breedteverhouding. H.264-videocodec is beschikbaar voor transcodering.

Als u elementen wilt verwerken met een verwerkingsprofiel, voegt u een profiel toe aan een map. Zie [verwerkingsprofielen gebruiken om elementen te verwerken](/help/assets/asset-microservices-configure-and-use.md#use-profiles).

## Video-elementen notities aanbrengen {#annotate-video-assets}

U kunt notities toevoegen aan video-elementen. Tijdens het annoteren van video&#39;s pauzeert de speler zodat u notities kunt aanbrengen in een frame. Zie voor meer informatie [beheren, video-elementen](manage-video-assets.md).

>[!NOTE]
>
>MXF-video-indeling wordt nog niet ondersteund met aantekeningen van video-elementen.

1. Van de [!DNL Assets] console, selecteren **[!UICONTROL Edit]** op de elementenkaart om de pagina met elementdetails weer te geven.
1. Klik op **[!UICONTROL Preview]**.
1. Als u de video wilt annoteren, klikt u op **[!UICONTROL Annotate]**. Er wordt een aantekening toegevoegd op het specifieke tijdstip (frame) in de video. Wanneer u notities maakt, kunt u op het canvas tekenen en een opmerking bij de tekening opnemen. Opmerkingen worden automatisch opgeslagen. Als u de wizard Annotatie wilt afsluiten, klikt u op **[!UICONTROL Close]**.
1. Zoek naar een specifiek punt in de video, geef de tijd in seconden op in het veld voor **tekst** en klik op **Springen**. Als u bijvoorbeeld de eerste 20 seconden van de video wilt overslaan, voert u 20 in het tekstveld in.
1. Klik op een annotatie om deze in de tijdlijn weer te geven. Als u de annotatie uit de tijdlijn wilt verwijderen, klikt u op **[!UICONTROL Delete]**.

## Aanbevolen werkwijzen en beperkingen {#tips-limitations}

* Zonder [!DNL Dynamic Media] -licentie, kunt u alleen MP4-bestanden verwerken met behulp van verwerkingsprofielen.
* Bij het transcoderen van MP4-bestanden met verwerkingsprofielen gelden de volgende richtlijnen en beperkingen:

   * Apple ProRes-bestanden kunnen alleen transcoderen naar een maximale resolutie van 1080p.
   * Als het bronbestand een bitsnelheid > 200 Mbps heeft, kunt u alleen transcoderen naar een maximale resolutie van 1080p.
   * Als de bronframesnelheid >=60 fps is, is de maximale grootte van het bronbestand dat u kunt gebruiken:

      * 400 MB voor 4.000 transcodering.
      * 800 MB voor 1080p-transcodering.
      * 8 GB voor 720p-transcodering.

   * De maximale bestandsgrootte die u kunt transcoderen naar een resolutie van 4 k is 2,55 GB MP4-bestand met een resolutie van 4 k, een bitsnelheid van 12 Mbps en 23 fps.

  **Zie ook**

* [Elementen vertalen](translate-assets.md)
* [Elementen HTTP-API](mac-api-assets.md)
* [Ondersteunde bestandsindelingen](file-format-support.md)
* [Zoeken in middelen](search-assets.md)
* [Verbonden elementen](use-assets-across-connected-assets-instances.md)
* [Elementen rapporteren](asset-reports.md)
* [Metagegevensschema&#39;s](metadata-schemas.md)
* [Elementen downloaden](download-assets-from-aem.md)
* [Metagegevens beheren](manage-metadata.md)
* [Zoeken in facetten](search-facets.md)
* [Verzamelingen beheren](manage-collections.md)
* [Bulkmetagegevens importeren](metadata-import-export.md)
* [Middelen publiceren naar AEM en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

>[!MORELIKETHIS]
>
>* [Dynamic Media-videodocumentatie](/help/assets/dynamic-media/video.md).
>* [Meer informatie over gebruik, typen en configuratie van verwerkingsprofielen](/help/assets/asset-microservices-configure-and-use.md).
