---
title: Adobe Stock Digital Assets gebruiken in AEM Assets
description: Adobe Stock-middelen zoeken, ophalen, licentiëren en beheren in Experience Manager. Behandel de gelicentieerde elementen als elk ander Experience Manager-element.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 41684858f1fe516046b9601c1d869fff180320e0
workflow-type: tm+mt
source-wordcount: '1088'
ht-degree: 18%

---


# Use Adobe Stock assets in AEM Assets {#use-adobe-stock-assets-in-aem-assets}

Organisaties kunnen hun Adobe Stock Enterprise Plan integreren met AEM Assets om ervoor te zorgen dat gelicentieerde middelen breed beschikbaar zijn voor hun creatieve en marketingprojecten, met de krachtige mogelijkheden voor middelenbeheer van AEM.

De voorraadservice van Adobe biedt ontwerpers en bedrijven toegang tot miljoenen kwalitatief hoogstaande, gekrulde, royaltyvrije foto&#39;s, vectoren, illustraties, video&#39;s, sjablonen en 3D-middelen voor al hun creatieve projecten. AEM-gebruikers kunnen snel Adobe Stock-middelen vinden, voorvertonen en in licentie geven die in AEM zijn opgeslagen, zonder de AEM-werkruimte te verlaten.

## AEM en Adobe Stock integreren {#integrate-aem-and-adobe-stock}

Als u communicatie tussen AEM en Adobe Stock wilt toestaan, maakt u een IMS-configuratie en een Adobe Stock-configuratie in AEM.

>[!NOTE]
>
>Alleen AEM-beheerders en beheerders van beheerconsole voor een organisatie kunnen de integratie uitvoeren omdat hiervoor beheerdersrechten vereist zijn.

### Create an IMS configuration {#create-an-ims-configuration}

1. Klik op het AEM-logo. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**. Klik op **[!UICONTROL Create]** en selecteer **[!UICONTROL Cloud Solution]** > **[!UICONTROL Adobe Stock]**.
1. U kunt een bestaand certificaat opnieuw gebruiken of selecteren **[!UICONTROL Create new certificate]**.
1. Klik op **[!UICONTROL Create certificate]**. Download de openbare sleutel wanneer deze is gemaakt. Klik op **[!UICONTROL Next]**.
1. Geef de juiste waarden op in de velden met de namen **[!UICONTROL Title]**, **[!UICONTROL Authorization Server]**, **[!UICONTROL API Key]**, **[!UICONTROL Client Secret]** en **[!UICONTROL Payload]**. See [JWT authentication quick start](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/JWT/JWT.md), for detailed information to fetch these values from Adobe Developer Console.
1. Voeg de gedownloade openbare sleutel toe aan uw Adobe Developer Console-serviceaccount.

### Adobe Stock-configuratie maken in AEM {#create-adobe-stock-configuration-in-aem}

1. Ga in de AEM-gebruikersinterface naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Stock]**.
1. Klik **[!UICONTROL Create]** om een configuratie tot stand te brengen en het te associëren met uw bestaande Configuratie IMS. Selecteren `PROD` als omgevingsparameter.
1. Laat in **[!UICONTROL Licensed Assets Path]** het veld de locatie ongewijzigd. Wijzig de locatie waar u de Adobe Stock-elementen wilt opslaan niet.
1. Voltooi het maken door alle vereiste eigenschappen toe te voegen. Klik op **[!UICONTROL Save & Close]**.
1. Voeg AEM-gebruikers of -groepen toe die een licentie voor de elementen kunnen verkrijgen.

>[!NOTE]
>
>Als er meerdere Adobe Stock Configurations zijn, selecteert u de gewenste configuratie in [!UICONTROL User Preferences] het deelvenster door op het AEM-logo in de AEM-gebruikersinterface te klikken.

## Adobe Stock Assets in AEM gebruiken en beheren {#usemanage}

Met deze mogelijkheid kunnen organisaties hun gebruikers toestaan te werken met Adobe Stock-middelen in AEM Assets. Vanuit de AEM-gebruikersinterface kunnen gebruikers zoeken in Adobe Stock-middelen en een licentie voor de vereiste middelen aanschaffen.

Zodra een Adobe Stock-middel in AEM in licentie is gegeven, kan het worden gebruikt en beheerd als een typisch middel. In AEM kunnen de gebruikers de elementen zoeken en voorvertonen; de elementen kopiëren en publiceren; delen van de activa op Brand Portal; toegang tot en gebruik de middelen via de AEM-bureaubladtoepassing; enzovoort.

<!--  ![Search for Adobe Stock assets and filter results from your AEM workspace](assets/adobe-stock-search-results-workspace.png)
*Figure: Search for Adobe Stock assets and filter results from your AEM workspace* -->

**A.** Zoek naar assets die vergelijkbaar zijn met de assets waarvan de Adobe Stock-id is opgegeven. **B.** Zoek naar assets die overeenkomen met de vorm of afdrukstand die u hebt geselecteerd. **C.** Zoek naar een of meer ondersteunde assettypen **D.** Open het deelvenster voor filters of vouw dit samen **E.** Verleen een licentie aan de geselecteerde asset in AEM en sla deze op **F.** Sla de asset op in AEM met een watermerk **G.** Verken assets op de Adobe Stock-website die vergelijkbaar zijn met de geselecteerde asset **H.** Bekijk de geselecteerde assets op de Adobe Stock-website **I.** Aantal geselecteerde assets in de zoekresultaten **J.** Schakel tussen kaart- en lijstweergave

### Elementen zoeken {#find-assets}

