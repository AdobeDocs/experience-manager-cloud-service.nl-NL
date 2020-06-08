---
title: Lanceringen maken
description: U kunt een lancering tot stand brengen om het bijwerken van een nieuwe versie van bestaande Web-pagina's voor toekomstige activering toe te laten.
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8
workflow-type: tm+mt
source-wordcount: '1000'
ht-degree: 14%

---


# Lanceringen maken {#creating-launches}

Maak een lancering om het bijwerken van een nieuwe versie van bestaande Web-pagina&#39;s voor toekomstige activering toe te laten. Wanneer u een Starten creeert, specificeert u een titel en de bronpagina:

* De titel wordt weergegeven in de [References](/help/sites-cloud/authoring/fundamentals/environment-tools.md#references) rail, vanwaar auteurs toegang hebben om er aan te werken.
* De onderliggende pagina&#39;s van de bronpagina worden standaard in de opstart opgenomen. U kunt desgewenst alleen de bronpagina gebruiken.
* Standaard worden de startpagina&#39;s automatisch bijgewerkt met Live Copy wanneer de bronpagina&#39;s veranderen. U kunt opgeven dat er een statische kopie wordt gemaakt om automatische wijzigingen te voorkomen. <!--By default, [Live Copy](/help/sites-administering/msm.md) automatically updates the launch pages as the source pages change. You can specify that a static copy is created to prevent automatic changes.-->

U kunt desgewenst de **Startdatum** (en -tijd) opgeven om te bepalen wanneer de startpagina&#39;s moeten worden gepromoveerd en geactiveerd. De **startdatum** werkt echter alleen in combinatie met de markering **Geschikt voor productie** (zie [Een startconfiguratie bewerken](/help/sites-cloud/authoring/launches/editing.md#editing-a-launch-configuration)). Opdat de acties automatisch zouden optreden, moeten beide worden ingesteld.

## Starten maken {#creating-a-launch}

U kunt een lancering van of Sites of de console van Lanceringen tot stand brengen:

1. Open de **Sites** - of **Launches** -console.

   >[!NOTE]
   >
   >Wanneer het gebruiken van de console van **Plaatsen** is het gebruikelijk om aan de plaats van de bronpagina te navigeren, maar dit is niet verplicht aangezien u kunt navigeren wanneer het selecteren van de Bron **van de** Lancering in de tovenaar.

1. Afhankelijk van de console die u gebruikt:
   * **Lanceringen**:
      1. Select **Create Launch** from the toolbar to open the wizard.
   * **Sites**:
      1. Select **Create** from the toolbar to open the selection box.
      1. Selecteer vervolgens Starten **maken** om de wizard te openen.
   >[!NOTE]
   >
   >In de **Sites**-console kunt u ook de [selectiemodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources) gebruiken om een pagina te selecteren voordat u **Maken** selecteert.
   >
   >Hiermee gebruikt u de geselecteerde pagina als de eerste bronpagina.

1. In de **Uitgezochte Bron** stap moet u Pagina **&#39;s** toevoegen. U kunt meerdere pagina&#39;s selecteren en het pad voor elke pagina opgeven:
   * Navigeer naar de gewenste locatie.
   * Selecteer de bronpagina(&#39;s) en bevestig (vinkje).
   Herhaal deze bewerking zo nodig.

   ![Startebron selecteren](/help/sites-cloud/authoring/assets/launches-select-source.png)

   >[!NOTE]
   >
   >Als u pagina&#39;s en/of vertakkingen wilt toevoegen aan een lancering, moeten deze zich binnen een site bevinden. d.w.z. onder een gemeenschappelijke hoofdmap.
   >
   >Als een site taalwortels onder het bovenste niveau bevat, moeten de pagina&#39;s en vertakkingen voor een introductie zich onder een gemeenschappelijke hoofdtaalbasis bevinden.

1. Voor elk item kunt u opgeven of:

   * **Inclusief subpagina**&#39;s:

      * Geef op of u de opstart wilt maken met of zonder de onderliggende pagina&#39;s.  Deze subpagina&#39;s worden standaard opgenomen.
   Ga verder met **Volgende**.

   ![Startebron selecteren](/help/sites-cloud/authoring/assets/launches-select-source-2.png)

1. In de stap **Eigenschappen** van de wizard kunt u het volgende opgeven:

   * **Titel** starten: De naam van de Launch. De naam moet zinvol zijn voor auteurs.
   * **met bestaande inhoud**: de oorspronkelijke inhoud wordt gebruikt om de opstart te maken.
   * **Gebruik een nieuwe sjabloon om de pagina** te vervangen: Zie Starten [maken met nieuwe sjabloon](#create-launch-with-new-template) voor meer informatie.
   * **Live-gegevens** van bronpagina overnemen: Selecteer deze optie als u de inhoud van startpagina&#39;s automatisch wilt bijwerken wanneer de bronpagina&#39;s veranderen. Met deze optie wordt dit bereikt door van de opstart een live kopie te maken. Deze optie is standaard geselecteerd. <!--Select this option to automatically update the content of launch pages when the source pages change. This option achieves this by making the launch a [live copy](/help/sites-administering/msm.md). By default, this option is selected.-->
   * **Startdatum**: de datum en het tijdstip waarop de lanceerkopie moet worden geactiveerd (afhankelijk van de markering **Productie gereed** ; zie [Launches - de Orde van Gebeurtenissen](/help/sites-cloud/authoring/launches/overview.md#launches-the-order-of-events)).
   ![Starteigenschappen](/help/sites-cloud/authoring/assets/launches-properties.png)

1. Gebruik **Maken** om het proces te voltooien en een nieuwe start te maken. In het bevestigingsvenster wordt u gevraagd of u het programma direct wilt starten.

   Als u de console terugkeert (met **Gedaan**) kunt u uw lancering zien (en toegang hebben) van of:

   * De [**Launches **-console](/help/sites-cloud/authoring/launches/overview.md#the-launches-console)
   * De [**Verwijzingen **in de console van** Plaatsen **](/help/sites-cloud/authoring/launches/overview.md#launches-in-references-sites-console)

### Starten met nieuwe sjabloon maken {#create-launch-with-new-template}

Bij het maken van een opstart kunt u opgeven of u een nieuwe sjabloon wilt gebruiken:

>[!NOTE]
>
>Deze optie is alleen beschikbaar wanneer u een site start via de **Sites** -console. Deze functie is niet beschikbaar wanneer u een opstart maakt via de **opstartconsole** .

![Starten met een nieuwe sjabloon maken](/help/sites-cloud/authoring/assets/launches-create-new-template.png)

Selecteer deze optie:

* Werk de andere beschikbare opties bij,
* Neem een nieuwe stap op waar u de vereiste sjabloon kunt selecteren.

![Een nieuwe sjabloon selecteren](/help/sites-cloud/authoring/assets/launches-select-template.png)

>[!CAUTION]
>
>Aangezien een andere sjabloon wordt gebruikt, is de nieuwe pagina leeg. Vanwege de verschillende paginastructuur wordt er geen inhoud over gekopieerd.
>
>Dit mechanisme kan worden gebruikt om het malplaatje van een [bestaande pagina](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#creating-a-new-page) te veranderen - hoewel het verlies van inhoud moet worden overwogen.

### Een geneste start maken {#creating-a-nested-launch}

Door een geneste opstart te maken (opstart binnen een opstart) kunt u een opstart maken op basis van een bestaande opstart, zodat ontwerpers kunnen profiteren van de wijzigingen die al zijn aangebracht, in plaats van meerdere keren dezelfde wijzigingen te moeten doorvoeren voor elke opstart.

>[!NOTE]
>
>Zie ook [Geneste opstart](/help/sites-cloud/authoring/launches/promoting.md#promoting-a-nested-launch)bevorderen.

#### Een geneste start maken - Opstartconsole {#creating-a-nested-launch-launches-console}

Het maken van een geneste opstart vanuit de **Launches** -console is in principe hetzelfde als het maken van een andere opstartafbeelding, met uitzondering dat u naar de opstartaftakking moet navigeren `/content/launches`:

1. Selecteer in de **Launches** -console **Maken**.
1. Selecteer **Pagina&#39;s toevoegen** en ga naar de startvertakking door `/content/launches` in het filter op te geven. Selecteer de vereiste start en bevestig dit met **Selecteren**:

   ![Een geneste start maken](/help/sites-cloud/authoring/assets/launches-create-nested.png)

1. Ga door met **Volgende** en voltooi de **eigenschappen** zoals bij elke andere lancering.

   ![Bron selecteren voor geneste start](/help/sites-cloud/authoring/assets/launches-create-nested-select.png)

#### Een geneste start maken - Sites-console {#creating-a-nested-launch-sites-console}

Een geneste start maken via de **Sites** -console op basis van een bestaande introductie:

1. Heb toegang tot de [Lancering van Verwijzingen (de console van Plaatsen)](/help/sites-cloud/authoring/launches/overview.md#launches-in-references-sites-console) om de beschikbare acties te tonen.
1. Selecteer **Start maken** om de wizard te openen (aangezien de bron al is geselecteerd, wordt de stap **Bron selecteren** overgeslagen).
1. Voer de **opstarthandleiding** en alle andere vereiste gegevens in (zoals bij een normale opstart).
1. Gebruik **Maken** om het proces te voltooien en een nieuwe start te maken. In het bevestigingsvenster wordt u gevraagd of u het programma direct wilt starten.

Als u **Gereed** selecteert, keert u terug naar het spoor met **Referenties** van de **Sites**-console. Als u de juiste pagina selecteert, wordt de nieuwe startpagina weergegeven.

### Een Starten verwijderen {#deleting-a-launch}

U kunt een lancering van de [lanceringsconsole](/help/sites-cloud/authoring/launches/overview.md#the-launches-console)schrappen:

* Selecteer de start door op de miniatuur te tikken of te klikken.
* De werkbalk wordt weergegeven. Selecteer Verwijderen.
* Bevestig de handeling.

>[!CAUTION]
>
>Als u een opstart verwijdert, wordt de opstart zelf en alle afstammende geneste opstarties verwijderd.
