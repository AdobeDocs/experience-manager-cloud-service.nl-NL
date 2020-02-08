---
title: Adobe Stock Digital Assets gebruiken in AEM Assets
description: Adobe Stock-middelen zoeken, ophalen, licentiëren en beheren in Experience Manager. Behandel de gelicentieerde elementen als elk ander Experience Manager-element.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# Adobe Stock Assets gebruiken in AEM Assets {#use-adobe-stock-assets-in-aem-assets}

Organisaties kunnen hun Adobe Stock Enterprise Plan integreren met AEM Assets om ervoor te zorgen dat gelicentieerde middelen breed beschikbaar zijn voor hun creatieve en marketingprojecten, met de krachtige mogelijkheden voor middelenbeheer van AEM.

De voorraadservice van Adobe biedt ontwerpers en bedrijven toegang tot miljoenen kwalitatief hoogstaande, gekrulde, royaltyvrije foto&#39;s, vectoren, illustraties, video&#39;s, sjablonen en 3D-middelen voor al hun creatieve projecten. AEM-gebruikers kunnen snel Adobe Stock-middelen vinden, voorvertonen en in licentie geven die in AEM zijn opgeslagen, zonder de AEM-werkruimte te verlaten.

## AEM en Adobe Stock integreren {#integrate-aem-and-adobe-stock}

Als u communicatie tussen AEM en Adobe Stock wilt toestaan, maakt u een IMS-configuratie en een Adobe Stock-configuratie in AEM.

>[!NOTE]
>
>Alleen AEM-beheerders en beheerders van beheerconsole voor een organisatie kunnen de integratie uitvoeren omdat hiervoor beheerdersrechten vereist zijn.

### Een IMS-configuratie maken {#create-an-ims-configuration}

1. Klik op het AEM-logo. Ga naar **[!UICONTROL Gereedschappen]** > **[!UICONTROL Beveiliging]** > **[!UICONTROL Adobe IMS Configurations]**. Klik op **[!UICONTROL Maken]** en selecteer **[!UICONTROL Cloudoplossing]** > **[!UICONTROL Adobe Stock]**.
1. Hergebruik een bestaand certificaat of selecteer **[!UICONTROL Nieuw certificaat]** maken.
1. Klik op **[!UICONTROL Certificaat]** maken. Download de openbare sleutel wanneer deze is gemaakt. Click **[!UICONTROL Next]**.
1. Geef de juiste waarden op in de velden **[!UICONTROL Titel]**, **[!UICONTROL Autorisatieserver]**, **[!UICONTROL API-sleutel]**, **[!UICONTROL Clientgeheim]** en **[!UICONTROL Payload]**. Zie [JWT-verificatie snel starten](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/JWT/JWT.md)voor meer informatie over het ophalen van deze waarden van Adobe I/O.
1. Voeg de gedownloade openbare sleutel toe aan uw Adobe I/O-serviceaccount.

### Adobe Stock-configuratie maken in AEM {#create-adobe-stock-configuration-in-aem}

1. Navigeer in de AEM-gebruikersinterface naar **[!UICONTROL Gereedschappen]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Stock]**.
1. Klik **[!UICONTROL creëren]** om een configuratie tot stand te brengen en het te associëren met uw bestaande Configuratie IMS. Selecteren `PROD` als omgevingsparameter.
1. Laat een locatie ongewijzigd in het veld Pad **[!UICONTROL met]** gelicentieerde elementen. Wijzig de locatie waar u de Adobe Stock-elementen wilt opslaan niet.
1. Voltooi het maken door alle vereiste eigenschappen toe te voegen. Klik op **[!UICONTROL Opslaan en sluiten]**.
1. Voeg AEM-gebruikers of -groepen toe die een licentie voor de elementen kunnen verkrijgen.

>[!NOTE]
>
>Als er meerdere Adobe Stock Configurations zijn, selecteert u de gewenste configuratie in het deelvenster [!UICONTROL Gebruikersvoorkeuren] door op het AEM-logo in de AEM-gebruikersinterface te klikken.

