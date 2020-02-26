---
title: Verwenden dynamischer eingebetteter Sequenzen
seo-title: Verwenden dynamischer eingebetteter Sequenzen
description: Auf dieser Seite erfahren Sie, wie Sie dynamische eingebettete Sequenzen in Ihrem AEM Screens-Projekt implementieren.
seo-description: Auf dieser Seite erfahren Sie, wie Sie dynamische eingebettete Sequenzen in Ihrem AEM Screens-Projekt implementieren.
uuid: 1f442489-2eeb-4dd8-b892-911fcccb3377
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: authoring
discoiquuid: a40eb5bb-fbf7-4c0d-a34a-db79b884de8f
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939

---


# Verwenden dynamischer eingebetteter Sequenzen{#using-dynamic-embedded-sequence}

Die Verwendung dynamischer eingebetteter Sequenzen umfasst die folgenden Themen:

* **Überblick**
* **Verwenden eines dynamischen eingebetteten Erlebnisses in AEM Screens**
* **Anzeigen der Ergebnisse**
* **Einschränken von Benutzern und Ändern der ACLs**

## Überblick {#overview}

***Dynamische eingebettete Sequenzen*** werden für große Projekte erstellt, die einer Hierarchie folgen. Dabei wird der untergeordnete Knoten in einem Standortordner und nicht in einem Kanalordner referenziert. Benutzer können so eine Sequenz anhand der ***Kanalrolle*** in einen Kanal einbetten. Damit kann der Benutzer standortspezifische Platzhalter für verschiedene Büros mithilfe einer eingebetteten Sequenz innerhalb eines Hauptkanals definieren.

Bei der Zuordnung eines Kanals zu einer Anzeige haben Sie die Möglichkeit, entweder den Pfad der Anzeige oder die Rolle des Kanals anzugeben, der nach Kontext zu einem aktuellen Kanal aufgelöst wird.

Um die dynamische eingebettete Sequenz zu verwenden, weisen Sie einen Kanal nach ***Kanalrolle*** zu. In „Kanalrolle“ wird der Kontext der Anzeige definiert. Die Rolle kann durch verschiedene Aktionen festgelegt werden und ist unabhängig vom eigentlichen Kanal, der der Rolle entspricht. In diesem Abschnitt wird ein Nutzungsszenario beschrieben, um Kanäle nach Rollen zu definieren. Außerdem erfahren Sie, wie Sie diesen Inhalt für einen globalen Kanal nutzen können. Sie können sich die Rolle auch als ID für die Zuweisung oder als Alias für den Kanal im Kontext vorstellen.

### Vorteile der Verwendung dynamischer eingebetteter Sequenzen {#benefits-of-using-dynamic-embedded-sequences}

Der Hauptvorteil der Platzierung eines Sequenzkanals innerhalb eines Standorts anstelle des Kanalordners besteht darin, dass lokale oder regionale Autoren Inhalte bearbeiten können, die für sie relevant sind, während sie gleichzeitig von der Bearbeitung von Kanälen weiter oben in der Hierarchie ausgeschlossen sind.

Wenn Sie einen *Kanal nach Rolle* referenzieren, können Sie eine lokale Version eines Kanals erstellen, um standortsspezifische Inhalte dynamisch aufzulösen. Zudem können Sie einen globalen Kanal erstellen, der die Inhalte für standortsspezifische Kanäle nutzt.

>[!NOTE]
>
>**Eingebettete Sequenzen im Vergleich zu dynamischen eingebetteten Sequenzen**
>
>Eine dynamische eingebettete Sequenz ist mit einer eingebetteten Sequenz vergleichbar. Sie unterscheidet sich allerdings dahingehend, dass der Benutzer einer Hierarchie folgen kann, bei der Änderungen/Aktualisierungen an einem Kanal auf einen anderen, in Bezug stehenden Kanal übertragen werden. Sie folgt einer Hierarchie und umfasst zudem Assets wie Bilder und Videos.
>
>Mit ***dynamischen eingebetteten Sequenzen*** können Sie standortspezifischen Inhalt anzeigen, während ***eingebettete Sequenzen*** nur eine allgemeine Diashow des Inhalts anzeigen. Außerdem müssen Sie beim Einrichten der dynamischen eingebetteten Sequenzen den Kanal mit Kanalrolle und Kanalname konfigurieren. Für die praktische Umsetzung gehen Sie wie folgt vor:
>
>Weitere Infos zur Implementierung von eingebetteten Sequenzen finden Sie unter [**Eingebettete Sequenzen **](/help/screens/embedded-sequences.md)in AEM Screens.

