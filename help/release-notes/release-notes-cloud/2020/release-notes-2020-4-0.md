---
title: Opmerkingen bij de release van Adobe Experience Manager as a Cloud Service voor 2020.4.0
description: "[!DNL Adobe Experience Manager] as a Cloud Service opmerkingen bij de release voor 2020.4.0."
exl-id: d98a3862-76fa-4b5b-b81a-333f5f532b67
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '608'
ht-degree: 0%

---

# Opmerkingen bij de release voor Adobe Experience Manager as a Cloud Service 2020.4.0 {#release-notes}

Deze pagina bevat een overzicht van de algemene opmerkingen bij de release voor [!DNL Experience Manager] as a Cloud Service 2020.4.0.

## Releasedatum {#release-date}

De releasedatum voor [!DNL Experience Manager] as a Cloud Service 2020.4.0 is 9 april 2020.

## Nieuwe functies in Assets {#assets}

Meer informatie over nieuwe functies, verbeteringen en foutoplossingen voor [!DNL Experience Manager Assets] en [!DNL Dynamic Media] in de huidige release.

* [ Brand Portal ](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html?lang=nl-NL) steunt de het gebruiksgevallen van de activadistributie voor Experience Manager Assets. [!DNL Brand Portal] helpt organisaties om aan hun marketingbehoeften te voldoen door goedgekeurde merk- en productmiddelen veilig te distribueren aan externe agentschappen, partners, interne teams en wederverkopers voor downloaden.
   * [!DNL Brand Portal] -configuratie is voltooid via [!DNL Adobe I/O] -console. Zie [ vormen Brand Portal ](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/publish/configure-aem-assets-with-brand-portal.html?lang=nl-NL).
   * Asset sourcing in [!DNL Brand Portal] wordt nog niet ondersteund bij [!DNL Experience Manager] as a Cloud Service.

