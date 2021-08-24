---
title: Cloud Resources instellen via Cloud Manager
description: Volg deze pagina voor informatie over het instellen van Cloud Resources via Cloud Manager
hide: true
index: false
source-git-commit: 4a6408c498b093fc8b3baf4bdf1798b4281c90c2
workflow-type: tm+mt
source-wordcount: '1424'
ht-degree: 0%

---

# Cloud Resources instellen via Cloud Manager {#setup-cloud-resources}

De systeembeheerder die is toegewezen aan de rol Bedrijfseigenaar moet toegang hebben tot en zich aanmelden bij Cloud Manager. Hierna moet een teamlid dat is toegewezen aan het bedrijfseigenaarsprofiel zich aanmelden bij Cloud Manager en uw cloudprogramma en -omgevingen maken zodat uw team van experts aan de slag kan.

## Doelstelling {#objective}

Dit document helpt u te begrijpen hoe uw cloudbronnen zijn gemaakt en wie dit kan doen.

Na het lezen van deze sectie moet u begrijpen:

* Een systeembeheerder die is toegewezen aan de rol Bedrijfseigenaar moet de eerste zijn die toegang heeft tot en zich aanmeldt bij Cloud Manager.
* Hoe uw cloudprogramma en -omgevingen worden gemaakt.

## Inleiding {#introduction}

Het toevoegen van cloudbronnen gebeurt via Cloud Manager door uw teamlid dat is toegewezen aan het productprofiel van Cloud Manager Business Owner. Dit individu begrijpt meestal de zakelijke behoeften en voltooit de initiële installatie van Cloud Manager.

