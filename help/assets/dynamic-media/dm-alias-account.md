---
title: Een Dynamic Media Company-aliasaccount configureren
description: Leer hoe te om een bedrijf aliasrekening in Dynamische Media te vormen.
contentOwner: Rick Brough
topic-tags: administering
content-type: reference
feature: Image Profiles
role: User,Admin
mini-toc-levels: 4
exl-id: 886063d4-71dd-48c8-a342-884ad2c111ca
source-git-commit: 36ab36ba7e14962eba3947865545b8a3f29f6bbc
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

Dynamische media-URL&#39;s en insluitcode van viewer bevatten uw accountnaam van het bedrijf. Deze accountnaam is gemaakt op het moment dat Dynamic Media wordt ingericht. Er kunnen scenario&#39;s zijn waar uw zaken een verwerving, of een herbranding hebben ondergaan, of u eenvoudig een meer memorabele naam wilt gebruiken. In dergelijke gevallen is het niet eenvoudig om de naam van uw bedrijfsaccount handmatig bij te werken in alle URL&#39;s en de insluitcode van de viewer die uit het vak komt. Bovendien is het mogelijk dat u invloed hebt op uw bestaande Dynamic Media-opslagplaats of op live-inhoud. Om dit probleem op te lossen, kunt u een Dynamic Media Company aliasaccount configureren.

Een Dynamic Media Company-aliasaccount zorgt ervoor dat alle updates die in uw zakelijke context worden aangebracht, zoals herbranding, weerspiegelen in de URL&#39;s van dynamische media en de insluitcode van de viewer in de gebruikersinterface. Een aliasaccount heeft ook een positief effect op uw SEO (Search Engine Optimization, optimalisatie van zoekprogramma&#39;s), omdat de URL&#39;s van de dynamische media en de insluitcode van de viewer de nieuwe accountnaam van het bedrijf weerspiegelen.

Houd rekening met het volgende wanneer u een Dynamic Media Company-aliasaccount configureert:

* Om het even welke bestaande Dynamische Media URLs of kijker bedden code op uw *levende* digitale eigenschappen manueel moeten worden bijgewerkt om op de nieuwe aliasnaam te wijzen. URL&#39;s of viewers die code insluiten met de oorspronkelijke naam van het Dynamic Media-bedrijf, blijven echter werken voor bestaande of nieuwe elementen.
* Het aliasaccountvermogen van Dynamic Media Company is beperkt tot de Experience Manager Assets Authoring-modus en -levering. De alias van het bedrijf werkt niet met Experience Manager Sites. De componenten WCM (Web Content Management) worden niet bijgewerkt voor deze wijziging. Die componenten blijven met de originele Dynamische bedrijfsnaam van Media werken voor het halen van Dynamische activa van Media.
* U kunt slechts één bedrijf-aliasaccount instellen op de **[!UICONTROL Edit Dynamic Media Configuration]** -pagina. U kunt echter wel zo veel bedrijfsaliasaccounts maken als een ondersteuningscase en de vereiste aliasnaam handmatig doorgeven in de URL&#39;s van Dynamic Media of de insluitcode van de viewer.
* Het uit-van-de-doos [ vermogen van de Invalidatie van het Geheime voorgeheugen ](/help/assets/dynamic-media/invalidate-cdn-cache-dynamic-media.md) van Dynamische Media maakt URLs met zowel Onderneming als van het Bedrijf Alias rekeningen ongeldig die in de Dynamische pagina van de Configuratie van Media in de Diensten van de Wolk worden gevormd.
* Wanneer u een bedrijf aliasrekening op de **[!UICONTROL Edit Dynamic Media Configuration]** pagina vormt, voor geheim voorgeheugenbevestiging om succesvol te zijn, moet u URLs voor *ongeldig maken zowel* de **[!UICONTROL Company]** rekening als de **[!UICONTROL Company Alias]** rekening, gelijktijdig.

Zie ook [ een Dynamische Configuratie van Media in de Diensten van de Wolk creëren ](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services)

## Een Dynamic Media Company-aliasaccount configureren {#configure-dm-alias-account}

U begint het vormen van een Dynamische het bedrijf aliasrekening van Media door eerst een geval van de Steun voor te leggen. Deze stap is vereist.

1. [ Gebruik Admin Console om een steungeval ](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html) tot stand te brengen.
1. Geef de volgende informatie op in uw ondersteuningsgeval:

   * De aliasnaam van het Dynamic Media-bedrijf die u wilt gebruiken. De naam moet *slechts* brieven bevatten (het gemengde toe te staan casing), aantallen, koppeltekens, en onderstrepingstekens.
   * Uw regio.
   * Of om het even welke [ heersers ](/help/assets/dynamic-media/using-rulesets-to-transform-urls.md) eerder worden gebruikt om het dienen van de Dynamische inhoud van Media door een afwisselende Dynamische naam van de het bedrijfrekening van Media te bereiken.

1. Nadat het alias account van Dynamic Media is gemaakt door Support, selecteert u in de Experience Manager as a Cloud Service Author-instantie het Experience Manager as a Cloud Service-logo voor toegang tot de algemene navigatieconsole.
1. Selecteer links van de console het pictogram Gereedschappen en ga naar **[!UICONTROL Cloud Services > Dynamic Media Configuration]** .
1. Selecteer **[!UICONTROL global]** op de pagina Dynamic Media Configuration Browser in het linkerdeelvenster (selecteer niet het mappictogram links van **[!UICONTROL global]** ). Selecteer vervolgens **[!UICONTROL Edit]** .

   ![ Dynamisch Bedrijf van Media Alias tekstgebied ](/help/assets/assets-dm/dm-company-alias.png)

1. Typ op de pagina **[!UICONTROL Edit Dynamic Media Configuration]** in het tekstveld **[!UICONTROL Company Alias]** de naam van het aliasaccount voor dynamische media die u eerder in het ondersteuningsgeval hebt opgegeven.
1. Selecteer **[!UICONTROL Save]** rechtsboven op de pagina.
Het aliasaccount van het bedrijf Dynamic Media wordt nu opgeslagen en ingeschakeld. Alle URL&#39;s en viewers die code insluiten voor bestaande en nieuwe elementen weerspiegelen nu de nieuwe naam van het bedrijf.