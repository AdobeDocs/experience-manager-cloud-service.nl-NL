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

Toepassingen op één pagina (SPA) kunnen de gebruiker een rijke, dynamische ervaring bieden die op vertrouwde manieren reageert en zich gedraagt, vaak net als een native toepassing. [ Deze functionaliteit wordt bereikt door op de cliënt te vertrouwen om de inhoud te laden vooraan en dan het zware heffen van de behandeling van gebruikersinteractie ](introduction.md#how-does-a-spa-work) te doen. Dit proces minimaliseert de hoeveelheid communicatie die nodig is tussen de client en de server, waardoor de app reactiever wordt.

Dit proces kan echter leiden tot langere openingstijden, vooral als de SPA groot en rijk is aan inhoud. Om de laadtijden te optimaliseren, kan een deel van de inhoud op de server worden weergegeven. Met SSR (Server-Side Rendering) kunt u de eerste belasting van de pagina versnellen en vervolgens verdere rendering doorgeven aan de client.

## Wanneer gebruikt u SSR {#when-to-use-ssr}

SSR is niet vereist voor alle projecten. Hoewel AEM volledig JS SSR voor SPA steunt, beveelt de Adobe niet aan het systematisch voor elk project uit te voeren.

Wanneer u besluit SSR te implementeren, moet u eerst inschatten welke extra complexiteit, inspanning en kosten het toevoegen van SSR realistisch vertegenwoordigt voor het project, inclusief het langetermijnonderhoud. Een SSR-architectuur mag alleen worden gekozen wanneer de toegevoegde waarde duidelijk hoger is dan de geraamde kosten.

SSR verstrekt gewoonlijk één of andere waarde wanneer er duidelijk &quot;ja&quot;aan één van beiden van de volgende vragen is:

* **SEO:** Is SSR nog vereist voor uw plaats behoorlijk door de onderzoeksmotoren worden geïndexeerd die verkeer brengen? Vergeet niet dat de zoekmachine die als hoofdopzoekprogramma wordt gebruikt nu JS evalueert.
* **de Snelheid van de Pagina:** verstrekt SSR een meetbare snelheidsverbetering in milieu&#39;s in real-life en voegt aan de algemene gebruikerservaring toe?

Slechts wanneer minstens één van deze twee vragen met duidelijk &quot;ja&quot;voor uw project wordt beantwoord adviseert de Adobe het uitvoeren van SSR. De volgende secties beschrijven hoe te om dit te doen gebruikend Adobe I/O Runtime, een deel van [ App Builder ](https://developer.adobe.com/app-builder).

## Adobe I/O Runtime {#adobe-i-o-runtime}

Als u [ zeker bent dat uw project de implementatie van SSR ](#when-to-use-ssr) vereist, is de geadviseerde oplossing van de Adobe Adobe I/O Runtime te gebruiken.

Raadpleeg de volgende secties voor meer informatie over Adobe I/O Runtime:

* [ https://developer.adobe.com/runtime ](https://developer.adobe.com/runtime) - voor een overzicht van de Runtime eigenschap van App Builder
* [ https://developer.adobe.com/app-builder ](https://developer.adobe.com/app-builder) - voor details over het volledige product van App Builder
* [ https://developer.adobe.com/runtime/docs/ ](https://developer.adobe.com/runtime/docs) - voor gedetailleerde documentatie

In de volgende secties wordt beschreven hoe Adobe I/O Runtime kan worden gebruikt om SSR voor uw SPA in twee verschillende modellen te implementeren:

* [AEM-gestuurde communicatiestroom](#aem-driven-communication-flow)
* [Adobe I/O Runtime-gestuurde communicatiestroom](#adobe-i-o-runtime-driven-communication-flow)

>[!NOTE]
>
>Adobe raadt een aparte Adobe I/O Runtime-werkruimte aan per omgeving (werkgebied, proefperiode, testen, enzovoort). Dit maakt het mogelijk om standaard SDLC-patronen (Systems Development Life Cycle) te gebruiken met verschillende versies van één toepassing die op verschillende omgevingen worden geïmplementeerd. Zie [ CI/CD voor de Toepassingen van App Builder ](https://developer.adobe.com/app-builder/docs/guides/deployment/ci_cd_for_firefly_apps/) voor meer informatie.
>
>Er is geen aparte werkruimte nodig per instantie (auteur, publiceren), tenzij er verschillen zijn in de runtimplementatie per instantietype.

>[!NOTE]
>
>Cloud Manager biedt geen ondersteuning voor implementatie op Adobe I/O Runtime. Als gevolg hiervan moet uw eigen infrastructuur zo zijn ingesteld dat SSR-code op de Adobe I/O Runtime kan worden geïmplementeerd.

## Configuratie van externe renderer {#remote-content-renderer-configuration}

AEM moet weten waar de extern gerenderde inhoud kan worden opgehaald. Ongeacht [ welk model u verkiest om voor SSR uit te voeren, ](#adobe-i-o-runtime) u moet specificeren om tot deze verre het teruggeven dienst AEM toegang te hebben.

Deze dienst wordt gedaan als **RemoteContentRenderer - de dienst van OSGi van de Fabriek van de Configuratie OSGi**. Zoek naar het koord &quot;RemoteContentRenderer&quot;in de console van de Configuratie van de Console van het Web bij `http://<host>:<port>/system/console/configMgr`.

![ Configuratie van Renderer ](assets/renderer-configuration.png)

De volgende velden zijn beschikbaar voor de configuratie:

* **het wegpatroon van de Inhoud** - Regelmatige uitdrukking om een gedeelte van de inhoud aan te passen, indien nodig
* **Verre eindpunt URL** - URL van het eindpunt dat voor het produceren van de inhoud verantwoordelijk is
   * Gebruik het beveiligde HTTPS-protocol als dit zich niet in het lokale netwerk bevindt.
* **Extra verzoekkopballen** - de Extra kopballen die aan het verzoek moeten worden toegevoegd dat naar het verre eindpunt wordt verzonden
   * Patroon: `key=value`
* **onderbreking van het Verzoek** - Verre onderbreking van het gastheerverzoek in milliseconden

>[!NOTE]
>
>Ongeacht als u verkiest om de [ AEM-gedreven communicatie stroom ](#aem-driven-communication-flow) of de [ Adobe I/O Runtime-gedreven stroom uit te voeren, ](#adobe-i-o-runtime-driven-communication-flow) u moet een verre configuratie van inhoudrenderer bepalen.

>[!NOTE]
>
>Deze configuratie gebruikt [ Verre Renderer van de Inhoud, ](#remote-content-renderer) die extra uitbreiding en aanpassingsopties beschikbaar heeft.

## AEM-gestuurde communicatiestroom {#aem-driven-communication-flow}

Wanneer het gebruiken van SSR, omvat het [ werkschema van de componenteninteractie ](introduction.md#interaction-with-the-spa-editor) van SPA in AEM een fase waarin de aanvankelijke inhoud van app op Adobe I/O Runtime wordt geproduceerd.

1. De browser vraagt om de SSR-inhoud van AEM.
1. AEM plaatst het model op Adobe I/O Runtime.
1. Adobe I/O Runtime retourneert de gegenereerde inhoud.
1. AEM dient de HTML die door Adobe I/O Runtime wordt geretourneerd via de HTML-sjabloon van de achtergrondpagina-component.

![ SSE CMS-gedreven AEM Adobe I/O ](assets/ssr-cms-drivenaemnode-adobeio.png)

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
   <th><strong> via AEM </strong><br /> </th>
   <td>
    <ul>
     <li>AEM beheert waar nodig injectiebibliotheken</li>
     <li>Bronnen alleen op AEM behouden <br /> </li>
    </ul> </td>
   <td>
    <ul>
     <li>Mogelijk niet bekend met SPA ontwikkelaar <br /> </li>
    </ul> </td>
  </tr>
  <tr>
   <th><strong>via Adobe I/O Runtime<br /> </strong></th>
   <td>
    <ul>
     <li>Bewegend aan SPA ontwikkelaars <br /> </li>
    </ul> </td>
   <td>
    <ul>
     <li>Clientlib-bronnen die door de toepassing worden vereist, zoals CSS en JavaScript, moeten door de AEM ontwikkelaar beschikbaar worden gesteld via de eigenschap <code><a href="/help/implementing/developing/introduction/clientlibs.md">allowProxy</a></code> <br /> . </li>
     <li>De middelen moeten tussen AEM en Adobe I/O Runtime <br /> worden gesynchroniseerd </li>
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

De [ Verre Configuratie van Renderer van de Inhoud ](#remote-content-renderer-configuration) die wordt vereist om SSR met uw SPA in AEM tikken in een meer algemene het teruggeven dienst te gebruiken die kan worden uitgebreid en worden aangepast om aan uw behoeften te voldoen.

### RemoteContentRenderingService {#remotecontentrenderingservice}

`RemoteContentRenderingService` De dienst OSGi om inhoud terug te winnen die op een verre server, zoals van Adobe I/O wordt teruggegeven. De inhoud die naar de externe server wordt verzonden, is gebaseerd op de doorgegeven parameter request.

`RemoteContentRenderingService` Kan worden geïnjecteerd door inversie van afhankelijkheid in een aangepast Sling-model of servlet wanneer aanvullende bewerking van de inhoud vereist is.

Deze dienst wordt intern gebruikt door [ RemoteContentRendererRequestHandlerServlet ](#remotecontentrendererrequesthandlerservlet).

### RemoteContentRendererRequestHandlerServlet {#remotecontentrendererrequesthandlerservlet}

`RemoteContentRendererRequestHandlerServlet` wordt gebruikt om de verzoekconfiguratie programmatically te plaatsen. `DefaultRemoteContentRendererRequestHandlerImpl`, laat de verstrekte implementatie van de standaardverzoekmanager, u veelvoudige configuraties tot stand brengen OSGi zodat kunt u een plaats in de inhoudsstructuur aan een ver eindpunt in kaart brengen.

Implementeer de interface `RemoteContentRendererRequestHandler` om een aangepaste aanvraaghandler toe te voegen. U moet de componenteigenschap `Constants.SERVICE_RANKING` instellen op een geheel getal dat groter is dan 100. Dit is de positie van de `DefaultRemoteContentRendererRequestHandlerImpl` .

```javascript
@Component(immediate = true,
        service = RemoteContentRendererRequestHandler.class,
        property={
            Constants.SERVICE_RANKING +":Integer=1000"
        })
public class CustomRemoteContentRendererRequestHandlerImpl implements RemoteContentRendererRequestHandler {}
```

### Vorm de Configuratie OSGi van de Standaardmanager {#configure-default-handler}

De configuratie van de standaardmanager moet worden gevormd zoals die in de sectie [ Verre Configuratie van de Renderer van de Inhoud ](#remote-content-renderer-configuration) wordt beschreven.

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

De servlets gebruiken de Verschuivende ModelExporter om de componentengegevens in series te vervaardigen. Standaard worden zowel `com.adobe.cq.export.json.ContainerExporter` als `com.adobe.cq.export.json.ComponentExporter` ondersteund als Sling Model-adapters. Indien nodig, kunt u klassen toevoegen die de aanvraag moet worden aangepast aan het gebruik van `RemoteContentRendererServlet` en het implementeren van `RemoteContentRendererRequestHandler#getSlingModelAdapterClasses` . De extra klassen moeten `ComponentExporter` uitbreiden.
