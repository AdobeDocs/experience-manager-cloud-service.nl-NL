---
title: Inleiding tot het beheren van SSL-certificaten
description: Leer hoe u in Cloud Manager zelfbedieningsgereedschappen hebt om SSL-certificaten te installeren.
exl-id: 0d41723c-c096-4882-a3fd-050b7c9996d8
source-git-commit: f7525b6b37e486a53791c2331dc6000e5248f8af
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 0%

---


# Inleiding tot het beheren van SSL-certificaten{#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_sslcert"
>title="SSL-certificaten beheren"
>abstract="Leer hoe u met Cloud Manager zelfservicegereedschappen hebt om SSL-certificaten te installeren en te beheren om uw site voor uw gebruikers te beveiligen. Cloud Manager gebruikt een platform-TLS-service voor het beheer van SSL-certificaten en persoonlijke sleutels die eigendom zijn van klanten en die zijn verkregen van certificeringsinstanties van derden."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/managing-certificates.html" text="Een SSL-certificaat weergeven, bijwerken en vervangen"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/managing-certificates.html" text="Status van een SSL-certificaat controleren"

Cloud Manager biedt u zelfbedieningsgereedschappen om SSL-certificaten te installeren en te beheren, zodat u uw site voor uw gebruikers kunt beveiligen. Cloud Manager gebruikt een platform-TLS-service voor het beheer van SSL-certificaten en persoonlijke sleutels die eigendom zijn van klanten en die zijn verkregen van certificeringsinstanties van derden, zoals Let&#39;s Encrypt.

## Inleiding tot certificaten {#certificates}

Bedrijven gebruiken SSL-certificaten om hun websites te beveiligen en hun klanten in staat te stellen er vertrouwen in te stellen. Voor gebruik van het SSL-protocol vereist een webserver het gebruik van een SSL-certificaat.

Wanneer een entiteit een certificaat aanvraagt bij een certificeringsinstantie, voltooit de certificeringsinstantie een verificatieproces. Dit kan zich van het verifiëren van domeinnaamcontrole tot het verzamelen van de documenten van de bedrijfregistratie en abonneeovereenkomsten uitstrekken. Zodra de informatie van een entiteit is geverifieerd, zal de CA hun openbare sleutel ondertekenen gebruikend de privé sleutel van CA. Omdat alle belangrijke certificeringsinstanties basiscertificaten hebben in webbrowsers, wordt het certificaat van de entiteit gekoppeld via een *vertrouwensketen* en de webbrowser herkent het als een vertrouwd certificaat.

>[!IMPORTANT]
>
>Cloud Manager biedt geen SSL-certificaten of persoonlijke sleutels. Deze moeten worden verkregen van certificeringsinstanties (CA&#39;s).

## SSL-beheerfuncties van Cloud Manager {#features}

Cloud Manager ondersteunt de volgende gebruiksopties voor SSL-certificaten van klanten.

* Een SSL-certificaat kan door meerdere omgevingen worden gebruikt. Dit wil zeggen dat het eenmaal kan worden toegevoegd en meerdere keren kan worden gebruikt.
* Elke Cloud Manager-omgeving kan meerdere certificaten gebruiken.
* Een persoonlijke sleutel kan meerdere SSL-certificaten uitgeven.
* Elk certificaat bevat gewoonlijk meerdere domeinen.
* De platformTLS de dienstroutes verzoeken aan de dienst CDN van de klant die op het SSL certificaat wordt gebaseerd dat wordt gebruikt om te eindigen en de dienst CDN die gastheren dat domein.
* AEM as a Cloud Service accepteert SSL-jokertekens voor een domein.

## Recommendations {#recommendations}

AEM alleen as a Cloud Service ondersteunt veilige `https` sites.

* Klanten met meerdere aangepaste domeinen willen niet telkens wanneer zij een domein toevoegen, een certificaat uploaden.
* Dergelijke klanten profiteren door één certificaat met veelvoudige domeinen te krijgen.

## Vereisten {#requirements}

* AEM as a Cloud Service accepteert alleen certificaten die voldoen aan het OV- (Organisatie-validatie) of EV-beleid (Extended Validation).
* Elk certificaat moet een X.509 TLS-certificaat zijn van een vertrouwde certificeringsinstantie (CA) met een overeenkomende persoonlijke RSA-sleutel van 2048 bits.
* Het DV-beleid (Domain Validation) wordt niet geaccepteerd.
* Zelfondertekende certificaten worden niet geaccepteerd.

OV- en EV-certificaten bieden gebruikers extra door CA gevalideerde informatie die kan worden gebruikt om te bepalen of de eigenaar van een website, de afzender van een e-mail of de digitale handtekening van uitvoerbare code of PDF-documenten betrouwbaar is. DV-certificaten staan een dergelijke eigendomsverificatie niet toe.

## Beperkingen {#limitations}

Cloud Manager staat op elk gewenst moment maximaal 50 SSL-certificaten toe. Deze kunnen aan één of meerdere milieu&#39;s over uw programma worden geassocieerd en ook om het even welke verlopen certificaten omvatten.

Als u de limiet hebt bereikt, controleert u uw certificaten en overweegt u:

* Verlopen certificaten verwijderen.
* Meerdere domeinen in hetzelfde certificaat groeperen, aangezien een certificaat meerdere domeinen kan bestrijken (maximaal 100 SAN&#39;s).

## Meer informatie {#learn-more}

Een gebruiker met de vereiste machtigingen kan Cloud Manager gebruiken om SSL-certificaten voor een programma te beheren. Raadpleeg de volgende documenten voor meer informatie over deze functies.

* [Een SSL-certificaat toevoegen](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md)
* [Een SSL-certificaat weergeven, bijwerken of vervangen](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md)
* [Een SSL-certificaat verwijderen](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md)
