---
title: '''[!DNL Experience Manager Assets] integratie met [!DNL Adobe Workfront]'''
description: Inleiding tot integratie tussen [!DNL Assets] en [!DNL Workfront]
role: Admin,Leader,Architect
feature: Integrations
exl-id: 365de3dc-51db-4dcf-94e2-104b5a5d33a8
source-git-commit: 1a0718d317f13924cd4da273f9184b4f165bbc7e
workflow-type: tm+mt
source-wordcount: '955'
ht-degree: 1%

---

# [!DNL Adobe Experience Manager] als [!DNL Cloud Service] [!DNL Assets] integratie met [!DNL Adobe Workfront] {#assets-integration-overview}

[!DNL Adobe Workfront] is een werkbeheertoepassing waarmee u de volledige levenscyclus van het werk op één locatie kunt beheren. De integratie tussen [!DNL Workfront] en [!DNL Adobe Experience Manager Assets] kunnen organisaties de snelheid van de inhoud en de tijd-aan-markt verbeteren door het werk en het beheer van digitale activa intrinsiek met elkaar te verbinden. In het kader van het beheer van hun werk in Workfront hebben gebruikers toegang tot de vereiste documenten en afbeeldingen.

De [!DNL Workfront for Experience Manager enhanced connector] maakt verbeterde bedrijfsprocessen mogelijk met end-to-end workflows en biedt gepersonaliseerde end-to-end clientervaringen en centrale opslag. Adobe biedt een standaardaansluiting en een verbeterde aansluiting om de twee oplossingen te integreren. Zie de ondersteunde functies hieronder voor een vergelijking en zie [wat nieuw is in de [!DNL enhanced connector]](https://one.workfront.com/s/csh?context=2467&amp;pubname=the-new-workfront-experience).

[!DNL Workfront for Experience Manager enhanced connector] stelt uw organisatie in staat om:

* Maak automatisch gekoppelde mappen voor Experience Managers in Workfront en deel de mappen in op basis van Workfront-Portfolio, -programma&#39;s en -projecten.
* Metagegevens van Workfront-projecten synchroniseren met mappen voor gekoppelde Experience Managers.
* Metagegevens van de Experience Manager worden bijgewerkt met nieuwe versies.
* Stel Workfront-objectstatussen in op basis van configureerbare omstandigheden met behulp van workflows voor Experience Managers.
* Publiceer elementen naar de publicatieomgeving van de Experience Manager of naar Brand Portal.

Raadpleeg de platformondersteuning en [eerste vereisten voor de verbeterde aansluiting](https://one.workfront.com/s/csh?context=2467&amp;pubname=the-new-workfront-experience).

>[!IMPORTANT]
>
>* Adobe vereist plaatsing en configuratie van [!DNL Adobe Workfront for Experience Manager enhanced connector] alleen via gecertificeerde partners of [!DNL Adobe Professional Services]. Indien opgesteld en gevormd zonder een verklaarde partner of [!DNL Adobe Professional Services], wordt deze niet ondersteund door Adobe.
>
>* Adobe kan updates voor [!DNL Adobe Workfront] en [!DNL Adobe Experience Manager] die deze aansluiting overbodig maken; als dit voorkomt, kunnen de klanten worden vereist om van het gebruik van deze schakelaar over te gaan.
>
>* Adobe steunt verbeterde schakelaarversies 1.7.4 en hoger. Eerdere pre-release en aangepaste versies worden niet ondersteund. Zie stap 5(a) van [Uitgebreide installatie-instructies](workfront-connector-install.md).
>
>* Zie [Partnercertificatieexamen voor Workfront voor verbeterde connector voor Experience Manager Assets](https://solutionpartners.adobe.com/solution-partners/home/applications/experience_cloud/workfront/journey/dev_core.html). Voor informatie over het examen, [Handleiding voor Examen](https://express.adobe.com/page/Tc7Mq6zLbPFy8/).


## Verschillende integraties vergelijken tussen [!DNL Assets] en [!DNL Workfront] {#feature-parity-matrix}

Hieronder volgen de details van de functies die beschikbaar zijn via verschillende soorten integratie tussen [!DNL Assets] en [!DNL Workfront].

| Functie | Beschrijving | [!DNL Workfront] and [!DNL Assets Essentials] | [!DNL Workfront] for [!DNL Experience Manager] connector | [!DNL Workfront for Experience Manager enhanced connector] |
|----|----|----|------|-----|
| Implementatiemethoden | Geschikt voor [!DNL Assets] aanbieden. | Assets Essentials | Cloud Service, beheerde services van Adobe, op locatie | Cloud Service, beheerde services van Adobe, op locatie |
| Digitale bestanden verzenden vanuit [!DNL Workfront] tot [!DNL Assets] | De nieuwste versie van een WF-document kan worden geüpload naar AEM Assets, dat als een nieuwe versie van het document wordt gekoppeld. | ✓ | ✓ | ✓ |
| Mappen handmatig koppelen AEM aan Workfront-objecten | Bestaande AEM mappen kunnen worden gekoppeld als een Workfront-map en de onderliggende elementen ervan worden gekoppeld als nieuwe Workfront-documenten. | ✓ | ✓ | ✓ |
| Koppeling [!DNL Assets] naar Workfront-objecten | Bestaande elementen in AEM kunnen worden gekoppeld aan een nieuw Workfront-document of als een nieuwe versie van een bestaand document. | ✓ | ✓ | ✓ |
| Middelen die aan gekoppelde mappen worden toegevoegd, worden automatisch naar AEM verzonden | Als het document wordt toegevoegd aan een gekoppelde map, wordt het bijbehorende element automatisch geüpload naar AEM Assets als een nieuw element. | ✓ | ✓ | ✓ |
| Gekoppelde AEM Assets downloaden vanuit Workfront | Wanneer een element in Workfront is gekoppeld, kan de gebruiker de bytes van het element downloaden. | ✓ | ✓ | ✓ |
| Zoeken naar AEM Assets vanuit Workfront | Met de AEM Assets-kiezer in Workfront kunt u zoeken in volledige tekst naar elementen. | ✓ | ✓ | ✓ |
| AEM maphiërarchie weergeven en navigeren vanuit Workfront | Met de AEM Assets-kiezer in Workfront kan door de AEM Assets-hiërarchie worden gebladerd. Dit wordt beperkt door de toegangsbesturingselementen en machtigingen die de gebruiker in AEM heeft ingesteld. | ✓ | ✓ | ✓ |
| Middelen ontkoppelen van AEM Assets in Workfront | Een bestaand gekoppeld element van AEM kan worden losgekoppeld van het bijbehorende Workfront-document. Hierdoor wordt het oorspronkelijke element in AEM niet verwijderd. | ✓ | ✓ | ✓ |
| Nieuw versioned element toevoegen aan AEM Assets vanuit Workfront | Wanneer een nieuw toegevoegde versie aan een document in Workfront wordt toegevoegd, kan een gebruiker de nieuwe versie naar AEM sturen om de bestaande versie te vervangen. | ✓ | ✓ | ✓ |
| In Workfront gekoppelde middelen wanneer op Direct door gebruiker AEM wordt geklikt | Gebruikers worden doorgestuurd naar AEM om een voorvertoning van een gekoppeld element weer te geven vanuit Workfront. | ✓ | ✓ | Aangepast |
| Automatisch gekoppelde AEM mappen maken in Workfront | Maak automatisch gekoppelde AEM mappen in Workfront met objectstatussen. Organiseer automatisch AEM mappen op basis van Workfront-Portfolio, -programma&#39;s en -projecten. | Nee | Nee | ✓ |
| Commentaar synchroniseren | Automatisch opmerkingen synchroniseren voor elementen van [!DNL Workfront] tot [!DNL Assets] | Nee | ✓ | ✓ |
| Metagegevens Workfront-element toewijzen aan AEM Assets | Workfront-object en aangepaste formuliereigenschappen kunnen worden toegewezen aan AEM eigenschappen van metagegevens van elementen. Waarden worden geduwd op eerste upload/verbinding. | ✓ | ✓ | ✓ |
| Automatisch aangepaste Forms voor documenten maken in Workfront | Voeg aangepaste formulieren toe aan Workfront-documenten, -taken en -problemen met behulp van AEM workflows. | Nee | Voeg handmatig het aangepaste formulier toe en synchroniseer vervolgens automatisch | ✓ |
| Automatisch in twee richtingen bijwerken van metagegevens tussen AEM Assets en Workfront | Metagegevens automatisch bijwerken tussen AEM Assets en Workfront. | Nee | ✓ | ✓ |
| Workfront-metagegevens toewijzen aan AEM Assets-mappen | Metagegevens van Workfront-projecten synchroniseren met gekoppelde AEM. | Nee | Nee | ✓ |
| Metagegevensupdates AEM met nieuwe versies | U kunt een configuratie in AEM maken om te bepalen of een nieuw versioned element in Workfront ook wijzigingen in de metagegevens doorvoert. | Nee | Nee | ✓ |
| AEM metagegevens automatisch bijwerken bij wijzigingen in Aangepast Forms in Workfront | Workfront is zodanig geconfigureerd dat de opgegeven eigenschappen van metagegevens van AEM elementen worden toegewezen aan een aangepast document. Wanneer een element voor het eerst wordt gekoppeld of wanneer een element wordt bijgewerkt, worden de waarden van deze metagegevenseigenschappen gekopieerd naar het overeenkomstige aangepaste formulierveld van het Workfront-document. Er moet op worden toegezien dat de AEM niet naar AEM worden teruggestuurd alsof het een wijziging betreft die in Workfront is ontstaan. | Nee | ✓ | ✓ |
| Nieuwe proefversie maken op gekoppelde elementen | Na het koppelen van een element in Workfront kan automatisch een bewijs worden gegenereerd. | Nee | ✓ | Aangepast |
| Status instellen voor Workfront-objecten | Workfront-objectstatussen instellen op basis van configureerbare voorwaarden met behulp van AEM workflows | Nee | Nee | ✓ |
| Middelen publiceren naar AEM Publish Environment of Brand Portal | Workfront-gebruikers de optie geven om gekoppelde elementen automatisch te publiceren naar een AEM-publicatieomgeving of Brand Portal. | Nee | Nee | ✓ |
