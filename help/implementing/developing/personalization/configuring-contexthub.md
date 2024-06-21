---
title: ContextHub configureren
description: Leer hoe te om de Hub van de Context, een kader te vormen om, contextgegevens op te slaan te manipuleren en voor te stellen.
exl-id: 1fd7d41e-31ad-4838-8749-a5791edcfd63
feature: Developing, Personalization
role: Admin, Architect, Developer
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '1609'
ht-degree: 0%

---

# ContextHub configureren {#configuring-contexthub}

ContextHub is een kader voor het opslaan van, het manipuleren van, en het voorstellen van contextgegevens. Voor meer details op ContextHub, zie [Overzicht van ContextHub-ontwikkelaars](contexthub.md).

U kunt de toolbar vormen ContextHub om te controleren of het op de wijze van de Voorproef verschijnt, om opslag te creëren ContextHub, en modules toe te voegen UI.

## Het tonen van en het Verbergen van ContextHub UI {#showing-and-hiding-the-contexthub-ui}

Vorm de dienst van ContextHub OSGi van Granite van de Adobe om te tonen of te verbergen [ContextHub UI](/help/sites-cloud/authoring/personalization/targeted-content.md) op uw pagina&#39;s. De PID van deze service is `com.adobe.granite.contexthub.impl.ContextHubImpl.`

Om de dienst te vormen kunt u of gebruiken [Webconsole](/help/implementing/deploying/configuring-osgi.md) of gebruik een JCR-knooppunt in de repository:

* **Webconsole:** Om UI te tonen, selecteer het bezit UI van de Show. Om UI te verbergen, ontruim het bezit UI van de Huid.
* **JCR-knooppunt:** Om UI te tonen, plaats boolean `com.adobe.granite.contexthub.show_ui` eigenschap aan `true`. Als u de gebruikersinterface wilt verbergen, stelt u de eigenschap in op `false`.

Wanneer het tonen van ContextHub UI, verschijnt het slechts op pagina&#39;s op AEM auteursinstanties. De interface wordt niet weergegeven op pagina&#39;s met publicatie-instanties.

## ContextHub UI-modi en modules toevoegen {#adding-contexthub-ui-modes-and-modules}

Vorm de wijzen UI en de modules die op de toolbar ContextHub op de wijze van de Voorproef verschijnen:

* UI-modi: Groepen gerelateerde modules
* Modules: widgets die contextgegevens uit een winkel beschikbaar maken en auteurs in staat stellen de context te manipuleren

UI-modi worden als een reeks pictogrammen aan de linkerkant van de werkbalk weergegeven. Wanneer geselecteerd, verschijnen de modules van een wijze UI aan het recht.

![ContextHub-werkbalk](assets/contexthub-toolbar.png)

