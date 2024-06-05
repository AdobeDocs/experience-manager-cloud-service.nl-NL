---
title: Starten bewerken
description: Nadat u een opstartafbeelding voor de pagina (of set pagina's) hebt gemaakt, kunt u de inhoud bewerken in de opstartafbeelding van de pagina's.
exl-id: d3cd3383-e0a0-4019-9f97-8baa3be99e6e
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 17%

---

# Starten bewerken {#editing-launches}

## Starten van pagina&#39;s bewerken {#editing-launch-pages}

Wanneer een startpagina (of een set pagina&#39;s) is gemaakt, kunt u de inhoud van de opstartafbeelding van de pagina&#39;s bewerken.

1. Toegang krijgen tot de [Starten vanuit verwijzingen (Sites-console)](/help/sites-cloud/authoring/launches/overview.md#launches-in-references-sites-console) om de beschikbare acties weer te geven.
1. Selecteren **Ga naar de pagina** om de pagina voor bewerking te openen.

Wanneer u de pagina bewerkt, ziet u een indicatie in de bovenste werkbalk, samen met de **Verlaten** en **Navigeren** opties:

![Starten vanuit paginaeditor verlaten en navigeren](/help/sites-cloud/authoring/assets/launches-edit-01.png)

>[!NOTE]
>
>U mag een pagina niet verplaatsen binnen een startperiode. Als u deze handeling uitvoert, wordt een waarschuwingsbericht weergegeven:
>
>* Waarschuwing: deze pagina is de bron van een opstart. Het verplaatsen van de pagina is niet toegestaan.

### Pagina&#39;s starten bewerken die zijn onderworpen aan een live kopie {#editing-launch-pages-subject-to-a-live-copy}

Als uw lancering op a gebaseerd is [Live kopie](/help/sites-cloud/administering/msm/overview.md) dan zult u:

* Zie slotsymbolen (kleine hanglocks) wanneer u een component (inhoud en/of eigenschappen) uitgeeft.
* Zie de **Live kopie** tab in **Pagina-eigenschappen**

Een livekopie wordt gebruikt om content te synchroniseren *van* de bronvertakking *naar* de startvertakking (om uw lancering up-to-date te houden als er veranderingen in de bron worden aangebracht).

U kunt wijzigingen aanbrengen op dezelfde manier als u een standaard live kopie kunt bewerken, bijvoorbeeld:

* Als u op een gesloten hangslot klikt, wordt deze synchronisatie verbroken en kunt u nieuwe updates voor de inhoud uitvoeren wanneer u de toepassing start. Als de vergrendeling is opgeheven (open hanglock), worden de wijzigingen niet overschreven door wijzigingen die op dezelfde locatie in de bronvertakking zijn aangebracht.
* **Overname** voor een bepaalde pagina onderbreken (en **hervatten**).

Zie [Live kopie van inhoud wijzigen](/help/sites-cloud/administering/msm/creating-live-copies.md) voor nadere informatie.

## Een startpagina vergelijken met de bijbehorende bronpagina {#comparing-a-launch-page-to-its-source-page}

Als u de door u aangebrachte wijzigingen wilt bijhouden, kunt u de start weergeven in **Referenties** en de startpagina vergelijken met de bijbehorende bronpagina:

1. In de **Sites** console, [navigeer naar de bronpagina&#39;s van uw lancering en selecteer één](/help/sites-cloud/authoring/basic-handling.md#viewing-and-selecting-resources).
1. Open de **[Verwijzingen](/help/sites-cloud/authoring/basic-handling.md#references)** en selecteert u **Starten**.
1. Selecteer vervolgens uw specifieke startpagina **Vergelijken met bron**:

   ![Starten vergelijken met bron](/help/sites-cloud/authoring/assets/launches-compare.png)

1. De twee pagina&#39;s (opstart en bron) worden naast elkaar geopend.

   Zie voor meer informatie over het gebruik van deze functie [Pagina grijs](/help/sites-cloud/authoring/sites-console/page-diff.md).

## De gebruikte bronpagina&#39;s wijzigen {#changing-the-source-pages-used}

U kunt op elk gewenst moment pagina&#39;s toevoegen aan of verwijderen uit het bereik van bronpagina&#39;s voor een opstart:

1. Open en selecteer de opstart vanuit:
   * De [Startconsole](/help/sites-cloud/authoring/launches/overview.md#the-launches-console):
      * Selecteren **Bewerken**.
   * [Referenties (Sites-console)](/help/sites-cloud/authoring/launches/overview.md#launches-in-references-sites-console) om de beschikbare acties weer te geven:
      * Selecteren **Starten bewerken**.
      * De bronpagina&#39;s worden weergegeven.
1. Breng de gewenste wijzigingen aan en bevestig vervolgens met **Opslaan**.

>[!NOTE]
>
>Als u pagina&#39;s wilt toevoegen aan een introductie, moeten deze zich onder een gemeenschappelijke hoofdtaalmap bevinden, dat wil zeggen binnen één site.

## Een opstartconfiguratie bewerken {#editing-a-launch-configuration}

U kunt op elk gewenst moment de eigenschappen voor een opstart bewerken:

1. Open en selecteer de opstart vanuit:
   * de [Startconsole](/help/sites-cloud/authoring/launches/overview.md#the-launches-console):
      * Selecteren **Eigenschappen**.
   * [Referenties (Sites-console)](/help/sites-cloud/authoring/launches/overview.md#launches-in-references-sites-console) om de beschikbare acties weer te geven:
      * Selecteren **Eigenschappen bewerken**.
      * De details worden weergegeven.
1. Breng de gewenste wijzigingen aan en bevestig vervolgens met **Opslaan**.
   * Zie [Lanceringen - de volgorde van gebeurtenissen](/help/sites-cloud/authoring/launches/overview.md#launches-the-order-of-events) voor informatie over het doel en de interactie van de velden **Startdatum** en **Geschikt voor productie**.

## De opstartstatus van een pagina vaststellen {#discovering-the-launch-status-of-a-page}

De status wordt weergegeven wanneer u een specifieke start selecteert op het tabblad Referenties (zie [Starten in verwijzingen (siteconsole)](/help/sites-cloud/authoring/launches/overview.md#launches-in-references-sites-console)).

![Status van opstart vaststellen](/help/sites-cloud/authoring/assets/launches-status.png)
