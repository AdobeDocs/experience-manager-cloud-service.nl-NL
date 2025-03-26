---
title: Modellen voor inhoudsfragmenten beheren
description: Leer hoe u Modellen van inhoudsfragmenten beheert. Deze fungeren als basis voor uw inhoudsfragmenten in AEM, zodat u gestructureerde inhoud kunt maken voor gebruik in koploze weergave of voor het ontwerpen van pagina's.
feature: Content Fragments
role: User, Developer, Architect
solution: Experience Manager Sites
exl-id: f94f75c2-12fa-47c0-a71b-327f4210077d
source-git-commit: b8a56b73f8178c432941b50821be91777f203dec
workflow-type: tm+mt
source-wordcount: '2288'
ht-degree: 0%

---

# Modellen voor inhoudsfragmenten beheren {#managing-content-fragment-models}

Van de console van het Fragment van de Inhoud kunt u uw Modellen van het Fragment van de Inhoud beheren, dan [ open de redacteur ](/help/sites-cloud/administering/content-fragments/content-fragment-models.md) om de structuur te bepalen.

De Modellen van het Fragment van de inhoud in Adobe Experience Manager (AEM) as a Cloud Service bepalen de structuur voor de inhoud van uw [ Fragmenten van de Inhoud ](/help/sites-cloud/administering/content-fragments/overview.md). Deze fragmenten kunnen vervolgens worden gebruikt als basis voor inhoud zonder kop of voor het ontwerpen van pagina&#39;s.

