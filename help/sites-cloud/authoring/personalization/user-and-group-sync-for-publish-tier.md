---
title: 'Registratie, aanmelding en gebruikersprofiel '
description: Meer informatie over registratie, aanmelding en gebruikersprofiel op de publicatiereeks
translation-type: tm+mt
source-git-commit: 2c00c3723c3c84365044b5cd2fe6779de0360736
workflow-type: tm+mt
source-wordcount: '1164'
ht-degree: 0%

---


# Registratie, aanmelding en gebruikersprofiel {#registration-login-and-userprofile}

## Inleiding {#introduction}

Webtoepassingen bieden veelal functies voor accountbeheer waarmee eindgebruikers zich op een website kunnen registreren, waardoor hun gebruikersprofielgegevens behouden blijven, zodat zij zich in de toekomst kunnen aanmelden en een consistente ervaring kunnen opdoen. In dit artikel wordt beschreven:

* Registratie
* Aanmelden
* Gebruikersprofielgegevens opslaan
* Groepslidmaatschap
* Gegevenssynchronisatie

>[!IMPORTANT]
>
>De functionaliteit die in dit artikel wordt beschreven werkt alleen als de functie Gebruikersgegevens synchroniseren is ingeschakeld. Op dit moment is een verzoek aan de klantenondersteuning vereist waarin het juiste programma en de juiste omgevingen worden aangegeven. Als deze optie niet is ingeschakeld, worden de gebruikersgegevens slechts gedurende een korte periode (1 tot 24 uur) bewaard voordat ze worden verwijderd.

## Registratie {#registration}

Wanneer een eindgebruiker zich registreert voor een account in een AEM toepassing, wordt een gebruikersaccount gemaakt op de AEM-publicatieservice, zoals wordt weerspiegeld in een gebruikersbron onder `/home/users` in de JCR-opslagplaats.

Er zijn twee manieren om registratie uit te voeren, zoals hieronder beschreven.

### Beheerde AEM {#aem-managed-registration}

U kunt aangepaste registratiecode schrijven die minimaal de gebruikersnaam en het wachtwoord van de eindgebruiker nodig heeft en waarmee een gebruikersrecord wordt gemaakt in AEM die u tijdens de aanmelding kunt gebruiken voor verificatie. De volgende stappen worden doorgaans gebruikt om dit registratiemechanisme samen te stellen:

1. Een aangepaste AEM die registratiegegevens verzamelt weergeven
1. Bij verzending wordt een naar behoren ingericht servicegebruiker gebruikt voor
   1. Verifieer dat een bestaande gebruiker niet reeds bestaat, gebruikend één van de methodes `findAuthorizables()` van de GebruikerManager API
   1. Een gebruikersrecord maken met een van de methoden `createUser()` van de UserManager-API
   1. Alle profielgegevens die zijn vastgelegd met de methoden `setProperty()` van de machtigbare interface, behouden
1. Optionele stromen, zoals de verplichting voor de gebruiker om zijn e-mail te valideren.

### Extern {#external-managed-registration}

In sommige gevallen is de registratie of het creëren van gebruikers eerder gebeurd in infrastructuur buiten AEM. In dat scenario, wordt het gebruikersverslag gecreeerd in AEM tijdens login.

## Aanmelden {#login}

Zodra een eindgebruiker op de AEM publicatiedienst wordt geregistreerd, kunnen deze gebruikers login om voor authentiek verklaarde toegang (gebruikend AEM vergunningsmechanismen) en voortgezette, gebruiker-specifieke gegevens zoals profielgegevens te hebben.

## Implementatie {#implementation}

Aanmelding kan op de volgende twee manieren worden uitgevoerd:

### Beheerde AEM {#aem-managed-implementation}

Klanten kunnen hun eigen aangepaste componenten schrijven. Meer leren, overweeg vertrouwd worden met:

