---
title: Regels voor gegevensbescherming en gegevensbescherming - gereedheid voor Adobe Experience Manager as a Cloud Service-sites
description: Leer over de steun van de Plaatsen van Adobe Experience Manager as a Cloud Service voor de diverse Regels van de Bescherming van Gegevens en van de Privacy van Gegevens; met inbegrip van de Algemene Verordening van de EU van de Bescherming van Gegevens (GDPR), de Wet van de Consumentenprivacy van Californië en hoe te om te voldoen wanneer het uitvoeren van een nieuw project van AEM as a Cloud Service.
exl-id: fdcad111-0cdd-46cc-964c-3f8669ca2030
feature: Compliance
role: Admin, Architect, Developer, Leader
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '1001'
ht-degree: 0%

---

# Adobe Experience Manager as a Cloud Service Site Readiness for Data Protection and Data Privacy Regulations {#aem-sites-readiness-for-data-protection-and-data-privacy-regulations}

>[!WARNING]
>
>De inhoud van dit document is geen juridisch advies en is niet bedoeld als vervanging van juridisch advies.
>
>Raadpleeg de juridische afdeling van uw bedrijf voor advies over regelgeving inzake gegevensbescherming en gegevensbescherming.

>[!NOTE]
>
>Voor meer informatie over de reactie van de Adobe op privacykwesties, en wat dit voor u als Adobe klant betekent, zie ](https://www.adobe.com/privacy.html) het Centrum van de Privacy van de Adobe van 0} {.[

Adobe Experience Manager as a Cloud Service Sites is klaar om klanten te helpen bij hun verplichtingen inzake privacy en bescherming van gegevens. Deze pagina begeleidt klanten door de procedures om dergelijke verzoeken in AEM Sites te behandelen. Hierin wordt de locatie van opgeslagen privégegevens beschreven en hoe deze handmatig of met code kunnen worden verwijderd.

Voor meer informatie, zie het [ Centrum van de Privacy van de Adobe ](https://www.adobe.com/privacy.html).

>[!NOTE]
>
>Zie [ Adobe Experience Manager as a Cloud Service Readiness voor de Regels van de Privacy van Gegevens en van Gegevens ](/help/compliance/data-privacy-and-protection-readiness/aem-readiness.md) voor verdere details.

## AEM-auteurlaag {#aem-author-tier}

De rekeningen van de gebruiker en de inhoud UGC op de auteurserver zijn behandeld in de [ documentatie van de Stichting AEM ](/help/compliance/data-privacy-and-protection-readiness/foundation-readiness.md).

## AEM-publicatielaag {#aem-publish-tier}

De rekeningen van de gebruiker worden gebruikt om bezoekers op de plaats voor authentiek te verklaren, en de inhoud UGC op publiceer server wordt behandeld in de [ documentatie van de Stichting AEM ](/help/compliance/data-privacy-and-protection-readiness/aem-readiness.md).

Standaard slaan AEM Sites-componenten geen formuliergegevens op die bezoekers op de publicatieserver hebben ingevoerd. Het wordt aanbevolen de gegevens naar een systeem van derden of naar Adobe Campaign te sturen voor verdere verwerking.

## Opt-in/Opt-out {#opt-in-opt-out}

<!--
AEM has a [cookie opt-out service](/help/sites-developing/cookie-optout.md ) that can be used for managing the opt-in/opt-out for users.
-->

Adobe Experience Manager is onderworpen aan een cookie-uitschakelservice die wordt gebruikt voor het beheer van de opt-in/opt-out voor gebruikers.

Naar Weigeren:

1. Navigeren naar:
   [ het Centrum van de Privacy van de Adobe - Opt-uit ](https://www.adobe.com/privacy/opt-out.html)

1. De rol neer aan **Diensten** - **gegevens van het de dienstgebruik van de Experience Cloud**.

1. Selecteer de referenced verbinding; momenteel genoemd **hier**.

1. U krijgt de volgende details te zien, samen met de opties om te weigeren of in te schakelen:

   * Als u aggregatie en analyse van gegevens over uw bezoek aan deze site wilt uitschakelen, moet u een cookie installeren op uw browser. Deze cookie identificeert dat u hebt uitgekozen.

     Als u de uitschakelcookie verwijdert of als u van computer of webbrowser verandert, moet u de functie opnieuw uitschakelen.

     Uitschakelen - Sluit mij uit van aggregatie en analyse van bezoekerssessies (installeer de `amcglobal.sc.omtrdc.net` -uitschakelcookie) - Klik hier.

     Inschakelen - Neem mij op in aggregatie en analyse van bezoekerssessies (installeer de `amcglobal.sc.omtrdc.net` -uitschakelcookie niet) - Klik hier.

   Voer de bovenstaande stappen uit om de werkelijke koppelingen te openen.

   >[!NOTE]
   >
   > Er is een verdere beschrijving in **2. Privacy.** sectie van de [ Algemene Voorwaarden van de Adobe van Gebruik ](https://www.adobe.com/legal/terms.html).

## Analytics Foundation {#analytics-foundation}

AEM Sites biedt een optionele integratie met de Analytics Foundation, die gebruik maakt van functionaliteit binnen de Adobe Analytics On-demand Service.

Voor meer informatie bij het beheren van de verzoeken van het gegevenssubject met betrekking tot Adobe Analytics zie [ Adobe Analytics en de Privacy van Gegevens ](https://experienceleague.adobe.com/docs/analytics/admin/data-governance/gdpr-view-settings.html).

## Personalization Foundation by Target {#personalization-foundation-by-target}

AEM Sites bevat een optionele integratie met Personalization Foundation by Target, die gebruikmaakt van functionaliteit binnen de Adobe Target On-demand Service.

Voor informatie over het beheren van de verzoeken van het gegevenssubject met betrekking tot Adobe Target zie [ Adobe Target - de Privacy en Algemene Verordening van de Bescherming van Gegevens ](https://experienceleague.adobe.com/docs/target-dev/developer/implementation/privacy/cmp-privacy-and-general-data-protection-regulation.html).

## ContextHub {#contexthub}

<!--
AEM provides an optional data layer with [ContextHub](/help/sites-developing/contexthub.md).
-->

AEM verstrekt een facultatieve gegevenslaag met ContextHub. Dit houdt bezoekersspecifieke gegevens in browser, die voor op regel-gebaseerde verpersoonlijking moeten worden gebruikt.

Door gebrek, wordt dit bezoeker-gegeven niet opgeslagen in AEM; AEM verzendt regels naar de gegevenslaag om verpersoonlijkingsbesluiten in browser te nemen.

### Opt-in/Opt-out implementeren {#implementing-opt-in-opt-out}

De eigenaar van de site moet een opt-out-component implementeren in overeenstemming met de volgende richtlijnen.

Deze richtlijnen voeren opt-in als gebrek uit. Daarom moet een websitebezoeker duidelijk hiermee instemmen, voordat persoonlijke gegevens worden opgeslagen in de (client-side) persistentie van de browser.

* De opt-out component zou moeten worden omvat telkens als de component ContextHub inbegrepen is.
* De bepalingen en voorwaarden die betrekking hebben op gegevensbescherming en privacy voor de website moeten aan de websitebezoeker worden getoond, zodat deze:

   * accepteren
   * afwijzen
   * vorige keuze wijzigen

* Als een plaatsbezoeker de voorwaarden van de plaats goedkeurt, zou het opt-outkoekje ContextHub moeten worden verwijderd:

  ```
  ContextHub.Utils.Cookie.removeItem('cq-opt-out');
  ```

* Als een plaatsbezoeker niet de voorwaarden van de plaats goedkeurt, zou het opt-out van ContextHub koekje moeten worden geplaatst:

  ```
  ContextHub.Utils.Cookie.setItem('cq-opt-out', 1);
  ```

* Om te controleren of ContextHub op opt-out wijze loopt, zou de volgende vraag in de browser console moeten worden gemaakt:

  ```
  var isOptedOut = ContextHub.isOptedOut(true) === true;
  // if isOptedOut is true, ContextHub is running in opt-out mode
  ```

### Previewing persistentie van ContextHub {#previewing-persistence-of-contexthub}

Aan voorproefpersistentie gebruikt ContextHub, kan een gebruiker:

* Gebruik de browserconsole, bijvoorbeeld:

   * Chrome:

      * Open Developer Tools > Application > Storage:

         * Local Storage > (website) > ContextHubPersistence
         * Session Storage > (website) > ContextHubPersistence
         * Cookies > (website) > SessionPersistence

   * Firefox:

      * Open Developer Tools > Storage:

         * Local Storage > (website) > ContextHubPersistence
         * Session Storage > (website) > ContextHubPersistence
         * Cookies > (website) > SessionPersistence

   * Safari:

      * Open Voorkeuren > Geavanceerd > Ontwikkelmenu tonen in menubalk
      * Ontwikkelen openen > JavaScript-console tonen

         * Console > Opslag > Lokale Opslag > (website) > ContextHubPersistence
         * Console > Opslag > Sessieopslag > (website) > ContextHubPersistence
         * Console > Opslag > Cookies > (website) > ContextHubPersistence

   * Internet Explorer:

      * Developer Tools openen > Console

         * `localStorage.getItem('ContextHubPersistence')`
         * `sessionStorage.getItem('ContextHubPersistence')`
         * `document.cookie`

* Gebruik ContextHub API, in de browser console:

   * ContextHub biedt de volgende gegevenspersistentielagen:

      * `ContextHub.Utils.Persistence.Modes.LOCAL` (standaardwaarde)
      * `ContextHub.Utils.Persistence.Modes.SESSION`
      * `ContextHub.Utils.Persistence.Modes.COOKIE`
      * `ContextHub.Utils.Persistence.Modes.WINDOW`

     De opslag ContextHub bepaalt welke persistentielaag wordt gebruikt, zo om de huidige staat van persistentie te bekijken alle lagen zouden moeten worden gecontroleerd.

Als u bijvoorbeeld gegevens wilt weergeven die zijn opgeslagen in localStorage:

Aan voorproefpersistentie gebruikt ContextHub, kan een gebruiker:

* Gebruik de browserconsole:

   * Chrome - open Developer Tools > Application > Storage:

      * Local Storage > (website) > ContextHubPersistence
      * Session Storage > (website) > ContextHubPersistence
      * Cookies > (website) > SessionPersistence

   * Firefox - open Developer Tools > Storage:

      * Local Storage > (website) > ContextHubPersistence
      * Session Storage > (website) > ContextHubPersistence
      * Cookies > (website) > SessionPersistence

* Gebruik ContextHub API, in de browser console:

   * ContextHub biedt de volgende gegevenspersistentielagen:

      * `ContextHub.Utils.Persistence.Modes.LOCAL` (standaardwaarde)
      * `ContextHub.Utils.Persistence.Modes.SESSION`
      * `ContextHub.Utils.Persistence.Modes.COOKIE`
      * `ContextHub.Utils.Persistence.Modes.WINDOW`

     De opslag ContextHub bepaalt welke persistentielaag wordt gebruikt, zo om de huidige staat van persistentie te bekijken alle lagen zouden moeten worden gecontroleerd.

Als u bijvoorbeeld gegevens wilt weergeven die zijn opgeslagen in localStorage:

```
var storage = new ContextHub.Utils.Persistence({ mode: ContextHub.Utils.Persistence.Modes.LOCAL });
console.log(storage.getTree());
```

### De persistentie van ContextHub wissen {#clearing-persistence-of-contexthub}

Om de persistentie te ontruimen ContextHub:

* Om persistentie van momenteel geladen opslag te ontruimen:

  ```
  // to be able to fully access persistence layer, Opt-Out must be turned off
  ContextHub.Utils.Cookie.removeItem('cq-opt-out');
  
  // following call asks all currently loaded stores to clear their data
  ContextHub.cleanAllStores();
  
  // following call asks all currently loaded stores to set back default values (provided in their configs)
  ContextHub.resetAllStores();
  ```

* Om een specifieke persistentielaag te ontruimen, bijvoorbeeld, sessionStorage:

  ```
  var storage = new ContextHub.Utils.Persistence({ mode: ContextHub.Utils.Persistence.Modes.SESSION });
  storage.setItem('/store', null);
  storage.setItem('/_', null);
  
  // to confirm that nothing is stored:
  console.log(storage.getTree());
  ```

* Om alle persistentielagen te ontruimen ContextHub, moet de aangewezen code voor alle lagen worden geroepen:

   * `ContextHub.Utils.Persistence.Modes.LOCAL` (standaardwaarde)
   * `ContextHub.Utils.Persistence.Modes.SESSION`
   * `ContextHub.Utils.Persistence.Modes.COOKIE`
   * `ContextHub.Utils.Persistence.Modes.WINDOW`