>[!IMPORTANT]
>
>Verschillende functies van de Content Fragment Console zijn beschikbaar via het programma Vroege adopter.
>
>Om de status te zien, en hoe te om toe te passen als u geinteresseerd bent, controleer de [ Nota&#39;s van de Versie ](/help/release-notes/release-notes-cloud/release-notes-current.md).

>[!NOTE]
>
>Deze pagina behandelt de sectie van de console die (slechts) de Modellen van het Fragment van de Inhoud toont. Zie voor andere deelvensters:
>
>* [Contentfragmenten beheren](/help/sites-cloud/administering/content-fragments/managing.md)
>* [ het Bekijken van en het Leiden Assets in de Console van Fragmenten van de Inhoud ](/help/sites-cloud/administering/content-fragments/assets-content-fragments-console.md)

>[!NOTE]
>
>De Fragmenten van de inhoud worden opgeslagen als **Assets**. De Modellen van het Fragment van de inhoud worden hoofdzakelijk geleid van de **console van de Fragmenten van de Inhoud**, maar kunnen ook van de [ Assets ](/help/assets/content-fragments/content-fragments-managing.md) console en de optie [ Modellen van het Fragment van de Inhoud ](/help/assets/content-fragments/content-fragments-models.md) worden geleid die van **Hulpmiddelen** - **Algemene** beschikbaar is.

## Werken met modellen van inhoudsfragmenten {#how-to-work-with-content-fragment-models}

Als een zeer snel overzicht, om met de Modellen van het Fragment van de Inhoud te werken u:

1. [Functionaliteit van inhoudsfragmentmodel inschakelen voor uw instantie](/help/sites-cloud/administering/content-fragments/setup.md)
1. [ creeer ](#creating-a-content-fragment-model) uw Model van het Fragment van de Inhoud.
   * Op dit punt kunt u **** het model (voor gebruik ook toelaten wanneer het creëren van de Fragmenten van de Inhoud).
1. [ bepaal ](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#defining-your-content-fragment-model) de structuur van uw model.
1. [ laat uw Model van het Fragment van de Inhoud ](#enabling-a-content-fragment-model) toe, als nog niet gedaan.
1. [ sta uw Modellen van het Fragment van de Inhoud op de vereiste omslagen van Assets ](#allowing-content-fragment-models-assets-folder) toe door **Beleid** te vormen.

## Basisstructuur en verwerking van modellen van inhoudsfragmenten in de console {#basic-structure-handling-content-fragment-models-console}

U kunt het uiterst linkerpaneel van de [ console van de Fragmenten van de Inhoud ](/help/sites-cloud/administering/content-fragments/overview.md#content-fragments-console) gebruiken om **Modellen van het Fragment van de Inhoud te selecteren** als middeltype aan mening, doorbladeren en leiden:

![ de console van Fragmenten van de Inhoud - navigatie ](/help/sites-cloud/administering/content-fragments/assets/cf-console-models-navigation.png)

Hiermee wordt de weergave voor Modellen van inhoudsfragmenten geopend:

![ de console van Fragmenten van de Inhoud - het Leiden Modellen van het Fragment van de Inhoud ](assets/cf-managing-content-fragment-models.png)

Hier kunt u zien dat er drie hoofdgebieden zijn:

* De bovenste werkbalk
   * Biedt standaard AEM-functionaliteit
   * Ook uw IMS-organisatie tonen
   * Verstrekt diverse [ acties ](#actions-unselected)
* Het linkerdeelvenster
   * Toont de [ wegen aan alle configuraties ](/help/sites-cloud/administering/content-fragments/setup.md#enable-content-fragment-functionality-configuration-browser) die als omslagen worden vermeld
   * Hier kunt u de mappenstructuur verbergen of weergeven
   * U kunt een specifieke map van de boomstructuur selecteren
   * Dit kan worden aangepast om geneste mappen (subconfiguraties) weer te geven
   * Naast de Modellen van het Fragment van de Inhoud, kunt u [ Fragmenten van de Inhoud ](/help/sites-cloud/administering/content-fragments/managing.md) of [ Assets ](/help/sites-cloud/administering/content-fragments/assets-content-fragments-console.md) bekijken; u kunt, verbindingen aan de panelen ook comprimeren of uitbreiden
* Het hoofd-/rechterdeelvenster - vanaf hier kunt u:
   * Zie de lijst met alle modellen van inhoudsfragmenten in de geselecteerde map:
      * De Modellen van het Fragment van de inhoud van de geselecteerde omslag, en alle subfolders zullen worden getoond:
         * De plaats wordt aangegeven door de broodkruimels; deze kunnen ook worden gebruikt om de plaats te veranderen:
      * [Informatie wordt over elk model weergegeven](#information-content-fragment-models)
         * [U kunt selecteren welke kolommen u wilt weergeven](#select-columns-console)
      * [ de Diverse gebieden van informatie ](#information-content-fragment-models) over een Model van het Fragment van de Inhoud verstrekken verbindingen; afhankelijk van het gebied, kunnen deze:
         * Open het juiste model in de editor
         * Informatie weergeven over het pad naar de configuratie
         * Informatie weergeven over de status van het model
      * [ Bepaalde andere gebieden van informatie ](#information-content-fragments) over een Model van het Fragment van de Inhoud kan voor [ Snelle het Filtreren ](#fast-filtering) worden gebruikt:
         * Selecteer een waarde in de kolom en deze wordt direct toegepast als filter
         * Het snelle filtreren wordt gesteund voor **Gewijzigd door**, **Gepubliceerd door** en **Status** column.s
      * Als u de muisaanwijzer op de kolomkoppen gebruikt, worden een vervolgkeuzelijst met handelingen en schuifregelaars voor de breedte weergegeven. Met deze opties kunt u:
         * Sorteren - selecteer de gewenste actie voor oplopend of aflopend
Hiermee wordt de hele tabel gesorteerd op basis van die kolom. Sorteren is alleen beschikbaar voor de desbetreffende kolommen.
         * De grootte van de kolom wijzigen - met de actie of de breedtegraadregelaars
      * Selecteer één, of meer, modellen voor verdere [ actie ](#actions-selected-content-fragment-models)
   * Open het [ paneel van de Filter ](#filter-content-fragment-models)
   * Een selectie van [ toetsenbordkortere weg ](/help/sites-cloud/administering/content-fragments/keyboard-shortcuts.md) is beschikbaar voor gebruik in deze console

## De informatie over uw modellen van het Fragment van de Inhoud wordt verstrekt die {#information-content-fragment-models}

Het hoofd/juiste paneel (lijstmening) van de console verstrekt een waaier van informatie over uw Modellen van het Fragment van de Inhoud. Sommige punten verstrekken ook directe verbindingen aan verdere acties en/of informatie:

* **Naam**
   * Verstrekt een verbinding om het model in de redacteur te openen.
* Vergrendeld
   * Wanneer het model is vergrendeld, wordt dit aangegeven met een hangslotpictogram.
* **Weg**
   * Verstrekt de weg als verbinding om de configuratie in de console te openen.
Als u de muis boven de mapnaam houdt, wordt het JCR-pad weergegeven.
* **Status**
   * Alleen informatie.
   * Kan voor [ Snelle het Filtreren ](#fast-filtering) worden gebruikt
* **Gewijzigd**
   * Alleen informatie.
* **gewijzigd door**
   * Alleen informatie.
   * Kan voor [ Snelle het Filtreren ](#fast-filtering) worden gebruikt.
* **Markeringen**
   * Alleen informatie.
   * Hiermee worden alle codes weergegeven die betrekking hebben op het model.
   * Kan voor [ Snelle het Filtreren ](#fast-filtering) worden gebruikt.
* **die bij** wordt gepubliceerd
   * Alleen informatie.
* **die door** wordt gepubliceerd
   * Alleen informatie.
   * Kan voor [ Snelle het Filtreren ](#fast-filtering) worden gebruikt.

## Modeleigenschappen {#model-properties}

Wanneer u een specifiek model selecteert, worden de eigenschappen van dat model getoond (zoals bepaald wanneer [ creërend het model ](#creating-a-content-fragment-model)). Als het model niet **Vergrendeld** is, dan kunnen sommige punten worden bijgewerkt. U kunt het informatiepictogram (naast de model **Titel**) ook gebruiken om dit informatiepaneel te openen en te sluiten.

![ de console van Fragmenten van de Inhoud - Informatie voor een geselecteerd Model van het Fragment van de Inhoud ](assets/cf-managing-content-fragment-models-selected.png)

* **[Weg](/help/sites-cloud/administering/content-fragments/setup.md#enable-content-fragment-functionality-configuration-browser)**
* **[Status](#enabling-a-content-fragment-model)**
* **Titel**
* **Markeringen**
* **Beschrijving**
* **het patroon van URL van de Voorproef**

  De Modellen van het Fragment van de inhoud staan auteurs toe om **** hun inhoud in een externe frontend toepassing voor te vertonen. Zodra de **Dienst van de Voorproef** wordt gevormd, voeg URL voor de frontend toepassing toe.

  De voorbeeld-URL moet dit patroon volgen:
    `https://<preview_url>?param=${expression}`

  Beschikbare expressies zijn:

   * `${contentFragment.path}`
   * `${contentFragment.model.path}`
   * `${contentFragment.model.name}`
   * `${contentFragment.variation}`
   * `${contentFragment.id}`

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

## Handelingen {#actions}

Nadat u een map hebt geselecteerd (in het linkerdeelvenster), kunt u een reeks handelingen gebruiken, rechtstreeks of na het selecteren van een specifiek model:

* De diverse acties zijn direct [ beschikbaar bij de console ](#actions-unselected)
* U kunt [ selecteren één, of meer, Modellen van het Fragment van de Inhoud om aangewezen acties ](#actions-selected-content-fragment) te tonen

### Handelingen (niet geselecteerd) {#actions-unselected}

Bepaalde acties zijn beschikbaar op de console - nadat u een map hebt geselecteerd, maar zonder een specifiek inhoudsfragmentmodel te selecteren:

* **[creeer](#creating-a-content-fragment-model)** een nieuw (leeg) model

### Handelingen voor een inhoudsfragmentmodel in de inhoudsfragmentconsole {#actions-selected-content-fragment-models}

Als u een specifiek model selecteert, wordt een werkbalk geopend die is toegespitst op de acties die beschikbaar zijn voor dat model. U kunt ook meerdere modellen selecteren. De beschikbare acties worden dienovereenkomstig aangepast.

* **[geeft](/help/sites-cloud/administering/content-fragments/content-fragment-models.md)** uit om uw Model van het Fragment van de Inhoud te bepalen.
* **publiceer** aan of [ publiceer ](/help/implementing/cloud-manager/manage-environments.md#environment-types) of [ Voorproef ](/help/implementing/cloud-manager/manage-environments.md#access-preview-service) rijen.
* **Slot**/**ontgrendelt** om te controleren of een gebruiker wordt toegestaan om het Model te wijzigen.
* **[laat](#enabling-a-content-fragment-model)** toe/**[](#disabling-a-content-fragment-model)** onbruikbaar maken om te controleren of een gebruiker wordt toegestaan om tot Inhoudsfragmenten te leiden die op dit model worden gebaseerd.

Het selecteren van één enkel model toont ook de [ modeleigenschappen ](#properties) in het juiste paneel.

## Kolommen selecteren die worden weergegeven in de console {#select-columns-console}

Zoals met andere consoles kunt u de kolommen vormen die zichtbaar, en beschikbaar voor actie zijn:

![ de console van Fragmenten van de Inhoud - kolomconfiguratie ](assets/cf-managing-console-column-icon.png)

Dit zal een lijst van kolommen voorstellen die u kunt verbergen of tonen:

![ de console van Fragmenten van de Inhoud - kolomconfiguratie ](assets/cf-managing-content-fragment-models-column-selection.png)

## Filtercontentfragmentmodellen {#filter-content-fragment-models}

Het deelvenster Filter biedt de volgende opties:

* een selectie van de voorspelling;
   * waaronder statusvelden, tags, gebruikers
   * een of meer voorspelden kunnen worden geselecteerd en gecombineerd om het filter te maken

<!--
* the opportunity to **Save** your filter
* the option to retrieve a saved search filter for reuse
-->

Zodra geselecteerd, wordt het **Filtreren door** opties getoond (bij de bovenkant van het belangrijkste paneel). Ze kunnen van daaruit worden geschrapt. Bijvoorbeeld:

![ de console van Fragmenten van de Inhoud - het Filtreren Modellen van het Fragment van de Inhoud ](assets/cf-managing-content-fragment-models-filter.png)

### Snel filteren {#fast-filtering}

U kunt ook een voorspelling selecteren door op een specifieke kolomwaarde in de lijst te klikken. U kunt een of meer waarden selecteren om voorspellingen te combineren.

Bijvoorbeeld, selecteer **Toegelaten** in de **3} kolom van de Status {.** Wanneer deze optie is geselecteerd, wordt deze weergegeven als een filtervoorspelling en wordt de lijst dienovereenkomstig gefilterd.

>[!NOTE]
>
>Het snelle filtreren wordt slechts gesteund voor de **Status**, **Gewijzigd door**, **Markeringen**, en **Gepubliceerd door** kolommen.

>[!NOTE]
>
>Het snelle Filteren werkt op de zelfde manier zoals voor [ Fragmenten van de Inhoud ](/help/sites-cloud/administering/content-fragments/managing.md#fast-filtering) in de console.

## Een inhoudsfragmentmodel maken {#creating-a-content-fragment-model}

1. Navigeer aan de omslag aangewezen aan uw [ configuratie, of subconfiguration ](/help/sites-cloud/administering/content-fragments/setup.md).
1. Het gebruik **creeert** om de dialoog te openen.

   >[!CAUTION]
   >
   >**creeer** optie zal slechts beschikbaar zijn:
   >
   >* Als het [ gebruik van de Modellen van het Fragment van de Inhoud ](/help/sites-cloud/administering/content-fragments/setup.md) is toegelaten
   >* als u de map hebt geselecteerd waarin u het model wilt maken.

1. Selecteer het **Weg** aan de configuratie en specificeer de **Naam**.

   >[!NOTE]
   >
   >De configuratie wordt automatisch ingevuld met de huidige configuratie (de map waarin u zich momenteel bevindt).
   >
   >U kunt de configuratie ook wijzigen door op het mappictogram te klikken.

   U kunt ook verschillende eigenschappen definiëren:

   * **Titel**
Als u eerst de **Titel** ingaat, zal de **Naam** van dat worden geproduceerd.
   * a **Beschrijving**
   * **laat model** toe [ laat het model ](#enabling-disabling-a-content-fragment-model) toe

   >[!NOTE]
   >
   >Zie [ Model van het Fragment van de Inhoud - Eigenschappen ](#model-properties) voor volledige details.

   ![ Titel en beschrijving ](assets/cf-managing-content-fragment-models-create.png)

1. Het gebruik **creeert** om het lege model te bewaren, of **creeert en opent**.

### Een inhoudsfragmentmodel inschakelen {#enabling-a-content-fragment-model}

Nadat een model is gemaakt, moet het zijn ingeschakeld zodat het:

* Deze optie is beschikbaar voor selectie wanneer u een inhoudsfragment maakt.
* Er kan vanuit een inhoudsfragmentmodel naar worden verwezen.
* Is beschikbaar aan GraphQL; zo wordt het schema geproduceerd.

U kunt **** een model toelaten:

* Bij het maken van een nieuw model
   * Er wordt een optie weergegeven in het dialoogvenster.
* Wanneer een model **** specifiek is onbruikbaar gemaakt
   * Wanneer het vereiste Model wordt geselecteerd, **laat** actie toe is beschikbaar in de hoogste toolbar.

### Een inhoudsfragmentmodel uitschakelen {#disabling-a-content-fragment-model}

Een model kan ook worden uitgeschakeld, zodat:

* Het model is niet meer beschikbaar als basis voor het creëren van *nieuwe* Fragmenten van de Inhoud.
* Echter:
   * Het GraphQL-schema wordt steeds gegenereerd en kan nog steeds worden opgevraagd (om te voorkomen dat JSON API wordt beïnvloed).
   * Om het even welke die Inhoudsfragmenten van het model worden gebaseerd kunnen nog van het eindpunt van GraphQL worden gevraagd en zijn teruggekeerd.
* Er kan niet meer naar het model worden verwezen, maar bestaande verwijzingen blijven ongewijzigd en kunnen nog steeds worden opgevraagd en geretourneerd vanaf het GraphQL-eindpunt.

Om een Model onbruikbaar te maken dat als **Toegelaten** wordt gemarkeerd, gebruikt u **onbruikbaar maken** optie van:

* De bovenste werkbalk als het vereiste model is geselecteerd.

## Modellen voor inhoudsfragmenten toestaan in uw Assets-map {#allowing-content-fragment-models-assets-folder}

Om inhoudsbeheer uit te voeren, kunt u **Beleid** op de omslag van Assets vormen om te controleren welke Modellen van het Fragment van de Inhoud voor de verwezenlijking van het Fragment in die omslag worden toegestaan.

>[!NOTE]
>
>Het mechanisme is gelijkaardig aan [ toestaand paginasjablonen ](/help/sites-cloud/authoring/page-editor/templates.md#allowing-a-template-author) voor een pagina, en zijn kinderen, in geavanceerde eigenschappen van een pagina.

Om het **Beleid** voor **toegelaten Modellen van het Fragment van de Inhoud te vormen**:

1. Navigeer en open **Eigenschappen** voor de vereiste omslag van Assets.

1. Open het **Beleid** lusje, waar u kunt vormen:

   * **Overgenomen van`<folder>`**

     Het beleid wordt automatisch geërft wanneer het creëren van nieuwe kindomslagen; het beleid kan (en de erfenis gebroken) worden opnieuw gevormd als subfolders modellen moeten toestaan verschillend aan de ouderomslag.

   * **Toegestane Modellen van het Fragment van de Inhoud door Weg**

     U kunt meerdere modellen toestaan.

   * **Toegestane Modellen van het Fragment van de Inhoud door Markering**

     U kunt meerdere modellen toestaan.

   ![ Beleid van het Model van het Fragment van de Inhoud ](assets/cf-cfmodels-policy-assets-folder.png)

1. **sparen** om het even welke veranderingen.

De modellen van inhoudsfragmenten die zijn toegestaan voor een map, worden als volgt opgelost:

* Het **Beleid** voor **Toegestane Modellen van het Fragment van de Inhoud**.
* Als dit leeg is, kunt u het beleid bepalen met behulp van de overervingsregels.
* Als de overervingsketen geen resultaat levert, dan bekijk de **configuratie van de Diensten van de Wolk** voor die omslag (ook eerst direct en dan via overerving).
* Als geen van de bovenstaande resultaten worden behaald, zijn er geen modellen toegestaan voor die map.

<!--
## Deleting a Content Fragment Model {#deleting-a-content-fragment-model}

>[!CAUTION]
>
>Deleting a Content Fragment model can impact dependent fragments.

To delete a Content Fragment model:

1. Navigate to, and select your Content Fragment Model. You can select multiple models.

1. Select **Delete** from the toolbar.

   >[!NOTE]
   >
   >If the model is referenced a warning is given, so that you can take appropriate action.
-->

## Een inhoudsfragmentmodel publiceren {#publishing-a-content-fragment-model}

Modellen van inhoudsfragmenten moeten worden gepubliceerd wanneer/voordat afhankelijke inhoudsfragmenten worden gepubliceerd.

Een inhoudsfragmentmodel publiceren:

1. Navigeer naar en selecteer het inhoudsfragmentmodel. U kunt meerdere modellen selecteren.

1. Selecteer **publiceren** van de toolbar.

1. In de Publish dialoog selecteert de **Bestemming**:

   * **de Publish dienst**
   * **de dienst van de Voorproef**

1. De workflow voor het publiceren van de geselecteerde modellen en de bijbehorende referenties wordt gestart. De gepubliceerde status wordt dan getoond in de console.

<!--
## Unpublishing a Content Fragment Model {#unpublishing-a-content-fragment-model}

Content Fragment Models can be unpublished if they are not referenced by any fragments.

To unpublish a Content Fragment Model:

1. Navigate to, and select your Content Fragment Model.
1. Select **Unpublish** from the toolbar.
   The published status is indicated in the console. 

If you try to unpublish a model that is currently used by one or more fragments, then an error warning is shown. For example: 

![Content Fragment Model error message when unpublishing a model that is in use](assets/cf-cfmodels-unpublish-error.png)

The message suggests that you check the [References](/help/sites-cloud/authoring/basic-handling.md#references) panel to investigate further:

![Content Fragment Model in References](assets/cf-cfmodels-references.png)
-->

## Vergrendelde modellen van inhoudsfragmenten {#locked-content-fragment-models}

Met deze functie kunt u bepalen of een model kan worden bijgewerkt, maar het biedt ook beheer voor modellen van inhoudsfragmenten die zijn gepubliceerd.

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

Om deze kwesties te richten, zijn de Modellen van het Fragment van de Inhoud *gesloten* in een LEZEN-ONLY wijze op auteur - zodra zij zijn gepubliceerd. Deze status wordt vermeld door **Vergrendelde**.

Wanneer het model **Vergrendeld** (op LEZEN-ONLY wijze) is, kunt u de inhoud en de structuur van modellen zien maar u kunt hen niet uitgeven.

U kunt **Vergrendelde** modellen van of de console, of modelredacteur beheren:

* Console

  Van de console, kunt u de LEZEN-ONLY wijze met **leiden ontgrendelt** en **ontgrendelt** acties in de toolbar.

   * U kunt **een model ontgrendelen** om uitgeeft toe te laten.

     Als u **** selecteert ontgrendel wordt een waarschuwing getoond, en u moet de **ontgrendelen** actie bevestigen.

     Vervolgens kunt u het model openen en bewerken.

   * U kunt **het model ook** Slot achteraf.
   * Het herpubliceren van het model keert het onmiddellijk aan **Vergrendelde** (LEZEN-ONLY) wijze terug.

* Modeleditor

   * Wanneer u een model opent dat wordt gesloten zult u worden gewaarschuwd, en met drie acties voorgesteld: **annuleert**, **Gelezen Mening**, **geeft** uit.

   * Als u **Mening slechts** selecteert, kunt u de inhoud en de structuur van het model zien.

   * Als u **uitgezocht geef** uit, kunt u uw updates uitgeven en opslaan:

     ![ geef uit - het gesloten Model van het Fragment van de Inhoud ](assets/cf-cfmodels-editor-locked-edit.png)

     >[!NOTE]
     >
     >Mogelijk staat er nog een waarschuwing boven aan het scherm, maar dat is wanneer het model al wordt gebruikt door bestaande inhoudsfragmenten.

   * **annuleert** keert u aan de console terug.
