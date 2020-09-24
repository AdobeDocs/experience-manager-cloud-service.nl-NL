---
title: Werken met Selectief publiceren in dynamische media
description: Informatie over het werken met Selectieve publicatie in dynamische media.
contentOwner: Rick Brough
topic-tags: dynamic-media
content-type: reference
docset: aem65
translation-type: tm+mt
source-git-commit: 04f40452ca89bc5298341b4338bc1d7762b908c2
workflow-type: tm+mt
source-wordcount: '2526'
ht-degree: 1%

---


# Selectieve publicatie op mapniveau configureren in Dynamic Media {#selective-publish-configure-folder}

U kunt ervoor kiezen om elementen naar of van AEM of Dynamic Media op mapniveau te publiceren of de publicatie ervan ongedaan te maken. U kunt hiervoor kiezen **[!UICONTROL Manage Publication]** of **[!UICONTROL Quick Publish]** in plaats van alleen te vertrouwen op de mappen **[!UICONTROL Dynamic Media Configuration]** waarvan de instellingen algemeen zijn voor alle mappen in de instantie Dynamic Media.

Met selectief publiceren kunt u bijvoorbeeld werken aan elementen voor producten die nog niet actief zijn. In een dergelijk geval heeft een marketingteam toegang tot SmartCrop-afbeeldingen en dynamische uitvoeringen die zijn gesynchroniseerd met Dynamic Media, zodat ze promotiemateriaal kunnen maken, zonder dat ze deze elementen hoeven te publiceren naar Dynamic Media voor wereldwijde levering.

<!-- 
>[!IMPORTANT]
>
>Selective Publish is only available in Dynamic Media - Scene7 mode.
-->

>[!NOTE]
>
>*Door elementen naar en van mappen te kopiëren* , wordt de publicatiestatus van deze elementen gewist. Wanneer u echter elementen *verplaatst* van en naar mappen waarvan de mapeigenschap is ingesteld op **[!UICONTROL Selective Publish]**, blijft de publicatiestatus van deze elementen behouden.

Als u later besluit om de **[!UICONTROL Selective Publish]** instellingen in een map te wijzigen, zijn deze wijzigingen alleen van toepassing op nieuwe elementen die u vanaf dat punt uploadt naar die map. De publicatiestatus van bestaande elementen in de map blijft ongewijzigd totdat u deze handmatig wijzigt vanuit een **[!UICONTROL Quick Publish]** van beide of het **[!UICONTROL Manage Publication]** dialoogvenster.

De optie van het omslagniveau **[!UICONTROL Dynamic Media Publish mode]** blijft altijd aan de waarde in gebreke die in het **[!UICONTROL Publish Assets]** plaatsen in uw **[!UICONTROL Dynamic Media Configuration.]** De volgende stappen in dit onderwerp wordt gevonden, echter, toont u hoe te om deze standaardwaarde op het omslagniveau (zoals die in de volgende stappen wordt beschreven) manueel te veranderen om de **[!UICONTROL Dynamic Media Configuration]** waarde met voeten te treden.

Ongeacht of u afhankelijk bent van de **[!UICONTROL Publish Assets]** waarde ingesteld in **[!UICONTROL Dynamic Media Configuration]**, of de **[!UICONTROL Dynamic Media Publish mode]** waarde ingesteld in de eigenschappen op mapniveau, kunt u nog steeds kiezen **[!UICONTROL Immediately]**, **[!UICONTROL Upon Activation]** of **[!UICONTROL Selective Publish.]** u kunt bijvoorbeeld de **[!UICONTROL Publish Assets]** waarde in uw **[!UICONTROL Dynamic Media Configuration]** instelling instellen op **[!UICONTROL Upon Activation]**, maar u kunt de waarde van de **[!UICONTROL Dynamic Media Publish]** **[!UICONTROL Selective Publish]** modus op mapniveau instellen op , andersom enzovoort.

Nadat u selectief publiceren in een omslag vormt, kunt u om het even welke volgend doen:

