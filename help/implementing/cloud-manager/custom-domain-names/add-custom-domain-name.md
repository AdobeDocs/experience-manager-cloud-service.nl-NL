---
title: Een aangepaste domeinnaam toevoegen
description: Leer hoe u een aangepaste domeinnaam kunt toevoegen met Cloud Manager.
exl-id: 0fc427b9-560f-4f6e-ac57-32cdf09ec623
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 4a369104ea8394989149541ee1a7b956383c8f12
workflow-type: tm+mt
source-wordcount: '702'
ht-degree: 0%

---


# Een aangepaste domeinnaam toevoegen {#adding-cdn}

Leer hoe u een aangepaste domeinnaam kunt toevoegen met Cloud Manager.

## Vereisten {#requirements}

Voldoe aan deze vereisten voordat u een aangepaste domeinnaam in Cloud Manager toevoegt.

* U moet een domeinSSL certificaat voor het domein hebben toegevoegd u wenst toe te voegen alvorens een naam van het douanedomein toe te voegen zoals die in het document [ wordt beschreven Toevoegend een SSL Certificaat ](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md).
* U moet de **BedrijfsEigenaar** of **rol van de Manager van de Plaatsing** hebben om een naam van het douanedomein in Cloud Manager toe te voegen.
* Gebruik de snelste CDN.

## Waar kunt u aangepaste domeinnamen toevoegen {#where}

U kunt een aangepaste domeinnaam vanuit twee locaties in Cloud Manager toevoegen:

* [Via de pagina Domeininstellingen](#adding-cdn-settings)
* [Van de pagina Milieu&#39;s](#adding-cdn-environments)

Wanneer u een aangepaste domeinnaam toevoegt, wordt het domein gediend met het meest specifieke, geldige certificaat. Als meerdere certificaten hetzelfde domein hebben, wordt de meest recente bijgewerkte versie gekozen. Adobe raadt u aan certificaten zodanig te beheren dat er geen overlappende domeinen zijn.

De stappen die in dit document worden beschreven, zijn gebaseerd op Snelheid. Als u een verschillende CDN gebruikte, vorm uw domein met CDN u aan gebruik hebt gekozen.

## Een aangepaste domeinnaam toevoegen via de pagina Domeininstellingen {#adding-cdn-settings}

Volg deze stappen om een naam van het douanedomein van de **pagina van de Montages van het Domein** toe te voegen.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma.

1. Navigeer aan het uitgezochte **lusje van de Montages van het Domein** in het linkernavigatievenster.

   ![ het venster van de Montages van het Domein ](/help/implementing/cloud-manager/assets/cdn/cdn-create.png)

1. Klik **voeg de knoop van het Domein** bij top-right toe om **te openen voeg de dialoog van de Naam van het Domein** toe.

   ![ voeg de dialoogdoos van het Domein toe ](/help/implementing/cloud-manager/assets/cdn/add-cdn1.png)

1. Op het **lusje van de Naam van het Domein**, ga de naam van het douanedomein op het **3} gebied van de Naam van het Domein in.**

   >[!NOTE]
   >
   >Neem geen `http://`, `https://` of spaties op wanneer u een domein betreedt.

1. Selecteer het **Milieu** de waarvan dienst met de domeinnaam wordt geassocieerd.

1. Selecteer of de **Publish** of **Voorproef** dienst.

1. Selecteer het **SSL van het Domein Certificaat** verbonden aan de domeinnaam van drop-down en selecteer **ga** verder.

1. Het **lusje van de Verificatie** verschijnt.

   ![ de naamcontrole van het Domein ](/help/implementing/cloud-manager/assets/cdn/cdn-create6.png)

   * Het **lusje van de Verificatie** beschrijft de volgende stappen om uw naam van het douanedomein te vormen, die een noodzakelijk TXT- verslag creeert.
   * U kunt deze stap onmiddellijk doen (alvorens **te klikken creeert** in de dialoogdoos) of nadat u **klikt creeer** in de dialoogdoos.
   * De opties en volgende stappen worden hieronder beschreven.

1. Klik **creëren** om de naam van het douanedomein in Cloud Manager te bewaren.

Wanneer u **selecteert creeer** in **voeg de tovenaar van het Domein van de Douane** toe, brengt Cloud Manager een TXT controle teweeg. Maak de TXT-record wanneer u de aangepaste domeinnaam in Cloud Manager instelt. Deze stap is echter niet vereist. Voor verdere controles, moet u actief selecteren **verifieer opnieuw** pictogram naast de status.

De naam is pas actief nadat Cloud Manager heeft gecontroleerd of het TXT-item is toegevoegd en geverifieerd. De status van **Verified en Geïmporteerde** wijst op een succesvolle TXT controle.

* Zie [ een verslag van TXT ](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) toevoegen om meer over verslagen te leren TXT.
* Zie [ de status van de domeinnaam van de Controle ](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) voor meer details op hoe Cloud Manager de naam van het douanedomein en zijn ingang TXT verifieert.

## Volgende stappen {#next-steps}

Nadat u uw aangepaste domeinnaam in Cloud Manager hebt gemaakt, voegt u een TXT-item toe om te controleren of het domein eigendom is. Ga aan het document [ te werk Toevoegend een Verslag TXT ](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) om vestiging uw naam van het douanedomein voort te zetten.

## Een aangepaste domeinnaam toevoegen op de pagina Environment {#adding-cdn-environments}

De stappen om een naam van het douanedomein van de **pagina van Milieu&#39;s** toe te voegen zijn het zelfde als wanneer [ toevoegend een naam van het douanedomein van de pagina van de Montages van het Domein ](#adding-cdn-settings), maar het ingangspunt verschilt. Volg deze stappen om een naam van het douanedomein van de **pagina van Milieu&#39;s** toe te voegen.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Navigeer aan de **pagina van het Detail van Milieu** voor het milieu van belang.

   ![ die domeinnaam op de pagina van de Details van het Milieu ingaan ](/help/implementing/cloud-manager/assets/cdn/cdn-create4.png)

1. Gebruik de **lijst van de Namen van het Domein** om de naam van het douanedomein voor te leggen.

   1. Voer de aangepaste domeinnaam in.
   1. Selecteer het SSL-certificaat dat aan deze naam is gekoppeld in de vervolgkeuzelijst.
   1. Klik **+ toevoegen**.

   ![ voeg een naam van het douanedomein toe ](/help/implementing/cloud-manager/assets/cdn/cdn-create3.png)

1. **voegt domeinnaam** dialoogdoos toe opent aan de **Naam van het Domein** tabel. Ga zoals u voor [ verder toevoegend een naam van het douanedomein van de pagina van de Montages van het Domein ](#adding-cdn-settings).
