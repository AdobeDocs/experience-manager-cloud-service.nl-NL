---
title: Inhoud automatiseren voor Creative Cloud-integratie
description: Variaties van elementen genereren met Creative Cloud-integratie
contentOwner: AG
feature: Upload, Asset Processing, Publishing, Asset Compute Microservices
role: User, Admin
exl-id: 4cff355e-d12c-44c7-b519-4cc37f49e396
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 0%

---

# Variaties van elementen genereren met [!DNL Adobe Creative Cloud] -integratie {#content-automation}

Inhoudsautomatiseringsinvoegtoepassing integreert [!DNL Adobe Experience Manager Assets] als een [!DNL Cloud Service] - en [!DNL Adobe Creative Cloud] -API om uw elementen op schaal creatief te verwerken. [!DNL Experience Manager] gebruikt cloud-based [ activa microservices ](/help/assets/asset-microservices-overview.md) om de [!DNL Adobe Creative Cloud] eigenschappen te gebruiken en de activa verwezenlijking en media behandeling te automatiseren.

Als u elementen wilt bewerken in [!DNL Adobe Photoshop] en [!DNL Adobe Lightroom] , hoeft u geen elementen te downloaden van [!DNL Experience Manager Assets] , te bewerken en opnieuw te uploaden. U maakt en configureert een verwerkingsprofiel in [!DNL Experience Manager], past het profiel toe op een map en uploadt de middelen naar de map. De geüploade elementen worden opnieuw verwerkt op basis van de verwerkingsprofielen en deze elementen kunnen variëren. De consequente en moeiteloze bulkverwerking bespaart handmatige inspanningen en verhoogt de snelheid van de inhoud, ook zonder de behoefte aan uitstekende creatieve vaardigheden. Ook, kunnen de ontwikkelaars en de partners de activa microservices met directe toegang tot deze APIs uitbreiden en douanelogica omvatten.

Gebruikers kunnen verwerkingsprofielen maken om de volgende creatieve bewerkingen op hun middelen te automatiseren:

* **auto-toon**: Gebruikt kunstmatige intelligentie om de inhoud van het beeld te analyseren en maakt op intelligente wijze licht en kleurencorrecties die op de unieke attributen van het beeld worden gebaseerd.

* **auto-rechtop**: Gebruikt kunstmatige intelligentie om de inhoud van het beeld te analyseren en scheefgetrokken perspectief in beelden te verbeteren. Bijvoorbeeld om niveauhorizonten te maken.

  ![ autotoon ](/help/assets/assets/content-automation-autotone.png)

  *Cijfer: Auto-toon en auto-recht kunnen helpen scheefgetrokken beelden verbeteren.*

* **Lightroom stelt** vooraf in: Past een user-defined blik op beelden toe om een verenigbare verschijning te bereiken gebruikend douane-made vooraf instelt.

  ![ Lightroom vooraf ingesteld ](/help/assets/assets/content-automation-lrpresets.png)

  *Cijfer: Adobe Lightroom vooraf ingesteld om beeldkwaliteit op een verenigbare manier voor vele beelden te verbeteren.*

* **Knipsel van het Beeld**: Gebruikt kunstmatige intelligentie om selectie rond aliente voorwerpen tot stand te brengen en achtergrond met één enkel bevel te verwijderen.

  ![ verwijdert achtergrond en snijdt een beeld uit een foto ](/help/assets/assets/content-automation-backgroundremove.png)

* **Masker van het Beeld**: Gebruikt kunstmatige intelligentie om masker rond aliente voorwerpen met één enkel bevel tot stand te brengen.

  ![ Masker een beeld gebruikend AI ](/help/assets/assets/content-automation-mask.png)

* **Acties van Photoshop**: Past een reeks [!DNL Adobe Photoshop] taken op een dossier of een partij van dossiers toe.

  ![ de acties van Photoshop ](/help/assets/assets/content-automation-psactions.png)

* **Slimme Vervanging van Objecten**: Doet verpersoonlijking bij schaal door u toe te staan om beelden te ruilen terwijl het behouden van alle gevolgen en aanpassing die binnen een dossier van PSD worden toegepast.

  ![ vervang voorwerpen slim ](/help/assets/assets/content-automation-objectreplace.png)

## Enable Content Automation for AEM as a Cloud Service program {#enable-content-automation}

De add-on voor automatisering van inhoud inschakelen voor AEM as a Cloud Service-programma met Cloud Manager:

1. Neem contact op met uw accountvertegenwoordiger om een licentie te verkrijgen voor de add-on Inhoudsautomatisering.
1. Ga naar Cloud Manager en schakel over naar uw organisatie met de bedrijfskiezer.
1. Klik op **[!UICONTROL Add Program]** en geef een programmanaam op.
1. Klik op **[!UICONTROL Continue]**.
1. Vouw **[!UICONTROL Assets]** uit en selecteer **[!UICONTROL Content Automation]** .
1. Klik op **[!UICONTROL Create]**.
1. Stel de pijpleiding in werking om [ de veranderingen in Cloud Manager ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code.html) op te stellen.

