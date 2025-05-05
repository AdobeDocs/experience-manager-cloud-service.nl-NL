---
title: Hoe kan ik Adaptive Forms Core Components inschakelen in een as a Cloud Service en lokale ontwikkelomgeving van AEM Forms?
description: Leer hoe u Adaptive Forms Core Components kunt inschakelen op AEM Forms as a Cloud Service.
contentOwner: Khushwant Singh
docset: CloudService
role: Admin, Developer, User
feature: Adaptive Forms, Core Components
exl-id: 32a574e2-faa9-4724-a833-1e4c584582cf
source-git-commit: 05548d56d791584781606b02839c5602b4469f7b
workflow-type: tm+mt
source-wordcount: '985'
ht-degree: 0%

---

# Adaptieve Forms Core-componenten inschakelen {#enable-headless-adaptive-forms-on-aem-forms-cloud-service}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-core-components/enable-adaptive-forms-core-components.html?lang=nl-NL) |
| AEM as a Cloud Service | Dit artikel |

Als u Adaptive Forms Core Components inschakelt op AEM Forms as a Cloud Service, kunt u beginnen met het maken, publiceren en leveren van Core Components based Adaptive Forms and Headless Forms met uw AEM Forms Cloud Service-instanties naar meerdere kanalen. Voor het gebruik van Headless Adaptive Forms hebt u de omgeving geschikt voor Adaptive Forms Core Components nodig.

## Overwegingen

