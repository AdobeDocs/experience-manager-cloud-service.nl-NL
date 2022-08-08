---
title: Integreren met Adobe Campaign Classic
description: Leer hoe u AEM as a Cloud Service met Adobe Campaign Classic kunt integreren om aantrekkelijke inhoud voor uw campagnes te maken.
feature: Administering
role: Admin
exl-id: 23874955-bdf3-41be-8a06-53d2afdd7f2b
source-git-commit: cab630838f5cce3c2a2749c61b0aa7504dc403f7
workflow-type: tm+mt
source-wordcount: '1302'
ht-degree: 0%

---

# Integreren met Adobe Campaign Classic {#integrating-campaign-classic}

Door AEM as a Cloud Service met Adobe Campaign te integreren, kunt u de levering van e-mail, inhoud en formulieren rechtstreeks in AEM as a Cloud Service beheren. De stappen van de configuratie in zowel Adobe Campaign Classic als AEM as a Cloud Service zijn nodig om bidirectionele communicatie tussen oplossingen toe te laten.

Dankzij deze integratie kunnen AEM as a Cloud Service en Adobe Campaign Classic onafhankelijk worden gebruikt. Marketers kunnen campagnes maken en doelgericht gebruik maken in Adobe Campaign, terwijl makers van inhoud tegelijkertijd in AEM as a Cloud Service aan het ontwerpen van inhoud kunnen werken. Dankzij de integratie kunnen de inhoud en het ontwerp van de campagne in AEM doelgericht worden opgezet en door de campagne worden geleverd.

## Integratiestappen {#integration-steps}

De integratie tussen AEM en Campagne vereist een aantal stappen in beide oplossingen.

