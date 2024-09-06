---
title: Het vormen Variabelen van de Pijpleiding
description: Leer hoe u pijpleidingsvariabelen in Cloud Manager kunt gebruiken om specifieke configuratievariabelen voor uw bouwstijl te beheren.
exl-id: cfcef2e2-0590-457d-a0f9-6092a6d9e0e8
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 5d6d3374f2dd95728b2d3ed0cf6fab4092f73568
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 0%

---

# Het vormen Variabelen van de Pijpleiding {#configuring-pipeline-variables}

Uw bouwstijlproces kan van specifieke configuratievariabelen afhangen die om in de git bewaarplaats ongepast zouden zijn te plaatsen of u kunt hen tussen pijpleidinguitvoeringen moeten variëren gebruikend de zelfde tak. Cloud Manager staat u toe om deze gegevens als pijpleidingsvariabelen te beheren.

## Pipetvariabelen {#pipeline-variables}

Met Cloud Manager kunt u pijpleidingvariabelen op verschillende manieren configureren.

* [Via de gebruikersinterface van Cloud Manager](#ui)
* [Cloud Manager CLI gebruiken](#cli)
* [ Gebruikend Cloud Manager API ](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/Variables/operation/getPipelineVariables)

Variabelen kunnen worden opgeslagen als normale tekst of in rust worden versleuteld. In beide gevallen worden variabelen binnen de ontwikkelomgeving beschikbaar gemaakt als een omgevingsvariabele waarnaar vervolgens kan worden verwezen vanuit het `pom.xml` -bestand of andere constructiescripts.

### Naamgevingsconventies voor variabelen via pijpleidingen {#naming-conventions}

Namen van variabelen moeten voldoen aan de volgende conventies.

* Variabelen mogen alleen alfanumerieke tekens en het onderstrepingsteken (`_`) bevatten.
* De namen moeten allemaal hoofdletters zijn.
* Er is een grens van 200 variabelen per pijpleiding.
* Elke naam moet 100 tekens of minder zijn.
* Elke `string` variabelewaarde moet minder dan 2048 tekens zijn.
* Elke waarde van een variabele van het type `secretString` moet uit maximaal 500 tekens bestaan.

## Via de gebruikersinterface van Cloud Manager {#ui}

De variabelen van de pijpleiding kunnen via Cloud Manager UI worden gevormd en worden beheerd. U moet toestemmingen hebben om de pijpleiding uit te geven om, pijpleidingsvariabelen toe te voegen uit te geven en te schrappen.

Als een pijpleiding loopt, veranderlijk beheer wordt geblokkeerd.

### Pipetvariabelen toevoegen {#add-ui}

1. Wanneer [ het leiden van uw pijpleidingen, ](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md) tikt of klikt de elliptische knoop van de pijpleiding waarvoor u pijpleidingsvariabelen wilt tot stand brengen en **Mening/geef variabelen** van het contextmenu selecteren.

   ![ Mening/geef pijpleidingsvariabelen uit ](/help/implementing/cloud-manager/assets/pipeline-variables-view-edit.png)

1. Het **venster van de Configuratie van Variabelen** opent. Ga de veranderlijke details in de eerste rij van de lijst in en tik of klik **toevoegen**.

   * **de Naam van de Configuratie** is een uniek herkenningsteken voor uw variabele, die [ pijpleidingsvariabele het noemen overeenkomsten ](#naming-conventions) moet leiden.
   * **Waarde** is de waarde die de variabele houdt.
   * **Toegepaste Stap** is de stap in de pijpleiding waarop de variabele van toepassing is. Dit is verplicht.
      * **bouwt**
      * **Functionele het testen**
      * **UI het testen**
   * **Type** bepaalt als de variabele gewone tekst is of als geheim wordt gecodeerd.

   ![ voeg veranderlijke ](/help/implementing/cloud-manager/assets/pipeline-variables-add-variable.png) toe

1. De naam wordt aan de tabel toegevoegd. Voeg extra variabelen toe zoals vereist en dan ontken of klik **sparen** om de variabelen te bewaren u aan de pijpleiding toevoegde.

### Variabelen voor pijplijn bewerken {#edit-ui}

1. Wanneer [ het leiden van uw pijpleidingen, ](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md) tikt of klikt de elliptische knoop van de pijpleiding waarvoor u pijpleidingsvariabelen wilt tot stand brengen en **Mening/geef variabelen** van het contextmenu selecteren.

   ![ Mening/geef pijpleidingsvariabelen uit ](/help/implementing/cloud-manager/assets/pipeline-variables-view-edit.png)

1. Het **venster van de Configuratie van Variabelen** opent. Tik of klik de elliptische knoop van de variabele u wenst uit te geven en te selecteren **geeft** uit.

   ![ geef veranderlijke ](/help/implementing/cloud-manager/assets/pipeline-variables-edit.png) uit

1. Werk de waarde van de variabele zoals vereist bij en tik of klik **** (het controleteken aan het eind van de rij) van toepassing zijn om de verandering of **verwerpen** (de achterste pijl) om de verandering terug te keren.

   * Alleen de waarde van de variabele kan worden bewerkt.

   ![ Uitgevend een variabele ](/help/implementing/cloud-manager/assets/pipeline-variables-edit-save.png)

1. Tik of klik **sparen** om de veranderingen te bewaren u aan de variabelen aan de pijpleiding aanbracht.

Als u wenst om een variabele te schrappen, uitgezocht **Schrapping** in plaats van **geef** van het elliptische menu van de pijpleidingsvariabele in het **venster van de Configuratie van Variabelen** uit.

## Cloud Manager CLI gebruiken {#cli}

Dit CLI bevel plaatst een variabele.

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test
```

Deze opdracht geeft een overzicht van variabelen.

```shell
$ aio cloudmanager:list-pipeline-variables PIPELINEID
```

Bij gebruik in een Maven `pom.xml` -bestand is het doorgaans handig om deze variabelen toe te wijzen aan Maven-eigenschappen met een vergelijkbare syntaxis.

```xml
        <profile>
            <id>cmBuild</id>
            <activation>
                <property>
                    <name>env.CM_BUILD</name>
                </property>
            </activation>
            <properties>
                <my.custom.property>${env.MY_CUSTOM_VARIABLE}</my.custom.property> 
            </properties>
        </profile>
```
