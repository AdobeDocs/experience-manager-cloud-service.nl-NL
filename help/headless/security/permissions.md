---
title: Bevoegdheidsoverwegingen voor inhoud zonder kop
description: Leer over verschillende toestemmings en ACL overwegingen voor een headless implementatie met Adobe Experience Manager. Begrijp de verschillende persona's en de potentiële toestemmingsniveaus nodig voor zowel auteur als milieu Publish.
feature: Headless, Content Fragments,GraphQL API
exl-id: 3fbee755-2fa4-471b-83fc-3f4bf056267a
role: Admin, Developer
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '811'
ht-degree: 0%

---

# Bevoegdheidsoverwegingen voor inhoud zonder kop

Met een implementatie zonder kop zijn er verschillende gebieden met beveiliging en machtigingen die moeten worden aangepakt. Machtigingen en personen kunnen globaal worden overwogen op basis van de AEM omgeving **Auteur** of **Publiceren**. Elke omgeving bevat verschillende personen en met verschillende behoeften.

## Overwegingen bij de auteurservice

In de service Auteur kunnen interne gebruikers inhoud maken, beheren en publiceren. Machtigingen draaien rond de verschillende personen die inhoud beheren.

### Rechten beheren op groepsniveau

Als beste praktijken, zouden de toestemmingen op Groepen in AEM moeten worden geplaatst. Deze groepen, die ook als lokale groepen worden bekend, kunnen binnen het AEM auteursmilieu worden beheerd.

