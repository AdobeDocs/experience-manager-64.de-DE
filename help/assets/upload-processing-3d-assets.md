---
title: Informationen zum Hochladen und Verarbeiten von 3D-Assets in AEM
seo-title: Informationen zum Hochladen und Verarbeiten von 3D-Assets in AEM
description: Best Practices zum Hochladen und Verarbeiten von 3D-Assets.
seo-description: Best Practices zum Hochladen und Verarbeiten von 3D-Assets.
uuid: d8abf460-adff-4f0f-92ae-2c8651a17488
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: a0319701-21eb-4b7f-8b2e-ac81a7a75875
exl-id: 4b8b0247-0978-40b5-92e2-319cfa44b34e
feature: 3D Assets
role: Business Practitioner
translation-type: tm+mt
source-git-commit: f9faa357f8de92d205f1a297767ba4176cfd1e10
workflow-type: tm+mt
source-wordcount: '868'
ht-degree: 75%

---

# Informationen zum Hochladen und Verarbeiten von 3D-Assets in AEM {#about-the-uploading-and-processing-of-d-assets-in-aem}

>[!IMPORTANT]
>
>AEM 3D in AEM 6.4 wird nicht mehr unterstützt. Adobe empfiehlt, die Funktion für 3D-Elemente in [AEM als Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/dynamicmedia/assets-3d.html#dynamicmedia) oder [AEM 6.5.3 oder höher zu verwenden.](https://experienceleague.adobe.com/docs/experience-manager-65/assets/dynamic/assets-3d.html#dynamic).

Verwenden Sie Standardverfahren zum Hochladen oder Synchronisieren, um 3D-Assets und ihre zugehörigen referenzierten Dateien in AEM Assets zu übertragen.

Informationen hierzu finden Sie unter [Hochladen von Assets](managing-assets-touch-ui.md#uploading-assets).

Adobe empfiehlt, dass Sie alle referenzierten Dateien hochladen, bevor Sie die primäre 3D-Modelldatei hochladen oder gleichzeitig hochladen. Diese Vorgehensweise ist jedoch nicht obligatorisch.

Wenn der Ladevorgang abgeschlossen ist, werden Ihre 3D-Dateien konvertiert und weiter verarbeitet, um das Asset für die Anzeige und das Rendering vorzubereiten.

## Best Practices beim Hochladen von 3D-Assets {#best-practices-for-uploading-d-assets}

* Im Allgemeinen können die 3D-Inhalte in der Ordnerhierarchie von AEM Assets ohne Einschränkungen hochgeladen werden. Bei der automatischen Auflösung von Dateiabhängigkeiten durch AEM 3D bestehen jedoch Umfangbeschränkungen, damit die Zeitdauer für die Suche nach großen Asset-Repositorys gesteuert werden kann. Adobe empfiehlt daher, 3D-Assets und ihre Dateiabhängigkeiten in nahe gelegene Ordner hochzuladen (gemeinsamer auf zweiter Ebene übergeordneter Ordner). Nach Auflösung der Dateiabhängigkeiten können Sie das 3D-Asset und die abhängigen Elemente frei an beliebige Stellen innerhalb des Repositorys bewegen, ohne die erstellten Beziehungen zu verlieren.
* Adobe empfiehlt, *vor* dem Hochladen eine einheitliche Ordnerstruktur für 3D-Inhalte festzulegen. Hier einige Tipps und empfohlene Vorgehensweisen:

   * **Unterhalten Sie für jedes hochzuladende 3D-Asset einen separaten Ordner**.

       Der Ordner enthält die primäre 3D-Modelldatei und alle abhängigen Elemente. Es ist zwar einfach, alle Assets und abhängigen Elemente in einem Ordner zu speichern, jedoch ist das anschließende Suchen nach Inhalten mühsam. Auch die gemeinsame Verwendung von abhängigen Elementen (Texturmaps) in Modellen wird erschwert.

   * **Legen Sie daher die Modelle in einem Ordner und die abhängigen Elemente in einem gleichgeordneten oder untergeordneten Ordner ab**.

      Mit dieser Vorgehensweise wird die Freigabe abhängiger Elemente in den Modellen unterstützt. Wenn die Zahl der Assets groß ist, kann es jedoch schwierig werden, bestimmte Abhängigkeiten zu finden.

   * **Erstellen Sie getrennte, parallele Ordnerhierarchien für Modelle und abhängige Elemente**.

      Sie können modellieren, wie 3D-Authoring-Anwendungen wie Autodesk Maya Inhalte speichern sollen.

* Abhängige Assets sollten erst gelöscht werden, wenn auch die zugehörigen 3D-Assets oder die referenzierenden Assets entfernt wurden. 3D-Assets können jedoch unabhängig von den abhängigen Assets jederzeit gelöscht werden. Falls eine Abhängigkeit versehentlich verloren geht, können Sie die Abhängigkeit auf einfache Weise auflösen und wiederherstellen.

    Siehe „Auflösen von Dateiabhängigkeiten“. 

## Leistungsaspekte beim Hochladen von 3D-Dateien {#performance-considerations-when-uploading-d-files}

In der Regel werden für die Konvertierung und Verarbeitung von 3D-Dateien erhebliche CPU- und Speicherressourcen auf einem Server verbraucht. Außerdem ist der Zeitaufwand beträchtlich. Die Verarbeitungszeiten variieren abhängig von der Größe des Modells und den Fähigkeiten des Servers beträchtlich. Beispiel: Ein typisches kleines Modell mit weniger als 100.000 Flächen kann in der Regel in weniger als einer Minute angezeigt und in 2–3 Minuten vollständig verarbeitet werden. Die Verarbeitung eines größeren Modells mit mehr als einer Million Flächen kann hingegen mehrere Dutzend Minuten in Anspruch nehmen.

Aufträge für Konvertieren, Verarbeiten und Rendern werden so in die Warteschlange gestellt, dass eine übermäßige Verlangsamung des Servers vermieden wird. Die Meldung &quot;Warten auf Verarbeitung...&quot; manchmal in der **[!UICONTROL Ansicht]** angezeigt wird, wenn Sie Assets hochgeladen haben. Dieser Status zeigt, dass andere Verarbeitungs- oder Renderaufträge abgeschlossen werden müssen, bevor das aktuelle Asset verarbeitet wird.

Mit den verfügbaren Verfahren lässt sich die Nutzung der CPU auf die Erfassungsverarbeitung und das Rendern beschränken. Informationen zur Konfiguration der CPU-Grenzwerte finden Sie unter [Erweiterte Konfigurationseinstellungen](advanced-config-3d.md).

## Überwachen des Verarbeitungsstatus Ihrer hochgeladenen 3D-Dateien {#monitoring-the-processing-status-of-your-uploaded-d-files}

Nur in **[!UICONTROL Ansicht]** werden der Verarbeitungsstatus und der Fortschritt als Fortschrittsbanner auf der Asset-Karte angezeigt. Jedes geladene 3D-Modell durchläuft in der Regel die folgenden 4–6 geordneten Verarbeitungsphasen:

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
   <td>Grundlegende anfängliche Verarbeitung und Metadaten-Extraktion.</td> 
  </tr> 
  <tr> 
   <td>2</td> 
   <td>Format konvertieren</td> 
   <td>Das 3D-Modell wird von einem nativen Format (Autodesk® Maya® oder Autodesk® 3ds Max®) in ein Zwischenformat (FBX) konvertiert.</td> 
  </tr> 
  <tr> 
   <td>3</td> 
   <td>Erstellen von Vorschauen</td> 
   <td>Die FBX- oder OBJ-Datei wird erfasst und verarbeitet. Dateiabhängigkeiten werden bei Möglichkeit als Asset-Referenzen ausgewertet und aufgelöst.</td> 
  </tr> 
  <tr> 
   <td>4</td> 
   <td>Erstellen von Schatten</td> 
   <td>Optional. Auf der Ausgangsebene unter dem 3D-Objekt können Sie einen Ambient Occlusion-Schlagschatten generieren. Siehe <a href="/help/assets/advanced-config-3d.md">Erweiterte Konfigurationseinstellungen</a>, um diese Verarbeitung zu aktivieren oder zu deaktivieren.</td> 
  </tr> 
  <tr> 
   <td>5<br /> </td> 
   <td>Erstellen von Lightmaps</td> 
   <td>Optional. Die Qualität der interaktiven Vorschau und des beschleunigten Renderns mit dem Standard-Renderer kann erhöht werden. Siehe <a href="/help/assets/advanced-config-3d.md">Erweiterte Konfigurationseinstellungen</a>, um diese Verarbeitung zu aktivieren oder zu deaktivieren.</td> 
  </tr> 
  <tr> 
   <td>6<br /> </td> 
   <td>Animation erstellen</td> 
   <td>Optional. Hier können Sie eine einfache Animation rendern, die anschließend in der Kartenansicht als visuelle Miniatur verwendet wird. Siehe <a href="/help/assets/advanced-config-3d.md">Erweiterte Konfigurationseinstellungen</a>, um diese Verarbeitung zu aktivieren oder zu deaktivieren.</td> 
  </tr> 
  <tr> 
   <td>7<br /> </td> 
   <td>Warten auf Verarbeitung</td> 
   <td>Wird angezeigt, wenn andere 3D-Assets Verarbeitungspriorität haben. Das sind beispielsweise Assets, die früher geladen wurden, deren Verarbeitung jedoch noch nicht abgeschlossen wurde.</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Sie können ein 3D-Asset in der Ansicht **[!UICONTROL Detail]** oder nach Abschluss der Phase &quot;Erstellen der Vorschau&quot;rendern. Sie müssen nicht warten, bis alle Verarbeitungsphasen abgeschlossen sind.
