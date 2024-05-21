---
title: Opmerkingen bij de release 2023.9.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de release 2023.9.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: d747f58b-8d6c-418d-9d2b-ec3ae4b6dc03
source-git-commit: 02ad83eb9fa9ed3bf06cf7fe0ef10fd9577f66a9
workflow-type: tm+mt
source-wordcount: '1440'
ht-degree: 0%

---


# Opmerkingen bij de release 2023.9.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de versie 2023.9.0 van [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van eerdere versies, zoals 2021 of 2022, vrij te geven.
>
>Kijk eens naar de [Experience Manager geeft Routekaart vrij](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html) voor meer informatie over de volgende activering van functies voor [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Zie [Recente documentatieupdates](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor meer informatie over documentatie-updates die niet rechtstreeks verband houden met een release.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als [!DNL Cloud Service] huidige release met functies (2023.9.0) is 28 september 2023. De volgende release met functies (2023.10.0) is gepland voor 26 oktober 2023.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U vindt de meest recente opmerkingen in de onderhoudsrelease [hier](/help/release-notes/maintenance/latest.md).

## Video vrijgeven {#release-video}

Bekijk de video Overzicht van de release van september 2023 voor een overzicht van de functies die zijn toegevoegd in de release van 2023.9.0:

>[!VIDEO](https://video.tv.adobe.com/v/3424826/?quality=12)

## AEM Edge Delivery Services {#edge-delivery}

Edge Delivery is een nieuwe reeks composable services die erop gericht zijn de impact van inhoud te maximaliseren om meetbare bedrijfsresultaten op het punt van klantinteractie aan te sturen.

Meer informatie over Edge Delivery Services in het artikel [hier](/help/edge/overview.md).

## [!DNL Experience Manager Assets] als [!DNL Cloud Service] {#assets}

### Nieuwe functies in de weergave Elementen {#assets-view-features}

**Metagegevensformulier toewijzen aan een map**

U kunt nu een metagegevensformulier toewijzen aan een specifieke map binnen uw implementatie. Alle elementen in de map, inclusief de elementen in de submappen, geven vervolgens de eigenschappen weer die in het toegewezen metagegevensformulier zijn gedefinieerd.

![metagegevensformulier toewijzen aan een map](/help/release-notes/assets/assign-to-folder.png)

### Nieuwe functies in de beheerweergave {#admin-view-features}

* **AEM Assets as a Cloud Service integreren met op documenten gebaseerde authoring voor Edge Delivery Services**: Integreer AEM Assets met op documenten gebaseerde authoring voor Edge Delivery Services om auteurs van websites in staat te stellen [gebruiken afbeeldingen die beschikbaar zijn in AEM Assets-opslagruimten tijdens het ontwerpen van documenten in Microsoft Word of Google Docs](/help/edge/using.md#integrate-assets-edge).

* **ZIP-archieven extraheren**: Mogelijkheid om ZIP-archieven te selecteren die in Experience Manager worden beheerd en [bestanden rechtstreeks uitpakken in Experience Manager](/help/assets/manage-digital-assets.md#extract-zip-archives) zonder ze te downloaden.

  ![Items vastzetten voor groepen](/help/release-notes/assets/extract-archive.png)

### Functies voor pre-release beschikbaar in [!DNL Experience Manager Assets] {#prerelease-features-assets}

* **Dynamic Media**: [Ondersteuning voor multicaption- en multiaudiotracks voor video&#39;s in Dynamic Media](/help/assets/dynamic-media/video.md#about-msma)—U kunt nu eenvoudig meerdere bijschriften en audiotracks toevoegen aan een primaire video. Dit betekent dat uw video&#39;s toegankelijk zijn voor een breed publiek. U kunt één gepubliceerde primaire video aanpassen aan een wereldwijd publiek in meerdere talen en de richtlijnen voor toegankelijkheid voor verschillende geografische regio&#39;s naleven. Auteurs kunnen de bijschriften en audiotracks ook beheren vanaf één tabblad in de gebruikersinterface.

  ![Het tabblad Bijschriften en audiotracks op de pagina Eigenschappen van een geselecteerd video-element.](/help/release-notes/assets/msma-aem-cs.png)*Het tabblad Bijschriften en audiotracks op de pagina Eigenschappen van een geselecteerd video-element.*

## [!DNL Experience Manager Forms] als [!DNL Cloud Service] {#forms}

### Nieuwe functies in [!DNL Experience Manager Forms] {#forms-features}

* [**Google reCAPTCHA-bedrijfsondersteuning**](/help/forms/captcha-adaptive-forms-core-components.md): Gebruik Google reCAPTCHA Enterprise in een adaptieve vorm om een betere bescherming te bieden tegen frauduleuze activiteiten en spam, zodat gebruikers veiliger worden. Met een geavanceerde risicoanalyse en naadloze integratie kunnen echte gebruikers eenvoudig formulieren indienen terwijl de bots effectief worden geblokkeerd.

* [**Adobe Analytics with Experience Cloud Setup Automation for Forms**](/help/forms/enable-adobe-analytics-adaptive-form-using-experience-cloud-setup-automation.md): U kunt nu Adobe Analytics met de Automatisering van de Opstelling van het Experience Cloud met een omdraaiing van een paar knopen toelaten. Hiermee kunt u AEM Forms as a Cloud Service verbinden met Experience Platforms-tags en Adobe Analytics om prestatiegegevens voor gepubliceerde formulieren vast te leggen en bij te houden.

  >[!VIDEO](https://video.tv.adobe.com/v/3424577/enable-adobe-analytics/?quality=12&learn=on)

* [**Adobe Analytics-rapportsjabloon voor Adaptive Forms**](/help/forms/view-understand-aem-forms-analytics-reports.md): Forms as a Cloud Service geeft nu een Adobe Analytics-rapport OOTB. Zo kunt u gemakkelijk de prestaties van uw formulieren begrijpen. De maatstaven op formulierniveau bieden u inzicht in de manier waarop het formulier werkt met meerdere prestatie-indicatoren (KPI&#39;s), zoals uitvoeringen, bezoekers, verzendingen, gemiddelde vultijd. Door gebruikersgedrag en feedback te volgen, kunt u delen van het formulier identificeren die verwarring veroorzaken en verbeteringen aanbrengen in het ontwerp en de functionaliteit van het formulier.

  ![Adobe Analyserapport Adaptive form user engagement](/help/forms/assets/forms-analytics-report.png)

* **[Formulierfragment in Adaptief Forms op basis van kerncomponenten](/help/forms/adaptive-form-fragments-core-components.md)**: U kunt dubbel werk afscheid nemen, uw digitale inventaris optimaliseren en de samenwerking verbeteren terwijl u de ervaring voor het maken van formulieren vergroot met formulierfragmenten. Deze herbruikbare componenten integreren naadloos in meerdere formulieren, waardoor het maken van consistente en professioneel ogende formulieren wordt gestroomlijnd. Formulierfragmenten zorgen voor herbruikbaarheid, standaardisering en consistentie van merken via de functie &#39;Eenmaal wijzigen en overal weerspiegelen&#39;. Ervaar meer onderhoudsgemak en efficiëntie, aangezien updates die op één plaats worden gemaakt, automatisch worden verspreid over alle vormen die deze fragmenten gebruiken.

* **[Verbeterde Adobe Sign Workflow-stap](/help/forms/aem-forms-workflow-step-reference.md#sign-document-step-sign-document-step)**: De Adobe Sign Workflow-stap wordt uitgebreid en omvat het volgende:
   * **Verificatie op basis van overheidsidentiteitskaart voor Adobe Sign**: Verificatie op basis van een Adobe Acrobat Sign-staatsidentificatie biedt een extra verificatielaag door gebruikers in staat te stellen hun identiteit te verifiëren met behulp van door de overheid uitgegeven id&#39;s (rijbewijs, nationale id, paspoort). Door vertrouwde identificatiedocumenten te gebruiken, voegt deze verbetering een extra niveau van vertrouwen aan het ondertekeningsproces toe, die het ideaal maakt voor scenario&#39;s die verhoogde veiligheid, naleving, en gebruikersbevestiging vereisen.

   * **Audittrail voor Adobe Sign-documenten**: Gebruik de functie Audittrail voor meer informatie over de levenscyclus van uw Adobe Sign-documenten. Met het audittrail, kunt u een uitvoerig verslag van alle acties en interactie handhaven met betrekking tot uw documenten. Dit omvat gegevens zoals wie het document heeft bekeken, bewerkt of ondertekend, samen met tijdstempels voor elke gebeurtenis. Deze verbetering is van cruciaal belang voor het handhaven van de naleving, het oplossen van geschillen en het verzekeren van de integriteit van uw digitale overeenkomsten.

   * **Nieuwe rollen voor ontvangers van de Overeenkomst voorbij enkel de Ondertekenaar**: Adobe Acrobat Sign heeft de optie om de rollen voor overeenkomstontvangers uit te breiden tot buiten alleen de ondertekenaar om beter aan hun workflowvereisten te voldoen. Wanneer toegelaten, heeft elke ontvanger in een Overeenkomst zijn rol individueel configureerbaar, met Ondertekenaar die het gebrek is.

* **Ondersteuning voor paginanummers in communicatie-API&#39;s**: Nu kunt u, samen met het ophalen van uw document via de communicatie-API&#39;s, ook de waardevolle informatie over het aantal pagina&#39;s in het document ontvangen.

* **[Fout bij afhandeling van aangepaste fouthandlers in de regeleditor](/help/forms/add-custom-error-handler-adaptive-forms-core-components.md)**: U kunt nu een aangepaste functie aanroepen als reactie op een fout die door een externe service is geretourneerd, en eindgebruikers een op maat gemaakte reactie geven. Bijvoorbeeld, kunt u een douanewerkschema in de achtergrond voor specifieke foutencodes aanhalen of de klant informeren dat de dienst neer is.

* **[64-bits versie van AEM Forms Designer](/help/forms/installing-configuring-designer.md)**: De 64-bits versie van AEM Forms Designer biedt verbeterde prestaties, schaalbaarheid en geheugenbeheer, zodat u meer mogelijkheden hebt om formulieren te maken. Met de 64-bits architectuur kunt u nog grotere en complexere projecten eenvoudig aanpakken, zodat u kunt zorgen voor naadloze ontwerpworkflows en geoptimaliseerde efficiëntie. Verhoog uw mogelijkheden voor formulierontwerp en omarm de toekomst van AEM Forms Designer met deze geavanceerde release.

### Programma voor vroegtijdige adoptie {#forms-early-adopter}

* **[Protect uw documenten met DocAssurance-API&#39;s (onderdeel van communicatie-API&#39;s)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: De DocAssurance-API&#39;s stellen u in staat gevoelige informatie te beveiligen door de documenten te ondertekenen en te versleutelen. Door versleuteling wordt de inhoud van een document omgezet in een onleesbare indeling, zodat alleen geautoriseerde gebruikers toegang hebben. Deze versterkte beschermingslaag beschermt niet alleen waardevolle gegevens tegen ongeoorloofde ogen, maar zorgt ook voor gemoedsrust. Met de handtekening-API&#39;s kunt u de beveiliging en privacy van Adobe PDF-documenten die door uw organisatie worden gedistribueerd en ontvangen, beschermen. Deze service gebruikt digitale handtekeningen en certificering om ervoor te zorgen dat alleen de beoogde ontvangers documenten kunnen wijzigen.

  U kunt schrijven naar `aem-forms-ea@adobe.com` van uw officiële e-mailidentiteitskaart om zich bij het vroege adoptieprogramma aan te sluiten en toegang tot het vermogen te verzoeken.

* **[Forms zonder hoofdadapter](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html)**: Gebruik Headless Adaptive Forms om uw ontwikkelaars in staat te stellen interactieve formulieren te maken, te publiceren en te beheren die via API&#39;s kunnen worden geopend en gebruikt in plaats van via een traditionele grafische gebruikersinterface. Met behulp van hoofdloze adaptieve formulieren kunt u:

   * multikanaalformulieren van hoge kwaliteit maken in de programmeertaal van uw keuze
   * U kunt zelf formulieren integreren in uw bureaublad en mobiele apps, websites en chattoepassingen
   * gebruik uw eigen UI-componenten opnieuw met formuliertoepassingen
   * de kracht van Adobe Experience Manager Forms gebruiken

  U kunt een e-mail verzenden naar `aem-forms-headless@adobe.com` van uw officiële e-mailadres om deel te nemen aan het vroege adoptieprogramma.

## [!DNL Experience Manager] als [!DNL Cloud Service] Stichting {#foundation}

### Nieuw gedrag CDN in cache plaatsen voor aan campagne gerelateerde URL-parameters {#cache-url-params}

Voor nieuwe milieu&#39;s, zal CDN marketing verwante vraagparameters door gebrek verwijderen om de prestaties van de marketing campagne en de slagverhoudingen van het geheime voorgeheugen te verhogen. Bestaande omgevingen blijven ongewijzigd. [Meer weten?](/help/implementing/dispatcher/caching.md#marketing-parameters)

### Regels voor vroege adoptie van verkeersfilters (inclusief WAF-regels) {#waf-early-adopter}

Het verkeer van de filter bij CDN die op wordt gebaseerd:

* aanvraagheaders en -eigenschappen (bijvoorbeeld IP-adres)
* verkeerspatronen gekend om met kwaadwillig verkeer worden geassocieerd

Wilt u de functie proberen en feedback delen? Een e-mail verzenden naar **aemcs-waf-adopter@adobe.com** van uw officiële e-mailadres voor meer informatie over het programma voor vroege adoptie. De ruimte is beperkt.

Meer informatie over de functie in het artikel [hier](/help/security/traffic-filter-rules-including-waf.md).

## Cloud Manager {#cloud-manager}

U vindt een volledige lijst met maandreleases van Cloud Manager [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migratiehulpmiddelen {#migration-tools}

U vindt een volledige lijst met de releases van de migratiehulpmiddelen [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
