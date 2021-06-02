---
title: Gebruikerstoewijzing gebruiken
description: Gebruikerstoewijzing gebruiken
exl-id: 88ce7ed3-46fe-4b3f-8e18-c7c8423faf24
source-git-commit: a9119ac04762c91230d52d6418b7808bca7e9f9f
workflow-type: tm+mt
source-wordcount: '1266'
ht-degree: 4%

---

# Gebruikend het Hulpmiddel van de Toewijzing van de Gebruiker {#user-mapping-tool}

## Overzicht {#overview}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_usermapping"
>title="Gereedschap Toewijzing gebruiker"
>abstract="Met het gereedschap Inhoud overbrengen kunt u gebruikers en groepen verplaatsen van uw bestaande AEM naar AEM als Cloud Service. Bestaande gebruikers en groepen moeten aan hun IMS-id&#39;s worden toegewezen om dubbele gebruikers en groepen op de Cloud Service-auteur te voorkomen."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=en#important-considerations" text="Belangrijke overwegingen voor het gebruik van het gereedschap Toewijzing gebruiker"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=en#using-user-mapping-tool" text="Gebruikerstoewijzing gebruiken"

Als onderdeel van de overgang naar Adobe Experience Manager (AEM) als Cloud Service, moet u gebruikers en groepen verplaatsen van uw bestaande AEM naar AEM als Cloud Service. Dit wordt gedaan door het Hulpmiddel van de Overdracht van de Inhoud.

Een belangrijke wijziging in AEM as Cloud Service is het volledig geïntegreerde gebruik van Adobe ID&#39;s voor toegang tot de authoringlaag.  Dit vereist gebruik van [Adobe Admin Console](https://helpx.adobe.com/nl/enterprise/using/admin-console.html) voor het beheren van gebruikers en gebruikersgroepen. De gebruikersprofielgegevens zijn gecentraliseerd in het Adobe Identity Management System (IMS) dat Single Sign-On biedt voor alle Adobe-cloudtoepassingen. Raadpleeg [Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/what-is-new-and-different.html?lang=en#identity-management) voor meer informatie. Vanwege deze wijziging moeten bestaande gebruikers en groepen worden toegewezen aan hun IMS-id&#39;s om dubbele gebruikers en groepen in de auteur van de Cloud Service te voorkomen.

### Gereedschap Toewijzing gebruiker {#mapping-tool}

Met het gereedschap Inhoud overbrengen (zonder gebruikerstoewijzing) worden alle gebruikers en groepen gemigreerd die zijn gekoppeld aan de inhoud die wordt gemigreerd. Het hulpmiddel van de Toewijzing van de Gebruiker is een deel van het Hulpmiddel van de Overdracht van de Inhoud, en zijn enig doel is de gebruikers en de groepen te wijzigen zodat zij correct door IMS, de enig-sign-on functionaliteit kunnen worden herkend die door AEM als Cloud Service wordt gebruikt. Zodra deze wijzigingen zijn aangebracht, migreert het gereedschap Inhoud overbrengen de gebruikers en groepen van de opgegeven inhoud zoals gewoonlijk.

## Belangrijke overwegingen {#important-considerations}

### Uitzonderlijke gevallen {#exceptional-cases}

De volgende specifieke gevallen worden geregistreerd:

1. Als een gebruiker geen e-mailadres heeft op het `profile/email` gebied van hun *jcr* knoop zal de gebruiker of de groep in kwestie worden gemigreerd maar niet in kaart gebracht.

1. Als een bepaalde e-mail niet wordt gevonden op het Adobe Identity Management System (IMS) voor de gebruikte organisatie-id (of als de IMS-id om een andere reden niet kan worden opgehaald), wordt de gebruiker of groep in kwestie gemigreerd, maar niet toegewezen.

1. Als de gebruiker momenteel is uitgeschakeld, wordt deze op dezelfde manier behandeld als wanneer de gebruiker niet is uitgeschakeld. Het wordt toegewezen en gemigreerd als normaal en blijft uitgeschakeld in de cloudinstantie.

1. Als een gebruiker op de instantie van de doel AEM Cloud Service met de zelfde gebruikersnaam (rep:principalName) zoals één van de gebruikers op de bron AEM instantie bestaat zal de gebruiker of de groep in kwestie niet worden gemigreerd.

### Aanvullende overwegingen {#additional-considerations}

* Als de instelling **Bestaande inhoud vegen op een Cloud-instantie voordat inname** wordt ingesteld, worden reeds overgedragen gebruikers op de Cloud Service-instantie samen met de gehele bestaande opslagplaats verwijderd en wordt een nieuwe opslagplaats gemaakt om inhoud in te voeren. Dit stelt ook alle montages met inbegrip van toestemmingen op de instantie van de doelCloud Service terug en is waar voor een admin gebruiker die aan **beheerders** groep wordt toegevoegd. De admin gebruiker zal aan **beheerders** groep opnieuw moeten worden toegevoegd om het toegangstoken voor CTT terug te winnen.

* Het wordt geadviseerd om het even welke bestaande gebruiker uit de AEM van de doelCloud Service te verwijderen alvorens CTT met Toewijzing van de Gebruiker in werking te stellen. Hiermee wordt elk conflict voorkomen tussen het migreren van gebruikers van de AEM naar de AEM instantie van het doel. Conflicten treden op tijdens inname als dezelfde gebruiker bestaat op de bron AEM instantie en de AEM instantie.

