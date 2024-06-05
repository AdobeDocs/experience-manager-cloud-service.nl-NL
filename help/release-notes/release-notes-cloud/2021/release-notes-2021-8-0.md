---
title: Opmerkingen bij de release 2021.8.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de release 2021.8.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 8b041934-1c4a-4670-9b03-d38f683b99e5
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1010'
ht-degree: 0%

---

# Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor de huidige (meest recente) versie van [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Vanaf hier kunt u navigeren om notities van eerdere versies weer te geven. Bijvoorbeeld voor die in 2020 en 2021.

>[!NOTE]
>
>Zie [Recente documentatieupdates](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor meer informatie over documentatie-updates die niet rechtstreeks verband houden met een release.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als [!DNL Cloud Service] huidige release (2021.8.0) is 26 augustus 2021.
De volgende release (2021.9.0) vindt plaats op 6 oktober 2021.

## Video vrijgeven {#release-video}

Kijk eens naar de [Overzicht release augustus 2021](https://video.tv.adobe.com/v/336277) video voor een overzicht van de toegevoegde functies.

## [!DNL Experience Manager Assets] als [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#assets-features}

* Wanneer de gebruiker digitale middelen als verbinding deelt, kan de gebruiker URL aan het klembord onmiddellijk kopiëren. Dankzij deze verbetering kunt u elementen sneller en handiger delen. Dankzij deze functionaliteit kunt u sneller en handig elementen delen.

  ![De optie URL kopiëren wanneer een element wordt gedeeld als een koppeling](/help/assets/assets/link-share-copy-URL-option.png)
  *Afbeelding: wanneer u een element deelt als een koppeling, kunt u de URL nu kopiëren en afzonderlijk delen.*

* Wanneer u TXT-bestanden uploadt, genereren de elementmicroservices automatisch een miniatuur. De PNG-miniatuur is een uitvoering van een TXT-bestand waarmee gebruikers de inhoud of de bestanden tot op zekere hoogte kunnen identificeren zonder de bestanden te openen. Deze functionaliteit vereist geen configuratie en werkt standaard.

  ![Er wordt automatisch een uitvoering van een TXT-bestand gegenereerd door [!DNL Assets] in PNG-indeling](/help/assets/assets/thumbnail-rendition-txt-file.png)
  *Afbeelding: Er wordt automatisch een uitvoering van een TXT-bestand gegenereerd om u te helpen het bestand te identificeren zonder het te openen.*

### Nieuwe functie in het dialoogvenster [!DNL Assets] prerelease-kanaal {#assets-prerelease-features}

* Gebruikers kunnen de elementen die in de zoekresultaten worden weergegeven nu sorteren in de kolom- en kaartweergave. Het sorteren werkt op de kolommen Naam, Gemaakt, Gewijzigd of Geen.

  ![De zoekresultaten sorteren in [!DNL Assets] in kolom- en kaartweergaven](/help/assets/assets/sort-searched-assets.png)
  *Afbeelding: De zoekresultaten sorteren in [!DNL Assets] in de kolom- en kaartweergave.*

### Buizen vastgesteld in [!DNL Assets] {#assets-bugs-fixed}

* Wanneer een lid van de contributiegroep naar de [!DNL Assets] Console, een extra `POST` Er wordt een aanvraag gegenereerd om een verzameling te maken. Dit verzoek is niet vereist. Het mislukt vanwege problemen met machtigingen en het leidt tot veel fouten in de logbestanden. (CQ-4328856)
* Wanneer gebruikers een element weergeven en de optie [!UICONTROL Timeline] in het pop-upmenu in het linkerdeelvenster wordt een fout weergegeven. In de logboeken, worden vele waarschuwingen geregistreerd toe te schrijven aan een slechte vraag. (CQ-4328919)

## [!DNL Experience Manager Forms] als [!DNL Cloud Service] {#forms}

### Nieuwe functies in [!DNL Forms] {#what-is-new-forms}

* De service automatede form conversion kan [PDF forms converteren naar Italiaans en Portugees](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?#language-specific-meta-model) naar Adaptive Forms.

* **Op acroform gebaseerd document of record**: as a Cloud Service AEM Forms-ondersteuning voor [Adobe Acrobat Form PDF (Acroform PDF)](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/generate-document-of-record-for-non-xfa-based-adaptive-forms.html) als een sjabloon voor Document of Record naast XFA-formuliersjabloon.

* **Microsoft® Azure Data Store-connector**: U kunt nu [Formuliergegevensmodel aansluiten op Microsoft® Azure Storage](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/configure-azure-storage.html). Hiermee kunt u adaptieve formuliergegevens ophalen en opslaan naar Microsoft® Azure Storage als een BLOB.

### Nieuwe functies beschikbaar in [!DNL Forms] prerelease-kanaal {#prerelease-features-forms}

* **Adobe Sign-rollen gebruiken in een adaptief formulier** - Adobe Sign for business and enterprise service levels kunnen optioneel de rollen voor overeenkomstontvangers uitbreiden, naast alleen de ondertekenaar, om beter aan hun workflowvereisten te voldoen. U kunt nu elke ontvanger van de overeenkomst inschakelen om zijn rol in een adaptief formulier te configureren, waarbij ondertekenaar de standaardrol is.

* **Analyses voor Adaptive Forms** - U kunt nu het gedrag van eindgebruikers vastleggen en volgen via Adobe Analytics for Adaptive Forms om inzichten van eindgebruikers te verzamelen. Het helpt geïnformeerde beslissingen te nemen op basis van gegevens om de gebruikerservaring te verbeteren.

* **Maak eenvoudig verbinding met AEM Forms met Microsoft® Dynamics en Salesforce.com** - De service biedt de configuratie van de box-gegevensbron en gegevensmodellen voor Microsoft® Dynamics en Salesforce.com. Zo kunnen ontwikkelaars Microsoft® Dynamics en Salesforce.com sneller en eenvoudiger configureren als gegevensbronnen voor een adaptieve vorm.

## CIF invoegtoepassing {#cloud-services-cif}

### Nieuwe functies {#what-is-new-cif}

* De nieuwe interface van de Plukker van de Categorie voor betere gebruikerservaring, verhoogde efficiency en betere steun voor complexe productcatalogus

  ![Nieuwe rubriekkiezer](/help/assets/CIF/category-picker.png)

* Betere A11Y-ondersteuning voor CIF Core Components

## Cloud Manager {#cloud-manager}

In deze sectie worden de opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service 2021.8.0 en 2021.7.0 beschreven.

## Releasedatum {#release-date-cm-aug}

De releasedatum voor Cloud Manager in AEM as a Cloud Service 2021.8.0 is 12 augustus 2021.
De volgende release is gepland voor 9 september 2021.

### Wat is er nieuw? {#what-is-new-aug}

* Klanten van Cloud Servicen kunnen nu SLA-rapporten (Service Level Agreement) weergeven in Cloud Manager. Dit zal de komende maanden geleidelijk beschikbaar komen.
Zie [SLA-rapportage](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/sla-reporting.html).

* Het type en de ernst van het IndexType en `IndexDamAssetLucene` de kwaliteitsvoorschriften zijn gewijzigd . Dit zijn nu beide bugs van Blocker *ernst*.

* De nieuwe de kwaliteitsregels van de indexkwaliteit van de eikel zijn geïntroduceerd om asynchrone en configuraties van de Tika te behandelen.

* Verhoog de maximale SSL-certs per programma tot 50.

* Self-service mogelijkheid om gebruikers in staat te stellen meerdere opslagruimten te maken en te beheren via de interface van Cloud Manager.

* SonarQube leest onnodig de gegevens uit de Git-geschiedenis. Op grote codebasis, zou dit tot een onnodige bouwstijlprestaties kunnen leiden.

* Er is nu een API beschikbaar om het Geweven gebiedsdeelheidsgeheime voorgeheugen per pijpleiding ongeldig te maken.

* De versie van het AEM Project Archetype dat wordt gebruikt door Cloud Manager is bijgewerkt naar versie 29.

### Opgeloste problemen {#bug-fixes-aug}

* Update Available status should not appear when the latest release is less than the current release.

* De eerste instapweigering mislukte voor nieuwe organisaties met lange namen.

* Soms, wanneer een pijpleiding tweemaal om een bepaalde reden in werking wordt gesteld, resulteert het in één van de executies die met een *`cannot update pipeline execution status`* fout.

## Inhoud overbrengen {#content-transfer-tool}

### Releasedatum {#release-date-ctt-latest}

De releasedatum voor Content Transfer Tool v1.5.6 is 11 augustus 2021.

### Opgeloste problemen {#bug-fixes-ctt}

* Soms zijn niet alle gebruikers gemigreerd naar de doelinstantie. Om deze correctie te verkrijgen, is CTT v1.5.6 vereist samen met aem-ethos-tools 1.2.354 of recentere versie op het doel AEM as a Cloud Service instantie.

* De **Inscriptie stoppen** werd uitgeschakeld tijdens het toevoegen aan de instantie Publiceren. Dit is niet nodig omdat er geen stap voor het herstellen van het mongo is tijdens de opname van Publiceren.

* De CTT heeft de `/tmp` map na een extractie. Dit leidde soms tot problemen met schijfruimte.
