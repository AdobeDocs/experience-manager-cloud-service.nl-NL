---
title: Dynamic Media met OpenAPI-mogelijkheden heeft vaak vragen gesteld
description: Dynamic Media met OpenAPI-mogelijkheden heeft vaak vragen gesteld
role: User
source-git-commit: 540aa876ba7ea54b7ef4324634f6c5e220ad19d3
workflow-type: tm+mt
source-wordcount: '1479'
ht-degree: 0%

---

# Dynamic Media met OpenAPI-mogelijkheden heeft vaak vragen gesteld {#new-dynaminc-media-apis-frequently-asked-questions}

+++**Zijn alle middelen in de Experience Manager Assets as a Cloud Service-opslagplaats beschikbaar voor zoeken en leveren met behulp van Dynamic Media met OpenAPI-mogelijkheden?**

Nee, alleen [goedgekeurde en laatste versie van de activa](/help/assets/approve-assets.md) zijn beschikbaar voor zoeken en leveren met behulp van Dynamic Media met OpenAPI-mogelijkheden, zodat alle kanalen en toepassingen consistent blijven.

+++

+++**Hoe kunnen beheerders nieuwe en bestaande activa merken die aan een omslag zoals goedgekeurd worden toegevoegd?**

De status van een activum in Experience Manager Assets wordt beheerst door `jcr:content/metadata/dam:status` eigenschap. De waarden van deze eigenschap kunnen zijn:

* Goedgekeurd

* Geweigerd

* Gevraagde wijzigingen

Experience Manager Assets maakt een onderscheid tussen de goedgekeurde status met behulp van een goedgekeurd pictogram dat beschikbaar is op de elementenkaart, zoals in de volgende afbeeldingen voor de weergaven Admin en Asset wordt getoond:

**Admin-weergave**

![Goedgekeurde middelen in de beheerweergave](/help/assets/assets/approved-assets-thumbs-up.png)

**Assets-weergave**

![Goedgekeurde middelen in Assets-weergave](/help/assets/assets/approved-assets-thumbs-up-assets-view.png)


