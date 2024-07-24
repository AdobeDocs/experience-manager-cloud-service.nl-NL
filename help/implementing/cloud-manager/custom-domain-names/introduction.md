---
title: Inleiding tot aangepaste domeinnamen
description: Met de gebruikersinterface van Cloud Manager kunt u een aangepast domein toevoegen om uw site op een zelfbedieningswijze te identificeren aan de hand van een unieke merknaam.
exl-id: ed03bff9-dfcc-4dfe-a501-a7facd24aa7d
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 1c9924b4477d53d86bb72eda8597a02304450195
workflow-type: tm+mt
source-wordcount: '722'
ht-degree: 1%

---


# Inleiding tot aangepaste domeinnamen {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_domains"
>title="Aangepaste domeinnamen beheren"
>abstract="Met de gebruikersinterface van Cloud Manager kunt u een aangepast domein toevoegen om uw site op een zelfbedieningswijze te identificeren aan de hand van een unieke merknaam."
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/custom-domain-names/add-custom-domain-name" text="Een aangepaste domeinnaam toevoegen"
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/custom-domain-names/managing-custom-domain-names" text="Aangepaste domeinnaam weergeven en bijwerken"

Adobe Experience Manager as a Cloud Service wordt voorzien van een standaarddomeinnaam, eindigend in `*.adobeaemcloud.com`. Met de gebruikersinterface van Cloud Manager kunt u een aangepast domein toevoegen om uw site op een zelfbedieningswijze te identificeren aan de hand van een unieke merknaam. De standaarddomeinnaam `*.adobeaemcloud.com` blijft behouden, zelfs nadat u aangepaste domeinnamen aan uw website hebt gekoppeld.

## Wat zijn aangepaste domeinnamen? {#what-are-custom-domain-names}

Elke website heeft een uniek, machineleesbaar numeriek adres, zoals `184.33.123.64`. Het systeem van de Naam van het Domein (DNS) is wat u douane, merkdomeinen in bijlage aan websites door numerieke adressen in memorabele adressen zoals `wknd.com` te vertalen laat hebben.

Het is een goede gewoonte om een domeinnaam voor uw site te hebben die voor uw klanten te onthouden is en die uw merk weerspiegelt.

U kunt een domeinnaam kopen van een registrar van domeinnamen, een bedrijf of organisatie die domeinnamen beheert en verkoopt. Domeinnaamregistrars beheren domeinnamen op DNS-servers.

>[!IMPORTANT]
>
>Cloud Manager is geen registrar voor domeinnamen en biedt geen DNS-services.

## Aangepaste domeinnamen en BYO CDN&#39;s {#byo-cdn}

AEM as a Cloud Service biedt de ingebouwde dienst van het netwerk van de inhoudslevering (CDN) aan, maar laat u ook uw-uw-eigen (BYO) CDN aan gebruik met AEM brengen. Aangepaste domeinen kunnen worden geïnstalleerd in de CDN met AEM beheer of in een CDN die u beheert.

* De domeinnamen van de douane (en certificaten) die in AEM-beheerde CDN worden geïnstalleerd worden beheerd via Cloud Manager.
* De domeinnamen van de douane (en certificaten) die in uw eigen CDN worden geïnstalleerd worden beheerd in die specifieke CDN.

**Domeinen die in uw eigen CDN worden beheerd te hoeven niet om door Cloud Manager worden geïnstalleerd.** Ze worden beschikbaar gesteld aan AEM via X-Forwarded-Host en komen overeen met de hosts die zijn gedefinieerd in de Dispatcher. Zie de [ CDN documentatie.](/help/implementing/dispatcher/cdn.md)

In één milieu kunt u beide domeinen hebben die in AEM-beheerde CDN worden geïnstalleerd en in uw eigen CDN worden geïnstalleerd.

## Workflow {#workflow}

Voor het toevoegen van een aangepaste domeinnaam is interactie tussen de DNS-service en Cloud Manager vereist. Wegens dit zijn er verscheidene stappen die worden vereist om de namen van het douanedomein te installeren, te vormen en te verifiëren. In de volgende tabel vindt u een overzicht van de vereiste stappen, waaronder koppelingen naar documentatiebronnen om deze stappen te voltooien.

| Stap | Beschrijving | Documentatie |
|---|---|---|
| 1 | SSL-certificaat toevoegen aan Cloud Manager | [ Toevoegend een SSL Certificaat ](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) |
| 2 | Aangepast domein toevoegen aan Cloud Manager | [ Toevoegend een Naam van het Domein van de Douane ](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) |
| 3 | TXT-record toevoegen om domein te verifiëren | [ Toevoegend een Verslag TXT ](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) |
| 4 | Status van domeinverificatie controleren | [ Controlerend de Status van de Naam van het Domein ](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) |
| 5 | DNS-instellingen configureren door DNS CNAME- of APEX-records toe te voegen die naar AEM as a Cloud Service wijzen | [ Vormend DNS Montages ](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) |
| 6 | DNS-recordstatus controleren | [ het Controleren DNS Status van het Verslag ](/help/implementing/cloud-manager/custom-domain-names/check-dns-record-status.md) |

>[!TIP]
>
>Het instellen van aangepaste domeinnamen met AEM als cloudservice is doorgaans een eenvoudig proces. Nochtans, in geval van domeindomeindelegatie kunnen de kwesties voorkomen die 1 tot 2 werkdagen kunnen vergen om op te lossen. Daarom wordt het ten zeerste aanbevolen de domeinen ruim vóór hun live datum te installeren. Zie het document [ Controlerend de Status van de Naam van het Domein ](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) voor meer informatie.

## Beperkingen {#limitations}

Er gelden verschillende beperkingen voor het gebruik van aangepaste domeinnamen met AEMaaCS.

* Aangepaste domeinnamen worden in Cloud Manager alleen ondersteund voor publicatie- en voorvertoningsservices voor Sites-programma&#39;s.
   * Aangepaste domeinen voor auteursservices worden niet ondersteund.
* Elke Cloud Manager-omgeving kan maximaal 500 aangepaste domeinen per omgeving hosten.
* De namen van het domein kunnen niet aan milieu&#39;s worden toegevoegd terwijl er een huidige lopende pijpleiding in bijlage aan die milieu&#39;s is.
* Dezelfde domeinnaam kan niet op meer dan één omgeving worden gebruikt.
* Er kan slechts één domeinnaam tegelijk worden toegevoegd.
* AEM as a Cloud Service ondersteunt geen jokertekendomeinen zoals `*.example.com` .
* Voordat u een aangepaste domeinnaam kunt toevoegen, moet een geldig SSL-certificaat met de aangepaste domeinnaam (jokertekens zijn geldig) voor uw programma zijn geïnstalleerd.

## Aan de slag! {#get-started}

* Krijg begonnen een nieuwe naam van het douanedomein voor uw project te vormen door een SSL certificaat toe te voegen.](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md)[
* Beheer uw bestaande domeinnamen door het document [ te herzien Managing de Namen van het Domein van de Douane.](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md)
