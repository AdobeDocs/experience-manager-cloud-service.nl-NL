---
title: Ontwikkelen AEM Handel voor AEM as a Cloud Service
description: Leer hoe te om een handel-toegelaten AEM project te produceren gebruikend het AEM projectarchetype. Leer hoe u het project bouwt en implementeert in een lokale ontwikkelomgeving met de AEM as a Cloud Service SDK.
topics: Commerce, Development
feature: Commerce Integration Framework
version: cloud-service
doc-type: tutorial
kt: 5826
thumbnail: 39476.jpg
exl-id: 6f28a52b-52f8-4b30-95cd-0f9cb521de62
source-git-commit: 3e2e7fa875e17235b4e47083b564882bb4950d0d
workflow-type: tm+mt
source-wordcount: '1002'
ht-degree: 4%

---

# Ontwikkelen AEM Handel voor AEM as a Cloud Service {#develop}

Voor de ontwikkeling van AEM handelsprojecten op basis van het kader voor de integratie van de handel (CIF) voor AEM as a Cloud Service gelden dezelfde regels en beste praktijken als voor andere AEM projecten, ook op AEM as a Cloud Service. Controleer eerst deze:

- [AEM-projectstructuur](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html)
- [AEM as a Cloud Service SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html)
- [Ontwikkelingsrichtlijnen voor AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html)

## Lokale ontwikkeling met AEM as a Cloud Service SDK {#local}

