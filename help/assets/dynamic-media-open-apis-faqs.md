---
title: Dynamische media met OpenAPI-mogelijkheden die vaak vragen stellen
description: Dynamische media met OpenAPI-mogelijkheden die vaak vragen stellen
role: User
exl-id: 3450e050-4b0b-4184-8e71-5e667d9ca721
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '1558'
ht-degree: 0%

---

# Dynamische media met OpenAPI-mogelijkheden die vaak vragen stellen {#new-dynaminc-media-apis-frequently-asked-questions}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b> Dynamische Media Prime en Ultimate </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b> AEM Assets Ultimate </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b> integratie van AEM Assets met Edge Delivery Services </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b> Uitbreidbaarheid UI </b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuw </i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b> laat Dynamische Media Prime en Ultimate </b></a> toe
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b> Beste praktijken van het Onderzoek </b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b> Beste praktijken van Meta-gegevens </b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b> Content Hub </b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b> Dynamische Media met mogelijkheden OpenAPI </b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b> de ontwikkelaarsdocumentatie van AEM Assets </b></a>
        </td>
    </tr>
</table>

>[!AVAILABILITY]
>
>De handleiding Dynamic Media met OpenAPI-mogelijkheden is nu beschikbaar in PDF-indeling. Download de volledige handleiding en gebruik Adobe Acrobat AI Assistant om je vragen te beantwoorden.
>
>[!BADGE  Dynamische Media met OpenAPI mogelijkhedenGids PDF ]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/dynamic-media-with-openapi-capabilities.pdf"}

+++**zijn alle activa in de bewaarplaats van Experience Manager Assets as a Cloud Service beschikbaar voor onderzoek en levering gebruikend Dynamische Media met mogelijkheden OpenAPI?**

Nr, slechts [ goedgekeurde en recentste versie van de activa ](/help/assets/approve-assets.md) zijn beschikbaar voor onderzoek en levering gebruikend Dynamische Media met mogelijkheden OpenAPI, die merkconsistentie over alle kanalen en toepassingen verzekeren.

+++

+++**hoe kunnen de beheerders nieuwe en bestaande activa merken die aan een omslag zoals worden toegevoegd?**

De status van een element in Experience Manager Assets wordt bepaald door de eigenschap `jcr:content/metadata/dam:status` . De waarden van deze eigenschap kunnen zijn:

* Goedgekeurd

* Geweigerd

* Gevraagde wijzigingen

Experience Manager Assets maakt een onderscheid tussen de goedgekeurde status met behulp van een goedgekeurd pictogram dat beschikbaar is op de elementenkaart, zoals in de volgende afbeeldingen voor de weergaven Admin en Asset wordt getoond:

**Admin mening**

![ Goedgekeurde activa in Admin mening ](/help/assets/assets/approved-assets-thumbs-up.png)

**de mening van Assets**

![ Goedgekeurde activa in de mening van Assets ](/help/assets/assets/approved-assets-thumbs-up-assets-view.png)


