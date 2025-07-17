---
title: HTML5-formulieren optimaliseren
description: U kunt de uitvoergrootte van de HTML5-formulieren optimaliseren.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: bdb9edc2-6a37-4d3f-97d5-0fc5664316be
feature: HTML5 Forms,Mobile Forms
exl-id: 14309ebd-8d00-4ca5-b4ab-44d80d97d066
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: 22aeedaaf4171ad295199a989e659b6bf5ce9834
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 0%

---

# HTML5-formulieren optimaliseren {#optimizing-html-forms}

<span class="preview"> De HTML5 Forms-functionaliteit wordt aangeboden als onderdeel van het programma voor vroege toegang. Als u toegang wilt aanvragen, stuurt u een e-mail van uw officiële (werk)e-mailadres naar aem-forms-ea@adobe.com.
</span>

HTML5-formulieren genereren formulieren in de HTML5-indeling. De resulterende uitvoer kan groot zijn, afhankelijk van factoren zoals de formuliergrootte en afbeeldingen in het formulier. Om de gegevensoverdracht te optimaliseren, is de geadviseerde benadering de reactie van HTML te comprimeren gebruikend de Server van het Web waarvan het verzoek wordt gediend. Deze benadering vermindert de reactiegrootte, het netwerkverkeer, en de tijd die wordt vereist om gegevens tussen de server en cliëntmachines te stromen.

Dit artikel beschrijft de stappen die worden vereist om compressie voor de Server 2.0 met 32 bits van het Web van Apache, met JBoss toe te laten.

>[!NOTE]
>
>De volgende instructies zijn niet van toepassing op andere servers dan Apache Web Server 2.0 32 bits.

Vraag de Apache-webserversoftware aan die op uw besturingssysteem van toepassing is:

* Voor Windows downloadt u de Apache-webserver van de Apache HTTP Server-projectsite.
* Download voor Solaris 64-bits de Apache-webserver van de website Sunfreeware for Solaris.
* Voor Linux wordt de Apache-webserver vooraf geïnstalleerd op een Linux-systeem.

Apache kan communiceren met JBoss via HTTP of het AJP-protocol.

1. Uncomment de volgende moduleconfiguraties in het *APACHE_HOME/conf/httpd.conf* dossier.

   ```java
   LoadModule proxy_balancer_module modules/mod_proxy.so
   LoadModule proxy_balancer_module modules/mod_proxy_http.so
   LoadModule deflate_module modules/mod_deflate.so
   ```

   >[!NOTE]
   >
   >Voor Linux is de standaard APACHE_HOME-map /etc/httpd/.

1. Configureer de proxy op poort 8080 van JBoss.

   Voeg de volgende configuratie aan het *APACHE_HOME/conf/httpd.conf* configuratiedossier toe.

   ```java
   ProxyPass / https://<server_Name>:8080/
   ProxyPassReverse / https://<server_Name>:8080/
   ```

   >[!NOTE]
   >
   >Wanneer u een volmacht gebruikt, worden de volgende configuratieveranderingen vereist:
   >
   >* Toegang: *https://&lt;server>:&lt;port>/system/console/configMgr*
   >* De configuratie voor het filter Apache Sling Reference bewerken
   >* Voeg in de sectie Hosts toestaan de vermelding voor de proxyserver toe

1. Compressie inschakelen.

   Voeg de volgende configuratie aan het *APACHE_HOME/conf/httpd.conf* configuratiedossier toe.

   ```xml
   <Location /content/xfaforms>
     <IfModule mod_deflate.c>
        SetOutputFilter DEFLATE
        # Don't compress
        SetEnvIfNoCase Request_URI \.(?:gif|jpe?g|png)$ no-gzip dont-vary
        SetEnvIfNoCase Request_URI \.(?:exe|t?gz|zip|bz2|sit|rar)$ no-gzip dont-vary
       #Dealing with proxy servers
   
        <IfModule mod_headers.c>
           Header append Vary User-Agent
        </IfModule>
     </IfModule>
   </Location>
   ```

1. Om tot de server van AEM toegang te hebben, gebruik https://[ Apache_server ]:80.
