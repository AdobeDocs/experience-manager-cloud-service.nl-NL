---
title: ContextHub Diagnostics
description: ContextHub verstrekt een diagnostische pagina waar u een overzicht van het kader ContextHub kunt zien
translation-type: tm+mt
source-git-commit: 1c518830f0bc9d9c7e6b11bebd6c0abd668ce040
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---


# ContextHub Diagnostics {#contexthub-diagnostics}

ContextHub verstrekt een diagnostische pagina waar u een overzicht van het kader kunt zien ContextHub. Als u de pagina wilt openen, gaat u bijvoorbeeld naar de `contexthub.diagnostics.html` pagina van de AEM auteur:

`http://<host>:<port>/conf/<site>/settings/cloudsettings/default/contexthub.diagnostics.html`

De pagina van de Diagnostiek ContextHub verstrekt informatie over de opslag en modules UI die zijn gecreeerd, de omslagen van de cliëntbibliotheek die, en verbindingen aan nuttige pagina&#39;s worden geladen.

>[!NOTE]
>
>De foutopsporingsmodus moet zijn ingeschakeld om diagnostische gegevens te kunnen retourneren. Als dit niet het geval is, is de pagina Diagnostics leeg. Zie [dit document](configuring-contexthub.md#debugging-contexthub) voor meer informatie over het inschakelen van de foutopsporingsmodus.

## Winkels {#stores}

De sectie van Sporen maakt een lijst van alle opslag ContextHub die zijn gevormd. Elk item in de lijst bestaat uit de volgende informatie:

* **Titel:** Het [opslagtype](sample-stores.md) waarop de winkel is gebaseerd.
* **pad:** Het pad naar de opslagplaats die de configuratie bevat.
* **resourceType:** Het pad van het opslagknooppunt waar het opslagtype is gedefinieerd.
* **clientlibs:** De categorieën van de cliëntbibliotheken die worden geladen die het archieftype uitvoeren.

## Modules {#modules}

De sectie van Modules maakt een lijst van alle modules ContextHub UI die zijn gevormd. Elk item in de lijst bestaat uit de volgende informatie:

* **Titel:** Het type [van Module](sample-modules.md) UI dat de module UI gebaseerd is.
* **pad:** Het pad naar de opslagplaats die de configuratie bevat.
* **resourceType:** Het pad van het knooppunt in de repository waar het type UI-module is gedefinieerd.
* **clientlibs:** De categorieën van de cliëntbibliotheken die worden geladen die het UI moduletype uitvoeren.

## Clientlibs {#clientlibs}

De sectie Clientlibs maakt een lijst van alle omslagen [van de](/help/implementing/developing/introduction/clientlibs.md) cliëntbibliotheek die ContextHub heeft geladen. De clientbibliotheken worden als volgt gecategoriseerd:

* **kernel.js:** De bibliotheken van de cliënt die het kader ContextHub, de segmentmotor, en opslagtypes uitvoeren.
* **ui.js:** De bibliotheken van de cliënt die ContextHub UI en UI moduletypes uitvoeren.
* **style.css:** CSS-bestanden die worden geladen uit clientbibliotheken.

## URL&#39;s {#urls}

De sectie URLs bevat verbindingen aan eigenschappen ContextHub:

* **Configuratie-editor:** Opent de pagina [van de Configuratie](configuring-contexthub.md) ContextHub waar u opslag, wijzen UI, en modules kunt vormen UI.
* **Configuratie van ContextHub-modules:** Opent het `/etc/cloudsettings/default/contexthub.config.kernel.js` dossier, dat de Javascript objecten vertegenwoordiging van de ContextHub opslagconfiguraties bevat.
* **Configuratie van ContextHub UI:** Opent het `/etc/cloudsettings/default/contexthub.config.ui.js` dossier, dat de Javascript objecten vertegenwoordiging van de ContextHub UI wijzeconfiguraties bevat.
* **kernel.js:** Opent het `/etc/cloudsettings/default/contexthub.kernel.js` dossier, dat de broncode van de cliëntbibliotheken bevat die het kader ContextHub, de segmentmotor, en opslagtypes uitvoeren.
* **ui.js:** Opent het `/etc/cloudsettings/default/contexthub.ui.js` dossier, dat de broncode van de cliëntbibliotheken bevat die de ContextHub UI en UI moduletypes uitvoeren.
* **style.css:** Opent het `/etc/cloudsettings/default/contexthub.styles.css` dossier, dat de CSS stijlen voor de modules ContextHub UI en UI bevat.
