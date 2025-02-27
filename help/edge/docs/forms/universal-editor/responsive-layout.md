---
title: De modus Universal Editor - responsief
description: In dit artikel wordt uitgelegd hoe u een voorbeeld van formulieren kunt bekijken met verschillende emulators in de Universal Editor om hun uiterlijk tijdens het ontwerpen te visualiseren.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 0c7fb491-4bad-4202-a472-87e6e6d9ab40
source-git-commit: 8f5b4d863ab469c44b4c221eab1fb128706b45c7
workflow-type: tm+mt
source-wordcount: '865'
ht-degree: 0%

---

# Responsieve modus in WYSIWYG Authoring

<span class="preview"> Deze functie is beschikbaar via het programma voor vroege toegang. Om toegang te verzoeken, verzend een e-mail van uw officieel adres naar <a href="mailto:aem-forms-ea@adobe.com"> aem-forms-ea@adobe.com </a> met uw GitHub organisatienaam en bewaarplaatsnaam. Bijvoorbeeld, als de bewaarplaats URL https://github.com/adobe/abc is, is de organisatienaam adobe en de bewaarplaatsnaam abc.</span>


De [ Universele Redacteur ](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) staat u toe om voorproef Edge Delivery Services Forms met verschillende mededingers om de blik en het gevoel van de vorm tijdens creatie te zien.

In de responsieve modus kunnen ontwikkelaars lay-outs ontwerpen die automatisch worden aangepast aan verschillende schermgrootten, zoals desktops, tablets en mobiele apparaten. De Universele Redacteur steunt mededingers voor Desktop, tablet, en mobiele apparaten. U kunt de hoogte en breedte instellen op basis van de schermgrootte en de volgende handelingen uitvoeren:

* De richting instellen
* De breedte en hoogte opgeven
* De richting wijzigen

## Forms voorvertonen in responsieve modus voor verschillende apparaten

De Universele Redacteur verstrekt een **Emulator** pictogram dat bij de hoger-juiste hoek van het scherm wordt gevestigd dat u toestaat om pagina&#39;s over verschillende apparatengrootte voor te vertonen en het gedrag van uw ontvankelijk ontwerp voor een betere gebruikerservaring te testen.

Ga als volgt te werk om te zien hoe formulieren in de Universal Editor worden weergegeven op verschillende schermgrootten:

1. Open het formulier in de Universal Editor om het te bewerken.
1. Selecteer het ![ pictogram van de Emulator ](/help/edge/docs/forms/universal-editor/assets/emulator.png) {height=2%, width=2%} beschikbaar op de Universele Toolbar van de Redacteur en klik het emulatorpictogram om de optie te tonen.

   ![ Responsieve Wijze ](/help/edge/docs/forms/universal-editor/assets/universal-editor-emulator.png)

1. Selecteer een optie om een formulier te emuleren in de Universal Editor op een geselecteerd apparaat: Computer, Tablet, Mobiel.

   ![ Responsieve wijze ](/help/edge/docs/forms/universal-editor/assets/ue-responsivemode.png) {width=40%, height=40%}

   Standaard wordt de editor geopend in een computerlay-out, waarbij de hoogte en breedte automatisch worden bepaald door de browser. U kunt ook een formulier emuleren op een mobiel apparaat of tablet. U kunt ook de schermbreedte en -hoogte aanpassen voor aangepaste apparaten.

De Universal Editor biedt verschillende emulators om formulieren voor te vertonen op verschillende apparaten. De onderstaande tabel bevat een overzicht van de beschikbare emulatortypen en de bijbehorende apparaatrepresentaties:

<table border="1" style="text-align:" left; border-collapse: collapse;">
    <tr>
        <th style="width: 20%">Type emulator</th>
        <th style="width: 80%">Apparaatafbeelding</th>
    </tr>
    <tr>
        <td style="width: 20%">Desktop</td>
        <td style="width: 80%"><img src="/help/edge/docs/forms/universal-editor/assets/universal-editor-desktop.png" alt="Emulator voor bureaublad" style="width: auto; height: auto"></td>
    </tr>
    <tr>
        <td style="width: 20%">Tablet</td>
        <td style="width: 80%"><img src="/help/edge/docs/forms/universal-editor/assets/universal-editor-tab.png" alt="Emulator voor tablet" style="width: auto; height: auto"></td>
    </tr>
    <tr>
        <td style="width: 20%">Mobiel</td>
        <td style="width: 80%"><img src="/help/edge/docs/forms/universal-editor/assets/universal-editor-mobile.png" alt="Mobiele emulator" style="width: auto; height: auto"></td>
    </tr>
    <tr>
        <td style="width: 20%">Aangepast apparaat</td>
        <td style="width: 80%"><img src="/help/edge/docs/forms/universal-editor/assets/universal-editor-custom.png" alt="Emulator voor aangepast apparaat" style="width: auto; height: auto"></td>
    </tr>
</table>

