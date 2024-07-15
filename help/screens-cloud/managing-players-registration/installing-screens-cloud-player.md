---
title: Players in Screens as a Cloud Service installeren en configureren
description: In deze pagina wordt beschreven hoe u spelers in Screens as a Cloud Service kunt installeren en configureren.
exl-id: a022738a-c543-4629-a244-f70fa294fe7f
feature: Developing Screens
role: Admin, Developer, User
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 0%

---

# Players in Screens as a Cloud Service installeren en configureren {#installing-players-screens-cloud}

In deze sectie wordt beschreven hoe u AEM Screens-spelers kunt installeren die zijn geregistreerd op externe AEM. U moet ook een fabrieksinstellingen maken van de bestaande speler en de nieuwe speler vervolgens registreren bij AEM Screens as a Cloud Service.

## Doelstelling {#objective}

Dit document helpt u te begrijpen hoe u de speler kunt instellen voordat u de spelers registreert. Na het lezen, zou u het volgende moeten kunnen begrijpen:

* waar u de spelers kunt installeren vanaf
* hoe u de speler kunt bijwerken naar de cloud-modus

## Stappen om de speler in te stellen op de cloudmodus {#cloud-mode-setup}

Nadat u de recentste speler van [ Downloads van de Speler van AEM Screens ](https://download.macromedia.com/screens/) hebt gedownload, bent u nu klaar om uw speler aan de wijze van de Wolk bij te werken.

Voer de onderstaande stappen uit om uw speler bij te werken:

1. Open AEM Screens Player.

   >[!NOTE]
   >U kunt kiezen of u wilt testen met specifieke hardwareapparaten of met een webextensie voor uw eigen speler.

1. Klik het **lusje van de Configuratie** en klik **aan de knoop van de Fabriek** onder **het Terugstellen** optie.

   ![afbeelding](/help/screens-cloud/assets/player/installplayer-2.png)

1. Klik **bevestigen** om uw speler terug te stellen.

1. Opnieuw van het **lusje van de Configuratie** en klik **Verandering in de knoop van de Wijze van de Wolk** onder **Wissel Runmode** optie.

   ![afbeelding](/help/screens-cloud/assets/player/installplayer-1.png)

1. Klik **bevestigen** dat herinneringen wanneer het schakelen aan wolkenwijze unregisters de speler.

## Standaardafspeelcontrole {#playback-monitoring}

De speler rapporteert verschillende afspeelmetriek bij elke `ping` die standaard 30 seconden bedraagt. Op basis van deze maatstaven kan Adobe verschillende randgevallen detecteren, zoals geplakte ervaring, een leeg scherm en planningsproblemen. Deze opsporing laat ons kwesties op het apparaat begrijpen en problemen oplossen, en bespoedigt daarom een onderzoek en correctieve maatregelen met u.

Met de standaardafspeelcontrole in een AEM Screens-speler kunnen we:

* Op afstand controleren of een speler de inhoud correct afspeelt.

* Verbeter reactiviteit aan lege schermen of gebroken ervaringen op het gebied.

* Vermindert het risico om een gebroken ervaring aan de gebruiker te tonen.

### Eigenschappen {#understand-properties}

De volgende eigenschappen worden in elke `ping` opgenomen:

| Eigenschap | Beschrijving |
|---|---|
| id {string} | de speler-id |
| activeChannel {string} | momenteel het kanaalpad afspelen, of null als er niets is gepland |
| activeElements {string} | door komma&#39;s gescheiden tekenreeks, momenteel zichtbare elementen in alle kanalen van de afspeelvolgorde (meerdere als er een lay-out met meerdere zones is) |
| isDefaultContent {boolean} | true als het afspeelkanaal wordt beschouwd als een standaard- of fallback-kanaal (heeft dus prioriteit 1 en geen planning) |
| hasContentChanged {boolean} | true als de inhoud in de laatste 5 minuten is gewijzigd, anders false |
| lastContentChange {string} | tijdstempel van de laatste inhoudswijziging |

>[!NOTE]
>U kunt desgewenst een geavanceerdere eigenschap inschakelen via de voorkeuren voor de speler (Afspeelcontrole inschakelen):
>|Eigenschap|Beschrijving|
>|—|—|
>|isContentRendering {boolean}|true als de GPU kan bevestigen dat de werkelijke inhoud wordt afgespeeld (op basis van pixelanalyse)|

### Beperkingen {#limitations}

Hieronder worden enkele beperkingen weergegeven voor elementaire afspeelcontrole:

* De speler rapporteert zijn eigen playbackstaat aan de server, zodat vereist het een actieve verbinding.

* De eigenschap `isContentRendering` die de GPU controleert, is te veel bronnen om standaard te kunnen worden ingeschakeld. Hiervoor is expliciete opt-in vereist bij de voorkeuren van de speler. U wordt aangeraden dit programma niet te gebruiken voor video&#39;s die in productie zijn.

* Deze functie wordt alleen ondersteund voor reekskanalen en heeft nog geen betrekking op het gebruik van interactieve kanalen (SPA).

* De metriek worden nog niet volledig blootgesteld aan klanten; de Adobe werkt aan het toelaten van dashboard-als rapporterings en alarmeringsmechanisme spoedig.

## Volgende functies {#whats-next}

Nu u de speler hebt geïnstalleerd en geconfigureerd in de cloud-modus, gaat u door met uw as a Cloud Service Screens-reis. Zie [ Registrerend Players in Screens as a Cloud Service ](/help/screens-cloud/managing-players-registration/registering-players-screens-cloud.md) van de Dienstverlener van Screens.
