---
title: Sandbox-programma's maken
description: Leer hoe u Cloud Manager kunt gebruiken om uw eigen sandboxprogramma te maken voor training, demo, POC of andere niet-productiedoeleinden.
exl-id: 10011392-3059-4bb0-88db-0af1d390742e
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 2d1382c84d872719332986baa5829d1623d9d9a6
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# Sandboxprogramma&#39;s maken {#create-sandbox-program}

Een zandbakprogramma wordt typisch gecreeerd om ten behoeve van opleiding, lopende demo&#39;s, enablement, POCs, of documentatie te dienen, en is niet bedoeld om levend verkeer te dragen. Zie [ Inleiding aan zandbakprogramma&#39;s ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md).

Leer meer over programmatypes in het document [ Begrijpend Programma en de Types van Programma ](program-types.md).

## Een sandboxprogramma maken {#create}

1. Logon aan Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, dichtbij de hoger-juiste hoek, klik **Programma** toevoegen.

   ![ Cloud Manager landende pagina ](assets/log-in.png)

1. In *maak uw tovenaar van het Programma*, op het **Naam van het Programma** tekstgebied, typ de naam u voor het programma wilt.

1. Onder **Doelstelling van het Programma**, uitgezochte ![ Toverstaf pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_MagicWand_18_N.svg) **opstelling een zandbak**.

   ![ de typeverwezenlijking van het Programma ](assets/create-sandbox.png)

1. (Optioneel) Voer in de rechterbenedenhoek van het dialoogvenster Wizard een van de volgende handelingen uit:

   * Sleep en laat vallen een beelddossier op het ![ pictogram van het Beeld ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Image_18_N.svg) **een doel van het programmabeeld** toevoegen.
   * Klik ![ pictogram van het Beeld ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Image_18_N.svg) **voeg een programmabeeld** toe, dan selecteer een beeld van een dossierbrowser.
   * Klik ![ pictogram van de Schrapping ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_DeleteOutline_18_N.svg) om een beeld te verwijderen dat u toevoegde.

1. Klik **verdergaan**.

1. In de **Oplossingen &amp; toe:voegen-ons** lijstdoos, selecteer één of meerdere oplossingen om in het programma te omvatten.

   * Klik op het chevron links van de naam van een oplossing om eventuele optionele invoegtoepassingen die u wilt opnemen in een geselecteerde oplossing, weer te geven.
   * De **Plaatsen**, **Assets**, en **Edge leveren de oplossingen van de Diensten** altijd worden geselecteerd door gebrek wanneer u een zandbakprogramma creeert. U kunt de selectie niet opheffen.

   ![ Uitgezochte oplossingen en toe:voegen-ons voor een zandbak ](assets/sandbox-solutions-add-ons.png)

1. Klik **creëren**. Cloud Manager maakt uw sandboxprogramma en geeft dit voor selectie weer op de bestemmingspagina.

![ zandbak verwezenlijking van overzichtspagina ](assets/sandbox-setup.png)

## Toegang tot sandbox {#access}

Nadat een nieuw sandboxprogramma is gemaakt, kunt u de details van de sandboxinstelling bekijken en de omgeving openen door de overzichtspagina van het programma te bekijken.

1. Van Cloud Manager die pagina, in het Sandbox programma landen, klik ![ Meer klein lijstpictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) op uw gecreeerd zandbakprogramma.

   ![ Toegang tot programma overzicht ](assets/program-overview-sandbox.png)

1. Wanneer de stap van de projectverwezenlijking voltooit, kunt u de **verbinding van Info van de Reactie van de Toegang** klikken om uw git repo te kunnen gebruiken.

   ![ configuratie van het Programma ](assets/create-program4.png)

   >[!TIP]
   >
   >Meer leren over de toegang tot van en het beheren van uw bewaarplaats van het Git, zie [ Toegang hebbend tot Git ](/help/implementing/cloud-manager/managing-code/accessing-repos.md).

1. Nadat het ontwikkelmilieu wordt gecreeerd, kunt u **AEM van de Toegang** klikken en in AEM ondertekenen.

   ![ Toegang AEM verbinding ](assets/create-program5.png)

1. Wanneer de niet productiepijplijn die aan ontwikkeling opstelt volledig is, leidt de tovenaar in vraag-aan-actie u om of tot de AEM ontwikkelomgeving toegang te hebben of code aan het ontwikkelmilieu op te stellen.

   ![ die zandbak ](assets/create-program-setup-deploy.png) opstelt

>[!TIP]
>
>Zie [ Navigerend de UI van Cloud Manager ](/help/implementing/cloud-manager/navigation.md) voor details op hoe te Cloud Manager navigeren en het begrijpen van de **Mijn console van Programma&#39;s**.
