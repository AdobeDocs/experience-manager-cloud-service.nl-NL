---
title: Werken met 3D-elementen in dynamische media
description: Leer hoe u met 3D-middelen werkt in Dynamic Media.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS and Experience Manager as a Cloud Service
topic-tags: introduction
content-type: reference
feature: 3D Assets
role: User
exl-id: 82084ba7-1302-4cbd-8626-d77b3aaa4ed1
source-git-commit: 36ab36ba7e14962eba3947865545b8a3f29f6bbc
workflow-type: tm+mt
source-wordcount: '2181'
ht-degree: 2%

---

# Werken met 3D-elementen in dynamische media {#working-with-three-d-assets-dm}

Met dynamische media kunt u 3D-elementen uploaden, beheren, weergeven en leveren als indrukwekkende ervaringen.

* Klik met één klik op het publiceren van 3D-elementen (met **[!UICONTROL Quick Publish]** op de werkbalk) om een URL te genereren.
* Geoptimaliseerde ondersteuning voor het weergeven van 3D-middelen met de voorinstelling voor interactieve maatviewer van hoge kwaliteit, aangedreven door Adobe Dimension.
* Met de 3D Media WCM-component kunt u eenvoudig 3D-elementen toevoegen aan uw [!DNL Adobe Experience Manager Sites] -pagina&#39;s.

Er is geen aanvullende installatie vereist voor het gebruik van 3D-elementen in dynamische media.

![ Schommel in 3d ](/help/assets/dynamic-media/assets/3d-dimensional-viewer-quickpublish-url-embed2a.png)

<!-- See also [Dynamic Media 3D Release Notes](/help/release-notes/aem3d-release-notes.md). -->

## 3D-indelingen die worden ondersteund in dynamische media {#supported-three-d-file-formats-in-dm}

Dynamische media ondersteunt de volgende 3D-bestandsindelingen.

