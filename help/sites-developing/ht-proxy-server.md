---
title: Verwendung des Proxy-Server-Tools
seo-title: How to use the Proxy Server Tool
description: Der Proxyserver fungiert als Zwischenserver, der Anforderungen zwischen einem Client und einem Server weiterleitet
seo-description: The proxy server acts as an intermediate server that relays requests between a client and a server
uuid: 30f4f46d-839e-4d23-a511-12f29b3cc8aa
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: development-tools
content-type: reference
discoiquuid: dfbc1d2f-80c1-4564-a01c-a5028b7257d7
exl-id: 63f3a172-b551-433a-aad5-58c6bfda82bb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '979'
ht-degree: 50%

---

# Verwendung des Proxy-Server-Tools{#how-to-use-the-proxy-server-tool}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Der Proxyserver fungiert als Zwischenserver, der Anforderungen zwischen einem Client und einem Server weiterleitet. Der Proxy-Server verfolgt alle Interaktionen zwischen Client und Server und gibt ein Protokoll der gesamten TCP-Kommunikation aus. Dadurch können Sie genau überwachen, was passiert, ohne auf den Hauptserver zugreifen zu müssen.

Den Proxyserver in Ihrer AEM-Installation finden Sie hier:

`crx-quickstart/opt/helpers/proxy-2.1.jar`

Sie können den Proxy-Server verwenden, um alle Interaktionen zwischen Client und Server unabhängig vom zugrunde liegenden Kommunikationsprotokoll zu überwachen. Sie können beispielsweise die folgenden Protokolle überwachen:

* HTTP für Webseiten
* HTTPS für sichere Webseiten
* SMTP für E-Mail-Nachrichten
* LDAP für die Benutzerverwaltung

Sie können den Proxyserver zum Beispiel zwischen zwei Anwendungen schalten, die über ein TCP/IP-Netzwerk kommunizieren, etwa einem Webbrowser und AEM. So können Sie genau überprüfen, was passiert, wenn Sie eine CQ-Seite anfragen.

## Starten des Proxyserver-Tools {#starting-the-proxy-server-tool}

Starten Sie den Server über die Befehlszeile:

`java -jar proxy-2.1.jar <host> <remoteport> <localport> [options]`

**Parameter**

`<host>`

Hierbei handelt es sich um die Hostadresse der CRX-Instanz, zu der Sie eine Verbindung aufbauen möchten. Wenn sich die Instanz auf Ihrem lokalen Computer befindet, lautet sie `localhost`.

`<remoteport>`

Hierbei handelt es sich um den Port der CRX-Zielinstanz. Der Standardport für eine neue AEM-Installation lautet zum Beispiel **`4502`** und der Standardport für eine neue AEM-Erstellungsinstanz `4502`.

`<localport>`

Dies ist der Port auf Ihrem lokalen Computer, zu dem Sie eine Verbindung aufbauen, um über den Proxy auf die CRX-Instanz zuzugreifen.

**Optionen**

`-q` (leiser Modus)

Die Ausgabe wird nicht in das Konsolenfenster geschrieben. Verwenden Sie dies, wenn Sie die Verbindung nicht verlangsamen möchten oder die Ausgabe in einer Datei protokollieren (siehe Option -logfile ).

`-b`(binärer Modus)

Wenn Sie nach bestimmten Byte-Kombinationen im Traffic suchen, aktivieren Sie den Binärmodus. Die Ausgabe enthält dann die Hexadezimal- und die Zeichenausgabe.

`-t` (Zeitstempel für Protokolleinträge)

Fügt jeder Protokollausgabe einen Zeitstempel hinzu. Der Zeitstempel wird in Sekunden angegeben, sodass er möglicherweise nicht für die Überprüfung einzelner Anforderungen geeignet ist. Verwenden Sie sie, um Ereignisse zu suchen, die zu einem bestimmten Zeitpunkt aufgetreten sind, wenn Sie den Proxyserver über einen längeren Zeitraum verwenden.

`-logfile <filename>` (Schreiben in Protokolldatei)

Schreibt die Konversation zwischen Client und Server in eine Protokolldatei. Dieser Parameter funktioniert auch im stillen Modus.

**`-i <numIndentions>`** (Einzug hinzufügen)

