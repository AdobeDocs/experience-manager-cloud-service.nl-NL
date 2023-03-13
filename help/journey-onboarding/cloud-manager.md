---
title: Cloud Manager openen
description: Leer hoe u toegang krijgt tot Cloud Manager zodat u uw projectbronnen kunt instellen.
role: Admin, User, Developer
exl-id: c9476ac9-8318-493e-a48d-94ff5a6433a7
source-git-commit: 225b34f081a942d67dfc1f6faeb09763ea9fde03
workflow-type: tm+mt
source-wordcount: '1055'
ht-degree: 0%

---

# Cloud Manager openen {#cloud-resources}

In dit deel van het [aan boord gaan,](overview.md) U leert hoe u toegang krijgt tot Cloud Manager zodat u uw projectbronnen kunt instellen.

## Doelstelling {#objective}

In het vorige artikel van deze instapreis: [Teamleden toewijzen aan productprofielen van Cloud Manager,](assign-profiles-cloud-manager.md) u hebt uw AEMaaCS-team de juiste rollen toegekend. Leer nu hoe u toegang krijgt tot Cloud Manager, zodat u uw projectbronnen kunt instellen die uw team zal gebruiken.

Aangezien u de vorige stap hebt uitgevoerd, heeft uw team toegang tot Cloud Manager. Cloud Manager wordt gebruikt om uw projectbronnen, zoals programma&#39;s en omgevingen, te maken en te beheren.

Na het lezen van dit document moet u begrijpen:

* Dat een systeembeheerder aan toegewezen **Zakelijke eigenaar** rol moet de eerste rol in uw organisatie zijn om u aan te melden en toegang te krijgen tot Cloud Manager.
* Meld u aan bij Cloud Manager.

## Cloud Manager {#cloud-manager}

Cloud Manager is een essentieel onderdeel van AEM as a Cloud Service en fungeert als één ingangspunt voor uw team. Het steunt klanten met ondernemingsontwikkelingsmontages met zijn speciaal gebouwde CI/CD pijpleidingen, die worden uitgerust om grondig te verzekeren en hoogste codekwaliteit om uitzonderlijke ervaringen te leveren. Cloud Manager biedt alles wat nodig is om op zelfbediening aan de slag te gaan, inclusief de mogelijkheid om cloudbronnen en -omgevingen te maken.

Typisch een teamlid dat aan wordt toegewezen **Zakelijke eigenaar** Het productprofiel is verantwoordelijk voor het toevoegen van cloudbronnen, zoals programma&#39;s en omgevingen. Dit individu begrijpt de bedrijfsbehoeften en wie de initiële installatie van Cloud Manager voltooit.

In het kader van deze instapreis hebt u als systeembeheerder al uzelf toegewezen aan de **Zakelijke eigenaar** productprofiel en stelt de cloudbronnen in. Afhankelijk van daadwerkelijke projectvereisten, kunnen de bedrijfseigenaars al dan niet het zelfde zijn als de systeembeheerder.

## Toegang tot Cloud Manager als systeembeheerder en bedrijfseigenaar {#access-sysadmin-bo}

Voor de teamleden die u aan de **Zakelijke eigenaar** de rol kan tot wolkenmanager toegang hebben en beginnen met het creëren van wolkenmiddelen, moet de systeembeheerder worden toegewezen **Zakelijke eigenaar** rol en meld u aan bij Cloud Manager, zoals u in de vorige stap van deze instapreis hebt gedaan.

1. Zorg ervoor dat u, als systeembeheerder, de **Zakelijke eigenaar** rol toegewezen.

   * Terugkeren naar de vorige stap van deze reis, [Teamleden toewijzen aan productprofielen van Cloud Manager,](assign-profiles-cloud-manager.md) voor meer informatie over de toewijzing van de **Zakelijke eigenaar** rol aan de systeembeheerder als u dit nog niet hebt gedaan.

