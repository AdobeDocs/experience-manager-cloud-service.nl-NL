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
source-git-commit: 924331ced6a3966a0705dae857f5e7e5af3c9664
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 0%

---

# Informatie over het configureren van een alias-account voor een Dynamic Media-bedrijf {#about-dm-alias-acct}

<!-- hide: yes
hidefromtoc: yes -->

>[!NOTE]
>
>De functie voor het maken van een alias-account voor een Dynamic Media-bedrijf bevindt zich in het Prerelease-kanaal voor januari 2022. De functie is in het algemeen beschikbaar in de release van februari 2022.

Dynamic Media-URL&#39;s en insluitcode voor viewers bevatten uw bedrijfsnaam. Deze accountnaam is gemaakt op het moment dat Dynamic Media de provisioning uitvoert. Er kunnen scenario&#39;s zijn waar uw zaken een verwerving, of een herbranding hebben ondergaan, of u eenvoudig een meer memorabele naam wilt gebruiken. In dergelijke gevallen is het niet eenvoudig om de naam van uw bedrijfsaccount handmatig bij te werken in alle URL&#39;s en de insluitcode van de viewer die uit het vak komt. Bovendien is het mogelijk dat u invloed hebt op uw bestaande Dynamic Media-opslagplaats of op live-inhoud. Om dit probleem op te lossen, kunt u een Dynamic Media-account voor bedrijfsaliassen configureren.

Een Dynamic Media-account voor bedrijfalias zorgt ervoor dat alle updates die in uw zakelijke context zijn aangebracht, zoals herbranding, worden weerspiegeld in alle Dynamic Media-URL&#39;s die buiten de box vallen en in de gebruikersinterface ingesloten code van de viewer. Een aliasaccount heeft ook een positief effect op uw SEO (Search Engine Optimization, optimalisatie van zoekprogramma&#39;s), omdat de Dynamic Media-URL&#39;s en de insluitcode van de viewer de nieuwe accountnaam van het bedrijf weerspiegelen.

Houd rekening met het volgende wanneer u een Dynamic Media-bedrijfsaliasaccount configureert:

* Bestaande Dynamic Media-URL&#39;s of viewerinsluitcode op uw *leven* digitale eigenschappen moeten handmatig worden bijgewerkt om de nieuwe aliasnaam te weerspiegelen. URL&#39;s of viewers die code insluiten met uw oorspronkelijke Dynamic Media-bedrijfsnaam, blijven echter werken voor bestaande of nieuwe elementen.
* De Dynamic Media-mogelijkheden voor aliasaccounts zijn beperkt tot de Experience Manager Assets Authoring-modus en -levering. De alias van het bedrijf werkt niet met Experience Manager Sites. De componenten WCM (Web Content Management) worden niet bijgewerkt voor deze wijziging. Deze componenten werken nog steeds met de oorspronkelijke Dynamic Media-bedrijfsnaam voor het ophalen van Dynamic Media-middelen.
* U kunt slechts één bedrijfsaliasaccount instellen op het tabblad **[!UICONTROL Edit Dynamic Media Configuration]** pagina. U kunt echter wel zoveel aliasaccounts van bedrijven maken als een ondersteuningsgeval en de vereiste aliasnaam handmatig doorgeven in de Dynamic Media URL&#39;s of de insluitcode van de viewer.
* De out-of-the-box [Cache-validatie](/help/assets/dynamic-media/invalidate-cdn-cache-dynamic-media.md) het vermogen van Dynamic Media maakt URLs met zowel Bedrijf als van het Bedrijf Alias rekeningen ongeldig die in de pagina van de Configuratie van Dynamic Media in Cloud Services worden gevormd.
* Wanneer u een bedrijf alias rekening op vormt **[!UICONTROL Edit Dynamic Media Configuration]** pagina, voor geheim voorgeheugenongeldigverklaring om succesvol te zijn, moet u URLs ongeldig maken voor *beide* de **[!UICONTROL Company]** en de **[!UICONTROL Company Alias]** account, gelijktijdig.

Zie ook [Een Dynamic Media-configuratie maken in Cloud Services](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services)

## Een aliasaccount voor een Dynamic Media-bedrijf configureren {#configure-dm-alias-account}

U begint een Dynamic Media-bedrijf aliasaccount te configureren door eerst een Support-case in te dienen. Deze stap is vereist.

1. [Gebruik de Admin Console om een steungeval tot stand te brengen](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html).
1. Geef de volgende informatie op in uw ondersteuningsgeval:

   * De aliasnaam van het Dynamic Media-bedrijf die u wilt gebruiken. De naam moet bevatten *alleen* letters (gebruik van hoofdletters en kleine letters), cijfers, afbreekstreepjes en onderstrepingstekens.
   * Uw regio.
   * Alle [regels](/help/assets/dynamic-media/using-rulesets-to-transform-urls.md) eerder worden gebruikt om Dynamic Media-inhoud te kunnen gebruiken via een andere Dynamic Media-accountnaam.

1. Nadat de Dynamic Media-aliasaccount is gemaakt door Support, selecteert u in de instantie as a Cloud Service auteur van Experience Manager het as a Cloud Service logo van de Experience Manager voor toegang tot de algemene navigatieconsole.
1. Selecteer links van de console het pictogram Gereedschappen en ga naar **[!UICONTROL Cloud Services > Dynamic Media Configuration]**.
1. Selecteer in het linkerdeelvenster van de Dynamic Media Configuration Browser-pagina de optie **[!UICONTROL global]** (selecteer het mappictogram niet links van **[!UICONTROL global]**). Selecteer vervolgens **[!UICONTROL Edit]**.

   ![Dynamic Media Company Alias tekstveld](/help/assets/assets-dm/dm-company-alias.png)

1. Op de **[!UICONTROL Edit Dynamic Media Configuration]** pagina, in de **[!UICONTROL Company Alias]** in het tekstveld typt u de naam van de Dynamic Media-aliasaccount die u eerder in uw ondersteuningsgeval hebt opgegeven.
1. Selecteer in de rechterbovenhoek van de pagina de optie **[!UICONTROL Save]**.
Het aliasaccount van het Dynamic Media-bedrijf wordt nu opgeslagen en ingeschakeld. alle URL&#39;s en insluitcode voor viewers voor bestaande en nieuwe elementen weerspiegelen nu de nieuwe naam van het bedrijf.