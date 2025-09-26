---
title: Aangepaste functies maken en toevoegen in een adaptief formulier
description: AEM Forms ondersteunt aangepaste functies, waarmee gebruikers hun eigen functies in de regeleditor kunnen maken en gebruiken.
keywords: Voeg een douanefunctie toe, gebruik een douanefunctie, creeer een douanefunctie, gebruik douanefunctie in regel redacteur.
feature: Adaptive Forms, Core Components
role: User, Developer
exl-id: e7ab4233-2e91-45c6-9377-0c9204d03ee9
source-git-commit: f772a193cce35a1054f5c6671557a6ec511671a9
workflow-type: tm+mt
source-wordcount: '1349'
ht-degree: 0%

---

# Een aangepaste functie maken voor een adaptief formulier op basis van kerncomponenten

Adaptieve Forms op basis van Core Components biedt een dynamische gebruikerservaring door de inhoud en het gedrag aan te passen op basis van de gebruikersinvoer. Met aangepaste functies kunnen ontwikkelaars hun functionaliteit uitbreiden, zodat formulieren aan specifieke vereisten voldoen. Door douanefuncties te integreren, kunnen de ontwikkelaars complexe logica uitvoeren, processen automatiseren, en unieke interactie introduceren die zich op specifieke bedrijfsvereisten of gebruikersverwachtingen richten. Het zorgt ervoor dat de formulieren niet alleen worden aangepast aan uiteenlopende omstandigheden, maar ook een preciezere en effectievere oplossing bieden voor verschillende gebruiksgevallen.
Dit artikel begeleidt u door de stappen voor het maken van aangepaste functies voor Adaptive Forms met behulp van kerncomponenten.

## Overwegingen

* De `parameter type` en `return type` bieden geen ondersteuning voor `None` .

* De functies die niet worden ondersteund in de lijst met aangepaste functies zijn:
   * Generatorfuncties
   * Functies Async/Await
   * Methodedefinities
   * Methoden van Class
   * Standaardparameters
   * Rustparameters

* De nieuwste ECMAScript-functies zijn beschikbaar als Early Access (EA), terwijl ECMAScript 2019 in het algemeen beschikbaar is.

## Vereisten om een aangepaste functie te maken

Voordat u een aangepaste functie toevoegt aan de Adaptive Forms, moet u het volgende doen:

**Software:**

* **Onbewerkte Redacteur van de Tekst (winde)**: Terwijl om het even welke duidelijke tekstredacteur kan werken, biedt een Geïntegreerde Milieu van de Ontwikkeling (winde) zoals de Code van Microsoft Visual Studio geavanceerde eigenschappen voor het gemakkelijkere uitgeven aan.

* **Git:** Dit systeem van de versiecontrole wordt vereist voor het beheren van codeveranderingen. Als u deze niet hebt geïnstalleerd, kunt u deze downloaden van https://git-scm.com.


## Een aangepaste functie maken