* [Publiceer selectief middelen naar Dynamic Media of AEM met Publicatie beheren.](#selective-publish-manage-publication)
* [Publiceer selectief elementen van Dynamic Media of AEM met Publicatie beheren.](#selective-unpublish-manage-publication)
* [Elementen publiceren naar dynamische media of AEM met Snel publiceren.](#quick-publish-aem-dm)
* [Publiceer elementen selectief of maak de publicatie ongedaan in de vorm van zoekresultaten.](#selective-publish-unpublish-search-results)

**Selectieve publicatie op mapniveau in Dynamic Media configureren**

1. Tik in AEM op het AEM om toegang te krijgen tot de globale navigatieconsole. Tik links op het navigatiepictogram (net boven het pictogram Gereedschappen) en tik vervolgens op **[!UICONTROL Assets > Files.]**
1. Voer een van de volgende handelingen uit:
   * Bewerk de eigenschappen van een bestaande map. Navigeer naar een map waarvan u de eigenschappen wilt bewerken. **[!UICONTROL Card View]** Ga naar **[!UICONTROL Column View]****[!UICONTROL List View]** de map. Selecteer de map, tik vervolgens op de werkbalk **[!UICONTROL Properties.]**
   * Bewerk de eigenschappen van een nieuwe map - In **[!UICONTROL Card View]**, **[!UICONTROL Column View]** of **[!UICONTROL List View]**, in de rechterbovenhoek van de pagina, tik **[!UICONTROL Create > Folder.]** in het **[!UICONTROL Create Folder]** dialoogvenster, voer een titel (vereist) voor de map in, tik vervolgens op **[!UICONTROL Create.]** Selecteer de map, tik vervolgens op de werkbalk op **[!UICONTROL Properties.]**

1. In the **[!UICONTROL Sync mode]** drop-down list, select one of the following:

   | Synchronisatiemodus | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Inherited]** | Geen expliciete synchronisatiewaarde in de map; in plaats daarvan, erft de omslag de synchronisatiewaarde van één van zijn voorouderomslagen of de standaardwijze die in uw **[!UICONTROL Dynamic Media Configuration.]** gedetailleerde status voor **[!UICONTROL Inherited]** toont door tooltip wordt geplaatst. |
   | **[!UICONTROL Sync everything in this folder sub-tree to dynamicmedia]** | Voor het publiceren naar dynamische media moet u de elementen synchroniseren met Dynamic Media. Als u deze optie selecteert, worden alle elementen in deze substructuur opgenomen voor synchronisatie met dynamische media. De mapspecifieke instellingen overschrijven de standaardinstelling in het dialoogvenster **[!UICONTROL Dynamic Media Configuration.]** |
   | **[!UICONTROL Exclude everything in this folder sub-tree from dynamicmedia sync]** | Sluit alle elementen in deze substructuur uit van synchroniseren naar dynamische media. |

   ![Selectieve publicatie op mapniveau](/help/assets/assets-dm/createfolder-properties-selectivepublish.png)

1. Selecteer een optie in de **[!UICONTROL Dynamic Media Publish mode]** vervolgkeuzelijst. Houd er rekening mee dat de **[!UICONTROL Dynamic Media Publish mode]** optie altijd standaard de waarde heeft die is ingesteld in het **[!UICONTROL Dynamic Media Configuration.]** dialoogvenster U kunt deze **[!UICONTROL Dynamic Media Configuration]** standaardwaarde echter handmatig overschrijven door een van de volgende opties te gebruiken.

   >[!IMPORTANT]
   >
   >Ongeacht de optie voor dynamische media-publicatie die u selecteert, worden updates die u later maakt voor een element dat *al* is gepubliceerd, onmiddellijk gepubliceerd zonder tussenkomst van de gebruiker.

   | Dynamische media publiceren, optie | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Immediately]** | Wanneer middelen naar deze map worden geüpload, neemt het systeem de elementen in AEM en wordt de URL/Embed onmiddellijk weergegeven. Deze optie is alleen gekoppeld aan AEM publicatie en er is geen tussenkomst van de gebruiker nodig om elementen te publiceren.<br>Deze optie is *niet* beschikbaar als u **[!UICONTROL Exclude everything in this folder sub-tree from dynamicmedia sync]** in **[!UICONTROL Sync mode]** de vorige stap hebt geselecteerd. |
   | **[!UICONTROL Upon Activation]** | Wanneer elementen naar deze map worden geüpload, moet u het element eerst expliciet publiceren voordat er een koppeling URL/Embed wordt opgegeven. Deze optie is alleen gekoppeld aan AEM publiceren.<br>Deze optie is *niet* beschikbaar als u **[!UICONTROL Exclude everything in this folder sub-tree from dynamicmedia sync]** in **[!UICONTROL Sync mode]** de vorige stap hebt geselecteerd. |
   | **[!UICONTROL Selective Publish]** | De activa worden gepubliceerd aan uw keus van of AEM of aan Dynamische Media voor levering in het openbare domein. Beide publicatiemethoden sluiten elkaar uit.  Met andere woorden, u kunt elementen publiceren naar DMS7 zodat u functies zoals Slim uitsnijden of dynamische uitvoeringen kunt gebruiken. U kunt ook uitsluitend elementen publiceren naar AEM voor een beveiligde voorvertoning. dezelfde activa worden *niet* aan DMS7 gepubliceerd voor levering in het publieke domein. Deze optie is niet beschikbaar als u **[!UICONTROL Exclude everything in this folder sub-tree from dynamicmedia sync]** in **[!UICONTROL Sync mode]** de vorige stap hebt geselecteerd. |

1. Tik in de rechterbovenhoek van de pagina op **[!UICONTROL Save & Close]** en tik vervolgens **[!UICONTROL OK]** om terug te keren naar AEM Assets.

## Elementen selectief publiceren naar Dynamic Media of AEM als Cloud Service met Publicatie beheren{#selective-publish-manage-publication}

Voordat u elementen selectief kunt publiceren naar Dynamic Media of om ze te AEM, moet u de **[!UICONTROL Manage Publication]** optie instellen **[!UICONTROL Publish Assets]** op **[!UICONTROL Dynamic Media Configuration]** **[!UICONTROL Selective Publish]** of selectief publiceren op mapniveau configureren.

Zie [Creating a Dynamic Media Configuration](#configuring-dynamic-media-cloud-services) or [Configuring selected publishing at the folder level in Dynamic Media](#selective-publish-configure-folder)

<!--
>[!IMPORTANT]
>
>Selective Publish is only available in Dynamic Media - Scene7 mode.
-->

>[!NOTE]
>
>*Door elementen naar en van mappen te kopiëren* , wordt de publicatiestatus van deze elementen gewist. Wanneer u echter elementen *verplaatst* van en naar mappen waarvan de mapeigenschap is ingesteld op **[!UICONTROL Selective Publish]**, blijft de publicatiestatus van deze elementen behouden.

**Elementen selectief publiceren naar Dynamic Media of AEM als Cloud Service met Publicatie beheren**

1. Tik in AEM op het AEM om toegang te krijgen tot de globale navigatieconsole. Tik links op het navigatiepictogram (net boven het pictogram Gereedschappen) en tik vervolgens op **[!UICONTROL Assets > Files.]**
1. Voer bij **[!UICONTROL Card View]**, **[!UICONTROL Column View]** of **[!UICONTROL List View]** een van de volgende handelingen uit:
   * Navigeer naar een map waarvan u de elementen wilt publiceren. Selecteer de map en tik vervolgens op de werkbalk op **[!UICONTROL Manage Publication.]** Mogelijk is het handig om deze te gebruiken, **[!UICONTROL List View]** zodat u de publicatiestatus van een bepaalde map eenvoudiger kunt controleren.
   * Navigeer naar een map waarvan u de elementen wilt publiceren. Open de map en selecteer vervolgens een of meer elementen. Tik op de werkbalk op **[!UICONTROL Manage Publication.]** U kunt het handig vinden om de publicatiestatus van een bepaald element te controleren **[!UICONTROL List View]** zodat u deze eenvoudiger kunt controleren.

      >[!NOTE]
      >
      >Als dit niet op de werkbalk wordt weergegeven, tikt u op de knop Ovaal en selecteert u **[!UICONTROL Manage Publication]** **[!UICONTROL Manage Publication]** in het lijstmenu.

1. Selecteer op de **[!UICONTROL Manage Publication - Options]** pagina onder **[!UICONTROL Action]** het gewenste activeringstype.

   | Actie | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Publish]** (tot AEM) | Selecteer deze optie als u elementen wilt publiceren die u wilt AEM voor een beveiligde voorvertoning. |
   | **[!UICONTROL Publish to Dynamic Media]** | Selecteer deze optie om elementen naar dynamische media te publiceren voor levering in het publieke domein of zodat u functies zoals Slim uitsnijden of dynamische uitvoeringen kunt gebruiken.<br>Deze optie is alleen beschikbaar als **[!UICONTROL Dynamic Media Publish mode]** deze is ingesteld op **[!UICONTROL Selective Publish]** in de eigenschappen van de map. |

1. Stel onder **[!UICONTROL Schedule]** de tijdinstellingen van de publicatie in.

   | Schema | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Now]** | Selecteer deze optie om de elementen direct te publiceren. |
   | **[!UICONTROL Later]** | Selecteer deze optie om de elementen op een bepaalde datum en tijd te publiceren. |

1. Tik in de rechterbovenhoek van de **[!UICONTROL Manage Publication]** pagina op **[!UICONTROL Next.]**
1. Voer op de **[!UICONTROL Manage Publication - Scope]** pagina een van de volgende handelingen uit:
   * Selecteer zo nodig een of meer elementen die u uit publicatie wilt verwijderen.
   * In the upper-right corner of the **[!UICONTROL Manage Publication - Scope]** page, tap **[!UICONTROL Publish]** or **[!UICONTROL Publish to Dynamic Media.]**
1. Tik op **[!UICONTROL OK.]**

### Publicatie van middelen via Dynamic Media selectief ongedaan maken of AEM met Publicatie beheren {#selective-unpublish-manage-publication}

1. Tik in AEM op het AEM om toegang te krijgen tot de globale navigatieconsole. Tik links op het navigatiepictogram (net boven het pictogram Gereedschappen) en tik vervolgens op **[!UICONTROL Assets > Files.]**
1. Voer bij **[!UICONTROL Card View]**, **[!UICONTROL Column View]** of **[!UICONTROL List View]** een van de volgende handelingen uit:
   * Navigeer naar een map waarvan u de publicatie ongedaan wilt maken. Selecteer de map en tik vervolgens op de werkbalk op **[!UICONTROL Manage Publication.]** Mogelijk is het handig om deze te gebruiken, **[!UICONTROL List View]** zodat u de publicatiestatus van een bepaalde map eenvoudiger kunt controleren.
   * Navigeer naar een map waarvan u de publicatie ongedaan wilt maken. Open de map en selecteer vervolgens een of meer elementen. Tik op de werkbalk op **[!UICONTROL Manage Publication.]** U kunt het handig vinden om de publicatiestatus van een bepaald element te controleren **[!UICONTROL List View]** zodat u deze eenvoudiger kunt controleren.

      >[!NOTE]
      >
      >Als dit niet op de werkbalk wordt weergegeven, tikt u op de knop Ovaal en selecteert u **[!UICONTROL Manage Publication]** **[!UICONTROL Manage Publication]** in het lijstmenu.

1. Selecteer op de **[!UICONTROL Manage Publication - Options]** pagina onder **[!UICONTROL Action]** het gewenste type deactivering.

   | Actie | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Unpublish]** (van AEM) | Selecteer deze optie als u de publicatie van elementen uit AEM wilt opheffen. |
   | **[!UICONTROL Unpublish from Dynamic Media]** | Selecteer deze optie als u de publicatie van elementen van Dynamic Media ongedaan wilt maken.<br>Deze optie is alleen beschikbaar als **[!UICONTROL Dynamic Media Publish mode]** deze is ingesteld op **[!UICONTROL Selective Publish]** in de eigenschappen van de map. |

