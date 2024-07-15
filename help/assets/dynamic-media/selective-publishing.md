---
title: Werken met Selectieve Publish in Dynamic Media
description: Leer hoe u met Selective Publish werkt in Dynamic Media.
contentOwner: Rick Brough
topic-tags: dynamic-media
content-type: reference
docset: aem65
feature: Publishing,Dynamic Media
role: User
exl-id: a5a2df68-be13-45a6-ad80-09fbd2fea8f2
source-git-commit: 26afff3a39a2a80c1f730287b99f3fb33bff0673
workflow-type: tm+mt
source-wordcount: '2544'
ht-degree: 0%

---

# Selectieve Publish configureren op mapniveau in Dynamic Media {#selective-publish-configure-folder}

U kunt ervoor kiezen om elementen te publiceren naar of te verwijderen uit Adobe Experience Manager of Dynamic Media. U kunt dit op mapniveau doen met **[!UICONTROL Manage Publication]** of **[!UICONTROL Quick Publish]** . Deze publicatiemethode is handig omdat deze niet alleen afhankelijk is van de **[!UICONTROL Dynamic Media Configuration]** -server waarvan de instellingen voor alle mappen in uw Dynamic Media-instantie gelden.

Met selectief publiceren kunt u bijvoorbeeld werken aan elementen voor producten die nog niet actief zijn. In dat geval kan een marketingteam toegang krijgen tot afbeeldingen met slimme uitsnijdingen en dynamische vertoningen die zijn gesynchroniseerd met Dynamic Media. Ze kunnen promotiematerialen maken, zonder dat ze die middelen naar Dynamic Media hoeven te publiceren voor wereldwijde levering.

<!-- 
>[!IMPORTANT]
>
>Selective Publish is only available in Dynamic Media - Scene7 mode.
-->

>[!NOTE]
>
>*het kopiëren* activa aan en van omslagen ontruimt de publicatiestaat van die activa. Nochtans, wanneer u ** activa aan en van omslagen verplaatst het waarvan omslagbezit aan **[!UICONTROL Selective Publish]** wordt geplaatst, publiceert staat van die activa wordt gehandhaafd.

Als u later besluit de **[!UICONTROL Selective Publish]** -instellingen in een map te wijzigen, hebben deze wijzigingen alleen invloed op nieuwe elementen die u vanaf dat punt uploadt naar die map. De publicatiestatus van bestaande elementen in de map blijft ongewijzigd totdat u deze handmatig wijzigt vanuit **[!UICONTROL Quick Publish]** of het dialoogvenster **[!UICONTROL Manage Publication]** .

De optie voor mapniveau **[!UICONTROL Dynamic Media Publish mode]** is altijd standaard ingesteld op de waarde die u vindt in de instelling **[!UICONTROL Publish Assets]** in de **[!UICONTROL Dynamic Media Configuration]** . De volgende stappen in dit onderwerp tonen u echter hoe u deze standaardwaarde op mapniveau (zoals beschreven in de volgende stappen) handmatig wijzigt om de waarde **[!UICONTROL Dynamic Media Configuration]** te overschrijven.

Ongeacht of u erop vertrouwt:

* De waarde **[!UICONTROL Publish Assets]** die is ingesteld in **[!UICONTROL Dynamic Media Configuration]**
* Of de waarde **[!UICONTROL Dynamic Media Publish mode]** die is ingesteld in de eigenschappen op mapniveau

U kunt nog steeds **[!UICONTROL Immediately]** , **[!UICONTROL Upon Activation]** of **[!UICONTROL Selective Publish]** kiezen. U kunt bijvoorbeeld de waarde **[!UICONTROL Publish Assets]** in de **[!UICONTROL Dynamic Media Configuration]** instellen op **[!UICONTROL On Activation]** . En u kunt de waarde van de modus **[!UICONTROL Dynamic Media Publish]** op mapniveau instellen op **[!UICONTROL Selective Publish]** , omgekeerd, enzovoort.

Nadat u selectief publiceren in een omslag vormt, kunt u om het even welke volgend doen:

* [ publiceert selectief activa aan Dynamic Media of Experience Manager gebruikend leidt Publicatie ](#selective-publish-manage-publication).
* [ unpublish selectief activa van Dynamic Media of Experience Manager gebruikend leidt Publicatie ](#selective-unpublish-manage-publication).
* [ de activa van Publish aan Dynamic Media of Experience Manager die Snelle Publish gebruiken ](#quick-publish-aem-dm).
* [ publiceert of maakt selectief activa als onderzoeksresultaten ](#selective-publish-unpublish-search-results) ongedaan.

**om Selectieve Publish op het omslagniveau in Dynamic Media te vormen:**

1. In Experience Manager, selecteer het embleem van de Experience Manager om tot de globale navigatieconsole toegang te hebben. Selecteer aan de linkerkant het navigatiepictogram (net boven het pictogram Gereedschappen) en ga naar **[!UICONTROL Assets]** > **[!UICONTROL Files]** .
1. Voer een van de volgende handelingen uit:
   * Bewerk de eigenschappen van een bestaande map - Navigeer in **[!UICONTROL Card View]** , **[!UICONTROL Column View]** of **[!UICONTROL List View]** naar een map waarvan u de eigenschappen wilt bewerken. Selecteer de map en selecteer vervolgens op de werkbalk **[!UICONTROL Properties]** .
   * Bewerk de eigenschappen van een nieuwe map. Ga in **[!UICONTROL Card View]** , **[!UICONTROL Column View]** of **[!UICONTROL List View]** rechtsboven op de pagina naar **[!UICONTROL Create]** > **[!UICONTROL Folder]** . Voer in het dialoogvenster **[!UICONTROL Create Folder]** een (vereiste) titel voor de map in en selecteer vervolgens **[!UICONTROL Create]** . Selecteer de map en selecteer vervolgens op de werkbalk **[!UICONTROL Properties]** .

1. Selecteer een van de volgende opties in de vervolgkeuzelijst **[!UICONTROL Sync mode]** :

   | Synchronisatiemodus | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Inherited]** | Er staat geen expliciete synchronisatiewaarde in de map. In plaats daarvan neemt de map de synchronisatiewaarde over van een van de bovenliggende mappen of de standaardmodus die is ingesteld in de **[!UICONTROL Dynamic Media Configuration]** . De gedetailleerde status voor **[!UICONTROL Inherited]** wordt weergegeven als knopinfo. |
   | **[!UICONTROL Sync everything in this folder subtree to Dynamic Media]** | Voor het publiceren naar Dynamic Media moet u de middelen synchroniseren met Dynamic Media. Als u deze optie selecteert, worden alle elementen in deze substructuur opgenomen die u kunt synchroniseren met Dynamic Media. De mapspecifieke instellingen overschrijven de standaardinstelling in de **[!UICONTROL Dynamic Media Configuration]** . |
   | **[!UICONTROL Exclude everything in this folder subtree from Dynamic Media sync]** | Sluit alle elementen in deze substructuur uit van synchroniseren naar Dynamic Media. |

   ![ selectief niveau van de Omslag publiceert ](/help/assets/assets-dm/createfolder-properties-selectivepublish.png)

1. Selecteer een optie in de vervolgkeuzelijst **[!UICONTROL Dynamic Media Publish mode]** . De optie **[!UICONTROL Dynamic Media Publish mode]** is altijd standaard ingesteld op de waarde die is ingesteld in **[!UICONTROL Dynamic Media Configuration]** . U kunt deze standaardwaarde voor **[!UICONTROL Dynamic Media Configuration]** echter handmatig overschrijven met een van de volgende opties.

   >[!IMPORTANT]
   >
   >Ongeacht de Dynamic Media Publish wijzeoptie selecteert u, om het even welke updates u later aan activa maakt die *reeds* gepubliceerd is, worden die updates onmiddellijk gepubliceerd zonder enige verdere gebruikersactie.

   | Dynamic Media Publish-modus, optie | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Immediately]** | Wanneer elementen naar deze map worden geüpload, worden de elementen door het systeem in de Experience Manager ingevoerd en wordt de URL/Embed onmiddellijk weergegeven. Deze optie is alleen gekoppeld aan publicatie door Experience Managers en er is geen tussenkomst van de gebruiker nodig om elementen te publiceren.<br> Deze optie is *niet* beschikbaar als u **[!UICONTROL Exclude everything in this folder subtree from Dynamic Media sync]** in **[!UICONTROL Sync mode]** in de vorige stap selecteerde. |
   | **[!UICONTROL Upon Activation]** | Wanneer elementen naar deze map worden geüpload, moet u het element eerst expliciet publiceren voordat een koppeling URL/Embed wordt opgegeven. Deze optie is alleen gekoppeld aan publiceren via Experience Manager.<br> Deze optie is *niet* beschikbaar als u **[!UICONTROL Exclude everything in this folder subtree from Dynamic Media sync]** in **[!UICONTROL Sync mode]** in de vorige stap selecteerde. |
   | **[!UICONTROL Selective Publish]** | Assets wordt gepubliceerd naar keuze van Experience Manager of naar Dynamic Media voor levering in het publieke domein. Beide publicatiemethoden sluiten elkaar uit. Met andere woorden, u kunt elementen publiceren naar DMS7 zodat u functies zoals Slim uitsnijden of dynamische uitvoeringen kunt gebruiken. Of, kunt u activa uitsluitend aan Experience Manager voor veilige voorproef publiceren; die zelfde activa zijn *niet* gepubliceerd aan DMS7 voor levering in het openbare domein. Deze optie is niet beschikbaar als u in de vorige stap **[!UICONTROL Exclude everything in this folder subtree from Dynamic Media sync]** in **[!UICONTROL Sync mode]** hebt geselecteerd. |

1. Selecteer in de rechterbovenhoek van de pagina **[!UICONTROL Save & Close]** en selecteer vervolgens **[!UICONTROL OK]** om terug te keren naar Experience Manager Assets.

## Middelen selectief publiceren naar Dynamic Media of Experience Manager as a Cloud Service met Publicatie beheren{#selective-publish-manage-publication}

Voordat u **[!UICONTROL Manage Publication]** kunt gebruiken om elementen selectief te publiceren naar Dynamic Media of naar Experience Manager, moet u een van de volgende handelingen uitvoeren:

* Stel de optie **[!UICONTROL Publish Assets]** in op **[!UICONTROL Dynamic Media Configuration]** to **[!UICONTROL Selective Publish]** .
* Of, vormde selectieve het publiceren op het omslagniveau.

Zie [ een configuratie van Dynamic Media ](#configuring-dynamic-media-cloud-services) of [ vormen Selectieve Publish op het omslagniveau in Dynamic Media ](#selective-publish-configure-folder) creëren

<!--
>[!IMPORTANT]
>
>Selective Publish is only available in Dynamic Media - Scene7 mode.
-->

>[!NOTE]
>
>*het kopiëren* activa aan en van omslagen ontruimt de publicatiestaat van die activa. Nochtans, wanneer u ** activa aan en van omslagen verplaatst het waarvan omslagbezit aan **[!UICONTROL Selective Publish]** wordt geplaatst, publiceert staat van die activa wordt gehandhaafd.

**om activa aan Dynamic Media of Experience Manager selectief te publiceren as a Cloud Service het gebruiken leidt Publicatie:**

1. In Experience Manager, selecteer het embleem van de Experience Manager om tot de globale navigatieconsole toegang te hebben. Selecteer aan de linkerkant het navigatiepictogram (net boven het pictogram Gereedschappen) en ga naar **[!UICONTROL Assets]** > **[!UICONTROL Files]** .
1. Voer in **[!UICONTROL Card View]**, **[!UICONTROL Column View]** of **[!UICONTROL List View]** een van de volgende handelingen uit:
   * Navigeer naar een map waarvan u de elementen wilt publiceren. Selecteer de map en selecteer vervolgens op de werkbalk **[!UICONTROL Manage Publication]** . Gebruik **[!UICONTROL List View]** om de publicatiestatus van een bepaalde map gemakkelijker te kunnen controleren.
   * Navigeer naar een map waarvan u de elementen wilt publiceren. Open de map en selecteer vervolgens een of meer elementen. Selecteer **[!UICONTROL Manage Publication]** op de werkbalk. Gebruik **[!UICONTROL List View]** om de publicatiestatus van een bepaald element gemakkelijker te kunnen controleren.

     >[!NOTE]
     >
     >Als **[!UICONTROL Manage Publication]** niet op de werkbalk wordt weergegeven, selecteert u de knop voor weglatingsteken en selecteert u vervolgens **[!UICONTROL Manage Publication]** in het lijstmenu.

1. Selecteer op de pagina **[!UICONTROL Manage Publication - Options]** onder **[!UICONTROL Action]** het gewenste activeringstype.

   | Handeling | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Publish]** (naar Experience Manager) | Selecteer deze optie als u elementen naar de Experience Manager wilt publiceren voor een beveiligde voorvertoning. |
   | **[!UICONTROL Publish to Dynamic Media]** | Selecteer deze optie als u elementen naar Dynamic Media wilt publiceren voor levering in het publieke domein of als u functies wilt gebruiken, zoals Slim uitsnijden of Dynamische vertoningen.<br> Deze optie is beschikbaar slechts als **[!UICONTROL Dynamic Media Publish mode]** aan **[!UICONTROL Selective Publish]** in de eigenschappen van de omslag wordt geplaatst. |

1. Stel onder **[!UICONTROL Schedule]** de tijdinstelling van de publicatie in.

   | Schema | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Now]** | Selecteer deze optie om de elementen direct te publiceren. |
   | **[!UICONTROL Later]** | Selecteer deze optie om de elementen op een bepaalde datum en tijd te publiceren. |

1. Selecteer **[!UICONTROL Next]** in de rechterbovenhoek van de pagina **[!UICONTROL Manage Publication]** .
1. Voer op de pagina **[!UICONTROL Manage Publication - Scope]** een van de volgende handelingen uit:
   * Selecteer zo nodig een of meer elementen die u uit publicatie wilt verwijderen.
   * Selecteer **[!UICONTROL Publish]** of **[!UICONTROL Publish to Dynamic Media]** in de rechterbovenhoek van de pagina **[!UICONTROL Manage Publication - Scope]** .
1. Selecteer **[!UICONTROL OK]** .

### Publicatie van middelen van Dynamic Media of Experience Manager selectief ongedaan maken met Publicatie beheren {#selective-unpublish-manage-publication}

1. In Experience Manager, selecteer het embleem van de Experience Manager om tot de globale navigatieconsole toegang te hebben. Selecteer aan de linkerkant het navigatiepictogram (net boven het pictogram Gereedschappen) en ga naar **[!UICONTROL Assets]** > **[!UICONTROL Files]** .
1. Voer in **[!UICONTROL Card View]**, **[!UICONTROL Column View]** of **[!UICONTROL List View]** een van de volgende handelingen uit:
   * Navigeer naar een map waarvan u de publicatie ongedaan wilt maken. Selecteer de map en selecteer vervolgens op de werkbalk **[!UICONTROL Manage Publication]** . Gebruik **[!UICONTROL List View]** om de publicatiestatus van een bepaalde map gemakkelijker te kunnen controleren.
   * Navigeer naar een map waarvan u de publicatie ongedaan wilt maken. Open de map en selecteer vervolgens een of meer elementen. Selecteer **[!UICONTROL Manage Publication]** op de werkbalk. Gebruik **[!UICONTROL List View]** om de publicatiestatus van een bepaald element gemakkelijker te kunnen controleren.

     >[!NOTE]
     >
     >Als **[!UICONTROL Manage Publication]** niet op de werkbalk wordt weergegeven, selecteert u de knop voor weglatingsteken en selecteert u vervolgens **[!UICONTROL Manage Publication]** in het lijstmenu.

1. Selecteer op de pagina **[!UICONTROL Manage Publication - Options]** onder **[!UICONTROL Action]** het gewenste type deactivering.

   | Handeling | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Unpublish]** (van Experience Manager) | Selecteer deze optie als u de publicatie van elementen uit Experience Manager wilt opheffen. |
   | **[!UICONTROL Unpublish from Dynamic Media]** | Als u de publicatie van elementen uit Dynamic Media wilt opheffen, selecteert u deze optie.<br> Deze optie is beschikbaar slechts als **[!UICONTROL Dynamic Media Publish mode]** aan **[!UICONTROL Selective Publish]** in de eigenschappen van de omslag wordt geplaatst. |