Das folgende Beispiel zeigt eine Lösung mit Konzentration auf die folgenden Schlüsselbegriffe:

* einen ***Hauptsequenzkanal*** für die globale Sequenz,
* eine ***dynamische eingebettete Sequenz*** für jeden lokal anpassbaren Teil der Sequenz,
* ***individual sequence channels***vin the respective locations with a *role* in the display that matches the **dynamic embedded sequence component&#39;s *role*.**

>[!NOTE]
>
>To learn more about channel assignment, see **[Channel Assignment](/help/screens/channel-assignment.md) **under Authoring section in AEM Screens documentation.

## Verwenden dynamischer eingebetteter Sequenzen {#using-dynamic-embedded-sequence-2}

Im folgenden Abschnitt wird die Erstellung einer dynamischen eingebetteten Sequenz in einem AEM Screens-Kanal erläutert.

### Voraussetzungen {#prerequisites}

Bevor Sie mit der Implementierung dieser Funktionalität beginnen, stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllen, um mit der Implementierung dynamischer eingebetteter Sequenzen beginnen zu können:

* Erstellen eines AEM Screens-Projekts (in diesem Beispiel **Demo**)

* Erstellen eines Kanals als **global** im Ordner **Kanäle**

* Hinzufügen von Inhalten zu Ihrem **globalen** Kanal (*Überprüfen Sie **Resources.zip**für relevante Assets*)

Die folgende Abbildung zeigt das Projekt **Demo** mit dem Kanal **Global** im Ordner **Kanäle.**\
![screen_shot_2018-09-07at21032pm](assets/screen_shot_2018-09-07at21032pm.png)

### Ressourcen {#resources}

Sie können die folgenden Ressourcen (Bilder) herunterladen (und zu Assets hinzufügen) und diese als Kanalinhalt für Demonstrationszwecke weiterverwenden.

[Datei laden](assets/resources.zip)

>[!NOTE]
>
>Weitere Infos zum Erstellen eines Projekts und zum Erstellen eines Sequenzkanals finden Sie in den folgenden Ressourcen:
>
>* **[Erstellen und Verwalten von Projekten](/help/screens/creating-a-screens-project.md)**
   >
   >
* **[Verwalten eines Kanals](/help/screens/managing-channels.md)**
>



Die Implementierung einer dynamischen eingebetteten Sequenz in einem AEM Screens-Projekt umfasst drei Hauptaufgaben:

1. **Einrichten des Klassifikationsschemas des Projekts, einschließlich Kanälen, Standorten und Anzeigen**
1. **Erstellen eines Zeitplans**
1. **Zuweisen eines Zeitplans zu jeder Anzeige**

Gehen Sie wie folgt vor, um die Funktion zu implementieren:

>[!CAUTION]
>
>Achten Sie bei der Implementierung dynamischer eingebetteter Sequenzen auf die Felder **Name** und **Titel**, während Sie Kanäle unter jedem Standort erstellen. Befolgen Sie die Hinweise zur Nomenklatur sorgfältig.

1. **Erstellen Sie zwei Standortordner.**

   Navigieren Sie im AEM Screens-Projekt zu Ihrem Ordner **Standorte** und erstellen Sie zwei Standortordner: **Region A** und **Region B**.

   >[!NOTE]
   >
   >Achten Sie beim Erstellen des Ordners **Region A** darauf, den **Titel** als **Region A** einzugeben und das Feld **Name** leer zu lassen. Damit wird automatisch der Name **region-a** übernommen.
   >
   >Ähnlich verhält es sich mit der Erstellung des Ordners **Region B**:

   ![screen_shot_2018-09-13at23212pm](assets/screen_shot_2018-09-13at23212pm.png)

   >[!NOTE]
   >
   >Informationen zum Erstellen eines Standorts finden Sie unter **[Erstellen und Verwalten von Standorten](/help/screens/managing-locations.md)**.

