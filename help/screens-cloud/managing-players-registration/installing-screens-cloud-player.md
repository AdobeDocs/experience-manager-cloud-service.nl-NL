---
title: Players in as a Cloud Service schermen installeren en configureren
description: In deze pagina wordt beschreven hoe u spelers in as a Cloud Service schermen kunt installeren en configureren.
exl-id: a022738a-c543-4629-a244-f70fa294fe7f
source-git-commit: 3367977496d3edad0f6f1e27e98eac95c791e870
workflow-type: tm+mt
source-wordcount: '600'
ht-degree: 0%

---

# Players in as a Cloud Service schermen installeren en configureren {#installing-players-screens-cloud}

In deze sectie wordt beschreven hoe u AEM Screens-spelers kunt installeren die zijn geregistreerd op externe AEM. Bovendien moet u de bestaande speler opnieuw instellen in de fabriek en de nieuwe speler vervolgens registreren tegen AEM Screens as a Cloud Service.

## Doelstelling {#objective}

Dit document helpt u te begrijpen hoe u de speler kunt instellen voordat u de spelers registreert. Na het lezen moet u het volgende kunnen begrijpen:

* waar u de spelers kunt installeren vanaf
* hoe u de speler kunt bijwerken naar de cloud-modus

## Stappen om de speler in te stellen op de cloudmodus {#cloud-mode-setup}

Wanneer u de nieuwste speler hebt gedownload van [Downloads voor AEM Screens Player](https://download.macromedia.com/screens/), kunt u de speler nu bijwerken naar de cloud-modus.

Voer de onderstaande stappen uit om uw speler bij te werken:

1. Open AEM Screens Player.

   >[!NOTE]
   >U kunt kiezen of u wilt testen met specifieke hardwareapparaten of met een webextensie voor uw eigen speler.

1. Klik op de knop **Configuratie** en klik op **Naar fabriek** knop onder **Herstellen** optie.

   ![afbeelding](/help/screens-cloud/assets/player/installplayer-2.png)

1. Klikken op **Bevestigen** om de speler opnieuw in te stellen.

1. Opnieuw vanaf de **Configuratie** en klik op **Wijzigen in de cloudmodus** knop onder **Runmode schakelen** optie.

   ![afbeelding](/help/screens-cloud/assets/player/installplayer-1.png)

1. Klikken op **Bevestigen** die ertoe aanzet wanneer overschakeling op wolkenwijze zal de speler deregistreren.

## Standaardafspeelcontrole {#playback-monitoring}

De speler rapporteert verschillende afspeelmetriek voor elke speler `ping` dat is standaard 30 seconden. Gebaseerd op deze metriek, kunnen wij diverse randgevallen zoals vastgezette ervaring, leeg scherm, en het plannen kwesties ontdekken. Dit laat ons kwesties op het apparaat begrijpen en problemen oplossen, en bespoedigt zo een onderzoek en correctieve maatregelen met u.

Met de standaardafspeelcontrole in een AEM Screens-speler kunnen we:

* Op afstand controleren of een speler de inhoud correct afspeelt.

* Verbeter reactiviteit aan lege schermen of gebroken ervaringen op het gebied.

* Vermindert het risico om een gebroken ervaring aan het eind - gebruiker te tonen.

### Eigenschappen {#understand-properties}

De volgende eigenschappen worden in elk `ping`:

| Eigenschap | Beschrijving |
|---|---|
| id {string} | de speler-id |
| activeChannel {string} | momenteel het kanaalpad afspelen, of null als er niets is gepland |
| activeElements {string} | door komma&#39;s gescheiden tekenreeks, momenteel zichtbare elementen in alle kanalen van de afspeelvolgorde (meerdere bij een lay-out met meerdere zones) |
| isDefaultContent {boolean} | true als het afspeelkanaal wordt beschouwd als een standaard- of fallback-kanaal (heeft dus prioriteit 1 en geen planning) |
| hasContentChanged {boolean} | true als de inhoud in de laatste 5 minuten is gewijzigd, anders false |
| lastContentChange {string} | tijdstempel van de laatste inhoudswijziging |

>[!NOTE]
>Naar keuze, kan een geavanceerdere bezit van de spelervoorkeur (Enable Playback Controle) worden toegelaten en dat is:
>|Eigenschap|Beschrijving|
>|—|—|
>|isContentRendering {boolean}|true als de GPU kan bevestigen dat de werkelijke inhoud wordt afgespeeld (op basis van pixelanalyse)|

### Beperkingen {#limitations}

Hieronder worden enkele beperkingen weergegeven voor elementaire afspeelcontrole:

* De speler rapporteert zijn eigen playbackstaat aan de server, zodat vereist het een actieve verbinding.

* De `isContentRendering` eigenschap die de GPU controleert, is momenteel te hulpbronnenintensief om standaard te kunnen worden ingeschakeld en vereist expliciete opt-in bij de voorkeuren voor spelers. U wordt aangeraden dit niet te gebruiken in combinatie met video&#39;s in productie.

* Deze functie wordt alleen ondersteund voor reekskanalen en heeft nog geen betrekking op het gebruik van interactieve kanalen (SPA).

* De metriek worden nog niet volledig aan onze klanten blootgesteld, wij werken hard aan het toelaten van dashboard-als rapportering en alarmeringsmechanisme in de nabije toekomst.

## Volgende functies {#whats-next}

Nu u de speler hebt geïnstalleerd en geconfigureerd voor de cloud-modus, moet u de as a Cloud Service reis van de schermen voortzetten door het document opnieuw te bekijken. [Afspeellagen registreren in as a Cloud Service schermen](/help/screens-cloud/managing-players-registration/registering-players-screens-cloud.md) van Screens Services Provider.