Creeer een cliëntbibliotheek om douanefuncties in de regelredacteur te roepen. Voor meer informatie, zie [ Gebruikend cliënt-Kant Bibliotheken ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/full-stack/clientlibs.html?lang=nl-NL#developing).

Stappen voor het maken van aangepaste functies zijn:

1. [Een clientbibliotheek maken](#create-client-library)
1. [Clientbibliotheek toevoegen aan een adaptief formulier](#use-custom-function)

### Een clientbibliotheek maken {#create-client-library}

U kunt aangepaste functies toevoegen door een clientbibliotheek toe te voegen. Voer de volgende stappen uit om een clientbibliotheek te maken:

**Kloon de Bewaarplaats**

Kloon uw [ Bewaarplaats van AEM Forms as a Cloud Service ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=nl-NL#accessing-git):

1. Open de opdrachtregel of het terminalvenster.

1. Navigeer naar de gewenste locatie op uw computer waar u de opslagplaats wilt opslaan.

1. Voer de volgende opdracht uit om de gegevensopslagruimte te klonen:

   `git clone [Git Repository URL]`

Met deze opdracht downloadt u de opslagplaats en maakt u een lokale map van de gekloonde opslagplaats op uw computer. Door deze gids, verwijzen wij naar deze omslag als [ AEMaaCS projectfolder ].

**voeg een Omslag van de Bibliotheek van de Cliënt toe**

Om nieuwe omslag van de cliëntbibliotheek aan de [ AEMaaCS projectfolder ] toe te voegen, volg deze stappen:

1. Open de [ AEMaaCS projectfolder ] in een redacteur.

   ![ de omslagstructuur van de douanefunctie ](/help/forms/assets/custom-library-folder-structure.png)

1. Zoek `ui.apps` .
1. Nieuwe map toevoegen. Voeg bijvoorbeeld een map toe met de naam `experience-league` .
1. Navigeer naar de map `/experience-league/` en voeg een `ClientLibraryFolder` toe. Maak bijvoorbeeld een clientbibliotheekmap met de naam `customclientlibs` .

   `Location is: [AEMaaCS project directory]/ui.apps/src/main/content/jcr_root/apps/`

**voegt dossiers en omslagen aan de omslag van de Bibliotheek van de Cliënt toe**

Voeg het volgende toe aan de toegevoegde omslag van de cliëntbibliotheek:

* .content.xml, bestand
* js.txt, bestand
* map js

`Location is: [AEMaaCS project directory]/ui.apps/src/main/content/jcr_root/apps/experience-league/customclientlibs/`

1. Voeg in `.content.xml` de volgende coderegels toe:

   ```javascript
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:cq="http://www.day.com/jcr/cq/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0"
   jcr:primaryType="cq:ClientLibraryFolder"
   categories="[customfunctionscategory]"/>
   ```

   >[!NOTE]
   >
   > U kunt een willekeurige naam kiezen voor de eigenschappen `client library folder` en `categories` .

1. Voeg in `js.txt` de volgende coderegels toe:

   ```javascript
         #base=js
       function.js
   ```

1. Voeg in de map `js` het javascript-bestand toe als `function.js` dat de aangepaste functies bevat:

   ```javascript
    /**
        * Calculates Age
        * @name calculateAge
        * @param {object} field
        * @return {string} 
    */
   
    function calculateAge(field) {
    var dob = new Date(field);
    var now = new Date();
   
    var age = now.getFullYear() - dob.getFullYear();
    var monthDiff = now.getMonth() - dob.getMonth();
   
    if (monthDiff < 0 || (monthDiff === 0 && now.getDate() < dob.getDate())) {
    age--;
    }
   
    return age;
    }
   ```

1. Sla de bestanden op.

![ de omslagstructuur van de douanefunctie ](/help/forms/assets/custom-function-added-files.png)

**omvat de nieuwe omslag in filter.xml**:

1. Navigeer aan het `/ui.apps/src/main/content/META-INF/vault/filter.xml` dossier in uw [ AEMaaCS projectfolder ].

2. Open het bestand en voeg de volgende regel aan het einde toe:

   `<filter root="/apps/experience-league" />`
3. Sla het bestand op.

![ de filter xml van de douanefunctie &lbrace;](/help/forms/assets/custom-function-filterxml.png)

**stel de pas gecreëerde de bibliotheekomslag van de Cliënt aan uw milieu van AEM** op

Stel AEM as a Cloud Service, [ AEMaaCS projectfolder ], aan uw milieu van Cloud Service op. Distribueren naar uw Cloud Service-omgeving:

1. De wijzigingen vastleggen

   1. U kunt de wijzigingen in de opslagplaats toevoegen, vastleggen en doorvoeren met behulp van de onderstaande opdrachten:

   ```javascript
       git add .
       git commit -a -m "Adding custom functions"
       git push
   ```

1. De bijgewerkte code implementeren:

   1. Trigger een plaatsing van uw code door de bestaande full-stack pijpleiding. Hiermee wordt de bijgewerkte code automatisch samengesteld en geïmplementeerd.

Als u niet reeds opstelling een pijpleiding hebt, verwijs naar de gids op [ hoe te opstelling een pijpleiding voor AEM Forms as a Cloud Service ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=nl-NL#setup-pipeline).

Zodra de pijpleiding met succes wordt uitgevoerd, wordt de douanefunctie die in de cliëntbibliotheek wordt toegevoegd beschikbaar in uw [ Aangepaste redacteur van de Regel van de Vorm ](/help/forms/rule-editor-core-components.md).

### Clientbibliotheek toevoegen aan een adaptief formulier{#use-custom-function}

Zodra u de clientbibliotheek hebt geïmplementeerd in uw Forms CS-omgeving, gebruikt u de mogelijkheden van de clientbibliotheek in uw adaptieve formulier. De clientbibliotheek toevoegen aan uw adaptieve formulier

1. Open het formulier in de bewerkingsmodus. Als u een formulier wilt openen in de bewerkingsmodus, selecteert u een formulier en selecteert u **[!UICONTROL Edit]** .
1. Open de browser Inhoud en selecteer de component **[!UICONTROL Guide Container]** van het adaptieve formulier.
1. Klik de eigenschappen van de Container van de Gids ![ eigenschappen van de Gids ](/help/forms/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer wordt geopend.
1. Open het tabblad **[!UICONTROL Basic]** en selecteer de naam van de **[!UICONTROL client library category]** in de vervolgkeuzelijst (in dit geval selecteert u `customfunctionscategory` ).

   ![ Toevoegend de de cliëntbibliotheek van de douanefunctie ](/help/forms/assets/clientlib-custom-function.png)

   >[!NOTE]
   >
   > U kunt meerdere categorieën toevoegen door een door komma&#39;s gescheiden lijst op te geven in het veld **[!UICONTROL Client library category]** .

1. Klik op **[!UICONTROL Done]**.

U kunt de douanefunctie in de [ regelredacteur van een Aangepaste Vorm ](/help/forms/rule-editor-core-components.md) gebruiken gebruikend de [ annotaties van JavaScript ](##js-annotations).

## Een aangepaste functie gebruiken in een adaptief formulier

In een AanpassingsVorm, kunt u [ douanefuncties binnen de regelredacteur ](/help/forms/rule-editor-core-components.md) gebruiken. Voeg de volgende code toe aan het JavaScript-bestand (`Function.js` ) om de leeftijd te berekenen op basis van de geboortedatum (JJJJ-MM-DD). Maak een aangepaste functie als `calculateAge()` die de geboortedatum als invoer neemt en de leeftijd retourneert:

```javascript
    /**
        * Calculates Age
        * @name calculateAge
        * @param {object} field
        * @return {string} 
    */

    function calculateAge(field) {
    var dob = new Date(field);
    var now = new Date();

    var age = now.getFullYear() - dob.getFullYear();
    var monthDiff = now.getMonth() - dob.getMonth();

    if (monthDiff < 0 || (monthDiff === 0 && now.getDate() < dob.getDate())) {
    age--;
    }

    return age;
    }
```

In het bovenstaande voorbeeld wordt de aangepaste functie `calculateAge` aangeroepen en wordt de leeftijd geretourneerd wanneer de gebruiker de geboortedatum in de notatie invoert (JJJJ-MM-DD).

![ Calcualte tegen douanefunctie in de Redacteur van de Regel ](/help/forms/assets/custom-function-calculate-age.png)

Bekijk een voorbeeld van het formulier om te zien hoe de aangepaste functies worden geïmplementeerd via de regeleditor:

![ berekent tegen douanefunctie in de Voorproef van de Vorm van de Redacteur van de Regel ](/help/forms/assets/custom-function-age-calculate-form.png)

>[!NOTE]
>
> U kunt naar de volgende [ omslag van de douanefunctie ](/help/forms/assets//customfunctions.zip) verwijzen. Download en installeer deze omslag in uw instantie van AEM gebruikend de [ Manager van het Pakket ](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/implementing/developer-tools/package-manager).

## Functies van Aangepaste functies

Aangepaste functies in AEM-formulieren bieden een robuuste oplossing voor het uitbreiden en aanpassen van de functionaliteit van uw formulieren. U kunt de aangepaste functies gebruiken om aan de specifieke behoeften van uw organisatie te voldoen.

Deze functies ondersteunen diverse mogelijkheden, zoals het werken met specifieke gebieden, het gebruiken van globale gebieden, en asynchrone verrichtingen, evenals het opnemen van caching mechanismen. Dankzij deze flexibiliteit kunnen formulieren zich aanpassen aan complexe vereisten en een efficiënte, op maat gemaakte gebruikerservaring bieden. Door gebruik te maken van deze geavanceerde functies kunt u de interactie van formulieren verbeteren en de prestaties optimaliseren, zodat uw AEM-formulieren zowel functioneler als responsiever worden.

Laten we eens kijken naar de functies van aangepaste functies.

### Asynchrone ondersteuning in aangepaste functies {#support-of-async-functions}

U kunt asynchrone functies in de regelredacteur uitvoeren gebruikend douanefuncties. Voor begeleiding op hoe te om dit te doen, verwijs naar het artikel [ Gebruikend asynchrone functies in een AanpassingsVorm ](/help/forms/using-async-funct-in-rule-editor.md).

### Veld- en globale bereikobjecten ondersteunen aangepaste functies {#support-field-and-global-objects}

Veldobjecten verwijzen naar de afzonderlijke componenten of elementen in een formulier, zoals tekstvelden, selectievakjes. Het object Globals bevat alleen-lezen variabelen, zoals formulierinstantie, doelveldinstantie en methoden voor het uitvoeren van formulierwijzigingen binnen aangepaste functies.

>[!NOTE]
>
> `param {scope} globals` moet de laatste parameter zijn en wordt niet weergegeven in de regeleditor van een adaptief formulier.

Voor meer informatie over werkingsgebiedvoorwerpen, zie de [ voorwerpen van het Toepassingsgebied in douanefuncties ](/help/forms/custom-function-core-component-scope-function.md) artikel.

### Ondersteuning voor caching in aangepaste functies

De adaptieve Forms voert caching voor douanefuncties uit om reactietijd te verbeteren terwijl het terugwinnen van de lijst van de douanefunctie in de regelredacteur. Er verschijnt een bericht als `Fetched following custom functions list from cache` in het `error.log` -bestand.

![ douanefunctie met geheim voorgeheugensteun ](/help/forms/assets/custom-function-cache-error.png)

Als de aangepaste functies worden gewijzigd, wordt het in cache plaatsen ongeldig en wordt het geparseerd.

## Problemen oplossen

* Als het JavaScript-bestand met code voor aangepaste functies een fout bevat, worden de aangepaste functies niet vermeld in de regeleditor van een adaptief formulier. Als u de lijst met aangepaste functies wilt controleren, navigeert u naar het `error.log` -bestand voor de fout. In het geval van een fout wordt de lijst met aangepaste functies leeg weergegeven:

  ![ dossier van het foutenlogboek ](/help/forms/assets/custom-function-list-error-file.png)

  Als er geen fout optreedt, wordt de aangepaste functie opgehaald en in het `error.log` -bestand weergegeven. Er verschijnt een bericht als `Fetched following custom functions list` in het `error.log` -bestand:

  ![ dossier van het foutenlogboek met juiste douanefunctie ](/help/forms/assets/custom-function-list-fetched-in-error.png)

## Volgende stap

Laat ons nu diverse [ voorbeelden van douanefuncties voor een Aangepaste Vorm zien die op de Componenten van de Kern ](/help/forms/custom-function-core-components-use-cases.md) wordt gebaseerd.

## Zie ook

{{see-also-rule-editor}}
