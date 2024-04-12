---
title: Inleiding tot aangepaste domeinnamen
description: Met de gebruikersinterface van Cloud Manager kunt u een aangepast domein toevoegen om uw site op een zelfbedieningswijze te identificeren met een unieke merknaam.
exl-id: ed03bff9-dfcc-4dfe-a501-a7facd24aa7d
source-git-commit: d9cd10772252d80487f578ee73f40ec334600029
workflow-type: tm+mt
source-wordcount: '741'
ht-degree: 0%

---


# Inleiding tot aangepaste domeinnamen {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_domains"
>title="Aangepaste domeinnamen beheren"
>abstract="Met de gebruikersinterface van Cloud Manager kunt u een aangepast domein toevoegen om uw site op een zelfbedieningswijze te identificeren met een unieke merknaam."
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/custom-domain-names/add-custom-domain-name" text="Een aangepaste domeinnaam toevoegen"
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/custom-domain-names/managing-custom-domain-names" text="Aangepaste domeinnaam weergeven en bijwerken"

Met de gebruikersinterface van Cloud Manager kunt u een aangepast domein toevoegen om uw site op een zelfbedieningswijze te identificeren met een unieke merknaam. Adobe Experience Manager as a Cloud Service heeft een standaarddomeinnaam, die eindigt in `*.adobeaemcloud.com`. Deze standaarddomeinnaam blijft behouden, zelfs nadat u aangepaste domeinnamen aan uw website hebt gekoppeld.

## Wat zijn aangepaste domeinnamen? {#what-are-custom-domain-names}

Elke website heeft een uniek, machineleesbaar numeriek adres, zoals `184.33.123.64`. Het systeem van de Naam van het Domein (DNS) is wat u douane, brandde domeinen in bijlage aan websites door numerieke adressen in memorabele adressen zoals te vertalen `wknd.com`.

Het is aan te raden een domeinnaam voor uw site te hebben die voor uw klanten te onthouden is en die uw merk weerspiegelt.

U kunt een domeinnaam kopen van een registrar van domeinnamen, een bedrijf of organisatie die domeinnamen beheert en verkoopt. Domeinnaamregistrars beheren domeinnamen op DNS-servers.

>[!IMPORTANT]
>
>Cloud Manager is geen registrar voor domeinnamen en biedt geen DNS-services.

## Aangepaste domeinnamen en BYO CDN&#39;s {#byo-cdn}

AEM as a Cloud Service biedt de ingebouwde dienst van het netwerk van de inhoudslevering (CDN) aan, maar laat u ook uw-uw-eigen (BYO) CDN aan gebruik met AEM brengen. Aangepaste domeinen kunnen worden geïnstalleerd in de CDN met AEM beheer of in een CDN die u beheert.

* Aangepaste domeinnamen (en certificaten) die in de door AEM beheerde CDN zijn geïnstalleerd, worden beheerd via Cloud Manager.
* De domeinnamen van de douane (en certificaten) die in uw eigen CDN worden geïnstalleerd worden beheerd in die specifieke CDN.

Domeinen die in uw eigen CDN worden beheerd, hoeven niet via Cloud Manager te worden geïnstalleerd. Zij worden ter beschikking gesteld aan AEM als x-Door:sturen-Gastheer en passen de gastheren aan die in de Verzender worden bepaald. Zie de [CDN-documentatie](/help/implementing/dispatcher/cdn.md).

In één milieu kunt u beide domeinen hebben die in AEM-beheerde CDN worden geïnstalleerd en in uw eigen CDN worden geïnstalleerd.

## Workflow {#workflow}

Voor het toevoegen van een aangepaste domeinnaam is interactie tussen de DNS-service en Cloud Manager vereist. Wegens dit zijn er verscheidene stappen die worden vereist om, douanedomeinamen te installeren te vormen en te verifiëren. In de volgende tabel vindt u een overzicht van de vereiste stappen, inclusief wat u moet doen als er algemene fouten optreden.

| Stap | Beschrijving | Verantwoordelijkheid | Meer informatie |
|--- |--- |--- |---|
| 1 | SSL-certificaat toevoegen aan Cloud Manager | Klant | [Een SSL-certificaat toevoegen](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) |
| 2 | TXT-record toevoegen om domein te verifiëren | Klant | [Een TXT-record toevoegen](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) |
| 3 | Status domeinverificatie controleren | Klant | [Status domeinnaam controleren](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) |
| 3 bis. | Als domeinverificatie mislukt met de status `Domain Verification Failure` | Klant | [Status domeinnaam controleren](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) |
| 3 ter | Als domeinverificatie mislukt met de status `Verified, Deployment Failed`, contact opnemen met Adobe | Klantenservice Adoben | [Status domeinnaam controleren](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) |
| 4 | DNS-instellingen configureren door DNS CNAME- of APEX-records toe te voegen die wijzen naar AEM as a Cloud Service | Klant | [DNS-instellingen configureren](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) |
| 5 | DNS-recordstatus controleren | Klant | [DNS-recordstatus controleren](/help/implementing/cloud-manager/custom-domain-names/check-dns-record-status.md) |
| 5 bis | Als de DNS-recordstatus mislukt met `DNS status not detected` | Klant | [DNS-recordstatus controleren](/help/implementing/cloud-manager/custom-domain-names/check-dns-record-status.md) |
| 5 ter | Als de DNS-recordstatus mislukt met `DNS resolves incorrectly` | Klant | [DNS-recordstatus controleren](/help/implementing/cloud-manager/custom-domain-names/check-dns-record-status.md) |

>[!TIP]
>
>Het instellen van aangepaste domeinnamen met AEM als cloudservice is doorgaans een eenvoudig proces. Nochtans bij gelegenheid kunnen de kwesties van de domeindelegatie voorkomen die 1 tot 2 werkdagen kunnen vergen om op te lossen. Daarom wordt het ten zeerste aanbevolen de domeinen ruim vóór hun live datum te installeren. Zie het document [Status domeinnaam controleren](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) voor meer informatie .

## Beperkingen {#limitations}

Er gelden verschillende beperkingen voor het gebruik van aangepaste domeinnamen met AEMaaCS.

* Aangepaste domeinnamen worden ondersteund in Cloud Manager voor zowel publicatie- als voorvertoningsservices voor Sites-programma&#39;s. Aangepaste domeinen voor auteursservices worden niet ondersteund.
* Elke Cloud Manager-omgeving kan maximaal 500 aangepaste domeinen per omgeving hosten.
* Domeinnamen kunnen niet aan omgevingen worden toegevoegd terwijl er een actieve pijpleiding aan die omgevingen is gekoppeld.
* Dezelfde domeinnaam kan niet op meer dan één omgeving worden gebruikt.
* Er kan slechts één domeinnaam tegelijk worden toegevoegd.
* AEM as a Cloud Service ondersteunt geen jokertekendomeinen zoals `*.example.com`.
* Voordat u een aangepaste domeinnaam kunt toevoegen, moet een geldig SSL-certificaat met de aangepaste domeinnaam (jokertekens zijn geldig) voor uw programma zijn geïnstalleerd. Zie [Een SSL-certificaat toevoegen](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) voor meer informatie.
