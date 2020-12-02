---
title: ContextHub configureren
description: Leer hoe te om de Hub van de Context te vormen.
translation-type: tm+mt
source-git-commit: b8bc27b51eefcfcfa1c23407a4ac0e7ff068081e
workflow-type: tm+mt
source-wordcount: '1683'
ht-degree: 0%

---


# ContextHub configureren {#configuring-contexthub}

ContextHub is een kader voor het opslaan van, het manipuleren van, en het voorstellen van contextgegevens. Voor meer detail op ContextHub, te zien gelieve [Overzicht van de ontwikkelaar ContextHub](contexthub.md).

U kunt de toolbar vormen ContextHub om te controleren of het op de wijze van de Voorproef verschijnt, om opslag te creëren ContextHub, en modules toe te voegen UI.

## Het tonen van en het Verbergen van ContextHub UI {#showing-and-hiding-the-contexthub-ui}

Vorm de dienst van ContextHub OSGi van Granite van Adobe om [ContextHub UI](/help/sites-cloud/authoring/personalization/targeted-content.md) op uw pagina&#39;s te tonen of te verbergen. De PID van deze service is `com.adobe.granite.contexthub.impl.ContextHubImpl.`

Om de dienst te vormen kunt u of [Webconsole](/help/implementing/deploying/configuring-osgi.md) gebruiken of een knoop JCR in de bewaarplaats gebruiken:

* **Webconsole:selecteer de eigenschap UI weergeven** om de interface weer te geven. Om UI te verbergen, ontruim het bezit UI van de Huid.
* **JCR-knooppunt:** Stel de Booleaanse  `com.adobe.granite.contexthub.show_ui` eigenschap in op  `true`. Als u de interface wilt verbergen, stelt u de eigenschap in op `false`.

Wanneer het tonen van ContextHub UI, verschijnt het slechts op pagina&#39;s op AEM auteursinstanties. De interface wordt niet weergegeven op pagina&#39;s met publicatie-instanties.

## ContextHub UI-modi en -modules toevoegen {#adding-contexthub-ui-modes-and-modules}

Vorm de wijzen UI en de modules die op de toolbar ContextHub op de wijze van de Voorproef verschijnen:

* UI-modi: Groepen van verwante modules
* Modules: Widgets die contextgegevens van een opslag blootstellen en auteurs toelaten om de context te manipuleren

UI-modi worden als een reeks pictogrammen aan de linkerkant van de werkbalk weergegeven. Wanneer geselecteerd, verschijnen de modules van een wijze UI aan het recht.

![ContextHub-werkbalk](assets/contexthub-toolbar.png)

