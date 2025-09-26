---
title: Dit artikel schetst diverse gebruiksgevallen voor de regeleditor in een adaptieve vorm op basis van kerncomponenten.
description: In dit artikel worden verschillende gebruiksgevallen voor de regeleditor in een adaptieve vorm op basis van kerncomponenten besproken. De code benadrukt ook hoe aangepaste functies kunnen worden gebruikt om op maat gemaakte regels voor formulieren te maken.
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner, Intermediate
exl-id: 062ed441-6e1f-4279-9542-7c0fedc9b200
source-git-commit: f772a193cce35a1054f5c6671557a6ec511671a9
workflow-type: tm+mt
source-wordcount: '1975'
ht-degree: 0%

---

# Verbeteringen in de regeleditor en hoofdletters/kleine letters gebruiken

<span class="preview"> Dit zijn pre-vrijlatingseigenschappen beschikbaar door ons <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=nl-NL#new-features"> pre-vrijgavekanaal </a>. Deze verbeteringen zijn ook van toepassing op Edge Delivery Services Forms.

Dit artikel introduceert de meest recente verbeteringen aan de regeleditor in Adaptive Forms. Deze updates zijn ontworpen om u te helpen formuliergedrag gemakkelijker te definiëren, zonder aangepaste code te schrijven, en om een dynamischere, responsieve en gepersonaliseerde formulierervaring te maken.

De onderstaande tabel bevat een overzicht van recente verbeteringen aan de regeleditor in Adaptive Forms, samen met een korte beschrijving en de belangrijkste voordelen van elke functie:

