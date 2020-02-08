---
title: Opmerkelijke wijzigingen in Adobe Experience Manager (AEM) als cloudservice
description: Opmerkelijke wijzigingen in Adobe Experience Manager (AEM) als cloudservice
translation-type: tm+mt
source-git-commit: e76de9b84931dced6383570e384ffdb6fb334daf

---


# Opmerkelijke wijzigingen in Adobe Experience Manager (AEM) als cloudservice {#notable-changes-aem-cloud}

De AEM Cloud Service biedt veel nieuwe functies en mogelijkheden voor het beheer van uw AEM-projecten. Er zijn echter een aantal verschillen tussen AEM-sites op locatie of in de beheerde service van Adobe in vergelijking met de AEM Cloud Service. In dit document worden de belangrijke verschillen belicht.

>[!NOTE]
>Dit document benadrukt de opmerkelijke veranderingen in AEM als geheel. Voor oplossing-specifieke veranderingen zie:
>
>* [Opvallende wijzigingen in AEM-sites in AEM Cloud Service](/help/sites-cloud/sites-cloud-changes.md)
>* [Opvallende wijzigingen in AEM-middelen in AEM Cloud Service](/help/assets/assets-cloud-changes.md)


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

Alle inhoud en submappen in `/apps` en `/libs` zijn alleen-lezen. Om het even welke eigenschap of douanecode die verwacht om veranderingen daar aan te brengen zal er niet doen. Er wordt een fout geretourneerd dat dergelijke inhoud alleen-lezen is en de schrijfbewerking niet kan worden voltooid. Dit heeft gevolgen op een aantal gebieden van AEM:

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

De webconsole, die in eerdere versies van AEM werd gebruikt om OSGi-instellingen te wijzigen, is niet beschikbaar in AEM Cloud Service. Daarom moeten wijzigingen in OSGi worden aangebracht via de CI/CD-pijplijn.

* Wijzigingen in OSGi-instellingen kunnen alleen via Git-persistentie worden uitgevoerd als op JCR gebaseerde OSGi-instellingen.
* Nieuwe of bijgewerkte OSGi-bundels moeten via Git worden geïntroduceerd als onderdeel van het aanlegproces van de CI/CD-pijplijn.

## Wijzigingen in publicatieruimte zijn niet toegestaan {#changes-to-publish-repo}

Directe wijzigingen in de publicatieopslagplaats zijn niet toegestaan op AEM Cloud Service. In eerdere versies van AEM (on-premise) of AEM (on-premise) op AMS konden wijzigingen in de code rechtstreeks worden aangebracht in de publicatieopslagplaats, bijvoorbeeld om gebruikers te maken, gebruikersprofielen bij te werken en knooppunten te maken. Dit is niet meer mogelijk en kan op de volgende manieren worden beperkt:

* Voor op inhoud en inhoud gebaseerde configuratie: Breng de wijzigingen aan in de auteurinstantie en publiceer deze.
* Voor code en configuratie: de wijzigingen in de GIT-opslagplaats aan te brengen en de CI/CD-pijpleiding uit te voeren.
* Voor gebruikersgerelateerde gegevens zoals formulierverzendingen of profielgegevens: gebruik de Unified Profile Service van Experience Cloud Platform of een andere sessie van derden.

## Aangepaste runmodi zijn niet toegestaan {#custom-runmodes}

De volgende runmodi zijn beschikbaar buiten de box voor AEM Cloud Service:

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

In AEM Cloud Service wordt inhoud gepubliceerd met behulp van [Sling Content Distribution](https://sling.apache.org/documentation/bundles/content-distribution.html). De replicatieagenten die in vorige versies van AEM worden gebruikt worden niet meer gebruikt of verstrekt, die de volgende gebieden van bestaande projecten zouden kunnen beïnvloeden AEM:

* Aangepaste workflows die bijvoorbeeld inhoud doorsturen naar replicatieagents van voorvertoningsservers.
* Aanpassing aan replicatieagenten om inhoud om te zetten
* De omgekeerde Replicatie gebruiken om inhoud van te brengen terug naar auteur publiceren

## Verwijderen van klassieke gebruikersinterface {#classic-ui}

De klassieke gebruikersinterface is niet meer beschikbaar in AEM Cloud Service.

## Levering op de website publiceren {#publish-side-delivery}

De versnelling van HTTP met inbegrip van CDN en verkeersbeheer voor auteur en publicatieservices worden door gebrek verstrekt in de Dienst van de Wolk AEM.

Voor projectovergangen van AMS of een installatie op locatie raadt Adobe u ten zeerste aan de ingebouwde CDN te gebruiken, omdat de functies in de AEM Cloud Service zijn geoptimaliseerd voor de geleverde CDN.

## Afhandeling en levering van bedrijfsmiddelen {#asset-handling}

Het uploaden, verwerken en downloaden van bedrijfsmiddelen is geoptimaliseerd in de AEM Cloud Service, zodat deze efficiënter kan worden geschaald en sneller kan worden geüpload en gedownload. Dit kan echter invloed hebben op sommige bestaande aangepaste code.

* De standaardworkflow **DAM Asset Update** in eerdere versies van AEM is niet meer beschikbaar.
* De componenten van de website die een binair **zonder transformatie** leveren zouden directe download moeten gebruiken.
   * De Sling GET servlet is veranderd om dit door gebrek te doen.
* De componenten van de website die een binair **met transformatie** (bijvoorbeeld, resize via servlet) leveren kunnen blijven werken aangezien zij hebben.
* Elementen die via Package Manager worden binnengebracht, moeten handmatig opnieuw worden verwerkt met behulp van de handeling **Element** opnieuw verwerken in de interface Elementen.
