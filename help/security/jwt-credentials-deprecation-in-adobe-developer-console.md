---
title: JWT Credentials Deprection in Adobe Developer Console
description: Meer informatie over de impact van afschrijving van JWT-referenties in Adobe Developer Console op AEM.
exl-id: 7c811081-484c-41f7-a289-4e9a10a837b3
feature: Security
role: Admin
source-git-commit: d3c00c33925a23ad5b1080c1e864cfdb5a8d1c1b
workflow-type: tm+mt
source-wordcount: '769'
ht-degree: 0%

---

# JWT Credentials Deprection in Adobe Developer Console {#jwt-credentials-deprecation-in-adobe-developer-console}

>[!NOTE]
>
>AEM 6.5 klanten zouden [ de vergelijkbare documentatie voor AEM 6.5 ](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/security/jwt-credentials-deprecation-in-adobe-developer-console) voor meer informatie moeten van verwijzingen voorzien.

De klanten van de Adobe gebruiken [ Adobe Developer Console ](https://developer.adobe.com/console) om geloofsbrieven te produceren die toegang tot diverse APIs toelaten. Klanten kiezen uit verschillende soorten referentie, variërend van OAuth Server-to-Server tot Single-Page App. Één van die credentietypes, de geloofsbrieven van de Rekening van de Dienst (JWT), is afgekeurd ten gunste van de geloofsbrieven van Server-aan-Server OAuth. De nieuwe geloofsbrieven van de Rekening van de Dienst (JWT) kunnen niet op of na 3 juni 2024 worden gecreeerd, en de bestaande geloofsbrieven van JWT zullen niet aan of na 27 jan. 2025 werken. U kunt [ lezen over de veroudering ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/).

Dit artikel bevat een extra context voor de manier waarop AEM as a Cloud Service de afleiding moet verwerken.

Het belangrijkste voordeel is dat AEM nu de nieuwe OAuth Server-to-Server geloofsbrieven voor AEM as a Cloud Service steunt. Mogelijk hebt u een e-mail ontvangen met instructies voor het migreren van uw JWT-gegevens. Deze migratie kan nu worden uitgevoerd.

In de volgende secties worden de scenario&#39;s weergegeven waarin klanten hun JWT-referenties (Service Account) moeten vervangen door OAuth Server-to-Server-referenties, nu AEM hen ondersteunt. [ las hoe ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#migration-overview) om de geloofsbrieven te migreren.

>[!NOTE]
>
>[**AEM** Developer Console ](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console) (neem nota van **AEM** in de naam, die het van **Adobe** Developer Console) onderscheidt verstrekt een nut om [ tokens te produceren JWT ](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) die voor server-aan-server APIs worden gebruikt. Deze gegevens zijn niet afgekeurd en kunnen ook in de toekomst worden gebruikt.

## AEM integreren met andere oplossingen voor Adobe {#integrating-aem-with-other-adobe-solutions}

**Actie**: Migreer uw configuratie aangezien AEM nu geloofsbrieven OAuth steunt.

**Relevante AEM versies**: AEM as a Cloud Service

AEM klanten gebruiken AEM om integratie met vele andere oplossingen van de Adobe te vormen. Bijvoorbeeld Adobe Target, Adobe Analytics en andere.

Zie {de Integraties IMS van de Opstelling voor AEM as a Cloud Service ](/help/security/setting-up-ims-integrations-for-aem-as-a-cloud-service.md) voor details van hoe te:[

* configuraties maken met OAuth-gebruikersgegevens
* migreer configuraties, die met geloofsbrieven JWT werden gecreeerd, om geloofsbrieven te gebruiken OAuth

## Cloud Manager API&#39;s {#cloud-manager-apis}

**Actie**: Migreer uw geloofsbrieven van JWT aan OAuth geloofsbrieven, die Cloud Manager nu steunt.

**Relevante AEM versies**: AEM as a Cloud Service

De klanten creëren de projecten van Adobe Developer Console zodat kunnen zij [ Cloud Manager APIs ](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/) aanhalen. De geloofsbrieven in het project van Adobe Developer zouden aan het server-aan-Server referentie type OAuth moeten worden gemigreerd alvorens de afgekeurde geloofsbrieven JWT in Januari 2025 verlopen.

## Automatisch gegenereerde projecten {#autogen-projects}

**Actie**: Migreer niet omdat de Adobe namens u gaat migreren.

**Relevante AEM versies**: AEM as a Cloud Service.

Als Cloud Manager AEM as a Cloud Service-omgevingen aanbiedt, wordt automatisch een Adobe Developer Console-project met JWT-referenties gegenereerd. Dit project is gemarkeerd als alleen-lezen, zoals in de onderstaande schermafbeelding wordt geïllustreerd. De klanten kunnen en zouden niet moeten proberen om deze projecten aan OAuth server-aan-Server geloofsbrieven te migreren. In plaats daarvan, zal de Adobe deze projecten op zich migreren, alvorens de geloofsbrieven niet meer bruikbaar zijn.

![ auto-geproduceerde projecten ](/help/security/assets/jwt-deprecation-autogen-projects.png)

## Veelgestelde vragen over automatisch gegenereerde projecten {#autogen-projects-faqs}

Deze sectie verstrekt antwoorden op de vaakst gestelde vragen over JWT geloofsvervanging voor auto-geproduceerde projecten in AEM as a Cloud Service.

**hoe ik doe welke projecten auto-geproduceerd zijn?**
Navigeren naar de Adobe Developer Console | Sectie Projecten.  Automatisch gegenereerde AEM as a Cloud Service-projecten krijgen een vergrendelingspictogram met de id &#39;Automatisch gegenereerd&#39;.  Automatisch gegenereerde projecten volgen de indeling AEM-p#####-e####### en worden gemaakt door de gebruiker van een technische account.

<img width="439" alt="image" src="https://git.corp.adobe.com/storage/user/16149/files/6b20a8a3-3711-4741-8f2c-ec5e36fe97cc">


**wat als wij kwesties met onze auto-geproduceerde projecten ontmoeten?**

De Zorg van de Klant van de Adobe van het contact ](https://helpx.adobe.com/ca/enterprise/using/support-for-experience-cloud.html).[

**zou ik vooruit moeten gaan en onze auto-geproduceerde projecten migreren?**

Er is geen actie vereist omdat Adobe automatisch gegenereerde gegevens voor uw rekening migreert voor omgevingen met AEM versie 17258 (aug &#39;24) en hoger.

**wat zijn de chronologie voor migratie van auto-geproduceerde projecten?**

Adobe zal in het eerste kwartaal van 2025 een gefaseerde migratiebenadering op gang brengen, te beginnen met ontwikkelomgevingen.

**hoe zal onze instantie van AEM as a Cloud Service worden beïnvloed als wij een AEM versie hebben die ouder is dan AEM Versie 17258 (aug &quot;24)?**

Automatisch gegenereerde projectintegratie werkt niet meer als ze in juni 2025 niet naar OAuth worden gemigreerd.

Om een vlotte overgang te verzekeren zouden de klanten ](https://helpx.adobe.com/ca/enterprise/using/support-for-experience-cloud.html) de Zorg van de Klant van de Adobe moeten contacteren [ en met het proces beginnen om aan de [ recentste AEM Versie ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/maintenance/latest) bij te werken. Dit zal voldoende tijd bieden voor regressietests en Adobe in staat stellen de migratie van projecten efficiënt te beheren.

**kan ik aan een gesteunde versie OAuth bevorderen zonder mijn Versie van AEM as a Cloud Service AEM te bevorderen?**

Nee. Om een vlotte overgang te verzekeren zouden de klanten ](https://helpx.adobe.com/ca/enterprise/using/support-for-experience-cloud.html) de Zorg van de Klant van de Adobe moeten contacteren [ en met het proces beginnen om aan de [ recentste AEM Versie ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/maintenance/latest) bij te werken. Dit zal voldoende tijd bieden voor regressietests en Adobe in staat stellen de migratie van projecten efficiënt te beheren.
