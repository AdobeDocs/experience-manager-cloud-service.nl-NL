---
title: Pagina-editor en Universal Editor
description: De Pagina-editor wordt nog steeds ondersteund door Adobe, maar de Universal Editor biedt geweldige mogelijkheden voor uw nieuwe projecten.
feature: Developing
role: Admin, Architect, Developer
exl-id: 0a13fb52-623e-4aff-b254-186d8d117e4d
source-git-commit: fd52e51c336e65ae698c5102cbe00b90e7038b5e
workflow-type: tm+mt
source-wordcount: '1068'
ht-degree: 0%

---

# Pagina-editor en Universal Editor {#page-editor-universal-editor}

De Pagina-editor wordt nog steeds ondersteund door Adobe, maar de Universal Editor biedt geweldige mogelijkheden voor uw nieuwe projecten.

## Achtergrond {#background}

Adobe introduceerde de [ Universele Redacteur ](/help/implementing/universal-editor/introduction.md) in 2024 als gestroomlijnde redacteur die een moderne op Javascript-Gebaseerde ontwikkelingsbenadering omarmt. De Universal Editor is een Adobe-visie voor een naadloze en uitbreidbare visuele ontwerpervaring met inhoud.

Erkennend de [ rijke eigenschapreeks van de Redacteur van de Pagina ](/help/sites-cloud/authoring/page-editor/introduction.md) en de ontelbare projecten die in het over de lange geschiedenis van AEM investeren, blijft Adobe volledig de Redacteur van de Pagina steunen, hoewel de innovatie op de Universele Redacteur zal worden geconcentreerd.

## Aanbeveling {#recommendation}

