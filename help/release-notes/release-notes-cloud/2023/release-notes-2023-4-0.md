---
title: Opmerkingen bij de release 2023.4.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de release 2023.4.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: c34aedee-e45a-4e2a-ae7f-930bc0cc026f
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1122'
ht-degree: 0%

---

# Opmerkingen bij de release 2023.4.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de versie 2023.4.0 van [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van eerdere versies, zoals 2021 of 2022, vrij te geven.
>
>Kijk eens naar de [Experience Manager geeft Routekaart vrij](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html) voor meer informatie over de volgende activering van functies voor [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Zie [Recente documentatieupdates](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor meer informatie over documentatie-updates die niet rechtstreeks verband houden met een release.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als [!DNL Cloud Service] huidige release met functies (2023.4.0) is 7 juni 2023. De volgende release met functies (2023.6.0) is gepland voor 29 juni 2023.

## Video vrijgeven {#release-video}

Bekijk de video Overzicht van de release van april 2023 voor een overzicht van de functies die zijn toegevoegd in de release van 2023.4.0:

>[!VIDEO](https://video.tv.adobe.com/v/3418681/?quality=12)

## [!DNL Experience Manager Sites] als [!DNL Cloud Service] {#sites}

### Nieuwe functies in [!DNL Experience Manager Sites] {#sites-features}

* Exporteer inhoudsfragmenten van AEM as a Cloud Service naar Adobe Target in JSON-indeling en maak overeenkomende JSON-aanbiedingen in Target.
* Ondersteuning voor paginering en sortering van GraphQL en verbeteringen in de interne cache helpen nu de prestaties van losgekoppelde clienttoepassingen te verbeteren wanneer u grote inhoudssets ophaalt van AEM met behulp van complexe GraphQL-query&#39;s en -filters.

### Nieuwe functies in [!DNL Experience Manager Sites] prerelease {#prerelease-sites}

* Inhoudsfragmenten en de bijbehorende verwijzingen kunnen nu worden gepubliceerd naar de [AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-environments.html#access-preview-service) met de [Console voor inhoudsfragment](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/content-fragments/content-fragments-console.html), zodat gebruikers een voorvertoning van de uiteindelijke ervaring kunnen bekijken in een ontkoppelde voorvertoningstoepassing voordat ze live gaan.
* Afbeeldingen kunnen nu dynamisch worden geoptimaliseerd voor weergave op het web in scenario&#39;s zonder kop met AEM GraphQL. [Query-variabelen](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/images.html#query-variables) kan worden gedefinieerd in GraphQL-query&#39;s zodat ontkoppelde clienttoepassingen aangepaste geoptimaliseerde afbeeldingen van AEM kunnen aanvragen.
* Labels op [Variaties in inhoudsfragment](https://experienceleague.adobe.com/docs/experience-manager-65/assets/content-fragments/content-fragments-variations.html) kan nu worden uitgevoerd naar JSON met behulp van de AEM GraphQL-API voor het leveren van inhoud.

## [!DNL Experience Manager Assets] als [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#assets-features}

* Extra ondersteuning voor WebP-afbeeldingen om automatisch metagegevens te extraheren, miniaturen en aangepaste uitvoeringen te genereren. De functie Slimme tags wordt nu ook ondersteund voor deze bestanden. Dynamic Media-mogelijkheden worden niet ondersteund voor WebP als invoerindeling.

* [Verbeterde zoekervaring](/help/assets/search-assets.md#aftersearch) - U kunt nu snel de volgende bewerkingen uitvoeren op de elementen die in de zoekresultaten worden weergegeven:

   * Een workflow maken
   * Een versie maken
   * Relatieve of niet-gerelateerde elementen

     U hoeft niet naar de middelenlocatie te navigeren en de eigenschappen ervan te bekijken om deze bewerkingen uit te voeren.

* Verbeteringen in de gebruiksvriendelijkheid van Color Search facet - Invoerveld voor kleurwaarden kan nu worden bewerkt en zoekresultaten worden alleen bijgewerkt wanneer u de kleurkiezer afsluit.

* Nieuwe protocolondersteuning gestart (DASH - Dynamic Adaptive Streaming via HTTP) voor Adaptive streaming in Dynamic Media-video (met CMAF ingeschakeld):
   * Adaptief streamen (DASH/HLS) zorgt voor een betere kijkervaring voor video&#39;s
   * DASH is het internationale standaardprotocol voor adaptieve videostreaming en wordt op grote schaal toegepast in de branche
   * Beschikbaar in alle regio&#39;s, in te schakelen via een ondersteuningsticket

* Dynamic Media _Opname_ - Experimenteer met testafbeeldingen of Dynamic Media-URL&#39;s om de uitvoer van verschillende afbeeldingsmodifiers te bekijken en de optimalisaties voor Smart Imaging voor de bestandsgrootte (met WebP- en AVIF-levering), de netwerkbandbreedte en de pixelverhouding van het apparaat te beoordelen. Zie [Dynamic Media-momentopname](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-snapshot.html).

### Functie in [!DNL Assets] prerelease {#prerelease-feature-assets}

* Dynamic Media - De gebruikersinterface voor bepaalde velden met betrekking tot Slim uitsnijden in een afbeeldingsprofiel wordt nu bijgewerkt met de huidige richtlijnen voor het definiëren van een slim uitsnijden. Zie [Opties voor uitsnijden](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/image-profiles.html#crop-options).

## [!DNL Experience Manager Forms] als [!DNL Cloud Service] {#forms}

### Nieuwe functies beschikbaar in [!DNL Forms] {#new-features-available-in-channel}

* **[Adaptieve Forms verzenden naar Microsoft® SharePoint en Microsoft® OneDrive](/help/forms/configuring-submit-actions.md)**: Verbeter de flexibiliteit van zakelijke gebruikers, zodat u snel nieuwe formulieren kunt starten en verzonden gegevens kunt opslaan in de dagelijkse tools die ze gebruiken, zoals de Microsoft® SharePoint-site of de OneDrive-map.

### Functies in [!DNL Forms] prerelease {#prerelease-features-forms}

* [Adaptieve Forms in AEM paginaeditor](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md): U kunt nu AEM Pagina-editor gebruiken om snel meerdere formulieren te maken en aan uw sitepagina&#39;s toe te voegen. Met deze functie kunnen auteurs van inhoud naadloze ervaringen met gegevensvastlegging op sitepagina&#39;s maken met behulp van de kracht van adaptieve formuliercomponenten, zoals dynamisch gedrag, validaties, gegevensintegratie, het genereren van een document van registratie- en bedrijfsprocesautomatisering. U kunt:

   * Maak een adaptief formulier door formuliercomponenten te slepen en neer te zetten op Adaptive Forms Container Component in AEM Sites Editor of Experience Fragments.
   * Met de wizard Adaptive Forms in de AEM Sites-editor kunt u onafhankelijk van elke sitepagina formulieren maken die u de vrijheid geven dergelijke formulieren op meerdere pagina&#39;s opnieuw te gebruiken.
   * Voeg meerdere formulieren toe aan een sitepagina, zodat de gebruikerservaring wordt gestroomlijnd en er meer flexibiliteit wordt geboden.

     >[!VIDEO](https://video.tv.adobe.com/v/3419284?quality=12&learn=on)

* [Adobe Acrobat Sign Solutions for Government](/help/forms/adobe-sign-integration-adaptive-forms.md): AEM Forms is nu geïntegreerd met Adobe Acrobat Sign Solutions voor de regering. Deze integratie biedt een geavanceerd niveau van naleving en beveiliging voor e-handtekeningen met Adaptief formulier-inzendingen voor met de overheid verband houdende rekeningen (overheidsdiensten en agentschappen).

  Dankzij de integratie met Adobe Acrobat Sign for Government kunnen partners en klanten van de Adobe in Adaptive Forms elektronische handtekeningen gebruiken voor een aantal van de meest bedrijfskritieke en gevoelige bedrijfsonderdelen. Deze extra laag van veiligheid zorgt ervoor dat alle e-handtekeningen volledig volgzaam met de Matige naleving FedRAMP zijn, die de klanten van de overheid van de Adobe van mening voorziet.

* Verbeterde foutafhandeling met aangepaste fouthandlers in de regeleditor: u kunt nu een aangepaste functie aanroepen (met behulp van de clientbibliotheek) als reactie op een fout die door een externe service is geretourneerd, en eindgebruikers een op maat gemaakte reactie geven. Of u kunt specifieke acties uitvoeren voor fouten die door een service worden geretourneerd. Bijvoorbeeld, kunt u een douanewerkschema in de achtergrond voor specifieke foutencodes aanhalen of de klant informeren dat de dienst neer is.

  Deze functionaliteit verbetert uw algemene fout-behandelend vermogen door op norm-gebaseerde foutenreacties in te voeren die achterwaarts compatibel met OOTB foutenmanagers, met grotere flexibiliteit en controle zijn.

### Forms-programma voor vroege adoptie zonder adapter {#forms-early-adopter}

Gebruik Headless Adaptive Forms om uw ontwikkelaars in staat te stellen interactieve formulieren te maken, te publiceren en te beheren die via API&#39;s kunnen worden geopend en gebruikt in plaats van via een traditionele grafische gebruikersinterface. Met behulp van hoofdloze adaptieve formulieren kunt u:

* multikanaalformulieren van hoge kwaliteit maken in de programmeertaal van uw keuze
* U kunt zelf formulieren integreren in uw bureaublad en mobiele apps, websites en chattoepassingen
* gebruik uw eigen UI-componenten opnieuw met formuliertoepassingen
* de kracht van Adobe Experience Manager Forms gebruiken

U kunt een e-mail verzenden naar `aem-forms-headless@adobe.com` van uw officiële e-mailadres om deel te nemen aan het vroege adoptieprogramma.

## [!DNL Experience Manager] als [!DNL Cloud Service] Stichting {#foundation}

### Nieuwe functies {#what-is-new-foundation}

* Extra publicatieregio&#39;s: klanten van sites kunnen maximaal drie publicatiegebieden in licentie geven, naast het primaire gebied. Het verkeer wordt verpletterd aan extra te publiceren landbouwbedrijven, die in verminderde latentie voor bepaalde verzoeken, en verhoogde veerkracht tegen regionale stroomonderbrekingen resulteren. Neem contact op met de accountmanager van de Adobe voor informatie over licenties [Aanvullende publicatieregio&#39;s](/help/operations/additional-publish-regions.md) voor uw programma&#39;s.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U vindt de meest recente opmerkingen in de onderhoudsrelease [hier](/help/release-notes/maintenance/latest.md).

## Cloud Manager {#cloud-manager}

U vindt een volledige lijst met maandreleases van Cloud Manager [hier.](/help/implementing/cloud-manager/release-notes/current.md)

## Migratiehulpmiddelen {#migration-tools}

U vindt een volledige lijst met de releases van de migratiehulpmiddelen [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
