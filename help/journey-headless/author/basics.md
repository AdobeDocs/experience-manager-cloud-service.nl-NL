---
title: Grondbeginselen van ontwerpen leren
description: Leer over de concepten en de mechanica van creatie inhoud voor uw Zwaarloze CMS gebruikend Inhoudsfragmenten.
exl-id: 3eca973f-b210-41bb-98da-ecbd2bae9803
solution: Experience Manager
feature: Headless
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '1727'
ht-degree: 0%

---

# Grondbeginselen van ontwerpen voor headless met AEM {#author-headless-basics}

## Het artikel tot nu toe {#story-so-far}

Aan het begin van de [AEM Schrijverreis zonder kopinhoud](overview.md) de [Inleiding](introduction.md) heeft betrekking op de basisbegrippen en de terminologie die relevant zijn voor het ontwerpen van koploze producten.

Dit artikel bouwt hierop voort, zodat u begrijpt hoe u uw eigen inhoud voor uw AEM project zonder titel kunt ontwerpen.

## Doelstelling {#objective}

* **Publiek**: Begin
* **Doelstelling**: Introduceer de basisbeginselen van CMS-ontwerpen zonder koptekst:
   * Inleiding tot ontwerpen met AEMaaCS
   * Inleiding tot inhoudsfragmenten

## Basisverwerking {#basic-handling}

Voordat u de stappen met inhoudsfragmenten gaat beheren, volgt een (zeer) korte inleiding op het gebruik van AEM...maar niets vervangt echt de ervaring van het aanmelden en het proberen om het systeem te gebruiken.

### Auteur, Voorvertoning en Publiceren {#author-preview-publish}

Een AEM-installatie bestaat meestal uit drie omgevingen:

* Auteur
* Publiceren
* Voorvertoning

U meldt zich aan, en gebruikt het auteursmilieu om uw inhoud te produceren. Wanneer u klaar bent, publiceert u de inhoud zodat deze algemeen beschikbaar wordt. Voor koploze gebruikers is dit voor andere toepassingen, voor webpagina&#39;s is dit voor lezers op het web.

Zie Concepten ontwerpen voor meer informatie.

Van de **Inhoudsfragmenten** console, kunt u ook publiceren aan **Voorvertoningsservice**, voor testen en voorvertonen, voordat u publiceert. Zie Een fragment publiceren en voorvertonen.

### Aanmelden {#signing-in}

Net als bij de meeste systemen moet u zich aanmelden. Als auteur krijgt u de volgende informatie:

* Gebruikersnaam (account)
* Wachtwoord
* Koppeling voor toegang tot het aanmeldingsscherm

Uw account is geconfigureerd met alle rechten die u nodig hebt. Als u problemen hebt, raadt de Adobe u aan contact op te nemen met uw interne team voor projectondersteuning.

### Navigatie {#navigation}

De eerste keer dat u zich aanmeldt bij een kleine online zelfstudie, worden enkele van de belangrijkste functies van de gebruikersinterface gemarkeerd.

Vervolgens kunt u het navigatievenster gebruiken om toegang te krijgen tot belangrijke gebieden van AEM. Voor inhoudsfragmenten gebruikt u de opdracht **Inhoudsfragmenten** console (voor sommige acties gebruikt u ook de **Activa** console).

U kunt het navigatievenster openen door het Adobe-pictogram linksboven te selecteren, gevolgd door het kleine kompaspictogram.

<!--
The Navigation Panel can be opened by selecting Adobe icon at the top left, followed by the small compass icon:

![Navigation panel](/help/journey-headless/author/assets/headless-journey-author-navigation-01.png)
-->

>[!NOTE]
>Hoewel Inhoudsfragmenten een kenmerk van AEM zijn **Sites** worden opgeslagen als **Activa**. Dit is een technisch detail dat u niet zou moeten beïnvloeden, maar zou nuttig kunnen zijn om te weten.

Binnen de console kunt u mappen in het linkerdeelvenster selecteren om naar het inhoudsfragment te navigeren. U kunt ook filteren en/of zoeken.

![Content Fragments-console](/help/sites-cloud/administering/content-fragments/assets/cf-managing-console-filter.png)

### Handelingen, selecteren, weergeven {#actions-selecting-viewing}

In de **Inhoudsfragmenten** een reeks acties beschikbaar is voor uw inhoudsfragmenten op de werkbalk:

<!-- ![Console actions](assets/cfm-managing-cf-console-01.png) -->

* **Openen in elementen**
* **Maken**
* De **Verwezen door** de kolom verstrekt ook een directe verbinding om alle ouderverwijzingen van dat fragment te tonen; met inbegrip van het van verwijzingen voorzien van de Fragmenten van de Inhoud, de Fragmenten van de Ervaring en pagina&#39;s.
* Als u de muis boven de mapnaam houdt, wordt het JCR-pad weergegeven.

