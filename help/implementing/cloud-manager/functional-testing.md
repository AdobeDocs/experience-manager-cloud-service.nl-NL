---
title: Functionele tests - Cloud Services
description: Functionele tests - Cloud Services
exl-id: 7eb50225-e638-4c05-a755-4647a00d8357
source-git-commit: 778fa187df675eada645c73911e6f02e8a112753
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 3%

---

# Functionele tests {#functional-testing}


>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_functionaltesting"
>title="Functionele tests"
>abstract="Functionele tests worden ingedeeld in drie typen: Functionele tests voor producten, aangepaste functionele tests en aangepaste UI-tests"

Functionele tests worden ingedeeld in drie typen:


* Functioneel testen van producten
* Aangepaste functionele tests
* Aangepaste UI-tests

## Functioneel testen van producten {#product-functional-testing}

De Functionele Tests van het product zijn een reeks stabiele HTTP integratietests (ITs) rond kernfunctionaliteit in AEM (bijvoorbeeld, creatie en replicatie) die klantenveranderingen in hun toepassingscode verhinderen worden opgesteld als het deze kernfunctionaliteit breekt.

Functionele tests van het product worden automatisch uitgevoerd wanneer een klant nieuwe code naar Cloud Manager implementeert en kunnen niet worden overgeslagen.

Zie [Productfunctionele tests](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) voor monstertests.

## Aangepaste functionele tests {#custom-functional-testing}

De het testen van de Functie van de Douane stap in de pijpleiding is altijd aanwezig en kan niet worden overgeslagen.

De bouw moet of nul of één test JARs produceren. Als er nultestJAR&#39;s worden geproduceerd, gaat de teststap standaard over. Als de build meerdere testJAR&#39;s produceert, is de geselecteerde JAR niet deterministisch.

>[!NOTE]
>Met de knop **Logboek downloaden** hebt u toegang tot een ZIP-bestand met de logboekbestanden voor de gedetailleerde versie van de testuitvoering. Deze logboeken bevatten niet de logboeken van het werkelijke AEM runtimeproces. Deze kunnen worden geopend met de standaardfunctionaliteit voor downloaden of staaflogbestanden. Zie [Logbestanden openen en beheren](/help/implementing/cloud-manager/manage-logs.md) voor meer informatie .


## Functionele tests schrijven {#writing-functional-tests}

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

Binnen dit JAR-bestand moeten de klassenamen van de werkelijke uit te voeren tests eindigen in `IT`.

Een klasse met de naam `com.myco.tests.aem.it.ExampleIT` zou worden uitgevoerd, maar een klasse met de naam `com.myco.tests.aem.it.ExampleTest` niet.

Bovendien moet de testcode onder een pakket met de naam `it` (Het filter voor uitsluitingen van dekking is `**/it/**/*.java`).

De testklassen moeten normale JUnit-tests zijn. De testinfrastructuur is ontworpen en geconfigureerd om compatibel te zijn met de conventies die worden gebruikt door de testbibliotheek aem-testing-clients. Ontwikkelaars worden ten zeerste aangeraden deze bibliotheek te gebruiken en de best practices ervan te volgen. Zie [Git Link](https://github.com/adobe/aem-testing-clients) voor meer informatie .

## Uitvoering lokale test {#local-test-execution}

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
