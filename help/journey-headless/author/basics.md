---
title: Grondbeginselen van ontwerpen leren
description: Leer over de concepten en de mechanica van creatie inhoud voor uw Zwaarloze CMS gebruikend Inhoudsfragmenten.
exl-id: 3eca973f-b210-41bb-98da-ecbd2bae9803
source-git-commit: 1473c1ffccc87cb3a0033750ee26d53baf62872f
workflow-type: tm+mt
source-wordcount: '1715'
ht-degree: 1%

---

# Grondbeginselen van ontwerpen voor headless met AEM {#author-headless-basics}

## Het artikel tot nu toe {#story-so-far}

Aan het begin van de [AEM Schrijverreis zonder kopinhoud](overview.md) de [Inleiding](introduction.md) heeft betrekking op de basisbegrippen en de terminologie die relevant zijn voor het ontwerpen van koploze producten.

Dit artikel bouwt hierop voort, zodat u begrijpt hoe u uw eigen inhoud voor uw AEM project zonder titel kunt ontwerpen.

## Doelstelling {#objective}

* **Publiek**: Begin
* **Doelstelling**: Introduceer de basisbeginselen van CMS-authoring zonder koppen:
   * Inleiding tot ontwerpen met AEMaaCS
   * Inleiding tot inhoudsfragmenten

## Basisbewerkingen {#basic-handling}

Voordat u de inhoud van fragmenten gaat beheren, volgt een (zeer) korte inleiding op het gebruik van AEM....maar niets vervangt echt de ervaring van het aanmelden en het proberen om het systeem te gebruiken.

### Auteur, Voorvertoning en Publiceren {#author-preview-publish}

Een AEM-installatie bestaat meestal uit drie omgevingen:

* Auteur
* Publicatie
* Voorvertoning

U meldt zich aan, en gebruikt het auteursmilieu om uw inhoud te produceren. Wanneer u klaar bent, publiceert u de inhoud zodat deze algemeen beschikbaar wordt. Voor koploze gebruikers is dit voor andere toepassingen, voor webpagina&#39;s is dit voor lezers op het web.

Zie Concepten ontwerpen voor meer informatie.

Van de **Inhoudsfragmenten** -console, kunt u ook publiceren naar de **Voorvertoningsservice**, voor testen en voorvertonen, voordat u publiceert. Zie Een fragment publiceren en voorvertonen.

### Aanmelden {#signing-in}

Net als bij de meeste systemen moet u zich aanmelden. Als auteur krijgt u de volgende informatie:

* Gebruikersnaam (account)
* Wachtwoord
* Koppeling voor toegang tot het aanmeldingsscherm

Uw account is geconfigureerd met alle rechten die u nodig hebt. Als u om het even welke kwesties hebt, adviseren wij dat u uw intern team van de projectsteun contacteert.

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

![Content Fragments-console](/help/sites-cloud/administering/content-fragments/assets/cfc-console-filter.png)

### Handelingen, selecteren, weergeven {#actions-selecting-viewing}

In de **Inhoudsfragmenten** een reeks acties beschikbaar is voor uw inhoudsfragmenten op de werkbalk:

<!-- ![Console actions](assets/cfm-managing-cf-console-01.png) -->

* **Openen in elementen**
* **Maken**
* De **Verwezen door** de kolom biedt ook een directe koppeling om alle bovenliggende verwijzingen van dat fragment weer te geven; inclusief verwijzen naar inhoudsfragmenten, ervaringsfragmenten en pagina&#39;s.
* Als u de muis boven de mapnaam houdt, wordt het JCR-pad weergegeven.

Nadat u het fragment hebt geselecteerd, zijn alle relevante handelingen beschikbaar:

<!-- ![Console actions - fragment selected](assets/cfm-managing-cf-console-selected-01.png) -->

* **Open**
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

U kunt dit doen door een reeks mappen te maken binnen **Bestanden** van de **Activa** console. Selecteer **Maken** optie (rechtsboven), gevolgd door **Map**:

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

#### Net voor het geval - Configuratie van Cloud Services van mappen {#cloud-services-folder}

Alleen voor het geval...

