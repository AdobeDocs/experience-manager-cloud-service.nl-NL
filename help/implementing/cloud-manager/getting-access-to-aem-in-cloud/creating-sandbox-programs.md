---
title: Sandbox-programma's maken
description: Leer hoe u Cloud Manager kunt gebruiken om uw eigen sandboxprogramma te maken voor training, demo, POC of andere niet-productiedoeleinden.
exl-id: 10011392-3059-4bb0-88db-0af1d390742e
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# Sandboxprogramma&#39;s maken {#create-sandbox-program}

Een zandbakprogramma wordt typisch gecreeerd om ten behoeve van opleiding, lopende demo&#39;s, enablement, POCs, of documentatie te dienen, en is niet bedoeld om levend verkeer te dragen. Zie [&#x200B; Inleiding aan zandbakprogramma&#39;s &#x200B;](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md).

Leer meer over programmatypes in het document [&#x200B; Begrijpend Programma en de Types van Programma &#x200B;](program-types.md).

## Een sandboxprogramma maken {#create}

1. Logon aan Cloud Manager bij [&#x200B; my.cloudmanager.adobe.com &#x200B;](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, dichtbij de hoger-juiste hoek, klik **Programma** toevoegen.

   ![&#x200B; Cloud Manager landende pagina &#x200B;](assets/log-in.png)

1. In *maak uw tovenaar van het Programma*, op het **Naam van het Programma** tekstgebied, typ de naam u voor het programma wilt.

1. Onder **Doelstelling van het Programma**, uitgezochte ![&#x200B; Toverstaf pictogram &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_MagicWand_18_N.svg) **opstelling een zandbak**.

   ![&#x200B; de typeverwezenlijking van het Programma &#x200B;](assets/create-sandbox.png)

1. (Optioneel) Voer in de rechterbenedenhoek van het dialoogvenster Wizard een van de volgende handelingen uit:

   * Sleep en laat vallen een beelddossier op het ![&#x200B; pictogram van het Beeld &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Image_18_N.svg) **een doel van het programmabeeld** toevoegen.
   * Klik ![&#x200B; pictogram van het Beeld &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Image_18_N.svg) **voeg een programmabeeld** toe, dan selecteer een beeld van een dossierbrowser.
   * Klik ![&#x200B; pictogram van de Schrapping &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_DeleteOutline_18_N.svg) om een beeld te verwijderen dat u toevoegde.

1. Klik **verdergaan**.

1. In de **Oplossingen &amp; toe:voegen-ons** lijstdoos, selecteer één of meerdere oplossingen om in het programma te omvatten.

   * Klik op het chevron links van de naam van een oplossing om eventuele optionele invoegtoepassingen die u wilt opnemen in een geselecteerde oplossing, weer te geven.
   * De **Plaatsen**, **Assets**, en **Edge Delivery Services** oplossingen worden altijd geselecteerd door gebrek wanneer u een zandbakprogramma creeert. U kunt de selectie niet opheffen.

   ![&#x200B; Uitgezochte oplossingen en toe:voegen-ons voor een zandbak &#x200B;](assets/sandbox-solutions-add-ons.png)

1. Klik **creëren**. Cloud Manager maakt uw sandboxprogramma en geeft dit voor selectie weer op de bestemmingspagina.

![&#x200B; zandbak verwezenlijking van overzichtspagina &#x200B;](assets/sandbox-setup.png)

## Toegang tot sandbox {#access}

Nadat een nieuw sandboxprogramma is gemaakt, kunt u de details van de sandboxinstelling bekijken en de omgeving openen door de overzichtspagina van het programma te bekijken.

1. Van Cloud Manager die pagina, in het Sandbox programma landen, klik ![&#x200B; Meer klein lijstpictogram &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) op uw gecreeerd zandbakprogramma.

   ![&#x200B; Toegang tot programma overzicht &#x200B;](assets/program-overview-sandbox.png)

1. Wanneer de stap van de projectverwezenlijking voltooit, kunt u de **verbinding van Info van de Reactie van de Toegang** klikken om uw git repo te kunnen gebruiken.

   ![&#x200B; configuratie van het Programma &#x200B;](assets/create-program4.png)

   >[!TIP]
   >
   >Meer leren over de toegang tot van en het beheren van uw bewaarplaats van het Git, zie [&#x200B; Toegang hebbend tot Git &#x200B;](/help/implementing/cloud-manager/managing-code/accessing-repos.md).

1. Nadat het ontwikkelmilieu wordt gecreeerd, kunt u **Toegang AEM** klikken en in AEM ondertekenen.

   ![&#x200B; verbinding van AEM van de Toegang &#x200B;](assets/create-program5.png)

1. Wanneer de niet-productiepijpleiding die aan ontwikkeling wordt opgesteld volledig is, gidst de tovenaar in call-to-action u om of tot de ontwikkelomgeving van AEM toegang te hebben of code aan de ontwikkelomgeving op te stellen.

   ![&#x200B; die zandbak &#x200B;](assets/create-program-setup-deploy.png) opstelt

>[!TIP]
>
>Zie [&#x200B; Navigerend de UI van Cloud Manager &#x200B;](/help/implementing/cloud-manager/navigation.md) voor details op hoe te Cloud Manager navigeren en het begrijpen van de **Mijn console van Programma&#39;s**.
