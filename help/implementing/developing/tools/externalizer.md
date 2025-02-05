---
title: URL's extern maken
description: ExternalAlizer is de dienst OSGi die u programmatically een middelweg in een externe en absolute URL laat omzetten.
exl-id: 06efb40f-6344-4831-8ed9-9fc49f2c7a3f
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---

# URL&#39;s extern maken {#externalizing-urls}

In AEM, is **ExternalAlizer** de dienst OSGi die u programmatically een middelweg (bijvoorbeeld, `/path/to/my/page`) in een externe en absolute URL (bijvoorbeeld, `https://www.mycompany.com/path/to/my/page`) laat omzetten door de weg met pre-gevormde DNS te bevestigen.

Omdat een instantie van AEM as a Cloud Service zijn extern zichtbare URL niet kan kennen en omdat soms een verbinding buiten het verzoekwerkingsgebied moet worden gecreeerd, verstrekt deze dienst een centrale plaats om die externe URLs te vormen en hen te bouwen.

Dit artikel verklaart hoe te om de dienst te vormen Externalzer en hoe te om het te gebruiken. Voor technische details van de dienst, zie [ JavaDocs ](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/Externalizer.html).

## Standaardgedrag van Externalzer en Hoe te om met voeten te treden {#default-behavior}

Buiten het vak wijst de service Externalzer een aantal domeinid&#39;s toe aan absolute URL-voorvoegsels die overeenkomen met de AEM service-URL&#39;s die voor de omgeving zijn gegenereerd, zoals `author https://author-p12345-e6789.adobeaemcloud.com` en `publish https://publish-p12345-e6789.adobeaemcloud.com` . De basis-URL&#39;s voor elk van deze standaarddomeinen worden gelezen van omgevingsvariabelen die door Cloud Manager worden gedefinieerd.

Ter referentie is de standaard OSGi-configuratie voor `com.day.cq.commons.impl.ExternalizerImpl.cfg.json` in feite:

```json
{
   "externalizer.domains": [
      "local $[env:AEM_EXTERNALIZER_LOCAL;default=http://localhost:4502]",
      "author $[env:AEM_EXTERNALIZER_AUTHOR;default=http://localhost:4502]",
      "publish $[env:AEM_EXTERNALIZER_PUBLISH;default=http://localhost:4503]",
      "preview $[env:AEM_EXTERNALIZER_PREVIEW;default=http://localhost:4503]"
   ]
}
```

>[!CAUTION]
>
>De standaardtoewijzingen `local`, `author`, `preview` en `publish` Externalalizer-domeinen in de OSGi-configuratie moeten met de hierboven vermelde oorspronkelijke waarden `$[env:...]` worden behouden.
>
>Het implementeren van een aangepast `com.day.cq.commons.impl.ExternalizerImpl.cfg.json` -bestand naar AEM as a Cloud Service waarbij een van deze &#39;out-of-the-box&#39;-domeintoewijzingen wordt weggelaten, kan leiden tot onvoorspelbaar toepassingsgedrag.

