---
title: Bijwerken  [!DNL Workfront for Experience Manager enhanced connector]
description: Bijwerken  [!DNL Workfront for Experience Manager enhanced connector]
exl-id: 09276b4d-a7c8-4927-8c0a-40eda48e55a7
feature: Workfront Integrations and Apps
role: Admin
source-git-commit: 257930bc2633a0d31ad3bd28305b8159597befa5
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---

# [!DNL Workfront for Experience Manager enhanced connector] bijwerken {#update-enhanced-connector-for-workfront}

Met [!UICONTROL Experience Manager Assets as a Cloud Service] kunt u de versie van [!DNL Workfront for Experience Manager enhanced connector] bijwerken van een vorige versie naar de meest recente versie.

>[!TIP]
>
>Zoekt u naar [!DNL Workfront for Experience Manager enhanced connector] updatedocumentatie voor AEM 6.5? Klik [ hier ](https://experienceleague.adobe.com/docs/experience-manager-65/assets/integrations/workfront-connector-install.html?lang=en##update-enhanced-connector-for-workfront).


Ga als volgt te werk om [!DNL Workfront for Experience Manager enhanced connector] bij te werken naar de meest recente versie:

1. Download de recentste versie van de verbeterde schakelaar van [ de Distributie van de Software van de Adobe ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=/content/software-distribution/en/details.html/content/dam/aemcloud/public/workfront-tools.ui.apps.zip).

1. [ Toegang ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/accessing-repos.html?lang=en) en kloon uw bewaarplaats van AEM as a Cloud Service van Cloud Manager.

1. Open de gekloonde Experience Manager as a Cloud Service opslagplaats met behulp van een IDE van uw keuze.

1. Plaats het verbeterde gedownloade schakelaar zip dossier in Stap 1 bij de volgende weg:

   ```TXT
      /ui.apps/src/main/resources/<zip file>
   ```

   >[!NOTE]
   >
   >Als de map `resources` niet bestaat, maakt u de map.

1. Werk de verbeterde schakelaarversie in ouder bij `pom.xml`.

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

1. Werk de afhankelijkheid bij in `all module pom.xml` .

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
   >Voeg `<scope>` en `<systemPath>` toe aan de afhankelijkheden in stap 5 en 6.

1. Sluit `pom.xml` in. Voeg de [!DNL Workfront for Experience Manager enhanced connector] pakketten aan `embeddeds` sectie van `pom.xml` van al uw subproject toe. De updates in alle modules opnemen `pom.xml` .

   ```XML
   <!-- Workfront Tools -->
   <embedded>
      <groupId>digital.hoodoo</groupId>
      <artifactId>workfront-tools.ui.apps</artifactId>
      <type>zip</type>
      <target>/apps/<path-to-project-install-folder>/install</target>
   </embedded>
   ```

   Het doel van de ingesloten sectie wordt ingesteld op `/apps/<path-to-project-install-folder>/install` . Dit JCR-pad `/apps/<path-to-project-install-folder>` moet worden opgenomen in de filterregels in het `all/src/main/content/META-INF/vault/filter.xml` -bestand. De filterregels voor de gegevensopslagruimte worden gewoonlijk afgeleid van de naam van het programma. Gebruik de naam van de map als doel in de bestaande regels.

1. [ verwijdert de gebiedsdelen op de distributiepunten van de Hoodoo ](remove-external-dependencies.md), als om het even welk.

1. Breng de wijzigingen aan in de repository.

1. Stel de pijpleiding in werking om [ de veranderingen in Cloud Manager ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code.html) op te stellen.
