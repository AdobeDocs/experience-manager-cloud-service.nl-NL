---
title: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service.
description: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: e9fa68869ca92945c44a79b783fbc8a53a875e81
workflow-type: tm+mt
source-wordcount: '1570'
ht-degree: 0%

---


# Huidige releaseopmerkingen voor as a Cloud Service [!DNL Adobe Experience Manager] {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release weergegeven voor de huidige (meest recente) versie van [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Vanaf hier kunt u navigeren om notities van eerdere versies weer te geven. bijvoorbeeld voor die in 2020, 2021, enzovoort.

>[!NOTE]
>
>Zie [Recente documentatieupdates](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor meer informatie over documentatie-updates die niet rechtstreeks verband houden met een release.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als [!DNL Cloud Service] huidige release (2021.9.0) is 6 oktober 2021.
De volgende release (2021.10.0) is op 28 oktober 2021.

## Video vrijgeven {#release-video}

Bekijk de video [September 2021 van de Versie Overzicht](https://video.tv.adobe.com/v/337381) voor een samenvatting van de toegevoegde eigenschappen.

## [!DNL Experience Manager Sites] als  [!DNL Cloud Service] {#sites}

### Nieuwe functie in het prerelease-kanaal [!DNL Sites] {#sites-prerelease-features}

* Inhoudsfragmentmodellen worden nu automatisch ingesteld op de status Alleen-lezen als ze eenmaal zijn gepubliceerd. Zo voorkomt u dat live API-query&#39;s per ongeluk worden afgebroken als een bewerkt model opnieuw wordt gepubliceerd. Gebruikers krijgen een waarschuwing te zien wanneer ze proberen een gepubliceerd model te bewerken. Bewerken is mogelijk bij het accepteren van de waarschuwing.

## [!DNL Experience Manager Assets] als  [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#assets-features}

* Gebruikers kunnen de elementen die in de zoekresultaten worden weergegeven nu sorteren in de kolom- en kaartweergave. Het sorteren werkt op de kolommen Naam, Gemaakt, Gewijzigd of Geen.

   ![De zoekresultaten sorteren  [!DNL Assets] in de kolom- en kaartweergave](/help/assets/assets/sort-searched-assets.png)
   *Afbeelding: U kunt de zoekresultaten sorteren  [!DNL Assets] in de kolom- en kaartweergave.*

* Voor het programmatisch aanroepen van verwerking met behulp van asset microservices wordt een nieuwe API geïntroduceerd. Ontwikkelaars kunnen nu een bestaand verwerkingsprofiel op mapniveau toepassen op een of meer specifieke elementen in een map. Het verwerkingsprofiel wordt toegepast op basis van aangepaste updates van eigenschappen van metagegevens. Zie `AssetProcessor` in [[!DNL Experience Manager] API referentie](https://www.adobe.io/experience-manager/reference-materials/). Zoals eerder is het mogelijk om de elementmicroservices van de gebruikersinterface [te gebruiken.](/help/assets/asset-microservices-configure-and-use.md)

<!-- Leave this commented.

### New feature in the [!DNL Assets] prerelease channel {#assets-prerelease-features}

Apparently, no new Assets features in Sep beta channel.
A/V transcription feature via CQ-4303854 has moved to Oct beta now.

### Bugs fixed in [!DNL Assets] {#assets-bugs-fixed}

No customer-reported bugs fixed in Sep release.
CQ-4328183 was not reported on CS so not documented here.
-->

## [!DNL Experience Manager Forms] als  [!DNL Cloud Service] {#forms}

### Nieuw in [!DNL Forms] {#what-is-new-forms-sep-2021}

* **Adobe Sign-rollen gebruiken in een adaptief formulier**: Adobe Sign for business and enterprise service levels hebben de mogelijkheid om de rollen voor overeenkomstontvangers uit te breiden, tot buiten alleen de ondertekenaar, zodat ze beter kunnen voldoen aan hun workflowvereisten. U kunt elke ontvanger van overeenkomst nu [toelaten om zijn rol in een Aangepast Vorm ](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/create-an-adaptive-form/use-adobe-sign/working-with-adobe-sign.html#addsignerstoanadaptiveform) te vormen, met Ondertekenaar die de standaardrol is.

* **Analyses voor Adaptive Forms**: U kunt het gedrag van de eindgebruiker nu vastleggen en volgen via Adobe Analytics for Adaptive Forms om inzichten van de eindgebruiker te verzamelen. Het helpt geïnformeerde beslissingen te nemen op basis van gegevens om de gebruikerservaring te verbeteren.

* **Sluit AEM Forms eenvoudig aan op Microsoft Dynamics en Salesforce**: De dienst verstrekt uit de doos gegevensbronconfiguratie en gegevensmodellen voor de Dynamica en Salesforce van Microsoft, die het voor ontwikkelaars  [sneller en gemakkelijker maken om de Dynamica en Salesforce van Microsoft als gegevensbronnen voor een adaptieve vorm](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/use-form-data-model/configure-msdynamics-salesforce.html?lang=en) te vormen.

* **Een adaptief formulier elektronisch ondertekenen met DocuSign:** U kunt DocuSign gebruiken om een adaptief formulier elektronisch te ondertekenen. De service biedt een aangepaste verzendactie om DocuSign te gebruiken met een adaptief formulier. U kunt het pakket dat beschikbaar is op Softwaredistributie installeren om de verzendactie te importeren.

### Bètafuncties van [!DNL Forms] {#sep-what-is-new-forms-prerelease}

* **Unified Storage-connector:** gebruik Unified Storage-connector om procesgegevens in door de klant beheerde opslagruimten extern te maken. U kunt bijvoorbeeld
   * Schakel de functie Opslaan en hervatten van Forms Portal in en sla adaptieve formulierconcepten op in een gegevensopslagruimte onder klantbeheer.
   * Sla AEM werkstroomgegevens (AEM gegevens van de Variabelen van het Werkschema) op die Gevoelige Persoonlijke Gegevens (SPD) in een klant-beheerde bewaarplaats bevatten.

* **[!DNL AEM Forms as a Cloud Service - Communications]**:  [Communicatie-](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/aem-forms-cloud-service-communications.html?lang=en) APIschappen combineren XDP-sjablonen en XML-gegevens om afdrukdocumenten in verschillende indelingen te genereren. Met deze service kunt u documenten genereren in synchrone modus. Met de API&#39;s kunt u toepassingen maken waarmee u:
   * Genereer documenten door sjabloonbestanden te vullen met XML-gegevens.
   * Uitvoerformulieren genereren in verschillende indelingen, waaronder niet-interactieve PDF-afdrukstromen.
   * Afdruk-PDF-bestanden genereren op basis van een XFA-formulier met PDF en Adobe Acrobat-formulier.

U kunt naar [!DNL formscsbeta@adobe.com] schrijven om u aan te melden voor het bètaprogramma.

## CIF-invoegtoepassing {#cloud-services-cif}

### Nieuwe functies {#what-is-new-cif}

* Het nieuwe lusje &quot;bijbehorende commerciële inhoud&quot;in de redacteur van Plaatsen verhoogt auteur efficiency door snel toegang tot relevante AEM productinhoud voor de huidige context te krijgen

   ![Gekoppelde commerciële inhoud](/help/assets/CIF/associated-commerce-content.png)

* Verbeterde gebruikersinterface van productkiezer voor een betere gebruikerservaring, verbeterde efficiëntie en ondersteuning voor complexe productcatalogus

   ![Nieuwe productkiezer](/help/assets/CIF/product-picker.png)

* Eigenschap &quot;include_in_menu&quot; in navigatiecomponent respecteren

### Opgeloste problemen {#bug-fixes-cif}

* Het leegmaken van de menucache werkt niet zoals verwacht

* JS-fouten tijdens AEM CS-implementatiestap en wanneer geen clientside-componenten worden gebruikt

* Kan CIF-wolkenconfiguratie niet maken in mappen met een sling:confignode

## [!DNL Experience Manager Screens] als  [!DNL Cloud Service] {#screens}

### Nieuwe functies {#what-is-new-screens}

* as a Cloud Service schermen ondersteunen nu elementaire afspeelcontrole. De speler zal nu diverse playbackmetriek met elk melden pingelt (gebrek aan 30 seconden). Op basis van de meetgegevens kunnen verschillende randgevallen worden gedetecteerd (geplakte ervaring, leeg scherm, planningsprobleem, enz.). Met deze functie kan het team op afstand controleren of een speler inhoud correct afspeelt, de reactiviteit verbetert tot lege schermen of gebroken ervaringen in het veld en het risico dat de eindgebruiker een verbroken ervaring krijgt verkleind.
Zie [Basic Playback Monitoring](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/manage-player-registration/installing-screens-cloud-player.html?lang=en#playback-monitoring) voor meer informatie.

* Ondersteuning van miniaturen voor video&#39;s wordt nu ondersteund in as a Cloud Service schermen. Een inhoudauteur kan een duimnagel voor video&#39;s bepalen zodat het beeld als placeholder kan worden gebruikt en behoorlijk het playback en richten van inhoud testen, terwijl de daadwerkelijke video door het aangewezen team wordt gebeëindigd. De afbeelding kan ook worden gebruikt voor het geval dat het afspelen van de video mislukt.
Zie [Ondersteuning van miniaturen voor video&#39;s](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/core-product-features/thumbnail-support-videos.html) voor meer informatie.

### Opgeloste problemen {#bug-fixes-screens}

* De speler kan de inhoud van de ingesloten pagina niet weergeven en dit probleem is nu opgelost.

* Na een geslaagde aanmelding werd het navigeren naar de standaardpagina (kanalen) beëindigd op een pagina Interne serverfout.

* Gekoppelde tagitems zijn niet verwijderd tijdens het verwijderen van afspeellijsten.

## [!DNL Experience Manager as a Cloud Service] Stichting {#foundation}

### Nieuwe functies in [!DNL Experience Manager as a Cloud Service] {#foundation-features}

**Geavanceerde netwerken**

>[!INFO]
>
>De geavanceerde voorzien van een netwerkeigenschap maakt deel uit van de versie 2021.9.0, en zal voor klanten medio oktober worden toegelaten.

[!DNL Adobe Experience Manager] als  [!DNL Cloud Service] nu biedt verscheidene soorten geavanceerde voorzien van een netwerkmogelijkheden, die omvatten:

* Flexibele uitgang van de Haven om verkeer uit niet-standaardhavens te ontspannen. Dit is nu mogelijk zonder contact op te nemen met de Adobe Support.
* Het specifieke IP adres van de uitgang om verkeer uit AEM as a Cloud Service van unieke IP te ontslaan, nu ondersteunend alle havens.
* VPN om verkeer tussen uw infrastructuur en AEM as a Cloud Service te beveiligen.

Lees de [documentatie](/help/security/configuring-advanced-networking.md) voor meer informatie, met inbegrip van hoe te om voorziening geavanceerd voorzien van een netwerk te dienen gebruikend de APIs van de Manager van de Wolk.

**Indexoptimalisatie**

Om de prestaties van onderzoeksvragen en het indexeren te verbeteren, is full-text index lucene-2 niet meer buiten-de-doos in [!DNL Adobe Experience Manager] als [!DNL Cloud Service] van deze versie inbegrepen. Om deze full-text index over AEM milieu&#39;s in overeenstemming met AEM klanten te verwijderen, werkt de Techniek van Adobe individueel en pro-actief met klanten voor een zachte en duurzame verwijdering van Lucene full-text index. Ga naar [!DNL Adobe Experience Manager] als [!DNL Cloud Service] [documentatie](/help/operations/indexing.md#index-optimizations) voor meer informatie en neem rechtstreeks contact op met onze ondersteuning als u vragen hebt.

## Cloud Manager {#cloud-manager}

In deze sectie worden de opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service 2021.9.0 en 2021.8.0 beschreven.

## Releasedatum {#release-date-cm-sept}

De releasedatum voor Cloud Manager in AEM as a Cloud Service 2021.9.0 is 9 september 2021.
De volgende release is gepland voor 7 oktober 2021.

### Wat is er nieuw? {#what-is-new-cm-sept}

* De versie van het AEM Projectarchetype dat door de Manager van de Wolk wordt gebruikt is bijgewerkt aan versie 30.

* De programmakaarten op de landingspagina van Cloud Manager en de bijbehorende ervaring zijn vernieuwd.

* Het logbestand met stappen voor codekwaliteit bevat nu uitgebreide logboekgegevens over het OakPal-scanproces.

* De opties in het menu van de pagina Activiteit bevatten nu een optie voor **Logbestand downloaden** voor voltooide uitvoering van de codegenerator. Als u deze optie selecteert, wordt het logboek met de stap build gedownload.

* Als u rechtstreeks op de programmakaart klikt, gaat u nu naar de overzichtspagina van Cloud Manager.

### Opgeloste problemen {#bug-fixes-sept}

* De gebruiker zal nu een begrijpelijker bericht wanneer het proberen om een nieuwe IP Lijst van gewenste personen in een programma toe te voegen dat het maximum toegestane aantal IP Lijsten van gewenste personen heeft bereikt die kunnen worden gevormd.

* Er is een onjuiste URL gekopieerd bij het selecteren van de menuoptie URL kopiëren in het scherm Opslagplaatsen.

## Cloud Acceleration Manager {#cam}

### Releasedatum {#release-date-october-cam}

De releasedatum voor Cloud Acceleration Manager is 4 oktober 2021.

### Nieuwe functies {#what-is-new-cam}

* Met Cloud Acceleration Manager kunnen gebruikers de BPA-rapporten nu bekijken in een afdrukbaar voorbeeld, zodat ze eenvoudig kunnen afdrukken of afdrukken naar PDF, zodat ze gemakkelijk kunnen worden gedeeld. Verwijs naar Stap 6 en 7 in [Gebruikend de Kaart van de Analyse van Beste praktijken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/cam-readiness-phase.html?lang=en#best-practices-analysis).

## De tool Content Transfer {#content-transfer-tool}

### Releasedatum {#release-date-ctt-latest}

De releasedatum voor Content Transfer Tool v1.6.0 is 4 oktober 2021.

### Wat is er nieuw? {#what-is-new-ctt}

* Verbeterde gebruikerstoewijzing met een vereenvoudigde gebruikerservaring, inclusief de volgende functies die hieronder worden vermeld. Voor meer details, verwijs naar [Gebruikend het Hulpmiddel van de Toewijzing van de Gebruiker](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=en#using-user-mapping-tool).
   * Verbinding met de gebruikersbeheerAPI testen voordat de gebruikerstoewijzing wordt uitgevoerd
   * Fouten op een fraaie manier overslaan en doorgaan met de gebruikerstoewijzingsactiviteit
   * Toewijzing van gebruikers mislukt niet meer als Toegangstoken verloopt (na 24 uur). Toewijzing van gebruikers kan opnieuw worden uitgevoerd vanaf het punt waarop het laatst is gestopt.

* Om de robuustheid te verhogen CTT, kan de inhoud aan of instantie Auteur of Publish tegelijkertijd worden opgenomen.

* Wanneer versies worden opgenomen, wordt het pad `/var/audit` automatisch opgenomen om auditgebeurtenissen te migreren.

## Analysator van best practices {#best-practices-analyzer}

### Releasedatum {#release-date-bpa-latest}

De releasedatum voor de analyse van best practices v2.1.18 is 2021 september.

### Wat is er nieuw? {#what-is-new}

* Mogelijkheid om het totale aantal knooppunten te detecteren en te rapporteren.

* Mogelijkheid om het type en de grootte van de knoopopslag te detecteren en te rapporteren.

### Opgeloste problemen {#bug-fixes-bpa}

* BPA ontdekte ten onrechte de aanwezigheid van een kader voor de integratie van de handel.
