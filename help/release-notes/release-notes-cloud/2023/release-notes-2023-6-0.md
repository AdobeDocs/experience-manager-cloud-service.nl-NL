---
title: Nota's van de versie voor 2023.6.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Nota's van de versie voor 2023.6.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: 29cf9548-e413-4e4f-b233-d6bb04918b22
feature: Release Information
role: Admin
source-git-commit: f28f212574dda0ece2cedb56a714d381e5bd7d3c
workflow-type: tm+mt
source-wordcount: '1322'
ht-degree: 0%

---

# Opmerkingen bij de release 2023.6.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de versie 2023.6.0 van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van eerdere versies, zoals 2021 of 2022, vrij te geven.
>
>Heb een blik bij de [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=nl-NL) vrij om over de aanstaande eigenschapactivering voor [!DNL Experience Manager] as a Cloud Service te leren.

>[!NOTE]
>
>Zie [ Recente Updates van de Documentatie ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=nl-NL) voor details van documentatieupdates niet direct met een versie verwant.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige release met functies (2023.6.0) is 29 juni 2023. De volgende release met functies (2023.7.0) is gepland voor 27 juli 2023.

## Video vrijgeven {#release-video}

Bekijk de video Overzicht van de release van juni 2023 voor een overzicht van de functies die in de release van 2023.6.0 zijn toegevoegd:

