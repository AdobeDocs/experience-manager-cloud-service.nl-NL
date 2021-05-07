---
title: Functionele tests - Cloud Services
description: Functionele tests - Cloud Services
exl-id: 7eb50225-e638-4c05-a755-4647a00d8357
translation-type: tm+mt
source-git-commit: f6c700f82bc5a1a3edf05911a29a6e4d32dd3f72
workflow-type: tm+mt
source-wordcount: '865'
ht-degree: 2%

---

# Functioneel testen {#functional-testing}


>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_functionaltesting"
>title="Functionele tests"
>abstract="Functionele tests zijn onderverdeeld in drie typen:Functionele tests van product, Aangepaste functionele tests, Aangepaste UI-tests"

Functionele tests worden ingedeeld in drie typen:


* Functioneel testen van producten
* Aangepaste functionele tests
* Aangepaste UI-tests

## Functioneel testen van product {#product-functional-testing}

De Functionele Tests van het product zijn een reeks stabiele HTTP integratietests (ITs) rond kernfunctionaliteit in AEM (bijvoorbeeld, creatie en replicatie) die klantenveranderingen in hun toepassingscode verhinderen worden opgesteld als het deze kernfunctionaliteit breekt.

Functionele tests van het product worden automatisch uitgevoerd wanneer een klant nieuwe code naar Cloud Manager implementeert en kunnen niet worden overgeslagen.

Zie [Productfunctionele tests](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) voor steekproeftests.

## Aangepaste functionele tests {#custom-functional-testing}

De het testen van de Functie van de Douane stap in de pijpleiding is altijd aanwezig en kan niet worden overgeslagen.

Als er echter geen test-JAR wordt geproduceerd door de constructie, slaagt de test standaard.

>[!NOTE]
>Met de knop **Logboek downloaden** hebt u toegang tot een ZIP-bestand met de logboekbestanden voor de gedetailleerde versie van de testuitvoering. Deze logboeken bevatten niet de logboeken van het werkelijke AEM runtimeproces. Deze kunnen worden geopend met de standaardfunctionaliteit voor downloaden of staaflogbestanden. Raadpleeg [Toegang tot en beheer van logbestanden](/help/implementing/cloud-manager/manage-logs.md) voor meer informatie.

## Aangepaste UI-tests {#custom-ui-testing}

AEM biedt zijn klanten een geïntegreerde suite met Cloud Manager-kwaliteitspoorten om ervoor te zorgen dat hun toepassingen probleemloos worden bijgewerkt. Met name kunnen klanten met behulp van IT-testpoorten al hun eigen tests maken en automatiseren die gebruikmaken van AEM API&#39;s.

