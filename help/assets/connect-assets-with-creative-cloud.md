---
title: AEM Assets verbinden met Creative Cloud
description: Leer hoe u AEM Assets configureert en verbindt met Creative Cloud. Maak verbinding met een Creative Cloud-machtiging die is ingericht voor een andere IMS-organisatie en gebruik de nieuwste Creative Cloud-integratie in AEM Assets, waaronder Express en Creative Cloud Libraries.
exl-id: 880200fe-94b3-49de-802c-34283f7c71bc
feature: Collaboration
role: User
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 0%

---

# AEM Assets verbinden met Creative Cloud  {#cross-org-entitlements}

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

Experience Manager Assets heeft de mogelijkheid om verbinding te maken met een Creative Cloud-machtiging die is ingericht voor een andere IMS-organisatie om de nieuwste Creative Cloud-integratie in AEM Assets, waaronder Express en Creative Cloud Libraries, eenvoudig te kunnen gebruiken.

Als uw Creative Cloud-producten en AEM Assets zijn ingericht voor aparte IMS-organisaties, kunt u verbinding maken met een andere Creative Cloud-organisatie om geïntegreerde workflows tussen de twee oplossingen uit te voeren.

## Vereisten {#prerequisites}

* Beheerdersrechten voor Experience Manager Assets

* Actief recht op Creative Cloud voor dezelfde gebruikersnaam die in Creative Cloud en Experience Manager wordt gebruikt. Rechten op persoonlijke en gefedereerde id&#39;s met hetzelfde e-mailadres worden beschouwd als verschillende gebruikers-id&#39;s.

## Verbinding maken met een nieuwe Creative Cloud-organisatie {#connect-to-creative-cloud-org}

Voer de volgende stappen uit om verbinding te maken met een nieuwe Creative Cloud-organisatie:

1. Ga naar **[!UICONTROL Settings]** > **[!UICONTROL Creative Cloud]**.

1. Selecteer de nieuwe Creative Cloud-organisatie in de vervolgkeuzelijst **[!UICONTROL Select new Creative Cloud org ID]** . In de lijst worden alle organisaties weergegeven waartoe u toegang hebt. Selecteer de organisatie met actieve Creative Cloud-rechten.

1. Klik op **[!UICONTROL Switch orgs]** om over te schakelen naar de nieuwe organisatie.

   ![ dwars-Org Entitlements ](assets/cross-org-entitlements.png)

## Beperkingen {#limitations}

* U kunt AEM Assets per keer verbinden met één Creative Cloud-organisatie. Verbinding met meerdere Creative Cloud-organisaties tegelijk wordt niet ondersteund.

* De Creative Cloud-organisatie waarmee u verbinding maakt in AEM Assets is van toepassing op alle gebruikers binnen uw organisatie.
