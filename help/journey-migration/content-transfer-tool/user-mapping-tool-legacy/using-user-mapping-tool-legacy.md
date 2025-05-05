---
title: Gebruikerstoewijzing gebruiken (verouderd)
description: Gebruikerstoewijzing gebruiken (verouderd)
exl-id: dcb750c4-0f81-4d11-ac6c-0592162b683d
hide: true
hidefromtoc: true
feature: Migration
role: Admin
source-git-commit: e5fd1b351047213adbb83ef1d1722352958ce823
workflow-type: tm+mt
source-wordcount: '803'
ht-degree: 1%

---


# Het gereedschap Toewijzing gebruiker gebruiken (verouderd) {#using-user-mapping-tool}

>[!INFO]
>
>Deze documentatie verwijst naar een verouderde versie van het hulpmiddel. Voor meer informatie over de recentste versie, zie [ de Migratie van de Groep ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/group-migration.md).

Het hulpmiddel van de Toewijzing van de Gebruiker gebruikt API die het toestaat om Adobe gebruikers van het Systeem van Identity Management (IMS) per e-mail op te zoeken en hun IMS IDs terug te keren. Deze API vereist de gebruiker om een identiteitskaart van de Cliënt voor hun organisatie, een Geheim van de Cliënt, en een Token van de Toegang of van de Drager tot stand te brengen.

## Het gereedschap Toewijzing gebruiker instellen {#setting-up-user-mapping}

**Vereiste:** de afbeelding van de Gebruiker vereist dat elke gebruiker die aan zijn identiteitskaart moet worden in kaart gebracht IMS een e-mailadres in zijn profiel in AEM, en in IMS heeft. Zelfs als de gebruiker een e-mailadres gebruikt als een gebruikers-id voor het aanmelden, werkt de toewijzing niet voor die gebruiker, tenzij het e-mailadres ook in het profiel en ook in IMS staat.

Voer de onderstaande stappen uit om dit in te stellen:

1. Navigeer aan [ Adobe Developer Console ](https://developer.adobe.com/console/) gebruikend uw Adobe ID.
1. Maak een project of open een bestaand project.
1. Voeg API toe - klik **toevoegen aan Project** en selecteer **API**
1. Kies Gebruikerbeheer-API. Deze optie is alleen beschikbaar als u beschikt over systeembeheerdersmachtigingen.
1. Maak een JWT-referentie.
1. Genereer een sleutelpaar of upload een openbare sleutel (rsa is geen goed). Er is een knoop, **produceer een openbaar/privé sleutelpaar** dat tot dit keypair voor u leidt. Zorg ervoor dat u zowel de openbare als de persoonlijke sleutels opslaat.
1. Navigeer naar de API voor gebruikersbeheer.
1. Produceer een toegangstoken (of dragerteken) door uw privé zeer belangrijke inhoud in het tekstvakje te kleven en **te klikken produceert Symbolisch**.
1. Sparen al deze informatie zoals **identiteitskaart van de Cliënt**, **Geheime Cliënt**, **identiteitskaart van de Technische Rekening**, **E-mail van de Technische Rekening**, **Org identiteitskaart**, en **Symbolisch van de Toegang** veilig.

## De gebruikersinterface openen voor het Hulpprogramma voor gebruikerstoewijzing {#user-interface}

Het hulpmiddel van de Toewijzing van de Gebruiker is geïntegreerd in het Hulpmiddel van de Overdracht van de Inhoud. U kunt het Hulpmiddel van de Overdracht van de Inhoud van [ Portaal van de Distributie van de Software downloaden ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html). Voor meer details op de recentste versie, zie [ Huidige Nota&#39;s van de Versie ](/help/release-notes/release-notes-cloud/release-notes-current.md).

1. Selecteer Adobe Experience Manager en navigeer aan hulpmiddelen > **Verrichtingen** > **de Migratie van de Inhoud**.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access1.png)

1. Klik de **kaart van de Toewijzing van 0&rbrace; Gebruiker.**

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access2.png)

