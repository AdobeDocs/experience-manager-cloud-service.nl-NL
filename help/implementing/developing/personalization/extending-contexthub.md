---
title: ContextHub uitbreiden
description: Bepaal nieuwe types van opslag ContextHub en modules wanneer de verstrekte niet aan uw oplossingsvereisten voldoen
translation-type: tm+mt
source-git-commit: ddfdcf74977adf00bc0ab01b0b1a669781f0d730
workflow-type: tm+mt
source-wordcount: '624'
ht-degree: 0%

---


# ContextHub uitbreiden {#extending-contexthub}

Bepaal nieuwe types van opslag ContextHub en modules wanneer de verstrekte niet aan uw oplossingsvereisten voldoen.

## Aangepaste winkelkandidaten maken {#creating-custom-store-candidates}

ContextHub-winkels worden gemaakt van geregistreerde winkelkandidaten. Als u een aangepast archief wilt maken, moet u een winkelkandidaat maken en registreren.

<!--The javascript file that includes the code that creates and registers the store candidate must be included in a [client library folder](/help/sites-developing/clientlibs.md#creating-client-library-folders). The category of the folder must match the following pattern:-->

Het javascript-bestand dat de code bevat waarmee de opslagkandidaat wordt gemaakt en geregistreerd, moet in een clientbibliotheekmap worden opgenomen. De categorie van de map moet overeenkomen met het volgende patroon:

```xml
contexthub.store.[storeType]
```

Het `storeType` deel van de categorie is het `storeType` waarmee de winkelkandidaat is geregistreerd. (Zie Een ContextHub Store-kandidaat [](#registering-a-contexthub-store-candidate)registreren). Bijvoorbeeld, voor storeType van `contexthub.mystore`, moet de categorie van de omslag van de cliëntbibliotheek zijn `contexthub.store.contexthub.mystore`.

### Een ContextHub Store-kandidaat maken {#creating-a-contexthub-store-candidate}

Om een opslagkandidaat tot stand te brengen, gebruikt u de [`ContextHub.Utils.inheritance.inherit`](contexthub-api.md#inherit-child-parent) functie om één van de basisopslag uit te breiden:

* [`ContextHub.Store.PersistedStore`](contexthub-api.md#contexthub-store-persistedstore)
* [`ContextHub.Store.SessionStore`](contexthub-api.md#contexthub-store-sessionstore)
* [`ContextHub.Store.JSONPStore`](contexthub-api.md#contexthub-store-jsonpstore)
* [`ContextHub.Store.PersistedJSONPStore`](contexthub-api.md#contexthub-store-persistedjsonpstore)

Merk op dat elke basisopslag de [`ContextHub.Store.Core`](contexthub-api.md#contexthub-store-core) opslag uitbreidt.

In het volgende voorbeeld wordt de eenvoudigste extensie van de `ContextHub.Store.PersistedStore` winkelkandidaat gemaakt:

```javascript
myStoreCandidate = function(){};
ContextHub.Utils.inheritance.inherit(myStoreCandidate,ContextHub.Store.PersistedStore);
```

Realistisch, zullen uw kandidaten van de douaneopslag extra functies bepalen of zullen de aanvankelijke configuratie van de opslag met voeten treden. Verschillende [voorbeeldwinkelkandidaten](sample-stores.md) zijn in de onderstaande opslagplaats geïnstalleerd `/libs/granite/contexthub/components/stores`.

### Registreren van een ContextHub Store-kandidaat {#registering-a-contexthub-store-candidate}

Registreer een opslagkandidaat om het met het kader te integreren ContextHub en opslag toe te laten om van het worden gecreeerd. Als u een winkelkandidaat wilt registreren, gebruikt u de [`registerStoreCandidate`](contexthub-api.md#registerstorecandidate-store-storetype-priority-applies) functie van de `ContextHub.Utils.storeCandidates` klasse.

Wanneer u een opslagkandidaat registreert, geeft u een naam voor het type winkel op. Wanneer het creëren van een opslag van de kandidaat, gebruikt u het opslagtype om de kandidaat te identificeren waarop het is gebaseerd.

Wanneer u een winkelkandidaat registreert, geeft u de prioriteit aan. Wanneer een opslagkandidaat wordt geregistreerd gebruikend het zelfde archieftype zoals een reeds-geregistreerde opslagkandidaat, wordt de kandidaat met de hogere prioriteit gebruikt. Daarom kunt u bestaande opslagkandidaten met nieuwe implementaties met voeten treden.

```javascript
ContextHub.Utils.storeCandidates.registerStoreCandidate(myStoreCandidate,
                                'contexthub.mystorecandidate', 0);
```

In de meeste gevallen is slechts één kandidaat noodzakelijk en de prioriteit kan worden geplaatst aan `0`, maar als u geinteresseerd bent kunt u over [geavanceerdere registraties leren,](contexthub-api.md#registerstorecandidate-store-storetype-priority-applies) die één van weinig opslagimplementaties toestaat om op voorwaarde javascript (`applies`) en kandidaatprioriteit worden gekozen.

## ContextHub UI-moduletypen maken {#creating-contexthub-ui-module-types}

Creeer de moduletypes van douane UI wanneer degenen die met ContextHub [worden](sample-modules.md) geïnstalleerd niet aan uw vereisten voldoen. Als u een type UI-module wilt maken, maakt u een nieuwe UI-modulerenderer door de `ContextHub.UI.BaseModuleRenderer` klasse uit te breiden en vervolgens te registreren met `ContextHub.UI`.

Als u een renderer voor een UI-module wilt maken, maakt u een `Class` object dat de logica bevat die de UI-module rendert. De klasse moet minimaal de volgende handelingen uitvoeren:

* Breid de `ContextHub.UI.BaseModuleRenderer` klasse uit. Deze klasse is de basisimplementatie voor alle UI modulerenderers. Het `Class` object definieert een eigenschap met de naam `extend` die u gebruikt om deze klasse een naam te geven als de klasse die wordt uitgebreid.
* Geef een standaardconfiguratie op. Maak een `defaultConfig` eigenschap. Dit bezit is een voorwerp dat de eigenschappen omvat die voor de module [`contexthub.base`](sample-modules.md#contexthub-base-ui-module-type) UI, en om het even welke andere eigenschappen worden bepaald die u vereist.

De bron voor `ContextHub.UI.BaseModuleRenderer` is gevestigd bij `/libs/granite/contexthub/code/ui/container/js/ContextHub.UI.BaseModuleRenderer.js`.  Gebruik de [`registerRenderer`](contexthub-api.md#registerrenderer-moduletype-renderer-dontrender) methode van de `ContextHub.UI` klasse om de renderer te registreren. U moet een naam voor het moduletype verstrekken. Wanneer beheerders een UI-module maken op basis van deze renderer, geven ze deze naam op.

Maak en registreer de rendererklasse in een automatisch uitgevoerde anonieme functie. Het volgende voorbeeld is gebaseerd op de broncode voor de module `contexthub.browserinfo` UI. Deze UI-module is een eenvoudige uitbreiding van de `ContextHub.UI.BaseModuleRenderer` klasse.

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

<!--The javascript file that includes the code that creates and registers the renderer must be included in a [client library folder](/help/sites-developing/clientlibs.md#creating-client-library-folders). The category of the folder must match the following pattern:-->

Het javascript-bestand dat de code bevat waarmee de renderer wordt gemaakt en geregistreerd, moet in een clientbibliotheekmap worden opgenomen. De categorie van de map moet overeenkomen met het volgende patroon:

```javascript
contexthub.module.[moduleType]
```

Het `[moduleType]` deel van de categorie is `moduleType` waarmee modulerenderer wordt geregistreerd. Bijvoorbeeld, voor `moduleType` van `contexthub.browserinfo`, moet de categorie van de omslag van de cliëntbibliotheek zijn `contexthub.module.contexthub.browserinfo`.
