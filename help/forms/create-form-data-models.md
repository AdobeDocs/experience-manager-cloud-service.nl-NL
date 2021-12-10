---
title: Hoe maakt u een formuliergegevensmodel?
description: Experience Manager Forms-gegevensintegratie biedt een intuïtieve gebruikersinterface voor het maken van en werken met formuliergegevensmodellen. Leer hoe te om modellen van vormgegevens met of zonder gevormde gegevensbronnen tot stand te brengen.
feature: Form Data Model
role: User, Developer
level: Beginner, Intermediate
exl-id: b17b7441-912c-44c7-a835-809f014a8c86
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '898'
ht-degree: 0%

---

# Formuliergegevensmodel maken {#create-form-data-model}

![Gegevensintegratie](do-not-localize/data-integeration.png)

[!DNL Experience Manager Forms] gegevensintegratie biedt een intuïtieve gebruikersinterface voor het maken van en werken met formuliergegevensmodellen. Een formuliergegevensmodel is gebaseerd op gegevensbronnen voor gegevensuitwisseling; u kunt echter wel een formuliergegevensmodel maken met of zonder gegevensbron. Er zijn twee benaderingen om van gegevensmodel afhankelijk van tot stand te brengen of u gegevensbronnen hebt gevormd:

* **Vooraf geconfigureerde gegevensbronnen gebruiken**: Als u gegevensbronnen hebt geconfigureerd zoals beschreven in [Gegevensbronnen configureren](configure-data-sources.md)kunt u deze selecteren tijdens het maken van een formuliergegevensmodel. Hiermee worden alle gegevensmodelobjecten, eigenschappen en services van de geselecteerde gegevensbronnen beschikbaar gemaakt voor gebruik in het formuliergegevensmodel.

* **Zonder gegevensbronnen**: Als u geen gegevensbronnen hebt geconfigureerd voor uw formuliergegevensmodel, kunt u het nog steeds maken zonder gegevensbronnen. U kunt het formuliergegevensmodel gebruiken om Adaptive Forms te ontwerpen <!--and interactive communication--> en test ze met behulp van voorbeeldgegevens. Als er gegevensbronnen beschikbaar zijn, kunt u het formuliergegevensmodel binden met gegevensbronnen. Dit wordt automatisch weerspiegeld in de gekoppelde adaptieve Forms<!--and interactive communications-->.

>[!NOTE]
>
>U moet lid zijn van beide **fdm-auteur** en **formuliergebruiker** groepen die u wilt maken en werken met het formuliergegevensmodel. Neem contact op met uw [!DNL Experience Manager] beheerder om lid te worden van de groepen.

## Formuliergegevensmodel maken {#data-sources}

Zorg ervoor dat u de gegevensbronnen hebt geconfigureerd die u wilt gebruiken in het formuliergegevensmodel, zoals beschreven in [Gegevensbronnen configureren](configure-data-sources.md). Ga als volgt te werk om een formuliergegevensmodel te maken op basis van geconfigureerde gegevensbronnen:

1. In [!DNL Experience Manager] auteurinstantie, navigeren aan **[!UICONTROL Forms > Data Integrations]**.
1. Tik op **[!UICONTROL Create > Form Data Model]**.
1. In het dialoogvenster Formuliergegevensmodel maken:

   * Geef een naam op voor het gegevensmodel van het formulier.
   * (**Optioneel**) Geef een titel, beschrijving en codes op voor het formuliergegevensmodel.
   * (**Optioneel en alleen van toepassing als gegevensbronnen zijn geconfigureerd**) Tik op het pictogram naast het pictogram **[!UICONTROL Data Source Configuration]** en selecteer het configuratieknooppunt waar de wolkendiensten voor de gegevensbronnen u wilt gebruiken verblijven. Het beperkt de lijst van gegevensbronnen beschikbaar voor selectie op de volgende pagina tot degenen beschikbaar in de geselecteerde configuratieknooppunt. Nochtans, om het even welke gegevensbestand JDBC en [!DNL Experience Manager] gegevensbronnen van gebruikersprofielen worden standaard weergegeven. Als u geen configuratieknooppunt selecteert, worden de gegevensbronnen van alle configuratieknooppunten vermeld.

1. Tik op **[!UICONTROL Next]**.

