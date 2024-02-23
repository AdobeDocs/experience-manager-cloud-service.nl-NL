---
title: Werken met 3D-middelen in Dynamic Media
description: Leer hoe u met 3D-middelen werkt in Dynamic Media.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS and Experience Manager as a Cloud Service
topic-tags: introduction
content-type: reference
feature: 3D Assets
role: User
exl-id: 82084ba7-1302-4cbd-8626-d77b3aaa4ed1
source-git-commit: f6162dcbc5b7937d55922e8c963a402697110329
workflow-type: tm+mt
source-wordcount: '2181'
ht-degree: 2%

---

# Werken met 3D-middelen in Dynamic Media {#working-with-three-d-assets-dm}

Met Dynamic Media kunt u 3D-middelen uploaden, beheren, weergeven en leveren als een indrukwekkende ervaring.

* Publiceren met één klik (gebruiken **[!UICONTROL Quick Publish]** op de werkbalk) van 3D-middelen om een URL te genereren.
* Geoptimaliseerde ondersteuning voor het weergeven van 3D-middelen met de voorinstelling voor interactieve maatviewer van hoge kwaliteit, aangedreven door Adobe Dimension.
* Met de 3D Media WCM-component kunt u eenvoudig 3D-elementen toevoegen aan uw [!DNL Adobe Experience Manager Sites] pagina&#39;s.

Er is geen aanvullende installatie vereist voor het gebruik van 3D-middelen in Dynamic Media.

![Schoen in 3d](/help/assets/dynamic-media/assets/3d-dimensional-viewer-quickpublish-url-embed2a.png)

<!-- See also [Dynamic Media 3D Release Notes](/help/release-notes/aem3d-release-notes.md). -->

## 3D-indelingen ondersteund in Dynamic Media {#supported-three-d-file-formats-in-dm}

Dynamic Media ondersteunt de volgende 3D-bestandsindelingen.