1. Stel onder **[!UICONTROL Schedule]** de timing van de deactivering in.

   | Schema | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Now]** | Selecteer deze optie om de publicatie van de elementen direct ongedaan te maken. |
   | **[!UICONTROL Later]** | Selecteer deze optie om de publicatie van de elementen op een bepaalde datum en tijd ongedaan te maken. |

1. Tik in de rechterbovenhoek van de **[!UICONTROL Manage Publication]** pagina op **[!UICONTROL Next.]**
1. Voer op de **[!UICONTROL Manage Publication - Scope]** pagina een van de volgende handelingen uit:
   * Selecteer een of meer elementen die u uit het ongedaan maken van de publicatie wilt verwijderen.
   * In the upper-right corner of the **[!UICONTROL Manage Publication - Scope]** page, tap **[!UICONTROL Unpublish]** or **[!UICONTROL Unpublish from Dynamic Media.]**
1. Tik op **[!UICONTROL OK.]**

## Elementen publiceren naar dynamische media of AEM met Snel publiceren {#quick-publish-aem-dm}

U kunt **[!UICONTROL Quick Publish]** voor eenvoudige gevallen van activering van middelen gebruiken. **[!UICONTROL Quick Publish]** publiceert de geselecteerde middelen onmiddellijk zonder verdere gebruikersinteractie. Daarom worden niet-gepubliceerde verwijzingen ook automatisch gepubliceerd.

