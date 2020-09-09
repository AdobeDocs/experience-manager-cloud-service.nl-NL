---
title: Omgevingen beheren - Cloud Service
description: Omgevingen beheren - Cloud Service
translation-type: tm+mt
source-git-commit: 3768474b41abe76ee639e51c9eae39d72ab7c4a4
workflow-type: tm+mt
source-wordcount: '790'
ht-degree: 7%

---


# Omgevingen beheren {#manage-environments}

In de volgende sectie worden de typen omgeving beschreven die een gebruiker kan maken en hoe de gebruiker een omgeving kan maken.

## Omgevingstypen {#environment-types}

Een gebruiker met de vereiste toestemmingen kan de volgende milieutypes (binnen de grenzen van wat aan de specifieke huurder beschikbaar is) tot stand brengen.

* **Productie- en Stage-omgeving**:
De productie en het werkgebied zijn beschikbaar als duo en worden gebruikt voor test- en productiedoeleinden.

* **Ontwikkeling**: Een ontwikkelomgeving kan worden gecreëerd voor ontwikkelings- en testdoeleinden en zal alleen worden geassocieerd met niet-productiepijpleidingen.

   >[!NOTE]
   >Een ontwikkelomgeving die automatisch in een Sandbox-programma wordt gemaakt, wordt geconfigureerd om de oplossingen Sites en Assets te bevatten.

   De volgende tabel geeft een overzicht van de typen omgeving en hun kenmerken:

   | Naam | Auteurlaag | Lijst publiceren | Gebruiker kan maken | Gebruiker kan | Pijpleiding die in verband kan worden gebracht met het milieu |
   |--- |--- |--- |--- |---|---|
   | Productie | Ja | Ja als sites zijn opgenomen | Ja | Nee | Productiepijpleiding |
   | Werkgebied | Ja | Ja als sites zijn opgenomen | Ja | Nee | Productiepijpleiding |
   | Ontwikkeling | Ja | Ja als sites zijn opgenomen | Ja | Ja | Niet-productiepijpleiding |

   >[!NOTE]
   >De productie en het werkgebied zijn beschikbaar als duo en worden gebruikt voor test- en productiedoeleinden.  De gebruiker kan niet alleen een werkgebied of alleen een productieomgeving maken.

## Een omgeving toevoegen {#adding-environments}


1. Klik op **Omgeving** toevoegen om een omgeving toe te voegen. Deze knop is toegankelijk via het scherm **Omgevingen** .
   ![](assets/environments-tab.png)

   De optie **Omgeving** toevoegen is ook beschikbaar op de **milieukeuren** wanneer het programma geen omgevingen bevat.

   ![](assets/no-environments.png)

   >[!NOTE]
   >De optie Omgeving **** toevoegen wordt uitgeschakeld bij gebrek aan machtigingen of bij een eventuele overeenkomst.

1. Het dialoogvenster **Omgeving toevoegen** wordt weergegeven. De gebruiker moet details verzenden zoals het **Omgevingstype**, de **Naam van de omgeving** en de **Beschrijving van de omgeving** (afhankelijk van de doelstelling van de gebruiker bij het creëren van de omgeving binnen de grenzen van wat beschikbaar is voor de specifieke tenant).

   ![](assets/add-environment2.png)

   >[!NOTE]
   >Bij het maken van een omgeving worden een of meer *integraties* gemaakt in Adobe I/O. Deze zijn zichtbaar voor klanten die toegang hebben tot de I/O-console van Adobe en mogen niet worden verwijderd. Dit wordt in de beschrijving in de I/O-console van Adobe gedisclastreerd.

   ![](assets/add-environment-image1.png)

1. Klik op **Opslaan** om een omgeving met de ingevulde criteria toe te voegen.  Nu toont het *scherm van het Overzicht* de kaart van waar u opstelling uw pijpleiding kunt.

   >[!NOTE]
   >Als, u nog niet opstelling uw niet productiepijplijn hebt, toont het *scherm van het Overzicht* de kaart van waar u uw niet productiepijplijn kunt tot stand brengen.

## Omgeving bijwerken {#updating-dev-environment}

Updates van werkgebied- en productieomgevingen worden automatisch door Adobe beheerd.

Updates voor ontwikkelomgevingen worden beheerd door gebruikers van het programma. Wanneer een omgeving niet de meest recente openbaar beschikbare AEM-release uitvoert, wordt in de status op Environment Card op het Homescherm de **UPDATE-BESCHIKBAAR** weergegeven.

![](assets/update-environ-1.png)


De optie **Bijwerken** is beschikbaar via de **Omgevingskaart** .
Deze optie is ook beschikbaar als u op **Details** van de kaart van **Milieu** klikt. De pagina **Omgevingen** wordt geopend en wanneer u de ontwikkelomgeving hebt geselecteerd, klikt u op **...** en selecteer **Update**, zoals aangetoond in hieronder figuur:

![](assets/environments-screen-update.png)

Het selecteren van deze optie zal een Manager van de Plaatsing toestaan om de pijpleiding verbonden aan dit milieu aan de recentste versie bij te werken en dan de pijpleiding uit te voeren.

Als de pijpleiding reeds is bijgewerkt, wordt de gebruiker ertoe aangezet om de pijpleiding uit te voeren.

## Omgeving verwijderen {#deleting-environment}

De gebruiker met de vereiste toestemmingen zal een milieu van de Ontwikkeling kunnen schrappen.

De optie **Verwijderen** is beschikbaar in het vervolgkeuzemenu van de **milieucaart** . Klik op **...** voor een ontwikkelomgeving die u wilt verwijderen.

![](assets/environ-delete.png)

De optie Verwijderen is ook beschikbaar als u op **Details** klikt op de kaart **Omgevingen** . De pagina **Omgevingen** wordt geopend en wanneer u de ontwikkelomgeving hebt geselecteerd, klikt u op **...** en selecteer **Verwijderen**, zoals in onderstaande afbeelding wordt getoond:

![](assets/environ-delete-2.png)


>[!NOTE]
Deze functie is niet beschikbaar voor de omgeving Productie/Werkgebied die is ingesteld in een regulier programma dat is ingesteld voor productiedoeleinden. De functie is echter beschikbaar voor Productie-/Stage-omgevingen in een Sandbox-programma.

## Toegang beheren {#managing-access}

Selecteer Toegang **** beheren in het vervolgkeuzemenu in de **milieucaart** . U kunt rechtstreeks naar de instantie van de auteur navigeren en de toegang voor uw omgeving beheren.

Zie Toegang [beheren tot instantie](/help/onboarding/getting-access-to-aem-in-cloud/navigation.md#manage-access-aem) Auteur voor meer informatie.

![](assets/environ-manage-access.png)


## Developer Console openen {#accessing-developer-console}

Selecteer **Developer Console** in het vervolgkeuzemenu in de **Environment** Card. Hiermee wordt een nieuw tabblad in uw browser geopend met de aanmeldingspagina naar de **Developer Console**.

Alleen gebruikers met de rol Developer hebben toegang tot de **Developer Console**. De uitzondering voor Sandbox-programma&#39;s, waar gebruikers met toegang tot het Sandbox-programma van Cloud Manager toegang hebben tot de **Developer Console**.

Raadpleeg de [Sluimerende en Shibernating Sandbox-omgevingen](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/sandbox-programs.html#hibernating-introduction) voor meer informatie.


![](assets/environ-dev-console.png)

Deze optie is ook beschikbaar als u op **Details** van de kaart van **Milieu** klikt. De pagina **Omgevingen** wordt geopend en wanneer u een omgeving selecteert, klikt u op **...** en selecteer **Developer Console**.

