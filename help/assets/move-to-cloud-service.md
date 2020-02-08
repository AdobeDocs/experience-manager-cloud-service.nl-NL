---
title: Migreren naar Cloud Service vanuit Adobe Experience Manager 6.x
description: Migreren naar Cloud Service vanuit Adobe Experience Manager 6.x
contentOwner: AG
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# Naar Adobe Experience Manager-middelen gaan als cloudservice {#move-to-assets-cloud-service}

<!-- About the need to move from previous AEM deployment to a cloud service deployment. And how does Adobe help do it OOTB?
-->

## Het migratiehulpprogramma {#migration-tool}

<!-- 
Link back to information about the tool in the Experience Manager as a Cloud Service docs if the tool works the same for Sites and Assets. Document the Assets-specific information here.

* What is the migration tool called? Is there a branding term for it?
* How much do we want to elaborate about the Pattern Detector rules? Is there a branding term for it?
* Before migrating using the tool, is any prepping required?
* See CQ-4271901

-->

Met het migratiehulpprogramma kunt u het volgende bereiken:

* Zet de bestaande workflowmodellen om in verwerkingsprofielen die werken met de Assets Compute Service.
* Verwijder niet-ondersteunde stappen uit de workflowmodellen.
* Workflowdraagraketten uitschakelen.
* Voeg de configuraties na bevestiging/validatie van de gebruiker samen in de bestaande broncode.

Met het migratiehulpprogramma maakt u verwerkingsprofielen in een Maven-module die gebruikers op de volgende twee manieren kunnen gebruiken:

* Voeg samen tot een van hun bestaande projecten.
* Voeg de module toe als nieuwe submodule.

Het migratiehulpmiddel verstrekt een rapport van de veranderingen het maakte en informatie over de veranderingen.

<!--  

What is the output of the tool, besides migrated content.

Give details about reports and logs of the tool. 

* How to access the report, including required permissions.
* How to read/interpret the report.
* Location of logs. How to read the logs.
* What common errors to look for. Troubleshooting for these errors.

-->

## Inhoud migreren naar een nieuwe implementatie {#content-migration-across-deployments}
