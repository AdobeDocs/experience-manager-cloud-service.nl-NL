---
title: Een adaptief formulier insluiten in AEM Sites-pagina
seo-title: Hwo to add an Adaptive Form to an AEM Sites page?
description: Met de component Adaptive Forms-Embed kunt u Adaptive Forms toevoegen aan of insluiten in een AEM Sites-pagina en zo een formulier invullen en verzenden zonder de AEM Sites-pagina's te verlaten.
feature: Adaptive Forms
exl-id: 359b05e8-d8c1-4a77-9e70-6f6b6e668560
source-git-commit: 2a487654c3af2d2ec3aa43481caed5e1d4fc77a2
workflow-type: tm+mt
source-wordcount: '1132'
ht-degree: 0%

---

# Een adaptief formulier insluiten op een pagina met AEM sites {#embed-an-adaptive-form-to-aem-sites-page}

## Overzicht {#overview}

Met AEM Forms kunnen formulierontwikkelaars de Adaptieve Forms naadloos insluiten in een AEM Sites-pagina of een webpagina die buiten AEM wordt gehost. Het ingesloten adaptieve formulier is volledig functioneel en gebruikers kunnen het formulier invullen en verzenden zonder de pagina te verlaten. Hiermee kan de gebruiker in de context van andere elementen op de webpagina blijven en tegelijkertijd met het formulier communiceren.



<!-- For information about embedding an Adaptive Form in an external web page, see [Embed Adaptive Form in external web page](/help/forms/using/embed-adaptive-form-external-web-page.md). -->

Op de AEM Sites-pagina kunt u een adaptief formulier toevoegen met:

* **Aangepaste Forms - component insluiten**
Met de adaptieve Forms - Embed-component kunnen AEM Sites-auteurs een bestaand adaptief formulier opnemen op een AEM Sites-pagina, waardoor het hergebruik van adaptieve formulieren wordt verbeterd. Bestaande Adaptieve Forms kunnen zelfstandig worden gebruikt of in de sitepagina worden ingesloten. Deze integratie biedt klanten een handige manier om Adaptive Forms die ze al hebben gemaakt opnieuw te gebruiken.

* **Middelenbrowser**
Alle formulieren zijn beschikbaar onder Elementen. U kunt het formulier slepen en neerzetten als middel op de pagina.

## Vereisten {#prerequisites}

Als u een adaptief formulier wilt insluiten in een AEM Sites-pagina waarop een bewerkbare sjabloon wordt gebruikt, moet u ervoor zorgen dat de component AEM formulier is geconfigureerd als een toegestane component in de gekoppelde sjabloon.

In geval van **Aangepaste Forms - component insluiten** is niet zichtbaar in het dialoogvenster **Deelvenster Componentbrowser** van AEM sitepagina voert u de volgende stappen uit, zoals in de video wordt geïllustreerd.

