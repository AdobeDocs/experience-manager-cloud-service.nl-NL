---
title: Toegangsbeheer op basis van kenmerken
description: Leer hoe te om op Attributen-gebaseerde toegangsbeheer toe te laten om op meta-gegevens-gebaseerde regels te bepalen om het niveau van toegang tot activa te bepalen beschikbaar in Content Hub
role: Admin
exl-id: 05f54b05-40b8-4a6c-af8f-5c3f7a2089d4
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '944'
ht-degree: 0%

---

# Toegangsbeheer op basis van kenmerken {#attribute-based-access-control}

Op attributen-gebaseerde toegangsbeheer (ABAC) staat de Beheerders van Content Hub toe om op meta-gegevens-gebaseerde regels te bepalen om het niveau van toegang tot activa te bepalen beschikbaar in Content Hub.

De beheerders voor een organisatie bepalen regels voor gebruikersgroepen, die aan een identiteitskaart van de Groep in kaart worden gebracht. De regels zijn een mengeling van [&#x200B; logische en vergelijkingsexploitanten &#x200B;](#supported-rule-constructs) en Admins kunnen zo vele regels bepalen aangezien zij activa toegang binnen Content Hub moeten beheren.

De regels zijn gebaseerd op metagegevens en als de voorwaarden die in de regel zijn gedefinieerd overeenkomen met de metagegevens van het element, wordt het element weergegeven aan de gebruikersgroep. Content Hub scant de activa meta-gegevens met inbegrip van de douanemetagegevens voor alle activa beschikbaar binnen **Alle Assets** en **Inzamelingen** om de resultaten aan gebruikersgroepen te tonen.

Bijvoorbeeld, sta toegang tot gebruikersgroep met Groep ID = 1011 toe, wanneer de activa meta-gegevens &quot;Merk = Merk X&quot;EN &quot;Regio = EMEA OF Amerika&quot;aanpast. Content Hub geeft alleen die elementen weer aan de gebruikersgroep met ID = 1011 waarbij Merk = `Brand X` en Regio = `EMEA` of `Americas` .

Enkele zeer belangrijke voordelen van op attribuut-gebaseerde toegangsbeheer omvatten:

* Elimineert de afhankelijkheid van de mapstructuur voor machtigingen

* Staat beheerders toe om activa te uploaden en toestemmingsstructuren met terugwerkende kracht te bepalen

* Vermindert het aantal duplicaten - verbetert de integriteit van elementen. Er zijn dubbele machtigingen nodig in op mappen gebaseerde machtigingen wanneer dezelfde elementen met verschillende groepen worden gedeeld.

## Hoe te om op Attribuut-Gebaseerd toegangsbeheer toe te laten? {#enable-attribute-based-access-control}

Op dit moment kunt u op kenmerken gebaseerde toegangsbeheerregels niet zelf maken met de Content Hub-gebruikersinterface.

Klik **Spreadsheet van de Download** om regels in een spreadsheet te downloaden en te bepalen. Maak een Adobe-ondersteuningsticket en verstrek de regels die in het spreadsheet zijn gedefinieerd aan Adobe.

[!BADGE &#x200B; Spreadsheet van de Download &#x200B;]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/ABAC_Get_Started_Template.xlsx"}


Definieer regels in het werkblad aan de hand van de richtlijnen die in dit artikel zijn gedefinieerd.

<!--

>[!IMPORTANT]
>
> After defining the rules, navigate to the **Validation Errors** tab of the spreadsheet and click **Run ABAC Validations**. **All validations passed** message confirms that you can provide the defined rules to Adobe.

-->

## Voorbeeld van een op kenmerken gebaseerde optie voor het gebruik van toegangsbeheer {#example-metadata-based-rules}

Om een grootschalige marketingimplementatie te ondersteunen, hebben verschillende teamleden in verschillende regio&#39;s en merken toegang tot digitale middelen nodig. Elke persoon heeft een specifiek bereik gebaseerd op regio en merk. ABAC past deze regels automatisch toe via metagegevens van elementen. In de volgende tabel worden de verschillende typen personen voor dit gebruiksgeval en de toegepaste regels weergegeven:

| Persona | Rol | Rolbeschrijving | Groep-id | ABAC-regel |
|---------------------|----------------|-----------------|------------|------------|
| John | EMEA Marketing Lead | Houdt toezicht op de uitvoering van marketing voor alle merken in EMEA. Voor alle merken die bestemd zijn voor EMEA-markten is toegang tot goedgekeurde activa nodig. | groep-emea-marketing | regio = &quot;EMEA&quot; |
| Mike | APAC Marketing Lead | Houdt toezicht op de uitvoering van marketing voor alle merken in APAC. Heeft voor alle merken die voor APAC-markten zijn bestemd, toegang tot goedgekeurde activa nodig. | groep-apac-marketing | regio = &quot;APAC&quot; |
| Sophie | Merk X Manager (EMEA) | Beheert Brand X-identiteit in EMEA. Alleen door Brand X goedgekeurde inhoud op de EMEA-markten te bekijken. | group-emea-brandx | regio = &quot;EMEA&quot; &amp;&amp; brand = &quot;merk X&quot; |
| Tom | Merk Y Manager (APAC) | Beheert merk Y-identiteit in APAC. Alleen door Merk Y goedgekeurde inhoud op APAC-markten bekijken. | group-apac-brandy | region = &quot;APAC&quot; &amp;&amp; brand = &quot;merk Y&quot; |

Met deze regels hebben Content Hub-beheerders het volgende:

* **korrelige, op regel-gebaseerde toegang**: De gebruikers zien slechts de activa relevant voor hun gebied en merk — geen handtoestemmingstoewijzingen.

* **Naadloze globale samenwerking**: De regionale en merkteams werkten parallel zonder toegangsconflicten.

* **Scalable en toekomstig-proefdruk toestemmingen**: Aangezien de nieuwe gebieden of de merken worden toegevoegd, kunnen de regels op meta-gegevens worden bijgewerkt.

>[!IMPORTANT]
>
> Door gebrek, worden alle andere gebruikersgroepen, die niet met om het even welke regels in het [&#x200B; spreadsheet &#x200B;](#enable-attribute-based-access-control) worden gespecificeerd, ontzegd toegang. Als een gebruiker geen deel van om het even welke groep uitmaakt waarvoor de regels ABAC worden bepaald, kunnen zij tot geen activa toegang hebben. Als u sommige gebruikers toegang tot alle activa (bijvoorbeeld, Admins) moet hebben, moet een groep met een groepsidentiteitskaart in spreadsheet met de details worden vermeld die deze bepaalde groep toegang tot alle activa vereist en Adobe zal het voor u vormen.


## Ondersteunde regelconstructies {#supported-rule-constructs}

* **Logische exploitanten**:
   * AND: Alle voorwaarden moeten waar zijn
   * OR: Ten minste één voorwaarde moet waar zijn
* **Vergelijkingsexploitanten**:
   * Gelijk aan (=): Controleert of een gebruiker of activa attribuut een waarde aanpast
   * Niet gelijk aan (!=): Controleert of een gebruiker- of elementkenmerk niet overeenkomt met een waarde

Wanneer metagegevensvelden van elementen arrays bevatten (bijvoorbeeld meerdere gebieden of tags), verwijst `Equals` naar `contains` logic en `Not Equals` naar `does not contain` logic.

Hierdoor kunt u eenvoudige en expressieve regels schrijven, zoals: ALLOW if region = emea AND assetType != prototype AND tags != vertrouwelijk.

## Richtsnoeren {#guidelines-attribute-based-access-control}

* De ABAC-regels zijn alleen van toepassing op activa die zijn goedgekeurd voor Content Hub. Voor meer informatie, zie [&#x200B; Assets voor Content Hub &#x200B;](/help/assets/approve-assets-content-hub.md) goedkeuren.

* Geef geen DENY-regels, maar zet DENY altijd om in ALLOW-regel. `ALLOW if region = <user-region> DENY if assetType = prototype AND confidential = yes` kan bijvoorbeeld worden omgezet in `ALLOW if region = <user-region> AND (assetType != prototype OR confidential != yes)` .

* ABAC-regels worden toegepast op gebruikersgroepen met behulp van de IMS Group ID, die beschikbaar is in de Admin Console.


* U kunt het [&#x200B; Doel van de Goedkeuring &#x200B;](/help/assets/approve-assets-content-hub.md#set-approval-target) voor activa plaatsen gebruikend het auteursmilieu van AEM as a Cloud Service. ABAC-regels worden toegepast op elementen die zijn goedgekeurd met Goedkeuringsdoel = `Content Hub` , aangezien Goedkeuringsdoel = `Delivery` is voor elementen die beschikbaar zijn voor `Delivery` + `Content Hub` . Assets gemarkeerd als Approval Target = `Delivery` zijn zichtbaar voor alle gebruikers in de inhoudshub.

* Zorg ervoor dat de metagegevensschema&#39;s die in ABAC-regels worden gebruikt, correct zijn gedefinieerd en beschikbaar zijn in AEM. Geef het volledige pad op van de metagegevensschema&#39;s in AEM die eigenschappen definiëren waarnaar in ABAC-regels wordt verwezen. U kunt desgewenst een testmap maken met een paar voorbeeldbestanden met metagegevenswaarden die overeenkomen met de ABAC-voorwaarden. Dit helpt bij het verifiëren van regelgedrag en het nauwkeurig evalueren van toegang.

* Leg de bedrijfsintentie van de regel in de opmerking vast, ongeacht of de voorwaarde correct is geschreven, aangezien de intent ons helpt de logica indien nodig te valideren en te corrigeren.

* De PDF-bestanden voor licenties die zijn ingesteld voor DRM, moeten zichtbaar zijn voor iedereen, zodat gebruikers ze kunnen zien wanneer ze het element met licentie downloaden.
