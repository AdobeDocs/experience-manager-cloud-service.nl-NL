---
title: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: b147c80581bcb554ae0b4ac971c5f98e7160d1df
workflow-type: tm+mt
source-wordcount: '1363'
ht-degree: 0%

---

# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In de volgende sectie worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van as a Cloud Service Experience Manager beschreven.

## Release 13665 {#release-13665}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 13665 samengevat, die op 27 september 2023 openbaar werd gemaakt. Deze onderhoudrelease vervangt release 13420.

2023.10.0 Activering van de functie biedt de volledige functie die is ingesteld voor deze onderhoudsrelease. Zie de [Experience Manager geeft Routekaart vrij](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html) voor meer informatie .

### Verbeteringen {#enhancements-13665}

* Verschillende verbeteringen in de API&#39;s voor inhoudsfragmenten.
* ASSETS-26713: Assets-dashboard: het nieuwe Experience UI-dashboard is nu bereikbaar via Touch UI.
* SITES-11206: Content Fragments: Search API for Content Fragments.
* SITES-11262: Inhoudsfragmenten: knop om over te schakelen naar de nieuwe Inhoudsfragmenteditor.
* SITES-15447: Core Components: Release van versie 2.23.4.
* FORMS-9624: Inleiding CAPTCHA-component voor Adaptive Forms op basis van Core Components.
* FORMS-9913: Verbeterde de visuele redacteur roept dienst door de capaciteit toe te voegen om gebieden te bevestigen en aangewezen fout en succesberichten te tonen.
* FORMS-10106: Enhanced GeneratePDFOutput API om het aantal pagina&#39;s in het gegenereerde document te retourneren.
* FORMS-2494: extra ondersteuning voor formulierfragmenten voor adaptieve Forms op basis van kerncomponenten.
* FORMS-9807: Toegevoegde ondersteuning voor navigatie naar een pagina-URL die wordt geretourneerd als gevolg van een geslaagde verzending via de Adaptive Form Rule-editor.
* FORMS-10571: hiermee hebt u de mogelijkheid toegevoegd om een URL voor het omleiden van een pagina voor dankuwel in te stellen op basis van het antwoord van een service die wordt gebruikt in een aangepaste verzendactie voor Adaptive Forms op basis van Core Components.

### Opgeloste problemen {#fixed-issues-13665}

