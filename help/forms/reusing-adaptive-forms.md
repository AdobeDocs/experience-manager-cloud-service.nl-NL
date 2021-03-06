---
title: Eigenschappen van metagegevens van een adaptief formulier opnieuw gebruiken
seo-title: Reuse metadata properties of an Adaptive Form
description: U kunt een bestaand adaptief formulier opnieuw gebruiken om een nieuwe Adaptieve Forms te maken.
seo-description: You can reuse an existing Adaptive Form to create new Adaptive Forms.
exl-id: fb8cf3a9-fd19-46bf-b40e-2af76ca68b9f
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---

# Eigenschappen van metagegevens van een adaptief formulier opnieuw gebruiken {#reusing-adaptive-forms}

Als u bepaalde eigenschappen van een bestaand adaptief formulier wilt gebruiken om een nieuw formulier te genereren, kunt u gewoon de functie Kopiëren en plakken gebruiken. Daarnaast kunt u het nieuwe adaptieve formulier plakken in het gewenste mappad. Alle metagegevenseigenschappen worden gerepliceerd en de XFA- en XSD-waarden voor op XFA en XSD gebaseerde adaptieve Forms worden ook gekopieerd.

>[!NOTE]
>
>De status en de revisiedetails worden niet gekopieerd. Als uw adaptief formulier bijvoorbeeld wordt gepubliceerd en u het kopieert, is het geplakte adaptieve formulier in ongepubliceerde staat. Op dezelfde manier geldt dat als een gekopieerd actief wordt gecontroleerd, het geplakte actief niet onder dezelfde revisie valt.

## Een adaptief formulier kopiëren {#copy-an-adaptive-form}

Kopieer een adaptief formulier op een van de volgende manieren:

1. Klikken op kopiëren ![aem6forms_copy](assets/aem6forms_copy.png) pictogram van Snelle acties.

   >[!NOTE]
   >
   >Snelle acties zijn de actiepunten die over een duimnagel worden getoond wanneer de muiswijzer.

1. Selecteer het adaptieve formulier. Het selectieproces is anders voor verschillende weergaven.

   Ga in de kaartweergave naar de selectiemodus door op de selectie te klikken ![aem6forms_check-circle](assets/aem6forms_check-circle.png) en klik op alle Adaptief Forms die u wilt kopiëren.

   Als u in de lijstweergave bent, klikt u op de selectievakjes van alle Adaptive Forms om deze te selecteren.

   >[!NOTE]
   >
   >Alle geselecteerde elementen moeten Adaptief Forms zijn, omdat de functie Kopiëren en plakken alleen wordt ondersteund voor Adaptief Forms. Alle geselecteerde elementen moeten in dezelfde map aanwezig zijn.

   Nadat u de elementen hebt geselecteerd, klikt u op de kopie ![aem6forms_copy](assets/aem6forms_copy.png) op de werkbalk om het geselecteerde adaptieve formulier te kopiëren.

## Een adaptief formulier plakken {#paste-an-adaptive-form}

Wanneer u op de kopieeractie klikt, wordt de selectiemodus automatisch verlaten en wordt de plakbewerking ![Plakken](assets/Smock_Paste_18_N.svg) zichtbaar. Ga nu naar het gewenste mappad en klik op Plakken ![Plakken](assets/Smock_Paste_18_N.svg) pictogram om het gekopieerde adaptieve formulier te plakken.

Als u plakt in dezelfde map of een ander bestand met dezelfde knooppuntnaam (waarmee het bestand is opgeslagen in de CRX-opslagruimte) bestaat in deze doelmap, wordt 1 toegevoegd aan het achtervoegsel (myaf wordt bijvoorbeeld myaf1 en als myaf1 op dezelfde locatie bestaat, wordt myaf myaf2. Alle andere eigenschappen blijven hetzelfde als het oorspronkelijke adaptieve formulier.

Nadat u op de plakbewerking hebt geklikt ![Plakken](assets/Smock_Paste_18_N.svg) pictogram, wordt het opnieuw verborgen. In één keer kunt u slechts één keer plakken. Als u opnieuw een kopie van hetzelfde element wilt maken, kopieert u het opnieuw.

## Inhoud van nieuw adaptief formulier wijzigen {#change-contents-of-new-adaptive-form}

De inhoud van een geplakte adaptieve Forms kan op de volgende manieren worden gewijzigd, zodat deze verschilt van het gekopieerde formulier:

1. **Eigenschappen van metagegevens wijzigen:**

   U kunt de eigenschappen van de metagegevens van het adaptieve formulier wijzigen, bijvoorbeeld de titel en de beschrijving. Zie voor meer informatie over eigenschappen van metagegevens en hoe deze kunnen worden gewijzigd [Formuliermetagegevens beheren](manage-form-metadata.md)

1. **XFA/XSD wijzigen voor adaptieve Forms op basis van XFA/XSD:**

   U kunt de XFA/XSD wijzigen die wordt gebruikt in Adaptive Forms. Als u wilt weten hoe deze Adaptive Forms kan worden gewijzigd, gaat u naar [Metagegevens van formulieren beheren](manage-form-metadata.md)

1. **Opnieuw publiceren:**

   Het geplakte element verschilt van het gekopieerde element. U kunt de presentatie publiceren als een nieuw element, zodat deze beschikbaar is voor eindgebruikers. Om te weten hoe te om activa te publiceren, <!-- see [Publishing and unpublishing forms](publishing-unpublishing-forms.md) -->
