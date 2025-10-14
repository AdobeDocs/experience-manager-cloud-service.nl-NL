---
title: Externe afhankelijkheden voor bestaande installaties verwijderen
description: Externe afhankelijkheden voor bestaande installaties verwijderen
feature: Workfront Integrations and Apps
exl-id: 5b28ce97-2719-47b8-a386-77d4aaddbe81
role: Admin
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 0%

---

# Externe afhankelijkheden voor bestaande installaties verwijderen {#remove-external-depedencies}

Adobe raadt u aan configuratiestappen uit te voeren voor bestaande verbeterde verbindingsinstallaties voor Workfront om de afhankelijkheden op de distributiepunten van de Hoodoo te verwijderen.

>[!NOTE]
>
>Voer de configuratiestappen slechts uit als u de verbeterde schakelaar voor Workfront vóór Maart 2022 hebt geïnstalleerd. Er zijn vanaf maart 2022 geen afhankelijkheden op de distributiepunten van Hoodoo voor nieuwe verbeterde connectorinstallaties voor Workfront.

De externe afhankelijkheden verwijderen:

1. Verwijder de volgende configuratie van de fotoopslagplaats uit het bovenliggende element `pom.xml` :

   ```XML
     <repository>
        <id>hoodoo-maven</id>
        <name>Hoodoo Repository</name>
        <url>https://gitlab.com/api/v4/projects/12715200/packages/maven</url>
     </repository>
   ```

1. Verwijder de volgende serverconfiguratie uit het `settings.xml` -bestand, beschikbaar op `./cloudmanager/maven/settings.xml` :

   ```XML
         <server>
            <id>hoodoo-maven</id>
            <configuration>
               <httpHeaders>
                     <property>
                        <name>Deploy-Token</name>
                        <value>xxxxxxxxxxxxxxxx</value>
                     </property>
               </httpHeaders>
            </configuration>
         </server>
   ```

1. Voer de [&#x200B; nieuwe installatiestappen &#x200B;](workfront-connector-install.md) uit.
