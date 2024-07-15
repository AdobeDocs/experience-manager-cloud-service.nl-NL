---
title: Dispatcher in de cloud
description: Meer informatie over Dispatcher-gereedschappen, de ondersteunde Apache-modules en de verouderde en flexibele modi.
feature: Dispatcher
exl-id: 6d78026b-687e-434e-b59d-9d101349a707
role: Admin
source-git-commit: 0e328d013f3c5b9b965010e4e410b6fda2de042e
workflow-type: tm+mt
source-wordcount: '716'
ht-degree: 0%

---

# Dispatcher in de cloud {#Dispatcher-in-the-cloud}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_dispoverview"
>title="Dispatcher in de cloud"
>abstract="Op deze pagina wordt beschreven hoe u de Dispatcher-gereedschappen, de ondersteunde Apache-modules kunt downloaden en uitpakken en wordt een uitgebreid overzicht gegeven van de oude en flexibele modi."

## Inleiding {#apache-and-dispatcher-configuration-and-testing}

Op deze pagina worden de Dispatcher-gereedschappen beschreven, evenals de manier waarop deze kunnen worden gedownload en uitgepakt, de ondersteunde Apache-modules en een uitgebreid overzicht van de oude en flexibele modi. Ook zijn er meer verwijzingen naar validatie en foutopsporing en naar het migreren van de Dispatcher-configuratie van AMS naar AEM as a Cloud Service. <!-- ERROR: NOT FOUND (HTTP ERROR 404) Also, see [this video](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-aem-dispatcher-cloud.html) for additional details about deploying dispatcher files in a cloud service environment. -->

## Dispatcher Tools {#dispatcher-sdk}

De Dispatcher Tools maakt deel uit van de algemene AEM as a Cloud Service SDK en biedt:

* Een vanilla-bestandsstructuur met de configuratiebestanden die moeten worden opgenomen in een toegewezen project voor Dispatcher.
* Klanten kunnen hiermee controleren of de Dispatcher-configuratie alleen door AEM as a Cloud Service ondersteunde instructies bevat. Bovendien controleert de werkbalk of de syntaxis correct is, zodat Apache correct kan worden gestart.
* Een Docker-afbeelding waarmee de Dispatcher lokaal wordt weergegeven.

## De gereedschappen downloaden en uitpakken {#extracting-the-sdk}

