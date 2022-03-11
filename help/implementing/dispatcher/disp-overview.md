---
title: Dispatcher in de cloud
description: 'Dispatcher in de cloud '
feature: Dispatcher
exl-id: 6d78026b-687e-434e-b59d-9d101349a707
source-git-commit: 4be76f19c27aeab84de388106a440434a99a738c
workflow-type: tm+mt
source-wordcount: '916'
ht-degree: 1%

---

# Dispatcher in de cloud {#Dispatcher-in-the-cloud}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_dispoverview"
>title="Dispatcher in de cloud"
>abstract="Op deze pagina wordt beschreven hoe u de verzendingsprogramma&#39;s, de ondersteunde apache-modules kunt downloaden en uitpakken. Ook vindt u een overzicht op hoog niveau van de oude en flexibele modi."

## Inleiding {#apache-and-dispatcher-configuration-and-testing}

Deze pagina beschrijft de verzendingsprogramma&#39;s en hoe u deze kunt downloaden en uitpakken, de ondersteunde apache-modules en biedt een overzicht op hoog niveau van de oude en flexibele modi. Daarnaast zijn er meer verwijzingen naar validatie en foutopsporing en naar AEM as a Cloud Service migratie van de Dispatcher-configuratie van AMS naar

## Verzendgereedschappen {#dispatcher-sdk}

De Dispatcher Tools maken deel uit van de algemene AEM as a Cloud Service SDK en bieden:

* Een vanilla-bestandsstructuur met de configuratiebestanden die moeten worden opgenomen in een toegewezen project voor Dispatcher.
* Tooling voor klanten om te bevestigen dat de configuratie van de Verzender slechts AEM as a Cloud Service gesteunde richtlijnen omvat.        Bovendien controleert het gereedschap ook of de syntaxis correct is, zodat de pijn correct kan beginnen.
* Een Docker-afbeelding waarmee de Dispatcher lokaal wordt weergegeven.

## De gereedschappen downloaden en uitpakken {#extracting-the-sdk}

