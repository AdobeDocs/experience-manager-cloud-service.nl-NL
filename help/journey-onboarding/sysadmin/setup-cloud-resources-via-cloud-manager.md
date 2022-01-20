---
title: Cloud Resources instellen via Cloud Manager
description: Volg deze pagina voor informatie over het instellen van Cloud Resources via Cloud Manager
role: Admin, User, Developer
exl-id: de3a33b7-b459-4e47-b232-a0f88e2ce22e
source-git-commit: 7fe39bbc8d5e965af7f339b2a524420c76360552
workflow-type: tm+mt
source-wordcount: '1242'
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

Volg de onderstaande secties om te leren hoe u uw [cloudserviceprogramma&#39;s](#create-cloud-service-program) en [omgevingen.](#create-cloud-environments)

### Voorwaarden {#prerequisites}

* De systeembeheerder die is toegewezen aan de rol Bedrijfseigenaar moet toegang hebben tot en zich aanmelden bij Cloud Manager.

* Begrijpen hoe [navigeer en meld u aan bij Cloud Manager.](/help/onboarding/learn-concepts/cloud-manager-introduction.md)

* Wees vertrouwd met [Productprofielen van Cloud Manager.](/help/onboarding/learn-concepts/aem-cs-team-product-profiles.md#cloud-manager-product-profiles)

* Begrijp de concepten van Cloud Manager [programma&#39;s](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/understand-program-types.md) en [omgevingen.](/help/implementing/cloud-manager/manage-environments.md)

## Navigeren naar Cloud Manager {#navigate-cloud-manager}

De gebruiker van de Bedrijfs Eigenaar zal een welkome e-mail met een verbinding ontvangen om te beginnen, of als zij het niet kunnen vinden, toegang hebben [Cloud Manager](https://my.cloudmanager.adobe.com/) direct door u aan te melden met uw Adobe ID.

Ga als volgt te werk om naar Cloud Manager te navigeren:

1. Klik op **Aan de slag**, zoals weergegeven in onderstaande afbeelding.
   ![](/help/journey-onboarding/assets/get-started-email.png)

1. U gaat naar Cloud Manager **Programma&#39;s en producten** pagina.

   >[!IMPORTANT]
   >
   >U kunt ook rechtstreeks naar de aanmeldingspagina van Cloud Manager navigeren vanuit [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/). Bladwijzer maken van deze pagina voor toekomstig gebruik en om u te helpen rechtstreeks naar de landingspagina van Cloud Manager te navigeren.

1. U wordt doorgestuurd naar de bestemmingspagina van Cloud Manager. Zie [De programma&#39;s van Cloud Manager weergeven](#viewing-programs) voor meer informatie.

Bovendien kunt u naar Cloud Manager navigeren **Programma&#39;s en producten** pagina van Adobe Experience Cloud homepage. Voer de onderstaande stappen uit:

1. Ga rechtstreeks naar [Adobe Experience Cloud](https://experience.adobe.com) en meld u aan met uw Adobe ID.

1. Selecteer op de startpagina van Adobe Experience Cloud de optie **Experience Manager**.

   ![](/help/journey-onboarding/assets/setup-resources2.png)

1. Hiermee gaat u naar de AEM homepage. Vanaf hier, starten **Cloud Manager** .

   ![](/help/journey-onboarding/assets/setup-resources3.png)

1. Nadat u zich hebt aangemeld, gaat u naar de bestemmingspagina van Cloud Manager. Zie [De programma&#39;s van Cloud Manager weergeven](#viewing-programs) voor meer informatie.

   >[!NOTE]
   >
   >Afhankelijk van de rollen die binnen worden toegewezen [!UICONTROL Cloud Manager] en de status van de toepassing, ziet u verschillende schermen tijdens het gebruik [!UICONTROL Cloud Manager] UI.

### Programma&#39;s weergeven op de bestemmingspagina van Cloud Manager {#viewing-programs}

Nadat u zich hebt aangemeld, gaat u naar de bestemmingspagina van Cloud Manager. Een van de drie opties wordt hieronder beschreven:

#### Als er geen programma&#39;s bestaan in Cloud Manager {#no-programs}

Als er geen programma&#39;s in uw organisatie aanwezig zijn, wordt u op de bestemmingspagina opgedragen het eerste programma te maken, zoals in de onderstaande afbeelding wordt getoond.

![](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin0.png)

#### Wanneer er al programma&#39;s bestaan in Cloud Manager {#programs-exist}

Als er al programma&#39;s bestaan in uw organisatie, wordt u op de bestemmingspagina opgedragen een ander programma toe te voegen en worden ook alle bestaande programma&#39;s weergegeven, zoals in de onderstaande afbeelding wordt getoond.

![](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin1.png)

#### Wanneer een Programma bestaat en de gebruiker de Beheerder van het Systeem is {#programs-exist-sysadmin}

Als er al programma&#39;s bestaan in uw organisatie en u een systeembeheerder bent, wordt de landingspagina weergegeven **Toegang beheren** samen met **Programma toevoegen** zoals weergegeven in de onderstaande afbeelding.

![](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/admin-console-4.png)


## Gebruikersrollen controleren {#verify-user-roles}

Nadat u zich hebt aangemeld bij Cloud Manager, volgt u de onderstaande stappen om te controleren of u het productprofiel van de eigenaar van het bedrijf hebt toegewezen:

1. Selecteer uw profiel rechtsboven, zoals hieronder wordt getoond.

   ![](/help/journey-onboarding/assets/setup-resources5.png)

1. Selecteren **Gebruikersrollen** en zorg ervoor dat u aan Bedrijfseigenaar wordt toegewezen.

   ![](/help/journey-onboarding/assets/setup-resources6.png)

1. Dit bevestigt uw gebruikersrol als Bedrijfseigenaar.

   ![](/help/journey-onboarding/assets/setup-resources7.png)

   Geweldig werk! U hebt zich met succes aangemeld bij Cloud Manager als bedrijfseigenaar.

## Cloud Service-programma maken {#create-cloud-service-program}

Voer de onderstaande stappen uit om uw cloudserviceprogramma te maken vanuit Cloud Manager:

1. Navigeer naar de bestemmingspagina van Cloud Manager, zoals hieronder wordt getoond.

   >[!NOTE]
   >
   >U moet een teamlid zijn dat is toegewezen aan het productprofiel van de Business Owner van Cloud Manager om deze stap te kunnen voltooien.

   Klik hier op **Programma toevoegen** om de wizard Programma toevoegen te starten.

   ![](/help/journey-onboarding/assets/setup-resources4.png)

   >[!TIP]
   >
   >Kijk naar de [video](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html) voor meer informatie over het maken van uw AEM als een Cloud-programma en voor meer informatie over belangrijke overwegingen voordat u uw programma maakt.

   >[!TIP]
   >
   >Voor stap voor stap instructies op hoe te om de Add tovenaar van het Programma te gebruiken, ga [hier](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-program.md).

1. Wanneer uw cloudprogramma met succes is gemaakt, kunt u naar uw programma navigeren om de **Overzicht** pagina van uw programma, zoals hieronder getoond.

   ![](/help/journey-onboarding/assets/setup-resources8.png)

   >[!NOTE]
   >
   >Als u dit nog niet hebt gedaan, is het nu een goed moment om uw leden voor ontwikkelaars toe te voegen aan uw team voor Cloud Manager. Raadpleeg het productprofiel Gebruikers toevoegen aan ontwikkelaar en volg de beschreven stappen.

1. Leden die zijn toegewezen aan het productprofiel voor ontwikkelaars kunnen zich aanmelden bij Cloud Manager en [Cloud Manager-kit beheren](/help/implementing/cloud-manager/managing-code/accessing-repos.md).

   Geweldig werk! Uw programma is nu gemaakt en uw Cloud Manager Git kan door uw ontwikkelaars worden geopend!


## Creëer uw Cloud-omgevingen {#create-cloud-environments}

Wanneer u uw cloudprogramma hebt gemaakt, maakt u uw cloudomgevingen.

Voer de onderstaande stappen uit om uw cloud-omgevingen te maken met Cloud Manager:

1. Ga naar Cloud Manager **Overzicht** pagina en selecteer **Toevoegen** van de milieukaart.

   ![](/help/journey-onboarding/assets/setup-resources9.png)

   >[!IMPORTANT]
   >
   >Een gebruiker van de Manager van de Wolk in de rol Bedrijfs van de Eigenaar of van de Manager van de Plaatsing moet worden het programma geopend om deze stap met succes te voltooien.

   Kijk ook eens naar de sneltoets [video](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html) zelfstudie voor meer informatie over omgevingen in Cloud Manager en over hoe u deze aan uw programma kunt toevoegen.

1. Hiermee wordt de wizard voor het toevoegen van omgevingen gestart die u begeleidt bij het toevoegen van uw omgeving. Voeg eerst uw ontwikkelomgeving toe om vertrouwd te raken met de wizard. Zie [Een omgeving toevoegen](/help/implementing/cloud-manager/manage-environments.md#adding-environments) voor meer informatie.

   >[!NOTE]
   >
   >Als u dit nog niet hebt gedaan, is het nu een goed moment om uw leden voor ontwikkelaars toe te voegen aan uw team voor Cloud Manager. Raadpleeg het productprofiel Gebruikers toevoegen aan ontwikkelaar en volg de beschreven stappen.

1. Leden die zijn toegewezen aan het productprofiel voor ontwikkelaars kunnen zich aanmelden bij Cloud Manager en [Cloud Manager Git beheren.](/help/implementing/cloud-manager/managing-code/accessing-repos.md)

   Geweldig werk! Uw programma is nu gemaakt en uw Cloud Manager Git is beschikbaar voor uw ontwikkelaars.

   Gefeliciteerd! Uw cloudprogrammaomgevingen zijn nu gemaakt en uw ontwikkelaars zijn toegevoegd aan het team!

## Volgende functies {#whats-next}

Aan uw teamleden moeten machtigingen voor de instantie worden verleend, aangezien machtigingen voor het beheren van Cloud Manager niet voldoende zijn. Nu uw cloudbronnen zijn gemaakt en klaar zijn om door uw team te worden geopend, moet de systeembeheerder uw teamleden toewijzen aan AEM as a Cloud Service productprofielen van Adobe Admin Console.

>[!NOTE]
>
>Om toegang te krijgen tot AEM as a Cloud Service gebruikers, moet deze behoren tot een van twee productprofielen `AEM Users` of `AEM Administrators`. Zie [Producten en gebruikerstoegang in Admin Console beheren](/help/security/ims-support.md#managing-products-and-user-access-in-admin-console) voor meer informatie.

U moet uw instapreis voortzetten door het document opnieuw te bekijken [Teamleden toewijzen aan AEM as a Cloud Service productprofielen.](/help/journey-onboarding/sysadmin/assign-team-members-aem-cloud-service.md)


## Aanvullende bronnen {#additional-resources}

Volg de aanvullende bronnen voor meer informatie over:

* [Programmypen en toevoegen van een programma](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html)
* [Omgevingstypen en een omgeving toevoegen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html)
* [Cloud Manager-kit beheren](/help/implementing/cloud-manager/managing-code/accessing-repos.md)
* [Toegang tot AEM as a Cloud Service vanaf Admin Console configureren](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/overview.html#adobe-ims-users)
