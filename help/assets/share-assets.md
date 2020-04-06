---
title: Elementen, mappen en verzamelingen delen als een koppeling
description: In dit artikel wordt beschreven hoe u elementen, mappen en verzamelingen als hyperlink deelt in de middelen van Experience Manager.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 82dd9bd69fe994f74c7be8a571e386f0e902f6a1

---


# Elementen delen en distribueren die worden beheerd in Experience Manager {#share-assets-from-aem}

Met Adobe Experience Manager (AEM) kunt u elementen, mappen en verzamelingen delen met leden van uw organisatie en externe entiteiten, waaronder partners en leveranciers. U kunt de volgende methoden gebruiken om elementen van Experience Manager-middelen te delen als cloudservice:

* Delen als koppeling
* Elementen downloaden
* Delen via AEM-bureaubladtoepassing
* Delen via Adobe Asset Link
* (Opkomende functionaliteit) Delen met behulp van Brand Portal

## Elementen delen als koppeling {#sharelink}

Gebruik het dialoogvenster Koppelen om de URL te genereren voor elementen die u met gebruikers wilt delen. Gebruikers met beheerdersrechten of met leesmachtigingen op de `/var/dam/share` locatie kunnen de koppelingen weergeven die met hen worden gedeeld. Het delen van elementen via een koppeling is een handige manier om bronnen beschikbaar te maken voor externe partijen zonder dat deze zich eerst hoeven aan te melden bij AEM Assets.

>[!NOTE]
>
>* U hebt ACL toestemming op de omslag of de activa nodig uitgeven die u als verbinding wilt delen.
>* Voordat u een koppeling met gebruikers deelt, moet u ervoor zorgen dat Day CQ Mail Service is geconfigureerd. Anders treedt een fout op.


1. Selecteer in de gebruikersinterface Elementen het element dat u wilt delen als een koppeling.
1. Klik/tik op de werkbalk op de koppeling **[!UICONTROL Delen]**.

   Er wordt automatisch een elementkoppeling gemaakt in het veld Koppeling **** delen. Kopieer deze koppeling en deel deze met de gebruikers. De standaardvervaltijd voor de verbinding is één dag.

   Alternatief, ga te werk om stappen 3-7 van deze procedure uit te voeren om e-mailontvangers toe te voegen, de vervaltijd voor de verbinding te vormen, en het van de dialoog te verzenden.

   >[!NOTE]
   >
   >Als een gedeeld element naar een andere locatie wordt verplaatst, werkt de koppeling niet meer. Maak de koppeling opnieuw en deel deze opnieuw met de gebruikers.

1. From the web console, open the **[!UICONTROL Day CQ Link Externalizer]** configuration and modify the following properties in the **[!UICONTROL Domains]** field with the values mentioned against each:

   * lokaal
   * author
   * publish
   Geef voor de lokale en auteur-eigenschappen de URL op voor respectievelijk de lokale instantie en de auteur. Zowel de lokale als de auteur-eigenschappen hebben dezelfde waarde als u één AEM-auteurinstantie uitvoert. Geef voor publiceren de URL voor de publicatie-instantie op.

