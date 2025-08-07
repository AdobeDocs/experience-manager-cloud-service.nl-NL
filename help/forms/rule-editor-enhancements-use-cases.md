---
title: Dit artikel schetst diverse gebruiksgevallen voor de regeleditor in een adaptieve vorm op basis van kerncomponenten.
description: In dit artikel worden verschillende gebruiksgevallen voor de regeleditor in een adaptieve vorm op basis van kerncomponenten besproken. De code benadrukt ook hoe aangepaste functies kunnen worden gebruikt om op maat gemaakte regels voor formulieren te maken.
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner, Intermediate
source-git-commit: 4ff533de73fcb91fb2b68cfdb3fd2602645ff7aa
workflow-type: tm+mt
source-wordcount: '1863'
ht-degree: 0%

---

# Verbeteringen in de regeleditor en hoofdletters/kleine letters gebruiken

<span class="preview"> Dit zijn pre-vrijlatingseigenschappen beschikbaar door ons <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html#new-features"> pre-vrijgavekanaal </a>.

Dit artikel introduceert de meest recente verbeteringen aan de regeleditor in Adaptive Forms. Deze updates zijn ontworpen om u te helpen formuliergedrag gemakkelijker te definiëren, zonder aangepaste code te schrijven, en om een dynamischere, responsieve en gepersonaliseerde formulierervaring te maken.

De onderstaande tabel bevat een overzicht van recente verbeteringen aan de regeleditor in Adaptief Forms, samen met een korte beschrijving en de belangrijkste voordelen van elke functie.:

| Verbetering | Beschrijving | Voordelen |
|---|----|---|
| **Bevestiging die de `validate()` methode** gebruikt | Beschikbaar in de functielijst om afzonderlijke velden, deelvensters of het hele formulier te valideren. | - Kortere validatie op deelvenster-, veld- of formulierniveau <br> - Betere gebruikerservaring met gericht foutbericht <br> - Voorkomt dat er vooruitgang wordt geboekt met onvolledige gegevens <br> - Vermindert de fout bij het verzenden van formulieren |
| **Download DOR** | De functie uit-van-de-doos beschikbaar in de regelredacteur om het Document van Verslag (DoR) te downloaden. | - Geen aangepaste ontwikkeling vereist voor het downloaden van DoR <br> - Consistente downloadervaring in verschillende formulieren |
| **Dynamische variabelen** | Maak regels met variabelen die worden gewijzigd op basis van gebruikersinvoer of andere voorwaarden. | - Maakt flexibele regelvoorwaarden mogelijk <br> - Minder behoefte aan dubbele logica <br> - elimineert de vereiste om verborgen velden te maken |
| **Aangepaste op gebeurtenis-gebaseerde regels** | Definieer regels die reageren op aangepaste gebeurtenissen buiten de standaardtriggers. | - Biedt ondersteuning voor gevallen van geavanceerd gebruik <br> - Meer controle over wanneer en hoe regels worden uitgevoerd <br> - Verbetert de interactiviteit |
| **context-bewuste herhaalbare paneeluitvoering** | Regels worden nu uitgevoerd in de juiste context voor elk herhaald deelvenster in plaats van alleen voor de laatste instantie. | - Nauwkeurige regeltoepassing voor elke herhalingsinstantie <br> - Vermindert fouten in dynamische secties <br> - Verbetert gebruikerservaring met herhaalde inhoud |
| **Steun voor vraagkoord, UTM, en browser parameters** | Maak regels die het formuliergedrag aanpassen op basis van URL-parameters of browserspecifieke waarden. | - Schakelt personalisatie op basis van bron of omgeving in <br> - Geschikt voor marketing of tracking-specific flows <br> - Geen noodzaak voor extra scripts of aanpassing |

Verken nu elke methode in detail met specifieke gebruiksgevallen om u te helpen begrijpen hoe deze eigenschappen kunnen worden gebruikt om een gepersonaliseerde ervaring voor gebruikers te leveren

## Methode valideren in functielijst

Verbeterde bevestigingsmogelijkheden die **toelaten bevestigen ()** methode in de functielijst moet worden gebruikt om panelen, gebieden, of volledige vormen te bevestigen. In een aanvraagformulier voor leningen die uit meerdere stappen bestaan, moet u bijvoorbeeld verschillende secties valideren voordat gebruikers kunnen verdergaan met de volgende stap.

**Scenario:** een financiële instelling biedt een multi-step vorm van de leningstoepassing aan waar de gebruikers verschillende secties zoals moeten voltooien:

