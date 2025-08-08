---
title: Een Edge Delivery-site configureren voor het gebruik van een externe Git-opslagplaats
description: Leer hoe u een Edge Delivery-site koppelt aan een particuliere of zakelijke Git-opslagplaats.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 87650caea6eb907093f0f327f1dbc19641098e4a
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---


# Een Edge Delivery-site configureren voor het gebruik van een externe Git-opslagplaats

U kunt uw Edge Delivery-site zo configureren dat code wordt opgehaald uit elke privéopslagplaats die al in Cloud Manager is geregistreerd.

**de Ondersteunde Leveranciers van het Git**

| Ondersteuningsniveau | Leveranciers | Notities |
| --- | --- | --- |
| Algemene beschikbaarheid | ・ De Onderneming van GitHub (zelf-ontvangen versie) <br>・ Bitbucket (de versie van de Wolk) <br>・ GitLab (Cloud en zelf-ontvangen versie) | Verbinding maken zonder inschakelen |
| Alpha programma | Azure DevOps (cloudversie) | [ Toegang van het Verzoek ](mailto:grp-cloudmanager_byog@adobe.com) |
| Beta programma | Door Adobe gehoste opslagplaats (gemaakt in Cloud Manager) | [ Toegang van het Verzoek ](mailto:grp-cloudmanager_byog@adobe.com) |

**om een plaats van Edge Delivery te vormen om een externe bewaarplaats van het Git te gebruiken:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer het aangewezen programma.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma met gevormde Edge Delivery Services, waar u een plaats van Edge Delivery wilt vormen om een externe reactie van de it te gebruiken.

1. In het linkerspoor, onder de **rubriek van het Programma**, klik **![pictogram van het Overzicht ](/help/implementing/cloud-manager/edge-delivery/assets/overview.svg) Overzicht**.

1. Voor de **pagina van het Overzicht van het 0&rbrace; Programma, klik** Edge Delivery **tabel.**

1. In de **plaatsen van Edge Delivery** lijst, klik ![ Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) aan het eind van een rij waarvan plaats u wilt vormen om een externe repo te gebruiken, dan **uw eigen Git** brengen.

1. In Breng uw eigen de dialoogvakje van het Git, in de **drop-down lijst van de Naam van de Bewaarplaats**, kies een repo van de Git met `READY` status, dan klik **bevestigen**.

   Cloud Manager retourneert een eenmalig geheim token. Als u de site opnieuw configureert, genereert Cloud Manager een nieuw geheim token.

1. Kopieer het teken en voeg het de plaatsconfiguratie in **helix-admin** toe, zoals die in de [ gids van de Git van BYO ](https://www.aem.live/developer/byo-git) wordt beschreven.

1. Terug in Cloud Manager, klik ![ Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) aan het eind van een rij de waarvan plaats u enkel vormde om een externe reactie te gebruiken, dan **de code van de Synchronisatie** te klikken.

1. Kies de tak aan synchronisatie, en klik **Synchronisatie**.

Elke commit op om het even welke tak teweegbrengt nu een automatische synchronisatie. Het gebruik **code van de Synchronisatie** opnieuw wanneer een volledige handsynchronisatie wordt vereist.

