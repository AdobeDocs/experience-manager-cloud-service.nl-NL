---
title: Hoe te om het Model van de Gegevens van de Vorm (FDM) tot stand te brengen?
description: Leer om een model van vormgegevens (FDM) tot stand te brengen, en gegevens te verzenden of terug te winnen naar een gegevensbron gebruikend een Aangepast Vorm of een Werkschema van AEM.
feature: Adaptive Forms, Form Data Model
role: User, Developer
level: Beginner, Intermediate
exl-id: b17b7441-912c-44c7-a835-809f014a8c86
source-git-commit: 76301ca614ae2256f5f8b00c41399298c761ee33
workflow-type: tm+mt
source-wordcount: '1472'
ht-degree: 0%

---

# Formuliergegevensmodel (FDM) maken {#create-form-data-model}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6.5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/create-form-data-models.html?lang=nl-NL) |
| AEM as a Cloud Service | Dit artikel |


![ de integratie van Gegevens ](do-not-localize/data-integeration.png)

[!DNL Experience Manager Forms] -gegevensintegratie biedt een intuïtieve gebruikersinterface voor het maken van en werken met formuliergegevensmodellen. Een model van de Gegevens van de Vorm (FDM) baseert zich op gegevensbronnen voor uitwisseling van gegevens; nochtans, kunt u een Model van de Gegevens van de Vorm (FDM) met of zonder een gegevensbron tot stand brengen. Er zijn twee benaderingen om van gegevensmodel afhankelijk van tot stand te brengen of u gegevensbronnen hebt gevormd:

* **Gebruikend preconfigured gegevensbronnen**: Als u gegevensbronnen zoals die in [ worden beschreven vormt gegevensbronnen ](configure-data-sources.md), kunt u hen selecteren terwijl het creëren van een model van vormgegevens (FDM). Hiermee worden alle gegevensmodelobjecten, -eigenschappen en -services van de geselecteerde gegevensbronnen beschikbaar voor gebruik in het FDM (Form Data Model).

* **Zonder gegevensbronnen**: Als u geen gegevensbronnen voor uw model van vormgegevens (FDM) hebt gevormd, kunt u het zonder gegevensbronnen nog tot stand brengen. Met FDM (Form Data Model) kunt u Adaptive Forms <!--and interactive communication--> ontwerpen en deze testen met behulp van voorbeeldgegevens. Wanneer de gegevensbronnen beschikbaar zijn, kunt u het Model van de Gegevens van de Vorm (FDM) met gegevensbronnen binden, die automatisch op in de bijbehorende Aanpassings Forms <!--and interactive communications--> wijst.

>[!NOTE]
>
>U moet een lid van zowel **fdm-auteur** en **vormen-gebruiker** groepen zijn om met het model van vormgegevens (FDM) te kunnen tot stand brengen en werken. Neem contact op met de [!DNL Experience Manager] -beheerder om lid te worden van de groepen.

## Formuliergegevensmodel (FDM) maken {#data-sources}

Zorg ervoor dat u de gegevensbronnen hebt gevormd u in het Model van de Gegevens van de Vorm (FDM) zoals die in [ worden beschreven vormt gegevensbronnen ](configure-data-sources.md) van plan bent te gebruiken. Ga als volgt te werk om een Form Data Model (FDM) te maken op basis van geconfigureerde gegevensbronnen:

1. Navigeer in [!DNL Experience Manager] auteurinstantie naar **[!UICONTROL Forms > Data Integrations]** .
1. Selecteer **[!UICONTROL Create > Form Data Model]** .
1. In het dialoogvenster Formuliergegevensmodel maken:

   * Geef een naam op voor het formuliergegevensmodel (FDM).
   * (**Facultatieve**) specificeer titel, beschrijving, en markeringen voor het model van vormgegevens (FDM).
   * (**Facultatief en van toepassing slechts als de gegevensbronnen** worden gevormd) selecteer het tikpictogram naast het **[!UICONTROL Data Source Configuration]** gebied en selecteer de configuratieknoop waar de wolkendiensten voor de gegevensbronnen u wilt gebruiken verblijven. Het beperkt de lijst van gegevensbronnen beschikbaar voor selectie op de volgende pagina tot degenen beschikbaar in de geselecteerde configuratieknoop. [!DNL Experience Manager] -gebruikersprofielgegevensbronnen worden standaard weergegeven. Als u geen configuratieknooppunt selecteert, worden de gegevensbronnen van alle configuratieknooppunten vermeld.

