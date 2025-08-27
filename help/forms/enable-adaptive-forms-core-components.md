---
title: Adaptieve Forms Core-componenten op AEM Forms as a Cloud Service controleren en inschakelen
description: Leer hoe u kunt controleren of Adaptive Forms Core Components is ingeschakeld en hoe u deze indien nodig kunt inschakelen op AEM Forms as a Cloud Service.
contentOwner: Khushwant Singh
docset: CloudService
role: Admin, Developer, User
feature: Adaptive Forms, Core Components
exl-id: 32a574e2-faa9-4724-a833-1e4c584582cf
hide: true
hidefromtoc: true
source-git-commit: 3c1931d67e69d155e777c8761fe2bbbd21461ddf
workflow-type: tm+mt
source-wordcount: '1235'
ht-degree: 0%

---

# Aangepaste Forms Core-componenten controleren en inschakelen {#enable-headless-adaptive-forms-on-aem-forms-cloud-service}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6.5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-core-components/enable-adaptive-forms-core-components.html) |
| AEM as a Cloud Service | Dit artikel |

Adaptieve Forms Core-componenten en Headless Adaptive Forms zijn al ingeschakeld voor de meeste AEM Forms as a Cloud Service-klanten. Hierdoor kunt u Adaptieve Forms en Headless Forms op basis van Core Components maken, publiceren en leveren met uw AEM Forms Cloud Service-instanties naar meerdere kanalen.

## Controleren of adaptieve Forms Core-componenten zijn ingeschakeld {#check-if-enabled}

Controleer voordat u een schakelprocedure uitvoert of Adaptive Forms Core Components al ingeschakeld is voor uw omgeving:

### Voor nieuwe AEM Forms as a Cloud Service-programma&#39;s

Wanneer u een nieuw AEM Forms as a Cloud Service-programma maakt, zijn Adaptive Forms Core Components en Headless Adaptive Forms al ingeschakeld voor uw omgeving.

### Voor bestaande Cloud Service-omgevingen

Als uw bestaand milieu van Cloud Service de optie [ verstrekt om Kern te creëren op componenten-Gebaseerde Aangepaste Forms ](creating-adaptive-form-core-components.md), worden de Aangepaste Componenten van de Kern van Forms en Zwaardeloze Aanpassings Forms reeds toegelaten voor uw milieu.

### Controleren op uw opslagplaats

Om te bevestigen dat Adaptive Forms Core Components geschikt zijn voor uw omgeving:

1. Clone your AEM Forms as a Cloud Service repository.

1. Open het `[AEM Repository Folder]/all/pom.xml` -bestand van de AEM Forms Cloud Service Git Repository.

1. Zoek naar de volgende gebiedsdelen:

   * core-forms-components-af-core
   * core-forms-components-core
   * core-forms-components-apps
   * core-forms-components-af-apps
   * core-forms-components-examples-apps
   * core-forms-components-examples-content

   ![ bepaal de plaats van het kern-vormen-componenten-af-kern artefact in all/pom.xml ](/help/forms/assets/enable-headless-adaptive-forms-on-aem-forms-cloud-service-locate-core-af-artifact.png)

   Als deze afhankelijkheden bestaan, worden Adaptive Forms Core Components ingeschakeld voor uw omgeving.

## Wanneer handmatige activering nodig is {#when-manual-enablement-needed}

Alleen als u een ouder Forms as a Cloud Service-programma hebt waarvoor Core Components niet is ingeschakeld (zoals hierboven is aangegeven), moet u handmatig adaptieve Forms Core Components-afhankelijkheden toevoegen aan uw AEM as a Cloud Service-opslagplaats en de opslagplaats implementeren in uw Cloud Service-omgevingen.

+++ Handmatige actiestappen 

>[!WARNING]
>
>Voer alleen deze stappen uit als de bovenstaande verificatiecontrole bevestigt dat Adaptive Forms Core Components NIET is ingeschakeld voor uw omgeving.

Voer de volgende stappen uit, in de aangegeven volgorde, om Adaptive Forms Core Components en Headless Adaptive Forms voor een AEM Forms as a Cloud Service-omgeving in te schakelen:

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


## &#x200B;2. Voeg adaptieve Forms Core Components-afhankelijkheden toe aan uw Git Repository {#add-adaptive-forms-core-components-dependencies}

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
   >  Zoek in het `${appId}` -bestand naar de term `[AEM Repository Folder]/all/pom.xml` om de term `-packages/application/install` te zoeken. De tekst voor de term `-packages/application/install` is de `${appId}` . De volgende code, `myheadlessform` is bijvoorbeeld `${appId}` .
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

## &#x200B;3. Bouw en stel de bijgewerkte code op

Implementeer de bijgewerkte code in uw lokale ontwikkelings- en Cloud Service-omgevingen om de Core Components in beide omgevingen in te schakelen:

