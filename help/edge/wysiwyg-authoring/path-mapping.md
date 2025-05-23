---
title: Padtoewijzing voor Edge Delivery Services
description: Leer hoe u paginapaden die in de AEM-ontwerpinstantie worden gebruikt, kunt toewijzen aan openbare paginapaden die op de website worden gebruikt en bepalen welke inhoud naar Edge Delivery Services wordt gepubliceerd.
feature: Edge Delivery Services
role: User
exl-id: 3d68135d-e84c-4bf4-93d1-38a0be70ce4a
index: false
hide: true
hidefromtoc: true
source-git-commit: 17c14a78c2cfa262e25c6196fa73c6c4b17e200a
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 0%

---

# Padtoewijzing voor Edge Delivery Services {#path-mapping}

Leer hoe u paginapaden die in de AEM-ontwerpinstantie worden gebruikt, kunt toewijzen aan openbare paginapaden die op de website worden gebruikt en bepalen welke inhoud naar Edge Delivery Services wordt gepubliceerd.

## Overzicht {#overview}

Als u WYSIWYG-inhoud wilt ontwerpen met AEM en deze wilt publiceren naar Edge Delivery Services, moet u de padtoewijzing van uw project instellen. Deze toewijzing heeft twee doelen.

* Hiermee wordt een relatie toegewezen en gemaakt tussen de paginapaden die worden gebruikt op uw AEM-ontwerpinstantie en de openbare paginapaden die worden gebruikt op uw website.
* Hiermee bepaalt u welke inhoud (pagina&#39;s, bladen, elementen, enz.) naar Edge Delivery Services wordt gepubliceerd.

De padtoewijzing moet voor elk project afzonderlijk worden geconfigureerd en op basis van de inhoud en URL-structuur van het project. Het wordt gebruikt door AEM tijdens inhoud het publiceren en terwijl het uitgeven van inhoud in de [ Universele Redacteur ](/help/sites-cloud/authoring/universal-editor/navigation.md).

## Configuratie-indeling {#configuration-format}

De indeling van de configuratie voor padtoewijzing bevat twee secties (`mappings` en `includes` ) die lijken op het volgende voorbeeld.

```json
{
  "mappings": [
    "/content/aem-boilerplate/:/",
    "/content/aem-boilerplate/configuration:/.helix/config.json"
  ],
  "includes:" [
    "/content/aem-boilerplate/"
  ]
}
```

### toewijzingen {#mappings}

De `mappings` -configuratie bevat een array met interne paden (in de AEM-ontwerpinstantie) en externe URL-paden (op de openbare website).

De notatie is `<internal paths>:<external path>` . Het bestaat doorgaans uit minimaal twee vermeldingen.

1. De eerste vermelding in het voorbeeld is de padtoewijzing van de websitepagina&#39;s.
1. Het tweede item bepaalt de toewijzing van de `.helix/config.json` aan de corresponderende spreadsheetpagina in de AEM-authoringopslagplaats.

In dit voorbeeld zijn alle pagina&#39;s die zijn opgeslagen onder `/content/aem-boilerplate/...` , rechtstreeks toegankelijk voor het publiek op de Edge Delivery Services-site onder `https://main--my-site--org.aem.live/....` .

>[!TIP]
>
>Alle tabelgegevens die als spreadsheets worden beheerd (bijvoorbeeld metagegevens, omleidingen en taxonomie) worden doorgaans gepubliceerd als `.json` API-URL&#39;s op Edge Delivery Services. Om dit te doen, moeten zij individueel in de kaartconfiguratie worden vermeld.
>
>Gelieve te zien het document [ Gebruikend Spreadsheets om Gegevens in Tabel ](/help/edge/wysiwyg-authoring/tabular-data.md) voor meer informatie te beheren.

### include {#includes}

De `includes` -configuratie bepaalt welke inhoudspaden daadwerkelijk naar Edge Delivery Services worden gerepliceerd. Het kan om het even welke serie van wegen ook bevatten en typisch bevat de de hoofdpagina van het hoogste niveau van plaatsen.

Assets die op Edge Delivery Services-pagina&#39;s wordt gebruikt, wordt doorgaans naast de webpagina gepubliceerd. Ze worden automatisch geëxporteerd van de AEM-ontwerpinstantie naar Edge Delivery Services.

>[!TIP]
>
>Als u een gebruikscase hebt waarin elementen die rechtstreeks naar Edge Delivery Services worden gepubliceerd (bijvoorbeeld als u afbeeldingen of PDF&#39;s direct toegankelijk wilt maken via hun URL&#39;s buiten een paginacontext), moet u ook de DAM-paden toevoegen aan de sectie `includes` van de configuratie.
>
>Als een elementenhoofdmap, zoals `/content/dam/my-site/documents` die een set PDF bevat, via `/assets/...` toegankelijk moet zijn voor het publiek, moet een item worden toegevoegd aan de sectie `includes` van de configuratie.

## Hoe te vormen {#how-to-configure}

Uw wegtoewijzingen kunnen op één van twee manieren afhankelijk van de opstelling van uw project worden gevormd.

1. Als het project voor `aem.live` wordt gevormd en de [ configuratiedienst ](https://www.aem.live/docs/config-service-setup) voor gecentraliseerde configuraties gebruikt, wordt de wegafbeelding voor elke plaats gevormd via deze configuratiedienst.

   * Hier volgt een voorbeeld van een cURL-aanvraag om padtoewijzingen te configureren.

   ```text
   curl --request POST \
     --url https://admin.aem.page/config/{org}/sites/{site}/public.json \
     --header 'Content-Type: application/json' \
     --header 'x-auth-token: ......' \
     --data '{
       "paths": {
       "mappings": [
         "/content/aem-boilerplate/:/",
         "/content/aem-boilerplate/configuration:/.helix/config.json"
       ],
       "includes": [
         "/content/aem-boilerplate/"
       ]
   }
   }'
   ```

1. Als het project niet de configuratieservice gebruikt, wordt de wegafbeelding gevormd via een `paths.json` dossier in u de bewaarplaats van GitHub projecten.

   * Zie [`https://github.com/adobe-rnd/aem-boilerplate-xwalk/blob/main/paths.json` ](https://github.com/adobe-rnd/aem-boilerplate-xwalk/blob/main/paths.json) voor een voorbeeld.

In beide gevallen, zodra u uw wegafbeeldingen vormt, kunt u de configuratie controleren via openbaar-toegankelijke configuratie URL `https://<branch>--<site>--<org>.aem.page/config.json`.
