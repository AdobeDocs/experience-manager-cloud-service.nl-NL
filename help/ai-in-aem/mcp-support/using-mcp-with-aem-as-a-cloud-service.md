---
title: MCP gebruiken met AEM as a Cloud Service
description: Leer hoe u het modelcontextprotocol met AEM as a Cloud Service kunt gebruiken
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
exl-id: ddb7fc8c-affc-4374-8e08-d45d96017109
source-git-commit: 6fccf4f197fbfd38aa6a84422dc347b02d03061d
workflow-type: tm+mt
source-wordcount: '1786'
ht-degree: 0%

---

# MCP gebruiken met AEM as a Cloud Service {#using-mcp-with-aem-as-a-cloud-service}

## Inleiding {#introduction}

Veel Adobe Experience Manager (AEM)-teams werken nu in Integrated Development Environment (IDE&#39;s) en chattoepassingen zoals Cursor, OpenAI ChatGPT, Anthropic Claude en Microsoft Copilot Studio. Deze toepassingen steunen het ModelProtocol van de Context (MCP), dat toepassingen toestaat om achterste-eindhulpmiddelen aan grote taalmodellen (LLMs) op een gestandaardiseerde manier bloot te stellen.

Met AEM MCP-integratie kunnen verschillende personen samenwerken rond dezelfde inhoud:

* **de Ontwikkelaars** kunnen inhoudsverrichtingen en werkschema&#39;s van hun winde of praatjetoepassing organiseren
* **Praktijken** en inhoudsarchitecten kunnen plaatsen, inhoudsfragmenten, en activa met AI hulp beheren terwijl het blijven binnen het bestaande toestemmingsmodel van AEM.

>[!IMPORTANT]
>
> Voor scenario&#39;s die inhoud wijzigen of schrappen, zouden de artsen de AI Hulp interface eerder moeten gebruiken dan direct het aanhalen van hulpmiddelen MCP. De AEM Agents die door AI Assistant worden uitgevoerd, bevatten ingebouwde beveiligingsinstellingen.
>

Dit artikel verklaart welke functionaliteit AEM MCP verstrekt, welke toepassingen MCP worden gesteund, hoe te om het te vormen, en hoe te om het in de praktijk te gebruiken.

## Waarom MCP nuttig is voor klanten van AEM {#why-mcp-is-useful-for-aem-customers}

Moderne winde en praatjetoepassingen gebruiken MCP als manier voor een LLM om hulpmiddelen te roepen die achter servers MCP worden blootgesteld. Klanten kunnen hun intentie in natuurlijke taal beschrijven in plaats van code te schrijven tegen API-specificaties op laag niveau. Bijvoorbeeld, laat een herinnering zoals *&quot;de heldenbanner voor deze campagne over alle pagina&#39;s&quot;bijwerken* LLM de aangewezen hulpmiddelen aanhalen MCP, die dan met AEM APIs in wisselwerking staan.

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
| **Cloud Manager** | `/cloudmanager` | Beheer Cloud Manager-entiteiten, inclusief programma&#39;s, omgevingen, opslagruimten en pijpleidingen, die ook kunnen worden geactiveerd. <br><br>*Deze server MCP is nu in **bèta**; om toegang, e-mail [ aemcs-mcp-feedback@adobe.com ](mailto:aemcs-mcp-feedback@adobe.com) met een beschrijving van uw gebruiksgeval te verzoeken.* |

De specifieke hulpmiddelen die door elke server MCP worden blootgesteld kunnen in tijd evolueren. In de praktijk kunt u uw MCP-Toegelaten toepassing vragen om hulpmiddelen via een herinnering zoals te ontdekken:

```
"List all AEM MCP tools available from this server and describe what they do."
```

De cliënt MCP gebruikt het protocol MCP om de hulpmiddellijst en schema&#39;s terug te winnen, die LLM dan kan gebruiken.

Verwijs het [ Leerprogramma van de Server MCP van de Inhoud ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/ai/mcp-servers/accelerate-content-operations-with-aem-mcp-server) en [ Video van de Server van Cloud Manager MCP ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/ai/mcp-servers/cloud-manager) voor meer informatie over hun mogelijkheden en hoe te om hen te gebruiken.

## Ondersteunde MCP-toepassingen {#supported-mcp-applications}

AEM MCP servers worden ontworpen om met een bepaalde reeks MCP-compatibele toepassingen te werken. Elke toepassing biedt een eigen configuratie-ervaring, maar de stappen op hoog niveau zijn vergelijkbaar.

### Chattoepassingen (web en bureaublad) {#chat-applications}

* Anthropic Claude
* OpenAI ChatGPT

### Gereedschappen voor ontwikkelaars (IDE-extensies, bureaubladtoepassingen, CLI&#39;s) {#developer-tools}

* Anthropic Claude Code (CLI, JetBrains, VS Code, Cursor)
* Augment Code (CLI, JetBrains, VS Code, Cursor)
* Augment Indent Desktop App
* Cline (JetBrains, VS Code, Cursor)
* Cursor
* GitHub Copilot (VS Code)
* Kiro (Desktop App, CLI)
* OpenAI Codex (Desktop App)
* OpenAI Codex CLI
* Windsurf

### Enterprise-platforms {#enterprise-platforms}

* Microsoft Copilot Studio

## Overzicht van setup {#setup-overview}

Het vormen MCP voor AEM impliceert twee belangrijke delen:

1. **Configuratie in elke MCP cliënttoepassing** zodat de toepassing weet hoe te met de AEM MCP servers te verbinden en OAuth login uit te voeren
1. **selecteer de Server MCP** alvorens aan herinnering te beginnen, zodat de cliënt MCP weet om het te gebruiken.

### AEM-configuratie {#aem-configuration}

De rechten die individuele gebruikers in AEM hebben, zijn standaard van toepassing op de toegang tot AEM MCP-servers. Wanneer een gebruiker door een MCP cliënttoepassing voor authentiek verklaart, dwingen de hulpmiddelen MCP de zelfde toegangsregels zoals handverrichtingen in AEM af. Een gebruiker kan alleen handelingen uitvoeren die al zijn geautoriseerd om uit te voeren.

#### Toegestane MCP-clienttoepassingen {#permitted-mcp-client-applications}

De volgende MCP cliënttoepassingen worden toegelaten door gebrek:

* Anthropic Claude
* Anthropic Claude Code
* Augmentcode
* Augment Indent
* Cline
* Cursor
* GitHub Copilot
* Kiro
* Microsoft Copilot Studio
* OpenAI ChatGPT
* OpenAI Codex
* OpenAI Codex CLI
* Windsurf

#### MCP-servers beperken {#restricting-mcp-servers}

Alle servers MCP worden gevoegd op lijst van gewenste personen door gebrek. Als beheerder, hebt u de optie om toegang tot specifieke servers MCP op de organisatie, het programma, of het milieuniveau te beperken. Deze beperking geeft u korrelige controle over welke mogelijkheden MCP aan gebruikers binnen uw organisatie beschikbaar zijn.

#### De Toegang van de Cliënt MCP beheren {#managing-mcp-client-access}

De beheerders kunnen toegang voor specifieke MCP cliënttoepassingen ook onbruikbaar maken als het beleid van uw organisatie het vereist. Als u wilt dat Adobe ondersteuning voor extra MCP-clientproducten inschakelt, stuurt u een koppeling naar de productwebsite. Als u een douaneMCP cliënt moet lijsten van gewenste personen, bereik ook uit.

Voor alle MCP server verwante verzoeken, voel vrij om ons in **aemcs-mcp-feedback@adobe.com** te contacteren

### Configuratie MCP-clienttoepassing {#mcp-client-application-configuration}

Elke gebruiker voert deze stap uit, of een beheerder van de MCP cliënttoepassing kan het uitvoeren waar gesteund. De configuratiedetails variëren iets tussen de toepassingen. De cliënten MCP evolueren snel, en de steun voor verre servers MCP wordt actief ontwikkeld. Mogelijk moet u de ontwikkelaarsmodus inschakelen voor toegang tot de functionaliteit voor het toevoegen van externe servers, maar het algemene proces is:

1. Een of meer URL&#39;s van AEM MCP-servers toevoegen
   * Vorm één of meerdere eindpunten MCP van de lijst hierboven. Bijvoorbeeld:`https://mcp.adobeaemcloud.com/adobe/mcp/content-readonly`
1. De verbinding activeren
   * Sla de configuratie op of activeer de configuratie zodat de MCP-clienttoepassing verbinding probeert te maken met de AEM MCP-server
1. Aanmelden met Adobe ID
   * Voltooi desgevraagd de Adobe-aanmeldstroom, zodat de toepassing OAuth-tokens kan ophalen die aan uw Adobe ID zijn gekoppeld
1. Onontdekte gereedschappen controleren
   * Zodra voor authentiek verklaard, ontdekt de toepassing hulpmiddelen MCP van de server. Vervolgens kunt u de LLM vragen om AEM-bewerkingen uit te voeren.

Hieronder vindt u een overzicht van de ondersteunde toepassingen, waarvan enkele zijn gekoppeld aan stapsgewijze hulplijnen:

#### Chattoepassingen (web en bureaublad) {#setup-chat-applications}

* [Anthropic Claude](/help/ai-in-aem/mcp-support/setup-claude.md)
* [OpenAI ChatGPT](/help/ai-in-aem/mcp-support/setup-chatgpt.md)

#### Gereedschappen voor ontwikkelaars (IDE-extensies, bureaubladtoepassingen, CLI&#39;s) {#setup-developer-tools}

* Anthropic Claude Code (CLI, JetBrains, VS Code, Cursor)
* Augment Code (CLI, JetBrains, VS Code, Cursor)
* Augment Indent Desktop App
* Cline (JetBrains, VS Code, Cursor)
* [Cursor](/help/ai-in-aem/mcp-support/setup-cursor.md)
* GitHub Copilot (VS Code)
* Kiro (Desktop App, CLI)
* OpenAI Codex (Desktop App)
* OpenAI Codex CLI
* Windsurf

#### Enterprise-platforms {#setup-enterprise-platforms}

* [Microsoft Copilot Studio](/help/ai-in-aem/mcp-support/setup-microsoft-copilot-studio.md)

## Verificatie {#authentication}

De Adobe-ontvangen MCP servers voeren OAuth uit en zijn geïntegreerd met het identiteitssysteem van de Adobe.

* Wanneer een MCP cliënttoepassing met een AEM server verbindt MCP, zien de gebruikers een Adobe login dialoog en voor authentiek verklaren met hun **Adobe ID**
* Na succesvolle login, verifieert het systeem dat de MCP cliënttoepassing in uw organisatie wordt toegelaten en dat de gevraagde server MCP wordt toegestaan. Als een van beide controles mislukt, wordt een foutbericht weergegeven.

![ MCP Cliënt niet toegelaten fout ](assets/MCP-Client-not-permitted.png)

* Zodra geverifieerd, geeft de server MCP tekenen uit die de toepassing voor verdere hulpmiddelvraag gebruikt
* De hulpmiddelen MCP respecteren de toestemmingen van AEM van de gebruiker. Alleen gebruikers die gemachtigd zijn om een inhoudsfragment in AEM te wijzigen, kunnen het wijzigen via MCP.

Deze benadering zorgt ervoor dat AI-ondersteunde bewerkingen voldoen aan uw bestaande AEM-model voor beveiliging en bestuur.

## MCP gebruiken met AEM {#using-mcp-with-aem}

Zodra AEM en uw MCP cliënttoepassingen worden gevormd, kunt u in uw toepassing van keus werken en LLM ertoe aanzetten om de verrichtingen van AEM uit te voeren. LLM leest de MCP hulpmiddelschema&#39;s, kiest welke hulpmiddelen te roepen, en opeenvolgt hen zoals nodig om uw verzoek te vervullen.

>[!IMPORTANT]
>
>Prompts die meerdere stappen bevatten of verschillende inhoudstypen als doel hebben, zoals afbeeldingen en tekst, werken het beste met een denkmodel. Laat een denkmodel toe of selecteer de het Vinden optie in uw cliënt MCP in plaats van het vertrouwen op Auto wijze.

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
   * **krijg paginacontent** - roep een hulpmiddel zoals `get-aem-page-content` om de pagina terug te winnen en van het `fragmentPath` bezit de plaats te bepalen.
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

```
"Create a new content fragment for the spring campaign based on our hero banner model and fill in its fields from this brief."
```

LLM kiest en coördineert automatisch de noodzakelijke hulpmiddelen MCP.

## Vertrouwensbeheer {#expectation-management}

Wanneer het werken met LLMs door MCP, houd het volgende in mening:

* **hoogst geschikt maar niet onfeilbaar**
LLM&#39;s kunnen complexe taken uitvoeren, maar zijn soms vatbaar voor fouten. Dezelfde prompt kan iets andere resultaten of presentaties opleveren zonder dat hiervoor een duidelijke reden bestaat. Evalueer altijd de uitvoer voordat u wijzigingen aanbrengt in de productie-inhoud.

* **het evolueren mogelijkheden**
LLM-modellen worden voortdurend verbeterd. In tijd, worden zij slimmer in het ontdekken van nieuwe manieren om hulpmiddelen te combineren MCP om uw doelstellingen te bereiken. Een taak die vandaag meerdere herinneringen vereiste, kan naadloos met één enkele herinnering morgen werken.

* **het menselijke toezicht is essentieel:**
Beschouw de LLM als een deskundige assistent die toezicht nodig heeft. Het heeft brede kennis en kan creatieve oplossingen bedenken, maar het profiteert van uw begeleiding en overzicht. Verifieer resultaten, vooral voor kritieke verrichtingen, en verstrek terugkoppel wanneer de output niet uw verwachtingen aanpast.

* **ben voorzichtig met auto-erkennende hulpmiddeluitvoeringen**
Sommige MCP cliënttoepassingen, zoals Claude, bieden de optie aan auto-erkende hulpmiddeluitvoeringen die door LLM worden gevraagd. Hoewel deze optie handig kan zijn voor alleen-lezen bewerkingen zoals het zoeken of ophalen van inhoud, is het verstandig om voorzichtig te zijn met gereedschappen die inhoud bijwerken of verwijderen. Bekijk elk verzoek tot uitvoering van een gereedschap voordat u handelingen bevestigt die uw AEM-omgeving wijzigen.

## Beperkingen {#limitations}

AEM steunt momenteel het vormen MCP servers in de toepassingen die onder [ worden vermeld Gesteunde Toepassingen MCP ](#supported-mcp-applications).

Als u een verschillende MCP cliënttoepassing zou willen gebruiken, voel vrij om uit in **aemcs-mcp-feedback@adobe.com** te bereiken om steun voor extra cliënten te verzoeken of een douane te lijsten van gewenste personen.
