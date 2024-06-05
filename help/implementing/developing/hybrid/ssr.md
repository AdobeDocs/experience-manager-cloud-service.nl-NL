---
title: SPA en rendering op de server
description: Door SSR (Server-Side Rendering) in uw SPA te gebruiken, kunt u de eerste laadbewerking van de pagina versnellen en vervolgens verdere rendering aan de client doorgeven.
exl-id: be409559-c7ce-4bc2-87cf-77132d7c2da1
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '1492'
ht-degree: 0%

---

# SPA en rendering op de server{#spa-and-server-side-rendering}

Toepassingen op één pagina (SPA) kunnen de gebruiker een rijke, dynamische ervaring bieden die op vertrouwde manieren reageert en zich gedraagt, vaak net als een native toepassing. [Deze functionaliteit wordt bereikt door op de client te vertrouwen om de inhoud vóór te laden en vervolgens de interactie van de gebruiker zwaar op te heffen](introduction.md#how-does-a-spa-work). Dit proces minimaliseert de hoeveelheid communicatie die nodig is tussen de client en de server, waardoor de app reactiever wordt.

Dit proces kan echter leiden tot langere openingstijden, vooral als de SPA groot en rijk is aan inhoud. Om de laadtijden te optimaliseren, kan een deel van de inhoud op de server worden weergegeven. Met SSR (Server-Side Rendering) kunt u de eerste belasting van de pagina versnellen en vervolgens verdere rendering doorgeven aan de client.

## Wanneer gebruikt u SSR {#when-to-use-ssr}

SSR is niet vereist voor alle projecten. Hoewel AEM volledig JS SSR voor SPA steunt, beveelt de Adobe niet aan het systematisch voor elk project uit te voeren.

Wanneer u besluit SSR te implementeren, moet u eerst inschatten welke extra complexiteit, inspanning en kosten het toevoegen van SSR realistisch vertegenwoordigt voor het project, inclusief het langetermijnonderhoud. Een SSR-architectuur mag alleen worden gekozen wanneer de toegevoegde waarde duidelijk hoger is dan de geraamde kosten.

SSR verstrekt gewoonlijk één of andere waarde wanneer er duidelijk &quot;ja&quot;aan één van beiden van de volgende vragen is:

* **SEO:** Is SSR nog vereist voor uw plaats om behoorlijk door de onderzoeksmotoren worden geïndexeerd die verkeer brengen? Vergeet niet dat de zoekmachine die als hoofdopzoekprogramma wordt gebruikt nu JS evalueert.
* **Paginasnelheid:** Biedt SSR een meetbare snelheidsverbetering in levensechte omgevingen en vergroot de algehele gebruikerservaring?

Slechts wanneer minstens één van deze twee vragen met duidelijk &quot;ja&quot;voor uw project wordt beantwoord adviseert de Adobe het uitvoeren van SSR. In de volgende secties wordt beschreven hoe u dit kunt doen met Adobe I/O Runtime, onderdeel van [App Builder](https://developer.adobe.com/app-builder).

## Adobe I/O Runtime {#adobe-i-o-runtime}

Als u [vertrouwen erop dat uw project de implementatie van SSR vereist](#when-to-use-ssr)De aanbevolen oplossing van Adobe is het gebruik van Adobe I/O Runtime.

Raadpleeg de volgende secties voor meer informatie over Adobe I/O Runtime:

* [https://developer.adobe.com/runtime](https://developer.adobe.com/runtime) - voor een overzicht van de Runtime eigenschap van App Builder
* [https://developer.adobe.com/app-builder](https://developer.adobe.com/app-builder) - voor meer informatie over het volledige App Builder-product
* [https://developer.adobe.com/runtime/docs/](https://developer.adobe.com/runtime/docs) - voor gedetailleerde documentatie

In de volgende secties wordt beschreven hoe Adobe I/O Runtime kan worden gebruikt om SSR voor uw SPA in twee verschillende modellen te implementeren:

* [AEM-gestuurde communicatiestroom](#aem-driven-communication-flow)
* [Adobe I/O Runtime-gestuurde communicatiestroom](#adobe-i-o-runtime-driven-communication-flow)

>[!NOTE]
>
>Adobe raadt een aparte Adobe I/O Runtime-werkruimte aan per omgeving (werkgebied, proefperiode, testen, enzovoort). Dit maakt het mogelijk om standaard SDLC-patronen (Systems Development Life Cycle) te gebruiken met verschillende versies van één toepassing die op verschillende omgevingen worden geïmplementeerd. Zie [CI/CD voor App Builder-toepassingen](https://developer.adobe.com/app-builder/docs/guides/deployment/ci_cd_for_firefly_apps/) voor meer informatie .
>
>Er is geen aparte werkruimte nodig per instantie (auteur, publiceren), tenzij er verschillen zijn in de runtimplementatie per instantietype.

>[!NOTE]
>
>Cloud Manager ondersteunt geen implementatie op Adobe I/O Runtime. Als gevolg hiervan moet uw eigen infrastructuur zo zijn ingesteld dat SSR-code op de Adobe I/O Runtime kan worden geïmplementeerd.

## Configuratie van externe renderer {#remote-content-renderer-configuration}

AEM moet weten waar de extern gerenderde inhoud kan worden opgehaald. Ongeacht [welk model u verkiest om voor SSR uit te voeren,](#adobe-i-o-runtime) u moet opgeven hoe u toegang kunt krijgen tot deze externe renderingsservice.

Deze service wordt uitgevoerd via de **RemoteContentRenderer - Configuratie in fabriek OSGi-service**. Zoek naar het koord &quot;RemoteContentRenderer&quot;in de console van de Configuratie van de Console van het Web bij `http://<host>:<port>/system/console/configMgr`.

![Rendererconfiguratie](assets/renderer-configuration.png)

De volgende velden zijn beschikbaar voor de configuratie:

* **Inhoudspatroon** - Reguliere expressie die zo nodig overeenkomt met een deel van de inhoud
* **URL van extern eindpunt** - URL van het eindpunt dat verantwoordelijk is voor het genereren van de inhoud
   * Gebruik het beveiligde HTTPS-protocol als dit zich niet in het lokale netwerk bevindt.
* **Aanvullende aanvraagheaders** - Extra kopballen die aan het verzoek moeten worden toegevoegd dat naar het verre eindpunt wordt verzonden
   * Patroon: `key=value`
* **Verzoek om time-out** - Time-out externe hostaanvraag in milliseconden

>[!NOTE]
>
>Ongeacht of u ervoor kiest om het [AEM-gestuurde communicatiestroom](#aem-driven-communication-flow) of de [door Adobe I/O Runtime aangedreven stroom,](#adobe-i-o-runtime-driven-communication-flow) u moet een configuratie van een externe inhoudrenderer definiëren.

>[!NOTE]
>
>Deze configuratie gebruikt de [Renderer voor externe inhoud,](#remote-content-renderer) waarvoor aanvullende opties voor extensie en aanpassing beschikbaar zijn.

## AEM-gestuurde communicatiestroom {#aem-driven-communication-flow}

Als u SSR gebruikt, wordt [interactieworkflow voor componenten](introduction.md#interaction-with-the-spa-editor) SPA in AEM omvat een fase waarin de initiële inhoud van de app op Adobe I/O Runtime wordt gegenereerd.

1. De browser vraagt om de SSR-inhoud van AEM.
1. AEM plaatst het model op Adobe I/O Runtime.
1. Adobe I/O Runtime retourneert de gegenereerde inhoud.
1. AEM dient de HTML die door Adobe I/O Runtime wordt geretourneerd via de HTML-sjabloon van de achtergrondpagina-component.

![SSE CMS-gestuurde AEM Adobe I/O](assets/ssr-cms-drivenaemnode-adobeio.png)

## Adobe I/O Runtime-gestuurde communicatiestroom {#adobe-i-o-runtime-driven-communication-flow}

In de vorige sectie worden de standaard en aanbevolen implementatie beschreven van rendering op de server met betrekking tot SPA in AEM, waarbij AEM de overvulling en het serveren van inhoud uitvoert.

Alternatief, kan SSR worden uitgevoerd zodat Adobe I/O Runtime voor bootstrapping verantwoordelijk is, effectief omkeerend de communicatie stroom.

Beide modellen zijn geldig en worden ondersteund door AEM. Men moet echter eerst de voor- en nadelen van elk model in overweging nemen voordat men een bepaald model toepast.

<table>
 <tbody>
  <tr>
   <th><strong>Bootstrapping</strong></th>
   <th><strong>Voordelen</strong></th>
   <th><strong>Nadelen</strong></th>
  </tr>
  <tr>
   <th><strong>via AEM</strong><br /> </th>
   <td>
    <ul>
     <li>AEM beheert waar nodig injectiebibliotheken</li>
     <li>Bronnen alleen behouden op AEM<br /> </li>
    </ul> </td>
   <td>
    <ul>
     <li>Mogelijk niet bekend bij SPA ontwikkelaar<br /> </li>
    </ul> </td>
  </tr>
  <tr>
   <th><strong>via Adobe I/O Runtime<br /> </strong></th>
   <td>
    <ul>
     <li>SPA ontwikkelaars meer bekend<br /> </li>
    </ul> </td>
   <td>
    <ul>
     <li>Clientlib-bronnen die door de toepassing worden vereist, zoals CSS en JavaScript, moeten door de AEM ontwikkelaar beschikbaar worden gesteld via de <code><a href="/help/implementing/developing/introduction/clientlibs.md">allowProxy</a></code> eigenschap<br /> </li>
     <li>Bronnen moeten worden gesynchroniseerd tussen AEM en Adobe I/O Runtime<br /> </li>
     <li>Om het ontwerpen van de SPA mogelijk te maken, is mogelijk een proxyserver voor Adobe I/O Runtime nodig</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## Planning voor SSR {#planning-for-ssr}

Over het algemeen moet slechts een deel van een toepassing op de server worden weergegeven. Het algemene voorbeeld is de inhoud die boven de voud wordt weergegeven bij de eerste keer dat de pagina wordt geladen, wordt weergegeven op de server. Dit proces bespaart tijd door aan de cliënt, reeds teruggegeven inhoud te leveren. Terwijl de gebruiker met de SPA communiceert, wordt de extra inhoud door de client gerenderd.

Wanneer u rendering op de server wilt implementeren voor uw SPA, moet u controleren welke delen van de app u nodig hebt.

## Een SPA ontwikkelen met behulp van SSR {#developing-an-spa-using-ssr}

SPA componenten kunnen door de client (in de browser) of de server worden gerenderd. Bij rendering op de server zijn browsereigenschappen zoals venstergrootte en -locatie niet aanwezig. Daarom moeten SPA componenten isomorf zijn, waarbij er geen aanname is over waar ze worden gerenderd.

Als u SSR wilt gebruiken, moet u de code in AEM en op Adobe I/O Runtime implementeren, die verantwoordelijk is voor de rendering op de server. De meeste code zijn hetzelfde, maar serverspecifieke taken verschillen.

## SSR voor SPA in AEM {#ssr-for-spas-in-aem}

SSR voor SPA in AEM vereist Adobe I/O Runtime, dat wordt opgeroepen voor het renderen van de zijde van de toepassingsinhoudsserver. Binnen de HTML van de app wordt een resource op Adobe I/O Runtime aangeroepen om de inhoud te renderen.

Net zoals AEM de Angular- en Reactie-SPA-frameworks buiten de box ondersteunt, wordt rendering op de server ook ondersteund voor Angular- en Reactie-apps. Zie de NPM documentatie voor beide kaders voor verdere details.

## Renderer voor externe inhoud {#remote-content-renderer}

De [Configuratie renderfunctie voor externe inhoud](#remote-content-renderer-configuration) die vereist is om SSR met uw SPA te gebruiken in AEM tikken op een meer algemene renderservice die kan worden uitgebreid en aangepast aan uw behoeften.

### RemoteContentRenderingService {#remotecontentrenderingservice}

`RemoteContentRenderingService` Een dienst OSGi om inhoud terug te winnen die op een verre server, zoals van Adobe I/O wordt teruggegeven. De inhoud die naar de externe server wordt verzonden, is gebaseerd op de doorgegeven parameter request.

`RemoteContentRenderingService` Kan worden geïnjecteerd door inversie van afhankelijkheid in een aangepast Sling-model of servlet wanneer extra inhoudsmanipulatie vereist is.

Deze dienst wordt intern gebruikt door [RemoteContentRendererRequestHandlerServlet](#remotecontentrendererrequesthandlerservlet).

### RemoteContentRendererRequestHandlerServlet {#remotecontentrendererrequesthandlerservlet}

De `RemoteContentRendererRequestHandlerServlet` wordt gebruikt om programmatically de verzoekconfiguratie te plaatsen. `DefaultRemoteContentRendererRequestHandlerImpl`, laat de verstrekte implementatie van de standaardverzoekmanager, u veelvoudige configuraties tot stand brengen OSGi zodat kunt u een plaats in de inhoudsstructuur aan een ver eindpunt in kaart brengen.

Om een manager van het douaneverzoek toe te voegen, voer uit `RemoteContentRendererRequestHandler` interface. Zorg ervoor dat u de `Constants.SERVICE_RANKING` componenteigenschap instellen op een geheel getal hoger dan 100. Dit is de positie van de component `DefaultRemoteContentRendererRequestHandlerImpl`.

```javascript
@Component(immediate = true,
        service = RemoteContentRendererRequestHandler.class,
        property={
            Constants.SERVICE_RANKING +":Integer=1000"
        })
public class CustomRemoteContentRendererRequestHandlerImpl implements RemoteContentRendererRequestHandler {}
```

### Vorm de Configuratie OSGi van de Standaardmanager {#configure-default-handler}

De configuratie van de standaardmanager moet worden gevormd zoals die in de sectie wordt beschreven [Configuratie renderfunctie voor externe inhoud](#remote-content-renderer-configuration).

### Renderergebruik van externe inhoud {#usage}

Een servlet ophalen en sommige inhoud retourneren die in de pagina is geïnjecteerd:

1. Zorg ervoor dat uw externe server toegankelijk is.
1. Voeg een van de volgende fragmenten toe aan de HTML-sjabloon van een AEM component.
1. Naar keuze, creeer of wijzig de configuraties OSGi.
1. Door de inhoud van uw site bladeren

Gewoonlijk is de HTML-sjabloon van een paginacomponent de belangrijkste ontvanger van een dergelijke functie.

```html
<sly data-sly-resource="${resource @ resourceType='cq/remote/content/renderer/request/handler'}" />
```

### Vereisten {#requirements}

De servlets gebruiken de Verschuivende ModelExporter om de componentengegevens in series te vervaardigen. Standaard worden beide `com.adobe.cq.export.json.ContainerExporter` en `com.adobe.cq.export.json.ComponentExporter` worden ondersteund als Sling Model-adapters. Indien nodig kunt u klassen toevoegen waaraan de aanvraag moet worden aangepast om de opdracht `RemoteContentRendererServlet` en de uitvoering van de `RemoteContentRendererRequestHandler#getSlingModelAdapterClasses`. De extra klassen moeten de `ComponentExporter`.
