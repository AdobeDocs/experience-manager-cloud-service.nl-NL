---
title: Hoe gebruik ik de metagegevenseigenschappen van een adaptief formulier opnieuw?
description: Ontdek om een bestaand adaptief formulier efficiënt te hergebruiken om een nieuw formulier te maken.
seo-description: You can reuse an existing Adaptive Form to create new Adaptive Forms.
feature: Adaptive Forms, Foundation Components
exl-id: fb8cf3a9-fd19-46bf-b40e-2af76ca68b9f
role: User, Developer
source-git-commit: b5340c23f0a2496f0528530bdd072871f0d70d62
workflow-type: tm+mt
source-wordcount: '601'
ht-degree: 0%

---

# Eigenschappen van metagegevens van een adaptief formulier opnieuw gebruiken {#reusing-adaptive-forms}

>[!NOTE]
>
> De Adobe adviseert het gebruiken van de moderne en verlengbare gegevens vangt [&#x200B; Componenten van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=nl-NL) voor [&#x200B; het creëren van nieuwe Aangepaste Forms &#x200B;](/help/forms/creating-adaptive-form-core-components.md) of [&#x200B; het toevoegen van Aangepaste Forms aan de pagina&#39;s van AEM Sites &#x200B;](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten.


| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [&#x200B; klik hier &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/reusing-adaptive-forms.html?lang=nl-NL) |
| AEM as a Cloud Service | Dit artikel |

Als u bepaalde eigenschappen van een bestaand adaptief formulier wilt gebruiken om een nieuw formulier te genereren, kunt u gewoon de functie Kopiëren en plakken gebruiken. Daarnaast kunt u het nieuwe adaptieve formulier plakken in het gewenste mappad. Alle metagegevenseigenschappen worden gerepliceerd en de XFA- en XSD-waarden voor op XFA en XSD gebaseerde adaptieve Forms worden ook gekopieerd.

>[!NOTE]
>
>De status en de revisiedetails worden niet gekopieerd. Als uw adaptief formulier bijvoorbeeld wordt gepubliceerd en u het kopieert, is het geplakte adaptieve formulier in ongepubliceerde staat. Op dezelfde manier geldt dat als een gekopieerd actief wordt gecontroleerd, het geplakte actief niet onder dezelfde revisie valt.

## Een adaptief formulier kopiëren {#copy-an-adaptive-form}

Kopieer een adaptief formulier op een van de volgende manieren:

1. Klik exemplaar ![&#x200B; aem6forms_copy &#x200B;](assets/aem6forms_copy.png) pictogram van Snelle acties.

   >[!NOTE]
   >
   >Snelle acties zijn de actiepunten die over een duimnagel worden getoond wanneer de muiswijzer.

1. Selecteer het adaptieve formulier. Het selectieproces is anders voor verschillende weergaven.

   Als u in kaartmening bent, ga naar selectiemodus door het selectie ![&#x200B; te klikken aem6forms_check-circle &#x200B;](assets/aem6forms_check-circle.png) pictogram en klik al Aangepast Forms dat u wilt kopiëren.

   Als u in de lijstweergave bent, klikt u op de selectievakjes van alle Adaptive Forms om deze te selecteren.

   >[!NOTE]
   >
   >Alle geselecteerde elementen moeten Adaptief Forms zijn, omdat de functie Kopiëren en plakken alleen wordt ondersteund voor Adaptief Forms. Alle geselecteerde elementen moeten in dezelfde map aanwezig zijn.

   Na het selecteren van de activa, klik het exemplaar ![&#x200B; aem6forms_copy &#x200B;](assets/aem6forms_copy.png) pictogram aanwezig in de toolbar om de geselecteerde Aangepaste Vorm te kopiëren.

## Een adaptief formulier plakken {#paste-an-adaptive-form}

Het klikken van de exemplaaractie verlaat automatisch de selectiewijze en maakt het deeg ![&#128279;](assets/Smock_Paste_18_N.svg) pictogram van het Deeg  &lbrace;zichtbaar. Ga nu naar de gewenste omslagweg en klik het deeg ![&#x200B; &#x200B;](assets/Smock_Paste_18_N.svg) pictogram van het Deeg &lbrace;om de gekopieerde Aangepaste Vorm te kleven.

Als u plakt in dezelfde map of een ander bestand met dezelfde knooppuntnaam (waarmee het bestand is opgeslagen in de CRX-opslagplaats) bestaat in deze doelmap, wordt 1 toegevoegd aan het achtervoegsel (myaf wordt bijvoorbeeld myaf1 en als myaf1 op dezelfde locatie bestaat, wordt myaf myaf2. Alle andere eigenschappen blijven hetzelfde als het oorspronkelijke adaptieve formulier.

Na het klikken van het deeg ![&#x200B; &#x200B;](assets/Smock_Paste_18_N.svg) pictogram van het Deeg, zal het opnieuw verborgen worden. U kunt tegelijkertijd slechts één keer plakken. Als u opnieuw een kopie van hetzelfde element wilt maken, kopieert u het opnieuw.

## Inhoud van nieuw adaptief formulier wijzigen {#change-contents-of-new-adaptive-form}

De inhoud van een geplakte adaptieve Forms kan op de volgende manieren worden gewijzigd, zodat deze verschilt van het gekopieerde formulier:

1. **de meta-gegevenseigenschappen van de Verandering:**

   U kunt de eigenschappen van de metagegevens van het adaptieve formulier wijzigen, bijvoorbeeld de titel en de beschrijving. Voor meer details over meta-gegevenseigenschappen en hoe zij kunnen worden veranderd, zie [&#x200B; het Leiden Metagegevens van de Vorm &#x200B;](manage-form-metadata.md)

1. **Verandering XFA/XSD voor op XFA/XSD-Gebaseerde Aangepaste Forms:**

   U kunt de XFA/XSD wijzigen die wordt gebruikt in Adaptive Forms. Om te weten hoe deze Aanpassings Forms kan worden veranderd, zie [&#x200B; het Leiden vormmeta-gegevens &#x200B;](manage-form-metadata.md)

1. **opnieuw publiceren:**

   Het geplakte element verschilt van het gekopieerde element. U kunt de presentatie publiceren als een nieuw element, zodat deze beschikbaar is voor eindgebruikers. Als u wilt weten hoe u een element publiceert, <!-- see [Publishing and unpublishing forms](publishing-unpublishing-forms.md) -->


## Zie ook {#see-also}

{{see-also}}