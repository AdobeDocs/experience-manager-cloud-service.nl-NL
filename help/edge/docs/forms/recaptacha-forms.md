---
title: reCAPTCHA gebruiken met Edge Delivery Services voor AEM Forms as a Cloud Service
description: Google reCAPTCHA gebruiken in een formulier voor Edge Delivery Services for AEM Forms
feature: Edge Delivery Services
exl-id: ac104e23-f175-435f-8414-19847efa5825
role: Admin, Architect, Developer
source-git-commit: bc422429d4a57bbbf89b7af2283b537a1f516ab5
workflow-type: tm+mt
source-wordcount: '815'
ht-degree: 0%

---


# reCAPTCHA gebruiken met Edge Delivery Services voor AEM Forms as a Cloud Service

<!--
<span>The **reCAPTCHA** feature is under the pre-release program. To request access to the **reCAPTCHA** feature for Edge Delivery Services for AEM Forms, send an email from your work address to mailto:aem-forms-ea@adobe.com.</span>
-->

reCAPTCHA is een populair hulpmiddel dat wordt gebruikt om websites te beschermen tegen frauduleuze activiteiten, spam en misbruik. In Edge Delivery Services biedt het Adaptive Forms Block de mogelijkheid om Google reCAPTCHA toe te voegen om onderscheid te maken tussen mensen en bots. Met deze functie kunnen gebruikers hun website beschermen tegen spam en misbruik.
Neem bijvoorbeeld een enquêteformulier waarin gegevens worden verzameld zoals begin- en eindreisdatums, kamerbudget, geschatte reiskosten en reizigersinformatie. In dergelijke gevallen bestaat het risico dat kwaadwillende gebruikers het formulier exploiteren voor doeleinden als het verzenden van phishinge-mails of het overlopen van het formulier met irrelevante of schadelijke inhoud met behulp van spambots. De integratie van reCAPTCHA biedt extra veiligheid door te verifiëren dat de bijdragen van echte gebruikers zijn, effectief minimaliserend spamingingingangen.

<!-- ![Recaptcha Image](/help/edge/docs/forms/assets/recaptcha-image.png){width="300" align="center"} -->

Edge Delivery Services steunt slechts de **gebaseerde Score (v3)-reCAPTCHA** voor het Aanpassings Blok van de Vorm.

![ Recaptcha V2 ](/help/forms/assets/recaptcha-v2-invisible.png){width="300" align="center"}


