---
title: Publicatie beheren
description: Elementen publiceren naar of verwijderen uit Experience Manager Assets, Dynamic Media en Brand Portal
mini-toc-levels: 1
feature: Asset Management, Publishing, Collaboration, Asset Processing
role: User, Architect, Admin
exl-id: 691a0925-0061-4c62-85ac-8257b96dddf2
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: tm+mt
source-wordcount: '1545'
ht-degree: 2%

---

# Publicaties beheren in Experience Manager Assets {#manage-publication-in-aem}

Als [!DNL Adobe Experience Manager Assets] beheerder, kunt u activa en omslagen publiceren die activa van uw auteursinstantie aan bevatten [!DNL Experience Manager Assets], [!DNL Dynamic Media], en [!DNL Brand Portal]. Ook kunt u plannen om een middel of een omslag op een recentere datum of een tijd te publiceren. Na publicatie kunnen de gebruikers de elementen openen en verder verspreiden onder andere gebruikers. Standaard kunt u elementen en mappen publiceren naar [!DNL Experience Manager Assets]. U kunt echter configureren [!DNL Experience Manager Assets] publiceren inschakelen in [[!DNL Dynamic Media]](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/config-dm.html) en [[!DNL Brand Portal]](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/brand-portal/configure-aem-assets-with-brand-portal.html).

U kunt elementen op het niveau van middelen of mappen publiceren of de publicatie ervan ongedaan maken met **[!UICONTROL Quick Publish]** of **[!UICONTROL Manage Publication]** beschikbaar in het dialoogvenster [!DNL Experience Manager Assets] interface. Als u volgende wijzigingen aanbrengt in het oorspronkelijke middel of de oorspronkelijke map in [!DNL Experience Manager Assets], worden de wijzigingen pas in het publicatieexemplaar doorgevoerd als u het document opnieuw publiceert vanaf [!DNL Experience Manager Assets]. Hiermee zorgt u ervoor dat wijzigingen die in uitvoering zijn, niet beschikbaar zijn in het publicatieexemplaar. Alleen goedgekeurde wijzigingen die door een beheerder zijn gepubliceerd, zijn beschikbaar in de publicatie-instantie.

