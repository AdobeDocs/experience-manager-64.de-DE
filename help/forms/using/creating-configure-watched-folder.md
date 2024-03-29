---
title: Erstellen oder Konfigurieren eines überwachten Ordners
seo-title: Create or Configure a watched folder
description: Erfahren Sie, wie Sie einen überwachten Ordner erstellen oder löschen oder die Eigenschaften eines vorhandenen überwachten Ordners ändern.
seo-description: Learn how to create or delete a watched folder, or modify the properties of an existing watched folder.
uuid: 659d4d8c-99b8-40dd-b884-bfee4d476fe1
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: publish
discoiquuid: 0ce7b338-6686-49b3-b58b-e7ab6b670708
exl-id: 7e2706e2-092f-4780-be8f-2bf444613d70
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1860'
ht-degree: 43%

---

# Erstellen oder konfigurieren Sie einen überwachten Ordner {#create-or-configure-a-watched-folder}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Ein Administrator kann einen Netzwerkordner konfigurieren, der als *Überwachter Ordner*, sodass ein Benutzer, der eine Datei (z. B. eine PDF-Datei) in den überwachten Ordner ablegt, einen vorkonfigurierten Vorgang startet und die Datei bearbeitet. Nachdem der angegebene Vorgang ausgeführt wurde, speichert der Vorgang die geänderte Datei in einem angegebenen Ausgabeordner. Ausführliche Informationen zur Verwaltung eines überwachten Ordners finden Sie unter [Administration-Hilfe](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md).

Sie können die Benutzeroberfläche des überwachten Ordners für Folgendes verwenden:

* Überwachten Ordner erstellen
* Ändern von Eigenschaften eines vorhandenen überwachten Ordners
* Überwachten Ordner löschen

## Überwachten Ordner erstellen {#create-a-watched-folder}

Bevor Sie einen überwachten Ordner konfigurieren, stellen Sie Folgendes sicher:

