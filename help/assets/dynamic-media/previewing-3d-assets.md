---
title: 3D-elementen voorvertonen
description: Leer hoe u een voorvertoning van 3D-middelen in Experience Manager kunt bekijken.
contentOwner: Rick Brough
feature: 3D Assets
role: User
exl-id: e873bd25-f841-4063-824f-7e48f40bb678
source-git-commit: 36ab36ba7e14962eba3947865545b8a3f29f6bbc
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 0%

---

# 3D-elementen voorvertonen in Adobe Experience Manager{#previewing-3d-assets}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6.5 | [&#x200B; klik hier &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/previewing-3d-assets.html?lang=nl-NL) |
| AEM as a Cloud Service | Dit artikel |

Experience Manager Assets ondersteunt het opnemen, beheren, voorvertonen en leveren van 3D-elementen.

U kunt een voorvertoning van 3D-elementen weergeven met de automatisch gegenereerde miniatuuruitvoeringen of de interactieve 3D-viewer. De interactieve 3D-viewer is beschikbaar op de pagina met elementdetails in Experience Manager. De viewer bevat onder andere een verzameling interactieve besturingselementen voor camera waarmee u de 3D-scène kunt roteren, zoomen en pannen.

<!-- See also [Working with 3D assets in Dynamic Media](/help/assets/dynamic-media/assets-3d.md). -->

## Ondersteunde indelingen voor miniatuurvoorvertoning in Experience Manager{#supported-thumbnail-previewing-assets}

Experience Manager genereert standaard miniaturen voor de volgende bestandsindelingen:

| 3D-bestandsextensie | Bestandsindeling | MIME-type | Notities |
|---|---|---|---|
| GLB | Binaire GL-transmissie | model/gltf-binair |  |
| FBX | Autodesk FBX | application/octet-stream |  |
| OBJ | WaveFront 3D-objectbestand | application/x-tgif |  |
| 3DS | 3D Studio-model | application/x-3ds |  |
| USDz | Universele beschrijving van scène | model/vnd.usdz+zip |  |

## Ondersteunde indelingen voor interactieve 3D-voorvertoning in Experience Manager{#supported-3d-previewing-assets}

Experience Manager biedt native ondersteuning voor interactieve 3D-voorvertoningen voor de volgende bestandsindelingen:

| 3D-bestandsextensie | Bestandsindeling | MIME-type | Notities |
|---|---|---|---|
| GLB | Binaire GL-transmissie | model/gltf-binair |  |
| GLTF | GL-indeling voor verzending | model/gltf+json | Zie de **Nota** hieronder. |
| OBJ | WaveFront 3D-objectbestand | application/x-tgif |  |
| STL | Stereolithografie | application/vnd.ms-pki.stl |  |


>[!NOTE]
>
>Als materialen niet worden gerenderd in de voorvertoning van een gLTF-model, controleert u of ze op de juiste wijze zijn benoemd en zich in een `textures` -map in dezelfde hoofdmap als het model bevinden, vergelijkbaar met het volgende:

     Activa (omslag) 
     model.gltf 
     model.bin 
     texturen (omslag) 
     material_0_baseColor.jpeg 
     material_0_normal.jpeg 

## Prestatieaspecten wanneer u een voorvertoning van 3D-elementen weergeeft in Experience Manager{#performance-3d-previewing-assets}

De tijd die nodig is om een 3D-element te openen op de pagina met de elementdetails, is afhankelijk van verschillende factoren, zoals bandbreedte, de complexiteit van de afbeelding en de vertraging van de server.

Bovendien zijn de mogelijkheden van de clientcomputer - zoals een werkstation, laptop of mobiel aanraakapparaat - ook belangrijk om te overwegen wanneer u de camera interactief manipuleert. Een redelijk krachtig systeem met goede grafische mogelijkheden kan de interactieve 3D-kijkervaring vloeiender en gunstiger maken.

**aan voorproef 3D activa in Experience Manager:**

1. Zorg ervoor dat u 3D-elementen hebt geüpload naar Experience Manager.
Zie [&#x200B; Gesteunde formaten voor 3D voorproef &#x200B;](#supported-3d-previewing-assets) en [&#x200B; activa &#x200B;](/help/assets/manage-digital-assets.md#uploading-assets) uploaden.
1. Ga vanuit Experience Manager op de pagina **[!UICONTROL Navigation]** naar **[!UICONTROL Assets]** > **[!UICONTROL Files]** .

   ![&#x200B; pagina van de Navigatie &#x200B;](/help/assets/dynamic-media/assets/navigation-assets.png)

1. Selecteer in de rechterbovenhoek van de pagina in de vervolgkeuzelijst Weergave de optie **[!UICONTROL Card View]** en navigeer naar een 3D-element waarvan u een voorvertoning wilt weergeven.

   ![&#x200B; Selectie van de 3D kaart &#x200B;](/help/assets/dynamic-media/assets/3d-card-select.png)
   _in de Mening van de Kaart, selecteer de kaart van 3D activa u voorproef wilt._

1. Selecteer de kaart van het 3D-element.

   ![&#x200B; Interactieve 3D voorproef &#x200B;](/help/assets/dynamic-media/assets/3d-preview.png)
   _Interactieve voorproef van een 3D activa in de pagina van de de meningsmening van activadetails._
1. Voer een van de volgende handelingen uit op de pagina met de elementdetails voor het 3D-element:

   | Weergave | Beschrijving | Muishandeling | Handeling op het aanraakscherm |
   | --- | --- | --- | --- |
   | **draai uw camera** | Draai de weergave rond de 3D-scène en -objecten. | Klik met de linkermuisknop en sleep. | Druk met één vinger en sleep. |
   | **Pannen uw camera** | U kunt de weergave naar links, rechts, omhoog of omlaag pannen. | Klik met de rechtermuisknop en sleep. | Druk met twee vingers en sleep. |
   | **Gezoem uw camera** | Ga in en uit gebieden van de 3D-scène. | Schuifwiel. | Kneep met twee vingers. |
   | **herenter uw camera** | Voer de camera opnieuw in op een punt op een object in de 3D-scène. | Dubbelklik. | Dubbelselecteren. |
   | **Terugstellen** | Selecteer in de rechterbenedenhoek van de pagina het pictogram Herstellen om het doelpunt van de weergave te herstellen naar het midden van het 3D-element. Met Herstellen wordt de camera ook dichter bij of verder weg geplaatst om het middel volledig en bij een redelijke weergavegrootte weer te geven. |   |   |
   | **Volledige het schermwijze** | Als u de modus Volledig scherm wilt inschakelen, klikt u op het pictogram Volledig scherm rechtsonder op de pagina. |   |   |

1. Wanneer u klaar bent, selecteert u **[!UICONTROL Close]** in de rechterbovenhoek van de pagina.
