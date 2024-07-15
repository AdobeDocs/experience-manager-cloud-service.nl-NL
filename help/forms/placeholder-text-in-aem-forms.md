---
title: Hoe kunt u plaatsaanduidingstekst toevoegen aan formuliervelden?
description: Plaatsaanduidingstekst is bedoeld om de gebruiker te helpen bij het invoeren van gegevens wanneer het besturingselement geen waarde heeft. Dit kan een samplewaarde of een korte beschrijving van de verwachte indeling zijn.
source-git-commit: d33c7278d16a8cce76c87b606ca09aa91f1c3563
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---


# Plaatsaanduidingstekst in [!DNL AEM Forms] {#placeholder-text-in-aem-forms}

De plaatsaanduidingstekst vertegenwoordigt een woord of korte woordgroep. Het is bedoeld om de gebruiker van gegevensingang te helpen wanneer de controle geen waarde heeft. Een plaatsaanduidingstekst kan een voorbeeldwaarde of een korte beschrijving van de verwachte indeling zijn. De tekst van de plaatsaanduiding wordt weergegeven voordat de gebruiker een waarde invoert. De tekst wordt verwijderd wanneer de gebruiker een waarde invoert of selecteert.

>[!NOTE]
>
>De plaatsaanduidingstekst moet, indien opgegeven, een waarde hebben die geen nieuwe regeltekens bevat.

![ component van de Datum met en zonder placeholder tekst ](assets/dat-picker-place-holder-text.png)

**A.** component van de Datum met placeholder tekst **B.** component van de Datum zonder placeholder tekst

[!DNL AEM Forms] biedt ondersteuning voor plaatsaanduidingstekst voor de velden Wachtwoord, Datumkiezer, Numeriek vak en Tekstvak.\
Plaatsaanduidingsteksten worden niet ondersteund voor de native HTML5-datumwidget. Een plaatsaanduidingstekst opgeven:

1. Klik met de rechtermuisknop op een component die Plaatsaanduidingstekst ondersteunt en klik op **Bewerken** . Het dialoogvenster Component bewerken wordt geopend.

1. Open de **Titel en tekst** tabel.
1. Specificeer een woord of een korte uitdrukking in het **Placeholder tekstvakje**. Klik **OK**.

>[!NOTE]
>
>Plaatsaanduidingstekst wordt niet ondersteund in [!DNL Microsoft Internet Explorer 9] .

