---
title: Testen van de codekwaliteit
description: Leer hoe het testen van de codekwaliteit van pijpleidingen werkt en hoe het de kwaliteit van uw plaatsingen kan verbeteren.
exl-id: e2981be9-fb14-451c-ad1e-97c487e6dc46
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 91a1fb46d4300540eeecf38f7f049a2991513d29
workflow-type: tm+mt
source-wordcount: '1164'
ht-degree: 0%

---

# Codekwaliteitstests {#code-quality-testing}

Leer hoe het testen van de codekwaliteit van pijpleidingen werkt en hoe het de kwaliteit van uw plaatsingen kan verbeteren.

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_codequalitytests"
>title="Codekwaliteitstests"
>abstract="Bij het testen van de codekwaliteit wordt uw toepassingscode geëvalueerd op basis van een set kwaliteitsregels. Het is het primaire doel van een code-kwaliteit slechts pijpleiding en wordt uitgevoerd onmiddellijk na de bouwstap in alle productie en niet-productiepijpleidingen."

## Inleiding {#introduction}

Bij het testen van de codekwaliteit wordt uw toepassingscode geëvalueerd op basis van een set kwaliteitsregels. Het is het primaire doel van een code-kwaliteit slechts pijpleiding en wordt uitgevoerd onmiddellijk na de bouwstap in alle productie en niet-productiepijpleidingen.

Zie [ Vormend Uw CI-CD Pijpleiding ](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) om meer over verschillende soorten pijpleidingen te leren.

## Codekwaliteitsregels {#understanding-code-quality-rules}

Testen van de codekwaliteit scant de broncode om ervoor te zorgen dat deze aan bepaalde kwaliteitscriteria voldoet. Deze stap wordt geïmplementeerd door een combinatie van SonarQube en inhoudspakketonderzoek met OakPAL. Er zijn meer dan 100 regels, die generieke regels van Java en AEM-specifieke regels combineren. Sommige AEM-specifieke regels zijn gebaseerd op beste praktijken van AEM Techniek en zijn gekend als [ de kwaliteitsregels van de douanecode ](/help/implementing/cloud-manager/custom-code-quality-rules.md).

U kunt de huidige volledige lijst van regels [ downloaden gebruikend deze verbinding ](/help/implementing/cloud-manager/assets/CodeQuality-rules-latest-CS.xlsx).

>[!IMPORTANT]
>
>Beginnend Donderdag, 13 Februari, 2025 (Cloud Manager 2025.2.0), gebruikt de Kwaliteit van de Code van Cloud Manager een bijgewerkte versie SonarQube 9.9 en een bijgewerkte lijst van regels die u hier [ kunt downloaden ](/help/implementing/cloud-manager/assets/CodeQuality-rules-latest-CS-2024-12-0.xlsx).

### Waarderingen met drie lagen {#three-tiered-gate}

Kwesties die door code kwaliteitstests worden geïdentificeerd worden toegewezen aan één van drie categorieën.

* **Kritieke** - Kwesties die een directe mislukking van de pijpleiding veroorzaken.

* **Belangrijk** - Kwesties die de pijpleiding veroorzaken om een gepauzeerde staat in te gaan. Een plaatsingsmanager, projectmanager, of bedrijfseigenaar kunnen of de kwesties met voeten treden, toestaand de pijpleiding om te werk te gaan. Alternatief, kunnen zij de kwesties goedkeuren, veroorzakend de pijpleiding om met een mislukking te stoppen.

* **Info** - Kwesties die puur voor informatiedoeleinden worden verstrekt en geen effect op de pijpleidingsuitvoering hebben

>[!NOTE]
>
>In een slechts pijpleiding van de codekwaliteit, kunnen de belangrijke mislukkingen in de gate van de Kwaliteit van de Code niet worden met voeten getreden aangezien de het testen stap van de codekwaliteit de definitieve stap in de pijpleiding is.

### Waarderingen {#ratings}

De resultaten van deze stap worden geleverd als **Waarderingen**.

De volgende tabel geeft een overzicht van de classificaties en foutdrempels voor elk van de kritieke, belangrijke en informatiecategorieën.

