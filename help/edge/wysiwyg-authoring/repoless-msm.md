---
title: Meerdeloos beheer van sites
description: Leer beste praktijkaanbevelingen over hoe te opstelling een project met meertalige plaatsen die één enkele codebasis op een repoless manier gebruiken.
feature: Edge Delivery Services
role: Admin, Architect, Developer
source-git-commit: 02957fb8671d953a683ebd6e168979b11ad391c4
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---


# Meerdeloos beheer van sites {#repoless-msm}

In dit document wordt ervan uitgegaan dat u al een basissite hebt gemaakt voor uw project met de naam `my-aem-site` en dat u de site wilt lokaliseren met AEM MSM-functie.

Als u uw project reeds voor het repoless gebruiksgeval hebt opgezet, wordt de wolkenconfiguratie toegewezen op het niveau van de wortelpagina, `/content/my-aem-site`. Voor meertalige sites moet deze configuratietoewijzing worden gewijzigd in de hoofdmap van de taal, zoals `/content/my-aem-site/language-master/de` .

