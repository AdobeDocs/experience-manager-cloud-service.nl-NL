---
title: Een Edge Delivery-site toevoegen aan Cloud Manager
description: Leer hoe u een Edge Delivery-site toevoegt aan uw productieprogramma of sandboxprogramma.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: 17e842c9-599a-4877-9834-1e7220f508a8
source-git-commit: a078d45f81fc7081012ebf24fa8f46dc1a218cd7
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# Een Edge Delivery-site toevoegen aan Cloud Manager {#adding}

Nadat u een Edge Delivery-site aan uw productieprogramma hebt toegevoegd, wordt er een licentie voor Edge Delivery Services op toegepast.

Het toevoegen van een plaats van Edge Delivery aan Cloud Manager wordt vereist om [ een steunkaartje voor uw project van Edge Delivery ](/help/edge/overview.md##support-ticket) te registreren.

Zie ook [ Inleiding aan Edge Delivery Services in Cloud Manager ](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md).

**om een plaats van Edge Delivery aan Cloud Manager toe te voegen:**

1. Meld u aan bij Cloud Manager op [`https://my.cloudmanager.adobe.com` ](https://my.cloudmanager.adobe.com/) en selecteer het gewenste programma.
1. Voer een van de volgende handelingen uit:

   * Van de **pagina van het Overzicht van het Programma**, klik **Edge Delivery** tabel. Dan, dichtbij de laag-juiste hoek van de pagina, klik **toevoegen de plaats van Edge Delivery**.

     ![ voeg de plaats van Edge Delivery van het lusje van Edge Delivery toe ](/help/implementing/cloud-manager/assets/cm-eds-add1.png)

   * In de upper-left hoek van de pagina, klik ![ tonen menupictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) om het linkerzijmenu te openbaren.
Onder de **rubriek van de Diensten**, klik ![ het paginapictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) **Edge Delivery Plaatsen**.
Vlak de hoger-juiste hoek van de pagina, klik **plaats** toevoegen.

     ![ voeg de plaats van Edge Delivery van de knoop van Plaatsen van Edge Delivery toe ](/help/implementing/cloud-manager/assets/cm-eds-add2.png)

1. In **voeg de plaats van Edge Delivery** dialoogdoos toe, verstrek de volgende informatie op de vereiste gebieden:

   | Tekstveld | Beschrijving |
   | - | --- |
   | Sitenaam | Voer de naam in van de Edge Delivery-site die u toevoegt.<br> de naam dient als uniek herkenningsteken voor de plaats binnen Cloud Manager. |
   | URL opslagplaats | Voer de Git-opslagplaats in waar de code van uw website is opgeslagen.<br> Dit gebied staat Cloud Manager toe om de code van die bewaarplaats tijdens het plaatsingsproces te trekken. |
   | Sitebeschrijving (optioneel) | Voer een korte beschrijving in van de Edge Delivery-site die u toevoegt.<br> de beschrijvingshulp van A om de plaats te identificeren en te onderscheiden, die het gemakkelijker maken om onder andere plaatsen te beheren en te erkennen u hebt toegevoegd. |

1. In de laag-juiste hoek van de dialoogdoos, voegt de klik **** toe.

1. In **verifieer het bezit van de bewaarplaats** dialoogdoos, verifieer de eigendom van uw bewaarplaats door de volgende stappen te doen:

   | Stapnummer | Beschrijving |
   | - | - |
   | **1** | Voeg een dossier met de weg en de naam `well-known/adobe/cloudmanager-challenge.txt` aan de `main` tak van de bewaarplaats van het Git toe die in het **Repository URL** gebied wordt vermeld. Voeg *niet* een periode bij het begin van de plaatsweg toe.<br> indien nodig, klik ![ pictogram van het Exemplaar ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg) om de weg aan het klembord te kopiëren. |
   | **2** | Voeg de code die in het tekstveld in Stap 2 wordt weergegeven toe aan het bestand dat u net hebt gemaakt in Stap 1.<br> indien nodig, klik ![ pictogram van het Exemplaar ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg) om de code aan het klembord te kopiëren. |
   | **3** | Maak een pull-verzoek in de Git-opslagplaats voor de wijzigingen die u net hebt gemaakt en voeg deze vervolgens samen tot `main` om de code vast te leggen. |

1. Klik **verifieer**.

Wanneer de opslagplaats wordt geverifieerd, wordt de status in de Edge Delivery-sitetabel bijgewerkt. Een groene cirkel met een wit vinkje geeft de status aan.

In de zelfde lijst, klik ![ Informatie over het plaatspictogram van Edge Delivery ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_InfoOutline_18_N.svg) om plaatsdetails te bekijken. Deze informatie omvat de geverifieerde Repository URL, samen met de URL&#39;s van de website Voorbeeld en Productie.
