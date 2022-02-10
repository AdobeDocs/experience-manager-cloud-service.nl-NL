---
title: Cloud Resources instellen via Cloud Manager
description: Leer hoe u Cloud Manager kunt gebruiken om uw eigen cloudbronnen in te stellen en te beheren.
role: Admin, User, Developer
exl-id: de3a33b7-b459-4e47-b232-a0f88e2ce22e
source-git-commit: 22a08a0cb80052485309ce3d33537e9fe303c6f5
workflow-type: tm+mt
source-wordcount: '1365'
ht-degree: 0%

---

# Cloud Resources instellen via Cloud Manager {#setup-cloud-resources}

Leer hoe u Cloud Manager kunt gebruiken om uw eigen cloudbronnen in te stellen en te beheren.

## Doelstelling {#objective}

Dit document helpt u te begrijpen hoe uw cloudbronnen zijn gemaakt en wie deze kan maken. Na het lezen van deze sectie moet u begrijpen:

* Een systeembeheerder die aan de **Zakelijke eigenaar** rol moet de eerste rol in uw organisatie zijn om u aan te melden en toegang te krijgen tot Cloud Manager.
* Hoe uw cloudprogramma en -omgevingen worden gemaakt.

## Inleiding {#introduction}

Het toevoegen van cloudbronnen gebeurt via Cloud Manager door uw teamlid dat is toegewezen aan de **Zakelijke eigenaar** productprofiel. Dit individu begrijpt meestal de zakelijke behoeften en voltooit de initiële installatie van Cloud Manager.

