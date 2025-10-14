---
title: Nota's van de versie voor 2021.8.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Nota's van de versie voor 2021.8.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: 8b041934-1c4a-4670-9b03-d38f683b99e5
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1010'
ht-degree: 0%

---

# Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor de huidige (meest recente) versie van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>
>Vanaf hier kunt u navigeren om notities van eerdere versies weer te geven. Bijvoorbeeld voor die in 2020 en 2021.

>[!NOTE]
>
>Zie [&#x200B; Recente Updates van de Documentatie &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=nl-NL) voor details van documentatieupdates niet direct met een versie verwant.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige release (2021.8.0) is 26 augustus 2021.
De volgende release (2021.9.0) vindt plaats op 6 oktober 2021.

## Video vrijgeven {#release-video}

Heb een blik bij de [&#x200B; Augustus 2021 video van het Overzicht van de Versie &#x200B;](https://video.tv.adobe.com/v/336277) voor een samenvatting van de toegevoegde eigenschappen.

## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#assets-features}

* Wanneer de gebruiker digitale middelen als verbinding deelt, kan de gebruiker URL aan het klembord onmiddellijk kopiëren. Dankzij deze verbetering kunt u elementen sneller en handiger delen. Dankzij deze functionaliteit kunt u sneller en handig elementen delen.

  ![&#x200B; optie van URL van het Exemplaar wanneer het delen van activa als verbinding &#x200B;](/help/assets/assets/link-share-copy-URL-option.png)
  *Cijfer: Wanneer het delen van een activa als verbinding, kunt u URL nu kopiëren om het afzonderlijk te delen.*

* Wanneer u TXT-bestanden uploadt, genereren de elementmicroservices automatisch een miniatuur. De PNG-miniatuur is een uitvoering van een TXT-bestand waarmee gebruikers de inhoud of de bestanden tot op zekere hoogte kunnen identificeren zonder de bestanden te openen. Deze functionaliteit vereist geen configuratie en werkt standaard.

  ![&#x200B; De vertoning van A van een TXT- dossier wordt automatisch geproduceerd door [!DNL Assets] in een formaat PNG &#x200B;](/help/assets/assets/thumbnail-rendition-txt-file.png)
  *Cijfer: Een vertoning van een TXT- dossier wordt automatisch geproduceerd om u te helpen het dossier identificeren zonder te openen.*

### Nieuwe functie in het [!DNL Assets] prereleasekanaal {#assets-prerelease-features}

* Gebruikers kunnen de elementen die in de zoekresultaten worden weergegeven nu sorteren in de kolom- en kaartweergave. Het sorteren werkt op de kolommen Naam, Gemaakt, Gewijzigd of Geen.

  ![&#x200B; Soort de onderzoeksresultaten in [!DNL Assets] in Kolom en de meningen van de Kaart &#x200B;](/help/assets/assets/sort-searched-assets.png)
  *Cijfer: Soort de onderzoeksresultaten in [!DNL Assets] in de meningen van de Kolom en van de Kaart.*

### Buizen gecorrigeerd in [!DNL Assets] {#assets-bugs-fixed}

* Wanneer een lid van de contributiegroep naar de [!DNL Assets] -console navigeert, wordt een extra `POST` -aanvraag gegenereerd om een verzameling te maken. Dit verzoek is niet vereist. Het mislukt vanwege problemen met machtigingen en het leidt tot veel fouten in de logbestanden. (CQ-4328856)
* Wanneer gebruikers een element bekijken en [!UICONTROL Timeline] selecteren in het pop-upmenu in het linkerdeelvenster, wordt een fout weergegeven. In de logboeken, worden vele waarschuwingen geregistreerd toe te schrijven aan een slechte vraag. (CQ-4328919)

## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

### Nieuwe functies in [!DNL Forms] {#what-is-new-forms}

* De dienst van de automatede form conversion kan [&#x200B; PDF forms in het Italiaans en Portugees &#x200B;](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?lang=nl-NL&#language-specific-meta-model) in Aanpassings Forms omzetten.

* **op acroform-Gebaseerd Document van Verslag**: De as a Cloud Service steunen van AEM Forms die [&#x200B; de Vorm van Adobe Acrobat PDF (Acroform PDF) gebruiken &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/generate-document-of-record-for-non-xfa-based-adaptive-forms.html?lang=nl-NL) als malplaatje voor Document van Verslag naast op XFA-Gebaseerd vormmalplaatje.

* **Microsoft® Azure schakelaar van de gegevensopslag**: U kunt [&#x200B; het Model van de Gegevens van de Vorm aan Microsoft® Azure Opslag &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/configure-azure-storage.html?lang=nl-NL) nu verbinden. Hiermee kunt u adaptieve formuliergegevens ophalen en opslaan naar Microsoft® Azure Storage als een BLOB.

### Nieuwe functies beschikbaar in [!DNL Forms] prereleasekanaal {#prerelease-features-forms}

* **de rollen van Adobe Sign van het Gebruik in een AanpassingsVorm** - Adobe Sign voor zaken en ondernemingsde dienstniveaus kunnen naar keuze de rollen voor de ontvangers van de Overeenkomst, voorbij enkel de Ondertekenaar uitbreiden, om hun werkschemavereisten beter aan te passen. U kunt nu elke ontvanger van de overeenkomst inschakelen om zijn rol in een adaptief formulier te configureren, waarbij ondertekenaar de standaardrol is.

* **Analytics voor Aanpassings Forms** - u kunt eindgebruikergedrag via Adobe Analytics voor Aanpassings Forms nu vangen en volgen om eindgebruikerinzicht te verzamelen. Het helpt geïnformeerde beslissingen te nemen op basis van gegevens om de gebruikerservaring te verbeteren.

* **verbindt gemakkelijk AEM Forms met de Dynamica Microsoft® en Salesforce.com** - de dienst verstrekt uit de de bronconfiguratie van de doos en gegevensmodellen voor de Dynamica Microsoft® en Salesforce.com. Zo kunnen ontwikkelaars Microsoft® Dynamics en Salesforce.com sneller en eenvoudiger configureren als gegevensbronnen voor een adaptieve vorm.

## CIF invoegtoepassing {#cloud-services-cif}

### Nieuwe functies {#what-is-new-cif}

* De nieuwe interface van de Plukker van de Categorie voor betere gebruikerservaring, verhoogde efficiency en betere steun voor complexe productcatalogus

  ![&#x200B; Nieuwe Plukker van de Categorie &#x200B;](/help/assets/CIF/category-picker.png)

* Betere A11Y-ondersteuning voor CIF Core Components

## Cloud Manager {#cloud-manager}

In deze sectie worden de opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service 2021.8.0 en 2021.7.0 beschreven.

## Releasedatum {#release-date-cm-aug}

De Releasedatum voor Cloud Manager in AEM as a Cloud Service 2021.8.0 is 12 augustus 2021.
De volgende release is gepland voor 9 september 2021.

### Wat is er nieuw? {#what-is-new-aug}

* Klanten van Cloud Servicen kunnen nu SLA-rapporten (Service Level Agreement) weergeven in Cloud Manager. Dit zal de komende maanden geleidelijk beschikbaar komen.
Zie [&#x200B; SLA die &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/sla-reporting.html?lang=nl-NL) meldt.

* Het type en de ernst van de IndexType- en `IndexDamAssetLucene` kwaliteitsregels zijn gewijzigd. Dit zijn nu beide Bugs van Blocker *strengheid*.

* De nieuwe de kwaliteitsregels van de index van Oak zijn geïntroduceerd om asynchrone en configuraties van de Tika te behandelen.

* Verhoog de maximale SSL-certs per programma tot 50.

* Self-service mogelijkheid om gebruikers in staat te stellen meerdere opslagruimten te maken en te beheren via de gebruikersinterface van Cloud Manager.

* SonarQube leest onnodig de gegevens uit de Git-geschiedenis. Op grote codebasis, zou dit tot een onnodige bouwstijlprestaties kunnen leiden.

* Er is nu een API beschikbaar om het Geweven gebiedsdeelheidsgeheime voorgeheugen per pijpleiding ongeldig te maken.

* De versie van het AEM Project Archetype dat door Cloud Manager wordt gebruikt, is bijgewerkt naar versie 29.

### Opgeloste problemen {#bug-fixes-aug}

* Update Available status should not appear when the latest release is less than the current release.

* De eerste instapweigering mislukte voor nieuwe organisaties met lange namen.

* Soms, wanneer een pijpleiding tweemaal om één of andere reden wordt teweeggebracht, resulteert het in één van de terechtstellingen die met een *`cannot update pipeline execution status`* fout ontbreken.

## Inhoud overbrengen {#content-transfer-tool}

### Releasedatum {#release-date-ctt-latest}

De releasedatum voor Content Transfer Tool v1.5.6 is 11 augustus 2021.

### Opgeloste problemen {#bug-fixes-ctt}

* Soms zijn niet alle gebruikers gemigreerd naar de doelinstantie. Voor deze correctie is CTT v1.5.6 vereist in combinatie met aem-ethos-tools 1.2.354 of hoger op de AEM as a Cloud Service-doelinstantie.

* De **knoop van de Opname van het Einde** werd onbruikbaar gemaakt tijdens opname aan de instantie van Publish. Dit is niet nodig omdat er geen mongo-herstelstap is tijdens Publish-inname.

* CTT heeft de map `/tmp` na een geslaagde extractie niet opgeschoond. Dit leidde soms tot problemen met schijfruimte.
