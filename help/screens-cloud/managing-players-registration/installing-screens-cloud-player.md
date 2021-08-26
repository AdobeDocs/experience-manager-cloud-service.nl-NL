---
title: Players in rasters installeren en configureren als Cloud Service
description: In deze pagina wordt beschreven hoe u spelers op schermen als Cloud Service kunt installeren en configureren.
source-git-commit: d5970e27773433c9e6e7175a103768ae591e87ba
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---


# Players in rasters installeren en configureren als Cloud Service {#installing-players-screens-cloud}

In deze sectie wordt beschreven hoe u AEM Screens-spelers kunt installeren die zijn geregistreerd op externe AEM. Bovendien moet u de bestaande speler opnieuw instellen in de fabriek en de nieuwe speler vervolgens registreren bij AEM Screens als Cloud Service.

## Doelstelling {#objective}

Dit document helpt u te begrijpen hoe u de speler kunt instellen voordat u de spelers registreert. Na het lezen moet u het volgende kunnen begrijpen:

* waar u de spelers kunt installeren vanaf
* hoe u de speler kunt bijwerken naar de cloud-modus

## Stappen om de speler in te stellen op de cloudmodus {#cloud-mode-setup}

Wanneer u de nieuwste speler hebt gedownload van [AEM Screens Player Downloads](https://download.macromedia.com/screens/), kunt u de speler nu bijwerken naar de Cloud-modus.

Voer de onderstaande stappen uit om uw speler bij te werken:

1. Open AEM Screens Player.

   >[!NOTE]
   >U kunt kiezen of u wilt testen met specifieke hardwareapparaten of met een webextensie voor uw eigen speler.

1. Klik op de tab **Configuration** en klik op **To Factory** onder **Reset**.

   ![afbeelding](/help/screens-cloud/assets/player/installplayer-2.png)

1. Klik op **Bevestig** om de speler opnieuw in te stellen.

1. Opnieuw van **Configuratie** tabel en klik op **Verandering in de Wijze van de Wolk** knoop onder **Runmode** optie van de Wisselen.

   ![afbeelding](/help/screens-cloud/assets/player/installplayer-1.png)

1. Klik op **Bevestig** dat ertoe aanzet wanneer het schakelen naar wolkenwijze de speler zal schrappen-register.

## Standaardafspeelcontrole {#playback-monitoring}

De speler rapporteert verschillende afspeelmetriek met elke `ping` die standaard op 30 seconden wordt ingesteld. Gebaseerd op de metriek, kunt u diverse randgevallen zoals gespleet ervaring, leeg scherm, en het plannen kwesties ontdekken. Dit laat u kwesties op het apparaat begrijpen en problemen oplossen, en bespoedigt zo een onderzoek en correctieve maatregelen.

Met de standaardafspeelcontrole in een AEM Screens-speler kunt u:

* Op afstand controleren of een speler de inhoud correct afspeelt.

* Verbeter reactiviteit aan lege schermen of gebroken ervaringen op het gebied.

* Vermindert het risico om een gebroken ervaring aan het eind - gebruiker te tonen.

### Eigenschappen {#understand-properties}

De volgende eigenschappen worden in elke `ping` opgenomen:

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

* De eigenschap `isContentRendering` die de GPU controleert, is momenteel hulpbronnenintensief om standaard te kunnen worden ingeschakeld en vereist expliciete opt-in bij de voorkeuren voor spelers. U wordt aangeraden dit effect niet samen met video&#39;s te gebruiken.

* Deze functie wordt ondersteund voor reekskanalen.

## Volgende functies {#whats-next}

Nu u de speler hebt geïnstalleerd en geconfigureerd in de cloud-modus, moet u uw schermen voortzetten als een Cloud Service-reis door het document opnieuw te bekijken, [Players in Screens registreren als een Cloud Service](/help/screens-cloud/managing-players-registration/registering-players-screens-cloud.md) van Screens Services Provider.
