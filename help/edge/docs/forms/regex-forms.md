---
title: AEM Forms Edge Delivery Services gebruikt vaak regex-expressies voor validatie van formuliervelden
description: AEM Forms Edge Delivery Services gebruikt vaak regex-expressies voor validatie van formuliervelden
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: 53a66eac5ca49183221a1d61b825401d4645859e
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---


# Algemeen gebruikte regex-expressies voor validaties

Hier volgen enkele reguliere expressies waarmee u formuliervalidatie kunt verbeteren die verder gaat dan wat moderne browsers bieden:

## Sterk wachtwoord

```regex
^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$
```

Zorgt voor ten minste 8 tekens met:

* Kleine letter (a-z)
* Hoofdletter (A-Z)
* Cijfer (0-9)
* Speciaal teken (@$!%*?&amp;)


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


## Tijd (UU:MM)

```regex
^([01][0-9]|2[0-3]):[0-5][0-9]$
```

Hiermee worden tijden gevalideerd in de notatie HH:MM (24-uursnotatie).


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
