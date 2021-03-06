---
title: URL's extern maken
description: ExternalAlizer is de dienst OSGi die u toestaat om een middelweg in externe en absolute URL programmatically om te zetten.
exl-id: 06efb40f-6344-4831-8ed9-9fc49f2c7a3f
source-git-commit: c08e442e58a4ff36e89a213aa7b297b538ae3bab
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 0%

---

# URL&#39;s extern maken {#externalizing-urls}

In AEM **ExternalAlizer** is de dienst OSGi die u toestaat om een middelweg programmatically om te zetten (b.v. `/path/to/my/page`) in een externe en absolute URL (bijvoorbeeld `https://www.mycompany.com/path/to/my/page`) door het pad vooraf te bevestigen met een vooraf geconfigureerde DNS.

Omdat een AEM as a Cloud Service instantie zijn uiterlijk zichtbare URL niet kan kennen en omdat soms een verbinding buiten het verzoekwerkingsgebied moet worden gecreeerd, verstrekt deze dienst een centrale plaats om die externe URLs te vormen en hen te bouwen.

Dit artikel verklaart hoe te om de dienst te vormen Externalzer en hoe te om het te gebruiken. Voor technische details van de dienst, gelieve te verwijzen naar [Javadocs](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/Externalizer.html).

## Standaardgedrag van Externalzer en Hoe te om met voeten te treden {#default-behavior}

Buiten-de doos, heeft de dienst Externalzer waarden zoals `author-p12345-e6789.adobeaemcloud.com` en `publish-p12345-e6789.adobeaemcloud.com`.

Als u deze waarden wilt overschrijven, gebruikt u de omgevingsvariabelen van Cloud Manager, zoals beschreven in het artikel [Het vormen OSGi voor AEM as a Cloud Service](/help/implementing/deploying/configuring-osgi.md#cloud-manager-api-format-for-setting-properties) en het instellen van de vooraf gedefinieerde `AEM_CDN_DOMAIN_AUTHOR` en `AEM_CDN_DOMAIN_PUBLISH` variabelen.

## Het vormen van de Dienst Externalzer {#configuring-the-externalizer-service}

De dienst ExternalAlizer staat u toe om het domein centraal te bepalen dat aan programmatically voorvoegselmiddelwegen kan worden gebruikt. De dienst Externalzer zou slechts voor toepassingen met ????n enkel domein moeten worden gebruikt.

>[!NOTE]
>
>Als u een [OSGi-configuraties voor AEM as a Cloud Service,](/help/implementing/deploying/overview.md#osgi-configuration) de volgende stappen zouden op een lokale ontwikkelaarinstantie moeten worden uitgevoerd en dan aan uw projectcode voor plaatsing ge??ngageerd.

Om een domeinafbeelding voor de dienst te bepalen Externalzer:

1. Navigeer aan de Manager van de Configuratie via:

   `https://<host>:<port>/system/console/configMgr`

1. Klikken **Day CQ Link ExternalAlizer** om het dialoogvenster Configuratie te openen.

   ![De configuratie ExternalAlizer OSGi](./assets/externalizer-osgi.png)

   >[!NOTE]
   >
   >De directe koppeling naar de configuratie is `https://<host>:<port>/system/console/configMgr/com.day.cq.commons.impl.ExternalizerImpl`

1. Een **Domeinen** toewijzing. Een toewijzing bestaat uit een unieke naam die in de code kan worden gebruikt om naar het domein, een ruimte en het domein te verwijzen:

   `<unique-name> [scheme://]server[:port][/contextpath]`

   Waar:

   * **`scheme`** is meestal http of https, maar kan een ander protocol zijn.

      * Het wordt aanbevolen https te gebruiken om https-koppelingen af te dwingen.
      * Deze wordt gebruikt als de clientcode het schema niet overschrijft wanneer u vraagt om externalisatie van een URL.
   * **`server`** is de gastheernaam (of een domeinnaam of ip adres).
   * **`port`** (optioneel) is het poortnummer.
   * **`contextpath`** (optioneel) wordt alleen ingesteld als AEM is ge??nstalleerd als een webapp onder een ander contextpad.

   Bijvoorbeeld: `production https://my.production.instance`

   De volgende toewijzingsnamen zijn vooraf gedefinieerd en moeten altijd worden ingesteld op basis van AEM:

   * `local` - de lokale instantie
   * `author` - DNS van het ontwerpsysteem
   * `publish` - het publiek met de website DNS geconfronteerd

   >[!NOTE]
   >
   >Met een aangepaste configuratie kunt u een nieuwe categorie toevoegen, zoals `production`, `staging` of zelfs externe niet-AEM systemen zoals `my-internal-webservice`. Het is nuttig om harde codering dergelijke URLs over verschillende plaatsen in codebase van een project te vermijden.

1. Klikken **Opslaan** om uw wijzigingen op te slaan.

### Het gebruiken van de Dienst Externalzer {#using-the-externalizer-service}

Deze sectie toont een paar voorbeelden van hoe de dienst Externalzer kan worden gebruikt.

>[!NOTE]
>
>In de context van HTML mogen geen absolute koppelingen worden gemaakt. Daarom dient dit nut in dergelijke gevallen niet te worden gebruikt.

* **Een pad extern maken met het domein &#39;publish&#39;:**

   ```java
   String myExternalizedUrl = externalizer.publishLink(resolver, "/my/page") + ".html";
   ```

   Het veronderstellen van de domeinafbeelding:

   * `publish https://www.website.com`

   * `myExternalizedUrl` eindigt omhoog met de waarde:

   * `https://www.website.com/contextpath/my/page.html`

* **Een pad extern maken met het domein &#39;auteur&#39;:**

   ```java
   String myExternalizedUrl = externalizer.authorLink(resolver, "/my/page") + ".html";
   ```

   Het veronderstellen van de domeinafbeelding:

   * `author https://author.website.com`

   * `myExternalizedUrl` eindigt omhoog met de waarde:

   * `https://author.website.com/contextpath/my/page.html`

* **Een pad extern maken met het &#39;lokale&#39; domein:**

   ```java
   String myExternalizedUrl = externalizer.externalLink(resolver, Externalizer.LOCAL, "/my/page") + ".html";
   ```

   Het veronderstellen van de domeinafbeelding:

   * `local https://publish-3.internal`

   * `myExternalizedUrl` eindigt omhoog met de waarde:

   * `https://publish-3.internal/contextpath/my/page.html`

>[!TIP]
>
>Meer voorbeelden vindt u in het gedeelte [Javadocs](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/Externalizer.html).
