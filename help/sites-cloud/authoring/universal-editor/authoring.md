---
title: Inhoud ontwerpen met de Universal Editor
description: Leer hoe gemakkelijk en intuïtief het is voor inhoudsauteurs om inhoud tot stand te brengen gebruikend de Universele Redacteur.
exl-id: 15fbf5bc-2e30-4ae7-9e7f-5891442228dd
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 3922375b52ae64d08cdc64d475a95e8bd240a587
workflow-type: tm+mt
source-wordcount: '1177'
ht-degree: 0%

---


# Inhoud ontwerpen met de Universal Editor {#authoring}

Leer hoe gemakkelijk en intuïtief het is voor inhoudsauteurs om inhoud tot stand te brengen gebruikend de Universele Redacteur.

## Inleiding {#introduction}

Met de Universal Editor kunt u elk aspect van elke inhoud in een implementatie bewerken, zodat u uitzonderlijke ervaringen kunt bieden, de snelheid van de inhoud kunt verhogen en een geavanceerde ontwikkelaarservaring kunt bieden.

Hiervoor verschaft de Universal Editor de auteur van inhoud een intuïtieve gebruikersinterface die minimale training vereist om eenvoudig in de inhoud te kunnen springen en beginnen met het bewerken ervan. In dit document wordt de auteurservaring van de Universal Editor beschreven.

>[!NOTE]
>
>In dit document wordt ervan uitgegaan dat u al vertrouwd bent met de toegang tot en navigatie in de Universal Editor. Als u niet bent, te zien gelieve het document [ dat tot de Universele Redacteur toegang heeft en navigeert.](/help/sites-cloud/authoring/universal-editor/navigation.md)

>[!TIP]
>
>Voor een meer gedetailleerde inleiding aan de Universele Redacteur, zie het document [ Universele Inleiding van de Redacteur.](/help/implementing/universal-editor/introduction.md)

## Inhoud bewerken {#editing-content}

Inhoud bewerken is eenvoudig en intuïtief. Terwijl u de muis over de inhoud in de editor beweegt, wordt bewerkbare inhoud gemarkeerd met een blauw vak.

![ Bewerkbare inhoud wordt benadrukt door een blauw vakje ](assets/editable-content.png)

