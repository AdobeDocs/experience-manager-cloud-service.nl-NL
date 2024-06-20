---
title: Ontwikkelen AEM Commerce voor AEM as a Cloud Service
description: Leer hoe te om een handel-toegelaten AEM project te produceren gebruikend het AEM projectarchetype. Leer hoe u het project bouwt en implementeert in een lokale ontwikkelomgeving met de AEM as a Cloud Service SDK.
topics: Commerce, Development
feature: Commerce Integration Framework
version: Cloud Service
doc-type: tutorial
kt: 5826
thumbnail: 39476.jpg
exl-id: 6f28a52b-52f8-4b30-95cd-0f9cb521de62
role: Admin
source-git-commit: 0e328d013f3c5b9b965010e4e410b6fda2de042e
workflow-type: tm+mt
source-wordcount: '908'
ht-degree: 2%

---

# Ontwikkelen AEM Commerce voor AEM as a Cloud Service {#develop}

Voor de ontwikkeling AEM Commerce-projecten, gebaseerd op Commerce integration framework (CIF) voor AEM as a Cloud Service, gelden dezelfde regels en beste praktijken als voor andere AEM projecten op AEM as a Cloud Service. Lees eerst het volgende:

- [AEM-projectstructuur](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html)
- [AEM as a Cloud Service SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-as-a-cloud-service-sdk.html)
- [Ontwikkelingsrichtlijnen voor AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines.html)

## Lokale ontwikkeling met AEM as a Cloud Service SDK {#local}

