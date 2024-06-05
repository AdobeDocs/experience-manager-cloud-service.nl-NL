---
title: Opmerkingen bij de release 2023.6.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de release 2023.6.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 29cf9548-e413-4e4f-b233-d6bb04918b22
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1322'
ht-degree: 0%

---

# Opmerkingen bij de release 2023.6.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de versie 2023.6.0 van [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van eerdere versies, zoals 2021 of 2022, vrij te geven.
>
>Kijk eens naar de [Experience Manager geeft Routekaart vrij](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html) voor meer informatie over de volgende activering van functies voor [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Zie [Recente documentatieupdates](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor meer informatie over documentatie-updates die niet rechtstreeks verband houden met een release.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als [!DNL Cloud Service] huidige release met functies (2023.6.0) is 29 juni 2023. De volgende release met functies (2023.7.0) is gepland voor 27 juli 2023.

## Video vrijgeven {#release-video}

Bekijk de video Overzicht van de release van juni 2023 voor een overzicht van de functies die in de release van 2023.6.0 zijn toegevoegd:

>[!VIDEO](https://video.tv.adobe.com/v/3420971/?quality=12)

## [!DNL Experience Manager Sites] als [!DNL Cloud Service] {#sites}

### Nieuwe functies in [!DNL Experience Manager Sites] {#sites-features}

* Inhoudsfragmenten en de bijbehorende verwijzingen kunnen nu worden gepubliceerd naar de [AEM](/help/implementing/cloud-manager/manage-environments.md#access-preview-service) met de [Console voor inhoudsfragment](/help/sites-cloud/administering/content-fragments/managing.md#content-fragments-console), zodat gebruikers een voorvertoning van de uiteindelijke ervaring kunnen bekijken in een ontkoppelde voorvertoningstoepassing voordat ze live gaan.

![Voorvertoning in console van inhoudsfragment](/help/assets/content-fragments-console-preview.png)

* Afbeeldingen kunnen nu dynamisch worden geoptimaliseerd voor weergave op het web in scenario&#39;s zonder kop met AEM GraphQL. [Query-variabelen](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/images.html#query-variables) kan worden gedefinieerd in GraphQL-query&#39;s zodat ontkoppelde clienttoepassingen aangepaste geoptimaliseerde afbeeldingen van AEM kunnen aanvragen.
* Labels op [Variaties in inhoudsfragment](https://experienceleague.adobe.com/docs/experience-manager-65/assets/content-fragments/content-fragments-variations.html) kan nu worden uitgevoerd naar JSON met behulp van de AEM GraphQL-API voor het leveren van inhoud.

## [!DNL Experience Manager Assets] als [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#assets-features}

**Beschikbaarheid van de weergave Nieuwe elementen**

De [nieuwe middelenweergave](/help/assets/assets-view-introduction.md) is nu beschikbaar in Experience Manager Assets. De weergave Elementen biedt een vereenvoudigde gebruikersinterface, waarmee u uw digitale elementen eenvoudig kunt beheren, detecteren en distribueren. De ervaring is gericht op creatieve personen, alleen-lezen klanten en minder belangrijke DAM-gebruikers.

![Tagbeheer](/help/assets/assets/my-workspace.png)

**Verbeterde zoekervaring**

Met Experience Manager Assets kunt u nu meer doen vanuit de gebruikersinterface voor zoekresultaten: u kunt nu:

* [Zoekopdracht uitvoeren binnen de huidige opslagplaats](/help/assets/search-assets.md) standaard in plaats van naar het trefwoord te zoeken in de gehele opslagplaats.

* [Ga naar de maplocatie](/help/assets/search-assets.md#aftersearch) voor elementen die in de zoekresultaten worden weergegeven.

**Voorvertoningen van miniaturen voor 3D-elementen**

[!DNL Experience Manager Assets] wordt nu gegenereerd [miniatuurvoorvertoningen van veelgebruikte 3D-bestandsindelingen](/help/assets/file-format-support.md) inclusief gLB, USDz, FBX, 3DS, OBJ en SBSAR. Wanneer deze bestanden worden geüpload, worden automatisch miniaturen gegenereerd.

**Dynamic Media: Bijgewerkte velden voor Smart Crop in afbeeldingsprofiel**

De gebruikersinterface voor bepaalde velden met betrekking tot Slim uitsnijden in een afbeeldingsprofiel wordt nu bijgewerkt met de huidige richtlijnen voor het definiëren van een slim uitsnijden. Zie [Opties voor uitsnijden](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/image-profiles.html#crop-options).

### Nieuwe functies in de weergave Elementen {#assets-view-features}

**Hiërarchische codering van elementen voor sneller zoeken**

Vlakke lijsten met gecontroleerde woordenboeken worden in de loop der tijd onbeheersbaar. De weergave Middelen ondersteunt nu [hiërarchische coderingsstructuur](/help/assets/tagging-management-assets-view.md), die het toepassen van relevante metagegevens, het indelen van elementen, het ondersteunen van zoeken, het hergebruiken van tags, het verbeteren van de detecteerbaarheid, enzovoort, vergemakkelijkt.

![Tagbeheer](/help/assets/assets/tags-hierarchy.png)

**Bestanden, mappen en verzamelingen vastzetten voor snelle toegang**

U kunt nu [bestanden, mappen en verzamelingen vastzetten voor snellere toegang](/help/assets/my-workspace-assets-view.md) op deze objecten te plaatsen als je ze later nodig hebt. De vastgezette items worden weergegeven in het dialoogvenster **Snelle toegang** van Mijn werkruimte. U kunt ze openen met Mijn werkruimte in plaats van naar de locatie te navigeren waar ze zijn opgeslagen in de opslagplaats.

![Taken in de werkruimte](/help/assets/assets/quick-access.png)

**Elementen filteren in de map Prullenbak**

In de weergave Elementen kunt u nu [filterelementen beschikbaar in de map Prullenbak](/help/assets/navigate-assets-view.md). U kunt standaard- of aangepaste filters toepassen om te zoeken in de juiste middelen in de map met prullenmand om deze te herstellen of permanent te verwijderen.

**Voorvertoningen van miniaturen voor 3D-elementen**

In de weergave Elementen worden nu miniatuurvoorvertoningen gegenereerd voor veelgebruikte 3D-bestandsindelingen, zoals gLB, USDz, FBX, 3DS, OBJ en SBSAR. Wanneer deze bestanden worden geüpload naar de weergave Middelen, worden standaard automatisch miniaturen gegenereerd door het systeem.

![Taken in de werkruimte](/help/assets/assets/3d-preview.png)

**Bovenste gezochte termen weergeven**

De weergave Middelen ondersteunt nu [het bekijken van hoogste gezochte termijnen binnen uw plaatsing](/help/assets/my-workspace-assets-view.md) met de **Inzichten** van Mijn werkruimte. U kunt ook naar gedetailleerde inzichten navigeren om de belangrijkste zoekopdrachten in de afgelopen 30 dagen of 12 maanden weer te geven.

![Taken in de werkruimte](/help/assets/assets/insights-top-searches.png)

**Verbeteringen in metagegevensformulieren**

In de weergave Elementen kunt u nu [toevoegen, tekst met meerdere waarden en eigenschappencomponenten voor vervolgkeuzelijsten](/help/assets/metadata-assets-view.md#property-components) op de metagegevensformulieren.

## [!DNL Experience Manager Forms] als [!DNL Cloud Service] {#forms}

### Nieuwe functies beschikbaar in [!DNL Forms] {#new-features-available-in-channel}

* [Adaptieve Forms in AEM paginaeditor](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md): U kunt nu AEM Pagina-editor gebruiken om snel meerdere formulieren te maken en aan uw sitepagina&#39;s toe te voegen. Met deze functie kunnen auteurs van inhoud naadloze ervaringen met gegevensvastlegging op sitepagina&#39;s maken met behulp van de kracht van adaptieve formuliercomponenten, zoals dynamisch gedrag, validaties, gegevensintegratie, het genereren van een document van registratie- en bedrijfsprocesautomatisering. U kunt:

   * Maak een adaptief formulier door formuliercomponenten te slepen en neer te zetten op Adaptive Forms Container Component in AEM Sites Editor of Experience Fragments.
   * Met de wizard Adaptive Forms in de AEM Sites-editor kunt u onafhankelijk van elke sitepagina formulieren maken die u de vrijheid geven dergelijke formulieren op meerdere pagina&#39;s opnieuw te gebruiken.
   * Voeg meerdere formulieren toe aan een sitepagina, zodat de gebruikerservaring wordt gestroomlijnd en er meer flexibiliteit wordt geboden.

     >[!VIDEO](https://video.tv.adobe.com/v/3419284?quality=12&learn=on)

* [Adobe Acrobat Sign Solutions for Government](/help/forms/adobe-sign-integration-adaptive-forms.md): AEM Forms is nu geïntegreerd met Adobe Acrobat Sign Solutions voor de regering. Deze integratie biedt een geavanceerd niveau van naleving en beveiliging voor e-handtekeningen met Adaptief formulier-inzendingen voor met de overheid verband houdende rekeningen (overheidsdiensten en agentschappen).

  Dankzij de integratie met Adobe Acrobat Sign Solutions for Government kunnen partners en klanten van de Adobe in Adaptive Forms elektronische handtekeningen gebruiken voor een aantal van de meest bedrijfskritieke en gevoelige bedrijfsonderdelen. Deze extra laag van veiligheid zorgt ervoor dat alle e-handtekeningen volledig volgzaam met de Matige naleving FedRAMP zijn, die de klanten van de overheid van de Adobe van mening voorziet.

* [Verbeterde foutafhandeling met aangepaste fouthandlers in de regeleditor](/help/forms/add-custom-error-handler-adaptive-forms.md): U kunt nu een aangepaste functie (met behulp van de clientbibliotheek) activeren als reactie op een fout die door een externe service is geretourneerd, en eindgebruikers een op maat gemaakte reactie geven. Of u kunt specifieke acties uitvoeren voor fouten die door een service worden geretourneerd. Bijvoorbeeld, kunt u een douanewerkschema in de achtergrond voor specifieke foutencodes aanhalen of de klant informeren dat de dienst neer is.

  Deze functionaliteit verbetert uw algemene fout-behandelend vermogen door op norm-gebaseerde foutenreacties in te voeren die achterwaarts compatibel met OOTB foutenmanagers, met grotere flexibiliteit en controle zijn.

* [Verbeterde verificatiemethoden voor het formuliergegevensmodel](/help/forms/configure-data-sources.md): Ervaar verhoogde veiligheid met de introductie van op clientreferenties gebaseerde verificatie voor het verbinden van AEM Forms met compatibele gegevensbronnen. Deze verbetering elimineert de behoefte aan imitatie of gebruikerslogin, die de bescherming van uw gegevens verstevigt.

* [Adaptieve Forms met herhaalbare secties](/help/forms/create-forms-repeatable-sections.md): U kunt nu maken [Accordeon](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion.html), [Wizard](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard.html), [Deelvenster](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel-container.html), en [Horizontale tabs](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs.html) in een op kerncomponenten gebaseerde adaptieve vorm om herhaalbare secties te maken.

  >[!VIDEO](https://video.tv.adobe.com/v/3421052/adaptive-forms-repeatable-sections-repeat-sections/?quality=12&learn=on)

  Met deze herhaalbare secties kunt u een onbeperkt aantal items opgeven zonder een vast aantal velden. Dit is handig wanneer de vereiste instanties van gegevens vooraf onbekend zijn. Forms-gebruikers kunnen eenvoudig secties toevoegen of verwijderen, waardoor formulieren kunnen worden aangepast aan verschillende scenario&#39;s voor gegevensinvoer en de verzameling van meerdere exemplaren van dezelfde gegevens kan worden vereenvoudigd.

* **[Adaptieve Forms verzenden naar Microsoft® SharePoint en Microsoft® OneDrive](/help/forms/configuring-submit-actions.md)**: Verbeter de flexibiliteit van zakelijke gebruikers, zodat u snel nieuwe formulieren kunt starten en verzonden gegevens kunt opslaan in de dagelijkse tools die ze gebruiken, zoals de Microsoft® SharePoint-site of de OneDrive-map.

### Forms-programma voor vroege adoptie zonder adapter {#forms-early-adopter}

Gebruiken [Forms zonder hoofdadapter](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html) om uw ontwikkelaars in staat te stellen om interactieve formulieren te maken, te publiceren en te beheren die via API&#39;s kunnen worden benaderd en waarmee interactie mogelijk is, in plaats van via een traditionele grafische gebruikersinterface. Met behulp van hoofdloze adaptieve formulieren kunt u:

* multikanaalformulieren van hoge kwaliteit maken in de programmeertaal van uw keuze
* U kunt zelf formulieren integreren in uw bureaublad en mobiele apps, websites en chattoepassingen
* gebruik uw eigen UI-componenten opnieuw met formuliertoepassingen
* de kracht van Adobe Experience Manager Forms gebruiken

U kunt een e-mail verzenden naar `aem-forms-headless@adobe.com` van uw officiële e-mailadres om deel te nemen aan het vroege adoptieprogramma.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U vindt de meest recente opmerkingen in de onderhoudsrelease [hier](/help/release-notes/maintenance/latest.md).

## Cloud Manager {#cloud-manager}

U vindt een volledige lijst met maandreleases van Cloud Manager [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migratiehulpmiddelen {#migration-tools}

U vindt een volledige lijst met de releases van de migratiehulpmiddelen [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
