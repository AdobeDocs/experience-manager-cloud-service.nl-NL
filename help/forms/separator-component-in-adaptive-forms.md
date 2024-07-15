---
title: Wat is een scheidingscomponent in Adaptive Forms?
description: De scheidingscomponent in Adaptief Forms helpt om delen van een formulier visueel te scheiden.
uuid: f8d2aed3-52aa-437f-bfe3-0c8779e7986c
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
docset: aem65
source-git-commit: 2d4ffd5518d671a55e45a1ab6f1fc41ac021fd80
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---


# Scheidingscomponent in Adaptieve Forms{#separator-component-in-adaptive-forms}

Met de scheidingscomponent kunt u deelvensters van een formulier visueel van elkaar scheiden. U kunt de algemene vormgeving en stijl van een scheidingscomponent definiëren door de volgende eigenschappen van de scheidingscomponent op te geven:

* **Naam van het Element:** specificeert de naam van de component. De SOM-expressies richten zich op de component met een waarde die is opgegeven in het veld Elementnaam.
* **Dikte:** specificeert de dikte van de separatorcomponent in pixel.

* **CSS Klasse:** specificeert de douaneCSS klasse voor de separatorcomponent

* **Gealigneerde stijlen:** met [!DNL AEM Forms], kunt u gealigneerde CSS stijlen nu toepassen op individuele Aangepaste componenten van de Vorm en voorproef de veranderingen in real time.

U kunt de modus Lay-out gebruiken om het aantal kolommen te definiëren waaraan de scheidingscomponent zich uitstrekt. Voor meer informatie, zie {de wijze van de Lay-out van het 0} Gebruik om componenten ](resize-using-layout-mode.md) te resize.[

De eigenschappen van een scheidingscomponent opgeven:

1. Selecteer een separatorcomponent en selecteer ![ cmp ](assets/cmppr.png). De eigenschappen worden geopend in het zijpaneel.
1. Klik op een tabblad in de sectie Inline CSS-eigenschappen zodat u CSS-eigenschappen kunt opgeven. Bijvoorbeeld a. Op het lusje van het Gebied, klik **Punt** toevoegen. Er wordt een rij met twee velden toegevoegd.
1. Geef in het eerste veld links een CSS3-eigenschap op die u wilt toepassen. Bijvoorbeeld, **grens**. U kunt een eigenschap ook selecteren door op de knop pijl-omlaag te klikken. De vervolgkeuzelijst is niet uitputtend en u kunt elke ondersteunde CSS3-eigenschapnaam opgeven in dit veld.
1. Geef in het aangrenzende veld een geldige waarde op voor de opgegeven CSS3-eigenschap. Bijvoorbeeld, **3 pixel stevige zwarte**.
1. Klik **toevoegen Punt** om een ander bezit en zijn waarde te specificeren.
1. Klik **Voorproef** zodat kunt u de veranderingen in de vorm zien.
1. Voer een van de volgende handelingen uit:
   * Bevestig de veranderingen door **O.K.** te klikken
   * Sluit de dialoogdoos zonder enige veranderingen door **te klikken annuleert**.

