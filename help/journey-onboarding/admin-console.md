---
title: De Admin Console openen
description: Zodra u de voorbereiding noodzakelijk aan het aan boord gaan en de grondbeginselen van structuur AEMaaCS begrijpt, bent u bereid om in de Admin Console voor het eerst te registreren.
exl-id: 0ccce328-a356-4ba9-b7fe-f67abc25b924
feature: Onboarding
role: Admin, User, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '1071'
ht-degree: 0%

---

# De Admin Console openen {#accessing-admin-console}

In dit deel van de [ onboarding reis, ](overview.md) leert u over de voorbereiding noodzakelijk alvorens u in het systeem voor het eerst kunt registreren.

## Doelstelling {#objective}

Nu u de artikel [ Terminologie van AEM as a Cloud Service ](terminology.md) hebt gelezen en de grondbeginselen van structuur begrijpt AEMaaCS, bent u bereid om in de Admin Console voor het eerst te registreren!

Als systeembeheerder bent u verantwoordelijk voor het beheer van gebruikers binnen uw organisatie. Dit doet u met de Admin Console. Na het lezen van deze sectie moet u:

* Begrijp wat een Adobe ID is.
* Aanmelden bij Admin Console.
* Begrijp hoe te om uw voorrechten als systeembeheerder via Admin Console te herzien.
* Zorg dat u weet hoe u contact kunt opnemen met de ondersteuning van Adoben voor hulp.

## De Admin Console {#admin-console}

De Adobe Admin Console is een centrale plaats voor het beheer en beheer van uw Adobe productlicenties en gebruikers. Met de Admin Console kunt u gebruikers op één locatie maken en beheren in plaats van binnen de verschillende afzonderlijke oplossingen.

## Adobe ID {#adobe-id}

Als u zich wilt aanmelden bij de Admin Console, hebt u een Adobe ID nodig. En Adobe ID is een account die is gekoppeld aan een specifiek e-mailadres dat vereist is voor aanmelding en toegang tot AEM as a Cloud Service of een van uw Adobe-oplossingen. Door je Adobe ID te gebruiken, bewaar je al je Adobe plannen en producten die aan één account zijn gekoppeld.

Wanneer u als systeembeheerder uw team instelt in de Admin Console, geeft u het e-mailadres op dat als Adobe ID wordt gebruikt.

Er zijn drie typen Adobe-id&#39;s:

* **Persoonlijke identiteitskaart**: Dit is het standaardtype van Adobe ID en in adobe.com gecreeerd. Dit account wordt beheerd door Adobe en iedereen kan een dergelijk account maken.

* **Enterprise ID**: De organisaties willen gewoonlijk controle van de gebruikersrekeningen verhogen. Alleen systeembeheerders kunnen id&#39;s voor ondernemingen maken en de organisatie heeft deze accounts in eigendom met Adobe die alleen als host fungeert.

* **Federated ID**: Met gefedereerde IDs neemt de organisatie volledige eigendom en controle van de rekeningen. Hiervoor moet uw organisatie de Adobe Experience Cloud integreren met uw SSO2-systeem (Single Sign-On). Dit staat gebruikers toe om tegen het systeem van SSO van hun organisatie eerder dan een rekening voor authentiek te verklaren die door Adobe wordt ontvangen.

Als systeembeheerder kunt u zelf en uw team aan boord van AEM as a Cloud Service laten gaan met behulp van persoonlijke id&#39;s voordat u de Enterprise- of federatieve id&#39;s hebt ingesteld. Zodra de onderneming of gefedereerde IDs opstelling zijn, kunnen de leden aan het gebruiken van die IDs worden overgegaan.

## Aanmelden bij Admin Console {#steps-admin-console}

Alvorens u de Admin Console kunt gebruiken om gebruikers binnen uw team te beheren, moet u ervoor zorgen dat u tot het kunt behoorlijk toegang hebben en de aangewezen toestemmingen hebben.

1. Als systeembeheerder ontvangt u meerdere e-mails van de Adobe als onderdeel van het instapproces. Zoek de welkomstmail die de informatie over de organisatienaam verstrekt waaraan u toegang hebt verleend.

