---
title: ContextHub uitbreiden
description: Bepaal nieuwe types van opslag ContextHub en modules wanneer de verstrekte niet aan uw oplossingsvereisten voldoen
exl-id: ba817c18-f8bd-485d-b043-87593a6a93b5
feature: Developing, Personalization
role: Admin, Architect, Developer
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 0%

---

# ContextHub uitbreiden {#extending-contexthub}

Bepaal nieuwe types van opslag ContextHub en modules wanneer de verstrekte niet aan uw oplossingsvereisten voldoen.

## Aangepaste winkelkandidaten maken {#creating-custom-store-candidates}

ContextHub-winkels worden gemaakt van geregistreerde winkelkandidaten. Als u een aangepast archief wilt maken, moet u een winkelkandidaat maken en registreren.

Het javascript-bestand dat de code bevat die de winkelkandidaat maakt en registreert, moet in een [clientbibliotheekmap](/help/implementing/developing/introduction/clientlibs.md). De categorie van de map moet overeenkomen met het volgende patroon:

```xml
contexthub.store.[storeType]
```

De `storeType` deel van de categorie is `storeType` waarmee de opslagkandidaat is geregistreerd. (Zie [Registreren van een ContextHub Store-kandidaat](#registering-a-contexthub-store-candidate)). Bijvoorbeeld voor storeType van `contexthub.mystore`moet de categorie van de clientbibliotheekmap `contexthub.store.contexthub.mystore`.

### Een ContextHub Store-kandidaat maken {#creating-a-contexthub-store-candidate}

Als u een winkelkandidaat wilt maken, gebruikt u de [`ContextHub.Utils.inheritance.inherit`](contexthub-api.md#inherit-child-parent) functie om één van de basisopslag uit te breiden:

* [` ContextHub.Store.PersistedStore`](contexthub-api.md#contexthub-store-persistedstore)
* [` ContextHub.Store.SessionStore`](contexthub-api.md#contexthub-store-sessionstore)
* [` ContextHub.Store.JSONPStore`](contexthub-api.md#contexthub-store-jsonpstore)
* [` ContextHub.Store.PersistedJSONPStore`](contexthub-api.md#contexthub-store-persistedjsonpstore)

Elke basisopslag breidt het [`ContextHub.Store.Core`](contexthub-api.md#contexthub-store-core) opslaan.

In het volgende voorbeeld wordt de eenvoudigste extensie van de `ContextHub.Store.PersistedStore` Winkelkandidaat:

```javascript
myStoreCandidate = function(){};
ContextHub.Utils.inheritance.inherit(myStoreCandidate,ContextHub.Store.PersistedStore);
```

Realistisch, zullen uw kandidaten van de douaneopslag extra functies bepalen of zullen de aanvankelijke configuratie van de opslag met voeten treden. Meerdere [voorbeeldopslagkandidaten](sample-stores.md) zijn hieronder geïnstalleerd in de opslagplaats `/libs/granite/contexthub/components/stores`.

### Registreren van een ContextHub Store-kandidaat {#registering-a-contexthub-store-candidate}

Registreer een opslagkandidaat om het met het kader te integreren ContextHub en opslag toe te laten om van het worden gecreeerd. Als u een winkelkandidaat wilt registreren, gebruikt u de opdracht [`registerStoreCandidate`](contexthub-api.md#registerstorecandidate-store-storetype-priority-applies) de functie van de `ContextHub.Utils.storeCandidates` klasse.

Wanneer u een opslagkandidaat registreert, geeft u een naam voor het type winkel op. Wanneer het creëren van een opslag van de kandidaat, gebruikt u het opslagtype om de kandidaat te identificeren waarop het is gebaseerd.

Wanneer u een winkelkandidaat registreert, geeft u de prioriteit aan. Wanneer een opslagkandidaat wordt geregistreerd gebruikend het zelfde archieftype zoals een reeds-geregistreerde opslagkandidaat, wordt de kandidaat met de hogere prioriteit gebruikt. Daarom kunt u bestaande opslagkandidaten met nieuwe implementaties met voeten treden.

```javascript
ContextHub.Utils.storeCandidates.registerStoreCandidate(myStoreCandidate,
                                'contexthub.mystorecandidate', 0);
```

In de meeste gevallen is slechts één kandidaat nodig en kan de prioriteit worden ingesteld op `0`, maar als je geïnteresseerd bent, kun je meer weten over [meer geavanceerde registraties,](contexthub-api.md#registerstorecandidate-store-storetype-priority-applies) dat één van weinig opslagimplementaties toestaat om op javascript voorwaarde worden gekozen (`applies`) en kandidaat-prioriteit.

## ContextHub UI-moduletypen maken {#creating-contexthub-ui-module-types}

Creeer de types van de module van douane UI wanneer degenen die zijn [geïnstalleerd met ContextHub](sample-modules.md) voldoet niet aan uw vereisten. Als u een type UI-module wilt maken, maakt u een renderer voor een UI-module door het dialoogvenster `ContextHub.UI.BaseModuleRenderer` en registreert deze vervolgens met `ContextHub.UI`.

Als u een renderer voor een UI-module wilt maken, maakt u een `Class` object dat de logica bevat die de UI-module rendert. De klasse moet minimaal de volgende handelingen uitvoeren:

* Breid uit `ContextHub.UI.BaseModuleRenderer` klasse. Deze klasse is de basisimplementatie voor alle UI modulerenderers. De `Class` object definieert een eigenschap met de naam `extend` die u gebruikt om deze klasse te benoemen als de klasse die wordt uitgebreid.
* Geef een standaardconfiguratie op. Een `defaultConfig` eigenschap. Deze eigenschap is een object dat de eigenschappen bevat die zijn gedefinieerd voor de [`contexthub.base`](sample-modules.md#contexthub-base-ui-module-type) UI-module en andere eigenschappen die u nodig hebt.

De bron voor `ContextHub.UI.BaseModuleRenderer` bevindt zich op `/libs/granite/contexthub/code/ui/container/js/ContextHub.UI.BaseModuleRenderer.js`.  Als u de renderer wilt registreren, gebruikt u de [`registerRenderer`](contexthub-api.md#registerrenderer-moduletype-renderer-dontrender) van de `ContextHub.UI` klasse. U moet een naam voor het moduletype verstrekken. Wanneer beheerders een UI-module maken op basis van deze renderer, geven ze deze naam op.

Maak en registreer de rendererklasse in een automatisch uitgevoerde anonieme functie. Het volgende voorbeeld is gebaseerd op de broncode voor de `contexthub.browserinfo` UI-module. Deze UI-module is een eenvoudige uitbreiding van de `ContextHub.UI.BaseModuleRenderer` klasse.

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

Het javascript-bestand dat de code bevat waarmee de renderer wordt gemaakt en geregistreerd, moet in een [clientbibliotheekmap](/help/implementing/developing/introduction/clientlibs.md). De categorie van de map moet overeenkomen met het volgende patroon:

```javascript
contexthub.module.[moduleType]
```

De `[moduleType]` deel van de categorie is `moduleType` waarmee de modulerenderer wordt geregistreerd. Bijvoorbeeld voor `moduleType` van `contexthub.browserinfo`moet de categorie van de clientbibliotheekmap `contexthub.module.contexthub.browserinfo`.
