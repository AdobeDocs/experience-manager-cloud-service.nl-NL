---
title: ContextHub uitbreiden
description: Bepaal nieuwe types van opslag ContextHub en modules wanneer de verstrekte niet aan uw oplossingsvereisten voldoen
exl-id: ba817c18-f8bd-485d-b043-87593a6a93b5
feature: Developing, Personalization
role: Admin, Architect, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 0%

---

# ContextHub uitbreiden {#extending-contexthub}

Bepaal nieuwe types van opslag ContextHub en modules wanneer de verstrekte niet aan uw oplossingsvereisten voldoen.

## Aangepaste winkelkandidaten maken {#creating-custom-store-candidates}

ContextHub-winkels worden gemaakt van geregistreerde winkelkandidaten. Als u een aangepast archief wilt maken, moet u een winkelkandidaat maken en registreren.

Het javascript- dossier dat de code omvat die tot en registreert de opslagkandidaat in de omslag van de a [ cliëntbibliotheek ](/help/implementing/developing/introduction/clientlibs.md) moet worden omvat. De categorie van de map moet overeenkomen met het volgende patroon:

```xml
contexthub.store.[storeType]
```

Het `storeType` -gedeelte van de categorie is de `storeType` waarmee de winkelkandidaat is geregistreerd. (Zie [ registrerend een Kandidaat van de Winkel ContextHub ](#registering-a-contexthub-store-candidate)). Voor het storeType van `contexthub.mystore` moet de categorie van de clientbibliotheekmap bijvoorbeeld `contexthub.store.contexthub.mystore` zijn.

### Een ContextHub Store-kandidaat maken {#creating-a-contexthub-store-candidate}

Als u een winkelkandidaat wilt maken, gebruikt u de functie [`ContextHub.Utils.inheritance.inherit`](contexthub-api.md#inherit-child-parent) om een van de basiswinkels uit te breiden:

* [` ContextHub.Store.PersistedStore`](contexthub-api.md#contexthub-store-persistedstore)
* [` ContextHub.Store.SessionStore`](contexthub-api.md#contexthub-store-sessionstore)
* [` ContextHub.Store.JSONPStore`](contexthub-api.md#contexthub-store-jsonpstore)
* [` ContextHub.Store.PersistedJSONPStore`](contexthub-api.md#contexthub-store-persistedjsonpstore)

Elke basisopslag breidt de [`ContextHub.Store.Core`](contexthub-api.md#contexthub-store-core) store uit.

In het volgende voorbeeld wordt de eenvoudigste extensie van de opslagkandidaat van `ContextHub.Store.PersistedStore` gemaakt:

```javascript
myStoreCandidate = function(){};
ContextHub.Utils.inheritance.inherit(myStoreCandidate,ContextHub.Store.PersistedStore);
```

Realistisch, zullen uw kandidaten van de douaneopslag extra functies bepalen of zullen de aanvankelijke configuratie van de opslag met voeten treden. Verscheidene [ de kandidaten van de steekproefopslag ](sample-stores.md) zijn geïnstalleerd in de bewaarplaats hieronder `/libs/granite/contexthub/components/stores`.

### Registreren van een ContextHub Store-kandidaat {#registering-a-contexthub-store-candidate}

Registreer een opslagkandidaat om het met het kader te integreren ContextHub en opslag toe te laten om van het worden gecreeerd. Gebruik de functie [`registerStoreCandidate`](contexthub-api.md#registerstorecandidate-store-storetype-priority-applies) van de `ContextHub.Utils.storeCandidates` -klasse om een winkelkandidaat te registreren.

Wanneer u een opslagkandidaat registreert, geeft u een naam voor het type winkel op. Wanneer het creëren van een opslag van de kandidaat, gebruikt u het opslagtype om de kandidaat te identificeren waarop het is gebaseerd.

Wanneer u een winkelkandidaat registreert, geeft u de prioriteit aan. Wanneer een opslagkandidaat wordt geregistreerd gebruikend het zelfde archieftype zoals een reeds-geregistreerde opslagkandidaat, wordt de kandidaat met de hogere prioriteit gebruikt. Daarom kunt u bestaande opslagkandidaten met nieuwe implementaties met voeten treden.

```javascript
ContextHub.Utils.storeCandidates.registerStoreCandidate(myStoreCandidate,
                                'contexthub.mystorecandidate', 0);
```

In de meeste gevallen is slechts één kandidaat noodzakelijk en de prioriteit kan aan `0` worden geplaatst, maar als u geinteresseerd bent kunt u over [ meer geavanceerde registraties ](contexthub-api.md#registerstorecandidate-store-storetype-priority-applies) leren, die één van weinige opslagimplementaties toestaat om op voorwaarde javascript (`applies`) en kandidaatprioriteit worden gekozen.

## ContextHub UI-moduletypen maken {#creating-contexthub-ui-module-types}

Creeer de moduletypes van douane UI wanneer degenen die [ met ContextHub ](sample-modules.md) worden geïnstalleerd niet aan uw vereisten voldoen. Als u een type UI-module wilt maken, maakt u een renderer voor een UI-module door de klasse `ContextHub.UI.BaseModuleRenderer` uit te breiden en deze vervolgens te registreren bij `ContextHub.UI` .

Als u een renderer voor een UI-module wilt maken, maakt u een `Class` -object dat de logica bevat die de UI-module rendert. De klasse moet minimaal de volgende handelingen uitvoeren:

* Breid de `ContextHub.UI.BaseModuleRenderer` -klasse uit. Deze klasse is de basisimplementatie voor alle UI modulerenderers. Het object `Class` definieert een eigenschap met de naam `extend` die u gebruikt om deze klasse een naam te geven als de klasse die wordt uitgebreid.
* Geef een standaardconfiguratie op. Maak een eigenschap `defaultConfig` . Deze eigenschap is een object dat de eigenschappen bevat die zijn gedefinieerd voor de module [`contexthub.base`](sample-modules.md#contexthub-base-ui-module-type) UI en andere eigenschappen die u nodig hebt.

De bron voor `ContextHub.UI.BaseModuleRenderer` bevindt zich in `/libs/granite/contexthub/code/ui/container/js/ContextHub.UI.BaseModuleRenderer.js` .  Gebruik de methode [`registerRenderer`](contexthub-api.md#registerrenderer-moduletype-renderer-dontrender) van de `ContextHub.UI` -klasse om de renderer te registreren. U moet een naam voor het moduletype verstrekken. Wanneer beheerders een UI-module maken op basis van deze renderer, geven ze deze naam op.

Maak en registreer de rendererklasse in een automatisch uitgevoerde anonieme functie. Het volgende voorbeeld is gebaseerd op de broncode voor de `contexthub.browserinfo` UI module. Deze UI-module is een eenvoudige uitbreiding van de klasse `ContextHub.UI.BaseModuleRenderer` .

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

Het javascript- dossier dat de code omvat die tot renderer leidt en registreert moet in de omslag van de a [ cliëntbibliotheek ](/help/implementing/developing/introduction/clientlibs.md) worden omvat. De categorie van de map moet overeenkomen met het volgende patroon:

```javascript
contexthub.module.[moduleType]
```

Het `[moduleType]` -gedeelte van de categorie is de `moduleType` waarmee de modulerenderer is geregistreerd. Voor `moduleType` of `contexthub.browserinfo` moet de categorie van de clientbibliotheekmap bijvoorbeeld `contexthub.module.contexthub.browserinfo` zijn.
