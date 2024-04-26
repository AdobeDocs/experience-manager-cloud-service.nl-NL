---
title: Opslagplaatsen voor Cloud Manager
description: Leer hoe u uw git-opslagruimten maakt, weergeeft en verwijdert in Cloud Manager.
exl-id: 6e1cf636-78f5-4270-9a21-38b4d5e5a0b0
source-git-commit: 4bf1d961705ce07c5ae5d33a546a276192f10178
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 0%

---


# Opslagplaatsen voor Cloud Manager {#cloud-manager-repos}

Leer hoe u uw git-opslagruimten maakt, weergeeft en verwijdert in Cloud Manager.

>[!NOTE]
>
>Er geldt een limiet van 300 gegevensbanken voor alle programma&#39;s in een bepaalde onderneming of IMS-organisatie.

## Opslagplaatsen toevoegen en beheren {#add-manage-repos}

Volg deze stappen om opslagruimten in Cloud Manager weer te geven en te beheren.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie en het juiste programma.

1. Van de **Programmaoverzicht** pagina, selecteert u de **Opslagplaatsen** tab naar **Opslagplaatsen** pagina.

1. Klikken **Opslagplaats toevoegen**.

   ![Opslagplaats toevoegen, knop](/help/implementing/cloud-manager/assets/repos/create-repo2.png)

1. Voer de gewenste naam en beschrijving in en klik op **Opslaan**.

   ![Dialoogvenster Opslagplaats toevoegen](/help/implementing/cloud-manager/assets/repos/repo-1.png)

Wanneer de wizard wordt gesloten, wordt uw nieuwe opslagplaats weergegeven in de tabel.

U kunt de gegevensopslagruimte in de tabel selecteren en op de knop voor weglatingsteken klikken en **Repository-URL kopiëren**, **Weergeven en bijwerken**, of **Verwijderen**.

![Opties voor opslagplaats](/help/implementing/cloud-manager/assets/repos/create-repo3.png)

In Cloud Manager gemaakte opslagruimten kunnen ook worden geselecteerd wanneer u pijpleidingen toevoegt of bewerkt. Zie [CI-CD-pijpleidingen](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) voor meer informatie.

Er is één enkele primaire bewaarplaats of een tak voor om het even welke bepaalde pijpleiding. Met [ondersteuning voor git-submodules](#git-submodule-support)Veel secundaire vertakkingen kunnen tijdens de bouwperiode worden opgenomen.

>[!NOTE]
>
>Een gebruiker moet de rol hebben **Implementatiebeheer** of **Zakelijke eigenaar** om een gegevensopslagruimte te kunnen toevoegen.

## Een opslagplaats verwijderen {#delete-repo}

Als u een opslagplaats verwijdert, gebeurt het volgende:

* Maak de verwijderde opslagplaats onbruikbaar voor nieuwe opslagplaatsen die in de toekomst kunnen worden gecreeerd.
   * Het foutbericht `Repository name should be unique within organization.` in dergelijke gevallen wordt aangetoond.
* Maak de verwijderde opslagplaats niet beschikbaar in Cloud Manager en niet beschikbaar voor het koppelen naar een pijpleiding.

Ga als volgt te werk om een opslagplaats in Cloud Manager te verwijderen.

1. Van de **Programmaoverzicht** pagina, klikt u op de **Opslagplaatsen** en navigeer naar de **Opslagplaatsen** pagina.

1. Selecteer de opslagplaats en klik op de knop voor weglatingsteken en selecteer **Verwijderen** om de gegevensopslagruimte te verwijderen.

## Ondersteuning voor Git-submodule {#git-submodule-support}

Git-submodules kunnen worden gebruikt om de inhoud van meerdere vertakkingen tijdens het samenstellen samen te voegen tussen git-opslagruimten.

Wanneer het de bouwstijlproces van de Manager van de Wolk uitvoert, nadat de bewaarplaats die voor de pijpleiding wordt gevormd wordt gekloond en de gevormde tak wordt gecontroleerd, als de tak een bevat `.gitmodules` in de hoofdmap, wordt de opdracht uitgevoerd.

Het volgende bevel zal elke submodule in de aangewezen folder uitchecken.

```
$ git submodule update --init
```

Deze techniek is een mogelijk alternatief voor de in het document beschreven oplossing [Werken met Meerdere bronopslaglocaties voor Git](/help/implementing/cloud-manager/managing-code/working-with-multiple-source-git-repositories.md) voor organisaties die comfortabel zijn met het gebruik van git-submodules en geen extern samenvoegingsproces willen beheren.

Stel bijvoorbeeld dat er drie opslagruimten zijn die elk één vertakking met de naam `main`. In de primaire opslagplaats, d.w.z. die gevormd in de pijpleidingen, `main` vertakking bevat een `pom.xml` dossier waarin de projecten in de andere twee gegevensbanken worden verklaard.

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

Vervolgens voegt u submodules toe voor de andere twee opslagruimten.

```shell
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectA/ project-a
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectB/ project-b
```

Dit leidt tot een `.gitmodules` bestand, vergelijkbaar met het volgende.

```text
[submodule "project-a"]
    path = project-a
    url = https://git.cloudmanager.adobe.com/ProgramName/projectA/
    branch = main
[submodule "project-b"]
    path = project-b
    url = https://git.cloudmanager.adobe.com/ProgramName/projectB/
    branch = main
```

Meer informatie over git-submodules vindt u in de [Git Reference Manual.](https://git-scm.com/book/en/v2/Git-Tools-Submodules)

### Beperkingen en Recommendations {#limitations-recommendations}

Houd rekening met de volgende beperkingen wanneer u git-submodules gebruikt.

* De URL van de it moet exact de syntaxis hebben die in de vorige sectie wordt beschreven.
* Alleen submodules in de hoofdmap van de vertakking worden ondersteund.
* Omwille van de beveiliging mag u referenties niet insluiten in URL&#39;s met git.
* Tenzij anders nodig, wordt het ten zeerste aanbevolen oppervlakkige submodules te gebruiken.
   * Voer hiervoor `git config -f .gitmodules submodule.<submodule path>.shallow true` voor elke submodule.
* Verwijzingen naar de Git-submodule worden opgeslagen naar specifieke it-opdrachten. Dientengevolge, wanneer veranderingen in de submodule bewaarplaats worden aangebracht, begaat referenced moet worden bijgewerkt.
   * Bijvoorbeeld door `git submodule update --remote`
