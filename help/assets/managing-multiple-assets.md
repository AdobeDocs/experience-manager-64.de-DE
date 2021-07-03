---
title: Massenbearbeitung von Metadaten mehrerer Assets und Sammlungen
description: Erfahren Sie, wie Sie die Metadaten vieler Assets und Sammlungen gleichzeitig bearbeiten können, um gängige Metadatenänderungen schnell zu übertragen.
contentOwner: AG
feature: Asset-Management,Metadaten,Sammlungen
role: User
exl-id: 3541b50a-f226-4a6a-9c2a-03a5f47f1c23
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 59%

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
>Die Massenbearbeitung kann auf Assets angewendet werden, die in einem Ordner oder einer Sammlung enthalten sind. Bei Assets, die in verschiedenen Ordnern verfügbar sind oder gemeinsamen Kriterien entsprechen, können die Metadaten stapelweise aus Asset-Suchergebnissen aktualisiert werden.

## Bearbeiten von Metadateneigenschaften mehrerer Assets {#editing-metadata-properties-of-multiple-assets}

1. Navigieren Sie auf der Assets-Benutzeroberfläche zum Speicherort der Assets, die Sie bearbeiten möchten.
1. Wählen Sie die Assets aus, für die Sie gemeinsame Eigenschaften bearbeiten möchten.
1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Eigenschaften]** , um die Eigenschaftenseite für die ausgewählten Assets zu öffnen.
1. Ändern Sie die Metadateneigenschaften für ausgewählte Assets auf den verschiedenen Registerkarten.
1. Um die Metadaten eines bestimmten Assets anzuzeigen, brechen Sie die Auswahl der verbleibenden Assets in der Liste ab. Wenn Sie die Auswahl einiger Assets auf der Seite [!UICONTROL Eigenschaften] abbrechen, werden die Metadaten solcher Assets nicht aktualisiert.
1. Um ein anderes Metadatenschema für die Assets auszuwählen, klicken Sie in der Symbolleiste auf **[!UICONTROL Einstellungen]** und wählen Sie ein Schema aus. Klicken Sie auf **[!UICONTROL Speichern und schließen]**.
1. Um die neuen Metadaten mit den vorhandenen Metadatenfeldern, die mehrere Werte enthalten, anzuhängen, wählen Sie den **[!UICONTROL Anlagenmodus]**. Wenn Sie diese Option nicht auswählen, ersetzen die neuen Metadaten die vorhandenen Metadaten in den entsprechenden Feldern. Klicken Sie auf **[!UICONTROL Übermitteln]**.

![Metadatenschema-Bulk wird auf mehrere Assets angewendet](assets/metadata-schema-bulk-edit.gif)

>[!CAUTION]
>
>Bei Feldern, die nur einen einzigen Wert enthalten, werden die neuen Metadaten nicht an den vorhandenen Wert im Feld angehängt, selbst wenn Sie **[!UICONTROL Anlagenmodus]** auswählen.

## Konfigurieren des Grenzwerts für die Metadaten-Massenaktualisierung {#configure-limit-for-bulk-metadata-update}

Um DOS-ähnliche Situationen zu vermeiden, beschränkt AEM die Anzahl der Parameter, die in einer Sling-Anforderung unterstützt werden. Wenn Sie die Metadaten vieler Assets auf einmal aktualisieren, erreichen Sie möglicherweise den Grenzwert, sodass die Metadaten für weitere Assets nicht aktualisiert werden können. AEM generiert die folgende Warnung in den Protokollen:

`org.apache.sling.engine.impl.parameters.Util Too many name/value pairs, stopped processing after 10000 entries`

Um den Grenzwert zu ändern, greifen Sie auf **[!UICONTROL Tools > Vorgänge > Web Console]** zu und ändern Sie den Wert von [!UICONTROL Maximale POST Parameters] in der OSGi-Konfiguration [!UICONTROL Apache Sling Request Parameter Handling].

>[!MORELIKETHIS]
>
>* [Metadaten mehrerer Sammlungen stapelweise bearbeiten](managing-collections-touch-ui.md#editing-collection-metadata-in-bulk)

