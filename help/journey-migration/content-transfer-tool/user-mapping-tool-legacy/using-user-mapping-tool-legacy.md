---
title: Gebruikerstoewijzing gebruiken (verouderd)
description: Gebruikerstoewijzing gebruiken (verouderd)
exl-id: dcb750c4-0f81-4d11-ac6c-0592162b683d
hide: true
hidefromtoc: true
feature: Migration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '806'
ht-degree: 1%

---

# Het gereedschap Toewijzing gebruiker gebruiken (verouderd) {#using-user-mapping-tool}

>[!INFO]
>
>Deze documentatie verwijst naar een verouderde versie van het hulpmiddel. Voor meer informatie over de meest recente versie raadpleegt u [Toewijzing van gebruikers en belangrijkste migratie](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/user-mapping-and-migration.md).

Het hulpmiddel van de Toewijzing van de Gebruiker gebruikt API die het toestaat om Adobe gebruikers van het Systeem van Identity Management (IMS) per e-mail op te zoeken en hun IMS IDs terug te keren. Deze API vereist de gebruiker om een identiteitskaart van de Cliënt voor hun organisatie, een Geheim van de Cliënt, en een Token van de Toegang of van de Drager tot stand te brengen.

## Het gereedschap Toewijzing gebruiker instellen {#setting-up-user-mapping}

**Vereiste:** Voor gebruikerstoewijzing moet elke gebruiker die aan zijn IMS-id moet worden toegewezen, een e-mailadres hebben in zijn profiel in AEM en in IMS. Zelfs als de gebruiker een e-mailadres gebruikt als een gebruikers-id voor het aanmelden, werkt de toewijzing niet voor die gebruiker, tenzij het e-mailadres ook in het profiel en ook in IMS staat.

Voer de onderstaande stappen uit om dit in te stellen:

1. Navigeren naar [Adobe Developer Console](https://developer.adobe.com/console/) met uw Adobe ID.
1. Maak een project of open een bestaand project.
1. Een API toevoegen - klik op **Toevoegen aan project** en selecteert u **API**
1. Kies Gebruikerbeheer-API. Deze optie is alleen beschikbaar als u beschikt over systeembeheerdersmachtigingen.
1. Maak een JWT-referentie.
1. Genereer een sleutelpaar of upload een openbare sleutel (rsa is geen goed). Er is een knop, **Een openbaar/privé-sleutelpaar genereren** dat tot dit keypair voor u leidt. Zorg ervoor dat u zowel de openbare als de persoonlijke sleutels opslaat.
1. Navigeer naar de API voor gebruikersbeheer.
1. Genereer een toegangstoken (of token voor toonder) door uw inhoud van de persoonlijke sleutel in het tekstvak te plakken en op **Token genereren**.
1. Alle informatie opslaan, zoals **Client-id**, **Clientgeheim**, **Technisch account-id**, **E-mail technische account**, **Org-id**, en **Toegangstoken** veilig.

## De gebruikersinterface openen voor het Hulpprogramma voor gebruikerstoewijzing {#user-interface}

Het hulpmiddel van de Toewijzing van de Gebruiker is geïntegreerd in het Hulpmiddel van de Overdracht van de Inhoud. U kunt het gereedschap Inhoud overbrengen downloaden van [Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html). Ga voor meer informatie over de nieuwste versie naar [Opmerkingen bij de huidige release](/help/release-notes/release-notes-cloud/release-notes-current.md).

1. Selecteer de Adobe Experience Manager en navigeer naar gereedschappen > **Bewerkingen** > **Inhoud migreren**.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access1.png)

1. Klik op de knop **Gebruikerstoewijzing** kaart.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access2.png)

