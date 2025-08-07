---
title: Edge Delivery Services for AEM Forms veelgebruikte regex-expressies voor validatie van formuliervelden
description: Edge Delivery Services for AEM Forms veelgebruikte regex-expressies voor validatie van formuliervelden
feature: Edge Delivery Services
role: User
hide: true
hidefromtoc: true
exl-id: 5cfe23bb-155f-4639-b7b7-5edc172ba92a
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 0%

---

# Algemeen gebruikte regex-expressies voor validaties

Hier volgen enkele reguliere expressies waarmee u formuliervalidatie kunt verbeteren die verder gaat dan wat moderne browsers bieden:

## Sterk wachtwoord

```regex
^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$
```

Zorgt voor ten minste 8 tekens met:

- Kleine letter (a-z)
- Hoofdletter (A-Z)
- Cijfer (0-9)
- Speciaal teken (@$!%*?&amp;)


## E-mailadres


```regex
^[a-zA-Z0-9.!#$%&'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:\.[a-zA-Z0-9-]+)*$
```

Hiermee worden letters, cijfers en speciale tekens in de gebruikersnaam en domeinnaam toegestaan.


## Telefoonnummer (Amerikaanse notatie)

```regex
^\(?([0-9]{3})\)?[-. ]([0-9]{3})[-. ]([0-9]{4})$
```

Hiermee valideert u telefoonnummers in de notatie (XXX) XXX-XXXX.



## URL

```regex
^(http|https)://.*$
```

Hiermee zorgt u voor een geldige URL die begint met http of https.



## Datum (JJJJ-MM-DD)

```regex
^\d{4}-(0[1-9]|1[0-2])-(0[1-9]|[12][0-9]|3[01])$
```

Valideert datums in de notatie JJJJ-MM-DD.


## Tijd (HH:MM)

```regex
^([01][0-9]|2[0-3]):[0-5][0-9]$
```

Valideert tijden in formaat HH :MM (24-uurformaat).


## Postcode (Amerikaanse notatie)

```regex
^\d{5}(?:[-\ ]\d{4})?$
```

Valideert Amerikaanse ZIP-codes van 5 cijfers met het optionele afbreekstreepje en de extensie 4 cijfers.


## Gebruikersnaam (alfanumeriek en onderstrepingsteken)

```regex
^[a-zA-Z0-9_]+$
```

Hiermee staat u letters, cijfers en onderstrepingstekens toe.


## Hexadecimale code kleur

```regex
^#[0-9a-fA-F]{6}$
```

Valideert hexadecimale 6-cijferige kleurcodes. Bijvoorbeeld #FFFFFF.


## IP-adres

```regex
^(25[0-5]|2[0-4][0-9]|1[0-9][0-9]|[0-9]{2,3})\.(25[0-5]|2[0-4][0-9]|1[0-9][0-9]|[0-9]{2,3})\.(25[0-5]|2[0-4][0-9]|1[0-9][0-9]|[0-9]{2,3})\.(25[0-5]|2[0-4][0-9]|1[0-9][0-9]|[0-9]{2,3})$
```

Valideert IPv4-adressen.



## Sociale-verzekeringsnummer (Amerikaanse notatie)

```regex
^\d{3}-\d{2}-\d{4}$
```



## Creditcardnummer

```regex
^(?:4[0-9]{12}(?:[0-9]{3})?|[25][1-7][0-9]{14}$
```

Hiermee valideert u telefoonnummers in de notatie (XXX) XXX-XXXX.



## Telefoonnummer (Amerikaanse notatie):

```regex
^[a-zA-Z0-9.!#$%&'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:\.[a-zA-Z0-9-]+)*$
```

Hiermee valideert u telefoonnummers in de notatie (XXX) XXX-XXXX.
