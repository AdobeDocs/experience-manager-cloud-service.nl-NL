---
title: IMS-ondersteuning voor Adobe Experience Manager as a Cloud Service
description: IMS-ondersteuning voor Adobe Experience Manager as a Cloud Service
translation-type: tm+mt
source-git-commit: c03e219d8261451e1215cf95babcbd4c1862d321

---


# IMS-ondersteuning voor Adobe Experience Manager as a Cloud Service {#ims-support-for-aem-as-a-cloud-service}

## Inleiding {#introduction}

* AEM as a Cloud Service omvat ondersteuning voor Admin Console voor AEM-instanties en verificatie op basis van het Adobe Identity Management System (afgekort IMS).
* Met de Admin Console kunnen beheerders alle gebruikers van Experience Cloud centraal beheren.
* Gebruikers en groepen kunnen worden toegewezen aan productprofielen die zijn gekoppeld aan AEM as a Cloud Service-instanties, zodat ze zich bij deze instantie kunnen aanmelden.

## Belangrijkste kenmerken {#key-highlights}

AEM as a Cloud Service biedt alleen ondersteuning voor IMS-verificatie voor authoring-, beheer- en ontwikkelaargebruikers. Het programma biedt geen ondersteuning voor externe eindgebruikers van klantsites, zoals sitebezoekers.

* De Admin Console zal klanten als IMS-organisaties, Author- en Publish-instanties in een omgeving als Product Context-instanties representeren. Hierdoor kunnen systeem- en productbeheerders de toegang tot instanties beheren.
* Productprofielen in de Admin Console bepalen tot welke instanties een gebruiker toegang heeft.
* Klanten kunnen hun eigen SAML 2-compatibele identiteitsproviders (afgekort IDP) gebruiken voor &#39;Single Sign On&#39; (eenmalig aanmelden).
* Alleen Enterprise- of federatieve id&#39;s voor Single Sign On (eenmalige aanmelding) van klanten worden ondersteund, geen persoonlijke Adobe ID&#39;s.

## Architectuur {#architecture}

IMS-verificatie werkt met het OAuth-protocol tussen AEM en het Adobe IMS-eindpunt. Zodra een gebruiker aan IMS is toegevoegd en een Adobe ID heeft, kan deze zich aanmelden bij de AEM-auteursservice met IMS-referenties.

De workflow voor gebruikersaanmelding wordt hieronder weergegeven; de gebruiker wordt doorgeleid naar IMS, optioneel naar de klant-IDP voor SSO, en vervolgens teruggeleid naar AEM.

![IMS-architectuur](/help/security/assets/ims1.png)

## Instellen {#how-to-set-up}

### Organisaties on-boarden in Adobe Admin Console {#onboarding-orgs-to-adobe-admin-console}

Als u Adobe IMS voor AEM-verificatie wilt gebruiken, is het on-boarden van de klant een eerste vereiste voor het gebruik van de Adobe IMS voor AEM-verificatie.

