---
title: Een adaptief formulier insluiten in AEM Sites-pagina
seo-title: Hwo to add an Adaptive Form to an AEM Sites page?
description: U kunt de AEM Forms Container-component gebruiken om adaptieve Forms toe te voegen aan of in te sluiten op een AEM Sites-pagina om een formulier in te vullen en te verzenden zonder de AEM Sites-pagina's te verlaten.
feature: Adaptive Forms
source-git-commit: dac38b2a90b2a1969e5332b8a658e8f1e0e5eccb
workflow-type: tm+mt
source-wordcount: '1027'
ht-degree: 0%

---

# Een adaptief formulier insluiten op een pagina met AEM sites {#embed-an-adaptive-form-to-aem-sites-page}

## Overzicht {#overview}

Met AEM Forms kunnen ontwikkelaars van formulieren adaptieve formulieren naadloos insluiten in een AEM Sites-pagina of een webpagina die buiten AEM wordt gehost. Het ingesloten adaptieve formulier is volledig functioneel en gebruikers kunnen het formulier invullen en verzenden zonder de pagina te verlaten. Hiermee kan de gebruiker in de context van andere elementen op de webpagina blijven en tegelijkertijd met het formulier communiceren.

<!-- For information about embedding an Adaptive Form in an external web page, see [Embed Adaptive Form in external web page](/help/forms/using/embed-adaptive-form-external-web-page.md). -->

Op de AEM Sites-pagina kunt u een adaptief formulier toevoegen met:

