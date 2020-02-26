---
title: Festlegen der Benutzeroberfläche
seo-title: Auswahl der Benutzeroberfläche
description: Legen Sie fest, welche Benutzeroberfläche Sie beim Arbeiten in AEM verwenden möchten.
seo-description: Legen Sie fest, welche Benutzeroberfläche Sie beim Arbeiten in AEM verwenden möchten.
uuid: af956219-178e-477b-a0cd-dd2341ed2ff0
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 9cadec1b-f435-4fd8-b4bc-1a23a0cf11f3
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939

---


# Auswahl der Benutzeroberfläche{#selecting-your-ui}

## Die Benutzeroberfläche

Die Autorenumgebung ermöglicht Folgendes:

* [Bearbeiten](/help/sites-authoring/author.md) (einschließlich [Seitenbearbeitung](/help/sites-authoring/author-environment-tools.md), [Verwaltung von Assets](/help/assets/home.md), [Communities](/help/communities/author-communities.md))

* [Verwaltungsaufgaben](/help/sites-administering/home.md), die Sie für die Erstellung und Verwaltung des Inhalts auf Ihrer Website benötigen

Zu diesem Zweck werden zwei grafische Benutzeroberflächen bereitgestellt. Diese stehen über jeden modernen Browser zur Verfügung.

1. Touch-optimierte Benutzeroberfläche

   * Dies ist die moderne, standardmäßige AEM-Benutzeroberfläche.
   * Sie ist überwiegend in Grau gehalten und zeichnet sich durch ihre klare und minimalistische Gestaltung aus.
   * Sie ist für die Verwendung auf Touch- und Desktop-Geräten konzipiert, entsprechend ist das Aussehen und Verhalten auf allen Geräten gleich. Geringfügige Unterschiede gibt es lediglich beim [Anzeigen und Auswählen von Ressourcen](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources) (tippen statt klicken). 

      * Desktop:
   ![screen_shot_2018-03-23at115248](assets/screen_shot_2018-03-23at115248.png)

   * Tablets (oder Desktop mit einer Breite von weniger als 1024 Pixeln):
   ![screen_shot_2018-03-23at115505](assets/screen_shot_2018-03-23at115505.png)

1. Klassische Benutzeroberfläche

   * Dies ist die vorherige Benutzeroberfläche von AEM.
   * Sie ist vorwiegend in Grün gehalten.
   * Sie wurde für die Nutzung auf Desktop-Geräten entwickelt.
   * Die folgende Dokumentation bezieht sich auf die moderne Benutzeroberfläche. Informationen zur Inhaltserstellung in der klassischen Benutzeroberfläche finden Sie in der [Dokumentation zur Inhaltserstellung für die klassische Benutzeroberfläche](/help/sites-classic-ui-authoring/classicui.md).
   ![chlimage_1-232](assets/chlimage_1-232.png)

## Wechseln der Benutzeroberfläche

Although the touch-enabled UI is now the standard UI and [feature parity](../release-notes/touch-ui-features-status.md) has been nearly reached with the administration and editing of sites, there may be times when the user wishes to switch to the [classic UI](/help/sites-classic-ui-authoring/classicui.md). Dazu stehen mehrere Optionen zur Verfügung.

>[!NOTE]
>
>Weitere Informationen zum Status der Funktionen in der klassischen Benutzeroberfläche finden Sie im Dokument [Funktionsparität bei der Touch-optimierten Benutzeroberfläche](../release-notes/touch-ui-features-status.md).

Sie können an verschiedenen Stellen definieren, welche Benutzeroberfläche verwendet werden soll:

* [Konfigurieren der Standard-Benutzeroberfläche für Ihre Instanz](#configuring-the-default-ui-for-your-instance) - Hiermit wird die Standard-Benutzeroberfläche festgelegt, die bei der Benutzeranmeldung angezeigt wird. Der Benutzer kann dies jedoch überschreiben und eine andere Benutzeroberfläche für sein Konto oder die aktuelle Sitzung auswählen.

* [Einrichten des Authoring der klassischen Benutzeroberfläche für Ihr Konto](/help/sites-authoring/select-ui.md#setting-classic-ui-authoring-for-your-account) - Hiermit wird festgelegt, dass die Benutzeroberfläche beim Bearbeiten von Seiten standardmäßig verwendet wird. Der Benutzer kann dies jedoch überschreiben und eine andere Benutzeroberfläche für sein Konto oder die aktuelle Sitzung auswählen.

* [Wechsel zur klassischen Benutzeroberfläche für die aktuelle Sitzung](#switching-to-classic-ui-for-the-current-session) - Diese Option wechselt zur klassischen Benutzeroberfläche für die aktuelle Sitzung.

* Bei der [Seitenbearbeitung überschreibt das System einige Einstellungen bezüglicher der Benutzeroberfläche](#ui-overrides-for-the-editor).

>[!CAUTION]
>
>Verschiedene Optionen für den Wechsel zur klassischen Benutzeroberfläche sind nicht vorkonfiguriert. Sie müssen speziell für Ihre Instanz konfiguriert werden.
>
>See [Enabling Access to Classic UI](/help/sites-administering/enable-classic-ui.md) for more information.

>[!NOTE]
>
>Instanzen, bei denen ein Upgrade von einer früheren Version durchgeführt wurde, behalten die klassische Benutzeroberfläche für die Seitenbearbeitung bei.
>
>After upgrade, page authoring will not be automatically switched to the touch-enabled UI, but you can configure this using the [OSGi configuration](/help/sites-deploying/configuring-osgi.md) of the **WCM Authoring UI Mode Service** ( `AuthoringUIMode` service). Weitere Informationen dazu finden Sie unter [Benutzeroberflächenüberschreibung für den Editor](#ui-overrides-for-the-editor).

## Configuring the Default UI for Your Instance {#configuring-the-default-ui-for-your-instance}

Ein Systemadministrator kann die bei Start und Anmeldung angezeigte Benutzeroberfläche mit der [Root-Zuordnung](/help/sites-deploying/osgi-configuration-settings.md) konfigurieren.

Diese Einstellungen kann durch Benutzerstandards oder Sitzungseinstellungen überschrieben werden.

## Festlegen der klassischen Autorenbenutzeroberfläche für Ihr Konto {#setting-classic-ui-authoring-for-your-account}

Jeder Benutzer kann über seine [Benutzereinstellungen](/help/sites-authoring/user-properties.md) definieren, ob die klassische Benutzeroberfläche (statt der Standard-Benutzeroberfläche) zur Seitenbearbeitung verwendet werden soll.

Diese Einstellung kann durch Sitzungseinstellungen überschrieben werden.

## Wechseln zur klassischen Benutzeroberfläche für die aktuelle Sitzung {#switching-to-classic-ui-for-the-current-session}

Bei Verwendung der Touch-optimierten Benutzeroberfläche möchten Benutzer vielleicht zur klassischen Benutzeroberfläche (nur für Desktops) zurückzukehren. Es gibt mehrere Methoden, in der aktuellen Sitzung zur klassischen Benutzeroberfläche zu wechseln:

* **Navigationslinks**

   >[!CAUTION]
   >
   >Die Option für den Wechsel zur klassischen Benutzeroberfläche ist nicht vorkonfiguriert. Sie muss speziell für Ihre Instanz konfiguriert werden.
   >
   >
   >See [Enabling Access to Classic UI](/help/sites-administering/enable-classic-ui.md) for more information.

   Wenn diese Funktion aktiviert ist, erscheint immer, wenn Sie die Maus über eine entsprechende Konsole bewegen, ein Symbol (eines Bildschirms). Wenn Sie darauf tippen/klicken, öffnet sich der entsprechende Bereich in der klassischen Benutzeroberfläche.

   Zum Beispiel die Verknüpfungen von **Sites** zu **siteadmin**: 

   ![screen_shot_2018-03-23at11924](assets/screen_shot_2018-03-23at111924.png)

* **URL**

   The classic UI can be accessed using the URL for the welcome screen at `welcome.html`. For example:

   `http://localhost:4502/welcome.html`

   >[!NOTE]
   >
   >Die Touch-optimierte Benutzeroberfläche kann über `sites.html` aufgerufen werden. Beispiel:
   >
   >
   >`http://localhost:4502/sites.html`

### Wechseln zur klassischen Benutzeroberfläche bei der Bearbeitung einer Seite {#switching-to-classic-ui-when-editing-a-page}

>[!CAUTION]
>
>Die Option für den Wechsel zur klassischen Benutzeroberfläche ist nicht vorkonfiguriert. Sie muss speziell für Ihre Instanz konfiguriert werden.
>
>See [Enabling Access to Classic UI](/help/sites-administering/enable-classic-ui.md) for more information.

Sofern aktiviert, ist die Option **Klassische Benutzeroberfläche öffnen** im Dialogfeld **Seiteninformationen** verfügbar: 

![chlimage_1-49](assets/chlimage_1-49.png)

### UI Overrides for the Editor {#ui-overrides-for-the-editor}

Die von einem Benutzer oder Systemadministrator festgelegten Einstellungen können bei der Seitenbearbeitung vom System überschreiben werden.

* Beim Bearbeiten von Seiten:

   * Use of the classic editor is forced when accessing the page using `cf#` in the URL. Beispiel:

      `http://localhost:4502/cf#/content/geometrixx/en/products/triangle.html`

   * Use of the touch-enabled editor is forced when using `/editor.html` in the URL or when using a touch device. Beispiel:

      `http://localhost:4502/editor.html/content/geometrixx/en/products/triangle.html`

* Jede erzwungene Einstellung ist temporär und nur für die aktuelle Browsersitzung gültig.

   * A cookie set will be set dependent on whether touch-enabled ( `editor.html`) or classic ( `cf#`) is used.

* Beim Öffnen von Seiten über `siteadmin` wird nach Folgendem gesucht:

   * dem Cookie
   * einer Benutzervoreinstellung
   * Wenn keines von beiden vorhanden ist, werden standardmäßig die in der [OSGi-Konfiguration](/help/sites-deploying/configuring-osgi.md) des **WCM Authoring UI Mode Service** (`AuthoringUIMode`-Service) festgelegten Definitionen verwendet.

>[!NOTE]
>
>Wenn [ein Benutzer bereits eine Voreinstellung für die Seitenbearbeitung festgelegt hat](#setting-classic-ui-authoring-for-your-account), wird diese nicht durch Änderung der OSGi-Eigenschaft außer Kraft gesetzt.

>[!CAUTION]
>
>Aufgrund der bereits erläuterten Verwendung von Cookies wird von folgenden Aktionen abgeraten:
>
>* Manuelles Bearbeiten der URL. Eine Nicht-Standard-URL könnte zu einer unbekannten Situation und zu Funktionsausfall führen.
>* Verwendung beider Editoren zur selben Zeit, z. B. in separaten Fenstern
>