Als eerste stap moeten klanten een organisatie hebben in Adobe IMS. Adobe Enterprise-klanten worden gerepresenteerd als IMS-organisaties in de [Adobe Admin Console](https://helpx.adobe.com/nl/enterprise/using/admin-console.html). Dit is de portal die Adobe-klanten gebruiken om hun productrechten voor hun gebruikers en groepen te beheren.

AEM-klanten moeten al een organisatie hebben, en als onderdeel van de IMS-provisioning worden de instanties van de klant beschikbaar gesteld in de Admin Console voor het beheer van gebruikersrechten en toegang.

Zodra een klant bestaat als IMS-organisatie, moet deze zijn/haar systeem configureren zoals hieronder samengevat:

![IMS on-boarden](/help/security/assets/ims2.png)

1. De aangewezen systeembeheerder ontvangt een uitnodiging om zich aan te melden bij Cloud Manager. Na aanmelding bij Cloud Manager kunnen de systeembeheerders ervoor kiezen AEM-programma&#39;s en -omgevingen in te stellen of naar de Admin Console te gaan voor beheertaken.
1. De systeembeheerder claimt een domein om het eigenaarschap van het respectieve domein (bijvoorbeeld acme.com) te bevestigen
1. De systeembeheerder stelt gebruikersdirectory&#39;s in
1. De systeembeheerder voert de IDP-configuratie uit in de Admin Console om de functie voor Single Sign On (eenmalig aanmelden) in te stellen.
1. De AEM-beheerder beheert de lokale groepen en toestemmingen en machtigingen, zoals gebruikelijk.

De basisbeginselen van Adobe Identity Management, inclusief de IDP-configuratie, worden [hier](https://helpx.adobe.com/nl/enterprise/using/set-up-identity.html) besproken.

Het gebruik van Enterprise Administration en Admin Console wordt [hier](https://helpx.adobe.com/nl/enterprise/managing/user-guide.html) besproken.

### Gebruikers on-boarden in Admin Console {#onboarding-users-in-admin-console}

Er zijn drie manieren voor het on-boarden van gebruikers, afhankelijk van de grootte en voorkeur van de klant: u kunt handmatig gebruikers maken in Admin Console, een csv-bestand uploaden, of gebruikers synchroniseren vanuit de Active Directory van de onderneming van de klant.

**Handmatige toevoeging via de gebruikersinterface van de Admin Console**

Gebruikers en groepen kunnen handmatig worden gemaakt in de gebruikersinterface van de Admin Console. Deze methode kan worden gebruikt als u niet veel gebruikers hoeft te beheren. Bijvoorbeeld minder dan 50 AEM-gebruikers, of als u deze methode al gebruikt voor het beheer van andere Adobe-producten als Analytics, Target of Creative Cloud-applicaties.

![Gebruiker on-boarden](/help/security/assets/ims3.png)

**Bestand uploaden in de gebruikersinterface van Admin Console**

Als u op een eenvoudige manier gebruikers wilt maken, kunt u een `.csv`-bestand uploaden om een aantal gebruikers tegelijk toe te voegen.

![Bestand uploaden](/help/security/assets/ims4.png)

**User Sync Tool**

Met de User Sync Tool (afgekort UST, tool voor gebruikerssynchronisatie) kunnen onze zakelijke klanten Adobe-gebruikers maken en beheren met Active Directory. Dit werkt ook voor andere geteste OpenLDAP-directoryservices. De doelgebruikers zijn de IT Identity Administrators (Enterprise Directory or System Admins) die de tool kunnen installeren en configureren. De opensourcetool kan door klanten worden aangepast aan hun specifieke vereisten.

Wanneer User Sync wordt uitgevoerd, wordt een lijst met gebruikers uit de Active Directory van de organisatie opgehaald en vergeleken met de lijst gebruikers in de Admin Console.  Vervolgens wordt de Adobe User Management-API opgeroepen, zodat de Admin Console wordt gesynchroniseerd met de directory van de organisatie. De wijzigingsflow is uitsluitend eenrichtingsverkeer. Wijzigingen die u aanbrengt in de Admin Console, worden niet doorgestuurd naar de directory.

Met deze tool kan de systeembeheerder gebruikersgroepen in de directory van de klant toewijzen met productconfiguratie en gebruikersgroepen in de Admin Console.

Voor het instellen van User Sync moet de organisatie een set referenties maken op dezelfde manier als voor het gebruik van de [User Management-API](https://www.adobe.io/apis/experienceplatform/umapi-new.html).

![User Sync Tool](/help/security/assets/ims5.png)

De User Sync Tool wordt [op deze locatie](https://github.com/adobe-apiplatform/user-sync.py/releases/latest)gedistribueerd via de Adobe Github-repository.

>[!NOTE]
>
> Er is een pre-releaseversie **2.4RC1** beschikbaar met ondersteuning voor het maken van dynamische groepen, die u [hier](https://github.com/adobe-apiplatform/user-sync.py/releases/tag/v2.4rc1) vindt.

De belangrijkste functies voor deze versie zijn de mogelijkheid om nieuwe LDAP-groepen dynamisch toe te wijzen voor gebruikerslidmaatschap in de Admin Console, en het maken van dynamische gebruikersgroepen.

Meer informatie over de nieuwe groepsfuncties vindt u [op deze locatie](https://github.com/adobe-apiplatform/user-sync.py/blob/v2/docs/en/user-manual/advanced_configuration.md#additional-group-options).

**User Sync-documentatie**

Raadpleeg de [UST-documentatie](https://adobe-apiplatform.github.io/user-sync.py/en/) voor meer informatie.

De User Sync Tool moet worden geregistreerd als een Adobe I/O-client-UMAPI volgens [deze](https://adobe-apiplatform.github.io/umapi-documentation/en/UM_Authentication.html) procedure.

Documentatie over de Adobe I/O-console vindt u [hier](https://www.adobe.io/apis/cloudplatform/console.html).

De User Management-API die door de User Sync Tool wordt gebruikt, wordt [hier](https://www.adobe.io/apis/cloudplatform/umapi-new.html) besproken.

## Adobe Experience as a Cloud Service configureren {#aem-configuration}

>[!NOTE]
>
>De vereiste AEM IMS-configuratie wordt automatisch geconfigureerd wanneer de AEM-omgevingen en -instanties worden ingericht. De beheerder kan dit echter naar wens wijzigen volgens de [hier](/help/implementing/deploying/overview.md) beschreven methode.

De vereiste AEM IMS-configuratie wordt automatisch geconfigureerd wanneer de AEM-omgevingen en -instanties worden ingericht.  Klantbeheerders kunnen een deel van de configuratie naar wens van de klanten wijzigen

De algemene aanpak bestaat in het configureren van Adobe IMS als een OAuth-provider. De **Apache Jackrabbit Oak Default Sync Handler** kan worden gewijzigd, net als bij LDAP-synchronisatie.

Hieronder vindt u de belangrijkste OSGI-configuraties die moeten worden aangepast om eigenschappen voor automatisch gebruikerslidmaatschap of groepstoewijzingen te wijzigen.

<!-- Arun to provide list of osgi configs -->

## Het gebruik {#how-to-use}

### Producten en gebruikerstoegang beheren in Admin Console {#managing-products-and-user-access-in-admin-console}

Wanneer de productbeheerder zich aanmeldt bij Admin Console, worden meerdere instanties van de AEM Managed Services-productcontext weergegeven, zoals hieronder wordt getoond:

![Instantieaanmelding](/help/security/assets/ims6.png)

In dit voorbeeld heeft de organisatie **AEM-MS-Onboard** 32 instanties die verschillende topologieën en omgevingen voor bijvoorbeeld fase of productie omspannen.

![Instantieaanmelding2](/help/security/assets/ims7.png)

Onder elke Context Product-instantie zijn er bijbehorende productprofielen. Deze productprofielen worden gebruikt voor het toewijzen van toegang aan gebruikers en groepen met de vereiste bevoegdheden.

Het profiel **Administrator_xxx** wordt gebruikt om beheerdersrechten toe te kennen in de bijbehorende AEM-instantie, terwijl het profiel **User_xxx** wordt gebruikt om standaardgebruikers toe te voegen.

Gebruikers en groepen die zijn toegevoegd onder dit productprofiel, kunnen zich aanmelden bij deze instantie, zoals in het onderstaande voorbeeld wordt getoond:

![Productprofiel](/help/security/assets/ims8.png)

### Aanmelden bij Adobe Experience Manager as a Cloud Service {#logging-in-to-aem}

**Aanmelden bij lokale beheerder**

AEM kan lokale aanmeldingen voor Admin-gebruikers blijven ondersteunen. Het aanmeldingsscherm heeft een optie voor lokale aanmelding:

![Lokale aanmelding](/help/security/assets/ims9.png)

<!-- the above image needs to be updated for skyline -->

**Op IMS gebaseerde aanmelding**

Voor andere gebruikers kan de op IMS gebaseerde aanmelding worden gebruikt zodra IMS in de instantie is geconfigureerd. De gebruiker klikt eerst op de knop Aanmelden met Adobe zoals hieronder wordt weergegeven:

![IMS-aanmelding](/help/security/assets/ims10.png)


>[!NOTE]
> Elke gebruiker die in IMS is gemaakt, kan met een Adobe-id of federatieve id worden gemaakt. Als een gebruiker wordt ingesteld met een Adobe-id, wordt deze geverifieerd met de Identiteitsprovider van het bedrijf.

De gebruiker wordt vervolgens omgeleid naar het IMS-aanmeldingsscherm en moet zijn/haar referenties invoeren:

![IMS-aanmelding2](/help/security/assets/ims11.png)

![IMS-aanmelding3](/help/security/assets/ims12.png)

Als een federatieve IDP tijdens de eerste installatie van de Admin Console wordt geconfigureerd, wordt de gebruiker omgeleid naar de klant-IDP voor SSO:

![IMS-aanmelding4](/help/security/assets/ims13.png)

Nadat de verificatie is voltooid, wordt de gebruiker teruggeleid naar AEM en aangemeld:

![IMS-aanmelding5](/help/security/assets/ims14.png)

### Toestemmingen en ACL&#39;s beheren in Adobe Experience Manager as a Cloud Service {#managing-permissions-in-aem}

De ACL&#39;s en toestemmingen worden nog steeds beheerd in AEM. De gebruikersgroepen die vanaf IMS worden gesynchroniseerd, kunnen worden toegewezen aan lokale groepen waar ACL&#39;s en rechten zijn gedefinieerd.

In het onderstaande voorbeeld voegen we gesynchroniseerde groepen toe aan de lokale **Dam_Users**-groep.

De gebruiker maakt deel uit van de volgende groepen in IMS:

![ACL1](/help/security/assets/ims15.png)

Wanneer de gebruiker zich aanmeldt, worden diens groepslidmaatschappen gesynchroniseerd zoals hieronder weergegeven:

![ACL2](/help/security/assets/ims16.png)

In AEM kunnen de gebruikersgroepen die via IMS zijn gesynchroniseerd, als leden worden toegevoegd aan bestaande lokale groepen zoals **DAM-gebruikers**.

![ACL3](/help/security/assets/ims17.png)

Zoals hieronder getoond neemt de groep **AEM-GRP_008** de toestemmingen en de rechten van **DAM-gebruikers** over; dit is een effectieve manier om toestemmingen voor gesynchroniseerde groepen te beheren, en deze wordt ook algemeen gebruikt in de op LDAP gebaseerde verificatie.

![ACL3](/help/security/assets/ims18.png)


### Cloud Manager openen {#accessing-cloud-manager}

Als u toegang wilt tot Cloud Manager of AEM als een Cloud Service-omgeving, moet u worden toegewezen aan profielen van het Cloud Manager-product.

Raadpleeg [Roldefinities](/help/onboarding/what-is-required/add-users-roles.md#role-definitions) voor meer informatie over rollen voor gebruikers die de beschikbaarheid van specifieke functies in Cloud Manager bepalen.

>[!NOTE]
>Cloud Manager heeft vooraf geconfigureerde rollen met de juiste machtigingen. Om over elk van de rollen met specifieke toestemmingen, pre-gevormde taken, of toestemmingen, verbonden aan elke rol te leren, verwijs naar Op [Rol gebaseerde Toestemmingen](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/what-is-required/role-based-permissions.html).

**Stappen voor het toevoegen van een Gebruiker**

1. Voeg een gebruiker aan een bepaald profiel of van het bestaande scherm van de gebruiker of van een nieuw gebruikersscherm toe.

1. U kunt ook een gebruiker toevoegen vanuit het scherm **Overzicht** , zoals in de onderstaande afbeelding wordt getoond.

   ![ACL3](/help/security/assets/ims23.png)

   >[!NOTE]
   >U kunt meerdere profielen aan een gebruiker toewijzen, zoals in de onderstaande afbeelding wordt getoond.

   ![ACL3](/help/security/assets/ims22.png)


1. Nadat u aan het juiste profiel bent toegevoegd, hebt u via [Adobe Experience Cloud](http://my.cloudmanager.adobe.com) toegang tot de respectievelijke huurders in Cloud Manager via de rechterbovenhoek van de gebruikersinterface.


### Instantie in AEM benaderen als cloudservice {#accessing-instance-cloud-service}

>[!IMPORTANT]
>De stappen die in het voorgaande gedeelte worden vermeld, moeten al zijn uitgevoerd voordat u toegang krijgt tot een instantie in AEM als Cloud Service.

Als u toegang wilt hebben tot een AEM-instantie in de **beheerconsole**, raadpleegt u het Cloud Manager-programma en de omgevingen in het programma in de productlijst in de **beheerconsole**.

In de onderstaande schermafbeelding ziet u bijvoorbeeld twee beschikbare omgevingen, namelijk de *dev-auteur* en een *publicatie*.

![ACL3](/help/security/assets/ims19.png)

Om toegang te krijgen tot AEM-instanties moet de gebruiker worden toegevoegd aan een groep van het desbetreffende Cloud Service Product.

Elke instantie van de auteur heeft een AEM-beheerdersprofiel en een AEM-gebruikersprofiel en elke publicatie-instantie heeft een AEM-gebruikersprofiel. U kunt desgewenst andere profielen toevoegen.

Als u toegang tot het beheerniveau wilt krijgen tot de AEM-instantie, voegt u de gebruiker toe aan het AEM-beheerdersprofiel voor dat specifieke product.

