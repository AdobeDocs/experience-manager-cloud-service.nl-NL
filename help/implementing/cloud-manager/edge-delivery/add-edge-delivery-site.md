---
title: Een Edge Delivery-site toevoegen aan Cloud Manager
description: Leer hoe u een Edge Delivery-site toevoegt aan uw productieprogramma of sandboxprogramma.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: c952e69aa637b30abec4deba0e643b4287d84330
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---


# Een Edge Delivery-site toevoegen aan Cloud Manager {#adding}

U kunt een Edge Delivery-site toevoegen aan uw productieprogramma of sandboxprogramma.

Het toevoegen van een plaats van Edge Delivery aan Cloud Manager wordt vereist om [ een steunkaartje voor uw project van Edge Delivery ](/help/edge/overview.md##support-ticket) te registreren.

Zie ook [ Inleiding aan Edge Delivery Services in Cloud Manager ](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md).

**om een plaats van Edge Delivery aan Cloud Manager toe te voegen:**

1. Meld u aan bij Cloud Manager op [`https://my.cloudmanager.adobe.com` ](https://my.cloudmanager.adobe.com/) en selecteer het gewenste programma.
1. Voer een van de volgende handelingen uit:

   * Van de **pagina van het Overzicht van het Programma**, klik **Edge Delivery** tabel. Dan, dichtbij de laag-juiste hoek van de pagina, klik **toevoegen de plaats van Edge Delivery**.

     ![ voeg de plaats van Edge Delivery van het lusje van Edge Delivery toe ](/help/implementing/cloud-manager/assets/cm-eds-add1.png)

   * Klik in de linkerbovenhoek van de pagina op het hamburgerpictogram om het linkernavigatiemenu weer te geven. Onder de **rubriek van de Diensten**, klik **de Plaatsen van Edge Delivery**. Vlak de hoger-juiste hoek van de pagina, klik **plaats** toevoegen.

     ![ voeg de plaats van Edge Delivery van de knoop van Plaatsen van Edge Delivery toe ](/help/implementing/cloud-manager/assets/cm-eds-add2.png)

1. In **voeg de plaats van Edge Delivery** dialoogdoos toe, verstrek de volgende informatie op de vereiste gebieden:

   | Tekstveld | Te verstrekken gegevens |
   | --- | --- |
   | Sitenaam | Voer de naam in van de Edge Delivery-site die u toevoegt. De naam fungeert als een unieke id voor de site in Cloud Manager. |
   | URL opslagplaats | Dit veld verwijst naar de Git-opslagplaats waar de code van uw website is opgeslagen. Met dit veld kan Cloud Manager tijdens het implementatieproces de code uit die opslagplaats ophalen. |
   | Sitebeschrijving (optioneel) | Voer een korte beschrijving in van de Edge Delivery-site die u toevoegt. Deze beschrijving helpt de site te identificeren en te onderscheiden, waardoor het eenvoudiger wordt om andere toegevoegde sites te beheren en te herkennen. |

1. In de laag-juiste hoek van de dialoogdoos, voegt de klik **** toe.

1. Het **verifieert de bezit van de bewaarplaats** dialoogvakje opent. Voer de volgende stappen uit terwijl deze is geopend:

   1. Voeg een dossier met de weg en de naam `well-known/adobe/cloudmanager-challenge.txt` aan de `main` tak van de bewaarplaats van het Git toe die in het **Repository URL** gebied wordt vermeld.
      * Indien nodig, klik het **pictogram van het Exemplaar** om de weg aan het klembord te kopiëren.
      * Voeg *niet* een periode bij het begin van de plaatsweg toe.
   1. Voeg de code van de **Stap&amp;amp toe;num; 1** gebied aan het dossier dat u in de vorige stap creeerde.
      * Indien nodig, klik het **pictogram van het Exemplaar** om de code aan het klembord te kopiëren.
   1. Maak in de Git-opslagplaats een pull-aanvraag voor de zojuist gemaakte wijzigingen en voeg deze vervolgens samen tot `main` .

1. Klik **verifieer**.

Nadat de opslagplaats is geverifieerd, verandert de status in de tabel Edge Deliver Sites in een groene cirkel met daarin een wit vinkje.