De Dispatcher-gereedschappen maken deel uit van de [as a Cloud Service SDK AEM](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md), kan worden gedownload van een ZIP-bestand op het [Softwaredistributie](https://downloads.experiencecloud.adobe.com/content/software-distribution/en/aemcloud.html) portaal. Elke nieuwe configuratie die beschikbaar is in die nieuwe versie van Dispatcher Tools kan worden gebruikt om te worden geïmplementeerd in Cloud-omgevingen waarop die versie van AEM in de cloud of hoger wordt uitgevoerd.

Pak de SDK uit, die de Dispatcher Tools voor zowel macOS, Linux als Windows bundelt.

**Voor macOS/Linux**, maakt u het artefact van het gereedschap Dispatcher uitvoerbaar en voert u dit uit. De Dispatcher Tools-bestanden worden automatisch geëxtraheerd onder de map waarin u het hebt opgeslagen (waar `version` is de versie van de Dispatcher Tools).

```bash
$ chmod +x aem-sdk-dispatcher-tools-<version>-unix.sh
$ ./aem-sdk-dispatcher-tools-<version>-unix.sh
Verifying archive integrity...  100%   All good.
Uncompressing aem-sdk-dispatcher-tools-<version>-unix.sh 100%
```

**Voor Windows**, haalt u het ZIP-archief van Dispatcher Tooling uit.

## Validatie en foutopsporing met de Dispatcher Tools {#validation-debug}

De dispatcherhulpmiddelen worden gebruikt om de configuratie van de Verzender van uw project te bevestigen en te zuiveren. Leer meer over hoe te om die hulpmiddelen op de pagina&#39;s te gebruiken die hieronder worden vermeld, op basis van of de de vraagersconfiguratie van uw project op flexibele wijze of erfeniswijze gestructureerd is:

* **Flexibele modus** - de aanbevolen modus en de standaardinstelling voor [AEM archetype 28](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=en) en hoger, die ook wordt gebruikt door Cloud Manager voor nieuwe omgevingen die zijn gemaakt na de release van Cloud Manager 2021.7.0. Klanten kunnen deze modus activeren door de map en het bestand toe te voegen `opt-in/USE_SOURCES_DIRECTLY`. Door deze flexibelere modus te gebruiken, zijn er geen beperkingen in de bestandsstructuur onder de map rewrites waarvoor in de oude modus slechts één bestand nodig was `rewrite.rules` bestand. Bovendien is er geen beperking op het aantal regels dat u kunt toevoegen. Zie voor meer informatie over de mapstructuur en lokale validatie [Validatie en foutopsporing met Dispatcher Tools](/help/implementing/dispatcher/validation-debug.md).

* **Oudere modus** - voor details over de omslagstructuur en lokale bevestiging voor de verouderde wijze van de configuratie van de verzender [Validatie en foutopsporing met Dispatcher Tools (verouderd)](/help/implementing/dispatcher/validation-debug-legacy.md)

Voor meer informatie over hoe te van het model van de erfenisconfiguratie aan flexibelere te migreren, die van AEM archetype 28 wordt voorzien, zie [deze documentatie](/help/implementing/dispatcher/validation-debug.md#migrating).

## Ondersteunde Apache-modules {#supported-directives}

In de onderstaande tabel staan de ondersteunde apache-modules:

| Modulenaam | Referentiepagina |
|---|---|
| `core` | [https://httpd.apache.org/docs/2.4/mod/core.html](https://httpd.apache.org/docs/2.4/mod/core.html) |
| `mod_access_compat` | [https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html) |
| `mod_alias` | [https://httpd.apache.org/docs/2.4/mod/mod_alias.html](https://httpd.apache.org/docs/2.4/mod/mod_alias.html) |
| `mod_allowmethods` | [https://httpd.apache.org/docs/2.4/mod/mod_allowmethods.html](https://httpd.apache.org/docs/2.4/mod/mod_allowmethods.html) |
| `mod_authn_core` | [https://httpd.apache.org/docs/2.4/mod/mod_authn_core.html](https://httpd.apache.org/docs/2.4/mod/mod_authn_core.html) |
| `mod_authn_file` | [https://httpd.apache.org/docs/2.4/mod/core.html](https://httpd.apache.org/docs/2.4/mod/mod_authn_file.html) |
| `mod_authz_core` | [https://httpd.apache.org/docs/2.4/mod/core.html](https://httpd.apache.org/docs/2.4/mod/mod_authz_core.html) |
| `mod_authz_groupfile` | [https://httpd.apache.org/docs/2.4/mod/mod_authz_groupfile.html](https://httpd.apache.org/docs/2.4/mod/mod_authz_groupfile.html) |
| `mod_deflate` | [https://httpd.apache.org/docs/2.4/mod/mod_deflate.html](https://httpd.apache.org/docs/2.4/mod/mod_deflate.html) |
| `mod_dir` | [https://httpd.apache.org/docs/2.4/mod/mod_dir.html](https://httpd.apache.org/docs/2.4/mod/mod_dir.html) |
| `mod_env` | [https://httpd.apache.org/docs/2.4/mod/mod_env.html](https://httpd.apache.org/docs/2.4/mod/mod_env.html) |
| `mod_filter` | [https://httpd.apache.org/docs/2.4/mod/mod_filter.html](https://httpd.apache.org/docs/2.4/mod/mod_filter.html) |
| `mod_headers` | [https://httpd.apache.org/docs/2.4/mod/mod_headers.html](https://httpd.apache.org/docs/2.4/mod/mod_headers.html) |
| `mod_mime` | [https://httpd.apache.org/docs/2.4/mod/mod_mime.html](https://httpd.apache.org/docs/2.4/mod/mod_mime.html) |
| `mod_proxy` | [https://httpd.apache.org/docs/2.4/mod/mod_proxy.html](https://httpd.apache.org/docs/2.4/mod/mod_proxy.html) |
| `mod_proxy_http` | [https://httpd.apache.org/docs/2.4/mod/mod_proxy_http.html](https://httpd.apache.org/docs/2.4/mod/mod_proxy_http.html) |
| `mod_remoteip` | [https://httpd.apache.org/docs/2.4/mod/mod_remoteip.html](https://httpd.apache.org/docs/2.4/mod/mod_remoteip.html) |
| `mod_reqtimeout` | [https://httpd.apache.org/docs/2.4/mod/mod_reqtimeout.html](https://httpd.apache.org/docs/2.4/mod/mod_reqtimeout.html) |
| `mod_rewrite` | [https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html](https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html) |
| `mod_security` | [https://modsecurity.org/](https://modsecurity.org/) |
| `mod_setenvif` | [https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html](https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html) |
| `mod_ssl (only the SSLProxyEngine directive)` | [https://httpd.apache.org/docs/2.4/mod/mod_ssl.html#sslproxyengine](https://httpd.apache.org/docs/2.4/mod/mod_ssl.html#sslproxyengine) |
| `mod_substitute` | [https://httpd.apache.org/docs/2.4/mod/mod_substitute.html](https://httpd.apache.org/docs/2.4/mod/mod_substitute.html) |
| `mod_userdir` | [https://httpd.apache.org/docs/2.4/mod/mod_userdir.html](https://httpd.apache.org/docs/2.4/mod/mod_userdir.html) |

Klanten kunnen geen arbitraire modules toevoegen, maar er kunnen in de toekomst wel extra modules worden overwogen. Klanten kunnen de lijst met instructies vinden die beschikbaar is voor een bepaalde versie van Dispatcher door de opdracht lijst van gewenste personen van de validator uit te voeren in de SDK.

De instructies die zijn toegestaan in Apache-configuratiebestanden, kunnen worden weergegeven door de opdracht lijst van gewenste personen van de validator uit te voeren:

```
$ validator allowlist
Cloud manager validator 2.0.4
 
Allowlisted directives:
  <Directory>
  ...
  
```

## Mapstructuur {#folder-structure}

De mappenstructuur van de applaus en de verzender van het project verschilt enigszins, afhankelijk van de modus die het project gebruikt, zoals beschreven in het dialoogvenster [Validatie en foutopsporing met de Dispatcher Tools](#validation-debug) hierboven.

## De Dispatcher-configuratie migreren van AMS {#ams-aem}

Voor meer informatie over hoe u de configuratie Dispatcher van AMS naar AEM as a Cloud Service kunt migreren, raadpleegt u de [De Dispatcher-configuratie migreren van AMS naar AEM](/help/implementing/dispatcher/ams-aem.md) as a Cloud Service pagina.
