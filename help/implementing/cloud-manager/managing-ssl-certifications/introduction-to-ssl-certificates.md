---
title: Inleiding tot SSL-certificaten
description: Voor meer informatie over de zelfbedieningsprogramma's van Cloud Manager kunt u SSL-certificaten installeren en beheren.
exl-id: 0d41723c-c096-4882-a3fd-050b7c9996d8
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: fa99656e0dd02bb97965e8629d5fa657fbae9424
workflow-type: tm+mt
source-wordcount: '928'
ht-degree: 0%

---


# Inleiding tot SSL-certificaten{#introduction}

In deze video ziet u hoe u SSL-certificaten (Secure Socket Layer) installeert en beheert.

>[!CONTEXTUALHELP]
>id="aemcloud_golive_sslcert"
>title="SSL-certificaten beheren"
>abstract="Leer hoe u met Cloud Manager zelfbedieningstools SSL-certificaten kunt installeren en beheren om uw site voor uw gebruikers te beveiligen. Cloud Manager gebruikt een platform-TLS-service voor het beheer van SSL-certificaten en persoonlijke sleutels die eigendom zijn van klanten en die zijn verkregen van certificeringsinstanties van derden."
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/managing-certificates" text="Een SSL-certificaat weergeven, bijwerken en vervangen"
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/managing-certificates" text="Status van een SSL-certificaat controleren"

## Wat zijn SSL-certificaten? {#overview}

Bedrijven en organisaties gebruiken SSL-certificaten (Secure Socket Layer) om hun websites te beveiligen en hun klanten in staat te stellen er vertrouwen in te stellen. Een webserver heeft een SSL-certificaat nodig om het SSL-protocol te kunnen gebruiken.

Wanneer een entiteit, zoals een organisatie of bedrijf, een certificaat aanvraagt van een certificeringsinstantie (CA), voltooit de CA een verificatieproces. Dit proces kan zich van het verifiëren van domeinnaamcontrole tot het verzamelen van de documenten van de bedrijfregistratie en abonneeovereenkomsten uitstrekken. Nadat de informatie van een entiteit is geverifieerd, ondertekent de CA hun openbare sleutel gebruikend de privé sleutel van CA. Omdat alle belangrijke Autoriteiten van het Certificaat wortelcertificaten in Webbrowsers hebben, wordt het certificaat van de entiteit verbonden door a *ketting van vertrouwen*, en Webbrowser erkent het als vertrouwd op certificaat.

>[!IMPORTANT]
>
>Cloud Manager biedt geen SSL-certificaten of persoonlijke sleutels. Deze onderdelen moeten worden verkregen van een certificeringsinstantie, een vertrouwde externe organisatie. Sommige bekende Autoriteiten van het Certificaat omvatten *DigiCert*, *versleutelings*, *GlobalSign*, *Vertrouwen*, en *Verisign*.

## Certificaten beheren met Cloud Manager {#cloud-manager}

Cloud Manager biedt zelfbedieningstools voor het installeren en beheren van SSL-certificaten, waarmee de sitebeveiliging voor uw gebruikers wordt gegarandeerd. Cloud Manager ondersteunt twee modellen voor het beheer van uw certificaten.