Aan het einde van dit artikel leert u:
- [Google reCAPTCHA inschakelen voor één formulier](#enable-google-recaptchas-for-a-single-form)
- [reCAPTCHA inschakelen voor alle formulieren op uw site](#enable-recaptcha-for-all-the-forms)

## Voorwaarden

- Begin met de ontwikkeling van Edge Delivery Services Forms door de stappen te volgen die in [ worden verklaard creeer een vorm gebruikend het AanpassingsBlok van Forms ](/help/edge/docs/forms/create-forms.md).
- Registreer uw domein met [ Google reCAPTCHA en verkrijg geloofsbrieven ](https://www.google.com/recaptcha/admin/create).

## Google reCAPTCHA inschakelen voor één formulier {#enable-google-recaptchas-for-a-single-form}

Als u Google reCAPTCHA voor één formulier inschakelt, moet de Google reCAPTCHA-service in een specifiek webformulier worden geïntegreerd om automatisch misbruik of spamverzending te voorkomen.

Google reCAPTCHA inschakelen voor één formulier:

1. [Vorm de reCAPTCHA geheime sleutel in het dossier van de projectconfiguratie](#configure-secret-key)
1. [De reCAPTCHA-sitesleutel toevoegen aan uw formulier](#add-site-key)

Beginnen reCaptcha in Edge Delivery Services Forms te vormen, verwijs naar het volgende [ spreadsheet ](/help/edge/docs/forms/assets/recaptcha.xlsx) dat de vormdefinitie voor een vorm omvat.

### Vorm de reCAPTCHA geheime sleutel in het dossier van de projectconfiguratie {#configure-secret-key}

Het Sitegeheim voor domein dat bij Google reCAPTCHA wordt geregistreerd wordt toegevoegd aan project het configuratiedossier (`.helix/config`) in uw omslag van het Project van AEM bij Microsoft SharePoint of de Aandrijving van Google. U voegt als volgt het Sitegeheim toe aan het configuratiebestand:

1. Ga naar de map AEM Project op Microsoft® SharePoint of Google Drive.
1. Maak het `.helix/config.xlsx` -bestand in uw AEM-projectmap in de Microsoft SharePoint-site of het `.helix/config` -bestand in de AEM-projectmap in uw Google Drive.

   >[!NOTE]
   >
   > Het [ dossier van de projectconfiguratie ](https://www.aem.live/docs/configuration) is een spreadsheet die bij `/.helix/config` wordt gevestigd. Als het bestand niet bestaat, maakt u het.

1. Open het `config` -bestand en voeg de volgende sleutel- en waardeparen toe:

   - **captcha.geheime**: Google reCAPTCHA geheime zeer belangrijke waarde
   - **captcha.type**: reCAPTCHA v2

   >[!NOTE]
   >
   >  - U kunt de reCAPTCHA sleutels van [ Google reCAPTCHA Admin Console ](https://www.google.com/recaptcha/admin) terugwinnen.
   >  - U moet de waarde van **captcha.type** in het `config` dossier als **reCAPTCHA v2** specificeren.

   Raadpleeg de schermafbeelding van een projectconfiguratiebestand hieronder:

   ![ het configuratiedossier van het Project ](/help/forms/assets/recaptcha-config-file.png)

1. Sla het `config` -bestand op.

1. Voorproef en publiceer het `config` dossier gebruikend [ AEM Sidekick ](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).

### Voeg reCAPTCHA-sitesleutel toe aan uw formulier {#add-site-key}

De sitecode voor een domein dat is geregistreerd bij Google reCAPTCHA, wordt toegevoegd aan het werkblad van het formulier dat moet worden beveiligd. De sitecode toevoegen aan een formulier:

1. Ga naar de map AEM Project op Microsoft® SharePoint of Google Drive en open uw spreadsheet. U kunt ook een nieuw werkblad voor een formulier maken.
1. Voeg een rij in het spreadsheet in om een nieuw veld toe te voegen als CAPTCHA, inclusief de volgende details:
   - **type**: captcha
   - **waarde**: Google reCAPTCHA plaats zeer belangrijke waarde

   Raadpleeg de onderstaande schermafbeelding waarin het spreadsheet met het nieuwe rijtype als CAPTCHA wordt weergegeven:

   ![ Recaptcha spreadsheet ](/help/edge/docs/forms/assets/recaptcha-spreadsheet.png)

   >[!NOTE]
   >
   >  U kunt de reCAPTCHA sleutels van [ Google reCAPTCHA Admin Console ](https://www.google.com/recaptcha/admin) terugwinnen.

1. Sla de spreadsheet op.
1. Het gebruik [ AEM Sidekick ](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) aan voorproef en publiceert het blad.

Nadat u nieuwe rij hebt toegevoegd aan de formulierdefinitie, wordt er een reCAPTCHA-badge weergegeven in de rechterbenedenhoek van het formulier. Dit zorgt ervoor dat het formulier nu wordt beschermd tegen frauduleuze activiteiten, spam en misbruik.

![ recaptcha-form ](/help/edge/docs/forms/assets/recaptcha-form.png)

## reCAPTCHA inschakelen voor alle formulieren op uw site{#enable-recaptcha-for-all-the-forms}

Als u Google reCAPTCHA wilt toepassen op alle formulieren op uw site die gebruikmaken van het Adaptive Forms Block, slaat u de vorige stappen over en sluit u de `sitekey` -waarde rechtstreeks in het `recaptcha.js` -bestand in. De waarde van de sitetoets opnemen in het `recaptcha.js` -bestand:

1. [Google reCAPTCHA Site Key bijwerken in het bestand recaptcha.js](#1-update-google-recaptcha-site-key-in-recaptchajs-file)
1. [Implementeer het bestand en bouw het project](#2-deploy-the-file-and-build-the-project)
1. [De site voorvertonen met AEM sidekick](#3-preview-the-site-using-the-aem-sidekick)

### Google reCAPTCHA Site Key bijwerken in bestand recaptcha.js

1. Open de overeenkomstige bewaarplaats GitHub op uw lokale machine.
1. Ga naar de map `[../Form Block/integrations]` en open het bestand `recaptcha.js` .
1. Vervang `siteKey` door de sleutelwaarde van de Google reCAPTCHA-site.

   ![ Recaptcha is op alle vormen van toepassing ](/help/forms/assets/recaptcha-apply-to-all-forms.png)

   >[!NOTE]
   >
   >  U kunt de reCAPTCHA sleutels van [ Google reCAPTCHA Admin Console ](https://www.google.com/recaptcha/admin) terugwinnen.

1. Sla het `recaptcha.js` -bestand op.

### Implementeer het bestand en bouw het project

Stel het bijgewerkte `recaptcha.js` dossier aan uw project GitHub op en verifieer een succesvolle bouwstijl.

### De site voorvertonen met AEM sidekick

Het gebruik [ AEM Sidekick ](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) om de plaats te voorproef en te publiceren.

De reCAPTCHA-badge wordt weergegeven voor alle formulieren op uw site.

