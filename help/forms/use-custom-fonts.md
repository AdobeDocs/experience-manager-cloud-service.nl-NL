---
title: Hoe kunnen we aangepaste lettertypen gebruiken in AEM Forms?
description: Leer aangepaste lettertypen toe te voegen aan een Forms as a Cloud Service-omgeving.
badgeSaas: label="AEM Forms" type="Positive" tooltip="van toepassing op AEM Forms)."
exl-id: 88214d36-fb97-4d46-a9fe-71dbc7826eb1
feature: Adaptive Forms
role: Admin, User
source-git-commit: 89b0f2a8ca9d2f60365a5c3962b0b4e826f79b3e
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# Aangepaste lettertypen gebruiken

**Cloud Service Communicatie documentatie is in bèta**

Met Forms as a Cloud Service Communications kunt u een XDP-sjabloon, een op XDP gebaseerd PDF-document of een Acrobat-formulier (AcroForm) combineren met XML-gegevens om PDF-documenten te genereren. U kunt Communicatie ook gebruiken om PDF- en XDP-documenten te combineren, opnieuw te rangschikken en te vergroten en om informatie over PDF-documenten te verkrijgen.

Naast de eerder genoemde bewerkingen kunt u lettertypen uit Cloud Service of aangepaste lettertypen (door de organisatie goedgekeurde lettertypen) gebruiken om de gegenereerde PDF-documenten te genereren. Met het Cloud Service-ontwikkelingsproject kunt u aangepaste lettertypen toevoegen aan uw Cloud Service-omgeving.

## Gedrag van PDF-documenten

U kunt [&#x200B; een doopvont &#x200B;](https://adobedocs.github.io/experience-manager-forms-cloud-service-developer-reference/references/output-sync/#tag/PrintedOutputOptions) aan een document van PDF inbedden. Wanneer een lettertype is ingesloten, wordt het PDF-document op alle platforms op dezelfde manier weergegeven. Er worden ingesloten lettertypen gebruikt voor een consistente vormgeving. Wanneer een lettertype niet is ingesloten, is de rendering van lettertypen afhankelijk van de renderinstellingen van PDF-viewerclients zoals Acrobat of Acrobat Reader. Als het lettertype beschikbaar is op de clientcomputer, gebruikt de PDF het opgegeven lettertype, anders wordt de PDF weergegeven met een standaard fallback-lettertype.

## Aangepaste lettertypen toevoegen aan uw Forms as a Cloud Service-omgeving {#custom-fonts-cloud-service}

Aangepaste lettertypen toevoegen aan uw Cloud Service-omgeving:

1. Opstelling en open het [&#x200B; lokale ontwikkelingsproject &#x200B;](setup-local-development-environment.md). U kunt elke gewenste IDE gebruiken.
1. Maak in de mapstructuur op hoofdniveau van het project een map (module) waarin u aangepaste lettertypen kunt opslaan en aangepaste lettertypen kunt toevoegen aan de map. Bijvoorbeeld lettertypen/src/main/resources
   ![&#x200B; omslag van Doopvonten &#x200B;](assets/fonts.png)

1. Open het bestand pom.xml in de module Fonts van het ontwikkelingsproject.
1. Voeg jar plug-in toe aan het pombestand:

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

1. Voeg het `<Font-Archive-Version>` manifest-item toe aan het .pom-bestand en stel de waarde van versie in op 1:

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

1. Voeg de map met lettertypen toe aan `<modules>` die in het pombestand wordt vermeld. Bijvoorbeeld:

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

1. Controle in de bijgewerkte code en [&#x200B; stelt de pijpleiding &#x200B;](/help/implementing/cloud-manager/deploy-code.md) in werking om de doopvonten aan uw milieu van Cloud Service op te stellen.

1. (Optioneel) Open de opdrachtprompt, navigeer naar de lokale projectmap en voer de onderstaande opdracht uit. De opdracht verpakt de lettertypen in een .jar-bestand, samen met relevante informatie. U kunt het .jar-bestand gebruiken om aangepaste lettertypen toe te voegen aan een lokale ontwikkelomgeving van Forms Cloud Service.

   ```shell
   mvn clean install
   ```

## Aangepaste lettertypen toevoegen aan uw lokale Forms Cloud Service-ontwikkelomgeving {#custom-fonts-cloud-service-sdk}

1. Start uw lokale ontwikkelomgeving.
1. Navigeer naar de map `<aem install directory>/crx-quickstart/install` .
1. Plaats de `<jar file contaning custom fonts and relevant deployment code>.jar` naar de installatiemap. Als u niet het .jar dossier hebt, voer de stappen uit in [&#x200B; worden vermeld voeg douanedoopvonten aan uw milieu van Forms as a Cloud Service &#x200B;](#custom-fonts-cloud-service) sectie toe om het dossier te produceren dat.
1. Stel het [&#x200B; op docker-Gebaseerde milieu van SDK &#x200B;](setup-local-development-environment.md#docker-microservices) in werking


   >[!NOTE]
   >
   >Wanneer u een bijgewerkt bestand met aangepaste lettertypen .jar in de lokale ontwikkelomgeving implementeert, start u de op dockers gebaseerde SDK-omgeving opnieuw.
