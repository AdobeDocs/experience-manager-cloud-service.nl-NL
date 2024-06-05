---
title: Testen van de codekwaliteit
description: Leer hoe het testen van de codekwaliteit van pijpleidingen werkt en hoe het de kwaliteit van uw plaatsingen kan verbeteren.
exl-id: e2981be9-fb14-451c-ad1e-97c487e6dc46
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '1171'
ht-degree: 0%

---

# Testen van de codekwaliteit {#code-quality-testing}

Leer hoe het testen van de codekwaliteit van pijpleidingen werkt en hoe het de kwaliteit van uw plaatsingen kan verbeteren.

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_codequalitytests"
>title="Testen van de codekwaliteit"
>abstract="Bij het testen van de codekwaliteit wordt uw toepassingscode geëvalueerd op basis van een set kwaliteitsregels. Het is het primaire doel van een code-kwaliteit slechts pijpleiding en wordt uitgevoerd onmiddellijk na de bouwstap in alle productie en niet-productiepijpleidingen."

## Inleiding {#introduction}

Bij het testen van de codekwaliteit wordt uw toepassingscode geëvalueerd op basis van een set kwaliteitsregels. Het is het primaire doel van een code-kwaliteit slechts pijpleiding en wordt uitgevoerd onmiddellijk na de bouwstap in alle productie en niet-productiepijpleidingen.

Zie [Het vormen van Uw CI-CD Pijpleiding](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) voor meer informatie over verschillende soorten pijpleidingen.

## Codekwaliteitsregels {#understanding-code-quality-rules}

Testen van de codekwaliteit scant de broncode om ervoor te zorgen dat deze aan bepaalde kwaliteitscriteria voldoet. Dit wordt geïmplementeerd door een combinatie van SonarQube en inhoudspakketonderzoek met behulp van OakPAL. Er zijn meer dan 100 regels, die generieke regels van Java en AEM-specifieke regels combineren. Sommige AEM-specifieke regels worden gecreeerd gebaseerd op beste praktijken van AEM Techniek en worden bedoeld zoals [aangepaste regels voor codekwaliteit](/help/implementing/cloud-manager/custom-code-quality-rules.md).

>[!NOTE]
>
>U kunt de volledige lijst met regels downloaden [met deze koppeling](/help/implementing/cloud-manager/assets/CodeQuality-rules-latest-CS.xlsx).

### Waarderingen met drie lagen {#three-tiered-gate}

Kwesties die door code kwaliteitstests worden geïdentificeerd worden toegewezen aan één van drie categorieën.

* **Kritiek** - Dit zijn kwesties die een onmiddellijk mislukken van de pijpleiding veroorzaken.

* **Belangrijk** - Dit zijn kwesties die de pijpleiding veroorzaken om een gepauzeerde staat in te gaan. Een plaatsingsmanager, projectmanager, of bedrijfseigenaar kunnen of de kwesties met voeten treden, waarin de pijpleiding te werk gaat, of zij kunnen de kwesties goedkeuren, in welk geval de pijpleiding met een mislukking stopt.

* **Info** - Dit zijn kwesties die louter ter informatie worden verstrekt en geen invloed hebben op de uitvoering van de pijpleiding

>[!NOTE]
>
>In een slechts pijpleiding van de codekwaliteit, kunnen de belangrijke mislukkingen in de gate van de Kwaliteit van de Code niet worden met voeten getreden aangezien de het testen stap van de codekwaliteit de definitieve stap in de pijpleiding is.

### Waarderingen {#ratings}

De resultaten van deze stap worden geleverd als **Waarderingen**.

De volgende tabel geeft een overzicht van de classificaties en foutdrempels voor elk van de kritieke, belangrijke en informatiecategorieën.

