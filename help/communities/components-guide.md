---
title: Handbuch der Community-Komponenten
seo-title: Community Components Guide
description: Ein interaktives Entwicklungstool für die ersten Schritte mit dem Social Component Framework (SCF)
seo-description: An interactive development tool to get started with the social component framework (SCF)
uuid: 120e56d1-b93c-4f92-bab4-6bb5e40e0ddf
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: a777a3f1-b39f-4d90-b9b6-02d3e321a86f
exl-id: 8cdd7b94-b247-4598-bb0f-36c5ec1319ec
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1187'
ht-degree: 4%

---

# Handbuch der Community-Komponenten {#community-components-guide}

Das Komponentenleitfaden der Community ist ein interaktives Entwicklungstool für die [Social Component Framework (SCF)](scf.md). Es bietet eine Liste der verfügbaren AEM Communities-Komponenten oder der komplexeren Funktionen, die aus mehreren Komponenten erstellt wurden.

Neben grundlegenden Informationen für jede Komponente ermöglicht das Handbuch Experimente mit der Funktionsweise der SCF-Komponenten/-Funktionen und deren Konfiguration oder Anpassung.

Informationen zu Entwicklungsgrundlagen für die einzelnen Komponenten finden Sie unter [Funktionen und Komponentengrundlagen](essentials.md).

## Erste Schritte {#getting-started}

Das Handbuch ist für Entwicklungs-Installationen von Autoren- (localhost:4502) und Veröffentlichungsinstanzen (localhost:4503) vorgesehen.

Auf die Website &quot;Community-Komponenten&quot;können Sie unter

