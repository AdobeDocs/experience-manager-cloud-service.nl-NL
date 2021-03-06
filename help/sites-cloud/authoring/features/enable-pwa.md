---
title: Progressieve webtoepassingsfuncties inschakelen
description: AEM Sites stelt de auteur van de inhoud in staat om via eenvoudige configuratie progressieve webtoepassingsmogelijkheden voor elke site in te schakelen in plaats van codering.
exl-id: 1552a4ce-137a-4208-b7f6-2fc06db8dc39
source-git-commit: 3910b47c5d25679d03409380d91afaa6ff5ab265
workflow-type: tm+mt
source-wordcount: '2004'
ht-degree: 0%

---

# Progressieve webtoepassingsfuncties inschakelen {#enabling-pwa}

Dankzij een eenvoudige configuratie kan een auteur van inhoud nu functies (PWA) voor progressieve webtoepassingen inschakelen voor ervaringen die zijn gemaakt in AEM Sites.

>[!CAUTION]
>
>Dit is een geavanceerde functie die het volgende vereist:
>
>* Kennis van PWA
>* Kennis van uw site en inhoudsstructuur
>* Begrip van cachestrategieën
>* Ondersteuning van uw ontwikkelingsteam
>
>Voordat u deze functie gebruikt, wordt u aangeraden dit met uw ontwikkelingsteam te bespreken om de beste manier te definiëren om deze voor uw project te gebruiken.

## Inleiding {#introduction}

[Progressieve webapps (PWA)](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps) Maak indrukwekkende app-achtige ervaringen voor AEM sites mogelijk door ze lokaal op de computer van de gebruiker op te slaan en offline toegankelijk te maken. Een gebruiker kan onderweg door een site bladeren, zelfs als hij een internetverbinding verliest. PWA maken naadloze ervaringen mogelijk, zelfs als het netwerk verloren of instabiel is.

In plaats van dat de site opnieuw moet worden gecodeerd, kan de auteur van de inhoud de PWA-eigenschappen als een extra tabblad configureren in het dialoogvenster [pagina-eigenschappen](/help/sites-cloud/authoring/fundamentals/page-properties.md) van een locatie.