* Persoonlijke gegevens
* Werkgelegenheidsdetails
* Details van lening
* Controleren en verzenden

Voordat een gebruiker van de ene stap naar de andere gaat, moet het formulier alleen de velden binnen de huidige sectie valideren. De gebruiker mag bijvoorbeeld niet naar &quot;Werkgelegenheidsdetails&quot; gaan, tenzij alle vereiste velden in &quot;Persoonlijke gegevens&quot; correct zijn ingevuld.

**Implementatie die gebruikt bevestigt () in de Redacteur van de Regel**

A **Volgende** knoop in elk paneel brengt een regel teweeg gebruikend **bevestigt ()** methode. De regel controleert of alle velden in het huidige deelvenster geldig zijn. Als de validatie wordt uitgevoerd, gaat het formulier naar het volgende venster. Als dat niet het geval is, worden foutberichten weergegeven die de gebruiker helpen de invoer te corrigeren.

Het schermafbeelding hieronder toont de regel die op **Volgende** knoop wordt toegepast:

![ bevestigt Volgende Knoop ](/help/forms/assets/validate-next.png)

In de bovengenoemde regel, controleert de **Volgende** knoop of de gebieden in de **Persoonlijke sectie van Details** geldig zijn. Als de details niet geldig zijn, beweegt de nadruk zich aan het **gebied van de Naam** in het **Persoonlijke Details** paneel.

![ output ](/help/forms/assets/valid-output.png)

>[!NOTE]
>
> U kunt **gebruiken bevestigt ()** methode op vormen, fragmenten, of individuele gebieden. Wanneer een fragment in een formulier wordt opgenomen, worden zowel het formulier als het fragment als opties weergegeven in de validatiecontext. In dit geval verwijst het fragment naar de velden in het fragment, terwijl het formulier verwijst naar het bovenliggende formulier waarin het fragment is ingesloten.

## DownloadDor als OOTB-functie in de Rule Editor

Gebruikend **DownloadDor ()** out-of-the-box (OOTB) functie in de Redacteur van de Regel, staat gebruiker toe om het Document van Verslag te downloaden, als de vorm wordt gevormd om Document van Recored te produceren.

>[!NOTE]
>
> Als de vorm niet voor Document van Verslag wordt gevormd, wordt een foutenmelding getoond wanneer de regel gebruikend **downloadDoR ()** functie wordt toegepast op de knoop.

**Scenario**: Een overheidsagentschap verstrekt een digitale toepassingsvorm voor het uitgeven van certificaten. Nadat de aanvrager het formulier heeft ingediend, verlangt hij vaak een kopie van het ingevulde formulier ter registratie of deelt hij dit met een andere dienst. Om de gebruikerservaring te verbeteren, wil het agentschap aanvragers de mogelijkheid bieden om een Document of Record (DoR) onmiddellijk na de indiening of in een stadium vóór de definitieve indiening te downloaden.

**Implementatie die DownloadDor () gebruikt in de Redacteur van de Regel**

A **de knoop van de Download** wordt toegevoegd aan vorm gebruikend de Redacteur van de Regel, wordt een regel gevormd om **te teweegbrengen DownloadDor ()** functie wanneer de knoop wordt geklikt.

Het schermafbeelding hieronder toont de regel die op de **downloadt** knoop wordt toegepast:

![ de regel van de Knoop van de Download ](/help/forms/assets/download-button-rule.png)

>[!NOTE]
>
> Het **gebied van de Input** staat de gebruiker toe om het dossier te specificeren - naam voor een downloadbaar document. Dit is een optionele parameter.

Als het formulier is geconfigureerd voor het genereren van doR, genereert en downloadt deze functie de PDF onmiddellijk, zonder dat er een aangepaste functie nodig is.

![ Document van Verslag ](/help/forms/assets/download-dor-output.png)

## Ondersteuning voor dynamische variabelen in regels

De verbeterde regeleditor ondersteunt nu het maken en gebruiken van dynamische (tijdelijke) variabelen. Deze variabelen kunnen door de levenscyclus van de vorm worden geplaatst en worden teruggewonnen gebruikend de ingebouwde **Reeks Variabele Waarde** en **krijgen Variabele functies van de Waarde**.
Deze variabelen:

* Deze gegevens worden niet samen met de formuliergegevens verzonden.
* Kan tussentijdse of berekende waarden bevatten.
* Kan worden gebruikt in voorwaardelijke logica en handelingen.

**Scenario**: Een e-commercebedrijf verstrekt een ordevorm waar de gebruikers een product en een aangewezen het verschepen methode kunnen selecteren. Terwijl de prijs van het product via een formulierveld wordt vastgelegd, worden de verzendkosten dynamisch bepaald op basis van de geselecteerde methode en het gekozen land.