>[!VIDEO](https://video.tv.adobe.com/v/3420971/?quality=12)

## [!DNL Experience Manager Sites] als een [!DNL Cloud Service] {#sites}

### Nieuwe functies in [!DNL Experience Manager Sites] {#sites-features}

* De Fragmenten van de inhoud en hun verwijzingen kunnen nu aan de [ AEM Dienst van de Voorproef ](/help/implementing/cloud-manager/manage-environments.md#access-preview-service) worden gepubliceerd gebruikend de [ Console van het Fragment van de Inhoud ](/help/sites-cloud/administering/content-fragments/managing.md#content-fragments-console), toestaand gebruikers aan voorproef de definitieve ervaring op een ontkoppelde voorproeftoepassing alvorens live te gaan.

![ Voorproef in de Console van het Fragment van de Inhoud ](/help/assets/content-fragments-console-preview.png)

* Afbeeldingen kunnen nu dynamisch worden geoptimaliseerd voor weergave op het web in scenario&#39;s zonder kop met AEM GraphQL. [ de variabelen van de Vraag ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/images.html?lang=nl-NL#query-variables) kunnen in de vragen van GraphQL worden bepaald om ontkoppelde cliënttoepassingen toe te staan verzoek dienovereenkomstig geoptimaliseerde beelden van AEM.
* De markeringen op [ de Variaties van het Fragment van de Inhoud ](https://experienceleague.adobe.com/docs/experience-manager-65/assets/content-fragments/content-fragments-variations.html?lang=nl-NL) kunnen nu output aan JSON gebruikend de AEM de inhoudslevering API van GraphQL worden.

## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#assets-features}

**Beschikbaarheid van Nieuwe mening van Assets**

De [ nieuwe mening van Assets ](/help/assets/assets-view-introduction.md) is nu beschikbaar in Experience Manager Assets. Assets View biedt een vereenvoudigde gebruikersinterface waarmee u uw digitale middelen eenvoudig kunt beheren, ontdekken en distribueren. De ervaring is gericht op creatieve personen, alleen-lezen klanten en minder belangrijke DAM-gebruikers.

![ het Taggen Beheer ](/help/assets/assets/my-workspace.png)

**de ervaringsverhogingen van het Onderzoek**

Met Experience Manager Assets kunt u nu meer doen vanuit de gebruikersinterface voor zoekresultaten: u kunt nu:

* [ voer onderzoek binnen de huidige bewaarplaats ](/help/assets/search-assets.md) door gebrek in plaats van het zoeken naar het sleutelwoord in de volledige bewaarplaats uit.

* [ navigeer aan de omslagplaats ](/help/assets/search-assets.md#aftersearch) voor activa die in de onderzoeksresultaten tonen.

**de voorproeven van de Duimnagel voor 3D activa**

[!DNL Experience Manager Assets] produceert nu [ duimnagelvoorproeven voor gemeenschappelijke 3D dossierformaten ](/help/assets/file-format-support.md) met inbegrip van gLB, USDz, FBX, 3DS, OBJ, en SBSAR. Wanneer deze bestanden worden geüpload, worden automatisch miniaturen gegenereerd.

**Dynamic Media: Bijgewerkte Slimme op uitsnijden betrekking hebbende gebieden in het profiel van het Beeld**

De gebruikersinterface voor bepaalde velden met betrekking tot Slim uitsnijden in een afbeeldingsprofiel wordt nu bijgewerkt met de huidige richtlijnen voor het definiëren van een slim uitsnijden. Zie [ opties van het Gewas ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/image-profiles.html?lang=nl-NL#crop-options).

### Nieuwe functies in de Assets-weergave {#assets-view-features}

**Hiërarchische het etiketteren van activa voor snellere onderzoekservaring**

Vlakke lijsten met gecontroleerde woordenboeken worden in de loop der tijd onbeheersbaar. De mening van Assets steunt nu [ hiërarchische het etiketteren structuur ](/help/assets/tagging-management-assets-view.md), die het toepassen van relevante meta-gegevens vergemakkelijkt, het categoriseren van activa, het steunen van onderzoek, het hergebruiken van markeringen, het verbeteren van ontdekkingsbaarheid, etc.

![ het Taggen Beheer ](/help/assets/assets/tags-hierarchy.png)

**Vastzetten dossiers, omslagen, en inzamelingen voor snelle toegang**

U kunt [ dossiers, omslagen, en inzamelingen nu spelden voor snellere toegang ](/help/assets/my-workspace-assets-view.md) tot deze punten wanneer u hen later nodig hebt. De vastgezette punten tonen in de **Snelle toegang** sectie van Mijn Workspace. U kunt ze openen met Mijn Workspace in plaats van naar de locatie te navigeren waar ze zijn opgeslagen in de repository.

![ Taken in Workspace ](/help/assets/assets/quick-access.png)

**de activa van de Filter in de omslag van het Afval**

De mening van Assets laat u nu toe [ filteractiva beschikbaar in de omslag van het Afval ](/help/assets/navigate-assets-view.md). U kunt standaard- of aangepaste filters toepassen om te zoeken in de juiste middelen in de map met prullenmand om deze te herstellen of permanent te verwijderen.

**de voorproeven van de Duimnagel voor 3D activa**

In de Assets-weergave worden nu miniatuurvoorvertoningen gegenereerd voor veelgebruikte 3D-bestandsindelingen, zoals gLB, USDz, FBX, 3DS, OBJ en SBSAR. Wanneer deze bestanden naar de Assets-weergave worden geüpload, worden automatisch miniaturen gegenereerd door het systeem.

![ Taken in Workspace ](/help/assets/assets/3d-preview.png)

**hoogste gezochte termijnen van de Mening**

De mening van Assets steunt nu [ het bekijken van hoogste gezochte termijnen binnen uw plaatsing ](/help/assets/my-workspace-assets-view.md) gebruikend de **sectie van Inzichten** van Mijn Workspace. U kunt ook naar gedetailleerde inzichten navigeren om de belangrijkste zoekopdrachten in de afgelopen 30 dagen of 12 maanden weer te geven.

![ Taken in Workspace ](/help/assets/assets/insights-top-searches.png)

**de vormverhogingen van meta-gegevens**

De mening van Assets laat u nu toe om multi-waardetekst en drop-down de componenten van het lijstbezit [&#128279;](/help/assets/metadata-assets-view.md#property-components) aan de meta-gegevensvormen toe te voegen.

## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

### Nieuwe functies beschikbaar in [!DNL Forms] {#new-features-available-in-channel}

* [ Aangepaste Forms binnen AEM Redacteur van de Pagina ](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md): U kunt nu AEM Redacteur van de Pagina gebruiken om veelvoudige vormen aan uw plaatspagina&#39;s snel tot stand te brengen en toe te voegen. Met deze functie kunnen auteurs van inhoud naadloze ervaringen met gegevensvastlegging op sitepagina&#39;s maken met behulp van de kracht van adaptieve formuliercomponenten, zoals dynamisch gedrag, validaties, gegevensintegratie, het genereren van een document van registratie- en bedrijfsprocesautomatisering. U kunt:

   * Maak een adaptief formulier door formuliercomponenten te slepen en neer te zetten op Adaptive Forms Container Component in AEM Sites Editor of Experience Fragments.
   * Met de wizard Adaptive Forms in de AEM Sites-editor kunt u onafhankelijk van elke sitepagina formulieren maken die u de vrijheid geven dergelijke formulieren op meerdere pagina&#39;s opnieuw te gebruiken.
   * Voeg meerdere formulieren toe aan een sitepagina, zodat de gebruikerservaring wordt gestroomlijnd en er meer flexibiliteit wordt geboden.

     >[!VIDEO](https://video.tv.adobe.com/v/3419284?quality=12&learn=on)

* [ Adobe Acrobat Sign Solutions voor Regering ](/help/forms/adobe-sign-integration-adaptive-forms.md): AEM Forms integreert nu met Adobe Acrobat Sign Solutions voor Regering. Deze integratie biedt een geavanceerd niveau van naleving en beveiliging voor e-handtekeningen met Adaptief formulier-inzendingen voor met de overheid verband houdende rekeningen (overheidsdiensten en agentschappen).

  Dankzij de integratie met Adobe Acrobat Sign Solutions for Government kunnen partners en klanten van de Adobe in Adaptive Forms elektronische handtekeningen gebruiken voor een aantal van de meest bedrijfskritieke en gevoelige bedrijfsonderdelen. Deze extra laag van veiligheid zorgt ervoor dat alle e-handtekeningen volledig volgzaam met de Matige naleving FedRAMP zijn, die de klanten van de overheid van de Adobe van mening voorziet.

* [ Verbeterde fout behandeling met de managers van de douanefout in regelredacteur ](/help/forms/add-custom-error-handler-adaptive-forms.md): U kunt een douanefunctie (het gebruiken van de Bibliotheek van de Cliënt) nu aanhalen in antwoord op een fout die door de externe dienst is teruggekeerd en een op maat gemaakte reactie aan eind - gebruikers verstrekken. Of u kunt specifieke acties uitvoeren voor fouten die door een service worden geretourneerd. Bijvoorbeeld, kunt u een douanewerkschema in de achtergrond voor specifieke foutencodes aanhalen of de klant informeren dat de dienst neer is.

  Deze functionaliteit verbetert uw algemene fout-behandelend vermogen door op norm-gebaseerde foutenreacties in te voeren die achterwaarts compatibel met OOTB foutenmanagers, met grotere flexibiliteit en controle zijn.

* [ Verbeterde authentificatiemethodes voor het Model van de Gegevens van de Vorm ](/help/forms/configure-data-sources.md): Ervaring verhoogde veiligheid met de introductie van de Gebaseerde authentificatie van de Referentie van de Cliënt voor het verbinden van AEM Forms met compatibele gegevensbronnen. Deze verbetering elimineert de behoefte aan imitatie of gebruikerslogin, die de bescherming van uw gegevens verstevigt.

* [ Aangepaste Forms met herhaalbare secties ](/help/forms/create-forms-repeatable-sections.md): U kunt [ Accordeon ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion.html?lang=nl-NL), [ Tovenaar ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard.html?lang=nl-NL), [ Comité ](https://experienceleague.adobe.com/nl/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel), en [ Horizontale componenten van Lusjes ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs.html?lang=nl-NL) in een op componenten gebaseerde Aangepaste Vorm van de Kern nu maken om herhaalbare secties tot stand te brengen.

  >[!VIDEO](https://video.tv.adobe.com/v/3421052/adaptive-forms-repeatable-sections-repeat-sections/?quality=12&learn=on)

  Met deze herhaalbare secties kunt u een onbeperkt aantal items opgeven zonder een vast aantal velden. Dit is handig wanneer de vereiste instanties van gegevens vooraf onbekend zijn. Forms-gebruikers kunnen eenvoudig secties toevoegen of verwijderen, waardoor formulieren kunnen worden aangepast aan verschillende scenario&#39;s voor gegevensinvoer en de verzameling van meerdere exemplaren van dezelfde gegevens kan worden vereenvoudigd.

* **[legt Aangepaste Forms aan Microsoft® SharePoint en Microsoft® OneDrive voor](/help/forms/configuring-submit-actions.md)**: Verbeter bedrijfsgebruikersbehendigheid zodat kunt u nieuwe vormen snel lanceren en voorgelegde gegevens opslaan in alledaagse hulpmiddelen die zij zoals plaats Microsoft® SharePoint of omslag OneDrive gebruiken.

### Forms-programma voor vroege adoptie zonder adapter {#forms-early-adopter}

Het gebruik [ Zwaardeloze Aanpassings Forms ](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=nl-NL) om uw ontwikkelaars toe te laten om, interactieve vormen tot stand te brengen te publiceren en te beheren die met door APIs, eerder dan door een traditioneel grafisch gebruikersinterface kunnen worden betreden en worden in wisselwerking getreden. Met behulp van hoofdloze adaptieve formulieren kunt u:

* multikanaalformulieren van hoge kwaliteit maken in de programmeertaal van uw keuze
* U kunt zelf formulieren integreren in uw bureaublad en mobiele apps, websites en chattoepassingen
* gebruik uw eigen UI-componenten opnieuw met formuliertoepassingen
* de kracht van Adobe Experience Manager Forms gebruiken

U kunt een e-mail naar `aem-forms-headless@adobe.com` verzenden vanuit uw officiële e-mailadres om deel te nemen aan het programma voor vroegtijdige adoptie.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U kunt de recentste nota&#39;s van de onderhoudsversie [ hier ](/help/release-notes/maintenance/latest.md) vinden.

## Cloud Manager {#cloud-manager}

U kunt een volledige lijst van de maandelijkse versies van Cloud Manager [ hier ](/help/implementing/cloud-manager/release-notes/current.md) vinden.

## Migratiehulpmiddelen {#migration-tools}

U kunt een volledige lijst van de versies van Hulpmiddelen van de Migratie [ hier ](/help/journey-migration/release-notes/release-notes-migration-tools-current.md) vinden.
