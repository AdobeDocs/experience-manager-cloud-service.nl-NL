---
title: SPA en rendering op de server
description: Het gebruiken van server zijhet teruggeven (SSR) in uw SPA kan de aanvankelijke lading van de pagina versnellen en dan verdere het teruggeven tot de cliënt overgaan.
translation-type: tm+mt
source-git-commit: 056fb27108d8f78acfc4658daa92912a48112f1f
workflow-type: tm+mt
source-wordcount: '1436'
ht-degree: 0%

---


# SPA en rendering op de server{#spa-and-server-side-rendering}

De enige paginatoepassingen (SPAs) kunnen de gebruiker een rijke, dynamische ervaring aanbieden die op vertrouwde manieren reageert en gedraagt, vaak enkel als een inheemse toepassing. [Dit wordt bereikt door op de client te vertrouwen om de inhoud op voorgrond te laden en vervolgens de verwerking van gebruikersinteractie](introduction.md#how-does-a-spa-work) zwaar op te heffen, zodat de benodigde hoeveelheid communicatie tussen de client en de server tot een minimum wordt beperkt, waardoor de app reactiever wordt.

Nochtans kan dit tot langere aanvankelijke ladingstijden leiden, vooral als SPA groot en rijk in zijn inhoud is. Om de laadtijden te optimaliseren, kan een deel van de inhoud op de server worden gerenderd. Met SSR (serverside rendering) kunt u de eerste belasting van de pagina versnellen en vervolgens verdere rendering doorgeven aan de client.

## Wanneer gebruikt u SSR {#when-to-use-ssr}

SSR is niet vereist voor alle projecten. Hoewel AEM volledig JS SSR voor SPA steunt, adviseert Adobe niet het systematisch voor elk project uit te voeren.

Wanneer u besluit SSR te implementeren, moet u eerst inschatten welke extra complexiteit, inspanning en kosten het toevoegen van SSR realistisch vertegenwoordigt voor het project, inclusief het langetermijnonderhoud. Een SSR-architectuur mag alleen worden gekozen wanneer de toegevoegde waarde duidelijk hoger is dan de geraamde kosten.

SSR verstrekt gewoonlijk één of andere waarde wanneer er duidelijk &quot;ja&quot;aan één van beiden van de volgende vragen is:

* **SEO:** Is SSR eigenlijk nog vereist voor uw plaats om behoorlijk door de onderzoeksmotoren worden geïndexeerd die verkeer brengen? Vergeet niet dat de zoekmachine die als hoofdopzoekprogramma wordt gebruikt nu JS evalueert.
* **Paginasnelheid:** Biedt SSR een meetbare snelheidsverbetering in levensechte omgevingen en vergroot de algehele gebruikerservaring?

Slechts wanneer minstens één van deze twee vragen met duidelijk &quot;ja&quot;voor uw project wordt beantwoord adviseert Adobe het uitvoeren van SSR. In de volgende secties wordt beschreven hoe u dit kunt doen met Adobe I/O Runtime.

## Adobe I/O Runtime {#adobe-i-o-runtime}

Als u zeker [bent dat uw project de implementatie van R](#when-to-use-ssr)vereist, is de geadviseerde oplossing van Adobe Adobe I/O Runtime te gebruiken.

Ga voor meer informatie over Adobe I/O Runtime naar

* [https://www.adobe.io/apis/experienceplatform/runtime.html](https://www.adobe.io/apis/experienceplatform/runtime.html) - voor een overzicht van de dienst
* [https://www.adobe.io/apis/experienceplatform/runtime/docs.html](https://www.adobe.io/apis/experienceplatform/runtime/docs.html) - voor gedetailleerde documentatie op het platform

De volgende secties specificeren hoe Adobe I/O Runtime kan worden gebruikt om SSR voor uw KUUROORD in twee verschillende modellen uit te voeren:

* [AEM-gestuurde communicatiestroom](#aem-driven-communication-flow)
* [Adobe I/O Runtime-gestuurde communicatiestroom](#adobe-i-o-runtime-driven-communication-flow)

>[!NOTE]
>
>Adobe raadt een aparte Adobe I/O Runtime-instantie aan voor elke AEM omgeving (auteur, publicatie, werkgebied, enz.).

## Configuratie van externe renderer {#remote-content-renderer-configuration}

AEM moet weten waar de op afstand gerenderde inhoud kan worden opgehaald. Ongeacht [welk model u verkiest om voor SSR uit te voeren,](#adobe-i-o-runtime) zult u aan AEM moeten specificeren hoe te om tot deze verre teruggevende dienst toegang te hebben.

Dit wordt gedaan via de **dienst** RemoteContentRenderer - van de Fabriek OSGi van de Configuratie. Zoek naar het koord &quot;RemoteContentRenderer&quot;in de console van de Configuratie van de Console van het Web bij `http://<host>:<port>/system/console/configMgr`.

![Rendererconfiguratie](assets/renderer-configuration.png)

De volgende velden zijn beschikbaar voor de configuratie:

* **Inhoudspatroon** - Reguliere expressie voor afstemming van een deel van de inhoud, indien nodig
* **Het verre eindpunt URL** - URL van het eindpunt dat voor het produceren van de inhoud verantwoordelijk is
   * Gebruik het beveiligde HTTPS-protocol als dit zich niet in het lokale netwerk bevindt.
* **Extra verzoekkopballen** - de Extra kopballen die aan het verzoek moeten worden toegevoegd dat naar het verre eindpunt wordt verzonden
   * Patroon: `key=value`
* **Time-out** aanvragen - Time-out externe hostaanvraag in milliseconden

>[!NOTE]
>
>Ongeacht of u verkiest om de [AEM-gedreven communicatie stroom](#aem-driven-communication-flow) of de [Adobe I/O Runtime-gedreven stroom uit te voeren,](#adobe-i-o-runtime-driven-communication-flow) moet u een verre configuratie van inhoudrenderer bepalen.

>[!NOTE]
>
>Deze configuratie gebruikt de renderer voor [externe inhoud,](#remote-content-renderer) waarvoor aanvullende opties voor extensie en aanpassing beschikbaar zijn.

## AEM-gestuurde communicatiestroom {#aem-driven-communication-flow}

Wanneer het gebruiken van SSR, omvat het werkschema [van de](introduction.md#interaction-with-the-spa-editor) componenteninteractie van SPAs in AEM een fase waarin de aanvankelijke inhoud van app op Adobe I/O Runtime wordt geproduceerd.

1. De browser vraagt om de SSR-inhoud van AEM.
1. AEM plaatst het model op Adobe I/O Runtime.
1. Adobe I/O Runtime retourneert de gegenereerde inhoud.
1. AEM dient de HTML die door Adobe I/O Runtime wordt geretourneerd via de HTML-sjabloon van de backend page component.

![SSE CMS-gestuurde AEM Adobe I/O](assets/ssr-cms-drivenaemnode-adobeio.png)

## Adobe I/O Runtime-gestuurde communicatiestroom {#adobe-i-o-runtime-driven-communication-flow}

De vorige sectie beschrijft de standaard en geadviseerde implementatie van server zijteruggeven met betrekking tot SPAs in AEM, waar AEM het bootstrapping en het dienen van inhoud uitvoert.

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
     <li>De middelen hoeven alleen op AEM te worden gehandhaafd<br /> </li>
    </ul> </td>
   <td>
    <ul>
     <li>Mogelijk onbekend aan ontwikkelaar van SPA<br /> </li>
    </ul> </td>
  </tr>
  <tr>
   <th><strong>via Adobe I/O Runtime<br /> </strong></th>
   <td>
    <ul>
     <li>Vertrouwelijker aan ontwikkelaars van het KUUROORD<br /> </li>
    </ul> </td>
   <td>
    <ul>
     <li>Clientlib-bronnen die door de toepassing worden vereist, zoals CSS en JavaScript, moeten door de AEM-ontwikkelaar beschikbaar worden gesteld via de <code><a href="/help/implementing/developing/introduction/clientlibs.md">allowProxy</a></code> eigenschap<br /> </li>
     <li>Bronnen moeten worden gesynchroniseerd tussen AEM en Adobe I/O Runtime<br /> </li>
     <li>Om creatie van het KUUROORD toe te laten, kan een volmachtsserver voor Adobe I/O Runtime noodzakelijk zijn</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## Planning voor SSR {#planning-for-ssr}

Over het algemeen hoeft slechts een deel van een toepassing aan serverzijde te worden gerenderd. Het algemene voorbeeld is de inhoud die boven de voud wordt weergegeven wanneer de pagina voor het eerst wordt geladen en op de server wordt weergegeven. Dit bespaart tijd door aan de cliënt, reeds teruggegeven inhoud te leveren. Aangezien de gebruiker met het KUUROORD in wisselwerking staat, wordt de extra inhoud teruggegeven door de cliënt.

Aangezien u overweegt het uitvoeren van server zijhet teruggeven voor uw SPA, moet u controleren voor welke delen van app het noodzakelijk zal zijn.

## Het ontwikkelen van een SPA die SSR gebruikt {#developing-an-spa-using-ssr}

De componenten van het KUUROORD zouden door de cliënt (in browser) of serverkant kunnen worden teruggegeven. Bij rendering op de server zijn browsereigenschappen zoals venstergrootte en -locatie niet aanwezig. Daarom zouden de componenten van het KUUROORD isomorf moeten zijn, die geen veronderstelling maken over waar zij zullen worden teruggegeven.

Als u SSR wilt gebruiken, moet u uw code zowel in AEM als op Adobe I/O Runtime implementeren, die verantwoordelijk is voor de rendering aan de serverzijde. De meeste code zijn hetzelfde, maar serverspecifieke taken verschillen.

## SSR voor SPA’s in AEM {#ssr-for-spas-in-aem}

SSR voor SPAs in AEM vereist Adobe I/O Runtime, die voor de teruggave van de de serverkant van de toepassingsinhoud wordt geroepen. Binnen de HTML van de app wordt een resource op Adobe I/O Runtime aangeroepen om de inhoud te renderen.

Enkel aangezien AEM de Hoekse en Reacte kaders van het KUUROORD uit-van-de doos steunt, wordt het teruggeven van de serverzijde ook gesteund voor Hoekige en Reacte apps. Zie de NPM documentatie voor beide kaders voor verdere details.

## Renderer voor externe inhoud {#remote-content-renderer}

De [Verre Configuratie](#remote-content-renderer-configuration) van Renderer van de Inhoud die wordt vereist om SSR met uw KUUROORD in AEM tikken in een meer algemene het teruggeven dienst te gebruiken die kan worden uitgebreid en worden aangepast om aan uw behoeften te voldoen.

### RemoteContentRenderingService {#remotecontentrenderingservice}

`RemoteContentRenderingService` is de dienst OSGi om inhoud terug te winnen die op een verre server, zoals van Adobe I/O wordt teruggegeven. De inhoud die naar de externe server wordt verzonden, is gebaseerd op de doorgegeven parameter request.

`RemoteContentRenderingService` kan door gebiedsinversie in of een douaneSling model of servlet worden geïnjecteerd wanneer de extra inhoudsmanipulatie wordt vereist.

Deze service wordt intern gebruikt door de [RemoteContentRendererRequestHandlerServlet](#remotecontentrendererrequesthandlerservlet).

### RemoteContentRendererRequestHandlerServlet {#remotecontentrendererrequesthandlerservlet}

Het `RemoteContentRendererRequestHandlerServlet` kan worden gebruikt om de verzoekconfiguratie programmatically te plaatsen. `DefaultRemoteContentRendererRequestHandlerImpl`, staat de verstrekte implementatie van de standaardverzoekmanager, u toe om veelvoudige configuraties tot stand te brengen OSGi om een plaats in de inhoudsstructuur aan een ver eindpunt in kaart te brengen.

Om een manager van het douaneverzoek toe te voegen, voer de `RemoteContentRendererRequestHandler` interface uit. Ben zeker om het `Constants.SERVICE_RANKING` componentenbezit aan een geheel te plaatsen hoger dan 100, dat de rangschikking van `DefaultRemoteContentRendererRequestHandlerImpl`is.

```javascript
@Component(immediate = true,
        service = RemoteContentRendererRequestHandler.class,
        property={
            Constants.SERVICE_RANKING +":Integer=1000"
        })
public class CustomRemoteContentRendererRequestHandlerImpl implements RemoteContentRendererRequestHandler {}
```

### Vorm de Configuratie OSGi van de Standaardmanager {#configure-default-handler}

De configuratie van de standaardmanager moet worden gevormd zoals die in de sectie [Verre Configuratie](#remote-content-renderer-configuration)van Renderer van Inhoud wordt beschreven.

### Renderergebruik van externe inhoud {#usage}

Om een servlet te hebben halen en wat inhoud terug te keren die in de pagina kan worden ingespoten:

1. Controleer of uw externe server toegankelijk is.
1. Voeg een van de volgende fragmenten toe aan de HTML-sjabloon van een AEM component.
1. Naar keuze, creeer of wijzig de configuraties OSGi.
1. Door de inhoud van uw site bladeren

Gewoonlijk is de HTML-sjabloon van een paginacomponent de belangrijkste ontvanger van een dergelijke functie.

```html
<sly data-sly-resource="${resource @ resourceType='cq/remote/content/renderer/request/handler'}" />
```

### Vereisten {#requirements}

De servers maken gebruik van de Sling Model Exporter om de componentgegevens te serialiseren. Standaard worden zowel de `com.adobe.cq.export.json.ContainerExporter` `com.adobe.cq.export.json.ComponentExporter` als de Sling Model-adapters ondersteund. Indien nodig, kunt u klassen toevoegen die het verzoek zou moeten worden aangepast aan het gebruiken van `RemoteContentRendererServlet` en het uitvoeren van `RemoteContentRendererRequestHandler#getSlingModelAdapterClasses`. De extra klassen moeten het `ComponentExporter`uitbreiden.
