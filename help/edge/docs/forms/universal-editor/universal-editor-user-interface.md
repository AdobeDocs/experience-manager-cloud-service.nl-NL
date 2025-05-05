---
title: Universele editor
description: Deze zelfstudie helpt u om aan de slag te gaan met de Universal Editor-interface. Het helpt u bij het begrijpen van de gebruikersinterface om uw eigen Edge Delivery Services-formulieren te maken in de Universal Editor.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 90321e81-bb55-48b2-b329-4944bf926309
source-git-commit: babddee34b486960536ce7075684bbe660b6e120
workflow-type: tm+mt
source-wordcount: '1706'
ht-degree: 0%

---


# De interface van de Universal Editor (WYSIWYG) verkennen

De [ Universele Redacteur ](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) biedt een eenvoudige, visuele, en intuïtieve interface van What You See Is What You Get (WYSIWYG) voor de Diensten van de Levering van de Rand van Adobe Forms aan. Het biedt een moderne interface met functionaliteit voor slepen en neerzetten voor efficiënt ontwerpen van formulieren.

![ Universele Gebruikersinterface van de Redacteur ](/help/edge/docs/forms/universal-editor/assets/universal-editor-interface.png)

## Wat leert u?

Aan het einde van deze zelfstudie gaat u als volgt te werk:

- De belangrijkste componenten van de interface van de Universal Editor begrijpen
- Navigeren met vertrouwen door de verschillende interfacesecties
- Zorg dat u weet hoe u essentiële gereedschappen voor formulieropbouw kunt gebruiken en gebruiken
- Bekend zijn met sneltoetsen die de productiviteit verhogen

## De Universal Editor Interface begrijpen

Wanneer u een formulier bewerkt met de Universal Editor, opent de console een interactieve WYSIWYG-interface waarmee u direct kunt beginnen met bewerken. Deze interface biedt real-time visuele feedback terwijl u werkt, waarbij u precies ziet hoe uw formulier er voor de eindgebruikers uitziet.

>[!NOTE]
>
> Leren hoe te om vormen te schrijven gebruikend de Universele Redacteur, zie het artikel [ Begonnen Worden met Edge Delivery Services voor AEM Forms gebruikend Universele Redacteur (WYSIWYG) ](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md).

![ Universele Gebruikersinterface van de Redacteur ](/help/edge/docs/forms/universal-editor/assets/universal-editor-interface1.png)

De interface van de Universele Redacteur is verdeeld in vier logische delen:

