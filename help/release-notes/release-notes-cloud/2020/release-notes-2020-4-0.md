---
title: Opmerkingen bij de release van Adobe Experience Manager as a Cloud Service voor 2020.4.0
description: "[!DNL Adobe Experience Manager] as a Cloud Service opmerkingen bij de release 2020.4.0."
exl-id: d98a3862-76fa-4b5b-b81a-333f5f532b67
source-git-commit: 9ceec0401b91bba2408bda89d4f2c486e2d51eec
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 0%

---

# Opmerkingen bij de release voor Adobe Experience Manager as a Cloud Service 2020.4.0 {#release-notes}

Deze pagina bevat de algemene opmerkingen voor de release [!DNL Experience Manager] as a Cloud Service 2020.4.0.

## Releasedatum {#release-date}

De releasedatum voor [!DNL Experience Manager] as a Cloud Service 2020.4.0 is 9 april 2020.

## Nieuwe functies in middelen {#assets}

Meer informatie over nieuwe functies, verbeteringen en foutoplossingen voor [!DNL Experience Manager Assets] en [!DNL Dynamic Media] in de huidige release.

* [Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html) biedt ondersteuning voor de gebruiksscenario&#39;s voor middelendistributie voor Experience Manager Assets. [!DNL Brand Portal] de organisaties van hulp om aan hun marketing behoeften te voldoen door goedgekeurde merk en productactiva aan externe agentschappen, partners, interne teams, en wederverkopers voor download veilig te verdelen.
   * [!DNL Brand Portal] de configuratie is voltooid door [!DNL Adobe I/O] console. Zie [Brand Portal configureren](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/publish/configure-aem-assets-with-brand-portal.html).
   * Asset sourcing in [!DNL Brand Portal] wordt nog niet ondersteund met [!DNL Experience Manager] as a Cloud Service.

* [Adobe-itemkoppeling](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) v2.0 werkt met [!DNL Experience Manager] as a Cloud Service. [!DNL Adobe Asset Link] stroomlijnt de samenwerking tussen creatieve en marketingmedewerkers in het proces voor het maken van inhoud door verbinding te maken [!DNL Experience Manager Assets] with [!DNL Creative Cloud] bureaubladapps [!DNL Adobe Photoshop], [!DNL Adobe Illustrator], en [!DNL Adobe InDesign] via in-app [!DNL Asset Link] deelvenster.
   * [!DNL Experience Manager] is vooraf geconfigureerd voor [!DNL Adobe Asset Link], wat resulteert in [eenvoudige configuratie](https://helpx.adobe.com/enterprise/using/configure-aem-assets-for-asset-link.html) en snellere implementatie voor creatieve professionals.
   * [!DNL Asset Link] ondersteunt nu een [omgevingsschakelaar Experience Manager](https://helpx.adobe.com/enterprise/using/manage-assets-using-adobe-asset-link.html#UseAdobeAssetLink) waarmee creatieve gebruikers eenvoudig verbinding kunnen maken met een andere [!DNL Experience Manager] milieu. Een voorbeeld waar deze functionaliteit nuttig is, is voor ontwerpers van agentschappen die met meerdere clients werken die verschillende [!DNL Experience Manager Assets] implementaties.

* Gebruikers kunnen configureren [nabewerkingsworkflows](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows) automatisch starten in de map [!UICONTROL Properties] gebruikersinterface voor de specifieke omslaghiërarchieën.
   * De map [!UICONTROL Properties] gebruikersinterface is vereenvoudigd, met nieuwe [!UICONTROL Asset Processing] tabblad met metagegevensprofiel, verwerkingsprofiel en de nieuwe workflowconfiguratie voor automatisch opstarten.

     ![Verwerkingsprofielen kunnen eenvoudig worden toegepast op mappen en alle elementen die naar mappen zijn geüpload, worden verwerkt met deze profielen](/help/assets/assets/asset-processing-folder-properties.png)

   * Met de optie voor herverwerking van middelen kunt u een specifiek verwerkingsprofiel selecteren om door de gebruiker geselecteerde elementen in submappen opnieuw te verwerken.

     ![Geselecteerde elementen opnieuw verwerken met een specifiek verwerkingsprofiel](/help/assets/assets/fpo-existing-asset-reprocess.gif)

   * [!DNL Dynamic Media]: Toegevoegde selectieve publicatieconfiguratie zodat elementen automatisch worden gepubliceerd voor een beveiligde voorvertoning. Bovendien kunnen de activa uitdrukkelijk aan Experience Manager worden gepubliceerd zonder aan DMS7 voor levering in het openbare domein te publiceren.

### Opgeloste problemen {#assets-bug-fixes}

* Oplossingen voor problemen met middelenverwerking.
* Oplossingen in [!DNL Dynamic Media] configuratie en het publiceren van activa aan [!DNL Dynamic Media] leveringsservice.

>[!MORELIKETHIS]
>
>* [Over Adobe-itemkoppeling](https://www.adobe.com/creativecloud/business/enterprise/adobe-asset-link.html)
>* [Brand Portal configureren](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/publish/configure-aem-assets-with-brand-portal.html)
>* [Vorm Experience Manager om met de Verbinding van Activa te werken](https://helpx.adobe.com/enterprise/using/configure-aem-assets-for-asset-link.html)
>* [Workflow maken in Experience Manager met behulp van asset microservices](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/manage/asset-microservices-configure-and-use.html#post-processing-workflows)

## Nieuwe functies in Cloud Manager {#whats-new-cloud-manager}

* De uitgever URLs zijn nu beschikbaar bij de pagina van het Milieu in de UI van de Manager van de Wolk.
* Wijzigingen in navigatie om gebruikers toe te staan een programma te bewerken, te schakelen of toe te voegen vanuit de overzichtspagina van Cloud Manager.
* Wijzigingen die gebruikers toestaan om programma te bewerken vanaf de landingspagina van de programmakaart in Cloud Manager.
* Nieuwe pijpleidingsstatus **Pijpleiding loopt** worden weergegeven tegen de omgeving waaraan het is gekoppeld.
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
* Experience Cloud-meldingen werden niet altijd ontvangen.
