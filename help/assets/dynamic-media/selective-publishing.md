---
title: Werken met Selectieve publicatie in Dynamic Media
description: Leer hoe u in Dynamic Media kunt werken met Selective Publish.
contentOwner: Rick Brough
topic-tags: dynamic-media
content-type: reference
docset: aem65
role: Business Practitioner
exl-id: a5a2df68-be13-45a6-ad80-09fbd2fea8f2
source-git-commit: d3ee23917eba4a2e4ae1f2bd44f5476d2ff7dce1
workflow-type: tm+mt
source-wordcount: '2537'
ht-degree: 1%

---

# Selectieve publicatie op mapniveau configureren in Dynamic Media {#selective-publish-configure-folder}

U kunt ervoor kiezen om elementen te publiceren naar of te verwijderen uit Adobe Experience Manager of Dynamic Media. U kunt dit op mapniveau doen met **[!UICONTROL Manage Publication]** of **[!UICONTROL Quick Publish]**. Deze publicatiemethode is handig omdat deze niet alleen afhankelijk is van de **[!UICONTROL Dynamic Media Configuration]** waarvan de instellingen algemeen gelden voor alle mappen in uw Dynamic Media-instantie.

Met selectief publiceren kunt u bijvoorbeeld werken aan elementen voor producten die nog niet actief zijn. In dat geval kan een marketingteam toegang krijgen tot afbeeldingen met slimme uitsnijdingen en dynamische vertoningen die zijn gesynchroniseerd met Dynamic Media. Ze kunnen promotiematerialen maken, zonder dat ze die middelen naar Dynamic Media hoeven te publiceren voor wereldwijde levering.

<!-- 
>[!IMPORTANT]
>
>Selective Publish is only available in Dynamic Media - Scene7 mode.
-->

>[!NOTE]
>
>*Door elementen van en naar mappen te* kopiëren, wordt de publicatiestatus van deze elementen gewist. Wanneer u *echter elementen naar en van mappen verplaatst waarvan de mapeigenschap is ingesteld op **[!UICONTROL Selective Publish]**, blijft de publicatiestatus van deze elementen behouden.*

Als u later besluit om de **[!UICONTROL Selective Publish]** montages in een omslag te veranderen, beïnvloeden die veranderingen slechts nieuwe activa die u aan die omslag van dat punt vooruit uploadt. De publicatiestatus van bestaande elementen in de map blijft ongewijzigd totdat u deze handmatig wijzigt vanuit **[!UICONTROL Quick Publish]** of het dialoogvenster **[!UICONTROL Manage Publication]**.

De optie **[!UICONTROL Dynamic Media Publish mode]** op mapniveau is altijd standaard ingesteld op de waarde die wordt gevonden in de instelling **[!UICONTROL Publish Assets]** in **[!UICONTROL Dynamic Media Configuration]**. De volgende stappen in dit onderwerp, echter, tonen u hoe te om deze standaardwaarde op het omslagniveau (zoals die in de volgende stappen wordt beschreven) manueel te veranderen om de **[!UICONTROL Dynamic Media Configuration]** waarde met voeten te treden.

Ongeacht of u erop vertrouwt:

* De waarde **[!UICONTROL Publish Assets]** die is ingesteld in **[!UICONTROL Dynamic Media Configuration]**
* Of de waarde **[!UICONTROL Dynamic Media Publish mode]** die is ingesteld in de eigenschappen op mapniveau

U kunt nog **[!UICONTROL Immediately]**, **[!UICONTROL Upon Activation]**, of **[!UICONTROL Selective Publish]** kiezen. U kunt bijvoorbeeld de waarde **[!UICONTROL Publish Assets]** in uw **[!UICONTROL Dynamic Media Configuration]** instellen op **[!UICONTROL On Activation]**. En, kunt u **[!UICONTROL Dynamic Media Publish]** wijzewaarde op het omslagniveau aan **[!UICONTROL Selective Publish]**, omgekeerd, etc. plaatsen.

Nadat u selectief publiceren in een omslag vormt, kunt u om het even welke volgend doen:

* [Publiceer selectief middelen naar Dynamic Media of Experience Manager met Publicatie](#selective-publish-manage-publication) beheren.
* [Publiceer selectief elementen van Dynamic Media of Experience Manager met Publicatie](#selective-unpublish-manage-publication) beheren.
* [Elementen publiceren naar Dynamic Media of Experience Manager met Snel publiceren](#quick-publish-aem-dm).
* [Publiceer elementen selectief of maak de publicatie ongedaan door zoekresultaten](#selective-publish-unpublish-search-results).

**Selectieve publicatie op mapniveau in Dynamic Media configureren:**

1. Tik in Experience Manager op het logo van de Experience Manager om toegang te krijgen tot de algemene navigatieconsole. Tik links op het navigatiepictogram (net boven het gereedschapspictogram) en tik op **[!UICONTROL Assets]** > **[!UICONTROL Files]**.
1. Voer een van de volgende handelingen uit:
   * Bewerk de eigenschappen van een bestaande map - Navigeer in **[!UICONTROL Card View]**, **[!UICONTROL Column View]** of **[!UICONTROL List View]** naar een map waarvan u de eigenschappen wilt bewerken. Selecteer de map en tik op **[!UICONTROL Properties]** op de werkbalk.
   * Bewerk de eigenschappen van een nieuwe map - tik **[!UICONTROL Create > Folder]**, **[!UICONTROL Column View]** of **[!UICONTROL List View]** in de rechterbovenhoek van de pagina. **[!UICONTROL Card View]** Voer in het dialoogvenster **[!UICONTROL Create Folder]** een titel (vereist) voor de map in en tik vervolgens op **[!UICONTROL Create]**. Selecteer de map en tik op **[!UICONTROL Properties]** op de werkbalk.

1. Selecteer een van de volgende opties in de vervolgkeuzelijst **[!UICONTROL Sync mode]**:

   | Synchronisatiemodus | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Inherited]** | Geen expliciete synchronisatiewaarde in de map; in plaats daarvan, erft de omslag de synchronisatiewaarde van één van zijn voorouderomslagen of de standaardwijze die in uw **[!UICONTROL Dynamic Media Configuration]** wordt geplaatst. De gedetailleerde status voor **[!UICONTROL Inherited]** wordt weergegeven als knopinfo. |
   | **[!UICONTROL Sync everything in this folder subtree to Dynamic Media]** | Voor het publiceren naar Dynamic Media moet u de middelen synchroniseren met Dynamic Media. Als u deze optie selecteert, worden alle elementen in deze substructuur opgenomen die u kunt synchroniseren met Dynamic Media. De omslag-specifieke montages treden het gebrek met voeten dat in **[!UICONTROL Dynamic Media Configuration]** plaatst. |
   | **[!UICONTROL Exclude everything in this folder subtree from Dynamic Media sync]** | Sluit alle elementen in deze substructuur uit van synchroniseren naar Dynamic Media. |

   ![Selectieve publicatie op mapniveau](/help/assets/assets-dm/createfolder-properties-selectivepublish.png)

1. Selecteer een optie in de vervolgkeuzelijst **[!UICONTROL Dynamic Media Publish mode]**. De optie **[!UICONTROL Dynamic Media Publish mode]** is altijd standaard ingesteld op de waarde die is ingesteld in **[!UICONTROL Dynamic Media Configuration]**. U kunt deze standaardwaarde **[!UICONTROL Dynamic Media Configuration]** echter handmatig overschrijven met een van de volgende opties.

   >[!IMPORTANT]
   >
   >Ongeacht de door u geselecteerde optie in de Dynamic Media-publicatiemodus worden eventuele updates die u later aanbrengt in een element dat *al* is gepubliceerd, onmiddellijk gepubliceerd zonder verdere actie van de gebruiker.

   | Dynamic Media-publicatiemodus, optie | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Immediately]** | Wanneer elementen naar deze map worden geüpload, worden de elementen door het systeem in de Experience Manager ingevoerd en wordt de URL/Embed onmiddellijk weergegeven. Deze optie is alleen gekoppeld aan publicatie door Experience Managers en er is geen tussenkomst van de gebruiker nodig om elementen te publiceren.<br>Deze optie is niet  ** beschikbaar als u  **[!UICONTROL Exclude everything in this folder subtree from Dynamic Media sync]** in  **[!UICONTROL Sync mode]** de vorige stap selecteerde. |
   | **[!UICONTROL Upon Activation]** | Wanneer elementen naar deze map worden geüpload, moet u het element eerst expliciet publiceren voordat een koppeling URL/Embed wordt opgegeven. Deze optie is alleen gekoppeld aan publiceren via Experience Manager.<br>Deze optie is niet  ** beschikbaar als u  **[!UICONTROL Exclude everything in this folder subtree from Dynamic Media sync]** in  **[!UICONTROL Sync mode]** de vorige stap selecteerde. |
   | **[!UICONTROL Selective Publish]** | De activa worden gepubliceerd aan uw keuze van of Experience Manager of aan Dynamic Media voor levering in het openbare domein. Beide publicatiemethoden sluiten elkaar uit. Met andere woorden, u kunt elementen publiceren naar DMS7 zodat u functies zoals Slim uitsnijden of dynamische uitvoeringen kunt gebruiken. U kunt ook uitsluitend elementen publiceren naar Experience Manager voor een veilige voorvertoning. dezelfde activa worden *niet* gepubliceerd naar DMS7 voor levering in het publieke domein. Deze optie is niet beschikbaar als u **[!UICONTROL Exclude everything in this folder subtree from Dynamic Media sync]** in **[!UICONTROL Sync mode]** in de vorige stap selecteerde. |

1. Tik in de rechterbovenhoek van de pagina op **[!UICONTROL Save & Close]** en tik vervolgens op **[!UICONTROL OK]** om terug te keren naar Experience Manager Assets.

## Elementen selectief publiceren naar Dynamic Media of Experience Manager als Cloud Service met Publicatie beheren{#selective-publish-manage-publication}

Voordat u **[!UICONTROL Manage Publication]** kunt gebruiken om elementen selectief te publiceren naar Dynamic Media of naar Experience Manager, moet u een van de volgende handelingen uitvoeren:

* Stel de optie **[!UICONTROL Publish Assets]** in **[!UICONTROL Dynamic Media Configuration]** in op **[!UICONTROL Selective Publish]**.
* Of, vormde selectieve het publiceren op het omslagniveau.

Zie [Een Dynamic Media-configuratie maken](#configuring-dynamic-media-cloud-services) of [Selectieve publicatie op mapniveau configureren in Dynamic Media](#selective-publish-configure-folder)

<!--
>[!IMPORTANT]
>
>Selective Publish is only available in Dynamic Media - Scene7 mode.
-->

>[!NOTE]
>
>*Door elementen van en naar mappen te* kopiëren, wordt de publicatiestatus van deze elementen gewist. Wanneer u *echter elementen naar en van mappen verplaatst waarvan de mapeigenschap is ingesteld op **[!UICONTROL Selective Publish]**, blijft de publicatiestatus van deze elementen behouden.*

**Elementen selectief publiceren naar Dynamic Media of Experience Manager als Cloud Service met Publicatie beheren:**

1. Tik in Experience Manager op het logo van de Experience Manager om toegang te krijgen tot de algemene navigatieconsole. Tik links op het navigatiepictogram (net boven het gereedschapspictogram) en tik op **[!UICONTROL Assets]** > **[!UICONTROL Files]**.
1. Voer in **[!UICONTROL Card View]**, **[!UICONTROL Column View]** of **[!UICONTROL List View]** een van de volgende handelingen uit:
   * Navigeer naar een map waarvan u de elementen wilt publiceren. Selecteer de map en tik op **[!UICONTROL Manage Publication]** op de werkbalk. Gebruik **[!UICONTROL List View]** zodat u de publicatiestatus van een bepaalde map eenvoudiger kunt controleren.
   * Navigeer naar een map waarvan u de elementen wilt publiceren. Open de map en selecteer vervolgens een of meer elementen. Tik op **[!UICONTROL Manage Publication]** op de werkbalk. Gebruik **[!UICONTROL List View]** zodat u de publicatiestatus van een bepaald element eenvoudiger kunt controleren.

      >[!NOTE]
      >
      >Als **[!UICONTROL Manage Publication]** niet op de werkbalk wordt weergegeven, tikt u op de knop voor weglatingsteken en selecteert u **[!UICONTROL Manage Publication]** in het lijstmenu.

1. Selecteer op de pagina **[!UICONTROL Manage Publication - Options]** onder **[!UICONTROL Action]** het gewenste activeringstype.

   | Actie | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Publish]** (naar Experience Manager) | Selecteer deze optie als u elementen naar de Experience Manager wilt publiceren voor een beveiligde voorvertoning. |
   | **[!UICONTROL Publish to Dynamic Media]** | Selecteer deze optie als u elementen naar Dynamic Media wilt publiceren voor levering in het publieke domein of als u functies wilt gebruiken, zoals Slim uitsnijden of Dynamische vertoningen.<br>Deze optie is alleen beschikbaar als  **[!UICONTROL Dynamic Media Publish mode]** deze is ingesteld  **[!UICONTROL Selective Publish]** in de eigenschappen van de map. |

1. Stel onder **[!UICONTROL Schedule]** de timing van de publicatie in.

   | Schema | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Now]** | Selecteer deze optie om de elementen direct te publiceren. |
   | **[!UICONTROL Later]** | Selecteer deze optie om de elementen op een bepaalde datum en tijd te publiceren. |

1. Tik in de rechterbovenhoek van de pagina **[!UICONTROL Manage Publication]** op **[!UICONTROL Next]**.
1. Voer op de pagina **[!UICONTROL Manage Publication - Scope]** een van de volgende handelingen uit:
   * Selecteer zo nodig een of meer elementen die u uit publicatie wilt verwijderen.
   * Tik in de rechterbovenhoek van de pagina **[!UICONTROL Manage Publication - Scope]** op **[!UICONTROL Publish]** of **[!UICONTROL Publish to Dynamic Media]**.
1. Tik op **[!UICONTROL OK]**.

### Publicatie van middelen van Dynamic Media of Experience Manager selectief ongedaan maken met Publicatie beheren {#selective-unpublish-manage-publication}

1. Tik in Experience Manager op het logo van de Experience Manager om toegang te krijgen tot de algemene navigatieconsole. Tik links op het navigatiepictogram (net boven het gereedschapspictogram) en tik op **[!UICONTROL Assets]** > **[!UICONTROL Files]**.
1. Voer in **[!UICONTROL Card View]**, **[!UICONTROL Column View]** of **[!UICONTROL List View]** een van de volgende handelingen uit:
   * Navigeer naar een map waarvan u de publicatie ongedaan wilt maken. Selecteer de map en tik op **[!UICONTROL Manage Publication]** op de werkbalk. Gebruik **[!UICONTROL List View]** zodat u de publicatiestatus van een bepaalde map eenvoudiger kunt controleren.
   * Navigeer naar een map waarvan u de publicatie ongedaan wilt maken. Open de map en selecteer vervolgens een of meer elementen. Tik op **[!UICONTROL Manage Publication]** op de werkbalk. Gebruik **[!UICONTROL List View]** zodat u de publicatiestatus van een bepaald element eenvoudiger kunt controleren.

      >[!NOTE]
      >
      >Als **[!UICONTROL Manage Publication]** niet op de werkbalk wordt weergegeven, tikt u op de knop voor weglatingsteken en selecteert u **[!UICONTROL Manage Publication]** in het lijstmenu.

1. Selecteer op de pagina **[!UICONTROL Manage Publication - Options]** onder **[!UICONTROL Action]** het gewenste type deactivering.

   | Actie | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Unpublish]** (van Experience Manager) | Selecteer deze optie als u de publicatie van elementen uit Experience Manager wilt opheffen. |
   | **[!UICONTROL Unpublish from Dynamic Media]** | Als u de publicatie van elementen uit Dynamic Media wilt opheffen, selecteert u deze optie.<br>Deze optie is alleen beschikbaar als  **[!UICONTROL Dynamic Media Publish mode]** deze is ingesteld  **[!UICONTROL Selective Publish]** in de eigenschappen van de map. |