1. Aanmelden bij Cloud Manager op [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en worden aangeboden met de normale landingspagina.

Door u met succes aan te melden als systeembeheerder met de **Zakelijke eigenaar** rol, initialiseert u Cloud Manager voor gebruik door andere gebruikers met **Zakelijke eigenaar** rol. Je ontvangt geen bevestiging van dit bericht of een bericht. Eenvoudig aanmelden is voldoende.

Totdat u zich bij Cloud Manager aanmeldt als systeembeheerder met de **Zakelijke eigenaar** rol, andere gebruikers met de **Zakelijke eigenaar** met deze rol kunnen geen programma&#39;s worden gemaakt in Cloud Manager, zelfs niet als aan deze programma&#39;s de juiste rollen zijn toegewezen.

## Navigeren naar Cloud Manager {#navigate-cloud-manager}

Gebruikers met de **Zakelijke eigenaar** de rol zal een welkome e-mail met een verbinding ontvangen om te beginnen. Volg de onderstaande stappen om naar Cloud Manager te navigeren met deze welkomstmail.

1. Klik op **Aan de slag**, zoals weergegeven in onderstaande afbeelding.
   ![E-mailvoorbeeld](/help/journey-onboarding/assets/get-started-email.png)

1. U gaat naar Cloud Manager **Programma&#39;s en producten** pagina.

   >[!TIP]
   >
   >U kunt ook rechtstreeks naar de aanmeldingspagina van Cloud Manager navigeren vanuit `[my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)`. Bladwijzer maken van deze pagina voor toekomstig gebruik.

1. U wordt doorgestuurd naar de bestemmingspagina van Cloud Manager.

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
>Afhankelijk van de rollen die in de Manager van de Wolk worden toegewezen en de staat van de toepassing, zult u verschillende schermen zien terwijl het gebruiken van de UI van de Manager van de Wolk.

## Programma&#39;s weergeven {#viewing-programs}

Zodra u toegang hebt tot Cloud Manager, hangt wat u ziet af van de status van uw programma&#39;s, zoals in de volgende secties wordt beschreven.

### Als er geen programma&#39;s bestaan {#no-programs}

Als er geen programma&#39;s in uw organisatie aanwezig zijn, wordt u op de bestemmingspagina opgedragen het eerste programma te maken.

![Geen programma&#39;s](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin0.png)

### Wanneer er al programma&#39;s bestaan {#programs-exist}

Als programma&#39;s al in uw organisatie aanwezig zijn, wordt op de landingspagina uw bestaande programma&#39;s weergegeven en wordt ook een knop weergegeven om aanvullende programma&#39;s toe te voegen.

![Er bestaan programma&#39;s](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin1.png)

### Wanneer een Programma bestaat en u een Beheerder van het Systeem bent {#programs-exist-sysadmin}

Als er al programma&#39;s in uw organisatie bestaan en u een systeembeheerder bent, wordt de bestemmingspagina weergegeven **Toegang beheren** samen met **Programma toevoegen** optie.

![Systeembeheerweergave](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/admin-console-4.png)

## Gebruikersrollen controleren {#verify-user-roles}

Nadat u zich hebt aangemeld bij Cloud Manager, kunt u controleren of u de opdracht **Zakelijke eigenaar** productprofiel.

1. Selecteer het profiel rechtsboven in het venster.

   ![Gebruikersprofiel](/help/journey-onboarding/assets/setup-resources5.png)

1. Selecteren **Gebruikersrollen** om de rollen te tonen die aan uw gebruiker worden toegewezen.

   ![Gebruikersrollen](/help/journey-onboarding/assets/setup-resources6.png)

1. Het dialoogvenster moet bevestigen dat de gebruiker **Zakelijke eigenaar** rol.

   ![Lijst met gebruikersrollen](/help/journey-onboarding/assets/setup-resources7.png)

U hebt zich met succes aangemeld bij Cloud Manager als bedrijfseigenaar. Als u geen toegewezen **Zakelijke eigenaar** en neemt u contact op met uw systeembeheerder.

## Volgende functies {#whats-next}

Nu u Cloud Manager kunt openen als systeembeheerder, kunt u het eerste programma maken.

U moet uw instapreis voortzetten door het document opnieuw te bekijken [Een programma maken](create-program.md) waar zult u leren dit te doen.

## Aanvullende bronnen {#additional-resources}

Volg de aanvullende bronnen voor meer informatie over:

* [Inleiding tot Cloud Manager](/help/onboarding/cloud-manager-introduction.md) - Meer informatie over Cloud Manager, Cloud Manager-programma&#39;s en omgevingen.
* [as a Cloud Service teams en productprofielen AEM](/help/onboarding/aem-cs-team-product-profiles.md) - Leer hoe AEM as a Cloud Service teams en productprofielen toegang tot uw gelicentieerde Adobe-oplossingen kunnen verlenen en beperken.
