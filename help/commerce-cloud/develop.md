---
title: Ontwikkelen AEM Commerce voor AEM as a Cloud Service
description: Leer hoe te om een handel-toegelaten AEM project te produceren gebruikend het AEM projectarchetype. Leer hoe u het project bouwt en implementeert in een lokale ontwikkelomgeving met de SDK van AEM as a Cloud Service.
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

Een lokale ontwikkelomgeving wordt aanbevolen voor CIF projecten. De CIF invoegtoepassing voor AEM as a Cloud Service is ook beschikbaar voor lokale ontwikkeling. Het kan van het [ portaal van de Distributie van de Software worden gedownload ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html).

De CIF Add-On wordt geleverd als een archief met verkoopfuncties. Het ZIP-bestand dat beschikbaar is op de portal Softwaredistributie bevat twee Sling Feature-archiefbestanden: een voor AEM auteur en een voor AEM publicatie-instanties.

**Nieuw aan AEM as a Cloud Service?** Controle uit [ een meer gedetailleerde gids aan vestiging een lokale ontwikkelomgeving gebruikend AEM as a Cloud Service SDK ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html).

### Vereiste software

Het volgende moet lokaal worden geïnstalleerd:

- [AEM as a Cloud Service SDK](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/aem-runtime.html#download-the-aem-as-a-cloud-service-sdk)
- [ Java™ 11 ](https://downloads.experiencecloud.adobe.com/content/software-distribution/en/general.html)
- [ Apache Maven ](https://maven.apache.org/) (3.3.9 of nieuwer)
- [ Node.js v10+ ](https://nodejs.org/en)
- [ npm 6+ ](https://www.npmjs.com/)
- [ Git ](https://git-scm.com/)

### Toegang tot de CIF

CIF toe:voegen-op kan als zip dossier van het [ portaal van de Distributie van de Software ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) worden gedownload. Het zip dossier bevat CIF toe:voegen-op als **het Sling archief van de Eigenschap**, is het geen AEM pakket. Aanbiedingen in SDK zijn toegankelijk met een AEM as a Cloud Service-licentie.

>[!TIP]
>
>Zorg ervoor u altijd de recentste versie CIF toe:voegen-aan gebruikt.

### Lokale instelling

Voor ontwikkeling van lokale CIF Add-on met de AEM as a Cloud Service SDK gaat u als volgt te werk:

1. De nieuwste AEM as a Cloud Service SDK ophalen
1. Pak de AEM .jar uit zodat u de `crx-quickstart` -map kunt maken, voer dan de volgende handelingen uit:

   ```bash
   java -jar <jar name> -unpack
   ```

1. Een `crx-quickstart/install` -map maken
1. Kopieer het juiste archiefbestand voor de verkoopfunctie van de CIF add-on naar de map `crx-quickstart/install` .

   Het ZIP-bestand met CIF add-on bevat twee archiefbestanden voor de verkoopfunctie `.far` . Zorg ervoor dat u de juiste naam gebruikt voor AEM auteur of AEM Publish, afhankelijk van hoe u de lokale AEM as a Cloud Service SDK wilt uitvoeren.

1. Maak een lokale besturingssysteemomgevingsvariabele met de naam `COMMERCE_ENDPOINT` die het Adobe Commerce GraphQL-eindpunt vasthoudt.

   Voorbeeld macOS X:

   ```bash
   export COMMERCE_ENDPOINT=https://<yourcommercesystem>/graphql
   ```

   Voorbeeld van Windows:

   ```bash
   set COMMERCE_ENDPOINT=https://<yourcommercesystem>/graphql
   ```

   Deze variabele wordt gebruikt door AEM om met uw handelssysteem te verbinden. Bovendien bevat de CIF add-on een lokale reverse-proxy waarmee het Commerce GraphQL-eindpunt lokaal beschikbaar wordt gemaakt. Deze volmacht wordt gebruikt door de CIF auteurshulpmiddelen (productconsole en plukkers) en voor de CIF cliënt-zijcomponenten die directe vraag van GraphQL doen.

   Deze variabele moet ook voor de AEM as a Cloud Service-omgeving worden ingesteld. Voor meer informatie over variabelen, zie [ het Vormen OSGi voor AEM as a Cloud Service ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/configuring-osgi.html#local-development).

1. (Optioneel) Als u niet-actieve catalogusfuncties wilt inschakelen, moet u een integratietoken maken voor uw Adobe Commerce-instantie. Volg de stappen bij [ Begonnen het worden ](./getting-started.md#staging) om het teken tot stand te brengen.

   Stel een geheim OSGi met de naam `COMMERCE_AUTH_HEADER` in op de volgende waarde:

   ```xml
   Authorization: Bearer <Access Token>
   ```

   Voor meer informatie over geheimen, zie [ Vormend OSGi voor AEM as a Cloud Service ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/configuring-osgi.html#local-development).

1. De SDK van AEM as a Cloud Service starten

>[!NOTE]
>
>Zorg ervoor dat u AEM as a Cloud Service SDK start in hetzelfde terminalvenster dat de omgevingsvariabele is ingesteld in stap 5. Als u het in een afzonderlijk eindvenster, of door het .jar dossier tweemaal te klikken begint, zorg ervoor dat de omgevingsvariabele zichtbaar is.

Controleer de installatie via de OSGI-console: `http://localhost:4502/system/console/osgi-installer` . De lijst moet de CIF add-on gerelateerde bundels, content-package en OSGI-configuraties bevatten, zoals gedefinieerd in het bestand met het functiemodel.

## Projectinstelling {#project}

Er zijn twee manieren om uw CIF project voor AEM as a Cloud Service te Bootstrappen.

### Projectarchetype AEM gebruiken

Het [ AEM Archetype van het Project ](https://github.com/adobe/aem-project-archetype) is het belangrijkste hulpmiddel om een vooraf gevormd project te Bootstrappen om met CIF begonnen te worden. CIF de Componenten van de Kern en alle vereiste configuraties kunnen in een geproduceerd project met één extra optie worden omvat.

>[!TIP]
>
>Gebruik altijd de recentste versie van [ AEM Archetype van het Project ](https://github.com/adobe/aem-project-archetype/releases) zodat kunt u het project produceren.

Zie AEM het gebruiksinstructies van de Archetype van het Project [ ](https://github.com/adobe/aem-project-archetype#usage) op hoe te om een AEM project te produceren. Als u CIF in het project wilt opnemen, gebruikt u de optie `includeCommerce` .

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

CIF Core Components kunnen in elk project worden gebruikt door het meegeleverde `all` -pakket op te nemen of afzonderlijk met behulp van het pakket met CIF inhoud en verwante OSGI-bundels. Om CIF de Componenten van de Kern aan een project manueel toe te voegen, gebruik de volgende gebiedsdelen:

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

Een tweede optie om een CIF project te beginnen is het [ AEM de Opslag van de Verwijzing van Venia ](https://github.com/adobe/aem-cif-guides-venia) te klonen en te gebruiken. De AEM Venia Reference Store is een voorbeeldtoepassing van de verwijzingsopslag die het gebruik van CIF Core Components voor AEM aantoont. Het is bedoeld als een set voorbeelden van best practices en een mogelijk beginpunt voor het ontwikkelen van uw eigen functionaliteit.

Om aan de slag te gaan met de Venia Reference Store, kloont u de Git-opslagplaats en begint u het project aan te passen aan uw behoeften.

>[!NOTE]
>
>Het Venia Reference Store-project bevat twee buildprofielen voor AEM as a Cloud Service en AEM 6.5. Controle [ project readme.md ](https://github.com/adobe/aem-cif-guides-venia/blob/main/README.md) zodat kunt u zien hoe zij worden gebruikt.

## Aanvullende bronnen

- [ AEM Archetype van het Project ](https://github.com/adobe/aem-project-archetype)
- [AEM Venia Reference Store ](https://github.com/adobe/aem-cif-guides-venia)
- [ portal van de Distributie van de Software ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)
