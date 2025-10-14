---
title: Regelsets gebruiken om URL's te transformeren
description: Leer hoe te om regelreeksen in Dynamische Media op te stellen om URLs om te zetten. Regelsets zijn instructiesets die in een scripttaal (zoals JavaScript) zijn geschreven en die XML-gegevens evalueren en bepaalde handelingen uitvoeren als die gegevens aan bepaalde voorwaarden voldoen.
contentOwner: Rick Brough
feature: Rulesets,Troubleshooting,Upload,Best Practices
role: User
exl-id: f8010125-ba89-406a-bede-f6aa2f858c70
source-git-commit: 36ab36ba7e14962eba3947865545b8a3f29f6bbc
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 0%

---

# Regelsets gebruiken om URL&#39;s te transformeren {#using-rulesets-to-transform-urls}

U kunt regelsets implementeren in dynamische media om URL&#39;s te transformeren. Regelsets zijn instructiesets die in een scripttaal (zoals JavaScript) zijn geschreven en die XML-gegevens evalueren en bepaalde handelingen uitvoeren als die gegevens aan bepaalde voorwaarden voldoen. Elke regel bestaat uit ten minste één voorwaarde en ten minste één actie. Een regel evalueert de gegevens van XML tegen de voorwaarden, en als een voorwaarde wordt voldaan, dan neemt het de aangewezen actie. Voorbeelden van regelsets zijn onder andere:

* Een MIME-achtervoegsel toevoegen. Voor veel services en websites zijn afbeeldingsachtervoegsels vereist, zoals het toevoegen van `.jpg` aan een URL.
* Een mappad naar de URL maken voor SEO-doeleinden (Search Engine Optimization, optimalisatie van zoekprogramma&#39;s).

  Zie [&#x200B; hoe Adobe Dynamic Media Classic SEO &#x200B;](/help/assets/dynamic-media/assets/s7_seo.pdf) steunt.

* Metagegevens toevoegen aan de URL voor SEO-doeleinden (Search Engine Optimization).

  Zie [&#x200B; hoe Adobe Dynamic Media Classic SEO &#x200B;](/help/assets/dynamic-media/assets/s7_seo.pdf) steunt.

* Door de positie van de inhoud in te stellen om een download te activeren.
* Vereenvoudig URL&#39;s met sjablonen voor beeldweergave voor personalisatie. Draai `rgb{XX,YY,ZZ}` bijvoorbeeld om in RTF-ready `\redXX\greenYY\blueZZ`

* Vraag om bepaalde tekens die moeten worden gecodeerd, zoals `$` , `{` en `}` , en bepaalde tekens die naar ImageServer moeten worden gedecodeerd. Facebook werkt bijvoorbeeld niet goed met URL&#39;s die speciale tekens bevatten.

In de context van Dynamic Media kunnen websites die een op XML gebaseerd systeem gebruiken voor het beheer van elementgegevens, XML-bestanden uploaden naar Dynamic Media. U kunt een van deze bestanden aanwijzen als het bestand met de regelset voor voorbewerking voor het bedienen van de dynamische media-elementen. Dit dossier herstructureert het standaard URL protocolformaat om aan de bedrijfslogica van systemen te voldoen die met Dynamische Media worden geïntegreerd. U geeft een XML-bestand op dat moet dienen als het pad naar het definitiebestand voor de regel.

>[!CAUTION]
>
>Wees voorzichtig bij het gebruik van linialen; u kunt voorkomen dat dynamische media-inhoud op uw website wordt weergegeven.

Er zijn voorbeeldregels beschikbaar die u kunnen helpen uw eigen regelset te maken.
Zie [&#x200B; de vastgestelde verwijzing van de Regel &#x200B;](https://experienceleague.adobe.com/nl/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/rule-set-reference/c-rule-set-reference).

Net als bij het maken van alle regelsets moet u ervoor zorgen dat uw XML-bestand geldig is voordat u het uploadt met een XML-validatieprogramma zoals xmlvalid.

Zorg er ook voor dat u eerst de regel test die is ingesteld in een testomgeving die geen invloed heeft op uw live productieomgeving.
Productieomgevingen en staging-omgevingen vereisen doorgaans verschillende logins.

Zie de [&#x200B; Desktoptoepassing van Adobe Dynamic Media Classic voor login informatie &#x200B;](https://experienceleague.adobe.com/nl/docs/dynamic-media-classic/using/getting-started/signing-out).

<!-- OBSOLETE CONTENT * **NA staging environment** login page: [https://s7sps1-staging.scene7.com/IpsWeb/](https://s7sps1-staging.scene7.com/IpsWeb/)
* **EMEA staging environment** login page: [https://s7sps3-staging.scene7.com/IpsWeb/](https://s7sps3-staging.scene7.com/IpsWeb/)
* **JAPAC staging environment** login page: [https://s7sps5-staging.scene7.com/IpsWeb/](https://s7sps5-staging.scene7.com/IpsWeb/) -->



## XML-regelsets implementeren {#deploy-xml-rule-sets}

1. Open de [&#x200B; Desktoptoepassing van Dynamic Media Classic &#x200B;](https://experienceleague.adobe.com/nl/docs/dynamic-media-classic/using/getting-started/signing-out), dan login aan uw rekening.

   Adobe heeft uw aanmeldingsgegevens en aanmeldingsgegevens opgegeven op het moment van de levering. Neem contact op met de Klantenondersteuning als u deze informatie niet hebt.

1. Upload het bestand met de regelset als volgt:

   * Selecteer **[!UICONTROL Upload]** op de algemene navigatiebalk.
   * Selecteer **[!UICONTROL Browse]** op de pagina **[!UICONTROL Upload]** in de linkerbovenhoek.
   * Blader in het dialoogvenster **[!UICONTROL Open]** naar het bestand met de regelset (XML).
   * Selecteer het bestand en selecteer vervolgens **[!UICONTROL Open]** .
   * Selecteer rechts van de pagina **[!UICONTROL Upload]** een doelmap voor het bestand met regelsets.
   * Controleer of onder aan de pagina de optie Publiceren na uploaden is ingeschakeld.
   * Selecteer **[!UICONTROL Submit Upload]** in de rechterbenedenhoek van de pagina.
   * Selecteer op de algemene navigatiebalk **[!UICONTROL Jobs]** om de status van de uploadtaak te controleren. Ga door met de volgende stappen in de kolom **[!UICONTROL Status]** op de pagina **[!UICONTROL Job]** .

1. Ga op de navigatiebalk boven aan de pagina naar **[!UICONTROL Setup]** > **[!UICONTROL Application Setup]** > **[!UICONTROL Publish Setup]** > **[!UICONTROL Image Server]** .
1. Zoek op de pagina **[!UICONTROL Image Server Publish]** onder de groep **[!UICONTROL Catalog Management]** naar **[!UICONTROL Rule Set Definition File Path]** en selecteer vervolgens **[!UICONTROL Select]** .
1. Blader op de pagina **[!UICONTROL Select Rule Set Definition File (XML)]** naar het bestand met de regelset en selecteer vervolgens in de rechterbenedenhoek van de pagina **[!UICONTROL Select]** .
1. Selecteer **[!UICONTROL Close]** in de rechterbenedenhoek van de pagina Setup.
1. Voer een publicatietaak voor afbeeldingsservers uit.

   De regelvastgestelde voorwaarden worden toegepast op de aanvragen voor de live Dynamic Media Image Servers.

   Als u het regelsetbestand wijzigt, worden de wijzigingen direct toegepast wanneer u het bijgewerkte regelsetbestand opnieuw uploadt en publiceert.
