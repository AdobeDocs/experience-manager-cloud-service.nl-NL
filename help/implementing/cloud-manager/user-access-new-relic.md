---
title: New Relic One
description: Meer informatie over de service voor het controleren van de prestaties van New Relic One-toepassingen (APM) voor AEM as a Cloud Service en over hoe u deze service kunt gebruiken.
exl-id: 9fa0c5eb-415d-4e56-8136-203d59be927e
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 40a76e39750d6dbeb03c43c8b68cddaf515a2614
workflow-type: tm+mt
source-wordcount: '1825'
ht-degree: 0%

---


# New Relic One {#user-access}

Meer informatie over de service voor het controleren van de prestaties van New Relic One-toepassingen (APM) voor AEM as a Cloud Service en over hoe u deze service kunt gebruiken.

## Inleiding {#introduction}

Adobe legt een grote nadruk op de controle, beschikbaarheid, en prestaties van uw toepassing. AEM as a Cloud Service biedt toegang tot een aangepaste New Relic One Monitoring-suite als onderdeel van de standaard productaanbieding om ervoor te zorgen dat uw teams optimaal zichtbaar zijn voor uw AEM as a Cloud Service-systeem en omgevingsprestaties.

In dit document wordt beschreven hoe u de toegang beheert tot de APM-functies (New Relic One Application Performance Monitoring) die in uw AEM as a Cloud Service-omgevingen zijn ingeschakeld om de prestaties te ondersteunen en u in staat te stellen optimaal gebruik te maken van AEM as a Cloud Service.