Om de formulierstructuur schoon te houden en onnodige verborgen velden te voorkomen, willen bedrijven de verzendkosten verwerken als een tijdelijke waarde die real-time berekening van het totale bedrag ondersteunt.

**Implementatie die de Vastgestelde Waarde van de Variabele gebruikt en de functies van de Waarde van de Variabele in de Redacteur van de Regel krijgt**

Een regel wordt gevormd om een tijdelijke variabele te plaatsen genoemd **extra lading** gebruikend de **Vastgestelde Variabele functie van de Waarde**. De waarde van deze variabele is afhankelijk van het geselecteerde land. Als de gebruiker bijvoorbeeld &quot;Verenigde Staten&quot; selecteert, wordt de waarde ingesteld op 50. Voor elk ander land is de waarde 100.

![ vastgestelde veranderlijke waarde ](/help/forms/assets/setvalue.png)

Later, wanneer het berekenen van de totale ladingskosten, wint de **Veranderlijke functie van de Waarde** de **extrapolatie** waarde terug die op het geselecteerde land wordt gebaseerd.

![ krijgt veranderlijke waarde ](/help/forms/assets/getvalue.png)

Deze waarde wordt dan toegevoegd aan de het verschepen kosten van het product, en het resultaat wordt getoond op het **Totale gebied van de Kosten van de Verzending**.

![ output ](/help/forms/assets/getsetvalue-output.png)

Op deze manier kunt u extra kosten dynamisch berekenen en weergeven zonder deze in een zichtbaar veld op te slaan, zodat u een schone, responsieve en codevrije gebruikerservaring hebt.


## Ondersteuning voor aangepaste regels op basis van gebeurtenissen

De verbeterde regelredacteur steunt de behandeling van de douanegebeurtenis gebruikend de **Gebeurtenis van de Verzending** en **op de functies van de Gebeurtenis van de Trekker**. Met deze functies kunnen verschillende delen van het formulier communiceren door aangepaste gebeurtenissen uit te zenden en te beluisteren, waardoor een schonere, modulaire logica mogelijk is zonder strakke koppeling van handelingen naar specifieke velden.

**Scenario**: Een vorm van de baantoepassing is geïntegreerd met een extern systeem van u dat achtergrondcontrole uitvoert. Zodra de controle volledig is, werkt het systeem de vorm met de **Voltooide Controle van de Achtergrond bij!** -bericht. Het formulier moet dynamisch aanpassen wat de aanvrager op basis van dit resultaat ziet.

In plaats van logica rechtstreeks te binden aan het veld dat de status ontvangt, gebruikt het formulier een aangepaste, op gebeurtenissen gebaseerde aanpak om de modulariteit en het onderhoud te verbeteren.

**Implementatie die de Gebeurtenis van de Verzending en op de Gebeurtenis van de Trekker gebruiken**

Wanneer de status van de achtergrondcontrole wordt bijgewerkt, gebruikt een regel **Gebeurtenis van de Verzending** om een douanegebeurtenis als **bgvmsg** samen met het statusresultaat uit te zenden. Een afzonderlijke regel luistert naar deze gebeurtenis gebruikend **op de Gebeurtenis van de Trekker**.

In de onderstaande schermafbeeldingen worden de regels weergegeven die zijn toegepast op de optie Is achtergrondverificatie voltooid? keuzerondje en het tekstveld bgvmsg.

![ verzendingsgebeurtenis ](/help/forms/assets/dispatch-event-rule.png)

![ op trekkergebeurtenis ](/help/forms/assets/trigger-event-rule.png)

Wanneer de gebeurtenis wordt gedetecteerd, wordt de status gecontroleerd en wordt het formulier dienovereenkomstig bijgewerkt. Bijvoorbeeld:

* Als de achtergrondcontrole is geslaagd, wordt een bevestigingsbericht weergegeven in het formulier.
* Indien aanvullende documenten nodig zijn, wordt in het formulier een sectie weergegeven waarin de aanvrager wordt verzocht de vereiste informatie te uploaden, samen met een waarschuwingsbericht.

![ de gebeurtenisoutput van de Verzending ](/help/forms/assets/dispatch-trigger-output.png)

Steun voor douanegebeurtenissen die ontwikkelaars toestaan om douanegebeurtenissen tot stand te brengen en teweeg te brengen die als voorwaarden in regelredacteur kunnen worden gebruikt.

