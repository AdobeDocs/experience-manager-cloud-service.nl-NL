---
title: New Relic One
description: Meer informatie over de service voor het controleren van de prestaties van New Relic One-toepassingen (APM) voor AEM as a Cloud Service en over hoe u deze service kunt gebruiken.
exl-id: 9fa0c5eb-415d-4e56-8136-203d59be927e
source-git-commit: d1b2226a1deec2e71056c43c84672cb4a358bc8c
workflow-type: tm+mt
source-wordcount: '1850'
ht-degree: 0%

---


# New Relic One {#user-access}

Meer informatie over de service voor het controleren van de prestaties van New Relic One-toepassingen (APM) voor AEM as a Cloud Service en over hoe u deze service kunt gebruiken.

## Inleiding {#introduction}

Adobe legt een grote nadruk op de controle, beschikbaarheid, en prestaties van uw toepassing. AEM as a Cloud Service biedt toegang tot een aangepaste New Relic One Monitoring-suite als onderdeel van de standaard productaanbieding om ervoor te zorgen dat uw teams optimaal zichtbaar zijn voor uw AEM as a Cloud Service systeem- en omgevingsprestaties.

In dit document wordt beschreven hoe u de toegang beheert tot de APM-functies (Application Performance Monitoring) van de New Relic One-toepassing die in uw AEM as a Cloud Service omgevingen zijn ingeschakeld, zodat u de prestaties kunt ondersteunen en optimaal kunt profiteren van AEM as a Cloud Service.

