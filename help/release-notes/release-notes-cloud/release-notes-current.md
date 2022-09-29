---
title: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service.
description: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: e59e5e79bfcdd19e159aadd4ed9567dfe624b21e
workflow-type: tm+mt
source-wordcount: '626'
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

De releasedatum van [!DNL Adobe Experience Manager] als [!DNL Cloud Service] huidige release (2022.8.0) is 1 september 2022.
De volgende release (2022.9.0) is gepland voor 13 oktober 2022.

## Video vrijgeven {#release-video}

Bekijk de video Overzicht van de release van augustus 2022 voor een overzicht van de functies die in de release van 2022.8.0 zijn toegevoegd:

>[!VIDEO](https://video.tv.adobe.com/v/346608/?quality=12)

## [!DNL Experience Manager Sites] als [!DNL Cloud Service] {#sites}

### Nieuwe functies in [!DNL Sites] {#sites-features}

* Met de E-mailcomponent kunt u inhoud maken in AEM die vervolgens als e-mails via Campaign Classic wordt bezorgd. De Core Email Component:
   * is gebaseerd op de [Core WCM-component](https://github.com/adobe/aem-core-wcm-components) die Bewerkbare sjablonen en het Stijlsysteem ondersteunt.
   * biedt tien voor e-mail geoptimaliseerde componenten voor productie (pagina, container, titel, tekst, afbeelding, knop, taser, Experience Fragment, Content Fragment, Segmentatie).
   * biedt dankzij de [invoeging van campagnevariabelen](https://github.com/adobe/aem-core-email-components/wiki/RTE-Personalization) op de meeste dialooggebieden en op de flexibele [Segmenteringscomponent](https://github.com/adobe/aem-core-email-components/wiki/Segmentation-component-(Technical-Documentation)).
   * biedt optimale e-mailvriendelijke HTML-uitvoer dankzij de [CSS-stijlen inliner](https://github.com/adobe/aem-core-email-components/wiki/HTML-Inliner:-Technical-documentation)de [HTML-kenmerkinliner](https://github.com/adobe/aem-core-email-components/wiki/HTML-Inliner:-Technical-documentation)en de [HTML-ontsmettingsmiddel](https://github.com/adobe/aem-core-email-components/wiki/HTML-sanitizing:-Technical-documentation).
   * Hiermee kunt u overal e-mails maken.

### Nieuwe functies beschikbaar in [!DNL Sites] prerelease-kanaal {#prerelease-features-sites}

* De [Console voor inhoudsfragment](/help/sites-cloud/administering/content-fragments/content-fragments-console.md) biedt gebruikers een optie voor het weergeven van het totale aantal taalkopieën dat aan een inhoudsfragment is gekoppeld. Er is 1-klik toegang beschikbaar om ook alle taalkopieën weer te geven. Gebruikers kunnen de tabelweergave ook filteren op de landinstelling van hun interesse.

![Talen voor inhoudsfragmenten](/help/release-notes/assets/cfconsole-languages.png)

## [!DNL Experience Manager Assets] als [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#features-assets}

* U kunt nu Adobe Experience Manager Assets configureren voor [het type elementen beperken dat gebruikers kunnen uploaden op basis van het MIME-type](/help/assets/configure-asset-upload-restrictions.md).

   ![Beperkingen voor het uploaden van middelen](/help/assets/assets/asset-upload-restrictions.png)

## [!DNL Experience Manager Forms] als [!DNL Cloud Service] {#forms}

### Nieuwe functies beschikbaar in [!DNL Forms] prerelease-kanaal {#prerelease-features-forms}

* [Adaptieve Forms-wizard](/help/forms/creating-adaptive-form.md): AEM Forms biedt een gebruiksvriendelijke wizard die Adaptive Forms snel ontwikkelt. De wizard beschikt over een snelle tabnavigatie waarmee u eenvoudig vooraf geconfigureerde sjablonen, stijlen, velden en verzendopties kunt selecteren om een adaptief formulier te maken. Deze release biedt de wizard de volgende verbeteringen:

   * Selecteer of deselecteer velden: Met de wizard kunt u een adaptief formulier maken op basis van JSON- en formuliergegevensmodelschema&#39;s. U kunt nu een subset van velden in een schema selecteren en opnemen in een adaptief formulier. De geselecteerde velden worden geconverteerd naar overeenkomstige componenten voor het vastleggen van adaptieve formuliergegevens om snel de gewenste adaptieve formulieren te maken.

   * Statische sjablonen gebruiken: Klanten met bestaande investeringen in verouderde statische sjablonen kunnen hun reis naar cloudacceptatie voortzetten door statische sjablonen in wizard te gebruiken om adaptieve formulieren te maken. Dit geeft klanten extra tijd om oude statische sjablonen te migreren naar moderne bewerkbare sjablonen.

* [Verborgen velden verwijderen uit een Document of Record (DoR) tijdens verwerking op de server](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md): U kunt het document met record PDF voor eindgebruikers genereren met alleen die velden die voor hen zichtbaar waren tijdens het vastleggen van gegevens. Bij het verzenden van het formulier controleert de server welke velden op basis van verzonden gegevens verborgen waren voor de eindgebruiker en sluit deze velden uit van het document met het oog op consistentie.

## CIF-invoegtoepassing {#cloud-services-cif}

### Nieuwe functies {#what-is-new-cif}

* Koppeling van AEM pagina&#39;s naar producten en categorieën via AEM pagina-eigenschappen plus overzicht in de cockpit van het product
   ![productcockpit page association](/help/assets/CIF/product_cockpit_page_association.png)

## Cloud Manager {#cloud-manager}

U vindt een volledige lijst met maandreleases van Cloud Manager [hier](/help/implementing/cloud-manager/release-notes-cloud-manager/release-notes-cm-current.md).

## Migratiehulpmiddelen {#migration-tools}

U kunt een volledige lijst vinden van de versies van de Hulpmiddelen van de Migratie [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
