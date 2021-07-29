---
title: Hoe te om onderzoeksfilters voor Inbox te vormen?
description: Leer hoe u zoekfilters voor Inbox-items configureert.
source-git-commit: ee32ab3659ee4696caa55b945b6b7895d94914a9
workflow-type: tm+mt
source-wordcount: '916'
ht-degree: 0%

---

# Zoekfilters voor Postvak IN configureren {#configure-search-filters-inbox}

U kunt zoekfilters configureren voor Postvak IN-items. Baseer uw onderzoekscriteria op een specifieke kolom Inbox om de resultaten te filtreren.

Als u bijvoorbeeld de items in het Postvak IN wilt filteren op basis van een kolombereik Datum van Postvak in, kunt u de voorspelling Datumbereik gebruiken om het datumbereik te definiëren.

Hieronder vindt u de beschikbare prediktypen voor Inbox:

* Bereik voorspellen

* Tekstvoorspelling

* Datumbereik

* Eigenschappenvoorspelling opties

>[!NOTE]
>
>Zorg ervoor dat u lid van de `workflow-administrators` groep bent om onderzoeksfilters voor Inbox te vormen.

## Een aangepaste configuratie maken of openen {#creating-opening-customized-configuration}

1. Ga naar **[!UICONTROL Tools]**, **[!UICONTROL General]**, **[!UICONTROL Search Forms]**.

1. Selecteer de **[!UICONTROL Inbox Search Rail]** configuratie en tik **[!UICONTROL Edit]**.
1. Neem de wijzigingen in de configuratie met voorspelling op met **[!UICONTROL Edit Search Forms]**.
1. Selecteer **[!UICONTROL Done]** om de configuratie op te slaan.

## Een aangepaste configuratie verwijderen {#delete-customized-configuration}

Een aangepaste configuratie verwijderen:

1. Ga naar **[!UICONTROL Tools]**, **[!UICONTROL General]**, **[!UICONTROL Search Forms]**.

1. Selecteer de **[!UICONTROL Inbox Search Rail]** configuratie en tik **[!UICONTROL Delete]**.

## Bereik vooraf instellen configureren {#range-predicate}

U kunt de punten van Inbox aan onderzoek naar een aantalwaaier binnen een kolom Inbox filtreren gebruikend de Voorkeur van de Waaier. U kunt er ook voor kiezen decimale waarden op te nemen voor getallen.

Om een Predicate van de Waaier te vormen:

1. Open het [formulier voor configuratie](#creating-opening-customized-configuration).
1. Tik op de tab **[!UICONTROL Select Predicate]** en sleep **[!UICONTROL Range Predicate]** naar het formulier.
1. Selecteer op het tabblad **[!UICONTROL Settings]** de kolomnaam Inbox waarop u de zoekopdracht wilt baseren, in het veld **[!UICONTROL Column Name]**.
1. Geef het label voor het filter op in het veld **[!UICONTROL Filter Label]**. Schakel het selectievakje **[!UICONTROL Enable Decimal Values]** in om decimale waarden voor getallen te accepteren bij het definiëren van het bereik.
1. Geef een optionele beschrijving op voor de configuratie en tik **[!UICONTROL Done]** om deze op te slaan.

De configuratiewijzigingen worden weerspiegeld wanneer u de pagina Filters opent. Het filterlabel dat u in stap 4 hebt opgegeven, wordt weergegeven als het label met een optie voor het definiëren van de maximum- en minimumwaarden. Wanneer u op Enter drukt, past [!DNL Experience Manager] de zoekcriteria toe op de kolomnaam die in stap 3 is opgegeven en retourneert deze de items in het Postvak IN.

>[!NOTE]
>
>In het artikel worden de meest recente gebruikersinterfaceopties weergegeven. De optienamen worden in de volgende release bijgewerkt in de gebruikersinterface.

## Tekstvoorspelling configureren {#text-predicate}

Filter Inbox-items om te zoeken naar een tekstreeks in een kolom Inbox met behulp van de Tekstvoorspelling.

Een tekstvoorspelling configureren:

1. Open het [formulier voor configuratie](#creating-opening-customized-configuration).
1. Tik op de tab **[!UICONTROL Select Predicate]** en sleep **[!UICONTROL Text Predicate]** naar het formulier.
1. Selecteer op het tabblad **[!UICONTROL Settings]** de kolomnaam Inbox waarop u de zoekopdracht wilt baseren, in het veld **[!UICONTROL Column Name]**.
1. Geef de tekst op die in het tekstvak Zoeken wordt weergegeven als plaatsaanduidingstekst in het veld **[!UICONTROL Search Text Box Placeholder]**.
1. Geef een optionele beschrijving op voor de configuratie en tik **[!UICONTROL Done]** om deze op te slaan.

De configuratiewijzigingen worden weerspiegeld wanneer u de pagina Filters opent. Wanneer u op Enter drukt, past [!DNL Experience Manager] de zoektekst toe die in stap 4 is opgegeven op de kolomnaam die in stap 3 is opgegeven en worden de items in het Postvak IN geretourneerd.

## Datumbereikvoorspelling configureren {#date-range-predicate}

Met de Datumbereikvoorspelling kunt u items in het Postvak IN filteren om te zoeken naar een datumbereik in een kolom in het Postvak In.

Een datumbereikvoorspelling configureren:

1. Open het [formulier voor configuratie](#creating-opening-customized-configuration).
1. Tik op de tab **[!UICONTROL Select Predicate]** en sleep **[!UICONTROL Date Range Predicate]** naar het formulier.
1. Selecteer op het tabblad **[!UICONTROL Settings]** de kolomnaam Inbox waarop u de zoekopdracht wilt baseren, in het veld **[!UICONTROL Column Name]**.
1. Geef het label voor het datumbereikfilter op in het veld **[!UICONTROL Filter Label]**.
1. Geef de begindatum en einddatumlabels voor het filter op.
1. Geef een optionele beschrijving op voor de configuratie en tik **[!UICONTROL Done]** om deze op te slaan.

De configuratiewijzigingen worden weerspiegeld wanneer u de pagina Filters opent. Het filterlabel dat u in stap 4 hebt opgegeven, wordt weergegeven als het label voor het datumbereikfilter, samen met de labels voor de begin- en einddatum die in stap 5 zijn opgegeven. [!DNL Experience Manager] past de zoekcriteria toe op de kolomnaam die in stap 3 is opgegeven en retourneert de items in het Postvak IN.

## Voorkeur voor aangepaste kolomopties configureren {#custom-column-options-predicate}

Met het voorvoegsel Aangepaste kolomopties kunt u de items in het Postvak IN filteren op een aangepaste optie in een kolom Inbox.

Een voorspelling voor aangepaste kolomopties configureren:

1. Open het [formulier voor configuratie](#creating-opening-customized-configuration).
1. Tik op de tab **[!UICONTROL Select Predicate]** en sleep **[!UICONTROL Custom Column Options Predicate]** naar het formulier.
1. Selecteer op het tabblad **[!UICONTROL Settings]** de kolomnaam Inbox waarop u de zoekopdracht wilt baseren, in het veld **[!UICONTROL Column Name]**.
1. Geef het label voor het filter met aangepaste kolomopties op in het veld **[!UICONTROL Filter Label]**.
1. Schakel het selectievakje **[!UICONTROL Single Select]** in om slechts één optie te selecteren terwijl u een filter toepast op een kolom Inbox.
1. In de sectie **[!UICONTROL Add Options]**:
   1. Selecteer **[!UICONTROL Manual]** om de opties van het filteronderzoek manueel te bepalen. Tik **[!UICONTROL Add Filter Options]** om de eerste optie te definiëren. Geef het label voor de kolomoptie op en geef de waarde van de optie op waarnaar u wilt zoeken. Als u bijvoorbeeld **Vrouwelijk** als waarde in een kolom Inbox wilt zoeken, kunt u **F** als label voor de kolomoptie opgeven en **Vrouwelijk** als tekst voor de optiewaarde toevoegen. Op dezelfde manier kunt u meer filteropties toevoegen.
   1. Selecteer **[!UICONTROL JSON Path]** om opties te definiëren met behulp van een JSON-bestandspad. Hier volgt een voorbeeld van een JSON-bestand waarin filteropties worden gedefinieerd:

      ```JSON
          {
         "options":[
            {
            "text":"Female",
            "value":"F"
            },
            {
            "text":"Male",
            "value":"M"
            }
          ]
        }
      ```

   1. Selecteer **[!UICONTROL CRX Options Path]** om opties te definiëren met behulp van de CRX-opslagpaden. Tik **[!UICONTROL Add Option Paths]** om meerdere paden toe te voegen. Hier volgt een voorbeeld voor het definiëren van `Male`- en `Female`-filteropties:

      ```JSON
         <gender jcr:primaryType="sling:OrderedFolder">
                        <male
                            jcr:primaryType="nt:unstructured"
                            jcr:title="Male"
                            value="M"/>
                        <female
                            jcr:primaryType="nt:unstructured"
                            jcr:title="Female"
                            value="F"/>
                    </gender>
      ```

1. Geef een optionele beschrijving op voor de configuratie en tik **[!UICONTROL Done]** om deze op te slaan.

De configuratiewijzigingen worden weerspiegeld wanneer u de pagina Filters opent. Het filterlabel dat u in stap 4 hebt opgegeven, wordt weergegeven als het label voor het voorvoegsel van de optie Aangepaste kolom. [!DNL Experience Manager] past de zoekcriteria die in stap 6 zijn gedefinieerd, toe op de kolomnaam die in stap 3 is opgegeven en retourneert de items in het Postvak IN.

In de volgende video worden de stappen geïllustreerd voor het filteren van een kolom op basis van de optiewaarden `true` en `false`.

>[!VIDEO](https://video.tv.adobe.com/v/335679)

## Zoekfilters weergeven op basis van voorspelling {#view-search-filters-for-predicates}

U kunt zoekfilters weergeven op basis van voorspelling. Selecteer **[!UICONTROL Filter]** op de Inbox pagina. De filters worden weergegeven in het linkervenster. Vervolgens kunt u de zoekcriteria opgeven om de items in het Postvak IN te filteren.

![Pagina Filters](assets/apply-filters.png)

Voor meer informatie bij het beheren van predikeconfiguraties, zie [Vormend Onderzoek Forms](search-forms.md).