U krijgt waarschijnlijk een eerste map waarin u uw mappen kunt maken. Dit is aangezien sommige configuratiedetails (gewoonlijk door een Ontwikkelaar of Beheerder van het Systeem) op de wortelomslag moeten worden toegepast. Dit interesseert u waarschijnlijk niet, maar als nodig kunt u controleren **Configuratie** in de **Cloud Services** van de map **Eigenschappen**:

![Mapeigenschappen maken - configuratie](/help/journey-headless/author/assets/headless-journey-author-folder-03.png)

>[!NOTE]
>
>U kunt meer lezen onder De configuratie toepassen op uw middelenmap.

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

<!--
Creating a Content Fragment is very similar - you just use the **Content Fragment** option instead:

![Create Content Fragment option](/help/journey-headless/author/assets/headless-journey-author-content-fragment-01.png)

This time a wizard opens. The first step is to select the Content Fragment Model that your fragment is based on:

![Create Content Fragment - select Model](/help/journey-headless/author/assets/headless-journey-author-content-fragment-02.png)

After continuing with **Next** you can supply the details (**Basic** and **Advanced**) for your fragment:

![Create Content Fragment - provide Name](/help/journey-headless/author/assets/headless-journey-author-content-fragment-03.png)

Confirm with **Create** and you can then **Open** your fragment in the editor.
-->

### Een fragment bewerken {#editing-fragment}

U kunt een fragment direct openen nadat u het hebt gemaakt, of door het te selecteren vanuit de console Inhoudsfragmenten (ook vanaf de console Elementen).

Wanneer de redacteur eerst opent ziet u:

* Een lijst met pictogrammen aan de linkerkant - hiermee hebt u toegang tot verschillende functies. De editor wordt geopend in het dialoogvenster **Variaties** -tabblad, vindt u hier de meeste bewerkingen plaats. U bent wellicht ook geïnteresseerd in de **Annotaties** en **Metagegevens** tabs.

* Een koptekst met informatie over het fragment en toegang tot verschillende handelingen.

* Het hoofdbewerkingsgebied. Dit is afhankelijk van het model waarmee het fragment is gemaakt.

Als voorbeelden:

* Een fragment dat alleen meerdere gegevens vereist, waarvan sommige een specifiek type hebben. Voor inhoud zonder kop zijn verwijzingen van essentieel belang (hierover leert u later op de reis).

  ![Inhoudsfragmenteditor - Mijn fragment](/help/journey-headless/author/assets/headless-journey-author-content-fragment-04.png)

* Een fragment waarmee u een lange sectie tekst kunt schrijven. Hier zijn aanvullende opties voor het beheren en opmaken van de tekst. U kunt zelfs de afzonderlijke tekstvelden openen in een volledige-schermeditor (met het kleine schermachtige pictogram rechts)

  ![Content Fragment Editor - Alaska Spirits](/help/journey-headless/author/assets/headless-journey-author-content-fragment-05.png)

>[!NOTE]
>
>Projectspecifieke documentatie kan nodig zijn om auteurs te helpen bij het voltooien van bepaalde velden.
>
>Zie Modellen van de Fragmenten van de Inhoud - de Types van Gegevens en Eigenschappen voor generische details.

Bevestig uw updates met of **Opslaan** of **Opslaan en sluiten**.

>[!NOTE]
>
>Voor meer details kunt u Variaties lezen - Inhoudsfragmenten ontwerpen.

#### Wat u (waarschijnlijk) niet hoeft te maken {#what-you-probably-do-not-need-to-worry-about}

Dit lijkt misschien een iets vreemde sectie, maar zodra u de Content Fragment Editor opent en gaat onderzoeken, ziet u verschillende opties die (waarschijnlijk) niet van toepassing zijn op de tocht zonder kop als Content Author. Dit is dus slechts een kort overzicht van wat je zou moeten kunnen negeren in de context zonder kop:

* **Modellen van contentfragmenten**

  De naam van het inhoudsfragmentmodel wordt boven in de editor weergegeven, direct onder de fragmentnaam. Dit is ook een verbinding die u aan de modelredacteur neemt.
Modellen van inhoudsfragmenten zijn in feite van vitaal belang voor inhoudsfragmenten als ze de structuur definiëren die u gebruikt. Het maken en bewerken van deze bestanden valt (gewoonlijk) echter onder de verantwoordelijkheid van een andere persoon, de Content Architect.

  >[!NOTE]
  >
  >Als u meer wilt weten, kunt u de AEM Headless Content Architect Journey lezen.

