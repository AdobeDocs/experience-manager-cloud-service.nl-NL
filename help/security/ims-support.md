---
title: IMS-ondersteuning voor Adobe Experience Manager as a Cloud Service
description: Ondersteuning voor Image Management System voor Adobe Experience Manager as a Cloud Service.
exl-id: fb563dbd-a761-4d83-9da1-58f8e462b383
source-git-commit: 678e81eb22cc1d7c239ac7a2594b39a3a60c51e2
workflow-type: tm+mt
source-wordcount: '1922'
ht-degree: 29%

---

# IMS-ondersteuning voor Adobe Experience Manager as a Cloud Service {#ims-support-for-aem-as-a-cloud-service}

## Inleiding {#introduction}

* AEM as a Cloud Service omvat ondersteuning voor Admin Console voor AEM-instanties en verificatie op basis van het Adobe Identity Management System (afgekort IMS).
* Met de Admin Console kunnen beheerders alle gebruikers van Experience Cloud centraal beheren.
* Gebruikers en groepen kunnen worden toegewezen aan productprofielen die zijn gekoppeld aan een AEM as a Cloud Service instantie, zodat zij zich kunnen aanmelden bij die instantie.

>[!TIP]
>
>Zie [Toegang tot AEM voor beheerders configureren](https://experienceleague.adobe.com/?recommended=ExperienceManager-A-1-2020.1.aem) voor een inleiding over hoe gebruikers het gebruik van Adobe IMS voor authentiek verklaren om as a Cloud Service te AEM. Leer ook hoe Adobe IMS-gebruikers, -gebruikersgroepen en -productprofielen worden gebruikt om de toegang tot AEM en de functies en functies ervan te beheren. Adobe ID vereist.

## Belangrijkste hooglichten {#key-highlights}

AEM as a Cloud Service biedt alleen ondersteuning voor IMS-verificatie voor auteur-, Admin- en Dev-gebruikers. Het programma biedt geen ondersteuning voor externe eindgebruikers van klantsites, zoals sitebezoekers.

* De Admin Console vertegenwoordigt klanten als organisaties IMS, Auteur, en Publish Instanties in een milieu als Instanties van de Context van het Product. Deze vertegenwoordiging staat systeem en de beheerders van het Product toe om toegang tot instanties te beheren.
* Productprofielen in de Admin Console bepalen tot welke instanties een gebruiker toegang heeft.
* Klanten kunnen hun eigen SAML 2-compatibele identiteitsproviders (IDP for short) gebruiken voor Single Sign On.
* Alleen Enterprise- of federatieve id&#39;s voor Single Sign On van klant worden ondersteund, geen persoonlijke Adobe-id&#39;s.

## Architectuur {#architecture}

IMS-verificatie werkt met het OAuth-protocol tussen AEM en het Adobe IMS-eindpunt. Zodra een gebruiker aan IMS is toegevoegd en een Adobe ID heeft, kan deze zich aanmelden bij de AEM-auteursservice met IMS-referenties.

De gebruikersopenings van een sessiestroom wordt hieronder weergegeven, de gebruiker wordt omgeleid naar IMS en optioneel naar de klant-IDP voor SSO en vervolgens teruggeleid naar AEM.

![IMS-architectuur](/help/security/assets/ims1.png)

## Instellen {#how-to-set-up}

### Organisaties aan boord nemen naar Adobe Admin Console {#onboarding-orgs-to-adobe-admin-console}

Als u Adobe IMS voor AEM-verificatie wilt gebruiken, is het on-boarden van de klant een eerste vereiste voor het gebruik van de Adobe IMS voor AEM-verificatie.

Als eerste stap moeten klanten beschikken over een organisatie die is ingericht in Adobe IMS. Adobe Enterprise-klanten worden in het [Adobe Admin Console](https://helpx.adobe.com/nl/enterprise/using/admin-console.html). Dit gebied is het portaal dat klanten van de Adobe gebruiken om hun productrechten voor hun gebruikers en groepen te beheren.

AEM klanten zouden reeds een Organisatie moeten hebben die wordt voorzien, en als deel van de levering IMS, worden de klanteninstanties ter beschikking gesteld in Admin Console voor het beheren van gebruikersrechten en toegang.

Nadat een klant als IMS Organisatie bestaat, moeten zij hun systeem vormen zoals samengevat in het volgende:

![IMS on-boarden](/help/security/assets/ims2.png)

1. De aangewezen systeembeheerder ontvangt een uitnodiging om u aan te melden bij Cloud Manager. Nadat u zich hebt aangemeld bij Cloud Manager, kunnen de systeembeheerders ervoor kiezen AEM programma&#39;s en omgevingen te bieden of naar de Admin Console te navigeren voor beheertaken.
1. De systeembeheerder beweert een domein om de eigendom van het respectieve domein (bijvoorbeeld, acme.com) te bevestigen
1. De systeembeheerder stelt gebruikersdirectory&#39;s in
1. De systeembeheerder voert IDP-configuratie in Admin Console uit om Single Sign-On in te stellen.
1. De AEM-beheerder beheert de lokale groepen en toestemmingen en machtigingen, zoals gebruikelijk.

De basisbeginselen van Adobe Identity Management, inclusief de IDP-configuratie, worden [hier](https://helpx.adobe.com/nl/enterprise/using/set-up-identity.html) besproken.

Het gebruik van Enterprise Administration en Admin Console wordt gedekt [hier](https://helpx.adobe.com/enterprise/admin-guide.html).

### Gebruikers aan boord in Admin Console {#onboarding-users-in-admin-console}

Er zijn drie manieren om aan boord van gebruikers te gaan. Elke methode is afhankelijk van de grootte van de klant en zijn voorkeur. U kunt gebruikers manueel tot stand brengen in Admin Console, een .csv dossier uploaden, of gebruikers van de onderneming Actieve Folder van de klant synchroniseren.

**Handmatige toevoeging via de gebruikersinterface van de Admin Console**

Gebruikers en groepen kunnen handmatig worden gemaakt in de gebruikersinterface van de Admin Console. Deze methode kan worden gebruikt als u niet veel gebruikers te beheren hebt. Stel bijvoorbeeld dat er minder dan 50 AEM gebruikers zijn of dat u deze methode al gebruikt voor het beheer van andere Adobe producten, zoals Analytics, Target of Creative Cloud.

![Gebruiker on-boarden](/help/security/assets/ims3.png)

**Bestand uploaden in de gebruikersinterface van Admin Console**

Als u op een eenvoudige manier gebruikers wilt maken, kunt u een `.csv`-bestand uploaden om een aantal gebruikers tegelijk toe te voegen.

![Bestand uploaden](/help/security/assets/ims4.png)

**User Sync Tool**

Het Hulpmiddel van de Synchronisatie van de gebruiker (MOET in het kort) laat de ondernemingsklanten van de Adobe toe om de gebruikers van de Adobe tot stand te brengen en te beheren gebruikend Actieve Folder. Dit MOET ook voor andere geteste OpenLDAP-directoryservices werken. De doelgebruikers zijn de Beheerders van de Identiteit van IT (de Folder van de Onderneming of de Beheerders van het Systeem) die het hulpmiddel kunnen installeren en vormen. Het opensource-programma kan worden aangepast, zodat klanten het kunnen aanpassen aan hun eigen specifieke vereisten.

Wanneer de looppas van de Synchronisatie van de Gebruiker, het een lijst van gebruikers van de Actieve Folder van de organisatie haalt en het met de lijst van gebruikers binnen de Admin Console vergelijkt. Het roept dan de Adobe API van het Gebruikersbeheer zodat de Admin Console met de folder van de organisatie wordt gesynchroniseerd. De wijzigingsflow is uitsluitend eenrichtingsverkeer. Wijzigingen die u aanbrengt in de Admin Console, worden niet doorgestuurd naar de directory.

Met dit hulpprogramma kan de systeembeheerder gebruikersgroepen in de directory van de klant toewijzen aan productconfiguratie en gebruikersgroepen in de Admin Console.

Om Gebruikerssynchronisatie in te stellen, moet de organisatie een set referenties maken op dezelfde manier als de [Gebruikersbeheer-API](https://developer.adobe.com/umapi/).

![User Sync Tool](/help/security/assets/ims5.png)

Het Hulpmiddel van de Synchronisatie van de gebruiker wordt verdeeld door de bewaarplaats van GitHub van de Adobe [op deze locatie](https://github.com/adobe-apiplatform/user-sync.py/releases/tag/v2.9.0rc2).

>[!NOTE]
>
>Er is een pre-releaseversie **2.4RC1** beschikbaar met ondersteuning voor het maken van dynamische groepen, die u [hier](https://github.com/adobe-apiplatform/user-sync.py/releases/tag/v2.4rc1) vindt.

De belangrijkste functies voor deze release zijn de mogelijkheid om nieuwe LDAP-groepen dynamisch toe te wijzen voor gebruikerslidmaatschap in de Admin Console en om een dynamische gebruikersgroep te maken.

Meer informatie over de nieuwe groepsfuncties vindt u [op deze locatie](https://adobe-apiplatform.github.io/user-sync.py/en/user-manual/advanced_configuration.html#additional-group-options).

**User Sync-documentatie**

Zie [MOET documentatie](https://adobe-apiplatform.github.io/user-sync.py/en/) voor meer informatie .

Het Hulpmiddel van de Synchronisatie van de Gebruiker moet als Adobe Developer cliënt UMAPI registreren gebruikend de procedure [hier](https://adobe-apiplatform.github.io/umapi-documentation/en/UM_Authentication.html).

Documentatie voor Adobe Developer Console vindt u [hier](https://developer.adobe.com/developer-console/).

De User Management-API die door de User Sync Tool wordt gebruikt, wordt [hier](https://adobe-apiplatform.github.io/user-sync.py/en/) besproken.

## Adobe Ervaring as a Cloud Service Configuratie {#aem-configuration}

>[!NOTE]
>
>De vereiste AEM IMS-configuratie wordt automatisch geconfigureerd wanneer de AEM omgevingen en instanties worden ingericht. De beheerder kan dit echter naar wens wijzigen volgens de [hier](/help/implementing/deploying/overview.md) beschreven methode.

De vereiste AEM IMS-configuratie wordt automatisch geconfigureerd wanneer de AEM omgevingen en instanties worden ingericht. Klantbeheerders kunnen een deel van de configuratie naar wens van de klanten wijzigen

De algemene aanpak bestaat in het configureren van Adobe IMS als een OAuth-provider. De **Apache Jackrabbit Oak Default Sync Handler** kan worden gewijzigd, net als bij LDAP-synchronisatie.

Hieronder ziet u de belangrijkste OSGI-configuraties die moeten worden gewijzigd om eigenschappen zoals Gebruikersautomatisch lidmaatschap of Groepstoewijzingen te wijzigen.

<!-- Arun to provide list of osgi configs -->

## Hoe wordt het gebruikt {#how-to-use}

### Producten en gebruikerstoegang in Admin Console beheren {#managing-products-and-user-access-in-admin-console}

Wanneer de Beheerder van het Product aan Admin Console het programma opent, zien zij veelvoudige instanties van de AEM as a Cloud Service Context van het Product, zoals hieronder getoond. Selecteer bijvoorbeeld een van de producten in het menu **Overzicht** pagina:

![Instantieaanmelding](/help/security/assets/ims6.png)

Er wordt een lijst met bestaande instanties weergegeven:

![Instantieaanmelding2](/help/security/assets/ims7.png)

Onder elke instantie van de Context van het Product, zijn er instanties die de diensten van de Auteur of van de Publicatie over Productie, Stadium, of milieu&#39;s van de Ontwikkeling overspannen. Elke instantie is gekoppeld aan de rollen Productprofielen of Cloud Manager. Deze productprofielen worden gebruikt om toegang toe te wijzen aan Gebruikers en Groepen met de vereiste voorrechten.

De **AEM Beheerders_xxx** profiel wordt gebruikt om beheerderrechten toe te kennen in de bijbehorende AEM **AEM Users_xxx** wordt gebruikt om gewone gebruikers toe te voegen.

Gebruikers en groepen die zijn toegevoegd onder dit productprofiel, kunnen zich aanmelden bij die instantie, zoals in het onderstaande voorbeeld wordt getoond:

![Productprofiel](/help/security/assets/ims8.png)

>[!WARNING]
>
>Wijzig de instelling **AEM** productprofielnaam. De naam van de **AEM** met het productprofiel worden de beheerdersrechten verwijderd van alle gebruikers die aan dat profiel zijn toegewezen.

### Aanmelden bij Adobe Experience Manager as a Cloud Service {#logging-in-to-aem}

**Aanmelden bij lokale beheerder**

AEM kan lokale aanmeldingen voor Admin-gebruikers blijven ondersteunen. Via het aanmeldingsscherm kunt u zich lokaal aanmelden:

![Lokale aanmelding](/help/security/assets/ims9.png)

<!-- the above image must be updated for skyline -->

**IMS-gebaseerde aanmelding**

Voor andere gebruikers, wordt de op IMS-Gebaseerde opening van een sessie gebruikt nadat IMS op de instantie wordt gevormd. De gebruiker klikt op de knop Aanmelden met Adobe, zoals hieronder wordt weergegeven:

![IMS-aanmelding](/help/security/assets/ims10.png)


>[!NOTE]
>
>Elke gebruiker die in IMS is gemaakt, kan met een Adobe ID of Federated ID worden gemaakt. Als een gebruiker opstelling gebruikend Federated ID is, worden zij voor authentiek verklaard gebruikend hun Leverancier van de Identiteit van het Bedrijf aan login.

Zij worden opnieuw gericht aan het IMS openings van een sessiescherm en moeten hun geloofsbrieven ingaan:

![IMS-aanmelding2](/help/security/assets/ims11.png)

![IMS-aanmelding3](/help/security/assets/ims12.png)

Als een gefedereerde IDP tijdens aanvankelijke opstelling van de Admin Console wordt gevormd, dan wordt de gebruiker opnieuw gericht aan klant IDP voor SSO:

![IMS-aanmelding4](/help/security/assets/ims13.png)

Nadat de authentificatie volledig is, wordt de gebruiker opnieuw gericht naar AEM en het programma geopend:

![IMS-aanmelding5](/help/security/assets/ims14.png)

### Bevoegdheden en ACL&#39;s beheren in Adobe Experience Manager as a Cloud Service {#managing-permissions-in-aem}

ACLs en de toestemmingen blijven in AEM worden beheerd. De gebruikersgroepen die vanaf IMS worden gesynchroniseerd, kunnen worden toegewezen aan lokale groepen waar ACL&#39;s en rechten zijn gedefinieerd.

In het onderstaande voorbeeld worden gesynchroniseerde groepen toegevoegd aan de lokale **Dam_Users** groeperen als voorbeeld.

De gebruiker maakt deel uit van de volgende groepen in IMS:

![ACL1](/help/security/assets/ims15.png)

Wanneer de gebruiker zich aanmeldt, worden diens groepslidmaatschappen gesynchroniseerd zoals hieronder weergegeven:

![ACL2](/help/security/assets/ims16.png)

In AEM kunnen de gebruikersgroepen die via IMS zijn gesynchroniseerd, als leden worden toegevoegd aan bestaande lokale groepen zoals **DAM-gebruikers**.

![ACL3](/help/security/assets/ims17.png)

Zoals hieronder getoond, de groep **AEM-GRP_008** erft de machtigingen en rechten van **DAM-gebruikers**. Deze overerving is een effectieve manier om machtigingen voor gesynchroniseerde groepen te beheren en wordt veel gebruikt in de op LDAP gebaseerde verificatiemethode.

![ACL3](/help/security/assets/ims18.png)


### Cloud Manager openen {#accessing-cloud-manager}

Als u toegang wilt tot Cloud Manager of tot omgevingen AEM as a Cloud Service, moet u zijn toegewezen aan profielen van het product Cloud Manager.

Zie Roldefinities als u meer wilt weten over rollen voor gebruikers die de beschikbaarheid van specifieke functies in Cloud Manager bepalen.

>[!NOTE]
>Cloud Manager heeft vooraf geconfigureerde rollen met de juiste machtigingen. Om over elk van de rollen met specifieke toestemmingen, pre-gevormde taken, of toestemmingen, verbonden aan elke rol te leren, zie [Op rollen gebaseerde machtigingen](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-manager/content/requirements/role-based-permissions).

**Stappen voor het toevoegen van een gebruiker**

1. Voeg een gebruiker toe aan een bepaald profiel vanaf het scherm van een bestaande gebruiker of vanaf het scherm van een nieuwe gebruiker.

1. U kunt ook een gebruiker toevoegen vanaf het scherm **Overview**, zoals in de onderstaande afbeelding wordt getoond.

   ![ACL3](/help/security/assets/ims23.png)

   >[!NOTE]
   >U kunt meerdere profielen aan een gebruiker toewijzen, zoals in de onderstaande afbeelding wordt getoond.

   ![ACL3](/help/security/assets/ims22.png)


1. Nadat u het juiste profiel hebt toegevoegd, kunt u de respectievelijke huurders in Cloud Manager openen via [Adobe Experience Cloud](https://my.cloudmanager.adobe.com) in de rechterbovenhoek van de gebruikersinterface.


### Een instantie openen in AEM as a Cloud Service {#accessing-instance-cloud-service}

>[!IMPORTANT]
>De stappen die in het voorgaande gedeelte worden vermeld, moeten al zijn uitgevoerd voordat u toegang krijgt tot een instantie in AEM as a Cloud Service.

Toegang krijgen tot een AEM instantie binnen de **Admin Console**, dient u het programma Cloud Manager en de omgevingen in het programma te bekijken in de productlijst van de **Admin Console**.

In de onderstaande screenshot ziet u bijvoorbeeld twee beschikbare omgevingen, namelijk *dev auteur* en *publish*.

![ACL3](/help/security/assets/ims19.png)

Om toegang tot AEM instanties te krijgen, moet de gebruiker aan een groep van het aangewezen Product van de Cloud Service worden toegevoegd.

Elke auteurinstantie heeft een AEM Beheerders en AEM Gebruikersprofiel en elke publicatie-instantie heeft een AEM Gebruikersprofiel. U kunt desgewenst andere profielen toevoegen.

Als u toegang tot het beheerniveau van de AEM-instantie wilt krijgen, voegt u de gebruiker toe aan het AEM-beheerdersprofiel voor dat specifieke product.
