---
title: Wat is een scheidingscomponent in Adaptive Forms?
description: De scheidingscomponent in Adaptief Forms helpt om delen van een formulier visueel te scheiden.
uuid: f8d2aed3-52aa-437f-bfe3-0c8779e7986c
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
docset: aem65
source-git-commit: 7e3eb3426002408a90e08bee9c2a8b7a7bfebb61
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---


# Scheidingscomponent in Adaptieve Forms{#separator-component-in-adaptive-forms}

Met de scheidingscomponent kunt u deelvensters van een formulier visueel van elkaar scheiden. U kunt de algemene vormgeving en stijl van een scheidingscomponent definiëren door de volgende eigenschappen van de scheidingscomponent op te geven:

* **Elementnaam:** Specifies the name of the component. De SOM-expressies richten zich op de component met een waarde die is opgegeven in het veld Elementnaam.
* **Dikte:** Hiermee wordt de dikte van de scheidingscomponent in pixels opgegeven.

* **CSS-klasse:** Hiermee wordt de aangepaste CSS-klasse voor de scheidingscomponent opgegeven

* **Inline stijlen:** Met [!DNL AEM Forms]kunt u inline CSS-stijlen nu toepassen op afzonderlijke componenten van het adaptieve formulier en een voorvertoning van de wijzigingen weergeven in real-time.

U kunt de modus Lay-out gebruiken om het aantal kolommen te definiëren waaraan de scheidingscomponent zich uitstrekt. Zie voor meer informatie [Gebruik de modus Lay-out om het formaat van componenten te wijzigen](resize-using-layout-mode.md).

De eigenschappen van een scheidingscomponent opgeven:

1. Selecteer een scheidingscomponent en tik op ![cmppr](assets/cmppr.png). De eigenschappen worden geopend in het zijpaneel.
1. Klik op een tabblad in de sectie Inline CSS-eigenschappen zodat u CSS-eigenschappen kunt opgeven. Bijvoorbeeld a. Klik op het tabblad Veld op **Item toevoegen**. Er wordt een rij met twee velden toegevoegd.
1. Geef in het eerste veld links een CSS3-eigenschap op die u wilt toepassen. Bijvoorbeeld: **border**. U kunt een eigenschap ook selecteren door op de knop pijl-omlaag te klikken. De vervolgkeuzelijst is niet uitputtend en u kunt elke ondersteunde CSS3-eigenschapnaam opgeven in dit veld.
1. Geef in het aangrenzende veld een geldige waarde op voor de opgegeven CSS3-eigenschap. Bijvoorbeeld: **3 pixels effen zwart**.
1. Klikken **Item toevoegen** om een andere eigenschap en de bijbehorende waarde op te geven.
1. Klikken **Voorvertoning** zodat u de wijzigingen in het formulier kunt zien.
1. Voer een van de volgende handelingen uit:
   * Wijzigingen bevestigen door op **OK**
   * Sluit het dialoogvenster zonder wijzigingen door op **Annuleren**.

