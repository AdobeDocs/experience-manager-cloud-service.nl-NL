---
title: Elementen downloaden
description: De activa van de download van  [!DNL Adobe Experience Manager Assets]  en laten of onbruikbaar maken de downloadfunctionaliteit toe.
contentOwner: Vishabh Gupta
feature: Asset Management
role: User
exl-id: f68b03ba-4ca1-4092-b257-16727fb12e13
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '1325'
ht-degree: 0%

---

# Elementen downloaden van [!DNL Adobe Experience Manager] {#download-assets-from-aem}

| [ Beste praktijken van het Onderzoek ](/help/assets/search-best-practices.md) | [ Beste praktijken van Meta-gegevens ](/help/assets/metadata-best-practices.md) | [ Content Hub ](/help/assets/product-overview.md) | [ Dynamic Media met mogelijkheden OpenAPI ](/help/assets/dynamic-media-open-apis-overview.md) | [ de ontwikkelaarsdocumentatie van AEM Assets ](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/download-assets-from-aem.html?lang=en) |
| AEM as a Cloud Service | Dit artikel |

U kunt elementen downloaden, zoals statische en dynamische uitvoeringen. U kunt ook e-mails met koppelingen naar elementen rechtstreeks vanuit [!DNL Adobe Experience Manager Assets] verzenden. Gedownloade elementen worden opgenomen in een ZIP-bestand. <!-- The compressed ZIP file has a maximum file size of 1 GB for the export job. A maximum of 500 total assets per export job are allowed. -->

<!--
>[!NOTE]
>
>Recipients of emails must be members of the `dam-users` group to access the ZIP download link in the email message. To be able to download the assets, the members must have permissions to launch workflows that trigger downloading of assets.
-->

De volgende elementtypen kunnen niet worden gedownload: Afbeeldingssets, Spin-sets, Gemengde mediasets en Carousel-sets.

U kunt elementen van Experience Manager downloaden met de volgende methoden:

