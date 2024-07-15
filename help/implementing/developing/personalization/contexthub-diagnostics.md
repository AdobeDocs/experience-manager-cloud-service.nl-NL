---
title: ContextHub Diagnostics
description: ContextHub verstrekt een diagnostische pagina waar u een overzicht van het kader ContextHub kunt zien
exl-id: c8d4e160-ea02-49f3-9e31-119445ef5a68
feature: Developing, Personalization
role: Admin, Architect, Developer
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# ContextHub Diagnostics {#contexthub-diagnostics}

ContextHub verstrekt een diagnostische pagina waar u een overzicht van het kader kunt zien ContextHub. Als u de pagina wilt openen, gaat u bijvoorbeeld naar de pagina `contexthub.diagnostics.html` van de AEM auteur-instantie:

`http://<host>:<port>/conf/<site>/settings/cloudsettings/default/contexthub.diagnostics.html`

De pagina van de Diagnostiek ContextHub verstrekt informatie over de opslag en modules UI die zijn gecreeerd, de omslagen van de cliëntbibliotheek die, en verbindingen aan nuttige pagina&#39;s worden geladen.

>[!NOTE]
>
>Om diagnostische informatie terug te geven moet de foutopsporingsmodus zijn ingeschakeld, anders is de diagnostische pagina leeg. Zie [ dit document ](configuring-contexthub.md#debugging-contexthub) voor details op hoe te om toe te laten zuiveren wijze.

## Winkels {#stores}

De sectie van Sporen maakt een lijst van alle opslag ContextHub die zijn gevormd. Elk item in de lijst bestaat uit de volgende informatie:

* **Titel:** het [ opslagtype ](sample-stores.md) dat de opslag op gebaseerd is.
* **weg:** de weg aan de opslagplaats knoop die de configuratie houdt.
* **resourceType:** de weg van de bewaargegevensknoop waar het opslagtype wordt bepaald.
* **clientlibs:** De categorieën van de cliëntbibliotheken die worden geladen die het archieftype uitvoeren.

## Modules {#modules}

De sectie van Modules maakt een lijst van alle modules ContextHub UI die zijn gevormd. Elk item in de lijst bestaat uit de volgende informatie:

* **Titel:** het [ type van Module UI ](sample-modules.md) dat de module UI gebaseerd is op.
* **weg:** de weg aan de opslagplaats knoop die de configuratie houdt.
* **resourceType:** de weg van de opslagplaats knoop waar het UI moduletype wordt bepaald.
* **clientlibs:** De categorieën van de cliëntbibliotheken die worden geladen die het UI moduletype uitvoeren.

## Clientlibs {#clientlibs}

De sectie van Clientlibs maakt een lijst van alle t [ omslagen van de cliëntbibliotheek ](/help/implementing/developing/introduction/clientlibs.md) die ContextHub heeft geladen. De clientbibliotheken worden als volgt gecategoriseerd:

* **kernel.js:** de bibliotheken van de Cliënt die het kader ContextHub, de segmentmotor, en opslagtypes uitvoeren.
* **ui.js:** de bibliotheken van de Cliënt die ContextHub UI en UI moduletypes uitvoeren.
* **style.css:** CSS dossiers die van cliëntbibliotheken worden geladen.

## URL&#39;s {#urls}

De sectie URLs bevat verbindingen aan eigenschappen ContextHub:

* **redacteur van de Configuratie:** opent de [ pagina van de Configuratie ContextHub ](configuring-contexthub.md) waar u opslag, wijzen UI, en modules kunt vormen UI.
* **Configuratie van modules ContextHub:** opent het `/etc/cloudsettings/default/contexthub.config.kernel.js` dossier, dat de objecten van JavaScript vertegenwoordiging van de ContextHub opslagconfiguraties bevat.
* **Configuratie van ContextHub UI:** opent het `/etc/cloudsettings/default/contexthub.config.ui.js` dossier, dat de objecten van JavaScript vertegenwoordiging van de ContextHub UI wijzeconfiguraties bevat.
* **kernel.js:** opent het `/etc/cloudsettings/default/contexthub.kernel.js` dossier, dat de broncode van de cliëntbibliotheken bevat die het kader ContextHub, de segmentmotor, en opslagtypes uitvoeren.
* **ui.js:** opent het `/etc/cloudsettings/default/contexthub.ui.js` dossier, dat de broncode van de cliëntbibliotheken bevat die de ContextHub UI en UI moduletypes uitvoeren.
* **style.css:** opent het `/etc/cloudsettings/default/contexthub.styles.css` dossier, dat de CSS stijlen voor de modules ContextHub UI en UI bevat.
