---
title: Protokollierung
seo-title: Logging
description: Erfahren Sie, wie Sie globale Parameter für den zentralen Protokollierungs-Service konfigurieren, bestimmte Einstellungen für einzelne Services festlegen oder eine Datenprotokollierung anfordern können.
seo-description: Learn how to configure global parameters for the central logging service, specific settings for the individual services or how to request data logging.
uuid: 8c9e3628-2f2c-445d-9706-5c7725b85fe2
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: configuring
content-type: reference
discoiquuid: 5aa69b10-2cd0-4d34-8104-8c3b88405926
feature: Configuring
exl-id: d94b776d-db06-4f46-ac7f-c3b8e4160b69
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 64%

---

# Protokollierung{#logging}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

AEM bietet Ihnen die Möglichkeit, Folgendes zu konfigurieren:

* globale Parameter für den zentralen Protokollierungsdienst
* Anforderungsdatenprotokollierung; eine spezielle Protokollierungskonfiguration für Anfrageinformationen
* Spezifische Einstellungen für die einzelnen Dienste; zum Beispiel eine einzelne Protokolldatei und das Format für die Protokollmeldungen

Hierbei handelt es sich jeweils um [OSGi-Konfigurationen](/help/sites-deploying/configuring-osgi.md).

>[!NOTE]
>
>Die Protokollierung in AEM basiert auf Sling-Prinzipien. Weitere Informationen finden Sie unter [Sling-Protokollierung](https://sling.apache.org/site/logging.html).

## Globale Protokollierung {#global-logging}

[Apache Sling Logging Configuration](/help/sites-deploying/osgi-configuration-settings.md) wird zum Konfigurieren der Root-Protokollfunktion verwendet. Dies definiert die globalen Einstellungen für die Anmeldung AEM:

* Protokollierungsstufe
* Speicherort der zentralen Protokolldatei
* Anzahl der beizubehaltenden Versionen
* Versionsrotation; entweder maximale Größe oder Zeitintervall
* Format zum Schreiben der Protokollmeldungen

>[!NOTE]
>
>In diesem [Knowledgebase-Artikel](https://helpx.adobe.com/de/experience-manager/kb/HowToRotateRequestAndAccessLog.html) wird das Rotieren von request.log- und access.log-Dateien erläutert.

## Logger und Writer für einzelne Dienste {#loggers-and-writers-for-individual-services}

Neben den globalen Protokollierungseinstellungen können Sie in AEM bestimmte Einstellungen für einzelne Dienste konfigurieren:

* Bestimmte Protokollierungsstufe
* Speicherort der einzelnen Protokolldatei
* Anzahl der beizubehaltenden Versionen
* Versionsrotation; entweder maximale Größe oder Zeitintervall
* Format zum Schreiben der Protokollmeldungen
* Logger (OSGi-Dienst, der die Protokollmeldungen bereitstellt)

So können Sie die Protokollmeldungen für einen einzelnen Dienst in eine separate Datei leiten. Dies kann insbesondere beim Entwickeln oder Testen nützlich sein, etwa wenn Sie für einen bestimmten Dienst auf eine höhere Protokollierungsstufe angewiesen sind.

AEM verwendet Folgendes, um Protokollmeldungen in die Datei zu schreiben:

1. Ein **OSGi-Dienst** (logger) schreibt eine Protokollmeldung.
1. A **Logging Logger** nimmt diese Nachricht und formatiert sie entsprechend Ihrer Spezifikation.
1. A **Protokollierungswriter** schreibt alle diese Nachrichten in die von Ihnen definierte physische Datei.

Diese Elemente sind über die folgenden Parameter mit den entsprechenden Elementen verknüpft:

* **Logger (Logging Logger)**

   Hiermit werden der Dienst bzw. die Dienste zum Generieren der Meldungen definiert.

* **Protokolldatei (Logging Logger)**

   Definieren Sie die physische Datei zum Speichern der Protokollmeldungen.

   Auf diese Weise werden Logging Logger und Logging Writer miteinander verknüpft. Der Wert muss für die herzustellende Verbindung mit den Parametern in der Logging-Writer-Konfiguration übereinstimmen.

* **Protokolldatei (Logging Writer)**

   Definieren Sie die physische Datei, in die die Protokollmeldungen geschrieben werden.

   Der Wert muss mit den Parametern in der Logging-Writer-Konfiguration übereinstimmen. Andernfalls erfolgt kein Abgleich. Wenn keine Übereinstimmung vorliegt, wird ein impliziter Writer mit Standardkonfiguration erstellt (tägliche Protokollrotation).

### Standard-Logger und -Writer {#standard-loggers-and-writers}

Bestimmte Logger und Writer sind in einer standardmäßigen AEM-Installation enthalten.

Das erste Paar ist ein Sonderfall, da sowohl `request.log`- als auch `access.log`-Dateien gesteuert werden:

* Der Logger:

   * Apache Sling Customizable Request Data Logger

      (org.apache.sling.engine.impl.log.RequestLoggerService)

   * Schreibt Meldungen zum Anforderungsinhalt in die Datei `request.log`.

* Ist verknüpft mit:

   * Apache Sling Request Logger

      (org.apache.sling.engine.impl.log.RequestLogger)

   * Schreibt Meldungen in `request.log` oder `access.log`.

Eine Anpassung ist hier ggf. möglich, obwohl die Standardkonfiguration für die meisten Installationen geeignet ist.

Die anderen Paare folgen der Standardkonfiguration:

* Der Logger:

   * Apache Sling Logging Logger-Konfiguration

      (org.apache.sling.commons.log.LogManager.factory.config)

   * Schreibt `Information`-Meldungen in `logs/error.log`.

* Ist mit dem folgenden Writer verknüpft:

   * Apache Sling Logging Write-Konfiguration

      (org.apache.sling.commons.log.LogManager.factory.writer)

* Der Logger:

   * Apache Sling Logging Logger-Konfiguration (org.apache.sling.commons.log.LogManager.factory.config.649d51b7-6425-45c9-81e6-2697a03d6be7)

   * Schreibt `Warning`-Meldungen in `../logs/error.log` für den `org.apache.pdfbox`-Dienst.

* Ist nicht mit einem bestimmten Writer verknüpft, sodass ein impliziter Writer mit Standardkonfiguration (tägliche Protokollrotation) verwendet wird.

### Erstellen eigener Logger und Writer {#creating-your-own-loggers-and-writers}

Sie können Ihr eigenes Logger-/Writer-Paar definieren:

1. Erstellen einer neuen Instanz der Factory-Konfiguration [Apache Sling Logging Logger-Konfiguration](/help/sites-deploying/osgi-configuration-settings.md).

   1. Geben Sie die Protokolldatei an.
   1. Geben Sie den Logger an.
   1. Konfigurieren Sie ggf. die anderen Parameter.

1. Erstellen einer neuen Instanz der Factory-Konfiguration [Apache Sling Logging Writer-Konfiguration](/help/sites-deploying/osgi-configuration-settings.md).

   1. Geben Sie die Protokolldatei an - diese muss mit der für den Logger angegebenen übereinstimmen.
   1. Konfigurieren Sie ggf. die anderen Parameter.

>[!NOTE]
>
>Unter bestimmten Umständen können Sie eine [benutzerdefinierte Protokolldatei](/help/sites-deploying/monitoring-and-maintaining.md#create-a-custom-log-file).
