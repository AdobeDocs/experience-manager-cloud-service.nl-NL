---
title: Lanceringen bewerken
description: 'Nadat u een opstartafbeelding voor de pagina (of set pagina''s) hebt gemaakt, kunt u de inhoud bewerken in de opstartafbeelding van de pagina(''s). '
translation-type: tm+mt
source-git-commit: 914eb7f7b040b99c11d9f109549eb13868058320
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 18%

---


# Lanceringen bewerken {#editing-launches}

## Starten van pagina&#39;s bewerken {#editing-launch-pages}

Wanneer een startpagina (of een set pagina&#39;s) is gemaakt, kunt u de inhoud bewerken in de opstartafbeelding van de pagina(&#39;s).

1. Open [Starten vanuit Referenties (Sites-console)](/help/sites-cloud/authoring/launches/overview.md#launches-in-references-sites-console) om de beschikbare handelingen weer te geven.
1. Selecteer **Ga naar de pagina** om de pagina te openen voor bewerking.

Als u de pagina bewerkt, ziet u een indicatie in de bovenste werkbalk, samen met de opties **Verlaten** en **Navigeren**:

![Starten vanuit paginaeditor verlaten en navigeren](/help/sites-cloud/authoring/assets/launches-edit-01.png)

### Starten van pagina&#39;s bewerken die zijn onderworpen aan een actieve kopie {#editing-launch-pages-subject-to-a-live-copy}

Als uw lancering op een levende kopie gebaseerd is, zult u: <!--If your launch is based upon a [live copy](/help/sites-administering/msm.md) then you will:-->

* Zie slotsymbolen (kleine hanglocks) wanneer u een component (inhoud en/of eigenschappen) uitgeeft.
* Zie het tabblad **Live kopie** in **Pagina-eigenschappen**

Een livekopie wordt gebruikt om content te synchroniseren *van* de bronvertakking *naar* de startvertakking (om uw lancering up-to-date te houden als er veranderingen in de bron worden aangebracht).

U kunt wijzigingen aanbrengen op dezelfde manier als waarop u een live standaardkopie kunt bewerken. bijvoorbeeld:

* Als u op een gesloten hangslot klikt, wordt deze synchronisatie verbroken en kunt u nieuwe updates voor de inhoud uitvoeren wanneer u de toepassing start. Als de vergrendeling is opgeheven (open hanglock), worden de wijzigingen niet overschreven door wijzigingen die op dezelfde locatie in de bronvertakking zijn aangebracht.
* **Overname** voor een bepaalde pagina onderbreken (en **hervatten**).

Zie Inhoud van Live kopie wijzigen voor meer informatie. <!--See [Changing Live Copy Content](/help/sites-administering/msm-livecopy.md#changing-live-copy-content) for further information.-->

## Een startpagina vergelijken met de bijbehorende bronpagina {#comparing-a-launch-page-to-its-source-page}

Als u de door u aangebrachte wijzigingen wilt bijhouden, kunt u de start weergeven in **Referenties** en de startpagina vergelijken met de bijbehorende bronpagina:

1. In **Sites** console, [navigeer aan de bronpagina&#39;s van uw lancering en selecteer één](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources).
1. Open het venster **[Referenties](/help/sites-cloud/authoring/getting-started/basic-handling.md#references)** en selecteer **Launches**.
1. Selecteer uw specifieke lancering toen **Vergelijk met Bron**:

   ![Starten vergelijken met bron](/help/sites-cloud/authoring/assets/launches-compare.png)

1. De twee pagina&#39;s (opstart en bron) worden naast elkaar geopend.

   Zie [Paginadiff](/help/sites-cloud/authoring/features/page-diff.md) voor volledige informatie over het gebruik van deze functie.

## De gebruikte bronpagina&#39;s wijzigen {#changing-the-source-pages-used}

U kunt op elk gewenst moment pagina&#39;s toevoegen aan of verwijderen uit het bereik van bronpagina&#39;s voor een opstart:

1. Open en selecteer de opstart vanuit:
   * Met de [Launches-console](/help/sites-cloud/authoring/launches/overview.md#the-launches-console):
      * Selecteer **Bewerken**.
   * [Referenties (Sites-console)](/help/sites-cloud/authoring/launches/overview.md#launches-in-references-sites-console) om de beschikbare acties weer te geven:
      * Selecteer **Starten bewerken**.
      * De bronpagina&#39;s worden weergegeven.
1. Breng de gewenste wijzigingen aan en bevestig vervolgens met **Opslaan**.

>[!NOTE]
>
>Als u pagina&#39;s wilt toevoegen aan een opstart, moeten deze zich onder een gemeenschappelijke taalbasis bevinden. d.w.z. binnen één locatie.

## Een opstartconfiguratie bewerken {#editing-a-launch-configuration}

U kunt op elk gewenst moment de eigenschappen voor een opstart bewerken:

1. Open en selecteer de opstart vanuit:
   * de [Startconsole](/help/sites-cloud/authoring/launches/overview.md#the-launches-console):
      * Selecteer **Eigenschappen**.
   * [Referenties (Sites-console)](/help/sites-cloud/authoring/launches/overview.md#launches-in-references-sites-console) om de beschikbare acties weer te geven:
      * Selecteer **Eigenschappen bewerken**.
      * De details worden weergegeven.
1. Breng de gewenste wijzigingen aan en bevestig vervolgens met **Opslaan**.
   * Zie [Lanceringen - de volgorde van gebeurtenissen](/help/sites-cloud/authoring/launches/overview.md#launches-the-order-of-events) voor informatie over het doel en de interactie van de velden **Startdatum** en **Geschikt voor productie**.

## De opstartstatus van een pagina {#discovering-the-launch-status-of-a-page} opzoeken

De status wordt weergegeven wanneer u een specifieke start selecteert op het tabblad Referenties (zie [Starten in Referenties (Sites Console)](/help/sites-cloud/authoring/launches/overview.md#launches-in-references-sites-console)).

![Status van opstarten weergeven](/help/sites-cloud/authoring/assets/launches-status.png)