1. Selecteer **[!UICONTROL Next]** .

1. (**van toepassing slechts als de gegevensbronnen** worden gevormd) het **[!UICONTROL Select Datasource]** scherm maakt een lijst van beschikbare gegevensbronnen, als om het even welk. Selecteer gegevensbronnen die u wilt gebruiken in het formuliergegevensmodel.
1. Selecteer **[!UICONTROL Create]** en selecteer **[!UICONTROL Open]** in het bevestigingsvenster om de editor voor het formuliergegevensmodel te openen.

   Laten we de verschillende componenten van de gebruikersinterface van de formuliergegevensmodel bekijken.

   ![ het Model van de Gegevens van de Vorm van A met drie gegevensbronnen - de dienst RESTful, [!DNL Experience Manager] gebruikersprofiel, en een RDBMS ](assets/fdm-ui.png)

   A. **[!UICONTROL Data Sources]** Hiermee worden gegevensbronnen in een formuliergegevensmodel weergegeven. Breid een gegevensbron uit om zijn voorwerpen en de diensten van het gegevensmodel te bekijken.

   B. **[!UICONTROL Refresh Data Source Definitions]** vangt om het even welke veranderingen in gegevensbrondefinities van gevormde gegevensbronnen terug en werkt hen op het Bronlusje van Gegevens van de Modelredacteur van de Gegevens van de Vorm bij.

   C. **[!UICONTROL Model]** Inhoudsgebied waar objecten van een toegevoegd gegevensmodel worden weergegeven.

   D. **[!UICONTROL Services]** Inhoudsgebied waar bewerkingen of services met toegevoegde gegevensbron worden weergegeven.

   E. **[!UICONTROL Toolbar]** Gereedschappen voor het werken met het formuliergegevensmodel (FDM). Op de werkbalk ziet u meer opties, afhankelijk van het geselecteerde object in het formuliergegevensmodel (FDM).

   F. **[!UICONTROL Add Selected]** Hiermee voegt u geselecteerde gegevensmodelobjecten en -services toe aan het formuliergegevensmodel.

Voor meer informatie over de Modelredacteur van Gegevens van de Vorm en hoe u met het kunt werken om het model van vormgegevens uit te geven en te vormen (FDM), zie [ Werk met het model van vormgegevens ](work-with-form-data-model.md).

## Gegevensbronnen bijwerken {#update}

Ga als volgt te werk om gegevensbronnen toe te voegen aan of bij te werken naar een bestaand formuliergegevensmodel (FDM).

1. Ga naar **[!UICONTROL Forms > Data Integrations]** en selecteer het formuliergegevensmodel (FDM) waarin u gegevensbronnen wilt toevoegen of bijwerken. Selecteer vervolgens **[!UICONTROL Properties]** .
1. Ga in de eigenschappen van het formuliergegevensmodel naar het tabblad **[!UICONTROL Update Source]** .

   Op het tabblad **[!UICONTROL Update Source]** :

   * Selecteer het bladerpictogram in het **[!UICONTROL Context-Aware Configuration]** gebied en selecteer een configuratieknooppunt waar de wolkenconfiguratie voor de gegevensbron u wilt toevoegen verblijft. Als u geen knooppunt selecteert, worden cloudconfiguraties die alleen in het knooppunt `global` staan, weergegeven wanneer u **[!UICONTROL Add Sources]** selecteert.

   * Als u een nieuwe gegevensbron wilt toevoegen, selecteert u **[!UICONTROL Add Sources]** en selecteert u de gegevensbronnen die u aan het formuliergegevensmodel (FDM) wilt toevoegen. Alle gegevensbronnen die zijn geconfigureerd in `global` en het geselecteerde configuratieknooppunt, indien aanwezig, worden weergegeven.

   * Als u een bestaande gegevensbron wilt vervangen door een andere gegevensbron van hetzelfde type, selecteert u het pictogram **[!UICONTROL Edit]** voor de gegevensbron en kiest u een van de beschikbare gegevensbronnen in de lijst.
   * Als u een bestaande gegevensbron wilt verwijderen, selecteert u het pictogram **[!UICONTROL Delete]** voor de gegevensbron. Het pictogram Verwijderen is uitgeschakeld als een gegevensmodelobject in de gegevensbron wordt toegevoegd aan het formuliergegevensmodel (FDM).

     ![ fdm-eigenschappen ](assets/fdm-properties.png)