Uw AEM-gebruikers kunnen zoeken naar middelen in zowel AEM- als Adobe-bestanden. Als de zoeklocatie niet beperkt is tot Adobe Stock, worden de zoekresultaten van AEM en Adobe Stock weergegeven.

* Als u op Adobe Stock-elementen wilt zoeken, klikt u op **[!UICONTROL Navigation]** > **[!UICONTROL Assets]** > **[!UICONTROL Search Adobe Stock]**.

* Als u wilt zoeken naar elementen in Adobe Stock en AEM Assets, klikt u op het zoekpictogram ![search_icon](assets/do-not-localize/search_icon.png).

U kunt ook `Location: Adobe Stock` in de zoekbalk typen om Adobe Stock-elementen te selecteren.  AEM biedt geavanceerde filtermogelijkheden voor de gezochte middelen, die gebruikers toestaan om snel nul-binnen op de vereiste activa gebruikend filters toe te staan, zoals types van gesteunde activa, beeldrichtlijn, en vergunning gegeven staat.

>[!NOTE]
>
>Assets waarnaar wordt gezocht vanuit Adobe Stock, worden alleen weergegeven in AEM. Adobe Stock-assets worden alleen opgehaald en opgeslagen in de AEM-opslagplaats nadat een gebruiker [een asset heeft opgeslagen](/help/assets/aem-assets-adobe-stock.md#saveassets) of [een licentie voor een asset heeft verleend](/help/assets/aem-assets-adobe-stock.md#licenseassets). Assets die al in AEM zijn opgeslagen, worden weergegeven en gemarkeerd voor eenvoudige referentie en toegang. Dergelijke assets worden bovendien met extra metadata opgeslagen om de bron aan te geven als Adobe Stock.

![Zoekfilters in AEM en gemarkeerde Adobe Stock-elementen in zoekresultaten](assets/aem-search-filters2.jpg)*Afbeelding: Zoekfilters in AEM en gemarkeerde Adobe Stock-elementen in zoekresultaten*

### De vereiste elementen opslaan en weergeven {#saveassets}

Selecteer een middel dat u in AEM wilt bewaren. Klik op Opslaan in de werkbalk boven in het scherm en geef de naam en locatie van het element op. De elementen zonder licentie worden lokaal met een watermerk opgeslagen.

De volgende keer dat u naar elementen zoekt, worden de opgeslagen elementen gemarkeerd met een badge om aan te geven dat dergelijke elementen beschikbaar zijn in AEM Assets.

>[!NOTE]
>
>De onlangs toegevoegde elementen geven een nieuwe badge weer in plaats van een badge met licentie.

### Licentie-elementen {#licenseassets}

Gebruikers kunnen een licentie voor Adobe Stock-middelen aanschaffen via het quotum van hun Adobe Stock Enterprise-abonnement. Wanneer u een licentie voor een element aanschaft, wordt het zonder watermerk opgeslagen en is het beschikbaar voor zoeken en gebruiken in AEM-elementen.

![Dialoogvenster voor het in licentie geven en opslaan van Adobe Stock-elementen in AEM Assets](assets/aem-stock_licenseandsave.jpg)*Afbeelding: Dialoogvenster voor het in licentie geven en opslaan van Adobe Stock-middelen in AEM Assets*

### Metagegevens en elementen openen {#access-metadata-and-asset-properties}

Gebruikers kunnen de metagegevens openen en voorvertonen, inclusief de eigenschappen van de metagegevens van Adobe Stock voor de elementen die zijn opgeslagen in AEM, en deze toevoegen **[!UICONTROL License References]** voor een element. De updates voor de licentieverwijzing worden echter niet gesynchroniseerd tussen AEM en de Adobe Stock-website.

Gebruikers kunnen de eigenschappen van zowel gelicentieerde als niet-gelicentieerde activa zien.

![Metagegevens en licentieverwijzingen van opgeslagen elementen](assets/metadata_properties.jpg)*weergeven en openen Metagegevens en licentieverwijzingen van opgeslagen elementen weergeven en openen*

## Bekende beperkingen {#known-limitations}

### Waarschuwing voor redactionele afbeelding wordt niet weergegeven

Wanneer gebruikers een licentie voor een afbeelding verlenen, kunnen ze niet controleren of een afbeelding alleen voor gebruik als redactie is. Om mogelijk misbruik te voorkomen, kunnen de beheerders de toegang tot redactionele middelen van de Console van Admin uitzetten.

### Onjuist licentietype wordt weergegeven

Het is mogelijk dat een onjuist licentietype in AEM wordt weergegeven voor een element. Gebruikers kunnen zich aanmelden bij de Adobe Stock-website om het type licentie te zien.

### Referentievelden en metagegevens zijn niet gesynchroniseerd

Wanneer een gebruiker een veld met een licentieverwijzing bijwerkt, wordt de informatie over de licentieverwijzing bijgewerkt in AEM, maar niet op de Adobe Stock-website. Als de gebruiker de referentievelden op de Adobe Stock-website bijwerkt, worden de updates ook niet gesynchroniseerd in AEM.

## Gerelateerde bronnen {#related-resources}

[Videozelfstudie over het gebruik van Adobe Stock Assets met AEM Assets](https://helpx.adobe.com/experience-manager/kt/assets/using/stock-assets-feature-video-use.html)

[Help bij Adobe Stock Enterprise Plan](https://helpx.adobe.com/enterprise/using/adobe-stock-enterprise.html)

[Veelgestelde vragen over Adobe Stock](https://helpx.adobe.com/stock/faq.html)
