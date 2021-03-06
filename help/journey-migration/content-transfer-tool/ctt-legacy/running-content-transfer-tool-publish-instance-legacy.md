---
title: Het gereedschap Inhoud overbrengen uitvoeren op een instantie Publiceren (verouderd)
description: Het gereedschap Inhoud overbrengen uitvoeren op een publicatie-instantie
hide: true
hidefromtoc: true
source-git-commit: 1fb4d0f2a3b3f9a27f5ab1228ec2d419149e0764
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%

---

# Het gereedschap Inhoud overbrengen uitvoeren op een instantie Publiceren (verouderd) {#run-content-transfer-tool-publish-instance}

## Inleiding {#introduction}

Met het CTT-hulpprogramma (Content Transfer Tool) wordt geen inhoudanalyse uitgevoerd voordat inhoud van de broninstantie naar de doelinstantie wordt overgebracht. CTT maakt bijvoorbeeld geen onderscheid tussen gepubliceerde en niet-gepubliceerde inhoud wanneer inhoud wordt ingesloten in een publicatieomgeving. Alle inhoud die in de migratieset wordt opgegeven, wordt in de gekozen doelinstantie opgenomen. De gebruiker heeft de capaciteit om een migratie in te voeren die in een instantie Auteur of Publish of beide wordt geplaatst.

>[!NOTE]
>Het is raadzaam om tijdens het verplaatsen van inhoud naar een instantie Production Content Transfer Tool te installeren op de instantie source Author om inhoud naar de instantie target Author te verplaatsen en op dezelfde manier Content Transfer Tool op de instantie source Publish te installeren om inhoud naar de instantie target Publish te verplaatsen. Zie [Aanbevolen aanpak](#recommended-approach) voor meer informatie hieronder.

## Aanbevolen aanpak {#recommended-approach}

Volg de onderstaande aanbevolen aanpak:

* Gebruik dezelfde versie van het gereedschap Inhoud overbrengen die ook voor de instantie Auteur is gebruikt.

* Er hoeft slechts één publicatieknooppunt te worden gemigreerd. Deze moet uit het taakverdelingsmechanisme worden verwijderd voordat de extractie wordt gestart.

* Gebruik bij het maken van de migratieset de URL van de auteur AEM de as a Cloud Service omgeving.

* Tijdens het publiceren wordt de publicatielaag niet verkleind (in tegenstelling tot de auteur).

   >[!IMPORTANT]
   >Als voorzorgsmaatregel, gelieve te vermijden om het even welke gebruiker in werking gestelde schrijven verrichtingen, zoals:
   > * Distributie van inhoud van AEM as a Cloud Service auteur naar Publiceren in die omgeving
   > * Gebruikerssynchronisatie tussen publicatie-instanties

