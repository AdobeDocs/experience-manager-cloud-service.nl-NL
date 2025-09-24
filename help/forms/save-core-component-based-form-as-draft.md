---
title: Hoe te om de op componenten gebaseerde Aangepaste Vorm van de Kern te bewaren als ontwerp en de component van Concepten en van Verzending te gebruiken om concepten en bijdragen te vermelden?
description: Leer hoe u op kerncomponenten gebaseerde adaptieve formulieren als concept opslaat. Begrijp ook hoe te om de component van Concepten en van Verzending aan lijstconcepten en voorlegging voor het programma geopende gebruikers te gebruiken?
feature: Adaptive Forms, Core Components
exl-id: c0653bef-afeb-40c1-b131-7d87ca5542bc
role: User, Developer
source-git-commit: 8f1fa3a95f232f34ad6ae89c391e9e2272a2c072
workflow-type: tm+mt
source-wordcount: '1319'
ht-degree: 0%

---


# Formulieren opslaan als concepten en deze weergeven op de pagina Sites

<!--This article provides information about the Auto-save feature, which is currently available as a pre-release feature. The pre-release feature is accessible only through our [pre-release channel](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/prerelease#new-features).-->

Neem bijvoorbeeld een gebruiker die begint met het invullen van een formulier, maar later moet pauzeren en terugsturen. AEM biedt een optie `save-as-draft` waarmee de gebruiker het formulier kan opslaan als concept dat later kan worden ingevuld. Om dit te vergemakkelijken, verstrekt AEM de **Concepten &amp; van de Verzending** de Poortcomponent van Forms uit de doos, die concepten en voorlegging op de pagina&#39;s van AEM Sites toont. De component bevat formulieren die zijn opgeslagen als concepten die later kunnen worden ingevuld, en formulieren die zijn verzonden. Alleen aangemelde gebruikers kunnen hun concepten bewerken of hun verzonden formulieren weergeven. Nochtans, als een anonieme gebruiker door de lijst van vormen navigeert gebruikend de **component van het Onderzoek &amp; van het Registreren** en een vorm als ontwerp opslaat, wordt dat ontwerp niet vermeld door de **Concepten &amp; van Submissies** component. Gebruikers moeten zich bij het verzenden van het formulier hebben aangemeld om concepten en verzendingen weer te geven.

![ pictogram Concepten ](assets/drafts-component.png)

## Voorwaarden

* Installeer de nieuwste versie om Adaptive Forms Core Components in te schakelen voor uw AEM Cloud Service-omgeving.

  Nadat u de nieuwste Core Components in uw omgeving hebt geïmplementeerd, zijn de Forms Portal-componenten toegankelijk in uw ontwerpomgeving.

* [ vorm Azure Opslag en Verenigde Schakelaar van de Opslag voor Concepten &amp; de Portaalcomponent van Forms van de Verzending ](#configure-azure-storage-and-unified-storage-connector-for-drafts--submissions-forms-portal-component)

### Azure Storage- en Unified Storage-connector configureren voor concepten en verzendingen voor Forms Portal-component

De **componenten van Concepten &amp; van Verzending** heeft een opslagopstelling voor het bewaren van en het van een lijst maken van concepten op de pagina van AEM Sites nodig. De Unified Storage Connector biedt een framework om AEM te koppelen aan externe opslag. Als u het formulier wilt opslaan als concept, zorgt u ervoor dat u een Azure-opslagaccount en een toegangstoets hebt om toegang tot het [!DNL Azure] -opslagaccount te verlenen. Eenmaal beschikt u over een Azure-opslagaccount en de toegangstoets, voert u de volgende stappen uit om een Azure-opslagconfiguratie te maken:

1. Navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Azure Storage]** .

   ![ Azure selectie van de Kaart van de Opslag ](/help/forms/assets/save-form-as-draft-azure-card.png)

1. Selecteer een configuratiemap om de configuratie te maken en selecteer **[!UICONTROL Create]** .

   ![ Uitgezochte de Omslag van de Configuratie van de Azure Opslag ](/help/forms/assets/save-form-as-draft-select-config-folder.png)

1. Geef een titel voor de configuratie op in het veld **[!UICONTROL Title]** .
1. Geef de naam van de [!DNL Azure] -opslagaccount op in de velden **[!UICONTROL Azure Storage Account]** en **[!UICONTROL Azure Access Key]** .

   ![ Azure Configuratie van de Opslag ](/help/forms/assets/save-form-as-draft-azure-storage.png)

   Typ `Connection String` in het tekstvak `Azure Storage Account` en `Azure Key` in het tekstvak `Azure Access key` .

1. Klik **sparen**.

   >[!NOTE]
   >
   > U kunt **[!UICONTROL Azure Storage Account]** en **[!UICONTROL Azure Access Key]** van [ Microsoft Azure Portal ](https://learn.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage?tabs=azure-portal) terugwinnen.

   Nadat u de Azure Storage Configuration hebt gemaakt, configureert u de Unified Storage Connector voor Forms Portal met de volgende stappen:

1. Navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Forms]** > **[!UICONTROL Unified Storage Connector]** .

   ![ Verenigde schakelaarOpslag ](/help/forms/assets/save-form-as-draft-unified-connector.png)

1. Selecteer **[!UICONTROL Forms Portal]** in de vervolgkeuzelijst **[!UICONTROL Azure]** in de sectie **[!UICONTROL Storage]** .
1. Geef het configuratiepad voor de Azure-opslagconfiguratie op in het veld **[!UICONTROL Storage Configuration Path]** .

   ![ Verenigde schakelaarOpslag die ](/help/forms/assets/save-form-as-draft-unified-connector-storage.png) plaatst

1. Selecteer **[!UICONTROL Save]** .

>[!NOTE]
>
> Als u een andere opslagoptie dan Azure moet configureren, schrijft u vanuit uw officiële e-mailadres naar aem-forms-ea@adobe.com met uw gedetailleerde vereisten.

Zodra u met succes de Schakelaar van de Opslag van de Azure en van de Verenigde Opslag voor het opslaan van de concepten en voorgelegde vormen hebt gevormd, voeg de **Concepten &amp; van de Verzending** component op de pagina van AEM Sites toe.

## Hoe kunt u de component Concepten en verzendingen toevoegen aan een AEM Sites-pagina?

U kunt uit-van-de-doos componenten van Forms Portal gebruiken om concepten en bijdragen op de pagina van Plaatsen een lijst te maken. Voer de volgende stappen uit om de **Concepten &amp; Submissions** poortcomponent toe te voegen:

1. Open de pagina van AEM Sites op een **geeft** wijze uit.
1. Ga naar **[!UICONTROL Page Information]** > **[!UICONTROL Edit Template]**
   ![ geef malplaatjebeleid ](/help/forms/assets/save-form-as-draft-edit-template.png) uit

1. Klik **[!UICONTROL Policy]** en selecteer **[!UICONTROL Drafts & Submissions]** checkbox onder de **[Naam van het Project van het Archetype van AEM ] - Forms en Communicatie Portaal**.

   ![ de Selectie van het Beleid ](/help/forms/assets/save-form-as-draft-enable-policy.png)

1. Klik op **[!UICONTROL Done]**.
1. Open de AEM Sites-pagina nu opnieuw in de ontwerpmodus.
1. Zoek de sectie in de pagina-editor waarin u de Forms Portal-component kunt toevoegen.
1. Klik **toevoegen** pictogram. Het pictogram is een plusteken (+) waarmee u nieuwe componenten kunt toevoegen.

   Het klikken **voegt** pictogram toe toont een **Nieuwe de dialoogdoos van de Component van het Tussenvoegsel** die diverse componenten voor toevoeging toont.

   >[!NOTE]
   >
   > U kunt ook de component slepen en neerzetten.

1. Blader door de beschikbare componenten in het dialoogvenster en selecteer de gewenste component in de lijst. Bijvoorbeeld, selecteer de **componenten van Concepten &amp; van Verzending** van de lijst om de **Concepten &amp; van Verzending** Forms Portal component toe te voegen.

   ![ voeg Ontwerp en de Component van de Verzending ](/help/forms/assets/save-form-as-draft-add-dns.png) toe

Nu, vorm de eigenschappen van de **Concepten en de component van Verzending** volgens de vereisten.

## Eigenschappen van de component Concepten en verzendingen configureren

U kunt de eigenschappen van de **Concepten &amp; Verzendingen** vormen:
1. Selecteer de **componenten van Concepten &amp; van Verzending**.
1. Klik ![ vormen pictogram ](assets/configure_icon.png) en de dialoogdoos verschijnt.
1. Geef in het dialoogvenster **[!UICONTROL Drafts and Submissions]** het volgende op:
   * **Titel** om een component in een pagina van Plaatsen en door gebrek te identificeren, verschijnt de titel bovenop de component.
   * **Uitgezochte Type**: Om op de vormlijst als ontwerp of voorgelegde vormen te wijzen. Als u **Ontwerp Forms** kiest, worden de vormen bewaard als concepten getoond. Alternatief, die **voorgelegde Forms** selecteren toont de vormen die door het programma geopende gebruikers worden voorgelegd.
   * **Lay-out**: Om de vormen van het lijstontwerp of voorgelegde vormen in het kaart of lijstformaat te tonen.

   ![ eigenschappen van het Ontwerp en van de Component van de Verzending ](/help/forms/assets/save-form-as-draft-dns-properties.png)

## Formulieren configureren om op te slaan als concepten

U kunt Adaptive Forms op de volgende twee manieren configureren om deze als concepten voor later gebruik op te slaan:
* [Handeling door gebruiker](#user-action)
* [Automatisch opslaan](#auto-save)

### Handeling door gebruiker

>[!NOTE]
>
> Zorg ervoor dat de [ versie van de Componenten van de Kern aan 3.0.24 of later ](https://github.com/adobe/aem-core-forms-components) wordt geplaatst om vormen als concepten te bewaren gebruikend **sparen de regel van de Vorm**.

Om een vorm als Ontwerp te bewaren, creeer a **sparen de regel van de Vorm** op een vormcomponent, zoals een knoop. Wanneer op de knop wordt geklikt, wordt de regel geactiveerd en wordt het formulier opgeslagen als concept. Voer de volgende stappen uit om a **sparen de regel van de Vorm** op een knoopcomponent tot stand te brengen:

1. Open een adaptief formulier in de bewerkingsmodus.
1. Selecteer het **[!UICONTROL Edit Rules]** pictogram om de Redacteur van de Regel voor de **2&rbrace; component van de Knoop &lbrace;te openen.**
1. Selecteer **[!UICONTROL Create]** om de regel voor knoop te vormen en tot stand te brengen.
1. In de **[!UICONTROL When]** sectie, wordt de uitgezochte **geklikt** en in de **[!UICONTROL Then]** sectie, selecteert **sparen Vorm** optie.
1. Selecteer **[!UICONTROL Done]** om de regel op te slaan.

   ![ creeer regel voor knoop ](/help/forms/assets/save-form-as-drfat-create-rule.png)

Wanneer u voorproef een Aangepast Vorm, vult het uit, en klikt **sparen Vorm** knoop, wordt de vorm bewaard als ontwerp.

### Concepten

>[!NOTE]
>
> Zorg ervoor dat de [ versie van de Componenten van de Kern aan 3.0.52 of later ](https://github.com/adobe/aem-core-forms-components) wordt geplaatst om vormen als concepten te bewaren gebruikend de auto sparen eigenschap.

U kunt ook een adaptief formulier zo configureren dat het automatisch wordt opgeslagen op basis van een gebeurtenis op basis van een tijd, zodat u zeker weet dat het formulier na de opgegeven duur wordt opgeslagen. Wanneer u [ de Poortcomponenten van Forms voor uw milieu ](/help/forms/list-forms-on-sites-page.md#enable-forms-portal-components-for-your-existing-environment) toelaat, **Auto sparen** tabel verschijnt in de containereigenschappen van Forms. U kunt de functie voor automatisch opslaan configureren voor een adaptief formulier:

1. Open in de auteur een adaptief formulier in de bewerkingsmodus.
1. Open de browser Inhoud en selecteer de component **[!UICONTROL Guide Container]** van het adaptieve formulier.
1. Klik de eigenschappen van de Container van de Gids ![ eigenschappen van de Gids ](/help/forms/assets/configure-icon.svg) pictogram en open het **[!UICONTROL Drafts]** lusje.

   ![ auto-sparen ](/help/forms/assets/auto-save.png)

1. Schakel het selectievakje **[!UICONTROL Automatically Save Drafts]** in om het formulier automatisch op te slaan als concepten.
1. Vorm **[!UICONTROL Save Preference]** als **sparen concepten met regelmatige intervallen**, om de vorm <!--based on the occurrence of an event or--> na een specifiek tijdsinterval automatisch te bewaren.
1. Geef het tijdsinterval in **[!UICONTROL Save interval frequency (Seconds)]** op om de duur in te stellen waarmee het automatisch opslaan van het formulier met het gedefinieerde interval wordt geactiveerd.
1. Klik op **[!UICONTROL Done]**.

## Concepten/verzonden formulieren op de pagina Sites weergeven met de component Concepten en verzendingen

Om opgeslagen ontwerpen of voorgelegde vormen te bekijken, gebruik de **Concepten &amp; van Indieningen** de Poortcomponent van Forms.
Wanneer **[!UICONTROL Select Type]** als **Concept Forms** in [ wordt geselecteerd vormt dialoog van de componenten Concepten &amp; van Verzending ](#configure-properties-of-the-drafts--submissions-component), verschijnen de vormen bewaard als concepten op de pagina van Plaatsen. U kunt de concepten openen door op de ellips (...) te klikken om het formulier in te vullen.

![ pictogram Concepten ](assets/drafts-component.png)

Wanneer **[!UICONTROL Select Type]** als **Voorgelegde Forms** in [ wordt geselecteerd vormt dialoog van de componenten van Concepten &amp; van Verzending ](#configure-properties-of-the-drafts--submissions-component), verschijnen de voorgelegde vormen. U kunt de verzonden formulieren weergeven, maar niet bewerken.

![ het pictogram van Verzending ](assets/submission-listing.png)

U kunt de formulieren ook verwijderen door te klikken op de ellips (...) in de rechterbenedenhoek van het formulier.

>[!NOTE]
>
> In de lijst Verzending in het Forms Portal worden alleen formulierverzendingen weergegeven die zijn gebaseerd op basis van Stichting.

## Volgende stappen

In het volgende artikel, laat ons [ leren hoe te om verwijzingen naar vormen op de pagina van Plaatsen toe te voegen gebruikend de Component van Forms Portal van de Verbinding ](/help/forms/add-form-link-to-aem-sites-page.md).

## Verwante artikelen

{{forms-portal-see-also}}

## Zie ook {#see-also}

{{see-also}}