<!-- * [Link Share](#link-share-download) -->

* [Gebruikersinterface Experience Manager](#download-assets)
* [ Commons van het Aandeel van Activa ](https://adobe-marketing-cloud.github.io/asset-share-commons/)
* [ Brand Portal ](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/brand-portal.html)
* [ Desktop app ](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#download-assets)

## Elementen downloaden via de interface [!DNL Experience Manager] {#download-assets}

Experience Manager optimaliseert de downloadervaring op basis van de hoeveelheid en de grootte van het element. Kleinere bestanden worden in real-time gedownload vanuit de gebruikersinterface. [!DNL Experience Manager] downloadt direct enkele elementaanvragen voor het oorspronkelijke bestand in plaats van afzonderlijke elementen in een ZIP-archief te omsluiten, zodat sneller kan worden gedownload. Experience Manager ondersteunt grote downloads met asynchrone verzoeken. Downloadaanvragen die groter zijn dan 100 GB worden gesplitst in meerdere ZIP-archieven met een maximale grootte van 100 MB elk.

Door gebrek, [!DNL Experience Manager] brengt een bericht in [[!DNL Experience Manager]  in werking Inbox ](/help/sites-cloud/authoring/inbox.md) op generatie van een downloadarchief.

![ Inbox bericht ](assets/inbox-notification-for-large-downloads.png)


### E-mailmeldingen inschakelen voor grote downloads {#enable-emails-for-large-downloads}

Asynchrone downloads worden in een van de volgende gevallen geactiveerd:

* Indien er meer dan tien activa zijn
* Als de downloadgrootte groter is dan 100 MB
* Als het downloaden meer dan 30 seconden duurt om voor te bereiden

Terwijl de asynchrone download achteraan loopt, kan de gebruiker blijven onderzoeken en verder in Experience Manager werken. Naast de meldingen in het Postvak IN van de Experience Manager kan Experience Manager e-mails verzenden om de gebruiker op de hoogte te stellen wanneer het downloadproces is voltooid. Om deze eigenschap toe te laten, kunnen de beheerders e-maildienst vormen door [ een SMTP serververbinding ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines.html#sending-email) te vormen.

Nadat de e-mailservice is geconfigureerd, kunnen beheerders en gebruikers e-mailmeldingen inschakelen via de interface Experience Manager.

E-mailmeldingen inschakelen:

1. Meld u aan bij [!DNL Experience Manager Assets] .
1. Klik op het gebruikerspictogram in de rechterbovenhoek en klik vervolgens op **[!UICONTROL My Preferences]** om het venster Gebruikersvoorkeuren te openen.
1. Selecteer het selectievakje **[!UICONTROL Asset Download email notifications]** en klik op **[!UICONTROL Accept]** .

   ![ toelaten-e-mail-berichten-voor-grote-downloads ](/help/assets/assets/enable-email-for-large-downloads.png)


Voer de volgende stappen uit om elementen te downloaden:

1. Klik in de gebruikersinterface van [!DNL Experience Manager] op **[!UICONTROL Assets]** > **[!UICONTROL Files]** .
1. Navigeer naar de elementen die u wilt downloaden. Selecteer de map of selecteer een of meer middelen in de map. Klik op **[!UICONTROL Download]** op de werkbalk.

   ![ Beschikbare opties bij het downloaden van elementen van [!DNL Experience Manager Assets]](/help/assets/assets/asset-download1.png)

1. Selecteer in het dialoogvenster Downloaden de gewenste downloadopties.

   | Downloadoptie | Beschrijving |
   |---|---|
   | **[!UICONTROL Create separate folder for each asset]** | Selecteer deze optie om een map te maken voor elk element dat alle gedownloade uitvoeringen voor het element bevat. Als deze optie niet is geselecteerd, bevindt elk element (en de bijbehorende uitvoeringen als deze zijn geselecteerd om te worden gedownload) zich in de bovenliggende map van het gegenereerde archief. |
   | **[!UICONTROL Email]** | Selecteer deze optie om een e-mailbericht (met een koppeling naar uw download) naar een andere gebruiker te verzenden. De ontvangende gebruiker moet lid van de `dam-users` groep zijn. De standaard e-mailsjablonen zijn beschikbaar op de volgende locaties:<ul><li>`/libs/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/libs/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul> De malplaatjes die u tijdens plaatsing aanpast zijn beschikbaar bij de volgende plaatsen: <ul><li>`/apps/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/apps/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul>U kunt huurdersspecifieke douanemalplaatjes bij de volgende plaatsen opslaan:<ul><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul> |
   | **[!UICONTROL Asset(s)]** | Selecteer deze optie als u het element in de oorspronkelijke vorm wilt downloaden.<br> de subassets optie is beschikbaar als het originele element subassets heeft. |
   | **[!UICONTROL Rendition(s)]** | Een vertoning is de binaire representatie van een element. Assets heeft een primaire representatie: die van het geüploade bestand. Zij kunnen om het even welk aantal vertegenwoordiging hebben. <br> Met deze optie kunt u de uitvoeringen selecteren die u wilt downloaden. Welke uitvoeringen beschikbaar zijn, is afhankelijk van het geselecteerde element. |
   | **[!UICONTROL Smart Crops]** | Selecteer deze optie als u alle slimme uitsnijduitvoeringen van het geselecteerde element wilt downloaden vanuit [!DNL Experience Manager] . Er wordt een ZIP-bestand met de Smart Crop-uitvoeringen gemaakt en gedownload naar uw lokale computer. |
   | **[!UICONTROL Dynamic Rendition(s)]** | Selecteer deze optie als u een reeks alternatieve vertoningen in real-time wilt genereren. Wanneer u deze optie selecteert, selecteert u ook de vertoningen die u dynamisch wilt tot stand brengen door uit de [ Vooraf ingestelde Beeld ](/help/assets/dynamic-media/image-presets.md) lijst te selecteren. <br> bovendien, kunt u de grootte en de eenheid van meting, formaat, kleurenruimte, resolutie, en om het even welke facultatieve beeldbepalingen selecteren zoals het omkeren van het beeld. De optie is alleen beschikbaar als u [!DNL Dynamic Media] hebt ingeschakeld. |

1. Klik in het dialoogvenster op **[!UICONTROL Download]** .

   Als e-mailmelding is ingeschakeld voor grote downloads, wordt een e-mail met een download-URL van de gearchiveerde ZIP-map in uw Postvak IN weergegeven. Klik op de downloadkoppeling in de e-mail om het ZIP-archief te downloaden.

   ![ e-mail-notifications-voor-grote-downloads ](/help/assets/assets/email-for-large-notification.png)

   U kunt de melding ook weergeven in het Postvak IN [!DNL Experience Manager] .

   ![ inbox-notifications-voor-grote-downloads ](/help/assets/assets/inbox-notification-for-large-downloads.png)

## Elementen downloaden die via koppelingen delen worden gedeeld {#link-share-download}

Het delen van elementen via een koppeling is een handige manier om deze beschikbaar te maken voor belangstellenden zonder dat zij zich hoeven aan te melden bij [!DNL Assets] . Zie [ functionaliteit van het Aandeel van de Verbinding ](/help/assets/share-assets.md#sharelink).

Wanneer gebruikers elementen downloaden van gedeelde koppelingen, gebruikt [!DNL Assets] een asynchrone service die snellere en ononderbroken downloads biedt. De te downloaden middelen worden op de achtergrond in een Postvak IN in een ZIP-archief met beheerbare bestandsgrootte in een wachtrij geplaatst. Voor grotere downloads wordt de download uitgeknipt in bestanden van 100 GB.

In [!UICONTROL Download Inbox] wordt de verwerkingsstatus van elk archief weergegeven. Zodra de verwerking is voltooid, kunt u de archieven downloaden van inbox.

![ Inbox van de Download ](assets/link-sharing-download-inbox.png)

## Enable asset download servlet {#enable-asset-download-servlet}

Met de standaardservlet in [!DNL Experience Manager] kunnen geverifieerde gebruikers willekeurig grote, gelijktijdige downloadaanvragen afgeven om ZIP-bestanden met elementen te maken. De downloadvoorbereiding kan prestatiesimplicaties hebben of kan zelfs de server en het netwerk overbelasten. Om dergelijke potentiële DoS-achtige risico&#39;s te verlichten die door deze eigenschap worden veroorzaakt, `AssetDownloadServlet` de component OSGi is gehandicapt voor publicatie instanties. Schakel het servlet-bestand bij de auteur uit als u de downloadfunctie niet nodig hebt voor instanties van de auteur.

Om het downloaden van activa van uw DAM toe te staan, bijvoorbeeld wanneer het gebruiken van iets zoals de Commons van het Aandeel van Activa of andere portaalachtige implementatie, laat manueel servlet via een configuratie OSGi toe. Adobe raadt u aan de toegestane downloadgrootte zo laag mogelijk in te stellen zonder dat dit van invloed is op de dagelijkse downloadvereisten. Een hoge waarde kan de prestaties beïnvloeden.

1. Maak een map met een naamgevingsconventie die zich richt op de publicatieroutmodus, namelijk `config.publish` :

   `/apps/<your-app-name>/config.publish`

1. Maak in de configuratiemap een bestand van het type `nt:file` genaamd `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config` .
1. Vul `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config` met de volgende code. Hiermee stelt u een maximale grootte (in bytes) voor het downloaden in als de waarde `asset.download.prezip.maxcontentsize` . In het onderstaande voorbeeld wordt de maximale grootte van de ZIP-download ingesteld op maximaal 100 kB.

   ```java
   enabled=B"true"
   asset.download.prezip.maxcontentsize=I"102400"
   ```

## Asset Download-server uitschakelen {#disable-asset-download-servlet}

Als u de downloadfunctionaliteit niet nodig hebt, dan onbruikbaar servlet om het even welke DoS-gelijkaardige risico&#39;s te verhinderen. `Asset Download Servlet` kan op een [!DNL Experience Manager] auteur en publiceer instanties worden onbruikbaar gemaakt door de configuratie van de verzender bij te werken om het even welke verzoeken van de activadownload te blokkeren. servlet kan ook manueel via de console OSGi direct worden onbruikbaar gemaakt.

1. Om activa te blokkeren downloadverzoeken via een verdienersconfiguratie geeft de `dispatcher.any` configuratie uit en voegt een nieuwe regel aan de [ filtersectie ](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#configuring) toe.

   `/0100 { /type "deny" /url "*.assetdownload.zip/assets.zip*" }`

## OnTime- of OffTime-uitvoering {#on-off-time-rendition}

Om de `OnOffTimeAssetAccessFilter` dienst toe te laten, moet u een configuratie tot stand brengen OSGi. Met deze service kunt u naast het element zelf ook toegang tot vertoningen en metagegevens blokkeren op basis van de instellingen voor aan- en uittijd. De OSGi-configuratie moet voor `com.day.cq.dam.core.impl.servlet.OnOffTimeAssetAccessFilter` zijn. Voer de onderstaande stappen uit:

1. In uw projectcode in Git, creeer een configuratiedossier bij `/apps/system/config/com.day.cq.dam.core.impl.servlet.OnOffTimeAssetAccessFilter.cfg.json`. Het bestand moet `{}` bevatten als inhoud, wat een lege OSGi-configuratie voor de corresponderende OSGi-component betekent. Deze actie laat de dienst toe.
1. Implementeer uw code, inclusief deze nieuwe configuratie, via [!DNL Cloud Manager] .
1. Nadat de uitvoeringen en metagegevens zijn geïmplementeerd, zijn deze toegankelijk volgens de instellingen voor aan- en uittijd van de elementen. Als de huidige datum of tijd vóór de on-time of na de off-time valt, wordt een foutenmelding getoond.
Voor meer details bij het toevoegen van een lege configuratie OSGi, zie deze [ gids ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/configuring-osgi.html?lang=en).

## Tips en beperkingen {#tips-limitations}

* Als u een lege map downloadt, geeft [!DNL Experience Manager] een succesbericht weer over het maken van een ZIP-archief, maar wordt het archief niet gemaakt.

**zie ook**

* [Assets vertalen](translate-assets.md)
* [ASSETS HTTP API](mac-api-assets.md)
* [Door Assets ondersteunde bestandsindelingen](file-format-support.md)
* [Zoeken in middelen](search-assets.md)
* [Verbonden elementen](use-assets-across-connected-assets-instances.md)
* [Elementen rapporteren](asset-reports.md)
* [Metagegevensschema&#39;s](metadata-schemas.md)
* [Metagegevens beheren](manage-metadata.md)
* [Zoeken in facetten](search-facets.md)
* [Verzamelingen beheren](manage-collections.md)
* [Bulkmetagegevens importeren](metadata-import-export.md)
* [Publish Assets naar AEM en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

>[!MORELIKETHIS]
>
>* [ Download DRM beschermde activa ](drm.md)
>* [ de activa van de Download gebruikend Desktop app van de Experience Manager op de Desktop van Win of van Mac ](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html)
>* [ de activa van de Download gebruikend de Verbinding van Assets van de Adobe van binnen gesteunde Adobe Creative Cloud apps ](https://helpx.adobe.com/nl/enterprise/using/manage-assets-using-adobe-asset-link.html)
