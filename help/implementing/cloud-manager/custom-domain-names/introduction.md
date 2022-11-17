---
title: Inleiding tot aangepaste domeinnamen
description: Met de gebruikersinterface van Cloud Manager kunt u een aangepast domein toevoegen om uw site op een zelfbediening te identificeren aan de hand van een unieke merknaam.
exl-id: ed03bff9-dfcc-4dfe-a501-a7facd24aa7d
source-git-commit: 42318a42a55134501eb13feca22791bb5db4e83f
workflow-type: tm+mt
source-wordcount: '665'
ht-degree: 1%

---


# Inleiding tot aangepaste domeinnamen {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_domains"
>title="Aangepaste domeinnamen beheren"
>abstract="Met de gebruikersinterface van Cloud Manager kunt u een aangepast domein toevoegen om uw site op een zelfbediening te identificeren aan de hand van een unieke merknaam."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/custom-domain-names/add-custom-domain-name.html" text="Een aangepaste domeinnaam toevoegen"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/custom-domain-names/view-update-replace-custom-domain-name.html" text="Aangepaste domeinnaam weergeven en bijwerken"

Met de gebruikersinterface van Cloud Manager kunt u een aangepast domein toevoegen om uw site op een zelfbediening te identificeren aan de hand van een unieke merknaam. Adobe Experience Manager as a Cloud Service heeft een standaarddomeinnaam, die eindigt in `*.adobeaemcloud.com`. Deze standaarddomeinnaam blijft behouden, zelfs nadat u aangepaste domeinnamen aan uw website hebt gekoppeld.

## Wat zijn aangepaste domeinnamen? {#what-are-custom-domain-names}

Elke website heeft een uniek, machineleesbaar numeriek adres, zoals `184.33.123.64`. Het systeem van de Naam van het Domein (DNS) is wat u toestaat om douane te hebben, brandde domeinen in bijlage aan websites door numerieke adressen in memorabele adressen zoals te vertalen `wknd.com`.

Het is aan te raden een domeinnaam voor uw site te hebben die voor uw klanten te onthouden is en die uw merk weerspiegelt.

U kunt een domeinnaam kopen van een registrar van domeinnamen, een bedrijf of organisatie die domeinnamen beheert en verkoopt. Domeinnaamregistrars beheren domeinnamen op DNS-servers.

>[!IMPORTANT]
>
>Cloud Manager is geen registrar voor domeinnamen en biedt geen DNS-services.

## Beperkingen {#limitations}

Er gelden een aantal beperkingen voor het gebruik van aangepaste domeinnamen met AEMaaCS.

* Aangepaste domeinnamen worden ondersteund in Cloud Manager voor zowel de publicatieservices als de voorvertoningsservices voor Sites-programma&#39;s. Aangepaste domeinen aan de zijde van de auteur worden niet ondersteund.
* Elke Cloud Manager-omgeving kan maximaal 500 aangepaste domeinen per omgeving hosten.
* AEM as a Cloud Service ondersteunt geen jokertekendomeinen.
* Voordat u een aangepaste domeinnaam kunt toevoegen, moet een geldig SSL-certificaat met de aangepaste domeinnaam voor uw programma zijn geïnstalleerd. Raadpleeg Een SSL-certificaat toevoegen voor meer informatie.
* De namen van het domein kunnen niet aan milieu&#39;s worden toegevoegd terwijl er een huidige lopende pijpleiding verbonden aan die milieu&#39;s is.
* Er kan slechts één domeinnaam tegelijk worden toegevoegd.
* Dezelfde domeinnaam kan niet op meer dan één omgeving worden gebruikt.

>[!NOTE]
>
>Aangepaste domeinen worden ondersteund in Cloud Manager **alleen** als u AEM beheerde CDN gebruikt. Als u uw eigen CDN en [wijs het aan AEM beheerde CDN](/help/implementing/dispatcher/cdn.md) u moet die specifieke CDN gebruiken om domeinen te beheren die geen Cloud Manager zijn.

## Workflow {#workflow}

Voor het toevoegen van een aangepaste domeinnaam is interactie tussen de DNS-service en Cloud Manager vereist. Wegens dit zijn er een aantal stappen die worden vereist om, de namen van het douanedomein te installeren te vormen en te verifiëren. In de volgende tabel vindt u een overzicht van de vereiste stappen, inclusief wat u moet doen als er algemene fouten optreden.

| Stap | Beschrijving | Verantwoordelijkheid | Meer informatie |
|--- |--- |--- |---|
| 1 | SSL-certificaat toevoegen aan Cloud Manager | Klant | [Een SSL-certificaat toevoegen](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) |
| 2 | TXT-record toevoegen om domein te verifiëren | Klant | [Een TXT-record toevoegen](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) |
| 3 | Status domeinverificatie controleren | Klant | [Status domeinnaam controleren](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) |
| 3 bis. | Als domeinverificatie mislukt met de status `Domain Verification Failure` | Klant | [Status domeinnaam controleren](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) |
| 3 ter | Als domeinverificatie mislukt met de status `Verified, Deployment Failed`, contact Adobe | Adobe Klantenservice | [Status domeinnaam controleren](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) |
| 4 | DNS-instellingen configureren door DNS CNAME- of APEX-records toe te voegen die wijzen naar AEM as a Cloud Service | Klant | [DNS-instellingen configureren](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) |
| 5 | DNS-recordstatus controleren | Klant | [DNS-recordstatus controleren](/help/implementing/cloud-manager/custom-domain-names/check-dns-record-status.md) |
| 5 bis | Als de DNS-recordstatus mislukt met `DNS status not detected` | Klant | [DNS-recordstatus controleren](/help/implementing/cloud-manager/custom-domain-names/check-dns-record-status.md) |
| 5 ter | Als de DNS-recordstatus mislukt met `DNS resolves incorrectly` | Klant | [DNS-recordstatus controleren](/help/implementing/cloud-manager/custom-domain-names/check-dns-record-status.md) |

>[!TIP]
>
>Het instellen van aangepaste domeinnamen met AEM als cloudservice is doorgaans een eenvoudig proces. Nochtans bij gelegenheid kunnen de kwesties van de domeindelegatie voorkomen die 1 tot 2 werkdagen kunnen vergen om op te lossen. Daarom wordt het ten zeerste aanbevolen de domeinen ruim vóór hun live datum te installeren. Zie het document [Status domeinnaam controleren](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) voor meer informatie .