## Op context gebaseerde regeluitvoering voor herhalende deelvensters

Adaptieve Forms ondersteunt contextbewuste regeluitvoering voor herhaalbare deelvensters. Op deze manier kunnen regels specifiek worden toegepast op de instantie van het deelvenster waar de gebruiker werkt, in plaats van dat ze alle instanties beïnvloeden of zich aan de laatste instantie aanpassen.

**Scenario**: Een vorm van de productorde laat gebruikers veelvoudige producten in afzonderlijke panelen toevoegen. Elk paneel omvat a **Aantal van het gebied van het Product** en a **Totale Kosten** gebied. Wanneer een gebruiker de hoeveelheid voor een product bijwerkt, moet het formulier de totale prijs opnieuw berekenen, maar alleen voor dat specifieke venster, niet voor alle andere deelvensters.

**Implementatie die Context-Aware Regels in de Redacteur van de Regel gebruikt**

Een regel wordt gevormd op het **Aantal gebied van het Product** binnen het herhaalbare productpaneel.

De hieronder screenshot toont de regel voor het **Aantal van het gebied van het Product** binnen het herhaalbare productpaneel:

![ aantal productregel ](/help/forms/assets/number-of-product-rule.png)

Wanneer de hoeveelheid wordt gewijzigd, haalt de regel de eenheidsprijs van het geselecteerde product op en berekent de totale kosten alleen voor dat paneel.

![ Context bewuste regeloutput ](/help/forms/assets/context-aware-rule-output.png)

## URL- en browserparameterregels in adaptieve Forms

Adaptieve Forms ondersteunt dynamische regeluitvoering met behulp van externe parameters die via de formulier-URL worden doorgegeven of die zijn afgeleid van de browseromgeving van de gebruiker. Dit maakt gepersonaliseerde en context-bewuste formulierervaringen mogelijk op basis van waar de bezoeker vandaan kwam of welk apparaat ze gebruiken.

## Toegestane parametertypen

| Type parameter | Ondersteunde opties | Beschrijving | Voorbeeldwaarde |
| --- | --- | --- | ---|
| Query-parameter | `ref` (alleen tekenreekswaarden) | Algemeen sleutelwaardepaar in URL na `?` | `?ref=partner123` |
| UTM-parameter | UTM Source <br> UTM Medium <br> de Campagne van UTM 1&rbrace; UTM <br> Term van UTM <br> Inhoud UTM | Speciale queryparameters die worden gebruikt voor het bijhouden van campagnes | `?utm_source=google&utm_medium=email` |
| URL-parameter | Hostnaam <br> Weg | Hiermee worden structurele componenten van de formulier-URL opgehaald | `hostname=www.example.com`, `path=/signup` |
| Browserparameter | Browser van de Agent van de Agent <br> Browser Taal <br> Browser Platform | Waarden afgeleid van de browser of het apparaat van de gebruiker | `Browser Agent=Mozilla`, `Language=en-US` |

**Scenario**: Een vorm van de loodgeneratie moet zijn welkomstbericht afhankelijk van de verkeersbron aanpassen. Wanneer een gebruiker op het formulier landt via een Google-advertentiecampagne (met gebruik van utm_source=google in de URL), moet het formulier een aangepaste begroeting weergeven.

**Implementatie die Parameter UTM gebruikt**

Een regel wordt gevormd op een tekstgebied dat douanebericht aan de gebruikers van Google toont en het gebruikt **utm_source** parameter.

In de onderstaande schermafbeelding wordt de regel weergegeven die op het tekstbericht is geconfigureerd:

![ regel op tekstbericht ](/help/forms/assets/utm-param-rule.png)

Als de **utm_source** parameterwaarde &quot;google&quot;evenaart, een douanebericht zoals &quot;de gebruikers van Google van Hello, welkom aan de Campagne Ad!&quot; wordt weergegeven.

![ utm-param-output ](/help/forms/assets/utm-param-output.png)

Op deze manier kunnen marketers relevante inhoud leveren aan gebruikers op basis van de campagne die hen naar het formulier heeft gebracht zonder dat handmatige invoer van velden of aangepaste scripts vereist zijn.

Deze verbeteringen verruimen aanzienlijk de mogelijkheden van de Adaptive Forms Rule Editor, waardoor ontwikkelaars beschikken over krachtige gereedschappen om meer dynamische, interactieve en intelligente formulieren te maken. Elke verbetering richt specifieke bedrijfsbehoeften terwijl het handhaven van het gebruiksgemak dat de Redacteur van de Regel voor zowel technische als niet-technische gebruikers toegankelijk maakt.