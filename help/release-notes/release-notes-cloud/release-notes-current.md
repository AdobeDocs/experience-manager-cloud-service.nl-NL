---
title: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service.
description: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: c497424271ea960d22a30b4a6c66432935ec820d
workflow-type: tm+mt
source-wordcount: '1188'
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

* [!DNL AEM Dynamic Media] biedt nu de flexibiliteit om [één alias-account configureren](../../assets/dynamic-media/dm-alias-account.md) in de gebruikersinterface, waarbij ervoor wordt gezorgd dat Dynamic Media-URL&#39;s en code voor insluiten van de viewer buiten de box worden bijgewerkt. Dit heeft een positieve invloed op SEO om de updates te weerspiegelen die zijn aangebracht in uw zakelijke context, zoals herbranding.

* U kunt nu de opdracht [!DNL Experience Manager Assets] gebruikersinterface naar:

   * Configureer de detectie van dubbele elementen in een opslagplaats.

   * Configureer het toevoegen van digitale watermerken aan afbeeldingen.

* De beheerders kunnen nu de e-mailservice configureren voor grote downloads. Hiermee kunnen gebruikers [e-mailmeldingen inschakelen voor grote downloads](/help/assets/download-assets-from-aem.md#enable-email-notifications-for-large-downloads) van de [!DNL Experience Manager Assets] interface. De gebruiker ontvangt een e-mailbericht met de downloadkoppeling van de gearchiveerde ZIP-map na voltooiing van het downloadproces.


* De [Publicatie beheren](/help/assets/manage-publication.md) wordt verbeterd met een verbeterde gebruikersinterface. De gebruikers kunnen inhoud publiceren of unpublish aan en van de geselecteerde bestemming. [Inhoud toevoegen](/help/assets/manage-publication.md#add-content) naar de publicatielijst vanuit de DAM-opslagplaats, [Inclusief mapinstellingen](/help/assets/manage-publication.md#include-folder-settings) de inhoud van de geselecteerde mappen publiceren en filters toepassen, en [publiceren plannen](/help/assets/manage-publication.md#publish-assets-later) naar een latere datum of tijd.

### Opgeloste problemen {#bug-fixes}

* Niet-verwerkte middelen zonder oorspronkelijke uitvoering worden naar de Asset compute verzonden voor verwerking terwijl de middelen van AEM on-premise naar cloudservices worden gemigreerd.

## [!DNL Experience Manager Forms] als [!DNL Cloud Service] {#forms}

### Nieuwe functies in [!DNL Forms] {#what-is-new-forms}

* **[!DNL AEM Forms as a Cloud Service - Communications]**: [Communicatie-API&#39;s](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/using-communications/aem-forms-cloud-service-communications.html) Hiermee kunt u een sjabloon en XML-gegevens combineren om afdrukdocumenten in verschillende indelingen te genereren. Met deze service kunt u documenten genereren in synchrone modus en in batchmodus. Met de API&#39;s kunt u toepassingen maken waarmee u:

   * Genereer documenten door sjabloonbestanden te vullen met XML-gegevens.
   * Formulieren genereren in verschillende indelingen, waaronder niet-interactieve PDF-afdrukstromen.
   * Afdruk-PDF genereren op basis van XFA-formulier-PDF.
   * Genereer bulksgewijs PDF-, PostScript-, PCL- en ZPL-documenten door meerdere gegevenssets samen te voegen met bronsjablonen.

* **Aangepaste lettertypen voor document van record- en PDF-documenten die zijn gemaakt met communicatie-API&#39;s**: U kunt nu met een merk goedgekeurde lettertypen gebruiken in PDF-documenten die zijn gegenereerd met communicatie-API&#39;s, zodat deze kunnen worden afgestemd op uw organisatorische vereisten.

### Nieuwe functies beschikbaar in [!DNL Forms] prerelease-kanaal {#prerelease-features-forms}

* **[Assembler-API](https://www.adobe.io/experience-manager-forms-cloud-service-developer-reference/references/assembler-sync/)**: Stel API&#39;s samen om PDF-documenten te combineren, opnieuw te rangschikken, te vergroten en te verkrijgen.


## CIF-invoegtoepassing {#cloud-services-cif}

### Nieuwe functies {#what-is-new-cif}

* Verbeterde myAccount-componenten
* De component van de Aanbeveling van het product steunt extra paginatypen (homepage, het winkelwagentje, de bevestiging van de orde)
* **Wishlist**
   * Aangemeld door bezoekers kunnen producten toevoegen aan een verlanglijst
   * Het beheren van de verlanglijst en de producten ervan is mogelijk via mijnAccount
   * De knop &quot;Toevoegen aan wenslijst&quot; kan worden ingeschakeld/uitgeschakeld op componentniveau via beleid (bijvoorbeeld productgummetje, productdetails)
   * Beschikbaar als een kerncomponent en in de AEM Venia Storefront

![Wishlist](/help/assets/CIF/wishlist.png)

## Cloud Manager {#cloud-manager}

### Releasedatum {#release-date-cm}

De releasedatum voor Cloud Manager in AEM as a Cloud Service 2022.01.0 is 20 januari 2022. De volgende release is gepland voor 10 februari 2022.

### Wat is er nieuw? {#what-is-new-cm}

* Cloud Manager wordt [vermijd het herbouwen van de codebasis wanneer het ontdekt dat het zelfde git begaan wordt gebruikt](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#build-artifact-reuse) in veelvoudige full-stack pijpleidingexecuties.
* Voor toegang tot het AEM-omgevingslogboek is nu de **Implementatiebeheer** productprofiel. Gebruikers zonder dit profiel zien een uitgeschakelde knop in de gebruikersinterface.
* UI zal niet front-end pijpleidingsconfiguratie voor een programma toestaan waar de Plaatsen niet als oplossing wordt toegelaten.
* Na het genereren van een wachtwoord voor het afsluiten wordt de vervaldatum weergegeven.

### Opgeloste problemen {#bug-fixes-cm}

* Null wijzeruitzonderingen die door sommige front-end pijpleidingsplaatsingen worden ontmoet zijn verbeterd.
* Omgevingsvariabelen kunnen nu worden toegevoegd, bijgewerkt en verwijderd wanneer een omgeving een verouderde versie van AEM uitvoert.
* De stap van het bouwstijlbeeld zal niet meer als FOUT voor pijpleidingen worden gemerkt die de geplande stap in bepaalde zeldzame gevallen gebruikten.
* Voor programma&#39;s met slechts één opslagplaats, zal het pijpleidingsuitvoeringsscherm nu de bewaarplaatsnaam tonen.

## De tool Content Transfer {#ctt-release}

### Releasedatum {#release-date-ctt}

De releasedatum voor Content Transfer Tool v1.8.6 is 3 februari 2022.

### Wat is er nieuw? {#what-is-new-ctt}

* Inhoudsvalidatie - Gebruikers kunnen betrouwbaar bepalen of alle inhoud die met het gereedschap Inhoud overbrengen is uitgepakt, is opgenomen in de doelinstantie. Als u deze functie wilt gebruiken, moet u deze inschakelen in het dialoogvenster `System Console` van de bron AEM omgeving. Zie [Inhoudsoverdrachten valideren - Aan de slag](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/validating-content-transfers.html?lang=en#getting-started) voor meer informatie .

### Opgeloste problemen {#bug-fixes-ctt}

* Sommige gebruikers zijn niet toegewezen omdat de toewijzing van de gebruiker hoofdlettergevoelig was. Dit is opgelost. Toewijzing van gebruikers is niet langer hoofdlettergevoelig.

## Analysator van best practices {#bpa-release}

### Releasedatum {#release-date-bpa}

De releasedatum voor de analyse van best practices v2.1.26 is 16 maart 2022.

### Wat is er nieuw? {#what-is-new-bpa}

* Mogelijkheid om niet-verwerkte activa te detecteren. Als onverwerkte middelen worden ontdekt, moeten deze activa of aan verwerkt worden geplaatst of moeten uit de migratie worden verwijderd die tijdens inhoudstransmissie wordt geplaatst om lopende in kwesties tijdens inhoudsinname te vermijden.
* Mogelijkheid om te detecteren of inhoud meer dan 1000 vanity-URL&#39;s heeft. Het gebruik van een hoog aantal vanity-URL&#39;s is niet de beste manier, omdat hiermee een laadbewerking wordt uitgevoerd op de servers Dispatcher en Publish.
* Mogelijkheid om problemen met betrekking tot de definities van de eikenindex te identificeren en incompatibiliteiten met AEM as a Cloud Service vast te stellen.
* Mogelijkheid om het gebruik van Externalzer-configuraties te detecteren en hierover verslag uit te brengen. In AEM as a Cloud Service configuraties Externalzer worden ingesteld door Cloud Manager. Daarom moeten bestaande configuraties Externalzer worden vernieuwd om de compatibiliteit te behouden.

### Opgeloste problemen {#bug-fixes-bpa}

* In sommige gevallen kon BPA niet worden uitgevoerd omdat FormsSelectiveFeaturesAnalysis een assertiefout genereerde. Dit is opgelost.
* BPA rapporteerde bevindingen met betrekking tot het WRK-patroon als MAJOR in plaats van als KRITIEK. Dit is opgelost.
* BPA rapporteerde onjuist bevindingen met betrekking tot OAK-indexdefinities in ui.apps als CRITICAL. Dit is opgelost
