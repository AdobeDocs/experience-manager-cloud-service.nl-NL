---
title: Registratie, aanmelding en gebruikersprofiel
description: Meer informatie over registratie, aanmelding, gebruikersgegevens en groepssynchronisatie voor AEM as a Cloud Service
exl-id: a991e710-a974-419f-8709-ad86c333dbf8
solution: Experience Manager Sites
feature: Authoring, Personalization
role: User
source-git-commit: 54159c25b60277268ade16b437891f268873fecf
workflow-type: tm+mt
source-wordcount: '1340'
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

Wanneer een eindgebruiker voor een rekening op een AEM toepassing registreert, wordt een gebruikersrekening gecreeerd op de dienst van AEM Publish, zoals die op een gebruikersmiddel onder wordt weerspiegeld `/home/users` in de gegevensopslagruimte van het JCR.

Er zijn twee manieren om registratie uit te voeren, zoals hieronder beschreven.

### AEM Beheerd {#aem-managed-registration}

U kunt aangepaste registratiecode schrijven die minimaal de gebruikersnaam en het wachtwoord van de gebruiker nodig heeft en een gebruikersrecord maakt in AEM die u tijdens de aanmelding kunt gebruiken voor verificatie. De volgende stappen worden doorgaans gebruikt om dit registratiemechanisme samen te stellen:

1. Een aangepaste AEM die registratiegegevens verzamelt weergeven
1. Bij verzending wordt een naar behoren ingericht servicegebruiker gebruikt voor
   1. Controleren of een bestaande gebruiker nog niet bestaat met een van de API&#39;s van UserManager `findAuthorizables()` methoden
   1. Een gebruikersrecord maken met een van de API&#39;s van UserManager `createUser()` methoden
   1. Behoud om het even welke profielgegevens die gebruikend de Authorizable interface worden gevangen `setProperty()` methoden
1. Optionele stromen, zoals de verplichting voor de gebruiker om zijn e-mail te valideren.

**Vereiste:**

