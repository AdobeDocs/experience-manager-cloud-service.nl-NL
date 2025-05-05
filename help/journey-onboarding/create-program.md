---
title: Een programma maken
description: Leer hoe u Cloud Manager kunt gebruiken om uw eerste programma te maken.
role: Admin, User, Developer
exl-id: ade4bb43-5f48-4938-ac75-118009f0a73b
feature: Onboarding
source-git-commit: bd05433bb4d92a4120b19ad99d211a4a5e1f06ca
workflow-type: tm+mt
source-wordcount: '671'
ht-degree: 0%

---

# Een programma maken {#create-program}

In dit deel van de [ onboarding reis ](overview.md), leert u hoe te om Cloud Manager te gebruiken om uw eerste programma tot stand te brengen.

## Doelstelling {#objective}

Na het herzien van het vorige document in deze onboarding reis, [ Toegang Cloud Manager ](cloud-manager.md), hebt u ervoor gezorgd u aangewezen toegang tot Cloud Manager hebt. U kunt nu uw eerste programma maken.

Nadat u dit document hebt gelezen, kunt u:

* Begrijp en leg uit wat een programma is.
* Weet het verschil tussen productie en zandbakprogramma&#39;s.
* Maak uw eigen programma.

## Wat is een programma? {#programs}

Programma&#39;s zijn het hoogste organisatieniveau in Cloud Manager. Afhankelijk van uw licentie met Adobe, kunt u met programma&#39;s uw oplossing organiseren en toegang verlenen aan bepaalde teamleden tot die programma&#39;s.

Cloud Manager-programma&#39;s vertegenwoordigen groepen Cloud Manager-omgevingen. Deze programma&#39;s ondersteunen logische reeksen bedrijfsinitiatieven, die doorgaans overeenkomen met een Service level agreement (SLA) met licentie. Het ene programma kan bijvoorbeeld de Adobe Experience Manager (AEM)-bronnen vertegenwoordigen om een wereldwijde openbare website voor een organisatie te ondersteunen, terwijl een ander programma een interne, centrale DAM vertegenwoordigt.

Kijk naar het voorbeeld van de theoretische WKND-ondernemingen voor reizen en avonturen, een huurder die gespecialiseerd is in reismedia. Ze zouden twee programma&#39;s kunnen hebben. Eén AEM Sites-programma voor de afdeling WKND Magazine en één AEM Assets-programma voor de afdeling WKND Media. Verschillende teamleden zouden dan toegang hebben tot de verschillende programma&#39;s vanwege hun eigen taakverdeling.

Er zijn twee verschillende soorten programma&#39;s:

* A **productieprogramma** wordt gecreeerd om levend verkeer voor uw plaats toe te laten. Dit programma is uw &quot;echte&quot; omgeving.
* A **zandbakprogramma** wordt typisch gecreeerd om de doeleinden van opleiding, lopende demo&#39;s, enablement, POCs, of documentatie te dienen.

Omdat ze verschillende doelen dienen, hebben de verschillende omgevingen verschillende opties. Het proces om ze te maken is echter vergelijkbaar. Voor deze instapreis creëert u een sandboxomgeving.

>[!TIP]
>
>Als u een productieprogramma moet creëren, zie de [ Extra sectie van Middelen ](#additional-resources) voor een verbinding aan documentatie beschrijvend programma in detail.

## Sandboxprogramma&#39;s maken {#create-sandbox}

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Van Cloud Manager het landen pagina, klik **voegt Programma** in de hoogste juiste hoek van het scherm toe.

   ![ Cloud Manager landende pagina ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/cloud-manager-my-programs.png)

1. Van creeer programmatovenaar, uitgezochte **Opstelling een zandbak**, dan verstrek een programmanaam en selecteer **verdergaan**.

   ![ de typeverwezenlijking van het Programma ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/create-sandbox.png)

1. In de **Opstelling uw zandbak** dialoogdoos, kunt u kiezen welke oplossingen u in uw zandbakprogramma wilt toelaten. De **Plaatsen** en **Assets** oplossingen zijn altijd inbegrepen in zandbakprogramma&#39;s en automatisch geselecteerd. Deze oplossingen zijn voldoende voor uw instapvoorbeeld. Klik **creëren**.

   ![ selectie van de Oplossing ](assets/set-up-sandbox-onboarding.png)

U ziet een nieuwe zandbakprogrammakaart op de landingspagina met een statusindicator aangezien het opstellingsproces vordert.

![ zandbak verwezenlijking van overzichtspagina ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/program-create-setupdemo2.png)

Zodra het programma volledig is, kunnen de leden van uw organisatie die aan het **productprofiel van de 1&rbrace; ontwikkelaar** wordt toegewezen zich bij Cloud Manager aanmelden en de bewaarplaatsen van de it van Cloud Manager beheren.

## Wat nu? {#whats-next}

Met het eerste programma dat u hebt gemaakt, kunt u nu omgevingen voor dit programma maken. Ga uw aan boord komende reis door het document te herzien [ voort creeer Milieu ](create-environments.md).

Zie ook [ aan boord uw plaats van Edge Delivery Services ](/help/implementing/cloud-manager/edge-delivery/create-edge-delivery-site.md).

## Aanvullende bronnen {#additional-resources}

Hieronder volgen aanvullende, optionele bronnen als u verder wilt gaan dan de inhoud van de instapreis.

* [ Programma&#39;s en de Types van Programma ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) - leer over de hiërarchie van Cloud Manager en hoe de verschillende soorten programma&#39;s in zijn structuur passen en hoe zij verschillen.
* [ Creërend de Programma&#39;s van Sandbox ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md) - leer hoe te om Cloud Manager te gebruiken om uw eigen zandbakprogramma voor opleiding, demonstratie, POC, of andere niet productiedoeleinden tot stand te brengen.
* [ Creërend de Programma&#39;s van de Productie ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) - leer hoe te om Cloud Manager te gebruiken om uw eigen productieprogramma tot stand te brengen om levend verkeer te ontvangen.
* [ Gebruikend Adobe Cloud Manager - de programma&#39;s van Cloud Manager ](https://experienceleague.adobe.com/nl/docs/experience-manager-learn/cloud-service/cloud-manager/programs) - de programma&#39;s van vertegenwoordigen reeksen milieu&#39;s van AEM ondersteunend logische reeksen bedrijfsinitiatieven, typisch die met een gekochte Service level agreement (SLA) beantwoorden.
* [ het Team van AEM as a Cloud Service en de Profielen van het Product ](/help/onboarding/aem-cs-team-product-profiles.md) - leer hoe het team en de productprofielen van AEM as a Cloud Service toegang tot uw vergunning gegeven oplossingen van Adobe kunnen verlenen en beperken.