De functie Aangepaste UI-tests is een optionele functie [Klantenkeuze-in](#customer-opt-in) waarmee onze klanten interfacetests voor hun toepassingen kunnen maken en automatisch kunnen uitvoeren. De tests UI zijn op selenium-Gebaseerde tests die in een beeld van de Docker worden verpakt om een brede keus in taal en kaders (zoals Java en Maven, Node en WebDriver.io, of om het even welk ander kader en technologie toe te staan die op Selenium worden voortgebouwd). U kunt meer over leren hoe te om UI te bouwen en tests UI van hier te schrijven. Bovendien kan een project van de Tests UI gemakkelijk worden geproduceerd door het AEM Project Archetype te gebruiken.

De klanten kunnen (via GIT) douanetests en testreeks voor UI tot stand brengen. De UI-test wordt uitgevoerd als onderdeel van een specifieke kwaliteitspoort voor elke Cloud Manager-pijplijn met hun specifieke stap en feedbackinformatie. Om het even welke tests van de UI met inbegrip van regressie en nieuwe functionaliteiten, zullen fouten om toelaten worden ontdekt en worden gemeld binnen de klantencontext.

De tests van de UI van de Klant lopen automatisch op de pijpleiding van de Productie onder de &quot;Testen van de UI van de Douane&quot;stap.

In tegenstelling tot Aangepaste functionele tests die HTTP-tests zijn die in Java zijn geschreven, kunnen de UI-tests een dockerafbeelding zijn met tests die in elke taal zijn geschreven, mits deze tests de conventies volgen die bij [UI-tests maken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/test-results/ui-testing.html?lang=en#building-ui-tests) zijn gedefinieerd.

>[!NOTE]
>Het wordt aanbevolen de structuur en de taal *(js en audio)* te volgen die gemakkelijk in [AEM Project Archetype](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/ui.tests) als uitgangspunt worden verstrekt.

### Klanten kiezen {#customer-opt-in}

Om hun tests UI te laten bouwen en worden uitgevoerd, moeten de klanten &quot;opt-in&quot;door een dossier aan hun codebewaarplaats toe te voegen, onder de bepaalde sub-module voor tests UI (naast het pom.xml- dossier van UI test submodule) en ervoor te zorgen dat dit dossier bij de wortel van het gebouwde `tar.gz` dossier is.

*Bestandsnaam*: `testing.properties`

*Inhoud*:  `one line: ui-tests.version=1`

Als dit niet in het gebouwde `tar.gz` dossier is, zullen de tests UI bouwen en de uitvoeringen worden overgeslagen

>[!NOTE]
>Productiepijpleidingen die vóór 10 februari 2021 zijn aangelegd, moeten worden bijgewerkt om de in dit punt beschreven interfacetests te kunnen gebruiken. Dit betekent hoofdzakelijk de Gebruiker de pijpleiding van de Productie moet uitgeven en **sparen** van UI klikken zelfs als geen veranderingen werden aangebracht.
>Verwijs naar [Het vormen van uw CI-CD Pijpleiding](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html?lang=en#using-cloud-manager) om meer over pijpleidingsconfiguratie te leren.

### Het schrijven van functionele tests {#writing-functional-tests}

Door de klant geschreven functionele tests moeten worden verpakt als een afzonderlijk JAR-bestand dat wordt geproduceerd door dezelfde Maven-build als de artefacten die moeten worden geïmplementeerd op AEM. Over het algemeen zou dit een afzonderlijke module Maven zijn. Het resulterende JAR dossier moet alle vereiste gebiedsdelen bevatten en zou over het algemeen worden gecreeerd gebruikend de getelegrafeerde assemblage-stop gebruikend jar-met-gebiedsdelen beschrijver.

Bovendien moet de JAR de Cloud-Manager-TestType manifestkopbal hebben die aan integratie-test wordt geplaatst. In de toekomst wordt verwacht dat extra headerwaarden worden ondersteund. Een voorbeeldconfiguratie voor maven-assemblage-stop is:

```java
<build>
    <plugins>
        <!-- Create self-contained jar with dependencies -->
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-assembly-plugin</artifactId>
            <version>3.1.0</version>
            <configuration>
                <descriptorRefs>
                    <descriptorRef>jar-with-dependencies</descriptorRef>
                </descriptorRefs>
                <archive>
                    <manifestEntries>
                        <Cloud-Manager-TestType>integration-test</Cloud-Manager-TestType>
                    </manifestEntries>
                </archive>
            </configuration>
            <executions>
                <execution>
                    <id>make-assembly</id>
                    <phase>package</phase>
                    <goals>
                        <goal>single</goal>
                    </goals>
                </execution>
            </executions>
        </plugin>
    </plugins>
```

In dit JAR-bestand moeten de klassenamen van de eigenlijke tests die uitgevoerd moeten worden, eindigen in de IT.

Een klasse met de naam `com.myco.tests.aem.ExampleIT` wordt bijvoorbeeld uitgevoerd, maar een klasse met de naam `com.myco.tests.aem.ExampleTest` niet.

De testklassen moeten normale JUnit-tests zijn. De testinfrastructuur is ontworpen en geconfigureerd om compatibel te zijn met de conventies die worden gebruikt door de testbibliotheek aem-testing-clients. Ontwikkelaars worden ten zeerste aangeraden deze bibliotheek te gebruiken en de best practices ervan te volgen. Raadpleeg [Koppeling magnetisch](https://github.com/adobe/aem-testing-clients) voor meer informatie.

### Uitvoering lokale test {#local-test-execution}

Aangezien de testklassen tests JUnit zijn, kunnen zij van mainstream Java IDEs zoals Eclipse, IntelliJ, NetBeans, etc. worden in werking gesteld.

Wanneer u deze tests uitvoert, moet u echter een aantal verschillende systeemeigenschappen instellen die door de em-testclients (en de onderliggende testclients voor verkopers) worden verwacht.

De systeemeigenschappen zijn als volgt:

* `sling.it.instances - should be set to 2`
* `sling.it.instance.url.1 - should be set to the author URL, for example, http://localhost:4502`
* `sling.it.instance.runmode.1 - should be set to author`
* `sling.it.instance.adminUser.1 - should be set to the author admin user, e.g. admin`
* `sling.it.instance.adminPassword.1 - should be set to the author admin password`
* `sling.it.instance.url.2 - should be set to the author URL, for example, http://localhost:4503`
* `sling.it.instance.runmode.2 - should be set to publish`
* `sling.it.instance.adminUser.2 - should be set to the publish admin user, for example, admin`
* `sling.it.instance.adminPassword.2 - should be set to the publish admin password`