| Naam | Definitie | Categorie | Drempel voor fout |
|--- |--- |--- |--- |
| Beveiligingsbeoordeling | A = Geen kwetsbaarheden <br/>B = minimaal 1 kleine kwetsbaarheid<br/> C = ten minste 1 grote kwetsbaarheid <br/>D = minimaal 1 kritieke kwetsbaarheid <br/>E = Minstens 1 blokkeerkwetsbaarheid | Kritiek | &lt; B |
| Betrouwbaarheidsbeoordeling | A = Geen fouten <br/>B = ten minste 1 kleine bug <br/>C = ten minste 1 grote bug <br/>D = minstens 1 kritieke bug<br>E = Minstens 1 blocker bug | Kritiek | &lt; D |
| Onderhoudsverklaring | Gedefinieerd door de openstaande herstelkosten voor code wordt gegesmelt als percentage van de tijd die al in de toepassing is gegaan<br/><ul><li>A = &lt;=5%</li><li>B = 6-10%</li><li>C = 11-20%</li><li>D = 21-50%</li><li>E = >50%</li></ul> | Belangrijk | &lt; A |
| Dekking | Gedefinieerd door een combinatie van de dekking van de testlijn en de conditie met behulp van de formule: <br/>`Coverage = (CT + CF + LC)/(2*B + EL)`  <ul><li>`CT` = Voorwaarden die zijn beoordeeld als `true` ten minste één keer tijdens het uitvoeren van eenheidstests</li><li>`CF` = Voorwaarden die zijn beoordeeld als `false` ten minste één keer tijdens het uitvoeren van eenheidstests</li><li>`LC` = Coverlines = lines_to_cover - uncover_lines</li><li>`B` = totaal aantal voorwaarden</li><li>`EL` = totaal aantal uitvoerbare regels (lines_to_cover)</li></ul> | Belangrijk | &lt; 50% |
| Overgeslagen eenheidstests | Aantal overgeslagen eenheidstests | Info | > 1 |
| Problemen openen | Algemene uitgiftypen - Vulnerabilities, Bugs en Codefragmenten | Info | > 0 |
| Gedupliceerde lijnen | Gedefinieerd als het aantal regels dat is betrokken bij gedupliceerde blokken. Een codeblok wordt als gedupliceerd beschouwd onder de volgende omstandigheden.<br>Niet-Java-projecten:<ul><li>Er moeten ten minste 100 opeenvolgende en gedupliceerde tokens zijn.</li><li>Deze tokens moeten ten minste worden verspreid over: </li><li>30 regels code voor COBOL </li><li>20 coderegels voor ABAP </li><li>10 coderegels voor andere talen</li></ul>Java-projecten:<ul></li><li> Er moeten minstens tien opeenvolgende en gedupliceerde instructies zijn, ongeacht het aantal tokens en regels.</li></ul>Verschillen in inspringing en in letterlijke tekenreeksen worden genegeerd wanneer duplicaten worden gedetecteerd. | Info | > 1% |
| Compatibiliteit met Cloud Service | Aantal geïdentificeerde compatibiliteitsproblemen met cloudservices | Info | > 0 |

