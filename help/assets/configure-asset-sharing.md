---
title: Elementen, mappen en verzamelingen delen als een koppeling
description: In dit artikel wordt beschreven hoe u elementen, mappen en verzamelingen als hyperlink deelt in de middelen van Experience Manager.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 82dd9bd69fe994f74c7be8a571e386f0e902f6a1

---


# Delen van koppelingen voor elementen configureren {#asset-link-sharing}

<!-- TBD: Web Console is not there so how to configure Day CQ email service? Or is it not required now? -->

Gebruik het dialoogvenster Koppelen om de URL te genereren voor elementen die u met gebruikers wilt delen. Gebruikers met beheerdersrechten of met leesmachtigingen op de `/var/dam/share` locatie kunnen de koppelingen weergeven die met hen worden gedeeld. Het delen van elementen via een koppeling is een handige manier om bronnen beschikbaar te maken voor externe partijen zonder dat deze zich eerst hoeven aan te melden bij AEM Assets.

>[!NOTE]
>
>Als u koppelingen van uw AEM-auteur naar externe entiteiten wilt delen, dient u alleen de volgende URL&#39;s voor `GET` aanvragen beschikbaar te maken. Blokkeer andere URL&#39;s om ervoor te zorgen dat uw AEM-auteur-instantie veilig is.
>* `[aem_server]:[port]/linkshare.html`
>* `[aem_server]:[port]/linksharepreview.html`
>* `[aem_server]:[port]/linkexpired.html`


## CQ-mailservice op dag configureren {#configmailservice}

Voordat u elementen kunt delen als koppelingen, configureert u de e-mailservice.

1. Click or tap the AEM logo, and then navigate to **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
1. Zoek vanuit de lijst met services de **[!UICONTROL Day CQ Mail Service]**.
1. Click the **[!UICONTROL Edit]** icon beside the service, and configure the following parameters for **Day CQ Mail Service]** with the details mentioned against their names:

   * hostnaam SMTP-server: hostnaam e-mailserver
   * SMTP-serverpoort: e-mailserverpoort
   * SMTP-gebruiker: gebruikersnaam e-mailserver
   * SMTP-wachtwoord: wachtwoord e-mailserver

1. Klik op **Opslaan** of tik op Opslaan.

## Maximale gegevensgrootte configureren {#maxdatasize}

Wanneer u elementen downloadt van de koppeling die wordt gedeeld met de functie voor het delen van koppelingen, comprimeert AEM de hiërarchie van elementen uit de opslagplaats en retourneert het element vervolgens in een ZIP-bestand. Bij gebrek aan beperkingen van de hoeveelheid gegevens die in een ZIP-bestand kan worden gecomprimeerd, worden enorme hoeveelheden gegevens gecomprimeerd, waardoor fouten in het geheugen in JVM worden veroorzaakt. Om het systeem van een potentiële ontkenning van de dienstaanval toe te schrijven aan deze situatie te beveiligen, vorm de maximumgrootte gebruikend de **Max (ongecomprimeerde)** parameter van de Grootte van de Inhoud voor Dag CQ DAM Adhoc Servlet van de Volmacht van het Aandeel van Activa in de Manager van de Configuratie. Als de niet-gecomprimeerde grootte van het element de geconfigureerde waarde overschrijdt, worden de verzoeken om het downloaden van het element afgewezen. De standaardwaarde is 100 MB.

1. Klik of tik op het AEM-logo en ga vervolgens naar **Gereedschappen** > **Bewerkingen** > **Webconsole**.
1. Zoek vanuit de webconsole de configuratie van de **Day CQ DAM Adhoc Asset Share Proxy Servlet** .
1. Open de configuratie van **Day CQ DAM Adhoc Asset Share Proxy Servlet** in de bewerkingsmodus en wijzig de waarde van de parameter **Max Content Size (niet-gecomprimeerd)**.
1. Sla de wijzigingen op.

<!--
Add content or link about how to configure sharing via BP, DA, AAL, etc.
-->