>[!TIP]
>
>Door gebrek, selecteert het tikken of het klikken op inhoud het voor het uitgeven. Als u uw inhoud door verbindingen wilt navigeren, schakelaar aan [ voorproefwijze.](/help/sites-cloud/authoring/universal-editor/navigation.md#preview-mode)

Afhankelijk van de inhoud u selecteert, kunt u verschillende op zijn plaats het uitgeven opties hebben en u kunt extra informatie en opties voor de inhoud in het [ eigenschappen spoor.](/help/sites-cloud/authoring/universal-editor/navigation.md#properties-rail)

### Onbewerkte tekst bewerken {#edit-plain-text}

U kunt de tekst op zijn plaats bewerken door te dubbelklikken op de component of erop te dubbeltikken.

![ het Uitgeven inhoud ](assets/editing-content.png)

Druk op Enter/Return of selecteer buiten het tekstvak om uw wijzigingen op te slaan.

Wanneer u selecteert om de tekstcomponent te selecteren, worden zijn details getoond in het [ eigenschappen spoor.](/help/sites-cloud/authoring/universal-editor/navigation.md#properties-rail) U kunt de tekst ook in de rails bewerken.

![ het Uitgeven tekst in de eigenschappen spoorstaaf ](assets/ue-editing-text-component-rail.png)

De details van uw tekst zijn ook beschikbaar in de eigenschappen rail. Wijzigingen worden automatisch opgeslagen als de focus het bewerkte veld verlaat in de eigenschappenrails.

### RTF-tekst bewerken {#edit-rich-text}

U kunt de tekst op zijn plaats bewerken door te dubbelklikken op de component of erop te dubbeltikken.

![ Uitgevend een rijke tekstcomponent ](assets/rich-text-editing.png)

Voor uw gemak zijn opmaakopties en details op uw tekst beschikbaar op twee plaatsen.

* Het **contextmenu** opent boven het rijke tekstblok en biedt basishet formatteren opties in context aan. Vanwege ruimtebeperkingen kunnen sommige opties achter de knop voor ovaal worden verborgen.
* De **[eigenschappen spoorstaaf](/help/sites-cloud/authoring/universal-editor/navigation.md#properties-rail)** toont alle het formatteren opties beschikbaar samen met de tekst.

Wijzigingen worden automatisch opgeslagen als de focus het bewerkte veld verlaat.

### Media bewerken {#edit-media}

U kunt zijn details in het [ eigenschappen spoor bekijken.](/help/sites-cloud/authoring/universal-editor/navigation.md#properties-rail)

![ het Uitgeven media ](assets/ue-edit-media.png)

1. Tik of klik op de voorvertoning van de geselecteerde afbeelding in de eigenschappenbalk.
1. Het [ activa selecteur ](/help/assets/asset-selector.md#using-asset-selector) venster opent om u toe te staan om activa te selecteren.
1. Selecteer deze optie om een nieuw element te selecteren.
1. Selecteer **Uitgezochte** om aan eigenschappen spoor terug te keren waar de activa werd vervangen.

Wijzigingen worden automatisch in de inhoud opgeslagen.

### Inhoudsfragmenten bewerken {#edit-content-fragment}

Als u a [ het Fragment van de Inhoud selecteert, ](/help/sites-cloud/administering/content-fragments/overview.md) kunt u zijn details in het [ eigenschappen spoor uitgeven.](/help/sites-cloud/authoring/universal-editor/navigation.md#properties-rail)

![ Uitgevend een Fragment van de Inhoud ](assets/ue-edit-cf.png)

De velden die zijn gedefinieerd in het inhoudsmodel van het geselecteerde inhoudsfragment, worden weergegeven en kunnen worden bewerkt in de eigenschappenbalk.

Als u een veld selecteert dat verwant is aan een inhoudsfragment, wordt het inhoudsfragment in de componentrail geladen en wordt het veld automatisch naar het veld geschoven.

Wijzigingen worden automatisch opgeslagen als de focus het bewerkte veld verlaat in de eigenschappenrails.

Als u uw Fragment van de Inhoud in de [ redacteur van het Fragment van de Inhoud ](/help/sites-cloud/administering/content-fragments/authoring.md) in plaats daarvan wilt uitgeven, klik [ uitgeven knoop ](/help/sites-cloud/authoring/universal-editor/navigation.md#edit) in de eigenschappen spoorstaaf.

Afhankelijk van de behoeften van uw workflow wilt u het inhoudsfragment wellicht bewerken in de universele editor of rechtstreeks in de editor voor inhoudsfragmenten.

### Componenten toevoegen aan containers {#adding-components}

1. Selecteer een containercomponent in de [ inhoudsboom ](/help/sites-cloud/authoring/universal-editor/navigation.md#content-tree-mode) of in de redacteur.
1. Selecteer vervolgens het invoegpictogram in de eigenschappenrails.

   ![ Selecterend een component om aan een container ](assets/ue-add-component.png) toe te voegen

De component wordt opgenomen in de container en kan in de redacteur worden uitgegeven.

>[!TIP]
>
>Gebruik de sneltoets `A` om een component aan de geselecteerde container toe te voegen.

### Componenten uit containers verwijderen {#deleting-components}

1. Selecteer een containercomponent in de [ inhoudsboom ](/help/sites-cloud/authoring/universal-editor/navigation.md#content-tree-mode) of in de redacteur.
1. Selecteer het chevron-pictogram van de container om de inhoud ervan in de inhoudsstructuur uit te vouwen.
1. Selecteer vervolgens in de inhoudsstructuur een component in de container.
1. Selecteer het verwijderingspictogram in de eigenschappenrails.

   ![ Deleting a component ](assets/ue-delete-component.png)

De geselecteerde component is verwijderd.

>[!TIP]
>
>Gebruik de sneltoets `Shift+Backspace` om de geselecteerde component uit de container te verwijderen.

### Componenten opnieuw ordenen in containers {#reordering-components}

1. Als niet reeds op [ wijze van de inhoudsboom, ](/help/sites-cloud/authoring/universal-editor/navigation.md#content-tree-mode) schakelaar aan het.
1. Selecteer een containercomponent in de inhoudsstructuur of in de editor.
1. Selecteer het chevron-pictogram van de container om de inhoud ervan in de inhoudsstructuur uit te vouwen.
1. De greeppictogrammen van de belemmering naast de componenten binnen de container tonen dat u hen kunt herschikken. Sleep de componenten om deze binnen de container opnieuw te ordenen.

   ![ opnieuw rangschikt componenten ](assets/ue-reordering-components.png)

1. De gesleepte component wordt grijs in de inhoudsstructuur, terwijl de invoegpositie wordt aangeduid met een blauwe lijn. Laat de component los om deze op de nieuwe locatie te plaatsen.

De componenten worden opnieuw gerangschikt in zowel de inhoudsstructuur als de editor

## Inhoud voorvertonen {#previewing-content}

Wanneer u klaar bent met het bewerken van inhoud, wilt u er vaak door navigeren om te zien hoe de inhoud er op andere pagina&#39;s uitziet. Op [ voorproefwijze ](/help/sites-cloud/authoring/universal-editor/navigation.md#preview-mode) kunt u verbindingen klikken om uw inhoud te navigeren zoals een lezer. De inhoud wordt in de editor gerenderd zoals deze zou worden gepubliceerd.

In de voorvertoningsmodus reageert de gebruiker op de inhoud door erop te tikken of erop te klikken, net als bij een lezer van de inhoud. Als u de inhoud voor het uitgeven wilt selecteren, knevel uit [ voorproefwijze.](/help/sites-cloud/authoring/universal-editor/navigation.md#preview-mode)

## Aanvullende bronnen {#additional-resources}

Raadpleeg dit document voor meer informatie over het publiceren van inhoud met de universele editor.

* [ het Publiceren Inhoud met de Universele Redacteur ](publishing.md) - leer hoe de Universele Redacteur inhoud publiceert en hoe uw apps de gepubliceerde inhoud kunnen behandelen.

Zie deze ontwikkelaarsdocumenten voor meer informatie over de technische details van de Universal Editor.

* [ Universele Inleiding van de Redacteur ](/help/implementing/universal-editor/introduction.md) - Leer hoe de Universele Redacteur het uitgeven om het even welk aspect van om het even welke inhoud in om het even welke implementatie toelaat zodat kunt u uitzonderlijke ervaringen leveren, inhoudssnelheid verhogen, en een ervaring van de allernieuwste ontwikkelaar verstrekken.
* [ Begonnen het Worden met de Universele Redacteur in AEM ](/help/implementing/universal-editor/getting-started.md) - leer hoe te om toegang tot de Universele Redacteur te krijgen en hoe te beginnen van instrumenten voorzien uw eerste AEM app om het te gebruiken.
* [ Universele Architectuur van de Redacteur ](/help/implementing/universal-editor/architecture.md) - Leer over de architectuur van de Universele Redacteur en hoe de gegevens tussen zijn diensten en lagen stromen.
* [ Attributen en Types ](/help/implementing/universal-editor/attributes-types.md) - leer over de gegevensattributen en de types die de Universele Redacteur vereist.
* [ Universele Authentificatie van de Redacteur ](/help/implementing/universal-editor/authentication.md) - leer hoe de Universele Redacteur voor authentiek verklaart.

## Componentovererving bewerken {#inheritance}

Overerving is het mechanisme waarbij inhoud kan worden gekoppeld, zodat het ene element automatisch het andere verandert.

Met de Universal Editor kunt u overerving voor inhoud annuleren door de inhoud eenvoudig bij te werken. De redacteur maakt automatisch overerving voor alle veranderingen onbruikbaar die door auteurs op die pagina worden aangebracht, ervoor zorgen dat de gewijzigde inhoud wordt behouden wanneer de updates van de blauwdruk worden gesynchroniseerd.

Voor meer details op hoe de overerving het gebruiken van de Universele Redacteur werkt, te zien gelieve de overerving van de document [ Inhoud in de Universele Redacteur.](/help/sites-cloud/authoring/universal-editor/inheritance.md)
