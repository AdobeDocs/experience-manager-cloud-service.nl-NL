---
title: De modus Universal Editor - responsief
description: In dit artikel wordt uitgelegd hoe u een voorbeeld van formulieren kunt bekijken met verschillende emulators in de Universal Editor om hun uiterlijk tijdens het ontwerpen te visualiseren.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 0c7fb491-4bad-4202-a472-87e6e6d9ab40
source-git-commit: 9127c58a72dc4942312907f9e8f0cdcc8de9aa4b
workflow-type: tm+mt
source-wordcount: '1285'
ht-degree: 0%

---


# Responsieve modus in WYSIWYG Authoring

<span class="preview"> Deze functie is beschikbaar via het programma voor vroege toegang. Om toegang te verzoeken, verzend een e-mail met uw GitHub organisatienaam en bewaarplaatsnaam van uw officieel adres aan <a href="mailto:aem-forms-ea@adobe.com"> aem-forms-ea@adobe.com </a>. Bijvoorbeeld, als de bewaarplaats URL https://github.com/adobe/abc is, is de organisatienaam adobe en de bewaarplaatsnaam abc.</span>

## Introductie tot responsieve Forms

In de wereld van vandaag met meerdere apparaten moeten uw formulieren er fantastisch uitzien en goed functioneren op schermen van elke grootte - van desktopmonitoren tot smartphones. Met de responsieve modus in de Universal Editor kunt u dit bereiken door tijdens het ontwerpproces een voorbeeld van uw formulieren te bekijken en uw formulieren te testen op verschillende apparaatgrootten.

De [ Universele Redacteur ](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) laat u toe om vormen tot stand te brengen die automatisch aan verschillende het schermgrootte aanpassen, die een optimale gebruikerservaring ongeacht het apparaat verstrekken dat wordt gebruikt.

## Forms voorvertonen in responsieve modus voor verschillende apparaten

De Universele Redacteur verstrekt een **Emulator** pictogram dat bij de hoger-juiste hoek van het scherm wordt gevestigd dat u toestaat om pagina&#39;s over verschillende apparatengrootte voor te vertonen en het gedrag van uw ontvankelijk ontwerp voor een betere gebruikerservaring te testen.

Een voorbeeld van een formulier weergeven in de responsieve modus:

1. Open het formulier in de Universal Editor om het te bewerken.
2. Klik het ![ pictogram van de Mededinger die een symbool van de apparatenvoorproef ](/help/edge/docs/forms/universal-editor/assets/emulator.png) {height=2%, breedte=2%} in de toolbar tonen.
3. Selecteer een apparaatindeling:
   - Desktop (standaard)
   - Tablet
   - Mobiel
   - Aangepast (breedte en hoogte opgeven)

![ Schermafbeelding van Universele Redacteur die ontvankelijke wijzeopties voor verschillende apparaten tonen ](/help/edge/docs/forms/universal-editor/assets/universal-editor-emulator.png)

U kunt het **pictogram van de Omwenteling van het Scherm {ook gebruiken 0} om tussen staande en landschapsrichtingen van een knevel te voorzien wanneer het voorvertonen op tablet of mobiele apparaten.**

De Universal Editor biedt verschillende emulators om formulieren voor te vertonen op verschillende apparaten. De onderstaande tabel bevat een overzicht van de beschikbare emulatortypen en de bijbehorende apparaatrepresentaties:

<table border="1" style="text-align:" left; border-collapse: collapse;">
    <tr>
        <th style="width: 20%">Type emulator</th>
        <th style="width: 80%">Apparaatafbeelding</th>
    </tr>
    <tr>
        <td style="width: 20%">Desktop</td>
        <td style="width: 80%"><img src="/help/edge/docs/forms/universal-editor/assets/universal-editor-desktop.png" alt="Bureaubladweergave van een formulier met een volledige-breedtelay-out" style="width: auto; height: auto"></td>
    </tr>
    <tr>
        <td style="width: 20%">Tablet</td>
        <td style="width: 80%"><img src="/help/edge/docs/forms/universal-editor/assets/universal-editor-tab.png" alt="Tabletweergave van een formulier met een indeling met gemiddelde breedte en aangepaste componenten" style="width: auto; height: auto"></td>
    </tr>
    <tr>
        <td style="width: 20%">Mobiel</td>
        <td style="width: 80%"><img src="/help/edge/docs/forms/universal-editor/assets/universal-editor-mobile.png" alt="De mobiele weergave van een formulier met een smalle indeling met gestapelde componenten" style="width: auto; height: auto"></td>
    </tr>
    <tr>
        <td style="width: 20%">Aangepast apparaat</td>
        <td style="width: 80%"><img src="/help/edge/docs/forms/universal-editor/assets/universal-editor-custom.png" alt="Aangepaste apparaatweergave van een formulier met door de gebruiker opgegeven afmetingen" style="width: auto; height: auto"></td>
    </tr>
