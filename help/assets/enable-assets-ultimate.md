---
title: Assets Ultimate inschakelen
description: Leer hoe u Assets Ultimate kunt inschakelen voor nieuwe en bestaande klanten.
feature: Asset Management
role: User, Admin
exl-id: 45cd8ccd-e5cf-42cd-aa7f-4ae59d0587f7
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '1362'
ht-degree: 0%

---

# [!DNL Assets] as a Cloud Service Ultimate inschakelen {#enable-assets-cloud-service-ultimate}

![ Verbetering aan Activa Cloud Service Ultimate ](/help/assets/assets/upgrade-assets-cs-ultimate-package-banner.png)

Met Assets as a Cloud Service Ultimate kunt u verschillende belangrijke DAM-mogelijkheden uitvoeren, zoals beheer van bedrijfsmiddelen en bibliotheekservices, beheer van beveiliging en rechten, Creative- en Experience Cloud-verbindingen, uitbreidbaarheid van de gebruikersinterface, API-gestuurde automatisering, integratie met Adobe- en niet-Adobe-toepassingen, aangepaste code-implementatie en nog veel meer. Zie [ Assets as a Cloud Service Ultimate Overzicht ](/help/assets/assets-ultimate-overview.md) voor de volledige lijst.

## Assets Ultimate inschakelen {#enable-assets-ultimate}

Nieuwe Assets as a Cloud Service-klanten moeten Assets Ultimate eerst inschakelen door een nieuw programma te maken met Cloud Manager.

Voer de volgende stappen uit:

1. Meld u aan bij Cloud Manager als systeembeheerder. Zorg ervoor dat u de juiste organisatie selecteert terwijl u zich aanmeldt.

   >[!NOTE]
   >
   >Voeg een nieuw programma toe aan het juiste Cloud Manager-productprofiel. Voor meer informatie, zie [ Rol Gebaseerde Toestemmingen in Cloud Manager ](/help/onboarding/cloud-manager-introduction.md#role-based-permissions).

1. [ creeer een nieuw programma ](/help/journey-onboarding/create-program.md) en [ voeg milieu&#39;s ](/help/journey-onboarding//create-environments.md) aan het toe.

   Selecteer **[!UICONTROL Assets Ultimate]** op het tabblad **[!UICONTROL Solutions & Add-ons]** tijdens het maken van het nieuwe programma. U kunt **[!UICONTROL Assets Ultimate]** ook uitbreiden en selecteren **[!UICONTROL Content Hub]** om [ Content Hub ](/help/assets/product-overview.md) voor activadistributie toe te laten.

   ![ AEM Assets Ultimate ](assets/aem-assets-ultimate-solutions.png)

1. Klik op **[!UICONTROL Create]** om het programma te maken. Assets Ultimate is nu ingeschakeld voor Experience Manager Assets as a Cloud Service.

De systeembeheerder heeft automatisch de bevoegdheid als AEM-beheerder op Assets Ultimate en ontvangt een e-mail om naar Admin Console te navigeren om de beschikbare productprofielen te beheren.

Uw AEM as a Cloud Service-exemplaar op Admin Console bestaat uit de volgende productprofielen:

* AEM-beheerders

* AEM-gebruikers

* [AEM Assets Collaborator-gebruikers](#onboard-collaborator-users)

* [AEM Assets Power Users](#onboard-power-users)

  ![ Profielen van het Product van AEM Assets ](assets/aem-assets-product-profiles.png)

Als u Content Hub for Assets as a Cloud Service hebt ingeschakeld, wordt in AEM Assets as a Cloud Service op Admin Console een nieuwe instantie gemaakt met `delivery` als achtervoegsel:

![ Nieuwe instantie voor Content Hub ](assets/new-instance-content-hub.png)

>[!NOTE]
>
>Als u Content Hub vóór 14 augustus 2024 hebt ingericht, wordt de nieuwe instantie gemaakt met `contenthub` als achtervoegsel.

De instantienaam voor Content Hub bevat geen `author` of `publish` .

Klik op de instantienaam om het `AEM Assets Limited Users` Content Hub-productprofiel te bekijken.

![ het productprofiel van Content Hub ](assets/content-hub-product-profile.png)

U kunt gebruikers of gebruikersgroepen aan dit productprofiel toevoegen om hen toegang tot Content Hub te verlenen.

>[!NOTE]
>
>Als u Content Hub vóór 14 augustus 2024 hebt ingericht, wordt het Content Hub-productprofiel `contenthub` vermeld na `Limited Users` in plaats van `delivery` .

## Assets Ultimate inschakelen voor bestaande klanten {#enable-assets-ultimate-existing-customers}

Bestaande Assets as a Cloud Service-klanten kunnen een upgrade uitvoeren naar Assets Ultimate door twee eenvoudige stappen uit te voeren. U kunt naar het Assets as a Cloud Service-programma in Cloud Manager navigeren en de status van de upgrade bekijken op de Program Card op basis van de beschikbaarheid van Assets Ultimate-credits. Als er voldoende credits beschikbaar zijn voor een upgrade naar Assets Ultimate, kunt u de status `Assets license upgrade required` zien, zoals in de volgende afbeelding wordt getoond:

![ de verbetering van AEM Assets aan Assets Ultimate ](assets/aem-assets-upgrade-status-ultimate.png)

Als een bestaande klant een nieuwe licentie aanschaft voor Assets Ultimate, wordt de upgrademoestand weergegeven als `Assets license upgrade available` .

### Vereisten voor upgrade {#prerequisites-assets-upgrade}

Alle omgevingen moeten worden geüpgraded naar de nieuwste AEM as a Cloud Service-releaseversie of minimaal een `2024.10.18175` releaseversie. Als u niet aan de minimumvereisten voldoet, neemt u contact op met uw Adobe-vertegenwoordiger om over te schakelen naar de vereiste AEM-releaseversie.

### Upgrade uitvoeren naar Assets Ultimate {#upgrade-assets-ultimate}

Voer de volgende stappen uit:

1. Klik op de naam van het programma nadat u hebt overgeschakeld naar de minimale vereisten voor de AEM-releaseversie. Een upgradekaart wordt net boven **[!UICONTROL Environments]** -sectie weergegeven, zoals in de volgende afbeelding wordt getoond:

   ![ de verbetering van AEM Assets aan Assets Ultimate ](assets/aem-assets-upgrade-card.png)

1. Klik op **[!UICONTROL Add Product Profiles]**. Cloud Manager geeft opties weer om nieuwe productprofielen toe te voegen aan alle omgevingen die beschikbaar zijn in het programma of de afzonderlijke omgevingen.

   ![ de verbeteringsopties van AEM Assets ](assets/aem-assets-upgrade-options.png)

1. Klik op **[!UICONTROL All Environments]** om de nieuwe productprofielen toe te voegen aan alle omgevingen in het programma of op **[!UICONTROL Individual Environments]** om de nieuwe productprofielen toe te voegen aan geselecteerde omgevingen.

   Als u op **[!UICONTROL Individual Environments]** klikt, wordt de lijst met alle omgevingen weergegeven die in het programma beschikbaar zijn.

1. Klik op het pictogram Meer opties voor een omgeving en selecteer **[!UICONTROL Add Product Profiles]** om de nieuwe productprofielen aan de geselecteerde omgeving toe te voegen.

   ![ AEM Assets uitgezochte individuele milieu&#39;s ](assets/aem-assets-individual-environments.png)

   U kunt productprofielen ook aan geselecteerde omgevingen toevoegen door naar de sectie **[!UICONTROL Environments]** te navigeren, op het pictogram Meer opties voor een omgeving te klikken en **[!UICONTROL Add Product Profiles]** te selecteren.

   De status van de omgeving wordt weergegeven `Adding Product Profiles` terwijl de nieuwe productprofielen worden toegevoegd en vervolgens `Running` weergegeven wanneer het proces is voltooid.

   U moet productprofielen toevoegen aan alle omgevingen die in het programma beschikbaar zijn, afzonderlijk of in alle omgevingen tegelijk, voordat u de volgende stap uitvoert.

1. Klik op **[!UICONTROL Upgrade]**. De optie **[!UICONTROL Upgrade]** wordt alleen weergegeven wanneer u productprofielen toevoegt aan alle beschikbare omgevingen.

   ![ Laatste stap in het verbeteringsproces ](assets/aem-assets-upgrade-button.png)

   Het upgradeproces is voltooid en u hebt uw Assets as a Cloud Service geüpgraded naar Assets Ultimate. De status van het programma wordt weergegeven `Assets Ultimate` .

   ![ status van het Programma na verbetering ](assets/program-status-post-upgrade.png)

Het AEM as a Cloud Service-exemplaar op Admin Console bevat nu de volgende productprofielen:

* AEM-beheerders

* AEM-gebruikers

* [AEM Assets Collaborator-gebruikers](#onboard-collaborator-users)

* [AEM Assets Power Users](#onboard-power-users)

![ Profielen van het Product van AEM Assets ](assets/aem-assets-product-profiles.png)

Als Content Hub ingeschakeld moet zijn, klikt u op het pictogram Meer opties (...) op de naam van het programma in Cloud Manager en selecteert u **[!UICONTROL Edit Program]** . Vouw **[!UICONTROL Assets Ultimate]** uit en klik op **[!UICONTROL Content Hub]** . Met deze stap wordt de Content Hub for Assets Ultimate ingeschakeld. Er is een nieuwe instantie gemaakt in AEM Assets as a Cloud Service op Admin Console met `delivery` als achtervoegsel:

![ Nieuwe instantie voor Content Hub ](assets/new-instance-content-hub.png)

>[!NOTE]
>
>Als u Content Hub vóór 14 augustus 2024 hebt ingericht, wordt de nieuwe instantie gemaakt met `contenthub` als achtervoegsel.

De instantienaam voor Content Hub bevat geen `author` of `publish` .

Klik op de instantienaam om het `AEM Assets Limited Users` Content Hub-productprofiel te bekijken.

![ het productprofiel van Content Hub ](assets/content-hub-product-profile.png)

U kunt gebruikers of gebruikersgroepen aan dit productprofiel toevoegen om hen toegang tot Content Hub te verlenen.

>[!NOTE]
>
>Als u Content Hub vóór 14 augustus 2024 hebt ingericht, wordt het Content Hub-productprofiel `contenthub` vermeld na `Limited Users` in plaats van `delivery` .

## On-board AEM Assets Collaborator-gebruikers {#onboard-collaborator-users}

Gebruikers van AEM Assets Collaborator kunnen samenwerken met middelen van Experience Manager via integratie van Assets die beschikbaar is voor uw organisatie in andere Adobe-producten en niet-Adobe-toepassingen, middelen maken en bewerken met ingebouwde Adobe Express en Firefly die gebruikmaken van professioneel ontworpen sjablonen, merkpakketten, Adobe Stock-middelen enzovoort, en goedgekeurde middelen van uw organisatie benaderen en benutten via AEM Assets Content Hub Portal.

Aan boord van Collaborator-gebruikers:

1. Open Experience Manager Assets-productprofielen door op de AEM as a Cloud Service-productnaam in de lijst met producten op Admin Console te klikken.

1. Klik op de productieauteur-instantie voor AEM as a Cloud Service:
   ![ de profielen van het Product voor AEM as a Cloud Service ](assets/aem-cloud-service-instances.png)

1. Klik op het gebruikersprofiel Deelnemers en klik op **[!UICONTROL Add users]** om gebruikers of gebruikersgroepen toe te voegen aan het productprofiel.
   ![ het productprofiel van de Gebruiker ](assets/aem-assets-collaborator-user-permissions.png)

1. Klik op **[!UICONTROL Save]** om de wijzigingen op te slaan.

U kunt ook toegang krijgen tot de services die zijn toegewezen aan gebruikers van Medewerkers, zoals wordt weergegeven in de volgende afbeelding:

![ de Diensten voor de gebruikers van de Medewerker ](assets/aem-assets-collaborator-users.png)

`Adobe Express` - en `AEM Assets Collaborator Users` -services zijn standaard ingeschakeld.

>[!NOTE]
>
>U kunt de schakeloptie in- en uitschakelen om de beschikbare services in of uit te schakelen. Hiervoor wordt echter aangeraden de standaardservices te gebruiken die zijn ingeschakeld voor de productprofielen.


## Ingebouwde AEM Assets Power-gebruikers {#onboard-power-users}

AEM Assets Power-gebruikers hebben toegang tot alle AEM Assets-mogelijkheden, waaronder het beheer van middelen, machtigingen, metagegevens en het algemene beheer en de automatisering rond digitale middelen, werken met middelen van Experience Manager via de integratie van Assets die beschikbaar is voor uw organisatie in andere Adobe- en niet-Adobe-toepassingen, maken en bewerken van middelen met behulp van ingebouwde Adobe Express en Firefly, waarbij gebruik wordt gemaakt van professioneel ontworpen sjablonen, merkkits, Adobe Stock-middelen enzovoort, en toegang krijgen tot en gebruik maken van goedgekeurde middelen van uw organisatie via AEM Assets vanuit uw organisatie via de portal voor Content Hub.

Aan boord van stroomgebruikers:

1. Open Experience Manager Assets-productprofielen door op de AEM as a Cloud Service-productnaam in de lijst met producten op Admin Console te klikken.

1. Klik op de productieauteur-instantie voor AEM as a Cloud Service:
   ![ de profielen van het Product voor AEM as a Cloud Service ](assets/aem-cloud-service-instances.png)

1. Klik op het productprofiel voor Power-gebruikers en klik op **[!UICONTROL Add users]** om gebruikers of gebruikersgroepen toe te voegen aan het productprofiel.
   ![ het productprofiel van de Gebruiker ](assets/aem-assets-power-user-permissions.png)

1. Klik op **[!UICONTROL Save]** om de wijzigingen op te slaan.

U kunt ook toegang krijgen tot de services die zijn toegewezen aan Power-gebruikers en deze weergeven, zoals in de volgende afbeelding wordt getoond:

![ de Diensten voor de gebruikers van de Macht ](assets/aem-assets-power-users.png)

`Adobe Express` - en `AEM Assets Power Users` -services zijn standaard ingeschakeld.

>[!NOTE]
>
>U kunt de schakeloptie in- en uitschakelen om de beschikbare services in of uit te schakelen. Hiervoor wordt echter aangeraden de standaardservices te gebruiken die zijn ingeschakeld voor de productprofielen.
