---
title: URL-omleidingen zonder pijplijn
description: Leer hoe u 301 of 302 omleidingen declareert zonder toegang tot Git- of Cloud Manager-pijpleidingen.
feature: Dispatcher
role: Admin
source-git-commit: 36b7d72f24bd60ad94762c9c9937105bea6e31b6
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 0%

---

# URL-omleidingen zonder pijplijn {#pipeline-free-redirects}

Om verschillende redenen herschrijven organisaties URL&#39;s op een manier die leidt tot een omleiding van 301 (of 302), wat betekent dat de browser wordt omgeleid naar een andere pagina.

De scenario&#39;s omvatten:

* Een verwijderde HTML-pagina, zodat de gebruiker naar een vervangende pagina (soms de startpagina) gaat en geen `404 Page Not Found` -fout ziet.
* Een hernoemde HTML-pagina.
* SEO-optimalisatie.

AEM as a Cloud Service biedt [ verscheidene benaderingen ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/foundation/administration/url-redirection) aan om cliënt-zij omleidingen uit te voeren, maar de strategie die in dit artikel wordt beschreven, zonder pijpleiding is omleiding, is een goede keus wanneer:

* De mensen die redirects handhaven zijn bedrijfsgebruikers, die niet de noodzakelijke toegang hebben om dossierveranderingen in broncontrole of de mogelijkheid vast te leggen om een Cloud Manager web-tier configuratiepijplijn uit te voeren.
* Het aantal omleidingen varieert van een paar tot tienduizenden.
* U wilt de optie van een gebruikersinterface, of als douaneproject worden gecreeerd of door [ ACS te gebruiken herschrijft de Bevelen van de Kaart Manager ](https://adobe-consulting-services.github.io/acs-aem-commons/features/redirect-map-manager/index.html).

De kern van deze functie is de mogelijkheid voor AEM Apache/Dispatcher om een of meer kaartbestanden te laden (of opnieuw te laden) die op een opgegeven locatie in de publicatieopslagplaats zijn geplaatst. Het is belangrijk om te vermelden dat hoe de dossiers daar krijgen buiten het werkingsgebied van deze eigenschap is maar u kunt één van de volgende methodes overwegen:

* De kaart voor herschrijven als een element invoegen in de gebruikersinterface van de auteur en deze publiceren.
* Het installeren van de [ ACS-Bevelen herschrijft de Manager van de Kaart ](https://adobe-consulting-services.github.io/acs-aem-commons/features/redirect-map-manager/index.html), die een gebruikersinterface omvat om de url in kaart te brengen en kan ook het herschrijven kaartdossier publiceren.
* Volledige flexibiliteit door een aangepaste toepassing te schrijven. U kunt bijvoorbeeld een gebruikersinterface of opdrachtregelinterface gebruiken om de URL-toewijzingen te beheren, of een formulier om een herschrijfmap te uploaden, die vervolgens AEM API&#39;s gebruikt om het kaartbestand voor herschrijven te publiceren.

>[!NOTE]
> Deze eigenschap vereist AEM versie **18311 of hoger**.

## De kaart voor herschrijven {#rewrite-map}

De kaart voor herschrijven wordt opnieuw geladen (indien gewijzigd) door de Apache HTTP-server standaard elke 300 seconden (de waarde kan worden geconfigureerd). Het dossierformaat zou de duidelijke tekst sleutel-waarde kaart RewriteMap dossierformaat moeten volgen dat in de [ documentatie Apache ](https://httpd.apache.org/docs/2.4/rewrite/rewritemap.html#txt) wordt beschreven.

Er moet een bestand met de naam `managed-rewrite-maps.yaml` worden gemaakt om de locatie van het kaartbestand voor herschrijven op te geven. Dit bestand moet één keer worden geïmplementeerd met de Cloud Manager-stackpijplijn of de weblaagpijplijn. Het dossier moet in de [ src/opt-in ](https://github.com/adobe/aem-project-archetype/tree/develop/src/main/archetype/dispatcher.cloud/src/opt-in) omslag van uw verzender configuratie worden gecreeerd. Zorg ervoor u de [ flexibele structuur van het wijzedossier ](/help/implementing/dispatcher/validation-debug.md#flexible-mode-file-structure) gebruikt.

U kunt het met het volgende patroon vormen:

```
maps:
- name: my.map
  path: <path-in-publish-repository>/redirectmap.txt
```

Als u het kaartbestand voor herschrijven bijvoorbeeld wilt plaatsen door het in te voeren in AEM als een element met de naam `mysite-redirectmap.txt` en het vervolgens te publiceren, kunt u een map opgeven onder `/content/dam` :

```
maps:
- name: my.map
  path: /content/dam/redirectmaps/mysite-redirectmap.txt
```

Vervolgens moet u in een Apache-configuratiebestand zoals `rewrites/rewrite.rules` of `<yourfile>.vhost` het kaartbestand configureren waarnaar wordt verwezen door de eigenschap name (`my.map` in het bovenstaande voorbeeld).

De instructie `RewriteMap` geeft aan dat de gegevens worden opgeslagen in een databasemanagementbestandsindeling (DBM) met behulp van de indeling `sdbm` (simple DBM).

De rest van de configuratie is afhankelijk van de indeling van de `redirectmap.txt` . De eenvoudigste indeling, die in het onderstaande voorbeeld wordt getoond, is een-op-een-toewijzing tussen de oorspronkelijke URL en de toegewezen URL:

```
# RewriteMap from managed rewrite maps
RewriteMap map.foo dbm=sdbm:/tmp/rewrites/my.map
RewriteCond ${map.foo:$1} !=""
RewriteRule ^(.*)$ ${map.foo:$1|/} [L,R=301]
```


## Overwegingen {#considerations}

Houd rekening met het volgende:

* Wanneer een kaart voor herschrijven wordt geladen, wordt Apache standaard gestart zonder te wachten tot het volledige kaartbestand of de volledige kaartbestanden zijn geladen. Er kunnen dus tijdelijke inconsistenties optreden totdat de volledige kaart of kaarten zijn geladen. Deze instelling kan worden gewijzigd, zodat Apache wacht tot de inhoud van de volledige kaart is geladen, maar het starten van Apache duurt langer. Als u dit gedrag wilt wijzigen zodat Apache wacht, voegt u `wait:true` toe aan het `managed-rewrite-maps.yaml` -bestand.
* Voeg `ttl: <integer>` toe aan het `managed-rewrite-maps.yaml` -bestand om de frequentie tussen de laadbewerkingen te wijzigen. Bijvoorbeeld: `ttl: 120` .
* Apache heeft een lengtelimiet van 1024 voor enkelvoudige vermeldingen RewriteMap.
