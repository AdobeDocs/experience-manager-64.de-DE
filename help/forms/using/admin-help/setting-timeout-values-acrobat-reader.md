---
title: 'Zeitlimitwerte zur Verwendung mit Acrobat Reader DC Extensions festlegen '
seo-title: Setting timeout values for use with Acrobat Reader DC extensions
description: Erfahren Sie, wie Sie Timeout-Werte für die Verwendung mit Acrobat Reader DC-Erweiterungen festlegen.
seo-description: Learn how to set timeout values for use with Acrobat Reader DC extensions.
uuid: d6d072a0-0a30-417a-98b1-df8b4ff8f911
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: a9aeeb89-45e9-4d5d-aa25-8145c89b64f2
exl-id: e7de9971-3eac-4248-8709-0da7dd709d1b
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 83%

---

# Zeitlimitwerte zur Verwendung mit Acrobat Reader DC Extensions festlegen  {#setting-timeout-values-for-use-with-acrobat-reader-dc-extensions}

Beim Arbeiten mit einer großen Anzahl von PDF-Dateien in Acrobat Reader DC Extensions sollten Sie sicherstellen, dass die folgenden Zeitlimitwerte entsprechend festgelegt sind, damit es bei Aufträgen nicht zu Zeitüberschreitungen und somit zu Fehlern kommt:

**Standard-Zeitsperre für Entsorgung:**

Dieser Wert kann in Administration Console festgelegt werden. Wählen Sie „Einstellungen“ > „Core-Systemeinstellungen“ > „Konfigurationen“ und geben Sie einen Wert für „Standard-Zeitsperre für Entsorgung“ an.

**User Manager AEM Forms Timeout:** Dieser Wert kann durch Bearbeiten der Datei &quot;config.xml&quot;festgelegt werden. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Konfiguration“ > „Konfigurationsdateien im- und exportieren“ und klicken Sie dann auf „Exportieren“. Öffnen Sie die exportierte Datei „config.xml“ und bearbeiten Sie die folgenden Zeilen:

&lt;entry key=&quot;assertionValidityInMinutes&quot; value=&quot;600&quot;/>

&lt;entry key=&quot;SessionTimeout&quot; value=&quot;600&quot;/>

Speichern Sie die Datei „config.xml“ und importieren Sie sie wieder zurück in Administration Console.

**Sitzungs-Timeout des Anwendungsservers:** Dieser Wert kann auf dem Anwendungsserver festgelegt werden. Weitere Informationen finden Sie in der Dokumentation des entsprechenden Anwendungsservers.
