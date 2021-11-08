---
title: Creating a Site
description: Leer hoe u AEM kunt gebruiken om een site te maken met behulp van sitesjablonen om de stijl en structuur van uw site te definiëren.
feature: Administering
role: Admin
source-git-commit: efeb97d4bd7e7c11ec2c0ba1244a32b8b9affdab
workflow-type: tm+mt
source-wordcount: '819'
ht-degree: 0%

---


# Een site maken {#creating-site}

Learn how to use AEM create a site using site templates to define the style and structure of your site.

>[!CAUTION]
>
>The Quick Site Creation tool is currently a tech preview. Het wordt ter beschikking gesteld voor test- en evaluatiedoeleinden en is niet bestemd voor gebruik in de productie, tenzij overeengekomen met Adobe Support.

## Overzicht {#overview}

Voordat auteurs van inhoud pagina&#39;s met inhoud kunnen maken, moet de site eerst worden gemaakt. Dit wordt over het algemeen uitgevoerd door een AEM beheerder die de aanvankelijke structuur van de plaats bepaalt. Door het gebruik van sitesjablonen kunt u snel en flexibel sites maken.

Met het gereedschap AEM Snel site maken kunnen niet-ontwikkelaars snel een nieuwe site maken met behulp van sitesjablonen.

Once created, the Quick Site Creation tool also enables fast customization of the theme and styling of the AEM site (JavaScript, CSS, and static resources). This allows the front-end developer, who need zero knowledge of AEM, to work separately from and parallel to the content creators. De AEM beheerder downloadt eenvoudig het plaatsthema en verstrekt het aan de front-end ontwikkelaar die het gebruikend hun favoriete hulpmiddelen aanpast en dan de veranderingen in de AEM codebewaarplaats vastlegt, die dan wordt opgesteld.

Dit document richt zich op het maken van sites met het gereedschap Snel site maken. Als u een overzicht wilt van de workflow voor het maken en aanpassen van de site, raadpleegt u de [Reis voor snel maken van site AEM](/help/journey-sites/quick-site/overview.md)

## Sitestructuur plannen {#structure}

Neem de tijd om ruim van tevoren rekening te houden met het doel en de geplande inhoud van uw site. This will drive how you design the structure of the site. Een goede sitestructuur ondersteunt eenvoudige navigatie en detectie van inhoud voor uw sitebezoekers en ondersteunt diverse AEM functies, zoals [beheer en vertaling op meerdere locaties.](/help/sites-cloud/administering/msm-and-translation.md)

>[!TIP]
>
>[De WKND-referentiesite](https://wknd.site) biedt een implementatie van best practices voor een volledig functionele website voor buitenshuis ervaren merken. Explore it to see how a well-built AEM site is structured.

## Site Templates {#site-templates}

Omdat de sitestructuur zo belangrijk is voor het succes van een site, is het handig om vooraf gedefinieerde structuren beschikbaar te hebben om snel een nieuwe site te implementeren op basis van een set bestaande standaarden. Site templates are a way to combine basic site content into a convenient and reusable package.

Sitesjablonen bevatten over het algemeen inhoud en structuur van de basissite en informatie over de sitestijl om snel met de nieuwe site aan de slag te kunnen gaan. Templates are powerful because they are reusable as well as customizable. En aangezien u veelvoudige malplaatjes beschikbaar in uw AEM installatie kunt hebben, hebt u de flexibiliteit om verschillende plaatsen tot stand te brengen om aan diverse bedrijfsbehoeften te voldoen.

>[!TIP]
>
>Voor meer informatie over sitesjablonen raadpleegt u de [Sitesjablonen](site-templates.md) artikel.

>[!NOTE]
>
>De sitesjabloon mag niet worden verward met paginasjablonen. Sitesjablonen definiëren de algehele structuur van een site. Een paginasjabloon definieert de structuur en initiële inhoud van een afzonderlijke pagina.

## Creating a Site {#create-site}

Het is eenvoudig om een site te maken met een sjabloon.

1. Onderteken in uw AEM ontwerpomgeving en navigeer naar de Sites-console

   * `https://<your-author-environment>.adobeaemcloud.com/sites.html/content`

1. Tik of klik op **Maken** rechtsboven in het scherm en in het keuzemenu selecteert u **Site van sjabloon**.

   ![Creating a site from a template](../assets/create-site-from-template.png)

1. Tik of klik in de wizard Site maken op een bestaande sjabloon in het linkerdeelvenster of op **Importeren** boven aan de linkerkolom om een nieuwe sjabloon te importeren.

   ![Wizard Site maken](../assets/site-creation-wizard.png)

   1. Als u ervoor kiest om in de bestandenbrowser de sjabloon te importeren die u wilt gebruiken en tikt of klikt u op **Uploaden**.

   1. Nadat de sjabloon is geüpload, wordt deze weergegeven in de lijst met beschikbare sjablonen.

1. Als u een sjabloon selecteert, wordt informatie over de sjabloon in de rechterkolom weergegeven. Selecteer de gewenste sjabloon en tik of klik op **Volgende**.

   ![Een sjabloon selecteren](../assets/select-site-template.png)

1. Geef een titel op voor uw site. Er kan een sitenaam worden opgegeven of deze wordt gegenereerd op basis van de titel als deze wordt weggelaten.

   * De titel van de site wordt weergegeven in de titelbalk van browsers.
   * The site name becomes part of the URL.
   * De sitenaam moet voldoen aan [AEM naamconventies voor pagina&#39;s.](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#page-name-restrictions-and-best-practices)

1. Tik of klik op **Maken** en de site wordt gemaakt op basis van de sitesjabloon.

   ![Details van de nieuwe site](../assets/create-site-details.png)

1. Tik of klik op **Gereed**.

   ![Success dialog](../assets/success.png)

1. In de plaatsenconsole, is de nieuwe plaats zichtbaar en kan worden genavigeerd om zijn basisstructuur te onderzoeken zoals die door het malplaatje wordt bepaald.

   ![Nieuwe sitestructuur](../assets/new-site.png)

Inhoudsauteurs kunnen nu beginnen met ontwerpen!

## Site Customization {#site-customization}

Als voor uw site aanpassingen nodig zijn die verder gaan dan de beschikbare sjablonen, hebt u een aantal opties.

* Als de sitestructuur of initiële inhoud moet worden aangepast, [De sitesjabloon kan aan uw vereisten worden aangepast.](site-templates.md)
* Als de sitestijl moet worden aangepast, [het site-thema kan worden gedownload en aangepast.](/help/journey-sites/quick-site/overview.md)
* Als de functionaliteit van de site moet worden aangepast, [de site kan volledig worden aangepast.](/help/implementing/developing/introduction/develop-wknd-tutorial.md)

Any customization should be undertaken with the support of a development team.
