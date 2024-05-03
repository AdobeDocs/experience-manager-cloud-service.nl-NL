---
title: Hoe te om Azure opslag te vormen?
description: Leer hoe u formulieren kunt integreren met Azure-opslagserver.
feature: Adaptive Forms, Form Data Model
role: User, Developer
exl-id: 606383b3-293c-43d2-9ba0-5843c4e0caa8
source-git-commit: 7b31a2ea016567979288c7a8e55ed5bf8dfc181d
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 0%

---

# Configureren [!DNL Azure] opslag {#configure-azure-storage}


![gegevensintegratie](assets/data-integeration.png)

[[!DNL Experience Manager Forms] Gegevensintegratie](data-integration.md) verstrekt een [!DNL Azure] opslagconfiguratie om formulieren te integreren met [!DNL Azure] opslagservices. Met FDM (Form Data Model) kunt u Adaptive Forms maken die interactief werkt met [!DNL Azure] server om bedrijfswerkstromen toe te laten. Bijvoorbeeld:

* Gegevens schrijven naar [!DNL Azure] op Aangepast formulier verzenden.
* Gegevens schrijven in [!DNL Azure] via aangepaste entiteiten die zijn gedefinieerd in het formuliergegevensmodel (FDM) en omgekeerd.
* Query [!DNL Azure] voor gegevens en vult Adaptive Forms vooraf in.
* Gegevens lezen van [!DNL Azure] server.

## Maken [!DNL Azure] opslagconfiguratie {#create-azure-storage-configuration}

Controleer voordat u deze stappen uitvoert of u een [!DNL Azure] opslagaccount en een toegangstoets om de toegang tot de [!DNL Azure] opslagaccount.

1. Navigeren naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Azure Storage]**.
1. Selecteer een map om de configuratie te maken en selecteer **[!UICONTROL Create]**.
1. Geef een titel voor de configuratie op in het dialoogvenster **[!UICONTROL Title]** veld.
1. Geef de naam van de [!DNL Azure] opslagaccount in de **[!UICONTROL Azure Storage Account]** veld.
1. Geef de sleutel op voor toegang tot Azure-opslagaccount in het dialoogvenster **[!UICONTROL Azure Access Key]** veld en selecteer **[!UICONTROL Save]**.

## Formuliergegevensmodel maken {#create-azure-form-data-model}

Na het maken van de [!DNL Azure] opslagconfiguratie, kunt u [Maak het formuliergegevensmodel](create-form-data-models.md). Geef de map op die de [!DNL Azure] in de **[!UICONTROL Data Source Configuration]** tijdens het maken van het formuliergegevensmodel (FDM). Vervolgens kunt u de configuratie selecteren in de lijst met configuraties in de opgegeven mapnaam.

### Toevoegen [!DNL Azure] services voor het formuliergegevensmodel {#add-azure-services}

Nadat u de objecten Form Data Model (FDM) en Data Model hebt gemaakt, kunt u [!DNL Azure] services voor het formuliergegevensmodel (FDM).

Toevoegen [!DNL Azure] diensten:

1. Selecteer in de modus Bewerken de services in het menu **[!UICONTROL Services]** in het linkerdeelvenster en selecteert u **[!UICONTROL Add Selected]**. De geselecteerde services worden weergegeven in het dialoogvenster **[!UICONTROL Services]** van het formuliergegevensmodel (FDM).

   ![Geselecteerde services toevoegen](assets/select-services.png)

1. In de **[!UICONTROL Services]** tabblad selecteert u de service en **[!UICONTROL Edit Properties]**. Definieer op basis van de service de invoer- of uitvoermodelobjecten voor de service.

1. Selecteren **[!UICONTROL Save]** om het formuliergegevensmodel (FDM) op te slaan.

   In de volgende tabel worden de beschikbare [!DNL Azure] diensten:

   <table>
    <tbody>
     <tr>
      <th><strong>Servicenaam</strong></th>
      <th><strong>Beschrijving</strong></th>
     </tr>
     <tr>
      <td>Get Blob from Azure</td>
      <td>Gegevens ophalen die zijn opgeslagen als een klob in Azure-opslag met een id of naam</td>
     </tr>
     <tr>
      <td>Get Blob met binaries URL van Azure</td>
      <td>Gegevens ophalen die zijn opgeslagen als een blob met URL voor binaire bestanden in Azure-opslag met een id of naam</td>
     </tr>
     <tr>
      <td>Blob opslaan in Azure</td>
      <td>Gebruik een blob-id om gegevens in Azure-opslag op te slaan</td>
     </tr>
     <tr>
      <td>Blob bijwerken in Azure</td>
      <td>Gebruik een blob-id om gegevens in Azure-opslag bij te werken</td>
     </tr>
     <tr>
      <td>Lijst met blob-id's ophalen uit Azure</td>
      <td>Haal een lijst met blob-id's uit Azure op basis van het nummer dat in de invoeraanvraag is gedefinieerd.</td>
     </tr>
     <tr>
      <td>SAS-URL's voor Blobs ophalen uit Azure</td>
      <td>Haal SAS-URL's voor Blobs op van Azure op basis van Blob-id's in de invoeraanvraag.</td>
     </tr>
     <tr>
      <td>Blob verwijderen uit Azure</td>
      <td>Gebruik een blob-id om gegevens uit Azure-opslag te verwijderen</td>
     </tr>
    </tbody>
   </table>

### Een objecteigenschap van een gegevensmodel definiëren als een zoeksleutel {#define-data-model-object-as-metadata}

Een objecteigenschap van een gegevensmodel definiëren als een zoeksleutel:

1. In de **[!UICONTROL Model]** tab, selecteert u de objecteigenschap van het gegevensmodel en selecteert u **[!UICONTROL Edit Properties]**.
1. Van de schakelaar **[!UICONTROL Search Key]** schakelt optie in op de status ON. Deze optie is alleen beschikbaar voor primaire gegevenstypen.
1. Selecteren **[!UICONTROL Done]** en selecteer vervolgens **[!UICONTROL Save]** om het formuliergegevensmodel op te slaan.

Nadat u objecteigenschappen van gegevensmodellen hebt gedefinieerd als zoeksleutels, worden de hashwaarden opgeslagen in Azure-indextags en in Base64-gecodeerde waarden worden opgeslagen in de Azure-metagegevens.

>[!NOTE]
>
>Per Azure-entiteit zijn slechts 10 zoeksleutels toegestaan, omdat Azure alleen 10 tags per Blob toestaat en de waarde van eigenschappen die is gemarkeerd als zoeksleutels na hashing wordt opgeslagen in Azure-indextags.

<!--

>[!MORELIKETHIS]
>
>* [Configure data sources for AEM Forms](/help/forms/configure-data-sources.md)
>* [Integrate Microsoft Dynamics 365 and Salesforce with Adaptive Forms](/help/forms/configure-msdynamics-salesforce.md)
>  [Add Forms Portal to an AEM Sites page](/help/forms/configure-forms-portal.md)

-->