1. Stel onder **[!UICONTROL Schedule]** de timing van de deactivering in.

   | Schema | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Now]** | Selecteer deze optie om de publicatie van de elementen direct ongedaan te maken. |
   | **[!UICONTROL Later]** | Selecteer deze optie om de publicatie van de elementen op een bepaalde datum en tijd ongedaan te maken. |

1. Selecteer **[!UICONTROL Next]** in de rechterbovenhoek van de pagina **[!UICONTROL Manage Publication]** .
1. Voer op de pagina **[!UICONTROL Manage Publication - Scope]** een van de volgende handelingen uit:
   * Selecteer een of meer elementen die u uit het ongedaan maken van de publicatie wilt verwijderen.
   * Selecteer **[!UICONTROL Unpublish]** of **[!UICONTROL Unpublish from Dynamic Media]** in de rechterbovenhoek van de pagina **[!UICONTROL Manage Publication - Scope]** .
1. Selecteer **[!UICONTROL OK]** .

## Publish-middelen naar Dynamic Media of Experience Manager met gebruik van Quick Publish {#quick-publish-aem-dm}

U kunt **[!UICONTROL Quick Publish]** gebruiken voor eenvoudige gevallen van activering van elementen. **[!UICONTROL Quick Publish]** publiceert de geselecteerde middelen onmiddellijk zonder verdere gebruikersinteractie. Niet-gepubliceerde verwijzingen worden ook automatisch gepubliceerd.

