---
title: Nota's van de versie voor 2023.8.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Nota's van de versie voor 2023.8.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: a0ffa6cf-64ae-468c-93f4-ac6805ef907e
feature: Release Information
role: Admin
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1691'
ht-degree: 0%

---

# Opmerkingen bij de release 2023.8.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de versie 2023.8.0 van [!DNL Experience Manager] as a Cloud Service beschreven.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige release met functies (2023.8.0) is 31 augustus 2023. De volgende release met functies (2023.9.0) is gepland voor 28 september 2023.

## Video vrijgeven {#release-video}

Bekijk de video Overzicht van de release van augustus 2023 voor een overzicht van de functies die in de release van 2023.8.0 zijn toegevoegd:

>[!VIDEO](https://video.tv.adobe.com/v/3423535/?quality=12)

## [!DNL Experience Manager Sites] als een [!DNL Cloud Service] {#sites}

### Nieuwe functies in [!DNL Experience Manager Sites] {#sites-features}

* De [&#x200B; Console van het Fragment van de Inhoud &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/content-fragments/content-fragments-console.html?lang=nl-NL) staat nu gebruikers toe om markeringen en onderzoek door markeringen te bekijken die als meta-gegevens op de Fragmenten van de Inhoud worden toegepast. Gebruikers hoeven voor deze functie niet meer over te schakelen op de gebruikersinterface van Assets, waardoor contextomschakeling wordt beperkt en de efficiëntie wordt verbeterd.

  ![&#x200B; Tags toevoegen in de Console van het Fragment van de Inhoud &#x200B;](/help/assets/content-fragments-console-tags.png)
* De nieuwe Content Fragment Editor is nu beschikbaar in AEM as a Cloud Service. Het stelt inhoudsauteurs in staat productiever te zijn door hun ontwerptaken te stroomlijnen en de noodzaak om tussen verschillende apps te schakelen tijdens het bewerken van inhoud te verminderen.
  ![&#x200B; Nieuwe Redacteur van het Fragment van de Inhoud &#x200B;](/help/release-notes/assets/newCFEditor.png)

De nieuwe editor voor inhoudsfragmenten biedt de volgende voordelen die niet beschikbaar zijn in de oorspronkelijke editor:

* Automatisch opslaan om efficiënter te ontwerpen en te voorkomen dat bewerkingen per ongeluk verloren gaan.
* De hiërarchische weergave van een inhoudsfragment en de bijbehorende verwijzingen met de boomstructuur voor snelle navigatie binnen een diep gestructureerd fragment.
  ![&#x200B; de Boom van de Structuur in de Redacteur van het Fragment van de Inhoud &#x200B;](/help/release-notes/assets/newCFEditor_StructureTree.png)

* In line uploaden van elementen als inhoudsverwijzingen zonder dat deze eerst naar Asset DAM hoeven te worden geüpload
* Ad-hocvoorvertoning van de gerenderde ervaring die door het inhoudsfragment wordt geleverd om auteurs te helpen de vormgeving van de inhoud op de frontend-app te visualiseren
* 1-klik het publiceren en unpublishing van het inhoudsfragment van de redacteur
* Taalkopieën weergeven en naar deze talen navigeren tijdens het bewerken van een inhoudsfragment
  ![&#x200B; Exemplaren van de Taal in de Redacteur van het Fragment van de Inhoud &#x200B;](/help/release-notes/assets/newCFEditor_LanguageCopies.PNG)

* Versies weergeven om de tijdlijn van een inhoudsfragment bij te houden

  ![&#x200B; Versies in de Redacteur van het Fragment van de Inhoud &#x200B;](/help/release-notes/assets/newCFEditor_Versionhistory.PNG)

* Bovenliggende verwijzingen weergeven om auteurs inzicht te geven in het effect van hun bewerkingen

  ![&#x200B; Verwijzingen van de Ouder in de Redacteur van het Fragment van de Inhoud &#x200B;](/help/release-notes/assets/newCFEditor_Parentreferences.PNG)

## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Nieuwe functies in de Assets-weergave {#assets-view-features}

<!--

**Assign metadata form to a folder**

You can now assign metadata form to a specific folder within your Assets Essentials deployment. All assets in the folder, including assets in the sub-folders, then display properties defined in the assigned metadata form.

![assign metadata form to a folder](/help/release-notes/assets/assign-to-folder.png)

-->

* **Bulk de invoeractiva van gegevensbronnen**: De beheerders hebben nu de [&#x200B; capaciteit om groot aantal activa &#x200B;](/help/assets/bulk-import-assets-view.md) van een gegevensbron in AEM Assets in te voeren. De beheerders hoeven geen afzonderlijke elementen of mappen meer te uploaden naar AEM Assets. Tot de ondersteunde gegevensbronnen voor bulkimport behoren Azure, AWS, Google Cloud en Dropbox.

  ![&#x200B; Bulk invoert activa van een gegevensbron &#x200B;](/help/release-notes/assets/bulk-import.png)

* **Beeld die hulpmiddelen uitgeven door Adobe Express** worden aangedreven: Gemakkelijke en intuïtieve [&#x200B; beeld die hulpmiddelen uitgeven door Adobe Express &#x200B;](/help/assets/edit-images-assets-view.md) beschikbaar direct binnen AEM Assets om inhoud te verhogen hergebruik en inhoudssnelheid te versnellen.

  ![&#x200B; Beeld dat met Adobe Express &#x200B;](/help/release-notes/assets/edit-adobe-express.png) uitgeeft

* **Flexibiliteit terwijl het spillen van punten voor Mijn Snelle Toegang van Workspace**: Mogelijkheid om punten voor u, voor uw volledige organisatie, of voor een lijst van groepen te selecteren en te speld zodat zij in de [&#x200B; Snelle sectie van de Toegang van Mijn Workspace &#x200B;](/help/assets/my-workspace-assets-view.md) tonen die op uw selectie wordt gebaseerd.

  ![&#x200B; Vastzetten punten voor groepen &#x200B;](/help/release-notes/assets/pin-items-for-groups.png)

### Nieuwe functies in de beheerweergave {#admin-view-features}

**Verbeteringen van het Onderzoek**

* De beheerders kunnen [&#x200B; de partijgrootte van activa &#x200B;](/help/assets/search-assets.md#configure-asset-batch-size) nu vormen die tonen wanneer u een onderzoek uitvoert. De resultaten van het activaonderzoek tonen in veelvouden van het gevormde aantal van de partijgrootte wanneer u verder neer scrolt om de resultaten te laden. U kunt kiezen uit de beschikbare batchformaten van 200, 500 en 1000 elementen. Als u een lagere batch-grootte instelt, resulteert dit in snellere zoekresponstijden.

  ![&#x200B; Assets de configuratie van de partijgrootte &#x200B;](/help/release-notes/assets/assets-batch-size-configuration.png)

* Experience Manager Assets bevat nu een nieuwe versie 9 van de index van `damAssetLucene` . `damAssetLucene-9` verandert het gedrag van het facet van de Vraag van Oak tellen aan [&#x200B; niet meer toegangsbeheer op de facettellingen &#x200B;](/help/assets/search-assets.md) die door de onderliggende onderzoeksindex zijn teruggekeerd, die in de snellere tijden van de onderzoeksreactie resulteert.

### Functies voor pre-release beschikbaar in [!DNL Experience Manager Assets] {#prerelease-features-assets}

* **Dynamische Media**: [&#x200B; Multi-caption en multi-audiospoorsteun voor video&#39;s in Dynamische Media &#x200B;](/help/assets/dynamic-media/video.md#about-msma) - u kunt veelvoudige titels en veelvoudige audiosporen aan een primaire video nu gemakkelijk toevoegen. Dit betekent dat uw video&#39;s toegankelijk zijn voor een breed publiek. U kunt één gepubliceerde primaire video aanpassen aan een wereldwijd publiek in meerdere talen en de richtlijnen voor toegankelijkheid voor verschillende geografische regio&#39;s naleven. Auteurs kunnen de bijschriften en audiotracks ook beheren vanaf één tabblad in de gebruikersinterface.

  ![&#x200B; Bijschriften en Audiosporen tabel op de pagina van Eigenschappen van een geselecteerd videoelement.](/help/release-notes/assets/msma-aem-cs.png)*Bijschriften en Audiosporen lusje op de pagina van Eigenschappen van geselecteerde videoactiva.*

* **Assets**: Mogelijkheid om de archieven te selecteren van het PIT die in Experience Manager worden beheerd en [&#x200B; die de dossiers direct in Experience Manager &#x200B;](/help/assets/manage-digital-assets.md#extract-zip-archives) halen zonder hen te downloaden.

  ![&#x200B; Vastzetten punten voor groepen &#x200B;](/help/release-notes/assets/extract-archive.png)


## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

### Nieuwe functies beschikbaar in [!DNL Forms] {#new-features-available-in-forms-channel}

* [**Google reCAPTCHA ondernemingssteun**](/help/forms/captcha-adaptive-forms.md): De Onderneming van Google reCAPTCHA in een AanpassingsVorm gebruiken om betere bescherming tegen frauduleuze activiteit en spam te verstrekken, die een veiliger gebruikerservaring verstrekken. Met een geavanceerde risicoanalyse en naadloze integratie kunnen echte gebruikers eenvoudig formulieren indienen terwijl de bots effectief worden geblokkeerd.


### Functies voor pre-release beschikbaar in [!DNL Forms] {#pre-release-features-available-in-forms-channel}

* **Adobe Analytics met de Automatisering van de Opstelling van Experience Cloud voor Forms**: U kunt Adobe Analytics met de Automatisering van de Opstelling van Experience Cloud met een omdraaiing van twee knopen nu toelaten. Hiermee kunt u AEM Forms as a Cloud Service verbinden met Experience Platform-tags en Adobe Analytics om prestatiegegevens voor gepubliceerde formulieren vast te leggen en bij te houden.

* **het rapportmalplaatje van Adobe Analytics voor Adaptieve Forms**: Forms as a Cloud Service verstrekt nu een Adobe Analytics rapport OOTB. Zo kunt u gemakkelijk de prestaties van uw formulieren begrijpen. Met de maatstaven op formulierniveau kunt u een insight laten zien hoe het formulier presteert op meerdere prestatie-indicatoren (KPI&#39;s), zoals uitvoeringen, bezoekers, verzendingen, gemiddelde vultijd. Door gebruikersgedrag en feedback te volgen, kunt u delen van het formulier identificeren die verwarring veroorzaken en verbeteringen aanbrengen in het ontwerp en de functionaliteit van het formulier.

  ![&#x200B; het adaptieve rapport van de de analysegegevens van de vormenbetrokkenheid van de gebruiker &#x200B;](/help/forms/assets/forms-analytics-report.png)

* **[Fragment van de Vorm in Aangepast Forms dat op de Componenten van de Kern](/help/forms/adaptive-form-fragments-core-components.md)** wordt gebaseerd: Zeg afscheid aan duplicatie, optimaliseer uw digitale inventaris, en verbeter samenwerking aangezien u uw vorm-bouwende ervaring met de Fragmenten van de Vorm opheft. Deze herbruikbare componenten integreren naadloos in meerdere formulieren, waardoor het maken van consistente en professioneel ogende formulieren wordt gestroomlijnd. Formulierfragmenten zorgen voor herbruikbaarheid, standaardisering en consistentie van merken via de functie &#39;Eenmaal wijzigen en overal weerspiegelen&#39;. Ervaar meer onderhoudsgemak en efficiëntie, aangezien updates die op één plaats worden gemaakt, automatisch worden verspreid over alle vormen die deze fragmenten gebruiken.

* **[Verbeterde stap van het Werkschema van het Ondertekenen van Adobe](/help/forms/aem-forms-workflow-step-reference.md#sign-document-step-sign-document-step)**: De stap van het Werkschema van het Ondertekenen van Adobe wordt verbeterd om het volgende te omvatten:
   * **op identiteitskaart-Gebaseerde Authentificatie van de Regering voor het Teken van Adobe**: De Op identiteitskaart-Gebaseerde Authentificatie van de Regering van Adobe Acrobat Sign biedt een extra laag van controle door gebruikers toe te laten om hun identiteit voor authentiek te verklaren gebruikend overheids-uitgegeven IDs (rijbewijs, nationale identiteitskaart, paspoort). Door vertrouwde identificatiedocumenten te gebruiken, voegt deze verbetering een extra niveau van vertrouwen aan het ondertekeningsproces toe, die het ideaal maakt voor scenario&#39;s die verhoogde veiligheid, naleving, en gebruikersbevestiging vereisen.

   * **Spoor van de Controle voor de Documenten van het Teken van Adobe**: Gebruik de eigenschap van het Spoor van de Controle voor gedetailleerde inzichten in de levenscyclus van uw documenten van het Teken van Adobe. Met het audittrail, kunt u een uitvoerig verslag van alle acties en interactie handhaven met betrekking tot uw documenten. Dit omvat gegevens zoals wie het document heeft bekeken, bewerkt of ondertekend, samen met tijdstempels voor elke gebeurtenis. Deze verbetering is van cruciaal belang voor het handhaven van de naleving, het oplossen van geschillen en het verzekeren van de integriteit van uw digitale overeenkomsten.

   * **Nieuwe rollen voor de ontvangers van de Overeenkomst voorbij enkel de Ondertekenaar**: Adobe Acrobat Sign heeft de optie om de rollen voor de ontvangers van de Overeenkomst voorbij enkel de Ondertekenaar uit te breiden om hun werkschemavereisten beter aan te passen. Wanneer toegelaten, heeft elke ontvanger in een Overeenkomst zijn rol individueel configureerbaar, met Ondertekenaar die het gebrek is.

* **[bescherm uw documenten met Document Assurance APIs (Deel van Communicatie APIs)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: Het document Assurance APIs machtigt u om gevoelige informatie te beschermen door de documenten te ondertekenen en te coderen. Door versleuteling wordt de inhoud van een document omgezet in een onleesbare indeling, zodat alleen geautoriseerde gebruikers toegang hebben. Deze versterkte beschermingslaag beschermt niet alleen waardevolle gegevens tegen ongeoorloofde ogen, maar zorgt ook voor gemoedsrust. Met de handtekening-API&#39;s kunt u de beveiliging en privacy van Adobe PDF-documenten die door uw organisatie worden gedistribueerd en ontvangen, beschermen. Deze service gebruikt digitale handtekeningen en certificering om ervoor te zorgen dat alleen de beoogde ontvangers documenten kunnen wijzigen.

* **de Steun van de Telling van de Pagina in Communicatie APIs**: Nu, samen met het terugwinnen van uw document door Communicatie APIs, kunt u de waardevolle informatie over het aantal pagina&#39;s ook ontvangen bevat binnen het document.

* **[Fout die met de managers van de douanefout in regelredacteur](/help/forms/add-custom-error-handler-adaptive-forms-core-components.md)** behandelt: U kunt een douanefunctie nu aanhalen als antwoord op een fout door de externe dienst is teruggekeerd en een op maat gemaakte reactie aan eind - gebruikers verstrekken. Bijvoorbeeld, kunt u een douanewerkschema in de achtergrond voor specifieke foutencodes aanhalen of de klant informeren dat de dienst neer is.


### Forms-programma voor vroege adoptie zonder adapter {#forms-early-adopter}

Het gebruik [&#x200B; Zwaardeloze Aanpassings Forms &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=nl-NL) om uw ontwikkelaars toe te laten om, interactieve vormen tot stand te brengen te publiceren en te beheren die met door APIs, eerder dan door een traditioneel grafisch gebruikersinterface kunnen worden betreden en worden in wisselwerking getreden. Met behulp van hoofdloze adaptieve formulieren kunt u:

* multikanaalformulieren van hoge kwaliteit maken in de programmeertaal van uw keuze
* U kunt zelf formulieren integreren in uw bureaublad en mobiele apps, websites en chattoepassingen
* gebruik uw eigen UI-componenten opnieuw met formuliertoepassingen
* de kracht van Adobe Experience Manager Forms gebruiken

U kunt een e-mail naar `aem-forms-headless@adobe.com` verzenden vanuit uw officiële e-mailadres om deel te nemen aan het programma voor vroegtijdige adoptie.


## [!DNL Experience Manager] als een [!DNL Cloud Service] Foundation {#foundation}

### CDN-logs {#cdn-logs}

Download CDN-logbestanden van Cloud Manager. Dit is handig voor optimalisatie van de cache-hit-verhouding en grotere zichtbaarheid in de inhoudsleveringsstroom. [&#x200B; leer over &#x200B;](/help/implementing/developing/introduction/logging.md#cdn-log) het CDN logboekformaat. Deze functie zal begin september geleidelijk aan aan aan de klanten worden aangeboden.

### Programma voor vroege adoptie van CDN- en WAF-regels {#waf-early-adopter}

Het verkeer van de filter bij CDN die op wordt gebaseerd:

* aanvraagheaders en -eigenschappen (bijvoorbeeld IP-adres)
* verkeerspatronen gekend om met kwaadwillig verkeer worden geassocieerd

Wilt u de functie proberen en feedback delen? Verzend een e-mail naar **aemcs-waf-adopter@adobe.com** van uw officiële e-mailidentiteitskaart om meer over het vroege adoptieprogramma te leren. De ruimte is beperkt.

Leer meer over de eigenschap in het artikel [&#x200B; hier &#x200B;](/help/security/traffic-filter-rules-including-waf.md).


## Opmerkingen bij de onderhoudsrelease {#maintenance}

U kunt de recentste nota&#39;s van de onderhoudsversie [&#x200B; hier &#x200B;](/help/release-notes/maintenance/latest.md) vinden.

## Cloud Manager {#cloud-manager}

U kunt een volledige lijst van de maandelijkse versies van Cloud Manager [&#x200B; hier &#x200B;](/help/implementing/cloud-manager/release-notes/current.md) vinden.

## Migratiehulpmiddelen {#migration-tools}

U kunt een volledige lijst van de versies van Hulpmiddelen van de Migratie [&#x200B; hier &#x200B;](/help/journey-migration/release-notes/release-notes-migration-tools-current.md) vinden.
