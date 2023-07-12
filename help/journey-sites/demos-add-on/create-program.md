---
title: Programma maken
description: Leer hoe te opstelling een nieuw programma en een pijpleiding om toe:voegen-op op te stellen.
exl-id: 06287618-0328-40b1-bba8-84002283f23f
source-git-commit: 7c33a618f474914ca80dff525552017c55a32517
workflow-type: tm+mt
source-wordcount: '709'
ht-degree: 0%

---


# Programma maken {#creating-a-program}

Leer hoe te opstelling een nieuw programma en een pijpleiding om toe:voegen-op op te stellen.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de AEM Reference Demos Add-on trip, [Invoegtoepassing demodemodus begrijpen,](installation.md) U leerde hoe het installatieproces van de Add-On van de Demos van de Verwijzing werkt, die hoe de verschillende stukken samenwerken. Nu moet u:

* U hebt een basiskennis van Cloud Manager.
* Begrijp hoe de pijpleidingen inhoud en configuratie aan AEM leveren.
* Bekijk hoe sjablonen met slechts een paar klikken nieuwe sites kunnen maken die vooraf zijn gevuld met demo-inhoud.

Dit artikel bouwt op die grondbeginselen voort en neemt de eerste configuratiestap om een programma voor het testen doeleinden tot stand te brengen en gebruikt een pijpleiding om toe:voegen-op inhoud op te stellen.

## Doelstelling {#objective}

Dit document helpt u begrijpen hoe te opstelling een nieuw programma en een pijpleiding om toe:voegen-op op te stellen. Na het lezen moet u:

* Begrijp hoe u met Cloud Manager een nieuw programma kunt maken.
* Zorg dat u weet hoe u de Add-on Reference Demos voor het nieuwe programma activeert.
* Kan een pijpleiding in werking stellen om toe:voegen-op inhoud op te stellen.

## Een programma maken {#create-program}

Nadat u zich hebt aangemeld bij Cloud Manager, kunt u een nieuw sandboxprogramma maken voor test- en demonstratiedoeleinden.

>[!NOTE]
>
>Je gebruiker moet lid zijn van de **Zakelijke eigenaar** rol in Cloud Manager in uw organisatie om programma&#39;s te maken.

1. Meld u aan bij Adobe Cloud Manager via [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/).

1. Nadat u zich hebt aangemeld, zorgt u ervoor dat u zich in de juiste organisatie bevindt door deze in de rechterbovenhoek van het scherm te controleren. Als u slechts lid bent van één org, is deze stap niet nodig.

   ![Overzicht van Cloud Manager](assets/cloud-manager.png)

1. Tik of klik op **Programma toevoegen** rechtsboven in het venster.

1. In de **Laten we uw programma maken** dialoogvenster:

   1. Een **Programmanaam** om uw programma te beschrijven.
   1. Tik of klik op **Een sandbox instellen** voor uw **Programmadoelstelling**
   1. Tik of klik op **Doorgaan**.

   ![Het dialoogvenster Programma maken](assets/create-program.png)

1. In de **Sandbox instellen** in het dialoogvenster **Oplossingen en invoegtoepassingen** tabel uitvouwen **Sites** item in de lijst door erop te tikken of erop te klikken en vervolgens te controleren **Demo van referenties**.

   * Als u ook demo&#39;s voor AEM Screens wilt maken, schakelt u het selectievakje **Schermen** ook in de lijst. Tik of klik op **Bijwerken**.

   ![Invoegtoepassing selecteren voor verwijzingsdemo in programma-instelling](assets/select-reference-demo-add-on.png)


1. Tik of klik op **Maken** en Cloud Manager wordt gestart met het instellen van uw sandboxprogramma. U wordt naar het scherm met het programmaoverzicht geleid en een korte bannermelding geeft aan dat het proces is gestart. Er is een kaart toegevoegd aan de overzichtspagina voor uw nieuwe programma. Het installatieproces duurt een paar minuten.

1. Zodra de installatie is voltooid, geeft de kaart voor de omgeving op de overzichtspagina zijn status als **Gereed**. Tik of klik op de kaart om de omgeving te openen.

   ![Programma is voltooid](assets/ready.png)

1. Uw omgeving is gereed en de invoegtoepassing is nu ingeschakeld als optie, maar de inhoud van de demo moet worden geïmplementeerd om beschikbaar te AEM. Om deze kraan te doen of de ellipsknoop naast Deploy te klikken aan Dev pijpleiding in **Pijpleidingen** kaart en selecteer **Uitvoeren**.

   ![Start](assets/run.png)

1. De pijpleiding begint en u wordt genomen aan een pagina die de vooruitgang van de plaatsing detailleert. U kunt bij het maken van het programma weg van dit scherm navigeren en indien nodig later terugkeren.

   ![Implementatie](assets/deployment.png)

De pijplijn kan enkele minuten duren. Zodra volledig, toe:voegen-op en zijn demo inhoud is beschikbaar voor gebruik in het AEM auteursmilieu.

## Volgende functies {#what-is-next}

Nu u dit deel van de AEM Toelage van de Demo van de Verwijzing hebt voltooid zou u moeten:

* Begrijp hoe u met Cloud Manager een nieuw programma kunt maken.
* Zorg dat u weet hoe u de Add-on Reference Demos voor het nieuwe programma activeert.
* Kan een pijpleiding in werking stellen om toe:voegen-op inhoud op te stellen.

Bouw op deze kennis voort en vervolg uw AEM Toelating van de Demo van de Verwijzing door het document opnieuw te bekijken [Maak een demo-site,](create-site.md) waar u zult leren om een demoplaats in AEM tot stand te brengen die op een bibliotheek van pre-gevormde malplaatjes wordt gebaseerd die door de pijpleiding werden opgesteld.

## Aanvullende bronnen {#additional-resources}

* [Documentatie van Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/cloud-manager-introduction.html) - Als u meer informatie wilt over de functies van Cloud Manager, kunt u de diepgaande technische documenten direct raadplegen.