Jede aktive Verbindung wird für eine bessere Lesbarkeit eingerückt. Der Standardwert ist 16 Ebenen. Diese Funktion wurde mit `proxy.jar version 1.16` eingeführt.

### Protokollformat {#log-format}

Die von proxy-2.1.jar erstellten Protokolleinträge haben das folgende Format:

`[timestamp (optional)] [Client|Server]-[ConnectionNumber]-[BytePosition] ->[Character Stream]`

So kann eine Web-Seitenanfrage zum Beispiel wie folgt aussehen:

`C-0-#000000 -> [GET /author/prox.html?CFC_cK=1102938422341 HTTP/1.1 ]`

* „C“ gibt an, dass dieser Eintrag vom Client stammt (es handelt sich dabei um die Anfrage einer Web-Seite).
* 0 ist die Verbindungsnummer (der Verbindungszähler beginnt bei 0)
* #00000 ist der Versatz im Bytestream. Hierbei handelt es sich um den ersten Eintrag, weshalb der Versatz bei 0 ist.
* `[GET <?>]` ist der Inhalt der Anfrage, im Beispiel eine der HTTP-Kopfzeilen (URL).

Wenn eine Verbindung geschlossen wird, werden die folgenden Informationen protokolliert:

```
C-6-Finished: 758 bytes (1.0 kb/s)
S-6-Finished: 665 bytes (1.0 kb/s)
```

Hier werden die Anzahl der Bytes, die zwischen dem Client (`C`) und dem Server (`S`) bei der 6. Verbindung übertragen wurden, und die durchschnittliche Geschwindigkeit angegeben.

**Beispiel einer Protokollausgabe**

Stellen Sie sich als Beispiel eine Seite vor, die bei einer Anfrage den folgenden Code ausgibt:

### Beispiel {#example}

Betrachten Sie beispielsweise ein sehr einfaches HTML-Dokument, das sich im Repository unter

`/content/test.html`

befindet, zusammen mit einer Bilddatei unter

`/content/test.jpg`

Der Inhalt von `test.html` ist:

```xml
<html>
<head>
    <title>Test</title>
</head>  
<body>
    Test<br>
    <img src="test.jpg">
</body>
</html>
```

Wenn wir davon ausgehen, dass die AEM-Instanz auf `localhost:4502` ausgeführt wird, starten wir den Proxy wie folgt:

`java -jar proxy.jar localhost 4502 4444 -logfile test.log`

Auf die CQ-/CRX-Instanz kann nun über den Proxy unter `localhost:4444` zugegriffen werden und sämtliche Kommunikation über diesen Port wird im Protokoll `test.log` erfasst.

Wenn wir nun die Ausgabe des Proxys beobachten, sehen wir die Interaktion zwischen dem Browser und der AEM Instanz.

Beim Start gibt der Proxy Folgendes aus:

```xml
starting proxy for localhost:4502 on port 4444
using logfile: <some-dir>/crx-quickstart/opt/helpers/test.log
```

Wenn Sie anschließend einen Browser öffnen und auf die Testseite unter

`http://localhost:4444/content/test.html`

zugreifen, sehen Sie, dass der Browser eine `GET`-Anfrage für die folgende Seite tätigt:

```shell
C-0-#000000 -> [GET /content/test.html HTTP/1.1 ]
C-0-#000033 -> [Host: localhost:4444 ]
C-0-#000055 -> [Connection: keep-alive ]
C-0-#000079 -> [User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_7_4) AppleWebKit/536.11 (KHTML, like Gecko) Chrome/20.0.1132.57 Safari/536.11 ]
C-0-#000212 -> [Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8 ]
C-0-#000285 -> [Accept-Encoding: gzip,deflate,sdch ]
C-0-#000321 -> [Accept-Language: en-US,en;q=0.8 ]
C-0-#000354 -> [Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.3 ]
C-0-#000402 -> [Cookie: login-token=179ba6bd-e0a7-4909-a965-e11c7f2bc2fc%3a618bd8a8-fbaf-43c5-827d-c84c62248c5e_22ee860cc9036fee%3acrx.default%3b21148fb0-eb6c]
C-0-#000543 -> [-43c9-a2b9-c8d40618d8ae%3ad87a3d1a-5e9a-4d5a-bab1-0ee60ad6d8df_d0e4ddce0fcd84b6%3acrx.default%3b5cb95227-ea51-47bf-850b-68ad1dfd7297%3af3bbb6]
C-0-#000684 -> [59-7913-4285-8857-832c087bafd5_c484727d3b3665ad%3acrx.default; ys-cq-siteadmin-tree=o%3Awidth%3Dn%253A240%5EselectedPath%3Ds%253A/content ]
C-0-#000824 -> [ ]
```

