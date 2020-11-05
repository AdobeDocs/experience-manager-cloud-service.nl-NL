---
title: Een aangepaste domeinnaam toevoegen
description: Een aangepaste domeinnaam toevoegen
translation-type: tm+mt
source-git-commit: b6b1ef8f97413dc8bf9b1fa7f355a02bdaeebfd8
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---


# Een aangepaste domeinnaam toevoegen {#adding-cdn}

Een gebruiker moet een Business Owner of Deployment Manager zijn om een aangepaste domeinnaam in Cloud Manager te kunnen toevoegen.

>[!NOTE]
>Voordat u een aangepaste domeinnaam kunt toevoegen, moet u een geldig SSL-certificaat met de aangepaste domeinnaam op uw programma installeren. Zie Een SSL-certificaat installeren (INSERT LINK) voor meer informatie.

Er kan slechts één domeinnaam tegelijk worden toegevoegd. Gebruikers kunnen echter jokertekens toevoegen, bijvoorbeeld `*.wknd.com` als een domeinnaam, zodat meerdere subdomeinen kunnen worden gehost met één TXT-record.
Elke Cloud Manager-omgeving kan maximaal 50 aangepaste domeinen per omgeving hosten.
Dezelfde domeinnaam kan niet op meer dan één omgeving worden gebruikt.

## Een aangepaste domeinnaam toevoegen vanaf de pagina Domeininstellingen {#adding-cdn-settings}

Voer de onderstaande stappen uit om een aangepaste domeinnaam toe te voegen van de pagina Domeininstellingen:

1. Navigeer van de Pagina van Milieu&#39;s aan de pagina van Montages van het Domein.

1. Selecteer Aangepaste domeinnaam toevoegen. Hiermee wordt de wizard Aangepaste domeinnaam toevoegen INSERT IMAGE gestart

1. Voer de aangepaste domeinnaam in. Opmerking: Neem &#39;http://&#39;, &#39;https://&#39;&#39; of spaties niet op wanneer u een domein betreedt.

1. Selecteer het milieu waarvan de Publish dienst met de domeinnaam zal worden geassocieerd.

1. Selecteer het SSL-certificaat in de keuzelijst en selecteer Doorgaan.

1. Dit zal u aan de Verificatie van de Naam van het Domein voor uw scherm van het Milieu nemen. Ga naar TXT-record toevoegen voor meer informatie. AFBEELDING INVOEGEN

Volg de instructies die worden gegeven om domeineigendom voor uw milieu te bewijzen:

1. Selecteer Doorgaan.
1. Voor CDN-implementatie is een geldig SSL-certificaat en een geslaagde TXT-verificatie vereist. Dit wordt aangegeven met de status &quot;Verified and Deployed&quot;.  AFBEELDING INVOEGEN
1. Ga naar het Controleren van de Verbinding van het TUSSENVOEGSEL van de Status van de Naam van het Domein van de Douane om meer over diverse statussen en te leren hoe te om te richten.

>[!NOTE]
>DNS het bewijs kan tot een paar uren aan erkenning, wegens DNS propagatievertragingen vergen. Cloud Manager controleert het eigendom en werkt de status bij die in de tabel met domeininstellingen kan worden weergegeven. Ga naar de KOPPELING Domeinnaamstatus controleren voor meer informatie.

## Een aangepaste domeinnaam uit de pagina Omgevingen toevoegen {#adding-cdn-environments}

1. Navigeer naar de pagina Omgevingsdetails voor de omgeving die u wilt gebruiken.
1. Gebruik de invoervelden boven aan de tabel Domeinnamen om de aangepaste domeinnaam SSL-certificaat in te dienen. Selecteer vervolgens Toevoegen.
1. Hiermee wordt de wizard Aangepaste domeinnaam toevoegen gestart, waarbij de naam van de omgeving vooraf is ingevuld.
1. Voer de aangepaste domeinnaam in. Opmerking: Neem geen `http://`, `https://`of spaties op bij het invoeren in uw domein. Selecteer Doorgaan.
1. Dit zal u aan de Verificatie van de Naam van het Domein voor uw scherm van het Milieu nemen. Ga naar Domeinverificatie (TXT-record toevoegen) voor meer informatie. AFBEELDING INVOEGEN

Volg de instructies die worden gegeven om domeineigendom voor uw milieu te bewijzen:

1. Selecteer Doorgaan.
1. Voor CDN-implementatie is een geldig SSL-certificaat en een geslaagde TXT-verificatie vereist. Dit wordt aangegeven met de status &quot;Verified and Deployed&quot;.

Op dit punt is uw aangepaste domeinnaam klaar om te worden getest en kan de naam `CNAME` ernaar verwijzen. Ga naar de Status van de Naam van het Domein om meer over diverse statussen en te leren hoe te om te richten.

>[!NOTE]
>DNS het bewijs kan tot een paar uren aan erkenning, wegens DNS propagatievertragingen vergen. Cloud Manager controleert het eigendom en werkt de status bij die in de tabel met domeininstellingen kan worden weergegeven. Ga naar de KOPPELING Domeinnaamstatus controleren voor meer informatie.