* [Bijgewerkte code maken en implementeren in een lokale ontwikkelomgeving (AEM as a Cloud Service SDK)](#core-components-on-aem-forms-local-sdk)

* [Updatecode samenstellen en implementeren in een AEM Forms as a Cloud Service-omgeving](#core-components-on-aem-forms-cs)

### Ontwikkel en stel bijgewerkte code op een lokale ontwikkelomgeving op {#core-components-on-aem-forms-local-sdk}

1. Open de opdrachtprompt of terminal.

1. Navigeer naar de hoofdmap van het project voor de gegevensopslagruimte van Git.

1. Voer de volgende opdracht uit om het pakket voor uw omgeving te maken:

   ```Shell
       mvn clean install
   ```



   Nadat het pakket met succes wordt gebouwd, kunt u het bij [ de Omslag van de Bewaarplaats van de it ] \all\target\ [appid].all- [ versie ].zip vinden

1. Gebruik de [ Manager van het Pakket ](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=en) om de [ Archetype Omslag van het Project van AEM ] \all\target\ [appid].all- [ versie ] .zip pakket op lokaal ontwikkelomgeving op te stellen.


### Updatecode samenstellen en implementeren in een AEM Forms as a Cloud Service-omgeving {#core-components-on-aem-forms-cs}

1. Open de terminal of opdrachtprompt.
1. Navigeer naar uw `[AEM Repository Folder]` en voer de volgende opdrachten in de vermelde volgorde uit

   ```Shell
    git add pom.xml
    git add all/pom.xml
    git add ui.apps/pom.xml
    git commit -m "Added dependencies for Adaptive Forms Core Components"
    git push origin
   ```

1. Nadat de dossiers aan de Bewaarplaats van de Bewaarplaats van het Git worden geëngageerd, [ stel de pijpleiding ](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html) in werking.

   Nadat de pijpleidingslooppas succesvol is, worden de Adaptieve Componenten van de Kern van Forms toegelaten voor het overeenkomstige milieu. Bovendien worden een Adaptive Forms (Core Components)-sjabloon en Canvas 3.0-thema toegevoegd aan uw Forms as a Cloud Service-omgeving, zodat u opties hebt voor het aanpassen en maken van op Core Components gebaseerde Adaptive Forms.

+++

## Veelgestelde vragen {#faq}

### Wat zijn kerncomponenten? {#core-components}

De [ Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) zijn een reeks gestandaardiseerde componenten van het Beheer van de Inhoud van het Web (WCM) voor AEM om ontwikkelingstijd te versnellen en onderhoudskosten van uw websites te drukken.

### Welke mogelijkheden worden toegevoegd aan het toelaten van kerncomponenten? {#core-components-capabilities}

Wanneer de Adaptive Forms Core Components voor uw omgeving is ingeschakeld, worden een leeg, op Core Components gebaseerd adaptief formulier sjabloon en Canvas 3.0 thema toegevoegd aan uw omgeving. Nadat u Adaptive Forms Core Components voor uw omgeving hebt ingeschakeld, kunt u:

* [ creeer de Componenten van de Kern die Adaptieve Forms ](/help/forms/creating-adaptive-form-core-components.md) worden gebaseerd.
* [ creeer de Componenten van de Kern gebaseerde Aangepaste malplaatjes van de Vorm ](/help/forms/template-editor.md).
* [ creeer douanethema&#39;s voor de Componenten van de Kern de Gebaseerde Aangepaste malplaatjes van de Vorm ](/help/forms/using-themes-in-core-components.md).
* [ de Reeks van de Kern van de Server Component gebaseerde Aangepaste vertegenwoordiging van de Vorm JSON aan kanalen zoals mobiel, Web, inheemse apps, en de diensten die de hoofdloze vertegenwoordiging van een vorm ](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html) vereisen.

### Hoe weet ik of ik Adaptive Forms Core Components handmatig moet inschakelen? {#manual-enablement-needed-faq}

De meeste klanten beschikken al over Adaptive Forms Core Components. U hoeft deze alleen handmatig in te schakelen als:

1. U hebt een ouder Forms as a Cloud Service-programma gemaakt voordat Core Components automatisch werd opgenomen
1. De verificatiecontrole in de [ Controle als de Aangepaste Componenten van de Kern van Forms ](#check-if-enabled) worden toegelaten bevestigt dat de vereiste gebiedsdelen van uw bewaarplaats missen

Als u onzeker bent, volg de verificatiestappen in [ Controle als de Aangepaste Componenten van de Kern van Forms ](#check-if-enabled) hierboven worden toegelaten sectie.

### Waarom worden formulieren op basis van kerncomponenten niet weergegeven in een project?

De op componenten-gebaseerde vormen van de kern kunnen niet teruggeven wegens een versiewanverhouding tussen het pakket van de Componenten van de Forms Core en de versie inbegrepen in het project archetype. Dit probleem doet zich doorgaans voor wanneer de versie die in het projectarchetype is opgegeven, gelijk is aan of hoger is dan de versie die in het Forms Core Components-pakket is opgenomen. Voer een van de volgende handelingen uit om dit probleem op te lossen:

* Gebruik een lagere versie van het pakket van de Componenten van de Kern van Forms in het projectarchetype.
* Verwijder de Forms Core Components-afhankelijkheid van het architectuurtype van het project, aangezien de vereiste versie al is opgenomen in AEM as a Cloud Service. Het Forms Core Components-pakket wordt vanaf release 2013 gebundeld met AEM als een Cloud SDK, bijvoorbeeld `AEM SDK v2025.3.20133.20250325T063357Z-250300` .

>[!MORELIKETHIS]
>
>* [ creeer een Aangepast Vorm ](/help/forms/creating-adaptive-form-core-components.md)