- **[A: De Kopbal van Experience Cloud](#experience-cloud-header)**
- **[B: Universele Toolbar van de Redacteur](#universal-editor-toolbar)**
- **[C: Het Comité van Eigenschappen](#properties-panel)**
- **[D: Redacteur](#editor)**

Laten we elke sectie in detail onderzoeken.

### Experience Cloud-koptekst

De Experience Cloud Header wordt boven aan de console weergegeven en biedt navigatiecontext binnen het bredere Adobe Experience Cloud-ecosysteem. U ziet hier uw huidige locatie en hebt snel toegang tot andere Experience Cloud-toepassingen.

![ Universal Editor Experience Cloud Header ](/help/edge/docs/forms/universal-editor/assets/universal-editor-experience-manager-header.png)

Laten we elke component onderzoeken:

- **Adobe Experience Cloud**

  Het klikken van de **verbinding van Adobe Experience Cloud** op de linkerkant van het scherm staat u toe om aan de wortel van de oplossing van Experience Manager te navigeren. Vanaf dat punt hebt u toegang tot andere gereedschappen, zoals Experience Manager Sites, Experience Manager Assets en Experience Manager Guides.

  ![ Adobe Experience Manager ](/help/edge/docs/forms/universal-editor/assets/universal-editor-experience-manager.png)

- **Naam van de Organisatie**

  De **Naam van de Organisatie** toont de naam van de organisatie van het Systeem van Identity Management (IMS) u momenteel wordt ondertekend in. Als u toegang hebt tot meerdere organisaties, kunt u tussen de organisaties schakelen via dit vervolgkeuzemenu. In de schermafbeelding is de momenteel geselecteerde IMS-organisatie bijvoorbeeld &quot;AEM Forms Internal01&quot;.

  ![ Organisatie ](/help/edge/docs/forms/universal-editor/assets/universal-editor-organization.png)

- **Hulp**

  Met het Help-pictogram hebt u snel toegang tot instructiemiddelen en ondersteuningsbronnen. Dit is met name handig wanneer u problemen tegenkomt of hulp nodig hebt bij specifieke functies. Je kunt ook feedback verzenden via deze sectie.

  ![ Hulp ](/help/edge/docs/forms/universal-editor/assets/ue-help.png)

- **Meldingen**

  De **sectie van Meldingen** toont het aantal momenteel toegewezen onvolledige berichten, verzoeken, en huidige taken in uw organisatie IMS. Als u deze sectie in de gaten houdt, kunt u boven op uw workflow blijven.

  ![ Bericht ](/help/edge/docs/forms/universal-editor/assets/ue-notification.png)

- **Oplossingen**

  Het **menu van Oplossingen** staat u toe om aan andere oplossingen van Adobe Experience Cloud over te schakelen, die het gemakkelijk maken om tussen verschillende hulpmiddelen in uw werkschema te bewegen.

  ![ Oplossingen ](/help/edge/docs/forms/universal-editor/assets/ue-solutions.png)

- **Profiel van de Gebruiker**

  Dit pictogram geeft uw profielgegevens weer, samen met de naam van de IMS-organisatie waarin u momenteel bent aangemeld. Klik op dit pictogram om accountinstellingen en afmeldingsopties te openen.

  ![ Auteur ](/help/edge/docs/forms/universal-editor/assets/ue-author.png)

### Werkbalk Universele editor

De werkbalk bevat essentiële navigatie- en bewerkingsgereedschappen. Hiermee kunt u schakelen tussen formulieren, formulieren publiceren of de publicatie ervan ongedaan maken, formuliereigenschappen bewerken en de regeleditor openen voor het toevoegen van dynamisch gedrag.

![ Universele Toolbar van de Redacteur ](/help/edge/docs/forms/universal-editor/assets/ue-toolbar.png)

Dit is wat elke component aanbiedt:

- **Knop van het Huis**

  Met de knop Home keert u terug naar de startpagina van de Universal Editor. Dit is handig wanneer u aan een ander formulier moet gaan werken. U kunt ook rechtstreeks een URL invoeren op de locatiebalk om naar elk formulier te navigeren dat u wilt bewerken.

  ![ Universeel Huis van de Redacteur ](/help/edge/docs/forms/universal-editor/assets/ue-home.png)

- **de Bar van de Plaats**

  De **Bar van de Plaats** toont het adres van de vorm u momenteel uitgeeft. Als u naar een ander formulier wilt schakelen, klikt u gewoon op de locatiebalk en voert u de URL in. De sneltoets waarmee de locatiebalk focus kan krijgen, is `l` .

  ![ de Bar van de Plaats ](/help/edge/docs/forms/universal-editor/assets/ue-locationbar.png)

- **Redacteur van de Regel**

  De **Redacteur van de Regel** laat u toe om dynamisch gedrag aan uw vormen door een intuïtieve visuele interface toe te voegen. Hiermee kunt u voorwaarden, validaties en handelingen maken die reageren op gebruikersinvoer, waardoor uw formulieren interactief en intelligent worden.

  ![ Redacteur van de Regel ](/help/edge/docs/forms/universal-editor/assets/ue-ruleeditor.png)

  >[!NOTE]
  >
  > - De uitbreiding van de Redacteur van de Regel wordt niet toegelaten door gebrek in Universele Redacteur. Om deze krachtige eigenschap toe te laten, contacteer ons bij [ aem-forms-ea@adobe.com ](mailto:aem-forms-ea@adobe.com) van uw officieel e-mailadres.
  > - Leren om regels tot stand te brengen en te beheren, verwijs naar de artikel [ Inleiding aan de Redacteur van de Regel in de Authoring van WYSIWYG ](/help/edge/docs/forms/universal-editor/rule-editor-universal-editor.md).

- **geef de Eigenschappen van de Vorm uit**

  De **geeft de optie van de Eigenschappen van de Vorm uit** staat u toe om belangrijke vormmontages zoals het Model van de Gegevens van de Vorm (FDM) en publicatiedatum te vormen. Deze eigenschappen beïnvloeden hoe uw formulier zich gedraagt en integreert met back-end systemen.

  ![ geef de Eigenschappen van de Vorm uit ](/help/edge/docs/forms/universal-editor/assets/ue-formproperties.png)

- **Montages van de Kopbal van de Authentificatie**

  De **optie van de Montages van de Kopbal van de Authentificatie** laat u de kopballen van de douaneauthentificatie voor lokale ontwikkelingsdoeleinden plaatsen. Dit is vooral handig wanneer u formulieren test waarvoor verificatiegegevens vereist zijn.

  ![ Kopbal van de Authentificatie ](/help/edge/docs/forms/universal-editor/assets/ue-authenticationheader.png)

- **Responsieve Wijze**

  De **Responsieve eigenschap van de Wijze** staat u toe om te testen hoe uw vorm op verschillende apparaten zal verschijnen. Standaard wordt de editor geopend in de computerlay-out, maar u kunt overschakelen naar de mobiele weergave om ervoor te zorgen dat het formulier bruikbaar en aantrekkelijk blijft op kleinere schermen.

  ![ Responsieve wijze ](/help/edge/docs/forms/universal-editor/assets/ue-responsivemode.png)

- **Modus van de Voorproef 0&rbrace;**

  **de Wijze van de Voorproef** toont precies uw vorm aangezien het zal verschijnen wanneer gepubliceerd. Op deze manier kunt u op dezelfde manier met het formulier werken door op koppelingen en knoppen te klikken als uw gebruikers. Dit is een essentiële stap voordat u publiceert om te controleren of alles naar behoren werkt. Schakelen tussen bewerkings- en voorvertoningsmodi met de sneltoets `p` .

  ![ Voorproef ](/help/edge/docs/forms/universal-editor/assets/ue-preview.png)

- **Open Pagina**

  De **Open knoop van de Pagina** opent uw vorm in een nieuw browser lusje voor voorproef. Dit geeft u een volledig-schermmening van uw vorm zonder de redacteursinterface. De sneltoets voor deze handeling is `o` .

  ![ Open Pagina ](/help/edge/docs/forms/universal-editor/assets/ue-openpage.png)

- **publiceer**

  Zodra uw vorm voor gebruikers klaar is, publiceert **&#x200B;**&#x200B;knoop het live en beschikbaar aan uw publiek. Dit is de laatste stap in de workflow voor het maken van formulieren.

  ![ publiceer ](/help/edge/docs/forms/universal-editor/assets/ue-publish.png)

- **Menu van de Ellipsis**

  Het klikken van de ellips (...) onthult extra opties, met inbegrip van de capaciteit om **&#x200B;**&#x200B;een vorm ongedaan te maken die momenteel levend is. Dit is handig wanneer u een formulier tijdelijk uit openbare toegang moet verwijderen of het moet vervangen door een bijgewerkte versie.

  ![ Ellipsis ](/help/edge/docs/forms/universal-editor/assets/ue-ellipsis.png)

### Deelvenster Eigenschappen

Het **Comité van Eigenschappen** verschijnt op de rechterkant van de interface en toont contextafhankelijke informatie die op wordt gebaseerd wat u in de vorm hebt geselecteerd. Als er geen component is geselecteerd, wordt de algehele formulierstructuur weergegeven.

![ het Comité van Eigenschappen ](/help/edge/docs/forms/universal-editor/assets/ue-properties-panel.png)

Laten we de belangrijkste onderdelen ervan onderzoeken:

- **de Wijze van Eigenschappen**

  De **eigenschappen** wijze toont montages en opties voor uw momenteel geselecteerde component. Hier kunt u afzonderlijke elementen van uw formulier aanpassen aan uw specifieke vereisten. De sneltoets voor het openen van eigenschappen van een geselecteerde component is `d` .

  ![ Eigenschappen ](/help/edge/docs/forms/universal-editor/assets/ue-properties.png)

- **de Boom van de Inhoud**

  De **Boom van de Inhoud** toont de hiërarchische structuur van uw vorm. Deze visuele weergave helpt u te begrijpen hoe componenten in elkaar zijn genest. Wanneer u op een item in de structuur klikt, wordt dit geselecteerd in de editor en wordt naar de desbetreffende locatie geschoven. Dit is vooral handig in complexe formulieren. Schakel de weergave van de inhoudsstructuur in met de sneltoets `f` .

  ![ de boom van de Inhoud ](/help/edge/docs/forms/universal-editor/assets/ue-contenttree.png)

- **produceer Variaties**

  **produceerde Variaties** eigenschap gebruikt kunstmatige intelligentie om verschillende versies van uw vorm tot stand te brengen die op specifieke herinneringen wordt gebaseerd. Zo kunt u experimenteren met verschillende benaderingen en ontwerpen zonder handmatig elke variatie te maken. U kunt vragen stellen via Adobe of door u worden aangepast.

  ![ produceer Variaties ](/help/edge/docs/forms/universal-editor/assets/ue-variations.png)

  >[!NOTE]
  >
  > Voor gedetailleerde instructies bij het gebruiken produceer Variaties voor vormen, verwijs naar [ produceer artikel van Variaties ](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/generative-ai/generate-variations).

- **Experimentatie**

  De **eigenschap van de Experimentatie** staat u toe om gecontroleerde tests in werking te stellen die verschillende vormontwerpen en lay-outs vergelijken. Door te analyseren hoe gebruikers met elke variant communiceren, kunt u gegevensgestuurde beslissingen nemen om de conversiesnelheden en gebruikerservaring te optimaliseren.

  ![ Experimentatie ](/help/edge/docs/forms/universal-editor/assets/ue-experimentation.png)

- **Personalization**

  De **Personalization** montages staan u toe om uw vormen met Adobe Experience Platform (AEP) of externe toepassingen te verbinden. Met deze verbinding kunt u op maat gemaakte formulierervaringen maken op basis van gebruikersgegevens en -gedrag, zodat relevantie en betrokkenheid toenemen.

  ![ Personalization ](/help/edge/docs/forms/universal-editor/assets/ue-personalizaton.png)

- **het Testen A/B**

  **het Testen A/B** helpt u specifieke variaties van uw vorm vergelijken om te bepalen welke beter presteert. In tegenstelling tot bredere experimenten richten A/B-tests zich doorgaans op het vergelijken van specifieke elementen of veranderingen om de meest effectieve optie te identificeren.

  ![ het Testen A/B ](/help/edge/docs/forms/universal-editor/assets/ue-abtesting.png)

- **Het Beheer van de Taak**

  De **eigenschap van het Beheer van de Taak 0&rbrace; stroomlijnt samenwerking door uw team te helpen, taken organiseren volgen en voltooien met betrekking tot vormverwezenlijking en optimalisering.** Dit zorgt ervoor dat projecten efficiënt worden voortgezet met duidelijke verantwoordingsplicht.

  ![ Het Beheer van de Taak ](/help/edge/docs/forms/universal-editor/assets/ue-taskmanagement.png)

- **Inhoudsconcepten**

  De **eigenschap van de Concepten van de Inhoud** staat u toe om inleidende versies van tekstelementen in uw vorm tot stand te brengen en te bewaren. U kunt concepten maken met bestaande formuliertekst of helemaal opnieuw beginnen en deze vervolgens bewerken of verwijderen. Door gebrek, zult u drie concepten zien, maar het klikken **toont Alle** onthult extra concepten.

  ![ Inhoudsconcepten ](/help/edge/docs/forms/universal-editor/assets/ue-contentdraft.png)

- **Gegevens Source**

  De **optie van Gegevens Source** laat u de gegevensbronnen voor uw Model van Gegevens van de Vorm (FDM) vormen en selecteren. Dankzij deze integratie zijn alle gegevensmodelobjecten, -eigenschappen en -services van uw geselecteerde bronnen beschikbaar voor gebruik in het formulier, zodat gegevens dynamisch kunnen worden opgehaald en verzonden.

  ![ Gegevens Source ](/help/edge/docs/forms/universal-editor/assets/ue-datasource.png)

- **voeg toe**

  **voegt** knoop toe openbaart een dropdown lijst van componenten die aan de momenteel geselecteerde container kunnen worden toegevoegd. Als u bijvoorbeeld een sectie Adaptief formulier selecteert, worden in deze lijst alle componenten weergegeven die aan die sectie kunnen worden toegevoegd. De sneltoets voor het openen van deze componentlijst is `a` .

  ![ voeg pictogram ](/help/edge/docs/forms/universal-editor/assets/ue-add.png) toe

- **Dupliceren**

  De **Duplicate** optie leidt tot een nauwkeurige kopie van uw geselecteerde component. Dit bespaart tijd wanneer u veelvoudige gelijkaardige elementen nodig hebt, aangezien u kunt dupliceren en dan wijzigen in plaats van creërend van kras.

  ![ Dupliceer Pictogram ](/help/edge/docs/forms/universal-editor/assets/ue-duplicate.png)

- **Schrapping**

  De **schrapping** optie verwijdert de geselecteerde component uit uw vorm. Wees voorzichtig wanneer u deze optie gebruikt, aangezien het element zonder een bevestigingsprompt direct wordt verwijderd.

  ![ Schrapping ](/help/edge/docs/forms/universal-editor/assets/ue-delete.png)

### Editor

De Editor is de centrale werkruimte waarin u uw formulier maakt en wijzigt. Het formulier dat u opgeeft op de locatiebalk, wordt weergegeven. Het toont een WYSIWYG-ervaring die precies laat zien hoe uw formulier er voor gebruikers uitziet. In de voorbeeldmodus kunt u op dezelfde manier werken met het formulier als uw gebruikers, door navigatie via knoppen en koppelingen te testen.

![ Redacteur ](/help/edge/docs/forms/universal-editor/assets/ue-editor.png)

In de Editor kunt u het grootste deel van uw tijd besteden aan het toevoegen van componenten, het configureren van eigenschappen en het rangschikken van componenten om een intuïtieve, effectieve formulierervaring te creëren.

## Overzicht van sneltoetsen

Houd rekening met de volgende essentiële sneltoetsen om uw productiviteit te verhogen:

- `l` - Focus op de locatiebalk
- `p` - Schakelen tussen bewerkings- en voorvertoningsmodi
- `o` - Het formulier openen op een nieuw tabblad
- `d` - Eigenschappen van de geselecteerde component openen
- `f` - De weergave van de inhoudsboomstructuur in-/uitschakelen
- `a` - De lijst met toe te voegen componenten openen