| Verbetering | Beschrijving | Voordelen |
|---|----|---|
| [ Bevestiging die gebruikt bevestigt () methode ](#validate-method-in-function-list) | Beschikbaar in de functielijst om afzonderlijke velden, deelvensters of het hele formulier te valideren. | - Kortere validatie op deelvenster-, veld- of formulierniveau <br> - Betere gebruikerservaring met gericht foutbericht <br> - Voorkomt dat er vooruitgang wordt geboekt met onvolledige gegevens <br> - Vermindert de fout bij het verzenden van formulieren |
| [ Document van de Download van Verslag ](#download-document-of-record) | De functie uit-van-de-doos beschikbaar in de regelredacteur om het Document van Verslag (DoR) te downloaden. | - Geen aangepaste ontwikkeling vereist voor het downloaden van DoR <br> - Consistente downloadervaring in verschillende formulieren |
| [ Dynamische variabelen ](#support-for-dynamic-variables-in-rules) | Maak regels met variabelen die worden gewijzigd op basis van gebruikersinvoer of andere voorwaarden. | - Maakt flexibele regelvoorwaarden mogelijk <br> - Minder behoefte aan dubbele logica <br> - elimineert de vereiste om verborgen velden te maken |
| [ Aangepaste op gebeurtenis-gebaseerde regels ](#custom-event-based-rules-support) | Definieer regels die reageren op aangepaste gebeurtenissen buiten de standaardtriggers. | - Biedt ondersteuning voor gevallen van geavanceerd gebruik <br> - Meer controle over wanneer en hoe regels worden uitgevoerd <br> - Verbetert de interactiviteit |
| [ context-bewuste herhaalbare paneeluitvoering ](#context-based-rule-execution-for-repeatable-panels) | Regels worden nu uitgevoerd in de juiste context voor elk herhaald deelvenster in plaats van alleen voor de laatste instantie. | - Nauwkeurige regeltoepassing voor elke herhalingsinstantie <br> - Vermindert fouten in dynamische secties <br> - Verbetert gebruikerservaring met herhaalde inhoud |
| [ Steun voor vraagkoord, UTM, en browser parameters ](#url-and-browser-parameter-based-rules-in-adaptive-forms) | Maak regels die het formuliergedrag aanpassen op basis van URL-parameters of browserspecifieke waarden. | - Schakelt personalisatie op basis van bron of omgeving in <br> - Geschikt voor marketing of tracking-specific flows <br> - Geen noodzaak voor extra scripts of aanpassing |

>[!NOTE]
>
> De verhogingen zijn ook van toepassing op de [ Redacteur van de Regel van de Diensten Forms van Edge Delivery ](/help/edge/docs/forms/universal-editor/rule-editor-universal-editor.md).

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
>U kunt **gebruiken bevestigt ()** methode op vormen, fragmenten, of individuele gebieden. Wanneer een fragment in een formulier wordt opgenomen, worden zowel het formulier als het fragment als opties weergegeven in de validatiecontext. In dit geval verwijst het fragment naar de velden in het fragment, terwijl het formulier verwijst naar het bovenliggende formulier waarin het fragment is ingesloten.

## Document van record downloaden

Gebruikend **DownloadDor ()** out-of-the-box (OOTB) functie in de Redacteur van de Regel, staat gebruiker toe om het Document van Verslag te downloaden, als de vorm wordt gevormd om Document van Recored te produceren.

>[!NOTE]
>
>Als de vorm niet voor Document van Verslag wordt gevormd, wordt een foutenmelding getoond wanneer de regel gebruikend **downloadDoR ()** functie wordt toegepast op de knoop.

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

De verbeterde regeleditor ondersteunt het maken en gebruiken van dynamische (tijdelijke) variabelen. Deze variabelen kunnen door de levenscyclus van de vorm worden geplaatst en worden teruggewonnen gebruikend de ingebouwde **Reeks Variabele Waarde** en **krijgen Variabele functies van de Waarde**.
Deze variabelen:

* Deze gegevens worden niet samen met de formuliergegevens verzonden.
* Kan tussentijdse of berekende waarden bevatten.
* Kan worden gebruikt in voorwaardelijke logica en handelingen.

**Scenario**: Een online het winkelen vorm staat gebruikers toe om een product te selecteren, hoeveelheid in te gaan, en een land voor het verschepen te kiezen. De prijs van het product is een vaste waarde die in een formulierveld wordt vastgelegd, terwijl de verzendkosten dynamisch variëren, afhankelijk van het geselecteerde land.

Om te voorkomen dat het formulier door verborgen velden wordt bedekt, besluiten bedrijven de verzendkosten op te slaan in een tijdelijke variabele en deze te gebruiken voor realtime berekeningen.

**Implementatie die de Vastgestelde Waarde van de Variabele gebruikt en de functies van de Waarde van de Variabele in de Redacteur van de Regel krijgt**

>[!VIDEO](https://video.tv.adobe.com/v/3471607/get-set-variable-final-video/?quality=12&learn=on)

Een regel wordt gevormd op het **fragment van het Adres** gebruikend de **Vastgestelde Variabele functie van de Waarde** om een tijdelijke genoemde variabele toe te wijzen **extra heffing**. De waarde van deze variabele wordt dynamisch gewijzigd op basis van het geselecteerde land. Bijvoorbeeld:

* Als de gebruiker Verenigde Staten selecteert, **extra lading** wordt geplaatst aan 500.
* Voor om het even welk ander land, **wordt de extra lading** geplaatst aan 100.

![ vastgestelde veranderlijke waarde ](/help/forms/assets/setvalue.png)

Later, wanneer de **Totale Kosten van de Verzending** wordt berekend, **krijgt de Veranderlijke functie van de Waarde** wordt gebruikt om de waarde van **extra lading** terug te winnen. Deze waarde wordt toegevoegd aan de **Prijs van het Product × Hoeveelheid van het Product** om het definitieve te betalen bedrag op de knoop te berekenen klikt.

![ krijgt veranderlijke waarde ](/help/forms/assets/getvalue.png)

Het **Totale gebied van de Kosten van de Verzending** werkt dynamisch bij om op zowel de productkosten als de verzendkosten te wijzen aangezien de gebruiker het land of de hoeveelheid verandert.
![ output ](/help/forms/assets/getsetvalue-output.png)

>[!NOTE]
>
> U kunt **ook toevoegen krijgt veranderlijke waarde** functie in wanneer voorwaarde.
> &#x200B;> ![Hiermee wordt de functie Variabele-waarde opgehaald in Wanneer voorwaarde ](/help/forms/assets/when-get-variable.png){width=50%,height=50%, align=center}

Deze aanpak maakt dynamische, real-time berekeningen mogelijk zonder extra velden aan het formulier toe te voegen, zodat de structuur schoon en gebruiksvriendelijk blijft.

## Ondersteuning voor aangepaste regels op basis van gebeurtenissen

De verbeterde regelredacteur steunt de behandeling van de douanegebeurtenis gebruikend de **Gebeurtenis van de Verzending** en **op de functies van de Gebeurtenis van de Trekker**. Met deze functies kunnen verschillende delen van het formulier communiceren door aangepaste gebeurtenissen uit te zenden en te beluisteren, waardoor een schonere, modulaire logica mogelijk is zonder strakke koppeling van handelingen naar specifieke velden.

**Scenario**: Een login vorm wordt gebouwd gebruikend een herbruikbaar login fragment dat **bevat gaat Gebruikersnaam** in en **gaat de gebieden van het Wachtwoord** in. Wanneer een gebruiker geldige geloofsbrieven verstrekt, bevestigt de vorm de input en stelt het **in werking krijgen OTP** proces. Nadat de gebruiker geldige OTP ingaat, worden zij opnieuw gericht aan de aangewezen pagina.

In plaats van het rechtstreeks binden van logica aan de gebieden, gebruikt de vorm een op gebeurtenis-gebaseerde benadering met **Gebeurtenis van de Verzending** en **op de Gebeurtenis van de Trekker** om modulariteit en onderhoudbaarheid te verbeteren.

**Implementatie die de Gebeurtenis van de Verzending en op de Gebeurtenis van de Trekker gebruiken**


>[!VIDEO](https://video.tv.adobe.com/v/3471610/dispatch-trigger-final/?quality=12&learn=on)

Het aanmeldingsfragment wordt aan het formulier toegevoegd, dat vooraf gedefinieerde velden voor Gebruikersnaam en Wachtwoord bevat. Een regel wordt gevormd op **krijgt OTP** knoop om het **Comité van de Bevestiging** te tonen, dat het inputgebied voor het ingaan van en het bevestigen van OTP omvat.

![ krijgt OTP Regel ](/help/forms/assets/get-otp-rule.png)

In het **Comité van de Bevestiging**, wordt een regel gevormd op Validate knoop. API integratie wordt gebruikt om OTP te bevestigen ingegaan op **ga OTP** gebied in. Als de bevestiging succesvol is, wordt a **genoemd** LoggedIn van de Gebeurtenis van de Verzending **&#x200B;**&#x200B;teweeggebracht met de gebeurtenislading die de API reactie bevatten.

![ In de regel van de trekkergebeurtenis ](/help/forms/assets/trigger-event-rule.png)

Op het vormniveau, wordt een regel gevormd om op de **LoggedIn** gebeurtenis te luisteren. Wanneer deze gebeurtenis wordt teweeggebracht, toont de regel het omleidingsbericht en neemt de gebruiker aan de dashboardpagina.

![ regel van de verzendingsgebeurtenis ](/help/forms/assets/dispatch-event-rule.png)

Wanneer de gebruiker het formulier verzendt met de juiste gegevens en een geldige OTP, is de aanmelding gelukt en wordt de gebruiker omgeleid naar het dashboard.

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

## Aanvullende bronnen

{{see-also-rule-editor}}
