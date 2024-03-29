---
title: Communities Sites-Konsole
seo-title: Communities Sites Console
description: Zugriff auf die Communities Sites-Konsole
seo-description: How to access the Communities Sites console
uuid: 85017055-b8af-4eeb-a8ab-1cbbba0f5a6a
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 5ac2fcef-05b8-46f7-9a15-997cdd79a3db
role: Admin
exl-id: f1408709-5402-4f55-bd37-9943fe828af0
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3263'
ht-degree: 4%

---

# Communities Sites-Konsole {#communities-sites-console}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Die Communities Sites-Konsole bietet Zugriff auf:

* Site-Erstellung
* Site-Bearbeitung
* Site-Management
* [Erstellen und Bearbeiten verschachtelter Gruppen](groups.md) (Unter-Communities)

Siehe [Erste Schritte mit AEM Communities](getting-started.md) , um zu erfahren, wie schnell eine Community-Site in der Autorenumgebung erstellt werden kann und wie Community-Gruppen aus der Autoren- und Veröffentlichungsumgebung erstellt werden.

>[!NOTE]
>
>Die Hauptmenüs der Gemeinschaften zur Erstellung von [Community-Sites](sites-console.md), [Community-Site-Vorlagen](sites.md), [Community-Gruppenvorlagen](tools-groups.md) und [Community-Funktionen](functions.md) sind nur zur Verwendung in der Autorenumgebung vorgesehen.

## Voraussetzungen {#prerequisites}

Bevor Sie eine Community-Site erstellen, ist dies *erforderlich* an:

