---
title: ContextHub uitbreiden
description: Bepaal nieuwe types van opslag ContextHub en modules wanneer de verstrekte niet aan uw oplossingsvereisten voldoen
translation-type: tm+mt
source-git-commit: 1c518830f0bc9d9c7e6b11bebd6c0abd668ce040
workflow-type: tm+mt
source-wordcount: '624'
ht-degree: 0%

---


# ContextHub uitbreiden {#extending-contexthub}

Bepaal nieuwe types van opslag ContextHub en modules wanneer de verstrekte niet aan uw oplossingsvereisten voldoen.

## Aangepaste winkelkandidaten {#creating-custom-store-candidates} maken

ContextHub-winkels worden gemaakt van geregistreerde winkelkandidaten. Als u een aangepast archief wilt maken, moet u een winkelkandidaat maken en registreren.

Het javascript-bestand dat de code bevat waarmee de opslagkandidaat wordt gemaakt en geregistreerd, moet worden opgenomen in een [clientbibliotheekmap](/help/implementing/developing/introduction/clientlibs.md). De categorie van de map moet overeenkomen met het volgende patroon:

```xml
contexthub.store.[storeType]
```

Het `storeType` deel van de categorie is `storeType` waarmee de opslagkandidaat wordt geregistreerd. (Zie [Registrerend een kandidaat van de Winkel ContextHub](#registering-a-contexthub-store-candidate)). Voor het storeType van `contexthub.mystore` moet de categorie van de map met de clientbibliotheek bijvoorbeeld `contexthub.store.contexthub.mystore` zijn.

### Een ContextHub Store-kandidaat {#creating-a-contexthub-store-candidate} maken

Om een opslagkandidaat tot stand te brengen, gebruikt u de [`ContextHub.Utils.inheritance.inherit`](contexthub-api.md#inherit-child-parent) functie om één van de basisopslag uit te breiden:

* [`ContextHub.Store.PersistedStore`](contexthub-api.md#contexthub-store-persistedstore)
* [`ContextHub.Store.SessionStore`](contexthub-api.md#contexthub-store-sessionstore)
* [`ContextHub.Store.JSONPStore`](contexthub-api.md#contexthub-store-jsonpstore)
* [`ContextHub.Store.PersistedJSONPStore`](contexthub-api.md#contexthub-store-persistedjsonpstore)

Merk op dat elke basisopslag [`ContextHub.Store.Core`](contexthub-api.md#contexthub-store-core) opslag uitbreidt.

In het volgende voorbeeld wordt de eenvoudigste extensie van de opslagkandidaat `ContextHub.Store.PersistedStore` gemaakt:

```javascript
myStoreCandidate = function(){};
ContextHub.Utils.inheritance.inherit(myStoreCandidate,ContextHub.Store.PersistedStore);
```

Realistisch, zullen uw kandidaten van de douaneopslag extra functies bepalen of zullen de aanvankelijke configuratie van de opslag met voeten treden. Verschillende [voorbeeldopslagkandidaten](sample-stores.md) worden in de opslagplaats onder `/libs/granite/contexthub/components/stores` geïnstalleerd.

### Registreren van een kandidaat van de Opslag ContextHub {#registering-a-contexthub-store-candidate}

Registreer een opslagkandidaat om het met het kader te integreren ContextHub en opslag toe te laten om van het worden gecreeerd. Als u een winkelkandidaat wilt registreren, gebruikt u de functie [`registerStoreCandidate`](contexthub-api.md#registerstorecandidate-store-storetype-priority-applies) van de klasse `ContextHub.Utils.storeCandidates`.

Wanneer u een opslagkandidaat registreert, geeft u een naam voor het type winkel op. Wanneer het creëren van een opslag van de kandidaat, gebruikt u het opslagtype om de kandidaat te identificeren waarop het is gebaseerd.

Wanneer u een winkelkandidaat registreert, geeft u de prioriteit aan. Wanneer een opslagkandidaat wordt geregistreerd gebruikend het zelfde archieftype zoals een reeds-geregistreerde opslagkandidaat, wordt de kandidaat met de hogere prioriteit gebruikt. Daarom kunt u bestaande opslagkandidaten met nieuwe implementaties met voeten treden.

```javascript
ContextHub.Utils.storeCandidates.registerStoreCandidate(myStoreCandidate,
                                'contexthub.mystorecandidate', 0);
```

In de meeste gevallen is slechts één kandidaat noodzakelijk en de prioriteit kan aan `0` worden geplaatst, maar als u geinteresseerd bent kunt u over [geavanceerdere registraties leren,](contexthub-api.md#registerstorecandidate-store-storetype-priority-applies) die één van weinige opslagimplementaties toelaat worden gekozen gebaseerd op javascript voorwaarde (`applies`) en kandidaatprioriteit.

## ContextHub UI-moduletypen maken {#creating-contexthub-ui-module-types}

Creeer de types van de douanemodule UI wanneer degenen die [geïnstalleerd met ContextHub](sample-modules.md) zijn niet aan uw vereisten voldoen. Als u een type UI-module wilt maken, maakt u een nieuwe UI-modulerenderer door de klasse `ContextHub.UI.BaseModuleRenderer` uit te breiden en deze vervolgens te registreren met `ContextHub.UI`.

Om een UI modulerenderer tot stand te brengen, creeer een `Class` voorwerp dat de logica bevat die de module UI teruggeeft. De klasse moet minimaal de volgende handelingen uitvoeren:

* Breid de `ContextHub.UI.BaseModuleRenderer` klasse uit. Deze klasse is de basisimplementatie voor alle UI modulerenderers. Met het object `Class` wordt een eigenschap met de naam `extend` gedefinieerd die u gebruikt om deze klasse een naam te geven als de klasse die wordt uitgebreid.
* Geef een standaardconfiguratie op. Maak een eigenschap `defaultConfig`. Deze eigenschap is een object dat de eigenschappen bevat die zijn gedefinieerd voor de UI-module [`contexthub.base`](sample-modules.md#contexthub-base-ui-module-type) en andere eigenschappen die u nodig hebt.

De bron voor `ContextHub.UI.BaseModuleRenderer` bevindt zich op `/libs/granite/contexthub/code/ui/container/js/ContextHub.UI.BaseModuleRenderer.js`.  Gebruik de methode [`registerRenderer`](contexthub-api.md#registerrenderer-moduletype-renderer-dontrender) van de klasse `ContextHub.UI` om de renderer te registreren. U moet een naam voor het moduletype verstrekken. Wanneer beheerders een UI-module maken op basis van deze renderer, geven ze deze naam op.

Maak en registreer de rendererklasse in een automatisch uitgevoerde anonieme functie. Het volgende voorbeeld is gebaseerd op de broncode voor `contexthub.browserinfo` UI module. Deze UI-module is een eenvoudige uitbreiding van de klasse `ContextHub.UI.BaseModuleRenderer`.

```javascript
;(function() {

    var SurferinfoRenderer = new Class({
        extend: ContextHub.UI.BaseModuleRenderer,

        defaultConfig: {
            icon: 'coral-Icon--globe',
            title: 'Browser/OS Information',

            storeMapping: {
                surferinfo: 'surferinfo'
            },

            template:
                '<p>{{surferinfo.browser.family}} {{surferinfo.browser.version}}</p>' +
                '<p>{{surferinfo.os.name}} {{surferinfo.os.version}}</p>'
        }
    });

    ContextHub.UI.registerRenderer('contexthub.browserinfo', new SurferinfoRenderer());

}());
```

Het javascript-bestand dat de code bevat die de renderer maakt en registreert, moet worden opgenomen in een [clientbibliotheekmap](/help/implementing/developing/introduction/clientlibs.md). De categorie van de map moet overeenkomen met het volgende patroon:

```javascript
contexthub.module.[moduleType]
```

Het `[moduleType]` deel van de categorie is `moduleType` waarmee modulerenderer wordt geregistreerd. Voor de `moduleType` van `contexthub.browserinfo` moet de categorie van de clientbibliotheekmap bijvoorbeeld `contexthub.module.contexthub.browserinfo` zijn.