* Wanneer de inhoud toevoegt wordt uitgevoerd, als de inhoud niet wordt overgebracht omdat het sinds de vorige overdracht niet is veranderd, zullen de gebruikers en de groepen verbonden aan die inhoud ook niet worden overgebracht, zelfs als de gebruikers en de groepen ondertussen zijn veranderd. Dit komt doordat gebruikers en groepen worden gemigreerd met de inhoud waaraan ze zijn gekoppeld.

* De inname zal in de volgende scenario&#39;s ontbreken:

1. Als de AEM Cloud Service van het doel een gebruiker met een verschillende gebruikersnaam maar zelfde e-mailadres heeft zoals één van de gebruikers op de bron AEM instantie.

1. Als er twee gebruikers op de AEM zijn met verschillende gebruikersnamen maar hetzelfde e-mailadres. AEM als Cloud Service staat twee gebruikers niet toe om hetzelfde e-mailadres te hebben.

## Het gebruiken van het Hulpmiddel van de Toewijzing van de Gebruiker {#using-user-mapping-tool}

Het hulpmiddel van de Toewijzing van de Gebruiker gebruikt API die het toestaat om gebruikers van het Systeem van Adobe Identity Management (IMS) per e-mail op te zoeken en hun IMS IDs terug te keren. Deze API vereist de gebruiker om een identiteitskaart van de Cliënt voor hun organisatie, een Geheim van de Cliënt, en een Token van de Toegang of van de Drager tot stand te brengen.

Voer de onderstaande stappen uit om dit in te stellen:

1. Navigeer naar [Adobe Developer Console](https://console.adobe.io) met uw Adobe ID.
1. Maak een nieuw project of open een bestaand project.
1. Voeg een API toe.
1. Kies Gebruikerbeheer-API.
1. Maak een JWT-referentie.
1. Genereer een sleutelpaar of upload een openbare sleutel (rsa is geen goed).
1. Genereer een toegangstoken (of teken JWT of dragertoken).
1. Sla al deze informatie op, zoals **Client ID**, **Client Secret**, **Technical Account ID**, **Technical Account Email**, **Org ID** en **Access Token**.

## Gebruikersinterface {#user-interface}

Het hulpmiddel van de Toewijzing van de Gebruiker is geïntegreerd in het Hulpmiddel van de Overdracht van de Inhoud. U kunt het hulpmiddel van de Overdracht van de Inhoud van [Portaal van de Distributie van de Software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) downloaden. Voor meer informatie over de recentste versie, verwijs naar [Huidige Nota&#39;s van de Versie](/help/release-notes/release-notes-cloud/release-notes-current.md).

1. Selecteer de Adobe Experience Manager en navigeer naar Tools -> **Operations** -> **Content Transfer**.
1. Klik op **Gebruikerstoewijzingsconfiguratie maken**.

   >[!NOTE]
   >Als u deze stap overslaat, worden gebruikers en groepstoewijzing overgeslagen tijdens de extractiefase.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-1.png)

   Vul de velden in de configuratie van de API voor gebruikersbeheer als volgt in:

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-2.png)

   * **Org-id**: Voer de Adobe Identity Management System (IMS) Org ID in voor de organisatie waarin de gebruikers worden gemigreerd.

      >[!NOTE]
      >Als u de organisatie-id wilt ophalen, meldt u zich aan bij de [Admin Console](https://adminconsole.adobe.com/) en kiest u uw organisatie (in de rechterbovenhoek) als u tot meer dan één organisatie behoort. De organisatie-id bevindt zich in de URL van die pagina, in de notatie zoals `xx@AdobeOrg`, waarbij xx de IMS Org-id is.  Afwisselend, kunt u Org identiteitskaart in [Adobe de pagina van de Console van de Ontwikkelaar ](https://console.adobe.io) vinden waar u het Symbolische van de Toegang produceert.

   * **Client-id**: Ga identiteitskaart van de Cliënt in die u van de stap van de Opstelling bewaarde.

   * **Toegangstoken**: Ga het Token van de Toegang in dat u van de stap van de Opstelling bewaarde.

      >[!NOTE]
      >Het toegangstoken verloopt elke 24 uur en er moet een nieuwe worden gemaakt. Als u een nieuw token wilt maken, gaat u terug naar [Adobe Developer Console](https://console.adobe.io), kiest u uw project, klikt u op **Gebruikersbeheer API** en plakt u dezelfde persoonlijke sleutel in het vak.

1. Nadat u de bovenstaande gegevens hebt ingevoerd, klikt u op **Opslaan**.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-3.png)


1. Maak een migratieset door op **Migratieset maken** te klikken en de velden te vullen en vervolgens op **Opslaan** te klikken. Raadpleeg [Het gereedschap Inhoud overbrengen uitvoeren](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#running-tool) voor meer informatie.

   >[!NOTE]
   >De schakeloptie voor het opnemen van toewijzingsgebruikers van IMS-gebruikers en -groepen is standaard ingeschakeld. Met deze instelling, wanneer Extractie wordt uitgevoerd op deze migratieset, wordt het gereedschap Toewijzing gebruiker uitgevoerd als onderdeel van de extractiefase. Dit is de aanbevolen manier om de extractiefase van het gereedschap Inhoud overbrengen uit te voeren. Als deze schakeloptie is uitgeschakeld en/of er geen configuratie voor gebruikerstoewijzing is gemaakt, worden gebruikers- en groepstoewijzing overgeslagen tijdens de extractiefase.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-4.png)

1. Als u de extractiefase wilt uitvoeren, raadpleegt u [Het gereedschap Inhoud overbrengen uitvoeren](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#running-tool).
