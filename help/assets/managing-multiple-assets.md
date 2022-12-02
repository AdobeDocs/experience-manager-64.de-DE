---
title: Massenbearbeitung von Metadaten mehrerer Assets und Sammlungen
description: Erfahren Sie, wie Sie die Metadaten vieler Assets und Sammlungen gleichzeitig bearbeiten können, um gängige Metadatenänderungen schnell zu übertragen.
contentOwner: AG
feature: Asset Management,Metadata,Collections
role: User
exl-id: 3541b50a-f226-4a6a-9c2a-03a5f47f1c23
source-git-commit: 937c9425e276f67486fba1d4563799fe68d35cc7
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 77%

---

# Verwalten mehrerer Assets und Sammlungen {#managing-multiple-assets-and-collections}

Erfahren Sie, wie Sie die Metadaten mehrerer Assets und Sammlungen simultan bearbeiten können, um schnell häufige Metadaten-Änderungen zu übertragen.

Mit Adobe Enterprise Manager Assets können Sie die Metadaten mehrerer Assets gleichzeitig bearbeiten, damit Sie häufig vorkommende Metadatenänderungen schnell und stapelweise an Assets übertragen können. Sie können die Metadaten für mehrere Sammlungen zusammen bearbeiten.

Verwenden Sie die Seite „Eigenschaften“, um Metadatenänderungen für mehrere Assets oder Sammlungen durchzuführen:

* Metadateneigenschaften in einen gemeinsamen Wert ändern
* Tags hinzufügen oder ändern

Verwenden Sie zum Anpassen der Seite mit den Metadateneigenschaften, einschließlich Hinzufügen, Ändern und Löschen von Metadateneigenschaften, den Schemaeditor.

>[!NOTE]
>
>Die Massenbearbeitung kann auf Assets angewendet werden, die in einem Ordner oder einer Sammlung enthalten sind. Bei Assets, die in verschiedenen Ordnern verfügbar sind oder gemeinsamen Kriterien entsprechen, können die Metadaten stapelweise aus Asset-Suchergebnissen aktualisiert werden.

## Bearbeiten von Metadateneigenschaften für mehrere Assets {#editing-metadata-properties-of-multiple-assets}

1. Navigieren Sie auf der Assets-Benutzeroberfläche zum Speicherort der Assets, die Sie bearbeiten möchten.
1. Wählen Sie die Assets aus, für die Sie gemeinsame Eigenschaften bearbeiten möchten.
1. Klicken Sie auf der Symbolleiste auf **[!UICONTROL Eigenschaften]**, um für die ausgewählten Assets die Seite „Eigenschaften“ zu öffnen.
1. Ändern Sie die Metadateneigenschaften für ausgewählte Assets auf den verschiedenen Registerkarten.
1. Heben Sie die Auswahl der anderen Assets in der Liste auf, um die Metadaten für ein bestimmtes Asset anzuzeigen. Wenn Sie die Auswahl einiger Assets auf der Seite [!UICONTROL Eigenschaften] abbrechen, werden die Metadaten dieser Assets nicht aktualisiert.
1. Wenn Sie ein anderes Metadatenschema für die Assets wählen möchten, klicken Sie auf der Symbolleiste auf **[!UICONTROL Einstellungen]** und wählen Sie das gewünschte Schema aus. Klicken Sie auf **[!UICONTROL Speichern und schließen]**.
1. Um die neuen Metadaten mit den vorhandenen Metadatenfeldern, die mehrere Werte enthalten, anzuhängen, wählen Sie den **[!UICONTROL Anlagenmodus]**. Wenn Sie diese Option nicht auswählen, ersetzen die neuen Metadaten die vorhandenen Metadaten in den entsprechenden Feldern. Klicken Sie auf **[!UICONTROL Senden]**.

![Massenanwendung des Metadatenschemata auf mehrere Assets](assets/metadata-schema-bulk-edit.gif)

>[!CAUTION]
>
>Bei Feldern, die nur einen einzigen Wert enthalten, werden die neuen Metadaten nicht an den vorhandenen Wert im Feld angehängt, selbst wenn Sie **[!UICONTROL Anlagenmodus]** auswählen.

## Konfigurieren des Grenzwerts für die Metadaten-Massenaktualisierung {#configure-limit-for-bulk-metadata-update}

Um DOS-ähnliche Situationen zu vermeiden, [!DNL Experience Manager] begrenzt die Anzahl der in einer Sling-Anfrage unterstützten Parameter. Wenn Sie die Metadaten vieler Assets auf einmal aktualisieren, erreichen Sie möglicherweise das Limit, sodass die Metadaten für weitere Assets nicht aktualisiert werden können. [!DNL Experience Manager] generiert die folgende Warnung in den Protokollen:

`org.apache.sling.engine.impl.parameters.Util Too many name/value pairs, stopped processing after 10000 entries`

Um das Limit zu ändern, gehen Sie zu **[!UICONTROL Tools > Vorgänge > Web-Konsole]** und ändern Sie den Wert der [!UICONTROL Max. POST-Parameter] in der OSGi-Konfiguration für das [!UICONTROL Parameter-Handling von Apache Sling-Anfragen].

>[!MORELIKETHIS]
>
>* [Stapelweises Bearbeiten der Metadaten mehrerer Sammlungen](managing-collections-touch-ui.md#editing-collection-metadata-in-bulk)