De eenvoudigste manier om groepslidmaatschap te beheren is om Adobe Identity Management System (IMS)-groepen te gebruiken en toe te wijzen [IMS-groepen naar lokale AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/security/ims-support.html#managing-permissions-in-aem).

![Toestemmingsstroom beheerconsole](assets/admin-console-aem-group-permissions.png)

Op hoog niveau is het proces:

1. IMS-gebruikers toevoegen aan een nieuwe of bestaande IMS-gebruikersgroep met de opdracht [Admin Console](https://adminconsole.adobe.com/)
1. IMS-groepen worden gesynchroniseerd met AEM wanneer gebruikers zich aanmelden.
1. Wijs IMS-groepen toe aan AEM groepen.
1. Machtigingen instellen voor AEM groepen.
1. Wanneer gebruikers zich aanmelden bij AEM en via IMS worden geverifieerd, nemen ze de machtigingen van de AEM groep over.

>[!TIP]
>
> Een gedetailleerde videoanalyse van het beheren van IMS en AEM gebruikers en groepen is te vinden [hier](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/overview.html).

Om te beheren **groepen** in AEM, navigeer naar **Gereedschappen** > **Beveiliging** > **Groepen**.

Navigeer naar om machtigingen van groepen in AEM te beheren **Gereedschappen** > **Beveiliging** > **Machtigingen**.

### DAM-gebruikers

&quot;DAM&quot; staat in dit verband voor Digital Asset Management. De **DAM-gebruikers** is een out van de kadergroep in AEM die voor &quot;alledaagse&quot;gebruikers kan worden gebruikt die digitale activa en de Fragments van de Inhoud beheren. Deze groep biedt machtigingen voor **weergave**, **toevoegen**, **update**, **delete**, en **publish** Content Fragments en alle andere bestanden in AEM Assets.

Als u IMS gebruikt voor groepslidmaatschap, voegt u de juiste IMS-groepen toe als leden van de **DAM-gebruikers** groep. Leden van de IMS-groep nemen de machtigingen van de groep DAM-gebruikers over wanneer ze zich aanmelden bij de AEM.

#### DAM-gebruikersgroep aanpassen

Het is beter om toestemmingen van een uit de bakgroep direct niet te wijzigen. In plaats daarvan kunt u ook uw eigen groep(en) maken die na de **DAM-gebruikers** groepsmachtigingen en beperken de toegang tot verschillende **mappen** in AEM Assets.

Voor meer granulaire machtigingen gebruikt u de optie **Machtigingen** console in AEM en werk het pad bij vanuit `/content/dam` naar een meer specifiek pad, dat wil zeggen: `/content/dam/mycontentfragments`.

Het kan wenselijk zijn om deze groep gebruikers toestemmingen te geven om inhoudsfragmenten tot stand te brengen en uit te geven maar niet te schrappen. Zie voor het controleren en toewijzen van machtigingen voor bewerken, maar niet verwijderen [Inhoudsfragmenten - Overwegingen verwijderen](/help/sites-cloud/administering/content-fragments/delete-considerations.md).

### Modeleditors

De mogelijkheid om te wijzigen **Modellen van inhoudsfragmenten** moet worden overgelaten aan beheerders of een **kleine groep** van gebruikers met verhoogde toestemmingen. Als u het model van het inhoudsfragment wijzigt, heeft dit veel downstreameffecten.

>[!CAUTION]
>
>Wijzigingen in modellen van inhoudsfragmenten veranderen de onderliggende GraphQL API waarop toepassingen zonder kop vertrouwen.

Als u een groep wilt creëren die de Modellen van het Fragment van de Inhoud maar niet volledige beheerderstoegang beheert, kunt u een groep met de volgende ingangen van de toegangscontrole tot stand brengen:

| Pad | Machtiging | Rechten |
|-----| -------------| ---------|
| `/conf` | **toestaan** | `jcr:read` |
| `/conf/<config-name>/settings/dam/cfm` | **toestaan** | `rep:write`, `crx:replicate` |

## Publish-servicerechten

De Publish-service wordt beschouwd als de &quot;live&quot;-omgeving en is doorgaans de interactie tussen GraphQL API-gebruikers en andere gebruikers. Inhoud wordt na bewerking en goedkeuring op de service Auteur gepubliceerd naar de Publish-service. De toepassing zonder koppen gebruikt vervolgens de goedgekeurde inhoud van de Publish-service via GraphQL API&#39;s.

Standaard is inhoud die via de GraphQL-eindpunten van AEM Publish-service wordt weergegeven, toegankelijk voor iedereen, inclusief niet-geverifieerde gebruikers.

### Machtigingen voor inhoud

Inhoud die via AEM GraphQL API&#39;s beschikbaar wordt gemaakt, kan worden beperkt met [Gesloten gebruikersgroepen (CUG&#39;s)](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/advanced/closed-user-groups.html) Stel deze in op mappen met elementen, waarin wordt aangegeven welke AEM Gebruikersgroepen (en hun leden) toegang hebben tot de inhoud van de mappen Middelen.

CUG&#39;s met middelen werken op:

* Eerst, ontken al toegang tot de omslag en subfolders
* Dan, die leestoegang tot de omslag en subfolders voor alle AEM Gebruikersgroepen verlenen die in de lijst van KUGs worden vermeld

CUG&#39;s kunnen worden ingesteld in middelenmappen die inhoud bevatten die via GraphQL API&#39;s beschikbaar wordt gemaakt. De toegang tot de omslagen van activa op AEM Publish zou via Gebruikersgroepen, eerder dan gebruiker direct moeten worden gecontroleerd. Maak (of hergebruik) een AEM gebruikersgroep die toegang verleent tot mappen met elementen die inhoud bevatten die door GraphQL API&#39;s beschikbaar is gemaakt.

#### Het verificatieschema selecteren{#publish-permissions-users}

De [AEM headless SDK](https://github.com/adobe/aem-headless-client-js#create-aemheadless-client) ondersteunt twee typen verificatie:

* [Op token gebaseerde verificatie](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) het gebruiken van de dienstgeloofsbrieven verbindend aan één enkele technische rekening.
* Standaardverificatie met AEM gebruikers.

### De GraphQL API openen

HTTP-aanvragen die de [juiste verificatiereferenties](https://github.com/adobe/aem-headless-client-js#create-aemheadless-client) op de GraphQL API-eindpunten van de AEM Publish-service vindt u inhoud die de referenties mogen lezen en die anoniem toegankelijk is. Andere gebruikers van de GraphQL API kunnen de inhoud in de door CUG&#39;s beveiligde mappen niet lezen.
