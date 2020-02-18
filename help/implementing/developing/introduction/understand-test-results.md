---
title: Lees uw testresultaten - Cloud Services
description: Testresultaten begrijpen - Cloud Services
translation-type: tm+mt
source-git-commit: e1504c73e443d449f8fc9d5fbad433ea1a298843

---


# De testresultaten begrijpen {#understand-test-results}

Cloud Manager for Cloud Services-pijplijnuitvoeringen ondersteunen de uitvoering van tests die worden uitgevoerd tegen de werkgebiedomgeving. Dit is in tegenstelling tot tests die tijdens de het Testen stap van de Bouwstijl en van de Eenheid worden uitgevoerd die offline, zonder toegang tot om het even welke lopende milieu AEM in werking worden gesteld.
Er zijn twee soorten tests in deze context die worden uitgevoerd:
* Door de klant geschreven tests
* Door Adobe geschreven tests

Beide soorten tests worden in een containerinfrastructuur in werking gesteld die voor het runnen van deze types van tests wordt ontworpen.


## Testen van de codekwaliteit {#code-quality-testing}

Als deel van de pijpleiding wordt de broncode gescand om ervoor te zorgen dat de plaatsingen aan bepaalde kwaliteitscriteria voldoen. Momenteel wordt dit geïmplementeerd door een combinatie van SonarQube en inhoudspakketonderzoek met gebruik van OakPAL. Er zijn meer dan 100 regels die generieke Java-regels en AEM-specifieke regels combineren. In de volgende tabel wordt de classificatie voor testcriteria samengevat:

| Naam | Definitie | Categorie | Drempel voor fout |
|--- |--- |--- |--- |
| Beveiligingsbeoordeling | A = 0 Kwetsbaarheid <br/>B = ten minste 1 Kleine Kwetsbaarheid<br/> C = ten minste 1 Ernstige Kwetsbaarheid <br/>D = ten minste 1 Kritieke Kwetsbaarheid <br/>E = ten minste 1 Kwetsbaarheid |  Kritiek | &lt; B |
| Betrouwbaarheidsbeoordeling | A = 0 Bug <br/>B = ten minste 1 kleine bug <br/>C = ten minste 1 groot probleem <br/>D = ten minste 1 kritisch probleem E = ten minste 1 blokkeerprobleem | Belangrijk | &lt; C |
| Onderhoudsverklaring | Uitstaande herstelkosten voor codegeuren zijn: <br/><ul><li>&lt;=5% van de tijd die al in de toepassing is ingegaan, is de rating A </li><li>tussen 6 en 10% is de rating een B </li><li>tussen 11 en 20% is de rating een C </li><li>tussen 21 en 50% is de rating een D</li><li>iets meer dan 50% is een E</li></ul> | Belangrijk | &lt; A |
| Dekking | Een combinatie van de dekking van de meetlijn en de toestand volgens deze formule: <br/>`Coverage = (CT + CF + LC)/(2*B + EL)` <br/>waarbij: CT = voorwaarden die ten minste één keer zijn geëvalueerd op &#39;true&#39; tijdens het uitvoeren van eenheidstests <br/>CF = voorwaarden die ten minste één keer zijn geëvalueerd op &#39;false&#39; tijdens het uitvoeren van eenheidstests <br/>LC = gedekte lijnen = lines_to_cover - uncoverlines <br/><br/> B = totaal aantal voorwaarden <br/>EL = totaal aantal uitvoerbare lijnen (lines_to_cover) | Belangrijk | &lt; 50% |
| Overgeslagen eenheidstests | Aantal overgeslagen eenheidstests. | Info | > 1 |
| Problemen openen | Algemene uitgiftypen - Vulnerabilities, Bugs en Codefragmenten | Info | > 1 |
| Gedupliceerde lijnen | Aantal lijnen betrokken bij gedupliceerde blokken. <br/>Een codeblok dat als gedupliceerd moet worden beschouwd: <br/><ul><li>**Niet-Java-projecten:**</li><li>Er moeten ten minste 100 opeenvolgende en gedupliceerde tokens zijn.</li><li>Deze tokens moeten ten minste op: </li><li>30 regels code voor COBOL </li><li>20 coderegels voor ABAP </li><li>10 coderegels voor andere talen</li><li>**Java-projecten:**</li><li> Er moeten minstens tien opeenvolgende en gedupliceerde verklaringen zijn, ongeacht het aantal tokens en lijnen.</li></ul> <br/>Verschillen in inspringing en in letterlijke tekenreeksen worden genegeerd bij het detecteren van duplicaten. | Info | > 1% |