</table>

## Indelingsmogelijkheden

Met de Universal Editor kunt u gebruiksvriendelijke formulieren maken die eindgebruikers een dynamische ervaring bieden. De formulierindeling bepaalt hoe items of componenten in een formulier worden weergegeven.

De Universal Editor ondersteunt de volgende typen indelingen voor formulieren:

- [Deelvensterlay-out](#panel-layout)
- [Wizard-indeling](#wizard-layout)
- [Accordeonlay-out](#accordion-layout)

### Layout deelvenster

De indeling van deelvensters is handig om verwante velden zo te ordenen dat u gemakkelijker kunt navigeren en de bijbehorende inhoud kunt vinden. In de indeling van het deelvenster worden formuliercomponenten in afzonderlijke secties of deelvensters gerangschikt in formulieren.

![ lay-out van het Comité die veelvoudige verschillende secties binnen een vorm tonen ](/help/edge/docs/forms/universal-editor/assets/panel-layout.png)

**Voorbeeld:** de vorm van de baantoepassing zou panelen kunnen gebruiken om &quot;Persoonlijke Informatie,&quot;Onderwijs,&quot;&quot;Ervaring van het Werk,&quot;en &quot;Verwijzingen&quot;in verschillende secties te scheiden.

**Reactiegedrag:** op kleinere schermen, stapelen de panelen typisch verticaal, die hun verschillende groeperingen handhaven terwijl het aanpassen aan de lagere breedte.

U kunt de [ paneelcomponent ](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel) gebruiken om de paneellay-out in een vorm toe te voegen. Voor gedetailleerde instructies op hoe te om diverse eigenschappen van de paneelcomponent te vormen, verwijs naar het [ artikel van de paneelcomponent ](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel).

### Wizard Layout

De indeling van de wizard helpt een complex formulier te vereenvoudigen door het op te splitsen in afzonderlijke stappen. Elke stap vertegenwoordigt een verschillend deel van het proces, en de gebruikers navigeren opeenvolgend door de stappen, vaak met **Volgende** en **Achter** knopen. U kunt de indeling van de wizard gebruiken om een formulier te maken dat uit meerdere secties of stappen bestaat.

![ lay-out die van de Tovenaar een multi-step vorm met navigatiecontroles toont ](/help/edge/docs/forms/universal-editor/assets/wizard-layout.png)

**Voorbeeld:** Een vorm van de verzekeringseis zou een tovenaar kunnen gebruiken om gebruikers door het verstrekken van inherente details te begeleiden, bewijsmateriaal te uploaden, persoonlijke informatie in te gaan, en de voorlegging te herzien.

**Responsief gedrag:** op mobiele apparaten, handhaaft de tovenaar zijn geleidelijke benadering maar past de inhoud binnen elke stap aan om het smallere scherm te passen, vaak stapelend elementen die zij aan zij op grotere schermen zouden verschijnen.

U kunt de [ tovenaar component ](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard) gebruiken om de tovenaarslay toe te voegen in een vorm. Voor gedetailleerde instructies op hoe te om de diverse eigenschappen van de tovenaarscomponent te vormen, verwijs naar het [ artikel van de tovenaarscomponent ](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard).

### Accordeonlay-out

De accordeonindeling geeft de inhoud in inklapbare secties of deelvensters weer in een adaptief formulier. Wanneer een sectie wordt uitgevouwen, geeft deze de inhoud binnen weer, terwijl andere secties worden samengevouwen. Deze indeling is ideaal voor het weergeven van grote hoeveelheden gegevens in een compacte vorm.

![ de lay-out van de Accordeon die uitbreidbare secties in een vorm tonen ](/help/edge/docs/forms/universal-editor/assets/accordion-layout.png)

**Voorbeeld:** de vorm van de productconfiguratie van A zou harmoniesecties voor &quot;Basisopties,&quot;Geavanceerde Eigenschappen,&quot;Accessoires,&quot;en &quot;Betalingsplannen kunnen gebruiken,&quot;toestaand gebruikers om zich op één aspect in een tijd te concentreren.

**Responsief gedrag:** het werk van Accordeons in het bijzonder goed op mobiele apparaten aangezien zij natuurlijk verticale ruimte door slechts de uitgebreide inhoudssectie te tonen besparen, die hen ideaal maken voor kleinere schermen.

U kunt de [ accordeoncomponent ](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion) gebruiken om de accordeonlay-out in een vorm toe te voegen. Voor gedetailleerde instructies op hoe te om de diverse eigenschappen van de accordeoncomponent te vormen, verwijs naar het [&#128279;](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion) artikel van de component 0&rbrace; accordeon &lbrace;.

### Hoe te om de juiste lay-out te kiezen?

Het is belangrijk om de juiste indeling te selecteren voor een optimale gebruikerservaring en functionaliteit van formulieren. De tabel geeft u inzicht in de verschillende beschikbare lay-outopties en helpt u bij het selecteren van de meest geschikte lay-out op basis van uw specifieke behoeften en gebruikssituaties:

| Functie | Layout deelvenster | Wizard Layout | Accordeonlay-out |
|----------------------|-----------------------------------------------|-----------------------------------------------|-----------------------------------------------|
| **Doel** | Hiermee groepeert u gerelateerde inhoud in afzonderlijke secties | Hiermee worden gebruikers door een proces of formulier met meerdere stappen geleid | Inhoud indelen in inklapbare secties |
| **Structuur** | Afzonderlijke secties | Opeenvolgende stappen/pagina&#39;s | Inklapbare deelvensters/secties |
| **Navigatie** | Klik op de kopteksten van het deelvenster om te navigeren | - Voorwaarts: &quot;Volgende&quot;knoop <br> - Achteruit: &quot;Achtergrond&quot;knoop <br> - Facultatieve het overslaan stappen | Klik op kopteksten om secties uit te vouwen/samen te vouwen |
| **Ervaring van 0&rbrace; Gebruiker** | Hiermee ordent u grote hoeveelheden inhoud op een beheerbare manier | Stapsgewijze begeleiding, waardoor de overweldigende | Compacte weergave met uitgevouwen/samengevouwen secties |
| **Geval van het Gebruik** | Complexe formulieren met gecategoriseerde secties | Installatieprocessen, complexe formulieren | Veelgestelde vragen, instellingenmenu&#39;s, gedetailleerde inhoudssecties |
| **Best voor mobiel** | Modern - panelen worden verticaal gestapeld | Goed - alleen de huidige stap wordt actief | Uitstekend - ruimte met inklapbare gedeelten behouden |

## Aanbevolen procedures voor responsieve Forms

Volg de onderstaande aanbevolen procedures om ervoor te zorgen dat uw formulieren op alle apparaten de beste ervaring bieden:

1. **Ontwerp voor mobiel eerst:** Begin door uw vorm voor mobiele apparaten te ontwerpen, dan verbetert voor grotere schermen. Deze benadering zorgt ervoor dat de kernfunctionaliteit op de kleinste schermen werkt.

2. **Gebruik aangewezen gebiedstypes:** kies gebiedstypes die goed op aanrakingsapparaten werken:
   - Vervolgkeuzelijsten gebruiken in plaats van keuzerondjes als er veel opties zijn
   - Datumkiezers gebruiken die zijn ontworpen voor aanraakinvoer
   - Zorg ervoor dat de knoppen en aanraakdoelen ten minste 44px x 44px zijn

3. **vereenvoudig voor kleinere schermen:**
   - Minder velden per rij weergeven op mobiele apparaten
   - U kunt optionele velden verbergen achter de optie Meer weergeven
   - Complexe formulieren onderbrengen in meer stappen op mobiele apparaten

4. **Test grondig:** test altijd uw vormen op daadwerkelijke apparaten of gebruikend de emulatorwijze in Universele Redacteur om ervoor te zorgen zij behoorlijk over schermgrootte functioneren.

5. **overweeg ladingstijden:** optimaliseer beeldgrootte en minimaliseer vereiste middelen, vooral voor mobiele gebruikers die langzamere verbindingen kunnen hebben.

## Problemen met responsieve Forms oplossen

| Probleem | Mogelijke oorzaak | Oplossing |
|-------|---------------|----------|
| Formulier wordt afgesloten op mobiele apparaten | Problemen met vaste breedte of overloop | Relatieve eenheden (%, rem) gebruiken in plaats van pixels en controleren op overloop:verborgen eigenschappen |
| Aanraakelementen die moeilijk te gebruiken zijn | Aanraakdoelen te klein of te dicht | De knoop/de inputgrootte van de verhoging tot minstens 44px 44px en voegt meer ruimte tussen interactieve elementen toe |
| Inhoud overloopt op kleine schermen | Geen responsieve regels voor kleinere viewports | Mediaquery&#39;s of responsklassen toevoegen om de lay-out voor verschillende schermgrootten aan te passen |
| Formulier te langzaam op mobiele apparaten | Grote afbeeldingen of buitensporige scripts | Afbeeldingen optimaliseren, JavaScript minimaliseren en lazy laden voor niet-kritieke elementen overwegen |
| Verschillende weergave tussen emulator en echte apparaten | Browserspecifieke rendering of apparaatvariaties | Test waar mogelijk op echte apparaten, niet alleen emulators |

## Zie ook

{#see-more-eds-forms}