Zie ook [ 3D formaten die in Experience Manager Assets ](/help/assets/file-format-support.md#support-3d-formats) worden gesteund

| 3D-bestandsextensie | Bestandsindeling | MIME-type | Notities |
|---|---|---|---|
| GLB | Binaire GL-transmissie | model/gltf-binair | Hiermee neemt u de materialen en structuren op als één enkel element. |
| OBJ | WaveFront 3D-objectbestand | application/x-tgif |  |
| STL | Stereolithografie | application/vnd.ms-pki.stl |  |
| USDZ | Universal Scene Description Zip-archief | model/vnd.usdz+zip | *Steun voor slechts opname; geen het bekijken of interactie is beschikbaar.* USDZ is een eigen 3D-indeling die door Safari of iOS kan worden weergegeven. |

De 3D Media WCM-component en de 3D-voorvertoning op de pagina Details van een element zijn niet compatibel met de nieuwste versie van Chrome (97.x). Als u met 3D-elementen wilt werken, gebruikt u Firefox of Safari of een eerdere versie van Chrome (96.x).

## Snel starten: 3D-elementen in dynamische media {#quick-start-three-d}

De volgende stapsgewijze beschrijving van de workflow is ontworpen om u te helpen snel aan de slag te gaan met 3D-middelen in Dynamic Media.

Voordat u met 3D-elementen werkt in Dynamic Media, moet u ervoor zorgen dat de beheerder van [!DNL Experience Manager] Dynamic Media Cloud Services al heeft ingeschakeld en geconfigureerd.

Zie [ Dynamische Diensten van de Wolk van Media vormen ](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services).

1. **upload 3D activa**

   * [Uw 3D-elementen uploaden voor gebruik in dynamische media](/help/assets/add-assets.md#upload-assets)
   * [Ondersteunde 3D-bestandsindelingen voor uploaden in dynamische media](#supported-three-d-file-formats-in-dm)

1. **beheert 3D activa**

   * 3D-middelen organiseren en doorzoeken

      * [Digitale elementen ordenen](/help/assets/organize-assets.md)
      * [3D-middelen zoeken](/help/assets/search-assets.md)

   * 3D-elementen weergeven

      * [3D-middelen weergeven en gebruiken](#viewing-three-d-assets)
      * [De voorinstelling voor de dimensionale viewer beheren](/help/assets/dynamic-media/managing-viewer-presets.md)

   * Werken met metagegevens van 3D-elementen

      * [Metagegevens voor digitale elementen beheren](/help/assets/manage-digital-assets.md#editing-properties)
      * [Metagegevensschema&#39;s](/help/assets/metadata-schemas.md)

1. **publiceer 3D activa**

   * [Statische dynamische media 3D-elementen publiceren](#publishing-three-d-assets)
   * [Alternatieve methoden voor het publiceren van Dynamic Media 3D-elementen met de Dimensional-viewer](#alternate-publish-methods)

## Informatie over het weergeven van en communiceren met 3D-elementen {#viewing-three-d-assets}

In deze sectie wordt beschreven hoe u 3D-elementen op twee verschillende manieren kunt weergeven en gebruiken: van binnen de pagina met elementdetails en van binnen de component 3D-media in Sites.

De interactieve 3D-viewer bevat onder andere een verzameling interactieve besturingselementen voor camera waarmee u het 3D-element kunt draaien, zoomen en pannen.

De tijd die nodig is om een 3D-element te openen in de weergave Asset Details is afhankelijk van verschillende factoren. Deze factoren zijn onder andere:

* Bandbreedte voor de server.
* Koppelingen naar de server
* Complexiteit van de afbeelding.

Bovendien zijn de mogelijkheden van de clientcomputer, zoals een werkstation, laptop of mobiel aanraakapparaat, ook belangrijk om te overwegen wanneer u de camera interactief manipuleert. Een redelijk krachtig systeem met goede grafische mogelijkheden kan de interactieve 3D-kijkervaring vloeiender en gunstiger maken.

>[!TIP]
>
>U kunt de voorinstelling voor de maatviewer openen in de Viewer Preset Editor om te navigeren door een 3D-element zonder dat u eerst 3D-bestanden hoeft te uploaden. De voorinstelling van de DIMM-viewer heeft een ingebouwd 3D-element waarmee u kunt communiceren.
>
>Zie [ vooraf instelt van de kijker beheren ](/help/assets/dynamic-media/managing-viewer-presets.md).

## Een 3D-element weergeven en interactief werken via de pagina met elementdetails {#viewing-three-d-assets-from-asset-details-page}

Zie ook [ activa van de Voorproef gebruikend de softwareinterface ](/help/assets/dynamic-media/previewing-assets.md).

**om met een 3D activa van de pagina van elementdetails te bekijken en in wisselwerking te staan:**

1. Controleer of u 3D-elementen hebt geüpload naar [!DNL Experience Manager] .

   Zie [ uw 3D activa voor gebruik in Dynamische Media ](/help/assets/add-assets.md#upload-assets) uploaden.

1. Selecteer in [!DNL Experience Manager] op de **[!UICONTROL Navigation]** -pagina de optie **[!UICONTROL Assets > Files]** .
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL View]** rechtsboven op de pagina de optie **[!UICONTROL Card View]** .
1. Navigeer naar een 3D-element dat u wilt weergeven.
1. Als u het element wilt openen op de pagina Details, selecteert u de kaart van het 3D-element.
1. Voer op de pagina Details voor het 3D-element een van de volgende handelingen uit:

   | Weergave | Beschrijving | Muishandeling | Handeling op het aanraakscherm |
   | --- | --- | --- | --- |
   | **draai uw camera** | Draai de weergave rond de 3D-scène en -objecten. | Klik met de linkermuisknop en sleep. | Druk met één vinger en sleep. |
   | **Pannen uw camera** | U kunt de weergave naar links, rechts, omhoog of omlaag pannen. | Klik met de rechtermuisknop en sleep. | Druk met twee vingers en sleep. |
   | **Gezoem uw camera** | Ga in- en uit gebieden in de 3D-scène. | Schuifwiel. | Kneep met twee vingers. |
   | **herenter uw camera** | Voer de camera opnieuw in op een punt op een object in de 3D-scène. | Dubbelklik. | Dubbelselecteren. |
   | **Terugstellen** | Selecteer in de rechterbenedenhoek van de pagina het pictogram Herstellen om het doelpunt van de weergave te herstellen naar het midden van het 3D-element. Met Herstellen wordt de camera ook dichter bij of verder weg geplaatst om het middel volledig en bij een redelijke weergavegrootte weer te geven. |   |   |
   | **Volledige het schermwijze** | Als u de modus Volledig scherm wilt inschakelen, klikt u op het pictogram Volledig scherm rechtsonder op de pagina. |   |   |

1. Selecteer **[!UICONTROL Close]** in de rechterbovenhoek van de pagina om terug te keren naar de Assets-pagina.

## Een 3D-element in een 3D-mediacomponent weergeven en hiermee communiceren {#interacting-with-asset-inside-three-d-media-component}

Wanneer de modus **[!UICONTROL Edit]** van een webpagina is geactiveerd, is interactie met een 3D-element niet mogelijk. Als u het element interactief wilt maken, kunt u de functie **[!UICONTROL Preview]** gebruiken om de webpagina in de pagina-editor weer te geven met volledige toegang tot de functionaliteit van de 3D Media-component.

>[!IMPORTANT]
>
>U kunt deze taak pas uitvoeren nadat u een 3D-mediacomponent aan een webpagina hebt toegevoegd en een 3D-element aan de component hebt toegewezen. Zie [ de 3D component van Media aan een Web-pagina ](#adding-the-three-d-media-component-to-a-web-page) toevoegen en [ een 3D activa aan een 3D component van Media ](#assigning-a-three-d-asset-to-the-component) toewijzen.

Zie ook [ activa van de Voorproef gebruikend de softwareinterface ](/help/assets/dynamic-media/previewing-assets.md).

**om met een 3D activa binnen een 3D component van Media te bekijken en in wisselwerking te staan:**

1. Voer een van de volgende handelingen uit terwijl de modus **[!UICONTROL Edit]** voor een webpagina is geactiveerd:

   * Rechtsboven op de pagina klikt u op **[!UICONTROL Preview]** om de modus **[!UICONTROL Preview]** te activeren.
   * Verwijder `/editor.html` uit de pagina-URL in de browser.

   ![ 3D activa die binnen de 3D component van Media tonen ](/help/assets/dynamic-media/assets/3d-asset-in-3d-mediaa.png)
Een volledig interactief 3D-element zoals wordt weergegeven in de modus **[!UICONTROL Preview]** .

1. Voer in de modus **[!UICONTROL Preview]** een van de volgende handelingen uit:

   | Weergave | Beschrijving | Muishandeling | Handeling op het aanraakscherm |
   | --- | --- | --- | --- |
   | **draai uw camera** | Draai de weergave rond de 3D-scène en -objecten. | Klik met de linkermuisknop en sleep. | Druk met één vinger en sleep. |
   | **Pannen uw camera** | U kunt de weergave naar links, rechts, omhoog of omlaag pannen. | Klik met de rechtermuisknop en sleep. | Druk met twee vingers en sleep. |
   | **Gezoem uw camera** | Ga in- en uit gebieden in de 3D-scène. | Schuifwiel. | Kneep met twee vingers. |
   | **herenter uw camera** | Voer de camera opnieuw in op een punt op een object in de 3D-scène. | Dubbelklik. | Dubbelselecteren. |
   | **Terugstellen** | Selecteer in de rechterbenedenhoek van de pagina het pictogram Herstellen om het doelpunt van de weergave te herstellen naar het midden van het 3D-element. Met Herstellen wordt de camera ook dichter bij of verder weg geplaatst om het middel volledig en bij een redelijke weergavegrootte weer te geven. |   |   |
   | **Volledige het schermwijze** | Als u de modus Volledig scherm wilt inschakelen, klikt u op het pictogram Volledig scherm rechtsonder op de pagina. |   |   |

## Informatie over het werken met de 3D-mediacomponent {#working-with-three-d-media-component}

Dynamische media bevat een component Dynamic Media 3D Media die u in [!DNL Experience Manager Sites] kunt gebruiken om interactieve weergave van 3D-modellen op uw webpagina&#39;s in te schakelen.

* [De 3D-mediacomponent toevoegen aan de paginasjabloon](#adding-three-d-media-component-to-page-template)
* [De 3D-mediacomponent toevoegen aan een webpagina](#adding-the-three-d-media-component-to-a-web-page)
   * [Optioneel - De 3D-mediacomponent configureren](#configuring-the-three-d-component)
* [Een 3D-element toewijzen aan de 3D-mediacomponent](#assigning-a-three-d-asset-to-the-component)

## De 3D-mediacomponent toevoegen aan de paginasjabloon {#adding-three-d-media-component-to-page-template}

1. Navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL Templates]** .
1. Navigeer naar de paginasjabloon waarin u de 3D-component wilt inschakelen en selecteer de sjabloon.
1. Selecteer **[!UICONTROL Edit]** om de sjabloon te openen.
1. Selecteer in de rechterbovenhoek van de pagina de optie **[!UICONTROL Structure]** -modus in het keuzemenu als deze nog niet actief is.

   ![ 3d-media-component-structuur ](/help/assets/dynamic-media/assets/3d-media-component-structurea.png)

1. Als u een leeg gebied wilt selecteren en de bijbehorende werkbalk wilt openen, selecteert u het lege gebied in het **[!UICONTROL Layout Container]** -gebied.
1. Selecteer op de werkbalk het pictogram **[!UICONTROL Policy]** om het dialoogvenster **[!UICONTROL Policy Editor]** te openen.
1. Blader in de sectie **[!UICONTROL Properties]** onder de tab **[!UICONTROL Allowed Components]** naar **[!UICONTROL Dynamic Media]** , vouw de lijst uit en controleer **[!UICONTROL 3D Media]** .
1. Selecteer **[!UICONTROL Done]** om de wijzigingen op te slaan en **[!UICONTROL Policy Editor]** te sluiten.

   U kunt de component Dynamische media 3D Media nu op alle pagina&#39;s plaatsen die dit malplaatje gebruiken.

## De 3D-mediacomponent toevoegen aan een webpagina {#adding-the-three-d-media-component-to-a-web-page}

Als u [!DNL Experience Manager] gebruikt als het webcontentbeheersysteem, kunt u 3D-elementen aan uw webpagina&#39;s toevoegen met behulp van de 3D Media-component.

Zie ook [ Dynamische activa van Media aan pagina&#39;s ](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md) toevoegen.

1. Open [!DNL Experience Manager Sites] en selecteer de webpagina waaraan u de Dynamic Media 3D Media-component wilt toevoegen.
1. Als u de pagina in de pagina-editor wilt openen, selecteert u het pictogram **[!UICONTROL Edit]** (potlood). Zorg ervoor dat de modus **[!UICONTROL Edit]** rechtsboven op de pagina is geselecteerd.

   ![ 3d-media-component-voeg toe ](/help/assets/dynamic-media/assets/3d-media-component-edita.png)

1. Selecteer op de werkbalk het pictogram Zijpaneel om de weergave van het deelvenster in of uit te schakelen.

1. Selecteer in het zijpaneel het pictogram met het plusteken om de lijst van **[!UICONTROL Components]** te openen.

   ![ 3d-media-component-belemmering-daling ](/help/assets/dynamic-media/assets/3d-assets-filtera.png)

1. Sleep de component **[!UICONTROL 3D Media]** van de lijst **[!UICONTROL Components]** naar de locatie op de pagina waar u de 3D-viewer wilt weergeven.

U kunt nu een 3D-element aan de component toewijzen.

Zie [ activa 3D aan de 3D component van Media toewijzen ](#assigning-a-three-d-asset-to-the-component)

### Optioneel - De 3D-mediacomponent configureren {#configuring-the-three-d-component}

1. Selecteer in de pagina-editor van [!DNL Experience Manager Sites] de component **[!UICONTROL 3D Media Viewer]** die u eerder aan de pagina hebt toegevoegd.
1. Selecteer het pictogram **[!UICONTROL Configuration]** (moersleutel) om het dialoogvenster voor componentconfiguratie te openen.

   ![ 3d-media-component-config ](/help/assets/dynamic-media/assets/3d-media-component-configa.png)

1. Selecteer in het dialoogvenster 3D-media in de vervolgkeuzelijst Voorinstelling viewer de optie **[!UICONTROL Dimensional]** om de voorinstelling voor de maatviewer toe te wijzen aan de component.

   ![ 3d-media-component-geef-config uit ](/help/assets/dynamic-media/assets/3d-media-component-edit-configa.png)

1. Selecteer in de rechterbovenhoek het vinkje waarop u de wijzigingen wilt opslaan.

## Een 3D-element toewijzen aan de 3D-mediacomponent {#assigning-a-three-d-asset-to-the-component}

Nadat u een 3D-mediacomponent aan een webpagina hebt toegevoegd, kunt u er een 3D-element aan toewijzen.

Zie [ de 3D component van Media aan een Web-pagina ](#adding-the-three-d-media-component-to-a-web-page) toevoegen.

1. Klik in de pagina-editor van [!DNL Experience Manager Sites] op het pictogram **[!UICONTROL Assets]** dat u wilt openen **[!UICONTROL Assets]** in het zijpaneel.
1. Selecteer **[!UICONTROL 3D]** in de vervolgkeuzelijst om alleen 3D-elementbestandstypen weer te geven.
1. Zoek in het zijpaneel naar het 3D-element dat u wilt weergeven op de pagina die u bewerkt.
1. Sleep het 3D-element van het zijpaneel van Assets naar de component **[!UICONTROL 3D Media]** die u eerder aan de pagina hebt toegevoegd.

   ![ wijst 3d activa aan 3d component van Media ](/help/assets/dynamic-media/assets/3d-asset-adda.png) toe

>[!NOTE]
>
>In de modus [!DNL Experience Manager Sites] **[!UICONTROL Edit]** van een webpagina wordt het 3D-element weergegeven in de component 3D-media, maar interactie met het element is niet mogelijk. Als u het element interactief wilt maken, kunt u de functie **[!UICONTROL Preview]** gebruiken om de webpagina in de pagina-editor weer te geven met volledige toegang tot de functionaliteit van de 3D Media-component.

## Statische dynamische media 3D-elementen publiceren {#publishing-three-d-assets}

De dynamische Media keurt diverse 3D dossierformaten goed die als *statische inhoud* in Dynamische Media worden gesteund. De statische inhoud betekent dat u 3D activa kunt uploaden en publiceren, maar er is geen steun voor *dynamische* beeldvorming of beeld het teruggeven die met 3D activa wordt geassocieerd. De reden hiervoor is dat Dynamic Media Imaging Server 3D-indelingen niet herkent. Nadat u een 3D-element hebt gepubliceerd in dynamische media, hebt u dus een directe URL die u kunt kopiëren. De URL voor het 3D-element volgt de gebruikelijke URL-structuur voor dynamische media. In tegenstelling tot traditionele afbeeldingselementen in Dynamic Media kunt u echter geen parameters in de URL van het element bewerken.

Zie ook [ een URL voor statische activa ](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md#obtaining-a-url-for-a-static-asset) verkrijgen.

In **[!UICONTROL Card View]** wordt een klein globpictogram direct onder de naam van een element weergegeven en links van de datum en tijd om aan te geven dat het is gepubliceerd. In de **[!UICONTROL List View]** geeft een kolom **[!UICONTROL Published]** aan welke assets zijn gepubliceerd en welke niet.

Als u [!DNL Experience Manager] als uw WCM gebruikt, gebruik deze het publiceren methode om de Dynamische Media 3D activa direct op uw Web-pagina toe te voegen.

Zie ook [ de Dynamische activa van Media publiceren ](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

Zie ook [ publiceren pagina&#39;s ](/help/sites-cloud/authoring/sites-console/publishing-pages.md).

**om statische Dynamische Media 3D activa te publiceren:**

1. Open een 3D-element (GLB, OBJ of STL-bestandsindeling).
1. Selecteer op de pagina Details op de werkbalk de optie **[!UICONTROL Quick Publish]** .

   ![ 3d-activa-snel-publiceer ](/help/assets/dynamic-media/assets/3d-asset-quick-publisha.png)

1. Selecteer **[!UICONTROL Close]** om het dialoogvenster te sluiten en terug te keren naar de pagina met elementdetails.
1. Selecteer **[!UICONTROL Renditions]** in de vervolgkeuzelijst links van de bestandsnaam van het 3D-element.

   ![ 3d-activa-vertoningen ](/help/assets/dynamic-media/assets/3d-asset-renditionsa.png)

1. Selecteer **[!UICONTROL original]**. Wanneer een 3D-element wordt gepubliceerd (of geactiveerd), wordt de knop **[!UICONTROL URL]** linksonder op de pagina weergegeven als aan alle volgende 3D-elementvoorwaarden is voldaan:
   * Het 3D-element heeft een ondersteunde indeling (GLB, OBJ, STL en USDZ).
   * Het 3D element werd opgenomen in het Dynamische Systeem van de Productie van het Beeld van Media (IPS).
   * Het 3D-element wordt gepubliceerd.

   ![ 3d-activa-url ](/help/assets/dynamic-media/assets/3d-asset-urla.png)

1. Selecteer **[!UICONTROL URL]** als u de directe productie-URL van het 3D-element wilt weergeven die u kunt kopiëren en gebruiken op webpagina&#39;s.

### Alternatieve methoden voor het publiceren van Dynamic Media 3D-elementen met de Dimensional-viewer {#alternate-publish-methods}

Gebruik de volgende twee methodes om Dynamische Media 3D activa te publiceren als u *niet* gebruikend [!DNL Experience Manager] als uw WCM bent.

* **[!UICONTROL URL]** - Gebruik **[!UICONTROL URL]** als u een systeem voor webcontentbeheer van derden gebruikt en u dynamische media 3D-elementen met de DIMM-viewer wilt koppelen aan uw webpagina&#39;s.

  Zie [ Verbinding URLs aan uw Webtoepassing ](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md#obtaining-a-url-for-an-asset).

* **[!UICONTROL Embed]** - Gebruik **[!UICONTROL Embed]** als u een dynamisch Media 3D-element wilt weergeven dat is ingesloten op een webpagina met de DIMM-viewer. U kopieert de insluitcode naar het klembord, zodat u deze op uw webpagina&#39;s kunt plakken. Het bewerken van de code is niet toegestaan in het dialoogvenster **[!UICONTROL Embed]**.

  Zie [ de Dynamische Video van Media, de kijker van het Beeld, of de kijker van de Afmeting op een Web-pagina ](/help/assets/dynamic-media/embed-code.md#embedding-the-video-or-image-viewer-on-a-web-page) inbedden.
