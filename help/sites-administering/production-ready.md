---
title: Ausführung von AEM im produktionsbereiten Modus
seo-title: Running AEM in Production Ready Mode
description: Erfahren Sie, wie Sie AEM im produktionsbereiten Modus ausführen.
seo-description: Learn how to run AEM in Production Ready Mode.
uuid: f48c8bae-c72f-4772-967e-f1526f096399
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: 32da99f0-f058-40ae-95a8-2522622438ce
exl-id: 2ab55a72-2eb2-49dc-8716-0a8a4d0c4b73
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 77%

---

# Ausführung von AEM im produktionsbereiten Modus{#running-aem-in-production-ready-mode}

Mit AEM 6.1 führt Adobe die neue `"nosamplecontent"` Ausführungsmodus, der darauf abzielt, die Schritte zu automatisieren, die zur Vorbereitung einer AEM Instanz für die Bereitstellung in einer Produktionsumgebung erforderlich sind.

Der neue Ausführungsmodus konfiguriert nicht nur automatisch die Instanz, um die in der Sicherheitsprüfliste beschriebenen Best Practices für die Sicherheit einzuhalten, sondern entfernt darüber hinaus alle Geometrixx-Beispielsanwendungen und -konfigurationen innerhalb des Prozesses.

>[!NOTE]
>
>Da der produktionsbereite Modus von AEM aus praktischen Gründen nur einen Großteil der für die Sicherung einer Instanz erforderlichen Aufgaben abdeckt, empfehlen wir Ihnen dringend, vor dem tatsächlichen Einsatz der Produktionsumgebung die [Sicherheitsprüfliste](/help/sites-administering/security-checklist.md) durchzugehen.
>
>Beachten Sie außerdem, dass durch die Ausführung von AEM im produktionsbereiten Modus CRXDE Lite effektiv deaktiviert wird. Wenn Sie es zum Debuggen benötigen, finden Sie unter [Aktivieren von CRXDE Lite in AEM](/help/sites-administering/enabling-crxde-lite.md) weitere Informationen.

![chlimage_1-83](assets/chlimage_1-83.png)

Um AEM im produktionsbereiten Modus auszuführen, müssen Sie lediglich die `nosamplecontent` über die `-r` runmode wechseln zu Ihren vorhandenen Startargumenten:

```shell
java -jar aem-quickstart.jar -r nosamplecontent
```

Beispielsweise können Sie den produktionsbereiten Modus zum Starten einer Autoreninstanz mit MongoDB-Persistenz verwenden:

```shell
java -jar aem-quickstart.jar -r author,crx3,crx3mongo,nosamplecontent -Doak.mongo.uri=mongodb://remoteserver:27017 -Doak.mongo.db=aem-author
```

## Ändern eines Teils des produktionsbereiten Modus {#changes-part-of-the-production-ready-mode}

Genauer gesagt werden die folgenden Konfigurationsveränderungen durchgeführt, wenn AEM im produktionsbereiten Modus ausgeführt wird:

1. Das **CRXDE-Support-Bundle** (`com.adobe.granite.crxde-support`) ist im produktionsbereiten Modus standardmäßig deaktiviert. Es kann jederzeit über das öffentliche Maven-Repository installiert werden. Für AEM 6.1. ist Version 3.0.0 erforderlich.

1. Das Bundle **Apache Sling Simple WebDAV Access to repositories** (`org.apache.sling.jcr.webdav`) ist nur für **Autoreninstanzen** verfügbar.

1. Neu erstellte Benutzer müssen das Passwort bei der ersten Anmeldung ändern. Dies gilt nicht für den Admin-Benutzer.
1. **Debug-Informationen generieren** ist für die **Apache Sling Java Script Handler**.

1. **Die Funktionen zum zugeordneten Inhalt** und **zum Erzeugen von Debug-Informationen** sind für den **Apache Sling Jsp Script Handler** deaktiviert.

1. Der **Day CQ WCM-Filter** ist auf `edit` bei der **Autoreninstanz** und auf `disabled` bei der **Veröffentlichungsinstanz** eingestellt.

1. Die **Adobe Granite HTML Library Manager** wird mit den folgenden Einstellungen konfiguriert:

   1. **Minify:** `enabled`
   1. **Debug:** `disabled`
   1. **Gzip:** `enabled`
   1. **Zeit:** `disabled`

1. Das **Apache Sling Get Servlet** ist so eingestellt, dass es sichere Konfigurationen standardmäßig unterstützt, so zum Beispiel wie folgt:

| **Konfiguration** | **Autor** | **Veröffentlichen** |
|---|---|---|
| TXT-Ausgabe | disabled | disabled |
| HTML-Ausgabedarstellung | disabled | disabled |
| JSON-Ausgabe | enabled | enabled |
| XML-Ausgabe | disabled | disabled |
| json.maximumresults | 1000 | 100 |
| Auto-Index | disabled | disabled |