Schakel de functie in van de bovenstaande logica voor een correcte werking [gegevenssynchronisatie](#data-synchronization-data-synchronization) door een verzoek in te dienen bij de Klantenondersteuning met vermelding van het desbetreffende programma en de relevante omgevingen.

### Extern {#external-managed-registration}

In sommige gevallen is de registratie of het creëren van gebruikers eerder gebeurd in infrastructuur buiten AEM. In dat scenario, wordt het gebruikersverslag gecreeerd in AEM tijdens login.

## Aanmelden {#login}

Zodra een eindgebruiker op de dienst van AEM Publish wordt geregistreerd, kunnen deze gebruikers login om voor authentiek verklaarde toegang (gebruikend AEM vergunningsmechanismen) en voortgezette, gebruiker-specifieke gegevens zoals profielgegevens te hebben.

## Implementatie {#implementation}

Aanmelding kan op de volgende twee manieren worden uitgevoerd:

### AEM Beheerd {#aem-managed-implementation}

Klanten kunnen hun eigen aangepaste componenten schrijven. Meer leren, overweeg vertrouwd worden met:

* De [Sling Authentication Framework](https://sling.apache.org/documentation/the-sling-engine/authentication/authentication-framework.html)
* en overwegen [waarbij de AEM communautaire deskundigenvergadering wordt gevraagd](https://bit.ly/ATACEFeb15) over aanmelden.

**Vereiste:**

Schakel de functie in van de bovenstaande logica voor een correcte werking [gegevenssynchronisatie](#data-synchronization-data-synchronization) door een verzoek in te dienen bij de Klantenondersteuning met vermelding van het desbetreffende programma en de relevante omgevingen.

### Integratie met een identiteitsprovider {#integration-with-an-idp}

De klanten kunnen met een IdP (identiteitsleverancier) integreren, die de gebruiker voor authentiek verklaart. De technologieën van de integratie omvatten SAML en OAuth/SSO, zoals hieronder beschreven.

**SAML GEBASEERD**

De klanten kunnen op SAML-Gebaseerde authentificatie via hun aangewezen SAML IdP gebruiken. Wanneer het gebruiken van een IdP met AEM, is IdP verantwoordelijk voor het voor authentiek verklaren van de geloofsbrieven van de gebruiker en het tussenhandel drijven van de authentificatie van de gebruiker met AEM, die tot het gebruikersverslag in AEM zoals nodig leiden, en het groepslidmaatschap van de gebruiker in AEM, zoals die door de bewering van SAML wordt beschreven.

>[!NOTE]
>
>Alleen de initiële verificatie van de gebruikersgegevens wordt geverifieerd door de IdP en volgende aanvragen om AEM worden uitgevoerd met behulp van een AEM token, zolang het cookie beschikbaar is.

Zie de documentatie voor meer informatie over de [SAML 2.0-verificatiehandler](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/authentication/saml-2-0.html).

**OAuth/SSO**

Zie de [Single Sign On (SSO)-documentatie](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/single-sign-on.html) voor informatie over het gebruiken van de AEMDienst van de Handler van de Authentificatie SSO.

De `com.adobe.granite.auth.oauth.provider` De interface kan met de leverancier OAuth van uw keus worden uitgevoerd.

**Vereiste:**

Als beste praktijken, baseer altijd op idP (de Leverancier van de Identiteit) als één enkel punt van waarheid wanneer het opslaan van gebruiker-specifieke gegevens. Als de aanvullende gebruikersgegevens zijn opgeslagen in de lokale opslagplaats, die geen deel uitmaakt van de idP, schakelt u [gegevenssynchronisatie](#data-synchronization-data-synchronization) door een verzoek in te dienen bij de Klantenondersteuning met vermelding van het desbetreffende programma en de relevante omgevingen. Naast [gegevenssynchronisatie](#data-synchronization-data-synchronization), in het geval van de SAML-authenticatieprovider, ervoor zorgen dat [dynamisch groepslidmaatschap](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/authentication/saml-2-0) is ingeschakeld.

### Vaste sessies en ingekapselde tokens {#sticky-sessions-and-encapsulated-tokens}

AEM as a Cloud Service maakt op cookies gebaseerde sticky-sessies mogelijk, zodat een eindgebruiker op elke aanvraag naar hetzelfde publicatieknooppunt wordt gerouteerd. In bepaalde gevallen, zoals gebruikersverkeersspikes, zou de ingekapselde symbolische eigenschap prestaties kunnen verhogen zodat het gebruikersverslag in de bewaarplaats te hoeven niet om op elke aanvraag worden van verwijzingen voorzien. Als het publicatieknooppunt waaraan een eindgebruiker een affiniteit heeft wordt vervangen, zijn het verslag van hun gebruiker - identiteitskaart beschikbaar op het nieuwe publicatieknooppunt, zoals die in wordt beschreven [gegevenssynchronisatie](#data-synchronization-data-synchronization) hieronder.

Als u de ingekapselde tokenfunctie wilt gebruiken, dient u bij de Klantenondersteuning een aanvraag in waarin het juiste programma en de juiste omgevingen worden vermeld. Nog belangrijker, kan het ingekapselde token niet worden ingeschakeld zonder [gegevenssynchronisatie](#data-synchronization-data-synchronization) en moet samen worden ingeschakeld. Controleer daarom zorgvuldig het gebruiksgeval voordat u de functie inschakelt en zorg ervoor dat deze essentieel is.

## Gebruikersprofiel {#user-profile}

Afhankelijk van de aard van de gegevens zijn er verschillende benaderingen voor het aanhouden van gegevens.

### AEM {#aem-repository}

Gebruikersprofielgegevens kunnen op twee manieren worden geschreven en gelezen:

* Gebruik op de server met de `com.adobe.granite.security.user` Interface UserPropertiesManager interface, die gegevens onder de knoop van de gebruiker in zal plaatsen `/home/users`. Zorg ervoor dat de pagina&#39;s die per gebruiker uniek zijn niet in het voorgeheugen onder worden gebracht.
* Client-kant die ContextHub gebruikt, zoals die door wordt beschreven [de documentatie](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/personalization/contexthub.html#personalization).

**Vereiste:**

Schakel de persistentielogica van het gebruikersprofiel aan de serverzijde in voor een correcte werking. [gegevenssynchronisatie](#data-synchronization-data-synchronization) door een verzoek in te dienen bij de Klantenondersteuning met vermelding van het desbetreffende programma en de relevante omgevingen.

### Gegevensopslag van derden {#third-party-data-stores}

Eindgebruikersgegevens kunnen naar externe leveranciers, zoals CRM&#39;s, worden verzonden en via API&#39;s worden opgehaald wanneer de gebruiker zich aanmeldt om AEM te maken en te blijven (of te vernieuwen) op het profielknooppunt van de AEM gebruiker en door AEM worden gebruikt.

Realtime toegang tot derdediensten om profielattributen terug te winnen is mogelijk, echter, is het belangrijk om ervoor te zorgen dit verzoekverwerking in AEM niet wezenlijk beïnvloedt.

**Vereiste:**

Schakel de functie in van de bovenstaande logica voor een correcte werking [gegevenssynchronisatie](#data-synchronization-data-synchronization) door een verzoek in te dienen bij de Klantenondersteuning met vermelding van het desbetreffende programma en de relevante omgevingen.

## Machtigingen (gesloten gebruikersgroepen) {#permissions-closed-user-groups}

Het Publish-niveau toegangsbeleid, ook genoemd Gesloten Gebruikersgroepen (CUGs), wordt bepaald in de AEM auteur als [hier beschreven](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/cug.html#applying-your-closed-user-group-to-content-pages). Als u bepaalde gedeelten of pagina&#39;s van een website van bepaalde gebruikers wilt beperken, past u de CUG&#39;s waar nodig toe met de auteur van de AEM, zoals hier beschreven. U kopieert deze secties of pagina&#39;s vervolgens naar de publicatielijst.

* Als de gebruikers login door met een identiteitsleverancier (IdP) het gebruiken van SAML voor authentiek te verklaren, zal de authentificatiemanager de groepslidmaatschappen van de gebruiker identificeren (die CUGs op publiceren rij zouden moeten aanpassen), en zal de vereniging tussen de gebruiker en de groep door een verslag van de bewaarplaats aanhouden
* Als login zonder integratie IdP wordt verwezenlijkt, kan de douanecode de zelfde de structuurverhoudingen van de bewaarplaats toepassen.

Onafhankelijk van login, kan de douanecode ook het groepslidmaatschap van een gebruiker voortzetten en beheren zoals vereist door de unieke vereisten van een organisatie.

## Gegevenssynchronisatie {#data-synchronization}

Eindgebruikers van een website hebben een verwachting van een consistente ervaring op elk verzoek van een webpagina of zelfs wanneer ze zich aanmelden met een andere browser, zelfs als ze deze niet kennen, worden ze naar verschillende serverknooppunten van de infrastructuur van de publicatielaag gebracht. AEM as a Cloud Service doet dit door de `/home` de omslaghiërarchie (de informatie van het gebruikersprofiel, groepslidmaatschap, etc.) over alle knopen van publiceren rij.

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
