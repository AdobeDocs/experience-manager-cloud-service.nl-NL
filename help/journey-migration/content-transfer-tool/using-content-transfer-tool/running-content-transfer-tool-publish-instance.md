---
title: Het gereedschap Inhoud overbrengen uitvoeren op een publicatie-instantie
description: Het gereedschap Inhoud overbrengen uitvoeren op een publicatie-instantie
exl-id: 01faab94-a939-4004-b094-e9eb8f67b96e
feature: Migration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 0%

---

# Het gereedschap Inhoud overbrengen uitvoeren op een publicatie-instantie {#run-content-transfer-tool-publish-instance}

## Inleiding {#introduction}

Met het gereedschap Inhoud overbrengen (CTT) kunt u geen inhoudanalyse uitvoeren voordat u inhoud van de broninstantie naar de doelinstantie overbrengt. CTT maakt bijvoorbeeld geen onderscheid tussen gepubliceerde en niet-gepubliceerde inhoud wanneer inhoud wordt ingesloten in een publicatieomgeving. De inhoud die in de migratieset wordt opgegeven, wordt in de gekozen doelinstantie opgenomen. De gebruiker heeft de capaciteit om een migratie in te voeren die in een instantie Auteur of Publish of beide wordt geplaatst.

>[!NOTE]
>Het is raadzaam om tijdens het verplaatsen van inhoud naar een instantie Production Content Transfer Tool te installeren op de instantie source Author om inhoud naar de instantie target Author te verplaatsen en op dezelfde manier Content Transfer Tool op de instantie source Publish te installeren om inhoud naar de instantie target Publish te verplaatsen. Zie [Aanbevolen aanpak](#recommended-approach) zie hieronder voor meer informatie .

## Aanbevolen aanpak {#recommended-approach}

Volg de onderstaande aanbevolen aanpak:

* Gebruik dezelfde versie van het gereedschap Inhoud overbrengen die ook voor de instantie Auteur is gebruikt.

* Er mag slechts één publicatieknooppunt worden gemigreerd. Deze moet uit het taakverdelingsmechanisme worden verwijderd voordat de extractie wordt gestart.

* Tijdens het publiceren wordt de publicatielaag niet verkleind (in tegenstelling tot de auteur).

  >[!IMPORTANT]
  >Als voorzorgsmaatregel, vermijd om het even welke gebruiker in werking gestelde schrijven verrichtingen, zoals:
  > * Distributie van inhoud van AEM as a Cloud Service auteur naar Publiceren in die omgeving
  > * Gebruikerssynchronisatie tussen publicatie-instanties
