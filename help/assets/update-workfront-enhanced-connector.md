---
title: Bijwerken [!DNL Workfront for Experience Manager enhanced connector]
description: Bijwerken [!DNL Workfront for Experience Manager enhanced connector]
exl-id: 09276b4d-a7c8-4927-8c0a-40eda48e55a7
feature: Workfront Integrations and Apps
role: Admin
source-git-commit: 257930bc2633a0d31ad3bd28305b8159597befa5
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---

# Bijwerken [!DNL Workfront for Experience Manager enhanced connector] {#update-enhanced-connector-for-workfront}

[!UICONTROL Experience Manager Assets as a Cloud Service] biedt u de mogelijkheid de [!DNL Workfront for Experience Manager enhanced connector] van een vorige versie naar de meest recente versie.

>[!TIP]
>
>Zoek je naar [!DNL Workfront for Experience Manager enhanced connector] documentatie voor AEM 6.5 bijwerken? Klikken [hier](https://experienceleague.adobe.com/docs/experience-manager-65/assets/integrations/workfront-connector-install.html?lang=en##update-enhanced-connector-for-workfront).


Als u het dialoogvenster [!DNL Workfront for Experience Manager enhanced connector] naar de meest recente versie:

1. Download de nieuwste versie van de verbeterde connector van [Softwaredistributie Adoben](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=/content/software-distribution/en/details.html/content/dam/aemcloud/public/workfront-tools.ui.apps.zip).

1. [Toegang](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/accessing-repos.html?lang=en) en kloon uw AEM as a Cloud Service opslagplaats uit Cloud Manager.

1. Open de gekloonde Experience Manager as a Cloud Service opslagplaats met behulp van een IDE van uw keuze.

1. Plaats het verbeterde gedownloade schakelaar zip dossier in Stap 1 bij de volgende weg:

   ```TXT
      /ui.apps/src/main/resources/<zip file>
   ```

   >[!NOTE]
   >
   >Als de `resources` de map bestaat niet. Maak de map.

1. De verbeterde schakelaarversie in ouder bijwerken `pom.xml`.

   ```XML
      <dependency>
         <groupId>digital.hoodoo</groupId>
         <artifactId>workfront-tools.ui.apps</artifactId>
         <type>zip</type>
         <version> updated enhanced connector version number</version>
         <scope>system</scope>
         <systemPath>${project.basedir}/ui.apps/src/main/resources/workfront-tools.ui.apps.zip</systemPath>
      </dependency>
   ```

1. Afhankelijkheid bijwerken in `all module pom.xml`.

   ```XML
      <dependency>
         <groupId>digital.hoodoo</groupId>
         <artifactId>workfront-tools.ui.apps</artifactId>
         <type>zip</type>
         <scope>system</scope>
         <systemPath>${project.basedir}/../ui.apps/src/main/resources/workfront-tools.ui.apps.zip</systemPath>
      </dependency>
   ```

   >[!NOTE]
   >
   >Zorg ervoor dat u `<scope>` en `<systemPath>` de afhankelijkheden in stap 5 en 6.

1. Bijwerken `pom.xml` worden ingesloten. Voeg de [!DNL Workfront for Experience Manager enhanced connector] pakketten naar `embeddeds` van de `pom.xml` van al uw subproject. De updates in alle modules opnemen `pom.xml`.

   ```XML
   <!-- Workfront Tools -->
   <embedded>
      <groupId>digital.hoodoo</groupId>
      <artifactId>workfront-tools.ui.apps</artifactId>
      <type>zip</type>
      <target>/apps/<path-to-project-install-folder>/install</target>
   </embedded>
   ```

   Het doel van de ingesloten sectie is ingesteld op `/apps/<path-to-project-install-folder>/install`. Dit JCR-pad `/apps/<path-to-project-install-folder>` moet worden opgenomen in de filterregels in de `all/src/main/content/META-INF/vault/filter.xml` bestand. De filterregels voor de gegevensopslagruimte worden gewoonlijk afgeleid van de naam van het programma. Gebruik de naam van de map als doel in de bestaande regels.

1. [De afhankelijkheden van de distributiepunten van Photoshop verwijderen](remove-external-dependencies.md), indien van toepassing.

1. Breng de wijzigingen aan in de repository.

1. De pijplijn in werking stellen aan [Wijzigingen in Cloud Manager implementeren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code.html).