1. Stel onder **[!UICONTROL Schedule]** de timing van de deactivering in.

   | Schema | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Now]** | Selecteer deze optie om de publicatie van de elementen direct ongedaan te maken. |
   | **[!UICONTROL Later]** | Selecteer deze optie om de publicatie van de elementen op een bepaalde datum en tijd ongedaan te maken. |

1. Tik in de rechterbovenhoek van de pagina **[!UICONTROL Manage Publication]** op **[!UICONTROL Next]**.
1. Voer op de pagina **[!UICONTROL Manage Publication - Scope]** een van de volgende handelingen uit:
   * Selecteer een of meer elementen die u uit het ongedaan maken van de publicatie wilt verwijderen.
   * Tik in de rechterbovenhoek van de pagina **[!UICONTROL Manage Publication - Scope]** op **[!UICONTROL Unpublish]** of **[!UICONTROL Unpublish from Dynamic Media]**.
1. Tik op **[!UICONTROL OK]**.

## Elementen publiceren naar Dynamic Media of Experience Manager met Snel publiceren {#quick-publish-aem-dm}

U kunt **[!UICONTROL Quick Publish]** voor eenvoudige gevallen van activering van elementen gebruiken. **[!UICONTROL Quick Publish]** publiceert de geselecteerde middelen onmiddellijk zonder verdere gebruikersinteractie. Niet-gepubliceerde verwijzingen worden ook automatisch gepubliceerd.

