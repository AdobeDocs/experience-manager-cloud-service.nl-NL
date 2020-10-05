---
title: Opvallende wijzigingen in Adobe Experience Manager (AEM) als Cloud Service
description: Opvallende wijzigingen in Adobe Experience Manager (AEM) als Cloud Service
translation-type: tm+mt
source-git-commit: c1014098cecf3c3f86a7af844801fb1202864b51
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 8%

---


# Notable Changes to Adobe Experience Manager (AEM) as a Cloud Service {#notable-changes-aem-cloud}

AEM Cloud Service biedt veel nieuwe functies en mogelijkheden voor het beheer van uw AEM-projecten. Er zijn echter een aantal verschillen tussen AEM Sites op locatie of in Adobe Managed Service in vergelijking met AEM Cloud Service. In dit document worden de belangrijke verschillen belicht.

>[!NOTE]
>Dit document benadrukt de opmerkelijke veranderingen in AEM als geheel. Voor meer informatie en oplossingsspecifieke veranderingen zie:
>
>* [Inleiding tot Adobe Experience Manager as a Cloud Service](/help/overview/introduction.md)
>* [Nieuwe functies en verschillen](/help/overview/what-is-new-and-different.md) tussen Adobe Experience Manager as a Cloud Service en eerdere versies
>* De [architectuur](/help/core-concepts/architecture.md) van Adobe Experience Manager as a Cloud Service
>* [Belangrijke wijzigingen in AEM Sites as a Cloud Service](/help/sites-cloud/sites-cloud-changes.md)
>* [Belangrijke wijzigingen in AEM Assets as a Cloud Service](/help/assets/assets-cloud-changes.md)


De belangrijkste verschillen zijn te vinden op de volgende gebieden:

* [/apps en /libs zijn onveranderlijk bij runtime](#apps-libs-immutable)

* [OSGi-bundels en -instellingen moeten zijn gebaseerd op gegevensopslagruimte](#osgi)

* [Wijzigingen in publicatieruimte zijn niet toegestaan](#changes-to-publish-repo)

* [Aangepaste runmodi zijn niet toegestaan](#custom-runmodes)

* [Verwijderen van replicatieagents](#replication-agents)

* [Verwijderen van klassieke gebruikersinterface](#classic-ui)

* [Levering op de website publiceren](#publish-side-delivery)

* [Afhandeling en levering van bedrijfsmiddelen](#asset-handling)

## /apps en /libs zijn onveranderlijk bij runtime {#apps-libs-immutable}

Alle inhoud en submappen in `/apps` en `/libs` zijn alleen-lezen. Om het even welke eigenschap of douanecode die verwacht om veranderingen daar aan te brengen zal er niet doen. Er wordt een fout geretourneerd dat dergelijke inhoud alleen-lezen is en de schrijfbewerking niet kan worden voltooid. Dit heeft gevolgen voor een aantal AEM:

* Er `/libs` zijn helemaal geen wijzigingen toegestaan.
   * Dit is geen nieuwe regel, nochtans werd dit niet afgedwongen in vorige on-premise versies van AEM.
* Bedekkingen voor gebieden `/libs` die mogen worden bedekt, zijn nog steeds toegestaan binnen `/apps`.
   * Dergelijke overlays moeten afkomstig zijn van Git via de CI/CD-leiding.
* De statische het ontwerpinformatie van het Malplaatje die in wordt opgeslagen `/apps` kan niet via UI worden uitgegeven.
   * Het wordt aanbevolen bewerkbare sjablonen te gebruiken.
   * Als de Statische Malplaatjes nog worden vereist, moet de configuratieinformatie uit Git via de pijpleiding CI/CD komen.
* MSM de Vervaging en de douaneMSM uitrolconfiguraties moeten van Git via de pijpleiding worden geïnstalleerd CI/CD.
* I18n vertalingsveranderingen moeten van Git via de CI/CD pijpleiding komen.

## OSGi-bundels en -instellingen moeten zijn gebaseerd op gegevensopslagruimte {#osgi}

De console van het Web, die in vorige versies van AEM wordt gebruikt om montages te veranderen OSGi, is niet beschikbaar in AEM Cloud Service. Daarom moeten wijzigingen in OSGi worden aangebracht via de CI/CD-pijplijn.

* Wijzigingen in OSGi-instellingen kunnen alleen via Git-persistentie worden uitgevoerd als op JCR gebaseerde OSGi-instellingen.
* Nieuwe of bijgewerkte OSGi-bundels moeten via Git worden geïntroduceerd als onderdeel van het aanlegproces van de CI/CD-pijplijn.

## Wijzigingen in publicatieruimte zijn niet toegestaan {#changes-to-publish-repo}

Directe wijzigingen in de publicatiereserver zijn niet toegestaan op AEM Cloud Service. In eerdere versies van on-premise AEM of AEM op AMS konden codewijzigingen rechtstreeks in de publicatieruimte worden aangebracht, bijvoorbeeld om gebruikers te maken, gebruikersprofiel bij te werken en knooppunten te maken. Dit is niet meer mogelijk en kan op de volgende manieren worden beperkt:

* Voor op inhoud en inhoud gebaseerde configuratie: Breng de wijzigingen aan in de auteurinstantie en publiceer deze.
* Voor code en configuratie: de wijzigingen in de GIT-opslagplaats aan te brengen en de CI/CD-pijpleiding uit te voeren.
* Voor gebruikersgerelateerde gegevens zoals formulierverzendingen of profielgegevens: gebruik de Verenigde Dienst van het Profiel van de Platform van Experience Cloud of andere derde partij zitting bewust opslag.

## Aangepaste runmodi zijn niet toegestaan {#custom-runmodes}

De volgende runmodes worden verstrekt uit-van-de-doos voor AEM Cloud Service:

* `author`
* `publish`
* `prod`
* `author.prod`
* `publish.prod`
* `stage`
* `author.stage`
* `publish.stage`
* `dev`
* `author.dev`
* `publish.dev`

Aanvullende of aangepaste uitvoermodi zijn niet mogelijk in AEM Cloud Service.

## Verwijderen van replicatieagents {#replication-agents}

In AEM Cloud Service wordt inhoud gepubliceerd met behulp van [Sling Content Distribution](https://sling.apache.org/documentation/bundles/content-distribution.html). De replicatieagenten die in vorige versies van AEM worden gebruikt worden niet meer gebruikt of verstrekt, die de volgende gebieden van bestaande AEM projecten zouden kunnen beïnvloeden:

* Aangepaste workflows die bijvoorbeeld inhoud doorsturen naar replicatieagents van voorvertoningsservers.
* Aanpassing aan replicatieagenten om inhoud om te zetten
* De omgekeerde Replicatie gebruiken om inhoud van te brengen terug naar auteur publiceren

## Verwijderen van klassieke gebruikersinterface {#classic-ui}

De klassieke gebruikersinterface is niet meer beschikbaar in AEM Cloud Service.

## Levering op de website publiceren {#publish-side-delivery}

De versnelling van HTTP met inbegrip van CDN en verkeersbeheer voor auteur en publiceer de diensten worden verstrekt door gebrek in AEM Cloud Service.

Voor project dat van AMS of een op-gebouw Adobe overgaat adviseert sterk leveraging ingebouwde CDN, omdat de eigenschappen binnen AEM Cloud Service voor CDN worden geoptimaliseerd verstrekt.

## Afhandeling en levering van bedrijfsmiddelen {#asset-handling}

Het uploaden, de verwerking en het downloaden van bedrijfsmiddelen zijn in Elementen geoptimaliseerd als een Cloud Service die efficiënter het toelaten van betere schrapping en snellere uploads en downloads. Dit kan echter invloed hebben op sommige bestaande aangepaste code.

* De standaardworkflow **DAM Asset Update** in eerdere versies van AEM is niet meer beschikbaar.
* De componenten van de website die een binair **zonder transformatie** leveren zouden directe download moeten gebruiken.
   * De Sling GET servlet is veranderd om dit door gebrek te doen.
* De componenten van de website die een binair **met transformatie** (bijvoorbeeld, resize via servlet) leveren kunnen blijven werken aangezien zij hebben.
* Elementen die via Package Manager worden binnengebracht, moeten handmatig opnieuw worden verwerkt met behulp van de handeling **Element** opnieuw verwerken in de interface Elementen.