>[!VIDEO](https://video.tv.adobe.com/v/39476/?quality=12&learn=on)

Een lokale ontwikkelomgeving wordt aanbevolen voor CIF projecten. De CIF Add-on die voor AEM as a Cloud Service is voorzien, is ook beschikbaar voor lokale ontwikkeling. Het kan worden gedownload van [Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html).

De CIF Add-On wordt geleverd als een archief met verkoopfuncties. Het ZIP-bestand dat beschikbaar is op de portal Softwaredistributie bevat twee Sling Feature-archiefbestanden: een voor AEM auteur en een voor AEM publicatie-instanties.

**Nieuw bij AEM as a Cloud Service?** Uitchecken [een gedetailleerdere handleiding voor het instellen van een lokale ontwikkelomgeving met behulp van de AEM as a Cloud Service SDK](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html).

### Vereiste software

Het volgende moet lokaal worden geïnstalleerd:

- [AEM as a Cloud Service SDK](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/aem-runtime.html#download-the-aem-as-a-cloud-service-sdk)
- [Java™ 11](https://downloads.experiencecloud.adobe.com/content/software-distribution/en/general.html)
- [Apache Maven](https://maven.apache.org/) (3.3.9 of hoger)
- [Node.js v10+](https://nodejs.org/en)
- [npm 6+](https://www.npmjs.com/)
- [Git](https://git-scm.com/)

### Toegang tot de CIF

De CIF invoegtoepassing kan als een zip-bestand worden gedownload van het tabblad [Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html). Het ZIP-bestand bevat de CIF add-on als **Sling Feature-archief** Het is echter geen AEM pakket. Aanbiedingen in SDK zijn toegankelijk met een AEM as a Cloud Service licentie.

>[!TIP]
>
>Zorg ervoor u altijd de recentste versie CIF toe:voegen-aan gebruikt.

### Lokale instelling

Voor ontwikkeling van lokale CIF Add-on met de AEM as a Cloud Service SDK gaat u als volgt te werk:

1. De nieuwste AEM as a Cloud Service SDK ophalen
1. De AEM .jar uitpakken zodat u de `crx-quickstart` map, uitvoeren:

   ```bash
   java -jar <jar name> -unpack
   ```

1. Een `crx-quickstart/install` map
1. Kopieer het correcte archiefbestand voor de verkoopfunctie van de CIF invoegtoepassing naar het `crx-quickstart/install` map.

   Het ZIP-bestand met CIF add-on bevat twee Sling Feature-archiefbestanden `.far` bestanden. Zorg ervoor om correcte voor AEM Auteur of AEM te gebruiken publiceren, afhankelijk van hoe u van plan bent om lokale AEM as a Cloud Service SDK in werking te stellen.

1. Een lokale besturingssysteemomgevingsvariabele maken met de naam `COMMERCE_ENDPOINT` het Adobe Commerce GraphQL-eindpunt vast te houden.

   Voorbeeld macOS X:

   ```bash
   export COMMERCE_ENDPOINT=https://<yourcommercesystem>/graphql
   ```

   Voorbeeld van Windows:

   ```bash
   set COMMERCE_ENDPOINT=https://<yourcommercesystem>/graphql
   ```

   Deze variabele wordt gebruikt door AEM om met uw handelssysteem te verbinden. Bovendien bevat de CIF add-on een lokale reverse-proxy waarmee het Commerce GraphQL-eindpunt lokaal beschikbaar wordt gemaakt. Deze volmacht wordt gebruikt door de CIF auteurshulpmiddelen (productconsole en plukkers) en voor de CIF cliënt-zijcomponenten die directe vraag van GraphQL doen.

   Deze variabele moet ook voor de AEM as a Cloud Service omgeving worden ingesteld. Zie voor meer informatie over variabelen [Het vormen OSGi voor AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/configuring-osgi.html#local-development).

1. (Optioneel) Als u niet-actieve catalogusfuncties wilt inschakelen, moet u een integratietoken maken voor uw Adobe Commerce-instantie. Voer de stappen uit bij [Aan de slag](./getting-started.md#staging) om het token te maken.

   Plaats een geheim OSGi met de naam `COMMERCE_AUTH_HEADER` op de volgende waarde:

   ```xml
   Authorization: Bearer <Access Token>
   ```

   Zie voor meer informatie over geheimen [Het vormen OSGi voor AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/configuring-osgi.html#local-development).

1. De AEM as a Cloud Service SDK starten

>[!NOTE]
>
>Zorg ervoor u AEM as a Cloud Service SDK in het zelfde eindvenster begint de omgevingsvariabele in stap 5 werd geplaatst. Als u het in een afzonderlijk eindvenster, of door het .jar dossier tweemaal te klikken begint, zorg ervoor dat de omgevingsvariabele zichtbaar is.

Verifieer de opstelling via de console OSGI: `http://localhost:4502/system/console/osgi-installer`. De lijst moet de CIF add-on gerelateerde bundels, content-package en OSGI-configuraties bevatten, zoals gedefinieerd in het bestand met het functiemodel.

## Projectinstelling {#project}

Er zijn twee manieren om uw CIF project voor AEM as a Cloud Service te Bootstrappen.

### Projectarchetype AEM gebruiken

De [Projectarchetype AEM](https://github.com/adobe/aem-project-archetype) is het belangrijkste hulpmiddel om een vooraf gevormd project te Bootstrappen om met CIF te beginnen. CIF de Componenten van de Kern en alle vereiste configuraties kunnen in een geproduceerd project met één extra optie worden omvat.

>[!TIP]
>
>Gebruik altijd de nieuwste versie van het dialoogvenster [Projectarchetype AEM](https://github.com/adobe/aem-project-archetype/releases) zodat kunt u het project produceren.

Zie AEM projectarchetype [gebruiksaanwijzingen](https://github.com/adobe/aem-project-archetype#usage) op hoe te om een AEM project te produceren. Als u CIF in het project wilt opnemen, gebruikt u de opdracht `includeCommerce` -optie.

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

CIF de Componenten van de Kern kunnen in om het even welk project worden gebruikt door één van beide inbegrepen verstrekte `all` afzonderlijk of met behulp van het CIF-inhoudspakket en de bijbehorende OSGI-bundels. Om CIF de Componenten van de Kern aan een project manueel toe te voegen, gebruik de volgende gebiedsdelen:

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

Een tweede optie om een CIF project te starten is het klonen en gebruiken van de [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia). De AEM Venia Reference Store is een voorbeeldtoepassing van de verwijzingsopslag die het gebruik van CIF Core Components voor AEM aantoont. Het is bedoeld als een set voorbeelden van best practices en een mogelijk beginpunt voor het ontwikkelen van uw eigen functionaliteit.

Om aan de slag te gaan met de Venia Reference Store, kloont u de Git-opslagplaats en begint u het project aan te passen aan uw behoeften.

>[!NOTE]
>
>Het project van de Referentieopslag van Venia bevat twee bouwstijlprofielen voor AEM as a Cloud Service en AEM 6.5. Controleren [project readme.md](https://github.com/adobe/aem-cif-guides-venia/blob/main/README.md) zodat u kunt zien hoe zij worden gebruikt.

## Aanvullende bronnen

- [Projectarchetype AEM](https://github.com/adobe/aem-project-archetype)
- [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia)
- [Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)