>[!NOTE]
>
>Als u elementen wilt gebruiken **[!UICONTROL Quick Publish]** om elementen te publiceren naar Dynamic Media of AEM, moet u controleren of **[!UICONTROL Selective Publish]** deze optie is ingeschakeld in uw **[!UICONTROL Dynamic Media Configuration]** map of in de mapeigenschappen van de geselecteerde map.

**Elementen publiceren naar dynamische media of AEM met Snel publiceren**

1. Tik in AEM op het AEM om toegang te krijgen tot de globale navigatieconsole. Tik links op de pagina op het navigatiepictogram (net boven het pictogram Gereedschappen) en tik vervolgens rechts op de pagina op **[!UICONTROL Assets > Files.]**
1. Voer bij **[!UICONTROL Card View]**, **[!UICONTROL Column View]** of **[!UICONTROL List View]** een van de volgende handelingen uit:
   * Navigeer naar een map waarvan u de elementen wilt publiceren. Selecteer de map en tik vervolgens op de werkbalk op **[!UICONTROL Quick Publish.]** Mogelijk is het handig om deze te gebruiken, **[!UICONTROL List View]** zodat u de publicatiestatus van een bepaalde map eenvoudiger kunt controleren.
   * Navigeer naar een map waarvan u de elementen wilt publiceren. Open de map en selecteer vervolgens een of meer elementen. Tik op de werkbalk op **[!UICONTROL Quick Publish.]** U kunt het handig vinden om de publicatiestatus van een bepaald element te controleren **[!UICONTROL List View]** zodat u deze eenvoudiger kunt controleren.

      >[!NOTE]
      >
      >Als dit niet op de werkbalk wordt weergegeven, tikt u op de knop Ovaal en selecteert u **[!UICONTROL Quick Publish]** **[!UICONTROL Quick Publish]** in het lijstmenu.

      ![Snel publiceren op mapniveau naar dynamische media](/help/assets/assets-dm/selective-publish-folder-quick-publish-to-dm.png)

