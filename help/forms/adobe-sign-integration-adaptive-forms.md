---
title: Hoe kan Adobe Acrobat Sign met AEM Forms worden geïntegreerd?
description: Leer hoe u Adobe Acrobat Sign for configureert [!DNL AEM Forms] as a Cloud Service?
feature: Adaptive Forms, Acrobat Sign
role: Admin, User
level: Intermediate
exl-id: 609c3072-1c3d-43fa-898a-b4e62db8483b
source-git-commit: 2128dac489c270d296f86b56ae811556fb5fe87e
workflow-type: tm+mt
source-wordcount: '1946'
ht-degree: 0%

---

# Verbinden [!DNL AEM Forms] as a Cloud Service met [!DNL Adobe Acrobat Sign] {#integrate-adobe-sign-with-aem-forms}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/adobe-sign-integration-adaptive-forms.html#adobe-acrobat-sign-for-government) |
| AEM as a Cloud Service | Dit artikel |

[!DNL Adobe Acrobat Sign] maakt workflows voor e-handtekeningen mogelijk voor adaptieve Forms- en AEM Workflows. E-handtekeningen verbeteren workflows om documenten te verwerken voor juridische documenten, verkoop, salarisadministratie, personeelsbeheer en nog veel meer gebieden.

Normaal [!DNL Adobe Acrobat Sign] en Adaptief Forms-scenario vult een gebruiker een adaptief formulier in om een service aan te vragen. Bijvoorbeeld een creditcardaanvraag en een burgerservicepakket. Wanneer een gebruiker het toepassingsformulier invult, verzendt en ondertekent, wordt het formulier naar de serviceprovider verzonden voor verdere actie. Serviceprovider controleert de toepassing en gebruikt [!DNL Adobe Acrobat Sign] om de goedgekeurde aanvraag te markeren. AEM Forms steunt zowel Adobe Acrobat Sign als Adobe Acrobat Sign Solutions voor de regering. Afhankelijk van uw licentie en vereisten kunt u AEM Forms integreren in of verbinden met een van de twee oplossingen:

