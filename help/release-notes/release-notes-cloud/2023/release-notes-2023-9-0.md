---
title: Nota's van de versie voor 2023.9.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Nota's van de versie voor 2023.9.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: d747f58b-8d6c-418d-9d2b-ec3ae4b6dc03
feature: Release Information
role: Admin
source-git-commit: bb149cd43158bfd1ceb43b04cc536c8c8291f968
workflow-type: tm+mt
source-wordcount: '1440'
ht-degree: 0%

---


# Opmerkingen bij de release 2023.9.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de versie 2023.9.0 van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van eerdere versies, zoals 2021 of 2022, vrij te geven.
>
>Heb een blik bij [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html) vrij om over de aanstaande eigenschapactivering voor [!DNL Experience Manager] as a Cloud Service te leren.

>[!NOTE]
>
>Zie [ Recente Updates van de Documentatie ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor details van documentatieupdates niet direct met een versie verwant.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige release met functies (2023.9.0) is 28 september 2023. De volgende release met functies (2023.10.0) is gepland voor 26 oktober 2023.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U kunt de recentste nota&#39;s van de onderhoudsversie [ hier ](/help/release-notes/maintenance/latest.md) vinden.

## Video vrijgeven {#release-video}

Bekijk de video Overzicht van de release van september 2023 voor een overzicht van de functies die zijn toegevoegd in de release van 2023.9.0:

>[!VIDEO](https://video.tv.adobe.com/v/3424826/?quality=12)

## AEM Edge Delivery Services {#edge-delivery}

Edge Delivery is een nieuwe reeks composable diensten die zich op het maximaliseren van het effect van inhoud concentreert om meetbare bedrijfsresultaten op het punt van klanteninteractie te drijven.

Leer meer over Edge Delivery Services in het artikel [ hier ](/help/edge/overview.md).

## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Nieuwe functies in de Assets-weergave {#assets-view-features}

**wijs meta-gegevensvorm aan een omslag** toe

U kunt nu een metagegevensformulier toewijzen aan een specifieke map binnen uw implementatie. Alle elementen in de map, inclusief de elementen in de submappen, geven vervolgens de eigenschappen weer die in het toegewezen metagegevensformulier zijn gedefinieerd.

![ wijs meta-gegevensvorm aan een omslag ](/help/release-notes/assets/assign-to-folder.png) toe

### Nieuwe functies in de beheerweergave {#admin-view-features}

* **integreer AEM Assets as a Cloud Service met op document-gebaseerde Authoring voor Edge Delivery Services**: Integreer AEM Assets met op document-gebaseerde Authoring voor Edge Delivery Services om websiteauteurs toe te laten om [ beelden beschikbaar in de bewaarplaatsen van AEM Assets te gebruiken terwijl het ontwerpen van documenten in Microsoft Word of Google Docs ](/help/edge/overview.md).

* **de archieven van het ZIP van het Extraheren**: Mogelijkheid om de archieven van het ZIP te selecteren die in Experience Manager worden beheerd en [ die de dossiers direct in Experience Manager ](/help/assets/manage-digital-assets.md#extract-zip-archives) halen zonder hen te downloaden.

  ![ Vastzetten punten voor groepen ](/help/release-notes/assets/extract-archive.png)

### Functies voor pre-release beschikbaar in [!DNL Experience Manager Assets] {#prerelease-features-assets}

* **Dynamische Media**: [ Multi-caption en multi-audiospoorsteun voor video&#39;s in Dynamische Media ](/help/assets/dynamic-media/video.md#about-msma) - u kunt veelvoudige titels en veelvoudige audiosporen aan een primaire video nu gemakkelijk toevoegen. Dit betekent dat uw video&#39;s toegankelijk zijn voor een breed publiek. U kunt één gepubliceerde primaire video aanpassen aan een wereldwijd publiek in meerdere talen en de richtlijnen voor toegankelijkheid voor verschillende geografische regio&#39;s naleven. Auteurs kunnen de bijschriften en audiotracks ook beheren vanaf één tabblad in de gebruikersinterface.

  ![ Bijschriften en Audiosporen tabel op de pagina van Eigenschappen van een geselecteerd videoelement.](/help/release-notes/assets/msma-aem-cs.png)*Bijschriften en Audiosporen lusje op de pagina van Eigenschappen van geselecteerde videoactiva.*

## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

### Nieuwe functies in [!DNL Experience Manager Forms] {#forms-features}

* [**Google reCAPTCHA ondernemingssteun**](/help/forms/captcha-adaptive-forms-core-components.md): De Onderneming van Google reCAPTCHA in een AanpassingsVorm gebruiken om betere bescherming tegen frauduleuze activiteit en spam te verstrekken, die een veiliger gebruikerservaring verstrekken. Met een geavanceerde risicoanalyse en naadloze integratie kunnen echte gebruikers eenvoudig formulieren indienen terwijl de bots effectief worden geblokkeerd.

* [**Adobe Analytics met de Automatisering van de Opstelling van Experience Cloud voor Forms**](/help/forms/enable-adobe-analytics-adaptive-form-using-experience-cloud-setup-automation.md): U kunt Adobe Analytics met de Automatisering van de Opstelling van Experience Cloud met een omdraaiing van twee knopen nu toelaten. Hiermee kunt u AEM Forms as a Cloud Service verbinden met Experience Platform-tags en Adobe Analytics om prestatiegegevens voor gepubliceerde formulieren vast te leggen en bij te houden.

  >[!VIDEO](https://video.tv.adobe.com/v/3424577/enable-adobe-analytics/?quality=12&learn=on)

* [**het rapportmalplaatje van Adobe Analytics voor Adaptieve Forms**](/help/forms/view-understand-aem-forms-analytics-reports.md): Forms as a Cloud Service verstrekt nu een Adobe Analytics rapport OOTB. Zo kunt u gemakkelijk de prestaties van uw formulieren begrijpen. Met de maatstaven op formulierniveau kunt u een insight laten zien hoe het formulier presteert op meerdere prestatie-indicatoren (KPI&#39;s), zoals uitvoeringen, bezoekers, verzendingen, gemiddelde vultijd. Door gebruikersgedrag en feedback te volgen, kunt u delen van het formulier identificeren die verwarring veroorzaken en verbeteringen aanbrengen in het ontwerp en de functionaliteit van het formulier.

  ![ het adaptieve rapport van de de analysegegevens van de vormenbetrokkenheid van de gebruiker ](/help/forms/assets/forms-analytics-report.png)

* **[Fragment van de Vorm in Aangepast Forms dat op de Componenten van de Kern](/help/forms/adaptive-form-fragments-core-components.md)** wordt gebaseerd: Zeg afscheid aan duplicatie, optimaliseer uw digitale inventaris, en verbeter samenwerking aangezien u uw vorm-bouwende ervaring met de Fragmenten van de Vorm opheft. Deze herbruikbare componenten integreren naadloos in meerdere formulieren, waardoor het maken van consistente en professioneel ogende formulieren wordt gestroomlijnd. Formulierfragmenten zorgen voor herbruikbaarheid, standaardisering en consistentie van merken via de functie &#39;Eenmaal wijzigen en overal weerspiegelen&#39;. Ervaar meer onderhoudsgemak en efficiëntie, aangezien updates die op één plaats worden gemaakt, automatisch worden verspreid over alle vormen die deze fragmenten gebruiken.

* **[Verbeterde stap van het Werkschema van het Ondertekenen van Adobe](/help/forms/aem-forms-workflow-step-reference.md#sign-document-step-sign-document-step)**: De stap van het Werkschema van het Ondertekenen van Adobe wordt verbeterd om het volgende te omvatten:
   * **op identiteitskaart-Gebaseerde Authentificatie van de Regering voor het Teken van Adobe**: De Op identiteitskaart-Gebaseerde Authentificatie van de Regering van Adobe Acrobat Sign biedt een extra laag van controle door gebruikers toe te laten om hun identiteit voor authentiek te verklaren gebruikend overheids-uitgegeven IDs (rijbewijs, nationale identiteitskaart, paspoort). Door vertrouwde identificatiedocumenten te gebruiken, voegt deze verbetering een extra niveau van vertrouwen aan het ondertekeningsproces toe, die het ideaal maakt voor scenario&#39;s die verhoogde veiligheid, naleving, en gebruikersbevestiging vereisen.

   * **Spoor van de Controle voor de Documenten van het Teken van Adobe**: Gebruik de eigenschap van het Spoor van de Controle voor gedetailleerde inzichten in de levenscyclus van uw documenten van het Teken van Adobe. Met het audittrail, kunt u een uitvoerig verslag van alle acties en interactie handhaven met betrekking tot uw documenten. Dit omvat gegevens zoals wie het document heeft bekeken, bewerkt of ondertekend, samen met tijdstempels voor elke gebeurtenis. Deze verbetering is van cruciaal belang voor het handhaven van de naleving, het oplossen van geschillen en het verzekeren van de integriteit van uw digitale overeenkomsten.

   * **Nieuwe rollen voor de ontvangers van de Overeenkomst voorbij enkel de Ondertekenaar**: Adobe Acrobat Sign heeft de optie om de rollen voor de ontvangers van de Overeenkomst voorbij enkel de Ondertekenaar uit te breiden om hun werkschemavereisten beter aan te passen. Wanneer toegelaten, heeft elke ontvanger in een Overeenkomst zijn rol individueel configureerbaar, met Ondertekenaar die het gebrek is.

* **de Steun van de Telling van de Pagina in Communicatie APIs**: Nu, samen met het terugwinnen van uw document door Communicatie APIs, kunt u de waardevolle informatie over het aantal pagina&#39;s ook ontvangen bevat binnen het document.

* **[Fout die met de managers van de douanefout in regelredacteur](/help/forms/add-custom-error-handler-adaptive-forms-core-components.md)** behandelt: U kunt een douanefunctie nu aanhalen als antwoord op een fout door de externe dienst is teruggekeerd en een op maat gemaakte reactie aan eind - gebruikers verstrekken. Bijvoorbeeld, kunt u een douanewerkschema in de achtergrond voor specifieke foutencodes aanhalen of de klant informeren dat de dienst neer is.

* **[met 64 bits Versie van AEM Forms Designer](/help/forms/installing-configuring-designer.md)**: De met 64 bits versie van AEM Forms Designer brengt verbeterde prestaties, scalability, en geheugenbeheer om uw ervaring van de vormverwezenlijking te versterken. Met de 64-bits architectuur kunt u nog grotere en complexere projecten eenvoudig aanpakken, zodat u kunt zorgen voor naadloze ontwerpworkflows en geoptimaliseerde efficiëntie. Verhoog uw mogelijkheden voor formulierontwerp en omarm de toekomst van AEM Forms Designer met deze baanbrekende release.

### Programma voor vroegtijdige adoptie {#forms-early-adopter}

* **[bescherm uw documenten met DocAssurance APIs (Deel van Communicatie APIs)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: De DocAssurance APIs machtigt u om gevoelige informatie te beschermen door de documenten te ondertekenen en te coderen. Door versleuteling wordt de inhoud van een document omgezet in een onleesbare indeling, zodat alleen geautoriseerde gebruikers toegang hebben. Deze versterkte beschermingslaag beschermt niet alleen waardevolle gegevens tegen ongeoorloofde ogen, maar zorgt ook voor gemoedsrust. Met de handtekening-API&#39;s kunt u de beveiliging en privacy van Adobe PDF-documenten die door uw organisatie worden gedistribueerd en ontvangen, beschermen. Deze service gebruikt digitale handtekeningen en certificering om ervoor te zorgen dat alleen de beoogde ontvangers documenten kunnen wijzigen.

  U kunt vanuit uw officiële e-mailid naar `aem-forms-ea@adobe.com` schrijven om deel te nemen aan het programma voor vroegtijdige adoptie en toegang tot deze functie aanvragen.

* **[](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html) de Zwaardeloze Adaptieve Forms van Forms 1}**: Gebruik Zwaardeloze Aangepaste om uw ontwikkelaars toe te laten om, interactieve vormen tot stand te brengen te publiceren en te beheren die met door APIs, eerder dan door een traditioneel grafisch gebruikersinterface kunnen worden betreden en worden in wisselwerking gesteld. Met behulp van hoofdloze adaptieve formulieren kunt u:

   * multikanaalformulieren van hoge kwaliteit maken in de programmeertaal van uw keuze
   * U kunt zelf formulieren integreren in uw bureaublad en mobiele apps, websites en chattoepassingen
   * gebruik uw eigen UI-componenten opnieuw met formuliertoepassingen
   * de kracht van Adobe Experience Manager Forms gebruiken

  U kunt een e-mail naar `aem-forms-headless@adobe.com` verzenden vanuit uw officiële e-mailadres om deel te nemen aan het programma voor vroegtijdige adoptie.

## [!DNL Experience Manager] als een [!DNL Cloud Service] Foundation {#foundation}

### Nieuw gedrag CDN in cache plaatsen voor aan campagne gerelateerde URL-parameters {#cache-url-params}

Voor nieuwe milieu&#39;s, zal CDN marketing verwante vraagparameters door gebrek verwijderen om de prestaties van de marketing campagne en de slagverhoudingen van het geheime voorgeheugen te verhogen. Bestaande omgevingen blijven ongewijzigd. [ leer meer ](/help/implementing/dispatcher/caching.md#marketing-parameters).

### Programma voor vroege adoptie van verkeersfilterregels (inclusief WAF-regels) {#waf-early-adopter}

Het verkeer van de filter bij CDN die op wordt gebaseerd:

* aanvraagheaders en -eigenschappen (bijvoorbeeld IP-adres)
* verkeerspatronen gekend om met kwaadwillig verkeer worden geassocieerd

Wilt u de functie proberen en feedback delen? Verzend een e-mail naar **aemcs-waf-adopter@adobe.com** van uw officiële e-mailidentiteitskaart om meer over het vroege adoptieprogramma te leren. De ruimte is beperkt.

Leer meer over de eigenschap in het artikel [ hier ](/help/security/traffic-filter-rules-including-waf.md).

## Cloud Manager {#cloud-manager}

U kunt een volledige lijst van de maandelijkse versies van Cloud Manager [ hier ](/help/implementing/cloud-manager/release-notes/current.md) vinden.

## Migratiehulpmiddelen {#migration-tools}

U kunt een volledige lijst van de versies van Hulpmiddelen van de Migratie [ hier ](/help/journey-migration/release-notes/release-notes-migration-tools-current.md) vinden.
