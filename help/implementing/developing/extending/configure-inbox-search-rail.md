---
title: Hoe te om onderzoeksfilters voor Inbox te vormen?
description: Leer hoe u zoekfilters voor Inbox-items configureert.
exl-id: 0e82d7ad-7a82-4d67-8eb8-9af6936652d8
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '925'
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
>Zorg ervoor dat u lid bent van de `workflow-administrators` groep om zoekfilters voor Inbox te configureren.

## Een aangepaste configuratie maken of openen {#creating-opening-customized-configuration}

1. Navigeren naar **[!UICONTROL Tools]**, **[!UICONTROL General]**, **[!UICONTROL Search Forms]**.

1. Selecteer de **[!UICONTROL Inbox Search Rail]** configuratie en selecteer **[!UICONTROL Edit]**.
1. Neem de wijzigingen in de predikconfiguratie op met **[!UICONTROL Edit Search Forms]**.
1. Selecteren **[!UICONTROL Done]** om de configuratie op te slaan.

## Een aangepaste configuratie verwijderen {#delete-customized-configuration}

Een aangepaste configuratie verwijderen:

1. Navigeren naar **[!UICONTROL Tools]**, **[!UICONTROL General]**, **[!UICONTROL Search Forms]**.

1. Selecteer de **[!UICONTROL Inbox Search Rail]** configuratie en selecteer **[!UICONTROL Delete]**.

## Bereik vooraf instellen configureren {#range-predicate}

U kunt de punten van Inbox aan onderzoek naar een aantalwaaier binnen een kolom Inbox filtreren gebruikend de Voorkeur van de Waaier. U kunt er ook voor kiezen decimale waarden op te nemen voor getallen.

Om een Predicate van de Waaier te vormen:

