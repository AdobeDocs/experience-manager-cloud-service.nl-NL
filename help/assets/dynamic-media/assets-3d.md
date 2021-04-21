---
title: Werken met 3D-elementen in Dynamic Media
description: Leer hoe u met 3D-middelen werkt in Dynamic Media.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS and Experience Manager as a Cloud Service
topic-tags: introduction
content-type: reference
feature: 3D-middelen
role: Business Practitioner
exl-id: 82084ba7-1302-4cbd-8626-d77b3aaa4ed1
translation-type: tm+mt
source-git-commit: e94289bccc09ceed89a2f8b926817507eaa19968
workflow-type: tm+mt
source-wordcount: '2198'
ht-degree: 2%

---

# Werken met 3D-elementen in Dynamic Media {#working-with-three-d-assets-dm}

Met Dynamic Media kunt u 3D-middelen uploaden, beheren, weergeven en leveren als een indrukwekkende ervaring.

* Klik met één klik op het publiceren van 3D-elementen (met **[!UICONTROL Quick Publish]** op de werkbalk) om een URL te genereren.
* Geoptimaliseerde ondersteuning voor het weergeven van 3D-middelen met de voorinstelling voor interactieve maatviewer van hoge kwaliteit, aangedreven door Adobe Dimension.
* Met de 3D Media WCM-component kunt u eenvoudig 3D-elementen toevoegen aan uw Adobe Experience Manager Sites-pagina&#39;s.

Er is geen aanvullende installatie vereist voor het gebruik van 3D-middelen in Dynamic Media.

![Schoen in 3d](/help/assets/dynamic-media/assets/3d-dimensional-viewer-quickpublish-url-embed2a.png)

<!-- See also [Dynamic Media 3D Release Notes](/help/release-notes/aem3d-release-notes.md). -->

## 3D-indelingen ondersteund in Dynamic Media {#supported-three-d-file-formats-in-dm}

Dynamic Media ondersteunt de volgende 3D-bestandsindelingen.