Om alle activa in een omslag goed te keuren, zie instructies op [ hoe te in bulk goedkeuren activa in een omslag ](/help/assets/approve-assets.md#bulk-approve-assets). Er is ook een video die het gehele proces weergeeft.

Nadat u een map hebt ingesteld voor bulkgoedkeuring, worden alle nieuwe middelen die aan de map worden toegevoegd, automatisch goedgekeurd. Alle bestaande activa worden na het opwerken van activa goedgekeurd. Zie [ het Opverwerken van digitale activa ](/help/assets/reprocessing.md) voor instructies op hoe te om activa opnieuw te verwerken. Als u kopieert of niet goedgekeurde activa van een andere omslag beweegt, moet u [ de activa ](/help/assets/reprocessing.md) opnieuw verwerken.

Het element wordt gemarkeerd als `Rejected` als de beheerder `Rejected` of `Changes requested` waarden opgeeft. Experience Manager Assets onderscheidt de Geweigerde status gebruikend ![ Verwerp Assets ](/help/assets/assets/do-not-localize/reject-assets.svg) beschikbaar op de activakaart in Admin mening.

Op dezelfde manier maakt Experience Manager Assets een onderscheid tussen de status Afgewezen in de Assets-weergave en de volgende status Afgewezen op de asset card:

![ Geweigerde activa in de mening van Assets ](/help/assets/assets/rejected-assets-admin-view.png)


+++

+++**Hoe kunt u de gebruiker of groepsidentiteitskaart van Adobe IMS (Adobe Identity Management Services) worden gebruikt om de rollen op activa in de mening van Admin van Experience Manager te plaatsen, voor het beveiligen van levering en onderzoekservaring?**

Gebruikers die toegang tot de Experience Manager Author-omgeving nodig hebben, worden beheerd als gebruikers van Adobe IMS in Adobe Admin Console. Voor informatie over wat de gebruikers van Adobe IMS zijn, en hoe zij in Admin Console worden betreden en worden geleid, zie [ gebruikers IMS van Adobe ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/adobe-ims-users.html?lang=en).

+++

+++**kunt u veelvoudige activa gelijktijdig binnen een omslag goedkeuren?**

Ja, u kunt meerdere elementen in een map tegelijk goedkeuren.

Voer de volgende stappen uit om meerdere elementen tegelijk goed te keuren in [!DNL Experience Manager Assets Admin view] :

1. Selecteer de elementen en klik op **[!UICONTROL Properties]** .
1. Schuif omlaag naar **[!UICONTROL Review Status]** op het tabblad **[!UICONTROL Basic]** .
1. Wijzig de revisiestatus in **[!UICONTROL Approved]** .
1. Klik op **[!UICONTROL Save & Close]**.

Op dezelfde manier als u meerdere elementen tegelijk wilt goedkeuren in een map in de Assets-weergave:

1. Selecteer de elementen en klik op **[!UICONTROL Bulk Metadata Edit]** .

1. Selecteer **[!UICONTROL Approved]** in het **[!UICONTROL Status]** -veld dat beschikbaar is in de sectie [!UICONTROL Properties] in het rechterdeelvenster.

1. Klik op **[!UICONTROL Save]**.


+++

+++**hoe ik activalevering en onderzoek naar de Dynamische Media OpenAPIs kan beveiligen?**

Met het beheer van centrale bedrijfsmiddelen in Experience Manager kunnen de DAM-beheerders of -beheerders de toegang tot bedrijfsmiddelen beheren. Ze kunnen de toegang beperken door rollen te configureren of door activerings- en deactiveringstijd in te stellen voor goedgekeurde elementen aan de ontwerpzijde, met name in de AEM as a Cloud Service-auteurinstantie.

Eindgebruikers die URL&#39;s van levering zoeken of gebruiken, kunnen toegang krijgen tot beperkte elementen nadat ze het autorisatieproces hebben doorstaan.

Voor meer informatie, zie [ Toegang tot activa in Experience Manager ](restrict-assets-delivery.md#authoring) beperken.

+++

+++**Hoe kunt u toestemmingen krijgen om de goedkeuringsstatus van een activa uit te geven?**

Als gebruiker DAM, zou u geen toestemmingen kunnen hebben om [ activa ](approve-assets.md#approve-assets) goed te keuren. Als u machtigingen wilt verkrijgen om de goedkeuringsstatus van een element te bewerken, kunnen de beheerders de standaardinstelling of elk ander metagegevensschema dat op de elementenmap wordt toegepast, bewerken en machtigingen voor het **[!UICONTROL Review Status]** -veld opgeven. Voor meer informatie, zie [ hoe te om uit te schakelen uitgeeft voor het gebied van de Status van het Overzicht ](approve-assets.md#configuration).

+++

+++**hoe de Dynamische Media met mogelijkheden OpenAPI van Dynamische oplossing van Media verschillend is?**

Dynamische media met OpenAPI-mogelijkheden en Dynamische media vertegenwoordigen afzonderlijke oplossingen die elk hun gespecialiseerde leveringsmogelijkheden bieden. Het is absoluut noodzakelijk om uw specifieke vereisten grondig te herzien om de meest passende oplossing te bepalen die op uw behoeften richt.

Algemene richtlijnen van Adobe zijn het benutten van Dynamic Media met OpenAPI-stack voor alle gebruikte integratietoepassingen (apps van de eerste of derde partij). Als er al een integratie met Dynamic Media-stapel bestaat, wordt aangeraden deze niet te wijzigen omdat de structuur van URL&#39;s met OpenAPI-stapels anders is. Alleen voor alle nieuwe integratiefuncties kunt u OpenAPI-stapels gebruiken. Als voor uw gebruiksscenario geavanceerde modifiers nodig zijn die niet beschikbaar zijn met een OpenAPI-stapel, vermijdt u de OpenAPI-stapel totdat Adobe de tussenruimte overbrugt. Zelfs voor standaard eigen levering via AEM Assets Cloud Services, kan de OpenAPI-stack worden geëvalueerd zolang uw gebruiksscenario wordt behandeld met de modifiers die beschikbaar zijn met de OpenAPI-stack. Tot slot kunnen dynamische media en dynamische media met een OpenAPI-stapel naast elkaar bestaan, afhankelijk van de aard van uw gebruiksscenario.

Hier volgen enkele belangrijke verschillen tussen Dynamic Media met OpenAPI-mogelijkheden en Dynamic Media:

| Dynamische media met OpenAPI-mogelijkheden | Dynamische media |
|---|---|
| [ Beschikbaar slechts met Assets as a Cloud Service ](/help/assets/dynamic-media-open-apis-overview.md#prerequisites-dynaminc-media-open-apis) | Ook beschikbaar bij On-premise of Adobe Managed Services met extra configuratie en leveringsstappen. |
| [ Beperkte reeks gesteunde beeldbepalingen, zoals breedte, hoogte, roteert, omkeert, kwaliteit, en formaat ](/help/assets/deliver-assets-apis.md) | Rijke set met beschikbare afbeeldingsopties |
| [ Beperkte die activalevering op gebruikers, rollen, datum, en tijd wordt gebaseerd ](/help/assets/restrict-assets-delivery.md) | Assets gepubliceerd naar Dynamic Media is toegankelijk voor alle gebruikers |
| De meeste ontwikkelaars zijn bekend met OpenAPI-specificaties. De rekbaarheid van AEM Assets wordt werkelijk eenvoudig door [ Micro-Frontend de Selector van Activa te gebruiken ](/help/assets/overview-asset-selector.md). | API&#39;s die zijn gebaseerd op SOAP en die een barrière vormen voor het ontwikkelen van integratieaanpassingen. |
| Wijzigingen die worden aangebracht in goedgekeurde elementen in DAM, inclusief versies-updates en wijzigingen in metagegevens, worden automatisch doorgevoerd in de URL&#39;s van de levering. Met een korte tijd-aan-Levende (TTL) waarde van 10 minuten die voor Dynamische Media met mogelijkheden OpenAPI via CDN wordt gevormd, worden de updates zichtbaar over alle creatie en gepubliceerde interfaces binnen 10 minuten. | Aanbevolen CDN TTL van 10 uur. U kunt de waarde van TTL met de actie van de geheim voorgeheugenontbinding met voeten treden. |
| Alleen goedgekeurde bedrijfsmiddelen zijn beschikbaar voor de levering van bedrijfsmiddelen aan downstreamtoepassingen, waardoor in digitale ervaringen goedgekeurde bedrijfsmiddelen onder een merknaam kunnen worden geplaatst. | Updates van een via Dynamic Media gepubliceerd element worden automatisch gepubliceerd zonder goedkeuringswerkstroom. Dit garandeert niet dat middelen die door een merk zijn goedgekeurd, in digitale ervaringen worden opgenomen. |
| Gebruiksrapporten op basis van het aantal geleverde elementen. Deze functie is binnenkort beschikbaar. | Gebruiksrapporten zijn niet beschikbaar. Deze functie is binnenkort beschikbaar. |
| Assets gemarkeerd als Verlopen op Assets as a Cloud Service-dataopslag is niet meer beschikbaar voor downstreamtoepassingen. | Geen intrinsieke vervaldatum van activa. Een middel blijft openbaar tot het uit de bewaarplaats van AEM as a Cloud Service wordt geschrapt. |
| Biedt geen ondersteuning voor voorinstellingen voor afbeeldingen en mogelijkheden voor slim uitsnijden voor video. | Ondersteunt voorinstellingen voor afbeeldingen en mogelijkheden voor slim uitsnijden voor video. |
| Dynamische videocoderingscodes die ervoor zorgen dat de beste coderingen worden uitgevoerd op basis van de invoervideo. Er is geen installatie vereist voor native video-levering. | Standaard 3-coderingen, ongeacht de invoervideo (kan van invloed zijn op de prestaties van de video). U moet handmatig verschillende coderingen instellen voor verschillende bitsnelheden voor video. |
| Moeilijk om op UID gebaseerde URL&#39;s met middelen te raden (maakt URL-verwarring mogelijk), maar SEO geoptimaliseerd. | URL-verwarring is alleen beschikbaar voor URL-queryparameters. Assets-id&#39;s (elementnamen) in URL&#39;s kunnen worden opgenomen. |

+++

+++**hoe de Dynamische Media met mogelijkheden OpenAPI de beperkingen van de Verbonden eigenschap van Assets richt?**

De onderstaande tabel geeft een overzicht van de belangrijkste verschillen tussen de twee oplossingen:

| Dynamische media met OpenAPI-mogelijkheden | Verbonden Assets |
|---|---|
| Assets op de externe DAM-implementatie is beschikbaar op AEM as a Cloud Service. | Assets op de externe DAM-implementatie kan beschikbaar zijn op AEM as a Cloud Service of Adobe Managed Services. |
| Elementbinaire bestanden worden niet gekopieerd wanneer middelen op een externe DAM-implementatie beschikbaar zijn in een AEM Sites-instantie. | De binaire middelen van activa worden gekopieerd wanneer de activa op een verre plaatsing DAM op een instantie van AEM Sites beschikbaar zijn. |
| Ondersteuning voor alle typen asset-indelingen die door AEM Assets worden ondersteund. | Geen ondersteuning voor video&#39;s. |
| U kunt Dynamische Media op de lokale plaatsing van Plaatsen gebruiken terwijl het halen van activa van verre plaatsing DAM. | De dynamische Media op lokale plaatsing van Plaatsen is read-only. |
| Geen beperkingen op het aantal AEM Sites-instanties dat is verbonden met een externe DAM-implementatie. U kunt [ de toegang tot activa op de instantie van Plaatsen beperken door rollen ](/help/assets/restrict-assets-delivery.md) voor goedgekeurde activa op verre DAM te vormen. | Beperking om maximaal 4 AEM Sites-instanties te verbinden met de externe DAM-implementatie. Voor een hoger aantal is aanvullende tests vereist. |
| Zowel Asset Selector als Dynamic Media met OpenAPI-mogelijkheden zijn uitbreidbaar om aangepaste integratie mogelijk te maken. | Connected Assets API&#39;s kunnen niet worden uitgebreid om aangepaste integratie toe te staan. |
| Wijzigingen die worden aangebracht in goedgekeurde middelen die beschikbaar zijn op de externe DAM-implementatie, inclusief updates van versies en wijzigingen in metagegevens, worden automatisch weerspiegeld in de Sites-instantie binnen een korte tijd-voor-live (TTL)-waarde van 10 minuten. | Updates van middelen op externe DAM-implementatie worden automatisch afgehandeld via levenscyclusgebeurtenissen, maar nemen veel meer tijd in beslag dan bij Dynamic Media met OpenAPI-mogelijkheden. |
| Metagegevens van middelen op externe DAM zijn ook beschikbaar in AEM Sites-instantie. | Metagegevens van middelen op externe DAM zijn niet beschikbaar op AEM Sites-instanties. |

+++
