---
title: Konfigurieren der Segmentierung mit ContextHub
seo-title: Configuring Segmentation with ContextHub
description: Erfahren Sie, wie Sie die Segmentierung mit ContextHub konfigurieren.
seo-description: Learn how to configure segmentation with Context Hub.
uuid: 196cfb18-317c-443d-b6f1-f559e4221baa
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 6cade87c-9ed5-47d7-9b39-c942268afdad
exl-id: 83e73a5d-c6fa-426a-8476-78769ae7a8c1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1483'
ht-degree: 56%

---

# Konfigurieren der Segmentierung mit ContextHub{#configuring-segmentation-with-contexthub}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

>[!NOTE]
>
>In diesem Abschnitt wird die Konfiguration der Segmentierung bei Verwendung von ContextHub beschrieben. Wenn Sie die ClientContext-Funktion verwenden, lesen Sie die entsprechende Dokumentation für [Konfigurieren der Segmentierung für ClientContext](/help/sites-administering/campaign-segmentation.md).

Die Segmentierung ist bei der Erstellung einer Kampagne eine grundlegende Überlegung. Siehe [Verwalten von Zielgruppen](/help/sites-authoring/managing-audiences.md) für Informationen zur Funktionsweise der Segmentierung und zu Schlüsselbegriffen.

Je nach den von Ihnen bereits zu den Besuchern Ihrer Site erfassten Informationen sowie je nach Ihren angepeilten Zielen müssen Sie die erforderlichen Segmente und Strategien für Ihre zielgerichteten Inhalte festlegen.

Diese Segmente werden dann verwendet, um einem Besucher gezielt bestimmte Inhalte anzuzeigen. Dieser Inhalt wird im Abschnitt [Personalisierung](/help/sites-authoring/personalization.md) der Website verwaltet. Hier festgelegte [Aktivitäten](/help/sites-authoring/activitylib.md) können auf jeder Seite einbezogen werden – und sie können bestimmen, auf welches Besuchersegment die spezialisierten Inhalte angewendet werden sollen.

AEM ermöglicht Ihnen die einfache Personalisierung des Benutzererlebnisses. Außerdem können Sie damit die Ergebnisse Ihrer Segmentdefinitionen überprüfen.

## Zugriff auf Segmente {#accessing-segments}

Die [Zielgruppen](/help/sites-authoring/managing-audiences.md) -Konsole wird verwendet, um Segmente für ContextHub oder ClientContext sowie Zielgruppen für Ihr Adobe Target-Konto zu verwalten. Diese Dokumentation befasst sich mit der Verwaltung von Segmenten für ContextHub. Für [ClientContext-Segmente](/help/sites-administering/campaign-segmentation.md) und Adobe Target-Segmenten, lesen Sie bitte die entsprechende Dokumentation.

Zum Zugriff auf Ihre Segmente wählen Sie in der globalen Navigation die Optionen **Navigation > Personalisierung > Zielgruppen** aus.

![chlimage_1-310](assets/chlimage_1-310.png)

## Segmenteditor {#segment-editor}

