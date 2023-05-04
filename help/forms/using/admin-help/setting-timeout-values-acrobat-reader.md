---
title: Festlegen von Timeout-Werten für die Verwendung mit Acrobat Reader DC Extensions
seo-title: Setting timeout values for use with Acrobat Reader DC extensions
description: Erfahren Sie, wie Sie Zeitüberschreitungswerte für die Verwendung mit Acrobat Reader DC-Erweiterungen festlegen.
seo-description: Learn how to set timeout values for use with Acrobat Reader DC extensions.
uuid: d6d072a0-0a30-417a-98b1-df8b4ff8f911
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: a9aeeb89-45e9-4d5d-aa25-8145c89b64f2
exl-id: e7de9971-3eac-4248-8709-0da7dd709d1b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 33%

---

# Festlegen von Timeout-Werten für die Verwendung mit Acrobat Reader DC Extensions  {#setting-timeout-values-for-use-with-acrobat-reader-dc-extensions}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Stellen Sie bei der Arbeit an vielen PDF-Dateien in Acrobat Reader DC-Erweiterungen sicher, dass die folgenden Zeitlimitwerte angemessen festgelegt sind, um zu verhindern, dass Aufträge zeitlich nicht ausfallen und fehlschlagen:

**Standard-Zeitsperre für Entsorgung:**

Dieser Wert kann in Administration Console festgelegt werden. Klicken Sie auf Einstellungen > Core-Systemeinstellungen > Konfigurationen und geben Sie einen Wert für Standard-Zeitüberschreitung bei Dokumentenbereitstellung an.

**Maximale Wartezeit des User Managers von AEM Forms:** Dieser Wert kann durch Bearbeiten der Datei config.xml festgelegt werden. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;User Management&quot;> &quot;Konfiguration&quot;> &quot;Konfigurationsdateien importieren und exportieren&quot;und klicken Sie dann auf &quot;Exportieren&quot;. Öffnen Sie die exportierte Datei &quot;config.xml&quot;und bearbeiten Sie die folgenden Zeilen:

&lt;entry key=&quot;assertionValidityInMinutes&quot; value=&quot;600&quot;/>

&lt;entry key=&quot;SessionTimeout&quot; value=&quot;600&quot;/>

Speichern Sie die Datei &quot;config.xml&quot;und importieren Sie sie dann wieder in die Administration Console.

**Maximale Wartezeit bei einer Anwendungsserversitzung:** Dieser Wert kann auf dem Anwendungsserver festgelegt werden. Weitere Informationen finden Sie in der Dokumentation des entsprechenden Anwendungsservers.
