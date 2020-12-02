---
title: Ontwikkelen AEM Handel voor AEM als Cloud Service
description: Leer hoe te om een handel-toegelaten AEM project te produceren gebruikend het AEM projectarchetype. Leer hoe te om het project aan een lokale ontwikkelomgeving te bouwen en op te stellen gebruikend de AEM als Cloud Service SDK.
topics: Commerce, Development
feature: Commerce Integration Framework
version: cloud-service
doc-type: tutorial
kt: 5826
thumbnail: 39476.jpg
translation-type: tm+mt
source-git-commit: 6be2ed60f4e672b99a85b55f833b8ae2f1b952b0
workflow-type: tm+mt
source-wordcount: '1070'
ht-degree: 7%

---


# Ontwikkelen AEM Handel voor AEM als Cloud Service {#develop}

De ontwikkeling van AEM Commerce-projecten op basis van het Kader voor de integratie van de Handel (CIF) voor AEM als Cloud Service volgt dezelfde regels en beste praktijken als andere AEM projecten op AEM als Cloud Service. Controleer eerst deze:

- [AEM-projectstructuur](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html)
- [AEM as a Cloud Service SDK](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html)
- [Ontwikkelingsrichtlijnen voor AEM as a Cloud Service](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/development-guidelines.html)

## Lokale ontwikkeling met AEM als Cloud Service SDK {#local}