| Naam | Definitie | Categorie | Drempel voor fout |
|--- |--- |--- |--- |
| Beveiligingsbeoordeling | A = Geen kwetsbaarheden <br/> B = minstens 1 minder kleine kwetsbaarheid <br/> C = minstens 1 belangrijke kwetsbaarheid <br/> D = minstens 1 kritieke kwetsbaarheid <br/> E = minstens 1 kwetsbaarheid van de blocker | Kritiek | &lt; B |
| Betrouwbaarheidsbeoordeling | A = Geen insecten <br/> B = minstens 1 minder kleine insect <br/> C = minstens 1 belangrijke insect <br/> D = minstens 1 kritieke insect <br> E = minstens 1 blocker insect | Kritiek | &lt; D |
| Onderhoudsverklaring | Gedefinieerd door de openstaande herstelkosten voor code ruikt als een percentage van de tijd dat al naar de toepassing is gegaan <br/><ul><li>A = &lt;=5%</li><li>B = 6-10%</li><li>C = 11-20%</li><li>D = 21-50%</li><li>E = >50%</li></ul> | Belangrijk | &lt; A |
| Dekking | Gedefinieerd door een combinatie van de dekking van de testlijn en de voorwaarde met de volgende formule: <br/>`Coverage = (CT + CF + LC)/(2*B + EL)`  <ul><li>`CT` = Voorwaarden die ten minste één keer als `true` zijn geëvalueerd tijdens het uitvoeren van eenheidstests</li><li>`CF` = Voorwaarden die ten minste één keer als `false` zijn geëvalueerd tijdens het uitvoeren van eenheidstests</li><li>`LC` = Covered lines = lines_to_cover - uncover_lines</li><li>`B` = totaal aantal voorwaarden</li><li>`EL` = totaal aantal uitvoerbare regels (lines_to_cover)</li></ul> | Belangrijk | &lt; 50% |
| Overgeslagen eenheidstests | Aantal overgeslagen eenheidstests | Info | > 1 |
| Problemen openen | Algemene uitgiftypen - Vulnerabilities, Bugs en Codefragmenten | Info | > 0 |
| Gedupliceerde lijnen | Gedefinieerd als het aantal regels dat is betrokken bij gedupliceerde blokken. Een codeblok wordt als gedupliceerd beschouwd onder de volgende omstandigheden.<br> niet-Java Projecten:<ul><li>Er moeten ten minste 100 opeenvolgende en gedupliceerde tokens zijn.</li><li>Deze tokens moeten ten minste worden verspreid over: </li><li>30 regels code voor COBOL </li><li>20 coderegels voor ABAP </li><li>10 coderegels voor andere talen</li></ul>Java-projecten:<ul></li><li> Er moeten minstens tien opeenvolgende en gedupliceerde instructies zijn, ongeacht het aantal tokens en regels.</li></ul>Verschillen in inspringing en in letterlijke tekenreeksen worden genegeerd wanneer duplicaten worden gedetecteerd. | Info | > 1% |
| Compatibiliteit met Cloud Service | Aantal geïdentificeerde compatibiliteitsproblemen met cloudservices | Info | > 0 |

