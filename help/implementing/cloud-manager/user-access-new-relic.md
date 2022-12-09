---
title: Nieuwe Relic One
description: Meer informatie over de service voor het controleren van de prestaties van New Relic One-toepassingen (APM) voor AEM as a Cloud Service en over hoe u deze service kunt gebruiken.
exl-id: 9fa0c5eb-415d-4e56-8136-203d59be927e
source-git-commit: 9089c66a2fdb5a05eb888e2af736862aff1b7a11
workflow-type: tm+mt
source-wordcount: '1607'
ht-degree: 0%

---


# Nieuwe Relic One {#user-access}

Meer informatie over de service voor het controleren van de prestaties van New Relic One-toepassingen (APM) voor AEM as a Cloud Service en over hoe u deze service kunt gebruiken.

## Inleiding {#introduction}

Adobe legt een grote nadruk op de controle, de beschikbaarheid, en de prestaties van uw toepassing. AEM as a Cloud Service biedt toegang tot een aangepaste New Relic One Monitoring-suite als onderdeel van de standaard productaanbieding om ervoor te zorgen dat uw teams optimaal zichtbaar zijn voor uw AEM as a Cloud Service systeem- en omgevingsprestaties.

In dit document wordt beschreven hoe u de toegang beheert tot de APM-functies (Application Performance Monitoring) van de New Relic One-toepassing die in uw AEM as a Cloud Service omgevingen zijn ingeschakeld, zodat u de prestaties kunt ondersteunen en optimaal kunt profiteren van AEM as a Cloud Service.

Wanneer een nieuw productieprogramma wordt gecreeerd, wordt de subrekening van New Relic One verbonden aan uw AEM as a Cloud Service Programma automatisch gecreeerd.

## Functies {#transaction-monitoring}

New Relic One APM for AEM as a Cloud Service heeft veel functies.

* Directe toegang tot een toegewezen New Relic One-account

* New Relic One APM-agent met instrumenten die exacte methodeaanroepen met regelnummers weergeeft, inclusief externe afhankelijkheden en databases

* Holistische optimalisatie van prestaties door de belangrijkste meetgegevens van infrastructuur-vlakke controle evenals toepassing (Adobe Experience Manager) controle te combineren

* Blootstelling van AEM as a Cloud Service JMX-bonen en gezondheidscontroles direct binnen New Relic Insights-meetgegevens, waardoor een grondige inspectie van de prestaties van de toepassingsstapel en gezondheidsmaatstaven mogelijk is.

## New Relic One-gebruikers beheren {#manage-users}

Voer de volgende stappen uit om de gebruikers van uw New Relic One-subaccount voor uw AEM as a Cloud Service programma te definiëren.

>[!NOTE]
>
>Een gebruiker in **Zakelijke eigenaar** of **Implementatiebeheer** De rol moet worden het programma geopend om Nieuw Relic te leiden Één gebruikers.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie.

1. Klik op het programma waarvoor u de New Relic One-gebruikers wilt beheren.

1. Onder aan het dialoogvenster **Omgevingen** kaart op de pagina van het programmaoverzicht, klik de ellipsieknoop en selecteer **Gebruikers beheren**.

   ![Gebruikers beheren](assets/newrelic-manage-users.png)

   * U hebt ook toegang tot de **Gebruikers beheren** optie via de ellipsieknop boven aan het dialoogvenster **Omgevingen** van uw programma.

1. In de **New Relic-gebruikers beheren** voert u de voor- en achternaam in van de gebruiker die u wilt toevoegen en klikt u op de knop **Toevoegen** knop. Herhaal deze stap voor alle gebruikers die u wilt toevoegen.

   ![Gebruikers toevoegen](assets/newrelic-add-users.png)

1. Om een Nieuw Relic te verwijderen Één gebruikers, klik de schrappingsknoop bij het rechtereind van de rij die de gebruiker vertegenwoordigt.

1. Klikken **Opslaan** om de gebruikers te maken.

Nadat de gebruikers zijn gedefinieerd, stuurt New Relic een bevestigingsbericht naar elke gebruiker aan wie u toegang hebt verleend, zodat de gebruiker het installatieproces kan voltooien en zich kan aanmelden.

>[!NOTE]
>
>Als u de New Relic One-gebruikers beheert, moet u uzelf ook toevoegen als gebruiker om toegang te hebben. De **Zakelijke eigenaar** of **Implementatiebeheer** volstaat niet om toegang tot Nieuwe Relic te hebben. U moet uzelf ook als gebruiker maken.

