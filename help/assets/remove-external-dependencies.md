---
title: Externe afhankelijkheden voor bestaande installaties verwijderen
description: Externe afhankelijkheden voor bestaande installaties verwijderen
feature: Workfront Integrations and Apps
exl-id: 5b28ce97-2719-47b8-a386-77d4aaddbe81
role: Admin
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# Externe afhankelijkheden voor bestaande installaties verwijderen {#remove-external-depedencies}

| [ Beste praktijken van het Onderzoek ](/help/assets/search-best-practices.md) | [ Beste praktijken van Meta-gegevens ](/help/assets/metadata-best-practices.md) | [ Content Hub ](/help/assets/product-overview.md) | [ Dynamic Media met mogelijkheden OpenAPI ](/help/assets/dynamic-media-open-apis-overview.md) | [ de ontwikkelaarsdocumentatie van AEM Assets ](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

De Adobe adviseert u om configuratiestappen voor bestaande verbeterde schakelaarinstallaties voor Workfront uit te voeren om de gebiedsdelen op de distributiepunten van de Hoodoo te verwijderen.

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

1. Voer de [ nieuwe installatiestappen ](workfront-connector-install.md) uit.
