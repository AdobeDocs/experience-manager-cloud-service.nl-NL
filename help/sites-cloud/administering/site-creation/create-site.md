---
title: Een site maken
description: Leer hoe u met AEM een site kunt maken met sitesjablonen om de stijl en structuur van uw site te definiëren.
feature: Administering
role: Admin
exl-id: 9c71c167-2934-4210-abd9-ab085b36593b
solution: Experience Manager Sites
source-git-commit: 4d45e7ef626ad0b46f5323263cca791b14f9732f
workflow-type: tm+mt
source-wordcount: '726'
ht-degree: 0%

---


# Een site maken {#creating-site}

Leer hoe u met AEM een site kunt maken met sitesjablonen om de stijl en structuur van uw site te definiëren.

## Overzicht {#overview}

Voordat auteurs van inhoud pagina&#39;s met inhoud kunnen maken, moet de site eerst worden gemaakt. Dit wordt over het algemeen uitgevoerd door een beheerder van AEM die de aanvankelijke structuur van de plaats bepaalt. Door sitesjablonen te gebruiken, kunt u sites snel en flexibel maken voor niet-ontwikkelaars.

## Sitestructuur plannen {#structure}

Neem de tijd om ruim van tevoren rekening te houden met het doel en de geplande inhoud van uw site. Zo kunt u de structuur van de site ontwerpen. Een goede plaatsstructuur steunt gemakkelijke navigatie en inhoudsontdekking voor uw plaatsbezoekers en steunt diverse eigenschappen van AEM zoals [ multisite beheer en vertaling.](/help/sites-cloud/administering/msm-and-translation.md)

## Sitesjablonen {#site-templates}

Omdat de sitestructuur zo belangrijk is voor het succes van een site, is het handig om vooraf gedefinieerde structuren beschikbaar te hebben om snel een nieuwe site te implementeren op basis van een set bestaande standaarden. Sitesjablonen zijn een manier om basissite-inhoud te combineren tot een handig en herbruikbaar pakket.

Sitesjablonen bevatten over het algemeen inhoud en structuur van de basissite en informatie over de siteopmaak om snel met de nieuwe site aan de slag te kunnen gaan. Sjablonen zijn krachtig omdat ze opnieuw kunnen worden gebruikt en aanpasbaar zijn. En aangezien u veelvoudige malplaatjes beschikbaar in uw installatie van AEM kunt hebben, hebt u de flexibiliteit om verschillende plaatsen tot stand te brengen om aan diverse bedrijfsbehoeften te voldoen.

>[!TIP]
>
>Voor verder detail op plaatsmalplaatjes, zie het document [ Malplaatjes van de Plaats.](site-templates.md)

>[!NOTE]
>
>Het plaatssjabloon moet niet met [ paginasjablonen worden verward.](/help/sites-cloud/authoring/page-editor/templates.md) Sitesjablonen definiëren de algehele structuur van een site. Een paginasjabloon definieert de structuur en initiële inhoud van een afzonderlijke pagina.

### Door Adobe verschafte sitesjablonen {#adobe-templates}

{{adobe-templates}}

## Een site maken {#create-site}

Het is eenvoudig om een site te maken met een sjabloon.

1. Aanmelden bij uw AEM-ontwerpomgeving en naar de Sites-console navigeren

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

1. Geef aanvullende sitedetails op zoals vereist door de sitesjabloon.

   * Voor verschillende templates zijn mogelijk aanvullende details vereist.
   * Bijvoorbeeld, vereisen de malplaatjes voor [ projecten van Edge Delivery Services ](https://www.aem.live/developer/ue-tutorial) de bewaarplaats GitHub van uw project.

1. Selecteer **creeer** en de plaats wordt gecreeerd van het plaatssjabloon.

   ![ Details van de nieuwe plaats ](../assets/create-site-details.png)

1. In de bevestigingsdialoog die verschijnt, uitgezocht **Gedaan**.

   ![ de dialoog van het Succes ](../assets/success.png)

1. In de plaatsenconsole, is de nieuwe plaats zichtbaar en kan worden genavigeerd om zijn basisstructuur te onderzoeken zoals die door het malplaatje wordt bepaald.

   ![ Nieuwe plaatsstructuur ](../assets/new-site.png)

Inhoudsauteurs kunnen nu beginnen met ontwerpen!

## Aanpassing van site {#site-customization}

Sjablonen zijn handig voor het snel instellen van de basisstructuur en -stijl van een site. Voor de meeste projecten is echter aanvullende opmaak en aanpassing vereist. Sitesjablonen helpen u de stijl van de site te ontkoppelen, zodat front-end ontwikkelaars geen kennis van AEM nodig hebben om de site op te maken en de site
werk gescheiden van en parallel aan de makers van de inhoud. Afhankelijk van het type project kan dit twee vormen aannemen.

* Voor projecten met de pagina van AEM authoring met de Universele Redacteur en levering door [ randlevering, ](/help/edge/overview.md) wordt al het stileren gedaan in het project GitHub.
   * Gelieve te zien het document [ Begonnen worden - Universele Zelfstudie van de Ontwikkelaar van de Redacteur ](https://www.aem.live/developer/ue-tutorial) voor meer informatie.
* Voor projecten met traditionele AEM paginauteurs en levering door [ publiceren levering, ](/help/sites-cloud/authoring/author-publish.md) downloadt de beheerder van AEM eenvoudig het plaatsthema en verstrekt het aan de front-end ontwikkelaar die het gebruikend hun favoriete hulpmiddelen aanpast en dan de veranderingen in de de codebewaarplaats van AEM toebedeelt, die dan wordt opgesteld.
   * Gelieve te zien de Reis van de Aanmaak van de Plaats van het document [ Snelle ](/help/journey-sites/quick-site/overview.md) voor meer informatie.
