---
title: Toegang tot opslagplaatsen
seo-title: Accessing Repositories
description: Op deze pagina wordt beschreven hoe u de Git-opslagplaats kunt openen en beheren.
seo-description: Follow this page to learn how to access and manage your Git repository.
exl-id: 0c0671a3-e400-46f3-ad86-166a6cfdd44b
source-git-commit: 3cdee254eebcf45762feff8fe081b006a803ef1b
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 5%

---

# Toegang tot opslagplaatsen {#accessing-repos}

U kunt de Git Repository openen en beheren met Self-Service Git Account Management vanuit de interface van Cloud Manager.

## Accountbeheer van Self-Service Repositories gebruiken {#self-service-repos}

Gebruik de **Access Repo Info** knoop beschikbaar bij de UI van de Manager van de Wolk, het meest opvallend op de pijpleidingskaart.

1. Navigeer naar **Pipelines** kaart van uw **Overzicht van het Programma** pagina.

1. U zult **Toegang Repo Info** optie bekijken om tot uw Bewaarplaats van de Bewaarplaats van de Git toegang te hebben en te beheren.

   ![](/help/implementing/cloud-manager/assets/repos/access-repo1.png)

   Bovendien, als u **niet-Productie** pijpleidingslusje selecteert, zult u de **optie van de Reactie van de Toegang ook daar bekijken Info**.

   ![](/help/implementing/cloud-manager/assets/repos/access-repo-nonprod.png)

   >[!NOTE]
   >De optie **Repo-info benaderen** is zichtbaar voor gebruikers in de rol Developer of Deployment Manager. Als u op deze knop klikt, wordt een dialoogvenster geopend waarin de gebruiker de URL naar zijn of haar gegevensopslagruimte voor de Intel Health Care Management Suite kan vinden, samen met de gebruikersnaam en het wachtwoord.

   ![](/help/implementing/cloud-manager/assets/repos/access-repo-create.png)

   De belangrijkste aspecten voor het beheer van uw Git in Cloud Manager zijn:

   * **URL**: De URL van de gegevensopslagruimte
   * **Gebruikersnaam**: De gebruikersnaam
   * **Wachtwoord**: De waarde die wordt weergegeven wanneer op de knop **Wachtwoord genereren** wordt geklikt.


      >[!NOTE]
      >Een gebruiker kan een kopie van de code uitchecken en wijzigingen aanbrengen in de lokale gegevensopslagruimte. Als de gebruiker klaar is, kan hij of zij de wijzigingen in de code doorvoeren naar de externe opslagplaats voor code in Cloud Manager.
