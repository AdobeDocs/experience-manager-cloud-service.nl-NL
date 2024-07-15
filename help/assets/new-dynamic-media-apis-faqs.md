---
title: Dynamic Media met OpenAPI-mogelijkheden heeft vaak vragen gesteld
description: Dynamic Media met OpenAPI-mogelijkheden heeft vaak vragen gesteld
role: User
source-git-commit: 0ad9f349c997c35862e4f571b4741ed4c0c947e2
workflow-type: tm+mt
source-wordcount: '1188'
ht-degree: 0%

---

# Dynamic Media met OpenAPI-mogelijkheden heeft vaak vragen gesteld {#new-dynaminc-media-apis-frequently-asked-questions}

+++**zijn alle activa in de as a Cloud Service bewaarplaats van Experience Manager Assets beschikbaar voor onderzoek en levering gebruikend Dynamic Media met mogelijkheden OpenAPI?**

Nr, slechts [ goedgekeurd en recentste versie van de activa ](/help/assets/approved-assets.md) zijn beschikbaar voor onderzoek en levering gebruikend Dynamic Media met mogelijkheden OpenAPI, die merkconsistentie over alle kanalen en toepassingen verzekeren.

+++

+++**hoe kunnen de beheerders nieuwe en bestaande activa merken die aan een omslag zoals worden toegevoegd?**

De status van een element in Experience Manager Assets wordt bepaald door de eigenschap `jcr:content/metadata/dam:status` . De waarden van deze eigenschap kunnen zijn:

* Goedgekeurd

* Geweigerd

* Gevraagde wijzigingen

Experience Manager Assets onderscheidt de Goedgekeurde status gebruikend ![ goedkeurt Assets ](assets/thumbs-up-icon.svg) beschikbaar op de activakaart, zoals die in het volgende beeld wordt getoond:

![ Pictogram voor Goedgekeurde activa ](/help/assets/assets/approved-assets-thumbs-up.png)

