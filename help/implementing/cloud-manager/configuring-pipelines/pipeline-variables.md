---
title: Pipetvariabelen in Cloud Manager
description: Leer hoe u pijpleidingsvariabelen in Cloud Manager kunt gebruiken om specifieke configuratievariabelen voor uw bouwstijl te beheren.
exl-id: cfcef2e2-0590-457d-a0f9-6092a6d9e0e8
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 2573eb5f8a8ff21a8e30b94287b554885cd1cd89
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 0%

---

# Pipetvariabelen in Cloud Manager {#configuring-pipeline-variables}

Uw bouwstijlproces zou op specifieke configuratievariabelen kunnen baseren die niet in de bewaarplaats van het Git zouden moeten worden opgeslagen. Of, kunt u hen tussen pijpleidingslooppas op de zelfde tak moeten aanpassen. Met Cloud Manager kunt u deze instellingen als pijpleidingvariabelen beheren.

## Info over pijpleidingsvariabelen {#pipeline-variables}

Met Cloud Manager kunt u pijpleidingvariabelen op verschillende manieren configureren.

* [De gebruikersinterface van Cloud Manager gebruiken](#ui)
* [Cloud Manager CLI gebruiken](#cli)
* [ Gebruikend Cloud Manager API ](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/Variables/operation/getPipelineVariables)

Variabelen kunnen worden opgeslagen als normale tekst of in rust worden versleuteld. In beide gevallen worden variabelen binnen de ontwikkelomgeving beschikbaar gemaakt als een omgevingsvariabele, waarnaar vervolgens kan worden verwezen vanuit het `pom.xml` -bestand of andere constructiescripts.

## Voeg een pijpleidingsvariabele door Cloud Manager toe {#ui}

De variabelen van de pijpleiding kunnen door het gebruikersinterface van Cloud Manager worden gevormd en worden beheerd. Zij helpen pijpleidingsbeheer stroomlijnen, vooral wanneer de variërende configuraties over verschillende stappen worden vereist.

U moet toestemmingen hebben om de pijpleiding uit te geven om, pijpleidingsvariabelen toe te voegen uit te geven en te schrappen.

Als een pijpleiding loopt, veranderlijk beheer wordt geblokkeerd.

**om een pijpleidingsvariabele door Cloud Manager toe te voegen:**

1. Wanneer [ het leiden van uw pijpleidingen ](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md), klik ![ Ellipse - Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) van de pijpleiding waarvoor u pijpleidingsvariabelen wilt tot stand brengen.

1. Van het drop-down menu, klik **Mening/geef variabelen** uit.

   ![ Mening/geef pijpleidingsvariabelen ](/help/implementing/cloud-manager/assets/pipeline-variables-view-edit.png) uit

1. In het **de dialoogvakje van de Configuratie van Variabelen**, ga de details in de eerste rij van de lijst in.

   | Veld | Beschrijving |
   | --- | --- |
   | Naam | A unique name of the configuration variable. Het identificeert de specifieke variabele die in de pijpleiding wordt gebruikt. De toepassing moet de volgende naamconventies in acht nemen:<ul><li>Variabelen mogen alleen alfanumerieke tekens en het onderstrepingsteken (`_`) bevatten.</li><li>De namen moeten allemaal hoofdletters zijn.</li><li>Er is een grens van 200 variabelen per pijpleiding.</li><li>Elke naam moet 100 tekens of minder zijn.</li><li>Elke `string` variabelewaarde moet minder dan 2048 tekens zijn.</li><li>Elke waarde van een variabele van het type `secretString` moet uit maximaal 500 tekens bestaan.</li></ul> |
   | Waarde | De waarde die de variabele aanhoudt. |
   | Toegepaste stap | Vereist. De stap in de pijpleiding waarop de variabele van toepassing is:<ul><li>**bouwt** - de variabele wordt toegepast tijdens het bouwstijlproces.</li><li>**Functioneel het testen** - de variabele wordt gebruikt tijdens de functionele het testen stap.</li><li>**UI het testen** - de variabele wordt gebruikt tijdens UI het testen fase.</li></ul> |
   | Type | Selecteer deze optie als de variabele onbewerkte tekst is of als geheim is gecodeerd. |

   ![ voeg veranderlijke ](/help/implementing/cloud-manager/assets/pipeline-variables-add-variable.png) toe

1. Klik **toevoegen**.

   Voeg zo nodig extra variabelen toe.

1. Klik **sparen**.

## Een pijpleidingsvariabele bewerken {#edit-ui}

1. Wanneer [ het leiden van uw pijpleidingen ](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md), klik ![ Ellipse - Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) van de pijpleiding waarvoor u pijpleidingsvariabelen wilt uitgeven.

1. In het drop-down menu, klik **Mening/geef variabelen** uit.

   ![ Mening/geef pijpleidingsvariabelen ](/help/implementing/cloud-manager/assets/pipeline-variables-view-edit.png) uit

1. In het **de dialoogvakje van de Configuratie van Variabelen 0} {, klik ![ Ellipse - Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) van de variabele die u wilt veranderen.**

1. In het drop-down menu, geeft de klik **** uit.

   ![ geef veranderlijke ](/help/implementing/cloud-manager/assets/pipeline-variables-edit.png) uit

1. Werk de waarde van de variabele bij zoals vereist.

   Alleen de waarde van de variabele kan worden gewijzigd.

1. Voer een van de volgende handelingen uit:

   * Klik ![ toepassen - het pictogram van het Vinkje ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Checkmark_18_N.svg) om de verandering toe te passen.
   * Klik ![ ongedaan maken pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Undo_18_N.svg) om de verandering terug te keren.

1. Klik **sparen**.

## Een pijpleidingsvariabele verwijderen {#delete-ui}

1. Wanneer [ het leiden van uw pijpleidingen ](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md), klik ![ Ellipse - Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) van de pijpleiding waarvoor u pijpleidingsvariabelen wilt schrappen.

1. In het drop-down menu, klik **Mening/geef variabelen** uit.

   ![ Mening/geef pijpleidingsvariabelen ](/help/implementing/cloud-manager/assets/pipeline-variables-view-edit.png) uit

1. In het **de dialoogvakje van de Configuratie van Variabelen 0} {, klik ![ Ellipse - Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) van de variabele u wilt verwijderen.**

1. In het drop-down menu, klik **Schrapping**.


## De pijpleidingsvariabelen van de reeks gebruikend Cloud Manager CLI {#cli}

Dit bevel in CLI (de Interface van de Lijn van het Bevel) plaatst een variabele.

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test
```

Deze opdracht geeft een overzicht van variabelen.

```shell
$ aio cloudmanager:list-pipeline-variables PIPELINEID
```

Bij gebruik in een Maven `pom.xml` -bestand is het vaak handig om deze variabelen te koppelen aan Maven-eigenschappen met een syntaxis die lijkt op het volgende voorbeeld:

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