>[!NOTE]
>
>Als u **[!UICONTROL Quick Publish]** wilt gebruiken om elementen te publiceren naar Dynamic Media of Experience Manager, moet u ervoor zorgen dat **[!UICONTROL Selective Publish]** is ingeschakeld in uw **[!UICONTROL Dynamic Media Configuration]** of in de mapeigenschappen van de geselecteerde map.

**om activa aan Dynamic Media of Experience Manager te publiceren die Snelle Publish gebruiken:**

1. In Experience Manager, selecteer het embleem van de Experience Manager om tot de globale navigatieconsole toegang te hebben. Selecteer aan de linkerkant van de pagina het navigatiepictogram (net boven het pictogram Gereedschappen) en aan de rechterkant van de pagina gaat u naar **[!UICONTROL Assets]** > **[!UICONTROL Files]** .
1. Voer in **[!UICONTROL Card View]**, **[!UICONTROL Column View]** of **[!UICONTROL List View]** een van de volgende handelingen uit:
   * Navigeer naar een map waarvan u de elementen wilt publiceren. Selecteer de map en selecteer vervolgens op de werkbalk **[!UICONTROL Quick Publish]** . Gebruik **[!UICONTROL List View]** om de publicatiestatus van een bepaalde map gemakkelijker te kunnen controleren.
   * Navigeer naar een map waarvan u de elementen wilt publiceren. Open de map en selecteer vervolgens een of meer elementen. Selecteer **[!UICONTROL Quick Publish]** op de werkbalk. Gebruik **[!UICONTROL List View]** om de publicatiestatus van een bepaald element gemakkelijker te kunnen controleren.

     >[!NOTE]
     >
     >Als **[!UICONTROL Quick Publish]** niet op de werkbalk wordt weergegeven, selecteert u de knop voor weglatingsteken en selecteert u vervolgens **[!UICONTROL Quick Publish]** in het lijstmenu.

     ![ omslag-niveau Snelle Publish aan Dynamic Media ](/help/assets/assets-dm/selective-publish-folder-quick-publish-to-dm.png)