Hoewel snel het versmallen, blijft er een eigenschaphiaat tussen de Universele Redacteur en de Redacteur van de Pagina ([ een eigenschapvergelijking kan in de volgende sectie ](#feature-comparison) worden gevonden).

Als vuistregel geldt:

* **Nieuwe projecten** zouden aan het leveraging van de Universele Redacteur moeten in gebreke blijven.
* **de Bestaande projecten** zouden de Redacteur van de Pagina moeten blijven gebruiken en zouden de Universele Redacteur moeten overwegen wanneer het beginnen van Edge Delivery of de inspanningen van de Zwaartepunt.

**welke redacteur u kiest zou volledig door de behoeften van uw individueel project moeten worden gedreven.**

## Functievergelijking {#feature-comparison}

Omdat het eigenschaphiaat tussen de twee redacteurs constant krimpt, ben zeker om de [ versienota&#39;s van de Universele Redacteur ](/help/release-notes/universal-editor/current.md) voor de recentste ontwikkelingen te raadplegen.

### Aflevering {#delivery}

|  | Pagina-editor | Notities | Universele editor | Notities |
|---|---|---|---|---|
| [ publiceer Levering ](/help/sites-cloud/authoring/author-publish.md) | [!BADGE  Beschikbaar ]{type=Positive} | Aanbevolen voor gebruik met de Core Components en traditionele AEM-projecten | [!BADGE  niet beschikbaar ]{type=Negative} | Traditionele AEM-pagina&#39;s zijn meestal gebaseerd op verschillende specifieke functies van de Pagina-editor die moeilijk kunnen worden gerepliceerd zoals deze in de Universal Editor worden gebruikt. |
| [ Edge Delivery ](/help/edge/overview.md) | [!BADGE  niet beschikbaar ]{type=Negative} |  | [!BADGE  Beschikbaar ]{type=Positive} |  |
| [ Hoofdloze Levering ](/help/headless/introduction.md) | [!BADGE  gedeeltelijk Beschikbaar ]{type=Caution} | Slechts met [ de Redacteur van het KUUROORD, ](/help/implementing/developing/hybrid/introduction.md) die [ werd afgekeurd ](/help/implementing/developing/hybrid/spa-editor-deprecation.md) ten gunste van de Universele Redacteur | [!BADGE  Beschikbaar ]{type=Positive} | Met de Universal Editor kunnen ontwikkelaars hun eigen webtoepassing gebruiken zonder specifieke frameworkvereisten of implementatiebeperkingen op te leggen. |

### Persistentie {#persistence}

|  | Pagina-editor | Notities | Universele editor | Notities |
|---|---|---|---|---|
| Paginacomponenten bewerken | [!BADGE  Beschikbaar ]{type=Positive} |  | [!BADGE  Beschikbaar ]{type=Positive} |  |
| Het uitgeven [ de Fragmenten van de Inhoud ](/help/assets/content-fragments/content-fragments.md) | [!BADGE  niet beschikbaar ]{type=Negative} |  | [!BADGE  Beschikbaar ]{type=Positive} | Inclusief het invoegen van nieuwe fragmenten en het opnieuw ordenen van fragmenten |

### Mogelijkheden {#capabilities}

|  | Pagina-editor | Notities | Universele editor | Notities |
|---|---|---|---|---|
| Paginasjablonen | [!BADGE  Beschikbaar ]{type=Positive} |  | [!BADGE  Beschikbaar ]{type=Positive} | De Universal Editor is niet op de hoogte van het gebruikte sjabloonsysteem. Nochtans, begunstigt het typische implementatiepatroon ontwikkelaar-bepaalde malplaatjes, aangezien het moderne frontend tooling het voor ontwikkelaars veel gemakkelijker maakt om malplaatjelogica direct in code te bepalen en te handhaven. |
| WYSIWYG Editing | [!BADGE  Beschikbaar ]{type=Positive} | Beperkt tot pagina&#39;s | [!BADGE  Beschikbaar ]{type=Positive} | Pagina&#39;s en inhoudsfragmenten ondersteunen |
| [ produceer Variaties ](/help/generative-ai/generate-variations.md) | [!BADGE  niet beschikbaar ]{type=Negative} |  | [!BADGE  Beschikbaar ]{type=Positive} | [ Beschikbaar als uitbreiding ](/help/implementing/universal-editor/extending.md) |
| Nieuw blok invoegen | [!BADGE  Beschikbaar ]{type=Positive} |  | [!BADGE  Beschikbaar ]{type=Positive} |  |
| Blok opnieuw ordenen | [!BADGE  Beschikbaar ]{type=Positive} | Mogelijkheid met slepen en neerzetten in context, maar niet in het zijpaneel van de boomweergave | [!BADGE  Beschikbaar ]{type=Positive} | Mogelijk via slepen en neerzetten in het zijpaneel van de &quot;boomweergave&quot;, maar nog niet in context (gepland) |
| Blok knippen/kopiëren-plakken | [!BADGE  Beschikbaar ]{type=Positive} |  | [!BADGE  niet beschikbaar ]{type=Negative} | Geplant |
| Stijlen toepassen | [!BADGE  Beschikbaar ]{type=Positive} | De stijlen kunnen op componenten worden toegepast gebruikend [ het Systeem van de Stijl.](/help/sites-cloud/authoring/page-editor/style-system.md) | [!BADGE  Beschikbaar ]{type=Positive} | Stijlen kunnen worden toegepast met behulp van reguliere componenteigenschappen (of Content Fragment). Dezelfde stijlkiezer is niet beschikbaar in de Universal Editor, maar met een multiselect-widget kan een vergelijkbare UX worden bereikt. |
| Lay-out toepassen | [!BADGE  Beschikbaar ]{type=Positive} | De plaatsen moeten het [ AEM Responsieve Net ](/help/implementing/developing/introduction/responsive-design.md) uitvoeren om auteurs toe te laten om componenten over drie vooraf bepaalde breekpunten te resize. | [!BADGE  Beschikbaar ]{type=Positive} | Lay-outs kunnen worden toegepast met behulp van de eigenschappen van een gewone component (of inhoudsfragment), maar het responsieve raster wordt niet ondersteund. |
| Ongedaan maken - Opnieuw | [!BADGE  Beschikbaar ]{type=Positive} |  | [!BADGE  Beschikbaar ]{type=Positive} |  |
| Publiceren (ook voor voorvertoning) | [!BADGE  Beschikbaar ]{type=Positive} |  | [!BADGE  Beschikbaar ]{type=Positive} |  |
| [ werkschema van het Begin ](/help/sites-cloud/authoring/workflows/overview.md) | [!BADGE  Beschikbaar ]{type=Positive} |  | [!BADGE  Beschikbaar ]{type=Positive} | Beschikbaar als extensie |
| Opmerkingen | [!BADGE  Beschikbaar ]{type=Positive} | Het gebruiken van [ aantekeningen ](/help/sites-cloud/authoring/page-editor/annotations.md) | [!BADGE  niet beschikbaar ]{type=Negative} | Geplant |
| Workfront-integratie | [!BADGE  niet beschikbaar ]{type=Negative} |  | [!BADGE  Beschikbaar ]{type=Positive} | Beschikbaar als extensie |
| [ MSM en Lanceringen ](/help/sites-cloud/administering/msm-and-translation.md) | [!BADGE  Beschikbaar ]{type=Positive} |  | [!BADGE  Beschikbaar ]{type=Positive} | Beschikbaar voor pagina&#39;s als extensie |
| Experimentatie en personalisatie | [!BADGE  Beschikbaar ]{type=Positive} | Het gebruiken van [ wijze van het Doel ](/help/sites-cloud/authoring/personalization/targeted-content.md) | [!BADGE  Beschikbaar ]{type=Positive} | Beschikbaar als extensie voor Edge Delivery Services |
| Inhoudsstructuur | [!BADGE  Beschikbaar ]{type=Positive} |  | [!BADGE  Beschikbaar ]{type=Positive} | Staat ook het opnieuw ordenen binnen de boom toe |
| Apparaatsimulatie | [!BADGE  Beschikbaar ]{type=Positive} | [ Gevormde apparaten kunnen worden gesimuleerd, ](/help/sites-cloud/administering/responsive-layout.md) maar de gebruiker kan geen verschillende het schermafmetingen manueel ingaan om te simuleren. | [!BADGE  Beschikbaar ]{type=Positive} | [ Om het even welke het schermafmetingen om te simuleren kunnen manueel zijn ingegaan, ](/help/sites-cloud/authoring/universal-editor/navigation.md#emulator) maar de standaardbreekpunten kunnen niet worden gevormd. |
| [ het sluiten van de Pagina ](/help/sites-cloud/authoring/sites-console/managing-pages.md) | [!BADGE  Beschikbaar ]{type=Positive} |  | [!BADGE  Beschikbaar ]{type=Positive} | Hiermee wordt de vergrendelingsstatus van Sites-console gerespecteerd, met een extensie die beschikbaar is om pagina&#39;s van de editor te vergrendelen/ontgrendelen |
| [ de eigenschappen van de Pagina ](/help/sites-cloud/authoring/sites-console/edit-page-properties.md) | [!BADGE  Beschikbaar ]{type=Positive} |  | [!BADGE  Beschikbaar ]{type=Positive} | Beschikbaar bij Sitebeheerder, met uitbreiding om tot de eigenschappen van pagina&#39;s van de redacteur ook toegang te hebben |
| Eigenschappen voor meerdere velden | [!BADGE  Beschikbaar ]{type=Positive} |  | [!BADGE  niet beschikbaar ]{type=Negative} | Geplant |
| [ Verre DAM ](/help/assets/dynamic-media-open-apis-overview.md) | [!BADGE  Beschikbaar ]{type=Positive} |  | [!BADGE  Beschikbaar ]{type=Positive} |  |
| [ Pagina het versioning ](/help/sites-cloud/authoring/sites-console/page-versions.md) | [!BADGE  Beschikbaar ]{type=Positive} |  | [!BADGE  Beschikbaar ]{type=Positive} |  |
| [ TimeWarp ](/help/sites-cloud/authoring/sites-console/page-versions.md#timewarp) en [ Diff Mening ](/help/sites-cloud/authoring/sites-console/page-diff.md) | [!BADGE  Beschikbaar ]{type=Positive} |  | [!BADGE  niet beschikbaar ]{type=Negative} | Geplant |
| Weergeven in beheerder | [!BADGE  Beschikbaar ]{type=Positive} |  | [!BADGE  Beschikbaar ]{type=Positive} | Beschikbaar als extensie voor pagina&#39;s |
| Paginastatus weergeven | [!BADGE  Beschikbaar ]{type=Positive} |  | [!BADGE  niet beschikbaar ]{type=Negative} | Beschikbaar in de siteconsole |
| Uitbreidbaarheid | [!BADGE  Beschikbaar ]{type=Positive} | Als AEM-overlays | [!BADGE  Beschikbaar ]{type=Positive} | Als duidelijk gedefinieerde uitbreidingspunten met de App Builder en zeer weinig AEM-specifieke kennis |

## De Universele Editor aannemen {#adopt-ue}

De Universele Redacteur biedt vele voordelen aan, die tot het een grote oplossing voor nieuwe projecten maken.

* **Visuele het Uitgeven:** als voor de Redacteur van de Pagina, kunnen de auteurs inhoud direct binnen de voorproef uitgeven en onmiddellijk zien hoe hun veranderingen de bezoekerservaring beïnvloeden.
* **Toekomst-Bewijs:** AEM roadmap geeft voorrang aan de Universele Redacteur als visuele redacteur. Als u het aanneemt, hebt u toegang tot de nieuwste innovaties en verbeteringen.
* **Eenvoudigere Integratie:** Geen AEM-specifieke SDK wordt vereist om de Universele Redacteur te gebruiken, verminderend technologiestapelslot-binnen.
* **breng Uw Eigen Toepassing:** De Universele Redacteur steunt om het even welk Webkader of architectuur, die goedkeuring toestaat zonder het vereisen van complex refactoring.
* **Uitbreidbaarheid:** de Universele Redacteur profiteert van een robuust [ uitbreidingskader, ](/help/implementing/universal-editor/extending.md) met inbegrip van integratie met GenAI, Workfront, en meer.

### Migreren naar de Universal Editor {#migrate-ue}

Er is geen rechtstreeks migratiepad van de Pagina-editor naar de Universal Editor. Dit is te wijten aan fundamentele verschillen in de twee technologieën.

* De Universal Editor introduceert geen functies zoals Sjablooneditor, Stijlsysteem of Responsief raster.
   * Deze gebruiksgevallen kunnen nu efficiënter worden afgehandeld met CSS en Javascript aan de voorzijde in Edge Delivery Services of projecten zonder kop.
* Aangezien de Universele Redacteur redacteur-a-dienst is, kan het uitvoerders niet toestaan om CSS of JS in de componentendialogen te injecteren.
   * Zo voorkomt u dat dialoogvensters van componenten automatisch worden geconverteerd vanuit de Pagina-editor.
   * Dit is van invloed op veel gebieden in de dialoogvensters, zoals aangepaste widgets, veldvalidatie, tonen/verbergen van regels en op een sjabloon gebaseerde aanpassingen.
      * Terwijl dergelijke mogelijkheden nog mogelijk zijn, lost de Universele Redacteur hen door configuratie op, in plaats van douane JavaScript die in dialogen wordt opgesteld.

Hoewel de Universele Redacteur het uitgeven van pagina&#39;s voor traditionele projecten van AEM (b.v. gebouwd met de Componenten van de Kern) technisch kan toelaten, baseren deze plaatsen zich typisch op verscheidene de redacteur-specifieke eigenschappen van de Pagina, zoals het Systeem van de Stijl, het Responsieve Net, Bewerkbare Malplaatjes, en douane Javascript binnen dialogen.

Aangezien de Universele Redacteur een meer gestroomlijnde, moderne benadering volgt die deze erfeniseigenschappen niet steunt, zou het migreren van dergelijke plaatsen significante reactoring vereisen. Om deze reden, {worden de 0} migrerende plaatsen van de Redacteur van de Pagina aan de Universele Redacteur slechts geadviseerd voor projecten die aan Edge Delivery Services overgaan.****
