---
title: Experience Manager [!DNL AEM Forms] as a Cloud Service architectuur
description: Begrijp de architectuur van [!DNL AEM Forms] as a Cloud Service om over de scalability, veerkracht, en prestatiesaspecten van het platform te leren.
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '1091'
ht-degree: 5%

---


# [!DNL AEM] as a Cloud Service architectuur {#architecture}

[!DNL AEM Forms] as a Cloud Service standaardiseert de plaatsingsarchitectuur voor alle klanten, met het doel om klanten van architectuuroverwegingen volledig vrij te maken. Terwijl de nieuwe AEM as a Cloud Service architectuur nog steeds afhankelijk is van het concept van microkorrels voor persistentie, hoeven klanten zich bijvoorbeeld niet zorgen te maken over welke microkernel ze moeten kiezen. De microkorrels die zowel op de auteur als op de publicatiezijde worden gebruikt, zijn uniek voor [!DNL AEM Cloud Service] en anderszins niet beschikbaar voor klanten voor installaties op locatie.

AEM as a Cloud Service heeft een dynamische architectuur met een variabel aantal AEM instanties. Het biedt ontwikkelings-, fase-, productie- en demonstratieomgevingen. Het biedt tools voor het beheer van AEM instanties (Cloud Manager), het onderhoud van gebruikers en verificaties (Admin Console en IMS-systeem (Adobe Identity Management)), het configureren van caching (Fastly CDN) en de ontwikkelomgeving in de cloud. Zie voor meer informatie over architectuur [Een inleiding tot de architectuur van [!DNL Adobe Experience Manager as a Cloud Service]](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/core-concepts/architecture.html?lang=en).

## Cloud Manager{#cloud-manager}

Cloud Manager is een essentieel onderdeel van [AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/introduction.html?lang=en). Elke nieuwe huurder van [!DNL AEM Forms] as a Cloud Service wordt eerst ingericht voor toegang tot Cloud Manager. Cloud Manager is het single-entry punt voor de bewerkingen en ontwikkelaars persona van onze klanten. Het is de plaats van waar de AEM programma&#39;s en milieu&#39;s kunnen worden beheerd. Cloud Manager is geëvolueerd als een zelfbedieningsportal waar de belangrijkste componenten van de AEM as a Cloud Service kunnen worden gecreeerd en worden gevormd:

* Programma&#39;s maken en beheren
* De AEM omgevingen binnen de programma&#39;s maken en beheren
* Het creëren van en het leiden van de pijpleidingen voor het opstellen van de klantencode en configuratie aan een bepaalde milieu
* Informatie over belangrijke levenscyclusgebeurtenissen voor deze componenten (bijvoorbeeld productupdates) Voor meer informatie over Cloud Manager raadpleegt u [Adobe Cloud Manager begrijpen](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/cloud-manager/understand-cloud-manager-for-aem.html) en [Inleiding tot Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html).

## Gebruikers en verificatie {#users-and-authentication}