1. Klik **creëren Configuratie van de Toewijzing van de Gebruiker**.

   >[!NOTE]
   >Als u deze stap overslaat, worden gebruikers en groepstoewijzing overgeslagen tijdens de extractiefase.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access5.png)

   Vul de gebieden in **het Beheer API Configuratie van de Gebruiker**, zoals hieronder beschreven.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access3.png)


   * **Org identiteitskaart**: Ga het Systeem van Identity Management van de Adobe (IMS) Org identiteitskaart voor de organisatie in die de gebruikers worden gemigreerd.

     >[!NOTE]
     >Om identiteitskaart van de Org, login aan de [ Admin Console ](https://adminconsole.adobe.com/) te krijgen en uw organisatie (in het hoger-juiste gebied) te kiezen als u tot meer dan één behoort. De organisatie-id staat in de URL van die pagina, in de notatie als `xx@AdobeOrg` , waarbij xx de IMS Org-id is. Afwisselend, kunt u identiteitskaart van de Org in de [ Adobe Developer Console ](https://developer.adobe.com/console/) pagina vinden waar u het Symbolische van de Toegang produceert.

   * **identiteitskaart van de Cliënt**: Ga identiteitskaart van de Cliënt in die u van de stap van de Opstelling bewaarde.

   * **Token van de Toegang**: Ga het Token van de Toegang in dat u van de stap van de Opstelling bewaarde.

     >[!NOTE]
     >De token Access verloopt elke 24 uur en er moet een nieuwe token worden gemaakt. Om een teken tot stand te brengen, ga terug in [ Adobe Developer Console ](https://developer.adobe.com/console/), kies uw project, klik **Beheer API van de Gebruiker**, en kleef de zelfde privé sleutel in de doos.

1. Na het bevolken van de gebieden, klik **Configuratie van de Test** om de verbinding aan de dienst van API van het Beheer van de Gebruiker te testen. Als de verbinding succesvol is, kunt u **sparen** klikken om de configuratie te bewaren.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access4.png)

1. Na het bewaren van de configuratie, selecteer de configuratie en klik **Toewijzing van de Gebruiker van het Begin**.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-landing4.png)

1. Klik **Begin** van de dialoogdoos zodat begint u het proces van de Toewijzing van de Gebruiker.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping3.png)

   Het toont de **Status** als **RUNNING**.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-start1.png)


1. Nadat de Toewijzing van de Gebruiker volledig is, klik **Resultaten** om de samenvatting te bekijken.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-landing5.png)

   >[!IMPORTANT]
   >
   >* Nadat de Toewijzing van de Gebruiker volledig is, kunt u terug naar de pagina van de Migratie van de Inhoud navigeren gebruikend breadcrumb. Op de kaart met gebruikerstoewijzing worden de status en het tijdstempel weergegeven. Klik **Overdracht van de Inhoud** zodat kunt u een migratie tot stand brengen die wordt geplaatst om extractie in werking te stellen. Zie [ Lopend het Hulpmiddel van de Overdracht van de Inhoud ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html#running-tool) voor meer details.

### De gebruikerstoewijzingsprocedure hervatten {#resume-user-mapping-process}

Als het proces voor het toewijzen van gebruikersgegevens is gestopt vanwege een van de volgende redenen:

* De optie **Toewijzing van de Gebruiker van het Einde** werd geselecteerd door de gebruiker.
* Het toegangstoken verstreek tijdens het proces.
* Of, een andere reden.

  >[!NOTE]
  >De voortgang wordt opgeslagen vanaf het punt waar het proces is gestopt.

Voer de onderstaande stappen uit om het proces voor het toewijzen van gebruikers te hervatten:

1. Klik **Logboek van de Mening** om het logboek van de Toewijzing van de Gebruiker te herzien zodat kunt u de bewaarde vooruitgang controleren.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping1.png)

1. Klik **knoop van de Toewijzing van de Gebruiker van het 0&rbrace; Begin opnieuw om van waar het weg verliet te hervatten.**

   >[!NOTE]
   >Zorg ervoor alvorens opnieuw te beginnen dat het toegangstoken nog geldig is of is verfrist.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping2.png)

1. Klik **Begin** van de dialoogdoos zodat hervat u het proces van de Toewijzing van de Gebruiker.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping3.png)

   Nadat het proces van de Afbeelding van de Gebruiker voltooit, kunt u de **Status** als **EINDELIJK** voor die specifieke configuratie bekijken.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping4.png)
