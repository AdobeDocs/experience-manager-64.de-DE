---
title: Wiederverwenden von Assets mit MSM
description: Sie können Assets für mehrere Seiten/Ordner verwenden, die aus übergeordneten Assets abgeleitet und mit diesen verknüpft sind. Die Assets bleiben mit einer primären Kopie synchron und erhalten mit wenigen Klicks die Aktualisierungen der übergeordneten Assets.
contentOwner: AG
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: d2372ebabf92fd83cff31d4f0b37c020756f03c1
workflow-type: tm+mt
source-wordcount: '3167'
ht-degree: 79%

---


# Wiederverwenden von mit MSM für Assets[!DNL Assets]{#reuse-assets-using-msm-for-assets}

Multi-Site-Manager (MSM)-Funktionalität in [!DNL Adobe Experience Manager] ermöglicht Benutzern die Wiederverwendung von Inhalten, die einmal erstellt und über mehrere Websites hinweg wiederverwendet werden. Dasselbe gilt für digitale Assets wie MSM für die Funktionalität [!DNL Assets]. Mit MSM für [!DNL Assets] können Sie:

* Einmal Assets anlegen und dann Kopien dieser Assets erstellen, um sie in anderen Bereichen der Site wiederzuverwenden.
* Behalten Sie mehrere Kopien bei und aktualisieren Sie die ursprüngliche primäre Kopie einmal, um die Änderungen an die untergeordneten Kopien zu übertragen.
* Lokale Änderungen vornehmen, indem Sie die Verknüpfung zwischen übergeordneten und untergeordneten Assets vorübergehend oder dauerhaft unterbrechen.

## Voraussetzungen {#msm-prerequisites}