1. Selecteer **[!UICONTROL Save & Close]** om de updates op te slaan.

>[!NOTE]
>
>Zodra u nieuwe gegevensbronnen toevoegt of bestaande gegevensbronnen in een model van vormgegevens (FDM) bijwerkt, zorg ervoor dat u de bindende verwijzingen, zoals aangewezen, in Aanpassings Forms <!--and interactive communications--> bijwerkt die het bijgewerkte model van vormgegevens (FDM) gebruiken.

## Contextbewuste configuraties voor specifieke uitvoeringsmodi {#runmode-specific-context-aware-config}

[!UICONTROL Form Data Model (FDM)] gebruikt [ Sling context-bewuste configuraties ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/context-aware-configs.html?lang=nl-NL) om verschillende gegevensbronparameters te steunen om met gegevensbronnen voor verschillende [!DNL Experience Manager] looppaswijzen te verbinden.

Wanneer [!UICONTROL Form Data Model (FDM)] cloudconfiguraties gebruikt om parameters op te slaan, die bij inchecken en implementeren via bronbesturing (GIT-opslagruimte van Cloud-Manager) cloudconfiguratie met dezelfde parameters maakt voor alle uitvoermodi (Ontwikkeling, Werkgebied en Productie). Als er echter verschillende gegevenssets nodig zijn voor test- en productieomgevingen, gebruiken we gegevensbronparameters (bijvoorbeeld de URL van de gegevensbron) voor verschillende uitvoermodi van [!DNL Experience Manager] .

Om dit te bereiken moet u een configuratie tot stand brengen OSGi die parameter-waarde paren van de gegevensbron bevat. Dit negeert hetzelfde paar uit de cloudconfiguratie van [!UICONTROL Form Data Model (FDM)] tijdens de runtime. Aangezien de configuraties OSGi deze looppaswijzen door gebrek steunen, kunt u een gegevensbronparameter aan verschillende waarden met voeten treden die op looppaswijze worden gebaseerd.

Implementatiespecifieke cloudconfiguraties inschakelen in [!UICONTROL Form Data Model (FDM)] :

1. Cloudconfiguratie maken op een lokale ontwikkelingsinstantie. Voor gedetailleerde stappen, zie [ hoe te gegevensbronnen ](/help/forms/configure-data-sources.md) vormen.

1. Sla uw cloudconfiguratie op het bestandssysteem op.
   1. Pakket maken met filter `/conf/{foldername}/settings/cloudconfigs/fdm` . Gebruik dezelfde `{foldername}` als in stap 1. Vervang `fdm` door `azurestorage` voor Azure-opslagconfiguratie.
   1. Pakket samenstellen en downloaden. Voor details, zie [ pakketacties ](/help/implementing/developing/tools/package-manager.md).

1. Integreer de cloudconfiguratie in het project Archetype van [!DNL Experience Manager] .
   1. Pak het gedownloade pakket uit.
   1. Kopieer de map `jcr_root` en plaats deze `ui.content` > `src` > `main` > `content` .
   1. Werk `ui.content` > `src` > `main` > `content` > `META-INF` > `vault` > `filter.xml` bij voor het filter `/conf/{foldername}/settings/cloudconfigs/fdm` . Voor details, zie [ ui.content module van het Archetype van het Project van AEM ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/uicontent.html?lang=nl-NL). Wanneer dit archetype project door de pijpleiding van cm wordt opgesteld, wordt de zelfde wolkenconfiguratie geïnstalleerd op alle milieu&#39;s (of runmodes). Om de waarde van gebieden (zoals URL) van wolkenconfiguraties te veranderen die op milieu worden gebaseerd, gebruik de configuratie OSGi die in de volgende stap wordt besproken.

1. Maak een contextbewuste configuratie voor Apache Sling. Om de configuratie te creëren OSGi:
   1. **opstelling OSGi configuratiedossiers in [!DNL Experience Manager] project Archetype.**
