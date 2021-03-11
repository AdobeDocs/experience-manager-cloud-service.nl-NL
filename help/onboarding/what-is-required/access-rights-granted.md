---
title: Toegangsrechten verleend - wat is vereist
description: Toegangsrechten verleend - wat is vereist
translation-type: tm+mt
source-git-commit: 4904d7728befd3562940b35c7d44dbf9cae87fee
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 10%

---


# Toegangsrechten verleend {#access-rights-granted}

Adobe zal een **Organisatie** herkenningsteken voor uw bedrijf in het Systeem van Adobe Identity Management (IMS) tot stand brengen, waar al uw gebruikers en hun toestemmingen kunnen worden beheerd. Elke gebruiker, die lid van deze organisatie moet zijn, en toegang tot om het even welke [!UICONTROL Experience Cloud] dienst zal worden verleend, zal zijn eigen **Adobe ID** moeten hebben.

## Typen gebruikersidentiteiten {#user-identity-types}

Als u aan de slag wilt gaan met een Adobe ID, gaat u naar [Adobe-identiteitstypen beheren](https://helpx.adobe.com/enterprise/using/identity.html) voor gedetailleerde instructies voor het verkrijgen van een Adobe ID met behulp van een van de beschikbare identiteitstypen.

## Gebruikers en rollen {#users-and-roles}

Zodra Adobe een organisatie voor uw bedrijf heeft gecreëerd, zal uw aangewezen beheerder als eerste lid aan deze organisatie worden toegevoegd. De beheerder krijgt standaard de beheerdersmachtigingen toegewezen en krijgt het [!UICONTROL AEM Managed Services]**-product** en een of meer [!UICONTROL Cloud Manager]**-productprofielen** toegewezen.

1. Zodra uw systeembeheerder u toegang tot de Manager van de Wolk verleent, zult u een e-mail ontvangen die u aan de login van de Manager van de Wolk neemt pagina die ook via [Adobe Experience Cloud](https://my.cloudmanager.adobe.com/) toegankelijk is.

1. Klik op **Toegang beheren** op de openingspagina van Cloud Manager.

   ![](/help/onboarding/getting-access-to-aem-in-cloud/assets/sys-admin5.png)

1. Nadat u op **Toegang beheren** hebt geklikt, gaat u naar **Admin Console** vanwaar u de gebruikersrollen of machtigingen kunt beheren in Cloud Manager.

   ![](/help/onboarding/getting-access-to-aem-in-cloud/assets/sys-admin1.png)

   Vanaf de Admin Console kunt u taken uitvoeren SysAdmin zoals:
   * [Rollen beheren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/navigation.html?lang=en#manage-roles)
   * [Toegang tot instantie Auteur beheren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/navigation.html?lang=en#manage-access-aem)

>[!NOTE]
>Ga naar de sectie [Gebruikers en rollen](#users-roles) voor meer informatie over gebruikers en roldefinities in Cloud Manager.

Als deze rechten zijn toegekend, is uw beheerder nu ingesteld met één aanmelding (met Adobe ID) voor toegang tot de [!UICONTROL Experience Cloud]-services, aanmelding bij uw AEM cloudomgevingen en gebruik [!UICONTROL Cloud Manager].

## Gebruikers en rollen {#users-roles}

Voor veel functies in [!UICONTROL Cloud Manager] zijn specifieke machtigingen vereist.

[!UICONTROL Cloud Manager] definieert momenteel vier rollen voor gebruikers die de beschikbaarheid van specifieke functies bepalen:

* Business Owner
* Program Manager
* Deployment Manager
* Developer

>[!CAUTION]
>
>Als u [!UICONTROL Cloud Manager] wilt gebruiken, hebt u een Adobe ID en de Adobe Experience Manager nodig als context van het Product van de Cloud Service.

### Roldefinities {#role-definitions}

>[!NOTE]
>
>De ontwikkelaar persona in Admin Console is niet gerelateerd aan de rol van de Ontwikkelaar in [!UICONTROL Cloud Manager].

De volgende tabel geeft een overzicht van de rollen:

| [!UICONTROL Cloud Manager] Rollen | Beschrijving |
|--- |--- |
| Zakelijke eigenaar | Verantwoordelijk voor het bepalen van KPIs, het goedkeuren van productieplaatsingen en het met voeten treden van belangrijke 3-tier mislukkingen. |
| Programmabeheerder | Gebruikt [!UICONTROL Cloud Manager] om teamopstelling uit te voeren, status te herzien en KPIs te bekijken. Kan belangrijke fouten met drie niveaus goedkeuren. |
| Implementatiebeheer | Beheert implementatiebewerkingen. Gebruikt [!UICONTROL Cloud Manager] om werkgebied/productie plaatsingen uit te voeren. Kan CI/CD pijpleidingen uitgeven. Kan belangrijke fouten met drie niveaus goedkeuren. Kan toegang krijgen tot de Git-opslagplaats. |
| Ontwikkelaar | Ontwikkelt en test aangepaste toepassingscode. Gebruikt hoofdzakelijk [!UICONTROL Cloud Manager] om status te bekijken. Kan toegang krijgen tot de Git-opslagplaats voor code commit. |
| Inhoudsauteur | Doorgaans heeft dit geen invloed op [!UICONTROL Cloud Manager]. Kan [!UICONTROL Cloud Manager] de Schakelaar van het Programma gebruiken (die van [!UICONTROL Experience Cloud]) is genavigeerd om tot AEM toegang te hebben. |

### Het profiel van het integratieproduct {#integration-product-profile}

Naast het bovenstaande maakt Cloud Manager automatisch een productprofiel met de naam &quot;Integrations - Cloud Service&quot;. Dit productprofiel wordt gebruikt voor de integratie tussen Adobe Experience Manager en andere Adobe-producten. Dit productprofiel **moet** niet worden geschrapt. Als u dit profiel per ongeluk verwijdert, moet het handmatig opnieuw worden gemaakt. De weergavenaam voor dit profiel **must** is `CM_CS_DEFAULT`.

