---
title: Progressieve webtoepassingsfuncties inschakelen
description: AEM Sites stelt de auteur van de inhoud in staat om via eenvoudige configuratie progressieve webtoepassingsmogelijkheden voor elke site in te schakelen in plaats van codering.
exl-id: 1552a4ce-137a-4208-b7f6-2fc06db8dc39
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 4c4e05ae636701d914b654b7342a4bc2403c56c0
workflow-type: tm+mt
source-wordcount: '1926'
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
>Alvorens deze eigenschap te gebruiken, adviseert de Adobe dat u dit met uw ontwikkelingsteam bespreekt om de beste manier te bepalen om het voor uw project te gebruiken.

>[!IMPORTANT]
>
>De functies voor progressieve webapps (PWA) voor AEM Sites zijn verouderd.
>
>Bestaande projecten die gebruikmaken van deze functie blijven ondersteund, maar nieuwe projecten moeten deze functie niet gebruiken.

## Inleiding {#introduction}

[ Progressieve Web apps (PWA) ](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps) laat immersieve app-achtige ervaringen voor AEM plaatsen toe door hen toe te staan om plaatselijk op de machine van een gebruiker worden opgeslagen en offline toegankelijk zijn. Een gebruiker kan onderweg door een site bladeren, zelfs als hij een internetverbinding verliest. PWA maken een naadloze ervaring mogelijk, zelfs als het netwerk verloren of instabiel is.

In plaats van het vereisen van om het even welke hercodering van de plaats, kan een inhoudauteur PWA eigenschappen als extra lusje in de [ pagina eigenschappen ](/help/sites-cloud/authoring/sites-console/page-properties.md) van een plaats vormen.

