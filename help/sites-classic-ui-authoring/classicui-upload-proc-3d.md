---
title: Informationen zum Hochladen und Verarbeiten von 3D-Assets in AEM
seo-title: Allgemeine Informationen zum Hochladen und Verarbeiten von 3D-Assets in AEM
description: Adobe empfiehlt, alle referenzierten Dateien hochzuladen, bevor oder während Sie die primäre 3D-Modelldatei hochladen. Wenn der Ladevorgang abgeschlossen ist, werden Ihre 3D-Dateien konvertiert und weiter verarbeitet, um das Asset für die Anzeige und das Rendering vorzubereiten.
seo-description: Adobe empfiehlt, alle referenzierten Dateien hochzuladen, bevor oder während Sie die primäre 3D-Modelldatei hochladen. Wenn der Ladevorgang abgeschlossen ist, werden Ihre 3D-Dateien konvertiert und weiter verarbeitet, um das Asset für die Anzeige und das Rendering vorzubereiten.
uuid: 82ccfbf8-1f82-4960-b9e5-3ce65c16435a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 0be4a856-951b-4cb6-8103-8004052c63a0
translation-type: tm+mt
source-git-commit: e0ce860380a28a9dcaa6f8ce94ad278cdbe49fad

---


# Allgemeine Informationen zum Hochladen und Verarbeiten von 3D-Assets in AEM{#about-the-uploading-and-processing-of-d-assets-in-aem}

Verwenden Sie Standardverfahren zum Hochladen oder Synchronisieren, um 3D-Assets und ihre zugehörigen referenzierten Dateien in AEM Assets zu übertragen.