1. **Erstellen Sie unter jedem Standortordner zwei Standorte und einen Kanal.**

   1. Navigieren Sie zu **Demo** > **Standorte** > **Region A**.
   1. Select **Region A **and click **+ Create** from the action bar.
   1. Wählen Sie **Standort** im Assistenten und unter **Titel** die Option **Store 1** aus. Erstellen Sie auf ähnliche Weise einen weiteren Standort im Assistenten mit dem Titel **Store 2** mit **Titel** als **Store 2**. Sie können das Feld **Name** leer lassen, während Sie **Store 1** und **Store 2** erstellen.
   1. Wiederholen Sie Schritt (b) und wählen Sie jetzt **Sequenzkanal** im Assistenten aus. Geben Sie den **Titel** als **Region A** und den **Namen** als „region“ für diesen Kanal ein.
   >[!CAUTION]
   >
   >Geben Sie bei der Erstellung des Kanals **Region A** den **Titel** als „Region A“ und den **Namen** als **region** ein.

   ![screen_shot_2018-09-13at22857pm](assets/screen_shot_2018-09-13at22857pm.png)

   Erstellen Sie auf ähnliche Weise zwei Standorte unter **Region B** mit den Titeln **Store 3** und **Store 4**. Erstellen Sie außerdem einen **Sequenzkanal**, für den Sie als **Titel** den Wert **Region B** und als **Name** den Wert **region** wählen.

   >[!CAUTION]
   >
   >Achten Sie darauf, dass Sie denselben Namen für die Kanäle verwenden können, die in **Region A** und **Region B** als **region** erstellt wurden.

   ![screen_shot_2018-09-13at24408pm](assets/screen_shot_2018-09-13at24408pm.png)

1. **Erstellen Sie eine Anzeige und einen Kanal unter jedem Standort.**

   1. Navigieren Sie zu **Demo** > **Standorte** > **Region A** > **Store 1**.
   1. Select **Store 1 **and click **+ Create** from the action bar.
   1. Wählen Sie im Assistenten die Option **Anzeige** aus und erstellen Sie **Store1Display**.
   1. Wiederholen Sie Schritt (b) und wählen Sie jetzt **Sequenzkanal** im Assistenten aus. Wählen Sie unter **Titel** den Wert **Store1Channel** und unter **Name** den Wert **store**.
   >[!CAUTION]
   >
   >Bei der Erstellung eines Sequenzkanals ist es wichtig, dass der **Titel** des Kanals Ihren Anforderungen entspricht. Der **Name** sollte jedoch in allen lokalen Kanälen gleich sein.
   >
   >In this example, the channels under **Region A **and **Region B** share the same **Name** as **region** and channels under **Store 1**, **Store 2**, **Store 3**, and **Store 4 **share the same **Name** as **store**.

   ![screen_shot_2018-09-19at120206pm](assets/screen_shot_2018-09-19at120206pm.png)

   Erstellen Sie eine Anzeige als **Store2Display** und einen Kanal **Store2Channel** unter „Store 2“ (mit dem Namen **store**).

   >[!NOTE]
   >
   >Achten Sie darauf, dass Sie denselben Namen für die Kanäle verwenden können, die in **Store 1** und **Store 2** als **store** erstellt wurden.

   ![screen_shot_2018-09-19at120329pm](assets/screen_shot_2018-09-19at120329pm.png)

   Befolgen Sie die vorhergehenden Schritte, um einen Kanal und Display in **Store 3** und **Store 4** unter **Region B** zu erstellen. Auch hier ist darauf zu achten, dass Sie unter **Name** denselben Wert **store** verwenden, während Sie die Kanäle **Store3Channel** und **Store4Channel** erstellen.

   Die folgende Abbildung zeigt die Anzeige und den Kanal im **Store 3**.

   ![screen_shot_2018-09-19at120448pm](assets/screen_shot_2018-09-19at120448pm.png)

   Die folgende Abbildung zeigt die Anzeige und den Kanal im **Store 4**.

   ![screen_shot_2018-09-19at120552pm](assets/screen_shot_2018-09-19at120552pm.png)

