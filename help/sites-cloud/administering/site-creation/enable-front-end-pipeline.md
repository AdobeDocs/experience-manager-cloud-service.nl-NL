---
title: Het toelaten van de Voorste Pijpleiding
description: Leer hoe u de front-end pijpleiding voor bestaande plaatsen kunt toelaten om plaatsthema's te gebruiken om uw plaats sneller aan te passen.
feature: Administering
role: Admin
exl-id: 55d54d72-f87b-47c9-955f-67ec5244dd6e
solution: Experience Manager Sites
source-git-commit: d37bdc060ea569748745011346bc448a569ae91d
workflow-type: tm+mt
source-wordcount: '910'
ht-degree: 0%

---

# Het toelaten van de Voorste Pijpleiding {#enable-front-end-pipeline}

Leer hoe u de front-end pijpleiding voor bestaande plaatsen kunt toelaten om plaatsthema&#39;s te gebruiken om uw plaats sneller aan te passen.

## Overzicht {#overview}

De front-end pijpleiding is een mechanisme dat enkel de front-end code van uw websites kan snel opstellen die op [ wordt gebaseerd plaatsthema&#39;s ](site-themes.md) en [ plaatssjablonen ](site-templates.md).

Deze pijpleiding behandelt slechts front-end code, die het plaatsingsproces sneller dan volledig-stapel plaatsingen maakt. Met deze functie kunnen ontwikkelaars aan de voorzijde uw site eenvoudig aanpassen zonder dat ze kennis van AEM nodig hebben.

De plaatsen die op plaatsmalplaatjes worden gebaseerd kunnen de front-end pijpleiding door gebrek gebruiken. Dit document beschrijft hoe u uw bestaande plaatsen kunt aanpassen om uit de front-end pijpleiding voordeel te halen.

>[!TIP]
>
>Als u niet vertrouwd met de front-end pijpleiding bent en hoe te om plaatsen op te stellen snel gebruikend het en plaatssjablonen, zie [&#128279;](/help/journey-sites/quick-site/overview.md) de Reis van de Aanmaak van de Snelle Plaats  voor een inleiding.

AEM kan uw site zo configureren dat deze thema&#39;s laadt die worden geïmplementeerd met de Front End Pipeline, zelfs als uw site niet is gemaakt met sitesjablonen en -thema&#39;s, door deze in lagen boven op bestaande clientbibliotheken te plaatsen.

## Technische details {#technical-details}

Wanneer u de front-end pijplijn voor een plaats activeert, brengt AEM de volgende veranderingen in uw plaatsstructuur aan.

* Alle pagina&#39;s van de site bevatten één extra CSS- en JS-bestand, dat kan worden gewijzigd door updates te implementeren via een speciale Cloud Manager front-end pipe.
* De toegevoegde CSS- en JS-bestanden zijn aanvankelijk leeg. U kunt echter een map met &quot;themabronnen&quot; downloaden om de mappenstructuur in te stellen die nodig is om CSS- en JS-code-updates via de pijplijn te implementeren.
* Alleen ontwikkelaars kunnen de wijziging ongedaan maken door de knooppunten `SiteConfig` en `HtmlPageItemsConfig` die met deze bewerking onder `/conf/<site-name>/sling:configs` worden gemaakt, te verwijderen.

>[!NOTE]
>
>Met deze actie worden de bestaande clientbibliotheken van de site niet automatisch omgezet voor gebruik van de eindpijplijn voor lettertypen. Het verplaatsen van deze bronnen van de omslag van de cliëntbibliotheek naar de front-end pijpleidingsomslag is een taak die handwerk door een front-end ontwikkelaar vereist.

## Vereisten {#requirements}

AEM kan uw bestaande site automatisch aanpassen om de front-end pijplijn te gebruiken. Om dit werkschema te kunnen doen, moet uw plaats [ v2 of nieuwer van de Component van de Pagina van de Componenten van de Kern ](https://experienceleague.adobe.com/nl/docs/experience-manager-core-components/using/wcm-components/page) gebruiken.

## Het toelaten van Voorste Pijl-Eind {#enabling}

{{add-cm-allowlist-frontend-pipeline}}

Het toelaten van uw plaats wordt gedaan van de console van Plaatsen gebruikend het [ spoor van de Plaats ](site-rail.md).

1. Logboek in AEM en navigeer aan uw plaats via **Globale Navigatie** > **Plaatsen**.
1. Selecteer uw site in de console. Selecteer de hoofdmap van de site en geen onderliggende pagina&#39;s.
1. Met uw geselecteerde plaats, open de [ spoorselecteur ](/help/sites-cloud/authoring/basic-handling.md#rail-selector) bij de linkerzijde en kies **Plaats**.
1. In het **spoor van de Plaats**, klik de knoop **laat Voorste Pijpleiding van het Eind** toe.

   ![ laat front-end pijpleiding ](/help/sites-cloud/administering/assets/enable-front-end-pipeline.png) toe

1. AEM vraagt u te bevestigen met een overzicht van de aangebrachte wijzigingen. Bevestig en uw site is aangepast.

Nu, is uw plaats klaar om de front-end pijpleiding te gebruiken. Meer over de front-end pijpleiding en het beheren van uw plaatsthema leren zie:

* [Het Siterail gebruiken om uw Sitethema te beheren](site-rail.md)
* [ Snelle Reis van de Aanmaak van de Plaats ](/help/journey-sites/quick-site/overview.md) - Deze documentatierit geeft u en overzicht van begin tot eind van het proces om snel een plaats op te stellen gebruikend de front-end pijpleiding en het Snelle hulpmiddel van de Aanmaak van de Plaats.
* [ CI/CD Pijpleidingen ](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) - Dit document beschrijft de front-end pijpleiding in de context van de volledig-stapel en Webrijpijpleidingen.

## Pijpleiding aan de voorzijde en aangepaste domeinen {#custom-domains}

De voorste-Eind Pijpleiding kan met [ worden gebruikt de eigenschap van de douanedomeinen van Cloud Manager, ](/help/implementing/cloud-manager/custom-domain-names/introduction.md) maar gelieve zich van de volgende vereisten bewust te zijn wanneer het gebruiken van de twee eigenschappen samen.

### Statische front-end bestanden {#static-files}

Statische front-end activa die via de Voorste-Eind Pijpleiding worden opgesteld zullen, door gebrek, van het vooraf bepaalde statische domein van Adobe worden gediend.

Als u een aangepast domein nodig hebt voor front-end elementen, kunt u een aangepast domein installeren op de publicatielijst en de Dispatcher zodanig configureren dat specifieke paden (zoals `/static/` ) naar de statische hostinglocatie van Adobe worden geleid. Deze methode vereist het bijwerken van uw [ regels van Dispatcher ](https://experienceleague.adobe.com/nl/docs/experience-manager-dispatcher/using/dispatcher) behoorlijk en geheim voorgeheugenverzoeken om statische activa door:sturen.

Nadat u het aangepaste domein en de dispatcher hebt geconfigureerd, kunt u AEM configureren voor de front-end elementen van het statische domein.

### Configuratie {#configuration}

Zoals beschreven in de [ Technische Details ](#technical-details) sectie, die de Voorste-Eind eigenschap van de Pijl voor een plaats activeren leidt tot a `SiteConfig` en `HtmlPageItemsConfig` hieronder knopen `/conf/<site-name>/sling:configs`.

Als u de functie Aangepaste Cloud Manager-domeinen voor uw site samen met de Front End Pipeline wilt gebruiken voor statuselementen, moeten aanvullende eigenschappen aan deze knooppunten worden toegevoegd.

1. Stel de eigenschap `customFrontendPrefix` in `SiteConfig` voor de site in.
   1. Navigeer naar `/conf/<site-name>/sling:configs/com.adobe.aem.wcm.site.manager.config.SiteConfig` .
   1. Voeg de eigenschap `customFrontendPrefix = "https://your-custom-domain.com/static/"` toe of werk deze bij.
1. Hiermee wordt de `prefixPath` waarde van de `HtmlPageItemsConfig` bijgewerkt met het aangepaste domein.
   1. Navigeer naar `/conf/<site-name>/sling:configs/com.adobe.cq.wcm.core.components.config.HtmlPageItemsConfig` .
   1. Controleer of de `prefixPath` verwijst naar uw aangepaste domein, zoals `prefixPath = "https://your-custom-domain.com/static/<hash>/..."` .
   * Deze waarde kan desgewenst ook handmatig worden overschreven.
1. Controleer de instellingen.
   1. Na plaatsing, controleer dat de pagina&#39;s correct naar thematiedetecten van het douanedomein verwijzen.
   1. Open de ontwikkelaarsgereedschappen van uw browser en controleer de bestandspaden `theme.css` en `theme.js` om te controleren of deze vanaf het juiste domein zijn geladen.

Pagina&#39;s voor de site verwijzen vervolgens naar themaartefacten van die bijgewerkte URL. De verzender leidt dan verzoeken om die middelen aan het statische domein.

## Beste praktijken voor Voorste-Eind Ontwikkelaars {#best-practices}

Als u front-end activa plaatselijk moet ontwikkelen en testen alvorens via de Voor-Eind Pijpleiding op te stellen, overweeg de volgende benaderingen:

* Gebruik de Wijze van de Volmacht van de Bouwer van het Thema van de Plaats [&#128279;](https://github.com/adobe/aem-site-theme-builder?tab=readme-ov-file#proxy) om thema artefacten voor het testen plaatselijk met voeten te treden.
* Plaats uw themabestanden handmatig vanaf een lokale ontwikkelingsserver en werk de `prefixPath` in `HtmlPageItemsConfig` bij, zodat deze overeenkomt met het lokale serveradres.
* Zorg ervoor dat het in cache plaatsen van browsers tijdens het testen is uitgeschakeld om live updates te zien.

Voor meer details op lokale front-end ontwikkeling, verwijs naar de [ documentatie van de Bouwer van het Thema van de Plaats.](https://github.com/adobe/aem-site-theme-builder)
