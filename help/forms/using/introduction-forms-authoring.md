---
title: Einführung in das Authoring adaptiver Formulare
seo-title: Introduction to authoring adaptive forms
description: AEM Forms bietet eine benutzerfreundliche, aber leistungsstarke Benutzeroberfläche zum Authoring adaptiver Formulare. Es enthält eine Reihe von Komponenten und Werkzeugen, mit denen Sie Formulare erstellen können.
seo-description: AEM Forms provide easy-to-use yet powerful interface for authoring adaptive forms. It provides a host of components and tools that you can use to build forms.
uuid: 07ff8e79-daf7-4608-9171-91854619cc0b
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: introduction, author
discoiquuid: c7a1d13e-cb61-4082-8ae7-7f5eee9e0a51
feature: Adaptive Forms
exl-id: 62f1ddd3-9fc2-49dd-b588-0c3520e1cdd2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3081'
ht-degree: 57%

---

# Einführung in das Authoring adaptiver Formulare  {#introduction-to-authoring-adaptive-forms}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Übersicht {#overview}

Mit adaptiven Formularen können Sie ansprechende, responsive, dynamische und adaptive Formulare erstellen. AEM Forms bietet eine intuitive Benutzeroberfläche und vordefinierte Komponenten zum Erstellen und Verwenden adaptiver Formulare. Sie können ein adaptives Formular auf der Grundlage eines Formularmodells oder -schemas oder ohne Formularmodell erstellen. Es ist wichtig, sorgfältig ein Formularmodell zu wählen, das nicht nur Ihren Verwendungszwecken entspricht, sondern auch Ihre bestehenden Infrastrukturinvestitionen und -Assets erweitert. Sie können aus den folgenden Optionen wählen, um ein adaptives Formular zu erstellen:

* **Verwendung eines Formulardatenmodell**
   [Datenintegration](/help/forms/using/data-integration.md) ermöglicht die Integration von Entitäten und Services aus unterschiedlichen Datenquellen in ein Formulardatenmodell, das Sie zum Erstellen adaptiver Formulare verwenden können. Wählen Sie das Formulardatenmodell, wenn Sie ein adaptives Formular erstellen, für das Daten aus mehreren Datenquellen abgerufen und in diese geschrieben werden sollen.

* **Verwenden einer XDP-Formularvorlage** Dieses Formularmodell ist ideal, wenn bereits ein Bestand an XFA- oder XDP-basierten Formularen vorhanden ist. Es bietet eine direkte Möglichkeit, Ihre XFA-basierten Formulare in adaptive Formulare zu konvertieren. Alle vorhandenen XFA-Regeln werden in den zugehörigen adaptiven Formularen beibehalten. Die resultierenden adaptiven Formulare unterstützen XFA-Konstrukte wie Überprüfungen, Ereignisse, Eigenschaften und Muster.

* **Verwendung einer XML-Schemadefinition (XSD) oder eines JSON-Schemas** XML- und JSON-Schemas stellen die Struktur dar, in der Daten vom Back-End-System in Ihrem Unternehmen produziert oder genutzt werden. Sie können das Schema mit einem adaptiven Formular verknüpfen und dem Formular mithilfe der Elemente aus dem Schema dynamische Inhalte hinzufügen. Die Elemente des Schemas sind für die Verwendung auf der Registerkarte „Datenmodellobjekte“ des Content Browser verfügbar, wenn sie adaptive Formulare erstellen.

* **Verwenden von &quot;none&quot;oder &quot;without&quot;(Formularmodell)**

Adaptive Formulare, die mit dieser Option erstellt wurden, verwenden kein Formularmodell. Die XML-Datendatei, die aus diesen Formularen generiert wird, hat eine flache Struktur mit Feldern und entsprechenden Werten.

Weitere Informationen zum Erstellen eines adaptiven Formulars finden Sie unter [Erstellen eines adaptiven Formulars](/help/forms/using/creating-adaptive-form.md).

## Benutzeroberfläche für Authoring adaptiver Formulare {#adaptive-form-authoring-ui}

Die Touch-optimierte Benutzeroberfläche für das Authoring adaptiver Formulare ist intuitiv und bietet Folgendes:

* Drag-and-Drop-Funktion
* Standardmäßige Formularkomponenten
* Integriertes Repository für Assets

Wenn Sie ein neues adaptives Formular erstellen oder ein vorhandenes bearbeiten, verwenden Sie die folgenden Elemente der Benutzeroberfläche:

* [Randleiste](#sidebar)
* [Seitensymbolleiste](#page-toolbar)

* [Komponenten-Symbolleiste](#component-toolbar)
* [Seite mit adaptivem Formular](#af-page)

![Benutzeroberfläche für Authoring adaptiver Formulare](assets/formeditor.png)

**A.** Seitenleiste **B.** Seitensymbolleiste **C.** Seite des adaptiven Formulars

### Randleiste {#sidebar}

Die Seitenleiste ermöglicht Ihnen Folgendes:

* Anzeigen von Formularinhalt wie Bereichen, Komponenten, Feldern und Layout.
* Bearbeiten von Komponenteneigenschaften.
* Suchen, Anzeigen und Verwenden von Assets in Ihrem DAM (AEM Digital Asset Management)-Repository.
* Hinzufügen von Komponenten im Formular.

   ![Randleiste](assets/sidebar-comps-2.png)
   [Klicken Sie zum Vergrößern auf](assets/sidebar-comps-2.png)

**A.** Inhalt-Browser **B.** Eigenschaften-Browser **C.** Assets-Browser **D.** Komponenten-Browser

Die Seitenleiste enthält folgende Browser:

* **Inhaltsbrowser**

   Im Inhaltsbrowser können Sie

   * **Formularobjekte**

      Zeigt die Objekthierarchie des Formulars an. Der Autor kann zu bestimmten Formularkomponenten navigieren, indem er auf das entsprechende Element in der Formularobjektstruktur tippt. Der Autor kann in dieser Struktur Objekte suchen und neu anordnen.

   * **Datenmodellobjekte**

      Hiermit können Sie die Formularmodellhierarchie sehen.

      Damit können Sie Formularmodellelemente per Drag &amp; Drop auf das adaptive Formular ziehen. Die hinzugefügten Elemente werden automatisch in Formularkomponenten konvertiert, während ihre ursprünglichen Eigenschaften beibehalten werden. Sie können Datenmodellobjekte anzeigen, wenn Ihr Formular ein XML-Schema, ein JSON-Schema oder eine XDP-Vorlage verwendet.

* **Eigenschaften-Browser**

   Hier können Sie die Eigenschaften einer Komponente bearbeiten. Die Eigenschaften sind je nach Komponente verschieden. So zeigen Sie die Eigenschaften des Containers für adaptive Formulare an:

   Wählen Sie eine Komponente aus, tippen Sie dann auf ![field-level](assets/field-level.png) > **[!UICONTROL Container des adaptiven Formulars]** und anschließend auf ![cmppr](assets/cmppr.png).

* **Assets-Browser**

   Trennt verschiedene Inhaltstypen wie Bilder, Dokumente, Seiten, Filme usw. voneinander.

* **Komponenten-Browser**

   Enthält Komponenten, mit denen Sie ein adaptives Formular erstellen können. Sie können Komponenten in das adaptive Formular ziehen, um Formularelemente hinzuzufügen, und hinzugefügte Elemente gemäß den Anforderungen konfigurieren. In der folgenden Tabelle sind die im Komponenten-Browser aufgelisteten Komponenten beschrieben.

<table> 
 <tbody> 
  <tr> 
   <th><strong>Komponente</strong></th> 
   <th><strong>Funktionen</strong></th> 
  </tr> 
  <tr> 
   <td>Acrobat Sign Block</td> 
   <td>Fügt einen Textblock mit Platzhaltern für Felder hinzu, die beim Signieren mit Acrobat Sign ausgefüllt werden sollen.</td> 
  </tr> 
  <tr> 
   <td>Schaltfläche</td> 
   <td>Fügt eine Schaltfläche hinzu, die Sie konfigurieren können, um Aktionen auszuführen, wie Speichern, Zurücksetzen, Weiter, Zurück usw.</td> 
  </tr> 
  <tr> 
   <td>Captcha</td> 
   <td>Fügt die CAPTCHA-Validierung mithilfe des Google reCAPTCHA-Service hinzu. Weitere Informationen finden Sie unter <a href="/help/forms/using/captcha-adaptive-forms.md" target="_blank">Verwenden von CAPTCHA in adaptiven Formularen</a>.</td> 
  </tr> 
  <tr> 
   <td>Diagramm</td> 
   <td>Fügt ein Diagramm hinzu, das Sie in adaptiven Formularen und Dokumenten zur visuellen Darstellung zweidimensionaler Daten in wiederholbaren Bereichen und Tabellenzeilen verwenden können.</td> 
  </tr> 
  <tr> 
   <td>Kontrollkästchen</td> 
   <td>Fügt ein Kontrollkästchen hinzu.</td> 
  </tr> 
  <tr> 
   <td>Feld zur Datumseingabe</td> 
   <td>Verwenden Sie die Komponente Datumseingabefeld in Ihrem Formular, damit Kunden Tag, Monat und Jahr separat in drei Feldern ausfüllen können. Sie können das Erscheinungsbild der Komponente anpassen und das Datumsformat ändern. Beispielsweise können Sie Ihren Kunden die Eingabe von Datumsangaben im Format MM/TT/JJJJ oder TT/MM/JJJJ gestatten.</td> 
  </tr> 
  <tr> 
   <td>Datumsauswahl</td> 
   <td>Fügt ein Kalenderfeld hinzu, um ein Datum auszuwählen.</td> 
  </tr> 
  <tr> 
   <td>Dokumentfragment</td> 
   <td>Ermöglicht das Hinzufügen wiederverwendbarer Komponenten einer Korrespondenz.</td> 
  </tr> 
  <tr> 
   <td>Dokumentfragmentgruppe</td> 
   <td>Ermöglicht das Hinzufügen einer Gruppe verwandter Dokumentfragmente, die Sie in einer Briefvorlage als Einheit verwenden können.</td> 
  </tr> 
  <tr> 
   <td>Dropdown-Liste</td> 
   <td>Fügt eine Dropdown-Liste für Einzel- oder Mehrfachauswahl hinzu.</td> 
  </tr> 
  <tr> 
   <td>E-Mail</td> 
   <td><p>Fügt ein Feld zum Erfassen der E-Mail-Adresse hinzu. Die E-Mail-Komponente validiert standardmäßig E-Mail-Adressen mit dem folgenden regulären Ausdruck.</p> <p><code>^[a-zA-Z0-9.!#$%&amp;’*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:.[a-zA-Z0-9-]+)*$</code></p> </td> 
  </tr> 
  <tr> 
   <td>Dateianhang</td> 
   <td><p>Fügt eine Schaltfläche hinzu, mit der Benutzende ergänzende Dokumente suchen und an das Formular anhängen können.</p> <p><strong>Hinweis: </strong>Die Dateianlagenkomponente unterstützt einen vordefinierten Satz von Dateiformaten in adaptiven Formularen, die für Acrobat Sign aktiviert sind. Weitere Informationen finden Sie unter <a href="https://helpx.adobe.com/document-cloud/help/supported-file-formats-fill-sign.html">Unterstützte Dateiformate</a>.</p> </td> 
  </tr> 
  <tr> 
   <td>Dateianlagenliste</td> 
   <td>Fügt ein Feld hinzu, das alle mit der Dateianlagenkomponente hochgeladenen Anlagen auflistet.</td> 
  </tr> 
  <tr> 
   <td>Fußzeile<br /> </td> 
   <td>Fügt die Kopfzeile hinzu, die normalerweise das Logo eines Unternehmens, den Titel des Formulars und eine Zusammenfassung enthält.<br /> </td> 
  </tr> 
  <tr> 
   <td>Kopfzeile</td> 
   <td>Fügt die Fußzeile hinzu, die normalerweise Copyright-Informationen und Links zu anderen Seiten enthält. </td> 
  </tr> 
  <tr> 
   <td>Bild</td> 
   <td>Ermöglicht es Ihnen, ein Bild einzufügen.</td> 
  </tr> 
  <tr> 
   <td>Bildauswahl</td> 
   <td>Ermöglicht es Ihren Kunden, ein Bild auszuwählen, um Informationen bereitzustellen. Mithilfe dieser Informationen können Sie Ihren Kunden personalisierte Dienste anbieten.</td> 
  </tr> 
  <tr> 
   <td>Schaltfläche „Weiter“</td> 
   <td>Fügt eine Schaltfläche hinzu, um zum nächsten Bereich in einem Formular zu navigieren.</td> 
  </tr> 
  <tr> 
   <td>Numerisches Feld</td> 
   <td>Fügt ein Feld zum Erfassen numerischer Werte hinzu</td> 
  </tr> 
  <tr> 
   <td>Numerische Schritte</td> 
   <td>Verwenden Sie numerische Schritte in Ihrem Formular, damit Ihre Kunden einen numerischen Wert eingeben können, den sie anhand eines vordefinierten Schritts erhöhen oder verringern können.</td> 
  </tr> 
  <tr> 
   <td>Bereich</td> 
   <td><p>Fügt einen Bereich oder Unterbereich hinzu.</p> <p>Sie können auch eine Bereichskomponente aus der übergeordneten Bedienfeld-Symbolleiste mit der Schaltfläche <span class="uicontrol">Untergeordnetes Bedienfeld hinzufügen</span> hinzufügen. Ebenso können Sie eine bedienfeldspezifische Symbolleiste mit der Schaltfläche <span class="uicontrol">Bedienfeld-Symbolleiste hinzufügen</span> hinzufügen. Sie können die Position der Bedienfeld-Symbolleiste mithilfe des Dialogfelds „Bedienfeld bearbeiten“ konfigurieren.</p> </td> 
  </tr> 
  <tr> 
   <td>Kennwortfeld</td> 
   <td>Fügt ein Feld zum Erfassen eines Kennworts hinzu.</td> 
  </tr> 
  <tr> 
   <td>Schaltfläche "Zurück"</td> 
   <td>Fügt eine Schaltfläche hinzu, die Benutzer benötigen, um zur vorherigen Seite oder zum vorherigen Bedienfeld zurückzukehren.</td> 
  </tr> 
  <tr> 
   <td>Optionsschaltfläche</td> 
   <td>Fügt Optionsfelder hinzu.</td> 
  </tr> 
  <tr> 
   <td>Zurücksetzen-Schaltfläche</td> 
   <td>Fügt eine Schaltfläche zum Zurücksetzen von Formularfeldern hinzu.</td> 
  </tr> 
  <tr> 
   <td>Schaltfläche „Speichern“</td> 
   <td>Fügt eine Schaltfläche zum Speichern von Formulardaten hinzu.</td> 
  </tr> 
  <tr> 
   <td>Freihändige Unterschrift</td> 
   <td>Fügt ein Feld zum Erfassen von Freihandsignaturen hinzu.</td> 
  </tr> 
  <tr> 
   <td>Trennzeichen</td> 
   <td>Aktiviert die visuelle Trennung von Bereichen im Formular.</td> 
  </tr> 
  <tr> 
   <td>Unterschriftsschritt</td> 
   <td>Zeigt die Informationen an, die im Formular bereitgestellt werden, sowie die Signaturfelder, die der Benutzer zum Überprüfen und Signieren des Formulars verwenden kann.</td> 
  </tr> 
  <tr> 
   <td>Text</td> 
   <td>Ermöglicht die Angabe von statischem Text.</td> 
  </tr> 
  <tr> 
   <td>Senden-Schaltfläche</td> 
   <td>Fügt eine Senden-Schaltfläche hinzu, um das Formular an die konfigurierte Sendeaktion zu senden.</td> 
  </tr> 
  <tr> 
   <td>Zusammenfassungsschritt</td> 
   <td>Sendet das Formular und zeigt von den Autoren angegebenen Zusammenfassungstext an, nachdem das Formular gesendet wurde. </td> 
  </tr> 
  <tr> 
   <td>Schalter</td> 
   <td>Fügt einen Schalter hinzu, der einen Umschalter ausführt oder eine Aktion aktiviert/deaktiviert. Sie können nicht mehr als zwei Optionen in der Schalter-Komponente hinzufügen. Da ein Schalter nur zwei Werte haben kann: An und Aus, ist „Obligatorisch“ nicht verfügbar. Mindestens ein Wert wird unabhängig von der Benutzereingabe gespeichert. <br /> </td> 
  </tr> 
  <tr> 
   <td>Tabelle</td> 
   <td>Fügt eine Tabelle hinzu, mit der Sie Daten in Zeilen und Spalten organisieren können. </td> 
  </tr> 
  <tr> 
   <td>Telefonnummer</td> 
   <td><p>Fügt ein Feld zum Erfassen der Telefonnummer hinzu. Mit der Komponente „Telefonnummer“ können Autoren einen der folgenden Telefonnummerntypen konfigurieren. Jeder Typ ist mit einem standardmäßigen regulären Ausdruck für die Validierung verknüpft.</p> 
    <ul> 
     <li>Der Typ „International“ wird durch <code>^[+][0-9]{0,14}$</code> validiert.</li> 
     <li>Der Typ „USPhoneNumber“ wird durch <code>{'+1 ('999') '999-9999}</code> validiert.</li> 
     <li>Der Typ „UKPhoneNumber“ wird durch <code>text{'+'99 999 999 9999}</code> validiert.</li> 
     <li>Der Typ Benutzerdefiniert bietet kein standardmäßiges Überprüfungsmuster. Er nimmt den Wert des zuletzt ausgewählten Telefonnummerntyps an. Sie können auch Ihr eigenes benutzerdefiniertes Überprüfungsmuster angeben.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Geschäftsbedingungen<br /> </td> 
   <td>Fügt ein Feld hinzu, mit dem Autoren die Bedingungen festlegen können, die Benutzer überprüfen können, bevor sie das Formular ausfüllen.</td> 
  </tr> 
  <tr> 
   <td>Textfeld </td> 
   <td><p>Fügt ein Textfeld hinzu, in dem ein Benutzer die erforderlichen Informationen angeben kann. </p> <p>Standardmäßig akzeptiert die Textfeldkomponente nur Text. Sie können die Eingabe von Rich Text in einer Textfeldkomponente ermöglichen. Eine für Rich-Text aktivierte Textkomponente bietet Optionen zum Hinzufügen von Kopfzeilen, zum Ändern von Zeichenstilen (fett, kursiv, unterstreichen die Zeichen), zum Erstellen geordneter und ungeordneter Listen, zum Ändern von Texthintergrund und Textfarbe und zum Hinzufügen von Hyperlinks. Um Rich Text für ein Textfeld zu aktivieren, aktivieren Sie die Option <strong>Rich Text erlauben</strong> in den Komponenteneigenschaften.</p> </td> 
  </tr> 
  <tr> 
   <td>Titel</td> 
   <td>Gibt einen Titel für das adaptive Formular an.</td> 
  </tr> 
  <tr> 
   <td>Überprüfungsschritt</td> 
   <td><p>Fügt einen Platzhalter hinzu, um das ausgefüllte Formular zur Überprüfung durch den Benutzer anzuzeigen.</p> <p><strong>Hinweis</strong>: Das adaptive Formular, das die Überprüfungskomponente enthält, unterstützt keine anonymen Benutzer. Außerdem wird die Verwendung der Überprüfungskomponente in einem adaptiven Formularfragment nicht empfohlen.</p> </td> 
  </tr> 
 </tbody> 
</table>

#### Optimale Verfahren für das Arbeiten mit Komponenten {#best-practices}

Einige Best Practices und wichtige Punkte, die Sie beim Arbeiten mit adaptiven Formularkomponenten beachten sollten, sind:

* Jede Komponente verfügt über zugehörige Eigenschaften, die ihre Darstellung und Funktion steuern. Tippen Sie zum Konfigurieren der Eigenschaften einer Komponente auf die Komponente und auf ![cmppr](assets/cmppr.png), um die Komponenteneigenschaften im Eigenschaftenbrowser zu öffnen.
* Eine Komponente wird mit ihrem Elementnamen gekennzeichnet. Wenn Sie auf ![cmppr](assets/cmppr.png) tippen, können Sie den Namen der Komponente ändern, indem Sie den Wert des Felds **[!UICONTROL Elementname]** im Eigenschaftenbrowser ändern. Im Feld &quot;Elementname&quot;sind nur Buchstaben, Zahlen, Bindestriche (-) und Unterstriche (_) zulässig. Andere Sonderzeichen sind nicht zulässig und der Elementname sollte mit einem Brief beginnen.

* Sie können die title-Eigenschaft einer Komponente eines adaptiven Formulars inline im Formular-Editor ändern, ohne den Eigenschaftenbrowser zu öffnen, solange der Titel im Formular sichtbar ist. Gehen Sie dazu wie folgt vor:

   1. Wählen Sie eine Komponente aus, in der die Eigenschaft **[!UICONTROL Titel]** vorhanden und deren Eigenschaft **[!UICONTROL Titel ausblenden]** deaktiviert ist, indem Sie darauf tippen.
   1. Tippen Sie auf das ![aem_6_3_edit](assets/aem_6_3_edit.png), damit der Titel bearbeitet werden kann.
   1. Ändern Sie den Titel und drücken Sie die Return-Taste oder tippen Sie auf eine beliebige Stelle außerhalb der Komponente, um die Änderungen zu speichern. Drücken Sie die Esc-Taste, um die Änderungen zu verwerfen.

* Bei einigen Komponenten für adaptive Formulare, z. B. E-Mail und Telefon, stehen vordefinierte Überprüfungsmuster zur Verfügung. Sie können jedoch eine benutzerdefinierte Validierung angeben, indem Sie das Feld **[!UICONTROL Validierungsmuster]** unter dem Akkordeon „Muster“ in den Komponenteneigenschaften aktualisieren. Weitere Informationen zu Standardvalidierungen finden Sie in den Komponentenbeschreibungen in der Tabelle oben.

* Adaptive Formularfelder wie &quot;Numerisches Feld&quot;und &quot;E-Mail&quot;können so konfiguriert werden, dass sie spezielle HTML5-Eingabetypen enthalten. Wenn diese Felder auf Mobilgeräten und Tablets im Fokus sind, enthält die Tastatur direkt spezifische Buchstaben, Zahlen und andere Zeichen, die häufig für die Eingabe von Informationen in das betreffende Feld verwendet werden. Damit können Benutzer schnell Informationen eingeben, ohne zwischen Zeichensätzen auf der Tastatur zu wechseln. Um spezielle Eingaben für eine Komponente zu ermöglichen, aktivieren Sie das Kontrollkästchen **[!UICONTROL HTML-Typnummer verwenden]** in den Komponenteneigenschaften.

* Sie können die Eingabe von Rich Text in einer Textfeldkomponente ermöglichen. Um Rich Text für ein Textfeld zu aktivieren, aktivieren Sie das Kontrollkästchen **[!UICONTROL Rich Text zulassen]** in den Komponenteneigenschaften.

* Mithilfe von Textfeld-, E-Mail- und Telefonkomponenten können Sie in Feldern wie Name, Adresse, Kreditkarte, Telefon und E-Mail automatisch Werte aus den Daten übernehmen lassen, die in den Browsereinstellungen für das automatische Ausfüllen gespeichert sind. Um diese Funktion zu aktivieren, wählen Sie **[!UICONTROL Automatisches Ausfüllen aktivieren]** in den Komponenteneigenschaften und ein **[!UICONTROL Attribut für automatisches Ausfüllen]** aus. Wenn ein Benutzer ein adaptives Formular ausfüllt, werden die Werte aus dem Profil zum automatischen Ausfüllen im Browser oder auf der Grundlage der zuvor vom Benutzer ausgefüllten Werte vorgeschlagen. Beachten Sie, dass das automatische Ausfüllen nur funktioniert, wenn die Einstellungen für automatisches Ausfüllen im Browser des Benutzers aktiviert sind.

* Geben Sie in den Komponenteneigenschaften Werte für Optionsfeld- und Kontrollkästchenelemente im Format `{value}={text}` an.
* Die Dateianlagenkomponente ermöglicht es einem Benutzer standardmäßig, nur eine Datei anzuhängen. Sie können die Komponenteneigenschaften jedoch so konfigurieren, dass mehrere Anhänge unterstützt werden. Wenn ein Benutzer mehrere Dateien mit demselben Dateinamen anhängt, können die Anhänge einige Probleme verursachen. Daher wird empfohlen, bei der Formularübermittlung für jeden gesendeten Anhang eine eindeutige Kennung zu verknüpfen. Gehen Sie dazu wie folgt vor:

   1. Navigieren Sie auf Ihrem AEM Forms-Server zu **[!UICONTROL Adobe Experience Manager > Tools > Vorgänge > Webkonsole]**.
   1. Suchen Sie nach **[!UICONTROL Konfigurations-Service für adaptive Formulare]** und tippen Sie darauf.
   1. Aktivieren Sie im Dialog „Konfigurations-Service für adaptive Formulare“ **[!UICONTROL Dateinamen individualisieren]**. Diese Option ist standardmäßig deaktiviert.

* Damit Benutzer eine PDF über den Safari-Browser anhängen können, müssen Sie sicherstellen, dass **[!UICONTROL application/pdf]** wird der Eigenschaft &quot;Unterstützte Dateitypen&quot;der Komponente Dateianhang hinzugefügt. Adaptive Formulare, die mit der vorherigen AEM Forms-Version erstellt wurden, können **[!UICONTROL .pdf]** anstelle von **[!UICONTROL application/pdf]** in der Eigenschaft &quot;Unterstützte Dateitypen&quot;.

Weitere Informationen zum optimalen Arbeiten mit adaptiven Formularen finden Sie unter [Best Practices für die Arbeit mit adaptiven Formularen](/help/forms/using/adaptive-forms-best-practices.md).

>[!NOTE]
>
>Komponenten für adaptive Formulare unterstützen keine RTL-Sprachen (Right to Left – von rechts nach links). Zum Beispiel Hebräisch.

### Seitensymbolleiste {#page-toolbar}

Die Seitensymbolleiste oben bietet Optionen, mit denen Sie eine Vorschau des Formulars anzeigen, Formulareigenschaften ändern und das Formularlayout bearbeiten können. Sie können eine Vorschau des Formulars anzeigen, wenn Sie es erstellen, und entsprechend Änderungen vornehmen. In der Symbolleiste der Seite wird Folgendes angezeigt:

* **[!UICONTROL Seitliches Bedienfeld ein/aus]** ![toggle-side-panel](assets/toggle-side-panel.png): Hiermit können Sie die Seitenleiste ein- oder ausblenden.

* **[!UICONTROL Seiteninformationen]** ![theme-options](assets/theme-options.png): Hier können Sie Seiteneigenschaften anzeigen, ein Formular veröffentlichen bzw. dessen Veröffentlichung zurücknehmen, einen Formular-Workflow starten und ein Formular auf der klassischen Benutzeroberfläche öffnen.

* **[!UICONTROL Emulator]** ![ruler](assets/ruler.png): Hiermit können Sie die Darstellung des Formulars für verschiedene Displaygrößen (z. B. für Tablets und Mobiltelefone) emulieren.

* **[!UICONTROL Bearbeiten]**: Sie können andere Modi auswählen, z. B.: **Bearbeiten, Stile, Entwickler,** und **Design**.

   * **[!UICONTROL Bearbeiten]**: Hiermit können Sie die Eigenschaften des Formulars und seiner Komponenten bearbeiten. Dies tun Sie, indem Sie beispielsweise eine Komponente hinzufügen, ein Bild ablegen oder obligatorische Felder festlegen.
   * **[!UICONTROL Stil]**: Hiermit können Sie das Erscheinungsbild von Komponenten im Formular stilistisch anpassen. Im Stilmodus können Sie beispielsweise einen Bereich auswählen und dessen Hintergrundfarbe festlegen.
   * **[!UICONTROL Entwickler]**: Hier haben Entwickler folgende Möglichkeiten:

      * Erfahren Sie, woraus Formulare bestehen.
      * Debuggen Sie, was wo und wann passiert, was wiederum hilft, Probleme zu lösen.
   * **[!UICONTROL Design]**: Hiermit können Sie benutzerdefinierte Komponenten oder native Komponenten, die nicht in der Seitenleiste aufgeführt sind, aktivieren oder deaktivieren.


* **[!UICONTROL Vorschau]**: Hier können Sie das Aussehen des Formulars bei Veröffentlichung in einer Vorschau anzeigen.

### Komponenten-Symbolleiste {#component-toolbar}

![Komponentensymbolleiste in der Touch-Benutzeroberfläche](assets/component-toolbar.png)

Wenn Sie eine Komponente auswählen, wird eine Symbolleiste angezeigt, über die Sie sie bearbeiten können. Sie erhalten Optionen zum Ausschneiden, Einfügen, Verschieben und Angeben von Eigenschaften der Komponenten. Ihre Optionen sind:

A. **[!UICONTROL Konfigurieren]**: Wenn Sie auf **[!UICONTROL Konfigurieren]** tippen, werden in der Seitenleiste Komponenteneigenschaften sichtbar. Durch die Konfiguration dieser Eigenschaften können Sie die Datenerfassung anpassen. Sie können den Elementnamen der Komponente ändern und den Beschriftungstext im Feld Titel der Komponente angeben. Mit dem Elementnamen können Sie Werte erfassen, die Benutzer mithilfe der Komponente eingeben. In den Komponenteneigenschaften geben Sie das Verhalten der Komponente an und verwalten die Benutzereingabe. Konfigurieren Sie Eigenschaften in der Seitenleiste, um Benutzerdaten zu erfassen und sie für die weitere Verarbeitung zu verwenden. Mit den Eigenschaften für den adaptiven Formularcontainer können Sie Clientbibliotheken, Layouts, Designs, Datensatzdokument-, Speicher-, Sende- und Metadateneinstellungen festlegen.

B. **[!UICONTROL Kopieren]**: Sie können die Kopieroption verwenden, um eine Komponente zu kopieren und an anderen Positionen im Formular einzufügen. Wenn Sie eine Komponente einfügen, erhält die eingefügte Komponente einen neuen Elementnamen, behält jedoch die Eigenschaften der kopierten Komponente bei.

C.**[!UICONTROL Ausschneiden]**: Sie können die Option zum Ausschneiden verwenden, um eine Komponente von einer Position im adaptiven Formular an eine andere Position zu verschieben.

D. **[!UICONTROL Löschen]**: Hiermit können Sie die Komponente aus dem Formular löschen.

E. **[!UICONTROL Einfügen]**: Hiermit können Sie eine Komponente oberhalb der ausgewählten Komponente einfügen.

F. **[!UICONTROL Einfügen]**: Hiermit können Sie die mithilfe der oben genannten Optionen ausgeschnittene oder kopierte Komponente einfügen.

G. **[!UICONTROL Regeln bearbeiten]**: Hiermit können Sie den Regel-Editor öffnen. Weitere Informationen finden Sie unter [Regel-Editor](/help/forms/using/rule-editor.md).

H. **Gruppieren**: Mit dieser Funktion können Sie mehrere Komponenten auswählen, um sie zusammen auszuschneiden, zu kopieren oder einzufügen.

I. **[!UICONTROL Übergeordnet]**: Hier können Sie das übergeordnete Element einer Komponente auswählen. Beispiel: Ein Textfeld, das innerhalb eines Unterabschnitts liegt, der seinerseits Teil eines Abschnitts ist. Der Abschnitt befindet sich im Stammbereich des Handbuchs und der Container des adaptiven Formulars ist das übergeordnete Element eines Stammbereichs für Handbücher. Bei einer Komponente können Sie alle Optionen sehen, wobei die Sortierhierarchie von unten nach oben verläuft.

Wenn Sie beispielsweise für ein Textfeld auf **[!UICONTROL Übergeordnet]** tippen, sehen Sie Folgendes:

* Unterabschnitt
* Abschnitt
* guideRootPanel
* Container für adaptive Formulare

J. **sonstige**: Bietet weitere Optionen zum Arbeiten mit der ausgewählten Komponente.

* SOM-Ausdruck anzeigen
* Speichern eines Bedienfelds als Fragment (nur für Bedienfelder)
* Untergeordnetes Bedienfeld hinzufügen (nur für Bedienfelder)
* Bedienfeld-Symbolleiste hinzufügen (nur für Bereiche)
* Ersetzen (nicht für Bedienfelder)

### Seite mit adaptivem Formular {#af-page}

Die Seite des adaptiven Formulars ist das eigentliche Formular. Sie wird wie jede andere WCM-Seite als WCM-`cq:Page`-Komponente modelliert. Die folgende Abbildung zeigt die Inhaltsstruktur eines typischen adaptiven Formulars an.

![Inhaltstruktur einer WCM-Seite mit adaptivem Formular](assets/afstructure.png)

Die Inhaltsstruktur enthält in der Regel die folgenden Hauptkomponenten:

* **[!UICONTROL guideContainer]**: Der Stamm eines adaptiven Formulars, der als **Beginn eines adaptiven Formulars** in der Benutzeroberfläche des adaptiven Formulars markiert ist. In dieser Komponente können Sie Folgendes angeben:

   * *Mobiles Layout des adaptiven Formulars*: Definiert das Erscheinungsbild des Formulars auf Mobilgeräten.
   * *Dankeseite*: Definiert die Seite, auf die der Benutzer nach dem Senden des Formulars umgeleitet wird.
   * *Übermittlungsaktion*: Definiert, wie das Formular auf dem Server verarbeitet wird, sobald der Benutzer das Formular sendet.
   * *Formatierung*: Gibt den Pfad zur CSS-Datei an, die zum Anpassen des Erscheinungsbilds des Formulars verwendet wird.

* **[!UICONTROL rootPanel]**: Der Stammbereich eines adaptiven Formulars. Sie kann Unterbereiche unter dem Elementknoten enthalten. Jedem Bedienfeld einschließlich des Stammbereichs kann ein Layout zugeordnet sein. Das Layout des Bedienfelds bestimmt das Layout des Formulars. Beispielsweise werden im Akkordeon-Layout die Elemente *als Accordion-Schritte angeordnet.

* **[!UICONTROL toolbar]**: Ein Container für adaptive Formulare verfügt über eine zugehörige globale Symbolleiste, die global für das Formular ist. Diese Symbolleiste kann mit der Aktion **Symbolleiste hinzufügen** in der Bearbeitungsleiste hinzugefügt werden. Damit können Autoren Aktionen wie Übermitteln, Speichern, Zurücksetzen usw. hinzufügen.

* **[!UICONTROL Assets]**: Dieser Knoten enthält zusätzliche Informationen, die für die Formularbearbeitung verwendet werden. Beispiele: Formularmodelldetails, Lokalisierungsdetails usw).