Um MSM für [!DNL Assets] zu verwenden, installieren Sie mindestens [!DNL Experience Manager] 6.4 Service Pack 5. Weitere Informationen finden Sie in den Versionshinweisen zum aktuellen Service Pack](/help/release-notes/sp-release-notes.md).[

## Wissenswertes über Vorteile und Konzepte {#understand-benefits-concepts}

### Funktionsweise und Vorteile {#how-it-works-the-benefits}

Weitere Informationen zu Nutzungsszenarien einer Wiederverwendung identischer Inhalte (Text und Assets) über mehrere Web-Speicherorte hinweg finden Sie unter [Mögliche MSM-Szenarien](/help/sites-administering/msm.md). [!DNL Experience Manager] unterhält einen Link zwischen dem ursprünglichen Asset und dessen verknüpften Kopien, die als Live Copies (LCs) bezeichnet werden. Diese bestehende Verknüpfung ermöglicht Push-Übertragungen zentraler Änderungen an eine große Zahl von Live Copies. Auf diese Weise werden schnellere Aktualisierungen ermöglicht, während die mit der Verwaltung doppelter Kopien einhergehenden Beschränkungen entfallen. Die Übertragung von Änderungen erfolgt fehlerfrei und zentralisiert. Die Funktion lässt Raum für Aktualisierungen, die auf ausgewählte Live Copies beschränkt sind. Benutzer können die Verknüpfung, d. h. die Vererbung von Pausen, auflösen und lokale Änderungen vornehmen, die nicht überschrieben werden, wenn die primäre Kopie das nächste Mal aktualisiert und Änderungen ausgeführt werden. Die Trennung kann für einige ausgewählte Metadatenfelder oder für ein vollständiges Asset vorgenommen werden. Es bietet Flexibilität bei der lokalen Aktualisierung von Assets, die ursprünglich von einer primären Kopie geerbt wurden.

MSM behält eine (Live-)Beziehung zwischen dem Quell-Asset und seinen Live Copies bei, sodass:

* Änderungen an den Quell-Assets auch auf Live Copies angewendet werden (Rollout), d. h., die Live Copies werden mit der Quelle synchronisiert;

* Sie Live Copies aktualisieren können, indem Sie die Live-Beziehung aussetzen oder die Vererbung für wenige begrenzte Felder entfernen. Die Änderungen an der Quelle werden nicht mehr auf die Live Copy angewendet.

### Glossar der Begriffe in MSM für Assets   {#glossary-msm-for-assets}

* **Quelle:** Die ursprünglichen Assets oder Ordner. Primär Kopie, von der Live-Kopien abgeleitet werden.

* **Live Copy:** Die Kopie der Quellelemente/Ordner, die mit ihrer Quelle synchronisiert wird. Live Copies können eine Quelle für weitere Live Copies sein. Siehe [Erstellen von LCs](#create-live-copy-asset).

* **Vererbung:** Ein Link/Verweis zwischen einem Live-Copy-Asset/-Ordner und seiner Quelle, über den das System speichert, wohin die Updates gesendet werden sollen. Eine Vererbung existiert für Metadatenfelder auf granularer Ebene. Die Vererbung kann für ausgewählte Metadatenfelder entfernt werden, während die Live-Beziehung zwischen Quelle und zugehöriger Live Copy beibehalten wird.

* **Rollout**: Eine Aktion, die die Änderungen an der Quelle nach ihren Live-Kopien schiebt. Es ist möglich, mithilfe der Aktion „Rollout“ eine oder mehrere Live Copies in einem Schritt zu aktualisieren. Siehe [Rollout](#rollout-action).

* **Rollout-Konfiguration:** Regeln, die festlegen, welche Eigenschaften synchronisiert werden, wie und wann. Diese Konfigurationen werden beim Erstellen von Live Copies angewendet und können später bearbeitet werden. Dabei kann ein untergeordnetes Element die Rollout-Konfiguration vom zugehörigen übergeordneten Asset übernehmen. Verwenden Sie für MSM für [!DNL Assets] nur die Standard-Rollout-Konfiguration. Die anderen Rollout-Konfigurationen sind für MSM für [!DNL Assets] nicht verfügbar.

* **Synchronisieren:** Eine weitere Aktion, die zusätzlich zur Einführung eine Parität zwischen Quelltext und Live-Kopie herstellt, indem die Updates von der Quelle an Live-Kopien gesendet werden. Eine Synchronisierung wird für eine bestimmte Live Copy initiiert und die Aktion ruft die Änderungen von der Quelle ab. Mit dieser Aktion können Sie nur eine der Live Copies aktualisieren. Siehe [Aktion „Synchronisieren“](#about-synchronize-action).

* **Aussetzen: Entfernen Sie** vorübergehend die Live-Beziehung zwischen einer Live-Kopie und ihrem Quellasset/Ordner. Sie können die Beziehung wieder aufnehmen. Siehe [Aktion „Aussetzen“](#suspend-and-resume-relationship).

* **Fortsetzen:** Nehmen Sie die Live-Beziehung wieder auf, damit Beginn, die die Updates aus der Quelle erhalten haben, erneut eine Live-Kopie erhalten. Siehe [Aktion „Fortsetzen“](#suspend-and-resume-relationship).

* **Zurücksetzen:** Die Aktion &quot;Zurücksetzen&quot;bewirkt, dass die Live-Kopie erneut eine Kopie der Quelle darstellt, indem alle lokalen Änderungen überschrieben werden. Außerdem werden abgebrochene Vererbungsvorgänge entfernt und Vererbungen in allen Metadatenfeldern zurückgesetzt. Für zukünftige lokale Änderungen müssen Sie die Vererbung bestimmter Felder erneut abbrechen. Siehe [Lokale Änderungen an LC](#make-local-modifications-to-live-copy).

* **Trennen:** Entfernen Sie unwiderruflich die Live-Beziehung eines Live Copy-Assets/Ordners. Nach der Aktion „Trennen“ können Live Copies niemals Aktualisierungen aus der Quelle empfangen und sie haben keinen Live Copy-Status mehr. Siehe [Entfernen von Beziehungen](#remove-live-relationship).

## Erstellen von Live Copies eines Assets {#create-live-copy-asset}

Führen Sie einen der folgenden Schritte aus, um eine Live Copy aus einem oder mehreren Quell-Assets oder -Ordnern zu erstellen:

* **Methode 1**: Wählen Sie die Quellelemente aus und klicken Sie oben auf der Symbolleiste auf  **[!UICONTROL Erstellen]** >  **[!UICONTROL Live-]** Kopieren.
* **** Methode 2: Klicken Sie oben rechts in der AEM-Benutzeroberfläche auf **[!UICONTROL Erstellen > Live Copy]**.

Sie können Live Copies eines Assets oder Ordners einzeln erstellen. Sie können Live Copies erstellen, die aus einem Asset oder Ordner abgeleitet werden, der ebenfalls eine Live Copy ist.

Inhaltsfragmente werden für das Nutzungsszenario nicht unterstützt. Wenn Sie versuchen, deren Live Copies zu erstellen, werden die Inhaltsfragmente wie vorliegend und ohne Beziehung kopiert. Die kopierten Inhaltsfragmente sind eine Momentaufnahme und werden nicht zusammen mit den ursprünglichen Inhaltsfragmenten aktualisiert.

Führen Sie folgende Schritte aus, um Live Copies mit der ersten Methode zu erstellen:

1. Wählen Sie Quell-Assets oder -ordner aus. Klicken Sie in der Symbolleiste auf **[!UICONTROL Erstellen > Live Copy]**.
   ![Erstellen einer Live Copy über die AEM-Oberfläche](assets/lc_create1.png)
1. Wählen Sie Quell-Asset oder -ordner aus. Klicken Sie auf **[!UICONTROL Weiter]**.
1. Geben Sie einen Titel und Namen an. Assets haben keine untergeordneten Elemente. Wenn Sie eine Live Copy von Ordnern erstellen, können Sie die untergeordneten Elemente ein- oder ausschließen.
1. Wählen Sie eine Rollout-Konfiguration aus. Klicken Sie auf **[!UICONTROL Erstellen]**.

Führen Sie folgende Schritte aus, um Live Copies mit der zweiten Methode zu erstellen:

1. Klicken Sie oben rechts in der AEM-Oberfläche auf **[!UICONTROL Erstellen > Live Copy]**.
   ![Erstellen einer Live Copy über die AEM-Oberfläche](assets/lc_create2.png)
1. Wählen Sie Quell-Asset oder -ordner aus. Klicken Sie auf **[!UICONTROL Weiter]**.
1. Wählen Sie einen Zielordner aus. Klicken Sie auf **[!UICONTROL Weiter]**.
1. Geben Sie einen Titel und Namen an. Assets haben keine untergeordneten Elemente. Wenn Sie eine Live Copy von Ordnern erstellen, können Sie die untergeordneten Elemente ein- oder ausschließen.
1. Wählen Sie eine Rollout-Konfiguration aus. Klicken Sie auf **[!UICONTROL Erstellen]**.

>[!NOTE]
>
>Wenn eine Quelle oder Live Copy verschoben wird, werden die Beziehungen beibehalten. Wenn eine Live Copy gelöscht wird, werden die Beziehungen entfernt.

## Anzeigen verschiedener Eigenschaften und Status von Quelle und Live Copy {#view-properties-statuses-source-and-lc}

Sie können Informationen und MSM-bezogene Status der Live Copy wie Beziehung, Synchronisierung, Rollouts usw. in verschiedenen Bereichen der AEM-Benutzeroberfläche anzeigen. Die folgenden beiden Methoden funktionieren für Assets und Ordner:

* Wählen Sie Live Copy-Asset und suchen Sie die Informationen auf der Seite **[!UICONTROL Eigenschaften]**.
* Wählen Sie den Quellordner und suchen Sie die detaillierten Informationen zu den einzelnen Live-Kopien unter **[!UICONTROL Live Copy Console]**.

>[!TIP]
>
>Um den Status einiger separater Live-Kopien zu überprüfen, verwenden Sie die erste Methode, um die Seite **[!UICONTROL Eigenschaften]** zu überprüfen. Um den Status vieler Live-Kopien zu überprüfen, verwenden Sie die zweite Methode, um die Seite **[!UICONTROL Beziehungsstatus]** zu überprüfen.

### Informationen und Status von Live Copies    {#information-status-of-one-lc}

Führen Sie folgende Schritte aus, um Informationen und Status eines Live Copy-Assets oder -Ordners zu prüfen.

1. Wählen Sie ein Live Copy-Asset oder einen Ordner aus. Klicken Sie in der Symbolleiste auf **[!UICONTROL Eigenschaften]**. Sie können auch den Tastaturbefehl `p` verwenden.
1. Klicken Sie auf **[!UICONTROL Live Copy]**. Sie können den Pfad der Quelle, den Aussetzen-Status, den Synchronisierungsstatus, das letzte Rollout-Datum und den Benutzer, der das letzte Rollout durchgeführt hat, prüfen.
   ![Live Copy-Informationen und -Status werden in einer Konsole in den Eigenschaften angezeigt](assets/lc_folder_properties.png)
1. Eine Aktivierung oder Deaktivierung ist möglich, wenn untergeordnete Assets die Live Copy-Konfiguration übernehmen.
1. Sie können die Option für die Live Copy wählen, um die Rollout-Konfiguration vom übergeordneten Asset zu übernehmen oder die Konfiguration zu ändern.

### Informationen und Status aller Live Copies eines Ordners {#information-status-of-all-lcs-of-folder}

[!DNL Experience Manager] stellt eine Konsole bereit, um die Status aller Live Copies eines Quellordners zu prüfen. Diese Konsole zeigt den Status aller untergeordneten Assets an.

1. Wählen Sie einen Quellordner aus. Klicken Sie in der Symbolleiste auf **[!UICONTROL Eigenschaften]**. Sie können auch den Tastaturbefehl `p` verwenden.
1. Klicken Sie auf **[!UICONTROL Live Copy-Quelle]**. Klicken Sie auf **[!UICONTROL Live Copy-Übersicht]**, um die Konsole zu öffnen. Dieses Dashboard liefert übergeordnete Statusinformationen aller untergeordneten Assets.
   ![Anzeigen der Status von Live Copies in der Live Copy-Konsole der Quelle](assets/lc_statuses.png)
1. Um die detaillierten Informationen zu den einzelnen Assets im Ordner „Live Copy“ anzuzeigen, wählen Sie ein Asset aus und klicken Sie in der Symbolleiste auf **[!UICONTROL Beziehungsstatus]**.
   ![Detaillierte Informationen und Status eines untergeordneten Live Copy-Assets in einem Ordner](assets/lc_relationship_status.png)

>[!TIP]
>
>Sie können die Status von Live-Kopien anderer Ordner schnell sehen, ohne zu viel durchsuchen zu müssen. Ändern Sie den Ordner aus der oberen Mitte der **[!UICONTROL Live Copy-Benutzeroberfläche]**.

### Schnellaktionen in der Leiste „Verweise“ für Quellen {#quick-actions-from-references-rail-for-source}

Für Quell-Assets oder -ordner können Sie die folgenden Informationen über die Leiste „Verweise“ anzeigen und die folgenden Aktionen von dort aus direkt ausführen:

* Anzeigen der Pfade von Live Copies
* Öffnen oder zeigen Sie eine bestimmte Live-Kopie in der [!DNL Experience Manager]-Benutzeroberfläche an.
* Synchronisieren von Aktualisierungen mit einer bestimmten Live Copy
* Aussetzen der Beziehung oder Ändern der Rollout-Konfiguration für eine bestimmte Live Copy
* Zugreifen auf die Konsole „Live Copy-Übersicht“

Wählen Sie Quell-Asset oder -ordner aus, öffnen Sie die linke Leiste und klicken Sie auf **[!UICONTROL Verweise]**. Sie können auch ein Asset oder einen Ordner auswählen und den Tastaturbefehl `Alt + 4` verwenden.

![In der Leiste „Verweise“ für die ausgewählte Quelle verfügbare Aktionen und Informationen](assets/lc_referencerail_source.png)

Klicken Sie für eine bestimmte Live Copy auf **[!UICONTROL Live Copy bearbeiten]**, um die Beziehung auszusetzen oder die Rollout-Konfiguration zu ändern.

![Bei einer bestimmten Live-Kopie ist die Option zum Aussetzen der Beziehung oder zum Ändern der Rollout-Konfiguration über die Bezugsleiste verfügbar, wenn das Quellelement ausgewählt ist](assets/lc_edit_referencerail.png)

### Schnellaktionen in der Leiste „Verweise“ für Live Copies    {#quick-actions-from-references-rail-for-live-copy}

Für Live Copy-Assets oder -Ordner können Sie die folgenden Informationen über die Leiste „Verweise“ anzeigen und die folgenden Aktionen von dort aus direkt ausführen:

* Anzeigen des Pfads der zugehörigen Quelle.
* Öffnen oder zeigen Sie eine bestimmte Live-Kopie in der [!DNL Experience Manager]-Benutzeroberfläche an.
* Stellen Sie die Aktualisierungen bereit.

Wählen Sie Live Copy-Asset oder -Ordner aus, öffnen Sie die linke Leiste und klicken Sie auf **[!UICONTROL Verweise]**. Sie können auch ein Asset oder einen Ordner auswählen und den Tastaturbefehl `Alt + 4` verwenden.

![In der Leiste „Verweise“ für die ausgewählte Live Copy verfügbare Aktionen](assets/lc_referencerail.png)

## Übertragen von Änderungen von der Quelle an Live Copies    {#propagate-modifications-from-source-to-live-copies}

Nach der Bearbeitung einer Quelle können die Änderungen entweder mithilfe einer Aktion „Synchronisieren“ oder „Rollout“ an die Live Copies übertragen werden. Informationen zu den Unterschieden zwischen beiden Aktionen finden Sie im [Glossar](#glossary-msm-for-assets).

### Aktion „Rollout“ {#rollout-action}

Sie können eine Aktion „Rollout“ über das Quell-Asset initiieren und alle oder einige ausgewählte Live Copies aktualisieren.

1. Wählen Sie ein Live Copy-Asset oder einen Ordner aus. Klicken Sie in der Symbolleiste auf **[!UICONTROL Eigenschaften]**. Sie können auch den Tastaturbefehl `p` verwenden.
1. Klicken Sie auf **[!UICONTROL Live Copy-Quelle]**. Klicken Sie in der Symbolleiste auf **[!UICONTROL Rollout]**.
1. Wählen Sie die zu aktualisierenden Live Copies aus. Klicken Sie auf **[!UICONTROL Rollout]**.
1. Um ein Rollout der an den untergeordneten Assets vorgenommenen Aktualisierungen durchzuführen, wählen Sie **[!UICONTROL Rollout von Quelle und allen untergeordneten Elementen]** aus.
   ![Rollout von Quelländerungen an einige oder alle Live Copies](assets/lc_rollout_page.png)

>[!NOTE]
>
>Änderungen an einem Quell-Asset werden nur den Live Copies mit einem direkten Verweis bereitgestellt. Wenn eine Live Copy von einer anderen Live Copy abgeleitet wird, werden die Änderungen nicht der abgeleiteten Live Copy bereitgestellt.

Alternativ können Sie eine Rollout-Aktion über die Leiste [!UICONTROL References] starten, nachdem Sie eine bestimmte Live-Kopie ausgewählt haben. Weitere Informationen finden Sie unter [Schnellaktionen in der Leiste „Verweise“ für Live Copies](#quick-actions-from-references-rail-for-live-copy). Bei dieser Rollout-Methode werden nur die ausgewählte Live Copy und optional deren untergeordnete Elemente aktualisiert.

![Rollout von Quelländerungen an die ausgewählte Live Copy](assets/lc_rollout_dialog.png)

### Wissenswertes über die Aktion „Synchronisieren“ {#about-synchronize-action}

Durch eine Aktion „Synchronisieren“ werden die Änderungen einer Quelle nur an die ausgewählte Live Copy übertragen. Die Aktion „Synchronisieren“ respektiert und bewahrt die lokalen Änderungen, die nach dem Abbrechen der Vererbung vorgenommen wurden. Die lokalen Änderungen werden nicht überschrieben und die abgebrochene Vererbung wird nicht wiederhergestellt. Sie haben drei Möglichkeiten, um eine Aktion „Synchronisieren“ zu initiieren.

| Wohin in der [!DNL Experience Manager]-Schnittstelle | Zeitpunkt und Grund für die Verwendung | Verwendung |
|---|---|---|
| [!UICONTROL Leiste „Verweise“] | Schnelles Synchronisieren bei bereits ausgewählter Quelle | Siehe [Schnellaktionen in der Leiste „Verweise“ für Quellen](#quick-actions-from-references-rail-for-source) |
| Symbolleiste auf der Seite [!UICONTROL Eigenschaften] | Initiieren von Synchronisationen bei bereits öffneten Live Copy-Eigenschaften | Siehe [Synchronisieren von Live Copies](#synchronize-live-copy) |
| [!UICONTROL Konsole „Live Copy-Übersicht“] | Synchronisieren Sie schnell mehrere Assets (nicht unbedingt alle), wenn der Quellordner ausgewählt ist oder die Konsole [!UICONTROL Übersicht über die Live-Kopie] bereits geöffnet ist. Initiieren der Aktion „Synchronisieren“ für jeweils ein Asset, aber eine schnellere Methode, um mehrere Assets auf einmal zu synchronisieren | Siehe [Aktionen für viele Assets in einem Live Copy-Ordner](#take-actions-on-many-assets-in-lcfolder) |

### Synchronisieren von Live Copies    {#synchronize-live-copy}

Um eine Aktion „Synchronisieren“ zu starten, öffnen Sie die Seite **[!UICONTROL Eigenschaften]** einer Live Copy, klicken Sie auf **[!UICONTROL Live Copy]** und dann auf die gewünschte Aktion in der Symbolleiste.

Informationen zu Status und Informationen zu einer Synchronisierungsaktion finden Sie unter [Informationen und Status aller Live-Kopien eines Ordners](#information-status-of-all-lcs-of-folder).

![Aktion „Synchronisieren“ – Abrufen von Quelländerungen](assets/lc_sync.png)

>[!NOTE]
>
>Wenn die Beziehung ausgesetzt ist, ist die Aktion „Synchronisieren“ in der Symbolleiste nicht verfügbar. Während die Synchronisierungsaktion in der Leiste [!UICONTROL Referenzen] verfügbar ist, werden die Änderungen auch bei einer erfolgreichen Einführung nicht weitergegeben.

## Aussetzen und Fortsetzen der Beziehung {#suspend-and-resume-relationship}

Sie können die Beziehung vorübergehend aussetzen, um zu verhindern, dass eine Live Copy am Quell-Asset oder -ordner vorgenommene Änderungen erhält. Die Beziehung kann für die Live Copy auch fortgesetzt werden, um Änderungen von der Quelle zu erhalten.

Zum Aussetzen oder Fortsetzen öffnen Sie die Seite **[!UICONTROL Eigenschaften]** einer Live Copy, klicken Sie auf **[!UICONTROL Live Copy]** und dann auf die gewünschte Aktion in der Symbolleiste.

Beziehungen von mehreren Assets in einem Live Copy-Ordner können auch schnell über die Konsole **[!UICONTROL Live Copy-Übersicht]** ausgesetzt oder fortgesetzt werden. Siehe [Ausführen von Aktionen für viele Assets in einem Live Copy-Ordner](#take-actions-on-many-assets-in-lcfolder).

## Lokales Ändern von Live Copies {#make-local-modifications-to-live-copy}

Eine Live Copy ist eine Replikation der ursprünglichen Quelle zum Zeitpunkt ihrer Erstellung. Die Metadatenwerte einer Live Copy werden von der Quelle übernommen. Die Metadatenfelder halten einzeln die Vererbung mit den entsprechenden Feldern des Quell-Assets aufrecht.

Sie haben jedoch die Flexibilität, lokale Änderungen an einer Live Copy vorzunehmen, um einige ausgewählte Eigenschaften zu ändern. Um lokale Änderungen vorzunehmen, brechen Sie die Vererbung der gewünschten Eigenschaft ab. Wenn die Vererbung von mindestens einem Metadatenfeld abgebrochen wird, werden Live-Beziehung des Assets und Vererbung der anderen Metadatenfelder beibehalten. Bei einer Synchronisierung oder einem Rollout werden die lokalen Änderungen nicht überschrieben. Öffnen Sie dazu die Seite **[!UICONTROL Eigenschaften]** eines Live Copy-Assets und klicken Sie auf die Option **[!UICONTROL Vererbung abbrechen]** neben einem Metadatenfeld.

Sie können alle lokalen Änderungen rückgängig machen und das Asset auf den Status seiner Quelle zurücksetzen. Setzen Sie die Aktion unwiderruflich zurück, überschreiben Sie sofort alle lokalen Änderungen und stellen Sie die Vererbung bei allen Metadatenfeldern wieder her. Zwecks Wiederherstellung klicken Sie auf der Seite **[!UICONTROL Eigenschaften]** eines Live Copy-Assets in der Symbolleiste auf **[!UICONTROL Zurücksetzen]**.

![Aktion zurücksetzen überschreibt lokale Bearbeitungen und bringt die Live-Kopie zum Teil mit der Quelle](assets/lc_reset.png)

## Entfernen von Live-Beziehungen    {#remove-live-relationship}

Sie können die Beziehung zwischen Quelle und Live Copy mit der Aktion „Trennen“ vollständig entfernen. Nach dem Trennen wird die Live Copy zu einem eigenständigen Asset oder Ordner. Sie wird unmittelbar nach dem Trennen als neues Asset in der AEM-Oberfläche angezeigt. Führen Sie die folgenden Schritte aus, um eine Live Copy von ihrer Quelle zu trennen.

1. Wählen Sie ein Live Copy-Asset oder einen Ordner aus. Klicken Sie in der Symbolleiste auf **[!UICONTROL Eigenschaften]**. Sie können auch den Tastaturbefehl `p` verwenden.
1. Klicken Sie auf **[!UICONTROL Live Copy]**. Klicken Sie in der Symbolleiste auf **[!UICONTROL Trennen]**. Klicken Sie im angezeigten Dialogfeld auf **[!UICONTROL Trennen]**.
   ![Aktion „Trennen“ – vollständiges Entfernen der Beziehung zwischen Quelle und Live Copy](assets/lc_detach.png)

>[!CAUTION]
>
>Die Beziehung wird entfernt, sobald Sie im Dialogfeld auf [!UICONTROL Trennen] klicken. Sie können diesen Vorgang nicht rückgängig machen, indem Sie auf der Seite „Eigenschaften“ auf [!UICONTROL Abbrechen] klicken.

Mehrere Assets in einem Live Copy-Ordner können auch schnell über die Konsole **[!UICONTROL Live Copy-Übersicht]** getrennt werden. Siehe [Ausführen von Aktionen für viele Assets in einem Live Copy-Ordner](#take-actions-on-many-assets-in-lcfolder).

## Ausführen von Aktionen für viele Assets in einem Live Copy-Ordner {#take-actions-on-many-assets-in-lcfolder}

Wenn mehrere Assets in einem Live Copy-Ordner vorhanden sind, kann das Initiieren von Aktionen für jedes Asset mühsam sein. Sie können grundlegende Aktionen für eine große Zahl von Assets schnell über die Live Copy-Konsole initiieren. Die oben genannten Methoden können nach wie vor für einzelne Assets verwendet werden.

1. Wählen Sie einen Quellordner aus. Klicken Sie in der Symbolleiste auf **[!UICONTROL Eigenschaften]**. Sie können auch den Tastaturbefehl p verwenden.
1. Klicken Sie auf Live Copy-Quelle. Klicken Sie auf **[!UICONTROL Live Copy-Übersicht]**, um die Konsole zu öffnen.
1. Wählen Sie in diesem Dashboard ein Live Copy-Asset aus einem Live Copy-Ordner aus. Klicken Sie in der Symbolleiste auf die gewünschten Aktionen. Die verfügbaren Aktionen sind **[!UICONTROL Bearbeiten]**, **[!UICONTROL Synchronisieren]**, **[!UICONTROL Zurücksetzen]**, **[!UICONTROL Aussetzen]** und **[!UICONTROL Entfernen]**. Sie können diese Aktionen schnell für beliebige Assets in einer beliebigen Anzahl von Live Copy-Ordnern starten, die sich in einer Live-Beziehung mit dem ausgewählten Quellordner befinden.
   ![Einfaches Aktualisieren vieler Assets in Live Copy-Ordnern über die Konsole „Live Copy-Übersicht“](assets/lc_console_update_assets.png)

## Erweitern von MSM für Assets {#extend-msm-for-assets}

AEM ermöglicht es, die Funktionalität mithilfe der MSM-Java-APIs zu erweitern. Bei MSM für Assets funktioniert die Erweiterung genauso wie bei MSM für Sites. Weitere Details finden Sie unter [Erweitern von MSM](../sites-developing/extending-msm.md) sowie Informationen zu bestimmten Aufgaben in den folgenden Abschnitten:

* [Übersicht über APIs](../sites-developing/extending-msm.md#overview-of-the-java-api)
* [Erstellen einer neuen Aktion „Synchronisieren“](../sites-developing/extending-msm.md#creating-a-new-synchronization-action)
* [Erstellen einer neuen Rollout-Konfiguration](../sites-developing/extending-msm.md#creating-a-new-rollout-configuration)
* [Erstellen und Verwenden einer einfachen LiveActionFactory-Klasse](../sites-developing/extending-msm.md#creating-and-using-a-simple-liveactionfactory-class)

>[!NOTE]
>
>* Blueprints in MSM für Sites werden in MSM für Assets als Live Copy-Quellen bezeichnet.
>* Das Entfernen des Schritts „Kapitel“ im Assistenten zum Erstellen von Sites wird in MSM für Assets nicht unterstützt.
>* Das Konfigurieren von MSM-Sperren in Seiteneigenschaften (Touch-optimierte Benutzeroberfläche) wird in MSM für Assets nicht unterstützt.


## Auswirkungen von Asset-Management-Aufgaben auf Live Copies {#impact-of-asset-management-tasks-on-live-copies}

Live Copies und Quellen sind Assets oder Ordner, die in gewissem Umfang als digitale Assets verwaltet werden können. Einige Asset-Management-Aufgaben in AEM haben eine spezifische Auswirkung auf Live Copies.

* Beim Kopieren einer Live Copy wird ein Live Copy-Asset mit derselben Quelle wie bei der ersten Live Copy erstellt.
* Wenn Sie eine Quelle oder eine Live Copy verschieben, wird die Live-Beziehung beibehalten.
* Die Aktion „Bearbeiten“ funktioniert nicht bei Live Copy-Assets.
* Die Aktion „Checkout“ ist nicht für Live Copy-Assets verfügbar.
* Für Quellordner ist die Option zum Erstellen von Prüfungsaufgaben verfügbar.
* Beim Anzeigen der Asset-Liste in der Listen- und Spaltenansicht sind Live Copy-Assets oder -Ordner mit „Live Copy“ gekennzeichnet. Auf diese Weise lassen sich Live Copies in einem Ordner leicht erkennen.

## MSM für Assets und Sites im Vergleich {#compare-msm-for-assets-and-sites}

In weiteren Szenarien entspricht das Verhalten von MSM für Assets dem von MSM für Sites. Einige wichtige Unterschiede lauten wie folgt:

* In Sites können Sie Blueprints und deren Live Copies vergleichen. In Assets ist es jedoch nicht möglich, eine Quelle mit der zugehörigen Live Copy zu vergleichen.
* Sites verfügen normalerweise über untergeordnete Elemente, Assets jedoch nicht. Die Option zum Ein- oder Ausschließen von untergeordneten Elementen ist beim Erstellen von Live Copies einzelner Assets nicht vorhanden.
* Das Entfernen des Schritts „Kapitel“ im Assistenten zum Erstellen von Sites wird in MSM für Assets nicht unterstützt.
* Das Konfigurieren von MSM-Sperren in Seiteneigenschaften (Touch-optimierte Benutzeroberfläche) wird in MSM für Assets nicht unterstützt.
* Verwenden Sie für MSM für Assets nur die standardmäßige Rollout-Konfiguration. Die anderen Rollout-Konfigurationen sind für MSM für Assets nicht verfügbar.

## Einschränkungen von MSM für Assets {#limitations-of-msm-for-assets}

Im Folgenden finden Sie die Einschränkungen bei MSM für Assets.

* Inhaltsfragmente werden für das Nutzungsszenario nicht unterstützt. Wenn Sie versuchen, deren Live Copies zu erstellen, werden die Inhaltsfragmente wie vorliegend und ohne Beziehung kopiert. Die kopierten Inhaltsfragmente sind eine Momentaufnahme und werden nicht zusammen mit den ursprünglichen Inhaltsfragmenten aktualisiert.

* MSM funktioniert nicht mit aktiviertem Metadaten-Schreibback. Beim Zurückschreiben bricht das Erbe.