1. Selecteer een van de volgende opties in de **[!UICONTROL Quick Publish]** menulijst.

   | Snel publiceren, optie | Wat het doet |
   | --- | --- | 
   | Publiceren naar AEM | Hiermee publiceert u de geselecteerde elementen direct naar AEM. |
   | Publiceren naar Brand Portal | Hiermee publiceert u de geselecteerde elementen direct naar **[!UICONTROL Brand Portal.]**<br>Deze optie is alleen beschikbaar als uw AEM Assets-instantie **[!UICONTROL Brand Portal]**al is geconfigureerd. |
   | Publiceren naar dynamische media | Hiermee publiceert u de geselecteerde elementen direct naar Dynamic Media.<br>Een middel moet reeds aan Dynamische Media worden gesynchroniseerd. Indien nodig, zorg ervoor dat **[!UICONTROL Sync mode]** in de eigenschappen van een omslag reeds wordt geplaatst aan **[!UICONTROL Sync everything in this folder sub-tree to dynamicmedia.]** |

1. Tik **[!UICONTROL OK,]** vervolgens op **[!UICONTROL Close,]**

## Elementen selectief publiceren of de publicatie ervan ongedaan maken door middel van zoekresultaten {#selective-publish-unpublish-search-results}

In de zoekresultaten kunt u elementen uit verschillende elementmappen met verschillende publicatie-instellingen voor Dynamische media weergeven. Wanneer u een of meer elementen hebt geselecteerd in zoekresultaten en de elementen verschillende instellingen voor de publicatiemodus Dynamische media hebben, kunt u **[!UICONTROL Manage Publication]** vanaf de werkbalk een trigger voor publiceren of verwijderen.

