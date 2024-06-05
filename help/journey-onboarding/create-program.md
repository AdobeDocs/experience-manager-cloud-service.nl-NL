---
title: Een programma maken
description: Leer hoe u Cloud Manager gebruikt om uw eerste programma te maken.
role: Admin, User, Developer
exl-id: ade4bb43-5f48-4938-ac75-118009f0a73b
feature: Onboarding
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '669'
ht-degree: 0%

---

# Een programma maken {#create-program}

In dit deel van het [aan boord gaan,](overview.md) Leer hoe u Cloud Manager kunt gebruiken om uw eerste programma te maken.

## Doelstelling {#objective}

Na bestudering van het vorige document tijdens deze instapreis, [Access Cloud Manager,](cloud-manager.md) u hebt ervoor gezorgd dat u de juiste toegang hebt tot Cloud Manager. Nu kunt u uw eerste programma maken.

Nadat u dit document hebt gelezen, kunt u:

* Begrijp en leg uit wat een programma is.
* Weet het verschil tussen productie en zandbakprogramma&#39;s.
* Maak uw eigen programma.

## Wat is een programma? {#programs}

Programma&#39;s zijn het hoogste organisatieniveau in Cloud Manager. Afhankelijk van uw licentie met Adobe, kunt u met programma&#39;s uw oplossing organiseren en toegang verlenen aan bepaalde teamleden tot die programma&#39;s.

Cloud Manager-programma&#39;s vertegenwoordigen sets met Cloud Manager-omgevingen. Deze programma&#39;s steunen logische reeksen bedrijfsinitiatieven, typisch die aan een vergunning gegeven Overeenkomst van het Niveau van de Dienst (SLA) beantwoorden. Het ene programma kan bijvoorbeeld de Adobe Experience Manager-bronnen (AEM) vertegenwoordigen om een wereldwijde openbare website voor een organisatie te ondersteunen, terwijl een ander programma een interne, centrale DAM vertegenwoordigt.

Als u het voorbeeld van de theoretische Onderneming van het WKND Reizen en van het Avontuur herinnert, die een huurder is die zich op reis-verwante media concentreert, zouden zij twee programma&#39;s kunnen hebben. Eén AEM Sites-programma voor de afdeling WKND Magazine en één AEM Assets-programma voor de afdeling WKND Media. Verschillende teamleden zouden dan toegang hebben tot de verschillende programma&#39;s vanwege hun eigen taakverdeling.

Er zijn twee verschillende soorten programma&#39;s:

* A **productieprogramma** wordt gemaakt om live verkeer voor uw site in te schakelen. Dit is uw &quot;echte&quot; omgeving.
* A **sandboxprogramma** wordt typisch gecreeerd ten behoeve van opleiding, lopende demo&#39;s, enablement, POCs, of documentatie.

Omdat ze verschillende doelen dienen, hebben de verschillende omgevingen verschillende opties. Het proces om ze te maken is echter vergelijkbaar. Voor deze instapreis creëert u een sandboxomgeving.

>[!TIP]
>
>Als u een productieprogramma moet maken, raadpleegt u de [Aanvullende bronnen](#additional-resources) voor een koppeling naar documentatie waarin programma&#39;s gedetailleerd worden beschreven.

## Sandboxprogramma&#39;s maken {#create-sandbox}

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie.

1. Klik op de landingspagina van Cloud Manager op **Programma toevoegen** rechtsboven in het scherm.

   ![Openingspagina van Cloud Manager](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/cloud-manager-my-programs.png)

1. Selecteer in de wizard Programma maken de optie **Een sandbox instellen** Geef vervolgens een naam voor het programma op en selecteer **Doorgaan**.

   ![Programma-type maken](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/create-sandbox.png)

1. In de **Sandbox instellen** kunt u kiezen welke oplossingen u wilt inschakelen in uw sandboxprogramma. De **Sites** en **Activa** oplossingen worden altijd opgenomen in sandboxprogramma&#39;s en worden automatisch geselecteerd. Dit is voldoende voor uw instapvoorbeeld. Klikken **Maken**.

   ![Selectie van oplossing](assets/set-up-sandbox-onboarding.png)

U ziet een nieuwe zandbakprogrammakaart op de landingspagina met een statusindicator aangezien het opstellingsproces vordert.

![Sandbox-ontwerp van overzichtspagina](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/program-create-setupdemo2.png)

Nadat het programma is voltooid, worden leden van uw organisatie toegewezen aan de **Ontwikkelaar** Het productprofiel kan u aanmelden bij Cloud Manager en de opslagruimten voor cloudbeheer beheren.

## Volgende functies {#whats-next}

Nu uw eerste programma is gemaakt, kunt u er omgevingen voor maken. Ga door met de volgende revisie van het document [Maak omgevingen.](create-environments.md)

## Aanvullende bronnen {#additional-resources}

Hieronder volgen aanvullende, optionele bronnen als u verder wilt gaan dan de inhoud van de instapreis.

* [Programma&#39;s en programmatypen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) - Leer meer over de hiërarchie van Cloud Manager en hoe de verschillende typen programma&#39;s in de structuur passen en hoe ze verschillen.
* [Sandbox-programma&#39;s maken](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md) - Leer hoe u met Cloud Manager uw eigen sandboxprogramma kunt maken voor training, demo, POC of andere niet-productiedoeleinden.
* [Productieprogramma&#39;s maken](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) - Leer hoe u Cloud Manager kunt gebruiken om uw eigen productieprogramma te maken voor het hosten van live verkeer.
* [Adobe Cloud Manager gebruiken - Programma&#39;s](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html) - De programma&#39;s van de Manager van de Wolk vertegenwoordigen reeksen AEM milieu&#39;s die logische reeksen bedrijfsinitiatieven steunen, typisch die aan een gekochte Overeenkomst van het Niveau van de Dienst (SLA) beantwoorden.
* [as a Cloud Service teams en productprofielen AEM](/help/onboarding/aem-cs-team-product-profiles.md) - Leer hoe AEM as a Cloud Service teams en productprofielen toegang tot uw gelicentieerde oplossingen voor Adoben kunnen verlenen en beperken.