* Überwachte Ordner sind eine erweiterte Funktion AEM Formulare. Dies erfordert AEM Forms Add-On-Paket, damit es funktioniert. Stellen Sie sicher, dass das entsprechende AEM Forms Add-On-Paket installiert und konfiguriert ist.
* Sie können den überwachten Ordner in einem freigegebenen oder lokalen Speicher erstellen. Stellen Sie sicher, dass AEM Forms-Benutzer, der für die Ausführung des überwachten Ordners konfiguriert ist, Lese- und Schreibberechtigungen für den überwachten Ordner besitzt.
* Sie können einen Dienst, einen Workflow oder ein Skript verwenden, um einen Vorgang mit einem überwachten Ordner zu automatisieren. Stellen Sie sicher, dass der entsprechende Dienst, Workflow oder ein Skript erstellt wurde und ausgeführt werden kann. Weitere Informationen zur Erstellung von Services, Workflows und Skripts finden Sie unter [Verschiedene Methoden zur Verarbeitung von Dateien](/help/forms/using/watched-folder-in-aem-forms.md#various-methods-for-processing-files).
* Ein überwachter Ordner verfügt über verschiedene Eigenschaften, siehe [Eigenschaften für überwachte Ordner](/help/forms/using/watched-folder-in-aem-forms.md#watchedfolderproperties).

Führen Sie die folgenden Schritte aus, um einen überwachten Ordner zu erstellen:

1. Tippen **Adobe Experience Manager** in der linken oberen Ecke des Bildschirms.
1. Tippen **Instrumente** > **Forms** > **Überwachten Ordner konfigurieren**. Eine Liste der bereits konfigurierten überwachten Ordner wird angezeigt.
1. Tippen Sie auf **Neu**. Eine Liste mit den Feldern, die erforderlich sind, um den überwachten Ordner zu erstellen, wird angezeigt:

   * **Name**: Identifiziert den überwachten Ordner. Verwenden Sie nur alphanumerische Zeichen für den Namen.
   * **Pfad**: Gibt den Speicherort des überwachten Ordners an. In einer Clusterumgebung muss diese Einstellung auf einen freigegebenen Netzwerkordner verweisen, auf den jeder Benutzer zugreifen kann, der auf verschiedenen Knoten eines Clusters AEM.
   * **Prozessdateien verwenden**: Der Typ des zu startenden Prozesses. Zur Auswahl stehen Workflow, Skript oder Dienst.
   * **Dienstname/Skript-Pfad/Workflow-Pfad:** Das Verhalten des Feldes basiert auf dem Wert, der für das Feld **Prozessdateien, die Folgendes verwenden** definiert wird. Sie können die folgenden Werte angeben:

      * Für einen Workflow geben Sie das Workflow-Modell an, das ausgeführt werden soll. Beispiel: /etc/workflow/models/&lt;workflow_name>/jcr:content/model
      * Für ein Skript geben Sie den JCR-Pfad des auszuführenden Skripts an. Beispiel: /etc/watchfolder/test/testScript.ecma
      * Für einen Dienst geben Sie den Filter an, der zum Suchen nach einem OSGi-Dienst verwendet werden soll. Der Dienst ist als Implementierung der com.adobe.aemfd.watchfolder.service.api.ContentProcessor-Schnittstelle registriert. Beispiel: Der folgende Code ist eine benutzerdefinierte Implementierung der ContentProcessor-Schnittstelle mit der benutzerdefinierten Eigenschaft „foo=bar“.

   >[!NOTE]
   >
   >Wenn Sie **Diensleistung** für **Prozessdateien verwenden** festgelegt ist, muss der Wert des Felds Dienstname(inputProcessorType) in Klammern gesetzt werden. Beispiel: (foo=bar).

   ```java
   @Component(metatype = true, immediate = true, label = "WF Test Service", description = "WF Test Service")
   @Service(value = {OutputWriter.class, ContentProcessor.class})
   @Property(name = "foo", value = "bar")
   public class OutputWriter implements ContentProcessor {
   ```

   * **Muster für Ausgabedateien**: Geben Sie eine durch Semikolon (;) getrennte Liste von Mustern an, die ein überwachter Ordner verwendet, um den Namen und Speicherort von Ausgabedateien und Ordnern zu bestimmen. Informationen zu Dateimustern finden Sie unter [Grundlegendes zu Dateimustern](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#about-file-patterns).


1. Tippen **Erweitert**. Der erweiterte Tab enthält weitere Felder. Die meisten dieser Felder enthalten einen Standardwert.

   * **Payload Mapper-Filter:** Wenn Sie einen überwachten Ordner erstellen, wird eine Ordnerstruktur innerhalb des überwachten Ordners erstellt. Die Ordnerstruktur enthält Ordner für Phasen, Ergebnisse, Aufbewahrung, Eingabe und Fehler. Die Ordnerstruktur kann als Eingabe-Payload für den Workflow dienen und die Ausgabe von einem Workflow akzeptieren. Sie kann gegebenenfalls auch Fehlerquellen auflisten. Die Struktur der Nutzdaten unterscheidet sich von der Struktur eines überwachten Ordners anders. Sie können benutzerdefinierte Skripte schreiben, um die Struktur eines überwachten Ordners der Payload zuzuordnen. Ein solches Skript wird als Payload-Mapper-Filter bezeichnet. Es sind zwei vordefinierte Payload-Mapper-Implementierungen verfügbar. Wenn Sie [eine benutzerdefinierte Implementierung](/help/forms/using/watched-folder-in-aem-forms.md#creating-a-custom-payload-mapper-filter)verwenden Sie eine der nativen Implementierungen:

      * **Standard-Mapper:** Verwenden Sie den Standard-Payload-Mapper, um den Eingabe- und Ausgabe-Inhalt der überwachten Ordner in separaten Eingabe- und Ausgabeordnern in der Payload zu belassen.
      * **Einfacher dateibasierter Payload-Mapper:** Verwenden Sie den einfachen dateibasierten Payload-Mapper, um Eingabe- und Ausgabe-Inhalte direkt im Nutzdatenordner zu beizubehalten. Es wird keine zusätzliche Hierarchie erstellt, wie z. B. ein Standard-Mapper.
   * **Ausführungsmodus**: Geben Sie die kommagetrennte Liste der zulässigen Ausführungsmodi für die Ausführung des Workflows an.
   * **Zeitüberschreitung für Stage-Dateien nach:** Geben Sie die Anzahl Sekunden an, nach denen für eine Eingabedatei/einen Ordner, der bereits zur Verarbeitung abgerufen wurde, eine Zeitüberschreitung eintritt und ein Fehler gemeldet wird. Der Zeitüberschreitungsmechanismus wird nur aktiviert, wenn der Wert für diese Eigenschaft eine positive Zahl ist.
   * **Stage-Dateien mit Zeitüberschreitung bei Einschränkung löschen:** Wenn diese Option aktiviert ist, wird der Mechanismus **Zeitüberschreitung für Stage-Dateien nach** nur bei aktivierten Einschränkungen für den überwachten Ordner aktiviert.
   * **Überprüfen des Eingabeordners alle:** Geben Sie das Intervall in Sekunden an, innerhalb dessen der überwachte Ordner auf Eingaben überprüft wird. Außer wenn die Einstellung „Einschränken“ aktiviert ist, muss das Abfrageintervall länger sein als die Verarbeitungsdauer für einen durchschnittlichen Auftrag. Anderenfalls könnte es zu einer Überlastung des Systems kommen. Der Wert des Intervalls muss größer oder gleich 1 sein.
   * **Muster für auszuschließende Dateien**: Geben Sie eine durch Semikolon (;) getrennte Liste von Mustern an, die von einem überwachten Ordner verwendet werden, um zu bestimmen, welche Dateien und Ordner überprüft und aufgenommen werden sollen. Alle Dateien oder Ordner, die diesem angegebenen Muster entsprechen, werden nicht für die Verarbeitung überprüft. Informationen zu Dateimustern finden Sie unter [Grundlegendes zu Dateimustern](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#about-file-patterns).
   * **Muster für einzuschließende Dateien:** Geben Sie eine durch Semikolon (;) getrennte Liste von Mustern an, die vom überwachten Ordner verwendet wird, um zu ermitteln, welche Ordner und Dateien überprüft und aufgenommen werden sollen. Wenn als Muster für einzuschließende Dateien beispielsweise „input*“ eingegeben wird, werden alle Dateien und Ordner aufgenommen, die „input*“ im Namen enthalten. Der Standardwert ist &amp;ast, der alle Dateien und Ordner bedeutet. Weitere Informationen zu Dateimustern finden Sie unter [Grundlegendes zu Dateimustern](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#about-file-patterns).
   * **Wartezeit:** Geben Sie die Zeit in Millisekunden an, die gewartet wird, bevor ein Ordner oder eine Datei nach der Erstellung überprüft wird. Wenn die Wartezeit beispielsweise 3.600.000 Millisekunden (eine Stunde) beträgt und die Datei vor einer Minute erstellt wurde, wird diese Datei abgerufen, nachdem 59 oder mehr Minuten vergangen sind. Der Standardwert ist 0.

      Diese Einstellung ist nützlich, um sicherzustellen, dass der gesamte Inhalt einer Datei oder eines Ordners in den Eingabeordner kopiert wurde. Wenn Sie beispielsweise eine große Datei verarbeiten müssen und das Herunterladen der Datei 10 Minuten dauert, legen Sie die Wartezeit auf 10 x 60 x 1000 Millisekunden fest. Dieses Intervall verhindert, dass der überwachte Ordner die Datei bereits überprüft, wenn sie noch keine 10 Minuten alt ist.

   * **Ergebnisse löschen, die älter sind als:** Geben Sie die Anzahl der Tage an, nach denen die Dateien und Ordner gelöscht werden, die älter als der angegebene Wert sind. Diese Einstellung hilft sicherzustellen, dass der Ergebnisordner nicht voll wird. Ein Wert von -1 Tagen bedeutet, dass der Ergebnisordner nie gelöscht wird. Der Standardwert ist -1.
   * **Ergebnis-Ordnername:** Geben Sie den Namen des Ordners ein, um die Ergebnisse zu speichern. Wenn die Ergebnisse nicht in diesem Ordner angezeigt werden, überprüfen Sie den Fehlerordner. Schreibgeschützte Dateien werden nicht verarbeitet und im Fehlerordner gespeichert. Sie können einen absoluten oder relativen Pfad mit den folgenden Dateimustern verwenden:

      * %F = Dateinamenpräfix
      * %E = Dateinamenerweiterung
      * %Y = Jahr (vollständig)
      * %y = Jahr (letzte zwei Stellen)
      * %M = Monat
      * %D = Tag des Monats
      * %d = Tag des Jahres
      * %H = Stunde (24-Stunden-Format)
      * %h = Stunde (12-Stunden-Format)
      * %m = Minute
      * %s = Sekunde
      * %l = Millisekunde
      * %R = Zufallszahl (zwischen 0 und 9)
      * %P = Prozess- oder Auftrags-ID
      * Wenn es beispielsweise am 17. Juli 2009 20 Uhr ist und Sie C:/Test/WF0/failure/%Y/%M/%D/%H/ angeben, ist der Ergebnisordner C:/Test/WF0/failure/2009/07/17/20.
      * Wenn der Pfad nicht absolut, sondern relativ ist, wird der Ordner im überwachten Ordner erstellt. Der Standardwert ist result/%Y/%M/%D/, der Ergebnisordner im überwachten Ordner. Informationen zu Dateimustern finden Sie unter [Grundlegendes zu Dateimustern](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#about-file-patterns).
   * **Fehler-Ordnername:** Geben Sie den Ordner an, in dem die Dateien gespeichert sind. Dieser Speicherort ist stets relativ zum überwachten Ordner. Sie können Dateimuster verwenden, wie für &quot;Ergebnisordner&quot;beschrieben.
   * **„Bewahren“-Ordnername:** Der Speicherort, an dem Dateien nach erfolgreicher Überprüfung und Aufnahme gespeichert werden. Der Pfad kann ein absolutes, relatives oder Null-Verzeichnis sein. Sie können Dateimuster verwenden, wie für &quot;Ergebnisordner&quot;beschrieben. Der Standardwert ist preserve/%Y/%M/%D/.
   * **Stapelgröße:** Die Anzahl der Dateien oder Ordner, die pro Überprüfung aufgenommen werden. Dadurch wird eine Überlastung des Systems verhindert. Das gleichzeitige Überprüfen zu vieler Dateien kann zu einem Absturz führen. Der Standardwert ist 2.

      Wenn das Überprüfungsintervall gering ist, wird der Eingabeordner häufig von den Threads überprüft. Wenn Dateien häufig im überwachten Ordner abgelegt werden, sollten Sie das Überprüfungsintervall klein halten. Wenn Dateien selten abgelegt werden, verwenden Sie ein größeres Überprüfungsintervall, damit die anderen Dienste die Threads verwenden können.

   * **Throttle On:** Wenn diese Option aktiviert ist, wird die Anzahl der Aufträge für den überwachten Ordner begrenzt, die AEM Forms zu jeder Zeit verarbeiten kann. Der Wert für die Stapelgröße bestimmt die maximale Anzahl an Aufträgen. Weitere Informationen finden Sie unter [Einschränken](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#about-throttling)
   * **Vorhandene Dateien mit ähnlichem Namen überschreiben**: Wenn der Wert auf True festgelegt ist, werden Dateien im Ergebnisordner und im Aufbewahrungsordner überschrieben. Bei Festlegung auf &quot;False&quot;werden Dateien und Ordner mit dem Suffix &quot;Numerischer Index&quot;für den Namen verwendet. Der Standardwert ist False.
   * **Dateien bei Fehler beibehalten:** Wenn der Wert auf True festgelegt ist, werden die Eingabedateien im Falle eines Fehlers beibehalten. Der Standardwert lautet true.
   * **Dateien mit Muster einbeziehen:** Geben Sie eine durch Semikolon (;) getrennte Liste von Mustern an, die vom überwachten Ordner verwendet wird, um zu ermitteln, welche Ordner und Dateien überprüft und aufgenommen werden sollen. Wenn als Muster für einzuschließende Dateien beispielsweise „input*“ eingegeben wird, werden alle Dateien und Ordner aufgenommen, die „input*“ im Namen enthalten. Weitere Informationen finden Sie in der [Administration-Hilfe](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md).
   * **Überwachten Ordner asynchron aufrufen:** Gibt den Aufruftyp als „asynchron“ oder „synchron“ an. Der Standardwert ist „asynchron“. Asynchron wird für langlebige Prozesse empfohlen, während synchron für transiente oder kurzlebige Prozesse empfohlen wird.
   * **Überwachten Ordner aktivieren:** Wenn diese Option aktiviert ist, wird der Überwachungsordner aktiviert. Der Standardwert ist True.



## Ändern von Eigenschaften eines vorhandenen überwachten Ordners {#modify-properties-of-an-existing-watched-folder}

Sie können nicht nur den Namen des überwachten Ordners ändern, sondern auch alle Eigenschaften eines vorhandenen überwachten Ordners. Führen Sie die folgenden Schritte aus, um die Eigenschaften eines vorhandenen überwachten Ordners zu ändern:

1. Tippen Sie auf **Adobe Experience Manager** in der oberen linken Ecke des Bildschirms angezeigt.
1. Tippen **Instrumente** > **Forms** > **Überwachten Ordner konfigurieren**. Eine Liste der bereits konfigurierten überwachten Ordner wird angezeigt.
1. Wählen Sie auf der linken Seite des Bildschirms des überwachten Ordners den überwachten Ordner aus und tippen Sie auf **Bearbeiten.** Eine Liste mit den Feldern, die erforderlich sind, um den überwachten Ordner zu erstellen, wird angezeigt. Die Felder, die auf der Registerkarte **Grundeinstellungen** aufgeführt sind, sind Pflichtfelder. Der erweiterte Tab enthält weitere Felder. Die meisten dieser Felder enthalten einen Standardwert. Sie können diese Eigenschaften entsprechend Ihren Anforderungen ändern.
1. Tippen Sie nach dem Ändern der Eigenschaften auf **Aktualisieren**. Die geänderten Eigenschaften werden gespeichert.
