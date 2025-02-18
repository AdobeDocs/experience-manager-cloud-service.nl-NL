---
title: Introductie van Universal Editor
description: De Universele Redacteur is een modern visueel auteursgereedschap dat wordt ontworpen om uw marketing organisatie te machtigen om uitvoerbare Webervaringen te produceren.
exl-id: d4fc2384-a0f5-4a6f-9572-62749786be4c
feature: Developing
role: Admin, Architect, Developer
source-git-commit: c88aa13c6bc75c8f9cd624d00ef768290981c840
workflow-type: tm+mt
source-wordcount: '949'
ht-degree: 0%

---


# Introductie van Universal Editor {#introduction}

De Universele Redacteur is een modern visueel auteursgereedschap dat wordt ontworpen om uw marketing organisatie te machtigen om uitvoerbare Webervaringen te produceren.

## Overzicht {#overview}

De Universal Editor is een veelzijdige visuele editor die deel uitmaakt van Adobe Experience Manager Sites. Auteurs kunnen hiermee &#39;what-you-see-is-what-you-get&#39; (WYSIWYG)-bewerkingen uitvoeren van elke headless- of headful-ervaring. Het biedt:

* **Onmiddellijk het Uitgeven**: De auteurs kunnen inhoud direct binnen de voorproefervaring uitgeven, die de behoefte elimineren om van naar individuele inhoudsbronnen de plaats te bepalen en te navigeren.
* **Visuele het Uitgeven**: Terwijl het aanbrengen van veranderingen, zien de auteurs onmiddellijk hoe zij de daadwerkelijke bezoekerservaring beïnvloeden, minimaliserend wrijving.
* **Ontdekking Opties**: Duidelijk geëtiketteerde opties en een intuïtieve UI machtigen auteurs om meta-gegevens te vormen en lay-outs samen te stellen met gemak.
* **niet-Technisch**: Geen gespecialiseerde deskundigheid wordt vereist om uit te geven, terwijl de collectieve merkrichtlijnen automatisch worden afgedwongen, die het schrapen van inhoudstaken over uw organisatie vergemakkelijken.
* **Integratie en Uitbreidbaarheid**: Volledig geïntegreerd met AEM, staan de flexibele [ uitbreidingspunten van de Universele Redacteur ](#extensibility) alle essentiële hulpmiddelen toe om binnen één enkele, samenhangende interface worden verenigd. Van AI-functies tot aangepaste extensies die zijn afgestemd op uw unieke bedrijfsbehoeften, stelt het teams in staat werkstromen te stroomlijnen en de productiviteit moeiteloos te verbeteren.

Samenvattend:

* **de Auteurs profiteren** van de flexibiliteit van de Universele Redacteur aangezien het het zelfde verenigbare visuele uitgeven voor alle vormen van de inhoud van AEM steunt.
* **de Ontwikkelaars profiteren** van de veelzijdigheid van de Universele Redacteur aangezien het ware ontkoppeling van de implementatie steunt.

Omdat ware redacteur-a-a-dienst en over het algemeen flexibeler is, is de Universele Redacteur van plan om uiteindelijk de [ Redacteur van de Pagina te vervangen.](/help/sites-cloud/authoring/page-editor/introduction.md)

## Ondersteunde architecturen {#supported-architectures}

De Universal Editor ondersteunt de volgende twee primaire AEM-instellingen:

1. **[Edge Delivery Services](/help/edge/overview.md)**: Dit is de aangewezen benadering voor zijn eenvoud, snellere tijd-aan-waarde, en verbeterde prestaties.
1. **[Hoofdloze Implementaties](/help/headless/introduction.md)**: Als u een bestaand hoofdloos project of specifieke vereisten voor ontkoppelde het teruggeven hebt, staat de Universele Redacteur visuele het uitgeven van ondernemingskwaliteit zonder de behoefte toe om het volledige project te weerspiegelen. Het is compatibel met vrijwel elke architectuur (SSR, CSR), webframework (Next.js, React, Astro, enz.) en hostingmodellen (&quot;breng uw eigen app&quot;).

>[!TIP]
>
>Gelieve te zien het document [ Universele Gevallen van het Gebruik van de Redacteur en het Leren Wegen ](/help/implementing/universal-editor/use-cases.md) voor meer details op de gesteunde architectuur.

## Ondersteunde AEM-versies {#aem-versions}

De Universal Editor wordt ondersteund door:

* AEM as a Cloud Service (release `2023.8.13099` of hoger)
* AEM 6.5 (servicepack 21 of 22 plus een functiepakket)

Deze documentatie is bedoeld voor gebruik van de Universal Editor met AEM as a Cloud Service. Voor het gebruiken van de Universele Redacteur met AEM 6.5, [ gelieve te zien AEM 6.5 documentatie.](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/developing/headless/universal-editor/introduction)

## Functies {#features}

De Universele Redacteur biedt vele eigenschappen aan om een brede waaier van gebruiksgevallen voor efficiënt inhoudsbeheer te steunen.

* **[WYSIWYG](/help/sites-cloud/authoring/universal-editor/authoring.md)**: Voer uit wat-u-ziet-is-wat-u-krijgt het uitgeven van om het even welke vorm van Webinhoud, met inbegrip van gewone teksten, rijke teksten, media, en meta-gegevens.
* **[Samenstelling](/help/sites-cloud/authoring/universal-editor/authoring.md#editing-content)**: Creeer, geef uit, herordend, nestel, of schrap inhoudsblokken van diverse types (titels, knopen, tellers, secties, bed, enz. in).
* **[Lay-out](/help/sites-cloud/authoring/universal-editor/templates.md)**: Gebruik paginasjablonen, pas visuele stijlen toe, en stel lay-outs met blokken zoals kolommen, carrousels, en accordeons samen.
* **[Simulatie van het Apparaat](/help/sites-cloud/authoring/universal-editor/navigation.md#emulator)**: Voorproef en optimaliseer inhoud voor verschillende bezoekersapparaten terwijl het uitgeven.
* **Omnichannel**: Hergebruik zowel gestructureerde als ongestructureerde inhoud over veelvoudige kanalen.
* **[Localization](/help/sites-cloud/authoring/universal-editor/inheritance.md)**: De werkschema&#39;s van de de inhoudvertaling van de stroomlijn en behandelt efficiënt gelokaliseerde inhoudsovererving met de Manager van de multi-Plaats.
* **Consistentie**: Verzeker naleving van merkrichtlijnen en handhaaf uniformiteit over alle inhoud.
* **Veiligheid**: [ dwingt toegangscontrole ](/help/implementing/universal-editor/authentication.md) af, beschermt inhoudsintegriteit, en spoorveranderingen met [ robuuste versioning.](/help/sites-cloud/authoring/sites-console/page-versions.md)
* **[het Publiceren](/help/sites-cloud/authoring/universal-editor/publishing.md)**: Integreer overzicht, goedkeuring, en publicatiewerkschema&#39;s direct binnen de redacteur.
* **verenigd**: integreert volledig met de hulpmiddelen van AEM zoals de [ Console van Plaatsen, ](/help/sites-cloud/authoring/sites-console/introduction.md) [ de Redacteur van het Fragment van de Inhoud, ](/help/sites-cloud/administering/content-fragments/overview.md) en vele meer, die een samenhangende auteurservaring verstrekken.

## Uitbreidbaarheid {#extensibility}

De Universele Redacteur is niet alleen zeer geschikt uit-van-de-doos, maar biedt een aantal uitbreidingsmogelijkheden.

* **de Uitbreidingen** zijn talrijke en klaar-gemaakt om vereisten zoals het steunen van werkschema&#39;s te steunen, die variaties produceren, en toelatend experimenteren om enkelen te noemen.
* **Verlengbare UI** staat u toe om uw eigen uitbreidingen tot stand te brengen gebruikend het zelfde onderliggende kader dat de kant-en-klare uitbreidingen hefboomwerking toelatend uiteindelijke flexibiliteit om aan uw projectbehoeften aan te passen.
* **de Punten van de Uitbreiding** zoals blokken, de types van douanegegevens, en gebeurtenissen staan voor naadloze integratie van douanebedrijfsvereisten voorbij UI toe.

>[!TIP]
>
>Voor meer informatie over de rekbaarheid van de Universele Redacteur, te zien gelieve het document [ Uitbreidend de Universele Redacteur.](/help/implementing/universal-editor/extending.md)

## De Universal Editor en de Content Fragment Editor {#universal-editor-content-fragment-editor}

Op het eerste gezicht lijken de Universal Editor en de Content Fragment Editor vergelijkbare bewerkingsmogelijkheden. Deze editors bieden echter zeer verschillende mogelijkheden en vervullen verschillende taken van de marketingdeskundige.

### Inhoudsfragmenteditor {#content-fragment-editor}

Een marketingdeskundige wil inhoud maken zonder de layout ervan te hoeven omschrijven, zodat deze in een groot aantal contexten opnieuw kan worden gebruikt.

* De onderliggende taak die moet worden uitgevoerd, is het schalen van de inhoudsstrategie.

### Universele editor {#universal-editor}

Een marketingdeskundige wil inhoud maken die is toegesneden op de lay-out van een bepaalde context en die een uitzonderlijke ervaring biedt.

* De onderliggende taak die u moet uitvoeren, is op overtuigende wijze verbinding maken met de lezers.

## Beperkingen {#limitations}

Houd rekening met de volgende beperkingen wanneer u de Universal Editor verkent en de implementatie ervan in uw eigen projecten doorvoert.

* Niet meer dan 25 AEM-bronnen (Content Fragments, pages, Experience Fragments, Assets, enz.) mogen als instrumentatie op één pagina worden gebruikt.
* AEM as a Cloud Service en [ AEM 6.5 ](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/developing/headless/universal-editor/introduction) zijn de enige gesteunde AEM achtergronden.
* Release `2023.8.13099` of hoger is vereist voor AEM as a Cloud Service.
* Inhoudsauteurs moeten een eigen Experience Cloud-account hebben.
* Als deel van AEM, steunt de Universele Redacteur [ zelfde Desktopbrowsers zoals AEM.](/help/overview/supported-platforms.md)
   * Mobiele versies van deze browsers worden niet ondersteund.

{{ue-ip-allow-lists}}

## Volgende stappen {#next-steps}

Gelieve te zien het document [ Universele Gevallen van het Gebruik van de Redacteur en het Leren Wegen ](/help/implementing/universal-editor/use-cases.md) om meer over gemeenschappelijke gebruiksgevallen voor de Universele Redacteur te leren en de juiste documentatiemiddelen te ontdekken om u in uw project te steunen.
