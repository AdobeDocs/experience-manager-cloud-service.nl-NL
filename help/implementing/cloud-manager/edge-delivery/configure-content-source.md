---
title: Source voor inhoud configureren
description: Leer hoe u de inhoudsbron voor uw Edge Delivery-site configureert. Gebruik "fstab.yaml"met de architectuur van Helix 4, of gebruik de geleide tovenaar in Cloud Manager (of de Dienst API van de Configuratie) met de architectuur van Helix 5.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: f82eafc0-03d0-4c69-9b28-e769a012531b
source-git-commit: 71618a5603328990603db2ee7554048c9020a883
workflow-type: tm+mt
source-wordcount: '580'
ht-degree: 0%

---

# De inhoudsbron configureren in één klik voor Edge Delivery Services {#config-content-source}

>[!IMPORTANT]
>
>*Helix* is de interne naam voor de onderliggende architectuur aandrijvend AEM Sites met op document-gebaseerde creatie. Het is geen functie of productnaam. In dit artikel, *Helix* verwijst naar de architectuurversie die door uw Plaatsen van Edge Delivery wordt gebruikt. Helix 5 is de huidige versie van de onderliggende architectuur; Helix 4 is de vorige versie.

Adobe Experience Manager (AEM) Edge Delivery Services staat de levering van inhoud van veelvoudige bronnen zoals Google Drive, SharePoint, of AEM zelf toe, gebruikend een snel, globaal gedistribueerd randnetwerk.

De inhoudsbronconfiguratie verschilt op de volgende manier tussen de twee architectuurversies:

| Versie | Methode voor inhoudsbronconfiguratie |
| --- | --- |
| Helix 4 | YAML-bestand (`fstab.yaml`) |
| Helix 5 | De Dienst API van de configuratie (*nr`fstab.yaml`*) |

Dit artikel biedt uitgebreide configuratiestappen, voorbeelden en validatie-instructies voor beide versies.

**alvorens u** begint

Als u [&#x200B; gebruikt één klik Edge Delivery in Cloud Manager &#x200B;](/help/implementing/cloud-manager/edge-delivery/create-edge-delivery-site.md##one-click-edge-delivery-site), gebruikt uw plaats Helix 5 met één enkele bewaarplaats. [&#x200B; volg Helix 5 instructies &#x200B;](#config-helix5) en gebruik de verstrekte versie van Helix 4 YAML van de instructies als reserve.

**Bepaal uw versie van de Helix**

* Helix 4 - Uw project bevat een `fstab.yaml` -bestand.
* Helix 5 - Uw project *gebruikt* niet `fstab.yaml` en werd opstelling door [&#x200B; Cloud Manager gebruikend de geleide tovenaar &#x200B;](/help/implementing/cloud-manager/edge-delivery/add-edge-delivery-site.md) of API.

Bevestig de gegevens in de gegevensopslagruimte of raadpleeg uw beheerder als u nog niet zeker weet.

## De inhoudsbron voor Helix 4 configureren

In Helix 4 definieert het `fstab.yaml` -bestand de inhoudsbron voor uw site. Dit bestand wijst URL-padvoorvoegsels (zogenaamde bergpunten) toe aan externe inhoudsbronnen die zich in de hoofdmap van uw GitHub-opslagplaats bevinden. Een typisch voorbeeld ziet er als volgt uit:

```yaml
mountpoints:
  /: https://drive.google.com/drive/folders/your-folder-id
```

Het bovenstaande voorbeeld is alleen ter illustratie. De werkelijke URL moet verwijzen naar de inhoudsbron, zoals een Google Drive-map, een SharePoint-map of een AEM-pad.

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

### Validatie

* Gebruikend de Uitbreiding van AEM Sidekick Chrome, klik **Voorproef** > **publiceren** > **Test de levende plaats**.
* URL valideren: `https://main--<repo>--<org>.hlx.page/`

## De inhoudsbron voor Helix 5 configureren {#config-helix5}

Helix 5 is zonder voorwerp, gebruikt `fstab.yaml` niet, en steunt veelvoudige plaatsen die de zelfde folder delen. De configuratie wordt beheerd door de API van de Dienst van de Configuratie of de gebruikersinterface van de Plaatsen van Edge Delivery. De configuratie is plaats-niveau (niet bewaarplaats-niveau).

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

### Validatie

* Gebruikend de Uitbreiding van AEM Sidekick Chrome, klik **Voorproef** > **publiceren** > **Test de levende plaats**.
* URL valideren: `https://main--<repo>--<org>.aem.page/`
* (Optioneel) Controleer de huidige configuratie via de volgende API-aanroep van `GET` :

  ```bash
  GET /api/{program}/{programId}/site/{siteId}
  ```
