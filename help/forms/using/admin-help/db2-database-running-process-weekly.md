---
title: "Datenbank DB2: Einen Prozess wöchentlich ausführen"
seo-title: "DB2 database: Running a process weekly"
description: Erfahren Sie, wie Sie die Leistung Ihrer AEM Forms DB2-Datenbank verbessern können.
seo-description: See how you can improve the performance of your AEM forms DB2 database.
uuid: 36070087-c250-41df-a841-aa922e777697
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: fc0e8183-5d50-4fc0-997a-5f3168ba0d70
exl-id: f40fcfab-63e0-4e43-aac5-95426e3dd1fb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 25%

---

# DB2-Datenbank: Einen Prozess wöchentlich ausführen{#db-database-running-a-process-weekly}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Wenn Ihre AEM Forms DB2-Datenbank langsam ausgeführt wird, kann die Ausführung des folgenden wöchentlichen Prozesses die Leistung verbessern:

1. Starten Sie das DB2 Control Center:

   (Windows) Wählen Sie Start > Programme > IBM DB2 > Allgemeine Administrationstools > Kontrollzentrum.

   (Linux und UNIX) Geben Sie an einer Eingabeaufforderung den Befehl `db2jcc` ein.

1. Klicken Sie in der Objektstruktur des DB2 Control Center auf Alle Datenbanken.
1. Klicken Sie auf die für AEM Formulare erstellte Datenbank und dann auf den Ordner Tabellen .
1. Wählen Sie alle Datenbanktabellen im Inhaltsbereich aus, klicken Sie mit der rechten Maustaste darauf und wählen Sie &quot;Run Statistics&quot;.
1. Gehen Sie zu Statistiken > Indexstatistiken .
1. Wählen Sie &quot;Collect Statistics For All Indexes&quot;, &quot;Collect Statistics For Indexes With Extended Detailed Statistics&quot;und klicken Sie auf &quot;OK&quot;.

Nach Abschluss des Vorgangs wird eine Meldung angezeigt. Schließen Sie die Meldung.
