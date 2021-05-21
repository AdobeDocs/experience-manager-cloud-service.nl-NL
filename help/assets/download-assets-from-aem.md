---
title: Elementen downloaden
description: Download elementen van [!DNL Adobe Experience Manager Assets] en schakel de downloadfunctionaliteit in of uit.
contentOwner: AG
feature: Beheer van bedrijfsmiddelen
role: Business Practitioner
exl-id: f68b03ba-4ca1-4092-b257-16727fb12e13
source-git-commit: 715e6e56294172989aa8e512b5cbc6679312e379
workflow-type: tm+mt
source-wordcount: '896'
ht-degree: 1%

---

# Elementen downloaden van [!DNL Adobe Experience Manager] {#download-assets-from-aem}

U kunt elementen downloaden, zoals statische en dynamische uitvoeringen. U kunt ook e-mails met koppelingen naar elementen rechtstreeks vanuit [!DNL Adobe Experience Manager Assets] verzenden. Gedownloade elementen worden gebundeld in een ZIP-bestand. Het gecomprimeerde ZIP-bestand heeft een maximale bestandsgrootte van 1 GB voor de exporttaak. Er zijn maximaal 500 totale elementen per exporttaak toegestaan.

>[!NOTE]
>
>Ontvangers van e-mailberichten moeten lid zijn van de groep `dam-users` om toegang te krijgen tot de ZIP-downloadkoppeling in het e-mailbericht. Om de elementen te kunnen downloaden, moeten de leden machtigingen hebben om workflows te starten die het downloaden van elementen activeren.

De elementtypen Afbeeldingssets, Spin-sets, Gemengde mediasets en Carousel-sets kunnen niet worden gedownload.

U kunt Experience Manager-elementen downloaden met de volgende methoden:

* [Gebruikersinterface Experience Manager](#download-in-aem)
* [Commentaar voor het delen van bedrijfsmiddelen](https://adobe-marketing-cloud.github.io/asset-share-commons/)
* [Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/brand-portal.html)
* [Desktop-app](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#download-assets)

## Elementen downloaden via [!DNL Experience Manager]-interface {#download-in-aem}

De asynchrone downloaddienst verstrekt een kader voor naadloze download van grote activa. Kleinere bestanden worden in realtime gedownload vanuit de gebruikersinterface. De grote bestanden worden asynchroon gedownload en gebruikers worden via meldingen via Experience Managers in het Postvak IN op de hoogte gebracht van het invullen. Zie [Inbox van Experience Manager begrijpen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/getting-started/inbox.html).

![Melding downloaden](assets/download-notification.png)

*Afbeelding: Melding downloaden via  [!DNL Experience Manager] Postvak IN.*

Asynchrone downloads worden in een van de volgende gevallen geactiveerd:

* Als er meer dan 10 elementen of meer dan 100 MB zijn om te downloaden.
* Als het downloaden meer dan 30 seconden duurt om voor te bereiden.

Voer de volgende stappen uit om elementen te downloaden:

1. Klik in [!DNL Experience Manager] gebruikersinterface op **[!UICONTROL Assets]** > **[!UICONTROL Files]**.
1. Navigeer naar de elementen die u wilt downloaden. Selecteer de map of selecteer een of meer middelen in de map. Klik op **[!UICONTROL Download]** op de werkbalk.

   ![Beschikbare opties voor het downloaden van elementen van  [!DNL Experience Manager Assets]](/help/assets/assets/asset-download1.png)

   *Afbeelding: Opties in het dialoogvenster Downloaden.*

1. Selecteer in het dialoogvenster Downloaden de gewenste downloadopties.

   | Downloadoptie | Beschrijving |
   |---|---|
   | **[!UICONTROL Create separate folder for each asset]** | Selecteer deze optie om elk element dat u downloadt, inclusief elementen, op te nemen in onderliggende mappen die onder de bovenliggende map van het element zijn genest in één map op uw lokale computer. Wanneer deze optie *niet* selecteert, door gebrek, wordt de omslaghiërarchie genegeerd en alle activa worden gedownload in één omslag in uw lokale computer. |
   | **[!UICONTROL Email]** | Selecteer deze optie als u een e-mailbericht wilt verzenden naar de ontvanger. De standaard e-mailsjablonen zijn beschikbaar op de volgende locaties:<ul><li>`/libs/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/libs/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul> De malplaatjes die u tijdens plaatsing aanpast zijn beschikbaar bij de volgende plaatsen: <ul><li>`/apps/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/apps/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul>U kunt huurdersspecifieke douanemalplaatjes bij de volgende plaatsen opslaan:<ul><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul> |
   | **[!UICONTROL Asset(s)]** | Selecteer deze optie als u het element in de oorspronkelijke vorm zonder vertoningen wilt downloaden.<br>De optie Subassets is beschikbaar als het oorspronkelijke element subassets heeft. |
   | **[!UICONTROL Rendition(s)]** | Een vertoning is de binaire representatie van een element. Elementen hebben een primaire representatie, namelijk die van het geüploade bestand. Zij kunnen om het even welk aantal vertegenwoordiging hebben. <br> Met deze optie kunt u de uitvoeringen selecteren die u wilt downloaden. Welke uitvoeringen beschikbaar zijn, is afhankelijk van het element dat u hebt geselecteerd. |
   | **[!UICONTROL Smart Crops]** | Selecteer deze optie als u alle slimme uitsnijduitvoeringen van het geselecteerde element wilt downloaden vanuit [!DNL Experience Manager]. Er wordt een ZIP-bestand met de Smart Crop-uitvoeringen gemaakt en gedownload naar uw lokale computer. |
   | **[!UICONTROL Dynamic Rendition(s)]** | Selecteer deze optie als u een reeks alternatieve vertoningen in real-time wilt genereren. Wanneer u deze optie selecteert, selecteert u ook de uitvoeringen die u dynamisch wilt maken door een optie te selecteren in de lijst [Voorinstelling afbeelding](/help/assets/dynamic-media/image-presets.md). <br>Bovendien kunt u de grootte en maateenheid, de indeling, de kleurruimte, de resolutie en eventuele optionele afbeeldingsaanpassingen selecteren, zoals het omkeren van de afbeelding. De optie is alleen beschikbaar als u [!DNL Dynamic Media] hebt ingeschakeld. |

1. Klik in het dialoogvenster op **[!UICONTROL Download]**.

## Enable asset download servlet {#enable-asset-download-servlet}

Met de standaardservlet in [!DNL Experience Manager] kunnen geverifieerde gebruikers willekeurig grote, gelijktijdige downloadverzoeken afgeven om ZIP-bestanden met elementen te maken. De downloadvoorbereiding kan prestatiesimplicaties hebben of kan zelfs de server en het netwerk overbelasten. Om dergelijke potentiële DoS-achtige risico&#39;s te verlichten die door deze eigenschap worden veroorzaakt, `AssetDownloadServlet` OSGi component is gehandicapt voor publicatieinstanties. Als u de downloadfunctie niet nodig hebt op auteur-instanties, schakelt u het servlet-programma uit bij de auteur.

Om het downloaden van activa van uw DAM toe te staan, bijvoorbeeld wanneer het gebruiken van iets zoals de Commons van het Aandeel van Activa of andere portaalachtige implementatie, laat manueel servlet via een configuratie OSGi toe. Adobe raadt u aan de toegestane downloadgrootte zo laag mogelijk in te stellen zonder dat dit van invloed is op de vereisten voor het dagelijks downloaden. Een hoge waarde kan van invloed zijn op de prestaties.

1. Maak een map met een naamgevingsconventie die zich richt op de publicatieruntime, dat wil zeggen `config.publish`:

   `/apps/<your-app-name>/config.publish`

1. Maak in de configuratiemap een nieuw bestand van het type `nt:file` met de naam `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config`.
1. Vul `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config` met het volgende. Hiermee stelt u een maximale grootte (in bytes) voor het downloaden in als waarde `asset.download.prezip.maxcontentsize`. In het onderstaande voorbeeld wordt de maximale grootte van de ZIP-download ingesteld op maximaal 100 kB.

   ```java
   enabled=B"true"
   asset.download.prezip.maxcontentsize=I"102400"
   ```

## Subserver {#disable-asset-download-servlet} uitschakelen

Als u de downloadfunctionaliteit niet nodig hebt, dan onbruikbaar servlet om het even welke DoS-gelijkaardige risico&#39;s te verhinderen. `Asset Download Servlet` kan op [!DNL Experience Manager] auteur en publiceer instanties worden onbruikbaar gemaakt door de configuratie van de verzender bij te werken om om het even welke verzoeken van de activadownload te blokkeren. servlet kan ook manueel via de console OSGi direct worden onbruikbaar gemaakt.

1. Om activa te blokkeren downloadverzoeken via een verdienersconfiguratie geef de `dispatcher.any` configuratie uit en voeg een nieuwe regel aan [filtersectie](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#configuring) toe.

   `/0100 { /type "deny" /url "*.assetdownload.zip/assets.zip*" }`

>[!MORELIKETHIS]
>
>* [Met DRM beveiligde middelen downloaden](drm.md)
* [Items downloaden met de bureaubladtoepassing Experience Manager op Windows of Mac](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html)
* [Elementen downloaden met de Adobe Assets Link vanuit de ondersteunde Adobe Creative Cloud-apps](https://helpx.adobe.com/nl/enterprise/using/manage-assets-using-adobe-asset-link.html)

