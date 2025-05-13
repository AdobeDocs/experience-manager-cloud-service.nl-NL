---
title: Opmerkingen bij de release voor Cloud Manager 2025.5.0
description: Meer informatie over de release van Cloud Manager 2025.5.0 in Adobe Experience Manager as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: f9f4226bff8a0772878c144773eb8ff841a0a8d0
workflow-type: tm+mt
source-wordcount: '830'
ht-degree: 0%

---

# Opmerkingen bij de release voor Cloud Manager 2025.5.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

<!-- https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.03.0+Release -->

Meer informatie over de release van Cloud Manager 2025.5.0 in AEM (Adobe Experience Manager) as a Cloud Service.

Zie ook de [ huidige versienota&#39;s voor Adobe Experience Manager as a Cloud Service ](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Releasedatums {#release-date}

De releasedatum voor Cloud Manager 2025.5.0 in AEM as a Cloud Service is donderdag 8 mei 2025.

De volgende geplande release is donderdag 5 juni 2025.

## Nieuwe functies {#what-is-new}

### De inhoudsbron configureren in één klik voor Edge Delivery Services

Adobe Experience Manager (AEM) Edge Delivery Services staat de levering van inhoud van veelvoudige bronnen zoals Google Drive, SharePoint, of AEM zelf toe, gebruikend een snel, globaal gedistribueerd randnetwerk.

De configuratie van de inhoudsbron verschilt op de volgende manier tussen Helix 4 en Helix 5:

| Versie | Methode voor inhoudsbronconfiguratie |
| --- | --- |
| Helix 4 | YAML-bestand (`fstab.yaml`) |
| Helix 5 | De Dienst API van de configuratie (*nr`fstab.yaml`*) |

Dit artikel biedt uitgebreide configuratiestappen, voorbeelden en validatie-instructies voor beide versies.

**alvorens u** begint

Als u [ gebruikt één klik Edge Delivery in Cloud Manager ](/help/implementing/cloud-manager/edge-delivery/create-edge-delivery-site.md##one-click-edge-delivery-site), is uw plaats Helix 5 met één enkele bewaarplaats. Volg de instructies van Helix 5 en gebruik de meegeleverde Helix 4 YAML versie van instructies als fallback.

**Bepaal uw versie van de Helix**

* Helix 4 - Uw project bevat een `fstab.yaml` -bestand.
* Helix 5 - Uw project *gebruikt* niet `fstab.yaml` en werd opstelling door Edge Delivery Services UI of API.

Bevestig de gegevens in de gegevensopslagruimte of raadpleeg uw beheerder als u nog niet zeker weet.

#### De inhoudsbron voor Helix 4 configureren

In Helix 4 definieert het bestand fstab.yaml de inhoudsbron voor uw site. Dit bestand wijst URL-padvoorvoegsels (zogenaamde bergpunten) toe aan externe inhoudsbronnen die zich in de hoofdmap van uw GitHub-opslagplaats bevinden. Een typisch voorbeeld ziet er als volgt uit:

```yaml
mountpoints:
  /: https://drive.google.com/drive/folders/your-folder-id
```

Dit voorbeeld is alleen ter illustratie. De werkelijke URL moet verwijzen naar de inhoudsbron, zoals een specifieke Google Drive-map, SharePoint-map of AEM-pad.

**om de inhoudsbron voor Helix 4 te vormen:**

De stappen variëren door het bronsysteem dat u gebruikt.

* **de Aandrijving van Google**

   1. Maak een map voor Google Drive.
   1. Deel de map met `helix@adobe.com` .
   1. Hiermee wordt de koppeling voor de deelbare map opgehaald.
   1. Werk uw `fstab.yaml` bij zoals in het volgende voorbeeld wordt getoond:

      ```yaml
      mountpoints: 
          /: https://drive.google.com/drive/folders/<folder-id>
      ```

   1. Leg en duw veranderingen in GitHub vast.

* **SharePoint**

   1. Maak een SharePoint-map of -documentbibliotheek.
   1. Deel toegang met `helix@adobe.com` .
   1. Haal de URL van de map op.
   1. Werk uw `fstab.yaml` bij zoals in het volgende voorbeeld wordt getoond:

      ```yaml
      mountpoints:
        /: https://<tenant>.sharepoint.com/sites/<site>/Shared%20Documents/<folder>
      ```

   1. Leg en duw veranderingen in GitHub vast.

* **AEM**

   1. Identificeer uw AEM-inhoudspad.
   1. Gebruik de URL voor het exporteren van AEM-inhoud, zoals in het volgende voorbeeld wordt getoond:

      ```yaml
      mountpoints:
        /: https://author.<your-aem-instance>.com/bin/franklin.delivery/<org>/<repo>/main
      ```

   1. Leg en duw veranderingen in GitHub vast.

##### Validatie

* Gebruikend de Uitbreiding van AEM Sidekick Chrome, klik **Voorproef** > **publiceren** > **Test de levende plaats**.
* URL valideren: `https://main--<repo>--<org>.hlx.page/`

#### De inhoudsbron voor Helix 5 configureren

Helix 5 is zonder voorwerp, gebruikt `fstab.yaml` niet, en steunt veelvoudige plaatsen die de zelfde folder delen. De configuratie wordt beheerd door de API van de Dienst van de Configuratie of de UI van Edge Delivery Services. De configuratie is plaats-niveau (niet bewaarplaats-niveau).

Conceptuele verschillen zijn de volgende:

| Verhouding | Helix 4 | Helix 5 |
| --- | --- | --- |
| Configuratie | Gereed tot en met `fstab.yaml` | Gereed via de API of UI in plaats van via YAML. |
| Bergpunten | Gedefinieerd in `fstab.yaml` . | Niet vereist. De wortel wordt impliciet begrepen. |

**om de inhoudsbron voor Helix 5 te vormen:**

1. Gebruikend de Dienst API van de Configuratie, verifieer door een API sleutel of toegangstoken.
1. Stel de volgende `PUT` API-aanroep in:

   ```bash {.line-numbering}
   PUT /api/{program}/{programId}/site/{siteId}
   Content-Type: application/json
   
   {
     "sitename": "my-site",
     "branchName": "main",
     "version": "v5",
     "repo": "my-content-repo-link"
   }
   ```

1. Reactie valideren (wordt verwacht: HTTP 200 OK).

##### Validatie

* Gebruikend de Uitbreiding van AEM Sidekick Chrome, klik **Voorproef** > **publiceren** > **Test de levende plaats**.
* URL valideren: `https://main--<repo>--<org>.aem.page/`
* (Optioneel) Controleer de huidige configuratie via de volgende API-aanroep van `GET` :

  ```bash
  GET /api/{program}/{programId}/site/{siteId}
  ```

<!--
* **AI-powered build summaries now available for internal use**

    Internal users can now use AI-powered build summaries to simplify build log analysis. The feature provides actionable recommendations and helps identify the root causes of build failures.

    ![Build Summary dialog box](/help/implementing/cloud-manager/release-notes/assets/build-summary.png)
-->


## Programma voor vroegtijdige adoptie {#early-adoption}

Neem deel aan het Cloud Manager-programma voor vroege adoptie om exclusieve toegang te krijgen tot de volgende functies voordat ze algemeen worden uitgebracht.

Momenteel zijn de volgende mogelijkheden voor vroege adoptie beschikbaar:

### Edge Delivery Pipet toevoegen {#add-eds-pipeline}

**Pijpleidingen** worden nu gesteund voor plaatsen die met Edge Delivery Services worden gebouwd, die dit vermogen voorbij enkel de milieu&#39;s van Cloud Service uitbreiden. U kunt **Pijpleidingen** gebruiken om montages zoals verkeer het filtreren regels en de configuraties van de Firewall van de Toepassing van het Web (WAF) te beheren, waar toepasselijk. Zie [ Ondersteunde Configuraties ](/help/operations/config-pipeline.md#configurations).

<!-- ![Add Edge Delivery pipeline in Add Pipeline drop-down list](/help/implementing/cloud-manager/release-notes/assets/add-edge-delivery-pipeline.png) -->

Als u in het testen van deze nieuwe eigenschap en het delen van uw terugkoppelt geinteresseerd bent, verzend een e-mail naar [ grp-aemeds-config-pipeline-adopter@adobe.com ](mailto:grp-aemeds-config-pipeline-adopter@adobe.com) van uw e-mailadres verbonden aan uw Adobe ID.

### Kies voor uw eigen git - nu met ondersteuning voor Azure DevOps {#gitlab-bitbucket-azure-vsts}

<!-- BOTH CS & AMS -->

Klanten kunnen nu hun Azure DevOps Git-opslagruimten in Cloud Manager aan boord nemen, met ondersteuning voor zowel moderne Azure DevOps- als oudere VSTS-opslagruimten (Visual Studio Team Services).

* Voor Edge Delivery Services-gebruikers kan de ingebouwde opslagplaats worden gebruikt voor het synchroniseren en implementeren van sitecode.
* Voor AEM as a Cloud Service- en Adobe Managed Services-gebruikers (AMS) kan de opslagplaats worden gekoppeld aan zowel full-stack als frontend pijpleidingen.

De steun voor extra pijpleidingstypes en trekverzoekbevestiging door pijpleidingen van de codekwaliteit komt binnenkort.

Zie [ externe bewaarplaatsen in Cloud Manager ](/help/implementing/cloud-manager/managing-code/external-repositories.md) toevoegen.

![ voeg de dialoogdoos van de Bewaarplaats ](/help/implementing/cloud-manager/release-notes/assets/azure-repo.png) toe

Als u in het testen van deze nieuwe eigenschap en het delen van uw terugkoppelt geinteresseerd bent, verzend een e-mail naar [ Grp-CloudManager_BYOG@adobe.com ](mailto:grp-cloudmanager_byog@adobe.com) van uw e-mailadres verbonden aan uw Adobe ID. Zorg ervoor dat u ook het Git-platform opgeeft dat u wilt gebruiken en dat u zich in een opslagstructuur van een privéserver, een openbare opslagruimte of een bedrijfsopslagruimte bevindt.

<!--
## Bug fixes

* Issue

* Issue

* Issue
-->

<!-- ## Known issues {#known-issues} -->

