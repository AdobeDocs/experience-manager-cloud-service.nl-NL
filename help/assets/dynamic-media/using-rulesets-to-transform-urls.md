---
title: Regelsets gebruiken om URL's te transformeren
description: Leer hoe u regelsets in Dynamic Media kunt gebruiken om URL's te transformeren. Regelsets zijn instructiesets die in een scripttaal (zoals JavaScript) zijn geschreven en die XML-gegevens evalueren en bepaalde handelingen uitvoeren als die gegevens aan bepaalde voorwaarden voldoen.
contentOwner: Rick Brough
feature: Rulesets,Troubleshooting,Upload,Best Practices
role: User
exl-id: f8010125-ba89-406a-bede-f6aa2f858c70
source-git-commit: 35f31c95e92148ff5f3472f26ea9c40fa5a17947
workflow-type: tm+mt
source-wordcount: '683'
ht-degree: 0%

---

# Regelsets gebruiken om URL&#39;s te transformeren {#using-rulesets-to-transform-urls}

U kunt regelsets in Dynamic Media gebruiken om URL&#39;s te transformeren. Regelsets zijn instructiesets die in een scripttaal (zoals JavaScript) zijn geschreven en die XML-gegevens evalueren en bepaalde handelingen uitvoeren als die gegevens aan bepaalde voorwaarden voldoen. Elke regel bestaat uit ten minste één voorwaarde en ten minste één actie. Een regel evalueert de gegevens van XML tegen de voorwaarden, en als een voorwaarde wordt voldaan, dan neemt het de aangewezen actie. Voorbeelden van regelsets zijn onder andere:

* Een MIME-achtervoegsel toevoegen. Voor veel services en websites zijn afbeeldingsachtervoegsels vereist, zoals toevoegen `.jpg` naar een URL.
* Een mappad naar de URL maken voor SEO-doeleinden (Search Engine Optimization, optimalisatie van zoekprogramma&#39;s).

  Zie [Hoe Adobe Dynamic Media Classic SEO ondersteunt](/help/assets/dynamic-media/assets/s7_seo.pdf).

* Metagegevens toevoegen aan de URL voor SEO-doeleinden (Search Engine Optimization).

  Zie [Hoe Adobe Dynamic Media Classic SEO ondersteunt](/help/assets/dynamic-media/assets/s7_seo.pdf).

* Door de positie van de inhoud in te stellen om een download te activeren.
* Vereenvoudig URL&#39;s met sjablonen voor beeldweergave voor personalisatie. Bijvoorbeeld draaien `rgb{XX,YY,ZZ}` in RTF-gereed `\redXX\greenYY\blueZZ`

* Vraag om bepaalde tekens die moeten worden gecodeerd, zoals `$`, `{`, en `}`en bepaalde tekens die naar ImageServer moeten worden gedecodeerd. Facebook werkt bijvoorbeeld niet goed met URL&#39;s die speciale tekens bevatten.

  Zie [Speciale tekens uit URL&#39;s verwijderen](https://helpx.adobe.com/experience-manager/scene7/kb/base/scene7-rulesets/remove-special-characters-urls.html).

In de context van Dynamic Media kunnen websites die een op XML gebaseerd systeem gebruiken voor het beheer van elementgegevens, XML-bestanden uploaden naar Dynamic Media. U kunt een van deze bestanden aanwijzen als het bestand met de voorverwerkingsregel voor het bedienen van Dynamic Media-elementen. Dit bestand herstructureert de standaard URL-protocolindeling om te voldoen aan de bedrijfslogica van systemen die met Dynamic Media worden geïntegreerd. U geeft een XML-bestand op dat moet dienen als het pad naar het definitiebestand voor de regel.

>[!CAUTION]
>
>Wees voorzichtig bij het gebruik van linialen; ze kunnen voorkomen dat Dynamic Media-inhoud op uw website wordt weergegeven.

Er zijn voorbeeldregels beschikbaar die u kunnen helpen uw eigen regelset te maken.
Zie [Referentie voor regelset](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/rule-set-reference/c-rule-set-reference.html).

Net als bij het maken van alle regelsets moet u ervoor zorgen dat uw XML-bestand geldig is voordat u het uploadt met een XML-validatieprogramma zoals xmlvalid.
Zie ook [Problemen met regelsets oplossen](https://helpx.adobe.com/experience-manager/scene7/kb/base/scene7-rulesets/scene7-ruleset-troubleshooting.html).

Zorg er ook voor dat u eerst de regel test die is ingesteld in een testomgeving die geen invloed heeft op uw live productieomgeving.
Productieomgevingen en staging-omgevingen vereisen doorgaans verschillende logins.

Zie de [Adobe Dynamic Media Classic-bureaubladtoepassing voor aanmeldingsgegevens](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#sign-in-dmc-app).

<!-- OBSOLETE CONTENT * **NA staging environment** login page: [https://s7sps1-staging.scene7.com/IpsWeb/](https://s7sps1-staging.scene7.com/IpsWeb/)
* **EMEA staging environment** login page: [https://s7sps3-staging.scene7.com/IpsWeb/](https://s7sps3-staging.scene7.com/IpsWeb/)
* **JAPAC staging environment** login page: [https://s7sps5-staging.scene7.com/IpsWeb/](https://s7sps5-staging.scene7.com/IpsWeb/) -->

Zie ook [De afbeelding &#39;asset&#39; gebruiken in plaats van &#39;is&#39; in een regelset](https://helpx.adobe.com/experience-manager/scene7/kb/base/scene7-rulesets/ruleset-asset-instead-image.html).

## XML-regelsets implementeren {#deploy-xml-rule-sets}

1. Open de [Dynamic Media Classic-bureaubladtoepassing](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started)en meld u vervolgens aan bij uw account.

   Uw aanmeldingsgegevens en aanmeldingsgegevens zijn door de Adobe opgegeven op het moment van levering. Neem contact op met de Klantenondersteuning als u deze informatie niet hebt.

1. Upload het bestand met de regelset als volgt:

   * Selecteer op de algemene navigatiebalk de optie **[!UICONTROL Upload]**.
   * Op de **[!UICONTROL Upload]** pagina, bij de linkerbovenhoek, selecteert u **[!UICONTROL Browse]**.
   * In de **[!UICONTROL Open]** bladert u naar het bestand met de regelset (XML).
   * Selecteer het bestand en selecteer vervolgens **[!UICONTROL Open]**.
   * Aan de rechterkant van het **[!UICONTROL Upload]** pagina, selecteert u een doelmap voor het regelsetbestand.
   * Controleer of onder aan de pagina de optie Publiceren na uploaden is ingeschakeld.
   * Selecteer in de rechterbenedenhoek van de pagina de optie **[!UICONTROL Submit Upload]**.
   * Selecteer op de algemene navigatiebalk de optie **[!UICONTROL Jobs]** om de status van de uploadtaak te controleren. Wanneer de **[!UICONTROL Status]** kolom op de **[!UICONTROL Job]** De pagina zegt Geüpload Klaar, ga aan de volgende stappen verder.

1. Navigeer op de navigatiebalk boven aan de pagina naar **[!UICONTROL Setup]** > **[!UICONTROL Application Setup]** > **[!UICONTROL Publish Setup]** > **[!UICONTROL Image Server]**.
1. Op de **[!UICONTROL Image Server Publish]** pagina, onder de **[!UICONTROL Catalog Management]** groep, zoeken **[!UICONTROL Rule Set Definition File Path]** selecteert u vervolgens **[!UICONTROL Select]**.
1. Op de **[!UICONTROL Select Rule Set Definition File (XML)]** pagina, bladert u naar het bestand met de regelset en selecteert u vervolgens in de rechterbenedenhoek van de pagina de optie **[!UICONTROL Select]**.
1. Selecteer in de rechterbenedenhoek van de pagina Setup de optie **[!UICONTROL Close]**.
1. Voer een publicatietaak voor afbeeldingsservers uit.

   De regelingestelde voorwaarden worden toegepast op de aanvragen voor live Dynamic Media Image Servers.

   Als u het regelsetbestand wijzigt, worden de wijzigingen direct toegepast wanneer u het bijgewerkte regelsetbestand opnieuw uploadt en publiceert.
