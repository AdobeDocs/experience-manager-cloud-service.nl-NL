---
title: Een site maken
description: Leer hoe u AEM kunt gebruiken om een site te maken met behulp van sitesjablonen om de stijl en structuur van uw site te definiëren.
feature: Administering
role: Admin
exl-id: 9c71c167-2934-4210-abd9-ab085b36593b
solution: Experience Manager Sites
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 0%

---

# Een site maken {#creating-site}

Leer hoe u een site kunt gebruiken AEM maken met sitesjablonen om de stijl en structuur van uw site te definiëren.

## Overzicht {#overview}

Voordat auteurs van inhoud pagina&#39;s met inhoud kunnen maken, moet de site eerst worden gemaakt. Dit wordt over het algemeen uitgevoerd door een AEM beheerder die de aanvankelijke structuur van de plaats bepaalt. Door het gebruik van sitesjablonen kunt u snel en flexibel sites maken.

Met het gereedschap AEM Snel site maken kunnen niet-ontwikkelaars snel een geheel nieuwe site maken met behulp van sitesjablonen.

Nadat u de site hebt gemaakt, kunt u met het gereedschap Snel site maken het thema en de opmaak van de AEM site (JavaScript, CSS en statische bronnen) snel aanpassen. Hierdoor kan de front-end ontwikkelaar, die geen kennis van AEM nodig heeft, onafhankelijk van en parallel met de makers van de inhoud werken. De AEM beheerder downloadt eenvoudig het plaatsthema en verstrekt het aan de front-end ontwikkelaar die het gebruikend hun favoriete hulpmiddelen aanpast en dan de veranderingen in de AEM codebewaarplaats vastlegt, die dan wordt opgesteld.

Dit document richt zich op het maken van sites met het gereedschap Snel site maken. Als u een overzicht van het de plaatsverwezenlijking en aanpassingswerkschema zou willen, zie [ AEM Snelle Reis van de Aanmaak van de Plaats ](/help/journey-sites/quick-site/overview.md)

## Sitestructuur plannen {#structure}

Neem de tijd om ruim van tevoren rekening te houden met het doel en de geplande inhoud van uw site. Zo kunt u de structuur van de site ontwerpen. Een goede plaatsstructuur steunt gemakkelijke navigatie en inhoudsontdekking voor uw plaatsbezoekers en steunt diverse AEM eigenschappen zoals [ beheer en vertaling van meerdere plaatsen ](/help/sites-cloud/administering/msm-and-translation.md).

>[!TIP]
>
>[ de WKND verwijzingsplaats ](https://wknd.site) verstrekt een best-praktijkimplementatie van een volledig functionele buitenervaringswebsite. Ontdek het om te zien hoe een goed gebouwde AEM site gestructureerd is.

## Sitesjablonen {#site-templates}

Omdat de sitestructuur zo belangrijk is voor het succes van een site, is het handig om vooraf gedefinieerde structuren beschikbaar te hebben om snel een nieuwe site te implementeren op basis van een set bestaande standaarden. Sitesjablonen zijn een manier om basissite-inhoud te combineren tot een handig en herbruikbaar pakket.

Sitesjablonen bevatten over het algemeen inhoud en structuur van de basissite en informatie over de siteopmaak om snel met de nieuwe site aan de slag te kunnen gaan. Sjablonen zijn krachtig omdat ze opnieuw kunnen worden gebruikt en aanpasbaar zijn. En aangezien u veelvoudige malplaatjes beschikbaar in uw AEM installatie kunt hebben, hebt u de flexibiliteit om verschillende plaatsen tot stand te brengen om aan diverse bedrijfsbehoeften te voldoen.

>[!TIP]
>
>Voor verder detail op plaatsmalplaatjes, zie {de Malplaatjes van 0} Plaats ](site-templates.md).[

>[!NOTE]
>
>De sitesjabloon mag niet worden verward met paginasjablonen. Sitesjablonen definiëren de algehele structuur van een site. Een paginasjabloon definieert de structuur en initiële inhoud van een afzonderlijke pagina.

## Een site maken {#create-site}

Het is eenvoudig om een site te maken met een sjabloon.

1. Onderteken in uw AEM ontwerpomgeving en navigeer naar de Sites-console

   * `https://<your-author-environment>.adobeaemcloud.com/sites.html/content`

1. Selecteer **creeer** bij het hoogste recht van het scherm en van het drop-down menu uitgezocht **Plaats van malplaatje**.

   ![ Creërend een plaats van een malplaatje ](../assets/create-site-from-template.png)

1. In de Create tovenaar van de Plaats, selecteer een bestaand malplaatje in het linkerpaneel of op **de Invoer** bij de bovenkant van de linkerkolom om een nieuw malplaatje in te voeren.

   ![ tovenaar van de creatie van de Plaats ](../assets/site-creation-wizard.png)

   1. Als u verkoos om, in dossierbrowser in te voeren, bepaal de plaats van het malplaatje u **gebruiken en wilt selecteren uploadt**.

   1. Zodra het geüpload, verschijnt het in de lijst van beschikbare malplaatjes.

1. Als u een sjabloon selecteert, wordt informatie over de sjabloon in de rechterkolom weergegeven. Met uw gewenste geselecteerde malplaatje, uitgezochte **Volgende**.

   ![ selecteer een malplaatje ](../assets/select-site-template.png)

1. Geef een titel op voor uw site. U kunt een sitenaam opgeven of genereren op basis van de titel als u deze weglaat.

   * De titel van de site wordt weergegeven in de titelbalk van browsers.
   * De sitenaam wordt onderdeel van de URL.
   * De plaatsnaam moet [ AEM pagina het noemen overeenkomsten ](/help/sites-cloud/authoring/sites-console/organizing-pages.md#page-name-restrictions-and-best-practices) naleven.

1. Selecteer **creeer** en de plaats wordt gecreeerd van het plaatssjabloon.

   ![ Details van de nieuwe plaats ](../assets/create-site-details.png)

1. In de bevestigingsdialoog die verschijnt, uitgezocht **Gedaan**.

   ![ de dialoog van het Succes ](../assets/success.png)

1. In de plaatsenconsole, is de nieuwe plaats zichtbaar en kan worden genavigeerd om zijn basisstructuur te onderzoeken zoals die door het malplaatje wordt bepaald.

   ![ Nieuwe plaatsstructuur ](../assets/new-site.png)

Inhoudsauteurs kunnen nu beginnen met ontwerpen!

## Aanpassing van site {#site-customization}

Als voor uw site aanpassingen nodig zijn die verder gaan dan de sjablonen die beschikbaar zijn, hebt u verschillende opties.

* Als de plaatsstructuur of de aanvankelijke inhoud moet worden aangepast, [ kan het plaatsmalplaatje worden aangepast om aan uw vereisten ](site-templates.md) te voldoen.
* Als de plaats het stileren moet worden aangepast, [ kan het plaatsthema worden gedownload en worden aangepast ](/help/journey-sites/quick-site/overview.md).
* Als de plaatsfunctionaliteit moet worden aangepast, [ kan de plaats volledig worden aangepast ](/help/implementing/developing/introduction/develop-wknd-tutorial.md).

Elke aanpassing moet plaatsvinden met de steun van een ontwikkelingsteam.
