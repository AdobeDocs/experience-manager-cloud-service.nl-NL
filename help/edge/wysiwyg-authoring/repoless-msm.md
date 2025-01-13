---
title: Meerdeloos beheer van sites
description: Leer beste praktijkaanbevelingen op hoe te om een project op een repoless manier met gelokaliseerde plaatsen te vestigen die hefboomwerking één enkele codebasis, elk omhoog door Edge Delivery Services worden gediend.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: f6b861ed-18e4-4c81-92d2-49fadfe4669a
source-git-commit: 42218450ab03201c69c59053f720954183f4b652
workflow-type: tm+mt
source-wordcount: '1222'
ht-degree: 0%

---

# Meerdeloos beheer van sites {#repoless-msm}

Leer beste praktijkaanbevelingen op hoe te om een project op een repoless manier met gelokaliseerde plaatsen te vestigen die hefboomwerking één enkele codebasis, elk omhoog door Edge Delivery Services worden gediend.

## Overzicht {#overview}

[ Multisite Manager (MSM) ](/help/sites-cloud/administering/msm/overview.md) en zijn Levende eigenschappen van het Exemplaar laten u toe om de zelfde plaatsinhoud in veelvoudige plaatsen te gebruiken, terwijl het toestaan voor variaties. U kunt inhoud één keer ontwerpen en Actieve kopieën maken. MSM onderhoudt levende verhoudingen tussen uw broninhoud en zijn Levende Kopieën zodat wanneer u de broninhoud verandert, de bron en Levende Kopieën kunnen worden gesynchroniseerd.

Met MSM kunt u een volledige inhoudsstructuur voor uw merk maken voor verschillende landinstellingen en talen en de inhoud centraal ontwerpen. Uw gelokaliseerde sites kunnen dan elk door Edge Delivery Services worden geleverd, waarbij een centrale codebasis wordt gebruikt.

## Vereisten {#requirements}

Om MSM in een repoless gebruikscase te vormen, moet u een aantal taken eerst voltooien.

* Dit document veronderstelt dat u reeds een plaats voor uw project hebt gecreeerd dat op de [ Begonnen Gids van de Ontwikkelaar wordt gebaseerd die voor de Authoring van WYSIWYG met Edge Delivery Services ](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md) gids wordt.
* U moet reeds [ toegelaten de repoless eigenschap voor uw project hebben.](/help/edge/wysiwyg-authoring/repoless.md)

## Hoofdletters gebruiken {#use-case}

In dit document wordt ervan uitgegaan dat u al een algemene gelokaliseerde sitestructuur voor uw project hebt gemaakt. Het gebruikt als voorbeeld de volgende structuur voor het merk wknd met een aanwezigheid in Zwitserland en Duitsland.

```text
/content/wknd
/content/wknd/language-masters
/content/wknd/language-masters/en
/content/wknd/language-masters/de
/content/wknd/language-masters/fr
/content/wknd/language-masters/it
/content/wknd/ch
/content/wknd/ch/de
/content/wknd/ch/fr
/content/wknd/ch/it
/content/wknd/ch/en
/content/wknd/de
/content/wknd/de/de
/content/wknd/de/en
```

De inhoud in `language-masters` is de bron van Levende Exemplaren voor de gelokaliseerde plaatsen: Duitsland (`de`) en Zwitserland (`ch`). Het doel van dit document is om plaatsen van Edge Delivery Services tot stand te brengen die allen de zelfde codebasis voor elke gelokaliseerde plaats gebruiken.

## Configuratie {#configuration}

Er zijn verscheidene stappen aan het vormen van MSM repoless gebruiksgeval.

