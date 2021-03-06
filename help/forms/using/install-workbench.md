---
title: Installieren von Workbench
seo-title: Install workbench
description: Installieren Sie Workbench.
uuid: null
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: null
source-git-commit: 19dcda357b34e7160792d43cb9335fc3be0dedbc
workflow-type: tm+mt
source-wordcount: '2743'
ht-degree: 89%

---


# Installieren von Workbench {#install-workbench}

Dieses Dokument enthält Anweisungen zur Installation und Konfiguration von Workbench. Das Installationsprogramm installiert außerdem Designer.

## Info {#about}

Die Informationen in diesem Dokument richten sich an Administratoren und Entwickler, die für die Installation, Konfiguration, Verwaltung oder Bereitstellung von Workbench zuständig sind.
Darüber hinaus finden Sie darin die Informationen, die erforderlich sind, um Ihr System so konfigurieren, dass aktualisierte Prozesse von Adobe ® AEM Forms® Enterprise Suite (ES) Update 1 (8.2.x) und Adobe® AEM Forms® Enterprise Suite 2 (ES2) unterstützt werden.
Es wird vorausgesetzt, dass die Leser dieses Dokuments mit dem Microsoft® Windows®-Betriebssystem vertraut sind.

## Zusätzliche Informationen {#additional-information}

Die Ressourcen in dieser Tabelle können Ihnen dabei helfen, mehr über AEM Forms zu erfahren, und vermitteln Ihnen die ersten Schritte.
<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Informationen</strong></p> </td> 
   <td><p><strong>Siehe</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Informationen bezüglich der Prozesse für Workbench</p> </td> 
   <td><p><a href="http://www.adobe.com/go/learn_aemforms_workbench_61_de">Workbench-Hilfe</a><br /> <br /> </p> </td> 
  </tr> 
  <tr> 
   <td><p>Allgemeine Informationen zu AEM Forms und dessen Integration in anderen Adobe-Produkten</p> </td> 
   <td><p><a href="http://adobe.com/go/learn_aemforms_introduction_65_de">Übersicht über AEM Forms</a><br /> <br /> </p> </td> 
  </tr> 
  <tr> 
   <td><p>Ein Tutorial zum Erstellen und Testen einer AEM Forms-Anwendung in Workspace</p> </td> 
   <td><p><a href="http://adobe.com/go/learn_aemforms_firstapp_ds_65">Erstellen der ersten AEM Forms-Anwendung</a><br /> <br /> </p> </td> 
  </tr> 
  <tr> 
   <td><p>Die gesamte Dokumentation, die für AEM Forms verfügbar ist</p> </td> 
   <td><p><a href="http://adobe.com/go/learn_aemforms_introduction_65">AEM Forms-Dokumentation</a><br /> <br /> </p> </td> 
  </tr> 
  <tr> 
   <td><p>Sonstige Dienste und Produkte, die in AEM Forms integriert werden können</p> </td> 
   <td><p><a href="http://www.adobe.com/de/">www.adobe.com</a><br /> <br /> </p> </td> 
  </tr> 
  <tr> 
   <td><p>Patch-Updates, technische Hinweise und zusätzliche Informationen zu dieser Produktversion</p> </td> 
   <td><p><a href="https://www.adobe.com/account/sign-in.supportportal.html">Wenden Sie sich an den Adobe Enterprise-Support</a><br /> <br /> </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Der Flex-Workspace wird für AEM Forms nicht mehr unterstützt. Es ist für die AEM Forms-Version verfügbar.

## Vor der Installation {#before-you-install}

### Installation von Workbench – Übersicht {#workbench-installation-overview}

Workbench ist eine integrierte Entwicklungsumgebung (IDE), die Entwickler und Formularersteller verwenden, um automatisierte Geschäftsprozesse und Formulare zu erstellen. Sie wird auch verwendet, um die Ressourcen und Dienste zu verwalten, die die Prozesse und die Formulare verwenden.

Die folgende Abbildung zeigt die Workbench-Installation, einschließlich:
* Process Design mit Workbench
* Formularentwickler mit Designer

>[!NOTE]
>
>Der AEM Forms-Server erfordert ein separates Installationsprogramm. Weitere Informationen finden Sie in der Dokumentation zur Installation von AEM Forms auf JEE.

## Systemanforderungen {#system-prerequisites}