## Adobe Stock Assets in AEM gebruiken en beheren {#usemanage}

Met deze mogelijkheid kunnen organisaties hun gebruikers toestaan te werken met Adobe Stock-middelen in AEM Assets. Vanuit de AEM-gebruikersinterface kunnen gebruikers zoeken in Adobe Stock-middelen en een licentie voor de vereiste middelen aanschaffen.

Zodra een Adobe Stock-middel in AEM in licentie is gegeven, kan het worden gebruikt en beheerd als een typisch middel. In AEM kunnen de gebruikers de elementen zoeken en voorvertonen; de elementen kopiëren en publiceren; delen van de activa op Brand Portal; toegang tot en gebruik de middelen via de AEM-bureaubladtoepassing; enzovoort.

<!--  ![Search for Adobe Stock assets and filter results from your AEM workspace](assets/adobe-stock-search-results-workspace.png)
*Figure: Search for Adobe Stock assets and filter results from your AEM workspace* -->

**** A. Zoek middelen die vergelijkbaar zijn met de middelen waarvan de Adobe Stock ID is opgegeven. **** B. Zoeken in elementen die overeenkomen met de vorm- of oriëntatieoptie die u hebt geselecteerd. **************** C.**Zoek naar één van meer gesteunde activa types** D. Open of vouwt het venster Filters **E. Licentie toewijzen en het geselecteerde element opslaan in AEM** F. Sla het element in AEM op met watermerk **G. Verken elementen op de Adobe Stock-website die vergelijkbaar zijn met de geselecteerde asset** H. Bekijk de geselecteerde middelen op Adobe Stock-website **I. Aantal geselecteerde elementen uit de zoekresultaten** J. Schakelen tussen de kaartweergave en de lijstweergave

### Elementen zoeken {#find-assets}

Uw AEM-gebruikers kunnen zoeken naar middelen in zowel AEM- als Adobe-bestanden. Als de zoeklocatie niet beperkt is tot Adobe Stock, worden de zoekresultaten van AEM en Adobe Stock weergegeven.

* Als u Adobe Stock-elementen wilt zoeken, klikt u op **[!UICONTROL Navigatie]** > **[!UICONTROL Middelen]** > Adobe Stock **** zoeken.

* Als u wilt zoeken naar elementen in Adobe Stock en AEM Assets, klikt u op het zoekpictogram ![search_icon](assets/do-not-localize/search_icon.png).

U kunt ook `Location: Adobe Stock` in de zoekbalk typen om Adobe Stock-elementen te selecteren.  AEM biedt geavanceerde filtermogelijkheden voor de gezochte middelen, die gebruikers toestaan om snel nul-binnen op de vereiste activa gebruikend filters toe te staan, zoals types van gesteunde activa, beeldrichtlijn, en vergunning gegeven staat.

>[!NOTE]
>
>Elementen die worden doorzocht vanuit Adobe Stock worden alleen weergegeven in AEM. Adobe Stock Assets worden alleen opgehaald en opgeslagen in AEM-opslagruimte nadat een gebruiker een middel [](/help/assets/aem-assets-adobe-stock.md#saveassets) heeft opgeslagen of een [licentie heeft verleend voor een middel](/help/assets/aem-assets-adobe-stock.md#licenseassets). Elementen die al in AEM zijn opgeslagen, worden weergegeven en gemarkeerd voor eenvoudige referentie en toegang. Dergelijke elementen worden bovendien met extra metagegevens opgeslagen om de bron aan te geven als Adobe Stock.

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

Gebruikers kunnen de metagegevens openen en voorvertonen, inclusief de eigenschappen van de Adobe Stock-metagegevens voor de elementen die zijn opgeslagen in AEM, en **[!UICONTROL Licentieverwijzingen]** toevoegen voor een element. De updates voor de licentieverwijzing worden echter niet gesynchroniseerd tussen AEM en de Adobe Stock-website.

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