1. Open de [formulier voor configuratie](#creating-opening-customized-configuration).
1. Selecteer de **[!UICONTROL Select Predicate]** en slepen **[!UICONTROL Range Predicate]** op het formulier.
1. In de **[!UICONTROL Settings]** selecteert u de kolomnaam Inbox waarop u de zoekopdracht wilt baseren, van **[!UICONTROL Column Name]** veld.
1. Geef het label voor het filter op in het dialoogvenster **[!UICONTROL Filter Label]** veld. Selecteer de **[!UICONTROL Enable Decimal Values]** Schakel het selectievakje in om decimale waarden voor getallen te accepteren tijdens het definiëren van het bereik.
1. Geef een optionele beschrijving voor de configuratie op en selecteer **[!UICONTROL Done]** opslaan.

De configuratiewijzigingen worden weerspiegeld wanneer u de pagina Filters opent. Het filterlabel dat u in stap 4 hebt opgegeven, wordt weergegeven als het label met een optie voor het definiëren van de maximum- en minimumwaarden. Wanneer u op Enter drukt, [!DNL Experience Manager] past de zoekcriteria toe op de kolomnaam die in stap 3 is opgegeven en retourneert de items in het Postvak IN.

>[!NOTE]
>
>In het artikel worden de meest recente gebruikersinterfaceopties weergegeven. De optienamen worden bijgewerkt in de gebruikersinterface van de volgende release.

## Tekstvoorspelling configureren {#text-predicate}

Filter Inbox-items om te zoeken naar een tekstreeks in een kolom Inbox met behulp van de Tekstvoorspelling.

Een tekstvoorspelling configureren:

1. Open de [formulier voor configuratie](#creating-opening-customized-configuration).
1. Selecteer de **[!UICONTROL Select Predicate]** en slepen **[!UICONTROL Text Predicate]** op het formulier.
1. In de **[!UICONTROL Settings]** selecteert u de kolomnaam Inbox waarop u de zoekopdracht wilt baseren, van **[!UICONTROL Column Name]** veld.
1. Geef de tekst op die in het tekstvak Zoeken wordt weergegeven als plaatsaanduidingstekst in het dialoogvenster **[!UICONTROL Search Text Box Placeholder]** veld.
1. Geef een optionele beschrijving voor de configuratie op en selecteer **[!UICONTROL Done]** opslaan.

De configuratiewijzigingen worden weerspiegeld wanneer u de pagina Filters opent. Wanneer u op Enter drukt, [!DNL Experience Manager] past de zoektekst die in stap 4 is opgegeven, toe op de kolomnaam die in stap 3 is opgegeven en retourneert de items in het Postvak IN.

## Datumbereikvoorspelling configureren {#date-range-predicate}

Met de Datumbereikvoorspelling kunt u items in het Postvak IN filteren om te zoeken naar een datumbereik in een kolom in het Postvak In.

Een datumbereikvoorspelling configureren:

1. Open de [formulier voor configuratie](#creating-opening-customized-configuration).
1. Selecteer de **[!UICONTROL Select Predicate]** en slepen **[!UICONTROL Date Range Predicate]** op het formulier.
1. In de **[!UICONTROL Settings]** selecteert u de kolomnaam Inbox waarop u de zoekopdracht wilt baseren, van **[!UICONTROL Column Name]** veld.
1. Geef het label voor het datumbereikfilter op in het dialoogvenster **[!UICONTROL Filter Label]** veld.
1. Geef de begindatum en einddatumlabels voor het filter op.
1. Geef een optionele beschrijving voor de configuratie op en selecteer **[!UICONTROL Done]** opslaan.

De configuratiewijzigingen worden weerspiegeld wanneer u de pagina Filters opent. Het filterlabel dat u in stap 4 hebt opgegeven, wordt weergegeven als het label voor het datumbereikfilter, samen met de labels voor de begin- en einddatum die in stap 5 zijn opgegeven. [!DNL Experience Manager] past de zoekcriteria toe op de kolomnaam die in stap 3 is opgegeven en retourneert de items in het Postvak IN.

## Voorkeur voor aangepaste kolomopties configureren {#custom-column-options-predicate}

Met het voorvoegsel Aangepaste kolomopties kunt u de items in het Postvak IN filteren op een aangepaste optie in een kolom Inbox.

Een voorspelling voor aangepaste kolomopties configureren:

1. Open de [formulier voor configuratie](#creating-opening-customized-configuration).
1. Selecteer de **[!UICONTROL Select Predicate]** en slepen **[!UICONTROL Custom Column Options Predicate]** op het formulier.
1. In de **[!UICONTROL Settings]** selecteert u de kolomnaam Inbox waarop u de zoekopdracht wilt baseren, van **[!UICONTROL Column Name]** veld.
1. Geef het label voor het filter met aangepaste kolomopties op in het dialoogvenster **[!UICONTROL Filter Label]** veld.
1. Selecteer de **[!UICONTROL Single Select]** Schakel het selectievakje in om de selectie van slechts één optie in te schakelen terwijl u een filter toepast op een kolom Inbox.
1. In de **[!UICONTROL Add Options]** sectie:
   1. Selecteren **[!UICONTROL Manual]** om de opties voor filterzoekopdrachten handmatig te definiëren. Selecteren **[!UICONTROL Add Filter Options]** om de eerste optie te definiëren. Geef het label voor de kolomoptie en de tekst van de optiewaarde op die u wilt zoeken. Als u bijvoorbeeld naar **Vrouwelijk** als een waarde in een kolom Inbox, kunt u specificeren **F** als label voor de kolomoptie en toevoegen **Vrouwelijk** als de tekst van de optiewaarde. U kunt ook meer filteropties toevoegen.
   1. Selecteren **[!UICONTROL JSON Path]** om opties te definiëren via een JSON-bestandspad. Hier volgt een voorbeeld van een JSON-bestand waarin filteropties worden gedefinieerd:

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

   1. Selecteren **[!UICONTROL CRX Options Path]** opties definiëren met behulp van de CRX-opslagpaden. Selecteren **[!UICONTROL Add Option Paths]** meerdere paden toevoegen. Hier volgt een voorbeeld voor het definiëren van `Male` en `Female` filteropties:

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

1. Geef een optionele beschrijving voor de configuratie op en selecteer **[!UICONTROL Done]** opslaan.

De configuratiewijzigingen worden weerspiegeld wanneer u de pagina Filters opent. Het filterlabel dat u in stap 4 hebt opgegeven, wordt weergegeven als het label voor het voorvoegsel van de optie Aangepaste kolom. [!DNL Experience Manager] past de zoekcriteria die in stap 6 zijn gedefinieerd, toe op de kolomnaam die in stap 3 is opgegeven en retourneert de items in het Postvak IN.

In de volgende video worden de stappen geïllustreerd voor het filteren van een kolom op basis van de `true` en `false` optiewaarden.

>[!VIDEO](https://video.tv.adobe.com/v/335679)

## Zoekfilters weergeven op basis van voorspelling {#view-search-filters-for-predicates}

U kunt zoekfilters weergeven op basis van voorspelling. Selecteren **[!UICONTROL Filter]** op de pagina Inbox. De filters worden weergegeven in het linkervenster. Vervolgens kunt u de zoekcriteria opgeven om de items in het Postvak IN te filteren.

![Pagina Filters](assets/apply-filters.png)

Voor meer informatie bij het beheren van predikeconfiguraties, zie [Zoeken in Forms configureren](search-forms.md).
