---
title: Hoe te om toegang tot een adaptieve redacteur van de vormenregel te verlenen om gebruikersgroepen te selecteren?
description: Er zijn verschillende soorten gebruikers met verschillende vaardigheden die werken met Adaptive Forms. Leer hoe te om de toegang van de regelredacteur tot gebruikers te beperken die op hun rol of functie wordt gebaseerd.
feature: Adaptive Forms
role: User
level: Beginner, Intermediate
hide: true
hidefromtoc: true
source-git-commit: 937bd4653e454beea3111cfc7ef7b4bbc1ace193
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---


# De toegang van de regelredacteur van de subsidie tot uitgezochte gebruikersgroepen {#grant-rule-editor-access-to-select-user-groups}

## Overzicht {#overview}

Er zijn verschillende soorten gebruikers met verschillende vaardigheden die werken met Adaptive Forms. Terwijl deskundige gebruikers de juiste kennis kunnen hebben om met manuscripten en complexe regels te werken, kunnen er gebruikers op basisniveau zijn die slechts met de lay-out en basiseigenschappen van Aangepast Forms moeten werken.

Met [!DNL Experience Manager Forms] kunt u de toegang van regeleditors beperken tot gebruikers op basis van hun rol of functie. In de Adaptieve montages van de Dienst van de Configuratie van Forms, kunt u de [ gebruikersgroepen ](forms-groups-privileges-tasks.md) specificeren die tot regelredacteur kunnen bekijken en toegang hebben.

## Geef gebruikersgroepen op die toegang kunnen krijgen tot de regeleditor {#specify-user-groups-that-can-access-rule-editor}

1. Meld u aan bij [!DNL Experience Manager Forms] als beheerder.
1. In de auteursinstantie, klik ![ Adobe Experience Manager ](assets/adobeexperiencemanager.png) Adobe Experience Manager > Hulpmiddelen ![ hamer ](assets/hammer-icon.svg) > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**. De webconsole wordt in een nieuw venster geopend.

   ![ 1-2 ](assets/1-2.png)

1. Zoek en klik op **[!UICONTROL Adaptive Form Configuration Service]** in het [!UICONTROL Web Console] -venster. **[!UICONTROL Adaptive Form Configuration Service]** wordt weergegeven. Wijzig geen waarde en klik op **[!UICONTROL Save]** .

   Er wordt een bestand `/apps/system/config/com.adobe.aemds.guide.service.impl.AdaptiveFormConfigurationServiceImpl.config` gemaakt in de CRX-opslagplaats.

1. Meld u als beheerder aan bij CRXDE. Open het bestand `/apps/system/config/com.adobe.aemds.guide.service.impl.AdaptiveFormConfigurationServiceImpl.config` om het te bewerken.
1. Gebruik de volgende eigenschap om de naam op te geven van een groep die toegang heeft tot een regeleditor (bijvoorbeeld RuleEditorsUserGroup) en klik op **[!UICONTROL Save All]** .

   `af.ruleeditor.custom.groups=["RuleEditorsUserGroup"]`

   Als u toegang voor meerdere groepen wilt inschakelen, geeft u een lijst op met door komma&#39;s gescheiden waarden:

   `af.ruleeditor.custom.groups=["RuleEditorsUserGroup", "PermittedUserGroup"]`

   ![ creeer Gebruiker ](assets/create_user_new.png)

   Nu, wanneer een gebruiker die geen deel uitmaakt van de opgegeven gebruikersgroep (hier)    `RuleEditorsUserGroup`) tikt een gebied, geeft het pictogram van de Regel uit ( ![ geef-rules1 ](assets/edit-rules1.png)) is niet beschikbaar in de toolbar van Componenten:

   ![ componentStoolbarwithre ](assets/componentstoolbarwithre.png)

   De toolbar van componenten zoals zichtbaar aan een gebruiker met de toegang van de regelredacteur:

   ![ componentStoolbarwithoutre ](assets/componentstoolbarwithoutre.png)

   De toolbar van Componenten zoals zichtbaar aan een gebruiker zonder de toegang van de regelredacteur

   Voor instructies bij het toevoegen van gebruikers aan groepen, zie [ Beleid van de Gebruiker en Veiligheid ](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security.html).

