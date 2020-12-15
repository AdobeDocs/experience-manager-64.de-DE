---
title: Massenbearbeitungsmetadaten mehrerer Assets und Sammlungen
description: Hier erfahren Sie, wie Sie die Metadaten vieler Assets und Sammlungen gleichzeitig bearbeiten, um häufig vorkommende Metadatenänderungen schnell zu übertragen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 97bb17ce719f82449e28f9b32eb651b632b0f8b5
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 77%

---


# Verwalten mehrerer Assets und Sammlungen {#managing-multiple-assets-and-collections}

Erfahren Sie, wie Sie die Metadaten mehrerer Assets und Sammlungen simultan bearbeiten können, um schnell häufige Metadaten-Änderungen zu übertragen.

Mit Adobe Enterprise Manager (AEM) Assets können Sie die Metadaten mehrerer Assets gleichzeitig bearbeiten, sodass Sie allgemeine Metadatenänderungen an Assets zusammen vornehmen können. Sie können die Metadaten für mehrere Sammlungen zusammen bearbeiten.

Verwenden Sie die Seite „Eigenschaften“, um Metadatenänderungen für mehrere Assets oder Sammlungen durchzuführen:

* Metadateneigenschaften in einen gemeinsamen Wert ändern
* Tags hinzufügen oder ändern

Verwenden Sie zum Anpassen der Seite mit den Metadateneigenschaften, einschließlich Hinzufügen, Ändern und Löschen von Metadateneigenschaften, den Schemaeditor.

>[!NOTE]
>
>Die Massenbearbeitung kann auf Assets angewendet werden, die in einem Ordner oder einer Sammlung enthalten sind. Bei Assets, die über mehrere Ordner hinweg verfügbar sind oder die einem allgemeinen Kriterium entsprechen, ist es möglich, die Metadaten stapelweise aus den Asset-Suchergebnissen zu aktualisieren.

## Bearbeiten von Metadateneigenschaften mehrerer Assets {#editing-metadata-properties-of-multiple-assets}

1. Navigieren Sie auf der Assets-Benutzeroberfläche zum Speicherort der Assets, die Sie bearbeiten möchten.
1. Wählen Sie die Assets aus, für die Sie gemeinsame Eigenschaften bearbeiten möchten.
1. Tippen oder klicken Sie auf das Symbol **[!UICONTROL Eigenschaften]**, um die Eigenschaftenseite für die ausgewählten Assets zu öffnen.

   >[!NOTE]
   >
   >Wenn Sie mehrere Assets auswählen, wird die niedrigste gemeinsame übergeordnete Form für die Assets ausgewählt. Anders ausgedrückt, zeigt die Seite &quot;Eigenschaften&quot;nur Metadatenfelder an, die auf den Eigenschaftsseiten aller einzelnen Assets häufig vorkommen.

1. Ändern Sie die Metadateneigenschaften für ausgewählte Assets auf den verschiedenen Registerkarten.
1. Heben Sie die Auswahl der anderen Assets in der Liste auf, um den Metadateneditor für ein bestimmtes Asset anzuzeigen. Die Metadateneditorfelder werden mit den Metadaten für das jeweilige Asset gefüllt.

   >[!NOTE]
   >
   >* Auf der Eigenschaftenseite können Sie Assets aus der Asset-Liste entfernen, indem Sie die Auswahl aufheben. In der Asset-Liste sind alle Assets standardmäßig ausgewählt. Die Metadaten für Assets, die Sie aus der Liste entfernen, werden nicht aktualisiert.
   >* Aktivieren Sie über der Asset-Liste das Kontrollkästchen neben **Titel**, um zwischen der Auswahl von Assets und dem Deaktivieren der Liste umzuschalten.


1. Wenn Sie ein anderes Metadatenschema für die Assets wählen möchten, tippen oder klicken Sie auf das Symbol **[!UICONTROL Einstellungen]** in der Symbolleiste und wählen Sie das gewünschte Schema aus.
1. Speichern Sie die Änderungen.
1. Um die neuen Metadaten mit den vorhandenen Metadatenfeldern, die mehrere Werte enthalten, anzuhängen, wählen Sie den **[!UICONTROL Anlagenmodus]**. Wenn Sie diese Option nicht auswählen, ersetzen die neuen Metadaten die vorhandenen Metadaten in den entsprechenden Feldern. Tippen oder klicken Sie auf **[!UICONTROL Absenden]**.

   >[!CAUTION]
   >
   >Bei Feldern, die nur einen einzigen Wert enthalten, werden die neuen Metadaten nicht an den vorhandenen Wert im Feld angehängt, selbst wenn Sie **[!UICONTROL Anlagenmodus]** auswählen.

## Konfigurieren des Grenzwerts für die Metadaten-Massenaktualisierung {#configure-limit-for-bulk-metadata-update}

Um DOS-ähnliche Situationen zu vermeiden, beschränkt AEM die Anzahl der Parameter, die in einer Sling-Anforderung unterstützt werden. Wenn Sie die Metadaten vieler Assets auf einmal aktualisieren, erreichen Sie möglicherweise den Grenzwert, sodass die Metadaten für weitere Assets nicht aktualisiert werden können. AEM generiert die folgende Warnung in den Protokollen:

`org.apache.sling.engine.impl.parameters.Util Too many name/value pairs, stopped processing after 10000 entries`

Um den Grenzwert zu ändern, rufen Sie **[!UICONTROL Tools > Vorgänge > Web-Konsole]** auf und ändern Sie den Wert von [!UICONTROL Maximale POST Parameter] in [!UICONTROL Apache Sling Request Parameter Handling] OSGi-Konfiguration.

>[!MORELIKETHIS]
>
>* [Metadaten mehrerer Sammlungen stapelweise bearbeiten](managing-collections-touch-ui.md#editing-collection-metadata-in-bulk)