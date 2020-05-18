---
title: Assets van AEM downloaden
description: Leer hoe u elementen downloadt van AEM en de downloadfunctionaliteit in- of uitschakelt.
contentOwner: AG
translation-type: tm+mt
source-git-commit: c978be66702b7f032f78a1509f2a11315d1ed89f
workflow-type: tm+mt
source-wordcount: '653'
ht-degree: 1%

---


# Assets van AEM downloaden {#download-assets-from-aem}

U kunt elementen downloaden, zoals statische en dynamische uitvoeringen. Gedownloade elementen worden gebundeld in een ZIP-bestand. Het gecomprimeerde ZIP-bestand heeft een maximale bestandsgrootte van 1 GB voor de exporttaak. U kunt maximaal 500 elementen per exporttaak gebruiken.

>[!NOTE]
>
>Om de elementen te kunnen downloaden, moeten de leden machtigingen hebben om workflows te starten die het downloaden van elementen activeren.

Als u elementen wilt downloaden, navigeert u naar een element, selecteert u het element en tikt u op het **[!UICONTROL Download]** pictogram op de werkbalk of klikt u erop. Geef in het dialoogvenster dat verschijnt de gewenste downloadopties op.

De elementtypen Afbeeldingssets, Spin-sets, Gemengde mediasets en Carousel-sets kunnen niet worden gedownload.

![Beschikbare opties voor het downloaden van elementen van AEM-elementen](assets/asset_download_dialog.png)

*Afbeelding: Beschikbare opties voor het downloaden van elementen van AEM Assets.*

Hieronder vindt u de opties Exporteren/downloaden. Dynamische uitvoeringen zijn uniek voor Dynamische media en u kunt uitvoeringen ter plekke genereren naast het element dat u hebt geselecteerd. Deze optie is alleen beschikbaar als u Dynamische media hebt ingeschakeld.

| Opties voor exporteren of downloaden | Beschrijvingen |
|---|---|
| [!UICONTROL Assets] | Selecteer deze optie om het element in de oorspronkelijke vorm te downloaden zonder dat er uitvoeringen plaatsvinden. |
| [!UICONTROL Renditions] | Een vertoning is de binaire representatie van een element. Elementen hebben een primaire representatie, namelijk die van het geüploade bestand. Zij kunnen om het even welk aantal vertegenwoordiging hebben. <br> Met deze optie kunt u de uitvoeringen selecteren die u wilt downloaden. Welke uitvoeringen beschikbaar zijn, is afhankelijk van het element dat u selecteert. |
| [!UICONTROL Dynamic Renditions] | Een dynamische vertoning genereert andere uitvoeringen ter plekke. Wanneer u deze optie selecteert, selecteert u ook de uitvoeringen die u dynamisch wilt maken door een optie te selecteren in de lijst met voorinstellingen voor afbeeldingen. Bovendien kunt u de grootte en de maateenheid, de indeling, de kleurruimte, de resolutie en alle wijzigingstoetsen voor afbeeldingen selecteren (bijvoorbeeld om de afbeelding om te keren) |
| [!UICONTROL Create separate folder for each asset] | Selecteer deze optie om de mappenhiërarchie te behouden tijdens het downloaden van elementen. Standaard wordt de maphiërarchie genegeerd en worden alle elementen in één map op uw lokale systeem gedownload. |

De optie Uitvoeringen van optie is beschikbaar als het element uitvoeringen heeft. De optie Subassets is beschikbaar als het element subassets bevat.

Wanneer u een map selecteert om te downloaden, wordt de volledige elementenhiërarchie onder de map gedownload. Selecteer **[!UICONTROL Create separate folder for each asset]**.

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

De functie `Asset Download Servlet` kan worden uitgeschakeld op een AEM-publicatie-instantie door de configuratie van de verzender bij te werken om aanvragen voor het downloaden van middelen te blokkeren. servlet kan ook manueel via de console OSGi direct worden onbruikbaar gemaakt.

1. Om activa te blokkeren downloadverzoeken via een verzenderconfiguratie geef de `dispatcher.any` configuratie uit en voeg een nieuwe regel aan de [filtersectie](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#defining-a-filter)toe.

   `/0100 { /type "deny" /url "*.assetdownload.zip/assets.zip*" }`

>[!MORELIKETHIS]
>
>* [Met DRM beveiligde middelen downloaden](drm.md)
>* [Elementen downloaden met de AEM-bureaubladtoepassing op Windows- of Mac-bureaublad](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html)
>* [Elementen downloaden met Adobe Assets Link vanuit de ondersteunde Adobe Creative Cloud-toepassingen](https://helpx.adobe.com/nl/enterprise/using/manage-assets-using-adobe-asset-link.html)

