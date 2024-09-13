---
title: Een Edge Delivery-site toevoegen aan Cloud Manager
description: Leer hoe u een Edge Delivery-site toevoegt aan uw productieprogramma of sandboxprogramma.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: b222b4384b1c2a21ecbb244d149ce7e51cc7990f
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 0%

---


## Een Edge Delivery-site toevoegen aan Cloud Manager {#eds-add-site}

Nadat u Edge Delivery Services aan een productieprogramma hebt toegevoegd, wordt uw licentie voor Edge Delivery Services erop toegepast.

Een klikbaar lusje genoemd **Edge Delivery** wordt gezien op de pagina van het Overzicht. Als u op het tabblad klikt, wordt een tabel weergegeven met elke Edge Delivery-site die u hebt toegevoegd. In het linkernavigatievenster, onder de **Diensten** groepering, merk de menuoptie genoemd **de Plaatsen van Edge Delivery** op.

![ pagina van het Overzicht die de Plaatsen van Edge Delivery in linkernavigatievenster en het lusje van Edge Delivery rechts van het lusje van de Levering van Publish tonen ](/help/implementing/cloud-manager/assets/cm-overview-eds.png)

**om een plaats van Edge Delivery aan Cloud Manager toe te voegen:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer het aangewezen programma.
1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma met gevormde Edge Delivery Services, waar u een plaats van Edge Delivery wilt toevoegen.
1. Voer een van de volgende handelingen uit:
   * Van de **pagina van het Overzicht van het Programma**, klik **Edge Delivery** tabel. Dan, dichtbij de laag-juiste hoek van de pagina, klik **toevoegen de plaats van Edge Delivery**.

     ![ voeg de Plaats van Edge Delivery van het lusje van Edge Delivery toe ](/help/implementing/cloud-manager/assets/cm-eds-add1.png)

     De **Edge Delivery om lijst**, zoals die in het beeld hierboven wordt gezien te doen, is een facultatieve controlelijstgids aan boord die wordt bedoeld om u te helpen met het gebruiken van Edge Delivery beginnen. Zie [ Ongeveer Edge Delivery lijst ](#ed-todo-list) te doen.

   * Klik in de linkerbovenhoek van de pagina op het hamburgerpictogram om het linkernavigatiemenu weer te geven. Onder de **rubriek van de Diensten**, klik **de Plaatsen van Edge Delivery**. Vlak de hoger-juiste hoek van de pagina, klik **plaats** toevoegen.

     ![ voeg de Plaats van Edge Delivery van de knoop van Plaatsen van Edge Delivery toe ](/help/implementing/cloud-manager/assets/cm-eds-add2.png)

1. In **voeg de plaats van Edge Delivery** dialoogdoos toe, doe het volgende:

   | Tekstveld | Wat moet u doen? |
   | --- | --- |
   | Sitenaam | Voer de naam in van de Edge Delivery-site die u toevoegt. De naam fungeert als een unieke id voor de site in Cloud Manager. |
   | URL opslagplaats | Dit veld verwijst naar de Git-opslagplaats waar de code van uw website is opgeslagen.<br> ga URL van de bewaarplaats van het Git in die de noodzakelijke dossiers en middelen (zoals HTML, CSS, JavaScript, en andere Webactiva) voor uw plaats van Edge Delivery bevat. Op deze manier kan Cloud Manager tijdens het implementatieproces de code uit die opslagplaats ophalen. |
   | Sitebeschrijving (optioneel) | Voer een korte beschrijving in van de Edge Delivery-site die u toevoegt.<br> Deze beschrijving helpt om de plaats te identificeren en te onderscheiden, die het gemakkelijker maken om onder andere plaatsen te beheren en te erkennen u hebt toegevoegd. U kunt desgewenst details opnemen over het doel, de inhoud of andere relevante informatie van de site die de functie of het bereik van de site kan verduidelijken. |

1. In de laag-juiste hoek van de dialoogdoos, voegt de klik **** toe.

1. In **verifieer bezit van de bewaarplaats** dialoogdoos, doe elk van het volgende:

   | Stap | Beschrijving |
   | --- | --- |
   | 1 | Voeg een dossier met de plaatsweg aan de `main` tak van de bewaarplaats van het Git toe die in het **Repository URL** gebied van de Bewaarplaats vermeld is. Klik zo nodig op het pictogram Kopiëren om het pad naar het klembord te kopiëren.<br> Het locatiepad is:<br>`well-known/adobe/cloudmanager-challenge.txt`.<br><br> voeg *niet* een periode bij het begin van de plaatsweg toe, is binnen:<br>`.well-known/adobe/cloudmanager-challenge.txt` |
   | 2 | Voeg de gegenereerde code toe aan het bestand dat u in Stap 1 hebt gemaakt. Klik zo nodig op het pictogram Kopiëren om de code naar het klembord te kopiëren. |
   | 3 | Maak in de Git-opslagplaats een pull-aanvraag en voeg deze samen om de code vast te leggen. |

1. Klik **verifieer**. Nadat de opslagplaats is geverifieerd, verandert de status in de tabel Edge Deliver Sites in een groene cirkel met daarin een wit vinkje.
