---
title: Assets van AEM downloaden
description: Leer hoe u elementen downloadt van AEM en de downloadfunctionaliteit in- of uitschakelt.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 748255ef2b3bae9ecca900cdfe7d3be594fb2552
workflow-type: tm+mt
source-wordcount: '750'
ht-degree: 1%

---


# Download assets from [!DNL Adobe Experience Manager] {#download-assets-from-aem}

U kunt elementen downloaden, zoals statische en dynamische uitvoeringen. U kunt ook e-mails met koppelingen naar middelen rechtstreeks verzenden vanuit [!DNL Adobe Experience Manager Assets]. Gedownloade elementen worden gebundeld in een ZIP-bestand. Het gecomprimeerde ZIP-bestand heeft een maximale bestandsgrootte van 1 GB voor de exporttaak. Er zijn maximaal 500 totale elementen per exporttaak toegestaan.

>[!NOTE]
>
>Ontvangers van e-mailberichten moeten lid zijn van de `dam-users` groep om toegang te krijgen tot de koppeling voor het downloaden van postadressen in het e-mailbericht. Om de elementen te kunnen downloaden, moeten de leden machtigingen hebben om workflows te starten die het downloaden van elementen activeren.

De elementtypen Afbeeldingssets, Spin-sets, Gemengde mediasets en Carousel-sets kunnen niet worden gedownload.

**Als u elementen wilt downloaden,**

1. In the upper-left corner of AEM, tap the AEM logo, then in the left rail, tap **[!UICONTROL Navigation]** (Compass icon).
1. Tik op de navigatiepagina **[!UICONTROL Assets > Files]**.
1. Navigeer naar een map die elementen bevat die u wilt downloaden.
1. Selecteer de map of selecteer een of meer middelen in de map.
1. Tik op de werkbalk **[!UICONTROL Download]**.

   ![Beschikbare opties voor het downloaden van middelen van Experience Manager Assets](/help/assets/assets/asset-download.png)

   *Opties in het dialoogvenster Downloaden.*

1. Selecteer in het dialoogvenster Downloaden de gewenste downloadopties.

   | Downloadoptie | Beschrijving |
   |---|---|
   | **[!UICONTROL Create separate folder for each asset]** | Selecteer deze optie om elk element dat u downloadt, inclusief elementen, op te nemen in onderliggende mappen die onder de bovenliggende map van het element zijn genest in één map op uw lokale computer. Als deze optie *niet* standaard is geselecteerd, wordt de maphiërarchie genegeerd en worden alle elementen naar één map op uw lokale computer gedownload. |
   | **[!UICONTROL Email]** | Selecteer deze optie als u een e-mailbericht wilt verzenden naar de ontvanger. De standaard e-mailsjablonen zijn beschikbaar op de volgende locaties:<ul><li>`/libs/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/libs/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul> De malplaatjes die u tijdens plaatsing aanpast zijn beschikbaar bij de volgende plaatsen: <ul><li>`/apps/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/apps/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul>U kunt huurdersspecifieke douanemalplaatjes bij de volgende plaatsen opslaan:<ul><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul> |
   | **[!UICONTROL Asset(s)]** | Selecteer deze optie als u het element in de oorspronkelijke vorm zonder vertoningen wilt downloaden.<br>De optie Subassets is beschikbaar als het oorspronkelijke element subassets heeft. |
   | **[!UICONTROL Rendition(s)]** | Een vertoning is de binaire representatie van een element. Elementen hebben een primaire representatie, namelijk die van het geüploade bestand. Zij kunnen om het even welk aantal vertegenwoordiging hebben. <br> Met deze optie kunt u de uitvoeringen selecteren die u wilt downloaden. Welke uitvoeringen beschikbaar zijn, is afhankelijk van het element dat u hebt geselecteerd. |
   | **[!UICONTROL Smart Crops]** | Selecteer deze optie als u alle slimme uitsnijduitvoeringen van het geselecteerde element wilt downloaden vanuit AEM. Er wordt een ZIP-bestand met de Smart Crop-uitvoeringen gemaakt en gedownload naar uw lokale computer. |
   | **[!UICONTROL Dynamic Rendition(s)]** | Selecteer deze optie als u een reeks alternatieve vertoningen in real-time wilt genereren. Wanneer u deze optie selecteert, selecteert u ook de uitvoeringen die u dynamisch wilt maken door een optie te selecteren in de lijst [Voorinstelling](/help/assets/dynamic-media/image-presets.md) afbeelding. <br>Bovendien kunt u de grootte en maateenheid, de indeling, de kleurruimte, de resolutie en eventuele optionele afbeeldingsaanpassingen selecteren, zoals het omkeren van de afbeelding. De optie is alleen beschikbaar als u deze hebt [!DNL Dynamic Media] ingeschakeld. |

1. In the dialog box, tap **[!UICONTROL Download]**.


## Enable asset download servlet {#enable-asset-download-servlet}

Met de standaardservlet in AEM kunnen geverifieerde gebruikers willekeurig grote, gelijktijdige downloadaanvragen afgeven voor het maken van ZIP-bestanden met elementen die zichtbaar zijn voor hen en die de server en het netwerk kunnen overbelasten. Om potentiële risico&#39;s van Dos te verlichten die door deze eigenschap worden veroorzaakt, wordt de component `AssetDownloadServlet` OSGi onbruikbaar gemaakt door gebrek voor publiceer instanties.

Om het downloaden van activa van uw DAM toe te staan, bijvoorbeeld wanneer het gebruiken van iets zoals de Commons van het Aandeel van Activa of andere portaalachtige implementatie, laat manueel servlet via een configuratie OSGi toe. Adobe raadt u aan de toegestane downloadgrootte zo laag mogelijk in te stellen zonder dat dit van invloed is op de vereisten voor het dagelijks downloaden. Een hoge waarde kan van invloed zijn op de prestaties.

1. Maak een map met een naamgevingsconventie die zich richt op de publicatie-runtime, namelijk `config.publish`:

   `/apps/<your-app-name>/config.publish`

1. Maak in de configuratiemap een nieuw bestand van het type `nt:file` genaamd `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config`.
1. Vul `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config` met de volgende code. Hiermee stelt u een maximale grootte (in bytes) in voor het downloaden als waarde van `asset.download.prezip.maxcontentsize`. In het onderstaande voorbeeld wordt de maximale grootte van de ZIP-download ingesteld op maximaal 100 kB.

   ```java
   enabled=B"true"
   asset.download.prezip.maxcontentsize=I"102400"
   ```

## Asset Download-server uitschakelen {#disable-asset-download-servlet}

De functie `Asset Download Servlet` kan op een AEM Publish-instantie worden uitgeschakeld door de configuratie van de verzender bij te werken om aanvragen voor het downloaden van middelen te blokkeren. servlet kan ook manueel via de console OSGi direct worden onbruikbaar gemaakt.

1. Om activa te blokkeren downloadverzoeken via een verzenderconfiguratie geef de `dispatcher.any` configuratie uit en voeg een nieuwe regel aan de [filtersectie](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#defining-a-filter)toe.

   `/0100 { /type "deny" /url "*.assetdownload.zip/assets.zip*" }`

>[!MORELIKETHIS]
>
>* [Met DRM beveiligde middelen downloaden](drm.md)
>* [Elementen downloaden met de AEM-bureaubladtoepassing op Windows- of Mac-bureaublad](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html)
>* [Elementen downloaden met Adobe Assets Link vanuit de ondersteunde Adobe Creative Cloud-toepassingen](https://helpx.adobe.com/nl/enterprise/using/manage-assets-using-adobe-asset-link.html)