* Wanneer opgeslagen of gepubliceerd, activeert deze configuratie een gebeurtenismanager die uit schrijft [manifestbestanden](https://developer.mozilla.org/en-US/docs/Web/Manifest) en [servicearbeider](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API) die PWA-functies op de site inschakelen.
* Er worden ook segmenttoewijzingen bijgehouden om ervoor te zorgen dat de serviceworker wordt aangeboden vanuit de hoofdmap van de toepassing, zodat inhoud die buiten de app valt, kan worden vernieuwd en offline mogelijkheden worden toegestaan.

Met PWA beschikt de gebruiker over een lokale kopie van de site, zodat hij zelfs zonder internetverbinding een app-achtige ervaring heeft.

>[!NOTE]
>
>Progressieve webtoepassingen zijn een evoluerende technologie en ondersteuning voor lokale installatie van apps en andere functies [is afhankelijk van de browser die u gebruikt.](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Installable_PWAs#Summary)

## Vereisten {#prerequisites}

Als u PWA-functies voor uw site wilt gebruiken, hebt u twee vereisten voor uw projectomgeving:

1. [Basiscomponenten gebruiken](#adjust-components) om deze functie te gebruiken
1. [De verzender aanpassen](#adjust-dispatcher) regels om de vereiste bestanden beschikbaar te maken

Dit zijn technische stappen die de auteur met het ontwikkelingsteam zal moeten coördineren. Deze stappen zijn slechts eenmaal per site vereist.

### Basiscomponenten gebruiken {#adjust-components}

Core Components versie 2.15.0 en hoger biedt volledige ondersteuning voor de PWA-functies van AEM sites. Aangezien AEMaaCS altijd de nieuwste versie van de Core Components bevat, kunt u de functies van PWA offline benutten. Uw AEMaaCS-project voldoet automatisch aan deze vereiste.

>[!NOTE]
>
>Adobe raadt u niet aan de PWA-functies te gebruiken voor aangepaste componenten of voor componenten die niet [uitgebreid van de Componenten van de Kern.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/customizing.html)
<!--
Your components need to include the [manifest files](https://developer.mozilla.org/en-US/docs/Web/Manifest) and [service worker,](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API) which supports the PWA features.

 To do this, the developer will need to add the following link to the `customheaderlibs.html` file of your page component.

```xml
<link rel="manifest" href="/content/<projectName>/manifest.webmanifest" crossorigin="use-credentials"/>
```

The developer will also need to add the following link to the `customfooterlibs.html` file of your page component.

```xml
<script>
        // Check that service workers are supported
        if ('serviceWorker' in navigator) {
            // Use the window load event to make sure the page load performs well
            window.addEventListener('load', () => {
                let serviceWorker = '/<projectName>sw.js';
                navigator.serviceWorker.register(serviceWorker);
            });
        }
</script>
```
-->

### Uw Dispatcher aanpassen {#adjust-dispatcher}

De functie PWA genereert en gebruikt `/content/<sitename>/manifest.webmanifest` bestanden. Standaard, [de verzender](/help/implementing/dispatcher/overview.md) maakt dergelijke bestanden niet zichtbaar. Om deze dossiers bloot te stellen, moet de ontwikkelaar de volgende configuratie aan uw plaatsproject toevoegen.

```text
File location: [project directory]/dispatcher/src/conf.dispatcher.d/filters/filters.any >

# Allow webmanifest files
/0102 { /type "allow" /extension "webmanifest" /path "/content/*/manifest" }
```

Afhankelijk van uw project kunt u verschillende soorten uitbreidingen aan de herschrijfregels willen omvatten. De `webmanifest` uitbreiding kan nuttig zijn om in de herschrijfvoorwaarden te omvatten wanneer u een regel introduceerde die verzoeken verbergt en opnieuw richt aan `/content/<projectName>`.

```text
RewriteCond %{REQUEST_URI} (.html|.jpe?g|.png|.svg|.webmanifest)$
```

## PWA inschakelen voor uw site {#enabling-pwa-for-your-site}

Met [de voorwaarden](#prerequisites) , is het heel eenvoudig voor de auteur van de inhoud om PWA-functies in te schakelen voor een site. Hieronder volgt een basisoverzicht van hoe u dit kunt doen. Afzonderlijke opties worden gedetailleerd in de sectie [Gedetailleerde opties.](#detailed-options)

1. Meld u aan bij AEM.
1. Tik of klik in het hoofdmenu op **Navigatie** -> **Sites**.
1. Selecteer uw siteproject en tik of klik op [**Eigenschappen**](/help/sites-cloud/authoring/fundamentals/page-properties.md) of gebruik de sneltoets `p`.
1. Selecteer **Progressieve webtoepassing** en configureert u de toepasselijke eigenschappen. U wilt minimaal:
   1. Selecteer de optie **PWA inschakelen**.
   1. Definieer de **OpstartURL**.

      ![PWA inschakelen](../assets/pwa-enable.png)

   1. Upload een pictogram van 512 x 512 png naar de DAM en verwijs naar dat pictogram voor de app.

      ![Pictogram PWA definiëren](../assets/pwa-icon.png)

   1. Vorm de wegen u de de dienstarbeider offline wilt nemen. Typische paden zijn:
      * `/content/<sitename>`
      * `/content/experiencefragements/<sitename>`
      * `/content/dam/<sitename>`
      * Alle fontverwijzingen van derden
      * `/etc/clientlibs/<sitename>`

      ![Offline PWA-paden definiëren](../assets/pwa-offline.png)


1. Tik of klik op **Opslaan en sluiten**.

Uw site is nu geconfigureerd en u kunt [installeer de toepassing als een lokale toepassing.](#using-pwa-enabled-site)

## Uw site waarop PWA is ingeschakeld gebruiken {#using-pwa-enabled-site}

Nu hebt u [Uw site geconfigureerd voor ondersteuning van PWA,](#enabling-pwa-for-your-site) Je kunt het zelf ervaren.

1. Open de site in een [ondersteunde browser.](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Installable_PWAs#Summary)
1. Er verschijnt een nieuw pictogram op de adresbalk van de browser om aan te geven dat de site kan worden geïnstalleerd als een lokale app.
   * Afhankelijk van de browser kan het pictogram variëren en kan de browser ook een melding (zoals een banner of een dialoogvenster) weergeven die aangeeft dat het mogelijk is om de toepassing als een lokale app te installeren.
1. Installeer de toepassing.
1. De app wordt geïnstalleerd op het beginscherm van uw apparaat.
1. Open de app, blader een beetje, en zie dat de pagina&#39;s offline beschikbaar zijn.

## Gedetailleerde opties {#detailed-options}

In het volgende gedeelte worden meer details gegeven over de beschikbare opties wanneer [uw site configureren voor PWA.](#enabling-pwa-for-your-site)

### Installeerbare ervaring configureren {#configure-installable-experience}

Met deze instellingen kan uw site zich gedragen als een native app door deze te installeren op het thuisscherm van de bezoeker en offline beschikbaar te maken.

* **PWA inschakelen** - Dit is de hoofdschakeloptie om PWA voor de site in te schakelen.
* **OpstartURL** - Dit is de [voorkeurs start-URL](https://developer.mozilla.org/en-US/docs/Web/Manifest/start_url) dat de app wordt geopend wanneer de gebruiker de lokaal geïnstalleerde toepassing laadt.
   * Dit kan elk pad in de inhoudsstructuur zijn.
   * Dit hoeft niet de basis te zijn en is vaak een speciale welkomstpagina voor de app.
   * Als deze URL relatief is, wordt de manifest-URL gebruikt als basis-URL om deze op te lossen.
   * Als deze functie leeg blijft, gebruikt deze het adres van de webpagina van waaruit de webtoepassing is geïnstalleerd.
   * U wordt aangeraden een waarde in te stellen.
* **Weergavemodus** - Een app waarvoor PWA is ingeschakeld, is nog steeds een AEM die via een browser wordt geleverd. [Deze weergaveopties](https://developer.mozilla.org/en-US/docs/Web/Manifest/display) Hiermee bepaalt u hoe de browser moet worden verborgen of op een andere manier aan de gebruiker op het lokale apparaat moet worden weergegeven.
   * **Zelfstandig** - De browser is volledig verborgen voor de gebruiker en lijkt een native app. Dit is de standaardwaarde.
      * Met deze optie moet toepassingsnavigatie volledig door uw inhoud gebruikend verbindingen en componenten op de pagina&#39;s van de plaats zonder de browser navigatiecontroles mogelijk zijn.
   * **Browser** - De browser wordt op dezelfde manier weergegeven als wanneer u de site bezoekt.
   * **Minimale interface** - De browser is meestal verborgen, zoals een native app, maar de standaardbesturingselementen voor navigatie worden weergegeven.
   * **Volledig scherm** - De browser is volledig verborgen, zoals een native app, maar wordt weergegeven in de modus Volledig scherm.
      * Met deze optie moet toepassingsnavigatie volledig door uw inhoud gebruikend verbindingen en componenten op de pagina&#39;s van de plaats zonder de browser navigatiecontroles mogelijk zijn.
* **Schermoriëntatie** - Als lokale app moet de PWA weten hoe ze moet omgaan [apparaatoriëntaties.](https://developer.mozilla.org/en-US/docs/Web/Manifest/orientation)
   * **Alle** - De app past de oriëntatie van het apparaat van de gebruiker aan. Dit is de standaardwaarde.
   * **Staand** - Hierdoor wordt de toepassing met een staande lay-out geopend, ongeacht de richting van het apparaat van de gebruiker.
   * **Liggend** - Hierdoor wordt de toepassing gedwongen liggend te openen, ongeacht de richting van het apparaat van de gebruiker.
* **Themakleur** - Hiermee worden de [kleur van de app](https://developer.mozilla.org/en-US/docs/Web/Manifest/theme_color) dat beïnvloedt hoe het werkende systeem van de lokale gebruiker de inheemse toolbar UI en navigatiecontroles toont. Afhankelijk van de browser kan dit invloed hebben op andere presentatie-elementen van de app.
   * Gebruik het pop-upvenster Kleurenvak om een kleur te selecteren.
   * De kleur kan ook worden gedefinieerd door hexadecimale waarde of door de waarde RGB.
* **Achtergrondkleur** - Hiermee worden de [achtergrondkleur van de app,](https://developer.mozilla.org/en-US/docs/Web/Manifest/background_color) wordt weergegeven terwijl de toepassing wordt geladen.
   * Gebruik het pop-upvenster Kleurenvak om een kleur te selecteren.
   * De kleur kan ook worden gedefinieerd door hexadecimale waarde of door de waarde RGB.
   * Bepaalde browsers [automatisch een welkomstscherm maken](https://developer.mozilla.org/en-US/docs/Web/Manifest#Splash_screens) in de toepassingsnaam, achtergrondkleur en pictogram.
* **Pictogram** - Deze definitie [het pictogram](https://developer.mozilla.org/en-US/docs/Web/Manifest/icons) die de toepassing op het apparaat van de gebruiker vertegenwoordigt.
   * Het pictogram moet een png-bestand van 512x512 pixels zijn.
   * Het pictogram moet [opgeslagen in DAM.](/help/assets/overview.md)

### Cachebeheer (geavanceerd) {#offline-configuration}

Deze instellingen stellen delen van deze site offline beschikbaar en lokaal beschikbaar op het apparaat van uw bezoeker. Hierdoor kunt u de cache van de webtoepassing beheren om netwerkaanvragen te optimaliseren en offline ervaringen te ondersteunen.

* **Caching strategie en frequentie van inhoudvernieuwing** - Deze instelling definieert het cachemodel voor uw PWA.
   * **Matig** - [Deze instelling](https://web.dev/stale-while-revalidate/) is het geval voor de meeste plaatsen en is de standaardwaarde.
      * Met deze instelling wordt de inhoud die eerst door de gebruiker wordt weergegeven, vanuit de cache geladen en terwijl de gebruiker die inhoud gebruikt, wordt de rest van de inhoud in de cache opnieuw gevalideerd.
   * **Vaak** - Dit is het geval voor sites die updates nodig hebben, om heel snel te zijn, zoals veilinghuizen.
      * Met deze instelling zoekt de toepassing eerst naar de meest recente inhoud via het netwerk en als deze niet beschikbaar is, wordt de lokale cache hersteld.
   * **Zelden** - Dit is het geval voor plaatsen die bijna statisch zijn zoals verwijzingspagina&#39;s.
      * Met deze instelling zoekt de toepassing eerst naar de inhoud in de cache en als deze niet beschikbaar is, wordt deze teruggezet naar het netwerk om de inhoud op te halen.
* **Bestanden vooraf in cache plaatsen** - Deze bestanden die op AEM worden gehost, worden in de lokale browsercache opgeslagen wanneer de serviceworker installeert en voordat deze wordt gebruikt. Dit garandeert dat de webtoepassing volledig functioneert wanneer deze offline is.
* **Paden opnemen** - Netwerkverzoeken voor de gedefinieerde paden worden onderschept en inhoud in de cache wordt geretourneerd in overeenstemming met de geconfigureerde **Caching strategie en frequentie van inhoudvernieuwing**.
* **Uitsluitingen cache** - Deze bestanden worden nooit in cache geplaatst, ongeacht de instellingen onder **Bestanden vooraf in cache plaatsen** en **Padinsluitingen**.

>[!TIP]
>
>Uw ontwikkelingsteam heeft waarschijnlijk waardevolle input betreffende hoe uw off-line configuratie zou moeten opstelling.

## Beperkingen en Recommendations {#limitations-recommendations}

Niet alle PWA-functies zijn beschikbaar voor AEM Sites. Dit zijn een paar opmerkelijke beperkingen.

* Pagina&#39;s worden niet automatisch gesynchroniseerd of bijgewerkt als de gebruiker de app niet gebruikt.

Adobe doet ook de volgende aanbevelingen wanneer u PWA uitvoert.

### Minimaliseer het aantal middelen aan pre-geheime voorgeheugen. {#minimize-precache}

Adobe raadt u aan het aantal pagina&#39;s te beperken tot voorcaching.

* Bibliotheken insluiten om het aantal items te verminderen dat moet worden beheerd bij het in cache plaatsen.
* Beperk het aantal afbeeldingsvariaties tot het aantal vooraf in de cache plaatsen.

### Schakel PWA in nadat de projectscripts en -opmaakmodellen zijn gestabiliseerd. {#pwa-stabilized}

Clientbibliotheken worden geleverd met de toevoeging van een cacheselectiekader, waarbij het volgende patroon wordt gevolgd `lc-<checksumHash>-lc`. Elke keer dat een van de bestanden (en afhankelijkheden) waaruit een bibliotheekwijziging bestaat, wordt deze kiezer gewijzigd. Als u een cliënt-bibliotheek vermeld die door de dienst-arbeider moet worden pre-caching en u naar een nieuwe versie wilt verwijzen, wint u manueel de ingang terug en werkt bij. Dientengevolge, adviseren wij u om uw plaats te vormen om een PWA te zijn nadat de projectmanuscripten en stylesheets worden gestabiliseerd.

### Beperk het aantal afbeeldingsvariaties tot een minimum. {#minimize-variations}

De afbeeldingscomponent van de AEM Core Components bepaalt een van de voorste uiteinden van de beste uitvoering die moet worden opgehaald. Dit mechanisme bevat ook een tijdstempel die overeenkomt met de laatste gewijzigde tijd van die bron. Dit mechanisme compliceert de configuratie van PWA pre-geheime voorgeheugen.

Wanneer het vormen van pre-geheime voorgeheugen, moet de gebruiker alle wegvariaties vermelden die kunnen worden gehaald. Deze variaties bestaan uit parameters zoals kwaliteit en breedte. Het wordt ten zeerste aanbevolen het aantal van deze variaties te beperken tot maximaal drie - klein, middelgroot, groot. U kunt dat doen via de inhoudspolitieke dialoog van het [Afbeeldingscomponent.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/image.html)

Als niet zorgvuldig gevormd, kunnen het geheugen en het netwerkgebruik de prestaties van uw PWA ernstig beïnvloeden. Ook als u bijvoorbeeld 50 afbeeldingen wilt vooraf instellen en 3 breedten per afbeelding wilt hebben, moet de gebruiker die de site beheert een lijst met maximaal 150 items bijhouden in de sectie PWA pre-cache van de pagina-eigenschappen.

Adobe raadt u ook aan uw site te configureren als een PWA nadat het gebruik van afbeeldingen in het project is gestabiliseerd.