* [Sling Authentication Framework](https://sling.apache.org/documentation/the-sling-engine/authentication/authentication-framework.html)
* En denk na [het vragen van de AEM Communautaire Deskundigen zitting](http://bit.ly/ATACEFeb15) over login.

### Integratie met een identiteitsprovider {#integration-with-an-idp}

De klanten kunnen met een IdP (identiteitsleverancier) integreren, die de gebruiker voor authentiek verklaart. De technologieën van de integratie omvatten SAML en OAuth/SSO, zoals hieronder beschreven.

**SAML GEBASEERD**

De klanten kunnen op SAML-Gebaseerde authentificatie via hun aangewezen SAML IdP gebruiken. Wanneer het gebruiken van een IdP met AEM, is IdP verantwoordelijk voor het voor authentiek verklaren van de geloofsbrieven van de eindgebruiker en het tussenhandel drijven van de authentificatie van de gebruiker met AEM, die tot het gebruikersverslag in AEM zoals nodig leiden, en het groepslidmaatschap van de gebruiker in AEM, zoals die door de bewering van SAML wordt beschreven.

>[!NOTE]
>
>Alleen de initiële verificatie van de gebruikersgegevens wordt geverifieerd door de IdP en volgende aanvragen om AEM worden uitgevoerd met behulp van een AEM token, zolang het cookie beschikbaar is.

Zie documentatie voor meer informatie over [SAML 2.0 de Handler van de Authentificatie](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/saml-2-0-authenticationhandler.html?lang=en#saml-authentication-handler).

**OAuth/SSO**

Raadpleeg de [Single Sign On (SSO) documentatie](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/single-sign-on.html) voor informatie over het gebruik van AEM SSO Authentication Handler Service.

De `com.adobe.granite.auth.oauth.provider` interface kan met de leverancier OAuth van uw keus worden uitgevoerd.

### Vaste sessies en ingekapselde tokens {#sticky-sessions-and-encapsulated-tokens}

AEM als Cloud Service op cookie-gebaseerde kleverige toegelaten zittingen heeft, die ervoor zorgt dat een eindgebruiker aan het zelfde publicatieknooppunt op elk verzoek wordt verpletterd. Om de prestaties te verbeteren, wordt de ingekapselde symbolische eigenschap toegelaten door gebrek zodat te hoeven het gebruikersverslag in de bewaarplaats niet om op elke verzoek worden van verwijzingen voorzien. Als het publicatieknooppunt dat een eindgebruiker een affiniteit heeft om wordt vervangen, zal hun verslag van gebruikersidentificatie beschikbaar op het nieuwe publicatieknooppunt zijn, zoals die in de hieronder sectie van de gegevenssynchronisatie wordt beschreven.

## Gebruikersprofiel {#user-profile}

Afhankelijk van de aard van de gegevens zijn er verschillende benaderingen voor het aanhouden van gegevens.

### AEM opslagplaats {#aem-repository}

Gebruikersprofielgegevens kunnen op twee manieren worden geschreven en gelezen:

* Server-side gebruik met de interface `com.adobe.granite.security.user` Interface UserPropertiesManager, die gegevens onder de knoop van de gebruiker in `/home/users` zal plaatsen. Zorg ervoor dat de pagina&#39;s die per gebruiker uniek zijn niet in het voorgeheugen onder worden gebracht.
* Client-kant die ContextHub gebruiken, zoals die door [de documentatie](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/personalization/contexthub.html?lang=en#personalization) wordt beschreven.

### Gegevensopslag van derden {#third-party-data-stores}

Eindgebruikersgegevens kunnen naar externe leveranciers, zoals CRM&#39;s, worden verzonden en via API&#39;s worden opgehaald wanneer de gebruiker zich aanmeldt om AEM te maken en te blijven (of te vernieuwen) op het profielknooppunt van de AEM gebruiker en door AEM worden gebruikt.

Realtime toegang tot services van derden om profielkenmerken op te halen is mogelijk, maar het is belangrijk ervoor te zorgen dat dit de verwerking van verzoeken in AEM niet wezenlijk beïnvloedt.

## Machtigingen (gesloten gebruikersgroepen) {#permissions-closed-user-groups}

Beleid voor toegang op de publicatielaag, ook wel &#39;Closed User Group&#39; (CUG&#39;s) genoemd, wordt in de AEM gedefinieerd als [hier beschreven](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/cug.html?lang=en#applying-your-closed-user-group-to-content-pages). Om bepaalde secties of pagina&#39;s van een website van sommige gebruikers te beperken, pas CUGs toe zoals nodig gebruikend de AEM auteur, zoals hier beschreven, en herhaling hen aan de publicatielaag.

* Als de gebruikers login door met een identiteitsleverancier (IdP) het gebruiken van SAML voor authentiek te verklaren, zal de authentificatiemanager de groepslidmaatschappen van de gebruiker identificeren (die CUGs op publiceren rij zouden moeten aanpassen), en zal de vereniging tussen de gebruiker en de groep door een verslag van de bewaarplaats aanhouden
* Als login zonder de integratie wordt verwezenlijkt IdP, kan de douanecode de zelfde de structuurverhoudingen van de bewaarplaats toepassen.

Onafhankelijk van login, kan de douanecode ook het groepslidmaatschap van een gebruiker voortzetten en beheren zoals vereist door de unieke vereisten van een organisatie.

## Gegevenssynchronisatie {#data-synchronization}

Eindgebruikers van een website hebben een verwachting van een consistente ervaring op elk verzoek van een webpagina of zelfs wanneer ze zich aanmelden met een andere browser, zelfs als ze deze niet kennen, worden ze naar verschillende serverknooppunten van de infrastructuur van de publicatielaag gebracht. AEM als Cloud Service dit door de `/home` omslaghiërarchie (informatie van het gebruikersprofiel, groepslidmaatschap, enz.) over alle knopen van de publicatielaag snel te synchroniseren.

In tegenstelling tot andere AEM oplossingen, gebruikt de gebruiker en de synchronisatie van het groepslidmaatschap in AEM als Cloud Service geen punt aan punt overseinenbenadering, in plaats van het uitvoeren van een publish-subscribe benadering die klantenconfiguratie niet vereist.

>[!NOTE]
>
>Het gebruikersprofiel en de synchronisatie van het groepslidmaatschap zijn standaard niet ingeschakeld en de gegevens worden dus niet gesynchroniseerd met of zelfs niet permanent voortgezet op de publicatielaag. Om de functie in te schakelen, stuurt u een verzoek naar de Klantenondersteuning met vermelding van het juiste programma en de juiste omgevingen.

## Overwegingen {#cache-considerations} in cache opslaan

De voor authentiek verklaarde HTTP- verzoeken kunnen moeilijk zijn om op zowel CDN als Dispatcher in het voorgeheugen onder te brengen aangezien zij de mogelijkheid van gebruiker-specifieke staat dragen die als deel van de reactie van het verzoek wordt overgebracht. Als geverifieerde verzoeken per ongeluk in de cache worden geplaatst en aan andere browsers worden aangeboden, kan dit leiden tot onjuiste ervaringen of zelfs tot het lekken van beveiligde of gebruikersgegevens.

De benaderingen voor het handhaven van hoge geheim voorgeheugen-capaciteit van verzoeken terwijl het steunen van gebruiker-specifieke reacties omvatten:

* AEM Verzendmachtigingen gevoelige caching
* Dynamisch afspelen opnemen
* AEM ContextHub