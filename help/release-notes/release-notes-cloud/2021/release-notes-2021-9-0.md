---
title: Nota's van de versie voor 2021.9.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Nota's van de versie voor 2021.9.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: 8c12ff09-fbc8-42dd-87c0-46e509604f36
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1519'
ht-degree: 0%

---

# Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor de huidige (meest recente) versie van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>
>Vanaf hier kunt u navigeren om notities van eerdere versies vrij te geven, bijvoorbeeld voor de versies in 2020 en 2021.

>[!NOTE]
>
>Zie [ Recente Updates van de Documentatie ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor details van documentatieupdates niet direct met een versie verwant.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige release (2021.9.0) is 6 oktober 2021.
De volgende release (2021.10.0) is op 4 november 2021.

## Video vrijgeven {#release-video}

Heb een blik bij de ](https://video.tv.adobe.com/v/337381) video van het Overzicht van de Versie 0} September 2021 {voor een samenvatting van de toegevoegde eigenschappen.[

## [!DNL Experience Manager Sites] als een [!DNL Cloud Service] {#sites}

### Nieuwe functie in het [!DNL Sites] prereleasekanaal {#sites-prerelease-features}

* Inhoudsfragmentmodellen worden nu automatisch ingesteld op een alleen-lezen status nadat ze zijn gepubliceerd, om te voorkomen dat live API-query&#39;s per ongeluk worden onderbroken nadat een bewerkt model opnieuw is gepubliceerd. Gebruikers krijgen een waarschuwing te zien wanneer ze proberen een gepubliceerd model te bewerken. Bewerken is mogelijk bij het accepteren van de waarschuwing.

## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#assets-features}

* Gebruikers kunnen de elementen die in de zoekresultaten worden weergegeven nu sorteren in de kolom- en kaartweergave. Het sorteren werkt op de kolommen Naam, Gemaakt, Gewijzigd of Geen.

  ![ Soort de onderzoeksresultaten in [!DNL Assets] in Kolom en de meningen van de Kaart ](/help/assets/assets/sort-searched-assets.png)
  *Cijfer: Soort de onderzoeksresultaten in [!DNL Assets] in de meningen van de Kolom en van de Kaart.*

* Voor het programmatisch aanroepen van verwerking met behulp van asset microservices wordt een nieuwe API geïntroduceerd. Ontwikkelaars kunnen nu een bestaand verwerkingsprofiel op mapniveau toepassen op een of meer specifieke elementen in een map. Het verwerkingsprofiel wordt toegepast op basis van aangepaste updates van eigenschappen van metagegevens. Zie `AssetProcessor` in de [[!DNL Experience Manager]  API verwijzing ](https://developer.adobe.com/experience-manager/reference-materials/). Zoals voordien, is het mogelijk aan [ gebruik activa microservices van het gebruikersinterface ](/help/assets/asset-microservices-configure-and-use.md).

<!-- Leave this commented.

### New feature in the [!DNL Assets] prerelease channel {#assets-prerelease-features}

Apparently, no new Assets features in Sep beta channel.
A/V transcription feature by way of CQ-4303854 has moved to Oct beta now.

### Bugs fixed in [!DNL Assets] {#assets-bugs-fixed}

No customer-reported bugs fixed in Sep release.
CQ-4328183 was not reported on CS so not documented here.
-->

## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

### Nieuwe functies in [!DNL Forms] {#what-is-new-forms-sep-2021}

* **de rollen van Adobe Sign van het Gebruik in een Aangepaste Vorm** - Adobe Sign voor zaken en ondernemingsde dienstniveaus laten u naar keuze de rollen voor de ontvangers van de Overeenkomst, voorbij enkel de Ondertekenaar uitbreiden, om hun werkschemavereisten beter aan te passen. U kunt [ elke ontvanger van de overeenkomst nu toelaten om hun rol in een Aangepaste Vorm ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/use-adobe-sign/working-with-adobe-sign.html#addsignerstoanadaptiveform) te vormen, met Ondertekenaar die de standaardrol is.

* **Analytics voor Aanpassings Forms** - u kunt eindgebruikergedrag nu vangen en volgen als Adobe Analytics voor Aanpassings Forms om eindgebruikerinzicht te verzamelen. Het helpt geïnformeerde beslissingen te nemen op basis van gegevens om de gebruikerservaring te verbeteren.

* **verbindt gemakkelijk Adobe Experience Manager (AEM) Forms met de Dynamiek Microsoft® en Salesforce** - de dienst verstrekt out-of-the-box gegevensbronconfiguratie en gegevensmodellen voor de Dynamica en Salesforce van Microsoft®. Dit maakt het [ sneller en gemakkelijker voor ontwikkelaars om de Dynamica en Salesforce van Microsoft® als gegevensbronnen voor een adaptieve vorm ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/configure-msdynamics-salesforce.html) te vormen.

* **e-Onderteken een adaptieve vorm gebruikend DocuSign** - U kunt DocuSign gebruiken om een adaptieve vorm elektronisch te ondertekenen. De service biedt een aangepaste verzendactie om DocuSign te gebruiken met een adaptief formulier. U kunt het pakket dat beschikbaar is op Softwaredistributie installeren om de verzendactie te importeren.

### Beta-functies van [!DNL Forms] {#sep-what-is-new-forms-prerelease}

* **Verenigde Schakelaar van de Opslag** - Gebruik Verenigde Schakelaar van de Opslag om in-procesgegevens in klant-beheerde bewaarplaatsen extern te maken. U kunt bijvoorbeeld
   * Schakel de functie Opslaan en hervatten van Forms Portal in en sla adaptieve formulierconcepten op in een gegevensopslagruimte onder beheer van de klant.
   * Sla AEM werkstroomgegevens (AEM gegevens van de Variabelen van het Werkschema) op die Gevoelige Persoonlijke Gegevens (SPD) in een klant-beheerde bewaarplaats bevatten.

* **[!DNL AEM Forms as a Cloud Service - Communications]** - [ Communicatie APIs ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications.html) hulp u XDP malplaatjes en de gegevens van XML combineert om drukdocumenten in diverse formaten te produceren. Met de service kunt u documenten in synchrone modus genereren. Met de API&#39;s kunt u toepassingen maken waarmee u:
   * Genereer documenten door sjabloonbestanden te vullen met XML-gegevens.
   * Uitvoerformulieren genereren in verschillende indelingen, waaronder niet-interactieve PDF-afdrukstromen.
   * Afdruk-PDF-bestanden genereren op basis van een XFA-formulier met PDF en Adobe Acrobat-formulier.

U kunt schrijven naar [!DNL formscsbeta@adobe.com] om u aan te melden voor het bètaprogramma.

## CIF invoegtoepassing {#cloud-services-cif}

### Nieuwe functies {#what-is-new-cif}

* Het nieuwe tabblad &quot;Associated commerce content&quot; in de AEM Sites Editor verhoogt de efficiëntie van de auteur door snel toegang te krijgen tot relevante AEM productinhoud voor de huidige context

  ![ Verwante handelsinhoud ](/help/assets/CIF/associated-commerce-content.png)

* Verbeterde gebruikersinterface van de productkiezer voor een betere gebruikerservaring, verbeterde efficiëntie en ondersteuning voor complexe productcatalogus

  ![ Nieuwe Plukker van het Product ](/help/assets/CIF/product-picker.png)

* Eigenschap &quot;include_in_menu&quot; in navigatiecomponent respecteren

### Opgeloste problemen {#bug-fixes-cif}

* Het leegmaken van de menucache werkt niet zoals verwacht

* JS-fouten tijdens de implementatiestap AEM CS en wanneer geen clientcomponenten worden gebruikt

* Kan CIF wolkenconfiguratie in omslagen tot stand brengen die een helling hebben:vormt knoop

## [!DNL Experience Manager Screens] als een [!DNL Cloud Service] {#screens}

### Nieuwe functies {#what-is-new-screens}

* Screens as a Cloud Service ondersteunt nu elementaire afspeelcontrole. De speler rapporteert nu verschillende playbackmetriek met elk pingelt (gebrek aan 30 seconden). Op basis van de meetgegevens kunnen er verschillende randgevallen worden gedetecteerd (geplakte ervaring, leeg scherm, planningsprobleem, enzovoort). Met deze functie kan het team op afstand controleren of een speler inhoud correct afspeelt. Het verbetert de reactiviteit aan lege schermen of gebroken ervaringen op het gebied, en vermindert het risico om een gebroken ervaring aan de gebruiker te tonen.
Zie [ Basis Controle van de Playback ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/screens-as-cloud-service/manage-player-registration/installing-screens-cloud-player.html#playback-monitoring) voor meer details.

* Ondersteuning voor miniaturen voor video&#39;s die nu worden ondersteund in Screens as a Cloud Service. Een inhoudauteur kan een duimnagel voor video&#39;s bepalen zodat het beeld als placeholder wordt gebruikt en behoorlijk het playback en richten van inhoud test, terwijl de daadwerkelijke video door het aangewezen team wordt voltooid. De afbeelding kan ook worden gebruikt als het afspelen van de video mislukt.
Zie [ Steun van de Duimnagel voor Video&#39;s ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/screens-as-cloud-service/core-product-features/thumbnail-support-videos.html) voor meer details.

### Opgeloste problemen {#bug-fixes-screens}

* De speler kan de inhoud van de ingesloten pagina niet weergeven. Het probleem is nu opgelost.

* Na een geslaagde aanmelding werd het navigeren naar de standaardpagina (kanalen) beëindigd op een pagina Interne serverfout.

* Gekoppelde tagitems zijn niet verwijderd tijdens het verwijderen van afspeellijsten.

## [!DNL Experience Manager as a Cloud Service] Foundation {#foundation}

### Nieuwe functies in [!DNL Experience Manager as a Cloud Service] {#foundation-features}

**Geavanceerde Voorzien van een netwerk**

>[!INFO]
>
>De geavanceerde voorzien van een netwerkeigenschap maakt deel uit van de versie 2021.9.0, en werd toegelaten voor klanten medio oktober 2021.

[!DNL Adobe Experience Manager] als [!DNL Cloud Service] biedt nu diverse soorten geavanceerde netwerkmogelijkheden, waaronder:

* Flexibele uitgang van de Haven om verkeer uit niet-standaardhavens te ontspannen. Dit is nu mogelijk zonder contact op te nemen met de Adobe Support.
* Het specifieke IP adres van de uitgang om verkeer uit AEM as a Cloud Service van unieke IP te egress, nu ondersteunend alle havens.
* VPN om verkeer tussen uw infrastructuur en AEM as a Cloud Service te beveiligen.

Lees de [ documentatie ](/help/security/configuring-advanced-networking.md) voor meer informatie, met inbegrip van hoe te voorziening geavanceerd voorzien van een netwerk te dienen gebruikend Cloud Manager APIs.

**de Optimalisaties van de Index**

Om de prestaties van onderzoeksvragen en het indexeren te verbeteren, wordt full-text index lucene-2 niet meer gebruikt uit-van-de-doos in [!DNL Adobe Experience Manager] als [!DNL Cloud Service] van deze versie. Om deze full-text index op AEM milieu&#39;s in overeenstemming met AEM klanten te verwijderen, werkt de Techniek van de Adobe individueel en pro-actief met klanten voor een zachte en duurzame verwijdering van de full-text index van Lucene. Bezoek [!DNL Adobe Experience Manager] als a [!DNL Cloud Service] [ documentatie ](/help/operations/indexing.md#index-optimizations) voor meer informatie en de steun van de contactAdobe direct als u vragen hebt.

## Cloud Manager {#cloud-manager}

In deze sectie worden de opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service 2021.9.0 en 2021.8.0 beschreven.

## Releasedatum {#release-date-cm-sept}

De releasedatum voor Cloud Manager in AEM as a Cloud Service 2021.9.0 is 9 september 2021.
De volgende release is gepland voor 7 oktober 2021.

### Wat is er nieuw? {#what-is-new-cm-sept}

* De versie van het AEM Project Archetype dat door Cloud Manager wordt gebruikt, is bijgewerkt naar versie 30.

* De programmakaarten op de landingspagina van Cloud Manager en de bijbehorende ervaring zijn vernieuwd.

* Het logbestand met stappen voor codekwaliteit bevat nu uitgebreide logboekgegevens over het OakPal-scanproces.

* De opties van het het paginamenu van de Activiteit omvatten nu een optie aan **Logboek van de Download** voor voltooide uitvoeren van de Generator van de Code. Als u deze optie selecteert, wordt het logboek van de stap build gedownload.

* Als u rechtstreeks op de programmakaart klikt, gaat u nu naar de pagina Cloud Manager Overview (Overzicht van).

### Opgeloste problemen {#bug-fixes-sept}

* De gebruikers zien nu een begrijpelijker bericht wanneer het proberen om een IP lijst van gewenste personen in een programma toe te voegen dat het maximum toegestane aantal IP lijsten van gewenste personen heeft bereikt die kunnen worden gevormd.

* De onjuiste URL is gekopieerd wanneer u de menuoptie URL kopiëren in het scherm Opslagplaatsen selecteert.

## Cloud Acceleration Manager {#cam}

### Releasedatum {#release-date-october-cam}

De Releasedatum voor Cloud Acceleration Manager is 4 oktober 2021.

### Nieuwe functies {#what-is-new-cam}

* Cloud Acceleration Manager biedt gebruikers nu de mogelijkheid om de BPA-rapporten in een afdrukbare voorvertoning weer te geven, zodat eenvoudig kan worden afgedrukt of afgedrukt naar PDF, zodat u ze gemakkelijk kunt delen. Zie Stap 6 en 7 in [ Gebruikend de Kaart van de Analyse van Beste praktijken ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-acceleration-manager/using-cam/cam-readiness-phase.html#best-practices-analysis).

## Inhoud overbrengen {#content-transfer-tool}

### Releasedatum {#release-date-ctt-latest}

De releasedatum voor Content Transfer Tool v1.6.0 is 4 oktober 2021.

### Wat is er nieuw? {#what-is-new-ctt}

* Verbeterde gebruikerstoewijzing met een vereenvoudigde gebruikerservaring, inclusief de volgende functies die hieronder worden vermeld. Voor meer details, zie [ Gebruikend het Hulpmiddel van de Toewijzing van de Gebruiker ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/legacy-user-mapping-tool/using-user-mapping-tool-legacy.html#using-user-mapping-tool).
   * Verbinding met de gebruikersbeheerAPI testen voordat de gebruikerstoewijzing wordt uitgevoerd
   * Fouten op een fraaie manier overslaan en doorgaan met de gebruikerstoewijzingsactiviteit
   * De Toewijzing van de gebruiker ontbreekt niet meer als het Token van de Toegang (na 24 uren) verloopt. Toewijzing van gebruikers kan opnieuw worden uitgevoerd vanaf het punt waar de gebruikerstoewijzing het laatst is gestopt.

* Om de CTT robuustheid te verhogen, kan de inhoud aan of instantie Auteur of instantie Publish tegelijkertijd worden opgenomen.

* Wanneer versies worden opgenomen, wordt het pad `/var/audit` automatisch opgenomen om auditgebeurtenissen te migreren.

## Analysator van best practices {#best-practices-analyzer}

### Releasedatum {#release-date-bpa-latest}

De releasedatum voor de analyse van best practices v2.1.18 is 2021 september.

### Wat is er nieuw? {#what-is-new}

* Mogelijkheid om het totale aantal knooppunten te detecteren en te rapporteren.

* Mogelijkheid om het type en de grootte van de knoopopslag te detecteren en te rapporteren.

### Opgeloste problemen {#bug-fixes-bpa}

* BPA detecteerde ten onrechte de aanwezigheid van Commerce integration framework.
