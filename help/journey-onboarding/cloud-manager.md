---
title: Cloud Manager openen
description: Leer hoe u toegang krijgt tot Cloud Manager zodat u uw projectbronnen kunt instellen.
role: Admin, User, Developer
exl-id: c9476ac9-8318-493e-a48d-94ff5a6433a7
source-git-commit: 0e0337f6e14aa2f5b616ebc0a4b3c95089637369
workflow-type: tm+mt
source-wordcount: '1040'
ht-degree: 0%

---

# Cloud Manager openen {#cloud-resources}

In dit deel van het [aan boord gaan,](overview.md) U leert hoe u toegang krijgt tot Cloud Manager zodat u uw projectbronnen kunt instellen.

## Doelstelling {#objective}

In het vorige artikel van deze instapreis: [Teamleden toewijzen aan productprofielen van Cloud Manager,](assign-profiles-cloud-manager.md) u hebt uw AEMaaCS-team de juiste rollen toegekend. Leer nu hoe u toegang krijgt tot Cloud Manager, zodat u de projectbronnen kunt instellen die door uw team worden gebruikt.

Aangezien u de vorige stap hebt uitgevoerd, heeft uw team toegang tot Cloud Manager. Cloud Manager wordt gebruikt om uw projectbronnen, zoals programma&#39;s en omgevingen, te maken en te beheren.

Nadat u dit document hebt gelezen, hebt u het volgende nodig:

* Dat een systeembeheerder aan toegewezen **Zakelijke eigenaar** rol moet de eerste rol in uw organisatie zijn om u aan te melden en toegang te krijgen tot Cloud Manager.
* Aanmelden bij Cloud Manager.

## Cloud Manager {#cloud-manager}

Cloud Manager is een essentieel onderdeel van AEM as a Cloud Service en fungeert als één ingangspunt voor uw team. Het steunt klanten met ondernemingsontwikkelingsmontages met zijn speciaal gebouwde CI/CD pijpleidingen, die worden uitgerust om grondig te verzekeren en hoogste codekwaliteit om uitzonderlijke ervaringen te leveren. Cloud Manager biedt alles wat nodig is om op zelfbediening aan de slag te gaan, inclusief de mogelijkheid om cloudbronnen en -omgevingen te maken.

Typisch een teamlid dat aan wordt toegewezen **Zakelijke eigenaar** Het productprofiel is verantwoordelijk voor het toevoegen van cloudbronnen, zoals programma&#39;s en omgevingen. Dit individu begrijpt de bedrijfsbehoeften en wie de initiële installatie van Cloud Manager voltooit.

In het kader van deze instapreis hebt u als systeembeheerder al uzelf toegewezen aan de **Zakelijke eigenaar** productprofiel en kan de cloudbronnen instellen. Afhankelijk van daadwerkelijke projectvereisten, kunnen de bedrijfseigenaars of niet het zelfde als de systeembeheerder zijn.

## Toegang tot Cloud Manager als systeembeheerder en bedrijfseigenaar {#access-sysadmin-bo}

Voor de teamleden die u aan de **Zakelijke eigenaar** de rol kan tot wolkenmanager toegang hebben en beginnen met het creëren van wolkenmiddelen, moet de systeembeheerder worden toegewezen **Zakelijke eigenaar** rol. Ze moeten zich ook aanmelden bij Cloud Manager, net als in de vorige stap op deze instapreis.

1. Zorg ervoor dat u, als systeembeheerder, de **Zakelijke eigenaar** rol toegewezen.

   * Terugkeren naar de vorige stap van deze reis, [Teamleden toewijzen aan productprofielen van Cloud Manager,](assign-profiles-cloud-manager.md) voor meer informatie over de toewijzing van de **Zakelijke eigenaar** rol aan de systeembeheerder.

