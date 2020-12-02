---
title: Opmerkingen bij de release voor Cloud Manager in AEM als Cloud Service Release 2020.4.0
description: Opmerkingen bij de release voor Cloud Manager in AEM als Cloud Service Release 2020.4.0
translation-type: tm+mt
source-git-commit: ca690144a8254d5ffba354f0f96d9ef1c5202533
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---


# Opmerkingen bij de release voor Cloud Manager in Adobe Experience Manager als Cloud Service 2020.4.0 {#release-notes}

Deze pagina bevat de releaseopmerkingen voor Cloud Manager in AEM als Cloud Service 2020.4.0.

## Releasedatum {#release-date}

De releasedatum voor Cloud Manager in AEM als Cloud Service 2020.4.0 is 9 april 2020.

## Wat is er nieuw?{#whats-new-cloud-manager}

* De uitgever URLs zijn nu beschikbaar bij de pagina van het Milieu in de UI van de Manager van de Wolk.
* Wijzigingen in navigatie om gebruikers toe te staan een programma te bewerken, te schakelen of toe te voegen vanuit de overzichtspagina van Cloud Manager.
* Wijzigingen die gebruikers toestaan om programma te bewerken vanaf de landingspagina van de programmakaart op de landingspagina van Cloud Manager.
* Nieuwe pijpleidingsstatus **Pijpleiding die** tegen het milieu wordt getoond het met wordt geassocieerd.
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
* Experience Cloud-meldingen werden niet altijd ontvangen.

