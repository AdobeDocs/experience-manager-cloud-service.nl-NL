---
title: Markering
description: Begrijp hoe de redacteur van het Fragment van de Inhoud markeringssyntaxis gebruikt om u toe te staan om inhoud gemakkelijk tot stand te brengen, voor zowel pagina creatie als hoofdloze levering.
feature: Content Fragments
role: User
exl-id: 6fbf8128-3b7f-4eda-bbbd-3336578d2586
solution: Experience Manager Sites
source-git-commit: be60f0371e652549cec6e57d1449b6e07b996514
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 2%

---

# Markering {#markdown}

Wanneer u [&#x200B; de Fragmenten van de Inhoud creeert &#x200B;](/help/sites-cloud/administering/content-fragments/authoring.md#edit-multi-line-text-fields-plaintext-markdown) kunt u [&#x200B; Multiline tekstgebieden &#x200B;](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#data-types) hebben die met het **StandaardType** van **worden bepaald Markdown**. De redacteur van het Fragment van de Inhoud gebruikt *syntaxis van de prijsdaling* om u toe te staan om inhoud voor zowel pagina auteursrecht als hoofdloze levering gemakkelijk te schrijven:

![&#x200B; de Meerdere gebieden van de Prijsverhoging van de lijntekst in de redacteur &#x200B;](/help/sites-cloud/administering/content-fragments/assets/cf-markdown-field-edit.png)

U kunt het volgende definiëren:

* [Kop](/help/sites-cloud/administering/content-fragments/markdown.md#heading-notation)
* [Alinea&#39;s en regeleinden](/help/sites-cloud/administering/content-fragments/markdown.md#paragraphs-and-line-breaks)
* [Koppelingen](/help/sites-cloud/administering/content-fragments/markdown.md#links)
* [Afbeeldingen](/help/sites-cloud/administering/content-fragments/markdown.md#images)
* [Aanhalingstekens blokkeren](/help/sites-cloud/administering/content-fragments/markdown.md#block-quotes)
* [Lijsten](/help/sites-cloud/administering/content-fragments/markdown.md#lists)
* [Nadruk](/help/sites-cloud/administering/content-fragments/markdown.md#emphasis)
* [Codeblokken](/help/sites-cloud/administering/content-fragments/markdown.md#code-blocks)
* [Backslash-escapen](/help/sites-cloud/administering/content-fragments/markdown.md#backslash-escapes)

## Kop {#heading-notation}

Als u een koptekst wilt maken, plaatst u een hash-symbool (#) vóór de kop. Één knoeiboelsymbool (#) wijst op H1, twee knoeiboelsymbolen (##) voor H2 etc. U kunt maximaal zes hashsymbolen gebruiken. Bijvoorbeeld:

    `## This is an H2`

    `### This is an H3`

    `###### This is a H6`

U kunt desgewenst een H1 maken door de tekst in gelijke tekens te onderstrepen en een H2 te maken door de tekst in mintekens te onderstrepen. Bijvoorbeeld:

    `This is an H1`

    `=============`

    `This is an H2`

    `-------------`

## Alinea&#39;s en regeleinden {#paragraphs-and-line-breaks}

Een alinea is gewoon een of meer opeenvolgende tekstregels, gescheiden door een of meer lege regels. Een lege regel is een regel die alleen spaties of tabs bevat. Normale alinea&#39;s mogen niet met spaties of tabs worden ingesprongen.

Een regeleinde wordt gemaakt door een regel met twee of meer spaties te eindigen en een regeleinde.

## Koppelingen {#links}

U kunt inline-koppelingen en verwijzingskoppelingen maken.

In beide stijlen wordt de koppelingstekst gescheiden door vierkante haakjes `[]` .

Dit zijn voorbeelden van inlineverbindingen:

    `This is [an example](https://example.com/ "Title") inline link.`

    `This is [an example (non-standard) of an email link](emailto:myaddress@mydomain.info)`

    `[This link](https://example.net/) has no title attribute.`

Een verwijzingskoppeling heeft de volgende syntaxis:

    `Hey you should [checkout][0] this [cool thing][wiki] that I [made][].`

    `[0]: https://www.google.ca`

    `[wiki]: https://www.wikipedia.org`

    `[made]: https://www.stackoverflow.com`

## Afbeeldingen {#images}

De syntaxis voor afbeeldingen lijkt op die voor koppelingen. U kunt inline-afbeeldingen en afbeeldingen waarnaar wordt verwezen maken.

Een inline-afbeelding heeft bijvoorbeeld de volgende syntaxis:

    `![Alt text](/path/to/img.jpg)`

    `![Alt text](/path/to/img.jpg "Optional title")`

De syntaxis bevat:

* Een uitroepteken: !;
* gevolgd door een set vierkante haakjes die de tekst van het alt-kenmerk voor de afbeelding bevat;
* gevolgd door een reeks haakjes, die de URL of het pad naar de afbeelding bevatten, en een optioneel titelkenmerk dat tussen dubbele of enkele aanhalingstekens staat.

Een afbeelding in de stijl Referentie heeft de volgende syntaxis:

    `![Alt text][id]`

Waarbij &quot;id&quot; de naam van een gedefinieerde afbeeldingsverwijzing is. Verwijzingen naar afbeeldingen worden gedefinieerd met dezelfde syntaxis als verwijzingen naar koppelingen:

    `[id]: url/to/image "Optional title attribute"`

## Aanhalingstekens blokkeren {#block-quotes}

U kunt tekst aanhalen door het symbool > vóór de tekst toe te voegen. Bijvoorbeeld:

    `>This is block quotes`

U kunt geneste blokaanhalingstekens hebben. Bijvoorbeeld:

    `> This is the first level of quoting.`

    `>`

        `>> This is a nested blockquote.`

    `>`

    `> Back to the first level.`

## Lijsten {#lists}

U kunt zowel geordende als ongeordende lijsten maken.

Als u een ongeordende lijst wilt maken, gebruikt u het symbool &ast; (sterretje) vóór de items in de lijst. Bijvoorbeeld:

    `* item in list`

    `* item in list`

    `* item in list`

Als u een geordende lijst wilt maken, voegt u de nummers toe, gevolgd door een punt, vóór elk item in de lijst. Bijvoorbeeld:

    `1. First item in list.`

    `2. Second item in list.`

    `3. Third item in list.`

## Nadruk {#emphasis}

U kunt cursieve of vette opmaak toevoegen aan uw tekst.

U kunt als volgt cursief maken:

    `*single asterisks*`

    `_single underscores_`

    `Keyboard shortcut: Ctrl-I (Cmd-I)`

U kunt tekst als volgt vet maken:

    `**double asterisks**`

    `__double underscores__`

    `Keyboard shortcut: Ctrl-B (Cmd-B)`

Als u een bereik van code wilt aangeven, plaatst u de code tussen aanhalingstekens (&grave;). In tegenstelling tot een vooraf opgemaakt codeblok geeft een codebereik code binnen een normale alinea aan.

Bijvoorbeeld:

    ``Use the `printf()` function.``

## Codeblokken {#code-blocks}

Codeblokken worden doorgaans gebruikt om broncode te illustreren. U kunt codeblokken maken door de code in te springen met een tab of een minimum van 4 spaties. Bijvoorbeeld:

    `This is a normal paragraph.`

        `This is a code block.`

## Backslash-escapen {#backslash-escapes}

U kunt backslash-escapes gebruiken om letterlijke tekens te genereren die ook een speciale betekenis hebben in de opmaaksyntaxis. Als u bijvoorbeeld een woord met letterlijke sterretjes wilt omringen (in plaats van een HTML &lt;em>-tag), kunt u als volgt backslashes vóór de sterretjes gebruiken:

    `\\*literal asterisks\\*`

Backslash-escapes zijn beschikbaar voor de volgende tekens:

    ` \ backslash`

    `` ` backtick``

    ` * asterisk`

    ` _ underscore`

    ` {} curly braces`

    ` [] square brackets`

    ` () parentheses`

    ` # hash mark`

    ` + plus sign`

    ` - minus sign (hyphen)`

    ` . dot`
