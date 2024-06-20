---
title: Ondersteuning voor Git-submodule
description: Leer hoe u Git-submodules kunt gebruiken om de inhoud van meerdere vertakkingen in git-opslagruimten tijdens het samenstellen samen te voegen.
exl-id: fa5b0f49-4b87-4f39-ad50-7e62094d85f4
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# Ondersteuning voor Git-submodule voor opslagplaatsen voor Adoben {#git-submodule-support}

Git-submodules kunnen worden gebruikt om de inhoud van meerdere vertakkingen tijdens het samenstellen samen te voegen tussen git-opslagruimten.

Wanneer het de bouwstijlproces van de Manager van de Wolk uitvoert, nadat de bewaarplaats die voor de pijpleiding wordt gevormd wordt gekloond en de gevormde tak wordt gecontroleerd, als de tak een bevat `.gitmodules` in de hoofdmap, wordt de opdracht uitgevoerd.

Het volgende bevel zal elke submodule in de aangewezen folder uitchecken.

```
$ git submodule update --init
```

Deze techniek is een mogelijk alternatief voor de in het document beschreven oplossing [Werken met Meerdere bronopslaglocaties voor Git](/help/implementing/cloud-manager/managing-code/working-with-multiple-source-git-repositories.md) voor organisaties die comfortabel zijn met het gebruik van git-submodules en geen extern samenvoegingsproces willen beheren.

Stel bijvoorbeeld dat er drie opslagruimten zijn die elk één vertakking met de naam `main`. In de primaire opslagplaats, d.w.z. die gevormd in de pijpleidingen, `main` vertakking bevat een `pom.xml` dossier waarin de projecten in de andere twee gegevensbanken worden verklaard.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="https://maven.apache.org/POM/4.0.0" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="https://maven.apache.org/POM/4.0.0 https://maven.apache.org/maven-v4_0_0.xsd">
    <modelVersion>4.0.0</modelVersion>
   
    <groupId>customer.group.id</groupId>
    <artifactId>customer-reactor</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <packaging>pom</packaging>
   
    <modules>
        <module>project-a</module>
        <module>project-b</module>
    </modules>
   
</project>
```

Vervolgens voegt u submodules toe voor de andere twee opslagruimten.

```shell
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectA/ project-a
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectB/ project-b
```

Dit leidt tot een `.gitmodules` bestand, vergelijkbaar met het volgende.

```text
[submodule "project-a"]
    path = project-a
    url = https://git.cloudmanager.adobe.com/ProgramName/projectA/
    branch = main
[submodule "project-b"]
    path = project-b
    url = https://git.cloudmanager.adobe.com/ProgramName/projectB/
    branch = main
```

Meer informatie over git-submodules vindt u in de [Git Reference Manual.](https://git-scm.com/book/en/v2/Git-Tools-Submodules)

### Beperkingen en Recommendations {#limitations-recommendations}

Houd rekening met de volgende beperkingen wanneer u git-submodules gebruikt met opslagruimten die door Adobe worden beheerd.

* De URL van de it moet exact de syntaxis hebben die in de vorige sectie wordt beschreven.
* Alleen submodules in de hoofdmap van de vertakking worden ondersteund.
* Omwille van de beveiliging mag u referenties niet insluiten in URL&#39;s met git.
* Tenzij anders nodig, wordt het ten zeerste aanbevolen oppervlakkige submodules te gebruiken.
   * Voer hiervoor `git config -f .gitmodules submodule.<submodule path>.shallow true` voor elke submodule.
* Verwijzingen naar de Git-submodule worden opgeslagen naar specifieke it-opdrachten. Dientengevolge, wanneer veranderingen in de submodule bewaarplaats worden aangebracht, begaat referenced moet worden bijgewerkt.
   * Bijvoorbeeld door `git submodule update --remote`

## Ondersteuning voor Git-submodule voor privéopslagplaatsen {#private-repositories}

Ondersteuning voor it-submodules bij gebruik [privéopslagplaatsen](private-repositories.md) is grotendeels hetzelfde als bij het gebruik van gegevensbanken voor Adoben.

Na het instellen van uw `pom.xml` en het bestand uitvoeren `git submodule` opdrachten, moet u een `.gitmodules` bestand naar de hoofdmap van de aggregatoropslagplaats voor Cloud Manager om de installatie van de submodule te detecteren.

![.gitmodules, bestand](assets/gitmodules.png)

![aggregator](assets/aggregator.png)

### Beperkingen en Recommendations {#limitations-recommendations-private-repos}

Houd rekening met de volgende beperkingen wanneer u git-submodules gebruikt met persoonlijke opslagruimten.

* De URL&#39;s van de it voor de submodules kunnen de HTTPS- of SSH-indeling hebben, maar ze moeten een koppeling naar een github.com-opslagplaats maken
   * Het toevoegen van een ondermodule van de opslagplaats van de Adobe aan een aggregatorbewaarplaats GitHub of vice versa zal niet werken.
* De ondermodules GitHub moeten voor de AdobeApp toegankelijk zijn GitHub.
* [De beperkingen van het gebruik van git-submodules met door Adobe beheerde opslagplaatsen](#limitations-recommendations) ook van toepassing.