1. **Fügen Sie den Kanälen an ihren jeweiligen Standorten Inhalt hinzu.**

   Navigieren Sie zu **Demo** > **Standorte** > **Region A** > **Region A** und klicken Sie in der Aktionsleiste auf **Bearbeiten**. Ziehen Sie die Assets, die Sie hinzufügen möchten, in Ihren Kanal.

   >[!NOTE]
   >
   >Sie können die Datei ***Resources.zip*** im Abschnitt **Ressourcen** verwenden, um die Bilder als Assets für Ihren Kanalinhalt zu verwenden.

   ![screen_shot_2018-09-12at12438pm](assets/screen_shot_2018-09-12at12438pm.png)

   Navigieren Sie zu **Demo** > **Standorte** > **Region B** > **Region B** und klicken Sie in der Aktionsleiste auf **Bearbeiten**, um die Assets in Ihren Kanal zu ziehen, wie nachfolgend gezeigt:

   ![screen_shot_2018-09-12at13133pm](assets/screen_shot_2018-09-12at13133pm.png)

   Folgen Sie den vorherigen Schritten und den Ressourcen, um Inhalte zu den folgenden Kanälen hinzuzufügen:

   * **Store1Channel**
   * **Store2Channel**
   * **Store3Channel**
   * **Store4Channel**

1. **Zeitplan erstellen**

   Navigieren Sie zum Ordner **Zeitpläne** in Ihrem AEM Screens-Projekt und klicken Sie in der Aktionsleiste auf **Erstellen**, um einen neuen Zeitplan zu erstellen.

   Die folgende Abbildung zeigt den **AdSchedule**, der im Projekt **Demo** erstellt wurde.

   ![screen_shot_2018-09-13at33307pm](assets/screen_shot_2018-09-13at33307pm.png)

1. **Weisen Sie einem Zeitplan Kanäle zu**

   1. Navigieren Sie zu **Demo** > **Zeitpläne** > **AdSchedule** und klicken Sie in der Aktionsleiste auf **Dashboard**.
   1. Klicken Sie auf **+ Kanal zuweisen** im Bedienfeld **ZUGEWIESENE KANÄLE**, um das Dialogfeld **Kanalzuweisung** zu öffnen.
   1. Wählen Sie als Vorgehensweise für **Kanal referenzieren** nach Pfad.
   1. Select the **Channel Path** as **Demo*** --> ***Channels*** --> ***Global***.
   1. Geben Sie als **Kanalrolle** den Wert **GlobalAdSegment** ein.
   1. Wählen Sie unter **Unterstützte Ereignisse** die Optionen **Erster Ladevorgang**, **Bildschirm bei Untätigkeit** und **Benutzerinteraktion** aus.
   1. Klicken Sie auf **Speichern**.
   **Kanal nach Rolle für die Region zuweisen:**

   1. Klicken Sie auf **+ Kanal zuweisen** im Bedienfeld **ZUGEWIESENE KANÄLE**, um das Dialogfeld **Kanalzuweisung** zu öffnen.
   1. Wählen Sie als Vorgehensweise für **Kanal referenzieren** die Option „Name“ aus.
   1. Geben Sie unter **Kanalname** den Wert **region** ein.
   1. Geben Sie als **Kanalrolle** den Wert **RegionAdSegment** ein.
   1. Klicken Sie auf **Speichern**.
   **Kanal nach Rolle für den Store zuweisen:**

   1. Klicken Sie auf **+ Kanal zuweisen** im Bedienfeld **ZUGEWIESENE KANÄLE**, um das Dialogfeld **Kanalzuweisung** zu öffnen.
   1. Wählen Sie als Vorgehensweise für **Kanal referenzieren** die Option „Name“ aus.
   1. Geben Sie den **Kanalnamen** als **store** ein.
   1. Geben Sie als **Kanalrolle** den Wert **StoreAdSegment** ein.
   1. Klicken Sie auf **Speichern**.
   Die folgende Abbildung zeigt die zugewiesenen Kanäle nach Pfad und Rolle.

   ![screen_shot_2018-09-12at21429pm](assets/screen_shot_2018-09-12at21429pm.png)

