---
title: Hoe wordt AFP-API voor uitvoersynchronisatie gebruikt?
description: Leer hoe u de AFP Output Sync API gebruikt om uitvoeruitvoeruitvoeruitvoeruitvoeringen op te halen en te synchroniseren.
feature: Adaptive Forms, APIs & Integrations, Document Services
role: Admin, User
exl-id: 5602fc63-ef74-44eb-b3be-61b8f8a2795a
source-git-commit: 03e46bb43e684a6b7057045cf298f40f9f1fe622
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---

# AFP-uitvoer genereren met de AEM Forms API

<span class="preview"> Dit is een pre-versieeigenschap en toegankelijk door ons [ pre-vrijgavekanaal ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html#new-features). </span>

Advanced Function Presentation (AFP) is een krachtige documentindeling die voornamelijk voor afdrukdoeleinden is ontworpen.\
In deze handleiding worden alle stappen en configuraties beschreven die nodig zijn om AFP-uitvoer met AEM Forms te genereren.

<!--
## Prerequisites

To support AFP output generation, the following OSGi bundles must be present and in an **active** state:

* **AFP Core Bundle** – Available in the AFP repository
* **Forms Output Core** – Found in the Forms Output comments package
* **Bedrock Connector** – Provided by the Forms Output API
* **Cloud Ready Implementation** – Available through the Forms installer

>[!NOTE]
>
> * If any bundle is inactive, resolve dependency issues or reinstall manually.
> * To enable AFP generation, the `FT_FORMS-17887` toggle configurations must be set in AEM configuration manager.-->

## AFP Generation-API

Genereert een AFP-bestand (Advanced Function Presentation) met een XDP-sjabloon en invoergegevens.

### Toestemming

U kunt of **BasicAuth** gebruiken (geloofsbrieven Admin) voor lokale milieu&#39;s of **&#x200B;**&#x200B;vergunning BeveelAuth voor de instanties van de Wolk van AEM.

### Verzoek

**Eindpunt:**
`POST http://<server>:<port>/adobe/forms/document/generate/afp`

### Kopteksten

| Sleutel | Waarde |
| --------------- | ------------------------------------------------------ |
| `Content-Type` | `application/pdf` |
| `Authorization` | `(Bearer Access token)` |

### Indieningsinstantie

**inhoud-Type: multipart/form-data**

| Sleutel | Type | Vereist | Beschrijving |
| ---------- | ---- | -------- | ------------------------------------------------------------------------- |
| `template` | Bestand/tekst | Ja | XDP-bestand gebruikt als sjabloon voor AFP genereren (bijvoorbeeld `demo.xdp`) |
| `data` | Bestand/tekst | Nee | Gegevensbestand (XML of JSON) dat met de sjabloon moet worden samengevoegd (bijvoorbeeld `data.xml`) |
| `options` | Tekst | Nee | JSON-tekenreeks met opties voor het besturen van AFP-uitvoer (bijvoorbeeld resolutie, landinstelling) |

**Voorbeeld `options` JSON (het gebied van de Tekst):**

```json
{
  "pdfVersion": "1.7",
  "resolution": 300,
  "locale": "en-US",
  "embedFonts": true,
  "contentRoot": "/usr/tmp"
}
```

### Reacties

| Code | Beschrijving |
| ----- | ------------------------------------------------------------------------- |
| `200` | Bewerking gelukt. Retourneert de AFP-documentstroom. |
| `400` | Onjuist verzoek. De payload van de aanvraag is onjuist geformuleerd of er ontbreken vereiste velden. |
| `500` | Interne serverfout. Probeer het later opnieuw. |

### Krullen, opdracht

```
curl --location 'http://<server>:<port>/adobe/forms/document/generate/afp' \
--header 'Authorization: Bearertoken <base64-encoded-credentials>' \
--form 'template=@"<path-to-template>.xdp"' \
--form 'data=@"<path-to-data-file>.xml"' \
--form 'options=<JSON-options-string>'
```

### API testen

U kunt het .yaml-bestand downloaden en uploaden naar Postman om de functionaliteit van de API&#39;s te controleren.

![ AFP Postman beeld ](/help/forms/assets/afp-postman.png)

U kunt het antwoord opslaan en het opgeslagen bestand openen in de AFP-lezer om het weer te geven.

![ de lezer van PDF ](/help/forms/assets/afp-pdf.png)