* Wanneer u een vers as a Cloud Service programma van AEM Forms creeert, [ de Aangepaste Componenten van de Kern van Forms en Zwaardeloze Aanpassings Forms worden reeds toegelaten voor uw milieu ](#are-adaptive-forms-core-components-enabled-for-my-environment).

* Als u een ouder as a Cloud Service programma van Forms hebt waar de Componenten van de Kern [ niet ](#enable-components) worden toegelaten, kunt u [ de Aangepaste gebiedsdelen van de Componenten van de Kern van Forms ](#enable-headless-adaptive-forms-for-an-aem-forms-as-a-cloud-service-environment) toevoegen aan uw bewaarplaats van AEM as a Cloud Service en de bewaarplaats opstellen aan uw milieu&#39;s van de Cloud Service om Zwaardeloze Aanpassings Forms toe te laten.

* Als uw bestaand milieu van de Cloud Service optie [ verstrekt om op kern-componenten-Gebaseerde Aangepaste Forms ](creating-adaptive-form-core-components.md) tot stand te brengen, zijn de Aangepaste Componenten van de Kern van Forms en Zwaardeloze Aanpassings Forms reeds toegelaten voor uw milieu en u kunt de Aangepaste Forms van de Component van de Kern als hoofdloze vormen aan kanalen zoals mobiel, Web, inheemse apps, en de diensten dienen die een hoofdloze vertegenwoordiging van Aanpassings Forms vereisen.


## Adaptieve Forms Core-componenten en Forms zonder koptekst inschakelen {#enable-headless-forms}

Voer de volgende stappen uit in de aangegeven volgorde om Adaptive Forms Core Components en Headless Adaptive Forms voor een AEM Forms as a Cloud Service omgeving in te schakelen


![ laat kerncomponenten en hoofd toe aanpassende vormen ](/help/forms/assets/enable-headless-adaptive-forms-on-aem-forms-cloud-service.png)


## 1. Clone your AEM Forms as a Cloud Service Git Repository {#clone-git-repository}

1. Login aan [ Cloud Manager ](https://my.cloudmanager.adobe.com/) en selecteer uw organisatie en programma.

1. Navigeer aan de **Pipelines** kaart van uw **pagina van het Overzicht van het Programma**, klik de **Info van de Reactie van de Toegang** knoop om tot uw Bewaarplaats van het Bezit van het Bezit toegang te hebben en te beheren. De pagina bevat de volgende informatie:

   * URL naar de Cloud Manager Git Repository.
   * Referenties van de Git Repository (Gebruikersnaam en Wachtwoord) Gebruikersnaam.

   Klik **produceer Wachtwoord** om het wachtwoord te bekijken of te produceren.

1. Open terminal of bevelherinnering op uw lokale computer en stel het volgende bevel in werking:

   ```Shell
   git clone [Git Repository URL]
   ```

   Geef de gegevens op wanneer u hierom wordt gevraagd. De opslagplaats is gekloond op uw lokale computer.


## 2. Voeg adaptieve Forms Core Components-afhankelijkheden toe aan uw Git Repository {#add-adaptive-forms-core-components-dependencies}

1. Open de map Git Repository in een tekstcode-editor zonder opmaak. Bijvoorbeeld, de Code van VS.
1. Open het `[AEM Repository Folder]\pom.xml` -bestand om het te bewerken.
1. Vervang versies van `core.forms.components.version`, `core.forms.components.af.version` en `core.wcm.components.version` componenten met versies die in [ worden gespecificeerd kerncomponentendocumentatie ](https://github.com/adobe/aem-core-forms-components). Als de component niet bestaat, voegt u deze componenten toe.

   ```XML
   <!-- Replace the version with the latest released version at https://github.com/adobe/aem-core-forms-components/tags -->
   
   <properties>
       <core.wcm.components.version>2.22.10</core.wcm.components.version>
       <core.forms.components.version>2.0.18</core.forms.components.version>
       <core.forms.components.af.version>2.0.18</core.forms.components.af.version>
   </properties>
   ```

   ![ de recentste versie van de Verwijzing van de Componenten van de Kern van Forms ](/help/forms/assets/latest-forms-component-version.png)

1. Voeg in de sectie Afhankelijkheden van het `[AEM Repository Folder]\pom.xml` -bestand de volgende afhankelijkheden toe en sla het bestand op.

   ```XML
       <!-- WCM Core Component Examples Dependencies -->
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.apps</artifactId>
               <type>zip</type>
               <version>${core.wcm.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.content</artifactId>
               <type>zip</type>
               <version>${core.wcm.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.config</artifactId>
               <version>${core.wcm.components.version}</version>
               <type>zip</type>
           </dependency>    
           <!-- End of WCM Core Component Examples Dependencies -->
           <!-- Forms Core Component Dependencies -->
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-core</artifactId>
               <version>${core.forms.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-apps</artifactId>
               <version>${core.forms.components.version}</version>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-af-core</artifactId>
               <version>${core.forms.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-af-apps</artifactId>
               <version>${core.forms.components.version}</version>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-apps</artifactId>
               <type>zip</type>
               <version>${core.forms.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-content</artifactId>
               <type>zip</type>
               <version>${core.forms.components.version}</version>
           </dependency>
   <!-- End of AEM Forms Core Component Dependencies -->
   ```

1. Open het `[AEM Repository Folder]/all/pom.xml` -bestand om het te bewerken. Voeg de volgende afhankelijkheden toe aan de sectie `<embeddeds>` en sla het bestand op.

   ```XML
   <!-- WCM Core Component Examples Dependencies -->
   
   <!-- inside plugin config of filevault-package-maven-plugin -->  
   <!-- embed wcm core components examples artifacts -->
   
   <embedded>
       <groupId>com.adobe.cq</groupId>
       <artifactId>core.wcm.components.examples.ui.apps</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.cq</groupId>
       <artifactId>core.wcm.components.examples.ui.content</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.cq</groupId>
       <artifactId>core.wcm.components.examples.ui.config</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <!-- embed forms core components artifacts -->
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-af-apps</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/application/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-af-core</artifactId>
       <target>/apps/${appId}-vendor-packages/application/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-examples-apps</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-examples-content</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   ```

   >[!NOTE]
   >
   >
   >  Vervang `${appId}` door uw appId.
   >
   >  Zoek in het `[AEM Repository Folder]/all/pom.xml` -bestand naar de term `-packages/application/install` om de term `${appId}` te zoeken. De tekst voor de term `-packages/application/install` is de `${appId}` . De volgende code, `myheadlessform` is bijvoorbeeld `${appId}` .
   >
   >   ```
   >             <embedded>
   >                     <groupId>com.myheadlessform</groupId>
   >                     <artifactId>myheadlessform.ui.apps<artifactId>
   >                     <type>zip</type>
   >                   <target>/apps/myheadlessform-packages/application install</target>
   >             </embedded>
   >   ```

1. Voeg in de sectie `<dependencies>` van het `[AEM Repository Folder]/all/pom.xml` -bestand de volgende afhankelijkheden toe en sla het bestand op:

   ```XML
           <!-- Other existing dependencies -->
           <!-- wcm core components examples dependencies -->
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.apps</artifactId>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.config</artifactId>
               <type>zip</type>
               </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.content</artifactId>
               <type>zip</type>
           </dependency>
               <!-- forms core components dependencies -->
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-af-apps</artifactId>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-apps</artifactId>
               <type>zip</type>
           </dependency>
               <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-content</artifactId>
               <type>zip</type>
           </dependency>
   ```

1. Open de `[AEM Repository Folder]/ui.apps/pom.xml` voor bewerking. Voeg de `af-core bundle` afhankelijkheid toe en sla het bestand op.

   ```XML
       <dependency>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-af-core</artifactId>
       </dependency>
   ```

   >[!NOTE]
   >
   >Zorg ervoor dat de volgende Adaptive Forms Core Components-artefacten niet in uw project zijn opgenomen.
   >
   > `<dependency>`
   >
   >   `<groupId>com.adobe.aem</groupId>`
   >   `<artifactId>core-forms-components-apps</artifactId>`
   >
   > `</dependency>`
   >
   > en
   >
   > `<dependency>`
   >
   >   `<groupId>com.adobe.aem</groupId>`
   >   `<artifactId>core-forms-components-core</artifactId>`
   >
   > `</dependency>`


1. Sla het bestand op en sluit het.

## 3. Bouw en stel de bijgewerkte code op

Implementeer de bijgewerkte code in uw lokale ontwikkelings- en Cloud Service-omgevingen om de Core Components op beide omgevingen in te schakelen:

* [Bijgewerkte code maken en implementeren in een lokale ontwikkelomgeving (AEM as a Cloud Service SDK)](#core-components-on-aem-forms-local-sdk)

* [Een bijgewerkte code maken en implementeren in een AEM Forms as a Cloud Service omgeving](#core-components-on-aem-forms-cs)

### Ontwikkel en stel bijgewerkte code op een lokale ontwikkelomgeving op {#core-components-on-aem-forms-local-sdk}

1. Open de opdrachtprompt of terminal.

1. Navigeer naar de hoofdmap van het project voor de gegevensopslagruimte van Git.

1. Voer de volgende opdracht uit om het pakket voor uw omgeving te maken:

   ```Shell
       mvn clean install
   ```



   Nadat het pakket met succes wordt gebouwd, kunt u het bij [ de Omslag van de Bewaarplaats van de it ] \all\target\ [appid].all- [ versie ].zip vinden

1. Gebruik de [ Manager van het Pakket ](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=nl-NL) om het [ AEM Archetype Omslag van het Project ] \all\target\ [appid].all- [ versie ] .zip pakket op lokaal ontwikkelomgeving op te stellen.


### Een bijgewerkte code maken en implementeren in een AEM Forms as a Cloud Service omgeving {#core-components-on-aem-forms-cs}

1. Open de terminal of opdrachtprompt.
1. Navigeer naar uw `[AEM Repository Folder]` en voer de volgende opdrachten in de vermelde volgorde uit

   ```Shell
    git add pom.xml
    git add all/pom.xml
    git add ui.apps/pom.xml
    git commit -m "Added dependencies for Adaptive Forms Core Components"
    git push origin
   ```

1. Nadat de dossiers aan de Bewaarplaats van de Bewaarplaats van het Git worden geëngageerd, [ stel de pijpleiding ](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html?lang=nl-NL) in werking.

   Nadat de pijpleidingslooppas succesvol is, worden de Adaptieve Componenten van de Kern van Forms toegelaten voor het overeenkomstige milieu. Bovendien worden een Adaptive Forms (Core Components)-sjabloon en een Canvas 3.0-thema toegevoegd aan uw Forms as a Cloud Service omgeving, zodat u opties kunt kiezen om de op Core Components gebaseerde Adaptive Forms aan te passen en te maken.


## Veelgestelde vragen {#faq}

### Wat zijn kerncomponenten? {#core-components}

De [ Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=nl-NL) zijn een reeks gestandaardiseerde componenten van het Beheer van de Inhoud van het Web (WCM) voor AEM om ontwikkelingstijd te versnellen en onderhoudskosten van uw websites te drukken.

### Welke mogelijkheden worden toegevoegd aan het toelaten van kerncomponenten? {#core-components-capabilities}

Wanneer de Adaptive Forms Core Components voor uw omgeving is ingeschakeld, worden een leeg, op Core Components gebaseerd adaptief formulier sjabloon en Canvas 3.0 thema toegevoegd aan uw omgeving. Nadat u Adaptive Forms Core Components voor uw omgeving hebt ingeschakeld, kunt u:

* [ creeer de Componenten van de Kern die Adaptieve Forms ](/help/forms/creating-adaptive-form-core-components.md) worden gebaseerd.
* [ creeer de Componenten van de Kern gebaseerde Aangepaste malplaatjes van de Vorm ](/help/forms/template-editor.md).
* [ creeer douanethema&#39;s voor de Componenten van de Kern de Gebaseerde Aangepaste malplaatjes van de Vorm ](/help/forms/using-themes-in-core-components.md).
* [ de Reeks van de Kern van de Server Component gebaseerde Aangepaste vertegenwoordiging van de Vorm JSON aan kanalen zoals mobiel, Web, inheemse apps, en de diensten die de hoofdloze vertegenwoordiging van een vorm ](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=nl-NL) vereisen.

### Zijn Adaptive Forms Core Components ingeschakeld voor mijn omgeving? {#enable-components}

Om te controleren of Adaptive Forms Core Components geschikt zijn voor uw omgeving:

1. [ Kloon uw as a Cloud Service bewaarplaats van AEM Forms ](#1-clone-your-aem-forms-as-a-cloud-service-git-repository).

1. Open het `[AEM Repository Folder]/all/pom.xml` -bestand van de AEM Forms Cloud Service Git Repository.

1. Zoek naar de volgende gebiedsdelen:

   * core-forms-components-af-core
   * core-forms-components-core
   * core-forms-components-apps
   * core-forms-components-af-apps
   * core-forms-components-examples-apps
   * core-forms-components-examples-content

   ![ bepaal de plaats van het kern-vormen-componenten-af-kern artefact in all/pom.xml ](/help/forms/assets/enable-headless-adaptive-forms-on-aem-forms-cloud-service-locate-core-af-artifact.png)

   Als de afhankelijkheden bestaan, worden Adaptive Forms Core Components ingeschakeld voor uw omgeving.

>[!MORELIKETHIS]
>
>* [ creeer een Aangepast Vorm ](/help/forms/creating-adaptive-form-core-components.md)