1. In the email address box of the **[!UICONTROL Link Sharing]** dialog, type the email ID of the user you want to share the link with. U kunt de koppeling ook delen met meerdere gebruikers.

   Als de gebruiker lid is van uw organisatie, selecteert u de e-mailid van de gebruiker in de voorgestelde e-mailadressen die worden weergegeven in de lijst onder het invoergebied. Voor een externe gebruiker typt u de volledige e-mailid en selecteert u deze in de lijst.

   Als u wilt dat e-mailberichten naar gebruikers kunnen worden verzonden, configureert u de SMTP-servergegevens in [Day CQ Mail Service](/help/assets/configure-asset-sharing.md#configmailservice).

   >[!NOTE]
   >
   >Als u een e-mailadres invoert van een gebruiker die geen lid is van uw organisatie, wordt het woord &quot;Externe gebruiker&quot; voorafgegaan door de e-mailid van de gebruiker.

1. Voer in het vak **[!UICONTROL Onderwerp]** een onderwerp in voor het element dat u wilt delen.
1. Voer in het vak **[!UICONTROL Bericht]** een optioneel bericht in.
1. Geef in het veld **[!UICONTROL Verlopen]** een vervaldatum en -tijd voor de koppeling op met de datumkiezer. De vervaldatum wordt standaard ingesteld voor een week vanaf de datum waarop u de koppeling deelt.
1. Als u gebruikers de oorspronkelijke afbeelding samen met de uitvoeringen wilt laten downloaden, selecteert u **[!UICONTROL Downloaden van origineel bestand]** toestaan.

   >[!NOTE]
   >
   >Standaard kunnen gebruikers alleen de uitvoeringen downloaden van het element dat u als koppeling deelt.

1. Klik op **[!UICONTROL Delen]**. Een bericht bevestigt dat de koppeling via e-mail met de gebruikers wordt gedeeld.
1. Als u het gedeelde element wilt weergeven, klikt of tikt u op de koppeling in het e-mailbericht dat naar de gebruiker is verzonden. Het gedeelde element wordt weergegeven op de pagina **[!UICONTROL Adobe Marketing Cloud]** .

   Als u wilt schakelen naar de lijstweergave, klikt of tikt u op het layoutpictogram op de werkbalk.

1. Als u een voorvertoning van de asset wilt genereren, klikt of tikt u op de gedeelde asset. To close the preview and return to the **[!UICONTROL Marketing Cloud]** page, click/tap **[!UICONTROL Back]** in the toolbar. If you have shared a folder, click/tap **[!UICONTROL Parent Folder]** to return to the parent folder.

   >[!NOTE]
   >
   >AEM ondersteunt het genereren van een voorvertoning van elementen van deze MIME-typen: JPG, PNG, GIF, BMP, INDD, PDF en PPT. U kunt alleen de elementen van de andere MIME-typen downloaden.

1. Als u het gedeelde element wilt downloaden, klikt of tikt u op **[!UICONTROL Selecteren]** op de werkbalk, klikt/tikt u op het element en klikt/tikt u op **[!UICONTROL Downloaden]** op de werkbalk.
1. Als u de elementen die u als koppelingen hebt gedeeld, wilt weergeven, gaat u naar de interface Middelen en klikt of tikt u op het pictogram GlobalNav. Kies **[!UICONTROL Navigatie]** in de lijst om het navigatievenster weer te geven.
1. From the Navigation pane, choose **[!UICONTROL Shared Links]** to display a list of shared assets.
1. Als u een element niet meer wilt delen, selecteert u het en tikt u op Delen **[!UICONTROL opheffen]** of klikt u op de werkbalk.

Een bericht bevestigt dat u het element niet hebt gedeeld. Bovendien wordt de vermelding voor het element uit de lijst verwijderd.

## Elementen downloaden en delen {#download-and-share-assets}

Gebruikers kunnen bepaalde assets downloaden en deze delen buiten Experience Manager. Zie voor meer informatie [hoe u elementen](/help/assets/search-assets.md)kunt zoeken, [hoe u elementen](/help/assets/download-assets-from-aem.md)kunt downloaden en [hoe u verzamelingen kunt downloaden](manage-collections.md#download-a-collection)

## Elementen delen met creatieve professionals {#share-with-creatives}

Marketers en zakelijke gebruikers kunnen hun goedgekeurde bedrijfsmiddelen eenvoudig delen met hun creatieve professionals.

* **AEM-bureaubladtoepassing**: De app werkt op Windows en Mac. Zie Overzicht [van de](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/introduction.html)bureaubladtoepassing. Als u wilt weten hoe geautoriseerde desktopgebruikers gemakkelijk toegang hebben tot de gedeelde elementen, raadpleegt u de elementen [](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html#browse-search-preview-assets)Bladeren, Zoeken en Voorvertonen. De desktopgebruikers kunnen nieuwe elementen maken en deze delen met hun collega&#39;s die AEM-gebruikers zijn, bijvoorbeeld door nieuwe afbeeldingen te uploaden. Zie Elementen [uploaden met de bureaubladtoepassing](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html#upload-and-add-new-assets-to-aem).

* **Adobe-elementkoppeling**: De creatieve professionals kunnen rechtstreeks vanuit Adobe InDesign, Adobe Illustrator en Adobe Photoshop zoeken en middelen gebruiken.

### Beste werkwijzen en probleemoplossing {#bestpractices}

* Elementmappen of -verzamelingen die in hun naam een witruimte bevatten, worden mogelijk niet gedeeld.
* Als gebruikers de gedeelde elementen niet kunnen downloaden, vraagt u de AEM-beheerder na welke [downloadlimieten](/help/assets/configure-asset-sharing.md#maxdatasize) gelden.
* Als u geen e-mail met koppelingen naar gedeelde elementen kunt verzenden of als de andere gebruikers uw e-mail niet kunnen ontvangen, raadpleegt u uw AEM-beheerder als de [e-mailservice](/help/assets/configure-asset-sharing.md#configmailservice) is geconfigureerd of niet.
* Als u geen elementen kunt delen via de functie voor het delen van koppelingen, controleert u of u de juiste machtigingen hebt. Zie [Elementen](#sharelink)delen.

<!--
Add content or link about how to share using BP, DA, AAL, etc.
-->
