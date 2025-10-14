---
title: Registratie, aanmelding en gebruikersprofiel
description: Meer informatie over registratie, aanmelding, gebruikersgegevens en groepssynchronisatie voor AEM as a Cloud Service
exl-id: a991e710-a974-419f-8709-ad86c333dbf8
solution: Experience Manager Sites
feature: Authoring, Personalization
role: User
source-git-commit: 6719e0bcaa175081faa8ddf6803314bc478099d7
workflow-type: tm+mt
source-wordcount: '1343'
ht-degree: 0%

---

# Registratie, aanmelding en gebruikersprofiel {#registration-login-and-userprofile}

## Inleiding {#introduction}

Webtoepassingen bieden veelal functies voor accountbeheer waarmee eindgebruikers zich op een website kunnen registreren, waardoor hun gegevens over gebruikersgegevens behouden blijven. Hierdoor kunnen eindgebruikers zich in de toekomst aanmelden en genieten van een consistente ervaring. In dit artikel worden de volgende concepten voor AEM as a Cloud Service beschreven:

* Registratie
* Aanmelden
* Gebruikersprofielgegevens opslaan
* Groepslidmaatschap
* Gegevenssynchronisatie

## Registratie {#registration}

Wanneer een eindgebruiker zich registreert voor een account in een AEM toepassing, wordt een gebruikersaccount gemaakt op de AEM Publish-service, zoals wordt weerspiegeld in een gebruikersbron onder `/home/users` in de JCR-opslagplaats.

Er zijn twee manieren om registratie uit te voeren, zoals hieronder beschreven.

### AEM Beheerd {#aem-managed-registration}

U kunt aangepaste registratiecode schrijven die minimaal de gebruikersnaam en het wachtwoord van de gebruiker nodig heeft en een gebruikersrecord maakt in AEM die u tijdens de aanmelding kunt gebruiken voor verificatie. De volgende stappen worden doorgaans gebruikt om dit registratiemechanisme samen te stellen:

1. Een aangepaste AEM die registratiegegevens verzamelt weergeven
1. Bij verzending wordt een naar behoren ingericht servicegebruiker gebruikt voor
   1. Controleer of een bestaande gebruiker nog niet bestaat. Gebruik hiervoor een van de `findAuthorizables()` -methoden van de UserManager-API
   1. Een gebruikersrecord maken met een van de `createUser()` -methoden van de UserManager-API
   1. Alle profielgegevens die zijn vastgelegd met de methoden `setProperty()` van de machtigbare interface, behouden
1. Optionele stromen, zoals de verplichting voor de gebruiker om zijn e-mail te valideren.

**Vereiste:**

