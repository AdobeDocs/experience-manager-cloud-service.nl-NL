---
title: Hoe kan Adobe Acrobat Sign met AEM Forms worden geïntegreerd?
description: Leer hoe u Adobe Acrobat Sign for configureert [!DNL AEM Forms] as a Cloud Service?
feature: Adaptive Forms
role: User
level: Intermediate
source-git-commit: d9c5934c03b9c5aa91bafa09569d441fc7868937
workflow-type: tm+mt
source-wordcount: '1798'
ht-degree: 0%

---

# Verbinden [!DNL AEM Forms] as a Cloud Service met [!DNL Adobe Acrobat Sign] {#integrate-adobe-sign-with-aem-forms}

[!DNL Adobe Acrobat Sign] maakt workflows voor e-handtekeningen mogelijk voor Adaptive Forms en AEM Workflows. E-handtekeningen verbeteren workflows om documenten te verwerken voor juridische documenten, verkoop, salarisadministratie, personeelsbeheer en nog veel meer gebieden.

Normaal [!DNL Adobe Acrobat Sign] en Adaptief Forms-scenario vult een gebruiker een adaptief formulier in om een service aan te vragen. Bijvoorbeeld een creditcardaanvraag en een burgerservicepakket. Wanneer een gebruiker het toepassingsformulier invult, verzendt en ondertekent, wordt het formulier naar de serviceprovider verzonden voor verdere actie. Serviceprovider controleert de toepassing en gebruikt [!DNL Adobe Acrobat Sign] om de goedgekeurde aanvraag te markeren. AEM Forms steunt zowel Adobe Acrobat Sign als Adobe Acrobat Sign Solutions voor de regering. Afhankelijk van uw licentie en vereisten kunt u AEM Forms integreren in of verbinden met een van de twee oplossingen:

