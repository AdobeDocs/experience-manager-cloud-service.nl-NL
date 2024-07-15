---
title: Beheer  [!DNL Adobe Stock]  activa in  [!DNL Assets].
description: Onderzoek, haal, vergunning, en beheer  [!DNL Adobe Stock]  activa van binnen  [!DNL Adobe Experience Manager]. Gebruik de in licentie gegeven activa als elk ander digitaal actief.
contentOwner: Vishabh Gupta
feature: Adobe Stock
role: Admin, User
exl-id: 13f21d79-2a8d-4cb1-959e-c10cc44950ea
source-git-commit: ab2cf8007546f538ce54ff3e0b92bb0ef399c758
workflow-type: tm+mt
source-wordcount: '2305'
ht-degree: 2%

---

# [!DNL Adobe Stock] -elementen gebruiken in [!DNL Adobe Experience Manager Assets] {#use-adobe-stock-assets-in-aem-assets}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/aem-assets-adobe-stock.html?lang=en) |
| AEM as a Cloud Service | Dit artikel |

[!DNL Adobe Stock] biedt ontwerpers en bedrijven toegang tot miljoenen kwalitatief hoogstaande, gekrulde, royaltyvrije foto&#39;s, vectoren, illustraties, video&#39;s, sjablonen en 3D-middelen voor al hun creatieve projecten.

[!DNL Adobe Stock] voor zakelijke aanbiedingen, die standaard deelrechten voor de hele organisatie bevatten. Zodra een middel door een gebruiker van uw organisatie is vergunning gegeven, kunnen andere gebruikers van uw organisatie, dit middel identificeren downloaden en gebruiken zonder het moeten het opnieuw vergunning geven. Zodra een activa door uw organisatie zijn vergunning gegeven, is het recht om het te gebruiken onvoorwaardelijk.

Organisaties kunnen hun [!DNL Adobe Stock] Enterprise-plan integreren met [!DNL Experience Manager Assets] om ervoor te zorgen dat middelen met licentie breed beschikbaar zijn voor hun creatieve en marketingprojecten, met de krachtige mogelijkheden voor middelenbeheer van [!DNL Experience Manager] . [!DNL Experience Manager] -gebruikers kunnen snel Adobe Stock-elementen zoeken, voorvertonen en in licentie geven die zijn opgeslagen in [!DNL Experience Manager] , zonder de interface van [!DNL Experience Manager] te verlaten.

## Integeren [!DNL Experience Manager] en [!DNL Adobe Stock] {#integrate-aem-and-adobe-stock}

[!DNL Experience Manager Assets] biedt gebruikers de mogelijkheid om [!DNL Adobe Stock] -elementen rechtstreeks vanuit [!DNL Experience Manager] te zoeken, te bekijken, op te slaan en in licentie te geven.

**Eerste vereisten**

De integratie vereist:

