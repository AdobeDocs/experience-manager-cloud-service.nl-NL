---
title: Hoe te om een Redirect Pagina te vormen?
description: Leer hoe gebruikers kunnen worden omgeleid naar een webpagina die formulierauteurs kunnen configureren tijdens het maken van het formulier.
feature: Adaptive Forms
role: User
level: Intermediate
exl-id: e4dc01d2-7c89-4bd8-af0a-1d2df4676a9a
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---

# Omleidingspagina configureren {#configuring-redirect-page}

Formulierauteurs kunnen een pagina configureren voor elk formulier, waarnaar de formuliergebruikers worden omgeleid na het verzenden van een formulier.

1. Selecteer in de bewerkingsmodus een component en klik vervolgens op ![op veldniveau](assets/select_parent_icon.svg) > **[!UICONTROL Adaptive Form Container]** en klik vervolgens op ![cmppr](assets/configure-icon.svg).

1. Klik in de zijbalk op **[!UICONTROL Submission]**.

1. Geef de URL van de omleidingspagina op onder **[!UICONTROL Redirect URL/Path]** in de **[!UICONTROL Submission]** sectie.
1. Naar keuze, onder Verzenden Actie, voor Submit aan de het eindpuntactie van REST, kunt u de parameter vormen die tot de omleidingspagina wordt overgegaan.

   ![Pagina-configuratie omleiden](assets/redirect-url.png)

   Pagina-configuratie omleiden

Auteurs van formulieren kunnen de volgende parameters gebruiken die worden doorgegeven aan de pagina Bedankt. Voor alle beschikbare verzendhandelingen `status` en `owner` parameters worden doorgegeven. Naast deze twee parameters worden enkele aanvullende parameters doorgegeven voor de volgende verzendhandelingen:

* **[!UICONTROL Submit to REST endpoint]**: Parameters die voor parametertoewijzing in het veld worden toegevoegd, worden doorgegeven. `status` en `owner` parameters worden niet doorgegeven in deze verzendhandeling. Zie voor meer informatie [Het vormen van Submit aan het eindpunt REST legt Actie voor](configuring-submit-actions.md).
