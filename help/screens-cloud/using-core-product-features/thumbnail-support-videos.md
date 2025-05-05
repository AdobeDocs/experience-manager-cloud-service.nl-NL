---
title: Ondersteuning voor miniaturen voor video's in Screens as a Cloud Service
description: Op deze pagina wordt beschreven hoe u ondersteuning voor miniaturen voor video's in Screens as a Cloud Service kunt toevoegen.
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
>**Eerste vereisten**
>Voordat u leert hoe u miniaturen voor video&#39;s kunt gebruiken, moet u weten hoe u video-uitvoeringen voor kanalen maakt in Screens as a Cloud Service project. Zie [ Creërend VideoUitvoeringen in Screens as a Cloud Service ](/help/screens-cloud/configuring/creating-screens-video-renditions-cloud-service.md).

Voer de onderstaande stappen uit om miniaturen in video&#39;s te gebruiken:

1. Navigeer naar een bestaand Screens-kanaal of maak een kanaal.

   >[!NOTE]
   >Leren hoe te om een kanaal tot stand te brengen en inhoud aan een kanaal toe te voegen, zie [ Creërend en het Leiden een Kanaal in Screens as a Cloud Service ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/screens-as-cloud-service/create-content/creating-channels-screens-cloud.html?lang=nl-NL).

1. Selecteer het kanaal. Voor de actiebar, geeft de klik **&#x200B;**&#x200B;uit om de redacteur te openen.


   ![ geef knoop op actiebar ](/help/screens-cloud/using-core-product-features/assets/thumbnail-1.png) uit.

1. Voeg of geef een bestaande videocomponent, zoals aangetoond in hieronder figuur toe uit.

   ![ Gemarkeerd beeld van een videoactiva ](/help/screens-cloud/using-core-product-features/assets/thumbnail-2.png).

1. Voeg of geef een bestaande videocomponent, zoals aangetoond in hieronder figuur toe uit.

1. Selecteer de video en klik Configure (*moersleutel*) pictogram om de videoeigenschappen te openen.

   ![ Geselecteerde beeld van videoactiva met pijl die aan het Configure pictogram richten, geportretteerd als moersleutel. op de toolbar ](/help/screens-cloud/using-core-product-features/assets/thumbnail-3.png).

1. Het **Video** dialoogvakje opent waar u de **3&rbrace; dalingsstreek van de Duimnagel &lbrace;kunt bekijken.**

   ![ de dialoogdoos die van de Video beeld van videoactiva en de duimnageldoos toont ](/help/screens-cloud/using-core-product-features/assets/thumbnail-4.png).

1. De belemmering en laat vallen een beeld van de activa plukker aan de **1&rbrace; dalingsstreek van de Duimnagel &lbrace;en klikt** Gedaan **.**

   ![ de beeldplukker van Activa die achter de Videodialoogdoos met beeldactiva wordt getoond in de de dalingsdoos van de Duimnagel ](/help/screens-cloud/using-core-product-features/assets/thumbnail-5.png).

1. Klik **Voorproef**.

1. Als een video op de component wordt geplaatst, speelt de video. Als dat niet het geval is en de miniatuur is ingesteld, wordt de miniatuur afgespeeld. Anders, wordt de component beschouwd als niet gevormd en overgeslagen.

## Ondersteunde gevallen voor gebruik tijdens het gebruik van miniaturen in video&#39;s {#understand-use-case}

Miniatuur in video&#39;s biedt ondersteuning voor de volgende gebruiksscenario&#39;s:

* Een video-component zonder installatie wordt overgeslagen.

* De miniatuur wordt afgespeeld in een video-onderdeel met alleen de miniatuurset.

* De video wordt afgespeeld door een videocomponent met zowel de video (als de video de juiste uitvoering heeft) als de miniatuurset.

* Een video-component met de videoset speelt de miniatuur af, als er een afspeelfout optreedt, of slaat naar het volgende item over als de miniatuur niet is geconfigureerd.
