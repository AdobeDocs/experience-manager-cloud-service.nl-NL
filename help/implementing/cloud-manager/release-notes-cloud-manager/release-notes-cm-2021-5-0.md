---
title: Opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service versie 2021.5.0
description: Opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service versie 2021.5.0
feature: Release Information
exl-id: 8ae3cf2f-1865-427a-b612-bdf56e2f0304
source-git-commit: 09d5d125840abb6d6cc5443816f3b2fe6602459f
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# Opmerkingen bij de release voor Cloud Manager in Adobe Experience Manager as a Cloud Service 2021.5.0 {#release-notes}

Deze pagina bevat een overzicht van de opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service 2021.5.0.

>[!NOTE]
>Klik op [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html).

## Releasedatum {#release-date}

De releasedatum voor Cloud Manager in AEM as a Cloud Service 2021.5.0 is 6 mei 2021.

### Wat is er nieuw? {#what-is-new}

* De PackageOverlaps kwaliteitsregel ontdekt nu gevallen waar het zelfde pakket veelvoudige tijden, d.w.z. in veelvoudige ingebedde plaatsen, in de zelfde opgestelde pakketreeks werd opgesteld.

* Het eindpunt van de repository in de Public API bevat nu de Git URL.

* Het implementatielogboek dat door een gebruiker van Cloud Manager wordt gedownload, is begrijpelijker en bevat nu details over fouten en successcenario&#39;s.

* Intermitterende fouten die werden aangetroffen tijdens het doorvoeren van code naar Adobe-it, zijn nu opgelost.

* Invoegtoepassing voor handel kan nu worden toegepast op Sandbox-programma&#39;s tijdens de workflow van het bewerkingsprogramma.

* De *Programma bewerken* de ervaring is vernieuwd .

* De lijst van de Namen van het Domein in de pagina van Details van het Milieu zal tot 250 namen van Domein via paginering tonen.

* De **Oplossingen en invoegtoepassingen** tab in **Programma toevoegen** en **Programma bewerken** De werkschema&#39;s zullen de oplossing tonen, zelfs als slechts één oplossing voor het Programma beschikbaar is.

* Het foutenbericht in het bouwstijlstaplogboek toen de bouwstijl geen opgestelde inhoudspakketten produceerde was onduidelijk.

### Opgeloste problemen {#bug-fixes}

* Soms, kan de gebruiker een groene &quot;actieve&quot;status naast een IP Lijst van gewenste personen zien zelfs wanneer die configuratie niet werd opgesteld.

* In plaats van &#39;verwijderde&#39; variabelen te verwijderen, markeert de API voor pijpleidingvariabelen deze alleen met status **VERWIJDERD**.

* Sommige kwaliteitskwesties van het type Code Smell hadden een onjuiste invloed op de beoordeling Betrouwbaarheid.

* Omdat jokertekendomeinen niet worden ondersteund, staat de gebruikersinterface de gebruiker niet toe een jokertekendomein in te dienen.

* Wanneer een pijpleidingsuitvoering tussen middernacht en 1am UTC werd begonnen, werd de artefactversie die door de Manager van de Wolk werd geproduceerd niet gewaarborgd om groter te zijn dan een versie die de vorige dag werd gecreeerd.

* Tijdens de opstelling van het programma Sandbox, zodra het project met steekproefcode met succes is gecreeerd, zal Manage Git als verbinding van de heldenkaart in de pagina van het Overzicht verschijnen.
