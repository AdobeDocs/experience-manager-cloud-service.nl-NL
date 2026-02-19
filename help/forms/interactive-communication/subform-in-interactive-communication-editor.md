---
title: Subformulier in interactieve communicatie-editor
description: Met subformulier in de interactieve communicatie-editor kunt u lay-outs beheren, objecten positioneren en definiëren hoe inhoud over pagina's loopt.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
hide: true
index: false
hidefromtoc: true
source-git-commit: cdaceaabb8eeeec931b1897e1161f408606540b9
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---


# Subformulier in interactieve communicatie-editor

>[!NOTE]
>
> De interactieve communicatiecapaciteit is beschikbaar in het kader van het programma voor vroegtijdige adoptie. Verzend een e-mail van uw werkadres naar `aem-forms-ea@adobe.com` om toegang aan te vragen.

## &#x200B;1. Inleiding

Een subformulier in de interactieve communicatie-editor is een containerobject dat wordt gebruikt om velden, objecten en componenten te groeperen in een logische sectie. Het helpt lay-outs beheren, objecten plaatsen controleren, en bepalen hoe de inhoud over pagina&#39;s stroomt. Subformulieren zijn van essentieel belang voor het maken van gestructureerde, herbruikbare en responsieve communicatie, vooral wanneer u werkt met dynamische of herhaalde inhoud.

Door subformulieren te gebruiken, kunnen auteurs consistentie handhaven, paginering beheren, en volledige secties binden aan gestructureerde gegevensbronnen.

## &#x200B;2. Eigenschappen

2.1 Formulierontwerpindelingen

- **Vaste Lay-out:** de voorwerpen handhaven nauwkeurige posities op de pagina. Het beste voor statische ontwerpen waarvoor nauwkeurige plaatsing is vereist (bv. facturen of officiële letters).

- **Stroombare Lay-out:** de voorwerpen passen dynamisch gebaseerd op inhoudslengte en het schermgrootte aan. Geschikt voor communicatie die responsief ontwerp of variërende gegevenslengten vereisen.

2.2 Plaatsing subformulier

- **Paginering:** controleer hoe subforms over pagina&#39;s breken. U kunt onder andere subformulieren bijeenhouden of pagina-einden in subformulieren toestaan.

- **Positie:** specificeer of subform met betrekking tot zijn oudercontainer of stromen natuurlijk binnen de lay-out wordt geplaatst.

- **Vormgeving:** bepaal achtergrond, grenzen, en het stileren voor het subformulier om inhoud visueel te scheiden.

- **Aanwezigheid:** vorm zicht montages-Zichtbaar, Verborgen, of Voorwaardelijk-afhankelijk van bedrijfsregels of gegevenswaarden.

2.3 Gegevensbinding

- Subforms kunnen rechtstreeks aan **Model van de Gegevens van de Vorm (FDM)** knopen of series worden gebonden.

- Met binding kan het subformulier dynamisch worden herhaald voor elke record in een verzameling (bijvoorbeeld meerdere beleidsregels, transacties of adressen).

- Ondersteunt zowel de statische als de dynamische populatie van inhoud op basis van de gegevensstructuur.

## &#x200B;3. Gebruik

Subformulieren worden veel gebruikt voor:

- Documenten structureren in secties zoals koptekst, tekst en voettekst.

- Herhalende inhoud zoals tabellen, gespecificeerde rekeningen, of lijsten van beleid.

- Het beheren van paginering blijft dus gegroepeerde inhoud bij elkaar.

- Voorwaardelijke weergave van secties op basis van regels of gegevenswaarden.

- Het toepassen van (vaste of stroombare) lay-outcontrole afhankelijk van het communicatie type.

Auteurs kunnen een subformulier van de Objectbibliotheek naar het canvas slepen en de indeling, positie en binding ervan aanpassen vanuit het deelvenster Eigenschappen.

## &#x200B;4. Beste praktijken

- **kies wijs lay-out:** gebruik vaste lay-out voor vormen die nauwkeurige plaatsing, en stroombare lay-out voor dynamische, gegeven-gedreven mededelingen vereisen.

- **Bind inzamelingen zorgvuldig:** voor lijsten of series, bindt subforms direct aan inzamelingen FDM met malplaatjerijen.

- **optimaliseer paginering:** voorkom ongemakkelijke onderbrekingen door verwante voorwerpen in een subform te groeperen.

- **Voorwaardelijke aanwezigheid van het Gebruik:** verberg of toon dynamisch subforms die op gegevenswaarden worden gebaseerd.

- **handhaaf hiërarchie:** nesten subforms logisch om complexe lay-outs gemakkelijker te maken te beheren.

- **Test met gevarieerde gegevens:** Voorproef met korte, lange, en lege datasets om het ontwerp te verzekeren past correct aan.

Door subformulieren effectief te benutten, kunnen auteurs schonere layouts, betere controle over dynamische inhoud krijgen en ervoor zorgen dat de communicatie naadloos wordt aangepast aan zowel gegevensgestuurde als statische scenario&#39;s.
