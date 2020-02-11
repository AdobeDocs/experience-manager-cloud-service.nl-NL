---
title: IMS-ondersteuning voor Adobe Experience Manager als Cloud Service
description: 'IMS-ondersteuning voor Adobe Experience Manager als Cloud Service '
translation-type: tm+mt
source-git-commit: bef17376f0b7de79511f9ad6ceb00e9f084f45d2

---


# IMS-ondersteuning voor Adobe Experience Manager als Cloud Service {#ims-support-for-aem-as-a-cloud-service}

## Inleiding {#introduction}

* AEM als Cloud Service omvat ondersteuning voor Admin Console voor AEM-instanties en verificatie op basis van het Adobe Identity Management System (IMS for short).
* Met de beheerconsole kunnen beheerders alle gebruikers van de Experience Cloud centraal beheren.
* Gebruikers en groepen kunnen worden toegewezen aan productprofielen die als Cloud Service-instanties aan AEM zijn gekoppeld, zodat zij zich bij die instantie kunnen aanmelden.

## Belangrijkste hooglichten {#key-highlights}

AEM als Cloud Service biedt alleen ondersteuning voor IMS-verificatie voor auteur-, Admin- en Dev-gebruikers. Het biedt geen ondersteuning voor externe eindgebruikers van klantsites zoals sitebezoekers.

* De beheerconsole zal klanten als organisaties IMS, auteur en Publish Instanties in een milieu als Instanties van de Context van het Product vertegenwoordigen. Hierdoor kunnen systeem- en productbeheerders de toegang tot instanties beheren.
* Productprofielen in de beheerconsole bepalen tot welke instanties een gebruiker toegang heeft.
* Klanten kunnen hun eigen SAML 2-compatibele identiteitsproviders (IDP for short) gebruiken voor Single Sign On.
* Alleen Enterprise- of federatieve id&#39;s voor Single Sign On van klant worden ondersteund, geen persoonlijke Adobe-id&#39;s.

## Architectuur {#architecture}

IMS-verificatie werkt met het OAuth-protocol tussen AEM en het Adobe IMS-eindpunt. Nadat een gebruiker aan IMS is toegevoegd en een Adobe-id heeft, kunnen deze zich aanmelden bij de AEM-auteurservice met IMS-referenties.

De gebruikerslogin stroom wordt hieronder getoond, zal de gebruiker aan IMS en naar keuze aan klant IDP voor SSO worden opnieuw gericht en dan terug naar AEM.

![IMS-architectuur](/help/security/assets/ims1.png)

## Instellen {#how-to-set-up}

### Organisaties aan boord nemen in Adobe Admin Console {#onboarding-orgs-to-adobe-admin-console}

Als u Adobe IMS voor AEM-verificatie wilt gebruiken, is het een eerste vereiste dat de klant zich aan boord kan stellen van de Adobe Admin Console.