Wanneer een nieuw productieprogramma wordt gemaakt, wordt automatisch de New Relic One-subaccount gemaakt die aan uw AEM as a Cloud Service-programma is gekoppeld. [ Deze sub-account moet ](#activate-sub-account) worden geactiveerd beginnen het opnemen gegevens.

## Functies {#transaction-monitoring}

New Relic One APM voor AEM as a Cloud Service heeft veel functies.

* Directe toegang tot een toegewezen New Relic One-account

* New Relic One APM-agent met instrumenten die exacte methodeaanroepen met regelnummers weergeeft, inclusief externe afhankelijkheden en databases

* Holistische optimalisatie van prestaties door belangrijke metriek van infrastructuur-vlakke controle en toepassing (Adobe Experience Manager) controle te combineren

* Blootstelling van AEM as a Cloud Service JMX-bonen en gezondheidscontroles direct binnen New Relic Insights-meetgegevens, zodat de prestaties van de toepassingenstapel en de gezondheidsmaatstaven grondig kunnen worden gecontroleerd.

## Je New Relic One-subaccount activeren {#activate-sub-account}

Voor een nieuw gemaakt programma wordt een New Relic One-subaccount voor u gemaakt. U moet het echter activeren om gegevens in te voeren. Dit wordt niet automatisch gedaan. Voer de volgende stappen uit om uw subaccount te activeren.

>[!NOTE]
>
>Een gebruiker in **BedrijfsEigenaar** of **de rol van de Manager van de Plaatsing** moet worden het programma geopend om sub-account van New Relic One te beheren.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, klik het programma waarvoor u uw gebruikers van New Relic One wilt beheren.

1. Bij de bodem van de **kaart van Milieu** op de pagina van het programmaoverzicht, klik https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg en selecteer **New Relic** activeren.

   ![ beheert gebruikers ](assets/newrelic-activate-sub-account.png)

   * U kunt tot **toegang hebben leidt gebruikers** optie door https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg bij de bovenkant van het **milieu&#39;s** scherm van uw programma te klikken.

1. [ stel een pijpleiding ](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#running-pipelines) voor het zelfde milieu in werking aan succesvolle voltooiing om de subrekeningsactivering te voltooien.

Wanneer de subaccount wordt gedeactiveerd, worden geen gegevens ingevoerd.

## New Relic One-gebruikers beheren {#manage-users}

Voer de volgende stappen uit om de gebruikers van uw New Relic One-subaccount voor uw AEM as a Cloud Service-programma te definiëren.

>[!NOTE]
>
>Een gebruiker in **BedrijfsEigenaar** of **de rol van de Manager van de Plaatsing** moet worden het programma geopend om de gebruikers van New Relic One te beheren.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Klik op het programma waarvoor u de New Relic One-gebruikers wilt beheren.

1. Bij de bodem van de **kaart van Milieu** op de pagina van het programmaoverzicht, klik https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg en selecteer **leiden gebruikers**.

   ![ beheert gebruikers ](assets/newrelic-manage-users.png)

   * U kunt tot **toegang hebben leidt gebruikers** optie door https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg bij de bovenkant van het **milieu&#39;s** scherm van uw programma te klikken.

1. In **beheer de gebruikers van New Relic** dialoog, ga de eerste en achternaam van de gebruiker in u wilt toevoegen, en klik **toevoegen** knoop. Herhaal deze stap voor alle gebruikers die u wilt toevoegen.

   ![ voeg gebruikers ](assets/newrelic-add-users.png) toe

1. Als u een New Relic One-gebruiker wilt verwijderen, klikt u op de verwijderknop aan de rechterkant van de rij die de gebruiker vertegenwoordigt.

1. Klik **sparen** om de gebruikers tot stand te brengen.

Nadat de gebruikers zijn gedefinieerd, stuurt New Relic een bevestigingsbericht naar elke gebruiker aan wie u toegang hebt verleend, zodat de gebruiker het installatieproces kan voltooien en zich kan aanmelden.

>[!NOTE]
>
>Als u de New Relic One-gebruikers beheert, moet u uzelf ook toevoegen als gebruiker om toegang te hebben. Het zijn van de **BedrijfsEigenaar** of **Manager van de Plaatsing** volstaat niet om toegang tot New Relic One te hebben. U moet uzelf ook als gebruiker maken.

## Je New Relic One-gebruikersaccount activeren {#activate-user-account}

Zodra een gebruikersrekening van New Relic One zoals die in de voorproefsectie [ wordt beschreven de Gebruikers van New Relic One beheren ](#manage-users) wordt gecreeerd, verzendt New Relic die gebruikers een bevestigingsmail naar het verstrekte adres. Als gebruikers deze accounts willen gebruiken, moeten ze eerst hun accounts bij New Relic activeren door hun wachtwoorden opnieuw in te stellen.

Voer de volgende stappen uit om uw account als New Relic-gebruiker te activeren.

1. Klik op de koppeling in het e-mailbericht van New Relic. Hierdoor wordt uw browser geopend voor de aanmeldingspagina van New Relic.

1. Op New Relic teken binnen pagina, uitgezochte **vergeten uw wachtwoord?**.

   ![ login van New Relic ](/help/implementing/cloud-manager/assets/new-relic/newrelic-1.png)

1. Ga het e-mailadres in waar u bevestigingse-mail ontving, en selecteer **verzend mijn terugstellings verbinding**.

   ![ ga e-mailadres ](/help/implementing/cloud-manager/assets/new-relic/newrelic-2.png) in

1. New Relic stuurt je een e-mail met een koppeling om de account te bevestigen.

Als u geen bevestigingse-mail van New Relic ontvangt, zie [ het oplossen van problemensectie ](#troubshooting).

## Toegang tot New Relic One {#accessing-new-relic}

Zodra u [ uw rekening van New Relic ](#activate-account) hebt geactiveerd, kunt u tot New Relic One als Cloud Manager of direct toegang hebben.

**om tot New Relic One door Cloud Manager toegang te hebben:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Klik op het programma waartoe u New Relic One wilt openen.

1. Bij de bodem van de **kaart van Milieu&#39;s** op de pagina van het programmaoverzicht, klik https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg en selecteer **Open New Relic**.

   ![ beheert gebruikers ](assets/newrelic-access.png)

   * U kunt tot New Relic ook toegang hebben door https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg bij de bovenkant van het **milieu&#39;s** scherm van uw programma te klikken.

1. Meld u aan bij New Relic One op het nieuwe browsertabblad dat wordt geopend.

**om tot New Relic One direct toegang te hebben:**

1. Ga naar de aanmeldingspagina van New Relic op [`https://login.newrelic.com/login` ](https://login.newrelic.com/login)

1. Meld u aan bij New Relic One.

### Uw e-mail verifiëren {#verify-email}

Als u wordt gevraagd uw e-mail te verifiëren tijdens het aanmelden bij New Relic One, betekent dit dat uw e-mail is gekoppeld aan meerdere accounts. U kunt kiezen welk account u wilt openen.

Als u uw e-mailadres niet verifieert, probeert New Relic u aan te melden met de meest recente gebruikersrecord die aan uw e-mailadres is gekoppeld. Vermijd het verifiëren van uw e-mail tijdens elke login, klik **me** checkbox in het login scherm herinneren.

Voor meer hulp, open een steunkaartje als [ AEM Portaal van de Steun ](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html).

## Problemen met New Relic One-gebruikerstoegang oplossen {#troubleshooting}

Als u als gebruiker van New Relic One zoals die in de sectie [ wordt beschreven de Gebruikers van New Relic One van Beheer ](#manage-users) werd toegevoegd en niet van de originele de bevestiging e-mail van de rekeningsbevestiging kan de plaats bepalen volg deze stappen.

1. Navigeer naar de aanmeldingspagina van New Relic op [`login.newrelic.com/login` ](https://login.newrelic.com/login) .

1. Selecteer **vergeten uw wachtwoord?**.

   ![ login van New Relic ](/help/implementing/cloud-manager/assets/new-relic/newrelic-1.png)

1. Ga het e-mailadres in dat werd gebruikt om uw rekening tot stand te brengen, en selecteer **verzend mijn terugstellings verbinding**.

   ![ ga e-mailadres ](/help/implementing/cloud-manager/assets/new-relic/newrelic-2.png) in

1. New Relic stuurt je een e-mail met een koppeling om de account te bevestigen.

Als u het aanmeldingsproces voltooit en niet aan uw rekening wegens e-mail of wachtwoordfoutenmeldingen kan aanmelden, registreer een steunkaartje als [ Admin Console ](https://adminconsole.adobe.com/).

Voer de volgende handelingen uit als u geen e-mail van New Relic hebt ontvangen:

* Controleer uw [ spamfilters ](https://docs.newrelic.com/docs/accounts/accounts-billing/account-setup/create-your-new-relic-account/).
* Indien van toepassing, [ voeg New Relic aan uw e-maillijst van gewenste personen ](https://docs.newrelic.com/docs/accounts/accounts/account-maintenance/account-email-settings/#email-whitelist) toe.
* Als geen van beide suggesties helpt, geef terugkoppelen op het steunkaartje.

## Beperkingen {#limitations}

Voor het toevoegen van gebruikers aan New Relic One gelden de volgende beperkingen:

* Er kunnen maximaal 30 gebruikers worden toegevoegd. Als het maximumaantal gebruikers is bereikt, verwijdert u gebruikers om nieuwe gebruikers toe te voegen.
* De gebruikers die aan New Relic worden toegevoegd zijn van het type **Beperkt**, zie [ de documentatie van New Relic voor details ](https://docs.newrelic.com/docs/accounts/original-accounts-billing/original-users-roles/users-roles-original-user-model/#:~:text=In%20general%2C%20Admins%20take%20responsibility,Restricted%20Users%20can%20use%20them.&amp;text=One%20or%20more%20individuen%20who,change).
* AEM as a Cloud Service biedt alleen de New Relic One APM-oplossing en biedt geen ondersteuning voor waarschuwingen, logboekregistratie of API-integratie.

>[!NOTE]
>
>Als er gedurende 90 dagen of langer geen activiteit wordt gedetecteerd in uw New Relic One-subaccount, wordt de APM-agent gestopt.
>
>Volg de zelfde stappen in [ activeer Uw sub-Rekening van New Relic One ](#activate-sub-account) sectie van dit document om uw sub-rekening van New Relic One opnieuw te activeren.

Voor meer hulp of extra begeleiding op het dienstenaanbod van New Relic One voor uw Programma van AEM as a Cloud Service, open een steunkaartje als [ AEM Portaal van de Steun ](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html).

## Veelgestelde vragen {#faqs}

+++

### Wat volgt de Adobe met New Relic One? {#adobe-monitor}

Adobe volgt de auteur-, publicatie- en voorvertoningsservices van AEM as a Cloud Service (indien beschikbaar) via de New Relic One Java-plug-in. Adobe maakt aangepaste New Relic One APM-telemetrie en bewaking mogelijk in niet-productie- en productie-AEM as a Cloud Service-omgevingen.

Uw New Relic One-account is gekoppeld aan een account met een primaire Adobe en bevat meerdere toepassingen die erin worden gerapporteerd: drie per AEM as a Cloud Service-omgeving.

* Eén toepassing voor de auteurservice per omgeving
* Eén toepassing voor de publicatieservice per omgeving (inclusief Golden Publish)
* Eén toepassing voor de voorbeeldservice per omgeving

Opmerking:

* Elke toepassing gebruikt één licentiecode.
* AEM as a Cloud Service-omgevingen rapporteren slechts aan één New Relic One-account.
* De volledige meetgegevens en gebeurtenissen voor de bewaking van beide New Relic One worden zeven dagen bewaard.
+++

+++

### Verstuurt de Adobe waarschuwingsberichten van New Relic One? {#alerting-new-relic}

Adobe biedt New Relic One alleen toegang voor observatiedoeleinden en maakt er geen gebruik van voor klantwaarschuwingen of interne operationele waarschuwingen. De berichten voor om het even welke incidenten worden verzonden gebruikend [ profielen van het gebruikersbericht ](/help/journey-onboarding/notification-profiles.md).
+++

+++

### Wie heeft toegang tot de gegevens van de New Relic One Cloud Service? {#access-new-relic-cloud}

Volledige leestoegang wordt verleend voor maximaal 30 leden van uw team. Leestoegang omvat alle APM-meetgegevens die door de New Relic One-agent worden verzameld.
+++

+++

### Wordt aangepaste SSO-configuratie ondersteund? {#custom-sso}

Aangepaste SSO-configuratie wordt niet ondersteund voor de New Relic One-account die is ingericht door Adobe.
+++

+++

### Wat gebeurt er als ik al een New Relic-abonnement heb op de locatie? {#new-relic-subscription}

New Relic One is het nieuwe platform voor waarneming vanuit New Relic en biedt ondersteuning voor Adoben en uw teams in staat om op één plaats metingen en gebeurtenissen te observeren, te controleren en weer te geven.

New Relic One biedt gebruikers de mogelijkheid om te zoeken in alle accounts waar ze toegang hebben tot de gegevens van alle services en hosts in één weergave en deze zichtbaar te maken.

Terwijl de steun van de Adobe de toepassing van AEM as a Cloud Service gebruikend New Relic One en andere interne hulpmiddelen als deel van uw dienst controleert, kunnen uw teams New Relic voor op-gebouw ontvangen diensten en infrastructuur blijven gebruiken. Ze kunnen de gegevens visualiseren van zowel de Adobe New Relic One-account als door de klant beheerde New Relic-accounts.

>[!NOTE]
>
>Om beide gegevensreeksen binnen New Relic One te bekijken, moet een gebruiker de juiste toestemmingen hebben en de zelfde login methodologie voor beide rekeningen (Adobe New Relic One en de klant-beheerde rekeningen van New Relic) gebruiken.

+++

+++

### De APM-agent voor mijn New Relic One-account wordt gestopt. Wat is er gebeurd? {#deactivated}

[ de agenten van APM worden tegengehouden ](#limitations) als geen activiteit voor 90 dagen of meer wordt ontdekt. Volg de zelfde stappen in [ activeer Uw sub-Rekening van New Relic One ](#activate-sub-account) sectie van dit document om uw sub-rekening van New Relic One opnieuw te activeren.
+++