>[!VIDEO](https://video.tv.adobe.com/v/39476/?quality=12&learn=on)

Een lokale ontwikkelomgeving wordt aanbevolen voor CIF-projecten. De CIF-invoegtoepassing die voor AEM as a Cloud Service is voorzien, is ook beschikbaar voor lokale ontwikkeling. Het kan worden gedownload van [Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html).

De CIF Add-On wordt verstrekt als Sling Feature archief. Het ZIP-bestand dat beschikbaar is op de portal Softwaredistributie bevat twee Sling Feature-archiefbestanden: een voor AEM auteur en een voor AEM publicatie-instanties.

**Nieuw bij AEM as a Cloud Service?** Uitchecken [een gedetailleerdere handleiding voor het instellen van een lokale ontwikkelomgeving met behulp van de AEM as a Cloud Service SDK](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html).

### Vereiste software

Het volgende moet lokaal worden geïnstalleerd:

- [as a Cloud Service SDK AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/aem-runtime.html#download-the-aem-as-a-cloud-service-sdk)
- [Java 11](https://downloads.experiencecloud.adobe.com/content/software-distribution/en/general.html)
- [Apache Maven](https://maven.apache.org/) (3.3.9 of hoger)
- [Node.js v10+](https://nodejs.org/en/)
- [npm 6+](https://www.npmjs.com/)
- [Git](https://git-scm.com/)

### Toegang tot de CIF-invoegtoepassing

De CIF-invoegtoepassing kan als een ZIP-bestand worden gedownload van de [Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html). Het ZIP-bestand bevat de CIF-invoegtoepassing als **Archief met verkoopfuncties** Het is geen AEM pakket. Let op: toegang tot de SDK-aanbiedingen is beperkt tot diegenen met AEM as a Cloud Service licentie.

>[!TIP]
>
>Zorg ervoor u altijd de recentste versie van CIF toe:voegen-aan gebruikt.

### Lokale instelling

Voor lokale ontwikkeling van de CIF Add-on met behulp van de AEM as a Cloud Service SDK:

1. De nieuwste AEM as a Cloud Service SDK ophalen
1. Pak de AEM .jar uit om de `crx-quickstart` map, uitvoeren:

   ```bash
   java -jar <jar name> -unpack
   ```

1. Een `crx-quickstart/install` map
1. Kopieer het juiste archiefbestand voor de verkoopfunctie van de CIF-invoegtoepassing naar de `crx-quickstart/install` map.

   Het ZIP-bestand voor de CIF-invoegtoepassing bevat twee Sling Feature-archiefbestanden `.far` bestanden. Zorg ervoor dat u de juiste SDK gebruikt voor AEM-auteur of AEM-publicatie, afhankelijk van hoe u de lokale AEM as a Cloud Service SDK wilt uitvoeren.

1. Een lokale besturingssysteemomgevingsvariabele maken met de naam `COMMERCE_ENDPOINT` het eindpunt Magento GraphQL vasthouden.

   Voorbeeld Mac OSX:

   ```bash
   export COMMERCE_ENDPOINT=https://<yourmagentosystem>/graphql
   ```

   Voorbeeld van Windows:

   ```bash
   set COMMERCE_ENDPOINT=https://<yourmagentosystem>/graphql
   ```

   Deze variabele wordt gebruikt door AEM om met uw handelssysteem te verbinden. Bovendien omvat de toe:voegen-on CIF een lokale omgekeerde volmacht om het eindpunt van GraphQL van de Handel plaatselijk beschikbaar te maken. Dit wordt gebruikt door de CIF auteurshulpmiddelen (productconsole en plukkers) en voor CIF cliënt-zijcomponenten die directe vraag GraphQL doen.

   Deze variabele moet ook voor de AEM as a Cloud Service omgeving worden ingesteld. Zie voor meer informatie over variabelen [Het vormen OSGi voor AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html#local-development).

1. (Optioneel) Als u niet-actieve catalogusfuncties wilt inschakelen, moet u een integratietoken maken voor uw Magento-instantie. Volg de stappen op [Aan de slag](./getting-started.md#staging) om het token te maken.

   Plaats een geheim OSGi met de naam `COMMERCE_AUTH_HEADER` op de volgende waarde:

   ```xml
   Authorization: Bearer <Access Token>
   ```

   Voor meer informatie over geheimen raadpleegt u [Het vormen OSGi voor AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html#local-development).

1. De AEM as a Cloud Service SDK starten

>[!NOTE]
>
>Zorg ervoor u AEM as a Cloud Service SDK in het zelfde eindvenster begint de omgevingsvariabele in stap 5 werd geplaatst. Als u het in een afzonderlijk eindvenster of door het .jar dossier begint te tweemaal klikken zorg ervoor dat de omgevingsvariabele zichtbaar is.

Verifieer de opstelling via de console OSGI: `http://localhost:4502/system/console/osgi-installer`. De lijst moet de CIF-add-on gerelateerde bundels, het inhoudspakket en de configuraties OSGI bevatten, zoals gedefinieerd in het bestand met het functiemodel.

## Projectinstelling {#project}

Er zijn twee manieren om uw CIF project voor AEM as a Cloud Service op te starten.

### Projectarchetype AEM gebruiken

De [Projectarchetype AEM](https://github.com/adobe/aem-project-archetype) is het belangrijkste hulpmiddel om een vooraf gevormd project op te starten met CIF. De Componenten van de Kern van CIF en alle vereiste configuraties kunnen in een geproduceerd project met één extra optie worden omvat.

>[!TIP]
>
>Gebruik altijd de nieuwste versie van het dialoogvenster [Projectarchetype AEM](https://github.com/adobe/aem-project-archetype/releases) om het project te genereren.

Zie AEM projectarchetype [gebruiksaanwijzingen](https://github.com/adobe/aem-project-archetype#usage) op hoe te om een AEM project te produceren. Als u CIF wilt opnemen in het project, gebruikt u de `includeCommerce` optie.

Bijvoorbeeld:

```bash
mvn -B org.apache.maven.plugins:maven-archetype-plugin:3.2.1:generate \
 -D archetypeGroupId=com.adobe.aem \
 -D archetypeArtifactId=aem-project-archetype \
 -D archetypeVersion=35 \
 -D appTitle="My Site" \
 -D appId="mysite" \
 -D groupId="com.mysite" \
 -D includeCommerce=y
```

CIF de Componenten van de Kern kunnen in om het even welk project worden gebruikt door één van beide te omvatten verstrekt `all` hetzij afzonderlijk met gebruik van het CIF-inhoudspakket en de bijbehorende OSGI-bundels. Om de Componenten van de Kern van CIF aan een project manueel toe te voegen gebruiken de volgende gebiedsdelen:

```java
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>core-cif-components-apps</artifactId>
    <type>zip</type>
    <version>x.y.z</version>
</dependency>
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>core-cif-components-config</artifactId>
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

Een tweede optie om een CIF-project te starten is het klonen en gebruiken van de [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia). De AEM Venia Reference Store is een voorbeeldopslagtoepassing die het gebruik van CIF Core Components voor AEM aantoont. Het is bedoeld als een set voorbeelden van best practices en een mogelijk beginpunt voor het ontwikkelen van uw eigen functionaliteit.

Om aan de slag te gaan met de Venia Reference Store klonen we gewoon de Git-opslagplaats en begint u het project aan te passen aan uw behoeften.

>[!NOTE]
>
>Het project van de Referentieopslag van Venia bevat twee bouwstijlprofielen voor AEM as a Cloud Service en AEM 6.5. Controleer de [project readme.md](https://github.com/adobe/aem-cif-guides-venia/blob/main/README.md) om te zien hoe ze worden gebruikt.

## Aanvullende bronnen

- [Projectarchetype AEM](https://github.com/adobe/aem-project-archetype)
- [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia)
- [Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)