1. Selecteer een van de volgende opties in de menulijst van **[!UICONTROL Quick Publish]** .

   | Quick Publish, optie | Wat doet het? |
   | --- | --- | 
   | Publish naar Experience Manager | Hiermee publiceert u de geselecteerde elementen direct naar de Experience Manager. |
   | Publish naar Brand Portal | Hiermee publiceert u de geselecteerde elementen direct naar **[!UICONTROL Brand Portal]** .<br> Deze optie is slechts beschikbaar als uw instantie van Experience Manager Assets **[!UICONTROL Brand Portal]** reeds gevormd heeft. |
   | Publish naar Dynamic Media | Hiermee publiceert u de geselecteerde elementen direct naar Dynamic Media.<br> activa moeten reeds aan Dynamic Media worden gesynchroniseerd. Controleer, indien nodig, of **[!UICONTROL Sync mode]** in de eigenschappen van een map al is ingesteld op **[!UICONTROL Sync everything in this folder subtree to Dynamic Media]** . |

1. Selecteer **[!UICONTROL OK]** en selecteer vervolgens **[!UICONTROL Close]** .

## Elementen selectief publiceren of de publicatie ervan ongedaan maken via zoekresultaten {#selective-publish-unpublish-search-results}

In de zoekresultaten kunt u elementen uit verschillende middelenmappen met verschillende Dynamic Media-publicatie-instellingen weergeven. Als u een of meer elementen hebt geselecteerd in zoekresultaten en de elementen verschillende instellingen voor de Dynamic Media-publicatiemodus hebben, kunt u **[!UICONTROL Manage Publication]** activeren op de werkbalk om te publiceren of te publiceren.

