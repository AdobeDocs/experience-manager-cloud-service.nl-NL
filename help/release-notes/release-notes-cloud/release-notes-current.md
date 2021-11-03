---
title: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service.
description: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: ffdd1e306ed24409fd5ef946172d95b1ca5ed7cc
workflow-type: tm+mt
source-wordcount: '1911'
ht-degree: 0%

---


# Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor de huidige (meest recente) versie van [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Vanaf hier kunt u navigeren om notities van eerdere versies weer te geven. bijvoorbeeld voor die in 2020, 2021, enzovoort.

>[!NOTE]
>
>Zie [Recente documentatieupdates](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor meer informatie over documentatie-updates die niet rechtstreeks verband houden met een release.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als [!DNL Cloud Service] De huidige release (2021.9.0) is 6 oktober 2021.
De volgende release (2021.10.0) is op 4 november 2021.

## Video vrijgeven {#release-video}

Kijk eens naar de [Overzicht release september 2021](https://video.tv.adobe.com/v/337381) video voor een overzicht van de toegevoegde functies.

## [!DNL Experience Manager Sites] als [!DNL Cloud Service] {#sites}

### Nieuwe functie in het dialoogvenster [!DNL Sites] prerelease-kanaal {#sites-prerelease-features}

* Inhoudsfragmentmodellen worden nu automatisch ingesteld op de status Alleen-lezen als ze eenmaal zijn gepubliceerd. Zo voorkomt u dat live API-query&#39;s per ongeluk worden afgebroken als een bewerkt model opnieuw wordt gepubliceerd. Gebruikers krijgen een waarschuwing te zien wanneer ze proberen een gepubliceerd model te bewerken. Bewerken is mogelijk bij het accepteren van de waarschuwing.

## [!DNL Experience Manager Assets] als [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#assets-features}

* Annotatie van PDF-bestanden wordt nu ondersteund met native gereedschappen voor opmerkingen en annotaties uit Adobe Document Cloud. Annoteer de PDF-inhoud door tekst, markeringen, notities en tekeningen rechtstreeks in het voorvertoningsvenster van het document toe te voegen. Gebruikers kunnen ook naar interessepagina&#39;s in de PDF springen door op specifieke opmerkingen te klikken

* Gebruikers kunnen de elementen die in de zoekresultaten worden weergegeven nu sorteren in de kolom- en kaartweergave. Het sorteren werkt op de kolommen Naam, Gemaakt, Gewijzigd of Geen.

   ![De zoekresultaten sorteren in [!DNL Assets] in kolom- en kaartweergaven](/help/assets/assets/sort-searched-assets.png)
   *Afbeelding: De zoekresultaten sorteren in [!DNL Assets] in de kolom- en kaartweergave.*

### Nieuwe functie in het dialoogvenster [!DNL Assets] prerelease-kanaal {#assets-prerelease-features}

* [!DNL Assets] bevat nu een ingebouwde aansluiting voor [!DNL Azure Media Services] voor audio- en video-transcriptie. Wanneer gevormd, worden de gesteunde dossiers automatisch getranscripeerd en produceren dossiers WebVTT. De WebVTT-bijschriften worden gebruikt voor een effectievere zoekfunctie, ondertiteling of vertaling voor gebruik als ondertitels.

<!-- TBD: 'Unpublishing' this feature as suggested by engineering.

* To programmatically invoke processing using asset microservices, a new API is introduced. Developers can now apply an existing folder-level processing profile on one or more specific assets in a folder. The processing profile gets applied based on custom metadata properties updates. See `AssetProcessor` in the [[!DNL Experience Manager] API reference](https://www.adobe.io/experience-manager/reference-materials/). As before, it is possible to [use asset microservices from the user interface](/help/assets/asset-microservices-configure-and-use.md).

-->
<!-- Leave this commented.

### New feature in the [!DNL Assets] prerelease channel {#assets-prerelease-features}

Apparently, no new Assets features in Sep prerelease channel.
A/V transcription feature via CQ-4303854 has moved to Oct prerelease now.

### Bugs fixed in [!DNL Assets] {#assets-bugs-fixed}

No customer-reported bugs fixed in Sep release.
CQ-4328183 was not reported on CS so not documented here.
-->

## [!DNL Experience Manager Forms] als [!DNL Cloud Service] {#forms}

### Nieuwe functies in [!DNL Forms] {#what-is-new-forms-sep-2021}

* **Adobe Sign-rollen gebruiken in een adaptief formulier**: Adobe Sign for business and enterprise service levels hebben de mogelijkheid om de rollen voor overeenkomstontvangers uit te breiden, tot buiten alleen de ondertekenaar, zodat ze beter kunnen voldoen aan hun workflowvereisten. U kunt nu [elke ontvanger van de overeenkomst toestaan om zijn rol in een adaptief formulier te configureren](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/create-an-adaptive-form/use-adobe-sign/working-with-adobe-sign.html#addsignerstoanadaptiveform), waarbij Ondertekenaar de standaardrol is.

* **Analyses voor Adaptive Forms**: U kunt nu vastleggen en [eindgebruikersgedrag volgen via Adobe Analytics](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/integrate-aem-forms-with-adobe-analytics.html) voor Adaptive Forms om inzichten van eindgebruikers te verzamelen. Het helpt geïnformeerde beslissingen te nemen op basis van gegevens om de gebruikerservaring te verbeteren.

* **Verbind AEM Forms eenvoudig met Microsoft Dynamics en Salesforce**: De dienst verstrekt uit de doos gegevensbronconfiguratie en gegevensmodellen voor de Dynamica en Salesforce van Microsoft, makend het [ontwikkelaars kunnen Microsoft Dynamics en Salesforce sneller en eenvoudiger configureren als gegevensbronnen voor een adaptief formulier](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/use-form-data-model/configure-msdynamics-salesforce.html?lang=en).

* **Een adaptief formulier elektronisch ondertekenen met DocuSign:** [U kunt DocuSign gebruiken om een adaptief formulier elektronisch te ondertekenen](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/integrate-docusign-adaptive-forms.html). De service biedt een aangepaste verzendactie om DocuSign te gebruiken met een adaptief formulier.

### Bètafuncties van [!DNL Forms] {#sep-what-is-new-forms-prerelease}

* **Unified Storage-connector:** Gebruik Unified Storage Connector om procesgegevens in door de klant beheerde opslagruimten extern te maken. Bijvoorbeeld, kunt u in-proces AEM de gegevens van Werkstromen (AEM gegevens van de Variabelen van het Werkschema) opslaan die Gevoelige Persoonlijke Gegevens (SPD) in een klant-beheerde bewaarplaats bevatten.

   <!--* Enable Forms Portal’s save and resume functionality and store adaptive forms drafts in a customer-managed data repository.-->

* **[!DNL AEM Forms as a Cloud Service - Communications]**: [Communicatie-API&#39;s](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/aem-forms-cloud-service-communications.html?lang=en) Hiermee kunt u XDP-sjablonen en XML-gegevens combineren om afdrukdocumenten in verschillende indelingen te genereren. Met deze service kunt u documenten genereren in synchrone modus. Met de API&#39;s kunt u toepassingen maken waarmee u:
   * Genereer documenten door sjabloonbestanden te vullen met XML-gegevens.
   * Uitvoerformulieren genereren in verschillende indelingen, waaronder niet-interactieve PDF-afdrukstromen.
   * Afdruk-PDF-bestanden genereren op basis van een XFA-formulier met PDF en Adobe Acrobat-formulier.

U kunt schrijven naar [!DNL formscsbeta@adobe.com] om u aan te melden voor het bètaprogramma.

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

## [!DNL Experience Manager Screens] als [!DNL Cloud Service] {#screens}

### Nieuwe functies {#what-is-new-screens}

* as a Cloud Service schermen ondersteunen nu elementaire afspeelcontrole. De speler zal nu diverse playbackmetriek met elk melden pingelt (gebrek aan 30 seconden). Op basis van de meetgegevens kunnen verschillende randgevallen worden gedetecteerd (geplakte ervaring, leeg scherm, planningsprobleem, enz.). Met deze functie kan het team op afstand controleren of een speler inhoud correct afspeelt, de reactiviteit verbetert tot lege schermen of gebroken ervaringen in het veld en het risico dat de eindgebruiker een verbroken ervaring krijgt verkleind.
Zie [Standaardafspeelcontrole](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/manage-player-registration/installing-screens-cloud-player.html?lang=en#playback-monitoring) voor meer informatie .

* Ondersteuning van miniaturen voor video&#39;s wordt nu ondersteund in as a Cloud Service schermen. Een inhoudauteur kan een duimnagel voor video&#39;s bepalen zodat het beeld als placeholder kan worden gebruikt en behoorlijk het playback en richten van inhoud testen, terwijl de daadwerkelijke video door het aangewezen team wordt gebeëindigd. De afbeelding kan ook worden gebruikt voor het geval dat het afspelen van de video mislukt.
Zie [Ondersteuning van miniaturen voor video&#39;s](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/core-product-features/thumbnail-support-videos.html) voor meer informatie .

### Opgeloste problemen {#bug-fixes-screens}

* De speler kan de inhoud van de ingesloten pagina niet weergeven en dit probleem is nu opgelost.

* Na een geslaagde aanmelding werd het navigeren naar de standaardpagina (kanalen) beëindigd op een pagina Interne serverfout.

* Gekoppelde tagitems zijn niet verwijderd tijdens het verwijderen van afspeellijsten.

## [!DNL Experience Manager as a Cloud Service] Stichting {#foundation}

### Nieuwe functies in [!DNL Experience Manager as a Cloud Service] {#foundation-features}

**Geavanceerde netwerken**

[!DNL Adobe Experience Manager] als [!DNL Cloud Service] biedt nu diverse soorten geavanceerde voorzien van een netwerkmogelijkheden aan, die omvatten:

* Flexibele uitgang van de Haven om verkeer uit niet-standaardhavens te ontspannen. Dit is nu mogelijk zonder contact op te nemen met de Adobe Support.
* Het specifieke IP adres van de uitgang om verkeer uit AEM as a Cloud Service van unieke IP te ontslaan, nu ondersteunend alle havens.
* VPN om verkeer tussen uw infrastructuur en AEM as a Cloud Service te beveiligen.

Lees de [documentatie](/help/security/configuring-advanced-networking.md) voor meer informatie, zoals hoe u zelf geavanceerde netwerkvoorzieningen aanbiedt met gebruik van API&#39;s van Cloud Manager.

**Indexoptimalisatie**

Om de prestaties van onderzoeksvragen en het indexeren te verbeteren, wordt full-text index lucene-2 niet meer gebruikt buiten-van-de-doos binnen [!DNL Adobe Experience Manager] als [!DNL Cloud Service] uit deze release. Om deze full-text index over AEM milieu&#39;s in overeenstemming met AEM klanten te verwijderen, werkt de Techniek van Adobe individueel en pro-actief met klanten voor een zachte en duurzame verwijdering van Lucene full-text index. Ga naar [!DNL Adobe Experience Manager] als [!DNL Cloud Service] [documentatie](/help/operations/indexing.md#index-optimizations) voor meer informatie en neem direct contact op met onze ondersteuning als u vragen hebt.

## Cloud Manager {#cloud-manager}

In deze sectie worden de opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service 2021.10.0 en 2021.9.0 beschreven.

## Releasedatum {#release-date-cm-oct}

De releasedatum voor Cloud Manager in AEM as a Cloud Service 2021.10.0 is 14 oktober 2021.
De volgende release is gepland voor 4 november 2021.

### Wat is er nieuw? {#what-is-new-cm-oct}

* Ter voorbereiding op enkele aanstaande wijzigingen wordt nu in de gebruikersinterface verwezen naar en geëtiketteerd als bestaande implementatiepijplijnen **Volledige stapel** pijpleidingen.

* De kaart van de pijpleiding is verfrist om één enkel, geïntegreerd gezicht te tonen dat zowel productie als niet productiepijpleidingen toont, en de gebruiker kan Looppas/pauze direct selecteren/hervat van het actiemenu verbonden aan elke pijpleiding.

* Een gebruiker in de rol van de Manager van de Plaatsing kan de pijpleiding van de Productie op een zelfbediening manier via UI nu schrappen.

* De ervaring met toevoegen en bewerken van pijpleidingen is vernieuwd en gebruikt nu vertrouwde, moderne modellen.

* Gebruikers van Cloud Manager kunnen nu rechtstreeks vanuit de gebruikersinterface feedback verzenden via de **Feedback** op de rechterbovenhoek van de landingspagina.

* De jaarlijkse SLA-grafieken kunnen nu worden gedownload vanuit de gebruikersinterface van Cloud Manager.

* De kwaliteit van de code en de niet-productiepijpleiding zullen nu een efficiënter oppervlakkig klonen proces tijdens de bouwstijlstap gebruiken, die tot een snellere bouwtijd voor klanten met bijzonder grote git bewaarplaatsen leidt.

* Voeg IP de tovenaar van de Lijst van gewenste personen nu toe zal de gebruiker informeren als maximum toegestaan aantal IP Lijsten van gewenste personen is bereikt.

* De documentatie van de API voor Cloud Manager bevat nu een interactieve speelruimte waarmee aangemelde gebruikers vanuit hun browser kunnen experimenteren met de API. Zie [Afspelen van Cloud Manager-API](https://www.adobe.io/experience-cloud/cloud-manager/reference/playground/) voor meer informatie .

* De knopinfo op de programmakaart is beschrijfbaarder als een selectieoptie onder &#39;Navigeren naar&#39; is uitgeschakeld. Het toont nu &quot;een productiemilieu bestaat niet.&quot;

## Releasedatum {#release-date-cm-sept}

De releasedatum voor Cloud Manager in AEM as a Cloud Service 2021.9.0 is 9 september 2021.

### Opgeloste problemen {#bug-fixes-cm-oct}

* In zeldzame situaties, wanneer een personeel van Adobe de omgeving van een klant zou herstellen, werd het herstel als volledig beschouwd alvorens het milieu volledig operationeel was.

* Bepaalde interne verzoeken die tijdens het creëren van het milieu werden gedaan, werden niet opnieuw beproefd.

* Als de plaatsing mislukte fout na de controle van de domeinnaam voorkomt, is het foutenbericht verbeterd om de klant te verzoeken om hun vertegenwoordiger van de Adobe te contacteren.


### Wat is er nieuw? {#what-is-new-cm-sept}

* De versie van het AEM Projectarchetype dat door de Manager van de Wolk wordt gebruikt is bijgewerkt aan versie 30.

* De programmakaarten op de landingspagina van Cloud Manager en de bijbehorende ervaring zijn vernieuwd.

* Het logbestand met stappen voor codekwaliteit bevat nu uitgebreide logboekgegevens over het OakPal-scanproces.

* De opties in het menu Activiteit pagina bevatten nu een optie voor **Logbestand downloaden** voor voltooide uitvoering van de Code Generator. Als u deze optie selecteert, wordt het logboek met de stap build gedownload.

* Als u rechtstreeks op de programmakaart klikt, gaat u nu naar de overzichtspagina van Cloud Manager.

### Opgeloste problemen {#bug-fixes-sept}

* De gebruiker zal nu een begrijpelijker bericht wanneer het proberen om een nieuwe IP Lijst van gewenste personen in een programma toe te voegen dat het maximum toegestane aantal IP Lijsten van gewenste personen heeft bereikt die kunnen worden gevormd.

* Er is een onjuiste URL gekopieerd bij het selecteren van de menuoptie URL kopiëren in het scherm Opslagplaatsen.

## Cloud Acceleration Manager {#cam}

### Releasedatum {#release-date-october-cam}

De releasedatum voor Cloud Acceleration Manager is 4 oktober 2021.

### Nieuwe functies {#what-is-new-cam}

* Met Cloud Acceleration Manager kunnen gebruikers de BPA-rapporten nu bekijken in een afdrukbaar voorbeeld, zodat ze eenvoudig kunnen afdrukken of afdrukken naar PDF, zodat ze gemakkelijk kunnen worden gedeeld. Zie Stap 6 en 7 in [De kaart van de Analyse van Beste praktijken gebruiken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/cam-readiness-phase.html?lang=en#best-practices-analysis).

## De tool Content Transfer {#content-transfer-tool}

### Releasedatum {#release-date-ctt-latest}

De releasedatum voor Content Transfer Tool v1.6.0 is 4 oktober 2021.

### Wat is er nieuw? {#what-is-new-ctt}

* Verbeterd gereedschap voor het toewijzen van gebruikers met een vereenvoudigde gebruikerservaring, inclusief de volgende functies die hieronder worden vermeld. Raadpleeg voor meer informatie [Gebruikerstoewijzing gebruiken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/user-mapping-tool/using-user-mapping-tool.html).
   * Verbinding met de gebruikersbeheerAPI testen voordat de gebruikerstoewijzing wordt uitgevoerd
   * Fouten op een fraaie manier overslaan en doorgaan met de gebruikerstoewijzingsactiviteit
   * Toewijzing van gebruiker mislukt niet meer als **Toegangstoken** verloopt na 24 uur. Toewijzing van gebruikers kan opnieuw worden uitgevoerd vanaf het punt waarop het laatst is gestopt.

* Om de robuustheid van het hulpmiddel van de Overdracht van de Inhoud te verhogen, kan de inhoud aan of instantie Auteur of Publish tegelijkertijd worden opgenomen. Zie [Aan de slag met het gereedschap Inhoud overbrengen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=en) voor meer informatie .

* Wanneer versies worden opgenomen, wordt het pad `/var/audit` wordt automatisch opgenomen om auditgebeurtenissen te migreren.

## Analysator van best practices {#best-practices-analyzer}

### Releasedatum {#release-date-bpa-latest}

De releasedatum voor de analyse van best practices v2.1.20 is 5 oktober 2021.

### Wat is er nieuw? {#what-is-new}

* Mogelijkheid om de lengte van knoopnamen te detecteren en te rapporteren.

* Mogelijkheid om de totale indexgrootte op te sporen en te rapporteren.

* Mogelijkheid om elementen te detecteren en te rapporteren waarvoor de oorspronkelijke uitvoering ontbreekt.

