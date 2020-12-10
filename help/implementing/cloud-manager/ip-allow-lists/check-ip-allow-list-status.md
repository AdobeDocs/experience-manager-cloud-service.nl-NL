---
title: Status van IP-Lijst van gewenste personen controleren
description: Status van IP-Lijst van gewenste personen controleren
translation-type: tm+mt
source-git-commit: 4245bbad81327ffdba9c400a36a03d815e2ebdc7
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---


# Status IP-Lijst van gewenste personen {#check-allow-list-status} controleren

Volg de stappen hieronder om de status van updates aan uw IP Lijst van gewenste personen te bepalen:

1. Klik op het pictogram van de Status voor de IP Lijst van gewenste personen van de lijst van het **scherm van Milieu** en selecteer **IP Lijsten van gewenste personen** pagina.

1. Cloud Manager geeft een van de volgende statussen weer, zoals vermeld in de onderstaande sectie.

## Status van een IP Lijst van gewenste personen {#status}

Hier volgen de definities van status die in een IP-Lijst van gewenste personen worden weergegeven:

* **Toegepast**: IP de Lijst van gewenste personen wordt met succes toegepast op milieu&#39;s.  De omgevingen en service zijn zichtbaar zoals in de onderstaande afbeelding wordt getoond.

* **Bijwerken**: Er wordt een update van de IP-Lijst van gewenste personen uitgevoerd die een of meer van toepassing zijn of ongedaan maken. Elke toepassing toepassen en ongedaan maken wordt vermeld samen met Niet gestart/Bezig/Voltooid of Niet uitgevoerd.

* **Mislukt**: Een of meer toegepaste of verwijderde processen in een update zijn mislukt. Elke Toepassen en Toepassen ongedaan maken wordt samen met Voltooid of Mislukt weergegeven.
   * De status is mislukt, zelfs als een toepassing wordt toegepast of ongedaan wordt gemaakt in de update.
   * De status blijft Mislukt totdat alle fouten zijn gewist. De gebruiker moet het pictogram Opnieuw proberen naast de status selecteren om de fout te ontruimen.
   * De gebruiker zal geen IP Lijst van gewenste personen kunnen bijwerken of schrappen terwijl de status Ontbroken is.

* **Verwijderen**: Aanvraag verwijderen is bezig. Dit betekent dat alle services niet van toepassing zijn. Elke Unapply wordt vermeld samen met Niet begonnen/Bezig/Voltooid of Mislukt.
Zodra de verrichting van de Schrapping wordt voltooid, zal de IP Lijst van gewenste personen:
   * Niet meer weergegeven in de tabel IP-Lijst van gewenste personen * Niet meer toegepast op een service in het programma in Cloud Manager

* **Verwijderen is mislukt**: Een of meer verwijderingsprocessen in een verwijderbewerking zijn mislukt. Elke Unapply zal samen met Volledige of Ontbroken worden vermeld.

   * De status Verwijderen is mislukt, zelfs als de toepassing ongedaan wordt gemaakt.
   * De status blijft Verwijderen mislukt totdat alle fouten zijn gewist. Gebruiker moet Verwijderen selecteren in **..** menu uiterst rechts van de rij in de lijst om het even welke mislukking te ontruimen.
   * De gebruiker zal niet toestaan om IP Lijst van gewenste personen bij te werken terwijl de status Ontbroken is.

