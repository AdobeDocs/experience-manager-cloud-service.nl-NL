---
title: Toegang tot de Admin Console
description: Zodra u de voorbereidingen begrijpt die nodig zijn om aan boord te gaan en de basisbeginselen van de AEM as a Cloud Service-structuur, bent u klaar om u voor het eerst aan te melden bij de Admin Console.
exl-id: 0ccce328-a356-4ba9-b7fe-f67abc25b924
feature: Onboarding
role: Admin, User, Developer
source-git-commit: 8ed13eb6f476bab07da07549a83ab9ac16bdea72
workflow-type: tm+mt
source-wordcount: '1147'
ht-degree: 0%

---

# Toegang tot de Admin Console {#accessing-admin-console}

In dit deel van de [&#x200B; onboarding reis &#x200B;](overview.md), leert u over de voorbereiding noodzakelijk alvorens u in het systeem voor het eerst kunt registreren.

## Doelstelling {#objective}

Nu u de artikel [&#x200B; Terminologie van AEM as a Cloud Service &#x200B;](terminology.md) hebt gelezen en de grondbeginselen van structuur begrijpt AEMaaCS, bent u bereid om in Admin Console voor het eerst te registreren!

Als systeembeheerder bent u verantwoordelijk voor het beheer van gebruikers binnen uw organisatie die de Admin Console gebruiken. Na het lezen van deze sectie moet u het volgende kunnen doen:

* Begrijp wat een Adobe ID is.
* Aanmelden bij de Admin Console.
* Begrijp hoe te om uw voorrechten als systeembeheerder door middel van Admin Console te herzien.
* Vraag hoe u contact kunt opnemen met Adobe-ondersteuning voor hulp.

## Over de Admin Console {#admin-console}

De Adobe Admin Console is een centrale plaats voor het beheer en beheer van uw Adobe-productlicenties en -gebruikers. Met de Admin Console kunt u gebruikers op één locatie maken en beheren in plaats van binnen uw verschillende individuele oplossingen.

### Adobe ID {#adobe-id}

Als u zich wilt aanmelden bij de Admin Console, hebt u een Adobe ID nodig. Een Adobe ID is een account die is gekoppeld aan een specifiek e-mailadres dat vereist is om u aan te melden bij en toegang te krijgen tot AEM as a Cloud Service of een van uw Adobe-oplossingen. Als je Adobe ID gebruikt, houd je al je Adobe-plannen en -producten bij die aan één account zijn gekoppeld.

Wanneer u als systeembeheerder uw team instelt in de Admin Console, geeft u het e-mailadres op dat als de Adobe ID wordt gebruikt.

Er zijn drie typen Adobe-id&#39;s:

* **Persoonlijke identiteitskaart**: Het standaardtype van Adobe ID en in adobe.com gecreeerd. Beheerd door Adobe en iedereen kan een dergelijk account maken.

* **Enterprise ID**: De organisaties willen gewoonlijk controle van de rekeningen van de gebruikers verhogen. Alleen systeembeheerders kunnen id&#39;s voor bedrijven maken en de organisatie heeft deze accounts in handen van Adobe die alleen als host fungeert.

* **Federated ID**: Met gefedereerde IDs, neemt de organisatie volledige eigendom en controle van de rekeningen. Uw organisatie moet de Adobe Experience Cloud integreren met uw SSO2-systeem (Single Sign-On). Als u dit doet, kunnen gebruikers zich verifiëren op basis van het SSO-systeem van hun organisatie in plaats van op basis van een account die door Adobe wordt gehost.

Als systeembeheerder kunt u zich en uw team aan boord van AEM as a Cloud Service met persoonlijke id&#39;s. Voer deze taak uit voordat de bedrijfs- of gefedereerde id&#39;s zijn geïnstalleerd. Zodra de onderneming of gefedereerde IDs opstelling zijn, kunnen de leden aan het gebruiken van die IDs worden overgegaan.

### Aanmelden bij Admin Console {#steps-admin-console}

Voordat u de Admin Console kunt gebruiken om gebruikers binnen uw team te beheren, moet u ervoor zorgen dat u zelf toegang hebt tot de toepassing en over de juiste machtigingen beschikt.

1. Als systeembeheerder ontvangt u meerdere e-mails van Adobe als onderdeel van het instapproces. Zoek de welkomstmail die de informatie over de organisatienaam verstrekt waaraan u toegang hebt verleend.

1. Klik **krijgen begonnen** verbinding in uw welkome e-mail om aan Admin Console te navigeren. Als u e-mail niet kunt vinden, open direct browser aan Admin Console op [`https://adminconsole.adobe.com` &#x200B;](https://adminconsole.adobe.com).

   ![&#x200B; Welkome e-mail &#x200B;](/help/journey-onboarding/assets/get-started-email.png)

1. Meld u aan met uw Adobe ID. Op succesvolle login, ziet u de **pagina van het Overzicht** van Adobe Admin Console.

   ![&#x200B; Admin Console &#x200B;](/help/journey-onboarding/assets/get-started1.png)

1. Als u toegang tot veelvoudige organisaties hebt, zorg ervoor dat u zich bij de correcte organisatie hebt aangemeld. Als u uw organisatie wilt wijzigen, klikt u in de rechterbovenhoek op de naam van de organisatie en kiest u de gewenste organisatie waartoe u toegang nodig hebt.

   ![&#x200B; de org van de Verandering &#x200B;](/help/journey-onboarding/assets/admin-console-orgswitch.png)

1. Selecteer **Beheerders** van de **Gebruikers** kaart om te verifiëren dat u een systeembeheerder bent.

   ![&#x200B; de beheerders van het Overzicht &#x200B;](/help/journey-onboarding/assets/get-started2.png)

1. Nadat u **Beheerders** van de **Gebruikers** kaart klikt, kunt u zoeken door uw e-mail van Adobe ID, gebruikersbenaming, eerst, of achternaam in te gaan.

   ![&#x200B; de gebruikers van het Onderzoek &#x200B;](/help/journey-onboarding/assets/get-started3.png)

1. Als alles goed werkt, retourneert de zoekopdracht uw record. Als de waarde in de **ADMIN ROLE** kolom **Systeem** toont, weet u dat u (of de getoonde gebruiker) een systeembeheerder zijn.

   ![&#x200B; status van het Systeem &#x200B;](/help/journey-onboarding/assets/get-started4.png)

Gefeliciteerd, systeembeheerder!

## Toegang tot de Admin Console via Experience Hub  {#access-admin-console-via-experience-hub}

[&#x200B; Experience Hub &#x200B;](/help/experience-hub.md) is het verenigde, gepersonaliseerde huis voor AEM. Het brengt AEM Tools en de Admin Console samen op één plaats.

![&#x200B; optie van Admin Console aangezien het op de homepage van Experience Hub &#x200B;](/help/journey-onboarding/assets/experiencehub-adminconsole1.png) verschijnt

**om tot Admin Console door Experience Hub toegang te hebben:**

1. Klik [&#x200B; Adobe Experience Cloud &#x200B;](https://experience.adobe.com/#/@foundationinternal/home) om Experience Hub homepage te openen.

1. In de **Snelle toegang** groepering, klik [**Admin Console** &#x200B;](https://experience.adobe.com).

## Adobe Identity Management System {#ims}

AEM as a Cloud Service wordt vooraf geconfigureerd met Adobe Identity Management System (ook wel IMS genoemd) voor verificatie. Er is niets dat u als systeembeheerder moet doen om deze functionaliteit toe te laten.

Door IMS te gebruiken, consolideert AEM as a Cloud Service de login ervaring tussen AEM en de rest van Adobe Experience Cloud. Organisaties met veel Adobe-producten winnen het meest. Op rollen gebaseerde groepen maken in de Admin Console en producttoegang verlenen via IMS, zoals AEM as a Cloud Service.

Meer informatie over productprofielen en het toewijzen van gebruikers in het volgende gedeelte van deze instapreis.

## Contact opnemen met Adobe-ondersteuning {#support}

Als u problemen hebt, kunt u Adobe-ondersteuning openen via de Admin Console. Het **lusje van de Steun** laat u tot diverse de steunfuncties van Adobe door een eenvoudig en makkelijk te gebruiken interface toegang hebben.

![&#x200B; het lusje van de Steun &#x200B;](/help/journey-onboarding/assets/support-menu.png)

Op het tabblad kunt u zaken maken en beheren, rechtstreeks chatten met Adobe-vertegenwoordigers voor klantenondersteuning en sessies plannen met experts. Systeembeheerders en supportbeheerders moeten zich aanmelden voor toegang tot ondersteuningsgevallen en sessieopties van experts.

## Wat nu? {#whats-next}

Nu u dit document hebt gelezen, moet u:

* Begrijp wat en Adobe ID is.
* Aanmelden bij de Admin Console.
* Leer hoe u uw rechten als systeembeheerder kunt controleren met de Admin Console.
* Vraag hoe u contact kunt opnemen met Adobe-ondersteuning voor hulp.

U bent bereid om uw onboarding reis door te leren hoe te [&#x200B; teamleden aan de Profielen van het Product van Cloud Manager &#x200B;](assign-profiles-cloud-manager.md) toewijzen zodat uw collega&#39;s tot AEMaaCS kunnen ook toegang hebben.

## Aanvullende bronnen {#additional-resources}

Hieronder volgen aanvullende, optionele bronnen als u verder wilt gaan dan de inhoud van de instapreis.

* [&#x200B; Overzicht van Admin Console &#x200B;](https://helpx.adobe.com/nl/enterprise/using/admin-console.html) - een uitvoerig overzicht van Admin Console
* [&#x200B; creeer of werk Uw Adobe ID &#x200B;](https://helpx.adobe.com/ca/manage-account/using/create-update-adobe-id.html#HowtocreateorupdateyourAdobeID) bij - leer hoe te om een Adobe ID tot stand te brengen, het te veranderen, en veelvoudige Adobe IDs te beheren.
* [&#x200B; SAML 2.0 de Handler van de Authentificatie &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-65/content/security/saml-2-0-authenticationhandler#) - de schepen van AEM met een de authentificatiemanager van SAML. Deze manager verleent steun voor SAML 2.0 het Protocol van het Verzoek van de Authentificatie (Web-SSO profiel) gebruikend de POST van HTTP band.
* [&#x200B; Administratieve Rollen &#x200B;](https://helpx.adobe.com/nl/enterprise/using/admin-roles.html) - Gebruikend de Adobe Admin Console, kunnen de organisaties een flexibele administratieve hiërarchie bepalen die fijnkorrelig beheer van de het producttoegang en het gebruik van Adobe toelaat.
* [&#x200B; de Sessies van de Steun en van de Expert &#x200B;](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.html) - leer hoe te om tot de steunopties op Admin Console toegang te hebben, uw steungevallen te beheren, een deskundige zitting te plannen, en meer.
