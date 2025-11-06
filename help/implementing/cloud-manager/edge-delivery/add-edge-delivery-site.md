---
title: Een Edge Delivery-site toevoegen aan Cloud Manager
description: Leer hoe u een Edge Delivery-site toevoegt aan uw productieprogramma of sandboxprogramma.
feature: Cloud Manager, Developing
role: Admin, Developer
exl-id: 17e842c9-599a-4877-9834-1e7220f508a8
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 0%

---

# Een Edge Delivery-site toevoegen aan Cloud Manager {#adding}

>[!IMPORTANT]
>
>Ontdek waarom je op je Edge Delivery Services-site naar Cloud Manager moet gaan.
>Zie [ Voordelen om de Adobe geadviseerde weg voor Edge Delivery Services ](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md#recommended-path-eds) te gebruiken.

**om een plaats van Edge Delivery aan Cloud Manager toe te voegen:**

1. Zorg ervoor dat u uw programma eerst hebt gemaakt met een Edge Delivery Services-licentie voordat u zich aan boord van een Edge Delivery-site in Cloud Manager bevindt.
Zie [ een productieprogramma ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) creëren.
1. Teken in Cloud Manager bij [ experience.adobe.com ](https://experience.adobe.com).
1. In de **Snelle toegang** sectie, klik **Experience Manager**.
1. In het linkerzijpaneel, klik **Cloud Manager**.
1. Selecteer de gewenste organisatie.
1. Op de **Mijn console van Programma&#39;s**, klik een programma.
1. Voer een van de volgende handelingen uit:

   * Van de **pagina van het Overzicht van het Programma**, klik **Edge Delivery** tabel. Dan, dichtbij de laag-juiste hoek van de pagina, klik **toevoegen de plaats van Edge Delivery**.

     ![ voeg de plaats van Edge Delivery van het lusje van Edge Delivery toe ](/help/implementing/cloud-manager/assets/cm-eds-add1.png)

   * In de upper-left hoek van de pagina, klik ![ tonen menupictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) om het linkerzijmenu te openbaren.
Onder de **rubriek van de Diensten**, klik ![ het paginapictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) **Edge Delivery Plaatsen**.
Vlak de hoger-juiste hoek van de pagina, klik ![ pictogram van de Verbinding of voeg ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Link_18_N.svg) toe **plaats van Edge Delivery** toevoegt.

     ![ voeg de plaats van Edge Delivery van de knoop van Plaatsen van Edge Delivery toe ](/help/implementing/cloud-manager/assets/cm-eds-add2.png)

1. In **voeg de plaats van Edge Delivery** dialoogdoos toe, verstrek de volgende informatie op de vereiste gebieden:

   | Tekstveld | Beschrijving |
   | - | --- |
   | Sitenaam | Voer de naam in van de Edge Delivery-site die u toevoegt.<br> de naam dient als uniek herkenningsteken voor de plaats binnen Cloud Manager. |
   | Edge Delivery-oorsprong | Deze waarde geeft het URL-pad aan naar de inhoudsbron voor uw site in Edge Delivery Services. Cloud Manager wordt ook gekoppeld aan uw livesite.<br> URL omvat typisch de *tak*, *project*, en *huurder*, zoals in het volgende voorbeeld (voor illustratiedoeleinden slechts):<br>`https://main--{site}--{org}.aem.live` |
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