1. Aanmelden bij Cloud Manager op [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en worden aangeboden met de normale landingspagina.

Door u met succes aan te melden als systeembeheerder met de **Zakelijke eigenaar** rol, initialiseert u Cloud Manager voor gebruik door andere gebruikers met **Zakelijke eigenaar** rol. Je ontvangt geen bevestiging of bericht. Eenvoudig aanmelden is voldoende.

Totdat u zich bij Cloud Manager aanmeldt als systeembeheerder met de **Zakelijke eigenaar** rol, andere gebruikers met de **Zakelijke eigenaar** rol kan geen programma&#39;s maken in Cloud Manager. Deze regel is waar zelfs als zij de correcte rollen worden toegewezen.

## Navigeren naar Cloud Manager {#navigate-cloud-manager}

Gebruikers met de **Zakelijke eigenaar** de rol ontvangt een welkomstbericht met een koppeling om aan de slag te gaan. Volg de onderstaande stappen om naar Cloud Manager te navigeren met deze welkomstmail.

1. Klik in uw welkomstbericht op **Aan de slag**, zoals weergegeven in onderstaande afbeelding.
   ![E-mailvoorbeeld](/help/journey-onboarding/assets/get-started-email.png)

1. Ga naar Cloud Manager **Programma&#39;s en producten** pagina.

   >[!TIP]
   >
   >U kunt ook rechtstreeks naar de aanmeldingspagina van Cloud Manager navigeren vanuit `[my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)`. Bladwijzer maken van deze pagina voor toekomstig gebruik.

1. U wordt doorgestuurd naar de bestemmingspagina van Cloud Manager.

U kunt ook naar Cloud Manager navigeren **Programma&#39;s en producten** pagina van Adobe Experience Cloud homepage door deze stappen te volgen

1. Ga rechtstreeks naar [Adobe Experience Cloud](https://experience.adobe.com) en aanmelden met uw Adobe ID.

1. Selecteer op de startpagina van Adobe Experience Cloud de optie **Experience Manager** om de AEM homepage te openen.

   ![Homepage van Experience Cloud](/help/journey-onboarding/assets/setup-resources2.png)

1. Op de **Cloud Manager** tegel, selecteren **Starten**.

   ![AEM homepage](/help/journey-onboarding/assets/setup-resources3.png)

1. Nadat u zich hebt aangemeld, gaat u naar de bestemmingspagina van Cloud Manager. Zie [De programma&#39;s van Cloud Manager weergeven](#viewing-programs) voor meer informatie .

De manier waarop u via Cloud Manager toegang krijgt tot uw programma&#39;s en producten is een zaak van u en heeft geen invloed op de manier waarop u Cloud Manager gebruikt of op de manier waarop u uw programma&#39;s beheert.

>[!NOTE]
>
>Afhankelijk van de rollen die in de Manager van de Wolk worden toegewezen en de staat van de toepassing, ziet u verschillende schermen terwijl het gebruiken van de gebruikersinterface van de Manager van de Wolk.

## Programma&#39;s weergeven {#viewing-programs}

Nadat u Cloud Manager hebt geopend, is wat u ziet afhankelijk van de status van uw programma&#39;s, zoals in de volgende secties wordt beschreven.

### Als er geen programma&#39;s bestaan {#no-programs}

Als er geen programma&#39;s in uw organisatie aanwezig zijn, wordt u op de bestemmingspagina opgedragen het eerste programma te maken.

![Geen programma&#39;s](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin0.png)

### Wanneer er al programma&#39;s bestaan {#programs-exist}

Als er programma&#39;s in uw organisatie aanwezig zijn, wordt op de landingspagina uw bestaande programma&#39;s weergegeven en wordt ook een knop weergegeven waarmee u aanvullende programma&#39;s kunt toevoegen.

![Er bestaan programma&#39;s](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin1.png)

### Wanneer een Programma bestaat en u een Beheerder van het Systeem bent {#programs-exist-sysadmin}

Als programma&#39;s in uw organisatie bestaan en u een systeembeheerder bent, dan toont uw landingspagina **Toegang beheren** knop samen met **Programma toevoegen** -optie.

![Systeembeheerweergave](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/admin-console-4.png)

## Gebruikersrollen controleren {#verify-user-roles}

Nadat u zich hebt aangemeld bij Cloud Manager, kunt u controleren of u de opdracht **Zakelijke eigenaar** productprofiel.

1. Selecteer het profiel rechtsboven in het venster.

1. Om de rollen te tonen die aan uw gebruiker worden toegewezen, selecteer **Gebruikersrollen**.

   ![Gebruikersrollen](/help/journey-onboarding/assets/setup-resources6.png)

1. Het dialoogvenster moet bevestigen dat de gebruiker **Zakelijke eigenaar** rol.

   ![Lijst met gebruikersrollen](/help/journey-onboarding/assets/setup-resources7.png)

U hebt zich met succes aangemeld bij Cloud Manager als bedrijfseigenaar. Als u geen toegewezen **Zakelijke eigenaar** en neemt u contact op met uw systeembeheerder.

## Volgende functies {#whats-next}

Nu u Cloud Manager kunt openen als systeembeheerder, kunt u het eerste programma maken.

Ga door met de volgende revisie van het document [Een programma maken](create-program.md) waar u leert om dit te doen.

## Aanvullende bronnen {#additional-resources}

Hieronder volgen aanvullende, optionele bronnen als u verder wilt gaan dan de inhoud van de instapreis.

* [Inleiding tot Cloud Manager](/help/onboarding/cloud-manager-introduction.md) - Meer informatie over Cloud Manager, Cloud Manager-programma&#39;s en omgevingen.
* [as a Cloud Service teams en productprofielen AEM](/help/onboarding/aem-cs-team-product-profiles.md) - Leer hoe AEM as a Cloud Service teams en productprofielen toegang tot uw gelicentieerde oplossingen voor Adoben kunnen verlenen en beperken.
<!-- ERROR: Not Found (HTTP error 404) * [AEM Champion Tips and Tricks - Cloud Manager UI](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/expert-resources/aem-champions/cloud-manager-ui.md) - Watch this video for an overview of Cloud Manager's UI from an AEM champion. -->