* [AEM Forms verbinden met Adobe Acrobat Sign](#adobe-sign)
* [Connect AEM Forms met Adobe Acrobat Sign Solutions for Government](#adobe-acrobat-sign-for-government)

## AEM Forms verbinden met Adobe Acrobat Sign {#adobe-sign}

Verbinding maken **[!DNL AEM Forms]** with **[!DNL Adobe Acrobat Sign]**, stelt u de software en accounts in die in de sectie Voorwaarden worden vermeld, en configureert u de Adobe Sign Cloud Service in uw Forms-exemplaren voor as a Cloud Service auteur en publicatie:

### Vereisten om AEM Forms te verbinden met Adobe Acrobat Sign {#prerequisites-for-adobe-sign}

U hebt de volgende setup nodig om te integreren [!DNL Adobe Acrobat Sign] with [!DNL AEM Forms]:

1. Een actief [Adobe Acrobat Sign Developer Account](https://acrobat.adobe.com/us/en/sign/developer-form.html).
1. An [Adobe Acrobat Sign API-toepassing](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/create_app.md).
1. Credentials (client-id en clientgeheim) van [!DNL Adobe Acrobat Sign] API-toepassing
1. (Alleen voor verificatie op basis van overheidsidentiteitskaart) [De verificatiemethode inschakelen](https://helpx.adobe.com/sign/using/adobesign-authentication-government-id.html#AuditReport) voor verificatie met overheidsidentiteitskaart

### AEM Forms-auteur verbinden en instanties publiceren met Adobe Acrobat Sign {#configure-adobe-sign-with-aem-forms}

Nadat de eerste vereisten op zijn plaats zijn, voer de volgende stappen uit om te vormen [!DNL Adobe Acrobat Sign] with [!DNL AEM Forms] op de instanties Auteur.

1. Navigeer in AEM Forms-auteurinstantie naar **[!UICONTROL Tools]** ![hamer](assets/hammer.png) > **[!UICONTROL General]** > **[!UICONTROL Configuration Browser]**.
1. Op de **[!UICONTROL Configuration Browser]** pagina, selecteert u **[!UICONTROL Create]**.
1. In de **[!UICONTROL Create Configuration]** dialoogvenster, geeft u een **[!UICONTROL Title]** voor de configuratie, laat toe **[!UICONTROL Cloud Configurations]** en selecteert u **[!UICONTROL Create]**. Het leidt tot een configuratiecontainer om Cloud Servicen op te slaan. Zorg ervoor dat de mapnaam geen ruimte bevat.
1. Navigeren naar **[!UICONTROL Tools]** ![hamer](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Acrobat Sign]** en open de configuratiecontainer u in de vorige stap creeerde.

   >[!NOTE]
   >
   >Wanneer u een adaptief formulier maakt, geeft u de naam van de container op in het dialoogvenster **[!UICONTROL Configuration Container]** veld.

1. Selecteer op de configuratiepagina **[!UICONTROL Create]** om [!DNL Adobe Acrobat Sign] in AEM Forms.
1. In de **[!UICONTROL General]** tabblad van het **[!UICONTROL Create Adobe Acrobat Sign Configuration]** pagina, geeft u een **[!UICONTROL Name]** voor de configuratie, en selecteer **[!UICONTROL Next]**. U kunt desgewenst een **[!UICONTROL Title]** en bladert u om een **[!UICONTROL Thumbnail]** voor de configuratie.

1. Nu kunt u **[!UICONTROL Select solution]** om [!DNL Adobe Acrobat Sign].

   ![Adobe Acrobat Sign Solutions](assets/adobe-sign-solution.png)

<!--

[create URL](#create-a-redirect-url-for-your-aem-instance)
 -->

1. Kopieer de URL in het huidige browservenster naar een laptop en verwijder het onderdeel `/ui#/aem` via de URL. De gewijzigde URL wordt dan vereist om te vormen [!DNL Adobe Acrobat Sign] toepassing met [!DNL AEM Forms], in een latere stap. Selecteren **[!UICONTROL Next]**.

1. In de **[!UICONTROL Settings]** tab,
   * de **[!UICONTROL OAuth URL]** bevat het veld de standaard-URL die het Adobe Sign-databasespoor bevat. De opmaak van de URL is:

     `https://<shard>/public/oauth/v2`

     Bijvoorbeeld:
     `https://secure.na1.echosign.com/public/oauth/v2`

   * de **[!UICONTROL Access token URL]** bevat het veld de standaard-URL die het Adobe Sign-databasespoor bevat. De opmaak van de URL is:

     `https://<shard>/oauth/v2/token`

     Bijvoorbeeld:
     `https://api.na1.echosign.com/oauth/v2/token`

   waarbij:

   **nl1** verwijst naar de standaard databasedeelt. U kunt de waarde voor het delen van de database wijzigen. Zorg ervoor dat de [!DNL  Adobe Acrobat Sign] Cloud Configurations verwijzen naar de [correcte Shard](https://helpx.adobe.com/sign/using/identify-account-shard.html).

   >[!NOTE]
   >
   >* Houd de **Adobe Acrobat Sign-configuratie maken** pagina geopend. Sluit het bestand niet. U kunt **Client-id** en **Clientgeheim** na het configureren van OAuth-instellingen voor de [!DNL Adobe Acrobat Sign] zoals beschreven in volgende stappen.
   > * Nadat u zich hebt aangemeld bij uw Adobe Sign-account, navigeert u naar **[!UICONTROL Acrobat Sign API]** > **[!UICONTROL API Information]** > **[!UICONTROL REST API Methods Documentation]** > **[!UICONTROL OAuth Access Token]** voor toegang tot informatie over Adobe Sign OAuth URL en Access Token URL.

1. OAuth-instellingen configureren voor de [!DNL Adobe Acrobat Sign] toepassing:

   1. Een browservenster openen en aanmelden bij uw [!DNL Adobe Acrobat Sign] ontwikkelaarsaccount.
   1. Selecteer de toepassing waarvoor [!DNL AEM Forms]en selecteert u **[!UICONTROL Configure OAuth for Application]**.
   1. In de **[!UICONTROL Redirect URL]** voegt u de URL toe die u in een vorige stap hebt gekopieerd (stap 8) en klikt u op **[!UICONTROL Save]**.
   1. Het volgende bereik inschakelen voor de [!DNL Adobe Acrobat Sign] toepassing en klik **[!UICONTROL Save]**.

   * [!DNL aggrement_read]
   * [!DNL aggrement_write]
   * [!DNL aggrement_send]
   * [!DNL widget_read]
   * [!DNL widget_write]
   * [!DNL workflow_read]

   Voor geleidelijke informatie om montages OAuth voor te vormen [!DNL Adobe Acrobat Sign] en verkrijgen de toetsen, zie [Auteursinstellingen voor de toepassing configureren](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/configure_oauth.md) ontwikkelaarsdocumentatie.

   ![OAuth Config](/help/forms/assets/oauthconfig-new.png)

1. Ga terug naar de **[!UICONTROL Create Adobe Acrobat Sign Configuration]** pagina. In de **[!UICONTROL Settings]** tab, geeft u de [**[!UICONTROL Client ID]** (ook toepassings-id genoemd) en **[!UICONTROL Client Secret]**]. Gebruik de [Client-id en clientgeheim van Adobe Acrobat Sign-toepassing](https://opensource.adobe.com/acrobat-sign/developer_guide/helloworld.html#get-the-app-id-and-secret) die u in de vorige stap hebt gemaakt.

1. Selecteer de **[!UICONTROL Enable Adobe Acrobat Sign for attachments]** aan een adaptief formulier gekoppelde bestanden toevoegen aan de corresponderende [!DNL Adobe Acrobat Sign] document verzonden voor ondertekening.

1. Selecteer **[!UICONTROL Connect to Adobe Acrobat Sign]**. Geef bij de aanwijzing voor referenties de volgende informatie op **gebruikersnaam** en **password** van de account die wordt gebruikt tijdens het maken van [!DNL Adobe Acrobat Sign] toepassing. Wanneer gevraagd om te bevestigen, toegang voor `your developer account`, klik op **[!UICONTROL Allow Access]**. Als de gegevens juist zijn en u [!DNL AEM Forms] om toegang te krijgen tot [!DNL Adobe Acrobat Sign] ontwikkelaarsaccount, een succesbericht dat lijkt op het volgende:

   ![Adobe Acrobat Sign Cloud-configuratie gelukt](assets/adobe-sign-cloud-configuration-success.png)

1. Selecteren **[!UICONTROL Create]** om de [!DNL Adobe Acrobat Sign] configuratie.

1. Selecteer de configuratie en klik op **[!UICONTROL Publish]**, selecteert u de configuratie en klikt u op **[!UICONTROL Publish]**. De configuratie wordt in overeenkomende publicatieomgevingen gerepliceerd.

1. Herhaal alle bovenstaande stappen op uw ontwikkelaar-, werkgebied- en productieinstanties (al naargelang wat er nog over is) om het configureren te voltooien [!DNL Adobe Acrobat Sign] with [!DNL AEM Forms] voor uw omgeving.

Nu kunt u [Adobe Acrobat Sign-velden toevoegen aan een adaptief formulier](working-with-adobe-sign.md). Zorg ervoor dat u de configuratiecontainer die voor de Cloud Service wordt gebruikt toevoegt aan alle Adaptive Forms die voor [!DNL Adobe Acrobat Sign]. U kunt een configuratiecontainer opgeven met de eigenschappen van een adaptief formulier.

>[!NOTE]
>
> Als u de Adobe Sign-sandbox wilt configureren, kunt u dezelfde configuratiestappen volgen als in [Adobe Sign](#adobe-sign).

#### Problemen oplossen {#resolve-config-error}

Wanneer u verbinding maakt [!DNL Adobe Acrobat Sign] with [!DNL AEM Forms] en zoeken naar een fout `Unable to authorize access because the client configuration is invalid: invalid_request` zoals weergegeven in de onderstaande afbeelding. U lost dit op door de hieronder gegeven stappen te volgen:

![Configuratiefout](/help/forms/assets/config_error_sign.png)

1. Kopieer de URL in het huidige browservenster naar een laptop en verwijder het onderdeel `/ui#/aem` via de URL.
1. Een browservenster openen en aanmelden bij uw [!DNL Adobe Acrobat Sign] ontwikkelaarsaccount.
1. Selecteer de toepassing waarvoor [!DNL AEM Forms]en selecteert u **[!UICONTROL Configure OAuth for Application]**.
1. In de **[!UICONTROL Redirect URL]** voegt u de in een vorige stap gekopieerde URL toe en klikt u op **[!UICONTROL Save]**.

## Connect AEM Forms met Adobe Acrobat Sign Solutions for Government {#adobe-acrobat-sign-for-government}

Het verbinden van AEM Forms met Adobe Acrobat Sign Solutions voor de overheid is een proces dat uit meerdere stappen bestaat. Het gaat om:

* Omleidings-URL maken voor uw AEM
* De omleiding van URL en het bereik delen met Adobe Sign Solutions for Government-team
* Referenties ontvangen van het Adobe Sign-team
* Ontvangen gebruikersgegevens gebruiken om AEM Forms te verbinden met Adobe Acrobat Sign Solutions voor de overheid

![Adobe Sign Government Workflow](/help/forms/assets/adobe-acrobat-sign-govt-workflow.png)


AEM Forms as a Cloud Service biedt ontwikkelings-, fase- en productieomgevingen. U kunt beginnen met het verbinden van uw ontwikkelomgeving voor met Adobe Acrobat Sign Solutions for Government en later het werkgebied en de productieomgevingen verbinden.

### Voordat u begint {#prerequisites-for-adobe-sign-for-acrobat-sign-for-government}

Voordat u AEM Forms gaat verbinden met Adobe Acrobat Sign Solution, dient u ervoor te zorgen dat [Adobe Acrobat Sign Solutions for Government](https://opensource.adobe.com/acrobat-sign/signgov/gstarted.html#account-provisioning) account is ingericht.


### Connect AEM Forms as a Cloud Service met Adobe Acrobat Sign Solutions for Government {#connect-adobe-acrobat-sign-for-government}

#### Een omleidings-URL voor uw AEM maken

1. Ga in de as a Cloud Service auteurinstantie van Forms naar **[!UICONTROL Tools]** ![hamer](assets/hammer.png) > **[!UICONTROL General]** > **[!UICONTROL Configuration Browser]**.
1. Op de **[!UICONTROL Configuration Browser]** pagina, selecteert u **[!UICONTROL Create]**.
1. In de **[!UICONTROL Create Configuration]** dialoogvenster, geeft u een **[!UICONTROL Title]** voor de configuratie, laat toe **[!UICONTROL Cloud Configurations]** en selecteert u **[!UICONTROL Create]**. Het leidt tot een configuratiecontainer om Cloud Servicen op te slaan. Zorg ervoor dat de mapnaam geen ruimte bevat.
1. Navigeren naar **[!UICONTROL Tools]** ![hamer](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Acrobat Sign]** en open de configuratiecontainer u in de vorige stap creeerde. Wanneer u een adaptief formulier maakt, geeft u de naam van de container op in het dialoogvenster **[!UICONTROL Configuration Container]** veld.
1. Selecteer op de configuratiepagina **[!UICONTROL Create]** om [!DNL Adobe Acrobat Sign] in AEM Forms.
1. Kopieer de URL van het huidige browservenster naar een laptop en verwijder deze `/ui#/aem` via de URL. Deze URL wordt `re-direct URL`.
In de volgende sectie deelt u de opdracht `re-direct URL` en `Scopes` met Adobe Sign-team en aanvraagreferenties (client-id en clientgeheim).

#### De omleiding van URL en bereik delen met het team van Adobe Sign en referenties ontvangen

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

1. Open de `re-direct URL` in uw browser. U hebt de `re-direct URL` in de laatste stap van de [een omleidings-URL maken op uw AEM-instantie](#create-a-redirect-url-for-your-aem-instance) sectie.

1. In de **[!UICONTROL General]** tabblad van het **[!UICONTROL Create Adobe Sign Configuration]** pagina, geeft u een **[!UICONTROL Name]** voor de configuratie, en selecteer **[!UICONTROL Next]**. U kunt desgewenst een **[!UICONTROL Title]** en bladert u om een **[!UICONTROL Thumbnail]** voor de configuratie. Klik op **[!UICONTROL Next]**.

1. In de **[!UICONTROL Settings]** tabblad van het **[!UICONTROL Create Adobe Sign Configuration]** pagina, voor de **[!UICONTROL Select solution]** selecteert u [!DNL Adobe Acrobat Sign Solutions for Government].


   ![Adobe Acrobat Sign Solutions for Government](assets/adobe-sign-for-govt.png)

1. In de **[!UICONTROL Email]** opgegeven, geeft u het e-mailadres op dat aan uw Adobe Acrobat Sign Solutions for Government-account is gekoppeld.

1. In de **[!UICONTROL Settings]** tab,
   * de **[!UICONTROL OAuth URL]** bevat het veld de standaard-URL die het Adobe Sign-databasespoor bevat. De opmaak van de URL is:

     `https://<shard>/api/gateway/adobesignauthservice/api/v1/authorize`

     Bijvoorbeeld:
     `https://secure.na1.adobesign.us/api/gateway/adobesignauthservice/api/v1/authorize`

   * de **[!UICONTROL Access token URL]** bevat het veld de standaard-URL die het Adobe Sign-databasespoor bevat. De opmaak van de URL is:

     `https://<shard>/api/gateway/adobesignauthservice/api/v1/token`

     Bijvoorbeeld:
     `https://secure.na1.adobesign.us/api/gateway/adobesignauthservice/api/v1/token`

   waarbij:

   **nl1** verwijst naar de standaard databasedeelt. U kunt de waarde voor het delen van de database wijzigen. Zorg ervoor dat de [!DNL  Adobe Acrobat Sign] Cloud Configurations verwijzen naar de [correcte Shard](https://helpx.adobe.com/sign/using/identify-account-shard.html).

   >[!NOTE]
   >
   > * Nadat u zich hebt aangemeld bij uw Adobe Sign-account, navigeert u naar **[!UICONTROL Acrobat Sign API]** > **[!UICONTROL API Information]** > **[!UICONTROL REST API Methods Documentation]** > **[!UICONTROL OAuth Access Token]** voor toegang tot informatie met betrekking tot Adobe Sign Auth URL en Access Token URL.

1. Gebruik de gegevens die worden gedeeld door de vertegenwoordiger van Adobe Acrobat Sign for Government Solution ([Adobe Professional Services-teamlid]) in de vorige sectie als [**[!UICONTROL Client ID]** en **[!UICONTROL Client Secret]**].

1. Selecteer de **[!UICONTROL Enable Adobe Acrobat Sign for attachments]** aan een adaptief formulier gekoppelde bestanden toevoegen aan de corresponderende [!DNL Adobe Acrobat Sign] document verzonden voor ondertekening.

1. Selecteer **[!UICONTROL Connect to Adobe Sign]**. Geef bij de aanwijzing voor referenties de gebruikersnaam en het wachtwoord op van het account dat wordt gebruikt tijdens het maken van [!DNL Adobe Acrobat Sign] toepassing. Wanneer gevraagd om toegang te bevestigen voor `your developer account`, klik op **[!UICONTROL Allow Access]**. Als de gegevens juist zijn en u [!DNL AEM Forms] om toegang te krijgen tot [!DNL Adobe Acrobat Sign] ontwikkelaarsaccount, een succesbericht dat lijkt op het volgende:

   ![Adobe Acrobat Sign Cloud-configuratie gelukt](assets/adobe-sign-cloud-configuration-success.png)

   <!-- > When prompted for credentials, provide username and password of the account used while creating [!DNL Adobe Acrobat Sign] application. When asked to confirm access for `your developer account`, Click **[!UICONTROL Allow Access]**. -->

1. Selecteren **[!UICONTROL Create]** om de configuratie te maken.

1. Selecteer de configuratie en klik op **[!UICONTROL Publish]**, selecteert u de configuratie en klikt u op **[!UICONTROL Publish]**. De configuratie wordt gerepliceerd naar de overeenkomstige publicatieomgevingen.

1. Herhaal alle bovenstaande stappen op uw ontwikkelaar-, werkgebied- en productieinstanties (al naargelang wat er nog over is) om het configureren te voltooien [!DNL Adobe Acrobat Sign Solutions for Government] with [!DNL AEM Forms] voor uw omgeving.

Nu kunt u [Adobe Acrobat Sign-velden toevoegen aan een adaptief formulier gebruiken](working-with-adobe-sign.md) of [AEM](/help/forms/aem-forms-workflow-step-reference.md#sign-document-step-sign-document-step). Zorg ervoor dat u de configuratiecontainer die voor de configuratie van de Cloud Service wordt gebruikt aan al Adaptive Forms toevoegt die voor wordt toegelaten [!DNL Adobe Acrobat Sign]. U kunt een configuratiecontainer opgeven met de eigenschappen van een adaptief formulier.

## Configureren [!DNL Adobe Acrobat Sign] planner om de ondertekeningsstatus te synchroniseren {#configure-adobe-sign-scheduler-to-sync-the-signing-status}

AEM Forms as a Cloud Service, verleent de plannerdienst die de status van ondertekenaars met bepaalde intervallen controleert. De scenario&#39;s waarin u de plannerdienst vormt:

* Als u [Het formulier verzenden (nadat elke ontvanger de ondertekeningsceremonie heeft voltooid)](/help/forms/working-with-adobe-sign.md#select-adobe-sign-cloud-service-and-signing-order) om een document te ondertekenen, wordt het formulier pas verzonden nadat alle ondertekenaars het formulier hebben ondertekend.
* Als u het [Stap aanmelden in een AEM workflow](/help/forms/aem-forms-workflow-step-reference.md#sign-document-step) als u een document wilt ondertekenen, wacht de stap voor ondertekenen tot alle ondertekenaars het document ondertekenen, voordat wordt doorgegaan met de volgende stap van de workflow.

Standaard worden de [!DNL Adobe Acrobat Sign] De diensten van de planner controleren (opiniepeilingen) ondertekeningsreactie na om de 24 uur. U kunt het standaardinterval voor uw milieu veranderen.

Om het standaardinterval te veranderen, specificeer [uitsnijdexpressie](https://en.wikipedia.org/wiki/Cron#CRON_expression) voor de **sign.status.exp** eigendom van de **Adobe Acrobat Sign Configuration Service** configuratie.

Bijvoorbeeld, om de configuratieservice dagelijks bij 00:00 am in werking te stellen, plaats **sign.status.exp** eigendom van de **Adobe Acrobat Sign Configuration Service** te specificeren configuratie `0 0 0 1/1 * ? *`. In het volgende JSON-bestand wordt het voorbeeld weergegeven waarmee de configuratieservice dagelijks om 00:00 uur wordt uitgevoerd:

```json
{
  "sign.status.exp":"0 0 0 1/1 * ? *"
}
```

Om waarden van een configuratie te plaatsen, [OSGi-configuraties genereren met de AEM SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#generating-osgi-configurations-using-the-aem-sdk-quickstart), en [stel de configuratie op](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en#deployment-process) naar de instantie Cloud Service.


>[!MORELIKETHIS]
>
>* [Een formulier elektronisch ondertekenen met scripthandtekeningen](/help/forms/signing-forms-using-scribble.md)
>* [Aanbevolen procedures voor het gebruik van Adobe Acrobat Sign met Adaptive Forms](https://medium.com/adobetech/using-adobe-sign-to-e-sign-an-adaptive-form-heres-the-best-way-to-do-it-dc3e15f9b684)