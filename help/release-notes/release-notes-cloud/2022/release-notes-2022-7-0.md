---
title: Nota's van de versie voor 2022.7.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Nota's van de versie voor 2022.7.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: b339ab48-e836-4589-a573-9c50917b9280
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '935'
ht-degree: 0%

---

# Opmerkingen bij de release 202278.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de versie 2022.7.0 van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van vorige versies vrij te geven, bijvoorbeeld voor de versies in 2020, 2021 enzovoort.

>[!NOTE]
>
>Zie [ Recente Updates van de Documentatie ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor details van documentatieupdates niet direct met een versie verwant.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige release (2022.7.0) is 8 augustus 2022.

De volgende release (2022.8.0) is gepland voor 1 september 2022.

## Video vrijgeven {#release-video}

Bekijk de video Overzicht van de release van juli 2022 voor een overzicht van de functies die in de release van 2022.7.0 zijn toegevoegd:

>[!VIDEO](https://video.tv.adobe.com/v/345409/?quality=12)

## [!DNL Experience Manager Sites] als een [!DNL Cloud Service] {#sites}

### Nieuwe functies in [!DNL Sites] {#sites-features}

* De [ Console van het Fragment van de Inhoud ](/help/sites-cloud/administering/content-fragments/managing.md#content-fragments-console) steunt nu [ toetsenbordkortere weg ](/help/sites-cloud/administering/content-fragments/keyboard-shortcuts.md).

* AEM als Cloud Service [ Web-geoptimaliseerde beeldlevering ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/web-optimized-image-delivery.html) staat toe om paginasnelheid beduidend te verbeteren door formaten zoals WebP te leveren. Deze nieuwe service biedt ook flexibelere opties voor het vergroten en verkleinen en transformeren van afbeeldingen. Alle versies van de [ Component van het Beeld van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/image.html) laten u deze dienst gebruiken en beelden leveren als WebP door de klik van een optie in het beleid van de beeldcomponent.

* AEM personaliseringsactiviteiten kunnen nu gebruikmaken van ervaringsfragmenten in plaats van onze verouderde aanbiedingen. Deze functie:
   * biedt een migratiepad waarin AEM inhoud ervaringsfragmentaanbiedingen zou bevorderen in plaats van oudere bibliotheekaanbiedingen, zodat op de juiste wijze gevormde inhoud wordt geleverd die zich op de volgende schaaldatum aan de personalisatie aanpast.
   * Hiermee voorkomt u dat auteurs van inhoud per ongeluk ongestileerde inhoud op hun site weergeven.
   * staat het richten wijze van om het even welke component toe om in een ervaringsfragment (zowel JSON als de types van HTML) worden omgezet dat editable malplaatjes gebruikt.

>[!NOTE]
>
>Bestaande verpersoonlijkingsactiviteiten die reeds gebruikmaken van verouderde aanbiedingen, kunnen dit blijven doen, maar nieuwe verpersoonlijkingsactiviteiten moeten worden gecreëerd als ervaringsfragmenten, aangezien dat de aanbevolen aanpak is.

## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Nieuwe functies beschikbaar in [!DNL Assets] prereleasekanaal {#prerelease-features-assets}

U kunt Adobe Experience Manager Assets nu vormen om [ het type van activa te beperken die de gebruikers kunnen uploaden gebaseerd op het MIME type ](/help/assets/configure-asset-upload-restrictions.md).

![ Activa uploadt beperkingen ](/help/assets/assets/asset-upload-restrictions.png)

## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

### Nieuwe functies in [!DNL Forms] {#forms-features}

* **[de inputsteun van het Toetsenbord voor Krabbelhandtekeningen](/help/forms/signing-forms-using-scribble.md)**: De adaptieve Forms wordt meer en meer gebruikt op aanrakingsapparaten, en één gemeenschappelijke vereiste is handtekeningen te steunen. Het ondertekenen van documenten op aanraakapparaten is een geaccepteerde manier geworden voor het ondertekenen van formulieren. Adaptive Forms biedt native ondersteuning voor scripthandtekeningen en Adobe Sign voor dergelijke gebruiksgevallen. Nu kunt u, samen met andere reeds ondersteunde opties, ook het toetsenbord gebruiken voor het schrijven van scripts in een adaptief formulier. Het helpt ook toegankelijkheidscompatibiliteit te verbeteren.

![ de inputsteun van het Toetsenbord voor Krabbelhandtekeningen op iPhone ](/help/release-notes/assets/scribble-keyboard-mobile.png)

* **de Aangepaste tovenaar van Forms van het Gebruik in lokale taal**: U kunt de tovenaar in taal van uw keus gebruiken. Het biedt nu ondersteuning voor alle talen die door Adobe Experience Manager worden ondersteund.

### Nieuwe functies beschikbaar in [!DNL Forms] prereleasekanaal {#prerelease-features-forms}

<!-- 

* **[Launch Adaptive Form creation wizard from embed form component](/help/forms/using/embed-adaptive-form-aem-sites.md)**: You can now launch Adaptive Form creation wizard from embed form component. It helps improve content and forms authoring workflows for Sites and Forms practitioners trying to add enrollment experiences to a web page. 

![Keyboard input support for Scribble signatures on iphone](/help/release-notes/assets/froms-container.png) 

-->

* **[roept DDX aan - een stap van het Werkschema van de AEM](/help/forms/aem-forms-workflow-step-reference.md#invokeddx)**: De Beschrijving XML van het document (DDX) is een verklarende prijsverhogingstaal de waarvan elementen bouwstenen van documenten vertegenwoordigen. Deze bouwstenen omvatten PDF- en XDP-documenten en andere elementen, zoals opmerkingen, bladwijzers en gestileerde tekst. DDX-documenten zijn sjablonen voor de documenten en beschrijven de gewenste kenmerken van brondocumenten die in de resulterende documenten moeten worden weergegeven. Eén DDX kan worden gebruikt met een reeks brondocumenten. U kunt de Invoke stap en het Werkschema van de AEM gebruiken om diverse verrichtingen uit te voeren, zoals het assembleren van het demonteren van documenten, het creëren van en het wijzigen van Acrobat en XFA Forms, en andere die verrichtingen in [ worden beschreven DX Verwijzing ](https://helpx.adobe.com/content/dam/help/en/experience-manager/forms-cloud-service/ddxRef.pdf) documentatie.

* **[Bekeerling in PDF/A - een stap van het Werkschema van de AEM](/help/forms/aem-forms-workflow-step-reference.md##convert-pdfa)**: PDF/A is een archiefformaat voor behoud op lange termijn van de inhoud van het document, worden alle doopvonten ingebed en het dossier is niet samengeperst. Nu kunt u met de stap Omzetten in PDF/A en AEM Workflow uw documenten of bestanden in elke indeling converteren naar PDF/A-indeling.


## CIF invoegtoepassing {#cloud-services-cif}

### Nieuwe functies {#what-is-new-cif}

* Verrijking van productcatalogus ondersteunt nu AEM pagina&#39;s. Hierdoor kunnen auteurs pagina - productkoppeling beheren.

* Verschillende CIF Core-componentverbeteringen

### Bugfixes {#bug-fixes-cif}

* Aanmeldingstoken toevoegen aan prijsophaalbewerkingen op de client

* Onjuiste paginacomponent in de datalaag

## [!DNL Experience Manager] als een [!DNL Cloud Service] Foundation {#foundation}

### Nieuwe functies {#what-is-new-foundation}

* Browser van de Bewaarplaats [&#128279;](/help/implementing/developing/tools/repository-browser.md) heeft nu een gebied van de weginput, makend het mogelijk om rechtstreeks aan een specifieke omslag in de bewaarplaatshiërarchie te springen
* SCD (Sling Content Distribution) ondersteunt nu een expliciete &#39;invalidatie&#39;-actie om inhoud ongeldig te maken zonder dat die inhoud wordt gepubliceerd. Zie [ Caching in AEM as a Cloud Service ](/help/implementing/dispatcher/caching.md#explicit-invalidation) pagina voor verdere details.
* mod_macro is nu beschikbaar in AEM as a Cloud Service. Zie [ deze lijst ](/help/implementing/dispatcher/disp-overview.md) voor een lijst van gesteunde modules Apache.

### Verbeteringen in AEM as a Cloud Service SDK Dispatcher Tools {#dispatcher-tools-enhancements}

* Apache kan worden gestart met `docker_run_hot_reload.sh` -script. Hiermee worden alle volgende wijzigingen in de configuratie van apache en dispatcher automatisch geladen en gevalideerd, waardoor de ontwikkelsnelheid wordt verbeterd. Alleen ondersteund voor de flexibele modus van de verzendingsprogramma&#39;s. Ook, zie [ het Zuiveren van uw configuratie Apache en Dispatcher ](/help/implementing/dispatcher/validation-debug.md#automatic-reloading) voor extra details over automatisch herladen en bevestiging.
* De lokale configuratie van apache/verzender zal veranderingen in wolkenmilieu&#39;s nauwkeuriger volgen, die pariteit tussen de twee milieu&#39;s verhogen.

### Nieuwe functies beschikbaar in [!DNL Experience Manager] prereleasekanaal {#prerelease-features-foundation}

* AEM as a Cloud Service is nu geïntegreerd met Verenigde Shell om de gebruikerservaring te verbeteren en het met alle andere toepassingen van het Experience Cloud te verenigen. Zie [ AEM as a Cloud Service op Verenigde Shell ](/help/overview/aem-cloud-service-on-unified-shell.md) voor meer details.

## Adobe Learning Manager-connectors {#learn-manage}

* De nieuwe Adobe Learning Manager heeft connectors naar Adobe Experience Manager Sites, Marketo Engage en Adobe Commerce. Meer leren zie: [ de Gids van de Gebruiker van Adobe Learning Manager ](https://helpx.adobe.com/learning-manager/user-guide.html).

## Cloud Manager {#cloud-manager}

U kunt een volledige lijst van de maandelijkse versies van Cloud Manager [ hier ](/help/implementing/cloud-manager/release-notes/current.md) vinden.

## Migratiehulpmiddelen {#migration-tools}

U kunt een volledige lijst van de versies van Hulpmiddelen van de Migratie [ hier ](/help/journey-migration/release-notes/release-notes-migration-tools-current.md) vinden.
