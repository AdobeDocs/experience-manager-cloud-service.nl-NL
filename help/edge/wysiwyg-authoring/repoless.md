---
title: Code op verschillende sites opnieuw gebruiken
description: Als u veel vergelijkbare sites hebt die er meestal hetzelfde uitzien en hetzelfde gedrag vertonen, maar andere inhoud hebben, leert u hoe u code kunt delen over meerdere sites in een repoless-model.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: a6bc0f35-9e76-4b5a-8747-b64e144c08c4
source-git-commit: 7b37f3d387f0200531fe12cde649b978f98d5d49
workflow-type: tm+mt
source-wordcount: '1041'
ht-degree: 0%

---

# Code op verschillende sites opnieuw gebruiken {#repoless}

Als u veel vergelijkbare sites hebt die er meestal hetzelfde uitzien en hetzelfde gedrag vertonen, maar andere inhoud hebben, leert u hoe u code kunt delen over meerdere sites in een repoless-model.

## Eén Codebase voor meerdere sites {#one-codebase}

Standaard is AEM nauw gebonden aan uw gegevensopslagruimte, die voldoet aan de meeste gebruiksgevallen. Het is echter mogelijk dat er meerdere sites zijn die het meest van elkaar verschillen in de inhoud, maar u kunt hetzelfde codebasis gebruiken.

Eerder dan het creëren van veelvoudige bewaarplaatsen GitHub en het runnen van elke plaats van een specifieke bewaarplaats GitHub terwijl het houden van hen in synchronisatie, AEM steunt het runnen van veelvoudige plaatsen van de zelfde codebase.

