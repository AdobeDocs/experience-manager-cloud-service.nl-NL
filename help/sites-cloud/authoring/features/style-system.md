---
title: Stijlsysteem
description: Met het Stijlsysteem kan een sjabloonauteur stijlklassen definiëren in het inhoudsbeleid van een component, zodat de auteur van de inhoud deze kan selecteren wanneer hij de component op een pagina bewerkt. Deze stijlen kunnen alternatieve visuele variaties van een component zijn, waardoor het flexibeler wordt.
exl-id: 224928dd-e365-4f3e-91af-4d8d9f47efdd
source-git-commit: 0ad9f349c997c35862e4f571b4741ed4c0c947e2
workflow-type: tm+mt
source-wordcount: '1305'
ht-degree: 0%

---

# Stijlsysteem{#style-system}

Met het Stijlsysteem kan een sjabloonauteur stijlklassen definiëren in het inhoudsbeleid van een component, zodat de auteur van de inhoud deze kan selecteren wanneer hij de component op een pagina bewerkt. Deze stijlen kunnen alternatieve visuele variaties van een component zijn, waardoor de component flexibeler wordt.

Dit elimineert de behoefte om een douanecomponent voor elke stijl te ontwikkelen of het componentendialoogvenster aan te passen om dergelijke stijlfunctionaliteit toe te laten. Het leidt tot herbruikbaardere componenten die snel en gemakkelijk aan de behoeften van inhoudsauteurs zonder enige AEM achterwaartse ontwikkeling kunnen worden aangepast.

## Hoofdletters gebruiken {#use-case}

De auteurs van het malplaatje vergen niet alleen de capaciteit om te vormen hoe de componenten voor de inhoudsauteurs functioneren, maar ook om verscheidene alternatieve visuele variaties van een component te vormen.

Op dezelfde manier hebben inhoudsauteurs niet alleen de mogelijkheid nodig om de inhoud te structureren en te rangschikken, maar ook om te selecteren hoe de inhoud visueel wordt weergegeven.

Het systeem van de Stijl verstrekt een verenigde oplossing aan zowel de vereisten van de malplaatjeauteur als van de inhoudauteur:

* Sjabloonauteurs kunnen stijlklassen definiëren in het inhoudsbeleid van componenten.
* Inhoudsauteurs kunnen deze klassen vervolgens selecteren in een vervolgkeuzelijst wanneer ze de component op een pagina bewerken, zodat ze de bijbehorende stijlen kunnen toepassen.

De stijlklasse wordt dan opgenomen op het decoratie omslagelement van de component zodat de componentenontwikkelaar zich niet met de behandeling van de stijlen hoeft bezig te houden voorbij het verstrekken van hun CSS regels.

## Overzicht {#overview}

Het gebruik van het Stijlsysteem heeft doorgaans de volgende vorm.

1. De webontwerper maakt verschillende visuele variaties van een component.

1. De ontwikkelaar van HTML wordt voorzien van de HTML output van de componenten en de gewenste visuele variaties om uit te voeren.

1. De ontwikkelaar van HTML bepaalt de CSS klassen die aan elke visuele variatie beantwoorden en op het element moeten worden opgenomen die de componenten verpakt.

1. De HTML-ontwikkelaar implementeert de bijbehorende CSS-code (en eventueel JS-code) voor elk van de visuele variaties, zodat deze er zo uitzien als gedefinieerd.

1. De AEM ontwikkelaar plaatst de meegeleverde CSS (en optionele JS) in een [Clientbibliotheek](/help/implementing/developing/introduction/clientlibs.md) en implementeert.

1. De AEM ontwikkelaar of sjabloonauteur configureert de paginasjablonen en bewerkt het beleid van elke opgemaakte component, voegt de gedefinieerde CSS-klassen toe, geeft gebruikersvriendelijke namen aan elke stijl en geeft aan welke stijlen kunnen worden gecombineerd.

1. De auteur van de AEM pagina kan vervolgens de ontworpen stijlen in de pagina-editor kiezen via het stijlmenu van de werkbalk van de component.

Alleen de laatste drie stappen worden daadwerkelijk in AEM uitgevoerd. Dit betekent dat alle ontwikkeling van de vereiste CSS en JavaScript zonder AEM kan worden uitgevoerd.

