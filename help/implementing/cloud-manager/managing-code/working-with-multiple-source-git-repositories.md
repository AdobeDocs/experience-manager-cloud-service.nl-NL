---
title: Meerdere opslagplaatsen gebruiken
description: Leer hoe u meerdere git-opslagruimten beheert wanneer u werkt met Cloud Manager.
exl-id: 1b9cca36-c2d7-4f9e-9733-3f1f4f8b2c7a
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 0%

---

# Meerdere opslagplaatsen gebruiken {#working-with-multiple-source-git-repos}

Leer hoe u meerdere git-opslagruimten beheert wanneer u werkt met Cloud Manager.

## Beheerde Git-opslagruimten synchroniseren {#syncing-customer-managed-git-repositories}

In plaats van rechtstreeks te werken met de git-opslagplaats van Cloud Manager, [klanten kunnen met hun eigen git-opslagsysteem werken](integrating-with-git.md) of meerdere eigen git-opslagplaatsen. In deze gevallen moet een geautomatiseerd synchronisatieproces worden ingesteld om ervoor te zorgen dat de git-opslagplaats van Cloud Manager altijd wordt bijgewerkt.

Afhankelijk van waar de de gokbewaarplaats van de klant wordt ontvangen, zou een actie GitHub of een ononderbroken integratieoplossing zoals Jenkins aan opstelling de automatisering kunnen worden gebruikt. Met een automatisering kan elke stap naar een door de klant bediende git-opslagplaats automatisch worden doorgestuurd naar de git-opslagplaats van Cloud Manager.

Hoewel een dergelijke automatisering voor één enkele klant-eigenlijke git bewaarplaats direct door:sturen, vereist het vormen van dit voor veelvoudige bewaarplaatsen een eerste opstelling. De inhoud van meerdere opslagruimten voor it moet worden toegewezen aan verschillende directory&#39;s in de centrale opslagplaats van Cloud Manager. De git-opslagruimte van Cloud Manager moet zijn ingericht met een hoofdmap `pom.xml`, die van de verschillende subprojecten in de modulesectie een lijst maken.

Hier volgt een voorbeeld `pom.xml` bestand voor twee in eigendom van de klant zijnde it-opslagruimten.

* Het eerste project wordt in de genoemde folder gezet `project-a`.
* Het tweede project wordt in de genoemde folder gezet `project-b`.

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

Een dergelijke wortel `pom.xml` naar een vertakking in de git-opslagplaats van Cloud Manager. Vervolgens moeten de twee projecten zo worden ingesteld dat wijzigingen automatisch worden doorgestuurd naar de git-opslagplaats van Cloud Manager.

Een mogelijke oplossing zou de volgende zijn.

1. Een actie GitHub kan door een duw aan een tak in project A worden teweeggebracht.
1. De actie controleert project A en de de git bewaarplaats van de Manager van de Wolk en kopieert alle inhoud van project A aan de folder `project-a` in de git-opslagplaats van Cloud Manager.
1. Vervolgens legt de actie de wijziging vast.

Een wijziging in de hoofdvertakking in project A wordt bijvoorbeeld automatisch doorgevoerd in de hoofdvertakking in de git-opslagplaats van Cloud Manager. Er kan een toewijzing tussen vertakkingen plaatsvinden, zoals een duw naar een vertakking met de naam `dev` in project A wordt geduwd aan een tak genoemd `development` in de git-opslagplaats van Cloud Manager. Vergelijkbare stappen zijn vereist voor project B.

Afhankelijk van de vertakkingsstrategie en workflows kan de synchronisatie worden geconfigureerd voor verschillende vertakkingen. Als de gebruikte git bewaarplaats geen concept gelijkend op acties GitHub verstrekt, is een integratie door (of gelijkaardig) van Jenkins ook mogelijk. In dit geval activeert een webhaak een Jenkins-taak die het werk doet.

Voer de volgende stappen uit om een nieuwe, derde bron of opslagplaats toe te voegen.

1. Voeg een actie GitHub aan de nieuwe bewaarplaats toe die veranderingen van die bewaarplaats aan de git bewaarplaats van de Manager van de Wolk duwt.
1. Voer die actie ten minste één keer uit om ervoor te zorgen dat de projectcode zich in de git-opslagplaats van Cloud Manager bevindt.
1. Een verwijzing naar de nieuwe map toevoegen in de hoofdmap Maven `pom.xml` in de git-opslagplaats van Cloud Manager.

## Voorbeeld van GitHub-actie {#sample-github-action}

Dit is een steekproefGitHub actie die door een duw aan de belangrijkste tak wordt teweeggebracht en dan in een subdirectory van de git van de Manager van de Wolk duwt. De acties GitHub moeten van twee geheimen worden voorzien, `MAIN_USER` en `MAIN_PASSWORD`om verbinding te kunnen maken met en te kunnen drukken op de git-opslagplaats van Cloud Manager.

