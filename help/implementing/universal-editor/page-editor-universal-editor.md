---
title: Pagina-editor en Universal Editor
description: De Pagina-editor wordt nog steeds ondersteund door Adobe, maar de Universal Editor biedt geweldige mogelijkheden voor uw nieuwe projecten.
feature: Developing
role: Admin, Architect, Developer
exl-id: 0a13fb52-623e-4aff-b254-186d8d117e4d
source-git-commit: 90c542bfc6ba6bcab34b640e3539971b8b89034c
workflow-type: tm+mt
source-wordcount: '1067'
ht-degree: 0%

---

# Pagina-editor en Universal Editor {#page-editor-universal-editor}

De Pagina-editor wordt nog steeds ondersteund door Adobe, maar de Universal Editor biedt geweldige mogelijkheden voor uw nieuwe projecten.

## Achtergrond {#background}

Adobe introduceerde de [&#x200B; Universele Redacteur &#x200B;](/help/implementing/universal-editor/introduction.md) in 2024 als gestroomlijnde redacteur die een moderne op Javascript-Gebaseerde ontwikkelingsbenadering omarmt. De Universal Editor is een Adobe-visie voor een naadloze en uitbreidbare visuele ontwerpervaring met inhoud.

Erkennend de [&#x200B; rijke eigenschapreeks van de Redacteur van de Pagina &#x200B;](/help/sites-cloud/authoring/page-editor/introduction.md) en de ontelbare projecten die in het over de lange geschiedenis van AEM investeren, blijft Adobe volledig de Redacteur van de Pagina steunen, hoewel de innovatie op de Universele Redacteur zal worden geconcentreerd.

## Aanbeveling {#recommendation}

Hoewel snel het versmallen, blijft er een eigenschaphiaat tussen de Universele Redacteur en de Redacteur van de Pagina ([&#x200B; een eigenschapvergelijking kan in de volgende sectie &#x200B;](#feature-comparison) worden gevonden).

Als vuistregel geldt:

* **Nieuwe projecten** zouden aan het leveraging van de Universele Redacteur moeten in gebreke blijven.
* **de Bestaande projecten** zouden de Redacteur van de Pagina moeten blijven gebruiken en zouden de Universele Redacteur moeten overwegen wanneer het beginnen van Edge Delivery of de inspanningen van de Zwaartepunt.

**welke redacteur u kiest zou volledig door de behoeften van uw individueel project moeten worden gedreven.**

## Functievergelijking {#feature-comparison}

Omdat het eigenschaphiaat tussen de twee redacteurs constant krimpt, ben zeker om de [&#x200B; versienota&#39;s van de Universele Redacteur &#x200B;](/help/release-notes/universal-editor/current.md) voor de recentste ontwikkelingen te raadplegen.

### Aflevering {#delivery}

|  | Pagina-editor | Notities | Universele editor | Notities |
|---|---|---|---|---|
| [&#x200B; publiceer Levering &#x200B;](/help/sites-cloud/authoring/author-publish.md) | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} | Aanbevolen voor gebruik met de Core Components en traditionele AEM-projecten | [!BADGE &#x200B; niet beschikbaar &#x200B;]{type=Negative} | Traditionele AEM-pagina&#39;s zijn meestal gebaseerd op verschillende specifieke functies van de Pagina-editor die moeilijk kunnen worden gerepliceerd zoals deze in de Universal Editor worden gebruikt. |
| [&#x200B; Edge Delivery &#x200B;](/help/edge/overview.md) | [!BADGE &#x200B; niet beschikbaar &#x200B;]{type=Negative} |  | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} |  |
| [&#x200B; Hoofdloze Levering &#x200B;](/help/headless/introduction.md) | [!BADGE &#x200B; gedeeltelijk Beschikbaar &#x200B;]{type=Caution} | Slechts met [&#x200B; de Redacteur van het KUUROORD, &#x200B;](/help/implementing/developing/hybrid/introduction.md) die [&#x200B; werd afgekeurd &#x200B;](/help/implementing/developing/hybrid/spa-editor-deprecation.md) ten gunste van de Universele Redacteur | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} | Met de Universal Editor kunnen ontwikkelaars hun eigen webtoepassing gebruiken zonder specifieke frameworkvereisten of implementatiebeperkingen op te leggen. |

### Persistentie {#persistence}

|  | Pagina-editor | Notities | Universele editor | Notities |
|---|---|---|---|---|
| Paginacomponenten bewerken | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} |  | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} |  |
| Het uitgeven [&#x200B; de Fragmenten van de Inhoud &#x200B;](/help/assets/content-fragments/content-fragments.md) | [!BADGE &#x200B; niet beschikbaar &#x200B;]{type=Negative} |  | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} | Inclusief het invoegen van nieuwe fragmenten en het opnieuw ordenen van fragmenten |

### Mogelijkheden {#capabilities}

|  | Pagina-editor | Notities | Universele editor | Notities |
|---|---|---|---|---|
| Paginasjablonen | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} |  | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} | De Universal Editor is niet op de hoogte van het gebruikte sjabloonsysteem. Nochtans, begunstigt het typische implementatiepatroon ontwikkelaar-bepaalde malplaatjes, aangezien het moderne frontend tooling het voor ontwikkelaars veel gemakkelijker maakt om malplaatjelogica direct in code te bepalen en te handhaven. |
| WYSIWYG Editing | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} | Beperkt tot pagina&#39;s | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} | Pagina&#39;s en inhoudsfragmenten ondersteunen |
| [&#x200B; produceer Variaties &#x200B;](/help/generative-ai/generate-variations.md) | [!BADGE &#x200B; niet beschikbaar &#x200B;]{type=Negative} |  | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} | [&#x200B; Beschikbaar als uitbreiding &#x200B;](/help/implementing/universal-editor/extending.md) |
| Nieuw blok invoegen | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} |  | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} |  |
| Blok opnieuw ordenen | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} | Mogelijkheid met slepen en neerzetten in context, maar niet in het zijpaneel van de boomweergave | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} | Mogelijk via slepen en neerzetten in het zijpaneel van de &quot;boomweergave&quot;, maar nog niet in context (gepland) |
| Blok knippen/kopiëren-plakken | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} |  | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} |  |
| Stijlen toepassen | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} | De stijlen kunnen op componenten worden toegepast gebruikend [&#x200B; het Systeem van de Stijl.](/help/sites-cloud/authoring/page-editor/style-system.md) | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} | Stijlen kunnen worden toegepast met behulp van reguliere componenteigenschappen (of Content Fragment). Dezelfde stijlkiezer is niet beschikbaar in de Universal Editor, maar met een multiselect-widget kan een vergelijkbare UX worden bereikt. |
| Lay-out toepassen | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} | De plaatsen moeten het [&#x200B; AEM Responsieve Net &#x200B;](/help/implementing/developing/introduction/responsive-design.md) uitvoeren om auteurs toe te laten om componenten over drie vooraf bepaalde breekpunten te resize. | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} | Lay-outs kunnen worden toegepast met behulp van de eigenschappen van een gewone component (of inhoudsfragment), maar het responsieve raster wordt niet ondersteund. |
| Ongedaan maken - Opnieuw | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} |  | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} |  |
| Publiceren (ook voor voorvertoning) | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} |  | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} |  |
| [&#x200B; werkschema van het Begin &#x200B;](/help/sites-cloud/authoring/workflows/overview.md) | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} |  | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} | Beschikbaar als extensie |
| Opmerkingen | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} | Het gebruiken van [&#x200B; aantekeningen &#x200B;](/help/sites-cloud/authoring/page-editor/annotations.md) | [!BADGE &#x200B; niet beschikbaar &#x200B;]{type=Negative} | Geplant |
| Workfront-integratie | [!BADGE &#x200B; niet beschikbaar &#x200B;]{type=Negative} |  | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} | Beschikbaar als extensie |
| [&#x200B; MSM en Lanceringen &#x200B;](/help/sites-cloud/administering/msm-and-translation.md) | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} |  | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} | Beschikbaar voor pagina&#39;s als extensie |
| Experimentatie en personalisatie | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} | Het gebruiken van [&#x200B; wijze van het Doel &#x200B;](/help/sites-cloud/authoring/personalization/targeted-content.md) | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} | Beschikbaar als extensie voor Edge Delivery Services |
| Inhoudsstructuur | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} |  | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} | Staat ook het opnieuw ordenen binnen de boom toe |
| Apparaatsimulatie | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} | [&#x200B; Gevormde apparaten kunnen worden gesimuleerd, &#x200B;](/help/sites-cloud/administering/responsive-layout.md) maar de gebruiker kan geen verschillende het schermafmetingen manueel ingaan om te simuleren. | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} | [&#x200B; Om het even welke het schermafmetingen om te simuleren kunnen manueel zijn ingegaan, &#x200B;](/help/sites-cloud/authoring/universal-editor/navigation.md#emulator) maar de standaardbreekpunten kunnen niet worden gevormd. |
| [&#x200B; het sluiten van de Pagina &#x200B;](/help/sites-cloud/authoring/sites-console/managing-pages.md) | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} |  | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} | Hiermee wordt de vergrendelingsstatus van Sites-console gerespecteerd, met een extensie die beschikbaar is om pagina&#39;s van de editor te vergrendelen/ontgrendelen |
| [&#x200B; de eigenschappen van de Pagina &#x200B;](/help/sites-cloud/authoring/sites-console/edit-page-properties.md) | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} |  | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} | Beschikbaar bij Sitebeheerder, met uitbreiding om tot de eigenschappen van pagina&#39;s van de redacteur ook toegang te hebben |
| Eigenschappen voor meerdere velden | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} |  | [!BADGE &#x200B; niet beschikbaar &#x200B;]{type=Negative} | Geplant |
| [&#x200B; Verre DAM &#x200B;](/help/assets/dynamic-media-open-apis-overview.md) | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} |  | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} |  |
| [&#x200B; Pagina het versioning &#x200B;](/help/sites-cloud/authoring/sites-console/page-versions.md) | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} |  | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} |  |
| [&#x200B; TimeWarp &#x200B;](/help/sites-cloud/authoring/sites-console/page-versions.md#timewarp) en [&#x200B; Diff Mening &#x200B;](/help/sites-cloud/authoring/sites-console/page-diff.md) | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} |  | [!BADGE &#x200B; niet beschikbaar &#x200B;]{type=Negative} | Geplant |
| Weergeven in beheerder | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} |  | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} | Beschikbaar als extensie voor pagina&#39;s |
| Paginastatus weergeven | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} |  | [!BADGE &#x200B; niet beschikbaar &#x200B;]{type=Negative} | Beschikbaar in de siteconsole |
| Uitbreidbaarheid | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} | Als AEM-overlays | [!BADGE &#x200B; Beschikbaar &#x200B;]{type=Positive} | Als duidelijk gedefinieerde uitbreidingspunten met de App Builder en zeer weinig AEM-specifieke kennis |

## De Universele Editor aannemen {#adopt-ue}

De Universele Redacteur biedt vele voordelen aan, die tot het een grote oplossing voor nieuwe projecten maken.

* **Visuele het Uitgeven:** als voor de Redacteur van de Pagina, kunnen de auteurs inhoud direct binnen de voorproef uitgeven en onmiddellijk zien hoe hun veranderingen de bezoekerservaring beïnvloeden.
* **Toekomst-Bewijs:** AEM roadmap geeft voorrang aan de Universele Redacteur als visuele redacteur. Als u het aanneemt, hebt u toegang tot de nieuwste innovaties en verbeteringen.
* **Eenvoudigere Integratie:** Geen AEM-specifieke SDK wordt vereist om de Universele Redacteur te gebruiken, verminderend technologiestapelslot-binnen.
* **breng Uw Eigen Toepassing:** De Universele Redacteur steunt om het even welk Webkader of architectuur, die goedkeuring toestaat zonder het vereisen van complex refactoring.
* **Uitbreidbaarheid:** de Universele Redacteur profiteert van een robuust [&#x200B; uitbreidingskader, &#x200B;](/help/implementing/universal-editor/extending.md) met inbegrip van integratie met GenAI, Workfront, en meer.

### Migreren naar de Universal Editor {#migrate-ue}

Er is geen rechtstreeks migratiepad van de Pagina-editor naar de Universal Editor. Dit is te wijten aan fundamentele verschillen in de twee technologieën.

* De Universal Editor introduceert geen functies zoals Sjablooneditor, Stijlsysteem of Responsief raster.
   * Deze gebruiksgevallen kunnen nu efficiënter worden afgehandeld met CSS en Javascript aan de voorzijde in Edge Delivery Services of projecten zonder kop.
* Aangezien de Universele Redacteur redacteur-a-dienst is, kan het uitvoerders niet toestaan om CSS of JS in de componentendialogen te injecteren.
   * Zo voorkomt u dat dialoogvensters van componenten automatisch worden geconverteerd vanuit de Pagina-editor.
   * Dit is van invloed op veel gebieden in de dialoogvensters, zoals aangepaste widgets, veldvalidatie, tonen/verbergen van regels en op een sjabloon gebaseerde aanpassingen.
      * Terwijl dergelijke mogelijkheden nog mogelijk zijn, lost de Universele Redacteur hen door configuratie op, in plaats van douane JavaScript die in dialogen wordt opgesteld.

Hoewel de Universele Redacteur het uitgeven van pagina&#39;s voor traditionele projecten van AEM (b.v. gebouwd met de Componenten van de Kern) technisch kan toelaten, baseren deze plaatsen zich typisch op verscheidene de redacteur-specifieke eigenschappen van de Pagina, zoals het Systeem van de Stijl, het Responsieve Net, Bewerkbare Malplaatjes, en douane Javascript binnen dialogen.

Aangezien de Universele Redacteur een meer gestroomlijnde, moderne benadering volgt die deze erfeniseigenschappen niet steunt, zou het migreren van dergelijke plaatsen significante reactoring vereisen. Om deze reden, {worden de 0} migrerende plaatsen van de Redacteur van de Pagina aan de Universele Redacteur slechts geadviseerd voor projecten die aan Edge Delivery Services overgaan.**&#x200B;**