OSGi-fabrieksconfiguratiebestanden maken met PID `org.apache.sling.caconfig.impl.override.OsgiConfigurationOverrideProvider` . Maak een bestand met dezelfde naam onder elke uitvoermodusmap waarin de waarden per uitvoermodus moeten worden gewijzigd. Voor details, zie [ het Vormen OSGi voor  [!DNL Adobe Experience Manager]](/help/implementing/deploying/configuring-osgi.md#creating-sogi-configurations).

   1. **plaats de configuratiejson OSGI.** Om Apache Sling te gebruiken met behoud van context-Aware Configuration Override Provider:
      1. Selecteer in een lokale ontwikkelingsinstantie `/system/console/configMgr` de OSGi-configuratie in de fabriek met de naam **[!UICONTROL Apache Sling Context-Aware Configuration Override Provider: OSGi configuration]** .
      1. Geef een beschrijving.
      1. Selecteer **[!UICONTROL enabled]** .
      1. Geef onder Overschrijvingen velden op die moeten worden gewijzigd op basis van de omgeving in de syntaxis met regelafstand. Voor details, zie [ Apache die Context-Aware Configuratie - met voeten treedt ](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration-override.html#override-syntax). Bijvoorbeeld `cloudconfigs/fdm/{configName}/url="newURL"` .
U kunt meerdere overschrijvingen toevoegen door **[!UICONTROL +]** te selecteren.
      1. Selecteer **[!UICONTROL Save]** .
      1. Om Configuratie JSON te krijgen OSGi, volg de stappen in [ Genererend Configuraties OSGi gebruikend AEM SDK Quickstart ](/help/implementing/deploying/configuring-osgi.md#generating-osgi-configurations-using-the-aem-sdk-quickstart).
      1. Plaats JSON in de Dossiers van de Configuratie van de Fabriek OSGi die in de vorige stap worden gecreeerd.
      1. Wijzig de waarde van `newURL` op basis van de omgeving (of de runmode).
      1. Om geheime waarde te veranderen die op runmode wordt gebaseerd, kan de geheime variabele worden gecreeerd gebruikend [ wolkenmanager API ](/help/implementing/deploying/configuring-osgi.md#cloud-manager-api-format-for-setting-properties) en kan later in de [ Configuratie OSGi ](/help/implementing/deploying/configuring-osgi.md#secret-configuration-values) worden van verwijzingen voorzien.
Wanneer dit archetype project door de pijpleiding van cm wordt opgesteld, zal de opheffing verschillende waarden op verschillende milieu&#39;s (of looppaswijze) verstrekken.

      >[!NOTE]
      >
      >[!DNL Adobe Managed Service] de gebruikers kunnen de geheime waarden coderen gebruikend crypto steun voor details, zie [ encryptiesteun voor configuratieeigenschappen ](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/encryption-support-for-configuration-properties.html?lang=nl-NL#enabling-encryption-support) en plaats gecodeerde tekst in de waarde nadat [ context bewuste configuraties in de dienstpak 6.5.13.0 ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/create-form-data-models.html?lang=nl-NL#runmode-specific-context-aware-config) beschikbaar zijn.

1. Vernieuw de gegevensbrondefinities gebruikend de optie om gegevensbrondefinities in de [ modelredacteur van Gegevens van de Vorm ](#data-sources) te verfrissen FDM geheime voorgeheugen door FDM UI en de recentste configuratie te krijgen.

## Volgende stappen {#next-steps}

U hebt nu een Model van de Gegevens van de Vorm (FDM) met gegevensbronnen die aan het worden toegevoegd. Vervolgens kunt u het formuliergegevensmodel (FDM) bewerken om gegevensmodelobjecten en -services toe te voegen en te configureren, koppelingen tussen gegevensmodelobjecten toe te voegen, eigenschappen te bewerken, aangepaste gegevensmodelobjecten en -eigenschappen toe te voegen, voorbeeldgegevens te genereren, enzovoort.

Voor meer informatie, zie [ Werk met model van vormgegevens ](work-with-form-data-model.md).


>[!MORELIKETHIS]
>
>* [ Model van de Gegevens van de Vorm van het Gebruik (FDM) ](/help/forms/using-form-data-model.md)