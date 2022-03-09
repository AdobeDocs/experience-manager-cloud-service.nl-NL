---
title: Nieuwe Relic One
description: Meer informatie over de service New Relic One Application Performance Monitoring (APM) voor AEM as a Cloud Service en over hoe u toegang hebt tot deze service.
exl-id: 9fa0c5eb-415d-4e56-8136-203d59be927e
source-git-commit: 6cf164093cc543fe4847859b248e70efd86efbb1
workflow-type: tm+mt
source-wordcount: '1038'
ht-degree: 0%

---


# Nieuwe Relic One {#user-access}

Meer informatie over de service New Relic One Application Performance Monitoring (APM) voor AEM as a Cloud Service en over hoe u toegang hebt tot deze service.

## Inleiding {#introduction}

Adobe legt een grote nadruk op de controle, de beschikbaarheid, en de prestaties van uw toepassing. Om dit doel te helpen bereiken, verleent AEM as a Cloud Service toegang tot een douane Nieuwe Relic Één controlereeks als deel van het standaard product aanbieden om uw teams de maximumzichtbaarheid aan uw AEM as a Cloud Service systeem en milieu prestatiesmetriek te verzekeren.

In dit document worden de APM-functies (New Relic One Application Performance Monitoring) beschreven die op uw AEM as a Cloud Service omgevingen zijn ingeschakeld om de prestaties te ondersteunen en u te helpen het beste uit AEM as a Cloud Service te halen.

## Functies {#transaction-monitoring}

Nieuwe Relic One APM for AEM as a Cloud Service heeft veel functies.

* Directe toegang tot een toegewezen Nieuwe Relic One-account (toegang beheerd door Adobe Support)

* Instrumenteerde Nieuwe Relic Één APM agent die nauwkeurige methodevraag met lijnaantallen, met inbegrip van externe gebiedsdelen en gegevensbestanden toont

* Holistische optimalisatie van prestaties door de belangrijkste meetgegevens van infrastructuur-vlakke controle evenals toepassing (Adobe Experience Manager) controle te combineren

* Blootstelling van AEM as a Cloud Service JMX-bonen en gezondheidscontroles rechtstreeks binnen de nieuwe meetgegevens voor Relic Insights, waardoor een grondige inspectie van de prestaties van de toepassingsstapel en de gezondheidsmaatstaven mogelijk is.

## Toegang krijgen tot nieuwe advertentie {#accessing-new-relic}

Voer de volgende stappen uit om toegang te krijgen tot uw nieuwe e-mailaccount die is gekoppeld aan uw AEM as a Cloud Service programma.

1. Open een aanvraag door het tabblad Ondersteuning in de Admin Console te openen.
1. In uw verzoek, omvat de details van uw identiteitskaart van het Programma, evenals de lijst van gebruikers die toegang tot Nieuw Relic vereisen.
   * De volledige namen en geldige e-mailadressen van alle gebruikers moeten worden opgegeven.

Het document raadplegen [AEM Support Portal voor Experience Cloud](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html) voor meer informatie over het openen van tickets .

Zodra de toegang is verleend, verzendt het Nieuwe Relic een bevestigingsmail naar elke gebruiker, zodat kan de gebruiker het opstellingsproces voltooien en binnen ondertekenen.

Voer de volgende stappen uit als de gebruiker het bevestigingsbericht van de oorspronkelijke account niet kan vinden.

