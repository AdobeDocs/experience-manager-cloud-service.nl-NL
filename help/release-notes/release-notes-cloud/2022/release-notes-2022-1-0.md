---
title: Opmerkingen bij de release 2022.1.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de release 2022.1.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 1c40ab67-8fd7-4f29-b8c9-dd98b6d5b490
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1065'
ht-degree: 0%

---

# Opmerkingen bij de release 202.1.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de release met functies voor de versie 2022.1.0 van [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van vorige versies vrij te geven, bijvoorbeeld voor de versies in 2020, 2021 enzovoort.

>[!NOTE]
>
>Zie [Recente documentatieupdates](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor meer informatie over documentatie-updates die niet rechtstreeks verband houden met een release.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als [!DNL Cloud Service] huidige release (2022.1.0) is 3 februari 2022.
De volgende release (2022.3.0) is op 31 maart 2022.

## Video vrijgeven {#release-video}

Kijk eens naar de [Overzicht release januari 2022](https://video.tv.adobe.com/v/340120) video voor een overzicht van de functies die in de release 2022.1.0 zijn toegevoegd.

## Adobe Experience Manager Sites as a Cloud Service {#sites}

* De **[Vooruiteinde pijplijn inschakelen](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md)** is beschikbaar in het dialoogvenster **Site** rail van de Sites-console voor sites die versie 2 van de Page Core-component gebruiken. Deze knoop vormt de plaats om de thema&#39;s te laden die met de Voorste Pijpleiding van het Eind bovenop de bestaande cliëntbibliotheken worden opgesteld.

## [!DNL Experience Manager Assets] als [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#assets-features}

* [!DNL Dynamic Media] - U kunt nu AEM Dynamic Media-interface gebruiken om Algemene instellingen en Publicatie-instellingen te configureren in plaats van de Dynamic Media Classic-bureaubladtoepassing te doorlopen.

* [!DNL Dynamic Media] ondersteunt nu opname, voorvertoning, afspelen en publiceren voor MXF-video&#39;s. Annotatie en verbluffende video voor MXF-video&#39;s worden nog niet ondersteund.

* Nadat u een verbinding tussen externe DAM- en Sites-implementaties hebt geconfigureerd, worden de middelen op externe DAM beschikbaar gesteld op de implementatie van Sites. U kunt nu de opdracht [bewerkingen bijwerken, verwijderen, hernoemen en verplaatsen](/help/assets/use-assets-across-connected-assets-instances.md) op de externe DAM-middelen of -mappen. De updates zijn, met wat vertraging, automatisch beschikbaar op de plaatsing van Plaatsen.

### Nieuwe functies in het dialoogvenster [!DNL Assets] prerelease-kanaal {#assets-prerelease-features}

* [!DNL AEM Dynamic Media] biedt nu de flexibiliteit om [één alias-account configureren](/help/assets/dynamic-media/dm-alias-account.md) in de gebruikersinterface, waarbij ervoor wordt gezorgd dat Dynamic Media-URL&#39;s en code voor insluiten van de viewer buiten de box worden bijgewerkt. Dit heeft een positieve invloed op SEO om de updates te weerspiegelen die zijn aangebracht in uw zakelijke context, zoals herbranding.

* U kunt nu de opdracht [!DNL Experience Manager Assets] gebruikersinterface naar:

   * Configureer de detectie van dubbele elementen in een opslagplaats.

   * Configureer het toevoegen van digitale watermerken aan afbeeldingen.

* De beheerders kunnen nu de e-mailservice configureren voor grote downloads. Hiermee kunnen gebruikers [e-mailmeldingen inschakelen voor grote downloads](/help/assets/download-assets-from-aem.md#enable-email-notifications-for-large-downloads) van de [!DNL Experience Manager Assets] interface. De gebruiker ontvangt een e-mailbericht met de downloadkoppeling van de gearchiveerde ZIP-map na voltooiing van het downloadproces.


* De [Publicatie beheren](/help/assets/manage-publication.md) wordt verbeterd met een verbeterde gebruikersinterface. De gebruikers kunnen inhoud publiceren of unpublish aan en van de geselecteerde bestemming. [Inhoud toevoegen](/help/assets/manage-publication.md#add-content) naar de publicatielijst vanuit de DAM-opslagplaats, [Inclusief mapinstellingen](/help/assets/manage-publication.md#include-folder-settings) om inhoud van de geselecteerde omslagen te publiceren en filters toe te passen, en [publiceren plannen](/help/assets/manage-publication.md#publish-assets-later) naar een latere datum of tijd.

### Opgeloste problemen {#bug-fixes}

* Niet-verwerkte middelen zonder oorspronkelijke uitvoering worden naar de Asset compute verzonden voor verwerking terwijl de middelen van AEM on-premise naar cloudservices worden gemigreerd.

## [!DNL Experience Manager Forms] als [!DNL Cloud Service] {#forms}

### Nieuwe functies in [!DNL Forms] {#what-is-new-forms}

* **[!DNL AEM Forms as a Cloud Service - Communications]**: [Communicatie-API&#39;s](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/using-communications/aem-forms-cloud-service-communications.html) Hiermee kunt u een sjabloon en XML-gegevens combineren om afdrukdocumenten in verschillende indelingen te genereren. Met de service kunt u documenten genereren in synchrone modus en in batchmodus. Met de API&#39;s kunt u toepassingen maken waarmee u:

   * Genereer documenten door sjabloonbestanden te vullen met XML-gegevens.
   * Formulieren genereren in verschillende indelingen, waaronder niet-interactieve PDF-afdrukstromen.
   * Afdruk-PDF genereren op basis van XFA-formulier-PDF.
   * Genereer PDF-, PostScript-, PCL- en ZPL-documenten in bulk door meerdere gegevenssets samen te voegen met bronsjablonen.

* **Aangepaste lettertypen voor document van record- en PDF-documenten die zijn gemaakt met communicatie-API&#39;s**: U kunt nu met een merk goedgekeurde lettertypen gebruiken in PDF-documenten die zijn gegenereerd met communicatie-API&#39;s en die aan uw organisatorische vereisten voldoen.

### Nieuwe functies beschikbaar in [!DNL Forms] prerelease-kanaal {#prerelease-features-forms}

* **[Assembler API](https://www.adobe.io/experience-manager-forms-cloud-service-developer-reference/references/assembler-sync/)**: Assembler-API&#39;s om PDF-documenten te combineren, opnieuw te rangschikken, te vergroten en te verkrijgen.


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

De releasedatum voor Cloud Manager in AEM as a Cloud Service 2022.01.0 is 20 januari 2022. De volgende release is gepland voor 10 februari 2022.

### Wat is er nieuw? {#what-is-new-cm}

* Cloud Manager wordt [vermijd het opnieuw samenstellen van de codebasis wanneer het ontdekt dat het zelfde git begaan wordt gebruikt](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#build-artifact-reuse) in veelvoudige full-stack pijpleidingexecuties.
* Voor het openen van het AEM-omgevingslogboek is nu de **Implementatiebeheer** productprofiel. Gebruikers zonder dit profiel zien een uitgeschakelde knop in de gebruikersinterface.
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

* Inhoudsvalidatie - Gebruikers kunnen betrouwbaar bepalen of alle inhoud die met het gereedschap Inhoud overbrengen is uitgepakt, is opgenomen in de doelinstantie. Als u deze functie wilt gebruiken, schakelt u deze in het dialoogvenster `System Console` van de bron AEM omgeving. Zie [Inhoudsoverdrachten valideren - Aan de slag](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/validating-content-transfers.html#getting-started) voor meer informatie .

### Opgeloste problemen {#bug-fixes-ctt}

* Sommige gebruikers zijn niet toegewezen omdat de toewijzing van de gebruiker hoofdlettergevoelig was. Dit is opgelost. Gebruikerstoewijzing is niet langer hoofdlettergevoelig.

## Analysator van best practices {#bpa-release}

### Releasedatum {#release-date-bpa}

De releasedatum voor de analyse van best practices v2.1.24 is 1 februari 2022.

### Wat is er nieuw? {#what-is-new-bpa}

* Mogelijkheid om het aantal elementen met en zonder slimme tags te detecteren en hierover te rapporteren.
* Mogelijkheid om de gebruikte versie van de Core Component te detecteren en hierover verslag uit te brengen.
* Mogelijkheid om het type bronlaag (Auteur of Publiceren) waar BPA is uitgevoerd, op te sporen en te rapporteren.

### Opgeloste problemen {#bug-fixes-bpa}

* BPA-logica voor grootteaanpassing is sneller en efficiënter gemaakt.
* In sommige scenario&#39;s, verhoogde BPA niet de geanalyseerde telling toen het in werking werd gesteld. Dit is opgelost.
