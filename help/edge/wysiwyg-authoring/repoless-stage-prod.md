---
title: Stage- en Prod-omgevingen zonder weerstand
description: Leer hoe u afzonderlijke sites kunt instellen voor uw testomgeving en productieomgeving, waarbij u op een onophoudelijke manier één codebasis gebruikt.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 701bd9bc-30e8-4654-8248-a06d441d1504
source-git-commit: c9d0d3cd7e18b56db36a379b63f8fb48e18a40db
workflow-type: tm+mt
source-wordcount: '747'
ht-degree: 0%

---

# Stage- en Prod-omgevingen zonder weerstand {#repoless-stage-prod}

Leer hoe u afzonderlijke sites kunt instellen voor uw testomgeving en productieomgeving, waarbij u op een onophoudelijke manier één codebasis gebruikt.

## Overzicht {#overview}

U kunt desgewenst een andere site voor uw productieomgeving dan de testomgeving instellen. Vestiging een tweede plaats voor een afzonderlijke het opvoeren en productieopstelling is gelijkaardig aan de [ opstelling die voor multi plaatsbeheer ](/help/edge/wysiwyg-authoring/repoless-msm.md) wordt vereist. In feite, kan het met MSM plaatsstructuren worden gecombineerd indien vereist.

In dit document wordt gebruikgemaakt van het typische voorbeeld van afzonderlijke testomgevingen en productieomgevingen. U kunt voor elke gewenste omgeving aparte omgevingen maken.

## Vereisten {#requirements}

Als u werkgebied- en productieomgevingen zonder geheugen wilt configureren, moet u eerst de volgende taken uitvoeren:

* Dit document veronderstelt dat u reeds een plaats voor uw project hebt gecreeerd dat op de [ Begonnen Gids van de Ontwikkelaar wordt gebaseerd die voor de Authoring van WYSIWYG met de gids van Edge Delivery Services.](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md)
* U moet reeds [ toegelaten de repoless eigenschap voor uw project hebben.](/help/edge/wysiwyg-authoring/repoless.md)

## Configuratie {#configuration}

In dit document wordt beschreven hoe u een aparte productiesite voor uw project instelt met dezelfde codebasis. De volgende aannames zijn gemaakt.

* De testsite is al ingesteld en u wilt nu een configuratie voor de productiesite maken.
* De inhoudsstructuur in AEM-authoring is vergelijkbaar.
* Dezelfde padtoewijzingen worden gebruikt voor ophaling en productie.

In dit voorbeeld, veronderstellen wij dat een productiesite reeds voor het geroepen project is gecreeerd wknd waarvan de repo GitHub ook wknd wordt genoemd.

Er zijn twee stappen aan het vormen van een afzonderlijke productiesite.

