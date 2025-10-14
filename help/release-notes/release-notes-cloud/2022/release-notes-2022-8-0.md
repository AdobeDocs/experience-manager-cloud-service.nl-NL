---
title: Nota's van de versie voor 2022.8.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Nota's van de versie voor 2022.8.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: 0eff8100-5990-4553-8373-445fb7e6fb27
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '604'
ht-degree: 0%

---

# Opmerkingen bij de release 2022.8.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de versie 2022.8.0 van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van vorige versies vrij te geven, bijvoorbeeld voor de versies in 2020, 2021 enzovoort.

>[!NOTE]
>
>Zie [&#x200B; Recente Updates van de Documentatie &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=nl-NL) voor details van documentatieupdates niet direct met een versie verwant.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige release (2022.8.0) is 1 september 2022.
De volgende release (2022.10.0) is gepland voor 10 november 2022.

## Video vrijgeven {#release-video}

Bekijk de video Overzicht van de release van augustus 2022 voor een overzicht van de functies die in de release van 2022.8.0 zijn toegevoegd:

>[!VIDEO](https://video.tv.adobe.com/v/346608/?quality=12)

## [!DNL Experience Manager Sites] als een [!DNL Cloud Service] {#sites}

### Nieuwe functies in [!DNL Sites] {#sites-features}

* Met de E-mailcomponent kunt u inhoud maken in AEM die vervolgens als e-mails via Campaign Classic wordt bezorgd. De Core Email Component:
   * is gebaseerd op de [&#x200B; Component van WCM van de Kern &#x200B;](https://github.com/adobe/aem-core-wcm-components) die Bewerkbare Malplaatjes en het Systeem van de Stijl steunt.
   * biedt tien voor e-mail geoptimaliseerde componenten voor productie (pagina, container, titel, tekst, afbeelding, knop, taser, Experience Fragment, Content Fragment, Segmentatie).
   * verstrekt geavanceerde verpersoonlijking en segmentatie, dankzij de [&#x200B; toevoeging van de variabelen van de Campagne &#x200B;](https://github.com/adobe/aem-core-email-components/wiki/RTE-Personalization) op de meeste dialooggebieden, en aan de flexibele [&#x200B; component van de Segmentatie &#x200B;](https://github.com/adobe/aem-core-email-components/wiki/Segmentation-component-(Technical-Documentation)).
   * verstrekt optimale e-mail-vriendelijke HTML output, dankzij de [&#x200B; CSS stijlen inliner &#x200B;](https://github.com/adobe/aem-core-email-components/wiki/HTML-Inliner:-Technical-documentation), de [&#x200B; inliner van het attribuut van de HTML &#x200B;](https://github.com/adobe/aem-core-email-components/wiki/HTML-Inliner:-Technical-documentation), en [&#x200B; HTML sanitizer &#x200B;](https://github.com/adobe/aem-core-email-components/wiki/HTML-sanitizing:-Technical-documentation).
   * maakt het mogelijk om overal e-mails te maken.

### Nieuwe functies beschikbaar in [!DNL Sites] prereleasekanaal {#prerelease-features-sites}

* De [&#x200B; Console van het Fragment van de Inhoud &#x200B;](/help/sites-cloud/administering/content-fragments/managing.md#content-fragments-console) voorziet gebruikers van een optie om het totale aantal taalexemplaren te tonen verbonden aan een inhoudsfragment. Er is 1-klik toegang beschikbaar om ook alle taalkopieën weer te geven. Gebruikers kunnen de tabelweergave ook filteren op de landinstelling van hun interesse.

![&#x200B; de Talen van de Fragmenten van de Inhoud &#x200B;](/help/release-notes/assets/cfconsole-languages.png)

## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#features-assets}

* U kunt Adobe Experience Manager Assets nu vormen om [&#x200B; het type van activa te beperken die de gebruikers kunnen uploaden gebaseerd op het MIME type &#x200B;](/help/assets/configure-asset-upload-restrictions.md).

  ![&#x200B; Activa uploadt beperkingen &#x200B;](/help/assets/assets/asset-upload-restrictions.png)

## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

### Nieuwe functies beschikbaar in [!DNL Forms] prereleasekanaal {#prerelease-features-forms}

* [&#x200B; Aangepaste tovenaar van Forms &#x200B;](/help/forms/creating-adaptive-form.md): AEM Forms verstrekt zaken gebruikersvriendelijke tovenaar aan snel auteur Aangepaste Forms. De wizard beschikt over een snelle tabnavigatie waarmee u eenvoudig vooraf geconfigureerde sjablonen, stijlen, velden en verzendopties kunt selecteren om een adaptief formulier te maken. Deze release biedt de wizard de volgende verbeteringen:

   * Velden selecteren of deselecteren: met de wizard kunt u een adaptief formulier maken op basis van JSON- en formuliergegevensmodelschema&#39;s. U kunt nu een subset van velden in een schema selecteren en opnemen in een adaptief formulier. De geselecteerde velden worden geconverteerd naar overeenkomstige componenten voor het vastleggen van adaptieve formuliergegevens om snel de gewenste adaptieve formulieren te maken.

   * Statische sjablonen gebruiken: klanten met bestaande investeringen in verouderde statische sjablonen kunnen doorgaan met het toepassen van de cloud door statische sjablonen te gebruiken in de wizard voor het schrijven van adaptieve formulieren. Dit geeft klanten extra tijd om oude statische sjablonen te migreren naar moderne bewerkbare sjablonen.

* [&#x200B; verwijder verborgen gebieden uit een Document van Verslag (DoR) terwijl server-zijverwerking &#x200B;](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md): U kunt het document van verslag PDF voor eind produceren die slechts die gebieden bevatten die aan hen tijdens de ervaring van de gegevensvangst zichtbaar waren. Bij het verzenden van het formulier controleert de server welke velden aan de gebruiker zijn verborgen op basis van verzonden gegevens en sluit deze voor consistentie uit van het document van de record.

## CIF invoegtoepassing {#cloud-services-cif}

### Nieuwe functies {#what-is-new-cif}

* Koppeling van AEM pagina&#39;s naar producten en categorieën via AEM pagina-eigenschappen plus overzicht in de cockpit van het product
  ![&#x200B; de paginakoppeling van de productcockpit &#x200B;](/help/assets/CIF/product_cockpit_page_association.png)

## Cloud Manager {#cloud-manager}

U kunt een volledige lijst van de maandelijkse versies van Cloud Manager [&#x200B; hier &#x200B;](/help/implementing/cloud-manager/release-notes/current.md) vinden.

## Migratiehulpmiddelen {#migration-tools}

U kunt een volledige lijst van de versies van Hulpmiddelen van de Migratie [&#x200B; hier &#x200B;](/help/journey-migration/release-notes/release-notes-migration-tools-current.md) vinden.