Als u alle elementen in een map wilt goedkeuren, raadpleegt u de instructies over [hoe te bulk goedkeuren activa in een omslag](/help/assets/approve-assets.md#bulk-approve-assets). Er is ook een video die het gehele proces weergeeft.

Nadat u een map hebt ingesteld voor bulkgoedkeuring, worden alle nieuwe middelen die aan de map worden toegevoegd, automatisch goedgekeurd. Alle bestaande activa worden na het opwerken van activa goedgekeurd. Zie [Digitale middelen opnieuw verwerken](/help/assets/reprocessing.md) voor instructies over het opnieuw verwerken van elementen. Als u niet-goedgekeurde elementen uit een andere map kopieert of verplaatst, moet u [elementen opnieuw verwerken](/help/assets/reprocessing.md).

Het element is gemarkeerd als `Rejected`, als de beheerder `Rejected` of `Changes requested` waarden. Experience Manager Assets maakt onderscheid tussen de geweigerde status en ![Assets afwijzen](/help/assets/assets/do-not-localize/reject-assets.svg) beschikbaar op de elementenkaart in de beheerweergave.

Op dezelfde manier maakt Experience Manager Assets een onderscheid tussen de status Afgewezen in de Assets-weergave en de volgende status Afgewezen op de asset card:

![Geweigerde elementen in Assets-weergave](/help/assets/assets/rejected-assets-admin-view.png)


+++

+++**Hoe kunt u de gebruiker of groep-id van Adobe IMS (Adobe Identity Management Services) gebruiken om de rollen op middelen in te stellen in de mening van Admin van de Experience Manager, voor het beveiligen van levering en onderzoekservaring?**

Gebruikers die toegang tot de Experience Manager Author-omgeving nodig hebben, worden in de Admin Console van de Adobe beheerd als gebruikers van Adobe IMS. Voor informatie over welke gebruikers van Adobe IMS zijn, en hoe zij in Admin Console worden betreden en worden geleid, zie [Adobe IMS-gebruikers](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/adobe-ims-users.html?lang=en).

+++

+++**Kunt u meerdere elementen tegelijk in een map goedkeuren?**

Ja, u kunt meerdere elementen in een map tegelijk goedkeuren.

Voer de volgende stappen uit om meerdere elementen tegelijk goed te keuren in [!DNL Experience Manager Assets Admin view]:

1. Selecteer de elementen en klik op **[!UICONTROL Properties]**.
1. In de **[!UICONTROL Basic]** tab, omlaag schuiven naar **[!UICONTROL Review Status]**.
1. Wijzig de revisiestatus in **[!UICONTROL Approved]**.
1. Klik op **[!UICONTROL Save & Close]**.

Op dezelfde manier als u meerdere elementen tegelijk wilt goedkeuren in een map in de Assets-weergave:

1. Selecteer de elementen en klik op **[!UICONTROL Bulk Metadata Edit]**.

1. Selecteren **[!UICONTROL Approved]** in de **[!UICONTROL Status]** veld beschikbaar in [!UICONTROL Properties] in het rechterdeelvenster.

1. Klik op **[!UICONTROL Save]**.


+++

+++**Hoe kan ik de levering van middelen beveiligen en zoeken naar de Dynamic Media OpenAPI&#39;s?**

Het centrale beheer van activa in Experience Manager staat de Beheerders DAM of de Managers van het Merk toe om toegang tot activa te beheren. Ze kunnen de toegang beperken door rollen te configureren of door activerings- en deactiveringstijd in te stellen voor goedgekeurde elementen aan de ontwerpzijde, met name in de AEM as a Cloud Service-auteurinstantie.

Eindgebruikers die URL&#39;s van levering zoeken of gebruiken, kunnen toegang krijgen tot beperkte elementen nadat ze het autorisatieproces hebben doorstaan.

Zie voor meer informatie [Toegang tot elementen in Experience Manager beperken](restrict-assets-delivery.md#authoring).

+++

+++**Hoe kunt u toestemmingen krijgen om de goedkeuringsstatus van een activa uit te geven?**

Als DAM-gebruiker hebt u mogelijk geen machtigingen om [activa goedkeuren](approve-assets.md#approve-assets). Om de toestemmingen te krijgen om de goedkeuringsstatus van een middel uit te geven, kunnen de beheerders het gebrek of een ander meta-gegevensschema uitgeven dat op de activaomslag wordt toegepast om toestemmingen te verstrekken uitgeeft aan **[!UICONTROL Review Status]** veld. Zie voor meer informatie [bewerken voor de revisiestatus uitschakelen](approve-assets.md#configuration) veld.

+++

+++**Hoe verschilt Dynamic Media met OpenAPI-mogelijkheden van Dynamic Media-oplossingen?**

Dynamic Media met OpenAPI-mogelijkheden en Dynamic Media bieden verschillende oplossingen, elk met gespecialiseerde leveringsmogelijkheden. Het is absoluut noodzakelijk om uw specifieke vereisten grondig te herzien om de meest passende oplossing te bepalen die op uw behoeften richt.

Algemene richtlijnen van de Adobe zijn het benutten van Dynamic Media met OpenAPI-stack voor alle gebruikte integratietoepassingen (apps van de eerste of derde partij). Als er al een integratie met een Dynamic Media-stapel bestaat, is het raadzaam deze niet te wijzigen omdat de structuur van de URL&#39;s in de OpenAPI-stapel anders is. Alleen voor alle nieuwe integratiefuncties kunt u OpenAPI-stapels gebruiken. Als voor uw gebruiksscenario geavanceerde modifiers nodig zijn die niet beschikbaar zijn met een OpenAPI-stapel, vermijdt u de OpenAPI-stapel totdat de Adobe de tussenruimte overbrugt. Zelfs voor standaard native levering door AEM Assets-Cloud Servicen kan de OpenAPI-stapel worden geëvalueerd zolang uw gebruiksscenario wordt bedekt met de modifiers die beschikbaar zijn in de OpenAPI-stapel. Concluderend kunnen Dynamic Media en Dynamic Media met OpenAPI-stapel naast elkaar bestaan, afhankelijk van de aard van uw gebruiksscenario.

Hier volgen enkele belangrijke verschillen tussen Dynamic Media met OpenAPI-mogelijkheden en Dynamic Media:

| Dynamic Media met OpenAPI-mogelijkheden | Dynamic Media |
|---|---|
| [Alleen beschikbaar voor Assets as a Cloud Service](/help/assets/dynamic-media-open-apis-overview.md#prerequisites-dynaminc-media-open-apis) | Ook beschikbaar met On-premise of Adobe Managed Services met extra configuratie en leveringsstappen. |
| [Beperkte set ondersteunde afbeeldingsaanpassingen, zoals breedte, hoogte, roteren, spiegelen, kwaliteit en indeling](/help/assets/deliver-assets-apis.md) | Rijke set met beschikbare afbeeldingsopties |
| [Beperkte levering van middelen op basis van gebruikers, rollen, datum en tijd](/help/assets/restrict-assets-delivery.md) | Assets gepubliceerd naar Dynamic Media is toegankelijk voor alle gebruikers |
| De meeste ontwikkelaars zijn bekend met OpenAPI-specificaties. De uitbreidbaarheid van AEM Assets wordt heel eenvoudig met behulp van [Micro Frontend Asset Selector](/help/assets/asset-selector.md). | Op SOAP gebaseerde API&#39;s, die een barrière worden tijdens het ontwikkelen van integratieaanpassingen. |
| Wijzigingen die worden aangebracht in goedgekeurde elementen in DAM, inclusief versies-updates en wijzigingen in metagegevens, worden automatisch doorgevoerd in de URL&#39;s van de levering. Met een korte TTL-waarde (Time-to-Live) van 10 minuten die voor Dynamic Media met OpenAPI mogelijkheden via CDN wordt gevormd, worden de updates zichtbaar over alle creatie en gepubliceerde interfaces binnen 10 minuten. | Aanbevolen CDN TTL van 10 uur. U kunt de waarde van TTL met de actie van de geheim voorgeheugenontbinding met voeten treden. |
| Alleen goedgekeurde bedrijfsmiddelen zijn beschikbaar voor de levering van bedrijfsmiddelen aan downstreamtoepassingen, waardoor in digitale ervaringen goedgekeurde bedrijfsmiddelen onder een merknaam kunnen worden geplaatst. | Wijzigingen van gepubliceerde Dynamic Media-middelen worden automatisch gepubliceerd zonder enige goedkeuringswerkstroom. Dit betekent niet dat goedgekeurde middelen in digitale ervaringen automatisch worden bijgewerkt. |
| Gebruiksrapporten op basis van het aantal geleverde elementen. Deze functie is binnenkort beschikbaar. | Gebruiksrapporten zijn niet beschikbaar. Deze functie is binnenkort beschikbaar. |
| Assets gemarkeerd als Verlopen op Assets as a Cloud Service dataopslag is niet meer beschikbaar voor downstreamtoepassingen. | Geen intrinsieke vervaldatum van activa. Een middel blijft openbaar tot het uit de bewaarplaats van AEM as a Cloud Service wordt geschrapt. |
| Biedt geen ondersteuning voor voorinstellingen voor afbeeldingen en mogelijkheden voor slim uitsnijden voor video. | Ondersteunt voorinstellingen voor afbeeldingen en mogelijkheden voor slim uitsnijden voor video. |
| Dynamische videocoderingscodes die ervoor zorgen dat de beste coderingen worden uitgevoerd op basis van de invoervideo. Er is geen installatie vereist voor native video-levering. | Standaard 3-coderingen, ongeacht de invoervideo (kan van invloed zijn op de prestaties van de video). U moet handmatig verschillende coderingen instellen voor verschillende bitsnelheden voor video. |
| URL&#39;s op basis van UID-elementen (maakt URL-verwarring mogelijk) zijn moeilijk te raden, maar SEO is geoptimaliseerd. | URL-verwarring is alleen beschikbaar voor URL-queryparameters. Assets-id&#39;s (elementnamen) in URL&#39;s kunnen worden opgenomen. |

+++

+++**Hoe pakt Dynamic Media met OpenAPI-mogelijkheden de beperkingen van de functie Connected Assets aan?**

De onderstaande tabel geeft een overzicht van de belangrijkste verschillen tussen de twee oplossingen:

| Dynamic Media met OpenAPI-mogelijkheden | Verbonden Assets |
|---|---|
| Assets op de externe DAM-implementatie is beschikbaar op AEM as a Cloud Service. | Assets op de externe DAM-implementatie kan beschikbaar zijn op AEM as a Cloud Service of Adobe Managed Services. |
| Elementbinaire bestanden worden niet gekopieerd wanneer middelen op een externe DAM-implementatie beschikbaar zijn in een AEM Sites-instantie. | De binaire middelen van activa worden gekopieerd wanneer de activa op een verre plaatsing DAM op een instantie van AEM Sites beschikbaar zijn. |
| Ondersteuning voor alle typen asset-indelingen die door AEM Assets worden ondersteund. | Geen ondersteuning voor video&#39;s. |
| U kunt Dynamic Media gebruiken voor de implementatie van lokale sites terwijl u middelen haalt uit de externe DAM-implementatie. | Dynamic Media voor de implementatie van lokale sites is alleen-lezen. |
| Geen beperkingen op het aantal AEM Sites-instanties dat is verbonden met een externe DAM-implementatie. U kunt [de toegang tot elementen op de instantie Sites beperken door rollen te configureren](/help/assets/restrict-assets-delivery.md) voor goedgekeurde middelen op externe DAM. | Beperking om maximaal 4 AEM Sites-instanties te verbinden met de externe DAM-implementatie. Voor een hoger aantal is aanvullende tests vereist. |
| Zowel Asset Selector als Dynamic Media met OpenAPI-mogelijkheden zijn uitbreidbaar voor aangepaste integratie. | Connected Assets API&#39;s kunnen niet worden uitgebreid om aangepaste integratie toe te staan. |
| Wijzigingen die worden aangebracht in goedgekeurde middelen die beschikbaar zijn op de externe DAM-implementatie, inclusief updates van versies en wijzigingen in metagegevens, worden automatisch weerspiegeld in de Sites-instantie binnen een korte tijd-voor-live (TTL)-waarde van 10 minuten. | Updates van middelen op externe DAM-implementatie worden automatisch afgehandeld via levenscyclusgebeurtenissen, maar nemen veel meer tijd in beslag dan Dynamic Media met OpenAPI-mogelijkheden. |
| Metagegevens van middelen op externe DAM zijn ook beschikbaar in AEM Sites-instantie. | Metagegevens van middelen op externe DAM zijn niet beschikbaar op AEM Sites-instanties. |

+++



