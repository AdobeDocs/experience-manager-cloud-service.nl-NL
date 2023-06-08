---
title: Adaptieve Forms Core-componenten inschakelen in de as a Cloud Service en lokale ontwikkelomgeving van AEM Forms
seo-title: Step-by-Step Guide for enabling Adaptive Forms Core Components on AEM Forms as a Cloud Service and local development environment
description: Leer hoe u Adaptive Forms Core Components op AEM Forms as a Cloud Service kunt inschakelen met onze stapsgewijze handleiding. In onze zelfstudie wordt u door het proces geleid, zodat u deze krachtige functie eenvoudig kunt inschakelen voor uw AEM Forms-omgeving.
seo-description: Learn how to enable Adaptive Forms Core Components on AEM Forms as a Cloud Service with our step-by-step guide. Our tutorial walks you through the process, making it easy to enable this powerful feature for your AEM Forms environment.
contentOwner: Khushwant Singh
docset: CloudService
role: Admin
source-git-commit: f22554450d2eb1f4948f749ba00f78b568ee308f
workflow-type: tm+mt
source-wordcount: '1017'
ht-degree: 0%

---


# Adaptieve Forms Core-componenten inschakelen in de as a Cloud Service en lokale ontwikkelomgeving van AEM Forms {#enable-headless-adaptive-forms-on-aem-forms-cloud-service}

Als u Adaptive Forms Core Components inschakelt op AEM Forms as a Cloud Service, kunt u beginnen met het maken, publiceren en leveren van Core Components based Adaptive Forms and Headless Forms met uw AEM Forms Cloud Service-instanties naar meerdere kanalen. Voor het gebruik van Headless Adaptive Forms hebt u de omgeving geschikt voor Adaptive Forms Core Components nodig.

## Overwegingen

