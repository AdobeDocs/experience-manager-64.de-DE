---
title: Systeminformationen anzeigen
seo-title: View system information
description: Erfahren Sie, wie Sie Diagramme zur Ressourcenüberwachung und Informationen über den Server anzeigen, der AEM Forms ausführt.
seo-description: Learn how you can view resource monitoring charts and information about the server that is running AEM forms.
uuid: 983c1cc7-a8b3-48b2-a4c8-7b28a2e32537
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/health_monitor
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: d51460d9-c96c-4661-b93e-e015427878ab
exl-id: e4542335-fcee-4506-965a-5bfe79f4b29a
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 35%

---

# Systeminformationen anzeigen {#view-system-information}

Auf der Registerkarte „System“ werden Diagramme zur Ressourcenüberwachung und Informationen über den Server angezeigt, der AEM Forms ausführt. Klicken Sie in Administration Console in der rechten oberen Ecke der Seite auf „Health Monitor“, um diese Informationen anzuzeigen. Wenn Sie AEM Forms in einer Clusterumgebung ausführen, gelten die angezeigten Informationen für den auf der Serverliste ausgewählten Knoten.

Um die aktuellen Systeminformationen als Eigenschaftendatei zu speichern, klicken Sie auf „Speichern“.

Im rechten Bereich der Registerkarte „System“ werden die folgenden Informationen grafisch angezeigt:

* Anzahl der Auftrags- und Arbeitselemente
* Heap- und zugesicherte Heap-Auslastung
* Nicht-Heap- und zugesicherte Nicht-Heap-Auslastung

Sie können Ihren Zeiger auf der Zeitachse verschieben, um Werte für einen bestimmten Zeitpunkt abzurufen.

>[!NOTE]
>
>Die Diagrammdaten, Serverinformationswerte und die Uhrzeit werden alle 10 Minuten aktualisiert. Die Informationen werden nicht in Echtzeit angezeigt.

Im linken Bereich der Registerkarte „System“ werden die folgenden Informationen zum Server oder Knoten angezeigt:

**Virtuelle Maschine:** Java Virtual Machine (JVM)-Version auf dem Server.

**Anbieter virtueller Maschinen:** Hersteller des JVM.

**Virtual Machine-Version:** JVM-Versionsnummer

**Maschinenname:** Hostname des Servers, auf dem AEM Formulare installiert sind.

**Up Time:** Die Zeit (in Stunden und Minuten), zu der der Server ausgeführt wurde.

**Just-in-Time-Compiler:** Der Name des verwendeten Compilers.

**Kompilierungszeit:** Die für die Kompilierung aufgewendete Zeit.

**Anzahl der Live-Threads:** Die Gesamtzahl der Threads, die derzeit im AEM Forms-System vorhanden sind.

**Threads-Spitze:** Die größte Anzahl von Live Threads, die je im System aufgezeichnet wurden.

**Anzahl der geladenen Klassen:** Anzahl der Klassen, die in die JVM geladen wurden.

**Anzahl der nicht geladenen Klassen:** Anzahl der Klassen, die von der JVM entladen wurden.

**Mindestens Heap:** Die Mindestmenge an Heap, die verwendet wurde.

**Maximale Heap-Größe:** Die maximal verwendete Heap-Menge.

**Betriebssystemname:** Der Name des Betriebssystems, das auf dem AEM forms-Server ausgeführt wird.

**Betriebssystemversion:** Versionsnummer des Betriebssystems, das auf dem AEM forms-Server ausgeführt wird.

**Betriebssystem-Arch:** Die Betriebssystemarchitektur, auf der die JVM ausgeführt wird.

**Anzahl der Prozessoren:** Die Anzahl der Prozessoren im System.

**Argumente virtueller Maschinen:** Das von der JVM verwendete Argument.

**Klassenpfad:** Der von der JVM verwendete Klassenpfad.

**Bibliothekspfad:** Der von der JVM verwendete Bibliothekspfad.

**Boot Class Path:** Der von der JVM verwendete Bootklassenpfad.

**Anwendungsservertyp:** Typ des Anwendungsservers, der zum Ausführen AEM Formularen verwendet wird.

**Application Server-Version:** Versionsnummer des Anwendungsservers, der zum Ausführen AEM Formulare verwendet wird.

**Application Server-Anbieter:** Hersteller des Anwendungsservers, der zum Ausführen AEM Formulare verwendet wird.

**Installationsdatum:** Datum (im Format jjjj-mm-tt), an dem AEM Formulare installiert wurden.

**AEM Forms-Version:** Version der AEM Formulare, die installiert sind.

**Patch-Version:** Patch-Nummer AEM Formulare.

**Datenbankname:** Art der Datenbank, die von AEM Formularen verwendet wird.

**Datenbankversion:** Versionsnummer der von AEM Formularen verwendeten Datenbank.

**Name des Datenbanklaufwerks:** Der Name des Treibers, mit dem die JVM eine Verbindung zur Datenbank herstellt.

**Datenbanktreiberversion:** Die Version des Treibers, mit dem die JVM eine Verbindung zur Datenbank herstellt.

Mit der Schaltfläche **Speichern** können Sie diese Systeminformationen in einer Eigenschaftendatei speichern.