```java
name: SYNC
env:
  # Username/email used to commit to Cloud Manager's Git repository
  USER_NAME: <NAME>
  USER_EMAIL: <EMAIL>
  # Directory within the Cloud Manager Git repository
  PROJECT_DIR: project-a
  # Cloud Manager's Git repository
  MAIN_REPOSITORY: https://$MAIN_USER:$MAIN_PASSWORD@git.cloudmanager.adobe.com/<PATH>
  # The branch in Cloud Manager's Git repository to push to
  MAIN_BRANCH : <BRANCH_NAME>
 
# Only run on a push to this branch
on:
  push:
     branches: [ main ]
 
jobs:
  build:
    runs-on: ubuntu-latest
 
    steps:
      # Checkout this project into a sub folder
      - uses: actions/checkout@v2
        with:
          path: sub
      # Cleanup sub project
      - name: Clean project
        run: |
          git -C sub log --format="%an : %s" -n 1 > commit.txt
          rm -rf sub/.git
          rm -rf sub/.github
      # Set global git configuration
      - name: Set git config
        run: |
          git config --global credential.helper cache
          git config --global user.email ${USER_EMAIL}
          git config --global user.name ${USER_NAME}
      # Checkout the main project
      - name: Checkout main project
        run:
          git clone -b ${MAIN_BRANCH} ${MAIN_REPOSITORY} ${MAIN_BRANCH} 
      # Move sub project
      - name: Move project to main project
        run: |
          rm -rf ${MAIN_BRANCH}/${PROJECT_DIR} 
          mv sub ${MAIN_BRANCH}/${PROJECT_DIR}
      - name: Commit Changes
        run: |
          git -C ${MAIN_BRANCH} add -f ${PROJECT_DIR}
          git -C ${MAIN_BRANCH} commit -F ../commit.txt
          git -C ${MAIN_BRANCH} push
```

Het gebruiken van een actie GitHub is flexibel. Elke toewijzing tussen vertakkingen van de it-opslagplaatsen kan worden uitgevoerd en elke toewijzing van de afzonderlijke it-projecten aan de mappenindeling van het hoofdproject.

>[!NOTE]
>
>Het voorbeeldscript gebruikt `git add` om de repository bij te werken. Hierbij wordt ervan uitgegaan dat verwijderingen worden opgenomen. Afhankelijk van de standaardconfiguratie van it moet deze worden vervangen door `git add --all`.

## Sample Jenkins Job {#sample-jenkins-job}

Dit is een voorbeeldscript dat kan worden gebruikt in een Jenkins-taak of vergelijkbaar en dat de volgende flow heeft:

1. Het wordt geactiveerd door een wijziging in een git-opslagplaats.
1. De baan Jenkins controleert de recentste staat van dat project of tak.
1. De taak activeert dit script.
1. Met dit script wordt op zijn beurt de git-opslagplaats van Cloud Manager uitgecheckt en wordt de projectcode toegewezen aan een submap.

De baan Jenkins moet van twee geheimen worden voorzien, `MAIN_USER` en `MAIN_PASSWORD`om verbinding te kunnen maken met en te kunnen drukken op de git-opslagplaats van Cloud Manager.

```java
# Username/email used to commit to Cloud Manager's Git repository
export USER_NAME=<NAME>
export USER_EMAIL=<EMAIL>
# Directory within the Cloud Manager Git repository
export PROJECT_DIR=project-a
# Cloud Manager's Git repository
export MAIN_REPOSITORY=https://$MAIN_USER:$MAIN_PASSWORD@git.cloudmanager.adobe.com/<PATH>
# The branch in Cloud Manager's Git repository to push to
export MAIN_BRANCH=<BRANCH_NAME>
 
# clean up and init
rm -rf target
mkdir target
 
# mv project to sub folder
mkdir target/sub
for f in .* *
do
    if [ "$f" != "." -a "$f" != ".." -a "$f" != "target" ]
    then
        mv "$f" target/sub
    fi
done
cd target
 
# capture log and remove git info
cd sub
git log --format="%an : %s" -n 1 > ../commit.txt
rm -rf .git
rm -rf .github
cd ..
 
# checkout main repository
git clone -b $MAIN_BRANCH $MAIN_REPOSITORY main
cd main
 
# configure main repository
git config credential.helper cache
git config user.email $USER_EMAIL
git config user.name $USER_NAME
 
# update project in main
rm -rf $PROJECT_DIR
mv ../sub $PROJECT_DIR
 
# commit changes to main
git add -f $PROJECT_DIR
git commit -F ../commit.txt
git push
```

Het gebruik van een Jenkins-taak is flexibel. Elke toewijzing tussen vertakkingen van de it-opslagplaatsen kan worden uitgevoerd en elke toewijzing van de afzonderlijke it-projecten aan de mappenindeling van het hoofdproject.

>[!NOTE]
>
>Het voorbeeldscript gebruikt `git add` om de repository bij te werken. Hierbij wordt ervan uitgegaan dat verwijderingen worden opgenomen. Afhankelijk van de standaardconfiguratie van it moet deze worden vervangen door `git add --all`.
