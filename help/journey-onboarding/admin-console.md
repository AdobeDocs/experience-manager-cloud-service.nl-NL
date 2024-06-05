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

In dit deel van het [aan boord gaan,](overview.md) u leert over de voorbereiding noodzakelijk alvorens u in het systeem voor het eerst kunt registreren.

## Doelstelling {#objective}

Nu hebt u het artikel gelezen [as a Cloud Service terminologie AEM](terminology.md) en begrijp de basisbeginselen van de AEMaaCS-structuur. U kunt zich voor het eerst aanmelden bij de Admin Console!

Als systeembeheerder bent u verantwoordelijk voor het beheer van gebruikers binnen uw organisatie. Dit doet u met de Admin Console. Na het lezen van deze sectie moet u:

* Begrijp wat een Adobe ID is.
* Aanmelden bij Admin Console.
* Begrijp hoe te om uw voorrechten als systeembeheerder via Admin Console te herzien.
* Zorg dat u weet hoe u contact kunt opnemen met de ondersteuning van Adoben voor hulp.

## De Admin Console {#admin-console}

De Adobe Admin Console is een centrale plaats voor het beheer en beheer van uw Adobe productlicenties en gebruikers. Met de Admin Console kunt u gebruikers op één locatie maken en beheren in plaats van binnen de verschillende afzonderlijke oplossingen.

## Adobe ID {#adobe-id}

Als u zich wilt aanmelden bij de Admin Console, hebt u een Adobe ID nodig. En Adobe ID is een account die is gekoppeld aan een specifiek e-mailadres dat vereist is voor aanmelding en toegang AEM as a Cloud Service of een van uw Adobe-oplossingen. Door je Adobe ID te gebruiken, bewaar je al je Adobe plannen en producten die aan één account zijn gekoppeld.

Wanneer u als systeembeheerder uw team instelt in de Admin Console, geeft u het e-mailadres op dat als Adobe ID wordt gebruikt.

Er zijn drie typen Adobe-id&#39;s:

* **Persoonlijke id**: Dit is het standaardtype van Adobe ID en wordt gecreeerd in adobe.com. Dit account wordt beheerd door Adobe en iedereen kan een dergelijk account maken.

* **Enterprise ID**: Organisaties willen doorgaans de controle over de gebruikersaccounts vergroten. Alleen systeembeheerders kunnen id&#39;s voor ondernemingen maken en de organisatie heeft deze accounts in eigendom met Adobe die alleen als host fungeert.

* **Federated ID**: Met federatieve id&#39;s neemt de organisatie de volledige eigendom en controle over de rekeningen. Hiervoor moet uw organisatie de Adobe Experience Cloud integreren met uw SSO2-systeem (Single Sign-On). Dit staat gebruikers toe om tegen het systeem van SSO van hun organisatie eerder dan een rekening voor authentiek te verklaren die door Adobe wordt ontvangen.

Als systeembeheerder, kunt u aan boord van zich en uw team op AEM as a Cloud Service het gebruiken van persoonlijke IDs besluiten alvorens onderneming of gefedereerde IDs opstelling zijn. Zodra de onderneming of gefedereerde IDs opstelling zijn, kunnen de leden aan het gebruiken van die IDs worden overgegaan.

## Aanmelden bij Admin Console {#steps-admin-console}

Alvorens u de Admin Console kunt gebruiken om gebruikers binnen uw team te beheren, moet u ervoor zorgen dat u tot het kunt behoorlijk toegang hebben en de aangewezen toestemmingen hebben.

1. Als systeembeheerder ontvangt u meerdere e-mails van de Adobe als onderdeel van het instapproces. Zoek de welkomstmail die de informatie over de organisatienaam verstrekt waaraan u toegang hebt verleend.

1. Klik op de knop **Aan de slag** koppeling in uw welkomstbericht om naar de Admin Console te navigeren. Als u het e-mailbericht niet kunt vinden, opent u een browser rechtstreeks naar de Admin Console op [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com).

   ![Welkom-e-mail](/help/journey-onboarding/assets/get-started-email.png)

1. Meld u aan met uw Adobe ID. Bij een geslaagde aanmelding ziet u de **Overzicht** pagina van de Adobe Admin Console.

   ![De Admin Console](/help/journey-onboarding/assets/get-started1.png)

1. Als u toegang tot veelvoudige organisaties hebt, zorg ervoor dat u in correcte organisatie hebt geregistreerd. Als u uw organisatie wilt wijzigen, klikt u in de rechterbovenhoek op de naam van de organisatie en kiest u de gewenste organisatie waartoe u toegang nodig hebt.

   ![org wijzigen](/help/journey-onboarding/assets/admin-console-orgswitch.png)

