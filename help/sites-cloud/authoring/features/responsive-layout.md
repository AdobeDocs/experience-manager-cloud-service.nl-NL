---
title: Responsieve lay-out
description: Met AEM kunt u een responsieve lay-out voor uw pagina's maken
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# Responsieve lay-out {#responsive-layout}

Met AEM kunt u een responsieve lay-out voor uw pagina&#39;s gebruiken met behulp van de **component Layout Container** .

Dit biedt een alineasysteem waarmee u componenten binnen een responsief raster kunt plaatsen. Met dit raster kunt u de lay-out opnieuw rangschikken op basis van de grootte en de indeling van het apparaat/venster. De component wordt gebruikt in combinatie met de modus [**Lay-out **](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes), waarmee u uw responsieve lay-out afhankelijk van het apparaat kunt maken en bewerken.

De container layout:

* Biedt een horizontale uitlijning op het raster, samen met de mogelijkheid om componenten naast elkaar in het raster te plaatsen en te bepalen wanneer ze moeten samenvouwen/opnieuw plaatsen.
* Gebruikt vooraf gedefinieerde onderbrekingspunten (bijvoorbeeld voor telefoon, tablet, enz.) waarmee u het vereiste gedrag van inhoud voor verwante apparaten/oriëntatie kunt definiëren.
   * U kunt bijvoorbeeld de grootte van de component aanpassen of de component zichtbaar is op bepaalde apparaten.
* Kan worden genest om kolombesturing toe te staan.

De gebruiker kan dan zien hoe de inhoud wordt gerenderd voor specifieke apparaten met behulp van de emulator.

AEM realiseert een responsieve indeling voor uw pagina&#39;s met behulp van een combinatie van mechanismen:

* [**Containercomponent **](#adding-a-layout-container-and-its-content-edit-mode)layout

   Deze component is beschikbaar in de [componentenbrowser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser) en verstrekt een net-paragraaf systeem om u toe te staan om componenten binnen een ontvankelijk net toe te voegen en te plaatsen. Deze kan ook als het standaardalineasysteem op de pagina worden ingesteld.

* [**Lay-outmodus **](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes)

   Zodra de lay-outcontainer op de pagina wordt geplaatst, kunt u de wijze van de **Lay-out** gebruiken om inhoud binnen het ontvankelijke net te plaatsen.

* [**Emulator **](#selecting-a-device-to-emulate)Hiermee kunt u responsieve websites maken en bewerken die de lay-out op basis van de grootte van het apparaat/venster opnieuw rangschikken door de grootte van componenten interactief aan te passen. De gebruiker kan dan zien hoe de inhoud wordt gerenderd met de emulator.

Met deze responsieve rastermechanismen kunt u:

* Gebruik onderbrekingspunten om verschillende inhoudslay-outs te definiëren op basis van de apparaatbreedte (afhankelijk van het apparaattype en de oriëntatie).
* Gebruik dezelfde onderbrekingspunten en inhoudelay-outs om ervoor te zorgen dat de inhoud reageert op de grootte van het browservenster op het bureaublad.
* Gebruik Horizontaal magnetisch raster om componenten in het raster te plaatsen, de grootte desgewenst aan te passen en te bepalen wanneer ze naast elkaar of boven/onder moeten samenvouwen/opnieuw moeten plaatsen.
* Componenten verbergen voor specifieke apparaatlay-outs.
* Kolombesturingselement realiseren.

Afhankelijk van uw project, zou de Container van de Lay-out als standaardparagraafsysteem voor uw pagina&#39;s of als component beschikbaar kunnen worden gebruikt om aan uw pagina via componentenbrowser (of allebei) worden toegevoegd.

>[!TIP]
>
>Adobe verstrekt [documentatie](https://adobe-marketing-cloud.github.io/aem-responsivegrid/) GitHub van de ontvankelijke lay-out als verwijzing die aan front-end ontwikkelaars kan worden gegeven die hen toestaan om het net AEM buiten AEM te gebruiken, bijvoorbeeld wanneer het creëren van statische HTML mock-ups voor een toekomstige plaats AEM.

>[!NOTE]
>
>Het gebruik van de bovenstaande mechanismen wordt ingeschakeld door configuratie op de sjabloon. Zie Responsieve lay-out configureren voor meer informatie. <!-- Use of the above mechanisms is enabled by configuration on the template. See [Configuring Responsive Layout](/help/sites-administering/configuring-responsive-layout.md) for further information.-->

## Lay-outdefinities, Apparaatemulatie en Onderbrekingspunten {#layout-definitions-device-emulation-and-breakpoints}

Wanneer u uw website-inhoud maakt, moet u ervoor zorgen dat uw inhoud correct wordt weergegeven voor het apparaat dat wordt gebruikt om de inhoud weer te geven.

Met AEM kunt u lay-outs definiëren die afhankelijk zijn van de breedte van het apparaat:

* Met de emulator kunt u deze lay-outs emuleren op een reeks apparaten. Naast het apparaattype kan de richting, geselecteerd met de optie **Apparaat** roteren, invloed hebben op het geselecteerde onderbrekingspunt wanneer de breedte verandert.
* Onderbrekingspunten zijn de punten die de layoutdefinities scheiden.
   * Ze definiëren in feite de maximale breedte (in pixels) van elk apparaat met een specifieke lay-out.
   * De onderbrekingspunten zijn gewoonlijk geldig voor een selectie van apparaten, afhankelijk van de breedte van hun vertoningen.
   * Het bereik van een onderbrekingspunt loopt door tot het volgende onderbrekingspunt.
   * U kunt het onderbrekingspunt niet specifiek selecteren, zal selecteren een apparaat en de richtlijn automatisch het aangewezen breekpunt selecteren.

Het apparaat **Desktop**, dat geen specifieke breedte heeft, heeft betrekking op het standaardbreekpunt (d.w.z. alles boven het laatst gevormde breekpunt).

>[!NOTE]
>
>Het zou mogelijk zijn om breekpunten voor elk individueel apparaat te bepalen, maar dit zou drastisch de inspanning die voor lay-outdefinitie en onderhoud wordt vereist verhogen.

Wanneer u de emulator gebruikt, selecteert u een specifiek apparaat voor de definitie van emulatie en layout en wordt het desbetreffende onderbrekingspunt ook gemarkeerd. Alle layoutwijzigingen die u aanbrengt, zijn van toepassing op andere apparaten waarop het onderbrekingspunt van toepassing is, dat wil zeggen apparaten die links van de actieve onderbrekingspuntmarkering zijn geplaatst, maar vóór de volgende onderbrekingspuntmarkering.

Wanneer u bijvoorbeeld de **iPhone 6 Plus** van het apparaat (gedefinieerd met een breedte van 540 pixels) selecteert voor emulatie en lay-out, wordt ook de **telefoon** met onderbrekingspunten (gedefinieerd als 768 pixels) geactiveerd. Alle layoutwijzigingen die u aanbrengt voor de **iPhone 6** , zijn van toepassing op andere apparaten onder het onderbrekingspunt **Telefoons** , zoals **iPhone 5** (gedefinieerd als 320 pixels).

![Emulators](/help/sites-cloud/authoring/assets/responsive-layout-emulators.png)

## Een apparaat selecteren om te emuleren {#selecting-a-device-to-emulate}

1. Open de vereiste pagina om te bewerken. Bijvoorbeeld:

   `http://<host>:<port>/editor.html/content/wknd/en/sports/la-skateparks.html`

1. Selecteer het pictogram **Emulator** op de bovenste werkbalk:

   ![Emulator-knop](/help/sites-cloud/authoring/assets/emulator.png)

1. De emulatorwerkbalk wordt geopend.

   ![Emulator, werkbalk](/help/sites-cloud/authoring/assets/responsive-layout-emulator-toolbar.png)

   Op de emulatorwerkbalk worden extra layoutopties weergegeven:

   * **Apparaat** roteren - Hiermee kunt u een apparaat roteren van verticale (staande) richting naar horizontale (liggende) richting en andersom.
   ![De knop Apparaat liggend roteren](/help/sites-cloud/authoring/assets/responsive-layout-rotate-device-landscape-button.png)
   ![De knop Staand apparaat roteren](/help/sites-cloud/authoring/assets/responsive-layout-rotate-device-portrait-button.png)

   * **Selecteer Apparaat** - Definieer een specifiek apparaat dat u wilt emuleren in een lijst (zie de volgende stap voor meer informatie)
   ![Apparaat selecteren, knop](/help/sites-cloud/authoring/assets/responsive-layout-select-device-button.png)

1. Als u een specifiek apparaat wilt selecteren om te emuleren, kunt u:

   * Gebruik het pictogram Apparaat selecteren en selecteer een keuze in een vervolgkeuzelijst.
   * Tik/klik op de apparaatindicator op de emulatorwerkbalk.
   ![Apparaatvervolgkeuzelijst selecteren](/help/sites-cloud/authoring/assets/responsive-layout-select-device-dropdown.png)

1. Nadat een specifiek apparaat is geselecteerd, kunt u:

   * Zie de actieve markering voor het geselecteerde apparaat, zoals **iPad.**
   * Zie de actieve markering voor het juiste [breekpunt](#layout-definitions-device-emulation-and-breakpoints) , zoals **Tablet.**
   * De blauwe stippellijn geeft de *voud* voor het geselecteerde apparaat aan (hier is een **iPhone 6 Plus** liggend).
   ![De vouw](/help/sites-cloud/authoring/assets/responsive-layout-fold.png)

   * De vouwlijn kan ook worden beschouwd als het pagina-regeleinde (niet te verwarren met de [onderbrekingspunten](#layout-definitions-device-emulation-and-breakpoints)) voor de inhoud. Dit wordt voor het gemak weergegeven om aan te geven welk deel van de inhoud de gebruiker op het apparaat ziet voordat hij of zij schuift.
   * De lijn voor de vouwlijn wordt niet weergegeven als de hoogte van het geëmuleerde apparaat groter is dan de schermgrootte.
   * De vouw wordt getoond voor het gemak van de auteur en niet op de gepubliceerde pagina getoond.


## Een container voor lay-out en de bijbehorende inhoud toevoegen (modus Bewerken) {#adding-a-layout-container-and-its-content-edit-mode}

Een **container** voor layout is een alineasysteem dat:

* Bevat andere componenten.
* Definieert de lay-out.
* Hiermee reageert u op wijzigingen.

>[!NOTE]
>
>Als de **container** voor layout nog niet beschikbaar is, moet deze expliciet worden geactiveerd voor een alineasysteem/pagina. <!-- If not already available, the **Layout Container** must be explicitly [activated for a paragraph system/page](/help/sites-administering/configuring-responsive-layout.md).-->

1. De **container** van de Lay-out is beschikbaar als standaardcomponent in Browser [van](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser)Componenten. Van hieruit kunt u het naar de vereiste plaats op de pagina slepen waarna u de Componenten van de **Belemmering hier** placeholder zult zien.
1. Vervolgens kunt u componenten aan de lay-outcontainer toevoegen. Deze componenten bevatten de werkelijke inhoud:

   ![Lay-outcontainer](/help/sites-cloud/authoring/assets/responsive-layout-add-to-layout-container.png)

## Handeling selecteren en uitvoeren in een container Layout (modus Bewerken) {#selecting-and-taking-action-on-a-layout-container-edit-mode}

Net als bij andere componenten kunt u een container van de layout selecteren en vervolgens actie ondernemen (knippen, kopiëren, verwijderen) (in de modus **Bewerken** ):

>[!CAUTION]
>
>Aangezien een lay-outcontainer een paragraafsysteem is, zal het schrappen van de component zowel het lay-outnet als alle componenten (en hun inhoud) schrappen die binnen de container worden gehouden.

1. Als u de muisaanwijzer boven de tijdelijke aanduiding voor het raster houdt of erop tikt, wordt het menu Handeling weergegeven.

   ![Toevoegen aan de lay-outcontainer](/help/sites-cloud/authoring/assets/responsive-layout-container.png)

   U moet de optie **Bovenliggend** selecteren.

   ![Bovenliggende knop](/help/sites-cloud/authoring/assets/responsive-layout-parent-button.png)

1. Als de lay-outcomponent genest is, stelt het selecteren van de optie **Bovenliggend** een drop-down selectie voor, die u toestaat om de genestelde lay-outcontainer of zijn ouder(s) te selecteren.

   Wanneer u de muis boven de containernamen in de vervolgkeuzelijst plaatst, wordt de omtrek van de namen op de pagina weergegeven.

   * De laagst geneste container voor de layout wordt omgeven door een blauwe omtrek.
   * Elke volgende container zal een lichtere schaduw van blauw zijn.
   ![Geneste containers](/help/sites-cloud/authoring/assets/responsive-layout-nested.png)

1. Hierdoor wordt het volledige raster met de inhoud gemarkeerd. De actiewerkbalk wordt weergegeven, waar u een handeling zoals **Verwijderen kunt selecteren.**

## Indelingen definiëren (modus Indeling) {#defining-layouts-layout-mode}

>[!NOTE]
>
>U kunt een afzonderlijke indeling definiëren voor elk [onderbrekingspunt](#layout-definitions-device-emulation-and-breakpoints) (zoals wordt bepaald door het geëmuleerde apparaattype en de stand).

Als u de lay-out wilt configureren van een responsief raster dat met de container voor lay-out is geïmplementeerd, moet u de modus **Lay-out** gebruiken.

**De lay-outmodus** kan op twee manieren worden gestart.

* Gebruik het [modusmenu op de werkbalk](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) en kies de **modus Indeling** .
   * Selecteer de modus **Lay-out** op dezelfde manier als u schakelt naar de modus **Bewerken** of **Doelmodus** .
   * **De modus Lay-out** blijft blijvend en u laat de modus **Lay-out** pas weer los als u een andere modus selecteert via de moduskiezer.
* Wanneer u een afzonderlijke component [bewerkt.](/help/sites-cloud/authoring/fundamentals/editing-content.md#edit-component-layout)
   * Met de optie **Lay-out** in het snelmenu van de component kunt u overschakelen naar de modus **Lay-out** .
   * **De modus Lay-out** blijft bestaan tijdens het bewerken van de component en keert terug naar de modus **Bewerken** als de focus naar een andere component is gewijzigd.

In de lay-outmodus kunt u verschillende handelingen op een raster uitvoeren:

* Wijzig de grootte van de inhoudcomponenten met de blauwe stippen. Het resizing zal altijd breken-aan-net. Wanneer u het formaat van het achtergrondraster wijzigt, wordt dit weergegeven als hulp bij het uitlijnen:

   ![Formaat van componenten wijzigen](/help/sites-cloud/authoring/assets/responsive-layout-resizing.png)

   >[!NOTE]
   >
   >Verhoudingen en verhoudingen blijven behouden wanneer de grootte van componenten zoals **afbeeldingen** wordt gewijzigd.

* Klik/tik op een inhoudscomponent, op de werkbalk kunt u:
   * **Bovenliggend element** - Hiermee kunt u de volledige containercomponent voor de lay-out selecteren om actie te ondernemen over het geheel.
   * **Zweven naar nieuwe regel** - De component wordt naar een nieuwe regel verplaatst, afhankelijk van de ruimte die beschikbaar is in het raster.
   * **Component** verbergen - De component wordt onzichtbaar gemaakt (u kunt deze herstellen vanaf de werkbalk van de container voor de layout).
   ![Component verbergen](/help/sites-cloud/authoring/assets/responsive-layout-hide.png)

* In de modus **Lay-out** kunt u op de componenten voor **slepen hier** tikken of klikken om de volledige component te selecteren. De werkbalk voor deze modus wordt dan weergegeven.

   De werkbalk heeft verschillende opties, afhankelijk van de status van de lay-outcomponent en de onderdelen ervan. Bijvoorbeeld:

   * **Bovenliggend element** - selecteer de bovenliggende component.

      ![Bovenliggende knop](/help/sites-cloud/authoring/assets/responsive-layout-parent-button.png)

   * **Verborgen componenten** tonen - Alle of afzonderlijke componenten zichtbaar maken. Het getal geeft aan hoeveel verborgen componenten er momenteel zijn. De teller toont hoeveel componenten verborgen zijn.

      ![Knop Verborgen componenten tonen](/help/sites-cloud/authoring/assets/responsive-layout-show-button.png)

   * **Vorige layout** van onderbrekingspunten - De standaardlayout herstellen. Dit betekent dat er geen aangepaste indeling wordt opgelegd.

      ![De knop voor de indeling van onderbrekingspunten herstellen](/help/sites-cloud/authoring/assets/responsive-layout-revert-button.png)

   * **Zweven naar nieuwe regel** - De component omhoog verplaatsen als de afstand dit toestaat.

      ![Zweven naar nieuwe regelknop](/help/sites-cloud/authoring/assets/responsive-layout-float-button.png)

   * **Component** verbergen - De huidige component verbergen.

      ![Component-knop verbergen](/help/sites-cloud/authoring/assets/responsive-layout-hide-button.png)
   >[!NOTE]
   >
   >In het bovenstaande voorbeeld zijn de acties voor zweven en verbergen beschikbaar omdat deze container van de layout is genest in een bovenliggende container van de layout.

   * **Onzichtbaar maken componenten** Selecteer de bovenliggende componenten om de actiewerkbalk weer te geven met de optie Verborgen componenten **** tonen. In dit voorbeeld zijn twee componenten verborgen.

      ![Componenten zichtbaar maken](/help/sites-cloud/authoring/assets/responsive-layout-unhide.png)
   Als u de optie Verborgen onderdelen **** tonen selecteert, worden de onderdelen die momenteel op hun oorspronkelijke positie zijn verborgen blauw weergegeven.

   ![Alle knoppen herstellen](/help/sites-cloud/authoring/assets/responsive-layout-restore-all.png)

   Als u Alle **verborgen componenten** herstellen selecteert, worden alle verborgen componenten zichtbaar.
