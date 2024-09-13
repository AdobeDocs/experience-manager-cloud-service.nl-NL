---
title: Inleiding tot het beheren van SSL-certificaten
description: Leer hoe u met Cloud Manager zelfbedieningstools SSL-certificaten kunt installeren.
exl-id: 0d41723c-c096-4882-a3fd-050b7c9996d8
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: bc9aa376a402a55191e153f662262ff65df32f5e
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 0%

---


# Inleiding tot het beheren van SSL-certificaten{#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_sslcert"
>title="SSL-certificaten beheren"
>abstract="Leer hoe u met Cloud Manager zelfbedieningstools SSL-certificaten kunt installeren en beheren om uw site voor uw gebruikers te beveiligen. Cloud Manager gebruikt een platform-TLS-service voor het beheer van SSL-certificaten en persoonlijke sleutels die eigendom zijn van klanten en die zijn verkregen van certificeringsinstanties van derden."
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/managing-certificates" text="Een SSL-certificaat weergeven, bijwerken en vervangen"
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/managing-certificates" text="Status van een SSL-certificaat controleren"


Cloud Manager biedt zelfbedieningsgereedschappen voor het installeren en beheren van SSL-certificaten (Secure Socket Layer), zodat de sitebeveiliging voor uw gebruikers gegarandeerd is. De volgende twee gebruiksgevallen worden ondersteund:

<!-- CQDOC-21758, #1 -->

