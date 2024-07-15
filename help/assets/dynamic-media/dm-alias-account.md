---
title: Een alias-account voor een Dynamic Media-bedrijf configureren
description: Leer hoe u een bedrijf-aliasaccount in Dynamic Media configureert.
contentOwner: Rick Brough
topic-tags: administering
content-type: reference
feature: Image Profiles
role: User,Admin
mini-toc-levels: 4
exl-id: 886063d4-71dd-48c8-a342-884ad2c111ca
source-git-commit: f7525b6b37e486a53791c2331dc6000e5248f8af
workflow-type: tm+mt
source-wordcount: '645'
ht-degree: 0%

---

# Informatie over het configureren van een alias-account voor een Dynamic Media-bedrijf {#about-dm-alias-acct}

<!-- hide: yes
hidefromtoc: yes -->

<!-- >[!NOTE]
>
>This feature to create a Dynamic Media company alias account is in the Prerelease Channel for January 2022. See [Prerelease Channel documentation](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=en#enable-prerelease) for information on how to enable the feature for your environment. The feature is generally available in the February 2022 release. -->

Dynamic Media-URL&#39;s en insluitcode voor viewers bevatten uw bedrijfsnaam. Deze accountnaam is gemaakt op het moment dat Dynamic Media de provisioning uitvoert. Er kunnen scenario&#39;s zijn waar uw zaken een verwerving, of een herbranding hebben ondergaan, of u eenvoudig een meer memorabele naam wilt gebruiken. In dergelijke gevallen is het niet eenvoudig om de naam van uw bedrijfsaccount handmatig bij te werken in alle URL&#39;s en de insluitcode van de viewer die uit het vak komt. Bovendien is het mogelijk dat u invloed hebt op uw bestaande Dynamic Media-opslagplaats of op live-inhoud. Om dit probleem op te lossen, kunt u een Dynamic Media-account voor bedrijfsaliassen configureren.

Een Dynamic Media-account voor bedrijfalias zorgt ervoor dat alle updates die in uw zakelijke context zijn aangebracht, zoals herbranding, worden weerspiegeld in alle Dynamic Media-URL&#39;s die buiten de box vallen en in de gebruikersinterface ingesloten code van de viewer. Een aliasaccount heeft ook een positief effect op uw SEO (Search Engine Optimization, optimalisatie van zoekprogramma&#39;s), omdat de Dynamic Media-URL&#39;s en de insluitcode van de viewer de nieuwe accountnaam van het bedrijf weerspiegelen.

Houd rekening met het volgende wanneer u een Dynamic Media-bedrijfsaliasaccount configureert:

* Om het even welke bestaande Dynamic Media URLs of kijker bedden code op uw *levende* digitale eigenschappen moet manueel worden bijgewerkt om op de nieuwe aliasnaam te wijzen. URL&#39;s of viewers die code insluiten met uw oorspronkelijke Dynamic Media-bedrijfsnaam, blijven echter werken voor bestaande of nieuwe elementen.
* De Dynamic Media-mogelijkheden voor aliasaccounts zijn beperkt tot de Experience Manager Assets Authoring-modus en -levering. De alias van het bedrijf werkt niet met Experience Manager Sites. De componenten WCM (Web Content Management) worden niet bijgewerkt voor deze wijziging. Deze componenten werken nog steeds met de oorspronkelijke Dynamic Media-bedrijfsnaam voor het ophalen van Dynamic Media-middelen.
* U kunt slechts één bedrijf-aliasaccount instellen op de **[!UICONTROL Edit Dynamic Media Configuration]** -pagina. U kunt echter wel zoveel aliasaccounts van bedrijven maken als een ondersteuningsgeval en de vereiste aliasnaam handmatig doorgeven in de Dynamic Media URL&#39;s of de insluitcode van de viewer.
* Het uit-van-de-doos [ vermogen van de Invalidatie van het Geheime voorgeheugen ](/help/assets/dynamic-media/invalidate-cdn-cache-dynamic-media.md) van Dynamic Media maakt URLs met zowel Onderneming als van het Bedrijf Alias rekeningen ongeldig die in de pagina van de Configuratie van Dynamic Media in Cloud Servicen worden gevormd.
* Wanneer u een bedrijf aliasrekening op de **[!UICONTROL Edit Dynamic Media Configuration]** pagina vormt, voor geheim voorgeheugenbevestiging om succesvol te zijn, moet u URLs voor *ongeldig maken zowel* de **[!UICONTROL Company]** rekening als de **[!UICONTROL Company Alias]** rekening, gelijktijdig.

Zie ook [ een Configuratie van Dynamic Media in Cloud Servicen ](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services) creëren

## Een aliasaccount voor een Dynamic Media-bedrijf configureren {#configure-dm-alias-account}

U begint een Dynamic Media-bedrijf aliasaccount te configureren door eerst een Support-case in te dienen. Deze stap is vereist.

1. [ Gebruik de Admin Console om een steungeval ](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html) tot stand te brengen.
1. Geef de volgende informatie op in uw ondersteuningsgeval:

   * De aliasnaam van het Dynamic Media-bedrijf die u wilt gebruiken. De naam moet *slechts* brieven bevatten (het gemengde toe te staan casing), aantallen, koppeltekens, en onderstrepingstekens.
   * Uw regio.
   * Of om het even welke [ heersers ](/help/assets/dynamic-media/using-rulesets-to-transform-urls.md) eerder worden gebruikt om het dienen van de inhoud van Dynamic Media door een afwisselende naam van de het bedrijfrekening van Dynamic Media te bereiken.

1. Nadat de Dynamic Media-aliasaccount is gemaakt door Support, selecteert u in de Experience Manager as a Cloud Service auteur het as a Cloud Service logo van de Experience Manager voor toegang tot de algemene navigatieconsole.
1. Selecteer links van de console het pictogram Gereedschappen en ga naar **[!UICONTROL Cloud Services > Dynamic Media Configuration]** .
1. Selecteer **[!UICONTROL global]** op de pagina Dynamic Media Configuration Browser in het linkerdeelvenster (selecteer niet het mappictogram links van **[!UICONTROL global]** ). Selecteer vervolgens **[!UICONTROL Edit]** .

   ![ Dynamic Media Company Alias tekstgebied ](/help/assets/assets-dm/dm-company-alias.png)

1. Typ op de pagina **[!UICONTROL Edit Dynamic Media Configuration]** in het tekstveld **[!UICONTROL Company Alias]** de naam van de Dynamic Media-aliasaccount die u eerder in het ondersteuningsgeval hebt opgegeven.
1. Selecteer **[!UICONTROL Save]** rechtsboven op de pagina.
Het aliasaccount van het Dynamic Media-bedrijf wordt nu opgeslagen en ingeschakeld. Alle URL&#39;s en in de viewer ingesloten code voor bestaande en nieuwe elementen weerspiegelen nu de nieuwe naam van het bedrijf.