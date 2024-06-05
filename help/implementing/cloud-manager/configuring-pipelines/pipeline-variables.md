---
title: Het vormen Variabelen van de Pijpleiding
description: Leer hoe u pijpleidingsvariabelen in de Manager van de Wolk kunt gebruiken om specifieke configuratievariabelen voor uw bouwstijl te beheren.
exl-id: cfcef2e2-0590-457d-a0f9-6092a6d9e0e8
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 0%

---

# Het vormen Variabelen van de Pijpleiding {#configuring-pipeline-variables}

Uw bouwstijlproces kan van specifieke configuratievariabelen afhangen die om in de git bewaarplaats ongepast zouden zijn te plaatsen of u kunt hen tussen pijpleidinguitvoeringen moeten variëren gebruikend de zelfde tak. Met Cloud Manager kunt u deze gegevens beheren als pijpleidingvariabelen.

## Pipetvariabelen {#pipeline-variables}

Met Cloud Manager kunt u pijpleidingvariabelen op verschillende manieren configureren.

* [Via de interface van Cloud Manager](#ui)
* [Cloud Manager CLI gebruiken](#cli)
* [De API voor Cloud Manager gebruiken](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/Variables/operation/getPipelineVariables)

Variabelen kunnen worden opgeslagen als normale tekst of in rust worden versleuteld. In beide gevallen worden variabelen binnen de ontwikkelomgeving beschikbaar gemaakt als een omgevingsvariabele die vervolgens van binnen de `pom.xml` of andere build-scripts.

### Naamgevingsconventies voor variabelen via pijpleidingen {#naming-conventions}

Namen van variabelen moeten voldoen aan de volgende conventies.

* Variabelen mogen alleen alfanumerieke tekens en het onderstrepingsteken (`_`).
* De namen moeten allemaal hoofdletters zijn.
* Er is een grens van 200 variabelen per pijpleiding.
* Elke naam moet 100 tekens of minder zijn.
* Elk `string` waarde van variabele moet minder dan 2048 tekens zijn.
* Elk `secretString` waarde van tekstvariabele moet maximaal 500 tekens zijn.

## Via de interface van Cloud Manager {#ui}

De variabelen van de pijpleiding kunnen via de UI van de Manager van de Wolk worden gevormd en worden beheerd. U moet toestemmingen hebben om de pijpleiding uit te geven om, pijpleidingsvariabelen toe te voegen uit te geven en te schrappen.

Als een pijpleiding loopt, veranderlijk beheer wordt geblokkeerd.

### Pipetvariabelen toevoegen {#add-ui}

1. Wanneer [het beheer van uw pijpleidingen,](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md) tik of klik de elliptische knoop van de pijpleiding waarvoor u pijpleidingsvariabelen wilt tot stand brengen en selecteren **Variabelen weergeven/bewerken** in het contextmenu.

   ![Pijplijnvariabelen weergeven/bewerken](/help/implementing/cloud-manager/assets/pipeline-variables-view-edit.png)

1. De **Configuratie variabelen** wordt geopend. Voer de variabeledetails in de eerste rij van de tabel in en tik of klik op **Toevoegen**.

   * **Configuratienaam** is een unieke id voor de variabele die moet worden afgespeeld [de veranderlijke noemende overeenkomsten van de pijpleiding.](#naming-conventions)
   * **Waarde** is de waarde die de variabele aanhoudt.
   * **Toegepaste stap** is de stap in de pijpleiding waarop de variabele van toepassing is. Dit is verplicht.
      * **Opbouwen**
      * **Functionele tests**
      * **UI-tests**
   * **Type** definieert of de variabele onbewerkte tekst is of als geheim is gecodeerd.

   ![Variabele toevoegen](/help/implementing/cloud-manager/assets/pipeline-variables-add-variable.png)

1. De naam wordt aan de tabel toegevoegd. Voeg desgewenst extra variabelen toe en tik of klik op **Opslaan** om de variabelen te bewaren u aan de pijpleiding toevoegde.

### Variabelen voor pijplijn bewerken {#edit-ui}

1. Wanneer [het beheer van uw pijpleidingen,](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md) tik of klik de elliptische knoop van de pijpleiding waarvoor u pijpleidingsvariabelen wilt tot stand brengen en selecteren **Variabelen weergeven/bewerken** in het contextmenu.

   ![Pijplijnvariabelen weergeven/bewerken](/help/implementing/cloud-manager/assets/pipeline-variables-view-edit.png)

1. De **Configuratie variabelen** wordt geopend. Tik of klik op de knop Ovaal van de variabele die u wilt bewerken en selecteer **Bewerken**.

   ![Variabele bewerken](/help/implementing/cloud-manager/assets/pipeline-variables-edit.png)

1. Werk de waarde van de variabele bij zoals vereist en tik of klik **Toepassen** (het vinkje aan het einde van de rij) om de wijziging toe te passen of **Negeren** (de achterste pijl) om de wijziging terug te draaien.

   * Alleen de waarde van de variabele kan worden bewerkt.

   ![Een variabele bewerken](/help/implementing/cloud-manager/assets/pipeline-variables-edit-save.png)

1. Tik of klik op **Opslaan** om de veranderingen te bewaren u aan de variabelen aan de pijpleiding aanbracht.

Als u een variabele wilt verwijderen, selecteert u **Verwijderen** in plaats van **Bewerken** in het ovaalmenu van de pijpleidingvariabele in het dialoogvenster **Configuratie variabelen** venster.

## Cloud Manager CLI gebruiken {#cli}

Dit CLI bevel plaatst een variabele.

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test
```

Deze opdracht geeft een overzicht van variabelen.

```shell
$ aio cloudmanager:list-pipeline-variables PIPELINEID
```

Indien gebruikt in een Maven `pom.xml` , is het doorgaans handig om deze variabelen toe te wijzen aan Maven-eigenschappen met een vergelijkbare syntaxis.

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
