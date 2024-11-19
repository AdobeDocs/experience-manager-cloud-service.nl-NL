---
title: Assets goedkeuren voor Content Hub
description: Leer hoe u middelen in Assets as a Cloud Service goedkeurt om ze beschikbaar te maken in Content Hub.
exl-id: fc849028-ab56-4388-b8d6-e36cac8f868f
source-git-commit: ed7331647ea2227e6047e42e21444b743ee5ce6d
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 0%

---

# Assets goedkeuren voor Content Hub {#approve-assets-content-hub}

| [ Beste praktijken van het Onderzoek ](/help/assets/search-best-practices.md) | [ Beste praktijken van Meta-gegevens ](/help/assets/metadata-best-practices.md) | [ Content Hub ](/help/assets/product-overview.md) | [ Dynamic Media met mogelijkheden OpenAPI ](/help/assets/dynamic-media-open-apis-overview.md) | [ de ontwikkelaarsdocumentatie van AEM Assets ](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

![ keur activa voor Content Hub ](assets/content-hub-approve-assets.png) goed

>[!AVAILABILITY]
>
>Content Hub-gids is nu beschikbaar in de PDF-indeling. Download de volledige handleiding en gebruik Adobe Acrobat AI Assistant om je vragen te beantwoorden.
>
>[!BADGE  de PDF van de Gids van Content Hub ]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/content-hub.pdf"}

Merkbeheerders en marketeers houden strikte controle over merkmiddelen. Alleen goedgekeurde en nieuwste versie van het middel is beschikbaar voor gebruik in Content Hub, zodat alle kanalen en toepassingen consistent zijn.

Met AEM Assets as a Cloud Service kunt u middelen goedkeuren om het beheer van bedrijfsmiddelen te stroomlijnen, zodat een gecontroleerd en efficiënt proces voor de verwerking van bedrijfsmiddelen wordt gegarandeerd.

## Voordat u begint {#pre-requisites}

Voordat u begint, moet u beschikken over:

* Toegang tot AEM Assets as a Cloud Service

* Schrijf toestemmingen om activa meta-gegevens uit te geven om het **[!UICONTROL Status]** gebied beschikbaar in [ activa eigenschappen ](/help/assets/manage-organize-assets-view.md##manage-asset-status) voor een activa uit te geven.

## Assets goedkeuren voor Content Hub{#approve-assets-for-content-hub}

De elementen die zijn gemarkeerd als `approved` in Assets as a Cloud Service, zijn automatisch beschikbaar in Content Hub.

>[!NOTE]
>
Assets as a Cloud Service en Content Hub moeten dezelfde organisatie gebruiken om de middelen in Content Hub weer te geven.

De elementstatus instellen op `approved` in de Assets-weergave in AEM as a Cloud Service:

1. Selecteer het element en klik op **[!UICONTROL Details]** op de werkbalk.

1. Selecteer op het tabblad **[!UICONTROL Basic]** de elementstatus als `approved` in de vervolgkeuzelijst **[!UICONTROL Status]** .
1. Klik op **[!UICONTROL Save]**.

   >[!VIDEO](https://video.tv.adobe.com/v/3433172)

Als u activa gebruikend mening Admin moet goedkeuren, zie [ activa goedkeuren gebruikend mening Admin ](/help/assets/approve-assets.md#approve-assets).

## Bulk activa voor Content Hub goedkeuren met de Assets-weergave {#bulk-approve-assets-content-hub}

Bulk keurt activa goed gebruikend de mening van Assets voor AEM Assets as a Cloud Service. Alle in bulk goedgekeurde activa worden vervolgens beschikbaar in Content Hub.

Om het in bulk goed te keuren activa binnen een omslag in de mening van Assets:

1. Selecteer de elementen en klik op **[!UICONTROL Bulk Metadata Edit]** .

1. Selecteer **[!UICONTROL Approved]** in het **[!UICONTROL Status]** -veld dat beschikbaar is in de sectie [!UICONTROL Properties] in het rechterdeelvenster.

1. Klik op **[!UICONTROL Save]**.

## Goedkeuring van nieuw opgenomen elementen automatiseren in de beheerweergave {#automate-approval-newly-ingested-assets}

Nadat u van de Assets-weergave naar de Admin-weergave bent overgeschakeld, kunt u mapinstellingen zodanig instellen dat alle nieuwe elementen die aan de map zijn toegevoegd, automatisch worden goedgekeurd.

U kunt op de volgende manieren schakelen tussen de weergaven Beheer en Assets:
![ Mijn overzicht van Workspace ](assets/assets-view.png)

Voer de volgende stappen uit om goedkeuring voor nieuw opgenomen elementen in [!DNL Experience Manager Admin view] te automatiseren:

1. Maak een map in de ontwerpomgeving (https://author-pXXX-eYYY.adobeaemcloud.com). Vervang _XXX_ met uw programma identiteitskaart en _JJJ_ met milieu identiteitskaart van de Experience Manager.
1. Navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Profiles]** .
1. Klik op **[!UICONTROL Create]** rechtsboven op de pagina.
1. Voeg een profieltitel toe en klik op **[!UICONTROL Create]** . Het metagegevensprofiel is gemaakt.
1. Selecteer het nieuwe metagegevensprofiel en klik op **[!UICONTROL Edit _(e)_]** . <br> Het **[!UICONTROL Edit Metadata Profile]** -formulier wordt geopend met de tab **[!UICONTROL Basic]** gemarkeerd.
1. Sleep een **[!UICONTROL Single Line Text Field]** van de sectie **[!UICONTROL Build Form]** naar de rechterkant van de sectie Metagegevens in het formulier.
1. Klik op het veld dat u zojuist hebt toegevoegd en voer de volgende updates uit in het deelvenster **[!UICONTROL Settings]** :
   1. Verander **[!UICONTROL Field Label]** in _Goedgekeurde Assets_.
   1. Werk **[!UICONTROL Map to property]** aan _bij./jcr:content/metadata/dam:status_.
   1. Verander de Standaardwaarde in _goedgekeurd_.

1. Klik op **[!UICONTROL Save]**.
1. Selecteer op de pagina **[!UICONTROL Metadata Profiles]** het nieuwe metagegevensprofiel.
1. Klik op **[!UICONTROL Apply Metadata Profile to Folder(s)]** in de bovenste actiebalk.
1. Selecteer de map(pen) die u wilt goedkeuren en klik op **[!UICONTROL Apply]** .
   <br> De machtiging voor de gehele map wordt ingesteld op goedkeuring en alle middelen die naar deze map worden geüpload, worden automatisch goedgekeurd.

   >[!VIDEO](https://video.tv.adobe.com/v/3427431)

>[!NOTE]
> 
Met deze methode worden de nieuwe elementen in de map goedgekeurd. Voor bestaande elementen in de map moet u deze handmatig selecteren en goedkeuren.

## Middelen beheren die met Content Hub zijn geüpload {#manage-assets-uploaded-using-content-hub}

[ de gebruikers van Content Hub met rechten om activa ](/help/assets/deploy-content-hub.md#onboard-content-hub-users-add-assets) toe te voegen kunnen [ activa aan Content Hub ](/help/assets/upload-brand-approved-assets.md) of van lokaal dossiersysteem of de invoeractiva van OneDrive of de gegevensbronnen van de Dropbox toevoegen. Alle middelen worden op het hoogste niveau weergegeven in Content Hub, ongeacht de mapstructuur die beschikbaar is op uw lokale bestandssysteem of de gegevensbronnen OneDrive en Dropbox om de zoekmogelijkheden te verbeteren.

De vertoning van activa die gebruikend Content Hub worden geupload hangt af van als u [ de auto-goedkeuringsknevel ](/help/assets/configure-content-hub-ui-options.md#configure-import-options-content-hub) hebt toegelaten:

* Als de schakeloptie **[!UICONTROL Auto-approval]** is ingeschakeld, zijn de elementen die u uploadt met Content Hub automatisch beschikbaar.

* Als de schakeloptie **[!UICONTROL Auto-approval]** is uitgeschakeld, worden de elementen die u uploadt met Content Hub niet automatisch weergegeven. De middelen zijn beschikbaar in de `hydrated-assets` map van uw as a Cloud Service omgeving van Assets. Navigeer aan de omslag en [ bulkgeef ](#bulk-approve-assets-content-hub) het statuut van die activa `Approved` voor die activa uit om in Content Hub te tonen.

![ Content Hub goedkeuringsproces ](/help/assets/assets/content-hub-approval.png)