* [https://&lt;server>:&lt;port>/content/community-components/en.html](http://localhost:4502/content/community-components/en.html)

Die Interaktionen mit den Communities-Komponenten variieren je nach:

* Der Server (Autor oder Veröffentlichung)
* Ob der Site-Besucher angemeldet ist oder nicht
* Wenn angemeldet, die dem Mitglied zugewiesenen Berechtigungen
* Gibt an, ob das Standard-SRP [JSRP](jsrp.md)verwendet wird

Fügen Sie beim Autor Folgendes ein, um den Bearbeitungsmodus zu aktivieren: `editor.html` oder `cf#` als erstes Pfadsegment nach dem Servernamen:

* Standard-Benutzeroberfläche:

   [https://&lt;server>:&lt;port>/editor.html/content/community-components/en.html](http://localhost:4502/editor.html/content/community-components/en.html)

* Klassische Benutzeroberfläche:

   [https://&lt;server>:&lt;port>/cf#/content/community-components/en.html](http://localhost:4502/cf#/content/community-components/en.html)

>[!NOTE]
>
>Beim Autor im Bearbeitungsmodus sind die Links auf einer Seite nicht aktiv.
>
>Um zu einer Komponentenseite zu navigieren, wählen Sie zunächst den Vorschaumodus aus, um die Links zu aktivieren.
>
>Kehren Sie bei angezeigter Komponentenseite im Browser zum Bearbeitungsmodus zurück, um das Bearbeitungsdialogfeld der Komponente zu öffnen.
>
>Allgemeine Informationen zum Authoring finden Sie unter [Kurzanleitung zum Erstellen von Seiten](../../help/sites-authoring/qg-page-authoring.md).
>
>Wenn Sie nicht mit AEM vertraut sind, lesen Sie die Dokumentation unter [grundlegende Handhabung](../../help/sites-authoring/basic-handling.md).

### Startseite {#home-page}

Das Handbuch enthält eine Liste von SCF-Komponenten, die links auf der Seite für die Vorschau und das Prototyping verfügbar sind.

Komponentenleitfaden, wie in einer Autoreninstanz im Bearbeitungsmodus angezeigt:

![chlimage_1-404](assets/chlimage_1-404.png)

## Komponentenseiten {#component-pages}

Wählen Sie eine Komponente aus der Liste auf der linken Seite der Seite aus.

![chlimage_1-405](assets/chlimage_1-405.png)

Der Hauptteil des Handbuchs wird angezeigt:

1. Titel: Der Name der ausgewählten Komponente
1. [Client-seitige Bibliotheken](#client-side-libraries): Liste einer oder mehrerer erforderlicher Kategorien
1. [Einschließlich](scf.md#add-or-include-a-communities-component): Wenn die Komponente dynamisch eingeschlossen werden kann, kann der Status im Bearbeitungsmodus des Autors umgeschaltet werden:

   * Wenn hinzugefügt, wird folgender Text angezeigt: &quot;Diese Komponente wird über ihren par -Knoten einbezogen.&quot;
   * Wenn enthalten, lautet der angezeigte Text: &quot;Diese Komponente wird dynamisch einbezogen.&quot;
   * Wenn nicht eingeschlossen, wird kein Text angezeigt

1. Beispielkomponente oder -funktion: eine aktive Instanz der Komponente oder Funktion. Wenn eine Komponente geändert werden soll, kann sie durch Änderungen an den Vorlagen, CSS und Daten, die im Tab-Abschnitt bereitgestellt werden, geändert werden.

>[!NOTE]
>
>Nachdem Sie eine Auswahl auf der linken Seite getroffen haben, wird die Komponente unten angezeigt, anstatt neben der Liste der Komponenten, wenn das Browser-Fenster zu eng ist.

### Autoreninteraktionen {#author-interactions}

Wenn Sie das Handbuch in einer Autoreninstanz verwenden, ist es möglich, die Konfiguration einer Komponente durch Öffnen des Dialogfelds zu erleben. Informationen für Entwickler finden Sie im Abschnitt [Komponenten- und Funktionsgrundlagen](essentials.md) -Abschnitt der Dokumentation, während die Dialogfeldeinstellungen unter [Communities-Komponenten](author-communities.md) für Autoren.

Im Handbuch &quot;Community Components&quot;werden einige Einstellungen für das Komponenten-Dialogfeld mit dem [Einschließlich](scf.md#add-or-include-a-communities-component) Status umschalten. Um zwischen der Verwendung der vorhandenen Ressource oder einer dynamisch eingeschlossenen Ressource umzuschalten, wählen Sie im Bearbeitungsmodus sowohl die Komponente als auch den einschließbaren Text aus und doppelklicken Sie, um das Bearbeitungsdialogfeld zu öffnen:

![chlimage_1-406](assets/chlimage_1-406.png)

Unter dem **Vorlagen** tab:

![chlimage_1-407](assets/chlimage_1-407.png)

* **Untergeordnete Komponente mit sling:include einschließen**

   Wenn diese Option deaktiviert ist, verwendet das Komponentenleitfaden die vorhandene Ressource im Repository (einen jcr-Knoten, der einem par -Knoten untergeordnet ist).

   * angezeigter Text: &quot;Diese Komponente wird über ihren par -Knoten einbezogen.&quot;

   Wenn diese Option aktiviert ist, verwendet das Komponentenleitfaden Sling, um eine Komponente des resourceType des untergeordneten Knotens (nicht vorhandene Ressource) dynamisch einzuschließen.

   * angezeigter Text: &quot;Diese Komponente wird dynamisch einbezogen.&quot;

   Diese Option ist standardmäßig deaktiviert.

### Veröffentlichungsinteraktionen {#publish-interactions}

Bei Verwendung des Handbuchs in einer Veröffentlichungsinstanz ist es möglich, die Komponenten und Funktionen als Site-Besucher (nicht angemeldet) und als Mitglieder mit verschiedenen Berechtigungen beim Anmelden zu erleben.

>[!NOTE]
>
>Beachten Sie, wenn das SRP standardmäßig auf [JSRP](jsrp.md)festgelegt ist, wird UGC, der in die Veröffentlichungsinstanz eingegeben wird, nur bei der Veröffentlichung sichtbar und *nicht *in der [Moderation](moderate-ugc.md) auf der Autoreninstanz.

## Client-seitige Bibliotheken {#client-side-libraries}

Die clientseitigen Bibliotheken (clientlibs), die für jede Komponente aufgelistet sind, sind *erforderlich* , auf die verwiesen wird, wenn die Komponente auf einer Seite platziert wird. Die clientlibs bieten eine Möglichkeit, den Download von JavaScript und CSS zu verwalten und zu optimieren, die zum Rendern der Komponente im Browser verwendet werden.

Weitere Informationen finden Sie unter [Clientlibs für Communities-Komponenten](clientlibs.md).

## Personifikation {#impersonation}

Verwenden Sie in der Autoreninstanz, in der häufig ein Benutzer als Administrator oder Entwickler angemeldet ist, das Textfeld links neben der Komponente, um die angemeldete Komponente als einen anderen Benutzer zu erleben. **[!UICONTROL Identität annehmen]** -Schaltfläche, um entweder den Benutzernamen einzugeben oder aus der Pulldown-Liste auszuwählen, und klicken Sie dann auf die Schaltfläche. Klicken Sie auf Wiederherstellen , um den Identitätswechsel zu signalisieren und zu beenden.

Die Veröffentlichungsinstanz muss nicht stellvertretend agieren. Verwenden Sie einfach den Link Anmelden/Abmelden , um verschiedene Benutzer zu stellvertreten, z. B. die [Demobenutzer](tutorials.md#demo-users).

## Anpassung {#customization}

Wenn diese Option aktiviert ist, steht jede SCF-Komponente für die Prototypisierung möglicher Anpassungen zur Verfügung, indem die Vorlage, CSS und Daten der Komponente vorübergehend geändert werden.

### Aktivieren der Anpassung {#enabling-customization}

>[!NOTE]
>
>**Dieses Tool ist schreibgeschützt**. An Vorlagen, CSS oder Daten vorgenommene Änderungen werden nicht im Repository gespeichert.

Um schnell mit Anpassungen zu experimentieren, muss die `scg:showIde`-Eigenschaft muss zum JCR-Knoten der Inhaltsseite der Komponente hinzugefügt und auf &quot;true&quot;gesetzt werden.

Verwenden der Kommentarkomponente als Beispiel für die Autoren- oder Veröffentlichungsinstanz, die mit Administratorrechten angemeldet ist:

1. Navigieren Sie zu [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md)

   Beispiel: [http://localhost:4503/crx/de](http://localhost:4503/crx/de)

1. Wählen Sie die `jcr:content` Knoten

   Beispiel: `/content/community-components/en/comments/jcr:content`

1. Eigenschaft hinzufügen

   * **Name** `scg:showIde`
   * **Typ** `String`
   * **Wert** `true`

1. Klicken Sie auf **[!UICONTROL Alle speichern]**
1. Laden Sie die Seite &quot;Kommentare&quot;im Handbuch erneut.

   [http://localhost:4503/content/community-components/en/comments.html](http://localhost:4503/content/community-components/en/comments.html)

1. Beachten Sie, dass es jetzt 3 Registerkarten für Vorlagen, CSS und Daten gibt.

![chlimage_1-408](assets/chlimage_1-408.png) ![chlimage_1-409](assets/chlimage_1-409.png)

### Registerkarte &quot;Vorlagen&quot; {#templates-tab}

Wählen Sie den Tab Vorlagen aus, um die mit der Komponente verknüpften Vorlagen anzuzeigen.

Mit dem Vorlagen-Editor können lokale Bearbeitungen kompiliert und auf die Beispielkomponenteninstanz oben auf der Seite angewendet werden, ohne dass sich dies auf die Komponente im Repository auswirkt.

Wenn Sie die Kompilierung auf lokalen Bearbeitungen ausführen, werden alle Fehler hervorgehoben, indem Sie einen Punkt in der Rinne platzieren und den Text rot markieren.

### CSS-Registerkarte {#css-tab}

Wählen Sie die Registerkarte CSS aus, um die mit der Komponente verknüpfte CSS anzuzeigen.

Wenn eine Komponente aus mehreren Komponenten zusammengesetzt ist, können einige CSS unter einer der anderen Komponenten aufgeführt sein.

Mit dem CSS-Editor kann das CSS geändert und auf die Beispielkomponenteninstanz oben auf der Seite angewendet werden.

Es kann eine Regel ausgewählt werden, um die Teile des DOM mithilfe dieser Regel hervorzuheben, indem Sie neben der Regel in der Rinne auf klicken.

### Registerkarte &quot;Daten&quot; {#data-tab}

Wählen Sie die Registerkarte Daten aus, um die Endpunktdaten .social.json anzuzeigen. Diese Daten können bearbeitet werden und werden auf die Beispielkomponenteninstanz angewendet.

Syntaxfehler können im Rinnstein markiert und im Editor hervorgehoben werden.