| | Hoofdletters gebruiken | Beschrijving |
| --- | --- | --- |
| 1 | **Adobe beheerde certificaat (DV)** | Met Cloud Manager kunnen gebruikers een DV-certificaat (Domain Validation) configureren dat afkomstig is van Adobe voor snelle domeininstallatie. DV-certificaten zijn het meest elementaire niveau van SSL-certificering en worden vaak gebruikt voor testdoeleinden of voor het beveiligen van websites met basiscodering. DV de certificaten zijn beschikbaar in zowel [ productieprogramma&#39;s als zandbakprogramma&#39;s ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md). Nadat het DV-certificaat is gemaakt, wordt dit door de Adobe automatisch elke drie maanden vernieuwd, tenzij het wordt verwijderd. |
| 2 | **Klant beheerde certificaat (OV/EV)** | Cloud Manager gebruikt de dienst van platformTLS (de Veiligheid van de Laag van het Vervoer) om klant-bezeten SSL certificaten en privé sleutels van de Autoriteiten van het Certificaat van de derde te beheren, zoals *laten versleutelen*. |

>[!NOTE]
>
>Klanten mogen geen DV-certificaten (Domain Validation) uploaden.


## Inleiding tot certificaten {#certificates}

Bedrijven en organisaties gebruiken SSL-certificaten om hun websites te beveiligen en hun klanten in staat te stellen er vertrouwen in te stellen. Voor gebruik van het SSL-protocol vereist een webserver het gebruik van een SSL-certificaat.

Wanneer een entiteit, zoals een organisatie of bedrijf, een certificaat aanvraagt van een certificeringsinstantie (CA), voltooit de CA een verificatieproces. Dit proces kan zich van het verifiëren van domeinnaamcontrole tot het verzamelen van de documenten van de bedrijfregistratie en abonneeovereenkomsten uitstrekken. Nadat de informatie van een entiteit is geverifieerd, ondertekent de CA hun openbare sleutel gebruikend de privé sleutel van CA. Omdat alle belangrijke Autoriteiten van het Certificaat wortelcertificaten in Webbrowsers hebben, wordt het certificaat van de entiteit verbonden door a *ketting van vertrouwen*, en Webbrowser erkent het als vertrouwd op certificaat.

>[!IMPORTANT]
>
>Cloud Manager biedt geen SSL-certificaten of persoonlijke sleutels. Deze zaken moeten van een CertificatieAutoriteit, een vertrouwde op derdeorganisatie worden verkregen. Sommige bekende Autoriteiten van het Certificaat omvatten *DigiCert*, *versleutelings*, *GlobalSign*, *Vertrouwen*, en *Verisign*.

## Cloud Manager SSL-beheerfuncties {#features}

Cloud Manager biedt ondersteuning voor de volgende gebruiksopties voor SSL-certificaten van klanten.

* Meerdere omgevingen kunnen een SSL-certificaat gebruiken. Dat wil zeggen dat het eenmaal kan worden toegevoegd, maar meerdere keren wordt gebruikt.
* Elke Cloud Manager-omgeving kan meerdere certificaten gebruiken.
* Een persoonlijke sleutel kan meerdere SSL-certificaten uitgeven.
* Elk certificaat bevat gewoonlijk meerdere domeinen.
* De platformTLS de dienstroutes verzoeken aan de dienst CDN van de klant die op het SSL certificaat wordt gebaseerd dat wordt gebruikt om te eindigen en de dienst CDN die gastheren dat domein.
* AEM as a Cloud Service accepteert SSL-jokertekens voor een domein.

## Recommendations {#recommendations}

AEM as a Cloud Service ondersteunt alleen beveiligde `https` sites.

* Klanten met meerdere aangepaste domeinen willen niet telkens wanneer zij een domein toevoegen, een certificaat uploaden.
* Dergelijke klanten profiteren door één certificaat met veelvoudige domeinen te krijgen.

## Certificaatvereisten {#requirements}

* AEM as a Cloud Service accepteert certificaten die voldoen aan het beleid OV (Organisation Validation), EV (Extended Validation) of DV (Domain Validation). <!-- CQDOC-21758, #2 -->
* Elk certificaat moet een X.509 TLS-certificaat zijn van een vertrouwde certificeringsinstantie met een overeenkomende persoonlijke RSA-sleutel van 2048 bits.
* Zelfondertekende certificaten worden niet geaccepteerd.

OV- en EV-certificaten bieden voor CA gevalideerde informatie. Met deze informatie kunnen gebruikers beoordelen of de eigenaar van de website, de e-mailafzender of de digitale handtekening van code- of PDF-documenten kan worden vertrouwd. DV-certificaten staan een dergelijke eigendomsverificatie niet toe.

### Door de klant beheerde certificaatindeling {#certificate-format}

<!-- CQDOC-21758, #3 -->

SSL-certificaatbestanden moeten de PEM-indeling hebben om bij Cloud Manager te worden geïnstalleerd. Algemene bestandsextensies in de PEM-indeling zijn onder andere `.pem,` . `crt` , `.cer` en `.cert` .

De volgende `openssl` -opdrachten kunnen worden gebruikt om niet-PEM-certificaten om te zetten.

* PFX converteren naar PEM

  ```shell
  openssl pkcs12 -in certificate.pfx -out certificate.cer -nodes
  ```

* P7B converteren naar PEM

  ```shell
  openssl pkcs7 -print_certs -in certificate.p7b -out certificate.cer
  ```

* DER converteren naar PEM

  ```shell
  openssl x509 -inform der -in certificate.cer -out certificate.pem
  ```

## Beperkingen {#limitations}

Cloud Manager staat op elk moment maximaal 50 geïnstalleerde SSL-certificaten toe. Deze certificaten kunnen aan één of meerdere milieu&#39;s over uw programma worden geassocieerd en ook om het even welke verlopen certificaten omvatten.

Als u de limiet hebt bereikt, controleert u uw certificaten en overweegt u:

* Verlopen certificaten verwijderen.
* Meerdere domeinen in hetzelfde certificaat groeperen, aangezien een certificaat meerdere domeinen kan bestrijken (maximaal 100 SAN&#39;s).

## Meer informatie {#learn-more}

Een gebruiker met de vereiste machtigingen kan Cloud Manager gebruiken om SSL-certificaten voor een programma te beheren. Raadpleeg de volgende documenten voor meer informatie over het gebruik van deze functies.

* [ voeg een SSL certificaat toe ](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) <!--CQDOC-21758, #4 -->
* [ beheer SSL certificaten ](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md) <!--CQDOC-21758, #4 -->

