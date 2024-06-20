---
title: Gebruik van CIF product- en rubriekkiezer
description: Leer hoe te om CIF product & categoriekiezer in uw componenten van de klantenhandel te gebruiken om auteurs en verkopers te steunen om met handelsproduct en catalogusgegevens efficiënt te werken.
sub-product: Commerce
topics: Development
version: Cloud Service
activity: develop
audience: developer
feature: Commerce Integration Framework
exl-id: 30f1f263-1b78-46ae-99ed-61861c488b2a
role: Admin
source-git-commit: 0e328d013f3c5b9b965010e4e410b6fda2de042e
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 0%

---

# AEM Content &amp; Commerce Authoring Pickers {#cif-pickers}

AEM Content &amp; Commerce Authoring biedt een reeks ontwerpgereedschappen waarmee AEM auteurs en marketers efficiënt kunnen werken met handelsproductgegevens en -catalogi. De productkiezer en de rubriekkiezer maken deel uit van CIF invoegtoepassing en worden gebruikt door de CIF Core Components. Projecten kunnen deze kiezers in elk dialoogvenster gebruiken om producten of categorieën te selecteren.

## Productkiezer {#product-picker}

Om de productkiezer in een projectcomponent te gebruiken, moet een ontwikkelaar toevoegen `commerce/gui/components/common/cifproductfield` naar een componentdialoogvenster. Gebruik bijvoorbeeld het volgende voor de `cq:dialog`:

```xml
<product jcr:primaryType="nt:unstructured"
    sling:resourceType="commerce/gui/components/common/cifproductfield"
    fieldDescription="The product or product variant displayed by the teaser"
    fieldLabel="Select Product"
    filter="folderOrProductOrVariant"
    name="./selection"
    selectionId="sku"/>
```

In het productveld kunt u naar het product navigeren dat een gebruiker wil selecteren aan de hand van de verschillende weergaven. Door gebrek keert het productgebied identiteitskaart van het product terug, maar het kan het vormen gebruikend `selectionId` kenmerk.

Het veld Productkiezer ondersteunt de volgende optionele eigenschappen:

- selectionId (id, uid, SKU, slug, gecombineerdeSlug, gecombineerdeSku) - laat u het productkenmerk kiezen dat door de kiezer moet worden geretourneerd (gebrek = id). Het gebruiken SKU keert SKU van het geselecteerde product terug. Het gebruiken van gecombineerdeSku keert een koord als base#variant met SKUs van het basisproduct en de geselecteerde variant terug, of één enkele SKU als een basisproduct wordt geselecteerd.
- filter (folderOrProduct, folderOrProductOrVariant) - filtert de inhoud die door de kiezer moet worden gerenderd tijdens het navigeren in de productstructuur. folderOrProduct - rendert mappen en producten. folderOrProductOrVariant - geeft omslagen, product, en productvarianten terug. Als een product of productvariant wordt weergegeven, wordt deze ook selecteerbaar in de kiezer. (standaard = folderOrProduct)
- meerdere (true, false) - de selectie van een of meerdere producten inschakelen (standaard = false)
- emptyText - om de lege tekstwaarde van het plukkerveld te vormen

Ook standaardeigenschappen voor dialoogvensters, zoals `name`, `fieldLabel`, of `fieldDescription`, worden ondersteund.

>[!CAUTION]
>
>De `cifproductfield` component vereist de `cif.shell.picker` clientlib. Als u een clientlib aan een dialoogvenster wilt toevoegen, kunt u de eigenschap extraClientlibs gebruiken.
>[!CAUTION]
>
>Vanaf CIF Core Components versie 2.0.0 wordt de ondersteuning voor `id` is verwijderd en vervangen door `uid`. Adobe raadt u aan `sku` of `slug` als product-id. Adobe blijft steun verlenen `id` alleen voor projecten die CIF Core Components versie 1.x gebruiken.

Een volledig werkend voorbeeld van het `cifproductfield` kunt u vinden in het dialoogvenster [CIF kerncomponenten](https://github.com/adobe/aem-core-cif-components/blob/master/ui.apps/src/main/content/jcr_root/apps/core/cif/components/commerce/productteaser/v1/productteaser/_cq_dialog/.content.xml) project. Zie ook [Dialoogvensters aanpassen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/customizing.html#customizing-dialogs) van de AEM Core Components documentatie.

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

- selectionId(id, uid, slug, urlPath, idAndUrlPath) _(afgekeurd)_, uidAndUrlPath _(afgekeurd)_) - Hiermee kunt u het categoriekenmerk kiezen dat door de kiezer moet worden geretourneerd (standaard = id).
- meerdere (true, false) - de selectie van een of meerdere categorieën inschakelen (standaard = false)

Ook standaardeigenschappen voor dialoogvensters, zoals `name`, `fieldLabel`, of `fieldDescription`, worden ondersteund.

>[!CAUTION]
>
>Gelijk aan de `cifproductfield` de component `cifcategoryfield` vereist ook `cif.shell.picker` clientlib. Als u een clientlib aan een dialoogvenster wilt toevoegen, kunt u de opdracht `extraClientlibs` eigenschap. Zie [Dialoogvensters aanpassen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/customizing.html#customizing-dialogs) van de AEM Core Components documentatie.
>[!CAUTION]
>
>Vanaf CIF Core Components versie 2.0.0 wordt de ondersteuning voor `id` is verwijderd en vervangen door `uid`. Adobe raadt u aan `uid` of `urlPath` als categorie-id. Adobe blijft steun verlenen `id` &amp; `idAndUrlPath` alleen voor projecten die CIF Core Components versie 1.x gebruiken.

Een volledig werkend voorbeeld van het `cifcategoryfield` kunt u vinden in het dialoogvenster [CIF kerncomponenten](https://github.com/adobe/aem-core-cif-components/blob/master/ui.apps/src/main/content/jcr_root/apps/core/cif/components/commerce/featuredcategorylist/v1/featuredcategorylist/_cq_dialog/.content.xml) project.