1. (**Alleen van toepassing als gegevensbronnen zijn geconfigureerd**) **[!UICONTROL Select Datasource]** het scherm maakt een lijst van beschikbare gegevensbronnen, als om het even welk. Selecteer gegevensbronnen die u wilt gebruiken in het formuliergegevensmodel.
1. Tikken **[!UICONTROL Create]** en tikt u in het bevestigingsvenster op **[!UICONTROL Open]** om de formuliergegevensmodeleditor te openen.

   Laten we de verschillende componenten van de gebruikersinterface van de formuliergegevensmodel bekijken.

   ![Een model van de Gegevens van de Vorm met drie gegevensbronnen - de dienst RESTful; [!DNL Experience Manager] gebruikersprofiel en een RDBMS](assets/fdm-ui.png)

   A. **[!UICONTROL Data Sources]** Hier worden gegevensbronnen in een formuliergegevensmodel weergegeven. Breid een gegevensbron uit om zijn voorwerpen en de diensten van het gegevensmodel te bekijken.

   B. **[!UICONTROL Refresh Data Source Definitions]** Krijgt om het even welke veranderingen in gegevensbrondefinities van gevormde gegevensbronnen en werkt hen op het Bronlusje van Gegevens van de Modelredacteur van de Gegevens van de Vorm bij.

   C. **[!UICONTROL Model]** Inhoudsgebied waar objecten van een toegevoegd gegevensmodel worden weergegeven.

   D. **[!UICONTROL Services]** Inhoudsgebied waar bewerkingen of services met toegevoegde gegevensbron worden weergegeven.

   E. **[!UICONTROL Toolbar]** Gereedschappen voor het werken met het formuliergegevensmodel. Op de werkbalk ziet u meer opties, afhankelijk van het geselecteerde object in het formuliergegevensmodel.

   F. **[!UICONTROL Add Selected]** Hiermee voegt u geselecteerde gegevensmodelobjecten en -services toe aan het formuliergegevensmodel.

Voor meer informatie over de redacteur van het Model van de Gegevens van de Vorm en hoe u met het kunt werken om het model van vormgegevens uit te geven en te vormen, zie [Werken met formuliergegevensmodel](work-with-form-data-model.md).

## Gegevensbronnen bijwerken {#update}

Ga als volgt te werk om gegevensbronnen toe te voegen aan of bij te werken naar een bestaand formuliergegevensmodel.

1. Ga naar **[!UICONTROL Forms > Data Integrations]** selecteert u het formuliergegevensmodel waaraan u gegevensbronnen wilt toevoegen of bijwerken en tikt u op **[!UICONTROL Properties]**.
1. Ga in de eigenschappen van het formuliergegevensmodel naar **[!UICONTROL Update Source]** tab.

   In de **[!UICONTROL Update Source]** tab:

   * Tik op het bladerpictogram in het dialoogvenster **[!UICONTROL Context-Aware Configuration]** en selecteer een configuratienode waar de wolkenconfiguratie voor de gegevensbron u wilt toevoegen verblijft. Als u geen knooppunt selecteert, blijven cloudconfiguraties alleen in de `global` de knoop wordt vermeld wanneer u tikt **[!UICONTROL Add Sources]**.

   * Tik op **[!UICONTROL Add Sources]** en selecteert u de gegevensbronnen die u aan het formuliergegevensmodel wilt toevoegen. Alle gegevensbronnen geconfigureerd in `global` en het geselecteerde configuratieknooppunt, als om het even welk, wordt getoond.

   * Tik op de knop **[!UICONTROL Edit]** pictogram voor de gegevensbron en selecteer uit de lijst van beschikbare gegevensbronnen.
   * Tik op de knop **[!UICONTROL Delete]** pictogram voor de gegevensbron. Het pictogram Verwijderen is uitgeschakeld als een gegevensmodelobject in de gegevensbron wordt toegevoegd aan het formuliergegevensmodel.

      ![fdm-eigenschappen](assets/fdm-properties.png)

1. Tikken **[!UICONTROL Save & Close]** om de updates op te slaan.

>[!NOTE]
>
>Nadat u nieuwe gegevensbronnen hebt toegevoegd of bestaande gegevensbronnen hebt bijgewerkt in een formuliergegevensmodel, moet u de bindingsverwijzingen naar behoren bijwerken in Adaptive Forms<!--and interactive communications--> die gebruikmaken van het bijgewerkte formuliergegevensmodel.

## Volgende stappen {#next-steps}

U hebt nu een formuliergegevensmodel waaraan gegevensbronnen zijn toegevoegd. Vervolgens kunt u het formuliergegevensmodel bewerken om gegevensmodelobjecten en -services toe te voegen en te configureren, koppelingen tussen gegevensmodelobjecten toe te voegen, eigenschappen te bewerken, aangepaste gegevensmodelobjecten en -eigenschappen toe te voegen, voorbeeldgegevens te genereren, enzovoort.

Zie voor meer informatie [Werken met formuliergegevensmodel](work-with-form-data-model.md).
