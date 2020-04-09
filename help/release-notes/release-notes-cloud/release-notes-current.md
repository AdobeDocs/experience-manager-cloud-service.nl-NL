---
title: Opmerkingen bij de release Adobe Experience Manager als Cloud Service voor 2020.4.0
description: Opmerkingen bij de release Experience Manager voor 2020.4.0
translation-type: tm+mt
source-git-commit: 2258cc72d10fa85d89832b63016ccb393f453bff

---


# Release Notes for Adobe Experience Manager as a Cloud Service 2020.4.0 {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor [!DNL Experience Manager] als Cloud Service 2020.4.0 beschreven.

## Releasedatum {#release-date}

De releasedatum voor [!DNL Experience Manager] als cloudservice 2020.4.0 is 9 april 2020.

## Nieuwe functies in middelen {#assets}

Informatie over nieuwe functies, verbeteringen en foutoplossingen voor [!DNL Experience Manager Assets] [!DNL Dynamic Media] en in de huidige release.

* [Brand Portal](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/home.html) ondersteunt de praktijkvoorbeelden van middelendistributie voor Experience Manager-middelen. [!DNL Brand Portal] de organisaties van hulp om aan hun marketing behoeften te voldoen door goedgekeurde merk en productactiva aan externe agentschappen, partners, interne teams, en wederverkopers voor download veilig te verdelen.
   * [!DNL Brand Portal] configuratie wordt voltooid door [!DNL Adobe I/O] console.
   * Asset sourcing in [!DNL Brand Portal] wordt nog niet ondersteund met [!DNL Experience Manager] de Cloud Service.

* [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) v2.0 werkt met [!DNL Experience Manager] als cloudservice. [!DNL Adobe Asset Link] stroomlijnt de samenwerking tussen ontwerpers en marketers bij het maken van inhoud door verbinding te maken [!DNL Experience Manager Assets] met [!DNL Creative Cloud] bureaubladtoepassingen [!DNL Adobe Photoshop], [!DNL Adobe Illustrator]en [!DNL Adobe InDesign] via het [!DNL Asset Link] deelvenster in de app.
   * [!DNL Experience Manager] is vooraf geconfigureerd voor [!DNL Adobe Asset Link], wat resulteert in [eenvoudige configuratie](https://helpx.adobe.com/enterprise/using/configure-aem-assets-for-asset-link.html) en snellere implementatie voor creatieve professionals.
   * [!DNL Asset Link] ondersteunt nu een [Experience Manager-omgevingsswitch](https://helpx.adobe.com/enterprise/using/manage-assets-using-adobe-asset-link.html#UseAdobeAssetLink) waarmee creatieve gebruikers eenvoudig verbinding kunnen maken met een andere [!DNL Experience Manager] omgeving. Een voorbeeld waar deze functionaliteit nuttig is, is voor agentontwerpers die met veelvoudige cliënten werken gebruikend verschillende [!DNL Experience Manager Assets] plaatsingen.

* Gebruikers kunnen workflows [na](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows) verwerking zo configureren dat deze automatisch worden gestart in de gebruikersinterface [!UICONTROL Eigenschappen] van map voor de specifieke maphiërarchieën.
   * De gebruikersinterface [!UICONTROL Eigenschappen] van map is vereenvoudigd, met het nieuwe tabblad [!UICONTROL Asset Processing] met metagegevensprofiel, verwerkingsprofiel en de nieuwe workflowconfiguratie voor automatisch opstarten.
   * In het dialoogvenster voor het opwerken van bedrijfsmiddelen kunt u een specifiek verwerkingsprofiel selecteren en besluiten deze opnieuw in submappen te verwerken.
   * [!DNL Dynamic Media]: Toegevoegde selectieve publicatieconfiguratie zodat elementen automatisch worden gepubliceerd voor een beveiligde voorvertoning. Bovendien kunnen de elementen expliciet worden gepubliceerd naar Experience Manager zonder dat ze naar DMS7 worden gepubliceerd voor levering in het publieke domein.

### Opgeloste problemen {#assets-bug-fixes}

* Oplossingen voor problemen met de verwerking van bedrijfsmiddelen.
* Oplossingen in [!DNL Dynamic Media] configuratie en het publiceren activa aan de [!DNL Dynamic Media] leveringsdienst.

>[!MORELIKETHIS]
>
>* [Over Adobe Asset Link](https://www.adobe.com/creativecloud/business/enterprise/adobe-asset-link.html)
>* [Brand-portal configureren](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/publish/configure-aem-assets-with-brand-portal.html)
>* [Experience Manager configureren om te werken met Asset Link](https://helpx.adobe.com/enterprise/using/configure-aem-assets-for-asset-link.html)
>* [Workflow maken in Experience Manager met behulp van middelen microservices](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/assets/manage/asset-microservices-configure-and-use.html#post-processing-workflows)


## Nieuwe functies in Cloud Manager {#whats-new-cloud-manager}

* De uitgever URLs zijn nu beschikbaar bij de pagina van het Milieu in de UI van de Manager van de Wolk.
* Wijzigingen in navigatie om gebruikers toe te staan een programma te bewerken, te schakelen of toe te voegen vanuit de overzichtspagina van Cloud Manager.
* Wijzigingen die gebruikers toestaan om programma te bewerken vanaf de landingspagina van de programmakaart op de landingspagina van Cloud Manager.
* De nieuwe pijpleiding van de **Pijpleiding** die tegen het milieu wordt getoond het met wordt geassocieerd.
* Verbeteringen om de pagina van de pijpleidingsuitvoering begrijpelijk te maken. Dit omvat vertoning van de naam van de Pijpleiding (niet productiepijplijn slechts) en type, en een badge om erop te wijzen of is de pijpleidingsstatus Bezig/Geannuleerd/Ontbroken.
* Knopinfo om de gebruikerservaring en de begrijpelijkheid te verbeteren rond de vraag waarom de knop Programma/omgeving toevoegen is uitgeschakeld.
* Mislukte omgevingen kunnen nu worden verwijderd via de gebruikersinterface en de API.
* Het proces dat wordt gebruikt om de wachtwoorden van de it te produceren is veerkrachtiger gemaakt aan kwesties in de onderliggende de dienstlaag.

### Opgeloste problemen {#bug-fixes-cloud-manager}

* De verbindingen aan het werkgebiedmilieu op de de detailpagina van de pijpleidingsuitvoering navigeerden niet constant aan de correcte plaats.
* Individuele stappen in het proces voor het maken van een omgeving worden eerder dan nodig uitgesteld, waardoor het proces mislukt.
* De Gemaakt configuratie die in de bouwstijlcontainer wordt gebruikt werd bijgewerkt om imaturen te vermijden toen het downloaden van artefactmeta-gegevens.
* In sommige gevallen, zou de stap van het Beeld van de Bouwstijl er niet in slagen om klantenpakketten met succes te downloaden.
* Bepaalde omstandigheden die zich niet vaak voordoen, verhinderen dat omgevingen worden verwijderd.
* Experience Cloud-meldingen zijn niet altijd ontvangen.
