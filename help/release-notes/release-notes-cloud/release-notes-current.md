---
title: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] als Cloud Service.
description: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] als Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: 03151f72a86e708a0a91c141d5901a9fb7a311a5
workflow-type: tm+mt
source-wordcount: '1191'
ht-degree: 0%

---


# Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] als Cloud Service {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor de huidige (meest recente) versie van [!DNL Experience Manager] als Cloud Service weergegeven.

>[!NOTE]
>
>Vanaf hier kunt u navigeren om notities van eerdere versies weer te geven. bijvoorbeeld voor die in 2020, 2021, enzovoort.

>[!NOTE]
>
>Zie [Recente documentatieupdates](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor meer informatie over documentatie-updates die niet rechtstreeks verband houden met een release.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als [!DNL Cloud Service] huidige release (2021.8.0) is 26 augustus 2021.
De volgende release (2021.9.0) vindt plaats op 30 september 2021.

## Video vrijgeven {#release-video}

Bekijk de video [August 2021 Release Overview](https://video.tv.adobe.com/v/336277) voor een overzicht van de toegevoegde functies.

## [!DNL Experience Manager Assets] als  [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#assets-features}

* Wanneer gebruikers digitale elementen delen als een koppeling, kunnen ze de URL direct naar het klembord kopiëren. Dankzij deze verbetering kunt u elementen sneller en gemakkelijker delen. Dankzij deze functionaliteit kunt u sneller en handig elementen delen.

   ![De optie URL kopiëren wanneer een element wordt gedeeld als een koppeling](/help/assets/assets/link-share-copy-URL-option.png)
   *Afbeelding: Wanneer u een element deelt als een koppeling, kunt u de URL nu kopiëren en afzonderlijk delen.*

* Wanneer u TXT-bestanden uploadt, genereert de elementmicroservices automatisch een miniatuur. De PNG-miniatuur is een uitvoering van het TXT-bestand waarmee gebruikers de inhoud of de bestanden tot op zekere hoogte kunnen identificeren zonder de bestanden te openen. Deze functionaliteit vereist geen configuratie en werkt standaard.

   ![Een uitvoering van een TXT-bestand wordt automatisch gegenereerd  [!DNL Assets] in PNG-indeling](/help/assets/assets/thumbnail-rendition-txt-file.png)
   *Afbeelding: Er wordt automatisch een uitvoering van een TXT-bestand gegenereerd om u te helpen het bestand te identificeren zonder het te openen.*

### Nieuwe functie in het prerelease-kanaal [!DNL Assets] {#assets-prerelease-features}

* Gebruikers kunnen de elementen die in de zoekresultaten worden weergegeven nu sorteren in de kolom- en kaartweergave. Het sorteren werkt op de kolommen Naam, Gemaakt, Gewijzigd of Geen.

   ![De zoekresultaten sorteren  [!DNL Assets] in de kolom- en kaartweergave](/help/assets/assets/sort-searched-assets.png)
   *Afbeelding: U kunt de zoekresultaten sorteren  [!DNL Assets] in de kolom- en kaartweergave.*

### Buizen vastgesteld in [!DNL Assets] {#assets-bugs-fixed}

* Wanneer een lid van de contributorgroep aan de [!DNL Assets] Console navigeert, wordt een extra `POST` verzoek geproduceerd om een Inzameling te proberen en tot stand te brengen. Dit verzoek wordt niet vereist, het ontbreekt wegens toestemmingskwesties, en leidt tot veel fouten in de logboeken. (CQ-4328856)
* Wanneer gebruikers een element weergeven en [!UICONTROL Timeline] selecteren in het pop-upmenu in het linkerdeelvenster, wordt een fout weergegeven. In de logboeken, worden vele waarschuwingen geregistreerd toe te schrijven aan een slechte vraag. (CQ-4328919)

## [!DNL Experience Manager Forms] als  [!DNL Cloud Service] {#forms}

### Nieuw in [!DNL Forms] {#what-is-new-forms}

<!-- * Automated Forms Conversion service can [convert PDF Forms in Italian and Portuguese language](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?#language-specific-meta-model) to Adaptive Forms. -->

* AEM Archetype-project voor Forms als Cloud Service bevat nu [4 nieuwe thema&#39;s en formuliergegevensmodellen voor Microsoft Dynamics en Salesforce.com](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/setup-environment/setup-local-development-environment.html?#forms-cloud-service-local-development-environment).

* **Op acroform gebaseerd Document of Record**: AEM Forms als Cloud Service ondersteunt het gebruik van  [Adobe Acrobat Form PDF (Acroform PDF) ](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/create-an-adaptive-form/generate-document-of-record-for-non-xfa-based-adaptive-forms.html) als sjabloon voor Document of Record naast XFA-formuliersjablonen.

* **Microsoft Azure Data Store-connector**: U kunt nu het Model van de Gegevens van het Vorm met de Opslag [ van Microsoft Azure ](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/use-form-data-model/configure-azure-storage.html)verbinden. Hiermee kunt u adaptieve formuliergegevens ophalen en opslaan naar Microsoft Azure Storage als een BLOB.

### Bètafunctie van [!DNL Forms] {#aug-what-is-new-forms-prerelease}

* **Unified Storage-connector:met de** Unified Storage-connector kunt u uw gegevensbronnen aansluiten op een AEM workflow of een adaptief formulier zonder gegevens over de opslag van AEM Forms-Cloud Servicen te behouden. Hiermee kunt u PII (Persoonlijk identificeerbare informatie) veilig verwerken en gegevens rechtstreeks opslaan in de Azure-gegevensopslag.

* **[!DNL AEM Forms as a Cloud Service - Communications]**:  [Communicatie-](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/aem-forms-cloud-service-communications.html) APIschappen combineren XDP-sjablonen en XML-gegevens om afdrukdocumenten in verschillende indelingen te genereren. Met deze service kunt u documenten genereren in synchrone modus. Met de API&#39;s kunt u toepassingen maken waarmee u:
   * Genereer documenten door sjabloonbestanden te vullen met XML-gegevens.
   * Uitvoerformulieren genereren in verschillende indelingen, waaronder niet-interactieve PDF-afdrukstromen.
   * Genereer PDF-bestanden voor afdrukken vanuit een XFA-formulier, PDF- en Adobe Acrobat-formulier.

U kunt naar [!DNL formscsbeta@adobe.com] schrijven om u aan te melden voor het bètaprogramma.

### Nieuwe functies beschikbaar in het prerelease-kanaal [!DNL Forms] {#prerelease-features-forms}

* **Adobe Sign-rollen gebruiken in een adaptief formulier**: Adobe Sign for business and enterprise service levels hebben de mogelijkheid om de rollen voor overeenkomstontvangers uit te breiden, tot buiten alleen de ondertekenaar, zodat ze beter kunnen voldoen aan hun workflowvereisten. U kunt elke ontvanger van overeenkomst nu [toelaten om zijn rol in een Aangepast Vorm ](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/create-an-adaptive-form/use-adobe-sign/working-with-adobe-sign.html?#addsignerstoanadaptiveform) te vormen, met Ondertekenaar die de standaardrol is.

* **Analyses voor Adaptive Forms**: U kunt het gedrag van de eindgebruiker nu vastleggen en volgen via Adobe Analytics for Adaptive Forms om inzichten van de eindgebruiker te verzamelen. Het helpt geïnformeerde beslissingen te nemen op basis van gegevens om de gebruikerservaring te verbeteren.

* **Maak eenvoudig verbinding met AEM Forms met Microsoft Dynamics en Salesforce.com**: De dienst verstrekt uit de doos gegevensbronconfiguratie en gegevensmodellen voor de Dynamica van Microsoft en Salesforce.com, die het voor ontwikkelaars  [sneller en gemakkelijker maken om de Dynamiek van Microsoft en Salesforce.com als gegevensbronnen voor een adaptieve vorm](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/use-form-data-model/configure-msdynamics-salesforce.html) te vormen.

## CIF-invoegtoepassing {#cloud-services-cif}

### Nieuwe functies {#what-is-new-cif}

* De nieuwe interface van de Categoriekiezer voor betere gebruikerservaring, verhoogde efficiency en betere steun voor complexe productcatalogus

   ![Nieuwe rubriekkiezer](/help/assets/CIF/category-picker.png)

* Betere A11Y-ondersteuning voor CIF Core-componenten

## Cloud Manager {#cloud-manager}

In deze sectie worden de opmerkingen bij de release voor Cloud Manager in AEM beschreven als Cloud Service 2021.8.0 en 2021.7.0.

## Releasedatum {#release-date-cm-aug}

De releasedatum voor Cloud Manager in AEM als Cloud Service 2021.8.0 is 12 augustus 2021.
De volgende release is gepland voor 9 september 2021.

### Wat is er nieuw? {#what-is-new-aug}

* Klanten van Cloud Servicen kunnen nu SLA-rapporten (Service Level Agreement) weergeven in Cloud Manager. Dit zal de komende maanden geleidelijk beschikbaar worden gesteld.
Zie [SLA Rapportering](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/sla-reporting.html) om meer te leren.

* Het type en de strengheid van de IndexType en `IndexDamAssetLucene` kwaliteitsregels zijn veranderd. Dit zijn nu beide bugs van Blocker *serverity*.

* De nieuwe de kwaliteitsregels van de indexkwaliteit van de eikel zijn geïntroduceerd om asynchrone en tika configuraties te behandelen.

* Verhoog de maximale SSL-certs per programma tot 50.

* Self-service mogelijkheid om gebruikers in staat te stellen meerdere opslagruimten te maken en te beheren via de interface van Cloud Manager.

* SonarQube leest onnodig de gegevens uit de Git-geschiedenis. Op grote codebasis, zou dit tot een onnodige bouwstijlprestaties kunnen leiden.

* Er is nu een API beschikbaar om het Geweven gebiedsdeelheidsgeheime voorgeheugen per pijpleiding ongeldig te maken.

* De versie van het AEM Project Archetype dat wordt gebruikt door Cloud Manager is bijgewerkt naar versie 29.

### Opgeloste problemen {#bug-fixes-aug}

* Update Available status should not be displayed when the latest release is less than the current release.

* De eerste instapweigering mislukte voor nieuwe organisaties met zeer lange namen.

* Af en toe, wanneer een pijpleiding tweemaal om één of andere reden wordt teweeggebracht, resulteert het in één van de uitvoeringen die met *geen status van de pijpleidingsuitvoering kan bijwerken* fout.

## De tool Content Transfer {#content-transfer-tool}

### Releasedatum {#release-date-ctt-latest}

De releasedatum voor Content Transfer Tool v1.5.6 is 11 augustus 2021.

### Opgeloste problemen {#bug-fixes-ctt}

* In sommige gevallen zijn niet alle gebruikers gemigreerd naar de doelinstantie. Om deze moeilijke CTT v1.5.6 te krijgen wordt vereist samen met aem-ethos-hulpmiddelen 1.2.354 of recentere versie op het doel AEM als instantie van de Cloud Service.

* De **Stop Ingestie** knoop werd onbruikbaar gemaakt tijdens opname aan de Publish instantie. Dit is niet nodig omdat er geen stap voor het herstellen van het mongo is tijdens de opname van Publiceren.

* CTT heeft de map `/tmp` niet opgeschoond na een geslaagde extractie. Dit leidde soms tot problemen met schijfruimte.

