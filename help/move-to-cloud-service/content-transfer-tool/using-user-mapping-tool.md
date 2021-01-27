---
title: Gebruikerstoewijzing gebruiken
description: Gebruikerstoewijzing gebruiken
translation-type: tm+mt
source-git-commit: a5129eac9f8032de5931b75c83eea62e480c1847
workflow-type: tm+mt
source-wordcount: '754'
ht-degree: 4%

---


# Gebruikend het Hulpmiddel van de Toewijzing van de Gebruiker {#user-mapping-tool}

## Overzicht {#overview}

Als deel van de overgangsreis aan AEM als Cloud Service, moet u gebruikers en groepen van uw bestaand AEM systeem aan AEM als Cloud Service bewegen. Dit wordt gedaan door het Hulpmiddel van de Overdracht van de Inhoud.

Een belangrijke wijziging in AEM as Cloud Service is het volledig geïntegreerde gebruik van Adobe ID&#39;s voor toegang tot de authoringlaag.  Hiervoor moet de Adobe Admin Console worden gebruikt voor het beheer van gebruikers en gebruikersgroepen. De gebruikersprofielgegevens zijn gecentraliseerd in het Adobe Identity Management System (IMS) dat Single Sign-On biedt voor alle Adobe-cloudtoepassingen. Raadpleeg Identity Management voor meer informatie. Vanwege deze wijziging moeten bestaande gebruikers en groepen worden toegewezen aan hun IMS-id&#39;s om dubbele gebruikers en groepen in de auteur van de Cloud Service te voorkomen.

## Belangrijke overwegingen {#important-considerations}

Er zijn enkele uitzonderlijke gevallen die in overweging moeten worden genomen. De volgende specifieke gevallen worden geregistreerd en de betrokken gebruiker of groep wordt niet toegewezen:

1. Als een gebruiker geen e-mailadres heeft op het `profile/email` gebied van hun jcr knoop.

1. Als een bepaalde e-mail niet wordt gevonden op het IMS-systeem voor de gebruikte organisatie-id (of als de IMS-id om een andere reden niet kan worden opgehaald).

1. Als de gebruiker momenteel is uitgeschakeld, wordt deze op dezelfde manier behandeld als wanneer de gebruiker niet is uitgeschakeld.  Het wordt toegewezen en gemigreerd als normaal en blijft uitgeschakeld in de cloudinstantie.

## Het gebruiken van het Hulpmiddel van de Toewijzing van de Gebruiker {#using-user-mapping-tool}

Het gereedschap Toewijzing gebruiker gebruikt een API waarmee IMS-gebruikers via e-mail kunnen worden opgezocht en hun IMS-id&#39;s kunnen worden geretourneerd. Deze API vereist de gebruiker om een identiteitskaart van de Cliënt voor hun organisatie, een Geheim van de Cliënt, en een Token van de Token van de Toegang te creëren/Drager.

Voer de volgende stappen uit om dit in te stellen:

1. Navigeer naar [Adobe Developer Console](https://console.adobe.io) met uw Adobe ID.
1. Een nieuw project maken of een bestaand project openen
1. Een API toevoegen
1. Gebruikerbeheer-API kiezen
1. Een JWT-referentie maken
1. Een sleutelpaar genereren of een openbare sleutel uploaden (rsa is geen goed)
1. Genereer een toegangstoken (of teken JWT of dragertoken).
1. Sla al deze gegevens (client-id, clientgeheim, technische-accountid, e-mail voor technische account, organisatie-id, toegangstoken) op een veilige plaats op.

## Gebruikersinterface {#user-interface}

Het hulpmiddel van de Toewijzing van de Gebruiker is geïntegreerd in het Hulpmiddel van de Overdracht van de Inhoud. U kunt het hulpmiddel van de Overdracht van de Inhoud van de Portaal van de Distributie van de Software downloaden. Raadpleeg Opmerkingen bij de release voor meer informatie over de meest recente versie.

1. Selecteer de Adobe Experience Manager selecteren en navigeer naar gereedschappen -> **Bewerkingen** -> **Inhoud overbrengen**.
1. Klik op **Gebruikerstoewijzingsconfiguratie maken**.

   >[!NOTE]
   >Als u deze stap overslaat, worden gebruikers en groepstoewijzing overgeslagen tijdens de extractiefase.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-1.png)

   Vul de velden in de configuratie van de API voor gebruikersbeheer als volgt in:

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-2.png)

   * **Org-id**: Voer de IMS-organisatie-id in voor de organisatie waarin de gebruikers worden gemigreerd.

      >[!NOTE]
      >Als u de organisatie-id wilt ophalen, meldt u zich aan bij de [Admin Console](https://adminconsole.adobe.com/) en kiest u uw organisatie (in de rechterbovenhoek) als u tot meer dan één organisatie behoort. De organisatie-id bevindt zich in de URL van die pagina, in de notatie zoals `xx@AdobeOrg`, waarbij xx de IMS Org-id is.  Afwisselend, kunt u Org identiteitskaart in [Adobe de pagina van de Console van de Ontwikkelaar ](https://console.adobe.io) vinden waar u het Symbolische van de Toegang produceert.

   * **Client-id**: Ga identiteitskaart van de Cliënt in die u van de stap van de Opstelling bewaarde

   * **Toegangstoken**: Ga het Token van de Toegang in dat u van de stap van de Opstelling bewaarde

      >[!NOTE]
      >Het toegangstoken verloopt elke 24 uur en er moet een nieuwe worden gemaakt. Als u een nieuw token wilt maken, gaat u terug naar [Adobe Developer Console](https://console.adobe.io) en kiest u uw project. Klik vervolgens op de API voor gebruikersbeheer en plak dezelfde persoonlijke sleutel in het vak.

1. Nadat u de bovenstaande gegevens hebt ingevoerd, klikt u op **Opslaan**.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-3.png)


1. Maak een migratieset door op **Migratieset maken** te klikken en de velden te vullen en vervolgens op **Opslaan** te klikken. Raadpleeg Het gereedschap Inhoud overbrengen uitvoeren voor meer informatie.

   >[!NOTE]
   >De schakeloptie voor het opnemen van toewijzingsgebruikers van IMS-gebruikers en -groepen is standaard ingeschakeld. Met deze instelling, wanneer Extractie wordt uitgevoerd op deze migratieset, wordt het gereedschap Toewijzing gebruiker uitgevoerd als onderdeel van de extractiefase. Dit is de aanbevolen manier om de extractiefase van het gereedschap Inhoud overbrengen uit te voeren. Als deze schakeloptie is uitgeschakeld en/of er geen configuratie voor gebruikerstoewijzing is gemaakt, worden gebruikers- en groepstoewijzing overgeslagen tijdens de extractiefase.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-4.png)

1. Als u de extractiefase wilt uitvoeren, raadpleegt u [Het gereedschap Inhoud overbrengen uitvoeren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#running-tool).



