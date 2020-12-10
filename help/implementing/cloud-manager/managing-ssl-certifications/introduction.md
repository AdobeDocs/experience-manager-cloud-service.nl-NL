---
title: Inleiding - SSL-certificaten beheren
description: Inleiding - SSL-certificaten beheren
translation-type: tm+mt
source-git-commit: 5ebe94c8562b952521effa3b67267c3eab925d16
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---


# Inleiding {#introduction}

Cloud Manager biedt klanten de mogelijkheid om zelf SSL-certificaten te installeren via de interface van Cloud Manager. Cloud Manager gebruikt een Platform-TLS-service voor het beheer van SSL-certificaten en persoonlijke sleutels die eigendom zijn van klanten en die doorgaans worden verkregen van certificeringsinstanties van derden, bijvoorbeeld &quot;Laten we versleutelen&quot;.

>[!IMPORTANT]
>Cloud Manager biedt geen SSL-certificaten of persoonlijke sleutels. Deze moeten afkomstig zijn van certificeringsinstanties van derden. Raadpleeg [Een SSL-certificaat ophalen](/help/implementing/cloud-manager/managing-ssl-certifications/get-ssl-certificate.md) voor meer informatie.

>[!NOTE]
>AEM als Cloud Service ondersteunt alleen beveiligde https-sites. Klanten met meerdere aangepaste domeinen willen niet telkens wanneer zij een domein toevoegen, een certificaat uploaden. Daarom zullen dergelijke klanten profiteren door één certificaat met meerdere domeinen te krijgen.

Cloud Manager ondersteunt de volgende SSL-certificaatvereisten voor klanten:

* Een SSL-certificaat kan door meerdere omgevingen worden gebruikt, dat wil zeggen één keer toevoegen en meerdere keren gebruiken.
* Elke Cloud Manager-omgeving kan meerdere certificaten gebruiken.
* Een persoonlijke sleutel kan meerdere SSL-certificaten uitgeven.
* Elk certificaat bevat gewoonlijk meerdere domeinen.
* De de dienstroutes van Platform TLS verzoeken aan de Dienst CDN van de klant die op het SSL certificaat wordt gebaseerd dat wordt gebruikt om te eindigen en de Dienst CDN die gastheren dat domein.

Met behulp van de pagina met SSL-certificaten voor de gebruikersinterface van Cloud Manager kan een gebruiker met machtigingen verschillende taken uitvoeren om SSL-certificaten voor een programma te beheren:

* Een SSL-certificaat toevoegen
* Een SSL-certificaat weergeven, bijwerken of vervangen
   >[!NOTE]
   >Met deze acties kunt u details weergeven of een certificaat vervangen dat bijna verlopen is.
* Een SSL-certificaat verwijderen