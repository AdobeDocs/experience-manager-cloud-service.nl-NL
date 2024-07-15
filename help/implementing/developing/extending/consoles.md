---
title: Consoles aanpassen
description: Leer over de verschillende opties die AEM verstrekt om de consoles van uw auteursinstantie aan te passen.
exl-id: 832f9a86-07c4-4229-a0dc-8ad50a8195b0
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 0%

---

# Consoles aanpassen {#customizing-consoles}

AEM verstrekt opties om de consoles (en de [ pagina auteursfunctionaliteit ](/help/implementing/developing/extending/page-authoring.md)) van uw auteursinstantie aan te passen.

## Clientlibs {#clientlibs}

Clientlibs staan u toe om de standaardimplementatie uit te breiden om nieuwe functionaliteit aan te bieden, terwijl het hergebruiken van standaardfuncties, voorwerpen, en methodes. Wanneer u clientlibs aanpast, kunt u onder `/apps.` bijvoorbeeld uw eigen clientlib maken die de code bevat die is vereist voor uw aangepaste component.

Zie [ Gebruikend cliënt-Kant Bibliotheken op AEM as a Cloud Service ](/help/implementing/developing/introduction/clientlibs.md).

## Bedekkingen {#overlays}

Bedekkingen zijn gebaseerd op knooppuntdefinities en maken het mogelijk om de standaardfunctionaliteit onder `/libs` te bedekken met uw eigen aangepaste functionaliteit onder `/apps` . Wanneer het creëren van een bekleding, wordt een 1:1 exemplaar van origineel niet vereist, aangezien [ het Schuiven middelfusie ](/help/implementing/developing/introduction/sling-resource-merger.md) voor overerving toestaat.

Bedekkingen kunnen op verschillende manieren worden gebruikt om uw AEM uit te breiden. In de volgende secties worden verschillende voorbeelden gegeven.

Zie ook [ Bekledingen voor Adobe Experience Manager as a Cloud Service ](/help/implementing/developing/introduction/overlays.md).

>[!TIP]
>
>Als u in opties geinteresseerd bent om de auteurservaring aan te passen, zie [ Aanpassend de Authoring van de Pagina ](/help/implementing/developing/extending/page-authoring.md).

## De standaardweergave voor een console aanpassen {#customizing-the-default-view-for-a-console}

U kunt de standaardweergave (kolom, kaart, lijst) voor een console aanpassen:

* U kunt de volgorde van de weergaven wijzigen door de vereiste gegevens onder te plaatsen:

   * `/libs/wcm/core/content/sites/jcr:content/views`

   * De eerste vermelding is de standaardinstelling.

   * De beschikbare knooppunten zijn gerelateerd aan de beschikbare weergaveopties:

      * `column`
      * `card`
      * `list`

* Bijvoorbeeld in een overlay voor een lijst:

   * `/apps/wcm/core/content/sites/jcr:content/views/list`

   * Definieer de volgende eigenschap:

      * **Naam**: `sling:orderBefore`
      * **Type**: `String`
      * **Waarde**: `column`

### Een nieuwe handeling toevoegen aan de werkbalk {#add-a-new-action-to-the-toolbar}

U kunt uw eigen componenten bouwen en de overeenkomstige cliëntbibliotheken voor douaneacties omvatten.

* Bijvoorbeeld, kunt u a **willen tot stand brengen bevordert aan Sociale Media** actie bij:

   * `/apps/wcm/core/clientlibs/sites/js/socialmedia.js`

   * Dit kan dan met een toolbarpunt op uw console worden verbonden:

   * `/apps/<yourProject>/admin/ext/launches`

   * In de selectiemodus bijvoorbeeld:

   * `content/jcr:content/body/content/header/items/selection/items/socialmedia`

### Een werkbalkactie beperken tot een specifieke groep {#restrict-a-toolbar-action-to-a-specific-group}

U kunt een aangepaste rendervoorwaarde gebruiken om de standaardhandeling te bedekken en specifieke voorwaarden op te leggen waaraan moet worden voldaan voordat deze wordt gerenderd.

U kunt bijvoorbeeld een component maken om de rendervoorwaarden volgens een groep te beheren:

* `/apps/myapp/components/renderconditions/group`

Om deze op **toe te passen creeer de actie van de Plaats** op de plaatsenconsole:

* `/libs/wcm/core/content/sites`

1. Maak de bedekking:

   * `/apps/wcm/core/content/sites`

1. Voeg vervolgens de rendervoorwaarde voor de actie toe:

   * `jcr:content/body/content/header/items/default/items/create/items/createsite/rendercondition`

Met eigenschappen op dit knooppunt kunt u de handeling `groups` definiëren die de specifieke handeling mag uitvoeren, bijvoorbeeld `administrators`

### Kolommen aanpassen in de lijstweergave {#customizing-columns-in-list-view}

U kunt als volgt de kolommen in de lijstweergave aanpassen:

1. Bedek de lijst met beschikbare kolommen.

   * Op het knooppunt:

     `/apps/wcm/core/content/common/availablecolumns`

1. Voeg uw nieuwe kolommen toe of verwijder bestaande kolommen.

Als u extra gegevens wilt opnemen, moet u a [ PageInfoProvider ](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/PageInfoProvider.html) met a `pageInfoProviderType` bezit schrijven.

>[!NOTE]
>
>Deze functie is geoptimaliseerd voor kolommen met tekstvelden. Voor andere gegevenstypen is het mogelijk om `cq/gui/components/siteadmin/admin/listview/columns/analyticscolumnrenderer` in `/apps` te bedekken.

### Bronnen filteren {#filtering-resources}

Wanneer het gebruiken van een console, moet een gebruiker vaak uit middelen zoals pagina&#39;s, componenten, of activa selecteren. Dit kan de vorm hebben van een lijst waaruit de auteur een punt moet kiezen.

Om de lijst tot een redelijke grootte en ook relevant voor het gebruiksgeval te houden, kan een filter in de vorm van een douanevoorspelling worden uitgevoerd. Zie [ het Aanpassen van de Authoring van de Pagina ](/help/implementing/developing/extending/page-authoring.md#filtering-resources) voor details.
