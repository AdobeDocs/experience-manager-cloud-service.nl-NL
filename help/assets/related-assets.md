---
title: Verwante activa
description: Leer hoe u elementen koppelt die bepaalde algemene kenmerken delen. U kunt de eigenschap ook gebruiken om bron/afgeleide verhoudingen tussen activa tot stand te brengen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# Verwante activa {#related-assets}

Met de functie Verwante elementen kunt u elementen handmatig koppelen op basis van de behoeften van uw organisatie. U kunt bijvoorbeeld een licentiebestand koppelen aan een element of aan een afbeelding/video over een vergelijkbaar onderwerp. U kunt elementen die bepaalde algemene kenmerken delen, aan elkaar koppelen. U kunt de eigenschap ook gebruiken om bron/afgeleide verhoudingen tussen activa tot stand te brengen. Als u bijvoorbeeld een PDF-bestand hebt dat is gegenereerd vanuit een INDD-bestand, kunt u het PDF-bestand koppelen aan het INDD-bronbestand.

Op deze manier hebt u de flexibiliteit om een bestand met een lage resolutie (bijvoorbeeld PDF/JPG) te delen aan leveranciers/agentschappen en het bestand met een hoge resolutie (bijvoorbeeld INDD) alleen op verzoek beschikbaar te maken.

## Relatieve elementen {#relating-assets}

1. Open vanuit de interface Middelen de pagina met eigenschappen voor een element dat u wilt koppelen. U kunt ook het element selecteren in de lijstweergave. U kunt het element ook selecteren in een verzameling.
1. Als u een ander element wilt koppelen aan het element dat u hebt geselecteerd, klikt of tikt u op het pictogram **[!UICONTROL Relate]** op de werkbalk.
1. Voer een van de volgende handelingen uit:

   * Als u het bronbestand voor het element wilt koppelen, selecteert u **[!UICONTROL Bron]** in de lijst.
   * Als u een afgeleid bestand wilt koppelen, selecteert u **[!UICONTROL Afgeleid]** van de lijst.
   * Als u een relatie in twee richtingen wilt maken tussen de elementen, selecteert u **[!UICONTROL Overige]** in de lijst.

1. Navigeer in het scherm **[!UICONTROL Element]** selecteren naar de locatie van het element dat u wilt koppelen en selecteer het.

1. Klik op het pictogram **[!UICONTROL Bevestigen]** of tik erop.
1. Klik op **[!UICONTROL OK]** of tik erop om het dialoogvenster te sluiten. Afhankelijk van uw keuze voor relatie in stap 3 wordt het gerelateerde actief vermeld onder een geschikte categorie in de **[!UICONTROL verwante]** sectie. Als het element dat u hebt verwant bijvoorbeeld het bronbestand voor het huidige element is, wordt het weergegeven onder **[!UICONTROL Bron]**.
1. Als u de koppeling tussen een element wilt verbreken, klikt of tikt u op het pictogram **[!UICONTROL Verhouding ongedaan maken]** op de werkbalk.
1. Selecteer de elementen die u niet wilt koppelen in het dialoogvenster Relaties **** verwijderen en klik op **[!UICONTROL Onafhankelijk]** maken.
1. Klik op **[!UICONTROL OK]** of Tik op OK om het dialoogvenster te sluiten. De activa waarvoor u betrekkingen schrapte worden geschrapt van de lijst van verwante activa onder de **[!UICONTROL Verwante]** sectie.

## Gerelateerde elementen vertalen {#translating-related-assets}

Het maken van bron-/afgeleide relaties tussen elementen met de functie Verwante elementen is ook handig in vertaalworkflows. Wanneer u een vertaalworkflow uitvoert op een afgeleid element, haalt AEM Assets automatisch alle elementen op waarnaar het bronbestand verwijst en die het bevat voor vertaling. Op deze manier wordt het element waarnaar door het bronelement wordt verwezen, samen met de bron en afgeleide elementen omgezet. Neem bijvoorbeeld een scenario waarin uw Engelse taalkopie een afgeleid element en het bronbestand van dat element bevat, zoals wordt weergegeven.

Als het bronbestand is gerelateerd aan een ander element, haalt AEM Assets het element waarnaar wordt verwezen op en neemt het dit voor vertaling op.

1. Vertaal de elementen in de bronmap naar een doeltaal door de stappen in [Een nieuw vertaalproject](/help/assets/translate-assets.md#create-a-new-translation-project)maken uit te voeren. In dit geval vertaalt u uw middelen bijvoorbeeld naar het Frans.
1. Open vanuit de pagina Projecten de vertaalmap.
1. Klik/Tik de projecttegel om de detailspagina te openen.
1. Klik op of tik op de ovalen onder de Vertaaltaak-kaart om de status van de vertaling weer te geven.
1. Selecteer het element en klik/tik op **[!UICONTROL Tonen in elementen]** op de werkbalk om de vertaalstatus voor het element weer te geven.
1. Klik op het bronelement of tik erop om te controleren of de aan de bron gerelateerde elementen zijn omgezet.
1. Selecteer het element dat betrekking heeft op de bron en klik op **[!UICONTROL Tonen in elementen]**. Het vertaalde gerelateerde element wordt weergegeven.
