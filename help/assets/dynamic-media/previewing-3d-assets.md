---
title: 3D-elementen voorvertonen
description: Leer hoe u een voorvertoning van 3D-elementen kunt weergeven
translation-type: tm+mt
source-git-commit: d84a6692f2d0aae496bd2bd98ac99c2663f3fe52
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 4%

---


# 3D-elementen voorvertonen in AEM{#previewing-3d-assets}

Adobe Experience Manager ondersteunt het uploaden, leveren en interactief voorvertonen van 3D-elementen als onderdeel van het ontwerpproces.

De interactieve 3D-viewer is beschikbaar op de pagina met elementdetails in AEM. De viewer bevat onder andere een verzameling interactieve besturingselementen voor camera waarmee u het 3D-element kunt draaien, zoomen en pannen.

<!-- See also [Working with 3D assets in Dynamic Media](/help/assets/dynamic-media/assets-3d.md). -->

## Ondersteunde indelingen voor 3D-voorvertoning in AEM{#supported-3d-previewing-assets}

Interactieve 3D-voorvertoning in AEM ondersteunt de volgende bestandsindelingen:

| 3D-bestandsextensie | Bestandsindeling | MIME-type | Opmerkingen |
|---|---|---|---|
| GLB | Binaire GL-transmissie | model/gltf-binair |  |
| GLTF | GL-indeling voor verzending | model/gltf+json | Zie **Opmerking** hieronder. |
| OBJ | WaveFront 3D-objectbestand | application/x-tgif |  |
| STL | Stereolithografie | application/vnd.ms-pki.stl |  |
| DN | Adobe Dimension | model/x-adobe-dn | Alleen ondersteuning voor inname; voorvertoning niet beschikbaar. |
| USDZ | Universal Scene Description Zip-archief | model/vnd.usdz+zip | Alleen ondersteuning voor inname; voorvertoning niet beschikbaar. |

**Opmerking**: Als materialen niet in voorproef van een gLTF model teruggeven, zorg ervoor zij behoorlijk worden genoemd en in een omslag in de zelfde wortelomslag zoals het model worden gevestigd, gelijkend op het volgende: `textures`

    Element (map)
    model.
    gltfmodel.
    bintextures (map)
    material_0_baseColor.
    jpegmaterial_0_normal.jpeg

## Prestatieaspecten wanneer u 3D-elementen in AEM bekijkt{#performance-3d-previewing-assets}

De tijd die nodig is om een 3D-element te openen op de pagina met de elementdetails, is afhankelijk van verschillende factoren, zoals bandbreedte, de complexiteit van de afbeelding en de vertraging van de server.

Bovendien zijn de mogelijkheden van de clientcomputer, zoals een werkstation, laptop of mobiel aanraakapparaat, ook belangrijk om te overwegen wanneer u de camera interactief manipuleert. Een redelijk krachtig systeem met goede grafische mogelijkheden kan de interactieve 3D-kijkervaring vloeiender en gunstiger maken.

**Een voorvertoning weergeven van 3D-elementen in AEM**

1. Zorg ervoor dat u 3D-elementen hebt geüpload naar AEM.
See [Supported formats for 3D preview](#supported-3d-previewing-assets) and [Uploading assets](/help/assets/manage-digital-assets.md#uploading-assets).
1. Tik vanaf AEM op de **[!UICONTROL Navigation]** pagina **[!UICONTROL Assets > Files]**.

   ![Navigatiepagina](/help/assets/dynamic-media/assets/navigation-assets.png)

1. Tik in de rechterbovenhoek van de pagina in de vervolgkeuzelijst Weergave op **[!UICONTROL Card View]** en ga naar een 3D-asset waarvan u een voorvertoning wilt weergeven.

   ![3D-kaart selecteren](/help/assets/dynamic-media/assets/3d-card-select.png)
   _Tik in de Kaartweergave op de kaart van het 3D-element waarvan u een voorvertoning wilt weergeven._

1. Tik op de kaart van het 3D-element om dit te openen in de weergavepagina voor elementdetails.

   ![Interactieve 3D-voorvertoning](/help/assets/dynamic-media/assets/3d-preview.png)
   _Interactieve voorvertoning van een 3D-element op de pagina met de elementdetails._
1. Voer een van de volgende handelingen uit op de pagina met de elementdetails voor het 3D-element:
   * **Draai uw camera**- Draai uw mening rond de 3D scène en de voorwerpen.
      * _Muis_: Klik met de linkermuisknop en sleep.
      * _Aanraakscherm_: Druk met één vinger en sleep.
   * **Pannen op uw camera**: pannen uw weergave naar links, rechts, omhoog of omlaag.
      * _Muis_: Klik met de rechtermuisknop en sleep.
      * _Aanraakscherm_: Druk met twee vingers en sleep.
   * **Zoom de camera** in en uit. Zoom de camera in en uit de gebieden van de 3D-scène.
      * _Muis_: Schuifwiel.
      * _Aanraakscherm_: Kneep met twee vingers.
   * **Start de camera** opnieuw op. Voer de camera opnieuw in op een punt op een object in de 3D-scène.
      * _Muis_: Dubbelklik.
      * _Aanraakscherm_: Dubbeltik.
   * **Herstellen**- Tik in de rechterbenedenhoek van de pagina op het pictogram Herstellen om het doelpunt van de weergave te herstellen naar het midden van het 3D-element. Met Herstellen wordt de camera ook dichter bij of verder weg geplaatst om het middel volledig en bij een redelijke weergavegrootte weer te geven.
   * **Modus** Volledig scherm - Tik op het pictogram Volledig scherm rechtsonder op de pagina om de modus Volledig scherm te activeren.

1. When you are finished, near the upper-right corner of the page, tap **[!UICONTROL Close]**.
