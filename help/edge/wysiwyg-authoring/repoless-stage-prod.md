---
title: Stage- en Prod-omgevingen zonder weerstand
description: Leer hoe u afzonderlijke sites kunt instellen voor uw testomgeving en productieomgeving, waarbij u op een onophoudelijke manier één codebasis gebruikt.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 701bd9bc-30e8-4654-8248-a06d441d1504
source-git-commit: 42218450ab03201c69c59053f720954183f4b652
workflow-type: tm+mt
source-wordcount: '654'
ht-degree: 0%

---

# Stage- en Prod-omgevingen zonder weerstand {#repoless-stage-prod}

Leer hoe u afzonderlijke sites kunt instellen voor uw testomgeving en productieomgeving, waarbij u op een onophoudelijke manier één codebasis gebruikt.

## Overzicht {#overview}

U kunt desgewenst een andere site voor uw productieomgeving dan de testomgeving instellen. Het vestigen van een tweede plaats voor een afzonderlijke het opvoeren en productieconfiguratie is gelijkaardig aan de [ opstelling die voor multi plaatsbeheer wordt vereist.](/help/edge/wysiwyg-authoring/repoless-msm.md) In feite kan het indien nodig worden gecombineerd met MSM-sitestructuren.

In dit document wordt gebruikgemaakt van het typische voorbeeld van afzonderlijke testomgevingen en productieomgevingen. U kunt voor elke gewenste omgeving aparte omgevingen maken.

## Configuratie {#configuration}

In dit document wordt beschreven hoe u een aparte productiesite voor uw project instelt met dezelfde codebasis. De volgende aannames zijn gemaakt.

* De testsite is al ingesteld en u wilt nu een configuratie voor de productiesite maken.
* De inhoudstructuur in AEM ontwerpomgeving is vergelijkbaar.
* Dezelfde padtoewijzingen worden gebruikt voor ophaling en productie.

In dit voorbeeld, veronderstellen wij dat een productiesite reeds voor het geroepen project is gecreeerd wknd waarvan de repo GitHub ook wknd wordt genoemd.

Er zijn twee stappen aan het vormen van een afzonderlijke productiesite.

1. [Maak nieuwe Edge Delivery Services voor uw productieomgeving.](#create-edge-site)
1. [Werk de cloudconfiguratie bij in AEM voor uw productiesite.](#update-cloud-configuration)

### Nieuwe Edge Delivery Services-sites maken voor uw productieomgeving {#create-edge-site}

1. Haal het auteur-token en de technische account voor uw programma op.
   * Gelieve te zien het document **Hergebruikende Code over Plaatsen** voor details op hoe te [ uw toegangstoken ](/help/edge/wysiwyg-authoring/repoless.md#access-token) en de [ technische rekening ](/help/edge/wysiwyg-authoring/repoless.md#access-control) voor uw programma verkrijgen.
1. Creeer een nieuwe plaats door de volgende vraag aan de configuratieservice te maken. Overweeg:
   * De projectnaam in de POST-URL moet de nieuwe sitenaam zijn die u maakt. In dit voorbeeld is dit `wknd-prod` .
   * De `code` -configuratie moet dezelfde zijn als u hebt gebruikt voor het maken van het project.
   * `content` > `source` > `url` moet worden aangepast aan de naam van de nieuwe site die u maakt. In dit voorbeeld is dit `wknd-prod` .
   * De naam van de site in de URL van de POST moet dus gelijk zijn aan de naam van de site in `content` > `source` > `url` .

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
                       "*@adobe.com"
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

### Cloud Configurations bijwerken in AEM voor uw productiesite {#update-cloud-configuration}

Uw AEM moet worden geconfigureerd om de nieuwe Edge Delivery-sites te gebruiken die u in de vorige sectie hebt gemaakt voor een specifieke productiesite. In dit voorbeeld moet inhoud onder `/content/wknd` in uw productieomgeving weten of u de `wknd-prod` -site wilt gebruiken die u hebt gemaakt.

1. Teken in de AEM productieinstantie en ga naar **Hulpmiddelen** -> **Cloud Servicen** -> **Configuratie van Edge Delivery Services**.
1. Selecteer de configuratie die automatisch voor uw project werd gecreeerd.
1. Tik of klik **Eigenschappen** in de hulpmiddelbar.
1. In het **venster van de Configuratie van Edge Delivery Services**:
   * Verstrek uw organisatie GitHub op het **gebied van de Organisatie**.
   * Wijzig de sitenaam in de naam van de site die u in de vorige sectie hebt gemaakt. In dit geval is dat `wknd-prod` .
   * Het projecttype van de verandering in **aem.live met repoless config opstelling**.
1. Tik of klik **sparen &amp; sluit**.

## Uw instellingen controleren {#verify}

Nu u alle noodzakelijke configuratieveranderingen hebt aangebracht, verifieer dat alles zoals verwacht werkt.

1. Meld u aan bij de ontwerpinstantie voor AEM productie.
1. Navigeer aan de **Console van Plaatsen** door **Navigatie** te gaan -> **Plaatsen**.
1. Selecteer een pagina op uw site.
1. Tik of klik **uitgeven** in de toolbar.
1. Zorg ervoor dat de pagina correct wordt weergegeven in de Universal Editor en dat deze dezelfde code gebruikt als de hoofdmap van de site.
1. Wijzig de pagina en publiceer deze opnieuw.
1. Ga naar de site met nieuwe Edge Delivery Services voor die pagina op `https://main--wknd-prod--<your-github-org>.aem.page` .

Als u de aangebrachte wijzigingen ziet, werkt de afzonderlijke installatie van de productiesite correct.
