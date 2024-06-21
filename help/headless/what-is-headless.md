---
title: Wat is een headless CMS?
description: Meer informatie over Headless CMS. Hoe werken ze? Wat zijn de alternatieven en verschillen? Waarom zou u een Headless CMS willen gebruiken?
exl-id: 53f24f69-ad49-4b8e-9a91-36cd64c1f2b9
feature: Headless
role: Admin, Developer
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '742'
ht-degree: 0%

---

# Wat is een headless CMS? {#what-is-a-headless-cms}

Beheer van inhoud zonder hoofd is een belangrijke ontwikkeling voor het huidige webontwerp, dat de geavanceerde clienttoepassingen loskoppelt van het back-end contentbeheersysteem. Een CMS zonder kop is daarom verantwoordelijk voor de (back-end) contentbeheerdiensten, samen met de mechanismen waarmee de (frontend) toepassingen toegang kunnen krijgen tot die inhoud.

Maar wat betekent de term eigenlijk? Hier geven we een (zeer snelle) inleiding aan de belangrijkste concepten.

## Wat is een inhoudsbeheersysteem (CMS)? {#content-management-system}

Laten we beginnen met de basisbeginselen - wat is een inhoudsbeheersysteem?

In een contentbeheersysteem (CMS) wordt de inhoud die wordt gebruikt voor uw online ervaringen opgeslagen, beheerd en geleverd.

## Traditioneel CMS {#traditional-cms}

Een CMS heeft traditioneel zowel de achtergrondfunctionaliteit voor opslag en levering van inhoud als de frontendtechnologie opgenomen die wordt gebruikt om de markering weer te geven voor een ervaring die uw browser zal weergeven (de presentatielaag).

Zeer krachtig, zodat u de volledige controle hebt over de inhoud en opmaak, maar niet beschikt over de flexibiliteit die nodig is in de snel bewegende omgeving van vandaag, bijvoorbeeld bij de interface met externe apps.

## CMS zonder hoofd {#headless-cms}

Met een systeem voor inhoudsbeheer zonder kop zijn back-end en front-end nu ontkoppeld.

Het onderdeel zonder kop is de achterkant van de inhoud, omdat een CMS (headless Content Management System) een back-end alleen inhoudsbeheersysteem is dat expliciet is ontworpen en gebouwd als een opslagplaats voor inhoud die inhoud toegankelijk maakt via een API, voor weergave op elk apparaat.

De front-end, die onafhankelijk van elkaar wordt ontwikkeld en onderhouden, haalt inhoud van de headless backend op met behulp van een Content Delivery API, typisch in formaat JSON. Dit kan bijvoorbeeld een React- of een Angular-toepassing (toepassing voor één pagina (SPA)) zijn.

Voor een CMS-achtergrond zonder kop is meestal de structuur van de inhoud vereist op basis van een model of schema. Hierdoor kunnen clienttoepassingen de juiste inhoud aanvragen voor het renderen van een ervaring. Sommige CMS kunnen zowel gestructureerde als ongestructureerde inhoud in JSON-indeling beschikbaar maken.

Een zeer belangrijk kenmerk van deze topologie is dat de inhoud die door het hoofd CMS in formaat JSON wordt gediend zuivere inhoud, zonder ontwerp of lay-outinformatie is. In een CMS-implementatie zonder kop blijft alle opmaak en lay-out behouden door de ontkoppelde frontendtoepassing.

Een zeer belangrijk voordeel van een koploze topologie CMS is de capaciteit om inhoud over veelvoudige kanalen opnieuw te gebruiken, die verschillende cliënt-zij frontend implementaties kunnen gebruiken. Dit kan het vooruitstrevende ontwikkelingsproces efficiënter maken. Maar het betekent ook dat het ontwikkelingsproces van de frontendervaring zeer code en IT-centric kan worden, waarbij IT in wezen de ervaring bezit.

## API&#39;s voor levering van inhoud {#content-delivery-apis}

Een CMS zonder kop kan een of meerdere manieren bieden om inhoud toegankelijk te maken voor clienttoepassingen. Meestal HTTP REST API&#39;s, GraphQL API&#39;s of beide.

Hoewel een REST API vaak een eenvoudigere manier lijkt om inhoud aan te vragen (bijvoorbeeld door JSON te bieden voor alle inhoud die aan een criterium voldoet), leveren deze doorgaans te veel inhoud aan een clienttoepassing. Dit kan ertoe leiden dat de client de inhoud moet parseren en uitfilteren die werkelijk nodig is voor rendering.

GraphQL daarentegen is een meer gericht mechanisme waarmee clienttoepassingen kunnen zoeken naar exact de inhoud die nodig is om een ervaring te renderen.

## CMS volledig stapelen {#fullstack-cms}

Een full-Stack CMS vertegenwoordigt algemeen de traditionele topologie voor inhoudsbeheer en levering, door de inhoud te omvatten achterste en vooruitstrevende technologie voor het teruggeven van ervaringen. Inhoud wordt meestal geleverd in CMS met volledige stack via API&#39;s voor interne inhoudslevering. De frontend functionaliteit is typisch specifiek voor volledige stapel CMS. Deze koppeling van frontend-technologie met content backend maakt het mogelijk om WYSIWYG-ervaring (what-you-see-is-what-you-get) te gebruiken als een belangrijk voordeel.

## Hybride CMS {#hybrid-cms}

Een moderne evolutie van de full-stack CMS kan een hybride CMS zijn. Dit is bedoeld om de beste van beide werelden te combineren:

* efficiënte frontendontwikkeling tussen kanalen met behulp van moderne frontend-instrumenten;
* terwijl het behouden van WYSIWYG ervaring ontwerper om niet-technische gebruikers te machtigen, en IT te vermijden die een knelpunt voor dwars-organisatorische inhoud en ervaringsbeheer wordt.

Dit wordt bereikt door moderne frontend-frameworks, zoals React, te gebruiken, maar met behoud van een essentieel minimum aan koppeling met de contentachtergrond.

## Ontkoppelde CMS {#decoupled-cms}

Hoewel de term ontkoppelde CMS soms onafhankelijk wordt gebruikt, beschrijft het in wezen een koploze CMS-backend door de nadruk te leggen op zijn belangrijkste kenmerk van ontkoppelde CMS-toepassing aan de clientzijde.

## Hoofdzakelijk CMS {#headful-cms}

Dit is een andere term voor een traditioneel CMS.

## Verdere lezing {#further-reading}

U kunt meer over het gebruiken van AEM in een headless topologie CMS hier lezen:

* [Inleiding tot Adobe Experience Manager als een headless CMS](/help/headless/introduction.md)