1. Selecteren **Beheerders** van de **Gebruikers** kaart om te verifiëren dat u een systeembeheerder bent.

   ![Revisiebeheerders](/help/journey-onboarding/assets/get-started2.png)

1. Nadat u op **Beheerders** van de **Gebruikers** -kaart, kunt u zoeken door uw Adobe ID-e-mail, gebruikersnaam, voornaam of achternaam in te voeren.

   ![Gebruikers zoeken](/help/journey-onboarding/assets/get-started3.png)

1. Als alles naar behoren werkt, retourneert de zoekopdracht uw record. Als de waarde in de **ADMIN ROLE** kolomtonen **Systeem**, weet u dat u (of de getoonde gebruiker) een systeembeheerder zijn.

   ![Systeemstatus](/help/journey-onboarding/assets/get-started4.png)

Gefeliciteerd, systeembeheerder!

## Adobe Identity Management-systeem {#ims}

AEM as a Cloud Service wordt vooraf geconfigureerd met Adobe Identity Management System (ook wel IMS genoemd) voor verificatie. Er is niets u als systeembeheerder moet doen om dit toe te laten.

Door IMS te gebruiken, consolideert AEM as a Cloud Service de login ervaring tussen AEM en de rest van Adobe Experience Cloud. Organisaties met meerdere producten van de Adobe hebben vooral baat bij het maken van op rol gebaseerde groepen in de Admin Console en het toewijzen van toegang tot meerdere producten, waaronder AEM as a Cloud Service via IMS.

Meer informatie over productprofielen en het toewijzen van gebruikers in het volgende gedeelte van deze instapreis.

## Contact opnemen met Adobe-ondersteuning {#support}

Als u problemen hebt, kunt u de ondersteuning voor Adoben openen via de Admin Console. De **Ondersteuning** kunt u via een eenvoudige en gebruiksvriendelijke interface toegang krijgen tot verschillende functies voor ondersteuning van Adoben.

![Het tabblad Ondersteuning](/help/journey-onboarding/assets/support-menu.png)

Op het tabblad kunt u zaken maken en beheren, rechtstreeks chatten met Adobe-vertegenwoordigers van klantenondersteuning en sessies plannen met experts. Systeembeheerders en supportbeheerders moeten zich aanmelden voor toegang tot ondersteuningsgevallen en sessieopties van experts.

## Volgende functies {#whats-next}

Nu u dit document hebt gelezen, moet u:

* Begrijp wat en Adobe ID is.
* Aanmelden bij Admin Console.
* Begrijp hoe te om uw voorrechten als systeembeheerder via Admin Console te herzien.
* Zorg dat u weet hoe u contact kunt opnemen met de ondersteuning van Adoben voor hulp.

U bent klaar om uw instapreis voort te zetten door te leren hoe te [teamleden toewijzen aan productprofielen van Cloud Manager](assign-profiles-cloud-manager.md) zodat uw collega&#39;s ook toegang hebben tot AEMaaCS.

## Aanvullende bronnen {#additional-resources}

Hieronder volgen aanvullende, optionele bronnen als u verder wilt gaan dan de inhoud van de instapreis.

* [Overzicht van Admin Console](https://helpx.adobe.com/nl/enterprise/using/admin-console.html) - Een uitgebreid overzicht van de Admin Console
* [Adobe ID maken of bijwerken](https://helpx.adobe.com/ca/manage-account/using/create-update-adobe-id.html#HowtocreateorupdateyourAdobeID) - Leer hoe u een Adobe ID maakt, wijzigt en meerdere Adobe-id&#39;s beheert.
* [SAML 2.0-verificatiehandler](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/saml-2-0-authenticationhandler.html) - AEM schepen met een SAML authentificatiemanager. Deze manager verleent steun voor SAML 2.0 het Protocol van het Verzoek van de Authentificatie (Web-SSO profiel) gebruikend de POST van HTTP band.
* [Administratieve rollen](https://helpx.adobe.com/enterprise/using/admin-roles.ug.html) - Met behulp van de Adobe Admin Console kunnen organisaties een flexibele beheershiërarchie definiëren die een geavanceerd beheer van de toegang tot en het gebruik van producten in de Adobe mogelijk maakt.
* [Ondersteunings- en sessies met experts](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) - Leer hoe u toegang krijgt tot de ondersteuningsopties op de Admin Console, hoe u uw ondersteuningsgevallen beheert, hoe u een sessie met een expert instelt, enzovoort.