Deze vereenvoudigde opstelling, die de behoefte aan codereplicatie elimineert is ook genoemd geworden [ &quot;repoless&quot;, ](https://www.aem.live/docs/repoless) omdat allen behalve uw eerste plaats geen bewaarplaats GitHub van hun nodig heeft.

Als voor uw project de onherroepelijke flexibiliteit van hergebruik van code op verschillende sites nodig is, kunt u de functie activeren.

Ongeacht het aantal sites dat u uiteindelijk zonder problemen wilt maken, moet u de eerste site maken, die als uw basissite fungeert. In dit document wordt uitgelegd hoe u voor het eerst een site maakt voor onophoudelijk gebruik.

## Vereisten {#prerequisites}

Als u van deze functie wilt profiteren, moet u het volgende doen.

* Uw plaats is reeds volledig opstelling door het document [ Begonnen Gids van de Ontwikkelaar te volgen Begonnen voor het Authoring van WYSIWYG met Edge Delivery Services.](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md)
* U gebruikt minimaal AEM as a Cloud Service 2024.08.

U zult ook Adobe moeten vragen om twee punten voor u te vormen. Neem contact op met de Adobe via uw Slack of stel een supportprobleem aan de orde om deze verzoeken in te dienen.

* De {](https://www.aem.live/docs/config-service-setup#prerequisites) de configuratiedienst 0} aem.live is actief voor uw milieu en u wordt gevormd als beheerder.[
* De functie voor probleemloos afdrukken moet zijn ingeschakeld voor uw programma door Adobe.

## Repoless-functie activeren {#activate}

Er zijn verschillende stappen om de functie voor probleemloos gebruik voor uw project te activeren.

1. [Toegangstoken ophalen](#access-token)
1. [Configuratieservice instellen](#config-service)
1. [Siteconfiguratie en technische account toevoegen](#access-control)
1. [AEM bijwerken](#update-aem)
1. [Site verifiëren](#authenticate-site)

In deze stappen wordt de site `https://wknd.site` als voorbeeld gebruikt. Vervang uw eigen product op de juiste manier.

### Toegangstoken ophalen {#access-token}

U zult eerst een toegangstoken nodig hebben om de configuratieservice te gebruiken en het voor het repoless gebruiksgeval te vormen.

1. Ga naar `https://admin.hlx.page/login` en gebruik het `login_adobe` -adres om u aan te melden bij de identiteitsprovider van de Adobe.
1. U wordt doorgestuurd naar `https://admin.hlx.page/profile` .
1. Kopieer met behulp van de ontwikkelaarsgereedschappen van uw browser de waarde van de `x-auth-token` ofwel uit het JSON-webtoken-cookie dat de pagina van `admin.hlx.page` instelt.

Zodra u uw toegangstoken hebt, kan het in de kopbal van cURL- verzoeken in het volgende formaat worden overgegaan.

```text
--header 'x-auth-token: <your-token>'
```

### Uw configuratieservice configureren {#config-service}

Zoals vermeld in de [ eerste vereisten, ](#prerequisites) de configuratiedienst moet voor uw milieu worden toegelaten. U kunt de installatie van uw configuratieservice controleren met deze opdracht cURL.

```text
curl  --location 'https://admin.hlx.page/config/<your-github-org>.json' \
--header 'x-auth-token: <your-token>'
```

Als de configuratieservice correct wordt ingesteld, zal JSON gelijkend op het volgende zijn teruggekeerd.

```json
{
  "title": "<your-github-org>",
  "description": "Your GitHub Org",
  "lastModified": "2024-11-14T12:14:04.230Z",
  "created": "2024-11-14T12:13:37.032Z",
  "version": 1,
  "users": [
    {
      "email": "justthisguyyouknow@adobe.com",
      "roles": [
        "admin"
      ],
      "id": "<your-id>"
    }
  ]
}
```

Bereik uit aan Adobe via uw kanaal van de Slack van het project of breng een steunkwestie aan als uw configuratieservice niet wordt toegelaten. Zodra u uw teken hebt en geverifieerd dat de configuratieservice wordt toegelaten, kunt u de configuratie voortzetten.

1. Controleer of de inhoudsbron op de juiste wijze is ingesteld.

   ```text
   curl --request GET \
   --url https://admin.hlx.page/config/<your-github-org>/sites/<your-aem-project>.json \
   --header 'x-auth-token: <your-token>'
   ```

1. Voeg een wegafbeelding aan de openbare configuratie toe.

   ```text
   curl --request POST \
     --url https://admin.hlx.page/config/<your-github-org>/sites/<your-aem-project>/public.json \
     --header 'x-auth-token: <your-token>' \
     --header 'Content-Type: application/json' \
     --data '{
       "paths": {
           "mappings": [
               "/content/<your-site-content>/:/"
      ],
           "includes": [
               "/content/<your-site-content>/"
           ]
       }
   }'
   ```

Wanneer de openbare configuratie is gemaakt, kunt u deze openen via een URL die lijkt op `https://main--<your-aem-project>--<your-github-org>.aem.page/config.json` om de openbare configuratie te controleren.

### Padtoewijzing toevoegen voor siteconfiguratie en technische account instellen {#access-control}

U moet een siteconfiguratie maken en deze toevoegen aan uw padtoewijzing.

1. Creeer een nieuwe pagina bij de wortel van uw plaats en kies het [**malplaatje van de Configuratie**.](/help/edge/wysiwyg-authoring/tabular-data.md#other)
   * U kunt de configuratie leeg laten met alleen de vooraf gedefinieerde kolommen `key` en `value` . U hoeft deze alleen te maken.
1. Creeer een afbeelding in de openbare configuratie aan de plaatsconfiguratie gebruikend een cURL bevel gelijkend op het volgende.

   ```text
   curl --request POST \
     --url https://admin.hlx.page/config/<your-github-org>/sites/<your-aem-project>/public.json \
     --header 'x-auth-token: <your-token>' \
     --header 'Content-Type: application/json' \
     --data '{
       "paths": {
           "mappings": [
               "/content/<your-site-content>/:/",
               "/content/<your-site-content>/configuration:/.helix/config.json"
      ],
           "includes": [
               "/content/<your-site-content>/"
           ]
       }
   }'
   ```
1. Valideer dat de openbare configuratie is geplaatst en beschikbaar met een cURL bevel gelijkend op het volgende is.

   ```text
   curl 'https://main--<your-aem-project>--<your-github-org>.aem.live/config.json'
   ```

Zodra de plaatsconfiguratie in kaart wordt gebracht, kunt u toegangsbeheer vormen door uw technische rekening te bepalen zodat heeft het voorrechten om te publiceren.

1. Haal in uw browser de technische account op als antwoord op de volgende koppeling.

   ```text
   https://author-p<programID>-e<envionmentID>.adobeaemcloud.com/bin/franklin.delivery/<your-github-org>/<your-aem-project>/main/.helix/config.json
   ```

1. De reactie zal gelijkaardig aan het volgende zijn.

   ```json
   {
     "total": 1,
     "offset": 0,
     "limit": 1,
     "data": [
       {
         "key": "admin.role.publish",
         "value": "<tech-account-id>@techacct.adobe.com"
       }
     ],
     ":type": "sheet"
   }
   ```

1. Stel de technische account in uw configuratie in met een cURL-opdracht die lijkt op het volgende:

   ```text
   curl --request POST \
     --url https://admin.hlx.page/config/<your-github-org>/sites/<your-aem-project>/access.json \
     --header 'Content-Type: application/json' \
     --header 'x-auth-token: <your-token>' \
     --data '{
       "admin": {
           "role": {
               "admin": [
                   "*@adobe.com"
               ],
               "config_admin": [
                   "<tech-account-id>@techacct.adobe.com"
               ]
           },
           "requireAuth": "auto"
       }
   }'
   ```

Aangezien u nu de configuratieservice gebruikt, kunt u `fstab.yaml` en `paths.json` verwijderen uit uw Git-opslagplaats.

>[!NOTE]
>
>Als u de configuratieservice gebruikt en de padtoewijzing via `config.json` toegankelijk maakt, wordt het `path.json` -bestand genegeerd.

Zodra AEM voor repoless gebruik wordt gevormd, moet u de configuratieservice gebruiken en een geldige `config.json` van de wegafbeelding voorzien.

### AEM bijwerken {#update-aem}

Nu bent u klaar om de noodzakelijke veranderingen in uw Edge Delivery Services in AEM aan te brengen.

1. Teken in de AEM auteursinstantie en ga naar **Hulpmiddelen** -> **Cloud Servicen** -> **Configuratie van Edge Delivery Services** en selecteer de configuratie die automatisch voor uw plaats werd gecreeerd en tikken of **Eigenschappen** in de hulpmiddelbar klikken.
1. In het **venster van de Configuratie van 0} Edge Delivery Services {, verander projecttype in** aem.live met repoless config opstelling **en tik of klik** sparen &amp; dicht **.**
   ![ Configuratie van Edge Delivery Services ](/help/edge/wysiwyg-authoring/assets/repoless/edge-delivery-services-configuration.png)
1. Ga terug naar uw site met de Universal Editor en zorg ervoor dat deze nog steeds correct wordt weergegeven.
1. Wijzig enkele inhoud en publiceer deze opnieuw.
1. Ga naar de gepubliceerde site op `https://main--<your-aem-project>--<your-github-org>.aem.page/` en controleer of de wijzigingen correct zijn doorgevoerd.

Uw project is nu ingesteld voor onophoudelijk gebruik.

## Volgende stappen {#next-steps}

Nu uw basissite is geconfigureerd voor onophoudelijk gebruik, kunt u extra sites maken die gebruikmaken van dezelfde codebasis. Raadpleeg de volgende documentatie, afhankelijk van uw gebruiksscenario.

* [Meerdeloos beheer van sites](/help/edge/wysiwyg-authoring/repoless-msm.md)
* [Stage- en Prod-omgevingen zonder weerstand](/help/edge/wysiwyg-authoring/repoless-stage-prod.md)

## Problemen oplossen {#troubleshooting}

Het meest voorkomende probleem dat u tegenkomt na het configureren van het gebruiksscenario voor onophoudelijk gebruik, is dat pagina&#39;s in de Universal Editor niet meer worden gerenderd of dat u een witte pagina of een algemeen AEM as a Cloud Service-foutbericht ontvangt. In dergelijke gevallen:

* De bron van de weergegeven pagina weergeven.
   * Is er eigenlijk iets teruggegeven (correcte HTML head met `scripts.js`, `aem.js`, en redacteurs-verwante JSON dossiers)?
* Controleer de AEM `error.log` van de auteurinstantie op uitzonderingen.
   * De meest voorkomende kwestie is dat de paginacomponent met 404 fouten ontbreekt.
   * `config.json or paths.json` kan niet worden geladen
   * `component-definition.json` enz. kan niet worden geladen
