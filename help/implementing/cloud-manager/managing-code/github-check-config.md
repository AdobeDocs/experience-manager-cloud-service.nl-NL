---
title: GitHub Check Configuration for Private Repositories
description: Leer hoe u de pijpleidingen kunt beheren die automatisch worden gemaakt om elke pull-aanvraag naar een privéopslagplaats te valideren.
exl-id: 3ae3c19e-2621-4073-ae17-32663ccf9e7b
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 0a08d5fc033f4f4f57b824492766e5b42a801b6e
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 0%

---

# GitHub-controleconfiguratie voor privéopslagruimten {#github-check-config}

Leer hoe u de pijpleidingen kunt beheren die automatisch worden gemaakt om elke pull-aanvraag naar een privéopslagplaats te valideren.

## Configuratie van GitHub-controles {#configuration}

Wanneer het gebruiken van [ privé bewaarplaatsen ](private-repositories.md#using), wordt de a [ volledige pijpleiding van de kwaliteit van de stapelcode ](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) automatisch gecreeerd. Deze pijpleiding is begonnen bij elke update van het trekkingsverzoek.

U kunt deze controles besturen door een `.cloudmanager/pr_pipelines.yml` configuratiebestand te maken in de standaardvertakking van de privéopslagruimte.

```yaml
github:
  shouldDeletePreviousComment: false
  shouldSkipCheckAnnotations: false
pipelines:
  - type: CI_CD
    template:
      programId: 1234
      pipelineId: 456
    namePrefix: Full Stack Code Quality Pipeline for PR
    importantMetricsFailureBehavior: CONTINUE
```

| Parameter | Mogelijke waarden | Standaard | Beschrijving |
| --- | --- | --- | --- |
| `shouldDeletePreviousComment` | `true` of `false` | `false` | Of om slechts de laatste commentaar met de codeaftastenresultaten op dit GitHub trekkingsverzoek te houden of allen te houden. Als u deze instelt op `false` (standaardwaarde), worden eerdere opmerkingen niet verwijderd. |
| `shouldSkipCheckAnnotations` | `true` of `false` | `false` | Of om extra annotaties te hebben aanwezig op de controle van het trekkingsverzoek GitHub of niet. Als u deze instelt op `false` (standaardwaarde), worden controleannotaties niet overgeslagen en worden deze opgenomen in de feedback. |
| `type` | `CI_CD` | nvt | Bepaalt het gedrag van (Ononderbroken Integratie/Ononderbroken Plaatsing) pijpleidingsconfiguraties CI/CD. |
| `template.programId` | Geheel | Er worden geen pijpleidingvariabelen opnieuw gebruikt | U kunt het gebruiken om de [ pijpleidingsvariabelen ](/help/implementing/cloud-manager/configuring-pipelines/pipeline-variables.md) te hergebruiken die op een bestaande pijpleiding automatisch door elk trektrekkingsverzoek wordt gecreeerd. |
| `template.pipelineId` | Geheel | Er worden geen pijpleidingvariabelen opnieuw gebruikt | U kunt het gebruiken om de [ pijpleidingsvariabelen ](/help/implementing/cloud-manager/configuring-pipelines/pipeline-variables.md) te hergebruiken die op een bestaande pijpleiding automatisch door elk trektrekkingsverzoek wordt gecreeerd. |
| `namePrefix` | String | `Full Stack Code Quality Pipeline for PR` | Gebruikt om de prefix voor de naam van de pijpleiding te plaatsen die automatisch wordt gecreeerd. |
| `importantMetricsFailureBehavior` | `CONTINUE` of `FAIL` of `PAUSE` | `CONTINUE` | Plaatst het belangrijke metrische gedrag van de pijpleiding <br>`CONTINUE` = als belangrijke metrische ontbreekt, de pijpleiding zich automatisch <br>`FAIL` = de pijpleiding eindigt met een FAILED status als belangrijke metrische ontbreekt <br>`PAUSE` = de stap van het codescannen een WAITING status ontvangt wanneer belangrijke metrisch ontbreekt en moet manueel worden hervat |