## Je New Relic One-gebruikersaccount activeren {#activate-account}

Zodra een New Relic One-gebruikersaccount is gemaakt zoals beschreven in de voorbeeldsectie [New Relic One-gebruikers beheren](#manage-users), New Relic stuurt deze gebruikers een bevestigingsbericht naar het opgegeven adres. Om die rekeningen te gebruiken, moeten de gebruikers hun rekeningen met Nieuw Relic eerst activeren door hun wachtwoorden opnieuw in te stellen.

Voer de volgende stappen uit om uw account als New Relic-gebruiker te activeren.

1. Klik op de koppeling in het e-mailbericht van New Relic. Hiermee opent u de browser naar de pagina Nieuw bericht voor aanmelding.

1. Selecteer op de pagina Nieuw reliëf de optie **Bent u uw wachtwoord vergeten?**.

   ![Aanmelden bij New Relic](/help/implementing/cloud-manager/assets/new-relic/newrelic-1.png)

1. Voer het e-mailadres in waar u het bevestigingsbericht hebt ontvangen en selecteer **Mijn terugstelkoppeling verzenden**.

   ![E-mailadres invoeren](/help/implementing/cloud-manager/assets/new-relic/newrelic-2.png)

1. New Relic stuurt je een e-mail met een link om het account te bevestigen.

Als je geen bevestigingsbericht van New Relic hebt ontvangen, raadpleeg dan de [sectie Problemen oplossen.](#troubshooting)

## New Relic One openen {#accessing-new-relic}

Zodra u [je New Relic-account heeft geactiveerd,](#activate-account) u kunt New Relic One openen via Cloud Manager of rechtstreeks.

New Relic One openen via Cloud Manager:

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie.

1. Klik op het programma waartoe u New Relic One wilt openen.

1. Onder aan het dialoogvenster **Omgevingen** kaart op de pagina van het programmaoverzicht, klik de ellipsieknoop en selecteer **New Relic openen**.

   ![Gebruikers beheren](assets/newrelic-access.png)

   * U kunt New Relic ook benaderen via de ellipsknop boven aan het dialoogvenster **Omgevingen** van uw programma.

1. Meld u aan bij New Relic One op het nieuwe browsertabblad dat wordt geopend.

New Relic One rechtstreeks openen:

1. Ga naar de aanmeldingspagina van New Relic op [`https://login.newrelic.com/login`](https://login.newrelic.com/login)

1. Meld u aan bij New Relic One.

### Je e-mail verifiëren {#verify-email}

Als u wordt gevraagd uw e-mail te verifiëren tijdens het aanmelden bij Nieuwe Relic One, betekent dit dat uw e-mail is gekoppeld aan meerdere accounts. Op deze manier kunt u kiezen welk account u wilt openen.

Als u uw e-mailadres niet verifieert, probeert New Relic u aan te melden met de meest recente gebruikersrecord die aan uw e-mailadres is gekoppeld. Als u wilt voorkomen dat uw e-mail tijdens elke aanmelding wordt gecontroleerd, klikt u op de knop **Onthoud mijn gegevens** Schakel het selectievakje in het aanmeldingsscherm in.

Voor meer hulp, gelieve een steunkaartje via te openen [Ondersteuningsportaal voor AEM](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html).

## Problemen met New Relic One Access oplossen {#troubleshooting}

Als u als Nieuwe Relic Één gebruiker zoals die in de sectie wordt beschreven werd toegevoegd [New Relic One-gebruikers beheren](#manage-users) en kan de originele accountbevestigingsmail niet vinden volg deze stappen.

1. Ga naar de aanmeldingspagina van New Relic op [`login.newrelic.com/login`](https://login.newrelic.com/login).

1. Selecteren **Bent u uw wachtwoord vergeten?**.

   ![Aanmelden bij New Relic](/help/implementing/cloud-manager/assets/new-relic/newrelic-1.png)

1. Voer het e-mailadres in dat is gebruikt om uw account te maken en selecteer **Mijn terugstelkoppeling verzenden**.

   ![E-mailadres invoeren](/help/implementing/cloud-manager/assets/new-relic/newrelic-2.png)

1. New Relic stuurt je een e-mail met een link om het account te bevestigen.

Als u het aanmeldingsproces hebt voltooid en zich niet kunt aanmelden bij uw account vanwege e-mail- of wachtwoordfoutberichten, registreert u een ondersteuningsticket via [Admin Console.](https://adminconsole.adobe.com/)

Als je geen e-mail van New Relic ontvangt:

* Controleer uw [spamfilters](https://docs.newrelic.com/docs/accounts/accounts-billing/account-setup/create-your-new-relic-account/).
* Indien van toepassing, [New Relic toevoegen aan uw e-maillijst van gewenste personen](https://docs.newrelic.com/docs/accounts/accounts/account-maintenance/account-email-settings/#email-whitelist).
* Als geen van beide suggesties helpt, geef dan feedback op het ondersteuningsticket en Adobe Support-team helpt u verder.

## Beperkingen {#limitations}

Voor het toevoegen van gebruikers aan New Relic One gelden de volgende beperkingen:

* Er kunnen maximaal 25 gebruikers worden toegevoegd. Als het maximumaantal gebruikers is bereikt, verwijdert u gebruikers om nieuwe gebruikers toe te voegen.
* Gebruikers die aan New Relic worden toegevoegd, zijn van het type **Beperkt** verwijzen naar [de documentatie van New Relic voor meer informatie.](https://docs.newrelic.com/docs/accounts/original-accounts-billing/original-users-roles/users-roles-original-user-model/#:~:text=In%20general%2C%20Admins%20take%20responsibility,Restricted%20Users%20can%20use%20them.&amp;text=One%20or%20more%20individuen%20who,change)%20any%20New%20Relic%20features.)
* AEM as a Cloud Service biedt alleen de New Relic One APM-oplossing en biedt geen ondersteuning voor waarschuwingen, logboekregistratie of API-integratie.

Voor meer hulp of extra begeleiding over New Relic One-aanbiedingen voor uw AEM as a Cloud Service Programma, gelieve een steunkaartje via te openen [Ondersteuningsportaal voor AEM](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html).

## Veelgestelde vragen over New Relic One {#faqs}

### Wat controleert Adobe met Nieuwe Relic Één? {#adobe-monitor}

Adobe bewaakt de AEM as a Cloud Service auteur, publiceert en voorproef (indien beschikbaar) services via de New Relic One Java-plug-in. Adobe maakt aangepaste New Relic One APM-telemetrie en bewaking mogelijk in niet-productie- en productieomgevingen AEM as a Cloud Service omgevingen.

Uw Nieuwe Relic One-account is gekoppeld aan een primaire Adobe-account en heeft meerdere toepassingen die erin rapporteren: drie per AEM as a Cloud Service omgeving.

* Eén toepassing voor de auteurservice per omgeving
* Eén toepassing voor de publicatieservice per omgeving (inclusief Golden Publish)
* Eén toepassing voor de voorbeeldservice per omgeving

Opmerking:

* Elke toepassing gebruikt één licentiecode.
* AEM as a Cloud Service omgevingen rapporteren slechts aan één New Relic One-account.
* De volledige controlemetriek en de gebeurtenissen voor beide Nieuwe Relic Één worden behouden voor zeven dagen.

### Wie heeft toegang tot de gegevens van de New Relic One Cloud Service? {#access-new-relic-cloud}

Volledige leestoegang wordt verleend voor maximaal 10 leden van uw team. Leestoegang omvat alle APM-meetgegevens die door de New Relic One-agent zijn verzameld.

### Wordt aangepaste SSO-configuratie ondersteund? {#custom-sso}

De configuratie van SSO van de douane wordt niet gesteund voor Nieuwe Relic Één rekening die door Adobe wordt voorzien.

### Wat gebeurt er als ik al een New Relic-abonnement heb op de locatie? {#new-relic-subscription}

New Relic One is het nieuwe platform voor waarneming vanuit New Relic en biedt ondersteuning van Adobe en uw teams de mogelijkheid om metingen en gebeurtenissen op één plaats te observeren, te controleren en weer te geven.

New Relic One biedt gebruikers de mogelijkheid om te zoeken in alle accounts waar ze toegang hebben tot de gegevens van alle services en hosts in één weergave en deze zichtbaar te maken.

Terwijl de steun van Adobe de AEM as a Cloud Service toepassing zal controleren gebruikend New Relic One en andere interne hulpmiddelen als deel van uw dienst, kunnen uw teams New Relic voor op-gebouw ontvangen diensten en infrastructuur blijven hefboomwerking. Ze kunnen de gegevens visualiseren van zowel de Adobe New Relic One-account als door de klant beheerde New Relic-accounts.

>[!NOTE]
>
>Om beide gegevensreeksen binnen New Relic One te bekijken, moet een gebruiker de juiste toestemmingen hebben en de zelfde login methodologie voor beide rekeningen (Adobe New Relic One en de klant-beheerde rekeningen van New Relic gebruiken).
