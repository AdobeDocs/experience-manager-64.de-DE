---
title: Layout-Design
seo-title: Layout Design
description: In den Layoutdesigndetails wird erläutert, wie Sie Layouts erstellen können, die für Ihre Briefe oder interaktive Kommunikation verwendet werden können.
seo-description: Layout Design Details explains how you can create layouts to be used for your letters or Interactive Communications.
uuid: b21af474-07f5-4bfe-af7d-0c322e2452ae
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management, interactive-communications
discoiquuid: 046b1bf9-1ac7-4e2e-ab37-6fe5422dfa20
feature: Correspondence Management
exl-id: 92f90e7f-2869-4201-a927-47de1fc08f5c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1321'
ht-degree: 14%

---

# Layout-Design {#layout-design}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

XFA-Formularvorlagen oder XDPs sind Vorlagen für:

* [Briefe](/help/forms/using/create-letter.md)
* [Druckkanal](/help/forms/using/web-channel-print-channel.md#printchannel) von [Interaktiver Kommunikation](/help/forms/using/interactive-communications-overview.md)

* Layout-Fragmente

Eine XDP wird mit Adobe Forms Designer entwickelt. In diesem Artikel finden Sie Informationen zum Erstellen von XDPs und zum Erstellen einer effektiven Korrespondenz/interaktiven Kommunikation, z. B. wo Formularfelder oder Zielbereiche verwendet werden und wann Layout-Fragmente verwendet werden sollten.

## Erstellen eines Layouts für Briefe oder für den Druckkanal von interaktiver Kommunikation {#creating-a-layout-for-letters-or-for-interactive-communications-print-channel}

Ein Layout bestimmt das grafische Layout eines Briefs/Druckkanals einer interaktiven Kommunikation. Das Layout kann typische Formularfelder wie &quot;Adresse&quot;und &quot;Referenz&quot;enthalten. Es enthält auch leere Unterformulare, die Zielbereiche darstellen. Erstellen Sie das Layout im Formulardesigner. Danach lädt es der Anwendungsspezialist auf den AEM-Server. Von dort können Sie das Layout beim Erstellen einer Korrespondenzvorlage oder eines Druckkanals einer interaktiven Kommunikation auswählen.

![Designer: Layout erstellen](assets/claimsubrogationlayout.png)

Führen Sie die folgenden Schritte aus, um Layouts für Briefe/Druckkanäle der interaktiven Kommunikation zu erstellen:

1. Analysieren Sie das Layout und bestimmen Sie den Inhalt, der auf allen Seiten wiederholt wird. Normalerweise fallen Seitenkopf und -fuß in diese Kategorie. Dieser Inhalt wird auf Übergeordneten Layoutseiten platziert. Der restliche Inhalt wird auf die Textseiten des Layouts übertragen. In einer Richtlinienjacke können das Logo und die Firmenadresse zu Übergeordneten Kopf- und Fußzeilen hinzugefügt werden. Beispielsweise verwendet der Hinweis auf den Abbruch dasselbe Layout.
1. Unterteilen Sie beim Entwerfen von Textseiten den Seiteninhalt in Abschnitte. Jeder Abschnitt ist als Teilformular konzipiert, das in das Layout selbst oder als Fragment-Layout eingebettet ist. Wenn der Abschnitt eine Tabelle enthält, modellieren Sie den Abschnitt als Layout-Fragment.
1. Ein Layout kann wie folgt gestaltet werden:

   1. Machen Sie jeden Abschnitt zu einem separaten Teilformular, das alle Elemente des Abschnitts enthält.
   1. Weisen Sie jedem Abschnitt ein untergeordnetes Teilformular desselben übergeordneten Teilformulars zu. Das Layout des übergeordneten Teilformulars ist auf Fluss eingestellt, damit die Abschnitte unter verschoben werden können, falls große Daten in vorherigen Abschnitten zusammengeführt werden.
   1. Der Primäre Bereich kann auch für andere Layouts wiederverwendet werden. Erstellen Sie es als Fragment-Layout.
   1. Die Details des zusätzlichen Abschnitts enthalten nur zwei Elemente, die untereinander platziert sind, können große Daten enthalten und sind als Fluss konzipiert.
   1. Andere Abschnitte enthalten Elemente an bestimmten Positionen, sodass sie als positioniertes Layout konzipiert sind.
   1. Teilen Sie einen Abschnitt in Teilformulare auf, wenn der Abschnitt Elemente an bestimmten Positionen enthält und diese Elemente große Datenmengen enthalten. Ordnen Sie dann die Teilformulare an, um das gewünschte Verhalten zu erzielen.
   1. Fügen Sie für den Abschnitt &quot;Primärer Aufenthalt&quot;einen Platzhalter-Zielbereich hinzu. Dieser Platzhalter ist zum Zeitpunkt der Erstellung des Briefs/der interaktiven Kommunikation an den Primären Fragmentspeicherort gebunden.
   1. Laden Sie das Layout (und gegebenenfalls das Fragment, das das Layout verwendet) auf den AEM Forms-Server hoch.

## Schema verwenden {#using-schema}

Sie können ein Schema in einem Layout oder Layout-Fragment verwenden, es ist jedoch nicht erforderlich. Wenn Sie ein Schema verwenden, stellen Sie Folgendes sicher:

1. Das Layout und alle Fragmentlayouts, die in einem Brief/interaktiver Kommunikation verwendet werden, verwenden dasselbe Schema wie der Brief/die interaktive Kommunikation.
1. Alle Felder, die mit Daten gefüllt werden müssen, sind an das Schema gebunden.

## Verknüpfungsfähige Felder erstellen {#creating-relatable-fields}

Standardmäßig werden alle Felder als mit verschiedenen anderen Datenquellen verknüpfungsfähig betrachtet. Wenn Ihr Layout Felder enthält, die nicht mit einer Datenquelle verknüpft werden können, geben Sie dem Feld das Suffix &quot;_int&quot;(intern) an. z. B. pageCount_int.

Ein verknüpfungsfähiges Feld muss:

* es muss ein XFA &lt;field> oder &lt;exclGroup> sein
* über einen XFA-Bindungsverweis verfügen
* , wenn es ein &lt;exclgroup>muss mindestens ein untergeordnetes Optionsfeld vorhanden sein; andernfalls kann der Werttyp nicht bestimmt werden

Ein verknüpfungsfähiges Feld muss:

* einen Namen haben

Ein verknüpfungsfähiges Feld darf nicht:

* Fügen Sie ein &quot;_int&quot;-Suffix in seinen Namen ein.
* haben Bindungssatz &quot;none&quot;
* es muss ein untergeordnetes Element eines &lt;exclGroup>-Elements sein

Solange ein verknüpfungsfähiges Feld die oben beschriebenen Kriterien erfüllt, kann es sich an einer beliebigen Position und in jeder Verschachtelungstiefe im Layout befinden. Verknüpfungsfähige Felder können auf Übergeordneten Seiten verwendet werden.

Felder sind in ihrer Layoutkonfiguration flexibler als Zielbereich-Teilformulare. sie sind jedoch an einen einzelnen Werttyp gebunden. Sie können ein Feld vergrößern oder auf eine feste Breite und Höhe usw. festlegen. Das aufgelöste Modul- oder Regelergebnis wird in das Feld übertragen.

## Festlegen der Verwendung von Teilformularen und Textfeldern {#deciding-when-to-use-subforms-and-text-nbsp-fields}

Verwenden Sie ein Teilformular, wenn Sie mehrere Modulinhalte in einem vertikalen Textfluss-Layout von oben nach unten (mehrere Absätze oder Bilder) erfassen möchten. Ihr Layout muss die Tatsache handhaben, dass das Teilformular an die Inhaltsgröße angepasst wird. Wenn Sie nicht sicher sein können, dass die Länge des mit dem Teilformular/der Zielgruppe verknüpften Inhalts nie den für das Teilformular im Layout reservierten Platz überschreitet, erstellen Sie das Teilformular als untergeordnetes Element in einem Container mit einem fließenden Teilformular. Dadurch wird sichergestellt, dass Layout-Objekte unterhalb des Teilformulars beim Vergrößern des Teilformulars nach unten fließen.

Verwenden Sie ein Feld, wenn Sie Moduldaten oder Datenwörterbuchelementdaten im Schema Ihres Layouts erfassen möchten (da die Felder an Daten gebunden sind) oder um Modulinhalte auf einer Übergeordneten Seite anzuzeigen. Beachten Sie, dass sich die Position von Inhalten auf einer Masterseite nicht an die Inhalte einer Hauptteilseite anpasst; stellen Sie also sicher, dass ein Bildfeld als Kopfzeilenlogo verwendet wird. Diese Tabelle enthält weitere Kriterien für die Entscheidung, wann ein Teilformular oder ein Feld in einem Layout verwendet werden soll.

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Voraussetzungen zur Verwendung eines Unterformulars</strong></p> </td> 
   <td><p><strong>Voraussetzungen zur Verwendung eines Textfeldes</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Es enthält eine Kombination von Elementen, z. B. einen Nachnamen und einen Vornamen</p> </td> 
   <td><p>Es enthält ein einzelnes Element, z. B. eine Richtliniennummer.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Es enthält mehrere Absätze</p> </td> 
   <td><p>Text wird umschlossen und ausgerichtet</p> </td> 
  </tr> 
  <tr> 
   <td><p>Sich wiederholende, optionale und bedingte Datengruppen sind an Teilformulare gebunden, um das Risiko von Designfehlern zu verringern, die auftreten könnten, wenn Skripte zum Erzielen der gleichen Ergebnisse verwendet werden</p> </td> 
   <td><p>Elemente wie das Logo und die Adresse Ihres Unternehmens werden auf allen Seiten eines Briefs/einer interaktiven Kommunikation angezeigt. Erstellen Sie in diesem Fall Formularfelder für diese Elemente und platzieren Sie sie auf der Übergeordneten Seite. Wenn Sie die Feldbindung auf "Keine Datenbindung"setzen, werden die Felder "Keine Datenbindung"im Brief-/interaktiven Kommunikations-Editor als verknüpfungsfähige Felder angezeigt. Wenn Sie diesen Feldern einen bestimmten Inhaltstyp zuordnen möchten, müssen sie über Bindungen verfügen.</p> <p>Wenn Ihre Firmenadresse mehr als eine Datenzeile enthält, verwenden Sie das Textfeld mit der Option "Mehrere Zeilen zulassen", um die Adresse im Layout darzustellen.</p> <p>Wenn der Datentyp eines Textfelds auf Nur-Text festgelegt ist, wird die Textversion der Modulausgabe anstelle der Rich-Text-Version verwendet (alle Formatierungen werden verworfen). Damit die Formatierung erhalten bleibt, legen Sie für den Datentyp des Textfelds Rich-Text fest.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Textfluss</p> </td> 
   <td><p>Textfelder und Bildfelder werden auf Übergeordneten Seiten verwendet. Übergeordnete Seiten können keine Teilformulare als Zielbereiche verwenden.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Objekte werden gruppiert und organisiert, ohne das Teilformular an ein Datenelement zu binden</p> </td> 
   <td><p> </p> </td> 
  </tr> 
  <tr> 
   <td><p>Innerhalb des Teilformulars befindet sich ein Textfeld. Das Teilformular kann vergrößert werden und darf andere Objekte unterhalb des Layouts nicht überschreiben.</p> </td> 
   <td><p>Sie benötigen einfachen Zugriff auf die Daten in der Nachbearbeitung.</p> </td> 
  </tr> 
 </tbody> 
</table>

## Sich wiederholende Elemente einrichten {#setting-up-repetitive-elements}

Wenn Elemente wie das Logo und die Adresse Ihres Unternehmens auf allen Seiten eines Briefs/einer interaktiven Kommunikation angezeigt werden, erstellen Sie Formularfelder für diese Elemente und platzieren Sie sie auf der Übergeordneten Seite. Nehmen Sie die Bindung für diese Felder über den Feldnamen vor.

## Geben Sie das Server-Renderformat an {#specify-the-server-nbsp-render-format}

Verwenden Sie das Server-Renderformat des Layouts in das dynamische XML-Formular. ansonsten können Briefe/interaktive Kommunikation, die auf diesem Layout basieren, nicht korrekt dargestellt werden. Das Server-Renderformat ist in Forms Designer standardmäßig auf das dynamische XML-Formular eingestellt. So stellen Sie sicher, dass Sie das richtige Format verwenden:

* Klicken Sie in Designer auf **[!UICONTROL Datei > Formulareigenschaften > Standard]** und stellen Sie sicher, dass die Einstellung &quot;PDF Render/Format&quot;auf &quot;Dynamisches XML-Formular&quot;festgelegt ist.