Pictogrammen zijn verwijzingen uit de [Pictogrambibliotheek van Koral UI](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/coral-ui/coralui3/Coral.Icon.html#availableIcons).

### UI-modus toevoegen {#adding-a-ui-mode}

Voeg een wijze UI aan groep verwante modules ContextHub toe. Wanneer u de wijze UI creeert, verstrekt u de titel en het pictogram die in de toolbar ContextHub verschijnen.

1. Selecteer Extra > Sites > Context Hub in de Experience Manager.
1. Selecteer de standaardcontainer van de Configuratie.
1. Selecteer de Configuratie van de Hub van de Context.
1. Selecteer de Create knoop, en selecteer dan de Wijze UI van de Hub van de Context.

   ![UI-modus toevoegen](assets/contexthub-ui-mode.png)

1. Geef waarden op voor de volgende eigenschappen:

   * UI Mode Title: The title that identify the UI mode
   * Pictogram Modus: De kiezer voor de [Pictogram Koraalinterface](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/coral-ui/coralui3/Coral.Icon.html#availableIcons) bijvoorbeeld `coral-Icon--user`
   * Toegelaten: Uitgezocht om de wijze UI op de toolbar te tonen ContextHub

1. Selecteer Opslaan.

### Een UI-module toevoegen {#adding-a-ui-module}

Voeg een module ContextHub UI aan een wijze UI toe zodat het in de toolbar ContextHub voor het voorvertonen van paginainhoud verschijnt. Wanneer u een module UI toevoegt, creeert u een geval van een moduletype dat met ContextHub wordt geregistreerd. Om een module UI toe te voegen, moet u de naam van het bijbehorende moduletype kennen.

AEM verstrekt een moduletype van basisUI evenals verscheidene types van steekproefUI Module waarop u een module UI kunt baseren. In de volgende tabel vindt u een korte beschrijving van elke tabel. Voor informatie over het ontwikkelen van een module van douaneUI, zie [ContextHub UI-modules maken](extending-contexthub.md#creating-contexthub-ui-module-types).

De eigenschappen van de module UI omvatten een detailconfiguratie waar u waarden voor module-specifieke eigenschappen kunt verstrekken. U verstrekt de detailconfiguratie in formaat JSON. De kolom van het Type van Module in de lijst verstrekt verbindingen aan informatie over de code JSON die voor elk UI moduletype wordt vereist.

| Moduletype | Beschrijving | Winkel |
|---|---|---|
| [contexthub.base](sample-modules.md#contexthub-base-ui-module-type) | Een generiek type UI-module | Gevormd in de eigenschappen van de UI module |
| [contexthub.browserinfo](sample-modules.md#contexthub-browserinfo-ui-module-type) | Hiermee wordt informatie over de browser weergegeven | `surferinfo` |
| [contexthub.datetime](sample-modules.md#contexthub-datetime-ui-module-type) | Datum- en tijdgegevens weergeven | `datetime` |
| [contexthub.location](sample-modules.md#contexthub-location-ui-module-type) | Geeft de breedte en lengte van de client en de locatie op een kaart weer. Hiermee kunt u de locatie wijzigen. | `geolocation` |
| [contexthub.screen-orientation](sample-modules.md#contexthub-screen-orientation-ui-module-type) | Geeft de schermstand van het apparaat (liggend of staand) weer | `emulators` |
| [contexthub.tagcloud](sample-modules.md#contexthub-tagcloud-ui-module-type) | Statistieken over paginatags weergeven | `tagcloud` |
| [graniet.profile](sample-modules.md#granite-profile-ui-module-type) | Hiermee geeft u de profielgegevens voor de huidige gebruiker weer, inclusief `authorizableID`, `displayName` en `familyName`. U kunt de waarde wijzigen van `displayName` en `familyName`. | `profile` |

1. Selecteer Extra > Sites > ContextHub in de Experience Manager.
1. Selecteer de Container van de Configuratie waaraan u een module UI wilt toevoegen.
1. Selecteer of typ de Configuratie ContextHub waaraan u de module UI wilt toevoegen.
1. Selecteer de wijze UI waaraan u de module UI toevoegt.
1. Selecteer de Create knoop, dan uitgezochte Module ContextHub UI (algemeen).

   ![De module ContextHub UI](assets/contexthub-ui-module.png)

1. Geef waarden op voor de volgende eigenschappen:

   * UI Module Title: Een titel die de UI module identificeert
   * Moduletype: het moduletype
   * Toegelaten: Uitgezocht om de module UI in de toolbar te tonen ContextHub

1. (Optioneel) Als u de standaardwinkelconfiguratie wilt overschrijven, voert u een JSON-object in om de UI-module te configureren.
1. Selecteer Opslaan.

## Een ContextHub-winkel maken {#creating-a-contexthub-store}

Creeer een opslag van de Hub van de Context om gebruikersgegevens en toegang tot de gegevens voort te zetten zoals nodig. ContextHub-winkels zijn gebaseerd op geregistreerde winkelkandidaten. Wanneer u de opslag creeert, hebt u de waarde van storeType nodig waarmee de opslagkandidaat werd geregistreerd. (Zie [Aangepaste winkelkandidaten maken](extending-contexthub.md#creating-custom-store-candidates).)

### Gedetailleerde opslagconfiguratie {#detailed-store-configuration}

Wanneer u een opslag vormt, laat het bezit van de Configuratie van het Detail u toe om waarden voor store-specific eigenschappen te verstrekken. De waarde is gebaseerd op de `config` parameter van de opslag `init` functie. Daarom of u deze waarde, en het formaat van de waarde moet verstrekken, hangt van de opslag af.

De waarde van het bezit van de Configuratie van het Detail is een `config` object in JSON-indeling.

### Voorbeeld van winkelkandidaten {#sample-store-candidates}

AEM verstrekt de volgende kandidaten van de steekproefopslag waarop u een opslag kunt baseren.

| Winkeltype | Beschrijving |
|---|---|
| [aem.segmentation](sample-stores.md#aem-segmentation-sample-store-candidate) | Bewaren voor opgeloste en onopgeloste segmenten ContextHub. Wint automatisch segmenten van ContextHub SegmentManager terug |
| [contexthub.geolocation](sample-stores.md#contexthub-geolocation-sample-store-candidate) | Hiermee slaat u de breedte en lengte van de browserlocatie op. |
| [graniet.emulators](sample-stores.md#granite-emulators-sample-store-candidate) | Definieert eigenschappen en mogelijkheden voor verschillende apparaten en detecteert het huidige clientapparaat |
| [graniet.profile](sample-stores.md#granite-profile-sample-store-candidate) | Hiermee worden profielgegevens voor de huidige gebruiker opgeslagen |
| [contexthub.surferinfo](sample-stores.md#contexthub-surferinfo-sample-store-candidate) | Hiermee wordt informatie over de client opgeslagen, zoals apparaatinformatie, browsertype en vensterrichting |

1. Selecteer Extra > Sites > ContextHub in de Experience Manager.
1. Selecteer de standaardconfiguratiecontainer.
1. Contexthub-configuratie selecteren
1. Om een opslag toe te voegen, selecteer het Create pictogram en selecteer dan Configuratie van de Winkel ContextHub.

   ![Configuratie van ContextHub-store](assets/contexthub-store-configuration.png)

1. Geef waarden op voor de basisconfiguratie-eigenschappen en selecteer Volgende:

   * **Configuratitel:** De titel die de winkel identificeert
   * **Winkeltype:** De waarde van het storeType bezit van de opslagkandidaat waarop om de opslag te baseren
   * **Vereist:** Selecteren
   * **Ingeschakeld:** Selecteren om de winkel in te schakelen

1. (Optioneel) Als u de standaardopslagconfiguratie wilt overschrijven, voert u een JSON-object in het vak Detail Configuration (JSON) in.
1. Selecteer Opslaan.

## Voorbeeld: een JSONP-service gebruiken  {#example-using-a-jsonp-service}

Dit voorbeeld illustreert hoe te om een opslag te vormen en de gegevens in een module UI te tonen. In dit voorbeeld wordt de MD5-service van de site jsontest.com gebruikt als gegevensbron voor een winkel. De service retourneert de MD5-hash-code van een tekenreeks in JSON-indeling.

Een contexthub.generic-jsonp-opslag is geconfigureerd zodat deze gegevens opslaat voor de serviceaanroep `https://md5.jsontest.com/?text=%22text%20to%20md5%22`. De dienst keert de volgende gegevens terug die in een module UI worden getoond:

```javascript
{
   "md5": "919a56ab62b6d5e1219fe1d95248a2c5",
   "original": "\"text to md5\""
}
```

### Een contexthub.generic-jsonp Store maken {#creating-a-contexthub-generic-jsonp-store}

De contextthub.generic-jsonp-voorbeeldopslagkandidaat stelt u in staat gegevens op te halen uit een JSONP-service of een webservice die JSON-gegevens retourneert. Voor deze opslagkandidaat, gebruik de opslagconfiguratie om details over de dienst te verstrekken JSONP aan gebruik.

De [init](contexthub-api.md#init-name-config) de functie van de `ContextHub.Store.JSONPStore` JavaScript-klasse definieert een `config` object dat deze winkelkandidaat initialiseert. De `config` object bevat een `service` object dat details over de JSONP-service bevat. Om de opslag te vormen, verstrekt u `service` object in JSON-indeling als de waarde voor de eigenschap Detail Configuration.

Als u gegevens wilt opslaan van de MD5-service van de site jsontest.com, gebruikt u de procedure in [Een ContextHub-winkel maken](#creating-a-contexthub-store) de volgende eigenschappen gebruiken:

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

Gebruik de procedure in [Een UI-module toevoegen](#adding-a-ui-module) om de module UI aan een bestaande Wijze UI, zoals de wijze van de steekproef toe te voegen Persona UI. Voor de Module UI, gebruik de volgende bezitswaarden:

* **UI-moduletitel:** MD5
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

Bewerk de configuratie van ContextHub en controleer de optie **Foutopsporing**

1. Selecteer in het vak **Extra > Sites > ContextHub**
1. De standaardinstelling selecteren **Configuratie-container**
1. Selecteer de **ContextHub-configuratie** en selecteert u **Geselecteerd element bewerken**
1. Selecteren **Foutopsporing** en selecteert u **Opslaan**

### Via CRXDE {#via-crxde}

CRXDE Lite gebruiken om de eigenschap in te stellen `debug` tot **true** onder:

* `/conf/global/settings/cloudsettings` of
* `/conf/<site>/settings/cloudsettings`

### Het registreren zuivert Berichten voor ContextHub {#logging-debug-messages-for-contexthub}

Vorm de Dienst van ContextHub OSGi van de Adobe Granite (PID = `com.adobe.granite.contexthub.impl.ContextHubImpl`) om gedetailleerde Debug berichten te registreren die wanneer het ontwikkelen nuttig zijn.

Om de dienst te vormen kunt u of gebruiken [Webconsole](/help/implementing/deploying/configuring-osgi.md) of gebruik een JCR-knooppunt in de repository:

* Webconsole: Als u Foutopsporingsberichten wilt registreren, selecteert u de eigenschap Foutopsporing.
* JCR-knooppunt: als u foutopsporingsberichten wilt registreren, stelt u de Boolean in `com.adobe.granite.contexthub.debug` eigenschap aan `true`.

### Stille modus {#silent-mode}

In de modus Stil worden alle foutopsporingsgegevens onderdrukt. In tegenstelling tot normale zuiveren optie, die onafhankelijk voor elke configuratie kan worden geplaatst ContextHub, is de stille wijze het globale plaatsen die precedent over om het even welke neemt zuiveren montages op het ContextHub configuratieniveau.

Dit is nuttig voor uw publicatie-instantie, waar u helemaal geen foutopsporingsinformatie wilt. Omdat het een globaal plaatsen is, wordt het toegelaten via OSGi.

1. Open de **Configuratie Adobe Experience Manager-webconsole** om `http://<host>:<port>/system/console/configMgr`
1. Zoeken naar **ContextHub met Adobe graniet**
1. Klik op de configuratie **ContextHub met Adobe graniet** om de eigenschappen te bewerken
1. Schakel de optie in **Stille modus** en klik op **Opslaan**

## ContextHub uitschakelen {#disabling-contexthub}

ContextHub kan worden onbruikbaar gemaakt om het te verhinderen js/css te laden en te initialiseren. Er zijn twee opties om ContextHub onbruikbaar te maken:

* Bewerk de configuratie van ContextHub en controleer de optie **ContextHub uitschakelen**

   1. Selecteer in het vak **Extra > Sites > ContextHub**
   1. De standaardinstelling selecteren **Configuratie-container**
   1. Selecteer de **ContextHub-configuratie** en selecteert u **Geselecteerd element bewerken**
   1. Selecteren **ContextHub uitschakelen** en selecteert u **Opslaan**

of

* CRXDE Lite gebruiken om de eigenschap in te stellen `disabled` tot **true** krachtens `/conf/global/settings/cloudsettings/<configName>/contexthub`