1. [AEM siteconfiguraties bijwerken.](#update-aem-configurations)
1. [Maak nieuwe sites met Edge Delivery Services voor uw gelokaliseerde pagina&#39;s.](#create-edge-sites)
1. [Werk de cloudconfiguratie bij in AEM voor uw gelokaliseerde sites.](#update-cloud-configurations)

### AEM siteconfiguraties bijwerken {#update-aem-configurations}

[ de Configuraties ](/help/implementing/developing/introduction/configurations.md) kunnen van als werkruimten worden gedacht die kunnen worden gebruikt om groepen montages en hun bijbehorende inhoud voor organisatorische doeleinden te verzamelen. Wanneer u een site in AEM maakt, wordt er automatisch een configuratie voor gemaakt.

Over het algemeen wilt u bepaalde inhoud delen tussen sites, zoals:

* Sjablonen die zijn gemaakt van de inhoud in de blauwdruk
* Modellen van inhoudsfragment, doorgeduurd, query&#39;s enzovoort.

U kunt aanvullende configuraties maken om dit delen mogelijk te maken. Voor het wint gebruiksgeval, zouden wij configuraties voor de volgende wegen nodig hebben.

```text
/content/wknd
/content/wknd/ch
/content/wknd/de
```

Namelijk zult u een configuratie voor de wortel van de inhoud van het merk van het wknd (`/content/wknd`) hebben die door de blauwdrukken en een configuratie wordt gebruikt door elke gelokaliseerde plaats (Zwitserland en Duitsland).

1. Meld u aan bij uw AEM ontwerpinstantie.
1. Navigeer aan **Browser van de Configuratie** door **Hulpmiddelen** te gaan -> **Algemeen** -> **Browser van de Configuratie**.
1. Selecteer de configuratie die automatisch voor uw project (in dit geval wint) werd gecreeerd en dan tikken of **klikken creeert** in de toolbar.
1. In **creeer de dialoog van de Configuratie**, verstrek een beschrijvende **Naam** voor uw gelokaliseerde plaats (zoals `Switzerland`) en voor **Titel** gebruik de zelfde titel van de gelokaliseerde grootte (in dit geval `ch`).
1. Selecteer de **eigenschap van de Configuratie van de Wolk 0} {en om het even welke extra eigenschappen u voor uw project zoals** Bewerkbare Malplaatjes **kunt nodig hebben.**
1. Tik of klik **creeer**.

Maak configuraties voor elke gelokaliseerde site die u nodig hebt. In het geval van wint, zou u een configuratie voor `de` evenals naast de `ch` configuratie moeten tot stand brengen.

Zodra de configuraties worden gecreeerd, moet u ervoor zorgen dat de gelokaliseerde plaatsen hen gebruiken.

1. Meld u aan bij uw AEM ontwerpinstantie.
1. Navigeer aan de **Console van Plaatsen** door **Navigatie** te gaan -> **Plaatsen**.
1. Selecteer de gelokaliseerde site, bijvoorbeeld `Switzerland` .
1. Tik of klik **Eigenschappen** in de hulpmiddelbar.
1. In het pagina eigenschappenvenster, selecteer het **Geavanceerde** lusje en onder de **rubriek van de Configuratie**, unselect de optie **Geërft van /content/wknd**, waar `wknd` de plaatswortel is.
1. In **het gebied van de Configuratie van de Wolk**, gebruik wegbrowser om de configuratie te selecteren u voor uw gelokaliseerde plaats zoals `Switzerland` onder `/conf/wknd/ch` creeerde.
1. Tik of klik **sparen &amp; sluit**.

Wijs de respectieve configuraties aan de extra gelokaliseerde plaatsen toe. In het geval van wknd, zou u `/conf/wknd/de` configuratie aan de plaats van Duitsland ook moeten toewijzen.

### Nieuwe sites voor Edge Delivery Services maken voor uw gelokaliseerde pagina&#39;s {#create-edge-sites}

Als u meer sites wilt verbinden met Edge Delivery Services voor een meertalige site-instelling met meerdere regio&#39;s, moet u een nieuwe site aem.live instellen voor elk van uw AEM MSM-sites. Er is een 1:1 verhouding tussen AEM plaatsen MSM en aem.live plaatsen met een gedeelde bewaarplaats van de Git en codebasis.

In dit voorbeeld maken we de site `wknd-ch` voor de Zwitserse aanwezigheid van wint, waarvan de gelokaliseerde inhoud zich onder het AEM `/content/wknd/ch` bevindt.

1. Haal het auteur-token en de technische account voor uw programma op.
   * Gelieve te zien het document **Hergebruikende Code over Plaatsen** voor details op hoe te [ uw toegangstoken ](/help/edge/wysiwyg-authoring/repoless.md#access-token) en de [ technische rekening ](/help/edge/wysiwyg-authoring/repoless.md#access-control) voor uw programma verkrijgen.
1. Creeer een nieuwe plaats door de volgende vraag aan de configuratieservice te maken. Overweeg:
   * De projectnaam in de POST-URL moet de nieuwe sitenaam zijn die u maakt. In dit voorbeeld is dit `wknd-ch` .
   * De `code` -configuratie moet dezelfde zijn als u hebt gebruikt voor het maken van het project.
   * `content` > `source` > `url` moet worden aangepast aan de naam van de nieuwe site die u maakt. In dit voorbeeld is dit `wknd-ch` .
   * De naam van de site in de URL van de POST moet dus gelijk zijn aan de naam van de site in `content` > `source` > `url` .

   ```text
   curl --request POST \
     --url https://admin.hlx.page/config/<your-github-org>/sites/wknd-ch.json \
     --header 'Content-Type: application/json' \
     --header 'x-auth-token: <your-token>' \
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
               "url": "https://author-p<programID>-e<environmentID>.adobeaemcloud.com/bin/franklin.delivery/<your-github-org>/wknd-ch/main",
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
     --url https://admin.hlx.page/config/<your-github-org>/sites/wknd-ch/public.json \
     --header 'Content-Type: application/json' \
     --header 'x-auth-token: <your-token>' \
     --data '{
       "paths": {
           "mappings": [
               "/content/wknd/ch/:/"
           ],
           "includes": [
               "/content/wknd/ch/"
           ]
       }
   }'
   ```

1. Controleer of de openbare configuratie van uw nieuwe site werkt door `https://main--wknd-ch--<your-github-org>.aem.page/config.json` aan te roepen en de inhoud van de geretourneerde JSON te controleren.

Herhaal de stappen om extra gelokaliseerde sites te maken. In het geval van wint, zou u een `wknd-de` plaats voor de Duitse aanwezigheid moeten tot stand brengen.

### Cloudconfiguraties bijwerken in AEM voor uw gelokaliseerde pagina&#39;s {#update-cloud-configurations}

Uw pagina&#39;s in AEM moeten worden geconfigureerd om de nieuwe Edge Delivery-sites te gebruiken die u in de vorige sectie hebt gemaakt voor uw gelokaliseerde aanwezigheid. In dit voorbeeld moet inhoud onder `/content/wknd/ch` weten dat u de `wknd-ch` -site die u hebt gemaakt, kunt gebruiken. Op dezelfde manier moet inhoud onder `/content/wknd/de` de `wknd-de` -site gebruiken.

1. Teken in de AEM auteursinstantie en ga naar **Hulpmiddelen** -> **Cloud Servicen** -> **Configuratie van Edge Delivery Services**.
1. Selecteer de configuratie die automatisch voor uw project en toen de omslag werd gecreeerd die voor de gelokaliseerde pagina werd gecreeerd. In dit geval is dat Zwitserland (`ch`).
1. Tik of klik **creeer** > **Configuratie** in de hulpmiddelbar.
1. In het **venster van de Configuratie van Edge Delivery Services**:
   * Verstrek uw organisatie GitHub op het **gebied van de Organisatie**.
   * Wijzig de sitenaam in de naam van de site die u in de vorige sectie hebt gemaakt. In dit geval is dat `wknd-ch` .
   * Het projecttype van de verandering in **aem.live met repoless config opstelling**.
1. Tik of klik **sparen &amp; sluit**.

## Uw instellingen controleren {#verify}

Nu u alle noodzakelijke configuratieveranderingen hebt aangebracht, verifieer dat alles zoals verwacht werkt.

1. Meld u aan bij uw AEM ontwerpinstantie.
1. Navigeer aan de **Console van Plaatsen** door **Navigatie** te gaan -> **Plaatsen**.
1. Selecteer de gelokaliseerde site, bijvoorbeeld `Switzerland` .
1. Tik of klik **uitgeven** in de toolbar.
1. Zorg ervoor dat de pagina correct wordt weergegeven in de Universal Editor en dat deze dezelfde code gebruikt als de hoofdmap van de site.
1. Wijzig de pagina en publiceer deze opnieuw.
1. Ga naar de site met nieuwe Edge Delivery Services voor die gelokaliseerde pagina op `https://main--wknd-ch--<your-github-org>.aem.page` .

Als u de veranderingen ziet die u aanbracht, werkt uw opstelling MSM behoorlijk.
