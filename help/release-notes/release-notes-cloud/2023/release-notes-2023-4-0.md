---
title: Nota's van de versie voor 2023.4.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Nota's van de versie voor 2023.4.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: c34aedee-e45a-4e2a-ae7f-930bc0cc026f
feature: Release Information
role: Admin
source-git-commit: b4ffcddddfcd990c359380071f19b5442dee9eb2
workflow-type: tm+mt
source-wordcount: '1112'
ht-degree: 0%

---

# Opmerkingen bij de release 2023.4.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de versie 2023.4.0 van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van eerdere versies, zoals 2021 of 2022, vrij te geven.
>
>Heb een blik bij [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=nl-NL) vrij om over de aanstaande eigenschapactivering voor [!DNL Experience Manager] as a Cloud Service te leren.

>[!NOTE]
>
>Zie [ Recente Updates van de Documentatie ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=nl-NL) voor details van documentatieupdates niet direct met een versie verwant.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige release met functies (2023.4.0) is 7 juni 2023. De volgende release met functies (2023.6.0) is gepland voor 29 juni 2023.

## Video vrijgeven {#release-video}

Bekijk de video Overzicht van de release van april 2023 voor een overzicht van de functies die zijn toegevoegd in de release van 2023.4.0:

>[!VIDEO](https://video.tv.adobe.com/v/3418681/?quality=12)

## [!DNL Experience Manager Sites] als een [!DNL Cloud Service] {#sites}

### Nieuwe functies in [!DNL Experience Manager Sites] {#sites-features}

* Exporteer inhoudsfragmenten van AEM as a Cloud Service naar Adobe Target in JSON-indeling en maak overeenkomende JSON-aanbiedingen in Target.
* Ondersteuning voor paginering en sortering door GraphQL en verbeteringen in de interne cache helpen u nu de prestaties van losgekoppelde clienttoepassingen te verbeteren wanneer u grote inhoudssets van AEM ophaalt met behulp van complexe GraphQL-query&#39;s en -filters.

### Nieuwe functies in [!DNL Experience Manager Sites] prerelease {#prerelease-sites}

* De Fragmenten van de inhoud en hun verwijzingen kunnen nu aan de [ Dienst van de Voorproef van AEM ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-environments.html?lang=nl-NL#access-preview-service) worden gepubliceerd gebruikend de [ Console van het Fragment van de Inhoud ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/content-fragments/content-fragments-console.html?lang=nl-NL), toestaand gebruikers aan voorproef de definitieve ervaring op een ontkoppelde voorproeftoepassing alvorens live te gaan.
* Afbeeldingen kunnen nu dynamisch worden geoptimaliseerd voor weergave op het web in scenario&#39;s zonder kop met AEM GraphQL. [ de variabelen van de Vraag ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/images.html?lang=nl-NL#query-variables) kunnen in de vragen van GraphQL worden bepaald om ontkoppelde cliënttoepassingen toe te staan verzoek dienovereenkomstig geoptimaliseerde beelden van AEM.
* De markeringen op [ de Variaties van het Fragment van de Inhoud ](https://experienceleague.adobe.com/docs/experience-manager-65/assets/content-fragments/content-fragments-variations.html?lang=nl-NL) kunnen nu output aan JSON gebruikend AEM GraphQL de inhoudslevering API worden.

## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#assets-features}

* Extra ondersteuning voor WebP-afbeeldingen om automatisch metagegevens te extraheren, miniaturen en aangepaste uitvoeringen te genereren. De functie Slimme tags wordt nu ook ondersteund voor deze bestanden. Dynamische mediafuncties worden niet ondersteund voor WebP als invoerindeling.

* [ de ervaringsverhogingen van het Onderzoek ](/help/assets/search-assets.md#aftersearch) - u kunt de volgende verrichtingen op de activa nu snel uitvoeren die in de onderzoeksresultaten tonen:

   * Een workflow maken
   * Een versie maken
   * Relatieve of niet-gerelateerde elementen

     U hoeft niet naar de middelenlocatie te navigeren en de eigenschappen ervan te bekijken om deze bewerkingen uit te voeren.

* Verbeteringen in de gebruiksvriendelijkheid van Color Search facet - Invoerveld voor kleurwaarden kan nu worden bewerkt en zoekresultaten worden alleen bijgewerkt wanneer u de kleurkiezer afsluit.

* Nieuwe protocolondersteuning gestart (DASH - Dynamic Adaptive Streaming via HTTP) voor Adaptive streaming in Dynamic Media video levering (met CMAF ingeschakeld):
   * Adaptief streamen (DASH/HLS) zorgt voor een betere kijkervaring voor video&#39;s
   * DASH is het internationale standaardprotocol voor adaptieve videostreaming en wordt op grote schaal toegepast in de branche

* De dynamische Opname van Media _0&rbrace; - Experimenteer met testbeelden of Dynamische Media URLs, om de output van verschillende beeldbepalingen te zien, en slimme optimalisaties van het Beeld voor dossiergrootte (met levering WebP en AVIF), netwerkbandbreedte, en de Verhouding van het Pixel van het Apparaat te beoordelen._ Zie [ Dynamische Momentopname van Media ](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-snapshot.html?lang=nl-NL).

### Functie in [!DNL Assets] prerelease {#prerelease-feature-assets}

* Dynamische media - De gebruikersinterface voor bepaalde velden met betrekking tot Slim uitsnijden in een afbeeldingsprofiel wordt nu bijgewerkt met de huidige richtlijnen voor het definiëren van een slim uitsnijden. Zie [ opties van het Gewas ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/image-profiles.html?lang=nl-NL#crop-options).

## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

### Nieuwe functies beschikbaar in [!DNL Forms] {#new-features-available-in-channel}

* **[legt Aangepaste Forms aan Microsoft® SharePoint en Microsoft® OneDrive voor](/help/forms/configuring-submit-actions.md)**: Verbeter bedrijfsgebruikersbehendigheid zodat kunt u nieuwe vormen snel lanceren en voorgelegde gegevens opslaan in alledaagse hulpmiddelen die zij zoals plaats Microsoft® SharePoint of omslag OneDrive gebruiken.

### Functies in [!DNL Forms] prerelease {#prerelease-features-forms}

* [ Aangepaste Forms binnen de Redacteur van de Pagina van AEM ](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md): U kunt nu de Redacteur van de Pagina van AEM gebruiken om veelvoudige vormen aan uw plaatspagina&#39;s snel tot stand te brengen en toe te voegen. Met deze functie kunnen auteurs van inhoud naadloze ervaringen met gegevensvastlegging op sitepagina&#39;s maken met behulp van de kracht van adaptieve formuliercomponenten, zoals dynamisch gedrag, validaties, gegevensintegratie, het genereren van een document van registratie- en bedrijfsprocesautomatisering. U kunt:

   * Maak een adaptief formulier door formuliercomponenten te slepen en neer te zetten op Adaptive Forms Container Component in AEM Sites Editor of Experience Fragments.
   * Met de wizard Adaptive Forms in de AEM Sites-editor kunt u onafhankelijk van elke sitepagina formulieren maken die u de vrijheid geven dergelijke formulieren op meerdere pagina&#39;s opnieuw te gebruiken.
   * Voeg meerdere formulieren toe aan een sitepagina, zodat de gebruikerservaring wordt gestroomlijnd en er meer flexibiliteit wordt geboden.

     >[!VIDEO](https://video.tv.adobe.com/v/3419284?quality=12&learn=on)

* [ Adobe Acrobat Sign Solutions voor Regering ](/help/forms/adobe-sign-integration-adaptive-forms.md): AEM Forms integreert nu met Adobe Acrobat Sign Solutions voor Regering. Deze integratie biedt een geavanceerd niveau van naleving en beveiliging voor e-handtekeningen met Adaptief formulier-inzendingen voor met de overheid verband houdende rekeningen (overheidsdiensten en agentschappen).

  Dankzij de integratie met Adobe Acrobat Sign for Government kunnen Adobe-partners en overheidsklanten in Adaptive Forms elektronische handtekeningen gebruiken voor een aantal van de meest bedrijfskritieke en gevoelige bedrijfsonderdelen. Deze extra laag van veiligheid zorgt ervoor dat alle e-handtekeningen volledig volgzaam met de Matige naleving FedRAMP zijn, die de klanten van de overheid van Adobe van mening voorzien.

* Verbeterde foutafhandeling met aangepaste fouthandlers in de regeleditor: u kunt nu een aangepaste functie aanroepen (met behulp van de clientbibliotheek) als reactie op een fout die door een externe service is geretourneerd, en eindgebruikers een op maat gemaakte reactie geven. Of u kunt specifieke acties uitvoeren voor fouten die door een service worden geretourneerd. Bijvoorbeeld, kunt u een douanewerkschema in de achtergrond voor specifieke foutencodes aanhalen of de klant informeren dat de dienst neer is.

  Deze functionaliteit verbetert uw algemene fout-behandelend vermogen door op norm-gebaseerde foutenreacties in te voeren die achterwaarts compatibel met OOTB foutenmanagers, met grotere flexibiliteit en controle zijn.

### Forms-programma voor vroege adoptie zonder adapter {#forms-early-adopter}

Gebruik Headless Adaptive Forms om uw ontwikkelaars in staat te stellen interactieve formulieren te maken, te publiceren en te beheren die via API&#39;s kunnen worden geopend en gebruikt in plaats van via een traditionele grafische gebruikersinterface. Met behulp van hoofdloze adaptieve formulieren kunt u:

* multikanaalformulieren van hoge kwaliteit maken in de programmeertaal van uw keuze
* U kunt zelf formulieren integreren in uw bureaublad en mobiele apps, websites en chattoepassingen
* gebruik uw eigen UI-componenten opnieuw met formuliertoepassingen
* de kracht van Adobe Experience Manager Forms gebruiken

U kunt een e-mail naar `aem-forms-headless@adobe.com` verzenden vanuit uw officiële e-mailadres om deel te nemen aan het programma voor vroegtijdige adoptie.

## [!DNL Experience Manager] als een [!DNL Cloud Service] Foundation {#foundation}

### Nieuwe functies {#what-is-new-foundation}

* Extra publicatieregio&#39;s: klanten van sites kunnen maximaal drie publicatiegebieden in licentie geven, naast het primaire gebied. Het verkeer wordt verpletterd aan extra te publiceren landbouwbedrijven, die in verminderde latentie voor bepaalde verzoeken, en verhoogde veerkracht tegen regionale stroomonderbrekingen resulteren. Contacteer uw Manager van de Rekening van Adobe voor informatie over het verlenen van vergunningen [ Extra publiceer Gebieden ](/help/operations/additional-publish-regions.md) voor uw programma&#39;s.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U kunt de recentste nota&#39;s van de onderhoudsversie [ hier ](/help/release-notes/maintenance/latest.md) vinden.

## Cloud Manager {#cloud-manager}

U kunt een volledige lijst van de maandelijkse versies van Cloud Manager [ hier ](/help/implementing/cloud-manager/release-notes/current.md) vinden.

## Migratiehulpmiddelen {#migration-tools}

U kunt een volledige lijst van de versies van Hulpmiddelen van de Migratie [ hier ](/help/journey-migration/release-notes/release-notes-migration-tools-current.md) vinden.
