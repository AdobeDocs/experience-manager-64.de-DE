---
title: Bereinigen von Datensätzen aus der Job Manager-Datenbank
seo-title: Purge records from the Job Manager database
description: Große Prozessdaten können zu niedrigerer AEM Forms-Leistung führen. Es empfiehlt sich, Prozessdaten zu löschen, wenn Datensätze nicht mehr benötigt werden.
seo-description: Large process data can result in lower AEM forms performance. It is good practice to purge process data when records are no longer necessary.
uuid: cf214498-36e9-4dcc-b4d4-e7c46f80dbab
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/health_monitor
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 69a406f2-4fa8-40bb-b671-7b0f5b6a2c4c
exl-id: be2e2a4b-5aac-4612-81b6-b4bbb3036d77
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 7%

---

# Bereinigen von Datensätzen aus der Job Manager-Datenbank {#purge-records-from-the-job-manager-database}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Prozessdaten, die beim Aufrufen eines langlebigen Prozesses generiert werden, können zu groß werden, was zu einer geringeren AEM der Formularleistung und zur Verwendung unnötigen Festplattenspeichers führt. Es empfiehlt sich, Prozessdaten zu löschen, wenn Datensätze nicht mehr benötigt werden.

Sie können Administration Console verwenden, um eine einmalige Bereinigung veralteter Datensätze durchzuführen oder regelmäßige automatische Bereinigungen zu planen. Weitere Methoden zum Bereinigen veralteter Datensätze finden Sie unter [Prozessdaten bereinigen](/help/forms/using/admin-help/purging-process-data.md#purging-process-data).

**Auf die Seite &quot;Zeitplaner für die Auftragsbereinigung&quot;zugreifen**

1. Klicken Sie in Administration Console oben rechts auf der Seite auf Health Monitor .
1. Klicken Sie auf die Registerkarte &quot;Zeitplaner für die Auftragsbereinigung&quot;.

Informationen zu derzeit geplanten Bereinigungen werden im Feld Informationen zur Zeitplanung für die Auftragsbereinigung angezeigt.

>[!NOTE]
>
>Durch Klicken auf Planung stoppen werden alle in der Zukunft geplanten Bereinigungen beendet. Bereinigungsaufträge, die bereits ausgeführt werden, werden jedoch nicht beendet.

**Eine einmalige Bereinigung planen**

1. Wählen Sie &quot;Nur einmal&quot;aus.
1. Geben Sie im Bereich &quot;Filter für abgeschlossene Datensätze bereinigen&quot;die Anzahl der Tage oder Wochen an, nach denen ein Datensatz als veraltet gilt und zur Bereinigung bereit ist.

   >[!NOTE]
   >
   >Datensätze, die sich auf nicht abgeschlossene Prozesse beziehen, werden nicht bereinigt, auch wenn sie älter als das angegebene Alter sind.

1. Geben Sie an, wann die Bereinigung ausgeführt werden soll. Aktivieren Sie das Kontrollkästchen Aktuelles Datum und Uhrzeit verwenden oder deaktivieren Sie das Kontrollkästchen und klicken Sie auf die Kalender- und Uhrensymbole, um Datum und Uhrzeit der Bereinigung anzugeben.

   >[!NOTE]
   >
   >Wenn Sie ein Startdatum und eine Startzeit angeben, die in der Vergangenheit liegen, erfolgt die Bereinigung sofort, wenn Sie auf Planung starten klicken.

1. Klicken Sie auf Planung starten . Alle zuvor geplanten Planungseinstellungen werden durch die neuen Einstellungen ersetzt.

**Automatische Bereinigungsplanung konfigurieren**

1. Wählen Sie &quot;Wiederholen alle&quot;und geben Sie die Anzahl der Tage oder Wochen zwischen den Bereinigungen an.
1. Geben Sie im Bereich &quot;Filter für abgeschlossene Datensätze bereinigen&quot;die Anzahl der Tage oder Wochen an, nach denen ein Datensatz als veraltet gilt und zur Bereinigung bereit ist. Sie können den Wert nicht auf `0` einstellen.

   >[!NOTE]
   >
   >Datensätze, die sich auf nicht abgeschlossene Prozesse beziehen, werden nicht bereinigt, auch wenn sie älter als das angegebene Alter sind.

1. Geben Sie an, wann die Bereinigung beginnen soll. Aktivieren Sie das Kontrollkästchen Aktuelles Datum und Uhrzeit verwenden oder deaktivieren Sie das Kontrollkästchen und klicken Sie auf die Kalender- und Uhrensymbole, um Datum und Uhrzeit der Bereinigung anzugeben.

   >[!NOTE]
   >
   >Wenn Sie ein Startdatum und eine Startzeit angeben, die in der Vergangenheit liegen, berechnet AEM Formulare das logische nächste Startdatum basierend auf dem angegebenen Datum. Wenn Sie beispielsweise planen, dass die Auftragsbereinigung ab dem 7. April wöchentlich durchgeführt wird und jetzt der 9. April ist, wird die erste Bereinigung am 14. April durchgeführt.

1. Klicken Sie auf Planung starten . Alle zuvor geplanten Planungseinstellungen werden durch die neuen Einstellungen ersetzt.