Als u de add-on voor automatisering van inhoud wilt toevoegen aan een bestaand AEM as a Cloud Service-programma in Cloud Manager:

1. Klik op ... op de programmakaart.

1. Selecteer **[!UICONTROL Edit Program]** en selecteer vervolgens **[!UICONTROL Solutions & Add-ons]** tab.

1. Vouw **[!UICONTROL Assets]** uit en selecteer **[!UICONTROL Content Automation]** .
1. Klik op **[!UICONTROL Update]**.
1. Stel de pijpleiding in werking om [ de veranderingen in Cloud Manager ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code.html) op te stellen.

## Een verwerkingsprofiel gebruiken om uw creatieve middelen bulksgewijs te bewerken {#process-assets}

Ga als volgt te werk als u verwerkingsprofielen wilt gebruiken om automatisch variaties te maken:

1. Navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Processing Profiles]** .

1. Selecteer **[!UICONTROL Create]** en geef een **[!UICONTROL Name]** op.

1. Selecteer het tabblad **[!UICONTROL Creative]** , geef de uitvoermap op en selecteer **[!UICONTROL Add New]** om een creatieve configuratie toe te voegen.

1. Geef **[!UICONTROL Rendition Name]** (of uitvoernaam), **[!UICONTROL Extension]** (of bestandstype), selecteer **[!UICONTROL Quality]** (of uitvoerparameters), selecteer **[!UICONTROL Includes]** en **[!UICONTROL Excludes]** MIME-typelijsten (of invoerelementfilter) en selecteer de gewenste creatieve bewerking.

   ![[!UICONTROL Creative] tab in [!UICONTROL Processing Profile]](assets/creative-processing-profile.png)

1. Sommige bewerkingen vereisen extra parameters (element). Geef indien nodig waarden op voor deze extra parameters.

1. Voeg meer creatieve bewerkingen toe als onderdeel van hetzelfde verwerkingsprofiel of sla het profiel op.

1. Pas het verwerkingsprofiel toe op een map. Selecteer **[!UICONTROL Asset Processing]** op de pagina **[!UICONTROL Properties]** van een map en selecteer het verwerkingsprofiel dat u wilt toepassen.

Nadat u het verwerkingsprofiel op een DAM-map hebt toegepast, worden naast de standaardverwerking ook de gedefinieerde bewerkingen uitgevoerd door alle elementen die in deze map zijn geüpload of bijgewerkt. De submappen overerven dezelfde profielen als die zijn toegepast op de bovenliggende mappen. Gebruikers kunnen deze overerving overschrijven.

Als u de bestaande elementen wilt verwerken, selecteert u de elementen, selecteert u de optie **[!UICONTROL Reprocess]** en selecteert u vervolgens het gewenste verwerkingsprofiel.

## Tips en beperkingen {#limitations-best-practices}

* [!DNL Experience Manager] beperkt de verwerking van middelen tot 300 verzoeken per minuut per milieu en 700 verzoeken per minuut per organisatie.
* De bestandsgrootte is beperkt tot 4 GB voor API-bewerkingen van [!DNL Adobe Photoshop] en 1 GB voor [!DNL Adobe Lightroom] -bewerkingen.
* PDF-uitvoeringen van Microsoft Office-documenten (&quot;.docx&quot;, &quot;.doc&quot;, &quot;.ppt&quot;, &quot;.pptx&quot;, &quot;.xls&quot;, &quot;.xlsx&quot;) zijn beperkt tot bestanden van 100 MB of minder.
* Videotranscodering is beperkt tot invoerbestanden van 15 GB of minder.

**zie ook**

* [Assets vertalen](translate-assets.md)
* [ASSETS HTTP API](mac-api-assets.md)
* [Door Assets ondersteunde bestandsindelingen](file-format-support.md)
* [Zoeken in middelen](search-assets.md)
* [Verbonden elementen](use-assets-across-connected-assets-instances.md)
* [Elementen rapporteren](asset-reports.md)
* [Metagegevensschema&#39;s](metadata-schemas.md)
* [Elementen downloaden](download-assets-from-aem.md)
* [Metagegevens beheren](manage-metadata.md)
* [Zoeken in facetten](search-facets.md)
* [Verzamelingen beheren](manage-collections.md)
* [Bulkmetagegevens importeren](metadata-import-export.md)
* [Assets publiceren naar AEM en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

>[!MORELIKETHIS]
>
>* [ vorm en gebruik activa microdiensten via verwerkingsprofielen ](/help/assets/asset-microservices-configure-and-use.md).
>* [ integreer  [!DNL Experience Manager]  met  [!DNL Creative Cloud]](/help/assets/aem-cc-integration-best-practices.md).
>* [ Inname van activa en verwerking met activa microservices: Een overzicht ](/help/assets/asset-microservices-overview.md).