Volg de onderstaande secties om te leren hoe u uw [cloudserviceprogramma&#39;s](#create-cloud-service-program) en [omgevingen.](#create-cloud-environments)

### Vereisten {#prerequisites}

* De systeembeheerder die aan **Zakelijke eigenaar** rol moet zich hebben aangemeld bij Cloud Manager voordat andere gebruikers met de functie **Zakelijke eigenaar** Hiermee wordt geprobeerd toegang te krijgen tot Cloud Manager om de in dit document beschreven stappen uit te voeren en uit te voeren.

   * Terugkeren naar de [Teamleden toewijzen aan productprofielen van Cloud Manager](/help/journey-onboarding/sysadmin/assign-team-members-cloud-manager.md) een document van deze reis voor meer informatie .

* U moet begrijpen hoe [navigeer en meld u aan bij Cloud Manager.](/help/onboarding/learn-concepts/cloud-manager-introduction.md)

* U zou vertrouwd met moeten zijn [Productprofielen van Cloud Manager.](/help/onboarding/learn-concepts/aem-cs-team-product-profiles.md#cloud-manager-product-profiles)

* U moet de concepten van Cloud Manager begrijpen [programma&#39;s](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/understand-program-types.md) en [omgevingen.](/help/implementing/cloud-manager/manage-environments.md)

## Toegang tot Cloud Manager als systeembeheerder en bedrijfseigenaar {#access-sysadmin-bo}

Voor de teamleden die u aan de **Zakelijke eigenaar** de rol kan tot wolkenmanager toegang hebben en beginnen met het creëren van wolkenmiddelen, moet de Beheerder van het Systeem toewijzen **Zakelijke eigenaar** rol en meld u aan bij Cloud Manager.

1. Zorg ervoor dat u, als systeembeheerder, de **Zakelijke eigenaar** rol toegewezen.

   * Terugkeren naar de vorige stap van deze reis, [Teamleden toewijzen aan productprofielen van Cloud Manager,](/help/journey-onboarding/sysadmin/assign-team-members-cloud-manager.md) voor meer informatie over de toewijzing van de **Zakelijke eigenaar** rol aan de Beheerder van het Systeem als u dit nog niet hebt gedaan.

1. Aanmelden bij Cloud Manager op [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en worden aangeboden met de normale landingspagina.

Door u met succes aan te melden als Systeembeheerder met de **Zakelijke eigenaar** rol, initialiseert u Cloud Manager voor gebruik door andere gebruikers met **Zakelijke eigenaar** rol. Je ontvangt geen bevestiging van dit bericht of een bericht. Eenvoudig aanmelden is voldoende.

Totdat u zich bij Cloud Manager als systeembeheerder aanmeldt bij het dialoogvenster **Zakelijke eigenaar** rol, andere gebruikers met de **Zakelijke eigenaar** met deze rol kunnen geen programma&#39;s worden gemaakt in Cloud Manager, zelfs niet als aan deze programma&#39;s de juiste rollen zijn toegewezen.

## Navigeren naar Cloud Manager {#navigate-cloud-manager}

De gebruiker met de **Zakelijke eigenaar** de rol zal een welkome e-mail met een verbinding ontvangen om te beginnen. Volg de onderstaande stappen om naar Cloud Manager te navigeren met deze welkomstmail.

1. Klik op **Aan de slag**, zoals weergegeven in onderstaande afbeelding.
   ![E-mailvoorbeeld](/help/journey-onboarding/assets/get-started-email.png)

1. U gaat naar Cloud Manager **Programma&#39;s en producten** pagina.

   >[!TIP]
   >
   >U kunt ook rechtstreeks naar de aanmeldingspagina van Cloud Manager navigeren vanuit [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/). Bladwijzer maken van deze pagina voor toekomstig gebruik.

1. U wordt doorgestuurd naar de bestemmingspagina van Cloud Manager. Zie [De programma&#39;s van Cloud Manager weergeven](#viewing-programs) voor meer informatie.

U kunt ook naar Cloud Manager navigeren **Programma&#39;s en producten** pagina van Adobe Experience Cloud homepage door deze stappen te volgen

1. Ga rechtstreeks naar [Adobe Experience Cloud](https://experience.adobe.com) en meld u aan met uw Adobe ID.

1. Selecteer op de startpagina van Adobe Experience Cloud de optie **Experience Manager**.

   ![Experience Cloud homepage](/help/journey-onboarding/assets/setup-resources2.png)

1. Hiermee gaat u naar de AEM homepage. Klik hier op **Starten** op de **Cloud Manager** tegel.

   ![AEM homepage](/help/journey-onboarding/assets/setup-resources3.png)

1. Nadat u zich hebt aangemeld, gaat u naar de bestemmingspagina van Cloud Manager. Zie [De programma&#39;s van Cloud Manager weergeven](#viewing-programs) voor meer informatie.

De manier waarop u via Cloud Manager toegang krijgt tot uw programma&#39;s en producten is een zaak van u en heeft geen invloed op de manier waarop u Cloud Manager gebruikt of op de manier waarop u uw programma&#39;s beheert.

>[!NOTE]
>
>Afhankelijk van de rollen die binnen worden toegewezen [!UICONTROL Cloud Manager] en de status van de toepassing, ziet u verschillende schermen tijdens het gebruik [!UICONTROL Cloud Manager] UI.

### Programma&#39;s weergeven {#viewing-programs}

Zodra u toegang hebt tot Cloud Manager, hangt wat u ziet af van de status van uw programma&#39;s, zoals in de volgende secties wordt beschreven.

#### Als er geen programma&#39;s bestaan {#no-programs}

Als er geen programma&#39;s in uw organisatie aanwezig zijn, wordt u op de bestemmingspagina opgedragen het eerste programma te maken.

![Geen programma&#39;s](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin0.png)

#### Wanneer er al programma&#39;s bestaan {#programs-exist}

Als programma&#39;s al in uw organisatie aanwezig zijn, wordt op de landingspagina uw bestaande programma&#39;s weergegeven en wordt ook een knop weergegeven om aanvullende programma&#39;s toe te voegen.

![Er bestaan programma&#39;s](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin1.png)

#### Wanneer een Programma bestaat en u een Beheerder van het Systeem bent {#programs-exist-sysadmin}

Als programma&#39;s al in uw organisatie bestaan en u een Systeembeheerder bent, wordt de landingspagina weergegeven **Toegang beheren** samen met **Programma toevoegen** optie.

![Systeembeheerweergave](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/admin-console-4.png)


## Gebruikersrollen controleren {#verify-user-roles}

Nadat u zich hebt aangemeld bij Cloud Manager, kunt u controleren of u de opdracht **Zakelijke eigenaar** productprofiel.

1. Selecteer het profiel rechtsboven in het venster.

   ![Gebruikersprofiel](/help/journey-onboarding/assets/setup-resources5.png)

1. Selecteren **Gebruikersrollen** om de rollen te tonen die aan uw gebruiker worden toegewezen.

   ![Gebruikersrollen](/help/journey-onboarding/assets/setup-resources6.png)

1. Bevestigt uw gebruiker heeft **Zakelijke eigenaar** rol.

   ![Lijst met gebruikersrollen](/help/journey-onboarding/assets/setup-resources7.png)

U hebt zich met succes aangemeld bij Cloud Manager als bedrijfseigenaar. Als u geen toegewezen **Zakelijke eigenaar** en neemt u contact op met uw systeembeheerder.

## Een Cloud Service-programma maken {#create-cloud-service-program}

Nu u ervoor hebt gezorgd dat u de juiste toegang hebt, kunt u uw eerste programma maken.

1. Ga naar de bestemmingspagina van Cloud Manager op [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en meld u aan.

1. Klik op de bestemmingspagina van Cloud Manager op **Programma toevoegen** om de wizard Programma toevoegen te starten.

   ![Openingspagina](/help/journey-onboarding/assets/setup-resources4.png)

   >[!TIP]
   >
   >Voor geleidelijke instructie op hoe te om de Add tovenaar van het Programma te gebruiken, verwijs naar het document [Productieprogramma&#39;s maken](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-program.md) of bekijk dit [video](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html) voor meer informatie over het maken van uw AEM als een Cloud-programma en voor meer informatie over belangrijke overwegingen voordat u uw programma maakt.


1. Als uw cloudprogramma met succes is gemaakt, kunt u vanuit de landingspagina van Cloud Manager naar uw programma navigeren om de **Overzicht** pagina van uw programma.

   ![Overzicht van programma](/help/journey-onboarding/assets/setup-resources8.png)

1. Leden die zijn toegewezen aan het productprofiel voor ontwikkelaars kunnen zich aanmelden bij Cloud Manager en de opslagruimten voor cloudbeheer beheren.

   * Als u dat nog niet hebt gedaan, is het nu een goed moment om leden toe te wijzen aan de **Ontwikkelaar** rol in uw Cloud Manager-team. Terugkeren naar de [Teamleden toewijzen aan productprofielen van Cloud Manager](/help/journey-onboarding/sysadmin/assign-team-members-cloud-manager.md) een document van deze reis voor meer informatie .

Uw programma is nu gemaakt en de gegevensopslagruimte van uw cloudbeheer is beschikbaar voor uw ontwikkelaars.

## Creëer uw Cloud-omgevingen {#create-cloud-environments}

Wanneer u uw cloudprogramma hebt gemaakt, maakt u uw cloudomgevingen.

1. Ga naar de bestemmingspagina van Cloud Manager op [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u **Toevoegen** van de milieukaart.

   ![Knop Omgeving toevoegen](/help/journey-onboarding/assets/setup-resources9.png)

1. De wizard voor het toevoegen van omgevingen start en begeleidt u door het toevoegen van uw omgeving. Voeg eerst uw ontwikkelomgeving toe om vertrouwd te raken met de wizard.

   >[!TIP]
   >
   >Het document raadplegen [Een omgeving toevoegen](/help/implementing/cloud-manager/manage-environments.md#adding-environments) voor meer informatie of om te kijken [deze korte videozelfstudie](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html) voor meer informatie over omgevingen in Cloud Manager en hoe u deze aan uw programma kunt toevoegen.

1. Aan de **Ontwikkelaar** Met het profiel product kunt u zich aanmelden bij Cloud Manager en de Git-opslagruimten van Cloud Manager beheren.

Het programma is nu gemaakt en uw cloudbeheerpakket is beschikbaar voor uw ontwikkelaars.

## Volgende functies {#whats-next}

Nu uw wolkenmiddelen zijn gecreeerd en klaar om door uw team worden betreden, moet de Beheerder van het Systeem uw teamleden aan AEM as a Cloud Service productprofielen van Adobe Admin Console toewijzen om tot die middelen toegang te hebben.

U moet uw instapreis voortzetten door het document opnieuw te bekijken [Teamleden toewijzen aan AEM as a Cloud Service productprofielen](/help/journey-onboarding/sysadmin/assign-team-members-aem-cloud-service.md) waar u zult leren hoe te om uw teamleden de rechten te verlenen zij hebben om tot uw nieuwe milieu&#39;s toegang te hebben.

## Aanvullende bronnen {#additional-resources}

Volg de aanvullende bronnen voor meer informatie over:

* [Programmypen en toevoegen van een programma](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html)
* [Omgevingstypen en een omgeving toevoegen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html)
* [Cloud Manager-kit beheren](/help/implementing/cloud-manager/managing-code/accessing-repos.md)
* [Toegang tot AEM as a Cloud Service vanaf Admin Console configureren](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/overview.html#adobe-ims-users)
