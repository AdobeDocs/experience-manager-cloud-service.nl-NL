---
title: Toegang van gebruiker tot nieuw Relic
description: Toegang van gebruiker tot nieuw Relic
index: false
hide: true
source-git-commit: 22dc38ac4aa736ae5c676cfba16e16b0b3e44936
workflow-type: tm+mt
source-wordcount: '998'
ht-degree: 0%

---


# Nieuwe Relic Application Performance Monitoring voor AEM as a Cloud Service {#new-relic}

## Inleiding {#introduction}

Adobe legt een hoge nadruk op de controle, de beschikbaarheid, en de prestaties van uw toepassing. Om dit doel te helpen bereiken, verleent AEM as a Cloud Service toegang tot een douane Nieuwe Relische controlereeks als deel van het standaardproductaanbod om uw teams de maximumzichtbaarheid aan uw systeem van de Cloud Service van Adobe Experience Manager en milieu prestatiesmetriek te verzekeren. In deze sectie worden de nieuwe functies voor de bewaking van Relic beschreven die op uw AEM as a Cloud Service omgevingen zijn ingeschakeld om de prestaties te ondersteunen en u in staat te stellen optimaal te profiteren van AEM as a Cloud Service omgevingen.

## as a Cloud Service transactiecontrole AEM via New Relic {#transaction-monitoring}

Hier zijn zeer belangrijke eigenschappen in Nieuwe Relic Controle van de Prestaties van de Toepassing voor AEM as a Cloud Service:

* Directe toegang tot een toegewezen Nieuwe Relic One-account (toegang beheerd door Adobe Support).

* Instrumented Nieuwe Relic APM agent die nauwkeurige methodevraag met lijnaantallen, met inbegrip van externe gebiedsdelen en gegevensbestanden toont.

* Holistische optimalisatie van prestaties door belangrijke metriek van infrastructuur-vlakke controle evenals toepassing (Adobe Experience Manager) controle te combineren.

* Blootstelling van AEM as a Cloud Service JMX-bonen en Health Checks rechtstreeks aan nieuwe gegevens over Relic Insights, waardoor een grondige inspectie van de prestaties van de toepassingenstapel en gezondheidsmaatstaven mogelijk is.

## Toegang tot uw AEM as a Cloud Service nieuwe account {#accessing-new-relic}

Uw toegewezen Nieuwe Relic-account wordt door Adobe geleverd en beheerd via de betrokkenheid van de klant. Adobe blijft de eigenaar en beheerder en zal de account namens u beschikbaar stellen voor toegang tot uw toegewezen subaccount.

Om toegang te krijgen tot uw Nieuwe Relische sub-rekening verbonden aan uw AEM as a Cloud Service Programma:

* Open een aanvraag door het tabblad Ondersteuning in de Admin Console te openen.
* Zorg ervoor dat uw ticket de details van uw programma-id bevat, evenals de lijst met gebruikers die u Adobe-teams vraagt om de nieuwe Relic-toegang te openen.
* Alle gebruikers moeten een volledige naam en een geldig e-mailadres hebben.

   >[!NOTE]
   >Voor meer informatie over AEM Support Portal, gelieve Steun voor Experience Cloud.

Zodra de toegang is verleend, verzendt het Nieuwe Relic een bevestigingsmail naar elke gebruiker, zodat kunnen zij het opstellingsproces voltooien en binnen ondertekenen. Als ze het bevestigingsbericht van de oorspronkelijke account niet kunnen vinden:

1. Navigeer naar de aanmeldingspagina van New Relic op login.newrelic.com/login.

1. Selecteer vergeten uw wachtwoord.

1. Typ het e-mailadres van de account en selecteer Mijn wachtwoord verzenden.

1. Wanneer het systeem van New Relic een e-mailbericht retourneert, selecteert u de koppeling in het bericht om uw account opnieuw te bevestigen.

   >[!NOTE]
   >Als je geen e-mail van New Relic ontvangt:
   >Controleer uw spamfilters. Voeg, indien van toepassing, Nieuw bericht toe aan uw e-maillijst van gewenste personen.
   >Feedback op het ondersteuningsticket en onze teams helpen u verder

1. Als u het aanmeldingsproces hebt voltooid en zich niet kunt aanmelden bij uw account vanwege e-mail- of wachtwoordfoutberichten, kunt u ons een ondersteuningsticket via Admin Console sturen.