1. Klikken **Config. gebruikerstoewijzing maken**.

   >[!NOTE]
   >Als u deze stap overslaat, worden gebruikers en groepstoewijzing overgeslagen tijdens de extractiefase.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access5.png)

   Vul de velden in **API-configuratie voor gebruikersbeheer**, zoals hieronder beschreven.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access3.png)


   * **Org-id**: Voer de Adobe Identity Management System (IMS) Org ID in voor de organisatie waarop de gebruikers worden gemigreerd.

     >[!NOTE]
     >Als u de organisatie-id wilt ophalen, meldt u zich aan bij de [Admin Console](https://adminconsole.adobe.com/) en kies uw organisatie (in het hoger-juiste gebied) als u tot meer dan één behoort. De organisatie-id staat in de URL van die pagina, in de notatie `xx@AdobeOrg`, waarbij xx de IMS Org ID is. U kunt de organisatie-id ook vinden in het dialoogvenster [Adobe Developer Console](https://developer.adobe.com/console/) pagina waar u het Token van de Toegang produceert.

   * **Client-id**: Ga identiteitskaart van de Cliënt in die u van de stap van de Opstelling bewaarde.

   * **Toegangstoken**: Ga het Token van de Toegang in dat u van de stap van de Opstelling bewaarde.

     >[!NOTE]
     >De token Access verloopt elke 24 uur en er moet een nieuwe token worden gemaakt. Ga terug naar [Adobe Developer Console](https://developer.adobe.com/console/), kies uw project, klik **Gebruikersbeheer-API** en plak dezelfde persoonlijke sleutel in het vak.

1. Klik op **Configuratie testen** om de verbinding met de API-service voor gebruikersbeheer te testen. Als de verbinding tot stand is gebracht, kunt u op **Opslaan** om de configuratie op te slaan.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access4.png)

1. Na het bewaren van de configuratie, selecteer de configuratie en klik **Gebruikerstoewijzing starten**.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-landing4.png)

1. Klikken **Start** in het dialoogvenster, zodat u het proces Gebruikerstoewijzing start.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping3.png)

   De interface geeft de **Status** als **UITVOEREN**.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-start1.png)


1. Nadat de Toewijzing van de Gebruiker volledig is, klik **Resultaten** om de samenvatting te bekijken.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-landing5.png)

   >[!IMPORTANT]
   >
   >* Nadat de Toewijzing van de Gebruiker volledig is, kunt u terug naar de pagina van de Migratie van de Inhoud navigeren gebruikend breadcrumb. Op de kaart met gebruikerstoewijzing worden de status en het tijdstempel weergegeven. Klikken **Inhoud overbrengen** zodat u een migratieset kunt maken die wordt uitgevoerd. Zie [Het gereedschap Inhoud overbrengen uitvoeren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html#running-tool) voor meer informatie .

### De gebruikerstoewijzingsprocedure hervatten {#resume-user-mapping-process}

Als het proces voor het toewijzen van gebruikersgegevens is gestopt vanwege een van de volgende redenen:

* De optie **Gebruikerstoewijzing stoppen** is geselecteerd door de gebruiker.
* Het toegangstoken verstreek tijdens het proces.
* Of, een andere reden.

  >[!NOTE]
  >De voortgang wordt opgeslagen vanaf het punt waar het proces is gestopt.

Voer de onderstaande stappen uit om het proces voor het toewijzen van gebruikers te hervatten:

1. Klikken **Logboek weergeven** om het logbestand met gebruikerstoewijzing te bekijken, zodat u de opgeslagen voortgang kunt controleren.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping1.png)

1. Klikken **Gebruikerstoewijzing starten** opnieuw om te hervatten vanaf het punt waar deze was uitgeschakeld.

   >[!NOTE]
   >Zorg ervoor alvorens opnieuw te beginnen dat het toegangstoken nog geldig is of is verfrist.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping2.png)

1. Klikken **Start** in het dialoogvenster, zodat u het proces Gebruikerstoewijzing kunt hervatten.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping3.png)

   Nadat het proces voor gebruikerstoewijzing is voltooid, kunt u de **Status** als **VOLTOOID** voor die specifieke configuratie.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping4.png)