Die AEM-Instanz antwortet mit den Inhalten der Datei `test.html`:

```shell
S-0-#000000 -> [HTTP/1.1 200 OK ]
S-0-#000017 -> [Connection: Keep-Alive ]
S-0-#000041 -> [Server: Day-Servlet-Engine/4.1.24  ]
S-0-#000077 -> [Content-Type: text/html;charset=utf-8 ]
S-0-#000116 -> [Content-Length: 104 ]
S-0-#000137 -> [Date: Mon, 16 Jul 2012 11:23:38 GMT ]
S-0-#000174 -> [Last-Modified: Mon, 16 Jul 2012 11:19:27 GMT ]
S-0-#000220 -> [ ]
S-0-#000222 -> [<html>]
S-0-#000229 -> [<head>]
S-0-#000236 -> [    <title>Test</title>]
S-0-#000260 -> [</head> ]
S-0-#000269 -> [<body>]
S-0-#000276 -> [ Test<br>]
S-0-#000286 -> [    <img src="test.jpg">]
S-0-#000311 -> [</body>]
S-0-#000319 -> [</html>]
```

### Verwendung des Proxy-Servers {#uses-of-the-proxy-server}

Die folgenden Szenarien veranschaulichen einige der Zwecke, für die der Proxy-Server verwendet werden kann:

**Suchen nach Cookies und ihren Werten**

Das folgende Beispiel für einen Protokolleintrag zeigt alle Cookies und deren Werte, die vom Client bei der sechsten seit dem Start des Proxys geöffneten Verbindung gesendet werden:

`C-6-#000635 -> [Cookie: cq3session=7e39bc51-ac72-3f48-88a9-ed80dbac0693; Show=ShowMode; JSESSIONID=68d78874-cabf-9444-84a4-538d43f5064d ]`

**Überprüfen von Kopfzeilen und ihren Werten**

Das folgende Beispiel für einen Protokolleintrag zeigt, dass der Server eine Keep-Alive-Verbindung herstellen kann und der Header für die Inhaltslänge ordnungsgemäß festgelegt wurde:

```
S-7-#000017 -> [Connection: Keep-Alive ]
 ...
 S-7-#000107 -> [Content-Length: 124 ]
```

**Überprüfen der Funktionsfähigkeit von Keep-Alive**

Keep-Alive ist eine Funktion von HTTP, die es einem Client ermöglicht, eine TCP-Verbindung zum Server wiederzuverwenden, um mehrere Anfragen zu tätigen (für Seiten-Code, Bilder, Stylesheets usw.). Ohne Keep-Alive muss der Client für jede Anfrage eine neue Verbindung aufbauen.

So überprüfen Sie, ob Keep-Alive funktioniert:

* Starten Sie den Proxyserver.
* Fragen Sie eine Seite an.
* Wenn Keep-Alive funktioniert, sollte der Verbindungszähler nie über 5 bis 10 Verbindungen hinausgehen.
* Wenn Keep-Alive nicht funktioniert, steigt der Verbindungszähler schnell.

**Finden verlorener Anfragen**

Sollten Anfragen in einer komplexen Serverumgebung, zum Beispiel einer mit Firewall und Dispatcher, verloren gehen, können Sie den Proxyserver verwenden, um herauszufinden, wo die Anfrage verloren ging. Bei einer Firewall:

* Proxy vor einer Firewall starten
* Starten Sie einen weiteren Proxy nach einer Firewall.
* Verwenden Sie die Proxys, um herauszufinden, wie weit die Anfragen kommen.

**Hängende Anfragen**

Gehen Sie wie folgt vor, wenn gelegentlich hängende Anfragen auftreten:

* Starten Sie den Proxy.
* Warten oder schreiben Sie das Zugriffsprotokoll in eine Datei mit jedem Eintrag mit einem Zeitstempel.
* Wenn hängende Anfragen auftreten, können Sie sehen, wie viele Verbindungen offen waren und welche Anfrage dafür verantwortlich ist.
