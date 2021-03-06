---
title: Gebruik van CIF-product en rubriekkiezer
description: Leer hoe te om het product en de categoriekiezer van CIF in uw componenten van de klantenhandel te gebruiken om auteurs en verkopers te steunen om met handelsproduct en catalogusgegevens efficiënt te werken.
sub-product: Commerce
topics: Development
version: cloud-service
activity: develop
audience: developer
feature: Commerce Integration Framework
exl-id: 30f1f263-1b78-46ae-99ed-61861c488b2a
source-git-commit: 2e0a2b543fe0b6302a5dd62055f89a8f30427e6b
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 0%

---

# AEM Content &amp; Commerce Authoring Pickers {#cif-pickers}

AEM Content &amp; Commerce Authoring biedt een reeks ontwerpgereedschappen waarmee AEM auteurs en marketers efficiënt kunnen werken met handelsproductgegevens en -catalogi. De productkiezer en de categoriekiezer maken deel uit van de CIF-invoegtoepassing en worden gebruikt door de CIF Core-componenten. Projecten kunnen deze kiezers in elk dialoogvenster gebruiken om producten of categorieën te selecteren.

## Productkiezer {#product-picker}

Om de productkiezer in een projectcomponent te gebruiken moet een ontwikkelaar toevoegen `commerce/gui/components/common/cifproductfield` naar een componentdialoogvenster. Gebruik bijvoorbeeld het volgende voor de cq:dialog:

```xml
<product jcr:primaryType="nt:unstructured"
    sling:resourceType="commerce/gui/components/common/cifproductfield"
    fieldDescription="The product or product variant displayed by the teaser"
    fieldLabel="Select Product"
    filter="folderOrProductOrVariant"
    name="./selection"
    selectionId="sku"/>
```

In het productveld kan worden genavigeerd naar het product dat een gebruiker wil selecteren via de verschillende weergaven. Door gebrek keert het productgebied identiteitskaart van het product terug, maar het kan het vormen gebruikend `selectionId` kenmerk.

Het veld Productkiezer ondersteunt de volgende optionele eigenschappen:

- selectionId (id, uid, sku, slug, gecombineerdeSlug, CombinationSku) - maakt het mogelijk het productkenmerk te kiezen dat door de kiezer moet worden geretourneerd (standaard = id). Het gebruiken van sku keert de sku van het geselecteerde product terug, terwijl het gebruiken van compiledSku en keert een koord als base#variant met de skus van het basisproduct en de geselecteerde variant, of één enkele sku terug als een basisproduct wordt geselecteerd.
- filter (folderOrProduct, folderOrProductOrVariant) - filtert de inhoud die door de kiezer moet worden gerenderd tijdens het navigeren in de productstructuur. folderOrProduct - rendert mappen en producten. folderOrProductOrVariant - geeft omslagen, product en productvarianten terug. Als een product of productvariant wordt weergegeven, wordt deze ook selecteerbaar in de kiezer. (standaard = folderOrProduct)
- meerdere (true, false) - de selectie van een of meerdere producten inschakelen (standaard = false)
- emptyText - om de lege tekstwaarde van het plukkerveld te vormen

Ook standaardeigenschappen voor diagramvelden, zoals `name`, `fieldLabel`, of `fieldDescription` worden ook ondersteund.

>[!CAUTION]
>
>De `cifproductfield` component vereist de `cif.shell.picker` clientlib. Als u een clientlib aan een dialoogvenster wilt toevoegen, kunt u de eigenschap extraClientlibs gebruiken.
>[!CAUTION]
>
>Vanaf CIF Core Components versie 2.0.0 wordt de ondersteuning voor `id` is verwijderd en vervangen door `uid`. We raden u aan het gebruik van `sku` of `slug` als product-id. Wij blijven steun verlenen `id` alleen voor projecten die CIF Core Components versie 1.x gebruiken.

Een volledig werkend voorbeeld van het `cifproductfield` kunt u vinden in het dialoogvenster [CIF Core-componenten](https://github.com/adobe/aem-core-cif-components/blob/master/ui.apps/src/main/content/jcr_root/apps/core/cif/components/commerce/productteaser/v1/productteaser/_cq_dialog/.content.xml) project. Zie ook [Dialoogvensters aanpassen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/customizing.html?lang=en#customizing-dialogs) van de AEM Core Components documentatie.

## Categoriekiezer {#category-picker}

De categoriekiezer kan ook in een componentdialoogvenster worden gebruikt, net als de productkiezer.

Het volgende fragment kan in een cq:dialog-configuratie worden gebruikt:

```xml
<category jcr:primaryType="nt:unstructured" 
    sling:resourceType="commerce/gui/components/common/cifcategoryfield" 
    fieldLabel="Category" 
    name="./categoryId" 
    selectionId="uid" />
```

Het veld Categoriekiezer ondersteunt de volgende optionele eigenschappen:

- selectionId(id, uid, slug, urlPath, idAndUrlPath) _(afgekeurd)_, uidAndUrlPath _(afgekeurd)_) - hiermee kunt u het categoriekenmerk kiezen dat door de kiezer moet worden geretourneerd (standaard = id).
- meerdere (true, false) - de selectie van een of meerdere categorieën inschakelen (standaard = false)

Ook standaardeigenschappen voor diagramvelden, zoals `name`, `fieldLabel`, of `fieldDescription` worden ook ondersteund.

>[!CAUTION]
>
>Gelijk aan de `cifproductfield` de component `cifcategoryfield` de component vereist ook `cif.shell.picker` clientlib. Als u een clientlib aan een dialoogvenster wilt toevoegen, kunt u de opdracht `extraClientlibs` eigenschap. Zie [Dialoogvensters aanpassen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/customizing.html?lang=en#customizing-dialogs) van de AEM Core Components documentatie.
>[!CAUTION]
>
>Vanaf CIF Core Components versie 2.0.0 wordt de ondersteuning voor `id` is verwijderd en vervangen door `uid`. We raden u aan het gebruik van `uid` of `urlPath` als categorie-id. Wij blijven steun verlenen `id` &amp; `idAndUrlPath` alleen voor projecten die CIF Core Components versie 1.x gebruiken.

Een volledig werkend voorbeeld van het `cifcategoryfield` kunt u vinden in het dialoogvenster [CIF Core-componenten](https://github.com/adobe/aem-core-cif-components/blob/master/ui.apps/src/main/content/jcr_root/apps/core/cif/components/commerce/featuredcategorylist/v1/featuredcategorylist/_cq_dialog/.content.xml) project.
