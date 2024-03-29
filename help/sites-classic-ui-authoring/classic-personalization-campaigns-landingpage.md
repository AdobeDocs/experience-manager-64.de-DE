---
title: Einstiegsseiten
seo-title: Landing Pages
description: Mit der Funktion für Einstiegsseiten können Sie schnell und einfach ein Design und Inhalte direkt in eine AEM-Seite importieren. Web-Entwickelnde können das HTML und zusätzliche Assets vorbereiten, die als komplette Seite oder nur als Teil einer Seite importiert werden können.
seo-description: The landing pages feature allows quick and easy importing of a design and content right into an AEM page. A web developer can prepare the HTML and additional assets that can be imported as a full page or only a part of a page.
uuid: bd01c7a4-473d-4f0e-8178-a7a937ef983a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 8be3adcf-5b3a-40e9-8f87-1a6f39aab554
exl-id: c8712b93-34b1-421c-8a39-ab9465b05efe
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3183'
ht-degree: 61%

---

# Einstiegsseiten{#landing-pages}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Mit der Funktion für Einstiegsseiten können Sie schnell und einfach ein Design und Inhalte direkt in eine AEM-Seite importieren. Ein Web-Entwickler kann das HTML und zusätzliche Assets vorbereiten, die als komplette Seite oder nur als Teil einer Seite importiert werden können. Die Funktion ist nützlich, um Marketing-Landingpages zu erstellen, die nur für eine begrenzte Zeit aktiv sind und schnell erstellt werden müssen.

Auf dieser Seite wird Folgendes beschrieben:

* Wie Landingpages aussehen AEM Komponenten einschließen?
* Erstellen einer Landingpage und Importieren eines Designpakets
* So arbeiten Sie mit Landingpages in AEM
* Einrichten mobiler Landingpages

Die Vorbereitung des Designpakets für den Import wird im Abschnitt [Erweitern und Konfigurieren des Design Importers](/help/sites-administering/extending-the-design-importer-for-landingpages.md). Die Integration mit Adobe Analytics wird im Abschnitt [Integrieren von Einstiegsseiten in Adobe Analytics.](/help/sites-administering/integrating-landing-pages-with-adobe-analytics.md)

## Was sind Landingpages? {#what-are-landing-pages}

Einstiegsseiten sind Websites mit einer oder mehreren Seiten, die den „Endpunkt“ einer Marketingkampagne darstellen – beispielsweise mit E-Mail, Adwords/Bannern oder sozialen Medien. Eine Landingpage kann verschiedenen Zwecken dienen, hat jedoch alle eine gemeinsame Sache - der Besucher sollte eine Aufgabe erfüllen und den Erfolg einer Landingpage definieren.

Die Landingpage-Funktion in AEM ermöglicht es Marketingexperten, mit Web-Designern in Agenturen oder internen Kreativteams zusammenzuarbeiten, um Seitenentwürfe zu erstellen, die einfach in AEM importiert und von Marketing-Experten bearbeitbar sind und unter der gleichen Verwaltung wie die anderen AEM veröffentlicht werden können.

Gehen Sie AEM wie folgt vor, um Landingpages zu erstellen:

1. Erstellen Sie eine Seite in AEM, die die Leinwandseite für die Einstiegsseiten enthält. Im Lieferumfang von AEM ist ein Beispiel namens **Import-Tool-Seite** enthalten.

1. [Bereiten Sie HTML und Assets vor.](/help/sites-administering/extending-the-design-importer-for-landingpages.md)
1. Komprimieren Sie die Ressourcen in einer ZIP-Datei, die hier als „Designpaket“ bezeichnet wird.
1. Importieren Sie das Designpaket in die Import-Tool-Seite. 
1. Ändern und veröffentlichen Sie die Seite.

### Desktop-Einstiegsseiten {#desktop-landing-pages}

Eine Einstiegsseite in AEM sieht wie folgt aus:

![chlimage_1-3](assets/chlimage_1-3.jpeg)