1. **Konfigurieren Sie die dynamische eingebettete Sequenz für den Kanal „Global“.**

   Navigieren Sie zum Kanal **Global**, den Sie ursprünglich im Projekt **Demo** erstellt haben.

   Klicken Sie in der Aktionsleiste auf **Bearbeiten**, um den Editor zu öffnen.

   ![screen_shot_2018-09-13at52754pm](assets/screen_shot_2018-09-13at52754pm.png)

   Ziehen Sie zwei Komponenten der **dynamischen eingebetteten Sequenz** in den Kanaleditor.

   Öffnen Sie die Eigenschaften einer der Komponenten und geben Sie die **Kanalzuordnungsrolle** als **RegionAdSegment** ein.

   Wählen Sie die andere Komponente aus und öffnen Sie die Eigenschaften, um die **Kanalzuordnungsrolle** als **StoreAdSegment** einzugeben.

   ![channeldisplay4](assets/channeldisplay4.gif)

1. **Zuweisen eines Zeitplans zu jeder Anzeige**

   1. Navigieren Sie zur jeweiligen Anzeige, z. B. **Demo** > **Standorte** > **Region A** >**Store 1** >**Store1Display**.
   1. Klicken Sie in der Aktionsleiste auf **Dashboard**, um das Anzeigen-Dashboard zu öffnen.
   1. Klicken Sie auf **...** im Bedienfeld **ZUGEWIESENE KANÄLE UND ZEITPLÄNE** und klicken Sie auf **+Zeitplan zuweisen**.
   1. Wählen Sie den Pfad zum Zeitplan aus (hier z. B. **Demo** > **Zeitpläne** >**AdSchedule**).
   1. Klicken Sie auf **Speichern**.

## Anzeigen der Ergebnisse {#viewing-the-results}

Sobald Sie die Einrichtung für Kanäle und die Anzeige abgeschlossen haben, starten Sie den AEM Screens-Player, um den Inhalt anzuzeigen.

