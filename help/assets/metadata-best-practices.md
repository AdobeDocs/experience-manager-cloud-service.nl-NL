---
title: Metagegevensbeheer en best practices
description: Leer meer over best practices voor metagegevens om uw digitale middelen effectief te beheren.
role: User, Admin
exl-id: d90519df-55a6-4e23-81ad-ff2365d71c0d
feature: Metadata, Best Practices
source-git-commit: c82f84fe99d8a196adebe504fef78ed8f0b747a9
workflow-type: tm+mt
source-wordcount: '1411'
ht-degree: 0%

---

<!-- Keywords to focus on:
metadata best practices
aem metadata 
experience manager metadata-->

# Metagegevensbeheer en best practices {#metadata-best-practices}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b> Dynamische Media Prime en Ultimate </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b> AEM Assets Ultimate </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b> integratie van AEM Assets met Edge Delivery Services </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b> Uitbreidbaarheid UI </b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuw </i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b> laat Dynamische Media Prime en Ultimate </b></a> toe
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b> Beste praktijken van het Onderzoek </b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b> Content Hub </b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b> Dynamische Media met mogelijkheden OpenAPI </b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b> de ontwikkelaarsdocumentatie van AEM Assets </b></a>
        </td>
    </tr>
</table>

Om uw bedrijf te laten opvallen en meer klanten aan te trekken, is het van cruciaal belang gebruik te maken van beelden, video&#39;s en andere digitale middelen van hoge kwaliteit. Hiervoor hebt u een proces nodig waarmee u metagegevens kunt toevoegen aan alle digitale elementen, zodat u deze gemakkelijk kunt doorzoeken. Metagegevens zijn de gegevens die essentiële gegevens bevatten over digitale elementen, zoals de naam, het type, de locatie in een opslagplaats, de gewijzigde datum en de bijbehorende tags. Metagegevens stroomlijnen het middelenbeheer, verbeteren de doorzoekbaarheid en toegankelijkheid en zorgen voor een effectieve versiebeheersing.