In diesem Abschnitt werden die Hardware- und Softwareanforderungen und die unterstützten Plattformen dargelegt.

### Mindestanforderungen an Hardware und Software {#minimum-hardware-software-requirements}

**Workbench**
Als Minimum werden die folgenden Anforderungen empfohlen: 
Speicherplatz für die Installation:
* 680 MB nur für Workbench.
* 2,15 GB auf einem einzigen Laufwerk für eine vollständige Installation von Workbench, Designer und die Assemblierung der Beispiele.
* 400 MB für temporäre Installationsordner – 200 MB im temporären Ordner des Benutzers und 200 MB im temporären Ordner von Windows.

>[!NOTE]
>
>Wenn sich diese Speicherorte alle auf einem einzigen Laufwerk befinden, müssen während der Installation 1,5 GB Speicherplatz zur Verfügung stehen. Die Dateien, die in den temporären Ordner kopiert werden, werden nach Abschluss der Installation gelöscht.

* Hardware-Anforderung: Intel® Pentium® 4 oder gleichwertiger AMD-Prozessor, 1 GHz.
* Laden Sie die neueste Version von Adobe AIR herunter und installieren Sie diese (von <a href="http://www.adobe.com/">www.adobe.com</a>) erforderlich für den Community Help Client, der in Workbench integriert ist.
* Java™ Runtime Environment (JRE) 6.0 Update 22 oder höher Updates auf 6.0 *Neu für 10*.
* Minimale Bildschirmauflösung 1024 x 768 Pixel oder höher mit 16-Bit-Farbtiefe oder höher.
* TCP/IPv4- oder TCP/IPv6-Netzwerkverbindung zum AEM Forms-Server.
* Installieren Sie Visual C++ Redistributable Runtime Packages 2012 32-Bit.
* Installieren Sie Visual C++ Redistributable Runtime Packages 2013 32-Bit.

>[!NOTE]
>
>Wenn auf Ihrem Computer Adobe® Acrobat® X installiert ist, stellen Sie sicher, dass Sie es deinstallieren, bevor Sie Workbench installieren. Sie können Acrobat erneut installieren, nachdem Sie Workbench installiert haben.

>[!NOTE]
>
>Sie müssen über Administratorrechte verfügen, um Workbench installieren zu können. Wenn Sie die Installation nicht unter einem Administratorkonto durchführen, werden Sie vom Installationsprogramm zur Eingabe der Berechtigungen für ein passendes Konto aufgefordert.

### Unterstützte Plattformen {#supported-platforms}

