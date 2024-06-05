---
title: ContextHub Diagnostics
description: ContextHub verstrekt een diagnostische pagina waar u een overzicht van het kader ContextHub kunt zien
exl-id: c8d4e160-ea02-49f3-9e31-119445ef5a68
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# ContextHub Diagnostics {#contexthub-diagnostics}

ContextHub verstrekt een diagnostische pagina waar u een overzicht van het kader kunt zien ContextHub. Ga naar de pagina om de pagina te openen `contexthub.diagnostics.html` pagina van de AEM auteur, bijvoorbeeld:

`http://<host>:<port>/conf/<site>/settings/cloudsettings/default/contexthub.diagnostics.html`

De pagina van de Diagnostiek ContextHub verstrekt informatie over de opslag en modules UI die zijn gecreeerd, de omslagen van de cliëntbibliotheek die, en verbindingen aan nuttige pagina&#39;s worden geladen.

>[!NOTE]
>
>Om diagnostische informatie terug te geven moet de foutopsporingsmodus zijn ingeschakeld, anders is de diagnostische pagina leeg. Zie [dit document](configuring-contexthub.md#debugging-contexthub) voor details over hoe te om te toelaten zuiveren wijze.

## Winkels {#stores}

De sectie van Sporen maakt een lijst van alle opslag ContextHub die zijn gevormd. Elk item in de lijst bestaat uit de volgende informatie:

* **Titel:** De [winkeltype](sample-stores.md) dat de winkel hierop is gebaseerd.
* **pad:** Het pad naar de opslagplaats die de configuratie bevat.
* **resourceType:** Het pad van het opslagknooppunt waar het opslagtype is gedefinieerd.
* **clientlibs:** De categorieën van de cliëntbibliotheken die worden geladen die het archieftype uitvoeren.

## Modules {#modules}

De sectie van Modules maakt een lijst van alle modules ContextHub UI die zijn gevormd. Elk item in de lijst bestaat uit de volgende informatie:

* **Titel:** De [Type UI-module](sample-modules.md) dat de module UI op gebaseerd is.
* **pad:** Het pad naar de opslagplaats die de configuratie bevat.
* **resourceType:** Het pad van het knooppunt in de repository waar het type UI-module is gedefinieerd.
* **clientlibs:** De categorieën van de cliëntbibliotheken die worden geladen die het UI moduletype uitvoeren.

## Clientlibs {#clientlibs}

In de sectie Clientlibs worden alle clips weergegeven[clientbibliotheekmappen](/help/implementing/developing/introduction/clientlibs.md) die ContextHub heeft geladen. De clientbibliotheken worden als volgt gecategoriseerd:

* **kernel.js:** De bibliotheken van de cliënt die het kader ContextHub, de segmentmotor, en opslagtypes uitvoeren.
* **ui.js:** De bibliotheken van de cliënt die ContextHub UI en UI moduletypes uitvoeren.
* **style.css:** CSS-bestanden die worden geladen uit clientbibliotheken.

## URL&#39;s {#urls}

De sectie URLs bevat verbindingen aan eigenschappen ContextHub:

* **Configuratie-editor:** Hiermee opent u de [ContextHub Configuration-pagina](configuring-contexthub.md) waar u opslag, wijzen UI, en modules UI kunt vormen.
* **Configuratie van ContextHub-modules:** Hiermee opent u de `/etc/cloudsettings/default/contexthub.config.kernel.js` bestand, dat de JavaScript-objectrepresentatie van de ContextHub-opslagconfiguraties bevat.
* **Configuratie van ContextHub UI:** Hiermee opent u de `/etc/cloudsettings/default/contexthub.config.ui.js` bestand, dat de JavaScript-objectrepresentatie bevat van de ContextHub UI-modusconfiguraties.
* **kernel.js:** Hiermee opent u de `/etc/cloudsettings/default/contexthub.kernel.js` dossier, dat de broncode van de cliëntbibliotheken bevat die het kader ContextHub, de segmentmotor, en opslagtypes uitvoeren.
* **ui.js:** Hiermee opent u de `/etc/cloudsettings/default/contexthub.ui.js` dossier, dat de broncode van de cliëntbibliotheken bevat die de ContextHub UI en UI moduletypes uitvoeren.
* **style.css:** Hiermee opent u de `/etc/cloudsettings/default/contexthub.styles.css` bestand, dat de CSS-stijlen voor de modules ContextHub UI en UI bevat.