>[!NOTE]
>
>Zie [Metrische definities](https://docs.sonarqube.org/display/SONAR/Metric+Definitions) voor meer gedetailleerde definities.

U kunt de lijst met regels hier downloaden [code-quality-rules.xlsx](/help/implementing/cloud-manager/assets/CodeQuality-Rules-new-one.xlsx)

>[!NOTE]
>
>Voor meer informatie over de regels voor de kwaliteit van aangepaste code die worden uitgevoerd door [!UICONTROL Cloud Manager], raadpleegt u [Aangepaste regels](/help/implementing/cloud-manager/custom-code-quality-rules.md)voor codekwaliteit.

### Werken met valse positieven {#dealing-with-false-positives}

Het kwaliteitscontroleproces is niet perfect en zal soms ten onrechte problemen identificeren die eigenlijk niet problematisch zijn. Dit wordt een &quot;vals-positief&quot; genoemd.

In deze gevallen kan de broncode worden geannoteerd met de standaard-Java- `@SuppressWarnings` annotatie die de regel-id opgeeft als het annotatiekenmerk. Een veelvoorkomend probleem is bijvoorbeeld dat de SonarQube-regel voor het detecteren van gecodeerde wachtwoorden agressief kan zijn ten aanzien van de manier waarop een gecodeerd wachtwoord wordt geïdentificeerd.

Om naar een specifiek voorbeeld te kijken, zou deze code vrij gemeenschappelijk in een project zijn AEM dat code heeft om met één of andere externe dienst te verbinden:

```java
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

SonarQube verhoogt vervolgens de kwetsbaarheid van de blokker. Na het herzien van de code, identificeert u dat dit geen kwetsbaarheid is en kan dit met aangewezen regel identiteitskaart annoteren

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

Maar als de code eigenlijk dit was:

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String PROP_SERVICE_PASSWORD = "password";
```

Dan is de correcte oplossing het hardcoded wachtwoord te verwijderen.

>[!NOTE]
>
>Het is weliswaar aan te raden de `@SuppressWarnings` annotatie zo specifiek mogelijk te maken, d.w.z. alleen de specifieke instructie of het specifieke blok dat de uitgave veroorzaakt, aan te brengen, maar het is wel mogelijk om een annotatie op klasseniveau te maken.

## Functionele tests schrijven {#writing-functional-tests}

Door de klant geschreven functionele tests moeten worden verpakt als een afzonderlijk JAR-bestand dat door dezelfde Maven-build wordt geproduceerd als de artefacten die op AEM moeten worden geïmplementeerd. Over het algemeen zou dit een afzonderlijke module Maven zijn. Het resulterende JAR dossier moet alle vereiste gebiedsdelen bevatten en zou over het algemeen worden gecreeerd gebruikend de getelegrafeerde assemblage-stop gebruikend jar-met-gebiedsdelen beschrijver.

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

Een klasse met de naam `com.myco.tests.aem.ExampleIT` zou bijvoorbeeld worden uitgevoerd, maar een klasse met de naam `com.myco.tests.aem.ExampleTest` niet.

De testklassen moeten normale JUnit-tests zijn. De testinfrastructuur is ontworpen en geconfigureerd om compatibel te zijn met de conventies die worden gebruikt door de testbibliotheek aem-testing-clients. Ontwikkelaars worden ten zeerste aangeraden deze bibliotheek te gebruiken en de best practices ervan te volgen. Raadpleeg [Git Link](https://github.com/adobe/aem-testing-clients) voor meer informatie.

## Aangepaste functionele tests {#custom-functional-test}

De het testen van de Functie van de Douane stap in de pijpleiding is altijd aanwezig en kan niet worden overgeslagen.

Als er echter geen test-JAR wordt geproduceerd door de constructie, slaagt de test standaard. Deze stap wordt onmiddellijk na de implementatie van het werkgebied uitgevoerd.

>[!NOTE]
>Met de knop Logboek **** downloaden hebt u toegang tot een ZIP-bestand met de logbestanden voor de gedetailleerde versie van de testuitvoering. Deze logboeken bevatten niet de logboeken van het werkelijke AEM-runtimeproces. Deze logboeken zijn toegankelijk via de standaardfunctionaliteit voor downloaden of staaflogbestanden. Raadpleeg [Logboeken](/help/implementing/cloud-manager/manage-logs.md) openen en beheren voor meer informatie.

## Uitvoering lokale test {#local-test-execution}

Aangezien de testklassen tests JUnit zijn, kunnen zij van mainstream Java IDEs zoals Eclipse, IntelliJ, NetBeans, etc. worden in werking gesteld.

Wanneer deze tests echter noodzakelijkerwijs worden uitgevoerd, moet een verscheidenheid aan systeemeigenschappen worden ingesteld die door de aem-testing-clients (en de onderliggende Sling Testing Clients) worden verwacht.

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