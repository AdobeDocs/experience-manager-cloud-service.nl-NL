---
title: Opslagplaatsen voor Cloud Manager
description: Opslagplaatsen voor Cloud Manager
source-git-commit: e5d52c92c9162a58cc1a8e4f5d1169d59ee13119
workflow-type: tm+mt
source-wordcount: '613'
ht-degree: 0%

---

# Opslagplaatsen voor Cloud Manager {#cloud-manager-repos}

Opslagplaatsen die zijn gemaakt en beschikbaar zijn in Cloud Manager, kunnen worden weergegeven en beheerd via de pagina Opslagplaatsen.

>[!NOTE]
>Er geldt een limiet van 300 gegevensbanken voor alle programma&#39;s in een bepaald bedrijf (of IMS Org).

## Opslagplaatsen toevoegen en beheren {#add-manage-repos}

Voer de onderstaande stappen uit om opslagruimten in Cloud Manager weer te geven en te beheren:

1. Van **Overzicht van het Programma** pagina, klik op **Bewaarplaatsen** lusje en navigeer aan **Bewaarplaatsen** pagina.

1. Klik op **Opslagplaats toevoegen** om de wizard te starten.

   >[!NOTE]
   >Een gebruiker in de Manager van de Plaatsing of de rol van BedrijfsEigenaar moet worden het programma geopend om een bewaarplaats kunnen toevoegen.

   ![](/help/implementing/cloud-manager/assets/repos/create-repo2.png)

1. Voer de gewenste naam en beschrijving in en klik op **Opslaan**.

   ![](/help/implementing/cloud-manager/assets/repos/repo-1.png)

1. Selecteer **Opslaan**. De nieuwe reactie wordt weergegeven in de tabel, zoals hieronder wordt weergegeven.

   >[!NOTE]
   >In Cloud Manager gemaakte opslagplaatsen kunnen u ook selecteren tijdens het toevoegen of bewerken van pijpleidingstappen. Verwijs naar [Vorm uw CI-CD Pijpleiding](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html?lang=en) om meer te leren. Er is één *primaire* bewaarplaats of een tak voor om het even welke bepaalde pijpleiding. Met [Ondersteuning voor Git-submodule](#git-submodule-support) kunnen er echter veel secundaire vertakkingen worden opgenomen tijdens het bouwen.

   ![](/help/implementing/cloud-manager/assets/repos/create-repo3.png)

1. U kunt de gegevensopslagruimte selecteren en op de menuopties van uiterst rechts in de tabel klikken naar **Repository URL kopiëren** of **View &amp; Update** of **Delete** uw gegevensopslagruimte, zoals in de onderstaande afbeelding wordt getoond.

   ![](/help/implementing/cloud-manager/assets/repos/create-repo3.png)

## Een opslagplaats verwijderen {#delete-repo}

Voer de onderstaande stappen uit om een opslagplaats in Cloud Manager te verwijderen:
>[!NOTE]
>Als u een opslagplaats verwijdert, gebeurt het volgende:
>1. Maak de verwijderde opslagplaats onbruikbaar voor nieuwe opslagplaatsen die in de toekomst kunnen worden gecreeerd. In dit geval wordt een foutbericht weergegeven zoals hieronder wordt getoond:
   >*De naam van de opslagplaats moet binnen de organisatie uniek zijn.*
>1. Maak de verwijderde opslagplaats niet beschikbaar in Cloud Manager en kan daarom niet worden gekoppeld aan een pijpleiding.


1. Van **Overzicht van het Programma** pagina, klik op **Bewaarplaatsen** lusje en navigeer aan **Bewaarplaatsen** pagina.

1. Selecteer de opslagplaats en klik op de menuopties helemaal rechts van de tabel. Klik op **Delete** om de gegevensopslagruimte te verwijderen, zoals in de onderstaande afbeelding wordt getoond.

   ![](/help/implementing/cloud-manager/assets/repos/delete-repo.png)


## Ondersteuning voor Git-submodule {#git-submodule-support}

Git-submodules kunnen worden gebruikt om de inhoud van meerdere vertakkingen tijdens het samenstellen samen te voegen tussen git-opslagruimten. Wanneer het de bouwstijlproces van de Manager van de Wolk uitvoert, nadat de bewaarplaats die voor de pijpleiding wordt gevormd wordt gekloond en de gevormde tak wordt gecontroleerd, als de tak een `.gitmodules` dossier in de wortelfolder bevat, wordt het bevel uitgevoerd.

```
$ git submodule update --init
```

Dit zal elke submodule in de aangewezen folder uitchecken. Deze techniek is een mogelijk alternatief voor https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/managing-code/working-with-multiple-source-git-repositories.html voor organisaties die vertrouwd zijn met het gebruik van git-submodules en geen extern samenvoegingsproces willen beheren.

Stel dat er drie opslagplaatsen zijn, die elk een enkele vertakking met de naam main bevatten. In de &quot;primaire&quot; opslagplaats, d.w.z. de opslagplaats die in de pijpleidingen is geconfigureerd, heeft de hoofdtak een bestand pom.xml waarin de projecten in de andere twee opslagplaatsen worden aangegeven:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
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

Vervolgens voegt u submodules toe voor de andere twee opslagruimten:

```
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectA/ project-a
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectB/ project-b
```

Dit resulteert in een `.gitmodules` dossier dat als dit kijkt:

```
[submodule "project-a"]
    path = project-a
    url = https://git.cloudmanager.adobe.com/ProgramName/projectA/
    branch = main
[submodule "project-b"]
    path = project-b
    url = https://git.cloudmanager.adobe.com/ProgramName/projectB/
    branch = main
```

Meer informatie over git-submodules vindt u in de [Git-referentiehandleiding](https://git-scm.com/book/en/v2/Git-Tools-Submodules).

Houd rekening met het volgende wanneer u git-submodules gebruikt:

* De URL van de it moet exact in de hierboven beschreven syntaxis staan. Sluit om beveiligingsredenen geen referenties in deze URL&#39;s in.
* Alleen submodules in de hoofdmap van de vertakking worden ondersteund.
* Git-submoduleverwijzingen worden opgeslagen naar specifieke it-opdrachten. Dientengevolge, wanneer veranderingen in de submodule bewaarplaats worden aangebracht, moet het gecommitteerde referenced worden bijgewerkt, bijvoorbeeld door `git submodule update --remote` te gebruiken.
* Tenzij anders nodig, wordt het ten zeerste aanbevolen &quot;oppervlakkige&quot; submodules te gebruiken. Om dit te doen, stel `git config -f .gitmodules submodule.<submodule path>.shallow true` voor elke submodule in werking.

