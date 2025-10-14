---
title: Starten bewerken
description: Nadat u een opstartafbeelding voor de pagina (of set pagina's) hebt gemaakt, kunt u de inhoud bewerken in de opstartafbeelding van de pagina's.
exl-id: d3cd3383-e0a0-4019-9f97-8baa3be99e6e
solution: Experience Manager Sites
feature: Authoring, Launches
role: User
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 17%

---

# Starten bewerken {#editing-launches}

## Starten van pagina&#39;s bewerken {#editing-launch-pages}

Wanneer een startpagina (of een set pagina&#39;s) is gemaakt, kunt u de inhoud van de opstartafbeelding van de pagina&#39;s bewerken.

1. Heb toegang tot [&#x200B; Lancering van Verwijzingen (de console van Plaatsen) &#x200B;](/help/sites-cloud/authoring/launches/overview.md#launches-in-references-sites-console) om de beschikbare acties te tonen.
1. Selecteer **gaan naar de pagina** om de pagina voor het uitgeven te openen.

Wanneer het uitgeven van de pagina, kunt u een aanwijzing in de hoogste toolbar zien, samen met **Verlof** en **navigeren** opties:

![&#x200B; Verlof en navigeer lancering van de Redacteur van de Pagina &#x200B;](/help/sites-cloud/authoring/assets/launches-edit-01.png)

>[!NOTE]
>
>U mag een pagina niet verplaatsen binnen een startperiode. Als u deze handeling uitvoert, wordt een waarschuwingsbericht weergegeven:
>
>* Waarschuwing: deze pagina is de bron van een opstart. Het verplaatsen van de pagina is niet toegestaan.

### Pagina&#39;s starten bewerken die zijn onderworpen aan een live kopie {#editing-launch-pages-subject-to-a-live-copy}

Als uw lancering op a [&#x200B; Levend Exemplaar &#x200B;](/help/sites-cloud/administering/msm/overview.md) gebaseerd is dan zult u:

* Zie slotsymbolen (kleine hanglocks) wanneer u een component (inhoud en/of eigenschappen) uitgeeft.
* Zie **Levende 1&rbrace; lusje van het Exemplaar &lbrace;in** Eigenschappen van de Pagina **&#x200B;**

Een livekopie wordt gebruikt om content te synchroniseren *van* de bronvertakking *naar* de startvertakking (om uw lancering up-to-date te houden als er veranderingen in de bron worden aangebracht).

U kunt wijzigingen aanbrengen op dezelfde manier als u een standaard live kopie kunt bewerken, bijvoorbeeld:

* Als u op een gesloten hangslot klikt, wordt deze synchronisatie verbroken en kunt u nieuwe updates voor de inhoud uitvoeren wanneer u de toepassing start. Als de vergrendeling is opgeheven (open hanglock), worden de wijzigingen niet overschreven door wijzigingen die op dezelfde locatie in de bronvertakking zijn aangebracht.
* **Overname** voor een bepaalde pagina onderbreken (en **hervatten**).

Zie [&#x200B; Veranderend Levende Inhoud van het Exemplaar &#x200B;](/help/sites-cloud/administering/msm/creating-live-copies.md) voor verdere informatie.

## Een startpagina vergelijken met de bijbehorende Source-pagina {#comparing-a-launch-page-to-its-source-page}

Als u de door u aangebrachte wijzigingen wilt bijhouden, kunt u de start weergeven in **Referenties** en de startpagina vergelijken met de bijbehorende bronpagina:

1. In de **console van Plaatsen**, [&#x200B; navigeer aan de bronpagina&#39;s van uw lancering en selecteer één &#x200B;](/help/sites-cloud/authoring/basic-handling.md#viewing-and-selecting-resources).
1. Open het **[paneel van Verwijzingen](/help/sites-cloud/authoring/basic-handling.md#references)** en selecteer **Lanceringen**.
1. Selecteer uw specifieke lancering toen **vergelijk met Source**:

   ![&#x200B; Vergelijkende lancering aan bron &#x200B;](/help/sites-cloud/authoring/assets/launches-compare.png)

1. De twee pagina&#39;s (opstart en bron) worden naast elkaar geopend.

   Voor volledige informatie over het gebruiken van deze eigenschap zie [&#x200B; Afschuiving van de Pagina &#x200B;](/help/sites-cloud/authoring/sites-console/page-diff.md).

## De gebruikte Source-pagina&#39;s wijzigen {#changing-the-source-pages-used}

U kunt op elk gewenst moment pagina&#39;s toevoegen aan of verwijderen uit het bereik van bronpagina&#39;s voor een opstart:

1. Open en selecteer de opstart vanuit:
   * De [&#x200B; console van Lanceringen &#x200B;](/help/sites-cloud/authoring/launches/overview.md#the-launches-console):
      * Selecteer **uitgeven**.
   * [&#x200B; Verwijzingen (de console van Plaatsen) &#x200B;](/help/sites-cloud/authoring/launches/overview.md#launches-in-references-sites-console) om de beschikbare acties te tonen:
      * Selecteer **uitgeven Lancering**.
      * De bronpagina&#39;s worden weergegeven.
1. Breng de gewenste wijzigingen aan en bevestig vervolgens met **Opslaan**.

>[!NOTE]
>
>Als u pagina&#39;s wilt toevoegen aan een introductie, moeten deze zich onder een gemeenschappelijke hoofdtaalmap bevinden, dat wil zeggen binnen één site.

## Een opstartconfiguratie bewerken {#editing-a-launch-configuration}

U kunt op elk gewenst moment de eigenschappen voor een opstart bewerken:

1. Open en selecteer de opstart vanuit:
   * de [&#x200B; console van Lanceringen &#x200B;](/help/sites-cloud/authoring/launches/overview.md#the-launches-console):
      * Selecteer **Eigenschappen**.
   * [&#x200B; Verwijzingen (de console van Plaatsen) &#x200B;](/help/sites-cloud/authoring/launches/overview.md#launches-in-references-sites-console) om de beschikbare acties te tonen:
      * Selecteer **uitgeven Eigenschappen**.
      * De details worden weergegeven.
1. Breng de gewenste wijzigingen aan en bevestig vervolgens met **Opslaan**.
   * Zie [Lanceringen - de volgorde van gebeurtenissen](/help/sites-cloud/authoring/launches/overview.md#launches-the-order-of-events) voor informatie over het doel en de interactie van de velden **Startdatum** en **Geschikt voor productie**.

## De opstartstatus van een pagina vaststellen {#discovering-the-launch-status-of-a-page}

De status wordt getoond wanneer u een specifieke lancering van het verwijzingenlusje selecteert (zie [&#x200B; Lanceringen in Verwijzingen (de Console van Plaatsen) &#x200B;](/help/sites-cloud/authoring/launches/overview.md#launches-in-references-sites-console)).

![&#x200B; ontdekt lanceringsstatus &#x200B;](/help/sites-cloud/authoring/assets/launches-status.png)