* [AEM Forms verbinden met Adobe Acrobat Sign](#adobe-sign)
* [Connect AEM Forms met Adobe Acrobat Sign Solutions for Government](#adobe-acrobat-sign-for-government)

## AEM Forms verbinden met Adobe Acrobat Sign {#adobe-sign}

Verbinding maken **[!DNL AEM Forms]** with **[!DNL Adobe Acrobat Sign]**, stelt u de software en accounts in die in de sectie Voorwaarden worden vermeld, en configureert u de Adobe Sign Cloud Service in uw Forms-exemplaren voor as a Cloud Service auteur en publicatie:

### Vereisten om AEM Forms te verbinden met Adobe Acrobat Sign {#prerequisites-for-adobe-sign}

U hebt de volgende setup nodig om te integreren [!DNL Adobe Acrobat Sign] with [!DNL AEM Forms]:

1. Een actief [Adobe Acrobat Sign Developer Account](https://acrobat.adobe.com/us/en/sign/developer-form.html).
1. An [Adobe Acrobat Sign API-toepassing](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/create_app.md).
1. Credentials (client-id en clientgeheim) van [!DNL Adobe Acrobat Sign] API-toepassing.
1. (Alleen voor verificatie op basis van overheidsidentiteitskaart) [De verificatiemethode inschakelen](https://helpx.adobe.com/sign/using/adobesign-authentication-government-id.html#AuditReport) voor verificatie met overheidsidentiteitskaart



### AEM Forms-auteur verbinden en instanties publiceren met Adobe Acrobat Sign {#configure-adobe-sign-with-aem-forms}

Nadat de eerste vereisten op zijn plaats zijn, voer de volgende stappen uit om te vormen [!DNL Adobe Acrobat Sign] with [!DNL AEM Forms] op de instanties Auteur.

1. Navigeer in AEM Forms-auteurinstantie naar **[!UICONTROL Tools]** ![hamer](assets/hammer.png) > **[!UICONTROL General]** > **[!UICONTROL Configuration Browser]**.
1. Op de **[!UICONTROL Configuration Browser]** pagina, tikken **[!UICONTROL Create]**.
1. In de **[!UICONTROL Create Configuration]** dialoogvenster, geeft u een **[!UICONTROL Title]** voor de configuratie, laat toe **[!UICONTROL Cloud Configurations]** en tikken **[!UICONTROL Create]**. Het leidt tot een configuratiecontainer om Cloud Services op te slaan. Zorg ervoor dat de mapnaam geen ruimte bevat.
1. Navigeren naar **[!UICONTROL Tools]** ![hamer](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Acrobat Sign]** en open de configuratiecontainer u in de vorige stap creeerde.

   >[!NOTE]
   >
   >Wanneer u een adaptief formulier maakt, geeft u de naam van de container op in het dialoogvenster **[!UICONTROL Configuration Container]** veld.

1. Tik op de configuratiepagina op **[!UICONTROL Create]** om [!DNL Adobe Acrobat Sign] in AEM Forms.
1. In de **[!UICONTROL General]** tabblad van het dialoogvenster **[!UICONTROL Create Adobe Acrobat Sign Configuration]** pagina, geeft u een **[!UICONTROL Name]** voor de configuratie en tik **[!UICONTROL Next]**. U kunt desgewenst een **[!UICONTROL Title]** en blader om een **[!UICONTROL Thumbnail]** voor de configuratie.

1. Nu kunt u **[!UICONTROL Select solution]** om [!DNL Adobe Acrobat Sign].

   ![Adobe Acrobat Sign Solutions for Government](assets/adobe-sign-solution.png)

1. Kopieer de URL in het huidige browservenster naar een laptop en verwijder het onderdeel `/ui#/aem` via de URL. De gewijzigde URL wordt dan vereist om te vormen [!DNL Adobe Acrobat Sign] toepassing met [!DNL AEM Forms], in een latere stap. Tik op **[!UICONTROL Next]**.

1. In de **[!UICONTROL Settings]** de **[!UICONTROL OAuth URL]** bevat de standaard-URL. De opmaak van de URL is:

   `https://<shard>/public/oAuth/v2`

   Bijvoorbeeld:
   `https://secure.na1.echosign.com/public/oauth/v2`

   waarbij:

   **nl1** verwijst naar de standaard databasedeelt. U kunt de waarde voor het delen van de database wijzigen. Zorg ervoor dat de [!DNL  Adobe Acrobat Sign] Cloud Configurations verwijzen naar de [correcte Shard](https://helpx.adobe.com/sign/using/identify-account-shard.html).

   Als u een andere [!DNL Adobe Acrobat Sign] configuratie voor een Adobe Experience Manager-functie of -component, moet u ervoor zorgen dat alle [!DNL Adobe Acrobat Sign] Cloud Configurations verwijzen naar hetzelfde segment.

   >[!NOTE]
   >
   > De **Adobe Acrobat Sign-configuratie maken** pagina geopend. Sluit het bestand niet. U kunt **Client-id** en **Clientgeheim** na het configureren van OAuth-instellingen voor de [!DNL Adobe Acrobat Sign] zoals beschreven in volgende stappen.


1. OAuth-instellingen configureren voor de [!DNL Adobe Acrobat Sign] toepassing:

   1. Een browservenster openen en aanmelden bij uw [!DNL Adobe Acrobat Sign] ontwikkelaarsaccount.
   1. Selecteer de toepassing waarvoor [!DNL AEM Forms]en tikken **[!UICONTROL Configure OAuth for Application]**.
   1. In de **[!UICONTROL Redirect URL]** voegt u de URL toe die u in een vorige stap hebt gekopieerd (stap 8) en klikt u op **[!UICONTROL Save]**.
   1. Het volgende bereik inschakelen voor de [!DNL Adobe Acrobat Sign] toepassing en klik **[!UICONTROL Save]**.

   * [!DNL aggrement_read]
   * [!DNL aggrement_write]
   * [!DNL aggrement_send]
   * [!DNL widget_read]
   * [!DNL widget_write]
   * [!DNL workflow_read]

   Voor geleidelijke informatie om montages OAuth voor te vormen [!DNL Adobe Acrobat Sign] en verkrijgen de toetsen, zie [Auteursinstellingen voor de toepassing configureren](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/configure_oauth.md) ontwikkelaarsdocumentatie.

   ![OAuth Config](assets/oauthconfig_new.png)

1. Ga terug naar de **[!UICONTROL Create Adobe Acrobat Sign Configuration]** pagina. In de **[!UICONTROL Settings]** tab, geeft u de [**[!UICONTROL Client ID]** (ook toepassings-id genoemd) en **[!UICONTROL Client Secret]**]. Gebruik de [Client-id en clientgeheim van Adobe Acrobat Sign-toepassing](https://opensource.adobe.com/acrobat-sign/developer_guide/helloworld.html#get-the-app-id-and-secret) die u in de vorige stap hebt gemaakt.

1. Selecteer **[!UICONTROL Enable Adobe Acrobat Sign for attachments]** aan een adaptief formulier gekoppelde bestanden toevoegen aan de corresponderende [!DNL Adobe Acrobat Sign] document verzonden voor ondertekening.

1. Tik op **[!UICONTROL Connect to Adobe Acrobat Sign]**. Geef bij de aanwijzing voor referenties de volgende informatie op **gebruikersnaam** en **password** van de account die wordt gebruikt tijdens het maken van [!DNL Adobe Acrobat Sign] toepassing. Wanneer gevraagd om te bevestigen, toegang voor `your developer account`, klik op **[!UICONTROL Allow Access]**. Als de gegevens juist zijn en u [!DNL AEM Forms] om toegang te krijgen tot uw [!DNL Adobe Acrobat Sign] ontwikkelaarsaccount, een succesbericht dat lijkt op het volgende:

   ![Adobe Acrobat Sign Cloud-configuratie gelukt](assets/adobe-sign-cloud-configuration-success.png)

1. Tikken **[!UICONTROL Create]** om de [!DNL Adobe Acrobat Sign] configuratie.

1. Selecteer de configuratie en klik op **[!UICONTROL Publish]**, selecteert u de configuratie en klikt u op **[!UICONTROL Publish]**. De configuratie wordt in overeenkomende publicatieomgevingen gerepliceerd.

1. Herhaal alle bovenstaande stappen op uw ontwikkelaar-, werkgebied- en productieinstanties (al naargelang wat er nog over is) om het configureren te voltooien [!DNL Adobe Acrobat Sign] with [!DNL AEM Forms] voor uw omgeving.

Nu kunt u [Adobe Acrobat Sign-velden toevoegen aan een adaptief formulier](working-with-adobe-sign.md). Zorg ervoor dat u de configuratiecontainer die voor de Cloud Service wordt gebruikt toevoegt aan alle Adaptive Forms die voor [!DNL Adobe Acrobat Sign]. U kunt een configuratiecontainer opgeven op basis van de eigenschappen van een adaptief formulier.

## Connect AEM Forms met Adobe Acrobat Sign Solutions for Government {#adobe-acrobat-sign-for-government}

[!BADGE pre-releasedocumentatie]{type=Caution tooltip="Gele status"}
<span class="preview"> Deze sectie bevat pre-releasedocumentatie en kan worden gewijzigd.</span>

AEM Forms verbinden met Adobe Acrobat Sign Solutions voor de overheid is een proces dat uit meerdere stappen bestaat. Het gaat om:

* Omleidings-URL maken voor uw AEM
* De omleiding van URL en het bereik delen met Adobe Sign Solutions for Government-team
* Referenties ontvangen van het Adobe Sign-team
* Ontvangen gebruikersgegevens gebruiken om AEM Forms te verbinden met Adobe Acrobat Sign Solutions voor de overheid

![](/help/forms/assets/adobe-acrobat-sign-govt-workflow.png)


AEM Forms as a Cloud Service biedt ontwikkelings-, fase- en productieomgevingen. U kunt beginnen met het verbinden van uw ontwikkelomgeving voor met Adobe Acrobat Sign Solutions for Government en later het werkgebied en de productieomgevingen verbinden.

### Voordat u begint {#prerequisites-for-adobe-sign-for-acrobat-sign-for-government}

Voordat u AEM Forms gaat verbinden met Adobe Acrobat Sign Solution, dient u ervoor te zorgen dat [Adobe Acrobat Sign Solutions for Government](https://opensource.adobe.com/acrobat-sign/signgov/gstarted.html#account-provisioning) account is ingericht.


### Connect AEM Forms as a Cloud Service met Adobe Acrobat Sign Solutions for Government {#connect-adobe-acrobat-sign-for-government}

#### Een omleidings-URL maken voor uw AEM-instantie

1. Ga in de as a Cloud Service auteurinstantie van Forms naar **[!UICONTROL Tools]** ![hamer](assets/hammer.png) > **[!UICONTROL General]** > **[!UICONTROL Configuration Browser]**.
1. Op de **[!UICONTROL Configuration Browser]** pagina, tikken **[!UICONTROL Create]**.
1. In de **[!UICONTROL Create Configuration]** dialoogvenster, geeft u een **[!UICONTROL Title]** voor de configuratie, laat toe **[!UICONTROL Cloud Configurations]** en tikken **[!UICONTROL Create]**. Het leidt tot een configuratiecontainer om Cloud Services op te slaan. Zorg ervoor dat de mapnaam geen ruimte bevat.
1. Navigeren naar **[!UICONTROL Tools]** ![hamer](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Acrobat Sign]** en open de configuratiecontainer u in de vorige stap creeerde. Wanneer u een adaptief formulier maakt, geeft u de naam van de container op in het dialoogvenster **[!UICONTROL Configuration Container]** veld.
1. Tik op de configuratiepagina op **[!UICONTROL Create]** om [!DNL Adobe Acrobat Sign] in AEM Forms.
1. Kopieer de URL van het huidige browservenster naar een laptop en verwijder deze `/ui#/aem` via de URL. Deze URL wordt `re-direct URL`. In de volgende sectie deelt u de opdracht `re-direct URL` en `Scopes` met Adobe Sign-team en aanvraagreferenties (client-id en clientgeheim).


#### Deel de omleiding URL en het bereik met het team van Adobe Sign en ontvang geloofsbrieven

Het Adobe Acrobat Sign for Government Solutions-team heeft `re-direct URL` en het bepaalde bereik dat voor uw Adobe Acrobat Sign-toepassing (hieronder vermeld) moet worden ingeschakeld om referenties te genereren (client-id en clientgeheim) waarmee u AEM Forms kunt verbinden met Adobe Acrobat Sign Solutions for Government.

Deel de `scopes` (zie hieronder) en de `re-direct URL` gemaakt en genoteerd als laatste stap in de vorige sectie met uw Adobe Acrobat Sign for Government Solution-vertegenwoordiger ([Adobe Professional Services-teamlid](https://opensource.adobe.com/acrobat-sign/signgov/gstarted.html#password)).

**_Segmenten_**

* [!DNL aggrement_read]
* [!DNL aggrement_write]
* [!DNL aggrement_send]
* [!DNL widget_read]
* [!DNL widget_write]
* [!DNL workflow_read]
* [!DNL offline_access]

De vertegenwoordiger genereert en deelt referenties met u. In de volgende sectie gebruikt u de referenties (client-id en clientgeheim) om AEM Forms te verbinden met Adobe Acrobat Sign Solutions for Government.

#### Gebruik de ontvangen referenties om AEM Forms te verbinden met Adobe Acrobat Sign Solutions voor de overheid

1. Open de `re-direct URL` in uw browser. U hebt de `re-direct URL` in de laatste stap van de [een omleidings-URL maken op uw AEM-instantie](#create-redirect-url) sectie.

1. In de **[!UICONTROL General]** tabblad van het dialoogvenster **[!UICONTROL Create Adobe Sign Configuration]** pagina, geeft u een **[!UICONTROL Name]** voor de configuratie en tik **[!UICONTROL Next]**. U kunt desgewenst een **[!UICONTROL Title]** en blader om een **[!UICONTROL Thumbnail]** voor de configuratie. Klik op **[!UICONTROL Next]**.

1. In de **[!UICONTROL Settings]** tabblad van het dialoogvenster **[!UICONTROL Create Adobe Sign Configuration]** pagina, voor de **[!UICONTROL Select solution]** selecteert u [!DNL Adobe Acrobat Sign Solutions for Government].

   ![Adobe Acrobat Sign Solutions for Government](assets/adobe-sign-for-govt.png)

1. In de **[!UICONTROL Email]** opgegeven, geeft u het e-mailadres op dat aan uw Adobe Acrobat Sign Solutions for Government-account is gekoppeld.

1. De **[!UICONTROL OAuth URL]** in het veld wordt de Adobe Sign-databaseschijf opgegeven. Het veld bevat de standaard-URL. Wijzig de URL niet.

1. Gebruik de gegevens die worden gedeeld door de vertegenwoordiger van Adobe Acrobat Sign for Government Solution ([Adobe Professional Services-teamlid]) in de vorige sectie als [**[!UICONTROL Client ID]** en **[!UICONTROL Client Secret]**].

1. Selecteer **[!UICONTROL Enable Adobe Acrobat Sign for attachments]** aan een adaptief formulier gekoppelde bestanden toevoegen aan de corresponderende [!DNL Adobe Acrobat Sign] document verzonden voor ondertekening.

1. Tik op **[!UICONTROL Connect to Adobe Sign]**. Geef bij de aanwijzing voor referenties de gebruikersnaam en het wachtwoord op van het account dat wordt gebruikt tijdens het maken van [!DNL Adobe Acrobat Sign] toepassing. Wanneer gevraagd om toegang te bevestigen voor `your developer account`, klik op **[!UICONTROL Allow Access]**. Als de gegevens juist zijn en u [!DNL AEM Forms] om toegang te krijgen tot uw [!DNL Adobe Acrobat Sign] ontwikkelaarsaccount, een succesbericht dat lijkt op het volgende:

   ![Adobe Acrobat Sign Cloud-configuratie gelukt](assets/adobe-sign-cloud-configuration-success.png)

   <!-- > When prompted for credentials, provide username and password of the account used while creating [!DNL Adobe Acrobat Sign] application. When asked to confirm access for `your developer account`, Click **[!UICONTROL Allow Access]**. -->

1. Tikken **[!UICONTROL Create]** om de configuratie te maken.

1. Selecteer de configuratie en klik op **[!UICONTROL Publish]**, selecteert u de configuratie en klikt u op **[!UICONTROL Publish]**. De configuratie wordt gerepliceerd naar de overeenkomstige publicatieomgevingen.

1. Herhaal alle bovenstaande stappen op uw ontwikkelaar-, werkgebied- en productieinstanties (al naargelang wat er nog over is) om het configureren te voltooien [!DNL Adobe Acrobat Sign Solutions for Government] with [!DNL AEM Forms] voor uw omgeving.

Nu kunt u [Adobe Acrobat Sign-velden toevoegen aan een adaptief formulier gebruiken](working-with-adobe-sign.md) of [AEM](/help/forms/aem-forms-workflow-step-reference.md#sign-document-step-sign-document-step). Zorg ervoor dat u de configuratiecontainer die voor de configuratie van de Cloud Service wordt gebruikt aan al Adaptive Forms toevoegt die voor wordt toegelaten [!DNL Adobe Acrobat Sign]. U kunt een configuratiecontainer opgeven op basis van de eigenschappen van een adaptief formulier.

## (Alleen voor AEM workflows) Configureren [!DNL Adobe Acrobat Sign] planner om de ondertekeningsstatus te synchroniseren {#configure-adobe-sign-scheduler-to-sync-the-signing-status}

Wanneer u [!DNL Adobe Acrobat Sign] Workflowstap voor het ondertekenen van een adaptief formulier: het formulier kan door ondertekenaars worden doorgegeven of tegelijkertijd naar alle ondertekenaars worden verzonden, afhankelijk van de configuratie van de workflowstap. [!DNL Adobe Acrobat Sign] Aangepaste adaptieve Forms worden alleen naar Experience Manager Forms Server verzonden nadat alle ondertekenaars het ondertekeningsproces hebben voltooid.

Standaard worden de [!DNL Adobe Acrobat Sign] De diensten van de planner controleren (opiniepeilingen) ondertekeningsreactie na om de 24 uur. U kunt het standaardinterval voor uw milieu veranderen.

Als u het standaardinterval wilt wijzigen, geeft u een [uitsnijdexpressie](https://en.wikipedia.org/wiki/Cron#CRON_expression) voor de **sign.status.exp** eigendom van de **Adobe Acrobat Sign Configuration Service** configuratie.

Bijvoorbeeld, om de configuratieservice dagelijks bij 00:00 am in werking te stellen, plaats **sign.status.exp** eigendom van de **Adobe Acrobat Sign Configuration Service** te specificeren configuratie `0 0 0 1/1 * ? *`. In het volgende JSON-bestand wordt het voorbeeld weergegeven waarmee de configuratieservice dagelijks om 00:00 uur wordt uitgevoerd:

```json
{
  "sign.status.exp":"0 0 0 1/1 * ? *"
}
```

Om waarden van een configuratie te plaatsen, [OSGi-configuraties genereren met de AEM SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#generating-osgi-configurations-using-the-aem-sdk-quickstart), en [stel de configuratie op](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en#deployment-process) naar de instantie Cloud Service.


## Verwante artikelen {#related-articles}

* [Adobe Acrobat Sign gebruiken in een adaptief formulier](working-with-adobe-sign.md)

* [Aanbevolen procedures voor het gebruik van Adobe Acrobat Sign met Adaptive Forms](https://medium.com/adobetech/using-adobe-sign-to-e-sign-an-adaptive-form-heres-the-best-way-to-do-it-dc3e15f9b684)