Om de `preview` en `publish` waarden met voeten te treden, gebruik de het omgevingsvariabelen van Cloud Manager zoals die in het artikel [ worden beschreven het Vormen OSGi voor AEM as a Cloud Service ](/help/implementing/deploying/configuring-osgi.md#cloud-manager-api-format-for-setting-properties) en het plaatsen van vooraf bepaalde `AEM_CDN_DOMAIN_PUBLISH` en `AEM_CDN_DOMAIN_PREVIEW` variabelen.

## Het vormen van de Dienst Externalzer {#configuring-the-externalizer-service}

De dienst ExternalAlizer laat u centraal het domein bepalen dat aan programmatically prefixmiddelwegen kan worden gebruikt. De dienst Externalzer zou slechts voor toepassingen met één enkel domein moeten worden gebruikt.

>[!NOTE]
>
>Zoals wanneer het toepassen van om het even welke [ configuraties OSGi voor AEM as a Cloud Service ](/help/implementing/deploying/overview.md#osgi-configuration), zouden de volgende stappen op een lokale ontwikkelaarinstantie moeten worden uitgevoerd en dan aan uw projectcode voor plaatsing geëngageerd.

Om een domeinafbeelding voor de dienst te bepalen Externalzer:

1. Navigeer aan de Manager van de Configuratie via:

   `https://<host>:<port>/system/console/configMgr`

1. Klik **Dag CQ Verbinding Externalzer** om de doos van de configuratiedialoog te openen.

   ![ de configuratie ExternalExternalSGi ](./assets/externalizer-osgi.png)

   >[!NOTE]
   >
   >De directe koppeling naar de configuratie is `https://<host>:<port>/system/console/configMgr/com.day.cq.commons.impl.ExternalizerImpl`

1. Bepaal de afbeelding van a **Domeinen**. Een toewijzing bestaat uit een unieke naam die in de code kan worden gebruikt om naar het domein, een ruimte en het domein te verwijzen:

   `<unique-name> [scheme://]server[:port][/contextpath]`

   Waarbij:

   * **`scheme`** is meestal http of https, maar kan een ander protocol zijn.

      * Adobe raadt u aan https te gebruiken om https-koppelingen af te dwingen.
      * Deze wordt gebruikt als de clientcode het schema niet overschrijft wanneer wordt gevraagd om externalisatie van een URL.

   * **`server`** is de hostnaam (een domeinnaam of ip-adres).
   * **`port`** (optioneel) is het poortnummer.
   * **`contextpath`** (optioneel) wordt alleen ingesteld als AEM is geïnstalleerd als een webapp onder een ander contextpad.

   Bijvoorbeeld: `production https://my.production.instance`

   De volgende toewijzingsnamen zijn vooraf gedefinieerd en moeten altijd worden ingesteld op basis van AEM:

   * `local` - de lokale instantie
   * `author` - de DNS van het ontwerpsysteem
   * `publish` - de openbare naar voren gerichte website DNS

   >[!NOTE]
   >
   >Met een aangepaste configuratie kunt u een nieuwe categorie toevoegen, zoals `production` , `staging` of zelfs externe niet-AEM systemen, zoals `my-internal-webservice` . Het is nuttig om harde codering dergelijke URLs over verschillende plaatsen in codebase van een project te vermijden.

1. Klik **sparen** om uw veranderingen te bewaren.

### Het gebruiken van de Dienst Externalzer {#using-the-externalizer-service}

Deze sectie toont een paar voorbeelden van hoe de dienst Externalzer kan worden gebruikt.

>[!NOTE]
>
>In de context van HTML mogen geen absolute koppelingen worden gemaakt. Gebruik dit hulpprogramma daarom in dergelijke gevallen niet.

* **om een weg met het &quot;te externaliseren&quot;domein:**

  ```java
  String myExternalizedUrl = externalizer.publishLink(resolver, "/my/page") + ".html";
  ```

  Het veronderstellen van de domeinafbeelding:

   * `publish https://www.website.com`

   * `myExternalizedUrl` eindigt omhoog met de waarde:

   * `https://www.website.com/contextpath/my/page.html`

* **om een weg met het &quot;auteur&quot;domein externaliseren:**

  ```java
  String myExternalizedUrl = externalizer.authorLink(resolver, "/my/page") + ".html";
  ```

  Het veronderstellen van de domeinafbeelding:

   * `author https://author.website.com`

   * `myExternalizedUrl` eindigt omhoog met de waarde:

   * `https://author.website.com/contextpath/my/page.html`

* **om een weg met het &quot;lokale&quot;domein externaliseren:**

  ```java
  String myExternalizedUrl = externalizer.externalLink(resolver, Externalizer.LOCAL, "/my/page") + ".html";
  ```

  Het veronderstellen van de domeinafbeelding:

   * `local https://publish-3.internal`

   * `myExternalizedUrl` eindigt omhoog met de waarde:

   * `https://publish-3.internal/contextpath/my/page.html`

>[!TIP]
>
>U kunt meer voorbeelden in [ JavaDocs ](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/Externalizer.html) vinden.
