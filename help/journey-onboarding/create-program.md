---
title: Een programma maken
description: Leer hoe u Cloud Manager gebruikt om uw eerste programma te maken.
role: Admin, User, Developer
exl-id: ade4bb43-5f48-4938-ac75-118009f0a73b
source-git-commit: 971ef47b66da6d7e032f6109afb4830d49c00071
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 0%

---

# Een programma maken {#create-program}

In dit deel van het [aan boord gaan,](overview.md) u leert hoe u Cloud Manager kunt gebruiken om uw eerste programma te maken.

## Doelstelling {#objective}

Na bestudering van het vorige document tijdens deze instapreis, [Access Cloud Manager,](cloud-manager.md) u hebt ervoor gezorgd dat u de juiste toegang hebt tot Cloud Manager. Nu kunt u uw eerste programma maken.

Na het lezen van dit document zult u:

* Begrijp wat een programma is.
* Weet het verschil tussen productie en zandbakprogramma&#39;s.
* Uw eigen programma kunnen maken.

## Wat is een programma? {#programs}

Programma&#39;s zijn het hoogste organisatieniveau in Cloud Manager. Afhankelijk van uw vergunning met Adobe, staan de programma&#39;s u toe om uw oplossing te organiseren en toegang tot bepaalde teamleden tot die programma&#39;s te verlenen.

Cloud Manager-programma&#39;s vertegenwoordigen sets met Cloud Manager-omgevingen. Deze programma&#39;s steunen logische reeksen bedrijfsinitiatieven, typisch die aan een vergunning gegeven Overeenkomst van het Niveau van de Dienst (SLA) beantwoorden. Het ene programma kan bijvoorbeeld de AEM zijn om een algemene openbare website voor een organisatie te ondersteunen, terwijl een ander programma een interne, centrale DAM vertegenwoordigt.

Als u het voorbeeld van de theoretische Onderneming van het WKND Reizen en van het Avontuur herinnert, die een huurder is die zich op reisgerelateerde media concentreert, zouden zij twee programma&#39;s kunnen hebben: één Sites-programma voor de afdeling WKND Magazine en één Assets-programma voor de afdeling WKND Media. Verschillende teamleden zouden dan toegang hebben tot de verschillende programma&#39;s vanwege hun eigen taakverdeling.

Er zijn twee verschillende soorten programma&#39;s:

* A **productieprogramma** wordt gemaakt om live verkeer voor uw site in te schakelen. Dit is uw &quot;echte&quot; omgeving.
* A **sandboxprogramma** wordt typisch gecreeerd ten behoeve van opleiding, lopende demo&#39;s, enablement, POCs, of documentatie.

Omdat ze verschillende doelen dienen, hebben de verschillende omgevingen verschillende opties. Het proces om ze te maken is echter vergelijkbaar. Voor deze instapreis creëren we een zandbakomgeving.

>[!TIP]
>
>Als u een productieprogramma moet maken, raadpleegt u de [Aanvullende bronnen](#additional-resources) voor een koppeling naar documentatie waarin programma&#39;s gedetailleerd worden beschreven.

## Sandboxprogramma&#39;s maken {#create-sandbox}

Ga als volgt te werk om een sandboxprogramma te maken.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie.

1. Klik op de landingspagina van Cloud Manager op **Programma toevoegen** in de rechterbovenhoek van het scherm.

   ![Openingspagina van Cloud Manager](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin1.png)

1. Selecteer in de wizard Programma maken de optie **Een sandbox instellen**, geef een naam voor het programma op en klik op **Maken**.

   ![Programma-type maken](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/create-sandbox.png)

Naarmate het installatieproces vordert, wordt op de bestemmingspagina een nieuwe sandbox-programmakaart met een statusindicator weergegeven.

![Sandbox-ontwerp van overzichtspagina](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/program-create-setupdemo2.png)

Nadat het programma is voltooid, worden leden van uw organisatie toegewezen aan de **Ontwikkelaar** Met het profiel product kunt u zich aanmelden bij Cloud Manager en de Git-opslagruimten van Cloud Manager beheren.

## Volgende functies {#whats-next}

Nu uw eerste programma is gemaakt, kunt u er omgevingen voor maken. U moet uw instapreis voortzetten door het document opnieuw te bekijken [Maak omgevingen.](create-environments.md)

## Aanvullende bronnen {#additional-resources}

Volg de aanvullende bronnen voor meer informatie over:

* [Programma&#39;s en programmatypen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) - Leer meer over de hiërarchie van Cloud Manager en hoe de verschillende typen programma&#39;s in de structuur passen en hoe ze verschillen.
* [Sandbox-programma&#39;s maken](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md) - Leer hoe u met Cloud Manager uw eigen sandboxprogramma kunt maken voor training, demo, POC of andere niet-productiedoeleinden.
* [Productieprogramma&#39;s maken](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) - Leer hoe u Cloud Manager kunt gebruiken om uw eigen productieprogramma te maken voor het hosten van liveverkeer.
* [Adobe Cloud Manager gebruiken - Programma&#39;s](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html) - De programma&#39;s van de Manager van de Wolk vertegenwoordigen reeksen AEM milieu&#39;s die logische reeksen bedrijfsinitiatieven steunen, typisch die aan een gekochte Overeenkomst van het Niveau van de Dienst (SLA) beantwoorden.
* [as a Cloud Service teams en productprofielen AEM](/help/onboarding/aem-cs-team-product-profiles.md) - Leer hoe AEM as a Cloud Service teams en productprofielen toegang tot uw gelicentieerde Adobe-oplossingen kunnen verlenen en beperken.