Om alle activa in een omslag goed te keuren, zie instructies op [ hoe te in bulk goedkeuren activa in een omslag ](/help/assets/approved-assets.md#bulk-approve-assets). Er is ook een video die het gehele proces weergeeft.

Nadat u een map hebt ingesteld voor bulkgoedkeuring, worden alle nieuwe middelen die aan de map worden toegevoegd, automatisch goedgekeurd. Alle bestaande activa worden na het opwerken van activa goedgekeurd. Zie [ het Opverwerken van digitale activa ](/help/assets/reprocessing.md) voor instructies op hoe te om activa opnieuw te verwerken. Als u kopieert of niet goedgekeurde activa van een andere omslag beweegt, moet u [ de activa ](/help/assets/reprocessing.md) opnieuw verwerken.

Het element wordt gemarkeerd als `Rejected` als de beheerder `Rejected` of `Changes requested` waarden opgeeft. Experience Manager Assets onderscheidt de Geweigerde status gebruikend ![ Weigeer Assets ](/help/assets/assets/do-not-localize/reject-assets.svg) beschikbaar op de activakaart.

+++

+++**hoe kunt u de gebruiker of groepsidentiteitskaart van Adobe IMS (de Diensten van Adobe Identity Management) worden gebruikt om de rollen op activa in de mening van Admin van de Experience Manager te plaatsen, voor het beveiligen van levering en onderzoekservaring?**

Gebruikers die toegang tot de Experience Manager Author-omgeving nodig hebben, worden in de Admin Console van de Adobe beheerd als gebruikers van Adobe IMS. Voor informatie over wat de gebruikers van Adobe IMS zijn, en hoe zij in Admin Console worden betreden en beheerd, zie [ gebruikers IMS van Adobe ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/adobe-ims-users.html?lang=en).

+++

+++**kunt u veelvoudige activa gelijktijdig binnen een omslag goedkeuren?**

Ja, u kunt meerdere elementen in een map tegelijk goedkeuren.

Voer de volgende stappen uit om meerdere elementen tegelijk goed te keuren in [!DNL Experience Manager Assets] :

1. Selecteer de elementen en klik op **[!UICONTROL Properties]** .
1. Schuif omlaag naar **[!UICONTROL Review Status]** op het tabblad **[!UICONTROL Basic]** .
1. Wijzig de revisiestatus in **[!UICONTROL Approved]** .
1. Klik op **[!UICONTROL Save & Close]**.

+++

+++**Hoe kan ik activalevering en onderzoek naar Dynamic Media OpenAPIs beveiligen?**

Het centrale beheer van activa in Experience Manager staat de Beheerders DAM of de Managers van het Merk toe om toegang tot activa te beheren. Zij kunnen de toegang beperken door rollen voor goedgekeurde activa aan de auteurskant, specifiek op de auteursinstantie van AEM as a Cloud Service te vormen.

Eindgebruikers die URL&#39;s van levering zoeken of gebruiken, kunnen toegang krijgen tot beperkte elementen nadat ze het autorisatieproces hebben doorstaan.

Voor meer informatie, zie [ toegang tot activa in Experience Manager ](restrict-assets-delivery.md#authoring) beperken.

+++

+++**Hoe kunt u toestemmingen krijgen om de goedkeuringsstatus van een activa uit te geven?**

Als gebruiker DAM, zou u geen toestemmingen kunnen hebben om [ activa ](approved-assets.md#approve-assets) goed te keuren. Als u machtigingen wilt verkrijgen om de goedkeuringsstatus van een element te bewerken, kunnen de beheerders de standaardinstelling of elk ander metagegevensschema dat op de elementenmap wordt toegepast, bewerken en machtigingen voor het **[!UICONTROL Review Status]** -veld opgeven. Voor meer informatie, zie [ hoe te om uit te schakelen uitgeeft voor het gebied van de Status van het Overzicht ](approved-assets.md#configuration).

+++

+++**hoe Dynamic Media met mogelijkheden OpenAPI van de oplossing van Dynamic Media verschillend is?**

Dynamic Media met OpenAPI-mogelijkheden en Dynamic Media bieden verschillende oplossingen, elk met gespecialiseerde leveringsmogelijkheden. Het is absoluut noodzakelijk om uw specifieke vereisten grondig te herzien om de meest passende oplossing te bepalen die op uw behoeften richt.

Hier volgen enkele belangrijke verschillen tussen Dynamic Media met OpenAPI-mogelijkheden en Dynamic Media:

| Dynamic Media met OpenAPI-mogelijkheden | Dynamic Media |
|---|---|
| [ Beschikbaar slechts met Assets as a Cloud Service ](/help/assets/new-dynamic-media-overview.md#prerequisites-new-dynaminc-media-apis) | Ook beschikbaar met On-premise of Adobe Managed Services met extra configuratie en leveringsstappen. |
| [ Beperkte reeks gesteunde beeldbepalingen, zoals breedte, hoogte, roteert, omkeert, kwaliteit, en formaat ](/help/assets/deliver-assets-apis.md) | Rijke set met beschikbare afbeeldingsopties |
| [ Beperkte die activalevering op gebruikers en rollen wordt gebaseerd ](/help/assets/restrict-assets-delivery.md) | Assets gepubliceerd naar Dynamic Media is toegankelijk voor alle gebruikers |
| Ondersteunt slimme uitsnijdingen in afbeeldingen | Ondersteunt slim uitsnijden in afbeeldingen en video |
| Stapelen op basis van OpenAPI-specificaties, waarmee de meeste ontwikkelaars te maken hebben. De rekbaarheid van AEM Assets wordt werkelijk eenvoudig door [ Micro Frontend de Selector van Activa te gebruiken ](/help/assets/asset-selector.md). | Op SOAP gebaseerde API&#39;s, die een barrière worden tijdens het ontwikkelen van integratieaanpassingen. |
| Wijzigingen die worden aangebracht in goedgekeurde elementen in DAM, inclusief versies-updates en wijzigingen in metagegevens, worden automatisch doorgevoerd in de URL&#39;s van de levering. Met een korte TTL-waarde (Time-to-Live) van 10 minuten die voor Dynamic Media met OpenAPI mogelijkheden via CDN wordt gevormd, worden de updates zichtbaar over alle creatie en gepubliceerde interfaces binnen 10 minuten. | Aanbevolen CDN TTL van 10 uur. U kunt de waarde van TTL met de actie van de geheim voorgeheugenontbinding met voeten treden. |
| Alleen goedgekeurde bedrijfsmiddelen zijn beschikbaar voor de levering van bedrijfsmiddelen aan downstreamtoepassingen, waardoor in digitale ervaringen goedgekeurde bedrijfsmiddelen onder een merknaam kunnen worden geplaatst. De geleverde activa respecteren de status van de afloopdatum van het activum op instantie van de auteur van de gegevensopslagplaats van AEM as a Cloud Service. | Wijzigingen van gepubliceerde Dynamic Media-middelen worden automatisch gepubliceerd zonder enige goedkeuringswerkstroom. Dit betekent niet dat goedgekeurde middelen in digitale ervaringen automatisch worden bijgewerkt. Geen intrinsieke vervaldatum van activa. Een middel blijft openbaar tot het uit de bewaarplaats van AEM as a Cloud Service wordt geschrapt. |
| Gebruiksrapporten op basis van het aantal geleverde elementen. | Gebruiksrapporten zijn niet beschikbaar. |

+++

+++**hoe Dynamic Media met mogelijkheden OpenAPI de beperkingen van de Verbonden eigenschap van Assets richt?**

De onderstaande tabel geeft een overzicht van de belangrijkste verschillen tussen de twee oplossingen:

| Dynamic Media met OpenAPI-mogelijkheden | Verbonden Assets |
|---|---|
| Assets op de externe DAM-implementatie is beschikbaar op AEM as a Cloud Service. | Assets op de externe DAM-implementatie kan beschikbaar zijn op AEM as a Cloud Service of Adobe Managed Services. |
| Elementbinaire bestanden worden niet gekopieerd wanneer middelen op een externe DAM-implementatie beschikbaar zijn in een AEM Sites-instantie. | De binaire middelen van activa worden gekopieerd wanneer de activa op een verre plaatsing DAM op een instantie van AEM Sites beschikbaar zijn. |
| Ondersteuning voor alle typen asset-indelingen die door AEM Assets worden ondersteund. | Geen ondersteuning voor video&#39;s. |
| Biedt ondersteuning voor slim uitsnijden van afbeeldingen. | Ondersteuning voor Dynamic Media-afbeeldingen met slimme gewassen en voorinstellingen voor afbeeldingen. |
| U kunt Dynamic Media gebruiken voor de implementatie van lokale sites terwijl u middelen haalt uit de externe DAM-implementatie. | Dynamic Media voor de implementatie van lokale sites is alleen-lezen. |
| Geen beperkingen op het aantal AEM Sites-instanties dat is verbonden met een externe DAM-implementatie. U kunt [ de toegang tot activa op de instantie van Plaatsen beperken door rollen ](/help/assets/restrict-assets-delivery.md) voor goedgekeurde activa op verre DAM te vormen. | Beperking om maximaal 4 AEM Sites-instanties te verbinden met de externe DAM-implementatie. Voor een hoger aantal is aanvullende tests vereist. |
| Zowel Asset Selector als Dynamic Media met OpenAPI-mogelijkheden zijn uitbreidbaar voor aangepaste integratie. | Connected Assets API&#39;s kunnen niet worden uitgebreid om aangepaste integratie toe te staan. |
| Wijzigingen die worden aangebracht in goedgekeurde middelen die beschikbaar zijn op de externe DAM-implementatie, inclusief updates van versies en wijzigingen in metagegevens, worden automatisch weerspiegeld in de Sites-instantie binnen een korte tijd-voor-live (TTL)-waarde van 10 minuten. | Updates van middelen op externe DAM-implementatie worden automatisch afgehandeld via levenscyclusgebeurtenissen, maar nemen veel meer tijd in beslag dan Dynamic Media met OpenAPI-mogelijkheden. |
| Metagegevens van middelen op externe DAM zijn ook beschikbaar in AEM Sites-instantie. | Metagegevens van middelen op externe DAM zijn niet beschikbaar op AEM Sites-instanties. |

+++



