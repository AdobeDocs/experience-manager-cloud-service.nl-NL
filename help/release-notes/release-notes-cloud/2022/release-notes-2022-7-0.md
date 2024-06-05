---
title: Opmerkingen bij de release 2022.7.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de release 2022.7.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: b339ab48-e836-4589-a573-9c50917b9280
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '935'
ht-degree: 0%

---

# Opmerkingen bij de release 202278.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de release met functies voor de versie 2022.7.0 van [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van vorige versies vrij te geven, bijvoorbeeld voor de versies in 2020, 2021 enzovoort.

>[!NOTE]
>
>Zie [Recente documentatieupdates](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor meer informatie over documentatie-updates die niet rechtstreeks verband houden met een release.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als [!DNL Cloud Service] huidige release (2022.7.0) is 8 augustus 2022.

De volgende release (2022.8.0) is gepland voor 1 september 2022.

## Video vrijgeven {#release-video}

Bekijk de video Overzicht van de release van juli 2022 voor een overzicht van de functies die in de release van 2022.7.0 zijn toegevoegd:

>[!VIDEO](https://video.tv.adobe.com/v/345409/?quality=12)

## [!DNL Experience Manager Sites] als [!DNL Cloud Service] {#sites}

### Nieuwe functies in [!DNL Sites] {#sites-features}

* De [Console voor inhoudsfragment](/help/sites-cloud/administering/content-fragments/managing.md#content-fragments-console) now supports [sneltoetsen](/help/sites-cloud/administering/content-fragments/keyboard-shortcuts.md).

* AEM als Cloud Service [voor het web geoptimaliseerde afbeeldingslevering](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/web-optimized-image-delivery.html) staat toe om paginasnelheid beduidend te verbeteren door formaten zoals WebP te leveren. Deze nieuwe service biedt ook flexibelere opties voor het vergroten en verkleinen en transformeren van afbeeldingen. Alle versies van de [Component Core Image](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/image.html) laat u deze dienst gebruiken en beelden leveren als WebP door een optie in het beleid van de beeldcomponent te klikken.

* AEM personaliseringsactiviteiten kunnen nu gebruikmaken van ervaringsfragmenten in plaats van onze verouderde aanbiedingen. Deze functie:
   * biedt een migratiepad waarin AEM inhoud ervaringsfragmentaanbiedingen zou bevorderen in plaats van oudere bibliotheekaanbiedingen, zodat op de juiste wijze gevormde inhoud wordt geleverd die zich op de volgende schaaldatum aan de personalisatie aanpast.
   * Hiermee voorkomt u dat auteurs van inhoud per ongeluk ongestileerde inhoud op hun site weergeven.
   * staat het richten wijze van om het even welke component toe om in een ervaringsfragment (zowel JSON als de types van HTML) worden omgezet dat editable malplaatjes gebruikt.

>[!NOTE]
>
>Bestaande verpersoonlijkingsactiviteiten die reeds gebruikmaken van verouderde aanbiedingen, kunnen dit blijven doen, maar nieuwe verpersoonlijkingsactiviteiten moeten worden gecreëerd als ervaringsfragmenten, aangezien dat de aanbevolen aanpak is.

## [!DNL Experience Manager Assets] als [!DNL Cloud Service] {#assets}

### Nieuwe functies beschikbaar in [!DNL Assets] prerelease-kanaal {#prerelease-features-assets}

U kunt nu Adobe Experience Manager Assets configureren voor [het type elementen beperken dat gebruikers kunnen uploaden op basis van het MIME-type](/help/assets/configure-asset-upload-restrictions.md).

![Beperkingen voor het uploaden van middelen](/help/assets/assets/asset-upload-restrictions.png)

## [!DNL Experience Manager Forms] als [!DNL Cloud Service] {#forms}

### Nieuwe functies in [!DNL Forms] {#forms-features}

* **[Ondersteuning voor toetsenbordinvoer voor scripthandtekeningen](/help/forms/signing-forms-using-scribble.md)**: Adaptieve Forms wordt steeds vaker gebruikt op aanraakapparaten en handtekeningen worden vaak ondersteund. Het ondertekenen van documenten op aanraakapparaten is een geaccepteerde manier geworden voor het ondertekenen van formulieren. Adaptive Forms biedt native ondersteuning voor scripthandtekeningen en Adobe Sign voor dergelijke gebruiksgevallen. Nu kunt u, samen met andere reeds ondersteunde opties, ook het toetsenbord gebruiken voor het schrijven van scripts in een adaptief formulier. Het helpt ook toegankelijkheidscompatibiliteit te verbeteren.

![Ondersteuning voor toetsenbordinvoer voor scripthandtekeningen op iPhone](/help/release-notes/assets/scribble-keyboard-mobile.png)

* **De wizard Adaptieve Forms gebruiken in de lokale taal**: U kunt de wizard gebruiken in de taal van uw keuze. Het biedt nu ondersteuning voor alle talen die door Adobe Experience Manager worden ondersteund.

### Nieuwe functies beschikbaar in [!DNL Forms] prerelease-kanaal {#prerelease-features-forms}

<!-- 

* **[Launch Adaptive Form creation wizard from embed form component](/help/forms/using/embed-adaptive-form-aem-sites.md)**: You can now launch Adaptive Form creation wizard from embed form component. It helps improve content and forms authoring workflows for Sites and Forms practitioners trying to add enrollment experiences to a web page. 

![Keyboard input support for Scribble signatures on iphone](/help/release-notes/assets/froms-container.png) 

-->

* **[DDX aanroepen - Een stap voor AEM workflow](/help/forms/aem-forms-workflow-step-reference.md#invokeddx)**: Document Description XML (DDX) is een declaratieve opmaaktaal waarvan de elementen bouwstenen van documenten vertegenwoordigen. Deze bouwstenen omvatten PDF- en XDP-documenten en andere elementen, zoals opmerkingen, bladwijzers en gestileerde tekst. DDX-documenten zijn sjablonen voor de documenten en beschrijven de gewenste kenmerken van brondocumenten die in de resulterende documenten moeten worden weergegeven. Eén DDX kan worden gebruikt met een reeks brondocumenten. U kunt de Invoke stap en de Werkstroom van de AEM gebruiken om diverse verrichtingen uit te voeren, zoals het assembleren van het demonteren van documenten, het creëren van en het wijzigen van Acrobat en XFA Forms, en andere die verrichtingen in [DDX-referentie](https://helpx.adobe.com/content/dam/help/en/experience-manager/forms-cloud-service/ddxRef.pdf) documentatie.

* **[Omzetten in PDF/A - Een stap voor AEM workflow](/help/forms/aem-forms-workflow-step-reference.md##convert-pdfa)**: PDF/A is een archiefindeling voor langdurige bewaring van de inhoud van het document, alle lettertypen worden ingesloten en het bestand wordt niet gecomprimeerd. Nu kunt u met de stap Omzetten in PDF/A en AEM Workflow uw documenten of bestanden in elke indeling converteren naar PDF/A-indeling.


## CIF invoegtoepassing {#cloud-services-cif}

### Nieuwe functies {#what-is-new-cif}

* Verrijking van productcatalogus ondersteunt nu AEM pagina&#39;s. Hierdoor kunnen auteurs pagina - productkoppeling beheren.

* Verschillende CIF Core-componentverbeteringen

### Bugfixes {#bug-fixes-cif}

* Aanmeldingstoken toevoegen aan prijsophaalbewerkingen op de client

* Onjuiste paginacomponent in de datalaag

## [!DNL Experience Manager] als [!DNL Cloud Service] Stichting {#foundation}

### Nieuwe functies {#what-is-new-foundation}

* De [Browser voor opslagplaats](/help/implementing/developing/tools/repository-browser.md) heeft nu een veld voor padinvoer, zodat u rechtstreeks naar een specifieke map in de hiërarchie van de opslagplaats kunt gaan
* SCD (Sling Content Distribution) ondersteunt nu een expliciete &#39;invalidatie&#39;-actie om inhoud ongeldig te maken zonder dat die inhoud wordt gepubliceerd. Zie [Caching in AEM as a Cloud Service](/help/implementing/dispatcher/caching.md#explicit-invalidation) voor meer informatie.
* mod_macro is nu beschikbaar in AEM as a Cloud Service. Zie [deze tabel](/help/implementing/dispatcher/disp-overview.md) voor een lijst met ondersteunde Apache-modules.

### Verbeteringen AEM as a Cloud Service SDK Dispatcher Tools {#dispatcher-tools-enhancements}

* Apache kan worden gestart met `docker_run_hot_reload.sh` script, dat automatisch alle volgende wijzigingen in de configuratie apache en dispatcher laadt en valideert, waardoor de ontwikkelsnelheid wordt verbeterd. Alleen ondersteund voor de flexibele modus van de verzendingsprogramma&#39;s. Zie ook [Fouten opsporen in uw Apache- en Dispatcher-configuratie](/help/implementing/dispatcher/validation-debug.md#automatic-reloading) voor meer informatie over automatisch opnieuw laden en valideren.
* De lokale configuratie van apache/verzender zal veranderingen in wolkenmilieu&#39;s nauwkeuriger volgen, die pariteit tussen de twee milieu&#39;s verhogen.

### Nieuwe functies beschikbaar in [!DNL Experience Manager] prerelease-kanaal {#prerelease-features-foundation}

* AEM as a Cloud Service is nu geïntegreerd met Verenigde Shell om de gebruikerservaring te verbeteren en het met alle andere toepassingen van het Experience Cloud te verenigen. Zie [AEM as a Cloud Service op Verenigde Shell](/help/overview/aem-cloud-service-on-unified-shell.md) voor meer informatie .

## Adobe Learning Manager-connectors {#learn-manage}

* De nieuwe Adobe Learning Manager heeft connectors naar Adobe Experience Manager Sites, Marketo Engage en Adobe Commerce. Zie voor meer informatie: [Adobe Learning Manager-gebruikershandleiding](https://helpx.adobe.com/learning-manager/user-guide.html).

## Cloud Manager {#cloud-manager}

U vindt een volledige lijst met maandreleases van Cloud Manager [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migratiehulpmiddelen {#migration-tools}

U vindt een volledige lijst met de releases van de migratiehulpmiddelen [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