Nadat u het fragment hebt geselecteerd, zijn alle relevante handelingen beschikbaar:

<!-- ![Console actions - fragment selected](assets/cfm-managing-cf-console-selected-01.png) -->

* **Openen**
* **Publiceren** (en **Publiceren ongedaan maken**)
* **Kopiëren**
* **Verplaatsen**
* **Naam wijzigen**
* **Verwijderen**

>[!NOTE]
>
>Handelingen zoals Publiceren, Publiceren ongedaan maken, Verwijderen, Verplaatsen, Naam wijzigen, Kopiëren, een asynchrone taak activeren. De voortgang van die taak kan worden gecontroleerd via de interface AEM Async Jobs.

<!--
The **Assets** console has dedicated **Action Toolbars**, and **Quick Actions** that you can use after selecting a resource (for example, a folder or content fragment).

The Quick Actions are available for a single resource, see **Basel** in the example below:

![Quick Actions](/help/journey-headless/author/assets/headless-journey-author-navigation-05.png)

The Actions Toolbar provides access to the full range of actions - applicable for the current scenario. The actions available can change; for example, dependent on your location, or whether you have selected multiple resources:

![Action Toolbar](/help/journey-headless/author/assets/headless-journey-author-navigation-06.png)

You can select the format for viewing your resources with the View Selector:

![View Selector](/help/journey-headless/author/assets/headless-journey-author-navigation-03.png)

You can view additional information about items using the Rail Selector. This also gives access to additional actions.

![Left Rail](/help/journey-headless/author/assets/headless-journey-author-navigation-04.png)
-->

## Inhoudsfragmenten ontwerpen {#authoring-content-fragments}

Dat was dus een zeer snelle inleiding op de AEM Gebruikersinterface (UI), maar hopelijk hebt u de kans gehad om het uit te proberen. Nu komen we neer op je echte interesse - Content Fragments voor Headless.

We moeten de zaken van begin tot eind doorlopen, maar in uw instantie zijn mogelijk al mappen en/of fragmenten gemaakt. Deze bevinden zich mogelijk op verschillende locaties. De beginselen zijn dezelfde.

### Organiseren en navigeren {#organizing-and-navigating}

Tenzij u zeer weinig Inhoudsfragmenten hebt, wilt u deze ordenen - zodat u (en anderen) ze opnieuw kunt vinden.

#### Een map maken {#creating-folder}

U kunt dit doen door een reeks mappen te maken binnen **Bestanden** van de **Activa** console. Selecteer de **Maken** optie (rechtsboven), gevolgd door **Map**:

![Map maken, optie](/help/journey-headless/author/assets/headless-journey-author-folder-01.png)

Er wordt een dialoogvenster geopend waarin u de details kunt invoeren en vervolgens kunt bevestigen met **Maken**:

![Map maken, dialoogvenster](/help/journey-headless/author/assets/headless-journey-author-folder-02.png)

#### Paden en tags gebruiken om de in de map beschikbare modellen van inhoudsfragmenten te beperken {#tags-paths-for-models-in-folder}

Deze sectie is iets geavanceerder. U hebt het niet echt nodig als u gewoon begint en dingen probeert, maar het is *zeer* Dit is handig wanneer u veel fragmenten hebt. Het is dus goed om dat te weten, ook al gebruikt u het nog niet helemaal.

Uw Content Architect zal alle Content Fragment Models hebben gecreeerd die voor uw huidige project worden vereist, en misschien ook sommige andere projecten. Om de zaken voor zich, en andere auteurs eenvoudig te houden, kunt u de lijst van modellen beperken beschikbaar voor een specifieke omslag.

Nadat u de map hebt gemaakt, kunt u de map openen **Eigenschappen**. Hier zijn diverse lusjes met informatie, en configuratiedetails, over de omslag. Met name voor inhoudsfragmenten kunt u de opdracht **Beleid** om specifieke paden en/of tags voor deze map te definiëren. Dit beperkt de modellen van het Fragment van de Inhoud beschikbaar voor gebruik in de omslag aangezien het betekent dat de Modellen van het Fragment van de Inhoud aan deze vereisten moeten voldoen alvorens zij kunnen worden gebruikt om fragmenten in deze omslag te produceren.

![Mapeigenschappen maken - beleid](/help/journey-headless/author/assets/headless-journey-author-folder-04.png)

>[!NOTE]
>
>U kunt meer informatie lezen onder Modellen van inhoudsfragmenten - Modellen van inhoudsfragmenten toestaan in de middelenmap.

Vervolgens navigeert u door deze mappen om inhoudsfragmenten te maken en te bewerken.

#### Net voor het geval - Configuratie van Cloud Servicen van mappen {#cloud-services-folder}

