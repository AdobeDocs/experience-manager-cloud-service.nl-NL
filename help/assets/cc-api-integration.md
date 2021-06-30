---
title: Inhoud automatiseren voor Creative Cloud-integratie
description: Variaties van elementen genereren met Creative Cloud-integratie
contentOwner: AG
feature: Uploaden, Asset Processing, Publiceren, Asset compute Microservices, Workflow
role: Business Practitioner,Administrator
source-git-commit: 05f2bfac12d37b8ef9940e3381c709891cabe236
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---


# Variaties van elementen genereren met behulp van [!DNL Adobe Creative Cloud]-integratie {#content-automation}

Inhoudsautomatisering add-on integreert Experience Manager Assets als Cloud Service- en Adobe Creative Cloud API&#39;s om uw elementen op schaal creatief te verwerken. Experience Manager gebruikt op cloud gebaseerde [assetmicroservices](/help/assets/asset-microservices-overview.md) om de Adobe Creative Cloud-functies te benutten en het maken en verwerken van middelen te automatiseren.

Als u elementen wilt bewerken in [!DNL Adobe Photoshop] en [!DNL Adobe Lightroom], hoeft u geen bestanden te downloaden van, bewerken en uploaden naar [!DNL Experience Manager Assets]. U hoeft alleen een verwerkingsprofiel te maken en te configureren, het profiel toe te passen op een map en de elementen te uploaden naar de map. De elementen die naar de map zijn geüpload, worden verwerkt om verschillende variaties van dat element te maken. De consistente en moeiteloze bulkverwerking en het uitgeven van activa bespaarde handinspanningen en verhoogt inhoudssnelheid. Bovendien kunnen ontwikkelaars en partners de assetmicroservices uitbreiden met directe toegang tot deze API&#39;s en aangepaste logica opnemen.

Gebruikers kunnen verwerkingsprofielen maken om de volgende creatieve bewerkingen op hun middelen te automatiseren:

**Automatische tint**: Hiermee maakt u gebruik van kunstmatige intelligentie om de inhoud van de afbeelding te analyseren en maakt u op intelligente wijze licht- en kleurcorrecties op basis van de unieke kenmerken van de afbeelding.
**Automatisch rechtop**: Gebruikt kunstmatige intelligentie om de inhoud van het beeld te analyseren en scheefgetrokken perspectief in beelden te verbeteren. Bijvoorbeeld om niveauhorizonten te maken.
**Lightroom-voorinstellingen**: Hiermee past u een door de gebruiker gedefinieerde vormgeving toe op afbeeldingen voor een consistente weergave met behulp van aangepaste voorinstellingen.
**Knipsel** afbeelding: Gebruikt kunstmatige intelligentie om selectie rond aliente voorwerpen tot stand te brengen en achtergrond met één enkele bevel te verwijderen.
**Afbeeldingsmasker**: Gebruikt kunstmatige intelligentie om masker rond aliente voorwerpen met één enkele bevel tot stand te brengen.
**Photoshop-handelingen**: Hiermee wordt een reeks taken (in Photoshop) toegepast op een bestand of een groep bestanden.
**Vervanging** slim object: Hiermee past u de weergave op schaal aan door afbeeldingen te wisselen met behoud van alle effecten en aanpassingen die in een PSD-bestand zijn toegepast.

## Een verwerkingsprofiel gebruiken om elementen te verwerken {#process-assets}

Ga als volgt te werk als u verwerkingsprofielen wilt gebruiken om automatisch variaties te maken:

1. Neem contact op met de klantenondersteuning van Adobe om de licentie te verkrijgen.
1. Navigeer naar Gereedschappen > Middelen > Profielen verwerken.
1. Selecteer Maken en geef een naam op.
1. Selecteer het tabblad Creatief. Geef de uitvoermap op en selecteer [!UICONTROL Add New] om creatieve configuraties toe te voegen. Geef de naam van de vertoning (of de naam van de uitvoer), de extensie (of het bestandstype), selecteer Kwaliteit (of uitvoerparameters), selecteer de lijst MIME-typen (of het filter voor invoerelementen) en selecteer de gewenste creatieve bewerking.
1. Voor sommige bewerkingen is een aanvullende parameter (element) vereist. Geef desgevraagd waarden op voor deze aanvullende parameters.

1. Voeg meer creatieve bewerkingen toe als onderdeel van hetzelfde verwerkingsprofiel of sla het profiel op.

1. Pas het verwerkingsprofiel toe op een map. Selecteer mapeigenschappen, Verwerking van middelen en selecteer het gemaakte verwerkingsprofiel.

Nadat het verwerkingsprofiel is toegepast op een DAM-map, worden naast de standaardverwerking ook de gedefinieerde bewerkingen uitgevoerd door alle elementen die in deze map (of in submappen, tenzij deze worden overschreven) zijn geüpload of bijgewerkt.

Als u de bestaande elementen handmatig wilt verwerken, selecteert u de elementen en selecteert u de optie **[!UICONTROL Reprocess]**. Selecteer vervolgens het gewenste verwerkingsprofiel.

## Tips en beperkingen {#limitations-best-practices}

* [!DNL Experience Manager] beperkt de verwerking van bedrijfsmiddelen tot 300 verzoeken per minuut per omgeving en 700 verzoeken per minuut per organisatie.
* De bestandsgrootte is beperkt tot 4 GB voor [!DNL Adobe Photoshop] API-bewerkingen en 1 GB voor [!DNL Adobe Lightroom]-bewerkingen.

>[!MORELIKETHIS]
>
>* [Configureer en gebruik de assetmicroservices via verwerkingsprofielen](/help/assets/asset-microservices-configure-and-use.md).
>* [ [!DNL Experience Manager] Integreren met [!DNL Creative Cloud]](/help/assets/aem-cc-integration-best-practices.md).