1. Navigeer naar de aanmeldingspagina van New Relic op [`login.newrelic.com/login`](https://login.newrelic.com/login).

1. Selecteren **Bent u uw wachtwoord vergeten?**.

   ![Nieuwe aanmelding voor Relic](/help/implementing/cloud-manager/assets/new-relic/newrelic-1.png)

1. Typ het e-mailadres van de account en selecteer **Mijn terugstelkoppeling verzenden**.

   ![E-mailadres invoeren](/help/implementing/cloud-manager/assets/new-relic/newrelic-2.png)

1. Het nieuwe e-mailbericht zal de gebruiker een e-mail sturen met een koppeling om het account te bevestigen.

Als u het aanmeldingsproces hebt voltooid en zich niet kunt aanmelden bij uw account vanwege e-mail- of wachtwoordfoutberichten, registreert u een ondersteuningsticket via [Admin Console](https://adminconsole.adobe.com/).

>[!TIP]
>
>Als je geen e-mail van New Relic ontvangt:
>
>* Controleer uw [spamfilters](https://docs.newrelic.com/docs/accounts/accounts-billing/account-setup/create-your-new-relic-account/).
>* Indien van toepassing, [Nieuw bericht toevoegen aan uw e-maillijst van gewenste personen](https://docs.newrelic.com/docs/accounts/accounts/account-maintenance/account-email-settings/#email-whitelist).
>* Als geen van beide suggesties helpt, geef dan feedback op het ondersteuningsticket en Adobe Support-team helpt u verder.


### Je e-mail verifiëren {#verify-email}

Als u tijdens het aanmelden wordt gevraagd uw e-mail te verifiëren, betekent dit dat uw e-mail is gekoppeld aan meerdere accounts. Op deze manier kunt u kiezen welk account u wilt openen.

Als u uw e-mailadres niet verifieert, probeert New Relic u aan te melden met de laatst gemaakte gebruikersrecord die aan uw e-mailadres is gekoppeld. Als u wilt voorkomen dat uw e-mail tijdens elke aanmelding wordt gecontroleerd, klikt u op de knop **Onthoud mijn gegevens** Schakel het selectievakje in het aanmeldingsscherm in.

Voor meer hulp, gelieve een steunkaartje via te openen [Ondersteuningsportaal voor AEM](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html).

## Uitzonderingen {#exceptions}

AEM as a Cloud Service biedt slechts de Nieuwe Relic Één APM oplossing aan en verleent geen steun voor alarmering, registreren, of API integratie.

Voor meer hulp of extra begeleiding op Nieuw Relic Één dienstenaanbod voor uw AEM as a Cloud Service Programma, gelieve een steunkaartje via te openen [Ondersteuningsportaal voor AEM](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html).

## Veelgestelde vragen voor nieuwe zakelijke account {#faqs}

### Wat controleert Adobe met Nieuwe Relic Één? {#adobe-monitor}

Adobe volgt de AEM as a Cloud Service auteur, publiceert en voorproef (waar beschikbaar) de diensten via Nieuwe Relic One&#39;s Java-plug-in. Adobe maakt aangepaste New Relic One APM-telemetrie en bewaking mogelijk in niet-productie- en productie-AEM as a Cloud Service omgevingen.

Uw Nieuwe Relic One-account is gekoppeld aan een primaire Adobe-account en heeft meerdere toepassingen die erin rapporteren: drie per AEM as a Cloud Service omgeving.

* Eén toepassing voor de auteurservice per omgeving
* Eén toepassing voor de publicatieservice per omgeving (inclusief Golden Publish)
* Eén toepassing voor de voorbeeldservice per omgeving

Opmerking:

* Elke toepassing gebruikt één licentiecode.
* AEM as a Cloud Service milieu&#39;s rapporteren aan slechts één Nieuwe Relic Één rekening.
* De volledige controlemetriek en de gebeurtenissen voor beide Nieuwe Relic Één worden behouden voor 7 dagen.

### Wie heeft toegang tot de gegevens van de nieuwe Relic One-cloudservice? {#access-new-relic-cloud}

Volledige leestoegang wordt verleend voor maximaal 10 leden van uw team. De gelezen toegang zal alle die meetkunde APM omvatten door Nieuw Relic wordt verzameld Één agent.

### Wordt aangepaste SSO-configuratie ondersteund? {#custom-sso}

De configuratie van SSO van de douane wordt niet gesteund voor Nieuwe Relic Één rekening die door Adobe wordt voorzien.

### Wat als ik reeds een op-gebouw Nieuw Relisch abonnement heb? {#new-relic-subscription}

Nieuwe Relic Één is het nieuwe observability platform van Nieuw Relic en het laat de steun van Adobe en uw teams toe om, metriek en gebeurtenissen, allen op één plaats waar te waarnemen te controleren en te bekijken.

Nieuwe Relic Één verstrekt gebruikers de capaciteit om over alle rekeningen te zoeken waar zij toegang hebben en de gegevens van alle diensten en gastheren in één mening visualiseren.

Terwijl de steun van Adobe de AEM as a Cloud Service toepassing zal controleren gebruikend Nieuw Relic Één en andere interne hulpmiddelen als deel van uw dienst, kunnen uw teams Nieuwe Relic voor op-gebouw ontvangen diensten en infrastructuur blijven hefboomwerking. Zij zullen de gegevens van zowel Adobe New Relic Één rekening als klant-geleide Nieuwe Relische rekeningen kunnen visualiseren.

>[!NOTE]
>
>Om beide gegevensreeksen binnen Nieuwe Relic te bekijken Één, moet een gebruiker de juiste toestemmingen hebben en de zelfde login methodologie voor beide rekeningen (Adobe Nieuw Relic Één en de klant-geleide Nieuwe Relische rekeningen) gebruiken.
