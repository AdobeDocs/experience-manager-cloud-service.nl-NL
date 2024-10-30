---
title: Pipeline-free URL Redirects
description: Learn how to declare 301 or 302 redirects without access to Git or Cloud Manager pipelines.
feature: Dispatcher
role: Admin
source-git-commit: 567c75f456f609dbc254753b439151d0f4100bc0
workflow-type: tm+mt
source-wordcount: '653'
ht-degree: 0%

---

# Pipeline-free URL Redirects {#pipeline-free-redirects}

>[!NOTE]
>This feature is not yet released.

For various reasons, organizations rewrite URLs in a way that causes a 301 (or 302) redirect, meaning that the browser is redirected to a different page.

Scenarios include:

* `404 Page Not Found`
* Een hernoemde HTML-pagina.
* SEO-optimalisatie.

AEM als Dienst van de Wolk biedt [ verscheidene benaderingen ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/foundation/administration/url-redirection) aan om cliënt-zij omleidingen uit te voeren, maar de strategie die in dit artikel wordt beschreven, zonder pijpleiding-vrije redirects, is een goede keus wanneer:

* De mensen die de omleidingen onderhouden zijn zakelijke gebruikers, die niet de noodzakelijke toegang hebben om bestandswijzigingen vast te leggen in broncontrole of de mogelijkheid om een configuratiepijplijn voor de weblaagconfiguratie van Cloud Manager uit te voeren.
* The number of redirects ranges from a few to tens of thousands.
* [](https://adobe-consulting-services.github.io/acs-aem-commons/features/redirect-map-manager/index.html)

The core of this feature is the ability for AEM Apache/Dispatcher to load (or reload) one or more rewrite map files that have been placed in a specified location in the publish repository. It is important to mention that how the files get there is outside the scope of this feature but you can consider one of the following methods:

* Ingesting the rewrite map as an asset in the author user interface and publishing it.
* [](https://adobe-consulting-services.github.io/acs-aem-commons/features/redirect-map-manager/index.html)
* Full flexibility by writing a custom application. U kunt bijvoorbeeld een gebruikersinterface of opdrachtregelinterface gebruiken om de URL-toewijzingen te beheren of een formulier om een herschrijfkaart te uploaden, dat vervolgens AEM API&#39;s gebruikt om het rewrite-mapbestand te publiceren.

>[!NOTE]
> Deze eigenschap vereist AEM versie **18311 of hoger**.

## De kaart voor herschrijven {#rewrite-map}

De herschrijfkaart wordt standaard opnieuw geladen (indien gewijzigd) door de Apache HTTP-server om de 300 seconden (de waarde kan worden geconfigureerd). Het dossierformaat zou de onbewerkte tekst sleutel-waarde kaart RewriteMap dossierformaat moeten volgen dat in de [ documentatie van Apache ](https://httpd.apache.org/docs/2.4/rewrite/rewritemap.html#txt) wordt beschreven.

`managed-rewrite-maps.yaml` [](https://github.com/adobe/aem-project-archetype/tree/develop/src/main/archetype/dispatcher.cloud/src/opt-in) [](/help/implementing/dispatcher/validation-debug.md#flexible-mode-file-structure)

You can configure it with the following pattern:

```
maps:
- name: my.map
  path: <path-in-publish-repository>/redirectmap.txt
```

`mysite-redirectmap.txt``/content/dam`

```
maps:
- name: my.map
  path: /content/dam/redirectmaps/mysite-redirectmap.txt
```

`rewrites/rewrite.rules``<yourfile>.vhost``my.map`

`RewriteMap``sdbm`

`redirectmap.txt` De eenvoudigste notatie, die in het onderstaande voorbeeld wordt getoond, is een-op-een-toewijzing tussen de oorspronkelijke URL en de toegewezen URL:

```
# RewriteMap from managed rewrite maps
RewriteMap map.foo dbm=sdbm:/tmp/rewrites/my.map
RewriteCond ${map.foo:$1} !=""
RewriteRule ^(.*)$ ${map.foo:$1|/} [L,R=301]
```


## Overwegingen {#considerations}

Houd rekening met het volgende:

* Bij het laden van een herschrijfkaart wordt Apache standaard gestart zonder te wachten tot het volledige kaartbestand of de volledige kaartbestanden zijn geladen. Er kunnen dus tijdelijke inconsistenties zijn totdat de volledige kaart(en) is/zijn geladen. Deze instelling kan worden gewijzigd zodat Apache wacht totdat de volledige kaartinhoud is geladen, maar het starten van Apache duurt langer. Als u dit gedrag wilt wijzigen zodat Apache wacht, voegt u `wait:true` toe aan het `managed-rewrite-maps.yaml` -bestand.
* `ttl: <integer>``managed-rewrite-maps.yaml` `ttl: 120`
* Apache has an 1024 length limit for RewriteMap single entries.