Siehe [Hochladen von Assets](/help/assets/managing-assets-touch-ui.md#uploading-assets).

Adobe empfiehlt, dass Sie alle referenzierten Dateien hochladen, bevor Sie die primäre 3D-Modelldatei hochladen oder gleichzeitig hochladen. Diese Vorgehensweise ist jedoch nicht obligatorisch.

Wenn der Ladevorgang abgeschlossen ist, werden Ihre 3D-Dateien konvertiert und weiter verarbeitet, um das Asset für die Anzeige und das Rendering vorzubereiten.

## Best Practices beim Hochladen von 3D-Assets {#best-practices-for-uploading-d-assets}

* Im Allgemeinen können die 3D-Inhalte in der Ordnerhierarchie von AEM Assets ohne Einschränkungen hochgeladen werden. Bei der automatischen Auflösung von Dateiabhängigkeiten durch AEM 3D bestehen jedoch Umfangbeschränkungen, damit die Zeitdauer für die Suche nach großen Asset-Repositorys gesteuert werden kann. Adobe empfiehlt daher, 3D-Assets und ihre Dateiabhängigkeiten in nahe gelegene Ordner hochzuladen (gemeinsamer auf zweiter Ebene übergeordneter Ordner). Nach Auflösung der Dateiabhängigkeiten können Sie das 3D-Asset und die abhängigen Elemente frei an beliebige Stellen innerhalb des Repositorys bewegen, ohne die erstellten Beziehungen zu verlieren.
* Adobe empfiehlt, dass Sie sich für eine einheitliche Ordnerstruktur für 3D-Inhalte entscheiden, bevor Sie *hochladen. Hier einige Tipps und empfohlene Vorgehensweisen:

   * **Unterhalten Sie für jedes hochzuladende 3D-Asset einen separaten Ordner**.

       Der Ordner enthält die primäre 3D-Modelldatei und alle abhängigen Elemente. Es ist zwar einfach, alle Assets und abhängigen Elemente in einem Ordner zu speichern, jedoch ist das anschließende Suchen nach Inhalten mühsam. Auch die gemeinsame Verwendung von abhängigen Elementen (Texturmaps) in Modellen wird erschwert.

   * **Legen Sie daher die Modelle in einem Ordner und die abhängigen Elemente in einem gleichgeordneten oder untergeordneten Ordner ab**.

      Mit dieser Vorgehensweise wird die Freigabe abhängiger Elemente in den Modellen unterstützt. Wenn die Zahl der Assets groß ist, kann es jedoch schwierig werden, bestimmte Abhängigkeiten zu finden.

   * **Erstellen Sie getrennte, parallele Ordnerhierarchien für Modelle und abhängige Elemente**.

      Sie können modellieren, wie 3D-Authoring-Anwendungen wie Autodesk Maya Inhalte speichern sollen.

* Abhängige Assets sollten erst gelöscht werden, wenn auch die zugehörigen 3D-Assets oder die referenzierenden Assets entfernt wurden. 3D-Assets können jedoch unabhängig von den abhängigen Assets jederzeit gelöscht werden. Falls eine Abhängigkeit versehentlich verloren geht, können Sie die Abhängigkeit auf einfache Weise auflösen und wiederherstellen.

   Siehe [Auflösen von Dateiabhängigkeiten](/help/assets/resolve-file-dependencies.md).

## Leistungsaspekte beim Hochladen von 3D-Dateien {#performance-considerations-when-uploading-d-files}

In der Regel werden für die Konvertierung und Verarbeitung von 3D-Dateien erhebliche CPU- und Speicherressourcen auf einem Server verbraucht. Außerdem ist der Zeitaufwand beträchtlich. Die Verarbeitungszeiten variieren abhängig von der Größe des Modells und den Fähigkeiten des Servers beträchtlich. Beispiel: Ein typisches kleines Modell mit weniger als 100.000 Flächen kann in der Regel in weniger als einer Minute angezeigt und in 2–3 Minuten vollständig verarbeitet werden. Die Verarbeitung eines größeren Modells mit mehr als einer Million Flächen kann hingegen mehrere Dutzend Minuten in Anspruch nehmen.

Aufträge für Konvertieren, Verarbeiten und Rendern werden so in die Warteschlange gestellt, dass eine übermäßige Verlangsamung des Servers vermieden wird. The message &quot;Waiting for processing...&quot; is sometimes shown in the **[!UICONTROL Card View]** at the time you uploaded assets. Dieser Status zeigt, dass andere Verarbeitungs- oder Renderaufträge abgeschlossen werden müssen, bevor das aktuelle Asset verarbeitet wird.

## Überwachen des Verarbeitungsstatus Ihrer hochgeladenen 3D-Dateien {#monitoring-the-processing-status-of-your-uploaded-d-files}

In **[!UICONTROL Card View]** only, the processing status and progression is displayed as a progress banner on the asset&#39;s card. Jedes geladene 3D-Modell durchläuft in der Regel die folgenden 4–6 geordneten Verarbeitungsphasen:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Verarbeitungsstufe</strong><br /> </td> 
   <td><strong>Verarbeitungsnamen</strong></td> 
   <td><strong>Beschreibung</strong></td> 
  </tr> 
  <tr> 
   <td>1</td> 
   <td>Verarbeitung</td> 
   <td>Grundlegende Verarbeitung und Extraktion von Metadaten.</td> 
  </tr> 
  <tr> 
   <td>2</td> 
   <td>Format konvertieren</td> 
   <td>Das 3D-Modell wird von einem nativen Format (Autodesk® Maya® oder Autodesk® 3ds Max®) in ein Zwischenformat (FBX) konvertiert.</td> 
  </tr> 
  <tr> 
   <td>3</td> 
   <td>Vorschau erstellen</td> 
   <td>Die FBX- oder OBJ-Datei wird erfasst und verarbeitet. Dateiabhängigkeiten werden bei Möglichkeit als Asset-Referenzen ausgewertet und aufgelöst.</td> 
  </tr> 
  <tr> 
   <td>4</td> 
   <td>Erstellen von Lightmaps</td> 
   <td>Optional. Damit können Sie die Qualität der interaktiven Vorschau verbessern und das Rendern mit dem Standard-Renderer beschleunigen.</td> 
  </tr> 
  <tr> 
   <td>5</td> 
   <td>Animation erstellen</td> 
   <td>Optional. Damit können Sie eine einfache Animation rendern, die anschließend als visuelle Miniaturansicht in der Kartenansicht verwendet wird.</td> 
  </tr> 
  <tr> 
   <td>6</td> 
   <td>Warten auf Verarbeitung</td> 
   <td>Wird angezeigt, wenn andere 3D-Assets Verarbeitungspriorität haben. Das sind beispielsweise Assets, die früher geladen wurden, deren Verarbeitung jedoch noch nicht abgeschlossen wurde.</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>You can view a 3D asset in **[!UICONTROL Detail View]** or render it after the Creating preview stage is complete. Sie müssen nicht warten, bis alle Verarbeitungsphasen abgeschlossen sind.