Volg de onderstaande secties om te leren hoe u uw [cloudserviceprogramma&#39;s](#create-cloud-service-program) en [omgevingen](#create-cloud-environments) kunt maken.

### Voorwaarden {#prerequisites}

* De systeembeheerder die is toegewezen aan de rol Bedrijfseigenaar moet toegang hebben tot en zich aanmelden bij Cloud Manager.

* Begrijp hoe te [navigeren en login aan de Manager van de Wolk](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/what-is-required/navigate-to-cloud-manager.html?lang=en).

* Zorg dat u bekend bent met de [productprofielen van Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#cloud-manager-product-profiles).

* Begrijp de concepten Cloud Manager [programma&#39;s](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/understand-program-types.html?lang=en) en [omgevingen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html?lang=en)

## Navigeren naar Cloud Manager {#navigate-cloud-manager}

De gebruiker van de Bedrijfs Eigenaar zal een welkome e-mail met een verbinding ontvangen om te beginnen, of als zij niet het kunnen vinden, toegang [Cloud Manager](https://my.cloudmanager.adobe.com/) door het programma te openen gebruikend uw Adobe ID.

Ga als volgt te werk om naar Cloud Manager te navigeren:

1. Klik in uw welkomstbericht op **Aan de slag**, zoals in de onderstaande afbeelding wordt getoond.
   ![](/help/onboarding/onboarding-journey/assets/get-started-email.png)

1. U gaat naar de pagina **Programma&#39;s en producten** van Cloud Manager.

   >[!IMPORTANT]
   >U kunt ook rechtstreeks naar de aanmeldingspagina van Cloud Manager navigeren via [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/). Markeer deze pagina ter referentie als bladwijzer en om u te helpen rechtstreeks naar de landingspagina van Cloud Manager te navigeren.

1. U wordt doorgestuurd naar de bestemmingspagina van Cloud Manager. Zie [De sectie Programma&#39;s van Cloud Manager bekijken](#viewing-programs) voor meer informatie.

Daarnaast kunt u vanaf de startpagina van Adobe Experience Cloud naar de pagina **Programma&#39;s en producten** van Cloud Manager navigeren. Voer de onderstaande stappen uit:

1. Navigeer rechtstreeks naar [Adobe Experience Cloud](https://experience.adobe.com) en meld u aan met uw Adobe ID.

1. Selecteer **Experience Manager** op de startpagina van Adobe Experience Cloud.

   ![](/help/onboarding/onboarding-journey/assets/setup-resources2.png)

1. Hiermee gaat u naar de AEM homepage. Start **Cloud Manager** vanaf hier.

   ![](/help/onboarding/onboarding-journey/assets/setup-resources3.png)

1. Nadat u zich hebt aangemeld, gaat u naar de bestemmingspagina van Cloud Manager. Zie [De sectie Programma&#39;s van Cloud Manager bekijken](#viewing-programs) voor meer informatie.

   >[!NOTE]
   >Afhankelijk van de rollen die in [!UICONTROL Cloud Manager] en de staat van de toepassing worden toegewezen, zult u verschillende schermen zien terwijl het gebruiken van [!UICONTROL Cloud Manager] UI.

### Programma&#39;s weergeven op de bestemmingspagina van Cloud Manager {#viewing-programs}

Nadat u zich hebt aangemeld, gaat u naar de bestemmingspagina van Cloud Manager. Een van de drie opties wordt hieronder beschreven:

#### Als er geen programma&#39;s bestaan in Cloud Manager {#no-programs}

Als er geen programma&#39;s in uw organisatie aanwezig zijn, wordt u op de bestemmingspagina opgedragen het eerste programma te maken, zoals in de onderstaande afbeelding wordt getoond.

![](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin0.png)

#### Wanneer er al programma&#39;s bestaan in Cloud Manager {#programs-exist}

Als er al programma&#39;s bestaan in uw organisatie, wordt u op de bestemmingspagina opgedragen een ander programma toe te voegen en worden ook alle bestaande programma&#39;s weergegeven, zoals in de onderstaande afbeelding wordt getoond.

![](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin1.png)

#### Wanneer een Programma bestaat en de gebruiker de Beheerder van het Systeem is {#programs-exist-sysadmin}

Als een of meer programma&#39;s al in uw organisatie aanwezig zijn en u een systeembeheerder bent, wordt op de landingspagina de knop **Toegang beheren** weergegeven, samen met de optie **Programma toevoegen**, zoals in de onderstaande afbeelding wordt getoond.

![](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/admin-console-4.png)


## Gebruikersrollen controleren {#verify-user-roles}

Nadat u zich hebt aangemeld bij Cloud Manager, volgt u de onderstaande stappen om te controleren of u het productprofiel van de eigenaar van het bedrijf hebt toegewezen:

1. Selecteer uw profiel rechtsboven, zoals hieronder wordt getoond.

   ![](/help/onboarding/onboarding-journey/assets/setup-resources5.png)

1. Selecteer **Gebruikersrollen** en zorg ervoor dat u aan Bedrijfseigenaar wordt toegewezen.

   ![](/help/onboarding/onboarding-journey/assets/setup-resources6.png)

1. Dit bevestigt uw gebruikersrol als Bedrijfseigenaar.

   ![](/help/onboarding/onboarding-journey/assets/setup-resources7.png)

   Geweldig werk! U hebt zich met succes aangemeld bij Cloud Manager als bedrijfseigenaar.

## Cloud Service-programma maken {#create-cloud-service-program}

Voer de onderstaande stappen uit om uw cloudserviceprogramma te maken vanuit Cloud Manager:

1. Navigeer naar de bestemmingspagina van Cloud Manager, zoals hieronder wordt getoond.

   >[!NOTE]
   >U moet een teamlid zijn dat is toegewezen aan het productprofiel van de Business Owner van Cloud Manager om deze stap te kunnen voltooien.

   Van hier, klik op **Add Programma** om de Add tovenaar van het Programma te lanceren.

   ![](/help/onboarding/onboarding-journey/assets/setup-resources4.png)

   >[!NOTE]
   >Bekijk de [video](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html?lang=en) om te leren hoe u uw AEM maakt als een Cloud-programma en meer informatie te krijgen over belangrijke overwegingen voordat u uw programma maakt.

   >[!IMPORTANT]
   >Voor geleidelijke instructie op hoe te om de Add tovenaar van het Programma te gebruiken, ga [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/production-programs/creating-production-program.html?lang=en).
   >
   >* Vergeet niet dat de naam van het programma na het maken niet kan worden gewijzigd. We raden u aan zeker te zijn van de naam die u aan uw programma wilt geven.
   >* Als u de naam van het programma moet wijzigen, moet u een kwestie openen met Adobe Support of contact opnemen met uw Adobe-vertegenwoordiger. Zij zullen helpen bij het effectief schrappen van het programma. U moet opnieuw beginnen met mogelijk verlies van werk dat uw team heeft gedaan.


1. Wanneer uw cloudprogramma met succes is gemaakt, kunt u naar uw programma navigeren om de pagina **Overzicht** van uw programma weer te geven, zoals hieronder wordt weergegeven.

   ![](/help/onboarding/onboarding-journey/assets/setup-resources8.png)

   >[!NOTE]
   >Als u dat nog niet hebt gedaan, is het nu een goed moment om uw leden voor ontwikkelaars toe te voegen aan uw team voor Cloud Manager. Raadpleeg het productprofiel Gebruikers toevoegen aan ontwikkelaar en volg de beschreven stappen.

1. Leden die zijn toegewezen aan het productprofiel voor ontwikkelaars kunnen zich aanmelden bij Cloud Manager en [Cloud Manager Git](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/managing-code/accessing-git.html?lang=en) beheren.

   Geweldig werk! Uw programma is nu gemaakt en uw Cloud Manager Git kan door uw ontwikkelaars worden geopend!


## Creëer uw Cloud-omgevingen {#create-cloud-environments}

Wanneer u uw cloudprogramma hebt gemaakt, maakt u uw cloudomgevingen.

Voer de onderstaande stappen uit om uw cloud-omgevingen te maken met Cloud Manager:

1. Navigeer naar de pagina **Overzicht** van Cloud Manager en selecteer **Add** van de milieukaart.

   ![](/help/onboarding/onboarding-journey/assets/setup-resources9.png)

   >[!IMPORTANT]
   >Een gebruiker van de Manager van de Wolk in de rol Bedrijfs van de Eigenaar of van de Manager van de Plaatsing moet worden het programma geopend om deze stap met succes te voltooien.

   Bekijk bovendien de korte [videozelfstudie](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=en) voor meer informatie over de omgevingen van Cloud Manager en over de manier waarop u deze aan uw programma kunt toevoegen.

1. Hiermee wordt de wizard voor het toevoegen van omgevingen gestart die u begeleidt bij het toevoegen van uw omgeving. Voeg eerst uw ontwikkelomgeving toe om vertrouwd te raken met de wizard. Raadpleeg [Een omgeving toevoegen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html?lang=en#adding-environments) voor meer informatie.

   >[!NOTE]
   >Als u dat nog niet hebt gedaan, is het nu een goed moment om uw leden voor ontwikkelaars toe te voegen aan uw team voor Cloud Manager. Raadpleeg het productprofiel Gebruikers toevoegen aan ontwikkelaar en volg de beschreven stappen.

1. Leden die zijn toegewezen aan het productprofiel voor ontwikkelaars kunnen zich aanmelden bij Cloud Manager en [Cloud Manager Git](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/managing-code/accessing-git.html?lang=en) beheren.

   Geweldig werk! Uw programma is nu gemaakt en uw Cloud Manager Git is beschikbaar voor uw ontwikkelaars.

   Gefeliciteerd! Uw cloudprogrammaomgevingen zijn nu gemaakt en uw ontwikkelaars zijn toegevoegd aan het team!

## Volgende functies {#whats-next}

Aan uw teamleden moeten machtigingen voor de instantie worden verleend, aangezien machtigingen voor het beheren van Cloud Manager niet voldoende zijn. Nu uw wolkenmiddelen zijn gecreeerd en klaar om door uw team worden betreden, moet de Beheerder van het Systeem uw teamleden aan AEM als profielen van de Cloud Service van Adobe Admin Console toewijzen.

>[!NOTE]
>Om toegang tot AEM als Cloud Service te krijgen, moeten gebruikers tot één van twee productprofielen `AEM Users` of `AEM Administrators` behoren. Zie [Producten en Toegang van de Gebruiker in Admin Console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html?lang=en#managing-products-and-user-access-in-admin-console) beheren om meer te leren.

U zou uw aan boord komende reis door het document moeten voortzetten dat de Leden van het Team toewijst om als Profielen van het Product van de Cloud Service te AEM.


## Aanvullende bronnen {#additional-resources}

Volg de aanvullende bronnen voor meer informatie over:

* [Programmypen en toevoegen van een programma](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html?lang=en)
* [Omgevingstypen en een omgeving toevoegen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=en)
* [Cloud Manager-kit beheren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/managing-code/accessing-git.html?lang=en)
* [Toegang tot AEM configureren als Cloud Service van Admin Console](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/overview.html?lang=en#adobe-ims-users)