1. Klik **krijgen begonnen** verbinding in uw welkome e-mail om aan Admin Console te navigeren. Als u e-mail niet kunt vinden, open browser rechtstreeks aan Admin Console bij [`https://adminconsole.adobe.com` ](https://adminconsole.adobe.com).

   ![ Welkome e-mail ](/help/journey-onboarding/assets/get-started-email.png)

1. Meld u aan met uw Adobe ID. Op succesvolle login, ziet u de **pagina van het Overzicht** van Adobe Admin Console.

   ![ de Admin Console ](/help/journey-onboarding/assets/get-started1.png)

1. Als u toegang tot veelvoudige organisaties hebt, zorg ervoor dat u in correcte organisatie hebt geregistreerd. Als u uw organisatie wilt wijzigen, klikt u in de rechterbovenhoek op de naam van de organisatie en kiest u de gewenste organisatie waartoe u toegang nodig hebt.

   ![ de org van de Verandering ](/help/journey-onboarding/assets/admin-console-orgswitch.png)

1. Selecteer **Beheerders** van de **Gebruikers** kaart om te verifiëren dat u een systeembeheerder bent.

   ![ de beheerders van het Overzicht ](/help/journey-onboarding/assets/get-started2.png)

1. Nadat u **Beheerders** van de **Gebruikers** kaart klikt, kunt u zoeken door uw e-mail van Adobe ID, gebruikersbenaming, eerst, of achternaam in te gaan.

   ![ de gebruikers van het Onderzoek ](/help/journey-onboarding/assets/get-started3.png)

1. Als alles naar behoren werkt, retourneert de zoekopdracht uw record. Als de waarde in de **ADMIN ROLE** kolom **Systeem** toont, weet u dat u (of de getoonde gebruiker) een systeembeheerder zijn.

   ![ status van het Systeem ](/help/journey-onboarding/assets/get-started4.png)

Gefeliciteerd, systeembeheerder!

## Adobe Identity Management-systeem {#ims}

AEM as a Cloud Service wordt vooraf geconfigureerd met het Adobe Identity Management System (ook wel IMS genoemd) voor verificatie. Er is niets u als systeembeheerder moet doen om dit toe te laten.

Door IMS te gebruiken, consolideert AEM as a Cloud Service de login ervaring tussen AEM en de rest van Adobe Experience Cloud. Organisaties met meerdere producten van de Adobe hebben vooral baat bij het maken van op rollen gebaseerde groepen in de Admin Console en het toewijzen van toegang tot meerdere producten, waaronder AEM as a Cloud Service via IMS.

Meer informatie over productprofielen en het toewijzen van gebruikers in het volgende gedeelte van deze instapreis.

## Contact opnemen met Adobe-ondersteuning {#support}

Als u problemen hebt, kunt u de ondersteuning voor Adoben openen via de Admin Console. Het **lusje van de Steun** laat u tot diverse functies van de Adobe steun door een eenvoudig en makkelijk te gebruiken interface toegang hebben.

![ het lusje van de Steun ](/help/journey-onboarding/assets/support-menu.png)

Op het tabblad kunt u zaken maken en beheren, rechtstreeks chatten met Adobe-vertegenwoordigers van klantenondersteuning en sessies plannen met experts. Systeembeheerders en supportbeheerders moeten zich aanmelden voor toegang tot ondersteuningsgevallen en sessieopties van experts.

## Volgende functies {#whats-next}

Nu u dit document hebt gelezen, moet u:

* Begrijp wat en Adobe ID is.
* Aanmelden bij Admin Console.
* Begrijp hoe te om uw voorrechten als systeembeheerder via Admin Console te herzien.
* Zorg dat u weet hoe u contact kunt opnemen met de ondersteuning van Adoben voor hulp.

U bent bereid om uw onboarding reis door te leren hoe te [ teamleden aan de Profielen van het Product van Cloud Manager ](assign-profiles-cloud-manager.md) toewijzen zodat u collega&#39;s tot AEMaaCS kunnen ook toegang hebben.

## Aanvullende bronnen {#additional-resources}

Hieronder volgen aanvullende, optionele bronnen als u verder wilt gaan dan de inhoud van de instapreis.

* [ Overzicht van de Admin Console ](https://helpx.adobe.com/nl/enterprise/using/admin-console.html) - een uitvoerig overzicht van de Admin Console
* [ creeer of werk Uw Adobe ID ](https://helpx.adobe.com/ca/manage-account/using/create-update-adobe-id.html#HowtocreateorupdateyourAdobeID) bij - leer hoe te om een Adobe ID tot stand te brengen, het te veranderen, en veelvoudige Adobe IDs te beheren.
* [ SAML 2.0 de Handler van de Authentificatie ](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/saml-2-0-authenticationhandler.html) - AEM schepen met een de authentificatiemanager van SAML. Deze manager verleent steun voor SAML 2.0 het Protocol van het Verzoek van de Authentificatie (Web-SSO profiel) gebruikend de POST van HTTP band.
* [ Administratieve Rollen ](https://helpx.adobe.com/enterprise/using/admin-roles.ug.html) - Gebruikend Adobe Admin Console, kunnen de organisaties een flexibele administratieve hiërarchie bepalen die fijnkorrelig beheer van de toegang en het gebruik van het het productproduct van de Adobe toelaat.
* [ de Sessies van de Steun en van de Expert ](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) - leer hoe te om tot de steunopties op de Admin Console toegang te hebben, uw steungevallen te beheren, een Deskundige Zitting, en meer te plannen.