U kunt het **pictogram van de Omwenteling van het 1} Scherm gebruiken {om tussen staande en liggende richtingen van een knevel te voorzien wanneer het voorvertonen van een vorm op verschillende apparaten.** Het helpt ontwikkelaars testen hoe het responsieve ontwerp zich aan het schermomwentelingen op diverse apparaten aanpast.

De Universal Editor ondersteunt de verschillende formulierindelingen. Om de verschillende lay-out te onderzoeken, verwijs naar de [ sectie van de Mogelijkheden van de Lay-out ](#layout-capabilities).

## Indelingsmogelijkheden

Met de Universal Editor kunt u gebruiksvriendelijke formulieren maken die eindgebruikers een dynamische ervaring bieden. De formulierindeling bepaalt hoe items of componenten in een formulier worden weergegeven.

De Universal Editor ondersteunt de volgende typen indelingen voor formulieren:
* [Deelvensterlay-out](#panel-layout)
* [Wizard-indeling](#wizard-layout)
* [Accordeonlay-out](#accordion-layout)

### Layout deelvenster

De indeling van deelvensters is handig om verwante velden zo te ordenen dat u gemakkelijker kunt navigeren en de bijbehorende inhoud kunt vinden. In de indeling van het deelvenster worden formuliercomponenten in afzonderlijke secties of deelvensters in formulieren gerangschikt.

![ Lay-out van het Comité ](/help/edge/docs/forms/universal-editor/assets/panel-layout.png)

U kunt de [ paneelcomponent ](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel) gebruiken om de paneellay-out in een vorm toe te voegen. Voor gedetailleerde instructies op hoe te om diverse eigenschappen van de paneelcomponent te vormen, verwijs naar het [ artikel van de paneelcomponent ](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel).

### Wizard Layout


De indeling van de wizard helpt een complex formulier te vereenvoudigen door het op te splitsen in afzonderlijke stappen. Elke stap vertegenwoordigt een verschillend deel van het proces, en de gebruikers navigeren opeenvolgend door de stappen, vaak met **Volgende** en **Achter** knopen. U kunt de indeling van de wizard gebruiken om een formulier te maken dat uit meerdere secties of stappen bestaat.

![ Lay-out van de Tovenaar ](/help/edge/docs/forms/universal-editor/assets/wizard-layout.png)

U kunt de [ tovenaar component ](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard) gebruiken om de tovenaarslay toe te voegen in een vorm. Voor gedetailleerde instructies op hoe te om de diverse eigenschappen van de tovenaarscomponent te vormen, verwijs naar het [ artikel van de tovenaarscomponent ](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard).

### Accordeonlay-out

De accordeonindeling geeft de inhoud in inklapbare secties of deelvensters weer in een adaptief formulier. Wanneer een sectie wordt uitgevouwen, geeft deze de inhoud binnen weer, terwijl andere secties worden samengevouwen. Deze indeling is ideaal voor het weergeven van grote hoeveelheden gegevens in een compacte vorm.

![ Lay-out van de Accordeon ](/help/edge/docs/forms/universal-editor/assets/accordion-layout.png)

U kunt de [ accordeoncomponent ](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion) gebruiken om de accordeonlay-out in een vorm toe te voegen. Voor gedetailleerde instructies op hoe te om de diverse eigenschappen van de accordeoncomponent te vormen, verwijs naar het ](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion) artikel van de component 0} accordeon {.[

### Hoe te om de juiste lay-out te kiezen?

Het is belangrijk om de juiste indeling te selecteren voor een optimale gebruikerservaring en functionaliteit van formulieren. De tabel geeft u inzicht in de verschillende beschikbare lay-outopties en helpt u bij het selecteren van de meest geschikte lay-out op basis van uw specifieke behoeften en gebruikssituaties:

| Functie | Layout deelvenster | Wizard Layout | Accordeonlay-out |
|----------------------|-----------------------------------------------|-----------------------------------------------|-----------------------------------------------|
| **Doel** | Hiermee groepeert u gerelateerde inhoud in afzonderlijke secties | Hiermee worden gebruikers door een proces of formulier met meerdere stappen geleid | Inhoud indelen in inklapbare secties |
| **Structuur** | Afzonderlijke secties | Opeenvolgende stappen/pagina&#39;s | Inklapbare deelvensters/secties |
| **Navigatie** | Klik op de kopteksten van het deelvenster om te navigeren | - Voorwaarts: &quot;Volgende&quot;knoop <br> - Achteruit: &quot;Achtergrond&quot;knoop <br> - Facultatieve het overslaan stappen | Klik op kopteksten om secties uit te vouwen/samen te vouwen |
| **Ervaring van 0} Gebruiker** | Hiermee ordent u grote hoeveelheden inhoud op een beheerbare manier | Stapsgewijze begeleiding, waardoor de overweldigende | Compacte weergave met uitgevouwen/samengevouwen secties |
| **Geval van het Gebruik** | Complexe formulieren met gecategoriseerde secties | Installatieprocessen, complexe formulieren | Veelgestelde vragen, instellingenmenu&#39;s, gedetailleerde inhoudssecties |

## Zie ook

{{universal-editor-see-also}}
