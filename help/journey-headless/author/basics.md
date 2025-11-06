---
title: Grondbeginselen van ontwerpen leren
description: Leer over de concepten en de mechanica van het ontwerpen van inhoud voor uw Headless CMS gebruikend Inhoudsfragmenten.
exl-id: 3eca973f-b210-41bb-98da-ecbd2bae9803
solution: Experience Manager
feature: Headless, Content Fragments,GraphQL API
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1733'
ht-degree: 0%

---

# Grondbeginselen van ontwerpen voor headless met AEM {#author-headless-basics}

## Het artikel tot nu toe {#story-so-far}

Aan het begin van de [&#x200B; Reis van de Auteur van de Inhoud van AEM Headless &#x200B;](overview.md) de [&#x200B; Inleiding &#x200B;](introduction.md) behandelde de basisconcepten en de terminologie relevant voor creatie voor hoofd.

Dit artikel bouwt hierop voort, zodat u begrijpt hoe u uw eigen inhoud voor uw AEM-project zonder titel kunt maken.

## Doelstelling {#objective}

* **Publiek**: Begin
* **Doelstelling**: Introduceer de grondbeginselen van de Schrijven van CMS zonder Titel:
   * Inleiding tot ontwerpen met AEMaaCS
   * Inleiding tot inhoudsfragmenten

## Basisverwerking {#basic-handling}

Voordat u de contentfragmenten gaat beheren, volgt u een (zeer) snelle inleiding op het gebruik van AEM...maar niets vervangt echt de ervaring van het aanmelden en het proberen om het systeem te gebruiken.

### Auteur, Voorvertoning en Publiceren {#author-preview-publish}

Een AEM-installatie bestaat meestal uit drie omgevingen:

* Auteur
* Publiceren
* Voorvertoning

U meldt zich aan, en gebruikt het auteursmilieu om uw inhoud te produceren. Wanneer u klaar bent, publiceert u de inhoud zodat deze algemeen beschikbaar wordt. Voor koploze gebruikers is dit voor andere toepassingen, voor webpagina&#39;s is dit voor lezers op het web.

Zie Concepten ontwerpen voor meer informatie.

Van de **console van de Fragmenten van de Inhoud**, kunt u aan de **Dienst van de Voorproef**, voor het testen en het voorvertonen, voorafgaand aan publiceren ook publiceren. Zie Een fragment publiceren en voorvertonen.

### Aanmelden {#signing-in}

Net als bij de meeste systemen moet u zich aanmelden. Als auteur krijgt u de volgende informatie:

* Gebruikersnaam (account)
* Wachtwoord
* Koppeling voor toegang tot het aanmeldingsscherm

Uw account is geconfigureerd met alle rechten die u nodig hebt. Als u problemen hebt, raadt Adobe u aan contact op te nemen met uw interne team voor projectondersteuning.

### Navigatie {#navigation}

De eerste keer dat u zich aanmeldt bij een kleine online zelfstudie, worden enkele van de belangrijkste functies van de gebruikersinterface gemarkeerd.

Vervolgens kunt u het navigatievenster gebruiken om toegang te krijgen tot belangrijke gebieden van AEM. Voor de Fragmenten van de Inhoud, gebruikt u de **console van de Fragmenten van de Inhoud** (voor sommige acties zult u ook de **Assets** console gebruiken).

U kunt het navigatievenster openen door het Adobe-pictogram linksboven te selecteren, gevolgd door het kleine kompaspictogram.

>[!NOTE]
>Hoewel de Fragmenten van de Inhoud een eigenschap van de Plaatsen van AEM **zijn, worden zij bewaard als** Assets **.** Dit is een technisch detail dat u niet zou moeten beïnvloeden, maar zou nuttig kunnen zijn om te weten.

Binnen de console van de Fragmenten van de Inhoud kunt u omslagen in het linkerpaneel selecteren om aan uw Inhoudsfragment te navigeren. U kunt ook filteren en/of zoeken.

![&#x200B; de console van Fragmenten van de Inhoud &#x200B;](/help/sites-cloud/administering/content-fragments/assets/cf-managing-console-filter.png)

### Handelingen, selecteren, weergeven {#actions-selecting-viewing}

In de **console van de Fragmenten van de Inhoud** is een waaier van acties beschikbaar voor uw inhoudsfragmenten van de toolbar:

* **Open in Assets**
* **creeer**
* De **die** kolom van verwijzingen wordt voorzien verstrekt ook een directe verbinding om alle ouderverwijzingen van dat fragment te tonen; met inbegrip van het van verwijzingen voorzien van de Fragmenten van de Inhoud, de Fragmenten van de Ervaring en pagina&#39;s.
* Als u de muis boven de mapnaam houdt, wordt het JCR-pad weergegeven.

Nadat u het fragment hebt geselecteerd, zijn er verdere acties beschikbaar (al naar gelang van toepassing):

* **Open**
* **publiceer** (en **unpublish**)
* **beheert Markeringen**
* **Exemplaar**
* **vervangen**
* **Beweging**
* **anders noemen**
* **Schrapping**

>[!NOTE]
>
>Handelingen zoals Publiceren, Publiceren ongedaan maken, Verwijderen, Verplaatsen, Naam wijzigen, Kopiëren, een asynchrone taak activeren. De voortgang van die taak kan worden gecontroleerd via de gebruikersinterface van AEM Async Jobs.

## Inhoudsfragmenten ontwerpen {#authoring-content-fragments}

Dat was dus een zeer snelle inleiding op de gebruikersinterface van AEM, maar hopelijk hebt u de kans gehad om het uit te proberen. Nu komen we neer op je echte interesse - Content Fragments voor Headless.

We moeten de zaken van begin tot eind doorlopen, maar in uw instantie zijn mogelijk al mappen en/of fragmenten gemaakt. Deze bevinden zich mogelijk op verschillende locaties. De beginselen zijn dezelfde.

### Organiseren en navigeren {#organizing-and-navigating}

Tenzij u zeer weinig Inhoudsfragmenten hebt, wilt u deze ordenen - zodat u (en anderen) ze opnieuw kunt vinden.

#### Een map maken {#creating-folder}

U kunt dit doen door een reeks omslagen binnen **te creëren Dossiers** sectie van de **Assets** console. Selecteer **creeer** optie (hoogste recht), die door **Omslag** wordt gevolgd:

![&#x200B; creeer de optie van de Omslag &#x200B;](/help/journey-headless/author/assets/headless-journey-author-folder-01.png)

Een dialoog opent waar u de details kunt ingaan, dan bevestig met **&#x200B;**&#x200B;creëren:

![&#x200B; creeer de dialoog van de Omslag &#x200B;](/help/journey-headless/author/assets/headless-journey-author-folder-02.png)

#### Paden en tags gebruiken om de in de map beschikbare modellen van inhoudsfragmenten te beperken {#tags-paths-for-models-in-folder}

Deze sectie is iets geavanceerder. U hebt het niet echt nodig als u enkel begint en dingen probeert, maar het is *zeer* nuttig wanneer u vele fragmenten hebt. Het is dus goed om dat te weten, ook al gebruikt u het nog niet helemaal.

Uw Content Architect zal alle Content Fragment Models hebben gecreeerd die voor uw huidige project worden vereist, en misschien ook sommige andere projecten. Om de zaken voor zich, en andere auteurs eenvoudig te houden, kunt u de lijst van modellen beperken beschikbaar voor een specifieke omslag.

Na het creëren van uw omslag kunt u de omslag **Eigenschappen** openen. Hier zijn diverse lusjes met informatie, en configuratiedetails, over de omslag. Met name voor de Fragmenten van de Inhoud, kunt u het **lusje van Beleid** gebruiken om specifieke wegen en/of markeringen voor deze omslag te bepalen. Dit beperkt de modellen van het Fragment van de Inhoud beschikbaar voor gebruik in de omslag aangezien het betekent dat de Modellen van het Fragment van de Inhoud aan deze vereisten moeten voldoen alvorens zij kunnen worden gebruikt om fragmenten in deze omslag te produceren.

![&#x200B; creeer de Eigenschappen van de Omslag - Beleid &#x200B;](/help/journey-headless/author/assets/headless-journey-author-folder-04.png)

>[!NOTE]
>
>U kunt meer informatie lezen onder Modellen van inhoudsfragmenten - Modellen van inhoudsfragmenten toestaan in uw Assets-map.

Vervolgens navigeert u door deze mappen om inhoudsfragmenten te maken en te bewerken.

#### Alleen in geval - Configuratie van Mapcloudservices {#cloud-services-folder}

Alleen voor het geval...

U krijgt waarschijnlijk een eerste map waarin u uw mappen kunt maken. Dit is aangezien sommige configuratiedetails (gewoonlijk door een Ontwikkelaar of Beheerder van het Systeem) op de wortelomslag moeten worden toegepast. Dit zal waarschijnlijk u niet interesseren, maar indien nodig kunt u de **Configuratie** in de **Diensten van de Wolk** van de omslag **Eigenschappen** controleren:

![&#x200B; creeer de Eigenschappen van de Omslag - Configuratie &#x200B;](/help/journey-headless/author/assets/headless-journey-author-folder-03.png)

>[!NOTE]
>
>U kunt meer lezen onder De configuratie toepassen op uw Assets-map.

### Een inhoudsfragment maken {#creating-fragment}

In de **console van de Fragmenten van de Inhoud** kunt u **gebruiken creeer** om de **Nieuwe dialoog van het Fragment van de Inhoud** te openen:

![&#x200B; de console van Fragmenten van de Inhoud - Creërend een nieuw fragment &#x200B;](/help/sites-cloud/administering/content-fragments/assets/cfc-console-create.png)

Geef de volgende instellingen op:

* **Plaats**
* **model van het Fragment van de Inhoud**
* **Titel**
* **Naam**
* **Beschrijving**

Dan bevestig met of **creeer** of **creeer en open**.

### Een fragment bewerken {#editing-fragment}

U kunt een fragment direct openen nadat u het hebt gemaakt, of door het te selecteren via de console Inhoudsfragmenten (ook vanuit de Assets-console).

>[!NOTE]
>
>De Fragmenten van de inhoud zijn een eigenschap van Plaatsen, maar worden opgeslagen als **Assets**.
>
>Er zijn twee editors voor het ontwerpen van inhoudsfragmenten.
>
>* De nieuwe redacteur, hoofdzakelijk betreden van de **console van de Fragmenten van de Inhoud**.
>* De originele redacteur, hoofdzakelijk betreden van de **Assets** console.

Wanneer de redacteur eerst opent ziet u:

* bovenste werkbalk: voor belangrijke informatie en handelingen
   * een koppeling naar de Content Fragment Console (pictogram Start)
   * informatie over het model en de map
   * koppelingen naar Voorvertoning; als het standaard URL-voorvertoningspatroon is geconfigureerd voor het model
   * Handelingen publiceren en publiceren ongedaan maken
   * een optie om alle **Verwijzingen van de Ouder** (verbindingspictogram) te tonen
   * het fragment **Status**, en laatst bewaarde informatie
   * een schakeloptie voor het overschakelen naar de oorspronkelijke (op Assets gebaseerde) editor
* linkerpaneel: toont de **Variaties** voor het Fragment van de Inhoud, en zijn **Gebieden**:
   * U kunt deze koppelingen gebruiken om door de structuur van het inhoudsfragment te navigeren
* rechterdeelvenster: geeft tabbladen weer met de eigenschappen (metagegevens) en tags, informatie over de versiegeschiedenis en informatie over eventuele taalkopieën
   * in het **lusje van Eigenschappen** kunt u de **Titel** en **Beschrijving** voor het fragment bijwerken, of **Variatie**
* centraal deelvenster: geeft de daadwerkelijke velden en inhoud van de geselecteerde variatie weer
   * kunt u de inhoud bewerken
   * als **de gebieden van Tijdelijke aanduiding van het Lusje** worden bepaald binnen het model zij hier worden getoond, en kunnen voor het navigeren worden gebruikt

Een fragment kan bijvoorbeeld:

* Vereisen veelvoudige stukken van informatie, sommige met een specifiek type. Voor inhoud zonder kop zijn verwijzingen essentieel (u leert hierover later op uw reis).

* Hiermee kunt u een lange sectie tekst schrijven. Hier zijn aanvullende opties voor het beheren en opmaken van de tekst. U kunt zelfs de afzonderlijke tekstvelden openen in een volledige-schermeditor (met het kleine schermachtige pictogram rechts)

![&#x200B; de Redacteur van het Fragment van de Inhoud - de Rondjes van Alaska &#x200B;](/help/sites-cloud/administering/content-fragments/assets/cf-authoring-overview.png)

>[!NOTE]
>
>Projectspecifieke documentatie kan nodig zijn om auteurs te helpen bij het voltooien van bepaalde velden.
>
>Zie Modellen van de Fragmenten van de Inhoud - de Types van Gegevens en Eigenschappen voor generische details.

Bevestig uw updates met of **sparen** of **sparen &amp; sluit**.

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

Zodra u uw fragment hebt voltooid kunt u **publiceren** het zodat het aan de toepassingen zonder kop beschikbaar is.

De publicatieacties zijn beschikbaar in de editor:

![&#x200B; de Redacteur van het Fragment van de Inhoud - Mijn Fragment &#x200B;](/help/journey-headless/author/assets/headless-journey-author-content-fragment-06.png)

>[!NOTE]
>
>U kunt uw fragment van of de **Assets** of **console van de Fragmenten van de Inhoud** ook publiceren.

## Volgende functies {#whats-next}

Nu u de grondbeginselen hebt geleerd, moet de volgende stap [&#x200B; leren hoe over Verwijzingen &#x200B;](references.md). Dit zal de diverse beschikbare verwijzingen introduceren en bespreken, en hoe te om niveaus van structuur met de Verwijzingen van het Fragment tot stand te brengen - een zeer belangrijk deel van creatie voor headless.

## Aanvullende bronnen {#additional-resources}

* [Concepten ontwerpen](/help/sites-cloud/authoring/author-publish.md)

* [&#x200B; Basis Behandelend &#x200B;](/help/sites-cloud/authoring/basic-handling.md) - deze pagina is hoofdzakelijk gebaseerd op de **console van Plaatsen**, maar vele/de meeste eigenschappen zijn ook relevant voor het ontwerpen van **Fragmenten van de Inhoud** onder de **Assets** console.

   * [Deelvenster Navigatie](/help/sites-cloud/authoring/basic-handling.md#navigation-panel)

   * [De koptekst](/help/sites-cloud/authoring/basic-handling.md#the-header)

   * [Werkbalk Handelingen](/help/sites-cloud/authoring/basic-handling.md#actions-toolbar)

   * [Snelle handelingen](/help/sites-cloud/authoring/basic-handling.md#quick-actions)

   * [Bronnen weergeven en selecteren](/help/sites-cloud/authoring/basic-handling.md#viewing-and-selecting-resources)

   * [Spoorwegkiezer](/help/sites-cloud/authoring/basic-handling.md#rail-selector)

* [Werken met inhoudsfragmenten](/help/sites-cloud/administering/content-fragments/overview.md)

   * [Inhoudsfragmenten beheren](/help/sites-cloud/administering/content-fragments/managing.md)

   * [De configuratie toepassen op uw Assets-map](/help/sites-cloud/administering/content-fragments/setup.md#apply-the-configuration-to-your-folder)

   * [Een inhoudsfragment maken](/help/sites-cloud/administering/content-fragments/managing.md#creating-a-content-fragment)

   * [Inhoudsfragmenten ontwerpen](/help/sites-cloud/administering/content-fragments/authoring.md)

   * Publiceren

      * Van de redacteur, of **Assets** console

         * [Snel publiceren](/help/assets/manage-publication.md#quick-publish)

         * [&#x200B; beheer Publicatie &#x200B;](/help/assets/manage-publication.md#manage-publication)

      * Van de **Console van de Fragmenten van de Inhoud**

         * [Een inhoudsfragment publiceren en voorvertonen](/help/sites-cloud/administering/content-fragments/managing.md#publishing-and-previewing-a-fragment)

   * [Modellen van inhoudsfragmenten](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md)

      * [Modellen van inhoudsfragmenten - gegevenstypen](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#data-types)

      * [Modellen van inhoudsfragmenten - eigenschappen](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#properties)

      * [Modellen van inhoudsfragmenten - Modellen van inhoudsfragmenten toestaan in uw Assets-map](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md#allowing-content-fragment-models-assets-folder)

* [Inhoudsfragmenten - oorspronkelijke editor, uit de Assets-console](/help/assets/content-fragments/content-fragments-variations.md)

* Aan de slag - hulplijnen
   * [Assets-instellingen voor mapkoppen maken](/help/headless/setup/create-assets-folder.md)

* AEM Headless Content Architect Reis

* AEM Headless Translation Reis
