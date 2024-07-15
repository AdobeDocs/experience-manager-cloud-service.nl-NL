---
title: Meerdere opslagplaatsen gebruiken
description: Leer hoe u meerdere git-opslagruimten beheert wanneer u met Cloud Manager werkt.
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

Leer hoe u meerdere git-opslagruimten beheert wanneer u met Cloud Manager werkt.

## Beheerde Git-opslagruimten synchroniseren {#syncing-customer-managed-git-repositories}

In plaats van direct het werken met Cloud Manager git bewaarplaats, [ klanten kunnen met hun eigen git bewaarplaats ](integrating-with-git.md) of veelvoudige eigen git bewaarplaatsen werken. In deze gevallen moet een geautomatiseerd synchronisatieproces worden ingesteld om ervoor te zorgen dat de Cloud Manager git-opslagplaats altijd up-to-date wordt gehouden.

Afhankelijk van waar de de gokbewaarplaats van de klant wordt ontvangen, zou een actie GitHub of een ononderbroken integratieoplossing zoals Jenkins aan opstelling de automatisering kunnen worden gebruikt. Met een automatisering kan elke stap naar een door de klant bediende it-opslagplaats automatisch worden doorgestuurd naar de Cloud Manager git-opslagplaats.

Hoewel een dergelijke automatisering voor één enkele klant-eigenlijke git bewaarplaats direct door:sturen, vereist het vormen van dit voor veelvoudige bewaarplaatsen een eerste opstelling. De inhoud van meerdere opslagplaatsen voor it moet worden toegewezen aan verschillende directory&#39;s binnen de enkele Cloud Manager-it-opslagplaats. Cloud Manager it-opslagplaats moet zijn voorzien van een hoofdmap Maven `pom.xml` , waarin de verschillende subprojecten worden vermeld in de sectie Modules.

Hieronder volgt een voorbeeldbestand `pom.xml` voor twee in eigendom van de klant zijnde it-opslagruimten.

* Het eerste project wordt in de folder genoemd `project-a` gezet.
* Het tweede project wordt in de folder genoemd `project-b` gezet.

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

Zo&#39;n root `pom.xml` wordt doorgegeven aan een vertakking in de Cloud Manager Git-opslagplaats. Vervolgens moeten de twee projecten zodanig worden ingesteld dat wijzigingen automatisch worden doorgestuurd naar de Cloud Manager git-opslagplaats.

Een mogelijke oplossing zou de volgende zijn.

1. Een actie GitHub kan door een duw aan een tak in project A worden teweeggebracht.
1. De actie checkt project A en de Cloud Manager git dataopslag uit en kopieert alle inhoud van project A naar de directory `project-a` in de Cloud Manager git dataopslag.
1. Vervolgens legt de actie de wijziging vast.

Bijvoorbeeld, wordt een verandering op de belangrijkste tak in project A automatisch geduwd aan de belangrijkste tak in de opslagplaats van de it van Cloud Manager. Er kan een toewijzing tussen vertakkingen zijn, zoals een duw naar een vertakking genoemd `dev` in project A wordt geduwd naar een vertakking genoemd `development` in de opslagplaats van de it van Cloud Manager. Vergelijkbare stappen zijn vereist voor project B.

Afhankelijk van de vertakkingsstrategie en workflows kan de synchronisatie worden geconfigureerd voor verschillende vertakkingen. Als de gebruikte git bewaarplaats geen concept gelijkend op acties GitHub verstrekt, is een integratie door (of gelijkaardig) van Jenkins ook mogelijk. In dit geval activeert een webhaak een Jenkins-taak die het werk doet.

Voer de volgende stappen uit om een nieuwe, derde bron of opslagplaats toe te voegen.

1. Voeg een actie GitHub aan de nieuwe bewaarplaats toe die veranderingen van die bewaarplaats aan Cloud Manager git bewaarplaats duwt.
1. Voer die actie minstens eenmaal uit om ervoor te zorgen dat de projectcode in Cloud Manager git repository is.
1. Voeg een verwijzing naar de nieuwe map toe in de hoofdmap Maven `pom.xml` in de Cloud Manager Git-opslagplaats.

## Voorbeeld van GitHub-actie {#sample-github-action}

Dit is een steekproefGitHub actie die door een duw aan de belangrijkste tak wordt teweeggebracht en dan in een subdirectory van Cloud Manager wordt duwen git bewaarplaats. De GitHub-acties moeten met twee geheimen worden geleverd, `MAIN_USER` en `MAIN_PASSWORD` , om verbinding te kunnen maken met en druk op de Cloud Manager git-opslagplaats.

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
>Het voorbeeldscript gebruikt `git add` om de gegevensopslagruimte bij te werken. Hierbij wordt ervan uitgegaan dat verwijderingen worden opgenomen. Afhankelijk van de standaardconfiguratie van de it moet deze worden vervangen door `git add --all` .

## Sample Jenkins Job {#sample-jenkins-job}

Dit is een voorbeeldscript dat kan worden gebruikt in een Jenkins-taak of vergelijkbaar en dat de volgende flow heeft:

1. Het wordt geactiveerd door een wijziging in een git-opslagplaats.
1. De baan Jenkins controleert de recentste staat van dat project of tak.
1. De taak activeert dit script.
1. Dit script controleert op zijn beurt de Cloud Manager git-opslagplaats en legt de projectcode vast aan een subdirectory.

De Jenkins-taak moet zijn voorzien van twee geheimen, `MAIN_USER` en `MAIN_PASSWORD` , om verbinding te kunnen maken met en te kunnen drukken op de Cloud Manager Git-opslagplaats.

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
>Het voorbeeldscript gebruikt `git add` om de gegevensopslagruimte bij te werken. Hierbij wordt ervan uitgegaan dat verwijderingen worden opgenomen. Afhankelijk van de standaardconfiguratie van de it moet deze worden vervangen door `git add --all` .
