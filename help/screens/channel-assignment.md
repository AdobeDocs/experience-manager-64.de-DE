---
title: Kanalzuweisung
seo-title: Kanalzuweisung
description: Auf dieser Seite erhalten Sie Informationen zur Kanalzuweisung und zu Dayparting.
seo-description: Auf dieser Seite erhalten Sie Informationen zur Kanalzuweisung und zu Dayparting.
uuid: 9ff9ca1c-c7d3-454c-9c65-24c0d40a9a36
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: authoring
discoiquuid: 6303a1fd-8ee7-4565-a0c7-9295a2cd9306
translation-type: tm+mt
source-git-commit: 8145f71848e956647cb4321aaa432b33b9ef9383

---


# Kanalzuweisung {#channel-assignment}

In diesem Abschnitt werden folgende Themen behandelt:

* **Zuweisen von Kanälen**
* **Eigenschaften des Dialogfelds „Kanalzuweisung“**
* **Dayparting**

Nachdem Sie eine Anzeige definiert haben, müssen Sie ihr einen Kanal zuweisen.

Auf dieser Seite wird beschrieben, wie Sie Ihren Anzeigen einen Kanal zuweisen.

**Voraussetzungen**:

* [Konfigurieren und Bereitstellen von Screens](/help/screens/configuring-screens-introduction.md)
* [Erstellen und Verwalten von Screens-Projekten](/help/screens/creating-a-screens-project.md)
* [Erstellen und Verwalten von Kanälen](/help/screens/managing-channels.md)
* [Erstellen und Verwalten von Standorten](/help/screens/managing-locations.md)
* [Erstellen und Verwalten von Anzeigen](/help/screens/managing-displays.md)

## Zuweisen eines Kanals {#assign-a-channel}

Gehen Sie wie folgt vor, um einer Anzeige einen Kanal zuzuweisen:

1. Navigate to the required display, for example, **DemoProject** > **Locations** > **SanJose** > **StoreDisplay**.

   ![screen_shot_2018-08-23at25359pm](assets/screen_shot_2018-08-23at25359pm.png)

