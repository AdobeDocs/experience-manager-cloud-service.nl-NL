---
title: Assets goedkeuren voor Content Hub
description: Leer hoe u middelen in Assets as a Cloud Service goedkeurt om ze beschikbaar te maken in Content Hub.
exl-id: fc849028-ab56-4388-b8d6-e36cac8f868f
source-git-commit: ba73cc52c337d16a2cd33438eb568adcabd492dd
workflow-type: tm+mt
source-wordcount: '1208'
ht-degree: 0%

---

# Assets goedkeuren voor Content Hub {#approve-assets-content-hub}

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

![ keur activa voor Content Hub ](assets/content-hub-approve-assets.png) goed

>[!AVAILABILITY]
>
>Content Hub-gids is nu beschikbaar in PDF-indeling. Download de volledige handleiding en gebruik Adobe Acrobat AI Assistant om je vragen te beantwoorden.
>
>[!BADGE &#x200B; de Gids PDF van Content Hub &#x200B;]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/content-hub.pdf"}

Merkbeheerders en marketeers houden strikte controle over merkmiddelen. Alleen goedgekeurde en nieuwste versie van het middel is beschikbaar voor gebruik in Content Hub, zodat alle kanalen en toepassingen consistent zijn.

Met AEM Assets as a Cloud Service kunt u middelen goedkeuren om het beheer van bedrijfsmiddelen te stroomlijnen, zodat u verzekerd bent van een gecontroleerd en efficiënt proces voor het verwerken van bedrijfsmiddelen.

## Voordat u begint {#pre-requisites}

Voordat u begint, moet u beschikken over:

* Toegang tot AEM Assets as a Cloud Service

* Schrijf toestemmingen om activa meta-gegevens uit te geven om het **[!UICONTROL Status]** gebied beschikbaar in [ activa eigenschappen ](/help/assets/manage-organize-assets-view.md##manage-asset-status) voor een activa uit te geven.

## Assets goedkeuren voor Content Hub{#approve-assets-for-content-hub}

De elementen die in Assets as a Cloud Service als `approved` zijn gemarkeerd, zijn automatisch beschikbaar in Content Hub.

>[!NOTE]
>
>Assets as a Cloud Service en Content Hub moeten dezelfde organisatie gebruiken om de middelen in Content Hub weer te geven.

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

## Goedkeuringsdoel instellen {#set-approval-target}

De mening van Assets laat u toe om goedgekeurde activa aan Dynamische Media met mogelijkheden OpenAPI, Content Hub, of allebei te publiceren die op de waarde worden gebaseerd die u op het **gebied van het Doel van de Goedkeuring** beschikbaar op de pagina van de Details van Activa plaatst.

Goedkeuringsdoel instellen:

1. Selecteer het element en klik op **[!UICONTROL Details]** op de werkbalk.

1. Selecteer op het tabblad **[!UICONTROL Basic]** de elementstatus in de vervolgkeuzelijst **[!UICONTROL Status]** . Mogelijke waarden zijn Goedgekeurd, Afgewezen en Geen status (standaardwaarde).

1. Als u **Goedgekeurd** in stap 2 selecteert, selecteer een goedkeuringsdoel. Mogelijke waarden zijn Delivery en Content Hub.

   * **Levering** is de standaardoptie die in het drop-down menu wordt geselecteerd en het publiceert de activa aan zowel [ Dynamische Media met OpenAPI ](/help/assets/dynamic-media-open-apis-overview.md) en [ Content Hub ](/help/assets/product-overview.md), als allebei voor Experience Manager Assets worden toegelaten.

   * Het selecteren van **Content Hub** publiceert enkel de activa aan Content Hub. Content Hub wordt alleen weergegeven als een optie als deze is ingeschakeld voor Experience Manager Assets.

   * Als u geen optie selecteert in de vervolgkeuzelijst, wordt de voor uw AEM as a Cloud Service-omgeving ingeschakelde standaardoptie automatisch toegepast op het element.


   Voor meer informatie over de beschikbare opties, zie [ StandaardDoel van de Goedkeuring en publiceer bestemmingen voor goedgekeurde activa ](#default-approval-target-options-publish-destinations).

   >[!NOTE]
   >
   >Het instellen van een goedkeuringsdoel is een beperkte beschikbaarheidsfunctie. U kunt het toegelaten krijgen of onbruikbaar maken door een steunkaartje te creëren. Als u Dynamische media met OpenAPI hebt ingeschakeld, is deze standaard ingeschakeld.

   ![ de status van de Goedkeuring ](/help/assets/assets/approval-status-delivery.png)

1. Geef andere elementeigenschappen op en klik op **[!UICONTROL Save]** .

Enkele extra punten die u wilt noteren zijn:

* Wanneer u niet de standaardmeta-gegevensvorm gebruikt en niet het **[!UICONTROL Approval Target]** gebied kunt bekijken, [ geef uw meta-gegevensvorm ](/help/assets/metadata-assets-view.md#metadata-forms) uit om het **[!UICONTROL Approval for]** gebied van de beschikbare componenten aan uw meta-gegevensvorm te slepen en klik **[!UICONTROL Save]**.

* Wanneer u het goedkeuringsdoel selecteert als `Content Hub` in de Assets-weergave, worden de elementen in Content Hub beschikbaar gesteld voor de gebruikers die deel uitmaken van dezelfde organisatie.

### Standaardgoedkeuringsdoel en publicatiedoelen voor goedgekeurde middelen {#default-approval-target-options-publish-destinations}

In de volgende tabel worden de voorwaarden weergegeven voor de weergave van de vervolgkeuzelijst `Approval Target` en het standaard goedkeuringsdoel op basis van de activering van DM met OpenAPI en Content Hub in uw AEM as a Cloud Service-omgeving:

| Dynamische media met OpenAPI | Content Hub | De vervolgkeuzelijst Goedkeuringsdoel wordt weergegeven? | Standaardgoedkeuringsdoel voor goedgekeurde elementen | Doel publiceren |
| --- | --- | --- | --- |---|
| Ingeschakeld | Ingeschakeld | Ja | Aflevering | Dynamische media met OpenAPI en Content Hub |
| Niet ingeschakeld | Ingeschakeld | Ja | Content Hub | Content Hub |
| Ingeschakeld | Niet ingeschakeld | Ja | Aflevering | Dynamische media met OpenAPI |
| Niet ingeschakeld | Niet ingeschakeld | Nee | NVT | NVT |

## Goedkeuring van nieuw opgenomen elementen automatiseren in de beheerweergave {#automate-approval-newly-ingested-assets}

Nadat u van de Assets-weergave naar de Admin-weergave bent overgeschakeld, kunt u mapinstellingen zodanig instellen dat alle nieuwe elementen die aan de map zijn toegevoegd, automatisch worden goedgekeurd.

U kunt op de volgende manieren schakelen tussen de weergaven Beheer en Assets:
![ Mijn overzicht van Workspace ](assets/assets-view.png)

Voer de volgende stappen uit om goedkeuring voor nieuw opgenomen elementen in [!DNL Experience Manager Admin view] te automatiseren:

1. Maak een map in de ontwerpomgeving (https://author-pXXX-eYYY.adobeaemcloud.com). Vervang _XXX_ met uw programmaidentiteitskaart en _JJJ_ met milieuidentiteitskaart van Experience Manager.
1. Navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Profiles]** .
1. Klik op **[!UICONTROL Create]** rechtsboven op de pagina.
1. Voeg een profieltitel toe en klik op **[!UICONTROL Create]** . Het metagegevensprofiel is gemaakt.
1. Selecteer het nieuwe metagegevensprofiel en klik op **[!UICONTROL Edit _(e)_]** . <br> Het **[!UICONTROL Edit Metadata Profile]** -formulier wordt geopend met de tab **[!UICONTROL Basic]** gemarkeerd.
1. Sleep een **[!UICONTROL Single Line Text Field]** van de sectie **[!UICONTROL Build Form]** naar de rechterkant van de sectie Metagegevens in het formulier.
1. Klik op het veld dat u zojuist hebt toegevoegd en voer de volgende updates uit in het deelvenster **[!UICONTROL Settings]** :
   1. Verander **[!UICONTROL Field Label]** in _Goedgekeurde Assets_.
   1. Werk **[!UICONTROL Map to property]** aan _bij./jcr:content/metadata/dam:status_.
   1. Verander de Standaardwaarde in _goedgekeurd_.

1. Net als bij stap 6 sleept u een **[!UICONTROL Single Line Text Field]** van de sectie **[!UICONTROL Build Form]** rechts naar de sectie Metagegevens in het formulier.
1. Klik op het veld dat u zojuist hebt toegevoegd en voer de volgende updates uit in het deelvenster **[!UICONTROL Settings]** :
   1. Verander **[!UICONTROL Field Label]** in _Doel van de Activering_.
   1. Werk **[!UICONTROL Map to property]** aan _bij./jcr:content/metadata/dam:activationTarget_.
   1. Verander de Standaardwaarde in _contenthub_.

1. Klik op **[!UICONTROL Save]**.
1. Selecteer op de pagina **[!UICONTROL Metadata Profiles]** het nieuwe metagegevensprofiel.
1. Klik op **[!UICONTROL Apply Metadata Profile to Folder(s)]** in de bovenste actiebalk.
1. Selecteer de map(pen) die u wilt goedkeuren en klik op **[!UICONTROL Apply]** .
   <br> De machtiging voor de gehele map wordt ingesteld op goedkeuring en alle middelen die naar deze map worden geüpload, worden automatisch goedgekeurd.

   >[!VIDEO](https://video.tv.adobe.com/v/3427431)

>[!NOTE]
> 
>Met deze methode worden de nieuwe elementen in de map goedgekeurd. Voor bestaande elementen in de map moet u deze handmatig selecteren en goedkeuren.

## Middelen beheren die met Content Hub zijn geüpload {#manage-assets-uploaded-using-content-hub}

[ de gebruikers van Content Hub met rechten om activa ](/help/assets/deploy-content-hub.md#onboard-content-hub-users-add-assets) toe te voegen kunnen [ activa aan Content Hub ](/help/assets/upload-brand-approved-assets.md) of van lokaal dossiersysteem of de invoeractiva van OneDrive of Dropbox gegevensbronnen toevoegen. Alle middelen worden op het hoogste niveau weergegeven in Content Hub, ongeacht de mapstructuur die beschikbaar is op uw lokale bestandssysteem of OneDrive- en Dropbox-gegevensbronnen om de zoekmogelijkheden te verbeteren.

De vertoning van activa die gebruikend Content Hub worden geupload hangt af van als u [ de auto-goedkeuringsknevel ](/help/assets/configure-content-hub-ui-options.md#configure-import-options-content-hub) hebt toegelaten:

* Als de schakeloptie **[!UICONTROL Auto-approval]** is ingeschakeld, zijn de elementen die u uploadt met Content Hub automatisch beschikbaar.

* Als de schakeloptie **[!UICONTROL Auto-approval]** is uitgeschakeld, worden de elementen die u uploadt met Content Hub niet automatisch weergegeven. De middelen zijn beschikbaar in de map `hydrated-assets` van uw Assets as a Cloud Service-omgeving. Navigeer aan de omslag en [ bulkgeef ](#bulk-approve-assets-content-hub) het statuut van die activa `Approved` voor die activa uit om in Content Hub te tonen.

![ Content Hub goedkeuringsproces ](/help/assets/assets/content-hub-approval.png)
