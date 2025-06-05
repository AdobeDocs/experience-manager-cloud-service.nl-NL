---
title: Een speciale testomgeving toevoegen
description: Leer hoe gespecialiseerde testomgevingen in Cloud Manager speciale ruimte bieden voor het valideren van functies onder bijna-productieomstandigheden, ideaal voor stresstests en geavanceerde controles voorafgaand aan de implementatie.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
badge: label="Vroege adoptie" type="Positive" url="/help/implementing/cloud-manager/release-notes/current.md#gitlab-bitbucket"
source-git-commit: 408e472470244c619e09ef58691b1cff7cdd0188
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 0%

---

# Een speciale testomgeving toevoegen{#add-special-test-enviro}

>[!NOTE]
>
>&#x200B;>De in dit artikel beschreven functie is alleen beschikbaar via het programma voor vroegtijdige goedkeuring. Om omhoog als vroege adopter te ondertekenen, zie [ Gespecialiseerde het Testen Milieu ](/help/implementing/cloud-manager/release-notes/current.md#specialized-test-environment).

De gespecialiseerde testomgeving (DevXL) is een nieuw type Cloud Manager-omgeving dat u kunt maken. Het is ontworpen om geavanceerde gebruiksgevallen zoals het Testen van de Erkenning van de Gebruiker (UAT) en prestatiesbevestiging te steunen. In tegenstelling tot traditionele Ontwikkeling, Snelle Ontwikkeling, of het Opvoeren van milieu&#39;s, werken de milieu&#39;s DevXL buiten de pijpleiding van de productieplaatsing. Als zodanig bieden ze u meer flexibiliteit terwijl u strikte isolatie behoudt om interferentie met productieworkflows te voorkomen.

DevXL is gebouwd om de grootte, scalability, en configuraties van een typisch het Staging milieu te weerspiegelen. Deze benadering zorgt ervoor dat tests die in DevXL worden uitgevoerd realistische inzichten in kunnen leveren hoe de code en de inhoud in productie-achtige omstandigheden presteren. De omgeving ondersteunt ook het rechtstreeks kopiëren van inhoud uit Productie of Stage. Het handhaaft ook pariteit met de milieu&#39;s van de Ontwikkeling in termen van plaatsingswerkschema&#39;s, toegangscontroles, en netwerkconfiguraties.

## Belangrijke functies en configuraties {#key-features}

| Categorie | DevXL-gedrag |
| --- | --- |
| Doel | UAT- en prestatietests. |
| Type pijpleiding | Niet in de productiepijplijn. |
| Omgevingsgrootte | Komt overeen met de Stage-omgeving. |
| Isolatie | Volledig geïsoleerd van andere omgevingen. |
| Codepijplijnen | Hetzelfde als de ontwikkelomgeving (validatie, build, implementatie). |
| Inhoud kopiëren | Toegestaan uit Productie- of Stage-omgeving. |
| Inhoud herstellen | Hetzelfde als de ontwikkelomgeving. |
| Toegangslogboeken | Hetzelfde als de ontwikkelomgeving. |
| Developer Console | Hetzelfde als de ontwikkelomgeving. |
| IP-Lijst van gewenste personen | Hetzelfde als de ontwikkelomgeving. |
| Netwerken | Hetzelfde als de ontwikkelomgeving (Services, domeinnaam, SSL-certificaten, Advanced Network). |

Zie ook [ Milieu&#39;s beheren ](/help/implementing/cloud-manager/manage-environments.md)

## Een speciale testomgeving toevoegen {#add-specialized-testing-environment}

Om een milieu toe te voegen of uit te geven, moet een gebruiker een lid van de **rol van de BedrijfsEigenaar** zijn.

**om een Gespecialiseerde het Testen Milieu toe te voegen:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, klik het programma waarvoor u een milieu wilt toevoegen.

1. Voer een van de volgende handelingen uit:

   Als **toevoegt milieu** optie (gehandicapt) wordt gedimd, kan het aan een gebrek aan toestemmingen of afhankelijk van de vergunning gegeven middelen zijn.

   * Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, op de **&#x200B;**&#x200B;kaart van Milieu&#39;s, klik **voegt Milieu** toe.

   ![ kaart van Milieu&#39;s ](assets/no-environments.png)

   * Op het linkerzijpaneel, klik ![&#128279;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Data_18_N.svg) **Milieu&#39;s** van Gegevens 0&rbrace; &lbrace;, dan op de pagina van Milieu&#39;s, dichtbij de hoger-juiste hoek, klik **toevoegt Milieu**.

     ![ Milieu&#39;s tabel ](assets/environments-tab.png)

1. In **voeg milieu** dialoogdoos toe, doe het volgende:

   * Klik [**Gespecialiseerde Milieu van de Test**](#environment-types).
   * Verstrek een milieu **Naam**. De naam van de omgeving kan niet worden gewijzigd nadat de omgeving is gemaakt.
   * (Facultatief) verstrek a **Beschrijving** voor het milieu.
   * Selecteer a **Primair gebied** van de drop-down lijst. Zodra gecreeerd, is het primaire gebied van het milieu DevXL (bijvoorbeeld, *Verenigde Staten (Westen US)*) gesloten en kan niet worden veranderd.

   ![ voeg milieu dialoogdoos met Gespecialiseerde het Testen van Milieu geselecteerde radioknoop ](assets/specialized-test-environment.png) toe

1. Klik **sparen**.

   De **pagina van het Overzicht** toont nu uw nieuw milieu in de **&#x200B;**&#x200B;kaart van Milieu&#39;s. U kunt nu pijpleidingen instellen voor uw nieuwe omgeving.