Die vollständige Liste der unterstützten Plattformen für Workbench finden Sie unter [Von AEM Forms unterstützte Plattformen](http://adobe.com/go/learn_aemforms_supportedplatforms_65_de).

## Überlegungen zur Installation von Designer {#designer-installation-considerations}

Standardmäßig enthält die Workbench-Installation eine entsprechende englische Version von Designer. Wenn das Programm zur Installation von Workbench eine vorhandene Version von Designer auf Ihrem Computer erkennt, kann es sein, dass die Installation abbricht und Sie aufgefordert werden, erst Ihre aktuelle Version von Designer zu entfernen, bevor Sie fortfahren können.
Die folgende Tabelle enthält eine vollständige Liste der möglicherweise auftretenden Installationsszenarien von Designer, sowie alle Aktionen, die Sie ausführen müssen, wenn Sie Workbench installieren.

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Aktuell installierte Version von Designer</strong></p> </td> 
   <td><p><strong>Erforderliche Aktionen</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Acrobat Pro oder Acrobat Pro Extended (mit Designer)</p> </td> 
   <td><p>Ohne. Die Workbench-Installation erkennt auf Ihrem Computer eine Instanz von Designer, die entweder mit Acrobat Pro oder Acrobat Pro Extended installiert wurde.
Verschiedene Versionen von Designer können parallel auf demselben System vorhanden sein – zum Beispiel Designer 8.2.x und 9.0.x. Es ist nicht erforderlich, die Version von Designer zu deinstallieren, die mit Acrobat 10 Pro oder Acrobat 10 Pro Extended installiert wurde.
<br /> <br /> </p> </td> 
  </tr> 
  <tr> 
   <td><p>Designer (eigenständig)</p> </td> 
   <td><p>Ohne. Die Version von Designer in Workbench ist nur in englischer Sprache verfügbar. Das Workbench-Installationsprogramm installiert keine neue Version von Designer. Stattdessen wird eine aktualisierte Version, zusammen mit dem Installationsprogramm von Workbench, gepatcht. Dies ermöglicht es Ihnen auch, Ihre lokalisierte Version von Designer in Workbench zu verwenden.<br /> <br /> </p> </td> 
  </tr> 
 </tbody> 
</table>

### Deinstallation von Designer (eigenständig) {#uninstall-designer-standalone}

1. Navigieren Sie zu **Systemsteuerung > Programme > Programme und Funktionen**
1. Wählen Sie unter Aktuell installierte Programm das Programm **Adobe Designer**.
1. Klicken Sie auf **Deinstallieren** und dann auf **Ja**.

### Deinstallation von Designer (eigenständig) unter Windows 10 {#uninstall-designer-standalone-windows10}

1. Navigieren Sie zu **Systemsteuerung > Programme > Programme und Funktionen**
1. Wählen Sie unter Aktuell installierte Programm das Programm **Adobe Designer**.
1. Klicken Sie auf **Deinstallieren** und dann auf **Ja**.

### Deinstallation von Designer, wenn das Programm in Acrobat Pro oder Acrobat Pro Extended enthalten ist {#uninstall-designer-included-with-acrobatpro-or-acrobatextended}

1. Navigieren Sie zu **Systemsteuerung > Programme > Programme und Funktionen**
1. Wählen Sie unter Aktuell installierte Programm **Adobe Acrobat Pro** oder **Adobe Acrobat Pro Extended**.
1. Klicken **Änderung** und klicken Sie anschließend auf **Nächste**.
1. Auswählen **Ändern** und klicken Sie anschließend auf **Nächste**.
1. Wählen Sie **Adobe Designer**, dann **Diese Funktion ist nicht verfügbar** und klicken Sie dann auf **Weiter**
1. Klicken Sie auf **Aktualisieren** und dann auf **Fertig stellen**

### Deinstallieren von Designer, das in Acrobat Pro oder Acrobat Pro Extended unter Windows 10 enthalten ist {#uninstall-designer-included-with-acrobatpro-or-acrobatextended-windows10}

1. Navigieren Sie zu **Systemsteuerung > Programme > Programme und Funktionen**
1. Wählen Sie unter Aktuell installierte Programm **Adobe Acrobat Pro** oder **Adobe Acrobat Pro Extended**.
1. Klicken **Änderung** und klicken Sie anschließend auf **Nächste**.
1. Auswählen **Ändern** und klicken Sie anschließend auf **Nächste**.
1. Wählen Sie **Adobe Designer**, dann **Diese Funktion ist nicht verfügbar** und klicken Sie dann auf **Weiter**
1. Klicken Sie auf **Aktualisieren** und dann auf **Fertig stellen**

## Workbench installieren {#installing-workbench}

In diesem Kapitel wird beschrieben, wie Workbench installiert wird.

### Installieren und Ausführen von Workbench {#installing-and-running-workbench}

Stellen Sie vor der Installation von Workbench sicher, dass die Umgebung über die Software und Hardware verfügt, die zum Ausführen von Workbench erforderlich ist (siehe Abschnitt **Vor der Installation**).

**Installation und Ausführung von Workbench:**

1. Führen Sie eine der folgenden Aufgaben aus:
   * Navigieren Sie zum Ordner \Workbench auf dem Installationsmedium und doppelklicken Sie auf die Datei „run_windows_installer.bat“.
   * Laden Sie Workbench auf Ihr Dateisystem herunter und entpacken Sie es. Nach dem Herunterladen navigieren Sie zum Ordner \Workbench und doppelklicken Sie auf die Datei „run_windows_installer.bat“.

   >[!IMPORTANT]
   >
   >Das Installationsprogramm von Workbench wird nur von einer DVD oder einem lokalen Laufwerk aus ausgeführt. Es kann nicht von einer Remote-Site aus ausgeführt werden.

   >[!NOTE]
   >
   >Wenn der Fehler „Virtuelle Java-Maschine kann nicht erstellt werden“ auftritt, erstellen Sie eine Umgebungsvariable mit dem Namen _JAVA_OPTIONS mit dem Wert -Xmx512M und führen Sie das Installationsprogramm aus.

1. Klicken Sie im Begrüßungsbildschirm auf Weiter.
1. Lesen Sie die Lizenzvereinbarung für das Produkt, wählen Sie Ich akzeptiere die Bedingungen der Lizenzvereinbarung und klicken Sie dann auf Weiter.
1. (Optional) Wählen Sie Adobe Designer installieren, wenn Sie dieses Werkzeug benötigen, um Formulare zu erstellen und zu ändern.

   >[!NOTE]
   >
   >Sie können weiterhin den mit Acrobat 10 installierten Designer verwenden, indem Sie diese Option deaktiviert lassen.

1. Akzeptieren Sie den angegebenen Standardordner oder klicken Sie auf „Auswählen“ und wechseln Sie zu dem Ordner, in dem Sie Workbench installieren möchten. Dann klicken Sie auf „Weiter“.

   >[!NOTE]
   >
   >Der Installationsordnerpfad darf keine #- (Raute-) und $- (Dollar-)Zeichen enthalten.

1. Lesen Sie die Vorinstallationsübersicht und klicken Sie auf Installieren. Das Installationsprogramm zeigt den Status der Installation an.
1. Lesen Sie die Installationsübersicht. Wählen Sie „AEM Forms Workbench starten“, um Workbench zu starten, und klicken Sie dann auf „Weiter“.
1. Lesen Sie die Versionshinweise und klicken Sie auf Fertig.
1. Jetzt sind die folgenden Elemente auf Ihrem Computer installiert:
   * **Workbench**: Um Workbench im Menü „Start“ auszuführen, wählen Sie „Alle Programme“ > „AEM Forms“ > „Workbench“, falls Sie den Verknüpfungsordner dort gespeichert haben. Weitere Informationen finden Sie in der Dokumentation Verwenden von Workbench.
   * **Designer**: Sie können von Workbench aus auf Designer zugreifen. Weitere Informationen finden Sie im Thema „Erste Schritte“ in der Designer-Hilfe.
   * **Workbench-Plug-in**: Befolgen Sie die Anweisungen unter &quot;3.3 Installation der Workbench Eclipse-Funktion&quot;auf Seite 6.
   * **AEM Forms SDK**: Weitere Informationen zur Verwendung des SDK finden Sie unter <a href="http://www.adobe.com/go/learn_lc_programming_10_de">Programmieren mit AEM Forms</a>.

## Aktualisieren von Prozessen {#upgrading-processes}

AEM Forms Update 1- und LiveCycle ES2-Prozesse können mit dem Upgrade-Assistenten auf AEM Forms-Anwendungen aktualisiert werden. Weitere Informationen finden Sie in der Dokumentation zum Aktualisieren von Legacy-Artefakten in der Workbench-Hilfe.

### Installation der Funktion Workbench Eclipse {#installing-workbench-eclipse-feature}

Sie können optional die Workbench-Funktion zu Eclipse hinzufügen. Sie können Workbench hinzufügen, nachdem Sie Workbench installiert haben. Für JBoss enthält die Datei zum Beispiel der folgende Speicherort:

* Workbench_DVD/additional/eclipse Herunterladen und Installieren von Eclipse 3.6 aus <a href="https://www.eclipse.org/downloads/">www.eclipse.org/downloads</a>.

### Konfigurieren der Eclipse-Aktualisierungsfunktion für Workbench {#configuring-eclipse-update-feature-for-workbench}

Workbench unterstützt die Aktualisierungsfunktion, um sicherzustellen, dass die aktuellste Version von Eclipse verwendet wird. Allerdings müssen Sie sicherstellen, dass bestimmte zusätzliche Module in jedem Download enthalten sind:

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Eclipse Version</strong></p> </td> 
   <td><p><strong>Für Workbench erforderliche Module</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Eclipse 3.6.x</p> </td> 
   <td><p>

* Graphical Editing Framework GEF [org.eclipse.gef.feature.group]: Dies ist im &quot;Graphical Modeling Framework SDK&quot;enthalten. [org.eclipse.gmf.sdk.feature.group]

* WST XML Core [org.eclipse.wst.xml_core.feature.feature.group]: Dies ist im &quot;Eclipse XML Editors and Tools&quot;enthalten. [org.eclipse.wst.xml_ui.feature.feature.group]

* Plug-in &quot;org.apache.commons.lang_2.3.0&quot; [Nicht zutreffend]: Dies ist in der &quot;Mylyn Task List (Erforderlich)&quot;enthalten. [org.eclipse.mylyn_feature.feature.group]

   </p> </td> 
  </tbody>
  </table>

**Installation und Bereitstellung der Workbench-Funktion in Eclipse**:
1. Starten Sie Eclipse.
1. Wählen Sie Hilfe > Neue Software installieren und klicken Sie auf Hinzufügen, um das Dialogfeld „Repository hinzufügen“ zu öffnen.
1. Klicken Sie im Dialogfeld „Repository hinzufügen“ auf Lokal und navigieren Sie zu dem Ordner, in dem die Workbench-Installation die Plug-in-ZIP-Datei gespeichert hat, dann wählen Sie die Datei workbench-updatesite.zip und klicken auf Öffnen.
1. Befolgen Sie die Anweisungen auf den nachfolgenden Bildschirmen, um die Workbench-Funktion in Eclipse bereitzustellen.

   >[!NOTE]
   >
   >Ignorieren Sie die Meldung „Warnung: Sie sind im Begriff, eine unsignierte Funktion zu installieren“, und klicken Sie auf Installieren, um fortzufahren.

   >[!NOTE]
   >
   >Mit dem Adobe AEM Forms Discovery-Plug-in für Flash Builder können Sie schnell Adobe Flex- und AIR-Anwendungen erstellen, die einen Dienst aufrufen, der über seine Remoting-Endpunkte Teil von AEM Forms ist. Informationen zur Installation und Aktualisierung des Plug-ins finden Sie auf der Adobe-Website unter **Link erforderlich**.

### Konfigurieren und Protokollieren auf dem Server {#configuring-and-logging-server}

Um Workbench zu verwenden, muss eine Instanz von AEM Forms laufen, normalerweise auf einem separaten Computer. Sie müssen über einen Benutzernamen und ein Kennwort verfügen, um sich bei AEM Forms anzumelden, außerdem müssen Ihnen Informationen über den Speicherort des Servers bekannt sein.

>[!NOTE]
>
>Wenn Sie AEM Forms konfiguriert haben, um EMC Documentum oder IBM FileNet-Repository-Anbieter zu verwenden, und Sie sich bei einem anderen Repository als demjenigen anmelden möchten, das in der Administration-Console von AEM Forms als Standard konfiguriert ist, müssen Sie den Benutzernamen als username@Repository angeben.

### Konfigurieren von Zeitlimiteinstellungen {#configuring-timeout-settings}

Standardmäßig beträgt das Zeitlimit von Workbench, unabhängig von Aktivität bzw. Inaktivität, zwei Stunden. Informationen zur Bearbeitung der Zeitlimiteinstellung finden Sie unter „Konfigurieren von User Management“ > „Erweiterte Systemattribute konfigurieren“ in der Hilfe zur Administration-Console.

### Konfigurieren von Workbench, um eine Verbindung über HTTPS herzustellen {#configuring-workbench-to-connect-over-HTTPS}

Um Workbench über HTTPS mit einem AEM Forms-Server zu verbinden, müssen Sie sicherstellen, dass die Zertifizierungsstelle (CA), die den öffentlichen Schlüssel ausgestellt hat, von Workbench als vertrauenswürdig eingestuft wird. Wenn das Zertifikat nicht als von einer vertrauenswürdigen Quelle kommend anerkannt wird, dann müssen Sie die Datei „cacert“ im Ordner „[Workbench_HOME]/workbench/jre/lib/security“ aktualisieren.

>[!NOTE]
>
>[Workbench_HOME] ist dabei der Ordner, in dem Sie Workbench installiert haben. Der standardmäßige Speicherort ist C:\Programme (x86)\Adobe Experience Manager Forms Workbench.

Stellen Sie sicher, dass Sie die Verbindung mit HTTPS herstellen, indem Sie den im Zertifikat angegebenen Namen verwenden. Dieser Name ist in der Regel der vollständig qualifizierte Hostname.

**Zur Aktualisierung der Datei „cacert“**:
1. Stellen Sie sicher, dass Sie eine Kopie des Secure Sockets Layer- (SSL-)Zertifikats haben. Kontaktieren Sie entweder den Administrator, der den SSL-Server konfiguriert hat, oder exportieren Sie das Zertifikat, indem Sie einen Webbrowser verwenden.

   >[!NOTE]
   >
   >Um das Zertifikat zu exportieren, öffnen Sie einen Webbrowser und melden Sie sich bei der Administration-Console an, installieren Sie dann das Zertifikat im Browser und exportieren Sie das Zertifikat vom Browser in einen temporären Speicherort (oder direkt in den Ordner [Workbench_HOME]/workbench/jre/lib/security).

1. Kopieren Sie das Zertifikat in den Ordner [Workbench_HOME]/workbench/jre/lib/security.

1. Öffnen Sie ein Eingabeaufforderungsfenster, navigieren Sie zu [Workbench_HOME]/workbench/jre/bin und geben Sie folgenden Befehl ein:
   `keytool -import -storepass changeit -file [Workbench_HOME]\workbench\jre\lib\security\ssl_cert_for_certname.cer -keystore [Workbench_HOME]\workbench\jre\lib\security\cacerts -alias example`
Dabei gilt:
   * changeit ist das Standardkennwort zum Keystore „cacerts“.
   * certname ist das Zertifikat, das Sie in Schritt 1 ausgewählt haben.
   * example ist der Aliasname, den Sie für das Zertifikat auswählen. Dieser Wert kann geändert werden

1. Wenn Sie dazu aufgefordert werden, das Zertifikat als vertrauenswürdig festzulegen, geben Sie Ja ein und drücken Sie danach die Eingabetaste. Das Keytool importiert dann die Datei „cacerts“ in den Ordner [Workbench_HOME]/workbench/jre/lib/security.

1. Schließen Sie Workbench und starten Sie es neu, um Änderungen anzuwenden.

### Konfiguration von Cache-Einstellungen für dynamisch erstellte Vorlagen {#configuring-cache-settings-for-dynamically-generated-templates}

Die folgenden Aspekte der Cache-Operation sollten Sie in Betracht gezogen werden, wenn Ihre Anwendung eindeutige Vorlagen spontan erstellt, indem XFA-Inhalte automatisch aktualisiert werden. In Wirklichkeit verwendet jede Transaktion eine neue, eindeutige Vorlage.

Wenn der Formularersteller oder die Formularausgabe im Cache nach Einträgen für eine bestimmte Formularvorlage sucht oder sie aktualisiert, verwendet er/sie mehrere Schlüsselwerte, um den entsprechenden Cache-Eintrag zu finden, auf den zugegriffen wird.

* **Dateiname der Vorlage**: Als primäre eindeutige Kennung des zwischengespeicherten Formulars wird der Pfad und der Dateiname der Vorlage verwendet.
* **Zeitstempel**: Die Vorlagedatei enthält einen Zeitstempel, der verwendet wird, um den Zeitpunkt der letzten Aktualisierung des Formulars zu bestimmen.
* **Vorlage-UUID**: Designer fügt in die jeweilige Vorlage eine eindeutige Kennung (UUID) für das Formular und seine Version ein. Immer wenn das Formular aktualisiert wird, wird die eingebettete UUID aktualisiert. Die XDP-Vorlage könnte zum Beispiel den folgenden Inhalt anzeigen:

   `<?xml version="1.0" encoding="UTF-8"?>`
   `<?xfa generator="AdobeAEM formsDesignerES_V8.2" APIVersion="2.6.7185.0"?><xdp:xdp xmlns:xdp=http://ns.adobe.com/xdp/ timeStamp="2008-07-29T21:22:12Z" uuid="823e538f-ff6c-4961-b759-f7626978a223"><template xmlns="http://www.xfa.org/schema/xfa-template/2.6/">`

* **Wiedergabeoptionen**: Im Formularwiedergabecache werden die Cache-Inhalte für jeden Satz von eindeutigen Wiedergabeoptionen separat gespeichert.


Der Forms-Dienst erhält Vorlagen durch Verweis auf Dateinamen oder Repository-Speicherort oder durch einen Wert als XML-Objekt im Speicher.
* **Durch Verweis übergebene Vorlagen**: Verwendet den Inhaltsstamm und den Formularnamen. Wenn bei jeder Anforderung eindeutige Vorlagen mit unterschiedlichem Dateinamen mithilfe dieser Methode übergeben werden, wächst der Datenträger-Cache endlos und wird nie wieder verwendet. Um dies zu verhindern, sollten eindeutige Vorlagen mit demselben Dateinamen übergeben werden, um sicherzustellen dass für alle Anforderungen derselbe Cache aktualisiert wird.
* **Nach Wert übergebene Vorlagen**: Verwendet die Vorlagen-Bytes, die zusammen mit den Daten übergeben werden, mithilfe des Parameters theinDataDoc. Wenn eindeutige Vorlagen mit unterschiedlichem UUID mithilfe dieser Methode übergeben werden, wächst der Datenträger-Cache endlos und wird nie wieder verwendet. Um dies zu verhindern, sollte das UUID-Attribut aus allen Vorlagen entfernt werden, um sicherzustellen, dass für die Vorlage kein Cache erstellt wird. Alternativ werden durch die Übergabe derselben UUID, deren Wert nicht Null ist, Cache-Objekte erstellt, es wird jedoch sichergestellt, dass bei jeder Anforderung derselbe Cache aktualisiert wird.

Um zu verhindern, dass der Cache endlos anwächst, sollten Sie die folgenden Faktoren für das Rendern von dynamisch generierten Vorlagen mithilfe der neuen AEM Forms-APIs, nämlich renderHTMLForm2 und renderPDFForm2, berücksichtigen.

Wenn Sie neue APIs verwenden, wird die Vorlage als ein Dokumentobjekt übergeben, das im Forms-Dienst bearbeitet wird, je nachdem, ob es passiviert ist oder nicht.

Für passivierte Dokumente, in denen die UUID und der Inhaltsstamm als Cache-Schlüssel dienen, sollten Sie folgende Aspekte beachten:
* Der Cache wird nicht für passivierte Eingabevorlagen ohne UUID erstellt.
* Wenn mehr als eine passivierte Eingabevorlage mit derselben UUID und demselben Inhaltsstamm übergeben werden, wird derselbe Cache überschrieben.

Für nicht passivierte Dokumente, in denen der Dateiname und der Inhaltsstamm als Cache-Schlüssel dienen, sollten Sie folgende Aspekte beachten:
* Bei nicht-passivierten Eingabevorlagen hängt das Zwischenspeichern vom Inhaltsstamm und vom Dateinamen ab, von wo aus das Dokument erstellt wurde.
Derselbe Cache wird nur für Anforderungen mit demselben Inhaltsstamm und demselben Dateinamen der Vorlage verwendet.
Die folgenden bewährten Methoden stellen sicher, dass der Cache nicht endlos wächst, wenn dynamisch erstellte Vorlagen an den Forms-Dienst übergeben werden:
   * Entfernen Sie die UUID oder übergeben Sie dieselbe UUID in allen dynamisch generierten Vorlagen.
   * Generieren Sie das Dokument entweder aus Vorlage-Bytes oder aus demselben Dateinamen auf der Festplatte.

### Deinstallieren von Workbench {#uninstalling-workbench}

Verwenden Sie die Funktion „Software“ in der Systemsteuerung, um das Deinstallationsprogramm zu starten. Die Workbench- und Designer-Anwendungen haben unterschiedliche Deinstallationsprogramme.

## Konfigurieren von AEM Forms XDC Editor {#configuring-aem-forms-xdc-editor}

Mit dem XDC Editor können Administratoren von Netzwerkdruckern XML Forms Architecture Device Configuration-(XDC-)Dateien erstellen und ändern. XDC-Dateien beschreiben die Eigenschaften von Druckern, wie die Druckersprache oder die Korrelation zwischen Papierformat und Position des Druckschachts.

Bevor der Administrator des Netzwerkdruckers den XDC-Editor verwendet, verschieben Sie die XDC-Beispiel-Dateien und lesen Sie die Datei Geräteprofile mit XDC-Editor erstellen.

**Abrufen der Beispiel-XDC-Dateien**:
1. Suchen Sie auf dem AEM Forms-Server den XDC-Ordner in [AEM Forms-Stammverzeichnis]\sdk\samples\Output\IVS.
1. Kopieren Sie den Inhalt dieses Ordners in ein Verzeichnis, auf das vom Workbench- oder Eclipse-System aus zugegriffen werden kann.

**Abrufen der XDC Editor-Hilfe**:
1. Gehen Sie zur Dokumentations-Website von AEM Forms.
1. Klicken Sie auf die Schaltfläche Entwickeln und navigieren Sie zu Erstellen von Geräteprofilen mit XDC Editor. Laden Sie die Datei xdc_editor_help_web.zip herunter und installieren Sie die Hilfedateien, indem Sie die Anweisungen befolgen, die in der Readme-Datei angeführt sind.

