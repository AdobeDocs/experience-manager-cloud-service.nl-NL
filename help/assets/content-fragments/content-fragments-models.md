---
title: Content Fragment Models (Assets - Content Fragments)
description: Leer hoe Content Fragment Models fungeert als basis voor inhoud zonder kop in AEM, zodat u inhoudsfragmenten met gestructureerde inhoud kunt maken.
exl-id: fd706c74-4cc1-426d-ab56-d1d1b521154b
feature: Content Fragments, GraphQL API
role: User, Admin, Developer
solution: Experience Manager Sites
source-git-commit: ce807274d6138473ff9661897a0816e0feb99f15
workflow-type: tm+mt
source-wordcount: '3604'
ht-degree: 1%

---

# Modellen van inhoudsfragmenten {#content-fragment-models}

De Modellen van het Fragment van de inhoud in AEM bepalen de structuur van inhoud voor uw [&#x200B; inhoudsfragmenten &#x200B;](/help/assets/content-fragments/content-fragments.md), die als stichting van uw inhoud zonder kop dienen.

U kunt als volgt modellen van inhoudsfragmenten gebruiken:

1. [Functionaliteit van inhoudsfragmentmodel inschakelen voor uw instantie](/help/assets/content-fragments/content-fragments-configuration-browser.md)
1. [&#x200B; creeer &#x200B;](#creating-a-content-fragment-model), en [&#x200B; vorm &#x200B;](#defining-your-content-fragment-model), uw Modellen van het Fragment van de Inhoud
1. [&#x200B; laat uw Modellen van het Fragment van de Inhoud &#x200B;](#enabling-disabling-a-content-fragment-model) voor gebruik toe wanneer het creëren van de Fragmenten van de Inhoud
1. [&#x200B; sta uw Modellen van het Fragment van de Inhoud op de vereiste omslagen van Assets &#x200B;](#allowing-content-fragment-models-assets-folder) toe door **Beleid** te vormen.

>[!NOTE]
>
>Ben me bewust van de [&#x200B; Beste praktijken &#x200B;](/help/assets/content-fragments/content-fragments.md#best-practices) wanneer het werken met uw Modellen van het Fragment van de Inhoud en de Fragmenten van de Inhoud.

>[!NOTE]
>
>De Fragmenten van de inhoud zijn een eigenschap van Plaatsen, maar worden opgeslagen als **Assets**.
>
>De Fragmenten van de inhoud en de Modellen van het Fragment van de Inhoud worden nu hoofdzakelijk beheerd met de **[console van de Fragmenten van de Inhoud](/help/sites-cloud/administering/content-fragments/overview.md#content-fragments-console)**, hoewel de Fragmenten van de Inhoud nog van de **Assets** console kunnen worden beheerd, en de Modellen van het Fragment van de Inhoud van de **Hulpmiddelen** console. Deze sectie behandelt beheer van **Assets** en **de consoles van Hulpmiddelen**.

>[!NOTE]
>
>Als een model met de [&#x200B; nieuwe modelredacteur &#x200B;](/help/sites-cloud/administering/content-fragments/content-fragment-models.md) werd gecreeerd zou u die redacteur voor het model altijd moeten gebruiken.
>
>Als u dan het model met deze (originele) modelredacteur opent, zult u het bericht zien:
>
>* &quot;This model has a custom UI Schema configured. De volgorde van velden die in deze interface worden weergegeven, komt mogelijk niet overeen met het UI-schema. Als u de velden wilt weergeven die zijn uitgelijnd met het UI-schema, moet u overschakelen naar de nieuwe Inhoudsfragmenteditor.&quot;

## Een inhoudsfragmentmodel maken {#creating-a-content-fragment-model}

1. Navigeer aan **Hulpmiddelen**, **Algemene**, dan open **Modellen van het Fragment van de Inhoud**.
1. Navigeer aan de omslag aangewezen aan uw [&#x200B; configuratie, of sub-configuratie &#x200B;](/help/assets/content-fragments/content-fragments-configuration-browser.md).
1. Het gebruik **creeert** om de tovenaar te openen.

   >[!CAUTION]
   >
   >Als het [&#x200B; gebruik van de modellen van het inhoudsfragment niet &#x200B;](/help/assets/content-fragments/content-fragments-configuration-browser.md) is toegelaten, **creeer** optie zal niet beschikbaar zijn.

1. Specificeer de **ModelTitel**.
U kunt diverse eigenschappen ook bepalen; bijvoorbeeld, voeg **Markeringen** toe, a **Beschrijving**, en selecteer **model** toelaten [&#x200B; om het model &#x200B;](#enabling-disabling-a-content-fragment-model) indien nodig toe te laten.

   >[!NOTE]
   >
   >Voor details over het **StandaardPatroon van de Voorproef URL** zie [&#x200B; Model van het Fragment van de Inhoud - Eigenschappen &#x200B;](#content-fragment-model-properties).

   ![&#x200B; titel en beschrijving &#x200B;](assets/cfm-models-02.png)

1. Het gebruik **creeert** om het lege model te bewaren. Een bericht zal op het succes van de actie wijzen, kunt u **Open** selecteren om het model onmiddellijk uit te geven, of **Gedaan** om aan de console terug te keren.

## Het model van het inhoudsfragment definiëren {#defining-your-content-fragment-model}

Het model van het inhoudsfragment bepaalt effectief de structuur van de resulterende inhoudsfragmenten gebruikend een selectie van **[Types van Gegevens](#data-types)**. Gebruikend de modelredacteur kunt u instanties van de gegevenstypes toevoegen, dan hen vormen om de vereiste gebieden tot stand te brengen:

>[!CAUTION]
>
>Het bewerken van een bestaand inhoudsfragmentmodel kan invloed hebben op afhankelijke fragmenten.

1. Navigeer aan **Hulpmiddelen**, **Algemene**, dan open **Modellen van het Fragment van de Inhoud**.

1. Navigeer naar de map met het fragmentmodel van de inhoud.
1. Open het vereiste model voor **uitgeven**; gebruik of de snelle actie, of selecteer het model en toen de actie van de toolbar.

   Zodra open de modelredacteur toont:

   * links: velden al gedefinieerd
   * rechts: **datatypen** voor het maken van velden (en **eigenschappen** voor gebruik als er velden zijn gemaakt)
   * top: een optie om de [&#x200B; nieuwe redacteur &#x200B;](/help/sites-cloud/administering/content-fragments/content-fragment-models.md) te proberen

   >[!NOTE]
   >
   >Wanneer een gebied zoals **Vereist**, wordt het **Etiket** vermeld in de linkerruit duidelijk met een asterix (**&#42;**).

![&#x200B; eigenschappen &#x200B;](assets/cfm-models-03.png)

1. **om een Gebied** toe te voegen

   * Sleep een vereist gegevenstype naar de vereiste locatie voor een veld:

     ![&#x200B; gegevenstype aan gebied &#x200B;](assets/cfm-models-04.png)

   * Zodra een gebied aan het model is toegevoegd, zal het juiste paneel de **Eigenschappen** tonen die voor dat bepaalde gegevenstype kunnen worden bepaald. Hier kunt u definiëren wat voor dat veld is vereist.

      * Vele eigenschappen zijn duidelijk-verklarend, voor extra details zie [&#x200B; Eigenschappen &#x200B;](#properties).
      * Het typen a **Etiket van het Gebied** zal de **Naam van het Bezit** auto-voltooien - als leeg, en het kan achteraf manueel worden bijgewerkt.

        >[!CAUTION]
        >
        >Wanneer manueel het bijwerken van de naam van het bezit **&#x200B;**&#x200B;voor een gegevenstype, merk op dat de namen slechts a-Z, a-z, 0-9 en onderstrepingsteken &quot;_&quot;als speciaal karakter moeten bevatten.
        >
        >Als modellen die in eerdere versies van AEM zijn gemaakt, ongeldige tekens bevatten, verwijdert of werkt u die tekens bij.

     Bijvoorbeeld:

     ![&#x200B; gebiedseigenschappen &#x200B;](assets/cfm-models-05.png)

1. **om een Gebied** te verwijderen

   Selecteer het vereiste veld en selecteer vervolgens het prullenbakpictogram. U wordt gevraagd de actie te bevestigen.

   ![&#x200B; verwijder &#x200B;](assets/cfm-models-06.png)

1. Voeg alle vereiste velden toe en definieer de bijbehorende eigenschappen, zoals vereist. Bijvoorbeeld:

   ![&#x200B; sparen &#x200B;](assets/cfm-models-07.png)

1. Selecteer **sparen** om de definitie voort te zetten.

## Gegevenstypen {#data-types}

Voor het definiëren van uw model zijn verschillende gegevenstypen beschikbaar:

* **Enige lijntekst**
   * Een veld toevoegen voor één regel tekst; de maximumlengte kan worden gedefinieerd
   * Het veld kan zo worden geconfigureerd dat fragmentauteurs nieuwe instanties van het veld kunnen maken

* **Meerdere lijntekst**
   * Een tekstgebied dat RTF-tekst, platte tekst of Markering kan zijn
   * Het veld kan zo worden geconfigureerd dat fragmentauteurs nieuwe instanties van het veld kunnen maken

  >[!NOTE]
  >
  >Of het tekstgebied Rijke Tekst, Onbewerkte Tekst, of Markting is, wordt bepaald in het model door het bezit **StandaardType**.
  >
  >Dit formaat kan niet van de [&#x200B; redacteur van het Fragment van de Inhoud &#x200B;](/help/sites-cloud/administering/content-fragments/authoring.md) worden veranderd, maar slechts van het Model.

* **Aantal**
   * Een numeriek veld toevoegen
   * Het veld kan zo worden geconfigureerd dat fragmentauteurs nieuwe instanties van het veld kunnen maken

* **Van Boole**
   * Een Booleaans selectievakje toevoegen

* **Datum en tijd**
   * Een datum- en/of tijdveld toevoegen

* **Opsomming**
   * Een set selectievakjes, keuzerondjes of vervolgkeuzelijsten toevoegen
      * U kunt de opties specificeren beschikbaar aan de fragmentauteur

* **Markeringen**
   * Hiermee kunnen auteurs van fragmenten gebieden met tags openen en selecteren

* **Verwijzing van het Fragment**
   * Verwijzingen andere Fragmenten van de Inhoud; kan worden gebruikt om [&#x200B; genestelde inhoud &#x200B;](#using-references-to-form-nested-content) tot stand te brengen
   * Het gegevenstype kan worden geconfigureerd om fragmentauteurs toe te staan:
      * Bewerk het fragment waarnaar wordt verwezen rechtstreeks.
      * Een nieuw inhoudsfragment maken op basis van het juiste model
      * Nieuwe instanties van het veld maken
   * De verwijzing geeft het pad naar de resource waarnaar wordt verwezen aan, bijvoorbeeld `/content/dam/path/to/resource`

* **Verwijzing van het Fragment (UUID)**
   * Verwijzingen andere Fragmenten van de Inhoud; kan worden gebruikt om [&#x200B; genestelde inhoud &#x200B;](#using-references-to-form-nested-content) tot stand te brengen
   * Het gegevenstype kan worden geconfigureerd om fragmentauteurs toe te staan:
      * Bewerk het fragment waarnaar wordt verwezen rechtstreeks.
      * Een nieuw inhoudsfragment maken op basis van het juiste model
      * Nieuwe instanties van het veld maken
   * In de redacteur, specificeert de verwijzing de weg aan het referenced middel; intern wordt de verwijzing gehouden als universeel unieke identiteitskaart (UUID) die verwijzingen het middel
      * U hoeft de UUID niet te weten; in de fragmenteditor kunt u naar het vereiste fragment bladeren

  >[!NOTE]
  >
  >De UUID&#39;s zijn specifiek voor de gegevensopslagruimte. Als u het [&#x200B; Hulpmiddel van het Exemplaar van de Inhoud &#x200B;](/help/implementing/developing/tools/content-copy.md) gebruikt om de Fragmenten van de Inhoud te kopiëren, zal UUIDs in het doelmilieu opnieuw worden berekend.

* **Verwijzing van de Inhoud**
   * Verwijzingen andere inhoud, van om het even welk type; kan worden gebruikt om [&#x200B; te creëren genestelde inhoud &#x200B;](#using-references-to-form-nested-content)
   * Als er naar een afbeelding wordt verwezen, kunt u ervoor kiezen een miniatuur weer te geven
   * Het veld kan zo worden geconfigureerd dat fragmentauteurs nieuwe instanties van het veld kunnen maken
   * De verwijzing geeft het pad naar de resource waarnaar wordt verwezen aan, bijvoorbeeld `/content/dam/path/to/resource`

* **Verwijzing van de Inhoud (UUID)**
   * Verwijzingen andere inhoud, van om het even welk type; kan worden gebruikt om [&#x200B; te creëren genestelde inhoud &#x200B;](#using-references-to-form-nested-content)
   * Als er naar een afbeelding wordt verwezen, kunt u ervoor kiezen een miniatuur weer te geven
   * Het veld kan zo worden geconfigureerd dat fragmentauteurs nieuwe instanties van het veld kunnen maken
   * In de redacteur, specificeert de verwijzing de weg aan het referenced middel; intern wordt de verwijzing gehouden als universeel unieke identiteitskaart (UUID) die verwijzingen het middel
      * U hoeft de UUID niet te weten; in de fragmenteditor kunt u naar de vereiste elementbron bladeren

  >[!NOTE]
  >
  >De UUID&#39;s zijn specifiek voor de gegevensopslagruimte. Als u het [&#x200B; Hulpmiddel van het Exemplaar van de Inhoud &#x200B;](/help/implementing/developing/tools/content-copy.md) gebruikt om de Fragmenten van de Inhoud te kopiëren, zal UUIDs in het doelmilieu opnieuw worden berekend.

* **voorwerp JSON**
   * Hiermee stelt u de auteur van inhoudsfragment in staat JSON-syntaxis in te voeren in de overeenkomende elementen van een fragment.
      * AEM toestaan direct JSON op te slaan dat u hebt gekopieerd/geplakt van een andere service.
      * De JSON wordt doorgegeven en uitvoer als JSON in GraphQL.
      * Neemt JSON-syntaxismarkering, automatisch aanvullen en foutmarkering op in de inhoudsfragmenteditor.

* **Placeholder van het Lusje**
   * Hiermee kunt u tabbladen invoeren die u kunt gebruiken bij het bewerken van de inhoud van het inhoudsfragment.
      * Deze worden getoond als verdelers in de modelredacteur, scheidend secties van de lijst van inhoudstypes. Elke instantie vertegenwoordigt het begin van een nieuw lusje.
      * In de fragmenteditor wordt elke instantie weergegeven als een tab.

     >[!NOTE]
     >
     >Dit gegevenstype wordt alleen gebruikt voor opmaak en wordt genegeerd door het AEM GraphQL-schema.

## Eigenschappen {#properties}

Vele eigenschappen zijn voor zichzelf verklarend, voor bepaalde eigenschappen zijn hieronder meer details te vinden:

* **de Naam van het Bezit**

  Wanneer manueel het bijwerken van dit bezit voor een gegevenstype, merk op dat de namen **&#x200B;**&#x200B;*slechts* a-z, a-z, 0-9 en onderstrepingsteken &quot;_&quot;als speciaal karakter moeten bevatten.

  >[!CAUTION]
  >
  >Als modellen die in eerdere versies van AEM zijn gemaakt, ongeldige tekens bevatten, verwijdert of werkt u die tekens bij.

* **geeft terug als**
De verschillende opties voor het realiseren/renderen van het veld in een fragment. Met deze eigenschap kunt u vaak definiëren of de auteur één instantie van het veld ziet of meerdere instanties mag maken. Wanneer **Veelvoudig Gebied** wordt gebruikt kunt u het minimum en maximumaantal punten bepalen - zie [&#x200B; Bevestiging &#x200B;](#validation) voor verdere details.

* **Etiket van het Gebied**
Het ingaan van het Etiket van het a **Gebied** zal autogenerate a **Naam van het Bezit**, die dan manueel kan worden bijgewerkt indien nodig.

* **Bevestiging**
De fundamentele bevestiging is beschikbaar door mechanismen zoals het **Vereiste** bezit. Sommige gegevenstypen hebben extra validatievelden. Zie [&#x200B; Bevestiging &#x200B;](#validation) voor verdere details.

* Voor het datatype **Tekst met meerdere regels** is het mogelijk het **standaardtype** als volgt te definiëren:

   * **Rijke Tekst**
   * **Markering**
   * **Onbewerkte Tekst**

  Als gespecificeerd niet, wordt de standaardwaarde **Rijke Tekst** gebruikt voor dit gebied.

  Het wijzigen van het **standaardtype** in een contentfragmentmodel heeft alleen effect op een bestaand, gerelateerd contentfragment nadat dat fragment is geopend in de editor en opgeslagen.

* **Uniek**
De inhoud (voor het specifieke veld) moet uniek zijn in alle inhoudsfragmenten die op basis van het huidige model zijn gemaakt.

  Dit wordt gebruikt om ervoor te zorgen dat inhoudsauteurs geen inhoud kunnen herhalen die al in een ander fragment van hetzelfde model is toegevoegd.

  Bijvoorbeeld, het 1&rbrace; gebied van de a **Enige lijntekst &lbrace;in het Model van het Fragment van de Inhoud kan niet de waarde** in twee afhankelijke Fragmenten van de Inhoud hebben. `Country` `Japan` Er wordt een waarschuwing weergegeven wanneer de tweede instantie wordt geprobeerd.

  >[!NOTE]
  >
  >Er wordt gezorgd voor uniformiteit per taalwortel.

  >[!NOTE]
  >
  >De variaties kunnen de zelfde *unieke* waarde zoals variaties van het zelfde fragment hebben, maar niet de zelfde waarde zoals die in om het even welke variatie van andere fragmenten wordt gebruikt.

  >[!CAUTION]
  >
  >Als u MSM (dat tot exemplaren van de Fragmenten van de Inhoud leidt) wilt gebruiken, dan zouden om het even welke **Unieke** beperkingen uit om het even welke Types moeten worden verwijderd van Gegevens die in de respectieve Modellen van het Fragment van de Inhoud worden gebruikt.

* Zie **[Verwijzing van de Inhoud](#content-reference)** voor meer details over dat specifieke gegevenstype en zijn eigenschappen.

* Zie **[Verwijzing van het Fragment (Genestelde Fragments)](#fragment-reference-nested-fragments)** voor meer details over dat specifieke gegevenstype en zijn eigenschappen.

* **Vertaalbaar**

  Het controleren van **Vertaalbare** checkbox op een gebied in de Modelredacteur van het Fragment van de Inhoud:

   * Controleer of de eigenschapsnaam van het veld wordt toegevoegd aan de vertaalconfiguratie, context `/content/dam/<sites-configuration>`, als deze nog niet aanwezig is.
   * Voor GraphQL: stel een eigenschap `<translatable>` in het veld Inhoudsfragment in op `yes` om GraphQL-queryfilter toe te staan voor JSON-uitvoer met alleen vertaalbare inhoud.

## Validatie {#validation}

Verschillende gegevenstypen bieden nu de mogelijkheid om validatievereisten te definiëren voor het tijdstip waarop inhoud wordt ingevoerd in het resulterende fragment:

* **Enige lijntekst**
   * Vergelijk met een vooraf gedefinieerde regex.
* **Aantal**
   * Controleren op specifieke waarden.
* **Verwijzing van de Inhoud**
   * Testen op specifieke typen inhoud.
   * Er kan alleen worden verwezen naar elementen van een opgegeven bestandsgrootte of kleiner.
   * Er kan alleen worden verwezen naar afbeeldingen met een vooraf gedefinieerde breedte en/of hoogte (in pixels).
* **Verwijzing van het Fragment**
   * Testen op een specifiek inhoudsfragmentmodel.
* **Min Aantal Punten** / **Max Aantal Punten**

  De gebieden die als a **Veelvoudig Gebied** zijn bepaald (die met **worden geplaatst teruggeven als**) hebben de opties:

   * **Min Aantal Punten**
   * **Max Aantal Punten**

  Deze worden gevalideerd:

   * De maximumwaarde wordt bevestigd in de [&#x200B; originele Redacteur van het Fragment van de Inhoud &#x200B;](/help/assets/content-fragments/content-fragments-variations.md).
   * Beide worden bevestigd in de [&#x200B; Redacteur van het Fragment van de Inhoud &#x200B;](/help/sites-cloud/administering/content-fragments/authoring.md).

## Referenties gebruiken om geneste inhoud te vormen {#using-references-to-form-nested-content}

Inhoudsfragmenten kunnen geneste inhoud vormen met een van de volgende gegevenstypen:

* [Content Reference](#content-reference)
   * Verstrekt een eenvoudige verwijzing naar andere inhoud; van om het even welk type.
   * Verstrekt door de gegevenstypes:
      * **Verwijzing van de Inhoud** - gebaseerd weg
      * **Verwijzing van de Inhoud (UUID)** - gebaseerd UUID
   * Kan worden geconfigureerd voor een of meerdere verwijzingen (in het resulterende fragment).

* [&#x200B; Verwijzing van het Fragment &#x200B;](#fragment-reference-nested-fragments) (Geneste Fragmenten)
   * Verwijzingen naar andere fragmenten, afhankelijk van de opgegeven modellen.
   * Verstrekt door de gegevenstypes:
      * **Verwijzing van het Fragment** - gebaseerd weg
      * **Verwijzing van het Fragment (UUID)** - gebaseerd UUID
   * Hiermee kunt u gestructureerde gegevens opnemen/ophalen.

     >[!NOTE]
     >
     >Deze methode is van bijzonder belang wanneer u [&#x200B; Zwaarloze Levering van de Inhoud gebruikend de Fragmenten van de Inhoud met GraphQL &#x200B;](/help/sites-cloud/administering/content-fragments/content-delivery-with-graphql.md) gebruikt.

   * Kan worden geconfigureerd voor een of meerdere verwijzingen (in het resulterende fragment).

>[!NOTE]
>
>Zie [&#x200B; bevorderen uw Fragmenten van de Inhoud voor Verwijzingen UUID &#x200B;](/help/headless/graphql-api/uuid-reference-upgrade.md) voor verdere informatie over de Verwijzing van de Inhoud/van het Fragment en de Verwijzing van de Inhoud/van het Fragment (UUID), en bevordering aan de op UUID-Gebaseerde gegevenstypes.

>[!NOTE]
>
>AEM heeft een terugkerende bescherming voor:
>
>* Content References
>  Zo voorkomt u dat de gebruiker een verwijzing naar het huidige fragment toevoegt. Dit kan leiden tot een leeg dialoogvenster van de kiezer voor fragmentverwijzing.
>
>* Fragmentverwijzingen in GraphQL
>  Wanneer u een diepe query maakt die meerdere Content Fragments retourneert waarnaar door elkaar wordt verwezen, wordt null geretourneerd bij de eerste instantie.

### Content Reference {#content-reference}

De **Verwijzing van de Inhoud** en **Verwijzing van de Inhoud (UUID)** gegevenstypes staan u toe om inhoud van een andere bron terug te geven; bijvoorbeeld, beeld, pagina of het Fragment van de Ervaring.

Naast de standaardeigenschappen kunt u opgeven:

* Het **Weg van de Wortel** voor om het even welke referenced inhoud
* De inhoudstypen waarnaar kan worden verwezen
* Beperkingen voor bestandsgrootten
* Als naar een afbeelding wordt verwezen:
   * Miniatuur tonen
   * Hoogte- en breedtebeperkingen voor afbeeldingen

![&#x200B; Verwijzing van de Inhoud &#x200B;](assets/cfm-content-reference.png)

### Fragmentverwijzing (geneste fragmenten) {#fragment-reference-nested-fragments}

De **Verwijzing van het Fragment** en **Verwijzing van het Fragment (UUID)** gegevenstypes kunnen één, of meer, de Fragmenten van de Inhoud van verwijzingen voorzien. Deze functie is met name van belang wanneer u inhoud ophaalt die u in uw app wilt gebruiken, aangezien u gestructureerde gegevens met meerdere lagen kunt ophalen.

Bijvoorbeeld:

* Een model dat details voor een werknemer bepaalt; deze omvatten:
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
>Dit is van bijzonder belang samen met [&#x200B; Hoofdloze Levering van de Inhoud gebruikend de Fragmenten van de Inhoud met GraphQL &#x200B;](/help/assets/content-fragments/content-fragments-graphql.md).

Naast de standaardeigenschappen kunt u definiëren:

* **geeft terug als**:

   * **multifield** - de fragmentauteur kan veelvoudige, individuele, verwijzingen creëren

   * **fragmentreference** - staat de fragmentauteur toe om één enkele verwijzing naar een fragment te selecteren

* **ModelType**
U kunt meerdere modellen selecteren. Bij het ontwerpen van het inhoudsfragment moeten fragmenten waarnaar wordt verwezen, met deze modellen zijn gemaakt.

* **Weg van de Wortel**
Geeft een hoofdpad aan voor alle fragmenten waarnaar wordt verwezen.

* **staat het Maken van het Fragment toe**

  Hierdoor kan de auteur van het fragment een fragment maken op basis van het juiste model.

   * **fragmentreferencecomposite** - staat de fragmentauteur toe om een samenstelling te bouwen, door veelvoudige fragmenten te selecteren

  ![&#x200B; Verwijzing van het Fragment &#x200B;](assets/cfm-fragment-reference.png)

>[!NOTE]
>
>Er is een terugkerend beschermingsmechanisme ingesteld. Hiermee wordt de gebruiker verboden het huidige inhoudsfragment in de fragmentverwijzing te selecteren. Dit kan leiden tot een leeg dialoogvenster van de kiezer voor fragmentverwijzing.
>
>Er is ook een herhalingsbescherming voor fragmentverwijzingen in GraphQL. Als u een diepe vraag over twee Fragments creeert van de Inhoud die elkaar van verwijzingen voorzien, zal het ongeldig terugkeren.

## Inhoudsfragmentmodel - eigenschappen {#content-fragment-model-properties}

U kunt **Eigenschappen** van een Model van het Fragment van de Inhoud uitgeven:

* **Basis**
   * **ModelTitel**
   * **Markeringen**
   * **Beschrijving**
   * **upload Beeld**
   * **Standaard het Patroon van URL van de Voorproef**

     >[!NOTE]
     >
     >Dit wordt slechts gebruikt door de *nieuwe* Redacteur van het Fragment van de Inhoud. Zie [&#x200B; Modellen van het Fragment van de Inhoud &#x200B;](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#content-fragment-model-properties) voor verdere informatie.


## Een inhoudsfragmentmodel in- of uitschakelen {#enabling-disabling-a-content-fragment-model}

Voor volledige controle over het gebruik van uw modellen van het Fragment van de Inhoud hebben zij een status die u kunt plaatsen.

### Een inhoudsfragmentmodel inschakelen {#enabling-a-content-fragment-model}

Wanneer een model wordt gecreeerd moet het worden toegelaten zodat het:

* Deze optie is beschikbaar voor selectie wanneer u een inhoudsfragment maakt.
* Er kan vanuit een inhoudsfragmentmodel naar worden verwezen.
* Is beschikbaar aan GraphQL; zo wordt het schema geproduceerd.

Een model inschakelen dat is gemarkeerd als:

* **Ontwerp** : mw (nooit toegelaten).
* **Gehandicapten** : is specifiek onbruikbaar gemaakt.

U gebruikt **toelaten** optie van één van beiden:

* De bovenste werkbalk als het vereiste model is geselecteerd.
* De corresponderende snelle actie (mouse-over het vereiste model).

![&#x200B; laat een Ontwerp of Gehandicapte Model &#x200B;](assets/cfm-status-enable.png) toe

### Een inhoudsfragmentmodel uitschakelen {#disabling-a-content-fragment-model}

Een model kan ook worden uitgeschakeld, zodat:

* Het model is niet meer beschikbaar als basis voor het creëren van *nieuwe* Fragmenten van de Inhoud.
* Echter:
   * Het GraphQL-schema wordt steeds gegenereerd en kan nog steeds worden opgevraagd (om te voorkomen dat JSON API wordt beïnvloed).
   * Om het even welke die Inhoudsfragmenten van het model worden gebaseerd kunnen nog van het eindpunt van GraphQL worden gevraagd en zijn teruggekeerd.
* Er kan niet meer naar het model worden verwezen, maar bestaande verwijzingen blijven ongewijzigd en kunnen nog steeds worden opgevraagd en geretourneerd vanaf het GraphQL-eindpunt.

Om een Model onbruikbaar te maken dat als **toegelaten** wordt gemarkeerd gebruikt u **maak** optie van één van beiden onbruikbaar:

* De bovenste werkbalk als het vereiste model is geselecteerd.
* De corresponderende snelle actie (mouse-over het vereiste model).

![&#x200B; maak toegelaten Model &#x200B;](assets/cfm-status-disable.png) onbruikbaar

## Modellen voor inhoudsfragmenten toestaan in uw Assets-map {#allowing-content-fragment-models-assets-folder}

Om inhoudsbeheer uit te voeren, kunt u **Beleid** op de omslag van Assets vormen om te controleren welke Modellen van het Fragment van de Inhoud voor de verwezenlijking van het Fragment in die omslag worden toegestaan.

>[!NOTE]
>
>Het mechanisme is gelijkaardig aan [&#x200B; toestaand paginasjablonen &#x200B;](/help/sites-cloud/authoring/page-editor/templates.md#allowing-a-template-author) voor een pagina, en zijn kinderen, in geavanceerde eigenschappen van een pagina.

Om het **Beleid** voor **toegelaten Modellen van het Fragment van de Inhoud te vormen**:

1. Navigeer en open **Eigenschappen** voor de vereiste omslag van Assets.

1. Open het **Beleid** lusje, waar u kunt vormen:

   * **Overgenomen van`<folder>`**

     Het beleid wordt automatisch geërft wanneer het creëren van nieuwe kindomslagen; het beleid kan (en de erfenis gebroken) worden opnieuw gevormd als de subomslagen modellen moeten toestaan verschillend aan de ouderomslag.

   * **Toegestane Modellen van het Fragment van de Inhoud door Weg**

     U kunt meerdere modellen toestaan.

   * **Toegestane Modellen van het Fragment van de Inhoud door Markering**

     U kunt meerdere modellen toestaan.

   ![&#x200B; Beleid van het Model van het Fragment van de Inhoud &#x200B;](assets/cfm-model-policy-assets-folder.png)

1. **sparen** om het even welke veranderingen.

De modellen van inhoudsfragmenten die zijn toegestaan voor een map, worden als volgt opgelost:

* Het **Beleid** voor **Toegestane Modellen van het Fragment van de Inhoud**.
* Als dit leeg is, kunt u het beleid bepalen met behulp van de overervingsregels.
* Als de overervingsketen geen resultaat levert, dan bekijk de **configuratie van de Diensten van de Wolk** voor die omslag (ook eerst direct en dan via overerving).
* Als geen van de bovenstaande resultaten worden behaald, zijn er geen modellen toegestaan voor die map.

## Een inhoudsfragmentmodel verwijderen {#deleting-a-content-fragment-model}

>[!CAUTION]
>
>Het verwijderen van een inhoudsfragmentmodel kan invloed hebben op afhankelijke fragmenten.

Een inhoudsfragmentmodel verwijderen:

1. Navigeer aan **Hulpmiddelen**, **Algemene**, dan open **Modellen van het Fragment van de Inhoud**.

1. Navigeer naar de map met het fragmentmodel van de inhoud.
1. Selecteer uw model, dat door **wordt gevolgd Schrapping** van de toolbar.

   >[!NOTE]
   >
   >Als naar het model wordt verwezen, wordt een waarschuwing gegeven. Voer de juiste actie uit.

## Een inhoudsfragmentmodel publiceren {#publishing-a-content-fragment-model}

Inhoudsfragmentmodellen moeten worden gepubliceerd wanneer/voordat afhankelijke inhoudsfragmenten worden gepubliceerd.

Een fragmentmodel voor inhoud publiceren:

1. Navigeer aan **Hulpmiddelen**, **Algemene**, dan open **Modellen van het Fragment van de Inhoud**.

1. Navigeer naar de map met het fragmentmodel van de inhoud.
1. Selecteer uw model, dat door **wordt gevolgd publiceert** van de toolbar.
De gepubliceerde status wordt vermeld in de console.

   >[!NOTE]
   >
   >Als u een inhoudsfragment publiceert waarvoor het model nog niet is gepubliceerd, geeft een selectielijst dit aan en wordt het model gepubliceerd met het fragment.

## Publicatie van een inhoudsfragmentmodel ongedaan maken {#unpublishing-a-content-fragment-model}

Inhoudsfragmentmodellen kunnen ongepubliceerd zijn als naar deze modellen niet wordt verwezen door fragmenten.

Publicatie van een inhoudsfragmentmodel ongedaan maken:

1. Navigeer aan **Hulpmiddelen**, **Algemene**, dan open **Modellen van het Fragment van de Inhoud**.

1. Navigeer naar de map met het fragmentmodel van de inhoud.
1. Selecteer uw model, dat door **wordt gevolgd unpublish** van de toolbar.
De gepubliceerde status wordt vermeld in de console.

Als u probeert de publicatie ongedaan te maken van een model dat momenteel wordt gebruikt door een of meer fragmenten, wordt u hiervan op de hoogte gesteld door een foutwaarschuwing:

![&#x200B; de foutenmelding van het Model van het Fragment van de Inhoud wanneer het ongedaan maken van een model dat in gebruik is &#x200B;](assets/cfm-model-unpublish-error.png)

Het bericht zal suggereren dat u het [&#x200B; paneel van Verwijzingen &#x200B;](/help/sites-cloud/authoring/basic-handling.md#references) controleert om verder te onderzoeken:

![&#x200B; Model van het Fragment van de Inhoud in Verwijzingen &#x200B;](assets/cfm-model-references.png)

## Vergrendelde (gepubliceerde) modellen van inhoudsfragmenten {#locked-published-content-fragment-models}

Deze functie biedt beheer voor modellen van inhoudsfragmenten die zijn gepubliceerd.

### De uitdaging {#the-challenge}

* Met Content Fragment Models wordt het schema voor GraphQL-query&#39;s in AEM bepaald.

   * AEM GraphQL-schema&#39;s worden gemaakt zodra een Content Fragment Model is gemaakt en kunnen bestaan in zowel auteur- als publicatieomgevingen.

   * Schema&#39;s bij publiceren zijn het meest kritiek aangezien zij de basis voor levende levering van inhoud van het Fragment van de Inhoud in formaat JSON verstrekken.

* Er kunnen zich problemen voordoen wanneer modellen van inhoudsfragmenten worden gewijzigd of met andere woorden worden bewerkt. Dit betekent dat het schema verandert, wat op zijn beurt bestaande vragen van GraphQL kan beïnvloeden.

* Het toevoegen van nieuwe velden aan een inhoudsfragmentmodel mag (gewoonlijk) geen nadelige effecten hebben. Als u echter bestaande gegevensvelden wijzigt (bijvoorbeeld hun naam) of velddefinities verwijdert, worden bestaande GraphQL-query&#39;s verbroken wanneer deze velden worden aangevraagd.

### De vereisten {#the-requirements}

* Gebruikers bewust maken van de risico&#39;s bij het bewerken van modellen die al worden gebruikt voor de levering van live-inhoud - met andere woorden, modellen die zijn gepubliceerd.

* Ook, om onbedoelde veranderingen te vermijden.

Één van beiden van deze zou vragen kunnen breken als de gewijzigde modellen opnieuw worden gepubliceerd.

### De oplossing {#the-solution}

Om deze kwesties te richten, zijn de Modellen van het Fragment van de Inhoud *gesloten* in een LEZEN-ONLY wijze op auteur - zodra zij zijn gepubliceerd. Dit wordt vermeld door **Vergrendelde**:

![&#x200B; Kaart van het gesloten Model van het Fragment van de Inhoud &#x200B;](assets/cfm-model-locked.png)

Wanneer het model **Vergrendeld** (op LEZEN-ONLY wijze) is, kunt u de inhoud en de structuur van modellen zien maar u kunt hen niet uitgeven.

U kunt **Vergrendelde** modellen van of de console, of modelredacteur beheren:

* Console

  Van de console, kunt u de LEZEN-ONLY wijze met **leiden ontgrendelt** en **ontgrendelt** acties in de toolbar:

  ![&#x200B; Toolbar van het gesloten Model van het Fragment van de Inhoud &#x200B;](assets/cfm-model-locked.png)

   * U kunt **een model ontgrendelen** om uitgeeft toe te laten.

     Als u **&#x200B;**&#x200B;ontgrendelt selecteert, wordt een waarschuwing getoond, en u moet de **ontgrendelen** actie bevestigen:
     ![&#x200B; Bericht wanneer het ontgrendelen van het Model van het Fragment van de Inhoud &#x200B;](assets/cfm-model-unlock-message.png)

     Vervolgens kunt u het model openen en bewerken.

   * U kunt **het model ook** Slot achteraf.
   * Het opnieuw publiceren van het model zal het onmiddellijk in **Vergrendelde** (LEZEN-ONLY) wijze zetten.

* Modeleditor

   * Wanneer u een model opent dat wordt gesloten, wordt u gewaarschuwd, en met drie acties voorgesteld: **annuleert**, **Mening Gelezen**, **geeft** uit:

     ![&#x200B; Bericht wanneer het bekijken van een gesloten Model van het Fragment van de Inhoud &#x200B;](assets/cfm-model-editor-lock-message.png)

   * Als u **Mening slechts** selecteert leest u de inhoud en de structuur van het model kunt zien:

     ![&#x200B; Mening las slechts - het gesloten Model van het Fragment van de Inhoud &#x200B;](assets/cfm-model-editor-locked-view-only.png)

   * Als u **uitgezocht geef** uit u kunt uw updates uitgeven en opslaan:

     ![&#x200B; geef uit - het gesloten Model van het Fragment van de Inhoud &#x200B;](assets/cfm-model-editor-locked-edit.png)

     >[!NOTE]
     >
     >Mogelijk staat er nog een waarschuwing boven aan het scherm, maar dat is wanneer het model al wordt gebruikt door bestaande inhoudsfragmenten.

   * **annuleert** u aan de console zal terugkeren.