* Wanneer bewaard of gepubliceerd, brengt deze configuratie een gebeurtenismanager teweeg die de [ duidelijke dossiers ](https://developer.mozilla.org/en-US/docs/Web/Manifest) en a [ de dienstarbeider ](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API) schrijft die PWA eigenschappen op de plaats toelaten.
* Er worden ook segmenttoewijzingen bijgehouden om ervoor te zorgen dat de serviceworker wordt aangeboden vanuit de hoofdmap van de toepassing, zodat inhoud die buiten de app valt, kan worden vernieuwd en offline mogelijkheden worden toegestaan.

Met PWA beschikt de gebruiker over een lokale kopie van de site, zodat hij zelfs zonder internetverbinding een app-achtige ervaring heeft.

>[!NOTE]
>
>De progressieve Web apps zijn evoluerende technologie en steun voor lokale app installatie en andere eigenschappen [ hangt van welke browser af u gebruikt.](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Tutorials/js13kGames/Installable_PWAs#summary)

## Vereisten {#prerequisites}

Als u PWA-functies voor uw site wilt gebruiken, hebt u twee vereisten voor uw projectomgeving:

1. [ Componenten van de Kern van het Gebruik ](#adjust-components) om uit deze eigenschap voordeel te halen
1. [ pas uw Dispatcher ](#adjust-dispatcher) regels aan om de vereiste dossiers bloot te stellen

Dit zijn technische stappen die de auteur met het ontwikkelingsteam moet coördineren. Deze stappen zijn slechts eenmaal per site vereist.

### Core-componenten gebruiken {#adjust-components}

Core Components versie 2.15.0 en hoger ondersteunen de PWA-functies van AEM sites volledig. Aangezien AEMaaCS altijd de nieuwste versie van de Core Components bevat, kunt u de functies van PWA uit-van-de-doos gebruiken. Uw AEMaaCS-project voldoet automatisch aan deze vereiste.

>[!NOTE]
>
>De Adobe adviseert niet gebruikend de eigenschappen van de PWA op douanecomponenten of componenten niet [ uitgebreid van de Componenten van de Kern.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/customizing.html)
<!--
Your components need to include the [manifest files](https://developer.mozilla.org/en-US/docs/Web/Manifest) and [service worker,](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API) which supports the PWA features.

 To do this, the developer adds the following link to the `customheaderlibs.html` file of your page component.

```xml
<link rel="manifest" href="/content/<projectName>/manifest.webmanifest" crossorigin="use-credentials"/>
```

The developer also adds the following link to the `customfooterlibs.html` file of your page component.

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

### Je Dispatcher aanpassen {#adjust-dispatcher}

De functie PWA genereert en gebruikt `/content/<sitename>/manifest.webmanifest` bestanden. Door gebrek, [ stelt Dispatcher ](/help/implementing/dispatcher/overview.md) dergelijke dossiers niet bloot. Om deze dossiers bloot te stellen, moet de ontwikkelaar de volgende configuratie aan uw plaatsproject toevoegen.

```text
File location: [project directory]/dispatcher/src/conf.dispatcher.d/filters/filters.any >

# Allow webmanifest files
/0102 { /type "allow" /extension "webmanifest" /path "/content/*/manifest" }
```

Afhankelijk van uw project, kunt u verschillende soorten uitbreidingen aan de herschrijfregels willen omvatten. De extensie `webmanifest` kan handig zijn om bij het herschrijven ook een regel op te nemen die verzoeken aan `/content/<projectName>` verbergt en doorstuurt.

```text
RewriteCond %{REQUEST_URI} (.html|.jpe?g|.png|.svg|.webmanifest)$
```

## PWA inschakelen voor uw site {#enabling-pwa-for-your-site}

Met [ voldaan aan eerste vereisten ](#prerequisites), is het voor een inhoudauteur gemakkelijk om de eigenschappen van PWA aan een plaats toe te laten. Hieronder volgt een basisoverzicht van hoe u dit kunt doen. De individuele opties zijn gedetailleerd in de sectie [ Gedetailleerde Opties.](#detailed-options)

1. Log in AEM.
1. Van het belangrijkste menu, uitgezochte **Navigatie** > **Plaatsen**.
1. Selecteer uw plaatsproject en selecteer [**Eigenschappen**](/help/sites-cloud/authoring/sites-console/page-properties.md) of gebruik hotkey `p`.
1. Selecteer het **Progressieve lusje van App van het Web** en vorm de toepasselijke eigenschappen. U wilt ten minste:
   1. Selecteer de optie **PWA** toelaten.
   1. Bepaal **Opstarten URL**.

      ![ laat PWA ](../assets/pwa-enable.png) toe

   1. Upload een pictogram van 512 x 512 png naar de DAM en verwijs naar dat pictogram voor de app.

      ![ bepalen PWA pictogram ](../assets/pwa-icon.png)

   1. Configureer de paden die de serviceworker offline moet gebruiken. Typische paden zijn:
      * `/content/<sitename>`
      * `/content/experiencefragements/<sitename>`
      * `/content/dam/<sitename>`
      * Eventuele verwijzingen naar lettertypen van derden
      * `/etc/clientlibs/<sitename>`

      ![ bepaalt PWA off-line wegen ](../assets/pwa-offline.png)

1. Selecteer **sparen &amp; Sluiten**.

Uw plaats wordt nu gevormd en u kunt [ het als lokale app installeren.](#using-pwa-enabled-site)

## Uw site waarop PWA is ingeschakeld gebruiken {#using-pwa-enabled-site}

Nu u [ uw plaats hebt gevormd om PWA te steunen, ](#enabling-pwa-for-your-site) kunt u het voor zich ervaren.

1. Heb toegang tot de plaats in a [ gesteunde browser ](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Tutorials/js13kGames/Installable_PWAs#summary).
1. Er verschijnt een nieuw pictogram op de adresbalk van de browser om aan te geven dat de site kan worden geïnstalleerd als een lokale app.
   * Afhankelijk van de browser kan het pictogram variëren en kan de browser ook een melding (zoals een banner of een dialoogvenster) weergeven die aangeeft dat het mogelijk is om de toepassing als een lokale app te installeren.
1. Installeer de toepassing.
1. De app is geïnstalleerd op het beginscherm van uw apparaat.
1. Open de app, blader een beetje, en zie dat de pagina&#39;s offline beschikbaar zijn.

## Gedetailleerde opties {#detailed-options}

De volgende sectie verstrekt meer detail op de beschikbare opties wanneer [ vormend uw plaats voor PWA.](#enabling-pwa-for-your-site)

### Installeerbare ervaring configureren {#configure-installable-experience}

Met deze instellingen kan uw site zich gedragen als een native app door deze installeerbaar te maken op het thuisscherm van de bezoeker en offline beschikbaar te stellen.

* **laat PWA** toe - dit is de belangrijkste knevel voor het toelaten van PWA voor de plaats.
* **Opstarten URL** - dit is het [ aangewezen begin URL ](https://developer.mozilla.org/en-US/docs/Web/Manifest/start_url) dat app opent wanneer de gebruiker plaatselijk geïnstalleerde app laadt.
   * Dit kan elk pad in de inhoudsstructuur zijn.
   * Dit hoeft niet de basis te zijn en is vaak een speciale welkomstpagina voor de app.
   * Als deze URL relatief is, wordt de manifest-URL gebruikt als basis-URL om deze op te lossen.
   * Als de functie leeg blijft, gebruikt deze het adres van de webpagina vanwaar de app is geïnstalleerd.
   * U wordt aangeraden een waarde in te stellen.
* **wijze van de Vertoning** - Een PWA-Toegelaten app is nog een AEM plaats die door browser wordt geleverd. [ Deze vertoningsopties ](https://developer.mozilla.org/en-US/docs/Web/Manifest/display) bepalen hoe browser zou moeten worden verborgen of anders aan de gebruiker op het lokale apparaat worden voorgesteld.
   * **Zelfstandig** - browser is verborgen van de gebruiker en het lijkt als inheemse app. Dit is de standaardwaarde.
      * Met deze optie moet toepassingsnavigatie volledig door uw inhoud gebruikend verbindingen en componenten op de pagina&#39;s van de plaats zonder de browser navigatiecontroles mogelijk zijn.
   * **Browser** - browser verschijnt aangezien het normaal wanneer het bezoeken van de plaats zou.
   * **Minimale UI** - browser is meestal verborgen, als inheemse app, maar de basisnavigatie controles worden blootgesteld.
   * **Volledig Scherm** - browser is verborgen, als inheemse app, maar op het volledige schermwijze teruggegeven.
      * Met deze optie moet toepassingsnavigatie volledig door uw inhoud gebruikend verbindingen en componenten op de pagina&#39;s van de plaats zonder de browser navigatiecontroles mogelijk zijn.
* **de richtlijn van het Scherm** - als lokale app, moet de PWA weten hoe te om [ apparatenrichtingen ](https://developer.mozilla.org/en-US/docs/Web/Manifest/orientation) te behandelen.
   * **om het even welk** - app past aan de richtlijn van het apparaat van de gebruiker aan. Dit is de standaardwaarde.
   * **Portret** - dit dwingt app om in portretlay-out ongeacht de richtlijn van het apparaat van de gebruiker te openen.
   * **Liggend** - dit dwingt app om in landschaplay-out ongeacht de richtlijn van het apparaat van de gebruiker te openen.
* **kleur van het Thema** - dit bepaalt de [ kleur van app ](https://developer.mozilla.org/en-US/docs/Web/Manifest/theme_color) die beïnvloedt hoe het werkende systeem van de lokale gebruiker de inheemse toolbar UI en navigatiecontroles toont. Afhankelijk van de browser kan dit invloed hebben op andere presentatie-elementen van de app.
   * Selecteer een kleur met het pop-upmenu Kleurenvak.
   * De kleur kan ook worden gedefinieerd door hexadecimale waarde of door de waarde RGB.
* **Achtergrondkleur** - dit bepaalt de [ achtergrondkleur van app ](https://developer.mozilla.org/en-US/docs/Web/Manifest/background_color), die wordt getoond aangezien app laadt.
   * Selecteer een kleur met het pop-upmenu Kleurenvak.
   * De kleur kan ook worden gedefinieerd door hexadecimale waarde of door de waarde RGB.
   * Bepaalde browsers [ bouwen automatisch een welkomstscherm ](https://developer.mozilla.org/en-US/docs/Web/Manifest#Splash_screens) van de toepassingsnaam, achtergrondkleur, en pictogram.
* **Pictogram** - dit bepaalt [ het pictogram ](https://developer.mozilla.org/en-US/docs/Web/Manifest/icons) dat app op het apparaat van de gebruiker vertegenwoordigt.
   * Het pictogram moet een png-bestand van 512x512 pixels zijn.
   * Het pictogram moet [ worden opgeslagen in DAM ](/help/assets/overview.md).

### Cachebeheer (geavanceerd) {#offline-configuration}

Deze instellingen stellen delen van deze site offline beschikbaar en lokaal beschikbaar op het apparaat van uw bezoeker. Hierdoor kunt u de cache van de webtoepassing beheren om netwerkaanvragen te optimaliseren en offline ervaringen te ondersteunen.

* **Caching strategie en frequentie van inhoud verfrissen zich** - Dit het plaatsen bepaalt het caching model voor uw PWA.
   * **Gematigd** - [ Dit het plaatsen ](https://web.dev/stale-while-revalidate/) is het geval voor de meeste plaatsen en is de standaardwaarde.
      * Met deze instelling wordt de inhoud die de gebruiker voor het eerst bekijkt, geladen uit de cache en terwijl de gebruiker die inhoud gebruikt, wordt de rest van de inhoud in de cache opnieuw gevalideerd.
   * **vaak** - dit is het geval voor plaatsen die updates nodig hebben om snel zoals veilinghuizen te zijn.
      * Met deze instelling zoekt de app eerst naar de meest recente inhoud via het netwerk en als deze niet beschikbaar is, wordt de lokale cache opnieuw opgehaald.
   * **Zelden** - dit is het geval voor plaatsen die bijna statisch zoals verwijzingspagina&#39;s zijn.
      * Met deze instelling zoekt de toepassing eerst naar de inhoud in de cache en als deze niet beschikbaar is, wordt de inhoud teruggezet naar het netwerk om deze op te halen.
* **Dossier pre-caching** - Deze die dossiers op AEM worden ontvangen worden bewaard aan het lokale browser geheime voorgeheugen wanneer de de dienstarbeider installeert en alvorens het wordt gebruikt. Dit garandeert dat de webtoepassing volledig functioneert wanneer deze offline is.
* **de uitbreidingen van Wegen** - de verzoeken van het netwerk voor de bepaalde wegen worden onderschept en de caching inhoud is terugkeer in overeenstemming met de gevormde **Caching strategie en de frequentie van inhoud verfrissen zich**.
* **uitsluitingen van het Geheime voorgeheugen** - Deze dossiers worden nooit in het voorgeheugen ondergebracht ongeacht de montages onder **Dossier pre-caching** en **de uitbreidingen van de Weg**.

>[!TIP]
>
>Uw ontwikkelingsteam heeft waarschijnlijk waardevolle input betreffende hoe uw off-line configuratie zou moeten opstelling.

## Beperkingen en Recommendations {#limitations-recommendations}

Niet alle PWA-functies zijn beschikbaar voor AEM Sites. Dit zijn een paar opmerkelijke beperkingen.

* Pagina&#39;s worden niet automatisch gesynchroniseerd of bijgewerkt als de gebruiker de app niet gebruikt.

Adobe raadt ook het volgende aan wanneer u PWA implementeert.

### Minimaliseer het aantal middelen aan pre-geheime voorgeheugen. {#minimize-precache}

Adobe raadt u aan het aantal pagina&#39;s te beperken tot het aantal pagina&#39;s dat in de cache wordt geplaatst.

* Bibliotheken insluiten zodat u het aantal te beheren items bij het in cache plaatsen kunt verminderen.
* Beperk het aantal afbeeldingsvariaties tot het aantal vooraf in de cache plaatsen.

### Schakel PWA in nadat de projectscripts en -stijlpagina&#39;s zijn gestabiliseerd. {#pwa-stabilized}

Clientbibliotheken worden geleverd met de toevoeging van een cacheselectiekader, waarbij het volgende patroon wordt weergegeven `lc-<checksumHash>-lc` . Telkens wanneer een van de bestanden (en afhankelijkheden) waaruit een bibliotheek bestaat, wordt gewijzigd, verandert deze kiezer. Als u een cliënt-bibliotheek vermeld die door de dienst-arbeider moet worden pre-caching en u naar een nieuwe versie wilt verwijzen, wint u manueel de ingang terug en werkt bij. Dientengevolge, adviseert de Adobe dat u uw plaats vormt om een PWA te zijn nadat de projectmanuscripten, en de stijlbladen, worden gestabiliseerd.

### Minimaliseer het aantal afbeeldingsvariaties. {#minimize-variations}

De afbeeldingscomponent van de AEM Core Components bepaalt een van de voorste uiteinden van de beste uitvoering die moet worden opgehaald. Dit mechanisme bevat ook een tijdstempel die overeenkomt met de laatste gewijzigde tijd van die bron. Dit mechanisme compliceert de configuratie van PWA pre-geheime voorgeheugen.

Wanneer het vormen van pre-geheime voorgeheugen, moet de gebruiker van alle wegvariaties een lijst maken die kunnen worden gehaald. Deze variaties bestaan uit parameters zoals kwaliteit en breedte. U wordt geadviseerd het aantal van deze variaties te verminderen tot maximaal drie - klein, middelgroot, groot. U kunt dat als inhoud-beleid dialoogdoos van de [ Component van het Beeld doen ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/image.html).

Als niet zorgvuldig gevormd, kunnen het geheugen en het netwerkgebruik de prestaties van uw PWA ernstig beïnvloeden. Als u bijvoorbeeld 50 afbeeldingen wilt vooraf instellen en drie breedten per afbeelding wilt hebben, moet de gebruiker die de site beheert, een lijst met maximaal 150 items bijhouden in de sectie PWA pre-cache van de pagina-eigenschappen.

Adobe raadt u ook aan uw site te configureren als een PWA nadat het gebruik van afbeeldingen in het project is gestabiliseerd.
