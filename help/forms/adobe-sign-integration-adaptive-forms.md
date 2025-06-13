---
title: Hoe kan Adobe Acrobat Sign met AEM Forms worden geïntegreerd?
description: Leer hoe te om Adobe Acrobat Sign voor  [!DNL AEM Forms]  as a Cloud Service te vormen?
feature: Adaptive Forms, Acrobat Sign
role: Admin, User
level: Intermediate
exl-id: 609c3072-1c3d-43fa-898a-b4e62db8483b
source-git-commit: 82a3016149645701abe829ad89c493f480956267
workflow-type: tm+mt
source-wordcount: '2022'
ht-degree: 0%

---

# Verbind [!DNL AEM Forms] as a Cloud Service met [!DNL Adobe Acrobat Sign] {#integrate-adobe-sign-with-aem-forms}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6.5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/adobe-sign-integration-adaptive-forms.html#adobe-acrobat-sign-for-government) |
| AEM as a Cloud Service | Dit artikel |

[!DNL Adobe Acrobat Sign] maakt workflows voor e-handtekeningen mogelijk voor adaptieve Forms- en AEM-workflows. E-handtekeningen verbeteren workflows om documenten te verwerken voor juridische documenten, verkoop, salarisadministratie, personeelsbeheer en nog veel meer gebieden.

In een standaard [!DNL Adobe Acrobat Sign] - en Adaptief Forms-scenario vult een gebruiker een adaptief formulier in om een service aan te vragen. Bijvoorbeeld een creditcardaanvraag en een burgerservicepakket. Wanneer een gebruiker het toepassingsformulier invult, verzendt en ondertekent, wordt het formulier naar de serviceprovider verzonden voor verdere actie. Serviceprovider controleert de toepassing en gebruikt [!DNL Adobe Acrobat Sign] om de goedgekeurde toepassing te markeren. AEM Forms steunt zowel Adobe Acrobat Sign als Adobe Acrobat Sign Solutions voor de regering. Afhankelijk van uw licentie en vereisten kunt u AEM Forms integreren in of verbinden met een van de twee oplossingen:

