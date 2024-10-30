---
title: Assets Premier
description: Meer informatie over belangrijke aspecten van Assets Premier, zoals belangrijke voordelen, gebruikerstypen en privileges.
feature: Asset Management
role: User, Admin
source-git-commit: f033efd954ea7f9d27a891bfb9c0226e9d9c1432
workflow-type: tm+mt
source-wordcount: '1055'
ht-degree: 0%

---

# [!DNL Assets] as a Cloud Service  {#assets-prime}

| [ Beste praktijken van het Onderzoek ](/help/assets/search-best-practices.md) | [](/help/assets/metadata-best-practices.md) | [](/help/assets/product-overview.md) | [](/help/assets/dynamic-media-open-apis-overview.md) | [](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

![](/help/assets/assets/aem-assets-prime-package-banner.png)

Assets as a Cloud Service Prime includes a lightweight DAM that enables you to perform various key capabilities, such as:

* ****

* ****

* ****

* ****

* ****

* **Poortervaring van de Distributie met geen rekbaarheidsopties (Content Hub)**: Hulpmiddelen om toegang tot de goedgekeurde digitale activa van een merk tot uitgebreide belanghebbenden uit te breiden om gebruik en merkconsistentie te verzekeren.

* **Integraties**: Integraties met andere Adobe en niet-Adobe toepassingen.

* **Dynamic Media (toe:voegen-op)**: Hulpmiddelen om beelden, video&#39;s, en andere opkomende inhoud voor rijke, interactieve, ervaringen van verschillende media voor om het even welk apparaat in schaal om te zetten en te leveren.

[](/help/assets/assets-ultimate-overview.md)

This article provides an end-to-end workflow to enable Assets as a Cloud Service Prime.

## Enable Assets as a Cloud Service Prime{#enable-assets-prime}

Enable Assets Prime  while creating a new program using Cloud Manager. Execute the following steps:

1. As a system administrator, log on to Cloud Manager. Zorg ervoor dat u de juiste organisatie selecteert terwijl u zich aanmeldt.

   >[!NOTE]
   >
   >Voeg een nieuw programma toe aan het juiste Cloud Manager-productprofiel. Voor meer informatie, zie [ Rol Gebaseerde Toestemmingen in Cloud Manager ](/help/onboarding/cloud-manager-introduction.md#role-based-permissions).

1. [](/help/journey-onboarding/create-program.md)

   **[!UICONTROL Solutions & Add-ons]****[!UICONTROL Assets Prime]** **[!UICONTROL Assets Prime]****[!UICONTROL Content Hub]**[](/help/assets/product-overview.md)

   ![](assets/aem-assets-prime.png)


1. **[!UICONTROL Create]**

1. **[!UICONTROL Add Environment]**

1. **[!UICONTROL Save]**

   ![](assets/aem-assets-prime-add-environment.png)

>[!NOTE]
>
>Assets Prime only allows you to create a production environment. The option to Add environment is no longer available once the production environment is created successfully.

Assets Prime is now enabled for Experience Manager Assets as a Cloud Service.

![](assets/aem-assets-prime-setup-complete.png)

Systeembeheerder heeft automatisch de machtiging als AEM beheerder en ontvangt een e-mail om naar de Admin Console te navigeren om productprofielen te beheren.


Uw AEM as a Cloud Service-exemplaar op Admin Console bestaat uit de volgende productprofielen:

* AEM Administrators

* AEM Users

* [AEM Assets Collaborator Users](#onboard-collaborator-users)

* [AEM Assets Power Users](#onboard-power-users)


![](assets/aem-assets-product-profiles.png)

U kunt gebruikers of gebruikersgroepen toevoegen aan de productprofielen AEM Assets Collaborator Users en AEM Assets Power Users. Voor meer informatie, zie [ aan boord de gebruikers van de Medewerker van AEM Assets ](#onboard-collaborator-users) en [ aan boord van de Macht van AEM Assets gebruikers ](#onboard-power-users).

Als u Content Hub for Assets as a Cloud Service hebt ingeschakeld, wordt een nieuwe instantie gemaakt in AEM Assets as a Cloud Service on Admin Console met `delivery` als achtervoegsel:

![ Nieuwe instantie voor Content Hub ](assets/new-instance-content-hub.png)

>[!NOTE]
>
>Als u Content Hub vóór 14 augustus 2024 hebt ingericht, wordt de nieuwe instantie gemaakt met `contenthub` als achtervoegsel.

`author``publish`

`AEM Assets Limited Users`

![](assets/content-hub-product-profile.png)

You can start adding users or user groups to this product profile to provide them access to Content Hub.

>[!NOTE]
>
>`contenthub``Limited Users``delivery`

## On-board AEM Assets Collaborator-gebruikers {#onboard-collaborator-users}

Gebruikers van AEM Assets Collaborator kunnen samenwerken met middelen van Experience Manager via integratie van Assets die beschikbaar is voor uw organisatie in andere Adobe producten en toepassingen die geen Adobe zijn, middelen maken en bewerken met behulp van ingebouwde Adobe Express en Firefly, waarbij gebruik wordt gemaakt van professioneel ontworpen sjablonen, merkpakketten, Adobe Stock-middelen enzovoort, en goedgekeurde middelen van uw organisatie benaderen en benutten via AEM Assets Content Hub Portal.

Aan boord van Collaborator-gebruikers:

1. Access Experience Manager Assets product profiles by clicking the AEM as a Cloud Service product name in the list of products on Admin Console.

1. Click the production author instance for AEM as a Cloud Service:
   ![](assets/aem-cloud-service-instances.png)

1. **[!UICONTROL Add users]**
   ![](assets/aem-assets-collaborator-user-permissions.png)

1. **[!UICONTROL Save]**

U kunt ook toegang krijgen tot de services die zijn toegewezen aan gebruikers van Medewerkers, zoals wordt weergegeven in de volgende afbeelding:

![ de Diensten voor de gebruikers van de Medewerker ](assets/aem-assets-collaborator-users.png)

`Adobe Express``AEM Assets Collaborator Users` You can turn the toggle off and on, as per your requirements, however, Adobe recommends to use the default services enabled for the product profiles.

## Onboard AEM Assets Power users {#onboard-power-users}

AEM Assets Power users can access all AEM Assets capabilities including managing assets, permissions, metadata and the overall governance and automation around digital assets, work with assets from Experience manager via integrations of Assets available to your organization in other Adobe and non-Adobe applications, create and edit assets using built-in Adobe Express and Firefly leveraging professionally designed templates, brand kits, Adobe Stock assets, and so on, and access and leverage approved assets from your organization using AEM Assets Content Hub portal.

To onboard Power users:

1. Access Experience Manager Assets product profiles by clicking the AEM as a Cloud Service product name in the list of products on Admin Console.

1. Click the production author instance for AEM as a Cloud Service:
   ![](assets/aem-cloud-service-instances.png)

1. **[!UICONTROL Add users]**
   ![](assets/aem-assets-power-user-permissions.png)

1. **[!UICONTROL Save]**

You can also access and view the services assigned to Power users, as depicted in the following image:

![ de Diensten voor de gebruikers van de Macht ](assets/aem-assets-power-users.png)

`Adobe Express` - en `AEM Assets Power Users` -services zijn standaard ingeschakeld. U kunt de schakeloptie naar wens in- en uitschakelen, maar de Adobe raadt u aan de standaardservices te gebruiken die zijn ingeschakeld voor de productprofielen.
