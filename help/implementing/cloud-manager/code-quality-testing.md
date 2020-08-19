---
title: Codekwaliteitstests - Cloud Services
description: Codekwaliteitstests - Cloud Services
translation-type: tm+mt
source-git-commit: 25ba5798de175b71be442d909ee5c9c37dcf10d4
workflow-type: tm+mt
source-wordcount: '714'
ht-degree: 2%

---


# Testen van de codekwaliteit {#code-quality-testing}

Het testen van de Kwaliteit van de Code evalueert de kwaliteit van uw toepassingscode. Het is de kerndoelstelling van een code-Kwaliteit enige pijpleiding en wordt uitgevoerd onmiddellijk na de bouwstap in alle niet-productie en productiepijpleidingen.

Verwijs naar het [Vormen van uw CI-CD Pijpleiding](/help/implementing/cloud-manager/configure-pipeline.md) om meer over verschillende types van pijpleidingen te leren.

## Inzicht in aangepaste regels voor codekwaliteit {#understanding-code-quality-rules}

Bij het testen van de kwaliteit van de code, wordt de broncode gescand om ervoor te zorgen dat het aan bepaalde kwaliteitscriteria voldoet. Momenteel wordt dit geïmplementeerd door een combinatie van SonarQube en inhoudspakketonderzoek met gebruik van OakPAL. Er zijn meer dan 100 regels die generieke Java-regels en AEM-specifieke regels combineren. Enkele AEM-specifieke regels worden gecreeerd gebaseerd op beste praktijken van AEM Techniek en worden bedoeld als Regels [van de Kwaliteit van de](/help/implementing/cloud-manager/custom-code-quality-rules.md)Code van de Douane.

>[!NOTE]
>U kunt de volledige lijst met regels [hier](/help/implementing/cloud-manager/assets/CodeQuality-rules-latest.xlsx)downloaden.

De resultaten van deze stap worden geleverd als *Classificatie*. In de volgende tabel wordt de classificatie voor testcriteria samengevat:

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

>[!NOTE]
>
>Zie [Metrische definities](https://docs.sonarqube.org/display/SONAR/Metric+Definitions) voor meer gedetailleerde definities.


>[!NOTE]
>
>Voor meer informatie over de regels voor de kwaliteit van aangepaste code die worden uitgevoerd door [!UICONTROL Cloud Manager], raadpleegt u [Aangepaste regels](/help/implementing/cloud-manager/custom-code-quality-rules.md)voor codekwaliteit.

## Werken met valse positieven {#dealing-with-false-positives}

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
