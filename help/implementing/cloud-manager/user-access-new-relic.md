---
title: Nieuwe Relic One
description: Meer informatie over de service New Relic One Application Performance Monitoring (APM) voor AEM as a Cloud Service en over hoe u toegang hebt tot deze service.
exl-id: 9fa0c5eb-415d-4e56-8136-203d59be927e
source-git-commit: 09049213eaf92830dc0e0d4c0885017c69a5d56e
workflow-type: tm+mt
source-wordcount: '1622'
ht-degree: 0%

---


# Nieuwe Relic One {#user-access}

Meer informatie over de service New Relic One Application Performance Monitoring (APM) voor AEM as a Cloud Service en over hoe u toegang hebt tot deze service.

## Inleiding {#introduction}

Adobe legt een grote nadruk op de controle, de beschikbaarheid, en de prestaties van uw toepassing. AEM as a Cloud Service biedt toegang tot een aangepaste Nieuwe Relic One-controlereeks als onderdeel van de standaard productaanbieding om ervoor te zorgen dat uw teams de maximale zichtbaarheid van uw AEM as a Cloud Service systeem- en omgevingsprestaties hebben.

In dit document wordt beschreven hoe u de toegang tot de APM-functies (New Relic One Application Performance Monitoring) die op uw AEM as a Cloud Service omgevingen zijn ingeschakeld, beheert voor de ondersteuning van prestaties en hoe u optimaal kunt profiteren van AEM as a Cloud Service omgevingen.

Wanneer een nieuw productieprogramma wordt gecreeerd, wordt Nieuwe Relic Één subaccount verbonden aan uw AEM as a Cloud Service Programma automatisch gecreeerd.

## Functies {#transaction-monitoring}

Nieuwe Relic One APM for AEM as a Cloud Service heeft veel functies.

* Directe toegang tot een toegewezen Nieuwe Relic One-account (toegang beheerd door Adobe Support)

* Instrumenteerde Nieuwe Relic Één APM agent die nauwkeurige methodevraag met lijnaantallen, met inbegrip van externe gebiedsdelen en gegevensbestanden toont

* Holistische optimalisatie van prestaties door de belangrijkste meetgegevens van infrastructuur-vlakke controle evenals toepassing (Adobe Experience Manager) controle te combineren

* Blootstelling van AEM as a Cloud Service JMX-bonen en gezondheidscontroles rechtstreeks binnen de nieuwe meetgegevens voor Relic Insights, waardoor een grondige inspectie van de prestaties van de toepassingsstapel en de gezondheidsmaatstaven mogelijk is.

## Nieuwe online-gebruikers beheren {#manage-users}

Voer de volgende stappen uit om de gebruikers van de nieuwe subaccount voor Relic One te definiëren die is gekoppeld aan uw AEM as a Cloud Service programma.

>[!NOTE]
>
>Een gebruiker in **Zakelijke eigenaar** of **Implementatiebeheer** De rol moet worden het programma geopend om Nieuw Relic te leiden Één gebruikers.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie.

1. Klik op het programma waarvoor u uw Nieuwe Relic Één gebruikers wilt beheren.

1. Naar de **Omgevingen** van de **Programmaoverzicht** pagina door op de knop **Omgevingen** aan de bovenkant van het scherm.

1. Op de **Omgevingen** scherm, klik de ellipsieknoop bij de bovenkant van het scherm naast het **Omgeving toevoegen** knop.

1. Klik in het menu Ovaal op **Gebruikers beheren**.

   ![Gebruikers beheren](assets/newrelic-manage-users.png)

1. In de **Nieuwe onlinegebruikers beheren** voert u de voor- en achternaam in van de gebruiker die u wilt toevoegen en klikt u op de knop **Toevoegen** knop. Herhaal deze stap voor alle gebruikers die u wilt toevoegen.

   ![Gebruikers toevoegen](assets/newrelic-add-users.png)

1. Om een Nieuw Relic te verwijderen Één gebruikers, klik de schrappingsknoop bij het rechtereind van de rij die de gebruiker vertegenwoordigt.

1. Klikken **Opslaan** om de gebruikers te maken.