>[!NOTE]
>
>Zie {de Metrische Definities van 0} SonarQube ](https://docs.sonarsource.com/sonarqube-server/latest/user-guide/code-metrics/metrics-definition/) voor meer gedetailleerde definities.[

>[!NOTE]
>
>Meer over de de kwaliteitsregels van de douanecode leren die door [!UICONTROL Cloud Manager] worden in werking gesteld, zie [ de Regels van de Kwaliteit van de Code van de Douane ](/help/implementing/cloud-manager/custom-code-quality-rules.md).

## Werken met valse positieven {#dealing-with-false-positives}

Het kwaliteitscontroleproces is niet perfect en identificeert soms problemen die eigenlijk geen problemen zijn. Deze staat wordt genoemd a **vals positief**.

In deze gevallen kan de broncode worden geannoteerd met de standaard Java `@SuppressWarnings` -annotatie die de regel-id opgeeft als het annotatiekenmerk. Bijvoorbeeld, één gemeenschappelijk vals positief is dat de regel SonarQube om hardcoded wachtwoorden te ontdekken agressief kan zijn over hoe een hard - gecodeerd wachtwoord wordt geïdentificeerd.

De volgende code is vrij gemeenschappelijk in een AEM project, dat code heeft om met één of andere externe dienst te verbinden.

```java
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

SonarQube vergroot een kwetsbaarheid voor blokkers. Maar na het herzien van de code, erkent u dat deze kwestie geen kwetsbaarheid is en kan de code met aangewezen regelidentiteitskaart annoteren.

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

Nochtans, als de code eigenlijk het volgende was:

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String PROP_SERVICE_PASSWORD = "password";
```

Dan is de correcte oplossing het hardcoded wachtwoord te verwijderen.

>[!NOTE]
>
>Hoewel het aan te raden is de annotatie `@SuppressWarnings` zo specifiek mogelijk te maken (bijvoorbeeld alleen de instructie of het blok dat de uitgave veroorzaakt aanwijzen), is het ook mogelijk om een annotatie op klasseniveau te maken.

>[!NOTE]
>Terwijl er geen expliciete veiligheidsteststap is, zijn er veiligheid-verwante code kwaliteitsregels die tijdens de stap van de codekwaliteit worden geëvalueerd. Zie [ Overzicht van de Veiligheid voor AEM as a Cloud Service ](/help/security/cloud-service-security-overview.md) om meer over veiligheid in Cloud Service te leren.

## Optimalisatie van inhoudspakketscannen {#content-package-scanning-optimization}

In het kader van het kwaliteitsanalyseproces voert Cloud Manager een analyse uit van de inhoudspakketten die door de Maven-build worden geproduceerd. Cloud Manager biedt optimalisaties om dit proces te versnellen, dat effectief is wanneer bepaalde verpakkingsbeperkingen worden nageleefd. De meest significante optimalisering richt projecten die één enkel &quot;al&quot;pakket produceren, die veelvoudige inhoudspakketten van de bouwstijl bevatten, die als overgeslagen duidelijk zijn. Wanneer Cloud Manager dit scenario detecteert in plaats van het &quot;all&quot;-pakket uit te pakken, worden de afzonderlijke inhoudspakketten direct gescand en gesorteerd op basis van afhankelijkheden. Neem bijvoorbeeld de volgende build-uitvoer.

* `all/myco-all-1.0.0-SNAPSHOT.zip` (content-package)
* `ui.apps/myco-ui.apps-1.0.0-SNAPSHOT.zip` (overgeslagen-content-package)
* `ui.content/myco-ui.content-1.0.0-SNAPSHOT.zip` (overgeslagen-content-package)

Als de enige items binnen `myco-all-1.0.0-SNAPSHOT.zip` de twee overgeslagen inhoudspakketten zijn, worden de twee ingesloten pakketten gescand in plaats van het &quot;all&quot;-inhoudspakket.

Voor projecten die tientallen ingebedde pakketten produceren, is deze optimalisering getoond om naar boven van 10 minuten per pijpleidingsuitvoering te besparen.

Een speciaal geval kan voorkomen wanneer het &quot;alle&quot;inhoudspakket een combinatie overgeslagen inhoudspakketten en bundels OSGi bevat. Als `myco-all-1.0.0-SNAPSHOT.zip` bijvoorbeeld de twee eerder vermelde ingesloten pakketten en een of meer OSGi-pakketten bevat, wordt een nieuw, minimaal inhoudspakket samengesteld met alleen de OSGi-bundels. Dit pakket krijgt altijd de naam `cloudmanager-synthetic-jar-package` en de opgenomen bundels worden in `/apps/cloudmanager-synthetic-installer/install` geplaatst.

>[!NOTE]
>
>* Deze optimalisatie heeft geen invloed op de pakketten die worden geïmplementeerd op AEM.
>* De overeenkomst tussen ingesloten inhoudspakketten en overgeslagen inhoudspakketten is afhankelijk van bestandsnamen. Deze optimalisatie kan niet optreden als meerdere overgeslagen pakketten dezelfde bestandsnaam hebben of als de bestandsnaam tijdens het insluiten verandert.