Alleen voor het geval...

U krijgt waarschijnlijk een eerste map waarin u uw mappen kunt maken. Dit is aangezien sommige configuratiedetails (gewoonlijk door een Ontwikkelaar of Beheerder van het Systeem) op de wortelomslag moeten worden toegepast. Dit interesseert u waarschijnlijk niet, maar als nodig kunt u controleren **Configuratie** in de **Cloud Servicen** van de map **Eigenschappen**:

![Mapeigenschappen maken - configuratie](/help/journey-headless/author/assets/headless-journey-author-folder-03.png)

>[!NOTE]
>
>U kunt meer lezen onder Toepassen de Configuratie op uw Omslag van Activa.

### Een inhoudsfragment maken {#creating-fragment}

In de **Inhoudsfragmenten** console die u kunt gebruiken **Maken** om de **Nieuw inhoudsfragment** dialoogvenster:

![Content Fragments console - Een nieuw fragment maken](/help/sites-cloud/administering/content-fragments/assets/cfc-console-create.png)

Geef de volgende instellingen op:

* **Locatie**
* **Inhoudsfragmentmodel**
* **Titel**
* **Naam**
* **Beschrijving**

Bevestig vervolgens met een van beide **Maken** of **Maken en openen**.

### Een fragment bewerken {#editing-fragment}

U kunt een fragment direct openen nadat u het hebt gemaakt, of door het te selecteren vanuit de console Inhoudsfragmenten (ook vanaf de console Elementen).

>[!NOTE]
>
>Inhoudsfragmenten zijn een functie Sites, maar worden opgeslagen als **Activa**.
>
>Er zijn twee editors voor het ontwerpen van inhoudsfragmenten.
>
>* De nieuwe editor, die voornamelijk wordt geopend vanuit de **Inhoudsfragmenten** console.
>* De oorspronkelijke editor, die voornamelijk wordt geopend vanuit de **Activa** console.

Wanneer de redacteur eerst opent ziet u:

* bovenste werkbalk: voor belangrijke informatie en handelingen
   * een koppeling naar de Content Fragment Console (pictogram Start)
   * informatie over het model en de map
   * koppelingen naar Voorvertoning; als het standaard URL-voorvertoningspatroon is geconfigureerd voor het model
   * Handelingen publiceren en publiceren ongedaan maken
   * een optie om alles weer te geven **Bovenliggende verwijzingen** (koppelingspictogram)
   * het fragment **Status** en laatst opgeslagen gegevens
   * een schakeloptie voor het overschakelen naar de oorspronkelijke (op elementen gebaseerde) editor
* linkerdeelvenster: toont de **Variaties** voor het inhoudsfragment en de bijbehorende **Velden**:
   * U kunt deze koppelingen gebruiken om door de structuur van het inhoudsfragment te navigeren
* rechterdeelvenster: geeft tabbladen weer met de eigenschappen (metagegevens) en tags, informatie over de versiegeschiedenis en informatie over eventuele taalkopieën
   * in de **Eigenschappen** kunt u de **Titel** en **Beschrijving** voor het fragment, of **Variatie**
* centraal deelvenster: geeft de daadwerkelijke velden en inhoud van de geselecteerde variatie weer
   * kunt u de inhoud bewerken
   * indien **Tijdelijke aanduiding voor tab** velden worden gedefinieerd binnen het model dat ze hier worden weergegeven en kunnen worden gebruikt voor navigatie

Een fragment kan bijvoorbeeld:

* Vereisen veelvoudige stukken van informatie, sommige met een specifiek type. Voor inhoud zonder kop zijn verwijzingen essentieel (u leert hierover later op uw reis).

* Hiermee kunt u een lange sectie tekst schrijven. Hier zijn aanvullende opties voor het beheren en opmaken van de tekst. U kunt zelfs de afzonderlijke tekstvelden openen in een volledige-schermeditor (met het kleine schermachtige pictogram rechts)

![Content Fragment Editor - Alaska Spirits](/help/sites-cloud/administering/content-fragments/assets/cf-authoring-overview.png)

>[!NOTE]
>
>Projectspecifieke documentatie kan nodig zijn om auteurs te helpen bij het voltooien van bepaalde velden.
>
>Zie Modellen van de Fragmenten van de Inhoud - de Types van Gegevens en Eigenschappen voor generische details.

Bevestig uw updates met één van beiden **Opslaan** of **Opslaan en sluiten**.

>[!NOTE]
>
>Voor meer details kunt u Variaties lezen - Inhoudsfragmenten ontwerpen.

#### Wat u (waarschijnlijk) niet hoeft te maken {#what-you-probably-do-not-need-to-worry-about}

