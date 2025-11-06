---
title: Programma's bewerken
description: Leer hoe u uw productie- en sandboxprogramma's kunt bewerken om de opties aan te passen nadat u deze hebt gemaakt.
exl-id: 819e4a6e-f77a-4594-a402-a300dcbdf510
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---


# Programma&#39;s bewerken {#editing-programs}

Om programma&#39;s te beheren en uit te geven, begin bij [**Mijn Programma&#39;s** console ](/help/implementing/cloud-manager/navigation.md). De **Mijn pagina van Programma&#39;s** verstrekt een overzicht van alle programma&#39;s waartot u toegang hebt. Wanneer het selecteren van een individueel programma, verstrekt de **pagina van het Overzicht van het 0} Programma details van het programma in een blik.**

Van het **Overzicht van het Programma**, kunnen de gebruikers met de vereiste toestemmingen [ productieprogramma&#39;s uitgeven die in uw organisatie ](creating-production-programs.md) worden gecreeerd en [ zandbakprogramma&#39;s die in uw organisatie ](creating-sandbox-programs.md) worden gecreeerd. Door een programma te bewerken kunt u:

* Voeg Sites-oplossing toe aan een bestaand programma met Assets en omgekeerd.
* Sites of Assets verwijderen uit een bestaand programma met zowel Sites als Assets.
* Voeg een ongebruikte oplossingsbevoegdheid aan een bestaand programma toe of creeer een nieuw programma.
* Sandboxprogramma&#39;s verwijderen.

## Machtigingen {#permissions}

U moet de **rol van de Bedrijfs eigenaar** hebben om programma&#39;s uit te geven, zandbakprogramma&#39;s te schrappen, en tot het Dashboard van de Vergunning toegang te hebben.

## Een programma bewerken {#editing}

Telkens wanneer een programma wordt uitgegeven, met inbegrip van het toevoegen van of het verwijderen van een oplossing of toe:voegen-op, worden die veranderingen van kracht na de volgende plaatsing.

**om een programma uit te geven:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Voor **[Mijn pagina van Programma&#39;s](#my-programs)**, klik het programma dat u wilt uitgeven om zijn details te tonen.

1. Klik de naam van uw programma in upper-left van de pagina en selecteer **programma** uitgeven.

   ![ geef programmaoptie ](assets/edit-program-overview.png) uit

1. De **geeft de pagina van het Programma** uit opent aan **Algemene** tabel.

   ![ Algemene tabel ](assets/edit-program-prod1.png)

1. De opties die beschikbaar zijn voor het bewerken van het programma zijn dezelfde opties voor het maken van programma&#39;s.
   * Zie [ tot de Programma&#39;s van de Productie ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) leiden en [ Sandbox Programma&#39;s ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md) voor details op de individuele opties.
   * [ de Extra opties ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#options) kunnen voor uw productieprogramma afhankelijk van de aanspraken van uw organisatie beschikbaar zijn.

1. Klik **Update** om uw veranderingen in het programma te bewaren.

## Een sandboxprogramma verwijderen {#delete-sandbox-program}

Als u een sandboxprogramma verwijdert, worden alle bijbehorende omgevingen en pijpleidingen verwijderd.

>[!TIP]
>
>De gebruikers met de **BedrijfsEigenaar** of **rollen van de Manager van de Plaatsing** kunnen hun productie en werkgebiedmilieu&#39;s in plaats van het volledige zandbakprogramma Alternatief schrappen.

**om een zandbakprogramma te schrappen:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Voor **[Mijn pagina van Programma&#39;s](#my-programs)**, klik het programma dat u wilt uitgeven om zijn details te tonen.

1. Klik de naam van uw programma in upper-left van de pagina en selecteer **Programma van de Schrapping**.

   ![ de programmaoptie van de Schrapping ](assets/delete-sandbox1.png)

Alternatief, kunt u ![ Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) op de kaart van uw programma van de overzichtspagina van Cloud Manager klikken en **Programma van de Schrapping** selecteren.

![ Schrap zandbak van programmakaart ](assets/delete-sandbox2.png)

>[!NOTE]
>
>Alleen sandboxprogramma&#39;s kunnen worden verwijderd. Productieprogramma&#39;s kunnen niet worden verwijderd.
