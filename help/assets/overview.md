---
title: Introductie van Assets as a Cloud Service voor Digital Asset Management in AEM
description: Introductie van Assets as a Cloud Service voor Digital Asset Management in AEM
exl-id: 4437f214-d058-4975-8b8f-869a12c8103b
source-git-commit: f72f72e87dabe89cafc0a56feb35f58ae1a97dfb
workflow-type: tm+mt
source-wordcount: '5078'
ht-degree: 0%

---

# Introductie van Assets as a Cloud Service voor Digital Asset Management in AEM {#assets-as-cloud-service-digital-asset-management-aem}

AEM Assets as a Cloud Service biedt een geïntegreerde, PaaS-oplossing in de cloud voor bedrijven, niet alleen om hun Digital Asset Management en Dynamic Media-bewerkingen uit te voeren, maar ook om slimme mogelijkheden van de volgende generatie te gebruiken, zoals AI/ML. Allemaal vanuit een systeem dat altijd actueel, altijd beschikbaar en altijd leerend is.

Adobe biedt robuuste DAM-oplossingen (Digital Asset Management) waarmee u optimaal kunt profiteren van uw digitale middelen. Adobe Experience Manager Assets heeft twee aparte ervaringen die dezelfde Cloud Services-opslagplaats gebruiken om aan uw vereisten te voldoen. Voor informatie over op persona-Gebaseerde ervaringen voor AEM Assets, zie [&#x200B; Beschikbare op persona-Gebaseerde ervaringen voor het Digitale Beheer van Activa &#x200B;](#persona-based-experiences).

Voor informatie over het dienstenaanbod van AEM Assets Ultimate en AEM Assets Prime, zie [&#x200B; Assets as a Cloud Service Ultimate &#x200B;](/help/assets/assets-ultimate-overview.md) en [&#x200B; Assets as a Cloud Service &#x200B;](/help/assets/assets-prime.md).

Enkele van de belangrijkste functies van Adobe Digital Asset Management zijn:

![&#x200B; toe:voegen-markeringen &#x200B;](assets/aem-assets-features-landing-page.png)


>[!BEGINTABS]

>[!TAB  Ingestie van Activa ]

## Inname van bedrijfsmiddelen {#asset-ingestion}

Met de functie voor bulkimport kunt u een groot aantal assets rechtstreeks vanuit een gegevensbron importeren naar Assets as a Cloud Service, zoals Azure, AWS, Google Cloud, Dropbox en OneDrive.

U kunt de bulkimportbewerking uitvoeren met de Admin-weergave of de Assets-weergave. De Assets-weergave biedt meer gegevensbronopties dan de Admin-weergave.

Naast de gebruikersinterface van de webbrowser ondersteunt Experience Manager andere clients op het bureaublad. Zij verstrekken ook uploadervaring zonder de behoefte om naar browser van het Web te gaan.

* Adobe Asset Link biedt toegang tot middelen van Experience Manager in Adobe Photoshop-, Adobe Illustrator- en Adobe InDesign-bureaubladtoepassingen. U kunt het geopende document uploaden naar Experience Manager. U kunt dit rechtstreeks doen via de Adobe Asset Link-interface in deze bureaubladtoepassingen.

* De Experience Manager-bureaubladtoepassing vereenvoudigt het werken met middelen op het bureaublad, onafhankelijk van het bestandstype of de oorspronkelijke toepassing die deze afhandelt. Het is handig om bestanden in geneste maphiërarchieën vanuit uw lokale bestandssysteem te uploaden, omdat het uploaden van de browser alleen het uploaden van platte bestandslijsten ondersteunt.

Gebruik de volgende koppelingen voor gedetailleerde documentatie over deze gereedschappen voor het opnemen van elementen:

<table>
<td>
   <a href="/help/assets/bulk-import-assets-view.md">
   <img alt="Gereedschap Bulk importeren" src="./assets/bulk-images.jpeg" />
   </a>
   <div>
      <a href="/help/assets/bulk-import-assets-view.md">
      <strong> het Bulk hulpmiddel van de Invoer van het Gebruik </strong>
      </a>
   </div>
   <p>
      <em> Leer hoe te om een groot aantal activa direct uit een gegevensbron in te voeren </em>
   </p>
</td>


<td>
   <a href="https://experienceleague.adobe.com/en/docs/experience-manager-desktop-app/using/get-started">
   <img alt="AEM-bureaubladtoepassing gebruiken" src="./assets/desktop-app-upload.jpeg" />
   </a>
   <div>
      <a href="https://experienceleague.adobe.com/en/docs/experience-manager-desktop-app/using/get-started">
      <strong> Desktop app van AEM van het Gebruik &lbrace;</strong>
      </a>
   </div>
   <p>
      <em> Leer hoe te om de Desktopapp van AEM te gebruiken om dossiers in genestelde omslaghiërarchieën van uw lokaal dossiersysteem te uploaden.</em>
   </p>
</td>
<td>
   <a href="https://helpx.adobe.com/enterprise/using/adobe-asset-link.html">
   <img alt="Adobe Asset Link gebruiken" src="./assets/adobe-asset-link.jpeg" />
   </a>
   <div>
      <a href="https://helpx.adobe.com/enterprise/using/adobe-asset-link.html">
      <strong> de Verband van Activa van Adobe van het Gebruik </strong>
      </a>
   </div>
   <p>
      <em> Leer hoe te om activa aan Experience Manager te uploaden gebruikend de toepassingen van Creative Cloud.</em>
   </p>
</td>
</table>

>[!TAB  AI-Aangedreven eigenschappen ]

**Slimme Markeringen**: De Slimme Markeringen gebruiken het kunstmatig intelligente kader van Adobe Sensei om zijn algoritme van de beelderkenning op uw markeringsstructuur en bedrijfstaxonomie te trainen. Deze inhoudsinfo wordt vervolgens gebruikt om relevante tags toe te passen op een andere set elementen. AEM past standaard automatisch slimme tags toe op geüploade elementen.

**Intelligente op kleur-gebaseerde Tagging &amp; Onderzoek**: AEM Assets gebruikt de mogelijkheden van Adobe Sensei AI om tussen kleuren in een beeld te onderscheiden en die eigenschappen als markeringen automatisch op opname toe te passen. Deze tags maken een verbeterde zoekervaring mogelijk op basis van de compositie van de afbeeldingskleur.

**AI-Gegenereerde meta-gegevens**: AEM Assets gebruikt AI om meta-gegevens, met inbegrip van Titel, Beschrijving, en Sleutelwoorden automatisch te produceren. Deze door AI gegenereerde velden verbeteren de nauwkeurigheid van metagegevens, waardoor de elementen gemakkelijker kunnen worden doorzocht, ingedeeld en aanbevolen. Deze aanpak verbetert niet alleen de efficiëntie door handmatige codering te elimineren, maar zorgt ook voor consistentie en schaalbaarheid op grote volumes digitale inhoud.

**AI-Gerichte activa bulksgewijs anders noemen**: [&#x200B; de mening van Assets staat u toe om veelvoudige activa in één keer anders te noemen gebruikend de Kunstmatige Intelligentie &#x200B;](/help/assets/bulk-rename-assets-view.md). U kunt meerdere bestanden tegelijk selecteren en de naam van alle bestanden tegelijk wijzigen. Sommige van het voorbeeld omzettend anders noemen herinneringen omvatten *Verandering alle dossiers in &quot;my-file&quot;en voeg een het stijgen aantal* toe en *Prefix de dossiers met 001, 002, enz. en vertaal in het Engels*.

<table>
<td>
   <a href="/help/assets/smart-tags.md">
   <img alt="Slimme tags in AEM Assets" src="./assets/smart-tags-ai.jpeg" />
   </a>
   <div>
      <a href="/help/assets/smart-tags.md">
      <strong> voeg AI Slimme Markeringen aan activa </strong> toe
      </a>
   </div>
   <p>
      <em> leer hoe te om slimme markeringen automatisch op geuploade activa toe te passen.</em>
   </p>
</td>


<td>
   <a href="/help/assets/color-tag-images.md">
   <img alt="Intelligente op kleuren gebaseerde tags toevoegen" src="./assets/color-tags.jpg" />
   </a>
   <div>
      <a href="/help/assets/manage-notifications-assets-view.md">
      <strong> voeg Intelligente op kleur-gebaseerde markeringen </strong> toe
      </a>
   </div>
   <p>
      <em> leer hoe te om kleur-gebaseerde markeringen automatisch op opname toe te passen.</em>
   </p>
</td>
<td>
   <a href="/help/assets/metadata-assets-view.md">
   <img alt="Door AI gegenereerde metagegevens" src="./assets/ai-generated-metadata-landing.jpg" />
   </a>
   <div>
      <a href="/help/assets/metadata-assets-view.md">
      <strong> AI-Gegenereerde meta-gegevens </strong>
      </a>
   </div>
   <p>
      <em> gebruik AI om activa meta-gegevens, zoals Titel en Beschrijving te produceren. </em>
   </p>
</td>
</table>

**Contextafhankelijke Onderzoek**: AEM Assets laat u activa zoeken beschikbaar in de bewaarplaats door tekstherinneringen te bepalen. Experience Manager Assets transformeert automatisch de tekstvragen om filters te zoeken en geeft de zoekresultaten weer. U kunt automatische filters weergeven en wijzigen met het deelvenster Filters om de zoekresultaten verder te beperken. Enkele voorbeelden van de vraag naar conversatietekst bevatten het volgende:

* *Beelden minstens 200px hoog en 100px breed met strand en duidelijke lucht* en
* *ik heb beelden van blauwe lucht nodig die 1500 en 2500 pixelhoogte zijn en in de afgelopen maand worden gecreeerd die niet verlopen is en goedgekeurd*.

**produceer activa gebruikend Adobe Firefly binnen AEM**: AEM Assets staat u toe om activa te produceren, als uw onderzoeksvraag geen resultaten terugkeert, gebruikend Adobe Firefly in real time. AEM Assets stelt u vervolgens in staat het gegenereerde image vanuit de AEM Assets-gebruikersinterface te uploaden naar de AEM Assets-opslagplaats.

**Integratie met Adobe Express**: AEM Assets integreert binnen met Adobe Express, die u toestaat om tot de activa toegang te hebben die direct in AEM Assets van binnen het gebruikersinterface van Adobe Express worden opgeslagen. U kunt ook Adobe Firefly Artificial Intelligence gebruiken in Express om afbeeldingen te genereren met behulp van eenvoudige tekstaanwijzingen en deze op Express canvas te plaatsen. U kunt vervolgens nieuwe of bewerkte inhoud opslaan in een AEM Assets-opslagplaats.

<table>
<td>
   <a href="/help/assets/search-assets-view.md#contextual-search">
   <img alt="Contextueel zoeken" src="./assets/ai-based-search.jpg" />
   </a>
   <div>
      <a href="/help/assets/search-assets-view.md#contextual-search">
      <strong> Contextual Onderzoek </strong>
      </a>
   </div>
   <p>
      <em> leer hoe te om activa te zoeken gebruikend eenvoudige tekstherinneringen.</em>
   </p>
</td>


<td>
   <a href="/help/assets/search-assets-view.md#search-firefly">
   <img alt="Elementen genereren met Adobe Firefly" src="./assets/adobe-firefly.jpg" />
   </a>
   <div>
      <a href="/help/assets/search-assets-view.md#search-firefly">
      <strong> produceer activa gebruikend Adobe Firefly </strong>
      </a>
   </div>
   <p>
      <em> produceer activa in real time gebruikend Adobe Firefly.</em>
   </p>
</td>
<td>
   <a href="/help/assets/native-integration-adobe-express.md">
   <img alt="Integratie met Adobe Express" src="./assets/content-hub-express.jpeg" />
   </a>
   <div>
      <a href="/help/assets/native-integration-adobe-express.md">
      <strong> Integratie met Adobe Express </strong>
      </a>
   </div>
   <p>
      <em> de eigenschappen van Adobe Express AI van het Gebruik binnen het gebruikersinterface van AEM Assets.</em>
   </p>
</td>
</table>

**Slimme Beeldvorming**: Het Slimme Beeld verstrekt zelfs betere prestaties van de levering van beeldactiva door het formaat en de dossiergrootte van een beeld automatisch te optimaliseren die op browser vermogen van een klant wordt gebaseerd. Deze functie werkt met uw bestaande voorinstellingen voor afbeeldingen en maakt gebruik van intelligentie bij levering. Deze intelligentie vermindert verder de grootte van het beelddossier die op browser en de snelheid van de netwerkverbinding wordt gebaseerd.

**Slim Gewas**: Een vermogen van Adobe Sensei AI, om het brandpunt automatisch in om het even welk beeld of video te ontdekken, en het gewas te bebouwen om het te handhaven. Het vangt het voorgenomen punt van belang ongeacht het schermgrootte en elimineert daarom vervelende handtaken en levert high-quality, snel ladende beelden en video die op om het even welk apparaat of scherm goed kijkt.

**AI-Gegenereerde videotitels**: AI-Gegenereerde videotitels in Adobe Dynamische het gebruiks kunstmatige intelligentie om titels voor videoinhoud automatisch te produceren. Deze functie is ontworpen om de toegankelijkheid te verbeteren en de gebruikerservaring te verbeteren door nauwkeurige bijschriften te bieden. Bijschriften worden gegenereerd op basis van de originele audio, eventuele extra audiotracks of extra bijschriften worden weergegeven op het tabblad `Captions and Audio` op de pagina met video-eigenschappen. Met ondersteuning voor meer dan 60 talen kunt u bijschriften reviseren en een voorvertoning weergeven voordat u de video publiceert.
<table>
<td>
   <a href="/help/assets/dynamic-media/imaging-faq.md">
   <img alt="Slimme afbeeldingen" src="./assets/smart-imaging.jpg" />
   </a>
   <div>
      <a href="/help/assets/dynamic-media/imaging-faq.md">
      <strong> Slimme Beeldvorming </strong>
      </a>
   </div>
   <p>
      <em> optimaliseer het formaat en de dossiergrootte van een beeld die op browser van een gebruiker vermogen en netwerksnelheid wordt gebaseerd.</em>
   </p>
</td>


<td>
   <a href="https://experienceleague.adobe.com/en/docs/experience-manager-learn/assets/dynamic-media/video/dynamic-media-smart-crop-video">
   <img alt="Slim uitsnijden" src="./assets/smart-cropping.jpg" />
   </a>
   <div>
      <a href="https://experienceleague.adobe.com/en/docs/experience-manager-learn/assets/dynamic-media/video/dynamic-media-smart-crop-video">
      <strong> Slim Uitsnijden </strong>
      </a>
   </div>
   <p>
      <em> AI van het Gebruik om het brandpunt automatisch in om het even welk beeld of video te ontdekken, en bebouwing om het te handhaven </em>
   </p>
</td>
<td>
   <a href="/help/assets/dynamic-media/video.md">
   <img alt="Door AI gegenereerde videobijschriften" src="./assets/videos-with-captions.jpg" />
   </a>
   <div>
      <a href="/help/assets/dynamic-media/video.md">
      <strong> AI-Gegenereerde videotitels </strong>
      </a>
   </div>
   <p>
      <em> gebruik kunstmatige intelligentie om titels voor videoinhoud automatisch te produceren. </em>
   </p>
</td>
</table>

>[!TAB  Ontdekking van activa ]

## Detectie van middelen {#asset-discovery}

Nadat u uw middelen naar AEM Assets hebt geïmporteerd, is het een uitdaging om snel de juiste middelen te vinden uit zo&#39;n enorme verzameling.

AEM Assets biedt functies die u helpen snel de juiste middelen te vinden. Deze functies omvatten door AI gegenereerde codering (slimme tags), aangepaste metagegevens en verbeterde zoekmogelijkheden.

**het beheer van Meta-gegevens**: De meta-gegevens is het meest kritieke aspect terwijl het beginnen van uw reis van het activabeheer. Het beheren van meta-gegevens krijgt volledig uit de controle van de beheerders zodra de activa aan de gebruikers worden verdeeld. Effectieve metagegevens voor elementen zorgen voor een betere zoekopdracht. Dit is de uiteindelijke bestemming voor elk DAM-programma.


**Meta-gegevens Forms**: Assets as a Cloud Service verstrekt vele standaardmeta-gegevensgebieden door gebrek. Als u extra meta-gegevensbehoeften hebt, en meer meta-gegevensgebieden nodig om zaken-specifieke meta-gegevens toe te voegen. Met metagegevensformulieren kunnen bedrijven aangepaste metagegevensvelden toevoegen aan de pagina Details van een element. De bedrijfsspecifieke metagegevens verbeteren het beheer en de ontdekking van de bedrijfsmiddelen. U kunt geheel nieuwe formulieren maken of een bestaand formulier opnieuw gebruiken.

<table>
<td>
   <a href="/help/assets/metadata-assets-view.md">
   <img alt="Metagegevens in de Assets-weergave beheren" src="./assets/manage-metadata-assets-view.jpeg" />
   </a>
   <div>
      <a href="/help/assets/metadata-assets-view.md">
      <strong> beheert Meta-gegevens in de mening van Assets </strong>
      </a>
   </div>
   <p>
      <em> leer hoe te om meta-gegevens en meta-gegevensvormen te beheren gebruikend de mening van Assets.</em>
   </p>
</td>


<td>
   <a href="https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager-blogs/how-to-manage-metadata-before-and-after-migrating-to-aem-assets/ba-p/744298">
   <img alt="Best practices op het gebied van metagegevensbeheer" src="./assets/metadata-best-practices.jpeg" />
   </a>
   <div>
      <a href="https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager-blogs/how-to-manage-metadata-before-and-after-migrating-to-aem-assets/ba-p/744298">
      <strong> het beheer beste praktijken van Meta-gegevens </strong>
      </a>
   </div>
   <p>
      <em> leer hoe te om meta-gegevens vóór en na het migreren van uw activa aan AEM te beheren.</em>
   </p>
</td>
<td>
   <a href="/help/assets/manage-metadata.md">
   <img alt="Adobe Asset Link gebruiken" src="./assets/metadata-management-admin-view.jpeg" />
   </a>
   <div>
      <a href="/help/assets/manage-metadata.md">
      <strong> beheert meta-gegevens in Admin mening </strong>
      </a>
   </div>
   <p>
      <em> Leer hoe te om meta-gegevens en meta-gegevensvormen te beheren gebruikend de mening Admin.</em>
   </p>
</td>
</table>

**Slimme Markeringen**: De Slimme Markeringen gebruiken het kunstmatig intelligente kader van Adobe Sensei om zijn algoritme van de beelderkenning op uw markeringsstructuur en bedrijfstaxonomie te trainen. Deze inhoudsinfo wordt vervolgens gebruikt om relevante tags toe te passen op een andere set elementen. AEM past standaard automatisch slimme tags toe op geüploade elementen.

**activa van het Onderzoek**: Zodra u de juiste meta-gegevens op zijn plaats hebt, staat AEM Assets u toe om het gebruiken van diverse exploitanten, vervangingen, geavanceerde vragen, en douanefilters te zoeken.

**Contextafhankelijke Onderzoek**: AEM Assets verstrekt ook het Contextuele vermogen van het Onderzoek, dat u toelaat om activa beschikbaar in de bewaarplaats te zoeken door tekstherinneringen te bepalen. Experience Manager Assets transformeert automatisch de tekstvragen om filters te zoeken en geeft de zoekresultaten weer. U kunt automatische filters weergeven en wijzigen met het deelvenster Filters om de zoekresultaten verder te beperken.

<table>
<td>
   <a href="/help/assets/smart-tags.md">
   <img alt="Slimme tags in AEM Assets" src="./assets/smart-tags-ai.jpeg" />
   </a>
   <div>
      <a href="/help/assets/smart-tags.md">
      <strong> voeg Slimme Markeringen aan activa </strong> toe
      </a>
   </div>
   <p>
      <em> leer hoe te om slimme markeringen automatisch op geuploade activa toe te passen.</em>
   </p>
</td>


<td>
   <a href="/help/assets/search-assets-view.md">
   <img alt="Zoeken in Assets" src="./assets/search-assets-view-landing.jpeg" />
   </a>
   <div>
      <a href="/help/assets/search-assets-view.md">
      <strong> de activa van het Onderzoek in de mening van Assets </strong>
      </a>
   </div>
   <p>
      <em> leer hoe te om Contextual Onderzoek en andere onderzoeksmogelijkheden in de mening van Assets effectief te gebruiken.</em>
   </p>
</td>
<td>
   <a href="/help/assets/search-best-practices.md">
   <img alt="Beste werkwijzen zoeken" src="./assets/search-best-practices.jpeg" />
   </a>
   <div>
      <a href="/help/assets/search-best-practices.md">
      <strong> beste praktijken van het Onderzoek </strong>
      </a>
   </div>
   <p>
      <em> leer over diverse scenario's om de gebruikers van AEM bij te staan om basis aan geavanceerd niveauonderzoek uit te voeren.</em>
   </p>
</td>
</table>

>[!TAB  Beheer van activa ]

## Beheer en beheer van bedrijfsmiddelen {#asset-management-governance}

Nadat u uw middelen hebt geüpload naar AEM Assets en de metagegevens hebt ingesteld voor een betere ontdekkingsmogelijkheden, kunt u verschillende taken voor het beheer van digitale elementen uitvoeren met behulp van de gebruikersvriendelijke interface van de Assets-weergave.

**Taken van het Beheer van Activa**: Sommige basistaken omvatten onderzoek, download, beweging, exemplaar, anders noemen, schrappen, bijwerken, en geven verrichtingen uit.

U kunt ook elementversies onderhouden, de status van elementen instellen en de vervaldatum van elementen instellen.

**Mijn Workspace**: De mening van Assets omvat ook een klantgerichte werkruimte die widgets verstrekt. Deze widgets bieden handige toegang tot belangrijke gebieden van de Assets-gebruikersinterface en tot informatie die voor u het meest relevant is. Deze pagina dient als een one-stop oplossing om een overzicht van uw het werkpunten te verstrekken en snelle toegang tot zeer belangrijke werkschema&#39;s te geven.

**Content Credentials**: Een andere krachtige eigenschap die AEM Assets steunt is Content Credentials. Merken maken zich meer dan ooit zorgen over inhoudstransparantie, AI-openbaarmaking en het voorkomen van het knoeien met activa. De Content Authenticity Initiative (CAI) in Adobe bouwt hulpmiddelen die aan de technische norm Coalition for Content Provenance and Authenticity (C2PA) voldoen. Content Credentials, een nieuw type gecodeerde, aanvervalsbare metagegevens, kan de kijkers helpen de inhoud te begrijpen en de integriteit van merkelementen te garanderen. Ze kunnen een groot aantal herkomstgegevens bevatten die insight de geschiedenis van een digitaal middel bieden.

<table>
<td>
   <a href="/help/assets/manage-organize-assets-view.md">
   <img alt="Taken voor middelenbeheer" src="./assets/asset-management.jpeg" />
   </a>
   <div>
      <a href="/help/assets/manage-organize-assets-view.md">
      <strong> de beheerstaken van Activa </strong>
      </a>
   </div>
   <p>
      <em> leer hoe te om sommige basis evenals geavanceerde taken van het activabeheer uit te voeren.</em>
   </p>
</td>


<td>
   <a href="/help/assets/my-workspace-assets-view.md">
   <img alt="Mt Workspace" src="./assets/my-workspace.jpeg" />
   </a>
   <div>
      <a href="/help/assets/my-workspace-assets-view.md">
      <strong> Mijn Workspace </strong>
      </a>
   </div>
   <p>
      <em> Leer hoe te met Mijn Workspace te werken om tot zeer belangrijke gebieden van het gebruikersinterface van Assets snel toegang te hebben.</em>
   </p>
</td>
<td>
   <a href="/help/assets/content-credentials.md">
   <img alt="Content Credentials" src="./assets/content-credentials.jpeg" />
   </a>
   <div>
      <a href="/help/assets/content-credentials.md">
      <strong> Content Credentials </strong>
      </a>
   </div>
   <p>
      <em> de inzichten van de winst op de geschiedenis van een digitaal bezit gebruikend Content Credentials.</em>
   </p>
</td>
</table>

**Inzamelingen**: AEM Assets laat u ook toe om uw activa in inzamelingen te organiseren. Een verzameling is een set elementen, mappen of andere verzamelingen in de weergave Adobe Experience Manager Assets. Gebruik verzamelingen om elementen tussen gebruikers te delen. In tegenstelling tot mappen kan een verzameling elementen van verschillende locaties bevatten. U kunt meerdere verzamelingen delen met een gebruiker. Elke verzameling bevat verwijzingen naar elementen. De referentiële integriteit van activa wordt gehandhaafd over inzamelingen.

**Meldingen**: De de meningsberichten van Assets laten u toe om de verrichtingen te controleren die op de activa, de omslagen, of de inzamelingen worden uitgevoerd beschikbaar in de bewaarplaats. U moet de inhoud selecteren en zich erop abonneren waarvoor de meldingen naar u worden verzonden. U kunt ook de categorieën configureren waarvoor de meldingen naar u worden verzonden.

**ontdekt dubbele activa**: AEM Assets steunt ook het ontdekken van dubbele activa. Als een DAM-gebruiker een of meer middelen uploadt die al in de opslagplaats aanwezig zijn, detecteert Experience Manager de duplicatie en wordt de gebruiker hiervan op de hoogte gesteld.



<table>
<td>
   <a href="/help/assets/manage-collections-assets-view.md">
   <img alt="Verzamelingen beheren" src="./assets/manage-collections.jpeg" />
   </a>
   <div>
      <a href="/help/assets/manage-collections-assets-view.md">
      <strong> beheert Inzamelingen </strong>
      </a>
   </div>
   <p>
      <em> Leer hoe te om uw activa in inzamelingen te organiseren voor efficiënt het delen van activa.</em>
   </p>
</td>


<td>
   <a href="/help/assets/manage-notifications-assets-view.md">
   <img alt="Meldingen instellen" src="./assets/manage-notifications.jpeg" />
   </a>
   <div>
      <a href="/help/assets/manage-notifications-assets-view.md">
      <strong> Vastgestelde Meldingen </strong>
      </a>
   </div>
   <p>
      <em> Leer hoe te om berichten te plaatsen om de verrichtingen te controleren die op activa, omslagen, of inzamelingen worden uitgevoerd.</em>
   </p>
</td>
<td>
   <a href="/help/assets/detect-duplicate-assets.md">
   <img alt="Gedupliceerde elementen detecteren" src="./assets/duplicate-assets.jpeg" />
   </a>
   <div>
      <a href="/help/assets/detect-duplicate-assets.md">
      <strong> ontdekt dubbele activa </strong>
      </a>
   </div>
   <p>
      <em> ontdekt dubbele activa die aan AEM Assets worden geupload en aan gebruikers op de hoogte brengen.</em>
   </p>
</td>
</table>

>[!TAB  Integraties ]

## Integratie met Adobe- en niet-Adobe-toepassingen {#integration-adobe-non-adode-apps}

AEM Assets kan naadloos worden geïntegreerd met verschillende Adobe- en niet-Adobe-toepassingen. Hieronder volgt een overzicht van de beschikbare integraties:

+++**Integratie met Adobe en niet-Adobe toepassingen**

* **Dynamische Media met mogelijkheden OpenAPI**: [&#x200B; Dynamische Media met mogelijkheden OpenAPI &#x200B;](/help/assets/dynamic-media-open-apis-overview.md) biedt een uitvoerige reeks [&#x200B; onderzoek &#x200B;](/help/assets/search-assets-api.md) en [&#x200B; levering &#x200B;](/help/assets/deliver-assets-apis.md) APIs aan. Hierdoor kunnen uw ontwikkelaars de levering van middelen eenvoudig integreren met hun toepassingen. De toepassingen zijn onder andere Adobe en toepassingen van derden. Het verstrekt een Micro Frontend activa selecteerde gebruikersinterface om goedgekeurde activa te zoeken en te selecteren. De kiezer kan moeiteloos worden geïntegreerd met elke toepassing die is gebaseerd op JavaScript-frameworks zoals React JS, Angular JS en Vanilla JS.

* **Micro-Frontend de Selector van Activa**: Micro-Frontend de Selecteur van Activa verstrekt een gebruikersinterface die met de bewaarplaats van Experience Manager Assets integreert zodat u kunt doorbladeren of digitale activa zoeken beschikbaar in de bewaarplaats. Vervolgens kunt u deze gebruiken in de ontwerpervaring van de toepassing.
U kunt Asset Selector integreren met een Adobe- of een niet-Adobe-toepassing.

<table>
<td>
   <a href="/help/assets/dynamic-media-open-apis-overview.md">
   <img alt="Overzicht van dynamische media met OpenAPI-mogelijkheden" src="./assets/dm-openapi-uses.jpeg" />
   </a>
   <div>
      <a href="/help/assets/dynamic-media-open-apis-overview.md">
      <strong> Dynamische Media met OpenAPI mogelijkheden overzicht </strong>
      </a>
   </div>
   <p>
      <em> leer zeer belangrijke voordelen en hoe te om het toegelaten te krijgen. </em>
   </p>
</td>


<td>
   <a href="/help/assets/restrict-assets-delivery.md">
   <img alt="Toegang tot middelen in Experience Manager beperken" src="./assets/restrict-assets.jpeg" />
   </a>
   <div>
      <a href="/help/assets/restrict-assets-delivery.md">
      <strong> Beperk toegang tot activa in Experience Manager </strong>
      </a>
   </div>
   <p>
      <em> Configureer rollen om toegang tot goedgekeurde elementen te beperken. </em>
   </p>
</td>
<td>
   <a href="/help/assets/overview-asset-selector.md">
   <img alt="Asset Selector" src="./assets/integration-asset-selector.jpeg" />
   </a>
   <div>
      <a href="/help/assets/overview-asset-selector.md">
      <strong> Micro-Frontend de selecteur van Activa </strong>
      </a>
   </div>
   <p>
      <em> Leer hoe te om de Selector van Activa van Micro-Front met een Adobe of een toepassing te integreren niet-Adobe.</em>
   </p>
</td>
</table>

+++

+++**Inheemse integratie met de toepassingen van Adobe**

* **Integratie met Adobe Workfront**: [!DNL Adobe Workfront] is een het werkbeheertoepassing die u helpt de volledige levenscyclus van het werk in één plaats beheren. Dankzij de integratie tussen [!DNL Workfront] en [!DNL Adobe Experience Manager Assets] kunnen organisaties de snelheid en tijd-aan-markt van inhoud verbeteren door het werk en het beheer van digitale elementen intrinsiek met elkaar te verbinden. In het kader van het beheer van hun werk in Workfront hebben gebruikers toegang tot de vereiste documenten en afbeeldingen.

  Adobe biedt aan [&#x200B;  [!DNL Workfront]  te integreren en  [!DNL Adobe Experience Manager Assets]  &#x200B;](https://experienceleague.adobe.com/en/docs/workfront/using/documents/wf-aem-integrations/wf-aem-essentials/aem-asset-integrations).

* **Integratie met Cijfer**: AEM Assets integreert binnen met Cijfer, dat ontwerpers toestaat om tot de activa toegang te hebben die direct in AEM Assets van binnen het Gebruikersinterface van Figma worden opgeslagen. U kunt inhoud die in AEM Assets wordt beheerd, op het Figma-canvas plaatsen en vervolgens nieuwe of bewerkte inhoud in de AEM Assets-opslagplaats opslaan. Om tot de Schakelaar van AEM Assets toegang te hebben beschikbaar op de Communautaire pagina van Figma, klik [&#x200B; hier &#x200B;](https://www.figma.com/community/plugin/1512561378275712210/adobe-experience-manager-aem-assets-connector).

* **Inheemse integratie met Adobe Express**: AEM Assets integreert binnen met Adobe Express, die u toestaat om tot de activa toegang te hebben die direct in AEM Assets van binnen het gebruikersinterface van Adobe Express worden opgeslagen. U kunt inhoud die in AEM Assets wordt beheerd, op het Express-canvas plaatsen en vervolgens nieuwe of bewerkte inhoud opslaan in een AEM Assets-opslagplaats.

* **verbind AEM Assets met Creative Cloud**: Experience Manager Assets kan met een recht van Creative Cloud verbinden provisioned in een verschillende organisatie IMS. Met deze functie kunt u de nieuwste Creative Cloud-integraties in AEM Assets gebruiken, waaronder Express en Creative Cloud Libraries. Als uw Creative Cloud-producten en AEM Assets zijn ingericht voor aparte IMS-organisaties, kunt u verbinding maken met een andere Creative Cloud-organisatie om geïntegreerde workflows tussen de twee oplossingen uit te voeren.

<table>
<td>
   <a href="/help/assets/workfront-integrations.md">
   <img alt="Integratie met Adobe Workfront" src="./assets/integration-adobe-workfront.jpeg" />
   </a>
   <div>
      <a href="/help/assets/workfront-integrations.md">
      <strong> Integratie met Adobe Workfront </strong>
      </a>
   </div>
   <p>
      <em> integreer met Adobe Workfront om de volledige het werklevenscyclus bij één plaats te beheren.</em>
   </p>
</td>
<td>
   <a href="/help/assets/manage-collections-assets-view.md">
   <img alt="Integratie met Figma" src="./assets/integration-commerce.jpeg" />
   </a>
   <div>
      <a href="/help/assets/manage-collections-assets-view.md">
      <strong> Integratie met Cijfer </strong>
      </a>
   </div>
   <p>
      <em> heb toegang tot de activa die in AEM Assets van binnen het Gebruikersinterface van Figma worden opgeslagen </em>
   </p>
</td>
<td>
   <a href="/help/assets/native-integration-adobe-express.md">
   <img alt="Native integratie met Adobe Express" src="./assets/integration-adobe-express.jpeg" />
   </a>
   <div>
      <a href="/help/assets/native-integration-adobe-express.md">
      <strong> Inheemse integratie met Adobe Express </strong>
      </a>
   </div>
   <p>
      <em> Plaats activa beschikbaar binnen AEM Assets op het Uitdrukkelijke canvas en bewaar bijgewerkte activa aan AEM. </em>
   </p>
</td>


</table>


* **Integratie met Adobe Journey Optimizer**: Breng marketing en creatieve werkschema&#39;s samen gebruikend Adobe Experience Manager Assets. Native geïntegreerd met Adobe Journey Optimizer, toegang tot Assets as a Cloud Service voor het opslaan, beheren, ontdekken en distribueren van digitale middelen. Het biedt één gecentraliseerde opslagplaats van middelen die u kunt gebruiken om uw berichten te vullen.

* **Integratie met Commerce**: De Integratie van Adobe Experience Manager (AEM) Assets voor Commerce combineert de robuuste mogelijkheden van AEM als systeem van het Beheer van Digitale Activa (DAM) met Adobe Commerce om eCommerce ervaringen te verbeteren. Deze mogelijkheden worden geleverd door Commerce-projecten aan te sluiten op een krachtige omgeving voor middelenbeheer van AEM, zodat u over een naadloze, schaalbare en efficiënte manier beschikt om bedrijfsmiddelen te beheren en te leveren in verschillende winkelomgevingen.
* **Integrating AEM Assets met op document-Gebaseerde Authoring stromen voor Edge Delivery Services**: Wanneer [!DNL AEM Assets] met uw op document-Gebaseerde Authoring hulpmiddelen, zoals [!DNL Microsoft Word] of [!DNL Google Docs] integreert, verstrekt het een Selecteur van Activa in uw auteursgereedschap. Gebruik deze Asset Selector om [!DNL AEM Assets] te openen en de goedgekeurde elementen in uw inhoud in te voegen.
Als u reeds een [!DNL Edge Delivery Services] website hebt, zie [[!DNL AEM Assets]  insteekmodule &#x200B;](https://github.com/adobe-rnd/aem-assets-plugin/blob/main/README.md) documentatie leren hoe te om [!DNL AEM Assets] met uw bestaand [!DNL AEM] project te integreren.

* **Integreer [!DNL AEM Assets] met [!DNL Universal Editor] gebaseerde ontwerpstromen voor[!DNL Edge Delivery Services]**: opstelling [!DNL Universal Editor] om met [!DNL AEM Assets] te integreren. Dankzij deze integratie kunt u [!DNL Dynamic Media with OpenAPI capabilities] gebruiken om elementen te leveren.

   * Zie [&#x200B; Configuratie in  [!DNL Edge Delivery]  Plaats &#x200B;](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/#configuration-in-edge-delivery-site) leren hoe te om een functie van de plukker van douaneactiva in [!DNL Universal Editor] toe te voegen. Met de aangepaste elementkiezer kunt u elementen rechtstreeks in uw [!DNL Universal Editor] -inhoud invoegen.
   * Zie het [&#x200B; overzicht van de Uitbreiding &#x200B;](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/#extension-overview) leren hoe te om tot [!DNL AEM Assets] toegang te hebben en de activa op te nemen terwijl het ontwerpen in [!DNL Universal Editor].

<table>
<td>
   <a href="https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/combine/assets">
   <img alt="Integratie met Adobe Journey Optimizer" src="./assets/integration-figma.jpeg" />
   </a>
   <div>
      <a href="https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/combine/assets">
      <strong> Integratie met Adobe Journey Optimizer </strong>
      </a>
   </div>
   <p>
      <em> breng marketing en creatieve werkschema's samen gebruikend integratie met AJO </em>
   </p>
</td>
<td>
   <a href="https://experienceleague.adobe.com/en/docs/commerce/aem-assets-integration/overview">
   <img alt="Integratie met Commerce" src="./assets/integration-ajo.jpeg" />
   </a>
   <div>
      <a href="https://experienceleague.adobe.com/en/docs/commerce/aem-assets-integration/overview">
      <strong> Integratie met Commerce </strong>
      </a>
   </div>
   <p>
      <em> integreer AEM Assets met Commerce om eCommerce ervaringen te verbeteren.</em>
   </p>
</td>
<td>
   <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md">
   <img alt="AEM Assets integreren met EDS" src="./assets/integrate-ue-assets.jpeg" />
   </a>
   <div>
      <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md">
      <strong> integreer AEM Assets met EDS </strong>
      </a>
   </div>
   <p>
      <em> integreer AEM Assets met op document-gebaseerde en Universele Redacteur gebaseerde auteursstromen.</em>
   </p>
</td>
</table>

+++

>[!TAB  Activatie van Activa ]

## Activering van element {#asset-activation}

Ontgrendel het volledige potentieel van uw digitale middelen met AEM Assets via Content Hub naar Dynamic Media — inclusief krachtige OpenAPI-mogelijkheden. AEM Assets biedt een uitgebreide reeks oplossingen die zijn ontworpen om de transformatie van bedrijfsmiddelen te stroomlijnen en de levering via verschillende kanalen te optimaliseren.

+++**Content Hub**

Content Hub is beschikbaar als onderdeel van Experience Manager Assets as a Cloud Service voor het democratiseren van de toegang tot online-inhoud voor organisaties en hun zakelijke partners. Het richt zich op het distribueren van middelen voor activering op schaal en het creëren van varianten van on-brand-inhoud met het oog op verbeterde marketingflexibiliteit.

Content Hub biedt de volgende belangrijke voordelen:

* **vind en deel alle merk goedgekeurde activa beschikbaar in een intuïtief portaal**: AEM Assets dient als één enkele bron van waarheid en alle goedgekeurde activa zijn automatisch beschikbaar op Content Hub in een vlakke hiërarchie om de onderzoekservaring te verbeteren.

* **Configureerbare Gebruikersinterface**: De gemeenschappelijkste eigenschappen binnen Content Hub, zoals filters voor onderzoek, beschikbare gebieden terwijl het toevoegen van of het invoeren van activa, activa eigenschappen, bannerinhoud voor branding zijn configureerbaar en een beheerder kan het gebruikersinterface van Content Hub gemakkelijk vormen die op hun vereisten wordt gebaseerd.

* **machtigt niet-creatieven om inhoud uit te geven en opnieuw te mengen terwijl het blijven op merk**: Content Hub staat u toe om nieuwe inhoud met Adobe Express (als u Adobe Express rechten hebt) tot stand te brengen. U kunt bestaande inhoud bewerken met gebruiksvriendelijke gereedschappen, onmerkvariaties maken met sjablonen en merkelementen en nieuwe inhoud maken met de nieuwste GenAI-mogelijkheden van Adobe Firefly.

* **de inzichten van de Versterking op hoe de inhoud over teams** wordt gebruikt: [!DNL Content Hub] verstrekt waardevolle inzichten in activa, richtend een gemeenschappelijke uitdaging die de marketing belanghebbenden vaak ontmoeten - de statistieken van het activagebruik die in marketing campagnes, kanalen, en verschillende gebieden worden gebruikt. Door een duidelijk inzicht te krijgen in de prestaties en populariteit van de middelen, biedt het actioneerbare inzichten die essentieel zijn voor het verbeteren van de gebruikerservaring.

<table>
<td>
   <a href="/help/assets/product-overview.md">
   <img alt="Content Hub - Overzicht" src="./assets/content-hub-overview.jpeg" />
   </a>
   <div>
      <a href="/help/assets/product-overview.md">
      <strong> Overzicht van Content Hub </strong>
      </a>
   </div>
   <p>
      <em> Leer meer over Content Hub, zijn belangrijkste voordelen, en hoe te om tot het toegang te hebben. </em>
   </p>
</td>


<td>
   <a href="/help/assets/configure-content-hub-ui-options.md">
   <img alt="Content Hub-gebruikersinterface configureren" src="./assets/content-hub-configuration.jpeg" />
   </a>
   <div>
      <a href="/help/assets/configure-content-hub-ui-options.md">
      <strong> vorm Content Hub Gebruikersinterface </strong>
      </a>
   </div>
   <p>
      <em> Leer hoe te om opties te vormen beschikbaar op het gebruikersinterface van Content Hub.</em>
   </p>
</td>
<td>
   <a href="/help/assets/edit-images-content-hub.md">
   <img alt="Bewerken met Adobe Express" src="./assets/content-hub-express.jpeg" />
   </a>
   <div>
      <a href="/help/assets/edit-images-content-hub.md">
      <strong> geef uit gebruikend Adobe Express </strong>
      </a>
   </div>
   <p>
      <em> leer hoe te om beelden in Content Hub uit te geven gebruikend Adobe Express.</em>
   </p>
</td>
</table>

+++

+++**Dynamische Media**

Met Dynamic Media kunt u op aanvraag rijke visuele merchandising- en marketingmiddelen leveren. Het helpt u ook om interactieve het bekijken ervaringen, met inbegrip van gezoem, 360 graadspin, en video tot stand te brengen en te dienen. Uw elementen worden dynamisch geschaald voor gebruik op internet-, mobiele en sociale sites. Het gebruiken van een reeks primaire bronactiva - zoals beelden, video, en 3D - Dynamische Media produceert en levert veelvoudige variaties van deze rijke inhoud, in echt - tijd door zijn globale, scalable, prestaties-geoptimaliseerde CDN (het Netwerk van de Levering van de Inhoud).

Dynamische media biedt de volgende sleutelfuncties:

* **Slimme Beeldvorming**: Het Slimme Beeld verstrekt zelfs betere prestaties van de levering van beeldactiva door het formaat en de dossiergrootte van een beeld automatisch te optimaliseren die op browser vermogen van een klant wordt gebaseerd. Deze functie werkt met uw bestaande voorinstellingen voor afbeeldingen en maakt gebruik van intelligentie bij levering. Deze intelligentie vermindert verder de grootte van het beelddossier die op browser en de snelheid van de netwerkverbinding wordt gebaseerd.

* **Aangepaste videoreeksen**: Een Aangepaste Video Reeks groepsversies van de zelfde video die bij verschillende beetjetarieven en formaten worden gecodeerd. U begint met uw originele, primaire video, die u in het systeem uploadt. Met dynamische media wordt die video automatisch in meerdere video&#39;s getranscodeerd. Op het moment van levering bepaalt het op intelligente wijze welk videoscherm, welke kwaliteit en welke indeling moet worden gebruikt en levert het aan de telefoon, tablet of desktopcomputer.

* **Slim Gewas**: Een vermogen van Adobe Sensei AI, om het brandpunt in om het even welk beeld of video automatisch te ontdekken, en het gewas te bebouwen om het te handhaven. Het vangt het voorgenomen punt van belang ongeacht het schermgrootte en elimineert daarom vervelende handtaken en levert high-quality, snel ladende beelden en video die op om het even welk apparaat of scherm goed kijkt.

* **Dynamische malplaatjes van Media**: Creeer in real time aanpasbare malplaatjes voor uw banners en vliegers gebruikend de Dynamische malplaatjes van Media, een malplaatjeredacteur van WYSIWYG. Publiceer uw sjabloon Dynamische media en gebruik deze in downstreamtoepassingen. Een sjabloon voor dynamische media bevat afbeeldings- en tekstlagen. Voeg parameters toe aan de afbeeldings- en tekstlagen van de sjabloon en gebruik Dynamische media-URL&#39;s om de laag te verplaatsen, de grootte ervan te wijzigen en de inhoud in real-time bij te werken.

* **Multi-audio en titel**: Voeg veelvoudige titels en veelvoudige audiosporen aan een primaire video toe. Dit betekent dat uw video&#39;s toegankelijk zijn voor een wereldwijd publiek. U kunt één gepubliceerde primaire video aanpassen aan een wereldwijd publiek in meerdere talen en de richtlijnen voor toegankelijkheid voor verschillende geografische regio&#39;s naleven. Auteurs kunnen de bijschriften en audiotracks ook beheren vanaf één tabblad in de gebruikersinterface.

* **Dynamische Aanpassings het Streamen over (DASH) steun van HTTP**: De dynamische Media steunt Aangepast het stromen in Dynamische Media videeverstrekking (met toegelaten CMAF), die een betere gebruiker het bekijken ervaring voor video&#39;s verzekert. DASH is het internationale standaardprotocol voor adaptieve videostreaming en wordt op grote schaal toegepast in de branche.

* **AI-Gegenereerde videotitels**: AI-Gegenereerde videotitels in Adobe Dynamische het gebruiks kunstmatige intelligentie om titels voor videoinhoud automatisch te produceren. Met ondersteuning voor meer dan 60 talen kunt u bijschriften reviseren en een voorvertoning weergeven voordat u de video publiceert.

Voor informatie over beschikbaar Dynamisch dienstenaanbod van Media, zie [&#x200B; Dynamische Media Prime en Ultimate &#x200B;](/help/assets/dynamic-media/dm-prime-ultimate.md).



<table>
<td>
   <a href="/help/assets/dynamic-media/dynamic-media.md">
   <img alt="Werken met dynamische media" src="./assets/work-with-dynamic-media.jpeg" />
   </a>
   <div>
      <a href="/help/assets/dynamic-media/dynamic-media.md">
      <strong> Werk met Dynamische Media </strong>
      </a>
   </div>
   <p>
      <em> Leer hoe te om activa voor consumptie op Web, mobiele, en sociale plaatsen te leveren. </em>
   </p>
</td>


<td>
   <a href="/help/assets/dynamic-media/dm-journey-part1.md">
   <img alt="Dynamische mediareis" src="./assets/dm-journey.jpeg" />
   </a>
   <div>
      <a href="/help/assets/dynamic-media/dm-journey-part1.md">
      <strong> Dynamische Reis van Media </strong>
      </a>
   </div>
   <p>
      <em> leer hoe de Dynamische Media waarde aan uw werk brengt.</em>
   </p>
</td>
<td>
   <a href="/help/assets/dynamic-media/dm-best-practices.md">
   <img alt="AEM Assets verbinden met Creative Cloud" src="./assets/dm-best-practices.jpeg" />
   </a>
   <div>
      <a href="/help/assets/dynamic-media/dm-best-practices.md">
      <strong> Dynamische beste praktijken van Media </strong>
      </a>
   </div>
   <p>
      <em> Beste praktijken terwijl het werken met beelden, video's, en kijkers.</em>
   </p>
</td>
</table>

+++

+++**Dynamische Media met mogelijkheden OpenAPI**

In de snelle digitale wereld van vandaag, is het ontsluiten van het volledige potentieel van de digitale activa van uw merk cruciaal om voor de concurrentie te blijven. Een holistische DAM-oplossing (Digital Assets Management) vereenvoudigt het beheer van bedrijfsmiddelen, bevordert de consistentie van merken en versnelt de levering van inhoud, waarbij de integriteit van merken en uitzonderlijke ervaringen met klanten worden gegarandeerd.

Dynamische media met OpenAPI-mogelijkheden zetten DAM centraal in een flexibel en efficiënt content-ecosysteem van supply chain om beheer en levering van middelen te garanderen.

Dynamische media met OpenAPI-mogelijkheden bieden de volgende belangrijke voordelen:

* **Naadloze integraties**: De dynamische Media met mogelijkheden OpenAPI biedt een uitvoerige reeks onderzoek en levering APIs aan. Het staat uw ontwikkelaars toe om de levering van activa met hun toepassingen [&#x200B; gemakkelijk &#x200B;](/help/assets/integrate-dynamic-media-open-apis.md) te integreren. De toepassingen zijn onder andere Adobe en toepassingen van derden. Het verstrekt a [&#x200B; Micro Frontend activa selecteerde gebruikersinterface &#x200B;](/help/assets/overview-asset-selector.md) om goedgekeurde activa te zoeken en te selecteren. De kiezer kan moeiteloos worden geïntegreerd met elke toepassing die is gebaseerd op JavaScript-frameworks zoals React JS, Angular JS en Vanilla JS.

* **Gecentraliseerd beheer van digitale activa**: DAM is de enige bron van waarheid voor alle digitale activa. Uw digitale middelen worden centraal beheerd in AEM Assets en worden aan verbruikende toepassingen geleverd door verwijzing gebruikend levering URLs, zonder activa te kopiëren binaries.

* **updates in real time**: Om het even welke veranderingen die in goedgekeurde activa in DAM, met inbegrip van versieupdates en meta-gegevenswijzigingen worden aangebracht, worden automatisch weerspiegeld in levering URLs. Met een korte tijd-aan-Levende (TTL) waarde van 10 minuten die voor Dynamische Media met mogelijkheden OpenAPI via CDN wordt gevormd, worden de updates zichtbaar over alle creatie en gepubliceerde interfaces binnen 10 minuten.

* **de consistentie van het Merk**: Slechts [&#x200B; merk-goedgekeurde activa &#x200B;](/help/assets/approve-assets.md) worden blootgesteld aan stroomafwaartse toepassingen. [&#x200B; de Managers en de Marketers van de Merk handhaven strikte controle over merkactiva &#x200B;](/help/assets/restrict-assets-delivery.md). Alleen de goedgekeurde en laatste versie van het middel is beschikbaar voor gebruik, zodat alle kanalen en toepassingen consistent blijven.

* **Web-geoptimaliseerde levering**: De digitale activa worden geleverd in Web-geoptimaliseerde formaten om de Velen van het Web van de Kern van uw digitale ervaringen te verbeteren. Deze optimalisatie omvat ondersteuning voor WebP-uitvoeringen voor afbeeldingen, adaptieve streaming via HLS- of DASH-protocollen voor video&#39;s en originele uitvoeringen voor documenten.

* **Dynamische activa transformatie**: Het systeem staat voor de transformatie van het beeld toe het gebruiken van parameters URL die als beeldbepalingen worden bekend. [&#x200B; bijvoorbeeld, breedte, hoogte, roteert, keert, kwaliteit, gewas, formaat, en slimme gewas &#x200B;](/help/assets/deliver-assets-apis.md) om. Transformeerde uitvoeringen worden dynamisch gegenereerd en naadloos via de CDN geleverd.

* **Veilige levering van activa**: De dynamische Media met mogelijkheden OpenAPI verstrekt een mechanisme voor controle over toegang tot uw digitale activa. U kunt gebruikersrollen of groepen als meta-gegevens voor te beveiligen activa specificeren en een vooraf bepaald tijdskader plaatsen waarin [&#x200B; slechts geautoriseerde gebruikers tot deze activa &#x200B;](/help/assets/restrict-assets-delivery.md) kunnen toegang hebben. De leverings-URL&#39;s voor beveiligde elementen worden tijdens de beperkte periode niet opgelost voor onbevoegde gebruikers.

Voor informatie over beschikbaar Dynamisch dienstenaanbod van Media, zie [&#x200B; Dynamische Media Prime en Ultimate &#x200B;](/help/assets/dynamic-media/dm-prime-ultimate.md).

<table>
<td>
   <a href="/help/assets/dynamic-media-open-apis-overview.md">
   <img alt="Overzicht van dynamische media met OpenAPI-mogelijkheden" src="./assets/dm-openapi-uses.jpeg" />
   </a>
   <div>
      <a href="/help/assets/dynamic-media-open-apis-overview.md">
      <strong> Dynamische Media met OpenAPI mogelijkheden overzicht </strong>
      </a>
   </div>
   <p>
      <em> leer zeer belangrijke voordelen en hoe te om het toegelaten te krijgen. </em>
   </p>
</td>


<td>
   <a href="/help/assets/restrict-assets-delivery.md">
   <img alt="Toegang tot middelen in Experience Manager beperken" src="./assets/restrict-assets.jpeg" />
   </a>
   <div>
      <a href="/help/assets/restrict-assets-delivery.md">
      <strong> Beperk toegang tot activa in Experience Manager </strong>
      </a>
   </div>
   <p>
      <em> Configureer rollen om toegang tot goedgekeurde elementen te beperken. </em>
   </p>
</td>
<td>
   <a href="/help/assets/integrate-remote-approved-assets-with-sites.md">
   <img alt="AEM Assets op afstand integreren met AEM Sites" src="./assets/integration-aem-sites.jpeg" />
   </a>
   <div>
      <a href="/help/assets/integrate-remote-approved-assets-with-sites.md">
      <strong> integreer verre AEM Assets met AEM Sites </strong>
      </a>
   </div>
   <p>
      <em> integreer verre AEM Assets met het milieu van AEM Sites. </em>
   </p>
</td>
</table>

+++

>[!TAB  Inzichten ]

## Asset Insights {#asset-insights}

Asset Reporting geeft beheerders inzicht in de activiteiten van de Adobe Experience Manager Assets View-omgeving. Deze gegevens bevatten nuttige informatie over de manier waarop gebruikers met inhoud en het product werken. Alle gebruikers hebben toegang tot het dashboard van Inzichten en de gebruikers die aan het het productprofiel van de Beheerder worden toegewezen kunnen user-defined rapporten tot stand brengen.

U kunt verschillende typen rapporten genereren, zoals Uploaden, downloaden en Dynamische levering van media.

* **Inzichten in de mening van Assets**: De mening van Assets laat u toe om gegevens in real time voor uw het meningsmilieu van Assets met het dashboard van Inzichten te bekijken. U kunt real-time gebeurtenismetriek tijdens de laatste 30 dagen of voor de laatste 12 maanden bekijken. Tot de gebeurtenissen behoren Downloads, Uploads, Opslaggebruik, Hoogste Zoekopdrachten, Aantal bedrijfsmiddelen op grootte en Aantal bedrijfsmiddelen op type element.

* **de integratie van Adobe Analytics in Admin mening**: De functionaliteit van de Inzichten van Assets laat u gebruikersratings en gebruiksstatistieken van beelden volgen die in derdewebsites, marketing campagnes, en Adobe creatieve oplossingen worden gebruikt. Met deze functie krijgt u inzicht in de prestaties en populariteit van de afbeeldingen. Met Assets Insights worden details van gebruikersactiviteit vastgelegd, zoals het aantal malen dat een afbeelding wordt beoordeeld, geklikt en afbeeldingen worden afgedrukt (het aantal keer dat een afbeelding op de website wordt geladen). Er worden scores toegewezen aan afbeeldingen op basis van deze statistieken. U kunt de scores en de prestatiesstatistieken gebruiken om populaire beelden voor opneming in catalogi, marketing campagnes, etc. te selecteren. U kunt zelfs archiverings en vergunningsvernieuwing beleid formuleren dat op deze statistieken wordt gebaseerd. Om Assets Insights gebruiksstatistieken voor activa te laten weergeven, configureert u eerst de functie voor het ophalen van rapportgegevens uit Adobe Analytics.

* **de Inzichten van Content Hub**: Content Hub verstrekt waardevolle inzichten in activa, richtend een gemeenschappelijke uitdaging die de marketing belanghebbenden vaak - de statistieken van het activagebruik ontmoeten die in marketing campagnes, kanalen, en verschillende gebieden worden gebruikt. Door een duidelijk inzicht te krijgen in de prestaties en populariteit van de middelen, biedt het actioneerbare inzichten die essentieel zijn voor het verbeteren van de gebruikerservaring.

<table>
<td>
   <a href="/help/assets/manage-reports-assets-view.md">
   <img alt="Rapporten beheren in de weergave Assets" src="./assets/assets-insights-assets-view.jpeg" />
   </a>
   <div>
      <a href="/help/assets/manage-reports-assets-view.md">
      <strong> beheert rapporten in de mening van Assets </strong>
      </a>
   </div>
   <p>
      <em> leidt inzichten op zeer belangrijke succesmetriek gebruikend de mening van Assets af. </em>
   </p>
</td>


<td>
   <a href="/help/assets/asset-reports.md">
   <img alt="Rapporten beheren in de beheerweergave" src="./assets/assets-insights-admin-view.jpeg" />
   </a>
   <div>
      <a href="/help/assets/asset-reports.md">
      <strong> beheert rapporten in Admin mening </strong>
      </a>
   </div>
   <p>
      <em> Leer hoe te om Adobe Analytics geïntegreerde rapporten in de mening te beheren Admin.</em>
   </p>
</td>
<td>
   <a href="/help/assets/insights-content-hub.md">
   <img alt="Assets-inzichten in Content Hub" src="./assets/asset-insights-content-hub.jpeg" />
   </a>
   <div>
      <a href="/help/assets/insights-content-hub.md">
      <strong> de inzichten van Assets in Content Hub </strong>
      </a>
   </div>
   <p>
      <em> leer hoe te om activa inzichten in Content Hub te bekijken.</em>
   </p>
</td>
</table>

>[!ENDTABS]

## Beschikbare persoonlijke ervaringen voor Digital Asset Management {#persona-based-experiences}

Adobe biedt robuuste DAM-oplossingen (Digital Asset Management) waarmee u optimaal kunt profiteren van uw digitale middelen. Adobe Experience Manager Assets heeft twee aparte ervaringen die dezelfde Cloud Services-opslagplaats gebruiken:

* **Admin Mening**: Het bestaande Assets as a Cloud Service gebruikersinterface. Gebruik de Admin-weergave voor alle geavanceerde mogelijkheden voor beheer van digitale middelen, zoals integratie, workflows, automatisering van inhoud, publicatie en meer.

* **de Mening van Assets**: Adobe de lichte ervaring van het activabeheer om, digitale activa op te slaan te beheren, te ontdekken en te gebruiken. Gestroomlijnde gebruikersinterface met essentiële mogelijkheden voor beheer van digitale bedrijfsmiddelen. Ontworpen voor de lichtgewicht DAM-gebruikers met focus op uploaden, metagegevensbeheer, zoeken, downloaden en delen.

![&#x200B; toe:voegen-markeringen &#x200B;](assets/newui-overview.svg)

Gebruikers met toegang tot de beheerweergave hebben ook toegang tot de Assets-weergave. Assets View biedt een vereenvoudigde gebruikersinterface waarmee u uw digitale middelen eenvoudig kunt beheren, ontdekken en distribueren. Een brede reeks gebruikers van verschillende functies, waaronder creatieve, marketing- en brancheteams, kan samenwerken aan middelen en toegang krijgen tot de juiste, goedgekeurde middelen wanneer en waar ze deze nodig hebben. Veel gebruikers van DAM geven de voorkeur aan de Assets-weergave omdat deze alleen een subset functies bevat. De ervaring is gericht op creatieve personen, alleen-lezen klanten en minder belangrijke DAM-gebruikers.

DAM-bibliotheken, ontwikkelaars en supergebruikers kunnen de Admin-weergave blijven gebruiken of, indien nodig, schakelen tussen de gebruikersinterfaces. U kunt de ervaring selecteren die het beste voor uw rol werkt.

Voor informatie over hoe te om tot de mening van Assets en sommige vereenvoudigingen toegang te hebben die het over de mening Admin aanbiedt, zie [&#x200B; Inleiding aan de mening van Assets &#x200B;](/help/assets/assets-view-introduction.md).

## AI Assistant in AEM

Voor klanten die [&#x200B; voltooide noodzakelijke criteria &#x200B;](/help/implementing/cloud-manager/ai-assistant-in-aem.md#get-access) hebben, is de Medewerker AI in AEM beschikbaar aan gebruikers van hun organisatie. Zie [&#x200B; Medewerker AI in AEM &#x200B;](/help/implementing/cloud-manager/ai-assistant-in-aem.md).