Zie ook [ activa van het Onderzoek in Experience Manager ](/help/assets/search-assets.md).

**om activa als onderzoeksresultaten selectief te publiceren of unpublish:**

1. In Experience Manager, in de upper-left hoek van de pagina, selecteer het embleem van de Experience Manager om tot de globale navigatieconsole toegang te hebben. Selecteer links op de pagina het navigatiepictogram (net boven het pictogram Gereedschappen) en ga vervolgens naar **[!UICONTROL Assets]** > **[!UICONTROL Files]** .
1. Selecteer in de werkbalk rechtsboven op de pagina het pictogram Zoeken (vergrootglas).
1. Voer in het tekstveld **[!UICONTROL Type to search]** een trefwoord in en druk op **[!UICONTROL Enter]** .
1. Selecteer in de rechterbovenhoek van de pagina het pictogram **[!UICONTROL List View]** .
1. Selecteer het pictogram **[!UICONTROL Filters]** in de linkerbovenhoek van de pagina.

   ![ de Mening van de Lijst en Filters in onderzoeksresultaten ](/help/assets/assets-dm/select-publish-search-result.png)

1. Vouw in het linkerdeelvenster **[!UICONTROL Status]** uit en vouw vervolgens de **[!UICONTROL Dynamic Media]** zoekvoorspelling uit.
1. Gebruik de selectievakjes **[!UICONTROL Published]** en **[!UICONTROL Unpublished]** om de zoekresultaten verder te verfijnen op basis van de gepubliceerde status van Dynamic Media-elementen.
U kunt deze selectievakjes ook gebruiken met de zoekvoorspelling **[!UICONTROL Publish]** om de zoekresultaten van de elementen **[!UICONTROL Published]** en **[!UICONTROL Unpublished]** Experience Manager te verfijnen.
1. Voer een van de volgende handelingen uit:
   * Selecteer een of meer elementen die u wilt publiceren of maak de publicatie ongedaan.
   * Selecteer **[!UICONTROL Select All]** in de rechterbovenhoek van de pagina **[!UICONTROL Search Results]** .
1. Selecteer **[!UICONTROL Manage Publication]** op de werkbalk. Selecteer zo nodig het ellipsiepictogram op de werkbalk om **[!UICONTROL Manage Publication]** te zien.
1. Selecteer op de pagina **[!UICONTROL Manage Publication - Options]** de gewenste actie.

   | Geselecteerde actie | Publish Assets-instelling in Dynamic Media Configuration | Assets zijn |
   | --- | --- | --- |
   | Publish | Onmiddellijk of bij activering | Gepubliceerd aan Experience Manager en Dynamic Media. |
   | Publish | Selectieve Publish | Alleen gepubliceerd naar Experience Manager. |
   | Publiceren ongedaan maken | Onmiddellijk of bij activering | Niet gepubliceerd vanuit Experience Manager en Dynamic Media. |
   | Publiceren ongedaan maken | Selectieve Publish | Niet gepubliceerd alleen vanuit Experience Manager. |
   | Publish naar Dynamic Media | Onmiddellijk of bij activering | Niet gepubliceerd naar Experience Manager, Dynamic Media of beide. |
   | Publish naar Dynamic Media | Selectieve Publish | Alleen gepubliceerd naar Dynamic Media. |
   | Publiceren vanuit Dynamic Media ongedaan maken | Onmiddellijk of bij activering | Niet ongepubliceerd vanuit Experience Manager, Dynamic Media of beide. |
   | Publiceren vanuit Dynamic Media ongedaan maken | Selectieve Publish | Alleen niet gepubliceerd vanuit Dynamic Media. |

