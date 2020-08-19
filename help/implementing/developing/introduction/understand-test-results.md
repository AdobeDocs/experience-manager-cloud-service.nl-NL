---
title: De testresultaten begrijpen - Cloud Services
description: Testresultaten begrijpen - Cloud Services
translation-type: tm+mt
source-git-commit: 6eee78f2883b15f793662dc1474b7b7874903702
workflow-type: tm+mt
source-wordcount: '1698'
ht-degree: 3%

---


# Inzicht in de testresultaten {#understand-test-results}

Cloud Manager for Cloud Services-pipeline-uitvoeringen ondersteunen de uitvoering van tests die worden uitgevoerd voor de stagingomgeving. Dit is in tegenstelling tot tests die tijdens de het Testen stap van de Bouwstijl en van de Eenheid worden in werking gesteld die offline, zonder toegang tot om het even welke lopende AEM milieu in werking worden gesteld.

Er zijn drie brede testcategorieën die worden ondersteund door Cloud Manager for Cloud Services Pipeline:

1. [Testen van de codekwaliteit](#code-quality-testing)
1. [Functionele tests](#functional-testing)
1. [Testen van content-controle](#content-audit-testing)

Deze tests kunnen:

* Door de klant geschreven
* met Adobe geschreven
* Open source tool (aangedreven door Lighthouse van Google)

   >[!NOTE]
   > Zowel door de klant geschreven tests als Adobe geschreven tests worden uitgevoerd in een containerinfrastructuur die is ontworpen voor het uitvoeren van deze tests.


## Testen van de codekwaliteit {#code-quality-testing}

Deze stap evalueert de kwaliteit van uw toepassingscode. Het is de kerndoelstelling van een code-Kwaliteit enige pijpleiding en wordt uitgevoerd onmiddellijk na de bouwstap in alle niet-productie en productiepijpleidingen.

Verwijs naar het [Vormen van uw CI-CD Pijpleiding](/help/implementing/cloud-manager/configure-pipeline.md) om meer over verschillende types van pijpleidingen te leren.

In het Testen van de Kwaliteit van de Code, wordt de broncode gescand om ervoor te zorgen dat het plaatsingen aan bepaalde kwaliteitscriteria voldoet. Momenteel wordt dit geïmplementeerd door een combinatie van SonarQube en inhoudspakketonderzoek met gebruik van OakPAL. Er zijn meer dan 100 regels die generieke Java-regels en AEM-specifieke regels combineren. Enkele AEM-specifieke regels worden gecreeerd gebaseerd op beste praktijken van AEM Techniek en worden bedoeld als Regels [van de Kwaliteit van de](/help/implementing/cloud-manager/custom-code-quality-rules.md)Code van de Douane.

De resultaten van deze stap worden geleverd als *Classificatie*. De onderstaande tabel geeft een overzicht van de scores voor verschillende testcriteria:

| Naam | Definitie | Categorie | Drempel voor fout |
|--- |--- |--- |--- |
| Beveiligingsbeoordeling | A = 0 Kwetsbaarheid <br/>B = ten minste 1 Kleine Kwetsbaarheid<br/> C = ten minste 1 Ernstige Kwetsbaarheid <br/>D = ten minste 1 Kritieke Kwetsbaarheid <br/>E = ten minste 1 Kwetsbaarheid | Kritiek | &lt; B |
| Betrouwbaarheidsbeoordeling | A = 0 Bug <br/>B = ten minste 1 kleine bug <br/>C = ten minste 1 groot probleem <br/>D = ten minste 1 kritisch probleem E = ten minste 1 blokkeerprobleem | Belangrijk | &lt; C |
| Onderhoudsverklaring | Uitstaande herstelkosten voor codegeuren zijn: <br/><ul><li>&lt;=5% van de tijd die al in de toepassing is ingegaan, is de rating A </li><li>tussen 6 en 10% is de rating een B </li><li>tussen 11 en 20% is de rating een C </li><li>tussen 21 en 50% is de rating een D</li><li>iets meer dan 50% is een E</li></ul> | Belangrijk | &lt; A |
| Dekking | Een combinatie van de dekking van de meetlijn en de toestand volgens deze formule: <br/>`Coverage = (CT + CF + LC)/(2*B + EL)`  <br/>waarbij: CT = voorwaarden die ten minste één keer zijn geëvalueerd op &#39;true&#39; tijdens het uitvoeren van eenheidstests <br/>CF = voorwaarden die ten minste één keer zijn geëvalueerd op &#39;false&#39; tijdens het uitvoeren van eenheidstests <br/>LC = gedekte lijnen = lines_to_cover - uncoverlines <br/><br/> B = totaal aantal voorwaarden <br/>EL = totaal aantal uitvoerbare lijnen (lines_to_cover) | Belangrijk | &lt; 50% |
| Overgeslagen eenheidstests | Aantal overgeslagen eenheidstests. | Info | > 1 |
| Problemen openen | Algemene uitgiftypen - Vulnerabilities, Bugs en Codefragmenten | Info | > 0 |
| Gedupliceerde lijnen | Aantal lijnen betrokken bij gedupliceerde blokken. <br/>Een codeblok dat als gedupliceerd moet worden beschouwd: <br/><ul><li>**Niet-Java-projecten:**</li><li>Er moeten ten minste 100 opeenvolgende en gedupliceerde tokens zijn.</li><li>Deze tokens moeten ten minste op: </li><li>30 regels code voor COBOL </li><li>20 coderegels voor ABAP </li><li>10 coderegels voor andere talen</li><li>**Java-projecten:**</li><li> Er moeten minstens tien opeenvolgende en gedupliceerde verklaringen zijn, ongeacht het aantal tokens en lijnen.</li></ul> <br/>Verschillen in inspringing en in letterlijke tekenreeksen worden genegeerd bij het detecteren van duplicaten. | Info | > 1% |
| Compatibiliteit met Cloud Service | Aantal geïdentificeerde kwesties van de Verenigbaarheid van de Cloud Service. | Info | > 0 |


U kunt de lijst met regels hier downloaden [code-quality-rules.xlsx](/help/implementing/cloud-manager/assets/CodeQuality-rules-latest.xlsx)

>[!NOTE]
>
>Zie [Metrische definities](https://docs.sonarqube.org/display/SONAR/Metric+Definitions) voor meer gedetailleerde definities.


>[!NOTE]
>
>Voor meer informatie over de regels voor de kwaliteit van aangepaste code die worden uitgevoerd door [!UICONTROL Cloud Manager], raadpleegt u [Aangepaste regels](/help/implementing/cloud-manager/custom-code-quality-rules.md)voor codekwaliteit.

### Werken met valse positieven {#dealing-with-false-positives}

Het kwaliteitscontroleproces is niet perfect en zal soms ten onrechte problemen identificeren die eigenlijk niet problematisch zijn. Dit wordt een &quot;vals-positief&quot; genoemd.

In deze gevallen kan de broncode worden geannoteerd met de standaard-Java- `@SuppressWarnings` annotatie die de regel-id opgeeft als het annotatiekenmerk. Een veelvoorkomend probleem is bijvoorbeeld dat de SonarQube-regel voor het detecteren van gecodeerde wachtwoorden agressief kan zijn ten aanzien van de manier waarop een gecodeerd wachtwoord wordt geïdentificeerd.

Om naar een specifiek voorbeeld te kijken, zou deze code vrij gemeenschappelijk in een AEM project zijn dat code heeft om met één of andere externe dienst te verbinden:

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

>[!NOTE]
>Terwijl er geen expliciete het Testen van de Veiligheid stap is, zijn er nog veiligheid-verwante code kwaliteitsregels die tijdens de stap van de codekwaliteit worden geëvalueerd. Verwijs naar het Overzicht van de [Veiligheid voor AEM als Cloud Service](/help/security/cloud-service-security-overview.md) om meer over veiligheid in Cloud Service te leren.

## Functionele tests {#functional-testing}

Functionele tests worden gecategoriseerd in twee typen:

* Functioneel testen van producten
* Aangepaste functionele tests

### Functioneel testen van producten {#product-functional-testing}

De Functionele Tests van het product zijn een reeks stabiele HTTP integratietests (ITs) rond kernfunctionaliteit in AEM (bijvoorbeeld, creatie en replicatie) die klantenveranderingen in hun toepassingscode verhinderen worden opgesteld als het deze kernfunctionaliteit breekt.

Functionele tests van het product worden automatisch uitgevoerd wanneer een klant nieuwe code naar Cloud Manager implementeert en kunnen niet worden overgeslagen.

Zie Functionele [producttests](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) voor steekproeftests.

### Aangepaste functionele tests {#custom-functional-testing}

De het testen van de Functie van de Douane stap in de pijpleiding is altijd aanwezig en kan niet worden overgeslagen.

Als er echter geen test-JAR wordt geproduceerd door de constructie, slaagt de test standaard.

>[!NOTE]
>Met de knop **Logboek downloaden** hebt u toegang tot een ZIP-bestand met de logboekbestanden voor de gedetailleerde versie van de testuitvoering. Deze logboeken bevatten niet de logboeken van het werkelijke AEM runtimeproces. Deze kunnen worden geopend met de standaardfunctionaliteit voor downloaden of staaflogbestanden. Raadpleeg [Toegang tot en beheer van logbestanden](/help/implementing/cloud-manager/manage-logs.md) voor meer informatie.


#### Functionele tests schrijven {#writing-functional-tests}

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

Een klasse met de naam `com.myco.tests.aem.ExampleIT` zou bijvoorbeeld worden uitgevoerd, maar een klasse met de naam `com.myco.tests.aem.ExampleTest` niet.

De testklassen moeten normale JUnit-tests zijn. De testinfrastructuur is ontworpen en geconfigureerd om compatibel te zijn met de conventies die worden gebruikt door de testbibliotheek aem-testing-clients. Ontwikkelaars worden ten zeerste aangeraden deze bibliotheek te gebruiken en de best practices ervan te volgen. Raadpleeg [Git Link](https://github.com/adobe/aem-testing-clients) voor meer informatie.

## Testen van content-controle {#content-audit-testing}

Content Audit is een functie die beschikbaar is in de productiepijplijnen van Cloud Manager voor sites die worden aangedreven door Lighthouse, een opensource-programma van Google. Deze functie is ingeschakeld in alle productiepijpleidingen van Cloud Manager.

Het valideert het plaatsingsproces en de hulp zorgt ervoor dat de ingevoerde veranderingen:

1. Voldoe aan basislijnnormen voor prestaties, toegankelijkheid, beste praktijken, SEO (de Optimalisering van de Motor van het Onderzoek), en PWA (de Progressieve App van het Web).

1. Neem geen regressies op in deze afmetingen.

De controle van de inhoud in de Manager van de Wolk zorgt ervoor dat de digitale ervaring van eindgebruikers op de plaats aan de hoogste normen kan worden gehandhaafd. De resultaten zijn informatief en stellen de gebruiker in staat de scores en de wijziging tussen de huidige en vorige scores te bekijken. Dit inzicht is waardevol om te bepalen als er een regressie is die met de huidige plaatsing zal worden geïntroduceerd.

### Resultaten van controle van inhoud {#understanding-content-audit-results}

De Controle van de inhoud verstrekt geaggregeerde en gedetailleerde op paginaniveau testresultaten via de de uitvoeringspagina van de Pijl van de Productie.

* De cijfers op het niveau van het samengevoegde niveau meten de gemiddelde score over de pagina&#39;s die werden gecontroleerd.
* Afzonderlijke scores op paginaniveau zijn ook beschikbaar via de neerwaartse boor.
* Er zijn details van de scores beschikbaar om te zien wat de resultaten zijn van de afzonderlijke tests, samen met aanwijzingen voor het verhelpen van problemen die tijdens de inhoudscontrole zijn vastgesteld.
* Een geschiedenis van de testresultaten wordt voortgeduurd binnen de Manager van de Wolk zodat kunnen de klanten zien of de veranderingen die in de pijpleidingslooppas worden geïntroduceerd om het even welke regressies van de vorige looppas omvatten.

#### Samengevoegde scores {#aggregate-scores}

Voor elk type test (prestaties, toegankelijkheid, SEO, aanbevolen methoden en PWA) is een score voor het geaggregeerde niveau beschikbaar.

De score voor het geaggregeerde niveau is gebaseerd op de gemiddelde score van de pagina&#39;s die in de run zijn opgenomen. De verandering op het gezamenlijke niveau vertegenwoordigt de gemiddelde score van de pagina&#39;s in de huidige looppas in vergelijking met het gemiddelde van de scores van de vorige looppas, zelfs als de inzameling van pagina&#39;s die om worden gevormd om zijn omvat tussen looppas is veranderd.

De waarde van de metrische waarde van de Verandering kan één van het volgende zijn:

* **Positieve waarde** : de pagina(&#39;s) zijn verbeterd op de geselecteerde test sinds de laatste productiepijpleiding

* **Negatieve waarde** : de pagina(&#39;s) zijn tijdens de geselecteerde test opnieuw geperst sinds de laatste productiepijpleiding

* **Geen wijziging** - de pagina(&#39;s) hebben dezelfde score behaald sinds de laatste productiepijpleiding

* **N.v.t** . - er was geen vorige score beschikbaar om te vergelijken

   ![](assets/content-audit-test1.png)

#### Scores op paginaniveau {#page-level-scores}

Door in een van de tests te boren, kunt u een gedetailleerdere score op paginaniveau zien. De gebruiker zal kunnen zien hoe de individuele pagina&#39;s voor de specifieke test samen met de verandering van de vorige tijd de test in werking werden gesteld.

Als u op de details van een afzonderlijke pagina klikt, krijgt u informatie over de elementen van de pagina die zijn geëvalueerd, en kunt u aangeven welke problemen u kunt oplossen als er mogelijkheden voor verbetering zijn gevonden. De details van de tests en de bijbehorende richtsnoeren worden verstrekt door Google Lighthouse.

![](assets/page-level-scores.png)

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