### Mobile Einstiegsseiten {#mobile-landing-pages}

Eine Einstiegsseite kann auch über eine mobile Version der Seite verfügen. Wenn Sie über eine separate mobile Version der Einstiegsseite verfügen möchten, muss das Importdesign zwei HTML-Dateien aufweisen: *index.htm(l)* und *mobile.index.htm(l)*.

Der Importvorgang für die Einstiegsseite ist identisch mit jenem für eine normale Einstiegsseite, das Einstiegsseiten-Design verfügt über eine zusätzliche HTML-Datei, die der mobilen Einstiegsseite entspricht. Diese HTML-Datei muss genau wie die Desktop-Einstiegsseiten-HTML ebenfalls über ein Leinwand-`div` mit `id=cqcanvas` verfügen und sie unterstützt sämtliche bearbeitbaren Komponenten, die für die Desktop-Einstiegsseite beschrieben sind.

Die mobile Einstiegsseite wird als untergeordnetes Element der Desktop-Einstiegsseite erstellt. Um sie zu öffnen, navigieren Sie zur Landingpage in Websites und öffnen Sie die untergeordnete Seite.

![chlimage_1-42](assets/chlimage_1-42.png)

>[!NOTE]
>
>Die mobile Landingpage wird zusammen mit der Desktop-Landingpage gelöscht/deaktiviert, wenn die Desktop-Landingpage gelöscht oder deaktiviert wird.

## Komponenten der Landingpage {#landing-page-components}

Um Teile des HTML zu markieren, damit diese beim Import in AEM bearbeitbar bleiben, können Sie Inhalt im Einstiegsseiten-HTML direkt AEM-Komponenten zuweisen. Das Design Importer versteht standardmäßig die folgenden Komponenten:

* Text, für Text
* Titel, für Inhalt in H1-6-Tags
* Bild, für Bilder, die austauschbar sein sollen
* Aktionsaufruf:

   * Clickthrough-Link
   * Grafischer Link

* CTA-Lead-Formular, um Benutzerinformationen zu erfassen
* Absatzsystem (Parsys), um das Hinzufügen einer beliebigen Komponente oder das Konvertieren der oben genannten Komponente zu ermöglichen

Außerdem ist es möglich, dies zu erweitern und benutzerdefinierte Komponenten zu unterstützen. In diesem Abschnitt werden die Komponenten detailliert beschrieben.

### Text {#text}

