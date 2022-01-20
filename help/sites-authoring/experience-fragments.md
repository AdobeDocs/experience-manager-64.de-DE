---
title: Experience Fragments
seo-title: Experience Fragments
description: Experience Fragments
seo-description: null
uuid: be1aceef-eb6e-47e5-a920-be5cc6de6191
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 1fe58af0-3005-46fc-8717-5d32557947ed
exl-id: 8906b3ab-cb08-4b3e-8796-334e36b1e491
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1309'
ht-degree: 90%

---

# Experience Fragments{#experience-fragments}

Ein Experience Fragment ist eine Gruppe aus einer oder mehreren Komponenten (einschließlich Inhalt und Layout), die innerhalb von Seiten referenziert werden können. Diese Gruppen können jede beliebige Komponente enthalten.

Ein Experience Fragment:

* ist Teil eines Erlebnisses (Seite).
* kann übergreifend für mehrere Seiten verwendet werden.
* basiert auf einer (bearbeitbaren) Vorlage, die seine Struktur und Komponenten definiert.
* besteht aus einer oder mehreren Komponenten mit Layout innerhalb eines Absatzsystems.
* kann Experience Fragments enthalten.
* kann mit anderen Komponenten (einschließlich anderen Experience Fragments) zu einer vollständigen Seite (Erlebnis) kombiniert werden.
* kann verschiedene Varianten aufweisen, die Inhalte und/oder Komponenten gemeinsam nutzen.
* kann in Bausteine untergliedert werden, die sich übergreifend für mehrere Varianten des Fragments verwenden lassen.

Experience Fragments können in folgenden Fällen verwendet werden:

* Wenn Autoren die Teile einer Seite (die sogenannten Fragmente eines Erlebnisses) wiederverwenden möchten, müssen sie das entsprechende Fragment kopieren und an der gewünschten Stelle einfügen. Das Erstellen und Verwalten dieser zum Kopieren/Einfügen vorgesehenen Erlebnisse sind zeitaufwendige und fehleranfällige Verfahren. Mit Experience Fragments ersparen Sie sich das Kopieren/Einfügen.
* Zur Unterstützung des Nutzungsszenarios mit Headless-Content-Management-Systemen. Autoren sollten AEM nur zum Erstellen von Inhalten nutzen, jedoch nicht für deren Bereitstellung für Kunden. In diesem Fall würde das Erlebnis über ein System/einen Touchpoint eines Drittanbieters für den Endnutzer bereitgestellt.

>[!NOTE]
>
>Für den Schreibzugriff auf Experience Fragments muss das betreffende Benutzerkonto der folgenden Gruppe angehören:
>
>`experience-fragments-editors`
>
>Wenden Sie sich an Ihren Systemadministrator, falls Probleme auftreten.

## Wann ist die Verwendung von Experience Fragments sinnvoll? {#when-should-you-use-experience-fragments}

Experience Fragments sollten in folgenden Fällen verwendet werden:

* Immer wenn Sie Erlebnisse wiederverwenden möchten.

   * Erlebnisse, die in Verbindung mit demselben oder ähnlichem Inhalt wiederverwendet werden

* Wenn Sie AEM als Inhaltsbereitstellungs-Plattform für Dritte nutzen möchten.

   * Nutzung durch beliebige Lösungen, bei denen AEM als Inhaltsbereitstellungs-Plattform fungieren soll
   * Einbetten von Inhalten in Touchpoints von Dritten

* Wenn ein Erlebnis verschiedene Varianten oder Ausgabeformate aufweist.

   * Kanal- oder kontextspezifische Varianten
   * Erlebnisse, die als Gruppe sinnvoll eingesetzt werden können (z. B. eine Kampagne, die abhängig vom jeweiligen Kanal unterschiedliche Erlebnisse liefert)

* Wenn Sie Omni-Channel-Commerce betreiben.

   * Skaliertes Teilen von Commerce-bezogenem Inhalt auf Social-Media-Kanälen
   * Ermöglichen von Transaktionen an Touchpoints

## Organisieren von Experience Fragments {#organizing-your-experience-fragments}

Folgendes wird empfohlen:
* Verwenden von Ordnern zum Organisieren der Experience Fragments,

