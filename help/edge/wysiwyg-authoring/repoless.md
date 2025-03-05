---
title: Code op verschillende sites opnieuw gebruiken
description: Als u veel vergelijkbare sites hebt die er meestal hetzelfde uitzien en hetzelfde gedrag vertonen, maar andere inhoud hebben, leert u hoe u code kunt delen over meerdere sites in een repoless-model.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: a6bc0f35-9e76-4b5a-8747-b64e144c08c4
source-git-commit: 7b46af35b202446fdea67e4125d74c3965d302d9
workflow-type: tm+mt
source-wordcount: '1039'
ht-degree: 0%

---

# Code op verschillende sites opnieuw gebruiken {#repoless}

Als u veel vergelijkbare sites hebt die er meestal hetzelfde uitzien en hetzelfde gedrag vertonen, maar andere inhoud hebben, leert u hoe u code kunt delen over meerdere sites in een repoless-model.

## Eén Codebase voor meerdere sites {#one-codebase}

AEM is standaard strak gebonden aan uw code-opslagplaats, die voldoet aan de meeste gebruiksgevallen. Het is echter mogelijk dat er meerdere sites zijn die het meest van elkaar verschillen in de inhoud, maar u kunt hetzelfde codebasis gebruiken.

In plaats van het creëren van veelvoudige bewaarplaatsen GitHub en het runnen van elke plaats van een specifieke bewaarplaats GitHub terwijl het houden van hen in synchronisatie, steunt AEM het runnen van veelvoudige plaatsen van de zelfde codebase.