* Stellen Sie sicher, dass eine oder mehrere Veröffentlichungsinstanzen ausgeführt werden
* Aktivieren Sie die [Tunneldienst](deploy-communities.md#tunnel-service-on-author) Mitglieder und Mitgliedergruppen verwalten
* Identifizieren Sie die [primärer Herausgeber](deploy-communities.md#primary-publisher)
* [Replikation konfigurieren](deploy-communities.md#replication-agents-on-author) wenn der primäre Publisher-Anschluss nicht der Standard ist (4503)

Um sicherzustellen, dass die Site viele Funktionen unterstützt, empfiehlt es sich, die folgenden Schritte auszuführen:

* Installieren Sie die [neueste Feature Pack](deploy-communities.md#latestfeaturepack)
* Aktivieren [Adobe Analytics](analytics.md) für AEM Communities
* Konfigurieren [email](email.md)
* Identifizieren [Community-Administratoren](users.md#creating-community-members)
* [OAuth-Handler aktivieren](social-login.md#adobe-granite-oauth-authentication-handler) für Anmeldung in sozialen Netzwerken

## Zugreifen auf die Communities Sites-Konsole {#accessing-communities-sites-console}

Gehen Sie in der Autorenumgebung in die Konsole Communities Sites :

* Über die globale Navigation: **[!UICONTROL Communities > Sites]**

Die Communities Sites-Konsole zeigt alle vorhandenen Community-Sites an. In dieser Konsole können Community-Sites erstellt, bearbeitet, verwaltet und gelöscht werden.

Um eine neue Community-Site zu erstellen, wählen Sie die **Erstellen** Symbol.

Um auf eine bestehende Community-Site zuzugreifen, wählen Sie zum Erstellen, Ändern, Veröffentlichen, Exportieren oder Hinzufügen einer verschachtelten Gruppe das Ordnersymbol der Sites aus.

Die folgende Abbildung zeigt beispielsweise die Haupt-Konsole Communities-Sites , in der die Ordner für zwei Community-Sites angezeigt werden: [enable](getting-started-enablement.md) und [interagieren](getting-started.md):

![chlimage_1-448](assets/chlimage_1-448.png)

## Erstellung einer Site {#site-creation}

Die Site-Erstellungskonsole bietet einen schrittweisen Ansatz, um Funktionen der Site basierend auf einer ausgewählten [Community-Site-Vorlage](sites.md) und -Einstellungen.

Jede erstellte Site verfügt über eine Anmeldefunktion, da sich Besucher der Site anmelden müssen, bevor sie Inhalte posten, Nachrichten senden oder an einer Gruppe teilnehmen können. Weitere Funktionen sind Benutzerprofile, Messaging, Benachrichtigungen, Site-Menü, Suche, Themen und Branding.

Der Prozess wird durch Auswahl der `Create` -Schaltfläche oben in der Communities-Sites-Konsole.

Der Erstellungsprozess besteht aus einer Reihe von Schritten, die als Bedienfelder mit einer Reihe von zu konfigurierenden Funktionen präsentiert werden (als Unterbedienfelder dargestellt). Es ist möglich, **Nächste** Schritt oder **Zurück** in den vorherigen Schritt, bevor die Site im letzten Schritt übergeben wird.

### Schritt 1: Site-Vorlage {#step-site-template}

![newsitetemplate](assets/newsitetemplate.png)

Im Bereich &quot;Site-Vorlage&quot;werden der Titel, die Beschreibung, der Site-Stamm, die Basissprache, der Name und die Site-Vorlage angegeben:

* **[!UICONTROL Community-Site-Titel]**: Ein Anzeigetitel für die Site.

   Der Titel wird auf der veröffentlichten Site sowie in der Administrator-Benutzeroberfläche der Site angezeigt.

* **[!UICONTROL Community-Site-Beschreibung]**: Eine Beschreibung der Site.

   Die Beschreibung wird nicht auf der veröffentlichten Site angezeigt.

* **[!UICONTROL Community-Site-Stammordner]**: Der Stammpfad zur Site.

   Der Standardstamm lautet `/content/sites`, aber der Stamm kann an einen beliebigen Ort auf der Website verschoben werden.

* **[!UICONTROL Community-Site-Basissprache]**: (lassen Sie für eine einzelne Sprache unberührt: Englisch) verwenden Sie das Pulldown-Menü, um eine Auswahl zu treffen *oder mehr* Basissprachen aus den verfügbaren Sprachen: Deutsch, Italienisch, Französisch, Japanisch, Spanisch, Portugiesisch (Brasilien), Chinesisch (Traditionell) und Chinesisch (vereinfacht). Für jede hinzugefügte Sprache wird eine Community-Site erstellt, die gemäß den Best Practices unter [Übersetzen von Inhalten für mehrsprachige Sites](../../help/sites-administering/translation.md). Die Stammseite jeder Site enthält eine untergeordnete Seite mit dem Namen des Sprachcodes einer der ausgewählten Sprachen, z. B. &quot;en&quot;für Englisch oder &quot;fr&quot;für Französisch.

* **[!UICONTROL Community-Site-Name]**: Der Name der Stammseite der Site, der in der URL angezeigt wird

   * Überprüfen Sie den Namen, da er nach der Erstellung der Site nicht einfach geändert werden kann.
   * Die Basis-URL ( `https://*server:port/site root/site name*)` wird unter dem `Community Site Name`
   * Hängen Sie für eine gültige URL einen Basissprachcode an + &quot;.html&quot;.

      *Beispiel*, `http://localhost:4502/content/sites/mysight/en.html`

* **[!UICONTROL Community-Site-Vorlage]** Menü: Verwenden Sie das Pulldown-Menü, um eine verfügbare [Community-Site-Vorlage](tools.md).

Wählen Sie **[!UICONTROL Weiter]** aus

### Schritt 2: Design {#step-design}

Das Bedienfeld &quot;Design&quot;enthält zwei Unterbedienfelder zur Auswahl des Designs und des Branding-Banners:

#### SITE-THEMA DER GEMEINSCHAFT {#community-site-theme}

![sitetheme-1](assets/sitetheme-1.png)

Das Framework verwendet `Twitter Bootstrap` , um ein responsives, flexibles Design auf die Site zu bringen. Es kann eines der vielen vorab geladenen Bootstrap-Designs ausgewählt werden, um die ausgewählte Community-Site-Vorlage zu gestalten. Andernfalls kann ein Bootstrap-Design hochgeladen werden.

Wenn diese Option aktiviert ist, wird das Design mit einem undurchsichtigen blauen Häkchen überlagert.

Nach der Veröffentlichung der Community-Site ist es möglich, [Eigenschaften bearbeiten](#modifying-site-properties) und wählen Sie ein anderes Design aus.

#### GEMEINSCHAFTLICHE SITE-BRANCHE {#community-site-branding}

![chlimage_1-449](assets/chlimage_1-449.png)

Community-Site-Branding ist ein Bild, das oben auf jeder Seite als Kopfzeile angezeigt wird.

Die Bildgröße sollte der erwarteten Anzeige der Seite im Browser und einer Höhe von 120 Pixel entsprechen.

Beachten Sie beim Erstellen oder Auswählen eines Bildes Folgendes:

* Die Bildhöhe wird vom oberen Rand des Bildes auf 120 Pixel zugeschnitten
* Das Bild wird am linken Rand des Browser-Fensters fixiert
* Die Größe des Bildes wird nicht geändert, d. h. wenn die Bildbreite ...

   * Weniger als die Browser-Breite, wird das Bild horizontal wiederholt
   * Größer als die Breite des Browsers, wird das Bild scheinbar zugeschnitten

Wählen Sie **[!UICONTROL Weiter]** aus.

### Schritt 3: Einstellungen {#step-settings}

Das Einstellungsbedienfeld enthält mehrere Unterbedienfelder mit Funktionen, die vor dem Wechsel zum letzten Schritt zur Erstellung der Site konfiguriert werden müssen.

* [BENUTZERVERWALTUNG](#user-management)
* [TAGGING](#tagging)
* [ROLLEN](#roles)
* [MODERATION](#moderation)
* [ANALYTICS](#analytics)
* [ÜBERSETZUNG](#translation)
* [AKTIVIERUNG](#enablement)

>[!NOTE]
>
>**Aktivieren des Tunneldienstes**
>
>Einige der Unterbereiche Einstellungen ermöglichen es einem vertrauenswürdigen Mitglied, UGC zu moderieren, Gruppen zu verwalten oder Kontakte für Aktivierungsressourcen in der Veröffentlichungsumgebung zu sein.
>
>Die Konvention ist für die Veröffentlichungsseite vorgesehen. [Benutzer und Benutzergruppen](users.md) (Mitglieder und Mitgliedergruppen) nicht in der Autorenumgebung dupliziert werden.
>
>Wenn Sie daher die Community-Site in der Autorenumgebung erstellen und vertrauenswürdigen Mitgliedern verschiedene Rollen zuweisen, müssen Sie Mitgliedsdaten aus der Veröffentlichungsumgebung abrufen.
>
>Dazu aktivieren Sie die ` [AEM Communities Publish Tunnel Service](deploy-communities.md#tunnel-service-on-author)`für die Autorenumgebung.

#### BENUTZERVERWALTUNG {#user-management}

![createsitesettings-1](assets/createsitesettings-1.png)

>[!NOTE]
>
>Es wird empfohlen, [Aktivierungs-Community-Sites](overview.md#enablement-community) privat sein (weitere Informationen erhalten Sie von Ihrem Kundenbetreuer).
>
>Eine Community-Site ist privat, wenn anonymen Site-Besuchern der Zugriff verweigert wird, sie sich möglicherweise nicht selbst registrieren und keine Anmeldung über soziale Netzwerke verwenden.

* **[!UICONTROL Benutzerregistrierung zulassen]**

   Wenn diese Option aktiviert ist, können Besucher der Site durch Selbstregistrierung Community-Mitglieder werden.

   Wenn diese Option deaktiviert ist, wird die Community-Site *eingeschränkt* und Besucher der Site müssen der Mitgliedergruppe der Community-Site zugewiesen werden, eine Anforderung stellen oder per E-Mail eingeladen werden. Wenn diese Option deaktiviert ist, sollte der anonyme Zugriff nicht erlaubt sein.

   Deaktivieren Sie die Option für *privat* Community-Site. Die Option Standard ist aktiviert.

* **[!UICONTROL Anonymen Zugriff erlauben]**

   Ist diese Option aktiviert, wird die Community-Site *open* und jeder Besucher der Site kann auf die Site zugreifen.

   Wenn diese Option deaktiviert ist, können nur angemeldete Mitglieder auf die Site zugreifen.

   Deaktivieren Sie die Option für *privat* Community-Site. Die Option Standard ist aktiviert.

* **[!UICONTROL Messaging zulassen]**

   Wenn diese Option aktiviert ist, können Mitglieder Nachrichten miteinander und an die Gruppe innerhalb der Community-Site senden.

   Wenn diese Option deaktiviert ist, werden Nachrichten nicht für die Community eingerichtet.

   Die Option Standard ist deaktiviert.

* **[!UICONTROL Anmeldung über soziale Medien erlauben: Facebook]**

   Wenn diese Option aktiviert ist, können sich Besucher der Site mit ihren Facebook-Kontoanmeldeinformationen anmelden. Die ausgewählte [Facebook-Cloud-Konfiguration](social-login.md#create-a-facebook-connect-cloud-service) sollte so konfiguriert werden, dass Benutzer zur Mitgliedergruppe der Community-Site hinzugefügt werden, sobald die Community-Site erstellt wurde.

   Wenn diese Option deaktiviert ist, wird keine Facebook-Anmeldung angezeigt.

   Lassen Sie die Option deaktiviert für *privat* Community-Site. Die Option Standard ist deaktiviert.

* **[!UICONTROL Anmeldung über soziale Medien erlauben: Twitter]**

   Wenn diese Option aktiviert ist, können sich Besucher der Site mit ihren Twitter-Kontoanmeldeinformationen anmelden. Die ausgewählte [Twitter-Cloud-Konfiguration](social-login.md#create-a-twitter-connect-cloud-service) sollte so konfiguriert werden, dass Benutzer zur Mitgliedergruppe der Community-Site hinzugefügt werden, sobald die Community-Site erstellt wurde.

   Wenn diese Option deaktiviert ist, wird keine Twitter-Anmeldung angezeigt.

   Lassen Sie die Option deaktiviert für *privat* Community-Site. Die Option Standard ist deaktiviert.

>[!NOTE]
>
>**[!UICONTROL Zulassen von Social-Anmeldungen]**
>
>Während möglicherweise Beispielkonfigurationen für Facebook und Twitter vorhanden und auswählbar sind, wird für eine [Produktionsumgebung](../../help/sites-administering/production-ready.md)ist es erforderlich, benutzerdefinierte Facebook- und Twitter-Anwendungen zu erstellen. Siehe [Anmeldung über Social Media mit Facebook und Twitter](social-login.md).

#### TAGGING {#tagging}

![chlimage_1-450](assets/chlimage_1-450.png)

Die Tags, die auf Community-Inhalte angewendet werden können, werden durch die Auswahl von Tag-Namespaces gesteuert, die zuvor durch die Variable [Tagging-Konsole](../../help/sites-administering/tags.md#tagging-console).

Darüber hinaus wird durch die Auswahl von Tag-Namespaces für die Community-Site die beim Definieren von Katalogen und Ressourcen angezeigte Auswahl eingeschränkt. Siehe [Tagging von Aktivierungsressourcen](tag-resources.md) für wichtige Informationen.

* Textsuchfeld: Eingabe beginnen, um die Tags zu identifizieren, die auf der Site verwendet werden dürfen

#### ROLLEN {#roles}

![chlimage_1-451](assets/chlimage_1-451.png)

Die [Rollen von Community-Mitgliedern](users.md) mit diesen Einstellungen zugewiesen werden.

Die Suche nach Community-Mitgliedern ist einfach durch die Suche nach Typ-Ahead.

* **[!UICONTROL Community-Manager]**

   Beginnen Sie mit der Typisierung, um ein oder mehrere Community-Mitglieder oder Mitgliedergruppen auszuwählen, die Community-Mitglieder und Mitgliedergruppen verwalten können.

* **[!UICONTROL Community-Moderatoren]**

   Beginnen Sie mit der Eingabe, um ein oder mehrere Community-Mitglieder oder Mitgliedergruppen auszuwählen, die als Moderatoren von benutzergenerierten Inhalten vertrauenswürdig sind.

* **[!UICONTROL Privilegierte Community-Mitglieder]**

   Beginnen Sie mit der Typisierung, um ein oder mehrere Community-Mitglieder oder Mitgliedergruppen auszuwählen, damit neue Inhalte erstellt werden können, wenn `Allow Privileged Member` wurde für eine [Community-Funktion](functions.md).

#### MODERATION {#moderation}

![chlimage_1-452](assets/chlimage_1-452.png)

Die globale Einstellung für die Moderation benutzergenerierter Inhalte (UGC) wird durch diese Einstellungen gesteuert. Einzelne Komponenten verfügen über zusätzliche Einstellungen zur Steuerung der Moderation.

* **[!UICONTROL Inhalt ist vormoderiert]**

   Wenn diese Option aktiviert ist, werden veröffentlichte Community-Inhalte erst angezeigt, nachdem sie von einem Moderator genehmigt wurden. Die Option Standard ist deaktiviert. Weitere Informationen finden Sie unter [Moderieren von Community-Inhalten](moderate-ugc.md#premoderation).

* **[!UICONTROL Kennzeichnung des Schwellenwerts, bevor der Inhalt ausgeblendet wird]**

   Bei mehr als 0 muss die Häufigkeit definiert werden, mit der ein Thema oder Beitrag gekennzeichnet werden muss, bevor er aus der öffentlichen Ansicht ausgeblendet wird. Wenn der Wert auf -1 festgelegt ist, wird das gekennzeichnete Thema oder der Beitrag nie aus der öffentlichen Ansicht ausgeblendet. Der Standardwert ist 5.

#### ANALYTICS {#analytics}

![chlimage_1-453](assets/chlimage_1-453.png)

* **[!UICONTROL Analytics aktivieren]**

   Nur verfügbar, wenn Adobe Analytics [konfiguriert](analytics.md) für Communities-Funktionen.

   Die Option Standard ist deaktiviert. Wenn diese Option aktiviert ist, wird ein zusätzliches Auswahlmenü angezeigt:

![chlimage_1-454](assets/chlimage_1-454.png)

* **[!UICONTROL Framework-Verweis der Cloud-Konfiguration]**

   Wählen Sie aus dem Pulldown-Menü das für diese Community-Site konfigurierte Analytics Cloud Service-Framework aus.

   `Communities`ist das Framework-Beispiel aus [Analytics-Konfiguration für Communities-Funktionen](analytics.md#aem-analytics-framework-configuration) Dokumentation.

#### ÜBERSETZUNG {#translation}

![chlimage_1-455](assets/chlimage_1-455.png)

* **[!UICONTROL Maschinelle Übersetzung zulassen]**
Wenn diese Option aktiviert ist (die Standardeinstellung ist deaktiviert), wird die maschinelle Übersetzung für benutzergenerierte Inhalte auf der Site aktiviert. Dies wirkt sich nicht auf andere Inhalte aus, z. B. Seiteninhalte, selbst wenn die Site als mehrsprachige Site eingerichtet ist. Siehe [Übersetzen benutzergenerierter Inhalte](translate-ugc.md) Informationen zum Konfigurieren eines lizenzierten Übersetzungsdienstes für AEM Communities. Siehe [Übersetzen von Inhalten für mehrsprachige Sites](../../help/sites-administering/translation.md) für einen vollständigen Überblick.

![chlimage_1-456](assets/chlimage_1-456.png)

* **[!UICONTROL Maschinelle Übersetzung für ausgewählte Sprachen aktivieren]**

   Die für die maschinelle Übersetzung aktivierten Sprachen entsprechen standardmäßig der Systemeinstellung, die von der [Konfiguration der Übersetzungsintegration](translate-ugc.md#translation-integration-configuration). Diese Standardeinstellungen können für diese Site überschrieben werden, indem Standardwerte gelöscht und/oder andere Sprachen aus dem Pulldown-Menü ausgewählt werden.

* **[!UICONTROL Übersetzungsanbieter auswählen]**

   Standardmäßig ist der Dienstleister ein Testdienst, der Folgendes verwendet: `microsoft`nur zur Veranschaulichung. Wenn kein Übersetzungsdienstleister lizenziert ist, **Maschinelle Übersetzung zulassen** deaktiviert werden.

* **[!UICONTROL Globalen geteilten Speicher auswählen]**

   Für eine Website mit mehreren Sprachkopien bietet ein globaler freigegebener Speicher einen einzigen Konversationsthread, der von jeder Sprachkopie aus sichtbar ist. Dies wird erreicht, indem eine der Sprachen als Sprachkopie ausgewählt wird. Der Standardwert ist *Kein globaler freigegebener Store*.

* **[!UICONTROL Übersetzungsanbieter-Konfiguration auswählen]**

   Wählen Sie eine [Framework zur Übersetzungsintegration](../../help/sites-administering/tc-tic.md) erstellt für den lizenzierten Übersetzungsanbieter.

* **Wählen Sie die Übersetzungsoptionen für Ihre Community-Site**

   * **[!UICONTROL Gesamte Seite übersetzen]**

      Wenn diese Option aktiviert ist, werden alle benutzergenerierten Inhalte einer Seite in die Basissprache der Seite übersetzt.

      Der Standardwert ist *nicht ausgewählt*.

   * **[!UICONTROL Nur Auswahl übersetzen]**

      Wenn diese Option aktiviert ist, wird neben jedem Beitrag eine Übersetzungsoption angezeigt, mit der einzelne Beiträge in die Basissprache der Seite übersetzt werden können.

      Der Standardwert ist *selected*.

* **Speicheroptionen auswählen**

   * **[!UICONTROL Beiträge auf Benutzeranfrage übersetzen und anschließend behalten.]**

      Wenn diese Option aktiviert ist, wird der Inhalt erst übersetzt, nachdem eine Anforderung gestellt wurde. Nach der Übersetzung wird die Übersetzung im Repository gespeichert.

      Der Standardwert ist *nicht ausgewählt*.

   * **[!UICONTROL Übersetzungen nicht behalten]**

      Wenn diese Option aktiviert ist, werden Übersetzungen nicht im Repository gespeichert.

      Wenn diese Option nicht ausgewählt ist, werden die Übersetzungen beibehalten.

      Der Standardwert ist *nicht ausgewählt*.

* **[!UICONTROL Smart Render]**
Wählen Sie eine von

   * `Always show contributions in the original language` (default)
   * `Always show contributions in user preferred language`
   * `Show contributions in user preferred language for only logged-in users`

#### AKTIVIERUNG {#enablement}

![chlimage_1-457](assets/chlimage_1-457.png)

Die `ENABLEMENT`Die Einstellungen gelten, wenn die ausgewählte Community-Site-Vorlage die [Zuweisungsfunktion](functions.md#assignments-function), der bei der Lizenzierung der Aktivierungsfunktionen verfügbar ist, und [konfiguriert](enablement.md). Die Referenz-Website-Vorlage, die die Zuweisungsfunktion enthält, lautet `Reference Structured Learning Site Template.`

* **[!UICONTROL Aktivierungsmanager]**

   (erforderlich) Nur Mitglieder der `Community Enablementmanagers` zur Verwaltung dieser Aktivierungs-Community ausgewählt werden. Aktivierungsmanager sind für die Zuweisung von Mitgliedern zu Ressourcen verantwortlich. Siehe auch [Verwalten von Benutzern und Benutzergruppen](users.md).

* **[!UICONTROL ID der Marketing Cloud-Organisation]**

   (optional) Die ID für eine [Video Heartbeat Analytics](analytics.md#video-heartbeat-analytics) Lizenz.

Wählen Sie **[!UICONTROL Weiter]** aus.

### Schritt 4: Community-Site erstellen {#step-create-communities-site}

Falls Anpassungen erforderlich sind, verwenden Sie die **Zurück** -Schaltfläche, um sie zu erstellen.

Einmal **Erstellen** ausgewählt und gestartet wurde, kann der Prozess zum Erstellen der Site nicht unterbrochen werden.

Nachdem die Site erstellt wurde:

* Das Ändern der URL (Knotenname) wird nicht unterstützt
* Künftige Änderungen an der Community-Site-Vorlage wirken sich nicht auf die erstellte Community-Site aus
* Die Deaktivierung der Community-Site-Vorlage hat keine Auswirkungen auf die erstellte Community-Site
* Es ist möglich, die [STRUKTUR](#modify-structure) einer Community-Site durch Ändern ihrer Eigenschaften

![chlimage_1-458](assets/chlimage_1-458.png)

Nach Abschluss des Vorgangs wird der Ordner für die neue Site in der Communities Sites-Konsole angezeigt. Von dort aus können Autoren Seiteninhalte hinzufügen oder Administratoren können die Eigenschaften der Site ändern.

![chlimage_1-459](assets/chlimage_1-459.png)

Um eine Community-Site zu ändern, wählen Sie deren Projektordner aus, um sie zu öffnen:

![siteactions-2](assets/siteactions-2.png)

Wenn Sie den Mauszeiger über eine Site bewegen oder eine Site-Karte berühren, werden Symbole angezeigt, die [Bearbeiten der Site im Autorenmodus](#authoring-site-content), [Öffnen der Site-Eigenschaften zur Änderung](#modifying-site-properties), [Veröffentlichen der Site](#publishing-the-site), [Exportieren der Site](#exporting-the-site)und [Löschen der Site](#deleting-the-site).

## Erstellen von Site-Inhalten {#authoring-site-content}

![chlimage_1-460](assets/chlimage_1-460.png)

Der Inhalt einer Website kann mit den gleichen Tools wie jede andere AEM erstellt werden. Um die Site für die Bearbeitung zu öffnen, wählen Sie die `Open Site` -Symbol, das beim Bewegen der Maus über die Site angezeigt wird. Die Site wird in einer neuen Registerkarte geöffnet, sodass die Konsole &quot;Communities-Sites&quot;weiterhin verfügbar ist.

![chlimage_1-461](assets/chlimage_1-461.png)

>[!NOTE]
>
>Wenn Sie nicht mit AEM vertraut sind, lesen Sie die Dokumentation unter [grundlegende Handhabung](../../help/sites-authoring/basic-handling.md) und [Kurzanleitung zum Erstellen von Seiten](../../help/sites-authoring/qg-page-authoring.md).

## Ändern von Site-Eigenschaften {#modifying-site-properties}

![chlimage_1-462](assets/chlimage_1-462.png)

Die Eigenschaften einer vorhandenen Site, die während des Site-Erstellungsprozesses angegeben werden, können durch Auswahl der `Edit Site`-Symbol, das angezeigt wird, wenn Sie den Mauszeiger über die Site bewegen.

`Details of the following properties match the descriptions provided in the` [Site-Erstellung](#site-creation) Abschnitt.

![chlimage_1-463](assets/chlimage_1-463.png)

### Standard ändern {#modify-basic}

Das BASIC-Bedienfeld ermöglicht die Änderung von

* Community-Site-Titel
* Community-Site-Beschreibung

Der Community-Site-Name darf nicht geändert werden.

Die Auswahl einer anderen Community-Site-Vorlage hätte keine Auswirkungen auf eine bestehende Community-Site, da keine Verbindung zwischen Vorlagen und Sites besteht.

Stattdessen wird die [STRUKTUR](#modify-structure) der Community-Site geändert werden.

### Struktur ändern {#modify-structure}

Das Bedienfeld STRUKTUR ermöglicht die Änderung der Struktur, die ursprünglich aus der ausgewählten Community-Site-Vorlage erstellt wurde. Im Bereich können Sie

* Zusätzliche Drag-and-Drop-Funktionen [Community-Funktionen](functions.md) in die Site-Struktur
* Auf einer Instanz einer Community-Funktion in der Site-Struktur:

   * **`gear icon`**

      Bearbeitungseinstellungen, einschließlich Anzeigentitel und URL-Name&amp;ast;

      sowie [privilegierte Mitgliedergruppen](users.md#privilegedmembersgroups)

   * **`trashcan icon`**

      Entfernen (Löschen) von Funktionen aus der Site-Struktur

   * **`grid icon`**

      Ändern der Reihenfolge der Funktionen, wie sie in der Navigationsleiste auf oberster Ebene der Site angezeigt werden

>[!NOTE]
>
>Sie können die Reihenfolge aller Funktionen in der Site-Struktur ändern, mit Ausnahme der Funktion oben. Daher kann die Startseite der Communities-Site nicht geändert werden.

>[!CAUTION]
>
>Der Anzeigentitel kann ohne Nebenwirkungen geändert werden. Es wird jedoch nicht empfohlen, den URL-Namen einer Community-Funktion zu bearbeiten, die zu einer Community-Site gehört.
>
>Wenn Sie beispielsweise die URL umbenennen, werden vorhandene UGC nicht verschoben, sodass der UGC-Wert &quot;verloren&quot;wird.

>[!CAUTION]
>
>Die Funktion &quot;Gruppen&quot;muss *not* die *first noch die einzige* in der Site-Struktur.
>
>Jede andere Funktion, z. B. die [Seitenfunktion](functions.md#page-function), muss zuerst eingeschlossen und aufgelistet werden.

#### Beispiel: Hinzufügen einer Katalogfunktion zu einer Community-Site-Struktur {#example-adding-a-catalog-function-to-a-community-site-structure}

![chlimage_1-464](assets/chlimage_1-464.png)

### Design ändern {#modify-design}

Im Bedienfeld DESIGN kann ein neues Design angewendet werden:

* [Community-Site-Thema](#community-site-theme)
* [Community-Site-Branding](#community-site-branding)
   * Scrollen Sie zum unteren Rand des Bedienfelds, um das Markenbild zu ändern.

### Einstellungen ändern {#modify-settings}

Das Fenster EINSTELLUNGEN ermöglicht den Zugriff auf die meisten Einstellungen unter den Unterfeldern von für Schritt 3 der Community-Site-Erstellung:

* [User Management](#user-management)
* [Tags](#tagging)
* [Moderation](#moderation)
* [Mitgliederrollen](#roles)
* [Analyse](#analytics)
* [Übersetzung](#translation)

### Miniaturansicht ändern {#modify-thumbnail}

Im Bedienfeld &quot;MINIATURANSICHT&quot;kann ein Bild hochgeladen werden, das die Site in der Konsole &quot;Communities-Sites&quot;darstellt.

### Aktivierung ändern {#modify-enablement}

Das Bedienfeld AKTIVIERUNG ermöglicht den Zugriff auf die Einstellungen, die während der Erstellung der Community-Site bereitgestellt werden.

Siehe [AKTIVIERUNG](#enablement) Beschreibung.

## Veröffentlichen der Site {#publishing-the-site}

Nachdem eine Community-Site neu erstellt oder geändert wurde, ist es möglich, die Site zu veröffentlichen (zu aktivieren), indem Sie die `Publish Site` -Symbol, das angezeigt wird, wenn Sie den Mauszeiger über die Site bewegen.

![chlimage_1-465](assets/chlimage_1-465.png)

Es gibt einen Hinweis, nachdem die Site erfolgreich veröffentlicht wurde.

![chlimage_1-466](assets/chlimage_1-466.png)

### Veröffentlichen mit verschachtelten Gruppen {#publishing-with-nested-groups}

Nach dem Veröffentlichen einer Community-Site muss jede Unter-Community (verschachtelte Gruppe), die mit der [Gruppenkonsole](groups.md).

## Exportieren der Site {#exporting-the-site}

![chlimage_1-467](assets/chlimage_1-467.png)

Wählen Sie das Exportsymbol aus, wenn Sie den Mauszeiger über die Website bewegen, um ein Paket der Community-Site zu erstellen, das beide in gespeichert ist. [Package Manager](../../help/sites-administering/package-manager.md) und heruntergeladen.\
Beachten Sie, dass UGC nicht im Site-Paket enthalten ist.

## Löschen der Site {#deleting-the-site}

![deleteicon-1](assets/deleteicon-1.png)

Um die Community-Site zu löschen, wählen Sie das Symbol Site löschen aus, das angezeigt wird, wenn Sie den Mauszeiger über die Site in der Communities-Site-Konsole bewegen. Mit dieser Aktion werden alle mit der Site verknüpften Elemente entfernt, z. B. benutzergenerierte Inhalte, Benutzergruppen, Assets und Datenbankdatensätze.

## Erstellte Community-Benutzergruppen {#created-community-user-groups}

Sobald die neue Community-Site veröffentlicht wurde, werden neue Mitgliedergruppen (Benutzergruppen werden in der Veröffentlichungsumgebung erstellt) erstellt, für die die entsprechenden Berechtigungen für verschiedene Admin- und Mitgliederrollen festgelegt sind.

Der für die Mitgliedergruppen erstellte Name enthält die *site-name* angesichts der Site in [Schritt 1](#step13asitetemplate) (der Name, der in der URL angezeigt wird) sowie eine eindeutige ID, um Konflikte mit Community-Sites und -Gruppen zu vermeiden, die denselben Site-Namen für verschiedene Community-Site-Stämme haben.

Wenn der Name beispielsweise &quot;engage&quot;für eine Site mit dem Titel &quot;Erste Schritte-Tutorial&quot;wäre, wäre die Benutzergruppe für Moderatoren:

* Titel: Community-Moderatoren einbinden
* Name: community-*engage-uid*-moderators

Beachten Sie, dass alle Mitglieder, denen beim Erstellen der Site Rollen als Moderatoren oder Gruppenadministratoren zugewiesen wurden, der entsprechenden Gruppe zugewiesen und der Mitgliedergruppe zugewiesen werden. Diese Gruppen und Mitgliederzuweisungen werden beim Veröffentlichen der neuen Site erstellt.

Weitere Informationen finden Sie unter [Verwalten von Benutzern und Benutzergruppen](users.md).

>[!NOTE]
>
>Wenn [Social-Anmeldung zulassen: Facebook](#user-management) aktiviert ist, sobald die Benutzergruppe
>
>* community-*&lt;site-name>*-*&lt;uid>*-members
>
erstellt wird, wird die angewendete [Facebook Cloud Service](social-login.md#createafacebookcloudservice) sollte so konfiguriert sein, dass Benutzer zu dieser Gruppe hinzugefügt werden.

## Authentifizierungsfehler konfigurieren {#configure-for-authentication-error}

Standardmäßig wird eine Community-Site zu einer Beispielanmeldeseite umgeleitet, wenn der Benutzer die falschen Anmeldedaten eingibt und sich nicht anmeldet. Diese Beispielanmeldung ist nicht auf einem [Produktionsserver](../../help/sites-administering/production-ready.md).

Führen Sie zur korrekten Umleitung die folgenden Schritte aus, um sicherzustellen, dass die Authentifizierung bei der Umleitung zur Community-Site fehlschlägt, sobald eine Site konfiguriert und zur Veröffentlichung gepusht wurde:

* Bei jeder AEM Veröffentlichungsinstanz
* Erste Anmeldung mit Administratorrechten
* Zugriff auf [Web-Konsole](../../help/sites-deploying/configuring-osgi.md)
   * Beispiel: [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Suchen `Adobe Granite Login Selector Authentication Handler`
* Wählen Sie die `pencil`Symbol zum Öffnen der Konfiguration zur Bearbeitung
* Geben Sie einen **[!UICONTROL Zuordnungen von Anmeldeseiten]** wie folgt:

   `/content/sites/<site-name>/path/to/login/page:/content/sites/<site-name>`

   Beispiel:

   `/content/sites/engage/en/signin:/content/sites/engage/en`

* Wählen Sie **[!UICONTROL Speichern]** aus

![chlimage_1-468](assets/chlimage_1-468.png)

### Testauthentifizierungsumleitung {#test-authentication-redirection}

Auf derselben AEM Veröffentlichungsinstanz, die mit einem Anmeldeseitenzuordnung für die Community-Site konfiguriert wurde:

* Navigieren Sie zur Startseite der Community-Site.
   * Beispiel: [http://localhost:4503/content/sites/engage/en.html](http://localhost:4503/content/sites/engage/en.html)

* Log Out auswählen
* Anmelden auswählen
* Geben Sie offensichtlich falsche Anmeldedaten ein, z. B. Benutzername &quot;x&quot;und Kennwort &quot;x&quot;.
* Die Anmeldeseite sollte mit dem Fehler &quot;Ungültige Anmeldung&quot;angezeigt werden.

![chlimage_1-469](assets/chlimage_1-469.png)

## Zugriff auf Community-Sites über die Konsole &quot;Haupt-Sites&quot; {#accessing-community-sites-from-main-sites-console}

In der Konsole für globale Navigations-Sites befinden sich Community-Sites im `Community Sites` Ordner.

Obwohl es möglich ist, auf eine Community-Site auf diese Weise zuzugreifen, sollte die Community-Site für administrative Aufgaben über die Communities-Sites-Konsole aufgerufen werden.

![chlimage_1-470](assets/chlimage_1-470.png)
