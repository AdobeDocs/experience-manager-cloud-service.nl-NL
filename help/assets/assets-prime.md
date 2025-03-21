---
title: Assets Prime
description: Meer informatie over belangrijke aspecten van Assets Prime, zoals belangrijke voordelen, gebruikerstypen en rechten.
feature: Asset Management
role: User, Admin
exl-id: 012f94c5-b1c3-4799-8eaf-af68d06c036f
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '1134'
ht-degree: 0%

---

# [!DNL Assets] as a Cloud Service Prime  {#assets-prime}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b> Dynamische Media Prime en Ultimate </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b> AEM Assets Ultimate </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b> integratie van AEM Assets met Edge Delivery Services </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b> Uitbreidbaarheid UI </b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuw </i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b> laat Dynamische Media Prime en Ultimate </b></a> toe
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b> Beste praktijken van het Onderzoek </b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b> Beste praktijken van Meta-gegevens </b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b> Content Hub </b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b> Dynamische Media met mogelijkheden OpenAPI </b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b> de ontwikkelaarsdocumentatie van AEM Assets </b></a>
        </td>
    </tr>
</table>

![ AEM Assets Prime banner image ](/help/assets/assets/aem-assets-prime-package-banner.png)

Assets as a Cloud Service Prime bevat een lichtgewicht DAM waarmee u verschillende belangrijke functies kunt uitvoeren, zoals:

* **het beheer van activa en de bibliotheekdiensten** &#x200B;: Hulpmiddelen die gebruikers toelaten om in te voeren, op te slaan, catalogus, controle te controleren, te beheren, en de digitale activa van een merk in een gecentraliseerde bewaarplaats te beheren

* **Onderzoek, Ontdekking, en Collaboration**: Hulpmiddelen die gebruikers toelaten om te doorbladeren, te ontdekken, te delen, en op activa samen te werken die zij rijke klantenervaringen moeten creëren.

* **Veiligheid &amp; Rights Management**: Hulpmiddelen om toegang, toestemmingen, rechten, en veiligheid te beheren om naleving, consistentie, en merkintegriteit te verzekeren.

* **de Verbindingen van Creative Cloud**: Hulpmiddelen die marketing &amp; creatieve teams toelaten om met vereenvoudigde toegang, commentaar, overzicht, en annotaties samen te werken om digitale activa bij te werken of te voltooien.

* **de Verbindingen van Experience Cloud**: Hulpmiddelen om inheemse toegang tot digitale activa van andere toepassingen en de diensten van Experience Cloud te steunen.

* **Poortervaring van de Distributie met geen rekbaarheidsopties (Content Hub)**: Hulpmiddelen om toegang tot de goedgekeurde digitale activa van een merk tot uitgebreide belanghebbenden uit te breiden om gebruik en merkconsistentie te verzekeren.

* **Integraties**: Integraties met andere toepassingen Adobe en niet-Adobe.

* **Dynamische Media (toe:voegen-op)**: Hulpmiddelen om beelden, video&#39;s, en andere opkomende inhoud voor rijke, interactieve, ervaringen van verschillende media voor om het even welk apparaat in schaal om te zetten en te leveren.

  >[!NOTE]
  >
  >Dynamic Media met OpenAPI-mogelijkheden, die u toegang biedt tot elementaire opties voor afbeeldingen zoals roteren, uitsnijden (alleen handmatig - geen slim uitsnijden), spiegelen, formaat, voorkeur, hoogte, breedte, kwaliteit, indeling en adaptieve videostreaming, is ook beschikbaar in Assets Prime. Neem contact op met het Adobe-accountteam voor meer informatie.

1. [ creeer een nieuw programma ](/help/journey-onboarding/create-program.md).

Nochtans, aangezien uw DAM behoeften groeien en u meer mogelijkheden, zoals, uitbreidbaarheid UI, API-gedreven automatisering, en plaatsing van de douanecode nodig hebt, moet u overwegen bevordering aan [ Assets Ultimate ](/help/assets/assets-ultimate-overview.md).

Dit artikel biedt een end-to-end workflow om Assets as a Cloud Service Prime in te schakelen.

## Assets as a Cloud Service Prime inschakelen{#enable-assets-prime}

Schakel Assets Prime in tijdens het maken van een nieuw programma met Cloud Manager. Voer de volgende stappen uit:

1. Meld u aan bij Cloud Manager als systeembeheerder. Zorg ervoor dat u de juiste organisatie selecteert terwijl u zich aanmeldt.

   >[!NOTE]
   >
   >Voeg een nieuw programma toe aan het juiste Cloud Manager-productprofiel. Voor meer informatie, zie [ Rol Gebaseerde Toestemmingen in Cloud Manager ](/help/onboarding/cloud-manager-introduction.md#role-based-permissions).

1. [ creeer een nieuw programma ](/help/journey-onboarding/create-program.md).

   Selecteer **[!UICONTROL Assets Prime]** op het tabblad **[!UICONTROL Solutions & Add-ons]** tijdens het maken van het nieuwe programma. U kunt **[!UICONTROL Assets Prime]** ook uitbreiden en selecteren **[!UICONTROL Content Hub]** om [ Content Hub ](/help/assets/product-overview.md) voor activadistributie toe te laten.

   ![ AEM Assets Ultimate ](assets/aem-assets-prime.png)


1. Klik op **[!UICONTROL Create]** om het programma te maken.

1. Klik op de programmakaart en klik op **[!UICONTROL Add Environment]** .

1. Geef de naam van de omgeving op, definieer een gebied en klik op **[!UICONTROL Save]** om de omgeving te maken.

   ![ voeg milieu aan Assets Prime ](assets/aem-assets-prime-add-environment.png) toe

>[!NOTE]
>
>Met Assets Prime kunt u alleen een productieomgeving maken. De optie Omgeving toevoegen is niet meer beschikbaar als de productieomgeving is voltooid.

Assets Prime is nu ingeschakeld voor Experience Manager Assets as a Cloud Service.

![ AEM Assets Prime is beschikbaar ](assets/aem-assets-prime-setup-complete.png)

Systeembeheerder heeft automatisch de machtiging als AEM-beheerder en ontvangt een e-mail om naar Admin Console te navigeren om productprofielen te beheren.


Uw AEM as a Cloud Service-exemplaar op Admin Console bestaat uit de volgende productprofielen:

* AEM-beheerders

* AEM-gebruikers

* [AEM Assets Collaborator-gebruikers](#onboard-collaborator-users)

* [AEM Assets Power Users](#onboard-power-users)


![ Profielen van het Product van AEM Assets ](assets/aem-assets-product-profiles.png)

U kunt gebruikers of gebruikersgroepen toevoegen aan de productprofielen AEM Assets Collaborator Users en AEM Assets Power Users. Voor meer informatie, zie [ aan boord de gebruikers van de Medewerker van AEM Assets ](#onboard-collaborator-users) en [ aan boord van de Macht van AEM Assets gebruikers ](#onboard-power-users).

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

## On-board AEM Assets Collaborator-gebruikers {#onboard-collaborator-users}

Gebruikers van AEM Assets Collaborator kunnen samenwerken met middelen van Experience Manager via integratie van Assets die beschikbaar is voor uw organisatie in andere Adobe-producten en niet-Adobe-toepassingen, middelen maken en bewerken met ingebouwde Adobe Express en Firefly die gebruikmaken van professioneel ontworpen sjablonen, merkpakketten, Adobe Stock-middelen enzovoort, en goedgekeurde middelen van uw organisatie benaderen en benutten via AEM Assets Content Hub Portal.

Aan boord van Collaborator-gebruikers:

1. Open Experience Manager Assets-productprofielen door op de AEM as a Cloud Service-productnaam in de lijst met producten op Admin Console te klikken.

1. Klik op de productieauteur-instantie voor AEM as a Cloud Service:
   ![ de profielen van het Product voor AEM as a Cloud Service ](assets/aem-cloud-service-instances.png)

1. Klik op het gebruikersprofiel van Medewerkers en klik op **[!UICONTROL Add users]** om de gebruiker aan het productprofiel toe te voegen.
   ![ het productprofiel van de Gebruiker ](assets/aem-assets-collaborator-user-permissions.png)

1. Klik op **[!UICONTROL Save]** om de wijzigingen op te slaan.

U kunt ook toegang krijgen tot de services die zijn toegewezen aan gebruikers van Medewerkers, zoals wordt weergegeven in de volgende afbeelding:

![ de Diensten voor de gebruikers van de Medewerker ](assets/aem-assets-collaborator-users.png)

`Adobe Express` - en `AEM Assets Collaborator Users` -services zijn standaard ingeschakeld. U kunt de schakeloptie naar wens in- en uitschakelen. Adobe raadt echter aan de standaardservices te gebruiken die zijn ingeschakeld voor de productprofielen.

## Ingebouwde AEM Assets Power-gebruikers {#onboard-power-users}

AEM Assets Power-gebruikers hebben toegang tot alle AEM Assets-mogelijkheden, waaronder het beheer van middelen, machtigingen, metagegevens en het algemene beheer en de automatisering rond digitale middelen, werken met middelen van Experience Manager via de integratie van Assets die beschikbaar is voor uw organisatie in andere Adobe- en niet-Adobe-toepassingen, maken en bewerken van middelen met behulp van ingebouwde Adobe Express en Firefly, waarbij gebruik wordt gemaakt van professioneel ontworpen sjablonen, merkkits, Adobe Stock-middelen enzovoort, en toegang krijgen tot en gebruik maken van goedgekeurde middelen van uw organisatie via AEM Assets vanuit uw organisatie via de portal voor Content Hub.

Aan boord van stroomgebruikers:

1. Open Experience Manager Assets-productprofielen door op de AEM as a Cloud Service-productnaam in de lijst met producten op Admin Console te klikken.

1. Klik op de productieauteur-instantie voor AEM as a Cloud Service:
   ![ de profielen van het Product voor AEM as a Cloud Service ](assets/aem-cloud-service-instances.png)

1. Klik op het productprofiel voor Power-gebruikers en klik op **[!UICONTROL Add users]** om de gebruiker aan het productprofiel toe te voegen.
   ![ het productprofiel van de Gebruiker ](assets/aem-assets-power-user-permissions.png)

1. Klik op **[!UICONTROL Save]** om de wijzigingen op te slaan.

U kunt ook toegang krijgen tot de services die zijn toegewezen aan Power-gebruikers en deze weergeven, zoals in de volgende afbeelding wordt getoond:

![ de Diensten voor de gebruikers van de Macht ](assets/aem-assets-power-users.png)

`Adobe Express` - en `AEM Assets Power Users` -services zijn standaard ingeschakeld. U kunt de schakeloptie naar wens in- en uitschakelen. Adobe raadt echter aan de standaardservices te gebruiken die zijn ingeschakeld voor de productprofielen.
