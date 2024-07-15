---
title: Elementen, mappen en verzamelingen distribueren en delen
description: Verdeel uw digitale activa gebruikend methodes zoals aandeel als verbinding, het downloaden, en via  [!DNL Brand Portal],  [!DNL desktop app], en  [!DNL Asset Link].
feature: Asset Management, Collaboration, Asset Distribution
role: Admin, User
exl-id: 14e897cc-75c2-42bd-8563-1f5dd23642a0
source-git-commit: ab2cf8007546f538ce54ff3e0b92bb0ef399c758
workflow-type: tm+mt
source-wordcount: '1771'
ht-degree: 0%

---

# Elementen delen en distribueren die worden beheerd in [!DNL Experience Manager] {#share-assets-from-aem}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/link-sharing.html?lang=en) |
| AEM as a Cloud Service | Dit artikel |

Met [!DNL Adobe Experience Manager Assets] kunt u elementen, mappen en verzamelingen delen met leden van uw organisatie en externe entiteiten, waaronder partners en leveranciers. Gebruik de volgende methoden om elementen van [!DNL Experience Manager Assets] te delen als een [!DNL Cloud Service] :

* [ Aandeel als verbinding ](#sharelink).
* [ de activa van de Download ](/help/assets/download-assets-from-aem.md) en delen afzonderlijk.
* Deel gebruikend [[!DNL Experience Manager]  Desktop app ](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html).
* Delen met [[!DNL Adobe Asset Link] ](https://www.adobe.com/creativecloud/business/enterprise/adobe-asset-link.html) .
* Delen met [[!DNL Brand Portal] ](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/brand-portal.html) .

## Vereisten {#prerequisites}

U hebt de voorrechten van de Beheerder nodig om [ montages voor het delen van activa als Verbinding ](#config-link-share-settings) te vormen.

## Instellingen voor gedeelde koppelingen configureren {#config-link-share-settings}

In [!DNL Experience Manager Assets] kunt u de standaardinstellingen voor het delen van koppelingen configureren.

1. Klik op het logo [!DNL Experience Manager] en navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Assets Configuration]** > **[!UICONTROL Link Share]** .
1. Begininstellingen:

   * **omvat Originelen:**

      * Selecteer `Select Include Originals` om standaard de optie `Include Originals` te selecteren in het dialoogvenster voor het delen van koppelingen.
      * Selecteer in het dialoogvenster Koppelen hoe de optie `Include Originals` wordt weergegeven. Met [!UICONTROL Editable] kan de gebruiker de instellingen wijzigen die hier in de Instellingen bij openen zijn gedefinieerd. Met `Read-only` wordt de instelling weergegeven, maar kan deze niet worden gewijzigd. `Hidden` verbergt de instelling en gebruikt de waarde die hier in de Begininstellingen is geconfigureerd.
   * **omvat Vertoningen:**
      * Selecteer `Select Include Renditions` optie om standaard de optie `Include Renditions` te selecteren in het dialoogvenster voor het delen van koppelingen.
      * Selecteer in het dialoogvenster Koppelen hoe de optie `Include Renditions` wordt weergegeven. Met [!UICONTROL Editable] kan de gebruiker de instellingen wijzigen die hier in de Instellingen bij openen zijn gedefinieerd. Met `Read-only` wordt de instelling weergegeven, maar kan deze niet worden gewijzigd. `Hidden` verbergt de instelling en gebruikt de waarde die hier in de Begininstellingen is geconfigureerd.

1. Geef de standaardgeldigheidsperiode voor de koppeling op in het veld `Validity Period` in de sectie `Expiration date` .

1. **[!UICONTROL Link share]** in de actiebalk:
   * Alle gebruikers met `jcr:modifyAccessControl` -machtigingen kunnen de optie [!UICONTROL Link share] weergeven. Het is standaard zichtbaar voor alle beheerders. De knop [!UICONTROL Link share] is standaard zichtbaar voor iedereen. U kunt configureren om deze optie alleen voor de gedefinieerde groepen weer te geven of u kunt deze optie ook van specifieke groepen weigeren. Selecteer `Allow only for groups` als u wilt dat bepaalde groepen de optie `Share Link` kunnen weergeven. Selecteer `Deny from groups` om de optie `Share Link` van specifieke groepen te weigeren. Nadat u een van deze opties hebt geselecteerd, geeft u de groepnamen op met het veld `Select Groups` om de groepnamen toe te voegen die u wilt toestaan of weigeren.

Voor de verwante montages van de Configuratie E-mail, bezoek [ Documentatie van de Dienst E-mail ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/networking/examples/email-service.html)

![ vorm E-maildienst ](/help/assets/assets/config-email-service.png)

## Elementen delen als koppeling {#sharelink}

Het delen van elementen via een koppeling is een handige manier om de bronnen beschikbaar te maken voor externe partijen, marketers en andere [!DNL Experience Manager] -gebruikers. Met deze functionaliteit kunnen anonieme gebruikers de elementen openen en downloaden die met hen worden gedeeld. Wanneer u elementen downloadt van een gedeelde koppeling, gebruikt [!DNL Experience Manager Assets] een asynchrone service waarmee u bestanden sneller en zonder onderbreking kunt downloaden. De te downloaden elementen worden op de achtergrond in ZIP-archieven van beheerbare bestandsgrootte in een wachtrij geplaatst. Voor grote downloads wordt de download gebundeld in meerdere bestanden van 100 GB per bestandsgrootte.

<!--
Users with administrator privileges or with read permissions at `/var/dam/share` location are able to view the links shared with them. 
-->

>[!NOTE]
>
>* U hebt ACL toestemming op de omslag of de activa nodig uitgeven die u als verbinding wilt delen.
>* [ laat uitgaande e-mails ](/help/implementing/developing/introduction/development-guidelines.md#sending-email) toe alvorens een verbinding met de gebruikers te delen.

Er zijn twee manieren om de elementen te delen met behulp van de functie voor het delen van koppelingen:

1. Produceer een gedeelde verbinding, [ exemplaar, en deel de activa verbinding ](#copy-and-share-assets-link) met andere gebruikers.
1. Produceer een gedeelde verbinding en [ deel de activa verbinding door e-mail ](#share-assets-link-through-email). U kunt de standaardwaarden wijzigen, zoals de vervaldatum en -tijd, en het downloaden van de oorspronkelijke elementen en de uitvoeringen toestaan. U kunt e-mail naar meerdere gebruikers verzenden door hun e-mailadres toe te voegen.

   ![ Verbinding die dialoog deelt ](assets/share-link.png)

In beide gevallen kunt u de standaardwaarden wijzigen, zoals de vervaldatum en -tijd, en het downloaden van de oorspronkelijke elementen en de uitvoeringen toestaan.

### De elementkoppeling kopiëren en delen{#copy-and-share-asset-link}

Elementen delen als een openbare URL:

1. Meld u aan bij [!DNL Experience Manager Assets] en ga naar **[!UICONTROL Files]** .
1. Selecteer de elementen of map met elementen. Klik **[!UICONTROL Share Link]** op de werkbalk.
1. Het dialoogvenster **[!UICONTROL Link Sharing]** wordt weergegeven met een koppeling naar automatisch gegenereerde elementen in het veld **[!UICONTROL Share Link]** .
1. Stel de vervaldatum van de gedeelde koppeling naar wens in.
1. Schakel onder **[!UICONTROL Link Settings]** `Include Originals` of `Include Renditions` in of uit om een van beide opties op te nemen of uit te sluiten. U moet ten minste de optie kiezen.
1. De namen van de geselecteerde Assets worden weergegeven in de rechterkolom van het dialoogvenster [!DNL Share Link] .
1. Kopieer de elementkoppeling en deel deze met de gebruikers.

### Koppeling met middelen delen via e-mailkennisgeving {#share-assets-link-through-email}

Elementen delen via e-mail:

1. Selecteer de elementen of map met elementen. Klik **[!UICONTROL Share Link]** op de werkbalk.
1. Het dialoogvenster **[!UICONTROL Link Sharing]** wordt weergegeven met een koppeling naar automatisch gegenereerde elementen in het veld **[!UICONTROL Share Link]** .

   * Typ in het vak E-mailadres het e-mailadres van de gebruiker met wie u de koppeling wilt delen. U kunt de koppeling delen met meerdere gebruikers. Als de gebruiker lid is van uw organisatie, selecteert u het e-mailadres in de suggesties in de vervolgkeuzelijst. Typ in het tekstveld E-mailadres het e-mailadres van de gebruiker met wie u de koppeling wilt delen en klik op [!UICONTROL Enter] . U kunt de koppeling delen met meerdere gebruikers.

   * Typ in het vak **[!UICONTROL Subject]** een onderwerp om het doel van de gedeelde elementen op te geven.
   * Typ desgewenst een bericht in het vak **[!UICONTROL Message]** .
   * Gebruik in het veld **[!UICONTROL Expiration]** de datumkiezer om een vervaldatum en -tijd voor de koppeling op te geven.
   * Schakel het selectievakje **[!UICONTROL Allow download of the original file]** in zodat de ontvangers de oorspronkelijke vertoning kunnen downloaden.

1. Klik op **[!UICONTROL Share]**. Een bericht bevestigt dat de koppeling wordt gedeeld met de gebruikers. De gebruikers ontvangen een e-mail met de gedeelde koppeling.

   ![ Verbinding die e-mail deelt ](assets/link-sharing-email-notification.png)

### E-mailsjabloon aanpassen {#customize-email-template}

Een goed ontworpen sjabloon biedt professionaliteit en bekwaamheid, waardoor uw boodschap en organisatie geloofwaardiger wordt. Met [!DNL Adobe Experience Manager] kunt u de e-mailsjabloon aanpassen. Deze wordt verzonden naar de ontvangers die het e-mailbericht met de gedeelde koppeling ontvangen. Bovendien kunnen aangepaste e-mailsjablonen uw e-mailinhoud aanpassen door uw ontvangers een naam te geven en te verwijzen naar specifieke gegevens die voor hen van belang zijn. Door deze persoonlijke aanraking voelt de ontvanger zich gewaardeerd en neemt de betrokkenheid toe. Bovendien zorgt een aangepaste sjabloon ervoor dat uw e-mails consistent zijn met uw merkidentiteit, waaronder logo&#39;s, kleuren en lettertypen. Consistentie versterkt de merkherkenning en het vertrouwen onder ontvangers.

#### Opmaak van een aangepaste e-mailsjabloon {#format-of-custom-email-template}

De e-mailsjabloon kan worden aangepast met platte tekst of met HTML. De standaard bewerkbare sjabloonkoppeling vindt u op `/libs/settings/dam/adhocassetshare/en.txt` . U kunt de sjabloon overschrijven door het bestand `/apps/settings/dam/adhocassetshare/en.txt` te maken. U kunt de e-mailsjabloon zo vaak als nodig is wijzigen.

| Plaatsaanduidingen | Beschrijving |
|---|-----|
| `${emailSubject}` | Onderwerp van een e-mail |
| `${emailInitiator}` | E-mailadres van de gebruiker die het e-mailbericht heeft gemaakt |
| `${emailMessage}` | E-mailadres |
| `${pagePath}` | URL van de gedeelde koppeling |
| `${linkExpiry}` | Vervaldatum van gedeelde koppeling |
<!--| `${host.prefix}` | Origin of the [!DNL Experience Manager] instance, for example `http://www.adobe.com"` |-->

#### Voorbeeld van een aangepaste e-mailsjabloon {#custom-email-template-example}

```
subject: ${emailSubject}

<!DOCTYPE html>
<html><body>
<p><strong>${emailInitiator}</strong> invited you to review assets.</p>
<p>${emailMessage}</p>
<p>The shared link will be available until ${linkExpiry}.
<p>
    <a href="${pagePath}" target="_blank"><strong>Open</strong></a>
</p>

</body></html>
```

<!--Sent from instance: ${host.prefix}-->

### Elementen downloaden via de elementkoppeling {#download-assets-using-asset-link}

Elke gebruiker die toegang heeft tot de koppeling voor gedeelde elementen, kan de elementen downloaden die in een ZIP-map zijn gebundeld. Het downloadproces is hetzelfde, ongeacht of een gebruiker de koppeling met gekopieerde middelen opent of de koppeling met middelen gebruikt die via e-mail wordt gedeeld.

* Klik op de elementkoppeling of plak de URL in uw browser. De interface [!UICONTROL Link Share] wordt geopend wanneer u naar de interface [!UICONTROL Card View] of [!UICONTROL List View] kunt schakelen.

* In [!UICONTROL Card View] kunt u de muisaanwijzer boven het gedeelde element of de map met gedeelde elementen plaatsen om de elementen te selecteren of in de wachtrij voor downloaden.

* Standaard wordt in de gebruikersinterface de optie **[!UICONTROL Download Inbox]** weergegeven. Het geeft de lijst weer van alle gedeelde elementen of mappen die samen met hun status in de wachtrij voor downloaden staan.

* Als u de middelen of map selecteert, verschijnt er een optie **[!UICONTROL Queue Download]** op het scherm. Klik op de optie **[!UICONTROL Queue Download]** om het downloadproces te starten.

  ![ download van de Rij ](assets/queue-download.png)

* Terwijl het downloadbestand is voorbereid, klikt u op de optie **[!UICONTROL Download Inbox]** om de status van uw download weer te geven. Voor grote downloads klikt u op de knop **[!UICONTROL Refresh]** om de status bij te werken.

  ![ Inbox van de Download ](assets/link-sharing-download-inbox.png)

* Wanneer de verwerking is voltooid, klikt u op de knop **[!UICONTROL Download]** om het ZIP-bestand te downloaden.

<!--
You can also copy the auto-generated link and share it with the users. The default expiration time for the link is one day.
-->

>[!NOTE]
>
>Als een gedeeld element naar een andere locatie wordt verplaatst, werkt de koppeling niet meer. Maak de koppeling opnieuw en deel deze opnieuw met de gebruikers.


<!--
## Share assets as a link {#sharelink}

To generate the URL for assets you want to share with users, use the Link Sharing dialog. Users with administrator privileges or with read permissions at `/var/dam/share` location are able to view the links shared with them. Sharing assets through a link is a convenient way of making resources available to external parties without them having to first log in to Experience Manager Assets.

>[!NOTE]
>
>* You need Edit ACL permission on the folder or the asset that you want to share as a link.
>* Before you share a link with users, ensure that Day CQ Mail Service is configured. Otherwise, an error occurs.

1. In the Assets user interface, select the asset to share as a link.
1. From the toolbar, click/tap the **[!UICONTROL Share Link]**.

   An asset link is auto-created in the **[!UICONTROL Share Link]** field. Copy this link and share it with the users. The default expiration time for the link is one day.

   Alternatively, proceed to perform steps 3-7 of this procedure to add email recipients, configure the expiration time for the link, and send it from the dialog.

   >[!NOTE]
   >
   >If a shared asset is moved to a different location, its link stops working. Re-create the link and re-share with the users.

1. From the web console, open the **[!UICONTROL Day CQ Link Externalizer]** configuration and modify the following properties in the **[!UICONTROL Domains]** field with the values mentioned against each:

    * local
    * author
    * publish

   For the local and author properties, provide the URL for the local and author instance respectively. Both local and author properties have the same value if you run a single Experience Manager author instance. For publish, provide the URL for the publish instance.

1. In the email address box of the **[!UICONTROL Link Sharing]** dialog, type the email ID of the user you want to share the link with. You can also share the link with multiple users.

   If the user is a member of your organization, select the user's email ID from the suggested email IDs that appear in the list below the typing area. For an external user, type the complete email ID and then select it from the list.

   To enable emails to be sent out to users, configure the SMTP server details in [Day CQ Mail Service](/help/assets/configure-asset-sharing.md#configmailservice).

   >[!NOTE]
   >
   >If you enter an email ID of a user that is not a member of your organization, the words "External User" are prefixed with the email ID of the user.

1. In the **[!UICONTROL Subject]** box, enter a subject for the asset you want to share.
1. In the **[!UICONTROL Message]** box, enter an optional message.
1. In the **[!UICONTROL Expiration]** field, specify an expiration date and time for the link using the date picker. By default, the expiration date is set for a week from the date you share the link.
1. To let users download the original image along with the renditions, select **[!UICONTROL Allow download of original file]**.

   >[!NOTE]
   >
   >By default, users can only download the renditions of the asset that you share as a link.

1. Click **[!UICONTROL Share]**. A message confirms that the link is shared with the users through an email.
1. To view the shared asset, click/tap the link in the email that is sent to the user. The shared asset is displayed in the **[!UICONTROL Adobe Marketing Cloud]** page.

   To toggle to the list view, click/tap the layout icon in the toolbar.

1. To generate a preview of the asset, click/tap the shared asset. To close the preview and return to the **[!UICONTROL Marketing Cloud]** page, click/tap **[!UICONTROL Back]** in the toolbar. If you have shared a folder, click/tap **[!UICONTROL Parent Folder]** to return to the parent folder.

   >[!NOTE]
   >
   >Experience Manager supports generating the preview of assets of these MIME types: JPG, PNG, GIF, BMP, INDD, PDF, and PPT. You can only download the assets of the other MIME types.

1. To download the shared asset, click/tap **[!UICONTROL Select]** from the toolbar, click/tap the asset, and then click/tap **[!UICONTROL Download]** from the toolbar.
1. To view the assets you shared as links, go to the Assets user interface and click/tap the GlobalNav icon. Choose **[!UICONTROL Navigation]** from the list to display the Navigation pane.
1. From the Navigation pane, choose **[!UICONTROL Shared Links]** to display a list of shared assets.
1. To un-share an asset, select it and tap/click **[!UICONTROL Unshare]** from the toolbar.

A message confirms that you unshared the asset. In addition, the entry for the asset is removed from the list.
-->

## Elementen downloaden en afzonderlijk delen {#download-and-share-assets}

Gebruikers kunnen de vereiste elementen downloaden en deze buiten [!DNL Experience Manager] delen. Voor meer informatie, zie [ hoe te activa ](/help/assets/search-assets.md) zoeken, [ hoe te activa ](/help/assets/download-assets-from-aem.md) downloaden, en [ hoe te om inzamelingen ](manage-collections.md#download-a-collection) te downloaden

## Elementen delen met creatieve professionals {#share-with-creatives}

Marketers en zakelijke gebruikers kunnen hun goedgekeurde bedrijfsmiddelen eenvoudig delen met hun creatieve professionals.

* **Desktop app van de Experience Manager**: App werkt op Vensters en Mac. Zie [ Desktop app overzicht ](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html). Om te weten hoe om het even welke geautoriseerde Desktopgebruiker tot de gedeelde activa kan gemakkelijk toegang hebben, zie [ doorbladeren, doorzoeken, en voorproefactiva ](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#browse-search-preview-assets). De desktopgebruikers kunnen elementen maken en deze delen met hun collega&#39;s die Experience Manager gebruikers zijn, bijvoorbeeld door nieuwe afbeeldingen te uploaden. Zie [ activa uploaden gebruikend Desktop app ](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#upload-and-add-new-assets-to-aem).

* **de Verbinding van Activa van de Adobe**: De creatieve beroeps kunnen activa van binnen [!DNL Adobe InDesign], [!DNL Adobe Illustrator], en [!DNL Adobe Photoshop] direct zoeken en gebruiken.

## Elementen delen configureren {#configure-sharing}

De verschillende opties om de activa te delen vereisen specifieke configuratie en hebben specifieke eerste vereisten.

### Delen van koppelingen voor elementen configureren {#asset-link-sharing}

<!-- TBD: Web Console is not there so how to configure Day CQ email service? Or is it not required now? -->

Als u de URL wilt genereren voor elementen die u met gebruikers wilt delen, gebruikt u het dialoogvenster Koppeling delen. Gebruikers met beheerdersrechten of met leesmachtigingen op de locatie `/var/dam/share` kunnen de koppelingen weergeven die met hen worden gedeeld. Het delen van elementen via een koppeling is een handige manier om bronnen beschikbaar te maken voor externe partijen zonder dat deze zich eerst hoeven aan te melden bij [!DNL Assets] .

>[!NOTE]
>
>Als u koppelingen van de instantie Auteur naar externe entiteiten wilt delen, dient u alleen de volgende URL&#39;s voor `GET` -aanvragen beschikbaar te maken. Blokkeer andere URL&#39;s om ervoor te zorgen dat de instantie Auteur beveiligd is.
>
>* `[aem_server]:[port]/linkshare.html`
>* `[aem_server]:[port]/linksharepreview.html`
>* `[aem_server]:[port]/linkexpired.html`

<!--
1. From the list of services, locate **[!UICONTROL Day CQ Mail Service]**.
1. Click the **[!UICONTROL Edit]** icon beside the service, and configure the following parameters for **Day CQ Mail Service** with the details mentioned against their names:

    * SMTP server host name: email server host name
    * SMTP server port: email server port
    * SMTP user: email server user name
    * SMTP password: email server password
-->

<!-- TBD: Commenting as Web Console is not available. Document the appropriate OSGi config method if available in CS.
### Configure maximum data size {#maxdatasize}

When you download assets from the link shared using the Link Sharing feature, Experience Manager compresses the asset hierarchy from the repository and then returns the asset in a ZIP file. However, in the absence of limits to the amount of data that can be compressed in a ZIP file, huge amounts of data is subjected to compression, which causes out of memory errors in JVM. To secure the system from a potential denial of service attack due to this situation, you can configure the maximum size of the downloaded files. If uncompressed size of the asset exceeds the configured value, asset download requests are rejected. The default value is 100 MB.

1. Click/Tap the Experience Manager logo and then go to **[!UICONTROL Tools]** &gt; **[!UICONTROL Operations]** &gt; **[!UICONTROL Web Console]**.
1. From the web console, locate the **[!UICONTROL Day CQ DAM Adhoc Asset Share Proxy Servlet]** configuration.
1. Open the configuration in edit mode, and modify the value of the **[!UICONTROL Max Content Size (uncompressed)]** parameter.
1. Save the changes.
-->

<!--
Add content or link about how to configure sharing via BP, DA, AAL, etc.
-->

### Desktopacties inschakelen voor gebruik met bureaubladtoepassing {#desktop-actions}

Vanuit de gebruikersinterface van [!DNL Assets] in een browser kunt u de middelenlocaties of uitchecken verkennen en het middel openen voor bewerking in uw desktoptoepassing. Deze opties worden genoemd Desktopacties en om het toe te laten, zie [ Desktopacties in  [!DNL Assets]  Webinterface ](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#desktopactions-v2) toelaten.

![ laat Desktopacties toe om als kortere weg te gebruiken wanneer het werken met Desktop app ](assets/enable_desktop_actions.png)

### Te gebruiken configuraties [!DNL Adobe Asset Link] {#configure-asset-link}

Adobe Asset Link stroomlijnt de samenwerking tussen ontwerpers en marketers bij het maken van inhoud. [!DNL Adobe Experience Manager Assets] wordt verbonden met [!DNL Creative Cloud] bureaubladapps [!DNL Adobe InDesign] , [!DNL Adobe Photoshop] en [!DNL Adobe Illustrator] . In het deelvenster [!DNL Adobe Asset Link] hebben creatieve toepassingen toegang tot inhoud die is opgeslagen in [!DNL Assets] en kunnen ze deze inhoud wijzigen zonder de meest bekende creatieve toepassingen te verlaten.

Zie [ hoe te om  [!DNL Assets]  te vormen om het met  [!DNL Adobe Asset Link] te gebruiken ](https://helpx.adobe.com/enterprise/using/configure-aem-assets-for-asset-link.html).

## Aanbevolen werkwijzen en problemen oplossen {#bestpractices}

* Elementmappen of -verzamelingen die in hun naam een witruimte bevatten, worden mogelijk niet gedeeld.
* Als gebruikers de gedeelde elementen niet kunnen downloaden, vraagt u de beheerder van de Experience Manager om de downloadlimieten. De standaardwaarde is 100 MB.
* Een gebruiker kan alleen een voorvertoning weergeven van een video die wordt gedeeld via het delen van koppelingen als er voor de video een statische video-uitvoering beschikbaar is op de locatie `/jcr:content/renditions` in het knooppunt van de video in de opslagplaats. De voorvertoning is niet afhankelijk van de beschikbaarheid van een [!DNL Dynamic Media] -uitvoering.
* Wanneer u een video-element downloadt via gedeelde koppelingen, worden de [!DNL Dynamic Media] -vertoningen niet opgenomen in het gedownloade archief.

<!--
* If you cannot send email with links to shared assets or if the other users cannot receive your email, check with your Experience Manager administrator if the [email service](/help/assets/configure-asset-sharing.md#configmailservice) is configured or not. 
* If you cannot share assets using link sharing functionality, ensure that you have the appropriate permissions. See [share assets](#sharelink).
-->

<!-- TBD: Add content or link about how to share using Brand Portal when it is available on [!DNL Cloud Service].
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