Voor de hierboven beschreven logica om correct te functioneren, gelieve [&#x200B; gegevenssynchronisatie &#x200B;](#data-synchronization-data-synchronization) toe te laten door voor te leggen
een verzoek aan de Klantenondersteuning met vermelding van het juiste programma en de juiste omgevingen.

### Extern {#external-managed-registration}

In sommige gevallen is de registratie of het creëren van gebruikers eerder gebeurd in infrastructuur buiten AEM. In dat scenario, wordt het gebruikersverslag gecreeerd in AEM tijdens login.

## Aanmelden {#login}

Zodra een eindgebruiker op de dienst van AEM Publish wordt geregistreerd, kunnen deze gebruikers login om voor authentiek verklaarde toegang (gebruikend AEM vergunningsmechanismen) en voortgezette, gebruiker-specifieke gegevens zoals profielgegevens te hebben.

## Implementatie {#implementation}

Aanmelding kan op de volgende twee manieren worden uitgevoerd:

### AEM Beheerd {#aem-managed-implementation}

Klanten kunnen hun eigen aangepaste componenten schrijven. Meer leren, overweeg vertrouwd worden met:

* Het [&#x200B; Sling Kader van de Authentificatie &#x200B;](https://sling.apache.org/documentation/the-sling-engine/authentication/authentication-framework.html)
* En overweeg [&#x200B; vragend de AEM Communautaire zitting van Deskundigen &#x200B;](https://bit.ly/ATACEFeb15) over login.

**Vereiste:**

Voor de hierboven beschreven logica om correct te functioneren, gelieve [&#x200B; gegevenssynchronisatie &#x200B;](#data-synchronization-data-synchronization) toe te laten door voor te leggen
een verzoek aan de Klantenondersteuning met vermelding van het juiste programma en de juiste omgevingen.

### Integratie met een identiteitsprovider {#integration-with-an-idp}

De klanten kunnen met een IdP (identiteitsleverancier) integreren, die de gebruiker voor authentiek verklaart. De technologieën van de integratie omvatten SAML en OAuth/SSO, zoals hieronder beschreven.

**GEBASEERDE SAML**

De klanten kunnen op SAML-Gebaseerde authentificatie via hun aangewezen SAML IdP gebruiken. Wanneer het gebruiken van een IdP met AEM, is IdP verantwoordelijk voor het voor authentiek verklaren van de geloofsbrieven van de gebruiker en het tussenhandel drijven van de authentificatie van de gebruiker met AEM, die tot het gebruikersverslag in AEM zoals nodig leiden, en het groepslidmaatschap van de gebruiker in AEM, zoals die door de bewering van SAML wordt beschreven.

>[!NOTE]
>
>Alleen de initiële verificatie van de gebruikersgegevens wordt geverifieerd door de IdP en volgende aanvragen om AEM worden uitgevoerd met behulp van een AEM token, zolang het cookie beschikbaar is.

Zie documentatie voor meer informatie over [&#x200B; SAML 2.0 de Handler van de Authentificatie &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/authentication/saml-2-0.html?lang=nl-NL).

**OAuth/SSO**

Zie het [&#x200B; Enige Ondertekenen (SSO) documentatie &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/single-sign-on.html?lang=nl-NL) voor informatie over het gebruiken van de AEMDienst van de Handler van de Authentificatie SSO.

De interface `com.adobe.granite.auth.oauth.provider` kan met de leverancier OAuth van uw keus worden uitgevoerd.

**Vereiste:**

Als beste praktijken, baseer altijd op idP (de Leverancier van de Identiteit) als één enkel punt van waarheid wanneer het opslaan van gebruiker-specifieke gegevens. Als de extra gebruikersinformatie in de lokale bewaarplaats wordt opgeslagen, die geen deel van idP uitmaakt, gelieve [&#x200B; gegevenssynchronisatie &#x200B;](#data-synchronization-data-synchronization) toe te laten door een verzoek aan de Steun van de Klant voor te leggen die op het aangewezen programma en de milieu&#39;s wijst. Naast [&#x200B; gegevenssynchronisatie &#x200B;](#data-synchronization-data-synchronization), in het geval van de de authentificatieleverancier van SAML, zorg ervoor dat [&#x200B; dynamisch groepslidmaatschap &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-learn/cloud-service/authentication/saml-2-0) wordt toegelaten.

### Vaste sessies en ingekapselde tokens {#sticky-sessions-and-encapsulated-tokens}

AEM as a Cloud Service maakt op cookies gebaseerde sticky-sessies mogelijk, zodat een eindgebruiker op elke aanvraag naar hetzelfde publicatieknooppunt wordt gerouteerd. In bepaalde gevallen, zoals gebruikersverkeersspikes, zou de ingekapselde symbolische eigenschap prestaties kunnen verhogen zodat het gebruikersverslag in de bewaarplaats te hoeven niet om op elke aanvraag worden van verwijzingen voorzien. Als publiceer knoop waaraan een eindgebruiker een affiniteit heeft wordt vervangen, is hun verslag van gebruikersidentiteitskaart beschikbaar op nieuw publiceer knoop, zoals die in de [&#x200B; hieronder beschreven gegevenssynchronisatie &#x200B;](#data-synchronization-data-synchronization) sectie wordt beschreven.

Als u de ingekapselde tokenfunctie wilt gebruiken, dient u bij de Klantenondersteuning een aanvraag in waarin het juiste programma en de juiste omgevingen worden vermeld. Nog belangrijker, kan het ingekapselde teken niet zonder [&#x200B; gegevenssynchronisatie &#x200B;](#data-synchronization-data-synchronization) worden toegelaten en moet samen worden toegelaten. Controleer daarom zorgvuldig het gebruiksgeval voordat u de functie inschakelt en zorg ervoor dat deze essentieel is.

## Gebruikersprofiel {#user-profile}

Afhankelijk van de aard van de gegevens zijn er verschillende benaderingen voor het aanhouden van gegevens.

### AEM {#aem-repository}

Gebruikersprofielgegevens kunnen op twee manieren worden geschreven en gelezen:

* Gebruik op de server met de interface `com.adobe.granite.security.user` Interface UserPropertiesManager, die gegevens onder het knooppunt van de gebruiker in `/home/users` plaatst. Zorg ervoor dat de pagina&#39;s die per gebruiker uniek zijn niet in het voorgeheugen onder worden gebracht.
* Cliënt-kant die ContextHub gebruiken, zoals die door [&#x200B; wordt beschreven de documentatie &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/personalization/contexthub.html?lang=nl-NL#personalization).

**Vereiste:**

Voor de server-zijlogica van het gebruikersprofiel persistentie om correct te functioneren, gelieve [&#x200B; gegevenssynchronisatie &#x200B;](#data-synchronization-data-synchronization) toe te laten door voor te leggen
een verzoek aan de Klantenondersteuning met vermelding van het juiste programma en de juiste omgevingen.

### Gegevensopslag van derden {#third-party-data-stores}

Eindgebruikersgegevens kunnen naar externe leveranciers, zoals CRM&#39;s, worden verzonden en via API&#39;s worden opgehaald wanneer de gebruiker zich aanmeldt om AEM te maken en te blijven (of te vernieuwen) op het profielknooppunt van de AEM gebruiker en door AEM worden gebruikt.

Realtime toegang tot derdediensten om profielattributen terug te winnen is mogelijk, echter, is het belangrijk om ervoor te zorgen dit verzoekverwerking in AEM niet wezenlijk beïnvloedt.

**Vereiste:**

Voor de hierboven beschreven logica om correct te functioneren, gelieve [&#x200B; gegevenssynchronisatie &#x200B;](#data-synchronization-data-synchronization) toe te laten door voor te leggen
een verzoek aan de Klantenondersteuning met vermelding van het juiste programma en de juiste omgevingen.

## Machtigingen (gesloten gebruikersgroepen) {#permissions-closed-user-groups}

Publish-rij toegangsbeleid, ook genoemd Gesloten Gebruikersgroepen (CUGs), wordt bepaald in de AEM auteur, zie [&#x200B; Creërend een Gesloten Groep van de Gebruiker &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/cug.html?lang=nl-NL#applying-your-closed-user-group-to-content-pages). Als u bepaalde gedeelten of pagina&#39;s van een website van bepaalde gebruikers wilt beperken, past u de CUG&#39;s waar nodig toe met de auteur van de AEM, zoals hier beschreven. U kopieert deze secties of pagina&#39;s vervolgens naar de publicatielijst.

* Als de gebruikers login door met een identiteitsleverancier (IdP) het gebruiken van SAML voor authentiek te verklaren, zal de authentificatiemanager de groepslidmaatschappen van de gebruiker identificeren (die CUGs op publiceren rij zouden moeten aanpassen), en zal de vereniging tussen de gebruiker en de groep door een verslag van de bewaarplaats aanhouden
* Als login zonder integratie IdP wordt verwezenlijkt, kan de douanecode de zelfde de structuurverhoudingen van de bewaarplaats toepassen.

Onafhankelijk van login, kan de douanecode ook het groepslidmaatschap van een gebruiker voortzetten en beheren zoals vereist door de unieke vereisten van een organisatie.

## Gegevenssynchronisatie {#data-synchronization}

Eindgebruikers van een website hebben een verwachting van een consistente ervaring op elk verzoek van een webpagina of zelfs wanneer ze zich aanmelden met een andere browser, zelfs als ze deze niet kennen, worden ze naar verschillende serverknooppunten van de infrastructuur van de publicatielaag gebracht. AEM as a Cloud Service doet dit door de maphiërarchie van `/home` (gegevens van gebruikersprofielen, groepslidmaatschap enzovoort) snel te synchroniseren over alle knooppunten van de publicatielaag.

In tegenstelling tot andere AEM oplossingen, gebruikt de gebruiker en de synchronisatie van het groepslidmaatschap in AEM as a Cloud Service geen punt om overseinenbenadering te richten, in plaats van het uitvoeren van een publish-subscribe benadering die klantenconfiguratie niet vereist.

>[!NOTE]
>
>Het gebruikersprofiel en de synchronisatie van het groepslidmaatschap zijn standaard niet ingeschakeld en de gegevens worden dus niet gesynchroniseerd met of zelfs niet permanent voortgezet op de publicatielaag. Om de functie in te schakelen, stuurt u een verzoek naar de Klantenondersteuning met vermelding van het juiste programma en de juiste omgevingen.

>[!IMPORTANT]
>
>Test de implementatie op schaal voordat u gegevenssynchronisatie inschakelt in de productieomgeving. Afhankelijk van het gebruiksgeval en de gegevens blijven bestaan, kunnen er enige problemen met de consistentie en de latentie optreden.

## Overwegingen bij cache {#cache-considerations}

De voor authentiek verklaarde HTTP- verzoeken kunnen moeilijk zijn om op zowel CDN als Dispatcher in het voorgeheugen onder te brengen aangezien zij de mogelijkheid van gebruiker-specifieke staat dragen die als deel van de reactie van het verzoek wordt overgebracht. Als geverifieerde verzoeken per ongeluk in de cache worden geplaatst en aan andere browsers worden aangeboden, kan dit leiden tot onjuiste ervaringen of zelfs tot het lekken van beveiligde of gebruikersgegevens.

De benaderingen voor het handhaven van hoge geheim voorgeheugen-capaciteit van verzoeken terwijl het steunen van gebruiker-specifieke reacties omvatten:

* Bevoegdheden van Dispatcher AEM
* Dynamisch afspelen opnemen
* AEM ContextHub