De Hulpmiddelen van Dispatcher, een deel van [ AEM as a Cloud Service SDK ](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md), kunnen van een zip dossier bij het [ 3} portaal van de Distributie van de Software worden gedownload. ](https://downloads.experiencecloud.adobe.com/content/software-distribution/en/aemcloud.html) Elke nieuwe configuratie die beschikbaar is in die nieuwe versie van Dispatcher Tools kan worden gebruikt voor implementatie in Cloud-omgevingen waarop die versie van AEM in de cloud of hoger wordt uitgevoerd.

Pak de SDK uit, die Dispatcher Tools voor macOS, Linux® en Windows bundelt.

**voor macOS/Linux**, maak het het hulpmiddelartefact van Dispatcher uitvoerbaar en stel het in werking. De Dispatcher Tools-bestanden worden automatisch geëxtraheerd onder de map waarin u de bestanden hebt opgeslagen (waarbij `version` de versie van de Dispatcher Tools is).

```bash
$ chmod +x aem-sdk-dispatcher-tools-<version>-unix.sh
$ ./aem-sdk-dispatcher-tools-<version>-unix.sh
Verifying archive integrity...  100%   All good.
Uncompressing aem-sdk-dispatcher-tools-<version>-unix.sh 100%
```

**voor Vensters**, haal het het Tooling zip archief van Dispatcher.

## Validatie en foutopsporing met de Dispatcher Tools {#validation-debug}

De Dispatcher-programma&#39;s worden gebruikt om de Dispatcher-configuratie van uw project te valideren en er fouten in op te sporen. Leer meer over hoe te om die hulpmiddelen op de pagina&#39;s te gebruiken die hieronder worden vermeld, gebaseerd op of de configuratie van Dispatcher van uw project op flexibele wijze of erfeniswijze gestructureerd is:

* **Flexibele wijze** - de geadviseerde wijze, en het gebrek voor [ AEM archetype 28 ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) en hoger, dat ook door Cloud Manager voor nieuwe milieu&#39;s wordt gebruikt die na de versie van Cloud Manager 2021.7.0 worden gecreeerd. Klanten kunnen deze modus activeren door de map en het bestand `opt-in/USE_SOURCES_DIRECTLY` toe te voegen. Door deze flexibelere modus te gebruiken, zijn er geen beperkingen in de bestandsstructuur onder de map rewrites waarvoor in de oude modus één `rewrite.rules` -bestand nodig was. Bovendien is er geen beperking op het aantal regels dat u kunt toevoegen. Voor details op omslagstructuur en lokale bevestiging, zie [ Valideren en het Zuiveren gebruikend de Hulpmiddelen van Dispatcher ](/help/implementing/dispatcher/validation-debug.md).

* **Verouderde wijze** - voor details op de omslagstructuur en lokale bevestiging voor de wijze van de configuratieerfenis van Dispatcher, zie [ Bevestigen en het Zuiveren gebruikend de Hulpmiddelen van Dispatcher (Verouderd) ](/help/implementing/dispatcher/validation-debug-legacy.md)

Voor meer informatie over hoe te van het model van de erfenisconfiguratie aan flexibelere te migreren, die van AEM archetype 28 wordt voorzien en daarna, zie [ deze documentatie ](/help/implementing/dispatcher/validation-debug.md#migrating).

## Inhoud verplaatsen {#content-disposition}

Voor de publicatielaag is de standaardinstelling voor het weergeven van lobs een bijlage. Overschrijf dit het plaatsen gebruikend de standaard [ kopbal van de inhoudsomzet ](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Disposition) in Dispatcher.

Hieronder ziet u een voorbeeld van hoe de configuratie eruit moet zien:

```
<LocationMatch "^\/content\/dam.*\.(pdf).*">
 Header unset Content-Disposition
 Header set Content-Disposition inline
</LocationMatch>
```

## Ondersteunde Apache-modules {#supported-directives}

In de onderstaande tabel staan de ondersteunde Apache-modules:

| Modulenaam | Referentiepagina |
|---|---|
| `core` | [ https://httpd.apache.org/docs/2.4/mod/core.html](https://httpd.apache.org/docs/2.4/mod/core.html) |
| `mod_access_compat` | [ https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html) |
| `mod_alias` | [ https://httpd.apache.org/docs/2.4/mod/mod_alias.html](https://httpd.apache.org/docs/2.4/mod/mod_alias.html) |
| `mod_allowmethods` | [ https://httpd.apache.org/docs/2.4/mod/mod_allowmethods.html](https://httpd.apache.org/docs/2.4/mod/mod_allowmethods.html) |
| `mod_authn_core` | [ https://httpd.apache.org/docs/2.4/mod/mod_authn_core.html](https://httpd.apache.org/docs/2.4/mod/mod_authn_core.html) |
| `mod_authn_file` | [ https://httpd.apache.org/docs/2.4/mod/core.html](https://httpd.apache.org/docs/2.4/mod/mod_authn_file.html) |
| `mod_authz_core` | [ https://httpd.apache.org/docs/2.4/mod/core.html](https://httpd.apache.org/docs/2.4/mod/mod_authz_core.html) |
| `mod_authz_groupfile` | [ https://httpd.apache.org/docs/2.4/mod/mod_authz_groupfile.html](https://httpd.apache.org/docs/2.4/mod/mod_authz_groupfile.html) |
| `mod_deflate` | [ https://httpd.apache.org/docs/2.4/mod/mod_deflate.html](https://httpd.apache.org/docs/2.4/mod/mod_deflate.html) |
| `mod_dir` | [ https://httpd.apache.org/docs/2.4/mod/mod_dir.html](https://httpd.apache.org/docs/2.4/mod/mod_dir.html) |
| `mod_env` | [ https://httpd.apache.org/docs/2.4/mod/mod_env.html](https://httpd.apache.org/docs/2.4/mod/mod_env.html) |
| `mod_filter` | [ https://httpd.apache.org/docs/2.4/mod/mod_filter.html](https://httpd.apache.org/docs/2.4/mod/mod_filter.html) |
| `mod_headers` | [ https://httpd.apache.org/docs/2.4/mod/mod_headers.html](https://httpd.apache.org/docs/2.4/mod/mod_headers.html) |
| `mod_mime` | [ https://httpd.apache.org/docs/2.4/mod/mod_mime.html](https://httpd.apache.org/docs/2.4/mod/mod_mime.html) |
| `mod_proxy` | [ https://httpd.apache.org/docs/2.4/mod/mod_proxy.html](https://httpd.apache.org/docs/2.4/mod/mod_proxy.html) |
| `mod_proxy_http` | [ https://httpd.apache.org/docs/2.4/mod/mod_proxy_http.html](https://httpd.apache.org/docs/2.4/mod/mod_proxy_http.html) |
| `mod_remoteip` | [ https://httpd.apache.org/docs/2.4/mod/mod_remoteip.html](https://httpd.apache.org/docs/2.4/mod/mod_remoteip.html) |
| `mod_reqtimeout` | [ https://httpd.apache.org/docs/2.4/mod/mod_reqtimeout.html](https://httpd.apache.org/docs/2.4/mod/mod_reqtimeout.html) |
| `mod_rewrite` | [ https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html](https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html) |
| `mod_security` | [ https://modsecurity.org/](https://modsecurity.org/) |
| `mod_setenvif` | [ https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html](https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html) |
| `mod_ssl (only the SSLProxyEngine directive)` | [ https://httpd.apache.org/docs/2.4/mod/mod_ssl.html#sslproxyengine](https://httpd.apache.org/docs/2.4/mod/mod_ssl.html#sslproxyengine) |
| `mod_substitute` | [ https://httpd.apache.org/docs/2.4/mod/mod_substitute.html](https://httpd.apache.org/docs/2.4/mod/mod_substitute.html) |
| `mod_userdir` | [ https://httpd.apache.org/docs/2.4/mod/mod_userdir.html](https://httpd.apache.org/docs/2.4/mod/mod_userdir.html) |
| `mod_macro` | [ https://httpd.apache.org/docs/2.4/mod/mod_macro.html](https://httpd.apache.org/docs/2.4/mod/mod_macro.html) |
| `mod_include (no directives supported)` | [ https://httpd.apache.org/docs/2.4/mod/mod_include.html](https://httpd.apache.org/docs/2.4/mod/mod_include.html) |


Klanten kunnen geen arbitraire modules toevoegen, maar er kunnen in de toekomst wel extra modules worden overwogen. Klanten kunnen de lijst met instructies voor een bepaalde Dispatcher-versie vinden door de opdracht lijst van gewenste personen van de validator uit te voeren in de SDK.

De instructies die zijn toegestaan in Apache-configuratiebestanden, kunnen worden weergegeven door de opdracht lijst van gewenste personen van de validator uit te voeren:

```
$ validator allowlist
Cloud manager validator 2.0.4
 
Allowlisted directives:
  <Directory>
  ...
  
```

## Mapstructuur {#folder-structure}

De de omslagstructuur van Apache en van Dispatcher van het project verschillen lichtjes gebaseerd op welke wijze dat het project, zoals die in de [ Bevestiging en het Zuiveren gebruikend de de Hulpmiddelen van Dispatcher ](#validation-debug) hierboven wordt beschreven sectie gebruikt.

## Dispatcher-configuratie migreren van AMS {#ams-aem}

Voor details op hoe te om de configuratie van Dispatcher van AMS aan AEM as a Cloud Service te migreren, zie [ migrerend de configuratie van Dispatcher van AMS aan AEM ](/help/implementing/dispatcher/ams-aem.md) as a Cloud Service pagina.
