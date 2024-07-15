---
title: Hoe kan ik metagegevens van een verzonden formulier bijwerken?
description: Leer hoe u met door de gebruiker verstrekte gegevens informatie aan metagegevens van een verzonden formulier kunt toevoegen. Dig dieper in op de manier waarop u de bijgewerkte metagegevens voor formulierverzending in de CRX-opslagplaats kunt bekijken.
feature: Adaptive Forms
role: User
level: Intermediate
source-git-commit: 2d4ffd5518d671a55e45a1ab6f1fc41ac021fd80
workflow-type: tm+mt
source-wordcount: '692'
ht-degree: 0%

---


# Informatie uit gebruikersgegevens toevoegen aan metagegevens voor het verzenden van formulieren {#adding-information-from-user-data-to-form-submission-metadata}

U kunt waarden die zijn ingevoerd in een element van het formulier gebruiken om metagegevensvelden van een concept of een formulier te berekenen. Met metagegevens kunt u inhoud filteren op basis van gebruikersgegevens. Een gebruiker voert bijvoorbeeld Jan Smit in het naamveld van het formulier. U kunt deze informatie gebruiken om metagegevens te berekenen die deze verzending kunnen categoriseren onder de JD voor initialen.

Als u metagegevensvelden wilt berekenen met door de gebruiker ingevoerde waarden, voegt u elementen van het formulier toe aan de metagegevens. Wanneer een gebruiker een waarde in dat element invoert, gebruikt een script de waarde om informatie te berekenen. Deze informatie wordt toegevoegd aan de metagegevens. Wanneer u een element als meta-gegevensgebied toevoegt, verstrekt u een sleutel voor het. De sleutel wordt toegevoegd als gebied in de meta-gegevens, en de gegevens verwerkte informatie wordt geregistreerd tegen het.

Een ziekteverzekeringsbedrijf publiceert bijvoorbeeld een formulier. In dit formulier legt een veld de pagina van de eindgebruikers vast. De klant wil alle verzendingen in een bepaald leeftijdsbereik controleren nadat meerdere gebruikers het formulier hebben verzonden. In plaats van alle gegevens te doorlopen die gecompliceerd worden door een toenemend aantal formulieren, helpen extra metagegevens de klant. De auteur van het formulier kan configureren welke eigenschappen/gegevens door de gebruiker worden ingevuld op het hoogste niveau, zodat de zoekopdracht het gemakkelijkst is. De extra meta-gegevens zijn door de gebruiker ingevulde informatie die op het hoogste niveau van de meta-gegevensknoop wordt opgeslagen, aangezien de auteur het vormde.

Een ander voorbeeld van een formulier waarin e-mailadres en telefoonnummer worden vastgelegd. Wanneer een gebruiker dit formulier anoniem bezoekt en het formulier verlaat, kan de auteur het formulier zodanig configureren dat de e-mailadres en het telefoonnummer automatisch worden opgeslagen. Dit formulier wordt automatisch opgeslagen en het telefoonnummer en de e-mailadres worden opgeslagen in het metagegevensknooppunt van het concept. Een gebruik-geval van deze configuratie is het lood management dashboard.

## Formulierelementen toevoegen aan metagegevens {#adding-form-elements-to-metadata}

Voer de volgende stappen uit om een element toe te voegen aan de metagegevens:

1. Open het adaptieve formulier in de bewerkingsmodus.\
   Als u het formulier wilt openen in de bewerkingsmodus, selecteert u in het formulierbeheer het formulier en selecteert u **[!UICONTROL Open]** .
1. Op geef wijze uit, selecteer een component, uitgezocht ![ gebied-niveau ](assets/select_parent_icon.svg) > **[!DNL Adaptive Form Container]**, en selecteer dan ![ cmp ](assets/configure-icon.svg).
1. Klik op **[!DNL Metadata]** in het zijpaneel.
1. Klik in de sectie Metagegevens op **[!DNL Add]** .
1. Voeg scripts toe in het veld Waarde van het tabblad Metagegevens. Met de scripts die u toevoegt, worden gegevens verzameld uit elementen op het formulier en worden waarden berekend die worden doorgegeven aan de metagegevens.

   **[!DNL true]** wordt bijvoorbeeld aangemeld als de ingevoerde leeftijd groter is dan 21 en **[!DNL false]** wordt geregistreerd als de ingevoerde leeftijd lager is dan 21. U voert het volgende script in op het tabblad Metagegevens:

   `(agebox.value >= 21) ? true : false`

   ![ manuscript van Meta-gegevens ](assets/add-element-metadata.png)

   Script ingevoerd op het tabblad Metagegevens

1. Klik op **[!DNL OK]**.

Nadat een gebruiker gegevens in het element invoert dat als meta-gegevensgebied wordt geselecteerd, wordt de gegevens gegevens gegevens geregistreerd in de meta-gegevens. U kunt de metagegevens bekijken in de opslagplaats die u hebt geconfigureerd voor het opslaan van metagegevens.

## Metagegevens voor bijgewerkte formulierverzending bekijken: {#seeing-updated-form-nbsp-submission-metadata}

In het bovenstaande voorbeeld worden de metagegevens opgeslagen in de CRX-opslagplaats. De metagegevens zien er als volgt uit:

![ Metagegevens ](assets/metadata_entry_new.png)

Als u een element van het controlevakje in de meta-gegevens toevoegt, worden de geselecteerde waarden opgeslagen als komma-gescheiden koord. U voegt bijvoorbeeld een component CheckBox toe aan het formulier en geeft de naam op als `checkbox1` . In de eigenschappen van de component van het controlevakje, voegt u de punten Rijvergunning, het Aantal van de Sociale Veiligheid, en Paspoort voor waarden 0, 1, en 2 toe.

![ Opstellend veelvoudige waarden van een controledoos ](assets/checkbox-metadata.png)

U selecteert de container Adaptief formulier en in de formuliereigenschappen voegt u een metagegevenssleutel `cb1` toe waarin `checkbox1.value` wordt opgeslagen, en publiceert u het formulier. Wanneer een klant het formulier invult, selecteert de klant de opties Paspoort en burgerservicenummer in het veld Selectievakje. De waarden 1 en 2 worden opgeslagen als 1, 2 in het cb1-veld van de metagegevens voor verzending.

![ de ingang van Meta-gegevens voor veelvoudige waarden die op een checkbox gebied ](assets/metadata-entry.png) worden geselecteerd

>[!NOTE]
>
>Het bovenstaande voorbeeld is alleen bedoeld voor leerdoeleinden. Zorg ervoor dat u naar metagegevens zoekt op de juiste locatie zoals deze is geconfigureerd in de [!DNL Experience Manager Forms] -implementatie.