1. Stel onder **[!UICONTROL Schedule]** de timing van de deactivering in.

   | Geselecteerd schema | Wat gebeurt er? |
   | --- | --- |
   | Nu | De geselecteerde actie wordt onmiddellijk uitgevoerd. |
   | Later | De geselecteerde actie wordt uitgevoerd op de geselecteerde bepaalde datum en tijd. |

1. Selecteer **[!UICONTROL Next]** in de rechterbovenhoek van de pagina **[!UICONTROL Manage Publication - Options]** .
1. (Optioneel) Controleer op de pagina **[!UICONTROL Manage Publication - Scope]** de kolom **[!UICONTROL Publish Target]** in de tabel voor de geselecteerde elementen.

   | Publish Assets-instelling in Dynamic Media Configuration | Geselecteerde actie | Publish-doel |
   | --- | --- | --- |
   | Onmiddellijk of <br> op Activering | Publish | Experience Manager en Dynamic Media |
   | Onmiddellijk of <br> op Activering | Publish naar Dynamic Media | Geen |
   | Selectieve Publish | Publish | Experience Manager |
   | Selectieve Publish | Publish naar Dynamic Media | Dynamic Media |
   | Onmiddellijk of <br> op Activering | Publiceren ongedaan maken | Experience Manager en Dynamic Media |
   | Onmiddellijk of <br> op Activering | Publiceren vanuit Dynamic Media ongedaan maken | Geen |
   | Selectieve Publish | Publiceren ongedaan maken | Experience Manager |
   | Selectieve Publish | Publiceren vanuit Dynamic Media ongedaan maken | Dynamic Media |

1. Voer op de pagina **[!UICONTROL Manage Publication - Scope]** een van de volgende handelingen uit:
   * Selecteer een of meer elementen die u uit publiceren of verwijderen.
   * Selecteer **[!UICONTROL Publish]** of **[!UICONTROL Unpublish]** in de rechterbovenhoek van de pagina **[!UICONTROL Manage Publication - Scope]** om de handeling te starten.
1. Selecteer **[!UICONTROL OK]** .

## De publicatiestatus van een element controleren {#check-publish-status-of-asset}

U kunt **[!UICONTROL Timeline]** met **[!UICONTROL Card view]** , **[!UICONTROL Column View]** of **[!UICONTROL List View]** in Experience Manager gebruiken om snel de publicatiestatus van een element te controleren.

**om te controleren publiceert status van activa:**

1. In Experience Manager, in de upper-left hoek van de pagina, selecteer het embleem van de Experience Manager om tot de globale navigatieconsole toegang te hebben. Selecteer links op de pagina het navigatiepictogram (net boven het pictogram Gereedschappen) en ga vervolgens naar **[!UICONTROL Assets]** > **[!UICONTROL Files]** .
1. Open in **[!UICONTROL Card View]** , **[!UICONTROL Column View]** of **[!UICONTROL List View]** (in de onderstaande schermafbeelding ziet u de **[!UICONTROL List View]** ) een map met elementen die u hebt gepubliceerd of die u niet hebt gepubliceerd.
1. Selecteer een element, zodat dit met een vinkje wordt weergegeven. Zie onderstaande schermafbeelding.
1. Selecteer **[!UICONTROL Timeline]** in de linkerbovenhoek van de pagina in het keuzemenu. Het gebied **[!UICONTROL Status]** in het linkerpaneel toont de publicatiestatus van het geselecteerde element.
Wanneer u **[!UICONTROL List View]** gebruikt, wordt een extra kolom voor de publicatiestatus **[!UICONTROL Dynamic Media]** weergegeven.
   * In een map die is geconfigureerd voor synchronisatie met Dynamic Media, wordt standaard de kolom **[!UICONTROL Dynamic Media]** weergegeven.
   * Een omslag die *niet* wordt gevormd om aan Dynamic Media te synchroniseren toont niet de kolom van Dynamic Media.
     ![ de Mening van de Lijst en Chronologie ](/help/assets/assets-dm/selective-publish-status-timeline.png)

## Problemen met selectieve Publish oplossen {#selective-publish-troubleshoot}

Een middel dat niet aan Dynamic Media wordt gesynchroniseerd maar een Dynamic Media publicatieactie teweegbrengt die op het in werking treedt resulteert in het volgende foutenbericht en de oplossing:

![ Selectieve fout van Publish ](/help/assets/assets-dm/selective-publish-error.png)