Zie ook Middelen [zoeken in AEM.](/help/assets/search-assets.md)

**Elementen selectief publiceren of verwijderen via zoekresultaten**

1. Tik in AEM, linksboven op de pagina, op het AEM logo om toegang te krijgen tot de algemene navigatieconsole. Tik links op de pagina op het navigatiepictogram (net boven het pictogram Gereedschappen) en tik vervolgens op **[!UICONTROL Assets > Files.]**
1. Tik in de werkbalk rechtsboven op de pagina op het pictogram Zoeken (vergrootglas).
1. Voer in het **[!UICONTROL Type to search]** tekstveld een trefwoord in en druk op **[!UICONTROL Enter.]**
1. Tik in de rechterbovenhoek van de pagina op het **[!UICONTROL List View]** pictogram.
1. Near the upper-left corner of the page, tap the **[!UICONTROL Filters]** icon.

   ![Lijstweergave en filters in zoekresultaten](/help/assets/assets-dm/select-publish-search-result.png)

1. Vouw in het linkerdeelvenster uit **[!UICONTROL Status]** en vouw vervolgens de **[!UICONTROL Dynamic Media]** zoekvoorspelling uit.
1. Gebruik de selectievakjes **[!UICONTROL Published]** en **[!UICONTROL Unpublished]** om de zoekresultaten verder te verfijnen op basis van de gepubliceerde status van Dynamic Media-elementen.
U kunt deze selectievakjes ook gebruiken in combinatie met de zoekvoorspelling om de zoekresultaten van elementen **[!UICONTROL Publish]** en **[!UICONTROL Published]** **[!UICONTROL Unpublished]** AEM te verfijnen.
1. Voer een van de volgende handelingen uit:
   * Selecteer een of meer elementen die u wilt publiceren of waarvan u de publicatie ongedaan wilt maken.
   * Near the upper-right corner of the **[!UICONTROL Search Results]** page, tap **[!UICONTROL Select All.]**
1. Tik op de werkbalk op **[!UICONTROL Manage Publication.]** Mogelijk moet u tikken op het ellipsiepictogram op de werkbalk om te zien **[!UICONTROL Manage Publication.]**
1. Selecteer de gewenste actie op de **[!UICONTROL Manage Publication - Options]** pagina.

   | Geselecteerde actie | Instelling Middelen publiceren in dynamische mediaconfiguratie | Elementen zijn |
   | --- | --- | --- |
   | Publicatie | Onmiddellijk of bij activering | Gepubliceerd naar AEM en dynamische media. |
   | Publicatie | Selectieve publicatie | Alleen naar AEM gepubliceerd. |
   | Publiceren ongedaan maken | Onmiddellijk of bij activering | Niet gepubliceerd via AEM en Dynamic Media. |
   | Publiceren ongedaan maken | Selectieve publicatie | Alleen niet gepubliceerd vanuit AEM. |
   | Publiceren naar dynamische media | Onmiddellijk of bij activering | Niet gepubliceerd naar AEM, of Dynamic Media, of beide. |
   | Publiceren naar dynamische media | Selectieve publicatie | Alleen gepubliceerd naar dynamische media. |
   | Publiceren van dynamische media ongedaan maken | Onmiddellijk of bij activering | Niet ongepubliceerd van AEM, of Dynamic Media, of beide. |
   | Publiceren van dynamische media ongedaan maken | Selectieve publicatie | Niet gepubliceerd met alleen Dynamic Media. |

