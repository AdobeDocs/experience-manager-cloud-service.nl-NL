---
title: AEM Screens inschakelen voor uw demo-site
description: Leer de stappen om de volledige as a Cloud Service AEM Screens-ervaring op uw demo-site in te schakelen.
exl-id: 369eea9f-2e81-4b87-841c-188b67657bab
source-git-commit: cdc60627bac17166c12ebdb77e7cf5b0ed92dc80
workflow-type: tm+mt
source-wordcount: '2671'
ht-degree: 0%

---

# AEM Screens inschakelen voor uw demo-site {#enable-screens}

Leer de stappen om de volledige as a Cloud Service AEM Screens-ervaring op uw demo-site in te schakelen.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de AEM Reference Demos Add-on trip, [Maak een demo-site,](create-site.md) u creeerde een nieuwe demoplaats die op de malplaatjes van de Toevoeging van de Demo van de Verwijzing wordt gebaseerd. Nu moet u:

* Begrijp hoe te om tot het AEM auteursmilieu toegang te hebben.
* Weet hoe u een site kunt maken op basis van een sjabloon.
* Begrijp de grondbeginselen van het navigeren van de plaatsstructuur en het uitgeven van een pagina.

Nu u uw eigen demo-site hebt om de beschikbare tools te verkennen en te begrijpen voor het beheren van uw demo-sites, kunt u nu de volledige as a Cloud Service AEM Screens-ervaring voor uw demo-sites inschakelen.

## Doelstelling {#objective}

De AEM Reference Demos Add-On bevat AEM Screens-inhoud voor We.Cafe, een verticaal bedrijf in een café. Dit document helpt u te begrijpen hoe u de Web.Cafe demo-instellingen kunt uitvoeren in de context van AEM Screens. Na het lezen moet u:

* De basisbeginselen van AEM Screens kennen.
* Begrijp de Web.Cafe demo-inhoud.
* Weet hoe u AEM Screens for We.Cafe kunt configureren.
   * Weet hoe u een Screens-project voor We.Cafe kunt maken.
   * Een gesimuleerde weerservice configureren met Google Sheets en API&#39;s.
   * Simuleer dynamisch veranderende inhoud van het Scherm die op uw &quot;weerdienst wordt gebaseerd.&quot;
   * Installeer en gebruik de schermspeler.

## Schermen begrijpen {#understand-screens}

AEM Screens as a Cloud Service is een digitale signaaloplossing waarmee marketers dynamische digitale ervaringen op schaal kunnen creëren en beheren. Met AEM Screens as a Cloud Service kunt u aantrekkelijke en dynamische digitale signage-ervaringen creëren die bedoeld zijn om te worden gebruikt in openbare ruimten.