Zie ook [3D-indelingen ondersteund in Experience Manager Assets](/help/assets/file-format-support.md#support-3d-formats)

| 3D-bestandsextensie | Bestandsindeling | MIME-type | Notities |
|---|---|---|---|
| GLB | Binaire GL-transmissie | model/gltf-binair | Hiermee neemt u de materialen en structuren op als één enkel element. |
| OBJ | WaveFront 3D-objectbestand | application/x-tgif |  |
| STL | Stereolithografie | application/vnd.ms-pki.stl |  |
| USDZ | Universal Scene Description Zip-archief | model/vnd.usdz+zip | *Alleen ondersteuning voor inname; geen weergave of interactie is beschikbaar.* USDZ is een eigen 3D-indeling die door Safari of iOS kan worden weergegeven. |

De 3D Media WCM-component en de 3D-voorvertoning op de pagina Details van een element zijn niet compatibel met de nieuwste versie van Chrome (97.x). Als u met 3D-elementen wilt werken, gebruikt u Firefox of Safari of een eerdere versie van Chrome (96.x).

## Snel starten: 3D-middelen in Dynamic Media {#quick-start-three-d}

De volgende stapsgewijze beschrijving van de workflow is ontworpen om u te helpen snel aan de slag te gaan met 3D-middelen in Dynamic Media.

Voordat u in Dynamic Media met 3D-middelen gaat werken, moet u ervoor zorgen dat [!DNL Experience Manager] beheerder heeft Dynamic Media-Cloud Servicen al ingeschakeld en geconfigureerd.

Zie [Dynamic Media-Cloud Servicen configureren](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services).

1. **3D-elementen uploaden**

   * [Uw 3D-elementen uploaden voor gebruik in Dynamic Media](/help/assets/add-assets.md#upload-assets)
   * [Ondersteunde 3D-bestandsindelingen voor uploaden in Dynamic Media](#supported-three-d-file-formats-in-dm)

1. **3D-middelen beheren**

   * 3D-middelen organiseren en doorzoeken

      * [Digitale elementen ordenen](/help/assets/organize-assets.md)
      * [3D-middelen zoeken](/help/assets/search-assets.md)

   * 3D-elementen weergeven

      * [3D-middelen weergeven en gebruiken](#viewing-three-d-assets)
      * [De voorinstelling voor de dimensionale viewer beheren](/help/assets/dynamic-media/managing-viewer-presets.md)

   * Werken met metagegevens van 3D-elementen

      * [Metagegevens voor digitale elementen beheren](/help/assets/manage-digital-assets.md#editing-properties)
      * [Metagegevensschema&#39;s](/help/assets/metadata-schemas.md)

1. **3D-elementen publiceren**

   * [Statische Dynamic Media 3D-elementen publiceren](#publishing-three-d-assets)
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
>Zie [Voorinstellingen voor viewers beheren](/help/assets/dynamic-media/managing-viewer-presets.md).

## Een 3D-element weergeven en interactief werken via de pagina met elementdetails {#viewing-three-d-assets-from-asset-details-page}

Zie ook [Elementen voorvertonen met de software-interface](/help/assets/dynamic-media/previewing-assets.md).

**U kunt als volgt een 3D-element weergeven en ermee werken op de pagina met elementdetails:**

1. Zorg ervoor dat u 3D-elementen hebt geüpload naar [!DNL Experience Manager].

   Zie [Uw 3D-elementen uploaden voor gebruik in Dynamic Media](/help/assets/add-assets.md#upload-assets).

1. Van [!DNL Experience Manager], over de **[!UICONTROL Navigation]** pagina, selecteert u **[!UICONTROL Assets > Files]**.
1. In de rechterbovenhoek van de pagina, vanaf de **[!UICONTROL View]** vervolgkeuzelijst, selecteert u **[!UICONTROL Card View]**.
1. Navigeer naar een 3D-element dat u wilt weergeven.
1. Als u het element wilt openen op de pagina Details, selecteert u de kaart van het 3D-element.
1. Voer op de pagina Details voor het 3D-element een van de volgende handelingen uit:

   | Weergave | Beschrijving | Muishandeling | Handeling op het aanraakscherm |
   | --- | --- | --- | --- |
   | **De camera draaien** | Draai de weergave rond de 3D-scène en -objecten. | Klik met de linkermuisknop en sleep. | Druk met één vinger en sleep. |
   | **Uw camera pannen** | U kunt de weergave naar links, rechts, omhoog of omlaag pannen. | Klik met de rechtermuisknop en sleep. | Druk met twee vingers en sleep. |
   | **Uw camera zoomen** | Ga in- en uit gebieden in de 3D-scène. | Schuifwiel. | Kneep met twee vingers. |
   | **De camera opnieuw opnemen** | Voer de camera opnieuw in op een punt op een object in de 3D-scène. | Dubbelklik. | Dubbelselecteren. |
   | **Herstellen** | Selecteer in de rechterbenedenhoek van de pagina het pictogram Herstellen om het doelpunt van de weergave te herstellen naar het midden van het 3D-element. Met Herstellen wordt de camera ook dichter bij of verder weg geplaatst om het middel volledig en bij een redelijke weergavegrootte weer te geven. |   |   |
   | **Modus Volledig scherm** | Als u de modus Volledig scherm wilt inschakelen, klikt u op het pictogram Volledig scherm rechtsonder op de pagina. |   |   |

1. Selecteer in de rechterbovenhoek van de pagina de optie **[!UICONTROL Close]** om terug te keren naar de middelenpagina.

## Een 3D-element in een 3D-mediacomponent weergeven en hiermee communiceren {#interacting-with-asset-inside-three-d-media-component}

Wanneer een webpagina zich in **[!UICONTROL Edit]** is geen interactie mogelijk met een 3D-element. Als u het element interactief wilt maken, kunt u de opdracht **[!UICONTROL Preview]** gebruiken om de webpagina in de pagina-editor weer te geven met volledige toegang tot de functionaliteit van de 3D-mediacomponent.

>[!IMPORTANT]
>
>U kunt deze taak pas uitvoeren nadat u een 3D-mediacomponent aan een webpagina hebt toegevoegd en een 3D-element aan de component hebt toegewezen. Zie [De 3D-mediacomponent toevoegen aan een webpagina](#adding-the-three-d-media-component-to-a-web-page) en [Een 3D-element toewijzen aan een 3D-mediacomponent](#assigning-a-three-d-asset-to-the-component).

Zie ook [Elementen voorvertonen met de software-interface](/help/assets/dynamic-media/previewing-assets.md).

**Een 3D-element in een 3D-mediacomponent weergeven en hiermee werken:**

1. Terwijl een webpagina zich in **[!UICONTROL Edit]** Voer een van de volgende handelingen uit in de modus:

   * Klik in de rechterbovenhoek van de pagina op **[!UICONTROL Preview]** om binnen te gaan **[!UICONTROL Preview]** -modus.
   * Verwijderen `/editor.html` van de pagina-URL in de browser.

   ![3D-element weergeven binnen de 3D-mediacomponent](/help/assets/dynamic-media/assets/3d-asset-in-3d-mediaa.png)
Een volledig interactief 3D-element zoals weergegeven in **[!UICONTROL Preview]** -modus.

1. Tijdens het aanmelden **[!UICONTROL Preview]** Voer een van de volgende handelingen uit in de modus:

   | Weergave | Beschrijving | Muishandeling | Handeling op het aanraakscherm |
   | --- | --- | --- | --- |
   | **De camera draaien** | Draai de weergave rond de 3D-scène en -objecten. | Klik met de linkermuisknop en sleep. | Druk met één vinger en sleep. |
   | **Uw camera pannen** | U kunt de weergave naar links, rechts, omhoog of omlaag pannen. | Klik met de rechtermuisknop en sleep. | Druk met twee vingers en sleep. |
   | **Uw camera zoomen** | Ga in- en uit gebieden in de 3D-scène. | Schuifwiel. | Kneep met twee vingers. |
   | **De camera opnieuw opnemen** | Voer de camera opnieuw in op een punt op een object in de 3D-scène. | Dubbelklik. | Dubbelselecteren. |
   | **Herstellen** | Selecteer in de rechterbenedenhoek van de pagina het pictogram Herstellen om het doelpunt van de weergave te herstellen naar het midden van het 3D-element. Met Herstellen wordt de camera ook dichter bij of verder weg geplaatst om het middel volledig en bij een redelijke weergavegrootte weer te geven. |   |   |
   | **Modus Volledig scherm** | Als u de modus Volledig scherm wilt inschakelen, klikt u op het pictogram Volledig scherm rechtsonder op de pagina. |   |   |

## Informatie over het werken met de 3D-mediacomponent {#working-with-three-d-media-component}

Dynamic Media bevat een Dynamic Media 3D Media-component die u kunt gebruiken in [!DNL Experience Manager Sites] om het interactief weergeven van 3D-modellen op uw webpagina&#39;s in te schakelen.

* [De 3D-mediacomponent toevoegen aan de paginasjabloon](#adding-three-d-media-component-to-page-template)
* [De 3D-mediacomponent toevoegen aan een webpagina](#adding-the-three-d-media-component-to-a-web-page)
   * [Optioneel - De 3D-mediacomponent configureren](#configuring-the-three-d-component)
* [Een 3D-element toewijzen aan de 3D-mediacomponent](#assigning-a-three-d-asset-to-the-component)

## De 3D-mediacomponent toevoegen aan de paginasjabloon {#adding-three-d-media-component-to-page-template}

1. Navigeren naar **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL Templates]**.
1. Navigeer naar de paginasjabloon waarin u de 3D-component wilt inschakelen en selecteer de sjabloon.
1. Selecteer **[!UICONTROL Edit]**.
1. Selecteer in de rechterbovenhoek van de pagina in het keuzemenu de optie **[!UICONTROL Structure]** als deze nog niet actief is.

   ![3d-media-component-structuur](/help/assets/dynamic-media/assets/3d-media-component-structurea.png)

1. Als u een leeg gebied wilt selecteren en de bijbehorende werkbalk wilt openen, selecteert u het lege gebied in het dialoogvenster **[!UICONTROL Layout Container]** regio.
1. Selecteer op de werkbalk de optie **[!UICONTROL Policy]** pictogram om het **[!UICONTROL Policy Editor]**.
1. In de **[!UICONTROL Properties]** , onder **[!UICONTROL Allowed Components]** tab, schuiven naar **[!UICONTROL Dynamic Media]** Vouw vervolgens de lijst uit en controleer **[!UICONTROL 3D Media]**.
1. Selecteren **[!UICONTROL Done]** om de wijzigingen op te slaan en het dialoogvenster **[!UICONTROL Policy Editor]**.

   U kunt de Dynamic Media 3D Media-component nu op alle pagina&#39;s plaatsen die deze sjabloon gebruiken.

## De 3D-mediacomponent toevoegen aan een webpagina {#adding-the-three-d-media-component-to-a-web-page}

Als u [!DNL Experience Manager] Als uw webinhoudbeheersysteem kunt u 3D-elementen aan uw webpagina&#39;s toevoegen met behulp van de 3D Media-component.

Zie ook [Dynamic Media-elementen toevoegen aan pagina&#39;s](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).

1. Openen [!DNL Experience Manager Sites] en selecteert u de webpagina waaraan u de Dynamic Media 3D Media-component wilt toevoegen.
1. Als u de pagina in de pagina-editor wilt openen, selecteert u de optie **[!UICONTROL Edit]** (potlood). Controleer of **[!UICONTROL Edit]** wordt rechtsboven op de pagina geselecteerd.

   ![3d-media-component-add](/help/assets/dynamic-media/assets/3d-media-component-edita.png)

1. Selecteer op de werkbalk het pictogram Zijpaneel om de weergave van het deelvenster in of uit te schakelen.

1. Selecteer in het zijpaneel het pictogram met het plusteken om het dialoogvenster **[!UICONTROL Components]** lijst.

   ![3d-media-component-slepen-neerzetten](/help/assets/dynamic-media/assets/3d-assets-filtera.png)

1. Sleep de **[!UICONTROL 3D Media]** uit de **[!UICONTROL Components]** Hiermee geeft u een lijst weer naar de locatie op de pagina waar u de 3D-viewer wilt weergeven.

U kunt nu een 3D-element aan de component toewijzen.

Zie [Een 3D-element toewijzen aan de 3D-mediacomponent](#assigning-a-three-d-asset-to-the-component)

### Optioneel - De 3D-mediacomponent configureren {#configuring-the-three-d-component}

1. In de [!DNL Experience Manager Sites] pagina-editor, selecteert u de **[!UICONTROL 3D Media Viewer]** die u eerder aan de pagina hebt toegevoegd.
1. Als u het dialoogvenster voor componentconfiguratie wilt openen, selecteert u de optie **[!UICONTROL Configuration]** pictogram (moersleutel)

   ![3d-media-component-config](/help/assets/dynamic-media/assets/3d-media-component-configa.png)

1. Selecteer in het dialoogvenster 3D-media in de vervolgkeuzelijst Voorinstelling viewer de optie **[!UICONTROL Dimensional]** om de voorinstelling voor de maatviewer toe te wijzen aan de component.

   ![3d-media-component-edit-config](/help/assets/dynamic-media/assets/3d-media-component-edit-configa.png)

1. Selecteer in de rechterbovenhoek het vinkje waarop u de wijzigingen wilt opslaan.

## Een 3D-element toewijzen aan de 3D-mediacomponent {#assigning-a-three-d-asset-to-the-component}

Nadat u een 3D-mediacomponent aan een webpagina hebt toegevoegd, kunt u er een 3D-element aan toewijzen.

Zie [De 3D-mediacomponent toevoegen aan een webpagina](#adding-the-three-d-media-component-to-a-web-page).

1. In de [!DNL Experience Manager Sites] pagina-editor, klik op de knop **[!UICONTROL Assets]** pictogram om te openen **[!UICONTROL Assets]** in het zijpaneel.
1. Selecteer in de vervolgkeuzelijst de optie **[!UICONTROL 3D]** alleen 3D-elementbestandstypen weergeven.
1. Zoek in het zijpaneel naar het 3D-element dat u wilt weergeven op de pagina die u bewerkt.
1. Sleep het 3D-element van het zijpaneel Middelen naar het deelvenster **[!UICONTROL 3D Media]** die u eerder aan de pagina hebt toegevoegd.

   ![3D-element toewijzen aan 3d-mediacomponent](/help/assets/dynamic-media/assets/3d-asset-adda.png)

>[!NOTE]
>
>Terwijl een webpagina zich in de [!DNL Experience Manager Sites] **[!UICONTROL Edit]** In de 3D-mediacomponent wordt het 3D-element weergegeven, maar interactie met het element is niet mogelijk. Als u het element interactief wilt maken, kunt u de opdracht **[!UICONTROL Preview]** gebruiken om de webpagina in de pagina-editor weer te geven met volledige toegang tot de functionaliteit van de 3D-mediacomponent.

## Statische Dynamic Media 3D-elementen publiceren {#publishing-three-d-assets}

Dynamic Media accepteert verschillende 3D-bestandsindelingen die worden ondersteund als *statische inhoud* in Dynamic Media. Statische inhoud betekent dat u 3D-elementen kunt uploaden en publiceren, maar dat er geen ondersteuning is voor *dynamic* afbeelding of afbeelding die wordt vernieuwd en die is gekoppeld aan het 3D-element. De reden hiervoor is dat Dynamic Media Imaging Server 3D-indelingen niet herkent. Nadat u een 3D-element hebt gepubliceerd in Dynamic Media, hebt u dus een directe URL die u kunt kopiëren. De URL voor het 3D-element volgt de gebruikelijke URL-structuur van Dynamic Media. In tegenstelling tot traditionele afbeeldingselementen in Dynamic Media kunt u echter geen parameters in de URL van het element bewerken.

Zie ook [Een URL verkrijgen voor een statisch element](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md#obtaining-a-url-for-a-static-asset).

In de **[!UICONTROL Card View]**, wordt een klein globpictogram direct onder de naam van een element weergegeven en links van de datum en tijd om aan te geven dat het is gepubliceerd. In de **[!UICONTROL List View]** geeft een kolom **[!UICONTROL Published]** aan welke assets zijn gepubliceerd en welke niet.

Als u [!DNL Experience Manager] als uw WCM, gebruik deze het publiceren methode om de Dynamic Media 3D activa direct op uw Web-pagina toe te voegen.

Zie ook [Dynamic Media-elementen publiceren](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

Zie ook [Pagina&#39;s publiceren](/help/sites-cloud/authoring/sites-console/publishing-pages.md).

**Statische Dynamic Media 3D-elementen publiceren:**

1. Open een 3D-element (GLB, OBJ of STL-bestandsindeling).
1. Selecteer op de pagina Details op de werkbalk de optie **[!UICONTROL Quick Publish]**.

   ![3d-asset-quick-publish](/help/assets/dynamic-media/assets/3d-asset-quick-publisha.png)

1. Selecteren **[!UICONTROL Close]** om het dialoogvenster te sluiten en terug te keren naar de pagina met elementdetails.
1. Selecteer in de vervolgkeuzelijst links van de bestandsnaam van het 3D-element de optie **[!UICONTROL Renditions]**.

   ![3d-asset-renditions](/help/assets/dynamic-media/assets/3d-asset-renditionsa.png)

1. Selecteer **[!UICONTROL original]**. Wanneer een 3D-element wordt gepubliceerd (of geactiveerd), wordt het **[!UICONTROL URL]** wordt linksonder op de pagina weergegeven als aan alle volgende 3D-elementvoorwaarden is voldaan:
   * Het 3D-element heeft een ondersteunde indeling (GLB, OBJ, STL en USDZ).
   * Het 3D-element is opgenomen in het Dynamic Media Image Production System (IPS).
   * Het 3D-element wordt gepubliceerd.

   ![3d-asset-url](/help/assets/dynamic-media/assets/3d-asset-urla.png)

1. Als u de directe productie-URL van het 3D-element wilt weergeven die u kunt kopiëren en gebruiken op webpagina&#39;s, selecteert u **[!UICONTROL URL]**.

### Alternatieve methoden voor het publiceren van Dynamic Media 3D-elementen met de Dimensional-viewer {#alternate-publish-methods}

Gebruik de volgende twee methoden voor het publiceren van Dynamic Media 3D-elementen als u *niet* gebruiken [!DNL Experience Manager] als uw WCM.

* **[!UICONTROL URL]** - Gebruik **[!UICONTROL URL]** als u een extern systeem voor webcontentbeheer gebruikt en u Dynamic Media 3D-middelen wilt koppelen aan uw webpagina&#39;s met de DIMM-viewer.

  Zie [URL&#39;s koppelen aan uw webtoepassing](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md#obtaining-a-url-for-an-asset).

* **[!UICONTROL Embed]** - Gebruik **[!UICONTROL Embed]** als u een Dynamic Media 3D-element wilt weergeven dat is ingesloten op een webpagina met de DIMM-viewer. U kopieert de insluitcode naar het klembord, zodat u deze op uw webpagina&#39;s kunt plakken. Het bewerken van de code is niet toegestaan in het dialoogvenster **[!UICONTROL Embed]**.

  Zie [De Dynamic Media Video-, Image Viewer- of Dimensional-viewer insluiten op een webpagina](/help/assets/dynamic-media/embed-code.md#embedding-the-video-or-image-viewer-on-a-web-page).