Als u tijdens het aanmelden wordt gevraagd uw e-mail te verifiëren, betekent dit dat uw e-mail is gekoppeld aan meerdere accounts en de optie krijgt om uw e-mail te verifiëren tijdens het aanmelden. Op deze manier kunt u kiezen welk account u wilt openen. Als u uw e-mailadres niet verifieert, probeert New Relic u aan te melden met de laatst gemaakte gebruikersrecord die aan uw e-mailadres is gekoppeld. Als u wilt voorkomen dat uw e-mail tijdens elke aanmelding wordt gecontroleerd, klikt u op het selectievakje Onthoud mijn gegevens in het aanmeldingsscherm.

Voor meer hulp, te openen gelieve een steunkaartje via AEM Portaal van de Steun.

## Uitzonderingen {#exceptions}

AEM as a Cloud Service richt het aanbieden rond Nieuwe Relic APM oplossing slechts en verleent geen steun voor alarmering, registreren of API integratiemogelijkheden.

Voor meer hulp of extra begeleiding over Nieuw Relisch aanbod voor uw AEM as a Cloud Service Programma, gelieve een steunkaartje via AEM Portaal van de Steun voor hulp te openen.

## Veelgestelde vragen voor nieuwe zakelijke account {#faqs}

### Wat controleert Adobe met Nieuw Relic? {#adobe-monitor}

Adobe bewaakt de AEM as a Cloud Service services voor auteurs, publiceren en voorvertonen (indien beschikbaar) via de insteekmodule New Relic APM Java. Met Adobe kunt u de aangepaste New Relic APM Telemetry en bewaking in niet-productie- en productie-AEM as a Cloud Service omgevingen mogelijk maken. Uw nieuwe Relische account is gekoppeld aan een primaire door Adobe onderhouden account en bevat meerdere toepassingen die hierin worden gerapporteerd.

Drie per AEM as a Cloud Service omgeving:

* Eén toepassing voor de service Auteur per omgeving
* Eén toepassing voor de service Publiceren per omgeving (inclusief Gulden publicatie)
* Eén toepassing voor de voorvertoningsservice per omgeving Elke toepassing gebruikt één licentiecode, AEM as a Cloud Service omgevingen slechts aan één nieuwe Relic-account rapporteren. De volledige controlemetriek en de gebeurtenissen voor zowel Nieuwe Relic APM als Infrastructuur worden bewaard voor 7 dagen.

### Wie heeft toegang tot de Nieuwe Relische gegevens van de Cloud Service? {#access-new-relic-cloud}

Volledige leestoegang wordt verleend voor maximaal 10 leden van uw team. De lees toegang zal alle die meetkunde APM omvatten door de Nieuwe Relic agent wordt verzameld.

### Wordt Aangepaste SSO-configuratie ondersteund? {#custom-sso}

Aangepaste SSO-configuratie wordt momenteel niet ondersteund voor de nieuwe Relic-account die door Adobe is ingericht.

### Wat als u reeds een op-gebouw Nieuw Relisch Abonnement hebt? {#new-relic-subscription}

Het nieuwe observability platform van Nieuw Relic genoemd Nieuwe Relic laat de Groepen van de Steun van de Adobe en uw teams toe om, metriek en gebeurtenissen, allen in één plaats waar te waarnemen te controleren en te bekijken. Nieuwe Relic Één verstrekt gebruikers de capaciteit om over alle rekeningen te zoeken waar zij toegang hebben en de gegevens van alle diensten en gastheren in één mening visualiseren. Terwijl de Teams van de Steun van Adobe de AEM as a Cloud Service toepassing zullen controleren gebruikend Nieuwe Relische en andere interne hulpmiddelen als deel van uw dienst, kunnen uw teams Nieuwe Relic voor op-gebouw ontvangen diensten en infrastructuur blijven gebruiken. Zij zullen de gegevens van zowel Adobe als klant beheerde Nieuwe Relische rekeningen kunnen visualiseren.

>[!NOTE]
>De gebruiker moet de juiste toestemmingen hebben en de zelfde login methodologie voor beide rekeningen (Adobe en klant beheerde Nieuwe Relische rekening) gebruiken.