>[!TIP]
>
>Voor alle informatie over AEM Screens as a Cloud Service raadpleegt u de [Aanvullende bronnen](#additional-resources) aan het einde van dit document.

Door de AEM Reference Demos Add-On te installeren, beschikt u automatisch over Web.Cafe-inhoud voor AEM Screens in uw demo-ontwerpomgeving. De stappen die worden beschreven in het dialoogvenster [Een demo-rasterproject implementeren](#deploy-project) staat u toe om de volledige ervaring van AEM Screens toe te laten door die inhoud te publiceren en aan media spelers etc. op te stellen.

## De demo-inhoud begrijpen {#demo-content}

De We.Cafe-koffiewinkel bestaat uit drie winkels op drie locaties in de VS. Alle drie winkels hebben drie vergelijkbare ervaringen:

* Een menukaart boven de teller met twee of drie verticale panelen
* Een toegangsscherm dat de straat onder ogen ziet met een horizontaal of verticaal paneel dat klanten in de winkel uitnodigt
* Een snelle zelfrangschikkende kioskcabine om de rij met één verticale tablet te mijden

>[!NOTE]
>
>Alleen de ingangsweergave kan in de huidige versie van de demo worden getest. Andere weergaven volgen in een toekomstige versie.
>
>De kiosk is niet opgenomen in de huidige versie van de demo. Het wordt in een toekomstige versie opgenomen.

De locatie in New York wordt verondersteld zich in een kleinere winkel te bevinden die niet veel ruimte heeft, en als zodanig:

* Het menubord heeft slechts twee verticale panelen in plaats van drie voor San Francisco en San Jose
* De ingangsweergave wordt verticaal in plaats van horizontaal geplaatst

>[!NOTE]
>
>Als u besluit verbinding te maken met de Cloud Service Schermen in het dialoogvenster [as a Cloud Service Connect-schermen](#connect-screens) , maakt u de locaties als mappen onder Weergave. Zie de [Aanvullende bronnen](#additional-resources) aan het einde van dit document voor meer informatie over de weergave.

### Cafe-indelingen {#care-layouts}

De locaties Web.Cafe hebben de volgende lay-outs.

![We.Cafe-indelingen](assets/cafe-layouts.png)

>[!NOTE]
>
>De metingen voor de schermen zijn in inches.

### Entrance {#entrance}

De ingangsweergave wordt dagelijks geparseerd en de eerste afbeelding wordt van ochtend tot middag gewijzigd. Op elke stap van de reeks wordt ook een ander speciaal koffiepreparaat geadverteerd, waarbij een gemeten ingesloten reeks wordt gebruikt om telkens een ander item af te spelen.

De laatste afbeelding op de ingangskanalen wordt ook gericht (d.w.z. dynamisch gewijzigd) op basis van de buitentemperatuur, die kan worden gesimuleerd zoals beschreven in het [Gesimuleerde gegevensbron maken](#data-source) sectie.

## Een demo-rasterproject implementeren {#deploy-project}

Als u de demo-inhoud wilt gebruiken in de sandbox die u in het dialoogvenster [Programma maken](create-program.md) stap, moet een plaats worden gecreeerd gebaseerd op een malplaatje.

Als u nog geen Web.Cafe demo-site hebt gemaakt, voert u gewoon dezelfde stappen uit als in het dialoogvenster [Demo-site maken](create-site.md) sectie. Als u de sjabloon selecteert, kiest u gewoon de **We.Cafe-websitesjabloon**.

![We.Cafe-sjabloon](assets/wecafe-template.png)

Zodra de tovenaar voltooit, zult u de inhoud vinden die onder Plaatsen wordt opgesteld en u kunt navigeren en onderzoeken aangezien u andere inhoud.

![Web.Cafe-inhoud](assets/wecafe-content.png)

Nu we Web.Cafe-inhoud hebben, hebt u een keuze over hoe u AEM Screens wilt testen:

* Als u alleen de inhoud binnen de AEM Sites-console wilt verkennen, kunt u gewoon meer verkennen en ontdekken in de [Aanvullende bronnen](#additional-resources) sectie! er is geen actie meer nodig .
* Ga naar de volgende sectie als u de volledige dynamische eigenschappen van AEM Screens wilt ervaren, [Scherminhoud dynamisch wijzigen.](#dynamically-change)

## Scherminhoud dynamisch wijzigen {#dynamically-change}

Net als AEM Sites kan AEM Screens inhoud dynamisch wijzigen op basis van context. De Wij.Cafe demo heeft kanalen die worden gevormd om verschillende inhoud afhankelijk van de huidige temperatuur te tonen. Om dit te simuleren, zullen we onze eigen eenvoudige weerdienst moeten creëren.

### Gesimuleerde gegevensbron maken {#data-source}

Aangezien het zeer moeilijk is het weer tijdens een demo of tijdens de test te veranderen, moeten temperatuurveranderingen worden gesimuleerd. Wij zullen de weerdienst simuleren door een temperatuurwaarde in een spreadsheet van het Blad van Google op te slaan die AEM ContextHub zal roepen om de temperatuur terug te winnen.

#### Google API-sleutel maken {#create-api-key}

Eerst moeten we een Google API-sleutel maken om de uitwisseling van gegevens te vergemakkelijken.

1. Meld u aan bij een Google-account.
1. De Cloud Console openen met deze koppeling `https://console.cloud.google.com`.
1. Maak een nieuw project door linksboven op de werkbalk op de naam van het huidige project te klikken **Google Cloud Platform** label.

   ![Google Cloud Console](assets/google-cloud-console.png)

1. Klik in het dialoogvenster Projectkiezer op **NIEUW PROJECT**.

   ![Nieuw project](assets/new-project.png)

1. Geef het project een naam en klik **MAKEN**.

   ![Project maken](assets/create-project.png)

1. Zorg ervoor dat uw nieuwe project is geselecteerd en selecteer vervolgens met het hamburgermenu in het dashboard van de Cloud Console de optie **API&#39;s en services**.

   ![API&#39;s en services](assets/apis-services.png)

1. Klik in het linkerdeelvenster van het venster API&#39;s en services op **Credentials** boven aan het venster klikt u op **CREDENTIALS MAKEN** en **API-sleutel**.

   ![Credentials](assets/credentials.png)

1. Kopieer de nieuwe API-sleutel in het dialoogvenster en sla deze op voor later gebruik. Klikken **SLUITEN** om het dialoogvenster te sluiten.

#### Google Sheets API inschakelen {#enable-sheets}

Als u de uitwisseling van Google Sheets-gegevens met behulp van uw API-sleutel wilt toestaan, moet u de Google Sheets API inschakelen.

1. Ga terug naar de Google Cloud Console op `https://console.cloud.google.com` voor uw project en gebruik vervolgens het hamburgermenu om **API&#39;s en services -> Bibliotheek**.

   ![API-bibliotheek](assets/api-library.png)

1. Blader in het scherm API-bibliotheek naar de zoekopdracht **Google Sheets API**. Klik erop.

   ![API-bibliotheekzoekopdracht](assets/api-library-search.png)

1. In de **Google Sheets API** vensterklik **INSCHAKELEN**.

   ![Google-API voor bladen](assets/sheets-api.png)

#### Google-werkblad met bladen maken {#create-spreadsheet}

Nu kunt u een Google Sheets-spreadsheet maken om uw weergegevens op te slaan.

1. Ga naar `https://docs.google.com` en maak een nieuw Google Sheets-werkblad.
1. Definieer de temperatuur door deze in te voeren `32` in cel A2.
1. Document delen door op **Delen** rechtsboven in het venster en onder **Koppeling ophalen** klikken **Wijzigen**.

   ![Werkblad delen](assets/share-sheet.png)

1. Kopieer de koppeling voor de volgende stap.

   ![Koppeling delen](assets/share-link.png)

1. Zoek de pagina-id.

   * De pagina-id is de willekeurige tekenreeks in de bladkoppeling die u hebt gekopieerd na `d/` en voor `/edit`.
   * Bijvoorbeeld:
      * Als uw URL `https://docs.google.com/spreadsheets/d/1cNM7j1B52HgMdsjf8frCQrXpnypIb8NkJ98YcxqaEP30/edit#gid=0`
      * De pagina-id is `1cNM7j1B52HgMdsjf8frCQrXpnypIb8NkJ98YcxqaEP30`.

1. Kopieer de pagina-id voor toekomstig gebruik.

#### Uw weerservice testen {#test-weather-service}

Nu u uw gegevensbron hebt gemaakt als een Google Sheets-spreadsheet en toegang via API hebt ingeschakeld, test u deze om te controleren of uw &quot;weerservice&quot; toegankelijk is.

1. Open een webbrowser.

1. Voer de volgende aanvraag in en vervang de waarden van de blad-id en de API-sleutel die u eerder hebt opgeslagen.

   ```
   https://sheets.googleapis.com/v4/spreadsheets/<yourSheetID>/values/Sheet1?key=<yourAPIKey>
   ```

1. Als u JSON-gegevens ontvangt die vergelijkbaar zijn met de volgende, stelt u deze op de juiste wijze in.

   ```json
   {
     "range": "Sheet1!A1:Z1000",
     "majorDimension": "ROWS",
     "values": [
       [],
       [
         "32"
       ]
     ]
   }
   ```

AEM Screens kan deze zelfde dienst gebruiken om tot de gesimuleerde weergegevens toegang te hebben. Dit zal in de volgende stap worden gevormd.

### ContextHub configureren {#configure-contexthub}

AEM Screens kan inhoud dynamisch wijzigen op basis van context. De demonstratie We.Cafe heeft kanalen die worden gevormd om verschillende inhoud afhankelijk van de huidige temperatuur te tonen door AEM ContextHub leveraging.

>[!TIP]
>
>Voor de volledige details van ContextHub, zie [Aanvullende bronnen](#additional-resources) aan het einde van dit document.

Wanneer de het scherminhoud wordt getoond, zal ContextHub uw weerdienst omhoog roepen om de huidige temperatuur te vinden om te bepalen welke inhoud aan vertoning.

Voor demo-doeleinden kunnen de waarden in het blad worden gewijzigd. ContextHub zal dit erkennen en de inhoud zal in het kanaal volgens de bijgewerkte temperatuur aanpassen.

1. Ga voor de auteur van AEMaaCS naar **Globale Navigatie -> Hulpmiddelen -> Plaatsen -> ContextHub**.
1. Selecteer de configuratiecontainer die de zelfde naam heeft zoals wat u het project gaf toen u het project van de Schermen van creeerde **We.Cafe-websitesjabloon**.
1. Selecteren **Configuratie -> ContextHub Configuration -> Google Sheets** klik vervolgens op **Volgende** rechtsboven.
1. De configuratie zou reeds JSON gegevens moeten hebben pre-gevormd. Er zijn twee waarden die moeten worden gewijzigd:
   1. Vervangen `[your Google Sheets id]` met de pagina-id [eerder opgeslagen.](#create-spreadsheet)
   1. Vervangen `[your Google API Key]` met de API-sleutel [eerder opgeslagen.](#create-api-key)
1. Klikken **Opslaan**.

Nu kunt u de temperatuurwaarde in uw spreadsheet van het Google veranderen en ContextHub zal de Schermen dynamisch bijwerken aangezien het &quot;de weerverandering ziet.&quot;

### Dynamische gegevens testen {#test-dynamic}

Nu AEM Screens en ContextHub met uw weerdienst worden verbonden, kunt u het testen om te zien hoe de schermen inhoud dynamisch kunnen bijwerken.

1. Toegang tot de instantie van de maker van de sandbox.
1. Navigeren naar de siteconsole via **Algemene navigatie -> Sites** en selecteer de volgende pagina **Schermen -> &lt;project-name> -> Kanalen -> Binnenkomst (staand)**.

   ![Projectinhoud demo selecteren](assets/project-content.png)

1. Klik op Bewerken op de werkbalk of typ de sneltoets `e` om de pagina te bewerken.

1. In de redacteur, kunt u de inhoud zien. Eén afbeelding is hoog verlicht in blauw met een doelpictogram in de hoek.

   ![Inhoud weergeven in editor](assets/screens-content-editor.png)

1. Wijzig de temperatuur die u hebt ingevoerd in het werkblad van 32 in 70 en bekijk de wijziging van de inhoud.

   ![Inhoud weergeven in editor](assets/screens-content-editor-2.png)

Op basis van de temperatuursverandering van een vriestemperatuur van 32°F (0°C) in een comfortabele 70°F (21°C) veranderde het aanbevolen beeld van een opwarmer theekopje in een koele, geijkte koffie.

>[!IMPORTANT]
>
>Gebruik de beschreven Google Sheets-oplossing alleen voor demo-doeleinden. Adobe biedt geen ondersteuning voor het gebruik van Google Sheets voor productieomgevingen.

## as a Cloud Service Connect-schermen {#connect-screens}

Als u ook een echte digitale handtekening wilt instellen, inclusief een speler die op een digitaal signaalapparaat of op uw computer wordt uitgevoerd, voert u de volgende stappen uit.

U kunt de demo ook eenvoudig voorvertonen in de Kanaaleditor op AEMaaCS.

>[!TIP]
>
>Voor alle details van de Redacteur van het Kanaal, zie [Aanvullende bronnen](#additional-resources) aan het einde van dit document.

### AEM Screens as a Cloud Service configureren {#configure-screens}

Eerst moet u de inhoud van uw schermdemo publiceren naar AEM Screens as a Cloud Service en de service configureren.

1. Publiceer de inhoud van uw demoscreensproject.
1. Navigeren naar as a Cloud Service schermen op `https://experience.adobe.com/screens` en aanmelden.
1. Rechtsboven in het scherm moet u controleren of u zich in de juiste organisatie bevindt.

   ![Controleer uw schermbeveiliging](assets/screens-org.png)

1. Klik in de linkerbovenhoek op de knop **Instellingen bewerken** pictogram, gevormd als een tandwiel.

   ![Instellingen bewerken](assets/screens-edit-settings.png)

1. Geef de URL&#39;s van de auteur van AEMaaCS op en publiceer instanties waar u uw demosite hebt gemaakt en klik op **Opslaan**.

   ![Scherminstelling](assets/screens-settings.png)

1. Nadat de schermen zijn aangesloten op de demo-instanties, wordt de inhoud van het kanaal opgehaald. Klikken op **Kanalen** in het linkerdeelvenster om de gepubliceerde kanalen te zien. Het kan even duren voordat de informatie wordt ingevuld. U kunt op blauw klikken **Synchroniseren** aan de rechterbovenhoek van het scherm om de informatie bij te werken.

   ![Info demokanaal](assets/screens-channels.png)

1. Klikken op **Weergaven** in het linkerdeelvenster. U hebt nog geen bestanden voor uw demo gemaakt. We simuleren de locaties van We.Cafe door voor elke locatie mappen te maken. Klikken op **Maken** rechtsboven in het scherm en selecteer **Map**.

   ![Weergave maken](assets/screens-displays.png)

1. Geef in het dialoogvenster een mapnaam op, bijvoorbeeld **San Jose** en klik op **Maken**.

1. Open de map door erop te klikken en klik vervolgens op **Maken** aan de rechterbovenhoek en selecteert u **Weergave**.

1. Geef een weergavenaam op en klik op **Maken**.

   ![Weergave maken](assets/create-display.png)

1. Nadat de weergave is gemaakt, klikt u op de naam van de weergave om het scherm met weergavedetails te openen. Aan de weergave moet een kanaal worden toegewezen dat vanuit uw demosite is gesynchroniseerd. Klikken op **Kanaal toewijzen** rechtsboven in het scherm.

   ![Kanaaldetails](assets/channel-detail.png)

1. Selecteer het kanaal in het dialoogvenster en klik op **Toewijzen**.

   ![Kanaal toewijzen](assets/assign-channel.png)

U kunt deze stappen voor uw extra plaatsen en vertoningen herhalen. Nadat de demo-site is voltooid, hebt u een koppeling naar AEM Screens tot stand gebracht en hebt u de benodigde configuratie voltooid.

U kunt de demo eenvoudig voorvertonen in de Kanaaleditor op AEMaaCS.

### Schermspeler gebruiken {#screens-player}

Als u de inhoud op een echt scherm wilt weergeven, kunt u de speler downloaden en lokaal instellen. AEM Screens as a Cloud Service levert de inhoud vervolgens aan uw speler

#### Een registratiecode genereren {#registration-code}

Eerst moet u een registratiecode maken om een speler veilig te verbinden met as a Cloud Service AEM Screens.

1. Navigeren naar as a Cloud Service schermen op `https://experience.adobe.com/screens` en aanmelden.
1. Rechtsboven in het scherm moet u controleren of u zich in de juiste organisatie bevindt.

   ![Controleer uw schermbeveiliging](assets/screens-org.png)

1. Klik in het linkerdeelvenster op **Player Management -> Registratiecodes** en klik vervolgens op **Code maken** rechtsboven in het scherm.

![Registratiecodes](assets/registration-codes.png)

1. Voer een naam voor de code in en klik op **Maken**.

   ![Code maken](assets/create-code.png)

1. Nadat de code is gemaakt, wordt deze weergegeven in de lijst. Klik om de code te kopiëren.

   ![Registratiecode](assets/registration-code.png)

#### Speler installeren en configureren {#install-player}

1. Download de speler van uw platform van `https://download.macromedia.com/screens/` en installeer het.
1. De speler uitvoeren en overschakelen op de **Configuratie** tab, naar beneden schuiven om beide te klikken en te bevestigen **Herstellen naar fabriek** en vervolgens **Wijzigen in de cloudmodus**.

   ![Player-instellingen](assets/player-configuration.png)

1. De speler wordt automatisch gewijzigd in **Spelerregistratie** tab. Voer de code in die u eerder hebt gegenereerd en klik op **Registreren**.

   ![Player registration](assets/player-registration-code.png)

1. Naar de **Systeeminformatie** om te bevestigen dat de speler is geregistreerd.

   ![Geregistreerde speler](assets/player-registered.png)

#### Speler aan een Vertoning toewijzen {#assign-player}

1. Navigeren naar as a Cloud Service schermen op `https://experience.adobe.com/screens` en aanmelden.
1. Rechtsboven in het scherm moet u controleren of u zich in de juiste organisatie bevindt.

   ![Controleer uw schermbeveiliging](assets/screens-org.png)

1. Klik in het linkerdeelvenster op **Player Management -> Players** en u ziet de speler die u eerder hebt geïnstalleerd en geregistreerd.

   ![Players](assets/players.png)

1. Klik op de naam van de speler om de details te openen en klik vervolgens op **Toewijzen aan weergave** in de rechterbovenhoek van het scherm.

   ![Speler toewijzen aan weergave](assets/assign-to-display.png)

1. Selecteer in het dialoogvenster de weergave die u eerder hebt gemaakt en klik op **Selecteren**.

   ![Een weergave toewijzen](assets/assign-a-display.png)

#### Afspelen! {#playback}

Nadat u een weergave aan een speler hebt toegewezen, levert AEM Screens as a Cloud Service de inhoud aan de speler waar deze zichtbaar is.

![staand item](assets/entrance-portrait.jpg)

![Entrance, liggend](assets/entrance-landscape.jpg)

## Volgende functies {#what-is-next}

Nu u dit deel van de AEM Toelage van de Demo van de Verwijzing hebt voltooid zou u moeten:

* De basisbeginselen van AEM Screens kennen.
* Begrijp de Web.Cafe demo-inhoud.
* Weet hoe u AEM Screens for We.Cafe kunt configureren.

U kunt nu de mogelijkheden van AEM Screens verkennen met uw eigen demo-sites. Ga door met het volgende traject, [Uw demosites beheren,](manage.md) waar u informatie krijgt over de beschikbare gereedschappen om u te helpen uw demosites te beheren en hoe u deze kunt verwijderen.

U kunt ook enkele extra bronnen bekijken die beschikbaar zijn in het dialoogvenster [Sectie Aanvullende bronnen](#additional-resources) voor meer informatie over de functies die u tijdens deze reis hebt gezien.

## Aanvullende bronnen {#additional-resources}

* [ContextHub-documentatie](/help/sites-cloud/authoring/personalization/contexthub.md) - Leer hoe ContextHub kan worden gebruikt om inhoud te personaliseren die op gebruikerscontext voorbij weersomstandigheden wordt gebaseerd.
* [API-toetsen gebruiken - Google-documentatie](https://developers.google.com/maps/documentation/javascript/get-api-key) - Een handige referentie voor meer informatie over het gebruik van Google API-sleutels.
* [Weergaven](/help/screens-cloud/creating-content/creating-displays-screens-cloud.md) - Meer informatie over wat een display in AEM Screens is en wat het kan doen.
* [Downloadspeler](/help/screens-cloud/managing-players-registration/installing-screens-cloud-player.md) - Leer hoe u toegang krijgt tot de schermspeler en hoe u deze installeert.
* [Speler registreren](/help/screens-cloud/managing-players-registration/registering-players-screens-cloud.md) - Leer hoe u een speler instelt en registreert bij uw AEM Screens-project.
* [Speler aan een Vertoning toewijzen](/help/screens-cloud/managing-players-registration/assigning-player-display.md) - Configureer een speler om uw inhoud weer te geven.