>[!NOTE]
>
>Als u **[!UICONTROL Quick Publish]** wilt gebruiken om elementen te publiceren naar Dynamic Media of Experience Manager, moet **[!UICONTROL Selective Publish]** zijn ingeschakeld in uw **[!UICONTROL Dynamic Media Configuration]** of in de mapeigenschappen van de geselecteerde map.

**Elementen publiceren naar Dynamic Media of Experience Manager met Snel publiceren:**

1. Tik in Experience Manager op het logo van de Experience Manager om toegang te krijgen tot de algemene navigatieconsole. Tik links op de pagina op het navigatiepictogram (net boven het pictogram Gereedschappen) en tik vervolgens rechts op de pagina op **[!UICONTROL Assets]** > **[!UICONTROL Files]**.
1. Voer in **[!UICONTROL Card View]**, **[!UICONTROL Column View]** of **[!UICONTROL List View]** een van de volgende handelingen uit:
   * Navigeer naar een map waarvan u de elementen wilt publiceren. Selecteer de map en tik op **[!UICONTROL Quick Publish]** op de werkbalk. Gebruik **[!UICONTROL List View]** zodat u de publicatiestatus van een bepaalde map eenvoudiger kunt controleren.
   * Navigeer naar een map waarvan u de elementen wilt publiceren. Open de map en selecteer vervolgens een of meer elementen. Tik op **[!UICONTROL Quick Publish]** op de werkbalk. Gebruik **[!UICONTROL List View]** zodat u de publicatiestatus van een bepaald element eenvoudiger kunt controleren.

      >[!NOTE]
      >
      >Als **[!UICONTROL Quick Publish]** niet op de werkbalk wordt weergegeven, tikt u op de knop voor weglatingsteken en selecteert u **[!UICONTROL Quick Publish]** in het lijstmenu.

      ![Snel publiceren op mapniveau naar Dynamic Media](/help/assets/assets-dm/selective-publish-folder-quick-publish-to-dm.png)

