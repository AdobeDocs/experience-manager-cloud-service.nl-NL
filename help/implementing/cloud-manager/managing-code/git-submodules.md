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

Wanneer het Cloud Manager-bouwproces wordt uitgevoerd, nadat de opslagplaats die voor de pijplijn is geconfigureerd, is gekloond en de geconfigureerde vertakking is uitgecheckt, wordt de opdracht uitgevoerd als de vertakking een `.gitmodules` -bestand in de hoofdmap bevat.

Het volgende bevel zal elke submodule in de aangewezen folder uitchecken.

```
$ git submodule update --init
```

Deze techniek is een potentieel alternatief aan de oplossing die in het document [ wordt beschreven Werkend met de Veelvoudige Bewaarplaatsen van de it van Source ](/help/implementing/cloud-manager/managing-code/working-with-multiple-source-git-repositories.md) voor organisaties die met het gebruiken van git submodules comfortabel zijn en geen extern het samenvoegen proces willen beheren.

Stel dat er drie opslagruimten zijn die elk één vertakking met de naam `main` bevatten. In de primaire opslagplaats, dat wil zeggen, die is geconfigureerd in de pijpleidingen, heeft de `main` -vertakking een `pom.xml` -bestand waarmee de projecten in de andere twee opslagplaatsen worden gedeclareerd.

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

Dit resulteert in een `.gitmodules` -bestand dat vergelijkbaar is met het volgende.

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

Meer informatie over git submodules kan in het [ Handboek van de Verwijzing van de it worden gevonden.](https://git-scm.com/book/en/v2/Git-Tools-Submodules)

### Beperkingen en Recommendations {#limitations-recommendations}

Houd rekening met de volgende beperkingen wanneer u git-submodules gebruikt met opslagruimten die door Adobe worden beheerd.

* De URL van de it moet exact de syntaxis hebben die in de vorige sectie wordt beschreven.
* Alleen submodules in de hoofdmap van de vertakking worden ondersteund.
* Omwille van de beveiliging mag u referenties niet insluiten in URL&#39;s met git.
* Tenzij anders nodig, wordt het ten zeerste aanbevolen oppervlakkige submodules te gebruiken.
   * Voer hiervoor `git config -f .gitmodules submodule.<submodule path>.shallow true` uit voor elke submodule.
* Verwijzingen naar de Git-submodule worden opgeslagen naar specifieke it-opdrachten. Dientengevolge, wanneer veranderingen in de submodule bewaarplaats worden aangebracht, begaat referenced moet worden bijgewerkt.
   * Bijvoorbeeld met `git submodule update --remote`

## Ondersteuning voor Git-submodule voor privéopslagplaatsen {#private-repositories}

Steun voor git submodules wanneer het gebruiken van [ privé bewaarplaatsen ](private-repositories.md) is grotendeels het zelfde als wanneer het gebruiken van de bewaarplaatsen van de Adobe.

Nadat u het `pom.xml` -bestand hebt ingesteld en de `git submodule` -opdrachten hebt uitgevoerd, moet u echter een `.gitmodules` -bestand aan de hoofdmap van de aggregatoropslagplaats toevoegen, zodat Cloud Manager de installatie van de submodule kan detecteren.

![ .gitmodules, bestand ](assets/gitmodules.png)

![ Agregator ](assets/aggregator.png)

### Beperkingen en Recommendations {#limitations-recommendations-private-repos}

Houd rekening met de volgende beperkingen wanneer u git-submodules gebruikt met persoonlijke opslagruimten.

* De URL&#39;s van de it voor de submodules kunnen de HTTPS- of SSH-indeling hebben, maar ze moeten een koppeling naar een github.com-opslagplaats maken
   * Het toevoegen van een ondermodule van de opslagplaats van de Adobe aan een aggregatorbewaarplaats GitHub of vice versa zal niet werken.
* De ondermodules GitHub moeten voor de AdobeApp toegankelijk zijn GitHub.
* [ de beperkingen om git submodules met Adobe-geleide bewaarplaatsen ](#limitations-recommendations) te gebruiken zijn ook van toepassing.
