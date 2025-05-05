---
title: Nota's van de versie voor 2022.1.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Nota's van de versie voor 2022.1.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: 1c40ab67-8fd7-4f29-b8c9-dd98b6d5b490
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1065'
ht-degree: 0%

---

# Opmerkingen bij de release 2022.1.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de versie 2022.1.0 van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van vorige versies vrij te geven, bijvoorbeeld voor de versies in 2020, 2021 enzovoort.

>[!NOTE]
>
>Zie [ Recente Updates van de Documentatie ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=nl-NL) voor details van documentatieupdates niet direct met een versie verwant.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige release (2022.1.0) is 3 februari 2022.
De volgende release (2022.3.0) is op 31 maart 2022.

## Video vrijgeven {#release-video}

Heb een blik bij de [ Januari 2022 het Overzicht van de Versie ](https://video.tv.adobe.com/v/340120) video voor een samenvatting van de eigenschappen die in de versie 2022.1.0 worden toegevoegd.

## Adobe Experience Manager Sites as a Cloud Service {#sites}

* **[laat Voorste knoop van de Pijl van het Eind toe](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md)** is beschikbaar in het **spoor van de Plaats** van de console van Plaatsen voor plaatsen die v2 van de Component van de Kern van de Pagina gebruiken. Deze knoop vormt de plaats om de thema&#39;s te laden die met de Voorste Pijpleiding van het Eind bovenop de bestaande cliëntbibliotheken worden opgesteld.

## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#assets-features}

* [!DNL Dynamic Media] - U kunt nu AEM Dynamic Media-interface gebruiken om Algemene instellingen en Publish Setup te configureren in plaats van de Dynamic Media Classic-bureaubladtoepassing te doorlopen.

* [!DNL Dynamic Media] ondersteunt nu opname, voorvertoning, afspelen en publiceren voor MXF-video&#39;s. Annotatie en verbluffende video voor MXF-video&#39;s worden nog niet ondersteund.

* Nadat u een verbinding tussen externe DAM- en Sites-implementaties hebt geconfigureerd, worden de middelen op externe DAM beschikbaar gesteld op de implementatie van Sites. U kunt de [ update nu uitvoeren, schrappen, hernoemen, en bewegingsverrichtingen ](/help/assets/use-assets-across-connected-assets-instances.md) op de verre activa DAM of de omslagen anders. De updates zijn, met wat vertraging, automatisch beschikbaar op de plaatsing van Plaatsen.

### Nieuwe functies in het [!DNL Assets] pre-releasekanaal {#assets-prerelease-features}

* [!DNL AEM Dynamic Media] verstrekt nu de flexibiliteit om [ één alias rekening ](/help/assets/dynamic-media/dm-alias-account.md) in het gebruikersinterface te vormen, daardoor het verzekeren van uit-van-de-doos Dynamic Media URLs en de Kijker bedt code wordt bijgewerkt. Dit heeft een positieve invloed op SEO om de updates te weerspiegelen die zijn aangebracht in uw zakelijke context, zoals herbranding.

* U kunt nu de gebruikersinterface van [!DNL Experience Manager Assets] gebruiken om:

   * Configureer de detectie van dubbele elementen in een opslagplaats.

   * Configureer het toevoegen van digitale watermerken aan afbeeldingen.

* De beheerders kunnen nu de e-mailservice configureren voor grote downloads. Het staat de gebruikers toe om [ e-mailberichten voor grote downloads ](/help/assets/download-assets-from-aem.md#enable-email-notifications-for-large-downloads) van de [!DNL Experience Manager Assets] interface toe te laten. De gebruiker ontvangt een e-mailbericht met de downloadkoppeling van de gearchiveerde ZIP-map na voltooiing van het downloadproces.


* [ leidt de eigenschap van de Publicatie ](/help/assets/manage-publication.md) wordt verbeterd met een beter gebruikersinterface. De gebruikers kunnen inhoud publiceren of unpublish aan en van de geselecteerde bestemming, [ toevoegen Inhoud ](/help/assets/manage-publication.md#add-content) aan de het publiceren lijst van over de bewaarplaats DAM, [ omvatten de Montages van de Omslag ](/help/assets/manage-publication.md#include-folder-settings) om inhoud van de geselecteerde omslagen te publiceren en filters toe te passen, en [ plannen het publiceren ](/help/assets/manage-publication.md#publish-assets-later) aan een recentere datum of een tijd.

### Opgeloste problemen {#bug-fixes}

* Niet-verwerkte middelen zonder oorspronkelijke uitvoering worden naar de Asset compute verzonden voor verwerking terwijl de middelen van AEM on-premise naar cloudservices worden gemigreerd.

## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

### Nieuwe functies in [!DNL Forms] {#what-is-new-forms}

* **[!DNL AEM Forms as a Cloud Service - Communications]**: [ Communicatie APIs ](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/using-communications/aem-forms-cloud-service-communications.html?lang=nl-NL) hulp u een malplaatje en de gegevens van XML combineert om drukdocumenten in diverse formaten te produceren. Met de service kunt u documenten genereren in synchrone modus en in batchmodus. Met de API&#39;s kunt u toepassingen maken waarmee u:

   * Genereer documenten door sjabloonbestanden te vullen met XML-gegevens.
   * Formulieren genereren in verschillende indelingen, waaronder niet-interactieve PDF-afdrukstromen.
   * Afdruk-PDF genereren op basis van XFA-formulier-PDF.
   * Genereer PDF-, PostScript-, PCL- en ZPL-documenten in bulk door meerdere gegevenssets samen te voegen met bronsjablonen.

* **de doopvonten van de Douane voor Document van Verslag en PDF documenten die met Mededelingen APIs** worden gecreeerd: U kunt merk goedgekeurde doopvonten in de documenten van PDF nu gebruiken die Communicatie APIs worden geproduceerd om op uw organisatorische vereisten te richten.

### Nieuwe functies beschikbaar in [!DNL Forms] prereleasekanaal {#prerelease-features-forms}

* **[Assembler API ](https://www.adobe.io/experience-manager-forms-cloud-service-developer-reference/references/assembler-sync/)**: Assembler APIs om te combineren, te herschikken, te verhogen en informatie over de documenten van PDF te verkrijgen.


## CIF invoegtoepassing {#cloud-services-cif}

### Nieuwe functies {#what-is-new-cif}

* Verbeterde myAccount-componenten
* De component van de Aanbeveling van het product steunt extra paginatypes (homepage, winkelwagentje, ordesbevestiging)
* **Wishlist**
   * Aangemeld door bezoekers kunnen producten toevoegen aan een wanlijst
   * Het beheren van de wantlist en zijn producten is mogelijk via mijnAccount
   * De knop &quot;Toevoegen aan wantlist&quot; kan worden ingeschakeld/uitgeschakeld op componentniveau via beleid (bijvoorbeeld productgummetje, productdetails)
   * Beschikbaar als een kerncomponent en in de AEM Venia Storefront

<!-- Image was not found during PR validation despite correct path ![Wishlist](/help/assets/CIF/wantlist.png) -->

## Cloud Manager {#cloud-manager}

### Releasedatum {#release-date-cm}

De releasedatum voor Cloud Manager is 20 januari 2022.01.0 in AEM as a Cloud Service. De volgende release is gepland voor 10 februari 2022.

### Wat is er nieuw? {#what-is-new-cm}

* Cloud Manager zal [ vermijden herbouwend de codebasis wanneer het ontdekt dat het zelfde gat ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#build-artifact-reuse) in veelvoudige full-stack pijpleidingsuitvoeringen wordt gebruikt.
* De toegang tot van het AEM milieulogboek vereist nu het **productprofiel van de Manager van de Plaatsing 0&rbrace;.** Gebruikers zonder dit profiel zien een uitgeschakelde knop in de gebruikersinterface.
* UI zal niet front-end pijpleidingsconfiguratie voor een programma toestaan waar de Plaatsen niet als oplossing wordt toegelaten.
* Bij het genereren van een wachtwoord voor een kit wordt de vervaldatum weergegeven.

### Opgeloste problemen {#bug-fixes-cm}

* Null wijzeruitzonderingen die door sommige front-end pijpleidingsplaatsingen worden ontmoet zijn verbeterd.
* Omgevingsvariabelen kunnen nu worden toegevoegd, bijgewerkt en verwijderd wanneer een omgeving een verouderde versie van AEM uitvoert.
* De stap van het bouwstijlbeeld zal niet meer als FOUT voor pijpleidingen worden gemerkt die de geplande stap in bepaalde zeldzame gevallen gebruikten.
* Voor programma&#39;s met slechts één opslagplaats, zal het pijpleidingsuitvoeringsscherm nu de bewaarplaatsnaam tonen.

## Inhoud overbrengen {#ctt-release}

### Releasedatum {#release-date-ctt}

De releasedatum voor Content Transfer Tool v1.8.6 is 3 februari 2022.

### Wat is er nieuw? {#what-is-new-ctt}

* Inhoudsvalidatie - Gebruikers kunnen betrouwbaar bepalen of alle inhoud die met het gereedschap Inhoud overbrengen is uitgepakt, is opgenomen in de doelinstantie. Als u deze functie wilt gebruiken, schakelt u deze in in de `System Console` AEM van de bronomgeving. Zie [ Bevaliderende Inhoudsoverdrachten - Begonnen het Worden ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/validating-content-transfers.html?lang=nl-NL#getting-started) voor meer details.

### Opgeloste problemen {#bug-fixes-ctt}

* Sommige gebruikers zijn niet toegewezen omdat de toewijzing van de gebruiker hoofdlettergevoelig was. Dit is opgelost. Gebruikerstoewijzing is niet langer hoofdlettergevoelig.

## Analysator van best practices {#bpa-release}

### Releasedatum {#release-date-bpa}

De releasedatum voor de analyse van best practices v2.1.24 is 1 februari 2022.

### Wat is er nieuw? {#what-is-new-bpa}

* Mogelijkheid om het aantal elementen met en zonder slimme tags te detecteren en hierover te rapporteren.
* Mogelijkheid om de gebruikte versie van de Core Component te detecteren en hierover verslag uit te brengen.
* Mogelijkheid om het type bronlaag (Auteur of Publish) waar BPA werd uitgevoerd op te sporen en te rapporteren.

### Opgeloste problemen {#bug-fixes-bpa}

* BPA-logica voor grootteaanpassing is sneller en efficiënter gemaakt.
* In sommige scenario&#39;s, verhoogde BPA niet de geanalyseerde telling toen het in werking werd gesteld. Dit is opgelost.