* **Gekoppelde inhoud**

  Dit is duidelijk aangezien het een lusje in de redacteur is.

  Inhoudsfragmenten zijn in AEM al een aantal versies beschikbaar. Oorspronkelijk zijn ze beschikbaar gesteld voor &quot;traditioneel&quot; gebruik bij het ontwerpen van pagina&#39;s....en zij worden in dit verband nog steeds gebruikt . Hierbij kan het gaan om het koppelen van elementen (bijvoorbeeld afbeeldingen) die weliswaar niet in het fragment zijn ingesloten, maar die wel beschikbaar moeten zijn voor de auteur wanneer deze een pagina ontwerpt.

* **Voorvertoning**

  Dit is een ander tabblad in de editor en biedt een technische weergave, voornamelijk bedoeld voor ontwikkelaars.

* **Paginaverwijzingen bijwerken**

  Deze handeling is beschikbaar via de **...** (ellipsen) drop-down. Het is niet interessant voor headless auteurs aangezien het op paginascreatie betrekking heeft.

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

* [Authoring van concepten](/help/sites-cloud/authoring/getting-started/concepts.md)

* [Basisverwerking](/help/sites-cloud/authoring/getting-started/basic-handling.md) - deze pagina is voornamelijk gebaseerd op de **Sites** console, maar veel/de meeste eigenschappen zijn ook relevant voor het ontwerpen **Inhoudsfragmenten** onder de **Activa** console.

   * [Deelvenster Navigatie](/help/sites-cloud/authoring/getting-started/basic-handling.md#navigation-panel)

   * [De koptekst](/help/sites-cloud/authoring/getting-started/basic-handling.md#the-header)

   * [Werkbalk Handelingen](/help/sites-cloud/authoring/getting-started/basic-handling.md#actions-toolbar)

   * [Snelle handelingen](/help/sites-cloud/authoring/getting-started/basic-handling.md#quick-actions)

   * [Bronnen weergeven en selecteren](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources)

   * [Spoorwegkiezer](/help/sites-cloud/authoring/getting-started/basic-handling.md#rail-selector)

* [Werken met contentfragmenten](/help/sites-cloud/administering/content-fragments/content-fragments.md)

   * [Contentfragmenten beheren](/help/sites-cloud/administering/content-fragments/content-fragments-managing.md)

   * [De configuratie toepassen op de middelenmap](/help/sites-cloud/administering/content-fragments/content-fragments-configuration-browser.md#apply-the-configuration-to-your-assets-folder)

   * [Een inhoudsfragment maken](/help/sites-cloud/administering/content-fragments/content-fragments-managing.md#creating-a-content-fragment)

   * [Variaties - Inhoudsfragmenten ontwerpen](/help/sites-cloud/administering/content-fragments/content-fragments-variations.md)

   * Publiceren

      * vanuit de editor, of **Activa** console

         * [Snel publiceren](/help/assets/manage-publication.md#quick-publish)

         * [Publicatie beheren](/help/assets/manage-publication.md#manage-publication)

      * Van de **Inhoudsfragmenten** Console

         * [Een inhoudsfragment publiceren en voorvertonen](/help/sites-cloud/administering/content-fragments/content-fragments-managing.md#publishing-and-previewing-a-fragment)

   * [Modellen van contentfragmenten](/help/sites-cloud/administering/content-fragments/content-fragments-models.md)

      * [Content Fragment Models - Data Types](/help/sites-cloud/administering/content-fragments/content-fragments-models.md#data-types)

      * [Modellen van inhoudsfragmenten - eigenschappen](/help/sites-cloud/administering/content-fragments/content-fragments-models.md#properties)

      * [Modellen van inhoudsfragmenten - Modellen van inhoudsfragmenten toestaan in uw middelenmap](/help/sites-cloud/administering/content-fragments/content-fragments-models.md#allowing-content-fragment-models-assets-folder)

* Aan de slag - hulplijnen
   * [Een headless Setup voor middelenmappen maken](/help/headless/setup/create-assets-folder.md)

* Reis van architect zonder hoofdinhoud AEM

* AEM doorlopende vertaalreis
