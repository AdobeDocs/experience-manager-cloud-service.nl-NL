---
title: Stijlsysteem
description: Met het Stijlsysteem kan een sjabloonauteur stijlklassen definiëren in het inhoudsbeleid van een component, zodat de auteur van de inhoud deze kan selecteren wanneer hij de component op een pagina bewerkt. Deze stijlen kunnen alternatieve visuele variaties van een component zijn, waardoor het flexibeler wordt.
exl-id: 224928dd-e365-4f3e-91af-4d8d9f47efdd
source-git-commit: 856266faf4cb99056b1763383d611e9b2c3c13ea
workflow-type: tm+mt
source-wordcount: '1327'
ht-degree: 1%

---

# Stijlsysteem{#style-system}

Met het Stijlsysteem kan een sjabloonauteur stijlklassen definiëren in het inhoudsbeleid van een component, zodat de auteur van de inhoud deze kan selecteren wanneer hij de component op een pagina bewerkt. Deze stijlen kunnen alternatieve visuele variaties van een component zijn, waardoor de component flexibeler wordt.

Dit elimineert de behoefte om een douanecomponent voor elke stijl te ontwikkelen of het componentendialoogvenster aan te passen om dergelijke stijlfunctionaliteit toe te laten. Het leidt tot herbruikbaardere componenten die snel en gemakkelijk aan de behoeften van inhoudsauteurs zonder enige AEM achterwaartse ontwikkeling kunnen worden aangepast.

## Hoofdlettergebruik {#use-case}

De auteurs van het malplaatje vergen niet alleen de capaciteit om te vormen hoe de componenten voor de inhoudsauteurs functioneren, maar ook om een aantal alternatieve visuele variaties van een component te vormen.

Op dezelfde manier hebben inhoudsauteurs niet alleen de mogelijkheid nodig om de inhoud te structureren en te rangschikken, maar ook om te selecteren hoe de inhoud visueel wordt weergegeven.

Het systeem van de Stijl verstrekt een verenigde oplossing aan zowel de vereisten van de malplaatjeauteur als van de inhoudauteur:

* Sjabloonauteurs kunnen stijlklassen definiëren in het inhoudsbeleid van componenten.
* Inhoudsauteurs kunnen deze klassen vervolgens selecteren in een vervolgkeuzelijst wanneer ze de component op een pagina bewerken om de bijbehorende stijlen toe te passen.

De stijlklasse wordt dan opgenomen op het decoratie omslagelement van de component zodat de componentenontwikkelaar zich niet met de behandeling van de stijlen moet bezighouden voorbij het verstrekken van hun CSS regels.

## Overzicht {#overview}

Het gebruik van het Stijlsysteem heeft doorgaans de volgende vorm.

1. De webontwerper maakt verschillende visuele variaties van een component.

1. De HTML-ontwikkelaar krijgt de HTML-uitvoer van de componenten en de gewenste visuele variaties die u wilt implementeren.

1. De HTML-ontwikkelaar definieert de CSS-klassen die overeenkomen met elke visuele variatie en die moeten worden ingevoegd op het element dat de componenten omvat.

1. De HTML-ontwikkelaar implementeert de bijbehorende CSS-code (en eventueel JS-code) voor elk van de visuele variaties, zodat deze er zo uitzien als gedefinieerd.

1. De AEM ontwikkelaar plaatst de meegeleverde CSS (en optionele JS) in een [Clientbibliotheek](/help/implementing/developing/introduction/clientlibs.md) en implementeert deze.

1. De AEM ontwikkelaar of sjabloonauteur configureert de paginasjablonen en bewerkt het beleid van elke opgemaakte component, voegt de gedefinieerde CSS-klassen toe, geeft gebruikersvriendelijke namen aan elke stijl en geeft aan welke stijlen kunnen worden gecombineerd.

1. De auteur van de AEM pagina kan vervolgens de ontworpen stijlen in de pagina-editor kiezen via het stijlmenu van de werkbalk van de component.

Merk op dat slechts de laatste drie stappen daadwerkelijk in AEM worden uitgevoerd. Dit betekent dat alle ontwikkeling van de vereiste CSS en Javascript zonder AEM kan worden uitgevoerd.

Voor een feitelijke implementatie van de stijlen is alleen implementatie op AEM en selectie binnen de componenten van de gewenste sjablonen vereist.