1. Stel onder **[!UICONTROL Schedule]** de timing van de deactivering in.

   | Geselecteerd schema | Wat er gebeurt |
   | --- | --- |
   | Nu | De geselecteerde actie wordt onmiddellijk uitgevoerd. |
   | Later | De geselecteerde actie wordt uitgevoerd op de geselecteerde bepaalde datum en tijd. |

1. Tik in de rechterbovenhoek van de **[!UICONTROL Manage Publication - Options]** pagina op **[!UICONTROL Next.]**
1. (Optioneel) Controleer op de **[!UICONTROL Manage Publication - Scope]** pagina de **[!UICONTROL Publish Target]** kolom in de tabel voor de geselecteerde elementen.

   | Instelling Middelen publiceren in dynamische mediaconfiguratie | Geselecteerde actie | Doel publiceren |
   | --- | --- | --- |
   | Onmiddellijk of <br>na activering | Publicatie | AEM en dynamische media |
   | Onmiddellijk of <br>na activering | Publiceren naar dynamische media | Geen |
   | Selectieve publicatie | Publicatie | AEM |
   | Selectieve publicatie | Publiceren naar dynamische media |  Dynamic Media  |
   | Onmiddellijk of <br>na activering | Publiceren ongedaan maken | AEM en dynamische media |
   | Onmiddellijk of <br>na activering | Publiceren van dynamische media ongedaan maken | Geen |
   | Selectieve publicatie | Publiceren ongedaan maken | AEM |
   | Selectieve publicatie | Publiceren van dynamische media ongedaan maken |  Dynamic Media  |

1. Voer op de **[!UICONTROL Manage Publication - Scope]** pagina een van de volgende handelingen uit:
   * Selecteer een of meer elementen die u uit publiceren of verwijderen.
   * In the upper-right corner of the **[!UICONTROL Manage Publication - Scope]** page, tap **[!UICONTROL Publish]** or **[!UICONTROL Unpublish]** to begin the action.
1. Tik op **[!UICONTROL OK.]**

## De publicatiestatus van een element controleren {#check-publish-status-of-asset}

U kunt **[!UICONTROL Timeline]** met **[!UICONTROL Card view]**, **[!UICONTROL Column View]****[!UICONTROL List View]** of in AEM gebruiken om snel de publicatiestatus van een element te controleren.

**De publicatiestatus van een element controleren**

1. Tik in AEM, linksboven op de pagina, op het AEM logo om toegang te krijgen tot de algemene navigatieconsole. Tik links op de pagina op het navigatiepictogram (net boven het pictogram Gereedschappen) en tik vervolgens op **[!UICONTROL Assets > Files.]**
1. Open in **[!UICONTROL Card View]**, **[!UICONTROL Column View]** of **[!UICONTROL List View]** (onderstaande schermafbeelding toont het **[!UICONTROL List View]**) een map met elementen die u hebt gepubliceerd of niet hebt gepubliceerd.
1. Selecteer een element, zodat dit met een vinkje wordt weergegeven. Zie onderstaande schermafbeelding.
1. Selecteer in de linkerbovenhoek van de pagina in het keuzemenu **[!UICONTROL Timeline.]** Het **[!UICONTROL Status]** gebied in het linkerdeelvenster om de publicatiestatus van het geselecteerde element weer te geven.
Als u **[!UICONTROL List View]** een extra kolom gebruikt voor de **[!UICONTROL Dynamic Media]** publicatiestatus, wordt er een extra kolom weergegeven.
   * Een omslag die aan synchronisatie aan Dynamische Media wordt gevormd zal de **[!UICONTROL Dynamic Media]** kolom door gebrek tonen.
   * Een map die *niet* is geconfigureerd voor synchronisatie met Dynamic Media, geeft de kolom Dynamische media niet weer.
      ![Lijstweergave en tijdlijn](/help/assets/assets-dm/selective-publish-status-timeline.png)

## Problemen met selectief publiceren oplossen {#selective-publish-troubleshoot}

Een middel dat niet aan Dynamische Media wordt gesynchroniseerd maar een Dynamische Media heeft publicatieactie teweeggebracht op het resulteert in het volgende foutenbericht en de oplossing:

![Selectieve publicatiefout](/help/assets/assets-dm/selective-publish-error.png)

