---
title: Implementieren von Windows 10 Player
seo-title: Implementieren von Windows 10 Player
description: 'Auf dieser Seite erfahren Sie, wie Sie den Windows 10 Player für AEM Screens konfigurieren. '
seo-description: 'Auf dieser Seite erfahren Sie, wie Sie den Windows 10 Player für AEM Screens konfigurieren. '
uuid: cdd7e9f1-f836-4d52-8026-80537a6623ca
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 9b66225a-a893-491b-b47c-ae7b3048ed80
translation-type: tm+mt
source-git-commit: c8694726dc29b391a157db3ef230f21517c957bd

---


# Implementieren von Windows 10 Player{#implementing-windows-player}

Dieser Abschnitt beschreibt, wie der Windows 10-Player für AEM Screens konfiguriert wird. Er enthält Informationen zur Konfigurationsdatei und präsentiert die verfügbaren Optionen und Empfehlungen zu den zum Entwickeln und Testen zu verwendenden Einstellungen.

## Installieren des Windows Players {#installing-windows-player}

Installieren Sie Windows Player für AEM Screens, um den Windows Player für AEM Screens zu implementieren.

Rufen Sie die Seite [**AEM 6.4 Player-Downloads **](https://download.macromedia.com/screens/)auf.

### Ad-hoc-Methode {#ad-hoc-method}

Die Ad-hoc-Methode zur Installation der neuesten Windows Player-Datei (*.exe*) finden Sie auf der Seite [**AEM 6.4 Player-Downloads **](https://download.macromedia.com/screens/).

Nachdem Sie die Anwendung heruntergeladen haben, führen Sie die Schritte im Player aus, um die Ad-hoc-Installation abzuschließen:

1. Halten Sie die linke obere Ecke gedrückt, um den Admin-Bereich zu öffnen.
1. Navigieren Sie im linken Aktionsmenü zu **Konfiguration**, geben Sie den Standort (die Adresse) der AEM-Instanz ein, zu der Sie eine Verbindung aufbauen möchten, und klicken Sie auf **Speichern**.

1. Click on the **Registration** link from the left action menu to complete the device registation process.

### Registrieren mehrere Windows 10-Player mit einer Konfiguration {#registering-multiple-windows-players-with-one-configuration}

Nachdem Sie den Windows Player installiert haben, können Sie mehrere Player mit einer Konfiguration registrieren.

>[!NOTE]
>
>**Massenregistrierung von Windows Playern**
>
>Beim Implementieren von Windows-Playern müssen Sie nicht jeden einzelnen Player manuell konfigurieren. Stattdessen können Sie auch die getestete und zur Bereitstellung bereite JSON-Konfigurationsdatei aktualisieren.
>
>Die Konfiguration stellt sicher, dass alle Player denselben in der Konfigurationsdatei angegebenen Server anpingen. Trotzdem müssen Sie noch jeden einzelnen Player manuell registrieren.

So konfigurieren Sie den Windows 10-Player:

1. Installieren Sie Windows Player.
1. Suchen Sie die Konfigurationsdatei unter ***%appdata%\com.adobe.aem.screens.player\config.json***.
1. Aktualisieren Sie die JSON-Konfigurationsdatei mit den nachstehenden Informationen und kopieren Sie sie dann bei allen Systemen, auf denen der Player vorhanden ist, in den gleichen Ordner.

### Richtlinienattribute    {#policy-attributes}

In der folgenden Tabelle finden Sie eine Zusammenfassung der Richtlinienattribute mit einer beispielhaften JSON-Richtliniendatei als Referenz:

| **Richtlinienname** | **Zweck** |
|---|---|
| server | Die URL zum Adobe Experience Manager(AEM)-Server. |
| resolution | Die Auflösung des Geräts. |
| rebootSchedule | Der Plan zum Neustarten des Players. |
| enableAdminUI | Aktivierung der Administrator-Benutzeroberfläche zum Konfigurieren des Geräts vor Ort. Stellen Sie diesen Wert auf „false“ ein, sobald die Benutzeroberfläche vollständig konfiguriert ist und produktiv verwendet wird. |
| enableOSD | Aktivierung der Kanalschalter-Benutzeroberfläche, damit Benutzer zwischen Kanälen auf dem Gerät wechseln können. Stellen Sie den Wert ggf. auf „false“ ein, sobald die Benutzeroberfläche vollständig konfiguriert ist und produktiv verwendet wird. |
| enableActivityUI | Aktivierung zum Anzeigen des Fortschritts von Aktivitäten wie Downloads und Synchronisierungen. Aktivieren Sie den Wert zwecks Fehlerbehebung und deaktivieren Sie ihn, sobald die Benutzeroberfläche vollständig konfiguriert ist und produktiv verwendet wird. |

#### Beispielhafte JSON-Richtliniendatei    {#example-policy-json-file}

```
{
    "server": "http://localhost:4502",
    "resolution": "auto",
    "rebootSchedule": "at 4:00 am",
    "enableAdminUI": false,
    "enableOSD": false,
    "enableActivityUI": false
}
```

