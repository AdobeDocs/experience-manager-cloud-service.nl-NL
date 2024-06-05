---
title: Opmerkingen bij de release 2023.8.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de release 2023.8.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a0ffa6cf-64ae-468c-93f4-ac6805ef907e
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1691'
ht-degree: 0%

---

# Opmerkingen bij de release 2023.8.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de versie 2023.8.0 van [!DNL Experience Manager] as a Cloud Service.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als [!DNL Cloud Service] huidige release met functies (2023.8.0) is 31 augustus 2023. De volgende release met functies (2023.9.0) is gepland voor 28 september 2023.

## Video vrijgeven {#release-video}

Bekijk de video Overzicht van de release van augustus 2023 voor een overzicht van de functies die in de release van 2023.8.0 zijn toegevoegd:

>[!VIDEO](https://video.tv.adobe.com/v/3423535/?quality=12)

## [!DNL Experience Manager Sites] als [!DNL Cloud Service] {#sites}

### Nieuwe functies in [!DNL Experience Manager Sites] {#sites-features}

* De [Console voor inhoudsfragment](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/content-fragments/content-fragments-console.html) Gebruikers kunnen nu tags weergeven en zoeken op tags die als metagegevens zijn toegepast op Inhoudsfragmenten. Gebruikers hoeven voor deze mogelijkheid niet meer over te schakelen op de interface Elementen, waardoor contextomschakeling wordt beperkt en de efficiëntie wordt verbeterd.

  ![Tags toevoegen in Content Fragment Console](/help/assets/content-fragments-console-tags.png)
* De nieuwe Inhoudsfragmenteditor is nu beschikbaar op AEM as a Cloud Service. Het stelt inhoudsauteurs in staat productiever te zijn door hun ontwerptaken te stroomlijnen en de noodzaak om tussen verschillende apps te schakelen tijdens het bewerken van inhoud te verminderen.
  ![Nieuwe editor voor inhoudsfragmenten](/help/release-notes/assets/newCFEditor.png)

De nieuwe editor voor inhoudsfragmenten biedt de volgende voordelen die niet beschikbaar zijn in de oorspronkelijke editor:
* Automatisch opslaan om efficiënter te ontwerpen en te voorkomen dat bewerkingen per ongeluk verloren gaan.
* De hiërarchische weergave van een inhoudsfragment en de bijbehorende verwijzingen met de boomstructuur voor snelle navigatie binnen een diep gestructureerd fragment.
  ![Boomstructuur in de editor voor inhoudsfragmenten](/help/release-notes/assets/newCFEditor_StructureTree.png)

* In line uploaden van elementen als inhoudsverwijzingen zonder dat deze eerst naar Asset DAM hoeven te worden geüpload
* Ad-hocvoorvertoning van de gerenderde ervaring die door het inhoudsfragment wordt geleverd om auteurs te helpen de vormgeving van de inhoud op de frontend-app te visualiseren
* 1-klik het publiceren en unpublishing van het inhoudsfragment van de redacteur
* Taalkopieën weergeven en naar deze talen navigeren tijdens het bewerken van een inhoudsfragment
  ![Taalkopieën in de Inhoudsfragmenteditor](/help/release-notes/assets/newCFEditor_LanguageCopies.PNG)

* Versies weergeven om de tijdlijn van een inhoudsfragment bij te houden

  ![Versies in de Content Fragment Editor](/help/release-notes/assets/newCFEditor_Versionhistory.PNG)

* Bovenliggende verwijzingen weergeven om auteurs inzicht te geven in het effect van hun bewerkingen

  ![Bovenliggende verwijzingen in de Content Fragment Editor](/help/release-notes/assets/newCFEditor_Parentreferences.PNG)

## [!DNL Experience Manager Assets] als [!DNL Cloud Service] {#assets}

### Nieuwe functies in de weergave Elementen {#assets-view-features}

<!--

**Assign metadata form to a folder**

You can now assign metadata form to a specific folder within your Assets Essentials deployment. All assets in the folder, including assets in the sub-folders, then display properties defined in the assigned metadata form.

![assign metadata form to a folder](/help/release-notes/assets/assign-to-folder.png)

-->

* **Bulkimportelementen uit gegevensbronnen**: Beheerders hebben nu de [mogelijkheid om een groot aantal activa te importeren](/help/assets/bulk-import-assets-view.md) van een gegevensbron naar AEM Assets. De beheerders hoeven geen afzonderlijke elementen of mappen meer te uploaden naar AEM Assets. Tot de ondersteunde gegevensbronnen voor bulkimport behoren Azure, AWS, Google Cloud en Dropbox.

  ![Elementen voor bulkimport uit een gegevensbron](/help/release-notes/assets/bulk-import.png)

* **Gereedschappen voor het bewerken van afbeeldingen aangedreven door Adobe Express**: Eenvoudig en intuïtief [gereedschappen voor het bewerken van afbeeldingen, aangedreven door Adobe Express](/help/assets/edit-images-assets-view.md) direct beschikbaar in AEM Assets om het hergebruik van inhoud te verhogen en de snelheid van inhoud te versnellen.

  ![Afbeeldingen bewerken met Adobe Express](/help/release-notes/assets/edit-adobe-express.png)

* **Flexibiliteit bij het vastzetten van items voor Mijn werkruimte Snelle toegang**: Mogelijkheid om items voor u, voor uw hele organisatie of voor een lijst met groepen te selecteren en vast te zetten, zodat deze in het dialoogvenster [Sectie Snelle toegang van Mijn werkruimte](/help/assets/my-workspace-assets-view.md) op basis van uw selectie.

  ![Items vastzetten voor groepen](/help/release-notes/assets/pin-items-for-groups.png)

### Nieuwe functies in de beheerweergave {#admin-view-features}

**Verbeteringen voor zoeken**

* Beheerders kunnen nu [de batchgrootte van elementen configureren](/help/assets/search-assets.md#configure-asset-batch-size) die worden weergegeven wanneer u een zoekopdracht uitvoert. De resultaten van het activaonderzoek tonen in veelvouden van het gevormde aantal van de partijgrootte wanneer u verder neer scrolt om de resultaten te laden. U kunt kiezen uit de beschikbare batchformaten van 200, 500 en 1000 elementen. Als u een lagere batch-grootte instelt, resulteert dit in snellere zoekresponstijden.

  ![Groepsgrootteconfiguratie van middelen](/help/release-notes/assets/assets-batch-size-configuration.png)

* Experience Manager Assets bevat nu een nieuwe versie 9 van `damAssetLucene` index. `damAssetLucene-9` wijzigt het gedrag van het tellen van Oak Query-facetten in [niet langer het toegangsbeheer op factentellingen evalueren](/help/assets/search-assets.md) wordt geretourneerd door de onderliggende zoekindex, wat resulteert in snellere zoekresponstijden.

### Functies voor pre-release beschikbaar in [!DNL Experience Manager Assets] {#prerelease-features-assets}

* **Dynamic Media**: [Ondersteuning voor multicaption- en multiaudiotracks voor video&#39;s in Dynamic Media](/help/assets/dynamic-media/video.md#about-msma)—U kunt nu eenvoudig meerdere bijschriften en audiotracks toevoegen aan een primaire video. Dit betekent dat uw video&#39;s toegankelijk zijn voor een breed publiek. U kunt één gepubliceerde primaire video aanpassen aan een wereldwijd publiek in meerdere talen en de richtlijnen voor toegankelijkheid voor verschillende geografische regio&#39;s naleven. Auteurs kunnen de bijschriften en audiotracks ook beheren vanaf één tabblad in de gebruikersinterface.

  ![Het tabblad Bijschriften en audiotracks op de pagina Eigenschappen van een geselecteerd video-element.](/help/release-notes/assets/msma-aem-cs.png)*Het tabblad Bijschriften en audiotracks op de pagina Eigenschappen van een geselecteerd video-element.*

* **Activa**: Mogelijkheid om ZIP-archieven te selecteren die in Experience Manager worden beheerd en [bestanden rechtstreeks uitpakken in Experience Manager](/help/assets/manage-digital-assets.md#extract-zip-archives) zonder ze te downloaden.

  ![Items vastzetten voor groepen](/help/release-notes/assets/extract-archive.png)


## [!DNL Experience Manager Forms] als [!DNL Cloud Service] {#forms}

### Nieuwe functies beschikbaar in [!DNL Forms] {#new-features-available-in-forms-channel}

* [**Google reCAPTCHA-bedrijfsondersteuning**](/help/forms/captcha-adaptive-forms.md): Gebruik Google reCAPTCHA Enterprise in een adaptieve vorm om een betere bescherming te bieden tegen frauduleuze activiteiten en spam, zodat gebruikers veiliger worden. Met een geavanceerde risicoanalyse en naadloze integratie kunnen echte gebruikers eenvoudig formulieren indienen terwijl de bots effectief worden geblokkeerd.


### Functies voor pre-release beschikbaar in [!DNL Forms] {#pre-release-features-available-in-forms-channel}

* **Adobe Analytics with Experience Cloud Setup Automation for Forms**: U kunt nu Adobe Analytics met de Automatisering van de Opstelling van het Experience Cloud met een omdraaiing van een paar knopen toelaten. Hiermee kunt u AEM Forms as a Cloud Service verbinden met Experience Platforms-tags en Adobe Analytics om prestatiegegevens voor gepubliceerde formulieren vast te leggen en bij te houden.

* **Adobe Analytics-rapportsjabloon voor Adaptive Forms**: Forms as a Cloud Service geeft nu een Adobe Analytics-rapport OOTB. Zo kunt u gemakkelijk de prestaties van uw formulieren begrijpen. De maatstaven op formulierniveau bieden u inzicht in de manier waarop het formulier werkt met meerdere prestatie-indicatoren (KPI&#39;s), zoals uitvoeringen, bezoekers, verzendingen, gemiddelde vultijd. Door gebruikersgedrag en feedback te volgen, kunt u delen van het formulier identificeren die verwarring veroorzaken en verbeteringen aanbrengen in het ontwerp en de functionaliteit van het formulier.

  ![Adobe Analyserapport Adaptive form user engagement](/help/forms/assets/forms-analytics-report.png)

* **[Formulierfragment in Adaptief Forms op basis van kerncomponenten](/help/forms/adaptive-form-fragments-core-components.md)**: U kunt dubbel werk afscheid nemen, uw digitale inventaris optimaliseren en de samenwerking verbeteren terwijl u de ervaring voor het maken van formulieren vergroot met formulierfragmenten. Deze herbruikbare componenten integreren naadloos in meerdere formulieren, waardoor het maken van consistente en professioneel ogende formulieren wordt gestroomlijnd. Formulierfragmenten zorgen voor herbruikbaarheid, standaardisering en consistentie van merken via de functie &#39;Eenmaal wijzigen en overal weerspiegelen&#39;. Ervaar meer onderhoudsgemak en efficiëntie, aangezien updates die op één plaats worden gemaakt, automatisch worden verspreid over alle vormen die deze fragmenten gebruiken.

* **[Verbeterde Adobe Sign Workflow-stap](/help/forms/aem-forms-workflow-step-reference.md#sign-document-step-sign-document-step)**: De Adobe Sign Workflow-stap wordt uitgebreid en omvat het volgende:
   * **Verificatie op basis van overheidsidentiteitskaart voor Adobe Sign**: Verificatie op basis van een Adobe Acrobat Sign-staatsidentificatie biedt een extra verificatielaag door gebruikers in staat te stellen hun identiteit te verifiëren met behulp van door de overheid uitgegeven id&#39;s (rijbewijs, nationale id, paspoort). Door vertrouwde identificatiedocumenten te gebruiken, voegt deze verbetering een extra niveau van vertrouwen aan het ondertekeningsproces toe, die het ideaal maakt voor scenario&#39;s die verhoogde veiligheid, naleving, en gebruikersbevestiging vereisen.

   * **Audittrail voor Adobe Sign-documenten**: Gebruik de functie Audittrail voor meer informatie over de levenscyclus van uw Adobe Sign-documenten. Met het audittrail, kunt u een uitvoerig verslag van alle acties en interactie handhaven met betrekking tot uw documenten. Dit omvat gegevens zoals wie het document heeft bekeken, bewerkt of ondertekend, samen met tijdstempels voor elke gebeurtenis. Deze verbetering is van cruciaal belang voor het handhaven van de naleving, het oplossen van geschillen en het verzekeren van de integriteit van uw digitale overeenkomsten.

   * **Nieuwe rollen voor ontvangers van de Overeenkomst voorbij enkel de Ondertekenaar**: Adobe Acrobat Sign heeft de optie om de rollen voor overeenkomstontvangers uit te breiden tot buiten alleen de ondertekenaar om beter aan hun workflowvereisten te voldoen. Wanneer toegelaten, heeft elke ontvanger in een Overeenkomst zijn rol individueel configureerbaar, met Ondertekenaar die het gebrek is.

* **[Protect uw documenten met Document Assurance-API&#39;s (onderdeel van communicatie-API&#39;s)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: Met de API&#39;s voor documentverzekering kunt u gevoelige informatie beveiligen door de documenten te ondertekenen en te versleutelen. Door versleuteling wordt de inhoud van een document omgezet in een onleesbare indeling, zodat alleen geautoriseerde gebruikers toegang hebben. Deze versterkte beschermingslaag beschermt niet alleen waardevolle gegevens tegen ongeoorloofde ogen, maar zorgt ook voor gemoedsrust. Met de handtekening-API&#39;s kunt u de beveiliging en privacy van Adobe PDF-documenten die door uw organisatie worden gedistribueerd en ontvangen, beschermen. Deze service gebruikt digitale handtekeningen en certificering om ervoor te zorgen dat alleen de beoogde ontvangers documenten kunnen wijzigen.

* **Ondersteuning voor paginanummers in communicatie-API&#39;s**: Nu kunt u, samen met het ophalen van uw document via de communicatie-API&#39;s, ook de waardevolle informatie over het aantal pagina&#39;s in het document ontvangen.

* **[Fout bij afhandeling van aangepaste fouthandlers in de regeleditor](/help/forms/add-custom-error-handler-adaptive-forms-core-components.md)**: U kunt nu een aangepaste functie aanroepen als reactie op een fout die door een externe service is geretourneerd, en eindgebruikers een op maat gemaakte reactie geven. Bijvoorbeeld, kunt u een douanewerkschema in de achtergrond voor specifieke foutencodes aanhalen of de klant informeren dat de dienst neer is.


### Forms-programma voor vroege adoptie zonder adapter {#forms-early-adopter}

Gebruiken [Forms zonder hoofdadapter](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html) om uw ontwikkelaars in staat te stellen om interactieve formulieren te maken, te publiceren en te beheren die via API&#39;s kunnen worden benaderd en waarmee interactie mogelijk is, in plaats van via een traditionele grafische gebruikersinterface. Met behulp van hoofdloze adaptieve formulieren kunt u:

* multikanaalformulieren van hoge kwaliteit maken in de programmeertaal van uw keuze
* U kunt zelf formulieren integreren in uw bureaublad en mobiele apps, websites en chattoepassingen
* gebruik uw eigen UI-componenten opnieuw met formuliertoepassingen
* de kracht van Adobe Experience Manager Forms gebruiken

U kunt een e-mail verzenden naar `aem-forms-headless@adobe.com` van uw officiële e-mailadres om deel te nemen aan het vroege adoptieprogramma.


## [!DNL Experience Manager] als [!DNL Cloud Service] Stichting {#foundation}

### CDN-logs {#cdn-logs}

Download CDN-logbestanden vanuit Cloud Manager. Dit is handig voor optimalisatie van de cache-hit verhouding en een betere zichtbaarheid in de leveringsstroom van de inhoud. [Meer informatie over](/help/implementing/developing/introduction/logging.md#cdn-log) de CDN-logindeling. Deze functie zal begin september geleidelijk aan aan aan de klanten worden aangeboden.

### Voortijdig-adoptieprogramma voor CDN- en WAF-regels {#waf-early-adopter}

Het verkeer van de filter bij CDN die op wordt gebaseerd:

* aanvraagheaders en -eigenschappen (bijvoorbeeld IP-adres)
* verkeerspatronen gekend om met kwaadwillig verkeer worden geassocieerd

Wilt u de functie proberen en feedback delen? Een e-mail verzenden naar **aemcs-waf-adopter@adobe.com** van uw officiële e-mailadres voor meer informatie over het programma voor vroege adoptie. De ruimte is beperkt.

Meer informatie over de functie in het artikel [hier](/help/security/traffic-filter-rules-including-waf.md).


## Opmerkingen bij de onderhoudsrelease {#maintenance}

U vindt de meest recente opmerkingen in de onderhoudsrelease [hier](/help/release-notes/maintenance/latest.md).

## Cloud Manager {#cloud-manager}

U vindt een volledige lijst met maandreleases van Cloud Manager [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migratiehulpmiddelen {#migration-tools}

U vindt een volledige lijst met de releases van de migratiehulpmiddelen [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
