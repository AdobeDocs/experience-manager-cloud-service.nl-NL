---
title: Hoe te om toegang tot een adaptieve redacteur van de vormenregel te verlenen om gebruikersgroepen te selecteren?
description: Er zijn verschillende soorten gebruikers met verschillende vaardigheden die werken met Adaptive Forms. Leer hoe te om de toegang van de regelredacteur tot gebruikers te beperken die op hun rol of functie wordt gebaseerd.
feature: Adaptive Forms
role: User
level: Beginner, Intermediate
source-git-commit: d33c7278d16a8cce76c87b606ca09aa91f1c3563
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---


# De toegang van de regelredacteur van de subsidie tot uitgezochte gebruikersgroepen {#grant-rule-editor-access-to-select-user-groups}

## Overzicht {#overview}

Er zijn verschillende soorten gebruikers met verschillende vaardigheden die werken met Adaptive Forms. Terwijl deskundige gebruikers de juiste kennis kunnen hebben om met manuscripten en complexe regels te werken, kunnen er gebruikers op basisniveau zijn die slechts met de lay-out en basiseigenschappen van Aangepast Forms moeten werken.

[!DNL Experience Manager Forms] laat u regeleditortoegang tot gebruikers beperken die op hun rol of functie wordt gebaseerd. In de instellingen van de Adaptive Forms Configuration Service kunt u de [gebruikersgroepen](forms-groups-privileges-tasks.md) die tot regelredacteur kunnen bekijken en toegang hebben.

## Geef gebruikersgroepen op die toegang kunnen krijgen tot de regeleditor {#specify-user-groups-that-can-access-rule-editor}

1. Aanmelden bij [!DNL Experience Manager Forms] als beheerder.
1. Klik in de auteur-instantie op ![Adobe Experience Manager](assets/adobeexperiencemanager.png)Adobe Experience Manager > Gereedschappen ![hamer](assets/hammer-icon.svg) > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**. De webconsole wordt in een nieuw venster geopend.

   ![1-2](assets/1-2.png)

1. In [!UICONTROL Web Console] Venster, zoeken en klikken **[!UICONTROL Adaptive Form Configuration Service]**. **[!UICONTROL Adaptive Form Configuration Service]** wordt weergegeven. Wijzig geen waarde en klik op **[!UICONTROL Save]**.

   Er wordt een bestand gemaakt `/apps/system/config/com.adobe.aemds.guide.service.impl.AdaptiveFormConfigurationServiceImpl.config` in CRX-opslagplaats.

1. Meld u als beheerder aan bij CRXDE. Bestand openen `/apps/system/config/com.adobe.aemds.guide.service.impl.AdaptiveFormConfigurationServiceImpl.config` voor bewerken.
1. Gebruik het volgende bezit om de naam van een groep te specificeren die tot regelredacteur (bijvoorbeeld, RuleEditorsUserGroup) kan toegang hebben en klik **[!UICONTROL Save All]**.

   `af.ruleeditor.custom.groups=["RuleEditorsUserGroup"]`

   Als u toegang voor meerdere groepen wilt inschakelen, geeft u een lijst op met door komma&#39;s gescheiden waarden:

   `af.ruleeditor.custom.groups=["RuleEditorsUserGroup", "PermittedUserGroup"]`

   ![Gebruiker maken](assets/create_user_new.png)

   Nu, wanneer een gebruiker die geen deel uitmaakt van de opgegeven gebruikersgroep (hier)    `RuleEditorsUserGroup`) tikt op een veld, het pictogram Regel bewerken ( ![edit-rules1](assets/edit-rules1.png)) is niet beschikbaar op de werkbalk Componenten:

   ![componentstoolbarwither](assets/componentstoolbarwithre.png)

   De toolbar van componenten zoals zichtbaar aan een gebruiker met de toegang van de regelredacteur:

   ![componentstoolbarwithouding](assets/componentstoolbarwithoutre.png)

   De toolbar van Componenten zoals zichtbaar aan een gebruiker zonder de toegang van de regelredacteur

   Zie voor instructies over het toevoegen van gebruikers aan groepen [Gebruikersbeheer en beveiliging](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security.html).