Dit lijkt misschien een iets vreemde sectie, maar zodra u de Content Fragment Editor opent en gaat onderzoeken, ziet u verschillende opties die (waarschijnlijk) niet van toepassing zijn op de tocht zonder kop als Content Author. Dit is dus slechts een kort overzicht van wat je zou moeten kunnen negeren in de context zonder kop:

* **Modellen van contentfragmenten**

  U kunt de naam van het model van het Fragment van de Inhoud in het juiste paneel van de redacteur zien. Dit is ook een verbinding die u aan de modelredacteur neemt.
Modellen van inhoudsfragmenten zijn in feite van vitaal belang voor inhoudsfragmenten als ze de structuur definiëren die u gebruikt. Het maken en bewerken van deze bestanden valt (gewoonlijk) echter onder de verantwoordelijkheid van een andere persoon, de Content Architect.

  >[!NOTE]
  >
  >Als u meer wilt weten, kunt u de AEM Headless Content Architect Journey lezen.

### Publiceren {#publishing}

<!-- needs more details -->

Nadat u het fragment hebt voltooid, kunt u **Publiceren** zodat deze beschikbaar is voor toepassingen zonder koppen.

De publicatieacties zijn beschikbaar in de editor:

![Inhoudsfragmenteditor - Mijn fragment](/help/journey-headless/author/assets/headless-journey-author-content-fragment-06.png)

>[!NOTE]
>
>U kunt het fragment ook publiceren via het dialoogvenster **Activa** of **Inhoudsfragmenten** console.

## Volgende functies {#whats-next}

Nu u de grondbeginselen hebt geleerd, is de volgende stap: [Meer informatie over verwijzingen](references.md). Dit zal de diverse beschikbare verwijzingen introduceren en bespreken, en hoe te om niveaus van structuur met de Verwijzingen van het Fragment tot stand te brengen - een zeer belangrijk deel van creatie voor headless.

## Aanvullende bronnen {#additional-resources}

* [Concepten ontwerpen](/help/sites-cloud/authoring/author-publish.md)

* [Basisverwerking](/help/sites-cloud/authoring/basic-handling.md) - deze pagina is voornamelijk gebaseerd op de **Sites** console, maar veel/de meeste eigenschappen zijn ook relevant voor het ontwerpen **Inhoudsfragmenten** onder de **Activa** console.

   * [Deelvenster Navigatie](/help/sites-cloud/authoring/basic-handling.md#navigation-panel)

   * [De koptekst](/help/sites-cloud/authoring/basic-handling.md#the-header)

   * [Werkbalk Handelingen](/help/sites-cloud/authoring/basic-handling.md#actions-toolbar)

   * [Snelle handelingen](/help/sites-cloud/authoring/basic-handling.md#quick-actions)

   * [Bronnen weergeven en selecteren](/help/sites-cloud/authoring/basic-handling.md#viewing-and-selecting-resources)

   * [Spoorwegkiezer](/help/sites-cloud/authoring/basic-handling.md#rail-selector)

* [Werken met inhoudsfragmenten](/help/sites-cloud/administering/content-fragments/overview.md)

   * [Inhoudsfragmenten beheren](/help/sites-cloud/administering/content-fragments/managing.md)

   * [De configuratie toepassen op de middelenmap](/help/sites-cloud/administering/content-fragments/setup.md#apply-the-configuration-to-your-folder)

   * [Een inhoudsfragment maken](/help/sites-cloud/administering/content-fragments/managing.md#creating-a-content-fragment)

   * [Inhoudsfragmenten ontwerpen](/help/sites-cloud/administering/content-fragments/authoring.md)

   * Publiceren

      * vanuit de editor, of **Activa** console

         * [Snel publiceren](/help/assets/manage-publication.md#quick-publish)

         * [Publicatie beheren](/help/assets/manage-publication.md#manage-publication)

      * Van de **Inhoudsfragmenten** Console

         * [Een inhoudsfragment publiceren en voorvertonen](/help/sites-cloud/administering/content-fragments/managing.md#publishing-and-previewing-a-fragment)

   * [Modellen van inhoudsfragmenten](/help/sites-cloud/administering/content-fragments/content-fragment-models.md)

      * [Modellen van inhoudsfragmenten - gegevenstypen](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#data-types)

      * [Modellen van inhoudsfragmenten - eigenschappen](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#properties)

      * [Modellen van inhoudsfragmenten - Modellen van inhoudsfragmenten toestaan in uw middelenmap](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#allowing-content-fragment-models-assets-folder)

* [Inhoudsfragmenten - oorspronkelijke editor, uit de middelenconsole](/help/assets/content-fragments/content-fragments-variations.md)

* Aan de slag - hulplijnen
   * [Een headless Setup voor middelenmappen maken](/help/headless/setup/create-assets-folder.md)

* Reis van architect zonder hoofdinhoud AEM

* AEM doorsnedenloze vertaalreis
