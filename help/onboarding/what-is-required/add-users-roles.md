---
title: Gebruikers en rollen toevoegen - wat is vereist
description: Gebruikers en rollen toevoegen - wat is vereist
translation-type: tm+mt
source-git-commit: 2b7ee2b7b0ce351ed48aeb2f3135c947eafe7247

---


# Gebruikers en rollen toevoegen - wat is vereist {#add-users-roles}


Voor veel functies in [!UICONTROL Cloud Manager] zijn specifieke machtigingen vereist. Zo kunnen alleen bepaalde gebruikers de KPI&#39;s (Key Performance Indicators) voor een programma instellen. Deze toestemmingen worden logisch gezien gegroepeerd in rollen.

[!UICONTROL Cloud Manager] definieert momenteel vier rollen voor gebruikers die de beschikbaarheid van specifieke functies bepalen:

* Zakelijke eigenaar
* Programmabeheerder
* Implementatiebeheer
* Ontwikkelaar

>[!CAUTION]
>
>Als u [!UICONTROL Cloud Manager]wilt gebruiken, hebt u een Adobe-id en de Adobe Managed Services-productcontext nodig.

## Roldefinities {#role-definitions}

>[!NOTE]
>
>De ontwikkelaarspersona in Admin Console is niet gerelateerd aan de rol van de ontwikkelaar in [!UICONTROL Cloud Manager].

De volgende tabel geeft een overzicht van de rollen:

| [!UICONTROL Rollen in Cloud Manager] | Beschrijving |
|--- |--- |
| Zakelijke eigenaar | Verantwoordelijk voor het bepalen van KPIs, het goedkeuren van productieplaatsingen en het met voeten treden van belangrijke 3-tier mislukkingen. |
| Programmabeheerder | Gebruikt [!UICONTROL Cloud Manager] om teamopstelling uit te voeren, status te herzien en KPIs te bekijken. Kan belangrijke fouten met drie niveaus goedkeuren. |
| Implementatiebeheer | Beheert implementatiebewerkingen. Gebruikt [!UICONTROL Cloud Manager] voor het uitvoeren van stage/productie-implementaties. Kan CI/CD pijpleidingen uitgeven. Kan belangrijke fouten met drie niveaus goedkeuren. Kan toegang krijgen tot de Git-opslagplaats. |
| Ontwikkelaar | Ontwikkelt en test aangepaste toepassingscode. Hiermee wordt voornamelijk [!UICONTROL Cloud Manager] gebruikt om de status weer te geven. Kan toegang krijgen tot de Git-opslagplaats voor code commit. |
| Inhoudsauteur | In het algemeen heeft dit geen invloed op [!UICONTROL Cloud Manager]. Kan [!UICONTROL Cloud Manager] Program Switcher (na navigeer vanuit [!UICONTROL Experience Cloud]) gebruiken om toegang te krijgen tot AEM. |

## Beheerconsole gebruiken om een profiel te maken {#using-admin-console-to-create-a-profile}

Rollen worden vanuit de beheerconsole van Adobe beheerd voor [!UICONTROL Cloud Manager] . U kunt specifieke rollidmaatschappen toevoegen door de gebruiker toe te voegen aan een productprofiel voor [!UICONTROL Cloud Manager] in Admin Console.

U kunt specifieke rolinstellingen toewijzen door de gebruiker toe te voegen aan een [!UICONTROL Cloud Manager] - **productprofiel** in de Adobe Admin Console, een centrale locatie voor het beheer van uw Adobe-rechten in uw hele organisatie. Raadpleeg de documentatie bij [Admin Console](https://helpx.adobe.com/enterprise/using/admin-console.html)voor meer informatie over de Adobe Admin Console.

>[!NOTE]
>
>Als u toegang wilt tot de beheerconsole en uw team wilt instellen (gebruikers en rollen), opent u een browser en gaat u naar [https://adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise).

Om de aangewezen op rol-gebaseerde toestemmingen aan de gebruikers van de Manager [!UICONTROL van de] Wolk te verstrekken, moet een beheerder in de **Organisatie** van de klant, nieuwe Profielen van het Product onder de Context van het Product van de Diensten van [!UICONTROL AEM Beheerde] .

Om de aangewezen op rol-gebaseerde toestemmingen aan de gebruikers van de Manager [!UICONTROL van de] Wolk te verstrekken, als beheerder moet u vier nieuwe Profielen van het Product onder de [!UICONTROL AEM Beheerde Context van het Product van de Diensten] creëren die aan elk van de vier rollen van de Manager [!UICONTROL van de] Wolk beantwoorden:

* Zakelijke eigenaar
* Implementatiebeheer
* Ontwikkelaar
* Programmabeheerder

U kunt gebruikers/groepen maken of toevoegen aan deze productprofielen met de [beheerconsole](https://adminconsole.adobe.com/) voor [!UICONTROL Cloud Manager], zoals in de onderstaande afbeelding wordt getoond:

1. Meld u aan bij de beheerconsole en klik op **Nieuw profiel** om een nieuw profiel toe te voegen.

1. Vul de velden in om een nieuwe rol in te stellen voor [!UICONTROL Cloud Manager].

   Voer **Profielnaam** en **Weergavenaam** in om een nieuw profiel te maken. Bovendien kunt u een **machtigingsgroep** voor het profiel selecteren.

   Klik op **Gereed** om de stap voor het maken van het profiel te voltooien.

   >[!NOTE]
   >
   >Bij het maken van deze productprofielen moet de **weergavenaam** de technische waarde zijn die is gedefinieerd door [!UICONTROL Cloud Manager] (zie onderstaande tabel). De **profielnaam** kan om het even wat zijn, hoewel om verwarring te vermijden het wordt geadviseerd om de waarden in de *Aanbevolen kolom van de Naam* van het Profiel hieronder te gebruiken. Als u dit wilt doen, schakelt u bij het maken van het productprofiel de optie **Zelfde als profielnaam** uit en geeft u de bijbehorende waarde op als de **weergavenaam**.

   | **Rol** | **Weergavenaam (vereist)** | **Aanbevolen profielnaam** |
   |---|---|---|
   | Zakelijke eigenaar | CM_BUSINESS_OWNER_ROLE_PROFILE | [!UICONTROL Cloud Manager] - Rol bedrijfseigenaar |
   | Implementatiebeheer | CM_DEPLOYMENT_MANAGER_ROLE_PROFILE | [!UICONTROL Cloud Manager] - Implementatiebeheerrol |
   | Ontwikkelaar | CM_DEVELOPER_ROLE_PROFILE | [!UICONTROL Cloud Manager] - Rol voor ontwikkelaars |
   | Programmabeheerder | CM_PROGRAM_MANAGER_ROLE_PROFILE | [!UICONTROL Cloud Manager] - Rol van Program Manager |

1. Nadat u een productprofiel hebt gemaakt, kunt u gebruikers (of groepen) toevoegen aan productprofielen.


