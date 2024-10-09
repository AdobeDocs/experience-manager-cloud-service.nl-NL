---
title: GitHub Check Configuration for Private Repositories
description: Leer hoe u de pijpleidingen kunt beheren die automatisch worden gemaakt om elke pull-aanvraag naar een privéopslagplaats te valideren.
exl-id: 3ae3c19e-2621-4073-ae17-32663ccf9e7b
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 6eabf593a7566129d32d9a5888cc480117bef51f
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# GitHub-controleconfiguratie voor privéopslagruimten {#github-check-config}

Leer hoe u de pijpleidingen kunt beheren die automatisch worden gemaakt om elke pull-aanvraag naar een privéopslagplaats te valideren.

## Configuratie van GitHub-controles {#configuration}

Wanneer het gebruiken van [ privé bewaarplaatsen ](private-repositories.md#using), wordt de a [ volledige pijpleiding van de kwaliteit van de stapelcode ](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) automatisch gecreeerd. Deze pijpleiding is begonnen bij elke update van het trekkingsverzoek.

U kunt deze controles besturen door een `.cloudmanager/pr_pipelines.yml` -bestand te maken in de standaardvertakking van de privéopslagruimte.

```yaml
github:
  shouldDeletePreviousComment: false
pipelines:
  - type: CI_CD
    template:
      programId: 1234
      pipelineId: 456
    namePrefix: Full Stack Code Quality Pipeline for PR 
    importantMetricsFailureBehavior: CONTINUE
```

| Parameter | Mogelijke waarden | Standaard | Beschrijving |
|---|---|---|---|
| `shouldDeletePreviousComment` | `true` of `false` | `false` | Of om slechts de laatste commentaar met de codeaftastenresultaten op dit GitHub trekkingsverzoek te houden of alles te houden |
| `type` | `CI_CD` | nvt | Bepaalt gedrag van een pijpleiding CI/CD |
| `template.programID` | Geheel | Er worden geen pijpleidingvariabelen opnieuw gebruikt | U kunt het gebruiken om de [ pijpleidingsvariabelen ](/help/implementing/cloud-manager/configuring-pipelines/pipeline-variables.md) te hergebruiken die op een bestaande pijpleiding automatisch door elk trektrekkingsverzoek wordt gecreeerd. |
| `template.pipelineID` | Geheel | Er worden geen pijpleidingvariabelen opnieuw gebruikt | U kunt het gebruiken om de [ pijpleidingsvariabelen ](/help/implementing/cloud-manager/configuring-pipelines/pipeline-variables.md) te hergebruiken die op een bestaande pijpleiding automatisch door elk trektrekkingsverzoek wordt gecreeerd. |
| `namePrefix` | String | `Full Stack Code Quality Pipeline for PR` | Gebruikt om de naam van de pijpleiding te plaatsen die automatisch wordt gecreeerd |
| `importantMetricsFailureBehavior` | `CONTINUE` of `FAIL` of `PAUSE` | `CONTINUE` | Plaatst het belangrijke metrische gedrag van de pijpleiding <br>`CONTINUE` = als belangrijke metrische ontbreekt, de pijpleiding zich automatisch <br>`FAIL` = de pijpleiding eindigt met een FAILED status als belangrijke metrische ontbreekt <br>`PAUSE` = de stap van het codescannen een WAITING status ontvangt wanneer belangrijke metrisch ontbreekt en moet manueel worden hervat |