Het volgende diagram illustreert de architectuur van het Systeem van de Stijl.

![aem-stijl-systeem](/help/sites-cloud/authoring/assets/style-system-architecture.png)

## Gebruiken {#use}

Om de eigenschap aan te tonen, zullen wij [WKND](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html) implementatie van de component [title ](https://www.adobe.com/go/aem_cmp_title_v2) als voorbeeld gebruiken.

De volgende secties [Als Inhoudsauteur](#as-a-content-author) en [Als Sjabloonauteur](#as-a-template-author) beschrijven hoe te om de functionaliteit van het Stijlsysteem te testen gebruikend het Systeem van de Stijl van WKND.

Ga als volgt te werk als u het Stijlsysteem voor uw eigen componenten wilt gebruiken:

1. Installeer de CSS als cliëntbibliotheken zoals die in de sectie [Overzicht](#overview) worden besproken.
1. Configureer de CSS-klassen die u beschikbaar wilt maken voor de auteurs van de inhoud, zoals beschreven in de sectie [Als sjabloonauteur](#as-a-template-author).
1. Inhoudsauteurs kunnen vervolgens de stijlen gebruiken zoals beschreven in de sectie [Als inhoudsauteur](#as-a-content-author).

### Als inhoudsauteur {#as-a-content-author}

1. Nadat u het WKND-project hebt geïnstalleerd, navigeert u naar de master introductiepagina van de Engelse taal van WKND op `http://<host>:<port>/sites.html/content/wknd/language-masters/en` en bewerkt u de pagina.
1. Selecteer een **Title**-component verder naar beneden op de pagina

   ![Stijlsysteem voor de auteur](/help/sites-cloud/authoring/assets/style-system-author1.png)

1. Tik of klik op de knop **Stijlen** op de werkbalk van de component **List** om het stijlmenu te openen en de weergave van de component te wijzigen.

   ![Stijlen selecteren](/help/sites-cloud/authoring/assets/style-system-author2.png)

   >[!NOTE]
   >
   >In dit voorbeeld sluiten de **Kleuren** stijlen (**Zwart**, **Wit** en **Grijs**) elkaar uit, terwijl de **Stijl** opties (**Onderstrepen**, &lt;a1 2/>Rechts uitlijnen **en** Mini-afstand **) kunnen worden gecombineerd.** Dit kan [in de sjabloon worden geconfigureerd als sjabloonauteur](#as-a-template-author).

### Als sjabloonauteur {#as-a-template-author}

1. Bewerk tijdens het bewerken van de master introductiepagina van de Engelse taal van WKND op `http://<host>:<port>/sites.html/content/wknd/language-masters/en` de sjabloon van de pagina via **Paginagegevens -> Sjabloon bewerken**.

   ![Sjabloon bewerken](/help/sites-cloud/authoring/assets/style-system-edit-template.png)

1. Bewerk het beleid van de component **Title** door te tikken op de knop **Policy** van de component of erop te klikken.

   ![Beleid bewerken](/help/sites-cloud/authoring/assets/style-system-edit-policy.png)

1. Op het tabblad Stijlen van de eigenschappen kunt u zien hoe de stijlen zijn geconfigureerd.

   ![Eigenschappen bewerken](/help/sites-cloud/authoring/assets/style-system-properties.png)

   * **Groepsnaam:** Stijlen kunnen worden gegroepeerd in het stijlmenu dat de auteur van de inhoud ziet bij het configureren van de stijl van de component.
   * **Stijlen kunnen worden gecombineerd:** Hiermee kunt u meerdere stijlen in die groep tegelijk selecteren.
   * **Stijlnaam:** de beschrijving van de stijl die bij het configureren van de stijl van de component wordt weergegeven aan de auteur van de inhoud.
   * **CSS-klassen:** de werkelijke naam van de CSS-klasse die aan de stijl is gekoppeld.

   Gebruik de sleephandgrepen om de volgorde van de groepen en de stijlen in de groepen te bepalen. Met de pictogrammen Toevoegen of Verwijderen kunt u groepen of stijlen in de groepen toevoegen of verwijderen.

>[!CAUTION]
>
>De CSS klassen (evenals om het even welk noodzakelijk Javascript) die als stijleigenschappen van het beleid van een component worden gevormd moeten als [Bibliotheken van de Cliënt ](/help/implementing/developing/introduction/clientlibs.md) worden opgesteld om te werken.

## Instellen {#setup}

Versie 2 en later van de Componenten van de kern wordt volledig toegelaten om uit het Systeem van de Stijl voordeel te halen en geen extra configuratie te vereisen.

De volgende stappen zijn alleen nodig om het Stijlsysteem in te schakelen voor uw eigen aangepaste componenten of om het tabblad Optionele stijlen in het dialoogvenster Bewerken in te schakelen.](#enable-styles-tab-edit)[

### Het tabblad Stijl in het dialoogvenster Ontwerpen inschakelen {#enable-styles-tab-design}

Een component werkt alleen met AEM Stijlsysteem en geeft het stijltabblad weer in het ontwerpdialoogvenster als de ontwikkelaar van de component het tabblad Stijl met de volgende instellingen in de component heeft opgenomen:

* `path = "/mnt/overlay/cq/gui/components/authoring/dialog/style/tab_design/styletab"`
* `sling:resourceType = "granite/ui/components/coral/foundation/include"`

>[!NOTE]
>Dit gebruikt [overlays](/help/implementing/developing/introduction/overlays.md), door middel van [Sling Resource Merger](/help/implementing/developing/introduction/sling-resource-merger.md).

Met de gevormde component, zullen de stijlen die door de paginaauteurs worden gevormd automatisch door AEM op het decoratie element worden opgenomen dat AEM automatisch rond elke editable component verpakt. De component zelf hoeft niets anders te doen om dit te bewerkstelligen.

### Tabblad Stijlen inschakelen in dialoogvenster Bewerken {#enable-styles-tab-edit}

Er is ook een optioneel tabblad Stijlen beschikbaar in het dialoogvenster Bewerken. In tegenstelling tot het tabblad Ontwerpdialoogvenster is het tabblad in het dialoogvenster Bewerken niet essentieel voor het functioneren van het Stijlsysteem, maar is het een optionele alternatieve interface voor de auteur van inhoud om stijlen in te stellen.

Het tabblad Bewerken kan op vergelijkbare wijze worden opgenomen als het tabblad van het dialoogvenster Ontwerpen:

* `path = "/mnt/overlay/cq/gui/components/authoring/dialog/style/tab_edit/styletab"`
* `sling:resourceType = "granite/ui/components/coral/foundation/include"`

>[!NOTE]
>Dit gebruikt [overlays](/help/implementing/developing/introduction/overlays.md), door middel van [Sling Resource Merger](/help/implementing/developing/introduction/sling-resource-merger.md).

>[!NOTE]
>
>Het tabblad Stijlen in het dialoogvenster Bewerken is niet standaard ingeschakeld.

### Stijlen met elementnamen {#styles-with-element-names}

Een ontwikkelaar kan ook een lijst met toegestane elementnamen voor stijlen op de component configureren met de reeksarray-eigenschap `cq:styleElements`. Vervolgens kan de sjabloonauteur op het tabblad Stijlen van het beleid in het ontwerpdialoogvenster ook een elementnaam kiezen die voor elke stijl moet worden ingesteld. Hiermee wordt de elementnaam van het omvattende element ingesteld.

Deze eigenschap wordt ingesteld op het knooppunt `cq:Component`. Bijvoorbeeld:

* `/apps/<yoursite>/components/content/list@cq:styleElements=[div,section,span]`

>[!CAUTION]
>
>Definieer geen elementnamen voor stijlen die kunnen worden gecombineerd. Wanneer meerdere elementnamen zijn gedefinieerd, is de volgorde van prioriteit:
>
>1. HTML heeft voorrang op alles: `data-sly-resource="${'path/to/resource' @ decorationTagName='span'}`
>1. Dan onder veelvoudige actieve stijlen, wordt de eerste stijl in de lijst van stijlen die in het beleid van de component worden gevormd genomen.
>1. Ten slotte wordt de `cq:htmlTag`/ `cq:tagName` van de component beschouwd als een terugvalwaarde.

>



Deze mogelijkheid om stijlnamen te definiëren is handig voor zeer algemene componenten, zoals de container van de layout of de component Content Fragment, zodat ze een extra betekenis krijgen.

Zo kan een container voor lay-out bijvoorbeeld semantiek als `<main>`, `<aside>`, `<nav>` enzovoort krijgen.
