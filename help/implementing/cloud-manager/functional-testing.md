---
title: Functionele tests - Cloud Services
description: Functionele tests - Cloud Services
translation-type: tm+mt
source-git-commit: dc006d50d703a17a84e3dc6631bc423f5de37f88
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 4%

---


# Functioneel testen {#functional-testing}

Functionele tests worden gecategoriseerd in twee typen:

* Functioneel testen van producten
* Aangepaste functionele tests

## Functioneel testen van product {#product-functional-testing}

De Functionele Tests van het product zijn een reeks stabiele HTTP integratietests (ITs) rond kernfunctionaliteit in AEM (bijvoorbeeld, creatie en replicatie) die klantenveranderingen in hun toepassingscode verhinderen worden opgesteld als het deze kernfunctionaliteit breekt.

Functionele tests van het product worden automatisch uitgevoerd wanneer een klant nieuwe code naar Cloud Manager implementeert en kunnen niet worden overgeslagen.

Zie [Productfunctionele tests](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) voor steekproeftests.

## Aangepaste functionele tests {#custom-functional-testing}

De het testen van de Functie van de Douane stap in de pijpleiding is altijd aanwezig en kan niet worden overgeslagen.

Als er echter geen test-JAR wordt geproduceerd door de constructie, slaagt de test standaard.

>[!NOTE]
>Met de knop **Logboek downloaden** hebt u toegang tot een ZIP-bestand met de logboekbestanden voor de gedetailleerde versie van de testuitvoering. Deze logboeken bevatten niet de logboeken van het werkelijke AEM runtimeproces. Deze kunnen worden geopend met de standaardfunctionaliteit voor downloaden of staaflogbestanden. Raadpleeg [Toegang tot en beheer van logbestanden](/help/implementing/cloud-manager/manage-logs.md) voor meer informatie.


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

