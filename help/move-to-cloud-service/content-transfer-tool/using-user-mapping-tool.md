---
title: Gebruikerstoewijzing gebruiken
description: Gebruikerstoewijzing gebruiken
translation-type: tm+mt
source-git-commit: 664c278494a5ac88362b994946060ab3baa846d8
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 6%

---


# Gebruikend het Hulpmiddel van de Toewijzing van de Gebruiker {#user-mapping-tool}

## Overzicht {#overview}

Als deel van de overgangsreis aan AEM als Cloud Service, moet u gebruikers en groepen van uw bestaand AEM systeem aan AEM als Cloud Service bewegen. Dit wordt gedaan door het Hulpmiddel van de Overdracht van de Inhoud.

Een belangrijke wijziging in AEM as Cloud Service is het volledig geïntegreerde gebruik van Adobe ID&#39;s voor toegang tot de authoringlaag.  Hiervoor moet de Adobe Admin Console worden gebruikt voor het beheer van gebruikers en gebruikersgroepen. De gebruikersprofielgegevens zijn gecentraliseerd in het Adobe Identity Management System (IMS) dat Single Sign-On biedt voor alle Adobe-cloudtoepassingen. Raadpleeg Identity Management voor meer informatie. Vanwege deze wijziging moeten bestaande gebruikers en groepen worden toegewezen aan hun IMS-id&#39;s om dubbele gebruikers en groepen in de auteur van de Cloud Service te voorkomen.

## Belangrijke overwegingen {#important-considerations}

Er zijn enkele uitzonderlijke gevallen die in overweging moeten worden genomen. De volgende specifieke gevallen worden geregistreerd en de betrokken gebruiker of groep wordt niet toegewezen:

1. Als een gebruiker geen e-mailadres heeft op het `profile/email` gebied van hun jcr knoop.

1. Als een bepaalde e-mail niet wordt gevonden op het IMS-systeem voor de gebruikte organisatie-id (of als de IMS-id om een andere reden niet kan worden opgehaald).

1. Als de gebruiker momenteel is uitgeschakeld, wordt deze op dezelfde manier behandeld als wanneer de gebruiker niet is uitgeschakeld.  Het wordt toegewezen en gemigreerd als normaal en blijft uitgeschakeld in de cloudinstantie.

## Het gebruiken van het Hulpmiddel van de Toewijzing van de Gebruiker {#using-user-mapping-tool}

Het gereedschap Toewijzing gebruiker gebruikt een API waarmee IMS-gebruikers via e-mail kunnen worden opgezocht en hun IMS-id&#39;s kunnen worden geretourneerd. Deze API vereist de gebruiker om een identiteitskaart van de Cliënt voor hun organisatie, een Geheim van de Cliënt, en een Token van de Token van de Toegang te creëren/Drager.

Voer de volgende stappen uit om dit in te stellen:

1. Navigeer naar [Adobe Developer Console](https://console.adobe.io) met uw Adobe ID.
1. Een nieuw project maken of een bestaand project openen
1. Een API toevoegen
1. Gebruikerbeheer-API kiezen
1. Een JWT-referentie maken
1. Een sleutelpaar genereren of een openbare sleutel uploaden (rsa is geen goed)
1. Genereer een toegangstoken (of teken JWT of dragertoken).
1. Sla al deze gegevens (client-id, clientgeheim, technische-accountid, e-mail voor technische account, organisatie-id, toegangstoken) op een veilige plaats op.