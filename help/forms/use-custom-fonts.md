---
title: 'Aangepaste lettertypen gebruiken '
description: 'Aangepaste lettertypen gebruiken '
source-git-commit: 94fe397d6ce08380ef08b65b47fe2c1aeb015ca3
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---


# Aangepaste lettertypen gebruiken

**Cloud Service Communications-documentatie bevindt zich in bèta**

Met Forms as a Cloud Service Communications kunt u een XDP-sjabloon, een op XDP gebaseerd PDF-document of een Acrobat-formulier (AcroForm) combineren met XML-gegevens om PDF-documenten te genereren. U kunt Communicatie ook gebruiken om PDF en XDP-documenten te combineren, opnieuw te rangschikken en uit te breiden en om informatie over PDF-documenten te verkrijgen.

Naast de eerder genoemde bewerkingen kunt u lettertypen gebruiken die zijn opgenomen in Cloud Service- of aangepaste lettertypen (door de organisatie goedgekeurde lettertypen) om de gegenereerde PDF-documenten te genereren. U kunt het ontwikkelingsproject van de Cloud Service gebruiken om douanedoopvonten aan uw milieu van de Cloud Service toe te voegen.

## Gedrag van PDF-documenten

U kunt [een lettertype insluiten](https://adobedocs.github.io/experience-manager-forms-cloud-service-developer-reference/api/sync/#tag/PDFOutputOptions) naar een PDF-document. Wanneer een lettertype is ingesloten, wordt het PDF-document op alle platformen op dezelfde manier weergegeven. Er worden ingesloten lettertypen gebruikt voor een consistente vormgeving. Wanneer een lettertype niet is ingesloten, is de rendering van het lettertype afhankelijk van de renderinstellingen van PDF viewer-clients zoals Acrobat of Acrobat Reader. Als het lettertype beschikbaar is op de clientcomputer, gebruikt de PDF het opgegeven lettertype, anders wordt de PDF weergegeven met een standaard fallback-lettertype.

## Aangepaste lettertypen toevoegen aan de as a Cloud Service Forms-omgeving {#custom-fonts-cloud-service}

Aangepaste lettertypen toevoegen aan uw Cloud Service-omgeving:

1. De instellingen en openen [lokaal ontwikkelingsproject](setup-local-development-environment.md). U kunt elke gewenste IDE gebruiken.
1. Maak in de mapstructuur op hoofdniveau van het project een map (module) waarin u aangepaste lettertypen kunt opslaan en aangepaste lettertypen kunt toevoegen aan de map. Bijvoorbeeld lettertypen/src/main/resources
   ![Map Fonts](assets/fonts.png)

1. Open het bestand pom.xml in de module Fonts van het ontwikkelingsproject.
1. Voeg jar plugin aan het pomdossier toe:

   ```xml
   <plugin>
       <groupId>org.apache.maven.plugins</groupId>
       <artifactId>maven-jar-plugin</artifactId>
       <version>3.1.2</version>
       <configuration>
           <archive>
               <manifest>
                   <addDefaultEntries/>
                   <addDefaultImplementationEntries/>
               </manifest>
           </archive>
       </configuration>
   </plugin>
   ```


1. Voeg de `<Font-Archive-Version>` manifesteer ingang het .pom dossier en vastgestelde waarde van versie aan 1:

   ```xml
   <plugin>
       <groupId>org.apache.maven.plugins</groupId>
       <artifactId>maven-jar-plugin</artifactId>
       <version>3.1.2</version>
       <configuration>
           <archive>
               <manifest>
                   <addDefaultEntries/>
                   <addDefaultImplementationEntries/>
               </manifest>
               <manifestEntries>
                   <Font-Archive-Version>1</Font-Archive-Version>
                   <Font-Archive-Contents>/</Font-Archive-Contents>
               </manifestEntries> 
           </archive>
       </configuration>
   </plugin>
   ```

1. Map met lettertypen toevoegen aan `<modules>` vermeld in het pombestand. Bijvoorbeeld:

   ```xml
   <modules>
       <module>all</module>
       <module>core</module>
       <module>ui.frontend</module>
       <module>ui.apps</module>
       <module>ui.apps.structure</module>
       <module>ui.config</module>
       <module>ui.content</module>
       <module>it.tests</module>
       <module>dispatcher</module>
       <module>dispatcher.ams</module>
       <module>dispatcher.cloud</module>
       <module>ui.tests</module>
       <module>fonts</module>
   </modules>
   ```

   De map Fonts bevat alle aangepaste lettertypen.

1. De bijgewerkte code inchecken en [de pijpleiding in werking stellen](/help/implementing/cloud-manager/deploy-code.md) om de lettertypen te implementeren in uw Cloud Service-omgeving.

1. (Optioneel) Open de opdrachtprompt, navigeer naar de lokale projectmap en voer de onderstaande opdracht uit. De opdracht verpakt de lettertypen in een .jar-bestand, samen met relevante informatie. Met het .jar-bestand kunt u aangepaste lettertypen toevoegen aan een lokale ontwikkelomgeving van Forms Cloud Service.

   ```shell
   mvn clean install
   ```

## Aangepaste lettertypen toevoegen aan uw lokale ontwikkelomgeving voor Forms Cloud Service {#custom-fonts-cloud-service-sdk}

1. Start uw lokale ontwikkelomgeving.
1. Navigeren naar `<aem install directory>/crx-quickstart/install` map.
1. Plaats de `<jar file contaning custom fonts and relevant deployment code>.jar` naar de installatiemap. Als u het .jar dossier niet hebt, voer de stappen uit die in worden vermeld [Aangepaste lettertypen toevoegen aan de as a Cloud Service Forms-omgeving](#custom-fonts-cloud-service) om het bestand te genereren.
1. Voer de [SDK-omgeving op basis van docker](setup-local-development-environment.md#docker-microservices)


   >[!NOTE]
   >
   >Wanneer u een bijgewerkt bestand met aangepaste lettertypen .jar naar de lokale ontwikkelomgeving implementeert, start u de op docker gebaseerde SDK-omgeving opnieuw.