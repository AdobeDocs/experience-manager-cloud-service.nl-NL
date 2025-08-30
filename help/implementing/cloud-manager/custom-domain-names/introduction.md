---
title: Inleiding tot aangepaste domeinnamen
description: Met de gebruikersinterface van Cloud Manager kunt u een aangepast domein toevoegen om uw site op een zelfbedieningswijze te identificeren aan de hand van een unieke merknaam.
exl-id: ed03bff9-dfcc-4dfe-a501-a7facd24aa7d
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: fdd86b966f0480c00b7cd975d63a48b82fb1d027
workflow-type: tm+mt
source-wordcount: '698'
ht-degree: 1%

---


# Inleiding tot aangepaste domeinnamen {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_domains"
>title="Aangepaste domeinnamen beheren"
>abstract="Met de gebruikersinterface van Cloud Manager kunt u een aangepast domein toevoegen om uw site op een zelfbedieningswijze te identificeren aan de hand van een unieke merknaam."
>additional-url="https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/custom-domain-names/add-custom-domain-name" text="Een aangepaste domeinnaam toevoegen"
>additional-url="https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/custom-domain-names/managing-custom-domain-names" text="Aangepaste domeinnaam weergeven en bijwerken"

Adobe Experience Manager as a Cloud Service wordt voorzien van een standaarddomeinnaam, eindigend in `*.adobeaemcloud.com`. Met de gebruikersinterface van Cloud Manager kunt u een aangepast domein toevoegen om uw site op een zelfbedieningswijze te identificeren aan de hand van een unieke merknaam. De standaarddomeinnaam `*.adobeaemcloud.com` blijft behouden, zelfs nadat u aangepaste domeinnamen aan uw website hebt gekoppeld.

## Wat zijn aangepaste domeinnamen? {#what-are-custom-domain-names}

Elke website heeft een uniek, machineleesbaar numeriek adres, zoals `184.33.123.64`. Het systeem van de Naam van het Domein (DNS) is wat u douane, merkdomeinen in bijlage aan websites door numerieke adressen in memorabele adressen zoals `wknd.com` te vertalen laat hebben.

Het is een goede gewoonte om een domeinnaam voor uw site te hebben die voor uw klanten te onthouden is en die uw merk weerspiegelt.

U kunt een domeinnaam kopen van een registrar van domeinnamen, een bedrijf of organisatie die domeinnamen beheert en verkoopt. Domeinnaamregistrars beheren domeinnamen op DNS-servers.

>[!IMPORTANT]
>
>Cloud Manager is geen registrar voor domeinnamen en biedt geen DNS-services.

## Aangepaste domeinnamen en breng uw eigen CDN&#39;s {#byo-cdn}

AEM as a Cloud Service biedt een ingebouwde CDN-service (Content Delivery Network), maar biedt u ook de mogelijkheid om CDN (Thuis brengen) voor gebruik met AEM te gebruiken. Aangepaste domeinen kunnen worden geïnstalleerd in de door AEM beheerde CDN of in een CDN die u beheert.

* Cloud Manager beheert aangepaste domeinnamen en certificaten die in de door AEM beheerde CDN zijn geïnstalleerd.
* De domeinnamen en de certificaten van de douane die in een BYO CDN worden geïnstalleerd worden beheerd direct binnen die CDN.

**Domeinen die in uw eigen CDN worden beheerd vereisen geen installatie door Cloud Manager** - zij worden ter beschikking gesteld aan AEM als x-Door:sturen-Gastheer en passen de gastheren aan die in Dispatcher worden bepaald. Zie de [ CDN documentatie ](/help/implementing/dispatcher/cdn.md).

In één milieu, kunt u beide domeinen hebben die in AEM-Beheerde CDN worden geïnstalleerd en in een CDN BYO worden geïnstalleerd.

## Workflow {#workflow}

Voor het toevoegen van een aangepaste domeinnaam is interactie tussen de DNS-service en Cloud Manager vereist. Vanwege deze workflow zijn er verschillende stappen vereist voor het installeren, configureren en verifiëren van aangepaste domeinnamen. In de volgende tabel worden de vereiste stappen beschreven, met koppelingen naar de documentatiebronnen om die stappen te voltooien.

>[!WARNING]
>
>Stap 4 van de looppas (vorm DNS) *slechts nadat* Stap 3 (voeg domeinafbeelding toe) met succes heeft voltooid. Na deze orde registreert het domein met Adobe CDN en plaatst - omhoog het correcte verpletteren, beschermend uw plaats tegen domeinovernames.

| Stap | Beschrijving |
| --- | --- |
| 1 | [ voeg SSL certificaat ](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) toe |
| 2 | [ voeg een douanedomein ](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) toe |
| 3 | [ voeg domeinafbeelding ](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) toe |
| 4 | [ vorm DNS ](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md#config-dns) |
| 5 | [ DNS van de Controle status ](/help/implementing/cloud-manager/custom-domain-names/check-dns-record-status.md) |

>[!TIP]
>
>Het instellen van aangepaste domeinnamen met AEM als cloudservice is doorgaans een eenvoudig proces. Soms kunnen echter problemen met domeindelegatie optreden die 1 tot 2 werkdagen in beslag kunnen nemen om op te lossen. Daarom wordt aangeraden de domeinen ruim vóór hun live datum te installeren. Zie het document [ status van de domeinnaam van de Controle ](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) voor meer informatie.

## Gebruiksnotities {#usage-notes}

* Aangepaste domeinnamen worden in Cloud Manager alleen ondersteund voor publicatie- en voorvertoningsservices voor Sites-programma&#39;s.
   * Aangepaste domeinen voor auteursservices worden niet ondersteund.
* Elke Cloud Manager-omgeving kan maximaal 500 aangepaste domeinen per omgeving hosten.
* De namen van het domein kunnen niet aan milieu&#39;s worden toegevoegd terwijl er een huidige lopende pijpleiding in bijlage aan die milieu&#39;s is.
* Dezelfde domeinnaam kan niet in meer dan één omgeving worden gebruikt.
* Er kan slechts één domeinnaam tegelijk worden toegevoegd.
* AEM as a Cloud Service ondersteunt geen jokertekendomeinen zoals `*.example.com` .
* Voordat u een aangepaste domeinnaam kunt toevoegen, moet een geldig SSL-certificaat met de aangepaste domeinnaam (jokertekens zijn geldig) voor uw programma zijn geïnstalleerd.
* De extra configuratiestappen worden vereist om een naam van het douanedomein met [ de Voorste-Eind eigenschap van de Pijpleiding ](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md#custom-domains) te gebruiken.

## Aan de slag {#get-started}

* Krijg begonnen een nieuwe naam van het douanedomein voor uw project te vormen door een SSL certificaat [ toe te voegen.](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md)
* Beheer uw bestaande domeinnamen door het document [ te herzien beheert de namen van het douanedomein ](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md).
