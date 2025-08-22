---
title: Hoe kunt u formulierkoppelingen toevoegen op de AEM Sites-pagina met behulp van de Link Forms Portal-component?
description: Leer hoe u koppelingen naar formulieren toevoegt aan de AEM Sites-pagina.
feature: Adaptive Forms, Core Components
role: User, Developer, Admin
exl-id: a55d0776-8827-46cc-9625-5d6f5f6bda3b
source-git-commit: 16b1e7ffa4e3812e9207bb283c63029939f7d14e
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---

# Formulierkoppelingen toevoegen aan sitepagina

In het scenario van de bankenwebsite, verbetert de **Portaal van de Verbinding** de component van Forms navigatie door gebruikers aan specifieke vormen over diverse secties van de plaats te leiden. Het bevat directe verwijzingen naar formulieren zoals aanvragen voor leningen, formulieren voor het openen van accounts of feedbackenquêtes, die strategisch op de hele website worden geplaatst. De **component van de Verbinding** neemt verbindingen op die gebruikers aan specifieke Aanpassings Forms binnen de pagina van Plaatsen leiden. Zo hebben anonieme gebruikers op de website van de bank toegang tot een algemeen onderzoeksformulier, terwijl aangemelde gebruikers rechtstreeks toegang hebben tot veiligere formulieren, zoals leningsaanvragen of formulieren voor het verlenen van vergunningen voor transacties.

![ het pictogram van de Verbinding ](/help/forms/assets/link-forms.png)

## Voorwaarde

Voordat u de verschillende mogelijkheden van een Forms Portal-component gaat verkennen, moet u ervoor zorgen dat Core Components geschikt zijn voor uw omgeving. Installeer de nieuwste versie om Adaptive Forms Core Components in te schakelen voor uw AEM Cloud Service-omgeving.

Nadat u de nieuwste Core Components in uw omgeving hebt geïmplementeerd, zijn de Forms Portal-componenten toegankelijk in uw ontwerpomgeving.

## De component Koppeling toevoegen aan uw sitepagina

Om de **poortcomponent van de Verbinding** &lbrace;aan uw pagina van Plaatsen toe te voegen, voer de volgende stappen uit:

1. Open de pagina van AEM Sites op een **geeft** wijze uit.
1. Ga naar **[!UICONTROL Page Information]** > **[!UICONTROL Edit Template]**
   ![ geef malplaatjebeleid ](/help/forms/assets/save-form-as-draft-edit-template.png) uit

1. Klik **[!UICONTROL Policy]** en selecteer **[!UICONTROL Link]** checkbox onder de **[Naam van het Project van het Archetype van AEM ] - Forms en Communicatie Portaal**.

   ![ de Selectie van het Beleid ](/help/forms/assets/add-link.png)

1. Klik op **[!UICONTROL Done]**.
1. Open nu de AEM Sites-pagina opnieuw in de ontwerpmodus.
1. Zoek de sectie in de pagina-editor waarin u de Forms Portal-component kunt toevoegen.

1. Klik **toevoegen** pictogram. Het pictogram is een plusteken (+) waarmee u nieuwe componenten kunt toevoegen.

   Het klikken **voegt** pictogram toe toont een **Nieuwe de dialoogdoos van de Component van het Tussenvoegsel** die diverse componenten voor toevoeging toont.

   >[!NOTE]
   >
   > U kunt ook de component slepen en neerzetten.

1. Blader door de beschikbare componenten in het dialoogvenster en selecteer de gewenste component in de lijst. Bijvoorbeeld, selecteer de **component van de Verbinding** van de lijst om de **Component van de Verbinding** van Forms Portal toe te voegen component.

   ![ component van de Verbinding ](/help/forms/assets/add-link-in-sites.png)

Nu, vorm de eigenschappen van de **component van de Verbinding**.

## Begrijp de eigenschappen van de component van de Verbinding

U kunt **eigenschappen van de 1&rbrace; component van de Verbinding &lbrace;gemakkelijk aanpassen gebruikend Configure Dialoog voor een naadloze gebruikerservaring.** Om te vormen, selecteer de component en selecteer dan ![ pictogram ](assets/configure_icon.png) vormen. Het dialoogvenster **[!UICONTROL Link]** wordt geopend.

### Tabblad weergeven

![ het Lusje van de Vertoning ](/help/forms/assets/link-asset-tab.png)

Geef op het tabblad **[!UICONTROL Display]** het bijschrift en de knopinfo voor koppelingen op om de formulieren die door de koppeling worden vertegenwoordigd, gemakkelijker te kunnen identificeren.

### Tabblad Informatie over element

![ het Lusje van Info van Assets ](/help/forms/assets/link-asset-info.png)

Geef op het tabblad **[!UICONTROL Asset Info]** het pad naar de opslagplaats op waar het element wordt opgeslagen.

### Zoekparameters, tabblad

![ het Lusje van de Params van de Vraag ](/help/forms/assets/link-query-tab.png)

Geef op het tabblad **[!UICONTROL Query Params]** de aanvullende parameters op in de indeling sleutelwaardepaar. Wanneer op de koppeling wordt geklikt, worden deze aanvullende parameters doorgegeven en samen met het formulier doorgegeven.

## Formulierkoppelingen op de pagina Sites weergeven met de component Link

Voorproef de pagina van Plaatsen om de verbinding aan een Aangepaste Vorm te bekijken, die in het **Info van Assets** eigenschappen lusje van de **&#x200B;**&#x200B;component van de Verbinding wordt gespecificeerd. Als u op de koppeling klikt, wordt het formulier op het scherm weergegeven voor gebruikers die het op basis van de machtigingen kunnen openen.

![ het Lusje van de Params van de Vraag ](/help/forms/assets/link-forms.png)

## Verwante artikelen

{{forms-portal-see-also}}

## Zie ook {#see-also}

{{see-also}}