Der **Segmenteditor** ermöglicht Ihnen die einfache Veränderung eines Segments. Wählen Sie zur Bearbeitung eines Segments ein Segment aus der [Liste von Segmenten](/help/sites-administering/segmentation.md#accessing-segments) aus und klicken Sie auf die Schaltfläche **Bearbeiten**.

![segmenteditor](assets/segmenteditor.png)

Mithilfe des Komponenten-Browsers können Sie **UND**- und **ODER**-Container zur Festlegung der Segmentlogik und anschließend zusätzliche Komponenten zum Vergleich von Eigenschaften und Werten oder Referenzskripts oder anderen Segmenten zur Definition der Auswahlkriterien (siehe [Erstellen eines neuen Segments](#creating-a-new-segment)) hinzufügen, um das genaue Szenario für die Auswahl des Segments festzulegen.

Wenn die gesamte Anweisung mit „true“ bewertet wurde, wird das Segment aufgelöst. Falls mehrere Segmente zutreffen, wird außerdem der Faktor **Verstärken** verwendet. Unter [Erstellen eines neuen Segments](#creating-a-new-segment) finden Sie weitere Details zum [Faktor „Verstärken“](/help/sites-administering/campaign-segmentation.md#boost-factor).

>[!CAUTION]
>
>Der Segmenteditor prüft nicht auf Zirkelbezüge. Beispiel: Segment A verweist auf ein anderes Segment B, das wiederum auf Segment A verweist. Sie müssen sicherstellen, dass Ihre Segmente keine zirkulären Verweise enthalten.

### Container {#containers}

Die folgenden Container sind standardmäßig verfügbar und ermöglichen es Ihnen, Vergleiche und Verweise für die boolesche Auswertung zusammenzufassen. Sie können vom Komponenten-Browser in den Editor gezogen werden. Im folgenden Abschnitt [Verwenden von UND- und ODER-Containern](/help/sites-administering/segmentation.md#using-and-and-or-containers) erhalten Sie weitere Informationen.

<table> 
 <tbody> 
  <tr> 
   <td>UND-Container<br /> </td> 
   <td>Der boolesche UND-Operator<br /> </td> 
  </tr> 
  <tr> 
   <td>ODER-Container<br /> </td> 
   <td>Der boolesche ODER-Operator</td> 
  </tr> 
 </tbody> 
</table>

### Vergleiche {#comparisons}

Die folgenden Segmentvergleiche sind standardmäßig verfügbar, um Segmenteigenschaften zu bewerten. Sie können vom Komponenten-Browser in den Editor gezogen werden.

<table> 
 <tbody> 
  <tr> 
   <td>Eigenschaft-Wert<br /> </td> 
   <td>Vergleicht eine Eigenschaft eines Geschäfts mit einem definierten Wert<br /> </td> 
  </tr> 
  <tr> 
   <td>Eigenschaft-Eigenschaft</td> 
   <td>Vergleicht eine Eigenschaft eines Geschäfts mit einer anderen Eigenschaft<br /> </td> 
  </tr> 
  <tr> 
   <td>Eigenschaft-Segment-Referenz</td> 
   <td>Vergleicht eine Eigenschaft eines Geschäfts mit einem anderen referenzierten Segment<br /> </td> 
  </tr> 
  <tr> 
   <td>Eigenschaft-Skript-Referenz</td> 
   <td>Vergleicht eine Eigenschaft eines Geschäfts mit den Ergebnissen eines Skripts<br /> </td> 
  </tr> 
  <tr> 
   <td>Segment-Referenz-Skript-Referenz</td> 
   <td>Vergleicht ein referenziertes Segment mit den Ergebnissen eines Skripts<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Ist der Datentyp beim Vergleich von Werten nicht festgesetzt (d. h. auf „auto detect“ eingestellt), vergleicht die Segmentierungs-Engine von ContextHub die Werte einfach auf die Art und Weise, wie auch JavaScript es tun würde. Werte werden nicht auf die erwarteten Typen übertragen, was zu irreführenden Ergebnissen führen kann. Beispiel:
>
>`null < 30 // will return true`
>
>Daher sollten Sie beim [Erstellen eines Segments](/help/sites-administering/segmentation.md#creating-a-new-segment) immer einen **Datentyp** auswählen, wenn die Typen der verglichenen Werte bekannt sind. Beispiel:
>
>Beim Vergleich der Eigenschaft `profile/age` wissen Sie bereits, dass der verglichene Typ **number** sein wird. Selbst wenn `profile/age` nicht festgelegt ist, wird ein Vergleich von `profile/age` unter 30 wie erwartet **false** ergeben.

### Verweise {#references}

Die folgenden Verweise sind standardmäßig verfügbar, um eine direkte Verknüpfung zu einem Skript oder einem anderen Segment herzustellen. Sie können vom Komponenten-Browser in den Editor gezogen werden.

<table> 
 <tbody> 
  <tr> 
   <td>Segment-Referenz<br /> </td> 
   <td>Bewerten Sie das referenzierte Segment.</td> 
  </tr> 
  <tr> 
   <td>Skript-Referenz</td> 
   <td>Bewerten Sie das referenzierte Skript. Weitere Informationen finden Sie im folgenden Abschnitt <a href="/help/sites-administering/segmentation.md#using-script-references">Verwenden von Skript-Referenzen</a>.</td> 
  </tr> 
 </tbody> 
</table>

## Erstellen eines neuen Segments {#creating-a-new-segment}

Festlegen eines neuen Segments

1. Klicken oder tippen Sie nach dem [Zugriff auf die Segmente](/help/sites-administering/segmentation.md#accessing-segments) auf die Schaltfläche „Erstellen“ und wählen Sie **ContextHub-Segment erstellen** aus.

   ![chlimage_1-311](assets/chlimage_1-311.png)

1. Geben Sie unter **Neues ContextHub-Segment** einen Titel für das Segment sowie bei Bedarf einen Verstärkungswert ein und tippen oder klicken Sie auf **Erstellen**.

   ![chlimage_1-312](assets/chlimage_1-312.png)

   Jedes Segment verfügt über einen Verstärkungsparameter, der als Gewichtungsfaktor verwendet wird. Eine höhere Zahl zeigt an, dass das Segment in Instanzen mit mehreren gültigen Segmenten bei der Auswahl gegenüber einem Segment mit einer niedrigeren Zahl bevorzugt wird.

   * Mindestwert: `0`
   * Höchstwert: `1000000`

1. Ziehen Sie einen Vergleich oder Verweis in den Segmenteditor. Der Vergleich oder Verweis wird dann im standardmäßigen UND-Container angezeigt.
1. Doppelklicken oder tippen Sie auf die Konfigurationsoption des neuen Verweises oder Segments, um die spezifischen Parameter zu bearbeiten. In diesem Beispiel testen wir Menschen in San Jose.

   ![screen_shot_2012-02-02at103135am](assets/screen_shot_2012-02-02at103135am.png)

   Legen Sie immer eine **Datentyp** wenn möglich, um sicherzustellen, dass Ihre Vergleiche richtig bewertet werden. Siehe [Vergleiche](/help/sites-administering/segmentation.md#comparisons) für weitere Informationen.

1. Klicken **OK** , um Ihre Definition zu speichern:
1. Fügen Sie bei Bedarf weitere Komponenten hinzu. Sie können boolesche Ausdrücke mithilfe der Container-Komponenten für UND- und ODER-Vergleiche formulieren (siehe [Verwenden von UND- und ODER-Containern](/help/sites-administering/segmentation.md#using-and-and-or-containers) unten). Mit dem Segmenteditor können Sie nicht mehr benötigte Komponenten löschen oder diese an neue Positionen innerhalb der Anweisung ziehen.

### Verwenden von UND- und ODER-Containern {#using-and-and-or-containers}

Mithilfe der UND- und ODER-Container-Komponenten können Sie komplexe Segmente in AEM erstellen. Dabei ist es hilfreich, einige grundlegende Punkte zu beachten:

* Die oberste Ebene der Definition ist immer der ursprünglich erstellte UND-Container. Dies kann nicht verändert werden, hat allerdings auch keine Auswirkungen auf den Rest der Segmentdefinition.
* Stellen Sie sicher, dass die Verschachtelung Ihres Containers sinnvoll ist. Die Container können als die Klammern Ihres booleschen Ausdrucks betrachtet werden.

Das folgende Beispiel wird verwendet, um Besucher auszuwählen, die in unserer Hauptaltersgruppe berücksichtigt werden:

Männlich und zwischen 30 und 59 Jahren

ODER

Weiblich und zwischen 30 und 59 Jahren

Beginnen Sie damit, eine ODER-Container-Komponente innerhalb des standardmäßigen UND-Containers zu platzieren. Fügen Sie innerhalb des ODER-Containers zwei UND-Container hinzu und in diesen wiederum die Eigenschafts- oder Verweiskomponenten.

![screen_shot_2012-02-02at105145am](assets/screen_shot_2012-02-02at105145am.png)

### Verwenden von Skript-Referenzen {#using-script-references}

Mithilfe der Skript-Referenzkomponente kann die Auswertung einer Segmenteigenschaft an ein externes Skript delegiert werden. Sobald das Skript ordnungsgemäß konfiguriert ist, kann es als jede andere Komponente einer Segmentbedingung verwendet werden.

#### Definieren eines Skripts für einen Verweis {#defining-a-script-to-reference}

1. Fügen Sie die Datei zur clientlib `contexthub.segment-engine.scripts` hinzu.
1. Implementieren Sie eine Funktion, die einen Wert zurückgibt. Beispiel:

   ```
   ContextHub.console.log(ContextHub.Shared.timestamp(), '[loading] contexthub.segment-engine.scripts - script.profile-info.js');
   
   (function() {
       'use strict';
   
       /**
        * Sample script returning profile information. Returns user info if data is available, false otherwise.
        *
        * @returns {Boolean}
        */
       var getProfileInfo = function() {
           /* let the SegmentEngine know when script should be re-run */
           this.dependOn(ContextHub.SegmentEngine.Property('profile/age'));
           this.dependOn(ContextHub.SegmentEngine.Property('profile/givenName'));
   
           /* variables */
           var name = ContextHub.get('profile/givenName');
           var age = ContextHub.get('profile/age');
   
           return name === 'Joe' && age === 123;
       };
   
       /* register function */
       ContextHub.SegmentEngine.ScriptManager.register('getProfileInfo', getProfileInfo);
   
   })();
   ```

1. Registrieren Sie das Skript bei `ContextHub.SegmentEngine.ScriptManager.register`.

Wenn das Skript von zusätzlichen Eigenschaften abhängig ist, sollte dieses `this.dependOn()` abrufen. Wenn das Skript beispielsweise von `profile/age` abhängt:

```
this.dependOn(ContextHub.SegmentEngine.Property('profile/age'));
```

#### Verweisen auf ein Skript {#referencing-a-script}

1. Erstellen Sie ein ContextHub-Segment.
1. Hinzufügen **Skript-Referenz** -Komponente an der gewünschten Stelle des Segments.
1. Öffnen Sie das Dialogfeld &quot;Bearbeiten&quot;der **Skript-Referenz** -Komponente. Wenn [ordnungsgemäß konfiguriert](/help/sites-administering/segmentation.md#defining-a-script-to-reference), sollte das Skript im **Skriptname** Dropdown-Liste.

## Testen der Anwendung eines Segments  {#testing-the-application-of-a-segment}

Sobald das Segment definiert wurde, können die potenziellen Ergebnisse mithilfe von **[ContextHub](/help/sites-authoring/ch-previewing.md) getestet werden.**

1. Seitenvorschau
1. Klicken Sie auf das ContextHub-Symbol, um die ContextHub-Symbolleiste anzuzeigen.
1. Wählen Sie eine Persona aus, die dem von Ihnen erstellten Segment entspricht
1. ContextHub löst die entsprechenden Segmente für die ausgewählte Person auf

Beispielsweise ist unsere einfache Segmentdefinition zur Identifizierung von Benutzern in unserer Hauptaltersgruppe eine einfache Segmentdefinition, die auf dem Alter und Geschlecht des Benutzers basiert. Das Laden einer spezifischen Rolle, die mit diesen Kriterien übereinstimmt, zeigt, ob das Segment erfolgreich aufgelöst wurde:

![screen_shot_2012-02-02at105926am](assets/screen_shot_2012-02-02at105926am.png)

Oder ob es nicht aufgelöst wurde:

![screen_shot_2012-02-02at110019am](assets/screen_shot_2012-02-02at110019am.png)

>[!NOTE]
>
>Alle Eigenschaften werden sofort aufgelöst, obwohl sich die meisten beim Neuladen der Seite ändern.

Solche Tests können auch auf Inhaltsseiten und in Kombination mit zielgerichteten Inhalten und damit verbundenen Inhalten durchgeführt werden. **Tätigkeiten** und **Erlebnisse**.

Wenn Sie eine Aktivität und ein Erlebnis mithilfe des obigen Segmentbeispiels für die Hauptseitengruppe eingerichtet haben, können Sie Ihr Segment einfach mit der Aktivität testen. Weitere Informationen zum Einrichten einer Aktivität finden Sie in der entsprechenden [Dokumentation zum Verfassen zielgerichteter Inhalte](/help/sites-authoring/content-targeting-touch.md).

1. Im Bearbeitungsmodus einer Seite, auf der Sie zielgerichtete Inhalte eingerichtet haben, können Sie sehen, dass der Inhalt über das Pfeilsymbol im Inhalt angesprochen wird.

   ![chlimage_1-313](assets/chlimage_1-313.png)

1. Wechseln Sie in den Vorschaumodus und anschließend mithilfe von ContextHub zu einer Rolle, die nicht mit der für das Erlebnis konfigurierten Segmentierung übereinstimmt.

   ![chlimage_1-314](assets/chlimage_1-314.png)

1. Wechseln Sie zu einer Rolle, die nicht mit der für das Erlebnis konfigurierten Segmentierung übereinstimmt, und sehen Sie, wie sich das Erlebnis entsprechend verändert.

   ![chlimage_1-315](assets/chlimage_1-315.png)

## Verwenden Ihres Segments {#using-your-segment}

Segmente werden verwendet, um den tatsächlichen Inhalt zu steuern, der für bestimmte Zielgruppen sichtbar ist. Unter [Verwalten von Zielgruppen](/help/sites-authoring/managing-audiences.md) finden Sie weitere Informationen zu Zielgruppen und Segmenten; unter [Bearbeiten gezielter Inhalte](/help/sites-authoring/content-targeting-touch.md) finden Sie weitere Informationen zur Nutzung von Zielgruppen und Segmenten zur gezielten Platzierung von Inhalten.
