---
title: Hoe maakt u een formuliergegevensmodel?
description: Experience Manager Forms-gegevensintegratie biedt een intuïtieve gebruikersinterface voor het maken van en werken met formuliergegevensmodellen. Leer hoe te om modellen van vormgegevens met of zonder gevormde gegevensbronnen tot stand te brengen.
feature: Form Data Model
role: User, Developer
level: Beginner, Intermediate
exl-id: b17b7441-912c-44c7-a835-809f014a8c86
source-git-commit: b6dcb6308d1f4af7a002671f797db766e5cfe9b5
workflow-type: tm+mt
source-wordcount: '1485'
ht-degree: 0%

---

# Formuliergegevensmodel maken {#create-form-data-model}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/create-form-data-models.html) |
| AEM as a Cloud Service | Dit artikel |


![Gegevensintegratie](do-not-localize/data-integeration.png)

[!DNL Experience Manager Forms] gegevensintegratie biedt een intuïtieve gebruikersinterface voor het maken van en werken met formuliergegevensmodellen. Een formuliergegevensmodel is gebaseerd op gegevensbronnen voor gegevensuitwisseling; u kunt echter wel een formuliergegevensmodel maken met of zonder gegevensbron. Er zijn twee benaderingen om van gegevensmodel afhankelijk van tot stand te brengen of u gegevensbronnen hebt gevormd:

* **Vooraf geconfigureerde gegevensbronnen gebruiken**: Als u gegevensbronnen hebt geconfigureerd zoals beschreven in [Gegevensbronnen configureren](configure-data-sources.md)kunt u deze selecteren tijdens het maken van een formuliergegevensmodel. Hiermee worden alle gegevensmodelobjecten, eigenschappen en services van de geselecteerde gegevensbronnen beschikbaar gemaakt voor gebruik in het formuliergegevensmodel.

* **Zonder gegevensbronnen**: Als u geen gegevensbronnen hebt geconfigureerd voor uw formuliergegevensmodel, kunt u het nog steeds maken zonder gegevensbronnen. U kunt het formuliergegevensmodel gebruiken om Adaptive Forms te ontwerpen <!--and interactive communication--> en test ze met behulp van voorbeeldgegevens. Als er gegevensbronnen beschikbaar zijn, kunt u het formuliergegevensmodel binden met gegevensbronnen. Dit wordt automatisch weerspiegeld in de gekoppelde adaptieve Forms<!--and interactive communications-->.

>[!NOTE]
>
>U moet lid zijn van beide **fdm-auteur** en **formuliergebruiker** groepen die u wilt maken en werken met het formuliergegevensmodel. Neem contact op met uw [!DNL Experience Manager] beheerder om lid te worden van de groepen.

## Formuliergegevensmodel maken {#data-sources}

Zorg ervoor dat u de gegevensbronnen hebt geconfigureerd die u wilt gebruiken in het formuliergegevensmodel, zoals beschreven in [Gegevensbronnen configureren](configure-data-sources.md). Ga als volgt te werk om een formuliergegevensmodel te maken op basis van geconfigureerde gegevensbronnen:

1. In [!DNL Experience Manager] auteurinstantie, navigeren aan **[!UICONTROL Forms > Data Integrations]**.
1. Tik op **[!UICONTROL Create > Form Data Model]**.
1. In het dialoogvenster Formuliergegevensmodel maken:

   * Geef een naam op voor het gegevensmodel van het formulier.
   * (**Optioneel**) Geef een titel, beschrijving en codes op voor het formuliergegevensmodel.
   * (**Optioneel en alleen van toepassing als gegevensbronnen zijn geconfigureerd**) Tik op het pictogram naast het pictogram **[!UICONTROL Data Source Configuration]** en selecteer het configuratieknooppunt waar de wolkendiensten voor de gegevensbronnen u wilt gebruiken verblijven. Het beperkt de lijst van gegevensbronnen beschikbaar voor selectie op de volgende pagina tot degenen beschikbaar in de geselecteerde configuratieknooppunt. Alle [!DNL Experience Manager] gegevensbronnen van gebruikersprofielen worden standaard weergegeven. Als u geen configuratieknooppunt selecteert, worden de gegevensbronnen van alle configuratieknooppunten vermeld.

