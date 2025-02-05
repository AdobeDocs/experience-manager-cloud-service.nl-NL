---
title: Responsieve lay-out
description: Met AEM kunt u een responsieve lay-out voor uw pagina's maken
exl-id: 87202742-5bed-4e87-a427-456a1a0e72cc
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '1740'
ht-degree: 5%

---

# Responsieve lay-out {#responsive-layout}

AEM laat u een ontvankelijke lay-out voor uw pagina&#39;s door de **component van de Container van de Lay-out te gebruiken 0} hebben.**

Dit biedt een alineasysteem waarmee u componenten binnen een responsief raster kunt plaatsen. Met dit raster kunt u de lay-out opnieuw rangschikken op basis van de grootte en de indeling van het apparaat/venster. De component wordt gebruikt samen met de **wijze van de Lay-out[** ](/help/sites-cloud/authoring/page-editor/introduction.md#mode-selector), die u laat uw ontvankelijke lay-out afhankelijk van apparaat tot stand brengen en uitgeven.

De container layout:

* Biedt een horizontale uitlijning op het raster, samen met de mogelijkheid om componenten naast elkaar in het raster te plaatsen en te bepalen wanneer ze moeten samenvouwen/opnieuw plaatsen.
* Gebruikt vooraf gedefinieerde onderbrekingspunten (bijvoorbeeld voor telefoon, tablet, enzovoort) om het vereiste gedrag van inhoud voor verwante apparaten/oriëntatie te definiëren.
   * U kunt bijvoorbeeld de grootte van de component aanpassen of de component zichtbaar is op bepaalde apparaten.
* Kan worden genest om kolombesturing toe te staan.

De gebruiker kan dan zien hoe de inhoud wordt gerenderd voor specifieke apparaten met behulp van de emulator.

AEM realiseert responsieve lay-out voor uw pagina&#39;s gebruikend een combinatie mechanismen:

* **](#adding-a-layout-container-and-its-content-edit-mode)component van de Container van 0} Lay-out[**

  Deze component is beschikbaar in [ componentenbrowser ](/help/sites-cloud/authoring/page-editor/editor-side-panel.md#components-browser) en verstrekt een net-paragraaf systeem om u toe te staan om componenten binnen een ontvankelijk net toe te voegen en te plaatsen. Deze kan ook als het standaardalineasysteem op de pagina worden ingesteld.

* [**Lay-outmodus**](/help/sites-cloud/authoring/page-editor/introduction.md#mode-selector)

  Zodra de lay-outcontainer op uw pagina wordt geplaatst kunt u de **wijze van de Lay-out** gebruiken om inhoud binnen het ontvankelijke net te plaatsen.

* [**Emulator**](#selecting-a-device-to-emulate)
Zo kunt u responsieve websites maken en bewerken die de lay-out op basis van de grootte van het apparaat of venster opnieuw rangschikken door de grootte van componenten interactief aan te passen. De gebruiker kan dan zien hoe de inhoud wordt gerenderd met de emulator.

Met deze responsieve rastermechanismen kunt u:

* Gebruik onderbrekingspunten om verschillende inhoudslay-outs te definiëren op basis van de apparaatbreedte (afhankelijk van het apparaattype en de oriëntatie).
* Gebruik dezelfde onderbrekingspunten en inhoudelay-outs om ervoor te zorgen dat de inhoud reageert op de grootte van het browservenster op het bureaublad.
* Gebruik Horizontaal magnetisch raster om componenten in het raster te plaatsen, de grootte desgewenst aan te passen en te bepalen wanneer ze naast elkaar of boven/onder moeten samenvouwen/opnieuw moeten plaatsen.
* Componenten verbergen voor specifieke apparaatlay-outs.
* Kolombesturingselement realiseren.

Afhankelijk van uw project, zou de Container van de Lay-out als standaardparagraafsysteem voor uw pagina&#39;s of als component beschikbaar kunnen worden gebruikt om aan uw pagina door componentenbrowser (of allebei) worden toegevoegd.

>[!TIP]
>
>Adobe verstrekt [ documentatie GitHub ](https://adobe-marketing-cloud.github.io/aem-responsivegrid/) van de ontvankelijke lay-out als verwijzing die aan front-end ontwikkelaars kan worden gegeven die hen toestaan om het AEM net buiten AEM te gebruiken, bijvoorbeeld, wanneer het creëren van statische HTML mock-ups voor een toekomstige AEM plaats.

>[!NOTE]
>
>Het gebruik van de bovenstaande mechanismen wordt ingeschakeld door configuratie op de sjabloon. Gelieve te zien het document [ Vormend Responsieve Lay-out ](/help/sites-cloud/administering/responsive-layout.md) voor verdere informatie.

## Lay-outdefinities, Apparaatemulatie en Onderbrekingspunten {#layout-definitions-device-emulation-and-breakpoints}

Wanneer u uw website-inhoud maakt, moet u ervoor zorgen dat uw inhoud correct wordt weergegeven voor het apparaat dat wordt gebruikt om de inhoud weer te geven.

Met AEM kunt u lay-outs definiëren die afhankelijk zijn van de breedte van het apparaat:

* Met de emulator kunt u deze lay-outs emuleren op een reeks apparaten. Naast het apparatentype, kan de richtlijn, die door de **wordt geselecteerd het apparaat van de Roteren** optie, het breekpunt beïnvloeden dat wordt geselecteerd aangezien de breedte verandert.
* Onderbrekingspunten zijn de punten die de layoutdefinities scheiden.
   * Ze definiëren in feite de maximale breedte (in pixels) van elk apparaat met een specifieke layout.
   * De onderbrekingspunten zijn gewoonlijk geldig voor een selectie van apparaten, afhankelijk van de breedte van hun vertoningen.
   * Het bereik van een onderbrekingspunt loopt door tot het volgende onderbrekingspunt.
   * U kunt het onderbrekingspunt niet specifiek selecteren, zal selecteren een apparaat en de richtlijn automatisch het aangewezen breekpunt selecteren.

Het apparaat **Desktop**, dat geen specifieke breedte heeft, heeft op het standaardbreekpunt (namelijk alles boven het laatste gevormde breekpunt) betrekking.

>[!NOTE]
>
>Het zou mogelijk zijn om breekpunten voor elk individueel apparaat te bepalen, maar dit zou drastisch de inspanning die voor lay-outdefinitie en onderhoud wordt vereist verhogen.

Wanneer u de emulator gebruikt, selecteert u een specifiek apparaat voor emulatie- en layoutdefinitie en wordt het verwante onderbrekingspunt ook gemarkeerd. Wijzigingen in de layout zijn van toepassing op andere apparaten waarop het onderbrekingspunt van toepassing is. Namelijk om het even welke apparaten die aan de linkerzijde van de actieve breekpuntteller worden geplaatst, maar vóór de volgende breekpuntteller.

Bijvoorbeeld, wanneer u het apparaat **iPhone 6 plus** (die met een breedte van 540 pixel wordt bepaald) voor wedijver en lay-out selecteert, wordt de breekpunt **Telefoon** (die als 768 pixel wordt bepaald) geactiveerd ook. Om het even welke lay-outveranderingen u voor **iPhone 6** aanbrengt zijn van toepassing op andere apparaten onder **Telefoons** breekpunt, zoals **iPhone 5** (die als 320 pixel wordt bepaald).

![ Emulators ](/help/sites-cloud/authoring/assets/responsive-layout-emulators.png)

## Een apparaat selecteren om te emuleren {#selecting-a-device-to-emulate}

1. Open de vereiste pagina om te bewerken. Bijvoorbeeld:

   `http://<host>:<port>/editor.html/content/wknd/en/sports/la-skateparks.html`

1. Selecteer het **pictogram van de Mededinger** van de hoogste toolbar:

   ![ knoop van de Mededinger ](/help/sites-cloud/authoring/assets/emulator.png)

1. De emulatorwerkbalk wordt geopend.

   ![ toolbar van de Mededinger ](/help/sites-cloud/authoring/assets/responsive-layout-emulator-toolbar.png)

   Op de emulatorwerkbalk worden extra layoutopties weergegeven:

   * **roteer apparaat** - laat u een apparaat van verticale (staande) richtlijn aan horizontale (landschaps) richtlijn roteren en omgekeerd.

   ![ roteer apparaat liggend knoop ](/help/sites-cloud/authoring/assets/responsive-layout-rotate-device-landscape-button.png)
   ![ roteer apparatenportretknoop ](/help/sites-cloud/authoring/assets/responsive-layout-rotate-device-portrait-button.png)

   * **Uitgezochte Apparaat** - bepaal een specifiek apparaat om van een lijst (zie volgende stap voor details) na te streven

   ![ Uitgezochte knoop van het Apparaat ](/help/sites-cloud/authoring/assets/responsive-layout-select-device-button.png)

1. Als u een specifiek apparaat wilt selecteren om te emuleren, kunt u:

   * Gebruik het pictogram Apparaat selecteren en selecteer een keuze in een vervolgkeuzelijst.
   * Selecteer de apparaatindicator in de emulatorwerkbalk.

   ![Vervolgkeuzelijst Apparaat selecteren](/help/sites-cloud/authoring/assets/responsive-layout-select-device-dropdown.png)

1. Nadat een specifiek apparaat is geselecteerd, kunt u:

   * Zie de actieve teller voor het geselecteerde apparaat, zoals **iPad.**
   * Zie de actieve teller voor het aangewezen [ breekpunt ](#layout-definitions-device-emulation-and-breakpoints) zoals **Tablet.**
   * De blauwe gestippelde lijn vertegenwoordigt de *plooi* voor het geselecteerde apparaat (hier een **iPhone 6 plus** in landschap).

   ![ vouwt ](/help/sites-cloud/authoring/assets/responsive-layout-fold.png)

   * De vouw kan ook als de onderbreking van de paginalijn (niet om met de [ breekpunten ](#layout-definitions-device-emulation-and-breakpoints) worden verward) voor de inhoud worden beschouwd. Dit wordt voor het gemak weergegeven om aan te geven welk deel van de inhoud de gebruiker op het apparaat ziet voordat hij of zij schuift.
   * De lijn voor de vouw wordt niet getoond als de hoogte van het apparaat dat wordt geëmuleerd hoger is dan de het schermgrootte.
   * De vouw wordt getoond voor het gemak van de auteur en niet op de gepubliceerde pagina getoond.

## Een container voor lay-out en de bijbehorende inhoud toevoegen (modus Bewerken) {#adding-a-layout-container-and-its-content-edit-mode}

A **de Container van de Lay-out** is een paragraafsysteem dat:

* Bevat andere componenten.
* Definieert de layout.
* Hiermee reageert u op wijzigingen.

>[!NOTE]
>
>Als niet reeds beschikbaar, moet de **Container van de Lay-out** uitdrukkelijk [ voor een paragraafsysteem/pagina ](/help/sites-cloud/administering/responsive-layout.md) worden geactiveerd.

1. De **lay-outcontainer** is beschikbaar als standaardcomponent in de [componentbrowser](/help/sites-cloud/authoring/page-editor/editor-side-panel.md#components-browser). Van hier kunt u het aan de vereiste plaats op de pagina slepen waarna u de **Componenten van de Belemmering hier** placeholder kunt zien.
1. Vervolgens kunt u componenten aan de lay-outcontainer toevoegen. Deze componenten bevatten de werkelijke inhoud:

   ![ container van de Lay-out ](/help/sites-cloud/authoring/assets/responsive-layout-add-to-layout-container.png)

## Handeling selecteren en uitvoeren in een container Layout (modus Bewerken) {#selecting-and-taking-action-on-a-layout-container-edit-mode}

Zoals met andere componenten, kunt u selecteren en dan op (besnoeiing, exemplaar, schrapping) een Container van de Lay-out (wanneer in **uitgeven** wijze) handelen:

>[!CAUTION]
>
>Aangezien een lay-outcontainer een paragraafsysteem is, zal het schrappen van de component zowel het lay-outnet als alle componenten (en hun inhoud) schrappen die binnen de container worden gehouden.

1. Als u de muis boven de tijdelijke aanduiding voor het raster houdt of deze selecteert, wordt het actiemenu weergegeven.

   ![ voeg aan de lay-outcontainer ](/help/sites-cloud/authoring/assets/responsive-layout-container.png) toe

   U moet de **Ouder** optie selecteren.

   ![ Bovenliggende knoop ](/help/sites-cloud/authoring/assets/responsive-layout-parent-button.png)

1. Als de lay-outcomponent wordt genest, die de **ouder** optie selecteren stelt een drop-down selectie voor, latend u om de genestelde lay-outcontainer of zijn ouders te selecteren.

   Wanneer u de muis boven de containernamen in de vervolgkeuzelijst plaatst, worden de contouren ervan weergegeven op de pagina.

   * De laagst geneste container voor de layout is blauw.
   * Elke volgende container krijgt een omtrek van een lichtere kleur met blauw.

   ![ Geneste containers ](/help/sites-cloud/authoring/assets/responsive-layout-nested.png)

1. Het volledige raster wordt gemarkeerd met de inhoud ervan. De actietoolbar wordt getoond, van waar u een actie zoals **Schrapping kunt selecteren.**

## Indelingen definiëren (modus Indeling) {#defining-layouts-layout-mode}

>[!NOTE]
>
>U kunt een afzonderlijke lay-out voor elk [ breekpunt ](#layout-definitions-device-emulation-and-breakpoints) (zoals die door geëmuleerd apparatentype en richtlijn wordt bepaald) bepalen.

Om de lay-out van een ontvankelijk net te vormen dat met de Container van de Lay-out wordt uitgevoerd moet u de **wijze van de Lay-out** gebruiken.

**de wijze van de Lay-out** kan op twee manieren worden begonnen.

* Gebruik het [modusmenu op de werkbalk](/help/sites-cloud/authoring/page-editor/introduction.md#mode-selector) en kies de modus **Lay-out**
   * Selecteer de modus **Lay-out** op dezelfde manier als wanneer u schakelt naar de modus **Bewerken** of de modus **Targeting**.
   * De modus **Lay-out** is permanent en u verlaat de modus **Lay-out** pas wanneer u een andere modus selecteert via de moduskiezer.
* Wanneer [ het uitgeven van een individuele component ](/help/sites-cloud/authoring/page-editor/edit-content.md#editing-component-layout).
   * Door de **optie van de Lay-out** in het snelle actiemenu van de component te gebruiken, kunt u op **Lay-out** wijze schakelen.
   * **de wijze van de Lay-out 1} blijft terwijl het uitgeven van de component en keert terug naar** geef **wijze uit zodra de nadruk in een andere component verandert.**

In de lay-outmodus kunt u verschillende handelingen op een raster uitvoeren:

* Wijzig de grootte van de inhoudcomponenten met de blauwe stippen. Het resizing zal altijd breken-aan-net. Bij het wijzigen van de grootte wordt het achtergrondraster weergegeven als hulpmiddel bij de uitlijning:

  ![ Resize componenten ](/help/sites-cloud/authoring/assets/responsive-layout-resizing.png)

  >[!NOTE]
  >
  >De verhoudingen en de verhoudingen worden gehandhaafd wanneer de componenten zoals **Beelden** resized.

* Selecteer een inhoudcomponent, laat de toolbar u:
   * **Ouder** - laat u de volledige component van de lay-outcontainer voor het nemen van actie op het geheel selecteren.
   * **Vloeiend aan nieuwe lijn** - de component wordt bewogen aan een nieuwe lijn, afhankelijk van de ruimte beschikbaar binnen het net.
   * **de component van de Huid** - de component wordt gemaakt onzichtbaar (het kan van de toolbar van de lay-outcontainer worden hersteld).

  ![ de component van de Huid ](/help/sites-cloud/authoring/assets/responsive-layout-hide.png)

* Op **Lay-out** wijze kunt u de **componenten van de Belemmering hier** selecteren om de volledige component te selecteren. De werkbalk wordt weergegeven voor deze modus.

  De werkbalk heeft verschillende opties, afhankelijk van de status van de lay-outcomponent en de onderdelen ervan. Bijvoorbeeld:

   * **Ouder** - selecteer de oudercomponent.

     ![ Bovenliggende knoop ](/help/sites-cloud/authoring/assets/responsive-layout-parent-button.png)

   * **toon verborgen componenten** - openbaart alle of individuele componenten. Het getal geeft aan hoeveel verborgen componenten er momenteel zijn. De teller toont hoeveel componenten verborgen zijn.

     ![ toon verborgen componentenknoop ](/help/sites-cloud/authoring/assets/responsive-layout-show-button.png)

   * **keert breekpuntlay-out** terug - keer aan de standaardlay-out terug. Er wordt geen aangepaste indeling opgelegd.

     ![ keert de knoop van de breekpuntlay-out terug ](/help/sites-cloud/authoring/assets/responsive-layout-revert-button.png)

   * **Vloeiend aan nieuwe lijn** - beweeg de component omhoog een positie als het uit elkaar plaatsen toestaat.

     ![ drijft aan een nieuwe lijnknoop ](/help/sites-cloud/authoring/assets/responsive-layout-float-button.png)

   * **de component van de Huid** - verberg de huidige component.

     ![ de componentenknoop van de Huid ](/help/sites-cloud/authoring/assets/responsive-layout-hide-button.png)

  >[!NOTE]
  >
  >In het bovenstaande voorbeeld zijn de acties voor zweven en verbergen beschikbaar omdat deze container van de layout is genest in een bovenliggende container van de layout.

   * **unhide componenten**
Selecteer de oudercomponenten om de actietoolbar met **te tonen verborgen componenten** optie. In dit voorbeeld zijn twee componenten verborgen.

     ![ unhide componenten ](/help/sites-cloud/authoring/assets/responsive-layout-unhide.png)

  Als u de optie **Verborgen componenten weergeven** selecteert, worden de componenten die momenteel op hun oorspronkelijke positie zijn verborgen, blauw weergegeven.

  ![ herstel alle knoop ](/help/sites-cloud/authoring/assets/responsive-layout-restore-all.png)

  Het selecteren **herstelt alle** zal alle verborgen componenten onthullen.
