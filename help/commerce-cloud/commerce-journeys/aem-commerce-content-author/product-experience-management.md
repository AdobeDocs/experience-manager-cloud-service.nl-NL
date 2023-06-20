---
title: Ervaringen maken met producten
description: Leer hoe u productervaringen kunt opbouwen.
exl-id: 4ae70e40-fdf1-4a37-b4dd-0c4882d77908
source-git-commit: f7525b6b37e486a53791c2331dc6000e5248f8af
workflow-type: tm+mt
source-wordcount: '1154'
ht-degree: 0%

---

# Ervaringen maken met producten {#building-experiences}

Leer hoe u productervaringen kunt beheren.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de reis AEM Inhoud en Handel: [Ervaringen met gefaseerde productcatalogi beheren](staged-catalog.md)hebt u geleerd hoe u ervaringen met gefaseerde productcatalogi kunt beheren.

## Doelstelling {#objective}

Dit document helpt u te begrijpen hoe u productinhoud en ervaringen kunt opbouwen.

## Beheer van productervaring {#management}

Het Beheer van de Ervaring van het product is de discipline om productgegevens (die door een PIM of handelsoplossing wordt bezeten) met marketing inhoud in AEM te versieren. Deze verrijkte productgegevens met inhoud kunnen vervolgens op verschillende manieren worden gebruikt om een indrukwekkende boodschappenervaring te creëren.

In AEM kunt u verschillende typen inhoud maken en deze koppelen aan de productcatalogus. De bijbehorende inhoud kan gemakkelijk worden ontdekt en worden gebruikt die tot een hoge productiviteit leidt.

### Assets {#assets}

Op een hoog niveau zijn er twee soorten activa verbonden aan producten: product &amp; marketing. De activa van het product worden gewoonlijk beheerd door handelaren en concentreren zich op het tonen van het product (hoofdzakelijk voor een neutrale achtergrond). De activa worden of beheerd in de handelsoplossing of in AEM Assets (met een integratie van Activa aan de handel/pim oplossing).

Marketingmiddelen houden verband met het promoten en gebruiken van het product dat gewoonlijk eigendom is van marketing. De voorbeelden tonen veelvoudige producten (&quot;shop de blik&quot;), in een specifieke context (&quot;buitenvalinzameling&quot;), of hoe te pdfs. CIF biedt een eenvoudige manier om elk AEM element te koppelen aan een productcatalogusobject.

De eigenschappen van het element openen en overschakelen op de knop **Handel** tab. Op dit tabblad kunt u de koppeling met producten beheren. De tabel onder de kiezer bevat aanvullende informatie voor de gekoppelde objecten (alleen zichtbaar met een selectie). Klik op het detailspictogram om een volledig beeld in de productcockpit te krijgen. Als u een nieuw object wilt koppelen, klikt u op het pictogram van de productkiezer (mappictogram), selecteert u een object en sluit u de kiezer.

![pem-elementen](assets/pem-assets.png)

### Ervaringsfragmenten {#experience-fragments}

Met Experience Fragments kunt u op grote schaal herbruikbare of afzonderlijke productinhoud maken. De koppeling werkt ongeveer op dezelfde manier als een middel. Eigenschappen openen en overschakelen op **Handel** tab. Op dit tabblad kunt u de koppeling met producten en categorieën beheren. De tabellen onder de kiezers bevatten aanvullende informatie over de gekoppelde objecten (alleen zichtbaar met een selectie). Klik op het detailspictogram om een volledig beeld in de productcockpit te krijgen. Als u een nieuw object wilt koppelen, klikt u op het pictogram van de productkiezer (mappictogram), selecteert u een object en sluit u de kiezer.

![pem xf](assets/pem-xf.png)

### Contentfragmenten {#content-fragments}

Inhoudsfragmenten zijn het beste inhoudstype voor alle gestructureerde inhoud. Dit kan worden gebruikt om externe productgegevens te verhogen met extra marketinggegevens of om inhoud zonder kop te maken. De koppeling van een inhoudsfragment aan een productcatalogusobject vindt plaats via de referentietypen voor het product of de categorie in de Content Fragment Model Editor. U sleept gewoon het juiste referentietype naar het model en configureert het veld. Deze typen bieden ondersteuning voor enkelvoudige of meervoudige selectie.

![pem cf-model](assets/pem-cf-model.png)

Als u een nieuw inhoudsfragment maakt op basis van dit model, kunt u met deze referentietypen eenvoudig het juiste object selecteren met de desbetreffende kiezer.

![pem cf](assets/pem-cf.png)

### Product Cockpit {#product-cockpit}

Wij hebben de productcockpit (of console) in één van de vorige modules geïntroduceerd. De cockpit is een eenvoudige manier om niet alleen door de productcatalogus te bladeren, maar ook om alle bijbehorende AEM inhoud op één plaats te zien. Ga naar de productconsole en open de eigenschappen van een product dat bijbehorende inhoud heeft. Schakel over naar het desbetreffende tabblad om de bijbehorende inhoud weer te geven.

![pruimencockpit](assets/pem-cockpit.png)