>[!VIDEO](https://video.tv.adobe.com/v/3410544)

Als de pagina van Plaatsen een statisch malplaatje gebruikt, moet u het in het paragraafsysteem van de plaatspagina vormen.

## Een adaptief formulier insluiten {#af-component}

Een adaptief formulier insluiten met de opdracht **[!UICONTROL Adaptive Forms - Embed]** component:

1. Open de pagina AEM sites in de bewerkingsmodus waarin u een adaptief formulier wilt insluiten.
1. Sleep vanuit het deelvenster Componentbrowser de knop [!UICONTROL Adaptive Forms - Embed] op de pagina. U kunt ook naar een adaptief formulier zoeken in de middelenbrowser en het naar de sitepagina slepen. U kunt een nieuw adaptief formulier toevoegen of een bestaand adaptief formulier insluiten.

   >[!NOTE]
   >
   >Meerdere adaptieve Forms - Insluitcomponenten op een pagina worden niet ondersteund.

1. Tik op de werkbalk van de component op de knop **Formulier maken** pictogram. Er wordt een venster geopend waarin u het formulier kunt maken.

1. Tik op de ingesloten component Adaptief Forms - Insluiten op de sitepagina en tik vervolgens op ![settings_icon](assets/settings_icon.png) op de actiebalk. De **[!UICONTROL Edit Adaptive Forms - Embed]** wordt geopend.
1. Geef het volgende op in het dialoogvenster Aangepaste Forms bewerken - Insluiten.

   **Type element:** Selecteer het type element dat u wilt insluiten.
   * **Middelpad**: Blader naar het adaptieve formulier dat u wilt insluiten en selecteer dit. Deze wordt automatisch ingevuld als u deze uit de middelenbrowser hebt verwijderd.
   * **Verzending na verzending** : Selecteer de actie die moet worden geactiveerd bij het verzenden van het formulier. U kunt ervoor kiezen om een bedankbericht of een pagina voor bedankt weer te geven.
      * Tonen

      * **Bericht van dank**: Schrijf een bericht met de teksteditor Rich die moet worden weergegeven bij het verzenden van formulieren. Deze optie is alleen beschikbaar als u een bedankbericht wilt weergeven.
      * **Dankbriefje**: Blader en selecteer de pagina die u wilt weergeven bij het verzenden van het formulier. Deze optie is alleen beschikbaar wanneer u een pagina voor bedankt weergeeft.
         * **Doorverwijzen naar pagina voor bedankt**: Schakel deze optie in om de pagina met het ingesloten adaptieve formulier te vervangen door de pagina Hartelijk dank. Anders vervangt de pagina Hartelijk dank het Adaptief formulier in het dialoogvenster [!UICONTROL Adaptive Forms - Embed] zonder onderliggende sites op de pagina te vernieuwen. Deze optie is alleen beschikbaar wanneer u een pagina voor bedankt weergeeft.
   * **Paginataal gebruiken**: Gebruik de lokale versie van de AEM Sites-pagina in plaats van de landinstelling Adaptief formulier.
   * **Focus op formulier instellen**: Selecteer deze optie om de focus in te stellen op het eerste veld van het adaptieve formulier.
   * **Thema**: Selecteer een thema waarmee u opmaak definieert voor componenten van uw adaptieve formulier. Stijlen omvat vormgevingseigenschappen zoals letterstijl, achtergrondkleur, afmetingen en uitlijning.
   * **Het formulier bedekt de volledige breedte van het kader**: Als deze optie is ingeschakeld, wordt iframe niet gebruikt om het formulier te genereren.
   * **Hoogte**: Geef de hoogte van de container op. Laat deze leeg om de grootte van de container automatisch te wijzigen.
   * **CSS-clientbibliotheek**: Geef het pad naar een CSS-clientbibliotheek op.

1. Sla de instellingen op. Het adaptieve formulier is nu ingesloten in de pagina.

Met AEM site kunt u ook direct een adaptief formulier maken met de component Adaptief Forms - Insluiten. Voer de stappen uit om een adaptief formulier te maken met de opdracht **Aangepaste Forms - component insluiten** op AEM pagina met sites:
1. Open de pagina AEM sites in de bewerkingsmodus waarin u een adaptief formulier wilt insluiten.
1. Sleep vanuit het deelvenster Componentbrowser de component Adaptief Forms - Insluiten op de pagina.
1. Klik op de knop **Plus** en wordt u omgeleid naar de wizard Formulier maken.

   ![Adaptieve Forms - component insluiten](/help/forms/assets/aemformcontainer.png)

1. U kunt nu een adaptief formulier insluiten op AEM sitepagina&#39;s met de opdracht [!UICONTROL AEM Forms Container Component].

## Ingesloten adaptief formulier publiceren {#publishing-embedded-adaptive-form}

Overweeg de volgende scenario&#39;s voor het publiceren van een ingebedde Aangepaste Vorm in AEM plaatspagina:

* Als u de pagina met AEM sites voor het eerst publiceert en deze een ingesloten adaptief formulier bevat, publiceert u de pagina met sites en het ingesloten element.
* Als u alleen het ingesloten adaptieve formulier hebt gewijzigd in een gepubliceerde sitepagina, publiceert u het oorspronkelijke element en de wijzigingen worden weerspiegeld in de gepubliceerde sitepagina. De gepubliceerde sitepagina bevat een verwijzing naar het element en de pagina hoeft niet opnieuw te worden gepubliceerd.
* Als u de sitepagina en het ingesloten adaptieve formulier hebt gewijzigd, publiceert u de sitepagina en het ingesloten element opnieuw.

## Ingesloten adaptief formulier wijzigen  {#modifying-embedded-adaptive-form}

Op AEM sitepagina wordt een verwijzing naar het adaptieve formulier bijgehouden in de Adaptive Forms - Embed. Daarom blijven alle configuraties en eigenschappen die in het oorspronkelijke adaptieve formulier zijn geconfigureerd, zoals het thema, de stijlen en de verzendactie, behouden in het ingesloten adaptieve formulier.

Voer een van de volgende handelingen uit om een configuratie of eigenschap van het ingesloten adaptieve formulier te wijzigen.

* Open het oorspronkelijke formulier in adaptieve formulieren in de respectieve editors en wijzig deze.
* Tik in de bewerkingsmodus op het adaptieve formulier en tik vervolgens op **[!UICONTROL Edit in a new window]**. Het oorspronkelijke formulier wordt geopend in de bewerkingsmodus die u kunt wijzigen.

>[!NOTE]
>
>De wijzigingen die in het oorspronkelijke adaptieve formulier zijn aangebracht, worden automatisch doorgevoerd in het ingesloten formulier. Publiceer echter het adaptieve formulier of de sitepagina opnieuw om de wijzigingen in de gepubliceerde pagina weer te geven.

## Overwegingen en beste praktijken {#considerations-and-best-practices}

Houd rekening met de volgende punten wanneer u adaptieve formulieren insluit in AEM sitepagina&#39;s:

* Koptekst en voettekst in het oorspronkelijke formulier worden niet opgenomen in het ingesloten formulier.
* Concepten en opmerkingen van gebruikers met ingesloten formulieren worden ondersteund en kunnen worden weergegeven op de tabbladen Concepten en Verzonden Forms op de Forms Portal.
* De verzendactie die op het oorspronkelijke formulier is geconfigureerd, blijft behouden in het ingesloten formulier.
* Als u Adobe Analytics hebt geconfigureerd voor het oorspronkelijke formulier, worden de analysegegevens van het ingesloten formulier vastgelegd in Adobe Analytics. Het is echter niet beschikbaar in het rapport Formulieranalyse.
