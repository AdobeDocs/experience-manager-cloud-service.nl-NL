---
title: AEM Assets verbinden met Creative Cloud
description: Leer hoe u AEM Assets configureert en verbindt met Creative Cloud. Maak verbinding met een Creative Cloud dat is ingericht voor een andere IMS-organisatie en gebruik de meest recente integratie van Creatives Cloud in AEM Assets, waaronder Express en Creative Cloud Libraries.
exl-id: 880200fe-94b3-49de-802c-34283f7c71bc
feature: Collaboration
role: User
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 0%

---

# AEM Assets verbinden met Creative Cloud  {#cross-org-entitlements}

| [ Beste praktijken van het Onderzoek ](/help/assets/search-best-practices.md) | [ Beste praktijken van Meta-gegevens ](/help/assets/metadata-best-practices.md) | [ Content Hub ](/help/assets/product-overview.md) | [ Dynamic Media met mogelijkheden OpenAPI ](/help/assets/dynamic-media-open-apis-overview.md) | [ de ontwikkelaarsdocumentatie van AEM Assets ](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

Experience Manager Assets heeft de mogelijkheid om verbinding te maken met een machtiging voor een Creative Cloud die is ingericht voor een andere IMS-organisatie om eenvoudig de nieuwste integratie van Creatives Cloud in AEM Assets, waaronder Express en Creative Cloud Libraries, te kunnen gebruiken.

Als uw producten van het Creative Cloud en AEM Assets aan afzonderlijke organisaties IMS worden geleverd, kunt u met een verschillende organisatie van het Creative Cloud verbinden om geïntegreerde werkschema&#39;s tussen de twee oplossingen uit te voeren.

## Vereisten {#prerequisites}

* Beheerdersrechten voor Experience Manager Assets

* Actieve bevoegdheid tot Creative Cloud voor de zelfde gebruiker - identiteitskaart die over Creative Cloud en Experience Manager wordt gebruikt. Rechten op persoonlijke en gefedereerde id&#39;s met hetzelfde e-mailadres worden beschouwd als verschillende gebruikers-id&#39;s.

## Verbinding maken met een nieuwe Creative Cloud {#connect-to-creative-cloud-org}

Voer de volgende stappen uit om verbinding te maken met een nieuwe Creative Cloud-organisatie:

1. Ga naar **[!UICONTROL Settings]** > **[!UICONTROL Creative Cloud]**.

1. Selecteer de nieuwe organisatie van het Creative Cloud met behulp van de vervolgkeuzelijst **[!UICONTROL Select new Creative Cloud org ID]** . In de lijst worden alle organisaties weergegeven waartoe u toegang hebt. Selecteer de organisatie met actieve rechten voor Creatives Cloud.

1. Klik op **[!UICONTROL Switch orgs]** om over te schakelen naar de nieuwe organisatie.

   ![ dwars-Org Entitlements ](assets/cross-org-entitlements.png)

## Beperkingen {#limitations}

* U kunt AEM Assets per keer verbinden met één organisatie van het Creative Cloud. Verbinding met meerdere organisaties van het Creative Cloud tegelijk wordt niet ondersteund.

* De organisatie van het Creative Cloud waarmee u verbinding maakt binnen AEM Assets is van toepassing op alle gebruikers binnen uw organisatie.
