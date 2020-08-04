---
title: Ontwikkelen AEM Handel voor AEM als Cloud Service
description: Ontwikkelen AEM Handel voor AEM als Cloud Service
translation-type: tm+mt
source-git-commit: e30086c546d9efcc1da07ac5862c012a0db02c09
workflow-type: tm+mt
source-wordcount: '808'
ht-degree: 9%

---


# Ontwikkelen AEM Handel voor AEM als Cloud Service {#develop}

De ontwikkeling van AEM Commerce-projecten op basis van het Kader voor de integratie van de Handel (CIF) voor AEM als Cloud Service volgt dezelfde regels en beste praktijken als andere AEM projecten op AEM als Cloud Service. Controleer eerst deze:

- [AEM-projectstructuur](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html)
- [AEM as a Cloud Service SDK](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html)
- [Ontwikkelingsrichtlijnen voor AEM as a Cloud Service](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/development-guidelines.html)

## Lokale ontwikkeling met AEM als Cloud Service SDK {#local}

Een lokale ontwikkelomgeving wordt aanbevolen voor CIF-projecten. De CIF toe:voegen-On die voor AEM als milieu van de Cloud Service wordt verstrekt is ook beschikbaar voor lokale ontwikkeling. Het kan van het portaal [van de Distributie van de](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)Software worden gedownload.

De CIF Add-On wordt verstrekt als Sling Feature archief. Het ZIP-bestand dat beschikbaar is op de portal Softwaredistributie bevat twee Sling Feature-archiefbestanden: een voor AEM auteur en een voor AEM publicatie-instanties.

