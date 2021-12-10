---
title: 'Plaatsaanduidingstekst in [!DNL AEM Forms] '
description: Plaatsaanduidingstekst is bedoeld om de gebruiker te helpen bij het invoeren van gegevens wanneer het besturingselement geen waarde heeft. Dit kan een samplewaarde of een korte beschrijving van de verwachte indeling zijn.
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---


# Plaatsaanduidingstekst in [!DNL AEM Forms] {#placeholder-text-in-aem-forms}

De plaatsaanduidingstekst vertegenwoordigt een woord of korte woordgroep. Het is bedoeld om de gebruiker van gegevensingang te helpen wanneer de controle geen waarde heeft. Een plaatsaanduidingstekst kan een voorbeeldwaarde of een korte beschrijving van de verwachte indeling zijn. De tekst van de plaatsaanduiding wordt weergegeven voordat de gebruiker een waarde invoert. De tekst wordt verwijderd wanneer de gebruiker een waarde invoert of selecteert.

>[!NOTE]
>
>De plaatsaanduidingstekst moet, indien opgegeven, een waarde hebben die geen nieuwe regeltekens bevat.

![Datumcomponent met en zonder plaatsaanduidingstekst](assets/dat-picker-place-holder-text.png)

**A.** De component van de datum met placeholder tekst **B.** Datumcomponent zonder plaatsaanduidingstekst

[!DNL AEM Forms] ondersteuning voor plaatsaanduidingstekst voor de velden Wachtwoord, Datumkiezer, Numeriek vak en Tekstvak.\
Plaatsaanduidingsteksten worden niet ondersteund voor de native HTML5-datumwidget. Een plaatsaanduidingstekst opgeven:

1. Klik met de rechtermuisknop op een component die plaatsaanduidingstekst ondersteunt en klik op **Bewerken**. Het dialoogvenster Component bewerken wordt geopend.

1. Open de **Titel en tekst** tab.
1. Geef een woord of korte woordgroep op in het dialoogvenster **Tekstvak voor plaatsaanduiding**. Klikken **OK**.

>[!NOTE]
>
>Plaatsaanduidingstekst wordt niet ondersteund op [!DNL Microsoft Internet Explorer 9].

