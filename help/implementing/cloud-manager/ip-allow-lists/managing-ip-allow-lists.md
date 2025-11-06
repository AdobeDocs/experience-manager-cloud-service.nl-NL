---
title: IP-Lijsten van gewenste personen beheren
description: Leer hoe te om, de status van IP Lijsten van gewenste personen in Cloud Manager te bekijken uit te geven te schrappen en te controleren.
exl-id: 6efabe53-3f45-47d4-ac1f-979cae0ab33e
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 0%

---

# IP-Lijsten van gewenste personen beheren {#manage-ip-allow-lists}

Leer hoe te om, de status van IP Lijsten van gewenste personen in Cloud Manager te bekijken uit te geven te schrappen en te controleren.

## IP-Lijsten van gewenste personen weergeven en bijwerken {#update-ip-allow-lists}

Een gebruiker in de **BedrijfsEigenaar** of **rol van de Manager van de Plaatsing** kan deze stappen volgen en een IP Lijst van gewenste personen bijwerken.

**om IP Lijsten van gewenste personen te bekijken en bij te werken:**

1. Logon aan Cloud Manager bij [&#x200B; my.cloudmanager.adobe.com &#x200B;](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie en het programma.
1. Van de **pagina van het Overzicht**, in het linkerzijmenu, onder **Diensten**, klik ![&#x200B; het pictogram van de de lijstlijst van de Taak &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_TaskList_18_N.svg) **IP Lijsten van gewenste personen**.
1. Identificeer de rij voor de IP Lijsten van gewenste personen die u wilt bekijken of bijwerken.
1. Klik ![&#x200B; Meer pictogram &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) bij het rechtereind van de rij.
1. Van het drop-down menu, klik **Mening &amp; Update**.
De **Mening &amp; van de Update IP de dialoogdoos van de Lijst van gewenste personen** toont de naam, IP adressen (of waaiers) die de regel samen met de milieu&#39;s en de diensten bepalen waarop de regel wordt toegepast.
1. Wijzig desgewenst de naam of het IP-adres.

   Het toevoegen van of het verwijderen van een nieuwe IP waaier aan een IP Lijst van gewenste personen past automatisch het op alle overeenkomstige milieu/de diensten toe waarop het eerder werd toegepast.

   De updates kunnen niet aan een IP Lijst van gewenste personen worden gemaakt terwijl een vroegere update lopend is en niet is voltooid.

1. Klik **Update**.

## Controleer het statuut van IP Lijsten van gewenste personen {#check-allow-list-status}

1. Logon aan Cloud Manager bij [&#x200B; my.cloudmanager.adobe.com &#x200B;](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie en het programma.

1. Van de **pagina van het Overzicht**, in het linkerzijmenu, onder **Diensten**, klik ![&#x200B; het pictogram van de de lijstlijst van de Taak &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_TaskList_18_N.svg) **IP Lijsten van gewenste personen**.

1. In de **kolom van de Status** van de IP lijst van Lijsten van gewenste personen, bewaar de muiswijzer over een IP Lijst van gewenste personen die (in gebruik) groen is om één of meerdere diensten te zien die op het worden toegepast.

   De statuswaarden in de tabel hebben de volgende betekenis:

   | Status van IP Lijst van gewenste personen | Beschrijving |
   | --- | --- |
   | Toegepast | De IP Lijst van gewenste personen wordt met succes toegepast op één of meerdere milieu&#39;s. |
   | Bijwerken | Er wordt een update van de IP-Lijst van gewenste personen uitgevoerd, die een of meer toepassingen of het niet toepassen van de lijst kan omvatten. Elke toepassing/niet-toepassing is vermeld samen met zijn eigen status van **niet begonnen**, **Bezig**, **Volledig**, of **Ontbroken**. |
   | Mislukt | Een of meer toepassings- of verwijderingsproces van een update is mislukt.<br>・ Elke toepassing en toepassing wordt samen met de status vermeld.<br>・ De status is **Ontbroken** als één toepassing/unapplication in de update ontbreekt. De status blijft als **Ontbroken** tot alle mislukkingen worden ontruimd.<br>・ Klik **opnieuw** pictogram naast de status zodat kunt u de mislukking ontruimen.<br>・ U kunt geen IP Lijst van gewenste personen met a **Ontbroken** status bijwerken of schrappen. |
   | Verwijderen | Een schrapping van een IP Lijst van gewenste personen is lopend.<br>・ Bij verwijderen wordt de lijst uit alle services verwijderd.<br>・ Elke unapplication is vermeld samen met zijn eigen status van **niet Begonnen**, **Bezig**, **Volledig**, of **Ontbroken**.<br>・ Wanneer de schrappingsverrichting volledig is, verschijnt de IP Lijst van gewenste personen niet in de IP lijst van de Lijst van gewenste personen. Ook, wordt de IP Lijst van gewenste personen niet toegepast op om het even welke dienst in het programma in Cloud Manager. |
   | Verwijderen is mislukt | Een of meer toepassingen zijn tijdens het verwijderen mislukt.<br>・ Elke unapplication is vermeld samen met de status **Volledig** of **Ontbroken**.<br>・ De status wordt **Ontbroken Schrapping** als één unapplication ontbreekt. De status blijft als **Ontbroken Schrapping** tot alle mislukkingen worden ontruimd. Helemaal rechts van de lijstrij, klik ![&#x200B; Meer pictogram &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg), dan in het drop-down menu, klik **Schrapping** om het even welke mislukking te ontruimen.<br>・ U kunt geen IP Lijst van gewenste personen bijwerken terwijl de status **Ontbroken** is. |

## Een IP-Lijst van gewenste personen verwijderen {#delete-allow-list}

Wanneer u een IP Lijst van gewenste personen schrapt, maakt het automatisch de lijst van alle diensten ongedaan en schrapt het van de IP lijst van de Lijst van gewenste personen.

Een gebruiker in de **BedrijfsEigenaar** of **rol van de Manager van de Plaatsing** kan deze stappen volgen en een IP Lijst van gewenste personen bijwerken.

**om een IP Lijst van gewenste personen te schrappen:**

1. Logon aan Cloud Manager bij [&#x200B; my.cloudmanager.adobe.com &#x200B;](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie en het programma.
1. Van de **pagina van het Overzicht**, in het linkerzijmenu, onder **Diensten**, klik ![&#x200B; het pictogram van de de lijstlijst van de Taak &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_TaskList_18_N.svg) **IP Lijsten van gewenste personen**.
1. Identificeer de rij voor de IP Lijst van gewenste personen die u wilt schrappen, dan klik ![&#x200B; Meer pictogram &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) bij het rechtereind van de rij, dan klik **Schrapping**.
1. In het **schrapt IP de dialoogvakje van de Lijst van gewenste personen**, klik **Schrapping**.

## Bestaande CDN-configuraties {#pre-existing-cdn}

Als u een reeds bestaande configuratie CDN (het Netwerk van de Levering van de Inhoud) voor uw IP Lijsten van gewenste personen hebt, is er een informatief bericht op de **IP Lijst van gewenste personen** pagina. Het bericht moedigt u aan om deze configuraties als gebruikersinterface toe te voegen zodat zijn zij zichtbaar en configureerbaar in Cloud Manager.

Het bericht verdwijnt zodra alle bestaande omgevingsconfiguraties zijn gemigreerd met de interface. Het kan 1-2 werkdagen duren voordat het bericht verdwijnt.

Zie [&#x200B; een IP Lijst van gewenste personen &#x200B;](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md) voor meer details toevoegen.

Een gelijkaardig bericht wordt ook verstrekt op de **SSL Certificaten** en de **milieu&#39;s** pagina&#39;s voor milieu&#39;s die reeds bestaande configuraties CDN voor SSL certificaten of de namen van het douanedomein hebben.
