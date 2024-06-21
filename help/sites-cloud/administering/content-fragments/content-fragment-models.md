---
title: Modellen van inhoudsfragmenten
description: Leer hoe de Modellen van het Fragment van de Inhoud als basis voor uw Fragmenten van de Inhoud in AEM dienen, toestaand u om gestructureerde inhoud voor gebruik in hoofdloze levering, of paginaontwerp tot stand te brengen.
feature: Content Fragments
role: User, Developer, Architect
exl-id: 8ab5b15f-cefc-45bf-a388-928e8cc8c603
solution: Experience Manager Sites
source-git-commit: f66ea281e6abc373e9704e14c97b77d82c55323b
workflow-type: tm+mt
source-wordcount: '3209'
ht-degree: 1%

---

# Modellen van inhoudsfragmenten {#content-fragment-models}

Met Content Fragment Models in Adobe Experience Manager (AEM) as a Cloud Service wordt de structuur voor de inhoud van uw [Inhoudsfragmenten](/help/sites-cloud/administering/content-fragments/overview.md). Deze fragmenten kunnen vervolgens worden gebruikt voor het ontwerpen van pagina&#39;s of als basis voor inhoud zonder kop.

U kunt als volgt modellen van inhoudsfragmenten gebruiken:

1. [Functionaliteit van inhoudsfragmentmodel inschakelen voor uw instantie](/help/sites-cloud/administering/content-fragments/setup.md)
1. [Maken](#creating-a-content-fragment-model), en [vormen](#defining-your-content-fragment-model), uw modellen van inhoudsfragmenten
1. [Modellen van inhoudsfragmenten inschakelen](#enabling-disabling-a-content-fragment-model) voor gebruik bij het maken van inhoudsfragmenten
1. [Modellen van inhoudsfragmenten toestaan in de vereiste mappen Middelen](#allowing-content-fragment-models-assets-folder) door te vormen **Beleid**.

## Een inhoudsfragmentmodel maken {#creating-a-content-fragment-model}

1. Navigeren naar **Gereedschappen**, **Algemeen** en vervolgens openen **Modellen van inhoudsfragmenten**.
1. Navigeer naar de map die geschikt is voor uw [configuratie of subconfiguratie](/help/sites-cloud/administering/content-fragments/setup.md).
1. Gebruiken **Maken** om de wizard te openen.

   >[!CAUTION]
   >
   >Als de [het gebruik van Content Fragment-modellen is niet ingeschakeld](/help/sites-cloud/administering/content-fragments/setup.md)de **Maken** deze optie is niet beschikbaar.

1. Geef de **Modeltitel**.
U kunt ook verschillende eigenschappen definiëren, bijvoorbeeld **Tags**, **Beschrijving**, selecteert u **Model inschakelen** tot [het model inschakelen](#enabling-disabling-a-content-fragment-model) indien nodig en definieert de
   **URL-standaardvoorvertoningspatroon**.

   >[!NOTE]
   >
   >Zie [Inhoudsfragmentmodel - eigenschappen](#content-fragment-model-properties) voor volledige informatie.

   ![Titel en beschrijving](assets/cf-cfmodels-create.png)

1. Gebruiken **Maken** het lege model opslaan. Een bericht geeft het succes van de handeling aan. U kunt **Openen** het model onmiddellijk te bewerken, of **Gereed** om naar de console terug te keren.

>[!CAUTION]
>
>Als u meerdere fragmenten waarnaar wordt verwezen, wilt opvragen, is het niet aan te raden dat de verschillende fragmentmodellen veldnamen met dezelfde naam hebben, maar verschillende typen.
>
>Zie voor meer informatie [GraphQL API AEM voor gebruik met inhoudsfragmenten - Beperkingen](/help/headless/graphql-api/content-fragments.md#limitations)

### Inhoudsfragmentmodel - eigenschappen {#content-fragment-model-properties}

Deze eigenschappen worden gedefinieerd wanneer u een model maakt en kunnen later worden bewerkt met de opdracht **Eigenschappen** optie voor het inhoudsfragmentmodel:

* **Basis**
   * **Modeltitel**
   * **Tags**
   * **Beschrijving**
   * **Model inschakelen**
   * **URL-standaardvoorvertoningspatroon**
In de Inhoudsfragmenteditor kunnen auteurs **Voorvertoning** hun inhoud in een externe frontend toepassing. Wanneer de **Voorvertoningsservice** wordt gevormd, voeg URL voor de frontend toepassing toe.

     De voorbeeld-URL moet dit patroon volgen:
    `https://<preview_url>?param=${expression}`

     Beschikbare expressies zijn:

      * `${contentFragment.path}`
      * `${contentFragment.model.path}`
      * `${contentFragment.model.name}`
      * `${contentFragment.variation}`
      * `${contentFragment.id}`

   * **Afbeelding uploaden**

<!-- CHECK: currently under FT -->
<!--
* **GraphQL**
  Define names relevant for GraphQL.
  Changing the GraphQL API Name, or Query field names will impact client applications.
  * **API Name**
    Represents the GraphQL type and query field names in the GraphQL schema.
  * **Single Query Field Name**
    Represents the GraphQL single query field name in the GraphQL schema.
  * **Multiple Query Field Name**
    Represents the GraphQL multiple query field name in the GraphQL schema.
-->

## Het model van het inhoudsfragment definiëren {#defining-your-content-fragment-model}

Het inhoudsfragmentmodel definieert effectief de structuur van de resulterende inhoudsfragmenten met een selectie **[Gegevenstypen](#data-types)**. Gebruikend de modelredacteur kunt u instanties van de gegevenstypes toevoegen, dan hen vormen om de vereiste gebieden tot stand te brengen:

>[!CAUTION]
>
>Het bewerken van een model dat al wordt gebruikt door bestaande inhoudsfragmenten kan van invloed zijn op die afhankelijke fragmenten.

1. Navigeren naar **Gereedschappen**, **Algemeen** en vervolgens openen **Modellen van inhoudsfragmenten**.

1. Navigeer naar de map met het model van het inhoudsfragment.
1. Open het vereiste model voor **Bewerken**; gebruik de snelle actie of selecteer het model en vervolgens de actie op de werkbalk.

   Zodra open de modelredacteur toont:

   * links: velden al gedefinieerd
   * rechts: **datatypen** voor het maken van velden (en **eigenschappen** voor gebruik als er velden zijn gemaakt)

   >[!NOTE]
   >
   >Wanneer een veld wordt gedefinieerd als **Vereist** de **Label** aangegeven in het linkerdeelvenster is gemarkeerd met een asterix (**&#42;**).

![Eigenschappen](assets/cf-cfmodels-empty-model.png)

1. **Een veld toevoegen**

   * Sleep een vereist gegevenstype naar de vereiste locatie voor een veld:

     ![Gegevenstype slepen om veld te maken](assets/cf-cfmodels-create-field.png)

   * Nadat een veld aan het model is toegevoegd, wordt in het rechterdeelvenster het volgende weergegeven: **Eigenschappen** die voor dat bepaalde gegevenstype kunnen worden gedefinieerd. Hier kunt u definiëren wat voor dat veld is vereist.

      * Veel eigenschappen zijn niet-verklarend, voor meer details zie [Eigenschappen](#properties).
      * Een **Veldlabel** automatisch voltooit het **Eigenschapnaam**  - indien leeg, en het kan achteraf handmatig worden bijgewerkt.

        >[!CAUTION]
        >
        Wanneer u de eigenschap handmatig bijwerkt **Eigenschapnaam** voor een gegevenstype moeten namen bevatten *alleen* A-Z, a-z, 0-9 en onderstrepingsteken &quot;_&quot; als speciaal teken.
        >
        Als modellen die in eerdere versies van AEM zijn gemaakt, ongeldige tekens bevatten, verwijdert of werkt u die tekens bij.

     Bijvoorbeeld:

     ![Veldeigenschappen](assets/cf-cfmodels-field-properties.png)

1. **Een veld verwijderen**

   Selecteer het vereiste veld en selecteer vervolgens het prullenbakpictogram. U wordt gevraagd de actie te bevestigen.

   ![Verwijderen](assets/cf-cfmodels-remove-icon.png)

1. Voeg alle vereiste velden toe en definieer de bijbehorende eigenschappen, zoals vereist. Bijvoorbeeld:

   ![Opslaan](assets/cf-cfmodels-save.png)

1. Selecteren **Opslaan** om de definitie te handhaven.

## Gegevenstypen {#data-types}

Voor het definiëren van uw model zijn verschillende gegevenstypen beschikbaar:

* **Tekst met één regel**
   * Voeg een of meer velden van één regel tekst toe. De maximumlengte kan worden gedefinieerd
* **Tekst met meerdere regels**
   * Een tekstgebied dat RTF-tekst, platte tekst of Markering kan zijn

  >[!NOTE]
  >
  Of het tekstgebied RTF, Onbewerkte Tekst, of Markdown is wordt bepaald in het model door het bezit **Standaardtype**.
  >
  Deze indeling kan niet worden gewijzigd vanuit het dialoogvenster [Inhoudsfragmenteditor](/help/sites-cloud/administering/content-fragments/authoring.md), maar alleen van het model.

* **Getal**
   * Een of meer numerieke velden toevoegen
* **Boolean**
   * Een Booleaans selectievakje toevoegen
* **Datum en tijd**
   * Een datum en/of tijd toevoegen
* **Opsomming**
   * Een set selectievakjes, keuzerondjes of vervolgkeuzelijstvelden toevoegen
* **Tags**
   * Hiermee kunnen auteurs van fragmenten gebieden met tags openen en selecteren
* **Content Reference**
   * Verwijzingen naar andere inhoud, van elk type; kan worden gebruikt voor [geneste inhoud maken](#using-references-to-form-nested-content)
   * Als er naar een afbeelding wordt verwezen, kunt u ervoor kiezen een miniatuur weer te geven
* **Fragmentverwijzing**
   * Verwijzingen naar andere inhoudsfragmenten; kan worden gebruikt voor [geneste inhoud maken](#using-references-to-form-nested-content)
   * Het gegevenstype kan worden geconfigureerd om fragmentauteurs toe te staan:
      * Bewerk het fragment waarnaar wordt verwezen rechtstreeks.
      * Een nieuw inhoudsfragment maken op basis van het juiste model
* **JSON-object**
   * Hiermee stelt u de auteur van inhoudsfragment in staat JSON-syntaxis in te voeren in de overeenkomende elementen van een fragment.
      * Om AEM toe te staan direct JSON op te slaan die u van een andere dienst hebt gekopieerd/gekleefd.
      * De JSON wordt doorgegeven en uitvoer als JSON in GraphQL.
      * Neemt JSON-syntaxismarkering, automatisch aanvullen en foutmarkering op in de inhoudsfragmenteditor.
* **Tijdelijke aanduiding voor tab**
   * Hiermee kunt u tabbladen invoeren die u kunt gebruiken bij het bewerken van de inhoud van het inhoudsfragment.
      * Deze worden getoond als verdelers in de modelredacteur, scheidend secties van de lijst van inhoudstypes. Elke instantie vertegenwoordigt het begin van een nieuw lusje.
      * In de fragmenteditor wordt elke instantie weergegeven als een tab.

     >[!NOTE]
     >
     Dit gegevenstype wordt alleen gebruikt voor opmaak en wordt genegeerd door het schema AEM GraphQL.

## Eigenschappen {#properties}

Vele eigenschappen zijn voor zichzelf verklarend, voor bepaalde eigenschappen zijn hieronder meer details te vinden:

* **Eigenschapnaam**

  Namen wanneer u deze eigenschap handmatig bijwerkt voor een gegevenstype **moet** bevatten *alleen* A-Z, a-z, 0-9 en onderstrepingsteken &quot;_&quot; als speciaal teken.

  >[!CAUTION]
  >
  Als modellen die in eerdere versies van AEM zijn gemaakt, ongeldige tekens bevatten, verwijdert of werkt u die tekens bij.

* **Renderen als**

  De verschillende opties voor het realiseren/renderen van het veld in een fragment. Hierdoor kunt u vaak definiëren of de auteur één exemplaar van het veld ziet of meerdere exemplaren mag maken. Wanneer **Meerdere velden** wordt gebruikt U kunt het minimum en maximum aantal objecten definiëren - zie [Validatie](#validation) voor nadere bijzonderheden.

* **Veldlabel**
Een **Veldlabel** automatisch een **Eigenschapnaam**, die indien nodig handmatig kan worden bijgewerkt.

* **Validatie**
De basisbevestiging is beschikbaar door mechanismen zoals **Vereist** eigenschap. Sommige gegevenstypen hebben extra validatievelden. Zie [Validatie](#validation) voor nadere bijzonderheden.

* Voor het datatype **Tekst met meerdere regels** is het mogelijk het **standaardtype** als volgt te definiëren:

   * **RTF**
   * **Markering**
   * **Onbewerkte tekst**

  Indien niet opgegeven, wordt de standaardwaarde **RTF** wordt gebruikt voor dit veld.

  Het wijzigen van **Standaardtype** in een model van het Fragment van de Inhoud zal slechts op een bestaand, verwant, tevreden Fragment van kracht worden nadat dat fragment in de redacteur wordt geopend en wordt bewaard.

* **Uniek**
De inhoud (voor het specifieke veld) moet uniek zijn in alle inhoudsfragmenten die op basis van het huidige model zijn gemaakt.

  Dit wordt gebruikt om ervoor te zorgen dat inhoudsauteurs geen inhoud kunnen herhalen die al in een ander fragment van hetzelfde model is toegevoegd.

  Bijvoorbeeld een **Tekst met één regel** veld aangeroepen `Country` in het inhoudsfragmentmodel kan de waarde niet hebben `Japan` in twee afhankelijke inhoudsfragmenten. Er wordt een waarschuwing weergegeven wanneer de tweede instantie wordt geprobeerd.

  >[!NOTE]
  >
  Er wordt gezorgd voor uniformiteit per taalwortel.

  >[!NOTE]
  >
  Variaties kunnen hetzelfde hebben *uniek* waarde als variaties van hetzelfde fragment, maar niet dezelfde waarde als bij variaties van andere fragmenten.

* Zie **[Content Reference](#content-reference)** voor meer details over dat specifieke gegevenstype en zijn eigenschappen.

* Zie **[Fragmentverwijzing (geneste fragmenten)](#fragment-reference-nested-fragments)** voor meer details over dat specifieke gegevenstype en zijn eigenschappen.

* **Vertaalbaar**

  De **Vertaalbaar** Schakel het selectievakje in een veld in de editor van het inhoudsfragmentmodel in:

   * Zorg ervoor dat de eigenschapsnaam van het veld wordt toegevoegd aan de vertaalconfiguratie, context `/content/dam/<sites-configuration>`, indien nog niet aanwezig.
   * Voor GraphQL: stel een `<translatable>` eigenschap in het veld Inhoudsfragment naar `yes`, om GraphQL-queryfilter toe te staan voor JSON-uitvoer met alleen vertaalbare inhoud.

## Validatie {#validation}

Verschillende gegevenstypen bieden nu de mogelijkheid om validatievereisten te definiëren voor het tijdstip waarop inhoud wordt ingevoerd in het resulterende fragment:

* **Tekst met één regel**
   * Vergelijk met een vooraf gedefinieerde regex.
* **Getal**
   * Controleren op specifieke waarden.
* **Content Reference**
   * Testen op specifieke typen inhoud.
   * Er kan alleen worden verwezen naar elementen van een opgegeven bestandsgrootte of kleiner.
   * Er kan alleen worden verwezen naar afbeeldingen met een vooraf gedefinieerde breedte en/of hoogte (in pixels).
* **Fragmentverwijzing**
   * Testen op een specifiek model van een inhoudsfragment.
* **Min. aantal items** / **Max. aantal objecten**

  Velden die zijn gedefinieerd als een **Meerdere velden** (instellen met **Renderen als**) beschikt over de volgende opties:

   * **Min. aantal items**
   * **Max. aantal objecten**

  Deze worden gevalideerd in het dialoogvenster [Inhoudsfragmenteditor](/help/sites-cloud/administering/content-fragments/authoring.md).

## Referenties gebruiken om geneste inhoud te vormen {#using-references-to-form-nested-content}

Inhoudsfragmenten kunnen geneste inhoud vormen met een van de volgende gegevenstypen:

* **[Content Reference](#content-reference)**
   * Verstrekt een eenvoudige verwijzing naar andere inhoud; van om het even welk type.
   * Kan worden geconfigureerd voor een of meerdere verwijzingen (in het resulterende fragment).

* **[Fragmentverwijzing](#fragment-reference-nested-fragments)** (Geneste fragmenten)
   * Verwijzingen naar andere fragmenten, afhankelijk van de opgegeven modellen.
   * Hiermee kunt u gestructureerde gegevens opnemen/ophalen.
     >[!NOTE]
     >
     Deze methode is van bijzonder belang wanneer u gebruikt [Levering van inhoud zonder kop met gebruik van inhoudsfragmenten met GraphQL](/help/sites-cloud/administering/content-fragments/content-delivery-with-graphql.md).
   * Kan worden geconfigureerd voor een of meerdere verwijzingen (in het resulterende fragment).

>[!NOTE]
>
AEM heeft terugkerende bescherming voor:
>
* Inhoudsverwijzingen Dit voorkomt dat de gebruiker een verwijzing naar het huidige fragment toevoegt en kan leiden tot een leeg dialoogvenster van de kiezer voor fragmentverwijzingen.
>
* Fragmentverwijzingen in GraphQL Als u een diepe query maakt die meerdere Content Fragments retourneert waarnaar door elkaar wordt verwezen, retourneert deze null bij de eerste instantie.

>[!CAUTION]
>
Als u meerdere fragmenten waarnaar wordt verwezen, wilt opvragen, is het niet aan te raden dat de verschillende fragmentmodellen veldnamen met dezelfde naam hebben, maar verschillende typen.
>
Zie voor meer informatie [GraphQL API AEM voor gebruik met inhoudsfragmenten - Beperkingen](/help/headless/graphql-api/content-fragments.md#limitations)

### Content Reference {#content-reference}

Met de Content Reference kunt u inhoud van een andere bron renderen, bijvoorbeeld een afbeelding, pagina of Experience Fragment.

Naast de standaardeigenschappen kunt u opgeven:

* De **Hoofdpad**, die aangeeft waar inhoud waarnaar wordt verwezen, moet worden opgeslagen
  >[!NOTE]
  >
  Dit is verplicht als u afbeeldingen in dit veld rechtstreeks wilt uploaden en ernaar wilt verwijzen wanneer u de Content Fragment-editor gebruikt.
  >
  Zie [Referentieafbeeldingen](/help/sites-cloud/administering/content-fragments/authoring.md#reference-images) voor nadere bijzonderheden.

* De inhoudstypen waarnaar kan worden verwezen
  >[!NOTE]
  >
  Deze moeten **Afbeelding** als u afbeeldingen in dit veld rechtstreeks wilt uploaden en ernaar wilt verwijzen wanneer u de Inhoudsfragmenteditor gebruikt.
  >
  Zie [Referentieafbeeldingen](/help/sites-cloud/administering/content-fragments/authoring.md#reference-images) voor nadere bijzonderheden.

* Beperkingen voor bestandsgrootten
* Als naar een afbeelding wordt verwezen:
   * Miniatuur tonen
   * Hoogte- en breedtebeperkingen voor afbeeldingen

![Content Reference](assets/cf-cfmodels-content-reference.png)

### Fragmentverwijzing (geneste fragmenten) {#fragment-reference-nested-fragments}

De fragmentverwijzing verwijst naar een of meer inhoudsfragmenten. Deze functie is met name van belang wanneer u inhoud ophaalt die u in uw app wilt gebruiken, aangezien u gestructureerde gegevens met meerdere lagen kunt ophalen.

Bijvoorbeeld:

* Een model dat details voor een werknemer bepaalt; met inbegrip van:
   * Een verwijzing naar het model dat de werkgever (onderneming) definieert

```xml
type EmployeeModel {
    name: String
    firstName: String
    company: CompanyModel
}

type CompanyModel {
    name: String
    street: String
    city: String
}
```

>[!NOTE]
>
Fragmentverwijzingen zijn van bijzonder belang voor [Levering van inhoud zonder kop met gebruik van inhoudsfragmenten met GraphQL](/help/sites-cloud/administering/content-fragments/content-delivery-with-graphql.md).

Naast de standaardeigenschappen kunt u definiëren:

* **Renderen als**:

   * **multifield** - de auteur van het fragment kan meerdere, afzonderlijke, verwijzingen maken

   * **fragmentreference** - Hiermee kan de auteur van het fragment één verwijzing naar een fragment selecteren

* **Modeltype**
U kunt meerdere modellen selecteren. Wanneer u verwijzingen toevoegt aan een inhoudsfragment, moeten fragmenten waarnaar wordt verwezen, met deze modellen zijn gemaakt.

* **Hoofdpad**
Geeft een hoofdpad aan voor alle fragmenten waarnaar wordt verwezen.

* **Fragment maken toestaan**

  Hierdoor kan de auteur van het fragment een fragment maken op basis van het juiste model.

   * **fragmentreferencecomponent** - stelt de auteur van het fragment in staat een samenstelling samen te stellen door meerdere fragmenten te selecteren

  ![Fragmentverwijzing](assets/cf-cfmodels-fragment-reference.png)

>[!NOTE]
>
Er is een terugkerend beschermingsmechanisme ingesteld. Het is de gebruiker niet toegestaan het huidige inhoudsfragment in de fragmentverwijzing te selecteren en leidt mogelijk tot een leeg dialoogvenster van de kiezer voor fragmentverwijzing.
>
Ook fragmentverwijzingen worden in GraphQL herhaaldelijk beschermd. Als u een diepe vraag over twee Fragments creeert van de Inhoud die elkaar van verwijzingen voorzien, keert het ongeldig terug.

## Een inhoudsfragmentmodel in- of uitschakelen {#enabling-disabling-a-content-fragment-model}

U kunt **Inschakelen** of **Uitschakelen** uw modellen van het Fragment van de Inhoud, voor volledige controle over hun gebruik.

### Een inhoudsfragmentmodel inschakelen {#enabling-a-content-fragment-model}

Nadat een model is gemaakt, moet het zijn ingeschakeld zodat het:

* Deze optie is beschikbaar voor selectie wanneer u een inhoudsfragment maakt.
* Er kan vanuit een inhoudsfragmentmodel naar worden verwezen.
* Is beschikbaar aan GraphQL; zo wordt het schema geproduceerd.

Een model inschakelen dat is gemarkeerd als:

* **Concept** : new (Nooit ingeschakeld).
* **Uitgeschakeld** : is specifiek uitgeschakeld.

U gebruikt de **Inschakelen** optie van:

* De bovenste werkbalk als het vereiste model is geselecteerd.
* De corresponderende snelle actie (mouse-over het vereiste model).

![Concept of Uitgeschakeld model inschakelen](assets/cf-cfmodels-status-enable.png)

### Een inhoudsfragmentmodel uitschakelen {#disabling-a-content-fragment-model}

Een model kan ook worden uitgeschakeld, zodat:

* Het model is niet meer beschikbaar als basis voor het maken van *new* Inhoudsfragmenten
* Echter:
   * Het GraphQL-schema wordt steeds gegenereerd en kan nog steeds worden opgevraagd (om te voorkomen dat JSON API wordt beïnvloed).
   * Om het even welke die Inhoudsfragmenten van het model worden gebaseerd kunnen nog van het eindpunt van GraphQL worden gevraagd en zijn teruggekeerd.
* Er kan niet meer naar het model worden verwezen, maar bestaande verwijzingen blijven ongewijzigd en kunnen nog steeds worden opgevraagd en geretourneerd vanaf het GraphQL-eindpunt.

Een model uitschakelen dat is gemarkeerd als **Ingeschakeld**, gebruikt u de **Uitschakelen** optie van:

* De bovenste werkbalk als het vereiste model is geselecteerd.
* De corresponderende snelle actie (mouse-over het vereiste model).

![Een geactiveerd model uitschakelen](assets/cf-cfmodels-status-disable.png)

## Modellen voor inhoudsfragmenten toestaan in de middelenmap {#allowing-content-fragment-models-assets-folder}

Om inhoudsbeheer uit te voeren, kunt u vormen **Beleid** in de map Elementen om te bepalen welke modellen van inhoudsfragmenten mogen worden gemaakt voor fragmenten in die map.

>[!NOTE]
>
Het mechanisme lijkt op [toestaan, van paginasjablonen](/help/sites-cloud/authoring/sites-console/templates.md#allowing-a-template-author) voor een pagina en de onderliggende elementen, in geavanceerde eigenschappen van een pagina.

Om te vormen **Beleid** for **Modellen voor toegestane inhoudsfragmenten**:

1. Navigeren en openen **Eigenschappen** voor de map met vereiste middelen.

1. Open de **Beleid** tab, waar u kunt configureren:

   * **Overgenomen van`<folder>`**

     Het beleid wordt automatisch geërft wanneer het creëren van nieuwe kindomslagen; het beleid kan (en de erfenis gebroken) worden opnieuw gevormd als subfolders modellen moeten toestaan verschillend aan de ouderomslag.

   * **Modellen van inhoudsfragmenten op pad toestaan**

     U kunt meerdere modellen toestaan.

   * **Modellen voor inhoudsfragmenten zijn toegestaan op tag**

     U kunt meerdere modellen toestaan.

   ![Beleid inhoudsfragmentmodel](assets/cf-cfmodels-policy-assets-folder.png)

1. **Opslaan** eventuele wijzigingen.

De modellen van inhoudsfragmenten die zijn toegestaan voor een map, worden als volgt opgelost:
* De **Beleid** for **Modellen voor toegestane inhoudsfragmenten**.
* Als dit leeg is, kunt u het beleid bepalen met behulp van de overervingsregels.
* Als de overervingsketen geen resultaat oplevert, kijkt u naar de **Cloud Servicen** configuratie voor die map (ook eerst rechtstreeks en vervolgens via overerving).
* Als geen van de bovenstaande resultaten worden behaald, zijn er geen modellen toegestaan voor die map.

## Een inhoudsfragmentmodel verwijderen {#deleting-a-content-fragment-model}

>[!CAUTION]
>
Het verwijderen van een model van een inhoudsfragment kan invloed hebben op afhankelijke fragmenten.

Een model van een inhoudsfragment verwijderen:

1. Navigeren naar **Gereedschappen**, **Algemeen** en vervolgens openen **Modellen van inhoudsfragmenten**.

1. Navigeer naar de map met het model van het inhoudsfragment.
1. Selecteer uw model, gevolgd door **Verwijderen** op de werkbalk.

   >[!NOTE]
   >
   Als naar het model wordt verwezen, wordt een waarschuwing gegeven, zodat u aangewezen actie kunt nemen.

## Een inhoudsfragmentmodel publiceren {#publishing-a-content-fragment-model}

Modellen van inhoudsfragmenten moeten worden gepubliceerd wanneer/voordat afhankelijke inhoudsfragmenten worden gepubliceerd.

Een model van een inhoudsfragment publiceren:

1. Navigeren naar **Gereedschappen**, **Algemeen** en vervolgens openen **Modellen van inhoudsfragmenten**.

1. Navigeer naar de map met het model van het inhoudsfragment.
1. Selecteer uw model, gevolgd door **Publiceren** op de werkbalk.
De gepubliceerde status wordt getoond in de console.

   >[!NOTE]
   >
   Als u een inhoudsfragment publiceert waarvoor het model nog niet is gepubliceerd, wordt dit in een selectielijst aangegeven en wordt het model met het fragment gepubliceerd.

## Publicatie van een inhoudsfragmentmodel ongedaan maken {#unpublishing-a-content-fragment-model}

Modellen van inhoudsfragmenten kunnen ongepubliceerd zijn als naar deze modellen niet wordt verwezen door fragmenten.

Publicatie van een inhoudsfragmentmodel ongedaan maken:

1. Navigeren naar **Gereedschappen**, **Algemeen** en vervolgens openen **Modellen van inhoudsfragmenten**.

1. Navigeer naar de map met het model van het inhoudsfragment.
1. Selecteer uw model, gevolgd door **Publiceren ongedaan maken** op de werkbalk.
De gepubliceerde status wordt vermeld in de console.

Als u de publicatie probeert ongedaan te maken van een model dat momenteel wordt gebruikt door een of meer fragmenten, wordt een foutwaarschuwing weergegeven. Bijvoorbeeld:

![Foutbericht van Content Fragment Model bij het ongedaan maken van de publicatie van een model dat in gebruik is](assets/cf-cfmodels-unpublish-error.png)

Het bericht suggereert dat u de [Verwijzingen](/help/sites-cloud/authoring/basic-handling.md#references) panel voor een nader onderzoek :

![Inhoudsfragmentmodel in verwijzingen](assets/cf-cfmodels-references.png)

## Vergrendelde (gepubliceerde) modellen van inhoudsfragmenten {#locked-published-content-fragment-models}

Deze functie biedt beheer voor modellen van inhoudsfragmenten die zijn gepubliceerd.

### De uitdaging {#the-challenge}

* Met Content Fragment Models wordt het schema voor GraphQL-query&#39;s in AEM bepaald.

   * AEM GraphQL-schema&#39;s worden gemaakt zodra een Content Fragment Model is gemaakt en kunnen bestaan in zowel auteur- als publicatieomgevingen.

   * Schema&#39;s bij publiceren zijn het meest kritiek aangezien zij de basis voor levende levering van inhoud van het Fragment van de Inhoud in formaat JSON verstrekken.

* Er kunnen zich problemen voordoen wanneer modellen van inhoudsfragmenten worden gewijzigd of met andere woorden worden bewerkt. Dit betekent dat het schema verandert, wat op zijn beurt bestaande vragen van GraphQL kan beïnvloeden.

* Het toevoegen van nieuwe velden aan een inhoudsfragmentmodel mag (gewoonlijk) geen nadelige effecten hebben. Als u echter bestaande gegevensvelden wijzigt (bijvoorbeeld hun naam) of velddefinities verwijdert, worden bestaande GraphQL-query&#39;s verbroken wanneer deze velden worden aangevraagd.

### De vereisten {#the-requirements}

* Gebruikers bewust maken van de risico&#39;s bij het bewerken van modellen die al worden gebruikt voor de levering van live-inhoud (met andere woorden, modellen die zijn gepubliceerd).

* Ook, om onbedoelde veranderingen te vermijden.

Één van beide criteria zou vragen kunnen breken als de gewijzigde modellen opnieuw worden gepubliceerd.

### De oplossing {#the-solution}

U kunt deze problemen oplossen door Modellen voor inhoudsfragmenten op te stellen: *vergrendeld* in de modus ALLEEN-LEZEN op auteur - zodra ze zijn gepubliceerd. Deze status wordt aangegeven door **Vergrendeld**:

![Kaart van vergrendeld inhoudsfragmentmodel](assets/cf-cfmodels-locked.png)

Wanneer het model **Vergrendeld** (in de modus ALLEEN-LEZEN) kunt u de inhoud en structuur van modellen zien, maar u kunt deze niet bewerken.

U kunt **Vergrendeld** modellen van of de console, of modelredacteur:

* Console

  Vanuit de console kunt u de modus ALLEEN-LEZEN beheren met de **Ontgrendelen** en **Vergrendelen** acties op de werkbalk:

  ![Werkbalk van het vergrendelde inhoudsfragmentmodel](assets/cf-cfmodels-locked.png)

   * U kunt **Ontgrendelen** een model om bewerkingen in te schakelen.

     Als u **Ontgrendelen** er wordt een waarschuwing weergegeven en u moet de waarschuwing bevestigen **Ontgrendelen** handeling:
     ![Bericht bij ontgrendelen van inhoudsfragmentmodel](assets/cf-cfmodels-unlock-message.png)

     Vervolgens kunt u het model openen en bewerken.

   * U kunt **Vergrendelen** het model daarna.
   * Wanneer u het model opnieuw publiceert, wordt het meteen opnieuw gepubliceerd naar **Vergrendeld** (ALLEEN-LEZEN) modus.

* Modeleditor

   * Wanneer u een vergrendeld model opent, wordt u gewaarschuwd en krijgt u de volgende drie acties te zien: **Annuleren**, **Alleen-lezen weergeven**, **Bewerken**:

     ![Bericht bij weergave van een vergrendeld inhoudsfragmentmodel](assets/cf-cfmodels-editor-lock-message.png)

   * Als u **Alleen-lezen weergeven** kunt u de inhoud en structuur van het model zien:

     ![Alleen-lezen weergeven - Vergrendeld model inhoudsfragment](assets/cf-cfmodels-editor-locked-view-only.png)

   * Als u **Bewerken**, kunt u uw updates bewerken en opslaan:

     ![Bewerken - Vergrendeld inhoudsfragmentmodel](assets/cf-cfmodels-editor-locked-edit.png)

     >[!NOTE]
     >
     Mogelijk staat er nog een waarschuwing boven aan het scherm, maar dat is wanneer het model al wordt gebruikt door bestaande inhoudsfragmenten.

   * **Annuleren** keert u aan de console terug.
