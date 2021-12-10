---
title: 'Hoe een adaptief formulier in een pagina met AEM sites insluiten? '
description: U kunt Adaptieve Forms insluiten in AEM sitepagina's. Gebruikers kunnen formulieren invullen en verzenden zonder de sitepagina's te verlaten.
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '940'
ht-degree: 0%

---


# Een adaptief formulier insluiten in AEM sitepagina {#embed-an-adaptive-form-or-interactive-communication-in-aem-sites-page}

[!DNL AEM Forms] Hiermee kunnen formulierontwikkelaars Adaptieve Forms naadloos insluiten in een AEM Sites-pagina of een webpagina die buiten AEM wordt gehost. Het ingesloten adaptieve formulier is volledig functioneel en gebruikers kunnen het formulier invullen en verzenden zonder de pagina te verlaten. Hiermee kan de gebruiker in de context van andere elementen op de webpagina blijven en tegelijkertijd met het formulier communiceren.

<!-- For information about embedding an Adaptive Form in an external web page, see [Embed Adaptive Form in external web page](/help/forms/using/embed-adaptive-form-external-web-page.md). -->

Op de AEM Sites-pagina kunt u een adaptief formulier toevoegen met:

* **[[!DNL AEM Forms] Containercomponent](#af-component)**
   [!DNL AEM Forms] biedt een component die u aan uw sitepagina&#39;s kunt toevoegen. De [!DNL AEM Forms] Met de component Container kunt u een adaptief formulier insluiten.

* **[Middelenbrowser](/help/forms/using/embed-adaptive-form-aem-sites.md#asset-browser)**
Alle formulieren die u maakt, zijn beschikbaar onder Elementen. U kunt het formulier slepen en neerzetten als middel op de pagina.

## Vereisten {#prerequisites}

Als u een adaptief formulier wilt insluiten in een AEM sitepagina waarop een bewerkbare sjabloon wordt gebruikt, moet u ervoor zorgen dat de AEM formuliercomponent is geconfigureerd als een toegestane component in de bijbehorende sjabloon. Zie voor meer informatie **Beleid en eigenschappen (container met layout)** sectie in [Paginasjablonen maken](/help/sites-authoring/templates.md).

In het geval van een pagina van Plaatsen die een statisch malplaatje gebruikt, moet u het in het paragraafsysteem van de plaatspagina vormen. Zie [Componenten configureren in ontwerpmodus](/help/sites-authoring/default-components-designmode.md) voor meer informatie .

## Een adaptief formulier insluiten  {#af-component}

Een adaptief formulier insluiten met [!DNL AEM Forms] Containercomponent:

1. Open de pagina AEM sites in de bewerkingsmodus waarin u een adaptief formulier wilt insluiten.
1. Sleep vanuit het deelvenster Componentbrowser de knop [!DNL AEM Forms] Containercomponent op de pagina.

   U kunt ook naar een adaptief formulier zoeken in de middelenbrowser en het naar de sitepagina slepen. Het formulier wordt ingesloten in een [!DNL AEM Forms] Container.

   >[!NOTE]
   >
   >Meerdere [!DNL AEM Forms] Containercomponenten op een pagina worden niet ondersteund.

1. Tik op het ingesloten [!DNL AEM Forms] Containercomponent op de sitepagina en tik vervolgens op ![settings_icon](assets/settings_icon.png) op de actiebalk. De **[!UICONTROL Edit AEM Forms Container]** wordt geopend.
1. In het dialoogvenster Bewerken [!DNL AEM Forms] Geef het volgende op in het dialoogvenster Container.

   * **Type element:** Selecteer het type element dat u wilt insluiten. De opties zijn Adaptief formulier
   * **Middelpad**: Blader naar het adaptieve formulier dat u wilt insluiten en selecteer dit. Deze wordt automatisch ingevuld als u deze uit de middelenbrowser hebt verwijderd.
   * (Alleen adaptief formulier) **Verzending na verzending**: Selecteer de actie die moet worden geactiveerd bij het verzenden van het formulier. U kunt ervoor kiezen om een bedankbericht of een pagina voor bedankt weer te geven.

      * **Bericht van dank**: Schrijf een bericht met de teksteditor Rich die moet worden weergegeven bij het verzenden van formulieren. Deze optie is alleen beschikbaar als u een bedankbericht wilt weergeven.
      * **Dankbriefje**: Blader en selecteer de pagina die u wilt weergeven bij het verzenden van het formulier. Deze optie is alleen beschikbaar wanneer u een pagina voor bedankt weergeeft.
      * **Pagina bij verzending vernieuwen**: Schakel deze optie in om de pagina met het ingesloten adaptieve formulier te vernieuwen en de pagina voor bedankt weer te geven. Anders vervangt de pagina Hartelijk dank het Adaptief formulier in het dialoogvenster [!DNL AEM Forms] container, zonder de pagina te vernieuwen. Deze optie is alleen beschikbaar wanneer u een pagina voor bedankt weergeeft.
   * **Thema**: Selecteer een thema waarmee u opmaak definieert voor componenten van uw adaptieve formulier. Stijlen omvat vormgevingseigenschappen zoals letterstijl, achtergrondkleur, afmetingen en uitlijning.
   * **Hoogte**: Geef de hoogte van de container op. Laat deze leeg om de grootte van de container automatisch te wijzigen.
   * **CSS-clientbibliotheek**: Geef het pad naar een CSS-clientbibliotheek op.


1. Sla de instellingen op. Het adaptieve formulier is nu ingesloten in de pagina.

## Ingesloten adaptief formulier publiceren {#publishing-embedded-adaptive-form}

Neem de volgende scenario&#39;s in overweging voor het publiceren van een ingesloten element (adaptief formulier) op AEM sitepagina:

* Als u de pagina met AEM sites voor het eerst publiceert en deze een ingesloten adaptief formulier bevat, publiceert u de pagina met sites en het ingesloten element.
* Als u alleen het ingesloten adaptieve formulier hebt gewijzigd in een gepubliceerde sitepagina, publiceert u het oorspronkelijke element en de wijzigingen worden weerspiegeld in de gepubliceerde sitepagina. De gepubliceerde sitepagina bevat een verwijzing naar het element en de pagina hoeft niet opnieuw te worden gepubliceerd.
* Als u de sitepagina en het ingesloten adaptieve formulier hebt gewijzigd, publiceert u de sitepagina en het ingesloten element opnieuw.

## Ingesloten adaptief formulier wijzigen {#modifying-embedded-adaptive-form-and-interactive-communication}

Op de pagina AEM sites wordt een verwijzing naar het adaptieve formulier bijgehouden in het gedeelte [!DNL AEM Forms] Container. Daarom blijven alle configuraties en eigenschappen, zoals het thema, de stijlen en de verzendactie, die in het oorspronkelijke adaptieve formulier zijn geconfigureerd, behouden in het ingesloten adaptieve formulier.

Voer een van de volgende handelingen uit om een configuratie of eigenschap van het ingesloten adaptieve formulier te wijzigen.

* Open het oorspronkelijke formulier in Adaptive Forms in de respectievelijke editors en wijzig deze.
* Tik in de bewerkingsmodus op het adaptieve formulier en tik vervolgens op **[!UICONTROL Edit in a new window]**. Het oorspronkelijke formulier wordt geopend in de bewerkingsmodus die u kunt wijzigen.

>[!NOTE]
>
>De wijzigingen die in het oorspronkelijke adaptieve formulier zijn aangebracht, worden automatisch doorgevoerd in het ingesloten formulier. Publiceer echter het adaptieve formulier of de sitepagina opnieuw om de wijzigingen in de gepubliceerde pagina weer te geven.

## Overwegingen en beste praktijken {#considerations-and-best-practices}

Houd rekening met de volgende punten wanneer u Adaptive Forms insluit in AEM sitepagina&#39;s:

* Koptekst en voettekst in het oorspronkelijke formulier worden niet opgenomen in het ingesloten formulier.
* Concepten en opmerkingen van gebruikers met ingesloten formulieren worden ondersteund en kunnen worden weergegeven op de tabbladen Concepten en Verzonden Forms op de portal Formulieren.
* De verzendactie die op het oorspronkelijke formulier is geconfigureerd, blijft behouden in het ingesloten formulier.
* De ervaring die het richten en A/B tests die op de originele vorm worden gevormd werkt niet in de ingebedde vorm richten. U kunt echter de pagina Sites gebruiken om verschillende formulieren weer te geven op basis van gebruikersprofielen.
* Als u Adobe Analytics hebt geconfigureerd voor het oorspronkelijke formulier, worden de analysegegevens van het ingesloten formulier vastgelegd in Adobe Analytics. Het is echter niet beschikbaar in het rapport Formulieranalyse.