1. Selecteer een van de volgende opties in de menulijst **[!UICONTROL Quick Publish]**.

   | Snel publiceren, optie | Wat het doet |
   | --- | --- | 
   | Publiceren naar Experience Manager | Hiermee publiceert u de geselecteerde elementen direct naar de Experience Manager. |
   | Publiceren naar Brand Portal | Hiermee publiceert u de geselecteerde elementen direct naar **[!UICONTROL Brand Portal]**.<br>Deze optie is alleen beschikbaar als de Experience Manager Assets-instantie  **[!UICONTROL Brand Portal]** al is geconfigureerd. |
   | Publiceren naar Dynamic Media | Hiermee publiceert u de geselecteerde elementen direct naar Dynamic Media.<br>Een middel moet tot Dynamic Media reeds worden gesynchroniseerd. Indien nodig, zorg ervoor dat **[!UICONTROL Sync mode]** in de eigenschappen van een omslag reeds aan **[!UICONTROL Sync everything in this folder subtree to Dynamic Media]** wordt geplaatst. |

1. Tik **[!UICONTROL OK]** en tik vervolgens op **[!UICONTROL Close]**.

## Elementen selectief publiceren of verwijderen via zoekresultaten {#selective-publish-unpublish-search-results}

In de zoekresultaten kunt u elementen uit verschillende middelenmappen met verschillende Dynamic Media-publicatie-instellingen weergeven. Als u een of meer elementen hebt geselecteerd in zoekresultaten en de elementen verschillende instellingen voor de Dynamic Media-publicatiemodus hebben, kunt u **[!UICONTROL Manage Publication]** op de werkbalk activeren om te publiceren of te publiceren.