| | Model | Beschrijving |
| --- | --- | --- |
| A | **[Adobe beheerde SSL certificaat (DV)](#adobe-managed)** | Met Cloud Manager kunnen gebruikers DV-certificaten (Domain Validation) configureren die via Adobe worden geleverd voor snelle domeininstallatie. |
| B | **[Klant beheerde SSL certificaat (OV/EV)](#customer-managed)** | Cloud Manager biedt de dienst van platformTLS (de Veiligheid van de Laag van het Vervoer) aan om u te laten OV en EV SSL certificaten beheren die u en privé sleutels van de Autoriteiten van het Certificaat van de derde bezit, zoals *laat versleutelen*. |

Beide modellen bieden de volgende algemene functies voor het beheer van uw certificaten:

* Elke Cloud Manager-omgeving kan meerdere certificaten gebruiken.
* Een persoonlijke sleutel kan meerdere SSL-certificaten uitgeven.
* De platformTLS de dienstroutes verzoeken aan de dienst CDN van de klant die op het SSL certificaat wordt gebaseerd dat wordt gebruikt om te eindigen en de dienst CDN die gastheren dat domein.

>[!IMPORTANT]
>
>[ om een douanedomein met een milieu ](/help/implementing/cloud-manager/custom-domain-names/introduction.md) toe te voegen en te associëren, moet u een geldig SSL certificaat hebben dat het domein behandelt.

### Door Adobe beheerde SSL-certificaten (DV) {#adobe-managed}

DV-certificaten zijn het meest elementaire niveau van SSL-certificering en worden vaak gebruikt voor testdoeleinden of voor het beveiligen van websites met basiscodering. DV de certificaten zijn beschikbaar in zowel [ productieprogramma&#39;s als zandbakprogramma&#39;s ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md).

Nadat het DV-certificaat is gemaakt, wordt dit door de Adobe automatisch elke drie maanden vernieuwd, tenzij het wordt verwijderd.

### Door de klant beheerde OV/EV SSL-certificaten {#customer-managed}

OV- en EV-certificaten bieden voor CA gevalideerde informatie. Met deze informatie kunnen gebruikers beoordelen of de eigenaar van de website, de e-mailafzender of de digitale handtekening van code- of PDF-documenten kan worden vertrouwd. DV-certificaten staan een dergelijke eigendomsverificatie niet toe.

OV en EV bieden deze functies bovendien via DV-certificaten in Cloud Manager.

* Meerdere omgevingen kunnen een OV/EV-certificaat gebruiken. Dat wil zeggen dat het eenmaal kan worden toegevoegd, maar meerdere keren wordt gebruikt.
* Elk OV/EV-certificaat bevat doorgaans meerdere domeinen.
* Cloud Manager accepteert OV/EV-jokertekens voor een domein.

>[!TIP]
>
>Als u meerdere aangepaste domeinen hebt, is het mogelijk dat u niet elke keer een certificaat wilt uploaden wanneer u een nieuw domein toevoegt. In dat geval kunt u profiteren van het verkrijgen van één certificaat dat meerdere domeinen bestrijkt.

>[!NOTE]
>
>Als twee certificaten betrekking hebben op hetzelfde domein, wordt het certificaat dat nauwkeuriger is, toegepast.
>
>Als uw domein bijvoorbeeld `dev.adobe.com` is en u een certificaat voor `*.adobe.com` en een ander certificaat voor `dev.adobe.com` hebt, wordt het specifiekere (`dev.adobe.com`) gebruikt.

#### Vereisten voor door klanten beheerde OV/EV SSL-certificaten {#requirements}

Als u ervoor kiest om uw eigen door de klant beheerde OV/EV SSL-certificaat toe te voegen, moet het aan de volgende vereisten voldoen:

* AEM as a Cloud Service accepteert certificaten die voldoen aan het OV- (Organization Validation) of EV-beleid (Extended Validation).
   * Cloud Manager biedt geen ondersteuning voor het toevoegen van uw eigen DV-certificaten (Domain Validation).
* Elk certificaat moet een X.509 TLS-certificaat zijn van een vertrouwde certificeringsinstantie met een overeenkomende persoonlijke RSA-sleutel van 2048 bits.
* Zelfondertekende certificaten worden niet geaccepteerd.

#### Indeling voor door klanten beheerde certificaten {#certificate-format}

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

>[!TIP]
>
>Adobe raadt u aan de integriteit van uw certificaat lokaal te valideren met een hulpprogramma zoals `openssl verify -untrusted intermediate.pem certificate.pem` voordat u probeert het te installeren met Cloud Manager.

## Beperking van het aantal geïnstalleerde SSL-certificaten {#limitations}

Cloud Manager staat op elk moment maximaal 50 geïnstalleerde SSL-certificaten toe. Deze certificaten kunnen aan één of meerdere milieu&#39;s over uw programma worden geassocieerd en ook om het even welke verlopen certificaten omvatten.

Als u de limiet hebt bereikt, controleert u uw certificaten en kunt u eventueel verlopen certificaten verwijderen. U kunt ook meerdere domeinen in hetzelfde certificaat groeperen omdat een certificaat meerdere domeinen kan bestrijken (maximaal 100 SAN&#39;s).

## Meer informatie {#learn-more}

Een gebruiker met de vereiste machtigingen kan Cloud Manager gebruiken om SSL-certificaten voor een programma te beheren. Raadpleeg de volgende documenten voor meer informatie over het gebruik van deze functies.

* [ voeg een SSL certificaat toe ](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) <!--CQDOC-21758, #4 -->
* [ beheer SSL certificaten ](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md) <!--CQDOC-21758, #4 -->