* Verschillende vertalingen.
* CQ-4354428: Workflows: kan een taak in Postvak IN niet voltooien.
* SITES-9733: Content Fragments: Asset References in content fragment reference panel shows 0(zero) references.
* SITES-14561: Inhoudsfragmenten: Vaste en verbeterde HTML naar Markup-conversie.
* SITES-14882: Inhoudsfragmenten: als we het inhoudsfragment bewerken en het tabblad sluiten zonder op de knop Opslaan of Sluiten te klikken, worden de waarden opgeslagen.
* SITES-15167: Inhoudsfragmenten: het repareren van een variatie met een ongeldige lading retourneert niet 400, maar 500.
* SITES-15514: Content Fragments: Malformed Markdown output voor lijst binnen RTE.
* SITES-15661: Inhoudsfragmenten: gebruik geen unieke restrictie en wijzig de volgorde van items in verwijzingsvelden in de API Fragments.
* SITES-15730: Schermen: functionaliteit voor kanaalvoorvertoning werkt niet op het dashboard.
* SITES-15995: Inhoudsfragmenten: MIME-typen van zowel model- als fragmentlange tekstvelden worden gecodeerd.
* SITES-16074: Inhoudsfragmenten: Tagvelden die geen tekenreeks zijn[] kan niet van JCR worden opgehaald.
* SITES-16084: Inhoudsfragmenten: CFHomeCardModelImpl ontbreekt de doelnavigator.
* SITES-14773: De Fragmenten van de ervaring: De Verwijzing van de verbinding wordt niet bijgewerkt binnen ervaringsfragment.
* SITES-14899: De Fragmenten van de Ervaring: Veelvoudige aanbiedingen die voor XF variaties in Doel worden gecreeerd.
* SITES-8590: GraphQL: De coderingskwesties met variabelen in persisted query.
* SITES-9224: GraphQL: de uitzondering Writer is al gesloten in GraphQLServlet.
* SITES-14800: GraphQL: Exception in persisted GraphQL query&#39;s with variables.
* SITES-15586: GraphQL: Issue with persisted query filtering with null values.
* SITES-15622: GraphQL: Probleem met aanhoudende query&#39;s met getallen en bool parameters.
* SITES-15654: GraphQL: Issue with union &amp; properties with same name.
* SITES-15267: Opstarten: Bij de promotie worden geen opstartiepagina&#39;s opgehaald die zijn gewijzigd voordat de startconfiguratie werd gewijzigd.
* SITES-15406: Start: kan geen startpagina toevoegen.
* SITES-15427: Launches: Inconsistent gedrag van het bereik &quot;Huidige pagina en subpagina&#39;s bevorderen&quot;.
* SITES-15429: Launches: pagina&#39;s ontwerpen verwijderd tijdens het promoten van startpagina&#39;s.
* SITES-15462: Launches: Automatische promotieprocedure publiceert pagina&#39;s die buiten het promotiebereik vallen.
* SITES-15815: Launches: Verwijderde pagina uit Launch zorgt ervoor dat Starten niet correct wordt bevorderd.
* SITES-15223: Pagina-editor: kan componenten niet vergroten of verkleinen in emulator voor tabletgrootte.
* SITES-15463: Paginasjablonen: sjablonen kunnen niet worden gepubliceerd.
* FORMS-10700: wanneer u de component date picker gebruikt in een adaptief formulier dat is gebaseerd op Core Components:
   * Wanneer de gebruiker het formulier verzendt zonder invoer voor de datumcomponent op te geven, wordt een fout vastgelegd.
   * Wanneer u gelokaliseerde versies van de datumkiezer gebruikt, werken sommige maanden naadloos. Als u bepaalde andere maanden selecteert, treedt een componentfout op.
* FORMS-9598: De ingesloten AEM Forms-component werkt niet.
* FORMS-9579: u kunt geen waarde Van Boole tot een functie overgaan terwijl het gebruiken van de Redacteur van Regels.
* FORMS-9916: Als het veld als ongeldig wordt gemarkeerd, wordt een wijzigingsgebeurtenis opnieuw geactiveerd in hetzelfde veld. Deze onverwachte gebeurtenis activeert de regel opnieuw en maakt een lus die zich blijft herhalen tot een maximum van 10 herhalingen is bereikt.
* FORMS-10243: De optie Focus instellen werkt niet goed voor Adaptive Forms op basis van Core Components. Met name wanneer op een keuzerondje wordt geklikt en de regel &quot;focus instellen&quot; is ingeschakeld voor een tekstvakobject, kan de focus niet worden ingesteld zoals verwacht, ondanks andere regels die correct werken.
* FORMS-10416: Voor een Zeteloze Adaptieve Vorm, wanneer de eigenschap &quot;:type&quot; is opgenomen, wordt de component met meerdere regels ingevoerd als een gewone component voor tekstinvoer met één regel.
* FORMS-10015: Voor een adaptief formulier dat is gebaseerd op kerncomponenten, geeft het in de regeleditor, wanneer we het formulierobject kiezen, het volledige veldobject door aan de aangepaste functie in plaats van alleen de waarde van het veld.
* FORMS-9890: gebruikers in de groep van wolkenbeheerders, zonder vorm-gebruiker toegang, kunnen gegevensbronnen, formulieren, en het Model van de Gegevens van de Vorm tot stand brengen. Nochtans, kunnen zij de beschikbare diensten in het systeem niet bekijken wanneer het gebruiken van de &quot;Invoke dienst&quot;in de regelredacteur.
* FORMS-9075: Bij het verzenden van een adaptief formulier maken schermlezers niet alle foutberichten bekend voor de verplichte velden.
* FORMS-9014: De volgende toegankelijkheidsproblemen zijn opgelost:
   * Bij het openen van het krabbelhandtekeningvak slaat de cursor over naar de volgende component, niet binnen het vak zelf. Dit gedrag is bevestigd door het toegankelijkheidsteam.
   * Als u na het ondertekenen op Enter drukt, wordt het dialoogvenster niet gesloten. Gebruikers moeten expliciet op de knop OK klikken.
   * Na ondertekening wordt de tabvolgorde weer ingesteld op de bovenkant, in plaats van bij de handtekeningcomponent te blijven of naar de volgende component te gaan.
   * De optie voor het wissen van de handtekening, weergegeven door een kruispictogram, maakt geen deel uit van de tabvolgorde en wordt alleen weergegeven als u de muis boven het pictogram houdt.
   * Het dialoogvenster &quot;Handtekeningbevestiging wissen&quot; kan niet worden geopend via het toetsenbord.
   * Voor de duidelijkheid moet het label voor de toetsenbordknop worden gecorrigeerd.
   * Voor besturingselementen binnen de krabbelhandtekening ontbreekt de aanbevolen contrastverhouding.
   * De inactieve status van de knop OK/vinkje moet het kenmerk &quot;aria-uitgeschakeld&quot; bevatten.
   * De schermlezer laat de tekst die is gebruikt om de getypte handtekening te maken, onverlet, zodat deze niet toegankelijk is voor slechtzienden.