1. Tik op **[!UICONTROL Next]**.

1. (**Alleen van toepassing als gegevensbronnen zijn geconfigureerd**) **[!UICONTROL Select Datasource]** het scherm maakt een lijst van beschikbare gegevensbronnen, als om het even welk. Selecteer gegevensbronnen die u wilt gebruiken in het formuliergegevensmodel.
1. Tikken **[!UICONTROL Create]** en tikt u in het bevestigingsvenster op **[!UICONTROL Open]** om de formuliergegevensmodeleditor te openen.

   Laten we de verschillende componenten van de gebruikersinterface van de formuliergegevensmodel bekijken.

   ![Een model van de Gegevens van de Vorm met drie gegevensbronnen - de dienst RESTful; [!DNL Experience Manager] gebruikersprofiel en een RDBMS](assets/fdm-ui.png)

   A. **[!UICONTROL Data Sources]** Hier worden gegevensbronnen in een formuliergegevensmodel weergegeven. Breid een gegevensbron uit om zijn voorwerpen en de diensten van het gegevensmodel te bekijken.

   B. **[!UICONTROL Refresh Data Source Definitions]** Krijgt om het even welke veranderingen in gegevensbrondefinities van gevormde gegevensbronnen en werkt hen op het Bronlusje van Gegevens van de Modelredacteur van de Gegevens van de Vorm bij.

   C. **[!UICONTROL Model]** Inhoudsgebied waar objecten van een toegevoegd gegevensmodel worden weergegeven.

   D. **[!UICONTROL Services]** Inhoudsgebied waar bewerkingen of services met toegevoegde gegevensbron worden weergegeven.

   E. **[!UICONTROL Toolbar]** Gereedschappen voor het werken met het formuliergegevensmodel. Op de werkbalk ziet u meer opties, afhankelijk van het geselecteerde object in het formuliergegevensmodel.

   F. **[!UICONTROL Add Selected]** Hiermee voegt u geselecteerde gegevensmodelobjecten en -services toe aan het formuliergegevensmodel.

Voor meer informatie over de redacteur van het Model van de Gegevens van de Vorm en hoe u met het kunt werken om het model van vormgegevens uit te geven en te vormen, zie [Werken met formuliergegevensmodel](work-with-form-data-model.md).

## Gegevensbronnen bijwerken {#update}

Ga als volgt te werk om gegevensbronnen toe te voegen aan of bij te werken naar een bestaand formuliergegevensmodel.

1. Ga naar **[!UICONTROL Forms > Data Integrations]** selecteert u het formuliergegevensmodel waaraan u gegevensbronnen wilt toevoegen of bijwerken en tikt u op **[!UICONTROL Properties]**.
1. Ga in de eigenschappen van het formuliergegevensmodel naar **[!UICONTROL Update Source]** tab.

   In de **[!UICONTROL Update Source]** tab:

   * Tik op het bladerpictogram in het dialoogvenster **[!UICONTROL Context-Aware Configuration]** en selecteer een configuratienode waar de wolkenconfiguratie voor de gegevensbron u wilt toevoegen verblijft. Als u geen knooppunt selecteert, blijven cloudconfiguraties alleen in de `global` de knoop wordt vermeld wanneer u tikt **[!UICONTROL Add Sources]**.

   * Tik op **[!UICONTROL Add Sources]** en selecteert u de gegevensbronnen die u aan het formuliergegevensmodel wilt toevoegen. Alle gegevensbronnen geconfigureerd in `global` en het geselecteerde configuratieknooppunt, als om het even welk, wordt getoond.

   * Tik op de knop **[!UICONTROL Edit]** pictogram voor de gegevensbron en selecteer uit de lijst van beschikbare gegevensbronnen.
   * Tik op de knop **[!UICONTROL Delete]** pictogram voor de gegevensbron. Het pictogram Verwijderen is uitgeschakeld als een gegevensmodelobject in de gegevensbron wordt toegevoegd aan het formuliergegevensmodel.

     ![fdm-eigenschappen](assets/fdm-properties.png)