Deze vereenvoudigde opstelling, die de behoefte aan codereplicatie elimineert is ook genoemd geworden [ &quot;repoless&quot;](https://www.aem.live/docs/repoless), omdat al behalve uw eerste plaats geen bewaarplaats GitHub van hun nodig heeft.

Als voor uw project de onherroepelijke flexibiliteit van hergebruik van code op verschillende sites nodig is, kunt u de functie activeren.

Ongeacht het aantal sites dat u uiteindelijk zonder problemen wilt maken, moet u de eerste site maken, die als uw basissite fungeert. In dit document wordt uitgelegd hoe u voor het eerst een site maakt voor onophoudelijk gebruik.

## Vereisten {#prerequisites}

Als u van deze functie wilt profiteren, moet u het volgende doen.

* Uw plaats is reeds volledig opstelling door het document [ Begonnen Gids van de Ontwikkelaar te volgen Begonnen voor de Authoring van WYSIWYG met Edge Delivery Services ](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md).
* U gebruikt minimaal AEM as a Cloud Service 2024.08.

U moet Adobe ook vragen om de volgende items voor u te configureren. Ga via je Slack-kanaal naar of stel een supportprobleem op om Adobe te vragen deze wijzigingen aan te brengen:

* Vraag om de [ aem.live configuratieservice ](https://www.aem.live/docs/config-service-setup#prerequisites) voor uw milieu te activeren en dat u als beheerder wordt gevormd.
* Vraag of Adobe de functie voor probleemloos afdrukken voor uw programma moet inschakelen.
* Vraag Adobe om de org voor u te maken.

## Repoless-functie activeren {#activate}

Er zijn verschillende stappen om de functie voor probleemloos gebruik voor uw project te activeren.

1. [Toegangstoken ophalen](#access-token)
1. [Configuratieservice instellen](#config-service)
1. [Siteconfiguratie en technische account toevoegen](#access-control)
1. [AEM-configuratie bijwerken](#update-aem)
1. [Site verifiëren](#authenticate-site)

In deze stappen wordt de site `https://wknd.site` als voorbeeld gebruikt. Vervang uw eigen product op de juiste manier.

### Toegangstoken ophalen {#access-token}

U zult eerst een toegangstoken nodig hebben om de configuratieservice te gebruiken en het voor het repoless gebruiksgeval te vormen.

1. Ga naar `https://admin.hlx.page/login` en gebruik het `login_adobe` -adres om u aan te melden bij de Adobe-identiteitsprovider.
1. U wordt doorgestuurd naar `https://admin.hlx.page/profile` .
1. Kopieer met behulp van de ontwikkelaarsgereedschappen van uw browser de waarde van de `x-auth-token` ofwel uit het JSON-webtoken-cookie dat de pagina van `admin.hlx.page` instelt.

Zodra u uw toegangstoken hebt, kan het in de kopbal van cURL- verzoeken in het volgende formaat worden overgegaan.

```text
--header 'x-auth-token: <your-token>'
```

### Padtoewijzing toevoegen voor siteconfiguratie en technische account instellen {#access-control}

U moet een siteconfiguratie maken en deze toevoegen aan uw padtoewijzing.

1. Creeer een nieuwe pagina bij de wortel van uw plaats en kies het **malplaatje van de Configuratie[** ](/help/edge/wysiwyg-authoring/tabular-data.md#other).
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

1. Teken in de auteursinstantie van AEM en ga naar **Hulpmiddelen** -> **de Diensten van de Wolk** -> **Configuratie van Edge Delivery Services** en selecteer de configuratie die automatisch voor uw plaats werd gecreeerd en tikken of **Eigenschappen** in de hulpmiddelbar klikken.

1. In het **venster van de Configuratie van Edge Delivery Services**, selecteer het **3} lusje van de Authentificatie {en kopieer de waarde voor** Technische rekening identiteitskaart **.**

   * Het zal er ongeveer zo uitzien als `<tech-account-id>@techacct.adobe.com`
   * De technische account is hetzelfde voor alle sites in één AEM-auteuromgeving.

1. Stel de technische account voor de configuratie zonder opbergvak in met een cURL-opdracht vergelijkbaar met de volgende, waarbij u de technische account-id gebruikt die u hebt gekopieerd.

   * Pas het `admin` -blok aan om de gebruikers te definiëren die volledige beheertoegang tot de site moeten hebben.
      * Het is een array met e-mailadressen.
      * U kunt jokerteken `*` gebruiken.
      * Zie het document [ Vormende Authentificatie voor Auteurs ](https://www.aem.live/docs/authentication-setup-authoring#default-roles) voor meer informatie.

   ```text
   curl --request POST \
     --url https://admin.hlx.page/config/<your-github-org>/sites/<your-aem-project>/access.json \
     --header 'Content-Type: application/json' \
     --header 'x-auth-token: <your-token>' \
     --data '{
       "admin": {
           "role": {
               "admin": [
                   "<email>@<domain>.<tld>"
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

### AEM-configuratie bijwerken {#update-aem}

Nu ben je klaar om de benodigde wijzigingen aan te brengen in je Edge Delivery Services in AEM.

1. Teken in de auteursinstantie van AEM en ga naar **Hulpmiddelen** -> **de Diensten van de Wolk** -> **Configuratie van Edge Delivery Services** en selecteer de configuratie die automatisch voor uw plaats werd gecreeerd en tikken of **Eigenschappen** in de hulpmiddelbar klikken.
1. In het **venster van de Configuratie van Edge Delivery Services**, verander projecttype in **aem.live met repoless config opstelling** en ontvang of klik **sparen &amp; dicht**.
   ![ Configuratie van Edge Delivery Services ](/help/edge/wysiwyg-authoring/assets/repoless/edge-delivery-services-configuration.png)
1. Ga terug naar uw site met de Universal Editor en zorg ervoor dat deze nog steeds correct wordt weergegeven.
1. Wijzig enkele inhoud en publiceer deze opnieuw.
1. Ga naar de gepubliceerde site op `https://main--<your-aem-project>--<your-github-org>.aem.page/` en controleer of de wijzigingen correct zijn doorgevoerd.

Uw project is nu ingesteld voor onophoudelijk gebruik.

## Volgende stappen {#next-steps}

Nu uw basissite is geconfigureerd voor onophoudelijk gebruik, kunt u extra sites maken die gebruikmaken van dezelfde codebasis. Raadpleeg de volgende documentatie, afhankelijk van uw gebruiksscenario.

* [Meerdeloos beheer van sites](/help/edge/wysiwyg-authoring/repoless-msm.md)
* [Stage- en Prod-omgevingen zonder weerstand](/help/edge/wysiwyg-authoring/repoless-stage-prod.md)
* [Siteverificatie voor het ontwerpen van inhoud](/help/edge/wysiwyg-authoring/site-authentication.md)

## Problemen oplossen {#troubleshooting}

Het meest voorkomende probleem dat u tegenkomt na het configureren van het gebruiksscenario voor onophoudelijk gebruik, is dat pagina&#39;s in de Universal Editor niet meer worden gerenderd of dat u een witte pagina of een algemeen AEM as a Cloud Service-foutbericht ontvangt. In dergelijke gevallen:

* De bron van de weergegeven pagina weergeven.
   * Is er eigenlijk iets gerenderd (correcte HTML head met `scripts.js`, `aem.js`, en redacteurs-verwante JSON dossiers)?
* Controleer de AEM `error.log` van de auteurinstantie op uitzonderingen.
   * De meest voorkomende kwestie is dat de paginacomponent met 404 fouten ontbreekt.
   * `config.json or paths.json` kan niet worden geladen
   * `component-definition.json` enz. kan niet worden geladen
