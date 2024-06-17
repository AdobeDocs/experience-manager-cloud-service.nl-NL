---
title: AEM Assets verbinden met Creative Cloud
description: Leer hoe u AEM Assets configureert en verbindt met Creative Cloud. Verbind met een Creative Cloud recht dat aan een verschillende organisatie IMS wordt geleverd om de recentste integratie van het Creative Cloud in AEM Assets, met inbegrip van Uitdrukkelijke en Bibliotheken van het Creative Cloud gemakkelijk te gebruiken.
exl-id: 880200fe-94b3-49de-802c-34283f7c71bc
feature: Collaboration
role: User
source-git-commit: 257930bc2633a0d31ad3bd28305b8159597befa5
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%

---

# AEM Assets verbinden met Creative Cloud  {#cross-org-entitlements}

Experience Manager Assets heeft de mogelijkheid om verbinding te maken met een machtiging voor een Creative Cloud die is ingericht voor een andere IMS-organisatie om eenvoudig de nieuwste integratie van Creatives Cloud in AEM Assets te kunnen gebruiken, inclusief Express en Creative Cloud Libraries.

Als uw producten van het Creative Cloud en AEM Assets aan afzonderlijke organisaties IMS worden geleverd, kunt u met een verschillende organisatie van het Creative Cloud verbinden om geïntegreerde werkschema&#39;s tussen de twee oplossingen uit te voeren.

## Vereisten {#prerequisites}

* Beheerdersrechten voor Experience Manager Assets

* Actieve bevoegdheid tot Creative Cloud voor de zelfde gebruiker - identiteitskaart die over Creative Cloud en Experience Manager wordt gebruikt. Rechten op persoonlijke en gefedereerde id&#39;s met hetzelfde e-mailadres worden beschouwd als verschillende gebruikers-id&#39;s.

## Verbinding maken met een nieuwe Creative Cloud {#connect-to-creative-cloud-org}

Voer de volgende stappen uit om verbinding te maken met een nieuwe Creative Cloud-organisatie:

1. Ga naar **[!UICONTROL Settings]** > **[!UICONTROL Creative Cloud]**.

1. Selecteer de nieuwe organisatie van het Creative Cloud gebruikend **[!UICONTROL Select new Creative Cloud org ID]** vervolgkeuzelijst. In de lijst worden alle organisaties weergegeven waartoe u toegang hebt. Selecteer de organisatie met actieve rechten voor Creatives Cloud.

1. Klikken **[!UICONTROL Switch orgs]** om over te schakelen op de nieuwe organisatie.

   ![Rechten kruiselings](assets/cross-org-entitlements.png)

## Beperkingen {#limitations}

* U kunt AEM Assets per keer verbinden met één organisatie van het Creative Cloud. Verbinding met meerdere organisaties van het Creative Cloud tegelijk wordt niet ondersteund.

* De organisatie van het Creative Cloud waarmee u verbinding maakt binnen AEM Assets is van toepassing op alle gebruikers binnen uw organisatie.