1. Tikken **[!UICONTROL Save & Close]** om de updates op te slaan.

>[!NOTE]
>
>Nadat u nieuwe gegevensbronnen hebt toegevoegd of bestaande gegevensbronnen hebt bijgewerkt in een formuliergegevensmodel, moet u de bindingsverwijzingen naar behoren bijwerken in Adaptive Forms<!--and interactive communications--> die gebruikmaken van het bijgewerkte formuliergegevensmodel.

## Contextbewuste configuraties voor specifieke uitvoeringsmodi {#runmode-specific-context-aware-config}

[!UICONTROL Form Data Model] gebruiken [Contextbewuste configuraties verkopen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/context-aware-configs.html) om verschillende gegevensbronparameters te steunen om met gegevensbronnen voor verschillende [!DNL Experience Manager] uitvoeringsmodi.

Wanneer [!UICONTROL Form Data Model] gebruikt cloudconfiguraties om parameters op te slaan, die bij inchecken en implementeren via bronbesturing (GIT-opslagruimte van Cloud-Manager) cloudconfiguratie met dezelfde parameters voor alle uitvoeringsmodi (ontwikkeling, werkgebied en productie) maken. Als er echter verschillende gegevenssets nodig zijn voor test- en productieomgevingen, gebruiken we gegevensbronparameters (bijvoorbeeld URL van gegevensbron) voor verschillende [!DNL Experience Manager] uitvoeringsmodi.

Om dit te bereiken moet u een configuratie tot stand brengen OSGi die parameter-waarde paren van de gegevensbron bevat. Dit treedt het zelfde paar van met voeten [!UICONTROL Form Data Model] cloudconfiguratie bij uitvoering. Aangezien de configuraties OSGi deze looppaswijzen door gebrek steunen, kunt u een gegevensbronparameter aan verschillende waarden met voeten treden die op looppaswijze worden gebaseerd.

Implementatiespecifieke cloudconfiguraties inschakelen in [!UICONTROL Form Data Model]:

1. Cloudconfiguratie maken op een lokale ontwikkelingsinstantie. Voor gedetailleerde stappen raadpleegt u [Hoe te om gegevensbronnen te vormen](/help/forms/configure-data-sources.md).

1. Sla uw cloudconfiguratie op het bestandssysteem op.
   1. Pakket maken met filter `/conf/{foldername}/settings/cloudconfigs/fdm`. Hetzelfde gebruiken `{foldername}` zoals in stap 1. en vervangen `fdm` with `azurestorage` voor Azure-opslagconfiguratie.
   1. Pakket samenstellen en downloaden. Zie voor meer informatie [pakkethandelingen](/help/implementing/developing/tools/package-manager.md).

1. Cloudconfiguratie integreren in [!DNL Experience Manager] Archetype-project.
   1. Pak het gedownloade pakket uit.
   1. Kopiëren `jcr_root` en plaatst deze uw `ui.content` > `src` > `main` > `content`.
   1. Bijwerken `ui.content` > `src` > `main` > `content` > `META-INF` > `vault` > `filter.xml` om filter te bevatten `/conf/{foldername}/settings/cloudconfigs/fdm`. Zie voor meer informatie [ui.content module of AEM Project Archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/uicontent.html). Wanneer dit archetype project door de pijpleiding van cm wordt opgesteld, wordt de zelfde wolkenconfiguratie geïnstalleerd op alle milieu&#39;s (of runmodes). Om de waarde van gebieden (zoals URL) van wolkenconfiguraties te veranderen die op milieu worden gebaseerd, gebruik de configuratie OSGi die in de volgende stap wordt besproken.

1. Maak een contextbewuste configuratie voor Apache Sling. Om de configuratie te creëren OSGi:
   1. **OSGi-configuratiebestanden instellen in [!DNL Experience Manager] Archetype-project.**