Wanneer een nieuw productieprogramma wordt gecreeerd, wordt de subrekening van New Relic One verbonden aan uw AEM as a Cloud Service Programma automatisch gecreeerd. [Deze subaccount moet worden geactiveerd](#activate-sub-account) om te beginnen met het innemen van gegevens.

## Functies {#transaction-monitoring}

New Relic One APM for AEM as a Cloud Service heeft veel functies.

* Directe toegang tot een toegewezen New Relic One-account

* New Relic One APM-agent met instrumenten die exacte methodeaanroepen met regelnummers weergeeft, inclusief externe afhankelijkheden en databases

* Holistische optimalisatie van prestaties door belangrijke metriek van infrastructuur-vlakke controle en toepassing (Adobe Experience Manager) controle te combineren

* Blootstelling van AEM as a Cloud Service JMX-bonen en gezondheidscontroles direct binnen New Relic Insights-meetgegevens, waardoor een grondige inspectie van de prestaties van de toepassingsstapel en gezondheidsmaatstaven mogelijk is.

## Je New Relic One-subaccount activeren {#activate-sub-account}

Voor een nieuw gemaakt programma wordt een New Relic One-subaccount voor u gemaakt. U moet het echter activeren om gegevens in te voeren. Dit wordt niet automatisch gedaan. Voer de volgende stappen uit om uw subaccount te activeren.

>[!NOTE]
>
>Een gebruiker in **Zakelijke eigenaar** of **Implementatiebeheer** Deze rol moet zijn aangemeld voor het beheer van de New Relic One-subaccount.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie.

1. Op de **[Mijn programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)** tikt of klikt u op het programma waarvoor u uw New Relic One-gebruikers wilt beheren.

1. Onder aan het dialoogvenster **Omgevingen** kaart op de pagina van het programmaoverzicht, klik de ellipsieknoop en selecteer **New Relic activeren**.

   ![Gebruikers beheren](assets/newrelic-activate-sub-account.png)

   * U hebt ook toegang tot de **Gebruikers beheren** optie via de ellipsieknop boven aan de **Omgevingen** van uw programma.

1. [Een pijplijn uitvoeren](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#running-pipelines) voor dezelfde omgeving tot een geslaagde voltooiing om de activering van de subrekening te voltooien.

Wanneer de subaccount wordt gedeactiveerd, worden geen gegevens ingevoerd.

## New Relic One-gebruikers beheren {#manage-users}

Voer de volgende stappen uit om de gebruikers van uw New Relic One-subaccount voor uw AEM as a Cloud Service programma te definiëren.

>[!NOTE]
>
>Een gebruiker in **Zakelijke eigenaar** of **Implementatiebeheer** rol moet zijn aangemeld om New Relic One-gebruikers te beheren.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie.

1. Klik op het programma waarvoor u de New Relic One-gebruikers wilt beheren.

1. Onder aan het dialoogvenster **Omgevingen** kaart op de pagina van het programmaoverzicht, klik de ellipsieknoop en selecteer **Gebruikers beheren**.

   ![Gebruikers beheren](assets/newrelic-manage-users.png)

   * U hebt ook toegang tot de **Gebruikers beheren** optie via de ellipsieknop boven aan de **Omgevingen** van uw programma.

1. In de **New Relic-gebruikers beheren** voert u de voor- en achternaam in van de gebruiker die u wilt toevoegen en klikt u op de knop **Toevoegen** knop. Herhaal deze stap voor alle gebruikers die u wilt toevoegen.

   ![Gebruikers toevoegen](assets/newrelic-add-users.png)

1. Als u een New Relic One-gebruiker wilt verwijderen, klikt u op de verwijderknop aan de rechterkant van de rij die de gebruiker vertegenwoordigt.

1. Klikken **Opslaan** om de gebruikers te maken.

Nadat de gebruikers zijn gedefinieerd, stuurt New Relic een bevestigingsbericht naar elke gebruiker aan wie u toegang hebt verleend, zodat de gebruiker het installatieproces kan voltooien en zich kan aanmelden.

>[!NOTE]
>
>Als u de New Relic One-gebruikers beheert, moet u uzelf ook toevoegen als gebruiker om toegang te hebben. Het zijn **Zakelijke eigenaar** of **Implementatiebeheer** volstaat niet om toegang te hebben tot New Relic One. U moet uzelf ook als gebruiker maken.

## Je New Relic One-gebruikersaccount activeren {#activate-user-account}

Zodra een New Relic One-gebruikersaccount is gemaakt zoals wordt beschreven in de voorbeeldsectie [New Relic One-gebruikers beheren](#manage-users), stuurt New Relic deze gebruikers een bevestigingsbericht naar het opgegeven adres. Als gebruikers deze accounts willen gebruiken, moeten ze eerst hun accounts bij New Relic activeren door hun wachtwoorden opnieuw in te stellen.

Voer de volgende stappen uit om uw account als New Relic-gebruiker te activeren.

1. Klik op de koppeling in het e-mailbericht van New Relic. Hierdoor wordt uw browser geopend voor de aanmeldingspagina van New Relic.

1. Selecteer op de New Relic-aanmeldpagina de optie **Bent u uw wachtwoord vergeten?**.

   ![Aanmelden bij New Relic](/help/implementing/cloud-manager/assets/new-relic/newrelic-1.png)

1. Voer het e-mailadres in waar u het bevestigingsbericht hebt ontvangen en selecteer **Mijn terugstelkoppeling verzenden**.

   ![E-mailadres invoeren](/help/implementing/cloud-manager/assets/new-relic/newrelic-2.png)

1. New Relic stuurt je een e-mail met een link om het account te bevestigen.

Als je geen bevestigingsbericht van New Relic ontvangt, zie [sectie Problemen oplossen.](#troubshooting)

## New Relic One openen {#accessing-new-relic}

Als u eenmaal [je New Relic-account heeft geactiveerd,](#activate-account) u kunt New Relic One openen via Cloud Manager of rechtstreeks.

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

Als u wordt gevraagd uw e-mail te verifiëren tijdens het aanmelden bij New Relic One, betekent dit dat uw e-mail is gekoppeld aan meerdere accounts. Hiermee kunt u kiezen welk account u wilt openen.

Als u uw e-mailadres niet verifieert, probeert New Relic u aan te melden met de meest recente gebruikersrecord die aan uw e-mailadres is gekoppeld. Als u wilt voorkomen dat uw e-mail tijdens elke aanmelding wordt gecontroleerd, klikt u op de knop **Mijn gegevens onthouden** Schakel het selectievakje in het aanmeldingsscherm in.

Voor meer hulp, open een steunkaartje door [Ondersteuningsportaal voor AEM](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html).

## Problemen met New Relic One-gebruikerstoegang oplossen {#troubleshooting}

Als u bent toegevoegd als New Relic One-gebruiker, zoals beschreven in de sectie [New Relic One-gebruikers beheren](#manage-users) en kan de originele accountbevestigingsmail niet vinden volg deze stappen.

1. Ga naar de aanmeldingspagina van New Relic op [`login.newrelic.com/login`](https://login.newrelic.com/login).

1. Selecteren **Bent u uw wachtwoord vergeten?**.

   ![Aanmelden bij New Relic](/help/implementing/cloud-manager/assets/new-relic/newrelic-1.png)

1. Voer het e-mailadres in dat is gebruikt om uw account te maken en selecteer **Mijn terugstelkoppeling verzenden**.

   ![E-mailadres invoeren](/help/implementing/cloud-manager/assets/new-relic/newrelic-2.png)

1. New Relic stuurt je een e-mail met een link om het account te bevestigen.

Als u het aanmeldingsproces hebt voltooid en u zich niet kunt aanmelden bij uw account vanwege e-mail- of wachtwoordfoutberichten, registreert u een ondersteuningsticket via [Admin Console.](https://adminconsole.adobe.com/)

Als je geen e-mail van New Relic ontvangt:

* Controleer uw [spamfilters](https://docs.newrelic.com/docs/accounts/accounts-billing/account-setup/create-your-new-relic-account/).
* Indien van toepassing, [New Relic toevoegen aan uw e-maillijst van gewenste personen](https://docs.newrelic.com/docs/accounts/accounts/account-maintenance/account-email-settings/#email-whitelist).
* Als geen van beide suggesties u helpt, geef terugkoppelen op het steunkaartje en het team van de Steun van de Adobe kan u helpen.

## Beperkingen {#limitations}

Voor het toevoegen van gebruikers aan New Relic One gelden de volgende beperkingen:

* Er kunnen maximaal 30 gebruikers worden toegevoegd. Als het maximumaantal gebruikers is bereikt, verwijdert u gebruikers om nieuwe gebruikers toe te voegen.
* Gebruikers die aan New Relic worden toegevoegd, zijn van het type **Beperkt**, zie [de documentatie van New Relic voor meer informatie.](https://docs.newrelic.com/docs/accounts/original-accounts-billing/original-users-roles/users-roles-original-user-model/#:~:text=In%20general%2C%20Admins%20take%20responsibility,Restricted%20Users%20can%20use%20them.&amp;text=One%20or%20more%20individuen%20who,change)
* AEM as a Cloud Service biedt alleen de New Relic One APM-oplossing en biedt geen ondersteuning voor waarschuwingen, logboekregistratie of API-integratie.

>[!NOTE]
>
>Als er gedurende 90 dagen of langer geen activiteit wordt gedetecteerd in uw New Relic One-subaccount, wordt de APM-agent gestopt.
>
>Voer dezelfde stappen uit in het dialoogvenster [Je New Relic One-subaccount activeren](#activate-sub-account) in dit document om uw New Relic One-subaccount opnieuw te activeren.

Voor meer hulp of extra hulp bij New Relic One-aanbiedingen voor uw AEM as a Cloud Service Programma, open een steunkaartje via [AEM Support Portal.](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html)

## Veelgestelde vragen over New Relic One {#faqs}

### Wat volgt de Adobe met New Relic One? {#adobe-monitor}

Adobe volgt de AEM as a Cloud Service auteur-, publicatie- en voorvertoningsservices (indien beschikbaar) via de New Relic One Java-plug-in. Adobe maakt aangepaste New Relic One APM telemetrie en bewaking mogelijk in niet-productie- en productie-AEM as a Cloud Service omgevingen.

Uw New Relic One-account is gekoppeld aan een account met een primaire Adobe en bevat meerdere toepassingen die erin worden gerapporteerd: drie per AEM as a Cloud Service omgeving.

* Eén toepassing voor de auteurservice per omgeving
* Eén toepassing voor de publicatieservice per omgeving (inclusief Golden Publish)
* Eén toepassing voor de voorbeeldservice per omgeving

Opmerking:

* Elke toepassing gebruikt één licentiecode.
* AEM as a Cloud Service omgevingen rapporteren slechts aan één New Relic One-account.
* De volledige meetgegevens en gebeurtenissen voor de bewaking van beide New Relic One worden zeven dagen bewaard.

### Verstuurt de Adobe waarschuwingsberichten van New Relic One? {#alerting-new-relic}

Adobe biedt New Relic One alleen toegang voor observatiedoeleinden en maakt er geen gebruik van voor klantwaarschuwingen of interne operationele waarschuwingen. Meldingen voor incidenten worden verzonden met [profielen voor gebruikersmeldingen.](/help/journey-onboarding/notification-profiles.md)

### Wie heeft toegang tot de gegevens van de New Relic One Cloud Service? {#access-new-relic-cloud}

Volledige leestoegang wordt verleend voor maximaal 30 leden van uw team. Leestoegang omvat alle APM-meetgegevens die door de New Relic One-agent zijn verzameld.

### Wordt aangepaste SSO-configuratie ondersteund? {#custom-sso}

Aangepaste SSO-configuratie wordt niet ondersteund voor de New Relic One-account die is ingericht door Adobe.

### Wat gebeurt er als ik al een New Relic-abonnement heb op de locatie? {#new-relic-subscription}

New Relic One is het nieuwe platform voor waarneming vanuit New Relic en biedt ondersteuning voor Adoben en uw teams in staat om op één plaats metingen en gebeurtenissen te observeren, te controleren en weer te geven.

New Relic One biedt gebruikers de mogelijkheid om te zoeken in alle accounts waar ze toegang hebben tot de gegevens van alle services en hosts in één weergave en deze zichtbaar te maken.

Terwijl de steun van de Adobe de AEM as a Cloud Service toepassing zal controleren gebruikend New Relic One en andere interne hulpmiddelen als deel van uw dienst, kunnen uw teams New Relic voor op-gebouw ontvangen diensten en infrastructuur blijven gebruiken. Ze kunnen de gegevens visualiseren van zowel de Adobe New Relic One-account als door de klant beheerde New Relic-accounts.

>[!NOTE]
>
>Om beide gegevensreeksen binnen New Relic One te bekijken, moet een gebruiker de juiste toestemmingen hebben en de zelfde login methodologie voor beide rekeningen (Adobe New Relic One en de klant-beheerde rekeningen van New Relic) gebruiken.

### De APM-agent voor mijn New Relic One-account wordt gestopt. Wat is er gebeurd? {#deactivated}

[APM-agents worden gestopt](#limitations) als gedurende 90 dagen of langer geen activiteit wordt gedetecteerd. Voer dezelfde stappen uit in het dialoogvenster [Je New Relic One-subaccount activeren](#activate-sub-account) in dit document om uw New Relic One-subaccount opnieuw te activeren.