* Een [!DNL Experience Manager Assets] up and running als een [!DNL Cloud Service] -instantie
* Een [ ondernemings  [!DNL Adobe Stock]  plan ](https://stockenterprise.adobe.com/)
* Een gebruiker met machtigingen in Admin Console naar het standaardprofiel voor het product Stock
* Een gebruiker met machtigingen voor het Developer Access-profiel voor het maken van integratie in Adobe Developer Console

An enterprise [!DNL Adobe Stock] plan,

* Biedt productmachtigingen voor [!DNL Adobe Stock] (voorraden die zijn verbonden met Experience Manager)
* Crediteringen die zijn aangeschaft in de [!DNL Adobe Admin Console] voor uw aandelenrechten
* Hiermee schakelt u JWT-verificatie (Service Account) binnen [!DNL Adobe Developer Console] in voor uw aandelenrechten
* Hiermee kunt u de credits en licenties globaal beheren vanuit [!DNL Adobe Admin Console]

Binnen de machtiging bestaat er een standaardproductprofiel voor [!DNL Adobe Stock] in [!DNL Admin Console] . Er kunnen meerdere profielen worden gemaakt en deze profielen bepalen wie een licentie voor de activa van Stock kan verkrijgen. Een gebruiker die een directe toegang tot het productprofiel heeft kan tot [ https://stock.adobe.com/ ](https://stock.adobe.com/) toegang hebben en de activa van de Beeld van de vergunning. Terwijl er een andere methode is om de Toegang van de Ontwikkelaar te gebruiken om een integratie (API) tot stand te brengen. Deze integratie verifieert de communicatie tussen [!DNL Experience Manager Assets] en [!DNL Adobe Stock].

>[!NOTE]
>
>De beurswaarde van de &quot;Stock Service Account&quot; (JWT) wordt geleverd met de beurswaarde van de onderneming.
>
>De integratie ondersteunt geen Oauth-authenticatie voor aandelenrechten voor bedrijven.


<!--
### Create an IMS configuration {#create-an-ims-configuration}

1. In the [!DNL Experience Manager] user interface, navigate to **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**. Click **[!UICONTROL Create]** and select **[!UICONTROL Cloud Solution]** > **[!UICONTROL Adobe Stock]**.
1. Either reuse an existing certificate or select **[!UICONTROL Create new certificate]**.
1. Click **[!UICONTROL Create certificate]**. Once created, download the public key. Click **[!UICONTROL Next]**. Leave the [!UICONTROL Adobe IMS Technical Account Configuration] screen open to provide the required values shortly.
1. Access [Adobe Developer Console](https://console.adobe.io). Ensure that your account has administrator permissions for the organization for which the integration is required.
1. Click **[!UICONTROL Create new project]** and click **[!UICONTROL Add API]**. Select **[!UICONTROL Adobe Stock]** from the list of APIs that are available to you. Select [!UICONTROL OAUTH 2.0 Web].
1. Provide **[!UICONTROL Default redirect URI]** and **[!UICONTROL Redirect URI pattern]** values. Click **[!UICONTROL Save configured API]**. Copy the generated ID and secret.
1. In [!UICONTROL Adobe IMS Technical Account Configuration] screen, provide the values in the boxes titled **[!UICONTROL Title]**, **[!UICONTROL Authorization Server]**, **[!UICONTROL API Key]**, **[!UICONTROL Client Secret]**, and **[!UICONTROL Payload]**. For detailed information about these values, see [JWT authentication quick start](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/JWT/JWT.md).

-->
<!-- TBD: Update the URL to update the terminology when AIO team updates their documentation URL. Logged issue github.com/AdobeDocs/adobeio-auth/issues/63.
-->

<!--
### Create [!DNL Adobe Stock] configuration in [!DNL Experience Manager] {#create-adobe-stock-configuration-in-aem}

1. In the [!DNL Experience Manager], navigate to **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Stock]**.
1. Click **[!UICONTROL Create]** to create a configuration and associate it with your existing IMS Configuration. Select `PROD` as the environment parameter.
1. In **[!UICONTROL Licensed Assets Path]** field, leave a location as is. Do not change the location where you want to store the [!DNL Adobe Stock] assets.
1. Complete creation by adding all the required properties. Click **[!UICONTROL Save & Close]**.
1. Add [!DNL Experience Manager] users or groups, who can license the assets.

>[!NOTE]
>
>If there are multiple [!DNL Adobe Stock] configurations, select the desired configuration in User Preferences panel. To access the panel from Experience Manager home page, click the user icon and then click **[!UICONTROL User Preferences]** > **[!UICONTROL Stock Configuration]**.

-->

## Stappen voor integratie [!DNL Experience Manager] en [!DNL Adobe Stock] {#integration-steps}

Voer de volgende stappen uit in de vermelde reeks om [!DNL Experience Manager] en [!DNL Adobe Stock] te integreren:

1. [Openbaar certificaat verkrijgen](#public-certificate)

   Maak in [!DNL Experience Manager] een IMS-account en genereren een openbaar certificaat (openbare sleutel).

1. [ creeer de dienstrekening (JWT) verbinding ](#createnewintegration)

   Maak in [!DNL Adobe Developer Console] een project voor uw [!DNL Adobe Stock] -organisatie. Onder het project, vorm API gebruikend de openbare sleutel om een verbinding van de de dienstrekening (JWT) tot stand te brengen. Krijg de geloofsbrieven van de de dienstrekening en JWT payload informatie.

1. [IMS-account configureren](#create-ims-account-configuration)

   Configureer in [!DNL Experience Manager] de IMS-account met behulp van de gegevens van de serviceaccount en de JWT-payload.

1. [Cloudservice configureren](#configure-the-cloud-service)

   Configureer in [!DNL Experience Manager] een [!DNL Adobe Stock] -cloudservice met behulp van de IMS-account.


### Een IMS-configuratie maken {#create-an-ims-configuration}

De IMS-configuratie verifieert de [!DNL Experience Manager Assets] auteurinstantie met de [!DNL Adobe Stock] -machtiging.

De IMS-configuratie omvat twee stappen:

* [Openbaar certificaat verkrijgen](#public-certificate)
* [IMS-account configureren](#create-ims-account-configuration)

### Openbaar certificaat verkrijgen {#public-certificate}

Met de openbare sleutel (certificaat) wordt uw productprofiel in Adobe Developer Console geverifieerd.

1. Meld u aan bij uw [!DNL Experience Manager Assets] cloud-instantie.

1. Navigeer in het deelvenster **[!UICONTROL Tools]** naar **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]** .

1. Klik op **[!UICONTROL Create]** op de pagina Adobe IMS Configurations. De pagina **[!UICONTROL Adobe IMS Technical Account Configuration]** wordt geopend.

1. Selecteer op het tabblad **[!UICONTROL Certificate]** **[!UICONTROL Adobe Stock]** in de vervolgkeuzelijst **[!UICONTROL Cloud Solution]** .

1. U kunt een certificaat maken of een bestaand certificaat opnieuw gebruiken voor de configuratie.

   Om een certificaat tot stand te brengen, selecteer het **[!UICONTROL Create new certificate]** controlevakje en specificeer een **alias** voor de openbare sleutel. De alias fungeert als naam voor de openbare sleutel.

1. Klik op **[!UICONTROL Create certificate]**. Klik vervolgens op **[!UICONTROL OK]** om de openbare sleutel te genereren.

1. Klik op het pictogram **[!UICONTROL Download Public Key]** en sla het bestand met de openbare sleutel (.crt) op uw computer op. De openbare sleutel wordt later gebruikt om API voor uw Brand Portal huurder te vormen en de geloofsbrieven van de de dienstrekening in Adobe Developer Console te produceren.

   Klik op **[!UICONTROL Next]**.

   ![ produceren-certificaat ](assets/stock-integration-ims-account.png)

1. In het **lusje van de Rekening**, wordt de rekening van Adobe IMS gecreeerd die de geloofsbrieven van de de dienstrekening vereist.

   Open een nieuw lusje en [ creeer een de dienstrekening (JWT) verbinding in Adobe Developer Console ](#createnewintegration).

### Verbinding voor serviceaccount (JWT) maken {#createnewintegration}

In Adobe Developer Console worden projecten en API&#39;s geconfigureerd op organisatieniveau. Als u een API configureert, wordt een JWT-verbinding (Service Account) gemaakt. Er zijn twee methodes om API te vormen, door een zeer belangrijk paar (privé en openbare sleutels) te produceren of door een openbare sleutel te uploaden. In dit voorbeeld worden de gegevens van de serviceaccount gegenereerd door de openbare sleutel te uploaden.

Om de geloofsbrieven van de de dienstrekening en JWT lading te produceren:

1. Meld u aan bij Adobe Developer Console met systeembeheerdersrechten. Het gebrek URL is [ https://www.adobe.com/go/devs_console_ui ](https://www.adobe.com/go/devs_console_ui).


   Controleer of u de juiste IMS-organisatie (Stock Entitlement) hebt geselecteerd in de vervolgkeuzelijst (organisatie).

1. Klik op **[!UICONTROL Create new project]**. Er wordt een leeg project met een door het systeem gegenereerde naam gemaakt voor uw organisatie.

   Klik op **[!UICONTROL Edit project]**. Werk **[!UICONTROL Project Title]** en **[!UICONTROL Description]** bij en klik vervolgens op **[!UICONTROL Save]** .

1. Klik op het tabblad **[!UICONTROL Project overview]** op **[!UICONTROL Add API]** .

1. Selecteer **[!UICONTROL Adobe Stock]** in de **[!UICONTROL Add an API window]** . Klik op **[!UICONTROL Next]**.

1. Selecteer **[!UICONTROL Service Account (JWT)]** -verificatie in het **[!UICONTROL Configure API]** -venster. Klik op **[!UICONTROL Next]**.

   ![ creeer-jwt-geloofsbrieven ](assets/aem-stock-jwt.png)

1. Klik op **[!UICONTROL Upload your public key]**. Klik **[!UICONTROL Select a File]** en upload de openbare sleutel (.crt dossier) die u in [ hebt gedownload verkrijgen openbare certificaat ](#public-certificate) sectie. Klik op **[!UICONTROL Next]**.

1. Controleer de openbare sleutel en klik op **[!UICONTROL Next]** .

1. Selecteer het standaardproductprofiel van **[!UICONTROL Adobe Stock]** en klik op **[!UICONTROL Save configured API]** .

1. Nadat de API is geconfigureerd, wordt u omgeleid naar de API-overzichtspagina. Klik in de linkernavigatie onder **[!UICONTROL Credentials]** op de optie **[!UICONTROL Service Account (JWT)]** . Hier, kunt u de geloofsbrieven bekijken en acties uitvoeren zoals produceren JWT tokens, exemplaar credentiedetails, en terugwinnen cliëntgeheim.

1. Kopieer de **[!UICONTROL client ID]** vanaf de tab **[!UICONTROL Client Credentials]** .

   Klik op **[!UICONTROL Retrieve Client Secret]** en kopieer de **[!UICONTROL client secret]** .

   ![ produceren-jwt-geloofsbrieven ](assets/aem-stock-jwt-credential.png)

1. Navigeer naar het tabblad **[!UICONTROL Generate JWT]** en kopieer de **[!UICONTROL JWT Payload]** -gegevens.

U kunt cliëntidentiteitskaart (API sleutel), cliëntgeheim, en JWT nuttige lading nu gebruiken om [ de rekening IMS ](#create-ims-account-configuration) in [!DNL Experience Manager Assets] te vormen.

### IMS-account configureren {#create-ims-account-configuration}

U moet het [ certificaat ](#public-certificate) hebben en [ de dienstrekening (JWT) geloofsbrieven ](#createnewintegration) om de rekening te vormen IMS.

De IMS-account configureren:

1. Open de IMS-configuratie en ga naar het tabblad **[!UICONTROL Account]** . U hield de pagina open terwijl [ het openbare certificaat ](#public-certificate) verkrijgen.

1. Geef een **[!UICONTROL Title]** op voor het IMS-account.

   Op het **[!UICONTROL Authorization Server]** gebied, ga URL in: [ https://ims-na1.adobelogin.com/ ](https://ims-na1.adobelogin.com/).

   Ga cliëntidentiteitskaart op het **[!UICONTROL API key]** gebied, **[!UICONTROL Client Secret]**, en **[!UICONTROL Payload]** (JWT nuttige lading) in die u terwijl [ het creëren van de de dienstrekening (JWT) verbinding ](#createnewintegration) hebt gekopieerd.

1. Klik op **[!UICONTROL Create]**. Er wordt een IMS-accountconfiguratie gemaakt.

   ![ vorm-ims-rekening ](assets/aem-stock-ims-config.png)

1. Selecteer de IMS-accountconfiguratie en klik op **[!UICONTROL Check Health]** .

   Klik op **[!UICONTROL Check]** in het dialoogvenster. Voor succesvolle configuratie, lijkt een bericht dat het *Symbolische met succes* wordt teruggewonnen.

   ![ gezondheid-controle ](assets/aem-stock-healthcheck.png)


### Cloudservice configureren {#configure-the-cloud-service}

U kunt als volgt de cloudservice van [!DNL Adobe Stock] configureren:

1. Navigeer in de gebruikersinterface van [!DNL Experience Manager] naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Stock]** .

1. Klik op **[!UICONTROL Create]** op de pagina [!DNL Adobe Stock Configurations] .

1. Geef een **[!UICONTROL Title]** voor de cloudconfiguratie op.

   Selecteer de configuratie IMS die u terwijl [ het vormen van de rekening IMS ](#create-ims-account-configuration) hebt gecreeerd.

   Selecteer de landinstelling in de vervolgkeuzelijst.

   ![ aem-stock-cloud-config ](assets/aem-stock-cloud-config.png)

1. Klik op **[!UICONTROL Save & Close]**.

   De auteur-instantie [!DNL Experience Manager Assets] is nu geïntegreerd met [!DNL Adobe Stock] . U kunt meerdere [!DNL Adobe Stock] -configuraties maken (bijvoorbeeld configuraties op basis van landinstellingen). U kunt de elementen van [!DNL Adobe Stock] nu openen, zoeken en licentiëren vanuit de gebruikersinterface van [!DNL Experience Manager] .

   ![ onderzoek-voorraad-activa ](assets/aem-stock-searchstocks.png)

   >[!NOTE]
   >
   >In deze fase van integratie hebben alleen beheerders toegang tot de [!DNL Adobe Stock] -elementen, kunnen ze de Stock-elementen doorzoeken (met behulp van het besturingssysteem) en een licentie voor de [!DNL Adobe Stock] -elementen verkrijgen.
   >
   >Beheerders kunnen gebruikers of groepen verder toevoegen aan de [!DNL Adobe Stock] cloud-service en deze gebruikers die geen beheerder zijn in [!DNL Experience Manager] machtigingen geven om toegang te krijgen tot de Stock-configuratie.

1. Als u gebruikers of groepen wilt toevoegen, selecteert u de [!DNL Adobe Stock] wolkenconfiguratie en klikt u op **[!UICONTROL Properties]** .

1. Zoek om de gebruikers of de groepen toe te voegen aan wie u toestemmingen hebt toegewezen om tot de configuratie van Adobe Stock toegang te hebben. Zie [ toestemmingen aan gebruikersgroep ](#assign-permissions-to-group) toewijzen.


## Machtigingen toewijzen aan gebruikersgroep {#assign-permissions-to-group}

Beheerders kunnen gebruikersgroepen maken en bepaalde gebruikers of groepen machtigingen geven om toegang te krijgen tot de cloudservice van [!DNL Adobe Stock] .

Hieronder vindt u de machtigingen die een gebruiker nodig heeft om Adobe Stock-middelen te zoeken en te licentiëren:

* Het pad configureren: `/conf/global/settings/stock`
* Rechten: `jcr:read`
* Machtigingstype: `Allow`

U kunt een gebruikersgroep maken of machtigingen toewijzen aan een bestaande gebruikersgroep. Machtigingen kunnen worden toegewezen via de [!DNL Experience Manager Assets] -interface of vanuit de [!DNL User Admin] -console.

**om toegang tot een gebruikersgroep van [!DNL Experience Manager] te verlenen:**

1. Navigeer in de gebruikersinterface van [!DNL Experience Manager] naar **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Groups]** . Maak een gebruikersgroep voor [!DNL Adobe Stock] .

1. Navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Permissions]** .

1. Zoek naar de gebruikersgroep in het linkerpaneel en voeg nieuw **[!UICONTROL Access Control Entry (ACE)]** voor Adobe Stock toe.

   * Het pad configureren: `/conf/global/settings/stock`
   * Rechten: `jcr:read`
   * Machtigingstype: `Allow`

   Klik op **[!UICONTROL Add]**.

   ![ gebruiker-toestemmingen ](assets/aem-stock-user-permissions.png)

1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Stock]**. Selecteer de cloudconfiguratie van [!DNL Adobe Stock] en klik op **[!UICONTROL Properties]** .

1. Voeg de gemaakte gebruikersgroep toe aan de [!DNL Adobe Stock] -configuratie. Klik op **[!UICONTROL Save & Close]**.

   ![ wijs-gebruiker ](assets/aem-stock-adduser.png) toe

**om toegang tot een gebruiker van [!DNL User Admin Console] te verlenen:**

1. Open de Admin Console Gebruiker van [!DNL Experience Manager] . De standaard-URL is `http://localhost:4502/userdamin` .

1. Zoek in het linkerdeelvenster naar de gebruiker door de waarde `user_id` of `name` in te voeren. Dubbelklik om de gebruikerseigenschappen te openen.

1. Navigeer naar het tabblad **[!UICONTROL Permissions]** en sta `read` machtigingen toe voor de [!DNL Adobe Stock] cloudconfiguratie: `/conf/global/settings/stock` .

   >[!CAUTION]
   >
   >Als de cloudconfiguratie niet is toegestaan, heeft de gebruiker alleen toegang tot **[!UICONTROL Assets]** in de [!DNL Experience Manager] -interface.
   >
   >Als u toegang wilt tot [!UICONTROL Assets] - en [!DNL Adobe Stock] -elementen, moet u ervoor zorgen dat de cloudconfiguratie is toegestaan voor de gebruiker.

1. Klik op **[!UICONTROL Save]** om de machtigingen bij te werken.

   ![ toewijzen-gebruiker-in-gebruiker-admin ](assets/aem-stock-user-admin-console.png)

1. Voeg de gebruiker of de groep toe aan de cloudconfiguratie van [!DNL Adobe Stock] .


## Adobe Stock-middelen openen {#access-stock-assets}

Een gebruiker die geen beheerder is en machtigingen heeft voor de cloudconfiguratie van [!DNL Adobe Stock] , kan de elementen van [!DNL Adobe Stock] zoeken en een licentie verlenen via de interface van [!DNL Experience Manager] .

De gebruiker moet een extra stap uitvoeren om de cloudconfiguratie van [!DNL Adobe Stock] te activeren voordat hij toegang krijgt tot [!DNL Adobe Stock] -elementen. Het is een eenmalige activiteit. Als aan de gebruiker machtigingen worden toegewezen voor meerdere [!DNL Adobe Stock] cloudconfiguraties, kan de gebruiker de gewenste configuratie selecteren in de **[!UICONTROL User Preferences]** .

De cloudconfiguratie van [!DNL Adobe Stock] activeren:

1. Meld u aan bij [!DNL Experience Manager] .

1. Klik op het gebruikerspictogram in de rechterbovenhoek en klik vervolgens op **[!UICONTROL My Preferences]** . Het venster **[!UICONTROL User Preferences]** wordt geopend.

1. Selecteer de gewenste **[!UICONTROL Stock Configuration]** in de vervolgkeuzelijst en klik op **[!UICONTROL Accept]** om de configuratie te activeren.

   ![ gebruiker-voorkeur ](assets/aem-stock-preferences.png)

1. Navigeer naar **[!UICONTROL Assets]** > **[!UICONTROL Adobe Stock]** . U kunt nu [!DNL Adobe Stock] -elementen weergeven, zoeken en licentiëren.

In de volgende tabel wordt uitgelegd hoe de gebruikersmachtigingen werken wanneer u de elementen van [!DNL Adobe Stock] opent:

| Gebruiker | Groep | Machtigingen | Stock-configuratie accepteren in de gebruikersvoorkeuren | Toegang tot Assets | Toegang tot Adobe Stock |
| --- | --- | --- | --- | --- | --- |
| admin | NVT | Alles | NVT | Ja | Ja |
| test-doc1 | DAM-gebruiker | /conf/global/settings/stock/cloud-config | Ja | Ja | Ja |
| test-doc1 | DAM-gebruiker | /conf/global/settings/stock/cloud-config | Nee | Fout: kan gegevens niet laden | Nee |
| test-doc1 | DAM-gebruiker | **staat** toe: /conf/global/settings/stock **ontkent**: /cloud-config | De voorraadconfiguratie is niet zichtbaar | Ja | Nee |

## [!DNL Adobe Stock] -elementen gebruiken en beheren in [!DNL Experience Manager] {#usemanage}

Met behulp van deze mogelijkheid kunnen organisaties hun gebruikers toestaan te werken met [!DNL Adobe Stock] -elementen in [!DNL Experience Manager Assets] . Vanuit de gebruikersinterface van [!DNL Experience Manager] kunnen gebruikers zoeken in [!DNL Adobe Stock] -elementen en een licentie voor de vereiste elementen aanschaffen.

Zodra een [!DNL Adobe Stock] -element in [!DNL Experience Manager] in licentie is gegeven, kan het worden gebruikt en beheerd als een typisch element. In [!DNL Experience Manager] kunnen gebruikers de elementen zoeken en voorvertonen, de elementen kopiëren en publiceren, de elementen delen op [!DNL Brand Portal] , de elementen openen en gebruiken via de bureaubladtoepassing van [!DNL Experience Manager] , enzovoort.

![ Onderzoek naar [!DNL Adobe Stock] activa en filterresultaten van uw [!DNL Adobe Experience Manager] werkruimte ](assets/adobe-stock-search-results-workspace.png)

**A.** de activa van het onderzoek gelijkend op de activa waarvan [!DNL Adobe Stock] identiteitskaart wordt verstrekt. **B.** Zoek naar assets die overeenkomen met de vorm of afdrukstand die u hebt geselecteerd. **C.** Onderzoek naar één van meer gesteunde activa types **D.** Open of vouwt de filterruit **E.** Vergunning en sparen het geselecteerde activa in [!DNL Experience Manager] **F.** sparen de activa in [!DNL Experience Manager] met watermerk **G.** Onderzoek activa op [!DNL Adobe Stock] website die aan geselecteerde activa **gelijkaardig zijn H.** Bekijk de geselecteerde activa op [!DNL Adobe Stock] website **I.** Aantal geselecteerde activa van de onderzoeksresultaten **J.** Schakelaar tussen de mening van de Kaart en de mening van de Lijst

### Elementen zoeken {#find-assets}

Uw [!DNL Experience Manager] -gebruikers kunnen zoeken naar elementen in zowel [!DNL Experience Manager] als [!DNL Adobe Stock] . Wanneer de zoeklocatie niet beperkt is tot [!DNL Adobe Stock] , worden de zoekresultaten van [!DNL Experience Manager] en [!DNL Adobe Stock] weergegeven.

* Als u naar [!DNL Adobe Stock] elementen wilt zoeken, klikt u op **[!UICONTROL Navigation]** > **[!UICONTROL Assets]** > **[!UICONTROL Search Adobe Stock]** .

* Om naar activa over [!DNL Adobe Stock] en [!DNL Experience Manager Assets] te zoeken, klik onderzoek ![ ](assets/do-not-localize/search_icon.png).

U kunt ook `Location: Adobe Stock` in de zoekbalk typen om [!DNL Adobe Stock] -elementen te selecteren. [!DNL Experience Manager] biedt geavanceerde filtermogelijkheden voor de gezochte middelen, die gebruikers toestaan om snel nul-binnen op de vereiste activa gebruikend filters toe te staan, zoals types van gesteunde activa, beeldrichtlijn, en vergunning gegeven staat.

>[!NOTE]
>
>Assets die wordt gezocht vanuit [!DNL Adobe Stock] , wordt weergegeven in [!DNL Experience Manager] . [!DNL Adobe Stock] de activa worden opgehaald en in [!DNL Experience Manager] bewaart bewaart slechts na een gebruiker of [ activa ](/help/assets/aem-assets-adobe-stock.md#saveassets) of [ vergunningen opslaat en activa ](/help/assets/aem-assets-adobe-stock.md#licenseassets) opslaat. Assets die al in [!DNL Experience Manager] zijn opgeslagen, worden weergegeven en gemarkeerd voor eenvoudige referentie en toegang. Bovendien worden de elementen van [!DNL Stock] opgeslagen met extra metagegevens om de bron aan te geven als [!DNL Stock] .

![ filters van het Onderzoek in [!DNL Experience Manager] en benadrukte [!DNL Adobe Stock] activa in onderzoeksresultaten ](assets/aem-search-filters2.jpg)

### De vereiste elementen opslaan en weergeven {#saveassets}

Selecteer een element dat u wilt opslaan in [!DNL Experience Manager] . Klik op [!UICONTROL Save] in de werkbalk boven in het scherm en geef de naam en locatie van het element op. De elementen zonder licentie worden lokaal met een watermerk opgeslagen.

De volgende keer dat u naar elementen zoekt, worden de opgeslagen elementen gemarkeerd met een badge om aan te geven dat dergelijke elementen beschikbaar zijn in [!DNL Experience Manager Assets] .

>[!NOTE]
>
>De onlangs toegevoegde elementen geven een nieuwe badge weer in plaats van een badge met licentie.

### Licentie-elementen {#licenseassets}

Gebruikers kunnen een licentie voor [!DNL Adobe Stock] -middelen aanschaffen via het quotum van hun [!DNL Adobe Stock] -ondernemingsplan. Wanneer u een licentie voor een element aanschaft, wordt het zonder watermerk opgeslagen en is het beschikbaar voor zoeken en gebruiken in [!DNL Experience Manager Assets] .

![ Dialoogvenster voor het in licentie geven en opslaan van [!DNL Adobe Stock] -elementen in [!DNL Experience Manager Assets]](assets/aem-stock_licenseandsave.jpg)


### Metagegevens en elementen openen {#access-metadata-and-asset-properties}

Gebruikers kunnen de metagegevens openen en voorvertonen, inclusief de metagegevenseigenschappen [!DNL Adobe Stock] voor de elementen die zijn opgeslagen in [!DNL Experience Manager] , en **[!UICONTROL License References]** toevoegen voor een element. De updates voor de licentieverwijzing worden echter niet gesynchroniseerd tussen de [!DNL Experience Manager] - en [!DNL Adobe Stock] -website.

Gebruikers kunnen de eigenschappen van zowel gelicentieerde als niet-gelicentieerde activa zien.

![ Mening en toegang meta-gegevens en vergunningsverwijzingen van bewaarde activa ](assets/metadata_properties.jpg)


## Bekende beperkingen {#known-limitations}

* **Functionaliteit om gebruikers van vergunning te beperken werkt niet behoorlijk**: Alle gebruikers die `read` toestemmingen aan de voorraadconfiguratie hebben worden toegestaan om de [!DNL Adobe Stock] activa te zoeken en vergunning te geven.

* **niet-admin gebruikers moeten manueel de [!DNL Adobe Stock] wolkenconfiguratie** activeren: in het **[!UICONTROL User Preferences]** venster, toont **[!UICONTROL Stock Configuration]** de [!DNL Adobe Stock] wolkenconfiguratie zoals toegelaten maar het werkt niet voor een niet-admin gebruiker. De gebruiker moet op de knop **[!UICONTROL Accept]** klikken om de voorraadconfiguratie te activeren. Als deze stap ontbreekt, geeft het systeem een foutbericht weer over de toegang tot **[!UICONTROL Assets]** .

* **de redactionele beeldwaarschuwing wordt niet getoond**: Wanneer het verlenen van een vergunning van een beeld, kunnen de gebruikers niet controleren of een beeld Uitgeeflente slechts van het Gebruik is. Om mogelijk misbruik te voorkomen, kunnen de beheerders de toegang tot redactionele activa van de Admin Console uitzetten.

* **Verkeerd licentietype wordt getoond**: Het is mogelijk dat een onjuist licentietype in [!DNL Experience Manager] voor een element wordt getoond. Gebruikers kunnen zich aanmelden bij de [!DNL Adobe Stock] -website om het type licentie te zien.

* **de gebieden en de meta-gegevens van de Verwijzing worden niet gesynchroniseerd**: Wanneer een gebruiker een gebied van de vergunningsverwijzing bijwerkt, wordt de informatie van de vergunningsverwijzing bijgewerkt in [!DNL Experience Manager] maar niet op de [!DNL Adobe Stock] website. Als de gebruiker de referentievelden op de [!DNL Adobe Stock] -website bijwerkt, worden de updates niet gesynchroniseerd in [!DNL Experience Manager] .

<!--
## Use and manage [!DNL Adobe Stock] assets in [!DNL Experience Manager] {#usemanage}

Using this capability, organizations users can work using [!DNL Adobe Stock] assets in [!DNL Experience Manager Assets]. From within the [!DNL Experience Manager] user interface, users can search [!DNL Adobe Stock] assets and license the required assets.

Once an [!DNL Adobe Stock] asset is licensed in [!DNL Experience Manager], it can be used and managed like a typical asset. In [!DNL Experience Manager], the users can search and preview the assets; copy and publish the assets; share the assets on [!DNL Brand Portal]; access and use the assets via [!DNL Experience Manager] desktop app; and so on.
-->

<!--  ![Search for Adobe Stock assets and filter results from your Adobe Experience Manager workspace](assets/adobe-stock-search-results-workspace.png)

*Figure: Search for [!DNL Adobe Stock] assets and filter results from your [!DNL Experience Manager] interface.*

**A.** Search assets similar to the assets whose [!DNL Adobe Stock] ID is provided. **B.** Search assets that match your selection of shape or orientation. **C.** Search for one of more supported asset types **D.** Open or collapse the filters pane **E.** License and save the selected asset in [!DNL Experience Manager] **F.** Save the asset in [!DNL Experience Manager] with watermark **G.** Explore assets on [!DNL Adobe Stock] website that are similar to the selected asset **H.** View the selected assets on [!DNL Adobe Stock] website **I.** Number of selected assets from the search results **J.** Switch between Card view and List view -->

<!--
### Find assets {#find-assets}

Your [!DNL Experience Manager] users, can search for assets in both, [!DNL Experience Manager] and [!DNL Adobe Stock]. When the search location is not limited to [!DNL Adobe Stock], the search results from [!DNL Experience Manager] and [!DNL Adobe Stock] are displayed.

* To search for [!DNL Adobe Stock] assets, click **[!UICONTROL Navigation]** > **[!UICONTROL Assets]** > **[!UICONTROL Search Adobe Stock]**.

* To search for assets across [!DNL Adobe Stock] and [!DNL Experience Manager Assets], click search ![search](assets/do-not-localize/search_icon.png).

Alternatively, start typing `Location: Adobe Stock` in the search bar to select [!DNL Adobe Stock] assets. [!DNL Experience Manager] offers advanced filtering capabilities on the searched assets, allowing users to quickly zero-in on the required assets using filters, such as types of supported assets, image orientation, and licensed state.

>[!NOTE]
>
>Assets searched from [!DNL Adobe Stock] are just displayed in [!DNL Experience Manager]. [!DNL Adobe Stock] assets are fetched and stored in [!DNL Experience Manager] repository only after a user either [saves an asset](/help/assets/aem-assets-adobe-stock.md#saveassets) or [licenses and saves an asset](/help/assets/aem-assets-adobe-stock.md#licenseassets). Assets that are already stored in [!DNL Experience Manager] are displayed and highlighted for ease of reference and access. Also, the [!DNL Stock] assets are saved with some additional metadata to indicate the source as [!DNL Stock].

![Search filters in Experience Manager and highlighted Adobe Stock assets in search results](assets/aem-search-filters2.jpg)

*Figure: Search filters in [!DNL Experience Manager] and highlighted [!DNL Adobe Stock] assets in search results.*

### Save and view the required assets {#saveassets}

Select an asset that you want to save in [!DNL Experience Manager]. Click [!UICONTROL Save] in the toolbar at the top and provide the name and location of the asset. The unlicensed assets are saved locally with a watermark.

Next time when you search for assets, the saved assets are highlighted with a badge, to indicate that such assets are available in [!DNL Experience Manager Assets].

>[!NOTE]
>
>The recently added assets display a New badge instead of Licensed badge.

### License assets {#licenseassets}

Users can license [!DNL Adobe Stock] assets by using the quota of their [!DNL Adobe Stock] enterprise plan. When you license an asset, it is saved without a watermark and is available for searching and using in [!DNL Experience Manager Assets].

![Dialog to license and save Adobe Stock assets in Experience Manager Assets](assets/aem-stock_licenseandsave.jpg)

*Figure: Dialog to license and save [!DNL Adobe Stock] assets in [!DNL Experience Manager Assets].*

### Access metadata and asset properties {#access-metadata-and-asset-properties}

Users can access and preview the metadata, including the [!DNL Adobe Stock] metadata properties for the assets saved in [!DNL Experience Manager], and add **[!UICONTROL License References]** for an asset. However, the updates to license reference are not synced between [!DNL Experience Manager] and [!DNL Adobe Stock] website.

Users can see the properties for both, licensed and unlicensed assets.

![View and access metadata and license references of saved assets](assets/metadata_properties.jpg)

*Figure: View and access metadata and license references of saved assets.*

## Known limitations {#known-limitations}

* **Editorial image warning is not displayed**: When licensing an image, users cannot check if an image is Editorial Use Only. To prevent possible misuse, the administrators can turn off the access to editorial assets from the Admin Console.

* **Wrong license type is displayed**: It is possible that an incorrect license type is displayed in [!DNL Experience Manager] for an asset. Users can log into the [!DNL Adobe Stock] website to see the license type.

* **Reference fields and metadata are not synced**: When a user updates a license reference field, the license reference information is updated in [!DNL Experience Manager] but not on the [!DNL Adobe Stock] website. Similarly, if the user updates the reference fields on the [!DNL Adobe Stock] website, the updates are not synchronized in [!DNL Experience Manager].
-->

**zie ook**

* [Assets vertalen](translate-assets.md)
* [ASSETS HTTP API](mac-api-assets.md)
* [Door Assets ondersteunde bestandsindelingen](file-format-support.md)
* [Zoeken in middelen](search-assets.md)
* [Verbonden elementen](use-assets-across-connected-assets-instances.md)
* [Elementen rapporteren](asset-reports.md)
* [Metagegevensschema&#39;s](metadata-schemas.md)
* [Elementen downloaden](download-assets-from-aem.md)
* [Metagegevens beheren](manage-metadata.md)
* [Zoeken in facetten](search-facets.md)
* [Verzamelingen beheren](manage-collections.md)
* [Bulkmetagegevens importeren](metadata-import-export.md)
* [Publish Assets naar AEM en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

>[!MORELIKETHIS]
>
>* [ Videozelfstudie bij het gebruiken van de activa van Adobe Stock met Experience Manager Assets ](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/creative-workflows/adobe-stock.html)
>* [ de hulp van het ondernemingsplan van Adobe Stock ](https://helpx.adobe.com/enterprise/using/adobe-stock-enterprise.html)
>* [ Veelgestelde vragen van Adobe Stock ](https://helpx.adobe.com/stock/faq.html)