Leer hoe te om meta-gegevens in het Digitale systeem van het Beheer van Activa te gebruiken (DAM) om meta-gegevens van uw digitale activa [&#128279;](manage-metadata.md) effectief te beheren.

## Typen metagegevens

Op basis van de verschillende aspecten van gegevens worden metagegevens gecategoriseerd als technische metagegevens, informatieve metagegevens en metagegevens van het beheer.

### Technische metagegevens

Technische metagegevens omvatten de technische aspecten van een element. Dit soort metagegevens is van cruciaal belang voor de gebruikers om inzicht te krijgen in de inherente kenmerken van digitale elementen, waardoor een efficiënte verwerking en een efficiënt gebruik mogelijk worden.
Het bevat details zoals:

* Bestandsgrootte
* Indeling
* Resolutie
* Afmetingen
* Kleurmodus

### Informatieve metagegevens

Informatiemetagegevens omvatten beschrijvende informatie die het begrip van de inhoud van een element verbetert. Deze metagegevens zijn van cruciaal belang voor het detecteren van inhoud, doorzoekbaarheid en het begrijpen van de betekenis van het element. De informatieve meta-gegevens omvatten sleutelwoorden, titels, en beschrijvingen.

Wanneer u bijvoorbeeld een video beheert in Experience Manager Assets, kunnen we de volgende metagegevens over informatie opnemen:

* **Sleutelwoorden**: Marketing, de lancering van het Product, Bevordering
* **Bijschrift**: Introduceer ons recentste product met opwindende eigenschappen
* **Beschrijving**: Een gedetailleerd overzicht van de videoinhoud.

Gebruikers die op zoek zijn naar marketinggerelateerde inhoud, kunnen de betekenis van de bovenstaande video gemakkelijk vinden en begrijpen.

### Administratieve metagegevens

Administratieve metagegevens hebben betrekking op de beheeraspecten van digitale elementen. Het zorgt voor toegangsbeheer, naleving en beheer van de algemene levenscyclus van middelen binnen het systeem voor beheer van digitale middelen. Het bevat informatie over:

* Eigendom van activa
* Gebruiksrechten
* Machtigingen
* Overige administratieve gegevens

De administratieve meta-gegevens verzekeren het correcte activabeheer, controlerend toegang, en naleving binnen het digitale systeem van het activabeheer.

## Best practices voor metagegevens

### De strategie voor metagegevens vanaf het begin definiëren

Metagegevensbeheer begint met het definiëren van een metagegevensstrategie die een basis vormt voor het beoordelen van de langetermijnwaarde.

Het maken van een aangepast metagegevensschema naar wens is van cruciaal belang wanneer u uw strategie voor metagegevens plant. Een goed ontworpen schema biedt een gestructureerd kader voor het indelen en indelen van elementen in Experience Manager.

#### Video: Aangepaste velden toevoegen aan het metagegevensschema

>[!VIDEO](https://video.tv.adobe.com/v/3425977)

Uw strategie voor metagegevens kan het volgende definiëren:

* **Doelstellingen:** beschrijft duidelijk de doelstellingen en de verwachte resultaten van de meta-gegevens. Bepaal wat u wilt bereiken door de metagegevens toe te voegen.

* **Doel:** bepaal waarom u meta-gegevens vangt. Geef de waarde op die aan uw processen, systemen of organisatie wordt toegevoegd.

* **Plan van de Toegankelijkheid:** creeer een plan om de meta-gegevens gemakkelijk toegankelijk en ontdekkbaar te maken. Verklaar wie het gaat gebruiken, en de hulpmiddelen of methodes om te gebruiken.

* **eigenschappen van Meta-gegevens:** identificeer en bepaal zorgvuldig elk meta-gegevensbezit. Ervoor zorgen dat elke eigenschap een duidelijke reden heeft om in de overeenkomst te worden opgenomen, die verband houdt met de doelstellingen en het doel.

Om consistente resultaten in de hele opslagplaats te garanderen, moet u de strategie zorgvuldig plannen. Leer meer over [ meta-gegevensschema&#39;s ](metadata-schemas.md).

### Een beheerplan voor metagegevens maken

Het beheer van gegevens zorgt ervoor dat de inspanningen van de organisatie voor het beheer van metagegevens worden afgestemd op de algemene bedrijfsdoelstellingen.
De governancestrategie kan omvatten:

* Vaststelling van beleid en procedures voor het beheer van gegevens en metagegevens.
* Vaststellen van normen voor gegevenskwaliteit en -integriteit.
* Rollen en verantwoordelijkheden in gegevensbeheer definiëren.

Bepaal waar de informatie vandaan komt en bestudeer de details van de metagegevensstrategie, inclusief de eigenschappen en de bronnen ervan. De schaal kan afhankelijk zijn van de complexiteit van de strategie. In grotere ondernemingen, is er een hoofdsysteem van het meta-gegevensbeheer dat veelvoudige systemen in de hoofdstapel controleert.

>[!NOTE]
>
>Leer hoe te [ meta-gegevens van uw digitale activa ](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/metadata.html?lang=nl-NL) beheren.

### Verenigbaar zijn met de metagegevensstrategie

Een consistente metagegevensstrategie zorgt voor een effectieve organisatie en opvraging van digitale elementen. Een strategische aanpak hanteren voor het vastleggen en implementeren van metagegevenswaarden, zodat de evolutie soepel verloopt zonder onnodige wijzigingen. <br>

Bij het beheer van metagegevens in de hele onderneming is consistentie belangrijk bij het benoemen van en verwijzen naar elementen. Als u bijvoorbeeld meerdere elementen tegelijk beheert, kunt u overwegen metagegevens bulksgewijs toe te voegen. <br>

Hieronder volgen enkele aanbevolen procedures:

* **vermijd dubbele waarden:** als u een inzameling van beelden van een marketing campagne hebt, gebruik verenigbare namen en vermijd duplicaten.<br>
Bijvoorbeeld, in plaats van het gebruiken van dubbele namen zoals *campagne_image_001* en *campagne_image_002*, voer een systematische noemende overeenkomst zoals *event_promotion* en *product_launch* uit, die een duidelijke en bevolen identificatie verzekeren.

* **gecontroleerde woordenboeken van het Gebruik effectief:** voer gecontroleerde woordenboeken uit door gestandaardiseerde termijnen voor markeringen aan te wenden. Leer hoe te om [ AEM Tagging Kader ](/help/implementing/developing/introduction/tagging-framework.md) effectief uit te voeren.  <br>
Bijvoorbeeld, constant gebruik termijnen zoals *product_launch* of *event_promotion* wanneer het etiketteren van beelden met thema&#39;s om systematische opeenvolging te handhaven.

* **handhaaf nauwkeurigheid en volledigheid:** om meta-gegevens verenigbaar, nauwkeurigheid, volledigheid, en groepering over diverse bronnen te houden zijn essentieel.
Wanneer u bijvoorbeeld metagegevens toevoegt aan een PDF-document, moet u controleren of details zoals auteurnamen en trefwoorden correct en volledig zijn.

#### Video: bulkmetagegevens toevoegen aan elementen

>[!VIDEO](https://video.tv.adobe.com/v/3425978)

### De doorzoekbaarheid van metagegevens beoordelen en verbeteren

Beoordeel uw strategie voor metagegevens om de zoekbaarheid van metagegevens te verbeteren. Vereenvoudig workflows en verbeter zoekmogelijkheden voor efficiënt hergebruik. Vermijd het omgaan met metagegevens die geen duidelijk doel hebben.

U kunt de volgende aanbevolen procedures in overweging nemen om uw zoekbaarheid van metagegevens te optimaliseren:

* **optimalisering van het Sleutelwoord:** verbeter meta-gegevensonderzoek door sleutelwoorden te optimaliseren verbonden aan activa. U kunt de relevantie van trefwoorden voor bepaalde elementen in de [!UICONTROL Assets Manager] verbeteren door de volgende stappen uit te voeren:

   1. Ga naar **[!UICONTROL Assets]** > **[!UICONTROL File]** > **[!UICONTROL [Asset folder]]** .
   1. Selecteer het element waarvan u de metagegevens wilt bijwerken en klik op **[!UICONTROL Properties]** .
   1. Navigeer naar het tabblad **[!UICONTROL Advanced]** en klik vervolgens **[!UICONTROL Add]** onder **[!UICONTROL Elevate for search keywords]** . <br> u moet het standaardmeta-gegevensschema gebruiken om de onderzoekssleutelwoorden op te heffen.
   1. Voer het trefwoord in waarvoor u de zoekopdracht wilt opvoeren en klik op **[!UICONTROL Add]** .<br>
U kunt meerdere trefwoorden toevoegen en deze rangschikken naar prioriteit.
   1. Klik op **[!UICONTROL Save & Close]** .
Zoek het element met de trefwoorden die u hebt toegevoegd. Het element wordt weergegeven in de bovenste zoekresultaten.

  Leer hoe te om [ onderzoek in Experience Manager ](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/search-and-discovery/search-boost.html?lang=nl-NL) op te voeren.

* **de meta-gegevensgebieden van de Douane:** pas uw meta-gegevensgebieden aan om extra informatie over activa te vangen. Voeg bijvoorbeeld specifieke velden toe voor projectdetails, copyrightinformatie of andere relevante gegevens die de zoekmogelijkheden verbeteren. Leer [ om douanemetagegevens ](meta-edit.md) in Experience Manager Assets uit te geven of toe te voegen.


* **de bevestiging van Meta-gegevens:** voer bevestigingscontroles voor meta-gegevensingangen uit om consistentie en nauwkeurigheid te verzekeren. Het gebruik van gecontroleerde woordenboeken maakt het validatieproces vloeiender en vermindert de kans op onduidelijke of inconsistente items. Dit kan het instellen van richtlijnen voor bepaalde eigenschappen van metagegevens vereisen om dubbelzinnige of inconsistente informatie te voorkomen.

* **het volgen van het Gebruik:** beoordeelt de relevantie en het gebruik van verschillende meta-gegevenseigenschappen in tijd. Veelgebruikte metagegevens identificeren en de prioriteit ervan bepalen of een belangrijke bijdrage leveren aan zoek- en herstelprocessen.

#### Video: Trefwoorden toevoegen om zoekbaarheid te verbeteren

>[!VIDEO](https://video.tv.adobe.com/v/3425979)

### Metagegevens eenvoudig en begrijpelijk houden

Vereenvoudig metagegevens voor beter bestuur en gebruikerstoepassing. Houd het eenvoudig en gemakkelijk te begrijpen, en moedig gebruikers aan om essentiële informatie toe te voegen.
Gebruik de volgende aanbevolen procedures om de metagegevens te vereenvoudigen:

* **optimaliseer bezitsopties:** concentreer zich op het benadrukken van essentiële eigenschappen zonder de gebruikers met teveel meta-gegevensgebieden te belasten om in te vullen. Als u bijvoorbeeld metagegevens voor een afbeelding toevoegt, neemt u alleen sleutelvelden op zoals titel, beschrijving en tags voor een effectieve categorisering.

* **elimineer onnodige standaardeigenschappen:** vereenvoudig de meta-gegevensvorm door gebrek uit-van-de-doos eigenschappen irrelevant voor uw gebruiksgeval te elimineren. Verwijder zelden gebruikte standaardeigenschappen voor een schonere interface en ervaring.

* **herzien periodiek en werk meta-gegevens bij:** werk regelmatig meta-gegevens bij en pas aan veranderende behoeften en technologieën aan om ervoor te zorgen dat de gebruikers waardevolle informatie in tijd verstrekken.

### De reis van inhoud analyseren

Onderzoek de leveringsketen van de inhoud om meta-gegevensbronnen te vinden en alle belanghebbenden, van bovenaf, voor een grondige beste praktijken benadering te betrekken. Neem verschillende personeelsleden op om volledige ondersteuning in de hele organisatie te garanderen. <br> neem meta-gegevens in diverse stadia op om de verantwoordelijkheid te delen om activa details tijdens het uploaden te verstrekken. De integratie van [!DNL Experience Manager Assets] en [!DNL Workfront] biedt bijvoorbeeld aanzienlijke voordelen op het gebied van metagegevensbeheer, waardoor de efficiëntie en de samenwerking bij het maken en beheren van inhoud worden verbeterd. Deze integratie zorgt voor een effectieve synchronisatie van metagegevens voor gekoppelde elementen, waarbij de projectdetails automatisch worden bijgewerkt wanneer er wijzigingen worden aangebracht in [!DNL Workfront] .

Geef vroegtijdig informatie over doelstellingen, vooruitgang, mijlpalen en uitdagingen, zodat alle belanghebbenden er hun bijdrage aan kunnen leveren en kunnen samenwerken. Stimuleer samenwerking in de hele organisatie om efficiënte processen en waardevolle metagegevens te maken.

Leer meer over [ meta-gegevens en zijn verwante concepten ](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/metadata-concepts.html?lang=nl-NL) om uw meta-gegevens van Experience Manager effectief te beheren.
