---
title: Ondersteuning voor Git-submodule
description: Leer hoe u Git-submodules kunt gebruiken om de inhoud van meerdere vertakkingen in Git-opslagruimten tijdens het samenstellen samen te voegen.
exl-id: fa5b0f49-4b87-4f39-ad50-7e62094d85f4
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 0712ba8918696f4300089be24cad3e4125416c02
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# Ondersteuning voor Git-submodule voor Adobe-opslagruimten {#git-submodule-support}

Git-submodules kunnen worden gebruikt om de inhoud van meerdere vertakkingen tijdens het samenstellen samen te voegen via Git-opslagruimten.

Wanneer Cloud Manager bouwt proces loopt, klonen het depot van de pijpleiding en controleert de tak. Als er een `.gitmodules` -bestand in de hoofdmap van de vertakking bestaat, wordt de bijbehorende opdracht uitgevoerd.

Het volgende bevel controleert elke submodule in de aangewezen folder.

```
$ git submodule update --init
```

Deze techniek biedt een alternatief aan de oplossing die in [ wordt beschreven Werkend met de Veelvoudige Bewaarplaatsen van de it van Source ](/help/implementing/cloud-manager/managing-code/working-with-multiple-source-git-repositories.md). Het is ideaal voor organisaties die vertrouwd zijn met Git-submodules en liever geen extern samenvoegingsproces beheren.

Stel dat er bijvoorbeeld drie opslagplaatsen zijn. Elke gegevensopslagruimte bevat één vertakking met de naam `main` . In de primaire opslagplaats, dat wil zeggen, die is geconfigureerd in de pijpleidingen, heeft de `main` -vertakking een `pom.xml` -bestand waarmee de projecten in de andere twee opslagplaatsen worden gedeclareerd:

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

Vervolgens voegt u submodules toe voor de andere twee opslagruimten:

```shell
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectA/ project-a
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectB/ project-b
```

Het resultaat is een `.gitmodules` -bestand dat lijkt op het volgende:

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

Zie ook het [ Handboek van de Verwijzing van de Git ](https://git-scm.com/book/en/v2/Git-Tools-Submodules) voor meer informatie over submodules van het Git.

## Gebruiksnotities {#usage-notes}

* De URL voor de it moet exact de syntaxis hebben die in de vorige sectie is beschreven.
* Alleen submodules in de hoofdmap van de vertakking worden ondersteund.
* Sluit om beveiligingsredenen geen referenties in Git-URL&#39;s in.
* Tenzij anders nodig, adviseert Adobe dat u oppervlakkige submodules door het volgende in werking te stellen gebruikt:
  `git config -f .gitmodules submodule.<submodule path>.shallow true` voor elke submodule.
* De verwijzingen van de submodule van de Git worden opgeslagen aan specifieke Git begaat. Dientengevolge, wanneer veranderingen in de submodule bewaarplaats worden aangebracht, begaat referenced moet worden bijgewerkt.
Bijvoorbeeld door het volgende te gebruiken:

  `git submodule update --remote`

## Ondersteuning voor Git-submodule voor privéopslagruimten {#private-repositories}

De steun voor submodules van het Git in [ privé bewaarplaatsen ](private-repositories.md) is over het algemeen gelijkaardig aan hun gebruik met de bewaarplaatsen van Adobe.

Nadat u het `pom.xml` -bestand hebt geconfigureerd en de `git submodule` -opdrachten hebt uitgevoerd, moet u echter een `.gitmodules` -bestand aan de hoofdmap van de aggregatoropslagplaats toevoegen, zodat Cloud Manager de configuratie van de submodule herkent.

![ .gitmodules, bestand ](assets/gitmodules.png)

![ Agregator ](assets/aggregator.png)

### Gebruiksnotities {#usage-notes-recommendations-private-repos}

* URL&#39;s voor Git voor submodules kunnen de HTTPS- of SSH-indeling hebben, maar moeten verwijzen naar een GitHub.com-opslagplaats. Het toevoegen van een Adobe-opslagsubmodule aan een GitHub-aggregatoropslagplaats of het omgekeerde wordt niet ondersteund.
* GitHub-submodules moeten toegankelijk zijn voor de Adobe GitHub App.
* [ de beperkingen van het gebruiken van submodules van het Git met Adobe-Beheerde bewaarplaatsen ](#limitations-recommendations) zijn ook van toepassing.