Zie ook [Elementen zoeken in Experience Manager](/help/assets/search-assets.md).

**Elementen selectief publiceren of verwijderen via zoekresultaten:**

1. Tik in Experience Manager linksboven op de pagina op het logo van de Experience Manager om toegang te krijgen tot de algemene navigatieconsole. Tik links op de pagina op het navigatiepictogram (net boven het gereedschapspictogram) en tik op **[!UICONTROL Assets]** > **[!UICONTROL Files]**.
1. Tik in de werkbalk rechtsboven op de pagina op het pictogram Zoeken (vergrootglas).
1. Voer in het tekstveld **[!UICONTROL Type to search]** een trefwoord in en druk op **[!UICONTROL Enter]**.
1. Tik in de rechterbovenhoek van de pagina op het pictogram **[!UICONTROL List View]**.
1. Tik in de linkerbovenhoek van de pagina op het pictogram **[!UICONTROL Filters]**.

   ![Lijstweergave en filters in zoekresultaten](/help/assets/assets-dm/select-publish-search-result.png)

1. Vouw in het linkerdeelvenster **[!UICONTROL Status]** uit en vouw vervolgens de zoekvoorspelling **[!UICONTROL Dynamic Media]** uit.
1. Gebruik de selectievakjes **[!UICONTROL Published]** en **[!UICONTROL Unpublished]** om de zoekresultaten verder te verfijnen op basis van de gepubliceerde status van Dynamic Media-elementen.
U kunt deze selectievakjes ook gebruiken met de zoekvoorspelling **[!UICONTROL Publish]** om de zoekresultaten van de elementen **[!UICONTROL Published]** en **[!UICONTROL Unpublished]** Experience Manager te verfijnen.
1. Voer een van de volgende handelingen uit:
   * Selecteer een of meer elementen die u wilt publiceren of waarvan u de publicatie ongedaan wilt maken.
   * Tik in de rechterbovenhoek van de pagina **[!UICONTROL Search Results]** op **[!UICONTROL Select All]**.
1. Tik op **[!UICONTROL Manage Publication]** op de werkbalk. Tik, indien nodig, op het ellipspictogram op de werkbalk om **[!UICONTROL Manage Publication]** weer te geven.
1. Selecteer op de pagina **[!UICONTROL Manage Publication - Options]** de gewenste actie.

   | Geselecteerde actie | Instelling Middelen publiceren in Dynamic Media-configuratie | Elementen zijn |
   | --- | --- | --- |
   | Publicatie | Onmiddellijk of bij activering | Gepubliceerd aan Experience Manager en Dynamic Media. |
   | Publicatie | Selectieve publicatie | Alleen gepubliceerd naar Experience Manager. |
   | Publiceren ongedaan maken | Onmiddellijk of bij activering | Niet gepubliceerd vanuit Experience Manager en Dynamic Media. |
   | Publiceren ongedaan maken | Selectieve publicatie | Niet gepubliceerd alleen vanuit Experience Manager. |
   | Publiceren naar Dynamic Media | Onmiddellijk of bij activering | Niet gepubliceerd naar Experience Manager, Dynamic Media of beide. |
   | Publiceren naar Dynamic Media | Selectieve publicatie | Alleen gepubliceerd naar Dynamic Media. |
   | Publiceren vanuit Dynamic Media ongedaan maken | Onmiddellijk of bij activering | Niet ongepubliceerd vanuit Experience Manager, Dynamic Media of beide. |
   | Publiceren vanuit Dynamic Media ongedaan maken | Selectieve publicatie | Alleen niet gepubliceerd vanuit Dynamic Media. |

1. Stel onder **[!UICONTROL Schedule]** de timing van de deactivering in.

   | Geselecteerd schema | Wat er gebeurt |
   | --- | --- |
   | Nu | De geselecteerde actie wordt onmiddellijk uitgevoerd. |
   | Later | De geselecteerde actie wordt uitgevoerd op de geselecteerde bepaalde datum en tijd. |

