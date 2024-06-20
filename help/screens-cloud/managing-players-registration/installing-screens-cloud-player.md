---
title: Players in as a Cloud Service schermen installeren en configureren
description: In deze pagina wordt beschreven hoe u spelers in as a Cloud Service schermen kunt installeren en configureren.
exl-id: a022738a-c543-4629-a244-f70fa294fe7f
feature: Developing Screens
role: Admin, Developer, User
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 0%

---

# Players in as a Cloud Service schermen installeren en configureren {#installing-players-screens-cloud}

In deze sectie wordt beschreven hoe u AEM Screens-spelers kunt installeren die zijn geregistreerd op externe AEM. U moet ook een fabrieksinstellingen maken van de bestaande speler en de nieuwe speler vervolgens registreren tegen AEM Screens as a Cloud Service.

## Doelstelling {#objective}

Dit document helpt u te begrijpen hoe u de speler kunt instellen voordat u de spelers registreert. Na het lezen, zou u het volgende moeten kunnen begrijpen:

* waar u de spelers kunt installeren vanaf
* hoe u de speler kunt bijwerken naar de cloud-modus

## Stappen om de speler in te stellen op de cloudmodus {#cloud-mode-setup}

Nadat u de nieuwste speler hebt gedownload van [Downloads voor AEM Screens Player](https://download.macromedia.com/screens/), kunt u de speler nu bijwerken naar de cloud-modus.

Voer de onderstaande stappen uit om uw speler bij te werken:

1. Open AEM Screens Player.

   >[!NOTE]
   >U kunt kiezen of u wilt testen met specifieke hardwareapparaten of met een webextensie voor uw eigen speler.

1. Klik op de knop **Configuratie** en klik op **Naar fabriek** knop onder **Herstellen** -optie.

   ![afbeelding](/help/screens-cloud/assets/player/installplayer-2.png)

1. Klikken **Bevestigen** om de speler opnieuw in te stellen.

1. Opnieuw vanaf de **Configuratie** en klik op **Wijzigen in de cloudmodus** knop onder **Runmode schakelen** -optie.

   ![afbeelding](/help/screens-cloud/assets/player/installplayer-1.png)

1. Klikken **Bevestigen** dat ertoe aanzet wanneer het schakelen naar wolkenwijze maakt de speler onbruikbaar.

## Standaardafspeelcontrole {#playback-monitoring}

De speler rapporteert verschillende afspeelmetriek voor elke speler `ping` dat is standaard 30 seconden. Op basis van deze maatstaven kan Adobe verschillende randgevallen detecteren, zoals geplakte ervaring, een leeg scherm en planningsproblemen. Deze opsporing laat ons kwesties op het apparaat begrijpen en problemen oplossen, en bespoedigt daarom een onderzoek en correctieve maatregelen met u.

Met de standaardafspeelcontrole in een AEM Screens-speler kunnen we:

* Op afstand controleren of een speler de inhoud correct afspeelt.

* Verbeter reactiviteit aan lege schermen of gebroken ervaringen op het gebied.

* Vermindert het risico om een gebroken ervaring aan de gebruiker te tonen.

### Eigenschappen {#understand-properties}

De volgende eigenschappen worden in elk `ping`:

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

* De `isContentRendering` eigenschap die de GPU controleert, vergt te veel bronnen om standaard te kunnen worden ingeschakeld en vereist expliciete opt-in bij de voorkeuren voor de speler. U wordt aangeraden dit programma niet te gebruiken voor video&#39;s die in productie zijn.

* Deze functie wordt alleen ondersteund voor reekskanalen en heeft nog geen betrekking op het gebruik van interactieve kanalen (SPA).

* De metriek worden nog niet volledig blootgesteld aan klanten; de Adobe werkt aan het toelaten van dashboard-als rapporterings en alarmeringsmechanisme spoedig.

## Volgende functies {#whats-next}

Nu u de speler hebt geïnstalleerd en geconfigureerd in de cloud-modus, gaat u door met de as a Cloud Service reis naar de schermen. Zie [Afspeellagen registreren in as a Cloud Service schermen](/help/screens-cloud/managing-players-registration/registering-players-screens-cloud.md) van Screens Services Provider.