Zodra de gebruikers worden bepaald, verzendt het Nieuwe Relic een bevestigingsmail naar elke gebruiker aan wie u toegang verleende, zodat kan de gebruiker het opstellingsproces voltooien en binnen ondertekenen.

>[!NOTE]
>
>Als u Nieuwe Relic Één gebruikers beheert, moet u ook toevoegen als gebruiker om toegang te hebben. De **Zakelijke eigenaar** of **Implementatiebeheer** volstaat niet om toegang tot Nieuwe Relic te hebben. U moet uzelf ook als gebruiker maken.

## Je nieuwe gratis gebruikersaccount activeren {#activate-account}

Zodra een Nieuwe Relic Één gebruikersrekening zoals die in de voorproefsectie wordt beschreven wordt gecreeerd [Nieuwe online-gebruikers beheren](#manage-users), New Relic stuurt deze gebruikers een bevestigingsbericht naar het opgegeven adres. Om die rekeningen te gebruiken, moeten de gebruikers hun rekeningen met Nieuw Relic eerst activeren door hun wachtwoorden opnieuw in te stellen.

Voer de volgende stappen uit om uw account te activeren als nieuwe eBay-gebruiker.

1. Klik op de koppeling in de e-mail van New Relic. Hiermee opent u de browser naar de pagina Nieuw bericht voor aanmelding.

1. Selecteer op de pagina Nieuw reliëf de optie **Bent u uw wachtwoord vergeten?**.

   ![Nieuwe aanmelding voor Relic](/help/implementing/cloud-manager/assets/new-relic/newrelic-1.png)

1. Voer het e-mailadres in waar u het bevestigingsbericht hebt ontvangen en selecteer **Mijn terugstelkoppeling verzenden**.

   ![E-mailadres invoeren](/help/implementing/cloud-manager/assets/new-relic/newrelic-2.png)

1. Met Nieuwe advertentie ontvangt u een e-mail met een koppeling om het account te bevestigen.

Als je geen bevestigingsbericht van New Relic ontvangt, kun je naar de [sectie Problemen oplossen.](#troubshooting)

## Toegang krijgen tot nieuwe advertentie {#accessing-new-relic}

Zodra u [je nieuwe account heeft geactiveerd,](#activate-account) u hebt toegang tot New Relic One via Cloud Manager of rechtstreeks.

Ga als volgt te werk om toegang te krijgen tot nieuwe versie van Relic One via Cloud Manager:

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie.

1. Klik op het programma waarvoor u tot Nieuwe Relic wilt toegang hebben.

1. Naar de **Omgevingen** van de **Programmaoverzicht** pagina door op de knop **Omgevingen** aan de bovenkant van het scherm.

1. Op de **Omgevingen** scherm, klik de ellipsieknoop bij de bovenkant van het scherm naast het **Omgeving toevoegen** knop.

1. Klik in het menu Ovaal op **Nieuw bericht openen**.

1. Meld u aan bij Nieuwe lokale site op het nieuwe browsertabblad dat wordt geopend.

Om tot Nieuwe Relic rechtstreeks toegang te hebben:

1. Navigeer naar de aanmeldingspagina van New Relic op [`https://login.newrelic.com/login`](https://login.newrelic.com/login)

1. Meld u aan bij Nieuwe lokale versie.

### Je e-mail verifiëren {#verify-email}

Als u wordt gevraagd uw e-mail te verifiëren tijdens het aanmelden bij Nieuwe Relic One, betekent dit dat uw e-mail is gekoppeld aan meerdere accounts. Op deze manier kunt u kiezen welk account u wilt openen.

Als u uw e-mailadres niet verifieert, probeert New Relic u aan te melden met de laatst gemaakte gebruikersrecord die aan uw e-mailadres is gekoppeld. Als u wilt voorkomen dat uw e-mail tijdens elke aanmelding wordt gecontroleerd, klikt u op de knop **Onthoud mijn gegevens** Schakel het selectievakje in het aanmeldingsscherm in.

Voor meer hulp, gelieve een steunkaartje via te openen [Ondersteuningsportaal voor AEM](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html).

## Het oplossen van problemen Nieuwe Relic Één Toegang {#troubleshooting}

Als u als Nieuwe Relic Één gebruiker zoals die in de sectie wordt beschreven werd toegevoegd [Nieuwe online-gebruikers beheren](#manage-users) en kan de originele accountbevestigingsmail niet vinden volg deze stappen.

1. Navigeer naar de aanmeldingspagina van New Relic op [`login.newrelic.com/login`](https://login.newrelic.com/login).

1. Selecteren **Bent u uw wachtwoord vergeten?**.

   ![Nieuwe aanmelding voor Relic](/help/implementing/cloud-manager/assets/new-relic/newrelic-1.png)

1. Voer het e-mailadres in dat is gebruikt om uw account te maken en selecteer **Mijn terugstelkoppeling verzenden**.

   ![E-mailadres invoeren](/help/implementing/cloud-manager/assets/new-relic/newrelic-2.png)

1. Met Nieuwe advertentie ontvangt u een e-mail met een koppeling om het account te bevestigen.

Als u het aanmeldingsproces hebt voltooid en zich niet kunt aanmelden bij uw account vanwege e-mail- of wachtwoordfoutberichten, registreert u een ondersteuningsticket via [Admin Console.](https://adminconsole.adobe.com/)

Als je geen e-mail van New Relic ontvangt:

* Controleer uw [spamfilters](https://docs.newrelic.com/docs/accounts/accounts-billing/account-setup/create-your-new-relic-account/).
* Indien van toepassing, [Nieuw bericht toevoegen aan uw e-maillijst van gewenste personen](https://docs.newrelic.com/docs/accounts/accounts/account-maintenance/account-email-settings/#email-whitelist).
* Als geen van beide suggesties helpt, geef dan feedback op het ondersteuningsticket en Adobe Support-team helpt u verder.

## Beperkingen {#limitations}

De volgende beperkingen zijn van toepassing op het toevoegen van gebruikers aan Nieuwe Relic Één:

* Er kunnen maximaal 25 gebruikers worden toegevoegd. Als het maximumaantal gebruikers is bereikt, verwijdert u gebruikers om nieuwe gebruikers toe te voegen.
* De gebruikers die aan Nieuw Relic worden toegevoegd zullen van het type zijn **Beperkt** verwijzen naar [de Nieuwe Relische documentatie voor details.](https://docs.newrelic.com/docs/accounts/original-accounts-billing/original-users-roles/users-roles-original-user-model/#:~:text=In%20general%2C%20Admins%20take%20responsibility,Restricted%20Users%20can%20use%20them.&amp;text=One%20or%20more%20individuen%20who,change)%20any%20New%20Relic%20features.)
* AEM as a Cloud Service biedt slechts de Nieuwe Relic Één APM oplossing aan en verleent geen steun voor alarmering, registreren, of API integratie.

Voor meer hulp of extra begeleiding op Nieuw Relic Één dienstenaanbod voor uw AEM as a Cloud Service Programma, gelieve een steunkaartje via te openen [Ondersteuningsportaal voor AEM](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html).

## Veelgestelde vragen over Nieuwe Relic One {#faqs}

### Wat controleert Adobe met Nieuwe Relic Één? {#adobe-monitor}

Adobe volgt de AEM as a Cloud Service auteur, publiceert en voorproef (waar beschikbaar) de diensten via Nieuwe Relic One&#39;s Java-plug-in. Adobe maakt aangepaste New Relic One APM-telemetrie en bewaking mogelijk in niet-productie- en productie-AEM as a Cloud Service omgevingen.

Uw Nieuwe Relic One-account is gekoppeld aan een primaire Adobe-account en heeft meerdere toepassingen die erin rapporteren: drie per AEM as a Cloud Service omgeving.

* Eén toepassing voor de auteurservice per omgeving
* Eén toepassing voor de publicatieservice per omgeving (inclusief Golden Publish)
* Eén toepassing voor de voorbeeldservice per omgeving

Opmerking:

* Elke toepassing gebruikt één licentiecode.
* AEM as a Cloud Service milieu&#39;s rapporteren aan slechts één Nieuwe Relic Één rekening.
* De volledige controlemetriek en de gebeurtenissen voor beide Nieuwe Relic Één worden behouden voor zeven dagen.

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
