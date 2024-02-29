---
title: Een AEM Forms-formulier voor Edge Delivery Services publiceren
description: Een AEM Forms-formulier voor Edge Delivery Services publiceren
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: 3b24d0cd4099e0b8eb48c977f460b25c168af220
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---


# Uw formulier publiceren

Als u klaar bent om uw formulier met uw klanten te delen voor gegevensverzameling of verzending, kunt u het gewoon publiceren, zodat het formulier direct beschikbaar is voor uw klanten.

## Voorwaarden

* De [Formulierblok is ingeschakeld voor uw EDS-project op Github](/help/edge/docs/forms/create-forms.md).
* Uw formulier is volledig getest en klaar voor gebruik.
* Uw [spreadsheet is geconfigureerd](/help/edge/docs/forms/submit-forms.md) om gegevens te accepteren.

## Uw formulier publiceren

Het formulier publiceren:

1. Open uw Microsoft SharePoint- of Google Drive-account en navigeer naar uw `[AEM Edge Delivery project directory]`.

1. Open een documentbestand waarin u het formulier wilt insluiten. U kunt bijvoorbeeld het indexbestand openen of een nieuw document maken.

1. Bepaal de gewenste sectie in het document waar u het formulier wilt invoegen en navigeer naar de gewenste sectie.

1. Voeg een blok met de naam &#39;Form&#39; toe aan het bestand, vergelijkbaar met het onderstaande voorbeeld:

   | Formulier |
   |---|
   | [https://main—portal—wkndforms.hlx.live/inquiry.json](https://main--portal--wkndforms.hlx.live/enquiry.json) |

   Dit blok fungeert als tijdelijke aanduiding voor het ingesloten formulier. Voeg in de tweede rij van het blok de URL van de `<form>.json` bestand als hyperlink.

   >[!IMPORTANT]
   >
   >
   > Zorg ervoor dat de URL is opgemaakt als een hyperlink en niet wordt weergegeven als onbewerkte tekst.

   Gebruik de URL van de voorvertoning (.page URL) voor ontwikkelings- of testdoeleinden of de URL van de publicatie (.live) voor productiedoeleinden. Hier volgen enkele voorbeelden van URL&#39;s voor voorvertonen en publiceren:

   **Voorbeeld-URL**
| Formulier | |—| | [https://main—portal—wkndforms.hlx.page/inquiry.json](https://main--portal--wkndforms.hlx.page/enquiry.json)  |


   **URL publiceren**
| Formulier | |—| | [https://main—portal—wkndforms.hlx.live/inquiry.json](https://main--portal--wkndforms.hlx.live/enquiry.json)  |

1. Gebruiken [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) om de pagina voor te vertonen. Het formulier wordt nu weergegeven op de pagina. Hier ziet u bijvoorbeeld het formulier dat is gebaseerd op de [spreadsheet vragen](https://docs.google.com/spreadsheets/d/196lukD028RDK_evBelkOonPxC7w0l_IiJ-Yx3DvMfNk/edit#gid=0):


   [![Een voorbeeld-EDS-formulier](/help/edge/assets/eds-form.png)](https://main--portal--wkndforms.hlx.live/)

   Uw klanten kunnen het formulier nu invullen en verzenden.

## Problemen oplossen

+++ Kan gegevens niet naar formulier verzenden

Als er een fout optreedt die lijkt op het volgende bericht, geeft dit aan dat het spreadsheet nog niet is geconfigureerd voor het accepteren van de verzonden gegevens.

![fout bij het verzenden van formulier](/help/edge/assets/form-error.png)

+++


## Meer weergeven

* [Een formulier maken en een voorbeeld ervan bekijken](/help/edge/docs/forms/create-forms.md)
* [Formulier verzenden van gegevens inschakelen](/help/edge/docs/forms/submit-forms.md)
* [Een formulier publiceren naar sitepagina](/help/edge/docs/forms/publish-eds-forms.md)
* [Validaties toevoegen aan formuliervelden](/help/edge/docs/forms/validate-forms.md)
* [Thema&#39;s en vormstijl wijzigen](/help/edge/docs/forms/style-theme-forms.md)