1. [ creeer nieuwe plaatsen van Edge Delivery Services voor uw productiemilieu ](#create-edge-site).
1. [ de wolkenconfiguratie van de Update in AEM voor uw productiesite ](#update-cloud-configuration).

### Nieuwe Edge Delivery Services-sites maken voor uw productieomgeving {#create-edge-site}

1. Haal het auteur-token en de technische account voor uw programma op.
   * Gelieve te zien het document **Hergebruikende Code over Plaatsen** voor details op hoe te [ uw toegangstoken ](/help/edge/wysiwyg-authoring/repoless.md#access-token) en de [ technische rekening ](/help/edge/wysiwyg-authoring/repoless.md#access-control) voor uw programma verkrijgen.
1. Creeer een nieuwe plaats door de volgende vraag aan de configuratieservice te maken. Overweeg:
   * De projectnaam in POST URL moet de nieuwe plaatsnaam zijn u creeert. In dit voorbeeld is dit `wknd-prod` .
   * De `code` -configuratie moet dezelfde zijn als u hebt gebruikt voor het maken van het project.
   * `content` > `source` > `url` moet worden aangepast aan de naam van de nieuwe site die u maakt. In dit voorbeeld is dit `wknd-prod` .
   * De naam van de site in de URL POST en `content` > `source` > `url` moeten dus gelijk zijn.
   * Pas het `admin` -blok aan om de gebruikers te definiëren die volledige beheertoegang tot de site moeten hebben.
      * Het is een array met e-mailadressen.
      * U kunt jokerteken `*` gebruiken.
      * Zie het document [ Vormende Authentificatie voor Auteurs ](https://www.aem.live/docs/authentication-setup-authoring#default-roles) voor meer informatie.

   ```text
   curl --request POST \
     --url https://admin.hlx.page/config/<your-github-org>/sites/wknd-prod.json \
     --header 'x-auth-token: <your-token>' \
     --header 'Content-Type: application/json' \
     --data '{
       "code": {
           "owner": "<your-github-org>",
           "repo": "wknd",
           "source": {
               "type": "github",
               "url": "https://github.com/<your-github-org>/wknd"
           }
       },
       "content": {
           "source": {
               "url": "https://author-p<programID>-e<environmentID>.adobeaemcloud.com/bin/franklin.delivery/<your-github-org>/wknd-prod/main",
               "type": "markup",
               "suffix": ".html"
           }
       },
       "access": {
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
       }
   }'
   ```

1. Voeg de wegafbeelding voor uw nieuwe plaats toe door de volgende vraag aan de configuratieservice te maken.

   ```text
   curl --request POST \
     --url https://admin.hlx.page/config/<your-github-org>/sites/wknd-prod/public.json \
     --header 'x-auth-token: <your-token>' \
     --header 'Content-Type: application/json' \
     --data '{
       "paths": {
           "mappings": [
               "/content/wknd/:/"
           ],
           "includes": [
               "/content/wknd/"
           ]
       }
   }'
   ```

Controleer of de openbare configuratie van uw nieuwe site werkt door `https://main--wknd-prod--<your-github-org>.aem.page/config.json` aan te roepen en de inhoud van de geretourneerde JSON te controleren.

### Cloud Configurations in AEM bijwerken voor uw productiesite {#update-cloud-configuration}

Uw productie-AEM moet zo zijn geconfigureerd dat de nieuwe Edge Delivery-sites die u in de vorige sectie hebt gemaakt, worden gebruikt voor een specifieke productiesite. In dit voorbeeld moet inhoud onder `/content/wknd` in uw productieomgeving weten of u de `wknd-prod` -site wilt gebruiken die u hebt gemaakt.

1. Teken in de de productieinstantie van AEM en ga naar **Hulpmiddelen** -> **de Diensten van de Wolk** -> **Configuratie van Edge Delivery Services**.
1. Selecteer de configuratie die automatisch voor uw project werd gecreeerd.
1. Tik of klik **Eigenschappen** in de hulpmiddelbar.
1. In het **venster van de Configuratie van Edge Delivery Services**:
   * Verstrek uw organisatie GitHub op het **gebied van de Organisatie**.
   * Wijzig de sitenaam in de naam van de site die u in de vorige sectie hebt gemaakt. In dit geval is dat `wknd-prod` .
   * Het projecttype van de verandering in **aem.live met repoless config opstelling**.
1. Tik of klik **sparen &amp; sluit**.

## Uw instellingen controleren {#verify}

Nu u alle noodzakelijke configuratieveranderingen hebt aangebracht, verifieer dat alles zoals verwacht werkt.

1. Meld u aan bij uw AEM-productieontwerpinstantie.
1. Navigeer aan de **Console van Plaatsen** door **Navigatie** te gaan -> **Plaatsen**.
1. Selecteer een pagina op uw site.
1. Tik of klik **uitgeven** in de toolbar.
1. Zorg ervoor dat de pagina correct wordt weergegeven in de Universal Editor en dat deze dezelfde code gebruikt als de hoofdmap van de site.
1. Wijzig de pagina en publiceer deze opnieuw.
1. Ga naar de nieuwe Edge Delivery Services-site voor die pagina op `https://main--wknd-prod--<your-github-org>.aem.page` .

Als u de aangebrachte wijzigingen ziet, werkt de afzonderlijke installatie van de productiesite correct.