AEM as a Cloud Service omvat de steun van de Admin Console voor AEM instanties en op Adobe Identity Management System (IMS) gebaseerde authentificatie. Met de Admin Console kunnen beheerders alle gebruikers van Experience Cloud centraal beheren. Gebruikers en groepen kunnen worden toegewezen aan productprofielen die zijn gekoppeld aan AEM as a Cloud Service-instanties, zodat ze zich bij deze instantie kunnen aanmelden. Voor meer informatie over gebruikers, authentificatie, en, de toegang tot van een geval van AEM as a Cloud Service, zie [IMS-ondersteuning voor [!DNL Adobe Experience Manager] as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html?lang=en#introduction).

Verschillende personen zijn betrokken bij een typisch [!DNL AEM Forms] project. Nadat u zich bij uw [!DNL AEM Forms] as a Cloud Service instantie, kunt u [gebruikers toevoegen in beheerconsole](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html) voor personen die van toepassing zijn op uw organisatie of project en [gebruikers toewijzen aan geïntegreerde groepen](forms-groups-privileges-tasks.md) om hen vereiste voorrechten te verstrekken.

Verschillende ingebouwde [!DNL AEM Forms] specifieke gebruikersgroepen en rechten beschikbaar op [!DNL AEM Forms] als een Cloud Services-instantie, zie [Configureren, gebruiker, rollen en groepen](forms-groups-privileges-tasks.md).

## Ervaring met ontwikkelaars {#developer-experience}

De nieuwe architectuur die AEM as a Cloud Service steunt brengt enkele zeer belangrijke veranderingen in de algemene ontwikkelaarservaring. Een van de belangrijkste doelstellingen voor de wijzigingen in de ontwikkelaarservaring is om migratie zo snel mogelijk as a Cloud Service te laten AEM, met weinig wijzigingen in bestaande aangepaste code.

## Cloud-ontwikkeling {#cloud-development}

Hier volgen de richtlijnen voor het probleemloos uitvoeren van uw bestaande code in AEM as a Cloud Service omgeving:

* Sla uw code en configuraties op in de Git-opslagplaats van het bijbehorende programma Cloud Manager. Het maakt het beheren en integreren van code met CI/CD een bries.
* Toepassingscode en configuratie compatibel maken met de basislijn [!DNL AEM Forms] afbeeldingen. Met de nieuwste API&#39;s kunt u sneller en veiliger toepassingen maken.
* Gebruik de pijplijn van de Manager van de Wolk verbonden aan het milieu van de Manager van de Wolk om toepassingen te bouwen en op te stellen. Het helpt u om de nieuwste functies en fouten die zijn gecorrigeerd voor [!DNL AEM Forms] as a Cloud Service voor uw omgeving.
* Probeer dat uw douanetoepassingen alle codekwaliteit, veiligheid, en prestatiespoorten overgaan die in de pijpleiding worden afgedwongen. Het helpt veilige en beter presterende toepassingen te bouwen die tot betere klantenervaring leiden. U kunt altijd de interface van Cloud Manager gebruiken om bepaalde controles over te slaan.
Dit proces wordt meestal &#39;cloud-first&#39;-ontwikkeling genoemd. [!DNL AEM Forms] as a Cloud Service verstrekt ook een SDK om snelle ontwikkeling te steunen alvorens de hangende code en configuratieveranderingen in de wolk worden geprobeerd.
Sommige interfaces die eerder deel uitmaakten van AEM QuickStart zijn niet meer beschikbaar voor de gebruikers van de AEM as a Cloud Service omgeving. Bijvoorbeeld, de Console van het Web waar de bundels OSGI en hun bijbehorende configuratie worden beheerd. De browser van de gegevensopslagplaats voor CRXDE Lite-inhoud is alleen toegankelijk voor omgevingstypen die niet voor productie zijn bedoeld. Een ondergroep van de functionaliteit van de Console van het Web die de ontwikkelaars vereisen, vooral wanneer het over diagnostiek en statusdoeleinden komt, wordt beschikbaar gemaakt via een nieuwe ontwikkelaarsconsole.
Bovendien is snelle toegang tot de logbestanden van de verschillende omgevingen een van de meest voorkomende vereisten voor ontwikkelaars. Met [!DNL AEM Cloud Service]De logbestanden van de verschillende knooppunten in Auteur, Publish, worden beschikbaar gesteld via Cloud Manager, hetzij in de vorm van bestanden die kunnen worden gedownload hetzij via API&#39;s voor het bijhouden van de logbestanden. Vanwege de duidelijke scheiding tussen code en inhoud kunnen ontwikkelaars een bepaald proces gebruiken voor het bijwerken van inhoud als onderdeel van een implementatie. Vaak voorkomende gebruiksgevallen van veranderlijke content zijn:
* Standaard &quot;standaard&quot;inhoud die deel van het klantenproject uitmaakt (b.v. omslagen, malplaatjes, werkschema&#39;s...)
* Zoekindexdefinities
* ACL&#39;s en toestemmingen
* Servicegebruikers en -gebruikersgroepen
Stel uw ontwikkelomgeving in. [Uw CI/CD-pijplijn configureren](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html)en leren [uw code implementeren](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html) inzake het milieu.

## Lokale ontwikkeling {#local-development}

Wanneer u opstelling en vormt [!DNL AEM Forms] as a Cloud Service omgeving, stelt u ontwikkelings-, staging- en productieomgevingen in. Bovendien moet u een lokale ontwikkelomgeving instellen en configureren voor snelle iteraties en ontwikkeling. U kunt SDK downloaden en instellen AEM [!DNL AEM Forms] add-on functiearchief om een lokale [!DNL Forms] as a Cloud Service ontwikkelomgeving.  Zie voor gedetailleerde instructies [Een lokale ontwikkelomgeving instellen](setup-local-development-environment.md).

## Foutopsporing {#debugging}

AEM as a Cloud Service runnen op zelfbediening, schaalbare cloudinfrastructuur. Het vereist AEM ontwikkelaars om diverse facetten van AEM as a Cloud Service te begrijpen en te zuiveren, van bouw en opstelling aan het verkrijgen van details van het runnen van AEM toepassingen. Zie voor meer informatie [Foutopsporing AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/overview.html?lang=en).