Voor een feitelijke implementatie van de stijlen is alleen implementatie op AEM en selectie binnen de componenten van de gewenste sjablonen vereist.

Het volgende diagram illustreert de architectuur van het Systeem van de Stijl.

![aem-stijl-systeem](/help/sites-cloud/authoring/assets/style-system-architecture.png)

## Gebruiken {#use}

Om de functie te demonstreren, gebruiken we [WKND](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)implementatie van de kerncomponent [titelcomponent](https://www.adobe.com/go/aem_cmp_title_v2) als voorbeeld.

De volgende secties [Als inhoudsauteur](#as-a-content-author) en [Als sjabloonauteur](#as-a-template-author) beschrijf hoe te om de functionaliteit van het Systeem van de Stijl te testen gebruikend het Systeem van de Stijl van WKND.

Ga als volgt te werk als u het Stijlsysteem voor uw eigen componenten wilt gebruiken:

1. CSS installeren als clientbibliotheken zoals beschreven in de sectie [Overzicht](#overview).
1. CSS-klassen configureren die u beschikbaar wilt maken voor de auteurs van de inhoud, zoals wordt beschreven in de sectie [Als sjabloonauteur](#as-a-template-author).
1. Inhoudsauteurs kunnen vervolgens de stijlen gebruiken zoals beschreven in de sectie [Als inhoudsauteur](#as-a-content-author).

### Als inhoudsauteur {#as-a-content-author}

1. Na het installeren van het WKND-project navigeert u naar de hoofdpagina voor de Engelse taal van WKND op `http://<host>:<port>/sites.html/content/wknd/language-masters/en` en bewerkt u de pagina.
1. Selecteer een **Titel** component verder omlaag op de pagina

   ![Stijlsysteem voor de auteur](/help/sites-cloud/authoring/assets/style-system-author1.png)

1. Selecteer de **Stijlen** op de werkbalk van de **Lijst** om het stijlmenu te openen en de weergave van de component te wijzigen.

   ![Stijlen selecteren](/help/sites-cloud/authoring/assets/style-system-author2.png)

   >[!NOTE]
   >
   >In dit voorbeeld wordt **Kleuren** stijlen (**Zwart**, **Wit**, en **Grijs**) elkaar uitsluiten, terwijl de **Stijl** opties (**Onderstrepen**, **Rechts uitlijnen**, en **Mini-spatiëring**) kan worden gecombineerd. Dit kan [in de sjabloon worden geconfigureerd als sjabloonauteur](#as-a-template-author).

### Als sjabloonauteur {#as-a-template-author}

1. Tijdens het bewerken van de hoofdpagina voor de Engelse taal van WKND op `http://<host>:<port>/sites.html/content/wknd/language-masters/en`, bewerkt u de sjabloon van de pagina via **Paginagegevens > Sjabloon bewerken**.

   ![Sjabloon bewerken](/help/sites-cloud/authoring/assets/style-system-edit-template.png)

1. Het beleid van de **Titel** component door te tikken of op de component te klikken **Beleid** van de component.

   ![Beleid bewerken](/help/sites-cloud/authoring/assets/style-system-edit-policy.png)

1. Op het tabblad Stijlen van de eigenschappen kunt u zien hoe de stijlen zijn geconfigureerd.

   ![Eigenschappen bewerken](/help/sites-cloud/authoring/assets/style-system-properties.png)

   * **Groepsnaam:** Stijlen kunnen worden gegroepeerd in het stijlmenu dat de auteur van de inhoud ziet bij het configureren van de stijl van de component.
   * **Stijlen kunnen worden gecombineerd:** Hiermee kunt u meerdere stijlen in die groep tegelijk selecteren.
   * **Stijlnaam:** De beschrijving van de stijl die aan de inhoudsauteur wanneer het vormen van de stijl van de component zal tonen.
   * **CSS-klassen:** De werkelijke naam van de CSS-klasse die aan de stijl is gekoppeld.

   Gebruik de sleephandgrepen om de volgorde van de groepen en de stijlen in de groepen te bepalen. Met de pictogrammen Toevoegen of Verwijderen kunt u groepen of stijlen in de groepen toevoegen of verwijderen.

>[!CAUTION]
>
>De CSS-klassen - en eventueel noodzakelijke JavaScript - die zijn geconfigureerd als stijleigenschappen van het beleid van een component, moeten worden geïmplementeerd als [Clientbibliotheken](/help/implementing/developing/introduction/clientlibs.md) om te werken.

## Instellen {#setup}

Versie 2 en later van de Componenten van de kern wordt volledig toegelaten om uit het Systeem van de Stijl voordeel te halen en geen extra configuratie te vereisen.

De volgende stappen zijn alleen nodig om het Stijlsysteem in te schakelen voor uw eigen aangepaste componenten of om [Schakel het tabblad Optionele stijlen in het dialoogvenster Bewerken in.](#enable-styles-tab-edit)

### Het tabblad Stijl in het dialoogvenster Ontwerpen inschakelen {#enable-styles-tab-design}

Een component werkt alleen met AEM stijlsysteem en geeft het stijltabblad weer in het dialoogvenster Ontwerp, als de ontwikkelaar van de component het tabblad Stijl met de volgende instellingen in de component heeft:

* `path = "/mnt/overlay/cq/gui/components/authoring/dialog/style/tab_design/styletab"`
* `sling:resourceType = "granite/ui/components/coral/foundation/include"`

>[!NOTE]
>Dit gebruikt [bedekkingen](/help/implementing/developing/introduction/overlays.md)door de [Samenvoeging van verkoopbronnen](/help/implementing/developing/introduction/sling-resource-merger.md).

Met de gevormde component, worden de stijlen die door de paginaauteurs worden gevormd automatisch opgenomen door AEM op het decoratie element dat AEM automatisch rond elke editable component verpakt. De component zelf hoeft niets anders te doen om dit te bewerkstelligen.

### Het tabblad Stijlen inschakelen in het dialoogvenster Bewerken {#enable-styles-tab-edit}

Er is ook een optioneel tabblad Stijlen beschikbaar in het dialoogvenster Bewerken. In tegenstelling tot het tabblad Ontwerpdialoogvenster is het tabblad in het dialoogvenster Bewerken niet essentieel voor het functioneren van het Stijlsysteem, maar is het een optionele alternatieve interface voor de auteur van inhoud om stijlen in te stellen.

Het tabblad Bewerken kan op vergelijkbare wijze worden opgenomen als het tabblad van het dialoogvenster Ontwerpen:

* `path = "/mnt/overlay/cq/gui/components/authoring/dialog/style/tab_edit/styletab"`
* `sling:resourceType = "granite/ui/components/coral/foundation/include"`

>[!NOTE]
>Dit gebruikt [bedekkingen](/help/implementing/developing/introduction/overlays.md)door de [Samenvoeging van verkoopbronnen](/help/implementing/developing/introduction/sling-resource-merger.md).

>[!NOTE]
>
>Het tabblad Stijlen in het dialoogvenster Bewerken is niet standaard ingeschakeld.

### Stijlen met elementnamen {#styles-with-element-names}

Een ontwikkelaar kan ook een lijst met toegestane elementnamen voor stijlen op de component configureren met de `cq:styleElements` array-eigenschap string. Vervolgens kan de sjabloonauteur op het tabblad Stijlen van het beleid in het ontwerpdialoogvenster ook een elementnaam kiezen die voor elke stijl moet worden ingesteld. Hiermee wordt de elementnaam van het omvattende element ingesteld.

Deze eigenschap is ingesteld op het tabblad `cq:Component` knooppunt. Bijvoorbeeld:

* `/apps/<yoursite>/components/content/list@cq:styleElements=[div,section,span]`

>[!CAUTION]
>
>Definieer geen elementnamen voor stijlen die kunnen worden gecombineerd. Wanneer de veelvoudige elementnamen worden bepaald, is de orde van prioriteit:
>
>1. HTML heeft voorrang op alles: `data-sly-resource="${'path/to/resource' @ decorationTagName='span'}`
>1. Dan onder veelvoudige actieve stijlen, wordt de eerste stijl in de lijst van stijlen die in het beleid van de component worden gevormd genomen.
>1. Tot slot de componenten `cq:htmlTag`/ `cq:tagName` wordt beschouwd als een terugvalwaarde.
>

Deze mogelijkheid om stijlnamen te definiëren is handig voor algemene componenten, zoals de container van de layout of de component Content Fragment, zodat ze een extra betekenis krijgen.

Zo kan een container voor lay-out bijvoorbeeld semantiek krijgen `<main>`, `<aside>`, `<nav>`, enzovoort.
