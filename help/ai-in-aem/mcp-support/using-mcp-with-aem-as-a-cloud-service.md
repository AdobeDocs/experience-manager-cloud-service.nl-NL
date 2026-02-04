---
title: MCP gebruiken met AEM as a Cloud Service
description: Leer hoe u het modelcontextprotocol met AEM as a Cloud Service kunt gebruiken
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
source-git-commit: 243fbd007235949fc03852658f606d483ef9ce4d
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# MCP gebruiken met AEM as a Cloud Service {#using-mcp-with-aem-as-a-cloud-service}

## Inleiding {#introduction}

Veel Adobe Experience Manager (AEM)-teams werken nu in Integrated Development Environment (IDE&#39;s) en chattoepassingen zoals Cursor, ChatGPT, Anthropic Claude en Microsoft Copilot Studio. Deze toepassingen steunen het ModelProtocol van de Context (MCP), dat toepassingen toestaat om achterste-eindhulpmiddelen aan grote taalmodellen (LLMs) op een gestandaardiseerde manier bloot te stellen.

Met AEM MCP-integratie kunnen verschillende personen samenwerken rond dezelfde inhoud:

* **de Ontwikkelaars** kunnen inhoudsverrichtingen en werkschema&#39;s van hun winde of praatjetoepassing organiseren
* **Praktijken** en inhoudsarchitecten kunnen plaatsen, inhoudsfragmenten, en activa met AI hulp beheren terwijl het blijven binnen het bestaande toestemmingsmodel van AEM.

>[!IMPORTANT]
>
> Voor scenario&#39;s die inhoud wijzigen of schrappen, zouden de artsen de AI Hulpinterface eerder moeten gebruiken dan direct het aanhalen van hulpmiddelen MCP, omdat de Agenten van AEM die door AI Medewerker worden in werking gesteld ingebouwde waarborgen omvatten.
>

Dit artikel verklaart welke functionaliteit AEM MCP verstrekt, welke toepassingen MCP worden gesteund, hoe te om het te vormen, en hoe te om het in de praktijk te gebruiken.

## Waarom MCP nuttig is voor klanten van AEM {#why-mcp-is-useful-for-aem-customers}

Moderne winde en praatjetoepassingen gebruiken MCP als manier voor een LLM om hulpmiddelen te roepen die achter servers MCP worden blootgesteld. In plaats van het schrijven van code tegen laag-vlakke API specificaties, kunnen de klanten hun intent in natuurlijke taal (*&quot;bijwerken de heldenbanner voor deze campagne over alle pagina&#39;s&quot;*) en LLM laten aanhalen de aangewezen hulpmiddelen MCP, die beurtelings met AEM APIs in wisselwerking staan.

Belangrijkste voordelen zijn:

* **natuurlijk-taal interactie in plaats van API loodgieterswerk**
De hulpmiddelen MCP beschrijven welke verrichtingen beschikbaar zijn en hoe te om hen te roepen. LLM gebruikt deze schema&#39;s om te beslissen welke hulpmiddelen om te roepen en met welke parameters.
* **Consistente ervaring over toepassingen**
De zelfde hulpmiddelen van AEM MCP kunnen van veelvoudige MCP-compatibele toepassingen worden gebruikt, toestaand teams om te werken waar zij het meest productief zijn terwijl het roepen van de zelfde onderliggende mogelijkheden van AEM.
* **behouden Veiligheid en bestuur**
Verzoeken naar AEM MCP-gereedschappen worden uitgevoerd onder de identiteit van de geverifieerde gebruiker en elk gereedschap dwingt de bestaande AEM-machtigingen van de gebruiker af. Voor bewerkingen met AI gelden dezelfde toegangsregels als voor handmatige werkzaamheden in AEM.

## MCP-servers geleverd door AEM {#mcp-servers-provided-by-aem}

AEM stelt MCP-servers beschikbaar als HTTP-eindpunten. De hieronder vermelde eindpunten zijn relatief ten opzichte van:

`https://mcp.adobeaemcloud.com/adobe/mcp/`

### MCP-servers {#mcp-servers}

| **MCP Server** | **Eindpunt** | **Beschrijving** |
|---|---|----------------------------------------------------------------------------------------------------------------------|
| **Inhoud** | `/content` | Alle inhoudsbewerkingen op laag niveau, inclusief maken, lezen, bijwerken en verwijderen (CRUD) voor pagina&#39;s, fragmenten en elementen. |
| **Inhoud (read-only)** | `/content-readonly` | Alleen-lezen inhoudsbewerkingen (Ophalen, Lijst/Zoeken) voor pagina&#39;s, fragmenten en elementen. |

De specifieke hulpmiddelen die door elke server MCP worden blootgesteld kunnen in tijd evolueren. In de praktijk kunt u uw MCP-Toegelaten toepassing vragen om hulpmiddelen via een herinnering zoals te ontdekken:

*&quot;maak een lijst van alle hulpmiddelen MCP van AEM beschikbaar bij deze server en beschrijf wat zij doen.&quot;*

De cliënt MCP zal het protocol gebruiken MCP om de hulpmiddellijst en schema&#39;s terug te winnen, die LLM dan kan gebruiken.

## Ondersteunde MCP-toepassingen {#supported-mcp-applications}

AEM MCP-servers zijn ontworpen voor gebruik met een gedefinieerde set MCP-compatibele toepassingen. De volgende toepassingen worden ondersteund:

* Anthropic Claude
* Cursor
* OpenAI ChatGPT
* Microsoft Copilot Studio

Elke toepassing biedt een eigen configuratievenis, maar de stappen op hoog niveau zijn vergelijkbaar.

## Overzicht van setup {#setup-overview}

Het vormen MCP voor AEM impliceert twee belangrijkste delen:

1. **Configuratie in elke MCP cliënttoepassing** zodat de toepassing weet hoe te met de servers van AEM te verbinden MCP en OAuth login uit te voeren
1. **selecteer de Server MCP** alvorens te beginnen te veroorzaken, zodat de cliënt MCP het weet te gebruiken.

### AEM-configuratie {#aem-configuration}

Standaard wordt de toegang tot AEM MCP-servers bepaald door de machtigingen die afzonderlijke gebruikers in AEM hebben. Wanneer een gebruiker door een MCP cliënttoepassing voor authentiek verklaart, dwingen de hulpmiddelen MCP de zelfde toegangsregels zoals handverrichtingen in AEM af. Een gebruiker kan alleen handelingen uitvoeren die al zijn geautoriseerd om uit te voeren.

#### Toegestane MCP-clienttoepassingen {#permitted-mcp-client-applications}

De volgende MCP cliënttoepassingen worden toegelaten door gebrek:

* ChatGPT
* Claude
* MS Copilot Studio
* Cursor

#### MCP-servers beperken {#restricting-mcp-servers}

Alle servers MCP worden gevoegd op lijst van gewenste personen door gebrek. Als beheerder, hebt u de optie om toegang tot specifieke servers MCP op de organisatie, het programma, of het milieuniveau te beperken. Dit geeft u korrelige controle over welke mogelijkheden MCP aan gebruikers binnen uw organisatie beschikbaar zijn.

#### De Toegang van de Cliënt MCP beheren {#managing-mcp-client-access}

De beheerders kunnen toegang voor specifieke MCP cliënttoepassingen ook onbruikbaar maken als het beleid van uw organisatie het vereist. Als u wilt dat Adobe ondersteuning voor extra MCP-clientproducten inschakelt, stuurt u een koppeling naar de productwebsite. Als u een douaneMCP cliënt moet lijsten van gewenste personen, bereik ook uit.

Voor alle MCP server verwante verzoeken, voel vrij om ons in **aemcs-mcp-feedback@adobe.com** te contacteren

### Configuratie van MCP-clienttoepassing {#mcp-client-application-configuration}

Deze stap wordt uitgevoerd door elke gebruiker (of door een beheerder van de MCP cliënttoepassing, waar gesteund). De details van de configuratie variëren lichtjes tussen toepassingen. De cliënten MCP evolueren snel, en de steun voor verre servers MCP wordt actief ontwikkeld. Mogelijk moet u de ontwikkelaarsmodus inschakelen voor toegang tot de functionaliteit voor het toevoegen van externe servers, maar het algemene proces is:

1. De URL(s) van de AEM MCP-server toevoegen
   * Vorm het MCP eindpunt (s) van de lijst hierboven. Bijvoorbeeld:`https://mcp.adobeaemcloud.com/adobe/mcp/content-readonly`
1. De verbinding activeren
   * Sla de configuratie op of activeer de configuratie zodat de MCP-clienttoepassing verbinding probeert te maken met de AEM MCP-server
1. Aanmelden met Adobe ID
   * Voltooi desgevraagd de Adobe-aanmeldstroom, zodat de toepassing OAuth-tokens kan ophalen die aan uw Adobe ID zijn gekoppeld
1. Onontdekte gereedschappen controleren
   * Zodra voor authentiek verklaard, zal de toepassing hulpmiddelen MCP van de server ontdekken. Vervolgens kunt u de LLM vragen om AEM-bewerkingen uit te voeren.

Hieronder ziet u voorbeelden van hoe dit er in elke ondersteunde toepassing op een hoog niveau uitziet.

**ChatGPT**

![ vorm ChatGPT - Montages ](assets/chatgpt-1.png)

![ vorm ChatGPT - Apps &amp; Connectors - Geavanceerde Montages ](assets/chatgpt-2.png)

![ vorm ChatGPT - Apps &amp; Connectors - de wijze van de Ontwikkelaar ](assets/chatgpt-3.png)

![ vorm ChatGPT - Apps &amp; Connectors - creeer app ](assets/chatgpt-4.png)

![ vorm ChatGPT - Apps &amp; Connectors - Nieuwe app ](assets/chatgpt-5.png)

![ vorm ChatGPT - Apps &amp; Connectors - de Dienst van MCP van de Inhoud van AEM ](assets/chatgpt-6.png)

![ vorm ChatGPT - vraag de Dienst van MCP van de Inhoud van AEM ](assets/chatgpt-7.png)

* Voeg de URL&#39;s van de AEM MCP-server toe in het gebied waar MCP-verbindingen of -gereedschappen zijn geconfigureerd
* De verbinding activeren en u aanmelden bij uw Adobe ID bij omleiding
* Verwijs in een praatje, de gevormde hulpmiddelen van AEM in uw herinneringen, bijvoorbeeld:

  *&quot;Gebruikend de gevormde hulpmiddelen van AEM MCP, maak een lijst van alle plaatsen in onze auteursmilieu.&quot;*

**Claude**

![ vorm Claude - Montages ](assets/claude-1.png)

![ vorm Claude - Schakelaars ](assets/claude-2.png)

![ vorm Claude - Verbindingen - voeg douaneschakelaar ](assets/claude-3.png) toe

![ vorm Claude - Verbindingen - verbind douaneschakelaar ](assets/claude-4.png)

![ vorm Claude - Verbindingen - Vorm douaneschakelaar ](assets/claude-5.png)

![ vorm Claude - Verbindingen - de toestemmingen van het Aangepast schakelaarhulpmiddel ](assets/claude-6.png)

![ vorm Claude - vraag de Dienst van MCP van de Inhoud van AEM ](assets/claude-7.png)

* Registreer de URL(s) van de AEM MCP-server in de MCP-configuratie van Claude
* De Adobe-aanmeldstroom voltooien
* Schakel desgewenst automatische bevestiging in voor bepaalde gereedschappen in het configuratiegebied. Dit wordt aanbevolen voor zoek- of alleen-lezen bewerkingen.
* Verzeker de server MCP alvorens uw gesprek te beginnen wordt geselecteerd
* Vraag Claude om AEM-gerelateerde taken uit te voeren; Claude zal AEM-gereedschappen selecteren die door de MCP-server worden weergegeven op basis van uw vraag.

**Cursor**

![ vorm Cursor - Montages ](assets/cursor-1.png)

![ vorm Cursor - Hulpmiddelen &amp; MCP - voeg Douane MCP ](assets/cursor-2.png) toe

![ vorm Cursor - voeg de montages van Aangepast MCP ](assets/cursor-3.png) toe

![ vorm Cursor - verbind ](assets/cursor-4.png)

![ vorm Cursor - vraag de nieuwe dienst ](assets/cursor-5.png)

* Maak in de MCP-instellingen van de cursor een nieuw MCP-serveritem met de AEM MCP-URL(&#39;s)
* Verifiëren met uw Adobe ID wanneer hierom wordt gevraagd
* U kunt desgewenst afzonderlijke gereedschappen in- of uitschakelen door op de naam van het gereedschap te klikken. Alle gereedschappen zijn standaard ingeschakeld.
* Gebruik de cursoreditor of -chat om AEM-gereedschappen aan te roepen als onderdeel van ontwikkelings- of inhoudsworkflows.

**Microsoft Copilot Studio**

![ vorm Copilot - Agenten ](assets/copilot-1.png)

![ vorm Copilot - voeg hulpmiddel ](assets/copilot-2.png) toe

![ vorm Copilot - voeg hulpmiddel toe - modelprotocol van de Context ](assets/copilot-3.png)

![ vorm Copilot - voeg een modelserver van het Protocol van de Context (voorproef) toe ](assets/copilot-4.png)

![ vorm Copilot - voeg hulpmiddel toe - creeer nieuwe verbinding ](assets/copilot-5.png)

![ vorm Copilot - voeg hulpmiddel toe - voeg toe en vorm ](assets/copilot-6.png)

![ vorm Copilot - voeg hulpmiddel toe - vorm ](assets/copilot-7.png)

![ vorm Copilot - de verbinding van de Test ](assets/copilot-8.png)

![ vorm Copilot - beheer Verbindingen ](assets/copilot-9.png)

![ vorm Copilot - de Agent van de Test ](assets/copilot-10.png)

* Een nieuwe agent maken
* Navigeer aan de hulpmiddelsectie en klik **toevoegen hulpmiddel**
* Een bestaand gereedschap selecteren of een nieuw gereedschap maken
* Een nieuw MCP-hulpprogramma configureren dat verwijst naar de URL(s) van de AEM MCP-server
* Vestig een verbinding, die kan worden gedeeld of tussen agenten worden gewijd
* Meld u aan met behulp van uw Adobe ID wanneer u omgeleid bent
* Schakel desgewenst de modus voor automatisch bevestigen in of zorg dat de eindgebruiker dit bevestigt voor alle gereedschapsinteracties
* Wanneer het testen van uw agent, open eerst de verbindingsmanager om een verbinding aan uw zitting toe te wijzen, dan druk **opnieuw**.

## Verificatie {#authentication}

De door Adobe gehoste MCP-servers implementeren OAuth en zijn geïntegreerd met het Adobe-identiteitssysteem.

* Wanneer een MCP cliënttoepassing met een server van AEM MCP verbindt, zien de gebruikers een login van Adobe dialoog en voor authentiek verklaren met hun **Adobe ID**
* Na succesvolle login, verifieert het systeem dat de MCP cliënttoepassing in uw organisatie wordt toegelaten en dat de gevraagde server MCP wordt toegestaan. Als één van beide controle ontbreekt, wordt een foutenmelding getoond.

![ MCP Cliënt niet toegelaten fout ](assets/MCP-Client-not-permitted.png)

* Zodra geverifieerd, geeft de server MCP tekenen uit die de toepassing voor verdere hulpmiddelvraag gebruikt
* De hulpmiddelen MCP respecteren de toestemmingen van AEM van de gebruiker. Een gebruiker zonder toestemming om een inhoudsfragment in AEM te wijzigen, kan het ook niet via MCP wijzigen.

Dit zorgt ervoor dat AI-ondersteunde bewerkingen voldoen aan uw bestaande AEM-model voor beveiliging en bestuur.

## MCP gebruiken met AEM {#using-mcp-with-aem}

Zodra AEM en uw MCP cliënttoepassingen worden gevormd, kunt u in uw toepassing van keus werken en LLM ertoe aanzetten om de verrichtingen van AEM uit te voeren. LLM leest de MCP hulpmiddelschema&#39;s, kiest welke hulpmiddelen te roepen, en opeenvolgt hen zoals nodig om uw verzoek te vervullen.

>[!IMPORTANT]
>
>Voor beste resultaten, vooral met herinneringen die veelvoudige stappen bevatten of verschillende inhoudstypes zoals beelden en tekst richten, laat een denkmodel toe of selecteer de het Vinden optie in uw cliënt MCP eerder dan het baseren op Auto wijze.

### Voorbeeld van gebruik {#example-usecases}

Enkele representatieve scenario&#39;s zijn:

* **ontdekking van het Milieu**
   * Maak een lijst van omgevingen en licenties om te bepalen waar een workflow moet worden uitgevoerd.

* **het beheer van Plaatsen**
   * Lijstsites
   * Pagina&#39;s en pagina-inhoud maken, lezen, bijwerken en verwijderen.

* **het beheer van het Fragment van de Inhoud**
   * Zoeken naar inhoudsfragmenten
   * Nieuwe fragmenten maken
   * Bestaande fragmenten bijwerken wanneer het campagnebericht verandert.

* **het beheer van Assets**
   * Elementen importeren
   * Bestaande elementen zoeken
   * Elementen publiceren.

### Voorbeelden van workflows {#example-workflows}

De volgende voorbeelden illustreren hoe een LLM hulpmiddelen MCP samen zou kunnen ketenen.

1. **Werkend met een inhoudsfragment dat door een pagina** van verwijzingen wordt voorzien
   * **krijgt paginacontent** - Vraag een hulpmiddel zoals `get-aem-page-content` om de pagina terug te winnen en van het `fragmentPath` bezit de plaats te bepalen.
   * **los de fragmentweg** op - gebruik `resolve_fragment_path` om de weg in UUID om te zetten.
   * **de fragmentgegevens van de Vetch** - Vraag `get_fragment` om de huidige gebieden terug te winnen.
   * **werk het fragment** bij - vraag `patch_fragment` om veranderingen op de fragmentinhoud toe te passen.
1. **Creërend nieuwe inhoud die op een model** wordt gebaseerd
   * **ontdekt modellen** - Gebruik `list_models` om te zien welke modellen van het inhoudsfragment beschikbaar zijn.
   * **inspecteer een model** - Gebruik `get_model` om het het gebiedsschema van het model te begrijpen.
   * **creeer inhoud** - Gebruik `create_fragment` om een nieuw fragment met waarden tot stand te brengen die uit uw herinnering worden afgeleid.
1. **veilig het bijwerken van bestaande inhoud**
   * **las huidige gegevens** - Gebruik `get_fragment` om de bestaande gegevens en een ETag terug te winnen.
   * **pas een Reparatie JSON** toe - Gebruik `patch_fragment` met ETag en een document van het Reparatie JSON om het fragment bij te werken, ondersteunend optimistische gelijkenis.

Vanuit het perspectief van de gebruiker, kunnen deze werkschema&#39;s met herinneringen zoals worden in werking gesteld:

*&quot;Creeer een nieuw inhoudsfragment voor de lentecampagne die op ons model van heldenbanner wordt gebaseerd en vul zijn gebieden van dit korte in.&quot;*

LLM kiest en coördineert automatisch de noodzakelijke hulpmiddelen MCP.

## Vertrouwensbeheer {#expectation-management}

Wanneer het werken met LLMs door MCP, houd het volgende in mening:

* **hoogst geschikt maar niet onfeilbaar**
LLM&#39;s kunnen complexe taken uitvoeren, maar zijn soms vatbaar voor fouten. Dezelfde prompt kan iets andere resultaten of presentaties opleveren zonder dat hiervoor een duidelijke reden bestaat. Evalueer altijd de uitvoer voordat u wijzigingen aanbrengt in de productie-inhoud.

* **het evolueren mogelijkheden**
LLM-modellen worden voortdurend verbeterd. In tijd, worden zij slimmer in het ontdekken van nieuwe manieren om hulpmiddelen te combineren MCP om uw doelstellingen te bereiken. Een taak die vandaag meerdere herinneringen vereiste, kan naadloos met één enkele herinnering morgen werken.

* **Het menselijke toezicht is essentieel**
Beschouw de LLM als een deskundige assistent die toezicht nodig heeft. Het heeft brede kennis en kan creatieve oplossingen bedenken, maar het profiteert van uw begeleiding en overzicht. Verifieer resultaten, vooral voor kritieke verrichtingen, en verstrek terugkoppel wanneer de output niet uw verwachtingen aanpast.

* **ben voorzichtig met auto-erkennende hulpmiddeluitvoeringen**
Sommige MCP cliënttoepassingen, zoals Claude, bieden de optie aan auto-erkende hulpmiddeluitvoeringen die door LLM worden gevraagd. Hoewel dit handig kan zijn voor alleen-lezen bewerkingen, zoals het zoeken naar of ophalen van inhoud, moet u voorzichtig zijn met gereedschappen die inhoud bijwerken of verwijderen. Bekijk elk verzoek tot uitvoering van een gereedschap voordat u handelingen bevestigt die uw AEM-omgeving wijzigen.

## Beperkingen {#limitations}

AEM MCP-servers moeten momenteel worden geconfigureerd in ChatGPT, Claude, Cursor en Microsoft Copilot Studio.

Als u een verschillende MCP cliënttoepassing zou willen gebruiken, voel vrij om uit in **aemcs-mcp-feedback@adobe.com** te bereiken om steun voor extra cliënten te verzoeken of een douane te lijsten van gewenste personen.