**Nieuw bij AEM als Cloud Service?** Raadpleeg de [volgende handleiding voor het instellen van een lokale ontwikkelomgeving met de AEM als Cloud Service-SDK](https://docs.adobe.com/content/help/en/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html).

### Vereiste software

Het volgende moet lokaal worden geïnstalleerd:

- [AEM as a Cloud Service SDK](https://docs.adobe.com/content/help/en/*experience-manager-learn/cloud-service/local-development-environment-set-up/aem-runtime.html#download-the-aem-as-a-cloud-service-sdk)
- [Java 11](https://downloads.experiencecloud.adobe.com/content/software-distribution/en/general.html)
- [Apache Maven](https://maven.apache.org/) (3.3.9 of hoger)
- [Node.js v10+](https://nodejs.org/en/)
- [npm 6+](https://www.npmjs.com/)
- [Git](https://git-scm.com/)

### Toegang tot de CIF-invoegtoepassing

The CIF add-on can be downloaded as a zip file from the [Software Distribution portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html). Het ZIP-bestand bevat de CIF-invoegtoepassing als Sling Feature-archief. Het is geen AEM pakket. Let op: toegang tot de SDK-aanbiedingen is beperkt tot die met AEM als licentie voor Cloud Servicen.

>[!TIP]
>
>Zorg ervoor u altijd de recentste versie van CIF toe:voegen-aan gebruikt.

### Lokale instellingen

Voor de lokale ontwikkeling van de toe:voegen-op CIF die de AEM als Cloud Service SDK gebruikt:

1. Krijg de recentste AEM als Cloud Service SDK
2. Pak de AEM .jar uit om de `crx-quickstart` map te maken. Voer de volgende handelingen uit:

   ```bash
   java -jar <jar name> -unpack
   ```

3. Een `crx-quickstart/install` map maken
4. Kopieer het juiste archiefbestand voor de verkoopfunctie van de CIF-invoegtoepassing naar de `crx-quickstart/install` map.

   Het CIF-ZIP-bestand met invoegtoepassingen bevat twee Sling Feature- `.far` archiefbestanden. Zorg ervoor om correcte te gebruiken voor AEM Author of AEM Publish, afhankelijk van hoe u van plan bent om de lokale AEM als Cloud Service SDK in werking te stellen.

5. Creeer een lokale OS omgevingsvariabele genoemd die het eindpunt Magento GraphQL houdt. `COMMERCE_ENDPOINT`

   Voorbeeld Mac OSX:

   ```bash
   export COMMERCE_ENDPOINT=https://demo.magentosite.cloud/graphql
   ```

   Voorbeeld van Windows:

   ```bash
   set COMMERCE_ENDPOINT=https://demo.magentosite.cloud/graphql
   ```

   Deze variabele moet ook voor de AEM worden ingesteld als een Cloud Service-omgeving.

6. De AEM starten als Cloud Service-SDK

Verifieer de opstelling via de console OSGI:`http://localhost:4502/system/console/osgi-installer`. De lijst moet de CIF-add-on gerelateerde bundels, het inhoudspakket en de configuraties OSGI bevatten, zoals gedefinieerd in het bestand met het functiemodel.

## Projectinstelling {#project}

Er zijn twee manieren om uw CIF project voor AEM als Cloud Service op te starten.

### Projectarchetype AEM gebruiken

Het [AEM Archetype](https://github.com/adobe/aem-project-archetype) van het Project is het belangrijkste hulpmiddel om een vooraf gevormd project op te starten met CIF. De Componenten van de Kern van CIF en alle vereiste configuraties kunnen in een geproduceerd project met één extra optie worden omvat.

>[!TIP]
>
>Gebruik [AEM Projectarchetype 24 of hoger](https://github.com/adobe/aem-project-archetype/releases) om het project te genereren.

Zie AEM het [gebruiksinstructies](https://github.com/adobe/aem-project-archetype#usage) van het Archetype van het Project op hoe te om een AEM project te produceren. Als u CIF wilt opnemen in het project, gebruikt u de `includeCommerce` optie.

Bijvoorbeeld:

```bash
mvn -B archetype:generate \
 -D archetypeGroupId=com.adobe.granite.archetypes \
 -D archetypeArtifactId=aem-project-archetype \
 -D archetypeVersion=24 \
 -D aemVersion=cloud \
 -D appTitle="My Site" \
 -D appId="mysite" \
 -D groupId="com.mysite" \
 -D frontendModule=general \
 -D includeExamples=n \
 -D includeCommerce=y
```

CIF Core Components kunnen in elk project worden gebruikt door het geleverde `all` pakket op te nemen of door het pakket CIF content en verwante OSGI bunldes individueel te gebruiken. Om de Componenten van de Kern van CIF aan een project manueel toe te voegen gebruiken de volgende gebiedsdelen:

```java
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>core-cif-components-apps</artifactId>
    <type>zip</type>
    <version>x.y.z</version>
</dependency>
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>core-cif-components-core</artifactId>
    <version>x.y.z</version>
</dependency>
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>graphql-client</artifactId>
    <version>x.y.z</version>
</dependency>
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>magento-graphql</artifactId>
    <version>x.y.z</version>
</dependency>
```

### AEM Venia Reference Store gebruiken

Een tweede mogelijkheid om een CIF-project te starten is het klonen en gebruiken van de [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia). De AEM Venia Reference Store is een voorbeeldopslagtoepassing die het gebruik van CIF Core Components voor AEM aantoont. Het is bedoeld als een set voorbeelden met best practices en een mogelijk beginpunt voor het ontwikkelen van uw eigen functionaliteit.

Om aan de slag te gaan met de Venia Reference Store klonen we gewoon de Git-opslagplaats en begint u het project aan te passen aan uw behoeften.

>[!NOTE]
>
>Het project van de Referentieopslag van Venia bevat twee bouwstijlprofielen voor AEM als Cloud Service en AEM 6.5. Controleer het [project readme.md](https://github.com/adobe/aem-cif-guides-venia/blob/main/README.md) om te zien hoe zij worden gebruikt.

## Aanvullende bronnen

- [Projectarchetype AEM](https://github.com/adobe/aem-project-archetype)
- [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia)
- [Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)
