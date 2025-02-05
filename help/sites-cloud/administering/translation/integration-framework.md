---
title: Het Kader voor de Integratie van de Vertaling vormen
description: Leer hoe te om het Kader van de Integratie van de Vertaling te vormen om met de diensten van de derdevertalen te integreren.
feature: Language Copy
role: Admin
exl-id: 6e74cdee-7965-4087-a733-e9d81c4aa7c2
solution: Experience Manager Sites
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '1447'
ht-degree: 0%

---

# Het Kader voor de Integratie van de Vertaling vormen {#configuring-the-translation-integration-framework}

Het vertaalintegratiekader integreert met vertaaldiensten van derden om de vertaling van AEM inhoud te ordenen. Het gaat om drie basisstappen.

1. [ verbind met uw leverancier van de vertaaldienst ](#connecting-to-a-translation-service-provider).
1. [ creeer een configuratie van het Kader van de Integratie van de Vertaling ](#creating-a-translation-integration-configuration).
1. [ associeer de wolkenconfiguraties met uw pagina&#39;s ](#configuring-pages-for-translation).

Voor een overzicht van de eigenschappen van de inhoudsomzetting in AEM, zie [ Vertaal Inhoud voor Meertalige Plaatsen ](overview.md).

>[!TIP]
>
>Als u aan het vertalen van inhoud nieuw bent, zie ](/help/journey-sites/translation/overview.md) de Vertaalreis van 0} Plaatsen, die geleid weg door uw inhoud van AEM Sites te vertalen gebruikend AEM krachtige vertaalhulpmiddelen, ideaal voor die zonder AEM of vertaalervaring.[

## Verbinding maken met een vertaalserviceprovider {#connecting-to-a-translation-service-provider}

Maak een cloudconfiguratie die AEM verbindt met uw vertaalserviceprovider.

AEM omvat het vermogen om [ met Vertaler Microsoft® ](connect-ms-translator.md) door gebrek te verbinden. Andere verkopers van vertaaltechnologie met AEM schakelaars die lid van het de partnerprogramma van de Adobe Exchange zijn kunnen [ hier ](https://exchange.adobe.com/apps/browse/ec?page=1&amp;partnerLevel=All&amp;product=AEM&amp;q=experience+manager+translation&amp;sort=RELEVANCE) worden gevonden.

Nadat u een schakelaarpakket installeert, kunt u een wolkenconfiguratie voor de schakelaar creëren. Doorgaans moet u uw referenties opgeven voor verificatie bij de vertaalservice. Voor informatie over het toevoegen van een wolkenconfiguratie voor de Vertaalschakelaar Microsoft®, zie [ Integrerend met Vertaler Microsoft® ](connect-ms-translator.md).

Indien nodig kunt u meerdere cloudconfiguraties voor dezelfde aansluiting maken. U kunt bijvoorbeeld één configuratie maken voor elk van de accounts of projecten die u bij dezelfde leverancier hebt.

Nadat u een verbinding vormt, kunt u de configuratie tot stand brengen van het kader van de vertaalintegratie die het gebruikt.

## Een configuratie voor vertaalintegratie maken {#creating-a-translation-integration-configuration}

Maak een configuratie van het vertaalintegratieframework, zodat u kunt opgeven hoe u uw inhoud wilt vertalen. De configuratie bevat de volgende informatie:

* Welke vertaalserviceprovider moet worden gebruikt?
* Of het vertalen van mensen of machines moet worden uitgevoerd
* Of andere inhoud die aan een pagina of element is gekoppeld, zoals codes, moet worden vertaald

Nadat u een kaderconfiguratie creeert, associeert u de wolkenconfiguratie met de pagina&#39;s die u volgens de configuratie wilt vertalen. Wanneer het vertaalproces wordt gestart, gaat de vertaalworkflow verder volgens de bijbehorende frameworkconfiguratie.

Wanneer verschillende gedeelten van uw website verschillende vertaalvereisten hebben, kunt u overeenkomstig meerdere frameworkconfiguraties maken. Een meertalige website kan bijvoorbeeld kopieën in de Engelse, Spaanse en Japanse taal bevatten. De eigenaar van de site gebruikt twee verschillende vertaalserviceproviders voor Spaanse en Japanse vertalingen. Daarom worden twee configuraties van het kader gevormd. Elke configuratie gebruikt een verschillende leverancier van vertaaldiensten.

Nadat u een kader van de vertaalintegratie vormt, kunt u het [ associëren met de pagina&#39;s ](preparation.md) die het gebruiken.

>[!TIP]
>
>Voor een overzicht van de eigenschappen van de inhoudsomzetting in AEM, zie [ Vertaal Inhoud voor Meertalige Plaatsen ](overview.md).

Eén configuratie van het framework bepaalt hoe pagina-inhoud en elementen worden vertaald. Een vertaalconfiguratie maken:

1. In het [ globale navigatiemenu ](/help/sites-cloud/authoring/basic-handling.md#global-navigation), uitgezochte **Hulpmiddelen > Cloud Servicen &amp; de Cloud Servicen van de Vertaling**.
1. Navigeer naar de plaats waar u de configuratie in uw inhoudsstructuur wilt creëren. Dit is vaak gebaseerd op een bepaalde site of kan globaal zijn.
1. Verstrek de volgende informatie op de gebieden en selecteer dan **creëren**:
   1. Selecteer **Type van Configuratie** in drop-down.
   1. Ga a **Titel** voor uw configuratie in. De **Titel** identificeert de configuratie in de **Cloud Servicen** console en in pagina bezit drop-down lijsten.
   1. Naar keuze, typ a **Naam** om voor de opslagplaats knoop te gebruiken die de configuratie opslaat.
1. In **geef het venster van de Configuratie** uit, vorm de eigenschappen op de **Plaatsen** en **Assets** lusjes, en selecteer dan **sparen &amp; dicht**.

### Eigenschappen van siteconfiguratie {#sites-configuration-properties}

Het **lusje van Plaatsen** controleert hoe de vertaling van paginainhoud wordt uitgevoerd.

![ de configuratie van de Vertaling voor Plaatsen ](../assets/translation-configuration.png)

| Eigenschap | Beschrijving |
|---|---|
| Omzettingsmethode | Deze eigenschap definieert de vertaalmethode die het framework uitvoert voor site-inhoud:<br> - Machine Translation: De vertaalprovider voert de vertaling in real-time uit met behulp van automatische vertaling.<br>- Menselijke vertaling: de inhoud wordt naar de vertaalprovider gestuurd om door vertalers te worden vertaald.<br> - Niet vertalen: de inhoud wordt niet verzonden voor vertaling. Hiermee slaat u bepaalde vertakkingen met inhoud over die niet worden vertaald, maar wel kunnen worden bijgewerkt met de meest recente inhoud. |
| Vertaalbureau | Deze eigenschap definieert de vertaalprovider die de vertaling moet uitvoeren. Een leverancier verschijnt in de lijst wanneer zijn overeenkomstige schakelaar wordt geïnstalleerd. |
| Inhoudscategorie | (Alleen machinevertaling) Deze eigenschap is een categorie die de inhoud beschrijft die u wilt vertalen. De categorie kan van invloed zijn op de keuze van terminologie en woordgebruik bij het vertalen van inhoud. |
| Tags vertalen | Met deze optie schakelt u het vertalen van codes in die aan de pagina zijn gekoppeld. |
| Pagina Assets vertalen | This property define how to translate assets that are added to components from the file system or referenced from assets:<br> - Do not translate: Page assets are not translate.<br> - Gebruikend plaatsvertaling werkschema: Assets wordt behandeld volgens de configuratieeigenschappen op de **Plaatsen** tabel.<br> - Gebruikend activa vertaalwerkschema: Assets wordt behandeld volgens de eigenschappen die op **worden gevormd Assets** tabel. |
| Vertaling automatisch uitvoeren | Schakel deze eigenschap in om na het maken van vertaalprojecten automatisch vertaaltaken uit te voeren. U hebt geen mogelijkheid om de vertaaltaak te beoordelen en te vergroten wanneer u deze optie selecteert. |
| Alleen-bijwerken translatie uitschakelen | Als deze optie is ingeschakeld, worden bij het bijwerken van het vertaalproject alle vertaalbare velden voor vertaling ingediend, niet alleen de velden die zijn gewijzigd sinds de laatste vertaling. |

### Assets-configuratieeigenschappen {#assets-configuration-properties}

Assets-eigenschappen bepalen hoe elementen moeten worden geconfigureerd. Voor meer informatie over het vertalen van activa, zie [ Creërend de Kopieën van de Taal voor Assets ](/help/assets/translate-assets.md).

![ de configuratie van de Vertaling voor Plaatsen ](../assets/translation-configuration-assets.png)

| Eigenschap | Beschrijving |
|---|---|
| Omzettingsmethode | This property select the type of vertaling that the framework perform for assets:<br> - Machine Translation: The translation provider does the vertaling directly using machine conversion.<br> - Menselijke vertaling: inhoud wordt automatisch naar de vertaalprovider verzonden om handmatig te worden vertaald.<br> - Niet vertalen: Assets wordt niet verzonden voor vertaling. |
| Vertaalbureau | Deze eigenschap definieert de vertaalprovider die de vertaling moet uitvoeren. Een leverancier verschijnt in de lijst wanneer zijn overeenkomstige schakelaar wordt geïnstalleerd. |
| Inhoudscategorie | (Alleen machinevertaling) Met deze eigenschap wordt de inhoud beschreven die u wilt vertalen. De categorie kan van invloed zijn op de keuze van terminologie en woordgebruik bij het vertalen van inhoud. |
| Assets vertalen | Activeer deze eigenschap om elementen in het vertaalproject op te nemen. |
| Metagegevens vertalen | Activeer deze eigenschap zodat u metagegevens van elementen kunt vertalen. |
| Tags vertalen | Activeer deze eigenschap zodat u tags kunt vertalen die aan het element zijn gekoppeld. |
| Vertaling automatisch uitvoeren | Selecteer deze eigenschap zodat u na het maken van vertaalprojecten automatisch vertaaltaken kunt uitvoeren. U hebt geen gelegenheid om de vertaalbaan te herzien of te behandelen wanneer u deze optie selecteert. |
| Alleen-bijwerken translatie uitschakelen | Als deze optie is ingeschakeld, worden bij het bijwerken van het vertaalproject alle vertaalbare velden voor vertaling ingediend, niet alleen de velden die zijn gewijzigd sinds de laatste vertaling. |
| Velden voor inhoudsmodellen inschakelen voor vertaling | Het toelaten van deze optie gebruikt het **Vertaalbare** gebied op [ Modellen van het Fragment van de Inhoud ](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#properties) om te bepalen als het gebied wordt vertaald en creeert automatisch [ vertaalregels ](rules.md) dienovereenkomstig. Deze optie vervangt de vertaalregels die u hebt gemaakt. |

## Pagina&#39;s voor omzetting configureren {#configuring-pages-for-translation}

Als u de vertaling van uw bronpagina&#39;s in andere talen wilt configureren, koppelt u de pagina&#39;s aan de volgende cloudconfiguraties:

* De wolkenconfiguratie die AEM met uw vertaalleverancier verbindt.
* Het kader voor vertaalintegratie dat de details van de vertaling vormt.

De cloudconfiguratie van het vertaalintegratieframework identificeert de cloudconfiguratie die moet worden gebruikt om verbinding te maken met de serviceprovider. Wanneer u een bronpagina aan een configuratie van de kaderwolk associeert, moet de pagina met de configuratie van de de dienstverlener wolk worden geassocieerd die de configuratie van de kaderwolk gebruikt.

Wanneer u een pagina aan een wolkenconfiguratie associeert, erven de nakomelingen van de pagina de vereniging. Als u bijvoorbeeld de pagina `/content/wknd/language-masters/en/magazine` aan een Translation Integration Framework hebt gekoppeld, worden de pagina `magazine` en onderliggende pagina&#39;s eronder vertaald volgens het framework.

Indien nodig, kunt u de koppeling op een afstammende pagina overschrijven. De inhoud van een website gaat bijvoorbeeld vooral over reizen en levensstijl. Eén vertakking met pagina&#39;s beschrijft het bedrijf echter. In dat geval kan de hoofdpagina van de site worden gekoppeld aan een vertaalintegratieframework dat automatische vertaling opgeeft met de categorie Lifestyle. De tak die het bedrijf beschrijft zou een kader gebruiken dat machinevertaling gebruikend de Algemene categorie uitvoert.

### Een pagina koppelen aan een vertaalbureau {#associating-a-page-with-a-translation-provider}

Koppel een pagina aan de vertaalprovider die u gebruikt om de pagina en afstammende pagina&#39;s te vertalen.

1. In de plaatsenconsole, selecteer de pagina om **Eigenschappen van de Mening** te vormen en te selecteren.
1. Selecteer de **Cloud Servicen** tabel.
1. In **voeg de drop-down lijst van de Configuratie** toe, selecteer de configuratie.
1. Selecteer **sparen &amp; Sluiten**.

### Pagina&#39;s koppelen aan een vertaalintegratieframework {#associating-pages-with-a-translation-integration-framework}

Koppel een pagina aan het vertaalintegratieframework dat definieert hoe u de vertaling van de pagina en afstammende pagina&#39;s wilt uitvoeren.

1. In de plaatsenconsole, selecteer de pagina om **Eigenschappen van de Mening** te vormen en te selecteren.
1. Selecteer de **Cloud Servicen** tabel.
1. In **voeg de drop-down lijst van de Configuratie** toe, selecteer de configuratie.
1. Selecteer **sparen &amp; Sluiten**.
