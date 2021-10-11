---
title: Gebruikerstoewijzing gebruiken
description: Gebruikerstoewijzing gebruiken
source-git-commit: 2f763f774b21b0c3b43d61964dda2d2ae596161a
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 3%

---


# Het gereedschap Toewijzing gebruiker gebruiken {#using-user-mapping-tool}

Het hulpmiddel van de Toewijzing van de Gebruiker gebruikt API die het toestaat om gebruikers van het Systeem van Adobe Identity Management (IMS) per e-mail op te zoeken en hun IMS IDs terug te keren. Deze API vereist de gebruiker om een identiteitskaart van de Cliënt voor hun organisatie, een Geheim van de Cliënt, en een Token van de Toegang of van de Drager tot stand te brengen.

## Het gereedschap Toewijzing gebruiker instellen {#setting-up-user-mapping}

Voer de onderstaande stappen uit om dit in te stellen:

1. Navigeer naar [Adobe Developer Console](https://console.adobe.io) met uw Adobe ID.
1. Maak een nieuw project of open een bestaand project.
1. Een API toevoegen - Klik **Toevoegen aan project** en selecteer **API**
1. Kies Gebruikerbeheer-API.  Mogelijk moet u machtigingen ophalen om deze optie te kunnen gebruiken.
1. Maak een JWT-referentie.
1. Genereer een sleutelpaar of upload een openbare sleutel (rsa is geen goed).  Er is een knoop, **Genereer een openbaar/privé sleutelpaar**, die dit voor u zal doen.  Zorg ervoor dat u zowel de openbare als de persoonlijke sleutels opslaat.
1. Navigeer naar de API voor gebruikersbeheer.
1. Genereer een toegangstoken (of een token voor toonder) door uw inhoud van de persoonlijke sleutel in het tekstvak te plakken en te klikken op **Token genereren**.
1. Sla al deze informatie op, zoals **Client ID**, **Client Secret**, **Technical Account ID**, **Technical Account Email**, **Org ID** en **Access Token**.

## De gebruikersinterface openen voor het Hulpmiddel van de Toewijzing van de Gebruiker {#user-interface}

Het hulpmiddel van de Toewijzing van de Gebruiker is geïntegreerd in het Hulpmiddel van de Overdracht van de Inhoud. U kunt het hulpmiddel van de Overdracht van de Inhoud van [Portaal van de Distributie van de Software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) downloaden. Voor meer informatie over de recentste versie, verwijs naar [Huidige Nota&#39;s van de Versie](/help/release-notes/release-notes-cloud/release-notes-current.md).

1. Selecteer de Adobe Experience Manager en navigeer naar gereedschappen -> **Bewerkingen** -> **Inhoud migreren**.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-access1.png)

1. Klik op **Gebruikerstoewijzing** kaart.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-access2.png)

1. Klik op **Gebruikerstoewijzingsconfiguratie maken**.

   >[!NOTE]
   >Als u deze stap overslaat, worden gebruikers en groepstoewijzing overgeslagen tijdens de extractiefase.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-access5.png)

   Vul de velden in **Configuratie van API voor gebruikersbeheer**, zoals hieronder wordt beschreven.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-access3.png)


   * **Org-id**: Voer de Adobe Identity Management System (IMS) Org ID in voor de organisatie waarin de gebruikers worden gemigreerd.

      >[!NOTE]
      >Als u de organisatie-id wilt ophalen, meldt u zich aan bij de [Admin Console](https://adminconsole.adobe.com/) en kiest u uw organisatie (in de rechterbovenhoek) als u tot meer dan één organisatie behoort. De organisatie-id bevindt zich in de URL van die pagina, in de notatie zoals `xx@AdobeOrg`, waarbij xx de IMS Org-id is.  Afwisselend, kunt u Org identiteitskaart in [Adobe de pagina van de Console van de Ontwikkelaar ](https://console.adobe.io) vinden waar u het Symbolische van de Toegang produceert.

   * **Client-id**: Ga identiteitskaart van de Cliënt in die u van de stap van de Opstelling bewaarde.

   * **Toegangstoken**: Ga het Token van de Toegang in dat u van de stap van de Opstelling bewaarde.

      >[!NOTE]
      >Het toegangstoken verloopt elke 24 uur en er moet een nieuwe worden gemaakt. Als u een nieuw token wilt maken, gaat u terug naar [Adobe Developer Console](https://console.adobe.io), kiest u uw project, klikt u op **Gebruikersbeheer API** en plakt u dezelfde persoonlijke sleutel in het vak.

1. Nadat u de velden hebt gevuld, klikt u op **Configuratie testen** om de verbinding met de API-service voor gebruikersbeheer te testen. Als de verbinding succesvol is, zult u **sparen** kunnen klikken om de configuratie te bewaren.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-access4.png)

1. Nadat u de configuratie hebt opgeslagen, selecteert u de configuratie en klikt u op **Gebruikerstoewijzing starten**.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-landing4.png)

1. Zodra de Toewijzing van de Gebruiker volledig is, klik op **Resultaten** om de samenvatting te bekijken.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-landing5.png)

   >[!IMPORTANT]
   >Zodra de Toewijzing van de Gebruiker volledig is, kunt u terug naar de pagina van de Migratie van de Inhoud navigeren gebruikend breadcrumb. Op de kaart met gebruikerstoewijzing worden de status en het tijdstempel weergegeven. Klik op **Content Transfer** om een migratieset te maken die wordt uitgevoerd. Raadpleeg [Het gereedschap Inhoud overbrengen uitvoeren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#running-tool) voor meer informatie.
