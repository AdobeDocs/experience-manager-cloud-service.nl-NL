---
title: Programma maken
description: Leer hoe te opstelling een nieuw programma en een pijpleiding om toe:voegen-op op te stellen.
exl-id: 06287618-0328-40b1-bba8-84002283f23f
feature: Onboarding
role: Admin, User, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '688'
ht-degree: 0%

---


# Programma maken {#creating-a-program}

Leer hoe te opstelling een nieuw programma en een pijpleiding om toe:voegen-op op te stellen.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de Server van de Verwijzing van Adobe Experience Manager (AEM) de Toestemming van de Demo&#39;s van de Verwijzing toe:voegen-op reis, [ begrijpt Invoegtoepassing van de Demo van de Verwijzing ](installation.md), leerde u hoe het installatieproces van de Invoegtoepassing van de Demos van de Verwijzing werkt, die illustreert hoe de verschillende stukken samenwerken. Nu moet u:

* Een basisbegrip hebben van Cloud Manager.
* Begrijp hoe de pijpleidingen inhoud en configuratie aan AEM leveren.
* Bekijk hoe sjablonen met slechts een paar klikken sites kunnen maken die vooraf zijn gevuld met demo-inhoud.

Dit artikel bouwt op die grondbeginselen voort en neemt de eerste configuratiestap om een programma voor het testen doeleinden tot stand te brengen en gebruikt een pijpleiding om toe:voegen-op inhoud op te stellen.

## Doelstelling {#objective}

Dit document helpt u begrijpen hoe te opstelling een nieuw programma en een pijpleiding om toe:voegen-op op te stellen. Na het lezen moet u het volgende kunnen doen:

* Begrijp en leg uit hoe u Cloud Manager kunt gebruiken om een programma te maken.
* Activeer de Add-on Referentie-demo&#39;s voor het nieuwe programma.
* Stel een pijpleiding in werking zodat kunt u toe:voegen-op inhoud opstellen.

## Een programma maken {#create-program}

Nadat u zich hebt aangemeld bij Cloud Manager, kunt u een sandboxprogramma voor uw test- en demonstratiedoeleinden maken.

>[!NOTE]
>
>Uw gebruiker moet een lid van de **rol van de Bedrijfs eigenaar** in Cloud Manager in uw organisatie zijn om programma&#39;s tot stand te brengen.

1. Logboek in Adobe Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/).

1. Nadat u zich hebt aangemeld, zorgt u ervoor dat u zich in de juiste organisatie bevindt door deze in de rechterbovenhoek van het scherm te controleren. Als u slechts lid bent van één org, is deze stap niet nodig.

   ![ overzicht van Cloud Manager ](assets/cloud-manager.png)

1. Selecteer **Programma** bij het hoogste recht van het venster toevoegen.

1. In **maak uw dialoog van het Programma**:

   1. Verstrek de naam van het a **Programma** om uw programma te beschrijven.
   1. Selecteer **Opstelling een zandbak** voor uw **Doelstelling van het Programma**
   1. Selecteer **verdergaan**.

   ![ creeer programmadialoog ](assets/create-program.png)

1. In de **Opstelling uw zandbak** dialoog in de **Oplossingen &amp; toe:voegen-ons** lijst, breidt de **5} ingang van Plaatsen {in de lijst uit door het in kaart te brengen of te klikken en dan de Demo&#39;s van de Verwijzing** te controleren **.**

   * Als u ook demo&#39;s voor AEM Screens wilt tot stand brengen, controleer de **optie van Screens** in de lijst. Selecteer **Update**.

   ![ Selecterend toe:voegen-op voor verwijzingsdemo in programmaopstelling ](assets/select-reference-demo-add-on.png)


1. Selecteer **creeer** en Cloud Manager begint vestiging uw zandbakprogramma. U wordt naar het scherm met het programmaoverzicht geleid en een korte bannermelding geeft aan dat het proces is gestart. Er is een kaart toegevoegd aan de overzichtspagina voor uw nieuwe programma. Het installatieproces duurt een paar minuten.

1. Zodra de opstelling volledig is, toont de kaart voor het milieu op de overzichtspagina zijn status als **Klaar**. Selecteer de kaart zodat u de omgeving kunt openen.

   ![ volledige de verwezenlijking van het Programma ](assets/ready.png)

1. Uw omgeving is gereed en de invoegtoepassing is nu ingeschakeld als optie, maar de inhoud van de demo moet worden geïmplementeerd om beschikbaar te AEM. Om dit te doen, selecteer de ellipsknoop naast Deploy aan Dev pijpleiding in de **1} kaart van Pijpleidingen {en selecteer** Looppas **.**

   ![ Begin ](assets/run.png)

1. De pijpleiding begint en u wordt genomen aan een pagina die de vooruitgang van de plaatsing detailleert. U kunt bij het maken van het programma weg van dit scherm navigeren en indien nodig later terugkeren.

   ![ Plaatsing ](assets/deployment.png)

De pijplijn kan enkele minuten duren. Zodra volledig, zijn toe:voegen-aan en zijn demo inhoud beschikbaar voor gebruik in het AEM auteursmilieu.

## Volgende functies {#what-is-next}

Nu u dit deel van de AEM Invoegtoepassing van de Demo van de Verwijzing hebt voltooid zou u moeten:

* Begrijp hoe u Cloud Manager kunt gebruiken om een programma te maken.
* Zorg dat u weet hoe u de invoegtoepassing voor demo&#39;s referentie voor het programma activeert.
* Kan een pijpleiding in werking stellen zodat kunt u de toe:voegen-op inhoud opstellen.

Bouw op deze kennis voort en ga uw AEM Toelaatbare reis van de Demo van de Verwijzing door volgende het herzien [ tot een Plaats van de Demo ](create-site.md) leiden. In daar, leert u om een demoplaats in AEM tot stand te brengen die op een bibliotheek van pre-gevormde malplaatjes wordt gebaseerd die door de pijpleiding werden opgesteld.

## Aanvullende bronnen {#additional-resources}

* [ documentatie van Cloud Manager ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/onboarding-concepts/cloud-manager-introduction.html) - als u meer details over de eigenschappen van Cloud Manager zou willen, kunt u de diepgaande technische documenten direct willen raadplegen.
