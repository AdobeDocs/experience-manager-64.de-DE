---
title: Layout-Design
seo-title: Layout-Design
description: Layout-Designdetails erklären, wie Sie Layouts für Ihre Briefe oder interaktive Kommunikation in Correspondence Management erstellen können.
seo-description: Layout-Design Details erläutern, wie Sie Layouts für Ihre Briefe oder interaktive Kommunikation erstellen können.
uuid: b21af474-07f5-4bfe-af7d-0c322e2452ae
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management, interactive-communications
discoiquuid: 046b1bf9-1ac7-4e2e-ab37-6fe5422dfa20
feature: Korrespondenzverwaltung
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '1307'
ht-degree: 93%

---


# Layout-Design {#layout-design}

XFA-Formularvorlagen oder XDPs sind die Vorlagen für:

* [Briefe](/help/forms/using/create-letter.md)
* [Druckkanal](/help/forms/using/web-channel-print-channel.md#printchannel) von [Interaktiver Kommunikation](/help/forms/using/interactive-communications-overview.md)

* Layout-Fragmente

Eine XDP wird mit Adobe Forms Designer entwickelt. In diesem Artikel finden Sie Informationen zum Entwerfen Ihrer XDPs zum Erstellen effektiver Korrespondenz/Interaktive Kommunikation, z. B. wo Formularfelder oder Zielgruppen verwendet werden und wann Layout-Fragmente verwendet werden.

## Erstellen eines Layouts für Briefe oder für den Druckkanal von interaktiver Kommunikation {#creating-a-layout-for-letters-or-for-interactive-communications-print-channel}

Ein Layout bestimmt das grafische Layout eines Briefs/Druckkanals einer interaktiven Kommunikation. Das Layout kann typische Formularfelder wie „Adresse“ und „Referenz“ enthalten. Es enthält auch leere Unterformulare, die Zielbereiche darstellen. Erstellen Sie das Layout im Formulardesigner. Danach lädt es der Anwendungsspezialist auf den AEM-Server. Von dort können Sie das Layout bei der Erstellung einer Korrespondenzvorlage oder eines Druckkanals einer interaktiven Kommunikation auswählen.

![Designer: Layout erstellen](assets/claimsubrogationlayout.png)

Befolgen Sie diese Schritte, um Layouts für Briefe/Druckkanal einer interaktiven Kommunikation zu erstellen:

1. Analysieren Sie das Layout, und bestimmen Sie den Inhalt, der über alle Seiten wiederholt wird. Normalerweise fallen Seitenkopf- und -fußzeilen in diese Kategorie. Dieser Inhalt wird auf Mustervorlagenseiten des Layouts platziert. Der restliche Inhalt wird in den Hauptteilseiten des Layouts platziert. In einer Richtlinienhülle kann das Logo und die Unternehmensadresse zu den Kopf- und Fußzeilen der Mustervorlagenseite hinzugefügt werden. Beispiel: Abbruchsmitteilung dasselbe Layout.
1. Wenn Sie die Hauptteilseiten entwickeln, teilen Sie den Seiteninhalt in Abschnitte. Jeder Abschnitt wird als Unterformular entwickelt, das im Layout selbst oder als Fragment-Layout eingebettet wird. Wenn der Abschnitt eine Tabelle enthält, modellieren Sie ihn als Fragment-Layout.
1. Ein Layout kann folgendermaßen entwickelt werden:

   1. Machen Sie jeden Bereich zu einem separaten Unterformular mit allen Elementen des Abschnitts.
   1. Machen Sie jeden Abschnitt zu einem untergeordneten Unterformular des gleichen übergeordneten Unterformulars. Das Layout des übergeordneten Unterformulars ist auf Fluss eingestellt, um den Abschnitten das Wechseln zu ermöglichen, wenn große Datenmengen in vorherigen Abschnitten zusammengeführt werden.
   1. Der primäre Standortabschnitt kann auch in anderen Layouts wiederverwendet werden. Erstellen Sie ihn als Fragment-Layout.
   1. Die Details des zusätzlichen Abschnitts enthalten nur zwei Elemente, die untereinander platziert sind, können große Datenmengen enthalten und werden als Fluss entwickelt.
   1. Andere Abschnitte enthalten Elemente an bestimmten Positionen, sodass sie als positioniertes Layout entwickelt werden.
   1. Teilen Sie einen Abschnitt in Unterformulare, wenn der Abschnitt Elemente an bestimmten Positionen enthält und wenn diese Elemente große Datenmengen enthalten. Ordnen Sie dann die Unterformulare an, um das gewünschte Verhalten zu erzielen.
   1. Fügen Sie für den primären Standortabschnitt einen Platzhalter-Zielbereich hinzu. Der Platzhalter ist an den primären Fragmentstandort gebunden, wenn der Brief/die interaktive Kommunikation entwickelt wird.
   1. Laden Sie das Layout (und ggf. das Fragment, das das Layout verwendet) in den AEM Forms-Server hoch.

## Schema verwenden {#using-schema}

Sie können ein Schema in einem Layout oder Fragment-Layout verwenden, was aber nicht erforderlich ist. Wenn Sie ein Schema verwenden, stellen Sie Folgendes sicher:

1. Das Layout und alle Fragment-Layouts, die in einem Brief verwendet werden, verwenden das gleiche Schema wie der Brief/die interaktive Kommunikation.
1. Alle Felder, die mit Daten gefüllt werden müssen, sind an das Schema gebunden.

## Verknüpfungsfähige Felder erstellen {#creating-relatable-fields}

Standardmäßig werden alle Felder als verknüpfungsfähig mit vielen anderen Datenquellen betrachtet. Wenn das Layout Felder enthält, die nicht mit einer Datenquelle verknüpfungsfähig sind, fügen Sie den Namen dieser Felder das Suffix „_int“ (intern) hinzu. Beispiel: pageCount_int.

Ein verknüpfungsfähiges Feld muss folgende Voraussetzungen erfüllen:

* eine XFA- oder &lt;exclGroup>-Variable sein.
* Es muss einen XFA-Bindungsverweis haben.
* Wenn es sich um &lt;exclGroup> handelt, muss es über mindestens ein untergeordnetes Feld für ein Optionsfeld verfügen, andernfalls kann die Art des Wertes nicht ermittelt werden.

Ein verknüpfungsfähiges Feld muss folgende Voraussetzungen erfüllen:

* Es muss einen Namen haben.

Auf ein verknüpfungsfähiges Feld darf Folgendes NICHT zutreffen:

* An den Namen ist das Suffix „_int“ angehängt.
* Das Feld „binding“ ist auf „none“ eingestellt.
* ein untergeordnetes Element eines &lt;exclGroup>-Elements sein

Solange ein verknüpfungsfähiges Feld die oben genannten Kriterien erfüllt, kann es sich im Layout an jeder beliebigen Position und in jeder Verschachtelungstiefe befinden. Verknüpfungsfähige Felder lassen sich auf Masterseiten verwenden.

Felder sind in Bezug auf ihre Layoutkonfiguration flexibler als Unterformulare, die als Zielfelder verwendet werden, allerdings sind Felder an eine einzige Wertart gebunden. Sie können ein Feld in die Breite ziehen oder es mit einer festen Breite oder Höhe einrichten usw. Das aufgelöste Modul- oder Regelergebnis wird in das Feld übernommen.

## Wann sollten Unterformulare, wann Felder verwendet werden  {#deciding-when-to-use-subforms-and-text-nbsp-fields}

Verwenden Sie ein Unterformular für Inhalte aus mehreren Modulen in einem von oben nach unten angeordneten Layout mit vertikalem Fluss (mehrere Absätze oder Bilder). Die Höhe eines Unterformulars nimmt zu, damit es den vorgesehenen Inhalt fassen kann: Achten Sie darauf, dass Ihr Layout diesen Umstand bewältigen kann. Wenn Sie nicht sicher sein können, dass der mit dem Unterformular/dem Zielbereich verknüpfte Inhalt niemals mehr Raum einnimmt als für das Unterformular vorgesehen ist, richten Sie das Unterformular als untergeordnetes Element eines fließenden Unterformular-Containers ein. Damit stellen Sie sicher, dass Layout-Objekte unterhalb des Unterformulars nach unten rücken, wenn die Höhe des Unterformulars zunimmt.

Verwenden Sie ein Feld, wenn Sie Moduldaten oder Daten aus einem Datenlexikonelement in das Schema Ihres Layouts aufnehmen möchten (da Felder mit Daten verknüpft sind) oder wenn Modulinhalte auf einer Masterseite angezeigt werden sollen. Beachten Sie, dass sich die Position von Inhalten auf einer Masterseite nicht an die Inhalte einer Hauptteilseite anpasst; stellen Sie also sicher, dass ein Bildfeld als Kopfzeilenlogo verwendet wird. Die folgende Tabelle enthält weitere Kriterien für die Entscheidung, wann ein Unterformular und wann ein Feld im Layout verwendet werden sollte.

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Voraussetzungen zur Verwendung eines Unterformulars</strong></p> </td> 
   <td><p><strong>Voraussetzungen zur Verwendung eines Textfeldes</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Es enthält eine Kombination einzelner Elemente, z. B. Vorname und Nachname.</p> </td> 
   <td><p>Es enthält ein einzelnes Element, z. B. eine Policennummer.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Es enthält mehrere Absätze.</p> </td> 
   <td><p>Text wird umgebrochen und ausgerichtet.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Sich wiederholende, optionale und bedingte Datengruppen sind mit Unterformularen verknüpft, um das Risiko von Designfehlern zu verringern, wie sie auftreten könnten, wenn Sie zur Erzielung desselben Ergebnisses Skripte verwenden würden.</p> </td> 
   <td><p>Elemente wie das Logo und die Adresse Ihres Unternehmens werden auf allen Seiten eines Brief/der interaktiven Kommunikation angezeigt. Erstellen Sie in einem solchen Fall Formularfelder für die betreffenden Elemente und ordnen Sie die Felder auf der Masterseite an. Wenn Sie das Feld „binding“ auf „Keine Datenbindung“ einstellen, werden im Editor „Kommunikation“ keine Felder als verknüpfungsfähige Felder angezeigt. Wenn Sie mit diesen Feldern jedoch bestimmte Inhaltstypen verknüpfen möchten, muss der Bindungstyp im Feld „binding“ entsprechend eingerichtet werden.</p> <p>Wenn die Firmenadresse mehr als eine Datenzeile umfasst, verwenden Sie das Textfeld mit der Option „Mehrere Zeilen zulassen“, um die Adresse im Layout darzustellen.</p> <p>Wenn der Datentyp eines Textfeldes auf Normaltext eingestellt ist, wird die Normaltextversion der Modulausgabe an Stelle der Rich-Text-Version verwendet (d. h. alle Formatierungen gehen verloren). Wenn die Formatierung erhalten bleiben soll, stellen Sie den Datentyp des Textfeldes auf Rich-Text ein.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Text wird fortlaufend eingefügt (Textfluss).</p> </td> 
   <td><p>Textfelder und Bildfelder werden auf Masterseiten verwendet. Auf Masterseiten können Unterformulare nicht als Zielbereiche verwendet werden.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Objekte werden gruppiert und organisiert, ohne das Unterformular mit einem Datenelement zu verknüpfen.</p> </td> 
   <td><p> </p> </td> 
  </tr> 
  <tr> 
   <td><p>Innerhalb des Unterformulars ist ein Textfeld vorhanden. Das Unterformular kann an Größe zunehmen, ohne darunter angeordnete Layout-Objekte zu überschreiben.</p> </td> 
   <td><p>Sie benötigen einen einfachen Zugriff auf die Daten in der Nachbearbeitung.</p> </td> 
  </tr> 
 </tbody> 
</table>

## Sich wiederholende Elemente einrichten  {#setting-up-repetitive-elements}

Wenn Elemente wie das Logo und die Adresse Ihres Unternehmens auf allen Seiten eines Briefs/einer interaktiven Kommunikation angezeigt werden, erstellen Sie für diese Elemente Formularfelder und platzieren Sie diese auf der Masterseite. Nehmen Sie die Bindung für diese Felder über den Feldnamen vor.

## Server-Renderformat festlegen  {#specify-the-server-nbsp-render-format}

Verwenden Sie das Server-Renderformat des Layouts für das dynamische XML-Formular, andernfalls können Briefe/interaktive Kommunikation, die auf diesem Layout basieren, nicht korrekt gerendert werden. Das Server-Renderformat ist in Forms Designer standardmäßig auf das dynamische XML-Formular eingestellt. Sicherstellen, dass Sie das richtige Format verwenden:

* Klicken Sie in Designer auf **[!UICONTROL Datei > Formulareigenschaften > Standard]** und stellen Sie sicher, dass die Einstellung &quot;PDF-Wiedergabe/Format&quot;auf &quot;Dynamisches XML-Formular&quot;eingestellt ist.

