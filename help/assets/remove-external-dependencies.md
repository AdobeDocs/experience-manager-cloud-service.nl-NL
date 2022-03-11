---
title: Externe afhankelijkheden voor bestaande installaties verwijderen
description: Installeren [!DNL Workfront for Experience Manager enhanced connector]
feature: Integrations
exl-id: 5b28ce97-2719-47b8-a386-77d4aaddbe81
source-git-commit: d1f7b3ee9394751795273820c17e6feba84f7bf6
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---

# Externe afhankelijkheden voor bestaande installaties verwijderen {#remove-external-depedencies}

Adobe raadt u aan configuratiestappen uit te voeren voor bestaande verbeterde schakelaarinstallaties voor Workfront om de gebiedsdelen op de distributiepunten van de Hoodoo te verwijderen.

>[!NOTE]
>
>Voer de configuratiestappen slechts uit als u de verbeterde schakelaar voor Workfront vóór Maart 2022 hebt geïnstalleerd. Er zijn vanaf maart 2022 geen afhankelijkheden op de distributiepunten van Hoodoo voor nieuwe verbeterde connectorinstallaties voor Workfront.

De externe afhankelijkheden verwijderen:

1. De volgende configuratie van de fotoopslagplaats verwijderen uit het bovenliggende image `pom.xml`:

   ```XML
     <repository>
        <id>hoodoo-maven</id>
        <name>Hoodoo Repository</name>
        <url>https://gitlab.com/api/v4/projects/12715200/packages/maven</url>
     </repository>
   ```

1. Verwijder de volgende serverconfiguratie uit de `settings.xml` bestand, beschikbaar op `./cloudmanager/maven/settings.xml`:

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

1. Voer de [nieuwe installatiestappen](workfront-connector-install.md).