* [Konfigurieren der zulässigen Vorlagen für diese Ordner](#configure-allowed-templates-folder).

Mit dem Erstellen von Ordnern können Sie:

* eine aussagekräftige Struktur für Ihre Experience Fragments erstellen; zum Beispiel nach Klassifizierung

   >[!NOTE]
   >
   >Es ist nicht erforderlich, die Struktur Ihrer Experience Fragments an der Seitenstruktur Ihrer Site auszurichten.

* [Zuweisen der zulässigen Vorlagen auf Ordnerebene](#configure-allowed-templates-folder)

   >[!NOTE]
   >
   >Verwenden Sie den [Vorlagen-Editor](/help/sites-authoring/templates.md), wenn Sie eine eigene Vorlage erstellen möchten.

Das folgende Beispiel zeigt Experience Fragments, die nach `Contributors`. Die verwendete Struktur zeigt auch, wie andere Funktionen, wie Multi-Site-Management (einschließlich Sprachkopien), verwendet werden können.

>[!CAUTION]
>
>Der folgende Screenshot wurde von der WKND-Site mit Adobe Experience Manager as a Cloud Service aufgenommen.

![Ordner für Experience Fragments](assets/xf-folders.png)

## Erstellen und Konfigurieren eines Ordners für Ihre Experience Fragments {#creating-and-configuring-a-folder-for-your-experience-fragments}

Um einen Ordner für Ihre Experience Fragments zu erstellen und zu konfigurieren, wird Folgendes empfohlen:

1. [Erstellen eines Ordners](/help/sites-authoring/managing-pages.md#creating-a-new-folder).

1. [Konfigurieren der die zulässigen Experience Fragment-Vorlagen für diesen Ordner](#configure-allowed-templates-folder).

>[!NOTE]
>
>Es ist auch möglich, die [Zulässige Vorlagen für Ihre Instanz](#configure-allowed-templates-instance), aber diese Methode ist **not** empfohlen, da die Werte bei der Aktualisierung möglicherweise überschrieben werden.

### Konfigurieren zulässiger Vorlagen für Ihren Ordner {#configure-allowed-templates-folder}

>[!NOTE]
>
>Dies ist die empfohlene Methode zur Angabe der **[!UICONTROL zulässigen Vorlagen]**, da die Werte bei der Aktualisierung nicht überschrieben werden.

1. Navigieren Sie zum gewünschten Ordner mit **[!UICONTROL Experience Fragments]**.

1. Wählen Sie den Ordner und dann **[!UICONTROL Eigenschaften]** aus.

1. Geben Sie den regulären Ausdruck zum Abrufen der erforderlichen Vorlagen im Feld **[!UICONTROL Zulässige Vorlagen]** an.

   Beispiel:
   `/conf/(.*)/settings/wcm/templates/experience-fragment(.*)?`

   ![Experience Fragment-Eigenschaften – Zulässige Vorlagen](assets/xf-folders-templates.png)

1. Klicken Sie auf **[!UICONTROL Speichern und schließen]**.

### Konfigurieren zulässiger Vorlagen für Ihre Instanz {#configure-allowed-templates-instance}

>[!CAUTION]
>
>Es wird nicht empfohlen, die **[!UICONTROL Zulässige Vorlagen]** durch diese Methode, da die angegebenen Vorlagen bei der Aktualisierung überschrieben werden können.
>
>Verwenden Sie diesen Dialog nur zu Informationszwecken.

1. Navigieren Sie zur gewünschten Konsole **[!UICONTROL Experience Fragments]**.

1. Wählen Sie **[!UICONTROL Konfigurationsoptionen]** aus:

   ![Schaltfläche „Konfiguration“](assets/xf-folders-18.png)

1. Geben Sie im Dialogfeld **[!UICONTROL Experience Fragments konfigurieren]** die erforderlichen Vorlagen an:

   ![Experience Fragments konfigurieren](assets/xf-folders-19.png)

1. Wählen Sie **[!UICONTROL Speichern]** aus.

## Erstellen eines Experience Fragment {#creating-an-experience-fragment}

Gehen Sie zum Erstellen eines Experience Fragment folgendermaßen vor:

1. Wählen Sie in der globalen Navigation die Option **[!UICONTROL Experience Fragments]** aus.

   ![screen_shot_2018-04-05at92221am1](assets/screen_shot_2018-04-05at92221am1.png)

1. Navigieren Sie zum gewünschten Ordner und wählen Sie **[!UICONTROL Erstellen]**.

1. Wählen Sie **[!UICONTROL Experience Fragment]** aus, um den Assistenten zum **[!UICONTROL Erstellen von Experience Fragments]** zu öffnen.

   Wählen Sie die gewünschte **[!UICONTROL Vorlage]** aus und klicken Sie auf **[!UICONTROL Weiter]**:

   ![xf-authoring-02](assets/xf-authoring-02.png)


1. Geben Sie die **[!UICONTROL Eigenschaften]** für das Experience Fragment ein.

   Sie müssen einen **[!UICONTROL Titel]** angeben. Wenn Sie das Feld **[!UICONTROL Name]** leer lassen, wird der Name vom **[!UICONTROL Titel]** abgeleitet.

   ![xf-authoring-03](assets/xf-authoring-03.png)

1. Klicken Sie auf **[!UICONTROL Erstellen]**.

   Daraufhin wird eine Meldung angezeigt. Wählen Sie nun eine der folgenden Optionen aus:

   * **[!UICONTROL Fertig]**, um zur Konsole zurückzukehren
   * **[!UICONTROL Öffnen]**, um den Editor für Fragmente zu öffnen

## Bearbeiten eines Experience Fragment {#editing-your-experience-fragment}

Der Editor für Erlebnisfragmente bietet ähnliche Funktionen wie der normale Seiten-Editor. Siehe [Bearbeiten des Seiteninhalts](/help/sites-authoring/editing-content.md) für weitere Informationen zur Verwendung.

Die folgende Beispielvorgehensweise veranschaulicht, wie Sie Teaser für Produkte erstellen:

1. Ziehen Sie per Drag-and-Drop einen Kategorien-Teaser **** aus dem [Komponenten-Browser](/help/sites-authoring/author-environment-tools.md#components-browser).

   ![xf-authoring-04](assets/xf-authoring-04.png)

1. Wählen Sie in der Komponenten-Symbolleiste die Option **[[!UICONTROL Konfigurieren]](/help/sites-authoring/editing-content.md#edit-configure-copy-cut-delete-paste)**.
1. Fügen Sie das **[!UICONTROL Asset]** hinzu und definieren Sie die **[!UICONTROL Eigenschaften]** nach Bedarf.
1. Bestätigen Sie die Definitionen mit der Option **[!UICONTROL Fertig]** (Häkchen).
1. Fügen Sie bei Bedarf weitere Komponenten hinzu.

## Erstellen einer Experience Fragment-Variante {#creating-an-experience-fragment-variation}

Je nach Ihren Anforderungen können Sie Varianten eines Experience Fragment erstellen:

1. Öffnen Sie ein Fragment zur [Bearbeitung](/help/sites-authoring/experience-fragments.md#editing-your-experience-fragment).
1. Öffnen Sie die Registerkarte **[!UICONTROL Varianten]**.

   ![xf-authoring-06](assets/xf-authoring-06.png)

1. Die Option **Erstellen** ermöglicht es Ihnen, Folgendes zu erstellen:

   * **[!UICONTROL Variante]**
   * **[!UICONTROL Variante als Live Copy]**

1. Definieren Sie die gewünschten Eigenschaften:

   * **[!UICONTROL Vorlage]**
   * **[!UICONTROL Titel]**
   * **[!UICONTROL Name]** (Wenn Sie das Feld leer lassen, wird der Name vom Titel abgeleitet.)
   * **[!UICONTROL Beschreibung]**
   * **[!UICONTROL Varianten-Tags]**

   ![xf-authoring-07](assets/xf-authoring-07.png)

1. Bestätigen Sie Ihre Auswahl mit der Option **[!UICONTROL Fertig]** (Häkchen). Daraufhin wird die neue Variante im Bedienfeld angezeigt:

   ![xf-authoring-08](assets/xf-authoring-08.png)

## Verwenden eines Experience Fragment {#using-your-experience-fragment}

Jetzt können Sie das Experience Fragment auf Ihren Seiten verwenden:

1. Öffnen Sie eine beliebige Seite, um sie zu bearbeiten.

   Beispiel: [http://localhost:4502/editor.html/content/we-retail/language-masters/de/products/men.html](http://localhost:4502/editor.html/content/we-retail/language-masters/de/products/men.html)

1. Erstellen Sie eine Instanz der Experience-Fragment-Komponente, indem Sie die Komponente aus dem Komponenten-Browser auf das Seitenabsatzsystem ziehen:

   ![xf-authoring-09](assets/xf-authoring-09.png)

1. Fügen Sie das eigentliche Experience Fragment zur Komponenteninstanz hinzu, indem Sie einen der folgenden Schritte ausführen:

   * Ziehen Sie das gewünschte Fragment vom Asset-Browser auf die Komponente
   * Wählen Sie in der Komponenten-Symbolleiste die Option **[!UICONTROL Konfigurieren]** und geben Sie das zu verwendende Fragment an. Bestätigen Sie Ihre Auswahl mit der Option **Fertig** (Häkchen).

   ![xf-authoring-10](assets/xf-authoring-10.png)

   >[!NOTE]
   >
   >In der Komponenten-Symbolleiste dient die Option „Bearbeiten“ als Kurzbefehl zum Öffnen eines Fragments im Editor für Fragmente.

## Bausteine {#building-blocks}

Sie können eine oder mehrere Komponenten auswählen, um einen Baustein zur Wiederverwendung in Ihrem Fragment zu erstellen:

### Erstellen eines Bausteins {#creating-a-building-block}

So erstellen Sie einen neuen Baustein:

1. Wählen Sie im Editor für Experience Fragments die Komponenten, die wiederverwendet werden sollen:

   ![xf-authoring-12](assets/xf-authoring-12.png)

1. Wählen Sie in der Komponenten-Symbolleiste die Option **[!UICONTROL In Baustein umwandeln]** aus:

   ![xf-authoring-13-icon](assets/xf-authoring-13-icon.png)

   Beispiel:

   ![xf-authoring-13](assets/xf-authoring-13.png)

1. Geben Sie den **[!UICONTROL Namen des Bausteins]** ein und bestätigen Sie ihn mit der Option **[!UICONTROL Konvertieren]**:

   ![xf-authoring-14](assets/xf-authoring-14.png)

1. Der **Building-Block** wird auf der Registerkarte angezeigt und kann im Absatzsystem ausgewählt werden:

   ![xf-authoring-15](assets/xf-authoring-15.png)

### Verwalten eines Bausteins {#managing-a-building-block}

Der Baustein wird auf der Registerkarte **[!UICONTROL Bausteine]** angezeigt. Für jeden Baustein sind die folgenden Aktionen verfügbar:

* Zur Hauptvariante wechseln: zum Öffnen der Hauptvariante in einer neuen Registerkarte
* Umbenennen
* Löschen

![xf-authoring-16](assets/xf-authoring-16.png)

### Verwenden eines Bausteins {#using-a-building-block}

Sie können den Baustein wie bei jeder anderen Komponente auch in das Absatzsystem eines beliebigen Fragments ziehen.

## Einfache HTML-Ausgabe {#the-plain-html-rendition}

Mit dem `.plain.`-Selektor in der URL können Sie auf die einfache HTML-Ausgabe zugreifen.

Diese ist über den Browser verfügbar, aber ihr Hauptzweck ist es, anderen Applikationen (beispielsweise Web-Applikationen von Drittanbietern oder benutzerdefinierten mobilen Implementierungen) den direkten Zugriff auf den Inhalt des Experience Fragment zu ermöglichen, und zwar allein über die URL.

Die Plain-HTML-Wiedergabe fügt den Protokoll-, Host- und Kontextpfad zu Pfaden hinzu, welche:

* den folgenden Typ aufweisen: `src`, `href` oder `action`

* oder folgendermaßen enden: `-src` oder `-href`

Beispiel:

`.../brooklyn-coat/master.plain.html`

>[!NOTE]
>
>Links verweisen immer auf die Veröffentlichungsinstanz. Sie sind für die Nutzung durch Dritte bestimmt, sodass der Link immer von der Veröffentlichungsinstanz und nicht von der Autoreninstanz aufgerufen wird.

![xf-authoring-17](assets/xf-authoring-17.png)

## Exportieren von Experience Fragments {#exporting-experience-fragments}

Standardmäßig werden Experience Fragments im HTML-Format bereitgestellt. Dies kann von AEM und Drittkanalanbietern gleichermaßen verwendet werden.

Für den Export nach Adobe Target wird HTML verwendet. Vollständige Informationen finden Sie unter [Target-Integration mit Experience Fragments](/help/sites-administering/experience-fragments-target.md).