Als eerste stap moeten klanten beschikken over een organisatie die is ingericht in Adobe IMS. Adobe Enterprise-klanten worden vertegenwoordigd als IMS-organisaties in de [Adobe Admin Console](https://helpx.adobe.com/enterprise/using/admin-console.html) . Dit is de portal die Adobe-klanten gebruiken om hun productrechten voor hun gebruikers en groepen te beheren.

AEM-klanten moeten al beschikken over een organisatie en als onderdeel van de IMS-provisioning worden de exemplaren van de klant beschikbaar gesteld in de beheerconsole voor het beheer van gebruikersrechten en toegang.

Zodra een klant als IMS Organisatie bestaat, zullen zij hun systeem moeten vormen zoals hieronder samengevat:

![IMS aan boord](/help/security/assets/ims2.png)

1. De aangewezen systeembeheerder ontvangt een uitnodiging om u aan te melden bij Cloud Manager. Nadat u zich hebt aangemeld bij Cloud Manager, kunnen de systeembeheerders ervoor kiezen AEM-programma&#39;s en -omgevingen in te stellen of naar de beheerconsole te gaan voor beheertaken.
1. De beheerder van het Systeem beweert een domein om de eigendom van het respectieve domein (bijvoorbeeld acme.com) te bevestigen
1. De Beheerder van het Systeem plaatst omhoog de Folders van de Gebruiker
1. De systeembeheerder voert de IDP-configuratie uit in de beheerconsole om Single Sign On in te stellen.
1. De beheerder AEM beheert de lokale groepen en de toestemmingen en de voorrechten zoals gebruikelijk.

De basisbeginselen van Adobe Identity Management, inclusief de IDP-configuratie, worden [hier](https://helpx.adobe.com/enterprise/using/set-up-identity.html)besproken.

Het gebruik van Enterprise Administration en Admin Console wordt [hier](https://helpx.adobe.com/enterprise/managing/user-guide.html)besproken.

### Gebruikers aan boord nemen in beheerconsole {#onboarding-users-in-admin-console}

Er zijn drie manieren aan boord van gebruikers afhankelijk van de grootte van de klant en hun voorkeur: U kunt handmatig gebruikers maken in Admin Console, een .csv-bestand uploaden of gebruikers synchroniseren vanuit de Active Directory van de onderneming van de klant.

**Handmatige toevoeging via de interface van de beheerconsole**

Gebruikers en groepen kunnen handmatig worden gemaakt in de interface van de beheerconsole. Deze methode kan worden gebruikt als u niet een groot aantal gebruikers te beheren hebt. Minder dan 50 AEM-gebruikers bijvoorbeeld of als de gebruikers die u al gebruikt deze methode gebruiken voor het beheer van andere Adobe-producten, zoals Analytics, Target of Creative Cloud-toepassingen.

![Gebruiker aan boord](/help/security/assets/ims3.png)

**Bestand uploaden in interface van beheerconsole**

Voor een eenvoudige afhandeling van het maken van gebruikers kan een `.csv` bestand worden geüpload om gebruikers in bulk toe te voegen.

![Bestand uploaden](/help/security/assets/ims4.png)

**Gereedschap Gebruikerssynchronisatie**

Met het hulpprogramma voor gebruikerssynchronisatie (UST in het kort) kunnen klanten in onze onderneming Adobe-gebruikers maken en beheren met Active Directory. Dit werkt ook voor andere geteste OpenLDAP-directoryservices. De doelgebruikers zijn de Beheerders van de Identiteit van IT (de Folder van de Onderneming of de Beheerders van het Systeem) die het hulpmiddel zullen kunnen installeren en vormen. Het opensource-programma kan worden aangepast, zodat klanten het kunnen aanpassen aan hun eigen specifieke vereisten.

Wanneer de looppas van de Synchronisatie van de Gebruiker, het een lijst van gebruikers van de Actieve Folder van de organisatie haalt en het met de lijst van gebruikers binnen de Console Admin vergelijkt.  Vervolgens wordt de Adobe-API voor gebruikersbeheer aangeroepen, zodat de beheerconsole wordt gesynchroniseerd met de directory van de organisatie. De veranderingsstroom is volledig één manier. Wijzigingen die u aanbrengt in de beheerconsole worden niet doorgestuurd naar de map.

Met dit hulpprogramma kan de systeembeheerder gebruikersgroepen in de map van de klant toewijzen aan productconfiguratie en gebruikersgroepen in de beheerconsole.

Voor het instellen van Gebruikerssynchronisatie moet de organisatie een set referenties maken op dezelfde manier als voor het gebruik van de [gebruikersbeheerAPI](https://www.adobe.io/apis/experienceplatform/umapi-new.html).

![Gereedschap Gebruikerssynchronisatie](/help/security/assets/ims5.png)

Het gereedschap Gebruikerssynchronisatie wordt [op deze locatie](https://github.com/adobe-apiplatform/user-sync.py/releases/latest)gedistribueerd via de gegevensopslagruimte van Adobe Github.

>[!NOTE]
>
> Een pre-releaseversie **2.4RC1** is beschikbaar met de dynamische steun van de groepsverwezenlijking en kan [hier](https://github.com/adobe-apiplatform/user-sync.py/releases/tag/v2.4rc1)worden gevonden.

De belangrijkste functies voor deze release zijn de mogelijkheid om nieuwe LDAP-groepen dynamisch toe te wijzen voor gebruikerslidmaatschap in de beheerconsole en om een dynamische gebruikersgroep te maken.

Meer informatie over de nieuwe groepsfuncties vindt u [op deze locatie](https://github.com/adobe-apiplatform/user-sync.py/blob/v2/docs/en/user-manual/advanced_configuration.md#additional-group-options).

**Documentatie gebruikerssynchronisatie**

Raadpleeg de documentatie [bij het](https://adobe-apiplatform.github.io/user-sync.py/en/) STUURPROGRAMMA voor meer informatie.

Het hulpprogramma voor gebruikerssynchronisatie moet zich met de [hier](https://adobe-apiplatform.github.io/umapi-documentation/en/UM_Authentication.html)beschreven procedure registreren als een Adobe I/O-client-UMAPI.

Documentatie over de Adobe I/O-console vindt u [hier](https://www.adobe.io/apis/cloudplatform/console.html).

De gebruikersbeheer-API die wordt gebruikt door het gereedschap Gebruikerssynchronisatie wordt [hier](https://www.adobe.io/apis/cloudplatform/umapi-new.html)besproken.

## Adobe-ervaring als Cloud Service-configuratie {#aem-configuration}

> [!NOTE]
>
>De vereiste AEM IMS-configuratie wordt automatisch geconfigureerd wanneer de AEM-omgevingen en -instanties worden ingericht. De beheerder kan het echter naar wens wijzigen met de [hier](/help/implementing/deploying/overview.md)beschreven methode.

De vereiste AEM IMS-configuratie wordt automatisch geconfigureerd wanneer de AEM-omgevingen en -instanties worden ingericht.  De beheerders van de klant kunnen een deel van de configuratie volgens hun vereisten wijzigen

De algemene aanpak bestaat uit het configureren van Adobe IMS als een OAuth-provider. De **Apache Jackrabbit Oak Default Sync Handler** kan net als bij LDAP-synchronisatie worden gewijzigd.

Hieronder vindt u de belangrijkste OSGI-configuraties die moeten worden gewijzigd om eigenschappen zoals Gebruikersautomatisch lidmaatschap of Groepstoewijzingen te wijzigen.

<!-- Arun to provide list of osgi configs -->

## Hoe wordt het gebruikt {#how-to-use}

### Producten en gebruikerstoegang beheren in beheerconsole {#managing-products-and-user-access-in-admin-console}

Wanneer de productbeheerder zich aanmeldt bij de beheerconsole, worden meerdere exemplaren van de AEM Managed Services-productcontext weergegeven, zoals hieronder wordt getoond:

![Inloggen bij instanties](/help/security/assets/ims6.png)

In dit voorbeeld heeft de org **AEM-MS-Onboard** 32 instanties die verschillende topologieën en omgevingen zoals het werkgebied of Prod overspannen.

![Instances login2](/help/security/assets/ims7.png)

Onder elke instantie van de Context van het Product, zullen er bijbehorende Profielen van het Product zijn. Deze productprofielen worden gebruikt voor het toewijzen van toegang tot gebruikers en groepen met de vereiste bevoegdheden.

Het profiel **Administrator_xxx** wordt gebruikt om beheerdersrechten toe te kennen in de bijbehorende AEM-instantie terwijl het profiel **User_xxx** wordt gebruikt om standaardgebruikers toe te voegen.

Gebruikers en groepen die zijn toegevoegd onder dit productprofiel, kunnen zich aanmelden bij die specifieke instantie, zoals in het onderstaande voorbeeld wordt getoond:

![Productprofiel](/help/security/assets/ims8.png)

### Aanmelden bij Adobe Experience Manager als cloudservice (#logging-in-to-name)

**Aanmelden bij lokale beheerder**

AEM kan lokale aanmeldingen voor Admin-gebruikers blijven ondersteunen. Het aanmeldingsscherm heeft een optie om u lokaal aan te melden:

![Lokale aanmelding](/help/security/assets/ims9.png)

<!-- the above image needs to be updated for skyline -->

**Op IMS gebaseerde aanmelding**

Voor andere gebruikers kan de op IMS gebaseerde aanmelding worden gebruikt zodra IMS op de instantie is geconfigureerd. De gebruiker klikt eerst op de knop Aanmelden met Adobe zoals hieronder wordt weergegeven:

![IMS-aanmelding](/help/security/assets/ims10.png)

Ze worden vervolgens omgeleid naar het IMS-aanmeldingsscherm en moeten hun referenties invoeren:

![IMS-aanmelding2](/help/security/assets/ims11.png)

![IMS-aanmelding3](/help/security/assets/ims12.png)

Als een gefedereerde IDP tijdens aanvankelijke opstelling van de Console Admin wordt gevormd, dan zal de gebruiker aan klant IDP voor SSO worden opnieuw gericht:

![IMS-aanmelding4](/help/security/assets/ims13.png)

Nadat de verificatie is voltooid, wordt de gebruiker opnieuw omgeleid naar AEM en aangemeld:

![IMS-aanmelding5](/help/security/assets/ims14.png)

### Rechten en ACL&#39;s beheren in Adobe Experience Manager als Cloud Service {#managing-permissions-in-aem}

ACLs en de toestemmingen zullen in AEM verder worden beheerd. De Gebruikersgroepen die van IMS worden gesynchroniseerd kunnen aan lokale groepen worden toegewezen waar ACLs en voorrechten worden bepaald.

In het onderstaande voorbeeld voegen we als voorbeeld gesynchroniseerde groepen toe aan de lokale **Dam_Users** -groep.

De gebruiker maakt deel uit van de volgende Groepen in IMS:

![ACL1](/help/security/assets/ims15.png)

Wanneer de gebruiker zich aanmeldt, worden hun groepslidmaatschappen gesynchroniseerd, zoals hieronder wordt getoond:

![ACL2](/help/security/assets/ims16.png)

In AEM kunnen de gebruikersgroepen die via IMS zijn gesynchroniseerd, als leden worden toegevoegd aan bestaande lokale groepen, zoals **DAM-gebruikers**.

![ACL3](/help/security/assets/ims17.png)

Zoals hieronder getoond, erft de groep **AEM-GRP_008** de toestemmingen en de voorrechten van gebruikers **** DAM, is dit een efficiënte manier om Toestemmingen voor gesynchroniseerde groepen te beheren en algemeen gebruikt in de op LDAP gebaseerde Methode van de Authentificatie eveneens.

![ACL3](/help/security/assets/ims18.png)