OSGi-fabrieksconfiguratiebestanden maken met PID `org.apache.sling.caconfig.impl.override.OsgiConfigurationOverrideProvider`. Maak een bestand met dezelfde naam onder elke uitvoermodusmap waarin de waarden per uitvoermodus moeten worden gewijzigd. Zie voor meer informatie [OSGi configureren voor [!DNL Adobe Experience Manager]](/help/implementing/deploying/configuring-osgi.md#creating-sogi-configurations).

   1. **Stel de configuratie-json OSGI in.** Om Apache Sling Context-Aware de Leverancier van de Opheffing van de Configuratie te gebruiken:
      1. Instantie voor lokale ontwikkeling `/system/console/configMgr`selecteert u de OSGi-configuratie in de fabriek met de naam **[!UICONTROL Apache Sling Context-Aware Configuration Override Provider: OSGi configuration]**.
      1. Geef een beschrijving.
      1. Selecteer **[!UICONTROL enabled]**.
      1. Geef onder Overschrijvingen velden op die moeten worden gewijzigd op basis van de omgeving in de syntaxis met regelafstand. Zie voor meer informatie [Contextbewuste Apache Sling-configuratie - Overschrijven](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration-override.html#override-syntax). Bijvoorbeeld, `cloudconfigs/fdm/{configName}/url="newURL"`.
U kunt meerdere overschrijvingen toevoegen door **[!UICONTROL +]**.
      1. Selecteer **[!UICONTROL Save]**.
      1. Om OSGi Configuration JSON te krijgen, volg de stappen in [OSGi-configuraties genereren met de AEM SDK QuickStart](/help/implementing/deploying/configuring-osgi.md#generating-osgi-configurations-using-the-aem-sdk-quickstart).
      1. Plaats JSON in de Dossiers van de Configuratie van de Fabriek OSGi die in de vorige stap worden gecreeerd.
      1. De waarde wijzigen van `newURL` op basis van omgeving (of runmode).
      1. Om geheime waarde te veranderen die op runmode wordt gebaseerd, kan de geheime variabele tot stand worden gebracht gebruikend [cloudbeheer-API](/help/implementing/deploying/configuring-osgi.md#cloud-manager-api-format-for-setting-properties) en kan later worden verwezen in de [OSGi-configuratie](/help/implementing/deploying/configuring-osgi.md#secret-configuration-values).
Wanneer dit archetype project door de pijpleiding van cm wordt opgesteld, zal de opheffing verschillende waarden op verschillende milieu&#39;s (of looppaswijze) verstrekken.
      >[!NOTE]
      >
      >[!DNL Adobe Managed Service] gebruikers kunnen de geheime waarden coderen gebruikend crypto steun (voor details, zie [coderingsondersteuning voor configuratie-eigenschappen](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/encryption-support-for-configuration-properties.html#enabling-encryption-support) en plaats gecodeerde tekst na [de context bewuste configuraties zijn beschikbaar in de dienstpak 6.5.13.0](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/create-form-data-models.html#runmode-specific-context-aware-config).

1. Vernieuw de gegevensbrondefinities gebruikend de optie om gegevensbrondefinities in te vernieuwen [Formuliergegevensmodeleditor](#data-sources) om FDM geheime voorgeheugen door FDM UI te verfrissen en de recentste configuratie te krijgen.

## Volgende stappen {#next-steps}

U hebt nu een formuliergegevensmodel waaraan gegevensbronnen zijn toegevoegd. Vervolgens kunt u het formuliergegevensmodel bewerken om gegevensmodelobjecten en -services toe te voegen en te configureren, koppelingen tussen gegevensmodelobjecten toe te voegen, eigenschappen te bewerken, aangepaste gegevensmodelobjecten en -eigenschappen toe te voegen, voorbeeldgegevens te genereren, enzovoort.

Zie voor meer informatie [Werken met formuliergegevensmodel](work-with-form-data-model.md).
