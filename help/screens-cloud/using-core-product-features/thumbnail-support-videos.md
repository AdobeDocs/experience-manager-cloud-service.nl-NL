---
title: Ondersteuning voor miniaturen voor video's in as a Cloud Service schermen
description: Op deze pagina wordt beschreven hoe u ondersteuning voor miniaturen voor video's in as a Cloud Service schermen toevoegt.
index: true
exl-id: 7b15d7cc-f089-4008-9039-5f48343a0f20
feature: Developing Screens
role: Admin, Developer, User
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 0%

---

# Ondersteuning van miniaturen voor video&#39;s {#thumbnail-support-videos}

## Inleiding {#introduction}

Een inhoudauteur kan een duimnagel voor video&#39;s bepalen zodat het beeld als placeholder wordt gebruikt en behoorlijk het playback en richten van inhoud test, terwijl de daadwerkelijke video door het aangewezen team wordt voltooid. De afbeelding kan ook worden gebruikt voor het geval dat het afspelen van de video mislukt.

Door ondersteuning toe te voegen voor een miniatuurafbeelding op de video-component kan de klant op de juiste wijze een geldige component in het kanaal met werkelijke inhoud toevoegen en eventuele doelconfiguraties uitvoeren voordat de video wordt geleverd.

>[!NOTE]
>Als de miniatuurafbeelding op de video-component is ingesteld, wordt deze afgespeeld wanneer de video niet kan worden afgespeeld op de speler. Met deze workflow kunt u het gewenste bericht aan het publiek afspelen (door inhoud af te spelen) in plaats van het volledig over te slaan.

Met ondersteuning voor miniaturen kunt u het volgende doen:

* Een kanaalervaring voorbereiden wanneer de video&#39;s nog niet klaar zijn of wanneer u niet per se een grote download van middelen op de spelers wilt testen

* Stel een fallback-mechanisme in voor het geval er afspeelproblemen optreden op het apparaat.

## Miniaturen in video&#39;s gebruiken {#using-thumbnails}

>[!IMPORTANT]
>**Vereisten**
>Voordat u leert hoe u miniaturen voor video&#39;s kunt gebruiken, moet u weten hoe u video-uitvoeringen voor kanalen maakt in het as a Cloud Service project Schermen. Zie [Video-uitvoeringen maken in as a Cloud Service schermen](/help/screens-cloud/configuring/creating-screens-video-renditions-cloud-service.md).

Voer de onderstaande stappen uit om miniaturen in video&#39;s te gebruiken:

1. Navigeer naar een bestaand rasterkanaal of maak een kanaal.

   >[!NOTE]
   >Ga voor meer informatie over het maken van een kanaal en het toevoegen van inhoud aan een kanaal naar [Een kanaal maken en beheren in as a Cloud Service schermen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/screens-as-cloud-service/create-content/creating-channels-screens-cloud.html).

1. Selecteer het kanaal. Klik op de actiebalk op **Bewerken** de editor openen.


   ![De knop Bewerken op de actiebalk](/help/screens-cloud/using-core-product-features/assets/thumbnail-1.png).

1. Voeg of geef een bestaande videocomponent, zoals aangetoond in hieronder figuur toe uit.

   ![Gemarkeerde afbeelding van een video-element](/help/screens-cloud/using-core-product-features/assets/thumbnail-2.png).

1. Voeg of geef een bestaande videocomponent, zoals aangetoond in hieronder figuur toe uit.

1. Selecteer de video en klik op Configure (*moersleutel*) om de video-eigenschappen te openen.

   ![Afbeelding van geselecteerd video-element met pijl die wijst naar het pictogram Configureren, weergegeven als een moersleutel. op de werkbalk](/help/screens-cloud/using-core-product-features/assets/thumbnail-3.png).

1. De **Video** wordt geopend waar u de **Miniatuur** dropzone.

   ![Het dialoogvenster Video waarin de afbeelding van het video-element en het dialoogvenster Miniatuur worden weergegeven](/help/screens-cloud/using-core-product-features/assets/thumbnail-4.png).

1. Sleep een afbeelding van de elementkiezer naar de **Miniatuur** zone neerzetten en klikken **Gereed**.

   ![De afbeeldingskiezer van het element die achter het dialoogvenster Video wordt weergegeven met het afbeeldingselement dat wordt weergegeven in de vervolgkeuzelijst Miniatuur](/help/screens-cloud/using-core-product-features/assets/thumbnail-5.png).

1. Klikken **Voorvertoning**.

1. Als een video op de component wordt geplaatst, speelt de video. Als dat niet het geval is en de miniatuur is ingesteld, wordt de miniatuur afgespeeld. Anders, wordt de component beschouwd als niet gevormd en overgeslagen.

## Ondersteunde gevallen voor gebruik tijdens het gebruik van miniaturen in video&#39;s {#understand-use-case}

Miniatuur in video&#39;s biedt ondersteuning voor de volgende gebruiksscenario&#39;s:

* Een video-component zonder installatie wordt overgeslagen.

* De miniatuur wordt afgespeeld in een video-onderdeel met alleen de miniatuurset.

* De video wordt afgespeeld door een videocomponent met zowel de video (als de video de juiste uitvoering heeft) als de miniatuurset.

* Een video-component met de videoset speelt de miniatuur af, als er een afspeelfout optreedt, of slaat naar het volgende item over als de miniatuur niet is geconfigureerd.