1. [Installeer het AEM integratiepakket in de campagne.](#install-package)
1. [Een operator maken voor AEM in campagne](#create-operator)
1. [Integratie van campagnes configureren in AEM](#campaign-integration)
1. [De AEM ExternalAlizer configureren](#externalizer)
1. [De externe gebruiker van de campagne configureren in AEM](#configure-user)
1. [De externe AEM-account configureren in Campagne](#acc-setup)

Dit document leidt u door elk van deze stappen in detail

## Vereisten {#prerequisites}

* Toegang tot Adobe Campaign Classic voor beheerders
   * Om de integratie uit te voeren, hebt u een werkende instantie van Adobe Campaign Classic, met inbegrip van een gevormd gegevensbestand nodig.
   * Raadpleeg voor meer informatie over het instellen en configureren van Adobe Campaign Classic de [Adobe Campaign Classic-documentatie;](https://experienceleague.adobe.com/docs/campaign-classic/using/campaign-classic-home.html) met name de gids Installatie en Configuratie.

* Toegang van beheerders tot AEM as a Cloud Service

## Het AEM integratiepakket installeren in een campagne {#install-package}

De **AEM integratie** -pakket in Adobe Campaign bevat een aantal standaardconfiguraties die nodig zijn om verbinding te maken met AEM.

1. Meld u als beheerder aan bij de Adobe Campaign-instantie met de clientconsole.

1. Selecteren **Gereedschappen** > **Geavanceerd** > **Pakket importeren...**.

   ![Pakket importeren](assets/import-package.png)

1. Klikken **Een standaardpakket installeren** en klik vervolgens op **Volgende**.

1. Controleer de **AEM integratie** pakket.

   ![Een standaardpakket installeren](assets/select-package.png)

1. Klikken **Volgende** en vervolgens **Start** om de installatie te starten.

   ![Voortgang van installatie](assets/installation.png)

1. Klikken **Sluiten** als de installatie is voltooid.

Het integratiepakket is nu geïnstalleerd.

## Operator for AEM in Campaign maken {#create-operator}

Het integratiepakket maakt automatisch de `aemserver` operator die AEM gebruikt om verbinding te maken met Adobe Campaign. U moet een veiligheidsstreek voor deze exploitant bepalen en zijn wachtwoord plaatsen.

1. Meld u met de clientconsole aan bij Adobe Campaign als beheerder.

1. Selecteren **Gereedschappen** -> **Verkenner** in de menubalk.

1. Navigeer in de verkenner naar de **Beheer** > **Toegangsbeheer** > **Operatoren** knooppunt.

1. Selecteer `aemserver` operator.

1. Op de **Bewerken** selecteert u de **Toegangsrechten** subtab en klik vervolgens op de knop **Bewerk de toegangsparameters...** koppeling.

   ![Beveiligingszone instellen](assets/access-rights.png)

1. Selecteer de aangewezen veiligheidsstreek en bepaal zonodig het vertrouwde op IP masker.

1. Klikken **Opslaan**.

1. Afmelden bij de Adobe Campaign-client.

1. Navigeer in het bestandssysteem van de Adobe Campaign-server naar de installatielocatie voor Campagne en bewerk de `serverConf.xml` als beheerder. Dit bestand bevindt zich doorgaans onder:
   * `C:\Program Files\Adobe\Adobe Campaign Classic v7\conf` in Windows.
   * `/usr/local/neolane/nl6/conf/eng` in Linux.

1. Zoeken naar `securityZone` en ervoor zorgen dat de volgende parameters worden ingesteld voor de beveiligingszone van de AEM.

   * `allowHTTP="true"`
   * `sessionTokenOnly="true"`
   * `allowUserPassword="true"`.

1. Sla het bestand op.

1. Zorg ervoor dat de beveiligingszone niet wordt overschreven door de desbetreffende instelling in het dialoogvenster `config-<server name>.xml` bestand.

   * Als het configuratiebestand een afzonderlijke instelling voor de beveiligingszone bevat, wijzigt u de instelling `allowUserPassword` kenmerk naar `true`.

1. Als u de Adobe Campaign Classic-serverpoort wilt wijzigen, vervangt u `8080` met de gewenste poort.

>[!CAUTION]
>
>Door gebrek, is er geen veiligheidsstreek die voor de exploitant wordt gevormd. Als u AEM verbinding wilt maken met Adobe Campaign, moet u een zone selecteren zoals in de vorige stappen wordt beschreven.
>
>Adobe beveelt ten zeerste aan een beveiligingszone in te stellen die is gewijd aan AEM om beveiligingsproblemen te voorkomen. Raadpleeg voor meer informatie over dit onderwerp de [Adobe Campaign Classic-documentatie.](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/additional-configurations/security-zones.html)

1. Ga in de Campagne-client terug naar de `aemserver` en selecteert u de **Algemeen** tab.

1. Klik op de knop **Wachtwoord opnieuw instellen...** koppeling.

1. Geef een wachtwoord op en bewaar dit op een veilige locatie voor toekomstig gebruik.

1. Klikken **OK** om het wachtwoord voor de `aemserver` operator.

## Campagne-integratie configureren in AEM {#campaign-integration}

AEM [de operator die u al hebt ingesteld in Campagne](#create-operator) om te communiceren met Campagne

1. Meld u als beheerder aan bij de AEM ontwerpinstantie.

1. Selecteer vanuit de globale spoorstaaf voor de navigatie **Gereedschappen** > **Cloud Services** > **Oudere Cloud Services** > **Adobe Campaign** en klik vervolgens op **Nu configureren**.

   ![Adobe Campaign configureren](assets/configure-campaign-service.png)

1. In de dialoog, creeer een de dienstconfiguratie van de Campagne door een **Titel** en klik op **Maken**.

   ![Het dialoogvenster Campagne configureren](assets/configure-campaign-dialog.png)

1. Er wordt een nieuw venster en dialoogvenster geopend om de configuratie te bewerken. Verstrek de noodzakelijke informatie.

   * **Gebruikersnaam** - Dit is [de Adobe Campaign AEM Integration package operator gemaakt in de vorige stap.](#create-operator) Standaard is dit `aemserver`.
   * **Wachtwoord** - Dit is het wachtwoord voor [de Adobe Campaign AEM Integration package operator gemaakt in de vorige stap.](#create-operator)
   * **API-eindpunt** - Dit is de URL van de Adobe Campaign-instantie.

   ![Adobe Campaign configureren in AEM](assets/configure-campaign.png)

1. Selecteren **Verbinding maken met Adobe Campaign** om de verbinding te verifiëren en klik vervolgens op **OK**.

AEM kan nu communiceren met Adobe Campaign.

>[!NOTE]
>
>Zorg ervoor dat uw Adobe Campaign-server via internet bereikbaar is. AEM as a Cloud Service heeft geen toegang tot particuliere netwerken.

## Het vormen van de AEM ExternalAlizer {#externalizer}

ExternalAlizer is de dienst OSGi in AEM die een middelweg in een externe en absolute URL omzet, die voor AEM noodzakelijk is om inhoud te dienen die de Campagne kan gebruiken.

1. Meld u als beheerder aan bij de AEM-ontwerpinstantie.
1. Bevestig publiceer instantie in de configuratie ExternalAlizer door de statusstortplaats van de diensten OSGi in te controleren [ontwikkelaarsconsole.](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html#osgi-services)
1. Als dit niet correct is, breng de noodzakelijke veranderingen in de overeenkomstige instantie git bewaarplaats aan en dan [Implementeer de configuratie met gebruik van cloudbeheer.](/help/implementing/cloud-manager/deploy-code.md)

```text
Service 3310 - [com.day.cq.commons.externalizer] (pid: com.day.cq.commons.impl.externalizerImpl)",
"  from Bundle 420 - Day Communique 5 Commons Library (com.day.cq.cq-commons), version 5.12.16",
"    component.id: 2149",
"    component.name: com.day.cq.commons.impl.externalizerImpl",
"    externalizer.contextpath: ",
"    externalizer.domains: [local https://author-p17558-e33255-cmstg.adobeaemcloud.com, author https://author-p17558-e33255-cmstg.adobeaemcloud.com,
     publish https://publish-p17558-e33255-cmstg.adobeaemcloud.com]",
"    externalizer.encodedpath: false",
"    externalizer.host: ",
"    feature-origins: [com.day.cq:cq-quickstart:slingosgifeature:cq-platform-model_quickstart_author:6.6.0-V23085]",
"    service.bundleid: 420",
"    service.description: Creates absolute URLs",
"    service.scope: bundle",
"    service.vendor: Adobe Systems Incorporated",
```

>[!NOTE]
>
>De publicatie-instantie moet bereikbaar zijn vanaf de Adobe Campaign-server.

## Het vormen van de campagne-verre Gebruiker in AEM {#configure-user}

Als campagne moet communiceren met AEM, moet u een wachtwoord instellen voor de `campaign-remote` gebruiker in AEM.

1. Meld u aan bij AEM als beheerder.
1. Klik op de hoofdnavigatieconsole op **Gereedschappen** in het linkerspoor.
1. Klik vervolgens op **Beveiliging** -> **Gebruikers** om de gebruikersbeheerconsole te openen.
1. Zoek de `campaign-remote` gebruiker.
1. Selecteer `campaign-remote` gebruiker en klik op **Eigenschappen** om de gebruiker te bewerken.
1. In de **Gebruikersinstellingen bewerken** venster, klikt u op **Wachtwoord wijzigen**.
1. Geef de gebruiker een nieuw wachtwoord op en noteer het wachtwoord op een veilige locatie voor toekomstig gebruik.
1. Klikken **Opslaan** om de wachtwoordwijziging op te slaan.
1. Klikken **Opslaan en sluiten** om de wijzigingen in de `campaign-remote` gebruiker.

## De externe AEM-account configureren in campagne {#acc-setup}

Wanneer [installeren **AEM integratie** pakket in Campaign,](#install-package) er wordt een externe account voor AEM gemaakt. Door deze externe account te configureren, kan Adobe Campaign verbinding maken met AEM as a Cloud Service, waardoor tweerichtingscommunicatie tussen de oplossingen mogelijk is.

1. Meld u met de clientconsole aan bij Adobe Campaign als beheerder.

1. Selecteren **Gereedschappen** -> **Verkenner** in de menubalk.

1. Navigeer in de verkenner naar de **Beheer** > **Platform** > **Externe rekeningen** knooppunt.

   ![Externe rekeningen](assets/external-accounts.png)

1. Zoek de externe AEM. Standaard heeft het de volgende waarden:

   * **Type** - AEM
   * **Label** - AEM
   * **Interne naam** - aemInstance

1. Op de **Algemeen** van dit account, voert u de gebruikersgegevens in die u in het [Wachtwoord voor externe gebruiker voor campagne instellen](#set-campaign-remote-password) stap.

   * **Server** - Het AEM serveradres van de auteur
      * De AEM auteurserver moet van de de serverinstantie van Adobe Campaign Classic bereikbaar zijn.
      * Controleer of het serveradres **niet** eindigt in een slash.
   * **Account** - Standaard is dit de `campaign-remote` gebruiker die u instelt in AEM in het dialoogvenster [Wachtwoord voor externe gebruiker voor campagne instellen](#set-campaign-remote-password) stap.
   * **Wachtwoord** - Dit wachtwoord is hetzelfde als het `campaign-remote` gebruiker die u instelt in AEM in het dialoogvenster [Wachtwoord voor externe gebruiker voor campagne instellen](#set-campaign-remote-password) stap.

1. Selecteer **Ingeschakeld** selectievakje.

1. Klikken **Opslaan**.

Adobe Campaign kan nu communiceren met AEM.

## Volgende stappen {#next-steps}

Met zowel Adobe Campaign Classic als AEM as a Cloud Service geconfigureerd is de integratie nu voltooid.

Je kunt nu leren hoe je een nieuwsbrief kunt maken in Adobe Experience Manager door door te gaan met [dit document.](/help/sites-cloud/authoring/campaign/creating-newsletters.md)
