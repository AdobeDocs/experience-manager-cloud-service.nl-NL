---
title: Inleiding aan IP Lijsten van gewenste personen
description: Leer hoe IP de Lijsten van gewenste personen kunnen beperken waarvan de adressen gebruikers tot domeinen in AEM as a Cloud Service kunnen toegang hebben.
exl-id: 352fae8e-d116-40b0-ba54-d7f001f076e8
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 593b8c704c5b016bb55ae6a25420b577044b4126
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---


# Inleiding aan IP Lijsten van gewenste personen {#introduction}

Leer hoe IP de Lijsten van gewenste personen kunnen beperken waarvan de adressen gebruikers tot domeinen in AEM as a Cloud Service kunnen toegang hebben.

>[!CONTEXTUALHELP]
>id="aemcloud_golive_ipallowlist"
>title="IP-Lijsten van gewenste personen beheren"
>abstract="AEM as a Cloud Service is via internet toegankelijk en wordt beveiligd door gebruikersverificatie en autorisatie. De Lijsten van gewenste personen van Cloud Manager IP kunnen worden gebruikt om toegang tot slechts vertrouwde op IP adressen te beperken en te controleren. Cloud Manager-gebruikers met de juiste machtigingen kunnen lijsten van gewenste personen met vertrouwde IP-adressen maken, waarmee de gebruikers van hun site toegang hebben tot hun AEM-domeinen."
>additional-url="https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/ip-allow-lists/add-ip-allow-lists" text="Een IP-Lijst van gewenste personen toevoegen"
>additional-url="https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/ip-allow-lists/managing-ip-allow-lists" text="Een IP-Lijst van gewenste personen weergeven en bijwerken"

## Overzicht {#overview}

AEM als cloudservice is standaard toegankelijk via internet. Terwijl de veiligheid door gebruikersauthentificatie en vergunning wordt behandeld, IP staat-lijst toe om toegang tot slechts vertrouwde op IP adressen te beperken.

De Lijsten van gewenste personen van Cloud Manager IP kunnen worden gebruikt om toegang tot slechts dergelijke vertrouwde op IP adressen te beperken en te controleren. De gebruikers van Cloud Manager met aangewezen toestemmingen kunnen [ tot IP Lijsten van gewenste personen ](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md) van vertrouwde op IP adressen leiden en toevoegen waarvan de gebruikers van hun plaats tot hun domeinen van AEM kunnen toegang hebben.

Na het toevoegen, [ IP kunnen de Lijsten van gewenste personen worden toegepast of ](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) veelvoudige tijden als eenheid of entiteit aan de auteursdienst, of een uitgeversdienst, of allebei, in een milieu ongedaan worden gemaakt.

>[!NOTE]
>
>Als geen IP Lijst van gewenste personen wordt toegepast, door gebrek worden alle IP adressen toegestaan. Wanneer een IP Lijst van gewenste personen wordt toegepast, worden geen IP adressen toegestaan behalve adressen op de IP Lijst van gewenste personen.

## Gebruiksnotities {#usage-notes}

* Er kunnen maximaal 50 IP-Lijsten van gewenste personen aan uw programma worden toegevoegd.
* Een maximum van 50 IP/CIDR adressen kan aan elke IP Lijst van gewenste personen worden toegevoegd.
* IP de namen van de Lijst van gewenste personen worden gesteund in Cloud Manager voor de auteursdienst, of de publicatieservice, of allebei, in een milieu.

### Voorste-Eind Pijpleidingen en IP Lijsten van gewenste personen {#front-end-pipeline}

Als u gebruik-of van plan bent te gebruiken-de [ front-end pijpleiding om plaatsen ](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md) te ontwikkelen, moet de volgende Lijst van gewenste personen van Cloud Manager IP vooraf worden toegevoegd.

Wanneer u [ de IP Lijst van gewenste personen ](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md#add-cm-allowlist) toevoegt, noem het *`Cloud Manager`*, dan kopieer de lijst van hieronder adressen en kleef hen in het IP de dialoogvakje van de Lijst van gewenste personen.

```text
52.254.106.192/28
20.186.185.181
52.254.106.240/28
52.254.107.128/28
52.254.105.192/28
52.254.106.176/28
20.186.185.227
52.254.106.144/28
52.254.107.64/28
20.186.185.239
20.22.83.112
52.254.107.80/28
52.254.107.144/28
52.254.106.224/28
20.14.241.153
52.254.107.0/28
52.254.107.32/28
52.254.106.208/28
40.70.154.136/29
52.254.106.160/28
52.254.107.16/28
52.254.106.0/28
4.152.211.251
```

Om verstoring van het runnen van de front-end pijpleiding te vermijden, zorg ervoor dat deze Lijst van gewenste personen van Cloud Manager IP wordt toegevoegd. Dan, pas de lijst op het milieu van de Auteur *toe alvorens* u de pijpleiding toelaat.

Zie [ IP Lijst van gewenste personen ](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) toepassen en [ eerst-eind pijpleiding ](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md) voor meer informatie toelaten.

### De Universal Editor en IP-Lijsten van gewenste personen {#universal-editor}

Als u van plan bent om de Universele Redacteur aan auteur uw inhoud te gebruiken, moet u de IP adressen toevoegen die de Universele Dienst van de Redacteur aan een Lijst van gewenste personen gebruikt en het toepassen.

1. Haal de IP-adressen die door de Universal Editor Service worden gebruikt, op van het volgende API-eindpunt: `http://universal-editor-service.adobe.io/ip-ranges` .
1. Maak een lijst van gewenste personen met die IP-adressen en noem deze `Universal Editor Service` of vergelijkbaar.
1. Pas de lijst van gewenste personen `Universal Editor Service` toe.

De lijst van IP adressen die door de Universele Dienst van de Redacteur worden gebruikt is onderhevig aan verandering en u moet uw lijst van gewenste personen dienovereenkomstig bijwerken.