1. Tap/click **Assign Channel** in the action bar

   Oder

   Tippen/klicken Sie auf **Dashboard** und klicken Sie auf **+Kanal zuweisen** im Bedienfeld **ZUGEWIESENE KANÄLE**, um das Dialogfeld **Kanalzuweisung** zu öffnen.

   ![screen_shot_2018-08-23at25938pm](assets/screen_shot_2018-08-23at25938pm.png)

   Sie können im Dialogfeld **Kanalzuweisung** die folgenden Eigenschaften konfigurieren:

   **Kanalrolle**:

   In „Kanalrolle“ wird der Kontext der Anzeige definiert. Die Rolle kann durch verschiedene Aktionen festgelegt werden und ist unabhängig vom eigentlichen Kanal, der der Rolle entspricht.

   **Kanal referenzieren**:

   Diese Option ermöglicht es Ihnen, einen Verweis zum gewünschten Kanal bereitzustellen, entweder in Form des Namens oder des Pfads des Kanals.

   * **nach Pfad**: Sie stellen einen expliziten Verweis durch Angabe des absoluten Pfads des Kanals bereit.
   * **nach Name**: Sie geben den Namen des Kanals ein, der entsprechend dem Kontext zu einem tatsächlichen Kanal führt. Mit dieser Funktion können Sie eine lokale Version eines Kanals erstellen, um standortspezifischen Inhalt dynamisch aufzulösen. Beispiel: ein Kanal mit dem Namen *Tagesangebote*, bei dem der eigentliche Inhalt in zwei Städten zwar unterschiedlich ist, aber bei allen Anzeigen dieselbe Kanalrolle vorhanden ist.
   **Priorität:**

   Mit „Priorität“ können Zuweisungen geordnet werden, falls mehrere die Wiedergabekriterien erfüllen. Höhere Werte haben stets Vorrang vor niedrigeren Werten. Wenn es beispielsweise die beiden Kanäle A und B gibt und A eine Priorität von 1 und B eine Priorität von 2 hat, wird Kanal B angezeigt, da er eine höhere Priorität als A hat.

   Die Priorität eines Kanals wird als Zahl (1 für Minimum) im Dialogfeld „Kanalzuweisung“ festgelegt, wie oben angegeben. Darüber hinaus werden die zugewiesenen Kanäle nach absteigender Priorität sortiert.

   **Unterstützte Ereignisse**:

   * **Erster Ladevorgang**: Lädt den Kanal, wenn der Player gestartet wird. Dies kann in Kombination mit einem Zeitplan mehreren Kanälen zugewiesen werden.
   * **Bildschirm bei Untätigkeit**: Lädt, wenn der Bildschirm inaktiv ist. Dies kann in Kombination mit einem Zeitplan mehreren Kanälen zugewiesen werden.
   * **Timer**: Muss eingestellt werden, wenn ein Zeitplan vorhanden ist
   * **Benutzerinteraktion**: Der Player wechselt in den angegebenen Kanal, wenn in einem inaktiven Kanal auf dem Bildschirm (Touch) eine Benutzerinteraktion stattfindet, und wird geladen, wenn der Bildschirm berührt wird.
   **Zeitplan**:

   Hiermit können Sie in einer Beschreibung in Textform angeben, wann der Kanal angezeigt werden soll. Sie können damit auch ein Startdatum (**aktiv ab**) und ein Enddatum (**aktiv bis**) definieren, zwischen denen der Kanal angezeigt werden soll. Die Syntax für den Planausdruck basiert auf later.js-Text und der Cron-Syntax:

   * [https://bunkat.github.io/later/parsers.html#text](https://bunkat.github.io/later/parsers.html#text)
   * [https://bunkat.github.io/later/parsers.html#cron](https://bunkat.github.io/later/parsers.html#cron)
   **Attraktions-QuickInfo anzeigen**:

   Mit der Option „Attraktions-QuickInfo anzeigen“ wird definiert, ob die Attraktions-QuickInfo (*Zum Beginnen irgendwo tippen*) angezeigt wird, während der Kanal ausgeführt wird.

1. Klicken Sie auf **Speichern**, um den erstellten Kanal einer Anzeige zuzuweisen.

## Dayparting      {#dayparting}

Wenn Zeitpläne mit **Dayparting** kombiniert werden, können Sie einen globalen Zeitplan mit mehreren Kanälen festlegen, die zu bestimmten Tageszeiten ausgeführt werden, und diese Einstellungen für alle Anzeigen wiederverwenden.

Bei Dayparting wird ein Tag in Zeitfenster unterteilt und festgelegt, welcher Inhalt zum gewünschten Zeitpunkt dargestellt wird. Mit AEM Screens können Sie den Dayparting-Zeitplan von Kanälen nach Bedarf für Tage, Wochen oder Monate festlegen.

Im Folgenden wird in drei Szenarien beschrieben, wie Dayparting mit Kanälen verwendet werden kann:

### Anzeigen von Inhalten an einem einzigen Tag unterteilt in mehrere Zeitfenster      {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

Im folgenden Beispiel wird veranschaulicht, wie ein Restaurant Dayparting verwendet, um sein Angebot für Frühstück, Mittagessen und Abendessen zu präsentieren.

Wir unterteilen jeden Tag in drei Zeitfenster, sodass der Kanalinhalt gemäß der Tageszeit angezeigt wird:

| **Kanal** | **Rolle** | **Priorität** | **Zeitplan** |
|---|---|---|---|
| Menü_A | Frühstück |  | nach 6:00 Uhr und vor 11:00 Uhr |
| Menü_B | Mittagessen |  | nach 11:00 Uhr und vor 15:00 Uhr |
| Menü_C | Abendessen |  | nach 15:00 Uhr und vor 20:00 Uhr |

#### Anzeigen von Inhalten an einem bestimmten Wochentag {#playing-content-on-a-particular-day-of-the-week}

In diesem Beispiel wird gezeigt, wie Dayparting in einem Casino umgesetzt wird, wo an jedem Wochenende von 20:00 Uhr bis 22:00 Uhr eine Live-Veranstaltung stattfindet und von 22:00 Uhr bis 1:00 Uhr in der Abendkarte spezielle Gerichte angeboten werden.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Kanal</strong></td> 
   <td><strong>Rolle</strong></td> 
   <td><strong>Priorität</strong></td> 
   <td><strong>Zeitplan</strong></td> 
  </tr> 
  <tr> 
   <td>Live-Konzert</td> 
   <td>Wochenende</td> 
   <td> </td> 
   <td>21. Oktober 2017–22. Oktober 2017 <br /> nach 20:00 Uhr und vor 22:00 Uhr</td> 
  </tr> 
  <tr> 
   <td>Spezialitätenkarte</td> 
   <td>Wochenende</td> 
   <td> </td> 
   <td>21. Oktober 2017–22. Oktober 2017 <br /> nach 22:00 Uhr und vor 01:00 Uhr</td> 
  </tr> 
 </tbody> 
</table>

### Anzeigen von Inhalten für einen bestimmten Monat oder mehrere Monate {#playing-content-for-a-particular-month-months}

Dieses Beispiel veranschaulicht Dayparting für einen Laden, der seine Sommerkollektion von Juni bis August und die Herbstkollektion von September bis Ende Oktober präsentiert.

Hier wird Dayparting auf monatlicher Basis erstellt, sodass der Kanalinhalt an den angegebenen Monaten im Jahr angezeigt wird.

| **Kanal** | **Rolle** | **Priorität** | **Zeitplan** |
|---|---|---|---|
| Sommerkollektion | Sommer |  | 01. Juni 2017–31. August 2017 |
| Herbstkollektion | Herbst |  | 01. September 2017–30. Oktober 2017 |

>[!NOTE]
>
>Darüber hinaus können Sie für jeden Kanal die ***Priorität*** festlegen. Wenn beispielsweise zwei Kanäle für denselben Tag und dieselbe Uhrzeit oder für denselben Monat festgelegt sind, wird der Kanal mit höherer Priorität zuerst gezeigt. Der Mindestwert für die Priorität beträgt 0.

### Anzeigen von Inhalt für Kanäle derselben Priorität      {#playing-content-for-channels-with-same-priority}

Diese Beispiele veranschaulichen die Verwendung von Dayparting durch einen Laden, der seine Winterkollektion mit demselben Zeitplan im Dezember präsentiert. Doch da die Priorität von Kanal B in dieser Woche 2 beträgt, wird der Inhalt von Kanal B anstelle des Inhalts von Kanal A gezeigt.

| **Kanal** | **Rolle** | **Priorität** | **Zeitplan** |
|---|---|---|---|
| A | Winter | 1 | 01. Dezember 2017–31. Dezember 2017 |
| B | Weihnachten | 2 | 24. Dezember 2017–31. Dezember 2017 |