* **[AEM Forms Container-component](/help/forms/using/embed-adaptive-form-aem-sites.md#af-component)**
AEM Forms biedt een component die u aan uw sitepagina&#39;s kunt toevoegen. Met de AEM Forms Container-component kunt u een adaptief formulier insluiten.

* **[Middelenbrowser](/help/forms/using/embed-adaptive-form-aem-sites.md#asset-browser)**
Alle formulieren zijn beschikbaar onder Elementen. U kunt het formulier slepen en neerzetten als middel op de pagina.

## Vereisten {#prerequisites}

Als u een adaptief formulier wilt insluiten in een AEM Sites-pagina waarop een bewerkbare sjabloon wordt gebruikt, moet u ervoor zorgen dat de component AEM formulier is geconfigureerd als een toegestane component in de gekoppelde sjabloon. Zie voor meer informatie **Beleid en eigenschappen (container met layout)** sectie in [Paginasjablonen maken](/help/sites-authoring/templates.md).

In het geval van een pagina van Plaatsen die een statisch malplaatje gebruikt, moet u het in het paragraafsysteem van de plaatspagina vormen. Zie [Componenten configureren in ontwerpmodus](/help/sites-authoring/default-components-designmode.md) voor meer informatie .

## Een adaptief formulier insluiten {#af-component}

Een adaptief formulier insluiten met AEM Forms Container-component:

1. Open de pagina AEM sites in de bewerkingsmodus waarin u een adaptief formulier wilt insluiten.
1. Sleep vanuit het deelvenster Componentbrowser de AEM Forms Container-component naar de pagina. U kunt ook naar een adaptief formulier zoeken in de middelenbrowser en het naar de sitepagina slepen. Het formulier wordt ingesloten in een AEM Forms-container. U kunt een nieuw adaptief formulier maken en toevoegen of een bestaand adaptief formulier insluiten.

   >[!NOTE]
   >
   >Meerdere AEM Forms Container-componenten op een pagina worden niet ondersteund.

1. Tik op de werkbalk van de component op de knop **Formulier maken** pictogram. Er wordt een venster geopend waarin het nieuwe formulier wordt gemaakt.

1. Tik op de ingesloten AEM Forms Container-component op de sitepagina en tik vervolgens op ![settings_icon](assets/settings_icon.png) op de actiebalk. De **[!UICONTROL Edit AEM Forms Container]** wordt geopend.
1. Geef het volgende op in het dialoogvenster AEM Forms-container bewerken.

   <!-- * **Asset Type:** Select the type of asset to embed. The options are Adaptive Form -->
   * **Middelpad**: Blader naar het adaptieve formulier dat u wilt insluiten en selecteer dit. Deze wordt automatisch ingevuld als u deze uit de middelenbrowser hebt verwijderd.
   * **Verzending na verzending** : Selecteer de actie die moet worden geactiveerd bij het verzenden van het formulier. U kunt ervoor kiezen om een bedankbericht of een pagina voor bedankt weer te geven.

      * **Bericht van dank**: Schrijf een bericht met de teksteditor Rich die moet worden weergegeven bij het verzenden van formulieren. Deze optie is alleen beschikbaar als u een bedankbericht wilt weergeven.
      * **Dankbriefje**: Blader en selecteer de pagina die u wilt weergeven bij het verzenden van het formulier. Deze optie is alleen beschikbaar wanneer u een pagina voor bedankt weergeeft.
         * **Doorverwijzen naar pagina voor bedankt**: Schakel deze optie in om de pagina met het ingesloten adaptieve formulier te vervangen door de pagina Hartelijk dank. Anders vervangt de pagina Bedankt het Adaptief formulier in de AEM Forms-container, zonder de onderliggende sites op de pagina te vernieuwen. Deze optie is alleen beschikbaar wanneer u een pagina voor bedankt weergeeft.
   * **Paginataal gebruiken**: Gebruik de lokale versie van de AEM Sites-pagina in plaats van de landinstelling Adaptief formulier.
   * **Focus op formulier instellen**: Selecteer deze optie om de focus in te stellen op het eerste veld van het adaptieve formulier.

   * **Thema**: Selecteer een thema waarmee u opmaak definieert voor componenten van uw adaptieve formulier. Stijlen omvat vormgevingseigenschappen zoals letterstijl, achtergrondkleur, afmetingen en uitlijning.
   * **Hoogte**: Geef de hoogte van de container op. Laat deze leeg om de grootte van de container automatisch te wijzigen.
   * **CSS-clientbibliotheek**: Geef het pad naar een CSS-clientbibliotheek op.

1. Sla de instellingen op. Het adaptieve formulier is nu ingesloten in de pagina.

## Ingesloten adaptief formulier publiceren {#publishing-embedded-adaptive-form}

Overweeg de volgende scenario&#39;s voor het publiceren van een ingebedde Aangepaste Vorm in AEM plaatspagina:

* Als u de pagina met AEM sites voor het eerst publiceert en deze een ingesloten adaptief formulier bevat, publiceert u de pagina met sites en het ingesloten element.
* Als u alleen het ingesloten adaptieve formulier hebt gewijzigd in een gepubliceerde sitepagina, publiceert u het oorspronkelijke element en de wijzigingen worden weerspiegeld in de gepubliceerde sitepagina. De gepubliceerde sitepagina bevat een verwijzing naar het element en de pagina hoeft niet opnieuw te worden gepubliceerd.
* Als u de sitepagina en het ingesloten adaptieve formulier hebt gewijzigd, publiceert u de sitepagina en het ingesloten element opnieuw.

## Ingesloten adaptief formulier wijzigen  {#modifying-embedded-adaptive-form}

Op AEM sitepagina wordt een verwijzing naar het adaptieve formulier bijgehouden in de AEM Forms-container. Daarom blijven alle configuraties en eigenschappen die in het oorspronkelijke adaptieve formulier zijn geconfigureerd, zoals het thema, de stijlen en de verzendactie, behouden in het ingesloten adaptieve formulier.

Voer een van de volgende handelingen uit om een configuratie of eigenschap van het ingesloten adaptieve formulier te wijzigen.

* Open het oorspronkelijke formulier in adaptieve formulieren in de respectieve editors en wijzig deze.
* Tik in de bewerkingsmodus op het adaptieve formulier en tik vervolgens op **[!UICONTROL Edit in a new window]**. Het oorspronkelijke formulier wordt geopend in de bewerkingsmodus die u kunt wijzigen.

>[!NOTE]
>
>De wijzigingen die in het oorspronkelijke adaptieve formulier zijn aangebracht, worden automatisch doorgevoerd in het ingesloten formulier. Publiceer echter het adaptieve formulier of de sitepagina opnieuw om de wijzigingen in de gepubliceerde pagina weer te geven.

## Overwegingen en beste praktijken {#considerations-and-best-practices}

Houd rekening met de volgende punten wanneer u adaptieve formulieren insluit in AEM sitepagina&#39;s:

* Koptekst en voettekst in het oorspronkelijke formulier worden niet opgenomen in het ingesloten formulier.
* Concepten en opmerkingen van gebruikers met ingesloten formulieren worden ondersteund en kunnen worden weergegeven op de tabbladen Concepten en Verzonden Forms op de portal Formulieren.
* De verzendactie die op het oorspronkelijke formulier is geconfigureerd, blijft behouden in het ingesloten formulier.
* De ervaring die het richten en A/B tests die op de originele vorm worden gevormd werkt niet in de ingebedde vorm richten. U kunt echter de pagina Sites gebruiken om verschillende formulieren weer te geven op basis van gebruikersprofielen.
* Als u Adobe Analytics hebt geconfigureerd voor het oorspronkelijke formulier, worden de analysegegevens van het ingesloten formulier vastgelegd in Adobe Analytics. Het is echter niet beschikbaar in het rapport Formulieranalyse.
