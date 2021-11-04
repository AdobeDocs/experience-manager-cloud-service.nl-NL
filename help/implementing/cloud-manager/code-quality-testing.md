---
title: Codekwaliteitstests - Cloud Services
description: Codekwaliteitstests - Cloud Services
exl-id: e2981be9-fb14-451c-ad1e-97c487e6dc46
source-git-commit: f8695dd8fdc9ffb203bab943c335ab2957df6251
workflow-type: tm+mt
source-wordcount: '867'
ht-degree: 1%

---

# Testen van de codekwaliteit {#code-quality-testing}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_codequalitytests"
>title="Testen van de codekwaliteit"
>abstract="Het testen van de Kwaliteit van de Code evalueert de kwaliteit van uw toepassingscode. Het is de kerndoelstelling van een code-Kwaliteit enige pijpleiding en wordt uitgevoerd onmiddellijk na de bouwstap in alle niet-productie en productiepijpleidingen."

Het testen van de Kwaliteit van de Code evalueert de kwaliteit van uw toepassingscode. Het is de kerndoelstelling van een code-Kwaliteit enige pijpleiding en wordt uitgevoerd onmiddellijk na de bouwstap in alle niet-productie en productiepijpleidingen.

Zie [Het vormen van uw CI-CD Pijpleiding](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) voor meer informatie over verschillende soorten pijpleidingen.

## Codekwaliteitsregels {#understanding-code-quality-rules}

Bij het testen van de kwaliteit van de code, wordt de broncode gescand om ervoor te zorgen dat het aan bepaalde kwaliteitscriteria voldoet. Momenteel wordt dit geïmplementeerd door een combinatie van SonarQube en inhoudspakketonderzoek met gebruik van OakPAL. Er zijn meer dan 100 regels die generieke Java-regels en AEM-specifieke regels combineren. Sommige AEM-specifieke regels worden gecreeerd gebaseerd op beste praktijken van AEM Techniek en worden bedoeld zoals [Aangepaste regels voor codekwaliteit](/help/implementing/cloud-manager/custom-code-quality-rules.md).

>[!NOTE]
>U kunt de volledige lijst met regels downloaden [hier](/help/implementing/cloud-manager/assets/CodeQuality-rules-latest-CS.xlsx).

**Drielagige plaat**

Deze stap voor het testen van de codekwaliteit bevat een structuur met drie niveaus voor de geïdentificeerde problemen:

* **Kritiek**: Dit zijn kwesties die door de poort worden geïdentificeerd en die een directe mislukking van de pijpleiding veroorzaken.

* **Belangrijk**: Dit zijn kwesties die door de poort worden geïdentificeerd die de pijpleiding veroorzaken om een gepauzeerde staat in te gaan. Een plaatsingsmanager, projectmanager, of bedrijfseigenaar kunnen of de kwesties met voeten treden, waarin de pijpleiding te werk gaat, of zij kunnen de kwesties goedkeuren, in welk geval de pijpleiding met een mislukking stopt.

* **Info**: Dit zijn kwesties die door de poort worden geïdentificeerd en die uitsluitend ter informatie worden verstrekt en geen invloed hebben op de uitvoering van de pijpleiding

De resultaten van deze stap worden geleverd als *Waarderingen*.

De volgende tabel geeft een overzicht van de classificaties en foutdrempels voor elk van de categorieën Kritiek, Belangrijk en Informatie:

| Naam | Definitie | Categorie | Drempel voor fout |
|--- |--- |--- |--- |
| Beveiligingsbeoordeling | A = 0 Kwetsbaarheid <br/>B = ten minste 1 kleine kwetsbaarheid<br/> C = ten minste 1 grote kwetsbaarheid <br/>D = minimaal 1 kritieke kwetsbaarheid <br/>E = ten minste 1 kwetsbaarheid van de blokker | Kritiek | &lt; B |
| Betrouwbaarheidsbeoordeling | A = 0 Bug <br/>B = minimaal 1 kleine bug <br/>C = ten minste 1 groot probleem <br/>D = minimaal 1 kritieke fout E = minimaal 1 blokkeringsfout | Belangrijk | &lt; C |
| Onderhoudsverklaring | Uitstaande herstelkosten voor codegeuren zijn: <br/><ul><li>&lt;=5% van de tijd die al in de toepassing is ingegaan, is de rating A </li><li>tussen 6 en 10% is de rating een B </li><li>tussen 11 en 20% is de rating een C </li><li>tussen 21 en 50% is de rating een D</li><li>iets meer dan 50% is een E</li></ul> | Belangrijk | &lt; A |
| Dekking | Een combinatie van de dekking van de meetlijn en de toestand volgens deze formule: <br/>`Coverage = (CT + CF + LC)/(2*B + EL)`  <br/>waarbij: CT = voorwaarden die ten minste één keer zijn geëvalueerd op &#39;true&#39; tijdens het uitvoeren van eenheidstests <br/>CF = voorwaarden die ten minste één keer zijn geëvalueerd op &#39;false&#39; tijdens het uitvoeren van eenheidstests <br/>LC = gedekte lijnen = lines_to_cover - uncoveren <br/><br/> B = totaal aantal voorwaarden <br/>EL = totaal aantal uitvoerbare lijnen (lijnen_naar_omslag) | Belangrijk | &lt; 50% |
| Overgeslagen eenheidstests | Aantal overgeslagen eenheidstests. | Info | > 1 |
| Problemen openen | Algemene uitgiftypen - Vulnerabilities, Bugs en Codefragmenten | Info | > 0 |
| Gedupliceerde lijnen | Aantal lijnen betrokken bij gedupliceerde blokken. <br/>Een codeblok dat als gedupliceerd moet worden beschouwd: <br/><ul><li>**Niet-Java-projecten:**</li><li>Er moeten ten minste 100 opeenvolgende en gedupliceerde tokens zijn.</li><li>Deze tokens moeten ten minste op: </li><li>30 regels code voor COBOL </li><li>20 coderegels voor ABAP </li><li>10 coderegels voor andere talen</li><li>**Java-projecten:**</li><li> Er moeten minstens tien opeenvolgende en gedupliceerde verklaringen zijn, ongeacht het aantal tokens en lijnen.</li></ul> <br/>Verschillen in inspringing en in letterlijke tekenreeksen worden genegeerd bij het detecteren van duplicaten. | Info | > 1% |
| Compatibiliteit met Cloud Service | Aantal geïdentificeerde kwesties van de Verenigbaarheid van de Cloud Service. | Info | > 0 |

>[!NOTE]
>
>Zie [Metrische definities](https://docs.sonarqube.org/display/SONAR/Metric+Definitions) voor meer gedetailleerde definities.


>[!NOTE]
>
>Meer informatie over de kwaliteitsregels van de aangepaste code die worden uitgevoerd door [!UICONTROL Cloud Manager], raadpleeg [Aangepaste regels voor codekwaliteit](/help/implementing/cloud-manager/custom-code-quality-rules.md).

## Werken met valse positieven {#dealing-with-false-positives}

Het kwaliteitscontroleproces is niet perfect en zal soms ten onrechte problemen identificeren die eigenlijk niet problematisch zijn. Dit wordt bedoeld als a *vals positief*.

In deze gevallen kan de broncode worden geannoteerd met de standaard-Java `@SuppressWarnings` annotatie die de regel-id opgeeft als het annotatiekenmerk. Een veelvoorkomend probleem is bijvoorbeeld dat de SonarQube-regel voor het detecteren van gecodeerde wachtwoorden agressief kan zijn ten aanzien van de manier waarop een gecodeerd wachtwoord wordt geïdentificeerd.

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
>Het is weliswaar de beste praktijk om `@SuppressWarnings` annotatie zo specifiek mogelijk, d.w.z. alleen de specifieke instructie of het blok dat de uitgave veroorzaakt, annoteren op klasseniveau mogelijk maken.

>[!NOTE]
>Terwijl er geen expliciete het Testen van de Veiligheid stap is, zijn er nog veiligheid-verwante code kwaliteitsregels die tijdens de stap van de codekwaliteit worden geëvalueerd. Zie [Beveiligingsoverzicht voor AEM as a Cloud Service](/help/security/cloud-service-security-overview.md) voor meer informatie over beveiliging in Cloud Service.
