---
title: '"Datenbank DB2: Einen Prozess wöchentlich ausführen"'
seo-title: 'DB2 database: Running a process weekly'
description: Erfahren Sie, wie Sie die Leistung Ihrer AEM Forms DB2-Datenbank verbessern können.
seo-description: See how you can improve the performance of your AEM forms DB2 database.
uuid: 36070087-c250-41df-a841-aa922e777697
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: fc0e8183-5d50-4fc0-997a-5f3168ba0d70
exl-id: f40fcfab-63e0-4e43-aac5-95426e3dd1fb
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 100%

---

# Datenbank DB2: Einen Prozess wöchentlich ausführen{#db-database-running-a-process-weekly}

Wenn Ihre DB2-Datenbank für AEM Forms immer langsamer werden sollte, führen Sie die folgenden Anweisungen wöchentlich aus, um ihre Leistung zu verbessern:

1. Starten Sie das DB2 Control Center:

   (Windows) Wählen Sie „Start“ > „Programme“ > „IBM DB2“ > „General Administration Tools“ > „Control Center“ aus.

   (Linux und UNIX) Geben Sie an einer Eingabeaufforderung den Befehl `db2jcc` ein.

1. Klicken Sie in der Objektstruktur des DB2 Control Center auf All Databases.
1. Klicken Sie auf die Datenbank, die Sie für AEM Forms erstellt haben, und klicken Sie auf den Ordner „Tables“.
1. Wählen Sie alle Datenbanktabellen im Inhaltsbereich aus, klicken Sie mit der rechten Maustaste darauf und wählen Sie die Option „Run Statistics“ aus.
1. Wechseln Sie zu „Statistics“ > „Index Statistics“.
1. Wählen Sie die Option „Collect statistics for all indexes“ und anschließend „Collect statistics for indexes with extended detailed statistics“ aus und klicken Sie dann auf „OK“.

Wenn der Vorgang abgeschlossen ist, wird eine entsprechende Meldung angezeigt. Schließen Sie die Meldung.
