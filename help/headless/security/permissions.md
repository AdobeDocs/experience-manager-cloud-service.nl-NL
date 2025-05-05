---
title: Bevoegdheidsoverwegingen voor inhoud zonder kop
description: Leer over verschillende toestemmings en ACL overwegingen voor een headless implementatie met Adobe Experience Manager. Begrijp de verschillende persona's en de potentiële toestemmingsniveaus nodig voor zowel auteur als milieu Publish.
feature: Headless, Content Fragments,GraphQL API
exl-id: 3fbee755-2fa4-471b-83fc-3f4bf056267a
role: Admin, Developer
source-git-commit: 6719e0bcaa175081faa8ddf6803314bc478099d7
workflow-type: tm+mt
source-wordcount: '817'
ht-degree: 0%

---

# Bevoegdheidsoverwegingen voor inhoud zonder kop

Met een implementatie zonder kop zijn er verschillende gebieden met beveiliging en machtigingen die moeten worden aangepakt. De toestemmingen en de personen kunnen globaal worden overwogen gebaseerd op het AEM milieu **Auteur** of **Publish**. Elke omgeving bevat verschillende personen en met verschillende behoeften.

## Overwegingen bij de auteurservice

In de service Auteur kunnen interne gebruikers inhoud maken, beheren en publiceren. Machtigingen draaien rond de verschillende personen die inhoud beheren.

### Rechten beheren op groepsniveau

Als beste praktijken, zouden de toestemmingen op Groepen in AEM moeten worden geplaatst. Deze groepen, die ook als lokale groepen worden bekend, kunnen binnen het AEM auteursmilieu worden beheerd.

De gemakkelijkste manier om groepslidmaatschap te beheren is de groepen van het Systeem van Identity Management van de Adobe (IMS) te gebruiken en [ groepen IMS aan lokale AEM ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/security/ims-support.html?lang=nl-NL#managing-permissions-in-aem) toe te wijzen.

![ stroom van de de consoletoestemming Admin ](assets/admin-console-aem-group-permissions.png)

Op hoog niveau is het proces:

1. Voeg Gebruikers IMS aan een nieuwe of bestaande IMS Gebruikersgroep toe gebruikend de [ Admin Console ](https://adminconsole.adobe.com/)
1. IMS-groepen worden gesynchroniseerd met AEM wanneer gebruikers zich aanmelden.
1. Wijs IMS-groepen toe aan AEM groepen.
1. Machtigingen instellen voor AEM groepen.
1. Wanneer gebruikers zich aanmelden bij AEM en via IMS worden geverifieerd, nemen ze de machtigingen van de AEM groep over.

>[!TIP]
>
>Voor een gedetailleerde videoanalyse van het beheren van IMS en AEM gebruikers en groepen zie [ het Vormen toegang tot AEM as a Cloud Service ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/overview.html?lang=nl-NL).

Om **groepen** in AEM te beheren, navigeer aan **Hulpmiddelen** > **Veiligheid** > **Groepen**.

Om toestemmingen van groepen in AEM te beheren, navigeer aan **Hulpmiddelen** > **Veiligheid** > **Toestemmingen**.

### DAM-gebruikers

&quot;DAM&quot; staat in dit verband voor Digital Asset Management. De **Gebruikers DAM** is een uit de doosgroep in AEM die voor &quot;alledaagse&quot;gebruikers kan worden gebruikt die digitale activa en de Fragmenten van de Inhoud beheren. Deze groep verstrekt toestemmingen aan **mening**, **&#x200B;**&#x200B;toevoegen, **update**, **schrapt**, en **publiceert** de Fragmenten van de Inhoud en alle andere dossiers in AEM Assets.

Als het gebruiken van IMS voor groepslidmaatschap, voeg de aangewezen groepen IMS als leden van de **DAM Gebruikers** groep toe. Leden van de IMS-groep nemen de machtigingen van de groep DAM-gebruikers over wanneer ze zich aanmelden bij de AEM.

#### DAM-gebruikersgroep aanpassen

Het is beter om toestemmingen van een uit de bakgroep direct niet te wijzigen. In plaats daarvan, kunt u uw eigen groep(en) ook tot stand brengen die na de **DAM gebruikers** groepstoestemmingen wordt gemodelleerd en toegang tot verschillende **omslagen** binnen AEM Assets verder beperken.

Voor meer korrelige toestemmingen gebruikt de **console van Toestemmingen** in AEM en werkt de weg van `/content/dam` aan een specifieker weg bij, namelijk `/content/dam/mycontentfragments`.

Het kan wenselijk zijn om deze groep gebruikers toestemmingen te geven om inhoudsfragmenten tot stand te brengen en uit te geven maar niet te schrappen. Om toestemmingen voor uit te geven te herzien en toe te wijzen, maar niet te schrappen zie [ de Fragmenten van de Inhoud - de Overwegingen van de Schrapping ](/help/sites-cloud/administering/content-fragments/delete-considerations.md).

### Modeleditors

De capaciteit om **Modellen van het Fragment van de Inhoud te wijzigen** zou aan beheerders of a **kleine groep** van gebruikers met opgeheven toestemmingen moeten worden verlaten. Als u het model van het inhoudsfragment wijzigt, heeft dit veel downstreameffecten.

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

Inhoud die via AEM GraphQL APIs wordt blootgesteld kan worden beperkt gebruikend [ Gesloten Groepen van de Gebruiker (CUGs) ](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/advanced/closed-user-groups.html?lang=nl-NL) geplaatst op activa omslagen, die specificeren welke AEM Gebruikersgroepen (en hun leden) tot de inhoud van de omslagen van Assets kunnen toegang hebben.

Assets CUG&#39;s werken door:

* Eerst, ontken al toegang tot de omslag en subfolders
* Dan, die leestoegang tot de omslag en subfolders voor alle AEM Gebruikersgroepen verlenen die in de lijst van KUGs worden vermeld

CUG&#39;s kunnen worden ingesteld in middelenmappen die inhoud bevatten die via GraphQL API&#39;s beschikbaar wordt gemaakt. De toegang tot de omslagen van activa op AEM Publish zou via Gebruikersgroepen, eerder dan gebruiker direct moeten worden gecontroleerd. Maak (of hergebruik) een AEM gebruikersgroep die toegang verleent tot mappen met elementen die inhoud bevatten die door GraphQL API&#39;s beschikbaar is gemaakt.

#### Het verificatieschema selecteren{#publish-permissions-users}

[ AEM Koploze SDK ](https://github.com/adobe/aem-headless-client-js#create-aemheadless-client) steunt twee types van authentificatie:

* [ Symbolische gebaseerde authentificatie ](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) die de dienstgeloofsbrieven gebruiken die aan één enkele technische rekening worden gebonden.
* Standaardverificatie met AEM gebruikers.

### De GraphQL API openen

De verzoeken van HTTP die de [ aangewezen authentificatiegeloofsbrieven ](https://github.com/adobe/aem-headless-client-js#create-aemheadless-client) verstrekken aan de eindpunten van GraphQL API van de dienst van AEM Publish omvatten inhoud de geloofsbrieven worden gemachtigd om te lezen, en anonymously toegankelijke inhoud. Andere gebruikers van de GraphQL API kunnen de inhoud in de door CUG&#39;s beveiligde mappen niet lezen.
