---
title: Inleiding - SSL-certificaten beheren
description: Inleiding - SSL-certificaten beheren
exl-id: 0d41723c-c096-4882-a3fd-050b7c9996d8
source-git-commit: 8e09031d1cf17bda9d4eb379f84462b2d29e1aa5
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# Inleiding {#introduction}

Cloud Manager biedt klanten de mogelijkheid om zelf SSL-certificaten te installeren via de interface van Cloud Manager. Cloud Manager gebruikt een Platform-TLS-service voor het beheer van SSL-certificaten en persoonlijke sleutels die eigendom zijn van klanten en die doorgaans worden verkregen van certificeringsinstanties van derden, bijvoorbeeld *Laten we versleutelen*.

## Belangrijke overwegingen {#important-considerations}

* Cloud Manager biedt geen SSL-certificaten of persoonlijke sleutels. Deze moeten afkomstig zijn van certificeringsinstanties van derden. Raadpleeg [Een SSL-certificaat ophalen](/help/implementing/cloud-manager/managing-ssl-certifications/get-ssl-certificate.md) voor meer informatie.

* AEM als Cloud Service ondersteunt alleen beveiligde `https`-sites. Klanten met meerdere aangepaste domeinen willen niet telkens wanneer zij een domein toevoegen, een certificaat uploaden. Daarom zullen dergelijke klanten profiteren door één certificaat met meerdere domeinen te krijgen.

* AEM als Cloud Service accepteert alleen OV-(Organisatie-validatie) of EV-(Uitgebreide validatie) certificaten. DV-certificaten (Domain Validation) worden niet geaccepteerd. Bovendien moet elk certificaat een X.509 TLS-certificaat zijn van een vertrouwde certificeringsinstantie (CA) met een overeenkomende 2048-bits RSA-privésleutel.

* AEM als Cloud Service accepteert jokertekens voor SSL-certificaten voor een domein.

Cloud Manager ondersteunt de volgende SSL-certificaatvereisten voor klanten:

* Een SSL-certificaat kan door meerdere omgevingen worden gebruikt, dat wil zeggen één keer toevoegen en meerdere keren gebruiken.
* Elke Cloud Manager-omgeving kan meerdere certificaten gebruiken.
* Een persoonlijke sleutel kan meerdere SSL-certificaten uitgeven.
* Elk certificaat bevat gewoonlijk meerdere domeinen.
* De de dienstroutes van Platform TLS verzoeken aan de Dienst CDN van de klant die op het SSL certificaat wordt gebaseerd dat wordt gebruikt om te eindigen en de Dienst CDN die gastheren dat domein.

Met behulp van de pagina met SSL-certificaten voor de gebruikersinterface van Cloud Manager kan een gebruiker met machtigingen verschillende taken uitvoeren om SSL-certificaten voor een programma te beheren:

* [Een SSL-certificaat toevoegen](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md)
* [Een SSL-certificaat weergeven, bijwerken of vervangen](/help/implementing/cloud-manager/managing-ssl-certifications/view-update-replace-ssl-certificate.md)
   >[!NOTE]
   >Met deze acties kunt u details weergeven of een certificaat vervangen dat bijna verlopen is.
* [Een SSL-certificaat verwijderen](/help/implementing/cloud-manager/managing-ssl-certifications/delete-ssl-certificate.md)