* [AEM Forms verbinden met Adobe Acrobat Sign](#adobe-sign)
* [Connect AEM Forms met Adobe Acrobat Sign Solutions for Government](#adobe-acrobat-sign-for-government)

## AEM Forms verbinden met Adobe Acrobat Sign {#adobe-sign}

Als u **[!DNL AEM Forms]** wilt verbinden met **[!DNL Adobe Acrobat Sign]** , stelt u de software en accounts in die worden vermeld in de sectie met voorwaarden, en configureert u de Adobe Sign Cloud Service in uw Forms as a Cloud Service Author and Publish-instanties:

### Vereisten om AEM Forms te verbinden met Adobe Acrobat Sign {#prerequisites-for-adobe-sign}

U hebt de volgende instellingen nodig om [!DNL Adobe Acrobat Sign] te integreren met [!DNL AEM Forms] :

1. Een actieve [ de ontwikkelaarsrekening van Adobe Acrobat Sign.](https://www.adobe.com/acrobat/business/developer-form.html)
1. Een [ toepassing van Adobe Acrobat Sign API ](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/create_app.md).
1. Referenties (client-id en clientgeheim) van [!DNL Adobe Acrobat Sign] API-toepassing.
1. (Slechts voor op identiteitskaart-Gebaseerde authentificatie van de Regering) [ laat de authentificatiemethode ](https://helpx.adobe.com/sign/using/adobesign-authentication-government-id.html#AuditReport) voor de authentificatie van identiteitskaart van de Regering toe.

### AEM Forms-auteur verbinden en instanties publiceren met Adobe Acrobat Sign {#configure-adobe-sign-with-aem-forms}

Voer de volgende stappen uit nadat aan de voorwaarden is voldaan om [!DNL Adobe Acrobat Sign] met [!DNL AEM Forms] te configureren voor de instanties Auteur.

1. Op de auteursinstantie van AEM Forms, navigeer aan **[!UICONTROL Tools]** ![ hammer ](assets/hammer.png) > **[!UICONTROL General]** > **[!UICONTROL Configuration Browser]**.
1. Selecteer op de pagina **[!UICONTROL Configuration Browser]** de optie **[!UICONTROL Create]** .
1. Geef in het dialoogvenster **[!UICONTROL Create Configuration]** een **[!UICONTROL Title]** voor de configuratie op, schakel **[!UICONTROL Cloud Configurations]** in en selecteer **[!UICONTROL Create]** . Er wordt een configuratiecontainer gemaakt voor de opslag van Cloud Services. Zorg ervoor dat de mapnaam geen ruimte bevat.
1. Navigeer aan **[!UICONTROL Tools]** ![ hamer ](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Acrobat Sign]** en open de configuratiecontainer u in de vorige stap creeerde.

   >[!NOTE]
   >
   >Wanneer u een adaptief formulier maakt, geeft u de naam van de container op in het veld **[!UICONTROL Configuration Container]** .

1. Selecteer op de configuratiepagina **[!UICONTROL Create]** om [!DNL Adobe Acrobat Sign] -configuratie te maken in AEM Forms.
1. Geef op het tabblad **[!UICONTROL General]** van de **[!UICONTROL Create Adobe Acrobat Sign Configuration]** -pagina een **[!UICONTROL Name]** voor de configuratie op en selecteer **[!UICONTROL Next]** . U kunt optioneel een **[!UICONTROL Title]** opgeven en bladeren om een **[!UICONTROL Thumbnail]** voor de configuratie te selecteren.

1. U kunt nu **[!UICONTROL Select solution]** selecteren om [!DNL Adobe Acrobat Sign] te selecteren.

   <!--![Adobe Acrobat Sign Solutions](assets/adobe-sign-solution.png)-->
   ![ Configuratie van Adobe Acrobat Sign Solutions ](assets/adobe-sign-solution-config.png)

<!--

[create URL](#create-a-redirect-url-for-your-aem-instance)
 -->

1. Kopieer de URL in het huidige browservenster naar een aantekenblok en verwijder het onderdeel `/ui#/aem` van de URL. De gewijzigde URL is vervolgens vereist om de [!DNL Adobe Acrobat Sign] -toepassing in een latere stap te configureren met [!DNL AEM Forms] . Selecteer **[!UICONTROL Next]** .

1. Op het tabblad **[!UICONTROL Settings]**
   * het veld **[!UICONTROL OAuth URL]** bevat de standaard-URL, die de Adobe Sign-databaseschakel bevat. De opmaak van de URL is:

     `https://<shard>/public/oauth/v2`

     Bijvoorbeeld:
     `https://secure.na1.echosign.com/public/oauth/v2`

   * het veld **[!UICONTROL Access token URL]** bevat de standaard-URL, die de Adobe Sign-databaseschakel bevat. De opmaak van de URL is:

     `https://<shard>/oauth/v2/token`

     Bijvoorbeeld:
     `https://api.na1.echosign.com/oauth/v2/token`

   waarbij:

   **na1** verwijst naar het standaardgegevensbestandaandeel. U kunt de waarde voor het delen van de database wijzigen. Zorg ervoor dat de [!DNL  Adobe Acrobat Sign] Configuraties van de Wolk aan [ correct richten deelt ](https://helpx.adobe.com/sign/using/identify-account-shard.html).

   >[!NOTE]
   >
   >* Houd **creeer de Configuratie van Adobe Acrobat Sign** open pagina. Sluit het bestand niet. U kunt **Identiteitskaart van de Cliënt terugwinnen** en **Geheime cliënt** na het vormen van montages OAuth voor de [!DNL Adobe Acrobat Sign] toepassing zoals die in volgende stappen wordt beschreven.
   > * Nadat u zich hebt aangemeld bij uw Adobe Sign-account, navigeert u naar **[!UICONTROL Acrobat Sign API]** > **[!UICONTROL API Information]** > **[!UICONTROL REST API Methods Documentation]** > **[!UICONTROL OAuth Access Token]** voor toegang tot informatie over de Adobe Sign OAuth URL en Access Token URL.

1. Configureer OAuth-instellingen voor de [!DNL Adobe Acrobat Sign] -toepassing:

   1. Open een browservenster en meld u aan bij uw [!DNL Adobe Acrobat Sign] -ontwikkelaarsaccount.
   1. Selecteer de toepassing die voor [!DNL AEM Forms] is geconfigureerd en selecteer **[!UICONTROL Configure OAuth for Application]** .
   1. Voeg in het vak **[!UICONTROL Redirect URL]** de URL toe die u in een vorige stap hebt gekopieerd (stap 8) en klik op **[!UICONTROL Save]** .
   1. Schakel het volgende bereik voor de toepassing [!DNL Adobe Acrobat Sign] in en klik op **[!UICONTROL Save]** .

   * [!DNL aggrement_read]
   * [!DNL aggrement_write]
   * [!DNL aggrement_send]
   * [!DNL widget_read]
   * [!DNL widget_write]
   * [!DNL workflow_read]

   >[!NOTE]
   > U kunt de bereikmodifier wijzigen van `self` in `account` rechtstreeks vanuit de gebruikersinterface van AEM, zoals in stap 12 wordt beschreven.

   Voor geleidelijke informatie om montages OAuth voor een [!DNL Adobe Acrobat Sign] toepassing te vormen en de sleutels te verkrijgen, zie [ montages van Auth voor de 2} de ontwikkelaarsdocumentatie van de toepassing {vormen.](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/configure_oauth.md)

   ![ OAuth Config ](/help/forms/assets/oauthconfig-new.png)

1. Ga terug naar de **[!UICONTROL Create Adobe Acrobat Sign Configuration]** pagina. Geef op het tabblad **[!UICONTROL Settings]** de [**[!UICONTROL Client ID]** (ook wel toepassings-id genoemd) en **[!UICONTROL Client Secret]**] op. Gebruik [ identiteitskaart van de Cliënt en Geheim van de Cliënt van de toepassing van Adobe Acrobat Sign ](https://opensource.adobe.com/acrobat-sign/developer_guide/helloworld.html#get-the-app-id-and-secret) u in de vorige stap creeerde.

1. In de sectie [!UICONTROL Authorization Scope] kunt u het bereik wijzigen naar &quot;account&quot; of &quot;zelf&quot; door het voorvoegsel &quot;self&quot; of &quot;account&quot; toe te voegen aan het bereik, indien nodig.
   ![ Reikwijdte van de Vergunning ](/help/forms/assets/authorization-scope.png)

1. Selecteer de optie **[!UICONTROL Enable Adobe Acrobat Sign for attachments]** om bestanden die zijn gekoppeld aan een adaptief formulier, toe te voegen aan het corresponderende [!DNL Adobe Acrobat Sign] -document dat ter ondertekening is verzonden.

1. Selecteer **[!UICONTROL Connect to Adobe Acrobat Sign]**. Wanneer ertoe aangezet voor geloofsbrieven, verstrek **gebruikersbenaming** en **wachtwoord** van de gebruikte rekening terwijl het creëren van [!DNL Adobe Acrobat Sign] toepassing. Klik op **[!UICONTROL Allow Access]** wanneer u wordt gevraagd om het document te bevestigen. `your developer account` Als de gegevens juist zijn en u [!DNL AEM Forms] toegang geeft tot uw [!DNL Adobe Acrobat Sign] -ontwikkelaarsaccount, verschijnt een succesbericht dat lijkt op het volgende.

   ![ Succes van de Configuratie van de Wolk Adobe Acrobat Sign ](assets/adobe-sign-cloud-configuration-success.png)

1. Selecteer **[!UICONTROL Create]** om de [!DNL Adobe Acrobat Sign] -configuratie te maken.

1. Selecteer de configuratie en klik op **[!UICONTROL Publish]** , selecteer de configuratie en klik op **[!UICONTROL Publish]** . De configuratie wordt in overeenkomende publicatieomgevingen gerepliceerd.

1. Herhaal alle bovenstaande stappen op uw ontwikkelaar-, werkgebied- en productieinstanties (afhankelijk van wat er nog over is) om het configureren van [!DNL Adobe Acrobat Sign] met [!DNL AEM Forms] voor uw omgeving te voltooien.

Nu, kunt u [ gebruiken toevoegt de gebieden van Adobe Acrobat Sign aan een AanpassingsVorm ](working-with-adobe-sign.md). Zorg ervoor dat u de configuratiecontainer die voor de Cloud Service wordt gebruikt, toevoegt aan alle Adaptive Forms die voor [!DNL Adobe Acrobat Sign] wordt ingeschakeld. U kunt een configuratiecontainer opgeven met de eigenschappen van een adaptief formulier.

>[!NOTE]
>
> Om de zandbak van het Teken van Adobe te vormen, kunt u de zelfde configuratiestappen volgen zoals die in [ het Teken van Adobe ](#adobe-sign) worden verklaard.

#### Problemen oplossen {#resolve-config-error}

Wanneer u [!DNL Adobe Acrobat Sign] verbindt met [!DNL AEM Forms] en een fout `Unable to authorize access because the client configuration is invalid: invalid_request` vindt zoals aangetoond in onderstaande afbeelding. U lost dit op door de hieronder gegeven stappen te volgen:

![ fout van de Configuratie ](/help/forms/assets/config_error_sign.png)

1. Kopieer de URL in het huidige browservenster naar een aantekenblok en verwijder het onderdeel `/ui#/aem` van de URL.
1. Open een browservenster en meld u aan bij uw [!DNL Adobe Acrobat Sign] -ontwikkelaarsaccount.
1. Selecteer de toepassing die voor [!DNL AEM Forms] is geconfigureerd en selecteer **[!UICONTROL Configure OAuth for Application]** .
1. Voeg in het vak **[!UICONTROL Redirect URL]** de URL toe die u in een vorige stap hebt gekopieerd en klik op **[!UICONTROL Save]** .

## Connect AEM Forms met Adobe Acrobat Sign Solutions for Government {#adobe-acrobat-sign-for-government}

Het verbinden van AEM Forms met Adobe Acrobat Sign Solutions voor de overheid is een proces dat uit meerdere stappen bestaat. Het gaat om:

* Omleidings-URL maken voor uw AEM-instanties
* URL en bereik omleiden delen met het Adobe-team Oplossingen ondertekenen voor de overheid
* Referenties ontvangen van het Adobe-ondertekeningsteam
* Ontvangen gebruikersgegevens gebruiken om AEM Forms te verbinden met Adobe Acrobat Sign Solutions voor de overheid

![ Werkschema van de Regering van het Ondertekenen van Adobe ](/help/forms/assets/adobe-acrobat-sign-govt-workflow.png)


AEM Forms as a Cloud Service biedt ontwikkelings-, stage- en productieomgevingen. U kunt beginnen met het verbinden van uw ontwikkelomgeving voor met Adobe Acrobat Sign Solutions for Government en later het werkgebied en de productieomgevingen verbinden.

### Voordat u begint {#prerequisites-for-adobe-sign-for-acrobat-sign-for-government}

Alvorens u begint AEM Forms met de Oplossing van Adobe Acrobat Sign te verbinden, zorg ervoor dat uw [ Adobe Acrobat Sign Solutions voor de rekening van de Overheid ](https://opensource.adobe.com/acrobat-sign/signgov/gstarted.html#account-provisioning) provisioned is.


### Connect AEM Forms as a Cloud Service met Adobe Acrobat Sign Solutions for Government {#connect-adobe-acrobat-sign-for-government}

#### Een omleidings-URL maken voor uw AEM-instantie

1. Op de de auteursinstantie van Forms as a Cloud Service, navigeer aan **[!UICONTROL Tools]** ![ hammer ](assets/hammer.png) > **[!UICONTROL General]** > **[!UICONTROL Configuration Browser]**.
1. Selecteer op de pagina **[!UICONTROL Configuration Browser]** de optie **[!UICONTROL Create]** .
1. Geef in het dialoogvenster **[!UICONTROL Create Configuration]** een **[!UICONTROL Title]** voor de configuratie op, schakel **[!UICONTROL Cloud Configurations]** in en selecteer **[!UICONTROL Create]** . Er wordt een configuratiecontainer gemaakt voor de opslag van Cloud Services. Zorg ervoor dat de mapnaam geen ruimte bevat.
1. Navigeer aan **[!UICONTROL Tools]** ![ hamer ](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Acrobat Sign]** en open de configuratiecontainer u in de vorige stap creeerde. Wanneer u een adaptief formulier maakt, geeft u de naam van de container op in het veld **[!UICONTROL Configuration Container]** .
1. Selecteer op de configuratiepagina **[!UICONTROL Create]** om [!DNL Adobe Acrobat Sign] -configuratie te maken in AEM Forms.
1. Kopieer de URL van het huidige browservenster naar een aantekenblok en verwijder `/ui#/aem` van de URL. Deze URL wordt `re-direct URL` genoemd.
In de volgende sectie deelt u de instructies `re-direct URL` en `Scopes` met het Adobe-ondertekeningsteam en vraagt u referenties aan (client-id en clientgeheim).

#### Deel de omleiding van URL en het bereik met het Adobe-ondertekeningsteam en ontvang referenties

Het team van Adobe Acrobat Sign for Government Solutions vereist dat `re-direct URL` en het bepaalde bereik zijn ingeschakeld voor uw Adobe Acrobat Sign-toepassing (hieronder vermeld) om referenties te genereren (client-id en clientgeheim) waarmee u AEM Forms kunt verbinden met Adobe Acrobat Sign Solutions for Government.

Deel `scopes` (hieronder vermeld) en `re-direct URL` creeerde en neer de laatste stap van vorige sectie met uw vertegenwoordiger van de Oplossing van de Adobe Acrobat Sign voor de Overheid ([ Adobe Professional Services teamlid ](https://opensource.adobe.com/acrobat-sign/signgov/gstarted.html#password)).

**_Scopes_**

* [!DNL aggrement_read]
* [!DNL aggrement_write]
* [!DNL aggrement_send]
* [!DNL widget_read]
* [!DNL widget_write]
* [!DNL workflow_read]
* [!DNL offline_access]

De vertegenwoordiger genereert en deelt referenties met u. In de volgende sectie gebruikt u de referenties (client-id en clientgeheim) om AEM Forms te verbinden met Adobe Acrobat Sign Solutions for Government.

#### Gebruik de ontvangen referenties om AEM Forms te verbinden met Adobe Acrobat Sign Solutions voor de overheid

1. Open `re-direct URL` in uw browser. U creeerde en noteerde neer `re-direct URL` in de laatste stap van [ tot een omleidingsURL op uw instantie van AEM ](#create-a-redirect-url-for-your-aem-instance) sectie.

1. Geef op het tabblad **[!UICONTROL General]** van de **[!UICONTROL Create Adobe Sign Configuration]** -pagina een **[!UICONTROL Name]** voor de configuratie op en selecteer **[!UICONTROL Next]** . U kunt optioneel een **[!UICONTROL Title]** opgeven en bladeren om een **[!UICONTROL Thumbnail]** voor de configuratie te selecteren. Klik op **[!UICONTROL Next]**.

1. Selecteer [!DNL Adobe Acrobat Sign Solutions for Government] op het tabblad **[!UICONTROL Settings]** van de **[!UICONTROL Create Adobe Sign Configuration]** -pagina voor de optie **[!UICONTROL Select solution]** .


   ![ Adobe Acrobat Sign Solutions voor Regering ](assets/adobe-sign-for-govt.png)

1. Geef in het veld **[!UICONTROL Email]** het e-mailadres op dat aan uw Adobe Acrobat Sign Solutions for Government-account is gekoppeld.

1. Op het tabblad **[!UICONTROL Settings]**
   * het veld **[!UICONTROL OAuth URL]** bevat de standaard-URL, die de Adobe Sign-databaseschakel bevat. De opmaak van de URL is:

     `https://<shard>/api/gateway/adobesignauthservice/api/v1/authorize`

     Bijvoorbeeld:
     `https://secure.na1.adobesign.us/api/gateway/adobesignauthservice/api/v1/authorize`

   * het veld **[!UICONTROL Access token URL]** bevat de standaard-URL, die de Adobe Sign-databaseschakel bevat. De opmaak van de URL is:

     `https://<shard>/api/gateway/adobesignauthservice/api/v1/token`

     Bijvoorbeeld:
     `https://secure.na1.adobesign.us/api/gateway/adobesignauthservice/api/v1/token`

   waarbij:

   **na1** verwijst naar het standaardgegevensbestandaandeel. U kunt de waarde voor het delen van de database wijzigen. Zorg ervoor dat de [!DNL  Adobe Acrobat Sign] Configuraties van de Wolk aan [ correct richten deelt ](https://helpx.adobe.com/sign/using/identify-account-shard.html).

   >[!NOTE]
   >
   > * Nadat u zich hebt aangemeld bij uw Adobe Sign-account, navigeert u naar **[!UICONTROL Acrobat Sign API]** > **[!UICONTROL API Information]** > **[!UICONTROL REST API Methods Documentation]** > **[!UICONTROL OAuth Access Token]** voor toegang tot informatie over de URL van de Adobe Sign Auth en Access Token URL.

1. Gebruik de geloofsbrieven die door Adobe Acrobat Sign voor de vertegenwoordiger van de Oplossing van de Overheid ([ Adobe Professional Services teamlid ]) in de vorige sectie als [**[!UICONTROL Client ID]** en **[!UICONTROL Client Secret]** worden gedeeld.

1. Selecteer de optie **[!UICONTROL Enable Adobe Acrobat Sign for attachments]** om bestanden die zijn gekoppeld aan een adaptief formulier, toe te voegen aan het corresponderende [!DNL Adobe Acrobat Sign] -document dat ter ondertekening is verzonden.

1. Selecteer **[!UICONTROL Connect to Adobe Sign]**. Geef bij de aanwijzing voor referenties de gebruikersnaam en het wachtwoord op van het account dat wordt gebruikt bij het maken van de [!DNL Adobe Acrobat Sign] -toepassing. Klik op **[!UICONTROL Allow Access]** wanneer u wordt gevraagd de toegang voor `your developer account` te bevestigen. Als de gegevens juist zijn en u [!DNL AEM Forms] toegang geeft tot uw [!DNL Adobe Acrobat Sign] -ontwikkelaarsaccount, verschijnt een succesbericht dat lijkt op het volgende.

   ![ Succes van de Configuratie van de Wolk Adobe Acrobat Sign ](assets/adobe-sign-cloud-configuration-success.png)

   <!-- > When prompted for credentials, provide username and password of the account used while creating [!DNL Adobe Acrobat Sign] application. When asked to confirm access for `your developer account`, Click **[!UICONTROL Allow Access]**. -->

1. Selecteer **[!UICONTROL Create]** om de configuratie te maken.

1. Selecteer de configuratie en klik op **[!UICONTROL Publish]** , selecteer de configuratie en klik op **[!UICONTROL Publish]** . De configuratie wordt gerepliceerd naar de overeenkomstige publicatieomgevingen.

1. Herhaal alle bovenstaande stappen op uw ontwikkelaar-, werkgebied- en productieinstanties (afhankelijk van wat er nog over is) om het configureren van [!DNL Adobe Acrobat Sign Solutions for Government] met [!DNL AEM Forms] voor uw omgeving te voltooien.

Nu, kunt u [ gebruiken toevoegt de gebieden van Adobe Acrobat Sign in een AanpassingsVorm ](working-with-adobe-sign.md) of [ Werkschema van AEM ](/help/forms/aem-forms-workflow-step-reference.md#sign-document-step-sign-document-step). Zorg ervoor dat u de configuratiecontainer die voor de Cloud Service-configuratie wordt gebruikt, toevoegt aan alle Adaptive Forms die voor [!DNL Adobe Acrobat Sign] wordt ingeschakeld. U kunt een configuratiecontainer opgeven met de eigenschappen van een adaptief formulier.

## Configureer de [!DNL Adobe Acrobat Sign] planner voor synchronisatie van de ondertekeningsstatus {#configure-adobe-sign-scheduler-to-sync-the-signing-status}

AEM Forms as a Cloud Service, verleent de plannerdienst die de status van ondertekenaars met bepaalde intervallen controleert. De scenario&#39;s waarin u de plannerdienst vormt:

* Als u [ gebruikt voorlegt de vorm (nadat elke ontvanger het ondertekenen ceremonie voltooit) ](/help/forms/working-with-adobe-sign.md#select-adobe-sign-cloud-service-and-signing-order) om een document te ondertekenen, wordt de vorm voorgelegd slechts nadat alle ondertekenaars de vorm hebben ondertekend.
* Als u de [ Stap van het Teken in een Werkschema van AEM ](/help/forms/aem-forms-workflow-step-reference.md#sign-document-step) gebruikt om een document te ondertekenen, wacht de gebarentstap op alle ondertekenaars om het document te ondertekenen, alvorens aan de volgende stap van het werkschema te werk te gaan.

Standaard controleert de [!DNL Adobe Acrobat Sign] Scheduler-services de ondertekenaarreactie na elke 24 uur. U kunt het standaardinterval voor uw milieu veranderen.

Om het standaardinterval te veranderen, specificeer a [ cron uitdrukking ](https://en.wikipedia.org/wiki/Cron#CRON_expression) voor het {**bezit 2} sign.status.exp van de** configuratie van de Dienst van de Configuratie van Adobe Acrobat Sign **.**

Bijvoorbeeld, om de configuratiedienst dagelijks bij 00 in werking te stellen:00 am, plaats het {**bezit 0} sign.status.exp van de** configuratie van de Dienst van de Configuratie van Adobe Acrobat Sign **om `0 0 0 1/1 * ? *` te specificeren.** In het volgende JSON-bestand wordt het voorbeeld weergegeven waarmee de configuratieservice dagelijks om 00:00 uur wordt uitgevoerd:

```json
{
  "sign.status.exp":"0 0 0 1/1 * ? *"
}
```

Om waarden van een configuratie te plaatsen, [ produceer OSGi Configuraties gebruikend AEM SDK ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#generating-osgi-configurations-using-the-aem-sdk-quickstart), en [ stel de configuratie ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en#deployment-process) aan uw instantie van Cloud Service op.

## Veelgestelde vragen

* **Q: Kan ik de pagina van de Handtekening van GovCloud van het Onderteken van Adobe in iframe teruggeven?**
* **A:** ja, kunt u de pagina van de Handtekening van GovCloud van het Teken van Adobe in een iframe teruggeven.

>[!MORELIKETHIS]
>
>* [ e-sign een vorm gebruikend krabbelhandtekeningen ](/help/forms/signing-forms-using-scribble.md)
>* [ Beste praktijken voor het gebruiken van Adobe Acrobat Sign met Aangepaste Forms ](https://medium.com/adobetech/using-adobe-sign-to-e-sign-an-adaptive-form-heres-the-best-way-to-do-it-dc3e15f9b684)
