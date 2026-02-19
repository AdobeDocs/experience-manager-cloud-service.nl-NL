---
title: Aan de slag met de Editor voor interactieve communicatie (IC)
description: Met interactieve communicatie kunnen organisaties gepersonaliseerde, gegevensgestuurde communicatie ontwerpen en leveren.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
exl-id: b30b3634-0457-4c29-84d3-78f1429b98d1
source-git-commit: cdaceaabb8eeeec931b1897e1161f408606540b9
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 0%

---

# Aan de slag met de Editor voor interactieve communicatie (IC)

>[!NOTE]
>
> De interactieve communicatiecapaciteit is beschikbaar in het kader van het programma voor vroegtijdige adoptie. Verzend een e-mail van uw werkadres naar `aem-forms-ea@adobe.com` om toegang aan te vragen.

De **Interactieve Communicatie (IC) Redacteur** in Adobe Experience Manager (AEM) Forms staat organisaties toe om gepersonaliseerde, gegeven-gedreven mededelingen zoals verklaringen, facturen, en brieven over digitale en drukkanalen te ontwerpen en te leveren. Deze gids verstrekt een overzicht van hoe te beginnen - van aan boord gaan tot het navigeren van de interface van de Redacteur IC.


## Toegang en toegang aan boord

### Toegangsvereisten

Om Interactieve Communicatie te gebruiken, verzeker uw milieu van AEM Forms as a Cloud Service **toe:voegen-op AEM Forms** omvat en dat uw rekening de aangewezen toestemmingen heeft.

### Browser verifiëren