* [&#128279;](https://helpx.adobe.com/nl/enterprise/using/adobe-asset-link.html) v2.0 van de Verbinding van Activa van de Adobe 0&rbrace; werkt met [!DNL Experience Manager] as a Cloud Service.  [!DNL Adobe Asset Link] stroomlijnt de samenwerking tussen ontwerpers en marketers bij het maken van inhoud door [!DNL Experience Manager Assets] te verbinden met [!DNL Creative Cloud] bureaubladapps [!DNL Adobe Photoshop] , [!DNL Adobe Illustrator] en [!DNL Adobe InDesign] via het deelvenster in-app [!DNL Asset Link] .
   * [!DNL Experience Manager] wordt pre-gevormd voor [!DNL Adobe Asset Link], wat in [ gemakkelijke configuratie ](https://helpx.adobe.com/nl/enterprise/using/configure-aem-assets-for-asset-link.html) en snellere uitrol aan creatieve beroeps resulteert.
   * [!DNL Asset Link] steunt nu een [ omgevingsschakelaar van de Experience Manager ](https://helpx.adobe.com/nl/enterprise/using/manage-assets-using-adobe-asset-link.html#UseAdobeAssetLink) die creatieve gebruikers toestaat om met een verschillend [!DNL Experience Manager] milieu gemakkelijk te verbinden. Een voorbeeld waar deze functionaliteit nuttig is, is voor ontwerpers van agentschappen die met meerdere clients werken die verschillende [!DNL Experience Manager Assets] -implementaties gebruiken.

* De gebruikers kunnen [ post-verwerkings werkschema&#39;s ](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows) vormen aan auto-begin in het omslag [!UICONTROL Properties] gebruikersinterface voor de specifieke omslaghiërarchieën.
   * De gebruikersinterface van de map [!UICONTROL Properties] wordt vereenvoudigd, waarbij het nieuwe tabblad [!UICONTROL Asset Processing] het metagegevensprofiel, het verwerkingsprofiel en de nieuwe workflowconfiguratie voor automatisch opstarten bevat.

     ![ de profielen van de Verwerking kunnen gemakkelijk op omslagen worden toegepast en alle activa die aan omslagen worden geupload verwerken gebruikend deze profielen ](/help/assets/assets/asset-processing-folder-properties.png)

   * Met de optie voor herverwerking van middelen kunt u een specifiek verwerkingsprofiel selecteren om door de gebruiker geselecteerde elementen in submappen opnieuw te verwerken.

     ![ opnieuw verwerkend geselecteerde activa gebruikend een specifiek verwerkingsprofiel ](/help/assets/assets/fpo-existing-asset-reprocess.gif)

   * [!DNL Dynamic Media]: Toegevoegde selectieve publicatieconfiguratie zodat elementen automatisch worden gepubliceerd voor een beveiligde voorvertoning. Bovendien kunnen de activa uitdrukkelijk aan Experience Manager worden gepubliceerd zonder aan DMS7 voor levering in het openbare domein te publiceren.

### Opgeloste problemen {#assets-bug-fixes}

* Oplossingen voor problemen met middelenverwerking.
* Oplossingen in [!DNL Dynamic Media] configuratie en het publiceren van elementen naar [!DNL Dynamic Media] leveringsservice.

>[!MORELIKETHIS]
>
>* [ Ongeveer de Verbinding van Activa van de Adobe ](https://www.adobe.com/creativecloud/business/enterprise/adobe-asset-link.html)
>* [ vorm Brand Portal ](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/publish/configure-aem-assets-with-brand-portal.html?lang=nl-NL)
>* [ vorm Experience Manager om met de Verbinding van Activa te werken ](https://helpx.adobe.com/nl/enterprise/using/configure-aem-assets-for-asset-link.html)
>* [ creeer werkschema in Experience Manager gebruikend activa microservices ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/manage/asset-microservices-configure-and-use.html?lang=nl-NL#post-processing-workflows)

## Nieuwe functies in Cloud Manager {#whats-new-cloud-manager}

* De uitgever URLs zijn nu beschikbaar bij de pagina van het Milieu in de UI van Cloud Manager.
* Wijzigingen in navigatie om gebruikers toe te staan een programma te bewerken, te schakelen of toe te voegen vanaf de overzichtspagina van Cloud Manager.
* Wijzigingen die gebruikers toestaan om programma te bewerken vanaf de programmakaart op de Cloud Manager-landingspagina.
* De nieuwe pijpleidingsstatus **die** in werking stelt tegen het milieu wordt het geassocieerd met.
* Verbeteringen om de pagina van de pijpleidingsuitvoering begrijpelijk te maken. Dit omvat vertoning van de naam van de Pijpleiding (niet productiepijplijn slechts) en type, en een badge om erop te wijzen of is de pijpleidingsstatus Bezig/Geannuleerd/Ontbroken.
* Knopinfo om de gebruikerservaring en de begrijpelijkheid te verbeteren rond de vraag waarom de knop Programma/omgeving toevoegen is uitgeschakeld.
* Mislukte omgevingen kunnen nu worden verwijderd via de interface en API.
* Het proces dat wordt gebruikt om de wachtwoorden van de it te produceren is veerkrachtiger gemaakt aan kwesties in de onderliggende de dienstlaag.

### Opgeloste problemen {#bug-fixes-cloud-manager}

* De verbindingen aan het werkgebiedmilieu op de de detailpagina van de pijpleidingsuitvoering navigeerden niet constant aan de correcte plaats.
* Individuele stappen in het proces voor het maken van een omgeving worden eerder dan nodig uitgesteld, waardoor het proces mislukt.
* De Gemaakt configuratie die in de bouwstijlcontainer wordt gebruikt werd bijgewerkt om imaturen te vermijden toen het downloaden van artefactmeta-gegevens.
* In sommige gevallen, zou de stap van het Beeld van de Bouwstijl er niet in slagen om klantenpakketten met succes te downloaden.
* Bepaalde omstandigheden die zich niet vaak voordoen, verhinderen dat omgevingen worden verwijderd.
* Experiencen Cloud werden niet consequent gemeld.