>[!NOTE]
>
>Weitere Informationen zum AEM Screens-Player finden Sie in den folgenden Ressourcen:
>
>* [**AEM Screens-Player-Downloads **](https://download.macromedia.com/screens/)
>* [**Arbeiten mit dem AEM Screens-Player **](/help/screens/working-with-screens-player.md)
>



Die folgende Ausgabe bestätigt Ihren Kanalinhalt im AEM Screens-Player, je nach Anzeigepfad.

**Szenario 1**:

Wenn Sie den Anzeigepfad als **Demo** > **Standorte** > **Region A** > „Store 1“ > **Store1Display** zuweisen, wird der folgende Inhalt im AEM Screens-Player angezeigt.

![channeldisplay1](assets/channeldisplay1.gif)

**Szenario 1**:

Wenn Sie den Anzeigepfad als **Demo** > **Standorte** > **Region B** > „Store 3“ > **Store3Display** zuweisen, wird der folgende Inhalt im AEM Screens-Player angezeigt.

![channeldisplay2](assets/channeldisplay2.gif)

## Einschränken von Benutzern und Ändern der ACLs {#restricting-users-and-modifying-the-acls}

Sie können globale, regionale oder lokale Autoren erstellen, die für sie relevante Inhalte bearbeiten, während sie gleichzeitig von der Bearbeitung von Kanälen weiter oben in der Hierarchie ausgeschlossen sind.

Sie müssen die ACLs ändern, um den Zugriff der Benutzer auf die Inhalte je nach Standort einzuschränken.

### Anwendungsbeispiel {#example-use-case}

Im folgenden Beispiel können Sie drei Benutzer für das obige Projekt „Demo“ erstellen.

Die Berechtigungen werden jeder Gruppe wie folgt zugewiesen:

**Gruppen**:

* **Global-Autor**: Besteht aus Benutzern, die Zugriff auf alle Standorte und Kanäle im Projekt **Demo** haben und über alle Lese-, Schreib- und Bearbeitungsberechtigungen verfügen.

* **Region-Autor**: Besteht aus Benutzern, die Lese-, Schreib- und Bearbeitungsberechtigungen für **Region A** und **Region B** besitzen.

* **Store-Autor**: Besteht aus Benutzern, die nur über Lese-, Schreib- und Bearbeitungsberechtigungen für **Store 1**, **Store 2**, **Store 3** und **Store 4** verfügen.

#### Schritte zum Erstellen von Benutzergruppen, Benutzern und Einrichten von ACLs {#steps-for-creating-user-groups-users-and-setting-up-acls}

>[!NOTE]
>
>Detaillierte Informationen dazu, wie Sie Projekte mithilfe von ACLs trennen, damit jede Einzelperson oder jedes Team ein eigenes Projekt handhabt, finden Sie unter **Einrichten von ACLs**.

Führen Sie die folgenden Schritte aus, um Gruppen und Benutzer zu erstellen und die ACLs gemäß den Berechtigungen zu ändern:

1. **Gruppen erstellen**

   1. Navigieren Sie zu **Adobe Experience Manager**.
   1. Klicken Sie auf **Tools** > **Sicherheit** > **Gruppen**.
   1. Klicken Sie auf **Gruppe erstellen** und geben Sie **Global-Autor** in **ID** ein.
   1. Klicken Sie auf **Speichern und schließen**.
   Erstellen Sie auf ähnliche Weise zwei weitere Gruppen wie **Region-Autor** und **Store-Autor**.

   ![screen_shot_2018-09-17at34008pm](assets/screen_shot_2018-09-17at34008pm.png)

1. **Benutzer erstellen und Gruppen Benutzer hinzufügen**

   1. Navigieren Sie zu **Adobe Experience Manager**.
   1. Klicken Sie auf **Tools** > **Sicherheit** > **Benutzer**.
   1. Klicken Sie auf **Benutzer erstellen** und geben Sie **Global-Benutzer** in **ID** ein.
   1. Geben Sie ein **Kennwort** ein und bestätigen Sie das Kennwort für diesen Benutzer.
   1. Klicken Sie auf die Registerkarte **Gruppen** und geben Sie den Gruppennamen in **Gruppe auswählen** ein. Geben Sie beispielsweise **Global-Autor** ein, um dieser Gruppe **Global-Benutzer** hinzuzufügen.
   1. Klicken Sie auf **Speichern und schließen**.
   Erstellen Sie auf ähnliche Weise zwei weitere Benutzer wie **Region-Benutzer** und **Store-Benutzer** und fügen Sie sie **Region-Autor** bzw. **Store-Autor** hinzu.

   >[!NOTE]
   >
   >Es empfiehlt sich, Benutzer einer Gruppe hinzuzufügen und dann den einzelnen Benutzergruppen Berechtigungen zuzuweisen.

   ![screen_shot_2018-09-17at34412pm](assets/screen_shot_2018-09-17at34412pm.png)

1. **Alle Gruppen zu den Mitwirkenden hinzufügen**

   1. Navigieren Sie zu **Adobe Experience Manager**.
   1. Klicken Sie auf **Tools** > **Sicherheit** > **Gruppen**.
   1. Wählen Sie in der Liste die Option **Mitwirkende** und anschließend die Registerkarte **Mitglieder** aus.
   1. Wählen Sie die **Gruppe**, z. B. **Global-Autor**, **Region-Autor** oder **Store-Autor**, für die Mitwirkenden aus.
   1. Klicken Sie auf **Speichern und schließen**.

1. **Auf die Berechtigungen für jede Gruppe zugreifen**

   1. Navigieren Sie zu *Useradmin* und ändern Sie mithilfe dieser Benutzeroberfläche die Berechtigungen für die verschiedenen Gruppen.
   1. Suchen Sie nach **Global-Autor** und klicken Sie auf die Registerkarte **Berechtigungen**, wie in der Abbildung unten dargestellt.
   1. Ebenso können Sie auf die Berechtigungen für **Region-Autor** und **Store-Autor** zugreifen.
   ![screen_shot_2018-09-18at73523am](assets/screen_shot_2018-09-18at73523am.png)

1. **Berechtigungen für jede Gruppe ändern**

   **Für Global-Autor:**

   1. Navigieren Sie zur Registerkarte **Berechtigungen**
   1. Navigieren Sie zu ***/content/screens/demo*** und prüfen Sie alle Berechtigungen
   1. Navigieren Sie zu ***/content/screens/demo/locations*** und prüfen Sie alle Berechtigungen
   1. Navigate to ***/content/screens/demo/locations***/***region-a*** and check all the permissions. Überprüfen Sie auf ähnliche Weise die Berechtigungen für **region-b**.
   Die Schritte sind in der folgenden Abbildung dargestellt:\
   ![screen_shot_2018-09-18at115752am](assets/screen_shot_2018-09-18at115752am.png)

   Die folgende Abbildung zeigt, dass der **Global-Benutzer** jetzt Zugriff auf den **Global-Kanal** und sowohl auf **Region A** als auch auf **Region B** mit allen vier Stores hat, nämlich **Store 1**, **Store 2**, **Store 3** und **Store 4**.

   ![global](assets/global.gif)

   **Für Region-Autor:**

   1. Navigieren Sie zur Registerkarte **Berechtigungen**.
   1. Navigieren Sie zu ***/content/screens/demo*** und prüfen Sie nur die Lese-Berechtigungen.
   1. Navigieren Sie zu ***/content/screens/demo/locations*** und prüfen Sie nur die **Leseberechtigungen**.
   1. Navigieren Sie zu /content/screens/demo/channels ***und deaktivieren Sie die Berechtigungen für den Kanal **Global**.***
   1. Navigate to ***/content/screens/demo/locations***/***region-a*** and check all the permissions. Überprüfen Sie auf ähnliche Weise die Berechtigungen für **region-b**.
   Die Schritte sind in der folgenden Abbildung dargestellt:

   ![screen_shot_2018-09-18at125158pm](assets/screen_shot_2018-09-18at125158pm.png)

   Die folgende Abbildung zeigt, dass der Region-Benutzer jetzt Zugriff auf **Region A** und **Region B** mit allen vier Stores hat, nämlich **Store 1**, **Store 2**, **Store 3** und **Store 4**, aber nicht auf den Kanal **Global**.

   ![region](assets/region.gif)

   **Für Store-Autor:**

   1. Navigieren Sie zur Registerkarte **Berechtigungen**.
   1. Navigieren Sie zu ***/content/screens/demo*** und überprüfen Sie nur die **Leseberechtigungen**.
   1. Navigieren Sie zu ***/content/screens/demo/locations*** und prüfen Sie nur die **Leseberechtigungen**.
   1. Navigieren Sie zu ***/content/screens/demo/channels*** und deaktivieren Sie die Berechtigungen für den Kanal **Global**.
   1. Navigieren Sie zu ***/content/screens/demo/locations/region-a*** und prüfen Sie nur die **Leseberechtigungen**. Ebenso sollten Sie nur die **Leseberechtigungen** für **region-b** prüfen.
   1. Navigate to ***/content/screens/demo/locations***/***region-a /store-1*** and check all the permissions. Prüfen Sie auf ähnliche Weise die Berechtigungen für **store-2, store-3** und **store-4**.
   Die Schritte sind in der folgenden Abbildung dargestellt:

   ![screen_shot_2018-09-18at12415pm](assets/screen_shot_2018-09-18at12415pm.png)

   Die folgende Abbildung zeigt, dass der **Store-Benutzer** nur Zugriff auf die vier Stores hat, nämlich **Store 1**, **Store 2**, **Store 3** und **Store 4**, aber keine Berechtigungen für den Zugriff auf den Kanal **Global** oder die Region-Kanäle („Region A“ und **Region B**).

   ![store](assets/store.gif)

>[!NOTE]
>
>Ausführliche Informationen zum Einrichten von Berechtigungen finden Sie in der Entwicklerdokumentation zu AEM Screens unter [**Einrichten von ACLs **](/help/screens/setting-up-acls.md).