>[!NOTE]
>
>Zie [Metrische definities van SonarQube](https://docs.sonarqube.org/latest/user-guide/metric-definitions/) voor meer gedetailleerde definities.

>[!NOTE]
>
>Meer informatie over de kwaliteitsregels voor aangepaste code die worden uitgevoerd door [!UICONTROL Cloud Manager], zie [Aangepaste regels voor codekwaliteit](/help/implementing/cloud-manager/custom-code-quality-rules.md).

## Werken met valse positieven {#dealing-with-false-positives}

Het kwaliteitscontroleproces is niet perfect en zal soms ten onrechte problemen identificeren die eigenlijk niet problematisch zijn. Dit wordt bedoeld als a **vals positief**.

In deze gevallen kan de broncode worden geannoteerd met de standaard-Java `@SuppressWarnings` annotatie die regel-id opgeeft als annotatiekenmerk. Bijvoorbeeld, één gemeenschappelijk vals positief is dat de regel SonarQube om hardcoded wachtwoorden te ontdekken agressief kan zijn over hoe een hard - gecodeerd wachtwoord wordt geïdentificeerd.

De volgende code is vrij gemeenschappelijk in een AEM project, dat code heeft om met één of andere externe dienst te verbinden.

```java
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

SonarQube zal dan een blokkeerkwetsbaarheid veroorzaken. Maar na het herzien van de code, erkent u dat dit geen kwetsbaarheid is en kan de code met aangewezen regelidentiteitskaart annoteren.

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
>Het is weliswaar de beste praktijk om `@SuppressWarnings` annotatie die zo specifiek mogelijk is, dat wil zeggen dat alleen de specifieke instructie of het specifieke blok dat de uitgave veroorzaakt, kan worden geannoteerd op klasseniveau.

>[!NOTE]
>Terwijl er geen expliciete veiligheidsteststap is, zijn er veiligheid-verwante code kwaliteitsregels die tijdens de stap van de codekwaliteit worden geëvalueerd. Zie [Beveiligingsoverzicht voor AEM as a Cloud Service](/help/security/cloud-service-security-overview.md) voor meer informatie over beveiliging in Cloud Service.

## Optimalisatie van inhoudspakketscannen {#content-package-scanning-optimization}

In het kader van het kwaliteitsanalyseproces voert Cloud Manager een analyse uit van de inhoudspakketten die door de Maven-build worden geproduceerd. Cloud Manager biedt optimalisaties om dit proces te versnellen, die effectief zijn wanneer bepaalde verpakkingsbeperkingen worden nageleefd. Het meest significant is de optimalisering die voor projecten wordt uitgevoerd die één enkel inhoudspakket uitvoeren, dat algemeen als &quot;allen&quot;pakket wordt bedoeld, dat verscheidene andere inhoudspakketten bevat die door de bouwstijl worden geproduceerd, die als overgeslagen worden gemerkt. Wanneer Cloud Manager dit scenario detecteert in plaats van het &quot;all&quot;-pakket uit te pakken, worden de afzonderlijke inhoudspakketten direct gescand en gesorteerd op basis van afhankelijkheden. Neem bijvoorbeeld de volgende build-uitvoer.

* `all/myco-all-1.0.0-SNAPSHOT.zip` (content-package)
* `ui.apps/myco-ui.apps-1.0.0-SNAPSHOT.zip` (overgeslagen-content-package)
* `ui.content/myco-ui.content-1.0.0-SNAPSHOT.zip` (overgeslagen-content-package)

Als de enige items binnen `myco-all-1.0.0-SNAPSHOT.zip` zijn de twee overgeslagen inhoudspakketten , dan worden de twee ingesloten pakketten gescand in plaats van het &quot; all &quot; - inhoudspakket .

Voor projecten die tientallen ingebedde pakketten produceren, is deze optimalisering getoond om naar boven van 10 minuten per pijpleidingsuitvoering te besparen.

Een speciaal geval kan voorkomen wanneer het &quot;alle&quot;inhoudspakket een combinatie overgeslagen inhoudspakketten en bundels OSGi bevat. Als `myco-all-1.0.0-SNAPSHOT.zip` bevat de twee eerder vermelde ingesloten pakketten en een of meer OSGi-bundels, dan wordt een nieuw, minimaal inhoudspakket samengesteld met alleen de OSGi-bundels. Dit pakket krijgt altijd een naam `cloudmanager-synthetic-jar-package` en de opgenomen bundels worden in `/apps/cloudmanager-synthetic-installer/install`.

>[!NOTE]
>
>* Deze optimalisatie heeft geen invloed op de pakketten die worden geïmplementeerd op AEM.
>* Omdat de overeenkomst tussen de ingesloten inhoudspakketten en de overgeslagen inhoudspakketten is gebaseerd op bestandsnamen, kan deze optimalisatie niet worden uitgevoerd als meerdere overgeslagen inhoudspakketten exact dezelfde bestandsnaam hebben of als de bestandsnaam tijdens het insluiten is gewijzigd.
