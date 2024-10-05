---
title: Meerdere opslagplaatsen gebruiken
description: Leer hoe u meerdere Git-opslagruimten beheert wanneer u met Cloud Manager werkt.
exl-id: 1b9cca36-c2d7-4f9e-9733-3f1f4f8b2c7a
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: b8b1748f9c50178fbcb167370c53285b55d809b1
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 0%

---

# Meerdere opslagplaatsen gebruiken {#working-with-multiple-source-git-repos}

Leer hoe u meerdere Git-opslagruimten beheert wanneer u met Cloud Manager werkt.

## Persoonlijke Git-opslagruimten synchroniseren {#syncing-customer-managed-git-repositories}

In plaats van direct werkend met de bewaarplaats van de Git van Cloud Manager, [ kunnen de klanten met hun eigen privé bewaarplaats van het Git ](integrating-with-git.md) of veelvoudige eigen bewaarplaatsen van het Git werken. In deze gevallen moet u een geautomatiseerd synchronisatieproces opzetten om ervoor te zorgen dat de Git-opslagplaats in Cloud Manager altijd up-to-date blijft.

Afhankelijk van waar de gegevensopslagplaats van het Git van de klant wordt ontvangen, zou een actie GitHub of een ononderbroken integratieoplossing zoals Jenkins aan opstelling de automatisering kunnen worden gebruikt. Met een automatische installatie kan elke push naar een Git-opslagplaats in eigendom van de klant automatisch worden doorgestuurd naar de Cloud Manager Git-opslagplaats.

Hoewel een dergelijke automatisering voor één enkele klant-eigendom van de opslagplaats van het Git direct door:sturen, vereist het vormen van het voor veelvoudige bewaarplaatsen een aanvankelijke opstelling. De inhoud van meerdere Git-opslagplaatsen moet worden toegewezen aan verschillende directory&#39;s binnen de enige Cloud Manager Git-opslagplaats. De Cloud Manager Git-opslagplaats moet zijn ingericht met een hoofdmap Maven `pom.xml` , waarin de verschillende subprojecten worden vermeld in de sectie Modules.

Hieronder volgt een voorbeeldbestand `pom.xml` voor twee Git-opslagruimten die eigendom zijn van klanten.

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

Zo&#39;n root `pom.xml` wordt doorgegeven aan een vertakking in de Cloud Manager Git-opslagplaats. Vervolgens moeten de twee projecten zo worden ingesteld dat wijzigingen automatisch worden doorgestuurd naar de Cloud Manager Git-opslagplaats.

Een mogelijke oplossing zou de volgende zijn.

1. Trigger een actie GitHub door aan een tak in project A te duwen.
1. Met de actie worden project A en de Cloud Manager Git-opslagplaats uitgecheckt. Vervolgens wordt alle inhoud van project A gekopieerd naar de map `project-a` in de Cloud Manager Git-opslagplaats.
1. Vervolgens legt de actie de wijziging vast.

Een wijziging van de hoofdvertakking in project A wordt bijvoorbeeld automatisch doorgevoerd in de hoofdvertakking in de Cloud Manager Git-opslagplaats. Er kan een toewijzing tussen vertakkingen zijn, zoals een duw naar een vertakking genoemd `dev` in project A wordt geduwd aan een vertakking genoemd `development` in de gegevensopslagplaats van de Git van Cloud Manager. Vergelijkbare stappen zijn vereist voor project B.

Afhankelijk van de vertakkingsstrategie en workflows kan de synchronisatie worden geconfigureerd voor verschillende vertakkingen. Als de gebruikte gegevensopslagplaats van de Git geen concept gelijkend op acties GitHub verstrekt, is een integratie door (of gelijkaardig) van Jenkins ook mogelijk. In dit geval activeert een webhaak een Jenkins-taak, die het werk doet.

Voer de volgende stappen uit om een nieuwe, derde bron of opslagplaats toe te voegen.

1. Voeg een actie GitHub aan de nieuwe bewaarplaats toe, die veranderingen van die bewaarplaats aan de bewaarplaats van het Git van Cloud Manager duwt.
1. Voer die actie minstens eenmaal uit om ervoor te zorgen dat de projectcode in de gegevensopslagplaats van het Git van Cloud Manager is.
1. Voeg in de Cloud Manager Git-opslagplaats een verwijzing naar de nieuwe map toe in de hoofdmap Maven `pom.xml` .



## Voorbeeld van actie GitHub {#sample-github-action}

Hier volgt een voorbeeld van een GitHub-actie die door een push naar de hoofdvertakking wordt geactiveerd. Vervolgens wordt naar een submap van de Cloud Manager Git-opslagplaats geduwd. De GitHub-acties moeten met twee geheimen worden geleverd, `MAIN_USER` en `MAIN_PASSWORD` , om verbinding te kunnen maken met en druk op de Cloud Manager Git-opslagplaats.

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

Het gebruiken van een actie GitHub is flexibel. Elke toewijzing tussen vertakkingen van de Git-opslagplaatsen kan worden uitgevoerd en elke toewijzing van de afzonderlijke Git-projecten aan de mappenlay-out van het hoofdproject.

>[!NOTE]
>
>Het voorbeeldscript gebruikt `git add` om de gegevensopslagruimte bij te werken. In het script wordt ervan uitgegaan dat verwijderingen worden opgenomen. Afhankelijk van de standaardconfiguratie van Git, moet deze worden vervangen door `git add --all` .

## Sample Jenkins-taak {#sample-jenkins-job}

Hier volgt een voorbeeldscript dat kan worden gebruikt in een Jenkins-taak of vergelijkbaar en dat de volgende flow heeft:

1. Het wordt geactiveerd door een wijziging in een Git-opslagplaats.
1. De baan Jenkins controleert de recentste staat van dat project of tak.
1. De taak activeert dit script.
1. Dit script zoekt op zijn beurt de Cloud Manager Git-opslagplaats uit en legt de projectcode vast aan een subdirectory.

De Jenkins-taak moet twee geheimen hebben, `MAIN_USER` en `MAIN_PASSWORD` , om verbinding te kunnen maken met en te kunnen drukken op de Cloud Manager Git-opslagplaats.

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

Het gebruik van een Jenkins-taak is flexibel. Elke toewijzing tussen vertakkingen van de Git-opslagplaatsen kan worden uitgevoerd en elke toewijzing van de afzonderlijke Git-projecten aan de mappenlay-out van het hoofdproject.

>[!NOTE]
>
>Het voorbeeldscript gebruikt `git add` om de gegevensopslagruimte bij te werken. In het script wordt ervan uitgegaan dat verwijderingen worden opgenomen. Afhankelijk van de standaardconfiguratie van Git, moet deze worden vervangen door `git add --all` .