Pictogrammen zijn verwijzingen uit de [Pictogrambibliotheek van de Koraal UI](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/coral-ui/coralui3/Coral.Icon.html#availableIcons).

### UI-modus {#adding-a-ui-mode} toevoegen

Voeg een wijze UI aan groep verwante modules ContextHub toe. Wanneer u de wijze UI creeert, verstrekt u de titel en het pictogram die in de toolbar ContextHub verschijnen.

1. Klik of tik op Gereedschappen > Sites > Context Hub in de Experience Manager.
1. Klik of tik de standaardContainer van de Configuratie.
1. Klik of tik de Configuratie van de Hub van de Context.
1. Klik of tik de Create knoop, en klik of tik dan de Wijze UI van de Hub van de Context.

   ![UI-modus toevoegen](assets/contexthub-ui-mode.png)

1. Geef waarden op voor de volgende eigenschappen:

   * Titel UI-modus: De titel die de UI-modus identificeert
   * Pictogram modus: De kiezer voor het [Koraal UI-pictogram](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/coral-ui/coralui3/Coral.Icon.html#availableIcons) dat moet worden gebruikt, bijvoorbeeld `coral-Icon--user`
   * Ingeschakeld: Selecteer om de wijze UI op de toolbar te tonen ContextHub

1. Klik op Opslaan of tik op Opslaan.

### Een UI-module {#adding-a-ui-module} toevoegen

Voeg een module ContextHub UI aan een wijze UI toe zodat het in de toolbar ContextHub voor het voorvertonen van paginainhoud verschijnt. Wanneer u een module UI toevoegt, creeert u een geval van een moduletype dat met ContextHub wordt geregistreerd. Om een module UI toe te voegen, moet u de naam van het bijbehorende moduletype kennen.

AEM verstrekt een moduletype van basisUI evenals verscheidene types van steekproefUI Module waarop u een module UI kunt baseren. De volgende tabel bevat een korte beschrijving van elke tabel. Voor informatie over het ontwikkelen van een module van douaneUI, zie [Creërend Modules UI ContextHub](extending-contexthub.md#creating-contexthub-ui-module-types).

De eigenschappen van de module UI omvatten een detailconfiguratie waar u waarden voor module-specifieke eigenschappen kunt verstrekken. U verstrekt de detailconfiguratie in formaat JSON. De kolom van het Type van Module in de lijst verstrekt verbindingen aan informatie over de code JSON die voor elk UI moduletype wordt vereist.

| Moduletype | Beschrijving | Winkel |
|---|---|---|
| [contexthub.base](sample-modules.md#contexthub-base-ui-module-type) | Een generiek type UI-module | Gevormd in de eigenschappen van de UI module |
| [contexthub.browserinfo](sample-modules.md#contexthub-browserinfo-ui-module-type) | Hiermee wordt informatie over de browser weergegeven | `surferinfo` |
| [contexthub.datetime](sample-modules.md#contexthub-datetime-ui-module-type) | Datum- en tijdgegevens weergeven | `datetime` |
| [contexthub.location](sample-modules.md#contexthub-location-ui-module-type) | Hiermee geeft u de breedte en lengte van de client en de locatie op een kaart weer. Hiermee kunt u de locatie wijzigen. | `geolocation` |
| [contexthub.screen-orientation](sample-modules.md#contexthub-screen-orientation-ui-module-type) | Geeft de schermstand van het apparaat (liggend of staand) weer | `emulators` |
| [contexthub.tagcloud](sample-modules.md#contexthub-tagcloud-ui-module-type) | Statistieken over paginatags weergeven | `tagcloud` |
| [graniet.profile](sample-modules.md#granite-profile-ui-module-type) | Hiermee geeft u de profielgegevens voor de huidige gebruiker weer, zoals `authorizableID`, `displayName` en `familyName`. U kunt de waarde van `displayName` en `familyName` veranderen. | `profile` |

1. Klik of tik op Extra > Sites > ContextHub in de Experience Manager.
1. Klik of tik de Container van de Configuratie waaraan u een module UI wilt toevoegen.
1. Klik of typ de Configuratie ContextHub waaraan u de module UI wilt toevoegen.
1. Klik of tik de wijze UI waaraan u de module UI toevoegt.
1. Klik of tik de Create knoop, dan klik of tik de Module van ContextHub UI (algemeen).

   ![De module ContextHub UI](assets/contexthub-ui-module.png)

1. Geef waarden op voor de volgende eigenschappen:

   * Titel module UI: Een titel die de UI-module identificeert
   * Moduletype: Het moduletype
   * Ingeschakeld: Selecteer om de module UI in de toolbar te tonen ContextHub

1. (Optioneel) Als u de standaardwinkelconfiguratie wilt overschrijven, voert u een JSON-object in om de UI-module te configureren.
1. Klik op Opslaan of tik op Opslaan.

## Een ContextHub-winkel {#creating-a-contexthub-store} maken

Creeer een opslag van de Hub van de Context om gebruikersgegevens en toegang tot de gegevens voort te zetten zoals nodig. ContextHub-winkels zijn gebaseerd op geregistreerde winkelkandidaten. Wanneer u de opslag creeert, hebt u de waarde van storeType nodig waarmee de opslagkandidaat werd geregistreerd. (Zie [Aangepaste winkelkandidaten maken](extending-contexthub.md#creating-custom-store-candidates).)

### Gedetailleerde opslagconfiguratie {#detailed-store-configuration}

Wanneer u een opslag vormt, laat het bezit van de Configuratie van het Detail u toe om waarden voor store-specific eigenschappen te verstrekken. De waarde is gebaseerd op de parameter `config` van de functie `init` van de opslag. Daarom of u deze waarde, en het formaat van de waarde moet verstrekken, hangt van de opslag af.

De waarde van het bezit van de Configuratie van het Detail is een `config` voorwerp in formaat JSON.

### Voorbeeld van winkelkandidaten {#sample-store-candidates}

AEM verstrekt de volgende kandidaten van de steekproefopslag waarop u een opslag kunt baseren.

| Winkeltype | Beschrijving |
|---|---|
| [aem.segmentation](sample-stores.md#aem-segmentation-sample-store-candidate) | Bewaren voor opgeloste en onopgeloste segmenten ContextHub. Wint automatisch segmenten van ContextHub SegmentManager terug |
| [contexthub.geolocation](sample-stores.md#contexthub-geolocation-sample-store-candidate) | Hiermee slaat u de breedte en lengte van de browserlocatie op. |
| [graniet.emulators](sample-stores.md#granite-emulators-sample-store-candidate) | Definieert eigenschappen en mogelijkheden voor een aantal apparaten en detecteert het huidige clientapparaat |
| [graniet.profile](sample-stores.md#granite-profile-sample-store-candidate) | Hiermee worden profielgegevens voor de huidige gebruiker opgeslagen |
| [contexthub.surferinfo](sample-stores.md#contexthub-surferinfo-sample-store-candidate) | Hiermee wordt informatie over de client opgeslagen, zoals apparaatinformatie, browsertype en vensterrichting |

1. Klik of tik op Extra > Sites > ContextHub in de Experience Manager.
1. Klik of tik de standaardconfiguratiecontainer.
1. Klik of tik Configuratie Contexthub
1. Als u een winkel wilt toevoegen, klikt of tikt u op het pictogram Maken en klikt of tikt u op ContextHub Store Configuration.

   ![Configuratie van ContextHub-store](assets/contexthub-store-configuration.png)

1. Geef waarden op voor de basisconfiguratie-eigenschappen en klik of tik op Volgende:

   * **Configuratitel:** de titel die de winkel identificeert
   * **Het Type van opslag:** de waarde van het storeType bezit van de opslagkandidaat waarop om de opslag te baseren
   * **Vereist:** Selecteren
   * **Ingeschakeld:** Selecteren om de winkel in te schakelen

1. (Optioneel) Als u de standaardopslagconfiguratie wilt overschrijven, voert u een JSON-object in het vak Detail Configuration (JSON) in.
1. Klik op Opslaan of tik op Opslaan.

## Voorbeeld: Een JSONP-service {#example-using-a-jsonp-service} gebruiken

Dit voorbeeld illustreert hoe te om een opslag te vormen en de gegevens in een module UI te tonen. In dit voorbeeld wordt de MD5-service van de site jsontest.com gebruikt als gegevensbron voor een winkel. De service retourneert de MD5-hash-code van een tekenreeks in JSON-indeling.

Een contexthub.generic-jsonp store wordt gevormd zodat het gegevens voor de de dienstvraag `https://md5.jsontest.com/?text=%22text%20to%20md5%22` opslaat. De dienst keert de volgende gegevens terug die in een module UI worden getoond:

```javascript
{
   "md5": "919a56ab62b6d5e1219fe1d95248a2c5",
   "original": "\"text to md5\""
}
```

### Een contexthub.generic-jsonp Store {#creating-a-contexthub-generic-jsonp-store} maken

De contextthub.generic-jsonp-voorbeeldopslagkandidaat stelt u in staat gegevens op te halen uit een JSONP-service of een webservice die JSON-gegevens retourneert. Voor deze opslagkandidaat, gebruik de opslagconfiguratie om details over de dienst te verstrekken JSONP aan gebruik.

De functie [init](contexthub-api.md#init-name-config) van de Javascript-klasse `ContextHub.Store.JSONPStore` definieert een `config`-object dat deze opslagkandidaat initialiseert. Het `config`-object bevat een `service`-object dat details over de JSONP-service bevat. Om de opslag te vormen, verstrekt u het `service` voorwerp in formaat JSON als waarde voor het bezit van de Configuratie van het Detail.

Om gegevens van de MD5 dienst van de plaats op te slaan jsontest.com, gebruik de procedure in [Creërend een Winkel ContextHub](#creating-a-contexthub-store) gebruikend de volgende eigenschappen:

* **Configuratitel:** md5
* **Winkeltype:** contexthub.generic-jsonp
* **Vereist:** Selecteren
* **Ingeschakeld:** Selecteren
* **Detailconfiguratie (JSON):**

   ```javascript
   {
    "service": {
    "jsonp": false,
    "timeout": 1000,
    "ttl": 1800000,
    "secure": false,
    "host": "md5.jsontest.com",
    "port": 80,
    "params":{
    "text":"text to md5"
        }
      }
    }
   ```

### Een UI-module toevoegen voor de md5-gegevens {#adding-a-ui-module-for-the-md-data}

Voeg een module UI aan de toolbar ContextHub toe om de gegevens te tonen die in het voorbeeld md5 opslag wordt opgeslagen. In dit voorbeeld wordt de module contexthub.base gebruikt om de volgende UI-module te produceren:

![ContextHub MD5-archief](assets/contexthub-md5-store.png)

Gebruik de procedure in [Toevoegend een Module UI](#adding-a-ui-module) om de module UI aan een bestaande Wijze UI, zoals de wijze van de steekproef toe te voegen Persona UI. Voor de Module UI, gebruik de volgende bezitswaarden:

* **Titel van UI-module:** MD5
* **Moduletype:** contexthub.base
* **Detailconfiguratie (JSON):**

   ```javascript
   {
    "icon": "coral-Icon--data",
    "title": "MD5 Conversion",
    "storeMapping": { "md5": "md5" },
    "template": "<p> {{md5.original}}</p>;
                 <p>{{md5.md5}}</p>"
   }
   ```

## Foutopsporing in ContextHub {#debugging-contexthub}

Een het zuiveren wijze voor ContextHub kan worden toegelaten om voor het oplossen van problemen toe te staan. Zuiver wijze kan of door de configuratie ContextHub of via CRXDE worden toegelaten.

### Via de configuratie {#via-the-configuration}

Bewerk de configuratie van ContextHub en controleer de optie **Debug**

1. Klik of tik **Gereedschappen > Sites > ContextHub**
1. Klik of tik het gebrek **Container van de Configuratie**
1. Selecteer **ContextHub Configuration** en klik of tik **Geselecteerd Element** bewerken
1. Klik of tik **Foutopsporing** en klik of tik **Opslaan**

### Via CRXDE {#via-crxde}

Gebruik CRXDE Lite om de eigenschap `debug` in te stellen op **true** onder:

* `/conf/global/settings/cloudsettings` or
* `/conf/<site>/settings/cloudsettings`

### Het registreren zuivert Berichten voor ContextHub {#logging-debug-messages-for-contexthub}

Vorm de dienst van ContextHub OSGi van Adobe Granite (PID = `com.adobe.granite.contexthub.impl.ContextHubImpl`) om gedetailleerde Debug berichten te registreren die wanneer het ontwikkelen nuttig zijn.

Om de dienst te vormen kunt u of [Webconsole](/help/implementing/deploying/configuring-osgi.md) gebruiken of een knoop JCR in de bewaarplaats gebruiken:

* Webconsole: Om te registreren zuivert berichten, selecteer het Debug bezit.
* JCR-knooppunt: Als u Foutopsporingsberichten wilt registreren, stelt u de Booleaanse eigenschap `com.adobe.granite.contexthub.debug` in op `true`.

### Stille modus {#silent-mode}

In de modus Stil worden alle foutopsporingsgegevens onderdrukt. In tegenstelling tot normale zuiveren optie, die onafhankelijk voor elke configuratie kan worden geplaatst ContextHub, is de stille wijze het globale plaatsen die precedent over om het even welke neemt zuiveren montages op het ContextHub configuratieniveau.

Dit is nuttig voor uw publicatie-instantie, waar u helemaal geen foutopsporingsinformatie wilt. Omdat het een globaal plaatsen is, wordt het toegelaten via OSGi.

1. Open **Adobe Experience Manager Web Console Configuration** op `http://<host>:<port>/system/console/configMgr`
1. Zoeken naar **Adobe granite ContextHub**
1. Klik de configuratie **Adobe granite ContextHub** om zijn eigenschappen uit te geven
1. Schakel de optie **Stille modus** in en klik op **Opslaan**

## ContextHub {#disabling-contexthub} uitschakelen

ContextHub kan worden onbruikbaar gemaakt om het te verhinderen js/css te laden en te initialiseren. Er zijn twee opties om ContextHub onbruikbaar te maken:

* Bewerk de configuratie van ContextHub en controleer de optie **Disable ContextHub**

   1. Klik of tik **Gereedschappen > Sites > ContextHub**
   1. Klik of tik het gebrek **Container van de Configuratie**
   1. Selecteer **ContextHub Configuration** en klik of tik **Geselecteerd Element** bewerken
   1. Klik of tik **Schakel ContextHub** uit en klik of tik **Save**

or

* Gebruik CRXDE Lite om de eigenschap `disabled` in te stellen op **true** onder `/conf/global/settings/cloudsettings/<configName>/contexthub`