Zie ook [Ondersteunde 3D-indelingen](/help/assets/file-format-support.md#support-3d-formats)

| 3D-bestandsextensie | Bestandsindeling | MIME-type | Opmerkingen |
|---|---|---|---|
| GLB | Binaire GL-transmissie | model/gltf-binair | Hiermee neemt u de materialen en structuren op als één enkel element. |
| OBJ | WaveFront 3D-objectbestand | application/x-tgif |  |
| STL | Stereolithografie | application/vnd.ms-pki.stl |  |
| USDZ | Universal Scene Description Zip-archief | model/vnd.usdz+zip | *Alleen ondersteuning voor inname; er is geen weergave of interactie beschikbaar.* USDZ is een eigen 3D-indeling die door Safari of iOS kan worden weergegeven. |

## Snel starten: 3D-elementen in Dynamic Media {#quick-start-three-d}

De volgende stapsgewijze beschrijving van de workflow is ontworpen om u te helpen snel aan de slag te gaan met 3D-middelen in Dynamic Media.

Voordat u in Dynamic Media met 3D-elementen gaat werken, moet u controleren of de beheerder van de Experience Manager Dynamic Media-Cloud Services al heeft ingeschakeld en geconfigureerd.

Zie [Dynamic Media-Cloud Services configureren](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services).

1. **3D-elementen uploaden**

   * [3D-middelen uploaden voor gebruik in Dynamic Media](/help/assets/add-assets.md#upload-assets)
   * [Ondersteunde 3D-bestandsindelingen voor uploaden in Dynamic Media](#supported-three-d-file-formats-in-dm)

1. **3D-middelen beheren**

   * 3D-middelen organiseren en doorzoeken

      * [Digitale elementen ordenen](/help/assets/organize-assets.md)
      * [3D-middelen zoeken](/help/assets/search-assets.md)
   * 3D-elementen weergeven

      * [3D-elementen weergeven en communiceren](#viewing-three-d-assets)
      * [De voorinstelling voor de dimensionale viewer beheren](/help/assets/dynamic-media/managing-viewer-presets.md)
   * Werken met metagegevens van 3D-elementen

      * [Metagegevens voor digitale elementen beheren](/help/assets/manage-digital-assets.md#editing-properties)
      * [Metagegevensschema&#39;s](/help/assets/metadata-schemas.md)



1. **3D-elementen publiceren**

   * [Statische Dynamic Media 3D-elementen publiceren](#publishing-three-d-assets)
   * [Alternatieve methoden voor het publiceren van Dynamic Media 3D-elementen met de Dimensional-viewer](#alternate-publish-methods)

## Informatie over het weergeven van en communiceren met 3D-elementen {#viewing-three-d-assets}

In deze sectie wordt beschreven hoe u 3D-elementen op twee verschillende manieren kunt weergeven en gebruiken: vanuit de pagina met elementdetails en vanuit de 3D-mediacomponent in Sites.

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
>Zie [Voorinstellingen voor viewers beheren](/help/assets/dynamic-media/managing-viewer-presets.md).

## Een 3D-element weergeven en interactief gebruiken op de pagina {#viewing-three-d-assets-from-asset-details-page} met elementdetails

Zie ook [Elementen voorvertonen met behulp van de softwareinterface](/help/assets/dynamic-media/previewing-assets.md).

**Een 3D-element weergeven en interactief werken via de pagina met elementdetails**

1. Zorg ervoor dat u 3D-elementen hebt geüpload naar de Experience Manager.

   Zie [Uw 3D-elementen uploaden voor gebruik in Dynamic Media](/help/assets/add-assets.md#upload-assets).

1. Tik **[!UICONTROL Assets > Files]** vanaf Experience Manager op de pagina **[!UICONTROL Navigation]**.
1. Tik in de rechterbovenhoek van de pagina in de vervolgkeuzelijst **[!UICONTROL View]** op **[!UICONTROL Card View]**.
1. Navigeer naar een 3D-element dat u wilt weergeven.
1. Tik op de kaart van het 3D-element om het element op de pagina Details te openen.
1. Voer op de pagina Details voor het 3D-element een van de volgende handelingen uit:

   * **Draai uw camera**  - Draai uw weergave rond de 3D-scène en de objecten.
      * _Muis_: Klik met de linkermuisknop en sleep.
      * _Aanraakscherm_: Druk met één vinger en sleep.
   * **Pannen met uw camera** : pannen met uw weergave naar links, rechts, omhoog of omlaag.
      * _Muis_: Klik met de rechtermuisknop en sleep.
      * _Aanraakscherm_: Druk met twee vingers en sleep.
   * **Zoom de camera**  in en uit. Zoom de camera in en uit de gebieden van de 3D-scène.
      * _Muis_: Schuifwiel.
      * _Aanraakscherm_: Kneep met twee vingers.
   * **Start de camera**  opnieuw op - centreer de camera opnieuw op een punt op een object in de 3D-scène.
      * _Muis_: Dubbelklik.
      * _Aanraakscherm_: Dubbeltik.
   * **Herstellen**  - Tik in de rechterbenedenhoek van de pagina op het pictogram Herstellen om het doelpunt van de weergave te herstellen naar het midden van het 3D-element. Met Herstellen wordt de camera ook dichter bij of verder weg geplaatst om het middel volledig en bij een redelijke weergavegrootte weer te geven.
   * **Modus**  Volledig scherm - Tik op het pictogram Volledig scherm om de modus Volledig scherm te activeren, in de rechterbenedenhoek van de pagina.

1. Tik in de rechterbovenhoek van de pagina op **[!UICONTROL Close]** om terug te keren naar de pagina Middelen.

## Een 3D-element in een 3D-mediacomponent {#interacting-with-asset-inside-three-d-media-component} weergeven en hiermee communiceren

Wanneer een webpagina in de modus **[!UICONTROL Edit]** staat, is interactie met een 3D-element niet mogelijk. Als u het element interactief wilt maken, kunt u de functie **[!UICONTROL Preview]** gebruiken om de webpagina in de pagina-editor weer te geven met volledige toegang tot de functionaliteit van de 3D Media-component.

>[!IMPORTANT]
>
>U kunt deze taak pas uitvoeren nadat u een 3D-mediacomponent aan een webpagina hebt toegevoegd en een 3D-element aan de component hebt toegewezen. Zie [De 3D-mediacomponent toevoegen aan een webpagina](#adding-the-three-d-media-component-to-a-web-page) en [Een 3D-element toewijzen aan een 3D-mediacomponent](#assigning-a-three-d-asset-to-the-component).

Zie ook [Elementen voorvertonen met behulp van de softwareinterface](/help/assets/dynamic-media/previewing-assets.md).

**Een 3D-element in een 3D-mediacomponent weergeven en ermee werken**

1. Voer een van de volgende handelingen uit terwijl de modus **[!UICONTROL Edit]** voor een webpagina is geactiveerd:

   * Rechtsboven op de pagina klikt u op **[!UICONTROL Preview]** om de modus **[!UICONTROL Preview]** te activeren.
   * Verwijder `/editor.html` uit de pagina-URL in de browser.

Een volledig interactief 3D-element zoals weergegeven in    ![3D-element dat in de 3D Media-](/help/assets/dynamic-media/assets/3d-asset-in-3d-mediaa.png)
componentA volledig interactief 3D-element wordt weergegeven, zoals in de  **[!UICONTROL Preview]** modus wordt weergegeven.

1. Voer in de modus **[!UICONTROL Preview]** een van de volgende handelingen uit:

   * **Draai uw camera**  - Draai uw weergave rond de 3D-scène en de objecten.
      * _Muis_: Klik met de linkermuisknop en sleep.
      * _Aanraakscherm_: Druk met één vinger en sleep.
   * **Pannen met uw camera** : pannen met uw weergave naar links, rechts, omhoog of omlaag.
      * _Muis_: Klik met de rechtermuisknop en sleep.
      * _Aanraakscherm_: Druk met twee vingers en sleep.
   * **Zoom de camera**  in en uit. Zoom de camera in en uit de gebieden van de 3D-scène.
      * _Muis_: Schuifwiel.
      * _Aanraakscherm_: Kneep met twee vingers.
   * **Start de camera**  opnieuw op - centreer de camera opnieuw op een punt op een object in de 3D-scène.
      * _Muis_: Dubbelklik.
      * _Aanraakscherm_: Dubbeltik.
   * **Herstellen**  - Tik in de rechterbenedenhoek van de pagina op het pictogram Herstellen om het doelpunt van de weergave te herstellen naar het midden van het 3D-element. Met Herstellen wordt de camera ook dichter bij of verder weg geplaatst om het middel volledig en bij een redelijke weergavegrootte weer te geven.
   * **Modus**  Volledig scherm - Tik op het pictogram Volledig scherm om de modus Volledig scherm te activeren, in de rechterbenedenhoek van de pagina.

## Informatie over het werken met de 3D-mediacomponent {#working-with-three-d-media-component}

Dynamic Media bevat een Dynamic Media 3D Media-component die u kunt gebruiken in Experience Manager Sites om interactieve weergave van 3D-modellen op uw webpagina&#39;s mogelijk te maken.

* [De 3D-mediacomponent toevoegen aan de paginasjabloon](#adding-three-d-media-component-to-page-template)
* [De 3D-mediacomponent toevoegen aan een webpagina](#adding-the-three-d-media-component-to-a-web-page)
   * [Optioneel - De 3D-mediacomponent configureren](#configuring-the-three-d-component)
* [Een 3D-element toewijzen aan de 3D-mediacomponent](#assigning-a-three-d-asset-to-the-component)


## De 3D-mediacomponent toevoegen aan de paginasjabloon {#adding-three-d-media-component-to-page-template}

1. Ga naar **[!UICONTROL Tools > General > Templates]**.
1. Navigeer naar de paginasjabloon waarin u de 3D-component wilt inschakelen en selecteer de sjabloon.
1. Tik op **[!UICONTROL Edit]** om de sjabloon te openen.
1. Selecteer in de rechterbovenhoek van de pagina **[!UICONTROL Structure]**-modus in het keuzemenu als deze nog niet actief is.

   ![3d-media-component-structuur](/help/assets/dynamic-media/assets/3d-media-component-structurea.png)

1. Tik op het lege gebied in het gebied **[!UICONTROL Layout Container]** om een leeg gebied te selecteren en de bijbehorende werkbalk te openen.
1. Tik op het pictogram **[!UICONTROL Policy]** op de werkbalk om **[!UICONTROL Policy Editor]** te openen.
1. Blader in de sectie **[!UICONTROL Properties]** onder het tabblad **[!UICONTROL Allowed Components]** naar **[!UICONTROL Dynamic Media]**, vouw vervolgens de lijst uit en controleer **[!UICONTROL 3D Media]**.
1. Tik **[!UICONTROL Done]** om de wijzigingen op te slaan en **[!UICONTROL Policy Editor]** te sluiten.

   U kunt de Dynamic Media 3D Media-component nu op alle pagina&#39;s plaatsen die deze sjabloon gebruiken.

## De 3D-mediacomponent toevoegen aan een webpagina {#adding-the-three-d-media-component-to-a-web-page}

Als u Experience Manager gebruikt als het webcontentbeheersysteem, kunt u 3D-elementen aan uw webpagina&#39;s toevoegen met behulp van de 3D Media-component.

Zie ook [Dynamic Media-elementen toevoegen aan pagina&#39;s](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).

1. Open Experience Manager Sites en selecteer de webpagina waaraan u de Dynamic Media 3D Media-component wilt toevoegen.
1. Tik op het pictogram **[!UICONTROL Edit]** (potlood) om de pagina in de pagina-editor te openen. Zorg ervoor dat de modus **[!UICONTROL Edit]** rechtsboven op de pagina is geselecteerd.

   ![3d-media-component-add](/help/assets/dynamic-media/assets/3d-media-component-edita.png)

1. Tik op het pictogram Zijpaneel op de werkbalk om de weergave van het deelvenster in of uit te schakelen.

1. Tik in het zijpaneel op het plusteken om de lijst **[!UICONTROL Components]** te openen.

   ![3d-media-component-slepen-neerzetten](/help/assets/dynamic-media/assets/3d-assets-filtera.png)

1. Sleep de component **[!UICONTROL 3D Media]** van de lijst **[!UICONTROL Components]** naar de locatie op de pagina waar u de 3D-viewer wilt weergeven.

U kunt nu een 3D-element aan de component toewijzen.

Zie [Een 3D-element toewijzen aan de 3D-mediacomponent](#assigning-a-three-d-asset-to-the-component)

### Optioneel - De 3D-mediacomponent {#configuring-the-three-d-component} configureren

1. Selecteer in de pagina-editor Sites Experience Manager de **[!UICONTROL 3D Media Viewer]**-component die u eerder aan de pagina hebt toegevoegd.
1. Tik op het pictogram **[!UICONTROL Configuration]** om het dialoogvenster voor componentconfiguratie te openen.

   ![3d-media-component-config](/help/assets/dynamic-media/assets/3d-media-component-configa.png)

1. Selecteer in het dialoogvenster 3D-media in de vervolgkeuzelijst Voorinstelling viewer de optie **[!UICONTROL Dimensional]** om de voorinstelling voor de maatviewer toe te wijzen aan de component.

   ![3d-media-component-edit-config](/help/assets/dynamic-media/assets/3d-media-component-edit-configa.png)

1. Tik in de rechterbovenhoek op het vinkje om de wijzigingen op te slaan.

## 3D-elementen toewijzen aan de 3D-mediacomponent {#assigning-a-three-d-asset-to-the-component}

Nadat u een 3D-mediacomponent aan een webpagina hebt toegevoegd, kunt u er een 3D-element aan toewijzen.

Zie [De 3D-mediacomponent toevoegen aan een webpagina](#adding-the-three-d-media-component-to-a-web-page).

1. Klik in de pagina-editor Sites Experience Manager op het pictogram **[!UICONTROL Assets]** om **[!UICONTROL Assets]** in het zijpaneel te openen.
1. Selecteer **[!UICONTROL 3D]** in de vervolgkeuzelijst om alleen 3D-elementbestandstypen weer te geven.
1. Zoek in het zijpaneel naar het 3D-element dat u wilt weergeven op de pagina die u bewerkt.
1. Sleep het 3D-element van het zijpaneel Middelen naar de **[!UICONTROL 3D Media]**-component die u eerder aan de pagina hebt toegevoegd.

   ![3D-element toewijzen aan 3d-mediacomponent](/help/assets/dynamic-media/assets/3d-asset-adda.png)

>[!NOTE]
>
>In de modus **[!UICONTROL Edit]** van de Experience Manager Sites wordt het 3D-element weergegeven in de 3D-mediacomponent, maar interactie met het element is niet mogelijk. Als u het element interactief wilt maken, kunt u de functie **[!UICONTROL Preview]** gebruiken om de webpagina in de pagina-editor weer te geven met volledige toegang tot de functionaliteit van de 3D Media-component.

## Statische Dynamic Media 3D-elementen publiceren {#publishing-three-d-assets}

Dynamic Media accepteert verschillende 3D-bestandsindelingen die worden ondersteund als *statische inhoud* in Dynamic Media. Statische inhoud houdt in dat u 3D-elementen kunt uploaden en publiceren, maar dat er geen ondersteuning is voor *dynamic*-beeldbewerking of het vernieuwen van afbeeldingen die aan het 3D-element zijn gekoppeld. De reden hiervoor is dat Dynamic Media Imaging Server 3D-indelingen niet herkent. Nadat u een 3D-element hebt gepubliceerd in Dynamic Media, hebt u dus een directe URL die u kunt kopiëren. De URL voor het 3D-element volgt de gebruikelijke URL-structuur van Dynamic Media. In tegenstelling tot traditionele afbeeldingselementen in Dynamic Media kunt u echter geen parameters in de URL van het element bewerken.

Zie ook [Een URL verkrijgen voor een statisch element](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md#obtaining-a-url-for-a-static-asset).

In **[!UICONTROL Card View]** verschijnt een klein globpictogram direct onder de naam van een element en links van zijn datum en tijd om erop te wijzen dat het wordt gepubliceerd. In de **[!UICONTROL List View]** geeft een kolom **[!UICONTROL Published]** aan welke assets zijn gepubliceerd en welke niet.

Als u Experience Manager als uw WCM gebruikt, gebruikt u deze publicatiemethode om de Dynamic Media 3D-elementen rechtstreeks op uw webpagina toe te voegen.

Zie ook [Dynamic Media-elementen publiceren](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

Zie ook [Pagina&#39;s publiceren](/help/sites-cloud/authoring/fundamentals/publishing-pages.md).

**Statische Dynamic Media 3D-elementen publiceren**

1. Open een 3D-element (GLB-, OBJ- of STL-bestandsindeling) om dit weer te geven op de pagina Details.
1. Tik op **[!UICONTROL Quick Publish]** op de werkbalk.

   ![3d-asset-quick-publish](/help/assets/dynamic-media/assets/3d-asset-quick-publisha.png)

1. Tik op **[!UICONTROL Close]** om het dialoogvenster te sluiten en terug te keren naar de pagina met elementdetails.
1. Tik in de vervolgkeuzelijst links van de bestandsnaam van het 3D-element op **[!UICONTROL Renditions]**.

   ![3d-asset-renditions](/help/assets/dynamic-media/assets/3d-asset-renditionsa.png)

1. Tik op **[!UICONTROL original]**. Wanneer een 3D-element wordt gepubliceerd (of geactiveerd), wordt de knop **[!UICONTROL URL]** linksonder op de pagina weergegeven als aan alle volgende 3D-elementvoorwaarden is voldaan:
   * Het 3D-element heeft een ondersteunde indeling (GLB, OBJ, STL en USDZ).
   * Het 3D-element is opgenomen in het Dynamic Media Image Production System (IPS).
   * Het 3D-element wordt gepubliceerd.

   ![3d-asset-url](/help/assets/dynamic-media/assets/3d-asset-urla.png)

1. Tik op **[!UICONTROL URL]** om de directe productie-URL van het 3D-element weer te geven die u kunt kopiëren en gebruiken op webpagina&#39;s.

### Alternatieve methoden voor het publiceren van Dynamic Media 3D-elementen met de Dimensional-viewer {#alternate-publish-methods}

Gebruik de volgende twee methoden voor het publiceren van Dynamic Media 3D-elementen als u *geen* gebruikt als uw WCM-Experience Manager.

* **[!UICONTROL URL]** - Gebruik deze optie  **[!UICONTROL URL]** als u een systeem voor webcontentbeheer van derden gebruikt en u Dynamic Media 3D-middelen wilt koppelen aan uw webpagina&#39;s met de DIMM-viewer.

   Zie [URL&#39;s koppelen aan uw webtoepassing](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md#obtaining-a-url-for-an-asset).

* **[!UICONTROL Embed]** - Gebruik deze optie  **[!UICONTROL Embed]** als u een Dynamic Media 3D-element wilt weergeven dat is ingesloten op een webpagina met de DIMM-viewer. U kopieert de insluitcode naar het klembord, zodat u deze op uw webpagina&#39;s kunt plakken. Het bewerken van de code is niet toegestaan in het dialoogvenster **[!UICONTROL Embed]**.

   Zie [De Dynamic Media-video, afbeeldingsviewer of dimensionale viewer insluiten op een webpagina](/help/assets/dynamic-media/embed-code.md#embedding-the-video-or-image-viewer-on-a-web-page).