* FORMS-9214: Voor Adaptive Forms based on Core Components, wordt de Aangepaste functie niet aangeroepen, tenzij deze wordt gebruikt om een ander veld te wijzigen, zoals het instellen van de waarde van een ander veld.
* Voor API&#39;s voor het genereren van documenten geeft het pad &quot;/inhoud&quot; een inconsistentie in het gebruik weer in het sjabloonpad, de inhoudsbasis en de gegevens. Het werkt in sommige gevallen correct, maar niet uniform.
* FORMS-10718: extra ondersteuning voor de resolveNode API van GuideBridge voor Adaptive Forms op basis van Core Components.
* FORMS-9998: In Adaptive Forms gebaseerd op Core Components, werken de functies &quot;Is Empty&quot; en &quot;Is Not Empty&quot; niet zoals verwacht bij het valideren van tekstinvoer via de Rule Editor.
* FORMS-10236: De component File Attachment werkt niet correct voor Adaptive Forms op basis van Core Components. Bij gebruik van de bijlage werken voorvertoningen van bestanden in eerste instantie, maar als u extra bestanden van vergelijkbare of verschillende typen of indelingen toevoegt, functioneert de voorvertoning niet.
* FORMS-10470: in component checkbox werkt de verzendknop niet wanneer de standaardwaarde uncheck (&#39;off&#39;) en datatype String is.
* FORMS-10534: In Adaptief Forms op basis van Core Components, wordt de optie Booleaanse operand aan de linkerkant weergegeven om aan te geven dat deze selecteerbaar is. Wanneer een gebruiker echter probeert deze te selecteren, treedt een foutmarkering of een foutmelding op, wat erop wijst dat de selectie niet naar behoren functioneert.
* FORMS-10248: In Adaptive Forms gebaseerd op Core Components, werkt het instellen van de waarde van een keuzerondje of selectievakje wanneer het gegevenstype Boolean is, niet zoals verwacht.
* FORMS-8114: De datumkiezer en het patroon worden niet correct gelezen door de NVDA-schermlezer. Met name bij gebruik van de NVDA-schermlezer wordt de datumkiezer zonder patroon correct gelezen. Wanneer een patroon echter wordt toegepast op de datumkiezer, wordt het gelezen als een tabel in plaats van correct te worden geïnterpreteerd.







### Bekende problemen {#known-issues-13665}

Geen

### Ingesloten technologieën {#embedded-tech-13665}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM | 1,54-T20230817132355-3800a65 | [API 1.54.0 voor ongewenste API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.54.0/index.html) |
| AEM SLING-API | Versie 2.27.2 | [API voor Apache Sling API 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Versie 1.4.20-1.4.0 | [HTML Sjabloontaalspecificaties](https://github.com/adobe/htl-spec) |
| AEM-kerncomponenten | Versie 2.23.4 | [AEM WCM Core-componenten](https://github.com/adobe/aem-core-wcm-components) |