>[!VIDEO](https://video.tv.adobe.com/v/39476/?quality=12&learn=on)

Een lokale ontwikkelomgeving wordt aanbevolen voor CIF-projecten. De CIF toe:voegen-On die voor AEM als milieu van de Cloud Service wordt verstrekt is ook beschikbaar voor lokale ontwikkeling. Het kan van [het portaal van de Distributie van de Software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) worden gedownload.

De CIF Add-On wordt verstrekt als Sling Feature archief. Het ZIP-bestand dat beschikbaar is op de portal Softwaredistributie bevat twee Sling Feature-archiefbestanden: een voor AEM auteur en een voor AEM publicatie-instanties.

**Nieuw bij AEM als Cloud Service?** Bekijk  [een gedetailleerdere handleiding voor het instellen van een lokale ontwikkelomgeving met de AEM als Cloud Service-SDK](https://docs.adobe.com/content/help/en/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html).

### Vereiste software

Het volgende moet lokaal worden geïnstalleerd:

- [AEM als Cloud Service SDK](https://docs.adobe.com/content/help/en/*experience-manager-learn/cloud-service/local-development-environment-set-up/aem-runtime.html#download-the-aem-as-a-cloud-service-sdk)
- [Java 11](https://downloads.experiencecloud.adobe.com/content/software-distribution/en/general.html)
- [Apache Maven](https://maven.apache.org/)  (3.3.9 of hoger)
- [Node.js v10+](https://nodejs.org/en/)
- [npm 6+](https://www.npmjs.com/)
- [Git](https://git-scm.com/)

### Toegang tot de CIF-invoegtoepassing

De CIF-invoegtoepassing kan als een zip-bestand worden gedownload van het [portal Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html). Het ZIP-bestand bevat de CIF-invoegtoepassing als **Sling Feature archive**, dit is geen AEM pakket. Let op: toegang tot de SDK-aanbiedingen is beperkt tot die met AEM als licentie voor Cloud Servicen.

>[!TIP]
>
>Zorg ervoor u altijd de recentste versie van CIF toe:voegen-aan gebruikt.

### Lokale instellingen

Voor de lokale ontwikkeling van de toe:voegen-op CIF die de AEM als Cloud Service SDK gebruikt:

1. Krijg de recentste AEM als Cloud Service SDK
1. Pak de AEM .jar uit om de `crx-quickstart` omslag tot stand te brengen, looppas:

   ```bash
   java -jar <jar name> -unpack
   ```

1. Een `crx-quickstart/install`-map maken
1. Kopieer het juiste archiefbestand voor de verkoopfunctie van de CIF-invoegtoepassing naar de map `crx-quickstart/install`.

   Het CIF-ZIP-bestand met invoegtoepassingen bevat twee Sling Feature-archiefbestanden `.far`. Zorg ervoor dat u de juiste methode gebruikt voor AEM-auteur of AEM-publicatie, afhankelijk van hoe u de lokale AEM als Cloud Service-SDK wilt uitvoeren.

1. Creeer een lokale OS omgevingsvariabele genoemd `COMMERCE_ENDPOINT` die het eindpunt Magento GraphQL houdt.

   Voorbeeld Mac OSX:

   ```bash
   export COMMERCE_ENDPOINT=https://demo.magentosite.cloud/graphql
   ```

   Voorbeeld van Windows:

   ```bash
   set COMMERCE_ENDPOINT=https://demo.magentosite.cloud/graphql
   ```

   Deze variabele moet ook voor de AEM worden ingesteld als een Cloud Service-omgeving.

   Voor meer informatie over variabelen, zie [Het vormen OSGi voor AEM als Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html#local-development).

1. (Optioneel) Als u functies voor gefaseerde catalogi wilt inschakelen, moet u een integratietoken maken voor uw Magento-instantie. Volg de stappen bij [Getting Started](./getting-started.md#staging) om het token te maken.

   Plaats een geheim OSGi met de naam `COMMERCE_AUTH_HEADER` aan de volgende waarde:

   ```xml
   Authorization: Bearer <Access Token>
   ```

   Voor meer informatie over geheimen, zie [Het vormen OSGi voor AEM als Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html#local-development).

1. De AEM starten als Cloud Service-SDK

1. De lokale GraphQL-proxyserver starten

   Om het eindpunt van Magento GraphQL plaatselijk voor toe:voegen-op CIF en de componenten CIF ter beschikking te stellen gebruik het volgende bevel. Het eindpunt GraphQL zal dan beschikbaar zijn bij `http://localhost:3002/graphql`.
Voorbeeld Mac OSX:

   ```bash
   npx local-cors-proxy --proxyUrl https://demo.magentosite.cloud --port 3002 --proxyPartial ''
   ```

   Voorbeeld van Windows:

   ```bash
   npx local-cors-proxy --proxyUrl https://demo.magentosite.cloud --port 3002 --proxyPartial '""'
   ```

   Het argument `--proxyPartial` moet een lege tekenreeks ontvangen.

   U kunt de lokale volmacht testen GraphQL door een grafiehQL vraaghulpmiddel aan `http://localhost:3002/graphql` te richten en een paar vragen te testen.

1. Meld u aan bij AEM SDK en configureer CIF om de lokale GraphQL-proxyserver te gebruiken.

   Navigeer naar de CIF-configuratie van de Cloud Service (Opties > Cloud Services > CIF-configuratie). Open de eigenschappen mening van config die door uw project wordt gebruikt.

   Gebruik voor de eigenschap `GraphQL Proxy Path` het lokale eindpunt van de proxyserver `http://localhost:3002/graphql`. Sla de configuratie op.

>[!NOTE]
>
>Duw niet de configuratie van stap 8 in de projectrepo. Dit config wordt slechts vereist voor een lokale ontwikkelingsopstelling. AEM als een Cloud Service milieu&#39;s reeds opstelling met de volmacht GraphQL tijdens het onboarding.

Verifieer de opstelling via de console OSGI: `http://localhost:4502/system/console/osgi-installer`. De lijst moet de CIF-add-on gerelateerde bundels, het inhoudspakket en de configuraties OSGI bevatten, zoals gedefinieerd in het bestand met het functiemodel.

## Projectinstelling {#project}

Er zijn twee manieren om uw CIF project voor AEM als Cloud Service op te starten.

### Projectarchetype AEM gebruiken

Het [AEM Archetype van het Project](https://github.com/adobe/aem-project-archetype) is het belangrijkste hulpmiddel om een vooraf gevormd project op te starten met CIF. De Componenten van de Kern van CIF en alle vereiste configuraties kunnen in een geproduceerd project met één extra optie worden omvat.

>[!TIP]
>
>Gebruik [AEM Projectarchetype 24 of later](https://github.com/adobe/aem-project-archetype/releases) om het project te genereren.

Zie AEM Project Archetype [gebruiksinstructies](https://github.com/adobe/aem-project-archetype#usage) op hoe te om een AEM project te produceren. Als u CIF wilt opnemen in het project, gebruikt u de optie `includeCommerce`.

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

De componenten van de Kern van CIF kunnen in om het even welk project worden gebruikt door of het verstrekte `all` pakket of individueel gebruikend het CIF inhoudspakket en verwante SGI bunldes te omvatten. Om de Componenten van de Kern van CIF aan een project manueel toe te voegen gebruiken de volgende gebiedsdelen:

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

Een tweede mogelijkheid om een CIF-project te starten, is het klonen en gebruiken van de [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia). De AEM Venia Reference Store is een voorbeeldopslagtoepassing die het gebruik van CIF Core Components voor AEM aantoont. Het is bedoeld als een set voorbeelden met best practices en een mogelijk beginpunt voor het ontwikkelen van uw eigen functionaliteit.

Om aan de slag te gaan met de Venia Reference Store klonen we gewoon de Git-opslagplaats en begint u het project aan te passen aan uw behoeften.

>[!NOTE]
>
>Het project van de Referentieopslag van Venia bevat twee bouwstijlprofielen voor AEM als Cloud Service en AEM 6.5. Controleer [project readme.md](https://github.com/adobe/aem-cif-guides-venia/blob/main/README.md) om te zien hoe zij worden gebruikt.

## Aanvullende bronnen

- [Projectarchetype AEM](https://github.com/adobe/aem-project-archetype)
- [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia)
- [Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)