Als u op het actiepictogram klikt, wordt dat stuk inhoud op een nieuw browsertabblad geopend.

## Afzonderlijke product- en rubriekpagina&#39;s verrijken {#enrich}

In de vorige modules hebt u geleerd hoe te met veelvoudige malplaatjes van de productcatalogus te werken. Meerdere sjablonen zijn een goede manier om verschillende sjablonen te maken, maar in veel gevallen is dit niet nodig. In veel gevallen kan dezelfde sjabloon worden gebruikt in combinatie met plaatsaanduidingen voor afzonderlijke inhoud. CIF steunt placeholders voor Inhoudsfragmenten en de Fragmenten van de Ervaring.

Laten we beginnen met de tijdelijke aanduiding voor het ervaringsfragment. Open een productsjabloon in de AEM editor. Sleep de **Fragmentatie van ervaring bij handel** op het malplaatje, dan open de config dialoog.

![tijdelijke aanduiding](assets/pem-placeholder.png)

Open het dialoogvenster van de component en voer een naam voor deze tijdelijke aanduiding in. U moet een tijdelijke aanduiding opgeven, zodat u zoveel plaatsaanduidingen kunt toevoegen als u nodig hebt.

![PEM XF-dialoogvenster](assets/pem-dialog-xf.png)

Open het ervaringsfragment dat u in de vorige stap aan een product hebt gekoppeld. Open eigenschappen en schakel over naar het tabblad Handel. Dezelfde plaatsaanduidingsnaam invoeren onder **Locatie tijdelijke aanduiding voor catalogus**.

![pem xf](assets/pem-xf.png)

Sleep nu de **Fragment met commerciële inhoud** op de sjabloon en open het configuratievenster.

![CF-dialoogvenster](assets/pem-dialog-cf.png)

Dit dialoogvenster wordt opnieuw gebruikt in het dialoogvenster Inhoud van kerncomponent fragment. Meer informatie vindt u onder extra bronnen. Het enige verschil is **Element koppelen** eigenschap die het id-veld (product-SKU of categorie-UID) in het model Inhoudsfragment configureert.

Bekijk nu een productpagina met een bijbehorend inhoudsfragment en/of ervaringsfragment. Wanneer AEM een pagina rendert, wordt gezocht naar elke plaatsaanduiding op basis van het type (Content or Experience Fragment), de id en de plaatsaanduidingsnaam voor Experience Fragments. AEM gebruikt een URL-oplosser om de id op te halen (SKU voor producten, UID voor categorieën). Als een Experience of Content Fragment wordt geretourneerd, wordt het gerenderd naar de plaatsaanduidingslocatie, anders wordt de plaatsaanduiding genegeerd.

![peperresultaat](assets/pem-result.png)

## Inhoud overzichtelijk maken {#making-shoppable}

Het is ook mogelijk om een regelmatige AEM pagina uit elkaar te zetten door commerciële componenten toe te voegen. Maak een nieuwe inhoudspagina in AEM en open de lege pagina in de editor.

![lege pem-pagina](assets/pem-page-empty.png)

Sleep eerst een productdetailcomponent naar de pagina. Schakel vervolgens over naar de zijbalk Middelen, schakel over naar producten en selecteer een product. Sleep het product naar de productcomponent. Hierdoor wordt een gewone productcomponent op een inhoudspagina weergegeven.

![pem-productpagina](assets/pem-page-product.png)

Als u bijbehorende inhoud voor dat product hebt gemaakt, schakelt u in de zijbalk Middelen over naar **Gekoppelde inhoud voor handel**. Op dit tabblad ziet u alle AEM inhoud die aan dit product is gekoppeld. Hierdoor kunt u de pagina&#39;s nu snel verfraaien met gekoppelde inhoud.

![pem verrijkte pagina](assets/pem-page-enriched.png)

## Einde van de reis? {#end-of-journey}

Gefeliciteerd! U hebt de reis van de Ontwikkelaar van de AEM Inhoud en van de Handel voltooid! Nu moet u:

* begrijpen hoe u elke AEM inhoud aan productcatalogusobjecten kunt koppelen
* gebruik plaatsaanduidingen om producten en categoriepagina&#39;s afzonderlijk te verrijken
* weten hoe u inhoud overzichtelijk kunt maken en het bijbehorende tabblad Inhoud kunt gebruiken

U bent nu klaar om productervaringen te beheren met AEM Content and Commerce. Er zijn echter nog veel meer opties beschikbaar voor AEM Inhoud en Handel. Bekijk enkele aanvullende bronnen die beschikbaar zijn in het dialoogvenster [Sectie Aanvullende bronnen](#additional-resources) voor meer informatie over de functies die u tijdens deze reis hebt gezien.

## Aanvullende bronnen {#additional-resources}

* [Ervaringen op het gebied van authoringhandel](/help/commerce-cloud/authoring/authoring-commerce-experiences.md)
* [Product Cockpit](/help/commerce-cloud/authoring/product-cockpit.md)
* [Component Inhoudsfragment](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html?lang=en)
