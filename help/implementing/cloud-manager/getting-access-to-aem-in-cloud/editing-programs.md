---
title: Programma's beheren en bewerken
description: Leer hoe u uw productie- en sandboxprogramma's kunt bewerken om de opties aan te passen nadat u deze hebt gemaakt.
exl-id: 819e4a6e-f77a-4594-a402-a300dcbdf510
source-git-commit: 2dfae31e32d375c82c4f690624e48f7f09feb4df
workflow-type: tm+mt
source-wordcount: '773'
ht-degree: 0%

---


# Programma&#39;s beheren en bewerken {#editing-programs}

De **Mijn programma&#39;s** biedt een overzicht van alle programma&#39;s waartoe u toegang hebt. Wanneer u een afzonderlijk programma selecteert, wordt **Programmaoverzicht** Deze pagina bevat in één oogopslag details over het programma.

Van de **Programmaoverzicht**, kunnen gebruikers met de vereiste machtigingen [productieprogramma&#39;s die in uw organisatie zijn gemaakt](creating-production-programs.md) en [sandboxprogramma&#39;s die in uw organisatie zijn gemaakt.](creating-sandbox-programs.md) Door een programma te bewerken kunt u:

* Voeg de oplossing van Plaatsen aan een bestaand programma met Activa toe en omgekeerd.
* Sites of middelen verwijderen uit een bestaand programma met zowel sites als middelen.
* Voeg een tweede, ongebruikte oplossingsrecht, aan of een bestaand programma of als nieuw Programma toe.
* Sandboxprogramma&#39;s verwijderen.

## Machtigingen {#permissions}

U moet lid zijn van de **Zakelijke eigenaar** rol voor het bewerken van programma&#39;s of het verwijderen van sandboxprogramma&#39;s en voor toegang tot het licentiedashboard.

## Mijn programma&#39;s {#my-programs}

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie.

1. De **Mijn programma&#39;s** De pagina bevat een lijst met alle programma&#39;s waartoe u toegang hebt als tegels.

![Pagina Mijn programma&#39;s](/help/implementing/cloud-manager/assets/my-programs.png)

### Oproep tot actie {#cta}

Bij de bovenkant van de pagina is een vraag-aan-actie relevant voor de status van uw organisatie. Als uw programma&#39;s bijvoorbeeld goed zijn ingesteld, kunnen de statistieken van uw activiteiten in de afgelopen 90 dagen worden weergegeven, zoals:

* Aantal [implementaties](/help/implementing/cloud-manager/deploy-code.md)
* Aantal [problemen met de codekwaliteit](/help/implementing/cloud-manager/code-quality-testing.md) geïdentificeerd
* Aantal builds

Of als u net de opstelling van uw org begint, zou er uiteinden op volgende stappen of documentatiemiddelen kunnen zijn.

### Tabblad Programma&#39;s {#programs-tab}

De **Programma&#39;s** worden kaarten weergegeven die elk programma vertegenwoordigen waartoe u toegang hebt. Tik of klik op een kaart om de **Programmaoverzicht** pagina van het programma voor meer informatie over het programma.

Gebruik de sorteeropties om het gewenste programma te vinden.

![Sorteeropties](/help/implementing/cloud-manager/assets/my-programs-sorting.png)

* Sorteren op
   * Gemaakt op (standaard)
   * Programmanaam
   * Status
* Oplopend (standaard) / Aflopend
* Rasterweergave (standaard)
* Lijstweergave

### Tabblad Licentie {#license-tab}

De **Licentie** biedt u snel toegang tot de [Licentiedashboard.](/help/implementing/cloud-manager/license-dashboard.md)

## Programmaoverzicht {#program-overview}

Als u een programma hebt geselecteerd in het menu **[Mijn programma&#39;s](#my-programs)** pagina, wordt in Cloud Manager het dialoogvenster **Programmaoverzicht** pagina voor het geselecteerde programma.

![Pagina Programmaoverzicht](/help/implementing/cloud-manager/assets/program-overview.png)

Tik of klik op de naam van het programma in de linkerbovenhoek van de pagina om snel over te schakelen naar een ander programma of terug naar de **[Mijn programma&#39;s](#my-programs)** pagina. U kunt [het geselecteerde programma bewerken](#editing) of [een programma toevoegen.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md)

![Programmaschakelaar](/help/implementing/cloud-manager/assets/program-switcher.png)

De vraag-aan-actie bij de bovenkant zal u nuttige informatie afhankelijk van de status van uw programma geven. Voor een nieuw programma ziet u mogelijk de volgende stappen worden aangeboden en een herinnering aan een datum waarop u live gaat, [ingesteld tijdens het maken van programma&#39;s.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md)

![Oproep tot actie voor een nieuw programma](/help/implementing/cloud-manager/assets/info-banner-new-program.png)

Voor een levend programma, de status van uw laatste plaatsing met verbindingen voor details en het beginnen van een nieuwe plaatsing.

![Oproep tot actie](/help/implementing/cloud-manager/assets/info-banner.png)

**Omgevingen** en **Pijpleidingen** de kaarten geven een snel overzicht van beide in het geselecteerde programma .

![Kaarten](/help/implementing/cloud-manager/assets/environments-pipelines.png)

De **Prestaties** kaart geeft een overzicht van de **[CDN-dashboard.](/help/implementing/cloud-manager/cdn-performance.md)**

![Prestatiekaart](/help/implementing/cloud-manager/assets/cdn-performance-dashboard.png)

## Een programma bewerken {#editing}

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie.

1. Op de **[Mijn programma&#39;s](#my-programs)** klikt u op het programma dat u wilt bewerken om de details weer te geven.

1. Klik op de naam van het programma linksboven op de pagina en selecteer **Programma bewerken**.

   ![Programma bewerken, optie](assets/edit-program-overview.png)

1. De **Programma bewerken** pagina wordt geopend voor de **Algemeen** tab.

   ![Tabblad Algemeen](assets/edit-program-prod1.png)

1. De beschikbare opties voor het bewerken van het programma zijn dezelfde als die voor het maken van het programma.
   * Zie de documenten [Productieprogramma&#39;s maken](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) en [Sandbox-programma&#39;s maken](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md) voor meer informatie over de afzonderlijke opties.
   * [Aanvullende opties](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#options) kan voor uw productieprogramma afhankelijk van de aanspraken van uw organisatie beschikbaar zijn.

1. Klikken **Bijwerken** om uw wijzigingen in het programma op te slaan.

De wijzigingen in het programma worden opgeslagen.

>[!NOTE]
>
>Telkens wanneer een programma wordt uitgegeven, met inbegrip van het toevoegen van of het verwijderen van een oplossing of toe:voegen-op, worden die veranderingen van kracht na de volgende plaatsing.

## Sandbox-programma&#39;s verwijderen {#delete-sandbox-program}

Als u een sandboxprogramma verwijdert, worden alle bijbehorende omgevingen en pijpleidingen verwijderd.

>[!TIP]
>
>Gebruikers met de **Zakelijke eigenaar** of **Implementatiebeheer** rollen kunnen hun productie en werkgebiedmilieu&#39;s in plaats van het volledige zandbakprogramma Alternatief schrappen.

Ga als volgt te werk om een sandboxprogramma te verwijderen.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie.

1. Op de **[Mijn programma&#39;s](#my-programs)** klikt u op het programma dat u wilt bewerken om de details weer te geven.

1. Klik op de naam van het programma linksboven op de pagina en selecteer **Programma verwijderen**.

   ![Programma verwijderen, optie](assets/delete-sandbox1.png)

U kunt ook op de knop Ovaal op de kaart van uw programma klikken op de overzichtspagina van Cloud Manager en **Programma verwijderen**.

![Sandbox verwijderen van programmakaart](assets/delete-sandbox2.png)

>[!NOTE]
>
>Alleen sandboxprogramma&#39;s kunnen worden verwijderd. Productieprogramma&#39;s kunnen niet worden verwijderd.