* [Elementen publiceren met Snel publiceren](#quick-publish)
* [Elementen publiceren met Publicatie beheren](#manage-publication)
* [Assets later publiceren](#publish-assets-later)
* [Elementen publiceren naar Dynamic Media](#publish-assets-to-dynamic-media)
* [Assets publiceren naar Brand Portal](#publish-assets-to-brand-portal)
* [Aanvraag voor publicatie](#request-publication)
* [Beperkingen en tips](#limitations-and-tips)

## Elementen publiceren met Snel publiceren {#quick-publish}

Met Snel publiceren kunt u inhoud direct naar het geselecteerde doel publiceren. Van de [!DNL Experience Manager Assets] navigeer naar de bovenliggende map en selecteer alle elementen of mappen die u wilt publiceren. Klikken **[!UICONTROL Quick Publish]** in de werkbalk en selecteert u in de vervolgkeuzelijst de bestemming waar u de elementen wilt publiceren.

![Snel publiceren](assets/quick-publish-to-aem.png)

## Elementen publiceren met Publicatie beheren {#manage-publication}

Met Publicatie beheren kunt u inhoud publiceren naar of verwijderen uit de geselecteerde bestemming. [inhoud toevoegen](#add-content) naar de publicatielijst vanuit de DAM-opslagplaats, [inclusief mapinstellingen](#include-folder-settings) om inhoud van de geselecteerde omslagen te publiceren en filters toe te passen, en [publiceren plannen](#publish-assets-later) naar een latere datum of tijd.

Van de [!DNL Experience Manager Assets] navigeer naar de bovenliggende map en selecteer alle elementen of mappen die u wilt publiceren. Klikken **[!UICONTROL Manage Publication]** van de werkbalk. Als u geen [!DNL Dynamic Media] en [!DNL Brand Portal] geconfigureerd in uw [!DNL Experience Manager Assets] kunt u elementen en mappen alleen publiceren naar [!DNL Experience Manager Assets].

![Publicatie beheren](assets/manage-publication-aem.png)

De volgende opties zijn beschikbaar in de [!UICONTROL Manage Publication] interface:

* [!UICONTROL Actions]
   * `Publish`: Elementen en mappen publiceren naar het geselecteerde doel
   * `Unpublish`: Verwijder elementen en mappen van het doel

* [!UICONTROL Destination]
   * `Publish`: Elementen en mappen publiceren naar [!DNL Experience Manager Assets] (`AEM`)
   * `Dynamic Media`: Elementen publiceren naar [!DNL Dynamic Media]
   * `Brand Portal`: Elementen en mappen publiceren naar [!DNL Brand Portal]

* [!UICONTROL Scheduling]
   * `Now`: Elementen direct publiceren
   * `Later`: Elementen publiceren op basis van de `Activation` datum of tijd

Klik op **[!UICONTROL Next]**. Op basis van de selectie **[!UICONTROL Scope]** bevat verschillende opties. De opties voor **[!UICONTROL Add Content]** en **[!UICONTROL Include Folder Settings]** zijn alleen beschikbaar voor het publiceren van elementen en mappen naar [!DNL Experience Manager Assets] (`Destination: Publish`).

![Publicatiebereik beheren](assets/manage-publication-aem-scope.png)

### Inhoud toevoegen {#add-content}

Publiceren naar [!DNL Experience Manager Assets] Hiermee kunt u meer inhoud (elementen en mappen) toevoegen aan de publicatielijst. U kunt meer elementen of mappen aan de lijst toevoegen via de opslagplaatsen voor dam. Klikken **[!UICONTROL Add Content]** om meer inhoud toe te voegen.

U kunt meerdere elementen uit een map toevoegen of meerdere mappen tegelijk toevoegen. U kunt echter geen elementen uit meerdere mappen tegelijk toevoegen.

![Inhoud toevoegen](assets/manage-publication-add-content.png)

### Inclusief mapinstellingen {#include-folder-settings}

Een map publiceren naar [!DNL Experience Manager Assets] publiceert alle elementen, submappen en de bijbehorende referenties.

Als u de mapinhoud wilt filteren die u wilt publiceren, klikt u op **[!UICONTROL Include Folder Settings]**:

* `Include folder contents`

   * Ingeschakeld: alle elementen van de geselecteerde map, submappen (inclusief alle elementen van de submappen) en verwijzingen worden gepubliceerd.
   * Uitgeschakeld: alleen de geselecteerde map (leeg) en verwijzingen worden gepubliceerd. De elementen van de geselecteerde map worden niet gepubliceerd.

* `Include folder contents` en `Include only immediate folder contents`

  Als beide opties zijn geselecteerd, worden alle elementen van de geselecteerde map, submappen (leeg) en verwijzingen gepubliceerd. De elementen van de submappen worden niet gepubliceerd.

<!--
* [!UICONTROL Include only immediate folder contents]: Only the subfolders content and references are published. 

Only the selected folder content and references are published.
-->

![Inclusief mapinstellingen](assets/manage-publication-include-folder-settings.png)

Nadat u de filters hebt toegepast, klikt u op **[!UICONTROL OK]** en klik vervolgens op **[!UICONTROL Publish]**. Als u op de knop Publiceren klikt, verschijnt er een bevestigingsbericht `Resource(s) have been scheduled for publication` wordt weergegeven. En de geselecteerde activa en (of) omslagen worden gepubliceerd aan de bepaalde bestemming die op de planner (`Now` of `Later`). Meld u aan bij uw publicatieexemplaar om te controleren of de middelen en (of) mappen zijn gepubliceerd.

![Publiceren naar AEM](assets/manage-publication-publish-aem.png)

In de bovenstaande illustratie kunt u verschillende waarden zien voor de **[!UICONTROL Publish Target]** kenmerk. Laten we niet vergeten dat u voor publicatie hebt gekozen tot [!DNL Experience Manager Assets] (`Destination: Publish`). Waarom toont het dan aan dat alleen een map en een middel worden gepubliceerd naar `AEM`en de andere twee activa voor beide worden gepubliceerd `AEM` en `Dynamic Media`?

Hier moet u de rol van mapeigenschappen begrijpen. Een map **[!UICONTROL Dynamic Media Publishing mode]** eigendom speelt een belangrijke rol bij de publicatie . Als u de eigenschappen van een map wilt weergeven, selecteert u een map en klikt u op **[!UICONTROL Properties]** op de werkbalk. Zie de eigenschappen van de bovenliggende map voor een element.

In de volgende tabel wordt uitgelegd hoe de publicatie plaatsvindt afhankelijk van de definitie **[!UICONTROL Destination]** en **[!UICONTROL Dynamic Media Publish mode]**:

| [!UICONTROL Destination] | [!UICONTROL Dynamic Media Publish mode] | [!UICONTROL Publish Target] | Toegestane inhoud |
| --- | --- | --- | --- |
| Publicatie | Selectieve publicatie | `AEM` | Middelen en mappen |
| Publicatie | Meteen | `AEM` en `Dynamic Media` | Middelen en mappen |
| Publicatie | Bij activering | `AEM` en `Dynamic Media` | Middelen en mappen |
|  Dynamic Media  | Selectieve publicatie | `Dynamic Media` | Assets |
|  Dynamic Media  | Meteen | `None` | Kan de elementen niet publiceren |
|  Dynamic Media  | Bij activering | `None` | Kan de elementen niet publiceren |

>[!NOTE]
>
>Alleen elementen worden gepubliceerd naar [!DNL Dynamic Media].
>
>Een map publiceren naar [!DNL Dynamic Media] wordt niet ondersteund.
>
>Als u een map selecteert (`Selective Publish`) en kiest u de [!DNL Dynamic Media] doel, de [!UICONTROL Publish Target] kenmerk spiegelt `None`.


Laten we nu de **[!UICONTROL Destination]** in het bovenstaande geval **[!UICONTROL Dynamic Media]** en verifieert u de resultaten. Op die manier wordt alleen de `Selective Publish` map is gepubliceerd naar [!DNL Dynamic Media]. De activa van `Immediate` en `Upon Activation` mappen worden niet gepubliceerd en weerspiegelen `None`.

![Publiceren naar Dynamic Media](assets/manage-publication-dynamic-media.png)

>[!NOTE]
>
>Indien [!DNL Dynamic Media] is niet geconfigureerd op uw [!DNL Experience Manager Assets] en de **[!UICONTROL Destination]** is **[!UICONTROL Publish]**, worden de elementen en mappen altijd gepubliceerd naar `AEM`.
>
>Publiceren naar [!DNL Brand Portal] is onafhankelijk van de mapeigenschappen. Alle elementen, mappen en verzamelingen kunnen naar Brand Portal worden gepubliceerd. Zie [middelen publiceren naar Brand Portal](#publish-assets-to-brand-portal).

>[!NOTE]
>
>Als u de [!DNL Manage Publication] kunt u de bestaande functies blijven gebruiken.
>
>U kunt de bestaande aanpassing echter verwijderen om de nieuwe [!DNL Manager Publication] functies.

## Assets later publiceren {#publish-assets-later}

De publicatieworkflow van elementen op een latere datum of tijd plannen:

1. Van de [!UICONTROL Experience Manager Assets] navigeer naar de bovenliggende map en selecteer alle elementen of mappen die u voor publicatie wilt plannen.
1. Klikken **[!UICONTROL Manage Publication]** van de werkbalk.
1. Klikken **[!UICONTROL Publish]** van **[!UICONTROL Action]** en selecteert u vervolgens de **[!UICONTROL Destination]** waar u de inhoud wilt publiceren.
1. Selecteer **[!UICONTROL Later]** vanuit **[!UICONTROL Scheduling]**.
1. Selecteer een **[!UICONTROL Activation date]** en de datum en tijd specificeren. Klik op **[!UICONTROL Next]**.

   ![Publicatieworkflow beheren](assets/manage-publication-workflow.png)

1. In de **[!UICONTROL Scope]** tab, **[!UICONTROL Add Content]** (indien nodig). Klik op **[!UICONTROL Next]**.
1. In de **[!UICONTROL Workflows]** , geeft u een titel voor de workflow op. Klik op **[!UICONTROL Publish Later]**.

   ![Titel werkstroom](assets/manage-publication-workflow-title.png)

   Meld u aan bij de doelinstantie om de gepubliceerde elementen te controleren (afhankelijk van de geplande datum of tijd).

## Elementen publiceren naar Dynamic Media {#publish-assets-to-dynamic-media}

Alleen elementen worden gepubliceerd naar [!DNL Dynamic Media]. Het publicatiegedrag verschilt echter op basis van de mapeigenschappen. Een map kan **[!UICONTROL Dynamic Media Publish mode]** geconfigureerd voor selectieve publicatie die een van de volgende mogelijkheden kan hebben:

* `Selective Publish`
* `Immediate`
* `Upon Activation`

Het publicatieproces voor **[!UICONTROL Immediate]** en **[!UICONTROL Upon Activation]** De modus is echter consistent, maar anders voor **[!UICONTROL Selective Publish]**. Zie [selectieve publicatie op mapniveau in Dynamic Media configureren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/selective-publishing.html). Nadat u selectief publiceren in een omslag vormt, kunt u om het even welke volgend doen:

* [Elementen selectief publiceren naar Dynamic Media of Experience Manager met Publicatie beheren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/selective-publishing.html?lang=en#selective-publish-manage-publication)
* [Publicatie van middelen van Dynamic Media of Experience Manager selectief ongedaan maken met Publicatie beheren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/selective-publishing.html?lang=en#selective-unpublish-manage-publication)
* [Elementen publiceren naar Dynamic Media of Experience Manager met Snel publiceren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/selective-publishing.html?lang=en#quick-publish-aem-dm)
* [Elementen selectief publiceren of de publicatie ervan ongedaan maken via zoekresultaten](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/selective-publishing.html?lang=en#selective-publish-unpublish-search-results)

## Assets publiceren naar Brand Portal {#publish-assets-to-brand-portal}

U kunt elementen, mappen en verzamelingen publiceren naar de [!DNL Experience Manager Assets Brand Portal] -instantie.

* [Assets publiceren naar Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/brand-portal/publish-to-brand-portal.html?lang=en#publish-assets-to-bp)
* [Mappen publiceren naar Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/brand-portal/publish-to-brand-portal.html?lang=en#publish-folders-to-brand-portal)
* [Verzamelingen publiceren naar Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/brand-portal/publish-to-brand-portal.html?lang=en#publish-collections-to-brand-portal)

## Aanvraag voor publicatie {#request-publication}

De `Request Publication` Deze optie helpt de workflow van Elementen te verifiëren voordat deze worden gepubliceerd op [!DNL AEM] Elementenomgeving. [!DNL AEM] biedt verschillende machtigingsniveaus voor verschillende gebruikers. U kunt een *contribuant* die elementen uploadt, maar deze pas kunnen publiceren nadat de uploads zijn geverifieerd. Ook als u een *Beheerder* u kunt workflows van de Elementen lezen en schrijven.

De optie Publicatie aanvragen is beschikbaar voor de volgende gebruikers:

* **Medewerker:** Als u een gebruiker bent die kan bijdragen aan [!DNL AEM] Middelen, dan hebt u beperkte toegang tot de [!DNL AEM] Workflow Elementen. `Manage publication` is verborgen voor u. Als medewerker kunt u alleen een bijdrage leveren door Elementen toe te voegen, maar u kunt deze niet publiceren of hebt geen leestoegang tot de workflow.

* **Werkstroomgebruiker:** Deze gebruiker kan geen elementen publiceren, maar heeft wel leestoegang tot de workflow. Als workflowgebruiker kunt u het volgende doen:
   * verzoek om publicatie
   * weergave `Manage publication` knop
   * de workflow plannen en de opties bekijken `schedule now` en `schedule later`

* **Beheerder:** Als beheerder kunt u de algemene workflowstappen voor de Middelen beheren. `Manage publication` is zichtbaar voor u. Als de bestemming `publish` is geselecteerd, kunt u later een element voor de workflowstap plannen.

>[!NOTE]
>
>Indien [!DNL Dynamic Media] is geselecteerd als een doel en wordt vervolgens de workflowstap uitgeschakeld voor **workflowgebruiker** en **admin** gebruikers.
>

## Beperkingen en tips {#limitations-and-tips}

* `Manage publication` is beschikbaar voor de gebruikers die beschikken over ten minste Leesmachtigingen voor de workflow.
* Lege mappen worden niet gepubliceerd.
* Als u een element publiceert dat wordt verwerkt, wordt alleen de oorspronkelijke inhoud gepubliceerd. De uitvoeringen ontbreken. Wacht tot de verwerking is voltooid en publiceer het element of publiceer het opnieuw nadat de verwerking is voltooid.
* Verwijder tijdens het verwijderen van de publicatie van een complex element alleen de publicatie van het element. Maak de publicatie van de referenties niet ongedaan, omdat ze door andere gepubliceerde elementen kunnen worden doorverwezen.