Om gesteunde browsers en cliëntplatforms te kennen, volg het verbonden artikel, [&#x200B; Gesteunde Platforms van de Cliënt &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/overview/supported-platforms)

>[!NOTE]
>
> **Steun voor browsers met snelle versiecycli:**
> De release van Firefox, Chrome en Edge wordt regelmatig bijgewerkt. Adobe streeft ernaar het supportniveau dat hierboven voor toekomstige versies van deze browsers wordt vermeld, te handhaven.

### Gebruikersrollen en -machtigingen configureren

De toegang tot eigenschappen van de Redacteur van IC wordt geregeerd door [&#x200B; gebruikersrollen binnen AEM &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions). Hieronder worden de sleutelfuncties beschreven die bij het maken en beheren van interactieve communicatie betrokken zijn:

| **Rol** | **Beschrijving** | **Zeer belangrijke Toestemmingen** |
| --------------------- | ---------------------------------------------------------- | -------------------------------------------- |
| **Auteur van de Vorm** | Creeert en geeft Interactieve Mededelingen uit. | IC&#39;s maken, bewerken, voorvertonen en publiceren. |
| **Auteur van het Malplaatje** | Ontwerpen herbruikbare malplaatjes voor Interactieve Mededelingen. | Sjablonen maken en vergrendelen, lay-outs definiëren. |
| **Beheerder** | Beheert gebruikerstoegang, machtigingen en configuraties. | Rollen toewijzen, sjablonen beheren, IC&#39;s publiceren. |
| **FDM Auteur** | [&#x200B; creeert en beheert de Modellen van de Gegevens van de Vorm (FDM) &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/create-form-data-models) voor gegevensintegratie. | Creeer, geef, en vorm gegevensbronnen en modellen uit. |

>[!NOTE]
>
> Zorg ervoor dat gebruikers deel uitmaken van de juiste AEM-groepen (bijvoorbeeld `forms-user` , `fdm-author` , `template-authors` ) om toegang te krijgen tot de bijbehorende functies.

## Toegang krijgen tot de IC-editor

1. Login aan uw **AEM Forms as a Cloud Service** instantie.
2. Navigeer aan **Forms > Interactieve Mededelingen**.
3. Klik **creëren** → **Interactieve Mededeling**.
4. Kies a **Malplaatje**, vorm gegevensbronnen, en klik **creeer** om de **Interactieve Communicatie Redacteur** te openen.

De redacteur verstrekt een verenigde milieu aan ontwerp, voorproef, en beheer zowel druk als Webversies van mededelingen.

## Navigeren door de interface

De **Interactieve Communicatie interface van de Redacteur** wordt ontworpen om auteurs intuïtieve toegang tot alle ontwerphulpmiddelen en configuratieopties te verlenen.

![&#x200B; vind IC Docu &#x200B;](/help/forms/interactive-communication/assets/navigate-the-interface.png)

### &#x200B;1. Werkbalk boven

![&#x200B; vind IC Docu &#x200B;](/help/forms/interactive-communication/assets/tool-bar.png)

**Plaats:** Bovenste sectie

**Doel:** verleent milieutoegang en globale acties.

**omvat:**

Toont het **milieu van Adobe Experience Cloud** (b.v., het Opvoeren), samen met de **projecttitel**, **Beta terugkoppelt**, **berichten**, en **profielcontroles** voor het beheren van gebruikersmontages en milieutoegang.

### &#x200B;2. Tabbalk (tabbladen ontwerp/stramien en Besturingselementen voor bestanden)

![&#x200B; vind IC Docu &#x200B;](/help/forms/interactive-communication/assets/tab-bar.png)

**Plaats:** onder de hoogste kopbal

**Doel:** beheer meningen en communicatie dossiers.

**omvat:**

**Lusjes:** Schakelaar tussen **Mening van het Ontwerp** en **Hoofdpaginamening** voor lay-out en herbruikbaar elementontwerp

**Naam van het Dossier:** toont de titel van de huidige mededeling (b.v., ic-11)

**Controles van de Mening:** Opties zoals regel, verwezenlijking, Gezoem (85%), Ongedaan maken/Opnieuw, Schrapping, de Voorproef van PDF, en sparen

### &#x200B;3. Linkerpaneel (navigatie- en componentgereedschappen)

![&#x200B; vind IC Docu &#x200B;](/help/forms/interactive-communication/assets/left-panel.png)

**Plaats:** linkerkant van de interface

**Doel:** de projectstructuur van de Toegang, herbruikbare activa, en gegevensbindingen.

**omvat:**

* **Homepage van het Huis:** neemt de gebruiker aan het belangrijkste Interactieve Communicatie (IC) homescherm, waar u bestaande ICs en omslagen kunt bekijken en beheren.

* **Comité van het Menu:** vertoningen mening-verwante opties zoals Linialen, de Grenzen van Objecten, Breuk aan Net, Breuk aan de Objecten van de Eigenschap, en de Invoer XDP eigenschap.

* **de Mening van de Hiërarchie:** toont de componentenstructuur van de mededeling, die de organisatie van pagina&#39;s, panelen, en subforms toont.

* **Bibliotheek van de Component:** bevat ontwerpelementen zoals Tekst, Beeld, Subform, en Streepjescode die op het canvas kunnen worden gesleept.

* **Fragments:** laat hergebruik van vooraf bepaald ontwerp en inhoudsblokken over veelvoudige mededelingen toe.

* **Model van Gegevens:** verbindt de mededeling met de onderliggende Modellen van de Gegevens van de Vorm (FDM) voor het binden van dynamische gegevens.

### &#x200B;4. Midden-Workspace (ontwerpcanvas)

![&#x200B; vind IC Docu &#x200B;](/help/forms/interactive-communication/assets/canvas.png)

**Plaats:** Centrum van de interface

**Doel:** Primaire werkruimte voor het ontwerpen van Interactieve Mededelingen.

**Eigenschappen:**

* Componenten slepen en neerzetten vanuit de bibliotheek

* Visuele lay-out rangschikken en opmaken

* Pagina&#39;s, subformulieren en velden toevoegen of bewerken

* Navigeren tussen pagina&#39;s (bijvoorbeeld &quot;1 van 1&quot;) met besturingselementen linksonder

* De uiteindelijke lay-out voorvertonen voordat u de publicatie uitvoert

### &#x200B;5. Rechterdeelvenster (deelvenster Eigenschappen)

![&#x200B; vind IC Docu &#x200B;](/help/forms/interactive-communication/assets/right-panel.png)

**Plaats:** Juiste kant van het scherm

**Doel:** pas componentengedrag en stijl aan.

**omvat:**

* Algemene instellingen (Naam, Type, Overlopen/Geplaatst)

* Opties voor lay-out en weergave

* Besturingselementen voor paginering, positie, aanwezigheid en gegevensbinding