Mit der Text-Komponente können Sie über einen WYSIWYG-Editor einen Textblock eingeben. Siehe [Textkomponente](/help/sites-authoring/default-components.md#text) für weitere Informationen.

![chlimage_1-43](assets/chlimage_1-43.png)

Im Folgenden finden Sie ein Beispiel für eine Text-Komponente auf einer Einstiegsseite:

![chlimage_1-44](assets/chlimage_1-44.png)

### Titel {#title}

In der title-Komponente können Sie einen Titel anzeigen und die Größe konfigurieren (h1-6). Siehe [Titelkomponente](/help/sites-authoring/default-components.md#title) für weitere Informationen.

![chlimage_1-45](assets/chlimage_1-45.png)

Im Folgenden finden Sie ein Beispiel für eine Titel-Komponente auf einer Einstiegsseite:

![chlimage_1-46](assets/chlimage_1-46.png)

### Bild {#image}

Die image-Komponente zeigt ein Bild an, das Sie entweder per Drag-and-Drop aus dem Content Finder ziehen oder per Klick hochladen können. Siehe [Bildkomponente](/help/sites-authoring/default-components.md) für weitere Informationen.

![chlimage_1-47](assets/chlimage_1-47.png)

Im Folgenden finden Sie ein Beispiel für eine Bild-Komponenten auf einer Einstiegsseite:

![chlimage_1-48](assets/chlimage_1-48.png)

### Aktionsaufruf (CTA) {#call-to-action-cta}

Ein Landingpage-Entwurf kann mehrere Links enthalten - einige davon können als &quot;Aktionsaufrufe&quot;gedacht sein.

Aktionsaufrufe (CTA) werden verwendet, um Besucher dazu zu bringen, sofort auf der Landingpage Maßnahmen zu ergreifen, z. B. &quot;Jetzt anmelden&quot;, &quot;Dieses Video anzeigen&quot;, &quot;Nur für begrenzte Zeit&quot;usw.

* Clickthrough-Link - Ermöglicht den Zusatz eines Textlinks, der den Besucher bei Klick zu einer Ziel-URL führt.
* Grafischer Link - Ermöglicht das Hinzufügen eines Bildes, das den Besucher durch Klicken auf eine Ziel-URL weiterleitet.

Beide CTA-Komponenten verfügen über ähnliche Optionen. Der Click Through-Link verfügt über zusätzliche Rich-Text-Optionen. Die Komponenten werden in den folgenden Absätzen ausführlich beschrieben.

### Click Through-Link {#click-through-link}

Diese CTA-Komponente kann dazu verwendet werden, der Einstiegsseite einen Textlink hinzuzufügen. Der Benutzer kann auf den Link klicken und wird dann zur in den Komponenteneigenschaften angegebenen URL weitergeleitet. Sie ist Teil der Gruppe &quot;Aktionsaufruf&quot;.

![chlimage_1-49](assets/chlimage_1-49.png)

**Beschriftung**: Der Text, den Benutzer sehen. Sie können die Formatierung mit dem Rich-Text-Editor anpassen.

**Ziel-URL**: Geben Sie den URI ein, zu dem Benutzer beim Klicken auf den Text weitergeleitet werden sollen.

**Rendering-Optionen**: Beschreibt Render-Optionen. Sie können aus folgenden Optionen auswählen:

* Seite in neuem Browserfenster laden
* Seite in aktuellem Fenster laden
* Seite im übergeordneten Frame laden
* Alle Frames abbrechen und Seite im vollständigen Browser-Fenster laden

**CSS**: Geben Sie auf der Registerkarte „Stil“ einen Pfad zu Ihrem CSS-Stylesheet ein.

**ID**: Geben Sie auf der Registerkarte „Stil“ eine eindeutige ID für die Komponente ein.

Im Folgenden finden Sie ein Beispiel für einen Clickthrough-Link:

![chlimage_1-50](assets/chlimage_1-50.png)

### Grafischer Link {#graphical-link}

Diese CTA-Komponente kann dazu verwendet werden, ein beliebiges grafisches Bild mit Link auf der Einstiegsseite hinzuzufügen. Beim Bild kann es sich um eine einfache Schaltfläche oder um ein grafisches Bild als Hintergrund handeln. Wenn der Benutzer auf das Bild klickt, wird er zur in den Komponenteneigenschaften angegebenen Ziel-URL weitergeleitet. Es ist Teil der **Aktionsaufruf** hinzugefügt.

![chlimage_1-51](assets/chlimage_1-51.png)

**Beschriftung**: Der Text, der Benutzern in der Grafik angezeigt wird. Sie können die Formatierung mit dem Rich-Text-Editor anpassen.

**Ziel-URL**: Geben Sie den URI ein, zu dem Benutzer beim Klicken auf das Bild weitergeleitet werden sollen.

**Rendering-Optionen**: Beschreibt Render-Optionen. Sie können aus folgenden Optionen auswählen:

* Seite in neuem Browserfenster laden
* Seite in aktuellem Fenster laden
* Seite im übergeordneten Frame laden
* Alle Frames abbrechen und Seite im vollständigen Browser-Fenster laden

**CSS**: Geben Sie auf der Registerkarte „Stil“ einen Pfad zu Ihrem CSS-Stylesheet ein.

**ID**: Geben Sie auf der Registerkarte „Stil“ eine eindeutige ID für die Komponente ein.

Im Folgenden finden Sie ein Beispiel für einen grafischen Link:

![chlimage_1-52](assets/chlimage_1-52.png)

## Lead-Formular für Aktionsaufrufe (CTA) {#call-to-action-cta-lead-form}

Ein Lead-Formular ist ein Formular, das dazu verwendet wird, die Informationen eines Besuchers/Leads zu sammeln. Diese Informationen können gespeichert und später dazu verwendet werden, anhand dieser Informationen effizientes Marketing durchzuführen. Die Informationen enthalten im Allgemeinen Titel, Namen, E-Mail, Geburtsdatum, Adresse, Interessen usw. Es ist Teil der **CTA-Lead-Formular** hinzugefügt.

Ein Beispiel für ein CTA-Lead-Formular sieht wie folgt aus:

![chlimage_1-53](assets/chlimage_1-53.png)

CTA-Lead-Formulare bestehen aus verschiedenen Komponenten:

* **Lead-Formular**
Die Lead-Formular-Komponente definiert den Anfang und das Ende eines neuen Lead-Formulars auf einer Seite. Andere Komponenten können dann zwischen diesen Elementen eingefügt werden, z. B. E-Mail-ID und Vorname.

* **Formularfelder und -elemente**
Formularfelder und -elemente können Textfelder, Optionsschaltflächen, Bilder usw. umfassen. Der Benutzer führt oft eine Aktion in einem Formularfeld aus, z. B. Eingabe von Text. Unter den Abschnitten für die einzelnen Formularelemente finden Sie weitere Informationen.

* **Profil-Komponenten**
Profil-Komponenten beziehen sich auf Besucherprofile, die für die Social Collaboration und andere Bereiche verwendet werden, für die eine Personalisierung erforderlich ist.

Oben sehen Sie ein Beispielformular. Es besteht aus der Komponente **Lead-Formular** (Start und Ende) mit den Eingabefeldern **Vorname** und **E-Mail-Adresse** sowie einem Feld **Senden**.

Im Sidekick sind folgende Komponenten für das CTA-Lead-Formular verfügbar:

![chlimage_1-54](assets/chlimage_1-54.png)

### Allgemeine Einstellungen für viele Lead-Formular-Komponenten {#settings-common-to-many-lead-form-components}

Obwohl jede der Lead-Formular-Komponenten einen anderen Zweck hat, bestehen viele aus ähnlichen Optionen und Parametern.

Wenn Sie eine der Formularkomponenten konfigurieren, stehen die folgenden Registerkarten im Dialogfeld zur Verfügung:

* **Titel und Text**
Hier müssen Sie die grundlegenden Informationen angeben, wie den Titel der Komponente und begleitenden Text. Gegebenenfalls können Sie hier auch andere Schlüsselinformationen definieren, z. B. ob für das Feld mehrere Optionen möglich sind und welche Elemente ausgewählt werden können.

* **Anfangswerte**
Ermöglicht Ihnen das Festlegen eines Standardwerts.

* **Beschränkungen**
Hier können Sie angeben, ob ein Feld erforderlich ist, und diese Beschränkungen für dieses Feld platzieren (z. B. ob nur numerische Werte zulässig sind).

* **Stile**
Gibt die Größe und den Stil der Felder an.

>[!NOTE]
>
>Die angezeigten Felder variieren je nach Komponente.
>
>Nicht alle Optionen stehen für alle Lead-Formular-Komponenten zur Verfügung. Weitere Informationen finden Sie unter Forms . [Allgemeine Einstellungen](/help/sites-authoring/default-components.md#formsgroup).

#### Lead-Formularkomponenten {#lead-form-components}

Im folgenden Abschnitt werden die Komponenten beschrieben, die für Aktionsaufruf-Lead-Formulare verfügbar sind.

**Über**: Bietet Benutzern die Möglichkeit, Informationen hinzuzufügen.

![chlimage_1-55](assets/chlimage_1-55.png)

**Adressfeld**: Ermöglicht Benutzern die Eingabe von Adressinformationen. Wenn Sie diese Komponente konfigurieren, müssen Sie im Dialogfeld den Elementnamen eingeben. Der Elementname ist der Name des Formularelements. Gibt an, wo im Repository die Daten gespeichert werden.

![chlimage_1-56](assets/chlimage_1-56.png)

**Geburtsdatum**: Benutzer können das Geburtsdatum eingeben.

![chlimage_1-57](assets/chlimage_1-57.png)

**E-Mail**: Bietet Benutzern die Möglichkeit, eine E-Mail-Adresse (zur Identifikation) einzugeben.

![chlimage_1-58](assets/chlimage_1-58.png)

**Vorname**: Stellt ein Feld bereit, in dem Benutzer ihren Vornamen angeben können.

![chlimage_1-59](assets/chlimage_1-59.png)

**Geschlecht**: Benutzer können ihr Geschlecht aus einer Dropdown-Liste auswählen.

![chlimage_1-60](assets/chlimage_1-60.png)

**Nachname**: Benutzer können Informationen zum Nachnamen eingeben.

![chlimage_1-61](assets/chlimage_1-61.png)

**Formular**: Fügen Sie diese Komponente hinzu, um Ihrer Einstiegsseite ein Lead-Formular hinzuzufügen. Ein Lead-Formular enthält automatisch die Felder „Beginn des Lead-Formulars“ und „Ende des Lead-Formulars“. Zwischen diesen Feldern fügen Sie die in diesem Abschnitt beschriebenen Lead-Formular-Komponenten hinzu.

![chlimage_1-62](assets/chlimage_1-62.png)

Die Lead-Formular-Komponente definiert den Beginn und das Ende eines Formulars mithilfe der Elemente **Formular-Start** und **Formular-Ende**. Diese werden immer gepaart, um sicherzustellen, dass das Formular korrekt definiert ist.

Nachdem Sie das Lead-Formular hinzugefügt haben, können Sie den Beginn des Formulars oder das Ende des Formulars konfigurieren, indem Sie auf **Bearbeiten** in der entsprechenden Leiste.

**Beginn des Lead-Formulars**

Für die Konfiguration sind zwei Registerkarten verfügbar: **Formular** und **Erweitert**:

![chlimage_1-63](assets/chlimage_1-63.png)

**Dankeseite**: Die Seite, auf die verwiesen wird, um Besuchern für ihre Eingabe zu danken. Wenn dies leer gelassen wird, wird das Formular nach der Übermittlung erneut angezeigt.

**Workflow starten**: Bestimmt, welcher Workflow ausgelöst wird, sobald ein Lead-Formular übermittelt wird.

![chlimage_1-64](assets/chlimage_1-64.png)

**Post-Optionen** Die folgenden Post-Optionen sind verfügbar:

* Lead erstellen
* Email Service: Abonnenten erstellen und zur Liste hinzufügen - Verwenden Sie diese Option, wenn Sie einen E-Mail-Dienstanbieter wie ExactTarget verwenden.
* E-Mail-Dienst: Abwesenheitsnachricht senden – Verwenden Sie diese Option, wenn Sie einen E-Mail-Dienstanbieter wie ExactTarget nutzen.
* E-Mail-Dienst: Benutzer von Liste entfernen – Verwenden Sie diese Option, wenn Sie einen E-Mail-Dienstanbieter wie ExactTarget nutzen.
* Benutzer entfernen

**Formular-ID**: Mit der Formular-ID wird das Formular eindeutig gekennzeichnet. Verwenden Sie die Formular-ID, wenn sich mehrere Formulare auf einer Seite befinden. Achten Sie darauf, dass die Formulare unterschiedliche IDs haben.

**Ladepfad**: Dies ist der Pfad zu den Knoteneigenschaften, mit denen vordefinierte Werte in die Formularfelder geladen werden.

Dies ist ein optionales Feld, das den Pfad zu einem Knoten im Repository angibt. Wenn dieser Knoten Eigenschaften hat, die den Feldnamen entsprechen, werden die jeweiligen Felder im Formular vorab mit den Werten dieser Eigenschaften ausgefüllt. Wenn keine Übereinstimmung besteht, steht im Feld der Standardwert.

**Client-Überprüfung**: Gibt an, ob für dieses Formular eine Client-Überprüfung erforderlich ist (eine Server-Überprüfung findet immer statt). Dies kann in Zusammenarbeit mit der Captcha-Formularkomponente geschehen.

**Validierungsressource**: Hiermit wird der Ressourcentyp für die Formularvalidierung definiert, wenn Sie das gesamte Lead-Formular (anstatt einzelne Felder) überprüfen möchten.

Wenn Sie das gesamte Formular überprüfen, führen Sie auch eine der folgenden Aufgaben aus:

* Ein Skript zur Client-Überprüfung:

   ` /apps/<myApp>/form/<myValidation>/formclientvalidation.jsp`

* Ein Skript zur Überprüfung auf der Server-Seite:

   ` /apps/<myApp>/form/<myValidation>/formservervalidation.jsp`

**Aktionskonfiguration**: Je nach Auswahl unter Post-Optionen ändert sich die Aktionskonfiguration. Wenn Sie z. B. „Lead erstellen“ auswählen, können Sie konfigurieren, welcher Liste der Lead hinzugefügt werden soll.

![chlimage_1-65](assets/chlimage_1-65.png)

* **Senden-Schaltfläche einblenden**
Gibt an, ob eine Senden-Schaltfläche angezeigt werden soll.

* **Senden-Name**
Eine ID, die erforderlich ist, wenn Sie mehrere Senden-Schaltflächen in einem Formular verwenden.

* **Senden-Titel**
Der Name, der auf der Schaltfläche angezeigt wird, z. B. „Senden“ oder „Übermitteln“.

* **Zurücksetzen-Schaltfläche einblenden**
Aktivieren Sie das Kontrollkästchen, um die Schaltfläche zum Zurücksetzen einzublenden.

* **Titel zurücksetzen**
Der Name, der auf der Schaltfläche zum Zurücksetzen angezeigt wird.

* **Beschreibung**
Informationen, die unter der Schaltfläche angezeigt werden.

## Erstellen einer Landingpage {#creating-a-landing-page}

Beim Erstellen einer Landingpage müssen Sie drei Schritte ausführen:

1. Erstellen Sie eine Importtool-Seite.
1. [Bereiten Sie den HTML-Code für den Import vor.](/help/sites-administering/extending-the-design-importer-for-landingpages.md)
1. Importieren Sie das Designpaket.

### Erstellen einer Importtool-Seite {#creating-an-importer-page}

Damit Sie Ihr Einstiegsseitendesign importieren können, müssen Sie eine Importtool-Seite erstellen. Dies ist z. B. unter einer Kampagne möglich. Mit der Vorlage „Importtool-Seite“ können Sie Ihre komplette HTML-Einstiegsseite importieren. Die Seite enthält ein Dropdown-Feld, in das das Designpaket der Landingpage per Drag &amp; Drop importiert werden kann.

>[!NOTE]
>
>Standardmäßig kann eine Importtool-Seite nur unter Kampagnen erstellt werden. Sie können diese Vorlage jedoch auch überlagern, um eine Landingpage unter `/content/mysite.`

So erstellen Sie eine neue Landingpage:

1. Navigieren Sie zu **Websites** Konsole.
1. Wählen Sie Ihre Kampagne im linken Bereich aus.
1. Klicken Sie auf **Neu**, um das Fenster **Seite erstellen** zu öffnen.
1. Wählen Sie die Vorlage **Import-Tool-Seite** aus, fügen Sie einen Titel und optional einen Namen hinzu und klicken Sie auf **Erstellen**.

   ![chlimage_1-66](assets/chlimage_1-66.png)

   Ihre neue Importtool-Seite wird angezeigt.

### Vorbereiten der HTML für den Import {#preparing-the-html-for-import}

Vor dem Import des Designpakets muss das HTML vorbereitet werden. Siehe [Erweitern und Konfigurieren des Design-Imports](/help/sites-administering/extending-the-design-importer-for-landingpages.md) für weitere Informationen.

### Importieren des Designpakets {#importing-the-design-package}

Wenn Sie eine Importtool-Seite erstellt haben, können Sie ein Designpaket importieren. Details zum Erstellen des Designpakets und der empfohlenen Struktur werden im Abschnitt [Erweitern und Konfigurieren des Design-Imports](/help/sites-administering/extending-the-design-importer-for-landingpages.md).

Wenn Sie das Designpaket fertig haben, beschreiben die folgenden Schritte, wie Sie das Designpaket auf eine Importtool-Seite importieren.

1. Öffnen Sie die Importtool-Seite, die Sie [früher erstellt](#creatingablankcanvaspage). Sie sehen eine Dropbox mit Text, in der **Zip**.

   ![chlimage_1-67](assets/chlimage_1-67.png)

1. Ziehen Sie das Designpaket per Drag-and-Drop auf den Ablagebereich. Der Pfeil ändert die Richtung, wenn ein Paket darüber gezogen wird.
1. Als Ergebnis des Drag-and-Drop-Vorgangs sehen Sie Ihre Einstiegsseite anstatt der Importtool-Seite. Ihre HTML-Einstiegsseite wurde erfolgreich importiert.

   ![chlimage_1-68](assets/chlimage_1-68.png)

>[!NOTE]
>
>Wenn Sie Probleme beim Importieren des Designpakets haben, lesen Sie [Fehlerbehebung](/help/sites-administering/extending-the-design-importer-for-landingpages.md#troubleshooting).

## Arbeiten mit Landingpages {#working-with-landing-pages}

Das Design und die Assets für eine Einstiegsseite werden im Allgemeinen von einem Designer, häufig in einer Agentur, in branchenüblichen Tools wie Adobe Photoshop oder Adobe Dreamweaver erstellt. Wenn das Design vollständig ist, sendet der Designer eine Zip-Datei mit sämtlichen Assets an die Marketing-Abteilung. Der Kontakt im Marketing ist dann dafür verantwortlich, die ZIP-Datei in AEM abzulegen und den Inhalt zu veröffentlichen.

Außerdem muss der Designer unter Umständen nach dem Import Veränderungen an der Einstiegsseite vornehmen, indem er Inhalte bearbeitet oder löscht und die Aktionsaufruf-Komponenten konfiguriert. Schließlich möchte der Marketing-Experte die Landingpage in der Vorschau ansehen und dann die Kampagne aktivieren, um sicherzustellen, dass die Landingpage veröffentlicht wird.

In diesem Abschnitt werden die folgenden Schritte beschrieben:

* Landingpage löschen
* Herunterladen des Designpakets
* Importinformationen anzeigen
* Zurücksetzen einer Landingpage
* [Konfigurieren der CTA-Komponenten und Hinzufügen von Inhalt zur Seite](#call-to-action-cta)
* Landingpage-Vorschau
* Landingpage aktivieren/publizieren

Wenn Sie das Designpaket importieren, steht oben auf der Landingpage die folgende Symbolleiste zur Verfügung:

![chlimage_1-69](assets/chlimage_1-69.png)

### Herunterladen des importierten Designpakets {#downloading-the-imported-design-package}

Beim Herunterladen der Zip-Datei können Sie aufzeichnen, welche Zip-Datei mit einer bestimmten Einstiegsseite importiert wurde. Beachten Sie, dass auf einer Seite vorgenommene Änderungen nicht der ZIP-Datei hinzugefügt werden.

Um das importierte Designpaket herunterzuladen, klicken Sie auf **Zip herunterladen** in der Symbolleiste der Einstiegsseite.

### Importinformationen anzeigen {#viewing-import-information}

Sie können jederzeit Informationen zum letzten Import anzeigen, indem Sie auf das blaue Ausrufezeichen oben auf der Landingpage in der klassischen Benutzeroberfläche klicken.

![chlimage_1-70](assets/chlimage_1-70.png)

Wenn im importierten Designpaket Probleme auftreten, weil es z. B. auf Bilder/Skripts verweist, die nicht im Paket enthalten sind, werden solche Probleme im Design Importer in Form einer Liste angezeigt. Um die Liste der Probleme anzuzeigen, klicken Sie in der klassischen Benutzeroberfläche in der Symbolleiste der Einstiegsseite auf den Link „Probleme“. Wenn Sie im folgenden Bild auf den Link **Probleme** klicken, wird das Fenster „Probleme beim Import“ geöffnet.

![chlimage_1-4](assets/chlimage_1-4.jpeg)

### Zurücksetzen einer Einstiegsseite {#resetting-a-landing-page}

Wenn Sie das Designpaket für Ihre Einstiegsseite erneut importieren möchten, nachdem Sie Änderungen daran vorgenommen haben, können Sie die Einstiegsseite löschen, indem Sie in der klassischen Benutzeroberfläche am oberen Rand der Einstiegsseite auf **Entfernen** klicken oder in der Touch-optimierten Benutzeroberfläche im Einstellungsmenü auf „Entfernen“ klicken. Dadurch wird die importierte Einstiegsseite gelöscht und stattdessen wird eine leere Import-Tool-Seite erstellt.

Wenn Sie die Einstiegsseite entfernen, können Sie die Inhaltsänderungen löschen. Wenn Sie auf **Nein** klicken, bleiben Inhaltsänderungen erhalten. Das heißt, dass die Struktur unter `jcr:content/importer` beibehalten wird und nur die Import-Tool-Seitenkomponente und die Ressourcen in `etc/design` entfernt werden. Wenn Sie dagegen auf **Ja** klicken, wird `jcr:content/importer` ebenfalls gelöscht.

>[!NOTE]
>
>Wenn Sie sich entscheiden, sämtliche Inhaltsänderungen zu löschen, gehen sämtliche Änderungen, die Sie an der importierten Einstiegsseite vorgenommen haben, sowie sämtliche Seiteneigenschaften verloren, wenn Sie auf **Entfernen** klicken.

### Ändern und Hinzufügen von Komponenten auf einer Landingpage {#modifying-and-adding-components-on-a-landing-page}

Um Komponenten auf der Landingpage zu ändern, doppelklicken Sie darauf, um sie zu öffnen und wie jede andere Komponente zu bearbeiten.

Um Komponenten zur Landingpage hinzuzufügen, ziehen Sie Komponenten per Drag-and-Drop auf die Landingpage - entweder aus dem Sidekick in der klassischen Benutzeroberfläche oder aus dem Bereich Komponenten in der Touch-optimierten Benutzeroberfläche - und bearbeiten Sie sie entsprechend.

>[!NOTE]
>
>Wenn eine Komponente auf der Landingpage nicht bearbeitet werden kann, müssen Sie die ZIP-Datei erneut importieren, nachdem [Ändern der HTML-Datei.](/help/sites-administering/extending-the-design-importer-for-landingpages.md) Das bedeutet, dass die nicht bearbeitbaren Teile während des Imports nicht in AEM Komponenten konvertiert wurden.

### Landingpage löschen {#deleting-a-landing-page}

Das Löschen einer Landingpage entspricht dem Löschen einer normalen AEM.

Die einzige Ausnahme besteht darin, dass beim Löschen einer Desktop-Landingpage auch die entsprechende mobile Landingpage gelöscht wird (sofern vorhanden), nicht aber umgekehrt.

### Landingpage veröffentlichen {#publishing-a-landing-page}

Sie können die Einstiegsseite und sämtliche abhängigen Elemente genau wie eine normale Seite veröffentlichen.

>[!NOTE]
>
>Beim Veröffentlichen einer Desktop-Einstiegsseite wird auch die entsprechende mobile Version veröffentlicht (sofern vorhanden). Bei der Veröffentlichung einer mobilen Landingpage wird die Desktop-Version jedoch nicht veröffentlicht.