1. Tik in de rechterbovenhoek van de pagina **[!UICONTROL Manage Publication - Options]** op **[!UICONTROL Next]**.
1. (Optioneel) Controleer op de pagina **[!UICONTROL Manage Publication - Scope]** de kolom **[!UICONTROL Publish Target]** in de tabel voor de geselecteerde elementen.

   | Instelling Middelen publiceren in Dynamic Media-configuratie | Geselecteerde actie | Doel publiceren |
   | --- | --- | --- |
   | Onmiddellijk of <br>Bij activering | Publicatie | Experience Manager en Dynamic Media |
   | Onmiddellijk of <br>Bij activering | Publiceren naar Dynamic Media | Geen |
   | Selectieve publicatie | Publicatie | Experience Manager |
   | Selectieve publicatie | Publiceren naar Dynamic Media |  Dynamic Media  |
   | Onmiddellijk of <br>Bij activering | Publiceren ongedaan maken | Experience Manager en Dynamic Media |
   | Onmiddellijk of <br>Bij activering | Publiceren vanuit Dynamic Media ongedaan maken | Geen |
   | Selectieve publicatie | Publiceren ongedaan maken | Experience Manager |
   | Selectieve publicatie | Publiceren vanuit Dynamic Media ongedaan maken |  Dynamic Media  |

1. Voer op de pagina **[!UICONTROL Manage Publication - Scope]** een van de volgende handelingen uit:
   * Selecteer een of meer elementen die u uit publiceren of verwijderen.
   * Tik in de rechterbovenhoek van de pagina **[!UICONTROL Manage Publication - Scope]** op **[!UICONTROL Publish]** of **[!UICONTROL Unpublish]** om de handeling te starten.
1. Tik op **[!UICONTROL OK]**.

## De publicatiestatus van een element {#check-publish-status-of-asset} controleren

U kunt **[!UICONTROL Timeline]** met **[!UICONTROL Card view]**, **[!UICONTROL Column View]**, of **[!UICONTROL List View]** in Experience Manager gebruiken om de publicatiestatus van een element snel te controleren.

**De publicatiestatus van een element controleren:**

1. Tik in Experience Manager linksboven op de pagina op het logo van de Experience Manager om toegang te krijgen tot de algemene navigatieconsole. Tik links op de pagina op het navigatiepictogram (net boven het gereedschapspictogram) en tik op **[!UICONTROL Assets]** > **[!UICONTROL Files]**.
1. Open in **[!UICONTROL Card View]**, **[!UICONTROL Column View]** of **[!UICONTROL List View]** (onderstaande schermafbeelding geeft de **[!UICONTROL List View]** weer) een map met elementen die u hebt gepubliceerd of die u niet hebt gepubliceerd.
1. Selecteer een element, zodat dit met een vinkje wordt weergegeven. Zie onderstaande schermafbeelding.
1. Selecteer **[!UICONTROL Timeline]** in de linkerbovenhoek van de pagina in het keuzemenu. Het gebied **[!UICONTROL Status]** in het linkerpaneel toont de publicatiestatus van het geselecteerde element.
Wanneer u **[!UICONTROL List View]** gebruikt, verschijnt een extra kolom voor **[!UICONTROL Dynamic Media]** publicatiestatus.
   * In een map die is geconfigureerd voor synchronisatie met Dynamic Media, wordt standaard de **[!UICONTROL Dynamic Media]**-kolom weergegeven.
   * Als een map *not* is geconfigureerd voor synchronisatie met Dynamic Media, wordt de Dynamic Media-kolom niet weergegeven.
      ![Lijstweergave en tijdlijn](/help/assets/assets-dm/selective-publish-status-timeline.png)

## Problemen met Selectieve publicatie {#selective-publish-troubleshoot} oplossen

Een middel dat niet aan Dynamic Media wordt gesynchroniseerd maar een Dynamic Media publicatieactie teweegbrengt die op het in werking treedt resulteert in het volgende foutenbericht en de oplossing:

![Selectieve publicatiefout](/help/assets/assets-dm/selective-publish-error.png)