* Wanneer u een nieuw as a Cloud Service AEM Forms-programma maakt, [Adaptieve Forms Core-componenten en Headless Adaptive Forms zijn al ingeschakeld voor uw omgeving](#are-adaptive-forms-core-components-enabled-for-my-environment).

* Als u een ouder as a Cloud Service Forms-programma hebt met Core Components [niet ingeschakeld](#enable-components), kunt u [Aangepaste Forms Core-componentafhankelijkheden toevoegen](#enable-headless-adaptive-forms-for-an-aem-forms-as-a-cloud-service-environment) naar uw AEM as a Cloud Service opslagplaats en implementeer de opslagplaats in uw Cloud Service-omgevingen om Headless Adaptive Forms in te schakelen.

* Als uw bestaande omgeving van de Cloud Service optie biedt voor [Adaptieve Forms op basis van Core Components maken](creating-adaptive-form-core-components.md), Adaptive Forms Core Components en Headless Adaptive Forms zijn al ingeschakeld voor uw omgeving en u kunt Adaptive Forms op basis van Core-componenten gebruiken als een vorm zonder kop voor kanalen als mobiel, web, native apps en services waarvoor een headless representatie van Adaptive Forms vereist is.


## Adaptieve Forms Core-componenten en Forms zonder koptekst inschakelen {#enable-headless-forms}

Voer de volgende stappen uit, in de aangegeven volgorde, om Adaptive Forms Core Components en Headless Adaptive Forms in te schakelen voor een AEM Forms as a Cloud Service omgeving


![](/help/forms/assets/enable-headless-adaptive-forms-on-aem-forms-cloud-service.png)


## 1. Clone your AEM Forms as a Cloud Service Git Repository {#clone-git-repository}

1. Aanmelden bij [Cloud Manager](https://my.cloudmanager.adobe.com/) en selecteert u uw organisatie en programma.

1. Ga naar de **Pijpleidingen** kaart van uw **Programmaoverzicht** pagina, klikt u op de knop **Repo-info openen** om toegang te krijgen tot uw Git Repository en deze te beheren. De pagina bevat de volgende informatie:

   * URL naar de Git Repository van Cloud Manager.
   * Referenties van de Git Repository (Gebruikersnaam en Wachtwoord) Gebruikersnaam.

   Klikken **Wachtwoord genereren** om het wachtwoord weer te geven of te genereren.

1. Open terminal of bevelherinnering op uw lokale computer en stel het volgende bevel in werking:

   ```Shell
   git clone [Git Repository URL]
   ```

   Geef de gegevens op wanneer u hierom wordt gevraagd. De opslagplaats is gekloond op uw lokale computer.


## 2. Voeg adaptieve Forms Core Components-afhankelijkheden toe aan uw Git Repository {#add-adaptive-forms-core-components-dependencies}

1. Open de map Git Repository in een tekstcode-editor zonder opmaak. Bijvoorbeeld, de Code van VS.
1. Open de `[AEM Repository Folder]\pom.xml` bestand voor bewerking.
1. Versies van de `core.forms.components.version`, `core.forms.components.af.version` en `core.wcm.components.version` componenten met versies opgegeven in [kerncomponentdocumentatie](https://github.com/adobe/aem-core-forms-components). Als de component niet bestaat, voegt u deze componenten toe.

   ```XML
   <!-- Replace the version with the latest released version at https://github.com/adobe/aem-core-forms-components/tags -->
   
   <properties>
       <core.wcm.components.version>2.22.10</core.wcm.components.version>
       <core.forms.components.version>2.0.18</core.forms.components.version>
       <core.forms.components.af.version>2.0.18</core.forms.components.af.version>
   </properties>
   ```

   ![Opname van de nieuwste versie van Forms Core Components](/help/forms/assets/latest-forms-component-version.png)

1. In de sectie Afhankelijkheden van het dialoogvenster `[AEM Repository Folder]\pom.xml` , voegt u de volgende afhankelijkheden toe en slaat u het bestand op.

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

1. Open de `[AEM Repository Folder]/all/pom.xml` bestand voor bewerking. Voeg de volgende gebiedsdelen in toe `<embeddeds>` en sla het bestand op.

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
   >  Vervangen `${appId}` met uw appId.
   >
   >  Als u uw `${appId}`in de `[AEM Repository Folder]/all/pom.xml` bestand, doorzoeken `-packages/application/install` term. De tekst voor de `-packages/application/install` term is uw `${appId}`. De volgende code, bijvoorbeeld `myheadlessform` is `${appId}`.
   >
   >   
   ```
   >             <embedded>
   >                     <groupId>com.myheadlessform</groupId>
   >                     <artifactId>myheadlessform.ui.apps<artifactId>
   >                     <type>zip</type>
   >                   <target>/apps/myheadlessform-packages/application install</target>
   >             </embedded>
   >   ```

1. In de `<dependencies>` van de `[AEM Repository Folder]/all/pom.xml` , voegt u de volgende afhankelijkheden toe en slaat u het bestand op:

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

1. Open de `[AEM Repository Folder]/ui.apps/pom.xml` voor bewerken. Voeg de `af-core bundle` en sla het bestand op.

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

## 3. De bijgewerkte code samenstellen en implementeren

Implementeer de bijgewerkte code in uw lokale ontwikkelings- en Cloud Service-omgevingen om de Core Components op beide omgevingen in te schakelen:

* [Ontwikkel en stel bijgewerkte code op een lokale ontwikkelomgeving (AEM as a Cloud Service SDK) op](#core-components-on-aem-forms-local-sdk)

* [Nieuwe code maken en implementeren in een as a Cloud Service AEM Forms-omgeving](#core-components-on-aem-forms-cs)

### Ontwikkel en stel bijgewerkte code op een lokale ontwikkelomgeving op {#core-components-on-aem-forms-local-sdk}

1. Open de opdrachtprompt of terminal.

1. Navigeer naar de hoofdmap van het project voor de gegevensopslagruimte van Git.

1. Voer de volgende opdracht uit om het pakket voor uw omgeving te maken:

   ```Shell
       mvn clean install
   ```



   Nadat het pakket is gemaakt, kunt u het vinden op [Map voor gegevensopslagruimte it]\all\target\[appid].all-[versie].zip

1. Gebruik de [Pakketbeheer](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=en) om [Projectmap Archetype AEM]\all\target\[appid].all-[versie]ZIP-pakket over de lokale ontwikkelomgeving.


### Nieuwe code maken en implementeren in een as a Cloud Service AEM Forms-omgeving {#core-components-on-aem-forms-cs}

1. Open de terminal of opdrachtprompt.
1. Ga naar uw `[AEM Repository Folder]` en voer de volgende bevelen in de vermelde orde in werking

   ```Shell
    git add pom.xml
    git add all/pom.xml
    git add ui.apps/pom.xml
    git commit -m "Added dependencies for Adaptive Forms Core Components"
    git push origin
   ```

1. Nadat de bestanden zijn toegewezen aan Git Repository, [De pijplijn uitvoeren](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html).

   Nadat de pijpleidingslooppas succesvol is, worden de Adaptieve Componenten van de Kern van Forms toegelaten voor het overeenkomstige milieu. Bovendien worden een Adaptive Forms (Core Components)-sjabloon en een Canvas 3.0-thema toegevoegd aan uw as a Cloud Service Forms-omgeving, zodat u opties hebt voor het aanpassen en maken van op Core Components gebaseerde Adaptive Forms.


## Veelgestelde vragen {#faq}

### Wat zijn kerncomponenten? {#core-components}

De [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) zijn een reeks gestandaardiseerde WCM-componenten (Web Content Management) voor AEM om de ontwikkelingstijd te versnellen en de onderhoudskosten van uw websites te verlagen.

### Welke mogelijkheden worden toegevoegd aan het toelaten van kerncomponenten? {#core-components-capabilities}

Wanneer de Adaptive Forms Core Components voor uw omgeving is ingeschakeld, worden een leeg, op Core Components gebaseerd adaptief formulier sjabloon en Canvas 3.0 thema toegevoegd aan uw omgeving. Nadat u Adaptive Forms Core Components voor uw omgeving hebt ingeschakeld, kunt u:

* [Op Adaptieve Forms gebaseerde Core Components maken](/help/forms/creating-adaptive-form-core-components.md).
* [Op kerncomponenten gebaseerde adaptieve formuliersjablonen maken](/help/forms/template-editor.md).
* [Aangepaste thema&#39;s maken voor adaptieve formuliersjablonen op basis van kerncomponenten](/help/forms/using-themes-in-core-components.md).
* [De JSON-representaties van de Serve Core Component gebaseerd op adaptieve formulieren naar kanalen zoals mobiel, web, systeemeigen apps en services waarvoor een formulier zonder kop moet worden weergegeven](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html).

### Zijn Adaptive Forms Core Components ingeschakeld voor mijn omgeving? {#enable-components}

Om te controleren of Adaptive Forms Core Components geschikt zijn voor uw omgeving:

1. [De as a Cloud Service AEM Forms-opslagplaats klonen](#1-clone-your-aem-forms-as-a-cloud-service-git-repository).

1. Open de `[AEM Repository Folder]/all/pom.xml` bestand van de AEM Forms Cloud Service Git Repository.

1. Zoek naar de volgende gebiedsdelen:

   * core-forms-components-af-core
   * core-forms-components-core
   * core-forms-components-apps
   * core-forms-components-af-apps
   * core-forms-components-examples-apps
   * core-forms-components-examples-content

   ![Zoek het core-forms-components-af-core artefact op all/pom.xml](/help/forms/assets/enable-headless-adaptive-forms-on-aem-forms-cloud-service-locate-core-af-artifact.png)

   Als de afhankelijkheden bestaan, worden Adaptive Forms Core Components ingeschakeld voor uw omgeving.

